# DS3_SPEC_E1A_RENKOC5_A3_r48_SESSION - executability spec and identity test (D3SSE2, 2026-10-28)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. **Session cell, tier SESSION-CANDIDATE (BOF not cleared), basis STORED (ledger label "rows-as-stored": tick-exact fills at the brick-completion tick price, stored $100.13 per 10-lot trade cost; NOT mapped to P9 in the ledger column, NOT direct-L2). NOT live-eligible until the live-latency result (D3SA, DS3_SESSION2_A) lands.** Cell = ASIA entries (18:00-02:00 ET) of the E1 group-A cell "true 12-point Renko bricks, colour-run state of 5, 3 x ATR stop, no target".

**Reconstructible: YES, entirely from code and tick data on disk.** Sources: ledger row (autopilot/DS3_SESSION_2_LEDGER.md line 43), rows l2vast/ds3/out/e1/E1A_RENKOC5_A3_r48_trades.parquet (ledger_index cid 2270; 7,298 rows, columns bar/side/ke/kx/E/pts/rs/mi/t_sig_ns), bars l2vast/ds3/out/bars/renko_48.parquet (217,583 bricks), code l2vast/ds3/code/e1/: e1_cells.py (lines 3, 9-14), e1_bars.py (_uni_bars lines 84-117, build 119-127), e1_core.py (color_state 18-30, state 31-37, stop_atr 47-49), e1_sim.py (_run 55-90, _path 32-54, run 101-111), e1_run.py (cell_params 10-12, gen_trades 13-18); ATR from l2vast/ds3/code/tb_lib.py (wilder 44-52, truer 53-57); tick-tape reference l2vast/ds3/out/bars/README_BARLIB.md and _identity_bars.csv.

## 0. Cell id decoded (every token)
- **E1A**: E1 (D3BAR, tick-built bar types) group A, cells created in e1_cells.A() (line 9-14): `E1A_RENKOC{conf}_{X}_{lab}` for conf in (2,5), exit X in (P60, A3), brick lab in r48/r80/r120.
- **RENKOC**: family 'RENKOC' = colour-run state on TRUE renko bricks (e1_core.state, line 36 -> color_state).
- **5**: conf = 5 consecutive same-colour bricks (params p=(5,)).
- **A3**: exit 'A3' = ATR stop of 3.0 x ATR, no target, state-following mode 1 (e1_run line 16; mode=1; lots=20, stopnom=30 for the lock engine, cell_params line 11).
- **r48**: bars = renko_48 = brick of 48 ticks = 12.00 pt (e1_cells RENKO_TB (48,'r48') = "T-B R=12 pt"). In e1_bars.build kind 'renko': `_uni_bars(ts,px,sz,ld, T=48, R=2*48=96, off=0)`.

