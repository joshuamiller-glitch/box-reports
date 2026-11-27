# LOOP C BEHAVIOUR TABLE: quick screen (fixed fills) vs exact engine, Asia MF1, same months (order 1530Z item 1) (W-DYNML)
Forward months 2024-04 .. 2026-10 (grid weeks 52-181), BOTH SIDES (the live MF1 trades long and short in one position slot), the SAME model bundle the engine ran (hook-feature models, loss mode, theta 0.2, 13-week refit, safety stop 1.5 x 40 pts, no target), the quick screen with the corrected fill (a stop set through the market = market exit). $ are per lot (engine: net_fee / 6 lots incl. fees; screen: points x 20 minus 4.84). Engine sets TL3_DX_AS_MF1_LCC13L_A (loop) and TL3_DX_AS_MF1_SAFE15_A (safety only). Screen code th_dynml/dml_behaviour.py.

## Answer first
With the fill bug fixed and BOTH sides in one slot, the quick screen reproduces the engine's behaviour: entries 1,508 vs 1,514, trades per week 11.4 vs 11.4, re-entries after a managed exit 621 vs 599, actions per trade 0.58 vs 0.58, stop-type exits 866 vs 864, safety-only entries 1,020 vs 1,054 and safety-only total $6.1k vs $6.1k per lot. The earlier 'pass' came from (1) the stop-fill bug (free fills at a level above the market) and (2) comparing long-only screen trades with an engine that trades both sides in one slot. The loop does lift the no-target safety-only run ($6k to $34k screen, $6k to $57k engine per lot), but the book's own bracket + target earns much more ($782k at 6 lots = $130k per lot whole forward): the lift was against the wrong reference.

| row | signals seen | entries | skipped (position open) | re-entries after a managed exit | trades/week | actions/trade | total $ per lot |
|---|---|---|---|---|---|---|---|
| ENGINE safety only (SAFE15) both sides | 7,922 | 1,054 | 6,868 | 0 | 7.95 | 0 | 6,086 |
| QUICK SCREEN safety only, fixed fills, both sides | 7,680 | 1,020 | 6,660 | 0 | 7.69 | 0 | 6,073 |
| ENGINE loop LCC13L both sides | 7,922 | 1,514 | 6,408 | 599 | 11.42 | 0.58 | 57,195 |
| QUICK SCREEN loop (same bundle, fixed fills), both sides | 7,680 | 1,508 | 6,172 | 621 | 11.37 | 0.58 | 33,751 |

How trades ended (count, $ per lot summed):
| exit | engine loop | quick screen loop (fixed) |
|---|---|---|
| loop take-all | 46, -15.4k | 55, -16.0k |
| stop-type (safety stop or the trail/tighten level hit; screen: Stop + trail set through the market, which the engine books as Stop) | 864, -509.3k | 866, -503.4k (Stop 183, -134.5k; trail through market 683, -368.9k) |
| session-time exit (engine UWTime + RollFlat) | 604, +581.9k | 587, +553.2k |

Long side only (the old comparison): engine 775 entries of 4,051 signals; screen (long-only slot) 1,203 of 3,951: different populations, which is why the first table looked inconsistent.

## Where the loop's gain came from (and its size)
1. Versus safety-only no-target holding the loop is better in both (engine +$51k, screen +$28k per lot): it exits losers before the 1.5x stop (the trail-through-market exits at about -1.1 R) and frees the slot for re-entries (599-621 re-entries).
2. Versus the book's own bracket + target it is much worse in the engine (income -62%, DD $228k vs $111k): the bracket's target harvests the winners the loop lets run to session end.
3. The quick-screen 'lift over the own bracket' (62.9k to 202.6k) was the fill bug: free fills at the trail level.
4. Remaining difference engine vs screen ($57k vs $34k per lot): not explained yet (fills at the second close vs the engine's latency, 6-lot book walk, UW time exits vs my session end); same structure, not the same dollars.

## Forced runs with W-DYNH (1530Z item 2): files delivered
(a) screen's entry list and action schedule, long-only population: box1 /mnt/l2/l2vast/_dynexit/qs_export/AS_MF1_bundle_* and AS_MF1_fixedmodel_* (see LEAD NOTE 20:50Z). The both-sides version of the entry list is the next export if W-DYNH wants it (the screen above is both sides). (b) engine entry logic with L1/L0 and (c) own target kept: for W-DYNH's builder; the loop code path is unchanged.

## Status of ideas
Everything about learned loss-side management is UNTESTED IDEA until the engine shows a candidate; the bare-entry design (1529Z) is next: dataset of every bare-trigger signal, label = advantage over the book's own bracket outcome, 60 s and 15 s states, equality test of the screen's and the hook's action on 400 states before any fit.
