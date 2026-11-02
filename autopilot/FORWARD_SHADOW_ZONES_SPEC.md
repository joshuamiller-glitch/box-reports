# FORWARD SHADOW ZONES SPEC (generic) - BASE-4, 2026-11-02
Log-only; nothing trades; nothing is acted on. Applies to D7 v1.3 EXACT (books K7 H7 M7 U7 P7 + A6). Rule-specific definitions (PUL k3 pulled-wall: `l2vast/ds3/out/zl_new/live_spec.md`, written by ZL-1) plug into the zone block below. Post-hoc/consistency labels only; no PASS.

## Files (append-only CSV, UTC, one header line, written by D7 at decision time)
1. `forward_register/shadow_signals.csv` - ONE ROW PER BASE SIGNAL D7 evaluates (taken or not, including signals skipped by the live layer and blocked by blackout/locks)
2. `forward_register/shadow_exit_fires.csv` - ONE ROW PER EXIT-LINE EVALUATION THAT FIRES (and one per first condition-met row per line per trade, even when the line is not live)
3. `forward_register/shadow_zone_flags.csv` - ONE ROW PER (SIGNAL x ZONE RULE) for every shadow zone rule (skip / half / re-target variants), so a rule can be added without re-running the base
4. `forward_register/shadow_events_<rule>.csv` - raw events of the detector itself (e.g. pul_events.csv) for the reproducibility check
5. `forward_register/shadow_daily.csv` - end of label day: base daily $ per book x session, locks fired (per-book week floor, day give-back, combined stack lock if live), kill-switch state

## shadow_signals.csv fields
signal_id, ts_signal_utc (end of the signal second), label_day, iso_week, book (K7/H7/M7/U7/P7/A6), session (asia london pre nyam nypm close), side (+1/-1), entry_px (planned), entry_px_filled, fill_ts_utc, stop_dist_pts, target_dist_pts, planned_lots, er20, er_mult, size_mult_runmax, lots_final (after ER, zone HALF, signal-state rules), zone_layer_live_action (none/half/skip/b73), taken (0/1), reason_not_taken (zone_skip / sigstate / blackout_U7 / lock_book_week / lock_book_day / lock_comb / busy / other), exit_ts_utc, exit_px, exit_reason (target stop thl2_loss take_line tighten_line lock time), pnl_pts_per_lot, pnl_usd, fees_usd, mfe_pts, mae_pts, th_l2_loss_cut_fired (0/1) and cut_ts, u7_blackout_active (0/1) and its side.

## shadow_exit_fires.csv fields (per profit line K7 tighten30 / P7 / H7 / U7 / '*' and the TH-L2 loss cut)
signal_id, line_id, first_true_ts_utc (first evaluation where pct>=a AND the gate holds), eval_grid_s (10 or 1; record the grid actually used by D7), pct_now, upnl_pts, tot_rel (rel_tot8), ahead_rel (rel_ahead8), spread_ticks, depth8_total, depth8_ahead, median_base_total, median_base_ahead (the 20-day same-minute medians used), line_live (0/1: did it exit the trade), exit_px_if_taken, pts_vs_own_exit (own bracket exit - fire price, signed with trade), would_exit_before_cut (0/1), also tighten: trail_pts and breach_ts. Evaluate EVERY line on EVERY open trade each second (1-s is preferred: the 10-s grid fires ~25% less often and later, see DS3_D7_TAKE_LINES.md section D) and log both 1-s and 10-s first-true times.

## shadow_zone_flags.csv fields (per signal x rule)
signal_id, rule_id, variant (skip/half/retarget/delay), D_pts, keep_h (zone lifetime), frame (AHEAD/BEHIND/AT), fresh_only (0/1), n_zones_in_frame, nearest_zone_px, nearest_zone_dist_pts (along trade direction), zone_age_s, zone_strength, zone_touches, source_stream, flag (0/1), would_action, base_pnl_usd_if_taken (filled at trade close; for a signal skipped live, the hypothetical outcome from the unfiltered path is logged at the base exit time), detector_state_ok (book span / feed gap flag).

