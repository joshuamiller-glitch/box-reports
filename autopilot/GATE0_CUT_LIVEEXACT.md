# GATE0 CUT LIVE-EXACT (ZL-2) - PRE-PROOF, post-hoc, no PASS claim
Written 2026-11-07T00:36Z. Evaluator of the live loss cut driven from the RAW NQZ6 mbp-10 stream (10 files, 135,325,221 records, 2,316,491 T records = prints), calibrated on the frozen live blind week (187 trades, sha256 424c68da...). Reads DS7.cs sha256 54697597... (read, not inferred): L2OnDepthSnapshot, L2ThSnapshot, PulledSupport, ManageThL2 loss branch, ManagePolicy loss line, Feature(secs_ext/pct/pulled_mult), OnMarketData loop (AdvExt update before ManageThL2 before ManagePolicy), RequestBookExit.
Code (l2vast/ds3/code/gate0/): zl2_cut_stream.py c0752233c59c.. (per-print stream, numba), zl2_cut_eval.py 736510ea430d.. (per-book evaluator), zl2_cut_report.py e65f1da7454c.. , zl2_cut_diag.py 4a00c8a21d86.. . Prereg shas in DECISIONS.md (3 lines, 00:3xZ). Bulk: /mnt/l2/l2vast/_gate0_zl2/ (stream_nq_blind.npz, classified CSVs, variants.txt, md5 manifests before/after IDENTICAL). No sealed/published tree read or written; no data/live CSV touched.

## What is modelled (per DS7.cs)
- One snapshot per T record (= one Last print). The T record carries the PRE-trade book in Databento; 10 levels per side. Snapshot skipped if <5 levels a side.
- cancelled(side) = sum over previous-snapshot levels of max(0, prevSize - curSize - traded@price); level absent now: price inside current best -> size 0, else ignored. traded@price = prints k-1 and k at that exact price (code uses ticks >= t0 where t0 = previous snapshot time, so the previous print is included).
- MedLevel = EWMA 0.001 of (sum top5 bid + top5 ask)/10 every snapshot, seeded with the first snapshot of the week (live ran before Sunday 18:00; ~1000-print memory so converged within minutes; week range of MedLevel 1.7-5.0).
- pulledLog row per snapshot; PulledSupport = own side over rows with ts >= now-5 s. DepthLive = non-trade book update within 120 s and >=5 levels each side.
- Book: AdvExt=entryPx, AdvExtTime=entry at start, strict worsening per print; ManageThL2 throttle ThL2LastEval set only after DepthLive passes (profit/loss branches both consume it); panel: -unreal>=30, MedLevel>0, pulled>=30*Med, newMae (now-AdvExtTime<=5 s). Policy line (from Mon 11-02 08:20 ET): own 1-s throttle, no DepthLive check, pct=unreal/stop <= -0.50, pulled/Med>=30, secs_ext<=5. Stops: 60 pts (K7 P7 U7 H7 M7 A7), O7 40, X3/X4/X5 75/75/60 (from ws3b brackets; X stops are an assumption). Market exit; no lot scaling, min age, suppression. Panel evaluated first, then policy, per print.
- Times: file clock is ET, EST all week -> epoch = ET + 5 h; stream clock = ts_recv (epoch ns).

## Approximations (documented, not fixed)
1. mbp-10 has 10 levels, NT8 DOM up to 20: cancels at ranks 11-20 and levels that drift between ranks 11-20 are invisible here (pulled biased LOW vs live).
2. Databento T records = MDP3 trade-summary entries; assumed equal to NT8/Rithmic Last events (EWMA memory and the 'k-1,k' traded window depend on print count).
3. Live clock is Globals.Now (arrival, system clock resolution unknown); stream uses ts_recv. If the live clock is coarse (ms/15 ms), more prints share t0 and traded is larger (pulled biased LOW further). The ordering of NT8 depth vs Last events within a packet is unknown.
4. Entry time is the file's entryTime (minute resolution for many books); the live per-slice fills (2 s apart; ResetTh on every fill resets AdvExt and PolicyLastEval but NOT ThL2LastEval) and the 30% limit add are not reproduced. Entry lag +/-10 s changes nothing (variants.txt).
5. Exit fill latency (cancel stop/target, then market) is not modelled; compare sim trigger with the live FILL second (second resolution).
6. Policy file load time (<=300 s polling after 08:20) and X-book stop distances assumed; PolicyCut vs ThL2Cut label depends on unobservable sub-second phase of the two 1-s throttles, so the label is not a calibration target.

