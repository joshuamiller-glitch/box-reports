# MORNING SUMMARY - Thursday 2026-11-19 (written by W-SUMMARY for the lead at ~11:55Z; page data as of 11:30-11:50Z)

Research only. No spend, nothing rented or released, nothing on the execution server or the live chart. Every number below is copied from a page or from MORNING.md; where something is not reported it says "not reported". Dates are ESTIMATES and each states the rate it assumes. The older edition (2026-11-18 13:15Z) is kept in MORNING_SUMMARY.md.

## 0. The one-paragraph version
Nothing is CONFIRMED or ready for D8 yet. The search found a handful of NEW BOOKS that beat a live book in the exact engine on the last 6 and last 3 months (14 Asia cells, both-side; 4 NY AM cells), but every one is labelled **BETTER, calibration pending** - they have not cleared the prior-year gate, the 30 date-shift controls, the layers or the exit run. The calibrated false-discovery rate (the judge) is at or below 10% only for a few families and blocks (Asia bands/pullback/Fibonacci-on-time bars; NY AM profile/stack/walls levels), and long-only cells never reach it. Most of the night went to discovering and fixing our own bugs (a double-counted fleet rate, a ladder side-mode bug, a 2025 engine artefact, a scheduler setting that ignored priorities). All four machines are 100% busy.

## 1. What was found overnight (status labels; calibrated FDR is the judge)
| item | label | what we know |
|---|---|---|
| Asia: 14 cells beat a live Asia book (all vs A7, both-side, engine, last 6 and 3 months, Asia rule: drawdown first AND dollars) | **BETTER, calibration pending** (LEAD at best; none delivered) | Asia cells with engine rows 662, finished REPLACE verdicts 476; beat A7: 14 both-side (of 363 tested), 0 long-only (of 113 tested), 0 short-only (0 tested); vs K7/P7/H7/U7: 0 beats. Examples (both-side, vs A7): Lda55d973 vol_750, La5b5d03a time_m_2, Lcb276f27 tm120, L1edb9fab tm300, L0a809c2e kagi_40, L17ce266f / L5d9e7166 tm240, L05222ff9 / L63ff9ae8 time_m_4, L7c368a4f time_m_5, L5c9e11b3 vol_750. Long-only twins (M ids) do NOT beat A7. |
| NY AM: 4 cells beat K7 (both-side) | **BETTER, calibration pending** | L01811caa, L0f097450 (= L3701b464, same stream), L6a25b155; REPLACE-K7 L0f097450 both-side L6M d ulcer -58, d $/wk +2,291, L3M -504 / +2,902; its long-only twin does NOT beat K7. Cells with engine rows 187, finished REPLACE verdicts 122. |
| Near-target (K7 target 2 ticks nearer, M7 latch) | engine rows complete; label per page DS3_NEAR_TARGET.md | NOT stalled: the hourly counter was wrong (see section 2). True state: 290 TL3_NT_ sets, 3,238 months, all done; identity 4/4 trade for trade; all 240 control months done; page current 11:07Z. Only month 202611 of 5 sets pending. K7 lock LK_K7_a80_L50 earlier read WEAK-BUT-POSITIVE (all prior years RED); only the target-shave variant was safe. |
| Calibration by family (W-SHORT) | measurement, see section 4 | Long-side cells never reach FDR <= 10% at stage A in either session; both-side Asia cells reach 5-10%. |
| Exit engine (68 recipes, 7 families) | BUILT PARTLY; no recipe number published | Chandelier trail, N adverse bars ("bricks"), latch hooks pass the same-entry identity test (>= 96.3% exit class+time); price fills differ from the screen (engine fills stops 0.7-1.4 points better): engine P&L is not comparable to screen P&L. Screen only RANKS recipes; the engine decides. |
| Layers (one at a time, then joint) | built, running; no result yet | automatic generator reproduces all 81 XA3 sets identically; 18 candidates, 432 fit set-months each; 69 landed of 7,812 queued at 11:25Z. |
| Live books as reference | see section 4 | No live book passes the bare rule (R0) in any session: their money comes from exits and layers. |
| XA3 / WP10 (earlier NY leads) | WEAK-BUT-POSITIVE | XA3 p = 0.09-0.13 on L6M vs same-bracket random entries; 30/30 date-shift controls; unchanged. |

