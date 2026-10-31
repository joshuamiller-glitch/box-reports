# D6_LOG_WRITER_SPEC - how D6 writes the SH-2 shadow log (worker D6S, 2026-10-31)

Reference code: `l2vast/ds3/code/shadow/d6_state.py` (pure numpy/pandas, no research imports, liftable) and its test `test_d6_state.py` (research comparison, prints the table in section 5). Field names equal `shadow_log_schema.csv`. No data after 2026-02-06 was used for results (ES to 2026-01-30). No credentials or account ids anywhere. Everything below is a log rule: the shadow path never touches orders, lots, stops, targets, locks or governors.

## 0. Rules that apply to every field
* **Clock.** t0 = the second the book's signal fires. State uses data stamped <= t0 (the ES-lead rule uses <= t0-1 s, see 1.4). `ts_eval_ms` <= t0+1000. Closed bars only. **Closed-bar rule differs by variable and matters:** ER 5-min bar closed iff `bar_end <= t0` (inclusive; a strict `<` changes ER for the 20.8% of signals that fire exactly on a 5-min boundary: only 79.3% of ER values then match). 45-s / 15-m / 1-h / 4-h line and pattern logic: closed iff `bar_end <= t0+1 s` (research "known second" = first print with second >= bar_end-1).
* **Bars** are epoch aligned and exist only if they had a print (never synthesise filler bars): 5m, 15m, 1h, 45s on epoch multiples; 4h and 1d anchored at the CME day (18:00 ET, follows DST); bar_end = exclusive end. The resampler in `d6_state.resample_epoch_bars` reproduces the research 5m/15m/1h/4h/1d bars exactly (section 5). Prices are the front-contract's own (not back-adjusted).
* **Null rule.** A state D6 cannot compute is written blank (empty string) with the reason in the `*_null_reason` field where one exists, else in the D6 error log; never 0, never "no fire". A rule field never filled by a failed computation (e.g. `zone_fire20`) must be blank, not 0.
* **Isolation (spec section 4).** Read-only (no order/position calls), evaluated after the live decision or on a separate thread, exceptions caught and fail-open (row written with blanks + `blocked_by` untouched), append-only buffered writes, disabled itself if p99 evaluation > 50 ms. All state below is O(1)-O(100) ops on rings D6 already holds; line touches are updated incrementally on each trade print, not by rescanning.
* Units: points (NQ 0.25 tick), epoch ms UTC for `*_ms`/`*_ts`, lots integer unless paper.

## 1. Table `signals`
### 1.1 Identity and book state (not shadow state; owner = D6 order logic)
| field | source in D6 | formula / units | null / timing |
|---|---|---|---|
| signal_id | book, t0, side | `book|t0_ms|side`, unique | never blank; one row for EVERY signal incl. not taken |
| ts_signal_ms, ts_eval_ms, trade_date, session, side | signal clock; ET clock; side +1/-1 | trade_date = ET date +6h; session by ET entry clock (schema list) | ts_eval_ms <= ts_signal_ms+1000 |
| book | D6 tag K6 P6 U6 H6 S6 W6 (MA6 CR M6 A6 O6) | | |
| signal_px | the price the book would enter at (planned entry price E) | pts | use E, not a later print: with last print at t0 instead of E the zone flag disagrees on 0.7% of signals (E vs last print: median 0.5 pt, p99 8.25 pt) |
| stop_d, tgt_d, lots_live, lots_research, lots_stack, taken, blocked_by, live_entry_mode, live_config_ver | live config | pts / lots; lots_stack = lots_live if >0 else lots_research/2.35 | blank only if the book config is unreadable; `synthetic` blank on real rows |

