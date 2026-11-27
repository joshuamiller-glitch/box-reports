# PLAN_NP: real-time exit PLAN for the 4 live NY PM books + NP-MACD + NP-CONF (W-PLAN-NP, round 1, 27 Nov ~04:15Z). Research only.

## ANSWER FIRST
- No plan passes the SOLUTION clause yet, on any NY PM book or on the 4-book mix. Every book stays on the list. Round 1 = quick screen on the 1-s NQ tape (ends 2026-10-09), books alone and as a sum at equal lots, not the exact engine.
- Leave-now triggers: 0 of 108 tape-only attribution tests carry information (6 books x 18 signals: adverse momentum 60/300 s, vol burst, no progress 10/30 min, stuck negative, give-back 25/40%, stall, roll-over, no new high 5/15 min, vol expansion, random control). So no plan uses a tape-based market "leave now" trigger. Book/flow triggers need MBO or 10-level paths for NP entries, not extracted yet.
- What does carry something is the SHAPE of the exit (scale-out + extended second target + breakeven + time stop), not a trigger. In hindsight it halves drawdown on MF3, NP-MACD and NP-CONF at equal income; walked forward it does not hold the income clause:
  - 4-book live mix, WF re-pick of the shape every 13 / 4 / 2 weeks: shallower max drawdown than fixed bracket in 13 / 12 / 12 of 13 forward periods and better worst week in 9 of 13, chained DD -34.2k / -31.0k / -32.4k vs -38.3k, worst week -11.8k..-13.8k vs -25.7k, BUT income 209k / 147k / 139k vs 287k (-27% / -49% / -52%); income higher in only 4-5 of 13 periods. Versus fixed bracket + live per-book layers: DD better 11 / 10 / 10 of 13, income 209k vs 299k. FAIL (income clause). Pessimistic fills: income 156k / 95k / 87k.
  - Hold-out (fit weeks 0-108, test 109-181) of a fit-picked shape: fails on MF1, MF3, MF4 (income 13-21% of reference), mixed on MF2, DD shallower but income -26% (NP-CONF) and -34% (NP-MACD).
- Plan of record for every book until a plan passes = the live exit (fixed bracket + per-book layers). The best candidate shape to carry into round 2 is below (hindsight, NOT validated).


## ROUND 2 UPDATE (04:20Z): two quick-screen candidates, nothing validated yet
- Family "target kept" (leg 1 at the own target, stop 0.5-0.75-1.0 S, optional runner / second target / BE / 3600 s time stop; 150 variants), WF pick with an income floor (last 26 wk income >= 90% of the own bracket), written before scoring.
- NP-MACD: walk-forward (2/4/13 wk) income 78k/76k/70k vs 43.7k fixed bracket, chained DD -20.4k vs -31.5k, L6M DD -5.2k vs -10.3k; income higher in 10-11 of 13 periods; pessimistic fills income 72k/70k/65k vs 39k; beats the random-pick null (income 97-99%, DD 89-91%). Clears the SOLUTION income-higher clause. Caveats: 2025 DD deeper, 2026 carries most of the gain, quick screen only, not yet on exact rows or the non-hindsight entry sample.
- 4 live books (equal lots), re-pick every 2 weeks: DD shallower in 10 of 13 periods, worst week better in 10, income -2% vs fixed bracket (-6% vs bracket + live layers; pessimistic -8%): clears clause 1 at step 2 only (step 4 fails on pessimistic income); beats the random-pick null on drawdown but not on income; 2026 income lower and DD deeper. Weak.
- MF2, MF3 clear the clause numerically but do not beat the random-pick null: not credited. MF1, MF4, NP-CONF fail.
- Not done: X24 steering (controller not posted), exact rows (disk 22 GB free < 32 GB rule), MBO/10-level paths (needs NP entries table; server C has no depth files). Details: PLAN_NP_LOG.md round 2.


## ROUND 3 UPDATE (stress test): the NP-MACD candidate is downgraded
- Not an outlier, both sides help, plan income above the fixed bracket in 26 of 27 pick-rule settings (floor 80/90/100%, history 13/26/52 wk, step 2/4/13) and chained DD shallower in 26 of 27; but the per-period clause (income higher in >= 9 of 13 with DD not deeper) holds in few settings and 52-week history is poor.
- Clean out-of-sample fixed rule (shape picked on weeks 0-108, held 109-181): income 18.3k vs 26.9k (-32%), DD -25.3k vs -31.5k: FAILS. The same shape on MF1/MF3/MF4/NP-CONF loses 33-43% income (MF4 negative): not general.
- So the walk-forward gain comes from re-picking among 19 variants, not from a fixed plan. Status: lead only. 4-book mix step 2: not a candidate. Details PLAN_NP_LOG.md round 3.

