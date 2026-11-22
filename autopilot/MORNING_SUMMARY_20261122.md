# MORNING PAGE, Sunday 22 Nov 2026 (first edition 12:40Z; refreshed through the day; research only: nothing on the execution server or any live chart was touched)

Plain words, for Josh. All numbers are 1 lot per book unless a line says otherwise. R0 = truly bare (no D7 rule of any kind). R1 = today's D7 wrapper on top. "L6M / L3M" = last 6 / last 3 months. Cells read ulcer / max drawdown / worst week / worst day / $ per week.

## 1. Where we are, in one paragraph
Brackets are no longer a fixed 60/60 for every book: every Asia, NY AM, London and NY PM candidate was re-screened at 17 shapes, then the best shape was run through the exact engine truly bare, with prior years and 30 luck controls. The ASIA POOL IS COMPLETE (11:29Z): 54 books pass every check bare at their own shape, plus 8 twins that share a trade list. NY AM has 10+ passes and is still draining (stage B ~16:00Z, stage C ~flat then draining). London and NY PM have not produced survivors yet. The exit run says NO exit variant beats the fixed bracket on any finished stack member ("none kept"). The first stack-rule fits say: on the stacks tested the D7 wrapper is not worth keeping as it was; the ER sizer and Trade Health on the new books were not in those fits and are now being built and fitted from truly bare, with zones, at 1, 2 and 4 lots (section 5). D8 Asia spec blocks and a parity pack (bars, signals, trades for two days) are in the mirror for coding.

## 2. Passes per session (distinct trade lists; twins inherit the verdict)
| session | books passing a+b+c+d bare at their shape | state |
|---|---|---|
| Asia | 54 (+8 twins) | POOL COMPLETE 11:29Z |
| NY AM | 10+ (pool 22 books, 14 from the new search) | stage B 17.0k rows left (~16:00Z), stage C ~7.9k (flat) |
| London | 0 so far | B/C waves running (3.8k rows) |
| NY PM | 0 so far | B/C waves running (3.1k rows) |
Full table (book | trigger | bar | bracket | L6M / L3M $/wk | max drawdown | 2023/24/25 | persistence | controls beaten): `autopilot/BRACKET_PASS_TABLE.md` (W-BRKT). Top Asia lines (by L6M $/wk per unit of ulcer): L5483cb3c urenko_56 profile_nodes.break P45 (L6M 2,849, max DD -7,644, 27/30); Lb0e6dfa3 tm240 libpattern.nr F40_80 (2,969, -8,614, 29/30); L548972b6 vsess_30 roc.break_native F40_80 (2,337, -5,429, 29/30); L7ea48296 cdr_100 mvote P45 (2,410, -7,540, 30/30).
READ WITH CARE: the shape of each book was picked as the best of 17 on the same last-6-months data; the null column on the pages (ladder bracket best in 2.6% of cells vs 5.9% if shapes were interchangeable) says the screen alone cannot rank shapes; the prior years + 30 luck controls decide, and every pass above went through them.

## 3. Stacks (FINALs), bare beside bare
Which stack is "the" Asia stack is not settled: the weighted search's early rounds closed on partial evidence (a 3,000 s patience timer ran out under queue starvation): that is fixed, the rounds were re-opened, the corrected FINAL on the complete pool is still to post. Two reference stacks:
| stack (1 lot each) | L6M R0 bare | L6M R1 today's wrapper | note |
|---|---|---|---|
| 5-book first run (Lb0e6dfa3.BRF40_80 + L385f4f2e.J502 + L92a90948 + L6b373671.BRP60 + L578701ed.BRF30_90) | 3,046 / -9,450 / -4,971 / $10,834 | 3,462 / -11,350 / -4,928 / $9,103 | L3M bare $10,600/wk; 2023-25 $1,042 / $1,917 / $1,982 per week |
| 4-book full-pool provisional (Lb0e6dfa3 + L385f4f2e.J502 + L9c2622b0.BRP45 + L4aaacdb2.BRP30) | 2,581 / -8,577 / -5,079 / $7,468 | 2,604 / -9,644 / -5,258 / $7,107 | L3M bare $6,327/wk; 2023-25 $931 / $1,234 / $1,441 |
UPDATE 12:56Z (reconciled 13:05Z): the COMPLETE-pool weighted Asia FINAL (asia-own-w, pool 80, all 60 sets of the 5th add round landed) is the 4-book stack (R1 L6M 2,604 / -9,644 / -5,258 / $7,107; controls 30/26/30). Reason the 5-book stack is not reached: the weighted loop judges an add at EQUAL WORST-PRIOR-YEAR MAX DRAWDOWN (your 14:13Z weights order), which is stricter than equal L6M ulcer: the 4-book stack needs a 5th book to earn >= $7,178/wk at equal worst-prior-year drawdown (-17,334, 2025) and 0 of 60 candidates pass (L92a90948 $6,846, L6b373671.BRP60 $6,694, L578701ed.BRF30_90 $6,155); on the L6M-ulcer basis L6b373671.BRP60 DOES pass as 5th add (return per ulcer 2.922 vs 2.757). Which basis decides is your call (decision 1 below). Equal-weight COMPLETE FINALs (pool 80, R1, 1 lot): asia-own = L385f4f2e.J502 alone (469 / -1,915 / -1,600 / $2,157, 30/27/30); asia-stay = Lb0e6dfa3.BRF40_80 alone (R0: 2,643 / -8,614 / -4,590 / $2,969, 29/20/30). The 5-book stack is stronger truly bare ($10,834 vs $7,468 per week at similar drawdown). The full-pool search stopped at 4 books because its 5th add round was judged on 35 of 60 candidate sets; computed on the landed sets, L6b373671.BRP60 passes every add-rule number, L578701ed.BRF30_90 fails worst week by ~5%. Corrected search is running. Bare D7 for the same session at the same drawdown: `BARE_D7_YARDSTICK.md` (R0 rows; bare beside bare only).

