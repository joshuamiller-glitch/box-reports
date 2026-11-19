# D8 COMBINATION PLAN (W-COMBO, order 1410Z; Josh: "after the winners, COMBINE them and pick the best stack")

Status: design + tooling + dry run. Research only. Prereg: `autopilot/PREREG_COMBO.md` (sha256 505e34f120fdcb59, line in DECISIONS.md). Code: `code/th_combo/` (combo_build.py, combo_score.py, combo_search.py, combo_loop.sh). Nothing here takes engine slots from first looks: the dry run is <= 84 set-months on box 1 at nice 8.
Order 1407Z applies: REPLACE ONLY. A candidate is a replacement of a live book; ADD is a reference column only.
**All dollars are engine BASE lots, net of $4.84 per lot round trip (outputs/FEES.md proxy). Live lots = max(1, floor(1.75 x base + 0.5)) per book; the dollar scale to live is about x1.75 but is NOT recomputed per trade here.**

## 1. What is combined (formal definition)

**Slots.** A slot is a (live book, session) pair the live D7 strategy actually trades (LIVE_BOOKS_REFERENCE.md, engine session codes in the trades `session` column: Asia 0, London 1, NY AM 3, NY PM 4):
| session | slots (live books) | engine swap hook |
|---|---|---|
| Asia (stage 1) | A7, H7, K7, P7, U7 | `swb_inject2 tag=<book> sess=[0] mode=swap` |
| NY AM (stage 1) | H7, K7, M7, O7, P7 | `swb_inject2 tag=<book> sess=[3] mode=swap` |
| London / NY PM (stage 2/3, not in this stage) | London: K7 M7 P7 U7; NY PM: K7 | codes 1 / 4 |
K7 in Asia and K7 in NY AM are DIFFERENT slots (the swap hook is per session code).

