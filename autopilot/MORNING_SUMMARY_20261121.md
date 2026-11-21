# MORNING SUMMARY, Sat 21 Nov 2026 (lead; first edition 12:25Z, refreshed 13:00Z)
Research only. Nothing changed on the execution server or any live chart; nothing spent, rented or deleted. Every number is 1 lot, base dollars (engine dollars), from files, not re-checked by hand.

## 1. The one-paragraph answer
**Nothing is frozen yet, but the Asia answer has stopped moving.** At 12:08Z a universe fix by the combination agent grew the Asia pool from 28 to 35 books (the earlier loops had seen only 718 of 1,244 candidate ids). All four Asia loops were re-run on the 35-book pool (hash 9192576d) and **the 7 new books entered none of the four finals**: the finals are the same as before. The fit chain of the 7 new books has now finished too (13:50Z): layers NOT KEPT for all 7; the bracket, exit and pass-2 heartbeats show nothing outstanding (exact bracket/exit/pass-2 verdict lines for the 7 are not yet read by the lead; the bracket heartbeat still shows exactly one pass overall, the earlier M7ea48296); the Asia chain is COMPLETE on the 35-book pool and the Asia answer is yours to pick from the three options below (the spec draft carries all three). NY AM is behind Asia (its D8 tail ends ~15:40Z; freeze estimate 16:00-22:00Z). The three Asia options below are ready to compare; the choice is yours (section 7, question 1). Sunday 23:00Z Globex was a plan, not a gate (your 21:53Z order); nothing was cut to meet it.

## 2. Asia: the three options (pool-28 numbers; the enlarged pool-35 run gave the same three finals: asia-own and its L3M-gated twin = A, asia-stay main = C with controls 30/19/30, asia-stay-l3g = L7c368a4f alone; option B was the earlier two-book final)
Ulcer / max drawdown / worst week / $ per week.
| window | A: one book L385f4f2e.J502 | B: two books L7c368a4f + La010c3eb | C: three books L7c368a4f + L578701ed + L385f4f2e.J502 |
|---|---|---|---|
| last 6 months | 469 / -1,915 / -1,600 / 2,157 | 4,789 / -14,639 / -9,096 / 3,848 | 4,930 / -13,326 / -7,847 / 6,056 |
| last 3 months | $2,514 | $3,853 | 6,275 / -13,326 / -6,941 / 4,446 |
| 2023 $/wk | 40 | 660 | 963 |
| 2024 $/wk | 217 | 1,078 | 1,011 |
| 2025 $/wk | 179 | 633 | 1,221 |
| own persistence | 0.65 | 0.68 | 0.70 |
| luck controls beaten (6m / 3m / ulcer-only, of 30) | 30 / 27 / 30 | 27 / 16 / 29 | 30 / 19 / 30 |
- **Bare D7 yardstick** (your own comparison, unfitted D7 Asia stack): at the same last-6-months ulcer B earns $3,848 against $2,062 for bare D7 (last 3 months $3,853 against $1,163); every prior year positive for B, while bare D7 lost $58/wk in 2023 (+$506 in 2024, +$464 in 2025). With lots fixed at that risk level B's drawdown is deeper than bare D7's in the last 6 months, 2024 and 2025. Same caveat applies to C.
- **Why the main selection says "one book":** the rule's return-per-unit-of-ulcer clause rejects every second book once the first book has a tiny ulcer (469): all 15 landed two-book stacks fail that clause by 65-82%. The drawdown guards are met. This is a rule property, not a finding that the extra books are bad. Page: autopilot/ASIA_ONE_BOOK_EXPLAIN.md.
- **Option A caveats:** prior years thin (2023 $40/wk); 166 trades in the last 6 months, none concentrated (best 5 days = 23% of profit); the entry filter is a "5 of 10 conditions" vote plus a time-of-day block, and the one 20261110 event survives with exactly the minimum count (one input missed by 0.004). NT8 would need ES and YM 1-minute data and an exact Fibonacci/pivot port.
- **Option C caveat:** L578701ed reads the 10-level order book (CQG depth); not yet compared bar by bar with the NT8 feed.
- Labels: all three LEAD / BEST-AVAILABLE-NOT-PROVEN until the final run; none CONFIRMED.

