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