## Required control rows (so a placebo can be built from the forward log itself)
- every signal, flagged or not (denominator);
- per day: count of flagged signals by rule (the same-count random-skip placebo is drawn from the unflagged signals of the same day);
- zone-detector heartbeat per hour (events seen, book rows seen, gaps) to separate "no zone" from "no data".

## Scoring on the forward log (monthly; ON/OFF check only, nothing acted on)
Per rule and per exit line: base P&L of flagged/fired rows, maxDD of the base series with the action applied (skip: rows removed; half: lots x0.5 with min 1 lot; take/tighten: exit at the logged fire price), per book x session (Asia separately for PUL), vs same-count random placebos (100 draws, 3 kinds: random rows per day, shuffled day, same-volume random early exit), weekly maxDD cut and mean delta with MDE, carrying week named, leave-one-week-out. A rule needs >= 12 forward weeks before any label other than SHADOW. 

## Implementation notes
- No look-ahead: a zone event is usable from the first decision AFTER the end of its 1-s bin; a line condition is evaluated on state as of the end of the evaluation second.
- Lock engine fields are logged from the engine the live D7 uses; if live D7 has no combined 12R stack lock, log lock_comb as always 0 (open question to the user, see MORNING).
- Reproducibility check for every detector: compare live events with the stream rebuilt from the 1-s L2 table for the same days; log the match rate (target >= 95% same price and second).