### 1.2 R2/R3 ER sizer (`d6_state.er_at`, `er_multiplier`, `hyp_lots`)
| field | source | formula | null rule |
|---|---|---|---|
| er20_5m | ring of the last 21 CLOSED 5m closes | Kaufman ER = abs(c[t]-c[t-20]) / sum_{i=t-19..t} abs(c[i]-c[i-1]); den 0 -> 0.0 | blank if < 21 closed bars or any close missing; reason in er_null_reason (`fewer_than_21_closed_5m_bars`, `nan_close`). No staleness rule exists in research (bar age median 120 s, up to the weekend gap): log er_bar_end_ts and do not null on age |
| er_bar_end_ts | bar_end of the newest of the 21 bars | epoch ms (= k*300000), bar_end <= t0 | blank with er20_5m |
| er_closes | the 21 closes, oldest first | ';' joined, `%.2f` (ticks 0.25 are exact) | blank with er20_5m |
| er_null_reason | | text | blank when ER present |
| er_mult_kb / er_mult_oth | er20_5m, book | K6: 1.5 if ER>=0.20 else 0.5 -> er_mult_kb (er_mult_oth blank). All other books: 1.5 if ER>=0.30 else 0.5 -> er_mult_oth (er_mult_kb blank) | blank if ER blank |
| hyp_lots_er | lots_live, mult | integer lots. **Open question 5 (rounding) is a parameter**: `half_up` = floor(x+0.5): K6 2->3/1, P6 7->11/4, U6 4->6/2, H6 2->3/1, H6 4->6/2; `floor1` = max(1,floor(x)): P6 7->10/3, others identical. Paper books (lots_live 0): research/2.35 unrounded | blank if lots_live = 0 and not paper, or ER blank. Record the rule used in live_config_ver |

### 1.3 R4 8-line zone (`kijun_1h`, `keltner_upper`, `crt_mid`, `prior_day_mid`, `cam_h3_rth`, `ote_lines_15m`, `make_line_records`, `zone_state`)
Lines (research stream names are used as `name` in zone_lines): `PDX|day|M` previous Globex day (18:00-18:00 ET) (H+L)/2 | `MAS|ich_kijun|1h` (max high of last **26** closed 1h bars + min low of same 26)/2 (not 52) | `MAS|kc_up|4h` EMA(close,span 20, adjust=False) + **2.0 x SMA(true range,10)** of closed 4h bars (see change request C4) | `CRT|M|4h` (H+L)/2 of the last closed 4h bar | `PIV|cam_H3|rth` C + 1.1(H-L)/4 of the previous RTH session 09:30:00-16:00:00 ET (H,L,C = high, low, last trade) | `FIB|ote62_up|15m`, `ote705_up|15m`, `ote79_up|15m` = L3 + r(H3-L3), r = 0.62/0.705/0.79, H3 = max of last 3 confirmed 15m fractal-2/2 swing highs (strict >, confirmed when bar j+2 closes), L3 = min of last 3 swing lows, valid only if H3-L3 >= 4.0; the row is replaced at the next swing confirmation of either kind (valid or not).
Each line is a record `px, formed_s, cap_s, touched_s`: formed_s = first print second >= bar_end-1 (RTH line: first print after the RTH close); cap_s = formed_s of the replacing row (inf while in force); touched_s = first second after formed_s whose [low, high] contains px, inf = fresh. **A line touched in the signal second itself is not fresh.** Touch state is updated per trade print and persisted (restart must not make touched lines fresh).
| field | formula | null rule |
|---|---|---|
| zone_file_ver | hash of (line names, parameters above, file build id) | blank only if the lines file is unreadable |
| zone_lines | for every ACTIVE line (formed_s <= t0 < cap_s) with 0 <= side*(px-signal_px) <= 60: `name:px:fresh`, ';' joined; touched lines are included with fresh=0 | empty string = file readable, no line within 60 (legit); blank = file stale/unreadable + D6 log reason |
| zone_fire20 | 1 iff some FRESH active line has 0 <= side*(px-signal_px) <= min(20, tgt_d) (dist 0 = line at the entry price counts) | blank (not 0) if the file is unreadable or any of the 8 builders is warming up (< 26 1h bars, < ~100 4h bars for the EMA seed, < ~200 15m bars) |

