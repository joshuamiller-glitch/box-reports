Updated 2026-11-19 13:00Z by W-NYENG. PRIORITY (order 0220Z): 1 Asia, 2 NY AM, 3 London, 4 NY PM (nothing dropped). Rule: a new book enters D8 when it beats the live book(s) it replaces in the exact engine vs TODAY's stack (drawdown first, then $/wk; L6M + L3M; no RED prior year; persistence > 0.60; 30 date-shift controls) AND has had the exit run on its own entries; "BETTER, calibration pending" until the calibration exists.

| order | session | D8 candidates | REPLACE rows finished | beats live book: yes / no / pending | exit run | date decided |
|---|---|---|---|---|---|---|
| 1 | Asia | 5642 REPLACE rows listed in D8_CANDIDATES.txt (757 cells with engine rows; 15 beat a live Asia book) | 613 | 15 yes / 598 finished-no / 17 pending | pending (exit screen takes Asia cells as their REPLACE rows land) | not decided; engine-only estimate Asia first ~Nov 21 04:00Z (W-ASIA, page NEW_BOOK_BEATS_LIVE_ASIA.md) |
| 2 | NY AM | 6844 REPLACE rows listed in D8_CANDIDATES.txt (187 cells with engine rows; 4 cells beat a live book) | 122 | 4 / 118 / 19 | pending (NOT started) | not decided; earliest 2026-11-20 12:00Z if the exit screen starts by 11-19 06:00Z |
| 3 | London | W-LONENG: NEW_BOOK_ENGINE_LONDON.md | n/a here | n/a here | pending | not decided |
| 4 | NY PM (behind NY AM in every W-NYENG file) | 787 REPLACE rows listed (0 cells with engine rows) | 0 | 0 / 0 / 0 | pending | not decided (nothing run yet; queued behind NY AM) |

Missing for each candidate: prior years 2023-25 without a RED year, the 30 date-shift controls, persistence > 0.60, exit run (68 recipes): NOT started on these candidates (screen stage owner; engine families trailing / staged / SAR 11-19 18:00Z, order flow 11-20 12:00Z, D8_EXIT_ENGINE_SUPPORT.md), then the engine confirmation of the top 3 recipes (ADD + REPLACE, L6M + L3M, prior years, 30 controls = 438 set-months per candidate).

D8 SPEC DATE (Asia + NY AM only): the engine cost after the exit screen for the 4 NY AM cells that beat a live book today is 1752 set-months = 1.9 h at the measured 928 set-months/h (0.6 h at 2,894/h). The date is set by the exit-screen stage and the unbuilt engine exit families, not by the engine queue: earliest 2026-11-20 12:00Z for NY AM, conditional on the exit screen starting by 11-19 06:00Z (duration not measured, candidate list still growing). Asia: W-LONENG's date; the combined date is the later of the two.

## RESTATED DATES (order 0613Z; engine only; TRUE fleet rate 3317 set-months/h = DONE files per hour = tp_admit counter (HEALTH.md 2,722/h double counts: the box-1 tree already holds the pulled results of the other hosts and then each host is added again); computed 13:00Z by W-NYENG, refreshed every 30 min)

| item | set-months | hours at 3317/h | date if the whole fleet worked on it |
|---|---|---|---|
| NY AM ladder STAGE 1 (every cell through ADD + REPLACE-K7 (L6M+L3M) and REPLACE vs P7 / M7 / H7): remaining = pending ADD/K7 lines 75957 + 2588 unbuilt cells x 12 + A2 queued 2088 + A2 still to be appended (alive cells x 18, ~91% alive) 146168 | 255269 | 77.0 | 2026-11-22 17:57Z |
| NY AM prior years queued now (7039 unique lines; the 52 sets that beat the live book on L6M+L3M run FIRST) | 7039 | 2.1 | 2026-11-19 15:07Z |
| Asia ladder (W-ASIA 06:11Z: ~93,000 set-months, measured Asia rate 1,255/h => Nov 22 08:20Z) | ~93,000 | ~34 at the fleet rate | 2026-11-20 17:02Z |
| COMBINED Asia + NY AM stage 1 (priority Asia first, then NY AM; same fleet) | 348269 | 105.0 | 2026-11-23 21:59Z |

FIRST NY AM CANDIDATE THROUGH EVERYTHING (prior years 37 + 30 controls x 6 = 180 + layers one at a time then joint ~1,068 + exit-recipe engine rows 438 = 1723 set-months = 0.52 h of engine at 3317/h): the engine part is short; the date is set by (a) the exit-recipe ENGINE families, NOT BUILT YET at 06:15Z (my commitments: per-entry recipes / opposite-signal exit 11-19 14:00Z-18:00Z, trailing / staged / stop-and-reverse 11-19 18:00Z, order-flow 11-20 12:00Z; every slip moves the date 1:1), (b) the exit screen (W-D8EXIT: NY AM 1,764 of 4,555 screened at 06:00Z, ETA ~4.5 h after Asia), (c) the layer-set builder for an arbitrary candidate (done by hand for XA3; to be automated by 11-19 14:00Z). Earliest: **2026-11-20 06:00Z + engine** (first candidate whose best recipes are per-entry / trailing / staged); order-flow recipes: 2026-11-21 00:00Z.

