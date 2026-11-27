# PLAN_LO: exit plans for the 3 London live books (W-PLAN-LO), round 1, 27 Nov 2026 ~04:25Z

## Answer first
- NO plan passes the SOLUTION clause for any London book in round 1. London's exits cannot be fixed by exits alone on what has been tried: fixed bracket stays the reference row, and the books stay on the list.
- Attribution: 0 of 42 (signal, side) tests carry information on the London holdout (BH q min 0.21): flow, OFI, sweeps, big prints, book imbalance (L1 and 10-level), wall ahead / room ahead, speed, momentum, absorption, spread. So there are NO "leave-now" triggers to put in a London plan. Same verdict as Asia/NY (0 YES of 25).
- One partial lead, MF2 (L12842dde, imbalance follow, 45/45, 4 lots live): a breakeven-style trail (once +0.5 x target = +22.5 pt is reached, stop trails 22.5 pt behind the best price; target 45 unchanged). Fixed rule, whole sample: max DD -75k vs -179k (REF), income 161k vs 164k; by year DD shallower 2023, 2025, 2026, deeper 2024 (-58k vs -53k). The neighbourhood (act 0.33-0.67 x T, dist 0.33-1.0 x T) cuts DD 20-60% everywhere. BUT: pessimistic stop-fill label income falls to -23k vs +41k for REF (trail stop fills cost 1.5 pt on a 45 pt bracket), and walk-forward picking over the full grid fails the income clause (fwd income 4k-40k vs 160k, shallower DD in 9-10 of 13 blocks). So: CANDIDATE for the drawdown side only, NOT a solution.
- MF1 (L19201dfc, 90 stop / 30 target, 8 lots) and MF3 (L74274eca, 120/60, 2 lots): nothing beats the bracket. The book's 30 / 60 pt target and the 08:30 ET flat are what earns; every change tried (tighter stop, partials, trails, no-progress, earlier flat) lowers income, usually with no DD gain (MF3 no-progress 40 min: DD -42k vs -49k, income -9%, L6M better; weak).
- London live mix itself in this harness (bare set TL3_SR_LO_STKd8w42lo_FSffb8_BARE, engine trades Apr 2023 - 12 Oct 2026, 5,918 of 6,093 trades with tape): engine +946k net, max DD -217k, worst week -106k at the set's lots; the directive's "~22k DD" is not this lot level (lots in the set: MF1 8, MF2 4, MF3 2 typical). 1-lot: sim +202k, DD -51k.

## Method (what was built)
Store: 6,093 live-set trades, dense 1-s paths with 10-level book and flow columns from tables/NQ/1s (code/th_plan_lo/build.py, /mnt/l2/l2vast/_plan_lo/). Simulator sim.py (stop first inside a second, trail applies next second, partial legs, BE, no-progress, max hold, trigger and steering-score hooks). Identity vs engine: income sim 906k vs engine 946k (-4%); L3M -12%; targets match 96% within 1 pt, stops 60% (engine stop slip) so the base stop slip is 0.4 pt. Every comparison is sim vs sim (same harness). Pessimistic label: stop slip 1.5 pt, target needs 1 tick through.
Defaults written before scoring: /mnt/l2/l2vast/_dynexit/fixed_rules_plan_lo.json.

