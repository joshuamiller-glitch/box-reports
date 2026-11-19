# ALL-NEW STACK, ASIA (W-COMBO, order 2230Z). DRY RUN / LEAD: re-run as first looks, prior years, controls, exits and pass 2 complete. Updated 2026-11-19 23:09Z.
Method: forward selection from an EMPTY stack on the ALL-NEW base (NO live book trades in any session, account layers ON at the D7 stand-in settings) with NEW books only; criterion = mean $/wk per unit of stack ulcer (return per drawdown; ulcer alone would favour empty stacks), exact production-driver runs at every step; the scorer only orders candidates. Columns: ulcer / max DD / worst week / mean $ per week, L6M (L3M beside), base lots.
Phase: wait1. Candidates tried: 60 (step 1 all; later steps the scorer-ordered top 15 exact).

| step | added / move | stack set | L6M | L3M | tried at this step |
|---|---|---|---|---|---|

Selected books in order (what each is):


Reference line, today, as run: JL3 ASIA-session trades only (all five live Asia books; the live stack's other sessions removed from the sum, interactions as run): L6M 8732 / -25697 / -16205 / 15741 ; L3M 9814 / -25697 / -14754 / 11903. (Whole-day JL3 for orientation: L6M 9416 / -31109 / -15728 / 18755.)

## JOINT LAYER REFIT PLAN (W-COMBO with W-LAYERS ALL_NEW_LAYER_PROGRAMME.md; order 2233Z addendum; PLAN ONLY, no engine slots until the all-new stack of the session exists)
**Principle (Josh):** every layer stays in D8; its SETTINGS are fitted fresh on the ALL-NEW stack, ALL TOGETHER. D7's settings are only the stand-in (level 0) while the search runs. Per-layer one-at-a-time runs are the SCREEN only; the VERDICT is ONE joint stage on the exact engine varying all layers together.
### (a) Layers, setting ranges (from layer_gen / jn05 JL3 hooklist) and level
| layer | level | hook | screen range (one at a time) | D7 stand-in |
|---|---|---|---|---|
| Trade Health profit side: take (TK) | book | ev_profit takes[tag] | pct 0.5/0.65/0.8/0.95 x sec 5/15/30 (12) | JL3 value for the live book of the same role |
| profit lock (LK) | book | ev_profit locks[tag] | pct 0.5/0.65/0.8 x X 0/10/20 (9) | |
| Trade Health loss side: loss cut (CU), context cut (CX) | book | ec_hooks rules book=tag | CU 0.4-1.0 x stop (4); CX 0.4/0.6/0.8 x stop, ctx fresh (3) | |
| own day cap (CP) | book | mf_inject cap | loss cap 1-4 x stop x 20 (4) | 12,000 / 4,800 |
| blackout after stop (BO) | book | ev_panel bo | 15/30/60 min (3) | 30 (P7 only today) |
| windows / NTZ / OTE-style (NT) | book | mf_inject2 ntz | 5 windows per session (NY AM 09:30-12:00, Asia 18:00-20:30 ET in 30-min steps) | none |
| W-FASTR picks (FR) | book | mixed | 14 | |
| DAY-DONE (DD) | account | scr_hooks conj -> dd_hooks | n 14/22/30 x thr -1800/-2400/-3600 x per-book/stack (18) | n 22, -2400 (-2R) |
| daily profit / loss caps | account | cap_tl, c_gov | 0.75x / 1x / 1.5x of the D7 caps (3) | D7 caps |
| book lock | account | wb_hooks | on / lock thresholds of the tag (3 levels) | D7 lock |
| stack rules (same-side lots cap, loss-cut stack rules, same-side-loser skip) | account | cde cap6, c_gov, ec stack cuts | cap 4/6/8 lots; skip on/off (3) | cap 6 |
| ER sizer | account | state sizer {thr, lo, hi} | thr 0.2/0.3/0.4 x lo 0.35/0.5/0.75 (3 levels) | thr 0.3, lo 0.5, hi 1.0 |
| zone layer | account/book | zone/NTZ lists | W-ZONES top-3 zone sets per session (3) | D7 zones |
| ATR-skip | account | ev_panel atr_skip | rel 1.3/1.6/2.0 (3) | 1.6 (P7) |
| session lot table | account | ev_panel sess_tl | 1x / 1.5x / 2x base lots by session (3) | base |
Account-level = DD, caps, book lock, stack rules, ER sizer, zone, ATR-skip, lot table (8 factors). Book-level = TK, LK, CU, CX, CP, BO, NT per book (7 factors per book; FR picks enter as extra levels of the matching factor). **Total factors F = 7 B + 8** (B = books in the stack: B=2 -> 22, B=4 -> 36, B=6 -> 50).
### (b) Screen design and joint design
**Screen (per-layer, one at a time, on the ALL-NEW stack with the other layers at D7 stand-in):** W-LAYERS S1 50 settings per book x 6 months (300 B set-months) + S2 account layers (22 sets, 132). Output per factor: top-3 settings by the standing rule (drawdown first, keeps >= 80% of the book's trades). This is a screen: it never decides.
**Joint stage (the verdict, ONE stage):** 3 levels per factor = {D7 stand-in, screen #1, screen #2} (screen #3 only if #2 ties). Exploration of the interaction:
1. J1 = orthogonal array: L81 (3^40) when F <= 40 (B <= 4), L243 (3^121) when 40 < F <= 121: 81 (or 243) sets, ALL factors varied together; run on 12 months (202510-202610 minus 202511, so the 2-week roll can use earlier fit windows) = 972 set-months (2,916 for L243). Main effects per factor on ulcer / maxDD / worst week / mean; two-factor aliasing is limited by the array (strength 2); report the effect table.
2. J2 = interaction check: the 8-10 factors with the largest main effects, L27 (3^13) on those only (others at their J1-best level) + one-factor-at-a-time interactions between account layers and the book layers they touch (DD x CP, ER sizer x lot table, book lock x BO): 27 + 12 = ~40 sets x 12 months = 480.
3. J3 = confirmation: the predicted best combination, 4 neighbours (each of the 4 most sensitive factors one level worse) and the D7-stand-in combination on the SAME stack = 6 sets x (12 months + 37 prior-year months) = 294. The verdict = the J3 best (standing rule: 6M pick with 3M beside, protection first, older years not a disaster, persistence >= 0.58 vs the unlayered all-new stack).
Number of engine sets in the joint stage: B <= 4: 81 + 40 + 6 = 127 sets; B 5-8: 243 + 40 + 6 = 289 sets.
### (c) Cost, set-months per session (6M + prior years + 30 controls + 2-week roll)
| stack size B | screen S0+S1+S2 (18B + 300B + 132) | joint J1 + J2 + J3 | S5 controls (30 x 6) | 2-week roll | total per stack |
|---|---|---|---|---|---|
| 2 | 768 | 972 + 480 + 294 = 1,746 | 180 | 0 extra (re-fits over the J1 runs' months: 6 roll points x 2 weeks inside the 12 months) | **2,694** |
| 4 | 1,404 | 1,746 | 180 | 0 | **3,330** |
| 6 | 2,040 | 2,916 + 480 + 294 = 3,690 | 180 | 0 | **5,910** |
(W-LAYERS' own estimate 318 B + 737 is the staged version with a ~40-set coordinate stage; this plan replaces its S3 by J1-J3 as ONE joint stage: +1,000-3,000 set-months, in return for an interaction table.) Two stacks per session (best + runner-up) double it. At the fleet's 3,500-3,800 set-months/h that is 0.7-1.6 h per stack; at the 10-20% STK cap 6-20 h.
### (d) Place in the order
stack selection (this page) -> pass 2 (filters / confluence / regime / windows / entry / in-trade / sizer) -> exit run (each book's best form) -> stack identity test (S0) -> SCREEN -> ONE joint stage (J1-J3) -> prior years inside J3 -> 30 controls -> 2-week roll validation -> D8 build spec. The all-new stack is re-selected after pass 2 / exits (the selection tables here are DRY RUN until then).
### (e) "Settings changed because the base changed" check
1. Level 0 of every factor is D7's setting; the J1 main-effect table states for every factor whether the best level is D7's or not, and by how much the stack changes (ulcer, maxDD, worst week, mean) - so each changed setting is reported against D7 on the SAME stack.
2. Re-fit control on the OLD base: the same screen + J1 procedure (cut to the book-level factors of one live book) is run on a JL3 base for one live book; if the procedure does not recover D7's own settings (or a no-worse level) there, the procedure is suspect, not the new stack.
3. Broken-test flag: any layered set whose trades are IDENTICAL to the unlayered base where the layer should act (no-op layer), or two different stacks giving identical layer-effect numbers, is flagged and the layer's hook wiring is checked (the inert-hook identity ID1-ID9 proves the wiring on the unlayered side).

### Status of the factor wiring (W-LAYERS 22:4xZ, W-COMBO decision)
Wired in the generators (offline-tested, not run): per-book TK, LK, CU, CX, CP, BO, NT (NT needs the ID7 identity run on a real stack before any NT set is trusted) and account-level DAY-DONE, own day caps, ER sizer (thr/lo), same-side lots cap (4/6/8), ATR-skip on the new books (1.3/1.6/2.0), same-side-loser skip (off / after 3). NOT wired (no parameter map in the JL3 hooklist): book-lock thresholds, zone / no-trade-window lists of the live stack, session lot table, daily profit/loss caps for new books beyond CP. Decision: these four stay at the D7 stand-in (never off) and are reported as 'not varied' in the J1 effect table until their parameter maps exist; the claim 'every layer fitted jointly' is therefore PARTIAL until they are wired; the plan's factor count falls accordingly (about 7B + 6 instead of 7B + 8).

## W-LAYERS UPDATE 22:4xZ (Josh addendum 2233Z: EVERY layer's settings fitted jointly; the four 'not wired' layers are wired and VARIED)
**Factor count back to FULL (all layers).** Book level per book (tag): TK, LK (Trade Health PROFIT side), CU, CX (Trade Health LOSS side), CP (own day cap), BO (post-stop blackout), NT (new-book no-trade windows = the NTZ layer for the new books), **BKL** (book give-back lock, NEW), **LOTS** (session lot table = the events' lots, NEW) = **9 per book**. Account / stack level: DD (DAY-DONE), CAP6 (same-side lots cap), SLS (same-side-loser skip), ER (ER sizer), ATR (ATR-skip on the new books), **ZONE** (points-of-interest no-trade set = the zone layer, NEW), **SCAP** (daily profit / loss caps on the sum of the new books, beyond each book's own cap, NEW) = **7**. **F = 9 B + 7** (B = 2 -> 25, B = 3 -> 34 (L81), B = 4 -> 43 (> 40: L243), B = 5 -> 52, B = 6 -> 61).
Trade Health on BOTH sides is in (profit: TK take / LK lock; loss: CU loss cut / CX context cut) and so is the zone layer (ZONE POI set + NT windows): confirmed.
**Parameter maps (found in sim.py / the JL3 hooklist; hook code/th_layers/lay_hooks.py, appended last in the set, identical to its base at every D7 default):**
| layer | where D7 keeps it | stand-in (level 0) | screen / joint range (centred on D7, rows far from it) | reference row (never a level) |
|---|---|---|---|---|
| BKL book lock | sim.py check_book_lock L3413 constants, overridden per tag by lay_hooks par.bl | peak 2.0 R, give-back 50%, weekly floor 12 R | peak 1.0 / 1.5 / 3.0 / 4.0 R with give-back 70 / 60 / 40 / 30% and weekly floor 8 / 10 / 15 / 20 R (4 settings) | off (peak 1e9) |
| ZONE | sim.py ntz_check on the POI set (PT.PoiSet) within 20 pts ahead, Half (x0.5) after P1_START; lay_hooks par.zone | dist 20, Half | dist 10 / 30 / 50 Half; dist 20 / 30 / 50 Skip (6 settings) | off (dist 0) |
| SCAP stack caps | engine has per-book caps only (check_limits); lay_hooks par.stack_caps sums the new books' day P&L | none beyond each book's own 12,000 / 4,800 | profit / loss 6,000 / 2,400; 12,000 / 3,600; 12,000 / 7,200; 24,000 / 4,800; 24,000 / 9,600 (5 settings) | none |
| LOTS session lot table | ev_panel sess_tl / the events' lots column (a new book's lots come from its events; whole lots only) | 1 base lot | x2 / x3 / x4 per book (3 settings) | - |
| NT windows / live NTZ | mf_multi stream ntz (D7's own GUARDS / SLOTLIST / on_gate act on the named live books only) | none | 5 windows per session (done) | - |
**Screen additions (per stack):** BKL 4 x B + LOTS 3 x B + ZONE 6 + SCAP 5 = 7 B + 11 settings x 6 months. **Identity (small, urgent):** ID_LH (lay_hooks at every D7 default) and ID_LOTS1 (lots x1 events) must reproduce the unlayered stack trade for trade; ID7 (ntz = []) likewise; two effect probes (zone Skip 50, book lock 1.0R/70%/8R) must DIFFER from the base or the wiring is flagged (broken-test rule).
**Cost per stack (set-months):** screen = 18 B (ID) + 366 B (61 settings x 6) + 222 (37 account settings x 6) + 4 (hook identity) ; joint J1 = 81 x 12 = 972 (F <= 40) or 243 x 12 = 2,916 (F <= 121) + J2 480 + J3 294 ; controls 180.
| B | F | screen | joint | controls | total per stack |
|---|---|---|---|---|---|
| 2 | 25 (L81) | 36 + 732 + 226 = 994 | 972 + 480 + 294 = 1,746 | 180 | **2,920** |
| 3 | 34 (L81) | 54 + 1,098 + 226 = 1,378 | 1,746 | 180 | **3,304** |
| 4 | 43 (L243) | 72 + 1,464 + 226 = 1,762 | 2,916 + 480 + 294 = 3,690 | 180 | **5,632** |
| 6 | 61 (L243) | 108 + 2,196 + 226 = 2,530 | 3,690 | 180 | **6,400** |
At 3,500-3,800 set-months/h: 0.8-1.8 h of the whole fleet per stack (two stacks per session double it).
**Re-fit control (plan e2):** unchanged. **Not wired, stated plainly:** the live stack's own GUARDS / SLOTLIST / on_gate rules (they act on the named live books, not on injected books); DAY-DONE per-book variants beyond the 18 settings.
