Updated 2026-11-19 15:00Z by W-NYENG. **RULE (order 1337Z): NO D8 build spec until the Asia AND NY AM ladders are COMPLETE**: every ladder cell has its first look, and every cell that beats a live book has prior years, controls, layers, exit run and the today / REPLACE / ADD pick. No wave dates. London and NY PM follow (stages 2 and 3). Funnel model redone at 14:00Z from landed data (order 1400Z).

## STAGE 1 COMPLETE (Asia + NY AM): THREE dates from a funnel with explicit stage pass rates, at the current rate **2404 set-months/h** (HEALTH.md fleet rate; tp_admit last hour says a different number at times; W-COMPILED factor not yet available, W-FASTLADDER share not included)

**Funnel stages and rates read from landed NY AM data:** (1) first look: 128 of 9081 ladder cells have REPLACE last-6-month + last-3-month rows; (2) BEATER under the W-ASIA gate (a REPLACE row beats today stack on BOTH L6M and L3M: ulcer lower, mean not lower, worst week and max DD not worse): **1.6% of looked-at cells (2 of 128); 0.8% with a REPLACE-K7 row; the looser rule (ulcer < 0 and mean >= 0 only) gives 4.7% (6)** (uncalibrated, label BETTER; calibration caveat: the whole-search null gives per-mode FDR both-side 8-25%, long-only 12-18%, i.e. a share of these yes rows is noise); (3) PASS prior years + persistence (rule B: no RED year in 2023/24/25; pooled persistence >= 0.58): **2 of 3 yes rows with all three prior years landed pass = 67%** (2 of 3 cells); the 4 REPLACE-K7 beaters: 3 pass (L01811caa, L6a25b155 pass, L0f097450 RED 2023); Asia: 8 passers among the beaters evaluated (W-ASIA); (4) only PASSERS get 30 controls (ADD and REPLACE variants: 2 x 180), layers (347, W-LAYERS cost) and exit rows (438) = 1106 set-months per passer; every beater gets prior years (37 per beating REPLACE set). REPLACE ONLY (order 1407Z): ADD rows are reference, not candidates, and are no longer queued; exit rows = top 3 recipes x REPLACE x (6+37) + 30 controls x 6 = 309.

**Remaining set-months that do NOT depend on the funnel:** NY AM first looks, REPLACE rows only, 42676 (27148 queued + 2588 unbuilt cells x 6; 6493 of 9081 cells built) + NY AM REPLACE vs the other live books for alive cells 148248 + Asia useful work as W-ASIA counts it after its gate (first looks 27k + a2 35k = 62000; follow-ups 4k prior years + 20k controls + 1.6k passer controls + 8 passers x layers/exit = 31880; total ~88k+). GATE applied to NY AM in the advance step at 14:25Z (same as Asia): prior years and controls only for sets that beat today stack on BOTH L6M and L3M; other cells wait in stage A2 for their a2 rows and drop out if none beats; 6,290 prior-year/control lines of non-beating sets were PARKED (parked_gate_1415.txt, 112 cells; 76 cells returned to A2).

| scenario | NY AM beaters share / pass rate | NY AM beaters -> passers | Asia beaters share / pass | NY AM follow-ups | Asia follow-ups | TOTAL set-months | hours | **STAGE 1 COMPLETE** |
|---|---|---|---|---|---|---|---|---|
| LOW (strict gate, half the measured share) | 0.8% / 50% | 71 -> 35 | 2.2% / 50% | 45795 | 15940 | 314659 | 131 | **2026-11-25 01:53Z** |
| BASE (STRICT gate, measured share less mid FDR) | 1.3% / 67% | 118 -> 79 | 3.0% / 67% | 98318 | 21736 | 372978 | 155 | **2026-11-26 02:09Z** |
| HIGH (strict gate, 3x: the a2 other-book rows add chances) | 4.7% / 80% | 426 -> 341 | 4.4% / 80% | 416009 | 31880 | 700813 | 292 | **2026-12-01 18:31Z** |
| VARIANT: LOOSER gate (ulcer < 0 and mean >= 0 only), measured share less mid FDR | 3.9% / 67% | 355 -> 237 | 3.0% / 67% | 294953 | 21736 | 569613 | 237 | **2026-11-29 11:56Z** |
| UPPER BOUND: every REPLACE beater gets everything (10% NY AM / 6.5% Asia) | 10.0% / 100% | 908 -> 908 | 6.5% / 100% | 1088358 | 47095 | 1388377 | 578 | 2026-12-13 16:31Z |

