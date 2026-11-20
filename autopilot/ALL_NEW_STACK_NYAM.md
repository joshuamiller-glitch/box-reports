# ALL-NEW STACK, NY AM (W-COMBO, order 2230Z). DRY RUN / LEAD: re-run as first looks, prior years, controls, exits and pass 2 complete. Updated 2026-11-20 03:59Z.
Method: forward selection from an EMPTY stack on the ALL-NEW base (NO live book trades in any session, account layers ON at the D7 stand-in settings) with NEW books only; SELECTION RULE (Josh: drawdown first): step 1 = best single book by mean $/wk per unit of ulcer (return per drawdown; a one-book stack is never chosen by ulcer alone); steps >= 2 = among candidates whose stack mean $/wk is NOT LOWER than that of the best single book, lowest stack ulcer (then max DD, then worst week); stop when no candidate lowers the ulcer by >= 1%. Equal-capital framing: a stack of k books = k books at base lots (1 lot each), no rescaling. Both views are shown per step (the ulcer view and the return-per-drawdown view), exact production-driver runs at every step; the scorer only orders candidates. Columns: ulcer / max DD / worst week / mean $ per week, L6M (L3M beside), base lots.
Phase: select. Candidates tried: 128 (step 1 all; later steps the scorer-ordered top 15 exact).

| step | added / move | stack set | L6M ulcer / maxDD / worst wk / mean | L3M | mean per unit ulcer (L6M) | what the other view would pick (return-per-drawdown / lowest-ulcer) | tried at this step |
|---|---|---|---|---|---|---|---|
| 1 | L39470318 | `TL3_ALN_NY_L39470318_BASE` | 3209 / -8642 / -8588 / 1827 | 3731 / -8642 / -8588 / 1462 | 0.57 | L39470318 / L488784d8 | 53 |
| 2 | L7cc56d99 | `TL3_ALN_NY_STK0f902785` | 4369 / -12320 / -10915 / 4232 | 4035 / -11656 / -4197 / 3628 | 0.97 | Lddba3fab / Lb447a16d | 15 |
| 3 | L488784d8 | `TL3_ALN_NY_STKbb21126c` | 4093 / -11817 / -7445 / 5193 | 3846 / -11587 / -3825 / 4167 | 1.27 | L12e67af0 / L488784d8 | 15 |
| 4 | Lddba3fab | `TL3_ALN_NY_STK0112c118` | 4043 / -13046 / -6503 / 6465 | 3748 / -12166 / -2968 / 5339 | 1.60 | Lddba3fab / Lddba3fab | 15 |
| 5 | Lc161c6cc | `TL3_ALN_NY_STKf3d2d0e0` | 4840 / -15321 / -8006 / 7987 | 4703 / -15321 / -8006 / 7164 | 1.65 | L12e67af0 / L063c1550 | 15 |

Selected books in order (what each is, plain words):

