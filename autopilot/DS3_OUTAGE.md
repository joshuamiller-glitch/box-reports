# DS3_OUTAGE - operational-outage replay of the live stack (DIS-AT, Z3, 2026-11-05)
Measurement, not a hypothesis test. No PASS claims, nothing live. Scope note l2vast/ds3/prereg/DIS_AT_scope.md sha256 37359aa058be1e464d6b46e2ea585fd42540f6122e27fc695d9443b9799bc65a (DECISIONS.md). DISCLOSURE: the scope note was filed after the replay machinery was built and its first numbers seen (I did not follow the scope-first order); the design is the Lead's brief unchanged; the first run's numbers were discarded after a lot-count bug fix; the two stress scenarios (iv), (v) were added for the assumptions list. Code l2vast/ds3/code/dis_at/ (at_lib.py, at_run.py, at_an.py); data l2vast/ds3/out/dis_at/. Object: the 21,397 taken trades of BASE-4 run_v13t_ts2 (Q1-A, live lock), 2023-04..2026-10, counterfactual delta per outage window on the 1-s path (no engine re-run: locks, ER state and other books are not re-simulated after a missed event). SYNTHETIC = a stress that assumes the live order structure differs from the brief.

## Plain sentences
1. With stops and targets as resting exchange orders (the brief's structure), an outage costs about $112-116 per outage-hour on average (scenarios i and ii, exact over all 1,320,115 trading-minute starts), almost entirely the entries that are not made (profits skipped and losses avoided net out): the median window changes nothing, the 1st percentile of a 60-minute window is -$12.1k and the worst is -$32.2k (60 min starting 2026-06-23 01:08 ET, a set of skipped winners), which is 26% of the HOLD episode ($122.0k) and is lost profit, not a drawdown.
2. The box-side exits are rarely what is at stake: 792 of the 21,397 trades (3.7%) end on a time / flat exit and 120 (0.56%) on an earlier box-side exit (TH cut or lock flatten); missing them for up to an hour changes the P&L by a mean of only +$0.61 (B) and -$0.72 (C) per 60-minute window (worst single window -$4.7k / -$10.5k); the platform-down orphan add (the cancel-on-exit missed) has only 2 candidate trades in 3.5 years (worst -$1.4k).
3. A disconnect in the middle of the entry slices (1 lot per 2 s) is a rare event (24,374 slice boundaries in 3.5 years; about $2.4 per hour of expected cost at 1 minute): if stops are placed at each slice fill, the unfilled remainder is lost (mean -$191 per event, 1st percentile -$7.3k, worst -$14.3k); if stops are placed only after the whole entry, the filled part is NAKED until reconnect and the worst event is -$14.3k (1 min) to -$42.2k (60 min) with the market exit at reconnect.
4. The risk that the brief's structure hides is the order-resting assumption: if the stops / targets are NOT resting at the exchange (box-side), a 60-minute outage costs a mean -$79 per hour but the worst placement is -$77.1k (2026-10-01 02:31 ET) and a 1-minute outage at the 2024-03-08 08:30 ET payroll release is -$30.0k; if the stop and target are not OCO at the exchange, a 15-minute window is -$34.5k at worst (2025-04-07 09:59), a 60-minute window -$72.9k (2026-03-23 06:14) and a full Asia-session outage -$345k (2.8x the HOLD episode; p01 across days -$69.3k).
5. Full-session outages with resting orders: asia -$1.75k mean, 1st percentile -$41.0k, worst -$58.0k (lost profit of the session); london -$0.2k / -$23.0k / -$42.8k; NY-AM -$0.7k / -$18.4k / -$37.0k; NY-PM -$12 / -$6.2k / -$14.0k.

## 1. Outage windows: scenarios (i) feed stops, (ii) platform down, (iv) NO resting orders (SYNTHETIC), (v) NON-OCO leg survives (SYNTHETIC)
Delta in $ vs the engine P&L, over EVERY trading-minute start 2023-04..2026-10 (the population; p01 = 1st percentile, i.e. the 99th percentile of the LOSS; worst = the minimum; best = the maximum gain from skipped losers); the last two columns are 1,000 random draws from the population (mean with its 95% interval, and the draw p01). share = windows with any change.
| scenario | N min | share nonzero | mean | p01 | worst | best | per outage-hour | random draws: mean (95%) | draws p01 |
|---|---|---|---|---|---|---|---|---|---|
| i feed stops (A+B+C) | 1 | 1.6% | -2 | +0 | -16.7k | +20.7k | -114 | -5 (-17 to +6) | +0 |
| ii platform down (A+B+C+D) | 1 | 1.6% | -2 | +0 | -16.7k | +20.7k | -114 | +15 (-5 to +34) | +0 |
| iv NO resting orders (A+B+C+F) | 1 | 2.9% | -1 | -76 | -30.0k | +20.7k | -90 | -15 (-36 to +7) | -180 |
| v NON-OCO leg survives (A+B+C+G) | 1 | 1.6% | -2 | +0 | -16.7k | +20.7k | -113 | -1 (-17 to +15) | +0 |
| i feed stops (A+B+C) | 5 | 7.3% | -10 | -2.5k | -17.0k | +21.3k | -115 | +23 (-24 to +71) | -1.3k |
| ii platform down (A+B+C+D) | 5 | 7.3% | -10 | -2.5k | -17.0k | +21.3k | -115 | +16 (-26 to +58) | -1.3k |
| iv NO resting orders (A+B+C+F) | 5 | 12.0% | -7 | -2.5k | -41.1k | +37.5k | -88 | +19 (-30 to +67) | -2.4k |
| v NON-OCO leg survives (A+B+C+G) | 5 | 7.3% | -10 | -2.5k | -17.0k | +21.3k | -116 | +24 (-8 to +56) | -1.2k |
| i feed stops (A+B+C) | 15 | 18.5% | -29 | -6.1k | -18.3k | +21.3k | -116 | +52 (-42 to +146) | -6.5k |
| ii platform down (A+B+C+D) | 15 | 18.5% | -29 | -6.1k | -18.3k | +21.3k | -116 | -13 (-91 to +66) | -5.5k |
| iv NO resting orders (A+B+C+F) | 15 | 27.6% | -22 | -6.5k | -46.8k | +43.7k | -86 | +16 (-71 to +103) | -4.9k |
| v NON-OCO leg survives (A+B+C+G) | 15 | 18.6% | -30 | -6.1k | -34.5k | +21.3k | -120 | -92 (-174 to -9) | -7.3k |
| i feed stops (A+B+C) | 60 | 44.1% | -112 | -12.1k | -32.2k | +21.9k | -112 | -44 (-216 to +129) | -10.9k |
| ii platform down (A+B+C+D) | 60 | 44.1% | -112 | -12.1k | -32.2k | +21.9k | -112 | -13 (-198 to +172) | -13.2k |
| iv NO resting orders (A+B+C+F) | 60 | 56.4% | -79 | -13.1k | -77.1k | +97.5k | -79 | +4 (-224 to +231) | -12.5k |
| v NON-OCO leg survives (A+B+C+G) | 60 | 44.4% | -114 | -12.2k | -72.9k | +51.3k | -114 | -107 (-298 to +83) | -11.8k |
Component means ($ per window) and worst windows by N (minutes 1 / 5 / 15 / 60): A new entries missed -1.91 / -9.66 / -29.18 / -111.56 (worst -$16.7k / -$17.0k / -$18.3k / -$32.2k); B time exit delayed +0.03 / +0.11 / +0.28 / +0.61 (worst -$4.7k); C cut or lock missed -0.01 / -0.06 / -0.18 / -0.72 (worst -$10.4k / -$10.5k); D orphan add 0.00 / 0.00 / 0.00 / -0.02 (worst -$1.4k at 60); F no resting orders +0.40 / +2.25 / +7.51 / +32.93 as a mean over all windows (SYNTHETIC; worst -$30.0k / -$41.1k / -$47.4k / -$72.8k); G non-OCO 0.00 / -0.04 / -0.87 / -2.81 (SYNTHETIC; worst -$2.7k / -$8.1k / -$32.7k / -$78.1k). ER-ladder lots are never 'missed': an outage removes whole entries (the ER multiplier is evaluated at the signal). Zone and the Q1-A multiplier follow the entry. Locks are re-evaluated only when the box is up; the 120 early-exit trades above contain both TH-L2 cuts and lock flattens (not separable in the engine record).

## 2. Worst placement (minimum over all starts)
| scenario | N min | worst | start (ET) | components at the worst window |
|---|---|---|---|---|
| i feed stops (A+B+C) | 1 | -16.7k | 2025-04-02 11:16 | A -16.7k, B +0, C +0, D +0, F +233, G +0 |
| ii platform down (A+B+C+D) | 1 | -16.7k | 2025-04-02 11:16 | A -16.7k, B +0, C +0, D +0, F +233, G +0 |
| iv NO resting orders (A+B+C+F) | 1 | -30.0k | 2024-03-08 08:30 | A +0, B +0, C +0, D +0, F -30.0k, G +0 |
| v NON-OCO leg survives (A+B+C+G) | 1 | -16.7k | 2025-04-02 11:16 | A -16.7k, B +0, C +0, D +0, F +233, G +0 |
| i feed stops (A+B+C) | 5 | -17.0k | 2023-09-20 18:12 | A -17.0k, B +0, C +0, D +0, F +0, G +0 |
| ii platform down (A+B+C+D) | 5 | -17.0k | 2023-09-20 18:12 | A -17.0k, B +0, C +0, D +0, F +0, G +0 |
| iv NO resting orders (A+B+C+F) | 5 | -41.1k | 2024-03-08 08:27 | A +0, B +0, C +0, D +0, F -41.1k, G +6.6k |
| v NON-OCO leg survives (A+B+C+G) | 5 | -17.0k | 2023-09-20 18:12 | A -17.0k, B +0, C +0, D +0, F +0, G +0 |
| i feed stops (A+B+C) | 15 | -18.3k | 2026-08-25 19:50 | A -18.3k, B +0, C +0, D +0, F +0, G +0 |
| ii platform down (A+B+C+D) | 15 | -18.3k | 2026-08-25 19:50 | A -18.3k, B +0, C +0, D +0, F +0, G +0 |
| iv NO resting orders (A+B+C+F) | 15 | -46.8k | 2026-03-30 20:34 | A +681, B +0, C +0, D +0, F -47.4k, G -2.2k |
| v NON-OCO leg survives (A+B+C+G) | 15 | -34.5k | 2025-04-07 09:59 | A -1.9k, B +0, C +0, D +0, F +0, G -32.7k |
| i feed stops (A+B+C) | 60 | -32.2k | 2026-06-23 01:08 | A -32.2k, B +0, C +0, D +0, F +0, G +0 |
| ii platform down (A+B+C+D) | 60 | -32.2k | 2026-06-23 01:08 | A -32.2k, B +0, C +0, D +0, F +0, G +0 |
| iv NO resting orders (A+B+C+F) | 60 | -77.1k | 2026-10-01 02:31 | A -16.6k, B +0, C +0, D +0, F -60.4k, G +0 |
| v NON-OCO leg survives (A+B+C+G) | 60 | -72.9k | 2026-03-23 06:14 | A +5.1k, B +68, C +0, D +0, F +87.3k, G -78.1k |
Worst windows for (i) / (ii) are always a skipped large winner (A), not a loss on an open position; the largest real loss placements are the SYNTHETIC ones.

## 3. Scenario (iii): disconnect before the entry fills complete (second resolution, all 24374 slice boundaries)
Events = a disconnect after k of ceil(c) slices (c contracts, 1 lot per 2 s) of every taken trade; protected = stop/target placed at each slice fill (the unfilled slices are lost); naked = stops placed after the full entry (the filled part runs unprotected until reconnect; if the library exit would have happened by reconnect it is replaced by a market exit at reconnect). Per event $:
| N min | events | protected mean | p01 | worst | naked mean | p01 | worst | share of events changed by naked | expected cost per outage-hour (protected / naked) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 24374 | -191 | -7.3k | -14.3k | -190 | -7.3k | -14.3k | 0.7% | -2 / -2 |
| 5 | 24374 | -191 | -7.3k | -14.3k | -187 | -7.3k | -14.3k | 7.6% | -0 / -0 |
| 15 | 24374 | -191 | -7.3k | -14.3k | -186 | -7.3k | -27.5k | 22.6% | -0 / -0 |
| 60 | 24374 | -191 | -7.3k | -14.3k | -229 | -10.3k | -42.2k | 54.1% | -0 / -0 |
The expected cost per outage-hour is tiny because the seconds in which entry slices are being filled are a tiny share of the 117 million seconds of the history; the worst-case placement (the disconnect at the moment of the largest entry) is the event worst above.

## 4. Full-session outages (every label day; all trades of the session lost / exits missed)
| session | scenario | days | mean | p01 across days | worst | best |
|---|---|---|---|---|---|---|
| asia (480 min) | i feed stops (A+B+C) | 963 | -1.8k | -41.0k | -58.0k | +29.3k |
| asia (480 min) | ii platform down (A+B+C+D) | 963 | -1.8k | -41.0k | -58.0k | +29.3k |
| asia (480 min) | iv NO resting orders (A+B+C+F) | 963 | -1.8k | -41.0k | -58.0k | +29.3k |
| asia (480 min) | v NON-OCO leg survives (A+B+C+G) | 963 | -2.0k | -69.3k | -345.2k | +176.3k |
| london (390 min) | i feed stops (A+B+C) | 963 | -234 | -23.0k | -42.8k | +23.5k |
| london (390 min) | ii platform down (A+B+C+D) | 963 | -236 | -23.0k | -42.8k | +23.5k |
| london (390 min) | iv NO resting orders (A+B+C+F) | 963 | -753 | -39.3k | -107.3k | +63.9k |
| london (390 min) | v NON-OCO leg survives (A+B+C+G) | 963 | -243 | -43.1k | -79.5k | +190.6k |
| nyam (150 min) | i feed stops (A+B+C) | 961 | -688 | -18.4k | -37.0k | +20.8k |
| nyam (150 min) | ii platform down (A+B+C+D) | 961 | -688 | -18.4k | -37.0k | +20.8k |
| nyam (150 min) | iv NO resting orders (A+B+C+F) | 961 | -454 | -31.5k | -77.1k | +43.0k |
| nyam (150 min) | v NON-OCO leg survives (A+B+C+G) | 961 | -669 | -32.0k | -76.5k | +51.5k |
| nypm (180 min) | i feed stops (A+B+C) | 961 | -12 | -6.2k | -14.0k | +12.5k |
| nypm (180 min) | ii platform down (A+B+C+D) | 961 | -12 | -6.2k | -14.0k | +12.5k |
| nypm (180 min) | iv NO resting orders (A+B+C+F) | 961 | +142 | -12.5k | -36.9k | +42.6k |
| nypm (180 min) | v NON-OCO leg survives (A+B+C+G) | 961 | -106 | -10.1k | -51.4k | +21.6k |
HOLD episode $122.0k for scale. The resting-order scenarios (i / ii) cost lost profits of the session (mean -$1.8k for Asia); the SYNTHETIC non-OCO case is the one that produces a large unwanted position count.

## 5. What the live code would do: UNVERIFIED, assumptions that need the user's confirmation
1. Are the stop and target submitted as EXCHANGE resting orders at fill time (per slice or only after the full 70% entry)? Everything in sections 1-4 for scenarios (i)-(iii) assumes yes. UNVERIFIED (the DS7 order-management code is not on this disk).
2. Are stop and target linked OCO at the exchange / broker, or two independent orders that the box cancels? If independent, an outage during which one leg fills leaves the other live (scenario v: up to -$72.9k at 60 minutes, -$345k for a full Asia session).
3. Does the broker session cancel working orders when the platform disconnects (cancel-on-disconnect / day-order handling)? If yes, scenario (iv) NO RESTING ORDERS applies to every disconnect: -$77.1k worst at 60 minutes and -$30.0k for a 1-minute outage at the wrong second.
4. The resting 30% add: is it an exchange limit order that the box cancels on exit (platform-down orphan, component D) or a box-side order?
5. Is the 16:55 flat / time exit box-side (a clock inside the platform) or exchange-side? In (i) and (ii) it is delayed to reconnect (component B).
6. After reconnect: does the platform reconcile positions, re-place missing stops, resume or cancel unfilled entry slices, and flatten positions it does not recognise? I assume lost slices and flat-at-reconnect for orphans.
7. Is there an FCM-level auto-liquidation or margin limit that acts during an outage?

## 6. Caveats
Trade-level counterfactuals on the 1-s path: no engine re-run, so lock state, ER state, ER-dependent lots and other books are not re-simulated after a missed entry or exit (a skipped trade changes later locks); the delta of a skipped trade is the engine net of that trade; the stress scenarios (iv) and (v) and the worst-window numbers are conditional on the assumptions in section 5 and are labelled SYNTHETIC; windows start on trading minutes of the 1-s path (the brief's random times are those minutes, uniform); 'full session' uses fixed session lengths in ET (asia 18:00 + 480 min, london 02:00 + 390, NY-AM 09:30 + 150, NY-PM 12:00 + 180); slippage costs as the engine (stop 2.45, market 0.80). The D component uses 2 candidates only.
