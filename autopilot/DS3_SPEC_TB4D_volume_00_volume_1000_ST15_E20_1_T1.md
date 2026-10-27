# DS3_SPEC_TB4D_volume_00_volume_1000_ST15_E20_1_T1 - executability spec and identity test (D3X, 2026-10-27)

Research output; NOT a live recommendation. No execution-server, chart or live change. Source: D3PB4 (autopilot/DS3_TPULLBACK4.md). Replay: l2vast/ds3/code/x_pb4.py + x_pb4_ticks.py (own tick cache from the raw tape tables, own volume-bar builder, own as-of regime/level/trigger state machine, own tick-path bracket walk).

**Verdict: DELIVERABLE WITH CONDITIONS (bar logic is NT8-implementable from tick data; no L2 at runtime). The conditions are bar-construction fidelity and signal-tick timing, below.** Identity vs the library trades (volume-1000 bars, ST15 regime, E20_1 level, T1 trigger; label days 2023-02..2026-10-08): 8082 library trades, 0.58% entry mismatch (47 library-only, 85 replay-only), 0.62% on entry + exit type + points. Limit 2%. The volume bars themselves: 534,660 of 534,661 replay bars have the identical completing-tick timestamp as the library's (same ticks, same N=1000 overflow-split rule).

## 1. Rule (NT8)
- **Data:** NQ front-month trade ticks (Last), Calculate = OnBarClose; a 1-minute NQ series for the references; 15-minute series for the regime. Instrument NQ ($20/pt, tick 0.25), continuous back-adjusted (MergeBackAdjusted).
- **Bars (pullback/trigger series X):** Volume 1000 bars (BarsPeriodType.Volume, Value 1000), session break at 18:00 ET (a partial bar at the label-day change is closed and never traded). Volume rule as built: contracts accumulate; a trade that overflows 1000 is split across bars and EACH completed bar is signalled on that tick.
- **Regime (as-of):** Supertrend(10, 3.0) on 15-minute bars of the 1-minute data (aligned :00/:15/:30/:45 ET): ATR Wilder(10) with SMA seed, median price, bands ratchet on the previous Close, direction changes when Close crosses the PREVIOUS bar's band (standard form; this differs from the TE6 variant). A 15-minute bar's regime is usable only from its close time (bar open + 15 min). Regime d = +1 / -1.
- **Level (as-of):** EMA(20) of 1-minute closes (alpha 2/21, seeded with the first close); the value of the last COMPLETED 1-minute bar at the signal tick.
- **Pullback / trigger T1 (long, regime +1; short mirrored):** on each completed volume bar: touch = Low <= level. A touch bar arms the setup for 600 s. While armed and not yet fired on this touch episode: fire if the bar closes up (Close > Open) AND Close > level. One fire per touch episode (re-armed only after a non-touch bar); a regime change clears all arming. Fire -> signal = side.
- **Entry:** edge-triggered (signal different from the previous bar's signal), bar not partial, signal tick's ET time before 15:00 or at/after 18:05, no open trade and not before the previous trade's exit second: market order sent ON the bar-completing tick, modelled fill at that tick's price (plus mapped slippage). One trade at a time.
- **Exit:** stop-market 60 pt and target limit 60 pt (1.0R) OCO from the entry price; first tick through a level decides (stop wins an identical tick); flat at the close of the last 1-minute bar before 16:55 ET (early-close days at the final bar's close); after any exit the next entry cannot be before the next whole second.
- **Lots / dollars:** 10 NQ lots, R = 10 x 60 x $20 = $12,000: day -2R = -$24,000, +5R = +$60,000, give-back arm +2R = $24,000 keep 50%, week floor -12R = -$144,000. At the 14/14 scale (14 lots, R $16,800): -$33,600 / +$84,000 / arm $33,600 / floor -$201,600.
- **Order types:** MARKET entry (optionally S10x1 slicing), STOP-MARKET + LIMIT target OCO, MARKET time exit, XJ stop-join optional (see DS3_SPEC_TE* for the layer; unvalidated live).

## 2. Identity test
| check | n library | n replay | mismatches | % |
|---|---|---|---|---|
| entries (completing-tick time, side) | 8082 | 8120 | 47 | 0.58 |
| entry + exit type + points (|diff|<=1 pt) | 8082 | 8120 | 50 | 0.62 |
Residuals: the library walks 1-second H/L after the entry second while the replay walks ticks (stop and target in the same second can differ), reference-series differences at contract rolls (the library's back-adjusted 1-minute series is offset from mine by a few tens of ticks that vary by contract, which moves the E20 level and the ST regime very slightly on roll days), and 47 library-only / 85 replay-only entries that are state-cascade effects of those. The tape (aggressor-level trade events, one row per trade) is what both sides use. Replay window ends 2026-10-08 (my tick cache covers label days through 2026-10-12, the 1-minute file through 2026-10-16).

## 3. Conditions that decide DELIVERABLE in a real NT8 Sim
1. **Volume-bar construction on the live feed.** The library bars are built from the tape's trade events (one row per aggressor-level trade, size per event). NT8 volume bars are built from the data feed's Last ticks (Rithmic): tick aggregation (how multi-fill trades are reported) changes where each 1000-contract boundary falls, hence every later bar. Required Sim check: compare NT8's volume-1000 bar boundaries (time, OHLC) for a day against the box's bars (l2vast/ds3/out/bars/volume_1000.parquet); if more than a few percent of boundaries differ, the book is not reproduced.
2. **Signal tick timing.** The model sends the market order on the tick that completes the bar and fills at that tick's price. NT8 with Calculate OnBarClose on Volume bars processes the bar on the completing tick (confirm in Sim; some bar types are processed on the first tick of the next bar). Either way the entry is milliseconds after a trade print, i.e. latency-sensitive: the library's delayed-entry tests (+1 s / +2 s) give about the same WF, so it is second-level sensitive, not sub-second, but this must be measured live.
3. **Cost.** Median market cost on this family is 87-115 $/trade at 10 lots in the D3PB4 mapping (about 30 trades/wk); the 2x-cost WF is 12,292/wk. The D3PB4 direct-L2 replay for this cell is still running (coverage 1.9% of trades): until it completes, the verdict is on mapped costs.

## 4. Expectation (D3PB4 rows, WF 143 weeks 10 lots)
| WF mean | WF SD | WF maxDD | WF CI lo | HOLD | HOLD Sharpe | 2023-04..2024-01 span | WF-PRE | trades/wk | win | avg win | avg loss | 1.5x / 2x cost WF | corr ST10 | corr HM10 | placebo (PRE) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 18,143 | 57,370 | 301,867 | 8,395 | 22,621 | 2.71 | 12,790 | 13,780 | 29.9 | 52% | 11,072 | -10,746 | 15,105 / 12,292 | 0.47 | 0.35 | 1.00 |

## 5. What could kill it
- Selection: best of 177 cells; one of 13 mapped PASS, the same family (ST regime + EMA20 pullback + volume/time/renko bars) recurs, so the independent evidence is one cluster; V2 DSR on the full ledger is near 0.
- Bar construction and tick-timing risks above (items 1-2) are untested live.
- Closed-trade/exact lock engine, position limit (10 lots), and cost mapping as for the TE books.
