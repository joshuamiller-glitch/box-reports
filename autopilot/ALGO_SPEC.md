# ALGO_SPEC - real-time trade-management algo for the live books (W-DYNA owns this page; order 13:07Z item e)

Version 0.1 skeleton, 2026-11-27 13:26Z. Keys-page standard: every item is `key = value` with its status: SPEC = read from running code / committed rule file (the relay can code it as written), READING = my reading of an agent's text or code that the owner must confirm, OPEN = not decided yet / owner named. Research only; nothing here touches the execution server. Version log: ALGO_LOG.md. Owners: A and B loops W-DYNC, C loop W-DYNML, engine hook W-DYNH, inputs and lags W-DYNX8, spec and match tables W-DYNA.

## 0. WHAT IS FIXED
```
entries                = the live books' own entries, unchanged (SPEC: events file ts, side, lots)
book list              = Asia MF1-MF4; NY AM MF1-MF9 (live mix TL3_SR_AS_STKd8da2eb47b_FSff6_PICKC, TL3_SR_NY_STKd8cd0279ff_FSff6_PICKC); London LO_MF1-3 (TL3_SR_LO_STKd8w42lo_FSffb8_BARE); NY PM NP_MF1,3,4 (TL3_SR_NP_STKd893133bd8_FSf46_PICKC)   (SPEC)
safety stop at entry   = book stop distance S0 x k_safe, k_safe in {1.0 (reference), 1.5, 2.0}; also a vol-based disaster stop   (OPEN: the value is chosen by the replay; W-DYNC)
fixed target           = NONE in the algo rows; the bracket is the reference row   (SPEC, order 13:05Z)
hard flat              = 16:55 ET for everything, nothing over the daily close   (SPEC, order 13:07Z; Josh trades intraday only)
session bell flatten   = the live rule (UWTime: Asia 02:00, NY AM 12:00, London 08:30, NY PM 16:00 ET) is REPLACED in the algo rows by the manage loop; the live-as-run row keeps it   (READING: order 0914Z S1; W-DYNH decides what the engine runs)
lots / sizing          = the live lots of each entry; the algo never exceeds the original size   (SPEC)
```

## 1. INTERFACE
```
function  manage(state, landscape) -> (action, reason)
call rate = every second on the second boundary AND on any own-order event (fill, reject, cancel ack); (SPEC: X24 sim steps a 5-s grid; the live loop is 1 s; OPEN: W-DYNC to confirm the 1-s rate gives the same decisions as the 5-s screen)
decision lag = decisions use inputs stamped <= t - lag(input); orders become effective LAT_FILL = 1.0 s (market) / LAT_CANCEL = 0.5 s (cancel) after the decision   (SPEC: code/replica/sim.py PRM LAT_FILL, LAT_CANCEL)
```
state (all values at decision time t, per open trade):
```
trade_id, book, side (+1/-1), lots_original, lots_open, entry_px, entry_ts
S0 (book stop pts), T0 (book target pts, reference scale only), R_pts = S0
open_pts = side*(last - entry_px) ; open_R = open_pts / S0 ; peak_pts (best open_pts since entry) ; mae_pts
t_in_trade (s), t_to_bell (s), t_to_flat (s to 16:55 ET)
state_name in {PROBE, CONFIRMED, RUNNING, DEFENDING, OUT}
stop_px (current stop price), stop_order_id, safety_stop_px (never widened), n_changes_last_60s, last_change_ts
partial_done (bool), partial_lots, readd_done (bool)
score_for, score_against, score (= for - against), score_items{i1..i4}, range_state in {EXPANDING, CONTRACTING, NORMAL}
```
landscape (all stamped; see section 3): NQ tape+flow+book (1 s), ES, RTY last (1 s), UW series (minutes, lag 60-120 s), clock.
action set (one per call; SPEC unless stated):
```
HOLD
TIGHTEN_STOP(px)        stop only moves toward price; ratchet
LOOSEN_TRAIL(dist)      only while open_pts > 0 and only inside guard rails (section 5)
EXTEND_TARGET / PULL_TARGET / RELEASE_TARGET   (X24: extension and pull-in HURT; kept as OPEN actions for loop B/C)
TAKE_PART(frac)         market; frac of lots_original, min 1 lot; 1 lot = TAKE_ALL
TAKE_ALL                market, closes the position, state -> OUT
READD(lots)             after TAKE_PART only; once per trade; never above lots_original; never when open_pts <= 0   (SPEC: order 03:54Z)
```
reason codes: `<loop>.<rule_id>` e.g. `A.R3_wall_pulled`, `B.score<=-3`, `GUARD.peak50`, `SAFETY.stop`, `CLOCK.flat1655`, `BELL.carry`; every call returns one.

