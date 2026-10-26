# REPORT PZ5 - LIVE-WEEKS FORWARD MONITOR (infrastructure; D00 x M7)
**Verdict: MONITOR BUILT, no test cell. 0 new live weeks exist after the frozen watermark 20261013, so every overlay reads TOO-EARLY.** Script: code/census/night_ins/ap_pz5_forward.py (extends the watch_n2x10.py approach; modifies no other script). Output: outputs/autopilot/watch/FORWARD_OVERLAYS.md (+ FORWARD_OVERLAYS_log.csv, FORWARD_OVERLAYS_state.json, FORWARD_<name>.json).

## What it does
- Runs each overlay in its own clean process against the CURRENT outputs/h2/ROWS_corrected_engine.parquet and 1-min arrays: N2X10 (H11-B N2_X10_HALT, via ap_h11_b hook), J6A (J6a b15k1_m0.0, ap_j6_core.mkmult), PA5 (L60_TWO_V terciles frozen on clean), PX1 (W60_MEAN1, divisor frozen at the watermark), PX26 (ALIGN_COUNTER_DOWN, RTH entries), K96B (HM stop-entry one-shot via ap_k96b.runb on the 1-s engine; needs the 1-s arrays refreshed as well).
- Reports per overlay: H2 and all-in weekly Sharpe pair vs overlay, new weeks after the watermark (weekly P&L table), new-week Sharpe, cumulative net difference, worst new week, and the pre-registered reading: PROMOTE-CANDIDATE only if >= 8 new weeks AND new-week uplift >= +0.10 AND cumulative new-week net difference > 0 AND worst new week not worse; HOLD-WATCH otherwise; TOO-EARLY below 8 weeks. Gates are not changed; a promotion only triggers a full re-run of the family gates.
- Skips if the rows file is unchanged (signature), `--force` overrides; the watermark is taken from watch/N2X10_state.json (20261013) so all watches share one cut; adapters failing are reported, never fatal; warns if rows extend past the 1-min bars.
- Usage after each weekly data refresh: `python3 -I ap_pz5_forward.py` (about 3 minutes).

## Validation
- Today's run reproduces every parent number from the stored reports: H2 / all-in uplift N2X10 +0.19/+0.24, J6a +0.14/+0.20, PA5 +0.06/+0.47, PX1 -0.16/+0.18, PX26 +0.08/+0.16, K96b +0.25/+0.62.
- Back-test mode `--watermark 20260901` (writes FORWARD_TEST.md, not the live file) exercised the new-week logic on 7 existing H2 weeks: N2X10 +0.17 new-week uplift (fired 2026-09-28 and 10-01), J6a -0.21, PA5 +0.73, K96b +0.90; all TOO-EARLY (7 < 8). These are in-sample H2 weeks, not forward evidence.

## Caveats
Mark-to-market rows past the last 1-min bar are clamped (same caveat as watch_n2x10.py); K96b depends on the 1-s arrays, which the weekly refresh must rebuild; PX1's mean divisor is frozen at the watermark (the parent used the all-trade mean).

DONE PZ5
