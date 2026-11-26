# SPEC_STACK_N5: coding spec pages for the six NY AM books of forward-register stack N5 (both-sides LEVEL books; every statement marked SPEC or READING)

Written 2026-11-26 23:39Z by W-SPEC9 (sub-agent of LEAD, not typed by Josh). Order: autopilot/DIRECTIVE_TEST9_2313Z.md part B (relay design under Josh's standing 18:22Z order). RESEARCH / SHADOW ONLY: nothing built, nothing coded, no gate or code change, nothing queued, nothing live, no spend, nothing deleted; the execution server, the live D8Asia.cs and every chart are untouched (D8Asia.cs was only read for its class list). Layout copied from the hand-verified pages D8_NYAM_SPEC_*.md / D8_BUILD_SPEC.md per-book blocks (sections 0 identity, 1 BAR, 2 TRIGGER, 3 signal to order, 4 sides and bracket, 5 other inputs, 6 one position / window / warm-up, 7 what trades, 8 parity data) with a stack overview, an existing-versus-new table and a coding list added.

Marks: **SPEC** = read from code or measured by re-running the engine code in this session; **READING** = my inference (stated as such). Where a source could not be found it says so; nothing is guessed. Book ids and parameters are those of FORWARD_REGISTER_STACKS.md (W-TEST8 section, seed 20261128); the stack is N5 only as a REGISTER object (equal weight, 1 lot per book, bare R0, no stack rules).

## STATUS LINE (read first)
- VERIFIED [SPEC]: for all 6 books the module source was found (th_grid/trig_levels_<name>.py -> triggers_d/lv_<name>.py, line construction in fd_levels.py / fd_levels2.py / fd_profile.py), the bar kernel source was found (th_bars/kernels.py via build_month.py), and the stored grid weekly table of the cell was reproduced exactly by re-running signal_fn and the gcore2x simulator for every held week (6 of 6 books with all held weeks equal). The 3 dated sessions per book were rebuilt from the stored trade tape with the engine bar kernel (all bars identical to the stored bars) and the signals, entries and exits in section 8 are those reproduced trades.
- NOT VERIFIED / OPEN: (a) the live-engine fill (book walk) is not re-run (the table uses the grid engine); (b) line values come from the engine's stored line files (files written 2026-11-17 19:55-23:08Z by fd_levels.py / fd_levels2.py / fd_profile.py from nq1m.npz, data to 2026-11-13; they were NOT re-derived from the tape here except that the 3.7 / L43f0cbfb / Le4fede95 pages already verify vwap, fib15, fibr_on, profile_nodes and piv_floor lines for other dates); (c) no D8 print-rule version exists for the activity bar `tsf` (see flags).
- NOTE Wf74d00e3 is also in stack N3 of the register (the A4-A5 / N4-N5 draw only avoided reuse inside its own draw); it is described again here so that this page stands alone.
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
| W3b484778 | NYAM | urenko_20 | prior_day false_break M=2,k=0.5 | fixed120/60 | 182-185 | 1219, 4.1, 1370 | yes | new (one parameter from frenko) | NEW | - |
| Wb1ab799c | NYAM | dchg_28 | vwap break n=3,k=0.25 | asym15u/30u | 182-185 | 1675, 4.5, 1624 | yes | spec exists, class by parameter | lines spec only; no VWAP code in D8Asia.cs | - |
| Wf74d00e3 | NYAM | dchg_20 | prior_day false_break M=3,k=0.5 | fixed120/120 | 169-185 | 1385, 4.5, 1043 | yes | spec exists, class by parameter | NEW | also in stack N3 |
| W3e503490 | NYAM | pnf_5 | prior_day false_break_native M=1,k=0.5 | sym8u | 182-185 | 1222, 4.1, 1677 | yes | spec only | NEW | - |
| W10e7f4cd | NYAM | dchg_14 | prior_day false_break_native M=3,k=0.5 | sym8u | 182-185 | 1272, 4.1, 1412 | yes | spec exists, class by parameter | NEW | - |
| Wd5038cce | NYAM | kagi_28 | prior_day false_break M=3,k=0.5 | sym15u | 169-185 | 1313, 4.5, 1050 | yes | same bars as dchg | NEW | - |

Status words: 'exists' = specified on a page AND a class in D8Asia.cs; 'spec only' = specified on a page, no class; 'new' = no page, no class. D8Asia.cs was read only for its class list (READING; its content is not part of this order).

## C. THE BOOKS (one block each; sections 0 to 8)


### BOOK W3b484778 (NYAM): urenko_20 + prior day level false break (M 2, k 0.5), BOTH sides, bracket fixed120/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W3b484778 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_W3b484778_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W3b484778.parquet` (11543 events: 5762 long, 5781 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `urenko_20`, module `trig_levels_prior_day` (code/th_grid/trig_levels_prior_day.py -> triggers_d/lv_prior_day.py), variant `false_break`, params {"M": 2, "k": 0.5}, bracket `fixed120/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/urenko_20/trig_levels_prior_day.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1219, L6M 2151, L3M 2359; t 4.1 over 1370 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored -212.89 / mine -212.89 pts, 10 / 10 trades; w183 2026-10-04 stored 81.97 / mine 81.97 pts, 2 / 2 trades; w184 2026-10-11 stored 179.49 / mine 179.49 pts, 4 / 4 trades; w185 2026-10-18 stored -129.86 / mine -129.86 pts, 9 / 9 trades

**1. BAR**
**BAR** row `urenko_20` = UniRenko (reversal = one full brick) RENKO. [SPEC] kernel k_renko (kernels.py lines 59-95), build_month.py lines 108-113: brick B = max(2, round(20 x s_rng)) ticks, reversal distance R = B, open offset O = 0, no wicks. State per session key: first print sets bo = bc = p, d = 0. d = 0: p >= bo + B -> up brick [bo, bo+B]; p <= bo - B -> down brick. d = +1: p >= bc + B -> continuation brick [bc, bc + B]; p <= bc - R -> reversal brick opening at bc - O = bc and closing at bc - R (height R, direction flips). Mirror for d = -1. A loop re-tests the same print, so one print can emit several bricks (same timestamp; volume to the first). Brick OHLC = (open, max, min, close) with no wicks; known time = timestamp of the completing print; no bar for an unfinished brick at the session end. Brick on the sample days: 20261023: brick_ticks=44, brick_pts=11.00, reversal_ticks=44; 20261014: brick_ticks=44, brick_pts=11.00, reversal_ticks=44; 20261007: brick_ticks=46, brick_pts=11.50, reversal_ticks=46. [SPEC] Price-only (D8_BUILD_SPEC line 13). [READING] urenko = the same kernel with R = B: a one-line change of FlexRenkoBuilder (reversal distance B instead of B/2).
- [SPEC] Bars per NYAM session in the loaded months: median 266 (min 15, max 1120, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/urenko_20/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 438 stored / 438 rebuilt / 438 identical (o,h,l,c,known_ts,part); td 20261014: 344 stored / 344 rebuilt / 344 identical (o,h,l,c,known_ts,part); td 20261007: 157 stored / 157 rebuilt / 157 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **new (one parameter from frenko)**: no urenko spec or class found; k_renko with R = B; FlexRenkoBuilder has R = B/2 (READING: a reversal-distance parameter).

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_prior_day` (th_grid/triggers_d/lv_prior_day.py; lines fd_levels.py lines 27-34). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 5 lines in this list order: PD_RTH__H, PD_RTH__L, PD_FULL__H, PD_FULL__L, PD_C__C.
- PD_RTH__H / __L = high / low of the PRIOR label day's RTH minutes (tord 930..1319 = 09:30-16:00 ET). PD_FULL__H / __L = high / low of ALL minutes of the prior label day (18:00 ET to 18:00 ET). PD_C__C = close of the prior label day's minute tord = 1319 (the 15:59 ET minute). Each is constant for the whole next label day (18:00 ET to 18:00 ET), so it is available from the very first Asia bar. 'prior label day' = the previous label day present in the store (weekends/holidays are skipped).
- Back-adjusted then converted to raw.
Variant `false_break` (M=2, k=0.5): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: M=2, k=0.5 -> k*u = 2.500 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PD_RTH_H 0.99, PD_RTH_L 0.99, PD_FULL_H 1.00, PD_FULL_L 1.00, PD_C_C 0.97.
- [READING] Module status: **NEW**: no spec page names prior_day; PD_C / PD_RTH are used inside D8Asia.cs for pivots and value area (line 1447 prints PD_C, VAL) but there is no prior-day level-trigger class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `fixed120/60` = stop 120 pts / target 60 pts, fixed (no unit rule); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 120 pts / target 60 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: One prior label day of 1-minute data. READING: with the NQ 1-minute series of the previous RTH day and previous 18:00-18:00 day the lines can be computed with no further history.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 2 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 316; share whose signal bar is bar 0 of the session: 0.04; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 39, 117, 201.75, 773.
- [SPEC] Held weeks only: 25 grid trades; share on bar 0: 0.00; signal-bar index quantiles: 2, 31, 128, 177, 325.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: PD_RTH_L 9, PD_C_C 7, PD_RTH_H 5, PD_FULL_H 2, PD_FULL_L 2.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W3b484778_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 438, first known 2026-10-23T13:30:00.128Z, last known 2026-10-23T15:59:41.843Z; rebuilt-from-tape check 438/438/438; threshold values: brick_ticks=44, brick_pts=11.000, reversal_ticks=44
SIGNALS (raw events of the session: 30 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
12,2026-10-23T13:30:37.946Z,1,PD_RTH__L,29033.00,29040.25,5.00,Y
39,2026-10-23T13:34:05.756Z,-1,PD_RTH__L,29033.00,29029.25,5.00,Y
42,2026-10-23T13:34:21.533Z,1,PD_RTH__L,29033.00,29040.25,5.00,no
45,2026-10-23T13:35:06.663Z,-1,PD_RTH__L,29033.00,29029.25,5.00,no
50,2026-10-23T13:35:29.187Z,1,PD_RTH__L,29033.00,29040.25,5.00,no
51,2026-10-23T13:35:36.572Z,-1,PD_RTH__L,29033.00,29029.25,5.00,no
62,2026-10-23T13:36:32.498Z,1,PD_RTH__L,29033.00,29040.25,5.00,no
63,2026-10-23T13:36:42.221Z,-1,PD_RTH__L,29033.00,29029.25,5.00,no
78,2026-10-23T13:39:13.126Z,1,PD_RTH__L,29033.00,29040.25,5.00,no
81,2026-10-23T13:40:04.430Z,-1,PD_RTH__L,29033.00,29029.25,5.00,no
82,2026-10-23T13:40:08.087Z,1,PD_RTH__L,29033.00,29040.25,5.00,no
146,2026-10-23T13:52:24.953Z,1,PD_C__C,29145.00,29150.25,5.00,Y
147,2026-10-23T13:52:36.945Z,-1,PD_C__C,29145.00,29139.25,5.00,no
150,2026-10-23T13:53:24.165Z,1,PD_C__C,29145.00,29150.25,5.00,no
151,2026-10-23T13:53:28.882Z,-1,PD_C__C,29145.00,29139.25,5.00,no
172,2026-10-23T13:58:12.783Z,1,PD_C__C,29145.00,29150.25,5.00,no
181,2026-10-23T14:00:34.101Z,-1,PD_C__C,29145.00,29139.25,5.00,no
184,2026-10-23T14:00:54.963Z,1,PD_C__C,29145.00,29150.25,5.00,no
185,2026-10-23T14:00:58.283Z,-1,PD_C__C,29145.00,29139.25,5.00,no
186,2026-10-23T14:01:04.478Z,1,PD_C__C,29145.00,29150.25,5.00,no
201,2026-10-23T14:06:18.193Z,-1,PD_C__C,29145.00,29139.25,5.00,no
202,2026-10-23T14:06:39.093Z,1,PD_C__C,29145.00,29150.25,5.00,no
237,2026-10-23T14:16:17.072Z,-1,PD_C__C,29145.00,29139.25,5.00,no
252,2026-10-23T14:21:13.041Z,1,PD_C__C,29145.00,29150.25,5.00,no
257,2026-10-23T14:21:27.280Z,-1,PD_C__C,29145.00,29139.25,5.00,no
258,2026-10-23T14:21:51.673Z,1,PD_C__C,29145.00,29150.25,5.00,no
263,2026-10-23T14:23:48.306Z,-1,PD_C__C,29145.00,29139.25,5.00,no
278,2026-10-23T14:30:06.409Z,1,PD_C__C,29145.00,29150.25,5.00,no
279,2026-10-23T14:30:27.684Z,-1,PD_C__C,29145.00,29139.25,5.00,no
280,2026-10-23T14:30:42.391Z,1,PD_C__C,29145.00,29150.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
12,1,2026-10-23T13:30:38.962Z,29041.75,0.1776,29041.79,2026-10-23T13:32:35.061Z,29101.79,Target,120.0,60.0,60.00,1195.16
39,-1,2026-10-23T13:34:06.772Z,29030.25,0.1776,29030.21,2026-10-23T13:52:24.953Z,29150.50,Stop,120.0,60.0,-120.29,-2410.73
146,1,2026-10-23T13:52:25.954Z,29145.75,0.1776,29145.79,2026-10-23T14:38:39.363Z,29205.79,Target,120.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 24 of 438 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
6,2026-10-23T13:30:16.861Z,29007.25,29018.25,29007.25,29018.25,5.00,2026-10-23T13:30:08Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
7,2026-10-23T13:30:20.464Z,29018.25,29029.25,29018.25,29029.25,5.00,2026-10-23T13:30:16Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
8,2026-10-23T13:30:22.503Z,29029.25,29029.25,29018.25,29018.25,5.00,2026-10-23T13:30:20Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
9,2026-10-23T13:30:34.661Z,29018.25,29018.25,29007.25,29007.25,5.00,2026-10-23T13:30:22Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
10,2026-10-23T13:30:37.404Z,29007.25,29018.25,29007.25,29018.25,5.00,2026-10-23T13:30:34Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
11,2026-10-23T13:30:37.474Z,29018.25,29029.25,29018.25,29029.25,5.00,2026-10-23T13:30:37Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
12,2026-10-23T13:30:37.946Z,29029.25,29040.25,29029.25,29040.25,5.00,2026-10-23T13:30:37Z,2026-10-23T13:30:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,+1 PD_RTH_L
13,2026-10-23T13:30:46.304Z,29040.25,29051.25,29040.25,29051.25,5.00,2026-10-23T13:30:37Z,2026-10-23T13:30:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
...
33,2026-10-23T13:32:55.543Z,29084.25,29084.25,29073.25,29073.25,5.00,2026-10-23T13:32:47Z,2026-10-23T13:32:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
34,2026-10-23T13:33:04.899Z,29073.25,29073.25,29062.25,29062.25,5.00,2026-10-23T13:32:55Z,2026-10-23T13:32:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
35,2026-10-23T13:33:14.678Z,29062.25,29062.25,29051.25,29051.25,5.00,2026-10-23T13:33:04Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
36,2026-10-23T13:33:36.452Z,29051.25,29051.25,29040.25,29040.25,5.00,2026-10-23T13:33:14Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
37,2026-10-23T13:33:42.832Z,29040.25,29051.25,29040.25,29051.25,5.00,2026-10-23T13:33:36Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
38,2026-10-23T13:33:44.958Z,29051.25,29051.25,29040.25,29040.25,5.00,2026-10-23T13:33:42Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
39,2026-10-23T13:34:05.756Z,29040.25,29040.25,29029.25,29029.25,5.00,2026-10-23T13:33:44Z,2026-10-23T13:33:00Z,,PD_RTH_L=29033.00,-1 PD_RTH_L
40,2026-10-23T13:34:13.669Z,29029.25,29029.25,29018.25,29018.25,5.00,2026-10-23T13:34:05Z,2026-10-23T13:34:00Z,,PD_RTH_L=29033.00,
...
140,2026-10-23T13:51:18.089Z,29117.25,29117.25,29106.25,29106.25,5.00,2026-10-23T13:51:10Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
141,2026-10-23T13:51:23.329Z,29106.25,29117.25,29106.25,29117.25,5.00,2026-10-23T13:51:18Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
142,2026-10-23T13:51:41.453Z,29117.25,29128.25,29117.25,29128.25,5.00,2026-10-23T13:51:23Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
143,2026-10-23T13:51:49.962Z,29128.25,29128.25,29117.25,29117.25,5.00,2026-10-23T13:51:41Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
144,2026-10-23T13:51:58.292Z,29117.25,29128.25,29117.25,29128.25,5.00,2026-10-23T13:51:49Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
145,2026-10-23T13:52:19.828Z,29128.25,29139.25,29128.25,29139.25,5.00,2026-10-23T13:51:58Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
146,2026-10-23T13:52:24.953Z,29139.25,29150.25,29139.25,29150.25,5.00,2026-10-23T13:52:19Z,2026-10-23T13:52:00Z,PD_C_C=29145.00,PD_RTH_H=29594.75,+1 PD_C_C
147,2026-10-23T13:52:36.945Z,29150.25,29150.25,29139.25,29139.25,5.00,2026-10-23T13:52:24Z,2026-10-23T13:52:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,-1 PD_C_C
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=12 2026-10-23T13:30:37.946Z side +1 fired PD_RTH_L: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
k=39 2026-10-23T13:34:05.756Z side -1 fired PD_RTH_L: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
k=146 2026-10-23T13:52:24.953Z side +1 fired PD_C_C: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
```

#### td 20261014 (sess_id 202610143, NYAM session, grid week 184)
- bars of the session: 344, first known 2026-10-14T13:30:00.826Z, last known 2026-10-14T15:59:56.649Z; rebuilt-from-tape check 344/344/344; threshold values: brick_ticks=44, brick_pts=11.000, reversal_ticks=44
SIGNALS (raw events of the session: 12 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
43,2026-10-14T13:33:55.637Z,1,PD_RTH__L,30591.25,30595.50,5.00,Y
44,2026-10-14T13:34:02.492Z,-1,PD_RTH__L,30591.25,30584.50,5.00,no
85,2026-10-14T13:40:32.112Z,1,PD_RTH__L,30591.25,30595.50,5.00,no
96,2026-10-14T13:44:04.144Z,-1,PD_RTH__L,30591.25,30584.50,5.00,no
99,2026-10-14T13:45:01.599Z,1,PD_RTH__L,30591.25,30595.50,5.00,no
100,2026-10-14T13:45:08.286Z,-1,PD_RTH__L,30591.25,30584.50,5.00,no
101,2026-10-14T13:45:32.065Z,1,PD_RTH__L,30591.25,30595.50,5.00,no
102,2026-10-14T13:45:43.053Z,-1,PD_RTH__L,30591.25,30584.50,5.00,no
103,2026-10-14T13:46:03.474Z,1,PD_RTH__L,30591.25,30595.50,5.00,no
108,2026-10-14T13:46:48.201Z,-1,PD_RTH__L,30591.25,30584.50,5.00,no
109,2026-10-14T13:46:59.357Z,1,PD_RTH__L,30591.25,30595.50,5.00,no
128,2026-10-14T13:52:13.779Z,-1,PD_RTH__L,30591.25,30584.50,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
43,1,2026-10-14T13:33:56.722Z,30594.75,0.1776,30594.79,2026-10-14T13:48:08.179Z,30654.79,Target,120.0,60.0,60.00,1195.16
128,-1,2026-10-14T13:52:14.841Z,30586.00,0.1776,30585.96,2026-10-14T13:56:10.226Z,30525.96,Target,120.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 16 of 344 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
37,2026-10-14T13:33:07.938Z,30540.50,30551.50,30540.50,30551.50,5.00,2026-10-14T13:32:59Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
38,2026-10-14T13:33:11.139Z,30551.50,30562.50,30551.50,30562.50,5.00,2026-10-14T13:33:07Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
39,2026-10-14T13:33:24.514Z,30562.50,30573.50,30562.50,30573.50,5.00,2026-10-14T13:33:11Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
40,2026-10-14T13:33:26.978Z,30573.50,30584.50,30573.50,30584.50,5.00,2026-10-14T13:33:24Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
41,2026-10-14T13:33:29.038Z,30584.50,30584.50,30573.50,30573.50,5.00,2026-10-14T13:33:26Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
42,2026-10-14T13:33:32.221Z,30573.50,30584.50,30573.50,30584.50,5.00,2026-10-14T13:33:29Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
43,2026-10-14T13:33:55.637Z,30584.50,30595.50,30584.50,30595.50,5.00,2026-10-14T13:33:32Z,2026-10-14T13:33:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,+1 PD_RTH_L
44,2026-10-14T13:34:02.492Z,30595.50,30595.50,30584.50,30584.50,5.00,2026-10-14T13:33:55Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,-1 PD_RTH_L
...
122,2026-10-14T13:50:18.786Z,30639.50,30639.50,30628.50,30628.50,5.00,2026-10-14T13:50:05Z,2026-10-14T13:50:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,
123,2026-10-14T13:50:39.233Z,30628.50,30628.50,30617.50,30617.50,5.00,2026-10-14T13:50:18Z,2026-10-14T13:50:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,
124,2026-10-14T13:50:51.497Z,30617.50,30628.50,30617.50,30628.50,5.00,2026-10-14T13:50:39Z,2026-10-14T13:50:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,
125,2026-10-14T13:51:19.738Z,30628.50,30628.50,30617.50,30617.50,5.00,2026-10-14T13:50:51Z,2026-10-14T13:50:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,
126,2026-10-14T13:51:29.617Z,30617.50,30617.50,30606.50,30606.50,5.00,2026-10-14T13:51:19Z,2026-10-14T13:51:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,
127,2026-10-14T13:52:08.235Z,30606.50,30606.50,30595.50,30595.50,5.00,2026-10-14T13:51:29Z,2026-10-14T13:51:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,
128,2026-10-14T13:52:13.779Z,30595.50,30595.50,30584.50,30584.50,5.00,2026-10-14T13:52:08Z,2026-10-14T13:52:00Z,,PD_RTH_L=30591.25,-1 PD_RTH_L
129,2026-10-14T13:52:20.421Z,30584.50,30584.50,30573.50,30573.50,5.00,2026-10-14T13:52:13Z,2026-10-14T13:52:00Z,,PD_RTH_L=30591.25,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=43 2026-10-14T13:33:55.637Z side +1 fired PD_RTH_L: PD_RTH_H=30814.75; PD_RTH_L=30591.25; PD_FULL_H=30906.00; PD_FULL_L=30591.25; PD_C_C=30788.75
k=128 2026-10-14T13:52:13.779Z side -1 fired PD_RTH_L: PD_RTH_H=30814.75; PD_RTH_L=30591.25; PD_FULL_H=30906.00; PD_FULL_L=30591.25; PD_C_C=30788.75
```

#### td 20261007 (sess_id 202610073, NYAM session, grid week 183)
- bars of the session: 157, first known 2026-10-07T13:30:02.219Z, last known 2026-10-07T15:58:25.482Z; rebuilt-from-tape check 157/157/157; threshold values: brick_ticks=46, brick_pts=11.500, reversal_ticks=46
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
148,2026-10-07T15:35:56.747Z,1,PD_FULL__L,31309.25,31314.25,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
148,1,2026-10-07T15:35:57.748Z,31315.75,0.1776,31315.79,2026-10-07T15:59:59.207Z,31338.25,SessionEnd,120.0,60.0,22.46,444.27
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 157 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
142,2026-10-07T15:22:08.368Z,31279.75,31279.75,31268.25,31268.25,5.00,2026-10-07T15:21:34Z,2026-10-07T15:21:00Z,,PD_FULL_L=31309.25,
143,2026-10-07T15:22:51.334Z,31268.25,31279.75,31268.25,31279.75,5.00,2026-10-07T15:22:08Z,2026-10-07T15:22:00Z,,PD_FULL_L=31309.25,
144,2026-10-07T15:24:14.590Z,31279.75,31279.75,31268.25,31268.25,5.00,2026-10-07T15:22:51Z,2026-10-07T15:22:00Z,,PD_FULL_L=31309.25,
145,2026-10-07T15:26:37.862Z,31268.25,31279.75,31268.25,31279.75,5.00,2026-10-07T15:24:14Z,2026-10-07T15:24:00Z,,PD_FULL_L=31309.25,
146,2026-10-07T15:32:16.050Z,31279.75,31291.25,31279.75,31291.25,5.00,2026-10-07T15:26:37Z,2026-10-07T15:26:00Z,,PD_FULL_L=31309.25,
147,2026-10-07T15:35:08.270Z,31291.25,31302.75,31291.25,31302.75,5.00,2026-10-07T15:32:16Z,2026-10-07T15:32:00Z,,PD_FULL_L=31309.25,
148,2026-10-07T15:35:56.747Z,31302.75,31314.25,31302.75,31314.25,5.00,2026-10-07T15:35:08Z,2026-10-07T15:35:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,+1 PD_FULL_L
149,2026-10-07T15:37:04.468Z,31314.25,31325.75,31314.25,31325.75,5.00,2026-10-07T15:35:56Z,2026-10-07T15:35:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=148 2026-10-07T15:35:56.747Z side +1 fired PD_FULL_L: PD_RTH_H=31616.50; PD_RTH_L=31457.75; PD_FULL_H=31616.50; PD_FULL_L=31309.25; PD_C_C=31480.75
```

### BOOK Wb1ab799c (NYAM): dchg_28 + vwap level break (n 3, k 0.25), BOTH sides, bracket asym15u/30u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id Wb1ab799c (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_Wb1ab799c_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/Wb1ab799c.parquet` (14129 events: 7070 long, 7059 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `dchg_28`, module `trig_levels_vwap` (code/th_grid/trig_levels_vwap.py -> triggers_d/lv_vwap.py), variant `break`, params {"n": 3, "k": 0.25}, bracket `asym15u/30u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/dchg_28/trig_levels_vwap.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1675, L6M 1243, L3M 3072; t 4.5 over 1624 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored 291.15 / mine 291.15 pts, 10 / 10 trades; w183 2026-10-04 stored 221.36 / mine 221.36 pts, 9 / 9 trades; w184 2026-10-11 stored 181.43 / mine 181.43 pts, 10 / 10 trades; w185 2026-10-18 stored 282.43 / mine 282.43 pts, 10 / 10 trades

**1. BAR**
**BAR** row `dchg_28` = DIRECTIONAL-CHANGE leg bar. [SPEC] kernel k_dchg (kernels.py lines 197-225; build_month.py lines 125-128: `kagi_N` is built with EXACTLY the same kernel and thresholds as `dchg_N`, so the two rows are the same bars): reversal size theta = max(2, round(28 x s_rng)) ticks. Directional-change legs: a bar = a leg between two confirmed extremes. State per session key: d = 0 tracks the running high ehi and low elo from the first print; the first leg is decided when price is theta above the running low (up leg starts from that low, st = elo) or theta below the running high. d = +1: ext = running high (te = its time); when ext - p >= theta the leg is CONFIRMED: bar o = st, h = ext, l = st, c = ext, known time = timestamp of the confirming print (the close of the bar is the EXTREME, not the confirming price), then st = ext, d = -1, ext = p. d = -1 mirror (bar o = st, h = st, l = ext, c = ext). The unfinished last leg is never a bar. Theta on the sample days: 20261023: theta_ticks=61, theta_pts=15.25; 20261016: theta_ticks=61, theta_pts=15.25; 20261009: theta_ticks=64, theta_pts=16.00. [SPEC] Price-only (D8_BUILD_SPEC line 13). [READING] The live SwingBuilder class (D8Asia.cs) implements this kernel with a theta in ticks; kagi/dchg rows differ from it only in how theta is chosen (s_rng x N instead of the ATR rule).
- [SPEC] Bars per NYAM session in the loaded months: median 136 (min 9, max 545, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/dchg_28/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 233 stored / 233 rebuilt / 233 identical (o,h,l,c,known_ts,part); td 20261016: 179 stored / 179 rebuilt / 179 identical (o,h,l,c,known_ts,part); td 20261009: 98 stored / 98 rebuilt / 98 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec exists, class by parameter**: dchg_40 specified (D8_BUILD_SPEC L8cfda948); SwingBuilder(theta) in D8Asia.cs is the same kernel; theta rule here = max(2, round(N x s_rng)) not the ATR rule.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_vwap` (th_grid/triggers_d/lv_vwap.py; lines fd_levels.py lines 55-72 and 82-91). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 8 VWAP lines in this list order: VWAP0__V, RVWAP0__V, LVWAP0__V, YVWAP__V, AVPDH__V, AVPDL__V, WVWAP__V, MVWAP__V. Every VWAP = cumulative sum(typ x minute volume) / cumulative sum(volume) with typ = (h+l+c)/3 of the 1-minute bar, value at minute i uses minutes < i of the anchor period (shift by one minute, NaN on the anchor's first minute).
- VWAP0: anchored at the first minute of each label day (18:00 ET); valid when tord >= 30 and cumulative volume > 2000. RVWAP0: anchored 09:30 ET, valid 09:45-16:00 ET (tord 945..1319) and cum volume > 2000. LVWAP0: anchored 02:00 ET, valid 02:15-16:00 ET (tord 495..1319) and cum volume > 1000.
- YVWAP: the prior label day's RTH (09:30-16:00 ET) VWAP, constant for the whole next label day. AVPDH / AVPDL: VWAP anchored at the minute of the prior RTH day's high / low (the minute with the extreme h / l inside RTH), running over the whole next label day (value at i uses minutes a..i-1). WVWAP: anchored at the first minute of each ISO week (of the label date), valid when cumulative volume > 20000. MVWAP: anchored at the first minute of each calendar month, valid when cumulative volume > 20000.
- Back-adjusted then converted to raw (see store).
Variant `break` (n=3, k=0.25): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: n=3, k=0.25 -> k*u = 1.250 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): VWAP0 1.00, RVWAP0 0.78, LVWAP0 1.00, YVWAP 1.00, AVPDH 0.99, AVPDL 0.99, WVWAP 1.00, MVWAP 1.00.
- [READING] Module status: **lines spec only; no VWAP code in D8Asia.cs**: break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits).

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `asym15u/30u` = unit rule asym15u/30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule asym15u/30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ trades only (1-minute bars from the tape, with contract-roll back-adjustment).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: Needs the previous RTH day (YVWAP, AVPDH/L), the current ISO week and month (WVWAP/MVWAP; early in a week/month the volume gate delays validity). READING: starting a live chart cold needs the prior RTH day of 1-minute data plus the week-to-date and month-to-date minutes; the store itself runs from 2023-04-02.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 3 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 431; share whose signal bar is bar 0 of the session: 0.03; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 9.5, 46, 98, 442.
- [SPEC] Held weeks only: 39 grid trades; share on bar 0: 0.00; signal-bar index quantiles: 1, 10.5, 45, 84.5, 206.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: VWAP0 10, RVWAP0 10, LVWAP0 9, YVWAP 5, AVPDL 2, AVPDH 2, WVWAP 1.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/Wb1ab799c_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 233, first known 2026-10-23T13:30:02.530Z, last known 2026-10-23T15:59:05.197Z; rebuilt-from-tape check 233/233/233; threshold values: theta_ticks=61, theta_pts=15.250
SIGNALS (raw events of the session: 19 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
56,2026-10-23T13:43:34.178Z,-1,VWAP0__V,29115.02,29092.75,5.00,Y
73,2026-10-23T13:50:03.428Z,1,LVWAP0__V,29105.92,29137.00,5.00,no
79,2026-10-23T13:52:36.717Z,1,LVWAP0__V,29106.18,29156.25,5.00,no
81,2026-10-23T13:53:29.707Z,1,VWAP0__V,29115.21,29152.25,5.00,no
87,2026-10-23T13:56:41.929Z,1,LVWAP0__V,29107.49,29141.50,5.00,no
89,2026-10-23T13:57:20.905Z,1,VWAP0__V,29115.72,29140.25,5.00,no
93,2026-10-23T14:00:29.167Z,1,VWAP0__V,29116.23,29189.50,5.00,no
102,2026-10-23T14:05:52.890Z,-1,AVPDH__V,29193.50,29145.25,5.00,no
132,2026-10-23T14:19:01.822Z,-1,VWAP0__V,29121.17,29081.75,5.00,no
137,2026-10-23T14:21:14.814Z,1,RVWAP0__V,29103.23,29172.25,5.00,no
139,2026-10-23T14:22:41.787Z,1,VWAP0__V,29120.95,29165.75,5.00,no
146,2026-10-23T14:28:59.438Z,-1,VWAP0__V,29121.20,29090.00,5.00,no
149,2026-10-23T14:31:59.205Z,1,VWAP0__V,29121.19,29202.50,5.00,no
152,2026-10-23T14:33:43.903Z,-1,AVPDH__V,29190.19,29150.25,5.00,no
163,2026-10-23T14:43:21.724Z,1,AVPDH__V,29190.31,29254.25,5.00,Y
190,2026-10-23T15:06:28.384Z,-1,YVWAP__V,29283.77,29250.00,5.00,no
196,2026-10-23T15:11:28.224Z,-1,YVWAP__V,29283.77,29229.25,5.00,no
220,2026-10-23T15:30:37.583Z,-1,YVWAP__V,29283.77,29248.25,5.00,no
224,2026-10-23T15:44:48.016Z,-1,YVWAP__V,29283.77,29216.00,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
56,-1,2026-10-23T13:43:35.179Z,29113.00,0.1208,29112.97,2026-10-23T14:40:11.058Z,29233.25,Stop,120.0,120.0,-120.28,-2410.44
163,1,2026-10-23T14:43:22.806Z,29237.50,0.1208,29237.53,2026-10-23T15:59:59.487Z,29293.50,SessionEnd,120.0,120.0,55.97,1114.56
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 16 of 233 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
50,2026-10-23T13:41:01.692Z,29067.75,29067.75,29050.75,29050.75,5.00,2026-10-23T13:41:00Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
51,2026-10-23T13:41:22.216Z,29050.75,29069.50,29050.75,29069.50,5.00,2026-10-23T13:41:01Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
52,2026-10-23T13:41:33.059Z,29069.50,29069.50,29044.75,29044.75,5.00,2026-10-23T13:41:22Z,2026-10-23T13:41:00Z,,LVWAP0=29105.46,
53,2026-10-23T13:42:39.825Z,29044.75,29121.75,29044.75,29121.75,5.00,2026-10-23T13:41:33Z,2026-10-23T13:41:00Z,AVPDL=29120.32,AVPDH=29198.41,
54,2026-10-23T13:43:09.079Z,29121.75,29121.75,29090.50,29090.50,5.00,2026-10-23T13:42:39Z,2026-10-23T13:42:00Z,,LVWAP0=29104.89,
55,2026-10-23T13:43:25.533Z,29090.50,29108.75,29090.50,29108.75,5.00,2026-10-23T13:43:09Z,2026-10-23T13:43:00Z,LVWAP0=29104.78,VWAP0=29115.02,
56,2026-10-23T13:43:34.178Z,29108.75,29108.75,29092.75,29092.75,5.00,2026-10-23T13:43:25Z,2026-10-23T13:43:00Z,,LVWAP0=29104.78,-1 VWAP0
57,2026-10-23T13:43:41.217Z,29092.75,29113.50,29092.75,29113.50,5.00,2026-10-23T13:43:34Z,2026-10-23T13:43:00Z,LVWAP0=29104.78,VWAP0=29115.02,
...
157,2026-10-23T14:36:02.496Z,29144.75,29169.75,29144.75,29169.75,5.00,2026-10-23T14:35:31Z,2026-10-23T14:35:00Z,AVPDL=29124.72,AVPDH=29190.07,
158,2026-10-23T14:36:27.408Z,29169.75,29169.75,29141.75,29141.75,5.00,2026-10-23T14:36:02Z,2026-10-23T14:36:00Z,AVPDL=29124.84,AVPDH=29190.02,
159,2026-10-23T14:37:12.828Z,29141.75,29192.00,29141.75,29192.00,5.00,2026-10-23T14:36:27Z,2026-10-23T14:36:00Z,AVPDH=29190.02,YVWAP=29283.77,
160,2026-10-23T14:37:33.169Z,29192.00,29192.00,29160.00,29160.00,5.00,2026-10-23T14:37:12Z,2026-10-23T14:37:00Z,AVPDL=29125.01,AVPDH=29189.99,
161,2026-10-23T14:42:13.375Z,29160.00,29260.00,29160.00,29260.00,5.00,2026-10-23T14:37:33Z,2026-10-23T14:37:00Z,AVPDH=29189.99,YVWAP=29283.77,
162,2026-10-23T14:42:47.919Z,29260.00,29260.00,29238.75,29238.75,5.00,2026-10-23T14:42:13Z,2026-10-23T14:42:00Z,AVPDH=29190.31,YVWAP=29283.77,
163,2026-10-23T14:43:21.724Z,29238.75,29254.25,29238.75,29254.25,5.00,2026-10-23T14:42:47Z,2026-10-23T14:42:00Z,AVPDH=29190.31,YVWAP=29283.77,+1 AVPDH
164,2026-10-23T14:43:40.384Z,29254.25,29254.25,29234.00,29234.00,5.00,2026-10-23T14:43:21Z,2026-10-23T14:43:00Z,AVPDH=29190.42,YVWAP=29283.77,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=56 2026-10-23T13:43:34.178Z side -1 fired VWAP0: VWAP0=29115.02; LVWAP0=29104.78; YVWAP=29283.77; AVPDH=29197.54; AVPDL=29119.68; WVWAP=29621.16; MVWAP=30398.08
k=163 2026-10-23T14:43:21.724Z side +1 fired AVPDH: VWAP0=29125.25; RVWAP0=29116.38; LVWAP0=29122.48; YVWAP=29283.77; AVPDH=29190.31; AVPDL=29127.01; WVWAP=29601.93; MVWAP=30382.69
```

#### td 20261016 (sess_id 202610163, NYAM session, grid week 184)
- bars of the session: 179, first known 2026-10-16T13:30:04.920Z, last known 2026-10-16T15:56:54.309Z; rebuilt-from-tape check 179/179/179; threshold values: theta_ticks=61, theta_pts=15.250
SIGNALS (raw events of the session: 11 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
12,2026-10-16T13:32:51.414Z,1,AVPDL__V,30000.40,30023.75,5.00,Y
19,2026-10-16T13:34:24.484Z,-1,AVPDL__V,30000.46,29973.75,5.00,no
31,2026-10-16T13:39:06.328Z,-1,YVWAP__V,29921.82,29872.00,5.00,Y
44,2026-10-16T13:45:11.953Z,1,YVWAP__V,29921.82,29938.75,5.00,no
45,2026-10-16T13:45:21.545Z,-1,RVWAP0__V,29943.45,29921.00,5.00,no
48,2026-10-16T13:45:59.632Z,1,YVWAP__V,29921.82,29946.00,5.00,no
53,2026-10-16T13:49:10.792Z,-1,RVWAP0__V,29942.43,29868.00,5.00,no
55,2026-10-16T13:50:07.123Z,-1,YVWAP__V,29921.82,29886.00,5.00,no
128,2026-10-16T14:40:38.761Z,1,RVWAP0__V,29883.79,29934.00,5.00,no
132,2026-10-16T14:48:30.204Z,1,RVWAP0__V,29885.49,29947.00,5.00,no
137,2026-10-16T14:56:08.746Z,-1,RVWAP0__V,29886.62,29841.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
12,1,2026-10-16T13:32:52.464Z,30002.75,0.1208,30002.78,2026-10-16T13:38:07.018Z,29882.25,Stop,120.0,120.0,-120.53,-2415.44
31,-1,2026-10-16T13:39:07.338Z,29892.00,0.1208,29891.97,2026-10-16T15:05:35.517Z,29771.97,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 16 of 179 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
6,2026-10-16T13:31:16.857Z,29984.50,30002.00,29984.50,30002.00,5.00,2026-10-16T13:31:08Z,2026-10-16T13:31:00Z,AVPDL=30000.47,VWAP0=30096.46,
7,2026-10-16T13:31:38.396Z,30002.00,30002.00,29962.50,29962.50,5.00,2026-10-16T13:31:16Z,2026-10-16T13:31:00Z,YVWAP=29921.82,AVPDL=30000.47,
8,2026-10-16T13:32:18.814Z,29962.50,30013.00,29962.50,30013.00,5.00,2026-10-16T13:31:38Z,2026-10-16T13:31:00Z,AVPDL=30000.47,VWAP0=30096.46,
9,2026-10-16T13:32:23.240Z,30013.00,30013.00,29997.25,29997.25,5.00,2026-10-16T13:32:18Z,2026-10-16T13:32:00Z,YVWAP=29921.82,AVPDL=30000.40,
10,2026-10-16T13:32:40.688Z,29997.25,30024.75,29997.25,30024.75,5.00,2026-10-16T13:32:23Z,2026-10-16T13:32:00Z,AVPDL=30000.40,VWAP0=30093.21,
11,2026-10-16T13:32:45.063Z,30024.75,30024.75,30006.25,30006.25,5.00,2026-10-16T13:32:40Z,2026-10-16T13:32:00Z,AVPDL=30000.40,VWAP0=30093.21,
12,2026-10-16T13:32:51.414Z,30006.25,30023.75,30006.25,30023.75,5.00,2026-10-16T13:32:45Z,2026-10-16T13:32:00Z,AVPDL=30000.40,VWAP0=30093.21,+1 AVPDL
13,2026-10-16T13:33:22.202Z,30023.75,30023.75,30000.00,30000.00,5.00,2026-10-16T13:32:51Z,2026-10-16T13:32:00Z,YVWAP=29921.82,AVPDL=30000.40,
...
25,2026-10-16T13:37:22.026Z,29948.00,29948.00,29919.00,29919.00,5.00,2026-10-16T13:37:14Z,2026-10-16T13:37:00Z,,YVWAP=29921.82,
26,2026-10-16T13:37:31.472Z,29919.00,29936.75,29919.00,29936.75,5.00,2026-10-16T13:37:22Z,2026-10-16T13:37:00Z,YVWAP=29921.82,AVPDL=29999.49,
27,2026-10-16T13:37:43.256Z,29936.75,29936.75,29905.50,29905.50,5.00,2026-10-16T13:37:31Z,2026-10-16T13:37:00Z,,YVWAP=29921.82,
28,2026-10-16T13:37:55.246Z,29905.50,29922.00,29905.50,29922.00,5.00,2026-10-16T13:37:43Z,2026-10-16T13:37:00Z,YVWAP=29921.82,AVPDL=29999.49,
29,2026-10-16T13:38:10.209Z,29922.00,29922.00,29877.00,29877.00,5.00,2026-10-16T13:37:55Z,2026-10-16T13:37:00Z,,YVWAP=29921.82,
30,2026-10-16T13:38:47.118Z,29877.00,29904.25,29877.00,29904.25,5.00,2026-10-16T13:38:10Z,2026-10-16T13:38:00Z,,YVWAP=29921.82,
31,2026-10-16T13:39:06.328Z,29904.25,29904.25,29872.00,29872.00,5.00,2026-10-16T13:38:47Z,2026-10-16T13:38:00Z,,YVWAP=29921.82,-1 YVWAP
32,2026-10-16T13:39:52.801Z,29872.00,29911.50,29872.00,29911.50,5.00,2026-10-16T13:39:06Z,2026-10-16T13:39:00Z,,YVWAP=29921.82,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=12 2026-10-16T13:32:51.414Z side +1 fired AVPDL: VWAP0=30093.21; LVWAP0=30095.97; YVWAP=29921.82; AVPDH=30102.86; AVPDL=30000.40; WVWAP=30405.35; MVWAP=30830.69
k=31 2026-10-16T13:39:06.328Z side -1 fired YVWAP: VWAP0=30075.37; LVWAP0=30067.30; YVWAP=29921.82; AVPDH=30087.34; AVPDL=29998.90; WVWAP=30401.35; MVWAP=30827.53
```

#### td 20261009 (sess_id 202610093, NYAM session, grid week 183)
- bars of the session: 98, first known 2026-10-09T13:30:28.015Z, last known 2026-10-09T15:59:24.828Z; rebuilt-from-tape check 98/98/98; threshold values: theta_ticks=64, theta_pts=16.000
SIGNALS (raw events of the session: 18 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
2,2026-10-09T13:31:26.016Z,-1,LVWAP0__V,31204.39,31115.25,5.00,Y
4,2026-10-09T13:32:01.928Z,-1,VWAP0__V,31141.12,31117.25,5.00,no
10,2026-10-09T13:38:16.289Z,-1,VWAP0__V,31138.72,31069.00,5.00,no
13,2026-10-09T13:40:13.369Z,1,YVWAP__V,31084.65,31128.50,5.00,no
16,2026-10-09T13:41:53.885Z,-1,MVWAP__V,31120.92,31091.00,5.00,no
17,2026-10-09T13:42:23.847Z,1,YVWAP__V,31084.65,31109.00,5.00,no
22,2026-10-09T13:44:38.746Z,-1,YVWAP__V,31084.65,31031.00,5.00,no
32,2026-10-09T13:50:00.471Z,-1,AVPDL__V,31033.31,31010.50,5.00,Y
36,2026-10-09T13:52:09.855Z,-1,AVPDL__V,31033.20,31000.50,5.00,no
40,2026-10-09T13:57:13.970Z,-1,AVPDL__V,31032.89,31014.75,5.00,no
61,2026-10-09T14:21:58.587Z,1,AVPDL__V,31032.69,31054.75,5.00,no
65,2026-10-09T14:32:11.575Z,1,AVPDL__V,31032.91,31078.00,5.00,no
74,2026-10-09T14:48:58.899Z,-1,AVPDH__V,31067.29,31026.00,5.00,no
77,2026-10-09T14:59:41.243Z,1,RVWAP0__V,31062.49,31095.25,5.00,no
84,2026-10-09T15:16:50.652Z,-1,RVWAP0__V,31062.64,31036.50,5.00,no
87,2026-10-09T15:23:07.720Z,1,AVPDL__V,31035.87,31071.75,5.00,no
94,2026-10-09T15:35:15.961Z,-1,RVWAP0__V,31062.16,31024.00,5.00,no
97,2026-10-09T15:59:24.828Z,1,AVPDL__V,31036.56,31093.50,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
2,-1,2026-10-09T13:31:27.068Z,31126.00,0.1208,31125.97,2026-10-09T13:48:34.083Z,31005.97,Target,120.0,120.0,120.00,2395.16
32,-1,2026-10-09T13:50:01.494Z,31028.50,0.1208,31028.47,2026-10-09T15:59:59.766Z,31063.50,SessionEnd,120.0,120.0,-35.03,-705.44
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 12 of 98 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-09T13:30:28.015Z,31168.50,31168.50,31126.25,31126.25,5.00,2026-10-09T13:20:32Z,2026-10-09T13:20:00Z,MVWAP=31120.82,VWAP0=31139.26,
1,2026-10-09T13:30:53.229Z,31126.25,31151.75,31126.25,31151.75,5.00,2026-10-09T13:30:28Z,2026-10-09T13:30:00Z,VWAP0=31140.95,LVWAP0=31204.39,
2,2026-10-09T13:31:26.016Z,31151.75,31151.75,31115.25,31115.25,5.00,2026-10-09T13:30:53Z,2026-10-09T13:30:00Z,YVWAP=31084.65,MVWAP=31120.91,-1 LVWAP0
3,2026-10-09T13:31:57.580Z,31115.25,31135.75,31115.25,31135.75,5.00,2026-10-09T13:31:26Z,2026-10-09T13:31:00Z,MVWAP=31120.95,VWAP0=31141.12,
...
26,2026-10-09T13:45:08.278Z,31038.75,31038.75,31018.50,31018.50,5.00,2026-10-09T13:45:04Z,2026-10-09T13:45:00Z,,AVPDL=31033.62,
27,2026-10-09T13:45:34.705Z,31018.50,31047.75,31018.50,31047.75,5.00,2026-10-09T13:45:08Z,2026-10-09T13:45:00Z,AVPDL=31033.62,AVPDH=31071.76,
28,2026-10-09T13:47:20.627Z,31047.75,31047.75,31006.00,31006.00,5.00,2026-10-09T13:45:34Z,2026-10-09T13:45:00Z,,AVPDL=31033.62,
29,2026-10-09T13:48:11.547Z,31006.00,31037.25,31006.00,31037.25,5.00,2026-10-09T13:47:20Z,2026-10-09T13:47:00Z,AVPDL=31033.46,AVPDH=31071.32,
30,2026-10-09T13:48:48.460Z,31037.25,31037.25,30997.25,30997.25,5.00,2026-10-09T13:48:11Z,2026-10-09T13:48:00Z,,AVPDL=31033.42,
31,2026-10-09T13:49:43.056Z,30997.25,31031.50,30997.25,31031.50,5.00,2026-10-09T13:48:48Z,2026-10-09T13:48:00Z,,AVPDL=31033.42,
32,2026-10-09T13:50:00.471Z,31031.50,31031.50,31010.50,31010.50,5.00,2026-10-09T13:49:43Z,2026-10-09T13:49:00Z,,AVPDL=31033.31,-1 AVPDL
33,2026-10-09T13:50:26.682Z,31010.50,31033.50,31010.50,31033.50,5.00,2026-10-09T13:50:00Z,2026-10-09T13:50:00Z,AVPDL=31033.26,AVPDH=31070.82,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=2 2026-10-09T13:31:26.016Z side -1 fired LVWAP0: VWAP0=31140.95; LVWAP0=31204.39; YVWAP=31084.65; AVPDH=31068.43; AVPDL=31021.50; WVWAP=31261.91; MVWAP=31120.91
k=32 2026-10-09T13:50:00.471Z side -1 fired AVPDL: VWAP0=31126.87; RVWAP0=31095.02; LVWAP0=31157.45; YVWAP=31084.65; AVPDH=31070.94; AVPDL=31033.31; WVWAP=31257.53; MVWAP=31120.48
```

### BOOK Wf74d00e3 (NYAM): dchg_20 + prior day level false break (M 3, k 0.5), BOTH sides, bracket fixed120/120
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 17 of 17 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id Wf74d00e3 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_Wf74d00e3_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/Wf74d00e3.parquet` (23483 events: 11755 long, 11728 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `dchg_20`, module `trig_levels_prior_day` (code/th_grid/trig_levels_prior_day.py -> triggers_d/lv_prior_day.py), variant `false_break`, params {"M": 3, "k": 0.5}, bracket `fixed120/120`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/dchg_20/trig_levels_prior_day.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1385, L6M 2809, L3M 2640; t 4.5 over 1043 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 169..185 (2026-06-28 to 2026-10-24) = 17 held week(s); months in the cell file: 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored 6.16 / mine 6.16 pts, 8 / 8 trades; w182 2026-09-27 stored 210.47 / mine 210.47 pts, 7 / 7 trades; w183 2026-10-04 stored 125.99 / mine 125.99 pts, 2 / 2 trades; w184 2026-10-11 stored 1.96 / mine 1.96 pts, 3 / 3 trades; w185 2026-10-18 stored 174.98 / mine 174.98 pts, 5 / 5 trades (last 5 of 17 held weeks shown; 17 of 17 equal)

**1. BAR**
**BAR** row `dchg_20` = DIRECTIONAL-CHANGE leg bar. [SPEC] kernel k_dchg (kernels.py lines 197-225; build_month.py lines 125-128: `kagi_N` is built with EXACTLY the same kernel and thresholds as `dchg_N`, so the two rows are the same bars): reversal size theta = max(2, round(20 x s_rng)) ticks. Directional-change legs: a bar = a leg between two confirmed extremes. State per session key: d = 0 tracks the running high ehi and low elo from the first print; the first leg is decided when price is theta above the running low (up leg starts from that low, st = elo) or theta below the running high. d = +1: ext = running high (te = its time); when ext - p >= theta the leg is CONFIRMED: bar o = st, h = ext, l = st, c = ext, known time = timestamp of the confirming print (the close of the bar is the EXTREME, not the confirming price), then st = ext, d = -1, ext = p. d = -1 mirror (bar o = st, h = st, l = ext, c = ext). The unfinished last leg is never a bar. Theta on the sample days: 20261023: theta_ticks=44, theta_pts=11.00; 20261014: theta_ticks=44, theta_pts=11.00; 20261007: theta_ticks=46, theta_pts=11.50. [SPEC] Price-only (D8_BUILD_SPEC line 13). [READING] The live SwingBuilder class (D8Asia.cs) implements this kernel with a theta in ticks; kagi/dchg rows differ from it only in how theta is chosen (s_rng x N instead of the ATR rule).
- [SPEC] Bars per NYAM session in the loaded months: median 272 (min 15, max 1034, 222 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/dchg_20/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 417 stored / 417 rebuilt / 417 identical (o,h,l,c,known_ts,part); td 20261014: 291 stored / 291 rebuilt / 291 identical (o,h,l,c,known_ts,part); td 20261007: 146 stored / 146 rebuilt / 146 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec exists, class by parameter**: dchg_40 specified (D8_BUILD_SPEC L8cfda948); SwingBuilder(theta) in D8Asia.cs is the same kernel; theta rule here = max(2, round(N x s_rng)) not the ATR rule.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_prior_day` (th_grid/triggers_d/lv_prior_day.py; lines fd_levels.py lines 27-34). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 5 lines in this list order: PD_RTH__H, PD_RTH__L, PD_FULL__H, PD_FULL__L, PD_C__C.
- PD_RTH__H / __L = high / low of the PRIOR label day's RTH minutes (tord 930..1319 = 09:30-16:00 ET). PD_FULL__H / __L = high / low of ALL minutes of the prior label day (18:00 ET to 18:00 ET). PD_C__C = close of the prior label day's minute tord = 1319 (the 15:59 ET minute). Each is constant for the whole next label day (18:00 ET to 18:00 ET), so it is available from the very first Asia bar. 'prior label day' = the previous label day present in the store (weekends/holidays are skipped).
- Back-adjusted then converted to raw.
Variant `false_break` (M=3, k=0.5): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: M=3, k=0.5 -> k*u = 2.500 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 222 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PD_RTH_H 0.99, PD_RTH_L 0.99, PD_FULL_H 1.00, PD_FULL_L 1.00, PD_C_C 0.96.
- [READING] Module status: **NEW**: no spec page names prior_day; PD_C / PD_RTH are used inside D8Asia.cs for pivots and value area (line 1447 prints PD_C, VAL) but there is no prior-day level-trigger class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `fixed120/120` = stop 120 pts / target 120 pts, fixed (no unit rule); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 120 pts / target 120 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: One prior label day of 1-minute data. READING: with the NQ 1-minute series of the previous RTH day and previous 18:00-18:00 day the lines can be computed with no further history.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 3 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 336; share whose signal bar is bar 0 of the session: 0.10; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 14, 88, 212.5, 863.
- [SPEC] Held weeks only: 121 grid trades; share on bar 0: 0.11; signal-bar index quantiles: 0, 7, 58, 143, 363.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: PD_RTH_H 38, PD_C_C 35, PD_RTH_L 31, PD_FULL_L 10, PD_FULL_H 7.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/Wf74d00e3_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 417, first known 2026-10-23T13:30:01.534Z, last known 2026-10-23T15:58:58.890Z; rebuilt-from-tape check 417/417/417; threshold values: theta_ticks=44, theta_pts=11.000
SIGNALS (raw events of the session: 68 in total, 2 shown (those inside the input windows or traded); all are in the CSV file; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-23T13:30:01.534Z,-1,PD_RTH__L,29033.00,28994.75,5.00,Y
119,2026-10-23T13:45:35.177Z,1,PD_C__C,29145.00,29147.00,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,-1,2026-10-23T13:30:02.535Z,29010.25,0.1208,29010.22,2026-10-23T13:45:31.574Z,29130.50,Stop,120.0,120.0,-120.28,-2410.44
119,1,2026-10-23T13:45:36.226Z,29137.75,0.1208,29137.78,2026-10-23T14:41:54.155Z,29257.78,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 10 of 417 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-23T13:30:01.534Z,29030.75,29030.75,28994.75,28994.75,5.00,2026-10-23T13:29:00Z,2026-10-23T13:29:00Z,,PD_RTH_L=29033.00,-1 PD_RTH_L
1,2026-10-23T13:30:03.112Z,28994.75,29018.00,28994.75,29018.00,5.00,2026-10-23T13:30:01Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
...
113,2026-10-23T13:45:01.936Z,29113.50,29128.75,29113.50,29128.75,5.00,2026-10-23T13:44:58Z,2026-10-23T13:44:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
114,2026-10-23T13:45:06.549Z,29128.75,29128.75,29108.50,29108.50,5.00,2026-10-23T13:45:01Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
115,2026-10-23T13:45:07.922Z,29108.50,29123.25,29108.50,29123.25,5.00,2026-10-23T13:45:06Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
116,2026-10-23T13:45:12.776Z,29123.25,29123.25,29100.25,29100.25,5.00,2026-10-23T13:45:07Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
117,2026-10-23T13:45:14.609Z,29100.25,29112.00,29100.25,29112.00,5.00,2026-10-23T13:45:12Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
118,2026-10-23T13:45:15.450Z,29112.00,29112.00,29097.75,29097.75,5.00,2026-10-23T13:45:14Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
119,2026-10-23T13:45:35.177Z,29097.75,29147.00,29097.75,29147.00,5.00,2026-10-23T13:45:15Z,2026-10-23T13:45:00Z,PD_C_C=29145.00,PD_RTH_H=29594.75,+1 PD_C_C
120,2026-10-23T13:46:11.783Z,29147.00,29147.00,29107.25,29107.25,5.00,2026-10-23T13:45:35Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-23T13:30:01.534Z side -1 fired PD_RTH_L: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
k=119 2026-10-23T13:45:35.177Z side +1 fired PD_C_C: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
```

#### td 20261014 (sess_id 202610143, NYAM session, grid week 184)
- bars of the session: 291, first known 2026-10-14T13:30:05.246Z, last known 2026-10-14T15:59:51.593Z; rebuilt-from-tape check 291/291/291; threshold values: theta_ticks=44, theta_pts=11.000
SIGNALS (raw events of the session: 15 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
28,2026-10-14T13:33:44.715Z,1,PD_RTH__L,30591.25,30592.75,5.00,Y
30,2026-10-14T13:34:02.197Z,1,PD_RTH__L,30591.25,30597.75,5.00,no
31,2026-10-14T13:34:15.054Z,-1,PD_RTH__L,30591.25,30566.00,5.00,no
62,2026-10-14T13:40:58.005Z,1,PD_RTH__L,30591.25,30621.00,5.00,no
75,2026-10-14T13:44:55.174Z,-1,PD_RTH__L,30591.25,30567.75,5.00,no
76,2026-10-14T13:45:08.177Z,1,PD_RTH__L,30591.25,30599.75,5.00,no
77,2026-10-14T13:45:31.434Z,-1,PD_RTH__L,30591.25,30578.50,5.00,no
78,2026-10-14T13:45:33.525Z,1,PD_RTH__L,30591.25,30602.00,5.00,no
79,2026-10-14T13:45:34.431Z,-1,PD_RTH__L,30591.25,30589.00,5.00,no
80,2026-10-14T13:45:41.059Z,1,PD_RTH__L,30591.25,30601.00,5.00,no
81,2026-10-14T13:45:44.452Z,-1,PD_RTH__L,30591.25,30583.75,5.00,no
82,2026-10-14T13:46:22.422Z,1,PD_RTH__L,30591.25,30622.50,5.00,no
83,2026-10-14T13:46:57.685Z,-1,PD_RTH__L,30591.25,30582.75,5.00,no
84,2026-10-14T13:47:42.428Z,1,PD_RTH__L,30591.25,30627.25,5.00,no
99,2026-10-14T13:53:00.748Z,-1,PD_RTH__L,30591.25,30544.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
28,1,2026-10-14T13:33:45.942Z,30583.25,0.1208,30583.28,2026-10-14T14:12:04.262Z,30463.00,Stop,120.0,120.0,-120.28,-2410.44
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 291 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
22,2026-10-14T13:32:44.541Z,30533.00,30549.25,30533.00,30549.25,5.00,2026-10-14T13:32:39Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
23,2026-10-14T13:32:54.335Z,30549.25,30549.25,30517.25,30517.25,5.00,2026-10-14T13:32:44Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
24,2026-10-14T13:33:05.553Z,30517.25,30547.25,30517.25,30547.25,5.00,2026-10-14T13:32:54Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
25,2026-10-14T13:33:07.859Z,30547.25,30547.25,30536.00,30536.00,5.00,2026-10-14T13:33:05Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
26,2026-10-14T13:33:28.784Z,30536.00,30585.75,30536.00,30585.75,5.00,2026-10-14T13:33:07Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
27,2026-10-14T13:33:31.815Z,30585.75,30585.75,30570.25,30570.25,5.00,2026-10-14T13:33:28Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
28,2026-10-14T13:33:44.715Z,30570.25,30592.75,30570.25,30592.75,5.00,2026-10-14T13:33:31Z,2026-10-14T13:33:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,+1 PD_RTH_L
29,2026-10-14T13:33:54.762Z,30592.75,30592.75,30578.50,30578.50,5.00,2026-10-14T13:33:44Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=28 2026-10-14T13:33:44.715Z side +1 fired PD_RTH_L: PD_RTH_H=30814.75; PD_RTH_L=30591.25; PD_FULL_H=30906.00; PD_FULL_L=30591.25; PD_C_C=30788.75
```

#### td 20261007 (sess_id 202610073, NYAM session, grid week 183)
- bars of the session: 146, first known 2026-10-07T13:30:08.583Z, last known 2026-10-07T15:52:36.479Z; rebuilt-from-tape check 146/146/146; threshold values: theta_ticks=46, theta_pts=11.500
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
141,2026-10-07T15:43:12.008Z,1,PD_FULL__L,31309.25,31343.50,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
141,1,2026-10-07T15:43:13.023Z,31331.75,0.1208,31331.78,2026-10-07T15:59:59.207Z,31338.25,SessionEnd,120.0,120.0,6.47,124.56
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 146 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
135,2026-10-07T15:24:06.268Z,31265.25,31281.00,31265.25,31281.00,5.00,2026-10-07T15:22:49Z,2026-10-07T15:22:00Z,,PD_FULL_L=31309.25,
136,2026-10-07T15:26:36.181Z,31281.00,31281.00,31267.25,31267.25,5.00,2026-10-07T15:24:06Z,2026-10-07T15:24:00Z,,PD_FULL_L=31309.25,
137,2026-10-07T15:28:00.066Z,31267.25,31283.75,31267.25,31283.75,5.00,2026-10-07T15:26:36Z,2026-10-07T15:26:00Z,,PD_FULL_L=31309.25,
138,2026-10-07T15:29:41.556Z,31283.75,31283.75,31268.50,31268.50,5.00,2026-10-07T15:28:00Z,2026-10-07T15:28:00Z,,PD_FULL_L=31309.25,
139,2026-10-07T15:32:59.450Z,31268.50,31295.00,31268.50,31295.00,5.00,2026-10-07T15:29:41Z,2026-10-07T15:29:00Z,,PD_FULL_L=31309.25,
140,2026-10-07T15:34:57.400Z,31295.00,31295.00,31281.75,31281.75,5.00,2026-10-07T15:32:59Z,2026-10-07T15:32:00Z,,PD_FULL_L=31309.25,
141,2026-10-07T15:43:12.008Z,31281.75,31343.50,31281.75,31343.50,5.00,2026-10-07T15:34:57Z,2026-10-07T15:34:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,+1 PD_FULL_L
142,2026-10-07T15:44:26.006Z,31343.50,31343.50,31327.50,31327.50,5.00,2026-10-07T15:43:12Z,2026-10-07T15:43:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=141 2026-10-07T15:43:12.008Z side +1 fired PD_FULL_L: PD_RTH_H=31616.50; PD_RTH_L=31457.75; PD_FULL_H=31616.50; PD_FULL_L=31309.25; PD_C_C=31480.75
```

### BOOK W3e503490 (NYAM): pnf_5 + prior day level false break native (M 1, k 0.5), BOTH sides, bracket sym8u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W3e503490 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_W3e503490_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W3e503490.parquet` (17798 events: 8937 long, 8861 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `pnf_5`, module `trig_levels_prior_day` (code/th_grid/trig_levels_prior_day.py -> triggers_d/lv_prior_day.py), variant `false_break_native`, params {"M": 1, "k": 0.5}, bracket `sym8u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/pnf_5/trig_levels_prior_day.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1222, L6M 2750, L3M 2229; t 4.1 over 1677 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored 232.68 / mine 232.68 pts, 8 / 8 trades; w183 2026-10-04 stored 92.47 / mine 92.47 pts, 2 / 2 trades; w184 2026-10-11 stored -9.56 / mine -9.56 pts, 3 / 3 trades; w185 2026-10-18 stored -224.19 / mine -224.19 pts, 9 / 9 trades

**1. BAR**
**BAR** row `pnf_5` = POINT-AND-FIGURE column bar. [SPEC] kernel th_bars/kernels.py k_pnf (lines 248-273), built by build_month.py line 135-136: box B = max(1, round(5 x s_rng)) ticks (numpy round half to even; 1 tick = 0.25 pt), 3-box reversal. State per session key: first print sets lvl = st = p, d = 0. d = 0: a print >= lvl + B starts an UP column (st = lvl, lvl += ((p-lvl)//B) x B); a print <= lvl - B starts a DOWN column (mirror). d = +1: p >= lvl + B extends (lvl += ((p-lvl)//B) x B); p <= lvl - 3B CLOSES the column: bar o = st, h = lvl, l = st, c = lvl, then a DOWN column starts with st = lvl - B and lvl = lvl - ((lvl-p)//B) x B. d = -1 mirror (bar o = st, h = st, l = lvl, c = lvl; new st = lvl + B). One bar per COMPLETED column; known time = timestamp of the confirming print (the print that moved 3 boxes against the column); the unfinished column at the session end is never a bar; there are no part=1 bars. Resets at every session boundary (02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET) and at a contract roll. [SPEC] Price-only: unaffected by the print rule (D8_BUILD_SPEC line 13; D8_PRINT_RULE). Box on the three sample days: 20261023: box_ticks=11, box_pts=2.75; 20261014: box_ticks=11, box_pts=2.75; 20261007: box_ticks=11, box_pts=2.75.
- [SPEC] Bars per NYAM session in the loaded months: median 339 (min 22, max 1394, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/pnf_5/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 601 stored / 601 rebuilt / 601 identical (o,h,l,c,known_ts,part); td 20261014: 410 stored / 410 rebuilt / 410 identical (o,h,l,c,known_ts,part); td 20261007: 217 stored / 217 rebuilt / 217 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec only**: pnf_7 specified in D8_BUILD_SPEC (L9c2622b0, Asia; stored Asia bars rebuilt identical in D8_ASIA_NEWBOOK_INPUTS.md) and pnf_14 in D8_NYAM_SPEC_L43f0cbfb; NO class for it in D8Asia.cs (class list read): box is a parameter, so pnf_5 / pnf_10 are parameter changes of a builder that is specified but not yet in the strategy file.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_prior_day` (th_grid/triggers_d/lv_prior_day.py; lines fd_levels.py lines 27-34). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 5 lines in this list order: PD_RTH__H, PD_RTH__L, PD_FULL__H, PD_FULL__L, PD_C__C.
- PD_RTH__H / __L = high / low of the PRIOR label day's RTH minutes (tord 930..1319 = 09:30-16:00 ET). PD_FULL__H / __L = high / low of ALL minutes of the prior label day (18:00 ET to 18:00 ET). PD_C__C = close of the prior label day's minute tord = 1319 (the 15:59 ET minute). Each is constant for the whole next label day (18:00 ET to 18:00 ET), so it is available from the very first Asia bar. 'prior label day' = the previous label day present in the store (weekends/holidays are skipped).
- Back-adjusted then converted to raw.
Variant `false_break_native` (M=1, k=0.5): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (native) = rolling median of (high - low) over the previous 100 bars of THIS book's bar series (bars j-100..j-1, shifted one bar, min_periods 20, floor 0.5 pt; NaN before 20 bars) (fd_common.unit); every tolerance below is x u. With these parameters: M=1, k=0.5 -> k*u = 0.5 x u.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PD_RTH_H 0.99, PD_RTH_L 0.99, PD_FULL_H 1.00, PD_FULL_L 1.00, PD_C_C 0.97.
- [READING] Module status: **NEW**: no spec page names prior_day; PD_C / PD_RTH are used inside D8Asia.cs for pivots and value area (line 1447 prints PD_C, VAL) but there is no prior-day level-trigger class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `sym8u` = unit rule sym8u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule sym8u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: One prior label day of 1-minute data. READING: with the NQ 1-minute series of the previous RTH day and previous 18:00-18:00 day the lines can be computed with no further history.
- [SPEC] Warm-up of the trigger: native u needs 20 earlier bars of the continuous series (rolling 100, shifted). Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 279; share whose signal bar is bar 0 of the session: 0.06; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 34, 140, 263.5, 1113.
- [SPEC] Held weeks only: 22 grid trades; share on bar 0: 0.09; signal-bar index quantiles: 0, 20, 164, 257.5, 494.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: PD_RTH_L 8, PD_C_C 6, PD_RTH_H 4, PD_FULL_H 2, PD_FULL_L 2.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W3e503490_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 601, first known 2026-10-23T13:30:01.526Z, last known 2026-10-23T15:58:56.530Z; rebuilt-from-tape check 601/601/601; threshold values: box_ticks=11, box_pts=2.750
SIGNALS (raw events of the session: 51 in total, 4 shown (those inside the input windows or traded); all are in the CSV file; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-23T13:30:01.526Z,-1,PD_RTH__L,29033.00,28996.25,11.00,Y
62,2026-10-23T13:34:10.629Z,-1,PD_RTH__L,29033.00,29026.50,11.00,Y
63,2026-10-23T13:34:11.283Z,1,PD_RTH__L,29033.00,29034.75,11.00,no
205,2026-10-23T13:52:24.955Z,1,PD_C__C,29145.00,29155.75,11.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,-1,2026-10-23T13:30:02.526Z,29008.50,0.1776,29008.46,2026-10-23T13:32:31.257Z,29096.75,Stop,88.0,88.0,-88.29,-1770.73
62,-1,2026-10-23T13:34:11.633Z,29019.25,0.1776,29019.21,2026-10-23T13:42:25.737Z,29107.50,Stop,88.0,88.0,-88.29,-1770.73
205,1,2026-10-23T13:52:25.975Z,29145.50,0.1776,29145.54,2026-10-23T14:40:11.083Z,29233.54,Target,88.0,88.0,88.00,1755.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 18 of 601 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-23T13:30:01.526Z,29029.25,29029.25,28996.25,28996.25,11.00,2026-10-23T13:29:00Z,2026-10-23T13:29:00Z,,PD_RTH_L=29033.00,-1 PD_RTH_L
1,2026-10-23T13:30:03.112Z,28999.00,29015.50,28999.00,29015.50,11.00,2026-10-23T13:30:01Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
...
56,2026-10-23T13:33:38.205Z,29056.75,29056.75,29034.75,29034.75,11.00,2026-10-23T13:33:33Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
57,2026-10-23T13:33:44.067Z,29037.50,29051.25,29037.50,29051.25,11.00,2026-10-23T13:33:38Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
58,2026-10-23T13:33:47.625Z,29048.50,29048.50,29034.75,29034.75,11.00,2026-10-23T13:33:44Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
59,2026-10-23T13:33:49.689Z,29037.50,29048.50,29037.50,29048.50,11.00,2026-10-23T13:33:47Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
60,2026-10-23T13:33:52.857Z,29045.75,29045.75,29037.50,29037.50,11.00,2026-10-23T13:33:49Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
61,2026-10-23T13:34:01.873Z,29040.25,29048.50,29040.25,29048.50,11.00,2026-10-23T13:33:52Z,2026-10-23T13:33:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
62,2026-10-23T13:34:10.629Z,29045.75,29045.75,29026.50,29026.50,11.00,2026-10-23T13:34:01Z,2026-10-23T13:34:00Z,,PD_RTH_L=29033.00,-1 PD_RTH_L
63,2026-10-23T13:34:11.283Z,29029.25,29034.75,29029.25,29034.75,11.00,2026-10-23T13:34:10Z,2026-10-23T13:34:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,+1 PD_RTH_L
...
199,2026-10-23T13:51:17.605Z,29092.50,29120.00,29092.50,29120.00,11.00,2026-10-23T13:50:50Z,2026-10-23T13:50:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
200,2026-10-23T13:51:21.209Z,29117.25,29117.25,29106.25,29106.25,11.00,2026-10-23T13:51:17Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
201,2026-10-23T13:51:44.546Z,29109.00,29133.75,29109.00,29133.75,11.00,2026-10-23T13:51:21Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
202,2026-10-23T13:51:53.296Z,29131.00,29131.00,29114.50,29114.50,11.00,2026-10-23T13:51:44Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
203,2026-10-23T13:52:13.911Z,29117.25,29136.50,29117.25,29136.50,11.00,2026-10-23T13:51:53Z,2026-10-23T13:51:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
204,2026-10-23T13:52:16.191Z,29133.75,29133.75,29122.75,29122.75,11.00,2026-10-23T13:52:13Z,2026-10-23T13:52:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
205,2026-10-23T13:52:24.955Z,29125.50,29155.75,29125.50,29155.75,11.00,2026-10-23T13:52:16Z,2026-10-23T13:52:00Z,PD_C_C=29145.00,PD_RTH_H=29594.75,+1 PD_C_C
206,2026-10-23T13:52:30.994Z,29153.00,29153.00,29147.50,29147.50,11.00,2026-10-23T13:52:24Z,2026-10-23T13:52:00Z,PD_C_C=29145.00,PD_RTH_H=29594.75,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-23T13:30:01.526Z side -1 fired PD_RTH_L: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
k=62 2026-10-23T13:34:10.629Z side -1 fired PD_RTH_L: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
k=205 2026-10-23T13:52:24.955Z side +1 fired PD_C_C: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
```

#### td 20261014 (sess_id 202610143, NYAM session, grid week 184)
- bars of the session: 410, first known 2026-10-14T13:30:00.647Z, last known 2026-10-14T15:59:43.633Z; rebuilt-from-tape check 410/410/410; threshold values: box_ticks=11, box_pts=2.750
SIGNALS (raw events of the session: 13 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
35,2026-10-14T13:33:44.317Z,1,PD_RTH__L,30591.25,30592.75,12.38,Y
39,2026-10-14T13:34:02.197Z,1,PD_RTH__L,30591.25,30595.50,11.00,no
83,2026-10-14T13:40:33.658Z,1,PD_RTH__L,30591.25,30609.25,12.38,no
102,2026-10-14T13:44:54.210Z,-1,PD_RTH__L,30591.25,30568.00,11.00,no
103,2026-10-14T13:45:08.063Z,1,PD_RTH__L,30591.25,30598.25,11.00,no
104,2026-10-14T13:45:18.034Z,-1,PD_RTH__L,30591.25,30579.00,12.38,no
105,2026-10-14T13:45:33.406Z,1,PD_RTH__L,30591.25,30601.00,12.38,no
106,2026-10-14T13:45:34.401Z,-1,PD_RTH__L,30591.25,30590.00,12.38,no
108,2026-10-14T13:45:44.432Z,-1,PD_RTH__L,30591.25,30584.50,11.00,no
109,2026-10-14T13:46:22.422Z,1,PD_RTH__L,30591.25,30620.25,11.00,no
110,2026-10-14T13:46:57.174Z,-1,PD_RTH__L,30591.25,30584.50,11.00,no
111,2026-10-14T13:47:14.198Z,1,PD_RTH__L,30591.25,30601.00,11.00,no
136,2026-10-14T13:52:59.486Z,-1,PD_RTH__L,30591.25,30546.00,11.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
35,1,2026-10-14T13:33:45.353Z,30583.00,0.1776,30583.04,2026-10-14T13:57:57.606Z,30483.75,Stop,99.0,99.0,-99.29,-1990.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 410 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
29,2026-10-14T13:32:57.499Z,30521.25,30535.00,30521.25,30535.00,12.38,2026-10-14T13:32:54Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
30,2026-10-14T13:32:58.513Z,30532.25,30532.25,30526.75,30526.75,12.38,2026-10-14T13:32:57Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
31,2026-10-14T13:33:05.281Z,30529.50,30546.00,30529.50,30546.00,12.38,2026-10-14T13:32:58Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
32,2026-10-14T13:33:07.835Z,30543.25,30543.25,30537.75,30537.75,12.38,2026-10-14T13:33:05Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
33,2026-10-14T13:33:28.707Z,30540.50,30584.50,30540.50,30584.50,11.00,2026-10-14T13:33:07Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
34,2026-10-14T13:33:31.737Z,30581.75,30581.75,30570.75,30570.75,12.38,2026-10-14T13:33:28Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
35,2026-10-14T13:33:44.317Z,30573.50,30592.75,30573.50,30592.75,12.38,2026-10-14T13:33:31Z,2026-10-14T13:33:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,+1 PD_RTH_L
36,2026-10-14T13:33:48.388Z,30590.00,30590.00,30581.75,30581.75,12.38,2026-10-14T13:33:44Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=35 2026-10-14T13:33:44.317Z side +1 fired PD_RTH_L: PD_RTH_H=30814.75; PD_RTH_L=30591.25; PD_FULL_H=30906.00; PD_FULL_L=30591.25; PD_C_C=30788.75
```

#### td 20261007 (sess_id 202610073, NYAM session, grid week 183)
- bars of the session: 217, first known 2026-10-07T13:30:00.639Z, last known 2026-10-07T15:57:31.525Z; rebuilt-from-tape check 217/217/217; threshold values: box_ticks=11, box_pts=2.750
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
206,2026-10-07T15:43:03.010Z,1,PD_FULL__L,31309.25,31341.00,11.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
206,1,2026-10-07T15:43:04.021Z,31333.25,0.1776,31333.29,2026-10-07T15:59:59.207Z,31338.25,SessionEnd,88.0,88.0,4.96,94.27
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 217 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
200,2026-10-07T15:30:14.714Z,31272.25,31280.50,31272.25,31280.50,11.00,2026-10-07T15:29:11Z,2026-10-07T15:29:00Z,,PD_FULL_L=31309.25,
201,2026-10-07T15:30:25.585Z,31277.75,31277.75,31272.25,31272.25,11.00,2026-10-07T15:30:14Z,2026-10-07T15:30:00Z,,PD_FULL_L=31309.25,
202,2026-10-07T15:32:55.592Z,31275.00,31294.25,31275.00,31294.25,11.00,2026-10-07T15:30:25Z,2026-10-07T15:30:00Z,,PD_FULL_L=31309.25,
203,2026-10-07T15:33:45.693Z,31291.50,31291.50,31283.25,31283.25,11.00,2026-10-07T15:32:55Z,2026-10-07T15:32:00Z,,PD_FULL_L=31309.25,
204,2026-10-07T15:33:57.284Z,31286.00,31291.50,31286.00,31291.50,11.00,2026-10-07T15:33:45Z,2026-10-07T15:33:00Z,,PD_FULL_L=31309.25,
205,2026-10-07T15:34:52.492Z,31288.75,31288.75,31283.25,31283.25,11.00,2026-10-07T15:33:57Z,2026-10-07T15:33:00Z,,PD_FULL_L=31309.25,
206,2026-10-07T15:43:03.010Z,31286.00,31341.00,31286.00,31341.00,11.00,2026-10-07T15:34:52Z,2026-10-07T15:34:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,+1 PD_FULL_L
207,2026-10-07T15:44:24.104Z,31338.25,31338.25,31330.00,31330.00,11.00,2026-10-07T15:43:03Z,2026-10-07T15:43:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=206 2026-10-07T15:43:03.010Z side +1 fired PD_FULL_L: PD_RTH_H=31616.50; PD_RTH_L=31457.75; PD_FULL_H=31616.50; PD_FULL_L=31309.25; PD_C_C=31480.75
```

### BOOK W10e7f4cd (NYAM): dchg_14 + prior day level false break native (M 3, k 0.5), BOTH sides, bracket sym8u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W10e7f4cd (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_W10e7f4cd_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W10e7f4cd.parquet` (26582 events: 13270 long, 13312 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `dchg_14`, module `trig_levels_prior_day` (code/th_grid/trig_levels_prior_day.py -> triggers_d/lv_prior_day.py), variant `false_break_native`, params {"M": 3, "k": 0.5}, bracket `sym8u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/dchg_14/trig_levels_prior_day.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1272, L6M 3815, L3M 2985; t 4.1 over 1412 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored 258.97 / mine 258.97 pts, 8 / 8 trades; w183 2026-10-04 stored 110.74 / mine 110.74 pts, 2 / 2 trades; w184 2026-10-11 stored -14.54 / mine -14.54 pts, 3 / 3 trades; w185 2026-10-18 stored -63.56 / mine -63.56 pts, 7 / 7 trades

**1. BAR**
**BAR** row `dchg_14` = DIRECTIONAL-CHANGE leg bar. [SPEC] kernel k_dchg (kernels.py lines 197-225; build_month.py lines 125-128: `kagi_N` is built with EXACTLY the same kernel and thresholds as `dchg_N`, so the two rows are the same bars): reversal size theta = max(2, round(14 x s_rng)) ticks. Directional-change legs: a bar = a leg between two confirmed extremes. State per session key: d = 0 tracks the running high ehi and low elo from the first print; the first leg is decided when price is theta above the running low (up leg starts from that low, st = elo) or theta below the running high. d = +1: ext = running high (te = its time); when ext - p >= theta the leg is CONFIRMED: bar o = st, h = ext, l = st, c = ext, known time = timestamp of the confirming print (the close of the bar is the EXTREME, not the confirming price), then st = ext, d = -1, ext = p. d = -1 mirror (bar o = st, h = st, l = ext, c = ext). The unfinished last leg is never a bar. Theta on the sample days: 20261023: theta_ticks=31, theta_pts=7.75; 20261014: theta_ticks=31, theta_pts=7.75; 20261007: theta_ticks=32, theta_pts=8.00. [SPEC] Price-only (D8_BUILD_SPEC line 13). [READING] The live SwingBuilder class (D8Asia.cs) implements this kernel with a theta in ticks; kagi/dchg rows differ from it only in how theta is chosen (s_rng x N instead of the ATR rule).
- [SPEC] Bars per NYAM session in the loaded months: median 498 (min 28, max 1880, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/dchg_14/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 881 stored / 881 rebuilt / 881 identical (o,h,l,c,known_ts,part); td 20261014: 623 stored / 623 rebuilt / 623 identical (o,h,l,c,known_ts,part); td 20261007: 293 stored / 293 rebuilt / 293 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec exists, class by parameter**: dchg_40 specified (D8_BUILD_SPEC L8cfda948); SwingBuilder(theta) in D8Asia.cs is the same kernel; theta rule here = max(2, round(N x s_rng)) not the ATR rule.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_prior_day` (th_grid/triggers_d/lv_prior_day.py; lines fd_levels.py lines 27-34). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 5 lines in this list order: PD_RTH__H, PD_RTH__L, PD_FULL__H, PD_FULL__L, PD_C__C.
- PD_RTH__H / __L = high / low of the PRIOR label day's RTH minutes (tord 930..1319 = 09:30-16:00 ET). PD_FULL__H / __L = high / low of ALL minutes of the prior label day (18:00 ET to 18:00 ET). PD_C__C = close of the prior label day's minute tord = 1319 (the 15:59 ET minute). Each is constant for the whole next label day (18:00 ET to 18:00 ET), so it is available from the very first Asia bar. 'prior label day' = the previous label day present in the store (weekends/holidays are skipped).
- Back-adjusted then converted to raw.
Variant `false_break_native` (M=3, k=0.5): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (native) = rolling median of (high - low) over the previous 100 bars of THIS book's bar series (bars j-100..j-1, shifted one bar, min_periods 20, floor 0.5 pt; NaN before 20 bars) (fd_common.unit); every tolerance below is x u. With these parameters: M=3, k=0.5 -> k*u = 0.5 x u.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PD_RTH_H 0.99, PD_RTH_L 0.99, PD_FULL_H 1.00, PD_FULL_L 1.00, PD_C_C 0.97.
- [READING] Module status: **NEW**: no spec page names prior_day; PD_C / PD_RTH are used inside D8Asia.cs for pivots and value area (line 1447 prints PD_C, VAL) but there is no prior-day level-trigger class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `sym8u` = unit rule sym8u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule sym8u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: One prior label day of 1-minute data. READING: with the NQ 1-minute series of the previous RTH day and previous 18:00-18:00 day the lines can be computed with no further history.
- [SPEC] Warm-up of the trigger: native u needs 20 earlier bars of the continuous series (rolling 100, shifted). Memory M / hold n of the variant: 3 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 266; share whose signal bar is bar 0 of the session: 0.07; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 28.25, 193.5, 363.25, 1396.
- [SPEC] Held weeks only: 20 grid trades; share on bar 0: 0.10; signal-bar index quantiles: 0, 17.25, 228.5, 354.25, 585.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: PD_RTH_L 7, PD_C_C 5, PD_RTH_H 4, PD_FULL_H 2, PD_FULL_L 2.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W10e7f4cd_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 881, first known 2026-10-23T13:30:01.440Z, last known 2026-10-23T15:58:55.772Z; rebuilt-from-tape check 881/881/881; threshold values: theta_ticks=31, theta_pts=7.750
SIGNALS (raw events of the session: 75 in total, 2 shown (those inside the input windows or traded); all are in the CSV file; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-23T13:30:01.440Z,-1,PD_RTH__L,29033.00,28994.75,12.50,Y
243,2026-10-23T13:45:34.962Z,1,PD_C__C,29145.00,29147.00,13.62,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,-1,2026-10-23T13:30:02.448Z,29007.50,0.1208,29007.47,2026-10-23T13:42:25.737Z,29108.75,Stop,101.0,101.0,-101.28,-2030.44
243,1,2026-10-23T13:45:35.979Z,29137.75,0.1208,29137.78,2026-10-23T14:40:23.994Z,29243.78,Target,106.0,106.0,106.00,2115.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 10 of 881 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-23T13:30:01.440Z,29030.75,29030.75,28994.75,28994.75,12.50,2026-10-23T13:29:32Z,2026-10-23T13:29:00Z,,PD_RTH_L=29033.00,-1 PD_RTH_L
1,2026-10-23T13:30:02.944Z,28994.75,29018.00,28994.75,29018.00,12.50,2026-10-23T13:30:01Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
...
237,2026-10-23T13:45:14.007Z,29100.25,29112.00,29100.25,29112.00,13.50,2026-10-23T13:45:11Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
238,2026-10-23T13:45:15.237Z,29112.00,29112.00,29097.75,29097.75,13.50,2026-10-23T13:45:14Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
239,2026-10-23T13:45:17.413Z,29097.75,29115.25,29097.75,29115.25,13.50,2026-10-23T13:45:15Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
240,2026-10-23T13:45:18.541Z,29115.25,29115.25,29105.00,29105.00,13.62,2026-10-23T13:45:17Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
241,2026-10-23T13:45:24.450Z,29105.00,29128.00,29105.00,29128.00,13.62,2026-10-23T13:45:18Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
242,2026-10-23T13:45:29.887Z,29128.00,29128.00,29117.50,29117.50,13.75,2026-10-23T13:45:24Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
243,2026-10-23T13:45:34.962Z,29117.50,29147.00,29117.50,29147.00,13.62,2026-10-23T13:45:29Z,2026-10-23T13:45:00Z,PD_C_C=29145.00,PD_RTH_H=29594.75,+1 PD_C_C
244,2026-10-23T13:45:42.433Z,29147.00,29147.00,29129.50,29129.50,13.75,2026-10-23T13:45:34Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-23T13:30:01.440Z side -1 fired PD_RTH_L: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
k=243 2026-10-23T13:45:34.962Z side +1 fired PD_C_C: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
```

#### td 20261014 (sess_id 202610143, NYAM session, grid week 184)
- bars of the session: 623, first known 2026-10-14T13:30:02.288Z, last known 2026-10-14T15:59:42.729Z; rebuilt-from-tape check 623/623/623; threshold values: theta_ticks=31, theta_pts=7.750
SIGNALS (raw events of the session: 20 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
50,2026-10-14T13:33:44.307Z,1,PD_RTH__L,30591.25,30592.75,12.50,Y
54,2026-10-14T13:33:57.251Z,1,PD_RTH__L,30591.25,30597.75,12.50,no
55,2026-10-14T13:34:13.051Z,-1,PD_RTH__L,30591.25,30566.00,12.62,no
118,2026-10-14T13:40:32.751Z,1,PD_RTH__L,30591.25,30610.75,12.88,no
145,2026-10-14T13:43:57.304Z,-1,PD_RTH__L,30591.25,30591.00,12.88,no
147,2026-10-14T13:44:11.825Z,-1,PD_RTH__L,30591.25,30573.00,12.75,no
152,2026-10-14T13:45:07.038Z,1,PD_RTH__L,30591.25,30599.75,12.25,no
153,2026-10-14T13:45:17.954Z,-1,PD_RTH__L,30591.25,30578.50,12.25,no
156,2026-10-14T13:45:33.369Z,1,PD_RTH__L,30591.25,30602.00,12.25,no
157,2026-10-14T13:45:34.381Z,-1,PD_RTH__L,30591.25,30589.00,12.25,no
158,2026-10-14T13:45:39.347Z,1,PD_RTH__L,30591.25,30601.00,12.25,no
159,2026-10-14T13:45:44.363Z,-1,PD_RTH__L,30591.25,30583.75,12.25,no
160,2026-10-14T13:45:47.431Z,1,PD_RTH__L,30591.25,30595.25,12.25,no
161,2026-10-14T13:45:52.472Z,-1,PD_RTH__L,30591.25,30587.00,12.25,no
162,2026-10-14T13:45:54.913Z,1,PD_RTH__L,30591.25,30595.00,12.25,no
164,2026-10-14T13:45:58.819Z,1,PD_RTH__L,30591.25,30595.25,12.25,no
166,2026-10-14T13:46:17.413Z,1,PD_RTH__L,30591.25,30620.75,12.00,no
169,2026-10-14T13:46:56.675Z,-1,PD_RTH__L,30591.25,30582.75,11.75,no
170,2026-10-14T13:47:13.238Z,1,PD_RTH__L,30591.25,30603.25,12.00,no
205,2026-10-14T13:52:57.066Z,-1,PD_RTH__L,30591.25,30544.25,11.50,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
50,1,2026-10-14T13:33:45.353Z,30583.00,0.1208,30583.03,2026-10-14T13:58:22.525Z,30471.75,Stop,111.0,111.0,-111.28,-2230.44
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 623 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
44,2026-10-14T13:33:05.040Z,30526.75,30547.25,30526.75,30547.25,12.38,2026-10-14T13:32:58Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
45,2026-10-14T13:33:07.014Z,30547.25,30547.25,30536.00,30536.00,12.38,2026-10-14T13:33:05Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
46,2026-10-14T13:33:22.360Z,30536.00,30571.50,30536.00,30571.50,12.38,2026-10-14T13:33:07Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
47,2026-10-14T13:33:24.417Z,30571.50,30571.50,30563.75,30563.75,12.50,2026-10-14T13:33:22Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
48,2026-10-14T13:33:28.634Z,30563.75,30585.75,30563.75,30585.75,12.50,2026-10-14T13:33:24Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
49,2026-10-14T13:33:31.692Z,30585.75,30585.75,30570.25,30570.25,12.50,2026-10-14T13:33:28Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
50,2026-10-14T13:33:44.307Z,30570.25,30592.75,30570.25,30592.75,12.50,2026-10-14T13:33:31Z,2026-10-14T13:33:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,+1 PD_RTH_L
51,2026-10-14T13:33:48.239Z,30592.75,30592.75,30580.00,30580.00,12.50,2026-10-14T13:33:44Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=50 2026-10-14T13:33:44.307Z side +1 fired PD_RTH_L: PD_RTH_H=30814.75; PD_RTH_L=30591.25; PD_FULL_H=30906.00; PD_FULL_L=30591.25; PD_C_C=30788.75
```

#### td 20261007 (sess_id 202610073, NYAM session, grid week 183)
- bars of the session: 293, first known 2026-10-07T13:30:06.261Z, last known 2026-10-07T15:59:50.077Z; rebuilt-from-tape check 293/293/293; threshold values: theta_ticks=32, theta_pts=8.000
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
275,2026-10-07T15:39:55.267Z,1,PD_FULL__L,31309.25,31334.75,13.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
275,1,2026-10-07T15:39:56.704Z,31327.00,0.1208,31327.03,2026-10-07T15:59:59.207Z,31338.25,SessionEnd,105.0,105.0,11.22,219.56
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 293 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
269,2026-10-07T15:32:53.146Z,31272.00,31295.00,31272.00,31295.00,13.12,2026-10-07T15:30:25Z,2026-10-07T15:30:00Z,,PD_FULL_L=31309.25,
270,2026-10-07T15:33:26.443Z,31295.00,31295.00,31281.75,31281.75,13.25,2026-10-07T15:32:53Z,2026-10-07T15:32:00Z,,PD_FULL_L=31309.25,
271,2026-10-07T15:33:34.208Z,31281.75,31290.25,31281.75,31290.25,13.25,2026-10-07T15:33:26Z,2026-10-07T15:33:00Z,,PD_FULL_L=31309.25,
272,2026-10-07T15:33:45.693Z,31290.25,31290.25,31282.00,31282.00,13.12,2026-10-07T15:33:34Z,2026-10-07T15:33:00Z,,PD_FULL_L=31309.25,
273,2026-10-07T15:33:57.262Z,31282.00,31292.25,31282.00,31292.25,13.12,2026-10-07T15:33:45Z,2026-10-07T15:33:00Z,,PD_FULL_L=31309.25,
274,2026-10-07T15:34:30.791Z,31292.25,31292.25,31281.75,31281.75,13.00,2026-10-07T15:33:57Z,2026-10-07T15:33:00Z,,PD_FULL_L=31309.25,
275,2026-10-07T15:39:55.267Z,31281.75,31334.75,31281.75,31334.75,13.00,2026-10-07T15:34:30Z,2026-10-07T15:34:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,+1 PD_FULL_L
276,2026-10-07T15:40:07.285Z,31334.75,31334.75,31324.75,31324.75,13.00,2026-10-07T15:39:55Z,2026-10-07T15:39:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=275 2026-10-07T15:39:55.267Z side +1 fired PD_FULL_L: PD_RTH_H=31616.50; PD_RTH_L=31457.75; PD_FULL_H=31616.50; PD_FULL_L=31309.25; PD_C_C=31480.75
```

### BOOK Wd5038cce (NYAM): kagi_28 + prior day level false break (M 3, k 0.5), BOTH sides, bracket sym15u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 17 of 17 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id Wd5038cce (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_NY_Wd5038cce_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/Wd5038cce.parquet` (17337 events: 8680 long, 8657 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `kagi_28`, module `trig_levels_prior_day` (code/th_grid/trig_levels_prior_day.py -> triggers_d/lv_prior_day.py), variant `false_break`, params {"M": 3, "k": 0.5}, bracket `sym15u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/kagi_28/trig_levels_prior_day.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1313, L6M 2327, L3M 1321; t 4.5 over 1050 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 169..185 (2026-06-28 to 2026-10-24) = 17 held week(s); months in the cell file: 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored 18.62 / mine 18.62 pts, 6 / 6 trades; w182 2026-09-27 stored -28.12 / mine -28.12 pts, 7 / 7 trades; w183 2026-10-04 stored 128.97 / mine 128.97 pts, 2 / 2 trades; w184 2026-10-11 stored 6.44 / mine 6.44 pts, 3 / 3 trades; w185 2026-10-18 stored 62.16 / mine 62.16 pts, 6 / 6 trades (last 5 of 17 held weeks shown; 17 of 17 equal)

**1. BAR**
**BAR** row `kagi_28` = Kagi line (identical to dchg). [SPEC] kernel k_dchg (kernels.py lines 197-225; build_month.py lines 125-128: `kagi_N` is built with EXACTLY the same kernel and thresholds as `dchg_N`, so the two rows are the same bars): reversal size theta = max(2, round(28 x s_rng)) ticks. Directional-change legs: a bar = a leg between two confirmed extremes. State per session key: d = 0 tracks the running high ehi and low elo from the first print; the first leg is decided when price is theta above the running low (up leg starts from that low, st = elo) or theta below the running high. d = +1: ext = running high (te = its time); when ext - p >= theta the leg is CONFIRMED: bar o = st, h = ext, l = st, c = ext, known time = timestamp of the confirming print (the close of the bar is the EXTREME, not the confirming price), then st = ext, d = -1, ext = p. d = -1 mirror (bar o = st, h = st, l = ext, c = ext). The unfinished last leg is never a bar. Theta on the sample days: 20261023: theta_ticks=61, theta_pts=15.25; 20261014: theta_ticks=61, theta_pts=15.25; 20261007: theta_ticks=64, theta_pts=16.00. [SPEC] Price-only (D8_BUILD_SPEC line 13). [READING] The live SwingBuilder class (D8Asia.cs) implements this kernel with a theta in ticks; kagi/dchg rows differ from it only in how theta is chosen (s_rng x N instead of the ATR rule).
- [SPEC] Bars per NYAM session in the loaded months: median 147 (min 9, max 545, 222 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/kagi_28/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 233 stored / 233 rebuilt / 233 identical (o,h,l,c,known_ts,part); td 20261014: 173 stored / 173 rebuilt / 173 identical (o,h,l,c,known_ts,part); td 20261007: 70 stored / 70 rebuilt / 70 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **same bars as dchg**: kagi_N is built with the dchg kernel and thresholds (build_month.py line 127-128).

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_prior_day` (th_grid/triggers_d/lv_prior_day.py; lines fd_levels.py lines 27-34). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 5 lines in this list order: PD_RTH__H, PD_RTH__L, PD_FULL__H, PD_FULL__L, PD_C__C.
- PD_RTH__H / __L = high / low of the PRIOR label day's RTH minutes (tord 930..1319 = 09:30-16:00 ET). PD_FULL__H / __L = high / low of ALL minutes of the prior label day (18:00 ET to 18:00 ET). PD_C__C = close of the prior label day's minute tord = 1319 (the 15:59 ET minute). Each is constant for the whole next label day (18:00 ET to 18:00 ET), so it is available from the very first Asia bar. 'prior label day' = the previous label day present in the store (weekends/holidays are skipped).
- Back-adjusted then converted to raw.
Variant `false_break` (M=3, k=0.5): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: M=3, k=0.5 -> k*u = 2.500 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 222 NYAM sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PD_RTH_H 1.00, PD_RTH_L 1.00, PD_FULL_H 1.00, PD_FULL_L 1.00, PD_C_C 0.96.
- [READING] Module status: **NEW**: no spec page names prior_day; PD_C / PD_RTH are used inside D8Asia.cs for pivots and value area (line 1447 prints PD_C, VAL) but there is no prior-day level-trigger class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `sym15u` = unit rule sym15u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule sym15u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 3; window 09:30-12:00 ET (session code 3; signal bars with sess_id%10 == 3; flat at 12:00 ET).
- [SPEC] Warm-up of the level lines: One prior label day of 1-minute data. READING: with the NQ 1-minute series of the previous RTH day and previous 18:00-18:00 day the lines can be computed with no further history.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 3 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 338; share whose signal bar is bar 0 of the session: 0.13; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 6, 46.5, 109.75, 475.
- [SPEC] Held weeks only: 124 grid trades; share on bar 0: 0.17; signal-bar index quantiles: 0, 2, 28.5, 70.25, 184.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: PD_RTH_H 39, PD_C_C 38, PD_RTH_L 33, PD_FULL_L 7, PD_FULL_H 7.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/Wd5038cce_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610233, NYAM session, grid week 185)
- bars of the session: 233, first known 2026-10-23T13:30:02.530Z, last known 2026-10-23T15:59:05.197Z; rebuilt-from-tape check 233/233/233; threshold values: theta_ticks=61, theta_pts=15.250
SIGNALS (raw events of the session: 53 in total, 2 shown (those inside the input windows or traded); all are in the CSV file; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-23T13:30:02.530Z,-1,PD_RTH__L,29033.00,28994.75,5.00,Y
63,2026-10-23T13:45:38.446Z,1,PD_C__C,29145.00,29147.00,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,-1,2026-10-23T13:30:03.605Z,29001.25,0.1776,29001.21,2026-10-23T13:42:31.462Z,29121.50,Stop,120.0,120.0,-120.29,-2410.73
63,1,2026-10-23T13:45:39.504Z,29130.25,0.1776,29130.29,2026-10-23T14:40:31.351Z,29250.29,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 10 of 233 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-23T13:30:02.530Z,29030.75,29030.75,28994.75,28994.75,5.00,2026-10-23T13:27:50Z,2026-10-23T13:27:00Z,,PD_RTH_L=29033.00,-1 PD_RTH_L
1,2026-10-23T13:30:03.255Z,28994.75,29018.00,28994.75,29018.00,5.00,2026-10-23T13:30:02Z,2026-10-23T13:30:00Z,,PD_RTH_L=29033.00,
...
57,2026-10-23T13:43:41.217Z,29092.75,29113.50,29092.75,29113.50,5.00,2026-10-23T13:43:34Z,2026-10-23T13:43:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
58,2026-10-23T13:43:43.838Z,29113.50,29113.50,29096.50,29096.50,5.00,2026-10-23T13:43:41Z,2026-10-23T13:43:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
59,2026-10-23T13:44:26.418Z,29096.50,29125.00,29096.50,29125.00,5.00,2026-10-23T13:43:43Z,2026-10-23T13:43:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
60,2026-10-23T13:44:36.467Z,29125.00,29125.00,29102.00,29102.00,5.00,2026-10-23T13:44:26Z,2026-10-23T13:44:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
61,2026-10-23T13:45:03.400Z,29102.00,29128.75,29102.00,29128.75,5.00,2026-10-23T13:44:36Z,2026-10-23T13:44:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
62,2026-10-23T13:45:15.551Z,29128.75,29128.75,29097.75,29097.75,5.00,2026-10-23T13:45:03Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
63,2026-10-23T13:45:38.446Z,29097.75,29147.00,29097.75,29147.00,5.00,2026-10-23T13:45:15Z,2026-10-23T13:45:00Z,PD_C_C=29145.00,PD_RTH_H=29594.75,+1 PD_C_C
64,2026-10-23T13:46:23.130Z,29147.00,29147.00,29099.75,29099.75,5.00,2026-10-23T13:45:38Z,2026-10-23T13:45:00Z,PD_RTH_L=29033.00,PD_C_C=29145.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-23T13:30:02.530Z side -1 fired PD_RTH_L: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
k=63 2026-10-23T13:45:38.446Z side +1 fired PD_C_C: PD_RTH_H=29594.75; PD_RTH_L=29033.00; PD_FULL_H=29993.25; PD_FULL_L=29033.00; PD_C_C=29145.00
```

#### td 20261014 (sess_id 202610143, NYAM session, grid week 184)
- bars of the session: 173, first known 2026-10-14T13:30:10.028Z, last known 2026-10-14T15:59:57.071Z; rebuilt-from-tape check 173/173/173; threshold values: theta_ticks=61, theta_pts=15.250
SIGNALS (raw events of the session: 12 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
18,2026-10-14T13:34:02.607Z,1,PD_RTH__L,30591.25,30597.75,5.00,Y
19,2026-10-14T13:34:18.081Z,-1,PD_RTH__L,30591.25,30566.00,5.00,no
34,2026-10-14T13:41:03.538Z,1,PD_RTH__L,30591.25,30622.75,5.00,no
39,2026-10-14T13:44:56.498Z,-1,PD_RTH__L,30591.25,30567.75,5.00,no
40,2026-10-14T13:45:08.286Z,1,PD_RTH__L,30591.25,30599.75,5.00,no
41,2026-10-14T13:45:32.008Z,-1,PD_RTH__L,30591.25,30578.50,5.00,no
42,2026-10-14T13:45:42.973Z,1,PD_RTH__L,30591.25,30602.00,5.00,no
43,2026-10-14T13:46:03.644Z,-1,PD_RTH__L,30591.25,30583.75,5.00,no
44,2026-10-14T13:46:23.299Z,1,PD_RTH__L,30591.25,30622.50,5.00,no
45,2026-10-14T13:47:06.285Z,-1,PD_RTH__L,30591.25,30582.75,5.00,no
46,2026-10-14T13:47:45.393Z,1,PD_RTH__L,30591.25,30627.25,5.00,no
55,2026-10-14T13:53:01.039Z,-1,PD_RTH__L,30591.25,30544.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
18,1,2026-10-14T13:34:03.698Z,30581.75,0.1776,30581.79,2026-10-14T14:12:37.871Z,30461.50,Stop,120.0,120.0,-120.29,-2410.73
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 173 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
12,2026-10-14T13:32:31.819Z,30507.00,30553.25,30507.00,30553.25,5.00,2026-10-14T13:32:15Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
13,2026-10-14T13:32:40.526Z,30553.25,30553.25,30533.00,30533.00,5.00,2026-10-14T13:32:31Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
14,2026-10-14T13:32:49.113Z,30533.00,30549.25,30533.00,30549.25,5.00,2026-10-14T13:32:40Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
15,2026-10-14T13:32:54.457Z,30549.25,30549.25,30517.25,30517.25,5.00,2026-10-14T13:32:49Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
16,2026-10-14T13:33:29.935Z,30517.25,30585.75,30517.25,30585.75,5.00,2026-10-14T13:32:54Z,2026-10-14T13:32:00Z,,PD_RTH_L=30591.25,
17,2026-10-14T13:33:32.257Z,30585.75,30585.75,30570.25,30570.25,5.00,2026-10-14T13:33:29Z,2026-10-14T13:33:00Z,,PD_RTH_L=30591.25,
18,2026-10-14T13:34:02.607Z,30570.25,30597.75,30570.25,30597.75,5.00,2026-10-14T13:33:32Z,2026-10-14T13:33:00Z,PD_RTH_L=30591.25,PD_C_C=30788.75,+1 PD_RTH_L
19,2026-10-14T13:34:18.081Z,30597.75,30597.75,30566.00,30566.00,5.00,2026-10-14T13:34:02Z,2026-10-14T13:34:00Z,,PD_RTH_L=30591.25,-1 PD_RTH_L
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=18 2026-10-14T13:34:02.607Z side +1 fired PD_RTH_L: PD_RTH_H=30814.75; PD_RTH_L=30591.25; PD_FULL_H=30906.00; PD_FULL_L=30591.25; PD_C_C=30788.75
```

#### td 20261007 (sess_id 202610073, NYAM session, grid week 183)
- bars of the session: 70, first known 2026-10-07T13:30:09.652Z, last known 2026-10-07T15:54:26.963Z; rebuilt-from-tape check 70/70/70; threshold values: theta_ticks=64, theta_pts=16.000
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
65,2026-10-07T15:43:29.520Z,1,PD_FULL__L,31309.25,31343.50,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
65,1,2026-10-07T15:43:30.750Z,31328.75,0.1776,31328.79,2026-10-07T15:59:59.207Z,31338.25,SessionEnd,120.0,120.0,9.46,184.27
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 8 of 70 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
59,2026-10-07T15:14:07.151Z,31228.50,31305.50,31228.50,31305.50,5.00,2026-10-07T15:04:49Z,2026-10-07T15:04:00Z,,PD_FULL_L=31309.25,
60,2026-10-07T15:16:34.195Z,31305.50,31305.50,31285.00,31285.00,5.00,2026-10-07T15:14:07Z,2026-10-07T15:14:00Z,,PD_FULL_L=31309.25,
61,2026-10-07T15:18:29.988Z,31285.00,31307.25,31285.00,31307.25,5.00,2026-10-07T15:16:34Z,2026-10-07T15:16:00Z,,PD_FULL_L=31309.25,
62,2026-10-07T15:20:56.387Z,31307.25,31307.25,31277.25,31277.25,5.00,2026-10-07T15:18:29Z,2026-10-07T15:18:00Z,,PD_FULL_L=31309.25,
63,2026-10-07T15:21:38.761Z,31277.25,31294.00,31277.25,31294.00,5.00,2026-10-07T15:20:56Z,2026-10-07T15:20:00Z,,PD_FULL_L=31309.25,
64,2026-10-07T15:26:41.505Z,31294.00,31294.00,31265.25,31265.25,5.00,2026-10-07T15:21:38Z,2026-10-07T15:21:00Z,,PD_FULL_L=31309.25,
65,2026-10-07T15:43:29.520Z,31265.25,31343.50,31265.25,31343.50,5.00,2026-10-07T15:26:41Z,2026-10-07T15:26:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,+1 PD_FULL_L
66,2026-10-07T15:44:30.802Z,31343.50,31343.50,31327.50,31327.50,5.00,2026-10-07T15:43:29Z,2026-10-07T15:43:00Z,PD_FULL_L=31309.25,PD_RTH_L=31457.75,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=65 2026-10-07T15:43:29.520Z side +1 fired PD_FULL_L: PD_RTH_H=31616.50; PD_RTH_L=31457.75; PD_FULL_H=31616.50; PD_FULL_L=31309.25; PD_C_C=31480.75
```

## D. EXISTING VERSUS NEW, AND A ROUGH LIST OF WHAT WOULD HAVE TO BE CODED (READING; effort words are my judgement, not an estimate in hours)
**D1. Shared infrastructure for any of these books** (nothing here is specific to one book): (1) a continuous per-row bar series over ALL six session codes with the engine's reset rule at every session boundary and contract roll; (2) the daily scale table (stats_day: trailing-20-row medians of daily volume / prints / range, r0 constants; D8_BAR_DEFS section 2) built nightly, hole handling decided (stored vs hole-filled, as in the NY AM pages); (3) a 1-minute NQ series with roll back-adjustment and the label-day / ISO-week / month bookkeeping (D8Asia.cs already keeps a 1-minute series, READING); (4) the T0 level lookup (previous bar's whole-second close, minute index, 120 s staleness) and the line-at-minute-i convention (uses minutes < i); (5) the generic level_events logic for the variants used (below) with plain u = 5.0 pt or native u (rolling-100 median range shifted one bar, min 20, floor 0.5 pt) - D8Asia.cs has LevelBreakNative (break_native, n = 2) only; (6) session filter, part == 0, one position, flat at the session end, and the book's bracket (fixed points or the unit rule clip(m x u, 10, 120)).

**D2. Bar builders needed on this page:**
- `dchg`: spec exists, class by parameter - dchg_40 specified (D8_BUILD_SPEC L8cfda948); SwingBuilder(theta) in D8Asia.cs is the same kernel; theta rule here = max(2, round(N x s_rng)) not the ATR rule. Effort: small (SwingBuilder with theta = max(2, round(N x s_rng))).
- `kagi`: same bars as dchg - kagi_N is built with the dchg kernel and thresholds (build_month.py line 127-128). Effort: small (identical bars to dchg).
- `pnf`: spec only - pnf_7 specified in D8_BUILD_SPEC (L9c2622b0, Asia; stored Asia bars rebuilt identical in D8_ASIA_NEWBOOK_INPUTS.md) and pnf_14 in D8_NYAM_SPEC_L43f0cbfb; NO class for it in D8Asia.cs (class list read): box is a parameter, so pnf_5 / pnf_10 are parameter changes of a builder that is specified but not yet in the strategy file. Effort: medium (new class; kernel is 25 lines of Python).
- `urenko`: new (one parameter from frenko) - no urenko spec or class found; k_renko with R = B; FlexRenkoBuilder has R = B/2 (READING: a reversal-distance parameter). Effort: small (reversal distance parameter of the frenko class).

**D3. Level modules needed on this page:**
- `prior_day`: NEW - no spec page names prior_day; PD_C / PD_RTH are used inside D8Asia.cs for pivots and value area (line 1447 prints PD_C, VAL) but there is no prior-day level-trigger class. Effort: small (5 constants per label day).
- `vwap`: lines spec only; no VWAP code in D8Asia.cs - break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits). Effort: medium (8 anchored VWAP series on the 1-minute series: day / RTH / London / prior-day / two anchored at the prior RTH extreme minutes / week / month, each with its validity gate).

**D4. Trigger variants needed:** `break`, `false_break`, `false_break_native` (definitions in each book's section 2; the 4 base events break / reject / retest / false_break are all in fd_common.level_events, about 35 lines of Python).

**D5. Per book: what has to be coded on top of D1 (READING)**
- W3b484778 (false_break M=2/k=0.5): bar `urenko_20` [new (one parameter from frenko)]; module `prior_day` [NEW].
- Wb1ab799c (break n=3/k=0.25): bar `dchg_28` [spec exists, class by parameter]; module `vwap` [lines spec only; no VWAP code in D8Asia.cs].
- Wf74d00e3 (false_break M=3/k=0.5): bar `dchg_20` [spec exists, class by parameter]; module `prior_day` [NEW].
- W3e503490 (false_break_native M=1/k=0.5): bar `pnf_5` [spec only]; module `prior_day` [NEW].
- W10e7f4cd (false_break_native M=3/k=0.5): bar `dchg_14` [spec exists, class by parameter]; module `prior_day` [NEW].
- Wd5038cce (false_break M=3/k=0.5): bar `kagi_28` [same bars as dchg]; module `prior_day` [NEW].

**D6. Match test plan (READING):** run the live builder on the same tape for the three dated sessions of each book and compare (a) the bar closes and known times, (b) the line value of each line at T0 (CSV file), (c) the signal bars and fired lines (SIGNALS block), (d) order time = floor(known) + 2 s for the live engine versus signal known time + 1 s for the grid, (e) the exit reason and, within the stated slippage, the trade prices.

## E. OPEN POINTS FOR LEAD (READING unless marked)
- Print granularity for `tsf` (and any activity bar): the grid used the old per-record tape; D8 uses run-merged prints. A tsf book needs a LEAD decision before coding (build the old record semantics, or re-run the books on a run-merge `tsf`).
- Line files are the engine's stored files (written 2026-11-17, data to 2026-11-13). The trade tape has no files for 2026-10-31..11-04 (D8_BAR_DEFS), which touches profile / pivot / volume lines built over those days (see D8_NYAM_SPEC_Le4fede95 / B7bfd33b7 for the PRF5 hole); every dated session on this page is before 2026-10-25, so none is affected.
- Shared inputs inside the register [SPEC]: `dchg_N` and `kagi_N` rows are the SAME bars (same kernel, same thresholds), so a dchg book and a kagi book with the same module/variant/params/bracket produce the same signals (the Test 8 table lists such pairs, e.g. Wb1ab799c vs W050c781f, W10e7f4cd vs Wca8c5296); books on the same bar row share the bars but not the signals. A coder needs one builder for both.
- The 'level at T0' rule and the fact that Asia bar 0 / NY AM bar 0 take their lines and memory from the previous session are engine behaviours an NT8 coder would not guess; they are the main source of mismatch risk.