- L39470318 (W-BEST score 0.646, L6M wk 1531.0): volume bar 750 contracts [vol_750]; ~131 bars/hour; trigger trig_levels_profile_va / retest {"M": 10, "tol": 0.5}; SIDE: BOTH SIDES; bracket plain60/60. Alone on the all-new base: 3209 / -8642 / -8588 / 1827. LUCK CONTROL: beats 18 of 30 shifted controls (drawdown-first), 30 of 30 on ulcer alone, L3M 5 of 30 - FLAG: FAILS (< 27 of 30), kept for Josh to decide. prior years (book alone, vs equal-risk reference) 2023/2024/2025 = RED / RED / RED, persistence 0.52.
- L7cc56d99 (W-BEST score 0.944, L6M wk 2527.4): line-break bar 3_40 [lbrk_3_40]; ~10 bars/hour; trigger trig_levels_vwap / break {"n": 2, "k": 0.25}; SIDE: BOTH SIDES; bracket sym15u; median stop 120 pts / target 120 pts (events). Alone on the all-new base: 4790 / -13326 / -7749 / 2405. LUCK CONTROL: pending (30 controls queued at the front by W-COMBO 02:30Z). prior years: pending.
- L488784d8 (W-BEST score 0.614, L6M wk 1198.4): swing bar 0.25 ATR [swing_atr_0.25]; ~121 bars/hour; trigger trig_momentum_roc / break_native {"len": 20, "wd": 1.0}; SIDE: BOTH SIDES; bracket plain60/60; median stop 60 pts / target 60 pts (events). Alone on the all-new base: 2839 / -7243 / -3569 / 961. LUCK CONTROL: pending (30 controls queued at the front by W-COMBO 02:30Z). prior years: pending.
- Lddba3fab (W-BEST score 0.467, L6M wk 1479.3): dollar-run bar 2000 [drb_2000]; ~40 bars/hour; trigger trig_book_ice / fade_sm {"thr": 2, "sm": 3}; SIDE: BOTH SIDES as engine-run (screen mode was long; the long-only book is the M-id); bracket plain60/60. Alone on the all-new base: 4901 / -11294 / -8806 / 1272. LUCK CONTROL: pending (30 controls queued at the front by W-COMBO 02:30Z). prior years (book alone, vs equal-risk reference) 2023/2024/2025 = RED / RED / AMBER, persistence 0.51.
- Lc161c6cc (W-BEST score 0.510, L6M wk 1253.5): session-volume-clock bar 50 bars/session [vsess_50]; ~20 bars/hour; trigger trig_levels_vwap / break {"n": 3, "k": 0.5}; SIDE: BOTH SIDES; bracket plain60/60; median stop 60 pts / target 60 pts (events). Alone on the all-new base: 4470 / -12779 / -7295 / 1454. LUCK CONTROL: pending (30 controls queued at the front by W-COMBO 02:30Z). prior years: pending.

RE-RUN WITH NEW BOOKS at 03:33Z: new pool members ['L3459244a', 'Lf1083387', 'L5606297d', 'Lf6f0cc5f']

LAST SELECTION KNOWN (kept visible while the re-run is in progress; PARTIAL, not yet at the stop rule; archived 03:25Z UTC; pool size 51): L39470318 + L7cc56d99 + L488784d8 + Lddba3fab + Lc161c6cc - 5 books: step 1 L39470318 -> ulcer 3209 / maxDD -8642 / worst wk -8588 / $1827 per wk; step 2 L7cc56d99 -> ulcer 4369 / maxDD -12320 / worst wk -10915 / $4232 per wk; step 3 L488784d8 -> ulcer 4093 / maxDD -11817 / worst wk -7445 / $5193 per wk; step 4 Lddba3fab -> ulcer 4043 / maxDD -13046 / worst wk -6503 / $6465 per wk; step 5 Lc161c6cc -> ulcer 4840 / maxDD -15321 / worst wk -8006 / $7987 per wk
The re-run restarts whenever new books join the pool (first looks finish about 05:36Z); the final run will use the full pool including the both-side B books.

Top 10 candidates alone (all-new base: no live book trades anywhere), by L6M ulcer:

| cell | L6M | L3M |
|---|---|---|
| L488784d8 | 2839 / -7243 / -3569 / 961 | 3024 / -6311 / -3569 / 538 |
| L2b8ccd55 | 2930 / -6963 / -3494 / 787 | 3339 / -6963 / -2249 / 445 |
| L39470318 | 3209 / -8642 / -8588 / 1827 | 3731 / -8642 / -8588 / 1462 |
| L247629c9 | 3270 / -8926 / -5773 / 1099 | 2652 / -6422 / -2739 / 1092 |
| Lb447a16d | 3284 / -8336 / -2834 / 798 | 2954 / -8115 / -2834 / 915 |
| L12e67af0 | 3660 / -10250 / -6918 / 1619 | 3452 / -9377 / -6918 / 1201 |
| L11e120ff | 3711 / -11751 / -4794 / 444 | 1963 / -5484 / -3574 / 1163 |
| Lc161c6cc | 4470 / -12779 / -7295 / 1454 | 3531 / -10161 / -5037 / 1735 |
| L7cc56d99 | 4790 / -13326 / -7749 / 2405 | 4719 / -11089 / -7749 / 2166 |
| L582ae3cb | 4842 / -14058 / -11617 / 1506 | 3660 / -10804 / -1859 / 1788 |

