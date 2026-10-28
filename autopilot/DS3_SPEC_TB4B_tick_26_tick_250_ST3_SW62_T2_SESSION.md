# DS3_SPEC_TB4B_tick_26_tick_250_ST3_SW62_T2_SESSION - executability spec and identity test (D3SSE2, 2026-10-28)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. **Session cell, tier DEAD-IN-HOLD (the ledger gate failed: HOLD mean -1,060/trade, both HOLD halves <= 0; PRE-selected only), basis mapped (ledger label "mapped": stored pts x 200 - 100.13, tick-exact entries, not direct-L2). NOT live-eligible, and on the ledger evidence not a candidate for the D6 book even after D3SA; this spec exists because the D6 list named it.** Cell = ASIA entries (18:00-02:00 ET) of the T-PULLBACK sub-minute cell: 250-tick bars, Supertrend regime on 3-minute bars, 62% retrace of the last-60-minute range, trigger T2.

**Reconstructible: YES.** Sources: ledger row (autopilot/DS3_SESSION_2_LEDGER.md line 64), rows l2vast/ds3/out/pb4/TB4B_tick_26_tick_250_ST3_SW62_T2_trades.parquet (ledger_index cid 2135; 5,017 rows all dates), cells l2vast/ds3/code/pb4/pb4_cells.py (lines 3-17), signal l2vast/ds3/code/pb4/pb4_sig.py (docstring 1-10, refs 35-43, regime 45-63, asof 64-65, levels 66-74, _fire 75-100, signals 101-108), bars l2vast/ds3/code/e1/e1_bars.py (_tick_bars lines 15-35) and out/bars/tick_250.parquet, simulator e1_sim.py (_run 55-90, run 101-111), runner pb4_run.py (gen line 32-35: mode 0, 60.0, 1.0), supertrend/ema/agg/rsi in l2vast/ds3/code/tb_lib.py (87-98, 39-42, 26-37, 129-137), results autopilot/DS3_TPULLBACK4.md (line 67, "NT8 bar (OnBarClose): BarsPeriodType.Tick, Value 250").

## 0. Cell id decoded (every token)
- **TB4B_tick**: family key in pb4_cells.FAM: TB4B = tick-bar family, bars in {tick_250, 500, 1000, 2000}.
- **26**: j = the cell's index in the 30-cell stratified random sample of that family (pb4_cells.cells(), seed 44 + sum(ord(fam))); NOT a parameter.
- **tick_250**: pullback/trigger bar X = 250-tick bars: a bar closes ON the 250th trade tick of the label day (e1_bars._tick_bars, N = 250; each trade print counts as one tick; the cumulative count resets at each 18:00 ET label day and the partial bar is dropped, never traded).
- **ST3**: regime type ST, k = 3: Supertrend(ATR 10, mult 3.0) on 3-minute bars (pb4_sig.regime('ST',3)).
- **SW62**: pullback level = 62% retrace of the high/low range of the last 60 COMPLETED 1-minute bars (not a fractal swing): long level = H - 0.62 x (H - L); short level = L + 0.62 x (H - L), H = max of the last 60 one-minute highs, L = min of the last 60 lows (rolling, min_periods 60), as-of the latest 1-min bar complete at the X-bar time.
- **T2**: trigger T2.
- Fixed by construction: exit 'P60' = DS2 bracket 60-pt stop / 60-pt target (1.0R), mode 0 (edge events), W = 600 s arming window, regime/level as-of.

## 1. Rule (NT8), bar by bar
- **Bars:** NT8 Tick bar, Value 250 (BarsPeriodType.Tick, 250), OnBarClose; plus a 3-minute series (regime) and a 1-minute series (level, ATR not needed); Globex template, label day 18:00 ET (bar counter resets at the session break).
- **Regime d (pb4_sig.regime, tb_lib.supertrend):** 3-min bars aligned to epoch-minute // 3; Supertrend(10, 3.0): TR = max(H-L, |H-C[1]|, |L-C[1]|); ATR = Wilder, seed = mean of the first 10 TRs at index 9; hl2 = (H+L)/2; ub/lb = hl2 +/- 3.0 x ATR; fub = ub if (ub < fub[1] or Close[1] > fub[1]) else fub[1]; flb = lb if (lb > flb[1] or Close[1] < flb[1]) else flb[1]; first bar (index 9): d = +1 if Close > hl2 else -1; afterwards d = +1 if Close > fub[1], -1 if Close < flb[1] (PREVIOUS bar's bands, unlike the TE6 definition), else d[1]. d = 0 before index 9. **As-of:** a 3-min bar's d is usable from its close (bar start + 3 min) on: the X bar at time t uses the latest 3-min bar with start + 3 min <= t.
- **Level (SW62):** from the 1-min bars (continuous, not reset daily): rolling 60-bar max high and min low (needs 60 bars), as-of the latest completed 1-min bar (bar start + 1 min <= t). Both level_long and level_short are computed on every X bar; the one for the current regime side is used.
- **Pullback touch on an X bar:** regime +1: bar Low <= level_long; regime -1: bar High >= level_short. A touch bar stores aL = its t_sig and hL = its High (long) / lS = its Low (short); armed for W = 600 s after the MOST RECENT touch bar (t_sig - aL <= 600). A regime change clears both sides.
- **Trigger T2 (evaluated at each X-bar close, OnBarClose):** long: the bar is NOT a touch bar AND Close > hL (high of the most recent touch bar), within the arming window and not yet spent; short: bar not a touch bar AND Close < lS. One fire per touch episode: after a fire the episode is spent and re-arms only after a touch followed by a non-touch bar (pb4_sig lines 86-91).
- **Event:** d_signal[i] = side at the firing bar (an edge: the next bar firing the same side is skipped, e1_sim line 67).
- **Gate:** the firing bar's t_sig ET time-of-day must be < 15:00 or >= 18:05 (e1_sim.run okb); bar not partial; book flat (busy until the exit instant).
- **Entry:** MARKET order on the tick that completes the firing bar; modelled fill E = that tick's price (zero slippage in the rows). 10 lots in the ledger (S10x1 slicing in a direct pricing).
- **Bracket:** stop-market 60 pt = 240 ticks and limit target 60 pt = 240 ticks from E (observed: all 403 ASIA stops exactly -60.0). Path checked on the 1-s extremes from the entry second; in the entry second only ticks after the entry tick count; stop before target inside a second.
- **Flat rule:** market flat at the close of the first blocked minute, 16:55 ET (3 of 450 PRE ASIA trades).
- **Session filter (this cell):** keep the trade if the ENTRY TICK time (t_sig, ET, no +1 min) has minute-of-day >= 18:00 or < 02:00; exits not session-limited.
- **Order types:** MARKET entry, STOP-MARKET + LIMIT target OCO, MARKET time exit.
- **Lots at $1,000 risk per trade:** stop 60 pt = $1,200 per NQ lot -> 0.83 NQ lot, not whole-lot; MNQ ($120 stop risk) 8 contracts = $960. Ledger reference: 10 NQ lots (R = $12,000).
- **Costs:** $4.84 RT per contract; ledger $ = pts x 200 - 100.13 per 10-lot trade.