## Yardstick rows (1 lot, quick screen, May-Oct window = tape; L3M = weeks 169-181 = 2026-07-10..10-09, L6M = weeks 156-181)
| book | REF0 fixed bracket: inc / maxDD / worst wk (wk 26-181) | REFTH (+ live per-book layer): inc / DD | L3M inc/DD (REF0) | L6M inc/DD (REF0) |
|---|---|---|---|---|
| MF1 30/30 | 78.0k / -21.5k / -6.3k | 54.7k / -22.0k | 7.9k / -6.5k | 38.2k / -6.5k |
| MF2 120/120 | 44.2k / -34.6k / -17.3k | 82.0k / -24.3k | 15.9k / -5.6k | 21.5k / -9.7k |
| MF3 80/40 | 98.5k / -15.1k / -5.9k | same | 11.2k / -3.9k | 19.7k / -7.1k |
| MF4 60/60 | 66.5k / -19.7k / -7.0k | 64.0k / -21.0k | 9.7k / -9.8k | 24.6k / -9.8k |
| NP-MACD 90/30 | 43.7k / -31.5k / -8.1k | same (no layers) | 17.4k / -5.5k | 21.9k / -10.3k |
| NP-CONF 90/90 | 148.2k / -17.0k / -6.0k | same | 14.0k / -7.7k | 39.9k / -7.7k |
Fixed plans written before scoring (fixed_rules_plan_np.json; 0 free settings): A bank-early (half at 0.5T, BE, rest at T), B half-runner (half at T, BE, rest trails 0.5T, no target), C three targets (1/3 at 0.5T, 1/3 at T, last third trails 0.5T). 1-lot full-period incomes: A/B/C = MF1 39/54/20k, MF2 71/72/86k, MF3 60/107/52k, MF4 14/65/31k, NP-MACD -38/40/-37k, NP-CONF 123/136/108k. None beats REF0 on income except MF2 (all three; DD -24k..-31k vs -34.6k).

## Per-book plan (the shape that held best in hindsight, labelled; static, no steering; numbers in units of the book's own stop S and target T; none of these is a recommendation)
Common to all: entries are the books' own; initial stop = own stop S (or 0.75 S where stated; stop is structural distance from the entry signal, the live stop-market order); stop never widened; trail rule = breakeven (entry +0) once the first partial fills, no further trail in the t2 shape; flat at 16:00:01 ET (the live session end); no leave-now trigger (none carries information on the tape; book triggers pending MBO). Fills: targets limit at touch, stops stop-market (pessimistic label adds slip(lots)).
| book | stop | leg 1 | leg 2 / runner | BE / time | hindsight (wk 26-181, 1 lot) inc / DD vs REF0 | status |
|---|---|---|---|---|---|---|
| MF1 | S 30 | 67% at 1.0T (30 pt), | 33% at 1.5T (45 pt) | BE after leg 1 | 77.6k / -18.5k vs 78.0k / -21.5k; L3M 15.9k/-7.7k vs 7.9k/-6.5k | in-sample only; hold-out fails |
| MF2 | 0.75 S = 90 | 50% at 0.5T (60) | 50% at 3T (360, i.e. to the 16:00 flat) | BE, 3600 s time stop | 53.4k / -14.9k vs 44.2k / -34.6k | hold-out DD no better (2025 bad year) |
| MF3 | S 80 | 50% at 0.5T (20 pt) | 50% at 1.5T (60 pt) | BE no, no time stop | 94.8k / -10.2k vs 98.5k / -15.1k; L6M 15.9k / -4.3k vs 19.7k / -7.1k | hold-out income 21% of ref |
| MF4 | S 60 | 50% at 1.0T (60), | runner trails 0.25T = 15 pt behind best | none | 67.9k / -18.9k vs 66.5k / -19.7k; L3M 8.3k / -9.8k vs 9.7k / -9.8k | within noise of REF0 |
| NP-MACD | S 90 | 33% at 0.75T (22.5 pt) | 67% at 2T (60 pt) | no BE | 96.5k / -13.0k vs 43.7k / -31.5k | hindsight; hold-out DD -27k vs -31k, income -34% |
| NP-CONF | S 90 | 33% at 1.0T (90) | 67% at 2T (180) | BE after leg 1 | 149.9k / -13.9k vs 148.2k / -17.0k; L6M 47.1k / -7.2k vs 39.9k / -7.7k | best candidate for round 2 (24 fit-eligible variants, 42% hold-good) |
Lots: integer legs by round-half-up with at least 1 lot per leg, the rest to the last leg. For two legs of 33/67 or 50/50: 2 lots = 1+1; 3 lots = 1+2 (50/50 gives 1+2); 4 lots = 1+3 or 2+2; 6 lots = 2+4 or 3+3. Three-target plans (C): 2 lots collapse to two legs; 3 lots 1/1/1; 4 lots 2/1/1; 6 lots 3/2/1. At 1 lot a partial is impossible: arm breakeven at the first leg level, hold the whole lot to the LAST leg's level (the one-lot equivalent in plans.py build()).

## Data note for Josh (LEAD TO JOSH inputs)
All of round 1 needs only NT8 prices, 1-second bars, session clock and the live bracket (no 10-level, no MBO, no UW): the scale-out + extended-target shape and breakeven are bar/price rules. Book-state triggers (walls, pulls, absorption) were NOT run for NY PM: the MBO/10-level difference is open; the extractor exists for Asia/NY AM only.

## Caveats
- Quick screen (tape last-trade prices, entry at the event second, 0.25 pt stop slip; engine reproduces my bracket P&L within 5-20% on checked months; entry times match 100%), each book alone, one position at a time; no mix locks, zones, BookLock or day limits; REFTH only emulates the per-book layers. Tape ends 2026-10-09 (engine data to 10-31 not on the tape): L3M/L6M windows end 10-09.
- 681 x 6 variants were searched; hindsight rows are selection-biased and only the fit/hold and WF rows are evidence. The 6 books' attribution table is /mnt/l2/l2vast/_plan_np/attr_table.csv; defaults_table.csv, grid1_*.npz, wf1.csv are in the same directory; code in code/th_plan_np.
- NP-MACD / NP-CONF identity is a reading (see PLAN_NP_LOG.md); exact in-mix rows for them do not exist (a 14-recipe seed round per book x 42 months x alone/mix = 1,176 rows per book, W-DYNH's count).
