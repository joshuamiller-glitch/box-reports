Updated 2026-11-19 13:24Z by W-NYENG. PRIORITY (order 0220Z): 1 Asia, 2 NY AM, 3 London, 4 NY PM (nothing dropped). Rule: a new book enters D8 when it beats the live book(s) it replaces in the exact engine vs TODAY's stack (drawdown first, then $/wk; L6M + L3M; no RED prior year; persistence > 0.60; 30 date-shift controls) AND has had the exit run on its own entries; "BETTER, calibration pending" until the calibration exists.

| order | session | D8 candidates | REPLACE rows finished | beats live book: yes / no / pending | exit run | date decided |
|---|---|---|---|---|---|---|
| 1 | Asia | 5654 REPLACE rows listed in D8_CANDIDATES.txt (758 cells with engine rows; 15 beat a live Asia book) | 613 | 15 yes / 598 finished-no / 16 pending | pending (exit screen takes Asia cells as their REPLACE rows land) | not decided; engine-only estimate Asia first ~Nov 21 04:00Z (W-ASIA, page NEW_BOOK_BEATS_LIVE_ASIA.md) |
| 2 | NY AM | 6844 REPLACE rows listed in D8_CANDIDATES.txt (187 cells with engine rows; 4 cells beat a live book) | 122 | 4 / 118 / 19 | pending (NOT started) | not decided; earliest 2026-11-20 12:00Z if the exit screen starts by 11-19 06:00Z |
| 3 | London | W-LONENG: NEW_BOOK_ENGINE_LONDON.md | n/a here | n/a here | pending | not decided |
| 4 | NY PM (behind NY AM in every W-NYENG file) | 787 REPLACE rows listed (0 cells with engine rows) | 0 | 0 / 0 / 0 | pending | not decided (nothing run yet; queued behind NY AM) |

Missing for each candidate: prior years 2023-25 without a RED year, the 30 date-shift controls, persistence > 0.60, exit run (68 recipes): NOT started on these candidates (screen stage owner; engine families trailing / staged / SAR 11-19 18:00Z, order flow 11-20 12:00Z, D8_EXIT_ENGINE_SUPPORT.md), then the engine confirmation of the top 3 recipes (ADD + REPLACE, L6M + L3M, prior years, 30 controls = 438 set-months per candidate).

D8 SPEC DATE (Asia + NY AM only): the engine cost after the exit screen for the 4 NY AM cells that beat a live book today is 1752 set-months = 1.9 h at the measured 928 set-months/h (0.6 h at 2,894/h). The date is set by the exit-screen stage and the unbuilt engine exit families, not by the engine queue: earliest 2026-11-20 12:00Z for NY AM, conditional on the exit screen starting by 11-19 06:00Z (duration not measured, candidate list still growing). Asia: W-LONENG's date; the combined date is the later of the two.

## RESTATED DATES (order 0613Z; engine only; TRUE fleet rate 3911 set-months/h = DONE files per hour = tp_admit counter (HEALTH.md 2,722/h double counts: the box-1 tree already holds the pulled results of the other hosts and then each host is added again); computed 13:24Z by W-NYENG, refreshed every 30 min)

| item | set-months | hours at 3911/h | date if the whole fleet worked on it |
|---|---|---|---|
| NY AM ladder STAGE 1 (every cell through ADD + REPLACE-K7 (L6M+L3M) and REPLACE vs P7 / M7 / H7): remaining = pending ADD/K7 lines 75957 + 2588 unbuilt cells x 12 + A2 queued 2088 + A2 still to be appended (alive cells x 18, ~91% alive) 146168 | 255269 | 65.3 | 2026-11-22 06:40Z |
| NY AM prior years queued now (6973 unique lines; the 52 sets that beat the live book on L6M+L3M run FIRST) | 6973 | 1.8 | 2026-11-19 15:11Z |
| Asia ladder (W-ASIA 06:11Z: ~93,000 set-months, measured Asia rate 1,255/h => Nov 22 08:20Z) | ~93,000 | ~34 at the fleet rate | 2026-11-20 13:10Z |
| COMBINED Asia + NY AM stage 1 (priority Asia first, then NY AM; same fleet) | 348269 | 89.0 | 2026-11-23 06:27Z |

