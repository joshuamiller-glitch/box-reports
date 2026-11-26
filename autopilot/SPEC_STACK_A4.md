# SPEC_STACK_A4: coding spec pages for the six Asia books of forward-register stack A4 (both-sides LEVEL books; every statement marked SPEC or READING)

Written 2026-11-26 23:34Z by W-SPEC9 (sub-agent of LEAD, not typed by Josh). Order: autopilot/DIRECTIVE_TEST9_2313Z.md part B (relay design under Josh's standing 18:22Z order). RESEARCH / SHADOW ONLY: nothing built, nothing coded, no gate or code change, nothing queued, nothing live, no spend, nothing deleted; the execution server, the live D8Asia.cs and every chart are untouched (D8Asia.cs was only read for its class list). Layout copied from the hand-verified pages D8_NYAM_SPEC_*.md / D8_BUILD_SPEC.md per-book blocks (sections 0 identity, 1 BAR, 2 TRIGGER, 3 signal to order, 4 sides and bracket, 5 other inputs, 6 one position / window / warm-up, 7 what trades, 8 parity data) with a stack overview, an existing-versus-new table and a coding list added.

Marks: **SPEC** = read from code or measured by re-running the engine code in this session; **READING** = my inference (stated as such). Where a source could not be found it says so; nothing is guessed. Book ids and parameters are those of FORWARD_REGISTER_STACKS.md (W-TEST8 section, seed 20261128); the stack is A4 only as a REGISTER object (equal weight, 1 lot per book, bare R0, no stack rules).

## STATUS LINE (read first)
- VERIFIED [SPEC]: for all 6 books the module source was found (th_grid/trig_levels_<name>.py -> triggers_d/lv_<name>.py, line construction in fd_levels.py / fd_levels2.py / fd_profile.py), the bar kernel source was found (th_bars/kernels.py via build_month.py), and the stored grid weekly table of the cell was reproduced exactly by re-running signal_fn and the gcore2x simulator for every held week (6 of 6 books with all held weeks equal). The 3 dated sessions per book were rebuilt from the stored trade tape with the engine bar kernel (all bars identical to the stored bars) and the signals, entries and exits in section 8 are those reproduced trades.
- NOT VERIFIED / OPEN: (a) the live-engine fill (book walk) is not re-run (the table uses the grid engine); (b) line values come from the engine's stored line files (files written 2026-11-17 19:55-23:08Z by fd_levels.py / fd_levels2.py / fd_profile.py from nq1m.npz, data to 2026-11-13; they were NOT re-derived from the tape here except that the 3.7 / L43f0cbfb / Le4fede95 pages already verify vwap, fib15, fibr_on, profile_nodes and piv_floor lines for other dates); (c) no D8 print-rule version exists for the activity bar `tsf` (see flags).
- **RISK FLAG tsf**: 4 of 6 books (We7eba185, W68089a3e, Wf5779582, W65dc0e76) use the trade-size-filtered volume bar `tsf`, which has no spec page, no class and no run-merge bar set; see section C book text. The price bars of the other books (pnf, lbrk, dchg, kagi, frenko, urenko, swing) are unaffected by the D8 print rule (D8_BUILD_SPEC line 13).
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
| W73585da1 | Asia | pnf_7 | vwap retest M=10,tol=0.5 | fixed120/120 | 182-185 | 988, 4.6, 1078 | yes | spec only | lines spec only; no VWAP code in D8Asia.cs | - |
| We7eba185 | Asia | tsf_25_40 | fibr_pd break n=1,k=0.0 | plain60/60 | 156-185 | 675, 4.2, 944 | yes | NEW | NEW | tsf print-granularity risk |
| W68089a3e | Asia | tsf_5_400 | piv_floor break_native n=2,k=0.25 | plain60/60 | 156-185 | 573, 4.1, 942 | yes | NEW | lines exist in D8Asia.cs; trigger by parameter | tsf print-granularity risk; module+variant also in D8Asia.cs |
| W0e7037ba | Asia | lbrk_3_40 | profile_nodes retest M=3,tol=0.5 | fixed120/60 | 117-185 | 596, 5.1, 454 | yes | exists | spec exists, no code | - |
| Wf5779582 | Asia | tsf_10_60 | ob15 false_break M=3,k=0.5 | plain60/60 | 182-185 | 304, 4.4, 211 | yes | NEW | NEW | tsf print-granularity risk |
| W65dc0e76 | Asia | tsf_5_400 | fib15 break_native n=2,k=0.25 | plain60/60 | 182-185 | 663, 3.8, 1428 | NO | NEW | zigzag class exists | tsf print-granularity risk; no longer qualifies at span end |

Status words: 'exists' = specified on a page AND a class in D8Asia.cs; 'spec only' = specified on a page, no class; 'new' = no page, no class. D8Asia.cs was read only for its class list (READING; its content is not part of this order).

## C. THE BOOKS (one block each; sections 0 to 8)


### BOOK W73585da1 (Asia): pnf_7 + vwap level retest (M 10, tol 0.5), BOTH sides, bracket fixed120/120
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W73585da1 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W73585da1_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W73585da1.parquet` (13523 events: 6801 long, 6722 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `pnf_7`, module `trig_levels_vwap` (code/th_grid/trig_levels_vwap.py -> triggers_d/lv_vwap.py), variant `retest`, params {"M": 10, "tol": 0.5}, bracket `fixed120/120`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/pnf_7/trig_levels_vwap.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 988, L6M 2618, L3M 2026; t 4.6 over 1078 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored -84.24 / mine -84.24 pts, 7 / 7 trades; w183 2026-10-04 stored 430.26 / mine 430.26 pts, 7 / 7 trades; w184 2026-10-11 stored 44.65 / mine 44.65 pts, 5 / 5 trades; w185 2026-10-18 stored -199.74 / mine -199.74 pts, 7 / 7 trades

**1. BAR**
**BAR** row `pnf_7` = POINT-AND-FIGURE column bar. [SPEC] kernel th_bars/kernels.py k_pnf (lines 248-273), built by build_month.py line 135-136: box B = max(1, round(7 x s_rng)) ticks (numpy round half to even; 1 tick = 0.25 pt), 3-box reversal. State per session key: first print sets lvl = st = p, d = 0. d = 0: a print >= lvl + B starts an UP column (st = lvl, lvl += ((p-lvl)//B) x B); a print <= lvl - B starts a DOWN column (mirror). d = +1: p >= lvl + B extends (lvl += ((p-lvl)//B) x B); p <= lvl - 3B CLOSES the column: bar o = st, h = lvl, l = st, c = lvl, then a DOWN column starts with st = lvl - B and lvl = lvl - ((lvl-p)//B) x B. d = -1 mirror (bar o = st, h = st, l = lvl, c = lvl; new st = lvl + B). One bar per COMPLETED column; known time = timestamp of the confirming print (the print that moved 3 boxes against the column); the unfinished column at the session end is never a bar; there are no part=1 bars. Resets at every session boundary (02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET) and at a contract roll. [SPEC] Price-only: unaffected by the print rule (D8_BUILD_SPEC line 13; D8_PRINT_RULE). Box on the three sample days: 20261023: box_ticks=15, box_pts=3.75; 20261016: box_ticks=15, box_pts=3.75; 20261009: box_ticks=16, box_pts=4.00.
- [SPEC] Bars per Asia session in the loaded months: median 85 (min 19, max 608, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/pnf_7/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 265 stored / 265 rebuilt / 265 identical (o,h,l,c,known_ts,part); td 20261016: 139 stored / 139 rebuilt / 139 identical (o,h,l,c,known_ts,part); td 20261009: 78 stored / 78 rebuilt / 78 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec only**: pnf_7 specified in D8_BUILD_SPEC (L9c2622b0, Asia; stored Asia bars rebuilt identical in D8_ASIA_NEWBOOK_INPUTS.md) and pnf_14 in D8_NYAM_SPEC_L43f0cbfb; NO class for it in D8Asia.cs (class list read): box is a parameter, so pnf_5 / pnf_10 are parameter changes of a builder that is specified but not yet in the strategy file.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_vwap` (th_grid/triggers_d/lv_vwap.py; lines fd_levels.py lines 55-72 and 82-91). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 8 VWAP lines in this list order: VWAP0__V, RVWAP0__V, LVWAP0__V, YVWAP__V, AVPDH__V, AVPDL__V, WVWAP__V, MVWAP__V. Every VWAP = cumulative sum(typ x minute volume) / cumulative sum(volume) with typ = (h+l+c)/3 of the 1-minute bar, value at minute i uses minutes < i of the anchor period (shift by one minute, NaN on the anchor's first minute).
- VWAP0: anchored at the first minute of each label day (18:00 ET); valid when tord >= 30 and cumulative volume > 2000. RVWAP0: anchored 09:30 ET, valid 09:45-16:00 ET (tord 945..1319) and cum volume > 2000. LVWAP0: anchored 02:00 ET, valid 02:15-16:00 ET (tord 495..1319) and cum volume > 1000.
- YVWAP: the prior label day's RTH (09:30-16:00 ET) VWAP, constant for the whole next label day. AVPDH / AVPDL: VWAP anchored at the minute of the prior RTH day's high / low (the minute with the extreme h / l inside RTH), running over the whole next label day (value at i uses minutes a..i-1). WVWAP: anchored at the first minute of each ISO week (of the label date), valid when cumulative volume > 20000. MVWAP: anchored at the first minute of each calendar month, valid when cumulative volume > 20000.
- Back-adjusted then converted to raw (see store).
Variant `retest` (M=10, tol=0.5): [SPEC] retest(M, tol) (fd_common.level_events; the retest grid has no k, so k = 0): a break-up EDGE = edge(close > L); LONG if a break-up edge happened on any of the previous M bars (bars j-M..j-1) and low <= L + tol*u and close > L and close >= open; SHORT mirrored (break-down edge within M bars, high >= L - tol*u, close < L, close <= open); edge().
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: M=10, tol=0.5 -> tol*u = 2.500 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): VWAP0 0.87, RVWAP0 0.00, LVWAP0 0.00, YVWAP 1.00, AVPDH 0.99, AVPDL 0.99, WVWAP 0.90, MVWAP 0.99.
- [READING] Module status: **lines spec only; no VWAP code in D8Asia.cs**: break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits).

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `fixed120/120` = stop 120 pts / target 120 pts, fixed (no unit rule); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 120 pts / target 120 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ trades only (1-minute bars from the tape, with contract-roll back-adjustment).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: Needs the previous RTH day (YVWAP, AVPDH/L), the current ISO week and month (WVWAP/MVWAP; early in a week/month the volume gate delays validity). READING: starting a live chart cold needs the prior RTH day of 1-minute data plus the week-to-date and month-to-date minutes; the store itself runs from 2023-04-02.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 10 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (held-week grid trades, measured)**
- [SPEC] 26 grid trades in the held weeks; share of trades whose signal bar is bar 0 of the session: 0.08; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 6, 11.5, 47.75, 201.
- [SPEC] Fired line (first line in list order that fired) over those trades: VWAP0 14, AVPDL 4, AVPDH 4, YVWAP 2, WVWAP 2.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W73585da1_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610230, Asia session, grid week 185)
- bars of the session: 265, first known 2026-10-22T22:00:01.025Z, last known 2026-10-23T05:59:25.208Z; rebuilt-from-tape check 265/265/265; threshold values: box_ticks=15, box_pts=3.750
SIGNALS (raw events of the session: 71 in total, 2 shown (those inside the input windows or traded); all are in the CSV file; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
6,2026-10-22T22:04:47.027Z,1,AVPDL__V,29136.32,29146.50,5.00,Y
7,2026-10-22T22:05:30.825Z,-1,AVPDL__V,29136.32,29116.50,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
6,1,2026-10-22T22:04:48.360Z,29130.25,0.6389,29130.41,2026-10-23T05:59:59.668Z,29134.75,SessionEnd,120.0,120.0,4.34,81.97
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 13 bars before to 1 bar after each traded signal bar, 8 of 265 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-22T22:00:01.025Z,29116.50,29127.75,29116.50,29127.75,5.00,2026-10-22T20:52:01Z,2026-10-22T20:52:00Z,,VWAP0=29354.73,
1,2026-10-22T22:00:31.264Z,29124.00,29124.00,29090.25,29090.25,5.00,2026-10-22T22:00:01Z,2026-10-22T22:00:00Z,,AVPDL=29136.54,
2,2026-10-22T22:01:00.080Z,29094.00,29131.50,29094.00,29131.50,5.00,2026-10-22T22:00:31Z,2026-10-22T22:00:00Z,,AVPDL=29136.54,
3,2026-10-22T22:01:29.123Z,29127.75,29127.75,29116.50,29116.50,5.00,2026-10-22T22:01:00Z,2026-10-22T22:01:00Z,,AVPDL=29136.32,
4,2026-10-22T22:03:06.876Z,29120.25,29146.50,29120.25,29146.50,5.00,2026-10-22T22:01:29Z,2026-10-22T22:01:00Z,AVPDL=29136.32,AVPDH=29236.98,
5,2026-10-22T22:03:37.213Z,29142.75,29142.75,29127.75,29127.75,5.00,2026-10-22T22:03:06Z,2026-10-22T22:03:00Z,,AVPDL=29136.32,
6,2026-10-22T22:04:47.027Z,29131.50,29146.50,29131.50,29146.50,5.00,2026-10-22T22:03:37Z,2026-10-22T22:03:00Z,AVPDL=29136.32,AVPDH=29236.87,+1 AVPDL
7,2026-10-22T22:05:30.825Z,29142.75,29142.75,29116.50,29116.50,5.00,2026-10-22T22:04:47Z,2026-10-22T22:04:00Z,,AVPDL=29136.32,-1 AVPDL
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=6 2026-10-22T22:04:47.027Z side +1 fired AVPDL: YVWAP=29283.77; AVPDH=29236.87; AVPDL=29136.32; WVWAP=29667.54; MVWAP=30430.64
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 139, first known 2026-10-15T22:00:56.349Z, last known 2026-10-16T05:58:06.921Z; rebuilt-from-tape check 139/139/139; threshold values: box_ticks=15, box_pts=3.750
SIGNALS (raw events of the session: 14 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
30,2026-10-16T00:13:04.541Z,1,VWAP0__V,30041.08,30051.50,5.00,Y
31,2026-10-16T00:14:38.325Z,-1,VWAP0__V,30041.12,30036.50,5.00,no
32,2026-10-16T00:15:03.384Z,1,VWAP0__V,30041.11,30047.75,5.00,no
33,2026-10-16T00:18:32.147Z,-1,VWAP0__V,30041.11,30006.50,5.00,no
39,2026-10-16T00:28:26.883Z,-1,AVPDL__V,29971.63,29961.50,5.00,no
40,2026-10-16T00:30:50.081Z,1,AVPDL__V,29971.64,30002.75,5.00,no
48,2026-10-16T00:46:58.105Z,1,VWAP0__V,30027.03,30040.25,5.00,no
86,2026-10-16T03:04:20.738Z,1,AVPDH__V,30091.69,30111.50,5.00,no
91,2026-10-16T03:33:34.055Z,-1,AVPDH__V,30092.20,30085.25,5.00,no
92,2026-10-16T03:35:23.175Z,1,AVPDH__V,30092.21,30104.00,5.00,no
93,2026-10-16T03:38:11.638Z,-1,AVPDH__V,30092.22,30081.50,5.00,no
94,2026-10-16T03:40:32.620Z,1,AVPDH__V,30092.21,30104.00,5.00,no
95,2026-10-16T03:41:23.260Z,-1,AVPDH__V,30092.21,30074.00,5.00,no
96,2026-10-16T03:46:37.915Z,1,AVPDH__V,30092.22,30149.00,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
30,1,2026-10-16T00:13:06.442Z,30037.00,0.6389,30037.16,2026-10-16T03:49:45.280Z,30157.16,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 13 bars before to 1 bar after each traded signal bar, 15 of 139 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
17,2026-10-15T23:52:56.359Z,29991.50,29991.50,29984.00,29984.00,5.00,2026-10-15T23:51:20Z,2026-10-15T23:51:00Z,AVPDL=29970.96,VWAP0=30052.78,
18,2026-10-15T23:56:03.134Z,29987.75,30002.75,29987.75,30002.75,5.00,2026-10-15T23:52:56Z,2026-10-15T23:52:00Z,AVPDL=29970.96,VWAP0=30052.18,
19,2026-10-16T00:00:26.227Z,29999.00,29999.00,29980.25,29980.25,5.00,2026-10-15T23:56:03Z,2026-10-15T23:56:00Z,AVPDL=29970.99,VWAP0=30050.16,
20,2026-10-16T00:02:25.257Z,29984.00,30014.00,29984.00,30014.00,5.00,2026-10-16T00:00:26Z,2026-10-16T00:00:00Z,AVPDL=29971.00,VWAP0=30047.93,
21,2026-10-16T00:04:02.899Z,30010.25,30010.25,30002.75,30002.75,5.00,2026-10-16T00:02:25Z,2026-10-16T00:02:00Z,AVPDL=29971.08,VWAP0=30044.04,
22,2026-10-16T00:04:52.255Z,30006.50,30021.50,30006.50,30021.50,5.00,2026-10-16T00:04:02Z,2026-10-16T00:04:00Z,AVPDL=29971.12,VWAP0=30042.92,
23,2026-10-16T00:05:17.467Z,30017.75,30017.75,30010.25,30010.25,5.00,2026-10-16T00:04:52Z,2026-10-16T00:04:00Z,AVPDL=29971.12,VWAP0=30042.92,
24,2026-10-16T00:06:26.593Z,30014.00,30040.25,30014.00,30040.25,5.00,2026-10-16T00:05:17Z,2026-10-16T00:05:00Z,AVPDL=29971.15,VWAP0=30042.20,
25,2026-10-16T00:07:57.027Z,30036.50,30036.50,30021.50,30021.50,5.00,2026-10-16T00:06:26Z,2026-10-16T00:06:00Z,AVPDL=29971.18,VWAP0=30041.90,
26,2026-10-16T00:10:19.191Z,30025.25,30036.50,30025.25,30036.50,5.00,2026-10-16T00:07:57Z,2026-10-16T00:07:00Z,AVPDL=29971.22,VWAP0=30041.64,
27,2026-10-16T00:10:40.185Z,30032.75,30032.75,30021.50,30021.50,5.00,2026-10-16T00:10:19Z,2026-10-16T00:10:00Z,AVPDL=29971.27,VWAP0=30041.29,
28,2026-10-16T00:11:45.264Z,30025.25,30044.00,30025.25,30044.00,5.00,2026-10-16T00:10:40Z,2026-10-16T00:10:00Z,VWAP0=30041.29,AVPDH=30111.78,
29,2026-10-16T00:12:29.925Z,30040.25,30040.25,30032.75,30032.75,5.00,2026-10-16T00:11:45Z,2026-10-16T00:11:00Z,AVPDL=29971.30,VWAP0=30041.13,
30,2026-10-16T00:13:04.541Z,30036.50,30051.50,30036.50,30051.50,5.00,2026-10-16T00:12:29Z,2026-10-16T00:12:00Z,VWAP0=30041.08,AVPDH=30111.27,+1 VWAP0
31,2026-10-16T00:14:38.325Z,30047.75,30047.75,30036.50,30036.50,5.00,2026-10-16T00:13:04Z,2026-10-16T00:13:00Z,AVPDL=29971.36,VWAP0=30041.12,-1 VWAP0
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=30 2026-10-16T00:13:04.541Z side +1 fired VWAP0: VWAP0=30041.08; YVWAP=29921.82; AVPDH=30111.27; AVPDL=29971.32; WVWAP=30422.16; MVWAP=30846.35
```

#### td 20261009 (sess_id 202610090, Asia session, grid week 183)
- bars of the session: 78, first known 2026-10-08T22:00:08.144Z, last known 2026-10-09T05:59:18.627Z; rebuilt-from-tape check 78/78/78; threshold values: box_ticks=16, box_pts=4.000
SIGNALS (raw events of the session: 11 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
7,2026-10-08T22:39:09.814Z,1,AVPDH__V,31045.89,31072.50,5.00,Y
8,2026-10-08T23:09:45.651Z,-1,AVPDH__V,31045.93,31020.50,5.00,no
39,2026-10-09T00:57:16.521Z,1,VWAP0__V,31009.16,31024.50,5.00,no
40,2026-10-09T01:06:01.721Z,-1,VWAP0__V,31009.29,30976.50,5.00,no
45,2026-10-09T01:27:43.274Z,1,VWAP0__V,31006.62,31016.50,5.00,no
46,2026-10-09T01:34:42.923Z,-1,VWAP0__V,31006.27,30984.50,5.00,no
47,2026-10-09T01:47:41.543Z,1,VWAP0__V,31005.98,31060.50,5.00,no
63,2026-10-09T04:15:57.290Z,1,YVWAP__V,31084.65,31132.50,5.00,no
65,2026-10-09T04:37:18.046Z,1,MVWAP__V,31118.94,31136.50,5.00,no
68,2026-10-09T04:54:04.728Z,-1,MVWAP__V,31118.95,31100.50,5.00,no
69,2026-10-09T05:05:18.735Z,1,MVWAP__V,31118.95,31136.50,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
7,1,2026-10-08T22:39:11.101Z,31060.00,0.6389,31060.16,2026-10-09T05:59:57.199Z,31158.00,SessionEnd,120.0,120.0,97.84,1951.97
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 13 bars before to 1 bar after each traded signal bar, 9 of 78 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-08T22:00:08.144Z,31020.50,31020.50,31016.50,31016.50,5.00,2026-10-08T20:53:32Z,2026-10-08T20:53:00Z,,MVWAP=31120.16,
1,2026-10-08T22:01:11.232Z,31020.50,31028.50,31020.50,31028.50,5.00,2026-10-08T22:00:08Z,2026-10-08T22:00:00Z,AVPDL=30930.25,AVPDH=31046.03,
2,2026-10-08T22:04:15.371Z,31024.50,31024.50,30996.50,30996.50,5.00,2026-10-08T22:01:11Z,2026-10-08T22:01:00Z,AVPDL=30930.50,AVPDH=31046.01,
3,2026-10-08T22:10:52.950Z,31000.50,31032.50,31000.50,31032.50,5.00,2026-10-08T22:04:15Z,2026-10-08T22:04:00Z,AVPDL=30930.79,AVPDH=31045.95,
4,2026-10-08T22:14:00.573Z,31028.50,31028.50,31020.50,31020.50,5.00,2026-10-08T22:10:52Z,2026-10-08T22:10:00Z,AVPDL=30931.17,AVPDH=31045.91,
5,2026-10-08T22:23:53.253Z,31024.50,31052.50,31024.50,31052.50,5.00,2026-10-08T22:14:00Z,2026-10-08T22:14:00Z,AVPDH=31045.89,YVWAP=31084.65,
6,2026-10-08T22:27:18.442Z,31048.50,31048.50,31040.50,31040.50,5.00,2026-10-08T22:23:53Z,2026-10-08T22:23:00Z,AVPDL=30932.01,AVPDH=31045.89,
7,2026-10-08T22:39:09.814Z,31044.50,31072.50,31044.50,31072.50,5.00,2026-10-08T22:27:18Z,2026-10-08T22:27:00Z,AVPDH=31045.89,YVWAP=31084.65,+1 AVPDH
8,2026-10-08T23:09:45.651Z,31068.50,31068.50,31020.50,31020.50,5.00,2026-10-08T22:39:09Z,2026-10-08T22:39:00Z,AVPDL=30933.13,VWAP0=31036.86,-1 AVPDH
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=7 2026-10-08T22:39:09.814Z side +1 fired AVPDH: YVWAP=31084.65; AVPDH=31045.89; AVPDL=30932.21; WVWAP=31269.34; MVWAP=31120.02
```

### BOOK We7eba185 (Asia): tsf_25_40 + fibr pd level break (n 1, k 0.0), BOTH sides, bracket plain60/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 30 of 30 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id We7eba185 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_We7eba185_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/We7eba185.parquet` (1428 events: 729 long, 699 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `tsf_25_40`, module `trig_levels_fibr_pd` (code/th_grid/trig_levels_fibr_pd.py -> triggers_d/lv_fibr_pd.py), variant `break`, params {"n": 1, "k": 0.0}, bracket `plain60/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/tsf_25_40/trig_levels_fibr_pd.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 675, L6M 1186, L3M 612; t 4.2 over 944 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 156..185 (2026-03-29 to 2026-10-24) = 30 held week(s); months in the cell file: 202603, 202604, 202605, 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored 145.56 / mine 145.56 pts, 4 / 4 trades; w182 2026-09-27 stored 138.49 / mine 138.49 pts, 15 / 15 trades; w183 2026-10-04 stored 72.75 / mine 72.75 pts, 6 / 6 trades; w184 2026-10-11 stored 17.03 / mine 17.03 pts, 10 / 10 trades; w185 2026-10-18 stored -17.88 / mine -17.88 pts, 14 / 14 trades (last 5 of 30 held weeks shown; 30 of 30 equal)

**1. BAR**
**BAR** row `tsf_25_40` = TRADE-SIZE-FILTERED VOLUME bar (L = 25, N = 40). [SPEC] build_month.py lines 97-100 with kernel k_cum (kernels.py lines 11-33), mode 0: metric = print size if size >= 25 else 0; threshold thr = 40 x s_vol contracts (s_vol = abs_vol / r0_vol, fixed for the session). Per session key a bar opens at the first print; EVERY print updates o/h/l/c, volume, count (all prints, not only the counted ones; the registry text in th_bars/spec.py says 'OHLC uses only counted prints' but the code does not do that: code governs); cum += metric; the bar CLOSES at the print for which cum >= thr (the closing print stays in the bar, no split); known time = that print's timestamp; the last bar of the session is emitted with part = 1 (known at its last print) and is never a signal bar. Threshold on the sample days: 20261023: L=25, thr_contracts=39.87, s_vol=1.00; 20261016: L=25, thr_contracts=34.83, s_vol=0.87; 20261008: L=25, thr_contracts=34.28, s_vol=0.86. [SPEC] This row is an ACTIVITY (volume-accumulating) bar and the old-engine tape treats every MBO trade record as one print; D8_PRINT_RULE.md section 2 shows that volume-accumulating bars (vol, vsess, tick, dlt, cdr, dib ...) are DIFFERENT between contract level, run merge and the old engine bars (2% to 28% identical for volume-type bars). tsf is NOT in that proof table and has no run-merge version in /mnt/l2/l2vast/_d8spec/bars_c or bars_r. [READING] Because the filter acts on the SIZE of one print (record size >= L lots), merging records of the same price and side into one print (the D8 rule) changes which prints pass the filter and therefore every bar boundary: the grid result for this book is NOT proven for the D8 print stream, and a live bar builder cannot be matched without deciding the print granularity. RISK FLAG.
- [SPEC] Bars per Asia session in the loaded months: median 7 (min 1, max 35, 287 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/tsf_25_40/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 18 stored / 18 rebuilt / 18 identical (o,h,l,c,known_ts,part); td 20261016: 4 stored / 4 rebuilt / 4 identical (o,h,l,c,known_ts,part); td 20261008: 11 stored / 11 rebuilt / 11 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **NEW**: no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_fibr_pd` (th_grid/triggers_d/lv_fibr_pd.py; lines fd_levels2.py lines 131-146). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 18 lines FIBR_PD_*. H, L = PD_RTH__H, PD_RTH__L (prior label day's RTH high/low, 09:30-16:00 ET), constant over the label day.
- Range fibs (fd_levels2.py range_fib, lines 131-137): with range R = H - L (NaN unless R >= 8 points): DNxxx = H - r R and UPxxx = L + r R for r = 0.236, 0.382, 0.5, 0.618, 0.65, 0.786 (names DN236 DN382 DN500 DN618 DN650 DN786 UP236 .. UP786); XUxxxx = H + (e-1) R for e = 1.272, 1.618, 2.0 (XU1272 XU1618 XU2000); XDxxxx = L - (e-1) R (XD1272 XD1618 XD2000). List order: DN236 DN382 DN500 DN618 DN650 DN786 UP236 UP382 UP500 UP618 UP650 UP786 XU1272 XU1618 XU2000 XD1272 XD1618 XD2000 (18 lines).
Variant `break` (n=1, k=0.0): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: n=1, k=0.0 -> k*u = 0.000 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 287 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): FIBR_PD_DN236 1.00, FIBR_PD_DN382 1.00, FIBR_PD_DN500 1.00, FIBR_PD_DN618 1.00, FIBR_PD_DN650 1.00, FIBR_PD_DN786 1.00, FIBR_PD_UP236 1.00, FIBR_PD_UP382 1.00, FIBR_PD_UP500 1.00, FIBR_PD_UP618 1.00, FIBR_PD_UP650 1.00, FIBR_PD_UP786 1.00, FIBR_PD_XU1272 1.00, FIBR_PD_XU1618 1.00, FIBR_PD_XU2000 1.00, FIBR_PD_XD1272 1.00, FIBR_PD_XD1618 1.00, FIBR_PD_XD2000 1.00.
- [READING] Module status: **NEW**: no spec; the fibr_on range-fib text (D8_NYAM_SPEC_L43f0cbfb) is the same construction on the overnight range.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `plain60/60` = stop 60 pts / target 60 pts, fixed (no unit rule); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `vol (activity bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 60 pts / target 60 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: One prior RTH day of 1-minute data.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; tsf thresholds use s_vol.

**7. WHAT ACTUALLY TRADES (held-week grid trades, measured)**
- [SPEC] 276 grid trades in the held weeks; share of trades whose signal bar is bar 0 of the session: 0.24; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 1, 2, 6, 24.
- [SPEC] Fired line (first line in list order that fired) over those trades: FIBR_PD_DN236 52, FIBR_PD_DN382 34, FIBR_PD_DN786 33, FIBR_PD_XU1272 30, FIBR_PD_DN500 29, FIBR_PD_XD1272 28, FIBR_PD_DN618 20, FIBR_PD_XU1618 15, FIBR_PD_XD1618 11, FIBR_PD_DN650 9, FIBR_PD_XD2000 4, FIBR_PD_XU2000 3.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/We7eba185_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610230, Asia session, grid week 185)
- bars of the session: 18, first known 2026-10-22T22:00:15.892Z, last known 2026-10-23T05:59:59.668Z; rebuilt-from-tape check 18/18/18; threshold values: L=25, thr_contracts=39.866, s_vol=0.997
SIGNALS (raw events of the session: 7 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
1,2026-10-22T22:25:07.557Z,1,FIBR_PD_DN786,29153.21,29160.00,5.00,Y
2,2026-10-23T00:49:07.781Z,1,FIBR_PD_UP236,29165.57,29182.50,5.00,Y
5,2026-10-23T02:23:40.212Z,-1,FIBR_PD_DN786,29153.21,29149.75,5.00,Y
9,2026-10-23T03:32:01.600Z,1,FIBR_PD_DN786,29153.21,29171.75,5.00,no
12,2026-10-23T04:55:03.185Z,-1,FIBR_PD_DN786,29153.21,29134.00,5.00,no
15,2026-10-23T05:38:45.195Z,1,FIBR_PD_DN786,29153.21,29159.25,5.00,no
16,2026-10-23T05:59:31.923Z,-1,FIBR_PD_DN786,29153.21,29138.00,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
1,1,2026-10-22T22:25:08.637Z,29157.75,0.4398,29157.86,2026-10-22T23:01:08.688Z,29097.50,Stop,60.0,60.0,-60.36,-1212.04
2,1,2026-10-23T00:49:08.997Z,29183.00,0.4398,29183.11,2026-10-23T01:11:40.924Z,29122.50,Stop,60.0,60.0,-60.61,-1217.04
5,-1,2026-10-23T02:23:41.782Z,29150.50,0.4398,29150.39,2026-10-23T05:59:59.668Z,29135.25,SessionEnd,60.0,60.0,15.14,297.96
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (all 18 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-22T22:00:15.892Z,29116.50,29128.00,29090.75,29093.25,5.00,2026-10-22T20:59:58Z,2026-10-22T20:59:00Z,,FIBR_PD_XD2000=29429.00,
1,2026-10-22T22:25:07.557Z,29093.00,29165.75,29090.00,29160.00,5.00,2026-10-22T22:00:15Z,2026-10-22T22:00:00Z,FIBR_PD_DN786=29153.21,FIBR_PD_UP236=29165.57,+1 FIBR_PD_DN786
2,2026-10-23T00:49:07.781Z,29160.00,29187.75,29022.75,29182.50,5.00,2026-10-22T22:25:07Z,2026-10-22T22:25:00Z,FIBR_PD_UP236=29165.57,FIBR_PD_DN650=29229.61,+1 FIBR_PD_UP236
3,2026-10-23T01:43:36.278Z,29182.75,29204.00,29056.75,29199.25,5.00,2026-10-23T00:49:07Z,2026-10-23T00:49:00Z,FIBR_PD_UP236=29165.57,FIBR_PD_DN650=29229.61,
4,2026-10-23T01:47:14.561Z,29199.25,29212.50,29188.00,29206.50,5.00,2026-10-23T01:43:36Z,2026-10-23T01:43:00Z,FIBR_PD_UP236=29165.57,FIBR_PD_DN650=29229.61,
5,2026-10-23T02:23:40.212Z,29206.00,29211.75,29089.00,29149.75,5.00,2026-10-23T01:47:14Z,2026-10-23T01:47:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,-1 FIBR_PD_DN786
6,2026-10-23T02:24:55.103Z,29149.50,29166.25,29145.75,29151.50,5.00,2026-10-23T02:23:40Z,2026-10-23T02:23:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,
7,2026-10-23T02:25:20.834Z,29151.75,29154.50,29146.75,29148.75,5.00,2026-10-23T02:24:55Z,2026-10-23T02:24:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,
8,2026-10-23T02:28:16.405Z,29148.25,29160.00,29138.25,29151.50,5.00,2026-10-23T02:25:20Z,2026-10-23T02:25:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,
9,2026-10-23T03:32:01.600Z,29151.75,29204.00,29134.00,29171.75,5.00,2026-10-23T02:28:16Z,2026-10-23T02:28:00Z,FIBR_PD_UP236=29165.57,FIBR_PD_DN650=29229.61,+1 FIBR_PD_DN786
10,2026-10-23T03:32:14.210Z,29171.25,29174.25,29163.50,29170.00,5.00,2026-10-23T03:32:01Z,2026-10-23T03:32:00Z,FIBR_PD_UP236=29165.57,FIBR_PD_DN650=29229.61,
11,2026-10-23T04:31:35.919Z,29169.50,29195.50,29138.50,29173.00,5.00,2026-10-23T03:32:14Z,2026-10-23T03:32:00Z,FIBR_PD_UP236=29165.57,FIBR_PD_DN650=29229.61,
12,2026-10-23T04:55:03.185Z,29173.25,29177.00,29118.25,29134.00,5.00,2026-10-23T04:31:35Z,2026-10-23T04:31:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,-1 FIBR_PD_DN786
13,2026-10-23T05:26:22.576Z,29134.00,29154.75,29117.50,29125.00,5.00,2026-10-23T04:55:03Z,2026-10-23T04:55:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,
14,2026-10-23T05:33:25.958Z,29124.75,29151.75,29105.50,29140.00,5.00,2026-10-23T05:26:22Z,2026-10-23T05:26:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,
15,2026-10-23T05:38:45.195Z,29139.50,29163.25,29123.50,29159.25,5.00,2026-10-23T05:33:25Z,2026-10-23T05:33:00Z,FIBR_PD_DN786=29153.21,FIBR_PD_UP236=29165.57,+1 FIBR_PD_DN786
16,2026-10-23T05:59:31.923Z,29158.50,29188.25,29131.25,29138.00,5.00,2026-10-23T05:38:45Z,2026-10-23T05:38:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,-1 FIBR_PD_DN786
17,2026-10-23T05:59:59.668Z,29138.25,29138.25,29134.25,29135.00,5.00,2026-10-23T05:59:31Z,2026-10-23T05:59:00Z,FIBR_PD_XD1272=28880.20,FIBR_PD_DN786=29153.21,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=1 2026-10-22T22:25:07.557Z side +1 fired FIBR_PD_DN786: FIBR_PD_DN236=29462.18; FIBR_PD_DN382=29380.16; FIBR_PD_DN500=29313.88; FIBR_PD_DN618=29247.59; FIBR_PD_DN650=29229.61; FIBR_PD_DN786=29153.21; FIBR_PD_UP236=29165.57; FIBR_PD_UP382=29247.59; FIBR_PD_UP500=29313.88; FIBR_PD_UP618=29380.16; FIBR_PD_UP650=29398.14; FIBR_PD_UP786=29474.54; FIBR_PD_XU1272=29747.55; FIBR_PD_XU1618=29941.91; FIBR_PD_XU2000=30156.50; FIBR_PD_XD1272=28880.20; FIBR_PD_XD1618=28685.84; FIBR_PD_XD2000=28471.25
k=2 2026-10-23T00:49:07.781Z side +1 fired FIBR_PD_UP236: FIBR_PD_DN236=29462.18; FIBR_PD_DN382=29380.16; FIBR_PD_DN500=29313.88; FIBR_PD_DN618=29247.59; FIBR_PD_DN650=29229.61; FIBR_PD_DN786=29153.21; FIBR_PD_UP236=29165.57; FIBR_PD_UP382=29247.59; FIBR_PD_UP500=29313.88; FIBR_PD_UP618=29380.16; FIBR_PD_UP650=29398.14; FIBR_PD_UP786=29474.54; FIBR_PD_XU1272=29747.55; FIBR_PD_XU1618=29941.91; FIBR_PD_XU2000=30156.50; FIBR_PD_XD1272=28880.20; FIBR_PD_XD1618=28685.84; FIBR_PD_XD2000=28471.25
k=5 2026-10-23T02:23:40.212Z side -1 fired FIBR_PD_DN786: FIBR_PD_DN236=29462.18; FIBR_PD_DN382=29380.16; FIBR_PD_DN500=29313.88; FIBR_PD_DN618=29247.59; FIBR_PD_DN650=29229.61; FIBR_PD_DN786=29153.21; FIBR_PD_UP236=29165.57; FIBR_PD_UP382=29247.59; FIBR_PD_UP500=29313.88; FIBR_PD_UP618=29380.16; FIBR_PD_UP650=29398.14; FIBR_PD_UP786=29474.54; FIBR_PD_XU1272=29747.55; FIBR_PD_XU1618=29941.91; FIBR_PD_XU2000=30156.50; FIBR_PD_XD1272=28880.20; FIBR_PD_XD1618=28685.84; FIBR_PD_XD2000=28471.25
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 4, first known 2026-10-15T23:07:36.490Z, last known 2026-10-16T05:59:58.154Z; rebuilt-from-tape check 4/4/4; threshold values: L=25, thr_contracts=34.827, s_vol=0.871
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
1,2026-10-16T01:55:28.884Z,1,FIBR_PD_DN236,30061.23,30067.00,5.00,Y
2,2026-10-16T02:27:30.569Z,1,FIBR_PD_UP786,30073.86,30114.00,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
1,1,2026-10-16T01:55:31.728Z,30069.00,0.4398,30069.11,2026-10-16T02:36:47.750Z,30129.11,Target,60.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 4 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-15T23:07:36.490Z,30089.00,30128.00,30027.50,30046.75,5.00,2026-10-15T20:59:59Z,2026-10-15T20:59:00Z,FIBR_PD_XD1272=29919.49,FIBR_PD_DN786=30202.71,
1,2026-10-16T01:55:28.884Z,30047.00,30091.75,29959.25,30067.00,5.00,2026-10-15T23:07:36Z,2026-10-15T23:07:00Z,FIBR_PD_DN236=30061.23,FIBR_PD_UP786=30073.86,+1 FIBR_PD_DN236
2,2026-10-16T02:27:30.569Z,30067.00,30114.75,30043.25,30114.00,5.00,2026-10-16T01:55:28Z,2026-10-16T01:55:00Z,FIBR_PD_UP786=30073.86,FIBR_PD_XU1272=30352.95,+1 FIBR_PD_UP786
3,2026-10-16T05:59:58.154Z,30114.25,30225.00,30074.00,30191.25,5.00,2026-10-16T02:27:30Z,2026-10-16T02:27:00Z,FIBR_PD_UP786=30073.86,FIBR_PD_XU1272=30352.95,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=1 2026-10-16T01:55:28.884Z side +1 fired FIBR_PD_DN236: FIBR_PD_DN236=30061.23; FIBR_PD_DN382=29977.39; FIBR_PD_DN500=29909.62; FIBR_PD_DN618=29841.86; FIBR_PD_DN650=29823.49; FIBR_PD_DN786=29745.39; FIBR_PD_UP236=29758.02; FIBR_PD_UP382=29841.86; FIBR_PD_UP500=29909.62; FIBR_PD_UP618=29977.39; FIBR_PD_UP650=29995.76; FIBR_PD_UP786=30073.86; FIBR_PD_XU1272=30352.95; FIBR_PD_XU1618=30551.64; FIBR_PD_XU2000=30771.00; FIBR_PD_XD1272=29466.30; FIBR_PD_XD1618=29267.61; FIBR_PD_XD2000=29048.25
```

#### td 20261008 (sess_id 202610080, Asia session, grid week 183)
- bars of the session: 11, first known 2026-10-07T22:00:36.852Z, last known 2026-10-08T05:59:59.026Z; rebuilt-from-tape check 11/11/11; threshold values: L=25, thr_contracts=34.285, s_vol=0.857
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
0,2026-10-07T22:00:36.852Z,1,FIBR_PD_XD1272,31414.57,31419.25,5.00,Y
9,2026-10-08T04:00:18.887Z,-1,FIBR_PD_DN236,31356.35,31354.75,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,1,2026-10-07T22:00:38.295Z,31419.50,0.4398,31419.61,2026-10-08T03:54:22.744Z,31359.25,Stop,60.0,60.0,-60.36,-1212.04
9,-1,2026-10-08T04:00:20.638Z,31355.25,0.4398,31355.14,2026-10-08T05:59:59.026Z,31325.25,SessionEnd,60.0,60.0,29.89,592.96
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (all 11 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-07T22:00:36.852Z,31403.00,31419.25,31403.00,31419.25,5.00,2026-10-07T20:59:58Z,2026-10-07T20:59:00Z,FIBR_PD_XD1272=31414.57,FIBR_PD_DN786=31491.72,+1 FIBR_PD_XD1272
1,2026-10-08T00:41:43.288Z,31419.75,31459.00,31382.25,31385.50,5.00,2026-10-07T22:00:36Z,2026-10-07T22:00:00Z,FIBR_PD_UP786=31362.49,FIBR_PD_XU1272=31498.21,
2,2026-10-08T00:44:03.103Z,31385.25,31387.75,31377.50,31382.00,5.00,2026-10-08T00:41:43Z,2026-10-08T00:41:00Z,FIBR_PD_UP786=31362.49,FIBR_PD_XU1272=31498.21,
3,2026-10-08T00:47:06.726Z,31382.25,31384.00,31372.25,31382.25,5.00,2026-10-08T00:44:03Z,2026-10-08T00:44:00Z,FIBR_PD_UP786=31362.49,FIBR_PD_XU1272=31498.21,
4,2026-10-08T01:38:08.496Z,31382.50,31446.50,31375.75,31442.50,5.00,2026-10-08T00:47:06Z,2026-10-08T00:47:00Z,FIBR_PD_UP786=31362.49,FIBR_PD_XU1272=31498.21,
5,2026-10-08T01:45:55.770Z,31442.00,31448.75,31435.00,31435.00,5.00,2026-10-08T01:38:08Z,2026-10-08T01:38:00Z,FIBR_PD_UP786=31362.49,FIBR_PD_XU1272=31498.21,
6,2026-10-08T03:00:40.221Z,31435.00,31466.00,31406.50,31420.50,5.00,2026-10-08T01:45:55Z,2026-10-08T01:45:00Z,FIBR_PD_UP786=31362.49,FIBR_PD_XU1272=31498.21,
7,2026-10-08T03:43:44.411Z,31420.75,31421.50,31375.50,31380.00,5.00,2026-10-08T03:00:40Z,2026-10-08T03:00:00Z,FIBR_PD_UP786=31362.49,FIBR_PD_XU1272=31498.21,
8,2026-10-08T03:47:26.720Z,31380.00,31387.75,31377.25,31385.50,5.00,2026-10-08T03:43:44Z,2026-10-08T03:43:00Z,FIBR_PD_UP786=31362.49,FIBR_PD_XU1272=31498.21,
9,2026-10-08T04:00:18.887Z,31386.00,31393.75,31349.50,31354.75,5.00,2026-10-08T03:47:26Z,2026-10-08T03:47:00Z,FIBR_PD_UP650=31324.51,FIBR_PD_DN236=31356.35,-1 FIBR_PD_DN236
10,2026-10-08T05:59:59.026Z,31354.75,31411.25,31321.00,31325.00,5.00,2026-10-08T04:00:18Z,2026-10-08T04:00:00Z,FIBR_PD_UP650=31324.51,FIBR_PD_DN236=31356.35,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-07T22:00:36.852Z side +1 fired FIBR_PD_XD1272: FIBR_PD_DN236=31579.04; FIBR_PD_DN382=31555.86; FIBR_PD_DN500=31537.12; FIBR_PD_DN618=31518.39; FIBR_PD_DN650=31513.31; FIBR_PD_DN786=31491.72; FIBR_PD_UP236=31495.21; FIBR_PD_UP382=31518.39; FIBR_PD_UP500=31537.12; FIBR_PD_UP618=31555.86; FIBR_PD_UP650=31560.94; FIBR_PD_UP786=31582.53; FIBR_PD_XU1272=31659.68; FIBR_PD_XU1618=31714.61; FIBR_PD_XU2000=31775.25; FIBR_PD_XD1272=31414.57; FIBR_PD_XD1618=31359.64; FIBR_PD_XD2000=31299.00
k=9 2026-10-08T04:00:18.887Z side -1 fired FIBR_PD_DN236: FIBR_PD_DN236=31356.35; FIBR_PD_DN382=31315.58; FIBR_PD_DN500=31282.62; FIBR_PD_DN618=31249.67; FIBR_PD_DN650=31240.74; FIBR_PD_DN786=31202.76; FIBR_PD_UP236=31208.90; FIBR_PD_UP382=31249.67; FIBR_PD_UP500=31282.62; FIBR_PD_UP618=31315.58; FIBR_PD_UP650=31324.51; FIBR_PD_UP786=31362.49; FIBR_PD_XU1272=31498.21; FIBR_PD_XU1618=31594.83; FIBR_PD_XU2000=31701.50; FIBR_PD_XD1272=31067.04; FIBR_PD_XD1618=30970.42; FIBR_PD_XD2000=30863.75
```

### BOOK W68089a3e (Asia): tsf_5_400 + piv floor level break native (n 2, k 0.25), BOTH sides, bracket plain60/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 30 of 30 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W68089a3e (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W68089a3e_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W68089a3e.parquet` (1285 events: 669 long, 616 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `tsf_5_400`, module `trig_levels_piv_floor` (code/th_grid/trig_levels_piv_floor.py -> triggers_d/lv_piv_floor.py), variant `break_native`, params {"n": 2, "k": 0.25}, bracket `plain60/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/tsf_5_400/trig_levels_piv_floor.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 573, L6M 664, L3M 473; t 4.1 over 942 trades; mark: module+variant also in D8Asia.cs (relay confirms the book).
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 156..185 (2026-03-29 to 2026-10-24) = 30 held week(s); months in the cell file: 202603, 202604, 202605, 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored 71.06 / mine 71.06 pts, 4 / 4 trades; w182 2026-09-27 stored 50.07 / mine 50.07 pts, 11 / 11 trades; w183 2026-10-04 stored 53.15 / mine 53.15 pts, 8 / 8 trades; w184 2026-10-11 stored 18.82 / mine 18.82 pts, 11 / 11 trades; w185 2026-10-18 stored -65.32 / mine -65.32 pts, 11 / 11 trades (last 5 of 30 held weeks shown; 30 of 30 equal)

**1. BAR**
**BAR** row `tsf_5_400` = TRADE-SIZE-FILTERED VOLUME bar (L = 5, N = 400). [SPEC] build_month.py lines 97-100 with kernel k_cum (kernels.py lines 11-33), mode 0: metric = print size if size >= 5 else 0; threshold thr = 400 x s_vol contracts (s_vol = abs_vol / r0_vol, fixed for the session). Per session key a bar opens at the first print; EVERY print updates o/h/l/c, volume, count (all prints, not only the counted ones; the registry text in th_bars/spec.py says 'OHLC uses only counted prints' but the code does not do that: code governs); cum += metric; the bar CLOSES at the print for which cum >= thr (the closing print stays in the bar, no split); known time = that print's timestamp; the last bar of the session is emitted with part = 1 (known at its last print) and is never a signal bar. Threshold on the sample days: 20261023: L=5, thr_contracts=398.66, s_vol=1.00; 20261016: L=5, thr_contracts=348.27, s_vol=0.87; 20261009: L=5, thr_contracts=342.85, s_vol=0.86. [SPEC] This row is an ACTIVITY (volume-accumulating) bar and the old-engine tape treats every MBO trade record as one print; D8_PRINT_RULE.md section 2 shows that volume-accumulating bars (vol, vsess, tick, dlt, cdr, dib ...) are DIFFERENT between contract level, run merge and the old engine bars (2% to 28% identical for volume-type bars). tsf is NOT in that proof table and has no run-merge version in /mnt/l2/l2vast/_d8spec/bars_c or bars_r. [READING] Because the filter acts on the SIZE of one print (record size >= L lots), merging records of the same price and side into one print (the D8 rule) changes which prints pass the filter and therefore every bar boundary: the grid result for this book is NOT proven for the D8 print stream, and a live bar builder cannot be matched without deciding the print granularity. RISK FLAG.
- [SPEC] Bars per Asia session in the loaded months: median 8 (min 2, max 27, 287 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/tsf_5_400/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 10 stored / 10 rebuilt / 10 identical (o,h,l,c,known_ts,part); td 20261016: 7 stored / 7 rebuilt / 7 identical (o,h,l,c,known_ts,part); td 20261009: 9 stored / 9 rebuilt / 9 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **NEW**: no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_piv_floor` (th_grid/triggers_d/lv_piv_floor.py; lines fd_levels2.py lines 148-167). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 16 lines in this list order: PIV_D_P, PIV_D_R1, PIV_D_R2, PIV_D_R3, PIV_D_S1, PIV_D_S2, PIV_D_S3, PIV_W_P, PIV_W_R1, PIV_W_R2, PIV_W_R3, PIV_W_S1, PIV_W_S2, PIV_W_S3, CPR_TC, CPR_BC.
- Daily: from the prior RTH day high H, low L and close C (PD_RTH__H, PD_RTH__L, PD_C__C): P = (H+L+C)/3; R1 = 2P - L; S1 = 2P - H; R2 = P + (H-L); S2 = P - (H-L); R3 = H + 2(P - L); S3 = L - 2(H - P). Constant over the label day.
- Weekly: the same formulas from the previous ISO week's high / low / last 1-minute close (all minutes of that week, label-date weeks), constant over the next ISO week.
- CPR_BC = (H+L)/2, CPR_TC = 2P - BC from the prior RTH day.
- Raw price = adj - off.
Variant `break_native` (n=2, k=0.25): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (native) = rolling median of (high - low) over the previous 100 bars of THIS book's bar series (bars j-100..j-1, shifted one bar, min_periods 20, floor 0.5 pt; NaN before 20 bars) (fd_common.unit); every tolerance below is x u. With these parameters: n=2, k=0.25 -> k*u = 0.25 x u.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 287 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PIV_D_P 0.97, PIV_D_R1 0.97, PIV_D_R2 0.97, PIV_D_R3 0.97, PIV_D_S1 0.97, PIV_D_S2 0.97, PIV_D_S3 0.97, PIV_W_P 1.00, PIV_W_R1 1.00, PIV_W_R2 1.00, PIV_W_R3 1.00, PIV_W_S1 1.00, PIV_W_S2 1.00, PIV_W_S3 1.00, CPR_TC 0.97, CPR_BC 1.00.
- [READING] Module status: **lines exist in D8Asia.cs; trigger by parameter**: pivot lines (Piv()) and LevelBreakNative (break_native n=2, k) exist for L6b373671; plain break n=1, k=0 and the 16-line set incl. weekly and CPR need checking against pivLines.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `plain60/60` = stop 60 pts / target 60 pts, fixed (no unit rule); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `vol (activity bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 60 pts / target 60 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: Prior RTH day and prior ISO week of 1-minute data (the live class Piv() in D8Asia.cs skips the first loaded week).
- [SPEC] Warm-up of the trigger: native u needs 20 earlier bars of the continuous series (rolling 100, shifted). Memory M / hold n of the variant: 2 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; tsf thresholds use s_vol.

**7. WHAT ACTUALLY TRADES (held-week grid trades, measured)**
- [SPEC] 264 grid trades in the held weeks; share of trades whose signal bar is bar 0 of the session: 0.03; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 2, 4, 7, 17.
- [SPEC] Fired line (first line in list order that fired) over those trades: PIV_D_P 84, CPR_TC 48, PIV_D_S1 34, PIV_D_R1 28, CPR_BC 19, PIV_W_P 18, PIV_D_R2 12, PIV_W_R1 7, PIV_D_S2 4, PIV_W_S1 3, PIV_D_R3 2, PIV_W_S2 2.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W68089a3e_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610230, Asia session, grid week 185)
- bars of the session: 10, first known 2026-10-22T22:17:47.443Z, last known 2026-10-23T05:59:59.668Z; rebuilt-from-tape check 10/10/10; threshold values: L=5, thr_contracts=398.663, s_vol=0.997
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
8,2026-10-23T05:34:53.780Z,-1,CPR_TC,29201.29,29136.75,34.25,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
8,-1,2026-10-23T05:34:54.846Z,29124.00,0.4398,29123.89,2026-10-23T05:43:42.055Z,29184.25,Stop,60.0,60.0,-60.36,-1212.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 10 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-22T22:17:47.443Z,29116.50,29149.25,29090.00,29125.00,33.88,2026-10-22T20:59:58Z,2026-10-22T20:59:00Z,PIV_W_S1=28676.92,PIV_D_S3=29466.17,
1,2026-10-22T23:33:00.148Z,29125.00,29165.75,29060.00,29060.00,34.25,2026-10-22T22:17:47Z,2026-10-22T22:17:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,
2,2026-10-23T00:42:47.982Z,29059.50,29142.00,29022.75,29142.00,34.25,2026-10-22T23:33:00Z,2026-10-22T23:33:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,
3,2026-10-23T01:12:29.405Z,29141.50,29198.50,29114.00,29120.00,34.25,2026-10-23T00:42:47Z,2026-10-23T00:42:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,
4,2026-10-23T01:43:36.279Z,29120.25,29204.00,29056.75,29199.25,34.25,2026-10-23T01:12:29Z,2026-10-23T01:12:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,
5,2026-10-23T02:07:54.698Z,29198.75,29212.50,29089.00,29117.25,34.25,2026-10-23T01:43:36Z,2026-10-23T01:43:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,
6,2026-10-23T02:36:58.765Z,29117.00,29203.75,29106.50,29199.75,34.25,2026-10-23T02:07:54Z,2026-10-23T02:07:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,
7,2026-10-23T04:31:35.919Z,29199.75,29204.00,29134.00,29173.00,34.25,2026-10-23T02:36:58Z,2026-10-23T02:36:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,
8,2026-10-23T05:34:53.780Z,29173.25,29177.00,29105.50,29136.75,34.25,2026-10-23T04:31:35Z,2026-10-23T04:31:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,-1 CPR_TC
9,2026-10-23T05:59:59.668Z,29136.75,29188.25,29123.50,29135.00,34.25,2026-10-23T05:34:53Z,2026-10-23T05:34:00Z,PIV_D_S1=28920.42,CPR_TC=29201.29,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=8 2026-10-23T05:34:53.780Z side -1 fired CPR_TC: PIV_D_P=29257.58; PIV_D_R1=29482.17; PIV_D_R2=29819.33; PIV_D_R3=30043.92; PIV_D_S1=28920.42; PIV_D_S2=28695.83; PIV_D_S3=28358.67; PIV_W_P=29983.08; PIV_W_R1=30697.42; PIV_W_R2=32003.58; PIV_W_R3=32717.92; PIV_W_S1=28676.92; PIV_W_S2=27962.58; PIV_W_S3=26656.42; CPR_TC=29201.29; CPR_BC=29313.88
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 7, first known 2026-10-15T23:07:02.367Z, last known 2026-10-16T05:59:58.154Z; rebuilt-from-tape check 7/7/7; threshold values: L=5, thr_contracts=348.266, s_vol=0.871
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
1,2026-10-15T23:36:18.600Z,-1,CPR_TC,30063.38,30000.00,31.25,Y
4,2026-10-16T03:50:17.816Z,1,PIV_D_P,29986.50,30179.00,31.25,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
1,-1,2026-10-15T23:36:20.110Z,30000.50,0.4398,30000.39,2026-10-16T00:51:45.477Z,30060.75,Stop,60.0,60.0,-60.36,-1212.04
4,1,2026-10-16T03:50:18.939Z,30176.25,0.4398,30176.36,2026-10-16T05:59:58.154Z,30191.00,SessionEnd,60.0,60.0,14.64,287.96
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (all 7 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-15T23:07:02.367Z,30089.00,30128.00,30027.50,30035.00,31.25,2026-10-15T20:59:59Z,2026-10-15T20:59:00Z,PIV_D_S1=29955.08,CPR_TC=30246.46,
1,2026-10-15T23:36:18.600Z,30035.25,30064.00,30000.00,30000.00,31.25,2026-10-15T23:07:02Z,2026-10-15T23:07:00Z,PIV_D_P=29986.50,CPR_TC=30063.38,-1 CPR_TC
2,2026-10-16T00:27:58.158Z,29999.50,30052.50,29962.00,29962.25,31.25,2026-10-15T23:36:18Z,2026-10-15T23:36:00Z,PIV_W_S3=29913.50,PIV_D_P=29986.50,
3,2026-10-16T02:24:37.724Z,29962.00,30103.00,29959.25,30103.00,31.25,2026-10-16T00:27:58Z,2026-10-16T00:27:00Z,CPR_TC=30063.38,PIV_D_R1=30350.50,
4,2026-10-16T03:50:17.816Z,30102.75,30179.00,30074.00,30179.00,31.25,2026-10-16T02:24:37Z,2026-10-16T02:24:00Z,CPR_TC=30063.38,PIV_D_R1=30350.50,+1 PIV_D_P
5,2026-10-16T04:51:35.426Z,30174.50,30211.75,30148.75,30189.25,31.25,2026-10-16T03:50:17Z,2026-10-16T03:50:00Z,CPR_TC=30063.38,PIV_D_R1=30350.50,
6,2026-10-16T05:59:58.154Z,30189.50,30225.00,30161.75,30191.25,31.25,2026-10-16T04:51:35Z,2026-10-16T04:51:00Z,CPR_TC=30063.38,PIV_D_R1=30350.50,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=1 2026-10-15T23:36:18.600Z side -1 fired CPR_TC: PIV_D_P=29986.50; PIV_D_R1=30350.50; PIV_D_R2=30560.75; PIV_D_R3=30924.75; PIV_D_S1=29776.25; PIV_D_S2=29412.25; PIV_D_S3=29202.00; PIV_W_P=31177.25; PIV_W_R1=31562.50; PIV_W_R2=32001.75; PIV_W_R3=32387.00; PIV_W_S1=30738.00; PIV_W_S2=30352.75; PIV_W_S3=29913.50; CPR_TC=30063.38; CPR_BC=29909.62
k=4 2026-10-16T03:50:17.816Z side +1 fired PIV_D_P: PIV_D_P=29986.50; PIV_D_R1=30350.50; PIV_D_R2=30560.75; PIV_D_R3=30924.75; PIV_D_S1=29776.25; PIV_D_S2=29412.25; PIV_D_S3=29202.00; PIV_W_P=31177.25; PIV_W_R1=31562.50; PIV_W_R2=32001.75; PIV_W_R3=32387.00; PIV_W_S1=30738.00; PIV_W_S2=30352.75; PIV_W_S3=29913.50; CPR_TC=30063.38; CPR_BC=29909.62
```

#### td 20261009 (sess_id 202610090, Asia session, grid week 183)
- bars of the session: 9, first known 2026-10-08T22:57:29.280Z, last known 2026-10-09T05:59:57.199Z; rebuilt-from-tape check 9/9/9; threshold values: L=5, thr_contracts=342.848, s_vol=0.857
SIGNALS (raw events of the session: 3 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
2,2026-10-09T00:16:39.053Z,-1,CPR_TC,31011.12,30979.50,24.88,Y
5,2026-10-09T03:09:02.079Z,1,PIV_D_P,31046.00,31056.00,25.25,Y
7,2026-10-09T05:56:18.174Z,1,CPR_BC,31080.88,31171.00,25.50,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
2,-1,2026-10-09T00:16:40.837Z,30984.75,0.4398,30984.64,2026-10-09T01:42:28.479Z,31045.00,Stop,60.0,60.0,-60.36,-1212.04
5,1,2026-10-09T03:09:03.114Z,31053.50,0.4398,31053.61,2026-10-09T03:55:43.944Z,31113.61,Target,60.0,60.0,60.00,1195.16
7,1,2026-10-09T05:56:19.206Z,31170.25,0.4398,31170.36,2026-10-09T05:59:57.199Z,31158.00,SessionEnd,60.0,60.0,-12.36,-252.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (all 9 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-08T22:57:29.280Z,31020.50,31072.50,30995.00,31035.00,24.88,2026-10-08T20:59:59Z,2026-10-08T20:59:00Z,PIV_D_S3=30939.17,PIV_D_S2=31041.08,
1,2026-10-08T23:47:00.924Z,31034.50,31036.50,30990.00,30990.00,24.88,2026-10-08T22:57:29Z,2026-10-08T22:57:00Z,PIV_W_P=30896.08,CPR_TC=31011.12,
2,2026-10-09T00:16:39.053Z,30990.00,31002.50,30953.00,30979.50,24.88,2026-10-08T23:47:00Z,2026-10-08T23:47:00Z,PIV_W_P=30896.08,CPR_TC=31011.12,-1 CPR_TC
3,2026-10-09T01:15:45.564Z,30979.75,31034.00,30966.00,30987.50,25.12,2026-10-09T00:16:39Z,2026-10-09T00:16:00Z,PIV_W_P=30896.08,CPR_TC=31011.12,
4,2026-10-09T02:02:34.413Z,30986.00,31083.75,30966.50,31079.00,25.25,2026-10-09T01:15:45Z,2026-10-09T01:15:00Z,PIV_D_P=31046.00,CPR_BC=31080.88,
5,2026-10-09T03:09:02.079Z,31077.75,31089.75,31046.50,31056.00,25.25,2026-10-09T02:02:34Z,2026-10-09T02:02:00Z,PIV_D_P=31046.00,CPR_BC=31080.88,+1 PIV_D_P
6,2026-10-09T04:52:58.260Z,31056.00,31138.00,31040.50,31103.00,25.50,2026-10-09T03:09:02Z,2026-10-09T03:09:00Z,CPR_BC=31080.88,PIV_D_R1=31300.00,
7,2026-10-09T05:56:18.174Z,31103.00,31171.00,31102.00,31171.00,25.50,2026-10-09T04:52:58Z,2026-10-09T04:52:00Z,CPR_BC=31080.88,PIV_D_R1=31300.00,+1 CPR_BC
8,2026-10-09T05:59:57.199Z,31171.25,31177.00,31154.75,31158.25,25.50,2026-10-09T05:56:18Z,2026-10-09T05:56:00Z,CPR_BC=31080.88,PIV_D_R1=31300.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=2 2026-10-09T00:16:39.053Z side -1 fired CPR_TC: PIV_D_P=31046.00; PIV_D_R1=31300.00; PIV_D_R2=31623.75; PIV_D_R3=31877.75; PIV_D_S1=30722.25; PIV_D_S2=30468.25; PIV_D_S3=30144.50; PIV_W_P=30896.08; PIV_W_R1=31435.42; PIV_W_R2=31821.83; PIV_W_R3=32361.17; PIV_W_S1=30509.67; PIV_W_S2=29970.33; PIV_W_S3=29583.92; CPR_TC=31011.12; CPR_BC=31080.88
k=5 2026-10-09T03:09:02.079Z side +1 fired PIV_D_P: PIV_D_P=31046.00; PIV_D_R1=31300.00; PIV_D_R2=31623.75; PIV_D_R3=31877.75; PIV_D_S1=30722.25; PIV_D_S2=30468.25; PIV_D_S3=30144.50; PIV_W_P=30896.08; PIV_W_R1=31435.42; PIV_W_R2=31821.83; PIV_W_R3=32361.17; PIV_W_S1=30509.67; PIV_W_S2=29970.33; PIV_W_S3=29583.92; CPR_TC=31011.12; CPR_BC=31080.88
k=7 2026-10-09T05:56:18.174Z side +1 fired CPR_BC: PIV_D_P=31046.00; PIV_D_R1=31300.00; PIV_D_R2=31623.75; PIV_D_R3=31877.75; PIV_D_S1=30722.25; PIV_D_S2=30468.25; PIV_D_S3=30144.50; PIV_W_P=30896.08; PIV_W_R1=31435.42; PIV_W_R2=31821.83; PIV_W_R3=32361.17; PIV_W_S1=30509.67; PIV_W_S2=29970.33; PIV_W_S3=29583.92; CPR_TC=31011.12; CPR_BC=31080.88
```

### BOOK W0e7037ba (Asia): lbrk_3_40 + profile nodes level retest (M 3, tol 0.5), BOTH sides, bracket fixed120/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 69 of 69 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W0e7037ba (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W0e7037ba_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W0e7037ba.parquet` (662 events: 321 long, 341 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `lbrk_3_40`, module `trig_levels_profile_nodes` (code/th_grid/trig_levels_profile_nodes.py -> triggers_d/lv_profile_nodes.py), variant `retest`, params {"M": 3, "tol": 0.5}, bracket `fixed120/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/lbrk_3_40/trig_levels_profile_nodes.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 596, L6M 649, L3M 785; t 5.1 over 454 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 117..185 (2025-06-29 to 2026-10-24) = 69 held week(s); months in the cell file: 202506, 202507, 202508, 202509, 202510, 202512, 202601, 202602, 202603, 202604, 202605, 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored 59.76 / mine 59.76 pts, 1 / 1 trades; w182 2026-09-27 stored -126.19 / mine -126.19 pts, 5 / 5 trades; w183 2026-10-04 stored 69.86 / mine 69.86 pts, 2 / 2 trades; w184 2026-10-11 stored -60.89 / mine -60.89 pts, 2 / 2 trades; w185 2026-10-18 stored 92.73 / mine 92.73 pts, 6 / 6 trades (last 5 of 69 held weeks shown; 69 of 69 equal)

**1. BAR**
**BAR** row `lbrk_3_40` = 3-LINE BREAK on a scaled box. [SPEC] kernel k_lbrk (kernels.py lines 274-309), build_month.py: box B = max(2, round(40 x s_rng)) ticks, NL = 3. Full rule text: D8_BAR_DEFS.md section 3.9 (continuation = fixed box from the last line close; reversal when price breaks beyond the extreme of the last NL lines, the reversal line closes 1 tick beyond that extreme; several lines per print possible, same timestamp; unfinished line never a bar). Box on the sample days: 20261023: box_ticks=88, box_pts=22.00, NL=3; 20261016: box_ticks=87, box_pts=21.75, NL=3; 20261008: box_ticks=92, box_pts=23.00, NL=3. [SPEC] Price-only: unaffected by the print rule (proved identical contract-level / run-merge / old engine in D8_PRINT_RULE section 2).
- [SPEC] Bars per Asia session in the loaded months: median 10 (min 1, max 161, 479 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/lbrk_3_40/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 18 stored / 18 rebuilt / 18 identical (o,h,l,c,known_ts,part); td 20261016: 18 stored / 18 rebuilt / 18 identical (o,h,l,c,known_ts,part); td 20261008: 8 stored / 8 rebuilt / 8 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **exists**: lbrk_3_40 specified (D8_BAR_DEFS 3.9, D8_BUILD_SPEC L7cc56d99); class LineBreakBuilder in D8Asia.cs.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_profile_nodes` (th_grid/triggers_d/lv_profile_nodes.py; lines fd_profile.py (whole file)). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 10 lines in this list order: PRF1__HVN1, PRF1__HVN2, PRF1__LVN1, PRF1__LVN2, PRF1__SPH, PRF1__SPL, PRF5__HVN1, PRF5__HVN2, PRF5__LVN1, PRF5__LVN2.
- Profile of a label day d = every trade print of RTH (09:30 <= ET < 16:00, mm in [570, 960)) as a volume-at-price histogram in back-adjusted ticks (price ticks + round(offday x 4), offday = roll offset at 12:00 ET of that day); days with fewer than 1000 RTH prints are skipped.
- POC / value area: POC = max row; 70% value area by two-row expansion (add the 2 rows above vs the 2 rows below, the larger first, ties up) until >= 70% of volume.
- Smoothing: Gaussian kernel sigma 8 ticks over +-24 ticks. HVN1/HVN2 = the two highest smoothed local maxima (strict right, non-strict left) that are more than 8 ticks away from the POC (sorted by smoothed volume); LVN1/LVN2 = the two lowest smoothed local minima inside [VAL, VAH].
- SPH / SPL = top / bottom row of the longest run (>= 4 rows) of price rows touched by exactly ONE 30-minute bracket (single prints; brackets = (mm - 570)//30).
- PRF5 = the same on the SUM of the histograms of the last 5 profile days (the profile day and the 4 before it).
- A profile of label day d is applied to ALL minutes of the NEXT label day (18:00 ET evening of day d through 18:00 ET next day) (put(): arr[ld == labs[i+1]]); converted to raw by raw = adj - off[i]; prices x 0.25.
Variant `retest` (M=3, tol=0.5): [SPEC] retest(M, tol) (fd_common.level_events; the retest grid has no k, so k = 0): a break-up EDGE = edge(close > L); LONG if a break-up edge happened on any of the previous M bars (bars j-M..j-1) and low <= L + tol*u and close > L and close >= open; SHORT mirrored (break-down edge within M bars, high >= L - tol*u, close < L, close <= open); edge().
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: M=3, tol=0.5 -> tol*u = 2.500 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 479 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): PRF1_HVN1 0.99, PRF1_HVN2 0.99, PRF1_LVN1 0.99, PRF1_LVN2 0.96, PRF1_SPH 0.99, PRF1_SPL 0.99, PRF5_HVN1 0.99, PRF5_HVN2 0.99, PRF5_LVN1 0.99, PRF5_LVN2 0.99.
- [READING] Module status: **spec exists, no code**: D8_NYAM_SPEC_Le4fede95 / D8_TRIGGER_DEFS 3.7 D specify the 10 lines (verified from tape for NY AM); D8Asia.cs has ValueArea only, no HVN/LVN/single-print code.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `fixed120/60` = stop 120 pts / target 60 pts, fixed (no unit rule); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 120 pts / target 60 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ trade tape (every print with size and time) for 5 RTH days + the roll offsets; not derivable from bars.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: 5 complete RTH days of tape prints (price-volume histogram incl. 30-minute brackets); the store has 2 lines with a 3-day hole (see D8_NYAM_SPEC_B7bfd33b7 / Le4fede95 notes). READING: needs a tick-level volume-at-price accumulator for the last 5 RTH days.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 3 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (held-week grid trades, measured)**
- [SPEC] 211 grid trades in the held weeks; share of trades whose signal bar is bar 0 of the session: 0.09; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 3, 4, 11, 49.
- [SPEC] Fired line (first line in list order that fired) over those trades: PRF1_HVN1 51, PRF1_HVN2 30, PRF1_SPH 22, PRF1_LVN2 22, PRF1_LVN1 21, PRF1_SPL 18, PRF5_LVN1 15, PRF5_HVN1 12, PRF5_LVN2 11, PRF5_HVN2 9.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W0e7037ba_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610230, Asia session, grid week 185)
- bars of the session: 18, first known 2026-10-22T22:00:14.742Z, last known 2026-10-23T01:43:39.987Z; rebuilt-from-tape check 18/18/18; threshold values: box_ticks=88, box_pts=22.000, NL=3
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
3,2026-10-22T22:24:07.655Z,1,PRF1__HVN1,29137.25,29160.75,5.00,Y
11,2026-10-23T00:47:07.579Z,1,PRF1__HVN1,29137.25,29160.50,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
3,1,2026-10-22T22:24:09.645Z,29161.00,0.6389,29161.16,2026-10-23T00:03:56.937Z,29040.75,Stop,120.0,60.0,-120.41,-2413.03
11,1,2026-10-23T00:47:08.622Z,29160.00,0.6389,29160.16,2026-10-23T05:59:59.668Z,29134.75,SessionEnd,120.0,60.0,-25.41,-513.03
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (all 18 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-22T22:00:14.742Z,29116.50,29116.50,29094.50,29094.50,5.00,2026-10-22T20:49:51Z,2026-10-22T20:49:00Z,,PRF5_LVN1=29693.75,
1,2026-10-22T22:00:46.318Z,29094.50,29116.75,29094.50,29116.75,5.00,2026-10-22T22:00:14Z,2026-10-22T22:00:00Z,,PRF1_HVN1=29137.25,
2,2026-10-22T22:01:49.984Z,29116.75,29138.75,29116.75,29138.75,5.00,2026-10-22T22:00:46Z,2026-10-22T22:00:00Z,PRF1_HVN1=29137.25,PRF1_LVN1=29162.25,
3,2026-10-22T22:24:07.655Z,29138.75,29160.75,29138.75,29160.75,5.00,2026-10-22T22:01:49Z,2026-10-22T22:01:00Z,PRF1_HVN1=29137.25,PRF1_LVN1=29162.25,+1 PRF1_HVN1
4,2026-10-22T23:01:12.476Z,29160.75,29160.75,29094.25,29094.25,5.00,2026-10-22T22:24:07Z,2026-10-22T22:24:00Z,,PRF1_HVN1=29137.25,
5,2026-10-22T23:27:33.546Z,29094.25,29094.25,29072.25,29072.25,5.00,2026-10-22T23:01:12Z,2026-10-22T23:01:00Z,,PRF1_HVN1=29137.25,
6,2026-10-22T23:35:22.023Z,29072.25,29072.25,29050.25,29050.25,5.00,2026-10-22T23:27:33Z,2026-10-22T23:27:00Z,,PRF1_HVN1=29137.25,
7,2026-10-23T00:10:08.883Z,29050.25,29050.25,29028.25,29028.25,5.00,2026-10-22T23:35:22Z,2026-10-22T23:35:00Z,,PRF1_HVN1=29137.25,
8,2026-10-23T00:12:08.773Z,29028.25,29094.50,29028.25,29094.50,5.00,2026-10-23T00:10:08Z,2026-10-23T00:10:00Z,,PRF1_HVN1=29137.25,
9,2026-10-23T00:14:25.450Z,29094.50,29116.50,29094.50,29116.50,5.00,2026-10-23T00:12:08Z,2026-10-23T00:12:00Z,,PRF1_HVN1=29137.25,
10,2026-10-23T00:42:41.655Z,29116.50,29138.50,29116.50,29138.50,5.00,2026-10-23T00:14:25Z,2026-10-23T00:14:00Z,PRF1_HVN1=29137.25,PRF1_LVN1=29162.25,
11,2026-10-23T00:47:07.579Z,29138.50,29160.50,29138.50,29160.50,5.00,2026-10-23T00:42:41Z,2026-10-23T00:42:00Z,PRF1_HVN1=29137.25,PRF1_LVN1=29162.25,+1 PRF1_HVN1
12,2026-10-23T00:48:08.965Z,29160.50,29182.50,29160.50,29182.50,5.00,2026-10-23T00:47:07Z,2026-10-23T00:47:00Z,PRF1_LVN1=29162.25,PRF1_LVN2=29237.75,
13,2026-10-23T01:12:12.390Z,29182.50,29182.50,29116.25,29116.25,5.00,2026-10-23T00:48:08Z,2026-10-23T00:48:00Z,,PRF1_HVN1=29137.25,
14,2026-10-23T01:15:13.985Z,29116.25,29116.25,29094.25,29094.25,5.00,2026-10-23T01:12:12Z,2026-10-23T01:12:00Z,,PRF1_HVN1=29137.25,
15,2026-10-23T01:16:55.808Z,29094.25,29094.25,29072.25,29072.25,5.00,2026-10-23T01:15:13Z,2026-10-23T01:15:00Z,,PRF1_HVN1=29137.25,
16,2026-10-23T01:27:41.620Z,29072.25,29182.75,29072.25,29182.75,5.00,2026-10-23T01:16:55Z,2026-10-23T01:16:00Z,PRF1_LVN1=29162.25,PRF1_LVN2=29237.75,
17,2026-10-23T01:43:39.987Z,29182.75,29204.75,29182.75,29204.75,5.00,2026-10-23T01:27:41Z,2026-10-23T01:27:00Z,PRF1_LVN1=29162.25,PRF1_LVN2=29237.75,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=3 2026-10-22T22:24:07.655Z side +1 fired PRF1_HVN1: PRF1_HVN1=29137.25; PRF1_HVN2=29296.50; PRF1_LVN1=29162.25; PRF1_LVN2=29237.75; PRF1_SPH=29435.75; PRF1_SPL=29380.00; PRF5_HVN1=29853.00; PRF5_HVN2=29722.75; PRF5_LVN1=29586.25; PRF5_LVN2=29603.75
k=11 2026-10-23T00:47:07.579Z side +1 fired PRF1_HVN1: PRF1_HVN1=29137.25; PRF1_HVN2=29296.50; PRF1_LVN1=29162.25; PRF1_LVN2=29237.75; PRF1_SPH=29435.75; PRF1_SPL=29380.00; PRF5_HVN1=29853.00; PRF5_HVN2=29722.75; PRF5_LVN1=29586.25; PRF5_LVN2=29603.75
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 18, first known 2026-10-15T22:00:15.323Z, last known 2026-10-16T05:01:12.956Z; rebuilt-from-tape check 18/18/18; threshold values: box_ticks=87, box_pts=21.750, NL=3
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
8,2026-10-16T00:22:26.505Z,-1,PRF1__HVN2,29991.00,29979.75,5.00,Y
9,2026-10-16T00:51:09.383Z,1,PRF1__HVN2,29991.00,30045.75,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
8,-1,2026-10-16T00:22:27.624Z,29980.25,0.6389,29980.09,2026-10-16T02:22:42.516Z,30100.50,Stop,120.0,60.0,-120.41,-2413.03
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 18 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-15T22:00:15.323Z,30089.00,30110.75,30089.00,30110.75,5.00,2026-10-15T20:56:46Z,2026-10-15T20:56:00Z,,PRF1_HVN1=30173.00,
1,2026-10-15T22:31:16.596Z,30110.75,30110.75,30088.75,30088.75,5.00,2026-10-15T22:00:15Z,2026-10-15T22:00:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
2,2026-10-15T22:54:14.573Z,30088.75,30088.75,30067.00,30067.00,5.00,2026-10-15T22:31:16Z,2026-10-15T22:31:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
3,2026-10-15T23:02:27.199Z,30067.00,30067.00,30045.25,30045.25,5.00,2026-10-15T22:54:14Z,2026-10-15T22:54:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
4,2026-10-15T23:20:19.606Z,30045.25,30045.25,30023.50,30023.50,5.00,2026-10-15T23:02:27Z,2026-10-15T23:02:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
5,2026-10-15T23:35:26.025Z,30023.50,30023.50,30001.75,30001.75,5.00,2026-10-15T23:20:19Z,2026-10-15T23:20:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
6,2026-10-16T00:00:01.076Z,30001.75,30001.75,29980.00,29980.00,5.00,2026-10-15T23:35:26Z,2026-10-15T23:35:00Z,PRF1_HVN1=29959.00,PRF1_HVN2=29991.00,
7,2026-10-16T00:12:30.696Z,29980.00,30045.50,29980.00,30045.50,5.00,2026-10-16T00:00:01Z,2026-10-16T00:00:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
8,2026-10-16T00:22:26.505Z,30045.50,30045.50,29979.75,29979.75,5.00,2026-10-16T00:12:30Z,2026-10-16T00:12:00Z,PRF1_HVN1=29959.00,PRF1_HVN2=29991.00,-1 PRF1_HVN2
9,2026-10-16T00:51:09.383Z,29979.75,30045.75,29979.75,30045.75,5.00,2026-10-16T00:22:26Z,2026-10-16T00:22:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,+1 PRF1_HVN2
10,2026-10-16T01:02:20.876Z,30045.75,30067.50,30045.75,30067.50,5.00,2026-10-16T00:51:09Z,2026-10-16T00:51:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
11,2026-10-16T01:47:43.908Z,30067.50,30089.25,30067.50,30089.25,5.00,2026-10-16T01:02:20Z,2026-10-16T01:02:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
12,2026-10-16T02:27:09.409Z,30089.25,30111.00,30089.25,30111.00,5.00,2026-10-16T01:47:43Z,2026-10-16T01:47:00Z,PRF1_HVN2=29991.00,PRF1_LVN2=30115.50,
13,2026-10-16T03:45:58.006Z,30111.00,30132.75,30111.00,30132.75,5.00,2026-10-16T02:27:09Z,2026-10-16T02:27:00Z,PRF1_LVN2=30115.50,PRF5_LVN1=30838.00,
14,2026-10-16T03:48:35.826Z,30132.75,30154.50,30132.75,30154.50,5.00,2026-10-16T03:45:58Z,2026-10-16T03:45:00Z,PRF1_LVN2=30115.50,PRF5_LVN1=30838.00,
15,2026-10-16T03:50:17.816Z,30154.50,30176.25,30154.50,30176.25,5.00,2026-10-16T03:48:35Z,2026-10-16T03:48:00Z,PRF1_LVN2=30115.50,PRF5_LVN1=30838.00,
16,2026-10-16T03:51:09.171Z,30176.25,30198.00,30176.25,30198.00,5.00,2026-10-16T03:50:17Z,2026-10-16T03:50:00Z,PRF1_LVN2=30115.50,PRF5_LVN1=30838.00,
17,2026-10-16T05:01:12.956Z,30198.00,30219.75,30198.00,30219.75,5.00,2026-10-16T03:51:09Z,2026-10-16T03:51:00Z,PRF1_LVN2=30115.50,PRF5_LVN1=30838.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=8 2026-10-16T00:22:26.505Z side -1 fired PRF1_HVN2: PRF1_HVN1=29959.00; PRF1_HVN2=29991.00; PRF1_LVN1=29875.00; PRF1_LVN2=30115.50; PRF1_SPH=29682.75; PRF1_SPL=29622.50; PRF5_HVN1=30890.50; PRF5_HVN2=30897.00; PRF5_LVN1=30838.00; PRF5_LVN2=29875.00
```

#### td 20261008 (sess_id 202610080, Asia session, grid week 183)
- bars of the session: 8, first known 2026-10-07T22:02:10.798Z, last known 2026-10-08T05:55:44.273Z; rebuilt-from-tape check 8/8/8; threshold values: box_ticks=92, box_pts=23.000, NL=3
SIGNALS (raw events of the session: 3 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
2,2026-10-08T00:15:22.257Z,-1,PRF5__LVN1,31451.50,31402.75,5.00,Y
4,2026-10-08T01:57:39.705Z,1,PRF1__HVN1,31377.25,31449.25,5.00,no
5,2026-10-08T03:16:14.638Z,-1,PRF1__LVN2,31401.50,31379.50,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
2,-1,2026-10-08T00:15:23.364Z,31402.50,0.6389,31402.34,2026-10-08T05:51:22.350Z,31342.34,Target,120.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 8 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-07T22:02:10.798Z,31403.00,31426.00,31403.00,31426.00,5.00,2026-10-07T19:55:00Z,2026-10-07T19:55:00Z,PRF5_LVN1=30981.75,PRF1_LVN1=31491.25,
1,2026-10-07T23:15:07.894Z,31426.00,31449.00,31426.00,31449.00,5.00,2026-10-07T22:02:10Z,2026-10-07T22:02:00Z,PRF1_LVN2=31401.50,PRF5_LVN1=31451.50,
2,2026-10-08T00:15:22.257Z,31449.00,31449.00,31402.75,31402.75,5.00,2026-10-07T23:15:07Z,2026-10-07T23:15:00Z,PRF1_LVN2=31401.50,PRF5_LVN1=31451.50,-1 PRF5_LVN1
3,2026-10-08T00:43:47.630Z,31402.75,31402.75,31379.75,31379.75,5.00,2026-10-08T00:15:22Z,2026-10-08T00:15:00Z,PRF1_HVN1=31377.25,PRF1_LVN2=31401.50,
4,2026-10-08T01:57:39.705Z,31379.75,31449.25,31379.75,31449.25,5.00,2026-10-08T00:43:47Z,2026-10-08T00:43:00Z,PRF1_LVN2=31401.50,PRF5_LVN1=31451.50,+1 PRF1_HVN1
5,2026-10-08T03:16:14.638Z,31449.25,31449.25,31379.50,31379.50,5.00,2026-10-08T01:57:39Z,2026-10-08T01:57:00Z,PRF1_HVN1=31377.25,PRF1_LVN2=31401.50,-1 PRF1_LVN2
6,2026-10-08T03:56:03.008Z,31379.50,31379.50,31356.50,31356.50,5.00,2026-10-08T03:16:14Z,2026-10-08T03:16:00Z,PRF1_LVN1=31310.50,PRF1_HVN1=31377.25,
7,2026-10-08T05:55:44.273Z,31356.50,31356.50,31333.50,31333.50,5.00,2026-10-08T03:56:03Z,2026-10-08T03:56:00Z,PRF1_LVN1=31310.50,PRF1_HVN1=31377.25,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=2 2026-10-08T00:15:22.257Z side -1 fired PRF5_LVN1: PRF1_HVN1=31377.25; PRF1_HVN2=31251.00; PRF1_LVN1=31310.50; PRF1_LVN2=31401.50; PRF1_SPH=31191.00; PRF1_SPL=31143.00; PRF5_HVN1=31235.75; PRF5_HVN2=31530.75; PRF5_LVN1=31451.50; PRF5_LVN2=31465.50
```

### BOOK Wf5779582 (Asia): tsf_10_60 + ob15 level false break (M 3, k 0.5), BOTH sides, bracket plain60/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id Wf5779582 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_Wf5779582_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/Wf5779582.parquet` (329 events: 187 long, 142 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `tsf_10_60`, module `trig_levels_ob15` (code/th_grid/trig_levels_ob15.py -> triggers_d/lv_ob15.py), variant `false_break`, params {"M": 3, "k": 0.5}, bracket `plain60/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/tsf_10_60/trig_levels_ob15.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 304, L6M 945, L3M 1249; t 4.4 over 211 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored 178.43 / mine 178.43 pts, 5 / 5 trades; w183 2026-10-04 stored 0.00 / mine 0.00 pts, 0 / 0 trades; w184 2026-10-11 stored -0.84 / mine -0.84 pts, 2 / 2 trades; w185 2026-10-18 stored 2.05 / mine 2.05 pts, 3 / 3 trades

**1. BAR**
**BAR** row `tsf_10_60` = TRADE-SIZE-FILTERED VOLUME bar (L = 10, N = 60). [SPEC] build_month.py lines 97-100 with kernel k_cum (kernels.py lines 11-33), mode 0: metric = print size if size >= 10 else 0; threshold thr = 60 x s_vol contracts (s_vol = abs_vol / r0_vol, fixed for the session). Per session key a bar opens at the first print; EVERY print updates o/h/l/c, volume, count (all prints, not only the counted ones; the registry text in th_bars/spec.py says 'OHLC uses only counted prints' but the code does not do that: code governs); cum += metric; the bar CLOSES at the print for which cum >= thr (the closing print stays in the bar, no split); known time = that print's timestamp; the last bar of the session is emitted with part = 1 (known at its last print) and is never a signal bar. Threshold on the sample days: 20261022: L=10, thr_contracts=59.80, s_vol=1.00; 20261012: L=10, thr_contracts=51.43, s_vol=0.86; 20261001: L=10, thr_contracts=50.54, s_vol=0.84. [SPEC] This row is an ACTIVITY (volume-accumulating) bar and the old-engine tape treats every MBO trade record as one print; D8_PRINT_RULE.md section 2 shows that volume-accumulating bars (vol, vsess, tick, dlt, cdr, dib ...) are DIFFERENT between contract level, run merge and the old engine bars (2% to 28% identical for volume-type bars). tsf is NOT in that proof table and has no run-merge version in /mnt/l2/l2vast/_d8spec/bars_c or bars_r. [READING] Because the filter acts on the SIZE of one print (record size >= L lots), merging records of the same price and side into one print (the D8 rule) changes which prints pass the filter and therefore every bar boundary: the grid result for this book is NOT proven for the D8 print stream, and a live bar builder cannot be matched without deciding the print granularity. RISK FLAG.
- [SPEC] Bars per Asia session in the loaded months: median 18 (min 5, max 52, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/tsf_10_60/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261022: 37 stored / 37 rebuilt / 37 identical (o,h,l,c,known_ts,part); td 20261012: 19 stored / 19 rebuilt / 19 identical (o,h,l,c,known_ts,part); td 20261001: 24 stored / 24 rebuilt / 24 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **NEW**: no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_ob15` (th_grid/triggers_d/lv_ob15.py; lines fd_levels2.py lines 98-123 (w = 15)). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 4 lines in this list order: OB15_BULHI, OB15_BULLO, OB15_BEARHI, OB15_BEARLO = high / low of the latest 'fresh' bullish order block and of the latest 'fresh' bearish order block on 15-minute bars.
- 15-minute bars: aggregate the 1-minute store, bucket = floor(ts / 900 s), bar end = (k+1) x 900 s; ATR14 = ewm(alpha = 1/14, adjust = False) of the true range (the first bar's TR uses pc = its own close).
- Loop over 15-min bars j >= 2, in this order: (1) a stored bullish OB (high, low) is cleared if low[j] <= OB low; a bearish OB is cleared if high[j] >= OB high. (2) a = ATR14[j-1]. (3) body = close[j] - open[j]; BULLISH impulse if body >= 1.5 a and close[j] > max(high[j-4..j-1]): the OB is the nearest earlier bar q in j-1..j-4 with close[q] < open[q] (a down candle); store (high[q], low[q]). BEARISH: -body >= 1.5 a and close[j] < min(low[j-4..j-1]): nearest earlier up candle q (close > open); store its (high, low). (4) the line value of bar j = the stored OB (NaN if none). (Only the latest bullish and the latest bearish OB are kept.)
- The value of bar j is available from the bar END ((j+1) x 900 s) and held for at most 14400 minutes (10 days) (to_min age limit).
- Note [SPEC]: the code clears an OB when a later bar trades through its far side (bull: low <= OB low), not when it first touches it; the module docstring says 'fresh until touched'.
Variant `false_break` (M=3, k=0.5): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: M=3, k=0.5 -> k*u = 2.500 pt.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): OB15_BULHI 0.42, OB15_BULLO 0.42, OB15_BEARHI 0.43, OB15_BEARLO 0.43.
- [READING] Module status: **NEW**: no spec, no class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `plain60/60` = stop 60 pts / target 60 pts, fixed (no unit rule); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `vol (activity bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 60 pts / target 60 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only (aggregated to 15 minutes).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: State carried since the last OB was formed (up to 10 days of 15-minute bars) plus ATR14 with infinite memory (adjust=False from the first bar). READING: a cold start needs at least about 10 days of 15-minute bars to reproduce every line; shorter history gives NaN where an older OB still stood.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 3 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; tsf thresholds use s_vol.

**7. WHAT ACTUALLY TRADES (held-week grid trades, measured)**
- [SPEC] 10 grid trades in the held weeks; share of trades whose signal bar is bar 0 of the session: 0.10; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 3, 4, 11.5, 33.
- [SPEC] Fired line (first line in list order that fired) over those trades: OB15_BEARLO 7, OB15_BULHI 2, OB15_BEARHI 1.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/Wf5779582_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261022 (sess_id 202610220, Asia session, grid week 185)
- bars of the session: 37, first known 2026-10-21T22:03:02.464Z, last known 2026-10-22T05:59:59.408Z; rebuilt-from-tape check 37/37/37; threshold values: L=10, thr_contracts=59.799, s_vol=0.997
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
15,2026-10-22T02:06:41.553Z,-1,OB15_BULHI,29744.25,29741.75,5.00,Y
16,2026-10-22T02:17:24.459Z,-1,OB15_BULLO,29715.50,29700.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
15,-1,2026-10-22T02:06:42.869Z,29740.50,0.4398,29740.39,2026-10-22T02:32:39.248Z,29680.39,Target,60.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 37 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-21T22:03:02.464Z,29984.00,29993.25,29896.00,29901.50,5.00,2026-10-21T20:59:59Z,2026-10-21T20:59:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
1,2026-10-21T22:35:07.120Z,29901.25,29921.00,29831.75,29858.00,5.00,2026-10-21T22:03:02Z,2026-10-21T22:03:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
2,2026-10-21T22:52:19.675Z,29859.75,29863.25,29833.50,29846.00,5.00,2026-10-21T22:35:07Z,2026-10-21T22:35:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
3,2026-10-21T23:11:05.851Z,29846.25,29862.00,29805.25,29826.00,5.00,2026-10-21T22:52:19Z,2026-10-21T22:52:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
4,2026-10-21T23:37:18.529Z,29826.50,29837.50,29772.25,29786.00,5.00,2026-10-21T23:11:05Z,2026-10-21T23:11:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
5,2026-10-22T00:00:16.902Z,29786.50,29795.00,29753.50,29792.25,5.00,2026-10-21T23:37:18Z,2026-10-21T23:37:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
6,2026-10-22T00:17:54.550Z,29792.25,29854.50,29775.75,29790.25,5.00,2026-10-22T00:00:16Z,2026-10-22T00:00:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
7,2026-10-22T00:21:53.624Z,29790.00,29813.25,29778.25,29779.25,5.00,2026-10-22T00:17:54Z,2026-10-22T00:17:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
8,2026-10-22T01:16:29.157Z,29779.25,29826.25,29766.00,29802.25,5.00,2026-10-22T00:21:53Z,2026-10-22T00:21:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
9,2026-10-22T01:19:25.719Z,29802.50,29812.00,29772.00,29772.00,5.00,2026-10-22T01:16:29Z,2026-10-22T01:16:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
10,2026-10-22T01:28:08.805Z,29771.50,29784.50,29756.50,29780.00,5.00,2026-10-22T01:19:25Z,2026-10-22T01:19:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
11,2026-10-22T01:37:19.397Z,29780.75,29798.50,29745.25,29745.25,5.00,2026-10-22T01:28:08Z,2026-10-22T01:28:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
12,2026-10-22T01:38:03.085Z,29745.25,29755.25,29745.00,29745.00,5.00,2026-10-22T01:37:19Z,2026-10-22T01:37:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
13,2026-10-22T01:45:13.928Z,29745.25,29763.25,29731.00,29759.50,5.00,2026-10-22T01:38:03Z,2026-10-22T01:38:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
14,2026-10-22T02:01:48.863Z,29758.25,29768.00,29728.25,29751.00,5.00,2026-10-22T01:45:13Z,2026-10-22T01:45:00Z,OB15_BULHI=29744.25,OB15_BEARLO=30059.25,
15,2026-10-22T02:06:41.553Z,29750.75,29759.00,29741.75,29741.75,5.00,2026-10-22T02:01:48Z,2026-10-22T02:01:00Z,OB15_BULLO=29715.50,OB15_BULHI=29744.25,-1 OB15_BULHI
16,2026-10-22T02:17:24.459Z,29741.25,29748.75,29700.25,29700.25,5.00,2026-10-22T02:06:41Z,2026-10-22T02:06:00Z,,OB15_BULLO=29715.50,-1 OB15_BULLO
17,2026-10-22T02:29:48.678Z,29700.25,29707.75,29682.00,29695.50,5.00,2026-10-22T02:17:24Z,2026-10-22T02:17:00Z,,OB15_BEARLO=30059.25,
18,2026-10-22T02:56:36.397Z,29695.50,29711.75,29670.25,29678.00,5.00,2026-10-22T02:29:48Z,2026-10-22T02:29:00Z,,OB15_BEARLO=30059.25,
19,2026-10-22T03:02:47.535Z,29678.00,29697.25,29670.00,29670.00,5.00,2026-10-22T02:56:36Z,2026-10-22T02:56:00Z,,OB15_BEARLO=30059.25,
20,2026-10-22T03:08:36.436Z,29669.75,29684.50,29658.25,29673.00,5.00,2026-10-22T03:02:47Z,2026-10-22T03:02:00Z,,OB15_BEARLO=30059.25,
21,2026-10-22T03:28:21.999Z,29673.75,29692.00,29649.50,29666.00,5.00,2026-10-22T03:08:36Z,2026-10-22T03:08:00Z,,OB15_BEARLO=30059.25,
22,2026-10-22T03:32:39.439Z,29666.00,29674.50,29650.00,29650.00,5.00,2026-10-22T03:28:21Z,2026-10-22T03:28:00Z,,OB15_BEARLO=30059.25,
23,2026-10-22T03:35:31.900Z,29649.50,29651.00,29631.00,29631.25,5.00,2026-10-22T03:32:39Z,2026-10-22T03:32:00Z,,OB15_BEARLO=30059.25,
24,2026-10-22T03:35:42.342Z,29631.00,29633.25,29631.00,29631.00,5.00,2026-10-22T03:35:31Z,2026-10-22T03:35:00Z,,OB15_BEARLO=30059.25,
25,2026-10-22T03:53:31.169Z,29630.50,29653.25,29619.00,29620.00,5.00,2026-10-22T03:35:42Z,2026-10-22T03:35:00Z,,OB15_BEARLO=30059.25,
26,2026-10-22T04:23:12.593Z,29620.00,29636.00,29600.25,29600.25,5.00,2026-10-22T03:53:31Z,2026-10-22T03:53:00Z,,OB15_BEARLO=30059.25,
27,2026-10-22T04:34:52.333Z,29600.25,29620.50,29600.25,29600.25,5.00,2026-10-22T04:23:12Z,2026-10-22T04:23:00Z,,OB15_BEARLO=30059.25,
28,2026-10-22T04:34:52.355Z,29601.00,29601.00,29600.00,29600.00,5.00,2026-10-22T04:34:52Z,2026-10-22T04:34:00Z,,OB15_BEARLO=30059.25,
29,2026-10-22T04:49:07.757Z,29599.75,29615.00,29582.75,29590.75,5.00,2026-10-22T04:34:52Z,2026-10-22T04:34:00Z,,OB15_BEARLO=30059.25,
30,2026-10-22T05:22:24.254Z,29590.50,29627.00,29580.00,29580.00,5.00,2026-10-22T04:49:07Z,2026-10-22T04:49:00Z,,OB15_BEARLO=30059.25,
31,2026-10-22T05:24:38.179Z,29580.00,29583.75,29570.00,29570.00,5.00,2026-10-22T05:22:24Z,2026-10-22T05:22:00Z,,OB15_BEARLO=30059.25,
32,2026-10-22T05:29:27.372Z,29570.00,29598.50,29566.00,29584.25,5.00,2026-10-22T05:24:38Z,2026-10-22T05:24:00Z,,OB15_BEARLO=30059.25,
33,2026-10-22T05:40:14.503Z,29584.00,29591.75,29550.00,29550.00,5.00,2026-10-22T05:29:27Z,2026-10-22T05:29:00Z,,OB15_BEARLO=30059.25,
34,2026-10-22T05:41:14.110Z,29550.00,29552.00,29540.00,29540.00,5.00,2026-10-22T05:40:14Z,2026-10-22T05:40:00Z,,OB15_BEARLO=30059.25,
35,2026-10-22T05:59:20.383Z,29539.50,29549.75,29507.25,29542.50,5.00,2026-10-22T05:41:14Z,2026-10-22T05:41:00Z,,OB15_BEARLO=30059.25,
36,2026-10-22T05:59:59.408Z,29542.75,29548.75,29542.00,29545.00,5.00,2026-10-22T05:59:20Z,2026-10-22T05:59:00Z,,OB15_BEARLO=30059.25,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=15 2026-10-22T02:06:41.553Z side -1 fired OB15_BULHI: OB15_BULHI=29744.25; OB15_BULLO=29715.50; OB15_BEARHI=30084.50; OB15_BEARLO=30059.25
```

#### td 20261012 (sess_id 202610120, Asia session, grid week 184)
- bars of the session: 19, first known 2026-10-11T22:00:00.000Z, last known 2026-10-12T05:59:59.772Z; rebuilt-from-tape check 19/19/19; threshold values: L=10, thr_contracts=51.427, s_vol=0.857
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
2,2026-10-11T23:02:23.937Z,1,OB15_BEARLO,31181.50,31190.00,5.00,Y
3,2026-10-11T23:31:04.096Z,1,OB15_BEARHI,31217.25,31266.00,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
2,1,2026-10-11T23:02:25.083Z,31191.25,0.4398,31191.36,2026-10-11T23:27:33.428Z,31251.36,Target,60.0,60.0,60.00,1195.16
3,1,2026-10-11T23:31:05.159Z,31268.00,0.4398,31268.11,2026-10-12T00:52:40.695Z,31207.75,Stop,60.0,60.0,-60.36,-1212.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (all 19 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-11T22:00:00.000Z,31145.50,31145.50,31145.50,31145.50,5.00,2026-10-09T20:59:59Z,2026-10-09T20:59:00Z,,OB15_BEARLO=31181.50,
1,2026-10-11T22:04:05.117Z,31149.25,31186.00,31124.50,31180.50,5.00,2026-10-11T22:00:00Z,2026-10-11T22:00:00Z,,OB15_BEARLO=31181.50,
2,2026-10-11T23:02:23.937Z,31180.50,31200.00,31172.00,31190.00,5.00,2026-10-11T22:04:05Z,2026-10-11T22:04:00Z,OB15_BEARLO=31181.50,OB15_BEARHI=31217.25,+1 OB15_BEARLO
3,2026-10-11T23:31:04.096Z,31189.25,31266.00,31183.00,31266.00,5.00,2026-10-11T23:02:23Z,2026-10-11T23:02:00Z,OB15_BEARHI=31217.25,,+1 OB15_BEARHI
4,2026-10-11T23:43:27.626Z,31266.00,31289.25,31261.50,31273.25,5.00,2026-10-11T23:31:04Z,2026-10-11T23:31:00Z,,,
5,2026-10-12T00:19:50.945Z,31272.75,31276.75,31232.75,31240.50,5.00,2026-10-11T23:43:27Z,2026-10-11T23:43:00Z,,,
6,2026-10-12T00:46:40.177Z,31240.75,31261.75,31233.50,31239.00,5.00,2026-10-12T00:19:50Z,2026-10-12T00:19:00Z,,,
7,2026-10-12T00:52:50.111Z,31238.75,31254.00,31200.25,31200.25,5.00,2026-10-12T00:46:40Z,2026-10-12T00:46:00Z,,,
8,2026-10-12T01:09:31.593Z,31200.00,31242.50,31194.75,31206.00,5.00,2026-10-12T00:52:50Z,2026-10-12T00:52:00Z,,,
9,2026-10-12T01:23:06.664Z,31206.50,31223.00,31185.00,31185.00,5.00,2026-10-12T01:09:31Z,2026-10-12T01:09:00Z,,,
10,2026-10-12T01:38:26.185Z,31184.50,31191.25,31158.00,31188.00,5.00,2026-10-12T01:23:06Z,2026-10-12T01:23:00Z,,,
11,2026-10-12T01:47:05.936Z,31188.25,31198.50,31172.50,31181.75,5.00,2026-10-12T01:38:26Z,2026-10-12T01:38:00Z,,,
12,2026-10-12T01:52:47.917Z,31181.50,31212.75,31178.75,31212.75,5.00,2026-10-12T01:47:05Z,2026-10-12T01:47:00Z,,,
13,2026-10-12T02:28:17.889Z,31213.00,31239.00,31193.75,31239.00,5.00,2026-10-12T01:52:47Z,2026-10-12T01:52:00Z,,,
14,2026-10-12T02:39:05.598Z,31239.25,31242.50,31220.25,31223.00,5.00,2026-10-12T02:28:17Z,2026-10-12T02:28:00Z,,,
15,2026-10-12T03:18:46.729Z,31222.75,31236.75,31218.50,31219.50,5.00,2026-10-12T02:39:05Z,2026-10-12T02:39:00Z,,,
16,2026-10-12T04:13:13.769Z,31219.00,31244.50,31213.00,31220.50,5.00,2026-10-12T03:18:46Z,2026-10-12T03:18:00Z,,,
17,2026-10-12T05:46:01.519Z,31220.75,31259.75,31195.50,31203.50,5.00,2026-10-12T04:13:13Z,2026-10-12T04:13:00Z,,,
18,2026-10-12T05:59:59.772Z,31204.00,31232.75,31202.75,31203.25,5.00,2026-10-12T05:46:01Z,2026-10-12T05:46:00Z,,OB15_BEARLO=31244.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=2 2026-10-11T23:02:23.937Z side +1 fired OB15_BEARLO: OB15_BEARHI=31217.25; OB15_BEARLO=31181.50
k=3 2026-10-11T23:31:04.096Z side +1 fired OB15_BEARHI: OB15_BEARHI=31217.25; OB15_BEARLO=31181.50
```

#### td 20261001 (sess_id 202610010, Asia session, grid week 182)
- bars of the session: 24, first known 2026-09-30T22:05:59.255Z, last known 2026-10-01T05:59:59.928Z; rebuilt-from-tape check 24/24/24; threshold values: L=10, thr_contracts=50.544, s_vol=0.842
SIGNALS (raw events of the session: 4 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
3,2026-09-30T23:38:36.472Z,1,OB15_BEARLO,30811.25,30825.00,5.00,Y
4,2026-10-01T00:05:11.452Z,-1,OB15_BEARLO,30811.25,30795.00,5.00,Y
7,2026-10-01T01:15:01.808Z,1,OB15_BEARLO,30811.25,30815.00,5.00,Y
9,2026-10-01T02:29:55.371Z,1,OB15_BEARHI,30855.00,30857.00,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
3,1,2026-09-30T23:38:37.559Z,30827.25,0.4398,30827.36,2026-10-01T00:19:12.787Z,30767.00,Stop,60.0,60.0,-60.36,-1212.04
4,-1,2026-10-01T00:05:12.844Z,30795.75,0.4398,30795.64,2026-10-01T00:30:28.951Z,30735.64,Target,60.0,60.0,60.00,1195.16
7,1,2026-10-01T01:15:03.005Z,30814.00,0.4398,30814.11,2026-10-01T03:00:49.251Z,30874.11,Target,60.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (all 24 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-09-30T22:05:59.255Z,30707.00,30735.75,30684.50,30731.25,5.00,2026-09-30T20:59:59Z,2026-09-30T20:59:00Z,OB15_BULHI=30600.00,OB15_BEARLO=30811.25,
1,2026-09-30T22:44:02.733Z,30731.25,30794.75,30712.75,30778.25,5.00,2026-09-30T22:05:59Z,2026-09-30T22:05:00Z,OB15_BULHI=30600.00,OB15_BEARLO=30811.25,
2,2026-09-30T23:08:42.478Z,30778.50,30783.50,30759.50,30762.75,5.00,2026-09-30T22:44:02Z,2026-09-30T22:44:00Z,OB15_BULHI=30600.00,OB15_BEARLO=30811.25,
3,2026-09-30T23:38:36.472Z,30763.50,30825.00,30754.25,30825.00,5.00,2026-09-30T23:08:42Z,2026-09-30T23:08:00Z,OB15_BEARLO=30811.25,OB15_BEARHI=30855.00,+1 OB15_BEARLO
4,2026-10-01T00:05:11.452Z,30825.25,30834.25,30795.00,30795.00,5.00,2026-09-30T23:38:36Z,2026-09-30T23:38:00Z,OB15_BULHI=30600.00,OB15_BEARLO=30811.25,-1 OB15_BEARLO
5,2026-10-01T00:23:29.051Z,30794.75,30807.25,30754.75,30754.75,5.00,2026-10-01T00:05:11Z,2026-10-01T00:05:00Z,OB15_BULHI=30600.00,OB15_BEARLO=30811.25,
6,2026-10-01T01:08:02.329Z,30754.50,30806.00,30724.75,30799.25,5.00,2026-10-01T00:23:29Z,2026-10-01T00:23:00Z,OB15_BULHI=30600.00,OB15_BEARLO=30811.25,
7,2026-10-01T01:15:01.808Z,30799.25,30838.50,30796.50,30815.00,5.00,2026-10-01T01:08:02Z,2026-10-01T01:08:00Z,OB15_BEARLO=30811.25,OB15_BEARHI=30855.00,+1 OB15_BEARLO
8,2026-10-01T02:13:39.737Z,30814.50,30845.75,30804.25,30835.00,5.00,2026-10-01T01:15:01Z,2026-10-01T01:15:00Z,OB15_BEARLO=30811.25,OB15_BEARHI=30855.00,
9,2026-10-01T02:29:55.371Z,30834.75,30857.00,30820.50,30857.00,5.00,2026-10-01T02:13:39Z,2026-10-01T02:13:00Z,OB15_BEARHI=30855.00,,+1 OB15_BEARHI
10,2026-10-01T03:15:06.667Z,30857.00,30887.50,30849.50,30880.00,5.00,2026-10-01T02:29:55Z,2026-10-01T02:29:00Z,OB15_BEARHI=30855.00,,
11,2026-10-01T03:46:23.627Z,30879.75,30886.00,30860.00,30881.75,5.00,2026-10-01T03:15:06Z,2026-10-01T03:15:00Z,OB15_BULHI=30600.00,,
12,2026-10-01T03:59:13.595Z,30882.00,30930.00,30879.50,30930.00,5.00,2026-10-01T03:46:23Z,2026-10-01T03:46:00Z,OB15_BULHI=30600.00,,
13,2026-10-01T04:34:18.557Z,30930.00,30953.75,30921.00,30946.50,5.00,2026-10-01T03:59:13Z,2026-10-01T03:59:00Z,OB15_BULHI=30600.00,,
14,2026-10-01T04:39:34.606Z,30946.75,30961.00,30942.00,30953.00,5.00,2026-10-01T04:34:18Z,2026-10-01T04:34:00Z,OB15_BULHI=30600.00,,
15,2026-10-01T04:45:56.829Z,30953.25,30957.75,30941.50,30955.50,5.00,2026-10-01T04:39:34Z,2026-10-01T04:39:00Z,OB15_BULHI=30600.00,,
16,2026-10-01T04:50:04.056Z,30955.25,30980.00,30954.00,30970.00,5.00,2026-10-01T04:45:56Z,2026-10-01T04:45:00Z,OB15_BULHI=30600.00,,
17,2026-10-01T05:04:54.352Z,30970.25,31000.00,30964.25,31000.00,5.00,2026-10-01T04:50:04Z,2026-10-01T04:50:00Z,OB15_BULHI=30600.00,,
18,2026-10-01T05:05:42.243Z,31000.00,31007.50,30998.00,31007.50,5.00,2026-10-01T05:04:54Z,2026-10-01T05:04:00Z,OB15_BULHI=30600.00,,
19,2026-10-01T05:11:45.923Z,31008.00,31024.25,31007.00,31010.25,5.00,2026-10-01T05:05:42Z,2026-10-01T05:05:00Z,OB15_BULHI=30600.00,,
20,2026-10-01T05:27:08.397Z,31009.75,31049.75,31007.25,31049.75,5.00,2026-10-01T05:11:45Z,2026-10-01T05:11:00Z,OB15_BULHI=30600.00,,
21,2026-10-01T05:30:02.061Z,31049.75,31067.50,31041.50,31064.75,5.00,2026-10-01T05:27:08Z,2026-10-01T05:27:00Z,OB15_BULHI=30600.00,,
22,2026-10-01T05:55:11.089Z,31064.50,31094.50,31041.25,31083.00,5.00,2026-10-01T05:30:02Z,2026-10-01T05:30:00Z,OB15_BULHI=30600.00,,
23,2026-10-01T05:59:59.928Z,31084.25,31095.25,31078.25,31094.75,5.00,2026-10-01T05:55:11Z,2026-10-01T05:55:00Z,OB15_BULHI=30600.00,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=3 2026-09-30T23:38:36.472Z side +1 fired OB15_BEARLO: OB15_BULHI=30600.00; OB15_BULLO=30553.75; OB15_BEARHI=30855.00; OB15_BEARLO=30811.25
k=4 2026-10-01T00:05:11.452Z side -1 fired OB15_BEARLO: OB15_BULHI=30600.00; OB15_BULLO=30553.75; OB15_BEARHI=30855.00; OB15_BEARLO=30811.25
k=7 2026-10-01T01:15:01.808Z side +1 fired OB15_BEARLO: OB15_BULHI=30600.00; OB15_BULLO=30553.75; OB15_BEARHI=30855.00; OB15_BEARLO=30811.25
```

### BOOK W65dc0e76 (Asia): tsf_5_400 + fib15 level break native (n 2, k 0.25), BOTH sides, bracket plain60/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W65dc0e76 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W65dc0e76_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W65dc0e76.parquet` (2733 events: 1456 long, 1277 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `tsf_5_400`, module `trig_levels_fib15` (code/th_grid/trig_levels_fib15.py -> triggers_d/lv_fib15.py -> lv_fibleg.py (build('15'))), variant `break_native`, params {"n": 2, "k": 0.25}, bracket `plain60/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/tsf_5_400/trig_levels_fib15.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 663, L6M 1292, L3M 861; t 3.8 over 1428 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored -187.00 / mine -187.00 pts, 13 / 13 trades; w183 2026-10-04 stored -134.00 / mine -134.00 pts, 13 / 13 trades; w184 2026-10-11 stored 281.74 / mine 281.74 pts, 15 / 15 trades; w185 2026-10-18 stored -296.74 / mine -296.74 pts, 14 / 14 trades

**1. BAR**
**BAR** row `tsf_5_400` = TRADE-SIZE-FILTERED VOLUME bar (L = 5, N = 400). [SPEC] build_month.py lines 97-100 with kernel k_cum (kernels.py lines 11-33), mode 0: metric = print size if size >= 5 else 0; threshold thr = 400 x s_vol contracts (s_vol = abs_vol / r0_vol, fixed for the session). Per session key a bar opens at the first print; EVERY print updates o/h/l/c, volume, count (all prints, not only the counted ones; the registry text in th_bars/spec.py says 'OHLC uses only counted prints' but the code does not do that: code governs); cum += metric; the bar CLOSES at the print for which cum >= thr (the closing print stays in the bar, no split); known time = that print's timestamp; the last bar of the session is emitted with part = 1 (known at its last print) and is never a signal bar. Threshold on the sample days: 20261023: L=5, thr_contracts=398.66, s_vol=1.00; 20261016: L=5, thr_contracts=348.27, s_vol=0.87; 20261009: L=5, thr_contracts=342.85, s_vol=0.86. [SPEC] This row is an ACTIVITY (volume-accumulating) bar and the old-engine tape treats every MBO trade record as one print; D8_PRINT_RULE.md section 2 shows that volume-accumulating bars (vol, vsess, tick, dlt, cdr, dib ...) are DIFFERENT between contract level, run merge and the old engine bars (2% to 28% identical for volume-type bars). tsf is NOT in that proof table and has no run-merge version in /mnt/l2/l2vast/_d8spec/bars_c or bars_r. [READING] Because the filter acts on the SIZE of one print (record size >= L lots), merging records of the same price and side into one print (the D8 rule) changes which prints pass the filter and therefore every bar boundary: the grid result for this book is NOT proven for the D8 print stream, and a live bar builder cannot be matched without deciding the print granularity. RISK FLAG.
- [SPEC] Bars per Asia session in the loaded months: median 9 (min 2, max 21, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/tsf_5_400/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 10 stored / 10 rebuilt / 10 identical (o,h,l,c,known_ts,part); td 20261016: 7 stored / 7 rebuilt / 7 identical (o,h,l,c,known_ts,part); td 20261009: 9 stored / 9 rebuilt / 9 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **NEW**: no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_fib15` (th_grid/triggers_d/lv_fib15.py -> lv_fibleg.py (build('15')); lines fd_levels2.py lines 40-60). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 9 lines FIB15_R236, R382, R500, R618, R650, R786, E1272, E1618, E2000 (list order of lv_fibleg.ALL): Fibonacci levels of the last confirmed 15-minute swing leg.
- 15-minute bars from the 1-minute store (bucket floor(ts/900 s)); fractal pivots with strength k = 2 (high pivot at bar j: h[j] >= max(h[j-2..j+2]) and the unique maximum; low mirrored); a pivot counts only from the END of bar j+2 (confirmation).
- Zigzag: confirmed pivots alternate high / low; a later pivot of the same type replaces the previous only if more extreme (decided at confirmation time); leg B -> C = second-last -> last pivot, rng = C - B.
- R_r = C - r x rng for r = .236 .382 .5 .618 .65 .786; E_e = B + e x rng for e = 1.272 1.618 2.0; each valid from the end of the confirming bar and held 14400 minutes (10 days), then NaN.
- The module also stores FIB15_DIR (leg direction) and a leg-size column for exit use; they are not level lines.
Variant `break_native` (n=2, k=0.25): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (native) = rolling median of (high - low) over the previous 100 bars of THIS book's bar series (bars j-100..j-1, shifted one bar, min_periods 20, floor 0.5 pt; NaN before 20 bars) (fd_common.unit); every tolerance below is x u. With these parameters: n=2, k=0.25 -> k*u = 0.25 x u.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): FIB15_R236 1.00, FIB15_R382 1.00, FIB15_R500 1.00, FIB15_R618 1.00, FIB15_R650 1.00, FIB15_R786 1.00, FIB15_E1272 1.00, FIB15_E1618 1.00, FIB15_E2000 1.00.
- [READING] Module status: **zigzag class exists**: FibZig (fib15, fib60) in D8Asia.cs and D8_TRIGGER_DEFS 3.7 D text; the generic level_events variants (break_native n=2 exists as LevelBreakNative).

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `plain60/60` = stop 60 pts / target 60 pts, fixed (no unit rule); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `vol (activity bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 60 pts / target 60 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only (aggregated to 15 minutes).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: Needs the zigzag history: at least 3 alternating confirmed pivots (A, B, C); the live FibZig class in D8Asia.cs implements this rule. READING: a cold start needs a few days of 15-minute bars for the leg to be the same as the engine's (the zigzag replacement rule makes the current leg depend on earlier pivots).
- [SPEC] Warm-up of the trigger: native u needs 20 earlier bars of the continuous series (rolling 100, shifted). Memory M / hold n of the variant: 2 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; tsf thresholds use s_vol.

**7. WHAT ACTUALLY TRADES (held-week grid trades, measured)**
- [SPEC] 55 grid trades in the held weeks; share of trades whose signal bar is bar 0 of the session: 0.07; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 2, 4, 7, 19.
- [SPEC] Fired line (first line in list order that fired) over those trades: FIB15_R236 25, FIB15_R382 11, FIB15_R786 6, FIB15_R618 6, FIB15_R500 6, FIB15_R650 1.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W65dc0e76_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610230, Asia session, grid week 185)
- bars of the session: 10, first known 2026-10-22T22:17:47.443Z, last known 2026-10-23T05:59:59.668Z; rebuilt-from-tape check 10/10/10; threshold values: L=5, thr_contracts=398.663, s_vol=0.997
SIGNALS (raw events of the session: 4 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
3,2026-10-23T01:12:29.405Z,1,FIB15_R618,29107.81,29120.00,34.25,Y
7,2026-10-23T04:31:35.919Z,1,FIB15_R382,29140.02,29173.00,34.25,Y
8,2026-10-23T05:34:53.780Z,-1,FIB15_R786,29189.02,29136.75,34.25,Y
9,2026-10-23T05:59:59.668Z,-1,FIB15_R236,29150.52,29135.00,34.25,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
3,1,2026-10-23T01:12:30.466Z,29120.00,0.4398,29120.11,2026-10-23T01:17:37.396Z,29059.75,Stop,60.0,60.0,-60.36,-1212.04
7,1,2026-10-23T04:31:36.983Z,29173.00,0.4398,29173.11,2026-10-23T05:26:39.597Z,29112.75,Stop,60.0,60.0,-60.36,-1212.04
8,-1,2026-10-23T05:34:54.846Z,29124.00,0.4398,29123.89,2026-10-23T05:43:42.055Z,29184.25,Stop,60.0,60.0,-60.36,-1212.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (all 10 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-22T22:17:47.443Z,29116.50,29149.25,29090.00,29125.00,33.88,2026-10-22T20:59:58Z,2026-10-22T20:59:00Z,FIB15_R500=29124.00,FIB15_R382=29145.48,
1,2026-10-22T23:33:00.148Z,29125.00,29165.75,29060.00,29060.00,34.25,2026-10-22T22:17:47Z,2026-10-22T22:17:00Z,,FIB15_R786=29071.95,
2,2026-10-23T00:42:47.982Z,29059.50,29142.00,29022.75,29142.00,34.25,2026-10-22T23:33:00Z,2026-10-22T23:33:00Z,FIB15_R382=29129.94,FIB15_R236=29143.62,
3,2026-10-23T01:12:29.405Z,29141.50,29198.50,29114.00,29120.00,34.25,2026-10-23T00:42:47Z,2026-10-23T00:42:00Z,FIB15_R500=29118.88,FIB15_R382=29129.94,+1 FIB15_R618
4,2026-10-23T01:43:36.279Z,29120.25,29204.00,29056.75,29199.25,34.25,2026-10-23T01:12:29Z,2026-10-23T01:12:00Z,FIB15_R786=29135.15,,
5,2026-10-23T02:07:54.698Z,29198.75,29212.50,29089.00,29117.25,34.25,2026-10-23T01:43:36Z,2026-10-23T01:43:00Z,FIB15_R650=29115.70,FIB15_R786=29135.15,
6,2026-10-23T02:36:58.765Z,29117.00,29203.75,29106.50,29199.75,34.25,2026-10-23T02:07:54Z,2026-10-23T02:07:00Z,FIB15_R786=29135.15,,
7,2026-10-23T04:31:35.919Z,29199.75,29204.00,29134.00,29173.00,34.25,2026-10-23T02:36:58Z,2026-10-23T02:36:00Z,FIB15_R236=29167.72,FIB15_E1272=29264.11,+1 FIB15_R382
8,2026-10-23T05:34:53.780Z,29173.25,29177.00,29105.50,29136.75,34.25,2026-10-23T04:31:35Z,2026-10-23T04:31:00Z,FIB15_E1272=29114.96,FIB15_R236=29150.52,-1 FIB15_R786
9,2026-10-23T05:59:59.668Z,29136.75,29188.25,29123.50,29135.00,34.25,2026-10-23T05:34:53Z,2026-10-23T05:34:00Z,FIB15_E1272=29114.96,FIB15_R236=29150.52,-1 FIB15_R236
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=3 2026-10-23T01:12:29.405Z side +1 fired FIB15_R618: FIB15_R236=29143.62; FIB15_R382=29129.94; FIB15_R500=29118.88; FIB15_R618=29107.81; FIB15_R650=29104.81; FIB15_R786=29092.06; FIB15_E1272=29191.25; FIB15_E1618=29223.69; FIB15_E2000=29259.50
k=7 2026-10-23T04:31:35.919Z side +1 fired FIB15_R382: FIB15_R236=29167.72; FIB15_R382=29140.02; FIB15_R500=29117.62; FIB15_R618=29095.23; FIB15_R650=29089.16; FIB15_R786=29063.36; FIB15_E1272=29264.11; FIB15_E1618=29329.77; FIB15_E2000=29402.25
k=8 2026-10-23T05:34:53.780Z side -1 fired FIB15_R786: FIB15_R236=29150.52; FIB15_R382=29160.74; FIB15_R500=29169.00; FIB15_R618=29177.26; FIB15_R650=29179.50; FIB15_R786=29189.02; FIB15_E1272=29114.96; FIB15_E1618=29090.74; FIB15_E2000=29064.00
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 7, first known 2026-10-15T23:07:02.367Z, last known 2026-10-16T05:59:58.154Z; rebuilt-from-tape check 7/7/7; threshold values: L=5, thr_contracts=348.266, s_vol=0.871
SIGNALS (raw events of the session: 4 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
0,2026-10-15T23:07:02.367Z,-1,FIB15_R382,30099.53,30035.00,31.25,Y
1,2026-10-15T23:36:18.600Z,-1,FIB15_R236,30074.32,30000.00,31.25,no
4,2026-10-16T03:50:17.816Z,1,FIB15_R236,29981.26,30179.00,31.25,Y
6,2026-10-16T05:59:58.154Z,1,FIB15_R236,30179.24,30191.25,31.25,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,-1,2026-10-15T23:07:04.314Z,30036.75,0.4398,30036.64,2026-10-16T00:22:37.109Z,29976.64,Target,60.0,60.0,60.00,1195.16
4,1,2026-10-16T03:50:18.939Z,30176.25,0.4398,30176.36,2026-10-16T05:59:58.154Z,30191.00,SessionEnd,60.0,60.0,14.64,287.96
```
- check: the independent print-by-print scan equals the sim_slice points for all of 2 trades.
INPUTS (all 7 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-15T23:07:02.367Z,30089.00,30128.00,30027.50,30035.00,31.25,2026-10-15T20:59:59Z,2026-10-15T20:59:00Z,FIB15_R650=30031.32,FIB15_R618=30039.47,-1 FIB15_R382
1,2026-10-15T23:36:18.600Z,30035.25,30064.00,30000.00,30000.00,31.25,2026-10-15T23:07:02Z,2026-10-15T23:07:00Z,FIB15_E1272=29992.91,FIB15_R236=30074.32,-1 FIB15_R236
2,2026-10-16T00:27:58.158Z,29999.50,30052.50,29962.00,29962.25,31.25,2026-10-15T23:36:18Z,2026-10-15T23:36:00Z,FIB15_E1618=29937.46,FIB15_E1272=29992.91,
3,2026-10-16T02:24:37.724Z,29962.00,30103.00,29959.25,30103.00,31.25,2026-10-16T00:27:58Z,2026-10-16T00:27:00Z,FIB15_R382=30097.71,FIB15_R500=30116.62,
4,2026-10-16T03:50:17.816Z,30102.75,30179.00,30074.00,30179.00,31.25,2026-10-16T02:24:37Z,2026-10-16T02:24:00Z,FIB15_R786=30032.54,,+1 FIB15_R236
5,2026-10-16T04:51:35.426Z,30174.50,30211.75,30148.75,30189.25,31.25,2026-10-16T03:50:17Z,2026-10-16T03:50:00Z,FIB15_E1272=30177.08,FIB15_E1618=30236.33,
6,2026-10-16T05:59:58.154Z,30189.50,30225.00,30161.75,30191.25,31.25,2026-10-16T04:51:35Z,2026-10-16T04:51:00Z,FIB15_R236=30179.24,FIB15_E1272=30249.22,+1 FIB15_R236
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-15T23:07:02.367Z side -1 fired FIB15_R382: FIB15_R236=30136.69; FIB15_R382=30099.53; FIB15_R500=30069.50; FIB15_R618=30039.47; FIB15_R650=30031.32; FIB15_R786=29996.71; FIB15_E1272=30265.97; FIB15_E1618=30354.03; FIB15_E2000=30451.25
k=4 2026-10-16T03:50:17.816Z side +1 fired FIB15_R236: FIB15_R236=29981.26; FIB15_R382=29994.87; FIB15_R500=30005.88; FIB15_R618=30016.88; FIB15_R650=30019.86; FIB15_R786=30032.54; FIB15_E1272=29933.89; FIB15_E1618=29901.62; FIB15_E2000=29866.00
```

#### td 20261009 (sess_id 202610090, Asia session, grid week 183)
- bars of the session: 9, first known 2026-10-08T22:57:29.280Z, last known 2026-10-09T05:59:57.199Z; rebuilt-from-tape check 9/9/9; threshold values: L=5, thr_contracts=342.848, s_vol=0.857
SIGNALS (raw events of the session: 3 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u,trade
2,2026-10-09T00:16:39.053Z,-1,FIB15_R236,31030.02,30979.50,24.88,Y
5,2026-10-09T03:09:02.079Z,1,FIB15_R236,30982.43,31056.00,25.25,Y
7,2026-10-09T05:56:18.174Z,1,FIB15_R236,31052.12,31171.00,25.50,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
2,-1,2026-10-09T00:16:40.837Z,30984.75,0.4398,30984.64,2026-10-09T01:42:28.479Z,31045.00,Stop,60.0,60.0,-60.36,-1212.04
5,1,2026-10-09T03:09:03.114Z,31053.50,0.4398,31053.61,2026-10-09T03:55:43.944Z,31113.61,Target,60.0,60.0,60.00,1195.16
7,1,2026-10-09T05:56:19.206Z,31170.25,0.4398,31170.36,2026-10-09T05:59:57.199Z,31158.00,SessionEnd,60.0,60.0,-12.36,-252.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (all 9 bars; level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-08T22:57:29.280Z,31020.50,31072.50,30995.00,31035.00,24.88,2026-10-08T20:59:59Z,2026-10-08T20:59:00Z,FIB15_R786=30994.88,,
1,2026-10-08T23:47:00.924Z,31034.50,31036.50,30990.00,30990.00,24.88,2026-10-08T22:57:29Z,2026-10-08T22:57:00Z,FIB15_R650=30977.16,FIB15_R786=30994.88,
2,2026-10-09T00:16:39.053Z,30990.00,31002.50,30953.00,30979.50,24.88,2026-10-08T23:47:00Z,2026-10-08T23:47:00Z,FIB15_R618=30961.26,FIB15_R500=30982.50,-1 FIB15_R236
3,2026-10-09T01:15:45.564Z,30979.75,31034.00,30966.00,30987.50,25.12,2026-10-09T00:16:39Z,2026-10-09T00:16:00Z,FIB15_R500=30982.50,FIB15_R382=31003.74,
4,2026-10-09T02:02:34.413Z,30986.00,31083.75,30966.50,31079.00,25.25,2026-10-09T01:15:45Z,2026-10-09T01:15:00Z,FIB15_R786=31046.93,,
5,2026-10-09T03:09:02.079Z,31077.75,31089.75,31046.50,31056.00,25.25,2026-10-09T02:02:34Z,2026-10-09T02:02:00Z,FIB15_R786=31019.55,,+1 FIB15_R236
6,2026-10-09T04:52:58.260Z,31056.00,31138.00,31040.50,31103.00,25.50,2026-10-09T03:09:02Z,2026-10-09T03:09:00Z,FIB15_R236=31060.66,FIB15_E1272=31123.27,
7,2026-10-09T05:56:18.174Z,31103.00,31171.00,31102.00,31171.00,25.50,2026-10-09T04:52:58Z,2026-10-09T04:52:00Z,FIB15_R786=31079.21,,+1 FIB15_R236
8,2026-10-09T05:59:57.199Z,31171.25,31177.00,31154.75,31158.25,25.50,2026-10-09T05:56:18Z,2026-10-09T05:56:00Z,FIB15_R786=31129.33,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=2 2026-10-09T00:16:39.053Z side -1 fired FIB15_R236: FIB15_R236=31030.02; FIB15_R382=31003.74; FIB15_R500=30982.50; FIB15_R618=30961.26; FIB15_R650=30955.50; FIB15_R786=30931.02; FIB15_E1272=31121.46; FIB15_E1618=31183.74; FIB15_E2000=31252.50
k=5 2026-10-09T03:09:02.079Z side +1 fired FIB15_R236: FIB15_R236=30982.43; FIB15_R382=30992.29; FIB15_R500=31000.25; FIB15_R618=31008.21; FIB15_R650=31010.38; FIB15_R786=31019.55; FIB15_E1272=30948.14; FIB15_E1618=30924.79; FIB15_E2000=30899.00
k=7 2026-10-09T05:56:18.174Z side +1 fired FIB15_R236: FIB15_R236=31052.12; FIB15_R382=31059.31; FIB15_R500=31065.12; FIB15_R618=31070.94; FIB15_R650=31072.51; FIB15_R786=31079.21; FIB15_E1272=31027.10; FIB15_E1618=31010.06; FIB15_E2000=30991.25
```

## D. EXISTING VERSUS NEW, AND A ROUGH LIST OF WHAT WOULD HAVE TO BE CODED (READING; effort words are my judgement, not an estimate in hours)
**D1. Shared infrastructure for any of these books** (nothing here is specific to one book): (1) a continuous per-row bar series over ALL six session codes with the engine's reset rule at every session boundary and contract roll; (2) the daily scale table (stats_day: trailing-20-row medians of daily volume / prints / range, r0 constants; D8_BAR_DEFS section 2) built nightly, hole handling decided (stored vs hole-filled, as in the NY AM pages); (3) a 1-minute NQ series with roll back-adjustment and the label-day / ISO-week / month bookkeeping (D8Asia.cs already keeps a 1-minute series, READING); (4) the T0 level lookup (previous bar's whole-second close, minute index, 120 s staleness) and the line-at-minute-i convention (uses minutes < i); (5) the generic level_events logic for the variants used (below) with plain u = 5.0 pt or native u (rolling-100 median range shifted one bar, min 20, floor 0.5 pt) - D8Asia.cs has LevelBreakNative (break_native, n = 2) only; (6) session filter, part == 0, one position, flat at the session end, and the book's bracket (fixed points or the unit rule clip(m x u, 10, 120)).

**D2. Bar builders needed on this page:**
- `lbrk`: exists - lbrk_3_40 specified (D8_BAR_DEFS 3.9, D8_BUILD_SPEC L7cc56d99); class LineBreakBuilder in D8Asia.cs. Effort: small (class exists).
- `pnf`: spec only - pnf_7 specified in D8_BUILD_SPEC (L9c2622b0, Asia; stored Asia bars rebuilt identical in D8_ASIA_NEWBOOK_INPUTS.md) and pnf_14 in D8_NYAM_SPEC_L43f0cbfb; NO class for it in D8Asia.cs (class list read): box is a parameter, so pnf_5 / pnf_10 are parameter changes of a builder that is specified but not yet in the strategy file. Effort: medium (new class; kernel is 25 lines of Python).
- `tsf`: NEW - no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision. Effort: medium plus a DECISION on print granularity (see risk flag).

**D3. Level modules needed on this page:**
- `fib15`: zigzag class exists - FibZig (fib15, fib60) in D8Asia.cs and D8_TRIGGER_DEFS 3.7 D text; the generic level_events variants (break_native n=2 exists as LevelBreakNative). Effort: small (FibZig class exists; list the 9 lines).
- `fibr_pd`: NEW - no spec; the fibr_on range-fib text (D8_NYAM_SPEC_L43f0cbfb) is the same construction on the overnight range. Effort: small (18 lines from prior RTH H/L).
- `ob15`: NEW - no spec, no class. Effort: medium (15-min aggregation, ATR14 ewm, order-block state machine with 10-day memory).
- `piv_floor`: lines exist in D8Asia.cs; trigger by parameter - pivot lines (Piv()) and LevelBreakNative (break_native n=2, k) exist for L6b373671; plain break n=1, k=0 and the 16-line set incl. weekly and CPR need checking against pivLines. Effort: small (lines exist in D8Asia.cs; check list incl. weekly and CPR).
- `profile_nodes`: spec exists, no code - D8_NYAM_SPEC_Le4fede95 / D8_TRIGGER_DEFS 3.7 D specify the 10 lines (verified from tape for NY AM); D8Asia.cs has ValueArea only, no HVN/LVN/single-print code. Effort: large (tick volume-at-price accumulator for 5 RTH days, smoothing, HVN/LVN/single prints).
- `vwap`: lines spec only; no VWAP code in D8Asia.cs - break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits). Effort: medium (8 anchored VWAP series on the 1-minute series: day / RTH / London / prior-day / two anchored at the prior RTH extreme minutes / week / month, each with its validity gate).

**D4. Trigger variants needed:** `break`, `break_native`, `false_break`, `retest` (definitions in each book's section 2; the 4 base events break / reject / retest / false_break are all in fd_common.level_events, about 35 lines of Python).

**D5. Per book: what has to be coded on top of D1 (READING)**
- W73585da1 (retest M=10/tol=0.5): bar `pnf_7` [spec only]; module `vwap` [lines spec only; no VWAP code in D8Asia.cs].
- We7eba185 (break n=1/k=0.0): bar `tsf_25_40` [NEW]; module `fibr_pd` [NEW].
- W68089a3e (break_native n=2/k=0.25): bar `tsf_5_400` [NEW]; module `piv_floor` [lines exist in D8Asia.cs; trigger by parameter].
- W0e7037ba (retest M=3/tol=0.5): bar `lbrk_3_40` [exists]; module `profile_nodes` [spec exists, no code].
- Wf5779582 (false_break M=3/k=0.5): bar `tsf_10_60` [NEW]; module `ob15` [NEW].
- W65dc0e76 (break_native n=2/k=0.25): bar `tsf_5_400` [NEW]; module `fib15` [zigzag class exists].

**D6. Match test plan (READING):** run the live builder on the same tape for the three dated sessions of each book and compare (a) the bar closes and known times, (b) the line value of each line at T0 (CSV file), (c) the signal bars and fired lines (SIGNALS block), (d) order time = floor(known) + 2 s for the live engine versus signal known time + 1 s for the grid, (e) the exit reason and, within the stated slippage, the trade prices.

## E. OPEN POINTS FOR LEAD (READING unless marked)
- Print granularity for `tsf` (and any activity bar): the grid used the old per-record tape; D8 uses run-merged prints. A tsf book needs a LEAD decision before coding (build the old record semantics, or re-run the books on a run-merge `tsf`).
- Line files are the engine's stored files (data end 2026-11-13); a coder reproducing them from the tape will meet the 3-day store hole at 2026-10-31..11-04 for profile lines (see D8_NYAM_SPEC_Le4fede95 / B7bfd33b7).
- Near-twins inside the register: `dchg_N` and `kagi_N` rows are the same bars; ob15 / fib15 / piv_floor books on the same tsf row share signals; the register's stack score therefore counts some of these twice (the register's own near-twin rule is by module+variant+side+bar type).
- The 'level at T0' rule and the fact that Asia bar 0 / NY AM bar 0 take their lines and memory from the previous session are engine behaviours an NT8 coder would not guess; they are the main source of mismatch risk.
