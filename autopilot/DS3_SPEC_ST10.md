# DS3_SPEC_ST10 - the live DS2 ST book as a DS3 candidate: rule, identity statement, per-book dollars (D3X, 2026-10-26)

Research output for the Sim leader; NOT a live recommendation. No change to DualStrat/DualStrat2 or any chart. Source of the rule: outputs/h2/DualStrat.cs (class DualStrat, ComputeEngine / OnBarUpdate / TradingBlockedNow; live parameters of the ST book as in ds2lib / REPORT_ASSEMBLY: ST 10 lots, stop 60, target 1.0R). The live DualStrat2 file itself was not re-read; where the live window parameters differ from the h2 defaults (see 2) they were inferred from the benchmark rows and flagged.

**Verdict: DELIVERABLE (it is already an NT8 strategy: 1-minute chart, OnBarClose signal, bracket at the broker, no L2).** Identity: box replay vs library benchmark trade rows (pairP/ROWS_bench3.parquet, book ST, 2023-02-10..2026-10-16, 8233 trades): **1.07% entries mismatch, 1.40% mismatch on entry + exit time + exit type, 1.21% with a +/-2 min exit tolerance** (limit 2%). The DS2 series used in the portfolio (DS2_daily.parquet pnl_ST) additionally contains the P9 execution mapping (see 5); that layer is NOT re-derived here.

