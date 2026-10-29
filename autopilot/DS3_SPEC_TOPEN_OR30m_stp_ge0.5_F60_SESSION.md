# DS3_SPEC_TOPEN_OR30m_stp_ge0.5_F60_SESSION - NQ 30-minute opening-range stop-entry break "OR30m_stp_ge0.5 F60": complete NT8 build spec (D3SOB, 2026-10-29)

Self-contained: someone who has not read the study should be able to code and test it in NT8 from this file alone. Research output for Sim / forward paper only; NOT a live recommendation. Reconstructed from the code that generated and scored it: **cell definition** code/open2/f31_or.py (OR, stop-entry `stp`, condition `ge0.5`, scan window; day_events/build/make_variant(30,'stp','ge0.5')), code/open2/f_common.py (1-min bars, OR range, 20-day median), code/open2/o2_gen.py (entries() stop-entry branch, legs() F60 bracket, 16:00 time exit), **session window and lots** code/sb1/sb1_surv.py, **MEASURED replay** code/ssa_direct.py (V0) with code/ssq/ssq_prep.py and ssq_score.py (wave q1). Every number below is in that code or in the cell name. NOTE: the 30-minute OR makes every entry fall at or after 10:00:00, so this cell NEVER trades inside the 09:00-09:59 block of the live books.

## 0. One-paragraph plain-English description
Every day the high and low of the first 30 minutes of the NQ cash session (09:30-09:59 ET) are recorded. If that opening range is at least half as wide as the typical 30-minute opening range of the previous 20 days, then from 10:00:00 ET the strategy waits for price to trade one tick beyond either end of the range: a buy-stop one tick above the range high and a sell-stop one tick below the range low are both live until 10:30:00. The first one touched is filled (the other is cancelled) and the trade goes with the break. A protective stop 60 points away and a profit target 60 points away are placed; whichever is hit first ends the trade, and if neither is hit by 16:00 ET it exits at market. At most one trade a day, no re-entry.

## 1. Platform setup
- Instrument: NQ front month (continuous; the same expiry for the whole day; on roll day the new front month for the entire day). Tick 0.25 ($5.00), point value $20. The study price space is library back-adjusted with a per-day offset on 15 roll days (code/open2/o2_core.off2); NT8 trades the unadjusted contract, so OR_H / OR_L are computed from the day's own contract bars.
- Series: 1 Minute bars (OR and median) plus tick-level (or at least 1-second) trade data for the stop trigger: the study detects the break on 1-second high/low of printed trades. Calculate = On each tick (or OnBarClose for the 09:59 bar plus working stop orders, which is equivalent because the orders are exchange-side). Session template with the full 09:30-16:00 ET RTH; time zone America/New_York.
- **Bar time convention**: NT8 stamps a bar with its CLOSE time; the study labels bars by OPEN time. The 09:30 bar has `Time[0] = 09:31:00`; the 09:59 bar has `Time[0] = 10:00:00`.
- Strategy settings: `EntriesPerDirection = 1`, `EntryHandling = AllEntries`, `IsExitOnSessionCloseStrategy = false`, `TimeInForce = Gtc`, `StopTargetHandling = PerEntryExecution`.

