# CONFLUENCE_DEFS.md - exact definitions of the entry-table columns (W-CF1, built 2026-11-15 18:59Z)
Verdict line: definitions are frozen by code (code/th_confl/ta_cats.py, ta_user.py, ta_ind.py, ta_cond.py); this page is generated from the same registries; nothing here has been scored yet.

## Table and ids
- Table: /mnt/l2/l2vast/_confl/entry_table/ (entry_table.parquet joined from entry_table_AEL.parquet, entry_table_U.parquet, cols_M.parquet; signal-universe file signals_all.parquet when complete). One row per entry signal, key sig_id = <book7>_<sig_ts>, sig_ts = engine signal second (epoch s UTC).
- Universe: every try_entry call with a non-zero signal in the exact JN05W2 engine (43 months 2023-04..2026-10), logged by the inert hook code/th_deepen_ta/sig_hooks.py (identity proven: 202610 = 598 trades / 25,943.82 with the hook on). taken=1 rows are the engine's trades (exit/target/pnl real); taken=0 rows carry the engine's own skip reason (skip_reason: inTrade, SCR gate conj, dayHalt, timeBlocked, session lots 0, post-cut blackout, disabled ...) and a HYPOTHETICAL outcome (bracket of the book/session median target and stop walked on 1m bars, stop first in a tie, column outcome_type). Benched X-books (X3 X4 X5 ... 'disabled') are in a separate file (step 6).
- Outcome columns: pnl (engine net at base lots, $1.18/contract fee), pnl484 (gross - $4.84 x lots), gross, lots_base (live lots = x1.75), R = side*(exit-entry)/stop_pts, mfe_pts / mae_pts (1m bars between entry and exit, vs the 1m close of the entry bar), mins_held, exit_name (Target / stop / cut names), tgt_pts, stp_pts.
- Conventions: every condition is computed from information available at sig_ts: last COMPLETE 1m bar i (bar start <= sig_ts - 60); higher-timeframe bars only once complete (HTF bar end <= sig_ts); px = close of bar i; atr = 5-minute ATR14 (harness atr5, fallback 2.2 x mean 1m range). 'yes' = favourable to the trade (signed with side): int8 1 yes / 0 no / -1 unknown (level or history not available, e.g. RTH levels before 09:30 ET). Raw value beside it: v_* float32.
- NQ prices in the 1m series are the continuous front-month bars (uwbooks/min1_NQ.npz). The engine's own prices are offset by a slowly drifting constant; every condition uses ONLY the bar series, never the engine price. Quarterly roll gaps are not adjusted: multi-day levels can be distorted for about a day per quarter.
- LEAK RULE (category L and any state of D7): every outcome-dependent column uses trades CLOSED at the signal second only (exit_ts <= sig_ts). Trades open at sig_ts contribute only through 'other_same / other_opp_none / flat_stack' (positions, no results).
- Sessions: 0 asia 18:00-01:59 ET, 1 london 02:00-08:29, 2 pre 08:30-09:29, 3 nyam 09:30-11:59, 4 nypm 12:00-14:59, 5 close 15:00-17:59. Label day (ld) = Globex day (18:00 ET starts the next ld).
- Calendar: events from /mnt/l2/l2vast/_calendar/events.csv (2024-10..); 2023-04..2024-09 FOMC/CPI/NFP backfilled from the public schedule (approximate, flagged in code calendar()). Other releases before 2024-10 are missing.
- PASSES-ALONE RULE (set 2026-11-15 from the Block 18 nonsense controls): the plain Welch z is NOT used (clustered signals inflated it: nonsense passed |z|>2 in 33-36% of pooled cells). Test = zw, the cluster-robust week-level t (per calendar week the difference of mean outcome yes-minus-no over weeks with >=2 cases each side, t over weeks, >=8 weeks; code/th_confl/step3.py week_t). A condition passes alone in a cell type and outcome only if |zw| > the 99th percentile of |zw| of the 200 nonsense controls (c_Z_*) in that cell type and outcome, AND it keeps its sign in every calendar year with >=30 cases per side and in L6M. With zw the nonsense controls pass |z|>2 in 3.5-5.5% of cells (calibrated).
- PRICE OFFSET (fixed 2026-11-15): the 1m bar series is an additive gap-spliced series whose offset from the traded price grows from ~364 pts (2023-04) to ~3,730 pts (2026-10). Only ABSOLUTE-number conditions are affected: round 100/50 levels and 'distance to round number' (categories B and the round kind of the clusters) now use TRUE price = bar price + per-day offset (table /mnt/l2/l2vast/_confl/offset_table.parquet: ld, offset = median(engine entry_px - last complete 1m close) over that day's trades, filled across days) and are unknown (-1) on the 9 roll-splice days where the offset is ambiguous. Everything else (prior-day H/L/C, value areas, POCs, VWAP, opens, pivots, gaps, indicators) is differences/ratios inside the continuous series and needs no re-basing; gap-fill, naked POCs and weekly/monthly opens compare a level with the current price across rolls and are correct because the series is continuous. No condition was dropped.
- Levels: L = ta_lib.Lib.levels(): PDH PDL PDC (prior RTH day), ONH ONL (Globex 18:00-09:30), pPOC pVAH pVAL (prior RTH 1-pt typical-price volume profile, 70% value area), oPOC oVAH oVAL (overnight), cPOC cVAH cVAL (20-day composite), nPOCup/dn (nearest naked POC of the last 20 days above/below), SPhi/SPlo (prior-day single-print tail edge, 30-min TPO count 1), session VWAP and +-1/+-2 sigma, OR5/15/30 H/L and IB (60 min) H/L (only after they complete), week open, month open, nearest 50-pt round numbers, nearest unfilled RTH gap edge. Cluster = single-linkage group of levels with neighbour spacing <= D (D = 5, 10, 15 pts, 0.1 ATR, 0.2 ATR); strength = level count and distinct KINDS (pd, on, prof, vwap, or, ib, open, round, gap). 'Ahead' = between entry and entry + side x target_pts; 'behind' = within stop_pts behind the entry.
- USER_SET_V0 (registered 23:27Z before any result): see the c_U_* rows below and the header of code/th_confl/ta_user.py (exact definitions, unknown = no, no tuning). Interpretations that the user's text left open are fixed there and labelled; V1 will be registered separately if the user corrects any.
- Category M: classic indicators on 1/3/5/15/60-min and daily bars; condition suffixes: side (midline), sig (signal line), rise (1 bar), ewith/eagainst/eleave (extreme zone in/against/left within 3 bars), nodiv/divwith (divergence at the last fractal swing k=2, same timeframe), hi (unsigned state above threshold), on / fired1 / fired10 (squeeze), agree3of4 (side true on >=3 of 3m 5m 15m 60m). Simpler-style items are labelled PUBLIC FORMULA or APPROXIMATION in the formula column.


## defs_ABCDEKL.json
- c_B_with_PDH : price on the trade side of PDH (long: above, short: below)
- c_B_with_PDL : price on the trade side of PDL (long: above, short: below)
- c_B_with_PDC : price on the trade side of PDC (long: above, short: below)
- c_B_with_ONH : price on the trade side of ONH (long: above, short: below)
- c_B_with_ONL : price on the trade side of ONL (long: above, short: below)
- c_B_with_WOPEN : price on the trade side of WOPEN (long: above, short: below)
- c_B_with_MOPEN : price on the trade side of MOPEN (long: above, short: below)
- c_B_with_OR5H : price on the trade side of OR5H (long: above, short: below)
- c_B_with_OR5L : price on the trade side of OR5L (long: above, short: below)
- c_B_with_OR15H : price on the trade side of OR15H (long: above, short: below)
- c_B_with_OR15L : price on the trade side of OR15L (long: above, short: below)
- c_B_with_OR30H : price on the trade side of OR30H (long: above, short: below)
- c_B_with_OR30L : price on the trade side of OR30L (long: above, short: below)
- c_B_with_IBH : price on the trade side of IBH (long: above, short: below)
- c_B_with_IBL : price on the trade side of IBL (long: above, short: below)
- c_B_gap_dir_with : today RTH open gapped in the trade direction (needs RTH open: from 09:30 ET)
- c_B_gap_big20 : today RTH gap >= 20 pts
- c_B_gap_big50 : today RTH gap >= 50 pts
- c_B_gap_open : today RTH gap still unfilled (prior RTH close not yet traded) and |gap| > 5
- c_B_gap_fill_ahead : unfilled gap edge (prior close) lies AHEAD in the trade direction
- c_B_ahead_ge10 : nearest reference level AHEAD is >= 10 pts away (clear path)
- c_B_ahead_ge20 : nearest reference level AHEAD is >= 20 pts away (clear path)
- c_B_ahead_ge40 : nearest reference level AHEAD is >= 40 pts away (clear path)
- c_B_ahead_atr_ge0.5 : nearest reference level ahead >= 0.5 ATR(5m) away
- c_B_ahead_atr_ge1 : nearest reference level ahead >= 1 ATR(5m) away
- c_B_ahead_atr_ge2 : nearest reference level ahead >= 2 ATR(5m) away
- c_B_behind_le10 : a reference level sits within 10 pts BEHIND the entry (support)
- c_B_behind_le20 : a reference level sits within 20 pts BEHIND the entry (support)
- c_B_behind_le40 : a reference level sits within 40 pts BEHIND the entry (support)
- c_B_round100_clear20 : next round 100 (on the TRUE traded price = bar price + per-day offset, /mnt/l2/l2vast/_confl/offset_table.parquet) ahead is more than 20 pts away; unknown on roll-splice days
- c_B_round100_ahead_le10 : round 100 (true price) within 10 pts ahead
- c_B_round100_behind_le10 : round 100 (true price) within 10 pts behind (support)
- c_B_cl_ahead_cnt3_5 : NO cluster of >=3 levels (D=5pt) AHEAD inside the target distance (clear path)
- c_B_cl_ahead_cnt2_5 : NO cluster of >=2 levels (D=5pt) AHEAD inside the target distance
- c_B_cl_ahead_kinds2_5 : NO cluster with >=2 distinct KINDS (D=5pt) AHEAD inside the target distance
- c_B_cl_behind_cnt3_5 : cluster of >=3 levels (D=5pt) BEHIND the entry inside the stop distance (protected stop)
- c_B_cl_behind_kinds2_5 : cluster with >=2 distinct kinds (D=5pt) BEHIND the entry inside the stop distance
- c_B_cl_ahead_cnt3_10 : NO cluster of >=3 levels (D=10pt) AHEAD inside the target distance (clear path)
- c_B_cl_ahead_cnt2_10 : NO cluster of >=2 levels (D=10pt) AHEAD inside the target distance
- c_B_cl_ahead_kinds2_10 : NO cluster with >=2 distinct KINDS (D=10pt) AHEAD inside the target distance
- c_B_cl_behind_cnt3_10 : cluster of >=3 levels (D=10pt) BEHIND the entry inside the stop distance (protected stop)
- c_B_cl_behind_kinds2_10 : cluster with >=2 distinct kinds (D=10pt) BEHIND the entry inside the stop distance
- c_B_cl_ahead_cnt3_15 : NO cluster of >=3 levels (D=15pt) AHEAD inside the target distance (clear path)
- c_B_cl_ahead_cnt2_15 : NO cluster of >=2 levels (D=15pt) AHEAD inside the target distance
- c_B_cl_ahead_kinds2_15 : NO cluster with >=2 distinct KINDS (D=15pt) AHEAD inside the target distance
- c_B_cl_behind_cnt3_15 : cluster of >=3 levels (D=15pt) BEHIND the entry inside the stop distance (protected stop)
- c_B_cl_behind_kinds2_15 : cluster with >=2 distinct kinds (D=15pt) BEHIND the entry inside the stop distance
- c_B_cl_ahead_cnt3_a1 : NO cluster of >=3 levels (D=0.1atr) AHEAD inside the target distance (clear path)
- c_B_cl_ahead_cnt2_a1 : NO cluster of >=2 levels (D=0.1atr) AHEAD inside the target distance
- c_B_cl_ahead_kinds2_a1 : NO cluster with >=2 distinct KINDS (D=0.1atr) AHEAD inside the target distance
- c_B_cl_behind_cnt3_a1 : cluster of >=3 levels (D=0.1atr) BEHIND the entry inside the stop distance (protected stop)
- c_B_cl_behind_kinds2_a1 : cluster with >=2 distinct kinds (D=0.1atr) BEHIND the entry inside the stop distance
- c_B_cl_ahead_cnt3_a2 : NO cluster of >=3 levels (D=0.2atr) AHEAD inside the target distance (clear path)
- c_B_cl_ahead_cnt2_a2 : NO cluster of >=2 levels (D=0.2atr) AHEAD inside the target distance
- c_B_cl_ahead_kinds2_a2 : NO cluster with >=2 distinct KINDS (D=0.2atr) AHEAD inside the target distance
- c_B_cl_behind_cnt3_a2 : cluster of >=3 levels (D=0.2atr) BEHIND the entry inside the stop distance (protected stop)
- c_B_cl_behind_kinds2_a2 : cluster with >=2 distinct kinds (D=0.2atr) BEHIND the entry inside the stop distance
- c_B_cl_ahead_far : nearest >=2-level cluster (D=10pt) ahead is >= 30 pts away or absent
- c_A_trend_1m : EMA20 vs EMA50 of 1m closes on the trade side (up-trend for long)
- c_A_px_ema20_1m : last 1m close on the trade side of the 1m EMA20
- c_A_px_ema50_1m : last 1m close on the trade side of the 1m EMA50
- c_A_px_ema200_1m : last 1m close on the trade side of the 1m EMA200
- c_A_emaorder_1m : EMA20/50/200 ordered with the trade on 1m
- c_A_hhhl_1m : last two confirmed swing highs AND lows (fractal k=2) rising for long / falling for short on 1m
- c_A_swingbreak_1m : price beyond the last confirmed 1m swing high (long) / low (short)
- c_A_supertrend_1m : Supertrend(10,3) direction with the trade on 1m
- c_A_kc_mid_1m : price on the trade side of the Keltner midline (EMA20) on 1m
- c_A_kc_out_1m : price beyond the outer Keltner band (EMA20 +-1.5 ATR14) in the trade direction on 1m
- c_A_adx_rising_1m : ADX14 above its value 3 bars ago and above 20 on 1m
- c_A_di_1m : +DI vs -DI with the trade on 1m
- c_A_trend_3m : EMA20 vs EMA50 of 3m closes on the trade side (up-trend for long)
- c_A_px_ema20_3m : last 1m close on the trade side of the 3m EMA20
- c_A_px_ema50_3m : last 1m close on the trade side of the 3m EMA50
- c_A_px_ema200_3m : last 1m close on the trade side of the 3m EMA200
- c_A_emaorder_3m : EMA20/50/200 ordered with the trade on 3m
- c_A_hhhl_3m : last two confirmed swing highs AND lows (fractal k=2) rising for long / falling for short on 3m
- c_A_swingbreak_3m : price beyond the last confirmed 3m swing high (long) / low (short)
- c_A_supertrend_3m : Supertrend(10,3) direction with the trade on 3m
- c_A_kc_mid_3m : price on the trade side of the Keltner midline (EMA20) on 3m
- c_A_kc_out_3m : price beyond the outer Keltner band (EMA20 +-1.5 ATR14) in the trade direction on 3m
- c_A_adx_rising_3m : ADX14 above its value 3 bars ago and above 20 on 3m
- c_A_di_3m : +DI vs -DI with the trade on 3m
- c_A_trend_5m : EMA20 vs EMA50 of 5m closes on the trade side (up-trend for long)
- c_A_px_ema20_5m : last 1m close on the trade side of the 5m EMA20
- c_A_px_ema50_5m : last 1m close on the trade side of the 5m EMA50
- c_A_px_ema200_5m : last 1m close on the trade side of the 5m EMA200
- c_A_emaorder_5m : EMA20/50/200 ordered with the trade on 5m
- c_A_hhhl_5m : last two confirmed swing highs AND lows (fractal k=2) rising for long / falling for short on 5m
- c_A_swingbreak_5m : price beyond the last confirmed 5m swing high (long) / low (short)
- c_A_supertrend_5m : Supertrend(10,3) direction with the trade on 5m
- c_A_kc_mid_5m : price on the trade side of the Keltner midline (EMA20) on 5m
- c_A_kc_out_5m : price beyond the outer Keltner band (EMA20 +-1.5 ATR14) in the trade direction on 5m
- c_A_adx_rising_5m : ADX14 above its value 3 bars ago and above 20 on 5m
- c_A_di_5m : +DI vs -DI with the trade on 5m
- c_A_pbdepth_le0.5_5m : pullback depth (20-bar 5m leg extreme to price) <= 0.5 x ATR14(5m)
- c_A_pbdepth_le1_5m : pullback depth (20-bar 5m leg extreme to price) <= 1 x ATR14(5m)
- c_A_pbdepth_le1.5_5m : pullback depth (20-bar 5m leg extreme to price) <= 1.5 x ATR14(5m)
- c_A_firstpb_5m : first dip below(above) EMA9 since the last EMA20/50 flip on 5m, flip direction with the trade
- c_A_laterpb_5m : second or later dip on 5m since the last EMA20/50 flip, direction with the trade
- c_A_notext_le1_5m : NOT extended: signed distance of price beyond EMA20(5m) <= 1 ATR14(5m)
- c_A_notext_le1.5_5m : NOT extended: signed distance of price beyond EMA20(5m) <= 1.5 ATR14(5m)
- c_A_notext_le2_5m : NOT extended: signed distance of price beyond EMA20(5m) <= 2 ATR14(5m)
- c_A_trend_15m : EMA20 vs EMA50 of 15m closes on the trade side (up-trend for long)
- c_A_px_ema20_15m : last 1m close on the trade side of the 15m EMA20
- c_A_px_ema50_15m : last 1m close on the trade side of the 15m EMA50
- c_A_px_ema200_15m : last 1m close on the trade side of the 15m EMA200
- c_A_emaorder_15m : EMA20/50/200 ordered with the trade on 15m
- c_A_hhhl_15m : last two confirmed swing highs AND lows (fractal k=2) rising for long / falling for short on 15m
- c_A_swingbreak_15m : price beyond the last confirmed 15m swing high (long) / low (short)
- c_A_supertrend_15m : Supertrend(10,3) direction with the trade on 15m
- c_A_kc_mid_15m : price on the trade side of the Keltner midline (EMA20) on 15m
- c_A_kc_out_15m : price beyond the outer Keltner band (EMA20 +-1.5 ATR14) in the trade direction on 15m
- c_A_adx_rising_15m : ADX14 above its value 3 bars ago and above 20 on 15m
- c_A_di_15m : +DI vs -DI with the trade on 15m
- c_A_pbdepth_le0.5_15m : pullback depth (20-bar 15m leg extreme to price) <= 0.5 x ATR14(15m)
- c_A_pbdepth_le1_15m : pullback depth (20-bar 15m leg extreme to price) <= 1 x ATR14(15m)
- c_A_pbdepth_le1.5_15m : pullback depth (20-bar 15m leg extreme to price) <= 1.5 x ATR14(15m)
- c_A_firstpb_15m : first dip below(above) EMA9 since the last EMA20/50 flip on 15m, flip direction with the trade
- c_A_laterpb_15m : second or later dip on 15m since the last EMA20/50 flip, direction with the trade
- c_A_notext_le1_15m : NOT extended: signed distance of price beyond EMA20(15m) <= 1 ATR14(15m)
- c_A_notext_le1.5_15m : NOT extended: signed distance of price beyond EMA20(15m) <= 1.5 ATR14(15m)
- c_A_notext_le2_15m : NOT extended: signed distance of price beyond EMA20(15m) <= 2 ATR14(15m)
- c_A_trend_60m : EMA20 vs EMA50 of 60m closes on the trade side (up-trend for long)
- c_A_px_ema20_60m : last 1m close on the trade side of the 60m EMA20
- c_A_px_ema50_60m : last 1m close on the trade side of the 60m EMA50
- c_A_px_ema200_60m : last 1m close on the trade side of the 60m EMA200
- c_A_emaorder_60m : EMA20/50/200 ordered with the trade on 60m
- c_A_hhhl_60m : last two confirmed swing highs AND lows (fractal k=2) rising for long / falling for short on 60m
- c_A_swingbreak_60m : price beyond the last confirmed 60m swing high (long) / low (short)
- c_A_supertrend_60m : Supertrend(10,3) direction with the trade on 60m
- c_A_kc_mid_60m : price on the trade side of the Keltner midline (EMA20) on 60m
- c_A_kc_out_60m : price beyond the outer Keltner band (EMA20 +-1.5 ATR14) in the trade direction on 60m
- c_A_adx_rising_60m : ADX14 above its value 3 bars ago and above 20 on 60m
- c_A_di_60m : +DI vs -DI with the trade on 60m
- c_A_trend_1d : daily RTH-close EMA20 vs EMA50 (as of the prior RTH day) with the trade
- c_A_px_ema20_1d : price on the trade side of the daily EMA20 (prior RTH day)
- c_A_px_ema50_1d : price on the trade side of the daily EMA50 (prior RTH day)
- c_A_pd_candle_1d : prior RTH day closed up (long) / down (short)
- c_C_open_inside_value : today RTH open inside the prior RTH value area
- c_C_open_outside_with : RTH open outside prior value in the trade direction
- c_C_px_ppoc_side : price on the trade side of the prior day POC
- c_C_px_beyond_pva_with : price beyond the prior value area edge in the trade direction (above VAH long / below VAL short)
- c_C_px_inside_pva : price inside the prior day value area
- c_C_px_oPOC_side : price on the trade side of the overnight (Globex 18:00-09:30) POC; available from 09:30 ET
- c_C_px_beyond_ova_with : price beyond the overnight value area edge in the trade direction
- c_C_px_dpoc_side : price on the trade side of the DEVELOPING RTH POC
- c_C_px_beyond_dva_with : price beyond the developing RTH value area in the trade direction
- c_C_dpoc_migrating_with : developing POC moved >5 pts in the trade direction over the last 60 minutes
- c_C_npoc_ahead_le30 : NO naked POC within 30 pts ahead (clear path)
- c_C_npoc_ahead_le60 : NO naked POC within 60 pts ahead (clear path)
- c_C_npoc_behind : a naked POC lies within 40 pts behind (magnet/support)
- c_C_sp_ahead60 : NO prior-day single-print tail edge within 60 pts ahead
- c_C_poor_behind : prior day has a poor (unfinished) low behind a long / poor high behind a short
- c_C_poor_ahead : prior day poor high ahead of a long / poor low ahead of a short
- c_C_open_drive_with : open type drive (first 30 min RTH, known from 10:00 ET) in the trade direction
- c_C_open_testdrive_with : open type testdrive (first 30 min RTH, known from 10:00 ET) in the trade direction
- c_C_open_rejrev_with : open type rejrev (first 30 min RTH, known from 10:00 ET) in the trade direction
- c_C_open_auction_with : open type auction (first 30 min RTH, known from 10:00 ET) in the trade direction
- c_C_open_auction : open type = auction (balanced first 30 min)
- c_C_ib_broken_with : price beyond the initial balance (first 60 min RTH) in the trade direction (from 10:30 ET)
- c_C_ib_ext1.5 : price extended >= 1.5x the IB range in the trade direction
- c_C_ib_ext2 : price extended >= 2x the IB range in the trade direction
- c_C_ib_inside : price inside the initial balance
- c_C_px_c20poc_side : price on the trade side of the 20-day composite POC
- c_C_px_beyond_c20va_with : price beyond the 20-day composite value area in the trade direction
- c_C_px_c5poc_side : price on the trade side of the 5-day composite POC
- c_C_bal_breakout : prior day was a balance day (range < 0.8x 10-day median) and price now beyond its range in the trade direction
- c_C_look_above_fail_with : 'look below and fail' at prior-day low (long) / 'look above and fail' at prior-day high (short) within the last 60 min: trade AGREES with the failure
- c_C_look_above_fail_against : failed excursion beyond a prior-day extreme within 60 min that points AGAINST the trade
- c_D_sess_side : price on the trade side of the SESSION-anchored VWAP (anchor = session start: asia 18:00, london 02:00, pre 08:30, ny 09:30 ET)
- c_D_vwap_g1800_side : price on the trade side of VWAP anchored at 1800 ET
- c_D_vwap_rth0930_side : price on the trade side of VWAP anchored at th0930 ET
- c_D_weekly_side : price on the trade side of the weekly VWAP (anchor Sun 18:00 ET)
- c_D_monthly_side : price on the trade side of the monthly VWAP (anchor first bar of the label-day month)
- c_D_beyond_1sig : price beyond 1 sigma of session VWAP in the trade direction (volume-weighted std)
- c_D_beyond_2sig : price beyond 2 sigma of session VWAP in the trade direction (volume-weighted std)
- c_D_beyond_3sig : price beyond 3 sigma of session VWAP in the trade direction (volume-weighted std)
- c_D_inside_1sig : price within +-1 sigma of session VWAP
- c_D_dist_le1atr : |price - session VWAP| <= 1 ATR(5m)
- c_D_dist_le2atr : |price - session VWAP| <= 2 ATR(5m)
- c_D_slope15_with : session VWAP slope over 15 min with the trade
- c_D_slope60_with : session VWAP slope over 60 min with the trade
- c_D_avwap_dlow_side : price on the trade side of VWAP anchored at the label-day LOW so far
- c_D_avwap_dhigh_side : price on the trade side of VWAP anchored at the label-day HIGH so far
- c_D_avwap_event_side : price on the trade side of VWAP anchored at the last scheduled release (within 24 h)
- c_E_ret5_with : last 5-minute return with the trade
- c_E_ret5_strong : last 5-minute return with the trade by more than 0.5 ATR(5m)
- c_E_ret15_with : last 15-minute return with the trade
- c_E_ret15_strong : last 15-minute return with the trade by more than 0.5 ATR(5m)
- c_E_ret30_with : last 30-minute return with the trade
- c_E_ret30_strong : last 30-minute return with the trade by more than 0.5 ATR(5m)
- c_E_rv_ge0.8 : realized vol (30 min) >= 0.8 x its median at this clock time over the prior 20 days
- c_E_rv_ge1.2 : realized vol (30 min) >= 1.2 x its median at this clock time over the prior 20 days
- c_E_rv_ge1.5 : realized vol (30 min) >= 1.5 x its median at this clock time over the prior 20 days
- c_E_rangeused_le0.5 : label-day range so far <= 0.5 x the 10-day median full-day range (room left)
- c_E_rangeused_le0.8 : label-day range so far <= 0.8 x the 10-day median full-day range (room left)
- c_E_rangeused_le1 : label-day range so far <= 1 x the 10-day median full-day range (room left)
- c_E_bb_squeeze_5m : Bollinger(20) width on 5m at or below its 20th percentile (trailing 500 bars)
- c_E_bb_expand_5m : Bollinger(20) width on 5m at or above its 80th percentile
- c_E_er30_ge0.3_with : efficiency ratio (30 min, 5m bars) >= 0.3 and the net move is with the trade
- c_E_er30_ge0.5_with : efficiency ratio (30 min, 5m bars) >= 0.5 and the net move is with the trade
- c_E_er60_ge0.3_with : efficiency ratio (60 min, 5m bars) >= 0.3 and the net move is with the trade
- c_E_er60_ge0.5_with : efficiency ratio (60 min, 5m bars) >= 0.5 and the net move is with the trade
- c_K_no_release_next15 : NO scheduled major release (FOMC CPI NFP PPI PCE RETAIL GDP ISM) within the next 15 min
- c_K_no_release_next30 : NO scheduled major release (FOMC CPI NFP PPI PCE RETAIL GDP ISM) within the next 30 min
- c_K_no_release_next60 : NO scheduled major release (FOMC CPI NFP PPI PCE RETAIL GDP ISM) within the next 60 min
- c_K_post_release_15 : a major scheduled release occurred in the last 15 min
- c_K_post_release_30 : a major scheduled release occurred in the last 30 min
- c_K_post_release_60 : a major scheduled release occurred in the last 60 min
- c_K_event_day : label day has a major scheduled release
- c_K_day_before_event : next calendar/business day has a major scheduled release
- c_K_day_after_event : previous day had a major scheduled release
- c_K_fomc_day : label day is an FOMC announcement day
- c_K_fomc_next : day before an FOMC announcement
- c_K_fomc_prev : day after an FOMC announcement
- c_K_dow_mon : label day is mon
- c_K_dow_tue : label day is tue
- c_K_dow_wed : label day is wed
- c_K_dow_thu : label day is thu
- c_K_dow_fri : label day is fri
- c_K_opex_week : label day lies in the monthly opex week (15th-21st calendar window containing the 3rd Friday)
- c_K_opex_day : label day is the 3rd Friday
- c_K_month_end2 : label day is one of the last 2 business days of the month
- c_K_month_start3 : label day is one of the first 3 business days of the month
- c_K_quarter_end_week : last week of a calendar quarter
- c_K_first30 : signal in the first 30 minutes of its session
- c_K_last30 : signal in the last 30 minutes of its session
- c_K_third0 : signal in third 0 of its session (best/worst third is selected in step 3 from history, walk-forward)
- c_K_third1 : signal in third 1 of its session (best/worst third is selected in step 3 from history, walk-forward)
- c_K_third2 : signal in third 2 of its session (best/worst third is selected in step 3 from history, walk-forward)
- c_K_hour_00 : signal in the ET clock hour 00
- c_K_hour_01 : signal in the ET clock hour 01
- c_K_hour_02 : signal in the ET clock hour 02
- c_K_hour_03 : signal in the ET clock hour 03
- c_K_hour_04 : signal in the ET clock hour 04
- c_K_hour_05 : signal in the ET clock hour 05
- c_K_hour_06 : signal in the ET clock hour 06
- c_K_hour_07 : signal in the ET clock hour 07
- c_K_hour_08 : signal in the ET clock hour 08
- c_K_hour_09 : signal in the ET clock hour 09
- c_K_hour_10 : signal in the ET clock hour 10
- c_K_hour_11 : signal in the ET clock hour 11
- c_K_hour_12 : signal in the ET clock hour 12
- c_K_hour_13 : signal in the ET clock hour 13
- c_K_hour_14 : signal in the ET clock hour 14
- c_K_hour_15 : signal in the ET clock hour 15
- c_K_hour_16 : signal in the ET clock hour 16
- c_K_hour_17 : signal in the ET clock hour 17
- c_K_hour_18 : signal in the ET clock hour 18
- c_K_hour_19 : signal in the ET clock hour 19
- c_K_hour_20 : signal in the ET clock hour 20
- c_K_hour_21 : signal in the ET clock hour 21
- c_K_hour_22 : signal in the ET clock hour 22
- c_K_hour_23 : signal in the ET clock hour 23
- c_L_first_entry : this is the book's first entry of the session
- c_L_entry_le2 : this is the book's 1st or 2nd entry in the session
- c_L_first_not_loser : the book's first trade of the session was not a (closed) loser
- c_L_first_won : the book's first trade of the session closed a winner
- c_L_sess_net_ge0 : stack closed net in this session >= 0 R ($1,200)
- c_L_sess_net_ge0.5 : stack closed net in this session >= 0.5 R ($1,200)
- c_L_sess_net_ge1 : stack closed net in this session >= 1 R ($1,200)
- c_L_sess_net_gt_neg05 : stack closed net in this session > -0.5 R
- c_L_day_net_ge0 : stack closed net on the label day >= 0
- c_L_day_net_gt_neg1 : stack closed net on the label day > -1 R
- c_L_no_ss_loser30 : no same-side loser closed in the last 30 min (any book)
- c_L_no_ss_loser60 : no same-side loser closed in the last 60 min (any book)
- c_L_other_same : another book is already in on the SAME side
- c_L_other_opp_none : no book is in on the OPPOSITE side
- c_L_flat_stack : no open position in the stack
- c_L_last_tgt : the book's last closed trade hit its target
- c_L_gap30 : at least 30 min since the book last exited (fresh vs quick re-entry)
- c_L_ctx_fresh : entry context FRESH (not chasing, entry no <= 2, >= 30 min since the book last exited)
- c_L_ctx_chasing : entry context CHASING (chase_k > 1)

## defs_AEL.json

## defs_D4.json
- c_D4_ema21_px_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema21_px_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema21_px_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema21_px_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema21_px_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema8_px_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema8_px_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema8_px_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema8_px_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema8_px_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sma50_px_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sma50_px_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sma50_px_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sma50_px_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sma50_px_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_rsi14_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_rsi14_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_rsi14_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_rsi14_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_rsi14_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_macd12_26_9_hist_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_macd12_26_9_hist_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_macd12_26_9_hist_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_macd12_26_9_hist_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_macd12_26_9_hist_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_cci14_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_cci14_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_cci14_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_cci14_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_cci14_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_stoch14_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_stoch14_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_stoch14_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_stoch14_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_stoch14_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_supertrend_10_3_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_supertrend_10_3_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_supertrend_10_3_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_supertrend_10_3_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_supertrend_10_3_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_di14_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_di14_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_di14_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_di14_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_di14_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_linreg_slope20_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_linreg_slope20_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_linreg_slope20_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_linreg_slope20_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_linreg_slope20_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_donchian20_pos_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_donchian20_pos_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_donchian20_pos_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_donchian20_pos_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_donchian20_pos_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_psar_0.02_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_psar_0.02_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_psar_0.02_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_psar_0.02_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_psar_0.02_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ichi_std_cloud_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ichi_std_cloud_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ichi_std_cloud_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ichi_std_cloud_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ichi_std_cloud_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_trendcolor_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_trendcolor_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_trendcolor_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_trendcolor_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_trendcolor_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sqz_hist_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sqz_hist_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sqz_hist_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sqz_hist_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_sqz_hist_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_wave_mid_hist_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_wave_mid_hist_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_wave_mid_hist_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_wave_mid_hist_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_wave_mid_hist_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema_8_21_34_stack_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema_8_21_34_stack_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema_8_21_34_stack_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema_8_21_34_stack_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_ema_8_21_34_stack_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_kama21_px_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_kama21_px_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_kama21_px_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_kama21_px_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_kama21_px_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_hma21_px_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_hma21_px_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_hma21_px_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_hma21_px_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_hma21_px_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_vwma21_px_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_vwma21_px_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_vwma21_px_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_vwma21_px_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_vwma21_px_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_boll20_pctb_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_boll20_pctb_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_boll20_pctb_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_boll20_pctb_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_boll20_pctb_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_keltner20_pos_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_keltner20_pos_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_keltner20_pos_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_keltner20_pos_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_keltner20_pos_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_aroon25_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_aroon25_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_aroon25_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_aroon25_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_aroon25_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_tenx_bar_n4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_tenx_bar_n5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_tenx_bar_n6 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_tenx_bar_top : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_tenx_bar_veto : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_fam_mean_ge3 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_fam_mean_ge4 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_fam_mean_ge5 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_fam_topshare_ge50 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_fam_topshare_ge70 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_fam_conflict_le10 : D4 multi-timeframe alignment (see build_d4.py header)
- c_D4_fam_conflict_le25 : D4 multi-timeframe alignment (see build_d4.py header)

## Category M indicators (name | family | formula status)
- m_adline_<tf>_<cond> : volume | public
- m_adx14_<tf>_<cond> : trend | public
- m_adx21_<tf>_<cond> : trend | public
- m_adx7_<tf>_<cond> : trend | public
- m_ao_<tf>_<cond> : osc | public
- m_aroon14_<tf>_<cond> : trend | public
- m_aroon25_<tf>_<cond> : trend | public
- m_aroon50_<tf>_<cond> : trend | public
- m_atr_pct100_<tf>_<cond> : vol | public
- m_atr_pct250_<tf>_<cond> : vol | public
- m_boll10_pctb_<tf>_<cond> : vol | public
- m_boll10_walk_<tf>_<cond> : vol | approx: 3-bar sum of closes outside band
- m_boll10_width_pct_<tf>_<cond> : vol | public
- m_boll20_pctb_<tf>_<cond> : vol | public
- m_boll20_walk_<tf>_<cond> : vol | approx: 3-bar sum of closes outside band
- m_boll20_width_pct_<tf>_<cond> : vol | public
- m_boll40_pctb_<tf>_<cond> : vol | public
- m_boll40_walk_<tf>_<cond> : vol | approx: 3-bar sum of closes outside band
- m_boll40_width_pct_<tf>_<cond> : vol | public
- m_cci14_<tf>_<cond> : osc | public
- m_cci14_zeroreject_<tf>_<cond> : osc | public CCI; reject pattern = approx
- m_cci20_<tf>_<cond> : osc | public
- m_cci20_zeroreject_<tf>_<cond> : osc | public CCI; reject pattern = approx
- m_cci50_<tf>_<cond> : osc | public
- m_cci50_zeroreject_<tf>_<cond> : osc | public CCI; reject pattern = approx
- m_cmf10_<tf>_<cond> : volume | public
- m_cmf20_<tf>_<cond> : volume | public
- m_cmo14_<tf>_<cond> : osc | public
- m_cmo21_<tf>_<cond> : osc | public
- m_cmo9_<tf>_<cond> : osc | public
- m_compound_setup_<tf>_<cond> : simpler | APPROXIMATION of Compound Breakout setup: count of squeeze-on, NR7, volume dry-up, tight EMAs, inside bar (0-5)
- m_darvas_break_<tf>_<cond> : simpler | APPROXIMATION of Darvas box: 20-bar high/low unchanged for 3 bars = box; close beyond the box edge
- m_demarker14_<tf>_<cond> : osc | public
- m_demarker21_<tf>_<cond> : osc | public
- m_demarker7_<tf>_<cond> : osc | public
- m_di14_<tf>_<cond> : trend | public
- m_di21_<tf>_<cond> : trend | public
- m_di7_<tf>_<cond> : trend | public
- m_divergent_bar_<tf>_<cond> : simpler | APPROXIMATION of Divergent Bars: new low closing in the top third (bull) / new high closing in the bottom third (bear)
- m_donchian10_pos_<tf>_<cond> : trend | public
- m_donchian10_width_<tf>_<cond> : vol | public
- m_donchian20_pos_<tf>_<cond> : trend | public
- m_donchian20_width_<tf>_<cond> : vol | public
- m_donchian50_pos_<tf>_<cond> : trend | public
- m_donchian50_width_<tf>_<cond> : vol | public
- m_early_in_out_<tf>_<cond> : simpler | APPROXIMATION of Early In-N-Out: MACD(12,26,9) histogram slope turns with volume > 1.2x average
- m_ema100_px_<tf>_<cond> : trend | public
- m_ema200_px_<tf>_<cond> : trend | public
- m_ema21_hold_<tf>_<cond> : simpler | approx: last 3 bars all on one side of the 21 EMA (no bar pierced it)
- m_ema21_px_<tf>_<cond> : trend | public
- m_ema34_px_<tf>_<cond> : trend | public
- m_ema50_px_<tf>_<cond> : trend | public
- m_ema8_px_<tf>_<cond> : trend | public
- m_ema_8_21_34_stack_<tf>_<cond> : simpler | public (8/21/34 EMA ordering)
- m_ema_8_21_stack_<tf>_<cond> : simpler | public (8 over 21; USER_SET_V0 #5)
- m_ema_ribbon_<tf>_<cond> : simpler | PUBLIC-style EMA ribbon (8,13,21,34,55,89): +1 = fully stacked up
- m_ema_stack_fast_<tf>_<cond> : trend | public
- m_ema_stack_slow_<tf>_<cond> : trend | public
- m_eom14_<tf>_<cond> : volume | approx: ease of movement
- m_fisher10_<tf>_<cond> : osc | approx: smoothed Fisher
- m_fisher20_<tf>_<cond> : osc | approx: smoothed Fisher
- m_fisher5_<tf>_<cond> : osc | approx: smoothed Fisher
- m_force13_<tf>_<cond> : volume | public
- m_ha_run_<tf>_<cond> : pattern | public Heikin-Ashi colour run (signed length)
- m_hilo_range_osc_<tf>_<cond> : simpler | APPROXIMATION: position of close in the 20-bar high-low range, -1..+1
- m_hma100_px_<tf>_<cond> : trend | public
- m_hma200_px_<tf>_<cond> : trend | public
- m_hma21_px_<tf>_<cond> : trend | public
- m_hma34_px_<tf>_<cond> : trend | public
- m_hma50_px_<tf>_<cond> : trend | public
- m_hma8_px_<tf>_<cond> : trend | public
- m_hma_stack_fast_<tf>_<cond> : trend | public
- m_hma_stack_slow_<tf>_<cond> : trend | public
- m_holb_lohb_<tf>_<cond> : simpler | APPROXIMATION of HOLB/LOHB: close beyond the high of the lowest-bar (long) / low of the highest-bar (short) of the last 10 bars
- m_hv_pct10_<tf>_<cond> : vol | public
- m_hv_pct20_<tf>_<cond> : vol | public
- m_hv_pct50_<tf>_<cond> : vol | public
- m_ichi_fast_cloud_<tf>_<cond> : trend | public (cloud at t uses spans computed 13 bars earlier: causal)
- m_ichi_fast_lag_<tf>_<cond> : trend | public: close vs price 13 bars ago (lagging line clear)
- m_ichi_fast_tkkj_<tf>_<cond> : trend | public
- m_ichi_slow_cloud_<tf>_<cond> : trend | public (cloud at t uses spans computed 30 bars earlier: causal)
- m_ichi_slow_lag_<tf>_<cond> : trend | public: close vs price 30 bars ago (lagging line clear)
- m_ichi_slow_tkkj_<tf>_<cond> : trend | public
- m_ichi_std_cloud_<tf>_<cond> : trend | public (cloud at t uses spans computed 26 bars earlier: causal)
- m_ichi_std_lag_<tf>_<cond> : trend | public: close vs price 26 bars ago (lagging line clear)
- m_ichi_std_tkkj_<tf>_<cond> : trend | public
- m_kama100_px_<tf>_<cond> : trend | public
- m_kama200_px_<tf>_<cond> : trend | public
- m_kama21_px_<tf>_<cond> : trend | public
- m_kama34_px_<tf>_<cond> : trend | public
- m_kama50_px_<tf>_<cond> : trend | public
- m_kama8_px_<tf>_<cond> : trend | public
- m_kama_stack_fast_<tf>_<cond> : trend | public
- m_kama_stack_slow_<tf>_<cond> : trend | public
- m_keltner10_pos_<tf>_<cond> : vol | public
- m_keltner20_pos_<tf>_<cond> : vol | public
- m_keltner40_pos_<tf>_<cond> : vol | public
- m_launch_pad_tight_<tf>_<cond> : simpler | APPROXIMATION of Launch Pad: EMA 8/21/34 bunched within 0.3 ATR (unsigned state)
- m_linreg_chan10_<tf>_<cond> : trend | public
- m_linreg_chan20_<tf>_<cond> : trend | public
- m_linreg_chan50_<tf>_<cond> : trend | public
- m_linreg_slope10_<tf>_<cond> : trend | public
- m_linreg_slope20_<tf>_<cond> : trend | public
- m_linreg_slope50_<tf>_<cond> : trend | public
- m_macd12_26_9_hist_<tf>_<cond> : osc | public
- m_macd12_26_9_line_<tf>_<cond> : osc | public
- m_macd19_39_9_hist_<tf>_<cond> : osc | public
- m_macd19_39_9_line_<tf>_<cond> : osc | public
- m_macd8_17_9_hist_<tf>_<cond> : osc | public
- m_macd8_17_9_line_<tf>_<cond> : osc | public
- m_mfi14_<tf>_<cond> : osc | public
- m_mfi21_<tf>_<cond> : osc | public
- m_mfi7_<tf>_<cond> : osc | public
- m_mom10_<tf>_<cond> : osc | public
- m_mom20_<tf>_<cond> : osc | public
- m_mom5_<tf>_<cond> : osc | public
- m_momo_thrust_<tf>_<cond> : simpler | APPROXIMATION of Monster Momo: 5-bar move > 1.5 ATR14 with volume > 1.5x its 20-bar mean
- m_moxie_pop_<tf>_<cond> : simpler | APPROXIMATION of Moxie: 5-bar change beyond 2 sigma of its trailing 100-bar distribution (pop / drop)
- m_multicross_<tf>_<cond> : simpler | APPROXIMATION of Multi Cross: sum of signs of EMA 5/13, 8/21, 13/34, 21/55 (+-4 = all agree)
- m_narrow_range_nr4_<tf>_<cond> : pattern | prior bar was the narrowest of 4
- m_obv_<tf>_<cond> : volume | public OBV vs its EMA20
- m_pat_engulf_<tf>_<cond> : pattern | public
- m_pat_inside_<tf>_<cond> : pattern | public
- m_pat_outside_<tf>_<cond> : pattern | public
- m_pat_pin_<tf>_<cond> : pattern | approx: long wick > 2x body, opposite wick < body
- m_porsche_dot_<tf>_<cond> : simpler | APPROXIMATION of Porsche Dots: close crosses the EMA21 with ADX14 > 20
- m_psar_0.01_<tf>_<cond> : trend | public
- m_psar_0.02_<tf>_<cond> : trend | public
- m_psar_0.03_<tf>_<cond> : trend | public
- m_range_expansion_<tf>_<cond> : pattern | public
- m_ready_aim_fire_<tf>_<cond> : simpler | APPROXIMATION of Ready-Aim-Fire: setup (squeeze on within 10 bars) + confirmation (histogram sign) + trigger (close beyond prior bar extreme) agreeing
- m_rh_grab_<tf>_<cond> : simpler | APPROXIMATION of GRaB candles: whole bar beyond the 34 EMA wave
- m_rh_propulsion_<tf>_<cond> : simpler | APPROXIMATION of Propulsion Dots: close leaves the 34 wave in the last 3 bars (fresh cross)
- m_rh_wave34_<tf>_<cond> : simpler | PUBLIC idea (34 EMA of high / low wave); close above the high-EMA = +1, below the low-EMA = -1, inside = 0
- m_roc10_<tf>_<cond> : osc | public
- m_roc20_<tf>_<cond> : osc | public
- m_roc5_<tf>_<cond> : osc | public
- m_rsi14_<tf>_<cond> : osc | public
- m_rsi2_<tf>_<cond> : osc | public
- m_rsi21_<tf>_<cond> : osc | public
- m_rsi7_<tf>_<cond> : osc | public
- m_sma100_px_<tf>_<cond> : trend | public
- m_sma200_px_<tf>_<cond> : trend | public
- m_sma21_px_<tf>_<cond> : trend | public
- m_sma34_px_<tf>_<cond> : trend | public
- m_sma50_px_<tf>_<cond> : trend | public
- m_sma8_px_<tf>_<cond> : trend | public
- m_sma_stack_fast_<tf>_<cond> : trend | public
- m_sma_stack_slow_<tf>_<cond> : trend | public
- m_sqz_colour_<tf>_<cond> : simpler | PUBLIC four-colour histogram: >0 rising (2) / >0 falling (1) / <0 falling (-2) / <0 rising (-1); side = sign
- m_sqz_fired_<tf>_<cond> : simpler | public: squeeze released this bar; direction from histogram sign
- m_sqz_fresh5_<tf>_<cond> : simpler | PUBLIC squeeze release within the last 5 bars; sign = histogram direction at release
- m_sqz_hist_<tf>_<cond> : simpler | public formula (TTM-style squeeze histogram: linreg of close minus avg(avg(HH,LL),SMA20), length 20)
- m_sqz_on_<tf>_<cond> : simpler | public: BB(20,2) inside KC(20,1.5) [Keltner ATR = simple 20-bar ATR]
- m_sqz_strength_<tf>_<cond> : simpler | approx: number of Keltner widths (1.0, 1.5, 2.0) that contain the Bollinger bands (0-3)
- m_sqzpro_fire_any_<tf>_<cond> : simpler | APPROXIMATION: released from any of the three squeeze strengths, direction = histogram sign
- m_sqzpro_fire_tight_<tf>_<cond> : simpler | APPROXIMATION of Squeeze Pro: released from the tightest (KC 1.0) squeeze, direction = histogram sign
- m_stoch14_<tf>_<cond> : osc | public
- m_stoch21_<tf>_<cond> : osc | public
- m_stoch8_<tf>_<cond> : osc | public
- m_stochrsi14_<tf>_<cond> : osc | public
- m_stochrsi21_<tf>_<cond> : osc | public
- m_stochrsi8_<tf>_<cond> : osc | public
- m_supertrend_10_3_<tf>_<cond> : trend | public
- m_supertrend_14_4_<tf>_<cond> : trend | public
- m_supertrend_7_2_<tf>_<cond> : trend | public
- m_tenx_bar_<tf>_<cond> : simpler | APPROXIMATION of 10X Bars: ADX14 > 20 and DI sign (trending up / trending down / no trend)
- m_threebar_pivot_<tf>_<cond> : simpler | approx: three-bar reversal pivot (D7 cf_pattern_threebar form)
- m_top_hat_<tf>_<cond> : simpler | APPROXIMATION of Top Hat: inside bar then close beyond the mother bar in the EMA8/21 trend direction
- m_tr3ndy_flip_<tf>_<cond> : simpler | APPROXIMATION of Tr3ndy turn: Supertrend(10,2) flip this bar
- m_trend_osc_<tf>_<cond> : simpler | APPROXIMATION of Trend Oscillator: (EMA8 - EMA34) / ATR14
- m_trend_spark_<tf>_<cond> : simpler | APPROXIMATION of Trend Spark: close beyond the prior 3-bar extreme and on the right side of EMA8
- m_trendcolor_<tf>_<cond> : simpler | approx: close vs average of SMA5(high) and SMA5(low)
- m_trix15_<tf>_<cond> : osc | public
- m_trix30_<tf>_<cond> : osc | public
- m_trix8_<tf>_<cond> : osc | public
- m_true_lows_<tf>_<cond> : simpler | APPROXIMATION of True Lows/Highs: 10-bar extreme bar that closes in the recovered half
- m_tsc_strong_<tf>_<cond> : simpler | APPROXIMATION of Trend Strength Candles: ADX14 > 30 and DI sign
- m_tsc_vstrong_<tf>_<cond> : simpler | APPROXIMATION: ADX14 > 40 and DI sign
- m_turbo_vzo_<tf>_<cond> : simpler | PUBLIC formula of the Volume Zone Oscillator (14); Turbo variant thresholds are an APPROXIMATION
- m_uo_<tf>_<cond> : osc | public
- m_updown_vol20_<tf>_<cond> : volume | public
- m_vol_avg_rel_<tf>_<cond> : simpler | PUBLIC: volume / its 20-bar average
- m_volosc_<tf>_<cond> : volume | public
- m_vortex14_<tf>_<cond> : trend | public
- m_vortex21_<tf>_<cond> : trend | public
- m_vortex7_<tf>_<cond> : trend | public
- m_vwma100_px_<tf>_<cond> : trend | public
- m_vwma200_px_<tf>_<cond> : trend | public
- m_vwma21_px_<tf>_<cond> : trend | public
- m_vwma34_px_<tf>_<cond> : trend | public
- m_vwma50_px_<tf>_<cond> : trend | public
- m_vwma8_px_<tf>_<cond> : trend | public
- m_vwma_stack_fast_<tf>_<cond> : trend | public
- m_vwma_stack_slow_<tf>_<cond> : trend | public
- m_vwmacd_<tf>_<cond> : volume | public: volume-weighted MACD (EMA(price*vol)/EMA(vol) 12 minus 26)
- m_wave_agree_<tf>_<cond> : simpler | approx: all three wave histograms same sign
- m_wave_long_hist_<tf>_<cond> : simpler | approx: MACD(24,52,18) histogram
- m_wave_mid_hist_<tf>_<cond> : simpler | approx: MACD(12,26,9) histogram
- m_wave_short_hist_<tf>_<cond> : simpler | approx: MACD(5,13,5) histogram
- m_willr14_<tf>_<cond> : osc | public
- m_willr21_<tf>_<cond> : osc | public
- m_willr7_<tf>_<cond> : osc | public

## defs_S.json
- c_S_multisqz_on_ge2 : Multi Squeeze: >= 2 of the 6 timeframes (1,3,5,15,30,60) in a squeeze at the signal (PUBLIC squeeze rule)
- c_S_multisqz_on_ge3 : Multi Squeeze: >= 3 of the 6 timeframes (1,3,5,15,30,60) in a squeeze at the signal (PUBLIC squeeze rule)
- c_S_multisqz_on_ge4 : Multi Squeeze: >= 4 of the 6 timeframes (1,3,5,15,30,60) in a squeeze at the signal (PUBLIC squeeze rule)
- c_S_multisqz_fired_ge1 : Multi Squeeze fired: >= 1 timeframes fired a squeeze in the trade direction within the last 3 bars
- c_S_multisqz_fired_ge2 : Multi Squeeze fired: >= 2 timeframes fired a squeeze in the trade direction within the last 3 bars
- c_S_multisqz_fired_ge3 : Multi Squeeze fired: >= 3 timeframes fired a squeeze in the trade direction within the last 3 bars
- c_S_triple_sqz : Triple Squeeze: 5m, 15m and 60m all in a squeeze (APPROXIMATION of the vendor definition)
- c_S_sqz_rotation : Squeeze Rotation (APPROXIMATION): a squeeze fired with the trade on 1/3/5m while 15m or 60m is still in a squeeze
- c_S_sqzstat_pos_5m : squeeze statistics (walk-forward): the last 20 RESOLVED fired squeezes on 5m moved on average >0 pts in their fired direction over the next 12 bars
- c_S_sqzstat_pos_15m : squeeze statistics (walk-forward): the last 20 RESOLVED fired squeezes on 15m moved on average >0 pts in their fired direction over the next 12 bars
- c_S_pivot_P_side : price on the trade side of the daily floor-trader pivot P (prior RTH day H,L,C) [PUBLIC]
- c_S_pivot_R1S1_beyond : price beyond daily R1 (long) / S1 (short) [PUBLIC]
- c_S_pivot_R2S2_beyond : price beyond daily R2 / S2
- c_S_pivot_clear_10 : no daily pivot level within 10 pts ahead
- c_S_pivot_clear_20 : no daily pivot level within 20 pts ahead
- c_S_cama_H3L3_beyond : Camarilla H3 / L3 beyond in the trade direction [PUBLIC]
- c_S_cama_inside_H3L3 : price inside Camarilla H3-L3 (range day expectation)
- c_S_pd_fib50_side : price on the trade side of the prior day's 50% level
- c_S_fib_pullback_38_62 : trade enters after a 38-62% retracement of the last 15m swing leg (leg = last confirmed swing high - low; uses direction of the trade) [APPROXIMATION]
- c_S_measured_move_room : a measured move (last 15m swing leg length from here) reaches at least the target distance [APPROXIMATION]
- c_S_vwapmax_ge4 : VWAP Max (APPROXIMATION): price on the trade side of >= 4 of 6 anchored VWAPs (session, weekly, monthly, day-low, day-high, last event)
- c_S_vwapmax_ge5 : VWAP Max (APPROXIMATION): price on the trade side of >= 5 of 6 anchored VWAPs (session, weekly, monthly, day-low, day-high, last event)
- c_S_dpmr_used_le0.6 : DPMR (APPROXIMATION): label-day range so far <= 0.6 x the median range-so-far at the same clock time over the prior 20 days
- c_S_dpmr_used_le0.9 : DPMR (APPROXIMATION): label-day range so far <= 0.9 x the median range-so-far at the same clock time over the prior 20 days
- c_S_dpmr_used_le1.2 : DPMR (APPROXIMATION): label-day range so far <= 1.2 x the median range-so-far at the same clock time over the prior 20 days
- c_S_hpmr_used_le0.8 : HPMR (APPROXIMATION): last-60-min range <= 0.8 x the median at the same clock time (prior 20 days)
- c_S_hpmr_used_le1.2 : HPMR (APPROXIMATION): last-60-min range <= 1.2 x the median at the same clock time (prior 20 days)
- c_S_weekrange_used_le0.5 : weekly stats (APPROXIMATION): week range so far <= 0.5 x median full-week range of the prior 8 weeks
- c_S_weekrange_used_le0.8 : weekly stats (APPROXIMATION): week range so far <= 0.8 x median full-week range of the prior 8 weeks
- c_S_atrmove_le0.5 : ATR Move (APPROXIMATION): signed move from the prior RTH close in the trade direction <= 0.5 x 14-day mean RTH range (room left)
- c_S_atrmove_le1 : ATR Move (APPROXIMATION): signed move from the prior RTH close in the trade direction <= 1 x 14-day mean RTH range (room left)
- c_S_corr60_es_ge0.7 : Power Correlations: 60-minute rolling correlation of NQ and ES 1m returns >= 0.7
- c_S_conf15_es : ES 15-minute change in the trade direction (confirmation)
- c_S_corr60_rty_ge0.7 : Power Correlations: 60-minute rolling correlation of NQ and RTY 1m returns >= 0.7
- c_S_conf15_rty : RTY 15-minute change in the trade direction (confirmation)

## defs_T.json
- c_T_tick_close_side : NYSE TICK last 1m close on the trade side of zero (RTH only)
- c_T_tick_ma5_side : TICK 5-min mean on the trade side of zero
- c_T_tick_ma15_side : TICK 15-min mean on the trade side of zero
- c_T_tick_ma15_strong : TICK 15-min mean beyond 150 on the trade side
- c_T_tick_rising : TICK 5-min mean higher (long) / lower (short) than 15 min ago
- c_T_tick_ext_with_600 : TICK printed beyond 600 on the trade side within the last 15 min
- c_T_tick_no_ext_against_600 : NO TICK extreme beyond 600 against the trade within the last 15 min
- c_T_tick_ext_with_800 : TICK printed beyond 800 on the trade side within the last 15 min
- c_T_tick_no_ext_against_800 : NO TICK extreme beyond 800 against the trade within the last 15 min
- c_T_tick_ext_with_1000 : TICK printed beyond 1000 on the trade side within the last 15 min
- c_T_tick_no_ext_against_1000 : NO TICK extreme beyond 1000 against the trade within the last 15 min
- c_T_tick_cum_side : cumulative TICK (sum of 1m closes since the RTH open) on the trade side of zero
- c_T_tick_cum_slope : cumulative TICK rising (long) / falling (short) over 15 min
- c_T_tick_no_div : no TICK divergence against the trade: price made a new 30-min extreme in the trade direction while the TICK 30-min extreme did not confirm

## defs_U.json
- c_U_1 : USER_SET_V0 item 1: CCI14 5m and 15m same side of zero (unknown = no)
- c_U_2 : USER_SET_V0 item 2: price on trade side of session open and of the last-crossed prior-session level (unknown = no)
- c_U_3 : USER_SET_V0 item 3: prior-day POC side + outside/leaving prior VA + no HVN between entry and target (unknown = no)
- c_U_4 : USER_SET_V0 item 4: squeeze fired with trade (5m or 15m, last 10 bars) or 5m histogram rising with trade (unknown = no)
- c_U_5 : USER_SET_V0 item 5: 5m EMA8/EMA21 stacked with the trade (unknown = no)
- c_U_all5 : USER_SET_V0 all 5
- c_U_ge4 : USER_SET_V0 at least 4 of 5
- c_U_ge3 : USER_SET_V0 at least 3 of 5

## defs_V.json
- c_V_voodoo_clear15 : Voodoo-lines APPROXIMATION: no HVN (5 prior RTH profiles) / 60m swing level within 15 pts ahead
- c_V_voodoo_support10 : Voodoo-lines APPROXIMATION: such a level within 10 pts behind the entry
- c_V_qp_beyond_with : QuantPivots APPROXIMATION: price beyond the projected range edge (week open +- 0.5 x mean weekly range of 8 weeks) in the trade direction
- c_V_qp_inside : QuantPivots APPROXIMATION: price inside the projected range
- c_V_qp_room30 : QuantPivots APPROXIMATION: >= 30 pts of room to the projected edge ahead

## defs_Z.json
- c_Z_moon_oct0 : NONSENSE control (synodic phase octant 0 of 8 at sig_ts); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_oct1 : NONSENSE control (synodic phase octant 1 of 8 at sig_ts); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_oct2 : NONSENSE control (synodic phase octant 2 of 8 at sig_ts); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_oct3 : NONSENSE control (synodic phase octant 3 of 8 at sig_ts); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_oct4 : NONSENSE control (synodic phase octant 4 of 8 at sig_ts); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_oct5 : NONSENSE control (synodic phase octant 5 of 8 at sig_ts); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_oct6 : NONSENSE control (synodic phase octant 6 of 8 at sig_ts); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_oct7 : NONSENSE control (synodic phase octant 7 of 8 at sig_ts); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_wax : NONSENSE control (moon waxing (phase < 0.5)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_moon_fullish : NONSENSE control (phase within 0.1 of full); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_dom_odd : NONSENSE control (dom_odd); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_dom_even : NONSENSE control (dom_even); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_dom_le15 : NONSENSE control (dom_le15); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_dom_d012 : NONSENSE control (dom_d012); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_dom_d345 : NONSENSE control (dom_d345); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_dom_d6789 : NONSENSE control (dom_d6789); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_doy_odd : NONSENSE control (doy_odd); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_isow_odd : NONSENSE control (isow_odd); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_wom_1 : NONSENSE control (wom_1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_wd_odd : NONSENSE control (wd_odd); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_mon_odd : NONSENSE control (mon_odd); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_cal_mon_q1 : NONSENSE control (mon_q1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d0 : NONSENSE control (last digit of integer true price == 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d1 : NONSENSE control (last digit of integer true price == 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d2 : NONSENSE control (last digit of integer true price == 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d3 : NONSENSE control (last digit of integer true price == 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d4 : NONSENSE control (last digit of integer true price == 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d5 : NONSENSE control (last digit of integer true price == 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d6 : NONSENSE control (last digit of integer true price == 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d7 : NONSENSE control (last digit of integer true price == 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d8 : NONSENSE control (last digit of integer true price == 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxdig_d9 : NONSENSE control (last digit of integer true price == 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxfrac_lt50 : NONSENSE control (fractional part of true price < 0.50); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxmod10_lt5 : NONSENSE control (true price mod 10 < 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxmod100_lt50 : NONSENSE control (true price mod 100 < 50); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_pxmod25_lt12 : NONSENSE control (true price mod 25 < 12.5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b0 : NONSENSE control (bit 0 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b1 : NONSENSE control (bit 1 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b2 : NONSENSE control (bit 2 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b3 : NONSENSE control (bit 3 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b4 : NONSENSE control (bit 4 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b5 : NONSENSE control (bit 5 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b6 : NONSENSE control (bit 6 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b7 : NONSENSE control (bit 7 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b8 : NONSENSE control (bit 8 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b9 : NONSENSE control (bit 9 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b10 : NONSENSE control (bit 10 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b11 : NONSENSE control (bit 11 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b12 : NONSENSE control (bit 12 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b13 : NONSENSE control (bit 13 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b14 : NONSENSE control (bit 14 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hdate_b15 : NONSENSE control (bit 15 of sha256(seed|label day)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b0 : NONSENSE control (bit 0 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b1 : NONSENSE control (bit 1 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b2 : NONSENSE control (bit 2 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b3 : NONSENSE control (bit 3 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b4 : NONSENSE control (bit 4 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b5 : NONSENSE control (bit 5 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b6 : NONSENSE control (bit 6 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b7 : NONSENSE control (bit 7 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b8 : NONSENSE control (bit 8 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b9 : NONSENSE control (bit 9 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b10 : NONSENSE control (bit 10 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b11 : NONSENSE control (bit 11 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b12 : NONSENSE control (bit 12 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b13 : NONSENSE control (bit 13 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b14 : NONSENSE control (bit 14 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hts_b15 : NONSENSE control (bit 15 of sha256(seed|sig_ts)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hid_b0 : NONSENSE control (bit 0 of sha256(seed|sig_id)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hid_b1 : NONSENSE control (bit 1 of sha256(seed|sig_id)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hid_b2 : NONSENSE control (bit 2 of sha256(seed|sig_id)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hid_b3 : NONSENSE control (bit 3 of sha256(seed|sig_id)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hid_b4 : NONSENSE control (bit 4 of sha256(seed|sig_id)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hid_b5 : NONSENSE control (bit 5 of sha256(seed|sig_id)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hid_b6 : NONSENSE control (bit 6 of sha256(seed|sig_id)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_hid_b7 : NONSENSE control (bit 7 of sha256(seed|sig_id)); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_clock_minpar : NONSENSE control (minpar); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_clock_secpar : NONSENSE control (secpar); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_clock_tsmod3 : NONSENSE control (tsmod3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_clock_tsmod7 : NONSENSE control (tsmod7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_clock_hourpar : NONSENSE control (hourpar); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_clock_min_lt30 : NONSENSE control (min_lt30); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_clock_min5 : NONSENSE control (min5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_clock_min15lt7 : NONSENSE control (min15lt7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s0 : NONSENSE control (Markov coin, mean run 3 min, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s0 : NONSENSE control (Markov coin, mean run 8 min, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s0 : NONSENSE control (Markov coin, mean run 15 min, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s0 : NONSENSE control (Markov coin, mean run 30 min, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s0 : NONSENSE control (Markov coin, mean run 60 min, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s0 : NONSENSE control (Markov coin, mean run 120 min, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s0 : NONSENSE control (Markov coin, mean run 240 min, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s0 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s0 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s0 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s0 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 0); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s1 : NONSENSE control (Markov coin, mean run 3 min, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s1 : NONSENSE control (Markov coin, mean run 8 min, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s1 : NONSENSE control (Markov coin, mean run 15 min, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s1 : NONSENSE control (Markov coin, mean run 30 min, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s1 : NONSENSE control (Markov coin, mean run 60 min, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s1 : NONSENSE control (Markov coin, mean run 120 min, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s1 : NONSENSE control (Markov coin, mean run 240 min, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s1 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s1 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s1 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s1 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 1); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s2 : NONSENSE control (Markov coin, mean run 3 min, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s2 : NONSENSE control (Markov coin, mean run 8 min, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s2 : NONSENSE control (Markov coin, mean run 15 min, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s2 : NONSENSE control (Markov coin, mean run 30 min, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s2 : NONSENSE control (Markov coin, mean run 60 min, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s2 : NONSENSE control (Markov coin, mean run 120 min, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s2 : NONSENSE control (Markov coin, mean run 240 min, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s2 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s2 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s2 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s2 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 2); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s3 : NONSENSE control (Markov coin, mean run 3 min, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s3 : NONSENSE control (Markov coin, mean run 8 min, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s3 : NONSENSE control (Markov coin, mean run 15 min, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s3 : NONSENSE control (Markov coin, mean run 30 min, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s3 : NONSENSE control (Markov coin, mean run 60 min, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s3 : NONSENSE control (Markov coin, mean run 120 min, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s3 : NONSENSE control (Markov coin, mean run 240 min, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s3 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s3 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s3 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s3 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 3); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s4 : NONSENSE control (Markov coin, mean run 3 min, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s4 : NONSENSE control (Markov coin, mean run 8 min, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s4 : NONSENSE control (Markov coin, mean run 15 min, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s4 : NONSENSE control (Markov coin, mean run 30 min, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s4 : NONSENSE control (Markov coin, mean run 60 min, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s4 : NONSENSE control (Markov coin, mean run 120 min, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s4 : NONSENSE control (Markov coin, mean run 240 min, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s4 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s4 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s4 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s4 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 4); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s5 : NONSENSE control (Markov coin, mean run 3 min, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s5 : NONSENSE control (Markov coin, mean run 8 min, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s5 : NONSENSE control (Markov coin, mean run 15 min, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s5 : NONSENSE control (Markov coin, mean run 30 min, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s5 : NONSENSE control (Markov coin, mean run 60 min, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s5 : NONSENSE control (Markov coin, mean run 120 min, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s5 : NONSENSE control (Markov coin, mean run 240 min, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s5 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s5 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s5 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s5 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 5); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s6 : NONSENSE control (Markov coin, mean run 3 min, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s6 : NONSENSE control (Markov coin, mean run 8 min, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s6 : NONSENSE control (Markov coin, mean run 15 min, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s6 : NONSENSE control (Markov coin, mean run 30 min, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s6 : NONSENSE control (Markov coin, mean run 60 min, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s6 : NONSENSE control (Markov coin, mean run 120 min, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s6 : NONSENSE control (Markov coin, mean run 240 min, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s6 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s6 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s6 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s6 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 6); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s7 : NONSENSE control (Markov coin, mean run 3 min, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s7 : NONSENSE control (Markov coin, mean run 8 min, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s7 : NONSENSE control (Markov coin, mean run 15 min, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s7 : NONSENSE control (Markov coin, mean run 30 min, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s7 : NONSENSE control (Markov coin, mean run 60 min, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s7 : NONSENSE control (Markov coin, mean run 120 min, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s7 : NONSENSE control (Markov coin, mean run 240 min, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s7 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s7 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s7 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s7 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 7); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s8 : NONSENSE control (Markov coin, mean run 3 min, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s8 : NONSENSE control (Markov coin, mean run 8 min, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s8 : NONSENSE control (Markov coin, mean run 15 min, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s8 : NONSENSE control (Markov coin, mean run 30 min, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s8 : NONSENSE control (Markov coin, mean run 60 min, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s8 : NONSENSE control (Markov coin, mean run 120 min, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s8 : NONSENSE control (Markov coin, mean run 240 min, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s8 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s8 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s8 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s8 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 8); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s9 : NONSENSE control (Markov coin, mean run 3 min, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s9 : NONSENSE control (Markov coin, mean run 8 min, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s9 : NONSENSE control (Markov coin, mean run 15 min, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s9 : NONSENSE control (Markov coin, mean run 30 min, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s9 : NONSENSE control (Markov coin, mean run 60 min, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s9 : NONSENSE control (Markov coin, mean run 120 min, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L240_s9 : NONSENSE control (Markov coin, mean run 240 min, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L1_s9 : NONSENSE control (daily Markov coin, mean run 1 label days, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L2_s9 : NONSENSE control (daily Markov coin, mean run 2 label days, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L5_s9 : NONSENSE control (daily Markov coin, mean run 5 label days, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_dcoin_L10_s9 : NONSENSE control (daily Markov coin, mean run 10 label days, seed 9); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L3_s10 : NONSENSE control (Markov coin, mean run 3 min, seed 10); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L8_s10 : NONSENSE control (Markov coin, mean run 8 min, seed 10); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L15_s10 : NONSENSE control (Markov coin, mean run 15 min, seed 10); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L30_s10 : NONSENSE control (Markov coin, mean run 30 min, seed 10); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L60_s10 : NONSENSE control (Markov coin, mean run 60 min, seed 10); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1
- c_Z_coin_L120_s10 : NONSENSE control (Markov coin, mean run 120 min, seed 10); signed: yes = A for long, NOT A for short; seed CF1-NONSENSE-v1


# ===== Categories F G H I J + Block 5 (W-CF2) : merged verbatim from CONFLUENCE_DEFS_CF2.md =====
# CONFLUENCE_DEFS_CF2 (W-CF2). Categories F, G, H, I, J and Block 5. Code: code/th_confl_cf2. Columns: /mnt/l2/l2vast/_confl/cols_cf2/{FG,I,J,H,B5}.parquet keyed by sig_id (= <book7>_<sig_ts>).
VERDICT (data ends 2026-10-30): 5 column files (638 conditions, FG 101, I 72, J 148, H 55, B5 262) built for all 48,353 rows of signals_all.parquet (19,798 taken + 28,555 skipped, W-CF1's current rows; later rows are appended by `python3 code/th_confl_cf2/build_all.py <FG|I|J|H|B5>`, which only computes missing sig_ids); no PASS claims.

## Conventions (all families)
- Signal second T = sig_ts. Everything uses data with timestamp < T (seconds <= T-1; 1-minute bars with bar end <= T; prior-day files for daily/level data). No repainting, no look-ahead.
- s = +1 buy / -1 sell. Columns `c_<CAT>_<name>`: 1 yes / 0 no / NaN not computable (data not on the box for that date). Raw value beside each: `v_<CAT>_<name>` (signed with the trade where it has a side: positive = with the trade).
- "mine" side of the book = the trade's own side (bids for a buy); "ahead" side = the opposite side (asks for a buy).
- Sizes in contracts. NQ price in the replica = ticks of 0.25.
- Coverage: F,G,I(price parts) 2023-02..2026-10; I megacap/semis, J (UW + CME option snapshots) from 2024-10; VIX from 2024-09 (daily, prior close only: no intraday VIX on the box); NKD 2023-04..; 6J only 2026-05..; H (MBO) only on days with MBO on the box (2026-05..2026-10 now; the 2023-04..2026-04 NQ history is being bought and is added by rerunning the builder). YM exists only as 1-minute bars (min1), no tape.

## F. Volume and tape L1 (source: per-second table from mbp-10 replica prints, code sec_build.py; trade aggressor side from the print flag, B = buy aggressor verified against ask price)
- rvol5/rvol15: contracts traded in the last 5/15 min over the median of the same ET clock window on the previous 20 files (sessions). Conditions rvol5 >= 0.8/1.0/1.3/1.6/2.0, rvol15 >= 0.8/1.0/1.3/1.6.
- volrise5: last-5-min volume / the 5 min before >= 1.0/1.25/1.5. volrise1v5: last-minute volume x5 / last-5-min volume >= 1.0/1.5.
- cd{1,5,15}: s x (buy volume - sell volume) over the last 1/5/15 min; cdn = cd / total volume. Conditions cd>0; cdn >= 0.05/0.15. cdz5: cd5 over the standard deviation of the rolling 5-min delta in the trailing 60 min >= 0.5/1.0/1.5.
- ret{5,15,30}: s x price change over the window in points > 0.
- div15 (delta divergence): price progress with the trade over 15 min > 0.5 pt while cd15 is against; condition `no_div15` = not divergent. div15_strong: progress > 2 pt and cd15 < -10% of volume. div_ext: the last price is the 30-min extreme in the trade direction and cd5 is against; condition `no_div_ext`.
- big{10,25,50}_net{5,15} / noagainst: net volume of aggressor prints of size >= 10/25/50 with minus against the trade over 5/15 min > 0; `noagainst` = no such print against the trade in the window. (Replica prints are exchange events, sizes can be a sum of one aggressor order's fills at a level.)
- swing_share: share of aggressor volume in the trade direction within +-60 s of the last against-swing extreme in the last 15 min (the low for a buy) >= 0.5/0.55/0.6.
- absorb: with-trade aggressor volume in the last 5 min per point of progress (min 0.25 pt); `no_absorb_100/200/400` = ratio < 100/200/400 contracts per point.
- ice_with5 >= 1 / ice_against5 == 0: iceberg-refill flags of the DS7 print features (L_iceBidRef/L_iceAskRef) on the trade's own side / the opposite side in the last 5 min.

## G. Order book L2 (source: mbp-10 100 ms grid of the replica; book = last grid row before the end of second T-1)
- imb1/imb5/imb10: s x (bid - ask)/(bid + ask) of the best level / top 5 / all 10 levels >= 0 (>0), 0.1, 0.2, 0.35. imb5_m10/m60: same on top-5 averaged over the last 10/60 s, > 0 and >= 0.1.
- mine_thick: own-side top-5 depth / its median over the trailing 60 min >= 1.0/1.25/1.5. ahead_thin: opposite-side top-5 depth / its trailing-60-min median <= 0.8/1.0.
- spread_1tick: spread <= 1 tick. spread_le_med: spread <= trailing-60-min median.
- wall_ahead{4,10,40}: largest single level on the ahead side within 4/10/40 ticks of the touch; condition `no_wall_ahead{n}_lt{8,15,30}` = that level < 8/15/30 contracts. wall_behind (largest level on my side within n ticks) >= 8/15. wall_x: ahead wall within 10 ticks over the average level size (depth10/10) < 3/5 (`no_wall_ahead10_x3/x5`); behind wall >= 3x (`wall_behind10_x3`). (Level sizes in the replica book are small: top-of-book median 2 contracts, so 8-30 contracts is already a wall.)
- ahead_pulled{30,60}: depth removed from the ahead side (decrease of 10-level depth not explained by trades, best price unchanged) minus depth added, over 30/60 s, > 0. behind_added{30,60}: own side adds minus pulls > 0.
- micro_pos / micro_m10_pos: microprice (size-weighted mid) minus mid, signed, > 0 at the end of T-1 / averaged over 10 s > 0.
- resilient_ge{0.8,1.0}: if a sweep (>= 8 ticks of range in one second) happened in the last 5 min, the top-5 total depth now over its median in the 60 s before the sweep >= 0.8/1.0; no sweep in 5 min counts as yes.
- Limits: bsz/asz of the replica grid are the exchange top-10 only; no hidden size; 100 ms granularity.

## H. Order by order L3 (MBO; source: code mbo_sec.py book reconstruction from the MBO day files: A add, C cancel, F fill, M modify, R clear, T trade-no-book-effect; second table = event accumulators in [s, s+1) and order-level snapshot at the end of s)
- touch_ratio: mine touch size / ahead touch size >= 1/1.5/2; mine_queue_ge2orders (>= 2 resting orders at my touch); mine_touch_ge5; ahead_touch_le2.
- big10/big20: resting order of size >= 10 / >= 20 contracts within 10 ticks of the touch on my side present; `no_big{10,20}_ahead` none on the ahead side; aged_big_mine (such an order resting >= 60 s on my side); no_aged_big_ahead; big_mine_gt_ahead (largest order on my side > largest ahead).
- refill (iceberg): an order of original size >= 5 fully filled and a new add of 0.5-2x that size at the same price and side within 100 ms. refill_mine{60,300}_ge1/ge3 (own side, last 60/300 s); no_refill_ahead; refill_mine_gt_ahead.
- ctr (cancel-to-trade): cancelled volume within 5 ticks of the touch on a side over the traded volume hitting that side (+1) over 60/300 s. ctr_ahead_gt_mine; ctr_mine_lt10; ctr_ahead_ge30.
- arrival_imb{30,60}: (adds on my side - adds on ahead side)/(sum), near the touch (within 5 ticks), > 0 and >= 0.1.
- spoof-like: an order >= 10 contracts added and fully cancelled within 3 s with no fill. no_spoof_mine{60,300}; spoof_ahead{60,300}_ge1 (flag, direction not assumed; the table reports the lift sign).
- aggressor orders: consecutive trade records with the same event timestamp and side form one aggressor order. aggr20/aggr50 (orders >= 20/50 contracts) with / against in the last 60/300 s: with_ge1, no_against, with_gt_against. sweep3: aggressor orders crossing >= 3 price levels: no_sweep3_against, sweep3_with_ge1. gmax_with60 >= 10/25; gmax_against60 < 10/25.
- H is tested as a checklist item at all entries and in the strata "entry at a level" and "level ahead" (W-CF1 level columns c_B_behind_le10 and c_B_ahead_ge10 == 0) in DS3_CONFLUENCE_ITEMS_CF2.md.

## I. Intermarket
- ES/RTY/YM confirm{5,15,60}: s x z where z = return of the 1-minute close over the window / (trailing 240-min std of 1-minute changes x sqrt(W)) (min1 is back-adjusted so z is scale-free); condition z > 0 and z >= 0.5. nconf{W}: number of the three confirming (>= 2, = 3). NQ_leads_ES/RTY{5,15}: s x (zNQ - zES) > 0; NQ_lags_ES{5,15}: < 0.
- ES_ahead_{10,30,300}s: from the 1-second true prices (instr_1s): s x (ES bp move - NQ bp move) over the last 10/30/300 s > 0.5 bp (ES leading in the trade direction); ES_not_against: ES bp move >= -0.5 bp.
- ratio_trend{60,240}: s x change of NQ/ES (true prices, 1 s) over the last 60/240 min > 0.
- no_divergence30_{0.8,0.9}: if NQ's last close is in the top 10% (for a buy) of its 30-min range then the minimum position of ES/RTY/YM in their own 30-min ranges >= 0.8/0.9; if NQ is not at an extreme the condition is yes.
- mega_{with,leads,breadth_ge5}{5,15,60}: UW 1-minute closes of AAPL AMZN GOOGL META MSFT NVDA TSLA: equal-weight mean bp return s-signed > 0; mean minus QQQ > 0; >= 5 of 7 with the trade. NVDA_with and QQQ_with (NVDA is the semis proxy: SMH/XLK are not on the UW plan). From 2024-10.
- ZN_with/ZB_with/6E_with{5,15,60}: z of the 1-minute continuous ZN/ZB (rates falling = with a buy) and 6E (euro up = dollar down = with a buy), s-signed > 0 (raw/intermarket_zn_zb_6e/ohlcv1m).
- vix: fell_prior_day (VIX close of the prior session lower than the one before, signed so a falling VIX is with a buy), below_5d (below the mean of the prior 5), contango (VIX3M/VIX - 1 > 0.05). Daily prior-close values only.
- NKD_with{5,15,60}: s x NKD mid return over the window (bp) > 0 (all sessions; it is a clue for Asia and London). 6J_yen_weakening{15,60}: 6J mid fell (yen weakening = risk-on) over the window; only 2026-05..2026-11 on the box.

## J. Options and positioning (raw builders: code/th_t2b/p4_feat.py = CME NQ option snapshots (N{d,h,m}: daily/hourly/minute reference policy) + UW prior-day gamma/OI levels (NB_) + UW intraday gamma/tide (uw_tf.py); all causal, prior-day level rows only; UW history from 2024-10-01)
- gex_pos_{QQQ,SPX,NDX,SPY}_{oi,vol}: dealer gamma exposure (A_*_g_oi/_vol) > 0. gdir_with: UW gamma direction signed with the trade > 0.
- beyond_flip_{NDX,SPX}_{oi,vol} (NB levels) and _{Nd,Nh}_{oi,vol} (CME snapshots): the gamma flip is BEHIND the trade (price beyond the flip in the trade direction). flip_far{25,50,100}: |distance to flip| >= 25/50/100 NQ points. beyond_0dte_flip / 0dte_flip_far{25,50}: same for the 0DTE flip (Nd_/Nh_ *_fl0).
- nowall_ahead{25,50,100}: nearest call/put/magnet wall in front of the trade farther than 25/50/100 pts (or none); wall_behind{25,50}: a wall within 25/50 pts behind. 0dte_cw0/pw0_not_ahead{25,50}: 0DTE call/put wall not within 25/50 pts ahead.
- netgamma_pos_{Nd,Nh}_{oi,vol}: net gamma profile value at the current price > 0.
- em_used_lt{0.5,0.75,1.0}_{Nd,Nh}: |price - anchor| / implied move (CME NQ options) < threshold (implied move used so far); em_room_ge{50,100,150}: points to the expected-move edge in the trade direction >= 50/100/150; em_frac_pos: s x (price - anchor)/em > 0.
- iv_contango (UW NDX IV term: IV of the first expiry >= 28 DTE over the first >= 5 DTE > 1.0, prior day), iv_contango_steep (> 1.08), ivshort_fell (short IV below the prior day), ivshort_lt20.
- tide_{net,ncp,npp,nv}_{s,s5,s15,s30}: UW ETF-tide premium/volume series (net = call - put premium) signed with the trade; level and change over 5/15/30 min; > 0 for net/ncp/nv, < 0 for npp (put premium against).
- no_opp_burst{05,10}_{net,nv}_{s5,s15,s30}: the s-signed change in tide over 5/15/30 min is above the 5th/10th percentile of its distribution over the signal set (i.e. NOT in the worst 5%/10% opposing bursts). Percentile thresholds are descriptive of the signal set, not outcome-tuned.

## Block 5. Indicator states on ES, RTY, YM, megacap composite (Addendum 2). Code block5.py; PUBLIC FORMULA unless stated; completed 1/5/15-min bars (bar end <= T), standard settings.
- Per instrument X in {ES, RTY, YM, MEGA, NQ(reference)} and timeframe in {1m, 5m, 15m}: `c_B5_<X>_<tf>_<state>_with` where state in ema_stack (EMA8>21>34 in the trade direction), hold21 (last 3 closes on the trade side of EMA21), rsi (RSI14 Wilder > 50 side), cci (CCI20 > 0 side), macd (MACD 12/26/9 histogram side), macd_rising, supertrend (10,3 Wilder ATR), adx_di (ADX14 > 20 and DI side), vwap (close vs session VWAP anchored 18:00 ET; MEGA: equal-weight composite vs composite of 1m closes with unit volume = APPROXIMATION), sqz_fired_dir (TTM squeeze: Bollinger(20,2) inside Keltner(20,1.5xSMA TR) turned off within the last 3 bars, direction = linreg momentum sign), sqz_mom (momentum side); `c_B5_<X>_<tf>_sqz_on` (squeeze currently on).
- Agreement: `c_B5_ALL_<tf>_<state>_ge3of4 / _eq4of4` over ES, RTY, YM, MEGA.
- Power correlations: B5_corr_NQ_{ES,RTY,YM}_{60,240} (correlation of 1-minute changes over the last 60/240 completed minutes), B5_corr_NQ_MEGA_{60,240} (2024-10+), B5_corr_mean3_60, B5_corr_NQ_VIX_d20 (20 completed days, daily NQ close change vs VIX close change; VIX from 2024-09). Conditions corr >= 0.8/0.9 (indices), >= 0.7 (mega), VIX corr <= -0.7.
- W-CF1/W-CF4/W-CF5 indicator libraries (code/th_confl, th_confl_cf4, th_confl_cf5) can be pointed at ES/RTY/YM bars for further states; not run yet.

## Files and counts

| file   |   conditions c_* |   raw v_* |   signal rows |   % rows with any value |
|:-------|-----------------:|----------:|--------------:|------------------------:|
| FG     |              101 |        71 |         48353 |                   100   |
| I      |               72 |        71 |         48353 |                   100   |
| J      |              148 |       222 |         48353 |                    87.7 |
| H      |               55 |        43 |         48353 |                    42.4 |
| B5     |              262 |       223 |         48353 |                   100   |

Column names are listed by `python3 -c "import pandas as pd;print(list(pd.read_parquet('/mnt/l2/l2vast/_confl/cols_cf2/FG.parquet').columns))"`. J burst thresholds are frozen from the first full build (v_J_J_burst_q10_*/q05_* columns). H covers MBO days only (2026-05-01..2026-11-13 now). Known limits: YM has no tape or L2; intraday VIX is not on the box; 6J is L6M only; the megacap composite VWAP is an approximation.

## H2 (drift-robust L3, added after the full NQ MBO history; /mnt/l2/l2vast/_confl/cols_cf2/H2.parquet, 39 columns c_H2_*, code derive_h.py)
- H.parquet is now rebuilt on the full 2023-04..2026-11 MBO history for all 191,520 universe rows (per-second tables /mnt/l2/l2vast/_confl/cf2_mbo, 1,126 day files, compact).
- Because L3 microstructure drifted (order sizes at the touch, cancel-to-trade, spoof-like frequency), H2 compares each raw value (v_H_ctr_mine/ahead 60/300, touch sizes, bmax mine/ahead, spoof counts mine/ahead 60/300, gmax with/against, arrival_imb60, aggr20 with/against 300) with the same raw value over the entries of the previous 20 trading days (all books, causal, >= 150 prior entries): `_hi` = above the 80th percentile, `_lo` = at or below the 20th. Plus `spoof_ahead_gt_mine{60,300}` and `spoof_mine_gt_ahead{60,300}` (relative, no threshold).

## Block 14. Breadth, rotation and relative value (code cf2_b14.py; columns c_B14_* / v_B14_*, file B14.parquet). Registered BEFORE scoring.
Causal rule: last COMPLETE 1-minute bar (bar start + 60 <= sig_ts). Breadth items are regular-hours only (09:30-16:00 ET) and exist from 2024-10 (UW 1-minute history); NaN otherwise. s-signed: "with" = in the trade's direction.
- Members: AAPL AMZN GOOGL META MSFT NVDA TSLA (7 megacaps; Nasdaq-100 component bars are NOT bought, W-CH3 quote in DS3_DEEPEN_OUTSIDE.md) + QQQ SPY IWM DIA. Semis proxy = NVDA only (SMH/SOXX/AVGO are not in the 1-minute set; ETF quote below). Software proxy = MSFT (no IGV): software-vs-semis is an APPROXIMATION.
- share_vwap_with_ge{4,5,6}of7: number of the 7 above their own RTH-anchored VWAP (buy) or below (sell) >= 4/5/6. VWAP = cumulative close*volume / volume on 1-minute closes (APPROXIMATION of VWAP). share_ma20_with: same vs the 20-bar mean of closes.
- newhigh_minus_low_with_gt{0,2}: (# stocks whose close equals the session high so far - # at the session low), s-signed. hl_net_15bars_with_pos: cumulative of that over the last 15 bars > 0.
- adl: advance-decline line = cumulative (# up - # down 1-minute returns) over the 7 stocks within the RTH day. adl_at_extreme_with_ge0.9: position of the line in its last-30-bar range >= 0.9 (with the trade). no_adl_divergence_from_NQ: NOT (NQ at >= 0.9 of its 30-min range in the trade direction while the A/D line < 0.6). mcclellan_osc_with_pos: EMA19 - EMA39 (in minutes) of the net advancers > 0, s-signed (a McClellan-style oscillator, APPROXIMATION on 7 names). adv_dec_15bars_with_pos: sum of net advancers over 15 bars, s-signed > 0.
- Rotation (bp over W = 15, 60 min, s-signed, > 0): eq7_minus_QQQ (equal-weight megacaps minus cap-weighted QQQ: proxy for equal-weight vs cap-weight tech), NVDA_minus_QQQ (semis vs Nasdaq proxy), MSFT_minus_NVDA (software vs semis proxy), largest_minus_QQQ (the member with the largest PRIOR-day dollar volume).
- dispersion_15_{high,low}_vs_recent: cross-sectional std of the 7 stocks' 15-min returns above 1.2x / below 0.8x the median of the previous 800 observed signal values. avg_corr60_ge{0.3,0.5}, le0.2: mean pairwise correlation of the 7 stocks' 1-minute returns over the last 60 bars.
- Relative value (true prices from instr_1s, minute ends; all sessions): NQ_cheap_vs_ES_with_ge{0.5,1,1.5}: z of (log NQ - beta*log ES) vs its trailing 240-min mean/std (beta = trailing 240-min rolling regression slope of NQ on ES 1-minute changes, lagged one bar), signed so that cheap NQ is positive for a buy; NQ_rich_vs_ES_with is the opposite sign (NQ ahead of ES in the trade direction). NQ_cheap/rich_vs_QQQ_with_ge{0.5,1}: same on log(NQ/QQQ) over the last 120 RTH bars (2024-10+, RTH only); note "rich with the trade" mostly means NQ is leading QQQ in the trade direction. RTY_outperforming_ES_{60,240}_with: change of log(RTY/ES) over 60/240 min, s-signed > 0.

## Block 15. Macro, sentiment and positioning as DAY context (code cf2_b15.py; columns c_B15_* / v_B15_*, file B15.parquet). Registered BEFORE scoring.
Every series enters only after its publication time: Treasury par curve, VIX family (Cboe csv), SKEW, COR1M, Cboe put/call = same ET day 18:00 (usable from the next session); FRED HY/IG OAS = next day 09:00 ET (starts 2023-11-15: FRED keeps 3 years); FRED broad dollar = +8 days (STALE context only); CFTC COT = report date (Tuesday) + 3 days 15:30 ET; auction results = auction close + 2 min; earnings = SEC 8-K item 2.02 acceptance time; Fed speeches = scheduled start. All sources free without signup.
- Rates (Treasury yield curve, prior day): yield10_fell_prior_day_with / yield2_fell_prior_day_with / yield10_fell_5d_with (s-signed: falling yield with a buy); curve_steepened_prior_day (+ ge3bp, flattened ge3bp); big_yield_day_ge8bp. Intraday on the CME 1-minute continuous futures (ZN 10-year note, ZB, 6E; z-units): ZN_up_since_open_with and since 09:30 (yield falling with a buy), ZBminusZN_since_open_with (long end outperforming, curve-flattening proxy), 6E_up_since_open_with and since 09:30 (euro up = dollar down with a buy). Dollar index itself (DXY) is paid; FRED broad dollar is 8 days stale: usd_fell_20d_with_STALE; 6E is the intraday dollar proxy (APPROXIMATION).
- bondvol_proxy_ge1.25 / le0.8: ZN realized vol of 1-minute changes over the last 240 min over its trailing 20-day mean (APPROXIMATION of the MOVE index, which is paid).
- Credit (FRED ICE BofA option-adjusted spreads, from 2023-11-15; HYG/LQD ETF bars are not on the box, quote below): hy_narrowed_prior_day_with, hy_narrowed_5d_with, hy_stress_pct_ge80 / hy_calm_pct_le20 (252-day percentile).
- Volatility family: vix_fell_prior_day_with, vix9d_gt_vix, vix_backwardation_vs_3m (VIX > VIX3M), vix_contango_gt5pct (VIX/VIX3M < 0.95); 252-day percentile >= 80 / <= 20 of VIX, VVIX, SKEW, COR1M (CBOE implied correlation 1M).
- Put/call (Cboe daily statistics): total, index, equity, ETP put/call 252-day percentile >= 80 / <= 20; pc_eq_rose_prior_day.
- COT (CFTC TFF, NASDAQ MINI futures only): leveraged-money and asset-manager net position over open interest, 52-week percentile >= 80 / <= 20, rising over the last week.
- Treasury auctions (TreasuryDirect, notes 2/3/5/7/10 and bonds 20/30): auction_day_{any,2y,3y,5y,7y,10y,20y,30y}; within30min_of_note_bond_auction; after the result: auction_result_strong_btc (bid-to-cover over the mean of the last 6 same-term auctions > 1.0), weak (<= 0.95), yield_up_vs_prev_ge2bp / down_le-2bp (high yield vs previous same-term auction; the true tail needs when-issued yields which are not free: APPROXIMATION).
- Megacap earnings (SEC EDGAR 8-K item 2.02, acceptance time; any of 7, NVDA, big5 = AAPL AMZN GOOGL META MSFT): earn_*_day_after_report (session date is the first session after the filing: filed at/after 16:00 ET counts for the next session), earn_*_report_today (filing date, scheduled weeks ahead), earn_*_report_week (same ISO week).
- Fed speakers (federalreserve.gov speeches/events scrape by W-CAL): fed_speaker_today, fed_chair_speaks_today, fed_speech_within_60min, fed_speech_started_last_90min.
- NOT built (needs a paid or unavailable feed): economic surprise index (Citi/Bloomberg consensus: paid; no free consensus history), MOVE index itself (paid), DXY (paid), HYG/LQD bars (not on the box, quote below), SPX-wide/Nasdaq-100 breadth (components not bought).


# ===== Block 2 / Block 4 (W-CF4) : merged verbatim from CONFLUENCE_DEFS_CF4.md =====
# CONFLUENCE_DEFS_CF4 (W-CF4, Block 2 / Block 4). Auto-built by code/th_confl_cf4/c4_page.py

Key: `sid` = sig_id of the W-CF1 entry table (<book7>_<sig_ts>), all 48,353 signals (taken and skipped) in /mnt/l2/l2vast/_confl/entry_table/signals_all.parquet. CAVEAT: the NQ 1m bar store bars1m_NQ.npz is an additively gap-spliced series (its offset to the traded price grows from ~360 pts in 2023-04 to ~3,700 pts in 2026-10; local structure and ranges are exact, absolute levels are not): indicators here use ratios/differences only, no round-number levels. Files: /mnt/l2/l2vast/_confl/cols_cf4/cf4_<sub>.parquet. int8 columns: 1 yes, 0 no, -1 unknown. Raw value of the indicator beside each: `v_<ind>_<tf>` (float32).
Column name: c4_<indicator>_<tf>_<cond>, tf in 1m,3m,5m,15m,60m,1d. Bars: 1m from /mnt/l2/l2vast/_th_sz/bars1m_NQ.npz; HTF bars aligned to epoch (daily = Globex day, 18:00 ET); a bar is used only if its END <= signal second (completed bars only; no repainting anywhere).
Conditions (template): `side` state on trade side (x vs mid, or sign of the state); `sig` x on trade side of its signal line; `rise` x moving with the trade vs 1 bar ago; `fresh5` fresh signal (cross of signal line / midline / explicit event) with the trade within the last 5 bars, `fresh1` on the last bar; `ewith`/`eagainst` in the extreme zone on / against the trade side (z1,z2 = two zone sets); `eleave` left the zone against the trade within 3 bars; `eenter` entered the with-trade extreme within 3 bars; `nodiv`/`divwith` no divergence against / divergence in favour at the last two fractal swings (k=2) of that TF; `mtf_n` (raw count 0-6), `mtf_ge4`, `mtf_all` = number of timeframes (1,3,5,15,60,1d) where `side` is yes. unsigned indicators: `hi`,`lo_z`,`hi_z`,`rise`. Fast/slow variants are suffixed F / S (standard published setting has no suffix).

## B2-A momentum / oscillators: 3144 condition columns, 71 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| wt | PUBLIC LazyBear WaveTrend (10,21) | osc |
| wtF | PUBLIC LazyBear WaveTrend (6,12) | osc |
| wtS | PUBLIC LazyBear WaveTrend (14,30) | osc |
| sqzm_mom | PUBLIC LazyBear squeeze momentum value (20) | osc |
| sqzm_on | PUBLIC: BB(20,2) inside KC(20,1.5 SMA-TR) | osc |
| sqzm_bright | PUBLIC 4-colour histogram: positive rising / negative falling | osc |
| sqzmF_mom | PUBLIC LazyBear squeeze momentum value (12) | osc |
| sqzmF_on | PUBLIC: BB(12,2) inside KC(12,1.5 SMA-TR) | osc |
| sqzmF_bright | PUBLIC 4-colour histogram: positive rising / negative falling | osc |
| sqzmS_mom | PUBLIC LazyBear squeeze momentum value (34) | osc |
| sqzmS_on | PUBLIC: BB(34,2) inside KC(34,1.5 SMA-TR) | osc |
| sqzmS_bright | PUBLIC 4-colour histogram: positive rising / negative falling | osc |
| mcwt | APPROXIMATION of Market Cipher B: WT(9,12,3); dots = WT cross while WT2 beyond +-53 (ev) | osc |
| mcmf | APPROXIMATION: money flow = SMA60 of 150*(close-open)/(high-low) | osc |
| mc_comp | APPROXIMATION: WT1>WT2, money flow>0, RSI14>50 all agree (+1/-1) | osc |
| mc_comp2 | APPROXIMATION: sum of 3 signs | osc |
| qqe | PUBLIC QQE (RSI 14, SF 5, factor 4.236), trailing line by Wilder-ATR of smoothed RSI | osc |
| qqeF | PUBLIC QQE (RSI 7, SF 3, factor 3.000), trailing line by Wilder-ATR of smoothed RSI | osc |
| qqeS | PUBLIC QQE (RSI 21, SF 8, factor 4.236), trailing line by Wilder-ATR of smoothed RSI | osc |
| qqemod | APPROXIMATION of QQE Mod (Mihkel00): RSI6 sf5 factor3; colour bar = RSI-50 beyond +-3 AND outside BB(50,0.35) of the QQE line | osc |
| qqemod_hist | QQE Mod histogram RSI(6)-50 | osc |
| rsima14 | PUBLIC RSI(14) vs its SMA14; divergence at last fractal swing in template | osc |
| rsima7 | PUBLIC RSI(7) vs its SMA14; divergence at last fractal swing in template | osc |
| rsima21 | PUBLIC RSI(21) vs its SMA14; divergence at last fractal swing in template | osc |
| crsi | PUBLIC Connors RSI(3,2,100) | osc |
| crsiF | variant (2,2,50) | osc |
| srsi | PUBLIC StochRSI(14,14,3,3) | osc |
| srsiF | PUBLIC StochRSI(14,8,3,3) | osc |
| srsiS | PUBLIC StochRSI(14,21,3,3) | osc |
| stc | PUBLIC Schaff Trend Cycle (23,50,10,0.5) | osc |
| stcF | PUBLIC Schaff Trend Cycle (12,26,6,0.5) | osc |
| stcS | PUBLIC Schaff Trend Cycle (34,70,14,0.5) | osc |
| kst | PUBLIC Pring KST (10, 15, 20, 30) | osc |
| kstF | PUBLIC Pring KST (5, 8, 10, 15) | osc |
| kstS | PUBLIC Pring KST (20, 30, 40, 60) | osc |
| copp | PUBLIC Coppock WMA10(ROC14+ROC11) | osc |
| coppF | PUBLIC Coppock WMA6(ROC8+ROC6) | osc |
| coppS | PUBLIC Coppock WMA15(ROC21+ROC15) | osc |
| rvi | PUBLIC Ehlers/Donald Dorsey RVI(10), signal SWMA4 | osc |
| rviF | PUBLIC Ehlers/Donald Dorsey RVI(5), signal SWMA4 | osc |
| rviS | PUBLIC Ehlers/Donald Dorsey RVI(20), signal SWMA4 | osc |
| elder_bull | PUBLIC Elder Bull Power = high - EMA13 | osc |
| elder_bear | PUBLIC Elder Bear Power = low - EMA13 | osc |
| elder_impulse | PUBLIC Elder Impulse: EMA13 slope and MACD(12,26,9) hist slope both up (green) / down (red) | osc |
| elderF_bull | PUBLIC Elder Bull Power = high - EMA8 | osc |
| elderF_bear | PUBLIC Elder Bear Power = low - EMA8 | osc |
| elderF_impulse | PUBLIC Elder Impulse: EMA8 slope and MACD(12,26,9) hist slope both up (green) / down (red) | osc |
| elderS_bull | PUBLIC Elder Bull Power = high - EMA26 | osc |
| elderS_bear | PUBLIC Elder Bear Power = low - EMA26 | osc |
| elderS_impulse | PUBLIC Elder Impulse: EMA26 slope and MACD(12,26,9) hist slope both up (green) / down (red) | osc |
| smie | APPROXIMATION: SMI Ergodic = TSI(5,20) scaled 0-1, signal EMA5 | osc |
| smieF | APPROXIMATION: SMI Ergodic = TSI(3,10) scaled 0-1, signal EMA5 | osc |
| smieS | APPROXIMATION: SMI Ergodic = TSI(8,34) scaled 0-1, signal EMA5 | osc |
| smi | PUBLIC Blau SMI (10,3,3), signal EMA10 | osc |
| smiF | PUBLIC Blau SMI (5,3,3), signal EMA10 | osc |
| smiS | PUBLIC Blau SMI (21,5,5), signal EMA10 | osc |
| tsi | PUBLIC True Strength Index (25,13) signal EMA7 | osc |
| tsiF | PUBLIC True Strength Index (13,7) signal EMA7 | osc |
| tsiS | PUBLIC True Strength Index (40,20) signal EMA7 | osc |
| kvo | PUBLIC Klinger (34,55,13), cm resets on trend change | osc |
| kvoF | PUBLIC Klinger (14,28,7), cm resets on trend change | osc |
| kvoS | PUBLIC Klinger (55,89,21), cm resets on trend change | osc |
| chop | PUBLIC Choppiness Index(14); >61.8 choppy, <38.2 trending | osc |
| chopF | PUBLIC Choppiness Index(7); >61.8 choppy, <38.2 trending | osc |
| chopS | PUBLIC Choppiness Index(28); >61.8 choppy, <38.2 trending | osc |
| ker_abs | PUBLIC Kaufman efficiency ratio(10) | osc |
| ker_dir | signed Kaufman ER(10): direction x efficiency | osc |
| kerF_abs | PUBLIC Kaufman efficiency ratio(5) | osc |
| kerF_dir | signed Kaufman ER(5): direction x efficiency | osc |
| kerS_abs | PUBLIC Kaufman efficiency ratio(30) | osc |
| kerS_dir | signed Kaufman ER(30): direction x efficiency | osc |

## B2-B trend followers: 3330 condition columns, 103 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| utbot | PUBLIC UT Bot Alerts key=1 ATR=10 (close vs trailing stop; ev = buy/sell cross) | trend |
| utbotF | PUBLIC UT Bot Alerts key=1 ATR=5 (close vs trailing stop; ev = buy/sell cross) | trend |
| utbotS | PUBLIC UT Bot Alerts key=2 ATR=14 (close vs trailing stop; ev = buy/sell cross) | trend |
| chand | PUBLIC Chandelier Exit(22, ATR x3), ratcheting stops, dir flips when close crosses opposite stop | trend |
| chandF | PUBLIC Chandelier Exit(10, ATR x2), ratcheting stops, dir flips when close crosses opposite stop | trend |
| chandS | PUBLIC Chandelier Exit(44, ATR x4), ratcheting stops, dir flips when close crosses opposite stop | trend |
| ssl | PUBLIC SSL Channel(10): close > SMA(high) -> up, < SMA(low) -> down | trend |
| sslhyb | APPROXIMATION of SSL Hybrid (Mihkel00): baseline HMA60 side AND SSL(10) agree; exit SSL2 omitted | trend |
| sslF | PUBLIC SSL Channel(5): close > SMA(high) -> up, < SMA(low) -> down | trend |
| sslS | PUBLIC SSL Channel(20): close > SMA(high) -> up, < SMA(low) -> down | trend |
| hull | PUBLIC Hull Suite HMA(55) vs HMA 2 bars ago | trend |
| hull_px | price vs HMA(55) | trend |
| hullF | PUBLIC Hull Suite HMA(21) vs HMA 2 bars ago | trend |
| hullF_px | price vs HMA(21) | trend |
| hullS | PUBLIC Hull Suite HMA(89) vs HMA 2 bars ago | trend |
| hullS_px | price vs HMA(89) | trend |
| rfilt | PUBLIC Range Filter Buy&Sell (period 100, mult 3) | trend |
| rfilt_dir | filter direction (upward / downward run) | trend |
| rfiltF | PUBLIC Range Filter Buy&Sell (period 50, mult 2) | trend |
| rfiltF_dir | filter direction (upward / downward run) | trend |
| rfiltS | PUBLIC Range Filter Buy&Sell (period 200, mult 4) | trend |
| rfiltS_dir | filter direction (upward / downward run) | trend |
| halft | PUBLIC HalfTrend (everget/Alex Orekhov) amplitude=2 dev=2: trend flips on SMA(high/low) vs max-low/min-high and close vs prior bar extreme | trend |
| halftF | PUBLIC HalfTrend (everget/Alex Orekhov) amplitude=1 dev=2: trend flips on SMA(high/low) vs max-low/min-high and close vs prior bar extreme | trend |
| halftS | PUBLIC HalfTrend (everget/Alex Orekhov) amplitude=5 dev=2: trend flips on SMA(high/low) vs max-low/min-high and close vs prior bar extreme | trend |
| stA | PUBLIC Supertrend ATR(10) x3 on HL2 | trend |
| stAF | PUBLIC Supertrend ATR(7) x2 on HL2 | trend |
| stAS | PUBLIC Supertrend ATR(22) x4 on HL2 | trend |
| stA21 | PUBLIC Supertrend ATR(10) x2 on HL2 | trend |
| stP | PUBLIC Pivot Point SuperTrend (LonesomeTheBlue) pivot period 2 factor 3 atr 10 | trend |
| stPF | PUBLIC Pivot Point SuperTrend (LonesomeTheBlue) pivot period 1 factor 2 atr 10 | trend |
| stPS | PUBLIC Pivot Point SuperTrend (LonesomeTheBlue) pivot period 4 factor 4 atr 10 | trend |
| alligator | PUBLIC Williams Alligator 13/8/5 SMMA shifts 8/5/3, awake = lips>teeth>jaw (or reverse) | trend |
| alli_spread | lips - jaw in ATR (mouth opening) | trend |
| fractal_brk | PUBLIC Williams fractals (5-bar, confirmed 2 bars later): state = direction of last close break of the latest confirmed fractal | trend |
| fractal_alli | Williams: fractal break on the correct side of the Alligator teeth | trend |
| hilo | PUBLIC Gann HiLo Activator SMA(high/low,10) | trend |
| hiloF | PUBLIC Gann HiLo Activator SMA(high/low,5) | trend |
| hiloS | PUBLIC Gann HiLo Activator SMA(high/low,20) | trend |
| mcg_px | PUBLIC McGinley Dynamic N=14 | trend |
| mcg_slope | PUBLIC McGinley Dynamic N=14 (slope of the line) | trend |
| mcgF_px | PUBLIC McGinley Dynamic N=8 | trend |
| mcgF_slope | PUBLIC McGinley Dynamic N=8 (slope of the line) | trend |
| mcgS_px | PUBLIC McGinley Dynamic N=30 | trend |
| mcgS_slope | PUBLIC McGinley Dynamic N=30 (slope of the line) | trend |
| t3_px | PUBLIC Tillson T3 n=5 b=0.7 | trend |
| t3_slope | PUBLIC Tillson T3 n=5 b=0.7 (slope of the line) | trend |
| t3F_px | PUBLIC Tillson T3 n=3 b=0.7 | trend |
| t3F_slope | PUBLIC Tillson T3 n=3 b=0.7 (slope of the line) | trend |
| t3S_px | PUBLIC Tillson T3 n=10 b=0.7 | trend |
| t3S_slope | PUBLIC Tillson T3 n=10 b=0.7 (slope of the line) | trend |
| zlema_px | PUBLIC ZLEMA n=21 lag=(n-1)/2 | trend |
| zlema_slope | PUBLIC ZLEMA n=21 lag=(n-1)/2 (slope of the line) | trend |
| zlemaF_px | PUBLIC ZLEMA n=9 lag=(n-1)/2 | trend |
| zlemaF_slope | PUBLIC ZLEMA n=9 lag=(n-1)/2 (slope of the line) | trend |
| zlemaS_px | PUBLIC ZLEMA n=50 lag=(n-1)/2 | trend |
| zlemaS_slope | PUBLIC ZLEMA n=50 lag=(n-1)/2 (slope of the line) | trend |
| alma_px | PUBLIC ALMA window 9 offset 0.85 sigma 6 | trend |
| alma_slope | PUBLIC ALMA window 9 offset 0.85 sigma 6 (slope of the line) | trend |
| almaF_px | PUBLIC ALMA window 6 offset 0.85 sigma 6 | trend |
| almaF_slope | PUBLIC ALMA window 6 offset 0.85 sigma 6 (slope of the line) | trend |
| almaS_px | PUBLIC ALMA window 50 offset 0.85 sigma 6 | trend |
| almaS_slope | PUBLIC ALMA window 50 offset 0.85 sigma 6 (slope of the line) | trend |
| alma_x | ALMA9 vs ALMA50 | trend |
| nwe | APPROXIMATION: causal NW envelope, one-sided Gaussian kernel h=8 over 4h bars, band = 3*SMA100(|c-yhat|); z=(c-yhat)/band*3; ev = re-entry through band | trend |
| nweF | APPROXIMATION: causal NW envelope, one-sided Gaussian kernel h=4 over 4h bars, band = 3*SMA100(|c-yhat|); z=(c-yhat)/band*3; ev = re-entry through band | trend |
| nweS | APPROXIMATION: causal NW envelope, one-sided Gaussian kernel h=16 over 4h bars, band = 3*SMA100(|c-yhat|); z=(c-yhat)/band*3; ev = re-entry through band | trend |
| lrc | PUBLIC OLS regression channel 100, +-2 residual sd (exact window OLS) | trend |
| lrc_slope | OLS slope per bar in ATR | trend |
| lrcF | PUBLIC OLS regression channel 50, +-2 residual sd (exact window OLS) | trend |
| lrcF_slope | OLS slope per bar in ATR | trend |
| lrcS | PUBLIC OLS regression channel 200, +-2 residual sd (exact window OLS) | trend |
| lrcS_slope | OLS slope per bar in ATR | trend |
| seb | PUBLIC Standard Error Bands(21): SMA3 of linreg +-2 SE; z = distance in band half-widths | trend |
| sebF | PUBLIC Standard Error Bands(13): SMA3 of linreg +-2 SE; z = distance in band half-widths | trend |
| sebS | PUBLIC Standard Error Bands(55): SMA3 of linreg +-2 SE; z = distance in band half-widths | trend |
| turt20 | PUBLIC Turtle system (entry 20-bar breakout on close, exit 10-bar opposite extreme; flat state=0) | trend |
| don20_pos | PUBLIC Donchian(20) position -1..1 | trend |
| turt55 | PUBLIC Turtle system (entry 55-bar breakout on close, exit 20-bar opposite extreme; flat state=0) | trend |
| don55_pos | PUBLIC Donchian(55) position -1..1 | trend |
| turt10 | PUBLIC Turtle system (entry 10-bar breakout on close, exit 5-bar opposite extreme; flat state=0) | trend |
| don10_pos | PUBLIC Donchian(10) position -1..1 | trend |
| ichi_cloud | PUBLIC Ichimoku (9,26,52) price vs cloud (cloud at t = span computed 26 bars earlier) | trend |
| ichi_tk | tenkan-kijun cross | trend |
| ichi_kj | price vs kijun | trend |
| ichi_chikou | chikou clear: close vs close 26 bars ago | trend |
| ichi_futcloud | future cloud colour: senkou A vs B computed now (displaced +26, known at t) | trend |
| ichi_thick | cloud thickness in ATR | trend |
| ichi_score | Ichimoku score -5..5 (cloud, TK, price>kijun, chikou, future cloud); ewith = |score|>=4 with the trade | trend |
| ichiF_cloud | PUBLIC Ichimoku (6,13,26) price vs cloud (cloud at t = span computed 13 bars earlier) | trend |
| ichiF_tk | tenkan-kijun cross | trend |
| ichiF_kj | price vs kijun | trend |
| ichiF_chikou | chikou clear: close vs close 13 bars ago | trend |
| ichiF_futcloud | future cloud colour: senkou A vs B computed now (displaced +13, known at t) | trend |
| ichiF_thick | cloud thickness in ATR | trend |
| ichiF_score | Ichimoku score -5..5 (cloud, TK, price>kijun, chikou, future cloud); ewith = |score|>=4 with the trade | trend |
| ichiS_cloud | PUBLIC Ichimoku (12,30,60) price vs cloud (cloud at t = span computed 30 bars earlier) | trend |
| ichiS_tk | tenkan-kijun cross | trend |
| ichiS_kj | price vs kijun | trend |
| ichiS_chikou | chikou clear: close vs close 30 bars ago | trend |
| ichiS_futcloud | future cloud colour: senkou A vs B computed now (displaced +30, known at t) | trend |
| ichiS_thick | cloud thickness in ATR | trend |
| ichiS_score | Ichimoku score -5..5 (cloud, TK, price>kijun, chikou, future cloud); ewith = |score|>=4 with the trade | trend |

## B2-C smart-money / price action: 2030 condition columns, 103 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| struct | APPROXIMATION of ICT/LuxAlgo structure: fractal pivots k=3 confirmed k bars late; BOS = close beyond the last unbroken pivot in trend direction; state = trend after last break; ev = BOS | smc |
| choch | CHoCH: close beyond last unbroken pivot AGAINST the prior trend (k=3); ev = CHoCH, x = trend after | smc |
| ob_in | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| ob_near | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| ob_cnt | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; count of active support minus resistance zones | smc |
| ob_dsup | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest support below (unsigned feature) | smc |
| ob_dres | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest resistance above (unsigned feature) | smc |
| brk_in | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| brk_near | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; flipped zone within 1 ATR on the trade side | smc |
| structF | APPROXIMATION of ICT/LuxAlgo structure: fractal pivots k=2 confirmed k bars late; BOS = close beyond the last unbroken pivot in trend direction; state = trend after last break; ev = BOS | smc |
| chochF | CHoCH: close beyond last unbroken pivot AGAINST the prior trend (k=2); ev = CHoCH, x = trend after | smc |
| obF_in | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| obF_near | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| obF_cnt | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; count of active support minus resistance zones | smc |
| obF_dsup | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest support below (unsigned feature) | smc |
| obF_dres | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest resistance above (unsigned feature) | smc |
| brkF_in | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| brkF_near | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; flipped zone within 1 ATR on the trade side | smc |
| structS | APPROXIMATION of ICT/LuxAlgo structure: fractal pivots k=5 confirmed k bars late; BOS = close beyond the last unbroken pivot in trend direction; state = trend after last break; ev = BOS | smc |
| chochS | CHoCH: close beyond last unbroken pivot AGAINST the prior trend (k=5); ev = CHoCH, x = trend after | smc |
| obS_in | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| obS_near | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| obS_cnt | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; count of active support minus resistance zones | smc |
| obS_dsup | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest support below (unsigned feature) | smc |
| obS_dres | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest resistance above (unsigned feature) | smc |
| brkS_in | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| brkS_near | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; flipped zone within 1 ATR on the trade side | smc |
| fvg_in | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| fvg_near | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| fvg_cnt | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; count of active support minus resistance zones | smc |
| fvg_dsup | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest support below (unsigned feature) | smc |
| fvg_dres | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest resistance above (unsigned feature) | smc |
| ifvg_in | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| ifvg_near | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; flipped zone within 1 ATR on the trade side | smc |
| fvgF_in | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| fvgF_near | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| fvgF_cnt | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; count of active support minus resistance zones | smc |
| fvgF_dsup | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest support below (unsigned feature) | smc |
| fvgF_dres | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest resistance above (unsigned feature) | smc |
| ifvgF_in | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| ifvgF_near | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; flipped zone within 1 ATR on the trade side | smc |
| fvgS_in | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| fvgS_near | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| fvgS_cnt | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; count of active support minus resistance zones | smc |
| fvgS_dsup | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest support below (unsigned feature) | smc |
| fvgS_dres | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest resistance above (unsigned feature) | smc |
| ifvgS_in | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| ifvgS_near | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; flipped zone within 1 ATR on the trade side | smc |
| sd_in | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| sd_near | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| sd_cnt | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; count of active support minus resistance zones | smc |
| sd_dsup | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; ATR distance to nearest support below (unsigned feature) | smc |
| sd_dres | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; ATR distance to nearest resistance above (unsigned feature) | smc |
| sdflip_in | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| sdflip_near | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; flipped zone within 1 ATR on the trade side | smc |
| sdF_in | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| sdF_near | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| sdF_cnt | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; count of active support minus resistance zones | smc |
| sdF_dsup | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; ATR distance to nearest support below (unsigned feature) | smc |
| sdF_dres | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; ATR distance to nearest resistance above (unsigned feature) | smc |
| sdflipF_in | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| sdflipF_near | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; flipped zone within 1 ATR on the trade side | smc |
| sdS_in | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| sdS_near | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| sdS_cnt | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; count of active support minus resistance zones | smc |
| sdS_dsup | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; ATR distance to nearest support below (unsigned feature) | smc |
| sdS_dres | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; ATR distance to nearest resistance above (unsigned feature) | smc |
| sdflipS_in | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| sdflipS_near | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; flipped zone within 1 ATR on the trade side | smc |
| sfp | PUBLIC swing-failure pattern: bar trades through an unswept fractal(k=3) pivot and CLOSES back inside (+1 long = low swept) | smc |
| eqsweep | liquidity sweep of EQUAL highs/lows (two pivots within 0.10 ATR) with close back inside | smc |
| eqpool_up | ATR distance to nearest unswept equal-highs pool above | smc |
| eqpool_dn | ATR distance to nearest unswept equal-lows pool below | smc |
| sfpF | PUBLIC swing-failure pattern: bar trades through an unswept fractal(k=2) pivot and CLOSES back inside (+1 long = low swept) | smc |
| eqsweepF | liquidity sweep of EQUAL highs/lows (two pivots within 0.15 ATR) with close back inside | smc |
| eqpool_upF | ATR distance to nearest unswept equal-highs pool above | smc |
| eqpool_dnF | ATR distance to nearest unswept equal-lows pool below | smc |
| sfpS | PUBLIC swing-failure pattern: bar trades through an unswept fractal(k=5) pivot and CLOSES back inside (+1 long = low swept) | smc |
| eqsweepS | liquidity sweep of EQUAL highs/lows (two pivots within 0.10 ATR) with close back inside | smc |
| eqpool_upS | ATR distance to nearest unswept equal-highs pool above | smc |
| eqpool_dnS | ATR distance to nearest unswept equal-lows pool below | smc |
| pd | PUBLIC premium/discount: position in dealing range [last pivot low, last pivot high] (k=5); x=0.5-pos (+ = discount, good for longs) | smc |
| ote | PUBLIC OTE: retracement 62-79% of the last impulse leg between pivots (k=5); +1 long (leg up, pulled back), -1 short | smc |
| ote_wide | retracement 50-79% | smc |
| pdF | PUBLIC premium/discount: position in dealing range [last pivot low, last pivot high] (k=2); x=0.5-pos (+ = discount, good for longs) | smc |
| oteF | PUBLIC OTE: retracement 62-79% of the last impulse leg between pivots (k=2); +1 long (leg up, pulled back), -1 short | smc |
| ote_wideF | retracement 50-79% | smc |
| pdS | PUBLIC premium/discount: position in dealing range [last pivot low, last pivot high] (k=10); x=0.5-pos (+ = discount, good for longs) | smc |
| oteS | PUBLIC OTE: retracement 62-79% of the last impulse leg between pivots (k=10); +1 long (leg up, pulled back), -1 short | smc |
| ote_wideS | retracement 50-79% | smc |
| kz_asia | PUBLIC (ICT) ICT Asia kill zone 20:00-24:00 ET (bar open time) | smc |
| kz_london | PUBLIC (ICT) London open kill zone 02:00-05:00 ET (bar open time) | smc |
| kz_nyam | PUBLIC (ICT) NY open kill zone 07:00-10:00 ET (bar open time) | smc |
| kz_nyam2 | PUBLIC (ICT) NY AM 08:30-11:00 ET (bar open time) | smc |
| kz_lclose | PUBLIC (ICT) London close kill zone 10:00-12:00 ET (bar open time) | smc |
| kz_sb_am | PUBLIC (ICT) Silver Bullet 10:00-11:00 ET (bar open time) | smc |
| kz_sb_pm | PUBLIC (ICT) Silver Bullet 14:00-15:00 ET (bar open time) | smc |
| po3_asia | APPROXIMATION power-of-three: Asia range 20:00-24:00 ET; manipulation = sweep of Asia high/low after 02:00 with close back inside; +1 long/-1 short | smc |
| po3_asia_conf | po3_asia and price already beyond the Asia range midpoint (distribution started) | smc |
| po3_london | NY-session manipulation of the London range (02:00-08:00 ET) after 08:30: sweep and close back inside | smc |
| mopen | PUBLIC price vs ICT midnight open (00:00 ET) | smc |
| o830 | price vs 08:30 ET open | smc |
| o930 | price vs 09:30 ET open | smc |

## B2-D volume: 598 condition columns, 34 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| rvol | PUBLIC relative volume = bar volume / mean of the same clock bucket over the previous 20 sessions | volume |
| rvol_dir | relative volume signed by the bar colour | volume |
| delta | EXACT bar delta = aggressor buy volume - sell volume (cf2_sec tape) | volume |
| delta_ratio | EXACT delta / volume | volume |
| cvd | EXACT rolling CVD over 10 bars | volume |
| cvdF | EXACT rolling CVD over 5 bars | volume |
| cvdS | EXACT rolling CVD over 30 bars | volume |
| cvd_ema | EXACT cumulative delta minus its EMA20 (delta divergence vs price at the last two swings is the nodiv/divwith condition) | volume |
| vsa_absorb | APPROXIMATION effort vs result: volume > 1.5x avg with spread < 0.6 ATR; absorption of an up bar = -1, of a down bar = +1 | volume |
| vsa_nodemand | APPROXIMATION VSA: no-demand = up bar, narrow spread, volume below both previous bars (-1); no-supply mirror (+1) | volume |
| vsa_climax | APPROXIMATION VSA climax: ultra volume (>2.5x), wide spread, close off the extreme against the bar direction; selling climax +1, buying climax -1 | volume |
| vsa_upthrust | APPROXIMATION VSA upthrust (-1): new 10-bar high, close in lower 30%, volume > 1.5x; spring/test (+1) mirror | volume |
| vsa_stopvol | APPROXIMATION stopping volume: high volume bar closing in the opposite part of its range (+1 down bar closing high) | volume |
| wy_spring_ut | APPROXIMATION Wyckoff (causal) spring (+1): low pierces the 40-bar box low, close back inside; upthrust (-1) mirror | volume |
| wy_sos_sow | APPROXIMATION Wyckoff (causal) sign of strength (+1): close above the box on >1.5x volume and wide spread; sign of weakness (-1) mirror | volume |
| wy_phase | APPROXIMATION Wyckoff phase tag = direction of the last spring/SOS (+) or upthrust/SOW (-) within the last 20 bars | volume |
| vp_psess | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window psess | volume |
| vp_dsess | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window dsess | volume |
| vp_fr240 | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window fr240 | volume |
| vp_fr1440 | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window fr1440 | volume |
| vp_frsw | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window frsw | volume |
| avwap_asia_open | PUBLIC anchored VWAP from asia_open (typical price x volume, 1m) | volume |
| avwap_london_open | PUBLIC anchored VWAP from london_open (typical price x volume, 1m) | volume |
| avwap_ny_open | PUBLIC anchored VWAP from ny_open (typical price x volume, 1m) | volume |
| avwap_nypm_open | PUBLIC anchored VWAP from nypm_open (typical price x volume, 1m) | volume |
| avwap_midnight | PUBLIC anchored VWAP from midnight (typical price x volume, 1m) | volume |
| avwap_week_open | PUBLIC anchored VWAP from week_open (typical price x volume, 1m) | volume |
| avwap_month_open | PUBLIC anchored VWAP from month_open (typical price x volume, 1m) | volume |
| avwap_swing_hi_15m | PUBLIC anchored VWAP from swing_hi_15m (typical price x volume, 1m) | volume |
| avwap_swing_lo_15m | PUBLIC anchored VWAP from swing_lo_15m (typical price x volume, 1m) | volume |
| avwap_swing_hi_60m | PUBLIC anchored VWAP from swing_hi_60m (typical price x volume, 1m) | volume |
| avwap_swing_lo_60m | PUBLIC anchored VWAP from swing_lo_60m (typical price x volume, 1m) | volume |
| avwap_pd_high | PUBLIC anchored VWAP from pd_high (typical price x volume, 1m) | volume |
| avwap_pd_low | PUBLIC anchored VWAP from pd_low (typical price x volume, 1m) | volume |

## B2-E causal ML-style: 222 condition columns, 11 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| kr_dir | APPROXIMATION of jdehorty Kernel Regression (Rational Quadratic, h=8, alpha=1) using ONLY past bars (64-bar one-sided window; repainting end-point form not used); direction = slope of yhat; ev = fast (h-2) kernel crossing the slow one | ml |
| kr_px | price minus kernel estimate (h=8) | ml |
| krF_dir | APPROXIMATION of jdehorty Kernel Regression (Rational Quadratic, h=4, alpha=1) using ONLY past bars (64-bar one-sided window; repainting end-point form not used); direction = slope of yhat; ev = fast (h-1) kernel crossing the slow one | ml |
| krF_px | price minus kernel estimate (h=4) | ml |
| krS_dir | APPROXIMATION of jdehorty Kernel Regression (Rational Quadratic, h=16, alpha=1) using ONLY past bars (64-bar one-sided window; repainting end-point form not used); direction = slope of yhat; ev = fast (h-4) kernel crossing the slow one | ml |
| krS_px | price minus kernel estimate (h=16) | ml |
| lorentzian(1m) | APPROXIMATION of jdehorty Lorentzian Classification: features RSI14, WT(10,11), CCI20, ADX20, RSI9 scaled to 0-1; label = sign of the close 4 bars ahead (only rows whose label is already known); 8 nearest rows by sum log(1+|dx|) among rows sampled every h bars within 1500 (<=5m) / 800 bars; prediction = sum of the 8 labels (-8..8); evaluated at the last completed bar | ml |
| lorentzian(3m) | APPROXIMATION of jdehorty Lorentzian Classification: features RSI14, WT(10,11), CCI20, ADX20, RSI9 scaled to 0-1; label = sign of the close 4 bars ahead (only rows whose label is already known); 8 nearest rows by sum log(1+|dx|) among rows sampled every h bars within 1500 (<=5m) / 800 bars; prediction = sum of the 8 labels (-8..8); evaluated at the last completed bar | ml |
| lorentzian(5m) | APPROXIMATION of jdehorty Lorentzian Classification: features RSI14, WT(10,11), CCI20, ADX20, RSI9 scaled to 0-1; label = sign of the close 4 bars ahead (only rows whose label is already known); 8 nearest rows by sum log(1+|dx|) among rows sampled every h bars within 1500 (<=5m) / 800 bars; prediction = sum of the 8 labels (-8..8); evaluated at the last completed bar | ml |
| lorentzian(15m) | APPROXIMATION of jdehorty Lorentzian Classification: features RSI14, WT(10,11), CCI20, ADX20, RSI9 scaled to 0-1; label = sign of the close 4 bars ahead (only rows whose label is already known); 8 nearest rows by sum log(1+|dx|) among rows sampled every h bars within 1500 (<=5m) / 800 bars; prediction = sum of the 8 labels (-8..8); evaluated at the last completed bar | ml |
| lorentzian(60m) | APPROXIMATION of jdehorty Lorentzian Classification: features RSI14, WT(10,11), CCI20, ADX20, RSI9 scaled to 0-1; label = sign of the close 4 bars ahead (only rows whose label is already known); 8 nearest rows by sum log(1+|dx|) among rows sampled every h bars within 1500 (<=5m) / 800 bars; prediction = sum of the 8 labels (-8..8); evaluated at the last completed bar | ml |

## B2-C2 IRL/ERL sweeps (Addendum 5 Step B): 334 condition columns, 0 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|

## B11 candlestick library: 3370 condition columns, 61 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| cdl_hammer | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): hammer +1 bullish -1 bearish | candle |
| cdl_hanging_man | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): hanging_man +1 bullish -1 bearish | candle |
| cdl_inv_hammer | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): inv_hammer +1 bullish -1 bearish | candle |
| cdl_shooting_star | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): shooting_star +1 bullish -1 bearish | candle |
| cdl_engulfing | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): engulfing +1 bullish -1 bearish | candle |
| cdl_harami | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): harami +1 bullish -1 bearish | candle |
| cdl_harami_cross | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): harami_cross +1 bullish -1 bearish | candle |
| cdl_morning_star | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): morning_star +1 bullish -1 bearish | candle |
| cdl_star_doji | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): star_doji +1 bullish -1 bearish | candle |
| cdl_abandoned_baby | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): abandoned_baby +1 bullish -1 bearish | candle |
| cdl_dark_cloud | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): dark_cloud +1 bullish -1 bearish | candle |
| cdl_piercing | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): piercing +1 bullish -1 bearish | candle |
| cdl_tweezer | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): tweezer +1 bullish -1 bearish | candle |
| cdl_marubozu | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): marubozu +1 bullish -1 bearish | candle |
| cdl_closing_marubozu | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): closing_marubozu +1 bullish -1 bearish | candle |
| cdl_opening_marubozu | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): opening_marubozu +1 bullish -1 bearish | candle |
| cdl_dragonfly | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): dragonfly +1 bullish -1 bearish | candle |
| cdl_gravestone | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): gravestone +1 bullish -1 bearish | candle |
| cdl_takuri | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): takuri +1 bullish -1 bearish | candle |
| cdl_three_inside | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): three_inside +1 bullish -1 bearish | candle |
| cdl_three_outside | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): three_outside +1 bullish -1 bearish | candle |
| cdl_kicker | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): kicker +1 bullish -1 bearish | candle |
| cdl_belt_hold | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): belt_hold +1 bullish -1 bearish | candle |
| cdl_three_soldiers | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): three_soldiers +1 bullish -1 bearish | candle |
| cdl_three_crows | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): three_crows +1 bullish -1 bearish | candle |
| cdl_three_line_strike | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): three_line_strike +1 bullish -1 bearish | candle |
| cdl_advance_block | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): advance_block +1 bullish -1 bearish | candle |
| cdl_deliberation | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): deliberation +1 bullish -1 bearish | candle |
| cdl_stick_sandwich | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): stick_sandwich +1 bullish -1 bearish | candle |
| cdl_matching_low | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): matching_low +1 bullish -1 bearish | candle |
| cdl_homing_pigeon | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): homing_pigeon +1 bullish -1 bearish | candle |
| cdl_ladder_bottom | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): ladder_bottom +1 bullish -1 bearish | candle |
| cdl_unique_three_river | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): unique_three_river +1 bullish -1 bearish | candle |
| cdl_two_crows | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): two_crows +1 bullish -1 bearish | candle |
| cdl_upside_gap_two_crows | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): upside_gap_two_crows +1 bullish -1 bearish | candle |
| cdl_identical_crows | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): identical_crows +1 bullish -1 bearish | candle |
| cdl_thrusting | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): thrusting +1 bullish -1 bearish | candle |
| cdl_in_neck | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): in_neck +1 bullish -1 bearish | candle |
| cdl_on_neck | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): on_neck +1 bullish -1 bearish | candle |
| cdl_separating_lines | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): separating_lines +1 bullish -1 bearish | candle |
| cdl_side_by_side | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): side_by_side +1 bullish -1 bearish | candle |
| cdl_three_methods | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): three_methods +1 bullish -1 bearish | candle |
| cdl_mat_hold | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): mat_hold +1 bullish -1 bearish | candle |
| cdl_tasuki_gap | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): tasuki_gap +1 bullish -1 bearish | candle |
| cdl_breakaway | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): breakaway +1 bullish -1 bearish | candle |
| cdl_counterattack | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): counterattack +1 bullish -1 bearish | candle |
| cdl_inside_break | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): inside_break +1 bullish -1 bearish | candle |
| cdl_inside_break_close | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): inside_break_close +1 bullish -1 bearish | candle |
| cdl_high_wave | APPROXIMATION (neutral pattern, unsigned): high_wave | candle |
| cdl_spinning_top | APPROXIMATION (neutral pattern, unsigned): spinning_top | candle |
| cdl_long_legged_doji | APPROXIMATION (neutral pattern, unsigned): long_legged_doji | candle |
| cdl_doji | APPROXIMATION (neutral pattern, unsigned): doji | candle |
| cdl_rickshaw | APPROXIMATION (neutral pattern, unsigned): rickshaw | candle |
| cdl_long_line | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): long_line +1 bullish -1 bearish | candle |
| cdl_short_line | APPROXIMATION (neutral pattern, unsigned): short_line | candle |
| cdl_tri_star | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): tri_star +1 bullish -1 bearish | candle |
| cdl_inside_bar | APPROXIMATION (neutral pattern, unsigned): inside_bar | candle |
| cdl_outside_bar | APPROXIMATION (neutral pattern, unsigned): outside_bar | candle |
| cdl_pin_bar | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): pin_bar +1 bullish -1 bearish | candle |
| cdl_wide_range_trend | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): wide_range_trend +1 bullish -1 bearish | candle |
| cdl_gap_up_down | APPROXIMATION (Nison/TA-Lib style, thresholds in module doc): gap_up_down +1 bullish -1 bearish | candle |

Block 11 notes: Block 11: candlestick library (~60 patterns), APPROXIMATIONS of Nison / TA-Lib style rules with fixed thresholds (stated in CONFLUENCE_DEFS_CF4.md). All patterns use only bars <= the evaluated bar.
Thresholds (relative to the bar's own range and ATR14): long body: body >= 0.6*range and body >= 0.8*ATR*0.5 ; doji: body <= 0.1*range ; small body: body <= 0.3*range ; marubozu: shadows <= 0.03*range each ; gap = open beyond previous close by >= 0.1*ATR (rare on 24h futures bars; gap-based patterns therefore have low counts on 1-5 min bars) ; trend context: prior-4-bar close change > 0.5 ATR (up/down).
Conditions per pattern and timeframe (1m,3m,5m,15m,60m): side = pattern on the last completed bar in the trade direction; against = opposite; fresh1/fresh3/fresh5 = trade-direction pattern within the last 1/3/5 bars; against3/against5 = opposite within 3/5 bars; *_atlvl = the same only AT a level cluster (>= 2 distinct IRL/ERL range levels within 0.3 ATR15 of the signal price; own levels, because W-CF1 category B columns exist only for taken signals so far); c4_cdl_<tf>_nwith3 / nagainst3 = number of distinct non-neutral patterns with / against the trade in the last 3 bars, with_ge1/2/3, with_gt_against, with_atlvl. Neutral patterns (doji types, spinning top, inside/outside bar, short line) are unsigned: hi/rise only.

## B12 bar-level volume at price (footprint): 197 condition columns, 1 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| footprint (all c4_fp_*) | EXACT from prints: per-bar volume at price (1-tick levels). POC = max-volume tick (first on ties), position = (POC-low)/(high-low) in thirds; stacked imbalance = >=3 consecutive ticks with ask[P] >= 3*bid[P-1] and ask>=10 (buy) or bid[P] >= 3*ask[P+1] and bid>=10 (sell); unfinished auction = both bid and ask volume traded at the bar high (or low) tick; delta at extreme = ask-bid volume in the top / bottom third of the bar range; close delta = delta of the final 20% of the bar volume; centroid = volume-weighted mean tick; absorption = volume >= 2x its 20-bar average with range <= 0.6x its 20-bar average; _lvl = also at a level cluster (>=2 distinct IRL/ERL range levels within 0.3 ATR15); mtf = timeframes (1/3/5/15/60) agreeing | footprint |

## B10 geometry and chart patterns: 1188 condition columns, 75 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| tl_state | APPROXIMATION auto trendlines (pivot k=3): +1 above a valid up-line (2+ touches), -1 below a valid down-line; if both, they cancel | geom |
| tl_break | close beyond the pivot trendline by 0.1 ATR (+1 up-break of a down-line, -1 down-break of an up-line) | geom |
| tl_retest | retest of a just-broken trendline within 10 bars (within 0.15 ATR, close back beyond) | geom |
| tl_touch3 | touch count of the stronger valid trendline (>=3 is "tested") | geom |
| tl_dist_up | ATR distance of price above the up-line (support) | geom |
| tl_slope_up | slope of the up-line in ATR per bar (signed: steeper up = with a long) | geom |
| chan_pos | position inside the trendline channel (parallel through the farthest opposite pivot): +0.5 at the support line, -0.5 at the far line (long likes +) | geom |
| tri_sym | APPROXIMATION geometric pattern from the two pivot trendlines (k=3): tri_sym present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| tri_sym_on | tri_sym present (unsigned) | geom |
| tri_asc | APPROXIMATION geometric pattern from the two pivot trendlines (k=3): tri_asc present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| tri_asc_on | tri_asc present (unsigned) | geom |
| tri_desc | APPROXIMATION geometric pattern from the two pivot trendlines (k=3): tri_desc present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| tri_desc_on | tri_desc present (unsigned) | geom |
| wedge_rising | APPROXIMATION geometric pattern from the two pivot trendlines (k=3): wedge_rising present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| wedge_rising_on | wedge_rising present (unsigned) | geom |
| wedge_falling | APPROXIMATION geometric pattern from the two pivot trendlines (k=3): wedge_falling present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| wedge_falling_on | wedge_falling present (unsigned) | geom |
| rect | APPROXIMATION geometric pattern from the two pivot trendlines (k=3): rect present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| rect_on | rect present (unsigned) | geom |
| broaden | APPROXIMATION geometric pattern from the two pivot trendlines (k=3): broaden present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| broaden_on | broaden present (unsigned) | geom |
| pitchfork | APPROXIMATION Andrews pitchfork from the last three alternating pivots (k=3): ATR distance of price from the median line, ev = median-line cross | geom |
| fib_cluster | APPROXIMATION Fibonacci confluence: number of the last 4 legs (pivots k=3) with a .382/.5/.618/.786/1.272/1.618 level within 0.25 ATR of price (>=2 = cluster) | geom |
| fib_cluster_dir | price at a Fibonacci cluster (>=2 legs) with the sign of the last leg (pullback into a cluster after an up-leg = +1) | geom |
| fib_ext_up | ATR distance to the nearest 1.272/1.618 extension level above price | geom |
| fib_ext_dn | ATR distance to the nearest extension level below price | geom |
| tl_stateS | APPROXIMATION auto trendlines (pivot k=5): +1 above a valid up-line (2+ touches), -1 below a valid down-line; if both, they cancel | geom |
| tl_breakS | close beyond the pivot trendline by 0.1 ATR (+1 up-break of a down-line, -1 down-break of an up-line) | geom |
| tl_retestS | retest of a just-broken trendline within 10 bars (within 0.15 ATR, close back beyond) | geom |
| tl_touch3S | touch count of the stronger valid trendline (>=3 is "tested") | geom |
| tl_dist_upS | ATR distance of price above the up-line (support) | geom |
| tl_slope_upS | slope of the up-line in ATR per bar (signed: steeper up = with a long) | geom |
| chan_posS | position inside the trendline channel (parallel through the farthest opposite pivot): +0.5 at the support line, -0.5 at the far line (long likes +) | geom |
| tri_symS | APPROXIMATION geometric pattern from the two pivot trendlines (k=5): tri_sym present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| tri_sym_onS | tri_sym present (unsigned) | geom |
| tri_ascS | APPROXIMATION geometric pattern from the two pivot trendlines (k=5): tri_asc present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| tri_asc_onS | tri_asc present (unsigned) | geom |
| tri_descS | APPROXIMATION geometric pattern from the two pivot trendlines (k=5): tri_desc present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| tri_desc_onS | tri_desc present (unsigned) | geom |
| wedge_risingS | APPROXIMATION geometric pattern from the two pivot trendlines (k=5): wedge_rising present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| wedge_rising_onS | wedge_rising present (unsigned) | geom |
| wedge_fallingS | APPROXIMATION geometric pattern from the two pivot trendlines (k=5): wedge_falling present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| wedge_falling_onS | wedge_falling present (unsigned) | geom |
| rectS | APPROXIMATION geometric pattern from the two pivot trendlines (k=5): rect present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| rect_onS | rect present (unsigned) | geom |
| broadenS | APPROXIMATION geometric pattern from the two pivot trendlines (k=5): broaden present (flatness threshold 0.005 ATR/bar; ev uses the pattern state of the previous bar); +1/-1 = breakout of its upper/lower line | geom |
| broaden_onS | broaden present (unsigned) | geom |
| pitchforkS | APPROXIMATION Andrews pitchfork from the last three alternating pivots (k=5): ATR distance of price from the median line, ev = median-line cross | geom |
| fib_clusterS | APPROXIMATION Fibonacci confluence: number of the last 4 legs (pivots k=5) with a .382/.5/.618/.786/1.272/1.618 level within 0.25 ATR of price (>=2 = cluster) | geom |
| fib_cluster_dirS | price at a Fibonacci cluster (>=2 legs) with the sign of the last leg (pullback into a cluster after an up-leg = +1) | geom |
| fib_ext_upS | ATR distance to the nearest 1.272/1.618 extension level above price | geom |
| fib_ext_dnS | ATR distance to the nearest extension level below price | geom |
| harmonic | APPROXIMATION harmonic XABCD (pivots k=3) price inside the D zone (+-0.3 ATR): ABCD, Gartley (AB .618, D .786), Bat (AB .382-.5, D .886), Butterfly (AB .786, D 1.27), Crab (AB .382-.618, D 1.618) with ratio tolerance 5%; sign = bullish when the pattern completes at a low | geom |
| harm_abcd | harmonic abcd tolerance 5% | geom |
| harm_gartley | harmonic gartley tolerance 5% | geom |
| harm_bat | harmonic bat tolerance 5% | geom |
| harm_butterfly | harmonic butterfly tolerance 5% | geom |
| harm_crab | harmonic crab tolerance 5% | geom |
| lmw_hs | APPROXIMATION of Lo-Mamaysky-Wang 5-extrema rules (raw fractal pivots k=3 instead of kernel-smoothed extrema; the 1.5 pct / 0.75 pct price tolerances are replaced by ATR-scaled 0.6 ATR / 0.3 ATR because percent-of-price is meaningless intraday): hs top/bottom; state = pattern present on the last 5 alternating pivots (+1 bottom/bullish, -1 top/bearish), ev = close through the neckline | geom |
| lmw_broaden | APPROXIMATION of Lo-Mamaysky-Wang 5-extrema rules (raw fractal pivots k=3 instead of kernel-smoothed extrema; the 1.5 pct / 0.75 pct price tolerances are replaced by ATR-scaled 0.6 ATR / 0.3 ATR because percent-of-price is meaningless intraday): broaden top/bottom; state = pattern present on the last 5 alternating pivots (+1 bottom/bullish, -1 top/bearish), ev = close through the neckline | geom |
| lmw_tri | APPROXIMATION of Lo-Mamaysky-Wang 5-extrema rules (raw fractal pivots k=3 instead of kernel-smoothed extrema; the 1.5 pct / 0.75 pct price tolerances are replaced by ATR-scaled 0.6 ATR / 0.3 ATR because percent-of-price is meaningless intraday): tri top/bottom; state = pattern present on the last 5 alternating pivots (+1 bottom/bullish, -1 top/bearish), ev = close through the neckline | geom |
| lmw_rect | APPROXIMATION of Lo-Mamaysky-Wang 5-extrema rules (raw fractal pivots k=3 instead of kernel-smoothed extrema; the 1.5 pct / 0.75 pct price tolerances are replaced by ATR-scaled 0.6 ATR / 0.3 ATR because percent-of-price is meaningless intraday): rect top/bottom; state = pattern present on the last 5 alternating pivots (+1 bottom/bullish, -1 top/bearish), ev = close through the neckline | geom |
| lmw_double | APPROXIMATION of Lo-Mamaysky-Wang 5-extrema rules (raw fractal pivots k=3 instead of kernel-smoothed extrema; the 1.5 pct / 0.75 pct price tolerances are replaced by ATR-scaled 0.6 ATR / 0.3 ATR because percent-of-price is meaningless intraday): double top/bottom; state = pattern present on the last 5 alternating pivots (+1 bottom/bullish, -1 top/bearish), ev = close through the neckline | geom |
| harmonic_loose | APPROXIMATION harmonic XABCD (pivots k=3) price inside the D zone (+-0.3 ATR): ABCD, Gartley (AB .618, D .786), Bat (AB .382-.5, D .886), Butterfly (AB .786, D 1.27), Crab (AB .382-.618, D 1.618) with ratio tolerance 10%; sign = bullish when the pattern completes at a low | geom |
| harm_abcd_loose | harmonic abcd tolerance 10% | geom |
| harm_gartley_loose | harmonic gartley tolerance 10% | geom |
| harm_bat_loose | harmonic bat tolerance 10% | geom |
| harm_butterfly_loose | harmonic butterfly tolerance 10% | geom |
| harm_crab_loose | harmonic crab tolerance 10% | geom |
| flag | APPROXIMATION flag: pole >= 3 ATR within 10 bars, consolidation 5-25 bars with range <= 40% of the pole, ev = break in the pole direction | geom |
| pennant | flag whose second half is < 60% of the first-half range (converging = pennant) | geom |
| cup_handle | APPROXIMATION cup and handle: rim-bottom-rim (>=3 ATR deep, bottom in the middle third, right rim within 10% of depth) + handle <= 1/3 depth; ev = close above the right rim | geom |
| pnf | PUBLIC point-and-figure (close-based, box=4 pts, 3-box reversal): column direction, ev = double-top / double-bottom breakout | geom |
| threeline | PUBLIC three-line break on closes: colour of the last line, ev = reversal | geom |
| kagi | APPROXIMATION Kagi on closes with reversal = 1 ATR(14) at the bar: thickness yang(+1)/yin(-1), ev = thickness change | geom |

Block 10 notes: Block 10: geometry and chart patterns, MECHANICAL versions on completed bars (3/5/15/60-min). Pivots = fractal pivots of strength k, usable k bars after the pivot bar, kept ALTERNATING (a same-type pivot replaces the previous one only if more extreme, at the time it is confirmed).
Published rule vs approximation is stated per spec in the formula field. Tolerance disagreement for harmonics and LMW patterns is reported by c4_geom_tol.py.
Timeframes 3/5/15/60-min. Each pattern lists PUBLISHED RULE or APPROXIMATION in the formula column; tolerance disagreement table: autopilot/CF4_GEOM_TOL.md (harmonics 5 pct vs 10 pct ratio tolerance, pivot strength 3 vs 5 for trendlines / triangles / wedges / Fibonacci clusters).

## B4 alternate bars: ha1: 2311 condition columns (c4_<ind>_ha1_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: ha15: 2311 condition columns (c4_<ind>_ha15_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: ha3: 2311 condition columns (c4_<ind>_ha3_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: ha5: 2311 condition columns (c4_<ind>_ha5_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: ha60: 2311 condition columns (c4_<ind>_ha60_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: range16: 2311 condition columns (c4_<ind>_range16_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: range8: 2311 condition columns (c4_<ind>_range8_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: renko16: 2311 condition columns (c4_<ind>_renko16_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: renko8: 2311 condition columns (c4_<ind>_renko8_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: tick2000: 2311 condition columns (c4_<ind>_tick2000_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: vol2000: 2311 condition columns (c4_<ind>_vol2000_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## B4 alternate bars: vol500: 2311 condition columns (c4_<ind>_vol500_<cond>); same indicator definitions as Block 2 sub-blocks osc/trend/smc/vol(bar part: no tape delta/rvol)/ml(kernel) plus W-CF1 classic set (prefix w1_); bars from /mnt/l2/l2vast/_confl/altbars (APPROXIMATION: per-second tape path)

## Block 10 tolerance disagreement (how often two tolerances disagree)

| bars | item | A | B | active A | active B | both | A only | B only | disagree share of union |
|---|---|---|---|---|---|---|---|---|---|
| 3m | harmonic | tol 5pct | tol 10pct | 10831 | 13118 | 10831 | 0 | 2287 | 0.17 |
| 3m | harm_gartley | tol 5pct | tol 10pct | 650 | 1364 | 650 | 0 | 714 | 0.52 |
| 3m | harm_bat | 5pct | 10pct | 409 | 605 | 409 | 0 | 196 | 0.32 |
| 3m | harm_butterfly | 5pct | 10pct | 465 | 954 | 465 | 0 | 489 | 0.51 |
| 3m | harm_crab | 5pct | 10pct | 195 | 271 | 195 | 0 | 76 | 0.28 |
| 3m | harm_abcd | 5pct | 10pct | 9112 | 9924 | 8882 | 230 | 1042 | 0.13 |
| 3m | trendline state | pivot k=3 | pivot k=5 | 220651 | 211687 | 135565 | 85086 | 76122 | 0.54 |
| 3m | sym triangle on | k=3 | k=5 | 17478 | 15526 | 6688 | 10790 | 8838 | 0.75 |
| 3m | wedge rising on | k=3 | k=5 | 28484 | 26536 | 11054 | 17430 | 15482 | 0.75 |
| 3m | fib cluster>=2 | k=3 | k=5 | 169835 | 136001 | 108390 | 61445 | 27611 | 0.45 |
| 5m | harmonic | tol 5pct | tol 10pct | 6452 | 7781 | 6452 | 0 | 1329 | 0.17 |
| 5m | harm_gartley | tol 5pct | tol 10pct | 369 | 789 | 369 | 0 | 420 | 0.53 |
| 5m | harm_bat | 5pct | 10pct | 208 | 334 | 208 | 0 | 126 | 0.38 |
| 5m | harm_butterfly | 5pct | 10pct | 258 | 566 | 258 | 0 | 308 | 0.54 |
| 5m | harm_crab | 5pct | 10pct | 122 | 163 | 122 | 0 | 41 | 0.25 |
| 5m | harm_abcd | 5pct | 10pct | 5495 | 5929 | 5325 | 170 | 604 | 0.13 |
| 5m | trendline state | pivot k=3 | pivot k=5 | 132814 | 124465 | 80278 | 52536 | 44187 | 0.55 |
| 5m | sym triangle on | k=3 | k=5 | 10434 | 9439 | 3841 | 6593 | 5598 | 0.76 |
| 5m | wedge rising on | k=3 | k=5 | 17294 | 15407 | 6360 | 10934 | 9047 | 0.76 |
| 5m | fib cluster>=2 | k=3 | k=5 | 101435 | 81122 | 65017 | 36418 | 16105 | 0.45 |
| 15m | harmonic | tol 5pct | tol 10pct | 1774 | 2153 | 1774 | 0 | 379 | 0.18 |
| 15m | harm_gartley | tol 5pct | tol 10pct | 116 | 239 | 116 | 0 | 123 | 0.51 |
| 15m | harm_bat | 5pct | 10pct | 89 | 124 | 89 | 0 | 35 | 0.28 |
| 15m | harm_butterfly | 5pct | 10pct | 69 | 170 | 69 | 0 | 101 | 0.59 |
| 15m | harm_crab | 5pct | 10pct | 27 | 46 | 27 | 0 | 19 | 0.41 |
| 15m | harm_abcd | 5pct | 10pct | 1473 | 1574 | 1427 | 46 | 147 | 0.12 |
| 15m | trendline state | pivot k=3 | pivot k=5 | 42127 | 38906 | 24332 | 17795 | 14574 | 0.57 |
| 15m | sym triangle on | k=3 | k=5 | 3559 | 2604 | 1206 | 2353 | 1398 | 0.76 |
| 15m | wedge rising on | k=3 | k=5 | 4961 | 4173 | 1483 | 3478 | 2690 | 0.81 |
| 15m | fib cluster>=2 | k=3 | k=5 | 33037 | 25547 | 20457 | 12580 | 5090 | 0.46 |
| 60m | harmonic | tol 5pct | tol 10pct | 307 | 371 | 307 | 0 | 64 | 0.17 |
| 60m | harm_gartley | tol 5pct | tol 10pct | 18 | 32 | 18 | 0 | 14 | 0.44 |
| 60m | harm_bat | 5pct | 10pct | 25 | 30 | 25 | 0 | 5 | 0.17 |
| 60m | harm_butterfly | 5pct | 10pct | 10 | 27 | 10 | 0 | 17 | 0.63 |
| 60m | harm_crab | 5pct | 10pct | 17 | 23 | 17 | 0 | 6 | 0.26 |
| 60m | harm_abcd | 5pct | 10pct | 237 | 259 | 229 | 8 | 30 | 0.14 |
| 60m | trendline state | pivot k=3 | pivot k=5 | 9259 | 9956 | 5449 | 3810 | 4507 | 0.60 |
| 60m | sym triangle on | k=3 | k=5 | 684 | 686 | 286 | 398 | 400 | 0.74 |
| 60m | wedge rising on | k=3 | k=5 | 1216 | 1439 | 493 | 723 | 946 | 0.77 |
| 60m | fib cluster>=2 | k=3 | k=5 | 7250 | 5595 | 4330 | 2920 | 1265 | 0.49 |
## IRL / ERL (Addendum 5) - PRE-REGISTERED DEFINITIONS IRL_ERL_V0 (frozen before any Step A aggregate was computed; not tuned afterwards)
Code: code/th_confl_cf4/c4_irl_lib.py (ranges, scan, post-sweep metrics), c4_irl_events.py (events), c4_irl_score.py (tables). Events: /mnt/l2/l2vast/_confl/irl/ev_<variant>.parquet (ctrl=True rows are the random-level control).
Bars: NQ 1m (/mnt/l2/l2vast/_th_sz/bars1m_NQ.npz), sweep bars 1/3/5/15 min built from them, epoch-aligned, a bar is visible only after its end. ET sessions: asia 18:00-02:00, london 02:00-09:30, ny 09:30-16:00 (16:00-18:00 'gap'). ATR unit everywhere = 5-min ATR(14, Wilder) at the confirming close.
RANGES (13 definitions, each scored separately; values known only from completed bars): a_pd prior RTH day (09:30-16:00 ET) high/low, valid until the next RTH close; b_ps prior session high/low (the session that ended last: NY->Asia->London->NY); b_cs60 current session running high/low (bars before the poke bar), active once the session is 60 min old; c_on overnight range 18:00-09:30 valid 09:30-16:00; d_wk prior week (Sun 18:00-Fri 17:00 ET) high/low; e<TF>_<s> dealing range on 15/60/240-min bars = last confirmed major swing high and low (fractal strength s=10 or 20 bars each side, confirmed s bars late; invalid if high<=low); f_or30/f_or60 opening range of each session (first 30/60 min of Asia, London, NY) valid from its end to session end. NOT implemented (stated): 'equal highs/lows AT the range extreme' as an extra external level (the extreme itself only).
LEVELS: EXTERNAL = the range's own high/low. INTERNAL = (minor) confirmed fractal pivots of strength p (2/3/5) on the sweep bars, (eq) equal highs/lows = a pivot within 0.1 ATR of an earlier unswept same-side pivot within 24 h (level = the more extreme of the two), (fvg) far edge of an unfilled 3-candle FVG >= 0.1 ATR (bull FVG bottom, bear FVG top); an internal level must lie strictly inside (RL,RH) of the range at the confirming close. A level can carry several tags (external to one range, internal to a larger one): tag_<range> = 1 external, 2 internal, 0 neither. Levels live 24 h (ranges: until the range value changes), and a level is consumed by its FIRST touch.
SWEEP: first bar whose high (low) reaches the level; if it trades beyond by >= thr (1 tick 0.25 / 2 pts / 0.1 ATR of the sweep bar) and within W bars (1/2/3/5, counting the poke bar) a bar CLOSES back on the original side, the sweep is stamped at that close (entry = that close, fade direction d = -1 for a high swept, +1 for a low). A touch smaller than thr, or no close back within W bars, is not a sweep. Recorded per sweep: poke depth (extreme - level), bars from poke to close back, volume over the poke bars, delta (APPROXIMATION: close-location-value delta per bar x volume; exact tape delta joins later), ET time, session.
HEADLINE = sweep bars 5 min, thr 2 pts, W 3, minor pivot p 3. One-at-a-time sensitivities: tf 1/3/15, thr tick / 0.1 ATR, W 1/2/5, p 2/5.
MEASURES after the confirming close, horizons 15/30/60/120 min (1m bars): fav = max favourable excursion for the fade; net = fade return at the horizon close; mae = max adverse excursion for a fade entered at the close back inside; cont = 1 if any 1m close re-closes beyond the swept level (continuation); stop = 1 if adverse reaches the poke extreme +2 pts. All in points, divided by ATR in the tables.
CONTROLS: (1) ext vs int matched on poke depth (terciles), time of day (ET hour) and volatility (ATR terciles), cell-weighted difference with week-block bootstrap CI; (2) random levels: each real level is replaced by a level at the SAME distance from the price at its birth on a random side (2 seeds), pushed through the identical sweep scan and tags.
WORKED NQ EXAMPLES (headline). EXTERNAL: 2026-10-01 20:30 ET (Globex day 10-02, Asia) 5-min close back below the prior-day high: level 27151.25 (a_pd high; also external to b_ps and e15; internal to d_wk), poke high 27187.75 (36.5 pts beyond, 3 bars, 2 closes beyond), confirmed close 27112.25, fade short d=-1. INTERNAL: 2026-09-30 19:20 ET (Asia) a confirmed minor swing low at 27032.00 (inside prior-day and prior-session ranges, tags internal) poked to 27022.00 (10 pts) and closed back above; confirmed close 27039.75, fade long d=+1.

## Dropped / rebuilt-causal list (W-CF4, no repainting)
- Nadaraya-Watson envelope, LuxAlgo end-point (repainting) form: DROPPED. Rebuilt as a one-sided Gaussian kernel over past bars only (nwe, nweF, nweS); APPROXIMATION.
- Kernel Regression (jdehorty) end-point/Nadaraya-Watson repaint behaviour: rebuilt with a one-sided Rational Quadratic kernel on past bars only (kr*).
- ZigZag / ZigZag++ and any swing indicator drawn at the pivot bar: DROPPED as plotted; replaced by fractal pivots usable only k bars after the pivot (confirmed-pivot version everywhere: BOS/CHoCH, OB, SD, premium/discount, OTE, divergence).
- Williams fractals: only the confirmed form (usable 2 bars late). Alligator forward-shifted lines: causal reading (value at t is the line computed `shift` bars earlier). Ichimoku: cloud at t = spans computed 26 bars earlier; chikou compared with price 26 bars earlier; future cloud colour is known at t.
- Market Cipher B: proprietary, DROPPED as the original; APPROXIMATION composite (WaveTrend + money flow + RSI) built instead (mcwt, mcmf, mc_comp).
- Lorentzian Classification (jdehorty): APPROXIMATION; labels are used only for rows whose forward return window is already complete at the signal bar.
- Volume profile / anchored VWAP: use bars completed before the signal second only.
- Not built in this pass: Elliott/harmonic patterns, Tr3ndy/proprietary Simpler tools (Block 1 owner W-CF1).


# ===== Block 3 (W-CF5) : merged verbatim from CONFLUENCE_DEFS_CF5.md =====
**UNIVERSE NOTE (2026-11-15):** all CF5 parquet files are keyed by sig_id = book7_sig_ts over the W-CF1 signals_all.parquet universe (48,353 signals, taken + skipped), 1-min bars from uwbooks/min1_NQ.npz (to 2026-11-13) with a 2021-06..2023-01 warm-up prefix from cf6_min1_NQ_long.npz shifted to the unadjusted level. Category letter for the search: N (prefix n_). Files: A_named_hs, B_sess_named, B2_sessanch_named, C1_exec_named, C2_flow_named, D_statext_named under /mnt/l2/l2vast/_confl/cols_cf5/. Rebuild everything: code/th_confl_cf5/run_all.sh.

## Block 3 sub-block A: named-system indicators on HTF bars (DeMark, Raschke, Connors, Chande, Wilder, Kase, Ehlers, Brooks, statistical desk measures)

Columns: parquet /mnt/l2/l2vast/_confl/cols_cf5/A_named_hs.parquet keyed by sig_id (= book7_sig_ts, same as entry table). Column = n_<indicator>_<tf>_<cond> (int8: 1 yes, 0 no, -1 unknown/not yet defined) and n_v_<indicator>_<tf> raw value (float32). tf in 1m,3m,5m,15m,60m,1d (1d = RTH daily bars 09:30-16:00 ET, visible after 16:00 ET; 1-60m use all 24h 1-min NQ bars). Sign: every condition is with the trade side (long/short).

Causality: HTF bar visible only when its end <= signal second; kernels are recursive/rolling (bar i uses bars <= i). Checked: recomputing on bars truncated at the signal second reproduces the raw values (1,808 values, 0 mismatches).

Conditions per series (template): side (state on trade side of midline/signal), sig (vs signal line), rise (turning/rising with trade), ewith/eagainst/eleave (in extreme with/against, left extreme in last 3 bars), nodiv/divwith (no divergence against / divergence in favour at last fractal swing), hi (unsigned above threshold), agree3of4/agree4of4 (side true on 3m,5m,15m,60m). Event series: with1, with3, with10 (fresh signal in trade direction this bar / last 3 / last 10 bars), against3, against10, state / against_state (last signal within 30 bars). Count series: with_ge<k>, against_ge<k>, with_rising.

Standard settings first, then fast and slow variants where named _std/_fast/_slow. Dropped/covered elsewhere: ADX/DI, parabolic SAR, plain Williams %R, Wilder RSI, ATR are W-CF1 category M/E (not duplicated). REI, Kase true KPO peak-outs, MAMA-based trend-mode sine tests: approximated or not built, see formulas.

| indicator | formula (PUBLIC = published exact; APPROX = assumption stated) |
|---|---|
| dm_setup | PUBLIC: TD Setup (9 consecutive closes below/above close 4 bars earlier, after price flip); signed + = buy setup count (bullish exhaustion build) |
| dm_setup9_perf | PUBLIC: perfected setup 9 (bar 8 or 9 low below lows of bars 6,7; sell mirror); + = perfected BUY setup (bullish signal) |
| dm_setup9_any | PUBLIC: setup 9 completed, perfected or not |
| dm_cd | PUBLIC: TD Countdown (13 non-consecutive closes <= low 2 bars earlier, starts at setup 9; cancelled by opposite setup or close beyond TDST; recycles on new setup); + = buy countdown count |
| dm_cd13 | PUBLIC: countdown 13 with qualifier (bar-13 low <= close of countdown bar 8); + bullish |
| dm_cd13u | PUBLIC: first countdown-13 candidate bar regardless of qualifier |
| dm_combo | APPROX: TD Combo countdown (close<=low[2], low<prior low, close<prior close, close<=last counted close; mirrored) - published rule set recalled, exact vendor edge cases unverified |
| dm_combo13 | APPROX: TD Combo 13 event |
| dm_tdst | PUBLIC: close above latest TDST resistance (high of last completed buy setup) / below latest TDST support (low of last completed sell setup) |
| dm_flip | PUBLIC: TD price flip (close vs close 4 bars ago flips against close[1] vs close[5]); + bullish flip |
| dm_supply_line | APPROX: TD supply line = line through the last two descending TD highs (bar higher than both neighbours, confirmed 1 bar later); value = (close-line)/ATR14; nan if no valid line |
| dm_demand_line | APPROX: TD demand line through last two ascending TD lows; (close-line)/ATR14 |
| dm_line_break | APPROX: close crosses above supply line (+) or below demand line (-) |
| rk_310_std | PUBLIC: 3/10 oscillator (SMA3-SMA10 of (H+L)/2, signal SMA16) std=(3,10,16) |
| rk_310h_std | PUBLIC: 3/10 oscillator histogram (osc - signal) std |
| rk_310_fast | PUBLIC: 3/10 oscillator (SMA3-SMA10 of (H+L)/2, signal SMA16) fast=(2,5,8) |
| rk_310h_fast | PUBLIC: 3/10 oscillator histogram (osc - signal) fast |
| rk_310_slow | PUBLIC: 3/10 oscillator (SMA3-SMA10 of (H+L)/2, signal SMA16) slow=(5,20,30) |
| rk_310h_slow | PUBLIC: 3/10 oscillator histogram (osc - signal) slow |
| rk_grail_std | PUBLIC (Raschke holy grail): ADX14>30, trend by DI, bar touches EMA20 and closes on trend side; signal bar = completed setup bar (Raschke enters on break of its extreme = later bar) |
| rk_grail_fast | PUBLIC (Raschke holy grail): ADX14>25, trend by DI, bar touches EMA10 and closes on trend side; signal bar = completed setup bar (Raschke enters on break of its extreme = later bar) |
| rk_grail_slow | PUBLIC (Raschke holy grail): ADX14>30, trend by DI, bar touches EMA34 and closes on trend side; signal bar = completed setup bar (Raschke enters on break of its extreme = later bar) |
| rk_8020_std | APPROX (Raschke 80-20 reversal): prior bar opened in top 20% and closed in bottom 20% (or mirror), signal on the next completed bar closing beyond prior close |
| rk_8020_slow | APPROX (Raschke 80-20 reversal): prior bar opened in top 10% and closed in bottom 10% (or mirror), signal on the next completed bar closing beyond prior close |
| rk_8020_fast | APPROX (Raschke 80-20 reversal): prior bar opened in top 30% and closed in bottom 30% (or mirror), signal on the next completed bar closing beyond prior close |
| rk_soup_std | PUBLIC (Raschke turtle soup): new 20-bar low (high) whose prior 20-bar low was set >= 4 bars earlier, closing back above it; + bullish |
| rk_soup_fast | PUBLIC (Raschke turtle soup): new 10-bar low (high) whose prior 10-bar low was set >= 3 bars earlier, closing back above it; + bullish |
| rk_soup_slow | PUBLIC (Raschke turtle soup): new 40-bar low (high) whose prior 40-bar low was set >= 4 bars earlier, closing back above it; + bullish |
| rk_anti | APPROX (Raschke Anti): slow stochastic K(7,4) hooks back in the direction of a rising/falling D(SMA10) after one counter bar |
| rk_anti_d | PUBLIC stochastic parameters (7,4,10), Anti oscillator D line |
| cn_rsi2_std | PUBLIC Wilder RSI(2) with Connors thresholds (10,90) |
| cn_rsi_pb_std | PUBLIC (Connors RSI(2) pullback): RSI<10 with close above SMA(long trend), mirror for shorts |
| cn_rsi2_fast | PUBLIC Wilder RSI(2) with Connors thresholds (5,95) |
| cn_rsi_pb_fast | PUBLIC (Connors RSI(2) pullback): RSI<5 with close above SMA(sma50), mirror for shorts |
| cn_rsi3_slow | PUBLIC Wilder RSI(3) with Connors thresholds (20,80) |
| cn_rsi_pb_slow | PUBLIC (Connors RSI(3) pullback): RSI<20 with close above SMA(long trend), mirror for shorts |
| cn_cumrsi | PUBLIC (Connors cumulative RSI(2) 2 bars): sum<35 above SMA200 / >165 below |
| cn_cumrsi_raw | PUBLIC cumulative RSI(2) (2-bar sum) |
| cn_double7 | PUBLIC (Connors double sevens): close = 7-bar low while above SMA200 (mirror) |
| cn_double7_fast | APPROX fast variant: 3-bar low above SMA50 |
| cn_double7_slow | APPROX slow variant: 14-bar low above SMA200 |
| cn_ibs | PUBLIC IBS=(C-L)/(H-L); x = 0.5-IBS so + means closed near low (Connors mean-reversion long) |
| ch_fosc_std | PUBLIC Chande forecast oscillator 100*(C-TSF)/C, TSF=14-bar linear regression forecast, signal SMA3 |
| ch_fosc_fast | PUBLIC Chande forecast oscillator 100*(C-TSF)/C, TSF=7-bar linear regression forecast, signal SMA3 |
| ch_fosc_slow | PUBLIC Chande forecast oscillator 100*(C-TSF)/C, TSF=28-bar linear regression forecast, signal SMA3 |
| ch_dmi | PUBLIC Chande dynamic momentum index (variable RSI lookback 14/V clipped 5..30) |
| wl_volstop_std | PUBLIC Wilder volatility system: ATR(7) x 3.0 trail from significant close, ratchets; flips on close through stop |
| wl_volstop_flip_std | flip event of Wilder volatility stop |
| wl_volstop_dist_std | distance close - stop in ATR14, signed by stop side only meaningful with direction |
| wl_volstop_fast | PUBLIC Wilder volatility system: ATR(7) x 2.0 trail from significant close, ratchets; flips on close through stop |
| wl_volstop_flip_fast | flip event of Wilder volatility stop |
| wl_volstop_dist_fast | distance close - stop in ATR14, signed by stop side only meaningful with direction |
| wl_volstop_slow | PUBLIC Wilder volatility system: ATR(14) x 3.0 trail from significant close, ratchets; flips on close through stop |
| wl_volstop_flip_slow | flip event of Wilder volatility stop |
| wl_volstop_dist_slow | distance close - stop in ATR14, signed by stop side only meaningful with direction |
| ks_devstop1 | APPROX Kase Dev-Stop 1: trailing stop distance = mean(RTR,30)+1*std(RTR,30) from significant close (Kase uses 2-bar extreme; ratchet logic assumed) |
| ks_devstop2 | APPROX Kase Dev-Stop 2: trailing stop distance = mean(RTR,30)+2*std(RTR,30) from significant close (Kase uses 2-bar extreme; ratchet logic assumed) |
| ks_devstop3 | APPROX Kase Dev-Stop 3: trailing stop distance = mean(RTR,30)+3*std(RTR,30) from significant close (Kase uses 2-bar extreme; ratchet logic assumed) |
| ks_peak8 | APPROX Kase Peak Oscillator: 8-bar log-return normalised by its 200-bar std (true KPO uses cycle-length scaling; not published exactly) |
| ks_peak14 | APPROX Kase Peak Oscillator: 14-bar log-return normalised by its 200-bar std (true KPO uses cycle-length scaling; not published exactly) |
| ks_peak25 | APPROX Kase Peak Oscillator: 25-bar log-return normalised by its 200-bar std (true KPO uses cycle-length scaling; not published exactly) |
| eh_ss10 | PUBLIC SuperSmoother(10): value = price - SS; rise = SS slope |
| eh_ss6 | PUBLIC SuperSmoother(6): value = price - SS; rise = SS slope |
| eh_ss20 | PUBLIC SuperSmoother(20): value = price - SS; rise = SS slope |
| eh_roof_std | PUBLIC roofing filter HP48+SS10, normalised by 50-bar RMS; signal = prior value (turn) |
| eh_roof_fast | PUBLIC roofing filter HP30+SS6, normalised by 50-bar RMS; signal = prior value (turn) |
| eh_roof_slow | PUBLIC roofing filter HP80+SS15, normalised by 50-bar RMS; signal = prior value (turn) |
| eh_mama_std | PUBLIC MAMA/FAMA (fast 0.5 slow 0.05): (MAMA-FAMA)/ATR, MAMA slope |
| eh_mamapx_std | price vs MAMA in ATR |
| eh_dcp_long | PUBLIC homodyne dominant cycle period (bars); yes = long cycle (>20) |
| eh_dcp_short | PUBLIC dominant cycle period; yes = short cycle (<14) |
| eh_snr | APPROX Ehlers SNR (dB): amplitude of Hilbert I/Q over smoothed squared range, public block recalled |
| eh_trendmode | APPROX trend mode: |price - SMA(dominant cycle)| in ATR14 (Ehlers uses 1.5% of price + sinewave tests) |
| eh_mama_fast | PUBLIC MAMA/FAMA (fast 0.8 slow 0.1): (MAMA-FAMA)/ATR, MAMA slope |
| eh_mamapx_fast | price vs MAMA in ATR |
| eh_mama_slow | PUBLIC MAMA/FAMA (fast 0.25 slow 0.025): (MAMA-FAMA)/ATR, MAMA slope |
| eh_mamapx_slow | price vs MAMA in ATR |
| eh_ebsw_std | PUBLIC even-better sinewave (HP40, SS10) |
| eh_ebsw_fast | PUBLIC even-better sinewave (HP20, SS6) |
| eh_ebsw_slow | PUBLIC even-better sinewave (HP80, SS15) |
| eh_cyber_std | PUBLIC cyber cycle alpha=0.07 normalised; signal = prior value |
| eh_cyber_fast | PUBLIC cyber cycle alpha=0.15 normalised; signal = prior value |
| eh_cyber_slow | PUBLIC cyber cycle alpha=0.035 normalised; signal = prior value |
| bk_trendbars10 | PUBLIC definition (body>=60% of range): bull trend bars minus bear trend bars over 10 bars |
| bk_dojis10 | doji count (body<=25% range) over 10 bars; yes = many dojis (balance/chop) |
| bk_trendbars20 | PUBLIC definition (body>=60% of range): bull trend bars minus bear trend bars over 20 bars |
| bk_dojis20 | doji count (body<=25% range) over 20 bars; yes = many dojis (balance/chop) |
| bk_trendbars5 | PUBLIC definition (body>=60% of range): bull trend bars minus bear trend bars over 5 bars |
| bk_dojis5 | doji count (body<=25% range) over 5 bars; yes = many dojis (balance/chop) |
| bk_h2l2 | APPROX Brooks H2/L2: second pullback-break bar in EMA20 context (counter resets on new 10-bar extreme) |
| bk_h1h2 | APPROX Brooks H1 or H2 / L1 or L2 signal bar |
| bk_alwaysin | APPROX Brooks always-in: flips on strong trend bar (body>=60%) closing beyond EMA20 and 5-bar extreme |
| bk_micro | APPROX micro channel: signed run of consecutive higher-low/higher-high (lower-high/lower-low) bars |
| bk_failbo_std | APPROX Brooks failed breakout: new 20-bar extreme within last 3 bars, first close back inside; + bullish (failed breakdown) |
| bk_failbo_fast | APPROX Brooks failed breakout: new 10-bar extreme within last 2 bars, first close back inside; + bullish (failed breakdown) |
| bk_failbo_slow | APPROX Brooks failed breakout: new 40-bar extreme within last 5 bars, first close back inside; + bullish (failed breakdown) |
| bk_mm_room | APPROX measured move: projected target = last swing low + (last swing high - prior swing low); room = (target - close)/ATR (bull leg context) |
| st_zma20 | PUBLIC z-score of close vs SMA(20) using 20-bar std of close |
| st_zma50 | PUBLIC z-score of close vs SMA(50) using 50-bar std of close |
| st_zma200 | PUBLIC z-score of close vs SMA(200) using 200-bar std of close |
| st_vr_q4_w60 | PUBLIC Lo-MacKinlay variance ratio VR(q=4) over 60 bars (overlapping, no bias correction); yes = trending (VR>1) |
| st_vrlow_q4_w60 | mean-reversion side of VR (yes = VR<1) |
| st_vr_q8_w120 | PUBLIC Lo-MacKinlay variance ratio VR(q=8) over 120 bars (overlapping, no bias correction); yes = trending (VR>1) |
| st_vrlow_q8_w120 | mean-reversion side of VR (yes = VR<1) |
| st_hurst | APPROX Hurst from variance ratio: H=0.5+ln VR(q)/(2 ln q), q=8, 120 bars |
| st_vr_q2_w30 | PUBLIC Lo-MacKinlay variance ratio VR(q=2) over 30 bars (overlapping, no bias correction); yes = trending (VR>1) |
| st_vrlow_q2_w30 | mean-reversion side of VR (yes = VR<1) |
| st_nqlag_es30 | PUBLIC residual: beta(30 bars) x ES 3-bar return - NQ 3-bar return, z-scored (120 bars); + = NQ lagging ES up |
| st_corr_es | PUBLIC rolling correlation of NQ and ES bar returns, 60 bars |
| st_es_leads | PUBLIC lead-lag: corr(NQ_t, ES_t-1) - corr(ES_t, NQ_t-1) over 60 bars; yes = ES leads |
| st_nqlag_es60 | PUBLIC residual: beta(60 bars) x ES 3-bar return - NQ 3-bar return, z-scored (120 bars); + = NQ lagging ES up |
| st_nqlag_es120 | PUBLIC residual: beta(120 bars) x ES 3-bar return - NQ 3-bar return, z-scored (120 bars); + = NQ lagging ES up |
| st_amihud | PUBLIC Amihud illiquidity: mean(|ret|/(price*volume)) 20 bars relative to 200-bar mean |

## Block 3 sub-block B: session / daily named systems (file cols_cf5/B_sess_named.parquet, builder code/th_confl_cf5/cf5_sess.py + cf5_days.py)
Same keys and naming (n_<system>_<name>, int8 1/0/-1, raw n_v_*). Day = RTH 09:30-16:00 ET (1-pt TPO rows, 30-min brackets A..M). Prior-day features use the last RTH day completed (16:00 ET) before the signal second and are defined for every signal; "RTH-today" features (ORB, stretch, volatility breakout, oops, ACD, 80% rule, developing IB / POC) are defined only for signals inside 09:30-16:00 ET (else -1; about 70% of signals are outside RTH). Signals after 2026-10-16 21:00Z (bar store end) are -1. "with" = in the trade's direction. Causality verified by truncated-history recompute (552 values, 0 mismatches).
| prefix | condition | definition |
|---|---|---|
| cb_ (Crabel) | nr4, nr7 | PUBLIC: prior RTH day range is the narrowest of the last 4 / 7 RTH days |
| cb_ | inside, inside_nr4, outside | PUBLIC: prior day inside / outside the day before; inside day that is also NR4 |
| cb_ | prior_wide / prior_narrow | prior-day range / mean of previous 10 ranges > 1.5 / < 0.6 |
| cb_ | orb5/15/30 beyond, fresh15, failed, against_beyond, narrow | PUBLIC opening-range breakout on the first 5/15/30 min of RTH: price beyond OR in trade direction; first completed 1-min close beyond OR within last 15 min; closed beyond earlier but back inside OR; beyond OR on the other side; OR width below the 33rd percentile of the previous 60 days (APPROX threshold) |
| cb_ | stretch_std/fast/slow beyond, hit | PUBLIC Crabel stretch = mean over previous 10 (fast 5, slow 20) days of min(open-low, high-open); price beyond today's RTH open +/- stretch in trade direction (now) / touched since open |
| dl_ (Dalton) | pd_trend_with/against, pd_normvar_with/against, pd_nontrend, pd_normal, pd_neutral, pd_neutral_ext, pd_double | APPROX day-type of prior day from IB (first 60 min) and range extension: normal = range <= 1.15 IB; trend = one-sided extension >= 1.5 IB, other side <= 0.15 IB, close in extreme 25%; normal variation = one-sided smaller extension; neutral = both sides extended > 0.15 IB (neutral-extreme: close in extreme 20%); non-trend = range < 0.5 x mean10 and <= 1.15 IB; double distribution = two TPO peaks >= 20 rows apart with valley <= 30% of peak. "with" = trend/variation up and long, or down and short |
| dl_ | above_va_with, inside_va, against_va, poc_side_with, va_narrow, va_wide | PUBLIC TPO value area (70% of TPOs, Dalton two-row expansion from POC) and POC of the prior RTH day; price beyond VA in trade direction / inside / beyond on the other side / on trade side of POC; VA < 30% / > 60% of day range |
| dl_ | poor_high_*, poor_low_*, poor_extreme_ahead/behind, excess_high/low, excess_support_with | PUBLIC-style: poor high (low) = >= 2 TPOs at the extreme row and no single-print tail >= 6 pts; unrev = price has not traded beyond it since the day ended; ahead/behind relative to trade direction (poor extreme ahead = unrevisited poor high above a long); excess = single-print tail >= 6 rows (6 pts) at the extreme; excess_support_with = excess tail on the trade's side below(long)/above(short) price |
| dl_ | sp_ahead_30/60/120, sp_behind_*, sp_ahead_any | PUBLIC single prints: interior runs of single-TPO rows >= 6 rows (not touching profile extremes) in the last 5 completed days, not yet entered by price since; nearest within X pts in / against trade direction |
| dl_ | open_outside_va, open_outside_va_with, r80_active_with/against, r80_fresh60, r80_done | PUBLIC 80% rule (APPROX period definition): RTH open outside prior TPO value area, then two consecutive completed 30-min bracket closes inside VA; target = opposite VA edge; active = not yet reached; with = target direction equals trade; fresh60 = triggered within last 60 min; done = target reached |
| dl_ | ib_ext_up/dn/with/against, dev_trend_with, dev_neutral, dev_normal, in_ib, ib_narrow | developing day (after 60 min): extension beyond IB > 0.15 IB; developing trend = one-sided extension >= 1.0 IB; IB < 35% of mean10 range |
| dl_ | poc_migr_with, poc_same, dev_poc_side_with | developing TPO POC now vs one 30-min bracket earlier; price on trade side of developing POC |
| fa_ (Fisher ACD) | a_{std,fast,slow}_now_with/against, hit_with, fresh30, c_*_with, inor | APPROX: OR = first 30 (fast 15, slow 60) min, A = 0.10 (0.07, 0.15) x mean range of previous 10 days; A-up = OR high + A, A-down = OR low - A; now = price beyond A level; hit = A level touched; fresh30 = first touch within 30 min; C (with) = after the opposite A was hit, a close back through the whole OR in trade direction; inor = inside OR |
| fa_ | above_pr_with, inside_pr, pr_narrow | PUBLIC Fisher/Floor pivot range of prior day: central pivot range between (H+L)/2 and 2*(H+L+C)/3-(H+L)/2; price above it for long (below for short); inside; width < 50% of previous-10-day mean width |
| fa_ | nl15/30/60_{std,fast,slow}_with | APPROX number line: daily ACD score (A first hit +-2, C reversal +-2) summed over 15/30/60 days; with = signed sum >= 0.3 x window (= +-9 at 30 days, Fisher's threshold) |
| wl_ (Williams) | volbo_std/fast/slow beyond, hit | PUBLIC volatility breakout: RTH open +/- k x prior-day range, k = 0.5 (0.3, 0.8); price beyond now / touched since open |
| wl_ | oops_with/against, gap_with/against | PUBLIC oops: opened below prior low and traded back up through it (long) / opened above prior high and back down through it; with = price still on the re-entry side and trade in that direction. gap_with = RTH open beyond prior day's high (low) in trade direction |
| wl_ | smash_with/against | prior day closed beyond the previous day's high/low (Williams smash-style continuation) in / against trade direction |
| wl_ | tdom_first3, tdom_4_9, tdom_10_16, tdom_last3, tdom_seasonal_with | trading day of month (RTH calendar of the signal's Globex day); seasonal_with = mean RTH close-to-close return on the same trading-day-of-month over earlier days (>= 10 obs, expanding, causal) has the trade's sign |

## Block 3 sub-block C: execution-desk levels, seasonality, volume curve (C1, cf5_exec.py) and statistical order-flow measures (C2, cf5_flow.py)
Files cols_cf5/C1_exec_named.parquet (1-min bars, to 2026-10-16 21:00Z; later signals -1) and cols_cf5/C2_flow_named.parquet (per-second NQ tape/book table of W-CF2, cf2_sec; windows end at the signal second, rows < sig_ts only). Same keys/naming. ATR below = ATR14 of 15-min bars (completed). Globex day = ET+6h date, anchors: gx = Globex open 18:00 ET, ss = start of the signal's D7 session (asia 18:00, london 02:00, pre 08:30, nyam 09:30, nypm 12:00, close 15:00 ET).
| prefix | condition | definition |
|---|---|---|
| ex_{gx,ss}_ | vwap_side, twap_side, twap_vwap_with | PUBLIC: volume-weighted average of typical price (H+L+C)/3 per 1-min bar, and time-weighted mean of 1-min closes, from the anchor to the last completed bar; price on trade side of each; TWAP on trade side of VWAP (APPROX reading: time-average above volume-average means volume traded lower) |
| ex_{gx,ss}_ | vwap_ext1/2_with, vwap_ext1_against | distance of price from VWAP in ATR in trade direction > 1 / > 2; < -1 |
| ex_{gx,ss}_ | arrival_with1, arrival_against1 | arrival-price deviation: (price - anchor open price) x side / ATR > 1 / < -1 (execution desk: how far the move from an algorithm that arrived at the anchor has run) |
| ex_mv_ | large2, with, with_large, vwap_side, pullback_hold, pullback_deep | last large move: window 120 min, direction = sign of net close change, anchor = bar of the extreme that started it (lowest low if up); VWAP anchored there; large = move > 2 ATR; with = move direction equals trade; pullback_hold = large move with the trade and price still on the trade side of the move VWAP; deep = large move with the trade but price through the move VWAP |
| ex_volcurve_ | ahead, behind, ahead_move_with, sess_ahead, sess_behind | PUBLIC: cumulative Globex-day volume at the clock offset vs mean of the previous 20 Globex days at the same offset: > 1.2 ahead, < 0.8 behind; sess_ = volume since the session start vs same; ahead_move_with = ahead and 30-min move with trade |
| ex_range30_ | hi, lo | last-30-min close range vs previous-20-day mean at same clock: > 1.4 / < 0.7 |
| ex_seas30_ / ex_seas120_ | with, strong_with, strong_against | intraday seasonality curve: mean forward 30 (120) min change at this clock offset over the previous 60 Globex days (complete days only, causal) has the trade's sign (with), or |t| > 1 in trade's favour / against |
| fl_ofi{1,5,15,60,300}s_ | with, strong, z1, z2 | signed volume (aggressor buy minus sell, tape) over the window ending at the signal second: with = net with trade; strong = net/total > 0.3; z = net / std of non-overlapping same-length windows over the previous 30 min > 1 / 2 |
| fl_bimb{1,5,10}{1,5,15,60,300}s_ | with, strong | book imbalance (bid minus ask)/(sum) for top-1 / top-5 / top-10 depth, averaged over the window of end-of-second states (mbp-10 100 ms grid): with = favours trade; strong = > 0.2 (windows <= 15 s) / > 0.1 (longer) |
| fl_mic{W}s_with | | mean microprice offset (size-weighted mid minus mid) over the window with trade |
| fl_kyle_ | hi, lo, sign_with | Kyle lambda: slope of 1-s price change on 1-s signed volume over the last 300 s, |lambda| vs median |lambda| of the previous hour (5-min windows): hi > 1.5x, lo < 0.67x; sign_with = lambda positive in the trade's direction (APPROX: per-second regression, no intercept control) |
| fl_size{60,300}_ | up, down | trade-size distribution shift: mean print size in the window vs previous 30 min before it: > 1.3x / < 0.77x |
| fl_bigshare, fl_bignet{60,300}_ | up, with, strong | share of volume in prints >= 10 contracts vs baseline > 1.5x; net (buy-sell) volume of prints >= 25 contracts with trade / >= 50 contracts net |
| fl_qtr{60,300}_ | hi, lo | APPROX quote-to-trade ratio: book-update churn (depth pulled + added at non-best levels per the cf2_sec columns) per contract traded vs previous 30 min, > 1.5x / < 0.67x (true quote count not stored in cf2_sec) |
Not built (and why): index dispersion and realized-vs-implied vol / term-structure slope need the megacap composite (W-CF2 Block 5) and CBOE daily series (W-CF2 category J) - to be added in sub-block D if their feeds land; ADX/DI, parabolic, plain %R, ATR left to W-CF1 category M/E.

## Block 3 sub-block B2: opening-range systems re-anchored on the D7 session (cf5_ssn.py; file B2_sessanch_named.parquet; prefix n_ss_)
Because 70% of signals are outside RTH, Crabel ORB / stretch / Williams volatility breakout / Fisher ACD / oops are re-run with the opening of the signal's D7 session (asia 18:00, london 02:00, pre 08:30, nyam 09:30, nypm 12:00, close 15:00 ET) as "the open" and the previous Globex day's same session as "the prior day". avg10 = mean range of the previous 10 same-session ranges. Conditions: ss_nr4 / nr7 / inside (previous same session narrowest of 4 / 7 / inside the one before); ss_range_used_lt50 / gt100 / gt150 (session range so far / avg10); ss_orb{5,15,30}_beyond / fresh15 / failed / against_beyond (as cb_orb); ss_stretch_beyond / hit (stretch = mean of min(open-low, high-open) over previous 10 same sessions); ss_volbo_{std,fast,slow}_beyond / hit (open +- k x previous session range, k = 0.5 / 0.3 / 0.8); ss_a_{std,fast,slow}_now_with / now_against / hit_with / fresh30, ss_c_*_with, ss_inor_* (ACD: OR = first 15 / 5 / 30 min of the session, A = 0.10 / 0.07 / 0.15 x avg10 session range; APPROX, same C rule as fa_c); ss_oops_with / against, ss_gap_with / against (gap vs previous same session's high/low). All APPROX (no published session version exists).

## Block 3 sub-block D: outside series (cf5_stat.py; file D_statext_named.parquet; prefix n_sd_)
| condition | definition |
|---|---|
| sd_rviv{30,60,240}_gt1 / lt50 / gt15 | realized vol of the last 30/60/240 one-minute returns (annualized sqrt(252*390)) divided by VIX/100 (prior Cboe close; APPROX: S&P implied for NQ, no VXN on the box): > 1, < 0.5, > 1.5 |
| sd_vix_contango / backward / vix9d_inverted | PUBLIC term structure slope: VIX3M/VIX-1 > 0.05 / < 0; VIX9D/VIX-1 < 0 |
| sd_vix_fall1d_with / fall5d_with / vix_high / vix_low / vvix_vix_hi | VIX 1-day / 5-day change in the trade's favour (falling for longs, rising for shorts); VIX in top / bottom 20% of its 250-day range; VVIX/VIX above its 80th percentile of 250 days |
| sd_disp{5,15,60}_hi / lo, sd_breadth{5,15,60}_ge5 / le2, sd_mean{5,15,60}_with | index dispersion: cross-sectional std of the last 5/15/60-min returns of AAPL, AMZN, GOOGL, META, MSFT, NVDA, TSLA vs 1.5x / 0.6x of its running median over earlier signals; breadth = names moving with the trade >= 5 / <= 2 of 7; equal-weight mean return with trade (2024-10 onward, earlier -1) |

# ADDENDUM 6 BLOCKS (W-CF5): 7 time-of-day liquidity events, 8 opening prices and gaps
Universe: signals_all.parquet (191,520 signals, taken + skipped), keyed sig_id. Files: cols_cf5/B7_tod.parquet (prefix n7_), cols_cf5/B8_open.parquet (prefix n8_). int8: 1 yes, 0 no, -1 unknown. Code: code/th_confl_cf5/cf5_blk78.py. All APPROX labels = my coding of the user's wording, no published rule exists for these. Causality: completed 1-min bars only (bar start + 60 <= sig_ts); price "p" = close of the last completed 1-min bar; an event/opening price is the open of that event's 1-min bar and the move-based conditions are unknown (-1) while that bar is still incomplete; checked by recomputing on history truncated at the signal second (6 random signals, 3,606 values, 0 mismatches; the cash-open-gap group n8_cg_ excluded from that check only because the day-table builder drops a partial day, its inputs are the open and prior close). ATR60 = ATR14 of completed 60-min bars, ATRd = ATR14 of completed RTH daily bars. Absolute prices are never used (only differences), so the offset table is not needed. DST: the event time of day is wall-clock ET arithmetic; on the two DST-change days a year an event earlier in the day than the switch is off by 1 h.

## Block 7 (n7_), APPROX
Events (ET): t0200, t0300, t0830, t0930, t1000, t1030, t1100, t1130, t1300, t1500, t1550, t1600, t1615, t1700, t1800 (daily); t1400fomc = 14:00 on FOMC decision days only (0 elsewhere; FOMC dates: public 2023-04..2024-09 list + events.csv from 2024-10). Windows (start, duration): w0950 (09:50, 20 min), w1050 (10:50, 20), w1450 (14:50, 20), w1000_1100 (10:00, 60), w1400_1500 (14:00, 60), macro_xx50 (every hour xx:50-xx:10), tophour (xx:00, 5 min), halfhour (xx:30, 5 min).
For a point event E: pre15 = signal 1-15 minutes before E; post5 = 0-5 min after; post15 = 5-15 after; post30 = 15-30 after. For a window: pre15; in = inside the window; post15 / post30 = 0-15 / 15-30 min after the window ended.
Suffixes: (none) = signal is in that phase; _with / _against = and the move made in the window with / against the trade (pre15: trailing 15-min move; post5/post15/post30 of a point event: move since the event open; in: move since window start; post of a window: whole-window move open to close); _big_with / _big_against = same with |move| > 0.75 ATR60.
n7_grp_{rel,eur,nyo,fix,late}_<phase><suffix> = union (OR) over: rel = 08:30, 10:00, 14:00 FOMC; eur = 02:00, 03:00; nyo = 09:30, 10:30; fix = 11:00, 11:30; late = 15:00, 15:50, 16:00, 16:15.

## Block 8 (n8_), APPROX
Opening prices: mid (00:00 ET), o0830, o0930, o1800 (Globex reopen), week (first bar after a >= 36 h break), month, quarter (first bar of the ET calendar month / quarter). Latest occurrence <= signal (age limits 2 d for time-of-day opens, 10 d week, 40 d month, 100 d quarter else -1). For each open O: _side (price on trade side), _ext_with1/2 and _ext_against1/2 (distance x side beyond 1 / 2 ATR; ATR60 for the intraday opens, ATRd for week / month / quarter), _near (< 0.25 ATR), _cross_with30 / _cross_against30 (crossed O in / against trade direction within the last 30 bars), _retest_with (was >= 1 ATR beyond O in trade direction within 120 bars and is now 0-0.5 ATR from it). intraday_opens_ge3of4 / all4 and all_opens_ge5 / ge7 = how many of the opens are on the trade's side.
Gaps: a gap = a break > 50 min between 1-min bars (day gap) or >= 36 h (week gap); zone = [min, max](previous close, reopen), kept if size >= 0.2 ATR60; filled when price later trades back to the previous close. gapD_* uses the last 5 day gaps, gapW_* the last 3 week gaps (levels): _cur_unfilled / _cur_up_with (latest gap went up and trade is long, or down and short) / _cur_big (> ATR), _unf_ahead_1atr / 3atr and _unf_behind_1atr / 3atr (nearest unfilled gap edge in / against the trade direction within 1 or 3 ATR60), _inside_unf (price inside an unfilled gap), _unf_ahead_ge1 / ge2 (count of unfilled gaps ahead), _mid_side_with (price beyond the nearest unfilled gap's midpoint in trade direction).
Cash-open gap: ig_* = implied gap (price vs the last completed RTH close: with / against by > 1 or 0.5 ATRd, inside prior RTH range); cg_* (only for signals 09:30-18:00 ET, else -1) = actual 09:30 open vs prior RTH close: gap_with / gap_against, inside_range / outside_range of the prior RTH day, large (> 0.5 ATRd) / small (< 0.15), filled (price traded back to the prior close since 09:30), unfilled_with / unfilled_against (unfilled gap >= 0.15 ATRd in / against trade direction), filled_with_trade_dir (gap against the trade, now filled).
Session handoff: macro sessions Asia 18:00-02:00, London 02:00-09:30, NY 09:30-16:00 ET. hoLA (London vs Asia), hoNL (NY vs London), hoAN (Asia vs the previous NY), valid >= 30 min into the second session and within the same Globex day: _ext (second session's move so far has the same sign as the first session's whole move), _rev (opposite), _cur_with / _prev_with (second / first move with the trade), _ext_cur_with, _rev_cur_with, _prev_big (first move > 2 ATR60).
Overnight inventory: on_inv_with = (overnight VWAP of 18:00 to now, or to 09:30 once past it, minus the prior settle = last RTH close) x side > 0; _big_with / _big_against beyond 0.5 ATRd; px_vs_onvwap_with, px_onvwap_ext_with1 / ext_against1 (price vs the overnight VWAP by > 1 ATR60). Unknown 16:00-18:00 ET.

## Block 9 (n9_, file B9_structure.parquet, code cf5_blk9.py), APPROX unless noted
Week = Globex week (first bar after a break >= 36 h). Day of week from the Globex label day (Sunday evening = Monday). All ranges from completed 1-min bars (sparse-table range max/min). Causality check by truncated recompute: 6 random signals, 414 values, 0 mismatches.
- Week extremes: wk_opp_ext_in / wk_my_ext_in = the week's high / low (the one opposite / on the side of the trade: for a long my = low) was set on an EARLIER day of this week (known from the bars); _odds50 = walk-forward probability >= 0.5 that this extreme is already in on this weekday (share of earlier completed weeks, >= 20 weeks, Laplace-smoothed, whose high / low fell on an earlier weekday than today); wk_opp_in_but_odds_low, wk_opp_notin_odds_high = actual vs odds disagree. Descriptive history: the week's high forms on Mon/Tue/Wed/Thu/Fri 19/14/17/15/34 %, the low 32/15/13/13/27 % (285 weeks).
- wk_pos_top20 / bottom20 / mid: position in the week's range so far, oriented so top = in the trade's direction; wk_new_ext_with (price at a new week extreme in trade direction vs bars excluding the last 5); wk_used_lt50 / gt100 / gt150 (week range so far / mean of the previous 10 weeks' full range).
- Monday range: mon_inside, mon_ext_with0 / 1 / 2 and mon_ext_against0 / 1 / 2 (price beyond Monday's high/low by 0, 1x, 2x Monday's range, in / against trade direction); valid Tue-Fri. Monday = first 23 h of the Globex week.
- Month: mo_pos_top20 / bottom20, mo_used_gt100 / lt50 (month range so far / mean of the previous 6 months).
- Session extensions: psess_* (immediately preceding D7 session's range), ysame_* (same D7 session on the previous day), fhour_* (first hour of the current D7 session, valid after 62 min), asia_* (Asia 18:00-02:00 range, valid after it ended): _inside, _break_with / _break_against (price beyond the high/low in / against the trade direction), _ext05_with / _ext1_with (beyond by 0.5x / 1x of that range in trade direction).
- 90-minute quarters: six-hour sessions starting 20:00, 02:00, 08:00, 14:00 ET, quarters Q1..Q4 of 90 min. q_in1..q_in4 (current quarter). q1_consol (Q1 range < 0.8x mean Q1 range of the previous 14 days at the same clock, >= 5 valid), q1_range_gt_avg; q2_false_move (Q2 sweeps exactly one side of the Q1 range and closes back inside), q2_false_dir_with / against (the sweep direction with / against the trade); q3_complete_with, q3_claim_trend_opposite_sweep (Q3 net move opposite the Q2 sweep), q3_claim_trend_with; q_cur_move_with (net move of the current quarter so far); q3_live_after_false_with / against / q3_live_trend_with (inside Q3); q4_live_fade_of_q3, q4_live_fade_with, q4_live_cont_with (inside Q4: current move opposite / with Q3's). The claim as a statement about the market is tested directly in DS3_CONFLUENCE_B9_QUARTERS_CF5.md (3,603 sessions: Q1 is NOT the narrowest quarter more than chance (22 % vs 25 %); after a false move Q3 goes against the sweep 49.9 % (coin); Q4 net move opposite Q3 47.7 %, i.e. continuation is slightly MORE likely than the fade, z -2.7).
- Accumulation / manipulation / distribution tag from the Q1 range of the six-hour session (APPROX): amd_acc (in Q1, or no side of the Q1 range swept and price inside it), amd_manip_dir_with / against (a side of the Q1 range was swept after Q1 and price has not yet left through the opposite side: with = the sweep was against the trade's direction, e.g. long after a sweep of the Q1 low), amd_dist_with / against (price beyond the Q1 range in / against the trade direction, with or without a prior sweep), amd_sweep_then_dist_with (swept the opposite side first, then left through the trade side).

## Block 16 (n16_, file B16_calendar.parquet, code cf5_blk16.py), unsigned flags by the signal's Globex label day
Trading days = weekday label days with >= 600 one-minute bars; half_day = 600..1299 bars (normal 1380). first_td_month / first3 / last_td_month / last3 / last5; quarter_end_day / week, first_td_quarter, collar_reset_day (APPROX: JPM hedged-equity collar resets on the last trading day of Mar/Jun/Sep/Dec) and collar_reset_pm1; year_end_week, january_first_week, tax_loss_window (last 7 trading days of December + first 3 of January); opex_day (third Friday of the month), quad_witch (third Friday of Mar/Jun/Sep/Dec), opex_week, quad_week, day_after_opex, day_after_quad; vix_expiry_day (Wednesday 30 days before the third Friday of the next month, previous trading day if closed), vix_expiry_week, day_after_vix_expiry; roll_day (Thursday 8 days before the quarterly expiry), roll_week, roll_day_pm1, expiry_week_quarterly; russell_recon_day / week (last Friday of June), ndx_recon_day / week (third Friday of December, APPROX for the effective date), ndx_special_rebal_2023_07_24, sp_rebal_day (quad witching); pre_holiday / post_holiday (market closed on a weekday next to it), long_weekend_pre, half_day, day_after_half, thanksgiving_week, christmas_week (Dec 21+); fomc_day / day_before / day_after / fomc_week / week_after_fomc / week_before_fomc (decision dates: public 2023-04..2024-09 list + events.csv); estimated_tax_week (week containing Jan 15, Apr 15, Jun 15, Sep 15), april_tax_week; flow_heavy_day (union of opex, quad witch, month end, Russell, NDX recon, roll day). Schedules are public rules coded by me; no feed was used.

## Block 13 (n13_, file B13_micro.parquet, code cf5_blk13.py), APPROX
From the per-second table cf2_sec (rows < sig_ts) and 1-min bars. Baselines exclude the window and use earlier data only.
- Arrival intensity: arr{10,60,300}_hi / lo = prints per second over the last 10 / 60 / 300 s vs the 30 min before the window (> 2.0 / 1.5 / 1.3x, < 0.5 / 0.67 / 0.77x); arr_accel / arr_decel = last 30 s vs the 30 s before it (> 1.5x / < 0.67x); arr60_vs_300_hi; arrival_vs_clock_hi / lo = last 60 s rate vs the mean of the previous 20 Globex days in the same 5-min clock bucket (> 1.5x / < 0.67x).
- Spread and depth regime vs the clock: spread_wide / tight = mean top-of-book spread of the last 10 s vs the previous 20 days' median in the same 5-min bucket (> 1.25x / < 0.9x); depth_thin / thick = top-5-level depth (bid + ask) vs same (< 0.7x / > 1.3x).
- Volatility of volatility: vov{60,240}_hi / lo = coefficient of variation of |1-min return| over the last 60 / 240 bars vs its own trailing 5-day mean (> 1.25x / < 0.8x).
- Realized skewness and kurtosis of 1-min returns over 15 / 60 min: skew{15,60}_with, skew_strong_with / against (|skew| > 0.5 in / against the trade direction), kurt{15,60}_hi (> 6).
- Jumps (bipower): jshare{15,60}_hi / lo = max(0, 1 - BV/RV) > 0.3 / < 0.05 (BV = pi/2 x sum |r||r-1|); jump15_any / with / against, jump60_any = a 1-min return larger than 4 sigma (sigma^2 = BV60 per bar) within the last 15 / 60 bars, its sign with / against the trade.
- Toxicity: vpin_hi / lo = VPIN (500-contract volume buckets, 50-bucket mean of |buy - sell| / bucket size, buy / sell by aggressor) vs 1.3x / 0.8x the median of the previous 20 days' day-median; vpin_dir_with / against = signed net imbalance over the same 50 buckets with / against the trade (> +-0.02); vpin_hi_dir_with / against.
- Book resilience after sweeps: sweep = one second with >= 100 contracts on one aggressor side and > 4x the other; sweep120_any / with / against = a sweep ended between 6 and 120 s before the signal, direction with / against the trade; sweep_resilient / thin = consumed-side top-5 depth 5 s after the sweep vs just before (>= 0.9 / <= 0.5); sweep_thin_with, sweep_resilient_against.
- Time since the last large trade: lt25 / lt50 _since_lt10 / lt60 / gt300 (last second containing a print of >= 25 / >= 50 contracts), lt25_last_with60 / against60 (net sign of the large prints in that second with / against the trade, if within 60 s).
- Odd-lot share (proxy): avgprint{60,300}_le115 / ge16 = average print size over the window <= 1.15 contracts (mostly single-lot prints) / >= 1.6 (cf2_sec has no size histogram; true odd-lot share not available).
- Not built: order-book resilience measured on cf2_mbo (L3), only months on the box; quote counts (not stored).

## 1-MINUTE GRID VERSIONS FOR T-ALPHA (W-AL1), code/th_confl_cf5/cf5_grid.py and cf5_grid_a.py
Every block above runs unchanged on a 1-minute grid by overriding the signal table (cf5_core.SIG_OVERRIDE): rows = every NQ 1-minute bar start ts (epoch s, same as the panel ts_event) from 2023-02-01 to 2026-10-30 (1.34 M rows), evaluated at the FIRST second of the minute (only bars up to ts-60 used; same code and causality as the signal builds; checked: for 2,438 June-2025 signals the grid row at floor(sig_ts/60) equals the signal-build row in all 780 columns of Blocks 7, 8, 9, 0 mismatches). Orientation side = +1: '_with' = bullish, '_against' = bearish; '_S' files (cf5_grid.py <block> --side=-1) give the mirrored set if wanted. Files /mnt/l2/l2vast/_confl/cols_cf5/grid/<block>_<yyyymm>.parquet, first column ts, then int8 conditions (1/0/-1 unknown) and float32 raw values (n_v_*, graded):
- calendar / clock first: B16_<ym> (calendar, 48 cols), B7_<ym> (time-of-day events, 580), B9_<ym> (week / session structure, 69), B8_<ym> (opens, gaps, handoffs, 131), B13_<ym> (microstructure from cf2_sec, 61).
- A_<tf>_<ym> for tf in 1m 3m 5m 15m 60m 1d (named systems, 766 columns per tf incl. raw values), written by cf5_grid_a.py.
- then B2_, B_, C1_, D_, C2_ (session-anchored, Dalton/Crabel/ACD/Williams, execution levels, RV/VIX/dispersion, order flow), slower builds, chain log <tmp>
Entry points: grid_frame(side) in cf5_grid.py (the grid), run(block, ym) (one block-month), cf5_specs.specs(H) + cf5_cond.cond_block2 (indicator specs and the condition template), cf5_ind.py (plain-OHLC kernels). Graded values: the indicator value series themselves are the n_v_* columns of A_* (one per indicator x timeframe). Calendar and clock blocks have no graded value, they are flags.


# ===== Block 6 counting (W-CF6) : merged verbatim from CONFLUENCE_DEFS_CF6.md =====
# CONFLUENCE_DEFS_CF6.md (W-CF6, Block 6 candle counting). Code: outputs/code/th_confl_cf6. Columns: /mnt/l2/l2vast/_confl/cols_cf6/ keyed by sig_id = <book>_<signal ts>.
Status 2026-11-15 ~00:10Z: section 'ICT count (ICT_COUNT_V0)' final and pre-registered (below). Section 'Counting' (Brooks, second entry, legs, bar number, DeMark, streaks, time counts, waves, horizontal, own events) follows when the columns land.

## ICT count (ICT_COUNT_V0)  -- PRE-REGISTERED, key counts and rules R1-R4 are not tuned
Source: public thread supplied by the user, Addendum 4. Status of every piece: PUBLISHED RULE as stated in the thread, coded mechanically = APPROXIMATION of a discretionary method (the thread's "time distortion" clause is ignored as ordered).
Key counts (fixed): 7-8, 12-13, 20-21, 33-34, 40-42. Neighbours (two either side, not themselves key): 5,6,9,10 | 10,11,14,15 | 18,19,22,23 | 31,32,35,36 | 38,39,43,44.
Bars: NQ 1-minute store (uwbooks/min1_NQ.npz, 2023-02-01..2026-11-13; same roll fix as ta_lib) resampled: 3, 5, 15, 60 (epoch-aligned), 240 (from 18:00 ET, 6 bars per Globex day), daily (Globex day, 18:00 ET roll), weekly (Monday of the Globex day). Daily/weekly use the same 43+ months (no longer NQ history exists on the box; ES/RTY/YM not used here). Bar index i is COMPLETE when its end <= the query second.
Orientation: the up-count (from a LOW, counts up-closed candles, c > o) is coded once; the down-count (from a HIGH, down-closed candles) is the same code on the flipped series (h' = -l, l' = -h, o' = -o, c' = -c). Reported pooled over both and separately.
R1 anchor (three definitions, all causal):
 (a) bar of the lowest low (highest high) of the last W bars of that timeframe, W = 20 / 40 / 60 (earliest bar on ties). Consequence: the count cannot exceed ~W counted candles, so 40-42 is reachable only with W = 60 (and for b, c).
 (b) most recent confirmed swing extreme: m-bar fractal (low lower than m bars each side, <= on the right), m = 3 / 5 / 10, KNOWN ONLY m bars after the pivot bar (confirmation bar = pivot + m). Anchor = most recent confirmed pivot low (high); a new low (high) beyond the anchor moves the anchor to that bar.
 (c) session / week / month extreme: running lowest low (highest high) since the Globex-day start (18:00 ET) / Monday-of-week / calendar month of the Globex day (daily bars: week and month; weekly bars: month). New extreme beyond the anchor -> anchor moves to that bar. First bar of the group is the anchor at the group start.
R1 reset: in all three, a new extreme beyond the anchor resets the count to that bar (count 0 at the anchor bar).
R2 counted candle (base): from a low, only up-closed candles (c > o); from a high only down-closed. Variant noR2 = every non-inside candle counted.
R3 (base): inside candle (high <= prior high AND low >= prior low) is never counted. Variant noR3 = up-closed candles counted even if inside. Variant 'plain' = every candle counted (no R2, no R3).
R4 consolidation skipping (APPROXIMATION, most subjective): a causal box is detected at bar j when the last N bars (j-N+1..j) span a high-low range < k x ATR14(j); N = 8 / 12 / 20, k = 1 / 1.5. The box stays active until a bar CLOSES outside it (up-break: close > box high, down-break: close < box low; a bar that only wicks out stays inside; give up after 400 bars). On an up-break at bar t (count from a low) the anchor becomes max(anchor, t-1) (the last box bar), so box candles are not counted; mirrored for down-breaks with counts from a high. Applied to anchors a40, b5, c-day (c-week for daily). Also scored WITHOUT R4 (noR4), the default.
Count of bar i = number of counted candles with index in (anchor, i]. A 'counted candle at count k' is a bar that is counted and has count k; Step A events are these bars.
Step A outcomes (measure only, from the close of the event bar i, ATR = Wilder ATR14 of that timeframe at i):
 o0: retracement >= 0.5 ATR: close[i] - min(low[i+1..i+5]) >= 0.5 ATR (mirrored for down counts). o1: same with 1 ATR.
 o2/o3/o4: the leg extreme (max high over anchor..i) is NOT exceeded by any bar up to the 5th / 10th / 20th next counted candle ("swing extreme holds for the next 5/10/20 counted candles"). Needs that many later counted candles to exist.
 o5: turtle soup: event bar i is the first bar whose high exceeds the last confirmed 5-bar-fractal swing high (known at i) AND some close in i..i+3 is back below that swing. Rate among breakout event bars. o6 = same events but divided by ALL event bars at the count (unconditional).
Controls: key group vs the 4 neighbours (pooled rates); vs smooth trend (weighted least squares in rate space, features 1, ln k, k/60, (k/60)^2, weights N, fitted on ALL non-key counts 1..60 of that curve, prediction summed at the key counts); vs RANDOM anchors = the real anchor series circularly shifted in time by 1/3 and 2/3 of the sample (keeps the anchor-distance and reset statistics, destroys the link between anchor and price). CI: 400-draw month-block bootstrap. Windows: ALL (2023-04..2026-10), L1M, L3M, L6M, HOLD, PRE, X', GAP (cap 2026-10-31). Sessions (D7): s0 Asia 18:00-02:00, s1 London 02:00-08:30, s3 NY AM 09:30-12:00, s4 NY PM 12:00-15:00 (pre / close have no D7 book); session of the event bar's start.
Worked example 1 (60-min, anchor a40, base rules, count from LOW): anchor = 60-min bar starting 2026-10-08 13:00 ET, low 27,059.75 (lowest low of the last 40 bars). Counted (up-closed, non-inside) candles after it: 14:00 (1), 16:00 (2), 18:00 (3), 20:00 (4), 21:00 (5), 22:00 (6), 23:00 (7), 2026-10-09 00:00 (8; close 27,390.75). 15:00 and 19:00 are down-closed bars and are NOT counted (R2). At 00:00 the count sits at key count 8 (key group 7-8). Outcome o1: the next 5 bars' low was 27,385.75, i.e. a 5-pt dip against ATR 92.6: no 1-ATR retracement.
Worked example 2 (5-min, anchor b5, base rules): on 2026-10-06 ET the 04:40 bar (low 27,628.75) becomes the most recent CONFIRMED 5-bar swing low only at 05:05 (five bars later); until then the count was measured from an earlier pivot (count 11 at 05:00), at 05:05 it re-bases to 04:40 and reads 2. Counted candles then: 05:15 (3), 05:30 (4), 05:45 (5), 06:05 (6), 06:10 (7), 06:15 (8, close 27,700.75): 7-8 key count; inside/down candles skipped. Outcome o1: next 5 bars' low 27,698.75, no retracement. (Illustrates that pivot-anchored counts change when the pivot is confirmed, never earlier.)

## Counting (Block 6, Addendum 3) - exact coding, 2026-11-15
Common: bars = NQ time bars 1/3/5/15 (and 60 for DeMark HTF) from the 1-min store; a bar is used only if its end <= the signal second (ix = last complete bar); ATR = Wilder ATR14 of that timeframe; 'with' = the trade's direction (side), 'against' = opposite; column name c_N_<school>_<tf>_<cond> (int8 yes=1/no=0/-1 unknown), raw value v_N_*. Counters reset at the first bar of each Globex day (18:00 ET) for Brooks/streak counts. Code: code/th_confl_cf6/cf6_kern.py (numba), cf6_cols.py, cf6_cols2.py, cf6_build.py. 1,101 condition columns, 19,798 taken signals (skipped signals to follow when W-CF1's table has them). Alt bars (2000-tick, 8-pt range, true HA) NOT yet: HA colour runs use Heikin-Ashi computed from the time bars.
Status key: PUB = published rule coded as stated; APX = approximation.
1. BROOKS bar counting (APX of a discretionary method; two codings kept). Up leg (H count), mirrored (flipped series) for L. Coding A: pullback bar = high <= prior high; H bar = bar with high > prior high whose prior bar was a pullback bar; counts H1,H2,... within the current pullback; a bar making a new leg high ends the pullback and resets the count to 0 (reset event). Coding B: pullback bar = down-close bar (close < open); H bar = high > prior high after a down-close bar; reset when the close makes a new leg closing high. Cols: bk{A,B}_{tf}_with_n{1..4}_w{0,2,5} (event n, 4 = '>=4', within N bars), against_n{1,2,3}_w{N}, with_cur_{eq1,ge2}/against_cur_{ge2,ge3} (running count now), with/against_reset_w2, with_n2_at20ema_w2 (H2/L2 bar low/high within 0.5 ATR of EMA20 with close on the trade side) and with_any_at20ema_w2. Level version (count at a level) NOT yet built. Disagreement A vs B is printed in the page (Jaccard of yes sets).
2. SECOND ENTRY (APX). From coding A on the same bars: se_{tf}_first_entry_w5 / second_entry_w5 (last with-direction H1/H2 within 5 bars), second_h1failed (after the H1 bar, price traded below the H1 bar's low before the H2 bar), second_h1extreme_taken (H2 high above H1 high), second_gap_le4 / ge5 (bars between H1 and H2). D7-event version: se_d7_after_loser{30,60,120} (same-side signal of any book CLOSED as a loser within the last N minutes, exit_ts <= signal second), after_win{30,60}, after_loser_book60, nprior_sameside60_ge{1,2} (signals only, no outcome).
3. LEGS AND PUSHES (APX; mechanical). Big zig-zag 1.5 ATR (pivot confirmed when the reverse move >= 1.5 ATR of the confirming bar) defines the active leg from the last confirmed pivot; small zig-zag 0.6 ATR gives pushes: a push = a successive small swing extreme in the leg direction (higher highs in an up leg) plus the running extreme; wedge = pushes >= 3; with momentum divergence = RSI14 at the third push below RSI at the second (up leg). Cols lg_{tf}: active_leg_with/against, push1/push2/push3plus_with, wedge3_div_with / nodiv_with / div_against, pbleg{1,2,3plus}_against_active (active leg against the trade = a pullback in progress; its small legs counted), pb2_complete (>=2 pullback legs and the reversal confirmed), mm_same_ge0.9 and band 0.9-1.1 (active leg length / previous same-direction leg), mm_prev_ge0.9_against_trade, climax_late (largest-range bar in the last 20 pct of the leg, >= 2x median range, leg >= 6 bars), trendbar_run_with/against_ge{3,5,8} (consecutive bars with body >= 50 pct of range closing in direction). Timeframes 3/5/15.
4. BAR NUMBER (PUB arithmetic). bn_rth = 5-min bar number since 09:30 ET of the last complete bar (1..81, only 09:30-16:15), columns bn_rth_1..81, windows first6, first12, 7-12, 13-16, 17-21 (around 18-20), 22-29, midday 30-57, 58-69, last 12 (70-81); bn_sess = 5-min bar number since the D7 session start (Asia 18:00, London 02:00, pre 08:30, NY AM 09:30, NY PM 12:00, close 15:00), first6/first12/mid/last12; bars since the Globex-day high / low (bs_high_le{0,3}/ge{12,36}, bs_low_*, signed bs_ext_with/against_*); RTH high / low made in the first 6 / 12 RTH bars (valid after bar 12 only) incl. signed with/against versions. Shift control in shift_control.csv.
5. DEMARK (W-CF5's library cf5_ind.td_seq / td_combo; PUB for setup 9 + perfection, countdown, price flip, TDST; combo = W-CF5's coding, APX). dm_{3,5,15,60}: setup_support_ge{4,7,8,9} / setup_against_ge{...} (support = buy setup for a long: down move has run n bars; against = sell setup), cd_support/against_ge{8,12,13}, nine / nine_perf / c13 / c13q / combo13 / flip _support|_against_w{0,2,5,11} (event of that kind within N bars: 'against' for a long = sell-side event), tdst_with/against. HTF (15, 60) are read at the same signal second (last complete bar). My own independent kernel (cf6_kern.demark) agrees with W-CF5 on every perfected/unperfected 9 event it flags (it flags a subset: it ends a setup at 9).
6. STREAKS (PUB definitions). sk_{tf}: with/against runs ge{3,5,8} of: up/down closes (close > prior close), same colour (close > open), Heikin-Ashi colour (HA close=(o+h+l+c)/4, HA open=(prev HA open + prev HA close)/2), higher highs / lower lows, consecutive bars each making a NEW GLOBEX-DAY high / low (ge 3,5,8,10), inside-bar run ge{1,2,3}, narrow-bar (range < 0.5 ATR) run ge{2,3,5}, NR4 / NR7. Patterns (exact, completed bars, within 0 or 2 bars; 'with' = bullish for long): three white soldiers (3 up bars, closes rising, each open inside the prior body, closes in the top 30 pct of range, first body >= 0.3 ATR) / three black crows mirrored; three-line strike (3 down bars with lower closes, then an up bar that opens below the prior close and closes above the first bar's open) and mirror; rising / falling three methods (long bar body >= 0.8 ATR, then 3 small counter-colour bars with bodies <= half the long body staying inside its high-low range, then a bar closing beyond the long bar's close).
7. TIME COUNTS (APX; causal pivots). Zig-zag 1.0 ATR pivots, known at their confirmation bar. tc_{tf}: bars since the last confirmed swing low (for a long: leg age; for a short: since the swing high) 'with', and the opposite 'against'; near5/8/13/21/34/55 and 9/18/27/36 (+-1 bar), any-Fibonacci, any-fixed; leg symmetry ratio (current leg bars / previous leg bars) with band 0.85-1.15; raw minutes since the last signal of the same book / tf. 5 and 15 min.
8. WAVE COUNTS (APX, mechanical; discretionary Elliott cannot be coded). Big zig-zag 1.5 ATR pivots; state machine (kern.waves): wave 2 must not retrace beyond wave 1's start, wave 3 must end beyond wave 1's end (and 'valid' only if not shorter than wave 1; shortest-wave test), wave 4 must not enter wave 1 territory, after wave 5 comes A, B, C; B beyond the wave-5 end = trend resumes; any violation re-anchors. wv_{tf}_in_{w1..w5,A,B,C}_{with,against} (the developing swing's direction vs the trade), in3_with_valid, three_swing_corr_C_with.
9. HORIZONTAL COUNTS (APX). Box = the longest window (72,48,36,24,18,12,8 bars) ending 1-3 bars before the signal whose high-low span <= 3 ATR; the signal bar (or one of the last 3) must close beyond the box edge in the trade's direction. hz_{tf}: break_from_box_with, box width classes 8-12/13-24/25-48/49-72 bars, touches of the broken / other side (within 15 pct of the height of the edge, distinct visits >3 bars apart) ge3, ge4, target_inside / target_beyond the projection (height x 1, 1.5, 2) compared with our fixed target (tgt_pts); raw box bars, height, volume.
10. COUNTS ON D7'S OWN EVENTS. From the signal list of each book (signal events known at their own second): ev_book_sess_nprior_ge{1,2,3} (earlier signals of this book in the same Globex day and session), consec_same_ge{2,3} (run of same-side prior signals), flips (side change between consecutive signals of the book) in the last 60 / 180 min ge{1,2,3} for the book and for the whole stack, minutes since the last flip le{15,60,180}. 'Engine flips' are approximated by signal side changes: the engines' own flip log was not used. Outcome-dependent columns (se_d7_after_*) use only trades whose exit_ts <= the signal second.

### Worked examples (our own NQ data; ET times; the value shown is what the count said)
Brooks: (1) M7 short 2026-10-08 03:59:00 on 5-min coding A: a L2 (second lower-low bar after a failed attempt) formed within the last 2 bars (running count already reset to 2 -> 0 as a new low followed); trade R -0.62. (2) K7 short 2026-09-22 04:06:00: L2 with the bar high within 0.5 ATR of the 5-min EMA20 and close below it (textbook Low 2 at the 20 EMA): R +1.0.
Second entry: (1) P7 short 2026-10-15 03:52:00: last L-event on 5-min was a second entry, 3 bars after the first (H1/L1), R +1.0. (2) P7 long 2026-10-22 21:29:01: second entry 4 bars after the first, R -0.51.
Legs/pushes: (1) P7 long 2026-09-07 21:09:00: active 5-min leg up with 4 pushes (small 0.6-ATR swings) and RSI divergence at the last push: 'wedge with divergence with the trade' = yes (a late-leg entry), R +1.0. (2) P7 short 2026-09-15 11:50:00: two-legged pullback complete (>=2 small legs against the trade and the turn confirmed), R +1.0.
Bar number: (1) K7 short 2026-09-28 10:06:00: last complete 5-min bar = bar 7 since 09:30 (first-12 window), R +1.0. (2) P7 short 2026-10-12 11:14:00: bar 20 (the 17-21 'late-morning' window), R -0.57.
DeMark: (1) K7 long 2026-09-30 21:09:00: a buy setup 9 (five-min, 'support' for a long) completed within the last 5 bars, current signed setup state -5 (a sell setup 5 running), R +1.0. (2) H7 short 2026-10-12 21:50:00: a countdown 13 on the trade's own side completed within 11 bars ('c13_against'), R +1.0.
Streaks: (1) K7 short 2026-09-24 13:45:00: eight consecutive down closes on 5-min (with the short) - a streak of 8 - R -0.44. (2) P7 short 2026-10-11 21:08:00: three black crows completed within the last 2 bars, R +1.0.
Time counts: (1) K7 long 2026-10-18 23:15:00: 9 five-min bars since the last confirmed 1.0-ATR swing low (near 8 within +-1), R +1.0. (2) A7 short 2026-10-25 21:05:00: 8 bars since the last confirmed swing high, R -1.0.
Waves: (1) P7 short 2026-10-21 00:21:00: the 5-min zig-zag labels the developing swing as swing 3 in the trade's direction, R +1.0. (2) K7 short 2026-10-25 21:06:00: also swing 3 with the trade, R -0.8.
Horizontal: (1) K7 long 2026-10-27 18:18:00: break of an 8-bar, 25.75-pt box on 5-min in the trade's direction (box height << our target), R +1.0. (2) M7 long 2026-10-23 02:15:00: break of an 8-bar, 69-pt box, R -0.5.
Own events: (1) M7 short 2026-10-21 04:35:00: two book flips (side changes) in the last 60 minutes ('chop'), R +1.0. (2) P7 long 2026-10-13 04:09:00: two flips in 60 min, R -0.55.

## Addendum A (2026-11-15), appended after the sha line: long history for ICT Step A
Same rules R1-R4, key counts, outcomes, trend/neighbour/random-anchor controls as above, no change. Data: NQ.v.0 (GLBX.MDP3 ohlcv-1m, volume roll) 2013-01-02..2026-10-30 from data/autopilot/ohlcv1m/NQ_<year>.dbn.zst; additive back-adjust at each of the 55 instrument_id changes (earlier prices shifted by o_new - c_old); stored /mnt/l2/l2vast/_confl/cf6_min1_NQ_long.npz; bars as before (CF6_LONG=1). Month index base 2013-01. Eras: 2013-16, 2017-19, 2020-22 (PRE2023 = out of sample for the 7-8 hypothesis), 2023-26. Random anchors are shifted by 1/3 and 2/3 of the sample. Code: ict_stepA.py, ict_analyze_long.py (CF6_LONG=1), cf6_long.py.

## Addendum B (2026-11-15): Step B columns, alt-bar columns, Step C screen (appended; earlier text unchanged)
Step B (ict_stepB.py, CF6_LONG=1 bars so daily/weekly counts are warm): per tf 5/15/60/240 and anchor a40 / b5 / cday (+ a40 with R4 N12 k1.5): cur_with, cur_against (count of the move in the trade's direction / opposite, base rules), bars_since_anchor_with, distortion_with (bars since anchor / counted candles), atkey_with|against (count in {7,8,12,13,20,21,33,34,40,41,42}), keygroup_with (1=7-8, 2=12-13, 3=20-21, 4=33-34, 5=40-42), with78_after_retr / with3334_after_retr (key count with the trade AND the leg extreme minus close >= 0.5 ATR), exhaust_with_move / exhaust_against_move (count in 12-13,20-21,40-42 with / against the trade), per-group with_/against_ flags, ict_ntf_atkey_with|against(_ge1..3) over the four timeframes (a40), daily a20/a40 and weekly a20 context.
Alt bars (cf6_alt.py): Brooks coding A and streaks on range8/16, renko8/16, vol500/2000, tick2000 (W-CF4 stores); bar used only if ts_close <= signal second; HA from each bar set (APX).
Step C (ict_books.py, ict_books_run.py): standalone 1-min screen described in the page; cost 1.0 pt RT + $4.84 per lot; stop first when both levels in one minute.

## Addendum C (2026-11-15), appended: C4 and counting books
C4 (checklist as the signal) coding: see DS3_CONFLUENCE_C4.md 'What was built' (13 outcome-free clusters of 120 indicator states, 12-month trailing selection with |t| >= 2, direction from the training mean, entry = first minute >= 15 of the window with k kept clusters agreeing for 5 consecutive minutes, k = 3/4/5, one entry per side per window and day; brackets standard 30/60 and forecast 0.3F/0.6F). Block 17 analog columns: a_analogs.py. Counting books: count_books.py (definitions in the page section 'COUNTING BOOKS').
