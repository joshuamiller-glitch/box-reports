# DYNEXIT_WF - dynamic stops and targets on the live books, walked forward (W-DYNQ, orders 0301Z / 0303Z X9 / 0340Z intra-trade / 0343Z fixed rule rows)

## HONEST SCOREBOARD LINE (order 0525Z item 4; quick screen, bare, no Trade Health; updated at the time of the file)
**Tried:** 324 exit recipes per book on the 17 mapped live books (287 dynamic/static menu + 37 stuck-trade variants; 3 of 20 live books have no grid cell), 3 bracket-width/shape families, 5 re-pick rhythms (2/4/13 weeks), 2 random-entry draws, and 426-450 random-sample Test 5 qualifier cells (Asia 168, NY AM 171 of 1,641 / 1,900) with 6-7 pre-written fixed rules. About 2,000 walk-forward tests (14 arms x 5 mixes x 3 steps x several pools) and 3 best-of-all families: chance alone gives a few PASS lines; none of the PASS lines on the live books is stable.
**Failed:** every dynamic/static exit family as a walk-forward replacement of the live books' own brackets (all-17 13-week income -37%); every fixed rule on the live books (L6M income -74% to -157%); levels as stops/targets (levels are not walls); intra-trade recomputation (no better than set-once); the stuck-trade exit on the live books (fixed 45 min / 0.25R: whole-period income -14%, pessimistic -24%, DD -9%; it does not beat a random exit at the same count: Table S1).
**Open:** (1) stuck exit WITH the live Trade Health and on the exact engine (needs exact rows, asked); (2) the Asia trend-capture lead (X4 chandelier on qualifiers: wins 2024, 2025, 2026 and L6M, L3M drawdown deeper, random-entry null only on 130 cells; extended twin run in progress); (3) NY AM X3 range-left on the live books against a walk-forward bracket (fair test: DD $48.6k vs $52.1k, income +1%: PASS at 13 weeks, NY AM mix, not repeated at 2 / 4 weeks); (4) zones / trendlines / trigger-line trail / vol-burst / UW forecast range / X8 untested.
**Best current lead per session** (DD, worst week, income vs the fixed bracket; no Trade Health in any number):
- **Asia:** live books: nothing beats the own bracket (13-week pick: DD $27.2k vs $21.6k, income -32%). Fair test (walk-forward bracket as comparator): no pool passes. Qualifier sample (168 cells, not hindsight): X4 chandelier fixed rule L6M DD $157k vs $342k, income $956k vs $311k, but L3M DD $145k vs $105k and about 70% of its gain appears on random entries (trend capture, 2026): RECENT-ONLY lead, registered.
- **NY AM:** live books: nothing beats the own bracket (13-week pick DD $65.4k vs $57.0k, income -34%); fair test X3D (range-left target recomputed every bar) 13 weeks PASS: DD $48.6k vs $52.1k, worst week -$26.2k vs -$31.5k, income $419k vs $416k (+1%); the same pool at 2 and 4 weeks does not pass. Qualifier sample (171 cells): basket loses money on both sides; the dynamic pick loses less (PASS at 2/4/13 weeks vs the walk-forward bracket: income -$412k vs -$666k at 2 weeks).
- **London:** live books: 2-week pick L3M DD $2.1k vs $6.0k at income -14% (not stable over 3 years: -55%). Stuck exit L6M +4% income (45/0.25R), window win only in 2026. Nothing passes.
- **NY PM:** nothing (every rule worse than the own bracket in L6M and 2026).