FIRST NY AM CANDIDATE THROUGH EVERYTHING (prior years 37 + 30 controls x 6 = 180 + layers one at a time then joint ~1,068 + exit-recipe engine rows 438 = 1723 set-months = 0.44 h of engine at 3911/h): the engine part is short; the date is set by (a) the exit-recipe ENGINE families, NOT BUILT YET at 06:15Z (my commitments: per-entry recipes / opposite-signal exit 11-19 14:00Z-18:00Z, trailing / staged / stop-and-reverse 11-19 18:00Z, order-flow 11-20 12:00Z; every slip moves the date 1:1), (b) the exit screen (W-D8EXIT: NY AM 1,764 of 4,555 screened at 06:00Z, ETA ~4.5 h after Asia), (c) the layer-set builder for an arbitrary candidate (done by hand for XA3; to be automated by 11-19 14:00Z). Earliest: **2026-11-20 06:00Z + engine** (first candidate whose best recipes are per-entry / trailing / staged); order-flow recipes: 2026-11-21 00:00Z.

**D8 SPEC DATE (i) FIRST WAVE** (the 52 NY AM sets that beat a live book on L6M + L3M today, ~89596 set-months through everything = 23 h of engine after the exit engine families exist): **2026-11-21 10:54Z** at the earliest (engine starts when the exit-recipe engine families exist, assumed 2026-11-20 12:00Z; 4 REPLACE-yes cells only: **2026-11-20 13:45Z**). Asia first wave: W-ASIA.
**D8 SPEC DATE (ii) WHOLE LADDER:** stage 1 ends 2026-11-22 06:40Z (combined with Asia 2026-11-23 06:27Z) and then every row that beats a live book needs the 1723 set-months above: at today's 24% yes-rate (about 2179 NY AM cells) that is 3.8 million set-months = 40 days of the whole fleet; the null calibration (R4) is what shrinks it, so a whole-ladder date cannot be given without the calibrated yes-count; first-wave D8 is the realistic first spec. Josh decides machines vs waiting. Lever: restricting the A2 rows (REPLACE vs P7/M7/H7) to cells where ADD or REPLACE-K7 already beats the live book would cut ~102317 set-months (~26 h).

## Candidates under the persistence >= 0.58 gate and the ADD-vs-REPLACE rule (order 1324Z)

