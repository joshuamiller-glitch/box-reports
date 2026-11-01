# L2_FORWARD_LOG_SPEC - the L2 fields D6 would have to log so the 9 ranked exit-rule clusters can be scored forward without raw MBO (A10, 2026-11-01). Spec only: nothing is built, nothing is bought, no existing spec file is edited. NEEDS, not a PASS

Conventions inherited unchanged from `shadow_log_schema.csv` (columns table,field,type,required,rules,description), `D6_LOG_WRITER_SPEC.md` section 0 and `FORWARD_SHADOW_SPEC.md` sections 0 and 4: epoch ms UTC; `signal_id = book|epoch_ms|side` is the join key; every signal logged (taken or not; paper books S6 W6 MA6 C6 as paper rows); the log holds INPUTS, counterfactual exits are computed offline from tape + log; a state D6 cannot compute is written BLANK with a reason, never 0; read-only, evaluated off the order path, fail-open, append-only buffered writes, the L2 module disables ITSELF (not the signal log) if its p99 exceeds 50 ms; nothing before 2026-11-01 23:00Z (Sun 18:00 ET) is real; `synthetic=1` rows are refused by real runs. Rows below are in the same CSV layout; the `rules` column names the consumer: `all_l2` every L2 consumer, `l2sp` the profit-side clusters (cl11, 12, 13, 15, 16, 18, 8), `l2sl` the loss-side arm + tighten clusters (cl1, cl3), `l2lead` the lead flags of cl3 (iceberg, sweep, wall-gone, imb10), `uf_es` the UF-LOSS series inside cl3 (optional), `audit` quality checks. The machine-readable copy is `l2vast/ds3/out/l2clusters/l2_forward_log_schema_addition.csv`.

## 1. What each cluster needs and what D6 has

