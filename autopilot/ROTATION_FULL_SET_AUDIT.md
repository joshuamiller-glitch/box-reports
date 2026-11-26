# Rotation on the FULL candidate set: AUDIT ONLY (no run started, no engine row computed)

Order: Josh 14:22-14:25Z via LEAD (DIRECTIVE_20261126_1432Z_ROTATION_FULL_CANDIDATE_SET.md); W-ROT, written 2026-11-26 14:34Z. The pool-books version (today's survivors) is cancelled; its scratch result is kept as autopilot/SUPERSEDED_BOOK_ROTATION_POOL_VERSION.md (+ _ROWS.csv) and is NOT an answer.
Sources: autopilot/SURVIVOR_COUNTS.md (14:22Z), /mnt/l2/l2vast/_grid/res/*/ (npz headers read, not the data), code/th_grid/gcore2.py + gjob.py, a directory scan of /mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/ (160,948 ladder / ALN set dirs, DONE files counted), ENGINE_PLAN.md, SURVIVOR_COUNTS fleet rates.

## ANSWER FIRST
1. The full candidate set exists as stored results ONLY at the quick-screen level, and there it is complete: every cell the grid scored (44.03 million: Asia 9,797,654; London 10,744,790; NY AM 11,735,921; NY PM 11,753,727) has a stored WEEKLY array from 2023-04-02 (about 187 weeks to Oct 2026), per session, both/long/short, 7 or 17 brackets. Weekly bins fit 2-week steps exactly (not daily; a weekly ulcer is coarser than the daily one, ranking only).
2. Exact-engine (daily, 41 months) results exist for only a tiny part of that set: per session a few thousand book ids at most, most of them only the last 6 months (table 2). Exact engine on the whole set is impossible (1.8 billion set-months, about 311,000 fleet-hours).
3. The honest test is therefore **two-stage**: (A) the rotation walk on the quick-screen weekly results of the ENTIRE set (needs NO new replay, only compute: a few hours on 1 server, well under an hour on the fleet), then (B) re-score only the picked books with the exact engine: about 8,000-29,000 set-months (1.4-5 h on the whole fleet at 5,800/h; 10-93 h on 1-2 servers). Everything else is far more expensive (table 4).
4. Caveats Josh must see: the quick screen is not calibrated against the exact engine (stop / target tape walk, one position, no account layers, no depth / size-dependent fills); 13 of 17 level modules had stale pre-06:00Z grid results being re-run (UNVERIFIED rows until stamped); weekly not daily.

## 1. Candidates with stored results, per session, and the ladder stage reached

| session | cells scored (R0 quick screen, weekly arrays stored) | R0 passers now (cells / families) | exact-engine book ids with any stored set (ALN bare/R1/fit sets + ladder sets, not de-duplicated across the two families) | of which a set with >= 40 of 41 months | only <= 6 months (L6M) |
|---|---|---|---|---|---|
| Asia | 9,797,654 | 6,487 / 3,847 | ALN 4,537 + ASI ladder 3,356 | 3,136 + 84 | 1,401 + 3,205 |
| London | 10,744,790 | 3,158 / 2,237 | ALN 669 + LON ladder 2,296 (+ LYR 10) | 280 + 209 (+5) | 389 + 2,080 |
| NY AM | 11,735,921 | 24,702 / 11,460 | ALN 6,178 + NYE ladder 9,102 (+ NYW 307, NYL 51) | 4,084 + 891 | 2,094 + 8,139 |
| NY PM | 11,753,727 | 1,638 / 1,168 | ALN 544 (NY PM ladder sets sit inside the NYE / NYW names, not separable by name) | 427 | 117 |

Ladder stage reached (SURVIVOR_COUNTS): R0 bare quick-screen rule for every cell (done); R1 own-stop NOT run for the full grid (only ~1,700 pairs carry the arrays); R2 trust/look-ahead not run; R3 random-entry draws RUNNING (Asia 3,936 family-bests tested of 3,847 listed, London 806 of 2,237); R4 null not started as a full set; R5a exact engine L6M + L3M only for the family-bests that were queued ("engine rows on disk only for the leads"), prior years only for rows alive after that. So: an exact full-history book is a lead or a survivor; the other 99.9% of cells are quick-screen only.
Truly bare R0 exact sets (the ones used in the cancelled pool test), by name TL3_ALN_<S>_<id>_R0*: Asia 642 complete + 816 partial; NY AM 950 + 866 partial (NY AM and NY PM names both under NY); London 95 + 172; NY PM 80 + 60. Partial = not all 41 months landed.

## 2. Daily or monthly, and how much history per candidate

| result type | resolution | history per candidate | covers 2023-2026? |
|---|---|---|---|
| grid quick screen (npz A[param, bracket, week 0..199, session, mode, side]) | WEEKLY (week = 7-day bin from 2023-04-02), per session | all ~187 weeks from 2023-04-02 for EVERY cell | yes, all cells |
| exact engine month dirs (runs_rf/<set>/<YYYYMM>/trades.parquet) | trade level, so daily is derivable | R0 / BASE / CANC full sets: 41 months (202304-202610 minus 202511, tape hole); ladder sets mostly L6M = 6 months only | only the "full" counts in table 1 (Asia 3,136 + 84; London 280 + 209; NY AM 4,084 + 891; NY PM 427 ids); the rest cannot be ranked at 2024 dates |

Two-week steps need weekly or finer: the quick-screen weekly array is enough; monthly aggregates are not used anywhere. A candidate scored only on L6M cannot be ranked before May 2026; that excludes about 40-95% of the ids that have exact rows (table 1).

## 3. Fill model per stage

| stage | fill model |
|---|---|
| R0 / R1 / R2 / R3 (all grid cells, weekly arrays) | QUICK SCREEN (th_grid/gcore2.py, trade-for-trade identical to the older gcore run_multi): second-level tape walk on raw prints, entry = first print >= signal + 1 s plus slip ticks adverse, stop = first print at/through the stop (exit 1 tick through), target = first print 1 tick THROUGH the level, session end = last print before end; one position per bracket; equal-risk units R = points / stop (stop clipped 10..120 pts); screen cost points; JL3 day-done mask on the grid side. No account layers, no depth / size-dependent fills. NOT calibrated against the engine (SURVIVOR_COUNTS says so). |
| R5a and ALN sets (exact engine, runs_rf) | EXACT engine (sim.Replica with the mf_multi / hook chain; replica of the live path): R0 sets = truly bare, own bracket, 1 lot, fees, no D7 layers; BASE / CANC / ladder ADD / REPLACE sets = JL3 stack with account layers ON (R1 wrapper), so those rows are stack deltas, not independent streams. |

## 4. New replays the full-set test would need, hours, cheapest honest variants

Rates: whole fleet 5,800 set-months (rows) per hour (as given in the order); measured engine today 763 set-months/h on two servers (box 1 450 + Dallas 313; SURVIVOR_COUNTS); one server 313-450/h. 41 months per full-history set.

| variant | new set-months | whole fleet @5,800/h | two servers @763/h | one server @313-450/h |
|---|---|---|---|---|
| E. exact engine for EVERY cell (44.03 M cells) | 1.80 billion | ~311,000 h | impossible | impossible |
| D. exact for every R0 passer (35,985 cells) | 1.48 M | 254 h | 1,930 h | 3,300-4,700 h |
| C. exact for every passer family-best (18,712 families: Asia 3,847, London 2,237, NY AM 11,460, NY PM 1,168) | 767 k | 132 h | 1,005 h | 1,700-2,450 h |
| **B. quick-screen weekly walk on the WHOLE set, then exact only for the picked books (recommended)** | stage A: 0 replays (compute only, reads ~95 GB of stored npz; ranking 44 M cells x 80 dates x 5 lookbacks via cumulative sums: ~2-6 h on 1 server, < 1 h on the fleet). Stage B: each pick-date needs one month-run to cover its 2 held weeks, shared by persistent picks: about 8,000-29,000 set-months (upper bound 80 dates x 4 sessions x ~60 distinct picks x 1.5 months) | 1.4-5 h | 10-38 h | 18-93 h |
| A. quick-screen walk only (no exact stage) | 0 | compute only | compute only | compute only |
| fewer dates (4-week steps) | halves stage B, not stage A | | | |

Honest reading: the whole-set test is the quick-screen walk (variant A, then B for the picks). Anything that insists on exact daily results for the whole set is not feasible; for the passer families alone (C) it is 132 fleet-hours at the optimistic rate and about 1,000 hours on today's measured two-server rate.

## 5. How near-duplicates are skipped (cluster rule)

At each date, walk the ranked list from the top and take the next candidate that is not a near-duplicate of one already picked:
1. same FAMILY id (the grid's own connected-component rule: same module.variant on an adjacent bar size of the same bar type, adjacent parameter of the same variant, or the same parameter with another bracket or side) -> skip;
2. identical-signal twins (twin_ids.csv in _asi_lad, id_twins.csv in _nye: same events hash) -> counted once;
3. weekly-return correlation with any already-picked book >= 0.8 over the trailing lookback (and over the last 26 weeks) -> skip (for the exact stage, daily correlation).
Passers collapse about 36,000 cells to 18,700 families (x0.52); the same rule is applied to the ranked list at each date, not to a fixed pre-list (a pre-built list would be today's survivors again). The correlation threshold is a choice: stated before any run, and the result shown at 0.7 / 0.8 / 0.9.

## 6. What waits for Josh
Nothing started. If Josh says go: stage A first (no replay): I write the walk exactly as the order lists it (lookbacks 1/3/4/5/6, top 3/5/8 with the cluster rule, with and without the prior-year filter, against the held mixes Asia four / NY AM nine / NY PM four / London three) on the weekly quick-screen arrays of the whole set and report it labelled QUICK SCREEN, then ask for the exact stage for the picked books.