Scenario assumptions (REPLACE ONLY, STRICT gate = ulcer lower, mean not lower, worst week and max DD not worse on L6M and L3M): measured strict share 1.6%; LOW = half of it, 50% pass; BASE = the measured share minus the mid FDR 16.5% (calibration), pass rate = observed on the loose REPLACE yes rows (67%); HIGH = 3x the strict share, 80% pass; the LOOSER-gate row is a variant only. SMALL SAMPLE: 128 REPLACE looks. Asia beater share 2.4% (W-ASIA strict rule: 15 of 614) / 4.4% / 6.5% (looser rule 50 of 766), Asia pass rates as NY AM. First looks alone (NY AM 42676 + Asia 62000) end 2026-11-21 10:32Z. CAVEAT: the observed beater share comes from the cells looked at so far, which are the BEST screen-ranked ones (the ladder runs in rank order), so extrapolating it to all 9,081 cells over-states the BASE and HIGH rows; the true beater share of the tail is probably lower (LOW is the REPLACE-only bound). The biggest remaining uncertainty is the beater and pass share; the null calibration (R4) and the persistence/rule-B gates move it.

## ENGINE-SLOT SPLIT (re-proposed from remaining FIRST LOOKS, then gate-pass follow-ups; NOT applied)

Remaining first looks: Asia 62000 vs NY AM 42676 (+148248 NY AM other-book rows) => **Asia 59% / NY AM 41%** (25% / 75% with the other-book rows) = ~589 / ~1815 set-months/h at 2404/h; with the base-case follow-ups added the work ratio is NY AM 78% / Asia 22% (NY AM follow-ups 98318 vs Asia 21736): the follow-ups only exist for cells that pass, so they come AFTER the first looks, are small until prior years land, and are taken first by the mix when they appear. Proposal: start at **Asia 59% / NY AM 41%** (remaining first looks only; the other-book REPLACE rows are ordered behind the first looks of both ladders) and re-propose when the funnel is re-measured (each refresh of this page recomputes it). W-ASIA's passer controls (_asi/first.txt) stay first, my gate-pass follow-ups stay first in pending_l.txt / the front of pending_r5.txt; the mix file puts both unmixed ahead of the interleaved block. NY AM at the order's ~120/h would leave 2410 h of work. NOT applied: the QUEUES.txt edit (replace the _asi/pending.txt and _nye/pending_r5.txt lines by /mnt/l2/l2vast/_split/pending_mix.txt, built by code/th_nyeng/ny_mix.py <NYAM share>, e.g. 0.41) waits for the lead.

## Early-rung exits (4c): lines queued for cells that already left the ladder

Cells with stage "out" in the NY advance state: 7. Later-rung lines (other-book, prior-year, control) still queued for them: **0** (the advance step queues a later rung only after the earlier one passes). Park rule: any such line goes to /mnt/l2/l2vast/_nye/parked_out_cells.txt (not deleted). Exclusion list for W-DEDUP: cell ids with stage out = L02831614, L0f097450, La6a45b1a, La8f7d729, La96d4160, Lfa5912ed, Lfd4c2d53 (file /mnt/l2/l2vast/_nye/ladder_adv_state.json, key stage starting with "out"); W-DEDUP does the sweep, I own the advance logic.


## Candidates under the persistence >= 0.58 gate and the ADD-vs-REPLACE rule (order 1324Z)

