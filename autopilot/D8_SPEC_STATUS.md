Updated 2026-11-19 16:00Z by W-NYENG. **RULE (order 1337Z): NO D8 build spec until the Asia AND NY AM ladders are COMPLETE**: every ladder cell has its first look, and every cell that beats a live book has prior years, controls, layers, exit run and the today / REPLACE / ADD pick. No wave dates. London and NY PM follow (stages 2 and 3). Funnel model redone at 14:00Z from landed data (order 1400Z).

## STAGE 1 COMPLETE (Asia + NY AM): THREE dates from a funnel with explicit stage pass rates, at the current rate **3192 set-months/h** (HEALTH.md fleet rate; tp_admit last hour says a different number at times; W-COMPILED factor not yet available, W-FASTLADDER share not included)

**Funnel stages and rates read from landed NY AM data:** (1) first look: 193 of 9081 ladder cells have REPLACE last-6-month + last-3-month rows; (2) BEATER under the W-ASIA gate (a REPLACE row beats today stack on BOTH L6M and L3M: ulcer lower, mean not lower, worst week and max DD not worse): **1.0% of looked-at cells (2 of 193); 0.5% with a REPLACE-K7 row; the looser rule (ulcer < 0 and mean >= 0 only) gives 4.1% (8)** (uncalibrated, label BETTER; calibration caveat: the whole-search null gives per-mode FDR both-side 8-25%, long-only 12-18%, i.e. a share of these yes rows is noise); (3) PASS prior years + persistence (rule B: no RED year in 2023/24/25; pooled persistence >= 0.58): **5 of 6 yes rows with all three prior years landed pass = 83%** (2 of 3 cells); the 4 REPLACE-K7 beaters: 3 pass (L01811caa, L6a25b155 pass, L0f097450 RED 2023); Asia: 8 passers among the beaters evaluated (W-ASIA); (4) only PASSERS get 30 controls (ADD and REPLACE variants: 2 x 180), layers (347, W-LAYERS cost) and exit rows (438) = 1106 set-months per passer; every beater gets prior years (37 per beating REPLACE set). REPLACE ONLY (order 1407Z): ADD rows are reference, not candidates, and are no longer queued; exit rows = top 3 recipes x REPLACE x (6+37) + 30 controls x 6 = 309.

**Remaining set-months that do NOT depend on the funnel:** NY AM first looks, REPLACE rows only, 42394 (26866 queued + 2588 unbuilt cells x 6; 6493 of 9081 cells built) + NY AM REPLACE vs the other live books for alive cells 148248 + Asia useful work as W-ASIA counts it after its gate (first looks 27k + a2 35k = 62000; follow-ups 4k prior years + 20k controls + 1.6k passer controls + 8 passers x layers/exit = 31880; total ~88k+). GATE applied to NY AM in the advance step at 14:25Z (same as Asia): prior years and controls only for sets that beat today stack on BOTH L6M and L3M; other cells wait in stage A2 for their a2 rows and drop out if none beats; 6,290 prior-year/control lines of non-beating sets were PARKED (parked_gate_1415.txt, 112 cells; 76 cells returned to A2).

| scenario | NY AM beaters share / pass rate | NY AM beaters -> passers | Asia beaters share / pass | NY AM follow-ups | Asia follow-ups | TOTAL set-months | hours | **STAGE 1 COMPLETE** |
|---|---|---|---|---|---|---|---|---|
| LOW (strict gate, half the measured share) | 0.5% / 50% | 47 -> 24 | 2.2% / 50% | 30372 | 15940 | 298954 | 94 | **2026-11-23 13:39Z** |
| BASE (STRICT gate, measured share less mid FDR) | 0.9% / 83% | 79 -> 65 | 3.0% / 83% | 79690 | 21736 | 354068 | 111 | **2026-11-24 06:55Z** |
| HIGH (strict gate, 3x: the a2 other-book rows add chances) | 3.1% / 80% | 282 -> 226 | 4.4% / 80% | 275902 | 31880 | 560424 | 176 | **2026-11-26 23:34Z** |
| VARIANT: LOOSER gate (ulcer < 0 and mean >= 0 only), measured share less mid FDR | 3.5% / 83% | 314 -> 262 | 3.0% / 83% | 318759 | 21736 | 593137 | 186 | **2026-11-27 09:49Z** |
| UPPER BOUND: every REPLACE beater gets everything (10% NY AM / 6.5% Asia) | 10.0% / 100% | 908 -> 908 | 6.5% / 100% | 1088358 | 47095 | 1388095 | 435 | 2026-12-07 18:52Z |

