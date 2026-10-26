# DS3_SIM_TE7_kelt3m_n14_m1.0 - 2-week Sim-leader spec (D3X, 2026-10-26)
Parameter-level spec for a Sim run; NOT a live recommendation (anything run goes to the Sim leader first). Rule text is the DS3_SPEC_TE7_kelt3m_n14_m1.0.md rule (identity vs library 8504 trades, full-match mismatch under 2%); the section below repeats it.

## A. Chart / data series
NQ front-month continuous (MergeBackAdjusted), Globex ETH template (18:00 ET label day), primary series 3-min bars (+1-min series); add a 1-minute NQ series (Calculate OnBarClose, bracket and next-minute-open entry read the 1-min series). Time zone Eastern with DST auto. Tick replay off. Account: separate Sim account (no netting or locking with DS2/Set A). Start on a Sunday 18:00 ET so the first label day is complete; warm-up 3 trading days of history loaded (indicators need >=250 bars; the Supertrend/EMA/ATR state is continuous so load history, do not start flat-state mid-session).

## B. Rule (from the DS3 spec)
## 1. Rule (NT8)
- **Bars:** NQ 3-minute time bars (:00/:03/...), END-time stamped in NT8.
- **Indicator:** Keltner break: mid = EMA(Close, 14) (alpha 2/(n+1), seeded with the first close); ATR(10) with first value H-L and recursion ATR=(ATR[1]*9+TR)/10; upper = mid+1.0*ATR, lower = mid-1.0*ATR.
- **Signal:** Buy signal on the first bar whose Close is above upper (previous bar not above); sell signal on the first bar whose Close is below lower (previous bar not below); each side edge-triggered independently. The signal is read on the CLOSED bar (Calculate OnBarClose).
- **Entry:** market order at the open of the next 1-minute bar after the signal bar closes (the next 1-min bar must exist, i.e. no gap). Signals whose bar's last minute starts in 15:00-17:59 ET are ignored. One open trade at a time per book: signals while the book is in a trade (or on the exit minute) are dropped, not queued. 10 lots as 10 x 1-lot market slices 2 s apart (S10x1_g2) in the direct pricing.
- **Exit / bracket:** stop-market 60 pt and limit target 60 pt (1.0R) OCO from the entry (rows: from the entry bar's open; direct replay: 240/240 ticks from each slice fill); stop exits are worked as touch-join for 3 s then market (XJ3). Flat at 16:55 ET (market at the close of the bar ending >= 16:55; early-close days at the final bar). If both levels fall in one 1-min bar the replay takes the stop (the library uses the 1-s tape).
- **Session window (ET):** entries 18:00-14:59 ET (signal bars ending in the 15:00-17:59 window are blocked; the lock engine also blocks entries 18:00-18:05 and 15:00-16:54). Flat by 16:55.
- **Order types:** MARKET entry (sliced), STOP-MARKET + LIMIT target OCO, MARKET time exit; stop-join is a timer that replaces the stop with a passive limit for 3 s (P9 mechanism, see autopilot/P9_NT8_SPEC.md; unvalidated live, needs OnMarketData bid/ask).
- **Lots / dollars:** 10 NQ lots, R = 10 x 60 x $20 = $12,000. Per-book locks (exact 1-s mark-to-market engine in the series): day -2R = -$24,000, +5R = +$60,000; give-back arm +2R = $24,000 keep 50%; week floor -12R = -$144,000; cap off. At the 14/14 scale (R = $16,800, 14 lots): -$33,600 / +$84,000 / arm $33,600 / week floor -$201,600.
- **Execution mode:** NT8 strategy on a 3-minute NQ chart (a 1-minute data series is needed for the entry and bracket), OnBarClose; own per-book lock group. With default Market/Native stop execution the realised cost is higher than the direct-L2 series assume.


## C. Order handling: two modes
- **Mode 1 (default, plain): Market entry of the full 10 lots at the next 1-min open, OCO stop-market 60 pt / limit target 60 pt placed at the fill (stop and target from the FILL price; the box rows use the entry-bar open, the difference is the entry slippage), Market exit at 16:55 and on signal-free time exit.** Cost assumption in the box model for this mode: 0.995 pt per market order, 1.01 pt through a stop, $4.84 RT per contract. Realised results will be worse than the direct-L2 series, which assume Mode 2.
- **Mode 2 (optional layer, unvalidated live): S10x1_g2 + XJ3.** Entry as 10 market orders of 1 lot, the first at the next-minute open and then one every 2.0 s (tick-time timer, SubmitOrderUnmanaged, tag Tag_Entry; slices stop being sent if the book is flat-requested or the bracket exit fires). Each slice carries its own 60/60 OCO from its own fill (28 working orders alternative: one OCO on the net position is NOT what was replayed). Stop exits: on a trade print at/through the stop level, cancel the target, join the passive side (long exits at the best ask) for 3.0 s, then cancel and market the remainder; native StopMarket stays as a +20 pt catastrophe stop. See autopilot/P9_NT8_SPEC.md sections 1-3. Needs bid/ask via OnMarketData. Run Mode 1 first for week 1 and Mode 2 for week 2 only if Sim fills look sane.
- Per-book locks, evaluated live in the strategy: day realised -2R / +5R stop new entries; give-back arm at +2R day P&L, flatten and stop the day when it falls to 50% of the peak; week floor -12R: flatten and stop for the week; cap off. Entry blocks 18:00-18:05 and 15:00-16:54 ET.

## D. Lots and dollars
| scale | lots | R = lots x 60 x $20 | day -2R | day +5R | give-back arm (+2R) | week floor (-12R) |
|---|---|---|---|---|---|---|
| DS2 book scale | 10 | $12,000 | -$24,000 | +$60,000 | $24,000 keep 50% | -$144,000 |
| 14/14 scale | 14 | $16,800 | -$33,600 | +$84,000 | $33,600 keep 50% | -$201,600 |
Sim minimum viable run: 1 lot (R = $1,200; scale every dollar above by 0.1); the expectations below scale linearly.

## E. Expectation (box WF 142 weeks, 10 lots, direct-L2 pricing, exact locks; l2vast/ds3/out/te/direct_daily.parquet column TE7_kelt3m_n14_m1.0)
| mean $/wk | SD $/wk | trades/wk | win rate | WF at 2x cost $/wk | HOLD $/wk | 2023-04..24-01 $/wk |
|---|---|---|---|---|---|---|
| 16,863 | 59,362 | 26.8 | 52% | 12,395 | 12,885 | 6,365 |
Per-trade: avg win about +$11.2k, avg loss about -$11.0k at 10 lots (60-pt bracket). At 1 lot divide by 10. Mode 1 (plain Market/Native) will earn less than this table; the 2x-cost column is the better planning figure for Mode 1.

## F. What 2 weeks can and cannot say
- **Power:** 2-week mean has SE about $41,976 at 10 lots (SD 59,362/sqrt 2) against an expected mean of $16,863/wk: the mean CANNOT be confirmed or rejected in 2 weeks (a P&L within about +/-69k of expected, 90%, carries no information). Do not retire or promote on P&L.
- **What it can check (pass/fail):**
  1. Trade count: expected about 54 trades in 2 weeks (Poisson SD about 7); PASS if within 39-68; locks reduce it on bad days.
  2. Entry reconciliation: >= 95% of Sim entries match the box replay's entries (same signal bar, side, within one 1-min bar); every miss explained (data gap, lock, desync, rejection). Below 90% = rule not reproduced (FAIL).
  3. Bracket: 100% of entries carry both stop and target at 60 pt within 1 s of the fill; exits at 16:55 flat (no position at 17:00).
  4. Fill slippage vs model: mean market-entry slippage <= 1.0 pt (Mode 1; model 0.995) and stop-exit slippage <= 1.5 pt; Mode 2: mean slice-entry cost <= model (see box direct replay) + 0.5 pt, no more than 3 bar-misses. A mean slippage above 2 pt per market order FAILS the cost model regardless of P&L.
  5. Lock events: day -2R / +5R / give-back / week floor fire at the stated dollar levels (log each with time and P&L); no entries inside 18:00-18:05 / 15:00-16:54.
  6. Hard stops on the Sim: any week worse than the week floor, or any position left open after 16:57 = FAIL and stop the run.
- Diagnostic only (no verdict): sign and size of weekly P&L vs the box replay's P&L for the same weeks (replay pts x lots minus cost).

## G. Daily checklist for the Sim leader (reconcile against the box replay)
1. Before the open: confirm chart series, session template, contract (front month) and that the strategy shows 3 days of history; log the contract roll date if within 8 days.
2. After 17:00 ET: export the trade log (entry/exit time, price, side, lots, exit reason, slippage vs the signal bar's next-open print, lock events) to the daily push.
3. Ask the box for the replay file for that label day (x_te.py run on the day's 1-minute bars; entries list with time, side, bracket outcome); compare: entry times/sides (item F2), exit types, pts.
4. Mark each mismatch: data (missing minute), tie (stop and target in the same bar), lock, rejection, human. 
5. Check no position at 17:00; check position size equals 10 lots (or 1 lot) at all times; cancel orphan orders.
6. Weekly (Friday close): count trades vs expected, slippage means, lock events; write one line to FORWARD_REGISTER style log.
Budget: the box replay uses the 1-min files that currently end 2026-10-16; the box must extend the 1-min NQ file (ext trades 2026-10-19..23 exist) before daily reconciliation can run.
