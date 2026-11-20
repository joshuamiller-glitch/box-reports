# ORDER 20261120_1351Z: Josh: three-stage fit, and a deadline: Asia ready for Sunday's Globex open
Josh's own words (he is awake):
- 13:48Z, to the relay's proposal "per-book stage first on pool books, then re-pick the stack, then the joint fit as the verdict": **"Yes order it this way"**
- 13:48Z: **"It's friday - i want asia done for Globex open on Sunday and maybe New york AM for D8"**
- 13:41Z: **"the boxs decision to do the top90 or 150 of the huge list isn't bad"**
Everything below is the relay's (Claude's) plan to meet those words. Globex opens Sunday 2026-11-22 23:00Z.

## A. Method (his yes)
STAGE 1, PER BOOK, pool books only (own-checks passers; Asia 29 now, NY AM 7): the book's own settings: pass 2 (confluence incl. order-book and tape conditions, market-type gate, time windows, entry method), exits (all seven families), bracket size, own loss cut / lock / take. Every pick checked on prior years + luck controls + the search-aware null before it counts.
STAGE 2, RE-PICK the stack from the FITTED books (own-checks reading, equal-risk drawdown-first, 15% guard on adds, swaps and drops; the staying-power variant beside it). The raw-book stacks are provisional.
STAGE 3, JOINT FIT at the stack level: all account-level layers together + confirmation that the per-book settings hold in company; reference row = today's settings; the verdict comes from here. Then prior years + 30 stack controls on the fitted stack.
The layer fit started 13:34Z on the raw three-book Asia stack keeps running as the first look and proves the machinery; it is not the final fit.

## B. Deadline plan for ASIA (relay's proposal; lead: correct the times from measured rates and post the plan with dates in MORNING.md)
- Now -> Sat 06:00Z: stage 1 on the Asia pool; pool widening continues in rank order behind it (Josh: ranked order "isn't bad"); every new passer joins stage 1.
- Sat 06:00Z: POOL CUT-OFF for D8 v1 Asia: whatever has passed by then. Stage 2 re-pick.
- Sat 06:00Z -> 18:00Z: stage 3 joint fit + stack prior years + controls.
- Sat 18:00Z: autopilot/D8_BUILD_SPEC.md FROZEN for Asia: every book (bar definition, trigger, side exactly as engine-tested, entry method, exit, bracket, filters, windows), every layer setting, lot table at 1-lot base, with the evidence table and the label for each item (spec-backed / best-available-not-proven). The relay codes from that file only.
- Widening and fitting continue after the cut-off; later passers go to a later build, not v1.
NY AM: same three stages one step behind Asia ("maybe" in his words): Asia has first call on slots; NY AM takes what is left; London first looks keep a floor; NY PM waits.

## C. Needed NOW so the build can be coded in time (not after the spec freeze)
1. BAR DEFINITIONS + TEST VECTORS for every bar type used by any Asia or NY AM pool book (cumulative-delta range, session volume clock, median Renko, line-break, volume bars, quote-message bars, time bars, and any other in the pool): exact construction rule (inputs, session reset, rounding, what closes a bar, tick handling at the boundary), and for 3 sample days each a file of bar close timestamps + OHLCV as the engine built them, so the NT8 bar types can be checked bar for bar. Research artefacts only; no account numbers. Page: autopilot/D8_BAR_DEFS.md + files beside it.
2. The same for every TRIGGER in the pool: exact formula, parameters, warm-up, and a sample-day list of signal timestamps and sides.
3. Josh runs D8 from the Strategies tab, chart-free; no drawing objects. Say for each bar type what market data it needs (trades only / quotes / depth) so the load on his NT8 can be judged.
Start with the books in the current Asia stack and Stack A (NY AM), then the rest of the pool.

## D. Honesty rules for the deadline
If Asia cannot pass its checks fitted by the cut-off, say so plainly; the label goes into the spec as it is. No gate is loosened to meet Sunday. Post a countdown line every 2 hours: stage, done / total, the date each stage ends, and what is at risk.
