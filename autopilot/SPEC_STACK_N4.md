# SPEC_STACK_N4: coding spec pages for the six NY AM books of forward-register stack N4 (both-sides LEVEL books; every statement marked SPEC or READING)

Written 2026-11-26 23:39Z by W-SPEC9 (sub-agent of LEAD, not typed by Josh). Order: autopilot/DIRECTIVE_TEST9_2313Z.md part B (relay design under Josh's standing 18:22Z order). RESEARCH / SHADOW ONLY: nothing built, nothing coded, no gate or code change, nothing queued, nothing live, no spend, nothing deleted; the execution server, the live D8Asia.cs and every chart are untouched (D8Asia.cs was only read for its class list). Layout copied from the hand-verified pages D8_NYAM_SPEC_*.md / D8_BUILD_SPEC.md per-book blocks (sections 0 identity, 1 BAR, 2 TRIGGER, 3 signal to order, 4 sides and bracket, 5 other inputs, 6 one position / window / warm-up, 7 what trades, 8 parity data) with a stack overview, an existing-versus-new table and a coding list added.

Marks: **SPEC** = read from code or measured by re-running the engine code in this session; **READING** = my inference (stated as such). Where a source could not be found it says so; nothing is guessed. Book ids and parameters are those of FORWARD_REGISTER_STACKS.md (W-TEST8 section, seed 20261128); the stack is N4 only as a REGISTER object (equal weight, 1 lot per book, bare R0, no stack rules).

## STATUS LINE (read first)
- VERIFIED [SPEC]: for all 6 books the module source was found (th_grid/trig_levels_<name>.py -> triggers_d/lv_<name>.py, line construction in fd_levels.py / fd_levels2.py / fd_profile.py), the bar kernel source was found (th_bars/kernels.py via build_month.py), and the stored grid weekly table of the cell was reproduced exactly by re-running signal_fn and the gcore2x simulator for every held week (6 of 6 books with all held weeks equal). The 3 dated sessions per book were rebuilt from the stored trade tape with the engine bar kernel (all bars identical to the stored bars) and the signals, entries and exits in section 8 are those reproduced trades.
- NOT VERIFIED / OPEN: (a) the live-engine fill (book walk) is not re-run (the table uses the grid engine); (b) line values come from the engine's stored line files (files written 2026-11-17 19:55-23:08Z by fd_levels.py / fd_levels2.py / fd_profile.py from nq1m.npz, data to 2026-11-13; they were NOT re-derived from the tape here except that the 3.7 / L43f0cbfb / Le4fede95 pages already verify vwap, fib15, fibr_on, profile_nodes and piv_floor lines for other dates); (c) no D8 print-rule version exists for the activity bar `tsf` (see flags).
- **FLAG We3999e99 trades (almost) only on bar 0 of the session** (share 1.00 of its 41 grid trades in the loaded months; mean finite share of its lines in the session 0.97): see its sections 2 and 7.
- NOTE Wbcfa80fb is also in stack N1 of the register (the A4-A5 / N4-N5 draw only avoided reuse inside its own draw); it is described again here so that this page stands alone.
- **FLAG W9fd5ca5d placed 0 grid trades in its held weeks**; its dated sessions are from before the hold.
- Coding size: see section D (existing versus new, and a rough list of what would have to be coded).

## A. COMMON FACTS FOR EVERY BOOK ON THIS PAGE
**A1. Engine that produced the numbers (grid).**
[SPEC] GRID ENGINE (the engine that produced the cell numbers; th_grid/gcore2x.py RowCtx / sim_slice, constants in gcore.py and gjob.py): signals = rows of signal_fn on the book's bar row, kept only if the signal bar is part == 0 and its session code is the book's session (the session of the signal bar, sess_id % 10). ENTRY = the first trade print with timestamp >= t_close(signal bar) + 1 s (I0 = searchsorted(tape ts, t_close + 1e9)), filled at that print's price plus an adverse measured slippage in ticks (table autopilot/BAR_SLIPPAGE_TABLE.csv, window ALL, lat 0, 2 lots, by session and bar family: price/activity/time); a signal whose entry print is at or after the session end is skipped. STOP / TARGET = from the fill: stop at fill -/+ stop_pts, target at fill +/- tgt_pts (both in points, x4 ticks); exit by the first print AT or THROUGH the stop (exit price = that print's price, 1 tick adverse); the target is reached by the first print one tick THROUGH the level (exit AT the level); if neither before the session end, exit at the last print before the session end, 1 tick adverse. SESSION END = the next of 02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET after the signal bar's close (sess_end_fast; Asia ends 02:00 ET, NY AM 12:00 ET). COST = 4.84 USD round trip = 0.242 pt (x $20 per point). ONE POSITION: a signal whose entry print index is not after the last exit print index of the same (parameter set, bracket) is skipped; the blocking state is reset at each UTC calendar month (gcore2x.run_table / sim_slice: per-month segment). 1 NQ lot, $20 per point. UNIT RULES for sym/asym brackets: u = rolling median over 50 bars (min_periods 10, floor 0.25) of (high - low) of the book's bar row INCLUDING the signal bar (RowCtx: pd.Series(h-l).rolling(50, min_periods=10).median(), not shifted), stop/target = clip(m x u, 10, 120) points with m = 8 / 15 / 30 (sym8u / sym15u / sym30u) or (10,20) / (15,30) (asym); 'fixedA/B' = stop A points, target B points; 'plain60/60' = 60 / 60.

**A2. Live engine (for the match test).**
[SPEC] LIVE-ENGINE entry (D8_BUILD_SPEC.md (b2), quoted not re-derived here): market order at floor(known time of the signal bar, whole seconds) + 2 s, filled 1.0 s later at the 10-level book (buy at the ask side, sell at the bid side, average of the walked levels); stop order at fill -/+ stop_pts, target limit at fill +/- tgt_pts; one position per book; flat at 02:00 ET (Asia) / 12:00 ET (NY AM) + 1.0 s; contract rolls flat 1 ns before the roll second, entries skipped roll-120 s to roll+300 s. The per-bar table below uses the GRID engine because the grid is what produced the cell and the Test 8 numbers; the two differ in entry time (+1 s print vs +3 s book fill), slippage model and exit prices, so a live match test compares SIGNAL BARS and ORDER TIMES, and trade prices only within the stated slippage.

**A3. Level lines and the T0 rule.**
[SPEC] Line store: /mnt/l2/l2vast/_bars/feat_d/lines/<name>.npy float32 per 1-minute (raw price, NaN = none), built from /mnt/l2/l2vast/_bars/feat_d/nq1m.npz (fd_nq1m.py: NQ 1-minute OHLCV from the trade tape, back-adjusted at contract rolls: off = points lifted onto the newest contract; level lines are computed on back-adjusted prices and converted to raw at minute i: raw = adj - off[i]). Minute columns: ts (epoch s, minute START), o,h,l,c, v, d, off, et (ET minute of day), ld (label date = ET + 6 h; a 'label day' runs 18:00 ET to 18:00 ET), iid. tord = (et - 1080) mod 1440 = minutes since 18:00 ET.
[SPEC] Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.

