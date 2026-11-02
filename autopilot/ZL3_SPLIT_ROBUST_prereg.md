# PREREG ZL-3 execution-robust split family on V13T (written 2026-11-02 before any V13T statistic of these designs)
Base V13T = D7 V13Z with lines off (`run_v13z(ov={'lines':'empty'}, lock=None)`), lock none headline (no combined lock live). Add-fill ordering fix and cancel-on-exit are in the base (user answers 13:30Z). Market-exit cost 0.80 +- 0.22: sensitivity only (see section 5).
## 1. Designs (all keep F per book, the L2 class gate, veto bit 45; the add lots sum to the shipped risk-equal add a = (1-F) sd/(fill-stop) split by weights)
S0 shipped: one add, trigger first second with adverse >= 3.0 pts, market order sent 1 s later (fill = close of the send second + 1 tick).
S1 ladder3: three rungs w = 1/3 each at X = 2.5 / 3.0 / 3.5 (each rung its own trigger and market fill).
S2 ladder2: two rungs w = 1/2 at X = 2.75 / 3.25.
S3 band: one rung, trigger at the first second with 2.5 <= adverse <= 3.5.
S4 delayed: S0 with the send delayed 2 extra seconds.
S5 wide ladder3: X = 2 / 3 / 4, w = 1/3.
Exit rules: rungs that would fill after the (rebased-target) exit are not filled (fixed point, <= 4 iterations); target re-based on the average fill as in the shipped kernel.
## 2. Execution scenarios applied to every design (kernel-level): add fill 1 tick worse; 2 ticks worse; send 1 s later; 3 s later; 75% of add lots fill; 50% fill; combined (1 tick worse + 3 s later); combined+ (1 tick worse + 3 s later + 50% fill).
## 3. Metrics (drawdown first, lock none, V13T): weekly-cumulative maxDD in L3M, L6M, HOLD, MID, PRE, X'; worst-20 where n>=20 weeks; mean change and MDE; STRICT/TOLERANT/NOW-ONLY from z2lib tiers. Reference edge E_L6M = maxDD(market entry F=1) - maxDD(S0, no friction) on L6M; retention(design, scenario) = (maxDD(market) - maxDD(design, scenario)) / E_L6M.
## 4. Pass bar (all required): (a) retention >= 0.70 on L6M under the combined scenario (1 tick worse + 3 s later); (b) PRE maxDD (no friction) not worse than S0; (c) mean change L6M under the combined scenario not below -1 MDE of S0 under that scenario; (d) the same sign of the retention in HOLD; (e) placebo: for the winning design a random-dip placebo (per row the trigger X redrawn at random from {1,2,3,5}; 10 seeds, same fill model) with the design's L6M retention above the placebo's 90th percentile; (f) purged walk-forward on the design choice (each month from 2024-01, choose among S0..S5 by trailing-12-month no-friction maxDD (tie -> S0), apply next month) not worse than always-S0 in the 2024-01..2026-10 total and maxDD; (g) per book x session: no book x session slice with base maxDD > $20k where the design is worse than S0 by > 25% of that slice's maxDD in L6M.
## 5. Sensitivity (not a gate): market-exit cost 0.80 vs the engine's 0.995 on cut/take exits (estimate from exit counts); cancel-on-exit variants are already in the base.
## 6. Multiplicity: 6 designs x 8 scenarios = 48 cells, no other designs will be added after seeing results; any later design is a new prereg.