| cluster (rank) | what the scorer must reconstruct | L2 inputs (tables) | already legal in D6 (THP `pct mins secs_ext dd recov vel30 eff120 delta60 imb5 imb10 wall_tgt wall_stop curDepthRel pulled_sup10`) | missing in D6 v2.3b / v2.4 |
|---|---|---|---|---|
| cl11 (1), cl12 (3), cl13 (5), cl16 (4), cl15 (7), cl18 (8), cl8 (9): L2SP | latched MFE arm; ahead / total 8-tick depth relative to a 20-day baseline (hour, session, 30-min z, trailing 60 min); dwell of 1-4 consecutive 10-s rows; trail / lock / half exit; p70 take | l2_ladder_10s (dep8_*), l2_baseline, l2_intrade_10s (mfe_pts, rel_*), tape for the exit path | pct, curDepthRel (= rel_tot8_hour) | ahead-side depth, session/z/t60 baselines, latched MFE, dwell, trail/lock/half action; D6 v2.4 has no L2 field |
| cl1 (2): L2SL A45 tighten | adverse excursion >= 45 pts, tighten stop to MAE+10 (PRE/X' cut needs the price path only); optional pulled-liquidity share/mult over 5/10/30 s and new-extreme flag | tape; l2_flow_1s (pulled_*), l2_intrade_10s (pulled_sup5/10/30, med_own_level, pulled_share*, new_adv_ext*) | pct, secs_ext, pulled_sup10; tighten action (semantics to confirm) | pulled_sup5/30, medOwnLevel, shares, mult/z forms |
| cl3 (6): L2SL + UF-LOSS | as cl1 plus lead flags: iceberg against, sweep against, own-side wall gone, imb10 <= -0.3 (any 2 = K2) and UF-LOSS gates (cum_behind, refill ratio, ES imbalance) | l2_flow_1s (cons_*_best, sweep_*_n, bid/ask_sz1_end), l2_ladder_10s (imb10, ladders), l2_baseline own10, optional l2_es_10s | imb10 | icebergAgainst, sweepAgainst10, ownDepth10Rel, leadCount2of4, es_imb5 |

What is NOT requested: wall_tgt / wall_stop and queue position at the target or stop (mbp-10 sees ~2.5 pts, the brackets are 33-60 pts; no ranked cluster uses them), raw MBO order lifetimes (UF-LOSS cycle 6/8 items; declined by the user and not used by any ranked cluster), per-level prices beyond the gap counters, ES/RTY depth for anything but the optional UF-LOSS table.

## 2. Cadence (and why)

* **Flows at 1 s** (`l2_flow_1s`): the cluster windows are 5 s (pulled_sup5, new_adv_ext5), 10 s (iceberg, sweep, pulled_sup10) and 30 s; storing per-second sums lets the scorer rebuild every window exactly and re-cut thresholds offline. A 5-s cadence would break the 5-s windows.
* **Ladder at 10 s on the global 10-s epoch grid** (`l2_ladder_10s`): decisions in the research cells are taken on 10-s rows (L2SL dp10s rows, L2SP 10-s feed; exits at the close of the trigger/breach row). Depth levels are a state, not a flow, so one snapshot per decision row is enough; dwell latches count consecutive 10-s rows.
* **Per-second-in-trade at 10 s** (`l2_intrade_10s`): sided features computed by D6 itself on the same grid. They are derivable offline from the two market tables + tape, so they are the AUDIT MIRROR (section 6) and the direct input of the scorer; they can be switched off to save about 11 MB/day once the audit passes.
* **Tape**: the 1-s high/low/last path for the exit replay comes from the already-approved weekly NQ.v.0 ohlcv-1s feed (HM_FORWARD_FEED section 6, $1.15/wk) and from `px_hi/px_lo/px_last` in l2_flow_1s as a cross-check; no per-signal price path is logged.

## 3. Tables and fields (shadow_log_schema.csv layout)

Units: size = contracts; price = points (NQ tick 0.25); `ts_end_ms` = END of the second, exclusive; side = +1 long / -1 short; SUPPORTING side = bids for a long, asks for a short; AHEAD side = asks for a long, bids for a short (DS3_L2_FEATURE_DEFS.md); book state = last snapshot with exchange timestamp <= T; trade classification last >= ask buy / <= bid sell. `required` = 1 means the column must exist (blank allowed only with a null reason).

```csv
table,field,type,required,rules,description
l2_flow_1s,ts_end_ms,int,1,all_l2,"epoch ms UTC of the END of the second (k*1000, exclusive end; research convention: decision time T = end of second s). One row for EVERY second of the session while the L2 feed is connected, including seconds with no print (flows 0). Session = Sunday 18:00 ET to Friday 17:00 ET"
l2_flow_1s,contract,str,1,all_l2,"NQ front-month outright contract id (raw prices, no back-adjustment); a change between consecutive rows = roll; ES/RTY not logged here"
l2_flow_1s,ob_live,int,1,all_l2,"1 if a book snapshot with exchange timestamp <= T exists and ob_age_ms <= 3600000 (research ob_live), else 0 and the book fields of the row are blank"
l2_flow_1s,ob_age_ms,int,1,all_l2,T minus exchange timestamp of the last book update <= T (ms)
l2_flow_1s,l2_null_reason,str,0,all_l2,why book/flow fields are blank (feed_down|book_stale|roll|writer_overload|warmup); never write 0 for a state D6 could not compute
l2_flow_1s,n_trd,int,1,l2sp;l2sl,number of trade prints in the second
l2_flow_1s,vol,int,1,l2sp;l2sl,contracts traded in the second
l2_flow_1s,vol_buy,int,1,l2sp;l2sl,aggressor-buy contracts (print at or above the best ask before the print = buy; at or below the best bid = sell; others split by tick rule or dropped to vol_unk)
l2_flow_1s,vol_sell,int,1,l2sp;l2sl,aggressor-sell contracts
l2_flow_1s,px_hi,float,1,audit,highest trade price in the second (pts); cross-check against the weekly ohlcv-1s tape (HM feed)
l2_flow_1s,px_lo,float,1,audit,lowest trade price in the second
l2_flow_1s,px_last,float,1,audit,last trade price in the second
l2_flow_1s,pulled_bid_1_10,int,1,l2sp;l2sl,"contracts REMOVED from bid levels 1-10 during (T-1s,T] that were not executed (cancel / reduce; D6 rule: size decrease at a level not matched by a trade print at that price within +-100 ms; research parity target = Databento mbp-10 cancel actions). Supporting side of a LONG"
l2_flow_1s,pulled_ask_1_10,int,1,l2sp;l2sl,same for ask levels 1-10 (supporting side of a SHORT)
l2_flow_1s,added_bid_1_10,int,1,l2sl;l2lead,contracts ADDED on bid levels 1-10 during the second
l2_flow_1s,added_ask_1_10,int,1,l2sl;l2lead,contracts ADDED on ask levels 1-10 during the second
l2_flow_1s,cons_bid_best,int,1,l2lead,"contracts traded AT the best bid (aggressor sells hitting the displayed bid) in the second; the iceberg numerator for a SHORT loser is the 10-s sum of this field (ahead side of a short = bids), for a LONG loser the 10-s sum of cons_ask_best"
l2_flow_1s,cons_ask_best,int,1,l2lead,contracts traded AT the best ask in the second
l2_flow_1s,add_bid_best,int,0,l2lead,contracts added at the best bid in the second (refill numerator)
l2_flow_1s,add_ask_best,int,0,l2lead,contracts added at the best ask in the second
l2_flow_1s,can_bid_best,int,0,l2lead,contracts cancelled at the best bid in the second
l2_flow_1s,can_ask_best,int,0,l2lead,contracts cancelled at the best ask in the second
l2_flow_1s,bid_sz1_end,int,1,l2lead,size at best bid at T (iceberg denominator; displayed best size)
l2_flow_1s,ask_sz1_end,int,1,l2lead,size at best ask at T
l2_flow_1s,sweep_buy_n,int,1,l2lead,"number of trade-driven touch clears in the second in which a BUY aggressor consumed >= 2 ask price levels (research swp_n_buy; sweepAgainst10 of a LONG loser = sum over 10 s of sweep_sell_n, of a SHORT loser = sweep_buy_n)"
l2_flow_1s,sweep_sell_n,int,1,l2lead,same for SELL aggressors consuming >= 2 bid levels
l2_flow_1s,big25_buy,int,0,uf_es,aggressor-buy contracts in prints >= 25 contracts in the second
l2_flow_1s,big25_sell,int,0,uf_es,aggressor-sell contracts in prints >= 25 contracts
l2_flow_1s,vol_unk,int,0,audit,contracts whose aggressor side could not be assigned (quality flag)
l2_ladder_10s,ts_end_ms,int,1,all_l2,"epoch ms end of the second, on the global 10-s epoch grid (multiple of 10000), the same grid as the research dp10s rows; book state = last snapshot with exchange ts <= T"
l2_ladder_10s,contract,str,1,all_l2,as l2_flow_1s
l2_ladder_10s,ob_live,int,1,all_l2,as l2_flow_1s
l2_ladder_10s,bid_px1,float,1,all_l2,best bid price (pts)
l2_ladder_10s,ask_px1,float,1,all_l2,best ask price (pts)
l2_ladder_10s,bid_sz_L1,int,1,l2sp;l2sl;l2lead,"resting contracts at the 1-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L2,int,1,l2sp;l2sl;l2lead,"resting contracts at the 2-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L3,int,1,l2sp;l2sl;l2lead,"resting contracts at the 3-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L4,int,1,l2sp;l2sl;l2lead,"resting contracts at the 4-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L5,int,1,l2sp;l2sl;l2lead,"resting contracts at the 5-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L6,int,1,l2sp;l2sl;l2lead,"resting contracts at the 6-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L7,int,1,l2sp;l2sl;l2lead,"resting contracts at the 7-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L8,int,1,l2sp;l2sl;l2lead,"resting contracts at the 8-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L9,int,1,l2sp;l2sl;l2lead,"resting contracts at the 9-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,bid_sz_L10,int,1,l2sp;l2sl;l2lead,"resting contracts at the 10-th bid LEVEL (level 1 = best; levels, not ticks)"
l2_ladder_10s,ask_sz_L1,int,1,l2sp;l2sl;l2lead,resting contracts at the 1-th ask level
l2_ladder_10s,ask_sz_L2,int,1,l2sp;l2sl;l2lead,resting contracts at the 2-th ask level
l2_ladder_10s,ask_sz_L3,int,1,l2sp;l2sl;l2lead,resting contracts at the 3-th ask level
l2_ladder_10s,ask_sz_L4,int,1,l2sp;l2sl;l2lead,resting contracts at the 4-th ask level
l2_ladder_10s,ask_sz_L5,int,1,l2sp;l2sl;l2lead,resting contracts at the 5-th ask level
l2_ladder_10s,ask_sz_L6,int,1,l2sp;l2sl;l2lead,resting contracts at the 6-th ask level
l2_ladder_10s,ask_sz_L7,int,1,l2sp;l2sl;l2lead,resting contracts at the 7-th ask level
l2_ladder_10s,ask_sz_L8,int,1,l2sp;l2sl;l2lead,resting contracts at the 8-th ask level
l2_ladder_10s,ask_sz_L9,int,1,l2sp;l2sl;l2lead,resting contracts at the 9-th ask level
l2_ladder_10s,ask_sz_L10,int,1,l2sp;l2sl;l2lead,resting contracts at the 10-th ask level
l2_ladder_10s,bid_gap_ticks,int,1,l2sp;l2lead,(price span from level 1 to level 10 on the bid side in ticks) - 9; 0 = contiguous ladder. Needed to map price to level (research gap_behind/gap_ahead; ~1% of seconds are non-contiguous)
l2_ladder_10s,ask_gap_ticks,int,1,l2sp;l2lead,same on the ask side
l2_ladder_10s,dep8_bid,int,1,l2sp,"D6 value: sum of resting bid size at prices within 8 ticks of the touch (touch tick and 8 ticks away, i.e. nine ticks; contiguous ladder = levels 1-9; with gaps the levels whose price is within 8 ticks). Numerator of rel_tot8 / rel_ahead8 for a SHORT"
l2_ladder_10s,dep8_ask,int,1,l2sp,D6 value: same on the ask side (ahead side of a LONG)
l2_ladder_10s,imb5,float,1,l2sl;l2lead,"(sum bid L1-5 - sum ask L1-5)/(sum + ) UNSIDED, +=bid heavy; scorer multiplies by trade side"
l2_ladder_10s,imb10,float,1,l2sl;l2lead,"same over levels 1-10 (THP legal feature, D6 computes today)"
l2_ladder_10s,spread_ticks,int,0,audit,ask_px1 - bid_px1 in ticks
l2_baseline,baseline_ver,str,1,l2sp;l2lead,"hash of the baseline code + parameters (windows 20 label days, min 5 days, MAD scale 1.4826)"
l2_baseline,asof_ts_ms,int,1,l2sp;l2lead,epoch ms the table was frozen (18:00 ET rollover); uses only rows with label day < today
l2_baseline,kind,str,1,l2sp;l2lead,hour|sess|bucket30|own10 (one row per key)
l2_baseline,key,str,1,l2sp;l2lead,hour: ET hour 0-23; sess: asia|london|pre|nyam|nypm|close; bucket30: ET half-hour index 0-47; own10: ET hour
l2_baseline,n_days,int,1,l2sp;l2lead,prior label days available (a baseline with n_days < 5 is blank and the dependent features are blank with l2_null_reason=warmup)
l2_baseline,med_tot8,float,1,l2sp,median over the prior 20 label days of dep8_bid+dep8_ask (both sides) over the 10-s rows of that key
l2_baseline,med_bid8,float,1,l2sp,median of dep8_bid (ahead baseline of a SHORT)
l2_baseline,med_ask8,float,1,l2sp,median of dep8_ask (ahead baseline of a LONG)
l2_baseline,mad_tot8,float,0,l2sp,bucket30 only: median absolute deviation of the bucket medians x 1.4826 (z-score scale); z = (x - centre)/scale with centre = median of the bucket medians
l2_baseline,mad_bid8,float,0,l2sp,bucket30 only
l2_baseline,mad_ask8,float,0,l2sp,bucket30 only
l2_baseline,med_bid10,float,0,l2lead,own10 only: median of sum bid L1-10 (own-side depth norm of a LONG; ownDepth10Rel)
l2_baseline,med_ask10,float,0,l2lead,own10 only: median of sum ask L1-10
l2_intrade_10s,signal_id,str,1,all_l2,"key into signals (book|epoch_ms|side). One row per 10-s grid second while the trade is open: taken=1 trades until the live exit; taken=0 / paper trades until the hypothetical bracket (stop_d / tgt_d from signal_px on the tape) is touched or the 16:55 ET flatten, hard cap 24 h"
l2_intrade_10s,ts_end_ms,int,1,all_l2,10-s epoch grid second (end of second)
l2_intrade_10s,upnl_pts,float,1,l2sp;l2sl,"side*(px_last_T - signal_px), points, open P&L per contract before costs (research upnl)"
l2_intrade_10s,mfe_pts,float,1,l2sp,"running maximum of upnl_pts since entry second (latched MFE; the L2SP arm; D6 pct is current, not latched)"
l2_intrade_10s,mae_pts,float,1,l2sl,running maximum adverse excursion since entry second (>=0; = -min upnl_pts)
l2_intrade_10s,pct,float,1,l2sp;l2sl,upnl_pts / tgt_d (THP legal feature)
l2_intrade_10s,secs_since_mae_ext,int,1,l2sl,seconds since the last new adverse extreme (THP secs_ext analogue); newAdvExt{w} = 1 iff <= w
l2_intrade_10s,new_adv_ext5,int,1,l2sl,"1 if a new MAE maximum was set in (T-5s,T], 1-s px_hi/px_lo path"
l2_intrade_10s,new_adv_ext10,int,1,l2sl,"same, 10 s"
l2_intrade_10s,new_adv_ext30,int,1,l2sl,"same, 30 s"
l2_intrade_10s,pulled_sup5,int,1,l2sl,"contracts pulled from the SUPPORTING side (bids for a long) levels 1-10 over (T-5s,T] = sum of pulled_bid/ask_1_10 from l2_flow_1s"
l2_intrade_10s,pulled_sup10,int,1,l2sl,"same, 10 s (THP legal feature, D6 computes today)"
l2_intrade_10s,pulled_sup30,int,1,l2sl,"same, 30 s"
l2_intrade_10s,med_own_level,float,1,l2sl,median of the own-side (supporting) L1..L10 sizes at T (contracts)
l2_intrade_10s,own_depth10,int,1,l2sl;l2lead,sum of own-side L1..L10 sizes at T
l2_intrade_10s,pulled_share5,float,1,l2sl,pulled_sup5 / (pulled_sup5 + own_depth10); share10 and share30 likewise
l2_intrade_10s,pulled_share10,float,1,l2sl,
l2_intrade_10s,pulled_share30,float,1,l2sl,
l2_intrade_10s,ice_against,int,1,l2lead,"1 iff contracts traded at the best AHEAD price in (T-10s,T] (asks for a long loser) >= 10 x displayed best size at T"
l2_intrade_10s,swp_against10,int,1,l2lead,"sweeps by the adverse aggressor in (T-10s,T]"
l2_intrade_10s,own_depth10_rel,float,1,l2lead,own_depth10 / med_bid10 (long) or med_ask10 (short) of the ET hour (wall-gone flag: <= 0.5)
l2_intrade_10s,imb10_sided,float,1,l2sl;l2lead,imb10 x side
l2_intrade_10s,dep8_ahead,int,1,l2sp,"dep8_ask for a long, dep8_bid for a short at T"
l2_intrade_10s,dep8_behind,int,1,l2sp,the other side
l2_intrade_10s,rel_tot8_hour,float,1,l2sp,(dep8_bid+dep8_ask)/med_tot8[hour] = THP curDepthRel (D6 computes today)
l2_intrade_10s,rel_ahead8_hour,float,1,l2sp,dep8_ahead / med_ask8[hour] (long) or med_bid8[hour] (short)
l2_intrade_10s,rel_tot8_sess,float,1,l2sp,/ med_tot8[sess]
l2_intrade_10s,rel_ahead8_sess,float,1,l2sp,/ med_ask8|med_bid8[sess]
l2_intrade_10s,z_tot8_b30,float,1,l2sp,(tot8 - med_tot8[bucket30])/mad_tot8[bucket30]
l2_intrade_10s,z_ahead8_b30,float,1,l2sp,same for the ahead side
l2_intrade_10s,rel_tot8_t60,float,1,l2sp,tot8 / median of tot8 over the trailing 60 min of 10-s rows strictly before T (blank if < 60 samples)
l2_intrade_10s,rel_ahead8_t60,float,1,l2sp,same for the ahead side
l2_intrade_10s,l2_null_reason,str,0,all_l2,blank unless a feature is blank (warmup|book_stale|gap_ladder|roll)
signals,l2_ver,str,0,all_l2,"version/hash of the L2 module in force at the signal; a change starts a new scoring segment (scorer warns, like live_config_ver)"
signals,l2_null_reason,str,0,all_l2,why the entry-second L2 state is blank
signals,l2_rel_tot8_hour_t0,float,0,l2sp,curDepthRel at t0 (entry-side state; allows the L2 clusters to be re-cut as entry filters later)
signals,l2_rel_ahead8_hour_t0,float,0,l2sp,rel_ahead8_hour at t0
signals,l2_imb10_sided_t0,float,0,l2lead,imb10 x side at t0
signals,entry_fill_ts_ms,int,0,all_l2,joined after the fill: epoch ms of the first entry fill (live trades)
signals,entry_fill_px,float,0,all_l2,"joined after the fill: VWAP of the entry fills; research anchor is signal_px (planned E), so the scorer reports the difference"
l2_es_10s,ts_end_ms,int,1,uf_es,"10-s epoch grid second (optional table, only for the 11 UF-LOSS series inside cluster 3; skip if D6 has no ES depth)"
l2_es_10s,es_contract,str,1,uf_es,ES front contract id (roll guard)
l2_es_10s,es_imb5,float,1,uf_es,"(bidES5 - askES5)/(bidES5 + askES5) over 5 ES book levels, UNSIDED, last ES snapshot <= T"
l2_es_10s,es_hb_age_ms,int,1,uf_es,age of the last ES message of any type (quote or trade)
```

## 4. Storage per day (ESTIMATE from field counts; the D6 owner must measure the first full day and replace these)

Assumptions: CSV ~6.5 bytes per field incl. separator; 23 h x 3,600 = 82,800 session seconds per day; 8,280 ten-second rows; in-trade rows = 10-s grid seconds with at least one open trade (research 2025-26: about 460-490k open-trade seconds per day over 10 books incl. paper, i.e. about 48k rows; 50,000 used); five sessions a week; gzip about 4-5x, parquet about the same (the research dp10s store is 3.2 GB for 3 years, 135 columns).

| table | rows/day | fields | CSV MB/day | gz MB/day (est.) |
|---|---|---|---|---|
| l2_flow_1s | 82,800 | 29 | 15.6 | 3.5 |
| l2_ladder_10s | 8,280 | 32 | 1.7 | 0.4 |
| l2_intrade_10s | ~50,000 | 33 | 10.7 | 2.4 |
| l2_baseline | 24+6+48+24 = 102 | 13 | <0.01 | <0.01 |
| signals additions | ~60-85 | 7 | <0.01 | <0.01 |
| **total, full set** | | | **28** | **6.2** |
| total, minimum set (no l2_intrade_10s) | | | 17 | 3.9 |

Per week (5 sessions): about 140 MB CSV / 31 MB gz full; per year (50 weeks) about 7.0 GB CSV / 1.6 GB gz full; the 104-week read date needs about 14.6 GB CSV (3.2 GB gz). Optional l2_es_10s: 8,280 rows x 4 fields = 0.2 MB/day.

## 5. Writer constraints (additions to D6_LOG_WRITER_SPEC checklist, section 7)

1. Depth handler keeps per-second counters in pre-allocated arrays (O(1) per depth event, no allocation, no I/O); a separate thread flushes at the second boundary; ladder snapshot copy once per 10 s. NQ peaks at 10^4 depth events/s; if the handler p99 exceeds 50 ms the L2 module switches off and writes `l2_null_reason=writer_overload` (the signal log is unaffected).
2. Warm-up: baselines need >= 5 prior label days (min), 20 for full strength; the research store ends 2026-02-06, so the baseline table starts EMPTY at t0 (no seeding from history: the tick-level definitions differ). Clusters are scorable from the first week for the price-path part and from week 2 (hour/session) to week 4 (20-day) for the depth part; the scorer reports the blank rate and excludes, never zero-fills.
3. Roll: `contract` changes -> `l2_null_reason=roll` for the 10-s rows around the roll and baselines are keyed to the front contract's own sizes (no cross-contract median).
4. The L2 module must not change any order, lot, stop, target, lock or governor; `l2_ver` changes start a new segment.

## 6. Audit gate (pre-stated; the existing 0.5% rule cannot apply because D6's NT8 depth feed is not the research Databento mbp-10)

The research definitions were built on Databento mbp-10 (cancel actions, per-level sizes). D6 reads NT8 market depth, in which a size decrease is not labelled cancel versus fill. Before any cluster is scored: buy two sample weeks of NQ.v.0 mbp-10 (about $23-27 each, HM_FORWARD_FEED quotes; ~$50 of the ~$811 remaining) and rebuild l2_ladder_10s / l2_flow_1s with the research builder (`l2vast/ds3/code/l2feat/l2f_build.py`). Gate (all must hold): dep8_bid/ask median relative difference <= 3% and rank correlation >= 0.98 over 10-s rows; pulled_sup10 median relative difference <= 15% and rank correlation >= 0.90; ice_against / swp_against10 / new_adv_ext10 flag agreement >= 95%; blank rate <= 1% of session seconds; px_last equals the ohlcv-1s tape on >= 99.9% of seconds. If the gate fails the offending field is voided (the scorer prints which) and the cluster that needs it is NOT scored; the price-path core of cl1 / cl3 needs only the tape.

## 7. Cost and why this route

The log is free and permanent; the alternative (weekly mbp-10 purchase, $23.12-26.57 per NQ week; the approved L2 buy of ~$36/week for NQ+ES+RTY exhausts the remaining ~$811 in about 22 weeks) cannot reach the 104-week read of DS3_L2_CLUSTERS.md section 5 (about $2,400-2,800 for NQ alone). Raw MBO ($214 for L6M alone) was declined by the user and no ranked cluster needs it. So the D6 log is the data source and a purchased sample is the audit.
