# CONFLUENCE_DEFS_CF2 (W-CF2). Categories F, G, H, I, J and Block 5. Code: code/th_confl_cf2. Columns: /mnt/l2/l2vast/_confl/cols_cf2/{FG,I,J,H,B5}.parquet keyed by sig_id (= <book7>_<sig_ts>).
VERDICT: 5 column files (638 conditions, FG 101, I 72, J 148, H 55, B5 262) built for all 48,353 rows of signals_all.parquet (19,798 taken + 28,555 skipped, W-CF1's current rows; later rows are appended by `python3 code/th_confl_cf2/build_all.py <FG|I|J|H|B5>`, which only computes missing sig_ids); no PASS claims.

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
