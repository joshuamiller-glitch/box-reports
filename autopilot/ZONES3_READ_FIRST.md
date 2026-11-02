# ZONES-3 READ FIRST (lead, ~12:55Z 2026-11-02; refreshed at 18:00Z / 00:00Z / 03:00Z Tue)

## Bottom line
- The shipped zone layer (HALF D20 on the 7 coded lines + OTE-62 B73 D30) is NOT improved by anything we found. Its recent-year (Feb-Oct) drawdown benefit is mostly the size effect of halving ~10-12% of signals (indistinguishable from random halving at equal risk in F9/L6M/HOLD on the corrected base); its PRE edge (2024-02..2025-06) is real vs random halving on every base (ranks 0.00-0.06; 4-9 of 42 PRE slices beat chance vs 2.1 expected).
- A monthly-refit zone file does NOT beat the fixed layer (both lock frames).
- ~9,000 scored cells across 663 POI streams, density, order-book, tape, profile lines (36 streams, 576 runs), session structure, round numbers, gaps/FVG, flip families, break-with-trend, size-up, learned rules/trees: NONE survives the noise band + no-harm + same-volume placebo + carrying-week drop together. The screens are at chance (5.2% positive in L6M/PRE/X' vs 5.7-7.7% for random masks).
- ONE candidate survives every test so far, and it is MEAN-type, not a drawdown cut: the BT swing flip skip (Shadow only). Independent clean-room reproduction (Jaccard .917/.983), robust to the fill basis and to removing the take lines, delay-robust, all 4 calendar years positive, beats 1,980 (not count-matched; count-matched null running) null families. Definition: autopilot/DS3_BT_SWING_FLIP_CANDIDATE.md sec 13; forward check script code/zones3/bt_forward_check.py; Shadow log schema in FORWARD_SHADOW_ZONES_SPEC.md. LP_AGAINST (large print against the trade) is NOISE-leaning (its dollars are a take-line interaction).

## Base corrections that changed answers (all earlier tables carry a base label)
1. V13X -> V13Y: engine dropped TH-L2 loss cuts / take-line exits that preceded the resting-add fill (846 rows; B73 and generic 70/30 split).
2. V13Y -> V13Z (nfix): early-exit deltas were credited the 3.39 pt/lot target-fill cost; on basis N (live fills show targets fill at nominal, 11/11) the five D7 take lines LOSE money (~-19k/wk F9) and the exact D7 v1.3 base is far weaker than lines-off (F9 14.6k/182.8k vs 33.7k/132.1k). They pay only if live targets miss by >= ~2.2-2.8 pts (DS3_TAKE_COST_SURFACE_V13Z.md).
3. U7 exact never binds (our earlier all-books blackout was an assumption). The combined 12R stack lock (not in the user's text) creates many 'LOCK-ONLY' cuts; maxDD under it is lock-phase noise (a +-2-day shift moves it up to 2x).
4. The 70/30 entry split stays but its edge is fragile: X=3 is a spike; the add is a market order 1 s after the trigger; edge roughly halves under 1 tick worse / partial fills.

## Decisions needed from the user (open since this morning)
1. Fill basis for early exits (N: targets fill at nominal; M: ~3.4 pt shortfall): give your avg market profit-exit cost and avg shortfall of filled touched targets. On N the take lines should be reconsidered.
2. Does live D7 cancel the resting 30% when the 70% exits first (TH-L2 cut / take)? (engine did not; DS3_B73_ORDERING_NOTE.md)
3. Does live D7 carry the combined 12R stack lock on top of per-book week floor, day give-back and ER(20)?
4. Live L2 grid for the take lines (1 s vs 10 s) and the live definition of ahead_rel / tot_rel (D6 does not compute rel_ahead8).
5. THP_POLICY_D7.txt mapping: U7=SM, P7=PE (assumed from tags); K7/H7/M7=K6/H6/M6.
6. Proposals (not started): execution-robust split; P7 (PE) Asia risk control; a plain-pct take rule only if basis M is true.
7. Open the BT swing flip as a Shadow log in D7 (5-min bars + prints only)? and/or in the forward register from Mon 2026-11-02.

## Where things are
DS3_ZONES_3.md (sections 0-18, newest wins), MORNING_FLAGS.md (every flag and its updates), ZONES3_MASTER_TABLE.md + ZONES3_LEAD_REGISTER.md (S5), DS3_ZONES_3_SURVIVORS_V13Y.md (Z3), DS3_ZONES_3_CLAIMS_AUDIT.md (Z3 recomputed all headline numbers: match), per-agent pages (S1..S5, L2_*, B5_MANCINI, B73_GENERIC, D7_SPLIT_V13Y, LOCK_AUDIT, PHASE_AVG, NOISE, EPISODES_V13Y, V13Y/V13Z base + change table).