## 2. What failed or went wrong, and why (plain words)
1. **The fleet-rate figure was wrong for most of the night.** HEALTH.md summed per-host counts although box 1's result tree already holds A/B/Dallas results, so the engine rate looked about 2x too high (2,724/h vs the true ~1,410/h at 06:17Z). **Every date quoted from it before 06:17Z is void** (table in QUESTIONS_FOR_JOSH.md). HEALTH now uses box 1's count x 2 and says so (3,204 set-months/h at 11:50Z).
2. **Ladder side-mode bug (our own).** The ladder's event builder ignored a cell's mode (long / short): long-only cells' ADD and REPLACE sets traded both sides while the screen number was long-only. Asia: 1,307 of 1,890 cells built both-side sets; ~5,728 Asia set-months (~70% landed at the time) were on the "wrong book". Order 1014Z: the both-side engine results are VALID results for the both-side book that was run, so they stay as "(both sides, engine-tested)"; mode-correct long-only / short-only twins (Asia M ids; NY LO/SO sets) are run too and reported side by side. First reading: the both-side books beat A7 / K7, the long-only twins do not.
3. **Asia 2025 "RED" was an engine artefact.** Every new-book Asia set carried one trade on 2025-11-28 (day after Thanksgiving) that exited at 07:00:01Z when the tape had no prints, price recorded -0.25, gross -506,325 on 1 lot; 157 of 184 Asia 202511 set-months contain it. It created identical RED numbers across 13 cells. Fix (events builder only, production engine untouched): exit falls back to the last print; 157 "F" re-run sets queued first; list of 65 exposed session-ends 2023-04..2026-10 (only Asia on 2025-11-28 could hold a trade across it; NY AM: 6 holiday days; NY PM exposed on early-close days, not yet run). Until the F sets land, Asia 2025 colours are shown "as run" and "ex-artefact (diagnostic)". NY AM was checked (5,066 trade files): clean.
4. **The scheduler ignored our priorities.** The kernel's autogroup setting put every `setsid` worker in its own group at nice 0, so per-process nice values did nothing; the engine starved the grid (Frankfurt load 188/128). Fixed 03:40Z with a per-minute governor (`ag_nice_ctl.sh`; it must stay in the crontab) and one session per budgeted worker. Engine workers on Frankfurt/Singapore now get ~97-99% of a core.
5. **26 grid rows were never run** (3,682 pairs on rows that exist only on Frankfurt/Singapore but hash into partitions Dallas owns): an old partition hole. Running since 10:02Z (Frankfurt 62 results/min, Singapore 29/min); 18 of 26 done, 8 heavy ones (event bars B200/B500, TPO/footprint) ~12:30Z. "Real pass 1 FINISHED" lines at 09:44Z were wrong and were corrected. The 5 `vfpL` footprint rows (615 jobs, >45 min each) run as a background tail (default; QUESTIONS 19).
6. **Agents went silent.** W-LONENG disappeared (Asia sat unowned for hours); W-NYENG was silent 3 h 40 min (guard alert G sat unanswered 35 min); nobody was building the exit-engine families or the layer generator for ~4 h. Fixed: W-ASIA, W-EXITENG, W-LAYERS, W-FASTLADDER, W-NTFIX, W-SUMMARY started; HEALTH.md has a "live agents" table; alert G is sticky and re-wakes the lead every 15 min until answered; agents' own cron lines no longer count as proof of life.
7. **Near-target "stalled" was a counting bug** (see section 1); loop replaced by a cron that counts from the run directories.
8. **Gate wording was mixed up** (W-SHORT vs W-LAYERS "red" definitions; screen rule A vs engine rule B). Order 1122Z fixed the definition: engine rule B = stack WITH the new book vs TODAY's stack in the same prior year (>30% worse RED, 15-30% AMBER); rule A (screen) only orders the queue. Where no engine prior year has landed the verdict is "pending", not "fail".
9. **Fast engine path switched on at ~10:00Z, then briefly off 10:10-10:24Z by a false alarm** (the 2% re-check cron used a Python without numpy). Fixed; results in that window ran the exact path and are valid.
10. **Overnight context:** the lead was unreachable 05:35Z-13:03Z on 11-18 (see the 11-18 edition); LEAD NOTEs are now written ~every 30 min.