**QUICK SCREEN label on every number** (grid tape walk, gexit/sim_path kernel, 1 NQ base lot at $20/pt, grid fill + slippage + $4.84 RT cost in, one position per recipe at a time, the book's own session and side only, no stack rules, no account layers, NO Trade Health on either side, no pessimistic stop-fill applied: label only). Subjects: **17 of the 20 live books** (3 have no grid cell and are not guessed: Asia L385f4f2e_CX502, NY AM B7bfd33b7, NY AM Bf428c4a1.BRS8U) and a random sample of the Test 5 primary qualifier cells. Weekly P&L arrays, 186 weeks 2023-04-03..2026-10-30, the four Nov-2025 weeks excluded. Dollars = points x $20 per base lot. Code: code/th_dynq (dq_run.py kernel runner, dq_dynk.py intra-trade kernel, dq_levels.py, dq_wf.py, dq_fixed.py, dq_wf_t5.py). Raw per-book arrays: /mnt/l2/l2vast/_dynq/live3 (server C).

## ANSWER FIRST
**Headline: no dynamic exit beats the fixed bracket walking forward, drawdown first, on the live books (quick screen). The books' own fixed brackets are the best exits in this data set, and a re-picked fixed bracket (Test 3 part B) is the only reference that comes close on income. Nothing is a candidate; nothing goes to the forward register as an exit.**
1. **Primary walk-forward (pool = all 287 recipes, the existing exit pick rule, re-picked every 13 / 4 / 2 weeks, judged on the next period against the book's own fixed bracket), all 17 books summed, chained out-of-sample:** 13-week re-pick: forward max DD $60.9k vs $66.3k (8% shallower) but income $0.83M vs $1.32M (-37%): FAIL (needs income within -10%). 4-week: DD $113.7k vs $66.3k, income -52%: FAIL. 2-week (Josh's rhythm): DD $105.4k vs $66.3k (+59%), income -57%: FAIL. Faster re-picking is WORSE, not better: the pick rule (lowest ulcer first) chases the recent quiet recipe, which then earns little. By session and step see Table 1; L3M / L6M in Table 2. Recent windows are the only place a dynamic pick looks good: 2-week re-pick, all-17: L3M chained DD $14.6k vs $22.4k and worst week -$11.9k vs -$22.4k (both shallower) at income -28%, but L6M DD $27.4k vs $22.4k (deeper) and the whole 3 years say income -57%; London 2-week is the closest line (L3M DD $2.1k vs $6.0k, L6M $4.9k vs $10.1k, income -14% / -16%, but whole-period income -55%). That is a feature of the last 3-6 months, not of the 3 years, and the 13-week re-pick has the opposite sign in L3M (DD $32.3k vs $22.4k). Not a candidate.
2. **Family by family, live books only, forward (Table 3, each family alone with only its parameter re-picked):** lowers drawdown most: at 13 weeks X2 structure stops (-10% chained DD, income -10%), at 2 weeks X6 no-progress / time (-8% DD, income -6%); raises income most: the best FIXED bracket re-picked (REFPOOL, +1% income at 2 weeks, but chained DD +73%), then X5 staged (-1% income, DD +13%). No family passes (needs DD shallower or worst week better in 2/3 of periods with income within -10%, or higher income with DD not deeper): the closest are X2 (13w) and X6 (2w), both short of 2/3 of periods (7 of 12 and 26 of 44). Which families are real vs screen noise (Table 5): the picked families lose forward points vs the fixed bracket in every family (X3 and X5 at 13 weeks only marginally: -94 and -193 pts); X9 level recipes are picked most (the screen loves them: they are 80 of 287 recipes) and lose the most (-6,877 pts at 13 weeks, -13,110 at 2 weeks).
3. **Fixed rule rows (order 0343Z; defaults written down before scoring, free settings 1-3 each, Table 9 / 10): no family is a candidate.** Straight through all months vs the books' own brackets, every family loses L6M and L3M (L6M income -74% to -157%, DD 2-12x deeper) and wins at most 1 of 6 windows (X2 in 2024 only). Re-fitting adds nothing because the fixed rule is far below the fixed bracket to start with; walk-forward picks (item 1) are better than the fixed rules (income -37% vs -75..-108%) and still fail.
4. **Intra-trade re-computation (order 0340Z): updating inside the trade does not help.** Level stops/targets recomputed at every bar close (X9D) vs set once at entry (X9): chained DD as a fixed rule $271k vs $169k (fixed bracket $22k), walk-forward income -24% vs -27% (about the same); range-left target (X3D vs X3): DD +0% vs +6% and income -7% vs -12% at 13 weeks (X3D is the best-behaved family at 13 weeks, still FAIL; 16-17 order changes per trade without hysteresis). Order changes per trade: level recipes 1.2-6.8 (T1 3.1, T2 6.8, S4 1.2, T1S4 2.7; hysteresis 4 ticks 1.05, min 30 s 1.7). Identity check: updating switched off == the static row trade for trade (True, tested on prior-day-level T1S4 on every book run). Widening up to 1.0 / 1.5 x original risk (named cases not applicable here: levels have no 'protecting size'): no better than tighten-only.
5. **X9 level hit table (Table 6):** price is NOT attracted to any of the 13 level types: the fraction of entries whose nearest level ahead is touched by session end equals the same-distance shuffled-level null to the second decimal for every type (e.g. prior-day H/L/C 0.290 vs 0.297, VWAP and bands 0.690 vs 0.694, volume-profile nodes 0.439 vs 0.441, pivots 0.311 vs 0.319, round numbers 0.577 vs 0.581); after a touch the 5-point through / reject split is also at the null (0.42-0.47 through vs 0.42-0.46). Levels are not walls here; as stops they are just close. UW gamma levels (from 2024-10): touched on 2.5% of entries (too far to act as targets).
6. **Random-entry null (Tables 7 and 11, 2 random draws, same count and side mix per session instance):** the fixed rules on random entries are about level with the books' fixed brackets (L6M income difference -$124k to +$50k; X1 +$23k, X3 +$35k, X3D +$37k, X4 +$50k, X5 +$8k; X2 -$73k, X6 -$23k, X7 -$16k, X9 -$58k, X9D -$124k) and on the real, hindsight-tuned entries they lose -$355k to -$748k. So no exit 'harvests drift' (that would gain on the real entries too): the live books' brackets were tuned jointly with their entries on these very weeks, and no generic exit beats a hindsight-tuned bracket. This is the ceiling of this test: **the live books are not a fair arena for an exit that has to be found without hindsight**; the Test 5 baskets are (item 7).
7. **S2: Test 5 primary qualifier baskets (non-hindsight entries), RANDOM SAMPLE of cells: 127 Asia (7.7% of 1,641) and 82 NY AM (4.3% of 1,900); London / NY PM too thin to report** (the box was saturated: 1,048 nice-0 processes on C, my niced procs got 1-4 cores). Tables 8 and 8b. (a) Walk-forward, pool = all recipes: Asia 13-week PASS (DD $245k vs $253k, 9/12 periods, income -4%), Asia 2-week and 4-week FAIL (income -2% / -28%); NY AM 2-week and 4-week PASS (45/65 and 32/38 periods; both baskets LOSE about $350k, the pick loses $10k less; chained DD $417k vs $421k, $449k vs $421k) and 13-week FAIL (income -24%): pass / fail flips with the step and the session; 6 of 6 sample tests for the primary pool gives 3 PASS, at the loose second leg; treat as noise. (b) FIXED rules (pre-written, no search), Asia sample: recent windows win clearly (L6M income / DD: X4 chandelier $691k / $111k vs own $131k / $253k; X1 $506k / $112k; X6 $486k / $105k; X5 $383k / $88k; X3 $318k / $110k; L3M won by X1, X4, X5, X6) but years do not (2023: X2, X3, X5, X7 win by under $11k; 2024: X4 and X7; 2025: no rule wins): a 2026-only, high-volatility-regime effect (own point brackets earned $72k in 2026 on the sample vs $320-703k for the vol-scaled rules) and the live books show the opposite sign. NY AM sample: X3 (range-left target) wins 5 of 6 windows but the basket is negative in 3 of 4 years (loses less: L6M +$24k vs -$161k; 2026 -$66k vs -$284k). Random-exit null (Table 12, all 127 Asia cells, same hold weeks, random entries with the same count and side mix): the vol-scaled rules gain on RANDOM entries nearly as much as on the real ones (L6M rule-minus-own income: X1 +$261k random vs +$348k real, X4 +$367k vs +$534k, X6 +$234k vs +$328k, X5 +$308k vs +$242k, X3 +$431k vs +$152k, X7 +$422k vs +$168k): most of the Asia recent gain is the exits harvesting the 2026 regime/drift against point brackets that are too tight, not entry skill; the excess of real over random is about +$90k to +$170k (X1, X2, X4, X6) on a clustered 7.7% sample. **Not met: 'wins in most years AND both recent windows AND beats the random-exit null' for any rule** (years fail for every rule; the null is beaten only partly in L6M, L3M only by X1 and X6). RECENT-ONLY lead, filed as such: Asia qualifiers, fixed vol-scaled exits X1 (ATR bracket 1.5 / 3), X4 (chandelier 3), X6 (no-progress), for the forward register; 2 free settings or fewer for X1 / X4. Sample baskets are clustered (many cells from the same trigger families), so the effective n is small.
8. **Luck accounting:** 287 recipes per book (17 old-grid fixed refs + 62 old exit recipes + 20 X1 + 6 X3 + 7 X4 + 4 X5 + 9 X6 + 80 X9 static + 82 dynamic X3D/X9D, counting the live-menu rows; 6 'trail on the trigger's own line' recipes could not be built), 4,879 recipe-runs on the live books; walk-forward tests: 14 arms x 5 session mixes x 3 steps = 210 mix tests and 663 book tests; PASS under the loose second leg (higher income with DD not deeper) appears in 9 of 210 mix tests and 104 of 663 book tests: roughly what chance gives, all 9 are single-session mixes where the pick equals the fixed bracket in most periods or a tiny sample (NY PM), and none holds in both L3M and L6M for DD. Bonferroni on the sign p (smallest 0.00 for Asia 13-week 'DD or worst week better' 12/13, but income -32%: fails the income leg) cannot rescue any line. Scoreboard lines (method DYNEXIT, primary + 5 refs, steps 2/4/13) appended to /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl.
9. **What is not tested / known gaps:** X4 'trail on the trigger's own line' (the triggers do not export a line); X6 volatility-burst-against exit (not in the kernel); X2 supply/demand zones and trendlines/channels, X9 'zones' (no zone definition on the box); UW forecast range (X1c) not tested: the HAR forecast is the only forecast (constant within a session by construction, so no intra-trade update exists for it); UW wall quantities are static per day (rebuilt from end-of-day by-strike files, 60-120 s lag not even needed): no real intraday wall history before the recorder began; run on what exists and forward-register it; X8 (order book) = W-DYNX8; Trade Health interaction = W-DYNH (EXACT section below). Stop fills are the grid's (stop = first print through - 1 tick + measured slippage), the pessimistic stop-fill basis (fee $4.84/lot is already in; Stop exits worse by the DS3_DN_STOPFILL slippage) is NOT applied: label only.
10. **Honest caveats:** (a) the live books were chosen on the same weeks (the fixed bracket is in-sample, the exit pick is not; this biases AGAINST every exit); (b) the live books are on a 'mode-correct' stream: only the book's own side signals, so the other side cannot block it (the grid's stored 'long' column is the both-side stream: Asia L9c2622b0 3,088.6 pts / 1,629 trades here, identical to the grid core run on long-only signals, vs 4,444 / 1,328 in the stored column); (c) weekly resolution: drawdown and worst week are measured on weekly P&L, not on the day or the trade; 2-week periods have few weeks, so the per-period counts are noisy: read the chained curve; (d) 205 of the 287 recipes were present in the first run of the 17 books (identical code); (e) one pick rule only (the one named in the order); (f) 3 of 20 live books and every London / NY PM book are small samples.

## EXACT (reserved for W-DYNH)
Interaction with Trade Health (exit alone vs exit + the book's live Trade Health; where they fight) is W-DYNH's exact part. Note only: every number here is bare (no Trade Health, no stack, no layers). The exact-engine hooks that could run the families exist (EXIT_FAMILIES_*.md, D8_EXIT_ENGINE_SUPPORT.md); per-entry level stops/targets and the intra-trade dynamic hook are NOT built in the exact engine (see DYNEXIT_SPEC.md).


## TABLES (drawdown first everywhere; dyn = dynamic/picked exit, fixed = the book own fixed bracket)

### Table 1 - session mixes, primary (ALL pool = every dynamic recipe, ulcer rule), step 2 / 4 / 13 weeks (2 first)
| session, step | periods DD or worst week better | chained fwd max DD $ dyn / fixed | worst week $ dyn / fixed | fwd income $ dyn / fixed | income per $ DD dyn / fixed | picked != own | verdict |
|---|---|---|---|---|---|---|---|
| Asia, 2w | 30/60 (p 0.55) | 38,088 / 21,572 | -16,503 / -13,462 | 84,060 / 165,389 (-49%) | 2.21 / 7.67 | 80/80 | FAIL |
| NY AM, 2w | 29/59 (p 0.60) | 52,828 / 56,959 | -27,985 / -29,241 | 338,246 / 595,045 (-43%) | 6.40 / 10.45 | 80/80 | FAIL |
| London, 2w | 29/57 (p 0.50) | 33,739 / 39,466 | -18,995 / -21,137 | 130,285 / 286,820 (-55%) | 3.86 / 7.27 | 80/80 | FAIL |
| NY PM, 2w | 29/68 (p 0.91) | 85,495 / 33,512 | -30,545 / -12,601 | 18,584 / 274,830 (-93%) | 0.22 / 8.20 | 80/80 | FAIL |
| All 17 books, 2w | 21/59 (p 0.99) | 105,419 / 66,273 | -53,402 / -45,294 | 571,176 / 1,322,084 (-57%) | 5.42 / 19.95 | 80/80 | FAIL |
| Asia, 4w | 21/36 (p 0.20) | 33,426 / 21,572 | -12,407 / -13,462 | 66,751 / 165,389 (-60%) | 2.00 / 7.67 | 40/40 | FAIL |
| NY AM, 4w | 21/38 (p 0.31) | 70,173 / 56,959 | -29,090 / -29,241 | 348,329 / 595,045 (-41%) | 4.96 / 10.45 | 40/40 | FAIL |
| London, 4w | 18/35 (p 0.50) | 51,043 / 39,466 | -32,966 / -21,137 | 155,834 / 286,820 (-46%) | 3.05 / 7.27 | 40/40 | FAIL |
| NY PM, 4w | 18/38 (p 0.69) | 64,280 / 33,512 | -30,545 / -12,601 | 69,232 / 274,830 (-75%) | 1.08 / 8.20 | 40/40 | FAIL |
| All 17 books, 4w | 13/39 (p 0.99) | 113,745 / 66,273 | -58,021 / -45,294 | 640,145 / 1,322,084 (-52%) | 5.63 / 19.95 | 40/40 | FAIL |
| Asia, 13w | 12/13 (p 0.00) | 27,196 / 21,572 | -14,883 / -13,462 | 112,560 / 165,389 (-32%) | 4.14 / 7.67 | 13/13 | FAIL |
| NY AM, 13w | 8/13 (p 0.29) | 65,431 / 56,959 | -31,352 / -29,241 | 392,804 / 595,045 (-34%) | 6.00 / 10.45 | 13/13 | FAIL |
| London, 13w | 9/13 (p 0.13) | 51,014 / 39,466 | -18,995 / -21,137 | 146,065 / 286,820 (-49%) | 2.86 / 7.27 | 13/13 | FAIL |
| NY PM, 13w | 8/13 (p 0.29) | 28,321 / 33,512 | -19,247 / -12,601 | 182,931 / 274,830 (-33%) | 6.46 / 8.20 | 13/13 | FAIL |
| All 17 books, 13w | 9/13 (p 0.13) | 60,871 / 66,273 | -43,762 / -45,294 | 834,360 / 1,322,084 (-37%) | 13.71 / 19.95 | 13/13 | FAIL |

### Table 2 - L3M and L6M (forward periods starting wk 169+ / 156+), primary, drawdown first: chained DD $ dyn / fixed, income $ dyn / fixed
| session, step | L3M DD | L3M worst week | L3M income | L6M DD | L6M worst week | L6M income |
|---|---|---|---|---|---|---|
| Asia, 2w | 5,465 / 5,608 | -4,890 / -5,608 | 9,958 / 28,552 | 9,366 / 5,608 | -4,890 / -5,608 | 47,763 / 63,924 |
| NY AM, 2w | 35,435 / 29,241 | -21,325 / -29,241 | 71,952 / 103,905 | 46,557 / 29,241 | -21,325 / -29,241 | 160,620 / 265,036 |
| London, 2w | 2,109 / 6,048 | -2,109 / -6,048 | 73,027 / 85,415 | 4,860 / 10,062 | -4,860 / -10,062 | 107,241 / 127,368 |
| NY PM, 2w | 8,671 / 5,035 | -5,757 / -5,035 | 39,588 / 51,647 | 42,398 / 5,426 | -30,545 / -5,426 | 24,613 / 107,239 |
| All 17 books, 2w | 14,559 / 22,398 | -11,873 / -22,398 | 194,525 / 269,519 | 27,425 / 22,398 | -20,706 / -22,398 | 340,238 / 563,567 |
| Asia, 13w | 14,947 / 5,608 | -6,483 / -5,608 | 5,810 / 25,693 | 19,121 / 5,608 | -6,483 / -5,608 | 49,934 / 63,924 |
| NY AM, 13w | 40,726 / 29,241 | -20,454 / -29,241 | 39,195 / 113,922 | 65,431 / 29,241 | -20,454 / -29,241 | 94,712 / 265,036 |
| London, 13w | 8,037 / 6,048 | -8,037 / -6,048 | 77,397 / 89,087 | 10,062 / 10,062 | -10,062 / -10,062 | 115,678 / 127,368 |
| NY PM, 13w | 9,443 / 5,035 | -7,849 / -5,035 | 33,251 / 47,238 | 20,880 / 5,426 | -19,247 / -5,426 | 79,602 / 107,239 |
| All 17 books, 13w | 32,345 / 22,398 | -15,599 / -22,398 | 155,653 / 275,940 | 32,524 / 22,398 | -23,165 / -22,398 | 339,927 / 563,567 |

### Table 3 - family by family, live books only, forward (all 17 books summed; each arm = that family only, parameter re-picked by the same rule; REFPOOL = best FIXED bracket re-picked)

Step 2 weeks (sorted by chained DD change, deepest cut first)
| arm | chained fwd DD $ (fixed 66,273) | DD change | fwd income $ (fixed 1,322,084) | income change | periods DD or worst-week better | verdict |
|---|---|---|---|---|---|---|
| X6 | 61,190 | -8% | 1,243,948 | -6% | 26/44 | FAIL |
| X3 | 65,767 | -1% | 1,164,843 | -12% | 24/48 | FAIL |
| X3D | 66,698 | +1% | 1,146,608 | -13% | 24/47 | FAIL |
| X4 | 72,852 | +10% | 1,096,641 | -17% | 19/48 | FAIL |
| X1 | 73,087 | +10% | 1,278,632 | -3% | 27/43 | FAIL |
| X2 | 74,660 | +13% | 1,173,733 | -11% | 20/48 | FAIL |
| X5 | 74,941 | +13% | 1,311,429 | -1% | 22/43 | FAIL |
| X7 | 84,771 | +28% | 1,265,951 | -4% | 17/43 | FAIL |
| X9D | 86,635 | +31% | 1,002,768 | -24% | 17/51 | FAIL |
| ALL+REF | 90,306 | +36% | 556,351 | -58% | 22/59 | FAIL |
| STATIC | 92,617 | +40% | 690,947 | -48% | 24/55 | FAIL |
| X9 | 93,846 | +42% | 965,639 | -27% | 23/48 | FAIL |
| ALL | 105,419 | +59% | 571,176 | -57% | 21/59 | FAIL |
| REFPOOL | 114,967 | +73% | 1,334,172 | +1% | 26/46 | FAIL |

Step 13 weeks (sorted by chained DD change, deepest cut first)
| arm | chained fwd DD $ (fixed 66,273) | DD change | fwd income $ (fixed 1,322,084) | income change | periods DD or worst-week better | verdict |
|---|---|---|---|---|---|---|
| STATIC | 58,883 | -11% | 829,352 | -37% | 7/13 | FAIL |
| X2 | 59,785 | -10% | 1,185,545 | -10% | 7/12 | FAIL |
| ALL | 60,871 | -8% | 834,360 | -37% | 9/13 | FAIL |
| X3D | 66,378 | +0% | 1,224,333 | -7% | 6/12 | FAIL |
| X5 | 67,907 | +2% | 1,199,433 | -9% | 4/12 | FAIL |
| X3 | 69,921 | +6% | 1,162,941 | -12% | 9/12 | FAIL |
| X7 | 71,837 | +8% | 1,263,097 | -4% | 3/12 | FAIL |
| X4 | 75,438 | +14% | 1,137,325 | -14% | 4/12 | FAIL |
| ALL+REF | 76,902 | +16% | 729,589 | -45% | 8/13 | FAIL |
| X9 | 77,066 | +16% | 926,617 | -30% | 8/13 | FAIL |
| X1 | 80,525 | +22% | 1,168,238 | -12% | 5/12 | FAIL |
| X6 | 80,623 | +22% | 1,113,133 | -16% | 5/12 | FAIL |
| X9D | 91,399 | +38% | 847,022 | -36% | 1/12 | FAIL |
| REFPOOL | 116,419 | +76% | 1,161,789 | -12% | 7/13 | FAIL |

### Table 4 - per book, primary pool ALL, step 13 and step 2: forward chained DD $ and income $ dyn / fixed, verdict; books passing per family arm
| book | session | 13w DD | 13w income | 13w verdict | 2w DD | 2w income | 2w verdict |
|---|---|---|---|---|---|---|---|
| L12842dde.BRP45 | London | 29,889 / 41,404 | 35,813 / 67,198 | FAIL | 23,569 / 41,404 | 49,664 / 67,198 | FAIL |
| L19201dfc.BRF90_30 | London | 25,938 / 9,260 | 35,997 / 82,777 | FAIL | 11,297 / 9,260 | 35,106 / 82,777 | FAIL |
| L2c6916a5_R0_P60 | NYPM | 25,432 / 20,387 | 15,878 / 70,904 | FAIL | 28,942 / 20,387 | -18,221 / 70,904 | FAIL |
| L39287638.BRF80_40 | NYAM | 16,720 / 11,011 | 84,316 / 87,812 | FAIL | 26,962 / 11,011 | 59,550 / 87,812 | FAIL |
| L43f0cbfb.BRS8U | NYAM | 45,601 / 51,024 | 59,563 / 48,404 | PASS | 35,693 / 51,024 | 27,894 / 48,404 | FAIL |
| L4407508c.BRF120_60 | NYAM | 11,843 / 11,864 | 62,771 / 100,319 | FAIL | 15,260 / 11,864 | 50,051 / 100,319 | FAIL |
| L4aaacdb2_R0_P30 | Asia | 11,862 / 6,161 | 28,170 / 45,928 | FAIL | 20,127 / 6,161 | 15,578 / 45,928 | FAIL |
| L4bdd521a_R0_F80_40 | NYPM | 15,736 / 16,364 | 19,700 / 79,166 | FAIL | 21,540 / 16,364 | 10,333 / 79,166 | FAIL |
| L52359bf4_R0_P30 | NYPM | 15,755 / 22,243 | 71,320 / 57,791 | PASS | 37,598 / 22,243 | 14,753 / 57,791 | FAIL |
| L64390867.BRF80_40 | NYAM | 12,746 / 22,114 | 13,189 / 39,357 | FAIL | 13,165 / 22,114 | 9,993 / 39,357 | FAIL |
| L74274eca.BRF120_60 | London | 24,038 / 14,478 | 74,255 / 136,845 | FAIL | 31,645 / 14,478 | 45,516 / 136,845 | FAIL |
| L8cfda948.BRF90_30 | NYAM | 19,462 / 40,854 | 72,271 / 106,290 | FAIL | 16,613 / 40,854 | 103,658 / 106,290 | FAIL |
| L8e0bf58c_R0_S8U | NYPM | 33,333 / 21,402 | 76,032 / 66,968 | PASS | 53,968 / 21,402 | 11,720 / 66,968 | FAIL |
| L9c2622b0_R0_P45 | Asia | 19,067 / 18,092 | 43,182 / 59,145 | FAIL | 18,444 / 18,092 | 22,389 / 59,145 | FAIL |
| Lb0e6dfa3_R0_F40_80 | Asia | 30,921 / 17,678 | 41,208 / 60,317 | FAIL | 16,034 / 17,678 | 46,094 / 60,317 | FAIL |
| Le4fede95.BRF90_30 | NYAM | 40,692 / 46,614 | 1,585 / 105,328 | FAIL | 35,151 / 46,614 | 13,327 / 105,328 | FAIL |
| Lf0346d55.BRP60 | NYAM | 29,187 / 38,442 | 99,110 / 107,536 | FAIL | 47,781 / 38,442 | 73,773 / 107,536 | FAIL |

Books passing by arm (of 17):
| arm | step 13 | step 4 | step 2 |
|---|---|---|---|
| ALL | 3 | 1 | 0 |
| STATIC | 1 | 1 | 0 |
| REFPOOL | 5 | 5 | 5 |
| X1 | 2 | 6 | 3 |
| X2 | 2 | 2 | 2 |
| X3 | 2 | 4 | 8 |
| X4 | 2 | 1 | 3 |
| X5 | 1 | 3 | 5 |
| X6 | 2 | 3 | 2 |
| X7 | 3 | 3 | 5 |
| X9 | 2 | 2 | 1 |
| X3D | 5 | 1 | 3 |
| X9D | 0 | 3 | 2 |

### Table 5 - which families are real: picks of the ALL pool (live books), forward result of the periods where that family was picked (pts per base lot, dyn minus fixed, summed; DD better = periods where the pick had the shallower DD)
| family | picks 13w | books 13w | fwd pts vs fixed 13w | DD better 13w | picks 2w | books 2w | fwd pts vs fixed 2w | DD better 2w |
|---|---|---|---|---|---|---|---|---|
| X1 | 8 | 4 | -1,054 | 6 | 51 | 8 | -1,293 | 19 |
| X2 | 11 | 6 | -4,679 | 8 | 55 | 7 | -2,691 | 24 |
| X3 | 22 | 10 | -94 | 16 | 128 | 13 | -4,863 | 61 |
| X4 | 17 | 9 | -3,655 | 10 | 76 | 10 | -3,196 | 28 |
| X5 | 6 | 3 | -193 | 3 | 32 | 6 | -136 | 13 |
| X6 | 11 | 6 | -2,053 | 6 | 49 | 12 | -323 | 25 |
| X7 | 0 | 0 | +0 | 0 | 5 | 2 | -211 | 0 |
| X9 | 75 | 17 | -6,877 | 47 | 472 | 17 | -13,110 | 181 |
| X3D | 4 | 3 | -2,487 | 2 | 29 | 9 | -2,744 | 10 |
| X9D | 38 | 13 | -3,293 | 18 | 231 | 17 | -8,978 | 81 |

### Table 6 - X9 level hit table (live books, all entries, signals with a level ahead >= 4 pts; real = nearest level ahead of that type; null = same distances shuffled among entries of the same session code and month, 3 shuffles)
| level type | entries | touched by session end: real | null | after touch: through 5 pts first: real | null | rejected 5 pts first: real | null |
|---|---|---|---|---|---|---|---|
| pd | 86,261 | 0.290 | 0.297 | 0.422 | 0.423 | 0.574 | 0.572 |
| on | 85,229 | 0.322 | 0.331 | 0.458 | 0.422 | 0.535 | 0.572 |
| sess | 87,207 | 0.425 | 0.431 | 0.491 | 0.429 | 0.503 | 0.565 |
| ope | 73,136 | 0.408 | 0.409 | 0.418 | 0.428 | 0.576 | 0.567 |
| ib | 45,916 | 0.422 | 0.421 | 0.463 | 0.441 | 0.526 | 0.552 |
| vwap | 84,189 | 0.690 | 0.694 | 0.460 | 0.455 | 0.534 | 0.539 |
| avwap | 57,427 | 0.409 | 0.415 | 0.448 | 0.439 | 0.547 | 0.556 |
| piv | 104,812 | 0.311 | 0.319 | 0.442 | 0.430 | 0.549 | 0.564 |
| fib | 104,905 | 0.676 | 0.673 | 0.454 | 0.453 | 0.541 | 0.541 |
| vp | 69,490 | 0.439 | 0.441 | 0.427 | 0.425 | 0.569 | 0.570 |
| swing | 86,118 | 0.702 | 0.703 | 0.464 | 0.444 | 0.530 | 0.551 |
| uw | 16,582 | 0.025 | 0.026 | 0.299 | 0.416 | 0.701 | 0.584 |
| rnd | 105,814 | 0.577 | 0.581 | 0.460 | 0.424 | 0.537 | 0.572 |
| any | 105,773 | 0.812 | 0.812 | 0.466 | 0.456 | 0.528 | 0.538 |
| conf | 100,939 | 0.757 | 0.757 | 0.469 | 0.457 | 0.525 | 0.537 |

### Table 7 - random-entry null (same exits and pick rule on random entries, same count and side mix per session instance; mean of the draws): all-17 sum. Forward income and chained DD, dynamic pick MINUS the book own fixed bracket on the same entries, in $ (percent is meaningless: fixed brackets earn about zero on random entries)
| arm | step | real: income diff $ | random: income diff $ | real: chained DD diff $ | random: chained DD diff $ | random fixed-bracket income $ |
|---|---|---|---|---|---|---|
| ALL | 13 | -487,724 | -194,067 | -5,403 | +7,870 | -15,261 |
| STATIC | 13 | -492,732 | -193,434 | -7,390 | +15,220 | -15,261 |
| REFPOOL | 13 | -160,295 | -109,330 | +50,146 | +11,397 | -15,261 |
| X1 | 13 | -153,846 | -132,682 | +14,252 | +28,947 | -15,261 |
| X2 | 13 | -136,539 | -19,248 | -6,489 | +5,956 | -15,261 |
| X3 | 13 | -159,143 | -76,347 | +3,648 | -6,421 | -15,261 |
| X4 | 13 | -184,759 | -152,743 | +9,164 | +2,024 | -15,261 |
| X5 | 13 | -122,651 | -87,038 | +1,634 | +14,422 | -15,261 |
| X6 | 13 | -208,951 | -96,285 | +14,350 | -13,666 | -15,261 |
| X7 | 13 | -58,987 | +32,771 | +5,563 | -22,904 | -15,261 |
| X9 | 13 | -395,467 | -170,795 | +10,793 | +47,052 | -15,261 |
| X3D | 13 | -97,751 | -133,615 | +105 | +30,987 | -15,261 |
| X9D | 13 | -475,062 | -103,815 | +25,126 | -6,623 | -15,261 |
| ALL | 2 | -750,908 | -226,731 | +39,146 | +7,012 | -15,261 |
| STATIC | 2 | -631,137 | -139,173 | +26,344 | -19,364 | -15,261 |
| REFPOOL | 2 | +12,088 | -83,735 | +48,693 | -26,849 | -15,261 |
| X1 | 2 | -43,452 | -129,373 | +6,814 | +15,243 | -15,261 |
| X2 | 2 | -148,351 | +5,972 | +8,387 | +9,145 | -15,261 |
| X3 | 2 | -157,241 | -112,663 | -507 | +9,202 | -15,261 |
| X4 | 2 | -225,443 | -97,932 | +6,578 | -7,568 | -15,261 |
| X5 | 2 | -10,655 | -69,220 | +8,668 | +4,909 | -15,261 |
| X6 | 2 | -78,136 | -60,578 | -5,084 | -13,298 | -15,261 |
| X7 | 2 | -56,134 | +4,006 | +18,498 | -18,979 | -15,261 |
| X9 | 2 | -356,445 | -113,921 | +27,572 | +3,484 | -15,261 |
| X3D | 2 | -175,476 | -74,558 | +424 | -10,267 | -15,261 |
| X9D | 2 | -319,316 | -142,020 | +20,362 | +18,977 | -15,261 |

### Table 8 - S2: Test 5 primary qualifier baskets, a RANDOM SAMPLE of cells (quick screen; each held cell picks its own exit on its history, counted on its hold weeks only; income and DD of the equal-weight basket of the sampled cells, 1 base lot each; negative income = the sampled qualifiers lose money on their own fixed brackets)
| session, step, arm | cells | periods DD or worst week better | chained fwd DD $ dyn / fixed | fwd income $ dyn / fixed | L3M DD dyn / fixed | L6M DD dyn / fixed | verdict |
|---|---|---|---|---|---|---|---|
| Asia, 2w, ALL | 127 | 28/52 | 231,300 / 253,309 | 164,453 / 168,094 (-2%) | 231,300 / 253,309 | 231,300 / 253,309 | FAIL |
| Asia, 2w, REFPOOL | 127 | 23/49 | 249,192 / 253,309 | 202,724 / 168,094 (+21%) | 249,192 / 253,309 | 249,192 / 253,309 | **PASS** |
| Asia, 2w, X2 | 127 | 6/48 | 247,904 / 253,309 | 152,799 / 168,094 (-9%) | 247,904 / 253,309 | 247,904 / 253,309 | FAIL |
| Asia, 2w, X3 | 127 | 12/50 | 254,313 / 253,309 | 140,348 / 168,094 (-17%) | 254,313 / 253,309 | 254,313 / 253,309 | FAIL |
| Asia, 2w, X6 | 127 | 16/48 | 262,461 / 253,309 | 189,656 / 168,094 (+13%) | 262,461 / 253,309 | 262,461 / 253,309 | FAIL |
| NY AM, 2w, ALL | 82 | 45/65 | 417,024 / 421,189 | -351,937 / -362,168 (+3%) | 76,486 / 62,151 | 228,786 / 212,870 | **PASS** |
| NY AM, 2w, REFPOOL | 82 | 34/62 | 473,328 / 421,189 | -316,899 / -362,168 (+12%) | 72,436 / 62,151 | 249,793 / 212,870 | FAIL |
| NY AM, 2w, X2 | 82 | 19/65 | 437,776 / 421,189 | -300,895 / -362,168 (+17%) | 81,242 / 62,151 | 244,637 / 212,870 | FAIL |
| NY AM, 2w, X3 | 82 | 38/63 | 428,548 / 421,189 | -389,831 / -362,168 (-8%) | 49,768 / 62,151 | 204,026 / 212,870 | FAIL |
| NY AM, 2w, X6 | 82 | 32/64 | 431,379 / 421,189 | -365,732 / -362,168 (-1%) | 64,421 / 62,151 | 215,985 / 212,870 | FAIL |
| Asia, 4w, ALL | 127 | 18/33 | 263,977 / 253,309 | 121,376 / 168,094 (-28%) | 263,977 / 253,309 | 263,977 / 253,309 | FAIL |
| Asia, 4w, REFPOOL | 127 | 14/33 | 245,446 / 253,309 | 180,129 / 168,094 (+7%) | 245,446 / 253,309 | 245,446 / 253,309 | **PASS** |
| Asia, 4w, X2 | 127 | 3/33 | 253,309 / 253,309 | 150,476 / 168,094 (-10%) | 253,309 / 253,309 | 253,309 / 253,309 | FAIL |
| Asia, 4w, X3 | 127 | 7/33 | 258,240 / 253,309 | 121,448 / 168,094 (-28%) | 258,240 / 253,309 | 258,240 / 253,309 | FAIL |
| Asia, 4w, X6 | 127 | 8/33 | 257,280 / 253,309 | 190,488 / 168,094 (+13%) | 257,280 / 253,309 | 257,280 / 253,309 | FAIL |
| NY AM, 4w, ALL | 82 | 32/38 | 449,207 / 421,189 | -341,009 / -362,168 (+6%) | 75,537 / 62,151 | 270,703 / 212,870 | **PASS** |
| NY AM, 4w, REFPOOL | 82 | 23/38 | 483,139 / 421,189 | -344,416 / -362,168 (+5%) | 64,856 / 62,151 | 248,429 / 212,870 | FAIL |
| NY AM, 4w, X2 | 82 | 14/38 | 404,888 / 421,189 | -303,787 / -362,168 (+16%) | 62,151 / 62,151 | 212,870 / 212,870 | **PASS** |
| NY AM, 4w, X3 | 82 | 21/38 | 426,995 / 421,189 | -364,111 / -362,168 (-1%) | 46,162 / 62,151 | 192,694 / 212,870 | FAIL |
| NY AM, 4w, X6 | 82 | 20/38 | 429,355 / 421,189 | -408,495 / -362,168 (-13%) | 69,873 / 62,151 | 218,484 / 212,870 | FAIL |
| Asia, 13w, ALL | 127 | 9/12 | 245,347 / 253,309 | 160,549 / 168,094 (-4%) | 245,347 / 253,309 | 245,347 / 253,309 | **PASS** |
| Asia, 13w, REFPOOL | 127 | 6/12 | 272,002 / 253,309 | 210,115 / 168,094 (+25%) | 272,002 / 253,309 | 272,002 / 253,309 | FAIL |
| Asia, 13w, X1 | 127 | 5/12 | 250,319 / 253,309 | 115,230 / 168,094 (-31%) | 250,319 / 253,309 | 250,319 / 253,309 | FAIL |
| Asia, 13w, X2 | 127 | 2/12 | 239,805 / 253,309 | 169,402 / 168,094 (+1%) | 239,805 / 253,309 | 239,805 / 253,309 | **PASS** |
| Asia, 13w, X3 | 127 | 5/12 | 253,309 / 253,309 | 92,324 / 168,094 (-45%) | 253,309 / 253,309 | 253,309 / 253,309 | FAIL |
| Asia, 13w, X4 | 127 | 3/12 | 229,902 / 253,309 | 127,491 / 168,094 (-24%) | 229,902 / 253,309 | 229,902 / 253,309 | FAIL |
| Asia, 13w, X5 | 127 | 5/12 | 232,912 / 253,309 | 200,393 / 168,094 (+19%) | 232,912 / 253,309 | 232,912 / 253,309 | **PASS** |
| Asia, 13w, X6 | 127 | 4/12 | 257,144 / 253,309 | 119,194 / 168,094 (-29%) | 257,144 / 253,309 | 257,144 / 253,309 | FAIL |
| Asia, 13w, X7 | 127 | 2/12 | 248,825 / 253,309 | 171,804 / 168,094 (+2%) | 248,825 / 253,309 | 248,825 / 253,309 | **PASS** |
| Asia, 13w, X9 | 127 | 9/12 | 256,958 / 253,309 | 177,734 / 168,094 (+6%) | 256,958 / 253,309 | 256,958 / 253,309 | **PASS** |
| NY AM, 13w, ALL | 82 | 10/13 | 489,660 / 421,189 | -450,171 / -362,168 (-24%) | 85,262 / 62,151 | 266,781 / 212,870 | FAIL |
| NY AM, 13w, REFPOOL | 82 | 9/13 | 506,249 / 421,189 | -314,501 / -362,168 (+13%) | 71,387 / 62,151 | 274,380 / 212,870 | **PASS** |
| NY AM, 13w, X1 | 82 | 9/13 | 433,011 / 421,189 | -387,452 / -362,168 (-7%) | 73,551 / 62,151 | 236,650 / 212,870 | **PASS** |
| NY AM, 13w, X2 | 82 | 4/13 | 455,620 / 421,189 | -315,255 / -362,168 (+13%) | 65,339 / 62,151 | 245,441 / 212,870 | FAIL |
| NY AM, 13w, X3 | 82 | 9/13 | 408,665 / 421,189 | -338,756 / -362,168 (+6%) | 66,794 / 62,151 | 222,755 / 212,870 | **PASS** |
| NY AM, 13w, X4 | 82 | 8/13 | 456,823 / 421,189 | -413,211 / -362,168 (-14%) | 77,880 / 62,151 | 221,309 / 212,870 | FAIL |
| NY AM, 13w, X5 | 82 | 4/13 | 466,846 / 421,189 | -418,158 / -362,168 (-15%) | 72,408 / 62,151 | 239,607 / 212,870 | FAIL |
| NY AM, 13w, X6 | 82 | 9/13 | 462,343 / 421,189 | -441,483 / -362,168 (-22%) | 80,644 / 62,151 | 244,627 / 212,870 | FAIL |
| NY AM, 13w, X7 | 82 | 7/13 | 408,858 / 421,189 | -296,803 / -362,168 (+18%) | 58,561 / 62,151 | 215,803 / 212,870 | **PASS** |
| NY AM, 13w, X9 | 82 | 10/13 | 599,059 / 421,189 | -553,264 / -362,168 (-53%) | 81,593 / 62,151 | 296,077 / 212,870 | FAIL |

### Table 8b - S2 fixed rules (pre-written defaults) on the sampled qualifier cells: windows won of 6 (2023, 2024, 2025, 2026, L6M, L3M), L6M DD $ rule / fixed and L6M income $ rule / fixed
| session | rule | cells with the rule | windows won | L6M DD | L6M income | L3M DD | L3M income |
|---|---|---|---|---|---|---|---|
| Asia | X1 | 127 | 3 | 112,252 / 253,309 | 505,872 / 130,922 | 39,959 / 106,325 | 314,015 / 177,261 |
| Asia | X2 | 127 | 3 | 157,480 / 253,309 | 498,604 / 130,922 | 157,480 / 106,325 | 200,171 / 177,261 |
| Asia | X3 | 127 | 3 | 110,310 / 253,309 | 317,579 / 130,922 | 110,310 / 106,325 | 125,021 / 177,261 |
| Asia | X4 | 127 | 4 | 111,295 / 253,309 | 690,649 / 130,922 | 99,402 / 106,325 | 375,199 / 177,261 |
| Asia | X5 | 127 | 4 | 88,151 / 253,309 | 382,731 / 130,922 | 72,809 / 106,325 | 169,811 / 177,261 |
| Asia | X6 | 127 | 3 | 104,545 / 253,309 | 486,021 / 130,922 | 30,583 / 106,325 | 299,995 / 177,261 |
| Asia | X7 | 127 | 2 | 335,550 / 253,309 | 354,925 / 130,922 | 180,625 / 106,325 | 178,561 / 177,261 |
| Asia | X9 | 127 | 0 | 217,883 / 253,309 | -207,990 / 130,922 | 154,505 / 106,325 | -154,505 / 177,261 |
| Asia | X3D | 46 | 0 | 68,423 / 100,843 | 47,002 / 138,065 | 68,423 / 36,123 | -4,759 / 132,240 |
| Asia | X9D | 46 | 0 | 76,003 / 100,843 | -64,615 / 138,065 | 53,235 / 36,123 | -51,660 / 132,240 |
| NY AM | X1 | 82 | 1 | 256,534 / 170,520 | -252,855 / -161,256 | 64,654 / 62,151 | -25,377 / -31,659 |
| NY AM | X2 | 82 | 2 | 189,604 / 170,520 | -135,457 / -161,256 | 77,200 / 62,151 | 17,165 / -31,659 |
| NY AM | X3 | 82 | 5 | 68,175 / 170,520 | 24,241 / -161,256 | 60,700 / 62,151 | -3,540 / -31,659 |
| NY AM | X4 | 82 | 2 | 180,909 / 170,520 | -160,716 / -161,256 | 52,597 / 62,151 | 144 / -31,659 |
| NY AM | X5 | 82 | 1 | 321,993 / 170,520 | -316,823 / -161,256 | 62,261 / 62,151 | -57,091 / -31,659 |
| NY AM | X6 | 82 | 1 | 225,649 / 170,520 | -214,783 / -161,256 | 65,406 / 62,151 | -19,887 / -31,659 |
| NY AM | X7 | 82 | 0 | 172,257 / 170,520 | -131,405 / -161,256 | 74,360 / 62,151 | 15,499 / -31,659 |
| NY AM | X9 | 82 | 0 | 293,268 / 170,520 | -293,268 / -161,256 | 48,947 / 62,151 | -48,947 / -31,659 |
| NY AM | X3D | 46 | 3 | 51,713 / 61,523 | -9,274 / -10,277 | 51,713 / 49,280 | 7,250 / -10,018 |
| NY AM | X9D | 46 | 0 | 125,001 / 61,523 | -122,844 / -10,277 | 34,789 / 49,280 | -34,789 / -10,018 |


### Table 9 - FIXED RULE rows (no search, written before scoring: /mnt/l2/l2vast/_dynexit/fixed_rules_dynq.json), all 17 live books summed, straight through all months vs the book own fixed bracket (bare, no Trade Health either side). dyn / fixed: max DD $, income $; wins = books winning the window (win = shallower DD with income not lower by more than 10%, or higher income with DD not deeper)
| rule (free settings) | window | DD $ rule / fixed | worst week $ rule / fixed | income $ rule / fixed | books winning | window win |
|---|---|---|---|---|---|---|
| X1 volatility-scaled bracket (2) | L3M | 26,916 / 15,710 | -22,137 / -15,710 | 85,340 / 242,350 (-65%) | 2/17 | - |
| X1 volatility-scaled bracket (2) | L6M | 58,772 / 22,398 | -43,085 / -22,398 | 121,706 / 476,592 (-74%) | 0/17 | - |
| X1 volatility-scaled bracket (2) | 2026 | 71,543 / 66,273 | -43,085 / -39,181 | 225,213 / 541,724 (-58%) | 2/17 | - |
| X1 volatility-scaled bracket (2) | 2025 | 127,860 / 52,373 | -80,541 / -45,294 | 8,926 / 376,379 (-98%) | 0/17 | - |
| X1 volatility-scaled bracket (2) | 2024 | 52,320 / 35,514 | -33,249 / -35,514 | 110,149 / 315,901 (-65%) | 6/17 | - |
| X1 volatility-scaled bracket (2) | 2023 | 29,519 / 24,205 | -22,682 / -17,383 | 25,620 / 178,528 (-86%) | 3/17 | - |
| X2 structure stop (2) | L3M | 39,965 / 15,710 | -23,123 / -15,710 | 186,878 / 242,350 (-23%) | 1/17 | - |
| X2 structure stop (2) | L6M | 176,587 / 22,398 | -56,992 / -22,398 | 76,707 / 476,592 (-84%) | 0/17 | - |
| X2 structure stop (2) | 2026 | 176,587 / 66,273 | -56,992 / -39,181 | 276,988 / 541,724 (-49%) | 3/17 | - |
| X2 structure stop (2) | 2025 | 97,267 / 52,373 | -51,846 / -45,294 | 152,212 / 376,379 (-60%) | 2/17 | - |
| X2 structure stop (2) | 2024 | 33,801 / 35,514 | -32,326 / -35,514 | 369,415 / 315,901 (+17%) | 8/17 | WIN |
| X2 structure stop (2) | 2023 | 46,169 / 24,205 | -28,848 / -17,383 | 87,535 / 178,528 (-51%) | 1/17 | - |
| X3 range-left target (static) (2) | L3M | 79,873 / 15,710 | -21,877 / -15,710 | -56,206 / 242,350 (-123%) | 0/17 | - |
| X3 range-left target (static) (2) | L6M | 96,706 / 22,398 | -21,877 / -22,398 | -36,660 / 476,592 (-108%) | 0/17 | - |
| X3 range-left target (static) (2) | 2026 | 113,154 / 66,273 | -38,384 / -39,181 | -83,469 / 541,724 (-115%) | 0/17 | - |
| X3 range-left target (static) (2) | 2025 | 93,694 / 52,373 | -45,719 / -45,294 | -22,188 / 376,379 (-106%) | 2/17 | - |
| X3 range-left target (static) (2) | 2024 | 52,556 / 35,514 | -18,473 / -35,514 | 13,619 / 315,901 (-96%) | 3/17 | - |
| X3 range-left target (static) (2) | 2023 | 43,352 / 24,205 | -17,161 / -17,383 | -31,656 / 178,528 (-118%) | 1/17 | - |
| X3D range-left target, recomputed every bar (2) | L3M | 55,203 / 15,710 | -21,626 / -15,710 | -28,659 / 242,350 (-112%) | 1/17 | - |
| X3D range-left target, recomputed every bar (2) | L6M | 73,621 / 22,398 | -21,626 / -22,398 | -14,584 / 476,592 (-103%) | 1/17 | - |
| X3D range-left target, recomputed every bar (2) | 2026 | 89,270 / 66,273 | -37,450 / -39,181 | -50,470 / 541,724 (-109%) | 0/17 | - |
| X3D range-left target, recomputed every bar (2) | 2025 | 106,661 / 52,373 | -58,858 / -45,294 | -26,492 / 376,379 (-107%) | 1/17 | - |
| X3D range-left target, recomputed every bar (2) | 2024 | 52,401 / 35,514 | -21,379 / -35,514 | 2,358 / 315,901 (-99%) | 1/17 | - |
| X3D range-left target, recomputed every bar (2) | 2023 | 49,377 / 24,205 | -17,161 / -17,383 | -28,581 / 178,528 (-116%) | 1/17 | - |
| X4 chandelier trail (2) | L3M | 27,443 / 15,710 | -12,100 / -15,710 | 103,311 / 242,350 (-57%) | 1/17 | - |
| X4 chandelier trail (2) | L6M | 103,396 / 22,398 | -46,778 / -22,398 | 70,735 / 476,592 (-85%) | 0/17 | - |
| X4 chandelier trail (2) | 2026 | 103,396 / 66,273 | -46,778 / -39,181 | 105,178 / 541,724 (-81%) | 2/17 | - |
| X4 chandelier trail (2) | 2025 | 154,196 / 52,373 | -64,592 / -45,294 | -47,735 / 376,379 (-113%) | 2/17 | - |
| X4 chandelier trail (2) | 2024 | 48,081 / 35,514 | -34,683 / -35,514 | 167,062 / 315,901 (-47%) | 6/17 | - |
| X4 chandelier trail (2) | 2023 | 35,764 / 24,205 | -31,105 / -17,383 | 55,341 / 178,528 (-69%) | 5/17 | - |
| X5 staged (3) | L3M | 43,091 / 15,710 | -15,299 / -15,710 | 23,917 / 242,350 (-90%) | 0/17 | - |
| X5 staged (3) | L6M | 62,758 / 22,398 | -30,558 / -22,398 | 61,151 / 476,592 (-87%) | 0/17 | - |
| X5 staged (3) | 2026 | 78,884 / 66,273 | -30,558 / -39,181 | 87,681 / 541,724 (-84%) | 1/17 | - |
| X5 staged (3) | 2025 | 97,627 / 52,373 | -42,496 / -45,294 | 2,080 / 376,379 (-99%) | 1/17 | - |
| X5 staged (3) | 2024 | 58,046 / 35,514 | -31,453 / -35,514 | 21,771 / 315,901 (-93%) | 5/17 | - |
| X5 staged (3) | 2023 | 27,356 / 24,205 | -17,360 / -17,383 | 17,176 / 178,528 (-90%) | 4/17 | - |
| X6 no-progress (3) | L3M | 36,089 / 15,710 | -28,408 / -15,710 | 48,521 / 242,350 (-80%) | 2/17 | - |
| X6 no-progress (3) | L6M | 50,224 / 22,398 | -36,427 / -22,398 | 112,910 / 476,592 (-76%) | 1/17 | - |
| X6 no-progress (3) | 2026 | 68,245 / 66,273 | -36,427 / -39,181 | 247,047 / 541,724 (-54%) | 2/17 | - |
| X6 no-progress (3) | 2025 | 116,492 / 52,373 | -60,582 / -45,294 | -23,540 / 376,379 (-106%) | 0/17 | - |
| X6 no-progress (3) | 2024 | 53,526 / 35,514 | -36,789 / -35,514 | 51,424 / 315,901 (-84%) | 4/17 | - |
| X6 no-progress (3) | 2023 | 30,863 / 24,205 | -24,530 / -17,383 | 16,564 / 178,528 (-91%) | 3/17 | - |
| X7 opposite-signal exit (1) | L3M | 39,666 / 15,710 | -21,514 / -15,710 | 67,000 / 242,350 (-72%) | 0/17 | - |
| X7 opposite-signal exit (1) | L6M | 61,189 / 22,398 | -41,027 / -22,398 | 97,071 / 476,592 (-80%) | 0/17 | - |
| X7 opposite-signal exit (1) | 2026 | 119,342 / 66,273 | -51,642 / -39,181 | 131,153 / 541,724 (-76%) | 3/17 | - |
| X7 opposite-signal exit (1) | 2025 | 200,623 / 52,373 | -72,048 / -45,294 | -132,529 / 376,379 (-135%) | 1/17 | - |
| X7 opposite-signal exit (1) | 2024 | 42,628 / 35,514 | -24,739 / -35,514 | 296,935 / 315,901 (-6%) | 7/17 | - |
| X7 opposite-signal exit (1) | 2023 | 46,749 / 24,205 | -30,589 / -17,383 | 52,215 / 178,528 (-71%) | 6/17 | - |
| X9 any-level T1S4 (static) (2) | L3M | 91,922 / 15,710 | -15,851 / -15,710 | -84,556 / 242,350 (-135%) | 1/17 | - |
| X9 any-level T1S4 (static) (2) | L6M | 168,533 / 22,398 | -23,079 / -22,398 | -168,533 / 476,592 (-135%) | 0/17 | - |
| X9 any-level T1S4 (static) (2) | 2026 | 284,144 / 66,273 | -23,079 / -39,181 | -284,144 / 541,724 (-152%) | 0/17 | - |
| X9 any-level T1S4 (static) (2) | 2025 | 271,604 / 52,373 | -17,599 / -45,294 | -271,604 / 376,379 (-172%) | 0/17 | - |
| X9 any-level T1S4 (static) (2) | 2024 | 260,476 / 35,514 | -15,757 / -35,514 | -260,476 / 315,901 (-182%) | 1/17 | - |
| X9 any-level T1S4 (static) (2) | 2023 | 204,735 / 24,205 | -11,863 / -17,383 | -204,597 / 178,528 (-215%) | 1/17 | - |
| X9D any-level T1S4, recomputed every bar (2) | L3M | 140,220 / 15,710 | -17,275 / -15,710 | -140,220 / 242,350 (-158%) | 0/17 | - |
| X9D any-level T1S4, recomputed every bar (2) | L6M | 271,030 / 22,398 | -25,499 / -22,398 | -271,030 / 476,592 (-157%) | 0/17 | - |
| X9D any-level T1S4, recomputed every bar (2) | 2026 | 464,624 / 66,273 | -26,151 / -39,181 | -464,624 / 541,724 (-186%) | 0/17 | - |
| X9D any-level T1S4, recomputed every bar (2) | 2025 | 400,890 / 52,373 | -21,933 / -45,294 | -400,890 / 376,379 (-207%) | 0/17 | - |
| X9D any-level T1S4, recomputed every bar (2) | 2024 | 400,415 / 35,514 | -19,919 / -35,514 | -400,415 / 315,901 (-227%) | 1/17 | - |
| X9D any-level T1S4, recomputed every bar (2) | 2023 | 281,376 / 24,205 | -14,621 / -17,383 | -281,376 / 178,528 (-258%) | 0/17 | - |

### Table 10 - fixed rule: level types one by one (X9 default T1S4 for each type; static / recomputed every bar). Window wins out of 6 (2023, 2024, 2025, 2026, L6M, L3M); L6M and L3M DD $ rule / fixed
| level type | static wins/6 | static L6M DD | static L6M income | dynamic wins/6 | dynamic L6M DD | dynamic L6M income | static L3M DD | dynamic L3M DD | random-entry null (static, L6M income change %) |
|---|---|---|---|---|---|---|---|---|---|
| pd | 0 | 37,760 / 22,398 | 202,759 / 476,592 | 0 | 52,715 / 22,398 | 136,498 / 476,592 | 7,705 / 15,710 | 13,748 / 15,710 | +140 |
| on | 0 | 51,452 / 22,398 | 209,491 / 476,592 | 0 | 69,656 / 22,398 | 143,494 / 476,592 | 38,343 / 15,710 | 69,656 / 15,710 | -47 |
| sess | 0 | 32,834 / 22,398 | 141,144 / 476,592 | 0 | 69,811 / 22,398 | 75,848 / 476,592 | 32,834 / 15,710 | 69,811 / 15,710 | -11 |
| ope | 0 | 68,697 / 22,398 | 32,408 / 476,592 | 0 | 105,052 / 22,398 | -64,174 / 476,592 | 21,797 / 15,710 | 61,001 / 15,710 | +27 |
| ib | 0 | 34,791 / 22,398 | 260,001 / 476,592 | 0 | 40,059 / 22,398 | 146,247 / 476,592 | 26,206 / 15,710 | 40,059 / 15,710 | -52 |
| vwap | 0 | 79,302 / 22,398 | -54,535 / 476,592 | 0 | 281,945 / 22,398 | -281,945 / 476,592 | 30,837 / 15,710 | 132,604 / 15,710 | -26 |
| avwap | 0 | 43,261 / 22,398 | 203,932 / 476,592 | 0 | 36,417 / 22,398 | 116,859 / 476,592 | 43,261 / 15,710 | 36,417 / 15,710 | -49 |
| piv | 0 | 79,965 / 22,398 | 136,038 / 476,592 | 0 | 85,219 / 22,398 | 103,926 / 476,592 | 30,752 / 15,710 | 45,287 / 15,710 | +30 |
| fib | 0 | 82,280 / 22,398 | -68,878 / 476,592 | 0 | 277,452 / 22,398 | -276,924 / 476,592 | 29,834 / 15,710 | 124,584 / 15,710 | -75 |
| vp | 0 | 20,237 / 22,398 | 202,107 / 476,592 | 0 | 57,183 / 22,398 | 82,645 / 476,592 | 10,709 / 15,710 | 15,799 / 15,710 | +83 |
| swing | 0 | 57,237 / 22,398 | -13,133 / 476,592 | 0 | 271,495 / 22,398 | -262,539 / 476,592 | 32,571 / 15,710 | 119,282 / 15,710 | -25 |
| rnd | 0 | 49,797 / 22,398 | 17,229 / 476,592 | 0 | 285,814 / 22,398 | -285,814 / 476,592 | 34,371 / 15,710 | 120,851 / 15,710 | -39 |
| uw | 1 | 14,217 / 22,398 | 411,928 / 476,592 | 1 | 14,217 / 22,398 | 412,401 / 476,592 | 11,656 / 15,710 | 11,656 / 15,710 | +23 |
| any | 0 | 168,533 / 22,398 | -168,533 / 476,592 | 0 | 271,030 / 22,398 | -271,030 / 476,592 | 91,922 / 15,710 | 140,220 / 15,710 | -51 |

### Table 11 - random-entry null of the fixed rules (same rule on random entries, same count and side mix, 2 draw(s)): L6M income, rule MINUS the book own fixed bracket on the same entries, $, all-17 sum (a rule that only harvests drift would be positive here too)
| rule | real entries: L6M income diff $ | random entries: L6M income diff $ (mean of draws) | random entries: L6M DD diff $ | real: L6M DD diff $ |
|---|---|---|---|---|
| X1 volatility-scaled bracket | -354,886 | +23,131 | +11,862 | +36,375 |
| X2 structure stop | -399,885 | -73,109 | +105,011 | +154,189 |
| X3 range-left target (static) | -513,252 | +35,422 | -35,634 | +74,308 |
| X3D range-left target, recomputed every bar | -491,176 | +37,142 | -42,328 | +51,223 |
| X4 chandelier trail | -405,857 | +49,875 | -6,358 | +80,998 |
| X5 staged | -415,441 | +7,609 | +5,610 | +40,361 |
| X6 no-progress | -363,683 | -23,311 | +21,914 | +27,826 |
| X7 opposite-signal exit | -379,522 | -15,582 | +73,702 | +38,791 |
| X9 any-level T1S4 (static) | -645,125 | -57,979 | +26,350 | +146,135 |
| X9D any-level T1S4, recomputed every bar | -747,622 | -124,100 | +92,358 | +248,632 |



### Table 12 - S2 random-entry null of the fixed rules (Asia sample, 127 cells that have a random-entry twin; same cells, hold weeks, count and side mix of entries; rule MINUS the cell own fixed bracket on the same entries, income $k / chained DD change $k). A rule that only harvests drift / the 2026 regime gains on random entries as much as on real ones.
| rule | 2026 real | 2026 random | L6M real | L6M random | L3M real | L3M random | L6M DD change real | L6M DD change random | verdict vs null |
|---|---|---|---|---|---|---|---|---|---|
| X1 | +389 | +251 | +348 | +261 | +111 | +39 | -145 | -193 | real above random |
| X2 | +354 | +147 | +348 | +132 | -10 | -124 | -102 | -87 | real above random |
| X3 | +187 | +462 | +152 | +431 | -90 | +42 | -150 | -351 | real gain not above random gain |
| X4 | +592 | +355 | +534 | +367 | +166 | +164 | -148 | -179 | real above random |
| X5 | +296 | +309 | +242 | +308 | -26 | +73 | -167 | -233 | real gain not above random gain |
| X6 | +366 | +221 | +328 | +234 | +97 | +20 | -152 | -190 | real above random |
| X7 | +219 | +449 | +168 | +422 | -51 | +136 | +91 | -130 | real gain not above random gain |
| X9 | -394 | +24 | -378 | +59 | -375 | -152 | -45 | -106 | real gain not above random gain |

### Table 13 - order changes per trade of the intra-trade (dynamic) recipes (all 17 live books pooled; a live strategy has to send these)
| recipe | changes per trade |
|---|---|
| D9 level, target only, next level (T1) | 3.11 |
| D9 level, target only, second level (T2) | 6.75 |
| D9 level, stop only (S4) | 1.24 |
| D9 level, both (T1S4) | 2.66 |
| D9 T1S4, hysteresis 4 ticks (1 pt) | 1.05 |
| D9 T1S4, min 30 s between changes | 1.71 |
| D9 T1S4, widening allowed up to 1.0 x original risk | 2.64 |
| D9 T1S4, widening allowed up to 1.5 x original risk | 3.39 |
| X3D range-left target, share 0.5 / 0.75 / 1.0 | 16-17 (every bar; no hysteresis tested) |
Updates occur at bar closes of the book's own bars (+1 s delivery lag in the kernel), so the 1 s and 5 s minimum-time rules never bind (bars are longer); 30 s is shown. Hysteresis is in 0.25-pt ticks.

### Recipe menu as run (287 per book) and how the X9 options map
- REF 17: the grid's 7 brackets + 10 fixed point shapes (own bracket marked OWN). OLD 62 of the 68 screen recipes (no 'trail on the trigger's own line'). X1 new 20 (ATR14 k pairs 8; trailing 20-session range 6; HAR forecast 6). X3 new 6 and X3D 6 (dynamic twins; 2 stop choices x 3 shares: 0.5/0.75/1.0). X4 new 7. X5 new 4. X6 new 9.
- X9 levels, 13 types separately (prior-day H/L/C, overnight H/L, session H/L, session/day/week opens, IB, VWAP and +-1/2 sd bands, anchored VWAPs day and week, floor and weekly pivots (10), fib retracements/extensions of prior day and of the current confirmed leg (14), prior-day volume profile POC/VA edges/3 HVN, confirmed swings (m=3 and m=8, last and previous), round numbers (50-pt grid), UW QQQ gamma flip / call wall / put wall / magnet / gamma key mapped to the future (from 2024-10; static per day)) + 'any' (union) + 'conf' (levels with another type within 5 pts): (i) T1 next level ahead, (ii) T2 second level, (iii) S4 stop 1 pt beyond nearest level behind (S1 / S8 buffers on any and conf), (iv) T1S4 both, (v) minimum reward:risk 1.0 / 1.5 / 2.0 on T1S4 for any, pd, vwap, vp, (vi) confluence = type 'conf'. Dynamic twins D9 for every type except conf (T1, T2, S4, T1S4) + widen 1.0 / 1.5, hysteresis 4, min 30 s on any, sess, vwap, vp, pd.
- Not built: supply/demand zones, trendlines and channels, X4 trigger-line trail, X6 volatility-burst exit, UW forecast range (X1c UW leg), X8 (W-DYNX8).
- Level data history: all level types come from the book's own bars (full history) except UW (panel _uwregime/panel.parquet from 2024-10-02; levels are prior-day by-strike files, static within the trading day; true intraday UW wall movement exists only since the live recorder started on 18 Nov per the order, about 7 trading days: THIN, not scored; forward register).

### Files and counts
Raw per-book weekly arrays: /mnt/l2/l2vast/_dynq/live3 (17 books + rand1 + rand2), Test 5 sample /mnt/l2/l2vast/_dynq/t5 (server C). Fixed rules: /mnt/l2/l2vast/_dynexit/fixed_rules_dynq.json (copy autopilot/DYNEXIT_FIXED_RULES_DYNQ.json). Spec: autopilot/DYNEXIT_SPEC.md. Scoreboard: 90 lines (method DYNEXIT: primary + refs STATIC, REFPOOL, X3D, X9D, X6; 5 mixes; steps 2/4/13) appended to /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl. Compute used: live books 17 x 287 recipes + 34 random-entry runs + 2 re-runs; Test 5 sample about 220 cells x 205-287 recipes (+ Asia random null).
Time estimate for the rest of the Test 5 qualifier cells (3,541 Asia + NY AM cells, 3,320 not yet run): with the fleet this saturated (my niced procs got 1-4 cores) about 15 CPU-hours = 10-20 h wall; with 30 free cores 40 min.


## ROUND 2 UPDATE (order 0349Z; 05:22Z)
Sample grown to 426 Test 5 cells (Asia 157 = 9.6%, NY AM 139 = 7.3%, London 80, NY PM 50) by running on C and A (A stopped at the disk order; the other ~3,650 cells are NOT run: C gets about 1-2 cells/min under the fleet load). These tables REPLACE the S2 numbers quoted in item 7 above (Asia now: X4 chandelier wins 2024, 2025, 2026 and L6M on income and DD, but L3M has income +56% with DD deeper ($145k vs $105k), so the strict test (both recent windows) is NOT met; random-entry null still on the earlier 130 cells). Table 14 answers whether the Asia lead is a bracket-sizing effect: it is a SHAPE effect (tight stop, far target / trailing), not width.

### Table 14 - Asia lead vs bracket SIZING / SHAPE (130 Asia qualifier cells with a random-entry twin; hold weeks; basket income $k / chained DD $k; own = the qualifier cell own bracket; REF rows = every fixed bracket of the grid run through the same kernel; X1 / X4 / X6 = the pre-written fixed rules)
| bracket / rule | 2026 income | 2026 DD | L6M income | L6M DD | L3M income | L3M DD | 2023 / 2024 / 2025 income | random entries: 2026 income | random: L6M income |
|---|---|---|---|---|---|---|---|---|---|
| OWN | +101 | 265 | +150 | 265 | +202 | 103 | -5 / +53 / +50 | -409 | -386 |
| plain60/60 | +84 | 234 | +120 | 234 | +185 | 53 | -6 / +69 / +50 | -389 | -329 |
| sym8u | -14 | 324 | +39 | 324 | +84 | 186 | -6 / +63 / +86 | -521 | -462 |
| sym15u | +13 | 294 | +55 | 294 | +87 | 210 | -5 / +76 / +78 | -471 | -446 |
| sym30u | -65 | 293 | -2 | 293 | +54 | 190 | -5 / +99 / +91 | -479 | -461 |
| asym10u/20u | -55 | 322 | +6 | 322 | +93 | 155 | -5 / +83 / +108 | -450 | -436 |
| asym20u/10u | -13 | 302 | +60 | 302 | +101 | 209 | -5 / +79 / +93 | -539 | -506 |
| asym15u/30u | -93 | 324 | +1 | 324 | +72 | 206 | -5 / +102 / +100 | -550 | -489 |
| fixed30/30 | +124 | 131 | +152 | 131 | +38 | 90 | +1 / -22 / -20 | -300 | -282 |
| fixed90/90 | -10 | 231 | -18 | 231 | +16 | 198 | -5 / +80 / +83 | -379 | -398 |
| fixed120/120 | -82 | 338 | -6 | 338 | +71 | 211 | -5 / +83 / +122 | -546 | -506 |
| fixed40/80 | +388 | 126 | +338 | 126 | +154 | 72 | -2 / +34 / +81 | -233 | -192 |
| fixed80/40 | +22 | 142 | +65 | 142 | +79 | 136 | -5 / +17 / +48 | -620 | -565 |
| fixed30/90 | +417 | 142 | +423 | 132 | +172 | 75 | -2 / +41 / +29 | -92 | -61 |
| fixed90/30 | -183 | 244 | -124 | 244 | -56 | 141 | -5 / -29 / +77 | -685 | -630 |
| fixed60/120 | +284 | 179 | +297 | 179 | +210 | 134 | -7 / +81 / +103 | -371 | -348 |
| fixed120/60 | -41 | 298 | +47 | 298 | +126 | 143 | +0 / +28 / +24 | -604 | -548 |
| X1 | +513 | 121 | +516 | 121 | +331 | 44 | -6 / +10 / +10 | -156 | -118 |
| X4 | +718 | 155 | +708 | 118 | +391 | 102 | -5 / +107 / +36 | -42 | -13 |
| X6 | +490 | 113 | +497 | 113 | +317 | 35 | -6 / -37 / -3 | -188 | -146 |
| fixed45/45 | +301 | 159 | +296 | 159 | +212 | 65 | -2 / +34 / +38 | -345 | -296 |

### Table 8 - S2: Test 5 primary qualifier baskets, a RANDOM SAMPLE of cells (quick screen; each held cell picks its own exit on its history, counted on its hold weeks only; income and DD of the equal-weight basket of the sampled cells, 1 base lot each; negative income = the sampled qualifiers lose money on their own fixed brackets)
| session, step, arm | cells | periods DD or worst week better | chained fwd DD $ dyn / fixed | fwd income $ dyn / fixed | L3M DD dyn / fixed | L6M DD dyn / fixed | verdict |
|---|---|---|---|---|---|---|---|
| Asia, 2w, ALL | 157 | 30/52 | 292,917 / 342,424 | 306,351 / 354,723 (-14%) | 292,917 / 342,424 | 292,917 / 342,424 | FAIL |
| Asia, 2w, REFPOOL | 157 | 25/50 | 338,307 / 342,424 | 370,685 / 354,723 (+4%) | 338,307 / 342,424 | 338,307 / 342,424 | **PASS** |
| Asia, 2w, X2 | 157 | 8/48 | 331,107 / 342,424 | 329,584 / 354,723 (-7%) | 331,107 / 342,424 | 331,107 / 342,424 | FAIL |
| Asia, 2w, X3 | 157 | 22/50 | 340,291 / 342,424 | 307,814 / 354,723 (-13%) | 340,291 / 342,424 | 340,291 / 342,424 | FAIL |
| Asia, 2w, X6 | 157 | 20/48 | 346,876 / 342,424 | 355,447 / 354,723 (+0%) | 346,876 / 342,424 | 346,876 / 342,424 | FAIL |
| NY AM, 2w, ALL | 139 | 38/62 | 602,379 / 658,332 | -292,538 / -190,353 (-54%) | 88,088 / 77,613 | 303,063 / 268,607 | FAIL |
| NY AM, 2w, REFPOOL | 139 | 34/60 | 658,124 / 658,332 | -310,230 / -190,353 (-63%) | 101,163 / 77,613 | 275,297 / 268,607 | FAIL |
| NY AM, 2w, X2 | 139 | 26/59 | 641,051 / 658,332 | -97,786 / -190,353 (+49%) | 99,467 / 77,613 | 277,607 / 268,607 | **PASS** |
| NY AM, 2w, X3 | 139 | 30/58 | 671,402 / 658,332 | -222,261 / -190,353 (-17%) | 73,823 / 77,613 | 271,096 / 268,607 | FAIL |
| NY AM, 2w, X6 | 139 | 27/59 | 654,762 / 658,332 | -215,535 / -190,353 (-13%) | 83,462 / 77,613 | 260,483 / 268,607 | FAIL |
| London, 2w, ALL | 80 | 34/63 | 198,383 / 136,896 | -187,427 / -109,629 (-71%) | 33,632 / 30,895 | 33,632 / 30,895 | FAIL |
| London, 2w, REFPOOL | 80 | 25/61 | 201,977 / 136,896 | -115,852 / -109,629 (-6%) | 23,299 / 30,895 | 23,299 / 30,895 | FAIL |
| London, 2w, X2 | 80 | 14/59 | 162,258 / 136,896 | -133,493 / -109,629 (-22%) | 30,234 / 30,895 | 30,234 / 30,895 | FAIL |
| London, 2w, X3 | 80 | 15/59 | 153,765 / 136,896 | -112,275 / -109,629 (-2%) | 30,895 / 30,895 | 30,895 / 30,895 | FAIL |
| London, 2w, X6 | 80 | 18/62 | 139,027 / 136,896 | -70,814 / -109,629 (+35%) | 25,542 / 30,895 | 25,542 / 30,895 | FAIL |
| NY PM, 2w, ALL | 50 | 35/64 | 134,371 / 105,923 | -14,208 / 76,425 (-119%) | 11,094 / 18,067 | 45,352 / 49,906 | FAIL |
| NY PM, 2w, REFPOOL | 50 | 35/58 | 108,939 / 105,923 | 101,858 / 76,425 (+33%) | 12,456 / 18,067 | 39,815 / 49,906 | FAIL |
| NY PM, 2w, X2 | 50 | 21/57 | 92,537 / 105,923 | 114,486 / 76,425 (+50%) | 15,064 / 18,067 | 42,165 / 49,906 | **PASS** |
| NY PM, 2w, X3 | 50 | 15/60 | 98,890 / 105,923 | 60,137 / 76,425 (-21%) | 18,067 / 18,067 | 49,906 / 49,906 | FAIL |
| NY PM, 2w, X6 | 50 | 16/60 | 118,250 / 105,923 | -2,214 / 76,425 (-103%) | 18,067 / 18,067 | 49,906 / 49,906 | FAIL |
| Asia, 4w, ALL | 157 | 17/34 | 339,091 / 342,424 | 259,501 / 354,723 (-27%) | 339,091 / 342,424 | 339,091 / 342,424 | FAIL |
| Asia, 4w, REFPOOL | 157 | 16/34 | 334,561 / 342,424 | 335,156 / 354,723 (-6%) | 334,561 / 342,424 | 334,561 / 342,424 | FAIL |
| Asia, 4w, X2 | 157 | 5/33 | 342,424 / 342,424 | 355,859 / 354,723 (+0%) | 342,424 / 342,424 | 342,424 / 342,424 | **PASS** |
| Asia, 4w, X3 | 157 | 12/33 | 342,424 / 342,424 | 277,187 / 354,723 (-22%) | 342,424 / 342,424 | 342,424 / 342,424 | FAIL |
| Asia, 4w, X6 | 157 | 10/33 | 339,516 / 342,424 | 346,139 / 354,723 (-2%) | 339,516 / 342,424 | 339,516 / 342,424 | FAIL |
| NY AM, 4w, ALL | 139 | 25/37 | 635,716 / 658,332 | -293,747 / -190,353 (-54%) | 95,461 / 77,613 | 329,757 / 268,607 | FAIL |
| NY AM, 4w, REFPOOL | 139 | 21/38 | 659,058 / 658,332 | -306,700 / -190,353 (-61%) | 96,351 / 77,613 | 280,364 / 268,607 | FAIL |
| NY AM, 4w, X2 | 139 | 21/37 | 620,243 / 658,332 | -106,278 / -190,353 (+44%) | 92,176 / 77,613 | 275,185 / 268,607 | **PASS** |
| NY AM, 4w, X3 | 139 | 21/37 | 666,408 / 658,332 | -216,628 / -190,353 (-14%) | 82,678 / 77,613 | 264,152 / 268,607 | FAIL |
| NY AM, 4w, X6 | 139 | 16/37 | 643,587 / 658,332 | -309,787 / -190,353 (-63%) | 80,809 / 77,613 | 260,664 / 268,607 | FAIL |
| London, 4w, ALL | 80 | 20/38 | 207,220 / 136,896 | -207,220 / -109,629 (-89%) | 39,080 / 30,895 | 39,080 / 30,895 | FAIL |
| London, 4w, REFPOOL | 80 | 18/38 | 201,659 / 136,896 | -130,951 / -109,629 (-19%) | 24,817 / 30,895 | 24,817 / 30,895 | FAIL |
| London, 4w, X2 | 80 | 10/38 | 138,638 / 136,896 | -62,391 / -109,629 (+43%) | 30,895 / 30,895 | 30,895 / 30,895 | FAIL |
| London, 4w, X3 | 80 | 11/38 | 162,535 / 136,896 | -129,426 / -109,629 (-18%) | 30,895 / 30,895 | 30,895 / 30,895 | FAIL |
| London, 4w, X6 | 80 | 11/38 | 140,280 / 136,896 | -71,429 / -109,629 (+35%) | 30,895 / 30,895 | 30,895 / 30,895 | FAIL |
| NY PM, 4w, ALL | 50 | 23/37 | 178,540 / 105,923 | -65,186 / 76,425 (-185%) | 11,429 / 18,067 | 27,784 / 29,741 | FAIL |
| NY PM, 4w, REFPOOL | 50 | 20/36 | 103,372 / 105,923 | 51,329 / 76,425 (-33%) | 12,456 / 18,067 | 26,161 / 29,741 | FAIL |
| NY PM, 4w, X2 | 50 | 11/37 | 132,108 / 105,923 | 43,918 / 76,425 (-43%) | 18,067 / 18,067 | 29,741 / 29,741 | FAIL |
| NY PM, 4w, X3 | 50 | 9/36 | 121,896 / 105,923 | 6,377 / 76,425 (-92%) | 18,067 / 18,067 | 29,741 / 29,741 | FAIL |
| NY PM, 4w, X6 | 50 | 11/36 | 128,597 / 105,923 | -12,561 / 76,425 (-116%) | 18,067 / 18,067 | 29,741 / 29,741 | FAIL |
| Asia, 13w, ALL | 157 | 10/12 | 312,989 / 342,424 | 270,672 / 354,723 (-24%) | 312,989 / 342,424 | 312,989 / 342,424 | FAIL |
| Asia, 13w, REFPOOL | 157 | 6/12 | 361,117 / 342,424 | 370,833 / 354,723 (+5%) | 361,117 / 342,424 | 361,117 / 342,424 | FAIL |
| Asia, 13w, X1 | 157 | 8/12 | 333,264 / 342,424 | 307,134 / 354,723 (-13%) | 333,264 / 342,424 | 333,264 / 342,424 | FAIL |
| Asia, 13w, X2 | 157 | 2/12 | 322,400 / 342,424 | 361,364 / 354,723 (+2%) | 322,400 / 342,424 | 322,400 / 342,424 | **PASS** |
| Asia, 13w, X3 | 157 | 7/12 | 342,424 / 342,424 | 276,023 / 354,723 (-22%) | 342,424 / 342,424 | 342,424 / 342,424 | FAIL |
| Asia, 13w, X4 | 157 | 7/12 | 308,677 / 342,424 | 297,877 / 354,723 (-16%) | 308,677 / 342,424 | 308,677 / 342,424 | FAIL |
| Asia, 13w, X5 | 157 | 6/12 | 318,006 / 342,424 | 395,826 / 354,723 (+12%) | 318,006 / 342,424 | 318,006 / 342,424 | **PASS** |
| Asia, 13w, X6 | 157 | 5/12 | 339,642 / 342,424 | 292,447 / 354,723 (-18%) | 339,642 / 342,424 | 339,642 / 342,424 | FAIL |
| Asia, 13w, X7 | 157 | 2/12 | 337,940 / 342,424 | 358,433 / 354,723 (+1%) | 337,940 / 342,424 | 337,940 / 342,424 | **PASS** |
| Asia, 13w, X9 | 157 | 9/12 | 339,372 / 342,424 | 336,242 / 354,723 (-5%) | 339,372 / 342,424 | 339,372 / 342,424 | **PASS** |
| NY AM, 13w, ALL | 139 | 7/13 | 671,759 / 658,332 | -392,659 / -190,353 (-106%) | 101,948 / 77,613 | 323,569 / 268,607 | FAIL |
| NY AM, 13w, REFPOOL | 139 | 7/13 | 762,396 / 658,332 | -342,657 / -190,353 (-80%) | 83,912 / 77,613 | 361,933 / 268,607 | FAIL |
| NY AM, 13w, X1 | 139 | 10/13 | 680,255 / 658,332 | -306,830 / -190,353 (-61%) | 97,266 / 77,613 | 288,209 / 268,607 | FAIL |
| NY AM, 13w, X2 | 139 | 9/13 | 668,994 / 658,332 | -105,177 / -190,353 (+45%) | 83,371 / 77,613 | 277,410 / 268,607 | **PASS** |
| NY AM, 13w, X3 | 139 | 9/13 | 646,286 / 658,332 | -243,321 / -190,353 (-28%) | 81,653 / 77,613 | 273,385 / 268,607 | FAIL |
| NY AM, 13w, X4 | 139 | 8/13 | 628,144 / 658,332 | -249,859 / -190,353 (-31%) | 84,167 / 77,613 | 256,173 / 268,607 | FAIL |
| NY AM, 13w, X5 | 139 | 6/13 | 626,479 / 658,332 | -302,699 / -190,353 (-59%) | 88,508 / 77,613 | 281,766 / 268,607 | FAIL |
| NY AM, 13w, X6 | 139 | 8/13 | 652,890 / 658,332 | -332,755 / -190,353 (-75%) | 95,984 / 77,613 | 265,625 / 268,607 | FAIL |
| NY AM, 13w, X7 | 139 | 6/13 | 661,709 / 658,332 | -171,705 / -190,353 (+10%) | 77,741 / 77,613 | 268,607 / 268,607 | FAIL |
| NY AM, 13w, X9 | 139 | 8/13 | 730,036 / 658,332 | -570,547 / -190,353 (-200%) | 103,110 / 77,613 | 363,466 / 268,607 | FAIL |
| London, 13w, ALL | 80 | 8/13 | 155,532 / 136,896 | -136,493 / -109,629 (-25%) | 33,252 / 30,895 | 33,252 / 30,895 | FAIL |
| London, 13w, REFPOOL | 80 | 6/13 | 142,227 / 136,896 | -107,559 / -109,629 (+2%) | 24,712 / 30,895 | 24,712 / 30,895 | FAIL |
| London, 13w, X1 | 80 | 4/13 | 201,553 / 136,896 | -161,762 / -109,629 (-48%) | 23,942 / 30,895 | 23,942 / 30,895 | FAIL |
| London, 13w, X2 | 80 | 2/13 | 142,733 / 136,896 | -120,160 / -109,629 (-10%) | 30,895 / 30,895 | 30,895 / 30,895 | FAIL |
| London, 13w, X3 | 80 | 3/13 | 208,002 / 136,896 | -164,653 / -109,629 (-50%) | 30,895 / 30,895 | 30,895 / 30,895 | FAIL |
| London, 13w, X4 | 80 | 3/13 | 256,934 / 136,896 | -196,253 / -109,629 (-79%) | 32,639 / 30,895 | 32,639 / 30,895 | FAIL |
| London, 13w, X5 | 80 | 5/13 | 148,629 / 136,896 | -138,134 / -109,629 (-26%) | 36,572 / 30,895 | 36,572 / 30,895 | FAIL |
| London, 13w, X6 | 80 | 4/13 | 230,600 / 136,896 | -163,463 / -109,629 (-49%) | 30,895 / 30,895 | 30,895 / 30,895 | FAIL |
| London, 13w, X7 | 80 | 2/13 | 194,184 / 136,896 | -161,665 / -109,629 (-47%) | 30,895 / 30,895 | 30,895 / 30,895 | FAIL |
| London, 13w, X9 | 80 | 7/13 | 164,271 / 136,896 | -140,111 / -109,629 (-28%) | 33,252 / 30,895 | 33,252 / 30,895 | FAIL |
| NY PM, 13w, ALL | 50 | 10/12 | 183,697 / 105,923 | -40,064 / 76,425 (-152%) | 10,935 / 18,067 | 48,156 / 49,906 | FAIL |
| NY PM, 13w, REFPOOL | 50 | 8/12 | 141,068 / 105,923 | 17,659 / 76,425 (-77%) | 12,456 / 18,067 | 41,055 / 49,906 | FAIL |
| NY PM, 13w, X1 | 50 | 6/12 | 146,938 / 105,923 | -30,902 / 76,425 (-140%) | 18,067 / 18,067 | 49,906 / 49,906 | FAIL |
| NY PM, 13w, X2 | 50 | 5/12 | 94,428 / 105,923 | 73,909 / 76,425 (-3%) | 18,067 / 18,067 | 43,715 / 49,906 | FAIL |
| NY PM, 13w, X3 | 50 | 5/12 | 158,650 / 105,923 | -29,986 / 76,425 (-139%) | 18,067 / 18,067 | 49,906 / 49,906 | FAIL |
| NY PM, 13w, X4 | 50 | 4/12 | 98,890 / 105,923 | 53,536 / 76,425 (-30%) | 18,067 / 18,067 | 49,906 / 49,906 | FAIL |
| NY PM, 13w, X5 | 50 | 2/12 | 100,649 / 105,923 | 115,359 / 76,425 (+51%) | 18,067 / 18,067 | 49,906 / 49,906 | **PASS** |
| NY PM, 13w, X6 | 50 | 4/12 | 120,338 / 105,923 | -4,302 / 76,425 (-106%) | 18,067 / 18,067 | 49,906 / 49,906 | FAIL |
| NY PM, 13w, X7 | 50 | 2/12 | 108,503 / 105,923 | 14,919 / 76,425 (-80%) | 18,067 / 18,067 | 49,906 / 49,906 | FAIL |
| NY PM, 13w, X9 | 50 | 8/12 | 166,523 / 105,923 | 28,002 / 76,425 (-63%) | 10,935 / 18,067 | 35,940 / 49,906 | FAIL |

### Table 8b - S2 fixed rules (pre-written defaults) on the sampled qualifier cells: windows won of 6 (2023, 2024, 2025, 2026, L6M, L3M), L6M DD $ rule / fixed and L6M income $ rule / fixed
| session | rule | cells with the rule | windows won | L6M DD | L6M income | L3M DD | L3M income |
|---|---|---|---|---|---|---|---|
| Asia | X1 | 157 | 3 | 167,180 / 342,424 | 714,240 / 310,661 | 45,690 / 105,444 | 470,215 / 326,594 |
| Asia | X2 | 157 | 3 | 207,554 / 342,424 | 762,873 / 310,661 | 171,527 / 105,444 | 310,633 / 326,594 |
| Asia | X3 | 157 | 3 | 147,463 / 342,424 | 347,833 / 310,661 | 143,990 / 105,444 | 126,748 / 326,594 |
| Asia | X4 | 157 | 4 | 156,901 / 342,424 | 955,905 / 310,661 | 145,329 / 105,444 | 509,063 / 326,594 |
| Asia | X5 | 157 | 4 | 132,624 / 342,424 | 602,700 / 310,661 | 93,369 / 105,444 | 309,468 / 326,594 |
| Asia | X6 | 157 | 3 | 156,821 / 342,424 | 693,916 / 310,661 | 44,678 / 105,444 | 456,435 / 326,594 |
| Asia | X7 | 157 | 3 | 459,028 / 342,424 | 514,256 / 310,661 | 229,058 / 105,444 | 295,526 / 326,594 |
| Asia | X9 | 157 | 0 | 249,300 / 342,424 | -229,255 / 310,661 | 161,513 / 105,444 | -154,707 / 326,594 |
| Asia | X3D | 76 | 0 | 170,922 / 189,958 | 39,591 / 317,804 | 165,163 / 35,242 | -62,130 / 281,573 |
| Asia | X9D | 76 | 0 | 110,683 / 189,958 | -94,810 / 317,804 | 68,339 / 35,242 | -55,050 / 281,573 |
| NY AM | X1 | 139 | 0 | 485,752 / 192,169 | -465,426 / -69,032 | 177,471 / 77,613 | -108,580 / 7,757 |
| NY AM | X2 | 139 | 2 | 255,659 / 192,169 | -159,293 / -69,032 | 212,952 / 77,613 | 28,874 / 7,757 |
| NY AM | X3 | 139 | 3 | 176,965 / 192,169 | -7,663 / -69,032 | 120,974 / 77,613 | -395 / 7,757 |
| NY AM | X4 | 139 | 0 | 342,991 / 192,169 | -330,435 / -69,032 | 138,736 / 77,613 | -73,390 / 7,757 |
| NY AM | X5 | 139 | 0 | 508,825 / 192,169 | -504,073 / -69,032 | 119,645 / 77,613 | -114,893 / 7,757 |
| NY AM | X6 | 139 | 0 | 404,028 / 192,169 | -385,353 / -69,032 | 165,775 / 77,613 | -85,179 / 7,757 |
| NY AM | X7 | 139 | 0 | 392,876 / 192,169 | -335,582 / -69,032 | 178,156 / 77,613 | 2,965 / 7,757 |
| NY AM | X9 | 139 | 0 | 500,202 / 192,169 | -500,202 / -69,032 | 93,269 / 77,613 | -93,269 / 7,757 |
| NY AM | X3D | 100 | 0 | 126,533 / 102,036 | -40,838 / 112,740 | 119,751 / 72,313 | 10,774 / 29,399 |
| NY AM | X9D | 100 | 0 | 320,447 / 102,036 | -320,447 / 112,740 | 78,635 / 72,313 | -78,635 / 29,399 |
| London | X1 | 80 | 4 | 23,791 / 30,895 | 11,491 / 5,019 | 23,791 / 30,895 | -6,533 / -12,827 |
| London | X2 | 80 | 1 | 34,814 / 30,895 | 33,915 / 5,019 | 34,814 / 30,895 | -1,586 / -12,827 |
| London | X3 | 80 | 4 | 12,193 / 30,895 | 22,054 / 5,019 | 2,184 / 30,895 | 21,218 / -12,827 |
| London | X4 | 80 | 3 | 25,880 / 30,895 | 472 / 5,019 | 25,880 / 30,895 | -11,062 / -12,827 |
| London | X5 | 80 | 1 | 25,230 / 30,895 | -15,645 / 5,019 | 25,230 / 30,895 | -21,372 / -12,827 |
| London | X6 | 80 | 4 | 21,761 / 30,895 | 23,065 / 5,019 | 21,761 / 30,895 | 401 / -12,827 |
| London | X7 | 80 | 1 | 30,944 / 30,895 | -18,374 / 5,019 | 30,944 / 30,895 | -26,537 / -12,827 |
| London | X9 | 80 | 1 | 22,070 / 30,895 | -20,360 / 5,019 | 13,081 / 30,895 | -13,081 / -12,827 |
| London | X3D | 79 | 4 | 12,151 / 30,895 | 15,328 / 5,019 | 7,506 / 30,895 | 15,228 / -12,827 |
| London | X9D | 79 | 1 | 17,451 / 30,895 | -15,397 / 5,019 | 11,954 / 30,895 | -11,954 / -12,827 |
| NY PM | X1 | 50 | 0 | 24,535 / 25,740 | 5,038 / 94,816 | 17,940 / 18,067 | -16,259 / 11,994 |
| NY PM | X2 | 50 | 0 | 76,555 / 25,740 | -52,970 / 94,816 | 30,536 / 18,067 | -14,145 / 11,994 |
| NY PM | X3 | 50 | 1 | 15,049 / 25,740 | 33,309 / 94,816 | 15,049 / 18,067 | 9,011 / 11,994 |
| NY PM | X4 | 50 | 1 | 13,624 / 25,740 | 64,589 / 94,816 | 6,848 / 18,067 | 26,011 / 11,994 |
| NY PM | X5 | 50 | 0 | 12,700 / 25,740 | 22,401 / 94,816 | 5,899 / 18,067 | 5,733 / 11,994 |
| NY PM | X6 | 50 | 0 | 27,613 / 25,740 | 11,422 / 94,816 | 16,457 / 18,067 | -8,222 / 11,994 |
| NY PM | X7 | 50 | 0 | 27,131 / 25,740 | 35,243 / 94,816 | 27,131 / 18,067 | -12,301 / 11,994 |
| NY PM | X9 | 50 | 0 | 44,605 / 25,740 | -44,605 / 94,816 | 17,703 / 18,067 | -13,170 / 11,994 |
| NY PM | X3D | 47 | 2 | 17,682 / 25,740 | 49,681 / 94,816 | 10,433 / 18,067 | 28,541 / 11,994 |
| NY PM | X9D | 47 | 0 | 63,752 / 25,740 | -63,752 / 94,816 | 18,074 / 18,067 | -15,887 / 11,994 |


## ROUND 3 / ORDER 0525Z TABLES

## Stuck-trade exit (item 1), tables S1-S5 (sessions Asia, London, NY AM, NY PM, all 17; 3 live books unmapped; with-Trade-Health (d) and exact (g): NOT DONE, need exact rows)
Pessimistic = +0.85 pt (DS3_DN_STOPFILL 1-lot stop slippage) on every losing exit, label only. Null = same fraction of trades (hash of the entry time) exited unconditionally at the same minute. Kernel identity: with the stuck block off the own-bracket row equals the standard run (3,088.6 pts / 1,629 trades, tested). Fired shares in Table S3.

### Table S1 - (a) FIXED RULE stuck exit 45 min / 0.25R (leave when 45 min after the fill the best excursion is under 0.25 R and the trade is under water), on top of each book own bracket; chained windows, all books of the session summed, 1 base lot. rule / own: DD $, income $; pess = income with +0.85 pt on every losing exit (rule and own alike); NUL = random-exit null at the same fraction of trades exited at 45 min unconditionally
| session | window | DD rule / own | worst week rule / own | income rule / own | income pess rule / own | NUL income / DD | books winning | window win |
|---|---|---|---|---|---|---|---|---|
| Asia | L3M | 5,351 / 5,608 | -5,351 / -5,608 | 25,118 / 27,404 (-8%) | 20,953 / 23,562 | 28,396 / 7,912 | 1/3 | WIN |
| Asia | L6M | 6,039 / 5,608 | -5,351 / -5,608 | 39,652 / 41,102 (-4%) | 30,336 / 32,296 | 45,678 / 8,554 | 1/3 | - |
| Asia | 2026 | 21,236 / 19,955 | -8,426 / -8,426 | 57,340 / 62,673 (-9%) | 42,890 / 49,396 | 74,687 / 11,385 | 1/3 | - |
| Asia | 2025 | 21,354 / 19,243 | -14,077 / -13,462 | 29,591 / 41,668 (-29%) | 16,586 / 31,995 | 30,096 / 27,373 | 0/3 | - |
| Asia | 2024 | 15,632 / 20,482 | -7,170 / -7,429 | 49,104 / 59,619 (-18%) | 35,725 / 51,986 | 52,572 / 19,777 | 2/3 | - |
| Asia | 2023 | 13,235 / 9,075 | -5,876 / -6,041 | -2,386 / 11,966 (-120%) | -13,793 / 7,189 | 9,477 / 9,564 | 0/3 | - |
| Asia | ALL | 21,354 / 21,572 | -14,077 / -13,462 | 133,649 / 175,925 (-24%) | 81,408 / 140,565 | 166,832 / 32,176 | 0/3 | - |
| London | L3M | 11,094 / 6,048 | -11,094 / -6,048 | 48,330 / 60,726 (-20%) | 42,091 / 56,561 | 46,443 / 6,983 | 0/3 | - |
| London | L6M | 11,094 / 10,062 | -11,094 / -10,062 | 116,738 / 112,438 (+4%) | 104,430 / 103,683 | 91,887 / 7,656 | 2/3 | - |
| London | 2026 | 14,460 / 20,769 | -11,094 / -10,774 | 137,260 / 132,283 (+4%) | 116,435 / 117,816 | 116,762 / 17,277 | 1/3 | WIN |
| London | 2025 | 21,312 / 39,466 | -16,120 / -21,137 | 27,429 / 52,764 (-48%) | 4,292 / 39,674 | 15,462 / 44,741 | 1/3 | - |
| London | 2024 | 14,634 / 8,067 | -9,005 / -4,792 | 65,993 / 84,947 (-22%) | 42,686 / 74,662 | 85,791 / 5,601 | 2/3 | - |
| London | 2023 | 11,797 / 19,882 | -4,262 / -11,708 | 4,756 / 22,855 (-79%) | -12,567 / 16,803 | 36,550 / 13,360 | 1/3 | - |
| London | ALL | 21,312 / 39,466 | -16,120 / -21,137 | 235,439 / 292,848 (-20%) | 150,847 / 248,954 | 254,565 / 44,741 | 1/3 | - |
| NY AM | L3M | 11,633 / 13,763 | -11,633 / -13,763 | 100,354 / 105,834 (-5%) | 93,792 / 99,663 | 100,212 / 13,763 | 2/7 | WIN |
| NY AM | L6M | 28,781 / 29,241 | -28,781 / -29,241 | 227,183 / 227,464 (-0%) | 211,713 / 212,487 | 227,564 / 28,388 | 2/7 | WIN |
| NY AM | 2026 | 51,689 / 48,039 | -28,781 / -29,241 | 242,537 / 247,374 (-2%) | 216,901 / 222,588 | 249,558 / 48,314 | 3/7 | - |
| NY AM | 2025 | 40,963 / 47,331 | -23,492 / -23,492 | 191,750 / 188,320 (+2%) | 166,760 / 165,897 | 185,314 / 50,786 | 3/7 | WIN |
| NY AM | 2024 | 46,383 / 42,234 | -20,902 / -20,412 | 122,400 / 117,287 (+4%) | 96,458 / 95,697 | 119,116 / 43,590 | 4/7 | - |
| NY AM | 2023 | 31,293 / 33,564 | -19,100 / -16,841 | 23,211 / 77,326 (-70%) | 5,327 / 64,287 | 75,388 / 30,585 | 1/7 | - |
| NY AM | ALL | 52,678 / 56,959 | -28,781 / -29,241 | 579,899 / 630,307 (-8%) | 485,447 / 548,469 | 629,376 / 60,355 | 1/7 | WIN |
| NY PM | L3M | 3,456 / 5,035 | -3,160 / -5,035 | 41,099 / 48,386 (-15%) | 36,135 / 43,745 | 44,423 / 5,870 | 2/4 | - |
| NY PM | L6M | 6,884 / 5,035 | -6,884 / -5,035 | 72,971 / 95,589 (-24%) | 62,193 / 85,559 | 73,056 / 8,029 | 1/4 | - |
| NY PM | 2026 | 29,520 / 17,396 | -6,884 / -6,734 | 61,091 / 99,395 (-39%) | 43,717 / 83,364 | 73,198 / 17,939 | 0/4 | - |
| NY PM | 2025 | 17,746 / 16,106 | -11,071 / -11,596 | 82,774 / 93,627 (-12%) | 63,972 / 77,324 | 89,925 / 17,926 | 2/4 | - |
| NY PM | 2024 | 33,912 / 33,512 | -16,456 / -12,601 | 59,569 / 54,049 (+10%) | 40,733 / 37,678 | 71,900 / 31,552 | 2/4 | - |
| NY PM | 2023 | 15,972 / 16,125 | -6,884 / -8,855 | 57,372 / 66,381 (-14%) | 44,503 / 56,147 | 66,326 / 19,704 | 2/4 | - |
| NY PM | ALL | 41,707 / 33,512 | -16,456 / -12,601 | 260,806 / 313,452 (-17%) | 192,925 / 254,513 | 301,349 / 31,552 | 0/4 | - |
| All 17 | L3M | 18,625 / 15,710 | -18,625 / -15,710 | 214,901 / 242,350 (-11%) | 192,971 / 223,531 | 219,474 / 17,006 | 5/17 | - |
| All 17 | L6M | 21,751 / 22,398 | -21,751 / -22,398 | 456,543 / 476,592 (-4%) | 408,671 / 434,024 | 438,185 / 21,363 | 6/17 | WIN |
| All 17 | 2026 | 60,581 / 66,273 | -41,144 / -39,181 | 498,229 / 541,724 (-8%) | 419,944 / 473,163 | 514,204 / 49,281 | 5/17 | WIN |
| All 17 | 2025 | 46,972 / 52,373 | -37,650 / -45,294 | 331,543 / 376,379 (-12%) | 251,609 / 314,890 | 320,798 / 58,302 | 6/17 | - |
| All 17 | 2024 | 28,357 / 35,514 | -27,299 / -35,514 | 297,067 / 315,901 (-6%) | 215,603 / 260,022 | 329,378 / 32,160 | 10/17 | WIN |
| All 17 | 2023 | 29,105 / 24,205 | -24,502 / -17,383 | 82,954 / 178,528 (-54%) | 23,471 / 144,426 | 187,741 / 26,366 | 4/17 | - |
| All 17 | ALL | 60,581 / 66,273 | -41,144 / -45,294 | 1,209,793 / 1,412,532 (-14%) | 910,627 / 1,192,501 | 1,352,121 / 58,302 | 2/17 | - |

### Table S2 - (b) PLATEAU MAP, all books summed (17), income and DD change vs own bracket (rule minus own, percent of own), L6M | whole period | 2023-25 years won of 3; and random-exit null change in the same cell. Minutes down, R across

L6M income change %:
| minutes \ R | 0.1 | 0.25 | 0.5 |
|---|---|---|---|
| 20 | -0% (null -20%) | -5% (null -18%) | -23% (null -29%) |
| 30 | -9% (null -12%) | -15% (null -20%) | -33% (null -22%) |
| 45 | +3% (null -3%) | -4% (null -8%) | -16% (null -15%) |
| 60 | +7% (null -3%) | +4% (null -4%) | -13% (null -9%) |
| 90 | +2% (null -1%) | +5% (null +1%) | -5% (null -1%) |

L6M DD change %:
| minutes \ R | 0.1 | 0.25 | 0.5 |
|---|---|---|---|
| 20 | -5% (null -11%) | -11% (null +23%) | +1% (null +56%) |
| 30 | -11% (null -5%) | -16% (null -7%) | -14% (null -10%) |
| 45 | -10% (null -6%) | -3% (null -5%) | +23% (null -1%) |
| 60 | -10% (null -12%) | +5% (null -12%) | +32% (null -6%) |
| 90 | -7% (null -4%) | +6% (null -4%) | +17% (null -4%) |

whole period income change %:
| minutes \ R | 0.1 | 0.25 | 0.5 |
|---|---|---|---|
| 20 | -11% (null -7%) | -27% (null -12%) | -45% (null -27%) |
| 30 | -9% (null -3%) | -18% (null -10%) | -35% (null -15%) |
| 45 | -4% (null -1%) | -14% (null -4%) | -24% (null -8%) |
| 60 | +1% (null +0%) | -8% (null -3%) | -22% (null -9%) |
| 90 | -3% (null +0%) | -4% (null +1%) | -13% (null +0%) |

whole period DD change %:
| minutes \ R | 0.1 | 0.25 | 0.5 |
|---|---|---|---|
| 20 | -1% (null -10%) | -7% (null -22%) | -28% (null -9%) |
| 30 | -4% (null -22%) | -9% (null -21%) | -10% (null -21%) |
| 45 | -5% (null -11%) | -9% (null -12%) | -13% (null -12%) |
| 60 | -15% (null -12%) | -15% (null -19%) | -16% (null -19%) |
| 90 | -5% (null -6%) | -13% (null -9%) | +3% (null -8%) |

### Table S3 - relatives (45 min / 0.25R unless stated), all 17 books, rule / own; chained
| relative | L3M DD | L3M income | L6M DD | L6M income | whole DD | whole income | pess whole income | fired share of trades |
|---|---|---|---|---|---|---|---|---|
| STK|m45|r0.25 | 18,625 / 15,710 | 214,901 / 242,350 | 21,751 / 22,398 | 456,543 / 476,592 | 60,581 / 66,273 | 1,209,793 / 1,412,532 | 910,627 / 1,192,501 | 18% |
| STKB|bars6|r0.25 | 15,760 / 15,710 | 139,815 / 242,350 | 15,760 / 22,398 | 328,386 / 476,592 | 81,624 / 66,273 | 893,103 / 1,412,532 | 418,174 / 1,192,501 | 42% |
| STKB|bars12|r0.25 | 26,092 / 15,710 | 202,631 / 242,350 | 26,092 / 22,398 | 429,688 / 476,592 | 71,639 / 66,273 | 1,084,202 / 1,412,532 | 719,926 / 1,192,501 | 28% |
| STKN|noext6 | 21,571 / 15,710 | 100,049 / 242,350 | 21,571 / 22,398 | 277,685 / 476,592 | 51,692 / 66,273 | 628,903 / 1,412,532 | -18,389 / 1,192,501 | 61% |
| STKN|noext12 | 20,292 / 15,710 | 164,877 / 242,350 | 20,451 / 22,398 | 358,131 / 476,592 | 61,603 / 66,273 | 889,355 / 1,412,532 | 409,751 / 1,192,501 | 45% |
| STKT|m45|r0.25|left120 | 16,162 / 15,710 | 231,945 / 242,350 | 23,834 / 22,398 | 483,063 / 476,592 | 56,351 / 66,273 | 1,297,272 / 1,412,532 | 1,037,461 / 1,192,501 | 12% |
| STKH|m45|r0.25|halve | 16,576 / 15,710 | 233,867 / 242,350 | 22,601 / 22,398 | 467,490 / 476,592 | 61,495 / 66,273 | 1,301,937 / 1,412,532 | 1,075,837 / 1,192,501 | 14% |

### Table S4 - random-ENTRY twins (2 draws, same count and side mix): fixed rule minus own on random entries, all 17, $ (a rule that only trims noise or harvests drift also shows here)
| window | rule - own income real | rule - own income random (mean) | DD change real | DD change random |
|---|---|---|---|---|
| L3M | -27,449 | 12,596 | 2,916 | -8,348 |
| L6M | -20,049 | 14,736 | -646 | -18,475 |
| 2026 | -43,496 | 40,913 | -5,692 | -15,821 |
| ALL | -202,739 | -44,233 | -5,692 | -30,535 |

### Table S5 - (c) WALK-FORWARD of the exit pick (existing rule: eligible = L6M and L3M positive, >= 20 trades, no prior year >30% worse; lowest ulcer then highest recent income), pool = the stuck-exit recipes of the stated family, vs the book own bracket; steps 2 / 4 / 13 weeks; chained forward max DD $, worst week $, income $ rule / own; periods DD or worst week better; PASS per the order; pess = on pessimistic series
| session | step | pool | periods better | DD rule / own | worst week rule / own | income rule / own | pess income rule / own | picked != own | verdict |
|---|---|---|---|---|---|---|---|---|---|
| Asia | 2 | ALL | 11/52 | 24,581 / 21,572 | -13,462 / -13,462 | 161,658 / 165,389 | 132,460 / 133,310 | 80/80 | FAIL |
| Asia | 2 | STK | 10/52 | 24,575 / 21,572 | -13,462 / -13,462 | 161,959 / 165,389 | 133,130 / 133,310 | 80/80 | FAIL |
| Asia | 2 | STKB | 3/51 | 21,572 / 21,572 | -13,462 / -13,462 | 165,391 / 165,389 | 134,056 / 133,310 | 80/80 | identical (<0.5%) |
| Asia | 2 | STKN | 7/51 | 21,718 / 21,572 | -13,462 / -13,462 | 164,234 / 165,389 | 134,362 / 133,310 | 80/80 | FAIL |
| Asia | 2 | STKT | 4/51 | 20,489 / 21,572 | -13,462 / -13,462 | 166,298 / 165,389 | 133,013 / 133,310 | 80/80 | **PASS** |
| Asia | 2 | STKH | 4/51 | 21,510 / 21,572 | -13,462 / -13,462 | 165,488 / 165,389 | 133,117 / 133,310 | 80/80 | identical (<0.5%) |
| London | 2 | ALL | 16/53 | 55,539 / 39,466 | -21,518 / -21,137 | 221,505 / 286,820 | 224,825 / 247,295 | 80/80 | FAIL |
| London | 2 | STK | 14/53 | 55,539 / 39,466 | -21,518 / -21,137 | 212,493 / 286,820 | 226,500 / 247,295 | 80/80 | FAIL |
| London | 2 | STKB | 11/46 | 39,466 / 39,466 | -21,137 / -21,137 | 276,152 / 286,820 | 237,094 / 247,295 | 80/80 | FAIL |
| London | 2 | STKN | 7/47 | 39,466 / 39,466 | -21,137 / -21,137 | 275,783 / 286,820 | 242,770 / 247,295 | 80/80 | FAIL |
| London | 2 | STKT | 4/45 | 40,659 / 39,466 | -22,464 / -21,137 | 285,102 / 286,820 | 244,195 / 247,295 | 80/80 | FAIL |
| London | 2 | STKH | 11/46 | 38,550 / 39,466 | -21,137 / -21,137 | 280,632 / 286,820 | 248,821 / 247,295 | 80/80 | FAIL |
| NY AM | 2 | ALL | 19/55 | 60,611 / 56,959 | -29,241 / -29,241 | 563,194 / 595,045 | 481,723 / 522,064 | 80/80 | FAIL |
| NY AM | 2 | STK | 13/55 | 53,479 / 56,959 | -29,241 / -29,241 | 567,210 / 595,045 | 489,507 / 522,064 | 80/80 | FAIL |
| NY AM | 2 | STKB | 5/54 | 56,839 / 56,959 | -29,241 / -29,241 | 583,642 / 595,045 | 512,182 / 522,064 | 80/80 | FAIL |
| NY AM | 2 | STKN | 12/54 | 64,091 / 56,959 | -29,241 / -29,241 | 587,569 / 595,045 | 495,802 / 522,064 | 80/80 | FAIL |
| NY AM | 2 | STKT | 3/54 | 56,429 / 56,959 | -29,241 / -29,241 | 587,665 / 595,045 | 520,032 / 522,064 | 80/80 | FAIL |
| NY AM | 2 | STKH | 9/54 | 56,819 / 56,959 | -29,241 / -29,241 | 594,284 / 595,045 | 519,278 / 522,064 | 80/80 | identical (<0.5%) |
| NY PM | 2 | ALL | 30/57 | 29,209 / 33,512 | -11,596 / -12,601 | 241,405 / 274,830 | 211,548 / 222,776 | 80/80 | FAIL |
| NY PM | 2 | STK | 28/55 | 30,396 / 33,512 | -13,721 / -12,601 | 226,716 / 274,830 | 196,153 / 222,776 | 80/80 | FAIL |
| NY PM | 2 | STKB | 7/52 | 33,512 / 33,512 | -12,601 / -12,601 | 273,330 / 274,830 | 235,130 / 222,776 | 80/80 | FAIL |
| NY PM | 2 | STKN | 10/52 | 33,512 / 33,512 | -12,601 / -12,601 | 274,836 / 274,830 | 226,558 / 222,776 | 80/80 | identical (<0.5%) |
| NY PM | 2 | STKT | 11/53 | 30,107 / 33,512 | -13,626 / -12,601 | 275,820 / 274,830 | 221,240 / 222,776 | 80/80 | **PASS** |
| NY PM | 2 | STKH | 16/51 | 31,260 / 33,512 | -11,596 / -12,601 | 276,056 / 274,830 | 223,686 / 222,776 | 80/80 | **PASS** |
| All 17 | 2 | ALL | 18/45 | 63,372 / 66,273 | -45,294 / -45,294 | 1,187,761 / 1,322,084 | 1,050,556 / 1,125,445 | 80/80 | FAIL |
| All 17 | 2 | STK | 15/46 | 60,197 / 66,273 | -45,294 / -45,294 | 1,168,377 / 1,322,084 | 1,045,290 / 1,125,445 | 80/80 | FAIL |
| All 17 | 2 | STKB | 5/40 | 66,273 / 66,273 | -45,294 / -45,294 | 1,298,516 / 1,322,084 | 1,118,461 / 1,125,445 | 80/80 | FAIL |
| All 17 | 2 | STKN | 10/40 | 69,449 / 66,273 | -45,294 / -45,294 | 1,302,422 / 1,322,084 | 1,099,492 / 1,125,445 | 80/80 | FAIL |
| All 17 | 2 | STKT | 8/41 | 66,273 / 66,273 | -45,294 / -45,294 | 1,314,885 / 1,322,084 | 1,118,479 / 1,125,445 | 80/80 | FAIL |
| All 17 | 2 | STKH | 15/40 | 66,273 / 66,273 | -45,294 / -45,294 | 1,316,460 / 1,322,084 | 1,124,902 / 1,125,445 | 80/80 | identical (<0.5%) |
| Asia | 4 | ALL | 12/34 | 24,799 / 21,572 | -12,855 / -13,462 | 162,002 / 165,389 | 133,843 / 133,310 | 40/40 | FAIL |
| Asia | 4 | STK | 12/34 | 24,799 / 21,572 | -12,855 / -13,462 | 162,535 / 165,389 | 135,779 / 133,310 | 40/40 | FAIL |
| Asia | 4 | STKB | 1/33 | 21,572 / 21,572 | -13,462 / -13,462 | 166,355 / 165,389 | 134,089 / 133,310 | 40/40 | **PASS** |
| Asia | 4 | STKN | 4/33 | 21,572 / 21,572 | -13,462 / -13,462 | 167,500 / 165,389 | 135,443 / 133,310 | 40/40 | **PASS** |
| Asia | 4 | STKT | 2/33 | 21,214 / 21,572 | -13,462 / -13,462 | 165,231 / 165,389 | 133,045 / 133,310 | 40/40 | FAIL |
| Asia | 4 | STKH | 3/33 | 21,510 / 21,572 | -13,462 / -13,462 | 165,683 / 165,389 | 133,397 / 133,310 | 40/40 | identical (<0.5%) |
| London | 4 | ALL | 13/34 | 51,070 / 39,466 | -20,502 / -21,137 | 213,239 / 286,820 | 224,427 / 247,295 | 40/40 | FAIL |
| London | 4 | STK | 12/34 | 51,070 / 39,466 | -20,502 / -21,137 | 206,731 / 286,820 | 226,269 / 247,295 | 40/40 | FAIL |
| London | 4 | STKB | 9/31 | 39,466 / 39,466 | -21,137 / -21,137 | 273,088 / 286,820 | 249,167 / 247,295 | 40/40 | FAIL |
| London | 4 | STKN | 6/31 | 39,466 / 39,466 | -21,137 / -21,137 | 271,694 / 286,820 | 239,503 / 247,295 | 40/40 | FAIL |
| London | 4 | STKT | 3/31 | 40,659 / 39,466 | -22,464 / -21,137 | 278,430 / 286,820 | 245,822 / 247,295 | 40/40 | FAIL |
| London | 4 | STKH | 8/31 | 38,725 / 39,466 | -20,671 / -21,137 | 281,035 / 286,820 | 246,370 / 247,295 | 40/40 | FAIL |
| NY AM | 4 | ALL | 12/37 | 52,293 / 56,959 | -29,241 / -29,241 | 574,858 / 595,045 | 475,572 / 522,064 | 40/40 | FAIL |
| NY AM | 4 | STK | 8/37 | 56,183 / 56,959 | -29,241 / -29,241 | 562,633 / 595,045 | 487,091 / 522,064 | 40/40 | FAIL |
| NY AM | 4 | STKB | 3/37 | 56,959 / 56,959 | -29,241 / -29,241 | 583,271 / 595,045 | 508,772 / 522,064 | 40/40 | FAIL |
| NY AM | 4 | STKN | 7/37 | 53,069 / 56,959 | -29,241 / -29,241 | 582,492 / 595,045 | 486,863 / 522,064 | 40/40 | FAIL |
| NY AM | 4 | STKT | 2/37 | 56,959 / 56,959 | -29,241 / -29,241 | 585,724 / 595,045 | 517,386 / 522,064 | 40/40 | FAIL |
| NY AM | 4 | STKH | 4/37 | 56,687 / 56,959 | -29,241 / -29,241 | 591,635 / 595,045 | 517,136 / 522,064 | 40/40 | FAIL |
| NY PM | 4 | ALL | 19/37 | 26,729 / 33,512 | -11,181 / -12,601 | 241,314 / 274,830 | 207,756 / 222,776 | 40/40 | FAIL |
| NY PM | 4 | STK | 19/37 | 24,762 / 33,512 | -13,721 / -12,601 | 251,784 / 274,830 | 215,203 / 222,776 | 40/40 | FAIL |
| NY PM | 4 | STKB | 2/35 | 35,545 / 33,512 | -12,601 / -12,601 | 247,468 / 274,830 | 223,636 / 222,776 | 40/40 | FAIL |
| NY PM | 4 | STKN | 6/36 | 32,232 / 33,512 | -12,601 / -12,601 | 280,114 / 274,830 | 225,323 / 222,776 | 40/40 | **PASS** |
| NY PM | 4 | STKT | 10/35 | 28,331 / 33,512 | -13,626 / -12,601 | 280,980 / 274,830 | 227,991 / 222,776 | 40/40 | **PASS** |
| NY PM | 4 | STKH | 12/35 | 31,190 / 33,512 | -11,596 / -12,601 | 274,348 / 274,830 | 223,357 / 222,776 | 40/40 | FAIL |
| All 17 | 4 | ALL | 15/32 | 60,984 / 66,273 | -46,014 / -45,294 | 1,191,412 / 1,322,084 | 1,041,599 / 1,125,445 | 40/40 | FAIL |
| All 17 | 4 | STK | 15/33 | 61,316 / 66,273 | -45,219 / -45,294 | 1,183,683 / 1,322,084 | 1,064,342 / 1,125,445 | 40/40 | FAIL |
| All 17 | 4 | STKB | 5/31 | 66,273 / 66,273 | -41,515 / -45,294 | 1,270,182 / 1,322,084 | 1,115,663 / 1,125,445 | 40/40 | FAIL |
| All 17 | 4 | STKN | 9/30 | 66,353 / 66,273 | -46,089 / -45,294 | 1,301,801 / 1,322,084 | 1,087,132 / 1,125,445 | 40/40 | FAIL |
| All 17 | 4 | STKT | 10/31 | 66,273 / 66,273 | -45,069 / -45,294 | 1,310,365 / 1,322,084 | 1,124,243 / 1,125,445 | 40/40 | FAIL |
| All 17 | 4 | STKH | 15/30 | 66,273 / 66,273 | -45,567 / -45,294 | 1,312,701 / 1,322,084 | 1,120,261 / 1,125,445 | 40/40 | FAIL |
| Asia | 13 | ALL | 3/13 | 23,528 / 21,572 | -13,462 / -13,462 | 159,040 / 165,389 | 131,511 / 133,310 | 13/13 | FAIL |
| Asia | 13 | STK | 3/13 | 23,528 / 21,572 | -13,462 / -13,462 | 160,562 / 165,389 | 132,819 / 133,310 | 13/13 | FAIL |
| Asia | 13 | STKB | 2/13 | 22,463 / 21,572 | -13,462 / -13,462 | 163,230 / 165,389 | 130,680 / 133,310 | 13/13 | FAIL |
| Asia | 13 | STKN | 2/13 | 22,048 / 21,572 | -13,462 / -13,462 | 161,273 / 165,389 | 134,065 / 133,310 | 13/13 | FAIL |
| Asia | 13 | STKT | 1/13 | 22,836 / 21,572 | -13,462 / -13,462 | 163,339 / 165,389 | 130,461 / 133,310 | 13/13 | FAIL |
| Asia | 13 | STKH | 2/13 | 21,591 / 21,572 | -13,462 / -13,462 | 164,385 / 165,389 | 133,015 / 133,310 | 13/13 | FAIL |
| London | 13 | ALL | 5/13 | 43,400 / 39,466 | -21,518 / -21,137 | 247,093 / 286,820 | 215,903 / 247,295 | 13/13 | FAIL |
| London | 13 | STK | 5/13 | 43,400 / 39,466 | -21,518 / -21,137 | 244,215 / 286,820 | 211,839 / 247,295 | 13/13 | FAIL |
| London | 13 | STKB | 5/13 | 38,990 / 39,466 | -21,137 / -21,137 | 265,949 / 286,820 | 251,855 / 247,295 | 13/13 | FAIL |
| London | 13 | STKN | 4/13 | 39,466 / 39,466 | -21,137 / -21,137 | 278,827 / 286,820 | 240,835 / 247,295 | 13/13 | FAIL |
| London | 13 | STKT | 2/13 | 42,047 / 39,466 | -22,464 / -21,137 | 285,752 / 286,820 | 252,372 / 247,295 | 13/13 | FAIL |
| London | 13 | STKH | 5/13 | 39,191 / 39,466 | -21,137 / -21,137 | 283,283 / 286,820 | 242,048 / 247,295 | 13/13 | FAIL |
| NY AM | 13 | ALL | 7/13 | 49,109 / 56,959 | -27,996 / -29,241 | 577,418 / 595,045 | 495,389 / 522,064 | 13/13 | FAIL |
| NY AM | 13 | STK | 7/13 | 51,381 / 56,959 | -27,996 / -29,241 | 561,160 / 595,045 | 484,010 / 522,064 | 13/13 | FAIL |
| NY AM | 13 | STKB | 2/13 | 56,449 / 56,959 | -29,241 / -29,241 | 593,550 / 595,045 | 514,573 / 522,064 | 13/13 | FAIL |
| NY AM | 13 | STKN | 3/13 | 56,959 / 56,959 | -29,241 / -29,241 | 576,308 / 595,045 | 508,718 / 522,064 | 13/13 | FAIL |
| NY AM | 13 | STKT | 4/13 | 54,413 / 56,959 | -29,241 / -29,241 | 595,546 / 595,045 | 521,343 / 522,064 | 13/13 | **PASS** |
| NY AM | 13 | STKH | 5/13 | 52,277 / 56,959 | -29,241 / -29,241 | 593,745 / 595,045 | 518,657 / 522,064 | 13/13 | FAIL |
| NY PM | 13 | ALL | 9/13 | 28,337 / 33,512 | -11,972 / -12,601 | 253,663 / 274,830 | 196,066 / 222,776 | 13/13 | **PASS** |
| NY PM | 13 | STK | 8/13 | 24,762 / 33,512 | -13,721 / -12,601 | 246,279 / 274,830 | 186,903 / 222,776 | 13/13 | FAIL |
| NY PM | 13 | STKB | 4/13 | 24,414 / 33,512 | -11,596 / -12,601 | 260,423 / 274,830 | 213,897 / 222,776 | 13/13 | FAIL |
| NY PM | 13 | STKN | 3/13 | 31,012 / 33,512 | -12,601 / -12,601 | 276,108 / 274,830 | 237,494 / 222,776 | 13/13 | **PASS** |
| NY PM | 13 | STKT | 4/13 | 30,314 / 33,512 | -13,626 / -12,601 | 260,563 / 274,830 | 211,625 / 222,776 | 13/13 | FAIL |
| NY PM | 13 | STKH | 4/13 | 29,495 / 33,512 | -11,611 / -12,601 | 269,253 / 274,830 | 217,589 / 222,776 | 13/13 | FAIL |
| All 17 | 13 | ALL | 7/12 | 61,901 / 66,273 | -42,287 / -45,294 | 1,237,214 / 1,322,084 | 1,038,870 / 1,125,445 | 13/13 | FAIL |
| All 17 | 13 | STK | 5/12 | 61,380 / 66,273 | -43,750 / -45,294 | 1,212,215 / 1,322,084 | 1,015,572 / 1,125,445 | 13/13 | FAIL |
| All 17 | 13 | STKB | 5/12 | 64,953 / 66,273 | -39,748 / -45,294 | 1,283,152 / 1,322,084 | 1,111,004 / 1,125,445 | 13/13 | FAIL |
| All 17 | 13 | STKN | 3/12 | 62,768 / 66,273 | -46,089 / -45,294 | 1,292,516 / 1,322,084 | 1,121,113 / 1,125,445 | 13/13 | FAIL |
| All 17 | 13 | STKT | 3/12 | 63,068 / 66,273 | -45,745 / -45,294 | 1,305,200 / 1,322,084 | 1,115,801 / 1,125,445 | 13/13 | FAIL |
| All 17 | 13 | STKH | 5/12 | 65,372 / 66,273 | -45,567 / -45,294 | 1,310,666 / 1,322,084 | 1,111,309 / 1,125,445 | 13/13 | FAIL |


## Fair entries (item 2): tables F1, F2

### Table F1 - FAIR comparison, 17 live books: dynamic-exit pick vs WALK-FORWARD BRACKET (both chosen by the same standing pick rule on data before each date; bracket pool = the 17 grid brackets; fallback plain60/60 for both; neither side has hindsight). chained forward DD $, worst week $, income $ dyn / walk-forward bracket
| session | step | dynamic pool | periods DD or worst week better | DD dyn / bracket | worst week | income (change) | verdict |
|---|---|---|---|---|---|---|---|
| Asia | 2 | ALL | 35/64 | 34,253 / 36,332 | -15,049 / -16,563 | 48,899 / 130,288 (-62%) | FAIL |
| Asia | 2 | ALL+REF | 34/62 | 34,253 / 36,332 | -16,249 / -16,563 | 55,883 / 130,288 (-57%) | FAIL |
| Asia | 2 | X3D | 9/58 | 38,460 / 36,332 | -15,363 / -16,563 | 113,556 / 130,288 (-13%) | FAIL |
| Asia | 2 | X2 | 17/59 | 38,460 / 36,332 | -15,363 / -16,563 | 115,576 / 130,288 (-11%) | FAIL |
| NY AM | 2 | ALL | 32/60 | 53,064 / 65,279 | -25,140 / -26,348 | 299,115 / 405,487 (-26%) | FAIL |
| NY AM | 2 | ALL+REF | 31/60 | 50,688 / 65,279 | -25,140 / -26,348 | 284,124 / 405,487 (-30%) | FAIL |
| NY AM | 2 | X3D | 32/60 | 59,637 / 65,279 | -34,660 / -26,348 | 325,652 / 405,487 (-20%) | FAIL |
| NY AM | 2 | X2 | 29/56 | 66,881 / 65,279 | -36,554 / -26,348 | 384,808 / 405,487 (-5%) | FAIL |
| London | 2 | ALL | 27/55 | 36,935 / 34,315 | -18,995 / -22,860 | 112,316 / 259,599 (-57%) | FAIL |
| London | 2 | ALL+REF | 25/54 | 45,181 / 34,315 | -18,995 / -22,860 | 113,848 / 259,599 (-56%) | FAIL |
| London | 2 | X3D | 20/53 | 39,315 / 34,315 | -19,847 / -22,860 | 221,067 / 259,599 (-15%) | FAIL |
| London | 2 | X2 | 23/53 | 32,275 / 34,315 | -19,847 / -22,860 | 196,740 / 259,599 (-24%) | FAIL |
| NY PM | 2 | ALL | 25/68 | 83,491 / 36,676 | -30,545 / -15,897 | 23,184 / 334,681 (-93%) | FAIL |
| NY PM | 2 | ALL+REF | 24/66 | 71,993 / 36,676 | -30,545 / -15,897 | 44,526 / 334,681 (-87%) | FAIL |
| NY PM | 2 | X3D | 31/55 | 32,443 / 36,676 | -13,563 / -15,897 | 278,045 / 334,681 (-17%) | FAIL |
| NY PM | 2 | X2 | 27/53 | 45,704 / 36,676 | -21,504 / -15,897 | 287,476 / 334,681 (-14%) | FAIL |
| All 17 | 2 | ALL | 20/59 | 92,752 / 110,729 | -43,838 / -38,417 | 483,515 / 1,130,054 (-57%) | FAIL |
| All 17 | 2 | ALL+REF | 20/58 | 85,769 / 110,729 | -43,801 / -38,417 | 498,382 / 1,130,054 (-56%) | FAIL |
| All 17 | 2 | X3D | 20/50 | 77,714 / 110,729 | -41,419 / -38,417 | 938,320 / 1,130,054 (-17%) | FAIL |
| All 17 | 2 | X2 | 21/51 | 93,947 / 110,729 | -34,786 / -38,417 | 984,600 / 1,130,054 (-13%) | FAIL |
| Asia | 4 | ALL | 22/37 | 37,265 / 32,506 | -15,049 / -16,563 | 18,435 / 119,127 (-85%) | FAIL |
| Asia | 4 | ALL+REF | 21/37 | 37,265 / 32,506 | -16,249 / -16,563 | 20,895 / 119,127 (-82%) | FAIL |
| Asia | 4 | X3D | 10/37 | 38,460 / 32,506 | -15,363 / -16,563 | 112,454 / 119,127 (-6%) | FAIL |
| Asia | 4 | X2 | 14/37 | 43,170 / 32,506 | -15,363 / -16,563 | 97,063 / 119,127 (-19%) | FAIL |
| NY AM | 4 | ALL | 20/39 | 65,010 / 58,911 | -33,296 / -40,141 | 304,005 / 421,099 (-28%) | FAIL |
| NY AM | 4 | ALL+REF | 20/39 | 57,554 / 58,911 | -33,296 / -40,141 | 277,294 / 421,099 (-34%) | FAIL |
| NY AM | 4 | X3D | 22/38 | 59,415 / 58,911 | -34,660 / -40,141 | 334,146 / 421,099 (-21%) | FAIL |
| NY AM | 4 | X2 | 19/38 | 56,122 / 58,911 | -28,873 / -40,141 | 421,372 / 421,099 (+0%) | **PASS** |
| London | 4 | ALL | 21/36 | 56,362 / 41,494 | -31,394 / -20,025 | 135,917 / 237,792 (-43%) | FAIL |
| London | 4 | ALL+REF | 20/36 | 46,334 / 41,494 | -31,394 / -20,025 | 175,843 / 237,792 (-26%) | FAIL |
| London | 4 | X3D | 15/34 | 37,595 / 41,494 | -19,847 / -20,025 | 216,877 / 237,792 (-9%) | FAIL |
| London | 4 | X2 | 17/33 | 34,917 / 41,494 | -19,505 / -20,025 | 195,511 / 237,792 (-18%) | FAIL |
| NY PM | 4 | ALL | 15/38 | 64,280 / 37,367 | -30,545 / -18,083 | 85,941 / 301,098 (-71%) | FAIL |
| NY PM | 4 | ALL+REF | 14/38 | 47,525 / 37,367 | -30,545 / -18,083 | 111,742 / 301,098 (-63%) | FAIL |
| NY PM | 4 | X3D | 21/35 | 33,786 / 37,367 | -13,563 / -18,083 | 260,780 / 301,098 (-13%) | FAIL |
| NY PM | 4 | X2 | 20/35 | 49,169 / 37,367 | -21,504 / -18,083 | 265,842 / 301,098 (-12%) | FAIL |
| All 17 | 4 | ALL | 12/39 | 109,270 / 100,457 | -62,227 / -57,618 | 544,299 / 1,079,116 (-50%) | FAIL |
| All 17 | 4 | ALL+REF | 12/38 | 99,054 / 100,457 | -62,227 / -57,618 | 585,774 / 1,079,116 (-46%) | FAIL |
| All 17 | 4 | X3D | 15/34 | 84,391 / 100,457 | -41,419 / -57,618 | 924,258 / 1,079,116 (-14%) | FAIL |
| All 17 | 4 | X2 | 16/34 | 84,382 / 100,457 | -35,739 / -57,618 | 979,788 / 1,079,116 (-9%) | FAIL |
| Asia | 13 | ALL | 11/13 | 41,044 / 44,081 | -15,049 / -15,363 | 78,345 / 109,384 (-28%) | FAIL |
| Asia | 13 | ALL+REF | 11/13 | 40,710 / 44,081 | -15,049 / -15,363 | 72,961 / 109,384 (-33%) | FAIL |
| Asia | 13 | X3D | 3/13 | 38,460 / 44,081 | -15,363 / -15,363 | 109,159 / 109,384 (-0%) | FAIL |
| Asia | 13 | X2 | 4/13 | 38,460 / 44,081 | -15,363 / -15,363 | 118,118 / 109,384 (+8%) | **PASS** |
| NY AM | 13 | ALL | 9/13 | 66,097 / 52,097 | -25,519 / -31,546 | 350,554 / 415,612 (-16%) | FAIL |
| NY AM | 13 | ALL+REF | 8/13 | 90,761 / 52,097 | -31,124 / -31,546 | 313,209 / 415,612 (-25%) | FAIL |
| NY AM | 13 | X3D | 8/13 | 48,575 / 52,097 | -26,212 / -31,546 | 419,429 / 415,612 (+1%) | **PASS** |
| NY AM | 13 | X2 | 8/13 | 45,126 / 52,097 | -34,660 / -31,546 | 368,171 / 415,612 (-11%) | FAIL |
| London | 13 | ALL | 9/13 | 50,883 / 50,790 | -18,995 / -22,860 | 106,118 / 210,429 (-50%) | FAIL |
| London | 13 | ALL+REF | 9/13 | 31,954 / 50,790 | -19,562 / -22,860 | 141,745 / 210,429 (-33%) | FAIL |
| London | 13 | X3D | 6/13 | 37,238 / 50,790 | -19,847 / -22,860 | 198,478 / 210,429 (-6%) | FAIL |
| London | 13 | X2 | 9/13 | 38,369 / 50,790 | -19,847 / -22,860 | 225,674 / 210,429 (+7%) | **PASS** |
| NY PM | 13 | ALL | 8/13 | 28,321 / 38,584 | -19,247 / -15,897 | 182,931 / 272,289 (-33%) | FAIL |
| NY PM | 13 | ALL+REF | 7/13 | 28,321 / 38,584 | -22,146 / -15,897 | 130,695 / 272,289 (-52%) | FAIL |
| NY PM | 13 | X3D | 9/13 | 33,307 / 38,584 | -10,894 / -15,897 | 268,122 / 272,289 (-2%) | **PASS** |
| NY PM | 13 | X2 | 7/13 | 37,392 / 38,584 | -13,296 / -15,897 | 259,691 / 272,289 (-5%) | FAIL |
| All 17 | 13 | ALL | 8/13 | 55,943 / 115,822 | -36,221 / -42,795 | 717,948 / 1,007,714 (-29%) | FAIL |
| All 17 | 13 | ALL+REF | 7/13 | 78,524 / 115,822 | -36,221 / -42,795 | 658,612 / 1,007,714 (-35%) | FAIL |
| All 17 | 13 | X3D | 7/13 | 77,879 / 115,822 | -36,013 / -42,795 | 995,187 / 1,007,714 (-1%) | FAIL |
| All 17 | 13 | X2 | 10/13 | 74,024 / 115,822 | -40,448 / -42,795 | 971,653 / 1,007,714 (-4%) | **PASS** |

### Table F2 - FAIR comparison on the Test 5 qualifier cells (bracket NOT tuned on those weeks: the cell bracket is the qualifier family median; compared here against the WALK-FORWARD bracket pick): random sample of cells, held weeks only, baskets of the sampled cells (negative income = the qualifier sample loses money)
| session | step | dynamic pool | cells | periods better | DD dyn / bracket | income dyn / bracket | verdict |
|---|---|---|---|---|---|---|---|
| Asia | 2 | ALL | 168 | 30/54 | 292,974 / 347,972 | 295,131 / 379,532 | FAIL |
| Asia | 2 | ALL+REF | 168 | 27/53 | 334,676 / 347,972 | 216,076 / 379,532 | FAIL |
| Asia | 2 | X1 | 168 | 30/53 | 330,649 / 347,972 | 450,596 / 379,532 | **PASS** |
| Asia | 2 | X3 | 168 | 32/54 | 323,925 / 347,972 | 415,438 / 379,532 | **PASS** |
| Asia | 2 | X4 | 168 | 21/53 | 298,711 / 347,972 | 453,983 / 379,532 | **PASS** |
| Asia | 2 | X6 | 168 | 21/52 | 324,711 / 347,972 | 484,470 / 379,532 | **PASS** |
| NY AM | 2 | ALL | 171 | 36/67 | 687,749 / 872,805 | -412,388 / -666,417 | **PASS** |
| NY AM | 2 | ALL+REF | 171 | 37/68 | 685,080 / 872,805 | -435,629 / -666,417 | **PASS** |
| NY AM | 2 | X1 | 171 | 28/67 | 956,623 / 872,805 | -886,570 / -666,417 | FAIL |
| NY AM | 2 | X3 | 171 | 33/67 | 1,095,618 / 872,805 | -1,043,733 / -666,417 | FAIL |
| NY AM | 2 | X4 | 171 | 34/68 | 950,653 / 872,805 | -885,361 / -666,417 | FAIL |
| NY AM | 2 | X6 | 171 | 31/67 | 1,056,871 / 872,805 | -1,018,214 / -666,417 | FAIL |
| Asia | 4 | ALL | 168 | 21/35 | 313,353 / 337,304 | 247,355 / 389,992 | FAIL |
| Asia | 4 | ALL+REF | 168 | 19/34 | 340,380 / 337,304 | 194,102 / 389,992 | FAIL |
| Asia | 4 | X1 | 168 | 19/34 | 329,369 / 337,304 | 493,026 / 389,992 | **PASS** |
| Asia | 4 | X3 | 168 | 20/34 | 329,369 / 337,304 | 417,420 / 389,992 | **PASS** |
| Asia | 4 | X4 | 168 | 16/34 | 306,138 / 337,304 | 450,285 / 389,992 | **PASS** |
| Asia | 4 | X6 | 168 | 16/34 | 322,141 / 337,304 | 474,191 / 389,992 | **PASS** |
| NY AM | 4 | ALL | 171 | 28/39 | 807,218 / 821,160 | -587,089 / -740,175 | **PASS** |
| NY AM | 4 | ALL+REF | 171 | 27/40 | 774,587 / 821,160 | -584,293 / -740,175 | **PASS** |
| NY AM | 4 | X1 | 171 | 19/40 | 981,345 / 821,160 | -938,817 / -740,175 | FAIL |
| NY AM | 4 | X3 | 171 | 20/40 | 1,163,676 / 821,160 | -1,104,302 / -740,175 | FAIL |
| NY AM | 4 | X4 | 171 | 19/40 | 1,003,336 / 821,160 | -915,289 / -740,175 | FAIL |
| NY AM | 4 | X6 | 171 | 20/40 | 1,152,267 / 821,160 | -1,112,385 / -740,175 | FAIL |
| Asia | 13 | ALL | 168 | 8/12 | 281,898 / 344,262 | 253,877 / 372,705 | FAIL |
| Asia | 13 | ALL+REF | 168 | 7/12 | 306,566 / 344,262 | 266,184 / 372,705 | FAIL |
| Asia | 13 | X1 | 168 | 10/12 | 320,209 / 344,262 | 387,245 / 372,705 | **PASS** |
| Asia | 13 | X3 | 168 | 9/12 | 329,369 / 344,262 | 355,955 / 372,705 | **PASS** |
| Asia | 13 | X4 | 168 | 5/12 | 291,302 / 344,262 | 389,355 / 372,705 | **PASS** |
| Asia | 13 | X6 | 168 | 8/12 | 314,513 / 344,262 | 418,535 / 372,705 | **PASS** |
| NY AM | 13 | ALL | 171 | 7/13 | 843,997 / 981,147 | -713,155 / -751,966 | **PASS** |
| NY AM | 13 | ALL+REF | 171 | 8/13 | 911,832 / 981,147 | -732,723 / -751,966 | **PASS** |
| NY AM | 13 | X1 | 171 | 9/13 | 1,024,622 / 981,147 | -987,134 / -751,966 | FAIL |
| NY AM | 13 | X3 | 171 | 8/13 | 1,036,546 / 981,147 | -974,352 / -751,966 | FAIL |
| NY AM | 13 | X4 | 171 | 4/13 | 1,254,072 / 981,147 | -1,175,641 / -751,966 | FAIL |
| NY AM | 13 | X6 | 171 | 5/13 | 1,227,777 / 981,147 | -1,195,382 / -751,966 | FAIL |


## ROUND 3: Asia gap closure (X4 twin null on 133 Asia cells; X4t = tighter chandelier committed before scoring: stop 1.5 x U, chandelier 2.0 x ATR14)
Result: X4 on the 133 twin cells: L6M income $741k / DD $120k vs own $187k / $284k; L3M $395k / DD $106k vs own $229k / DD $104k (L3M DD now equal); on random entries X4 earns about $0 (L6M +$10k) while own loses $374k: real gain over own +$554k, random gain +$384k, excess of real over random +$170k. X4t (tighter, 2 settings): L6M $427k / DD $224k, L3M DD $200k vs own $104k: tighter is WORSE on drawdown; X4 stays as registered. NY AM widen-vs-shape: only 10 NY AM cells have a random twin yet (twin run continues on C): not reportable.

### Table 14/15 - Asia lead vs bracket SIZING / SHAPE (133 qualifier cells with a random-entry twin; hold weeks; basket income $k / chained DD $k; own = the qualifier cell own bracket; REF rows = every fixed bracket of the grid run through the same kernel; X1 / X4 / X6 = the pre-written fixed rules)
| bracket / rule | 2026 income | 2026 DD | L6M income | L6M DD | L3M income | L3M DD | 2023 / 2024 / 2025 income | random entries: 2026 income | random: L6M income |
|---|---|---|---|---|---|---|---|---|---|
| OWN | +134 | 284 | +187 | 284 | +229 | 104 | -5 / +53 / +64 | -405 | -374 |
| plain60/60 | +81 | 251 | +118 | 251 | +199 | 51 | -6 / +68 / +63 | -400 | -340 |
| sym8u | -7 | 343 | +54 | 343 | +85 | 187 | -6 / +63 / +100 | -525 | -460 |
| sym15u | +19 | 321 | +70 | 321 | +95 | 211 | -5 / +76 / +78 | -462 | -431 |
| sym30u | -57 | 320 | +14 | 320 | +63 | 191 | -5 / +100 / +105 | -471 | -447 |
| asym10u/20u | -49 | 350 | +19 | 350 | +100 | 158 | -5 / +84 / +122 | -445 | -426 |
| asym20u/10u | -11 | 330 | +70 | 330 | +104 | 212 | -5 / +80 / +107 | -540 | -502 |
| asym15u/30u | -85 | 351 | +17 | 351 | +80 | 207 | -5 / +102 / +115 | -543 | -476 |
| fixed30/30 | +135 | 140 | +161 | 140 | +34 | 96 | +1 / -24 / -20 | -292 | -272 |
| fixed90/90 | +3 | 250 | -3 | 250 | +16 | 210 | -5 / +80 / +105 | -354 | -367 |
| fixed120/120 | -74 | 365 | +9 | 365 | +80 | 212 | -5 / +83 / +136 | -538 | -492 |
| fixed40/80 | +419 | 135 | +363 | 135 | +155 | 78 | -2 / +34 / +90 | -226 | -177 |
| fixed80/40 | +52 | 155 | +103 | 155 | +104 | 129 | -5 / +18 / +62 | -621 | -556 |
| fixed30/90 | +437 | 142 | +440 | 138 | +174 | 85 | -2 / +40 / +37 | -86 | -52 |
| fixed90/30 | -143 | 232 | -83 | 232 | -33 | 132 | -5 / -29 / +86 | -675 | -619 |
| fixed60/120 | +293 | 182 | +313 | 182 | +218 | 142 | -7 / +81 / +119 | -372 | -343 |
| fixed120/60 | -21 | 319 | +73 | 319 | +134 | 150 | +0 / +28 / +33 | -616 | -551 |
| X1 | +551 | 128 | +558 | 128 | +352 | 44 | -6 / +10 / +28 | -183 | -134 |
| X4 | +755 | 155 | +741 | 120 | +395 | 106 | -5 / +107 / +77 | -30 | +10 |
| X6 | +528 | 120 | +539 | 120 | +338 | 34 | -6 / -36 / +11 | -213 | -160 |
| X4t | +463 | 224 | +427 | 224 | +79 | 200 | -6 / +13 / +53 | -98 | -83 |
| fixed45/45 | +322 | 180 | +317 | 180 | +219 | 72 | -2 / +34 / +43 | -326 | -270 |


## AS8 SECOND PAIR OF EYES (order 0525Z follow-up; PLAN_AS lead: stuck exit 0.75 min per stop point, 0.25R, under water + profitable trades leave 15 min before session end)
Same rule re-implemented in my kernel (code/th_dynq/dq_stuckk.py, DP[18] min per stop point, DP[19] end rule; identity: own row unchanged). My numbers vs PLAN_AS: **partly agree.** Recent windows agree; whole-period and drawdown do not on my 3 Asia live books, and the reasons are (a) books: my Asia set is 3 grid cells with 40/80, 45/45 and 30/30 brackets; PLAN_AS's MF4 (22 min stuck, fails in its own screen: 'cuts late winners in 2025-26') is my 30/30 book (whole income -42%, L6M -18%); the 60-pt MF1/MF2 books are not among my 17 mapped cells (unmapped), so the best-behaved books are missing; (b) weighting: PLAN_AS is live lots (60-pt stop gets fewer lots), mine is 1 lot per book; (c) PLAN_AS chose the 0.75 min/pt setting after seeing the plateau (its own caveat). On my 3 Asia books: whole income -32%, DD $25.8k vs $21.6k, L6M +4% income with DD $7.0k vs $5.6k, 2026 -18%. All 17: L6M +4%, L3M -2% with DD $12.8k vs $15.7k (window win), 2026 -3% (win), whole -15%, pessimistic -28%. Why all-17 stuck is -14% to -15% while PLAN_AS says -1% for Asia: the stuck exit costs income in 2023 (-54%) and 2025 (-12%) in my set and only trims noise in the recent windows; PLAN_AS's whole-period number is on four books with live-lot weighting that favours the wide-stop books.
Test 5 ASIA qualifier cells (not tuned on those weeks; bracket = family median), sample of 72 cells (growing): AS8 vs the cell's own bracket: wins L3M (income +98%, DD $80.6k vs $90.8k), L6M (+52%, DD $83.4k vs $90.8k), 2026 (+36%), 2025 (+120%) and loses 2024 (-219%, DD $91k vs $47k; 2023: no held weeks); whole period income -15% with DD deeper ($125k vs $101k); beats the random-exit null at the same fraction in L6M ($126k vs $81k) and L3M ($52k vs $13k). FAIR vs the WALK-FORWARD BRACKET (cells re-pick among 17 brackets on prior data): AS8 passes at 13, 4 and 2 weeks (chained DD $125k vs $184k / $181k / $188k, income $72k vs -$24k / +$30k / +$1k). Plain reading: with no hindsight on the bracket AS8 is better than a walk-forward bracket on Asia qualifiers, and recent-window better than the family bracket, but it is not better than the bracket across 2024 and it has a 2024 hole; it agrees with PLAN_AS on the direction in the recent windows, not on whole-period drawdown for these books.

NY AM widen-vs-shape (26 NY AM qualifier cells with random twins; L6M income / DD $k, own bracket 26/10): fixed90/90 3/21, 120/120 20/19, 30/90 -36/47, 40/80 -13/18, 60/120 -11/28, X1 -17/31, X4 -1/25, X4t -29/43, X6 -17/30; L3M X4 +24/10 vs own 14/9. No shape or width gain in NY AM (26 cells, thin): the Asia trend-capture lead is Asia-specific.

### Table A1 - AS8 on the 17 live books (quick screen, own bracket + stuck exit 0.75 min per stop point at 0.25R under water + profitable trades leave 15 min before session end); rule / own, all books of the session summed, 1 base lot; NUL = random exit at the same fraction (same end rule); pess = +0.85 pt per losing exit
| session | window | DD rule / own | income rule / own | pess income rule / own | NUL income / DD | stuck only (no end rule) income / DD | end rule only income / DD | win |
|---|---|---|---|---|---|---|---|---|
| Asia (3 books) | L3M | 6,992 / 5,608 | 22,575 / 27,404 (-18%) | 18,036 / 23,562 | 24,460 / 8,290 | 25,970 / 5,289 | 23,275 / 6,605 | - |
| Asia (3 books) | L6M | 6,992 / 5,608 | 42,741 / 41,102 (+4%) | 32,898 / 32,296 | 42,576 / 8,290 | 45,598 / 5,289 | 37,277 / 6,605 | - |
| Asia (3 books) | 2026 | 24,962 / 19,955 | 51,699 / 62,673 (-18%) | 36,212 / 49,396 | 74,866 / 8,290 | 56,748 / 23,529 | 56,391 / 21,395 | - |
| Asia (3 books) | 2025 | 25,753 / 19,243 | 26,987 / 41,668 (-35%) | 12,265 / 31,995 | 39,293 / 20,855 | 24,463 / 26,009 | 46,222 / 19,732 | - |
| Asia (3 books) | 2024 | 10,022 / 20,482 | 50,001 / 59,619 (-16%) | 33,681 / 51,986 | 53,350 / 17,329 | 49,059 / 11,396 | 60,751 / 17,997 | - |
| Asia (3 books) | 2023 | 16,229 / 9,075 | -9,426 / 11,966 (-179%) | -23,723 / 7,189 | 2,989 / 9,879 | -3,690 / 12,737 | 7,239 / 9,490 | - |
| Asia (3 books) | ALL | 25,753 / 21,572 | 119,261 / 175,925 (-32%) | 58,435 / 140,565 | 170,498 / 22,861 | 126,580 / 26,009 | 170,602 / 21,395 | - |
| London | L3M | 7,151 / 6,048 | 70,420 / 60,726 (+16%) | 64,283 / 56,561 | 51,831 / 11,278 | 66,526 / 10,078 | 63,900 / 7,906 | - |
| London | L6M | 7,151 / 10,062 | 128,742 / 112,438 (+15%) | 116,349 / 103,683 | 93,203 / 11,278 | 130,106 / 10,078 | 110,698 / 9,633 | WIN |
| London | 2026 | 14,614 / 20,769 | 138,725 / 132,283 (+5%) | 117,951 / 117,816 | 109,523 / 17,097 | 146,621 / 15,018 | 125,022 / 19,581 | WIN |
| London | 2025 | 33,980 / 39,466 | 27,445 / 52,764 (-48%) | 3,186 / 39,674 | 37,477 / 39,870 | 23,560 / 33,205 | 53,653 / 37,318 | - |
| London | 2024 | 18,081 / 8,067 | 67,591 / 84,947 (-20%) | 41,462 / 74,662 | 76,471 / 7,666 | 66,721 / 16,681 | 85,324 / 11,269 | - |
| London | 2023 | 16,909 / 19,882 | 9,904 / 22,855 (-57%) | -9,408 / 16,803 | 30,061 / 14,169 | 19,214 / 14,716 | 17,779 / 18,612 | - |
| London | ALL | 33,980 / 39,466 | 243,665 / 292,848 (-17%) | 153,191 / 248,954 | 253,533 / 39,870 | 256,115 / 33,205 | 281,778 / 37,318 | - |
| NY AM | L3M | 12,813 / 13,763 | 105,984 / 105,834 (+0%) | 97,943 / 99,663 | 105,417 / 12,813 | 105,571 / 13,073 | 106,229 / 12,813 | WIN |
| NY AM | L6M | 30,988 / 29,241 | 236,657 / 227,464 (+4%) | 218,484 / 212,487 | 234,592 / 30,988 | 230,109 / 29,241 | 233,708 / 30,988 | - |
| NY AM | 2026 | 46,512 / 48,039 | 252,354 / 247,374 (+2%) | 221,754 / 222,588 | 252,618 / 45,933 | 248,201 / 49,252 | 251,358 / 45,205 | WIN |
| NY AM | 2025 | 47,943 / 47,331 | 191,601 / 188,320 (+2%) | 161,273 / 165,897 | 179,408 / 51,706 | 200,067 / 42,342 | 183,827 / 50,715 | - |
| NY AM | 2024 | 42,036 / 42,234 | 56,523 / 117,287 (-52%) | 24,223 / 95,697 | 76,226 / 40,647 | 101,398 / 44,016 | 75,148 / 40,007 | - |
| NY AM | 2023 | 34,777 / 33,564 | 48,499 / 77,326 (-37%) | 27,385 / 64,287 | 51,392 / 41,567 | 71,430 / 26,909 | 50,233 / 41,845 | - |
| NY AM | ALL | 61,573 / 56,959 | 548,977 / 630,307 (-13%) | 434,635 / 548,469 | 559,644 / 69,459 | 621,095 / 49,252 | 560,565 / 67,248 | - |
| NY PM | L3M | 4,819 / 5,035 | 39,595 / 48,386 (-18%) | 33,526 / 43,745 | 38,685 / 7,240 | 43,843 / 2,710 | 44,256 / 5,467 | - |
| NY PM | L6M | 4,819 / 5,035 | 87,374 / 95,589 (-9%) | 74,828 / 85,559 | 84,059 / 7,240 | 84,974 / 4,243 | 97,427 / 5,467 | WIN |
| NY PM | 2026 | 20,273 / 17,396 | 80,278 / 99,395 (-19%) | 59,827 / 83,364 | 81,988 / 17,158 | 80,868 / 18,450 | 95,637 / 18,141 | - |
| NY PM | 2025 | 20,677 / 16,106 | 82,435 / 93,627 (-12%) | 59,468 / 77,324 | 76,388 / 22,799 | 87,781 / 14,965 | 80,898 / 19,930 | - |
| NY PM | 2024 | 22,466 / 33,512 | 68,202 / 54,049 (+26%) | 44,861 / 37,678 | 52,653 / 23,555 | 73,581 / 24,893 | 51,406 / 30,840 | WIN |
| NY PM | 2023 | 17,487 / 16,125 | 59,915 / 66,381 (-10%) | 43,714 / 56,147 | 66,204 / 15,065 | 60,037 / 19,616 | 73,009 / 13,191 | - |
| NY PM | ALL | 27,546 / 33,512 | 290,830 / 313,452 (-7%) | 207,870 / 254,513 | 277,234 / 24,500 | 302,267 / 27,347 | 300,950 / 30,840 | WIN |
| All 17 | L3M | 12,849 / 15,710 | 238,574 / 242,350 (-2%) | 213,788 / 223,531 | 220,393 / 9,823 | 241,910 / 19,008 | 237,660 / 11,106 | WIN |
| All 17 | L6M | 29,793 / 22,398 | 495,514 / 476,592 (+4%) | 442,559 / 434,024 | 454,431 / 28,488 | 490,787 / 24,052 | 479,111 / 28,563 | - |
| All 17 | 2026 | 66,180 / 66,273 | 523,056 / 541,724 (-3%) | 435,744 / 473,163 | 518,994 / 48,666 | 532,438 / 58,198 | 528,408 / 60,227 | WIN |
| All 17 | 2025 | 42,715 / 52,373 | 328,468 / 376,379 (-13%) | 236,192 / 314,890 | 332,566 / 45,677 | 335,870 / 54,210 | 364,599 / 44,674 | - |
| All 17 | 2024 | 25,557 / 35,514 | 242,317 / 315,901 (-23%) | 144,227 / 260,022 | 258,700 / 24,877 | 290,759 / 28,459 | 272,629 / 30,328 | - |
| All 17 | 2023 | 37,654 / 24,205 | 108,892 / 178,528 (-39%) | 37,968 / 144,426 | 150,647 / 25,176 | 146,990 / 32,801 | 148,260 / 31,231 | - |
| All 17 | ALL | 69,311 / 66,273 | 1,202,733 / 1,412,532 (-15%) | 854,131 / 1,192,501 | 1,260,909 / 48,666 | 1,306,057 / 58,198 | 1,313,895 / 60,227 | - |

### Table A2 - AS8 on the Test 5 ASIA qualifier cells (sample of 72 cells, hold weeks only, basket 1 lot per cell; bracket = the cell family-median bracket, not tuned on these weeks): AS8 vs the cell own bracket; NUL = random exit at the same fraction; pess
| window | DD AS8 / own | worst week | income AS8 / own | pess income AS8 / own | NUL income / DD | win |
|---|---|---|---|---|---|---|
| L3M | 80,552 / 90,847 | -45,211 / -45,094 | 52,294 / 26,467 (+98%) | 22,578 / 2,174 | 13,118 / 93,390 | WIN |
| L6M | 83,356 / 90,847 | -51,851 / -51,978 | 125,998 / 82,877 (+52%) | 78,041 / 42,111 | 80,568 / 97,410 | WIN |
| 2026 | 83,356 / 90,847 | -51,851 / -51,978 | 105,214 / 77,463 (+36%) | 51,001 / 32,396 | 82,696 / 97,410 | WIN |
| 2025 | 45,191 / 63,569 | -15,824 / -24,915 | 5,051 / -25,185 (+120%) | -16,556 / -35,640 | 5,266 / 43,064 | WIN |
| 2024 | 91,344 / 46,511 | -23,192 / -21,780 | -38,276 / 32,154 (-219%) | -66,139 / 20,458 | -57,633 / 101,029 | - |
| 2023 | 0 / 0 | 0 / 0 | 0 / 0 (n/a) | 0 / 0 | 0 / 0 | - |
| ALL | 125,218 / 100,988 | -51,851 / -51,978 | 71,988 / 84,433 (-15%) | -31,695 / 17,215 | 30,329 / 132,274 | - |

### Table A3 - FAIR: AS8 fixed rule vs the WALK-FORWARD BRACKET (each cell re-picks among the 17 grid brackets by the standing pick rule on data before the date; fallback plain60/60), same Asia cells, chained forward; step 13 / 4 / 2 weeks
| step | periods DD or worst week better | DD AS8 / WF bracket | worst week | income AS8 / WF bracket | L3M DD | L6M DD | L6M income | verdict |
|---|---|---|---|---|---|---|---|---|
| 13 | 5/10 | 125,218 / 184,023 | -51,851 / -67,157 | 71,988 / -23,661 (+404%) | 83,356 / 184,023 | 83,356 / 184,023 | 141,549 / 33,848 | **PASS** |
| 4 | 11/28 | 125,218 / 181,124 | -51,851 / -67,157 | 71,988 / 30,382 (+137%) | 81,304 / 138,417 | 83,356 / 181,124 | 114,639 / 27,849 | **PASS** |
| 2 | 22/47 | 125,218 / 187,981 | -51,851 / -72,337 | 71,988 / 825 (+8623%) | 81,304 / 143,597 | 83,356 / 187,981 | 141,549 / 12,872 | **PASS** |


## EXACT ROWS for the stuck exit (items 1(d), 1(g); W-DYNH sets, scored read-only with code/th_dynexit/dx_score.py functions; exact engine, live lots, 42 months, Nov 2025 excluded)
Sets TL3_DX_AS_{MF1,MF3}_{stk45,stk45h}_{A,M,N} (stk45 = leave at 45 min if best excursion < 0.25R and under water; stk45h = halve instead of leaving). A = the book alone bare vs TL3_DX_AS_<book>_fix_A; M = the live mix with this stream changed (live Trade Health kept) vs the live mix TL3_SR_AS_STKd8da2eb47b_FSff6_PICKC; N = the mix without the book's live Trade Health vs TL3_DX_AS_<book>_fix_N. Columns: max DD $ treated / reference (negative = loss), worst week, income $ treated / reference (change), pessimistic income (Stop exits worse by the DS3_DN_STOPFILL slippage) treated / reference, trades treated / reference.
| book | variant | subject | window | max DD | worst week | income | pessimistic income | trades |
|---|---|---|---|---|---|---|---|---|
| MF1 | stk45 | A | L3M | -75,083 / -72,079 | -48,431 / -31,183 | 50,601 / 101,602 (-50%) | 31,213 / 81,326 | 2916 / 2126 |
| MF1 | stk45 | A | L6M | -75,083 / -72,079 | -48,431 / -31,183 | 330,960 / 388,545 (-15%) | 288,336 / 343,997 | 2916 / 2126 |
| MF1 | stk45 | A | 2026 | -96,779 / -111,441 | -48,431 / -50,206 | 416,197 / 485,022 (-14%) | 355,221 / 420,494 | 2916 / 2126 |
| MF1 | stk45 | A | 2025 | -114,547 / -95,359 | -37,962 / -36,300 | -75 / 159,478 (-100%) | -33,819 / 120,998 | 2916 / 2126 |
| MF1 | stk45 | A | 2024 | -109,094 / -70,156 | -31,297 / -31,498 | 82,998 / 150,376 (-45%) | 67,754 / 127,880 | 2916 / 2126 |
| MF1 | stk45 | A | whole | -120,592 / -111,441 | -48,431 / -50,206 | 520,282 / 876,310 (-41%) | 408,394 / 745,330 | 2916 / 2126 |
| MF1 | stk45 | M | L3M | -36,177 / -36,934 | -19,695 / -19,755 | 122,389 / 147,423 (-17%) | 105,477 / 130,096 | 6748 / 6111 |
| MF1 | stk45 | M | L6M | -39,041 / -37,750 | -19,695 / -19,755 | 422,473 / 441,789 (-4%) | 383,823 / 402,194 | 6748 / 6111 |
| MF1 | stk45 | M | 2026 | -66,003 / -57,585 | -33,549 / -33,859 | 457,306 / 497,006 (-8%) | 400,775 / 438,660 | 6748 / 6111 |
| MF1 | stk45 | M | 2025 | -65,945 / -67,941 | -37,409 / -37,409 | 84,980 / 153,865 (-45%) | 52,247 / 118,462 | 6748 / 6111 |
| MF1 | stk45 | M | 2024 | -83,804 / -64,207 | -31,939 / -27,072 | 153,164 / 164,285 (-7%) | 137,382 / 145,626 | 6748 / 6111 |
| MF1 | stk45 | M | whole | -83,804 / -67,941 | -37,409 / -37,409 | 738,647 / 893,926 (-17%) | 630,917 / 777,271 | 6748 / 6111 |
| MF1 | stk45 | N | L3M | -36,253 / -34,875 | -19,420 / -17,346 | 117,123 / 145,661 (-20%) | 99,930 / 128,152 | 6683 / 6055 |
| MF1 | stk45 | N | L6M | -39,041 / -37,750 | -19,425 / -17,346 | 407,695 / 430,516 (-5%) | 368,347 / 390,321 | 6683 / 6055 |
| MF1 | stk45 | N | 2026 | -50,062 / -49,298 | -24,650 / -24,960 | 479,385 / 513,987 (-7%) | 422,495 / 455,342 | 6683 / 6055 |
| MF1 | stk45 | N | 2025 | -63,182 / -64,706 | -37,409 / -37,409 | 101,525 / 174,201 (-42%) | 68,731 / 138,835 | 6683 / 6055 |
| MF1 | stk45 | N | 2024 | -84,987 / -63,009 | -31,939 / -27,072 | 150,702 / 164,204 (-8%) | 134,919 / 145,544 | 6683 / 6055 |
| MF1 | stk45 | N | whole | -84,987 / -64,706 | -37,409 / -37,409 | 774,808 / 931,161 (-17%) | 666,657 / 814,244 | 6683 / 6055 |
| MF1 | stk45h | A | L3M | -71,369 / -72,079 | -37,403 / -31,183 | 83,632 / 101,602 (-18%) | 63,356 / 81,326 | 2126 / 2126 |
| MF1 | stk45h | A | L6M | -71,369 / -72,079 | -37,403 / -31,183 | 366,185 / 388,545 (-6%) | 321,637 / 343,997 | 2126 / 2126 |
| MF1 | stk45h | A | 2026 | -105,586 / -111,441 | -48,841 / -50,206 | 451,477 / 485,022 (-7%) | 386,949 / 420,494 | 2126 / 2126 |
| MF1 | stk45h | A | 2025 | -99,109 / -95,359 | -36,125 / -36,300 | 100,703 / 159,478 (-37%) | 62,223 / 120,998 | 2126 / 2126 |
| MF1 | stk45h | A | 2024 | -78,511 / -70,156 | -27,491 / -31,498 | 124,576 / 150,376 (-17%) | 102,080 / 127,880 | 2126 / 2126 |
| MF1 | stk45h | A | whole | -105,586 / -111,441 | -48,841 / -50,206 | 736,495 / 876,310 (-16%) | 605,515 / 745,330 | 2126 / 2126 |
| MF1 | stk45h | M | L3M | -35,444 / -36,934 | -19,995 / -19,755 | 146,343 / 147,423 (-1%) | 129,016 / 130,096 | 6111 / 6111 |
| MF1 | stk45h | M | L6M | -38,355 / -37,750 | -19,995 / -19,755 | 441,584 / 441,789 (-0%) | 401,989 / 402,194 | 6111 / 6111 |
| MF1 | stk45h | M | 2026 | -58,755 / -57,585 | -33,754 / -33,859 | 489,491 / 497,006 (-2%) | 431,145 / 438,660 | 6111 / 6111 |
| MF1 | stk45h | M | 2025 | -65,571 / -67,941 | -37,409 / -37,409 | 143,015 / 153,865 (-7%) | 107,612 / 118,462 | 6111 / 6111 |
| MF1 | stk45h | M | 2024 | -64,695 / -64,207 | -28,582 / -27,072 | 151,480 / 164,285 (-8%) | 132,821 / 145,626 | 6111 / 6111 |
| MF1 | stk45h | M | whole | -65,571 / -67,941 | -37,409 / -37,409 | 852,696 / 893,926 (-5%) | 736,041 / 777,271 | 6111 / 6111 |
| MF1 | stk45h | N | L3M | -33,860 / -34,875 | -18,061 / -17,346 | 143,646 / 145,661 (-1%) | 126,137 / 128,152 | 6055 / 6055 |
| MF1 | stk45h | N | L6M | -38,355 / -37,750 | -18,061 / -17,346 | 429,376 / 430,516 (-0%) | 389,181 / 390,321 | 6055 / 6055 |
| MF1 | stk45h | N | 2026 | -49,503 / -49,298 | -24,855 / -24,960 | 505,977 / 513,987 (-2%) | 447,332 / 455,342 | 6055 / 6055 |
| MF1 | stk45h | N | 2025 | -59,981 / -64,706 | -37,409 / -37,409 | 163,186 / 174,201 (-6%) | 127,820 / 138,835 | 6055 / 6055 |
| MF1 | stk45h | N | 2024 | -64,601 / -63,009 | -28,582 / -27,072 | 150,294 / 164,204 (-8%) | 131,634 / 145,544 | 6055 / 6055 |
| MF1 | stk45h | N | whole | -64,601 / -64,706 | -37,409 / -37,409 | 888,166 / 931,161 (-5%) | 771,249 / 814,244 | 6055 / 6055 |
| MF3 | stk45 | A | L3M | -47,552 / -43,634 | -19,019 / -21,151 | 112,092 / 120,042 (-7%) | 94,332 / 100,654 | 2946 / 2463 |
| MF3 | stk45 | A | L6M | -47,552 / -45,501 | -23,487 / -23,487 | 250,193 / 226,478 (+10%) | 206,237 / 179,710 | 2946 / 2463 |
| MF3 | stk45 | A | 2026 | -68,512 / -68,293 | -39,878 / -39,659 | 328,177 / 391,768 (-16%) | 264,981 / 324,576 | 2946 / 2463 |
| MF3 | stk45 | A | 2025 | -74,238 / -103,232 | -35,770 / -36,171 | 52,594 / 73,736 (-29%) | 23,438 / 36,884 | 2946 / 2463 |
| MF3 | stk45 | A | 2024 | -139,484 / -96,470 | -27,386 / -27,154 | -85,346 / 107,462 (-179%) | -97,778 / 89,702 | 2946 / 2463 |
| MF3 | stk45 | A | whole | -151,331 / -103,232 | -39,878 / -39,659 | 279,589 / 628,275 (-55%) | 173,177 / 502,475 | 2946 / 2463 |
| MF3 | stk45 | M | L3M | -33,769 / -36,934 | -15,505 / -19,755 | 147,423 / 147,423 (+0%) | 131,298 / 130,096 | 6348 / 6111 |
| MF3 | stk45 | M | L6M | -33,769 / -37,750 | -15,505 / -19,755 | 456,360 / 441,789 (+3%) | 418,689 / 402,194 | 6348 / 6111 |
| MF3 | stk45 | M | 2026 | -51,545 / -57,585 | -32,858 / -33,859 | 487,210 / 497,006 (-2%) | 432,083 / 438,660 | 6348 / 6111 |
| MF3 | stk45 | M | 2025 | -74,943 / -67,941 | -39,258 / -37,409 | 113,038 / 153,865 (-27%) | 82,412 / 118,462 | 6348 / 6111 |
| MF3 | stk45 | M | 2024 | -70,039 / -64,207 | -27,516 / -27,072 | 131,371 / 164,285 (-20%) | 116,982 / 145,626 | 6348 / 6111 |
| MF3 | stk45 | M | whole | -74,943 / -67,941 | -39,258 / -37,409 | 787,065 / 893,926 (-12%) | 683,913 / 777,271 | 6348 / 6111 |
| MF3 | stk45 | N | L3M | -37,391 / -41,912 | -8,971 / -13,221 | 186,326 / 200,020 (-7%) | 169,060 / 182,215 | 5825 / 5577 |
| MF3 | stk45 | N | L6M | -49,396 / -49,396 | -34,115 / -34,115 | 445,267 / 439,110 (+1%) | 404,437 / 397,079 | 5825 / 5577 |
| MF3 | stk45 | N | 2026 | -69,871 / -70,207 | -34,115 / -34,115 | 534,302 / 550,762 (-3%) | 475,450 / 489,804 | 5825 / 5577 |
| MF3 | stk45 | N | 2025 | -52,626 / -50,997 | -35,232 / -33,383 | 155,127 / 183,105 (-15%) | 123,946 / 148,252 | 5825 / 5577 |
| MF3 | stk45 | N | 2024 | -80,071 / -88,096 | -27,801 / -30,643 | 175,087 / 206,318 (-15%) | 159,978 / 187,267 | 5825 / 5577 |
| MF3 | stk45 | N | whole | -80,071 / -88,096 | -35,232 / -34,115 | 932,096 / 1,026,334 (-9%) | 824,006 / 907,348 | 5825 / 5577 |
| MF3 | stk45h | A | L3M | -39,729 / -43,634 | -20,031 / -21,151 | 120,597 / 120,042 (+0%) | 101,209 / 100,654 | 2463 / 2463 |
| MF3 | stk45h | A | L6M | -45,709 / -45,501 | -23,487 / -23,487 | 227,808 / 226,478 (+1%) | 181,040 / 179,710 | 2463 / 2463 |
| MF3 | stk45h | A | 2026 | -71,063 / -68,293 | -42,429 / -39,659 | 368,973 / 391,768 (-6%) | 301,781 / 324,576 | 2463 / 2463 |
| MF3 | stk45h | A | 2025 | -85,392 / -103,232 | -36,201 / -36,171 | 65,586 / 73,736 (-11%) | 28,734 / 36,884 | 2463 / 2463 |
| MF3 | stk45h | A | 2024 | -97,863 / -96,470 | -24,514 / -27,154 | 51,037 / 107,462 (-53%) | 33,277 / 89,702 | 2463 / 2463 |
| MF3 | stk45h | A | whole | -97,863 / -103,232 | -42,429 / -39,659 | 519,575 / 628,275 (-17%) | 393,775 / 502,475 | 2463 / 2463 |
| MF3 | stk45h | M | L3M | -35,549 / -36,934 | -17,625 / -19,755 | 143,658 / 147,423 (-3%) | 126,331 / 130,096 | 6105 / 6111 |
| MF3 | stk45h | M | L6M | -35,549 / -37,750 | -17,625 / -19,755 | 443,769 / 441,789 (+0%) | 404,174 / 402,194 | 6105 / 6111 |
| MF3 | stk45h | M | 2026 | -56,085 / -57,585 | -33,164 / -33,859 | 488,718 / 497,006 (-2%) | 430,223 / 438,660 | 6105 / 6111 |
| MF3 | stk45h | M | 2025 | -80,441 / -67,941 | -37,524 / -37,409 | 128,271 / 153,865 (-17%) | 93,137 / 118,462 | 6105 / 6111 |
| MF3 | stk45h | M | 2024 | -62,982 / -64,207 | -26,022 / -27,072 | 152,875 / 164,285 (-7%) | 134,216 / 145,626 | 6105 / 6111 |
| MF3 | stk45h | M | whole | -80,441 / -67,941 | -37,524 / -37,409 | 836,863 / 893,926 (-6%) | 720,329 / 777,271 | 6105 / 6111 |
| MF3 | stk45h | N | L3M | -39,182 / -41,912 | -11,091 / -13,221 | 189,220 / 200,020 (-5%) | 171,415 / 182,215 | 5580 / 5577 |
| MF3 | stk45h | N | L6M | -49,396 / -49,396 | -34,115 / -34,115 | 432,100 / 439,110 (-2%) | 390,069 / 397,079 | 5580 / 5577 |
| MF3 | stk45h | N | 2026 | -70,477 / -70,207 | -34,140 / -34,115 | 528,433 / 550,762 (-4%) | 467,328 / 489,804 | 5580 / 5577 |
| MF3 | stk45h | N | 2025 | -55,476 / -50,997 | -33,078 / -33,383 | 165,995 / 183,105 (-9%) | 131,142 / 148,252 | 5580 / 5577 |
| MF3 | stk45h | N | 2024 | -86,791 / -88,096 | -30,018 / -30,643 | 186,128 / 206,318 (-10%) | 167,077 / 187,267 | 5580 / 5577 |
| MF3 | stk45h | N | whole | -86,791 / -88,096 | -34,140 / -34,115 | 959,410 / 1,026,334 (-7%) | 840,276 / 907,348 | 5580 / 5577 |

**Reading (exact):** (1) the stuck exit costs income in the exact engine: alone MF1 whole -41% (halve -16%), MF3 -55% (halve -17%); inside the live mix with Trade Health MF1 -17% (halve -5%), MF3 -12% (halve -6%); max DD is deeper than the reference in the mix (stk45 MF1 -$83.8k vs -$67.9k, MF3 -$74.9k vs -$67.9k; halve about equal, MF3 halve -$80.4k vs -$67.9k deeper). Recent windows are mild: MF3 in the mix L6M +3% income with DD -$33.8k vs -$37.8k (shallower) and L3M DD -$33.8k vs -$36.9k; MF1 L6M -4%. (2) Trade Health neither duplicates nor fights the stuck exit visibly: the effect of the rule is almost the same with TH on (M) and with TH off (N) (MF1 whole -17% both; MF3 -12% vs -9%). (3) Halving is better than leaving everywhere (income loss 3x smaller, DD no worse), but it still does not beat the reference. **Exact vs quick screen:** same direction and ranking, exact is worse alone: quick screen Asia (3 books, 1 lot, 45/0.25R) whole -24%, DD flat; exact alone -41% / -55% with DD 8% / 47% deeper; quick all-17 whole -14% vs exact mix -12% to -17%: the quick screen understates the cost of the exit on the bare book by about 15-30 income points and agrees on the mix; quick L6M (+4% all-17, +4% Asia) vs exact mix L6M (-4% / +3%) agree. Pessimistic fills lower both sides by the same amount in the exact rows (about -$100k to -$130k whole): they do not change the verdict.