Scenario assumptions (REPLACE ONLY, STRICT gate = ulcer lower, mean not lower, worst week and max DD not worse on L6M and L3M): measured strict share 1.0%; LOW = half of it, 50% pass; BASE = the measured share minus the mid FDR 16.5% (calibration), pass rate = observed on the loose REPLACE yes rows (83%); HIGH = 3x the strict share, 80% pass; the LOOSER-gate row is a variant only. SMALL SAMPLE: 193 REPLACE looks. Asia beater share 2.4% (W-ASIA strict rule: 15 of 614) / 4.4% / 6.5% (looser rule 50 of 766), Asia pass rates as NY AM. First looks alone (NY AM 42394 + Asia 62000) end 2026-11-21 00:42Z. CAVEAT: the observed beater share comes from the cells looked at so far, which are the BEST screen-ranked ones (the ladder runs in rank order), so extrapolating it to all 9,081 cells over-states the BASE and HIGH rows; the true beater share of the tail is probably lower (LOW is the REPLACE-only bound). The biggest remaining uncertainty is the beater and pass share; the null calibration (R4) and the persistence/rule-B gates move it.

## ENGINE-SLOT SPLIT (re-proposed from remaining FIRST LOOKS, then gate-pass follow-ups; NOT applied)

Remaining first looks: Asia 62000 vs NY AM 42394 (+148248 NY AM other-book rows) => **Asia 59% / NY AM 41%** (25% / 75% with the other-book rows) = ~783 / ~2409 set-months/h at 3192/h; with the base-case follow-ups added the work ratio is NY AM 76% / Asia 24% (NY AM follow-ups 79690 vs Asia 21736): the follow-ups only exist for cells that pass, so they come AFTER the first looks, are small until prior years land, and are taken first by the mix when they appear. Proposal: start at **Asia 59% / NY AM 41%** (remaining first looks only; the other-book REPLACE rows are ordered behind the first looks of both ladders) and re-propose when the funnel is re-measured (each refresh of this page recomputes it). W-ASIA's passer controls (_asi/first.txt) stay first, my gate-pass follow-ups stay first in pending_l.txt / the front of pending_r5.txt; the mix file puts both unmixed ahead of the interleaved block. NY AM at the order's ~120/h would leave 2253 h of work. NOT applied: the QUEUES.txt edit (replace the _asi/pending.txt and _nye/pending_r5.txt lines by /mnt/l2/l2vast/_split/pending_mix.txt, built by code/th_nyeng/ny_mix.py <NYAM share>, e.g. 0.41) waits for the lead.

## Early-rung exits (4c): lines queued for cells that already left the ladder

Cells with stage "out" in the NY advance state: 29. Later-rung lines (other-book, prior-year, control) still queued for them: **0** (the advance step queues a later rung only after the earlier one passes). Park rule: any such line goes to /mnt/l2/l2vast/_nye/parked_out_cells.txt (not deleted). Exclusion list for W-DEDUP: cell ids with stage out = L02831614, L0f097450, L0f11d2f7, L175f93d1, L1801f948, L1a10b4db, L21f079b6, L28e7ee31, L30ae34bf, L3516aa98, L47e7770d, L66b909fe, L7af47322, L81a1349f, L98834592, La6a45b1a, La6e1543c, La872937f, La8f7d729, La96d4160, Lb4ee29cb, Lb8fe4f02, Lca409c7e, Ld40c5e85, Le788e239, Lfa5912ed, Lfc41c8c2, Lfd4c2d53, Lffb0f715 (file /mnt/l2/l2vast/_nye/ladder_adv_state.json, key stage starting with "out"); W-DEDUP does the sweep, I own the advance logic.

(pick table unavailable: FileNotFoundError(2, 'No such file or directory'))

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
