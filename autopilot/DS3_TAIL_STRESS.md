# DS3_TAIL_STRESS - tail-event stress replay of the six live books at live lots (DIS-AL, Z3, 2026-11-04)
Measurement, not a hypothesis test. No PASS claims, nothing live. Scope note l2vast/ds3/prereg/DIS_AL_scope.md sha256 67b2d2d94040fe7439d062db68a83283ebd4e8947786b84a3aba815d68e8cb61 (DECISIONS.md, before any statistic). Code l2vast/ds3/code/tail_stress/ (tail_days.py, replay_a.py, replay_b.py, replay_b2.py, slip_tape.py, tail_an*.py); data l2vast/ds3/out/tail_stress/. SYNTHETIC figures are marked SYNTHETIC; everything else is a replay of historical days.

## Plain sentences
1. On the 1-second engine at live lots (Q1-A ts2, live lock), the worst single day 2023-04..2026-10 was -$38.1k (2025-01-20), the worst week -$62.6k (2026 W44) and the maxDD (the HOLD episode) $122.0k; the 20 tail-range days of 2023-26 were NET POSITIVE for the live stack (mean +$12.2k per day, bootstrap 95% CI +$2.0k to +$23.0k; losing share 35% vs 48% on other days), the worst of them 2025-04-03 at -$28.3k.
2. The live day lock does NOT bound a single-day loss: the worst day is identical with and without the locks (-$38.1k both); the give-back lock only trims the worst WEEK by $3.9k (-$62.6k vs -$66.5k) and the maxDD by $8.8k ($122.0k vs $130.8k); the 12R week floor never binds on this base (floor-only = no lock, total and path identical).
3. Stop slippage through the tape is fat-tailed but is not what hurts: on 12,955 live-signal stop exits of 2023-26 the next-second price is on average 0.15 pt worse than the stop (median -0.25, 95th pct 5.0, 99th 16.5, max 102.3); on the 515 stop exits of tail days the mean is 1.05 pt, 95th pct 10.2, 99th 48.2; stressing the engine stop cost to 3x / 5x / 10x of 2.45 pt costs 5% / 11% / 24% of the total P&L but moves the worst day only from -$38.1k to -$39.0k / -$39.9k / -$42.2k and the maxDD from $122.0k to $125.0k / $127.9k / $135.3k.
4. The signal-level raw-entry object (no exits, no locks, 1-min fills; NOT the live stack) loses far more on bad days: worst day -$97.3k (2026-06-24) and worst week -$233.3k, and -$81.6k on 2020-03-20; the live stack's exits, zones and locks cut those losses by roughly 2-3x on the days both can be compared (2025-04-09: -$69.8k vs -$23.8k), so use the engine row for live-stack risk and the object only as an upper bound.
5. The risk that these replays cannot show is a limit-style move THROUGH resting stops: SYNTHETIC worst case with 18 lots net (Q1-A worst simultaneous net, $21.6k at the 60-pt stops) and the largest historical adverse 30-minute move scaled to today's index level (-1,449 pts, -5.8%) gives -$522k, x2.0 -$1.04M; a 7% / 13% / 20% limit move (1,750 / 3,250 / 5,000 pts at 25,000) would be -$630k / -$1.17M / -$1.8M, i.e. 5x to 15x the HOLD episode, not -$22k.

## 1. Tail-day sets
Label days of the owned NQ 1-min history 2013-2026 (3,545 days with >= 600 bars): top 40 each by RTH range (%), 24-hour range (%), maximum 1-minute |return|, maximum 5-minute |return|, and RTH-open gap (%), plus 40 named days (2015-08-24, 2018-02-05, 2020-02-24..03-31 limit-move era, six 2022 CPI days, 2024-08-05, 2025-04-03..09): 108 distinct tail days (by year 2013-2026: 2015 4, 2016 3, 2018 13, 2019 1, 2020 35, 2021 2, 2022 29, 2023 2, 2024 2, 2025 13, 2026 4). Largest RTH ranges: 2025-04-09 11.3% (2,185 pts), 2025-04-07 9.6%, 2020-03-13 8.5%, 2020-03-17 8.1%, 2025-04-08 8.0%, 2020-03-12 7.8%, 2020-03-20 7.5%, 2015-08-24 7.1% (288 pts). Largest 5-minute absolute moves: 4.85% (2025-04-09, up), 4.70% (2025-04-07), and the largest 5-minute down move -3.82% (2022-10-13). Table data/tail_days.csv. Distance from the previous RTH close (approximate CME reference): 27 days with a low <= -5%, 5 days <= -7% (2020-03-16 -12.8%, 2020-03-12 -10.9%, 2020-03-18 -8.5%, 2020-03-09 -8.3%, 2025-04-10 -7.0%), none <= -13%; 7 days with a high >= +7% (2025-04-09 +12.5%, 2020-03-13 +9.9%, 2020-03-17 +8.8%).

