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
signal_id, line_id, first_true_ts_utc (first evaluation where pct>=a AND the gate holds), eval_grid_s (10 or 1; record the grid actually used by D7), pct_now, upnl_pts, tot_rel (rel_tot8), ahead_rel (rel_ahead8), spread_ticks, depth8_total, depth8_ahead, median_base_total, median_base_ahead (the 20-day same-minute medians used), line_live (0/1: did it exit the trade), exit_px_if_taken, pts_vs_own_exit (own bracket exit - fire price, signed with trade), would_exit_before_cut (0/1), also tighten: trail_pts and breach_ts. Evaluate EVERY line on EVERY open trade each second (1-s is preferred: the 10-s grid fires 25-30% less often and later, see DS3_D7_TAKE_LINES.md section 10) and log both 1-s and 10-s first-true times.

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
