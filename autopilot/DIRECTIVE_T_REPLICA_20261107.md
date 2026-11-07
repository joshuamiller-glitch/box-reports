# T-REPLICA (user, 2026-11-07, overrides everything else)
The engine must reproduce live D7 EXACTLY from the owned mbp-10 event stream. No calibration factors, no injected live exits, no "data-capped" labels.
Method: port DS7.cs literally - ManageThL2 (loss branch: unreal from the fill average, -unreal >= 30, pulled >= 30 x MedLevel, newMae within 5 s, 1-s throttle per book, DepthLive = depth update < 120 s and >= 5 levels each side, skip while ExitPending), L2ThSnapshot (snapshot on EVERY PRINT; per level present in the previous snapshot: cancelled = max(0, size decrease - prints traded at that price since the previous snapshot); a level that vanished inside the current best = size 0, beyond it = ignored; own side only), PulledSupport (sum of pulledLog rows in the last 5 s), MedLevel (0.001 EWMA of (top-5 bid + top-5 ask)/10, seeded at the first snapshot), the policy line (pct = unreal / stop distance, secs_ext <= 5), the entry/adverse-extreme reset at every fill, EntriesPerDirection=1, the 70/30 add with L2 confirmation, P7 45-s confirm, sessions/caps/locks/blackout as coded.
Run on the raw mbp-10 records of the blind week (every book event and print, exchange timestamps + the measured ~1 s decision latency).
Acceptance: every one of the 92 live cuts reproduced within +-2 s and NO cut live did not make (list every residual by trade with the exact feature values on both sides); then the frozen four gates.
If a residual remains, the difference is in the data or the port - find it and name it; do not relabel it. Report GATE0_REPLICA.md; iterate until it passes or until you can prove with a concrete trade that the owned data cannot carry the decision.

## USER (2026-11-07T14:44Z): "When T-REPLICA passes, start T-TH-REDO A-G immediately on the replica engine without asking."
Standing authorization. PASS = the acceptance above (92/92 live cuts within +-2 s, zero cuts live did not make, frozen four gates met, residuals named) AND an independent QA read of the replica (CHAR-C style, from the C#) finds no mismatch/look-ahead/calibration. Then the lead launches A-G via code/th_redo/launch_AF.sh (full mode) on the replica engine, same hour, no question to the user; GATE0 json promoted by the replica owner only. THP refit cadence (first 2026-11-15 only if passed) as in the TH-REDO directive.

## USER REPLICA INPUTS (2026-11-07T18:49Z)
(1) Old-panel signal-state slots per v1.2 defaults, as the live log shows them firing: slot1 H7 SkipBot3 on Slope; slot2 K7 SkipTop3 on St1Dist; slot3 P7 SizeHi on St1Dist (x1.5 top third / x0.5 bottom); slot4 H7 SkipBot3 on St1Dist; min history 100; causal expanding rank. X1-X5 old panel = the parameter string in DS7_INSTALL v1.2 (Shadow since Mon 08:50). OTE mode B73 D30; tighten trail = 30 TICKS.
(2) Sizer rounding floor(lots*mult+0.5): 7 x 1.5 -> 11 SIZED; live filled 7 market + 3 add = 10 because one slice did not fill (SLIT cap/fill) - the 11 is right.
(3) Tuesday stall: connection drop; exact start/end to be read from the NT8 log - use inferred 02:04-02:16 and 19:19-19:55 until then.
(4) Chart loaded 30 days of NQ 12-26 (merged history off).
(5) Policy file text/mtimes as in GATE0_ANSWERS sec 6 (08:05 five lines / 08:15 empty / 08:20 one loss line).
(7) Promote the measured 0.175 s exchange fill + ~1 s callback and the cumvol resting-target rule into the headline - measurements, not fits.
DECISION: (c) keep iterating the non-cut residuals now; th_eval.csv from D7 v1.5 arrives Sun 11-08 18:00 ET (23:00Z) and then (a). A-G stay parked.