## ZL-1 pointer (2026-11-02): PUL k3 numbers for the forward register
PUL k3 4h skip D20, V13X: lock=12R L6M +29% / PRE +22% / X' +20%; lock=None (headline) L6M +1% / PRE +17% / X' +11% / MID -14%. Label LEAD (weak, PRE/X' only), LOCK-ONLY on L6M. Detail and the live definition + log fields: autopilot/DS3_ZONES_3_S7_BOOK.md (sections "LIVE definition of the PULLED-WALL zone", "FORWARD SHADOW LOG spec", "HEADLINE (lock=None...)"). Per-cell files: /mnt/l2/l2vast/ds3_zones3_new/zl1/lockoff_cells.csv, placebo_lockoff.csv.

## Z2 pointer (2026-11-02): CRT4h 30pts fw2 solo (rule_id Z2_CRT4h30fw2solo), half
Exact live definition and the extra log fields (crt_line_px, crt_formed_ts_utc, crt_age_s, other-line distances, solo flag, shipped_crt_flag): autopilot/DS3_ZONES_3_S2.md, section "LIVE definition (Shadow only) of the CRT4h 30pts fw2 solo zone cell". Label LEAD (STRICT, not one-month, placebo ranks 0.09-0.14), Asia-carried; V13X lock=None L6M maxDD -6%, Calmar L6M/HOLD/MID/PRE/X' +8/+9/+6/+4/+5%.

## ZL-2 pointer (2026-11-02): LARGE-PRINT rows, rule id ZL2_LP25_4H_D40 (Shadow log only, mean-type finding)
Definition (D7 from its own print tape, no book, no daily file): flag a signal if a single print of >= 25 contracts (either aggressor side) in the last 4 h lies between the entry and the target within min(40 pts, target distance) and its price has not been traded through since the print. Log per signal: lp_flag, lp_n_prints, lp_nearest_px, lp_nearest_dist, lp_nearest_size, lp_nearest_side (+1 buy aggressor), lp_age_s, lp_fresh_since (touch time or none). Action in the forward test = none (log only); the research frame skips the flagged rows. Evidence and label: autopilot/DS3_ZONES_3_L2_TAPE_LARGEPRINT.md and DS3_ZONES_3_ROW_LEVEL.md: flagged rows earn -$280 per taken row vs +$183 for the others in HOLD (V13X realised, lock none; tail-driven, London), -$40 vs +$119 in PRE, +$184 vs -$45 in X'; weekly mean delta of skipping them +$2.9k/wk L6M / +$1.9k/wk HOLD (inside the MDE), absent in PRE/X'. Skip is not delay-sensitive (state at the decision second only).

## ZL-1: BT swing flip (MEAN-type lead; log-only; nothing trades) - live definition and Shadow log fields (2026-11-02)
Status: LEAD, mean/expectancy effect (flagged taken trades lose; saved dollars rank <= 0.02 vs row-level placebos in L6M/HOLD, lock None; NOT a robust drawdown cut). Results and caveats: autopilot/DS3_ZONES_3_B5_MANCINI.md sections 1-8.
Live definition (D7 computes from its own tape; no daily file):
1. Keep 5-minute bars aligned to the clock (high/low of the trade prices in each 5-min window) in the same price frame as the entry price.
2. A SWING HIGH is a bar whose high is strictly above the highs of the 2 bars before and the 2 bars after it; a SWING LOW mirrors. The swing is knowable at the close of the 2nd bar after it. Keep the last 3 swing highs and last 3 swing lows (a 4th newer one of the same kind replaces the oldest); keep each as (price L, kind, known time).
3. A swing high L is BROKEN at the first second the traded price is >= L + 10 pts (a swing low: <= L - 10). At that second create a FLIP LEVEL at price L with direction: support if it was a high broken upward, resistance if a low broken downward; kept 4 h from the break second; remove the swing from the ring. FRESH = the traded price has not returned to L since it first moved 0.5 pt or more away from L after the break (when the break happens price is 10+ pts away; fresh ends at the first return to L).
4. Rule at a base signal (entry E, side, target distance td): the signal is FLAGGED if a fresh flip level lies between E and the target in the direction of travel with 0 <= distance <= min(40, td) pts (distance = L - E for a long, E - L for a short; a level equal to E counts as 0). Effect in Shadow: would_skip = 1 (nothing is skipped live).
5. Latency: the flip level is created in the second of the break; a signal in the same second sees it (the stream convention is 'state at the end of the signal second'); D7 acts on the previous completed second, 1-s and 3-s delay do not change the cut (PUL test; BT 1-s/3-s delay not yet run).
Log (one line per base signal D7 evaluates, whether or not it trades; forward_register/bt_flip_shadow.csv): ts_signal_utc, book, session, side, entry_price, target_dist_pts, stop_dist_pts, bt_flag_D40 (0/1), bt_flag_D20 (0/1), would_skip, n_fresh_flip_levels_ahead, nearest_flip_price, nearest_flip_dist_pts (along the trade direction), nearest_flip_age_s (signal minus break second), nearest_flip_break_size_pts (max extension beyond L), nearest_flip_dir (support/resistance), nearest_flip_swing_age_s (break minus swing known time), n_flip_levels_total_last_4h, n_flip_levels_behind_within_stop, trade_taken (0/1), base_net_dollars (when taken, from the base), exit_type. Also log each flip-level creation (bt_flip_events.csv: break_ts_utc, price L, kind, swing_known_ts_utc, ext) so the live detector can be compared with the stream rebuilt from the 1-s table (expected: same levels and seconds on >= 95% of events).
Scoring on the forward register: sum of base_net_dollars over would_skip = 1 trades (saved $ = minus that sum), by book x session and by month, against 200 draws of random same-count-per-day trades; the dollars, not the maxDD, are the test; monthly ON/OFF check only, nothing acted on.

## Z2 pointer UPDATE (2026-11-02 ~09:00Z): the CRT4h 30pts fw2 solo entry above is WITHDRAWN pending the V13Y screen
On the fixed base V13Y its lock=None L6M maxDD cut falls from +6% (V13X, defect base) to -0% and it loses STRICT; the live definition stays on file in DS3_ZONES_3_S2.md but should not be shadow-logged on the strength of the V13X numbers. Current Z2 candidate on V13Y: camH3 40pts fw8 any (lock=None only, STRICT, L6M maxDD -8%); its definition is "PIV|cam_H3|rth line (Camarilla H3 of the prior completed RTH session: Close + 1.1 x (High-Low)/4), fresh and formed within the last 8 h, ahead within 40 pts, other lines unrestricted, half lots".
