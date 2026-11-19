# ALL_NEW_LAYER_PROGRAMME - DESIGN ONLY (nothing queued) - W-LAYERS, 2026-11-19 22:3xZ, order 2230Z (D8 = ALL NEW BOOKS)
Layers for new books are fitted on the ALL-NEW stack of the session (W-COMBO's forward-selected stack of new books only, account-level layers ON), not inside today's live stack. The old programmes (REPLACE-K7 / REPLACE-A7 bases, xP7/xM7/xH7 slot variants, ADD bases) are parked; their landed results stay as records (NEW_BOOK_LAYER_FIT_BEATS_LIVE.md, no longer refreshed).

## 1. What the programme is (per session stack with B new books, tags MF1..MFB)
| stage | what | sets | months | set-months per stack |
|---|---|---|---|---|
| S0 identity | ID1-ID9 inert hooks per book tag (hook inert = the stack's trades, trade for trade) on 2 months | 9 x B | 2 | 18 B |
| S1 book layers, one at a time | for EACH book: profit take (TK 12), lock (LK 9), loss cut (CU 4), context cut (CX 3), blackout (BO 3), new-book no-trade windows (NT 5) + W-FASTR picks (FR 14) = 50 settings, the rest of the stack unchanged | 50 B | 6 (L6M, L3M inside) | 300 B |
| S2 account layers | DAY-DONE (DD 18 settings), own day caps (CP 4) on the whole stack, session lot tables | 22 | 6 | 132 |
| S3 joint | top-3 settings per layer per book, coordinate search around the best (about 40 sets) | 40 | 6 | 240 |
| S4 prior years | the joint winner + top-2 deviations on 2023 / 2024 / 2025 (37 months) vs the all-new stack without layers; amber 15-30%, red > 30% | 5 | 37 | 185 |
| S5 controls | 30 date-shift controls of the final layered stack (layered controls) | 30 | 6 | 180 |
Total per stack = 300 B + 18 B + 737 = **318 B + 737 set-months**: B=4 -> 2,009; B=6 -> 2,645. Two stacks per session (best + runner-up) double it. At the HEALTH rate (3,5xx-3,8xx set-months/h) one stack is 0.5-0.8 h of the whole fleet; at the measured fast-path rate less.
Selection rule (standing): pick on the trailing 6 months with 3 months beside, protection first (stack ulcer, worst week, max DD), then $/week; a setting must keep >= 80% of the book's trades; older years not a disaster (amber / red); the 2-week roll; persistence >= 0.58 on the stack difference vs the unlayered all-new stack; "today, as run" stays the single reference line.
Order of layers inside S1 is book by book in the stack's own-merit order; S2 is refitted jointly after S1 (account rules see the layered books). W-COMBO refits jointly on the final stack after pass 2.

## 2. Why after pass 2
Pass 2 (filters / confluence / regime gate / time windows / entry / in-trade / sizer) and the exit run change a book's entries and exits, i.e. what the layers would fit. So S1-S5 start on the stack AFTER each book's pass 2 + exit-run best form is chosen; an earlier (pre-pass-2) pass is only a DRY RUN on the unfiltered books and is not worth the engine time.

## 3. What has to be built (ready in ~2 h of agent time once the first all-new stack set exists)
1. layer_gen.py takes a TAG parameter (today hard-coded MF1): ev_profit takes / locks, ec_hooks rules ('book': tag), ev_panel cap_tl / sess_tl, one mf_inject per tag (cap, ntz via mf_inject2), extra_bo per tag. Verify: with B=1 it still reproduces the 81 XA3 sets (done today for MF1).
2. A base builder = W-COMBO's all-new stack set JSON (live books OFF, MF1..MFB injected); the generator reads it (combo_auto.py output) instead of a REPLACE row.
3. S0 identity per tag on the first stack (18 B set-months); then the cron (layer_cron.py, stage logic already there: identity -> fit -> score -> prior years -> joint -> controls) is pointed at the stack list (autopilot/ALL_NEW_STACK_*.md / combo state) instead of D8_CANDIDATES / best_books.
4. Fast path: the NYL kinds already have fast variants on K7 / A7 bases; the stack sets need their own exact-vs-fast pair (W-FASTLADDER / W-FAST2).

## 4. When it can start
Not before (a) W-COMBO has a selected all-new stack per session (Asia first), (b) pass 2 + the exit run have fixed the books' forms, (c) S0 identity passes on that stack. No dates until (a)-(b) exist; the DRY-RUN version on today's unfiltered best books is NOT queued.