## 2. STATE MACHINE (READING of DIRECTIVE_ENGINE_ALGO_0354Z + fixed_rules_x24.json; thresholds SPEC where they come from the committed X24 file)
```
PROBE      entry fill -> initial = safety stop only; no target. stays until CONFIRMED or exit.
           -> CONFIRMED  when score >= +2 (evidence FOR) and open_R >= +0.25            (OPEN: thresholds from loop A/B, W-DYNC)
           -> OUT        safety stop hit | CLOCK.flat1655
           -> DEFENDING  score <= -2 and open_R < 0 (evidence against while under water): cut policy by rule list (loop A)   (OPEN)
CONFIRMED  stop moved to structure / breakeven after the first partial.
           -> RUNNING    TAKE_PART done (score-sized 25/50/75 % of lots: score>=2 25 %, -1..1 50 %, <=-2 75 %) and stop at breakeven; target released
           -> DEFENDING  score <= -2
RUNNING    trail active, steered by score: base distance 0.6*T0 ; score>=2 x1.5 (only in profit) ; score<=-1 x0.5 ; score<=-2 x0.3 ; style by range_state (expanding: chandelier 0.8*5-min range; score>=1 not expanding: structure trail 3-min low/high -/+ 2 pt; score<=-2: 0.15*T0)
           guard rails: stop >= peak*(1-g), g=0.50 primary (0.25/0.75 variants); stop >= breakeven after the partial; ratchet only; at most one change per minute except tighten; initial safety stop never widened
           -> DEFENDING  score <= -2 or stop distance shrinks below 0.15*T0
           -> OUT        stop hit | TAKE_ALL | clock
DEFENDING  tight trail 0.15*T0 / take the remainder when score <= -3 and open_pts >= 0.3*T0 (TAKE_ALL); score recovers to >= +1 for 60 s -> back to RUNNING (OPEN: hysteresis)
OUT        flat; log the exit reason; the entry slot is free again for the book (engine rule: one position per book; SPEC from the live engine)
```
Every transition is logged with its reason and the input snapshot (section 7).