## Result (subset = 92 live cuts + 13 live non-cut trades whose print-MAE reached -30; the 12 'held' of the brief are 13 here by raw MAE)
Match = sim trigger from 1 s after to 10 s before the live exit fill (fixed before scoring).
| status | n | meaning |
|---|---|---|
| MATCH | 51 | live cut and sim cut within 10 s; median exit-minus-trigger lag 0.57 s |
| SIM_EARLY | 24 | live cut, sim triggered earlier than 10 s before the live fill (9 of them 11-18 s early = plausibly slow live exit, 15 of them 39 s to 2.4 h early = live did not cut at that moment) |
| MISS | 17 | live cut, sim never triggered before the live exit |
| FALSE_POS | 10 | live NOT cut (held), sim cut |
| HELD_OK | 3 | live not cut, sim not cut |
Live cuts reproduced at all (any time before live exit): 75 of 92 (81.5%); within 10 s: 51 of 92 (55.4%); within 20 s: 60 of 92 (65.2%). Live held trades that reached -30: sim agrees on 3 of 13 (23%). Of the 82 trades outside the subset (live not cut, print-MAE shallower than -30) the sim cuts none (82 of 82 agree).
Ingredient check (diagnostic): in the 25 s before the live exit, the sim's best pulled/MedLevel on armed prints is >=30 for 84 of 92 live cuts, >=20 for 90, >=10 for 92. Marginal: sim pulled/Med at its triggers is 30-40 in about half the SIM_EARLY and FALSE_POS rows. Misses have a median best 40 (13.9-109.7), i.e. in most misses the pull exists in the sim stream but did not coincide with a qualifying evaluation (cause not isolated: newMae timing, throttle phase and 10-level depth are all candidates).
Rule label: sim says ThL2Cut for 74 of 75 triggers (identical rule on 60-pt books, panel first); live after 08:20 split PolicyCut 37 / ThL2Cut 45 -> sub-second throttle phase, not reproducible; label agreement 54.7% is chance-like and NOT informative.
Sensitivities (variants.txt, not selected on): policy only +300 s start, entry lag +10/-3 s, pol_phase=slice: all identical to primary. Panel-only: 50 match/18 miss. Policy-only: 50/23. pulled window 4 s: 49/21. Multiplier 25: 55 match/11 miss/10 FP; 35: 51/22/9 FP. The multiplier is not fitted; 30 stays.

## Reading (post-hoc, PRE-PROOF)
The evaluator is live-exact in mechanics and reproduces most live cuts, but 10-level depth (pulled biased low), unknown live clock/packet ordering and unobservable fill/phase state leave 17 misses and 24 early triggers; the 13 held-at-(-30) trades are mostly (10/13) cut by the sim, i.e. the live did NOT cut near-threshold events the sim cuts (consistent with live pulled being measured lower or the live newMae/throttle phase). A TH table built on this evaluator inherits a ~40-45% per-trade disagreement on cut timing; do not call Gate 0 passed on this alone. Open for the user: (a) th_eval.csv from v1.5 will give pulled/MedLevel per evaluation to calibrate the 10- vs 20-level gap; (b) whether the live platform restarted mid-week (MedLevel reseed); (c) X3/X4/X5 stop distances.