Rules: REPLACE is the default. ADD only when (a) the whole stack is better with ADD than with REPLACE (ulcer first, then $/wk; last 6 months with last 3 months; no RED prior year) AND (b) removing K7 from the ADD stack makes L6M and L3M worse. REPLACE = the ADD stack with K7 switched off in the NY AM session, so the ADD stack WITHOUT K7 already exists as the REPLACE row: NO new "minus K7" engine set is needed (a K7-off-in-every-session set would only matter for K7's other sessions, which these rows leave untouched). Persistence = share of non-overlapping 2-week windows where the new stack is not worse than today's, POOLED over every month the set has run (last 6 months + prior years). Rule B colours from ny_ruleb (RED > 30% worse in a prior year). Stack columns are the whole stack (ulcer / max DD / worst week / mean $ per week, engine base lots, $4.84).

| cell | stack | window | ulcer | max DD | worst wk | mean $/wk | rule-B colour (worst %) |
|---|---|---|---|---|---|---|---|
| L01811caa | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L01811caa | REPLACE | L6M | 9342 | -29253 | -15108 | +20510 | n/a (recent window) (-1%) |
| L01811caa | ADD | L6M | 8963 | -27538 | -14519 | +19873 | n/a (recent window) (-5%) |
| L01811caa | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L01811caa | REPLACE | L3M | 10587 | -28995 | -13266 | +18707 | n/a (recent window) (-4%) |
| L01811caa | ADD | L3M | 10165 | -27538 | -11702 | +17640 | n/a (recent window) (-8%) |
| L01811caa | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L01811caa | REPLACE | Y2025 | 29382 | -83155 | -34691 | +7360 | GREEN (-8%) |
| L01811caa | ADD | Y2025 | 27815 | -78940 | -38025 | +7984 | GREEN (-2%) |
| L01811caa | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L01811caa | REPLACE | Y2024 | 24716 | -69388 | -39713 | +5169 | GREEN (+6%) |
| L01811caa | ADD | Y2024 | 25450 | -71363 | -38560 | +5073 | GREEN (+3%) |
| L01811caa | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L01811caa | REPLACE | Y2023 | 15029 | -46397 | -21702 | +2254 | AMBER (+24%) |
| L01811caa | ADD | Y2023 | 16062 | -40960 | -18785 | +2944 | GREEN (+7%) |
| L6a25b155 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L6a25b155 | REPLACE | L6M | 9238 | -29945 | -16733 | +19675 | n/a (recent window) (+6%) |
| L6a25b155 | ADD | L6M | 8981 | -28489 | -15872 | +19216 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L6a25b155 | REPLACE | L3M | 10415 | -29945 | -16733 | +17400 | n/a (recent window) (+6%) |
| L6a25b155 | ADD | L3M | 10159 | -28489 | -15872 | +17034 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L6a25b155 | REPLACE | Y2025 | 34575 | -93892 | -39081 | +7356 | GREEN (+3%) |
| L6a25b155 | ADD | Y2025 | 31437 | -91723 | -43606 | +8231 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2024 | 28814 | -72026 | -37355 | +4549 | - |
| L6a25b155 | REPLACE | Y2024 | 31815 | -69700 | -36113 | +5300 | GREEN (+10%) |
| L6a25b155 | ADD | Y2024 | 32304 | -71936 | -34960 | +5448 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L6a25b155 | REPLACE | Y2023 | 18087 | -48220 | -18408 | +2404 | AMBER (+15%) |
| L6a25b155 | ADD | Y2023 | 15491 | -42932 | -16215 | +3088 | GREEN (+3%) |
| L0f097450 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L0f097450 | REPLACE | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L0f097450 | ADD | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L0f097450 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L0f097450 | REPLACE | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L0f097450 | ADD | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L0f097450 | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L0f097450 | REPLACE | Y2025 | 27735 | -77634 | -32511 | +6709 | GREEN (+2%) |
| L0f097450 | ADD | Y2025 | 26308 | -76028 | -34457 | +7579 | GREEN (-11%) |
| L0f097450 | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L0f097450 | REPLACE | Y2024 | 26900 | -63077 | -38237 | +5219 | GREEN (+2%) |
| L0f097450 | ADD | Y2024 | 28023 | -66257 | -35122 | +5297 | GREEN (-3%) |
| L0f097450 | TODAY (JL3) | Y2023 | 19039 | -41848 | -17538 | +1797 | - |
| L0f097450 | REPLACE | Y2023 | 17341 | -46048 | -25258 | +1675 | RED (+44%) |
| L0f097450 | ADD | Y2023 | 16744 | -46713 | -19840 | +2334 | GREEN (+13%) |
| L3701b464 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L3701b464 | REPLACE | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L3701b464 | ADD | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L3701b464 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L3701b464 | REPLACE | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L3701b464 | ADD | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L3701b464 | all | Y2025 | pending | | | | |
| L3701b464 | all | Y2024 | pending | | | | |
| L3701b464 | all | Y2023 | pending | | | | |

| cell | pooled persistence REPLACE (months) | pooled persistence ADD (months) | RED years REPLACE / ADD | PICK | what is still needed |
|---|---|---|---|---|---|
| L01811caa | 0.59 (43 mo) | 0.60 (43 mo) | none / none | **ADD** (ADD better than REPLACE on L6M+L3M, K7 contributes) | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L6a25b155 | 0.59 (43 mo) | 0.65 (43 mo) | none / none | **ADD** (ADD better than REPLACE on L6M+L3M, K7 contributes) | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L0f097450 | 0.55 (43 mo) | 0.58 (43 mo) | Y2023 / none | **ADD** (ADD stack better than REPLACE on L6M and L3M (so K7 contributes), no RED year, persistence 0.58 >= 0.58) | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L3701b464 | 0.54 (6 mo) | 0.69 (6 mo) | none / none | **none yet** (REPLACE: prior years pending (0/3); persistence 0.54 < 0.58 | ADD: prior years pending (0/3)) | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |

**Candidates passing recent months + no RED year + persistence >= 0.58:** L01811caa (ADD), L6a25b155 (ADD), L0f097450 (ADD).
**Dates:** 30 controls: queued at the front (landing as the fleet reaches them, ~06 hours at 2,000 sm/h); layers + exit run: the layer programme per candidate is ~1,068 set-months (about 0.5 h of fleet) but needs the automatic layer builder (not built, my ETA 2026-11-20 12:00Z) and the exit engine families (builder not started); so the earliest "through everything" date for L01811caa and L6a25b155 (they stay first) is 2026-11-21 ~12:00Z, later if the exit engine builder starts late. L0f097450 (= L3701b464, same stream) is judged by the same ADD/REPLACE rule.

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
