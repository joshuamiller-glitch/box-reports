# DS3_SPEC_TB4W_03_time_15s_ST3_E20_1_T2_SESSION - executability spec and identity test (D3SSE2, 2026-10-28)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. **Session cell, tier SESSION-CANDIDATE (BOF not cleared), basis mapped (ledger label "mapped": stored pts x 200 - 100.13, second-resolution entries; direct-L2 verdict pending). NOT live-eligible until the live-latency result (D3SA, DS3_SESSION2_A) lands.** The ledger cell id is TB4W_03_time_15s_ST3_E20_1_T2_ntime14. Cell = ASIA entries (18:00-02:00 ET) of the T-PULLBACK sub-minute widening cell: 15-second bars, Supertrend regime on 3-minute bars, pullback to the 1-minute EMA20, trigger T2.

**Reconstructible: YES.** Sources: ledger row (autopilot/DS3_SESSION_2_LEDGER.md line 98), rows l2vast/ds3/out/pb4/TB4W_03_time_15s_ST3_E20_1_T2_ntime14_trades.parquet (ledger_index; 9,175 rows all dates), cell generator l2vast/ds3/code/pb4/pb4_widen.py (lines 1-18), signal pb4_sig.py (same file as TB4B: regime 45-63, levels 66-74, _fire 75-100), bars l2vast/ds3/code/pb4/pb4_bars.py (time bars, lines 29-39) and out/bars/time_15s.parquet, simulator e1_sim.py (mode 0), runner pb4_run.py; family report autopilot/DS3_TPULLBACK4.md (line 40: "NT8 bar (OnBarClose): BarsPeriodType.Second, Value 15").

## 0. Cell id decoded (every token)
- **TB4W**: the 3x3 widening group around every mapped-PASS cell of TB4A-E (pb4_widen: bar size x regime-bar k neighbours, i-1..i+1 along the family ladder and j-1..j+1 along KS = [3,5,10,15,30,60]; all other attributes fixed).
- **03**: index of the cell in the generated widening list (a counter, not a parameter).
- **time_15s**: bars = 15-second time bars.
- **ST3**: regime Supertrend(10, 3.0) on 3-minute bars (k = 3).
- **E20_1**: pullback level = EMA(20) of 1-minute closes. **T2**: trigger T2.
- **ntime14** (suffix, ledger name): the parent PASS cell is TB4A_time_14_time_30s_ST5_E20_1_T2 (30-s bars, ST5); this cell moves it one step on both ladders (30 s -> 15 s, k 5 -> 3). P60 bracket, mode 0, W = 600 s as in the parent.

