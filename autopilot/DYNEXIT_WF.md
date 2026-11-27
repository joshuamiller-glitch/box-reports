# DYNEXIT_WF - dynamic stops and targets on the live books, walked forward (W-DYNQ, orders 0301Z / 0303Z X9 / 0340Z intra-trade / 0343Z fixed rule rows)
**QUICK SCREEN label on every number** (grid tape walk, gexit/sim_path kernel, 1 NQ base lot at $20/pt, grid fill + slippage + $4.84 RT cost in, one position per recipe at a time, the book's own session and side only, no stack rules, no account layers, NO Trade Health on either side, no pessimistic stop-fill applied: label only). Subjects: **17 of the 20 live books** (3 have no grid cell and are not guessed: Asia L385f4f2e_CX502, NY AM B7bfd33b7, NY AM Bf428c4a1.BRS8U) and a random sample of the Test 5 primary qualifier cells. Weekly P&L arrays, 186 weeks 2023-04-03..2026-10-30, the four Nov-2025 weeks excluded. Dollars = points x $20 per base lot. Code: code/th_dynq (dq_run.py kernel runner, dq_dynk.py intra-trade kernel, dq_levels.py, dq_wf.py, dq_fixed.py, dq_wf_t5.py). Raw per-book arrays: /mnt/l2/l2vast/_dynq/live3 (server C).

## ANSWER FIRST
**Headline: no dynamic exit beats the fixed bracket walking forward, drawdown first, on the live books (quick screen). The books' own fixed brackets are the best exits in this data set, and a re-picked fixed bracket (Test 3 part B) is the only reference that comes close on income. Nothing is a candidate; nothing goes to the forward register as an exit.**
1. **Primary walk-forward (pool = all 287 recipes, the existing exit pick rule, re-picked every 13 / 4 / 2 weeks, judged on the next period against the book's own fixed bracket), all 17 books summed, chained out-of-sample:** 13-week re-pick: forward max DD $60.9k vs $66.3k (8% shallower) but income $0.83M vs $1.32M (-37%): FAIL (needs income within -10%). 4-week: DD $113.7k vs $66.3k, income -52%: FAIL. 2-week (Josh's rhythm): DD $105.4k vs $66.3k (+59%), income -57%: FAIL. Faster re-picking is WORSE, not better: the pick rule (lowest ulcer first) chases the recent quiet recipe, which then earns little. By session and step see Table 1; L3M / L6M in Table 2. Recent windows are the only place a dynamic pick looks good: 2-week re-pick, all-17: L3M chained DD $14.6k vs $22.4k and worst week -$11.9k vs -$22.4k (both shallower) at income -28%, but L6M DD $27.4k vs $22.4k (deeper) and the whole 3 years say income -57%; London 2-week is the closest line (L3M DD $2.1k vs $6.0k, L6M $4.9k vs $10.1k, income -14% / -16%, but whole-period income -55%). That is a feature of the last 3-6 months, not of the 3 years, and the 13-week re-pick has the opposite sign in L3M (DD $32.3k vs $22.4k). Not a candidate.
2. **Family by family, live books only, forward (Table 3, each family alone with only its parameter re-picked):** lowers drawdown most: at 13 weeks X2 structure stops (-10% chained DD, income -10%), at 2 weeks X6 no-progress / time (-8% DD, income -6%); raises income most: the best FIXED bracket re-picked (REFPOOL, +1% income at 2 weeks, but chained DD +73%), then X5 staged (-1% income, DD +13%). No family passes (needs DD shallower or worst week better in 2/3 of periods with income within -10%, or higher income with DD not deeper): the closest are X2 (13w) and X6 (2w), both short of 2/3 of periods (7 of 12 and 26 of 44). Which families are real vs screen noise (Table 5): the picked families lose forward points vs the fixed bracket in every family (X3 and X5 at 13 weeks only marginally: -94 and -193 pts); X9 level recipes are picked most (the screen loves them: they are 80 of 287 recipes) and lose the most (-6,877 pts at 13 weeks, -13,110 at 2 weeks).
3. **Fixed rule rows (order 0343Z; defaults written down before scoring, free settings 1-3 each, Table 9 / 10): no family is a candidate.** Straight through all months vs the books' own brackets, every family loses L6M and L3M (L6M income -74% to -157%, DD 2-12x deeper) and wins at most 1 of 6 windows (X2 in 2024 only). Re-fitting adds nothing because the fixed rule is far below the fixed bracket to start with; walk-forward picks (item 1) are better than the fixed rules (income -37% vs -75..-108%) and still fail.
4. **Intra-trade re-computation (order 0340Z): updating inside the trade does not help.** Level stops/targets recomputed at every bar close (X9D) vs set once at entry (X9): chained DD as a fixed rule $271k vs $169k (fixed bracket $22k), walk-forward income -24% vs -27% (about the same); range-left target (X3D vs X3): DD +0% vs +6% and income -7% vs -12% at 13 weeks (X3D is the best-behaved family at 13 weeks, still FAIL; 16-17 order changes per trade without hysteresis). Order changes per trade: level recipes 1.2-6.8 (T1 3.1, T2 6.8, S4 1.2, T1S4 2.7; hysteresis 4 ticks 1.05, min 30 s 1.7). Identity check: updating switched off == the static row trade for trade (True, tested on prior-day-level T1S4 on every book run). Widening up to 1.0 / 1.5 x original risk (named cases not applicable here: levels have no 'protecting size'): no better than tighten-only.
5. **X9 level hit table (Table 6):** price is NOT attracted to any of the 13 level types: the fraction of entries whose nearest level ahead is touched by session end equals the same-distance shuffled-level null to the second decimal for every type (e.g. prior-day H/L/C 0.290 vs 0.297, VWAP and bands 0.690 vs 0.694, volume-profile nodes 0.439 vs 0.441, pivots 0.311 vs 0.319, round numbers 0.577 vs 0.581); after a touch the 5-point through / reject split is also at the null (0.42-0.47 through vs 0.42-0.46). Levels are not walls here; as stops they are just close. UW gamma levels (from 2024-10): touched on 2.5% of entries (too far to act as targets).
6. **Random-entry null (Tables 7 and 11, 2 random draws, same count and side mix per session instance):** the fixed rules on random entries are about level with the books' fixed brackets (L6M income difference -$124k to +$50k; X1 +$23k, X3 +$35k, X3D +$37k, X4 +$50k, X5 +$8k; X2 -$73k, X6 -$23k, X7 -$16k, X9 -$58k, X9D -$124k) and on the real, hindsight-tuned entries they lose -$355k to -$748k. So no exit 'harvests drift' (that would gain on the real entries too): the live books' brackets were tuned jointly with their entries on these very weeks, and no generic exit beats a hindsight-tuned bracket. This is the ceiling of this test: **the live books are not a fair arena for an exit that has to be found without hindsight**; the Test 5 baskets are (item 7).
7. **S2: Test 5 primary qualifier baskets (non-hindsight entries), RANDOM SAMPLE of cells: 127 Asia (7.7% of 1,641) and 82 NY AM (4.3% of 1,900); London / NY PM too thin to report** (the box was saturated: 1,048 nice-0 processes on C, my niced procs got 1-4 cores). Tables 8 and 8b. (a) Walk-forward, pool = all recipes: Asia 13-week PASS (DD $245k vs $253k, 9/12 periods, income -4%), Asia 2-week and 4-week FAIL (income -2% / -28%); NY AM 2-week and 4-week PASS (45/65 and 32/38 periods; both baskets LOSE about $350k, the pick loses $10k less; chained DD $417k vs $421k, $449k vs $421k) and 13-week FAIL (income -24%): pass / fail flips with the step and the session; 6 of 6 sample tests for the primary pool gives 3 PASS, at the loose second leg; treat as noise. (b) FIXED rules (pre-written, no search), Asia sample: recent windows win clearly (L6M income / DD: X4 chandelier $691k / $111k vs own $131k / $253k; X1 $506k / $112k; X6 $486k / $105k; X5 $383k / $88k; X3 $318k / $110k; L3M won by X1, X4, X5, X6) but years do not (2023: X2, X3, X5, X7 win by under $11k; 2024: X4 and X7; 2025: no rule wins): a 2026-only, high-volatility-regime effect (own point brackets earned $72k in 2026 on the sample vs $320-703k for the vol-scaled rules) and the live books show the opposite sign. NY AM sample: X3 (range-left target) wins 5 of 6 windows but the basket is negative in 3 of 4 years (loses less: L6M +$24k vs -$161k; 2026 -$66k vs -$284k). **Not met: 'wins in most years AND both recent windows AND beats the random-exit null' for any rule** (random-exit null for the Asia sample: Table 12). Sample baskets are clustered (many cells from the same trigger families), so the effective n is small.
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