## 2. Loss per book on named tail days at live lots ($k)
Object A = signal-level replay of the six books' signal streams at live lots (session lots x A06 x B02 x ER Q1-A, sequential), 1-min fills, V2 PERCENT bracket (60 pts x year-median close / 20,620 each side), results at 2023-26 price scale; slip x1 / x3 / x5 = stop slippage 1.5 pt / 4.5 / 7.5 (x the year factor); ENG = the 1-s engine (live lock / no lock), 2023-26 days only (blank before). Object A is NOT the live stack.
| label day | RTH range / gap / max 5-min | A: KB | PE | SM | HM | MV | PB | A total x1 | A x1 / x3 / x5 | ENG live lock | ENG no lock |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 20150824 | 7.1% / 6.2% / 3.1% | -0.8 | +39.2 | -4.9 | +11.7 | -2.7 | -0.2 | +42.3 | +42.3 / +37.5 / +32.8 |  |  |
| 20180205 | 4.9% / 0.8% / 1.6% | -0.4 | -19.1 | -4.9 | -6.2 | -1.4 | -1.2 | -33.2 | -33.2 / -36.5 / -39.7 |  |  |
| 20200309 | 5.3% / 6.5% / 2.4% | -8.7 | -11.3 | -12.8 | +9.5 | -10.8 | -1.3 | -35.4 | -35.4 / -38.5 / -41.6 |  |  |
| 20200312 | 7.8% / 6.2% / 3.2% | -5.7 | -3.6 | +2.3 | +1.9 | -2.7 | -1.4 | -9.2 | -9.2 / -15.1 / -21.1 |  |  |
| 20200313 | 8.5% / 5.9% / 2.2% | +1.6 | +24.9 | +4.8 | -0.7 | +3.3 | -1.4 | +32.5 | +32.5 / +25.7 / +18.8 |  |  |
| 20200317 | 8.1% / 3.4% / 1.9% | +7.8 | -10.2 | -2.5 | +2.2 | +9.4 | +0.0 | +6.6 | +6.6 / +2.2 / -2.3 |  |  |
| 20200318 | 7.1% / 6.2% / 1.9% | +13.9 | +4.9 | +4.8 | -18.8 | -1.4 | +2.4 | +5.8 | +5.8 / +0.1 / -5.6 |  |  |
| 20200320 | 7.5% / 2.2% / 1.4% | -12.9 | -69.0 | -0.2 | -2.7 | +4.5 | -1.3 | -81.6 | -81.6 / -89.2 / -96.9 |  |  |
| 20220610 | 2.3% / 1.9% / 1.9% | -7.5 | -38.7 | -14.8 | -5.0 | -5.0 | -2.5 | -73.5 | -73.5 / -78.1 / -82.7 |  |  |
| 20220713 | 2.8% / 2.0% / 3.3% | -0.2 | -14.6 | -2.6 | -11.1 | -3.8 | +0.0 | -32.4 | -32.4 / -36.2 / -39.9 |  |  |
| 20220810 | 1.3% / 2.4% / 2.0% | -2.6 | -11.9 | +2.4 | -7.4 | -2.6 | +0.0 | -22.1 | -22.1 / -24.9 / -27.7 |  |  |
| 20220913 | 3.5% / 2.9% / 3.0% | -3.9 | +12.3 | +0.0 | +2.4 | -2.6 | -1.2 | +6.9 | +6.9 / +4.8 / +2.6 |  |  |
| 20221013 | 5.9% / 2.9% / 3.8% | +2.1 | +20.6 | +2.4 | +1.2 | +5.9 | +0.0 | +32.2 | +32.2 / +30.3 / +28.4 |  |  |
| 20221110 | 3.2% / 4.9% / 2.9% | -2.6 | -14.3 | -12.3 | -3.7 | -5.0 | +0.0 | -38.0 | -38.0 / -41.2 / -44.5 |  |  |
| 20240805 | 4.3% / 5.4% / 1.1% | +21.2 | +43.8 | -2.5 | +17.8 | -6.5 | +2.4 | +76.1 | +76.1 / +72.0 / +67.9 | +62.3 | +62.3 |
| 20250403 | 2.2% / 4.2% / 0.7% | -4.0 | -33.9 | +2.3 | +4.5 | -6.3 | -0.0 | -37.4 | -37.4 / -41.4 / -45.5 | -28.3 | -28.3 |
| 20250404 | 4.1% / 2.8% / 1.1% | +6.7 | -19.7 | +4.8 | +1.0 | +4.5 | -0.0 | -2.7 | -2.7 / -6.8 / -10.9 | -0.7 | -0.7 |
| 20250407 | 9.6% / 3.5% / 4.7% | -1.9 | -27.4 | -2.5 | +3.2 | -2.7 | +0.0 | -31.2 | -31.2 / -38.7 / -46.1 | +15.0 | +17.9 |
| 20250408 | 8.0% / 3.4% / 1.4% | +7.9 | -36.0 | -9.9 | -0.1 | -1.4 | +0.0 | -39.5 | -39.5 / -45.0 / -50.5 | +4.1 | +9.6 |
| 20250409 | 11.3% / 0.2% / 4.8% | -2.1 | -48.4 | -10.0 | -0.1 | -6.6 | -2.5 | -69.8 | -69.8 / -79.5 / -89.2 | -23.8 | -27.8 |
| 20250410 | 5.2% / 2.5% / 1.2% | -1.8 | +7.9 | -2.6 | -0.2 | -2.7 | -0.0 | +0.4 | +0.4 / -4.5 / -9.3 | -27.2 | -27.2 |
Per book, engine (live lock), worst day / worst week 2023-26: KB -$5.9k / -$15.6k, PE -$28.2k (2023-12-05) / -$56.9k, SM -$11.1k / -$21.6k, HM -$10.9k / -$19.4k, MV -$6.0k / -$14.3k, PB -$2.6k / -$7.6k. PE is the book that carries the tail: its tail-day sum is +$183k but its worst day is 3x any other book.
Raw-entry object A, tail vs other days (V2, x1): tail mean +$3.8k per day (sd $37.1k, losing share 46%) vs other days -$1.1k (sd $22.9k, 53%): the tail days are not systematically the bad days for the signal rules; the worst days of the object (2026-06-24 -$97.3k, 2025-11-21 -$88.9k, 2020-10-23 -$86.0k, 2018-02-09 -$84.5k, 2020-03-20 -$81.6k) are mostly whipsaw days.