**A4. Bar scale table.**
[SPEC] Scale factors (th_bars/build_month.py scales(), lines 13-32; D8_BAR_DEFS.md section 2): stats_day table = one row per Globex trading date (all instruments' T records): vol (contracts), n (prints), rng = (max over instruments of high-low)/4 in points. For row i: abs_x[i] = median of the previous up to 20 ROWS with value > 0 (rows, not calendar days; the current row not used; if fewer than 5 rows, r0 = median of the first 60 rows); s_x = abs_x / r0. Constants r0_vol = 610702, r0_n = 373169, r0_rng = 191.5 pt (D8_BAR_DEFS). Threshold fixed at the session's td for the whole session; every event-bar kernel resets at a change of session key (td x 10 + code) or instrument id. Series: the bar row's file is ONE continuous series over ALL six session codes (Asia 0, London 1, pre 2, NY AM 3, NY PM 4, close 5; only 0, 1, 3, 4 give signals), so the previous session's last bars are visible to the first bar of the next (memory M, hold n, native u).

**A5. How the 3 dated sessions per book were chosen (SPEC, my rule).** From the sessions with at least one grid trade in the held weeks (spells below), newest first, with bars >= half the median bars per session, one per grid week, preferring a different side/exit-reason mix than the ones already picked; if the book had fewer than three such sessions the latest sessions before the hold were used (marked 'BEFORE the held period'). The newest held week is grid week 185 (2026-10-18 to 2026-10-24), so the newest dates are mid to late October 2026. Each session table lists all raw events (or those near the traded signals when there are more than 40), the reproduced trades, and the input bars around each traded signal; the full session with every line value is in autopilot/spec_stack_inputs/<book>_td<td>.csv.

## B. STACK OVERVIEW AND EXISTING-VERSUS-NEW
| book | session | bar row | module / variant / params | bracket | held weeks (grid) | $/lot/wk, t, trades | still qualifies at span end (Test 8 table) | bar builder status [READING] | module status [READING] | flag |
|---|---|---|---|---|---|---|---|---|---|---|
| Wbcfa80fb | NYAM | swing_atr_0.25 | prior_day false_break M=1,k=0.0 | fixed120/120 | 169-185 | 1527, 4.9, 1045 | yes | exists | NEW | also in stack N1 |
| Wc7c3f9c5 | NYAM | pnf_7 | vwap break_native n=2,k=0.0 | sym30u | 117-185 | 1434, 4.1, 1587 | yes | spec only | lines spec only; no VWAP code in D8Asia.cs | - |
| We3999e99 | NYAM | pnf_7 | fibr_dev reject tol=0.5,conf=body | asym15u/30u | 182-185 | 946, 4.1, 617 | yes | spec only | NEW | bar-0-only |
| W9fd5ca5d | NYAM | pnf_10 | piv_floor reject tol=1.0,conf=body | fixed60/120 | 182-185 | 784, 4.0, 658 | yes | spec only | lines exist in D8Asia.cs; trigger by parameter | 0 held trades |
| W5ba295af | NYAM | urenko_40 | piv_wf retest M=3,tol=0.5 | sym30u | 169-185 | 1269, 4.1, 1237 | yes | new (one parameter from frenko) | NEW | - |
| Wbb4ef729 | NYAM | swing_pct_5 | vwap break n=2,k=0.25 | sym15u | 143-185 | 1861, 4.9, 1618 | yes | spec exists, class by parameter | lines spec only; no VWAP code in D8Asia.cs | - |

Status words: 'exists' = specified on a page AND a class in D8Asia.cs; 'spec only' = specified on a page, no class; 'new' = no page, no class. D8Asia.cs was read only for its class list (READING; its content is not part of this order).

## C. THE BOOKS (one block each; sections 0 to 8)


### BOOK Wbcfa80fb (NYAM): swing_atr_0.25 + prior day level false break (M 1, k 0.0), BOTH sides, bracket fixed120/120
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 17 of 17 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id Wbcfa80fb (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_Wbcfa80fb_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/Wbcfa80fb.parquet` (26957 events: 13477 long, 13480 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `swing_atr_0.25`, module `trig_levels_prior_day` (code/th_grid/trig_levels_prior_day.py -> triggers_d/lv_prior_day.py), variant `false_break`, params {"M": 1, "k": 0.0}, bracket `fixed120/120`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/swing_atr_0.25/trig_levels_prior_day.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1527, L6M 3554, L3M 3470; t 4.9 over 1045 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 169..185 (2026-06-28 to 2026-10-24) = 17 held week(s); months in the cell file: 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored 291.89 / mine 291.89 pts, 8 / 8 trades; w182 2026-09-27 stored 209.67 / mine 209.67 pts, 7 / 7 trades; w183 2026-10-04 stored 125.22 / mine 125.22 pts, 2 / 2 trades; w184 2026-10-11 stored 1.94 / mine 1.94 pts, 3 / 3 trades; w185 2026-10-18 stored 167.70 / mine 167.70 pts, 5 / 5 trades (last 5 of 17 held weeks shown; 17 of 17 equal)

**1. BAR**
**BAR** row `swing_atr_0.25` = SWING leg bar (kernel k_dchg). [SPEC] build_month.py lines 131-132: theta = max(2, round(0.25 x ATR)) ticks, ATR = max(1, 4 x abs_rng / 10) with abs_rng = the trailing-20-row median of the daily range in POINTS (a tenth of that median in ticks, NOT an intraday ATR; D8_BAR_DEFS 3.10). Leg bars exactly as `dchg`. Values on the sample days: 20261023: atr_ticks=167.75, theta_ticks=42, theta_pts=10.50, abs_rng_pts=419.38; 20261014: atr_ticks=167.50, theta_ticks=42, theta_pts=10.50, abs_rng_pts=418.75; 20261007: atr_ticks=175.30, theta_ticks=44, theta_pts=11.00, abs_rng_pts=438.25. [SPEC] Price-only. [SPEC] swing_atr_0.25 is already specified in D8_BAR_DEFS.md section 3.10 and D8_BUILD_SPEC (L488784d8).
- [SPEC] Bars per NYAM session in the loaded months: median 300 (min 17, max 1094, 222 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/swing_atr_0.25/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 469 stored / 469 rebuilt / 469 identical (o,h,l,c,known_ts,part); td 20261014: 321 stored / 321 rebuilt / 321 identical (o,h,l,c,known_ts,part); td 20261007: 154 stored / 154 rebuilt / 154 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **exists**: swing_atr_0.25 specified (D8_BAR_DEFS 3.10, L488784d8); SwingBuilder in D8Asia.cs.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_prior_day` (th_grid/triggers_d/lv_prior_day.py; lines fd_levels.py lines 27-34). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 5 lines in this list order: PD_RTH__H, PD_RTH__L, PD_FULL__H, PD_FULL__L, PD_C__C.
- PD_RTH__H / __L = high / low of the PRIOR label day's RTH minutes (tord 930..1319 = 09:30-16:00 ET). PD_FULL__H / __L = high / low of ALL minutes of the prior label day (18:00 ET to 18:00 ET). PD_C__C = close of the prior label day's minute tord = 1319 (the 15:59 ET minute). Each is constant for the whole next label day (18:00 ET to 18:00 ET), so it is available from the very first Asia bar. 'prior label day' = the previous label day present in the store (weekends/holidays are skipped).
- Back-adjusted then converted to raw.
Variant `false_break` (M=1, k=0.0): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: M=1, k=0.0 -> k*u = 0.000 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 222 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PD_RTH_H 0.99, PD_RTH_L 0.99, PD_FULL_H 1.00, PD_FULL_L 1.00, PD_C_C 0.96.
- [READING] Module status: **NEW**: no spec page names prior_day; PD_C / PD_RTH are used inside D8Asia.cs for pivots and value area (line 1447 prints PD_C, VAL) but there is no prior-day level-trigger class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `fixed120/120` = stop 120 pts / target 120 pts, fixed (no unit rule); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 120 pts / target 120 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: One prior label day of 1-minute data. READING: with the NQ 1-minute series of the previous RTH day and previous 18:00-18:00 day the lines can be computed with no further history.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng and abs_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 339; share whose signal bar is bar 0 of the session: 0.10; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 15, 97, 233, 939.
- [SPEC] Held weeks only: 123 grid trades; share on bar 0: 0.11; signal-bar index quantiles: 0, 7.5, 68, 153.5, 401.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: PD_RTH_H 39, PD_C_C 36, PD_RTH_L 31, PD_FULL_L 10, PD_FULL_H 7.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/Wbcfa80fb_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 469, first known 2026-10-23T13:30:01.526Z, last known 2026-10-23T15:58:58.797Z; rebuilt-from-tape check 469/469/469; threshold values: atr_ticks=167.750, theta_ticks=42, theta_pts=10.500, abs_rng_pts=419.375
SIGNALS (raw events of the session: 79 in total, 3 shown (those inside the input windows or traded); all are in the CSV file; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-23T13:30:01.526Z,-1,PD_RTH__L,29033.00,28994.75,5.00,Y
135,2026-10-23T13:45:35.116Z,1,PD_C__C,29145.00,29147.00,5.00,Y
136,2026-10-23T13:46:11.781Z,-1,PD_C__C,29145.00,29107.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,-1,2026-10-23T13:30:02.526Z,29008.50,0.1776,29008.46,2026-10-23T13:45:01.670Z,29129.00,Stop,120.0,120.0,-120.54,-2415.73
135,1,2026-10-23T13:45:36.146Z,29137.75,0.1776,29137.79,2026-10-23T14:41:54.155Z,29257.79,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 10 of 469 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-23T13:30:01.526Z,29030.75,29030.75,28994.75,28994.75,5.00,2026-10-23T13:29:00Z,2026-10-23T13:29:00Z,,PD_RTH_L=29033.00,-1 PD_RTH_L
1,2026-10-23T13:30:03.112Z,28994.75,29018.00,28994.75,29018.00,5.00,2026-10-23T13:30:01Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
...
129,2026-10-23T13:45:07.780Z,29108.50,29123.25,29108.50,29123.25,5.00,2026-10-23T13:45:06Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
130,2026-10-23T13:45:12.776Z,29123.25,29123.25,29100.25,29100.25,5.00,2026-10-23T13:45:07Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
131,2026-10-23T13:45:14.609Z,29100.25,29112.00,29100.25,29112.00,5.00,2026-10-23T13:45:12Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
132,2026-10-23T13:45:15.356Z,29112.00,29112.00,29097.75,29097.75,5.00,2026-10-23T13:45:14Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
133,2026-10-23T13:45:26.767Z,29097.75,29128.00,29097.75,29128.00,5.00,2026-10-23T13:45:15Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
134,2026-10-23T13:45:30.170Z,29128.00,29128.00,29117.50,29117.50,5.00,2026-10-23T13:45:26Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
135,2026-10-23T13:45:35.116Z,29117.50,29147.00,29117.50,29147.00,5.00,2026-10-23T13:45:30Z,2026-10-23T13:45:00Z,PD_C_C=29145.00,PD_RTH_H=29594.75,+1 PD_C_C
136,2026-10-23T13:46:11.781Z,29147.00,29147.00,29107.25,29107.25,5.00,2026-10-23T13:45:35Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,-1 PD_C_C
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-23T13:30:01.526Z side -1 fired PD_RTH_L: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
k=135 2026-10-23T13:45:35.116Z side +1 fired PD_C_C: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
```

#### td 20261014 (sess_id 202610143, NYAM session, grid week 184)
- bars of the session: 321, first known 2026-10-14T13:30:05.022Z, last known 2026-10-14T15:59:51.536Z; rebuilt-from-tape check 321/321/321; threshold values: atr_ticks=167.500, theta_ticks=42, theta_pts=10.500, abs_rng_pts=418.750
SIGNALS (raw events of the session: 20 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
30,2026-10-14T13:33:44.715Z,1,PD_RTH__L,30591.25,30592.75,5.00,Y
31,2026-10-14T13:33:54.762Z,-1,PD_RTH__L,30591.25,30578.50,5.00,no
32,2026-10-14T13:34:02.197Z,1,PD_RTH__L,30591.25,30597.75,5.00,no
33,2026-10-14T13:34:15.050Z,-1,PD_RTH__L,30591.25,30566.00,5.00,no
70,2026-10-14T13:40:52.013Z,1,PD_RTH__L,30591.25,30621.00,5.00,no
87,2026-10-14T13:44:55.174Z,-1,PD_RTH__L,30591.25,30567.75,5.00,no
88,2026-10-14T13:45:08.170Z,1,PD_RTH__L,30591.25,30599.75,5.00,no
89,2026-10-14T13:45:18.327Z,-1,PD_RTH__L,30591.25,30578.50,5.00,no
90,2026-10-14T13:45:33.518Z,1,PD_RTH__L,30591.25,30602.00,5.00,no
91,2026-10-14T13:45:34.424Z,-1,PD_RTH__L,30591.25,30589.00,5.00,no
92,2026-10-14T13:45:39.578Z,1,PD_RTH__L,30591.25,30601.00,5.00,no
93,2026-10-14T13:45:44.441Z,-1,PD_RTH__L,30591.25,30583.75,5.00,no
94,2026-10-14T13:45:55.010Z,1,PD_RTH__L,30591.25,30595.25,5.00,no
95,2026-10-14T13:45:56.063Z,-1,PD_RTH__L,30591.25,30584.75,5.00,no
96,2026-10-14T13:46:00.926Z,1,PD_RTH__L,30591.25,30595.25,5.00,no
97,2026-10-14T13:46:03.474Z,-1,PD_RTH__L,30591.25,30584.75,5.00,no
98,2026-10-14T13:46:22.422Z,1,PD_RTH__L,30591.25,30622.50,5.00,no
99,2026-10-14T13:46:57.641Z,-1,PD_RTH__L,30591.25,30582.75,5.00,no
100,2026-10-14T13:47:14.198Z,1,PD_RTH__L,30591.25,30603.25,5.00,no
117,2026-10-14T13:52:59.486Z,-1,PD_RTH__L,30591.25,30544.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
30,1,2026-10-14T13:33:45.942Z,30583.25,0.1776,30583.29,2026-10-14T14:12:04.262Z,30463.00,Stop,120.0,120.0,-120.29,-2410.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 321 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
24,2026-10-14T13:32:44.541Z,30533.00,30549.25,30533.00,30549.25,5.00,2026-10-14T13:32:39Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
25,2026-10-14T13:32:54.294Z,30549.25,30549.25,30517.25,30517.25,5.00,2026-10-14T13:32:44Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
26,2026-10-14T13:33:05.286Z,30517.25,30547.25,30517.25,30547.25,5.00,2026-10-14T13:32:54Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
27,2026-10-14T13:33:07.859Z,30547.25,30547.25,30536.00,30536.00,5.00,2026-10-14T13:33:05Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
28,2026-10-14T13:33:28.757Z,30536.00,30585.75,30536.00,30585.75,5.00,2026-10-14T13:33:07Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
29,2026-10-14T13:33:31.815Z,30585.75,30585.75,30570.25,30570.25,5.00,2026-10-14T13:33:28Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
30,2026-10-14T13:33:44.715Z,30570.25,30592.75,30570.25,30592.75,5.00,2026-10-14T13:33:31Z,2026-10-14T13:33:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,+1 PD_RTH_L
31,2026-10-14T13:33:54.762Z,30592.75,30592.75,30578.50,30578.50,5.00,2026-10-14T13:33:44Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,-1 PD_RTH_L
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=30 2026-10-14T13:33:44.715Z side +1 fired PD_RTH_L: PD_RTH_H=30814.75; PD_RTH_L=30591.25; PD_FULL_H=30906.00; PD_FULL_L=30591.25; PD_C_C=30788.75
```

#### td 20261007 (sess_id 202610073, NYAM session, grid week 183)
- bars of the session: 154, first known 2026-10-07T13:30:08.405Z, last known 2026-10-07T15:52:36.394Z; rebuilt-from-tape check 154/154/154; threshold values: atr_ticks=175.300, theta_ticks=44, theta_pts=11.000, abs_rng_pts=438.250
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
149,2026-10-07T15:43:09.698Z,1,PD_FULL__L,31309.25,31343.50,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
149,1,2026-10-07T15:43:11.387Z,31332.50,0.1776,31332.54,2026-10-07T15:59:59.207Z,31338.25,SessionEnd,120.0,120.0,5.71,109.27
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 154 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
143,2026-10-07T15:23:57.715Z,31265.25,31281.00,31265.25,31281.00,5.00,2026-10-07T15:22:49Z,2026-10-07T15:22:00Z,,PD_FULL_L=31309.25,
144,2026-10-07T15:26:36.181Z,31281.00,31281.00,31267.25,31267.25,5.00,2026-10-07T15:23:57Z,2026-10-07T15:23:00Z,,PD_FULL_L=31309.25,
145,2026-10-07T15:28:00.066Z,31267.25,31283.75,31267.25,31283.75,5.00,2026-10-07T15:26:36Z,2026-10-07T15:26:00Z,,PD_FULL_L=31309.25,
146,2026-10-07T15:29:40.976Z,31283.75,31283.75,31268.50,31268.50,5.00,2026-10-07T15:28:00Z,2026-10-07T15:28:00Z,,PD_FULL_L=31309.25,
147,2026-10-07T15:32:59.450Z,31268.50,31295.00,31268.50,31295.00,5.00,2026-10-07T15:29:40Z,2026-10-07T15:29:00Z,,PD_FULL_L=31309.25,
148,2026-10-07T15:34:56.340Z,31295.00,31295.00,31281.75,31281.75,5.00,2026-10-07T15:32:59Z,2026-10-07T15:32:00Z,,PD_FULL_L=31309.25,
149,2026-10-07T15:43:09.698Z,31281.75,31343.50,31281.75,31343.50,5.00,2026-10-07T15:34:56Z,2026-10-07T15:34:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,+1 PD_FULL_L
150,2026-10-07T15:44:24.104Z,31343.50,31343.50,31327.50,31327.50,5.00,2026-10-07T15:43:09Z,2026-10-07T15:43:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=149 2026-10-07T15:43:09.698Z side +1 fired PD_FULL_L: PD_RTH_H=31616.50; PD_RTH_L=31457.75; PD_FULL_H=31616.50; PD_FULL_L=31309.25; PD_C_C=31480.75
```

### BOOK Wc7c3f9c5 (NYAM): pnf_7 + vwap level break native (n 2, k 0.0), BOTH sides, bracket sym30u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 69 of 69 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id Wc7c3f9c5 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_Wc7c3f9c5_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/Wc7c3f9c5.parquet` (16792 events: 8407 long, 8385 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `pnf_7`, module `trig_levels_vwap` (code/th_grid/trig_levels_vwap.py -> triggers_d/lv_vwap.py), variant `break_native`, params {"n": 2, "k": 0.0}, bracket `sym30u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/pnf_7/trig_levels_vwap.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1434, L6M 613, L3M 323; t 4.1 over 1587 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 117..185 (2025-06-29 to 2026-10-24) = 69 held week(s); months in the cell file: 202506, 202507, 202508, 202509, 202510, 202512, 202601, 202602, 202603, 202604, 202605, 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored -389.75 / mine -389.75 pts, 8 / 8 trades; w182 2026-09-27 stored -198.78 / mine -198.78 pts, 10 / 10 trades; w183 2026-10-04 stored 310.06 / mine 310.06 pts, 10 / 10 trades; w184 2026-10-11 stored -370.98 / mine -370.98 pts, 10 / 10 trades; w185 2026-10-18 stored 274.36 / mine 274.36 pts, 10 / 10 trades (last 5 of 69 held weeks shown; 69 of 69 equal)

**1. BAR**
**BAR** row `pnf_7` = POINT-AND-FIGURE column bar. [SPEC] kernel th_bars/kernels.py k_pnf (lines 248-273), built by build_month.py line 135-136: box B = max(1, round(7 x s_rng)) ticks (numpy round half to even; 1 tick = 0.25 pt), 3-box reversal. State per session key: first print sets lvl = st = p, d = 0. d = 0: a print >= lvl + B starts an UP column (st = lvl, lvl += ((p-lvl)//B) x B); a print <= lvl - B starts a DOWN column (mirror). d = +1: p >= lvl + B extends (lvl += ((p-lvl)//B) x B); p <= lvl - 3B CLOSES the column: bar o = st, h = lvl, l = st, c = lvl, then a DOWN column starts with st = lvl - B and lvl = lvl - ((lvl-p)//B) x B. d = -1 mirror (bar o = st, h = st, l = lvl, c = lvl; new st = lvl + B). One bar per COMPLETED column; known time = timestamp of the confirming print (the print that moved 3 boxes against the column); the unfinished column at the session end is never a bar; there are no part=1 bars. Resets at every session boundary (02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET) and at a contract roll. [SPEC] Price-only: unaffected by the print rule (D8_BUILD_SPEC line 13; D8_PRINT_RULE). Box on the three sample days: 20261023: box_ticks=15, box_pts=3.75; 20261016: box_ticks=15, box_pts=3.75; 20261009: box_ticks=16, box_pts=4.00.
- [SPEC] Bars per NYAM session in the loaded months: median 177 (min 6, max 2195, 479 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/pnf_7/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 313 stored / 313 rebuilt / 313 identical (o,h,l,c,known_ts,part); td 20261016: 256 stored / 256 rebuilt / 256 identical (o,h,l,c,known_ts,part); td 20261009: 120 stored / 120 rebuilt / 120 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec only**: pnf_7 specified in D8_BUILD_SPEC (L9c2622b0, Asia; stored Asia bars rebuilt identical in D8_ASIA_NEWBOOK_INPUTS.md) and pnf_14 in D8_NYAM_SPEC_L43f0cbfb; NO class for it in D8Asia.cs (class list read): box is a parameter, so pnf_5 / pnf_10 are parameter changes of a builder that is specified but not yet in the strategy file.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_vwap` (th_grid/triggers_d/lv_vwap.py; lines fd_levels.py lines 55-72 and 82-91). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 8 VWAP lines in this list order: VWAP0__V, RVWAP0__V, LVWAP0__V, YVWAP__V, AVPDH__V, AVPDL__V, WVWAP__V, MVWAP__V. Every VWAP = cumulative sum(typ x minute volume) / cumulative sum(volume) with typ = (h+l+c)/3 of the 1-minute bar, value at minute i uses minutes < i of the anchor period (shift by one minute, NaN on the anchor's first minute).
- VWAP0: anchored at the first minute of each label day (18:00 ET); valid when tord >= 30 and cumulative volume > 2000. RVWAP0: anchored 09:30 ET, valid 09:45-16:00 ET (tord 945..1319) and cum volume > 2000. LVWAP0: anchored 02:00 ET, valid 02:15-16:00 ET (tord 495..1319) and cum volume > 1000.
- YVWAP: the prior label day's RTH (09:30-16:00 ET) VWAP, constant for the whole next label day. AVPDH / AVPDL: VWAP anchored at the minute of the prior RTH day's high / low (the minute with the extreme h / l inside RTH), running over the whole next label day (value at i uses minutes a..i-1). WVWAP: anchored at the first minute of each ISO week (of the label date), valid when cumulative volume > 20000. MVWAP: anchored at the first minute of each calendar month, valid when cumulative volume > 20000.
- Back-adjusted then converted to raw (see store).
Variant `break_native` (n=2, k=0.0): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (native) = rolling median of (high - low) over the previous 100 bars of THIS book's bar series (bars j-100..j-1, shifted one bar, min_periods 20, floor 0.5 pt; NaN before 20 bars) (fd_common.unit); every tolerance below is x u. With these parameters: n=2, k=0.0 -> k*u = 0.0 x u.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 479 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): VWAP0 1.00, RVWAP0 0.80, LVWAP0 1.00, YVWAP 1.00, AVPDH 0.99, AVPDL 0.99, WVWAP 1.00, MVWAP 1.00.
- [READING] Module status: **lines spec only; no VWAP code in D8Asia.cs**: break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits).

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `sym30u` = unit rule sym30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule sym30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ trades only (1-minute bars from the tape, with contract-roll back-adjustment).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: Needs the previous RTH day (YVWAP, AVPDH/L), the current ISO week and month (WVWAP/MVWAP; early in a week/month the volume gate delays validity). READING: starting a live chart cold needs the prior RTH day of 1-minute data plus the week-to-date and month-to-date minutes; the store itself runs from 2023-04-02.
- [SPEC] Warm-up of the trigger: native u needs 20 earlier bars of the continuous series (rolling 100, shifted). Memory M / hold n of the variant: 2 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 1030; share whose signal bar is bar 0 of the session: 0.05; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 6, 58, 147.5, 2070.
- [SPEC] Held weeks only: 721 grid trades; share on bar 0: 0.05; signal-bar index quantiles: 0, 5, 54, 133, 767.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: RVWAP0 171, LVWAP0 153, VWAP0 142, YVWAP 61, AVPDH 59, AVPDL 52, WVWAP 46, MVWAP 37.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/Wc7c3f9c5_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 313, first known 2026-10-23T13:30:01.544Z, last known 2026-10-23T15:59:01.851Z; rebuilt-from-tape check 313/313/313; threshold values: box_ticks=15, box_pts=3.750
SIGNALS (raw events of the session: 29 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
75,2026-10-23T13:43:22.208Z,-1,VWAP0__V,29115.02,29108.00,15.00,Y
82,2026-10-23T13:44:58.130Z,1,VWAP0__V,29114.95,29115.50,15.00,no
87,2026-10-23T13:45:14.741Z,-1,VWAP0__V,29114.98,29111.75,15.00,no
90,2026-10-23T13:46:11.793Z,1,LVWAP0__V,29105.05,29108.00,15.00,no
91,2026-10-23T13:46:19.115Z,-1,AVPDL__V,29119.57,29119.25,15.00,no
95,2026-10-23T13:47:27.268Z,-1,AVPDL__V,29119.49,29115.50,15.00,no
100,2026-10-23T13:49:18.210Z,1,VWAP0__V,29115.14,29119.25,15.00,no
105,2026-10-23T13:51:18.080Z,-1,AVPDL__V,29119.58,29119.25,15.00,no
106,2026-10-23T13:51:29.337Z,1,LVWAP0__V,29106.18,29108.00,15.00,no
108,2026-10-23T13:51:57.120Z,1,VWAP0__V,29115.16,29115.50,15.00,no
110,2026-10-23T13:52:16.555Z,1,AVPDL__V,29119.52,29123.00,15.00,no
118,2026-10-23T13:54:07.924Z,1,VWAP0__V,29115.62,29126.75,15.00,no
122,2026-10-23T13:56:06.679Z,1,LVWAP0__V,29107.49,29115.50,15.00,no
124,2026-10-23T13:56:32.849Z,1,VWAP0__V,29115.72,29123.00,15.00,no
130,2026-10-23T13:59:12.590Z,1,VWAP0__V,29115.91,29149.25,15.00,no
177,2026-10-23T14:18:07.215Z,-1,VWAP0__V,29121.28,29111.75,15.00,no
184,2026-10-23T14:21:00.297Z,1,VWAP0__V,29120.93,29123.00,15.00,no
186,2026-10-23T14:21:18.222Z,1,AVPDL__V,29123.62,29156.75,15.00,no
195,2026-10-23T14:26:19.893Z,-1,VWAP0__V,29121.49,29119.25,15.00,no
197,2026-10-23T14:27:44.757Z,-1,RVWAP0__V,29105.63,29100.50,15.00,no
202,2026-10-23T14:29:26.629Z,1,VWAP0__V,29121.12,29123.00,15.00,no
204,2026-10-23T14:30:28.365Z,1,AVPDL__V,29123.71,29134.25,15.00,no
207,2026-10-23T14:33:05.550Z,-1,AVPDH__V,29190.23,29171.75,15.00,no
218,2026-10-23T14:41:18.172Z,1,AVPDH__V,29190.08,29243.00,16.88,Y
238,2026-10-23T14:55:25.008Z,1,YVWAP__V,29283.77,29288.00,15.00,no
249,2026-10-23T15:05:41.082Z,-1,YVWAP__V,29283.77,29269.25,15.00,no
289,2026-10-23T15:29:05.385Z,-1,YVWAP__V,29283.77,29269.25,15.00,no
297,2026-10-23T15:39:59.134Z,-1,YVWAP__V,29283.77,29261.75,15.00,no
307,2026-10-23T15:54:22.076Z,-1,YVWAP__V,29283.77,29276.75,15.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
75,-1,2026-10-23T13:43:23.221Z,29100.25,0.1776,29100.21,2026-10-23T14:38:55.140Z,29220.50,Stop,120.0,120.0,-120.29,-2410.73
218,1,2026-10-23T14:41:19.225Z,29253.75,0.1776,29253.79,2026-10-23T15:59:59.487Z,29293.50,SessionEnd,120.0,120.0,39.71,789.27
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 16 of 313 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
69,2026-10-23T13:41:21.904Z,29055.50,29066.75,29055.50,29066.75,15.00,2026-10-23T13:41:01Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
70,2026-10-23T13:41:33.050Z,29063.00,29063.00,29048.00,29048.00,15.00,2026-10-23T13:41:21Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
71,2026-10-23T13:42:01.984Z,29051.75,29089.25,29051.75,29089.25,15.00,2026-10-23T13:41:33Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
72,2026-10-23T13:42:04.548Z,29085.50,29085.50,29078.00,29078.00,15.00,2026-10-23T13:42:01Z,2026-10-23T13:42:00Z,,LVWAP0=29104.89,
73,2026-10-23T13:42:39.825Z,29081.75,29119.25,29081.75,29119.25,15.00,2026-10-23T13:42:04Z,2026-10-23T13:42:00Z,VWAP0=29115.23,AVPDL=29119.90,
74,2026-10-23T13:43:08.973Z,29115.50,29115.50,29093.00,29093.00,15.00,2026-10-23T13:42:39Z,2026-10-23T13:42:00Z,,LVWAP0=29104.89,
75,2026-10-23T13:43:22.208Z,29096.75,29108.00,29096.75,29108.00,15.00,2026-10-23T13:43:08Z,2026-10-23T13:43:00Z,LVWAP0=29104.78,VWAP0=29115.02,-1 VWAP0
76,2026-10-23T13:43:33.469Z,29104.25,29104.25,29093.00,29093.00,15.00,2026-10-23T13:43:22Z,2026-10-23T13:43:00Z,,LVWAP0=29104.78,
...
212,2026-10-23T14:35:28.128Z,29156.75,29156.75,29145.50,29145.50,15.00,2026-10-23T14:35:15Z,2026-10-23T14:35:00Z,AVPDL=29124.72,AVPDH=29190.07,
213,2026-10-23T14:36:02.444Z,29149.25,29168.00,29149.25,29168.00,15.00,2026-10-23T14:35:28Z,2026-10-23T14:35:00Z,AVPDL=29124.72,AVPDH=29190.07,
214,2026-10-23T14:36:13.058Z,29164.25,29164.25,29141.75,29141.75,15.00,2026-10-23T14:36:02Z,2026-10-23T14:36:00Z,AVPDL=29124.84,AVPDH=29190.02,
215,2026-10-23T14:37:08.576Z,29145.50,29190.50,29145.50,29190.50,15.00,2026-10-23T14:36:13Z,2026-10-23T14:36:00Z,AVPDH=29190.02,YVWAP=29283.77,
216,2026-10-23T14:37:31.965Z,29186.75,29186.75,29160.50,29160.50,16.88,2026-10-23T14:37:08Z,2026-10-23T14:37:00Z,AVPDL=29125.01,AVPDH=29189.99,
217,2026-10-23T14:40:46.631Z,29164.25,29254.25,29164.25,29254.25,16.88,2026-10-23T14:37:31Z,2026-10-23T14:37:00Z,AVPDH=29189.99,YVWAP=29283.77,
218,2026-10-23T14:41:18.172Z,29250.50,29250.50,29243.00,29243.00,16.88,2026-10-23T14:40:46Z,2026-10-23T14:40:00Z,AVPDH=29190.08,YVWAP=29283.77,+1 AVPDH
219,2026-10-23T14:42:12.437Z,29246.75,29258.00,29246.75,29258.00,16.88,2026-10-23T14:41:18Z,2026-10-23T14:41:00Z,AVPDH=29190.21,YVWAP=29283.77,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=75 2026-10-23T13:43:22.208Z side -1 fired VWAP0: VWAP0=29115.02; LVWAP0=29104.78; YVWAP=29283.77; AVPDH=29197.54; AVPDL=29119.68; WVWAP=29621.16; MVWAP=30398.08
k=218 2026-10-23T14:41:18.172Z side +1 fired AVPDH: VWAP0=29124.04; RVWAP0=29113.59; LVWAP0=29120.87; YVWAP=29283.77; AVPDH=29190.08; AVPDL=29126.01; WVWAP=29602.35; MVWAP=30383.11
```

#### td 20261016 (sess_id 202610163, NYAM session, grid week 184)
- bars of the session: 256, first known 2026-10-16T13:30:00.829Z, last known 2026-10-16T15:56:48.331Z; rebuilt-from-tape check 256/256/256; threshold values: box_ticks=15, box_pts=3.750
SIGNALS (raw events of the session: 13 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
6,2026-10-16T13:30:58.703Z,1,AVPDL__V,30000.28,30001.00,15.00,Y
11,2026-10-16T13:31:53.202Z,-1,AVPDL__V,30000.47,29989.75,15.00,no
16,2026-10-16T13:32:44.113Z,1,AVPDL__V,30000.40,30008.50,15.00,no
25,2026-10-16T13:34:18.371Z,-1,AVPDL__V,30000.46,29993.50,15.00,no
32,2026-10-16T13:36:48.610Z,1,YVWAP__V,29921.82,29929.75,15.00,no
39,2026-10-16T13:37:55.235Z,-1,YVWAP__V,29921.82,29918.50,15.00,no
58,2026-10-16T13:45:10.112Z,1,YVWAP__V,29921.82,29926.00,15.00,Y
67,2026-10-16T13:47:06.558Z,-1,RVWAP0__V,29942.43,29933.50,15.00,no
73,2026-10-16T13:49:59.957Z,-1,YVWAP__V,29921.82,29903.50,15.00,no
174,2026-10-16T14:37:53.194Z,1,RVWAP0__V,29883.79,29888.50,15.00,Y
180,2026-10-16T14:44:35.988Z,1,RVWAP0__V,29885.02,29911.00,15.00,no
186,2026-10-16T14:49:59.019Z,1,YVWAP__V,29921.82,29926.00,15.00,no
189,2026-10-16T14:53:28.066Z,-1,RVWAP0__V,29887.17,29877.25,15.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
6,1,2026-10-16T13:30:59.741Z,30014.00,0.1776,30014.04,2026-10-16T13:37:57.265Z,29893.75,Stop,120.0,120.0,-120.29,-2410.73
58,1,2026-10-16T13:45:11.140Z,29934.25,0.1776,29934.29,2026-10-16T13:51:43.184Z,29814.00,Stop,120.0,120.0,-120.29,-2410.73
174,1,2026-10-16T14:37:54.517Z,29901.25,0.1776,29901.29,2026-10-16T15:05:23.308Z,29781.00,Stop,120.0,120.0,-120.29,-2410.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 24 of 256 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-16T13:30:00.829Z,30023.50,30023.50,30019.75,30019.75,15.00,2026-10-16T13:29:01Z,2026-10-16T13:29:00Z,AVPDL=30000.19,VWAP0=30101.75,
1,2026-10-16T13:30:04.859Z,30023.50,30042.25,30023.50,30042.25,15.00,2026-10-16T13:30:00Z,2026-10-16T13:30:00Z,AVPDL=30000.28,VWAP0=30100.90,
2,2026-10-16T13:30:25.750Z,30038.50,30038.50,29986.00,29986.00,15.00,2026-10-16T13:30:04Z,2026-10-16T13:30:00Z,YVWAP=29921.82,AVPDL=30000.28,
3,2026-10-16T13:30:43.108Z,29989.75,30008.50,29989.75,30008.50,15.00,2026-10-16T13:30:25Z,2026-10-16T13:30:00Z,AVPDL=30000.28,VWAP0=30100.90,
4,2026-10-16T13:30:44.999Z,30004.75,30004.75,29997.25,29997.25,15.00,2026-10-16T13:30:43Z,2026-10-16T13:30:00Z,YVWAP=29921.82,AVPDL=30000.28,
5,2026-10-16T13:30:53.614Z,30001.00,30012.25,30001.00,30012.25,15.00,2026-10-16T13:30:44Z,2026-10-16T13:30:00Z,AVPDL=30000.28,VWAP0=30100.90,
6,2026-10-16T13:30:58.703Z,30008.50,30008.50,30001.00,30001.00,15.00,2026-10-16T13:30:53Z,2026-10-16T13:30:00Z,AVPDL=30000.28,VWAP0=30100.90,+1 AVPDL
7,2026-10-16T13:31:02.291Z,30004.75,30016.00,30004.75,30016.00,15.00,2026-10-16T13:30:58Z,2026-10-16T13:30:00Z,AVPDL=30000.28,VWAP0=30100.90,
...
52,2026-10-16T13:43:22.460Z,29896.00,29896.00,29884.75,29884.75,15.00,2026-10-16T13:43:11Z,2026-10-16T13:43:00Z,,YVWAP=29921.82,
53,2026-10-16T13:43:38.445Z,29888.50,29907.25,29888.50,29907.25,15.00,2026-10-16T13:43:22Z,2026-10-16T13:43:00Z,,YVWAP=29921.82,
54,2026-10-16T13:43:52.509Z,29903.50,29903.50,29884.75,29884.75,15.00,2026-10-16T13:43:38Z,2026-10-16T13:43:00Z,,YVWAP=29921.82,
55,2026-10-16T13:44:20.717Z,29888.50,29899.75,29888.50,29899.75,15.00,2026-10-16T13:43:52Z,2026-10-16T13:43:00Z,,YVWAP=29921.82,
56,2026-10-16T13:44:26.933Z,29896.00,29896.00,29888.50,29888.50,15.00,2026-10-16T13:44:20Z,2026-10-16T13:44:00Z,,YVWAP=29921.82,
57,2026-10-16T13:45:06.060Z,29892.25,29941.00,29892.25,29941.00,15.00,2026-10-16T13:44:26Z,2026-10-16T13:44:00Z,YVWAP=29921.82,AVPDL=29995.50,
58,2026-10-16T13:45:10.112Z,29937.25,29937.25,29926.00,29926.00,15.00,2026-10-16T13:45:06Z,2026-10-16T13:45:00Z,YVWAP=29921.82,RVWAP0=29943.45,+1 YVWAP
59,2026-10-16T13:45:11.690Z,29929.75,29937.25,29929.75,29937.25,15.00,2026-10-16T13:45:10Z,2026-10-16T13:45:00Z,YVWAP=29921.82,RVWAP0=29943.45,
...
168,2026-10-16T14:32:05.639Z,29817.25,29817.25,29809.75,29809.75,15.00,2026-10-16T14:31:53Z,2026-10-16T14:31:00Z,,RVWAP0=29885.42,
169,2026-10-16T14:34:13.301Z,29813.50,29877.25,29813.50,29877.25,15.00,2026-10-16T14:32:05Z,2026-10-16T14:32:00Z,,RVWAP0=29884.81,
170,2026-10-16T14:34:59.451Z,29873.50,29873.50,29858.50,29858.50,15.00,2026-10-16T14:34:13Z,2026-10-16T14:34:00Z,,RVWAP0=29883.91,
171,2026-10-16T14:35:28.371Z,29862.25,29888.50,29862.25,29888.50,15.00,2026-10-16T14:34:59Z,2026-10-16T14:34:00Z,RVWAP0=29883.91,YVWAP=29921.82,
172,2026-10-16T14:36:30.160Z,29884.75,29884.75,29877.25,29877.25,15.00,2026-10-16T14:35:28Z,2026-10-16T14:35:00Z,,RVWAP0=29883.78,
173,2026-10-16T14:37:34.193Z,29881.00,29903.50,29881.00,29903.50,15.00,2026-10-16T14:36:30Z,2026-10-16T14:36:00Z,RVWAP0=29883.75,YVWAP=29921.82,
174,2026-10-16T14:37:53.194Z,29899.75,29899.75,29888.50,29888.50,15.00,2026-10-16T14:37:34Z,2026-10-16T14:37:00Z,RVWAP0=29883.79,YVWAP=29921.82,+1 RVWAP0
175,2026-10-16T14:39:29.674Z,29892.25,29922.25,29892.25,29922.25,15.00,2026-10-16T14:37:53Z,2026-10-16T14:37:00Z,YVWAP=29921.82,LVWAP0=29954.37,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=6 2026-10-16T13:30:58.703Z side +1 fired AVPDL: VWAP0=30100.90; LVWAP0=30110.62; YVWAP=29921.82; AVPDH=30109.46; AVPDL=30000.28; WVWAP=30407.24; MVWAP=30832.27
k=58 2026-10-16T13:45:10.112Z side +1 fired YVWAP: VWAP0=30054.73; RVWAP0=29943.45; LVWAP0=30038.08; YVWAP=29921.82; AVPDH=30069.15; AVPDL=29995.17; WVWAP=30397.13; MVWAP=30824.38
k=174 2026-10-16T14:37:53.194Z side +1 fired RVWAP0: VWAP0=29982.54; RVWAP0=29883.79; LVWAP0=29954.37; YVWAP=29921.82; AVPDH=30000.95; AVPDL=29974.41; WVWAP=30375.58; MVWAP=30808.37
```

#### td 20261009 (sess_id 202610093, NYAM session, grid week 183)
- bars of the session: 120, first known 2026-10-09T13:30:25.734Z, last known 2026-10-09T15:58:55.591Z; rebuilt-from-tape check 120/120/120; threshold values: box_ticks=16, box_pts=4.000
SIGNALS (raw events of the session: 22 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
3,2026-10-09T13:31:50.842Z,-1,VWAP0__V,31141.12,31135.00,16.00,Y
8,2026-10-09T13:33:37.215Z,1,MVWAP__V,31120.96,31135.00,16.00,no
11,2026-10-09T13:36:00.679Z,-1,VWAP0__V,31141.07,31123.00,16.00,no
13,2026-10-09T13:38:06.979Z,-1,MVWAP__V,31121.00,31103.00,16.00,no
16,2026-10-09T13:39:38.075Z,1,YVWAP__V,31084.65,31095.00,16.00,no
19,2026-10-09T13:41:41.056Z,-1,MVWAP__V,31120.92,31107.00,16.00,no
20,2026-10-09T13:41:52.542Z,1,YVWAP__V,31084.65,31091.00,16.00,no
25,2026-10-09T13:44:23.992Z,-1,YVWAP__V,31084.65,31067.00,16.00,no
35,2026-10-09T13:49:39.064Z,-1,AVPDL__V,31033.42,31031.00,16.00,Y
43,2026-10-09T13:56:47.079Z,-1,AVPDL__V,31032.98,31031.00,20.00,no
57,2026-10-09T14:05:54.384Z,-1,AVPDL__V,31032.73,31031.00,16.00,no
67,2026-10-09T14:15:25.301Z,-1,AVPDL__V,31032.70,31031.00,18.00,no
74,2026-10-09T14:21:17.975Z,1,AVPDL__V,31032.67,31035.00,18.00,no
78,2026-10-09T14:26:05.067Z,1,AVPDL__V,31032.76,31039.00,16.00,no
87,2026-10-09T14:39:47.708Z,-1,AVPDH__V,31067.65,31067.00,16.00,no
89,2026-10-09T14:46:58.235Z,-1,RVWAP0__V,31063.13,31059.00,16.00,no
92,2026-10-09T14:54:53.151Z,1,RVWAP0__V,31062.04,31071.00,18.00,no
101,2026-10-09T15:14:41.481Z,-1,RVWAP0__V,31063.30,31051.00,18.00,no
102,2026-10-09T15:16:42.053Z,1,AVPDL__V,31035.60,31039.00,18.00,no
111,2026-10-09T15:33:35.243Z,-1,RVWAP0__V,31062.42,31047.00,16.00,no
114,2026-10-09T15:42:14.618Z,1,AVPDL__V,31036.35,31059.00,16.00,no
118,2026-10-09T15:57:33.436Z,1,RVWAP0__V,31061.79,31079.00,16.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
3,-1,2026-10-09T13:31:51.858Z,31124.00,0.1776,31123.96,2026-10-09T13:48:41.038Z,31003.96,Target,120.0,120.0,120.00,2395.16
35,-1,2026-10-09T13:49:40.072Z,31018.50,0.1776,31018.46,2026-10-09T15:59:59.766Z,31063.50,SessionEnd,120.0,120.0,-45.04,-905.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 13 of 120 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-09T13:30:25.734Z,31167.00,31167.00,31127.00,31127.00,16.00,2026-10-09T13:28:00Z,2026-10-09T13:28:00Z,MVWAP=31120.89,VWAP0=31140.57,
1,2026-10-09T13:30:50.212Z,31131.00,31151.00,31131.00,31151.00,16.00,2026-10-09T13:30:25Z,2026-10-09T13:30:00Z,VWAP0=31140.95,LVWAP0=31204.39,
2,2026-10-09T13:31:26.016Z,31147.00,31147.00,31119.00,31119.00,16.00,2026-10-09T13:30:50Z,2026-10-09T13:30:00Z,YVWAP=31084.65,MVWAP=31120.91,
3,2026-10-09T13:31:50.842Z,31123.00,31135.00,31123.00,31135.00,16.00,2026-10-09T13:31:26Z,2026-10-09T13:31:00Z,MVWAP=31120.95,VWAP0=31141.12,-1 VWAP0
4,2026-10-09T13:32:01.249Z,31131.00,31131.00,31119.00,31119.00,16.00,2026-10-09T13:31:50Z,2026-10-09T13:31:00Z,YVWAP=31084.65,MVWAP=31120.95,
...
29,2026-10-09T13:45:04.845Z,31027.00,31035.00,31027.00,31035.00,16.00,2026-10-09T13:44:50Z,2026-10-09T13:44:00Z,AVPDL=31033.54,AVPDH=31071.94,
30,2026-10-09T13:45:08.113Z,31031.00,31031.00,31019.00,31019.00,16.00,2026-10-09T13:45:04Z,2026-10-09T13:45:00Z,,AVPDL=31033.62,
31,2026-10-09T13:45:20.350Z,31023.00,31047.00,31023.00,31047.00,16.00,2026-10-09T13:45:08Z,2026-10-09T13:45:00Z,AVPDL=31033.62,AVPDH=31071.76,
32,2026-10-09T13:47:15.692Z,31043.00,31043.00,31007.00,31007.00,16.00,2026-10-09T13:45:20Z,2026-10-09T13:45:00Z,,AVPDL=31033.62,
33,2026-10-09T13:48:10.681Z,31011.00,31035.00,31011.00,31035.00,16.00,2026-10-09T13:47:15Z,2026-10-09T13:47:00Z,AVPDL=31033.46,AVPDH=31071.32,
34,2026-10-09T13:48:47.843Z,31031.00,31031.00,30999.00,30999.00,16.00,2026-10-09T13:48:10Z,2026-10-09T13:48:00Z,,AVPDL=31033.42,
35,2026-10-09T13:49:39.064Z,31003.00,31031.00,31003.00,31031.00,16.00,2026-10-09T13:48:47Z,2026-10-09T13:48:00Z,,AVPDL=31033.42,-1 AVPDL
36,2026-10-09T13:49:55.373Z,31027.00,31027.00,31011.00,31011.00,16.00,2026-10-09T13:49:39Z,2026-10-09T13:49:00Z,,AVPDL=31033.31,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=3 2026-10-09T13:31:50.842Z side -1 fired VWAP0: VWAP0=31141.12; LVWAP0=31200.08; YVWAP=31084.65; AVPDH=31069.25; AVPDL=31023.89; WVWAP=31261.58; MVWAP=31120.95
k=35 2026-10-09T13:49:39.064Z side -1 fired AVPDL: VWAP0=31128.41; RVWAP0=31098.68; LVWAP0=31160.22; YVWAP=31084.65; AVPDH=31071.17; AVPDL=31033.42; WVWAP=31257.82; MVWAP=31120.56
```

### BOOK We3999e99 (NYAM): pnf_7 + fibr dev level reject (tol 0.5, conf body), BOTH sides, bracket asym15u/30u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id We3999e99 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_We3999e99_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/We3999e99.parquet` (4359 events: 2176 long, 2183 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `pnf_7`, module `trig_levels_fibr_dev` (code/th_grid/trig_levels_fibr_dev.py -> triggers_d/lv_fibr_dev.py), variant `reject`, params {"tol": 0.5, "conf": "body"}, bracket `asym15u/30u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/pnf_7/trig_levels_fibr_dev.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 946, L6M 1542, L3M 1632; t 4.1 over 617 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored -120.54 / mine -120.54 pts, 1 / 1 trades; w183 2026-10-04 stored 177.72 / mine 177.72 pts, 2 / 2 trades; w184 2026-10-11 stored 0.00 / mine 0.00 pts, 0 / 0 trades; w185 2026-10-18 stored 119.76 / mine 119.76 pts, 1 / 1 trades

**1. BAR**
**BAR** row `pnf_7` = POINT-AND-FIGURE column bar. [SPEC] kernel th_bars/kernels.py k_pnf (lines 248-273), built by build_month.py line 135-136: box B = max(1, round(7 x s_rng)) ticks (numpy round half to even; 1 tick = 0.25 pt), 3-box reversal. State per session key: first print sets lvl = st = p, d = 0. d = 0: a print >= lvl + B starts an UP column (st = lvl, lvl += ((p-lvl)//B) x B); a print <= lvl - B starts a DOWN column (mirror). d = +1: p >= lvl + B extends (lvl += ((p-lvl)//B) x B); p <= lvl - 3B CLOSES the column: bar o = st, h = lvl, l = st, c = lvl, then a DOWN column starts with st = lvl - B and lvl = lvl - ((lvl-p)//B) x B. d = -1 mirror (bar o = st, h = st, l = lvl, c = lvl; new st = lvl + B). One bar per COMPLETED column; known time = timestamp of the confirming print (the print that moved 3 boxes against the column); the unfinished column at the session end is never a bar; there are no part=1 bars. Resets at every session boundary (02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET) and at a contract roll. [SPEC] Price-only: unaffected by the print rule (D8_BUILD_SPEC line 13; D8_PRINT_RULE). Box on the three sample days: 20261019: box_ticks=16, box_pts=4.00; 20261008: box_ticks=16, box_pts=4.00; 20260928: box_ticks=15, box_pts=3.75.
- [SPEC] Bars per NYAM session in the loaded months: median 173 (min 11, max 769, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/pnf_7/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261019: 211 stored / 211 rebuilt / 211 identical (o,h,l,c,known_ts,part); td 20261008: 80 stored / 80 rebuilt / 80 identical (o,h,l,c,known_ts,part); td 20260928: 184 stored / 184 rebuilt / 184 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec only**: pnf_7 specified in D8_BUILD_SPEC (L9c2622b0, Asia; stored Asia bars rebuilt identical in D8_ASIA_NEWBOOK_INPUTS.md) and pnf_14 in D8_NYAM_SPEC_L43f0cbfb; NO class for it in D8Asia.cs (class list read): box is a parameter, so pnf_5 / pnf_10 are parameter changes of a builder that is specified but not yet in the strategy file.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_fibr_dev` (th_grid/triggers_d/lv_fibr_dev.py; lines fd_levels2.py lines 139-147 (dev_range)). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 18 lines FIBR_DEV_*. H, L = the DEVELOPING range of the CURRENT session of the minute grid: session boundaries at tord 480 (02:00 ET), 870 (08:30), 930 (09:30), 1080 (12:00), 1260 (16:00) [i.e. codes Asia 0 / London 1 / pre 2 / NY AM 3 / NY PM 4 / close 5]; running high / low of the minutes of the current session strictly before minute i, reset at each boundary; NaN on the first minute of a session.
- Range fibs (fd_levels2.py range_fib, lines 131-137): with range R = H - L (NaN unless R >= 8 points): DNxxx = H - r R and UPxxx = L + r R for r = 0.236, 0.382, 0.5, 0.618, 0.65, 0.786 (names DN236 DN382 DN500 DN618 DN650 DN786 UP236 .. UP786); XUxxxx = H + (e-1) R for e = 1.272, 1.618, 2.0 (XU1272 XU1618 XU2000); XDxxxx = L - (e-1) R (XD1272 XD1618 XD2000). List order: DN236 DN382 DN500 DN618 DN650 DN786 UP236 UP382 UP500 UP618 UP650 UP786 XU1272 XU1618 XU2000 XD1272 XD1618 XD2000 (18 lines).
[SPEC] CONSEQUENCE: the lines are rebuilt every minute and restart at every session boundary; the first NY AM bar's decision time T0 lies in the pre-market session (08:30-09:30), so on that bar the lines are the PRE-MARKET developing range; from the second NY AM bar on, the lines are the NY AM developing range (and need R >= 8 pt).
Variant `reject` (tol=0.5, conf=body): [SPEC] reject(tol, conf) (fd_common.level_events): SHORT if previous close pc < L and high >= L - tol*u and close < L (conf 'body': also close < open); LONG if pc > L and low <= L + tol*u and close > L (conf 'body': also close > open); edge().
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: tol=0.5 (x u), conf=body -> tol*u = 2.500 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): FIBR_DEV_DN236 0.97, FIBR_DEV_DN382 0.97, FIBR_DEV_DN500 0.97, FIBR_DEV_DN618 0.97, FIBR_DEV_DN650 0.97, FIBR_DEV_DN786 0.97, FIBR_DEV_UP236 0.97, FIBR_DEV_UP382 0.97, FIBR_DEV_UP500 0.97, FIBR_DEV_UP618 0.97, FIBR_DEV_UP650 0.97, FIBR_DEV_UP786 0.97, FIBR_DEV_XU1272 0.97, FIBR_DEV_XU1618 0.97, FIBR_DEV_XU2000 0.97, FIBR_DEV_XD1272 0.97, FIBR_DEV_XD1618 0.97, FIBR_DEV_XD2000 0.97.
- [READING] Module status: **NEW**: no spec.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `asym15u/30u` = unit rule asym15u/30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule asym15u/30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: None beyond the session's own minutes (needs R >= 8 pt).
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 41; share whose signal bar is bar 0 of the session: 1.00; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 0, 0, 0, 0.
- [SPEC] Held weeks only: 4 grid trades; share on bar 0: 1.00; signal-bar index quantiles: 0, 0, 0, 0, 0.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: FIBR_DEV_DN236 3, FIBR_DEV_DN500 1.
- **FLAG [SPEC]: every / almost every grid trade of this book is a bar-0 signal** (n = 41, share 1.00) although the lines are finite on later bars (mean finite share 0.97). Bar 0 takes its level values AND its memory from the previous session (T0 = last bar of the previous session): a coder who builds the lines only from the current session's data would not reproduce them.  [READING] On point-and-figure bars a `reject` needs the signal bar to touch the level (low or high within tol x u of it, here tol x u = 2.50 pt) while the previous close lies on the other side of the level; a P&F column opens one box (here about 3 to 5 pt) beyond the previous column's close, so after a column ends beyond the level the next column's extreme cannot come back within tol x u; only bar 0, where the level of the previous session replaces the level of the current one, can fire. (Not tested by an experiment here.)

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/We3999e99_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261019 (sess_id 202610193, NYAM session, grid week 185)
- bars of the session: 211, first known 2026-10-19T13:30:00.240Z, last known 2026-10-19T15:57:02.256Z; rebuilt-from-tape check 211/211/211; threshold values: box_ticks=16, box_pts=4.000
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-19T13:30:00.240Z,1,FIBR_DEV_DN236,29781.33,29786.50,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,1,2026-10-19T13:30:01.243Z,29772.75,0.1776,29772.79,2026-10-19T15:05:53.547Z,29892.79,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 2 of 211 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-19T13:30:00.240Z,29778.50,29786.50,29778.50,29786.50,5.00,2026-10-19T13:29:23Z,2026-10-19T13:29:00Z,FIBR_DEV_UP786=29782.53,FIBR_DEV_XU1272=29809.14,+1 FIBR_DEV_DN236
1,2026-10-19T13:30:16.114Z,29782.50,29782.50,29730.50,29730.50,5.00,2026-10-19T13:30:00Z,2026-10-19T13:30:00Z,,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-19T13:30:00.240Z side +1 fired FIBR_DEV_DN236: FIBR_DEV_DN236=29781.33; FIBR_DEV_DN382=29773.34; FIBR_DEV_DN500=29766.88; FIBR_DEV_DN618=29760.41; FIBR_DEV_DN650=29758.66; FIBR_DEV_DN786=29751.22; FIBR_DEV_UP236=29752.42; FIBR_DEV_UP382=29760.41; FIBR_DEV_UP500=29766.88; FIBR_DEV_UP618=29773.34; FIBR_DEV_UP650=29775.09; FIBR_DEV_UP786=29782.53; FIBR_DEV_XU1272=29809.14; FIBR_DEV_XU1618=29828.09; FIBR_DEV_XU2000=29849.00; FIBR_DEV_XD1272=29724.61; FIBR_DEV_XD1618=29705.66; FIBR_DEV_XD2000=29684.75
```

#### td 20261008 (sess_id 202610083, NYAM session, grid week 183)
- bars of the session: 80, first known 2026-10-08T13:30:01.317Z, last known 2026-10-08T15:57:53.282Z; rebuilt-from-tape check 80/80/80; threshold values: box_ticks=16, box_pts=4.000
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-08T13:30:01.317Z,1,FIBR_DEV_DN236,31234.34,31242.25,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,1,2026-10-08T13:30:02.329Z,31231.00,0.1776,31231.04,2026-10-08T14:28:37.517Z,31351.04,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 2 of 80 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-08T13:30:01.317Z,31234.25,31242.25,31234.25,31242.25,5.00,2026-10-08T13:24:22Z,2026-10-08T13:24:00Z,FIBR_DEV_UP786=31236.24,FIBR_DEV_XU1272=31278.28,+1 FIBR_DEV_DN236
1,2026-10-08T13:30:39.968Z,31238.25,31238.25,31198.25,31198.25,5.00,2026-10-08T13:30:01Z,2026-10-08T13:30:00Z,,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-08T13:30:01.317Z side +1 fired FIBR_DEV_DN236: FIBR_DEV_DN236=31234.34; FIBR_DEV_DN382=31221.71; FIBR_DEV_DN500=31211.50; FIBR_DEV_DN618=31201.29; FIBR_DEV_DN650=31198.53; FIBR_DEV_DN786=31186.76; FIBR_DEV_UP236=31188.66; FIBR_DEV_UP382=31201.29; FIBR_DEV_UP500=31211.50; FIBR_DEV_UP618=31221.71; FIBR_DEV_UP650=31224.47; FIBR_DEV_UP786=31236.24; FIBR_DEV_XU1272=31278.28; FIBR_DEV_XU1618=31308.21; FIBR_DEV_XU2000=31341.25; FIBR_DEV_XD1272=31144.72; FIBR_DEV_XD1618=31114.79; FIBR_DEV_XD2000=31081.75
```

#### td 20260928 (sess_id 202609283, NYAM session, grid week 182)
- bars of the session: 184, first known 2026-09-28T13:30:01.381Z, last known 2026-09-28T15:53:38.446Z; rebuilt-from-tape check 184/184/184; threshold values: box_ticks=15, box_pts=3.750
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-09-28T13:30:01.381Z,1,FIBR_DEV_DN500,30722.00,30729.25,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,1,2026-09-28T13:30:02.405Z,30715.50,0.1776,30715.54,2026-09-28T13:45:37.114Z,30595.25,Stop,120.0,120.0,-120.29,-2410.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 2 of 184 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-09-28T13:30:01.381Z,30718.00,30729.25,30718.00,30729.25,5.00,2026-09-28T13:29:29Z,2026-09-28T13:29:00Z,FIBR_DEV_DN500=30722.00,FIBR_DEV_DN382=30729.32,+1 FIBR_DEV_DN500
1,2026-09-28T13:30:07.733Z,30725.50,30725.50,30703.00,30703.00,5.00,2026-09-28T13:30:01Z,2026-09-28T13:30:00Z,,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-09-28T13:30:01.381Z side +1 fired FIBR_DEV_DN500: FIBR_DEV_DN236=30738.37; FIBR_DEV_DN382=30729.32; FIBR_DEV_DN500=30722.00; FIBR_DEV_DN618=30714.68; FIBR_DEV_DN650=30712.70; FIBR_DEV_DN786=30704.27; FIBR_DEV_UP236=30705.63; FIBR_DEV_UP382=30714.68; FIBR_DEV_UP500=30722.00; FIBR_DEV_UP618=30729.32; FIBR_DEV_UP650=30731.30; FIBR_DEV_UP786=30739.73; FIBR_DEV_XU1272=30769.86; FIBR_DEV_XU1618=30791.32; FIBR_DEV_XU2000=30815.00; FIBR_DEV_XD1272=30674.14; FIBR_DEV_XD1618=30652.68; FIBR_DEV_XD2000=30629.00
```

### BOOK W9fd5ca5d (NYAM): pnf_10 + piv floor level reject (tol 1.0, conf body), BOTH sides, bracket fixed60/120
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W9fd5ca5d (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_W9fd5ca5d_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W9fd5ca5d.parquet` (1819 events: 934 long, 885 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `pnf_10`, module `trig_levels_piv_floor` (code/th_grid/trig_levels_piv_floor.py -> triggers_d/lv_piv_floor.py), variant `reject`, params {"tol": 1.0, "conf": "body"}, bracket `fixed60/120`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/pnf_10/trig_levels_piv_floor.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 784, L6M 106, L3M -97; t 4.0 over 658 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored 0.00 / mine 0.00 pts, 0 / 0 trades; w183 2026-10-04 stored 0.00 / mine 0.00 pts, 0 / 0 trades; w184 2026-10-11 stored 0.00 / mine 0.00 pts, 0 / 0 trades; w185 2026-10-18 stored 0.00 / mine 0.00 pts, 0 / 0 trades

**1. BAR**
**BAR** row `pnf_10` = POINT-AND-FIGURE column bar. [SPEC] kernel th_bars/kernels.py k_pnf (lines 248-273), built by build_month.py line 135-136: box B = max(1, round(10 x s_rng)) ticks (numpy round half to even; 1 tick = 0.25 pt), 3-box reversal. State per session key: first print sets lvl = st = p, d = 0. d = 0: a print >= lvl + B starts an UP column (st = lvl, lvl += ((p-lvl)//B) x B); a print <= lvl - B starts a DOWN column (mirror). d = +1: p >= lvl + B extends (lvl += ((p-lvl)//B) x B); p <= lvl - 3B CLOSES the column: bar o = st, h = lvl, l = st, c = lvl, then a DOWN column starts with st = lvl - B and lvl = lvl - ((lvl-p)//B) x B. d = -1 mirror (bar o = st, h = st, l = lvl, c = lvl; new st = lvl + B). One bar per COMPLETED column; known time = timestamp of the confirming print (the print that moved 3 boxes against the column); the unfinished column at the session end is never a bar; there are no part=1 bars. Resets at every session boundary (02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET) and at a contract roll. [SPEC] Price-only: unaffected by the print rule (D8_BUILD_SPEC line 13; D8_PRINT_RULE). Box on the three sample days: 20260923: box_ticks=19, box_pts=4.75; 20260916: box_ticks=19, box_pts=4.75; 20260910: box_ticks=18, box_pts=4.50.
- [SPEC] Bars per NYAM session in the loaded months: median 91 (min 3, max 352, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/pnf_10/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20260923: 93 stored / 93 rebuilt / 93 identical (o,h,l,c,known_ts,part); td 20260916: 51 stored / 51 rebuilt / 51 identical (o,h,l,c,known_ts,part); td 20260910: 130 stored / 130 rebuilt / 130 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec only**: pnf_7 specified in D8_BUILD_SPEC (L9c2622b0, Asia; stored Asia bars rebuilt identical in D8_ASIA_NEWBOOK_INPUTS.md) and pnf_14 in D8_NYAM_SPEC_L43f0cbfb; NO class for it in D8Asia.cs (class list read): box is a parameter, so pnf_5 / pnf_10 are parameter changes of a builder that is specified but not yet in the strategy file.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_piv_floor` (th_grid/triggers_d/lv_piv_floor.py; lines fd_levels2.py lines 148-167). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 16 lines in this list order: PIV_D_P, PIV_D_R1, PIV_D_R2, PIV_D_R3, PIV_D_S1, PIV_D_S2, PIV_D_S3, PIV_W_P, PIV_W_R1, PIV_W_R2, PIV_W_R3, PIV_W_S1, PIV_W_S2, PIV_W_S3, CPR_TC, CPR_BC.
- Daily: from the prior RTH day high H, low L and close C (PD_RTH__H, PD_RTH__L, PD_C__C): P = (H+L+C)/3; R1 = 2P - L; S1 = 2P - H; R2 = P + (H-L); S2 = P - (H-L); R3 = H + 2(P - L); S3 = L - 2(H - P). Constant over the label day.
- Weekly: the same formulas from the previous ISO week's high / low / last 1-minute close (all minutes of that week, label-date weeks), constant over the next ISO week.
- CPR_BC = (H+L)/2, CPR_TC = 2P - BC from the prior RTH day.
- Raw price = adj - off.
Variant `reject` (tol=1.0, conf=body): [SPEC] reject(tol, conf) (fd_common.level_events): SHORT if previous close pc < L and high >= L - tol*u and close < L (conf 'body': also close < open); LONG if pc > L and low <= L + tol*u and close > L (conf 'body': also close > open); edge().
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: tol=1.0 (x u), conf=body -> tol*u = 5.000 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PIV_D_P 0.97, PIV_D_R1 0.97, PIV_D_R2 0.97, PIV_D_R3 0.97, PIV_D_S1 0.97, PIV_D_S2 0.97, PIV_D_S3 0.97, PIV_W_P 1.00, PIV_W_R1 1.00, PIV_W_R2 1.00, PIV_W_R3 1.00, PIV_W_S1 1.00, PIV_W_S2 1.00, PIV_W_S3 1.00, CPR_TC 0.97, CPR_BC 0.99.
- [READING] Module status: **lines exist in D8Asia.cs; trigger by parameter**: pivot lines (Piv()) and LevelBreakNative (break_native n=2, k) exist for L6b373671; plain break n=1, k=0 and the 16-line set incl. weekly and CPR need checking against pivLines.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `fixed60/120` = stop 60 pts / target 120 pts, fixed (no unit rule); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 60 pts / target 120 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: Prior RTH day and prior ISO week of 1-minute data (the live class Piv() in D8Asia.cs skips the first loaded week).
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 18; share whose signal bar is bar 0 of the session: 0.72; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 0, 0, 5.25, 104.
- [SPEC] 0 grid trades in the 4 held week(s) (the book stood in the Test 8 list but placed no trade in them); the dated sessions below are the latest sessions BEFORE the hold with trades (marked).

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W9fd5ca5d_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20260923 (sess_id 202609233, NYAM session, grid week 181, BEFORE the held period)
- bars of the session: 93, first known 2026-09-23T13:30:02.679Z, last known 2026-09-23T15:56:22.206Z; rebuilt-from-tape check 93/93/93; threshold values: box_ticks=19, box_pts=4.750
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
32,2026-09-23T14:01:57.364Z,1,PIV_D_S1,30840.00,30868.75,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
32,1,2026-09-23T14:01:58.412Z,30853.25,0.1776,30853.29,2026-09-23T14:07:40.750Z,30793.00,Stop,60.0,120.0,-60.29,-1210.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 93 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
26,2026-09-23T13:50:48.735Z,30878.25,30887.75,30878.25,30887.75,5.00,2026-09-23T13:50:03Z,2026-09-23T13:50:00Z,PIV_D_S1=30840.00,CPR_BC=30914.50,
27,2026-09-23T13:52:52.790Z,30883.00,30883.00,30845.00,30845.00,5.00,2026-09-23T13:50:48Z,2026-09-23T13:50:00Z,PIV_D_S1=30840.00,CPR_BC=30914.50,
28,2026-09-23T13:54:01.125Z,30849.75,30878.25,30849.75,30878.25,5.00,2026-09-23T13:52:52Z,2026-09-23T13:52:00Z,PIV_D_S1=30840.00,CPR_BC=30914.50,
29,2026-09-23T13:56:33.432Z,30873.50,30873.50,30835.50,30835.50,5.00,2026-09-23T13:54:01Z,2026-09-23T13:54:00Z,PIV_D_S2=30650.75,PIV_D_S1=30840.00,
30,2026-09-23T13:59:29.597Z,30840.25,30859.25,30840.25,30859.25,5.00,2026-09-23T13:56:33Z,2026-09-23T13:56:00Z,PIV_D_S1=30840.00,CPR_BC=30914.50,
31,2026-09-23T14:00:11.720Z,30854.50,30854.50,30840.25,30840.25,5.00,2026-09-23T13:59:29Z,2026-09-23T13:59:00Z,PIV_D_S1=30840.00,CPR_BC=30914.50,
32,2026-09-23T14:01:57.364Z,30845.00,30868.75,30845.00,30868.75,5.00,2026-09-23T14:00:11Z,2026-09-23T14:00:00Z,PIV_D_S1=30840.00,CPR_BC=30914.50,+1 PIV_D_S1
33,2026-09-23T14:05:03.137Z,30864.00,30864.00,30821.25,30821.25,5.00,2026-09-23T14:01:57Z,2026-09-23T14:01:00Z,PIV_D_S2=30650.75,PIV_D_S1=30840.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=32 2026-09-23T14:01:57.364Z side +1 fired PIV_D_S1: PIV_D_P=30952.75; PIV_D_R1=31142.00; PIV_D_R2=31254.75; PIV_D_R3=31444.00; PIV_D_S1=30840.00; PIV_D_S2=30650.75; PIV_D_S3=30538.00; PIV_W_P=29667.08; PIV_W_R1=30281.17; PIV_W_R2=30607.33; PIV_W_R3=31221.42; PIV_W_S1=29340.92; PIV_W_S2=28726.83; PIV_W_S3=28400.67; CPR_TC=30991.00; CPR_BC=30914.50
```

#### td 20260916 (sess_id 202609163, NYAM session, grid week 180, BEFORE the held period)
- bars of the session: 51, first known 2026-09-16T13:30:27.555Z, last known 2026-09-16T15:47:40.030Z; rebuilt-from-tape check 51/51/51; threshold values: box_ticks=19, box_pts=4.750
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-09-16T13:30:27.555Z,1,PIV_D_R1,29397.83,29420.00,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,1,2026-09-16T13:30:28.577Z,29403.00,0.1776,29403.04,2026-09-16T15:07:52.573Z,29523.04,Target,60.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 2 of 51 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-09-16T13:30:27.555Z,29386.75,29420.00,29386.75,29420.00,5.00,2026-09-16T13:23:15Z,2026-09-16T13:23:00Z,PIV_D_R1=29397.83,PIV_D_R2=29543.17,+1 PIV_D_R1
1,2026-09-16T13:30:41.501Z,29415.25,29415.25,29396.25,29396.25,5.00,2026-09-16T13:30:27Z,2026-09-16T13:30:00Z,CPR_BC=29331.12,PIV_D_R1=29397.83,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-09-16T13:30:27.555Z side +1 fired PIV_D_R1: PIV_D_P=29304.92; PIV_D_R1=29397.83; PIV_D_R2=29543.17; PIV_D_R3=29636.08; PIV_D_S1=29159.58; PIV_D_S2=29066.67; PIV_D_S3=28921.33; PIV_W_P=29692.25; PIV_W_R1=30050.75; PIV_W_R2=30416.50; PIV_W_R3=30775.00; PIV_W_S1=29326.50; PIV_W_S2=28968.00; PIV_W_S3=28602.25; CPR_TC=29278.71; CPR_BC=29331.12
```

#### td 20260910 (sess_id 202609103, NYAM session, grid week 179, BEFORE the held period)
- bars of the session: 130, first known 2026-09-10T13:30:16.908Z, last known 2026-09-10T15:58:33.855Z; rebuilt-from-tape check 130/130/130; threshold values: box_ticks=18, box_pts=4.500
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
104,2026-09-10T15:00:39.358Z,1,PIV_D_S2,29233.25,29265.00,5.00,Y
124,2026-09-10T15:45:34.901Z,1,PIV_D_S2,29233.25,29256.00,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
104,1,2026-09-10T15:00:40.480Z,29250.25,0.1776,29250.29,2026-09-10T15:56:33.902Z,29190.00,Stop,60.0,120.0,-60.29,-1210.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 130 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
98,2026-09-10T14:50:42.480Z,29220.00,29229.00,29220.00,29229.00,5.00,2026-09-10T14:48:30Z,2026-09-10T14:48:00Z,PIV_D_S3=29108.50,PIV_D_S2=29233.25,
99,2026-09-10T14:51:51.322Z,29224.50,29224.50,29211.00,29211.00,5.00,2026-09-10T14:50:42Z,2026-09-10T14:50:00Z,PIV_D_S3=29108.50,PIV_D_S2=29233.25,
100,2026-09-10T14:53:12.843Z,29215.50,29242.50,29215.50,29242.50,5.00,2026-09-10T14:51:51Z,2026-09-10T14:51:00Z,PIV_D_S2=29233.25,PIV_D_S1=29344.25,
101,2026-09-10T14:53:31.421Z,29238.00,29238.00,29229.00,29229.00,5.00,2026-09-10T14:53:12Z,2026-09-10T14:53:00Z,PIV_D_S3=29108.50,PIV_D_S2=29233.25,
102,2026-09-10T14:55:46.739Z,29233.50,29247.00,29233.50,29247.00,5.00,2026-09-10T14:53:31Z,2026-09-10T14:53:00Z,PIV_D_S2=29233.25,PIV_D_S1=29344.25,
103,2026-09-10T14:56:40.615Z,29242.50,29242.50,29233.50,29233.50,5.00,2026-09-10T14:55:46Z,2026-09-10T14:55:00Z,PIV_D_S2=29233.25,PIV_D_S1=29344.25,
104,2026-09-10T15:00:39.358Z,29238.00,29265.00,29238.00,29265.00,5.00,2026-09-10T14:56:40Z,2026-09-10T14:56:00Z,PIV_D_S2=29233.25,PIV_D_S1=29344.25,+1 PIV_D_S2
105,2026-09-10T15:03:32.379Z,29260.50,29260.50,29215.50,29215.50,5.00,2026-09-10T15:00:39Z,2026-09-10T15:00:00Z,PIV_D_S3=29108.50,PIV_D_S2=29233.25,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=104 2026-09-10T15:00:39.358Z side +1 fired PIV_D_S2: PIV_D_P=29469.00; PIV_D_R1=29580.00; PIV_D_R2=29704.75; PIV_D_R3=29815.75; PIV_D_S1=29344.25; PIV_D_S2=29233.25; PIV_D_S3=29108.50; PIV_W_P=29384.92; PIV_W_R1=29842.58; PIV_W_R2=30162.17; PIV_W_R3=30619.83; PIV_W_S1=29065.33; PIV_W_S2=28607.67; PIV_W_S3=28288.08; CPR_TC=29462.12; CPR_BC=29475.88
```

### BOOK W5ba295af (NYAM): urenko_40 + piv wf level retest (M 3, tol 0.5), BOTH sides, bracket sym30u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 17 of 17 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W5ba295af (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_W5ba295af_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W5ba295af.parquet` (5507 events: 2716 long, 2791 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `urenko_40`, module `trig_levels_piv_wf` (code/th_grid/trig_levels_piv_wf.py -> triggers_d/lv_piv_wf.py), variant `retest`, params {"M": 3, "tol": 0.5}, bracket `sym30u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/urenko_40/trig_levels_piv_wf.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1269, L6M 2483, L3M 10; t 4.1 over 1237 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 169..185 (2026-06-28 to 2026-10-24) = 17 held week(s); months in the cell file: 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored 221.38 / mine 221.38 pts, 7 / 7 trades; w182 2026-09-27 stored 24.60 / mine 24.60 pts, 9 / 9 trades; w183 2026-10-04 stored 66.58 / mine 66.58 pts, 6 / 6 trades; w184 2026-10-11 stored -347.28 / mine -347.28 pts, 9 / 9 trades; w185 2026-10-18 stored -64.64 / mine -64.64 pts, 5 / 5 trades (last 5 of 17 held weeks shown; 17 of 17 equal)

**1. BAR**
**BAR** row `urenko_40` = UniRenko (reversal = one full brick) RENKO. [SPEC] kernel k_renko (kernels.py lines 59-95), build_month.py lines 108-113: brick B = max(2, round(40 x s_rng)) ticks, reversal distance R = B, open offset O = 0, no wicks. State per session key: first print sets bo = bc = p, d = 0. d = 0: p >= bo + B -> up brick [bo, bo+B]; p <= bo - B -> down brick. d = +1: p >= bc + B -> continuation brick [bc, bc + B]; p <= bc - R -> reversal brick opening at bc - O = bc and closing at bc - R (height R, direction flips). Mirror for d = -1. A loop re-tests the same print, so one print can emit several bricks (same timestamp; volume to the first). Brick OHLC = (open, max, min, close) with no wicks; known time = timestamp of the completing print; no bar for an unfinished brick at the session end. Brick on the sample days: 20261023: brick_ticks=88, brick_pts=22.00, reversal_ticks=88; 20261016: brick_ticks=87, brick_pts=21.75, reversal_ticks=87; 20261009: brick_ticks=92, brick_pts=23.00, reversal_ticks=92. [SPEC] Price-only (D8_BUILD_SPEC line 13). [READING] urenko = the same kernel with R = B: a one-line change of FlexRenkoBuilder (reversal distance B instead of B/2).
- [SPEC] Bars per NYAM session in the loaded months: median 73 (min 6, max 284, 221 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/urenko_40/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 112 stored / 112 rebuilt / 112 identical (o,h,l,c,known_ts,part); td 20261016: 96 stored / 96 rebuilt / 96 identical (o,h,l,c,known_ts,part); td 20261009: 52 stored / 52 rebuilt / 52 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **new (one parameter from frenko)**: no urenko spec or class found; k_renko with R = B; FlexRenkoBuilder has R = B/2 (READING: a reversal-distance parameter).

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_piv_wf` (th_grid/triggers_d/lv_piv_wf.py; lines fd_levels2.py lines 148-167). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 17 lines in this list order: WOO_D_P, WOO_D_R1, WOO_D_S1, WOO_D_R2, WOO_D_S2, FPV_D_R1, FPV_D_R2, FPV_D_R3, FPV_D_S1, FPV_D_S2, FPV_D_S3, FPV_W_R1, FPV_W_R2, FPV_W_R3, FPV_W_S1, FPV_W_S2, FPV_W_S3.
- Woodie daily (H, L = prior RTH day high/low, Open = the 18:00 ET minute open of the CURRENT label day, OPEN_DAY__P, available from 18:01): Pw = (H + L + 2 Open)/4; R1 = 2Pw - L; S1 = 2Pw - H; R2 = Pw + (H-L); S2 = Pw - (H-L).
- Fibonacci pivots: P = (H+L+C)/3 and R = H-L from the prior RTH day (daily, FPV_D) or the previous ISO week (FPV_W); R1/R2/R3 = P + 0.382R / 0.618R / 1.0R; S1/S2/S3 = P - 0.382R / 0.618R / 1.0R.
- Raw price = adj - off.
Variant `retest` (M=3, tol=0.5): [SPEC] retest(M, tol) (fd_common.level_events; the retest grid has no k, so k = 0): a break-up EDGE = edge(close > L); LONG if a break-up edge happened on any of the previous M bars (bars j-M..j-1) and low <= L + tol*u and close > L and close >= open; SHORT mirrored (break-down edge within M bars, high >= L - tol*u, close < L, close <= open); edge().
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: M=3, tol=0.5 -> tol*u = 2.500 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 221 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): WOO_D_P 0.99, WOO_D_R1 0.99, WOO_D_S1 0.99, WOO_D_R2 0.99, WOO_D_S2 0.99, FPV_D_R1 0.96, FPV_D_R2 0.96, FPV_D_R3 0.96, FPV_D_S1 0.96, FPV_D_S2 0.96, FPV_D_S3 0.96, FPV_W_R1 1.00, FPV_W_R2 1.00, FPV_W_R3 1.00, FPV_W_S1 1.00, FPV_W_S2 1.00, FPV_W_S3 1.00.
- [READING] Module status: **NEW**: Woodie and Fibonacci pivots are not in any spec page.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `sym30u` = unit rule sym30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule sym30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: Prior RTH day, prior ISO week, and the current day's 18:00 minute open.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 3 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 372; share whose signal bar is bar 0 of the session: 0.04; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 8, 29, 55.25, 249.
- [SPEC] Held weeks only: 130 grid trades; share on bar 0: 0.06; signal-bar index quantiles: 0, 3.25, 16, 42.75, 103.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: WOO_D_P 21, FPV_D_S1 17, FPV_D_R1 14, WOO_D_R1 14, WOO_D_S1 14, FPV_D_S2 11, FPV_D_R2 9, FPV_D_S3 6, FPV_D_R3 6, WOO_D_S2 5, FPV_W_S1 4, FPV_W_S2 3.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W5ba295af_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 112, first known 2026-10-23T13:30:01.042Z, last known 2026-10-23T15:59:41.843Z; rebuilt-from-tape check 112/112/112; threshold values: brick_ticks=88, brick_pts=22.000, reversal_ticks=88
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
11,2026-10-23T13:35:06.663Z,-1,FPV_D_S1,29042.99,29029.25,5.00,Y
22,2026-10-23T13:40:11.918Z,1,FPV_D_S1,29042.99,29051.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
11,-1,2026-10-23T13:35:07.868Z,29029.75,0.1776,29029.71,2026-10-23T13:52:24.953Z,29150.00,Stop,120.0,120.0,-120.29,-2410.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 112 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
5,2026-10-23T13:31:34.114Z,29051.25,29073.25,29051.25,29073.25,5.00,2026-10-23T13:30:46Z,2026-10-23T13:30:00Z,FPV_D_S1=29042.99,FPV_W_S1=29211.25,
6,2026-10-23T13:32:30.605Z,29073.25,29095.25,29073.25,29095.25,5.00,2026-10-23T13:31:34Z,2026-10-23T13:31:00Z,FPV_D_S1=29042.99,FPV_W_S1=29211.25,
7,2026-10-23T13:32:55.543Z,29095.25,29095.25,29073.25,29073.25,5.00,2026-10-23T13:32:30Z,2026-10-23T13:32:00Z,FPV_D_S1=29042.99,FPV_W_S1=29211.25,
8,2026-10-23T13:33:14.678Z,29073.25,29073.25,29051.25,29051.25,5.00,2026-10-23T13:32:55Z,2026-10-23T13:32:00Z,FPV_D_S1=29042.99,FPV_W_S1=29211.25,
9,2026-10-23T13:34:05.756Z,29051.25,29051.25,29029.25,29029.25,5.00,2026-10-23T13:33:14Z,2026-10-23T13:33:00Z,FPV_D_S2=28910.42,FPV_D_S1=29042.99,
10,2026-10-23T13:34:51.846Z,29029.25,29051.25,29029.25,29051.25,5.00,2026-10-23T13:34:05Z,2026-10-23T13:34:00Z,FPV_D_S1=29042.99,FPV_W_S1=29211.25,
11,2026-10-23T13:35:06.663Z,29051.25,29051.25,29029.25,29029.25,5.00,2026-10-23T13:34:51Z,2026-10-23T13:34:00Z,FPV_D_S2=28910.42,FPV_D_S1=29042.99,-1 FPV_D_S1
12,2026-10-23T13:35:46.295Z,29029.25,29029.25,29007.25,29007.25,5.00,2026-10-23T13:35:06Z,2026-10-23T13:35:00Z,FPV_D_S2=28910.42,FPV_D_S1=29042.99,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=11 2026-10-23T13:35:06.663Z side -1 fired FPV_D_S1: WOO_D_P=29215.19; WOO_D_R1=29397.38; WOO_D_S1=28835.62; WOO_D_R2=29776.94; WOO_D_S2=28653.44; FPV_D_R1=29472.17; FPV_D_R2=29604.74; FPV_D_R3=29819.33; FPV_D_S1=29042.99; FPV_D_S2=28910.42; FPV_D_S3=28695.83; FPV_W_R1=30754.91; FPV_W_R2=31231.75; FPV_W_R3=32003.58; FPV_W_S1=29211.25; FPV_W_S2=28734.41; FPV_W_S3=27962.58
```

#### td 20261016 (sess_id 202610163, NYAM session, grid week 184)
- bars of the session: 96, first known 2026-10-16T13:30:04.578Z, last known 2026-10-16T15:57:04.704Z; rebuilt-from-tape check 96/96/96; threshold values: brick_ticks=87, brick_pts=21.750, reversal_ticks=87
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
5,2026-10-16T13:32:37.577Z,1,WOO_D_P,29999.31,30023.50,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
5,1,2026-10-16T13:32:38.605Z,30014.75,0.1776,30014.79,2026-10-16T13:37:57.265Z,29894.50,Stop,120.0,120.0,-120.29,-2410.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 7 of 96 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-16T13:30:04.578Z,30023.50,30045.25,30023.50,30045.25,5.00,2026-10-16T13:29:55Z,2026-10-16T13:29:00Z,WOO_D_P=29999.31,FPV_D_R1=30205.86,
1,2026-10-16T13:30:05.996Z,30045.25,30045.25,30023.50,30023.50,5.00,2026-10-16T13:30:04Z,2026-10-16T13:30:00Z,WOO_D_P=29999.31,FPV_D_R1=30205.86,
2,2026-10-16T13:30:14.667Z,30023.50,30023.50,30001.75,30001.75,5.00,2026-10-16T13:30:05Z,2026-10-16T13:30:00Z,WOO_D_P=29999.31,FPV_D_R1=30205.86,
3,2026-10-16T13:31:18.305Z,30001.75,30001.75,29980.00,29980.00,5.00,2026-10-16T13:30:14Z,2026-10-16T13:30:00Z,WOO_D_S1=29801.88,WOO_D_P=29999.31,
4,2026-10-16T13:32:00.234Z,29980.00,30001.75,29980.00,30001.75,5.00,2026-10-16T13:31:18Z,2026-10-16T13:31:00Z,WOO_D_P=29999.31,FPV_D_R1=30205.86,
5,2026-10-16T13:32:37.577Z,30001.75,30023.50,30001.75,30023.50,5.00,2026-10-16T13:32:00Z,2026-10-16T13:32:00Z,WOO_D_P=29999.31,FPV_D_R1=30205.86,+1 WOO_D_P
6,2026-10-16T13:32:52.622Z,30023.50,30023.50,30001.75,30001.75,5.00,2026-10-16T13:32:37Z,2026-10-16T13:32:00Z,WOO_D_P=29999.31,FPV_D_R1=30205.86,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=5 2026-10-16T13:32:37.577Z side +1 fired WOO_D_P: WOO_D_P=29999.31; WOO_D_R1=30376.12; WOO_D_S1=29801.88; WOO_D_R2=30573.56; WOO_D_S2=29425.06; FPV_D_R1=30205.86; FPV_D_R2=30341.39; FPV_D_R3=30560.75; FPV_D_S1=29767.14; FPV_D_S2=29631.61; FPV_D_S3=29412.25; FPV_W_R1=31492.21; FPV_W_R2=31686.79; FPV_W_R3=32001.75; FPV_W_S1=30862.29; FPV_W_S2=30667.71; FPV_W_S3=30352.75
```

#### td 20261009 (sess_id 202610093, NYAM session, grid week 183)
- bars of the session: 52, first known 2026-10-09T13:30:10.538Z, last known 2026-10-09T15:50:03.564Z; rebuilt-from-tape check 52/52/52; threshold values: brick_ticks=92, brick_pts=23.000, reversal_ticks=92
SIGNALS (raw events of the session: 7 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
32,2026-10-09T14:23:54.097Z,1,WOO_D_P,31050.69,31052.00,5.00,Y
37,2026-10-09T14:48:41.609Z,-1,WOO_D_P,31050.69,31029.00,5.00,no
38,2026-10-09T14:50:16.035Z,1,WOO_D_P,31050.69,31052.00,5.00,no
43,2026-10-09T15:19:10.702Z,1,WOO_D_P,31050.69,31075.00,5.00,no
45,2026-10-09T15:27:36.995Z,1,WOO_D_P,31050.69,31075.00,5.00,no
49,2026-10-09T15:42:16.802Z,1,WOO_D_P,31050.69,31075.00,5.00,no
51,2026-10-09T15:50:03.564Z,1,WOO_D_P,31050.69,31075.00,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
32,1,2026-10-09T14:23:55.161Z,31049.25,0.1776,31049.29,2026-10-09T15:59:59.766Z,31063.00,SessionEnd,120.0,120.0,13.71,269.27
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 52 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
26,2026-10-09T14:07:43.657Z,31029.00,31052.00,31029.00,31052.00,5.00,2026-10-09T14:04:51Z,2026-10-09T14:04:00Z,WOO_D_P=31050.69,FPV_W_R1=31249.72,
27,2026-10-09T14:10:21.739Z,31052.00,31052.00,31029.00,31029.00,5.00,2026-10-09T14:07:43Z,2026-10-09T14:07:00Z,FPV_D_S1=30825.30,WOO_D_P=31050.69,
28,2026-10-09T14:11:16.249Z,31029.00,31029.00,31006.00,31006.00,5.00,2026-10-09T14:10:21Z,2026-10-09T14:10:00Z,FPV_D_S1=30825.30,WOO_D_P=31050.69,
29,2026-10-09T14:12:38.987Z,31006.00,31029.00,31006.00,31029.00,5.00,2026-10-09T14:11:16Z,2026-10-09T14:11:00Z,FPV_D_S1=30825.30,WOO_D_P=31050.69,
30,2026-10-09T14:19:41.683Z,31029.00,31052.00,31029.00,31052.00,5.00,2026-10-09T14:12:38Z,2026-10-09T14:12:00Z,WOO_D_P=31050.69,FPV_W_R1=31249.72,
31,2026-10-09T14:22:02.921Z,31052.00,31052.00,31029.00,31029.00,5.00,2026-10-09T14:19:41Z,2026-10-09T14:19:00Z,FPV_D_S1=30825.30,WOO_D_P=31050.69,
32,2026-10-09T14:23:54.097Z,31029.00,31052.00,31029.00,31052.00,5.00,2026-10-09T14:22:02Z,2026-10-09T14:22:00Z,WOO_D_P=31050.69,FPV_W_R1=31249.72,+1 WOO_D_P
33,2026-10-09T14:30:52.424Z,31052.00,31075.00,31052.00,31075.00,5.00,2026-10-09T14:23:54Z,2026-10-09T14:23:00Z,WOO_D_P=31050.69,FPV_W_R1=31249.72,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=32 2026-10-09T14:23:54.097Z side +1 fired WOO_D_P: WOO_D_P=31050.69; WOO_D_R1=31309.38; WOO_D_S1=30731.62; WOO_D_R2=31628.44; WOO_D_S2=30472.94; FPV_D_R1=31266.70; FPV_D_R2=31403.05; FPV_D_R3=31623.75; FPV_D_S1=30825.30; FPV_D_S2=30688.95; FPV_D_S3=30468.25; FPV_W_R1=31249.72; FPV_W_R2=31468.20; FPV_W_R3=31821.83; FPV_W_S1=30542.45; FPV_W_S2=30323.97; FPV_W_S3=29970.33
```

### BOOK Wbb4ef729 (NYAM): swing_pct_5 + vwap level break (n 2, k 0.25), BOTH sides, bracket sym15u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 43 of 43 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id Wbb4ef729 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_Wbb4ef729_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/Wbb4ef729.parquet` (15786 events: 7903 long, 7883 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `swing_pct_5`, module `trig_levels_vwap` (code/th_grid/trig_levels_vwap.py -> triggers_d/lv_vwap.py), variant `break`, params {"n": 2, "k": 0.25}, bracket `sym15u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/swing_pct_5/trig_levels_vwap.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1861, L6M 2715, L3M 3708; t 4.9 over 1618 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 143..185 (2025-12-28 to 2026-10-24) = 43 held week(s); months in the cell file: 202512, 202601, 202602, 202603, 202604, 202605, 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored -199.73 / mine -199.73 pts, 10 / 10 trades; w182 2026-09-27 stored 34.52 / mine 34.52 pts, 10 / 10 trades; w183 2026-10-04 stored 356.06 / mine 356.06 pts, 9 / 9 trades; w184 2026-10-11 stored 231.14 / mine 231.14 pts, 9 / 9 trades; w185 2026-10-18 stored 67.32 / mine 67.32 pts, 11 / 11 trades (last 5 of 43 held weeks shown; 43 of 43 equal)

**1. BAR**
**BAR** row `swing_pct_5` = SWING leg bar (kernel k_dchg, see dchg rule). [SPEC] build_month.py line 130: theta = max(2, round(5 x px / 10000)) ticks where px is the price in TICKS of the CURRENT print (recomputed per print: 5 basis points of price; about 58 ticks = 14.5 pt near 29000). Leg bars exactly as `dchg` (bar o = st, c = extreme, known at the confirming print). Theta range on the sample days: 20261023: theta_ticks_min=58, theta_ticks_max=59; 20261016: theta_ticks_min=59, theta_ticks_max=60; 20261009: theta_ticks_min=62, theta_ticks_max=62. [SPEC] Price-only. [SPEC] swing_pct_8 is already specified in D8_BAR_DEFS.md section 3.10.
- [SPEC] Bars per NYAM session in the loaded months: median 149 (min 6, max 871, 353 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/swing_pct_5/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 245 stored / 245 rebuilt / 245 identical (o,h,l,c,known_ts,part); td 20261016: 189 stored / 189 rebuilt / 189 identical (o,h,l,c,known_ts,part); td 20261009: 102 stored / 102 rebuilt / 102 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec exists, class by parameter**: swing_pct_8 specified (D8_BAR_DEFS 3.10); SwingBuilder(theta) takes a fixed theta, here theta changes per print with price (READING: per-print theta needed).

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_vwap` (th_grid/triggers_d/lv_vwap.py; lines fd_levels.py lines 55-72 and 82-91). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 8 VWAP lines in this list order: VWAP0__V, RVWAP0__V, LVWAP0__V, YVWAP__V, AVPDH__V, AVPDL__V, WVWAP__V, MVWAP__V. Every VWAP = cumulative sum(typ x minute volume) / cumulative sum(volume) with typ = (h+l+c)/3 of the 1-minute bar, value at minute i uses minutes < i of the anchor period (shift by one minute, NaN on the anchor's first minute).
- VWAP0: anchored at the first minute of each label day (18:00 ET); valid when tord >= 30 and cumulative volume > 2000. RVWAP0: anchored 09:30 ET, valid 09:45-16:00 ET (tord 945..1319) and cum volume > 2000. LVWAP0: anchored 02:00 ET, valid 02:15-16:00 ET (tord 495..1319) and cum volume > 1000.
- YVWAP: the prior label day's RTH (09:30-16:00 ET) VWAP, constant for the whole next label day. AVPDH / AVPDL: VWAP anchored at the minute of the prior RTH day's high / low (the minute with the extreme h / l inside RTH), running over the whole next label day (value at i uses minutes a..i-1). WVWAP: anchored at the first minute of each ISO week (of the label date), valid when cumulative volume > 20000. MVWAP: anchored at the first minute of each calendar month, valid when cumulative volume > 20000.
- Back-adjusted then converted to raw (see store).
Variant `break` (n=2, k=0.25): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: n=2, k=0.25 -> k*u = 1.250 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 353 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): VWAP0 1.00, RVWAP0 0.79, LVWAP0 1.00, YVWAP 1.00, AVPDH 1.00, AVPDL 1.00, WVWAP 1.00, MVWAP 1.00.
- [READING] Module status: **lines spec only; no VWAP code in D8Asia.cs**: break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits).

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `sym15u` = unit rule sym15u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule sym15u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ trades only (1-minute bars from the tape, with contract-roll back-adjustment).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: Needs the previous RTH day (YVWAP, AVPDH/L), the current ISO week and month (WVWAP/MVWAP; early in a week/month the volume gate delays validity). READING: starting a live chart cold needs the prior RTH day of 1-minute data plus the week-to-date and month-to-date minutes; the store itself runs from 2023-04-02.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 2 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng (swing_pct: the print price only).

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 769; share whose signal bar is bar 0 of the session: 0.07; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 5, 50, 133, 759.
- [SPEC] Held weeks only: 524 grid trades; share on bar 0: 0.05; signal-bar index quantiles: 0, 9, 66, 153.25, 676.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: RVWAP0 127, LVWAP0 103, VWAP0 94, YVWAP 51, AVPDH 47, AVPDL 43, MVWAP 32, WVWAP 27.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/Wbb4ef729_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 245, first known 2026-10-23T13:30:02.140Z, last known 2026-10-23T15:59:01.851Z; rebuilt-from-tape check 245/245/245; threshold values: theta_ticks_min=58, theta_ticks_max=59
SIGNALS (raw events of the session: 20 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
59,2026-10-23T13:43:25.532Z,-1,VWAP0__V,29115.02,29108.75,5.00,Y
66,2026-10-23T13:45:07.080Z,1,LVWAP0__V,29105.05,29108.50,5.00,no
78,2026-10-23T13:49:34.100Z,1,LVWAP0__V,29105.92,29107.50,5.00,no
84,2026-10-23T13:51:58.277Z,1,LVWAP0__V,29106.18,29113.50,5.00,no
86,2026-10-23T13:52:16.906Z,1,VWAP0__V,29115.21,29122.50,5.00,no
94,2026-10-23T13:56:09.041Z,1,LVWAP0__V,29107.49,29115.50,5.00,no
96,2026-10-23T13:56:54.582Z,1,VWAP0__V,29115.72,29119.50,5.00,no
100,2026-10-23T13:59:12.590Z,1,VWAP0__V,29115.91,29146.00,5.00,no
109,2026-10-23T14:05:05.996Z,-1,AVPDH__V,29193.54,29175.75,5.00,no
139,2026-10-23T14:18:07.623Z,-1,VWAP0__V,29121.28,29113.75,5.00,no
144,2026-10-23T14:21:01.292Z,1,RVWAP0__V,29102.83,29120.50,5.00,no
146,2026-10-23T14:21:50.487Z,1,VWAP0__V,29120.95,29132.75,5.00,no
153,2026-10-23T14:28:38.902Z,-1,VWAP0__V,29121.38,29116.25,5.00,no
156,2026-10-23T14:30:41.111Z,1,VWAP0__V,29121.19,29134.00,5.00,no
159,2026-10-23T14:33:19.992Z,-1,AVPDH__V,29190.23,29172.25,5.00,no
170,2026-10-23T14:41:18.542Z,1,AVPDH__V,29190.21,29240.50,5.00,Y
199,2026-10-23T15:05:44.128Z,-1,YVWAP__V,29283.77,29270.00,5.00,no
205,2026-10-23T15:11:08.735Z,-1,YVWAP__V,29283.77,29245.00,5.00,no
229,2026-10-23T15:30:23.998Z,-1,YVWAP__V,29283.77,29266.00,5.00,no
235,2026-10-23T15:41:15.782Z,-1,YVWAP__V,29283.77,29268.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
59,-1,2026-10-23T13:43:26.605Z,29094.75,0.1776,29094.71,2026-10-23T14:38:49.095Z,29215.00,Stop,120.0,120.0,-120.29,-2410.73
170,1,2026-10-23T14:41:19.591Z,29254.75,0.1776,29254.79,2026-10-23T15:59:59.487Z,29293.50,SessionEnd,120.0,120.0,38.71,769.27
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 16 of 245 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
53,2026-10-23T13:41:00.279Z,29035.50,29067.75,29035.50,29067.75,5.00,2026-10-23T13:40:35Z,2026-10-23T13:40:00Z,,LVWAP0=29106.59,
54,2026-10-23T13:41:01.689Z,29067.75,29067.75,29050.75,29050.75,5.00,2026-10-23T13:41:00Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
55,2026-10-23T13:41:21.993Z,29050.75,29069.50,29050.75,29069.50,5.00,2026-10-23T13:41:01Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
56,2026-10-23T13:41:33.050Z,29069.50,29069.50,29044.75,29044.75,5.00,2026-10-23T13:41:21Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
57,2026-10-23T13:42:39.825Z,29044.75,29121.75,29044.75,29121.75,5.00,2026-10-23T13:41:33Z,2026-10-23T13:41:00Z,AVPDL=29120.32,AVPDH=29198.41,
58,2026-10-23T13:43:08.973Z,29121.75,29121.75,29090.50,29090.50,5.00,2026-10-23T13:42:39Z,2026-10-23T13:42:00Z,,LVWAP0=29104.89,
59,2026-10-23T13:43:25.532Z,29090.50,29108.75,29090.50,29108.75,5.00,2026-10-23T13:43:08Z,2026-10-23T13:43:00Z,LVWAP0=29104.78,VWAP0=29115.02,-1 VWAP0
60,2026-10-23T13:43:34.177Z,29108.75,29108.75,29092.75,29092.75,5.00,2026-10-23T13:43:25Z,2026-10-23T13:43:00Z,,LVWAP0=29104.78,
...
164,2026-10-23T14:35:29.196Z,29162.50,29162.50,29144.75,29144.75,5.00,2026-10-23T14:35:16Z,2026-10-23T14:35:00Z,AVPDL=29124.72,AVPDH=29190.07,
165,2026-10-23T14:36:02.476Z,29144.75,29169.75,29144.75,29169.75,5.00,2026-10-23T14:35:29Z,2026-10-23T14:35:00Z,AVPDL=29124.72,AVPDH=29190.07,
166,2026-10-23T14:36:13.235Z,29169.75,29169.75,29141.75,29141.75,5.00,2026-10-23T14:36:02Z,2026-10-23T14:36:00Z,AVPDL=29124.84,AVPDH=29190.02,
167,2026-10-23T14:37:12.606Z,29141.75,29192.00,29141.75,29192.00,5.00,2026-10-23T14:36:13Z,2026-10-23T14:36:00Z,AVPDH=29190.02,YVWAP=29283.77,
168,2026-10-23T14:37:32.927Z,29192.00,29192.00,29160.00,29160.00,5.00,2026-10-23T14:37:12Z,2026-10-23T14:37:00Z,AVPDL=29125.01,AVPDH=29189.99,
169,2026-10-23T14:41:04.787Z,29160.00,29255.00,29160.00,29255.00,5.00,2026-10-23T14:37:32Z,2026-10-23T14:37:00Z,AVPDH=29189.99,YVWAP=29283.77,
170,2026-10-23T14:41:18.542Z,29255.00,29255.00,29240.50,29240.50,5.00,2026-10-23T14:41:04Z,2026-10-23T14:41:00Z,AVPDH=29190.21,YVWAP=29283.77,+1 AVPDH
171,2026-10-23T14:42:12.646Z,29240.50,29260.00,29240.50,29260.00,5.00,2026-10-23T14:41:18Z,2026-10-23T14:41:00Z,AVPDH=29190.21,YVWAP=29283.77,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=59 2026-10-23T13:43:25.532Z side -1 fired VWAP0: VWAP0=29115.02; LVWAP0=29104.78; YVWAP=29283.77; AVPDH=29197.54; AVPDL=29119.68; WVWAP=29621.16; MVWAP=30398.08
k=170 2026-10-23T14:41:18.542Z side +1 fired AVPDH: VWAP0=29124.79; RVWAP0=29115.32; LVWAP0=29121.86; YVWAP=29283.77; AVPDH=29190.21; AVPDL=29126.62; WVWAP=29602.08; MVWAP=30382.85
```

#### td 20261016 (sess_id 202610163, NYAM session, grid week 184)
- bars of the session: 189, first known 2026-10-16T13:30:04.875Z, last known 2026-10-16T15:56:54.279Z; rebuilt-from-tape check 189/189/189; threshold values: theta_ticks_min=59, theta_ticks_max=60
SIGNALS (raw events of the session: 11 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
11,2026-10-16T13:32:44.926Z,1,AVPDL__V,30000.40,30006.25,5.00,Y
18,2026-10-16T13:34:19.259Z,-1,AVPDL__V,30000.46,29996.00,5.00,no
30,2026-10-16T13:38:47.094Z,-1,YVWAP__V,29921.82,29904.25,5.00,Y
45,2026-10-16T13:45:10.143Z,1,YVWAP__V,29921.82,29923.25,5.00,no
46,2026-10-16T13:45:11.919Z,-1,RVWAP0__V,29943.45,29938.75,5.00,no
49,2026-10-16T13:45:46.006Z,1,YVWAP__V,29921.82,29926.00,5.00,no
54,2026-10-16T13:47:45.123Z,-1,RVWAP0__V,29942.43,29927.50,5.00,no
56,2026-10-16T13:50:00.523Z,-1,YVWAP__V,29921.82,29903.75,5.00,no
129,2026-10-16T14:37:54.517Z,1,RVWAP0__V,29883.79,29886.00,5.00,no
133,2026-10-16T14:46:01.453Z,1,RVWAP0__V,29885.31,29906.75,5.00,no
138,2026-10-16T14:55:35.401Z,-1,RVWAP0__V,29886.62,29856.75,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
11,1,2026-10-16T13:32:45.931Z,30017.50,0.1776,30017.54,2026-10-16T13:37:57.265Z,29897.25,Stop,120.0,120.0,-120.29,-2410.73
30,-1,2026-10-16T13:38:48.113Z,29888.50,0.1776,29888.46,2026-10-16T15:05:39.281Z,29768.46,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 16 of 189 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
5,2026-10-16T13:31:08.138Z,30016.50,30016.50,29984.50,29984.50,5.00,2026-10-16T13:31:02Z,2026-10-16T13:31:00Z,YVWAP=29921.82,AVPDL=30000.47,
6,2026-10-16T13:31:16.857Z,29984.50,30002.00,29984.50,30002.00,5.00,2026-10-16T13:31:08Z,2026-10-16T13:31:00Z,AVPDL=30000.47,VWAP0=30096.46,
7,2026-10-16T13:31:38.396Z,30002.00,30002.00,29962.50,29962.50,5.00,2026-10-16T13:31:16Z,2026-10-16T13:31:00Z,YVWAP=29921.82,AVPDL=30000.47,
8,2026-10-16T13:32:18.814Z,29962.50,30013.00,29962.50,30013.00,5.00,2026-10-16T13:31:38Z,2026-10-16T13:31:00Z,AVPDL=30000.47,VWAP0=30096.46,
9,2026-10-16T13:32:23.240Z,30013.00,30013.00,29997.25,29997.25,5.00,2026-10-16T13:32:18Z,2026-10-16T13:32:00Z,YVWAP=29921.82,AVPDL=30000.40,
10,2026-10-16T13:32:40.688Z,29997.25,30024.75,29997.25,30024.75,5.00,2026-10-16T13:32:23Z,2026-10-16T13:32:00Z,AVPDL=30000.40,VWAP0=30093.21,
11,2026-10-16T13:32:44.926Z,30024.75,30024.75,30006.25,30006.25,5.00,2026-10-16T13:32:40Z,2026-10-16T13:32:00Z,AVPDL=30000.40,VWAP0=30093.21,+1 AVPDL
12,2026-10-16T13:32:51.399Z,30006.25,30023.75,30006.25,30023.75,5.00,2026-10-16T13:32:44Z,2026-10-16T13:32:00Z,AVPDL=30000.40,VWAP0=30093.21,
...
24,2026-10-16T13:37:14.887Z,29914.50,29948.00,29914.50,29948.00,5.00,2026-10-16T13:36:10Z,2026-10-16T13:36:00Z,YVWAP=29921.82,AVPDL=29999.92,
25,2026-10-16T13:37:22.026Z,29948.00,29948.00,29919.00,29919.00,5.00,2026-10-16T13:37:14Z,2026-10-16T13:37:00Z,,YVWAP=29921.82,
26,2026-10-16T13:37:31.376Z,29919.00,29936.75,29919.00,29936.75,5.00,2026-10-16T13:37:22Z,2026-10-16T13:37:00Z,YVWAP=29921.82,AVPDL=29999.49,
27,2026-10-16T13:37:43.147Z,29936.75,29936.75,29905.50,29905.50,5.00,2026-10-16T13:37:31Z,2026-10-16T13:37:00Z,,YVWAP=29921.82,
28,2026-10-16T13:37:55.246Z,29905.50,29922.00,29905.50,29922.00,5.00,2026-10-16T13:37:43Z,2026-10-16T13:37:00Z,YVWAP=29921.82,AVPDL=29999.49,
29,2026-10-16T13:38:09.933Z,29922.00,29922.00,29877.00,29877.00,5.00,2026-10-16T13:37:55Z,2026-10-16T13:37:00Z,,YVWAP=29921.82,
30,2026-10-16T13:38:47.094Z,29877.00,29904.25,29877.00,29904.25,5.00,2026-10-16T13:38:09Z,2026-10-16T13:38:00Z,,YVWAP=29921.82,-1 YVWAP
31,2026-10-16T13:39:06.328Z,29904.25,29904.25,29872.00,29872.00,5.00,2026-10-16T13:38:47Z,2026-10-16T13:38:00Z,,YVWAP=29921.82,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=11 2026-10-16T13:32:44.926Z side +1 fired AVPDL: VWAP0=30093.21; LVWAP0=30095.97; YVWAP=29921.82; AVPDH=30102.86; AVPDL=30000.40; WVWAP=30405.35; MVWAP=30830.69
k=30 2026-10-16T13:38:47.094Z side -1 fired YVWAP: VWAP0=30075.37; LVWAP0=30067.30; YVWAP=29921.82; AVPDH=30087.34; AVPDL=29998.90; WVWAP=30401.35; MVWAP=30827.53
```

#### td 20261009 (sess_id 202610093, NYAM session, grid week 183)
- bars of the session: 102, first known 2026-10-09T13:30:28.015Z, last known 2026-10-09T15:59:03.894Z; rebuilt-from-tape check 102/102/102; threshold values: theta_ticks_min=62, theta_ticks_max=62
SIGNALS (raw events of the session: 18 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
1,2026-10-09T13:30:52.735Z,-1,LVWAP0__V,31204.39,31151.75,5.00,Y
3,2026-10-09T13:31:56.533Z,-1,VWAP0__V,31141.12,31135.75,5.00,no
9,2026-10-09T13:38:09.086Z,-1,VWAP0__V,31139.76,31103.75,5.00,no
12,2026-10-09T13:39:42.695Z,1,YVWAP__V,31084.65,31094.50,5.00,no
15,2026-10-09T13:41:44.473Z,-1,MVWAP__V,31120.92,31108.25,5.00,no
16,2026-10-09T13:41:53.882Z,1,YVWAP__V,31084.65,31091.00,5.00,no
21,2026-10-09T13:44:27.210Z,-1,YVWAP__V,31084.65,31069.00,5.00,no
31,2026-10-09T13:49:43.046Z,-1,AVPDL__V,31033.42,31031.50,5.00,Y
35,2026-10-09T13:51:05.456Z,-1,AVPDL__V,31033.26,31023.00,5.00,no
39,2026-10-09T13:56:47.307Z,-1,AVPDL__V,31032.98,31031.00,5.00,no
62,2026-10-09T14:21:23.807Z,1,AVPDL__V,31032.67,31034.50,5.00,no
66,2026-10-09T14:27:10.878Z,1,AVPDL__V,31032.76,31038.75,5.00,no
77,2026-10-09T14:47:03.453Z,-1,RVWAP0__V,31063.13,31061.75,5.00,no
80,2026-10-09T14:56:54.348Z,1,RVWAP0__V,31062.49,31074.50,5.00,no
87,2026-10-09T15:14:46.838Z,-1,RVWAP0__V,31063.30,31053.75,5.00,no
90,2026-10-09T15:21:49.671Z,1,AVPDL__V,31035.82,31054.75,5.00,no
97,2026-10-09T15:33:35.243Z,-1,RVWAP0__V,31062.42,31049.25,5.00,no
100,2026-10-09T15:48:39.354Z,1,AVPDL__V,31036.44,31051.50,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
1,-1,2026-10-09T13:30:53.758Z,31134.75,0.1776,31134.71,2026-10-09T13:46:30.896Z,31014.71,Target,120.0,120.0,120.00,2395.16
31,-1,2026-10-09T13:49:44.087Z,31011.75,0.1776,31011.71,2026-10-09T15:59:59.766Z,31063.50,SessionEnd,120.0,120.0,-51.79,-1040.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 11 of 102 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-09T13:30:28.015Z,31168.50,31168.50,31126.25,31126.25,5.00,2026-10-09T13:20:32Z,2026-10-09T13:20:00Z,MVWAP=31120.82,VWAP0=31139.26,
1,2026-10-09T13:30:52.735Z,31126.25,31151.75,31126.25,31151.75,5.00,2026-10-09T13:30:28Z,2026-10-09T13:30:00Z,VWAP0=31140.95,LVWAP0=31204.39,-1 LVWAP0
2,2026-10-09T13:31:26.014Z,31151.75,31151.75,31115.25,31115.25,5.00,2026-10-09T13:30:52Z,2026-10-09T13:30:00Z,YVWAP=31084.65,MVWAP=31120.91,
...
25,2026-10-09T13:45:03.337Z,31021.50,31038.75,31021.50,31038.75,5.00,2026-10-09T13:45:00Z,2026-10-09T13:45:00Z,AVPDL=31033.62,AVPDH=31071.76,
26,2026-10-09T13:45:08.278Z,31038.75,31038.75,31018.50,31018.50,5.00,2026-10-09T13:45:03Z,2026-10-09T13:45:00Z,,AVPDL=31033.62,
27,2026-10-09T13:45:34.705Z,31018.50,31047.75,31018.50,31047.75,5.00,2026-10-09T13:45:08Z,2026-10-09T13:45:00Z,AVPDL=31033.62,AVPDH=31071.76,
28,2026-10-09T13:47:16.631Z,31047.75,31047.75,31006.00,31006.00,5.00,2026-10-09T13:45:34Z,2026-10-09T13:45:00Z,,AVPDL=31033.62,
29,2026-10-09T13:48:11.537Z,31006.00,31037.25,31006.00,31037.25,5.00,2026-10-09T13:47:16Z,2026-10-09T13:47:00Z,AVPDL=31033.46,AVPDH=31071.32,
30,2026-10-09T13:48:48.459Z,31037.25,31037.25,30997.25,30997.25,5.00,2026-10-09T13:48:11Z,2026-10-09T13:48:00Z,,AVPDL=31033.42,
31,2026-10-09T13:49:43.046Z,30997.25,31031.50,30997.25,31031.50,5.00,2026-10-09T13:48:48Z,2026-10-09T13:48:00Z,,AVPDL=31033.42,-1 AVPDL
32,2026-10-09T13:50:00.468Z,31031.50,31031.50,31010.50,31010.50,5.00,2026-10-09T13:49:43Z,2026-10-09T13:49:00Z,,AVPDL=31033.31,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=1 2026-10-09T13:30:52.735Z side -1 fired LVWAP0: VWAP0=31140.95; LVWAP0=31204.39; YVWAP=31084.65; AVPDH=31068.43; AVPDL=31021.50; WVWAP=31261.91; MVWAP=31120.91
k=31 2026-10-09T13:49:43.046Z side -1 fired AVPDL: VWAP0=31128.41; RVWAP0=31098.68; LVWAP0=31160.22; YVWAP=31084.65; AVPDH=31071.17; AVPDL=31033.42; WVWAP=31257.82; MVWAP=31120.56
```

## D. EXISTING VERSUS NEW, AND A ROUGH LIST OF WHAT WOULD HAVE TO BE CODED (READING; effort words are my judgement, not an estimate in hours)
**D1. Shared infrastructure for any of these books** (nothing here is specific to one book): (1) a continuous per-row bar series over ALL six session codes with the engine's reset rule at every session boundary and contract roll; (2) the daily scale table (stats_day: trailing-20-row medians of daily volume / prints / range, r0 constants; D8_BAR_DEFS section 2) built nightly, hole handling decided (stored vs hole-filled, as in the NY AM pages); (3) a 1-minute NQ series with roll back-adjustment and the label-day / ISO-week / month bookkeeping (D8Asia.cs already keeps a 1-minute series, READING); (4) the T0 level lookup (previous bar's whole-second close, minute index, 120 s staleness) and the line-at-minute-i convention (uses minutes < i); (5) the generic level_events logic for the variants used (below) with plain u = 5.0 pt or native u (rolling-100 median range shifted one bar, min 20, floor 0.5 pt) - D8Asia.cs has LevelBreakNative (break_native, n = 2) only; (6) session filter, part == 0, one position, flat at the session end, and the book's bracket (fixed points or the unit rule clip(m x u, 10, 120)).

**D2. Bar builders needed on this page:**
- `pnf`: spec only - pnf_7 specified in D8_BUILD_SPEC (L9c2622b0, Asia; stored Asia bars rebuilt identical in D8_ASIA_NEWBOOK_INPUTS.md) and pnf_14 in D8_NYAM_SPEC_L43f0cbfb; NO class for it in D8Asia.cs (class list read): box is a parameter, so pnf_5 / pnf_10 are parameter changes of a builder that is specified but not yet in the strategy file. Effort: medium (new class; kernel is 25 lines of Python).
- `swing_atr`: exists - swing_atr_0.25 specified (D8_BAR_DEFS 3.10, L488784d8); SwingBuilder in D8Asia.cs. Effort: small (class exists).
- `swing_pct`: spec exists, class by parameter - swing_pct_8 specified (D8_BAR_DEFS 3.10); SwingBuilder(theta) takes a fixed theta, here theta changes per print with price (READING: per-print theta needed). Effort: small-medium (theta recomputed per print from the price).
- `urenko`: new (one parameter from frenko) - no urenko spec or class found; k_renko with R = B; FlexRenkoBuilder has R = B/2 (READING: a reversal-distance parameter). Effort: small (reversal distance parameter of the frenko class).

**D3. Level modules needed on this page:**
- `fibr_dev`: NEW - no spec. Effort: medium (18 lines on a developing, per-minute session range with the 8-pt gate).
- `piv_floor`: lines exist in D8Asia.cs; trigger by parameter - pivot lines (Piv()) and LevelBreakNative (break_native n=2, k) exist for L6b373671; plain break n=1, k=0 and the 16-line set incl. weekly and CPR need checking against pivLines. Effort: small (lines exist in D8Asia.cs; check list incl. weekly and CPR).
- `piv_wf`: NEW - Woodie and Fibonacci pivots are not in any spec page. Effort: small (Woodie + Fibonacci pivots, formulas above).
- `prior_day`: NEW - no spec page names prior_day; PD_C / PD_RTH are used inside D8Asia.cs for pivots and value area (line 1447 prints PD_C, VAL) but there is no prior-day level-trigger class. Effort: small (5 constants per label day).
- `vwap`: lines spec only; no VWAP code in D8Asia.cs - break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits). Effort: medium (8 anchored VWAP series on the 1-minute series: day / RTH / London / prior-day / two anchored at the prior RTH extreme minutes / week / month, each with its validity gate).

**D4. Trigger variants needed:** `break`, `break_native`, `false_break`, `reject`, `retest` (definitions in each book's section 2; the 4 base events break / reject / retest / false_break are all in fd_common.level_events, about 35 lines of Python).

**D5. Per book: what has to be coded on top of D1 (READING)**
- Wbcfa80fb (false_break M=1/k=0.0): bar `swing_atr_0.25` [exists]; module `prior_day` [NEW].
- Wc7c3f9c5 (break_native n=2/k=0.0): bar `pnf_7` [spec only]; module `vwap` [lines spec only; no VWAP code in D8Asia.cs].
- We3999e99 (reject tol=0.5/conf=body): bar `pnf_7` [spec only]; module `fibr_dev` [NEW].
- W9fd5ca5d (reject tol=1.0/conf=body): bar `pnf_10` [spec only]; module `piv_floor` [lines exist in D8Asia.cs; trigger by parameter].
- W5ba295af (retest M=3/tol=0.5): bar `urenko_40` [new (one parameter from frenko)]; module `piv_wf` [NEW].
- Wbb4ef729 (break n=2/k=0.25): bar `swing_pct_5` [spec exists, class by parameter]; module `vwap` [lines spec only; no VWAP code in D8Asia.cs].

**D6. Match test plan (READING):** run the live builder on the same tape for the three dated sessions of each book and compare (a) the bar closes and known times, (b) the line value of each line at T0 (CSV file), (c) the signal bars and fired lines (SIGNALS block), (d) order time = floor(known) + 2 s for the live engine versus signal known time + 1 s for the grid, (e) the exit reason and, within the stated slippage, the trade prices.

## E. OPEN POINTS FOR LEAD (READING unless marked)
- Print granularity for `tsf` (and any activity bar): the grid used the old per-record tape; D8 uses run-merged prints. A tsf book needs a LEAD decision before coding (build the old record semantics, or re-run the books on a run-merge `tsf`).
- Line files are the engine's stored files (written 2026-11-17, data to 2026-11-13). The trade tape has no files for 2026-10-31..11-04 (D8_BAR_DEFS), which touches profile / pivot / volume lines built over those days (see D8_NYAM_SPEC_Le4fede95 / B7bfd33b7 for the PRF5 hole); every dated session on this page is before 2026-10-25, so none is affected.
- Shared inputs inside the register [SPEC]: `dchg_N` and `kagi_N` rows are the SAME bars (same kernel, same thresholds), so a dchg book and a kagi book with the same module/variant/params/bracket produce the same signals (the Test 8 table lists such pairs, e.g. Wb1ab799c vs W050c781f, W10e7f4cd vs Wca8c5296); books on the same bar row share the bars but not the signals. A coder needs one builder for both.
- The 'level at T0' rule and the fact that Asia bar 0 / NY AM bar 0 take their lines and memory from the previous session are engine behaviours an NT8 coder would not guess; they are the main source of mismatch risk.