Reference line, today, as run: JL3 NY AM-session trades only (the five live NY AM books H7, K7, M7, O7, P7 (their NY AM-session trades from the JL3 run, as-run lots: mostly 1 base lot, P7 1 to 4); the live stack's other sessions removed from the sum, interactions as run): L6M 8444 / -17976 / -7184 / 838 ; L3M 5586 / -12293 / -7184 / 1563. (Whole-day JL3 for orientation: L6M 9416 / -31109 / -15728 / 18755.)
In plain words: today's live NY AM session earns $838 per week on an ulcer of 8444 over the last 6 months (max DD -17976, worst week -7184); last 3 months $1563 per week on ulcer 5586.

SECOND REFERENCE LINES, EQUAL RISK (reading aid only: lots per book stay a factor of the joint refit; equal-risk rule agreed with W-LAYERS):
- Today's NY AM session scaled to the all-new stack's drawdown (today's lots scaled by k = 0.57, i.e. same ulcer as the stack): L6M 4840 / -10303 / -4118 / 480 ; L3M 3202 / -7046 / -4118 / 896. Compare with the stack: L6M 4840 / -15321 / -8006 / 7987 ; L3M 4703 / -15321 / -8006 / 7164.
- The all-new stack scaled to today's drawdown (stack lots scaled by k = 1.74, same ulcer as today): L6M 8444 / -26730 / -13967 / 13935 ; L3M 8205 / -26730 / -13967 / 12499. Compare with today: L6M 8444 / -17976 / -7184 / 838 ; L3M 5586 / -12293 / -7184 / 1563.
(Scaling is linear on the daily P&L: a reading aid, not a realisable lot setting; lots are whole, caps and DAY-DONE are dollar thresholds.)

## EQUAL-RISK (BUDGET) SELECTION: maximise $/wk inside an ulcer budget = 100% / 75% / 50% of today's Asia-session ulcer (8732, L6M); same pool, exact runs, stop when no candidate adds >= 1% $/wk. DRY RUN / LEAD.

**Budget 100% (ulcer <= 8732)**: phase done

| step | added | stack set | L6M ulcer / maxDD / worst wk / mean | L3M |
|---|---|---|---|---|
| 1 | L7c368a4f | `TL3_ALN_AS_L7c368a4f_BASE` | 4075 / -11123 / -7409 / 2456 | 2028 / -5118 / -3617 / 2434 |
| 2 | L191904b3 | `TL3_ALN_AS_STKb1480774` | 4893 / -16315 / -5870 / 5444 | 3786 / -12900 / -5870 / 5322 |
| 3 | L16118e0a | `TL3_ALN_AS_STKe8db1557` | 6431 / -20953 / -12400 / 7681 | 4666 / -12127 / -4628 / 7409 |
| 4 | L023ff9ff | `TL3_ALN_AS_STKd3540163` | 8236 / -23419 / -15656 / 8676 | 3668 / -11169 / -8196 / 9097 |
| 5 | L578701ed | `TL3_ALN_AS_STKa8320599` | 7173 / -19009 / -13165 / 9457 | 5466 / -14746 / -11376 / 7912 |

**Budget 75% (ulcer <= 6549)**: phase done

| step | added | stack set | L6M ulcer / maxDD / worst wk / mean | L3M |
|---|---|---|---|---|
| 1 | L7c368a4f | `TL3_ALN_AS_L7c368a4f_BASE` | 4075 / -11123 / -7409 / 2456 | 2028 / -5118 / -3617 / 2434 |
| 2 | L191904b3 | `TL3_ALN_AS_STKb1480774` | 4893 / -16315 / -5870 / 5444 | 3786 / -12900 / -5870 / 5322 |
| 3 | L16118e0a | `TL3_ALN_AS_STKe8db1557` | 6431 / -20953 / -12400 / 7681 | 4666 / -12127 / -4628 / 7409 |

**Budget 50% (ulcer <= 4366)**: phase done

| step | added | stack set | L6M ulcer / maxDD / worst wk / mean | L3M |
|---|---|---|---|---|
| 1 | L7c368a4f | `TL3_ALN_AS_L7c368a4f_BASE` | 4075 / -11123 / -7409 / 2456 | 2028 / -5118 / -3617 / 2434 |
| 2 | L1716c153 | `TL3_ALN_AS_STKc26bfa12` | 4084 / -14152 / -14152 / 3806 | 2765 / -8975 / -1892 / 3549 |


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

## W-LAYERS LAYER TABLE 23:4xZ (order 2300Z; owner of all rows = W-LAYERS; identity = small real engine runs, month 202610, test stack TL3_STK_ZA_febd6a89_85ab, base = TL3_LYR_ZA_febd6a89_85ab_BASE: 551 trades, 58 MF1, net_fee -24,649.32; 'identical' = trade for trade on (book, exit_ns, gross, lots, net_fee))
| layer | parameter map (hook / key) | identity test (inert == base) | effect probe (must differ, else wiring flagged) | wired at | owner |
|---|---|---|---|---|---|
| **BKL book give-back lock** | sim.py check_book_lock constants (peak 2.0 R, give-back 50%, weekly floor 12 R) -> lay_hooks par.bl[tag] | ID_LH (bl at D7 defaults): IDENTICAL (22:5xZ) and ID_LH2 (per-tag zone format): IDENTICAL (23:15Z) | FX_BKL_TIGHT (1.0 R / 70% / 8 R): 531 trades, MF1 58 -> 53: acts | 22:41Z | W-LAYERS |
| **ZONE (POI no-trade set)** | sim.py ntz_check on PT.PoiSet (20 pts ahead, Half x0.5) -> lay_hooks par.zone[tag] {dist, act, frac}; range dist 10/30/50 Half, 20/30/50 Skip; reference row off (dist 0) | ID_LH / ID_LH2: IDENTICAL | FX_ZONE_SKIP50: 543 trades, MF1 58 -> 41: acts | 22:41Z (per-tag 23:08Z) | W-LAYERS |
| **NT windows / NTZ for new books** | mf_multi stream ntz (W-COMBO key) ; windows DERIVED FROM THE BOOK'S OWN FIRST-LOOK TRADES (layer_gen.own_nt_windows: the worst non-overlapping 30-min entry windows by the book's own net P&L over L6M, negative only; test book: 20:00-20:30, 19:00-19:30 ET), not the live lists | MF1_ID7 (ntz = []): IDENTICAL (22:5xZ) | NT1: windows applied to the stream (JSON checked; engine effect probe not run, 0 sm left in budget) | 22:34Z | W-LAYERS (key by W-COMBO) |
| **LOTS session lot table** | a new book's lots = its events' lots column (scaled_events x2/x3/x4, whole lots); equal-risk judging below | ID_LOTS1 (events x1): IDENTICAL | none run (a x2 probe would change P&L by construction; to be shown in the first real J1) | 22:41Z | W-LAYERS |
| **SCAP daily profit/loss caps beyond the own cap** | lay_hooks par.stack_caps {tags, profit, loss} on the SUM of the new books' day P&L (engine has per-book caps only) ; range profit/loss 6,000/2,400; 12,000/3,600; 12,000/7,200; 24,000/4,800; 24,000/9,600 | ID_SCAP (1e12 / 1e12): IDENTICAL (23:15Z) | FX_SCAP_TIGHT 6,000/2,400: identical (never reached in 202610); FX_SCAP2 800/400: 541 trades, MF1 58 -> 22: acts | 22:41Z | W-LAYERS |
| **NRT near-target latch / give-back** | th_nt/wnt_hooks par.latch [{book: tag, X, stale | give | givep}] (NOT th_neartarget/nt_hooks, which is the P7 lock-ladder hook; I first wired the wrong module, the probe showed no effect, fixed) ; range X 0.90 stale 10 s; X 0.95 stale 20 s; X 0.90 give 8 pts; X 0.95 give 10% of target | ID_NRT2 (X = 9, never reached): IDENTICAL (23:33Z) | FX_NRT2 (0.90 / 10 s): 555 trades, 19 NtStale exits: acts | 23:2xZ | W-LAYERS (hook by W-NT) |
| **SHV target shave** | wnt_hooks par.shave {tag: ticks}: 2/4/8 ticks | covered by W-NT's identity (empty = Base) | not run | 23:2xZ | W-LAYERS (hook by W-NT) |
| **STC state-cut cell (Trade Health entry cut)** | ev_panel par.cut_tl [[tag, from, {arm, mult, win, pers, newmae, var}]] ; D7 K7 cell arm 45 / mult 10 / win 2 / pers 3 / var 2 ; range arm 30 / 60, mult 5 / 15 | not inert by construction (a cell always cuts); effect probe FX_STC_arm30 queued (1 sm), result to be posted | pending | 23:4xZ | W-LAYERS |
**Trade Health on BOTH sides is among the factors for EVERY book (per tag), hooks and ranges:** PROFIT side: TK take (ev_profit.takes[tag] = pct 0.5/0.65/0.8/0.95 x secs-without-new-extreme 5/15/30 = the early-profit take); LK lock (ev_profit.locks[tag] pct 0.5/0.65/0.8 -> stop to entry + 0/10/20 pts); NRT near-target latch + give-back (wnt_hooks, above); SHV target shave; BKL book give-back lock. LOSS side: CU loss cut (ec_hooks flat 0.4-1.0 x stop); CX context cut (ec_hooks flat, ctx fresh, 0.4/0.6/0.8 x stop); FR picks (no-follow-through nft < +10/+5 after 20 min, scratch after -45 exit at -5) ; STC state-cut cell (above) ; CP own day cap 1-4 stops ; BO blackout 15/30/60 min. Factor count per book now: TK, LK, CU, CX, CP, BO, NT, BKL, LOTS, NRT, SHV, STC, ZONE = 13 book-level factors per book; account / stack: DD, CAP6, SLS, ER, ATR, SCAP = 6 -> **F = 13 B + 6** (B=2 -> 32, B=3 -> 45 (L243), B=4 -> 58, B=6 -> 84; all <= 121 so L81 (F <= 40) only for B <= 2, otherwise L243: J1 = 243 x 12 = 2,916 set-months, B=7+ (F > 121 at B >= 9) needs a bigger array).
**EQUAL-RISK judging for the LOTS factor (proposal, to agree with W-COMBO):** a lots multiple changes risk and dollars together, so it is never compared in dollars. For each setting s on the same months take the stack's ulcer U_s and mean $/week M_s; the risk-matched scale is k_s = U_stand-in / U_s (size the whole stack so its ulcer equals the stand-in's); the equal-risk result is k_s * M_s (and k_s * worst week, k_s * max DD); the ranking statistic is M_s / U_s (return per unit ulcer) with the standing guard that the unscaled stack ulcer must stay within +15% of the stand-in (AMBER line) or the setting is only reported, not selected. A lots multiple that merely scales P&L therefore ties the stand-in; it wins only if the scaled dollars are higher at equal ulcer (diversification / session fit).
**Cost update (screen additions per book: BKL 4 + LOTS 3 + NRT 4 + SHV 3 + STC 4 + ZONE 6 = 24 settings; account SCAP 5):** screen per stack ~ 18 B + (86 settings per book) x 6 B + 37 x 6 + 8 = 534 B + 230 (B=2: 1,298; B=4: 2,366) ; J1 243 x 12 = 2,916 (B >= 3) + J2 480 + J3 294 + controls 180 -> B=2: 972 + 774 + 180 + 1,298 = **3,224**; B=3: 2,916 + 774 + 180 + 1,832 = **5,702**; B=4: **6,236**; B=6: **7,304**. At 3,500-3,800 set-months/h: 0.9-2.1 h of the whole fleet per stack.
**ERRATUM to the cost lines above (W-LAYERS, arithmetic): screen settings per book = TK 12 + LK 9 + CU 4 + CX 3 + CP 4 + BO 3 + NT 5 + FR 12 + BKL 4 + LOTS 3 + NRT 4 + SHV 3 + STC 4 + ZONE 6 = 76 (not 86); account / stack settings = DD 18 + ER 2 + CAP6 2 + ATR 2 + SLS 2 + SCAP 5 = 31. Screen per stack = 18 B + 76 x 6 B + 31 x 6 + 8 = 474 B + 194 set-months. Corrected totals per stack (screen + J1 + J2 + J3 + 180 controls): B=2 (F=32, L81): 1,142 + 972 + 480 + 294 + 180 = 3,068; B=3 (F=45, L243): 1,616 + 2,916 + 774 + 180 = 5,486; B=4 (F=58): 2,090 + 3,870 = 5,960; B=6 (F=84): 3,038 + 3,870 = 6,908; the L243 array holds up to 121 factors = B <= 8. At 3,500-3,800 set-months/h: 0.8-2.0 h of the whole fleet per stack.**