## 2. State kept per ET calendar date
- `rng30[date]` = (max High of the thirty 1-min bars 09:30..09:59) - (min Low of the same thirty bars), stored once the 09:59 bar has closed, only if the day qualifies. Keep the last 20 stored values of EARLIER dates (sliding window); `Median30` = median of that buffer (today excluded), valid only with >= 10 stored values (with 10-19 values use what exists; code: f_common.or_median(30, 570) = shift(1).rolling(20, min_periods=10).median() over the study's qualifying-day list). Warm the buffer from history (>= 20 trading days) before the first live day.
- Qualifying day (code f_common.rth_days): the 1-min bars 09:30..09:59 all exist with a Close (a gap disqualifies the day for trading and for the buffer); the study sample starts 2023-02-10.
- `tradedToday` flag.

## 3. Condition (evaluated once, at 10:00:00 ET, after the 09:59 bar has closed)
1. `OR_H = max High`, `OR_L = min Low` of the 09:30..09:59 bars (1-min bars). Require `OR_H > OR_L`.
2. `ratio = (OR_H - OR_L) / Median30`. Armed only if `ratio >= 0.5` (cell suffix `ge0.5`). If Median30 is invalid (fewer than 10 stored values): no trade. Nothing else filters (no gap, news, VIX, day-of-week).

## 4. Entry (stop-entry, `stp`)
- At 10:00:00 place two OCO stop orders: **buy stop at `OR_H + 0.25`** (one tick above the range high) and **sell stop at `OR_L - 0.25`** (one tick below the low). Study rule (code f31_or.py `etype=='stp'`): the break is the first 1-second bucket from 10:00:00 in which the second's printed high >= `OR_H + 0.25` (long) or printed low <= `OR_L - 0.25` (short); the scan covers the seconds 10:00:00..10:29:59 only (scan end = origin + max(60, 30 + 30) = 60 minutes after 09:30).
- If both triggers fall in the same 1-second bucket the study takes NO trade that day (code: `if a==b: return None`). NT8 would fill whichever order triggers first inside that second; this is a known, rare mismatch (open item).
- Cancel both orders at 10:30:00 if neither has filled. When one fills, cancel the other. No re-entry after a stop or target (`reentry = 'none'`).
- Study fill models: harness basis M fills at the level + 1 tick; basis T at the first print at/after the level + 1 tick. The MEASURED replay (D3SQ wave q1, V0) did **not** replay a resting stop order: it sent a MARKET order at the stored break second with 1 tick adverse entry slippage. A real stop-market order triggers at `OR_H + 0.25` and fills at that price or worse; the difference is not measured. (Replay stored entry second: see identity table.)
- Entry times (PRE): first 10:00:00, median about 10:01, last 10:29; all entries are >= 10:00:00, none in 09:30-09:59.

## 5. Exits (set when the entry fills, from the actual FILL price `F`)
- Stop: `F - 60` points for a long (`F + 60` short) = 240 ticks, stop-market, full size. Target: `F + 60` points (`F - 60`) = 240 ticks, limit, full size. OCO; no trailing, no break-even, no scaling. Stop first if both reachable inside one second.
- Time exit: if neither has filled, cancel both and exit at market at 16:00:00 ET (study `tl = 16:00`). On early-close days close at the last bar. The live stack's 16:55 flatten never binds.
- MEASURED-basis costs (V0): entry 1 tick adverse, stop-market walks the displayed book (measured stop slippage in PRE for this cell: mean 0.31 pt per stopped trade), target limit at touch plus the measured P9 Target correction by year (2023 -1.44, 2024 -1.53, 2025 -4.21, 2026 -4.32 pt on target exits), commission $4.84 round trip per contract (FEES.md NQ proxy = 0.242 pt).

## 6. Sizing and locks
- Risk unit $1,000 per trade at the stop: exact lots = 1000 / (60 x 20) = **0.833 NQ**; the study's replayed lot class is **1 NQ** ($1,200 risk on 1 contract). MNQ conversion (NOT replayed, arithmetic only): 8 MNQ ~ 0.8 NQ; fee $1.78 per MNQ round trip (FEES.md); the stop-fill model was measured on NQ.
- O6 scoring locks (x_locks, closed-trade): R = $1,000; no new entry at day realised <= -2R or >= +5R; give-back arm 2R keep 50 percent; week floor -12R. Moot for one trade a day.

## 7. Worked example (long)
09:30-09:59 range: high 21,040.00, low 20,985.00 (width 55.0); Median30 = 80.0; ratio 0.69 >= 0.5: armed. At 10:00:00 buy stop 21,040.25 and sell stop 20,984.75 are placed. At 10:07:12 price prints 21,040.25: the buy stop fills at about 21,040.50 (1 tick slip); the sell stop is cancelled; stop 20,980.50, target 21,100.50; exit at the first of those, else market at 16:00. (Illustrative numbers.)

## 8. What the study measured (points are NET per trade, MEASURED V0, commission included)
- Cluster 277; **pool rank 1 of 30** by MEASURED PRE t (3.99) and the single best cell of the O6 solve. PRE (2024-02-01..2025-06-30): 297 trades, 3.96/wk, hit 0.630 (stop 37 pct, target 62 pct, time 2 pct), mean net +13.31 pt; weekly at $1,000 risk +$878 (SD $1,905, MDE $616, t 3.99). X (2023-04-03..2024-01-31): 172 trades, 3.91/wk, hit 0.529, mean +1.62 pt (weekly t about 0.4: not distinguishable from zero). HOLD (D3SQ look 2): 5.38 pt [-5.21, 15.97], MDE 14.54, H25 3.18 / H26 15.14, beta (flip) HOLD -2.98, edge HOLD +8.37; break-even extra slippage PRE 13.31 / HOLD 5.38 pt. HOLD CI includes zero. Source tier SESSION-CANDIDATE (stored basis HOLD 4.44).
- O6 HOLD (this task, one look, weekly $ at $1,000 risk, 32 weeks): +$350/wk (CI [-335, 1,036], MDE 941); X +$105/wk (CI [-435, 646], MDE 750). Both inside the MDE.
- Identity data (replay entries, ET): PRE n = 297; first PRE entries [('2024-02-01 10:00:00','S'), ('2024-02-05 10:01:23','S'), ('2024-02-06 10:00:00','S')]; last PRE [('2025-06-26 10:00:08','L'), ('2025-06-27 10:00:00','L')]. X n = 172; first X [('2023-04-03 10:22:51','L'), ('2023-04-04 10:00:01','L'), ('2023-04-05 10:04:27','S')]; last X [('2024-01-30 10:00:04','S'), ('2024-01-31 10:13:52','S')]. Port check NOT performed in this task.

## 9. Evidence status and open items
- Status (autopilot/DS3_SESSION2_Q_OPEN_BOOK.md): single best cell of the pool on PRE; the PRE-selected 3-cell book containing it is DEAD (failed G3 beta, G8 2023 check, G9 best-of-N).
- The source-harness random-direction bracket-beta gate (beats_beta) for this cell is **no** (fails). Treat as a candidate for a forward register only.
- Open: (a) tick/second data for the stop trigger, NT8 stop-market fill vs the replay's market-at-break model; (b) same-second double trigger; (c) Median30 from the same 1-min bars; (d) buffer skips days with a missing first-30-minute close; (e) price space (library back-adjusted vs NT8 contract); (f) fee proxy and margin as in the other specs.