## Per-trade table (105 trades: all 92 live cuts + 13 live non-cut with print-MAE <= -30; ET; sim MAE from raw prints; 'best armed pulled/Med' = diagnostic for live cuts only)
| # | book | side | entry (ET) | live exit (ET) | live exit kind | live pts at exit | sim MAE | sim status | sim trigger (ET) | exit-minus-trigger s | sim rule | pulled/Med at trigger | best armed pulled/Med 25 s before live exit |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | P7 | L | 11-01 19:11 | 11-01 20:25:34 | Target | 60.0 | -33.7 | FALSE_POS | 11-01 19:23:45 | 3709.0 | ThL2Cut | 32.6 |  |
| 2 | P7 | L | 11-01 20:45 | 11-01 23:02:27 | Target | 60.1 | -38.9 | FALSE_POS | 11-01 21:00:00 | 7346.9 | ThL2Cut | 38.8 |  |
| 3 | K7 | L | 11-01 22:48 | 11-02 01:20:34 | ThL2Cut | -31.8 | -34.0 | MATCH | 11-02 01:20:33 | 0.8 | ThL2Cut | 43.1 | 49.4 |
| 4 | H7 | L | 11-01 22:50 | 11-02 01:21:10 | ThL2Cut | -34.4 | -34.4 | MISS |  |  |  |  | 25.3 |
| 5 | P7 | L | 11-01 23:03 | 11-02 01:21:10 | ThL2Cut | -35.2 | -35.5 | MISS |  |  |  |  | 25.3 |
| 6 | X4 | S | 11-02 02:21 | 11-02 02:39:36 | Target | 40.0 | -36.2 | HELD_OK |  |  |  |  |  |
| 7 | U7 | S | 11-02 02:40 | 11-02 03:01:49 | ThL2Cut | -32.5 | -32.5 | MISS |  |  |  |  | 17.1 |
| 8 | X5 | S | 11-02 04:00 | 11-02 04:06:50 | ThL2Cut | -35.2 | -30.5 | SIM_EARLY | 11-02 04:06:38 | 11.4 | ThL2Cut | 52.9 | 60.0 |
| 9 | M7 | S | 11-02 02:35 | 11-02 04:18:39 | ThL2Cut | -40.6 | -32.6 | SIM_EARLY | 11-02 04:15:49 | 169.2 | ThL2Cut | 30.9 | 44.2 |
| 10 | P7 | S | 11-02 03:23 | 11-02 04:18:39 | ThL2Cut | -51.4 | -35.4 | SIM_EARLY | 11-02 03:40:00 | 2318.1 | ThL2Cut | 33.3 | 44.2 |
| 11 | X4 | L | 11-02 04:39 | 11-02 07:06:08 | ThL2Cut | -44.4 | -31.4 | SIM_EARLY | 11-02 06:58:00 | 487.9 | ThL2Cut | 32.4 | 25.9 |
| 12 | K7 | S | 11-02 01:45 | 11-02 07:35:27 | Target | 60.0 | -34.0 | HELD_OK |  |  |  |  |  |
| 13 | M7 | S | 11-02 06:58 | 11-02 08:05:20 | PolicyTake | 42.0 | -32.2 | HELD_OK |  |  |  |  |  |
| 14 | X3 | S | 11-02 08:31 | 11-02 08:36:46 | PolicyCut | -42.2 | -30.8 | SIM_EARLY | 11-02 08:36:30 | 15.1 | ThL2Cut | 36.3 | 112.9 |
| 15 | K7 | S | 11-02 07:54 | 11-02 08:36:49 | ThL2Cut | -32.0 | -32.0 | MATCH | 11-02 08:36:48 | 0.6 | ThL2Cut | 138.1 | 147.8 |
| 16 | M7 | S | 11-02 08:20 | 11-02 08:36:50 | PolicyCut | -29.8 | -32.6 | MATCH | 11-02 08:36:49 | 0.6 | ThL2Cut | 119.6 | 147.8 |
| 17 | P7 | S | 11-02 07:51 | 11-02 08:36:55 | PolicyCut | -33.9 | -40.4 | MATCH | 11-02 08:36:52 | 2.6 | ThL2Cut | 157.1 | 159.2 |
| 18 | X3 | S | 11-02 08:38 | 11-02 08:43:22 | ThL2Cut | -30.6 | -31.9 | MATCH | 11-02 08:43:22 | -0.8 | ThL2Cut | 108.0 | 115.5 |
| 19 | P7 | S | 11-02 10:02 | 11-02 10:09:42 | PolicyCut | -35.9 | -30.4 | SIM_EARLY | 11-02 10:05:28 | 253.9 | ThL2Cut | 125.5 | 182.4 |
| 20 | M7 | S | 11-02 10:02 | 11-02 10:09:45 | ThL2Cut | -28.8 | -33.0 | MATCH | 11-02 10:09:43 | 1.1 | ThL2Cut | 135.9 | 146.1 |
| 21 | H7 | L | 11-02 10:25 | 11-02 10:38:19 | PolicyCut | -30.0 | -30.8 | SIM_EARLY | 11-02 10:32:43 | 335.1 | ThL2Cut | 57.6 | 67.2 |
| 22 | K7 | L | 11-02 10:36 | 11-02 10:38:42 | PolicyCut | -31.2 | -30.8 | MATCH | 11-02 10:38:42 | -0.2 | ThL2Cut | 56.4 | 63.0 |
| 23 | M7 | L | 11-02 10:22 | 11-02 10:47:27 | ThL2Cut | -35.8 | -30.2 | SIM_EARLY | 11-02 10:38:51 | 515.2 | ThL2Cut | 68.1 | 93.9 |
| 24 | K7 | S | 11-02 12:54 | 11-02 12:56:12 | ThL2Cut | -32.5 | -32.8 | MATCH | 11-02 12:56:11 | 0.3 | ThL2Cut | 87.5 | 94.4 |
| 25 | K7 | L | 11-02 18:21 | 11-02 18:45:37 | ThL2Cut | -30.8 | -30.8 | MATCH | 11-02 18:45:36 | 0.6 | ThL2Cut | 64.1 | 67.7 |
| 26 | K7 | S | 11-02 19:45 | 11-02 19:47:21 | ThL2Cut | -31.8 | -30.0 | MATCH | 11-02 19:47:19 | 1.2 | ThL2Cut | 35.4 | 50.6 |
| 27 | P7 | S | 11-02 18:47 | 11-02 20:29:16 | PolicyCut | -30.1 | -30.9 | MATCH | 11-02 20:29:12 | 3.3 | ThL2Cut | 56.9 | 78.6 |
| 28 | P7 | S | 11-02 20:42 | 11-02 21:03:11 | ThL2Cut | -31.4 | -30.4 | SIM_EARLY | 11-02 20:53:24 | 586.7 | ThL2Cut | 30.8 | 42.6 |
| 29 | K7 | L | 11-02 20:09 | 11-02 22:36:58 | PolicyCut | -40.2 | -31.0 | SIM_EARLY | 11-02 20:11:33 | 8724.5 | ThL2Cut | 34.4 | 51.3 |
| 30 | A7 | S | 11-03 00:36 | 11-03 00:42:01 | ThL2Cut | -40.2 | -35.8 | SIM_EARLY | 11-03 00:41:48 | 12.6 | ThL2Cut | 31.0 | 45.3 |
| 31 | K7 | S | 11-03 01:21 | 11-03 01:30:05 | ThL2Cut | -37.4 | -34.9 | MATCH | 11-03 01:30:05 | -0.2 | ThL2Cut | 72.6 | 87.4 |
| 32 | A7 | S | 11-03 01:19 | 11-03 01:30:05 | ThL2Cut | -35.0 | -32.5 | MATCH | 11-03 01:30:05 | -0.2 | ThL2Cut | 72.6 | 87.4 |
| 33 | K7 | L | 11-03 01:36 | 11-03 01:47:31 | ThL2Cut | -51.5 | -34.2 | SIM_EARLY | 11-03 01:45:34 | 116.5 | ThL2Cut | 30.4 | 24.4 |
| 34 | M7 | S | 11-03 02:04 | 11-03 02:47:29 | Stop | -80.8 | -48.5 | FALSE_POS | 11-03 02:29:16 | 1092.2 | ThL2Cut | 40.7 |  |
| 35 | K7 | S | 11-03 01:48 | 11-03 02:55:35 | Stop | -83.0 | -46.0 | FALSE_POS | 11-03 02:29:20 | 1574.7 | ThL2Cut | 69.8 |  |
| 36 | O7 | L | 11-03 09:41 | 11-03 09:53:39 | PolicyCut | -22.2 | -21.2 | MATCH | 11-03 09:53:37 | 1.2 | PolicyCut | 83.5 | 101.0 |
| 37 | P7 | L | 11-03 10:20 | 11-03 10:23:25 | ThL2Cut | -34.4 | -34.9 | MISS |  |  |  |  | 109.7 |
| 38 | M7 | L | 11-03 10:26 | 11-03 10:32:06 | PolicyCut | -32.2 | -34.5 | MATCH | 11-03 10:32:06 | -0.0 | ThL2Cut | 80.3 | 89.7 |
| 39 | K7 | L | 11-03 10:57 | 11-03 11:18:33 | PolicyCut | -32.8 | -30.0 | MATCH | 11-03 11:18:31 | 1.5 | ThL2Cut | 65.4 | 80.9 |
| 40 | K7 | S | 11-03 11:33 | 11-03 11:39:37 | ThL2Cut | -29.8 | -30.0 | MATCH | 11-03 11:39:36 | 0.2 | ThL2Cut | 55.0 | 55.0 |
| 41 | A7 | L | 11-03 18:13 | 11-03 18:31:21 | PolicyCut | -28.2 | -30.2 | MATCH | 11-03 18:31:20 | 0.4 | ThL2Cut | 36.0 | 36.0 |
| 42 | P7 | L | 11-03 18:13 | 11-03 18:37:42 | PolicyCut | -46.9 | -40.6 | SIM_EARLY | 11-03 18:34:41 | 180.6 | ThL2Cut | 30.3 | 55.0 |
| 43 | K7 | L | 11-03 18:06 | 11-03 18:37:42 | PolicyCut | -44.6 | -38.1 | SIM_EARLY | 11-03 18:34:41 | 180.6 | ThL2Cut | 30.3 | 55.0 |
| 44 | K7 | S | 11-03 18:57 | 11-03 19:04:10 | PolicyCut | -43.5 | -47.0 | MATCH | 11-03 19:04:07 | 2.6 | ThL2Cut | 32.8 | 45.8 |
| 45 | P7 | S | 11-03 18:56 | 11-03 19:04:10 | PolicyCut | -35.2 | -38.2 | MATCH | 11-03 19:04:07 | 2.6 | ThL2Cut | 32.8 | 35.3 |
| 46 | P7 | S | 11-03 20:03 | 11-03 20:03:27 | ThL2Cut | -30.4 | -31.9 | MISS |  |  |  |  | 98.8 |
| 47 | K7 | S | 11-03 20:03 | 11-03 20:03:30 | ThL2Cut | -39.0 | -31.8 | MATCH | 11-03 20:03:29 | 0.7 | ThL2Cut | 80.5 | 91.6 |
| 48 | A7 | S | 11-03 20:32 | 11-03 20:35:04 | PolicyCut | -32.8 | -33.0 | MATCH | 11-03 20:35:04 | -0.1 | ThL2Cut | 58.1 | 59.8 |
| 49 | A7 | S | 11-03 20:40 | 11-03 20:41:30 | PolicyCut | -42.5 | -30.2 | MATCH | 11-03 20:41:22 | 7.1 | ThL2Cut | 39.7 | 63.3 |
| 50 | P7 | S | 11-03 20:44 | 11-03 20:47:21 | PolicyCut | -37.6 | -35.9 | MATCH | 11-03 20:47:20 | 0.1 | ThL2Cut | 52.4 | 79.4 |
| 51 | A7 | S | 11-03 21:29 | 11-03 21:30:20 | ThL2Cut | -35.0 | -35.0 | MATCH | 11-03 21:30:20 | -0.8 | ThL2Cut | 38.3 | 39.4 |
| 52 | K7 | S | 11-03 22:03 | 11-03 22:03:18 | PolicyCut | -35.8 | -31.8 | MATCH | 11-03 22:03:18 | -0.0 | ThL2Cut | 32.2 | 45.0 |
| 53 | P7 | S | 11-03 22:15 | 11-03 22:16:23 | ThL2Cut | -30.6 | -33.3 | SIM_EARLY | 11-03 22:16:04 | 18.0 | ThL2Cut | 38.1 | 47.4 |
| 54 | A7 | S | 11-03 22:02 | 11-03 22:16:47 | PolicyCut | -31.8 | -35.2 | MATCH | 11-03 22:16:46 | 0.2 | ThL2Cut | 51.3 | 58.9 |
| 55 | P7 | S | 11-03 22:52 | 11-03 22:55:30 | PolicyCut | -36.2 | -35.0 | MATCH | 11-03 22:55:30 | -0.3 | ThL2Cut | 40.8 | 53.1 |
| 56 | P7 | S | 11-03 23:07 | 11-03 23:09:26 | PolicyCut | -34.1 | -31.4 | SIM_EARLY | 11-03 23:09:14 | 11.2 | ThL2Cut | 39.0 | 44.7 |
| 57 | K7 | S | 11-03 23:24 | 11-03 23:39:04 | ThL2Cut | -35.2 | -31.0 | MATCH | 11-03 23:39:01 | 2.2 | ThL2Cut | 53.7 | 64.3 |
| 58 | A7 | L | 11-04 00:11 | 11-04 00:15:23 | PolicyCut | -34.0 | -32.2 | MATCH | 11-04 00:15:21 | 1.9 | ThL2Cut | 73.3 | 88.5 |
| 59 | A7 | L | 11-04 00:17 | 11-04 00:21:54 | PolicyCut | -33.5 | -35.0 | MATCH | 11-04 00:21:53 | 0.2 | ThL2Cut | 33.0 | 33.0 |
| 60 | A7 | L | 11-04 00:24 | 11-04 00:27:18 | ThL2Cut | -26.0 | -31.5 | MISS |  |  |  |  | 47.5 |
| 61 | A7 | L | 11-04 00:31 | 11-04 00:43:18 | Target | 60.0 | -34.0 | FALSE_POS | 11-04 00:33:02 | 615.6 | ThL2Cut | 41.9 |  |
| 62 | K7 | L | 11-04 01:06 | 11-04 01:19:12 | ThL2Cut | -34.1 | -36.9 | MISS |  |  |  |  | 30.5 |
| 63 | P7 | L | 11-04 00:53 | 11-04 01:24:11 | PolicyCut | -41.0 | -45.2 | MATCH | 11-04 01:24:09 | 1.4 | ThL2Cut | 57.0 | 73.9 |
| 64 | A7 | L | 11-04 00:44 | 11-04 01:24:11 | PolicyCut | -44.2 | -48.5 | MATCH | 11-04 01:24:09 | 1.4 | ThL2Cut | 57.0 | 73.9 |
| 65 | M7 | L | 11-04 02:13 | 11-04 02:16:07 | PolicyCut | -33.0 | -33.0 | MISS |  |  |  |  | 83.1 |
| 66 | K7 | L | 11-04 02:12 | 11-04 02:21:31 | ThL2Cut | -32.8 | -35.8 | MISS |  |  |  |  | 21.8 |
| 67 | K7 | L | 11-04 03:36 | 11-04 04:02:07 | PolicyCut | -54.8 | -31.8 | SIM_EARLY | 11-04 03:59:06 | 180.5 | ThL2Cut | 33.6 | 44.0 |
| 68 | M7 | L | 11-04 03:57 | 11-04 04:02:07 | PolicyCut | -43.8 | -33.0 | SIM_EARLY | 11-04 04:01:27 | 39.1 | ThL2Cut | 32.2 | 44.0 |
| 69 | P7 | L | 11-04 03:36 | 11-04 04:02:07 | PolicyCut | -51.4 | -30.1 | SIM_EARLY | 11-04 04:01:07 | 59.9 | ThL2Cut | 31.1 | 44.0 |
| 70 | K7 | S | 11-04 04:03 | 11-04 04:08:30 | ThL2Cut | -38.0 | -33.0 | SIM_EARLY | 11-04 04:08:15 | 14.2 | ThL2Cut | 31.5 | 47.7 |
| 71 | K7 | L | 11-04 05:42 | 11-04 05:45:01 | ThL2Cut | -39.2 | -32.2 | MATCH | 11-04 05:44:56 | 5.0 | ThL2Cut | 45.3 | 97.0 |
| 72 | M7 | L | 11-04 06:00 | 11-04 07:00:02 | ThL2Cut | -37.9 | -38.1 | MATCH | 11-04 07:00:01 | 1.0 | ThL2Cut | 67.8 | 124.8 |
| 73 | P7 | L | 11-04 06:45 | 11-04 07:00:02 | ThL2Cut | -41.2 | -35.9 | MATCH | 11-04 07:00:01 | 1.0 | ThL2Cut | 67.8 | 124.8 |
| 74 | K7 | S | 11-04 11:06 | 11-04 11:08:05 | ThL2Cut | -32.8 | -33.2 | MATCH | 11-04 11:08:05 | -1.0 | ThL2Cut | 162.4 | 188.5 |
| 75 | M7 | L | 11-04 11:52 | 11-04 11:53:08 | ThL2Cut | -32.5 | -32.8 | MATCH | 11-04 11:53:08 | -1.0 | ThL2Cut | 75.3 | 92.2 |
| 76 | K7 | L | 11-04 12:27 | 11-04 12:36:43 | PolicyCut | -32.5 | -31.2 | MATCH | 11-04 12:36:41 | 1.4 | ThL2Cut | 56.9 | 83.9 |
| 77 | K7 | L | 11-04 14:09 | 11-04 14:17:26 | ThL2Cut | -29.2 | -31.2 | MISS |  |  |  |  | 68.4 |
| 78 | K7 | S | 11-04 14:33 | 11-04 15:31:33 | PolicyCut | -30.2 | -31.2 | MISS |  |  |  |  | 87.8 |
| 79 | A7 | S | 11-04 19:06 | 11-04 19:10:07 | ThL2Cut | -34.2 | -30.5 | MATCH | 11-04 19:10:06 | 0.0 | ThL2Cut | 64.5 | 77.4 |
| 80 | K7 | S | 11-04 19:27 | 11-04 19:30:26 | ThL2Cut | -32.5 | -35.0 | SIM_EARLY | 11-04 19:30:12 | 13.1 | ThL2Cut | 30.2 | 41.6 |
| 81 | A7 | S | 11-04 19:40 | 11-04 19:44:04 | ThL2Cut | -34.2 | -31.0 | MATCH | 11-04 19:43:58 | 5.8 | ThL2Cut | 38.7 | 38.7 |
| 82 | P7 | S | 11-04 19:27 | 11-04 19:57:29 | Target | 59.9 | -33.1 | FALSE_POS | 11-04 19:30:12 | 1636.1 | ThL2Cut | 30.2 |  |
| 83 | P7 | L | 11-04 21:31 | 11-04 21:34:08 | ThL2Cut | -33.3 | -31.8 | MATCH | 11-04 21:34:04 | 3.9 | ThL2Cut | 32.0 | 54.2 |
| 84 | K7 | L | 11-04 21:18 | 11-04 21:35:06 | PolicyCut | -29.0 | -33.0 | MATCH | 11-04 21:35:05 | 0.5 | ThL2Cut | 42.4 | 42.4 |
| 85 | P7 | L | 11-04 21:42 | 11-04 21:48:29 | PolicyCut | -32.9 | -31.4 | MATCH | 11-04 21:48:29 | -0.3 | ThL2Cut | 60.9 | 60.9 |
| 86 | K7 | S | 11-04 21:51 | 11-04 22:53:11 | Target | 60.0 | -30.5 | FALSE_POS | 11-04 22:06:51 | 2779.2 | ThL2Cut | 47.6 |  |
| 87 | K7 | S | 11-05 00:48 | 11-05 01:00:38 | ThL2Cut | -32.5 | -36.8 | MATCH | 11-05 01:00:38 | -0.3 | ThL2Cut | 61.5 | 63.1 |
| 88 | A7 | S | 11-05 00:52 | 11-05 01:13:43 | ThL2Cut | -44.5 | -33.0 | SIM_EARLY | 11-05 01:11:31 | 131.6 | ThL2Cut | 38.2 | 49.4 |
| 89 | P7 | S | 11-05 01:34 | 11-05 01:47:21 | ThL2Cut | -45.5 | -35.2 | SIM_EARLY | 11-05 01:47:09 | 11.5 | ThL2Cut | 30.6 | 47.0 |
| 90 | U7 | L | 11-05 02:10 | 11-05 02:16:10 | ThL2Cut | -33.1 | -33.1 | MISS |  |  |  |  | 40.4 |
| 91 | M7 | L | 11-05 02:05 | 11-05 02:22:04 | ThL2Cut | -39.5 | -37.2 | MATCH | 11-05 02:22:01 | 2.6 | ThL2Cut | 39.7 | 60.5 |
| 92 | P7 | L | 11-05 02:53 | 11-05 03:17:20 | Target | 59.9 | -30.8 | FALSE_POS | 11-05 03:03:54 | 805.1 | ThL2Cut | 34.9 |  |
| 93 | M7 | L | 11-05 02:53 | 11-05 03:17:20 | Target | 60.0 | -32.2 | FALSE_POS | 11-05 03:03:54 | 805.1 | ThL2Cut | 34.9 |  |
| 94 | M7 | L | 11-05 03:41 | 11-05 03:48:37 | ThL2Cut | -32.0 | -32.5 | MISS |  |  |  |  | 23.6 |
| 95 | P7 | L | 11-05 03:33 | 11-05 03:48:37 | ThL2Cut | -32.4 | -32.4 | MISS |  |  |  |  | 13.9 |
| 96 | P7 | L | 11-05 04:01 | 11-05 04:02:01 | ThL2Cut | -34.8 | -31.0 | MATCH | 11-05 04:02:00 | 1.0 | ThL2Cut | 38.2 | 53.5 |
| 97 | K7 | L | 11-05 03:12 | 11-05 04:09:53 | ThL2Cut | -34.8 | -31.5 | MATCH | 11-05 04:09:52 | 0.5 | ThL2Cut | 41.6 | 65.3 |
| 98 | K7 | S | 11-05 04:12 | 11-05 04:20:04 | PolicyCut | -35.5 | -32.5 | MATCH | 11-05 04:20:03 | 0.2 | ThL2Cut | 73.7 | 93.5 |
| 99 | K7 | S | 11-05 04:27 | 11-05 04:35:14 | BookLock | -42.8 | -45.8 | FALSE_POS | 11-05 04:35:03 | 10.4 | ThL2Cut | 37.4 |  |
| 100 | M7 | L | 11-05 05:08 | 11-05 07:22:47 | ThL2Cut | -37.5 | -34.2 | SIM_EARLY | 11-05 07:22:34 | 12.1 | ThL2Cut | 40.1 | 54.7 |
| 101 | M7 | S | 11-05 08:01 | 11-05 08:04:50 | ThL2Cut | -36.8 | -36.0 | MATCH | 11-05 08:04:49 | 0.3 | ThL2Cut | 34.6 | 40.3 |
| 102 | P7 | S | 11-05 07:58 | 11-05 08:04:52 | PolicyCut | -32.1 | -32.6 | MISS |  |  |  |  | 58.3 |
| 103 | U7 | S | 11-05 07:50 | 11-05 08:04:52 | ThL2Cut | -32.0 | -32.0 | MISS |  |  |  |  | 58.3 |
| 104 | P7 | S | 11-05 08:09 | 11-05 08:18:12 | PolicyCut | -31.2 | -34.2 | MISS |  |  |  |  | 35.4 |
| 105 | O7 | S | 11-05 09:42 | 11-05 09:43:07 | PolicyCut | -34.8 | -34.5 | MATCH | 11-05 09:43:07 | -0.2 | ThL2Cut | 443.7 | 448.9 |
