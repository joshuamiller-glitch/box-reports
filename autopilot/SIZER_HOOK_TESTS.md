# SIZER HOOK TESTS (BASE-4, 2026-11-02T14:47Z)

**Hook:** `V13T.run_v13t_live({'lots_mult': array(n=88,490 d rows), 'lots_round': 'single'|'sequential'})` replaces the ER(20) ladder with your per-signal multiplier array (NaN -> 1.0); the zone HALF factor (0.5 on the 7-line set), integer half-up min-1 lots and the governor (unrounded multiplier, running-max over taken signals) stay in the engine. `V13T.er_ladder_mult()` returns the live ladder by d row (x1.5 if ER >= 0.30 else x0.5, captured from the engine). `lots_round='sequential'` rounds the zone-halved session lots first (7 -> 4) and then multiplies by your sizer and rounds again (4 x 1.5 -> 6); the governor sees (rounded zone lots / session lots) x sizer. Costs: nothing else changes (V13T_LIVE).

1. lots_mult = the captured live ER ladder reproduces the default run: max|cube diff| = 0.0000 $ (single rounding).
2. lots_mult = ones (flat 1.0 sizer) equals the d7lib er=False run: max|cube diff| = 0.0000 $.
3. Ladder vs S4b per-row table (SIZER_LIVE_DEF, 18384 taken signals, independent ER(20) values): multiplier ER-ladder x zone factor matches S4b "mer" on 18384 of 18384 rows; ER>=0.30 -> x1.5 / else x0.5 rule applied to S4b's raw ER gives 18384 of 18384 matches with S4b mer.
4. Integer rule on S4b rows: single rounding (engine) reproduces S4b eff_lots on 18384 of 18384; sequential rounding (zone halve, round, x ER, round) differs from single on 353 rows; among zone rows 353 of 2606 (S4b: 353 of 2,606; PE 163 of 505: PE zone rows here 163 of 505); mean lots single 3.162, sequential 3.181.
5. Engine run with lots_round="sequential" (hook: zone-halved lots rounded first, then x ER, rounded once; governor multiplier = rounded-zone x ER): total 3475k vs single 3482k ($ over the whole history), max|cube diff| 19399 $/cell; L6M mean/maxDD single vs sequential below.

| variant | F9 | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| single (engine/live-as-coded) | 33.7 / DD 151 / w20 -307 | 36.7 / DD 151 / w20 99 | 30.4 / DD 151 / w20 -575 | 17.3 / DD 166 / w20 -790 | 4.8 / DD 92 / w20 -447 |
| sequential (7->4->6 style) | 33.2 / DD 158 / w20 -339 | 36.7 / DD 158 / w20 95 | 30.0 / DD 158 / w20 -606 | 17.4 / DD 169 / w20 -800 | 4.9 / DD 74 / w20 -445 |
| flat 1.0 (sizer off) | 19.9 / DD 135 / w20 -329 | 26.2 / DD 81 / w20 74 | 21.1 / DD 192 / w20 -514 | 13.8 / DD 120 / w20 -682 | 4.9 / DD 120 / w20 -358 |


Use: `m = my_sizer_array(d)`; `r = V13T.run_v13t_live({"lots_mult": m})`; compare with `V13T.run_v13t_live({})` (the live ER) and `{"lots_mult": np.ones(n)}` (sizer off). For equal-risk comparisons add `lscale`.