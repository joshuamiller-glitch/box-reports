# DS3_THL2_NEEDS - features a winning L2 policy would need that D6 does not compute (L2H, 2026-10-29)
No hypothesis reached CANDIDATE, so no winning feature is missing from D6 (imb5, imb10, wall_tgt, wall_stop, delta60 + path set): the set was sufficient for every rule that was tested and none of them beat hold. What the test showed about the existing features:
* **wall_tgt / wall_stop carry nothing in mbp-10.** Finite in 0.05% of profit-side seconds (19,021 of 39.5 M rows) and 0.04% for wall_stop; the 10 visible levels cover ~2.5 pts, the brackets are 33-60 pts. If D6 reads a deeper live ladder (NT8 depth beyond 10 levels, or MBO), the right test is H1-true (size AT the target at 50/70% of the way) and H2-true (size between price and stop); the research library cannot test it without an MBO deep-book rebuild of the book at the target price. Request to whoever owns the MBO replay: size resting at the trade's target and stop price, plus level age, sampled every 10 s in-trade, from MBO (not mbp-10).
* Normalised depth, if anyone wants to re-test H8 later (not recommended): `depth_rel` = total resting size, 8 ticks each side of the touch, divided by the median of the same quantity at the same ET hour over the prior 20 label days (min 5 days), 10-s sampling, side-free. D6 does not compute it; the H8 gate adds +0.28 [-0.24,+0.81] PRE and +0.18 [-0.57,+0.92] HOLD over the plain path rule, i.e. nothing.
* Nothing else is requested: sweep counts (H7), queue consumption/refill (H4), iceberg flags (H5), pulled size (H6), OFI30 (H9) and microprice offset (H10) were tested and did not carry a policy.
* **ES book imbalance** (es_imb5: (bidES5 - askES5)/(bidES5 + askES5) over 5 ES levels, sided with the NQ trade, 10-s sampling; D6 does not compute it) carries the largest descriptive reading in map B (loser L6M adjusted decile spread +7.85 pts, t +4.0) but NO rule built on it (H12) beats hold; do not add it to D6 on this evidence.

## L2EA (entry-side) additions, 2026-10-29
Entry policy uses only imb5, imb10, delta60, curDepthRel (rel_tot8 8-tick), pulled_sup10 (all computed by D6 tonight). NOT in D6 and needed if any other L2EA rule is ever promoted: rnd100_ahead (ticks to the next 100-point round number ahead of the entry), spread_t (spread at the signal second), pulled_opp10, depth_rel (10-level, sided), vpin50 (volume-clock VPIN over 50 buckets), rel_ahead8 / rel_behind8 (8-tick depth ahead/behind vs same-ET-minute median of prior 20 label days), es_imb5 (ES 5-level imbalance). None promoted (all V2 DEAD).

## L2SL (selective loss-health) additions, 2026-10-30T00:36Z
Features NOT computed by D6 that the loss_policy_candidate.txt lines use (D6 computes pct, imb10, pulled_sup10; all windows end at the decision second, side = supporting side of the trade):
* **pulled_sup5**: size cancelled over supporting-side levels 1-10 in the last 5 s (long: bids, short: asks), MBO/mbp-10 cancel events, window ends at the decision second
* **pulled_sup30**: same as pulled_sup10 over the last 30 s
* **medOwnLevel**: median of the own-side (supporting side: long bids / short asks) L1..L10 sizes at the decision second
* **pulledShare5**: pulled_sup5 / (pulled_sup5 + sum of own-side L1..L10 sizes now); same for pulledShare10, pulledShare30
* **newAdvExt5**: 1 if the 1-s adverse excursion in the last 5 s set a new maximum adverse excursion of the trade (exceeds the running max over entry..T-5 s); newAdvExt10, newAdvExt30 likewise
* **icebergAgainst**: 1 if iceberg_flag_ahead: size traded at the best AHEAD (against a loser: asks for a long, bids for a short) in 10 s >= 10x the displayed best size (refill rule of l2feat)
* **sweepAgainst10**: count of trade-driven touch clears (>= 2 levels consumed) by the adverse aggressor in the last 10 s
* **ownDepth10Rel**: sum of own-side L1..L10 sizes divided by the median of that quantity at the same ET hour over the prior 20 label days (min 3 days) (l2feat cum_behind10_rel)
* **leadCount2of4**: icebergAgainst + (sweepAgainst10>=1) + (ownDepth10Rel<=0.5) + (imb10<=-0.3)

## L2SP profit-health additions (2026-10-30)
Published profit rules (l2vast/ds3/out/l2set/profit_policy_candidate.txt) use only `pct` and `curDepthRel` (= rel_tot8: total resting size over 8 ticks each side of the touch / median of the same quantity at the same ET hour over the prior 20 label days, min 5 days). Everything else below is NOT computed by D6 and is needed only if a cell that uses it is ever promoted (no cell reached CANDIDATE; every pooled cell fails the no-target-correction basis in PRE+HOLD):
* `rel_ahead8` (ahead-side 8-tick depth / same-ET-hour median of prior 20 label days; ahead = asks for a long, bids for a short);
* session-median normalisation (row's ET session [asia <02:00 or >=18:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-15:15], median of prior 20 label days);
* trailing-60-min median of tot8 / ahead8 (strictly before the row, >= 60 samples of the 10-s feed);
* z-score of tot8 / ahead8 vs the same ET-30-minute bucket of the prior 20 label days (centre = median of bucket medians, scale = 1.4826 x median of bucket MADs);
* thick-duration latch (consecutive 10-s samples 2 / 4) and a latched MFE arm in points (`mfe_pts >= X`); in the policy syntax the arm is approximated by current `pct >= X / target`;
* actions: take-half-plus-trail-half and `tighten to +X locked` (stop at entry + X); the vocabulary is take | cut | tighten X only.
Widening the target when the book ahead is thin cannot be tested on the 10-s store (needs the post-exit 1-s price path); not requested.