## 1. Rule (NT8), bar by bar
- **Bars (tick-built Renko, e1_bars._uni_bars with T=48, R=96, off=0):** built from every NQ trade print, per label day (18:00 ET session); at the first tick of a label day: anchor = price, no direction. While direction d == 0: price >= anchor + 48 ticks emits an up brick [anchor, anchor+48]; price <= anchor - 48 emits a down brick. After an up brick (d=+1, last close lc): continuation brick when price >= lc + 48 ticks (opens at lc, closes lc+48); reversal brick when price <= lc - 96 ticks (opens at lc - 48, closes at lc - 96, i.e. the reversal brick is also 48 ticks tall and starts one brick below the last close, classic Renko). Mirror for d=-1 (continuation at lc - 48, reversal at lc + 96). A tick that gaps several bricks emits several bricks on the same tick (loop). A brick is KNOWN at the tick that completes it: t_sig = that tick's time (ns), p_sig = that tick's price. The partial bar at a label-day change is dropped (never traded).
- **State (e1_core.color_state, conf = 5):** s = +1 if brick close > open, -1 if < , 0 otherwise; run counts consecutive bricks of the same colour (reset to 1 on a colour change); if run >= 5 the state st = that colour; st persists through a shorter opposite run (a flip needs 5 same-colour bricks); everything (dr, run, st) resets to 0 at each new label day. The state is d[i] for brick i (0 until the first 5-run of the day).
- **When it trades (e1_sim._run, mode 1, state-following):** at every brick i with d[i] != 0 when the book is flat, i.e. NOT only on a state change, subject to: brick not partial; the brick's tick time-of-day ET (minute of day) < 15:00 or >= 18:05 (e1_sim.run okb: hm<900 or hm>=1085); time >= the previous trade's exit instant (busy); `blocked`: after a STOP-out no re-entry until the state leaves that side (s == blocked is skipped; blocked clears when d differs); a brick whose entry tick is also the signal-exit tick (multi-brick gap chain) is skipped.
- **Entry:** MARKET order on the completing tick (OnBarClose semantics for a brick = the tick that completes it); modelled fill price E = p_sig (that tick's price), no slippage in the rows (mapping/slippage added later, not in the ledger column). 20 lots at nominal 30-pt stop in the lock engine; the ledger scales to 10 lots.
- **Stop:** stop-market at E - side x sd, sd = 3.0 x ATR(14) of 1-minute bars, Wilder with SMA seed (tb_lib.wilder: y[13] = mean of the first 14 true ranges, y[i] = (y[i-1]*13 + TR)/14, NaN -> 0 before that), TR = max(H-L, |H-C[1]|, |L-C[1]|), taken from the last COMPLETED 1-min bar before the signal tick (index of the minute containing t_sig, minus 1) (e1_core.stop_atr). No minimum or maximum (observed stop distance in ASIA PRE: mean 23.9, median 19.9, 10th/90th percentile 9.2 / 43.3 pt; 2023 span mean 10.9). The stop price is not tick-rounded in the sim; NT8 rounds to the tick grid.
- **Target:** none (tr = 0).
- **Signal exit:** exit at the price of the first later brick whose state differs (the first j > i with d[j] != d[j-1]): market on that brick's completing tick, rs = 3 (183 of 424 PRE trades, mean +53.7 pt). The same brick's new state then opens the opposite trade (reversal) unless blocked.
- **Flat rule:** market flat at the close of the first blocked minute, 16:55 ET (rs = 2: 3 of 424 PRE trades); the stop is checked before anything else inside a second; for the entry second only ticks after the entry tick count.
- **Session filter (this cell):** keep the trade if the ENTRY TICK time (t_sig, ET, not +1 min) has minute-of-day >= 18:00 or < 02:00; earliest ASIA entry 18:05 or later. Exits are not session-limited.
- **Order types:** MARKET entry, STOP-MARKET (3 ATR), MARKET signal exit, MARKET 16:55 flat. No limit orders.
- **Lots at $1,000 risk per trade:** sd varies with ATR (typically 9-43 pt in PRE): NQ lots = floor(1000 / (sd x 20)) (sd 20 -> 2 lots, sd 25-50 -> 1 lot, sd > 50 -> 0); MNQ = floor(1000 / (sd x 2)) (sd 20 -> 25, sd 9 -> 55). Reference sizing in the ledger: 10 NQ lots equivalent (pts x 200 - 100.13); the registered cell is 20 lots at nominal 30 pt (R = $12,000 for the locks).
- **Costs:** $4.84 RT per contract; ledger $ = pts x 200 - 100.13 per 10-lot trade (stored all-in, 0.50 pt).

## 2. Identity test (runnable)
Bars: renko_48.parquet is the production brick list; the independent rebuild matched it on the audited day 20240320 (127 vs 127 bricks, identical, ticks per brick equal; out/bars/_identity_bars.csv). Trades: ledger filter = label day (t_sig ET + 6 h date) in [20230201, 20260206], ASIA by the tick-time minute-of-day.
| window (label days) | expected ASIA trades | first t_sig ET | last t_sig ET | mean $/trade (10-lot eq) | win | exits stop / signal / 16:55 | mean pts |
|---|---|---|---|---|---|---|---|
| PRE 2024-02-01..2025-06-30 | **424** | 2024-02-06 20:10:00.51 | 2025-06-29 18:55:19.85 | 2,341 | 27.1% | 238 / 183 / 3 | +12.2 |
| HOLD 2025-07-01..2026-02-06 | **188** | 2025-07-02 00:20:25.78 | 2026-02-06 00:32:14.35 | 2,321 | 29.3% | 113 / 74 / 1 | +12.1 |
| 2023 span 2023-04-01..2024-01-31 | 48 | 2023-05-03 21:30:41 | 2024-01-28 20:52:11 | -13 | 12.5% | 42 / 6 / 0 | +0.4 |
| ALL 2023-02-01..2026-02-06 | 673 | 2023-02-09 22:02:45 | 2026-02-06 00:32:14 | 2,149 | 26.4% | 402 / 266 / 5 | +11.2 |
These reproduce the ledger row (424, 2,341, HOLD 188 / 2,321, span -12.7).
**Test (user side, NT8):** (1) brick identity: NT8 Renko with brick size 12 pt on the same tick data must give the library bricks (classic Renko, 2-brick reversal, per-session reset at 18:00) - count bricks per day and compare the first/last brick prices; the NT8 Renko definition and the tick on which OnBarUpdate fires for a completed brick (the library signals on the completing tick; NT8 may fire on the first tick of the NEXT brick) are the uncertain points (README_BARLIB.md); (2) trades: run mode 1 with the 5-run state, 3 x ATR14(1m) stop, signal exit and the 15:00-18:05 gate; compare ASIA entries (time within 2 s, side) >= 95%, trade count within +/-5%, stop distance within 0.5 pt, exit type + exit time (+/-2 s for signal exits) >= 95%. Expect more tolerance than the 1-min cells: tick-time fills and NT8 tick aggregation differ.

## 3. Data, roll, holidays
Needs tick-level data (not 1-min). The brick state resets at each 18:00 ET label day, so history before the session is irrelevant for the state but the ATR(14, 1-min) needs 14 minutes of history. Flat 16:55-18:00; no roll crossing. Early closes flatten on the final bar.

## 4. Position limits
20 lots nominal in the registered cell (10-lot equivalent in the ledger); one position; reversal on signal exit means the book flips side within one tick (two orders: exit + entry).

## 5. Backtest expectation (ledger)
PRE 424 trades (5.65/wk), mean $2,341/trade (10-lot eq), MDE $1,686, t 3.89, win 27%; HOLD 188 trades, $2,321 (H2-2025 1,658; 2026 stub 4,151); 2023 span 48 trades, -13 (by year 2023 -49, 2024 2,450, 2025 2,022, 2026 stub 4,151). Payoff: winners average +111 pt, losers -24.7 pt (PRE ASIA): a trend-following, low-win-rate, fat-tail profile.

## 6. What could kill it
- **2023 span ~0 and thin early sample**: 48 ASIA trades in the span at -13/trade (win 12.5%; stops averaged 11 pt, ATR was small); the whole edge is 2024 onward. Break-even slippage (ledger HOLD) 2,321/200 = **11.6 pt per trade** (PRE 11.7), 2023 span about 0 (negative).
- **Heavy-tail dependence**: 27% winners averaging +111 pt (signal exits +54..+60 pt mean); a few trend days carry the mean; MDE per trade $1,686 vs mean 2,341; the two HOLD halves differ (H2-2025 1,658, 2026 stub 4,151 over about 5.5 weeks).
- **Stored-fill basis**: the rows fill at the brick-completion tick price with zero slippage and exit at the stop level (stop-market gap fills not modelled beyond the 1-s path); with 24-pt average stops, 0.5-1.5 pt of live slippage per stop exit is 2-6% of the stop but the cell's average win is carried by market signal exits, which sit on a reversal brick (a 96-tick move already happened) - slippage there is similar in pts. Unvalidated live.
- **Bar-type and tick identity risk** (largest implementation risk): NT8 Renko vs the library's uniform-renko code, the firing tick, session reset at 18:00 ET, tick aggregation of trades.
- **Selection**: one of the E1A cells (conf 2/5 x exit P60/A3 x brick 12/20/30 pt) and of the whole E1 program; the nearest T-B cell (TB9_RENKO_c5_k1_A3_N, approximations) was DEAD under the exact lock engine (WF -$0.2k/wk, e1_cells line 14); the predicted effect for this cell was about 0. Ledger: BOF not cleared; cluster 990 (pooled PRE mean 117 per trade).
- No limit orders, no news block; stop-fill quality in thin ASIA liquidity is not measured (direct replay pending).

## 7. Open items
- D3SA lists E1A as MEASURED-PROXY / stored basis (dynamic exit: no fixed stop/target ticks; signal exit). Direct replay of the tick-time entries and signal exits is the eligibility gate.
- Session lock thresholds and handoff (D3SD).
