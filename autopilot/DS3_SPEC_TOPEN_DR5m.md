# DS3_SPEC_TOPEN_DR5m - NQ opening-drive pullback book "DR5m_pb1_rm0.5 X60_75": complete NT8 build spec (D3CFA, 2026-10-28)

Self-contained: someone who has not read the study should be able to code and test it in NT8 from this file alone. Research output for Sim / forward paper only. NOT a live recommendation: the cross-instrument replication (autopilot/DS3_CONFIRM_A.md) found it does NOT replicate on ES, YM or RTY (0 of 3), and it fails the program-level best-of-N; the NQ-only evidence is a lucky-fit risk. The study's parameter-level description is DS3_SPEC_TOPEN_DR5m_pb1_rm0.5_X60_75.md; this file removes every ambiguity found while porting the rule (identity check below).

## 0. One-paragraph plain-English description
Every day the first five minutes of the NQ cash session (09:30-09:34 ET) are looked at. If the market moved decisively in one direction over those five minutes (net open-to-close move at least half of the typical 5-minute opening range of the previous 20 days), the strategy waits for the first 1-minute bar that closes against that move (the first small pause or pullback, any time from 09:35 up to 10:29) and, when that bar closes, buys (after an up-drive) or sells (after a down-drive) at market in the direction of the original drive. It then places a protective stop 60 points away and a profit target 75 points away; whichever is hit first ends the trade, and if neither is hit by 16:00 ET it exits at market. At most one trade a day, 10 contracts, no re-entry.

## 1. Platform setup
- Instrument: NQ front month (continuous contract, NT8 merge-back-adjusted or the same expiry for the whole day; on roll day use the new front month for the entire day). Tick 0.25 (= $5.00), point value $20.
- Chart: 1 Minute bars, Calculate = On bar close, Bars period type Minute/1, session template that contains the full 09:30-16:00 ET RTH (ETH template is fine; the logic below only uses the RTH bars). Chart time zone / strategy time = US Eastern (America/New_York, DST aware). All times below are ET.
- **Bar time convention**: NT8 stamps a bar with its CLOSE time. The study labels a bar by its OPEN time. "The 09:30 bar" = the minute 09:30:00-09:30:59 = the bar with `Time[0] = 09:31:00` in NT8. This file uses OPEN time with the NT8 stamp in brackets: bar 09:30 [NT stamp 09:31], bar 09:34 [09:35], bar 10:29 [10:30].
- Entry mode: Strategy with `EntriesPerDirection = 1`, `EntryHandling = AllEntries`, `IsExitOnSessionCloseStrategy = false`, `TimeInForce = Gtc`, `StopTargetHandling = PerEntryExecution`, `OrderFillResolution = Standard` (live logic uses only completed 1-min bars).

## 2. State kept per ET calendar date
- `rng5[date]` = (max High of the five bars 09:30, 09:31, 09:32, 09:33, 09:34) - (min Low of the same five bars), stored once the 09:34 bar [NT stamp 09:35] has closed, only if all five bars exist. Keep the last 20 such stored values of earlier dates (sliding window of the previous 20 sessions that have the five bars; holidays and days with missing bars are simply not stored).
- `Median5` = median of those stored values for the previous sessions (not including today). Valid only if at least 10 values are stored (the standard window is 20; with 10-19 values use what exists). Warm up the buffer from history (>= 20 trading days) before the first live day.
- `tradedToday` flag (reset at the first bar of each ET date).

## 3. Signal (evaluated once, on the close of the 09:34 bar [NT stamp 09:35:00])
1. Require the five bars 09:30-09:34 of today to exist (no gap).
2. `move = Close(09:34 bar) - Open(09:30 bar)`; `M5 = |move|`. If `move == 0`: no trade today.
3. `D = +1` (long) if `move > 0`, `-1` (short) if `move < 0`.
4. If `Median5` invalid (fewer than 10 values): no trade. If `M5 < 0.5 * Median5`: no trade (this filter passes on about 45 percent of days). Nothing else filters (no gap, no news/FOMC, no VIX filter, no day-of-week filter).
5. Otherwise the day is armed. Put today's `rng5` in the buffer after evaluating the signal (the median used today excludes today).

## 4. Entry (first 1-minute pullback bar, "pb1")
- Scan completed 1-minute bars with OPEN time 09:35, 09:36, ..., 10:29 (NT stamps 09:36 ... 10:30), in that order, each evaluated at its close (OnBarClose).
- The first bar whose close is AGAINST the drive is the pullback bar: for a long drive `Close < Open`; for a short drive `Close > Open`. (A doji with Close == Open is NOT a pullback bar; the bar must close strictly against the drive.) The scan is on the bar's own open and close only; no body-size or volume condition.
- On that bar's close (the OnBarClose call) submit ONE market order in the drive direction, 10 contracts: `EnterLong(10)` after an up-drive, `EnterShort(10)` after a down-drive. In the study it fills at the open of the next bar (the live stack submits at the bar close + 1 second).
- The latest possible pullback bar is the 10:29 bar [NT stamp 10:30:00]; if no bar from 09:35 to 10:29 closes against the drive, there is no trade today. So the latest entry is at about 10:30:00. A pullback bar is never accepted from 10:30 on.
- One entry per day: after the order is sent (or the scan ends without one) `tradedToday = true`; no re-entry after a stop or target, no second pullback.
- If a gap > 30 minutes in data occurs between the pullback bar and the next bar, do not enter (cannot happen in normal RTH).