**D8 SPEC DATE (i) FIRST WAVE** (the 52 NY AM sets that beat a live book on L6M + L3M today, ~89596 set-months through everything = 27 h of engine after the exit engine families exist): **2026-11-21 15:00Z** at the earliest (engine starts when the exit-recipe engine families exist, assumed 2026-11-20 12:00Z; 4 REPLACE-yes cells only: **2026-11-20 14:04Z**). Asia first wave: W-ASIA.
**D8 SPEC DATE (ii) WHOLE LADDER:** stage 1 ends 2026-11-22 17:57Z (combined with Asia 2026-11-23 21:59Z) and then every row that beats a live book needs the 1723 set-months above: at today's 24% yes-rate (about 2179 NY AM cells) that is 3.8 million set-months = 47 days of the whole fleet; the null calibration (R4) is what shrinks it, so a whole-ladder date cannot be given without the calibrated yes-count; first-wave D8 is the realistic first spec. Josh decides machines vs waiting. Lever: restricting the A2 rows (REPLACE vs P7/M7/H7) to cells where ADD or REPLACE-K7 already beats the live book would cut ~102317 set-months (~31 h).

## ENGINE RULE B (prior-year gate) for the 4 NY AM K7 beaters (order 1122Z; full table also on NEW_BOOK_BEATS_LIVE_NYAM.md)

**SIGN CONVENTION (explicit).** Rule B columns below are "% WORSE than today s stack" (positive = WORSE, negative = better): ulcer % = (new-ref)/ref; max DD % and worst week % = (ref-new)/|ref|; mean $/wk % = (ref-new)/|ref| (lower mean = positive = worse). The dollar columns elsewhere on this page: "d ulcer negative = better" (lower ulcer), "d worst week +1,631 = the worst week is $1,631 LESS bad than today s stack", "d max DD positive = less deep", "d mean positive = more $/wk". RED > 30% worse, AMBER 15-30%, GREEN otherwise; cell colour = worst of the four metrics; the verdict needs no RED year; a year with no engine rows yet = pending (not fail).

**Rule B = engine (REPLACE / ADD row vs TODAY s stack, same year).** Rule A (screen: bare stream, prior-year weekly R > 30% worse than the cell s own L6M) only orders the queue and is shown in its own column from the shortlist.

| cell | variant | year | ulcer % worse | max DD % worse | worst wk % worse | mean $/wk % worse | colour | persistence (2-wk windows new stack not worse) | rule A (screen, queue order only) |
|---|---|---|---|---|---|---|---|---|---|
| L01811caa | both sides REPLACE K7 | 2023 | -21% | +11% | +24% | -25% | AMBER | 0.47 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2024 | -14% | -4% | +6% | -14% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2025 | -12% | -9% | -11% | -8% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2023 | -15% | -2% | +7% | -64% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2024 | -12% | -1% | +3% | -12% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides ADD | 2025 | -17% | -14% | -2% | -17% | GREEN | 0.77 | see shortlist |
| L01811caa | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L0f097450 | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L0f097450 | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L0f097450 | both sides ADD | 2023 | -12% | +12% | +13% | -30% | GREEN | 0.53 | see shortlist |
| L0f097450 | both sides ADD | 2024 | -3% | -8% | -6% | -16% | GREEN | 0.54 | see shortlist |
| L0f097450 | both sides ADD | 2025 | -22% | -17% | -11% | -11% | GREEN | 0.69 | see shortlist |
| L0f097450 | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L0f097450 | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L0f097450 | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L0f097450 | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L0f097450 | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L0f097450 | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L0f097450 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L3701b464 | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L3701b464 | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L3701b464 | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L3701b464 | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L3701b464 | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L3701b464 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | both sides REPLACE K7 | 2023 | -4% | +15% | +5% | -34% | AMBER | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2024 | +10% | -3% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2025 | +3% | +3% | +0% | -7% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides ADD | 2023 | -18% | +3% | -8% | -72% | GREEN | 0.79 | see shortlist |
| L6a25b155 | both sides ADD | 2024 | +12% | -0% | -6% | -20% | GREEN | 0.54 | see shortlist |
| L6a25b155 | both sides ADD | 2025 | -6% | +0% | +12% | -20% | GREEN | 0.65 | see shortlist |
| L6a25b155 | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |

**Rule B verdict per row:**
- L01811caa both sides REPLACE K7: no RED year
- L01811caa both sides ADD: no RED year
- L01811caa long-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa long-only ADD: pending (no prior-year rows yet)
- L01811caa short-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa short-only ADD: pending (no prior-year rows yet)
- L0f097450 both sides REPLACE K7: RED year
- L0f097450 both sides ADD: no RED year
- L0f097450 long-only REPLACE K7: no RED year
- L0f097450 long-only ADD: no RED year
- L0f097450 short-only REPLACE K7: pending (no prior-year rows yet)
- L0f097450 short-only ADD: pending (no prior-year rows yet)
- L3701b464 both sides REPLACE K7: pending (no prior-year rows yet)
- L3701b464 both sides ADD: pending (no prior-year rows yet)
- L3701b464 long-only REPLACE K7: no RED year
- L3701b464 long-only ADD: no RED year
- L3701b464 short-only REPLACE K7: pending (no prior-year rows yet)
- L3701b464 short-only ADD: pending (no prior-year rows yet)
- L6a25b155 both sides REPLACE K7: no RED year
- L6a25b155 both sides ADD: no RED year
- L6a25b155 long-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 long-only ADD: pending (no prior-year rows yet)
- L6a25b155 short-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 short-only ADD: pending (no prior-year rows yet)
