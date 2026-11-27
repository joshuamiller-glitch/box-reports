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