## 5. Exits (set when the entry fills, from the actual average FILL price `F`)
- Stop: `F - 60.00` points for a long (`F + 60.00` short) = 240 ticks. In NT8: in `OnExecutionUpdate` for the entry fill (or managed `SetStopLoss(CalculationMode.Ticks, 240)` before the entry), a stop-market order for the full 10 contracts.
- Target: `F + 75.00` points for a long (`F - 75.00` short) = 300 ticks, a limit order for the full 10 contracts (`SetProfitTarget(CalculationMode.Ticks, 300)`). Stop and target are OCO; no trailing, no break-even, no scaling, no partials.
- Time exit: if neither has filled, cancel both and exit at market at the close of the 15:59 bar (= 16:00:00). NT8: in OnBarClose when `Time[0].TimeOfDay >= 16:00:00` (stamp of the 15:59 bar) and `Position.MarketPosition != Flat`: `ExitLong/ExitShort`. This is the study's harness exit (the large majority of trades end on stop or target before then: about 48 percent stop, 50 percent target, 2 percent time exit).
- The live stack also has a hard flatten at 16:55 ET (stack rule); it never binds on this book.
- Early-close days (13:00 cash close): the same rules; a position still open at the last bar is closed at market (the 13:00 close).

## 6. Sizing and lock rules (stack-level, not tested in the replication)
- Lots 10 (per-book unit R = lots x stop x $20 = $12,000). Per-book locks as the stack's per-book rules: day entry test -2R / +5R realised (no new entry if the book's day realised P&L is <= -2R or >= +5R: one trade a day so this is moot for this book alone); day give-back arm 2R, keep 50 percent; week floor -12R (stop the book for the rest of the ISO week if the week's realised P&L <= -12R). 2.7 percent of historical trades would exceed the 50-contract total cap with the other books open; the cap rule of the stack applies (take what the cap allows, else 0).
- The replication study used equal $1,000 risk per trade instead of 10 lots; dollar figures there are not comparable to the spec's 10-lot numbers.

## 7. Worked example (long)
09:30 bar opens 21,000.00; the 09:34 bar closes 21,022.00: `move = +22.0`; Median5 = 40.0, `M5 >= 0.5 x 40 = 20` so armed, D = long. Bars 09:35 (close 21,024 > open 21,020), 09:36 (close 21,026 > open 21,024), 09:37 close 21,021.5 < open 21,026: pullback bar. At the 09:37 bar close send buy 10 market; suppose fill 21,021.75: stop 20,961.75, target 21,096.75. Exit by whichever fills first, else market at 16:00.

## 8. What the study measured and how to compare a Sim run
- Study harness (NQ L2 replay, 2024-02..2026-10-16, 10 lots): about 2.3 trades per week, win rate 0.53-0.54, PF 1.36-1.40, $4.7k-5.3k/week standalone (see the older spec for the table), forward weeks to settle about 120-190.
- Port check (D3CFA, 2026-10-28): an independent bars-only implementation of Sections 2-4 reproduces the study event list on NQ exactly: 430 of 430 common days with identical side and identical entry minute (518 events for 2022-06..2026-10-16 vs 432 for the study's 2023-02-10..2026-10-16 window; the 86 extras lie in the 2022 warm-up; the study has one more day early in the window, 2023-02-24, and one after the data end, not reproduced and not investigated; the study median starts at its own 2023-02-10 start whereas the port used the 2022 warm-up). Daily trades per week 2.29 in both.
- Costs: market entry 1 tick adverse, stop fill 2 ticks adverse, target limit fills only on a 1-tick trade-through, fee $4.84 per contract round trip (FEES.md, NQ proxy). In Sim, log per trade: date, drive direction, M5, Median5, pullback bar time, entry fill, stop/target/time exit, points.

## 9. Open items for the Sim leader (none change the rule)
- The 09:30 bar open of the NT8 chart must be the first RTH trade (not the ETH 09:29 bar): verify the bar stamped 09:31 has Open equal to the cash open print.
- Median5 must be computed from the same 1-minute bar source (not the 5-minute series) to match the study to the tick.
- Margin: the 57-lot stack-plus-cell peak implies about $1.2M on the study's 5 percent-of-notional proxy against a $700k account; confirm broker intraday NQ margin before any sizing (D3O1 flag).
- Evidence status: forward register only. Replication on ES/YM/RTY failed (DS3_CONFIRM_A.md): WF $/wk per $1k risk ES +55, YM -114, RTY -162 versus NQ +443; the NQ-only result is the in-sample row.