## 1. Rule (NT8, as coded)
- **Instrument / bars:** NQ front month on a 1-MINUTE chart (NT8 bar time = bar END time). Session template: CME US Index Futures full session; ET clock (UseEasternDstAuto). Calculate = OnBarClose; BarsRequiredToTrade 250; engine primed on history, no historical-bar trading in real time.
- **Indicator:** Supertrend flip, ATR period **120**, multiplier **2.0**, source = **Close** (not median price). TR = max(H-L, |H-C[1]|, |L-C[1]|). ATR: for bars 0..119 the running mean of TR, afterwards Wilder RMA (ATR = (ATR[1]*119 + TR)/120). basicUp = Close - 2.0*ATR, basicDn = Close + 2.0*ATR; finalUp = (Close[1] > up[1]) ? max(basicUp, up[1]) : basicUp; finalDn = (Close[1] < dn[1]) ? min(basicDn, dn[1]) : basicDn. Trend starts +1; if trend[1] = -1 and Close > dn[1] -> +1; if trend[1] = +1 and Close < up[1] -> -1; else unchanged. A flip is the bar on which the trend changes.
- **Filter:** EMA(**200**) of Close (alpha = 2/201, seeded with the first close). BuyFlip = flip up and Close > EMA; SellFlip = flip down and Close < EMA. A flip rejected by the EMA filter is NOT retried (the trend state moves on).
- **Entry:** book flat, no order pending, not halted (per-book day/week), not time-blocked: market order at the close of the flip bar (fills at the next bar open in the model), qty 10 for DS2/DS3 scale (14 at Set A scale). One position; opposite flips while in a trade are ignored (no reversal exit).
- **Exit:** OCO bracket from the fill: stop-market 60 pt, target limit 60 pt (1.0R). TimeBlock exit: market at the close of the bar whose end time is >= 16:55 ET (FlattenAtHHmm 1655), and at the close of the final bar on CME early-close days. No trade-health exit (StThOn false in the benchmark), no trailing.
- **Session window (ET):** entries allowed for flip bars whose END time is from 18:01 to 15:01 (replay-inferred: the benchmark rows contain no entry whose signal bar starts between 15:01 and 17:59 ET and do contain entries from signal bars starting at 18:00); per h2 defaults the guard windows are GuardAsia/GuardNy blocks plus the 16:55 flatten - confirm against the live DualStrat2 properties before coding. Flat by 16:55 ET (also covered by NT8 exit-on-close as backstop); the book re-enters from 18:00.
- **Order types:** MARKET entry, STOP-MARKET + LIMIT target (OCO), MARKET time-block exit; unmanaged orders tagged ST_*.
- **Lots / dollars:** 10 NQ lots, R = 10 x 60 x $20 = $12,000. Per-book locks (realised, as live): day -2R = -$24,000, day +5R = +$60,000; give-back arm +2R = $24,000 keep 50% (combo level: once the book's day P&L has peaked at >= $24,000, stop for the day when it falls to 50% of the peak); week floor -12R = -$144,000 (the h2 file has ST weekly loss $57,600 at 8 lots, superseded by the DS3 per-book rule); cap off. At the 14/14 scale R = $16,800: -$33,600 / +$84,000 / arm $33,600 / floor -$201,600.
- **Execution mode:** existing strategy, Market entry and Native stop by default. The DS2 series assume the P9 execution policy (S14x1 slicing at 2 s gaps, passive stop-join with 3 s wait, 20 pt catastrophe stop; autopilot/P9_NT8_SPEC.md): this needs OnMarketData timers (second-level, not sub-second) and is UNVALIDATED live; with default Market/Native execution the realised cost is higher than the series assume.

## 2. Identity test
| check | n library | n replay | mismatches | % |
|---|---|---|---|---|
| entries (time, side) | 8233 | 8234 | 88 | 1.07 |
| entry + exit time + exit type | 8233 | 8234 | 115 | 1.40 |
| entry + exit type, exit within 2 min, pts within 0.5 | 8233 | 8234 | 100 | 1.21 |
Replay: x_st10.py (own loader, own online engine, back-adjusted 2013+ 1-minute files, engine started 2022-06-01). Differences: 13 bars in which stop and target both fall inside one 1-minute bar (the replay takes the stop; the benchmark resolved ties with the 1-second tape) and exit stamps one minute apart (second-resolution fills), plus holiday early closes (the replay uses the calendar derived from the data). Entry window start/end were inferred from the library rows. The replay covers the base trade rows only; the P9 point mapping, per-book locks and the 1-second lock engine of the DS2 series are not re-derived (not re-derived here; the lock arithmetic for T-B books was re-implemented separately in x_locks.py).

## 3. Data, roll, holidays
Continuous front NQ, back-adjusted (MergeBackAdjusted in NT8; the Supertrend and EMA run continuously across days, so the adjusted history matters). The book is flat from 16:55 to 18:00 ET so no trade crosses the quarterly roll; the benchmark drops no roll trade. Holidays/half days: no bars -> no trades; early-close days flatten at the final bar (13:00 / 13:15 ET; Good Friday 09:15 ET).

## 4. Position limits
10 lots, one position. DS2 + DS3 concurrency is the lead's computation (50-contract limit); note 10 ST + 10 HM + 7 WT = 27.

## 5. Costs and fills
Live cost model in the DS2 series: $4.84/contract RT plus the P9-mapped execution points (the mapping replaces the plain 0.995/1.01 model). Stop/target fills in the base rows are exactly +/-60 pt (no slippage) before mapping.

## 6. Backtest expectation (DS2_daily.parquet pnl_ST: ST10 with per-book locks, from the ASSEMBLY engine, live cost; weekly $)
| window | mean/wk | SD | maxDD (running peak in window) | worst week |
|---|---|---|---|---|
| WF 2024-02..2026-10 (142 wk) | 14,350 | 57,331 | 217,475 | -91,189 |
| WF-PRE (75 wk) | 12,242 | 52,834 | 188,070 | -88,671 |
| HOLD 2025-07+ (68 wk) | 16,463 | 61,612 | 217,475 | -91,189 |
| IS 2023-02..2024-01 (52 wk) | 4,660 | 46,264 | 218,808 | -80,106 |
| L8W | 22,235 | 96,747 | - | -86,384 |
Trades/week (after locks, WF): 26.0. Weekly correlation in WF: with HM10 0.41, with WT7 0.43. Win rate / average win / loss: base rows have target 4135, stop 3859, TimeBlock 315 of 8309 (win rate about 50% with symmetric +/-60 before the time-block exits); per-lot +/-$1,200 gross per target/stop.

## 7. What could kill it
- It is the live book: its edge is the period-specific ST/EMA flip trend; the benchmark's per-book timing placebo rank is 0.68 (D3L census), i.e. not distinguishable from random timing at the 0.95 bar.
- Execution: the series assume the P9 mapping (slicing + stop-join); default Market/Native execution is worse; slicing is unvalidated on the live copier.
- 1-minute bar assumptions: ties and second-level ordering inside a bar (13 tie bars in the replay), data-gap bars, vendor-vs-NT8 bar differences.
- Lock engine semantics (MTM vs closed-trade) and the 50-contract/margin interaction with other DS3 books.