## 3. Ladder counts per session (data as of 11:30-11:50Z; "not reported" = no page number)
| session | ladder cells | stages (A / B / C / out) | cells with engine rows | finished REPLACE verdicts | beat a live book (both-side / long-only / short-only) | rule B (engine prior years) | D8 candidates listed |
|---|---|---|---|---|---|---|---|
| 1 Asia | 3,197 (grew when mode-correct M cells were added) | 2,745 / 186 / 2 / 264 | 662 | 476 (A7 476, K7 67, P7 61, H7 65, U7 65) | 14 / 0 (of 113 tested) / 0 (0 tested); looser NY rule 34 | as run: all landed rows RED in 2025 = the artefact (ex-artefact: 2 RED, 11 none, of 13); verdict final only after the F sets land | 5,020 REPLACE rows listed (614 cells with engine rows, D8_SPEC_STATUS) |
| 2 NY AM | 9,081 | built 6,493; B 113, C 3, out 6 | 187 | 122 | 4 (L01811caa, L0f097450 = L3701b464, L6a25b155) / long-only 0 on the one evaluated cell, others pending / short-only pending | L01811caa REPLACE-K7 2023 AMBER, 2024 GREEN, 2025 GREEN, persistence 0.47 / 0.65 / 0.58; L0f097450 REPLACE-K7 2023 RED (worst week 44% worse), ADD rows GREEN; L6a25b155 no RED year; L3701b464 pending | 6,838 REPLACE rows listed |
| 3 London | 808 ladder cells (ids classified); sets 886 of 3,614 queued set-months done | not reported | not reported | not reported | not reported | not reported (controls not run, no label) | not reported; behind NY AM by order |
| 4 NY PM | 396 ladder cells | not reported | 0 | 0 | 0 / 0 / 0 | not reported | 787 REPLACE rows listed; nothing run (last in order) |

Priority order in force (orders 0220Z / 0228Z): stage 1 = Asia + NY AM whole pipeline, then London, then NY PM. R3 passers: SET 1 (strict, BH on the last-6-month p) has 0 passers in every session; SET 2 (BH on whole-history p) counts are on SURVIVOR_COUNTS.md but SET 2 alone is not usable as a pass rule (it does not separate real from random NY AM cells).

## 4. The two required tables
### 4a. FDR by family (null draw 1 through the same stage A; FDR = null family-bests / real family-bests at the threshold "beats >= 24 of 30 random draws"; blank where counts are too small; SURVIVOR_COUNTS.md refreshed 11:40Z; COARSE: stage A only, 30 draws, and levels:* families rest partly on stale level files, see "UNVERIFIED" below)
**Asia** (real tested 900 of 904 family-bests, null 364 of 372)
| trigger family | FDR on last-6-month p | FDR on whole-history p |
|---|---|---|
| pullback | 11% | 15% |
| bands | 12% | 17% |
| momentum | 22% | 14% |
| session structure | 23% | 26% |
| levels:Fibonacci | 25% | 26% |
| levels:VWAP | 25% | 18% |
| trend | 41% | 35% |
| tape / order flow | 51% | 29% |
| cross-market | 68% | 74% |
| levels:zones / supply-demand | (too few) | 129% |
| order book | (too few) | 76% |
| bar family | | |
| imbalance / run (information) | 11% | 17% |
| volume | 18% | 25% |
| tick | 23% | 28% |
| time | 25% | 21% |
| renko-type | 83% | 24% |
| range | 122% | 90% |
Top (trigger x bar) blocks, FDR(24): bands x imbalance/run 0%, bands x volume 0%, levels:swing S/R x time 0%, momentum x volume 0%, pullback x time 8%, levels:Fibonacci x time 10%, bands x time 11%, cross-market x volume 17%, session structure x time 17%, momentum x tick 20%.

