# DS3_TD4 - capacity, peak concurrent lots, margin proxy (D3SZ, addendum 2 D4, 2026-10-26)
Prereg l2vast/ds3/prereg/D4_prereg.md sha256 3a45d001fe3004764edf4b56a9fb8e76bcef0e36788d58114ee9ec5518e59fd1 (9 cells), pre-holdout text DS3_TD4_PREHOLD.md, holdout look once (track DS3_TD4). Code l2vast/ds3/code/sz/d4.py; rows l2vast/ds3/rows/DS3_TD4.json (all curves, windows WF-PRE/WF/HOLD, CIs, concurrency, margin).
## Method and caveats
Sweep cost model = firmlib.size_cost_usd, i.e. the measured market-walk surface (l2vast/riskS5/results/s113_NQ.csv: excess ticks per lot per round trip 4.6 @14, 6.1 @21, 7.4 @28, 9.4 @42, 10.7 @56 lots), $5/tick, charged per traded row as lots x (excess(L) - excess(base)) with base = 14 lots for ST/HM/WT (P9 basis) and 10 lots for the T-ENTRY books and TB7 (their pricing is the 10-lot S10x1 basis). The surface ends at 56 lots: 84/112/168 are LINEAR EXTRAPOLATION. It is a market-order sweep surface, so it is conservative for the slicing/stop-join books; locks do not see the size cost (applied after the lock engine). Each book is re-run in the exact lock engine at L lots (R = L x stop x $20), then cost subtracted. "Delta vs ST" = book at L lots minus ST at the same L (both with the surface), WF 142 weeks. ST below 14 lots receives a small credit (the surface is lower than at 14 lots), hence ST 10 lots = 15.5k here vs 14.4k at the nominal run.
## Capacity curves, WF weekly mean ($k/wk) by lots
| book | 5 | 10 | 14 | 20 | 28 | 42 | 56 | 84 | 112 | 168 | zero of own mean (lots) | peak of curve |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | 8.4 | 15.5 | 20.1 | 25.4 | 30.0 | 34.2 | 35.7 | 23.9 | -7.8 | -130.5 | ~105 | 56 |
| HM | 6.2 | 11.1 | 14.1 | 17.0 | 18.8 | 18.2 | 15.2 | -4.5 | -42.5 | -173.0 | ~78 | 28 |
| WT | 2.9 | 3.7 | 2.9 | -0.8 | -9.2 | -29.7 | -54.1 | -124.8 | -224.5 | -511.3 | ~19 | 10 |
| TE7_kelt3m | 9.1 | 16.8 | 22.0 | 27.9 | 33.5 | 39.1 | 42.0 | 32.4 | 2.5 | -118.3 | ~113 | 56 |
| TE6_st10m_n7 | 4.9 | 9.1 | 12.0 | 15.6 | 19.3 | 23.9 | 27.2 | 26.8 | 17.0 | -30.4 | ~132 | 56-84 |
| TE7_emax5m | 4.1 | 7.6 | 9.9 | 12.7 | 15.2 | 18.0 | 19.5 | 15.8 | 3.1 | -49.2 | ~115 | 56 |
| TB7_ORBNY | 3.2 | 6.1 | 8.1 | 10.9 | 13.9 | 18.4 | 22.2 | 26.5 | 26.2 | 11.9 | none to 168 | 84-112 |
Per-lot edge (WF mean / lots, $/lot/wk): ST 1686 @5 -> 814 @42 -> 637 @56; kelt 1827 -> 931 @42 -> 750 @56; st10m_n7 979 -> 568 @42; HM 1236 -> 434 @42; WT 574 -> -706 @42.
## Paired delta vs ST at the same lots (WF $k/wk)
kelt3m: +0.7 (5), +1.4 (10), +1.9 (14), +2.6 (20), +3.5 (28), +4.9 (42), +6.3 (56), +8.6 (84), +10.3, +12.2 (168): positive at every size and it grows, but only because ST's mean erodes faster; the CI at 10/28/56 lots is [-9.4k,+11.6k] / [-26.2k,+32.0k] / [-52.7k,+63.1k] (includes 0; MDE of the weekly pair ~20k). So the paired delta vs ST never falls to zero for kelt on the grid (no capacity limit set by ST), while in absolute terms kelt's own mean goes to zero at ~113 lots,; its WF curve peaks at 56 lots (93% of peak at 42). st10m_n7, emax5m and TB7 have NEGATIVE delta vs ST at all sizes up to ~56 lots (-6.3k/-7.9k/-9.4k at 10 lots, CIs [-17.4k,+3.5k], [-18.4k,+3.0k], [-21.9k,+1.5k]) and turn positive only above ~70-90 lots because ST collapses (extrapolated region): ST alone is the higher-mean book in WF at any realistic size; their value is diversification, not mean. HM and WT: delta vs ST negative everywhere (WT 10 lots CI [-21.2k,-3.2k]). Reading for capacity: practical size ceilings (own mean within 10% of curve peak, inside the measured surface <= 56 lots): ST ~42, kelt ~42, st10m ~56, emax ~56, HM ~20, WT <= 7-10 (WT7 is already at its maximum). Holdout curves peak at 56 (ST 43.0k), kelt peak 28 lots (21.1k) and are negative from 84 lots (holdout kelt much weaker than WF, see rows).
## Peak concurrent lots (exact-engine entry/exit-second interval replay, WF+IS full 953 days; not a sum of peaks)
| combination (lots) | peak | p99 | time share > 50 | entries blocked by a 50 cap (greedy) / entries | sum of nominal lots |
|---|---|---|---|---|---|
| DS2 10/10/7 | 27 | 27 | 0 | 0 / 15,613 | 27 |
| DS3a (kelt, st10m_n7, TB7) 10 each | 40 | 30 | 0 | 0 / 8,190 | 30 |
| DS3b (kelt, st10m_n7, emax) 10 each | 30 | 30 | 0 | 0 / 9,188 | 30 |
| DS2 + DS3a nominal | 67 | 47 | 0.4% | 90 / 23,803 | 57 |
| DS2 + DS3a, DS3 at 3/5/4 | 43 | 35 | 0 | 0 | 39 |
| DS2 + DS3b nominal | 57 | 57 | 9.2% | 626 / 24,801 | 57 |
| DS2 + DS3b, DS3 at 5 each | 42 | 42 | 0 | 0 / 24,801 | 42 |
| ALL7 nominal | 77 | 57 | 9.6% | 792 / 25,963 | 67 |
Notes: peak reaches the full sum (27, 30, 57) in many sessions, so concurrency does NOT reduce the peak for DS2 or DS3b: the books fire together (trend days). TB7 peaks at 2x its lots (20 at 10 lots): the T-B exit window is the whole exit bar, so an entry in the bar after an exit overlaps the prior exit interval by construction (the same convention that gave TB7 peak 20 in DS3_PORTFOLIO); it overstates DS3a/ALL7 peaks by up to 10. Interval end = the engine's lock/exit second.
## Margin proxy (ASSUMPTION; no margin file on disk, FEES.md has none)
Per-contract NQ margin assumed: intraday/day-trade $1,000 (low) and $2,500 (conservative) at the broker; CME overnight initial about $30,000 is irrelevant (all books flat 16:55 ET, no overnight). Proxy = peak concurrent contracts x figure: DS2 27 -> $27k-$68k; DS2+DS3b 5 each (42) -> $42k-$105k; DS2+DS3b nominal (57) -> $57k-$143k; DS2+DS3a nominal (67) -> $67k-$168k. Compare with the weekly SD (about $72k-$128k) and the maxDD ($312k-$545k): margin is secondary to the 50-contract limit and to drawdown. Replace with the account's actual margin schedule before use.
## Verdict and the lots to adopt
Capacity is not binding below ~40 lots per book in this model; the binding constraint is the 50-contract limit: DS2 (27) + DS3b at 10/10/10 (30) = 57 peak, over the cap 9.2% of the time, 626 entries blocked; DS3 at <= 5 lots each keeps the combined peak at 42. Sweep-model capacity is a ceiling on market-order sweeps; the T-ENTRY books use S10x1 slices and XJ3 stop-join, so their true curves are flatter than shown. MDE: paired weekly CIs above (every delta vs ST except WT includes 0).
