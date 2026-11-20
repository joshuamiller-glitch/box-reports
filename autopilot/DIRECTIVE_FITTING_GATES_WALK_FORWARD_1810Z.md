# ORDER 20261120_1810Z: Josh: how fitted settings are judged (walk-forward, not luck copies)
Josh's own words, 18:04-18:05Z: **"i just want D8 to be fit properly - if you keep coming up short on fitting and failing the luck test with D8 then maybe the test sucks or fitting too tight"**, and to the relay's proposal below: **"this is correct send it"**

The proposal he approved (relay's wording):

WHY: the date-shift luck test asks whether a setting helps the real book more than 27 of 30 shifted copies. That is the right gate for ENTRIES (a trigger, a filter, a time window, an entry method: things that must be signal-specific). It is the wrong gate for RISK-MANAGEMENT layers and brackets: a good loss cut, lock, take, cap or bracket lowers drawdown on almost any stream of trades, so it helps the shifted copies too and "fails" for being robust.

NEW GATES FOR FITTED SETTINGS (book-level layers: take, lock, loss cut, context cut, own cap, near-target latch, target shave, state cut; bracket size and shape; exits; account-level layers in the joint fit):
1. PICK on recent data (last 6 months with last 3 beside it, drawdown first, equal-risk dollars), as now.
2. WALK-FORWARD through history: pick on the trailing window, score the next 2 weeks, repeat across the whole history; the fitted version must beat the unfitted (bare / reference-row) version in at least 58% of periods (persistence >= 0.58), drawdown first.
3. PRIOR YEARS "not a disaster": in each of 2023, 2024, 2025 the fitted version is no worse than the unfitted version by more than the 15-30% band (amber 15-30% reported, red > 30% fails) on ulcer and $/wk at equal risk. NOT "positive in every prior year" as a hard fail for a fitted pick: Josh's standing rule is the tolerant gate.
4. BEST-OF-MANY CHECK stays: the search-aware null (the same screen and pick rule on random-entry books; the real pick's gain must beat at least 4 of 5 null draws). This is what guards against picking a fluke out of 56 settings.
5. The 27-of-30 date-shift count is still COMPUTED and SHOWN for fitted settings, as information, but it is NOT a gate for them.
UNCHANGED: for books themselves and for anything signal-specific (triggers, pass-2 confluence / gates / time windows / entry method) the own-checks gates stand: recent positive, prior years positive, persistence >= 0.58, >= 27 of 30 luck controls.

FITTING ITSELF:
6. Nothing is dropped at the one-setting-at-a-time screen. The screen only ranks: the top 2-3 settings per layer (plus the reference row) ALL go into the joint stage; the verdict comes from the joint fit (all layers varied together), judged by gates 2-4.
7. RE-SCORE under these gates, without re-running what has landed where the data exist: (a) the bracket-shape winners (7 Asia books so far; "0 passed" was under the old rule); (b) the exit sets that lowered drawdown in both recent windows and failed only on the luck copies or on one weak prior year (Asia pool on unaffected bars; NY AM L488784d8 already passes); (c) the layer picks (L15f14deb 12/30 and every book since). Say for each what changes.
8. Pages: ASIA_STAGE1_FIT.md, BRACKET_SHAPES_*.md, EXIT_CANC.md / EXIT_POOL_VERDICT*.md show the new verdict columns (walk-forward persistence, prior-year band, null) beside the old 27/30 count, with one plain line per book: fitted setting kept / not kept and why.
Cost and finish time in one line first; this is on the path to the Saturday cut-off, so stage-1 priority.