**NY AM** (real tested 1,814 of 1,821, null 728 of 730)
| trigger family | FDR (L6M p) | FDR (whole-history p) |
|---|---|---|
| bands | 7% | 19% |
| levels:profile / stack / walls / UW | 8% | 6% |
| levels:VWAP | 22% | 11% |
| trend | 22% | 49% |
| levels:session / prior / round / opens / gaps | 40% | 21% |
| momentum | 55% | 32% |
| levels:Fibonacci | 57% | 21% |
| order book | 62% | 39% |
| tape / order flow | 140% | 56% |
| levels:zones / supply-demand | (null produces more) | 261% |
| bar family | | |
| tick | 4% | 26% |
| dollar | 14% | 3% |
| delta | 15% | 24% |
| volume | 22% | 26% |
| time | 62% | 41% |
| kagi / P&F / line-break | 71% | 7% |
Top blocks: levels:profile/stack/walls x delta 0%, x dollar 0%, x tick 0%, x imbalance/run 5%, x volume 6%, x kagi/P&F 12%, x renko-type 15%, bands x time 17%, profile/stack/walls x time 17%, x event/swing 21%. **UNVERIFIED:** the profile/stack/walls family is a level family; the null side has only 0-6 tested cells in those blocks and part of the level files were stale (re-run: Frankfurt and Singapore done, Dallas ~12:30Z); read these 0% blocks as provisional until the calibration is redone.

**London** (real 333 of 335, null 454 of 457): no family or block reaches <= 10% on a usable count (only cross-market x time 0% on 5 cells; by bar family time 89%, others > 100% or blank on the last-6-month p): no search-level signal.
**NY PM** (real 191 of 193, null 230 of 233): trigger families momentum 40%, trend 84%, order book 88%, bands 100%; bar families renko-type 40%, volume 86%, imbalance/run 100%, time 129%: no search-level signal; 0 blocks with >= 5 real family-bests.

**Pooled vs per-mode (W-SHORT 09:5xZ; stage A, beat >= 24 of 30; the pooled table blends two different strata):**
| session | mode | FDR last-6-month p | FDR whole-history p |
|---|---|---|---|
| Asia | both-side | 2 / 45 = 5% | 31 / 294 = 10% |
| Asia | long | 86 / 236 = 36% | 195 / 543 = 36% |
| NY AM | both-side | 13 / 51 = 25% | 119 / 469 = 25% |
| NY AM | long | 74 / 172 = 43% | 368 / 1,276 = 29% |
Selected family-bests differ in mode mix between real and null (Asia long 67% real / 90% null; both 33% / 10%). Correction: report and pick thresholds PER MODE. Small counts: indicative.

**Deeper rungs (p <= 0.02 / 0.005; partial, only cells that reached stage B/C; lower bounds):** Asia whole-history p: 19/156 = 12% and 9/73 = 13%; NY AM whole-history p: 79/430 = 18% and 28/179 = 16%; p <= 0.001: none yet; last-6-month p: no real cell at p <= 0.02 (2 null NY AM cells did). Real beats null ~6-8x on whole history, above the 10% bar, not at 5%. Whole-history p is the statistic known to be biased.

**Overall calibration (stage A, partial draw 1, pooled; FDR at b = 24):** Asia last-6-month p 31%, whole-history p 27%; NY AM 39% / 28%; London 267% / 121%; NY PM 120% / 99% (above 100% = the random search produced more than the real one). **No session passes a calibrated rule at <= 10% on the pooled table.** The R3 SET 1 (strict) pass list is empty in every session.