## 3. Worst day / worst week table at live lots
| object | worst day | mean of the 5 worst days | worst week | 1st pct of days | tail-day mean | worst tail day |
|---|---|---|---|---|---|---|
| ENGINE live lock (2023-26, 935 days) | -$38.1k (2025-01-20) | n/a | -$62.6k (2026 W44); maxDD $122.0k | -$30.0k (95% CI -$33.7k to -$28.1k; 5th pct -$20.5k, CI -$22.9k to -$18.3k) | +$12.2k (CI +$2.0k to +$23.0k, n 20) | -$28.3k (2025-04-03) |
| ENGINE no floor / no give-back | -$38.1k (2025-01-20) | n/a | -$66.5k (2026 W06); maxDD $130.8k | n/a | +$12.5k | -$28.3k |
| ENGINE live lock, stop cost x3 / x5 / x10 | -$39.0k / -$39.9k / -$42.2k | n/a | -$63.7k / -$64.7k / -$65.0k; maxDD $125.0k / $127.9k / $135.3k | n/a | +$12.1k / +$11.9k / +$11.4k (mean per day; the 20-day sums are $241k / $237k / $227k) | -$28.4k / -$28.5k / -$28.7k |
| OBJECT A V2 (raw entries, 2013-26) x1 / x3 / x5 | -$97.3k / -$103.5k / -$109.7k (2026-06-24) | -$87.7k / -$94.1k / -$100.5k | -$233.3k / -$255.2k / -$277.1k (2015 W36) | -$57.6k (CI -$63.0k to -$54.3k) | +$3.8k / -$0.0k / -$3.9k (n 108; CI of the x1 mean -$2.8k to +$11.1k) | -$81.6k (2020-03-20) |
| OBJECT A V1 FIXED 60/60 (2023-26) x1 / x3 / x5 | -$93.2k / -$100.3k / -$107.4k | -$80.2k / -$87.4k / -$94.5k | -$184.0k / -$221.9k / -$259.7k (2025 W15) | -$56.9k | +$12.4k / +$8.8k / +$5.2k (n 21) | -$77.4k (2025-04-09) |
The engine is the only row that is the live stack's P&L; the engine number for the HOLD episode is the base maxDD ($122.0k). The weekly CI is reported only as the 1st percentile for the engine (n weeks 187; the weekly 1st-percentile is -$61.8k, CI -$62.6k to -$44.2k, dominated by one week).

