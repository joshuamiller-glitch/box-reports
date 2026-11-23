# MORNING SUMMARY, Mon 2026-11-23 (first edition 05:10Z; refreshes 08:00Z and 12:00Z)

Research and Shadow only. Nothing was touched on the execution server or any live chart. No spend, no new machine, no data deleted.
Every number says whether it is truly bare (R0) or carries today's D7 wrapper (R1), and the lot basis.

## 1. What changed since the 22 Nov page

- **Asia v1 build basis = the 5-book stack** TL3_ALN_AS_STKd8106b26ef (Lb0e6dfa3.BRF40_80, L385f4f2e.J502, L92a90948, L6b373671.BRP60, L578701ed.BRF30_90). Josh chose it at 15:00Z. Why the 4-book appeared: two runs of the same weighted search (5-book = step 5 of the 05:03Z run on a 47-book pool; 4-book = final of the re-opened run on the 80-book pool). No add-rule change was made.
- **Add rule now judged on recent risk** (Josh, "yes recents should drive this"): equal L6M ulcer + 15% L6M max-DD / worst-week guard, L3M beside; prior years are a check, blocked only by a negative year or persistence < 0.58 (the colours are information). My first version used the 15-30% band as a blocker and collapsed NY AM to zero books: gate error, fixed 16:17Z.
- **Pools complete:** Asia (80 books), NY AM (36), NY PM (6 passers), London (4 passers, flag 02:48Z after 46 D8-invalid cells were marked invalid_d8).

## 2. Stacks (truly bare beside bare D7 only)