### 1.4 R8 ES-lead (paper; `minute_bars_from_seconds`, `atr14`, `atr_before`, `last_px_at`, `eslead_lag_z`, `eslead_mult`)
Convention (matches the research feature to 1e-6): **t_end = t0-1 s** (last COMPLETED second before the signal second), w = 30 s.
| field | formula | null rule |
|---|---|---|
| es_px_t0 / nq_px_t0 | last trade stamped <= t0-1 s | blank if no print within 300 s, or ES contract differs between the two ends (roll) |
| es_px_tm30 / nq_px_tm30 | last trade stamped <= t0-31 s (needs a 1-s last-trade ring of >= 60 s per instrument; 1-min bars are NOT enough) | same |
| es_atr14_1m / nq_atr14_1m | simple mean of true range of the last 14 COMPLETED 1-min bars strictly before the minute containing t0-1; bars built from the **1-s last-price series** (research basis; tick H/L gives NQ ATR a median 9% larger, which flips the 1.5/0.5/1 class on 2.4% of signals); TR uses the previous close only if same contract | blank if < 14 bars or newest bar older than 120 min |
| es_feed_age_ms | age at t0-1 of the last ES TRADE print. 83.8% of historical signals have age <= 1 s, 95.3% <= 5 s, research tolerated <= 300 s: a flat ">1 s = untrusted" rule would flag ~16% of rows that are just quiet markets (see C6) | never blank when ES connected |
| eslead_lag_z | lag_z = es_z - nq_z, z = side*(px_t0-px_tm30)/(ATR14*sqrt(30/60)) | blank if any input blank |
| eslead_mult | 1.5 if lag_z >= 0.5, 0.5 if <= -0.5, else 1.0 | blank if lag_z blank (research would use x1; the log must not) |
"Forming ES bar" in the ESL report means only the 1-min *modes* (M1f = price at the decision second minus the close of the second-to-last completed bar); the scored 30-s rule needs no forming bar, it needs 1-s resolution prices at t0-1 and t0-31.

### 1.5 R1 PE45 summary fields (P6 only; `pe45_events`, `pe45_first_event_after`, `pe45_active_at`, `round_limit`)
| field | formula | null rule |
|---|---|---|
| pe45_event_ts | bar_end_ms of the first THREE_BAR_REV event in the signal direction whose known second (bar_end-1 s) is > t0, evaluated at 45-s bar closes until live exit (cap 40 min) | blank if none before the hold ends (legit "no event"); blank + D6 reason if the 45-s ring was invalid |
| pe45_limit_px | `round_limit((o+c)/2, side)`: tick grid toward the market (buy rounds up, sell down). Research fills at the unrounded mid | with pe45_event_ts |
| pe45_bars_n | rows written to pe45_bars for this signal | |
| other rules' fields | `prev_book_*`, `second_fire30` (R6, lead pins down), `hmfvg_*` (R9, default `hmfvg_enabled=0`, rest blank), `live_close_ts, live_exit_type, live_pts_ppl` (joined after close from real fills, blank until closed or if taken=0) | not part of this worker |

## 2. Table `pe45_bars` (P6 signals)
| field | rule |
|---|---|
| signal_id, seq | seq 0..n-1 chronological |
| bar_end_ms | k*45000, exclusive end. Research stores the bar by t1 = bar_end and knows it at the first print >= bar_end-1 s (56.4% of bars exactly at bar_end-1, 36.8% 0-5 s later, 6.8% later) |
| o, h, l, c, v | OHLC of the prints in [bar_end-45 s, bar_end); v = contracts; bars with no prints are absent (do not write filler) |
| rows to write | **at least 26 closed bars ending at or before t0+1 s** (schema says 3: with 3 bars the active-pattern answer matches only 81% of signals, 85% without the 10-bar guard; the first-event-after answer is 81% with the guard and 99.99% without it) + the forming-bar extremes (change request C2) + every closed bar after t0 until live exit or the 16:55 ET flatten (NO 40-min cap: lead finding, a cap changes 10% of PE replay results) |
Why 26: the research also treats a same-direction pattern completed up to 600 s before t0 and not yet back to its body mid as active at the signal (19.1% of signals). The oldest such event bar is 13 bars before the last closed bar L; it needs 2 earlier bars for the pattern and the research rolling-median guard needs >= 10 bars before it: bars L-23..L = **24 minimum** with the research guards (test: 99.87% active-set match at 24 and at 26, the residual 0.11% is a touch in the very second the pattern becomes known which the research excludes). If the scorer relaxes the guard to min_prior=2, **16 bars** suffice (99.86%); to find only the first event after t0 with the research guard, 10 bars are enough (100%). Log 26 (24 + 2 margin).
Event definition `pe45_events`: long = bar[-2] and bar[-1] closed down (c<o), last bar closed up (c>o) and c > High[-1]; short mirrored. `_strict` adds c[-1] < c[-2] (long) / > (short). Guards: each of the two gaps between consecutive bar completions among the 3 bars <= 4 bar lengths (180 s) - using bar_end, last-print or the research completion second gives the identical event set on all 89,464 / 78,412 events; rolling-median validity = >= 10 earlier bars in the series.