## 4. Stop slippage through gaps (assumption stated)
Engine: stops fill at the stop level + a flat 2.45 pt (stopcost), market exits 0.80. Tape check on 2023-26 (1-second path, live-signal stop exits with a 60-pt stop, E = path close at the signal second): slip_next = stop level minus the close one second after the touch (adverse positive), slip_within = stop level minus the extreme of the touch second. All stop exits (n 12,955): slip_next mean 0.15, median -0.25, 95th 5.0, 99th 16.5, max 102.3 pt, 14% worse than 2.45; slip_within mean 1.75, median 0.75, 95th 6.3, 99th 17.5. Tail-day stop exits (n 515): slip_next mean 1.05, 95th 10.2, 99th 48.2, max 101.8, 20% worse than 2.45; slip_within mean 3.2. The largest through-the-stop fills are single events (2025-10-24 SM 102 pt, 2025-02-12 MV 102 pt, 2025-02-07 PE 84 pt), so the flat 2.45 is right on average and wrong in the tail; the x3 / x5 / x10 rows above price that. Before 2023 the object uses the 1-min bar (fill at the stop level unless the bar opens beyond it; gap-through at the open) + 1.5 pt (x1), 4.5 (x3), 7.5 (x5), scaled by the percent factor.

## 5. Locks
Engine spec: per-book week floor 12R, day give-back arm 2R keep 50%, daily +- R caps (the caps are part of the spec in all rows below and were not varied). Results (live lock vs no floor / no give-back): total $2,520.1k vs $2,594.2k; worst day -$38.1k vs -$38.1k (the lock does not bound the day loss: the give-back arms only after a profit); worst week -$62.6k (2026 W44) vs -$66.5k (2026 W06); maxDD $122.0k vs $130.8k; tail-day sum +$244.1k vs +$250.3k. Floor-only (12R, no give-back) is identical to no lock; give-back-only is identical to the live lock: the 12R week floor never binds, the give-back lock is the only active protection and costs $74.0k of total P&L (2.9%) for $8.8k of maxDD. Examples: 2025-04-09 -$23.8k with the lock vs -$27.8k without; 2025-04-16 +$10.9k vs -$2.3k; 2025-04-08 +$4.1k vs +$9.6k.