## EQUAL-RISK RULE FOR THE LOTS FACTOR AND THE ALN BASE: AGREED TEXT (W-COMBO amendments to W-LAYERS' proposal, 23:xxZ; W-LAYERS to confirm in MORNING.md)
**Accepted from W-LAYERS:** a lots multiple is never compared in dollars; for setting s on the same months take the stack's U_s (ulcer) and M_s (mean $/wk); ranking statistic M_s / U_s (return per unit ulcer); the risk-matched equivalent (k_s = U_stand-in / U_s times M_s, max DD, worst week) is REPORTED, with the guard: the UNSCALED stack ulcer must stay within +15% of the stand-in or the setting is only reported, not selected.
**W-COMBO amendments:**
1. The guard also applies unscaled to max DD and worst week (each within +15% of the stand-in). Consequence stated openly: x2 / x3 / x4 lots roughly multiply the ulcer by 2-4, so they can never be SELECTED by this rule, only reported; the LOTS factor can therefore only move away from the 1-base-lot stand-in through a real diversification effect (a session-lot pattern that lowers drawdown per dollar). The choice of the live lot size is the separate LAST step (sizing of the final combination, live lots = max(1, floor(1.75 x base + 0.5))).
2. The scaled equivalent is a reporting number, not a realisable setting (lots are whole; a 1-base-lot book cannot be scaled down; day caps and DAY-DONE are dollar thresholds so P&L does not scale linearly): do not select on k_s * M_s alone.
3. Confounding in the orthogonal array: LOTS changes every other factor's dollar effect. J1 therefore records every run unscaled AND equal-risk-normalised (k = U_stand-in / U_run); the main effects of all NON-LOTS factors are estimated on the NORMALISED responses (ulcer-normalised mean = M/U, maxDD/U, worst week/U), the LOTS effect on M/U; the selection of every factor still ends in the unscaled J3 confirmation on the drawdown-first criterion.
4. Selection order stays Josh's: drawdown first (ulcer, max DD, worst week), then dollars, L6M with L3M beside, prior years, persistence >= 0.58; the return-per-ulcer ranking is used only for LOTS (and as the second view elsewhere).
**ALN base (replaces the TL3_STK test base for all layer work):** the joint refit runs on the ALL-NEW stack set built by `combo_aln.build_stack(S, [ids])` (name TL3_ALN_<S>_STK<hash>): TL3_EV_JL3 hooklist (account layers ON at the D7 stand-in) + swb_inject2 swap-off of EVERY live book in EVERY session (A7 [0]; H7 [0,3]; K7 [0,1,3,4]; M7 [1,3]; O7 [3]; P7 [0,1,3]; U7 [0,1]) + ONE mf_multi hook with streams MF1..MFB. Same structure as the TL3_STK test stacks, so stack_gen.stack_info / build_stack_sets / joint_gen read it unchanged; layers that act on live books (live-book cuts, locks, takes) are moot on this base; the account layers (DAY-DONE, caps, same-side rules, ER sizer, ATR-skip) act on the new books' trades only. Single-book ALN BASE sets (TL3_ALN_<S>_<id>_BASE) are the one-book special case (B=1).