## 4. Fit verdicts so far (stack rules + daily stops fitted on top of TODAY'S WRAPPER; the redo from bare is section 5)
- Single book Lb0e6dfa3.BRF40_80: the wrapper does nothing at 1 lot (R0 = R1, 0 days stopped); best joint pick (StackCut 50% + BookLock 1.5R/67% + whole-stack profit stop +8R) FAILS (a RED prior year, beats 13 of 30 controls): run it bare.
- 4-book stack (STKd8da2eb47b): joint pick (BookLock 2.0R/33% + per-book day profit stop +5R + whole-stack day profit stop +4R) L6M 1,989 / -9,294 / -5,258 / $7,229 vs R1 2,604 / -9,644 / $7,107: passes walk-forward (0.633 over 60 periods) and the year bands against the wrapper (GREEN x3). Against TRULY BARE (2,581 / -8,577 / $7,468) it is better on ulcer but worse on max drawdown and dollars: your call; null and controls pending.
- 5-book stack (STKd8106b26ef): verdict due ~12:30Z (joint stage running); page `ASIA_STACKRULES_AS_STKd8106b26ef.md`. NY AM 5-book: page posted at 12:12Z (`NYAM_STACKRULES...`).
- Every fit page now carries a "joint pick judged against truly bare" block (walk-forward, persistence, year band vs R0).

## 5. The all-layers fit from truly bare (your 12:19Z order): started
Base = truly bare; every layer added on top and judged against bare (walk-forward >= 58%, 15-30% year band, null >= 4/5): Trade Health loss and profit side (the per-trade cut / lock / take families), zones (6 distance settings now; zone-type variants by POI class being built; extra zone classes later), the ER sizer, BookLock, StackCut, per-book and whole-stack daily stops, c_gov, no-trade-set; at 1, 2 and 4 lots per book. About 26,000 set-months per stack; Asia screen 14:30Z-16:15Z (W-LAYERS gave both: 0 of ~5,500 rows done at 12:31Z, the follower queues in batches), joint verdict ~20:00Z (stack-fit share 35% first call).
Your question "zones and sizer tested?": the sizer was in the earlier fit but did nothing at 1 lot; and it turns out the D7 ER sizer only runs for the old L2-gated books (K7, P7, U7, H7, M7), never on a new-book stream at ANY lot size: a sizer hook for the new books is being built and tested now. Zones and Trade Health on the new books were not in the earlier fit: they are now. Three D7 Trade Health exits (ThL2Cut, ThL2Trail, PolicyCut: order-book-state exits) have no equivalent yet: on the list for you to decide.

## 6. Exit run ("nothing in D8 without it")
NONE KEPT for every finished member: Lb0e6dfa3, L6b373671, L578701ed, Le4fede95, L9c2622b0, L4aaacdb2, L385f4f2e.J502, L92a90948, B7bfd33b7, L7cc56d99, L43f0cbfb and the NY equal-5 members L8cfda948, Lbb254083, L8f11883e, Lf0346d55 (flowp_v15_t2 lowered ulcer in both windows at stage 1, red in prior years: none kept). The fixed brackets stay. A registry sweep of ~90 Asia books at new brackets runs at low priority (8% share, ~2.6 h).