**Choices per slot:** keep the live book, or one REPLACE passer for that slot (the passer carries its own best layers and its tested exit; a passer = REPLACE row passing L6M + L3M, rule B, engine persistence >= 0.58, controls, layers, exit run). ADD is never a choice (order 1407Z).
**Constraints:** a passer fills at most ONE slot at a time (its event stream cannot be used twice); each slot gets at most one passer; twin streams (W-DEDUP table) count as one passer; a passer can only fill a slot of its own session. **A passer can be a candidate for several slots:** its REPLACE set exists per slot (NY AM: `TL3_NYE_<id>_RK7 / RP7 / RM7 / RH7`; Asia: `TL3_ASI_<id>_RA7 / RK7 / RP7 / RH7 / RU7`; layer programmes per slot `TL3_NYL_<id>xK7 / xP7 / xM7`). The combination enumerates assignments of distinct passers to distinct slots (`code/th_combo/combo_slots.py`).
**Slot options of the current strict candidates (landed 43-month REPLACE sets, 15:18Z):** L01811caa: H7, K7, M7, P7 (NY AM; strict pass vs P7 and M7 with all prior years GREEN, persistence 0.69 / 0.61; vs H7 pass on L6M/L3M, prior years pending); L6a25b155: K7 (NY AM; its strict rows fail vs K7/M7/H7 per W-LAYERS, kept only as a screen option); L5c9e11b3: A7 and H7 (Asia; RA7 / RH7 43 months); Lda55d973: A7 (Asia). 44 assignments for these four; scorer A ranks P7<-L01811caa + K7<-L6a25b155 + A7<-Lda55d973 first (L6M ulcer 7,327 vs today's 9,416, mean $21.3k/wk, persistence 0.67), but same-session pairs (two NY AM books replaced) are exactly where a delta-additive scorer is weakest (see section 6).
**Combination** = one choice per slot across Asia and NY AM together. Number of combinations = prod_s (N_s + 1), N_s = passers for slot s (cost section).

**How the exact engine builds a combined set.** A single REPLACE set (e.g. `TL3_NYE_L01811caa_RK7`) = the JL3 baseline hooklist (`TL3_EV_JL3.json`: wb_hooks, ec_hooks, scr_hooks = DAY-DONE conj gate, c_gov, ev_panel, ev_profit) + `swb_inject2 {tag:K7, sess:[3], events:empty.parquet, mode:swap}` + `mf_inject {tag:MF1, events:<passer events parquet>, cap:[12000,4800], fill:through, hair:0.5, wait:10}`. A combined set = the same list with one `swb_inject2` per replaced slot and the replacements' event streams as SEPARATE books.
**ENGINE FINDING 1 (hook): do NOT stack several `mf_inject` hooks.** Reading `th_majorf/mf_inject.py`: the wrapper keeps its state in instance attributes (`s._uw_b`, `_uw_pend`, `_mf_cur`, `_mf_lim`) and the outermost wrapper handles every `mfent` event, so a second `mf_inject` runs BOTH event streams as ONE book under the LAST tag (one position at a time, one shared daily cap, trades of both streams labelled with the last tag); I also saw the merged tag in the (invalid-driver) first dry run. Sets built that way (`ny_build.mk` with a list of events: e.g. W-NYENG's C2/C3 combos, tags MF1..MF3) are therefore one merged book, not k independent books. Fix: `code/th_combo/mf_multi.py` (one hook, per-tag Book and state, same semantics line by line); identity vs `mf_inject` on one stream: trade for trade IDENTICAL on 202605 under the production driver (TL3_CMB_ID1 vs TL3_CMB_ID0). Builder: `code/th_combo/combo_build2.py combo_multi(name, [(live_book, session, events), ...])` (tags MF1..MFk in list order).
**ENGINE FINDING 2 (driver): combined and single sets must run through the PRODUCTION driver** (`tp_launch.py th_works_j/jn05_run2.py SET MONTH`, scrubbed env, as `th_s2/s2_remote_run.sh` / `ql_driver.py`). The local pattern `tp_launch.py state_sizer_ijk.py jbjobs SET:MONTH` does not give the JL3 stack (plain JL3 202605: 618 trades / P7 $47.4k vs landed 631 / $62.1k). Production driver check: a fresh copy of TL3_EV_JL3 (TL3_CMB_JL3F) 202605 is IDENTICAL to the landed JL3 in every field, and a fresh copy of TL3_NYE_L01811caa_RK7 is IDENTICAL to the landed RK7.
**Interaction channels (why a combined stack must be RUN, not added):** the account layers act on the whole stack: DAY-DONE conj gate (>= 22 stack closes in the day and day P&L <= -2R = -$2,400 base), stack cuts, book lock (`wb_hooks`), the sizer / lot tables, new-book day cap (`mf_inject cap`), blackout / no-trade zones, the policy-line hooks. Replacing a book changes which trades the other books take (their entries can be blocked by a day halt that the replacement triggered).
**Passers' own layers and exits in a combined set.** The layer hooks are keyed by book tag (`ev_profit` takes / locks, `ec_hooks` rules `book:MF1`, `ev_panel` cap_tl / sess_tl / bo books, `mf_inject` ntz). In a k-replacement combination each passer gets its own tag MFi and its layer keys are renamed MF1 -> MFi (code/th_layers/layer_gen.py hard-codes 'MF1': add a `tag` argument; see section 5). The tested exit recipe (W-EXITENG hook `ex_inject`) is a property of that passer's `mf_inject` hook entry, so it carries over per tag.

## 2. The fast combination scorer (screen)
Input: landed per-trade results only (`runs_rf/<set>/<month>/trades.parquet`: book, session, gross, lots; p484 = gross - 4.84 x lots), daily P&L over the weekday calendar (zero filled), months 202304-202610 minus 202511 (the 2025-11-28 tape hole; documented exclusion applied to every stream alike).
* **Scorer A (delta-additive, the one used for search):** combo_daily = JL3_daily + sum_i (R_i_daily - JL3_daily), R_i = the landed single REPLACE set of passer i (whole stack, so every single-replacement interaction is inside R_i; only the second-order interaction between replacements is ignored). For a single passer it is exact by construction.
* **Scorer B (slot swap, reference only):** JL3 - sum JL3 slot P&L + sum replacement MF1 P&L (ignores that the other books' trades change).
* Statistics (same as th_majorf/mf_stackscore.stats): ulcer (RMS drawdown of the cumulative daily curve) = primary, max DD, worst calendar week, mean $/week; windows L6M (202605-202610), L3M (202608-202610), 2023, 2024, 2025, ALL.
* Rule B colour per prior year vs today's stack: worst of ulcer / max DD / worst week "% worse" and mean $/wk "% lower": > 30% RED, 15-30% AMBER. Engine persistence = share of non-overlapping 14-day blocks where the combined stack P&L >= today's (gate >= 0.58).
* The scorer is used ONLY to rank and to drop clearly dominated combinations: dominated = worse than the best on ulcer AND mean by more than twice the measured scorer error. Error vs the exact engine: section 6.
Speed: 131 combinations (32 landed Asia RA7 passers x 3 NY AM RK7 passers incl. "keep") in 59 s cold (cache build), then about 0.05 s per combination.

## 3. Verdict plan (exact engine) and cost
1. **Singles** = the landed REPLACE sets (43 months each, nothing to run).
2. **Screen** all combinations with scorer A (exhaustive while prod (N_s+1) <= ~10^6; otherwise stepwise only).
3. **Exact verification, in stages (each stage keeps the engine hours small):**
   a. all PAIRS of slots among the top m = 3 passers per slot (by scorer A single-slot rank) plus the scorer's top 10 pairs outside that set;
   b. forward stepwise: start from today's stack; at each step the scorer ranks "add the replacement that most improves the stack" (L6M ulcer first, then mean $; L3M not worse; no RED prior year; persistence >= 0.58); the top K = 5 additions per step are run exactly (L6M 6 months first, the other 37 months only for the best 2); then backward: try removing each replacement, accept if the exact stack improves;
   c. the best few (F = 3) get 30 date-shift controls (both replacement event streams shifted together by the same +-7..35 days (same weekday); 6 months each) and the JOINT layer refit (section 5).
4. **Cost** (set-months; one full evaluation of one combination = 43 months: L6M 6 with L3M inside, prior years 37; S = number of slots with at least one passer; N = passers per slot; layers for the k = min(S,4) replaced slots of each final combination: 1,122 + 432 (k-1) set-months, W-LAYERS' per-candidate cost 432 fit + 590 prior years + 100 joint, plus 432 per extra replaced book):
| S | N per slot (total passers) | all pairs of slots | all triples | exhaustive (all combos) | PLAN: top-3 pairs + stepwise + controls (540) + layers | PLAN total |
|---|---|---|---|---|---|---|
| 2 (Asia A7 + NY AM K7: today) | 3 (6) | 387 | 0 | 387 | 387 + 516 + 540 + 4,662 | **6,105** |
| 2 | 10 (20) | 4,300 | 0 | 4,300 | same PLAN | **6,105** |
| 2 | 30 (60) | 38,700 | 0 | 38,700 | same | **6,105** |
| 2 | 100 (200) | 430,000 | 0 | 430,000 | same | **6,105** (exhaustive 430k = 5 h at 86k/h: no: 120 h at the fleet rate) |
| 5 (one session) | 3 (15) | 3,870 | 11,610 | 43,300 | 3,870 + 1,290 + 540 + 7,254 | **12,954** |
| 5 | 10 (50) | 43,000 | 430,000 | 6.9 M | same PLAN | **12,954** |
| 5 | 30 (150) | 387,000 | 11.6 M | 1.2 x 10^9 | same | **12,954** |
| 5 | 100 (500) | 4.3 M | 430 M | 4.5 x 10^11 | same | **12,954** |
| 10 (Asia 5 + NY AM 5: worst case) | 3 (30) | 17,415 | 139,320 | 4.5 x 10^7 | 17,415 + 2,580 + 540 + 7,254 | **27,789** |
| 10 | 10 (100) | 193,500 | 5.2 M | 1.1 x 10^12 | same PLAN | **27,789** |
| 10 | 30 (300) | 1.74 M | 139 M | 3.5 x 10^16 | same | **27,789** |
| 10 | 100 (1,000) | 19.4 M | 5.2 x 10^9 | 4.8 x 10^21 | same | **27,789** |
At the current fleet rate (HEALTH.md: ~3,000-3,800 set-months/h) 27,789 set-months is about 8 h, and the fast path (x2 on eligible kinds) halves it; exhaustive runs are impossible beyond S = 2 with N <= 10 (S = 2: 4,300 pairs = 1.3 h). So: for S <= 2 and N <= 10 run ALL pairs exactly; otherwise screen + stepwise + top-3 pairs covers the search with a cost independent of N, and the stage-wise exact checks (6 months first) cut the stepwise line about 5x.
Not included: the first looks and per-candidate follow-ups of the passers themselves (those are stage-1 ladder work), and the re-fit of controls for individual passers (already counted there).

## 4. How combinations are judged (standing rules)
Drawdown first (stack ulcer, max DD, worst week), then dollars (mean $/week); L6M pick with L3M beside; each prior year 2023 / 2024 / 2025 vs today's stack by rule B (> 30% worse RED, 15-30% AMBER; no RED year); engine persistence of the combined stack vs today's >= 0.58 pooled; 30 date-shift controls on the final few; REPLACE only. Deliverable table (one row per stack): today's stack / best combination / next best few; columns: slot fillers (Asia A7 / H7 / K7 / P7 / U7, NY AM H7 / K7 / M7 / O7 / P7: live book or passer id), L6M and L3M (ulcer, max DD, worst week, mean $/wk), 2023 / 2024 / 2025 (the same four + colour), persistence (pooled, blocks), controls (rank of the real combination among the 30 shifted ones), base and x1.75 dollars, and the verdict. Page: `autopilot/D8_COMBINATION_RESULT.md` (written when the ladders are complete).

## 5. Layers: JOINT refit of the final combinations
Per-passer layers were fitted one book at a time on the REPLACE base (W-LAYERS: identity, 72 fit sets x 6 months, scoring, top-2 prior years, joint). For a final combination of k replacements:
1. Build the combined base set (section 1) with each passer's fitted layers keyed by its own tag MFi.
2. JOINT stage = all layers varied together on the combined stack: the layer generator (`code/th_layers/layer_gen.py`, validated against the 81 XA3 sets) gets a `tag` argument and a `base_set` argument (the combined set JSON instead of the single REPLACE set) and emits, per layer, the setting grid for every replaced book at once (one book's setting varied while the others stay at their individually fitted best, 72 settings x k books x 6 months), then the best joint setting of each layer across books is combined (the "joint" sets, about 100 set-months), then the prior years (37 months) of the joint winner. Cost 432 k + 590 + 100 per combination (section 3).
3. The DAY-DONE setting and the account layers (L10, caps, locks, sizer) are varied once on the combined stack (they are stack-level, not book-level).
4. Judged with the same rules; the pick is the joint refit winner if it beats the one-at-a-time layers on L6M + L3M without a RED year, else the one-at-a-time layers stay.

## 6. Dry run on the provisional REPLACE passers (results)
(filled in below when the exact runs land)