## 1. Rule (NT8), bar by bar
- **Bars:** NT8 Second bars, Value 15 (BarsPeriodType.Second, 15), OnBarClose; a 3-minute series for the regime; a 1-minute series for the EMA. Library 15-s bars (pb4_bars.py): trade prints are bucketed by epoch seconds // 15 (aligned to :00/:15/:30/:45); a bar exists only if the bucket has at least one print; o/h/l/c = first/max/min/last price in the bucket; t_sig = bucket END ((bucket+1) x 15 s) and p_sig = the last print price of the bucket (the library fires at the bucket end with the last price; NT8 closes a time bar only when the first tick of the NEXT bucket arrives, which in quiet ASIA can be seconds later - see section 6).
- **Regime d:** as in the TB4B spec: tb_lib.supertrend(10, 3.0) on 3-minute bars (epoch-minute // 3): Wilder ATR with SMA seed at index 9; flips compare Close with the PREVIOUS bar's final bands; d = 0 before index 9; usable from the 3-min bar's close (start + 3 min) on.
- **Level E20_1:** EMA(20) of 1-minute closes, alpha 2/21, seeded with the first close, as-of the latest completed 1-min bar (start + 1 min <= t_sig). Same level for both sides.
- **Touch on a 15-s bar:** regime +1: bar Low <= level; regime -1: bar High >= level. Touch bars store aL = t_sig and hL = High (long) / lS = Low (short); arming window W = 600 s after the most recent touch bar.
- **Trigger T2 (15-s bar close):** long: bar is NOT a touch bar and Close > hL, inside the window, not spent; short: not a touch bar and Close < lS. One fire per touch episode (re-armed after a touch followed by a non-touch bar). A regime change clears the state.
- **Gate / entry / bracket / flat:** as the TB4B spec: t_sig ET time-of-day < 15:00 or >= 18:05; flat book; MARKET order at the bar-close tick, modelled fill E = p_sig; stop-market 60 pt (240 ticks) and limit target 60 pt (240 ticks) OCO (all 677 ASIA-all-window stops exactly -60.0); market flat at 16:55 ET.
- **Session filter:** keep the trade if the entry time t_sig (ET) has minute-of-day >= 18:00 or < 02:00. Every ASIA entry time falls on a 15-second boundary (e.g. 18:47:15), as the first/last stamps below show.
- **Order types:** MARKET entry, STOP-MARKET + LIMIT target OCO, MARKET time exit.
- **Lots at $1,000 risk per trade:** stop 60 pt = $1,200 per NQ lot -> 0.83 NQ lot; MNQ ($120 stop risk) 8 contracts = $960. Ledger reference: 10 NQ lots (R = $12,000).
- **Costs:** $4.84 RT per contract; ledger $ = pts x 200 - 100.13 per 10-lot trade.

## 2. Identity test (runnable)
Ledger filter: label day in [20230201, 20260206], ASIA by the entry-time minute-of-day.
| window (label days) | expected ASIA trades | first t_sig ET | last t_sig ET | mean $/trade (10 lots) | win | exits target / stop / 16:55 |
|---|---|---|---|---|---|---|
| PRE 2024-02-01..2025-06-30 | **800** | 2024-01-31 18:47:15 | 2025-06-29 22:58:30 | 1,237 | 55.6% | 442 / 353 / 5 |
| HOLD 2025-07-01..2026-02-06 | **369** | 2025-06-30 18:17:30 | 2026-02-06 01:16:30 | 494 | 52.6% | 193 / 175 / 1 |
| 2023 span 2023-04-01..2024-01-31 | 252 | 2023-04-02 18:27:15 | 2024-01-30 18:22:15 | -106 | 50.0% | 122 / 121 / 9 |
| ALL 2023-02-01..2026-02-06 | 1,470 | 2023-02-08 18:53:15 | 2026-02-06 01:16:30 | 718 | 53.5% | 778 / 677 / 15 |
These reproduce the ledger row (800, 1,237, HOLD 369 / 494, span -106).
**Test (user side, NT8):** (1) **bar identity (needed)**: NT8 15-s bars on the same tick data vs out/bars/time_15s.parquet: bar count per day, and for each bar the open/high/low/close and the bar end time; the library's bars close at the bucket end whereas NT8's OnBarUpdate for a time bar fires on the first tick of the next bucket - measure the lag (median/90th percentile, ASIA vs RTH) and re-run the cell with t_sig and E moved to that tick (the library's own robustness test: +1 s / +2 s entry delay, below); (2) trades: ASIA entries (time within 15 s, side) >= 90%, count within +/-5%, stop/target exactly 240/240 ticks, exit type >= 95%.

## 3. Data, roll, holidays
Tick data (or a 15-s series built from ticks) required; 1-minute and 3-minute series for EMA/Supertrend, continuous across days. Flat 16:55-18:00; no roll crossing. NT8 Second bars have no bar in an empty 15-s bucket (as the library).

## 4. Position limits
10 lots, one position, edge-triggered. Bracket fixed 240/240 ticks (fully replayable in D3SA).

## 5. Backtest expectation (ledger and family report)
PRE 800 trades (10.7/wk), mean $1,237, MDE $1,083, t 3.20; HOLD 369 trades, $494 (H2-2025 41, 2026 stub 1,878); 2023 span -106 (by year 2023 +2, 2024 1,301, 2025 601, 2026 stub 1,878). Family report (all hours, MAPPED, line 40): 30.6 trades/wk, PRE $15,661/wk, HOLD $13,189, 2023 span -$46, WF $14,578 (CI lo $5,035), +1 s / +2 s entry delay $12,560 / $12,466, 2x cost $11,297; paired vs ST10 +4.6 pt [MDE 2.6], vs the same rule on 1-min bars +5.2 [1.6]; mapped CANDIDATE (failed SPAN2>0), direct pending.

## 6. What could kill it
- **Bar-close convention** (largest): the rows fire at the 15-s bucket end with the last print; a live NT8 strategy acts on the first tick after the bucket. The family result with +1 s / +2 s delay is -14% / -14% on the all-hours WF mean (14,578 -> 12,560 / 12,466): the cell tolerates 1-2 s but ASIA gaps between prints can be longer.
- **Session cell is weak in HOLD**: ASIA HOLD $494/trade; break-even slippage from the ledger **2.5 pt** (HOLD) / 6.2 pt (PRE) / negative in the 2023 span (-0.5 pt); H2-2025 is about zero (41/trade) and the HOLD is carried by the 2026 stub (1,878, 5.5 wk).
- **Cost fragility**: 10.7 ASIA trades per week at 10 lots; gross edge per trade is small relative to cost (family median gross $167 vs $87 cost); the family table lists gross/cost of 303 / -67 $ per trade for this cell (column meaning as defined in DS3_TPULLBACK4.md section 4).
- **Selection**: widening neighbour of a PASS parent (TB4A_time_14), scored after the holdout look; the family concludes sub-minute bars add nothing over the 1-min version (-1,723 $/wk median); BOF not cleared; cluster 976.
- Bar identity (second bars, tick time stamps), the 2023 span negative, tie/ordering inside a second, no news block.

## 7. Open items
- D3SA: fixed-bracket leg, replayed with entries at the stored t_sig (plus the 1 s / 0 s delay arms); the bar-close lag test above is user-side NT8.
- Session lock thresholds and handoff (D3SD).
