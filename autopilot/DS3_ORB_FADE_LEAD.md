# DS3_ORB_FADE_LEAD - N1_ORB_LIM fade (OR=15, ctx=with, lim=4) exit 40/90, NY AM, both sides, injected on JL3 (W-ORB)

**FIVE-LINE PLAIN SUMMARY (refreshed 2026-11-27 20:32Z by the unattended loop)**
1. Tried: the one NQ LEAD of the shelf re-read (opening-range fade, 15-min OR, with-trend context, 4-point resting limit, stop 40 / target 90, 2 base lots) injected into the live-equivalent stack JL3 on the exact engine (events 261, limit fill model through-print + 0.5 pt).
2. Status: identity of the hook PASS; engine months landed L6M 6/6, L3M 3/3, HOLD 6/6, pooled 43/43; label now: LEAD (controls 10/30 valid: cannot be CONFIRMED).
3. L6M: mean $/wk +19933 vs JL3 18755 (base lots), ulcer 9242 vs 9416 (-2%), max DD -31109 vs -31109; trades of the book 28.
4. Needs in D7: new code (event book with own cap, resting limit entry) - nothing is delivered unless the label is LEAD or better with controls.
5. Next: 10 date-shifted controls (queued), 20 more draws needed for 30; older months; refit date 2026-11-17, next 2026-12-01.

**Header:** pick window end 2026-11-01 (shelf pick, trailing 26 weeks), refit 2026-11-17, data end of engine months 2026-10-31; trials: 1 pre-registered LEAD from 31,168 shelf/F cells (best-pick null p90 33.1 vs 33.4 R: marginal); walk-forward from the shelf re-read, engine rows are unselected re-runs; PBO not computed. Prereg autopilot/PREREG_ORB.md. Fees $4.84 RT (engine base lots; x1.75 live-lot column). Labels per DS3_PASS_RULE.md; FIRST PASS.

## Engine table vs JL3 (months landed only; ulcer first)

| window | months | ulcer with / JL3 (chg %) | mean $/wk with / JL3 (base) | x1.75 mean $/wk delta | max DD with / JL3 | worst wk with / JL3 | book trades | freed-book effect (other books mean $/wk) | flag vs JL3 |
|---|---|---|---|---|---|---|---|---|---|
| L6M | 6/6 | 9242 / 9416 (-2%) | 19933 / 18755 | +2062 | -31109 / -31109 | -14838 / -15728 | 28 | -96 | n/a (worse = ulcer up or mean down, AMBER>15 RED>30) |
| L3M | 3/3 | 10749 / 11035 (-3%) | 18178 / 16098 | +3640 | -31109 / -31109 | -14838 / -15728 | 15 | -199 | n/a (worse = ulcer up or mean down, AMBER>15 RED>30) |
| HOLD | 6/6 | 30250 / 29373 (+3%) | 8931 / 9280 | -612 | -84358 / -83756 | -37333 / -37324 | 32 | -64 | n/a (worse = ulcer up or mean down, AMBER>15 RED>30) |
| 2026 | 10/10 | 15149 / 15024 (+1%) | 17067 / 16553 | +900 | -58792 / -58740 | -20963 / -19819 | 50 | -84 | ok (worse = ulcer up or mean down, AMBER>15 RED>30) |
| 2025 | 12/12 | 34715 / 33572 (+3%) | 6763 / 6846 | -144 | -95611 / -91441 | -39137 / -38896 | 54 | -69 | ok (worse = ulcer up or mean down, AMBER>15 RED>30) |
| 2024 | 12/12 | 31943 / 28856 (+11%) | 4038 / 4549 | -894 | -74796 / -72026 | -37355 / -37355 | 60 | -0 | ok (worse = ulcer up or mean down, AMBER>15 RED>30) |
| 2023 | 9/9 | 16629 / 18922 (-12%) | 1925 / 1797 | +225 | -38624 / -41848 | -17538 / -17538 | 41 | +0 | ok (worse = ulcer up or mean down, AMBER>15 RED>30) |
| PRE(2023-04..2025-10) | 31/31 | 28810 / 27526 (+5%) | 4653 / 4849 | -344 | -95611 / -91441 | -39137 / -38896 | 145 | -23 | ok (worse = ulcer up or mean down, AMBER>15 RED>30) |
| pooled | 43/43 | 27140 / 26032 (+4%) | 7479 / 7499 | -35 | -95611 / -91441 | -39137 / -38896 | 205 | -40 | n/a (worse = ulcer up or mean down, AMBER>15 RED>30) |

## Controls (10 date-shifted, same rule on shifted days; L6M, complete months only)

| control | mean $/wk delta vs JL3 | ulcer chg % | book trades |
|---|---|---|---|
| TL3_MF_N1ORBLIM_CT7p | -213 | +1 | 29 |
| TL3_MF_N1ORBLIM_CT11p | -467 | +1 | 22 |
| TL3_MF_N1ORBLIM_CT13p | -385 | +5 | 19 |
| TL3_MF_N1ORBLIM_CT17p | +301 | +2 | 24 |
| TL3_MF_N1ORBLIM_CT19p | -31 | +1 | 26 |
| TL3_MF_N1ORBLIM_CT23p | -124 | +1 | 20 |
| TL3_MF_N1ORBLIM_CT7m | +94 | +0 | 19 |
| TL3_MF_N1ORBLIM_CT11m | -380 | -1 | 27 |
| TL3_MF_N1ORBLIM_CT13m | -158 | -0 | 16 |
| TL3_MF_N1ORBLIM_CT17m | -128 | -1 | 25 |

real delta +1178 $/wk, ulcer -2%; real rank by mean 1/11. Valid 10/30 needed: NOT FINISHED, no CONFIRMED.

Identity: 202610 PASS (691 vs 691 trades, 37159.82 vs 37159.82); 202504 PASS (637 vs 637 trades, 41239.76 vs 41239.76) (expected 691/37,159.82 and 637/41,239.76 at engine fee $1.18).

Caveat: shelf standalone is 1-min sim (entry next bar +1 tick); the engine injection is a resting limit with tape-through fill, so trade count and fills differ; 2026-11 months not in the engine set.
