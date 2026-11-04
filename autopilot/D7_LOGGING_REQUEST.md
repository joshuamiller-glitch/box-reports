# D7_LOGGING_REQUEST - one consolidated logging request for the platform owner (DIS-AP, CAL, 2026-11-04)
For the user to forward. Documentation only: no code was changed, nothing is live, no PASS claims. Scope note l2vast/ds3/prereg/DISAP_scope.md sha256 4036209bd6d833d324b73bec927225594a82c5e3af0fee375b10acbbe4ab6abe (DECISIONS.md, logged before this request was written). **All example rows are illustrative, not real data. Implementation costs are guesses by the research side, not estimates by the platform owner.**

## 0. Summary
Today the research folder has NO fill-level, signal-level or stop-level live file (DS3_LIVE_RECON.md could only use a 61-trade aggregated table; the STOP A/B has n = 0 per arm; LIVE_MONITOR_SPEC.md prints NO DATA for all 38 metrics on today's registers). Everything requested across the work reduces to **5 minimum files + 3 optional + 2 deferred**. Every counterfactual (shadow exits, what a cut would have done, extra trades, slice VWAP, refill outcomes of skipped signals) is computed offline from these inputs plus the already approved weekly 1-s tape; the platform logs inputs and events, never counterfactual outcomes.

| rank | file | decision value (a) | implementation cost, GUESS (b) | set |
|--|--|--|--|--|
| 1 | `fills.csv` | very high: live-vs-model $/wk, STOP A/B (model worth ~$3.1k/wk across six books), fees vs FEES.md, entry/target slippage | medium (NT8 execution export + order-type tag) | **MIN** |
| 2 | `signals.csv` | very high: pairs every engine signal with the box (taken / skipped / lots), Q1-A sizer audit, Shadow rule scoring R1-R9 | medium (the planned D6 v2.4 log writer) | **MIN** |
| 3 | `d6_stops.csv` | high: stop trigger time, true stop level, run-past-stop and join placement for the A/B | low-medium (a few fields per stop) | **MIN** |
| 4 | `th_cuts.csv` | high: TH-L2 is the swing factor of the stack (break-even 77.5%, 2025 -262k vs 2026 +201k on cut rows) | low-medium (one row when the rule fires) | **MIN** |
| 5 | `control_pnl.csv` | medium-high as an integrity check (a trade was missing from the platform CSV once, JOIN_RECON 0.5) | low (end-of-day totals) | **MIN** |
| 6 | `bars_1min.csv` NQ + ES | medium: regime monitor (4 of 9 metrics), ES-lead rule R8; NQ is covered by the approved weekly feed from 2026-11-07, ES is not | low | optional |
| 7 | `rf_1min.csv` | low-medium: unlocks one of five Shadow2 lines (DIS_E) | high (needs the L2 book events) | optional |
| 8 | `pe45_bars.csv` (R1 only) | low: one Shadow rule | medium | optional, only if R1 is kept |
| - | L2 forward log (`l2_flow_1s`, `l2_ladder_10s`, `l2_intrade_10s`) | low: every ranked L2 exit cluster is DEAD or LEAD-at-best | high, about 11+ MB/day | DEFERRED (L2_FORWARD_LOG_SPEC.md stays on file) |
| - | `lots.csv` | - | - | DROPPED (folded into `signals.csv`) |

**MINIMUM SET = fills.csv, signals.csv, d6_stops.csv, th_cuts.csv, control_pnl.csv.** With these the research can answer: does the box do what the engine does (and where not, in dollars), is native or join stop better, is TH-L2 above its break-even, and is the Q1-A sizer as simulated. Already specified and unchanged (written by the shadow code on the box, not part of this request): the Shadow registers `forward_register/{bt, nyam, fade, shadow2, sizer_shadow}/` (SHADOW_PACK.md, SHADOW_PACK_2.md, NYAM_SHADOW_SPEC.md, FADE_SHADOW_SPEC.md, BT_SHADOW_D7_V14_SPEC.md).

## 1. Conventions for every file (resolves the conflicts in section 4)
- UTF-8, comma-separated, LF, header row, one file per ET trading day `YYYYMMDD` (`fills_20261104.csv`) in `incoming/`, never rewritten after the day closes (append-only inside the day, fail-open); a column is added at the END only, with `schema_ver` bumped. Rotation: keep 90 days on the box, the research side archives.
- Times: `*_ms` = epoch milliseconds UTC, integer; `trade_date` and `label_day` = integer `YYYYMMDD`, `trade_date` = ET date of (ts + 6 h) (the exchange trade date; Sunday 18:00 ET belongs to Monday), `label_day` = same as `trade_date` except that weekend dates roll to Monday. No local-time strings.
- Prices in points of the raw front contract (not back-adjusted), tick 0.25; money in USD; lots = integer contracts (paper books may be fractional in the shadow registers only).
- `side` = +1 long / -1 short for a TRADE (signals, stops, cuts); `fills.csv` side = direction of the FILL (+1 buy, -1 sell). `BUY/SELL` text is accepted on input only.
- `signal_id` = `book|epoch_ms|side` (D6 book tag K6 P6 U6 H6 M6 A6 O6 S6 W6 MA6 C6; epoch_ms of the signal second t0). `trade_id` in fills.csv is the same string.
- Null rule: blank = not applicable or not computable (never 0, never a placeholder); a reason goes in the `*_null_reason` field where one exists. Booleans 0/1.
- Privacy: no account, login, token, key, order id, or free text anywhere; strategy/book tags and prices only. Fill-level rows are needed (slice VWAP and tick-level slippage cannot be recovered from aggregates), so the files stay in the private `incoming/` folder; only aggregated tables are written into research pages.

## 2. The minimum set
### 2.1 `fills.csv` (one row per executed fill slice or order event)
| column | type / unit | null rule | note |
|--|--|--|--|
| trade_id | str | required | = signal_id of signals.csv |
| book | str | required | D6 tag |
| side | int +1/-1 | required | direction of the fill |
| qty | int contracts | 0 only for a join placed, not filled; blank only if reject=1 | |
| price | float pts | blank if reject=1 or qty=0 | |
| time_ms | int epoch ms UTC | required | fill time (join / reject rows: time of the order event) |
| order_type | enum | required | `entry_market, entry_limit, add, target, stop_native, stop_join, stop_fallback, flatten, cut, time_exit, other` (`time_exit` added: the 60-min / session time exits that DS3_LIVE_RECON.md could not separate) |
| fee_usd | float | optional | total fee for the row, all-in; if absent the research uses FEES.md (0.242 pt per lot per fill) |
| reject | 0/1 | optional | rejected orders are their own outcome |
| slice_seq | int | optional | 1..n for the 1-lot / 2-s entry schedule (lets slice VWAP be rebuilt) |
| schema_ver | str | required | `d7log_v1` |
Written: at each fill, flushed per order event. Example: `K6|1793574060000|1,K6,1,1,29861.25,1793574061000,entry_market,2.42,0,1,d7log_v1` (illustrative).
Used by: LIVE_RECON (model-minus-live $/wk with block bootstrap), stop slippage and join fill rate, target fill, entry slippage vs L2 mid, fees vs FEES.md, STOP A/B tables, the Shadow scorers. Unlocks: the native vs join stop decision, the fee assumption (FEES.md flags NQ exchange fees as a proxy), and whether the engine's $/wk is what the box earns.
### 2.2 `signals.csv` (one row per signal of every book, taken or not; paper books as paper rows)
Canonical columns (a subset of the 95-field `shadow_log_schema.csv` / D6_LOG_WRITER_SPEC.md writer, plus the sizer fields of SHADOW_PACK.md):
`signal_id, ts_signal_ms, trade_date, label_day, book, session, side, signal_px, stop_d, tgt_d, lots_live, lots_l1, q1a_mult, zone_half, lots_final, taken, blocked_by, er20_5m, l2_mid_at_signal, live_config_ver, schema_ver`.
Definitions: `lots_live` = the D6 session-table lots (K6 2, P6 7, U6 4, H6 4 Asia / 2 NY-AM, M6 2, A6 1; 0 outside the table = logged with taken=0, blocked_by=session_off); `lots_l1` = lots after the A06/B02 flags (one rounding); `q1a_mult` = the ER Q1-A multiplier applied (0.5 if er20_5m < 0.30 else 1.0); `zone_half` = 1 if the zone HALF applied last; `lots_final` = contracts the strategy submitted for the trade (entry + add legs; the divisor of per-lot P&L); `er20_5m` = Kaufman ER of the last 21 closed epoch-aligned 5-min closes at t0 (bar_end <= t0), blank with a reason when not computable; `l2_mid_at_signal` = book mid at t0 (blank if no L2); `blocked_by` in {session_off, lock, overlap, block_window, other}; taken 0/1.
Written: at t0, one row per signal, flushed immediately (outcome columns are NOT written; they come from fills). Example: `K6|1793574060000|1,1793574060000,20261103,20261103,K6,nyam,1,29861.25,60,60,2,2,0.5,0,1,1,,0.31,29861.125,d7_v2.4,d7log_v1`.
Used by: pairing engine signals to box signals by (book, ts) for the "engine took but box skipped, or vice versa" row; Q1-A sizer audit (ER share <0.30, lots by book); entry slippage reference; Shadow rules R2-R9 (the rule-specific state columns of shadow_log_schema.csv are added only for the rules the user keeps); sizer-shadow would-be lines. Unlocks: whether the sizer and the box do what the engine simulates, which Shadow rules can be scored forward.
### 2.3 `d6_stops.csv` (one row per stop event)
`signal_id, ts_trigger_ms, stop_level, run_past_stop_pts, join_placed_ms, join_px, join_rejected, arm, schema_ver`.
`ts_trigger_ms` = the second the stop price traded; `stop_level` = the real stop (not the nominal 60); `run_past_stop_pts` = pts the last print was already beyond the stop at order placement (blank if native); `join_placed_ms/join_px` blank for native stops; `arm` = A (native, odd trade_date) or B (join, even trade_date) as the box applied it, so a deviation is visible (the joiner recomputes the intended arm). Written at stop trigger. Example: `P6|1793660400000|-1,1793664000000,29944.25,1.50,1793664000150,29944.00,0,B,d7log_v1`.
Used by: stops.csv (derived by fills_join.py), run-past-stop, join placement latency, the A/B tables. Unlocks: native vs join (n ~ 200 per arm; reviews at 30 / 60 / 120 per arm).
### 2.4 `th_cuts.csv` (one row per TH-L2 cut event; inputs and the event only)
`signal_id, book, side, lots, armed_ts_ms, arm_level_px, adverse_extreme_px, cut_trigger_ts_ms, pulled_own_10s, med_own_level, rule_params, schema_ver`.
`armed_ts_ms` = first time the trade reached the -30 pt arm; `adverse_extreme_px` = worst price at the trigger; `pulled_own_10s` / `med_own_level` = the two L2 inputs of the rule at the trigger (own-side size pulled in the last 10 s, median own-side level size), `rule_params` = `A30|k30|10s|medlvl`. The cut FILL itself is the `order_type=cut` row in fills.csv (price, qty, time); the 60-minute would-be outcome (STOP / TARGET / FLAT / OPEN), the per-cut value, the extra trades after a cut and the capacity effect are **derived offline** from fills + signals + the 1-s tape (this resolves the conflict with LIVE_MONITOR_SPEC.md, section 4). Written: at the cut trigger. Example: `P6|1793700000000|-1,P6,-1,7,1793697000000,29900.00,29931.25,1793700000000,4200,1300,A30|k30|10s|medlvl,d7log_v1`.
Used by: TH1-TH4 of the monitor (share of cuts on would-be stops vs the 0.775 break-even, cuts per week, extra trades, per-cut value), DS3_TH_MECHANISM.md follow-ups, ZL-2's TH out-of-sample work. Unlocks: whether to keep, retune or drop the cut (the cut is a near zero-sum bet per cut; 2025 cut rows -262k, 2026 +201k, PE 7 lots).
### 2.5 `control_pnl.csv` (end-of-day control totals from the platform's own P&L, one row per book per trade_date)
`trade_date, book, realised_usd_net, fees_usd, round_trips, open_contracts_at_eod, schema_ver`. Aggregated; no account id. Written once after the 16:55 ET flat / session close. Example: `20261103,P6,-2840.00,96.80,6,0,d7log_v1`.
Used by: tie-out of fills.csv (sum of joined round trips must equal `realised_usd_net`, within fees), weekly P&L and the concentration / drawdown metrics (C1-C5 of the monitor, derived from this when fills are not yet clean), detection of missing trades. Unlocks: trust in everything above (the platform strategy CSV once missed an ST trade of about -$17.7k).

## 3. Optional and deferred
### 3.1 `bars_1min.csv` (optional; NQ now covered by the approved weekly ohlcv-1s feed from 2026-11-07, ES is not)
`ts_ms` (bar start), `symbol` (NQ / ES, raw front contract), `open, high, low, close, volume`. Closed 1-min bars only, daily file, append-only. Used by: regime monitor R4-R7 (10-11h lag-1 autocorrelation, first-hour range share, NQ/ES vol ratio, gap-fill rate), nyam_regime_monthly (RTH bars), ES-lead rule R8 (feed age). Unlocks: the monthly regime read and the NQ-vs-ES series without a second data purchase. Ask only if the user does not extend the weekly feed to ES.
### 3.2 `rf_1min.csv` (optional, DIS_E only)
`ts_minute_ms, rf, n_touch_clears, ob_live, schema_ver`: `rf` = count of refill-failure events completed in the minute (a trade-driven touch clear whose book did not heal to <= the pre-clear spread and >= 50% of the pre-clear touch within 60 s, l2vast/TABLES.md); `ob_live` 0/1. Needs D7's own book events; the first weeks need an overlap day with the table RF for comparison (SHADOW_PACK_2 section 7). Unlocks the DIS_E Shadow2 line only; the other four lines need only trade prints.
### 3.3 `pe45_bars.csv` (optional, only if the PE 45-s three-bar rule R1 is kept)
`signal_id, seq, bar_end_ms, open, high, low, close, volume`: 26 bars before t0 and every 45-s bar to the live exit (FORWARD_SHADOW_SPEC section 1, R1).
### 3.4 Not requested
Out-of-RTH Shadow lines (DIS-B 08:35 ET, DIS-C Sunday 18:30 ET): no new file; the Shadow2 register logs the would-be signals and the weekly tape replays them. Raw MBO, queue position at target/stop, wall_tgt / wall_stop: not requested (mbp-10 sees about 2.5 points, no ranked cluster uses them). The L2 forward log of L2_FORWARD_LOG_SPEC.md: deferred (all ranked L2 exit clusters are DEAD or LEAD at best; revisit if TH-L2 is kept and a variant needs more than the two inputs in th_cuts.csv). `lots.csv`: folded into signals.csv. `weekly_pnl.csv`: derived from fills.csv, with control_pnl.csv as the check. `stops.csv`: derived by fills_join.py.

## 4. Conflicts found and how they are resolved
| # | same thing defined two ways | where | resolution (canonical) |
|--|--|--|--|
| 1 | signal id: `book|epoch_ms|side` (live) vs `<LINE>_<book>_<signal_sec>` / `<LINE>_<signal_sec>` (Shadow registers) | FILLS_CSV_SCHEMA vs SHADOW_PACK / SHADOW_PACK_2 | live files: `book|epoch_ms|side`; Shadow registers keep their line-prefixed ids in their own folders (a different namespace, join by book and signal second only when needed) |
| 2 | event time: ISO UTC strings (`ts_signal_utc`, `ts_exit_utc`) vs epoch ms | Shadow registers vs D6 / fills specs | new files use epoch ms UTC only; the two ISO columns of the registers are legacy and parsed as is |
| 3 | ER field: `er20_5m` (D6 schema, FORWARD_SHADOW_SPEC) vs `er_5m_20` (research feature, LIVE_MONITOR_SPEC S1 reader) | | canonical `er20_5m`; the monitor reader must also accept the alias (one-line change, NOT made now) |
| 4 | lots: `lots_live` = session-table lots (shadow_log_schema) vs the divisor "planned lots" of the joiner (FILLS_CSV_SCHEMA) vs `lots_l1/lots_actual` (SHADOW_PACK) vs `session_lots/ladder_mult/lots_final` (LIVE_MONITOR lots.csv) | | log all four levels in signals.csv: `lots_live` (table), `lots_l1` (A06/B02), `q1a_mult`, `zone_half`, `lots_final` (submitted). Per-lot P&L must divide by `lots_final`; the joiner currently divides by the column it calls lots_live, so after the ER ladder (live since 2026-11-02 19:30Z) it must be pointed at lots_final (documented, joiner NOT changed now). `lots_actual` of SHADOW_PACK is renamed `lots_final` |
| 5 | stop slippage sign: `side*(stop_level - fill)` + adverse (FILLS / monitor E2) vs "exit vs nominal" + better (LIVE_RECON.md and DS3_LIVE_RECON.md tables) | | canonical + = adverse; the two older tables are sign-reversed and are labelled so |
| 6 | arm day boundary: "exchange trade date" (FORWARD_STOP_AB) vs "ET clock + 6 h" (FILLS) | | same quantity; `trade_date` defined above, odd date = A native, even = B join |
| 7 | `th_cuts.csv` with shadow outcome fields written by the strategy (LIVE_MONITOR_SPEC) vs "log inputs, counterfactuals offline" (D6_LOG_WRITER_SPEC section 0) | | inputs-only (section 2.4); the monitor's TH reader should compute value / outcome from tape; LIVE_MONITOR_SPEC table to be updated when this request is accepted |
| 8 | `stops.csv` listed as a platform file (monitor) vs derived by fills_join.py (FILLS_CSV_SCHEMA) | | platform writes only `d6_stops.csv`; stops.csv stays derived |
| 9 | `weekly_pnl.csv` (monitor) vs derivable from fills | | derive; request only `control_pnl.csv` |
| 10 | `lots.csv` (monitor) vs the lots fields of signals.csv | | dropped |
| 11 | file name collision `<LINE>_fills.csv` (Shadow registers) vs `fills.csv` (live) | | different folders (`forward_register/shadow2/`, `sizer_shadow/` vs `forward_register/live/incoming/`); never merged |
| 12 | fee: per-row `fee_usd` vs constant 0.242 pt per lot-fill (FEES.md) | | `fee_usd` optional; if logged, it overrides the constant and is compared with FEES.md as a check |

## 5. Decisions for the user (not for the research side)
1. Approve the 5-file minimum set (the 5 are all inputs the box already has; section 0 costs are research-side guesses).
2. ES data: either extend the approved weekly 1-s feed to ES (a purchase, the same order of cost as the NQ feed) or ask for `bars_1min.csv` ES from the platform; without either, R4-R7 and R8 stay NO DATA.
3. Keep or drop the optional RF (DIS_E), PE45 (R1) and L2 logs: they unlock one Shadow line each at the highest cost.
4. If accepted: tell the research side the delivery folder and cadence; the joiner and the monitor will be pointed at it (those code changes are outside this document).