### 4b. Live books as reference (W-LIVEREF, 01:41Z, each live book run BARE on its live bar row, plain 60/60, both sides, no layers, last 6 months; engine $/wk = JL3 exact engine over 26 weeks to 2026-11-13, base lots; x1.75 = live lot multiplier)
| book | live session | L6M trades | passes R0 bare? | p at 1,000 draws | weakest-prior-year p | engine $/wk (base lots) | x1.75 live lots |
|---|---|---|---|---|---|---|---|
| A7 | Asia | 366 | fail | 0.326 | 0.050 | 846 (n=373, 1 lot) | 1,480 |
| H7 | Asia | 138 | fail | 0.093 | 0.238 | 1,772 (n=143, 2 lots) | 3,101 |
| H7 | NY AM | 86 | fail | 0.036 | 0.869 | 325 (n=38, 1 lot) | 569 |
| K7 | Asia | 683 | fail | 0.038 | 0.529 | 3,416 (n=843, 1 lot) | 5,979 |
| K7 | London | 583 | fail | 0.782 | 0.282 | -175 (n=458, 1 lot) | -306 |
| K7 | NY AM | 509 | fail | 0.916 | 0.270 | -378 (n=187, 1 lot) | -662 |
| K7 | NY PM | 476 | fail | 0.620 | 0.574 | 586 (n=156, 1 lot) | 1,025 |
| M7 | London | 527 | fail | 0.705 | 0.947 | -380 (n=515, 1 lot) | -666 |
| M7 | NY AM | 469 | fail | 0.502 | 0.033 | 417 (n=227, 1 lot) | 731 |
| O7 | NY AM | 65 | fail | 0.241 | 0.005 | 279 (n=45, 1 lot) | 488 |
| P7 | Asia | 658 | fail | 0.050 | 0.247 | 8,919 (n=599, 2 lots) | 15,609 |
| P7 | London | 547 | fail | 0.079 | 0.722 | 998 (n=398, 1 lot) | 1,746 |
| P7 | NY AM | 523 | fail | 0.871 | 0.466 | 284 (n=43, 1 lot) | 497 |
| U7 | Asia | 153 | fail | 0.068 | 0.047 | 1,731 (n=155, 2 lots) | 3,029 |
| U7 | London | 131 | fail | 0.670 | 0.678 | 1,093 (n=105, 2 lots) | 1,912 |
Reading: no live book passes the bare rule in any session; London K7/M7 and NY AM K7/P7 are negative on plain 60/60, so live dollars in those sessions come from the live bracket, exits and layers. Live-lot dollars use x1.75 base lots; fees per outputs/FEES.md ($4.84 round trip proxy; engine net_fee $1.18). Engine $/wk is NOT comparable in size to the bare R column. Asia 2025 real results in today's stack (JL3): A7 +$49,829 (304 trades), K7 +$35,095, H7 +$33,248, P7 +$176,090, U7 +$16,540.

## 5. D8 status, exit engine, layers, dates (all ESTIMATES; the rate is stated)
**Where D8 stands.** D8_BUILD_SPEC.md does not exist yet (first complete spec due Sat 2026-11-21 12:00Z - at risk, see the dates). Nothing enters D8 without (a) beating the live book it replaces in the exact engine (REPLACE headline, ADD beside; drawdown first, then $/week; last 6 and 3 months), (b) no RED prior year under engine rule B and persistence > 0.60, (c) 30 date-shift controls, (d) the calibrated search-level check, and (e) the exit run on its own entries (order 0213Z). Asia and NY AM are decided first; London and NY PM follow and are not holding D8 up. Current gate state of the beaters: Asia - W-LAYERS rule ("negative prior year" = red) passes 4 (L5c9e11b3, Ledfbf4d2, L5d9e7166 = L17ce266f; persistence 0.622), 10 fail persistence (<= 0.60), standing rule (> 30% worse than own L6M) passes 0 (the L6M is the selection window, so almost every pick is RED by it); the engine 2025 colours are an artefact until the F sets land. NY AM - no K7 replacement is clean on both gates yet (L01811caa persistence 0.47 in 2023; L0f097450 RED 2023); ADD rows are clean on prior years.

**Rates now.** HEALTH 11:50Z: fleet engine rate 3,204 set-months/h (box-1 DONE count x 2), engine queue 157,306 lines = 49.1 h; W-NYENG's tp_admit counter 3,032/h at 11:50Z; earlier today 2,254-2,700. Fast-path share of running engine slots (11:50Z): box 1 12/23 (52%), Dallas 18/18 (100%), Frankfurt 90/97 (93%), Singapore 52/59 (88%); target >= 90% by 12:30Z; per-job speed-up 1.9x on the fast kinds (identity 217/217 identical, 0 failures; 2.3x on one Asia month in the lab).

