# Order 1510Z Sat Nov 21 — Josh approved a new fit; the design text is written by the relay (Claude)

## Josh's words (verbatim)
- 14:10Z: "these fittings aren't including stopping for the day - profit .loss targets - only like TH?"
- 15:08Z: "ii"

What "ii" answers, as the relay put it to him at 15:05Z: "What to do about D7's stack rules inside the new-book numbers: (i) Keep them as they are and port them exactly. (ii) Fit them for the new books (stack-cut share, lock levels, daily caps), with a truly bare row for reference, in the same run as the daily-stop fit. (iii) Re-run everything truly bare." The relay recommended (ii) "because it matches your rule that layers stay on at their best setting, it settles the lot-size problem, and it folds into the daily-stop fit you asked about."

Everything below is the RELAY'S READING of how to run (ii). Details that are my choice are marked (relay). If a detail is wrong for the engine, say so and propose the nearest correct thing before running; do not silently change it. Research only. Nothing on the execution server or any live chart.

## STACK-RULE + DAILY-STOP FIT for the D8 stacks
Scope: Asia option A (L385f4f2e.J502), B (L7c368a4f + La010c3eb _CANF), C (L7c368a4f + L578701ed + L385f4f2e.J502), and the NY AM five-book final. Standing: re-run automatically on any stack whose FINAL changes membership (same watcher idea as the weights), and for London / NY PM stacks when built.

1. LOT-NEUTRAL FORM FIRST (relay): every setting is expressed so that the result is the same per lot at any lot size: dollar thresholds as multiples of R (R = lots x stop points x $20) or of the stack's summed R; StackCut as a share of the position with a stated rounding rule for 1 lot; sizer as a multiplier with a stated rounding rule. State the rounding rule for each. This is what removes the "holds at 1 lot only" problem.
2. FAMILIES (screen one family at a time, nothing dropped at the screen; grids are relay proposals, widen if cheap):
   a. StackCut: off (reference), 25 / 50 / 100% of the other same-side positions; Asia-only as today, and also tried on the NY AM stack (it is Asia-only today).
   b. BookLock give-back: off (reference); arm at day peak 1.5 / 2 / 3 R; give back 33 / 50 / 67% of peak. Weekly floor: off, -8 / -12 / -16 R.
   c. Per-book daily caps: profit stop off, +5 / +7.5 / +10 / +15 R; loss stop off, -2 / -3 / -4 / -6 R (today's +$12,000 / -$4,800 at stop 60 = +10 R / -4 R at 1 lot: confirm which element is which in the engine source first).
   d. WHOLE-STACK daily stops (new; none exists today): daily profit target that stops the session: off, +4 / +6 / +8 / +12 R of one book; daily loss limit: off, -3 / -4 / -6 / -8 R. Day-done variants as W-LAYERS proposed (18 settings) are fine.
   e. Sizer: off (reference), today's (thr 0.3, x0.5), and 2 neighbours; only meaningful at >= 2 lots: say so and run this family at 2 lots.
   f. Entry gates already in the wrapper (c_gov skip after 2 same-side losses; screens skip gate): on (today) vs off, as reference rows, so their effect is known.
3. REFERENCE ROWS, always shown: (R0) TRULY BARE = triggers + own bracket + session flat, every stack/account rule off, entry gates off; (R1) today's wrapper exactly (the current published numbers). Reference rows are never verdicts.
4. VERDICT from a JOINT stage (Josh's standing rule): top settings of each family varied together on the exact engine, drawdown first; interaction table; not one family frozen and the next fitted on top.
5. GATES = the fitted-setting gates Josh approved 18:10Z Nov 20: pick on recent data (L6M with L3M beside), walk-forward (fitted beats R1 in >= 58% of periods, drawdown-first), prior years inside the 15-30% band at equal risk, best-of-many null >= 4/5; 27/30 shown, not a gate. Because the prior-year band misbehaves on near-zero bases, ALSO print the band measured against whole-history dollars beside it (information; the gate itself is unchanged until Josh rules).
6. DELIVERABLE per stack: the best SETTING of each layer with its evidence ("none" is not a deliverable; if nothing passes, deliver the best setting labelled WEAK with its numbers for Josh to decide), plus the table: R0 bare / R1 today / fitted: ulcer / max DD / worst week / worst DAY / $ per week for L6M, L3M, 2023, 2024, 2025; days stopped per window; persistence; controls. Bare D7 at the same drawdown beside it (bare vs bare only).
7. LOT CHECK: run the final fitted setting of option C and of the NY AM stack at 2 lots and 4 lots; report per-lot results beside 1 lot. They must match except for whatever calibration 2's remaining gap is (see 8).
8. NAME THE REMAINING GAP in calibration 2 (L6M -14% per lot at x4 with rule counts matching): compare the trade lists and fills of the x4 set and the 1-lot set on the first five differing days. Is it the fill model at 4 lots (queue / through / hair), fees, or a layer? If fills: give measured slippage per lot at 1, 2, 4, 8 lots for each book in A, B, C and the NY AM five. Post this before the lot check.
9. BEFORE RUNNING: W-LAYERS (or whoever owns it) posts the plan in 6 lines: families and grid sizes after correction, set-months for screen / joint / null / lot check per stack, finish time, owner; the lead checks it against this order and starts it without waiting for the relay. Queue: at the head with the Asia stack lines; NY AM stack behind Asia.
10. D8_BUILD_SPEC.md: every option's numbers stay labelled "1 lot, with D7 stack layers as in 1.5" until this fit lands; then the fitted stack rules, in lot-neutral form with rounding rules, become part of the spec the NT8 build must implement.

The weights work (orders 1416Z/1419Z) continues; the weighted engine runs and the "-w" loops wait for item 8 and then run on the fitted lot-neutral wrapper, not on today's wrapper (relay: otherwise they would be fitted to rules that are about to change; say if you disagree).
