# ALGO inputs: pools / walls / book liquidity per second (W-DYNL; for ALGO_SPEC.md inputs table via W-DYNA; library owner for MBO and 10-level book features = W-DYNX8)
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