## 3. INPUTS (the landscape) - id, source, field, rate, lag, history, status
| id | source | field | rate | stamped lag | history on the box | status |
|---|---|---|---|---|---|---|
| nq_last/hi/lo/vol | tables/NQ/1s | trd_px_last, trd_px_hi, trd_px_lo, trd_vol | 1 s | decision lag 1 bar | 2023-04-02 .. 2026-11-13 | SPEC |
| nq_flow | tables/NQ/1s | buy_vol, sell_vol (aggressor), big1-3_*, swp_vol_buy/sell, swp_n_* | 1 s | 1 bar | same | SPEC |
| nq_book10 | tables/NQ/1s | bsz1..10, asz1..10, imb1/3/5/10, imb5_ema1s/ema10s, spread_t, micro, mid, bid_px, ask_px | 1 s snapshot at second end | 1 bar | same | SPEC |
| nq_book_events | tables/NQ/1s | n_add/can/mod_* and sz_add/can_* by level group b1/b23/b410/a1/a23/a410, ofi1, ofi5, depl_b/a_trd/can, nclr_b/a, refill_n, refillfail_n, age_ns | 1 s | 1 bar | same | SPEC |
| nq_mbo_l3 | raw/NQ_mbo (dbn.zst day files) | order-level add/cancel/modify/trade with order ids and ts_recv | per event | engine book latency LAT_BOOK (OPEN: sim.py PRM LAT_BOOK=-1.0) | 2023-04-02 .. 2026-11-13, box1 only (read in place) | SPEC for the replay (W-DYNX8 dyn_replay.py, W-DYNA dyn_mbo.py wall features); live feed equivalence OPEN (relay) |
| es_last, rty_last | tables/ES/1s, tables/RTY/1s | trd_px_last | 1 s | 1 bar | ES, RTY from 2023-08 | SPEC |
| ym_zn_zb_crude, nkd, 6j | tables (instr_1s etc.) | OPEN: W-DYNOF lists | 1 s | OPEN | OPEN | OPEN |
| stocks/QQQ/SPY | none on the box | - | - | - | - | OPEN: not available (list/quote only, W-DYNOF) |
| uw_tide, uw_flow_alerts, uw_gex_spot | Unusual Whales series | net premium ticks, Market Tide, alerts, spot GEX by minute | 1 min | 60-120 s delivery lag (SPEC: dx_dyn.py) | by-strike intraday walls only from the live recorder, 9 trading days (autopilot/UW_INTRADAY_HISTORY.md) | READING |
| clock | engine | ET time, session bell, 16:55 flat | 1 s | none | - | SPEC |
Feature definitions (side-adjusted; windows in seconds; SPEC = fixed_rules_x24.json items):
```
i1_delta  = sum(buy_vol - sell_vol, 60 s) / sum(trd_vol, 60 s) * side          FOR >= +0.10, AGAINST <= -0.10
i2_ofi    = sum(ofi5, 60 s) / std over the last 3600 s of the same 60-s sum * side    FOR >= +0.5, AGAINST <= -0.5
i3_book   = EMA over 60 s (span 60 samples) of imb5 * side                      FOR >= +0.15, AGAINST <= -0.15
i4_mom    = side * (last_now - last_300s_ago)                                    FOR >= +12 pt, AGAINST <= -12 pt
range_state = (max hi - min lo over 300 s) / mean of that quantity over the last 3600 s ; > 1.5 EXPANDING ; < 0.8 CONTRACTING
score_for = number of items FOR ; score_against = number AGAINST ; score = for - against ; cutoffs strong_for +3, for +2, against -2, strong_against -3
```