## 3. Table `stack_events` (R5; the lead pins the state, D6 writes it)
| field | source | rule |
|---|---|---|
| event_id, ts_stop_ms, stopped_signal_id, stopped_book, side | the stop fill of any live trade | one row for EVERY first-stop event of an episode, any session; ts = fill second |
| stopped_entry_session | ET session of the stopped trade's ENTRY | asia = 18:00-02:00 ET |
| first_stop | 1 if first same-side stop since the side was last flat | reset when the side is flat |
| books_same / books_opp | other open books same / opposite side at the stop second | `book:signal_id:lots:entry_px` ';' joined; empty string if none |
| hyp_action | `cut50` iff first_stop=1 and stopped_entry_session=asia and books_same non-empty else `none` | never blank |

## 4. Table `stops` (R7 execution A/B; per FORWARD_STOP_AB.md)
| field | source | rule |
|---|---|---|
| stop_id, signal_id, ts_trigger_ms, book, session | the live stop order | one row per live stop |
| arm_assigned | exchange trade date parity: odd = A (Native), even = B (JoinThenMarket 3 s), from 2026-11-02 | |
| order_type_actual | what was really sent (`native`/`join`); a mismatch is a reported deviation | |
| stop_level, lots, fill_vwap, slip_pts | real stop level; lots; VWAP of all slices; signed adverse distance of fill_vwap from stop_level | |
| join_placed_ms, join_filled, join_rejected, fallback_ms, fallback_fill_px | B only | rejected is its own outcome, never folded into not-filled; blank for A |
| run_past_stop_pts | last print vs stop level at the trigger second | |

## 5. Test match table (`python3 test_d6_state.py`, 68 s, one process)
| state | test against research | n | result |
|---|---|---|---|
| ER(20) | store `5m.er20` at the entry second of every trade (join: store row i = universe row i = tid-sorted sim_ok trade i, `entry_ts == s_in`, checked) | 42,954 (signals to 2026-01-19; see note) | **100.00% within 1e-6, max abs diff 3e-8 (float32 store)**; bar end = research last 1-min member close or k*300 gives identical results |
| ER(20) | same, closes from the tape-built (roll-adjusted path frame) 5m bars | 44,370 | 93.70% within 1e-6, max 0.15: all 6.3% differences are tape-frame vs raw front-contract closes on roll days (51% in Mar/Jun/Sep/Dec, rest isolated 0.25-1.75 pt close differences). D6 must use raw front-contract chart closes (= store) |
| ER(20) | den 0 | | research gives NaN (never occurs in 44,370); spec = 0.0 |
| bars | resample 1m->5m/15m/1h/4h/1d vs research bars | 212k/71k/17.7k/4.6k/773 | 100.00%, 99.999%, 99.994%, 100%, 100% (the misses are the final bucket at the cut) |
| 8 lines | each builder vs research stream (px and formed second) | 773 / 17,644 / 4,589 / 4,608 / 772 / 18,441 x3 | 100% rows reproduced, cap time 100% |
| zone_fire | D6 builders + tape touches vs research any-of-8 fresh-ahead, D = 10/15/20/30 | 44,370 | **100.000% agree (0 disagreements), fire rates 6.9% / 11.2% / 15.1% / 21.5%** |
| zone_fire | scorer `zone_recompute(zone_lines)` vs D6 flag | 6,000 | 0 mismatches |
| PE45 events | `c2_pat.events_for('tc','45s','R_three')` / `R_three_strict` | 89,464 / 78,412 | **exact set match** (bar, direction, body mid, open, extreme) for all three gap references |
| PE45 per signal | first event after t0 (K>=10 pre-signal bars) | 44,370 | 100.00% |
| PE45 per signal | active-at-signal set (<=600 s, unmitigated), K=24 / 26 / 26+completion age | 44,370 | 99.865% / 99.872% / 99.887% |
| ES lag_z | `S_lag_z_30` (and es_z, nq_z) of the ESL feature file | 44,370 (43,520 finite) | **NaN pattern 100%, max abs diff 0**, multiplier class 100% |
| ES sensitivity | t_end = t0 instead of t0-1 | 43,520 | class agreement only 85.1%: the convention is not optional |
Note on sealed data: `bars/time_1m.parquet` (ER exact check) contains rows after the cut in its second row group; only row group 0 (<= 2026-01-20) is decoded, hence ER A/B uses signals to 2026-01-19. An earlier test iteration decoded the whole file and discarded post-cut rows by filter; no post-cut value was used.

