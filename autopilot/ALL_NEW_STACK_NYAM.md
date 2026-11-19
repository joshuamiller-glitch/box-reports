# ALL-NEW STACK, NY AM (W-COMBO, order 2230Z). DRY RUN / LEAD. STATUS: NOT STARTED: waits for the both-side B-id NY AM books and the 1,525 stale re-runs (stale-pending cells excluded). Same method as ALL_NEW_STACK_ASIA.md: forward selection from an EMPTY NY AM session (all five live NY AM books OFF, account layers ON, rest of the day JL3), new books only (best_books_nyam.csv kind=new, B ids included), exact production-driver runs at every step, then drop/swap moves among new books; today, as run, one reference line at the bottom.

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