### 3b. POOLS / WALLS / 10-LEVEL BOOK PER SECOND (merged 2026-11-27 from ALGO_INPUTS_POOLS.md, owner W-DYNL; library owner for MBO columns W-DYNX8)
Status: SPEC for pool and 10-level columns (code/th_dynl/liq_sec.py, pools_api.py, x23_pools.py), READING for the MBO columns (reserved, NaN). Cross-market columns follow from W-DYNL. Lags stamped by the owner: FEED_LAG = bucket start + 2 s; pool tables read at the last 1-min bar closed <= ts - 2 s; decision effective ORDER_LAG = 3 s later (engine latency 2.6 s; the engine sim uses LAT_FILL 1.0 s: OPEN: W-DYNL/W-DYNH to reconcile 3 s vs 1.0 s). My own wall channels (dyn_mbo.py: behind/ahead wall size, share resting >= 120 s, pulled/consumed, refill; replay only, sample months) are an alternative MBO definition: attribution 0 of 24 (06:55Z); the MBO columns of this table supersede them if W-DYNX8 delivers.
Code: code/th_dynl/liq_sec.py (+ pools_api.py, x23_pools.py builders). Tables: /mnt/l2/l2vast/_dynexit/x23/pools_1m.npz, prof_1m.npz, uw_ndx_levels.csv (copies on server C). Status: SPEC for pool/10-level columns (built and run on one trade, 17,517 s: build 3.8 s; hook object 3.4 ms per call); READING for the MBO columns (reserved for W-DYNX8).
HOOK CONTRACT: every second the engine hook calls `pool_state(ts_ns, side, px, hi_run, lo_run, stop_px)` (or `PoolHook(side, stop_px).update(ts_ns, px, px_hi, px_lo)`) and receives the columns below. px / hi_run / lo_run are the last 1-s bucket known at ts - FEED_LAG (bucket start ts + 1 s + 1 s); pool tables are read at the last 1-min bar closed <= ts - 2 s. Any decision made on the row is effective ORDER_LAG = 3 s later (engine latency 2.6 s). Identity check: with the loop off the columns change nothing in the trade.
POOL KINDS (13): sw5 sw15 sw60 (unswept swing highs/lows, 5/15/60 one-minute bars; known n minutes after the extreme), eq (equal highs/lows within 1.5 pts, known 5 min after the later), f1 f5 (untouched 3-bar fair value gaps 1-min / 5-min, both edges), ob (unmitigated order blocks), p1 p5 p20 (POC/VAH/VAL of the last 1/5/20 completed Globex days), uwall uwflip (UW NDX call/put wall, flip, magnet scaled to NQ; static per day, previous day's EOD file), hl (prior day H/L/C, overnight H/L, IB H/L). 'any' = all except f1 and the UW kinds.
STATUS: HELD = not traded through since created; SWEPT_RECLAIMED = traded through in the current minute and price back on the original side (X23b). Evidence on what pools do (autopilot/DYNEXIT_X23.md): reached more often than random in Asia, nothing special AT the pool; swing-60 and fair value gaps behind protect a stop, VWAP/RTH open behind do not; equal-pool stop LEAD (Asia). So the loop should use pool distance as a target/clearance feature and the sweep-reclaim state as an event, not as a barrier.
| column | meaning |
|---|---|
| pa_dist / pb_dist | distance (pts) to the nearest HELD pool ahead / behind in the trade direction over kinds ANYK (>= 2 pts); NaN if none |
| pa_kind / pb_kind | index into ANYK of that pool |
| pa_<kind> / pb_<kind> | same per kind (13 kinds) |
| pa_n25 / pb_n25 | number of HELD pools within 25 pts ahead / behind |
| psw_a_dist / psw_b_dist | distance to the nearest SWEPT_RECLAIMED pool ahead / behind (sweep-and-reclaim in the current minute); NaN none |
| pstop_dist | distance from the CURRENT stop price to the nearest HELD pool on the protective side between price and stop (a pool protects the stop when it sits between price and stop); NaN if the stop is naked |
| pool_age_* | not provided (tables keep the most recent 4 pools per kind) |
| a_sz5 / a_sz10 / b_sz5 / b_sz10 | 10-level resting size AHEAD of / BEHIND the trade over the first 5 / 10 ticks (ahead = ask side for a long) |
| a_wall_sz / a_wall_tick | largest resting size ahead within 10 ticks and its tick |
| a_wall_drop / a_wall_state | size now vs the max of the last 10 s at the wall tick; state 0 none, 1 held, 2 EATEN (drop >= 50% and trade depletion > cancels over 10 s), 3 PULLED (drop >= 50% and cancels >= trade depletion) |
| a_depl_trd_5 / a_depl_can_5 / b_depl_trd_5 / b_depl_can_5 | sizes removed by trades / by cancels on the ahead / behind side summed over the last 5 s (book flow) |
| b_pulled_5 | behind-side cancels minus trades over 5 s: protecting size being pulled when positive |
| imb5, spread, refill_5 | book imbalance (5 levels), spread in ticks, refill count over 5 s (iceberg sign) |
| stop_vis_sz | resting size within +-1 tick of the stop price if the stop lies within 10 ticks of the touch, else NaN (10-level) |
| mbo_wall_a_dist, mbo_wall_a_sz, mbo_wall_a_state, mbo_size_behind_stop, mbo_cluster_behind_dist | RESERVED for W-DYNX8 (MBO, resting >= 120 s), NaN here |
LIMITS: 10-level depth covers 10 ticks (2.5 pts): walls and protecting size at a stop >= 3 pts away need MBO. Older months: the 1-s table exists for 2023-03..2026-10 (+ext weeks 2026-11) on box1; server C has a partial copy (W-DYNML) at /mnt/l2/l2vast/_dynml/nq/1s. UW intraday walls: 9 recorder days only (13-25 Nov 2026); everything older is static per day.



### 3c. LIVE L3 (MBO) QUANTITIES THE ENGINE NEEDS (order 1414Z item A; Josh accepts a live Databento L3 subscription) - READING of code/th_dynx8/l3_sec.py, dyn_replay.py, th_dynexit/dyn_mbo.py
```
feed            = Databento MBO (mdp3) for the front NQ contract: per record action (A add, C cancel, M modify, T trade, F fill, R clear/snapshot), side (B/A), price, size, order_id, flags (F_SNAPSHOT 32, F_LAST), ts_recv, ts_event, sequence, instrument_id; the day starts with R + snapshot adds (age of snapshot orders counted from the first record = lower bound)
book state kept = hash order_id -> (tick = price/0.25, size, side, insert ts, 'old' flag); per-tick arrays all-size and size resting >= 120 s (promotion queue: an order becomes 'old' 120 s after insert; a MODIFY that changes price or INCREASES size resets age and old flag; reduce-only modify keeps it)
fills/cancels   = CME sends F then C for a filled size: a pull = C size minus the order's fill; trades = T records at price ticks; per-second counters per tick: cancelled size, traded size, added size
per second (SPEC, W-DYNX8 l3sec table, stamp = end of second, records ts_recv < stamp): best bid tick, best ask tick, 5-level depth sums bid/ask, within 10 ticks of the touch: pulls NET of fills, adds, fills per side; bid and ask WALL within 30 pt and within 120 pt behind/ahead of the touch: size (max over a 5-tick window), distance in ticks, share of that window resting >= 120 s
per second (READING, W-DYNA dyn_mbo.py): behind wall and ahead wall relative to the trade (largest size within 160 ticks, >= 30 lots counts): size, old share, distance, cancel/trade/add size at the previous second's wall tick, pulled (drop >= 50 % with trades < 50 % of the drop) / consumed events, iceberg refill (re-add >= 50 % of traded size, >= 20 lots traded)
per trade (W-DYNL mbo_cols): size resting between price and the stop by age (old >= 1 / 3 minutes, all) and the cluster behind the stop (distance, size)
latency         = LAT_BOOK / ts_recv versus engine clock: OPEN (sim.py PRM LAT_BOOK=-1.0); live: use ts_recv of the subscription and an explicit measured lag; replay: records with ts_recv < stamp
capacity        = full-depth MBO for one contract: about 2-3 million records on a busy day (1 GB/day uncompressed zst ~ 65 MB); the book hash needs 2^21 slots; replay speed on one core about 15 s per day file, live is real time
```

OPEN: loop A rule features from the L3 wall channels (behind/ahead wall size, share of size resting >= 120 s, pulled/consumed, refill) are defined in code/th_dynexit/dyn_mbo.py (SPEC for the replay; no attribution passed them, W-DYNA 06:55Z: 0 of 24).

## 4. LOOP A (rule loop) - OPEN: W-DYNC to write the rule list and thresholds BEFORE scoring; copy here as `A.R<k> = condition -> action (reason)`
## 5. LOOP B (score loop) - SPEC for the X24 count machine (section 2 steering and guard rails; fixed_rules_x24.json), OPEN for any change
## 6. LOOP C (learned loop; W-DYNML code/th_dynml/algo_hook_c.py, loopc_trees.py, dml_algo_hookfit.py) - SPEC (read from the code, 15:20Z)
```
model             = LightGBM regressors, one per action (4: take-all, tighten, part, trail), target = advantage over HOLDING, in units of the book's own stop R0 (clipped to +-3 R0), fitted on 1-minute states of past trades
export format     = one bundle per (book, refit step) /mnt/l2/l2vast/_dynml/algo/hook/loopc_<TAG>_s<STEP>.json.gz (json, gzip, a few hundred KB to a few MB):
                    {"tag", "step" (refit weeks 4 or 13), "feats" (18 names, order fixed), "safety_mult" (1.5),
                     "periods": [ {"wk0","wk1","t0","t1" (epoch s of the forward period), "fit_end" (the model saw only trades that ended before it),
                                   "models": [ {"init": 0.0, "trees": [ {"f":[split feature index, -1 = leaf], "t":[threshold], "l":[left child], "r":[right child], "d":[default-left 0/1], "m":[missing type 0 None, 1 Zero, 2 NaN], "v":[leaf value]} ... ]} x4 ] } ... ] }
evaluator         = loopc_trees.py predict_one(trees, x, init): pure python/numpy, no lightgbm: per tree walk from node 0: v = x[f[i]]; NaN -> go left if (m[i]==2 and d[i]) else (0.0 <= t[i]); (m[i]==1 and |v|<=1e-35) -> d[i]; else go left iff v <= t[i]; prediction = init + sum of leaf values; identity-tested against lightgbm (dml_algo_hookfit.py)
model choice      = a trade is managed with the period whose [t0, t1) contains the decision second; after the last period the last model is reused; before the first nothing happens (hold)
features (x, 18)  = openR mfeR maeR sec R0pts hod nq60 nq300 nq900 ES60 ES300 RTY60 RTY300 CL60 CL300 ZN60 ZN300 gap
   openR  = open_pts / R0 (R0 = the book's own stop in pts; the hook holds the safety stop = safety_mult x R0 = 1.5 x R0 and rescales)   mfeR = best open R0 so far   maeR = -|worst open R0 so far|
   sec = seconds in trade   R0pts = R0   hod = ET hour of the decision minute shifted -18 h (Globex day clock; the key minute = entry + int(mins)*60)
   nq60/nq300/nq900 = side * (NQ close_now - NQ close_{60/300/900 s ago}) / R0 ; ES60 ES300 RTY60 RTY300 CL60 CL300 ZN60 ZN300 = side * 1e4 * (close_now / close_then - 1) (basis points) ; gap = ES300 - nq300 in bp
   feeds = instr_1s 1-s bars NQ ES RTY CL ZN, a bar is known at its start + 1 s; LAG 1 s: value = last bar with start + 1 + 1 <= decision second; missing -> NaN (trees route NaN by their default direction); no flow feature in this version
schedule          = decide ONCE per trade-minute: at the first call with int(minutes in trade) > last evaluated minute (minute k = first second with t - entry >= 60 k); minute 0 never
loss-mode gate    = mode 'loss': only when open_pts < 0 (openR < 0); otherwise HOLD without evaluating the model; mode 'joint' evaluates also in profit
decision          = theta = 0.2 R0: the action with the largest predicted advantage > theta that is ALLOWED: tighten only if (open_pts - 0.5*R0) > current stop distance; part only if lots >= 2 and not already parted (frac 0.5); trail only once per trade; ties go to the later action index
actions           = all (market, state OUT), tighten {to: open_pts - 0.5*R0 from entry, state DEFENDING}, part {0.5 of lots, state RUNNING}, trail {distance R0, state RUNNING}; reason string 'LOOP C adv %.2f R (all .. tight .. part .. trail ..) openR ..'
refit schedule    = purged walk-forward refit every 4 weeks (s4) and every 13 weeks (s13); a bundle holds all periods of the history up to the build date; for live a refit adds a period with its own t0 = the refit date
safety stop       = 1.5 x R0 from entry (k_safe 1.5), never widened
one bundle per    = book (cell id): Asia MF1 = Lb0e6dfa3_R0_F40_80; the other books as W-DYNML builds them (index: /mnt/l2/l2vast/_dynml/algo/hook/)
```
Match-test rows for Loop C: /mnt/l2/l2vast/_dynexit/algo_inputs/loopc/<book>_<bundle tag>_s<STEP>.csv: for each dated trade of section 8 and every trade-minute: the 18 features exactly as handed to the trees (column x18, json), openR/best/worst in R0, loss gate, the four predicted advantages pred_all pred_tight pred_part pred_trail, action, rule, reason. Asia MF1 done for its 3 trades (steps 4 and 13); other books as bundles are mapped to books (OPEN: W-DYNML to give the cell id for each book key). Trades after 2026-10-12 (instr_1s end) have NaN feeds for the cross-market columns (same as the engine would see without the feed). Pass criterion: predictions equal to 1e-9, same action at the same minute. OPEN: exact-engine action logs for these trades from W-DYNH, to compare actions with the hook's.

## 7. ORDER HANDLING AND LOG FORMAT
```
orders                 safety stop = stop-market at entry; stop changes = cancel/replace (one order live at a time), market for TAKE_PART/TAKE_ALL/READD; fills 'stop: -0.25 pt slip normal, -1.0 pt pessimistic; market exits next 5-s bar close -/+0.25 pt; fee 4.84 per lot round trip' (X24 quick screen, READING; engine: LAT_FILL 1.0 s, LAT_CANCEL 0.5 s)
change limits          at most one stop change per minute except tighten; widen never beyond the original safety stop; hysteresis 4 ticks on stop moves (dx_dyn.py: hyst ticks, minsec)
log file               one CSV row per manage() call that returns anything other than HOLD, plus one HOLD row every 60 s per open trade
log columns            ts_ns, ts_et, trade_id, book, side, lots_open, state_from, state_to, action, action_px, action_lots, reason, open_pts, open_R, peak_pts, stop_px, score_for, score_against, i1, i2, i3, i4, range_state, n_changes_60s, order_id, order_type, input_hash
input_hash             sha1 of the input row (the exact landscape row used) so a mismatch can be located
```
## 8. MATCH TEST (relay proves trade for trade)
per-second input tables: 57 trades = 3 per book (Asia MF1-4, NY AM MF1-9, London LO_MF1-3, NY PM NP_MF1/3/4), one Target exit, one Stop exit and one other exit (UWTime/EarlyCut/PolicyTake...) per book, the median-dated trade of each class in Aug-Oct 2026 lasting 3-40 min, in /mnt/l2/l2vast/_dynexit/algo_inputs/ on server C (MANIFEST.csv: book, session, trade_id, date, side, lots, entry_ns/px, exit_ns/px, exit_name, S0, T0, minutes, rows, file). Each file = one row per second from entry-3900 s to exit+10 s (the 3600 s warm-up makes every rolling window complete at entry), columns: ts_ns (second label of tables/NQ/1s), the NQ tape/flow/book fields of section 3 (trd_px_last/hi/lo, trd_vol, buy_vol, sell_vol, big1_*, swp_*, ofi1, ofi5, imb1/5/10, spread_t, bid_px, ask_px, mid, micro, bsz1-3, asz1-3, sz_add/can b1 a1, refill_n, depl_*), es_last, rty_last (ffilled), then the box's SPEC features i1_delta, i2_ofi, i3_book, i4_mom, range_ratio, range_state, for_n, against_n, score, open_pts, in_trade (1 between entry and exit), and `expected_state`, `expected_action`, `expected_reason` (EMPTY until the box reference implementation of W-DYNC/W-DYNH exists: OPEN). POOLS TABLES (W-DYNL, SPEC for pool/10-level/cross-market columns, mbo_* NaN until W-DYNX8): /mnt/l2/l2vast/_dynexit/algo_inputs/pools/<same stem>.pools.csv.gz, one row per second from the entry second to the exit, 106 columns (ts = second grid ns, k = seconds since entry; pools, sweep-reclaim, stop clearance, 10-level, cross-market ES/RTY/CL/ZN); stop = entry_px - side*S0 (k_safe 1.0); six trades ready (AS_MF1 20260930_030006_Stop, 20261013_054003_UWTime, 20261023_003203_Target; NY_MF5 20260921_140347_Stop, 20260923_140207_Target, 20260928_154038_UWTime), the rest of the manifest building (log algo_inputs/pools_build.log). Lag: features available at bucket start + 1 s + 1 s feed lag; order lag = engine LAT_FILL 1.0 s / LAT_CANCEL 0.5 s. Caveat: instr_1s ends 2026-10-12 (CL, ZN) / 10-16 (ES, RTY): later trades have NaN there. Missing-second convention: volumes and ofi = 0, prices and book fields forward-filled. Pass criterion: for every second the NT8 strategy's (state, action, reason) equals expected; stop/target/market fills within the engine's latency rules; tolerance on prices 0 ticks, on feature floats 1e-6.
## 9. OPEN LIST (owner)
```
loop A rule list and thresholds                    W-DYNC
loop C model and inference spec                    W-DYNML
engine hook equality (manage() at 1 s == screen)    W-DYNH
input lags for ES/RTY/UW/L3 in the live feed        W-DYNX8 + relay
other instruments (YM, ZN, ZB, crude, NKD, 6J) and stocks   W-DYNOF
safety stop multiple k_safe                         replay (W-DYNC)
```
