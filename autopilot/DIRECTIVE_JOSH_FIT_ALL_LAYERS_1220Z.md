# Order 1220Z Sun Nov 22 — from Josh (quoted), relay's reading marked "(relay)"

Context the relay gave Josh: on the 5-book Asia stack the stack-rule fit's joint pick ($9,074/wk, max DD -11,350) is worse than truly bare ($10,834, max DD -9,450), because the fit starts from D7's wrapper (R1) and tunes it; the sizer was inert at 1 lot; zones and Trade Health were not in the fit at all.

Josh, 12:15Z: "zones and sizer was tested?"
Josh, 12:19Z: "yes build all of those in- with 6 servers we cant test TH/zones and the sizer on final asia books?"

(relay) Josh wants every D7 layer built into D8 AND tested on the final Asia books now: Trade Health (loss side and profit side), zones, the sizer, plus the stack rules and daily stops already in the fit. His standing rules apply: every layer stays ON, the deliverable is the best SETTING of each layer ("none" is a reference row, never the verdict; a weak-but-positive setting is delivered with its evidence for him to decide); joint, not sequential; fitted settings judged by walk-forward >= 58%, prior-year 15-30% band, best-of-many null >= 4/5 (27/30 shown, not a gate); pick on recent data; never bare D8 beside fitted D7.

## 1. The fit, redone from bare, with all layers (W-LAYERS, with W-TH / zone / sizer owners; LEAD assigns)
a. BASE = TRULY BARE (R0) of the stack, not today's wrapper. Every candidate setting is added on top of bare and judged AGAINST BARE (walk-forward, year band, null). Keep the R1 row only as a labelled reference.
b. LAYERS (all of them): Trade Health loss side; Trade Health profit side; zones; the ER sizer; BookLock; StackCut; per-book daily profit stop and daily loss stop; whole-stack daily profit stop and daily loss stop; skip-after-losses (c_gov); no-trade-set handling. Settings menus as used for D7 (W-TH's menu, the zone menu, the sizer thresholds), fitted to these books, not copied from D7.
c. LOTS: the sizer and anything else that acts on lots is inert at 1 lot. Run the fit on a 2-lot and a 4-lot basis per book as well as 1 lot (dollar rules scaled with the lots: the "lin" form), and report per lot. A setting that only helps at 2+ lots is a valid result: say at which size.
d. METHOD: screen each layer one setting at a time on bare (nothing dropped at the screen), then the JOINT stage over the top settings of all layers together (orthogonal array as now), verdict from the joint stage; interaction table. Then lot check, null, controls.
e. STACKS: the Asia stack first: BOTH the first-run 5-book stack TL3_ALN_AS_STKd8106b26ef and the full-pool weighted FINAL when its re-opened search posts (timer fix); if they differ, fit both and show them side by side. Then the NY AM stack when its re-opened search posts a FINAL. London and NY PM when they have stacks.
f. PER-BOOK layers (Trade Health, zones) are fitted per book inside the stack run (the stack is the judge), since a per-book gain can vanish in the stack.

## 2. Slots (LEAD)
Six servers: give this fit first call with the stack-search rows; Asia before NY AM. Say what share it gets and the expected time for (i) the screen, (ii) the joint verdict on the Asia stack.

## 3. Report (LEAD TO JOSH, plain)
For the Asia stack, one table: truly bare | best joint setting of all layers | each layer's own best setting alone; columns last 6 and last 3 months $/wk, ulcer, max drawdown, worst week, worst day, 2023/24/25 $/wk; at 1, 2 and 4 lots per book (per lot); walk-forward %, band colours, null; and beside it truly bare D7 Asia scaled to the same max drawdown. One line per layer: the setting to build as the D8 default, and whether it beats bare or is weak-but-positive.

## 4. Build spec (W-D8SPEC)
The relay builds D8 Asia with ALL these layers in the code and in the panel. Write the exact rule text and parameters of each layer as the engine runs it (Trade Health loss/profit, zones, sizer, BookLock, StackCut, daily stops per book and whole stack, c_gov, no-trade-set) into D8_BUILD_SPEC.md under AUTO:LAYERS, each line SPEC or OPEN, with the fitted D8 default when item 1 lands. Until then the layers ship in the panel switched off (bare = what was tested).

Reply with one line per item and a time.