## 7. Lots: why x4 does not scale (W-LAYERS X4_GAP_ASIA5.md, 5-book stack, L6M)
Truly bare fills only: per lot the 4-lot run makes $9,653 vs $10,834 at 1 lot (-11%) and ulcer per lot is 29% worse (3,922 vs 3,046): the real fill cost at size. The earlier "x4 = 1.22x" result was mostly a RULE artefact: with BookLock's R left at the 1-lot value, BookLock closed 382 trades at 4 lots. Lot-scaled ("lin") wrapper at 4 lots: $8,748 per lot per week (-4% vs R1 1-lot $9,103). So: if D8 runs above 1 lot, every dollar rule must be scaled with the lots (R = lots x stop x $20; day caps in R), and expect ~-11% per lot of $/wk and ~+29% ulcer per lot from fills alone. Build the 1-lot numbers first.

## 8. D8 build spec and parity pack (W-D8SPEC)
`D8_BUILD_SPEC.md`: AUTO:BOOK blocks for 13 books (Asia 7, NY AM 6) with bar rule and thresholds, trigger, entry/one-position rules, bracket, session-end exit, filter, data needs, stack rules, each line SPEC or OPEN; AUTO:LAYERS (21 layer rows; every layer ships OFF in the panel until the all-layers fit lands). Parity pack: `D8_PARITY_<id>_<20261027|20261110>.md` for 13 books (BARS, SIGNALS, TRADES, INPUTS with ms times) + `D8_PARITY_TAPE_20261110_ASIA.md` (51,093 NQ prints). Independently re-implemented from stored events: Lb0e6dfa3 11,058/11,058, L92a90948 837/837, L6b373671 3,554/3,554, Le4fede95 19,161/19,162, L9c2622b0 5,845/5,845, L4aaacdb2 1,485/1,485, L43f0cbfb 25,009/25,009, L8cfda948 5,106/5,106, Lf0346d55 6,807/6,815 (explained by the feature-store defect below). OPEN: block-delta/OFI features and level-trigger line values not re-derived from tape. PORT FROM ENGINE EVENTS.

## 9. Overnight problems, what they cost
- Signature alert (Nov 21 15:33Z): 1,440 set-months (~2%) re-ran automatically before a whitelist stopped it.
- Queue starvation / ordering bugs (all fixed, nothing deleted): NY AM 2a started ~25 min late (prepush order); stage-B files mis-anchored ~2 h; stack-fit rows waited behind local-driver claims (sr_mover); chain head overshoot twice (hard cap); the declared shares summed to 162% then 110% (proportional squeeze); the "rows left" counters never shrank (source files kept landed lines: prune_sources.py pruned 75,465 rows). Fleet rate dipped to 10-12k set-months/h at times (normal 13-15k).
- 700 old-pool stack-rule screen rows pulled unleased (not wanted); partial add rounds (the timer): audited, re-opened, nothing deleted.
- Feature-store defect: duplicate (sess_id, bidx) keys on contract-roll sessions mask the feature to NaN on the second contract's bars; effect <= 0.15% of events per book (Lf0346d55 9 of 6,815); not fixed, not re-run (your call).
- pkill -f slip by W-GRIDOPS (took its own shell, nothing else); explicit pids only since.

## 10. Decisions for you (also in QUESTIONS_FOR_JOSH.md)
1. Asia v1: the stack to code: the COMPLETE-pool 4-book FINAL (worst-prior-year-drawdown basis) or the 5-book first-run stack (stronger on L6M-ulcer basis: bare $10,834 vs $7,468/wk)? Both are being fitted bare with all layers; say which basis decides the add rule (equal worst-prior-year max drawdown, as in your weights order, or equal L6M ulcer, as in the standing selection rule).
2. The wrapper: on every stack tested so far bare is at least as good on dollars and max drawdown; a fitted layer set only wins on ulcer (the 4-book joint pick). Build D8 bare first and add layers only if the all-layers fit (section 5) beats bare on the gates?
3. Feature-store roll-session defect (<= 0.15% of events): fix and re-run, or port from engine events as they are?
4. The patience timer on add rounds is removed (a round waits for all its sets); the add rule itself is unchanged.
5. The three order-book-state Trade Health exits (ThL2Cut, ThL2Trail, PolicyCut): build for new books or skip.
6. Live commission (the engine deducts $1.18/lot round trip, the pages use $4.84): which number is real? Published results are net of $4.84.
7. Sizing above 1 lot: the lot-scaled form (section 7) is mandatory; confirm 1 lot for the first SIM run.

## 11. Still running and when it lands (estimates at 12:40Z; ~13k set-months/hour)
NY AM stage B ~16:00Z; NY AM stage C draining; London and NY PM B/C ~2-3 h; corrected Asia FINALs (equal and weighted) after the re-opened rounds; all-layers fit: Asia screen 14:30Z-16:15Z, joint verdict ~20:00Z; the 5-book fit verdict ~12:30Z; sweep of ~90 Asia exits ~15:30Z; item 7 (bare second look at 1,173 old-wrapper rejects, 3,612 rows) behind the rest.