## 6. SYNTHETIC stress (all figures SYNTHETIC; upper bounds, not replays)
Largest historical adverse close-to-close moves 2013-2026 (percent of price scaled to 25,000): 1 min -867 pts (-3.47%, 2022-10-13), 5 min -954 (-3.82%, 2022-10-13), 15 min -1,142 (-4.57%, 2020-03-16), 30 min -1,449 (-5.80%, 2020-03-16), 60 min -1,383 (-5.53%, 2025-04-07); largest up moves +667 / +1,212 / +1,646 / +2,134 / +2,079 (2025-04-07/09). Loss for the stack's worst simultaneous exposure, 18 lots net (S4a SIZER_EXPOSURE, Q1-A, 60-pt stops, $21.6k stop risk), if every stop is passed and fills at the end of the move: loss = 18 x $20 x max(62.45, move).
| window | x1.0 | x1.5 | x2.0 | stops only |
|---|---|---|---|---|
| 1 min (867 pts) | -$312k | -$468k | -$624k | -$22.5k |
| 5 min (954 pts) | -$343k | -$515k | -$687k | -$22.5k |
| 15 min (1,142 pts) | -$411k | -$616k | -$822k | -$22.5k |
| 30 min (1,449 pts) | -$522k | -$783k | -$1.04M | -$22.5k |
| 60 min (1,383 pts) | -$498k | -$747k | -$995k | -$22.5k |
Limit-style move (SYNTHETIC): 7% / 13% / 20% of 25,000 = 1,750 / 3,250 / 5,000 pts x 18 lots x $20 = -$630k / -$1.17M / -$1.80M. Worst case 'all six books the same direction': the maximum simultaneous session lots are Asia KB 2 + PE 7 + SM 4 + HM 4 + PB 1 = 18 (London 15, NY-AM 10) at multiplier 1.0, i.e. the same 18 lots; the ER x0.5, A06 / B02 halvings and the zone half only reduce it. These losses are 2.6x to 15x the real engine HOLD maxDD ($122k) and 8x to 47x the real worst day (-$38k): the live record contains no event of this kind, and a single gap through the stops is the one scenario the replays cannot rule out.

## 7. CME limit / halt rules (from rulebook knowledge only; no lookup possible; UNVERIFIED items marked)
* Equity index futures price limits are tied to the NYSE-style market-wide circuit breaker levels: 7% (Level 1), 13% (Level 2), 20% (Level 3) below the prior-day reference price (UNVERIFIED exact reference time and the yearly reset convention); Level 1 and 2 halts apply in regular trading hours only (UNVERIFIED exact duration, believed 15 minutes, and the cut-off time of the afternoon); Level 3 ends trading for the day; outside regular hours a fixed overnight limit applies (believed 7% of the reference price, with trading allowed only at or inside the limit; UNVERIFIED, older rules used 5%).
* Our own data: 5 label days had the low at least 7% below the previous RTH close (2020-03-16, 03-12, 03-18, 03-09 and 2025-04-10 at -7.0%), none reached -13%; 2025-04-09 rose +12.5% from the prior close; so the level-1 / limit regime was reached in 2020 and perhaps in April 2025 (UNVERIFIED which of these days actually halted).
* Resting stops in a halt: stop orders are held by the exchange and trigger on trades at or through the stop price; during a halt or limit state no trades occur, so stops do not trigger and nothing fills; on reopening the triggered stops become market orders (CME stop orders are market-with-protection, UNVERIFIED protection points for NQ) and fill at the first available prices, which can be far beyond the stop; in a limit-down state the market can be offered only at the limit with no bids, so a long position may be unable to exit until the limit moves. This is why the SYNTHETIC limit rows above are labelled as upper bounds on slippage past the stops, not as predictions.
* None of the live code sees these rules (the engine fills at the stop plus a flat slip); the open question for the user is the stop type actually working at the exchange (stop-market with protection vs a stop-limit) and the broker's overnight margin behaviour in a limit state.

## 8. Caveats
Object A is a signal-level approximation (weekly correlation with the live stack 0.66-0.69, DS3_STACK_2013.md): no Trade-Health exits, locks, zones, PE confirmation or 70/30; its dollar figures overstate the live stack's tail losses (compare the 2025-04-09 row: A -$69.8k vs engine -$23.8k). The V2 percent bracket is the comparable pre-2023 object; V1 is native only for 2023-26. The tail-day sets are selected on the days' own range, which is look-ahead by construction (this is a stress replay, not a trading rule). Percent-of-price moves use raw closes, point moves the additive back-adjusted series. Bootstrap CIs are stationary block bootstraps (2,000 draws) over days (mean block 5 days; tail-day mean: i.i.d.). Slippage on the tape is measured with the signal-second close as the entry (not the engine fill) and is a property of stop touches, not of the live fills. CME items are from memory.