## 6. SCHEMA CHANGE REQUESTS (the CSV is not edited by this worker)
* **C1 pe45_bars pre-signal depth:** "3 bars before t0" -> **>= 26 closed bars** (24 minimum with research guards; 16 if the scorer uses min_prior=2).
* **C2 forming-bar extremes:** add to `signals`: `pe45_form_hi`, `pe45_form_lo` = max/min price of prints from the last closed 45-s bar's end through t0 inclusive (needed to know whether a pre-signal pattern was mitigated in the forming bar); optional `comp_ms` column in `pe45_bars` (first print time >= bar_end-1 s; fixes the 600-s age boundary, +0.015%).
* **C3 PE45 rule definition (lead decision):** research R1 cell (b, body mid, pure wait) takes an ACTIVE pre-signal pattern first (19.1% of signals), else the first event after t0. The schema/spec/scorer look only after t0. Either add `pe45_pre_event_ts`, `pe45_pre_limit_px` or state that R1 shadow = after-t0 only (then it is not the LEAD cell). Also `shadow_score.pe45_event` has no gap guard (180 s), no >= 10-prior-bar guard and no mitigation rule; use `d6_state.pe45_events` / `pe45_active_at`.
* **C4 Keltner:** FORWARD_SHADOW_SPEC R4 says "EMA20 4h + 1.5 ATR14"; the tested line (poi_gen `kc_up`, DS3_ZONES_2) is EMA20 + 2.0 x SMA(TR,10). d6_state uses the research definition (parameters selectable). Also the shadow set is 8 of the 11 tested lines (VAH sw15, LVN2 sw1h, HVN sw1h dropped): its research fire rate is **15.1% of signals at D=20** (not the 19% / 56 per week of the 11-line set), which is the reference for the "fire rate within 0.5-2x" gate.
* **C5 scorer `zone_recompute`** uses `0 < dist`; research counts a line exactly at the signal price (dist 0). Change to `0 <= dist`. Add `zone_null_reason`, `es_null_reason`, `pe45_null_reason` (only `er_null_reason` exists).
* **C6 ES fields:** document `es_px_t0` = last trade <= **t0-1 s**, `es_px_tm30` = <= **t0-31 s** (not "the signal second"); add `es_contract` (roll guard) and `es_hb_age_ms` (age of the last ES message of ANY type, quote or trade): `es_feed_age_ms` as trade age is > 1 s on 16.2% of historical signals, so the ">1 s = untrusted" flag mostly flags quiet markets.
* **C7 er_closes / er_bar_end_ts:** require >= 2 decimals; `er_bar_end_ts` in epoch ms. Add `lot_rule` (`half_up|floor1`) to signals so `hyp_lots_er` is auditable (or fold into live_config_ver).
* **C8 signal_px** = the book's planned entry price E (see 1.1).

## 7. What D6 must have before Monday (checklist)
1. 5-min ring: >= 25 closed epoch 5m bars of the front contract (raw closes, bar_end <= t0 inclusive), bars only when printed.
2. 45-s ring (P6 only): >= 26 closed epoch 45-s bars (o h l c v bar_end_ms), the forming bar's running high/low, all bars after the signal until live exit / 16:55 ET flatten; no filler bars.
3. Lines file: 1h bars >= 26 (kijun), 4h bars (18:00 ET anchor) >= 100 for EMA20 seed + ATR10 (decay 0.905/bar: 100 bars leave < 0.005 pt of seed error), 1d (Globex day) previous bar, previous RTH H/L/C (09:30-16:00 ET), 15m bars >= ~200 for 3 swing highs and lows; per-line touched_s persisted and updated on every print; file version hash.
4. ES and NQ: 1-s last-trade ring >= 60 s with trade timestamps, a contract id for ES, completed 1-min bars from the 1-s last prices (>= 15) for ATR14; heartbeat age.
5. A writer that is append-only, buffered, fail-open, measures its own p99 (< 50 ms or disables itself), writes blanks + reasons, and stamps `ts_eval_ms` after the live decision.
6. Open decisions the lead owes D6: lot rounding rule (half_up vs floor1), R1 pre-signal handling (C3), Keltner definition (C4), R5/R6 state definitions.
