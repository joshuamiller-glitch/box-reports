# DS3_ORB_FADE_LEAD - N1_ORB_LIM fade (OR=15, ctx=with, lim=4) exit 40/90, NY AM, both sides, injected on JL3 (W-ORB)

**FIVE-LINE PLAIN SUMMARY (refreshed 2026-11-18 09:58Z by the unattended loop)**
1. Tried: the one NQ LEAD of the shelf re-read (opening-range fade, 15-min OR, with-trend context, 4-point resting limit, stop 40 / target 90, 2 base lots) injected into the live-equivalent stack JL3 on the exact engine (events 261, limit fill model through-print + 0.5 pt).
2. Status: identity of the hook NOT PASSED YET; engine months landed L6M 0/6, L3M 0/3, HOLD 0/6, pooled 0/43; label now: NOT FINISHED (identity pending/failed).
3. L6M engine rows not complete yet (queue file /mnt/l2/l2vast/_orb/pending.txt, recent months first).
4. Needs in D7: new code (event book with own cap, resting limit entry) - nothing is delivered unless the label is LEAD or better with controls.
5. Next: 10 date-shifted controls (queued), 20 more draws needed for 30; older months; refit date 2026-11-17, next 2026-12-01.

**Header:** pick window end 2026-11-01 (shelf pick, trailing 26 weeks), refit 2026-11-17, data end of engine months 2026-10-31; trials: 1 pre-registered LEAD from 31,168 shelf/F cells (best-pick null p90 33.1 vs 33.4 R: marginal); walk-forward from the shelf re-read, engine rows are unselected re-runs; PBO not computed. Prereg autopilot/PREREG_ORB.md. Fees $4.84 RT (engine base lots; x1.75 live-lot column). Labels per DS3_PASS_RULE.md; FIRST PASS.

## Engine table vs JL3 (months landed only; ulcer first)

| window | months | ulcer with / JL3 (chg %) | mean $/wk with / JL3 (base) | x1.75 mean $/wk delta | max DD with / JL3 | worst wk with / JL3 | book trades | freed-book effect (other books mean $/wk) | flag vs JL3 |
|---|---|---|---|---|---|---|---|---|---|

## Controls (10 date-shifted, same rule on shifted days; L6M, complete months only)

none finished yet.

Identity: 202610 pending; 202504 pending (expected 691/37,159.82 and 637/41,239.76 at engine fee $1.18).

Caveat: shelf standalone is 1-min sim (entry next bar +1 tick); the engine injection is a resting limit with tape-through fill, so trade count and fills differ; 2026-11 months not in the engine set.