## The plans (stated as asked)
### MF2 L12842dde (candidate, drawdown side)
1. Initial stop: 45 pt (book bracket, unchanged; no structure stop tested better).
2. Moves: at +22.5 pt favourable the stop starts trailing 22.5 pt behind the best price (chandelier, tick-wise from the next second); so at +22.5 it sits at breakeven. No other tighten triggers (none carry information).
3. Targets: one, +45 pt, 100% off (live 4 lots all at target; 1 lot the same, no partial). No runner.
4. Leave-now triggers: none (attribution found none on either side).
5. Time: flat 08:30 ET (book's own), no other time rule.
Free settings: 2 (act, dist), fixed at 0.5 x T each (picked from the grid; neighbours all similar).
### MF1 L19201dfc and MF3 L74274eca: plan = the book bracket (stop 90 / target 30; stop 120 / target 60, flat 08:30 ET), no trail, no partial, no leave-now trigger, no extra time rule. This is the reference, stated as the plan because nothing tested beats it. Not a verdict: both stay on the list.

## Fixed-rule rows (live lots, sim; drawdown first). inc / max DD / worst week; ALL, L6M, L3M
| plan | ALL | L6M | L3M |
|---|---|---|---|
| REF fixed bracket | 906k / -230k / -115k | 456k / -41k / -23k | 160k / -41k / -22k |
| PA bank-and-run (half at T0, BE, runner 3 T0 + trail) | 761k / -238k / -118k | 426k / -40k / -29k | 146k / -40k / -21k |
| PB tight stop 0.5 S0 | 443k / -190k / -61k | 95k / -72k / -28k | 45k / -68k / -28k |
| PC no-progress 20 min, hold 2 h | 361k / -268k / -109k | 367k / -46k / -27k | 139k / -37k / -13k |
| PD target 2 T0 + trail | 275k / -207k / -81k | 209k / -54k / -26k | 70k / -49k / -26k |
| PE 3-leg scale | 338k / -201k / -88k | 170k / -47k / -23k | 35k / -47k / -23k |
Pessimistic label: REF 718k / -253k; PA 491k / -271k; the others lower. PB cuts worst week by half (-61k) at -51% income (income-clause fail). Per book at 1 lot: REF 202k / -51k.
Per-book fixed rule MF2 trail (above): live lots ALL 161k / -75k vs REF 164k / -179k; L6M 82k vs 102k; L3M 26k vs 38k; 1 lot: 2025 DD -18.9k vs -44.7k, 2026 -8.3k vs -17.1k.

## Walk-forward (130 variants x 3 books, expanding window from week 26, re-pick 2 / 4 / 13 weeks, 13-week forward blocks)
Drawdown-first pick with income floor 90% of REF in training: mix fwd income 176-298k vs REF 866k (fails the income clause), shallower DD in 7 of 13 blocks. Per book: MF2 shallower DD and better worst week in 9-10 of 13 blocks at every step but income 4k-41k vs 160k; MF1 and MF3 shallower DD in only 2-6 of 13. Verdict: re-fitting adds nothing here; the fixed trail on MF2 is better than any walk-forward pick.

## Counts
Variants tried this round: 130 grid recipes (each on 3 books, live / pessimistic / 1 lot), 5 fixed plans, 42 attribution tests (21 signals x 2 sides), 32 MF2 trail sensitivity rows, 24 walk-forward configurations: ~230 distinct settings. Luck: the MF2 trail is the best of ~130 recipes for MF2 on the whole sample; its robustness rests on the neighbourhood and 3 of 4 years, not on a null. NOT done in round 1: random-exit null, non-hindsight entries, exact-engine rows, family-sharing test, steering (X24).
## Data note for the LEAD TO JOSH line
Everything above uses only 10-level book + trade flow from the 1-s tables (what NT8 has). Nothing needed MBO. The full-MBO versus 10-level comparison for London has NOT been run (W-DYNX8's extractor covers Asia/NY entries only); no London plan needs a live MBO feed because no book-based part carried information at 10 levels.
## X24 hook
sim.py takes a per-second integer score array (sc) with thresholds sc_hi / sc_lo, trail loosen / tighten multipliers and a pull-in action (implemented); target-extension is stubbed (not implemented). The controller of W-DYNC plugs in by supplying sc per trade; a static row (sc = 0) runs beside it.
## Next (so the book is not dropped)
(1) random-exit null and exact-engine rows for the MF2 trail (queue_rows via dx_multi stg/chand recipe, MF2 A and M, ~42 months); (2) MF1: test structure stops behind the London range / sessions and the asymmetry (30 target vs 90 stop: 3:1) with a size-by-early-result rule; (3) MF3 no-progress 40 min with the non-hindsight sample; (4) London-open-window and day-type conditioned plans; (5) MBO cluster ahead of target for MF1 target extension once the London entries are given to W-DYNX8's extractor.

# ROUND 2 (quick screen on the London store; ~04:50Z). Output /mnt/l2/l2vast/_plan_lo/r2.out, code/th_plan_lo/r2.py
## Answer first
- MF2 trail passes the random-exit null: same share of changed trades (36.8%) exited at a random second, 300 draws: null max DD mean -133k (best -57k), only 1% of draws as shallow as the trail's -75k; null income 149k vs trail 161k. So the DD gain is the trail, not fewer/earlier trades.
- Pessimistic-fill-robust MF2 variant FOUND: wider initial stop with the same trail. Stop 1.5 x 45 = 67.5 pt, trail starts +22.5, 22.5 behind, target 45: income 257k (REF 164k), DD -79k (REF -179k); PESSIMISTIC income +91k, DD -106k (REF pess +33k / -228k). Stop 1.2 x (54 pt): 222k / -73k; pess +47k / -113k. (27 trail/stop settings tried; the 22.5/22.5 cell is best in every stop width; act 15 or 30 is clearly worse, so the grid has a real peak but is selected.) Equal-income frontier (income >= 95% REF): DD -73k to -94k vs -179k.
- MIX swap of MF2 only (MF1, MF3 = bracket), live lots, whole sample: stop 45: 903k / DD -161k / worst wk -94k vs REF 906k / -230k / -115k; stop 67.5: 999k / -189k / -91k. PESS: 662k / -178k vs 718k / -253k (stop 45); 777k / -207k (stop 67.5). By year: 2025 (REF DD -230k, income 89k) becomes 127k / -161k (stop 45) or 216k / -189k (67.5); 2023-24 and 2026 about unchanged. L6M and L3M are NOT better: L6M income 436k vs 456k, DD -46k vs -41k; L3M 148k vs 160k. So the gain is the 2025 bad stretch, no gain in the recent windows. 1 lot mix (stop 67.5): 225k / -41k vs REF 202k / -51k.
- Equal-income frontier walk-forward (target kept, last-26-week training window, pick = min DD with income >= 90% of own bracket, re-pick 13/4/2, 300/100 random-pick null): FAILS for all books and the mix. MF2 fwd income -64k to +17k vs 160k; MF1 fwd income 117-192k vs 529k; MF3 121-143k vs 177k with DD shallower in 6-10 of 13 blocks but not different from the random-pick null (P 0.14-0.44); mix 255-309k vs 866k. The wide family overfits; re-picking adds nothing. Fixed rule beats walk-forward.
- Structure stop (behind the 15-min pre-entry extreme +2 pt, capped at 0.5/0.75/1.0 x book stop, target kept): MF1 cap 1.0: income 480k vs 559k (-14%), DD -84k vs -108k, L6M 241k vs 312k: not equal income. MF2 and MF3: much worse. No pass.
- Early half-cut (size-by-early-result, half the lots off at market after N s if open <= -x S0, the rest to the book exit; needs >= 2 lots): MF1 300 s / -0.25 S0: income 557k vs 559k, DD -97k vs -108k (-10%), L6M 299k vs 312k, L3M 84k vs 93k = weak lead, not clean. MF3 900 s / -0.25: income +2.4%, DD -46.7k vs -48.6k (-4%): negligible. MF2: no gain.
## Plan now stated for MF2 (candidate, 2 free settings plus stop width)
Stop 67.5 pt (1.5 x book stop; risk per trade grows 50%, so at fixed lots the dollar risk rises; 1.2 x = 54 pt is the milder version), trail from +22.5 pt at 22.5 pt behind, target +45, all lots, flat 08:30 ET, no triggers. Verdict: candidate on the drawdown side that survives the null and the pessimistic label, but NOT a solution: the recent windows (L6M, L3M) do not improve, one bad year carries it, not run on non-hindsight entries (item 4 not done) and exact rows not queued (disk freeze). 
## Counts round 2
27 MF2 stop/trail cells x 2 labels, 1 null (300 draws), 24 equal-income WF configs (+ null), 18 structure-stop runs, 12 early-cut runs, 8 mix swaps: ~150 more settings; running total ~380.
## Not done
Non-hindsight entries (Test 5 London qualifiers), X24 controller (code/th_dync not posted yet), exact rows (disk rule).

# ROUND 3 (~05:20Z). Output /mnt/l2/l2vast/_plan_lo/r3.out r3b.out r3c.out; code/th_plan_lo/r3.py r3b.py r3c.py
## Answer first
1. FIT/HOLD (fit = my week index 0-108, hold = 109 on; cell picked on the fit part only, equal-income frontier: income >= 95% of REF in fit, min DD; 9 cells per stop width). Picks 22.5/22.5 at stop 45 and 54 (and 22.5/15 at 67.5). HOLD vs own bracket (REF hold 171k / DD -68k; pess 104k / -75k):
 - stop 45: hold 120k / -33k (income -30%); pess 28k / -47k. Fails the income clause.
 - stop 54: hold 176k / -36k (income +3%, DD -47%); pess 88k / -41k (income -15%, DD -45%). Passes non-pess, pessimistic income short by 5 points.
 - stop 67.5 (22.5/15): hold 124k / -35k; pess 30k / -54k.
 By year (stop 54): 2023 38k/-50k vs 43k/-50k; 2024 14k/-65k vs 47k/-53k (worse); 2025 25k/-73k vs -49k/-179k; 2026 146k/-36k vs 123k/-68k. L6M 69k/-36k vs 102k/-40k; L3M 14k/-22k vs 38k/-29k. So the plain trail does NOT improve the recent windows' income: it removes drawdown in 2025 and 2026 and costs income in 2024 and the last 6 months.
2. WHAT IT MEANS (day-type split, stop 45 trail minus REF, $ at live lots, whole sample, ex-post labels): high-range days +250k, mid -94k, low-range -160k; chop (low path efficiency) days +208k, trend days -224k. The trail earns on reversal / chop days and loses on trend days (trail stops out a winner that would have run to the 45 target or the +22.5 pullback). By year it is 2025 +38k, other years negative. So it is a regime effect: protection when the book's follow signal reverses, a cost when it trends. Pre-entry 15-min range tercile (known at entry): high-pre gain +19k in fit and +35k in hold (same sign both halves), low/mid-pre: ~0 in fit, -49k / -37k in hold.
3. DAY-TYPE GATE (causal): trail only when the pre-entry 15-min range >= the 67th percentile of the book's PAST trades' pre-range, else the plain bracket. Result (trail on 51% of trades): ALL 288k / DD -86k vs REF 164k / -179k; HOLD 242k / -44k vs 171k / -68k; L6M 140k / -28k vs 102k / -40k; L3M 39k / -22k vs 38k / -29k. Pessimistic: ALL 131k / -123k vs 33k / -228k; HOLD 164k / -54k vs 104k / -75k; L6M 112k / -30k vs 81k / -42k; L3M 27k / -23k vs 30k / -31k. Stop 54 version: ALL 307k / -90k; HOLD 255k / -39k; L6M 126k / -28k; L3M 30k / -22k; pess ALL 153k / -126k. This is the first London rule that improves income AND drawdown AND both recent windows (L3M income a wash) AND holds on the pessimistic label. CAVEAT: the idea of the gate came from the all-sample tercile table (hindsight on the choice of "pre-range", p67 is my a-priori third); threshold itself uses only past trades; 4 gated variants tried. CANDIDATE, needs the exact engine and the non-hindsight sample before it is called a solution.
4. GENERALISATION (same trail, activation and distance 0.5 x target, or 0.5 x stop, target kept, Asia 4 books and NY AM 9 books, W-DYNA path store 5-s grid, paths end at the live exit so TH cuts are inside both rows; fixed rule, all months): the trail HURTS. Asia mix REF 862k / -71k vs trail 714k / -85k; NY AM REF 3.18M / -212k vs trail 1.71M / -295k; per book DD better only for NY MF1 (-100k vs -110k), NY MF3, NY MF5 and income lower in all 13 books. Pessimistic worse still. So the trail is NOT a general plan: it is specific to MF2 (imbalance-follow, 45/45, long only). Say the same to W-PLAN-AS/NY/NP.
5. EXACT ROWS (not queued, disk freeze): MF2 survivors = stop 45 / 54 / 67.5 with the 22.5/22.5 trail, mix M and book-alone A, 42 months each = 3 x 2 x 42 = 252 rows (+ the gated version needs a per-entry gate flag from my store: events file with stop/trail by entry, 2 widths x 2 x 42 = 168 rows). Recipe = dx_multi chand/stage with act 22.5, dist 22.5. Total 420 rows when released.
6. Test 5 London qualifier entries (non-hindsight): NOT done. The qualifiers need the signal builder (dq_run with the gexit kernel) to create entries and 1-s paths; it is 1 to 2 hours of building; next in queue. X24: code/th_dync not posted yet.
## Count round 3
9 stop x trail cells x 2 labels fit/hold, 4 day-type splits, 4 gated variants x 2 labels, 3 x 13 books x 2 labels generalisation: ~150 more settings; running total ~530.