Rules (order 1407Z): REPLACE ONLY. The pick is always the REPLACE row; the ADD row is shown as a reference, not a candidate (supersedes the 1324Z ADD rule). REPLACE = the ADD stack with K7 switched off in the NY AM session, so the ADD stack WITHOUT K7 already exists as the REPLACE row: NO new "minus K7" engine set is needed (a K7-off-in-every-session set would only matter for K7's other sessions, which these rows leave untouched). Persistence = share of non-overlapping 2-week windows where the new stack is not worse than today's, POOLED over every month the set has run (last 6 months + prior years). Rule B colours from ny_ruleb (RED > 30% worse in a prior year). Stack columns are the whole stack (ulcer / max DD / worst week / mean $ per week, engine base lots, $4.84).

| cell | stack | window | ulcer | max DD | worst wk | mean $/wk | rule-B colour (worst %) |
|---|---|---|---|---|---|---|---|
| L01811caa | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L01811caa | REPLACE (candidate) | L6M | 9342 | -29253 | -15108 | +20510 | n/a (recent window) (-1%) |
| L01811caa | ADD (reference, not a candidate) | L6M | 8963 | -27538 | -14519 | +19873 | n/a (recent window) (-5%) |
| L01811caa | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L01811caa | REPLACE (candidate) | L3M | 10587 | -28995 | -13266 | +18707 | n/a (recent window) (-4%) |
| L01811caa | ADD (reference, not a candidate) | L3M | 10165 | -27538 | -11702 | +17640 | n/a (recent window) (-8%) |
| L01811caa | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L01811caa | REPLACE (candidate) | Y2025 | 29382 | -83155 | -34691 | +7360 | GREEN (-8%) |
| L01811caa | ADD (reference, not a candidate) | Y2025 | 27815 | -78940 | -38025 | +7984 | GREEN (-2%) |
| L01811caa | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L01811caa | REPLACE (candidate) | Y2024 | 24716 | -69388 | -39713 | +5169 | GREEN (+6%) |
| L01811caa | ADD (reference, not a candidate) | Y2024 | 25450 | -71363 | -38560 | +5073 | GREEN (+3%) |
| L01811caa | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L01811caa | REPLACE (candidate) | Y2023 | 15029 | -46397 | -21702 | +2254 | AMBER (+24%) |
| L01811caa | ADD (reference, not a candidate) | Y2023 | 16062 | -40960 | -18785 | +2944 | GREEN (+7%) |
| L6a25b155 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L6a25b155 | REPLACE (candidate) | L6M | 9238 | -29945 | -16733 | +19675 | n/a (recent window) (+6%) |
| L6a25b155 | ADD (reference, not a candidate) | L6M | 8981 | -28489 | -15872 | +19216 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L6a25b155 | REPLACE (candidate) | L3M | 10415 | -29945 | -16733 | +17400 | n/a (recent window) (+6%) |
| L6a25b155 | ADD (reference, not a candidate) | L3M | 10159 | -28489 | -15872 | +17034 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L6a25b155 | REPLACE (candidate) | Y2025 | 34575 | -93892 | -39081 | +7356 | GREEN (+3%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2025 | 31437 | -91723 | -43606 | +8231 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2024 | 28814 | -72026 | -37355 | +4549 | - |
| L6a25b155 | REPLACE (candidate) | Y2024 | 31815 | -69700 | -36113 | +5300 | GREEN (+10%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2024 | 32304 | -71936 | -34960 | +5448 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L6a25b155 | REPLACE (candidate) | Y2023 | 18087 | -48220 | -18408 | +2404 | AMBER (+15%) |
| L6a25b155 | ADD (reference, not a candidate) | Y2023 | 15491 | -42932 | -16215 | +3088 | GREEN (+3%) |
| L0f097450 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L0f097450 | REPLACE (candidate) | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L0f097450 | ADD (reference, not a candidate) | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L0f097450 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L0f097450 | REPLACE (candidate) | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L0f097450 | ADD (reference, not a candidate) | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L0f097450 | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L0f097450 | REPLACE (candidate) | Y2025 | 27735 | -77634 | -32511 | +6709 | GREEN (+2%) |
| L0f097450 | ADD (reference, not a candidate) | Y2025 | 26308 | -76028 | -34457 | +7579 | GREEN (-11%) |
| L0f097450 | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L0f097450 | REPLACE (candidate) | Y2024 | 26900 | -63077 | -38237 | +5219 | GREEN (+2%) |
| L0f097450 | ADD (reference, not a candidate) | Y2024 | 28023 | -66257 | -35122 | +5297 | GREEN (-3%) |
| L0f097450 | TODAY (JL3) | Y2023 | 19039 | -41848 | -17538 | +1797 | - |
| L0f097450 | REPLACE (candidate) | Y2023 | 17341 | -46048 | -25258 | +1675 | RED (+44%) |
| L0f097450 | ADD (reference, not a candidate) | Y2023 | 16744 | -46713 | -19840 | +2334 | GREEN (+13%) |
| L3701b464 (twin of L0f097450) | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L3701b464 (twin of L0f097450) | REPLACE (candidate) | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L3701b464 (twin of L0f097450) | ADD (reference, not a candidate) | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L3701b464 (twin of L0f097450) | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L3701b464 (twin of L0f097450) | REPLACE (candidate) | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L3701b464 (twin of L0f097450) | ADD (reference, not a candidate) | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L3701b464 (twin of L0f097450) | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L3701b464 (twin of L0f097450) | REPLACE (candidate) | Y2025 | 27735 | -77634 | -32511 | +6709 | GREEN (+2%) |
| L3701b464 | ADD | Y2025 | pending | | | | |
| L3701b464 (twin of L0f097450) | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L3701b464 (twin of L0f097450) | REPLACE (candidate) | Y2024 | 26900 | -63077 | -38237 | +5219 | GREEN (+2%) |
| L3701b464 | ADD | Y2024 | pending | | | | |
| L3701b464 (twin of L0f097450) | TODAY (JL3) | Y2023 | 19039 | -41848 | -17538 | +1797 | - |
| L3701b464 (twin of L0f097450) | REPLACE (candidate) | Y2023 | 17341 | -46048 | -25258 | +1675 | RED (+44%) |
| L3701b464 | ADD | Y2023 | pending | | | | |

| cell | pooled persistence REPLACE (months) | pooled persistence ADD (months) | RED years REPLACE / ADD | PICK | what is still needed |
|---|---|---|---|---|---|
| L01811caa | 0.59 (43 mo) | 0.60 (43 mo) | none / none | **REPLACE** (REPLACE: better on ulcer and mean $/wk, no RED year, pooled persistence 0.59 >= 0.58) [STRICT PASS (ulcer, mean, worst week and max DD all not worse on L6M and L3M)] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L6a25b155 | 0.59 (43 mo) | 0.65 (43 mo) | none / none | **REPLACE** (REPLACE: better on ulcer and mean $/wk, no RED year, pooled persistence 0.59 >= 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $1005; WORST WEEK L3M worse by $1005: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L0f097450 | 0.55 (43 mo) | 0.58 (43 mo) | Y2023 / none | **none yet** (REPLACE: RED Y2023; persistence 0.55 < 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $3120; WORST WEEK L3M worse by $3120: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L3701b464 (twin of L0f097450) | 0.55 (43 mo) | 0.59 (10 mo) | Y2023 / none | **none yet** (REPLACE: RED Y2023; persistence 0.55 < 0.58) [fails the STRICT criterion: WORST WEEK L6M worse by $3120; WORST WEEK L3M worse by $3120: BEST-AVAILABLE-NOT-PROVEN, Josh decides] | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |

**Candidates passing recent months + no RED year + persistence >= 0.58:** L01811caa (REPLACE), L6a25b155 (REPLACE).
**Dates:** 30 controls: queued at the front (landing as the fleet reaches them, ~06 hours at 2,000 sm/h); layers + exit run: the layer programme per candidate is ~1,068 set-months (about 0.5 h of fleet) but needs the automatic layer builder (not built, my ETA 2026-11-20 12:00Z) and the exit engine families (builder not started); so the earliest "through everything" date for L01811caa and L6a25b155 (they stay first) is 2026-11-21 ~12:00Z, later if the exit engine builder starts late. L0f097450 (= L3701b464, same stream) is judged by the same ADD/REPLACE rule.

## STRICT criterion table (Asia / D8 rule: stack ulcer LOWER, mean $/wk NOT LOWER, worst week NOT WORSE, max DD NOT WORSE; L6M with L3M beside; REPLACE-K7 vs TODAY stack; engine base lots, $4.84)
| cell | window | metric | today | REPLACE-K7 | change | pass |
|---|---|---|---|---|---|---|
| L01811caa | L6M | stack ulcer (lower = better) | +9416 | +9342 | -75 | PASS |
| L01811caa | L6M | max drawdown | -31109 | -29253 | +1857 | PASS |
| L01811caa | L6M | worst week | -15728 | -15108 | +620 | PASS |
| L01811caa | L6M | mean $/wk | +18755 | +20510 | +1755 | PASS |
| L01811caa | L3M | stack ulcer (lower = better) | +11035 | +10587 | -448 | PASS |
| L01811caa | L3M | max drawdown | -31109 | -28995 | +2114 | PASS |
| L01811caa | L3M | worst week | -15728 | -13266 | +2462 | PASS |
| L01811caa | L3M | mean $/wk | +16098 | +18707 | +2609 | PASS |
| L01811caa | both | STRICT VERDICT | | | | **PASS** |
| L6a25b155 | L6M | stack ulcer (lower = better) | +9416 | +9238 | -178 | PASS |
| L6a25b155 | L6M | max drawdown | -31109 | -29945 | +1164 | PASS |
| L6a25b155 | L6M | worst week | -15728 | -16733 | -1005 | **FAIL** |
| L6a25b155 | L6M | mean $/wk | +18755 | +19675 | +919 | PASS |
| L6a25b155 | L3M | stack ulcer (lower = better) | +11035 | +10415 | -620 | PASS |
| L6a25b155 | L3M | max drawdown | -31109 | -29945 | +1164 | PASS |
| L6a25b155 | L3M | worst week | -15728 | -16733 | -1005 | **FAIL** |
| L6a25b155 | L3M | mean $/wk | +16098 | +17400 | +1301 | PASS |
| L6a25b155 | both | STRICT VERDICT | | | | **FAIL** |
| L0f097450 | L6M | stack ulcer (lower = better) | +9416 | +9358 | -58 | PASS |
| L0f097450 | L6M | max drawdown | -31109 | -29253 | +1857 | PASS |
| L0f097450 | L6M | worst week | -15728 | -18848 | -3120 | **FAIL** |
| L0f097450 | L6M | mean $/wk | +18755 | +21047 | +2291 | PASS |
| L0f097450 | L3M | stack ulcer (lower = better) | +11035 | +10531 | -504 | PASS |
| L0f097450 | L3M | max drawdown | -31109 | -28828 | +2281 | PASS |
| L0f097450 | L3M | worst week | -15728 | -18848 | -3120 | **FAIL** |
| L0f097450 | L3M | mean $/wk | +16098 | +19000 | +2902 | PASS |
| L0f097450 | both | STRICT VERDICT | | | | **FAIL** |

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
| L3701b464 (twin of L0f097450) | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L3701b464 (twin of L0f097450) | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L3701b464 (twin of L0f097450) | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L3701b464 | both sides ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 (twin of L0f097450) | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L3701b464 (twin of L0f097450) | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L3701b464 (twin of L0f097450) | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L3701b464 (twin of L0f097450) | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L3701b464 (twin of L0f097450) | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L3701b464 (twin of L0f097450) | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
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
- L3701b464 both sides REPLACE K7: RED year
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