## 2. Identity test (runnable)
Ledger filter: label day (t_sig ET + 6 h date) in [20230201, 20260206], ASIA by the tick-time minute-of-day.
| window (label days) | expected ASIA trades | first t_sig ET | last t_sig ET | mean $/trade (10 lots) | win | exits target / stop / 16:55 |
|---|---|---|---|---|---|---|
| PRE 2024-02-01..2025-06-30 | **450** | 2024-01-31 20:50:25.55 | 2025-06-29 22:07:30.72 | 1,842 | 58.2% | 260 / 187 / 3 |
| HOLD 2025-07-01..2026-02-06 | **200** | 2025-06-30 21:38:04.81 | 2026-02-05 21:53:29.47 | **-1,060** | 46.0% | 92 / 108 / 0 |
| 2023 span 2023-04-01..2024-01-31 | 193 | 2023-04-02 19:35:33 | 2024-01-30 19:35:10 | 46 | 50.8% | 95 / 92 / 6 |
| ALL 2023-02-01..2026-02-06 | 880 | 2023-02-09 00:48:26 | 2026-02-05 21:53:29 | 775 | 53.8% | 468 / 403 / 9 |
These reproduce the ledger row (450, 1,842, HOLD 200 / -1,060, span 46).
**Test (user side, NT8):** (1) bar identity: NT8 250-tick bars on the same tick data vs out/bars/tick_250.parquet: bars per day and the first/last bar close time and price per day; NT8 counts ticks by its own rule (a multi-lot aggressor print may be one or several ticks; the library counts each Databento trade print), and the library resets the count at the 18:00 ET label day, so expect small boundary differences; (2) trades: implement regime/level/trigger as above and compare ASIA entries (time within 2 s, side) >= 90% (tick-bar identity makes this the loosest of the specs), count within +/-5%, stop/target exactly 240/240 ticks, exit type >= 95%.

## 3. Data, roll, holidays
Tick data required. The 60-bar 1-min range and the 3-min Supertrend run continuously across days (adjusted history). Flat 16:55-18:00; no roll crossing.

## 4. Position limits
10 lots, one position, edge-triggered; bracket fixed so D3SA can replay it fully (fixed 240/240 ticks).

## 5. Backtest expectation (ledger and family report)
PRE 450 trades (6.0/wk), mean $1,842, MDE $1,537, t 3.36; **HOLD 200 trades mean -$1,060 (H2-2025 -1,271; 2026 stub -100)**; 2023 span +46 (by year 2023 -146, 2024 1,601, 2025 594, 2026 stub -100). Family report (all hours, MAPPED, DS3_TPULLBACK4.md line 67): 23.0 trades/wk, PRE $14,893/wk, HOLD $4,469, 2023 span $3,058, WF $9,967 (CI lo $3,091), +1 s / +2 s delay $8,772 / $7,015, 2x cost $6,567; paired vs ST10 +3.6 pt [MDE 4.5], vs the same rule on 1-min bars +0.6 [2.1]; mapped PASS, direct pending.

## 6. What could kill it
- **It already failed the HOLD look in this session**: ASIA HOLD -1,060/trade (win 46%), break-even slippage negative (-5.3 pt); PRE 9.2 pt. The all-hours cell decays PRE 14.9k -> HOLD 4.5k per week.
- Selection: a stratified-random draw of 30 per family; the family's own conclusion is that sub-minute bars do not beat the 1-min version of the same rule (DS3_TPULLBACK4 headline: -1,723 $/wk, timing gain nil within power).
- Cost: gross edge per trade is small relative to cost (family median gross $167 vs cost $87 per 10-lot trade); 2x cost keeps 47% of cells positive.
- Bar identity risk (NT8 tick counting vs the library's trade-print counting) and the firing-tick convention; tie/ordering inside a second.
- 2023 span near zero; ASIA/LONDON pattern.

## 7. Open items
- Recommend not spending D3SA replay on this leg beyond the cheap fixed-bracket pass; the ledger already has it DEAD-IN-HOLD. Tier label stays DEAD-IN-HOLD.