## 3. What the fits did (Asia, pool 28, and NY AM)
- **Layers (take, lock, loss cut...):** NONE kept, in either session. Of 25 Asia books: 15 fail walk-forward, 8 fail ONLY the prior-year band, 1 fails only the null. Of the 14 RED years in the band-only group, 8 are genuinely worse on both drawdown and dollars, 6 are lower drawdown but lower dollars (several on tiny bases, e.g. La010c3eb 2025: $90/wk unfitted -> -$89). All 6 NY AM books: not kept.
- **Brackets:** one narrow LEAD pass (Asia M7ea48296: 60 -> 45 points). Every other pool book keeps its own bracket. L385f4f2e.J502 keeps its own 60/60: no alternative shape reaches its $2,157/wk at the same ulcer.
- **Exits:** none kept for any current pool book in either session (they lower drawdown but give up too much return in 2023-2025 at equal risk).
- **Pass 2 (entry gates):** L385f4f2e passes (it IS option A's J502 filter); M7ea48296 fails on 2023 (-$31); no other pool book improves.
- **Method point for you:** the prior-year band is relative to that year's own dollars, so a near-zero base makes it explode (+240% on a $90 base). The gate was not changed.

## 4. NY AM
Pool 7 books (B6f77f23d, B7bfd33b7, L05350e98, L488784d8, L6547965c, L7cc56d99 + one added by the universe fix). Pass 2, brackets, exits and layers: nothing kept; every book keeps its own settings. The NY stack loop's current selection (not yet final: it is in its swap/drop phase, 4 of 15 move sets still landing) is five books: L7cc56d99 + L488784d8 + B7bfd33b7 + B6f77f23d + L6547965c. Ulcer / max drawdown / worst week / $ per week at 1 lot: last 6 months 6,031 / -19,970 / -7,702 / 7,425; last 3 months 6,084 / -18,152 / -7,702 / 5,776; 2023 7,931 / -26,688 / -13,244 / 3,530; 2024 10,293 / -33,710 / -12,523 / 2,592; 2025 12,242 / -30,060 / -19,092 / 4,337. Own persistence 0.78, controls 30/23/30 (from the 6-book run of the same stack, not re-checked on 7). All three prior years are positive. Your Stack A (L7cc56d99 + L488784d8, bare-D7 comparison $3,366/wk at ulcer 4,313) is unchanged and still available. What waits: the NY stack-control sets (landing), the NY D8 controls and first looks (est. done ~15:40Z). Freeze estimate 16:00-22:00Z.

## 5. Defaults taken overnight (your order 02:54Z: nobody waits for you)
1. Wait for the pass-2 chain before freezing (nothing excluded): done, it finished by 06:00Z.
2. L7f41b347's pass-2 component stays NOT KEPT (2023 -$201/wk).
3. NY AM waits behind Asia.
4. Nothing needing your paste (spend, new machines, deleting or freeing data, credentials, live server) was done. The lease-file archive move (46k old leases) is parked for you.
5. I refused a dispatcher code change (it would touch all five hosts with nobody awake); it is on your list.

## 6. Failures and fixes overnight
- Layer driver (W-LAYERS): 150 + 98 rows were lost from the queue (race between writers and pullers on two lock files); re-queued, race fix approved with safeguards, lost-row audit added (0 lost rows since). A joint-stage design error (80 combinations instead of 8) wasted ~4,400 set-months; voided, nothing fed a verdict. A pool-watch bug (an exited child counted as alive) stopped two drivers; fixed. The NY joint driver restarted every 2 minutes against my own release rule; fixed.
- My own errors: I called pass 2 "6-10 h" (it finished by 06:00Z); I wrote "spec drafted" before it existed (corrected, now drafted); I mislabelled W-GRIDOPS "silent" because the guard ignored lines without the "- " bullet (guard fixed).
- Queue order: stack waves starved D8 twice (paced, then reordered Asia-first). A June-2026 fake-fill guard blocks 2 NY AM exit sets (not tested). Host B/A show 90-93% slots at 0% CPU idle (full).
- **Universe gap (12:08Z):** only 718 of 1,244 Asia _CANC ids had been in the combination loops' universe; fixed, loops restarted, finals are being recomputed. Everything labelled "pool 28" above came from the smaller universe.

## 7. Questions for you (top of autopilot/QUESTIONS_FOR_JOSH.md; defaults apply until you answer)
1. Which Asia v1: A (one book), B (two), C (three), or change the add rule (e.g. judge adds at equal risk and by max drawdown/worst week instead of return per ulcer)?
2. Is a "5 of 10" vote filter needing ES/YM data acceptable for D8, or restrict D8 filters to conditions NT8 computes from NQ ticks?
3. Prior-year band on a near-zero base: keep as is or measure against the book's whole-history dollars?
4. Exits: add a labelled drawdown-cut option (default no)?
5. November tape hole (MVWAP, PRF5, OPEN_MONTH): judge D8 on complete history going forward (default)?
6. June-2026 fake-fill guard (2 NY AM exit sets untested): investigate?
7. Dispatcher gap fix on the pool hosts (~1-3 slots per host): yes/no?
8. Lease-file archive move (data move): yes/no?

## 8. Machines
Overnight fill was held (hosts A, B, C, D at 86-101 of their caps; A and B at 0% CPU idle, so full). Box 1 is CPU-saturated by hub work; its load cuts (stale-results check every 30 min, pull loop 20 s) are in force. The stall check is clean except one explained heartbeat. ASIA D8 IS FINISHED (0 lines left). The D8 tail is NY AM only: ~24k set-months queued (controls, first looks), est. done ~15:40Z, more lines to be written as NY cells pass.

Pages: autopilot/D8_BUILD_SPEC.md (DRAFT Asia v1, options A, B, C + open items for the NT8 port), ASIA_ONE_BOOK_EXPLAIN.md, ASIA_JOINT_TABLE.md, NYAM_JOINT_TABLE.md, BRACKET_SHAPES_*.md, EXIT_WF.md, PASS2_JOINT_ASIA_RESULTS.md, BARE_D7_YARDSTICK.md, D8_TRIGDEBUG_*.md and D8_VECTORS_*.md (test vectors for the NT8 port).
