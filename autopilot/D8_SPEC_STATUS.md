Updated 2026-11-19 13:38Z by W-NYENG. **RULE (order 1337Z): NO D8 build spec until the Asia AND NY AM ladders are COMPLETE**: every ladder cell has its first look, and every cell that beats a live book has prior years, controls, layers, exit run and the today / REPLACE / ADD pick. No first-wave date. London and NY PM follow (stages 2 and 3).

## STAGE 1 COMPLETE (Asia + NY AM): one date

Rate used: **3905 set-months/h** = tp_admit counter, last hour (DONE files; HEALTH.md 13:35Z says 3,566/h from the last 30 min x 2; the fast-path share of W-FASTLADDER is not in this number: if it adds a measured share the date moves earlier by the same factor). Assumptions in the follow-up rows are marked ~: beaters = 26% of cells (the observed share of NY AM cells with any yes row: uncalibrated, label BETTER), half of the beaters pass the gates (rule B + persistence >= 0.58); per-candidate costs from W-LAYERS (347 layer set-months) and my exit-row count (438). Asia numbers are W-ASIA's own counts; Asia layer / exit work is inside their count only as far as they queue it.

| part | set-months remaining | hours at 3905/h |
|---|---|---|
| NY AM first looks (ADD + REPLACE-K7, last 6 months; ladder 9081 cells, 6493 built; queued 75957 + 2588 unbuilt cells x 12) | 107013 | 27.4 |
| Asia first looks + follow-ups as W-ASIA counts them (69146 queued + ~84758 still to be appended) + my estimate of Asia gate-pass follow-ups (42294: 2.4% beaters under the Asia rule x 3,197 cells, 74 prior-year + 965 per passer) | 196198 | 50.2 |
| NY AM follow-up: REPLACE vs the other live books (P7 / M7 / H7; 2088 queued + rest appended as cells pass stage A) | 148248 | 38.0 |
| NY AM follow-up: prior years 2023-25 for every cell that beats a live book (~2361 cells at the observed 26% yes-rate x 2 variants x 37 months; 6929 queued) | 174714 | 44.7 |
| NY AM follow-up: 30 date-shift controls for gate-pass candidates (~1180 cells = 50% of beaters x 180 per variant; 1232 queued) | 212400 | 54.4 |
| NY AM follow-up: layers one at a time then joint (gate-pass candidates x ~347 set-months each, the W-LAYERS cost per candidate; known 29 candidates: 4677 remaining per W-LAYERS) | 409460 | 104.9 |
| NY AM follow-up: exit-recipe engine rows (gate-pass candidates x 438; families unbuilt, W-EXITENG) | 516840 | 132.4 |
| **TOTAL** | **1764873** | **452.0 h = 18.8 days** |

**STAGE 1 COMPLETE DATE: 2026-12-08 09:35Z** (all parts at 3905/h with the whole fleet on Asia + NY AM). Biggest uncertainty: how many cells beat a live book and pass the gates (each gate-pass candidate costs ~965 set-months after its first look); the null calibration (R4) and the persistence/rule-B gates decide that number; first looks alone (NY AM 107013 + Asia part) end 2026-11-21 10:45Z.

SENSITIVITY (the beater share is the unknown): with REPLACE-only beaters at ~3.3% of NY AM cells (4 of 122 finished REPLACE verdicts) instead of 26%, the four NY AM follow-up rows that scale with beaters shrink ~8x and the total becomes ~615636 set-months = 158 h (2026-11-26 03:17Z). The true value lies between; the null calibration (R4) decides.

## ENGINE-SLOT SPLIT between the two ladders (proposal; the lead applies it)

Today NY AM lands ~136 set-months/h because strict file order puts Asia ahead of the NY AM ladder (QUEUES.txt: _asi/pending.txt before _nye/pending_r5.txt). The order says NY AM ~120 set-months/h: that would leave NY AM 13072 h behind Asia (1568675 set-months / 120 per hour), so the two ladders do NOT end together at that share. To end both at the same time the split follows the remaining work: **NY AM 89% (3471 set-months/h) / Asia 11% (434 set-months/h)** at 3905/h total; both end about 2026-12-08 09:35Z. Follow-ups of gate-pass candidates stay FIRST in both ladders (they are the first lines of pending_l.txt / the front of pending_r5.txt and the Asia equivalents; the mix takes them unmixed).

**Exact edit (the lead applies; I prepared the generator, nothing changed yet):** (1) QUEUES.txt: replace the two lines `/mnt/l2/l2vast/_asi/pending.txt` and `/mnt/l2/l2vast/_nye/pending_r5.txt` by ONE line `/mnt/l2/l2vast/_split/pending_mix.txt` at the position of the first of them (the dispatchers take the first unstarted line, so strict file order cannot share; the mix file interleaves in the ratio NY AM : Asia = 89 : 11 in blocks of 20 lines after the candidate follow-ups). (2) My cron `code/th_nyeng/ny_mix.py` rebuilds the mix file every 15 min from the two source queues (read-only on them; the two sources keep being re-ordered by their own scripts; completed lines drop out because they are DONE-checked). (3) PRIORITY.txt (box 1 only): ASI quota and NYR quota in the same ratio, e.g. NYR 21 / ASI 3 of the box-1 engine slots. Coordinate: W-ASIA keeps its reorder of _asi/pending.txt (source file), I keep pending_r5.txt.

## Early-rung exits (4c): lines queued for cells that already left the ladder

Cells with stage "out" in the NY advance state: 6. Later-rung lines (other-book, prior-year, control) still queued for them: **0** (the advance step only queues a later rung after the earlier one passes, so none were queued; first-look lines of out cells are the rung that made them out). Park rule: any such line goes to /mnt/l2/l2vast/_nye/parked_out_cells.txt (not deleted). Exclusion list for W-DEDUP: cell ids with stage out = L02831614, La6a45b1a, La8f7d729, La96d4160, Lfa5912ed, Lfd4c2d53 (file: /mnt/l2/l2vast/_nye/ladder_adv_state.json, key stage starting with "out"); W-DEDUP does the sweep, I own the advance logic.


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