**Dates (engine-only; quoted from D8_SPEC_STATUS.md 11:30Z at 2,696 set-months/h and the 06:25Z restatement; they scale with the rate, so the HEALTH rate above and the fast-path share should shorten them; not yet recomputed):**
| item | estimate | assumption |
|---|---|---|
| 4 NY AM REPLACE rows through everything | ~2026-11-20 14:33Z | exit-engine families exist by 11-20 12:00Z |
| NY AM first wave (52 sets = the 4 cells with variants, ~89,600 set-months) | ~2026-11-21 21:13Z at the earliest | same; 2,696/h |
| NY AM ladder stage 1 (255,269 set-months) | ~2026-11-23 10:11Z | whole fleet on NY AM; 2,696/h |
| Asia ladder | ~2026-11-20 22:00Z (whole fleet) to ~11-22 08:20Z (Asia's measured share) | W-ASIA 93,000 set-months |
| Asia + NY AM stage 1 combined (348,269 set-months) | ~2026-11-24 20:40Z | priority Asia first |
| whole ladder through everything | not given: ~3.8M set-months at a 24% yes-rate (~58 fleet-days at 2,696/h); the calibration must shrink it | |
Also pending: the layer queue lands only ~76-88 set-months/h at quota 36 (it did not scale with the quota yet), so the first candidates' layers are NOT done by ~16:00Z as estimated; W-LAYERS restates at 11:55Z. D8_BUILD_SPEC.md by Sat 11-21 12:00Z is therefore at risk for Asia and NY AM both-side books; the spec will be written as far as the evidence allows with every missing gate marked, and no book enters unlabelled.

**Exit engine (W-EXITENG).** Built under code/th_exiteng (production engine files untouched): chandelier trail, N adverse bars, latch; vol stop / R target / clock exit need no engine code. Same-entry identity over 43 months per set (gate 95% on exit class and time): bricks L01811caa 99.9% (1,229 trades), chandelier L0f097450 96.4% both-side / 96.7% mode-correct, latch Lb68a132d 97.8% / Mb68a132d 97.8%, clock L1edb9fab 96.3% / M1edb9fab 96.5%; inert pilot 19/19 trades equal. Bricks needs 50 months per family (43 done; 86 more queued). **Fill-model difference:** exit price within 3 ticks matched only 33%; the engine fills resting/trailing stops 0.7-1.4 points per trade better than the screen's "trigger print minus 1 tick" on the both-side sets, so engine P&L is not comparable to screen P&L; the screen only ranks recipes. Time exits land 3-10 s later in the engine. Exit-screen status (W-D8EXIT, 11:45Z): beats-live set 32 cells; of the earlier 14 cells 5 had an eligible exit (screen only). No recipe P&L is published; first top-3 engine results ~14:30-16:30Z today at best; staged / trails / stop-and-reverse / order-flow / opposite-signal exits: Nov 20 (D8_EXIT_ENGINE_SUPPORT.md). D8_EXIT_ENGINE_RESULTS.md does not exist yet.

**Layers (W-LAYERS).** Generator reproduces all 81 XA3 sets exactly and its scorer matches the XA3 L6M numbers on 20/20 sets. Identity passes for Asia Lda55d973xA7 and NY AM L6a25b155xK7. 18 candidates x 432 fit set-months (7,812 queued, 69 landed at 11:25Z). Layer-queue quota raised 12 -> 36 at 11:12Z.

## 6. Questions for Josh (QUESTIONS_FOR_JOSH.md; HEALTH.md shows 7 open; the file has items 1-19 plus duplicate number 16). The safe default is already applied for each.
| # | question | default applied |
|---|---|---|
| 1 | OAuth token printed once into an agent transcript ~20:45Z 11-18 | nothing printed or stored again; recommend you rotate it |
| 2 | exit recipes on every cell | answered by order 0224Z: broad exit run runs as a queue below the D8 path |
| 3 | null share / machines | no machine added or released |
| 4 | GitHub relay write permission | path enabled but idle |
| 5 | real level-3 restart test of the lead | only throwaway tests; real restart only with your agreement |
| 6 | WP10 / XA3 labels | XA3 WEAK-BUT-POSITIVE at best; layer programme keeps running |
| 7 / 9 | R3 pass rule: SET 1 (strict) vs SET 2 | SET 1 first, then SET 2 best p first; SET 2 alone not usable; calibrated rate is the judge |
| 8 | autonomous restart permission mode of the lead | real restart of b5 only with your agreement |
| 10 / 14 | engine depth: machines vs waiting | wait; stricter prior-year gate first; ordering only, nothing cut |
| 15 | broad exit run starves > 12 h | stay at ladder position; more machines is your call |
| 16 (date item, 16b, 16c) | D8 date for Asia / restated dates | superseded by the corrected table in the file; wait |
| 16 (second use of the number) | Asia beaters gate rule: standing rule vs "negative prior year = red" | standing rule governs delivery (nothing delivered); the 4 W-LAYERS passes keep front-of-queue follow-ups. NOTE: this entry still says "Y2025 RED vs the live book for all" - that is the engine artefact, not a result |
| 17 | real pass 1 end time / workers | 12 workers per host (default); remaining Frankfurt/Singapore rows moved to Dallas where possible |
| 18 | ladder side-mode bug | no decision; recorded so earlier "beats live" counts are not relied on |
| 19 | vfpL footprint rows (615 jobs) | background tail (6 workers, nice 2, Dallas); nothing dropped |

## 7. Machines (HEALTH.md 11:50Z; nothing rented or released)
| machine | busy % | threads | load | workers | queue (grid hours) | engine caps (PRIORITY / CAP files) |
|---|---|---|---|---|---|---|
| box 1 (London) | 100 | 32 | 84.4 | 29 | n/a | cap 36 (MemAvail ~71 GB, floor 40 GB) |
| server 2 (Dallas) | 100 | 64 | 133.4 | 21 | 112.5 h (118,320 grid jobs) | cap 28 (follower now lowers only on memory) |
| server A (Frankfurt) | 100 | 128 | 263.2 | 101 grid + 97 engine | 107.5 h (79,518) | cap 102 |
| server B (Singapore) | 100 | 128 | 242.0 | 101 grid + 83 engine | 42.5 h (72,105) | cap 102 |
Disk: data disk free box 1 294 GB, Dallas 26.7 TB, Frankfurt 6.3 TB, Singapore 6.2 TB; root free box 1 60.6 GB, Dallas 407 GB, Frankfurt 830 GB, Singapore 412 GB. Guard alerts E/F/G: none at 11:50Z (an E fired at 11:52Z; not yet explained here: the earlier E alerts were probe errors under load). Alert G (W-SHORT silent 85 min) was open at 11:50Z. Memory guard (per-minute, successful readings only, trips < 150 GB) runs on Frankfurt/Singapore. Engine caps were raised stepwise (Frankfurt+Singapore 38 -> 102: 644 -> 924 -> 1,108 -> 1,404 -> ~1,964 set-months/h combined at the last measured steps), Dallas 12 -> 28 (+59% at 28), box 1 32 -> 36. Real pass 1 (without the vfpL tail) ~11:30-12:30Z; stale pass-2 re-run done on Frankfurt/Singapore, Dallas ~12:30Z.

## 8. What changes for Josh - decisions or reading needed
1. **Nothing is ready for D8 and none of the "beats live" cells is delivered.** The honest label is BETTER, calibration pending (Asia 14 both-side; NY AM 4). Do not size anything on them.
2. **Pick the prior-year rule for Asia beaters** (QUESTIONS second item 16): the standing rule (default, nothing delivered) versus "negative year = red" (4 candidates pass).
3. **Machines vs waiting** (items 10 / 14 / 15 / 17): at ~3,200 set-months/h the stage-1 engine work is ~5 days; the broad exit run, null draws 3-5 and the vfpL tail will starve more than 12 h; layers are landing slowly. More machines or a narrower candidate list pulls it in.
4. **First complete D8 spec (Sat 11-21 12:00Z) is at risk**: it will carry every missing gate marked rather than be held for them, unless you instruct otherwise.
5. **Rotate the OAuth token** (item 1).
6. **Read nothing dated before 06:17Z 11-19 from HEALTH.md's fleet rate**; and treat every "beats live" count published before 10:15Z as superseded by the both-side / long-only / short-only table.
7. **Open technical items for the lead:** Asia F-set re-run (157 months) and the corrected 2025 rule-B colours; the pull-back of Frankfurt/Singapore stale results to Dallas (confirmation pending at 11:49Z); alert G for W-SHORT; the 11:52Z guard E.