| Session | Recent-basis result | Note |
|---|---|---|
| Asia | equal and weighted recent loops both stop at L385f4f2e.J502 alone (controls 30/27/30) | genuine rejection: every second book fails "return per ulcer >= 1.01 x the stack before" (J502's L6M is smooth) |
| NY AM | same 5 books as the current stack TL3_ALN_NY_STKd8b76ecd35 (L8cfda948, Lf0346d55, L7cc56d99, Lbb254083, L8f11883e), controls 30/26/30 | 4 of 5 members judged R0, stack carries today's account layers (R1) on the search basis |
| London | provisional step 1: L19201dfc.BRF90_30, L6M $1,768/wk (R1, 1 lot) vs bare D7 London $348/wk | pool now complete: next FINAL is real |
| NY PM | provisional step 1: L52359bf4.BRP30, L6M $1,188/wk (R1, 1 lot) | bare D7 NY PM yardstick (K7 alone) built, rows landing |

## 3. Asia 5-book all-layers fit (truly bare base), verdict 20:45Z, null 00:17Z

Last 6 months per lot, ulcer / max DD / $ per week: 1 lot bare 3,046 / -9,450 / $10,834 vs best joint 1,827 / -5,422 / $7,645; 2 lots 3,481 / -10,508 / $10,247 vs 1,367 / -4,347 / $4,925; 4 lots 3,922 / -13,091 / $9,653 vs 1,578 / -4,578 / $5,348.
Walk-forward 0.60 / 0.85 / 0.91, 29 of 30 date-shift controls, year bands RED/RED/RED, **search-aware null FAILED** (real cut 38.7% vs null draws 33.3, 38.9, 19.0, 44.5, 31.5: beats 3 of 5, gate 4).
Label: WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN. Tested-bare = layers OFF; the fitted 4-lot setting (BF4_JT1, D8_LAYER_KEYS.md) is the weak option for Josh to switch on.
Bare D7 Asia scaled to the same max DD earns $949 / $761 / $801 a week at 1 / 2 / 4 lots (best joint ~8x / 6x / 7x on the last 6 months).
**Skip-after-losses (CG) was a no-op in this fit** (hook had no gov_book); fixed (CGB1-3), identity proven 392 of 392 trades, CGB screen queued.
4-book Asia stack (reference): joint landed 04:35Z, WEAK-BUT-POSITIVE at 2 and 4 lots, weak at 1 lot, null not run.

## 4. Weights ("why do all the books have the same weight?")

Best whole-lot vectors at equal L6M ulcer: Asia 3-8-2-6-1 (+26% $, unconstrained 1-6-1-2-1 +86%), NY AM 4-3-1-7-5 (+38%, unconstrained 3-2-1-4-2 +57%); exact engine checks match to the dollar. They win only 0.14-0.34 of 14-day blocks (floor 0.58); the pick does not repeat. Equal weights stay the default; the D8 panel has a lots-per-book setting so any vector can be tried in SIM.

## 5. Book styles (Asia, 54 + 8 twins)

52 continuation (30 breakout, 21 momentum/trend, 1 flow-follow), 2 pullback-with-trend, 0 reversal/fade/false-break. Counter-trend books were produced (269 of 2,076 reached step 2, 64% positive in L6M and L3M) and **none passed the gates** (126 failed prior years, 33 the luck controls). The two pullback passers lose on the stack's worst 20 days. Page ASIA_BOOK_STYLES.md.

## 6. D8 port

- Asia spec blocks and parity pages: delivered earlier; Josh's NT8 export for 2026-11-10 reproduced the box on bars, signals and the J502 event.
- **Seed page for tonight's 23:00Z session is NOT valid:** the box has no data after 2026-11-13 21:59Z (no tape for 11-16..11-20). Decision needed from Josh (below).
- NY AM: hand-written blocks and parity pages for Lbb254083 and L8f11883e (both use earlier-session bars; 6J data on the box ends 2026-11-10 07:59Z); per-bar feature pages for Lf0346d55 and L8cfda948.
- London: block for L19201dfc (CL trigger; CL file ends 2026-11-13 08:59Z; two near-identical books in the pool).
- D8_LAYER_KEYS.md: every setting code and the BookLock/zone/dollar definitions (per-book R for CAP and BookLock).

## 7. Decisions for Josh (also in QUESTIONS_FOR_JOSH.md)

1. **Data for 11-16..11-20 (NQ + ES/YM)** so the Asia seed page is valid for SIM. Default: no spend without your paste.
2. Layers in the first SIM run: OFF/bare (tested) or the weak fitted setting ON? Default OFF, selectable.
3. Which basis decides the add rule is now answered (recents); the Asia pin stays the 5-book stack.
4. Feature-store roll-session defect (<= 0.15% of events): fix and re-run, or port as is?
5. Real live commission (engine deducts $1.18/lot round trip; published figures are net of $4.84 all-in).
6. Held programmes were released ("release both"): NY AM first looks and Asia widening run as fall-through only (they have taken 34 rows so far).

## 8. What is running (05:10Z)

Fleet ~460-560 slots at ~10.5k set-months an hour, hosts at 94%+ of cap, no stuck rows, no dead daemons.
Chain 35% (file ~1.4k rows; London/NY PM recent loops), stack-fit 35% (NY AM bare fit screen then joint; CGB screen; London pin after), exits, D8 tail (~5.6k rows, squeezed), NY AM first looks and Asia widening (spare slots only).
Expected: NY AM bare-fit table (later this morning), NY PM FINAL + yardstick, London FINAL (real) and exit verdict (~05:00-06:00Z), London bare fit (pin ~05:30Z, ends ~07:00-09:00Z).

## 9. Slips and fixes overnight

- My gate error (band as blocker) removed all NY AM books for ~20 minutes of recent-basis search; fixed 16:17Z.
- Bare-fit pages were stubs (prior-year bare base rows missing) and the other stacks stopped at a false identity DIFF: fixed 20:34Z / 20:45Z.
- London/NY PM loops saw pool 0: the sync process ran old code: fixed 22:06Z.
- NY PM controls on holidays/early closes: three rewrites, now clean.
- Stack-fit share was ~21% of the fleet instead of 35% (slot base): fixed 21:22Z. Host C cap raised then reverted (CPU-saturated).
- London pool flag held by 46 D8-invalid cells: marked invalid by W-BRKT2 (scope exceeded my wording, backups exist).

---
## UPDATE 08:10Z (second edition; next refresh 12:00Z)

**New answers since 05:10Z**
- **Combined book** (autopilot/D8_ALL_SESSIONS_COMBINED.md, regenerates every 2 h; truly bare, 1 lot per book, last 6 months, net of $4.84): Asia + NY AM $18,329/wk, max DD -17,237, worst week -4,596 (bare D7 $5,055/wk, max DD -41,510); + London $20,097/wk, max DD -18,172; all four $24,726/wk, max DD -17,437, worst week -3,975 (bare D7 $5,205/wk, max DD -69,232). Over 42 months all four: $8,897/wk, max DD -74,669 (bare D7 $2,119/wk, max DD -189,730). Engine series end 2026-10-30; NY PM = sum of its four members' bare sets; fitted table Asia only and worse than bare over 42 months.
- **Why the depth book was locked out** (DEPTH_BOOK_LOCK_INFO.md): BookLock BL2 (arm 1.5R, give-back 50%) arms at +45 points of day P&L on the 30/90 book and fires at half the peak, inside one trade; it helped at 2 and 4 lots (the dropped trades would have lost $30-35k in 6 months) and cost money at 1 lot; never scored per book; D8 rule: checked at most every 2 s, halt to the 18:00 ET roll.
- **London book trade frequency:** 1.89 trades per session (median 1), 17.6% of sessions with none, busiest 8 (L6M); 0.95 / 0.99 / 1.25 in 2023 / 2024 / 2025.
- **Skip-after-losses on the new books** (CGB1-3) screened: raises ulcer and max DD at every N, helps the worst week 6-25%, costs 4-10% of the dollars: not chosen.
- **4-book Asia reference stack** joint: weak-but-positive at 2 and 4 lots, weak at 1 lot, null not run.
- **Weights:** the best vectors do not repeat across blocks (0.14-0.34 vs floor 0.58); equal weights stay.
- **Book styles:** 52 of 54 Asia books are continuation types, 0 counter-trend passers.

**Work in flight (orders from Josh, all research only)**
- Daily loss stop test on the Asia stack (hook built, identity passed, 1,671-row screen queued) and session-end run-vs-flatten test (identity passed; first month: letting trades run to 17:00 ET was +$7,900 over flatten in 2026-10, one month only): both fall-through behind the ordered fits.
- Cross-session locks (whole-day loss/profit, week floor, carry-over between sessions): proxy done (carry-over 'skip later sessions after an earlier session lost > $3-5k' best candidate, -18% ulcer for -1% dollars on Asia + NY AM + London), merged 15-book set built, identity proof running.
- NY AM bare all-layers screen done; joint (with the daily-loss family) ETA ~11:00-11:30Z; London fit queued (screen ~10:30-11:15Z, joint ~14:00-14:30Z); Asia joint re-run with the daily-loss family + CGB3 ~18:00-20:00Z.
- London pool complete (02:48Z); NY PM recent-basis FINAL pending (~10:00Z); NY AM weighted recent loop FINAL ~18:00-22:00Z.
- NY AM first looks and Asia widening released ('release both') but only run on spare slots: nothing has run yet; ordered work fills every slot.

**Decisions still open for Josh**
1. Data for 11-16..11-20 so the Asia seed page is valid for SIM (the seed page is stale-as-of 11-13).
2. Layers ON or OFF in the first SIM run (tested bare = OFF; the fitted pick failed its null and its prior-year bands).
3. Feature-store roll-session defect: fix and re-run, or port as is.
4. Real live commission.
5. Hold on the original-rule NY AM weighted loop (reference row only; costs ~3.8k rows): left running.

**Slips since 05:10Z:** chain share flapped between 25% and 35% under the tier rule (fixed to key on the recent-basis tier only); W-GRIDOPS slot-report label artefact misread as a slow stack-fit (corrected); W-BRKT2 exceeded its scope when fixing London's pool flag (backups exist).