## RESTATEMENT OF THE ENGINE ROWS ON THE LIVE-WINDOW BASES (appended 2026-11-05)
Bases: V0 = engine as run (the tables above); V1 = 18:00-18:04 blocked; V2 = 09:30-09:59 and 18:00-18:04 blocked (ZL-2, DS3_LIVE_WINDOWS_BASE.md); my window masks reproduce ZL-2's daily series to 0.000 $. Engine rows only (live lock vs no floor / no give-back, stop cost x1 and x5); the signal-level raw-entry object (Object A) and the synthetic rows are NOT restated (Object A would need the windows applied to its signals; the synthetic rows scale with peak net lots, which is 18 under all three bases).
| base | lock | stop cost | total | worst day (label day) | worst week (ISO week) | maxDD | tail-day mean (20 days) | worst tail day (label day) |
|---|---|---|---|---|---|---|---|---|
| V0 | live lock | 1x | $2520k | $-38k (20250120) | $-63k (202644) | $122k | +12.2k | $-28k (20250403) |
| V0 | live lock | 5x | $2252k | $-40k (20250120) | $-65k (202644) | $128k | +11.8k | $-28k (20250403) |
| V0 | no floor / no give-back | 1x | $2594k | $-38k (20250120) | $-66k (202606) | $131k | +12.5k | $-28k (20250403) |
| V0 | no floor / no give-back | 5x | $2306k | $-40k (20250120) | $-68k (202606) | $137k | +12.0k | $-30k (20250409) |
| V1 | live lock | 1x | $2593k | $-38k (20250120) | $-61k (202644) | $103k | +11.6k | $-30k (20250409) |
| V1 | live lock | 5x | $2330k | $-40k (20250120) | $-63k (202644) | $109k | +11.2k | $-31k (20250409) |
| V1 | no floor / no give-back | 1x | $2680k | $-38k (20250120) | $-63k (202606) | $112k | +12.2k | $-30k (20250409) |
| V1 | no floor / no give-back | 5x | $2399k | $-40k (20250120) | $-65k (202606) | $119k | +11.6k | $-31k (20250409) |
| V2 | live lock | 1x | $2462k | $-37k (20240905) | $-60k (202644) | $94k | +12.0k | $-28k (20250410) |
| V2 | live lock | 5x | $2223k | $-38k (20240905) | $-62k (202644) | $100k | +11.6k | $-29k (20250410) |
| V2 | no floor / no give-back | 1x | $2537k | $-37k (20240905) | $-60k (202606) | $100k | +12.2k | $-28k (20250410) |
| V2 | no floor / no give-back | 5x | $2284k | $-38k (20240905) | $-62k (202644) | $106k | +11.6k | $-29k (20250410) |
Per book, engine live lock, worst day / worst week ($): 
| base | per book |
|---|---|
| V0 | {'KB': (-5920, -15563), 'PE': (-28230, -56897), 'SM': (-11113, -21638), 'HM': (-10942, -19383), 'MV': (-5960, -14284), 'PB': (-2625, -7640)} |
| V1 | {'KB': (-5920, -12693), 'PE': (-28230, -52191), 'SM': (-11113, -21638), 'HM': (-10942, -15777), 'MV': (-5960, -14284), 'PB': (-2625, -7640)} |
| V2 | {'KB': (-5674, -14855), 'PE': (-28230, -52191), 'SM': (-11113, -21638), 'HM': (-10942, -15840), 'MV': (-5451, -12798), 'PB': (-2625, -7640)} |
Reading: the worst single day of the engine is -$38.1k under V0 and V1 (2025-01-20) and -$37.2k under V2 (2024-09-05), so the live windows do not bound the worst day; the worst week is -$62.6k / -$61.3k / -$60.0k; the maxDD (the HOLD episode) falls $122.0k / $103.3k / $94.0k; the 20 tail-range days stay net positive for the live stack (mean +$12.2k / +$11.6k / +$12.0k per day); the worst tail day is -$28.3k / -$30.3k / -$28.4k. The lock effect (give-back lock vs none) keeps its sign: the lock trims the worst week by $3.9k / $1.7k / $0.4k and the maxDD by $8.8k / $8.8k / $6.4k at a cost of $74k / $87k / $75k of total P&L under V0 / V1 / V2.
CLOCK AUDIT NOTE (2026-11-05): slip_next in section 4 is the stop level minus the close of the NEXT PRINT SECOND on the 1-s path (index k+1), not strictly 'one second after the touch': the path holds only seconds with prints, so in thin hours k+1 can be several seconds later. All time windows in this page and in DS3_OUTAGE.md are epoch-second arithmetic (searchsorted on the second stamps); no window was built by adding a count to a path index.
