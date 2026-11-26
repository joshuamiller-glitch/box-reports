# SPEC_STACK_A5: coding spec pages for the six Asia books of forward-register stack A5 (both-sides LEVEL books; every statement marked SPEC or READING)

Written 2026-11-26 23:39Z by W-SPEC9 (sub-agent of LEAD, not typed by Josh). Order: autopilot/DIRECTIVE_TEST9_2313Z.md part B (relay design under Josh's standing 18:22Z order). RESEARCH / SHADOW ONLY: nothing built, nothing coded, no gate or code change, nothing queued, nothing live, no spend, nothing deleted; the execution server, the live D8Asia.cs and every chart are untouched (D8Asia.cs was only read for its class list). Layout copied from the hand-verified pages D8_NYAM_SPEC_*.md / D8_BUILD_SPEC.md per-book blocks (sections 0 identity, 1 BAR, 2 TRIGGER, 3 signal to order, 4 sides and bracket, 5 other inputs, 6 one position / window / warm-up, 7 what trades, 8 parity data) with a stack overview, an existing-versus-new table and a coding list added.

Marks: **SPEC** = read from code or measured by re-running the engine code in this session; **READING** = my inference (stated as such). Where a source could not be found it says so; nothing is guessed. Book ids and parameters are those of FORWARD_REGISTER_STACKS.md (W-TEST8 section, seed 20261128); the stack is A5 only as a REGISTER object (equal weight, 1 lot per book, bare R0, no stack rules).

## STATUS LINE (read first)
- VERIFIED [SPEC]: for all 6 books the module source was found (th_grid/trig_levels_<name>.py -> triggers_d/lv_<name>.py, line construction in fd_levels.py / fd_levels2.py / fd_profile.py), the bar kernel source was found (th_bars/kernels.py via build_month.py), and the stored grid weekly table of the cell was reproduced exactly by re-running signal_fn and the gcore2x simulator for every held week (6 of 6 books with all held weeks equal). The 3 dated sessions per book were rebuilt from the stored trade tape with the engine bar kernel (all bars identical to the stored bars) and the signals, entries and exits in section 8 are those reproduced trades.
- NOT VERIFIED / OPEN: (a) the live-engine fill (book walk) is not re-run (the table uses the grid engine); (b) line values come from the engine's stored line files (files written 2026-11-17 19:55-23:08Z by fd_levels.py / fd_levels2.py / fd_profile.py from nq1m.npz, data to 2026-11-13; they were NOT re-derived from the tape here except that the 3.7 / L43f0cbfb / Le4fede95 pages already verify vwap, fib15, fibr_on, profile_nodes and piv_floor lines for other dates); (c) no D8 print-rule version exists for the activity bar `tsf` (see flags).
- **RISK FLAG tsf**: 4 of 6 books (Wff6cb74e, W1539c680, W4a911926, W0d8714f7) use the trade-size-filtered volume bar `tsf`, which has no spec page, no class and no run-merge bar set; see section C book text. The price bars of the other books (pnf, lbrk, dchg, kagi, frenko, urenko, swing) are unaffected by the D8 print rule (D8_BUILD_SPEC line 13).
- **FLAG W0778abb1 trades (almost) only on bar 0 of the session** (share 1.00 of its 84 grid trades in the loaded months; mean finite share of its lines in the session 0.01): see its sections 2 and 7.
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
| Wff6cb74e | Asia | tsf_2_700 | ob5 false_break_native M=1,k=0.0 | sym15u | 169-185 | 541, 3.9, 506 | NO | NEW | NEW | tsf print-granularity risk; no longer qualifies at span end |
| W1539c680 | Asia | tsf_10_30 | swsr5 break_native n=3,k=0.5 | plain60/60 | 182-185 | 927, 4.1, 1954 | yes | NEW | NEW | tsf print-granularity risk |
| W87b89d8f | Asia | dchg_10 | vwap retest M=10,tol=0.5 | sym30u | 169-185 | 1072, 4.3, 1144 | yes | spec exists, class by parameter | lines spec only; no VWAP code in D8Asia.cs | - |
| W4a911926 | Asia | tsf_10_60 | ob15 break n=1,k=0.0 | plain60/60 | 182-185 | 314, 4.5, 218 | yes | NEW | NEW | tsf print-granularity risk |
| W0778abb1 | Asia | frenko_40 | fibr_on false_break_native M=1,k=0.0 | fixed30/90 | 169-185 | 401, 4.4, 322 | yes | exists | spec exists | bar-0-only |
| W0d8714f7 | Asia | tsf_10_250 | piv_floor break n=1,k=0.0 | plain60/60 | 156-168; 182-185 | 635, 4.3, 841 | yes | NEW | lines exist in D8Asia.cs; trigger by parameter | tsf print-granularity risk |

Status words: 'exists' = specified on a page AND a class in D8Asia.cs; 'spec only' = specified on a page, no class; 'new' = no page, no class. D8Asia.cs was read only for its class list (READING; its content is not part of this order).

## C. THE BOOKS (one block each; sections 0 to 8)


### BOOK Wff6cb74e (Asia): tsf_2_700 + ob5 level false break native (M 1, k 0.0), BOTH sides, bracket sym15u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 17 of 17 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id Wff6cb74e (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_Wff6cb74e_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/Wff6cb74e.parquet` (1034 events: 577 long, 457 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `tsf_2_700`, module `trig_levels_ob5` (code/th_grid/trig_levels_ob5.py -> triggers_d/lv_ob5.py), variant `false_break_native`, params {"M": 1, "k": 0.0}, bracket `sym15u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/tsf_2_700/trig_levels_ob5.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 541, L6M 964, L3M 772; t 3.9 over 506 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 169..185 (2026-06-28 to 2026-10-24) = 17 held week(s); months in the cell file: 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored -59.81 / mine -59.81 pts, 3 / 3 trades; w182 2026-09-27 stored 276.32 / mine 276.32 pts, 5 / 5 trades; w183 2026-10-04 stored -348.76 / mine -348.76 pts, 5 / 5 trades; w184 2026-10-11 stored -154.66 / mine -154.66 pts, 4 / 4 trades; w185 2026-10-18 stored 211.56 / mine 211.56 pts, 4 / 4 trades (last 5 of 17 held weeks shown; 17 of 17 equal)

**1. BAR**
**BAR** row `tsf_2_700` = TRADE-SIZE-FILTERED VOLUME bar (L = 2, N = 700). [SPEC] build_month.py lines 97-100 with kernel k_cum (kernels.py lines 11-33), mode 0: metric = print size if size >= 2 else 0; threshold thr = 700 x s_vol contracts (s_vol = abs_vol / r0_vol, fixed for the session). Per session key a bar opens at the first print; EVERY print updates o/h/l/c, volume, count (all prints, not only the counted ones; the registry text in th_bars/spec.py says 'OHLC uses only counted prints' but the code does not do that: code governs); cum += metric; the bar CLOSES at the print for which cum >= thr (the closing print stays in the bar, no split); known time = that print's timestamp; the last bar of the session is emitted with part = 1 (known at its last print) and is never a signal bar. Threshold on the sample days: 20261023: L=2, thr_contracts=697.66, s_vol=1.00; 20261016: L=2, thr_contracts=609.47, s_vol=0.87; 20261008: L=2, thr_contracts=599.98, s_vol=0.86. [SPEC] This row is an ACTIVITY (volume-accumulating) bar and the old-engine tape treats every MBO trade record as one print; D8_PRINT_RULE.md section 2 shows that volume-accumulating bars (vol, vsess, tick, dlt, cdr, dib ...) are DIFFERENT between contract level, run merge and the old engine bars (2% to 28% identical for volume-type bars). tsf is NOT in that proof table and has no run-merge version in /mnt/l2/l2vast/_d8spec/bars_c or bars_r. [READING] Because the filter acts on the SIZE of one print (record size >= L lots), merging records of the same price and side into one print (the D8 rule) changes which prints pass the filter and therefore every bar boundary: the grid result for this book is NOT proven for the D8 print stream, and a live bar builder cannot be matched without deciding the print granularity. RISK FLAG.
- [SPEC] Bars per Asia session in the loaded months: median 34 (min 4, max 77, 222 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/tsf_2_700/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 39 stored / 39 rebuilt / 39 identical (o,h,l,c,known_ts,part); td 20261016: 35 stored / 35 rebuilt / 35 identical (o,h,l,c,known_ts,part); td 20261008: 31 stored / 31 rebuilt / 31 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **NEW**: no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_ob5` (th_grid/triggers_d/lv_ob5.py; lines fd_levels2.py lines 98-123 (w = 5)). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 4 lines: OB5_BULHI, OB5_BULLO, OB5_BEARHI, OB5_BEARLO, built exactly as ob15 (same loop, same 1.5 ATR14 impulse rule, same clearing rule) on 5-MINUTE bars (bucket = floor(ts/300 s)); the value of bar j is available from the bar end and held for at most 4320 minutes (3 days).
Variant `false_break_native` (M=1, k=0.0): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (native) = rolling median of (high - low) over the previous 100 bars of THIS book's bar series (bars j-100..j-1, shifted one bar, min_periods 20, floor 0.5 pt; NaN before 20 bars) (fd_common.unit); every tolerance below is x u. With these parameters: M=1, k=0.0 -> k*u = 0.0 x u.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 222 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): OB5_BULHI 0.46, OB5_BULLO 0.46, OB5_BEARHI 0.40, OB5_BEARLO 0.40.
- [READING] Module status: **NEW**: no spec, no class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `sym15u` = unit rule sym15u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `vol (activity bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule sym15u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only (aggregated to 5 minutes).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: Up to 3 days of 5-minute bars of state, ATR14 infinite memory. READING: cold start needs about 3-4 days of 1-minute data.
- [SPEC] Warm-up of the trigger: native u needs 20 earlier bars of the continuous series (rolling 100, shifted). Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; tsf thresholds use s_vol.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 173; share whose signal bar is bar 0 of the session: 0.10; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 5, 11, 21, 67.
- [SPEC] Held weeks only: 77 grid trades; share on bar 0: 0.08; signal-bar index quantiles: 0, 5, 12, 20, 49.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: OB5_BULHI 42, OB5_BEARLO 23, OB5_BEARHI 11, OB5_BULLO 1.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/Wff6cb74e_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610230, Asia session, grid week 185)
- bars of the session: 39, first known 2026-10-22T22:04:06.640Z, last known 2026-10-23T05:59:59.668Z; rebuilt-from-tape check 39/39/39; threshold values: L=2, thr_contracts=697.659, s_vol=0.997
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
17,2026-10-23T01:17:48.326Z,-1,OB5_BULHI,29092.50,29066.75,21.50,Y
18,2026-10-23T01:24:03.743Z,1,OB5_BULHI,29092.50,29128.50,21.50,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
17,-1,2026-10-23T01:17:49.331Z,29068.75,0.4398,29068.64,2026-10-23T01:28:06.798Z,29189.25,Stop,120.0,120.0,-120.61,-2417.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 39 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-22T22:04:06.640Z,29116.50,29148.00,29090.00,29142.50,20.00,2026-10-22T20:59:58Z,2026-10-22T20:59:00Z,,,
1,2026-10-22T22:18:23.618Z,29144.25,29149.25,29114.75,29124.00,20.00,2026-10-22T22:04:06Z,2026-10-22T22:04:00Z,,,
2,2026-10-22T22:30:16.260Z,29124.50,29165.75,29117.50,29132.50,20.25,2026-10-22T22:18:23Z,2026-10-22T22:18:00Z,,,
3,2026-10-22T22:43:02.035Z,29132.25,29137.00,29103.50,29123.25,20.25,2026-10-22T22:30:16Z,2026-10-22T22:30:00Z,,,
4,2026-10-22T23:04:01.617Z,29121.50,29140.25,29087.50,29088.75,20.75,2026-10-22T22:43:02Z,2026-10-22T22:43:00Z,,,
5,2026-10-22T23:25:02.103Z,29090.50,29130.25,29074.50,29094.00,20.75,2026-10-22T23:04:01Z,2026-10-22T23:04:00Z,,,
6,2026-10-22T23:42:29.345Z,29094.25,29094.50,29042.25,29045.50,20.88,2026-10-22T23:25:02Z,2026-10-22T23:25:00Z,,,
7,2026-10-22T23:58:06.426Z,29045.25,29097.50,29044.50,29077.50,21.00,2026-10-22T23:42:29Z,2026-10-22T23:42:00Z,,,
8,2026-10-23T00:05:33.853Z,29078.25,29100.25,29037.00,29088.50,21.00,2026-10-22T23:58:06Z,2026-10-22T23:58:00Z,,,
9,2026-10-23T00:12:12.103Z,29088.75,29107.75,29022.75,29106.00,21.25,2026-10-23T00:05:33Z,2026-10-23T00:05:00Z,,,
10,2026-10-23T00:18:07.864Z,29106.25,29136.50,29085.50,29121.00,21.25,2026-10-23T00:12:12Z,2026-10-23T00:12:00Z,,,
11,2026-10-23T00:29:47.515Z,29123.50,29132.50,29069.00,29103.75,21.25,2026-10-23T00:18:07Z,2026-10-23T00:18:00Z,OB5_BULHI=29092.50,,
12,2026-10-23T00:43:29.588Z,29104.25,29142.00,29091.50,29132.50,21.50,2026-10-23T00:29:47Z,2026-10-23T00:29:00Z,OB5_BULHI=29092.50,,
13,2026-10-23T00:48:53.353Z,29132.50,29187.75,29120.00,29183.25,21.50,2026-10-23T00:43:29Z,2026-10-23T00:43:00Z,OB5_BULHI=29092.50,,
14,2026-10-23T00:57:51.893Z,29183.50,29198.50,29162.00,29193.50,21.50,2026-10-23T00:48:53Z,2026-10-23T00:48:00Z,OB5_BULHI=29092.50,,
15,2026-10-23T01:06:03.701Z,29193.75,29197.00,29139.00,29147.50,21.50,2026-10-23T00:57:51Z,2026-10-23T00:57:00Z,OB5_BULHI=29092.50,,
16,2026-10-23T01:13:19.625Z,29148.00,29151.25,29113.00,29118.00,21.50,2026-10-23T01:06:03Z,2026-10-23T01:06:00Z,OB5_BULHI=29092.50,,
17,2026-10-23T01:17:48.326Z,29118.75,29121.00,29056.75,29066.75,21.50,2026-10-23T01:13:19Z,2026-10-23T01:13:00Z,OB5_BULLO=29038.50,OB5_BULHI=29092.50,-1 OB5_BULHI
18,2026-10-23T01:24:03.743Z,29067.25,29158.25,29067.25,29128.50,21.50,2026-10-23T01:17:48Z,2026-10-23T01:17:00Z,OB5_BULHI=29092.50,,+1 OB5_BULHI
19,2026-10-23T01:30:57.671Z,29128.25,29200.00,29122.00,29158.00,21.88,2026-10-23T01:24:03Z,2026-10-23T01:24:00Z,OB5_BULHI=29092.50,,
20,2026-10-23T01:42:23.016Z,29158.00,29194.00,29129.25,29192.00,22.88,2026-10-23T01:30:57Z,2026-10-23T01:30:00Z,OB5_BULHI=29092.50,,
21,2026-10-23T01:47:53.603Z,29192.75,29212.50,29188.00,29203.25,22.88,2026-10-23T01:42:23Z,2026-10-23T01:42:00Z,OB5_BULHI=29092.50,,
22,2026-10-23T01:56:50.208Z,29203.50,29206.00,29113.00,29120.00,23.75,2026-10-23T01:47:53Z,2026-10-23T01:47:00Z,OB5_BULHI=29092.50,,
23,2026-10-23T02:00:14.857Z,29120.25,29131.75,29106.25,29107.00,23.75,2026-10-23T01:56:50Z,2026-10-23T01:56:00Z,OB5_BULHI=29092.50,,
24,2026-10-23T02:14:25.261Z,29106.75,29141.75,29089.00,29131.25,23.75,2026-10-23T02:00:14Z,2026-10-23T02:00:00Z,OB5_BULHI=29092.50,,
25,2026-10-23T02:24:22.527Z,29131.50,29164.00,29108.50,29163.25,24.00,2026-10-23T02:14:25Z,2026-10-23T02:14:00Z,OB5_BULHI=29092.50,,
26,2026-10-23T02:32:57.404Z,29163.50,29181.25,29138.25,29171.75,24.12,2026-10-23T02:24:22Z,2026-10-23T02:24:00Z,OB5_BULHI=29092.50,,
27,2026-10-23T02:48:21.413Z,29171.50,29204.00,29170.25,29174.25,24.38,2026-10-23T02:32:57Z,2026-10-23T02:32:00Z,OB5_BULHI=29092.50,,
28,2026-10-23T03:10:06.298Z,29174.00,29203.25,29151.25,29151.25,24.38,2026-10-23T02:48:21Z,2026-10-23T02:48:00Z,OB5_BULHI=29092.50,,
29,2026-10-23T03:25:28.879Z,29151.00,29178.25,29134.00,29155.50,25.00,2026-10-23T03:10:06Z,2026-10-23T03:10:00Z,OB5_BULHI=29092.50,,
30,2026-10-23T03:40:38.472Z,29156.25,29195.50,29146.75,29164.75,25.50,2026-10-23T03:25:28Z,2026-10-23T03:25:00Z,OB5_BULHI=29092.50,,
31,2026-10-23T04:06:16.319Z,29164.50,29192.00,29151.00,29182.25,25.62,2026-10-23T03:40:38Z,2026-10-23T03:40:00Z,OB5_BULHI=29092.50,,
32,2026-10-23T04:29:35.629Z,29182.75,29193.25,29138.50,29153.75,26.25,2026-10-23T04:06:16Z,2026-10-23T04:06:00Z,OB5_BULHI=29092.50,,
33,2026-10-23T04:53:30.591Z,29153.75,29177.00,29118.25,29134.75,26.25,2026-10-23T04:29:35Z,2026-10-23T04:29:00Z,OB5_BULHI=29092.50,,
34,2026-10-23T05:16:37.597Z,29135.25,29154.75,29117.50,29131.25,26.25,2026-10-23T04:53:30Z,2026-10-23T04:53:00Z,OB5_BULHI=29092.50,,
35,2026-10-23T05:33:18.544Z,29128.75,29153.25,29105.50,29145.50,26.25,2026-10-23T05:16:37Z,2026-10-23T05:16:00Z,OB5_BULHI=29092.50,,
36,2026-10-23T05:39:17.407Z,29145.50,29163.25,29123.50,29154.25,26.88,2026-10-23T05:33:18Z,2026-10-23T05:33:00Z,OB5_BULHI=29092.50,,
37,2026-10-23T05:52:12.032Z,29154.75,29188.25,29147.50,29153.00,26.88,2026-10-23T05:39:17Z,2026-10-23T05:39:00Z,OB5_BULHI=29092.50,,
38,2026-10-23T05:59:59.668Z,29152.75,29156.25,29131.25,29135.00,27.12,2026-10-23T05:52:12Z,2026-10-23T05:52:00Z,OB5_BULHI=29092.50,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=17 2026-10-23T01:17:48.326Z side -1 fired OB5_BULHI: OB5_BULHI=29092.50; OB5_BULLO=29038.50
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 35, first known 2026-10-15T22:17:52.484Z, last known 2026-10-16T05:59:58.154Z; rebuilt-from-tape check 35/35/35; threshold values: L=2, thr_contracts=609.466, s_vol=0.871
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
23,2026-10-16T03:45:49.934Z,1,OB5_BEARLO,30128.75,30129.00,17.00,Y
24,2026-10-16T03:50:17.816Z,1,OB5_BEARHI,30134.25,30172.25,17.25,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
23,1,2026-10-16T03:45:51.256Z,30129.50,0.4398,30129.61,2026-10-16T05:59:58.154Z,30191.00,SessionEnd,120.0,120.0,61.39,1222.96
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 35 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-15T22:17:52.484Z,30089.00,30128.00,30088.00,30119.25,14.50,2026-10-15T20:59:59Z,2026-10-15T20:59:00Z,,,
1,2026-10-15T22:36:01.835Z,30119.50,30124.00,30070.75,30071.75,14.50,2026-10-15T22:17:52Z,2026-10-15T22:17:00Z,,OB5_BEARLO=30128.75,
2,2026-10-15T23:00:22.711Z,30072.50,30092.50,30063.00,30065.50,14.50,2026-10-15T22:36:01Z,2026-10-15T22:36:00Z,,OB5_BEARLO=30128.75,
3,2026-10-15T23:07:42.076Z,30063.50,30067.00,30027.50,30048.25,15.12,2026-10-15T23:00:22Z,2026-10-15T23:00:00Z,,OB5_BEARLO=30128.75,
4,2026-10-15T23:20:22.853Z,30048.00,30064.00,30022.50,30022.50,15.12,2026-10-15T23:07:42Z,2026-10-15T23:07:00Z,,OB5_BEARLO=30128.75,
5,2026-10-15T23:36:09.810Z,30022.25,30027.00,30001.75,30002.25,15.12,2026-10-15T23:20:22Z,2026-10-15T23:20:00Z,,OB5_BEARLO=30128.75,
6,2026-10-15T23:45:48.971Z,30002.00,30007.25,29982.75,29993.50,15.12,2026-10-15T23:36:09Z,2026-10-15T23:36:00Z,,OB5_BEARLO=30128.75,
7,2026-10-16T00:00:28.925Z,29993.75,30003.25,29977.50,29997.00,15.38,2026-10-15T23:45:48Z,2026-10-15T23:45:00Z,,OB5_BEARLO=30128.75,
8,2026-10-16T00:05:52.066Z,29996.25,30023.50,29990.50,30021.25,15.38,2026-10-16T00:00:28Z,2026-10-16T00:00:00Z,,OB5_BEARLO=30128.75,
9,2026-10-16T00:16:58.614Z,30021.75,30052.50,30017.00,30020.00,15.50,2026-10-16T00:05:52Z,2026-10-16T00:05:00Z,,OB5_BEARLO=30128.75,
10,2026-10-16T00:23:00.048Z,30019.50,30028.75,29969.00,29983.25,15.50,2026-10-16T00:16:58Z,2026-10-16T00:16:00Z,,OB5_BEARLO=30128.75,
11,2026-10-16T00:29:03.096Z,29983.50,29995.50,29959.25,29981.75,15.50,2026-10-16T00:23:00Z,2026-10-16T00:23:00Z,,OB5_BEARLO=30128.75,
12,2026-10-16T00:38:35.401Z,29981.75,30024.00,29977.50,30018.75,15.50,2026-10-16T00:29:03Z,2026-10-16T00:29:00Z,,OB5_BEARLO=30128.75,
13,2026-10-16T00:51:44.565Z,30019.00,30052.25,30005.25,30052.00,15.50,2026-10-16T00:38:35Z,2026-10-16T00:38:00Z,,OB5_BEARLO=30128.75,
14,2026-10-16T01:02:19.381Z,30052.25,30067.00,30030.50,30066.25,15.50,2026-10-16T00:51:44Z,2026-10-16T00:51:00Z,,OB5_BEARLO=30128.75,
15,2026-10-16T01:20:49.818Z,30066.25,30077.75,30047.75,30065.50,15.75,2026-10-16T01:02:19Z,2026-10-16T01:02:00Z,,OB5_BEARLO=30128.75,
16,2026-10-16T01:36:21.878Z,30064.50,30076.50,30037.25,30074.25,16.00,2026-10-16T01:20:49Z,2026-10-16T01:20:00Z,,OB5_BEARLO=30128.75,
17,2026-10-16T01:52:53.479Z,30074.50,30091.75,30044.50,30070.25,16.00,2026-10-16T01:36:21Z,2026-10-16T01:36:00Z,,OB5_BEARLO=30128.75,
18,2026-10-16T02:10:00.354Z,30069.50,30078.00,30043.25,30078.00,16.25,2026-10-16T01:52:53Z,2026-10-16T01:52:00Z,,OB5_BEARLO=30128.75,
19,2026-10-16T02:26:25.184Z,30078.25,30106.00,30069.00,30099.00,16.62,2026-10-16T02:10:00Z,2026-10-16T02:10:00Z,,OB5_BEARLO=30128.75,
20,2026-10-16T02:38:54.997Z,30099.25,30129.75,30094.75,30125.00,16.75,2026-10-16T02:26:25Z,2026-10-16T02:26:00Z,,OB5_BEARLO=30128.75,
21,2026-10-16T03:02:20.686Z,30124.75,30126.75,30087.25,30108.75,16.75,2026-10-16T02:38:54Z,2026-10-16T02:38:00Z,,OB5_BEARLO=30128.75,
22,2026-10-16T03:30:31.916Z,30109.25,30130.50,30095.00,30103.25,16.75,2026-10-16T03:02:20Z,2026-10-16T03:02:00Z,,OB5_BEARLO=30128.75,
23,2026-10-16T03:45:49.934Z,30103.00,30129.00,30074.00,30129.00,17.00,2026-10-16T03:30:31Z,2026-10-16T03:30:00Z,OB5_BEARLO=30128.75,OB5_BEARHI=30134.25,+1 OB5_BEARLO
24,2026-10-16T03:50:17.816Z,30129.25,30172.25,30129.00,30172.25,17.25,2026-10-16T03:45:49Z,2026-10-16T03:45:00Z,OB5_BEARHI=30134.25,,+1 OB5_BEARHI
25,2026-10-16T03:51:56.125Z,30172.50,30211.75,30164.75,30197.25,17.88,2026-10-16T03:50:17Z,2026-10-16T03:50:00Z,OB5_BULHI=30105.25,,
26,2026-10-16T03:55:22.794Z,30197.00,30206.25,30170.75,30200.00,18.62,2026-10-16T03:51:56Z,2026-10-16T03:51:00Z,OB5_BULHI=30105.25,,
27,2026-10-16T04:08:03.397Z,30200.25,30207.25,30185.75,30190.00,18.62,2026-10-16T03:55:22Z,2026-10-16T03:55:00Z,OB5_BULHI=30105.25,,
28,2026-10-16T04:14:02.240Z,30189.75,30190.50,30148.75,30169.00,18.75,2026-10-16T04:08:03Z,2026-10-16T04:08:00Z,OB5_BULHI=30105.25,,
29,2026-10-16T04:27:41.353Z,30169.25,30198.00,30149.50,30186.25,18.75,2026-10-16T04:14:02Z,2026-10-16T04:14:00Z,OB5_BULHI=30105.25,,
30,2026-10-16T04:42:35.722Z,30186.75,30195.00,30162.75,30189.00,18.75,2026-10-16T04:27:41Z,2026-10-16T04:27:00Z,OB5_BULHI=30105.25,,
31,2026-10-16T05:01:55.733Z,30188.25,30220.00,30183.50,30212.75,19.00,2026-10-16T04:42:35Z,2026-10-16T04:42:00Z,OB5_BULHI=30105.25,,
32,2026-10-16T05:17:45.596Z,30212.25,30225.00,30189.25,30202.75,19.00,2026-10-16T05:01:55Z,2026-10-16T05:01:00Z,OB5_BULHI=30105.25,,
33,2026-10-16T05:37:51.001Z,30202.50,30205.00,30164.25,30164.25,19.75,2026-10-16T05:17:45Z,2026-10-16T05:17:00Z,OB5_BULHI=30105.25,,
34,2026-10-16T05:59:58.154Z,30164.00,30207.75,30161.75,30191.25,20.50,2026-10-16T05:37:51Z,2026-10-16T05:37:00Z,OB5_BULHI=30105.25,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=23 2026-10-16T03:45:49.934Z side +1 fired OB5_BEARLO: OB5_BEARHI=30134.25; OB5_BEARLO=30128.75
```

#### td 20261008 (sess_id 202610080, Asia session, grid week 183)
- bars of the session: 31, first known 2026-10-07T22:12:34.399Z, last known 2026-10-08T05:59:59.026Z; rebuilt-from-tape check 31/31/31; threshold values: L=2, thr_contracts=599.984, s_vol=0.857
SIGNALS (raw events of the session: 4 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
17,2026-10-08T02:36:36.771Z,1,OB5_BEARLO,31446.00,31452.75,12.38,Y
27,2026-10-08T05:11:05.586Z,1,OB5_BEARHI,31393.75,31407.50,13.50,no
29,2026-10-08T05:53:04.128Z,-1,OB5_BULHI,31370.75,31350.50,14.12,no
30,2026-10-08T05:59:59.026Z,-1,OB5_BULLO,31349.50,31325.00,14.12,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
17,1,2026-10-08T02:36:37.893Z,31451.25,0.4398,31451.36,2026-10-08T05:56:14.762Z,31331.00,Stop,120.0,120.0,-120.36,-2412.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 31 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-07T22:12:34.399Z,31403.00,31438.50,31403.00,31429.75,11.75,2026-10-07T20:59:58Z,2026-10-07T20:59:00Z,,,
1,2026-10-07T22:35:06.941Z,31429.50,31446.75,31419.50,31434.25,11.75,2026-10-07T22:12:34Z,2026-10-07T22:12:00Z,,,
2,2026-10-07T23:00:53.981Z,31434.25,31443.00,31423.25,31431.00,11.75,2026-10-07T22:35:06Z,2026-10-07T22:35:00Z,,,
3,2026-10-07T23:16:40.003Z,31430.75,31454.50,31428.75,31446.50,11.75,2026-10-07T23:00:53Z,2026-10-07T23:00:00Z,,,
4,2026-10-07T23:43:22.230Z,31447.00,31459.00,31443.00,31449.50,11.88,2026-10-07T23:16:40Z,2026-10-07T23:16:00Z,,,
5,2026-10-07T23:48:21.031Z,31449.25,31452.00,31426.75,31433.00,11.88,2026-10-07T23:43:22Z,2026-10-07T23:43:00Z,,,
6,2026-10-08T00:06:37.116Z,31433.25,31440.00,31414.00,31415.50,11.88,2026-10-07T23:48:21Z,2026-10-07T23:48:00Z,,,
7,2026-10-08T00:16:24.199Z,31415.75,31421.25,31399.00,31408.50,11.88,2026-10-08T00:06:37Z,2026-10-08T00:06:00Z,,OB5_BEARLO=31446.00,
8,2026-10-08T00:31:17.754Z,31408.50,31427.75,31387.00,31394.00,12.00,2026-10-08T00:16:24Z,2026-10-08T00:16:00Z,,OB5_BEARLO=31446.00,
9,2026-10-08T00:44:12.860Z,31394.25,31397.75,31377.50,31382.00,12.00,2026-10-08T00:31:17Z,2026-10-08T00:31:00Z,,OB5_BEARLO=31446.00,
10,2026-10-08T00:56:48.523Z,31382.50,31390.25,31372.25,31385.50,12.00,2026-10-08T00:44:12Z,2026-10-08T00:44:00Z,,OB5_BEARLO=31446.00,
11,2026-10-08T01:08:29.192Z,31386.00,31409.50,31377.50,31402.00,12.00,2026-10-08T00:56:48Z,2026-10-08T00:56:00Z,,OB5_BEARLO=31446.00,
12,2026-10-08T01:21:27.145Z,31401.25,31417.50,31384.25,31409.00,12.12,2026-10-08T01:08:29Z,2026-10-08T01:08:00Z,,OB5_BEARLO=31446.00,
13,2026-10-08T01:33:47.453Z,31410.50,31434.75,31391.50,31433.00,12.12,2026-10-08T01:21:27Z,2026-10-08T01:21:00Z,,OB5_BEARLO=31446.00,
14,2026-10-08T01:40:31.907Z,31433.00,31447.00,31432.75,31440.75,12.38,2026-10-08T01:33:47Z,2026-10-08T01:33:00Z,,OB5_BEARLO=31446.00,
15,2026-10-08T01:57:06.909Z,31440.50,31449.00,31431.25,31445.50,12.38,2026-10-08T01:40:31Z,2026-10-08T01:40:00Z,,OB5_BEARLO=31446.00,
16,2026-10-08T02:24:25.263Z,31445.50,31450.50,31429.75,31443.25,12.38,2026-10-08T01:57:06Z,2026-10-08T01:57:00Z,,OB5_BEARLO=31446.00,
17,2026-10-08T02:36:36.771Z,31443.00,31466.00,31438.75,31452.75,12.38,2026-10-08T02:24:25Z,2026-10-08T02:24:00Z,OB5_BEARLO=31446.00,OB5_BEARHI=31456.75,+1 OB5_BEARLO
18,2026-10-08T02:50:45.818Z,31453.00,31453.00,31429.25,31429.25,12.50,2026-10-08T02:36:36Z,2026-10-08T02:36:00Z,,OB5_BULLO=31438.75,
19,2026-10-08T03:00:40.221Z,31429.25,31430.25,31406.50,31420.50,12.50,2026-10-08T02:50:45Z,2026-10-08T02:50:00Z,,,
20,2026-10-08T03:15:47.769Z,31420.75,31421.50,31387.75,31387.75,12.50,2026-10-08T03:00:40Z,2026-10-08T03:00:00Z,,,
21,2026-10-08T03:27:08.409Z,31387.50,31412.25,31377.00,31410.75,12.50,2026-10-08T03:15:47Z,2026-10-08T03:15:00Z,,,
22,2026-10-08T03:43:49.387Z,31410.25,31418.50,31375.50,31381.50,12.50,2026-10-08T03:27:08Z,2026-10-08T03:27:00Z,,,
23,2026-10-08T03:53:21.893Z,31382.25,31393.75,31361.25,31361.50,12.50,2026-10-08T03:43:49Z,2026-10-08T03:43:00Z,,,
24,2026-10-08T04:03:28.001Z,31361.25,31366.50,31349.50,31366.50,12.75,2026-10-08T03:53:21Z,2026-10-08T03:53:00Z,,,
25,2026-10-08T04:27:04.142Z,31366.75,31380.75,31349.50,31380.75,12.75,2026-10-08T04:03:28Z,2026-10-08T04:03:00Z,OB5_BEARLO=31377.25,OB5_BEARHI=31393.75,
26,2026-10-08T04:46:53.298Z,31381.00,31401.75,31379.00,31390.75,13.12,2026-10-08T04:27:04Z,2026-10-08T04:27:00Z,OB5_BEARLO=31377.25,OB5_BEARHI=31393.75,
27,2026-10-08T05:11:05.586Z,31390.00,31407.50,31380.50,31407.50,13.50,2026-10-08T04:46:53Z,2026-10-08T04:46:00Z,OB5_BEARHI=31393.75,,+1 OB5_BEARHI
28,2026-10-08T05:34:13.085Z,31407.75,31411.25,31376.75,31400.00,13.88,2026-10-08T05:11:05Z,2026-10-08T05:11:00Z,OB5_BULHI=31370.75,,
29,2026-10-08T05:53:04.128Z,31400.25,31406.50,31340.50,31350.50,14.12,2026-10-08T05:34:13Z,2026-10-08T05:34:00Z,OB5_BULLO=31349.50,OB5_BULHI=31370.75,-1 OB5_BULHI
30,2026-10-08T05:59:59.026Z,31350.25,31350.50,31321.00,31325.00,14.12,2026-10-08T05:53:04Z,2026-10-08T05:53:00Z,,OB5_BULLO=31349.50,-1 OB5_BULLO
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=17 2026-10-08T02:36:36.771Z side +1 fired OB5_BEARLO: OB5_BEARHI=31456.75; OB5_BEARLO=31446.00
```

### BOOK W1539c680 (Asia): tsf_10_30 + swsr5 level break native (n 3, k 0.5), BOTH sides, bracket plain60/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W1539c680 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W1539c680_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W1539c680.parquet` (5414 events: 2854 long, 2560 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `tsf_10_30`, module `trig_levels_swsr5` (code/th_grid/trig_levels_swsr5.py -> triggers_d/lv_swsr5.py), variant `break_native`, params {"n": 3, "k": 0.5}, bracket `plain60/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/tsf_10_30/trig_levels_swsr5.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 927, L6M 1936, L3M 1437; t 4.1 over 1954 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 182..185 (2026-09-27 to 2026-10-24) = 4 held week(s); months in the cell file: 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w182 2026-09-27 stored 283.22 / mine 283.22 pts, 23 / 23 trades; w183 2026-10-04 stored -239.91 / mine -239.91 pts, 10 / 10 trades; w184 2026-10-11 stored 115.71 / mine 115.71 pts, 21 / 21 trades; w185 2026-10-18 stored 48.21 / mine 48.21 pts, 28 / 28 trades

**1. BAR**
**BAR** row `tsf_10_30` = TRADE-SIZE-FILTERED VOLUME bar (L = 10, N = 30). [SPEC] build_month.py lines 97-100 with kernel k_cum (kernels.py lines 11-33), mode 0: metric = print size if size >= 10 else 0; threshold thr = 30 x s_vol contracts (s_vol = abs_vol / r0_vol, fixed for the session). Per session key a bar opens at the first print; EVERY print updates o/h/l/c, volume, count (all prints, not only the counted ones; the registry text in th_bars/spec.py says 'OHLC uses only counted prints' but the code does not do that: code governs); cum += metric; the bar CLOSES at the print for which cum >= thr (the closing print stays in the bar, no split); known time = that print's timestamp; the last bar of the session is emitted with part = 1 (known at its last print) and is never a signal bar. Threshold on the sample days: 20261023: L=10, thr_contracts=29.90, s_vol=1.00; 20261016: L=10, thr_contracts=26.12, s_vol=0.87; 20261009: L=10, thr_contracts=25.71, s_vol=0.86. [SPEC] This row is an ACTIVITY (volume-accumulating) bar and the old-engine tape treats every MBO trade record as one print; D8_PRINT_RULE.md section 2 shows that volume-accumulating bars (vol, vsess, tick, dlt, cdr, dib ...) are DIFFERENT between contract level, run merge and the old engine bars (2% to 28% identical for volume-type bars). tsf is NOT in that proof table and has no run-merge version in /mnt/l2/l2vast/_d8spec/bars_c or bars_r. [READING] Because the filter acts on the SIZE of one print (record size >= L lots), merging records of the same price and side into one print (the D8 rule) changes which prints pass the filter and therefore every bar boundary: the grid result for this book is NOT proven for the D8 print stream, and a live bar builder cannot be matched without deciding the print granularity. RISK FLAG.
- [SPEC] Bars per Asia session in the loaded months: median 30 (min 8, max 86, 159 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/tsf_10_30/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 49 stored / 49 rebuilt / 49 identical (o,h,l,c,known_ts,part); td 20261016: 25 stored / 25 rebuilt / 25 identical (o,h,l,c,known_ts,part); td 20261009: 24 stored / 24 rebuilt / 24 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **NEW**: no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_swsr5` (th_grid/triggers_d/lv_swsr5.py; lines fd_levels2.py lines 61-88 (w = 5)). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 8 lines in this list order: SW5_H, SW5_L, SW5_HB, SW5_LB, SW5_EQH, SW5_EQL, SW5_EQH3, SW5_EQL3, on 5-MINUTE bars (bucket floor(ts/300 s); fractal pivots strength k = 2 confirmed at the END of bar j+2; every line held 4320 minutes (3 days) from its availability).
- SW5_H / SW5_L: price of the latest confirmed swing high / swing low.
- SW5_HB / SW5_LB (polarity flip): swing highs that a later 5-minute CLOSE broke (first close above the pivot price within 3000 bars) / swing lows broken by a close below; value = the pivot price, available from the end of the breaking bar; the latest such level.
- SW5_EQH / SW5_EQL: equal highs / lows: a pivot with at least 1 earlier same-type pivot among the previous 6 within 0.25 x ATR14 (5-min, ewm alpha 1/14 adjust False) of it; value = max (highs) / min (lows) of the cluster; SW5_EQH3 / SW5_EQL3: at least 2 earlier.
Variant `break_native` (n=3, k=0.5): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (native) = rolling median of (high - low) over the previous 100 bars of THIS book's bar series (bars j-100..j-1, shifted one bar, min_periods 20, floor 0.5 pt; NaN before 20 bars) (fd_common.unit); every tolerance below is x u. With these parameters: n=3, k=0.5 -> k*u = 0.5 x u.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 159 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): SW5_H 1.00, SW5_L 1.00, SW5_HB 1.00, SW5_LB 1.00, SW5_EQH 0.33, SW5_EQL 0.33, SW5_EQH3 0.09, SW5_EQL3 0.08.
- [READING] Module status: **NEW**: no spec, no class.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `plain60/60` = stop 60 pts / target 60 pts, fixed (no unit rule); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `vol (activity bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 60 pts / target 60 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only (aggregated to 5 minutes).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: State of the last 7 pivots and up to 3000 5-minute bars for break detection, ATR14 infinite memory. READING: cold start needs about 3-4 days of 1-minute data.
- [SPEC] Warm-up of the trigger: native u needs 20 earlier bars of the continuous series (rolling 100, shifted). Memory M / hold n of the variant: 3 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; tsf thresholds use s_vol.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 638; share whose signal bar is bar 0 of the session: 0.02; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 5, 13, 26, 82.
- [SPEC] Held weeks only: 82 grid trades; share on bar 0: 0.04; signal-bar index quantiles: 0, 5.25, 16, 27.75, 80.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: SW5_H 27, SW5_L 23, SW5_LB 18, SW5_HB 14.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W1539c680_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610230, Asia session, grid week 185)
- bars of the session: 49, first known 2026-10-22T22:00:15.892Z, last known 2026-10-23T05:59:59.668Z; rebuilt-from-tape check 49/49/49; threshold values: L=10, thr_contracts=29.900, s_vol=0.997
SIGNALS (raw events of the session: 13 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
5,2026-10-22T22:25:07.557Z,1,SW5_LB,29114.50,29160.00,13.75,Y
8,2026-10-22T23:33:00.148Z,-1,SW5_H,29140.25,29060.00,14.25,Y
9,2026-10-22T23:36:48.374Z,-1,SW5_L,29103.50,29057.50,14.38,no
12,2026-10-23T00:48:34.308Z,1,SW5_L,29069.00,29187.75,14.38,Y
14,2026-10-23T00:55:16.766Z,1,SW5_H,29136.50,29163.75,14.38,no
17,2026-10-23T01:12:29.405Z,-1,SW5_HB,29165.75,29120.00,15.12,Y
21,2026-10-23T01:47:14.561Z,1,SW5_HB,29165.75,29206.50,15.12,Y
24,2026-10-23T01:59:14.768Z,-1,SW5_H,29200.00,29116.50,16.00,Y
39,2026-10-23T05:30:34.379Z,-1,SW5_HB,29178.25,29133.75,16.75,Y
40,2026-10-23T05:33:25.958Z,-1,SW5_H,29154.75,29140.00,16.75,no
41,2026-10-23T05:37:39.248Z,1,SW5_L,29117.50,29141.50,16.75,no
44,2026-10-23T05:54:41.809Z,1,SW5_LB,29134.00,29148.50,18.50,no
47,2026-10-23T05:59:31.923Z,-1,SW5_HB,29154.75,29138.00,18.50,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
5,1,2026-10-22T22:25:08.637Z,29157.75,0.4398,29157.86,2026-10-22T23:01:08.688Z,29097.50,Stop,60.0,60.0,-60.36,-1212.04
8,-1,2026-10-22T23:33:01.223Z,29058.25,0.4398,29058.14,2026-10-23T00:14:25.524Z,29118.50,Stop,60.0,60.0,-60.36,-1212.04
12,1,2026-10-23T00:48:35.657Z,29184.50,0.4398,29184.61,2026-10-23T01:11:33.204Z,29124.25,Stop,60.0,60.0,-60.36,-1212.04
17,-1,2026-10-23T01:12:30.466Z,29120.00,0.4398,29119.89,2026-10-23T01:17:37.417Z,29059.89,Target,60.0,60.0,60.00,1195.16
21,1,2026-10-23T01:47:16.155Z,29202.75,0.4398,29202.86,2026-10-23T01:53:30.029Z,29142.50,Stop,60.0,60.0,-60.36,-1212.04
24,-1,2026-10-23T01:59:15.803Z,29115.75,0.4398,29115.64,2026-10-23T02:31:54.233Z,29176.00,Stop,60.0,60.0,-60.36,-1212.04
39,-1,2026-10-23T05:30:36.387Z,29133.75,0.4398,29133.64,2026-10-23T05:59:59.668Z,29135.25,SessionEnd,60.0,60.0,-1.61,-37.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 7 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 34 of 49 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-22T22:00:15.892Z,29116.50,29128.00,29090.75,29093.25,12.62,2026-10-22T20:59:58Z,2026-10-22T20:59:00Z,,SW5_L=29111.25,
1,2026-10-22T22:00:46.313Z,29093.00,29115.00,29090.00,29115.00,12.62,2026-10-22T22:00:15Z,2026-10-22T22:00:00Z,SW5_LB=29114.50,SW5_HB=29155.00,
2,2026-10-22T22:00:46.313Z,29115.00,29115.00,29115.00,29115.00,12.62,2026-10-22T22:00:46Z,2026-10-22T22:00:00Z,SW5_LB=29114.50,SW5_HB=29155.00,
3,2026-10-22T22:05:51.283Z,29115.00,29148.75,29114.00,29128.00,12.62,2026-10-22T22:00:46Z,2026-10-22T22:00:00Z,SW5_LB=29114.50,SW5_HB=29155.00,
4,2026-10-22T22:17:47.443Z,29128.75,29149.25,29115.50,29125.00,13.25,2026-10-22T22:05:51Z,2026-10-22T22:05:00Z,SW5_LB=29114.50,SW5_HB=29155.00,
5,2026-10-22T22:25:07.557Z,29125.00,29165.75,29117.50,29160.00,13.75,2026-10-22T22:17:47Z,2026-10-22T22:17:00Z,SW5_HB=29155.00,SW5_H=29215.00,+1 SW5_LB
6,2026-10-22T22:43:56.000Z,29160.00,29162.00,29103.50,29118.75,14.00,2026-10-22T22:25:07Z,2026-10-22T22:25:00Z,SW5_LB=29114.50,SW5_HB=29155.00,
7,2026-10-22T23:22:41.385Z,29118.50,29140.25,29074.50,29091.75,14.25,2026-10-22T22:43:56Z,2026-10-22T22:43:00Z,SW5_L=29072.00,SW5_LB=29114.50,
8,2026-10-22T23:33:00.148Z,29092.75,29097.75,29060.00,29060.00,14.25,2026-10-22T23:22:41Z,2026-10-22T23:22:00Z,,SW5_L=29103.50,-1 SW5_H
9,2026-10-22T23:36:48.374Z,29059.50,29068.50,29042.50,29057.50,14.38,2026-10-22T23:33:00Z,2026-10-22T23:33:00Z,,SW5_L=29103.50,-1 SW5_L
10,2026-10-23T00:31:52.563Z,29058.00,29136.50,29022.75,29115.00,14.38,2026-10-22T23:36:48Z,2026-10-22T23:36:00Z,SW5_L=29103.50,SW5_H=29140.25,
11,2026-10-23T00:40:30.111Z,29115.50,29127.25,29098.50,29122.00,14.38,2026-10-23T00:31:52Z,2026-10-23T00:31:00Z,SW5_HB=29100.25,SW5_H=29136.50,
12,2026-10-23T00:48:34.308Z,29122.25,29187.75,29114.25,29187.75,14.38,2026-10-23T00:40:30Z,2026-10-23T00:40:00Z,SW5_EQH=29140.25,,+1 SW5_L
13,2026-10-23T00:49:07.781Z,29187.00,29187.50,29179.50,29182.50,14.62,2026-10-23T00:48:34Z,2026-10-23T00:48:00Z,SW5_EQH=29140.25,,
14,2026-10-23T00:55:16.766Z,29182.75,29198.50,29162.00,29163.75,14.38,2026-10-23T00:49:07Z,2026-10-23T00:49:00Z,SW5_EQH=29140.25,,+1 SW5_H
15,2026-10-23T01:08:33.966Z,29164.00,29197.00,29129.50,29140.25,14.62,2026-10-23T00:55:16Z,2026-10-23T00:55:00Z,SW5_EQH=29140.25,SW5_HB=29165.75,
16,2026-10-23T01:11:14.323Z,29140.75,29143.75,29126.50,29132.75,14.88,2026-10-23T01:08:33Z,2026-10-23T01:08:00Z,SW5_L=29069.00,SW5_HB=29165.75,
17,2026-10-23T01:12:29.405Z,29132.75,29136.25,29114.00,29120.00,15.12,2026-10-23T01:11:14Z,2026-10-23T01:11:00Z,SW5_L=29069.00,SW5_HB=29165.75,-1 SW5_HB
18,2026-10-23T01:30:38.420Z,29120.25,29200.00,29056.75,29170.00,15.12,2026-10-23T01:12:29Z,2026-10-23T01:12:00Z,SW5_HB=29165.75,SW5_H=29198.50,
19,2026-10-23T01:42:39.969Z,29170.00,29200.00,29129.25,29200.00,16.00,2026-10-23T01:30:38Z,2026-10-23T01:30:00Z,SW5_H=29198.50,,
20,2026-10-23T01:43:36.279Z,29200.25,29204.00,29196.25,29199.25,16.00,2026-10-23T01:42:39Z,2026-10-23T01:42:00Z,SW5_HB=29165.75,SW5_H=29200.00,
21,2026-10-23T01:47:14.561Z,29198.75,29212.50,29188.00,29206.50,15.12,2026-10-23T01:43:36Z,2026-10-23T01:43:00Z,SW5_H=29200.00,,+1 SW5_HB
22,2026-10-23T01:57:20.155Z,29206.00,29211.75,29113.00,29121.00,16.00,2026-10-23T01:47:14Z,2026-10-23T01:47:00Z,SW5_L=29056.75,SW5_HB=29165.75,
23,2026-10-23T01:58:01.351Z,29121.00,29122.00,29113.00,29115.00,16.75,2026-10-23T01:57:20Z,2026-10-23T01:57:00Z,SW5_L=29056.75,SW5_HB=29165.75,
24,2026-10-23T01:59:14.768Z,29115.00,29119.25,29106.25,29116.50,16.00,2026-10-23T01:58:01Z,2026-10-23T01:58:00Z,SW5_L=29056.75,SW5_HB=29165.75,-1 SW5_H
25,2026-10-23T02:23:27.890Z,29116.25,29147.00,29089.00,29144.00,16.00,2026-10-23T01:59:14Z,2026-10-23T01:59:00Z,SW5_L=29056.75,SW5_HB=29165.75,
...
33,2026-10-23T03:21:12.446Z,29148.25,29149.00,29134.00,29139.75,15.12,2026-10-23T03:20:38Z,2026-10-23T03:20:00Z,,SW5_L=29167.00,
34,2026-10-23T03:32:01.600Z,29139.50,29180.00,29139.50,29171.75,15.12,2026-10-23T03:21:12Z,2026-10-23T03:21:00Z,SW5_L=29167.00,SW5_HB=29198.50,
35,2026-10-23T03:32:14.210Z,29171.25,29174.25,29163.50,29170.00,16.00,2026-10-23T03:32:01Z,2026-10-23T03:32:00Z,SW5_L=29167.00,SW5_H=29178.25,
36,2026-10-23T04:06:11.103Z,29169.50,29195.50,29151.00,29189.25,16.00,2026-10-23T03:32:14Z,2026-10-23T03:32:00Z,SW5_H=29178.25,SW5_HB=29198.50,
37,2026-10-23T04:35:04.183Z,29188.75,29193.25,29138.50,29150.00,16.75,2026-10-23T04:06:11Z,2026-10-23T04:06:00Z,,SW5_L=29151.00,
38,2026-10-23T05:26:22.576Z,29149.75,29158.50,29117.50,29125.00,16.75,2026-10-23T04:35:04Z,2026-10-23T04:35:00Z,,SW5_EQL=29134.00,
39,2026-10-23T05:30:34.379Z,29124.75,29135.00,29105.50,29133.75,16.75,2026-10-23T05:26:22Z,2026-10-23T05:26:00Z,SW5_L=29117.50,SW5_LB=29134.00,-1 SW5_HB
40,2026-10-23T05:33:25.958Z,29133.75,29151.75,29129.50,29140.00,16.75,2026-10-23T05:30:34Z,2026-10-23T05:30:00Z,SW5_LB=29134.00,SW5_H=29154.75,-1 SW5_H
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=5 2026-10-22T22:25:07.557Z side +1 fired SW5_LB: SW5_H=29215.00; SW5_L=29072.00; SW5_HB=29155.00; SW5_LB=29114.50; SW5_EQH=29215.00
k=8 2026-10-22T23:33:00.148Z side -1 fired SW5_H: SW5_H=29140.25; SW5_L=29103.50; SW5_HB=29155.00; SW5_LB=29103.50; SW5_EQL=29103.50
k=12 2026-10-23T00:48:34.308Z side +1 fired SW5_L: SW5_H=29136.50; SW5_L=29069.00; SW5_HB=29100.25; SW5_LB=29052.00; SW5_EQH=29140.25; SW5_EQL=29069.00; SW5_EQH3=29140.25
k=17 2026-10-23T01:12:29.405Z side -1 fired SW5_HB: SW5_H=29198.50; SW5_L=29069.00; SW5_HB=29165.75; SW5_LB=29052.00; SW5_EQL=29069.00
k=21 2026-10-23T01:47:14.561Z side +1 fired SW5_HB: SW5_H=29200.00; SW5_L=29056.75; SW5_HB=29165.75; SW5_LB=29052.00; SW5_EQH=29200.00
k=24 2026-10-23T01:59:14.768Z side -1 fired SW5_H: SW5_H=29200.00; SW5_L=29056.75; SW5_HB=29165.75; SW5_LB=29052.00; SW5_EQH=29200.00
k=39 2026-10-23T05:30:34.379Z side -1 fired SW5_HB: SW5_H=29154.75; SW5_L=29117.50; SW5_HB=29178.25; SW5_LB=29134.00; SW5_EQL=29117.50
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 25, first known 2026-10-15T22:10:21.980Z, last known 2026-10-16T05:59:58.154Z; rebuilt-from-tape check 25/25/25; threshold values: L=10, thr_contracts=26.120, s_vol=0.871
SIGNALS (raw events of the session: 5 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
3,2026-10-15T23:07:36.490Z,-1,SW5_LB,30106.75,30046.75,13.00,Y
11,2026-10-16T02:22:42.516Z,1,SW5_L,30037.25,30100.00,15.50,Y
13,2026-10-16T02:36:47.749Z,1,SW5_H,30091.75,30128.00,15.50,no
17,2026-10-16T04:22:22.481Z,1,SW5_H,30130.50,30190.00,15.75,Y
22,2026-10-16T05:44:37.835Z,-1,SW5_HB,30214.00,30173.00,16.75,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
3,-1,2026-10-15T23:07:37.542Z,30046.75,0.4398,30046.64,2026-10-15T23:42:51.557Z,29986.64,Target,60.0,60.0,60.00,1195.16
11,1,2026-10-16T02:22:43.945Z,30100.75,0.4398,30100.86,2026-10-16T03:49:45.727Z,30160.86,Target,60.0,60.0,60.00,1195.16
17,1,2026-10-16T04:22:24.329Z,30189.25,0.4398,30189.36,2026-10-16T05:59:58.154Z,30191.00,SessionEnd,60.0,60.0,1.64,27.96
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (all 25 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-15T22:10:21.980Z,30089.00,30128.00,30088.00,30119.25,12.88,2026-10-15T20:59:59Z,2026-10-15T20:59:00Z,SW5_L=30106.75,SW5_LB=30120.00,
1,2026-10-15T22:54:43.852Z,30117.75,30125.00,30064.00,30066.00,13.00,2026-10-15T22:10:21Z,2026-10-15T22:10:00Z,SW5_L=30036.50,SW5_LB=30106.75,
2,2026-10-15T23:06:38.470Z,30066.75,30073.25,30038.75,30038.75,13.00,2026-10-15T22:54:43Z,2026-10-15T22:54:00Z,SW5_L=30036.50,SW5_LB=30106.75,
3,2026-10-15T23:07:36.490Z,30038.50,30046.75,30027.50,30046.75,13.00,2026-10-15T23:06:38Z,2026-10-15T23:06:00Z,SW5_L=30036.50,SW5_LB=30106.75,-1 SW5_LB
4,2026-10-15T23:22:58.344Z,30047.00,30064.00,30010.75,30017.00,13.00,2026-10-15T23:07:36Z,2026-10-15T23:07:00Z,,SW5_L=30036.50,
5,2026-10-15T23:28:24.976Z,30017.25,30027.00,30010.50,30022.00,13.50,2026-10-15T23:22:58Z,2026-10-15T23:22:00Z,,SW5_L=30027.50,
6,2026-10-15T23:49:25.901Z,30022.00,30022.00,29982.50,29990.50,14.38,2026-10-15T23:28:24Z,2026-10-15T23:28:00Z,,SW5_L=30027.50,
7,2026-10-16T00:09:32.468Z,29990.00,30041.00,29977.50,30033.50,14.88,2026-10-15T23:49:25Z,2026-10-15T23:49:00Z,SW5_L=30027.50,SW5_H=30064.00,
8,2026-10-16T00:27:51.557Z,30033.25,30052.50,29962.50,29964.25,15.25,2026-10-16T00:09:32Z,2026-10-16T00:09:00Z,,SW5_L=29982.50,
9,2026-10-16T01:49:37.842Z,29964.50,30091.75,29959.25,30080.00,15.25,2026-10-16T00:27:51Z,2026-10-16T00:27:00Z,SW5_H=30052.50,SW5_HB=30158.50,
10,2026-10-16T01:55:28.884Z,30079.75,30084.75,30059.00,30067.00,15.25,2026-10-16T01:49:37Z,2026-10-16T01:49:00Z,SW5_HB=30064.00,SW5_H=30077.75,
11,2026-10-16T02:22:42.516Z,30067.00,30100.00,30043.25,30100.00,15.50,2026-10-16T01:55:28Z,2026-10-16T01:55:00Z,SW5_H=30077.75,,+1 SW5_L
12,2026-10-16T02:27:30.569Z,30100.25,30114.75,30093.75,30114.00,15.50,2026-10-16T02:22:42Z,2026-10-16T02:22:00Z,SW5_H=30091.75,,
13,2026-10-16T02:36:47.749Z,30114.25,30128.00,30094.75,30128.00,15.50,2026-10-16T02:27:30Z,2026-10-16T02:27:00Z,SW5_H=30091.75,,+1 SW5_H
14,2026-10-16T02:52:42.162Z,30128.50,30129.75,30096.00,30102.00,15.50,2026-10-16T02:36:47Z,2026-10-16T02:36:00Z,SW5_H=30091.75,,
15,2026-10-16T03:50:17.816Z,30101.75,30172.25,30074.00,30172.25,15.50,2026-10-16T02:52:42Z,2026-10-16T02:52:00Z,SW5_H=30129.75,,
16,2026-10-16T03:51:09.201Z,30172.50,30200.00,30164.75,30200.00,15.50,2026-10-16T03:50:17Z,2026-10-16T03:50:00Z,SW5_HB=30138.00,,
17,2026-10-16T04:22:22.481Z,30200.00,30211.75,30148.75,30190.00,15.75,2026-10-16T03:51:09Z,2026-10-16T03:51:00Z,SW5_HB=30138.00,,+1 SW5_H
18,2026-10-16T04:49:12.421Z,30190.25,30199.75,30162.75,30191.75,15.75,2026-10-16T04:22:22Z,2026-10-16T04:22:00Z,SW5_L=30074.00,SW5_HB=30196.75,
19,2026-10-16T05:04:29.489Z,30192.00,30220.00,30184.25,30214.25,15.75,2026-10-16T04:49:12Z,2026-10-16T04:49:00Z,SW5_H=30198.00,,
20,2026-10-16T05:09:33.284Z,30214.50,30225.00,30200.25,30200.25,16.25,2026-10-16T05:04:29Z,2026-10-16T05:04:00Z,SW5_H=30198.00,,
21,2026-10-16T05:29:29.279Z,30200.00,30207.00,30169.50,30170.75,16.25,2026-10-16T05:09:33Z,2026-10-16T05:09:00Z,SW5_L=30162.75,SW5_H=30198.00,
22,2026-10-16T05:44:37.835Z,30171.00,30198.00,30161.75,30173.00,16.75,2026-10-16T05:29:29Z,2026-10-16T05:29:00Z,SW5_L=30162.75,SW5_HB=30214.00,-1 SW5_HB
23,2026-10-16T05:52:18.209Z,30173.00,30193.00,30172.75,30189.75,17.12,2026-10-16T05:44:37Z,2026-10-16T05:44:00Z,SW5_L=30162.75,SW5_HB=30214.00,
24,2026-10-16T05:59:58.154Z,30190.00,30207.75,30189.75,30191.25,17.62,2026-10-16T05:52:18Z,2026-10-16T05:52:00Z,SW5_L=30161.75,SW5_HB=30214.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=3 2026-10-15T23:07:36.490Z side -1 fired SW5_LB: SW5_H=30138.00; SW5_L=30036.50; SW5_HB=30158.50; SW5_LB=30106.75
k=11 2026-10-16T02:22:42.516Z side +1 fired SW5_L: SW5_H=30077.75; SW5_L=30037.25; SW5_HB=30071.75; SW5_LB=29982.50; SW5_EQH=30077.75; SW5_EQL=30036.50
k=17 2026-10-16T04:22:22.481Z side +1 fired SW5_H: SW5_H=30130.50; SW5_L=30087.25; SW5_HB=30138.00; SW5_LB=29982.50; SW5_EQH=30130.50
```

#### td 20261009 (sess_id 202610090, Asia session, grid week 183)
- bars of the session: 24, first known 2026-10-08T22:41:08.333Z, last known 2026-10-09T05:59:57.199Z; rebuilt-from-tape check 24/24/24; threshold values: L=10, thr_contracts=25.714, s_vol=0.857
SIGNALS (raw events of the session: 8 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
1,2026-10-08T22:57:29.280Z,1,SW5_H,31015.75,31035.00,8.75,Y
4,2026-10-08T23:38:53.476Z,-1,SW5_H,31036.50,31009.00,8.75,no
8,2026-10-09T00:17:46.761Z,-1,SW5_LB,30995.25,30989.00,9.25,Y
15,2026-10-09T01:44:28.091Z,1,SW5_HB,31002.50,31048.75,9.75,Y
16,2026-10-09T01:53:52.388Z,1,SW5_H,31020.00,31052.00,9.75,no
21,2026-10-09T05:25:29.316Z,1,SW5_L,31064.00,31150.00,10.00,Y
22,2026-10-09T05:56:18.174Z,1,SW5_LB,31111.00,31171.00,10.00,no
23,2026-10-09T05:59:57.199Z,1,SW5_H,31137.25,31158.25,10.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
1,1,2026-10-08T22:57:39.190Z,31035.25,0.4398,31035.36,2026-10-08T23:51:08.615Z,30975.00,Stop,60.0,60.0,-60.36,-1212.04
8,-1,2026-10-09T00:17:48.114Z,30989.25,0.4398,30989.14,2026-10-09T01:43:50.973Z,31049.50,Stop,60.0,60.0,-60.36,-1212.04
15,1,2026-10-09T01:44:29.579Z,31052.00,0.4398,31052.11,2026-10-09T03:55:39.265Z,31112.11,Target,60.0,60.0,60.00,1195.16
21,1,2026-10-09T05:25:30.339Z,31148.25,0.4398,31148.36,2026-10-09T05:59:57.199Z,31158.00,SessionEnd,60.0,60.0,9.64,187.96
```
- check: the independent print-by-print scan equals the sim_slice points for all of 4 trades.
INPUTS (all 24 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-08T22:41:08.333Z,31020.50,31072.50,30995.00,31057.50,8.75,2026-10-08T20:59:59Z,2026-10-08T20:59:00Z,SW5_H=31015.75,,
1,2026-10-08T22:57:29.280Z,31056.25,31058.00,31025.25,31035.00,8.75,2026-10-08T22:41:08Z,2026-10-08T22:41:00Z,SW5_HB=31022.75,,+1 SW5_H
2,2026-10-08T23:27:18.770Z,31034.50,31036.50,30999.00,30999.75,8.75,2026-10-08T22:57:29Z,2026-10-08T22:57:00Z,SW5_L=30995.00,SW5_HB=31022.75,
3,2026-10-08T23:35:01.332Z,30999.75,31015.75,30990.00,31006.00,8.75,2026-10-08T23:27:18Z,2026-10-08T23:27:00Z,,SW5_L=31017.25,
4,2026-10-08T23:38:53.476Z,31006.50,31012.25,30997.25,31009.00,8.75,2026-10-08T23:35:01Z,2026-10-08T23:35:00Z,,SW5_L=31017.25,-1 SW5_H
5,2026-10-08T23:45:57.778Z,31009.25,31010.25,30993.25,30994.00,9.25,2026-10-08T23:38:53Z,2026-10-08T23:38:00Z,,SW5_L=31017.25,
6,2026-10-09T00:03:09.380Z,30994.25,31002.50,30963.25,30963.25,9.25,2026-10-08T23:45:57Z,2026-10-08T23:45:00Z,,SW5_L=30990.00,
7,2026-10-09T00:06:40.389Z,30963.00,30978.00,30953.00,30966.25,9.25,2026-10-09T00:03:09Z,2026-10-09T00:03:00Z,,SW5_L=30990.00,
8,2026-10-09T00:17:46.761Z,30966.75,30992.00,30962.25,30989.00,9.25,2026-10-09T00:06:40Z,2026-10-09T00:06:00Z,,SW5_L=30990.00,-1 SW5_LB
9,2026-10-09T00:46:25.198Z,30989.25,31034.00,30966.00,31027.00,9.25,2026-10-09T00:17:46Z,2026-10-09T00:17:00Z,SW5_HB=31022.75,,
10,2026-10-09T00:57:40.716Z,31026.75,31032.50,31000.00,31000.00,9.25,2026-10-09T00:46:25Z,2026-10-09T00:46:00Z,SW5_LB=30995.25,SW5_H=31002.50,
11,2026-10-09T01:00:33.593Z,30999.75,31002.25,30988.00,30990.00,9.25,2026-10-09T00:57:40Z,2026-10-09T00:57:00Z,SW5_L=30953.00,SW5_LB=30995.25,
12,2026-10-09T01:26:50.943Z,30990.00,31000.00,30966.50,31000.00,9.50,2026-10-09T01:00:33Z,2026-10-09T01:00:00Z,SW5_LB=30995.25,SW5_HB=31002.50,
13,2026-10-09T01:40:39.014Z,31000.25,31020.00,30981.50,31011.00,9.50,2026-10-09T01:26:50Z,2026-10-09T01:26:00Z,SW5_HB=31002.50,SW5_H=31034.00,
14,2026-10-09T01:42:56.218Z,31011.00,31047.75,31009.50,31041.75,9.75,2026-10-09T01:40:39Z,2026-10-09T01:40:00Z,SW5_H=31020.00,,
15,2026-10-09T01:44:28.091Z,31042.25,31051.75,31040.50,31048.75,9.75,2026-10-09T01:42:56Z,2026-10-09T01:42:00Z,SW5_H=31020.00,,+1 SW5_HB
16,2026-10-09T01:53:52.388Z,31049.00,31063.00,31044.00,31052.00,9.75,2026-10-09T01:44:28Z,2026-10-09T01:44:00Z,SW5_H=31020.00,,+1 SW5_H
17,2026-10-09T02:38:09.414Z,31052.00,31089.75,31046.50,31074.75,9.75,2026-10-09T01:53:52Z,2026-10-09T01:53:00Z,SW5_HB=31036.50,,
18,2026-10-09T03:12:41.519Z,31074.75,31084.25,31040.50,31045.00,10.00,2026-10-09T02:38:09Z,2026-10-09T02:38:00Z,SW5_LB=30995.25,SW5_L=31046.50,
19,2026-10-09T03:59:21.116Z,31044.75,31115.50,31042.75,31115.00,10.00,2026-10-09T03:12:41Z,2026-10-09T03:12:00Z,SW5_EQH=31086.75,,
20,2026-10-09T04:30:59.714Z,31114.75,31133.75,31111.00,31125.25,10.00,2026-10-09T03:59:21Z,2026-10-09T03:59:00Z,SW5_HB=31089.75,,
21,2026-10-09T05:25:29.316Z,31125.50,31150.00,31097.50,31150.00,10.00,2026-10-09T04:30:59Z,2026-10-09T04:30:00Z,SW5_H=31133.75,,+1 SW5_L
22,2026-10-09T05:56:18.174Z,31150.00,31171.00,31143.75,31171.00,10.00,2026-10-09T05:25:29Z,2026-10-09T05:25:00Z,SW5_HB=31138.00,,+1 SW5_LB
23,2026-10-09T05:59:57.199Z,31171.25,31177.00,31154.75,31158.25,10.00,2026-10-09T05:56:18Z,2026-10-09T05:56:00Z,SW5_HB=31138.00,,+1 SW5_H
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=1 2026-10-08T22:57:29.280Z side +1 fired SW5_H: SW5_H=31015.75; SW5_L=30995.00; SW5_HB=31022.75; SW5_LB=30915.50; SW5_EQH=31015.75; SW5_EQL=30995.00
k=8 2026-10-09T00:17:46.761Z side -1 fired SW5_LB: SW5_H=31036.50; SW5_L=30990.00; SW5_HB=31022.75; SW5_LB=30995.25
k=15 2026-10-09T01:44:28.091Z side +1 fired SW5_HB: SW5_H=31020.00; SW5_L=30966.50; SW5_HB=31002.50; SW5_LB=30995.25; SW5_EQH=31020.00
k=21 2026-10-09T05:25:29.316Z side +1 fired SW5_L: SW5_H=31133.75; SW5_L=31064.00; SW5_HB=31089.75; SW5_LB=30995.25
```

### BOOK W87b89d8f (Asia): dchg_10 + vwap level retest (M 10, tol 0.5), BOTH sides, bracket sym30u
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 17 of 17 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W87b89d8f (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W87b89d8f_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W87b89d8f.parquet` (52088 events: 26145 long, 25943 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `dchg_10`, module `trig_levels_vwap` (code/th_grid/trig_levels_vwap.py -> triggers_d/lv_vwap.py), variant `retest`, params {"M": 10, "tol": 0.5}, bracket `sym30u`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/dchg_10/trig_levels_vwap.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 1072, L6M 1774, L3M 983; t 4.3 over 1144 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 169..185 (2026-06-28 to 2026-10-24) = 17 held week(s); months in the cell file: 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored -300.50 / mine -300.50 pts, 6 / 6 trades; w182 2026-09-27 stored 199.62 / mine 199.62 pts, 8 / 8 trades; w183 2026-10-04 stored 262.12 / mine 262.12 pts, 7 / 7 trades; w184 2026-10-11 stored -251.85 / mine -251.85 pts, 7 / 7 trades; w185 2026-10-18 stored 363.37 / mine 363.37 pts, 8 / 8 trades (last 5 of 17 held weeks shown; 17 of 17 equal)

**1. BAR**
**BAR** row `dchg_10` = DIRECTIONAL-CHANGE leg bar. [SPEC] kernel k_dchg (kernels.py lines 197-225; build_month.py lines 125-128: `kagi_N` is built with EXACTLY the same kernel and thresholds as `dchg_N`, so the two rows are the same bars): reversal size theta = max(2, round(10 x s_rng)) ticks. Directional-change legs: a bar = a leg between two confirmed extremes. State per session key: d = 0 tracks the running high ehi and low elo from the first print; the first leg is decided when price is theta above the running low (up leg starts from that low, st = elo) or theta below the running high. d = +1: ext = running high (te = its time); when ext - p >= theta the leg is CONFIRMED: bar o = st, h = ext, l = st, c = ext, known time = timestamp of the confirming print (the close of the bar is the EXTREME, not the confirming price), then st = ext, d = -1, ext = p. d = -1 mirror (bar o = st, h = st, l = ext, c = ext). The unfinished last leg is never a bar. Theta on the sample days: 20261023: theta_ticks=22, theta_pts=5.50; 20261016: theta_ticks=22, theta_pts=5.50; 20261009: theta_ticks=23, theta_pts=5.75. [SPEC] Price-only (D8_BUILD_SPEC line 13). [READING] The live SwingBuilder class (D8Asia.cs) implements this kernel with a theta in ticks; kagi/dchg rows differ from it only in how theta is chosen (s_rng x N instead of the ATR rule).
- [SPEC] Bars per Asia session in the loaded months: median 449 (min 100, max 2637, 222 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/dchg_10/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261023: 1167 stored / 1167 rebuilt / 1167 identical (o,h,l,c,known_ts,part); td 20261016: 657 stored / 657 rebuilt / 657 identical (o,h,l,c,known_ts,part); td 20261009: 341 stored / 341 rebuilt / 341 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **spec exists, class by parameter**: dchg_40 specified (D8_BUILD_SPEC L8cfda948); SwingBuilder(theta) in D8Asia.cs is the same kernel; theta rule here = max(2, round(N x s_rng)) not the ATR rule.

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
- [SPEC, measured on the 222 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): VWAP0 0.86, RVWAP0 0.00, LVWAP0 0.00, YVWAP 1.00, AVPDH 0.99, AVPDL 0.99, WVWAP 0.89, MVWAP 0.98.
- [READING] Module status: **lines spec only; no VWAP code in D8Asia.cs**: break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits).

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `sym30u` = unit rule sym30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.4398, London 0.2067, NY AM 0.1208, NY PM 0.1012

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). unit rule sym30u: stop / target = clip(m x u, 10, 120) pts (see ENGINE text; u = rolling-50 median bar range of this row incl. the signal bar). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ trades only (1-minute bars from the tape, with contract-roll back-adjustment).
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: Needs the previous RTH day (YVWAP, AVPDH/L), the current ISO week and month (WVWAP/MVWAP; early in a week/month the volume gate delays validity). READING: starting a live chart cold needs the prior RTH day of 1-minute data plus the week-to-date and month-to-date minutes; the store itself runs from 2023-04-02.
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 10 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 377; share whose signal bar is bar 0 of the session: 0.03; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 17, 87, 343, 2179.
- [SPEC] Held weeks only: 144 grid trades; share on bar 0: 0.04; signal-bar index quantiles: 0, 8, 50, 218.25, 867.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: VWAP0 53, AVPDH 30, AVPDL 26, YVWAP 16, WVWAP 14, MVWAP 4, LVWAP0 1.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W87b89d8f_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261023 (sess_id 202610230, Asia session, grid week 185)
- bars of the session: 1167, first known 2026-10-22T22:00:00.162Z, last known 2026-10-23T05:59:08.187Z; rebuilt-from-tape check 1167/1167/1167; threshold values: theta_ticks=22, theta_pts=5.500
SIGNALS (raw events of the session: 234 in total, 1 shown (those inside the input windows or traded); all are in the CSV file; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
22,2026-10-22T22:02:06.681Z,1,AVPDL__V,29136.32,29146.75,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
22,1,2026-10-22T22:02:07.796Z,29140.00,0.4398,29140.11,2026-10-23T05:59:59.668Z,29134.75,SessionEnd,120.0,120.0,-5.36,-112.04
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 13 bars before to 1 bar after each traded signal bar, 15 of 1167 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
9,2026-10-22T22:00:46.312Z,29115.00,29115.00,29108.00,29108.00,5.00,2026-10-22T22:00:40Z,2026-10-22T22:00:00Z,,AVPDL=29136.54,
10,2026-10-22T22:00:49.074Z,29108.00,29133.75,29108.00,29133.75,5.00,2026-10-22T22:00:46Z,2026-10-22T22:00:00Z,,AVPDL=29136.54,
11,2026-10-22T22:00:50.950Z,29133.75,29133.75,29123.00,29123.00,5.00,2026-10-22T22:00:49Z,2026-10-22T22:00:00Z,,AVPDL=29136.54,
12,2026-10-22T22:00:57.386Z,29123.00,29131.00,29123.00,29131.00,5.00,2026-10-22T22:00:50Z,2026-10-22T22:00:00Z,,AVPDL=29136.54,
13,2026-10-22T22:01:09.254Z,29131.00,29131.00,29114.00,29114.00,5.00,2026-10-22T22:00:57Z,2026-10-22T22:00:00Z,,AVPDL=29136.54,
14,2026-10-22T22:01:10.902Z,29114.00,29126.50,29114.00,29126.50,5.00,2026-10-22T22:01:09Z,2026-10-22T22:01:00Z,,AVPDL=29136.32,
15,2026-10-22T22:01:22.091Z,29126.50,29126.50,29119.75,29119.75,5.00,2026-10-22T22:01:10Z,2026-10-22T22:01:00Z,,AVPDL=29136.32,
16,2026-10-22T22:01:35.895Z,29119.75,29128.50,29119.75,29128.50,5.00,2026-10-22T22:01:22Z,2026-10-22T22:01:00Z,,AVPDL=29136.32,
17,2026-10-22T22:01:39.256Z,29128.50,29128.50,29121.25,29121.25,5.00,2026-10-22T22:01:35Z,2026-10-22T22:01:00Z,,AVPDL=29136.32,
18,2026-10-22T22:01:47.776Z,29121.25,29134.25,29121.25,29134.25,5.00,2026-10-22T22:01:39Z,2026-10-22T22:01:00Z,,AVPDL=29136.32,
19,2026-10-22T22:01:49.824Z,29134.25,29134.25,29128.75,29128.75,5.00,2026-10-22T22:01:47Z,2026-10-22T22:01:00Z,,AVPDL=29136.32,
20,2026-10-22T22:01:59.121Z,29128.75,29143.75,29128.75,29143.75,5.00,2026-10-22T22:01:49Z,2026-10-22T22:01:00Z,AVPDL=29136.32,AVPDH=29236.98,
21,2026-10-22T22:01:59.353Z,29143.75,29143.75,29137.75,29137.75,5.00,2026-10-22T22:01:59Z,2026-10-22T22:01:00Z,AVPDL=29136.32,AVPDH=29236.98,
22,2026-10-22T22:02:06.681Z,29137.75,29146.75,29137.75,29146.75,5.00,2026-10-22T22:01:59Z,2026-10-22T22:01:00Z,AVPDL=29136.32,AVPDH=29236.98,+1 AVPDL
23,2026-10-22T22:02:14.508Z,29146.75,29146.75,29138.25,29138.25,5.00,2026-10-22T22:02:06Z,2026-10-22T22:02:00Z,AVPDL=29136.30,AVPDH=29236.91,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=22 2026-10-22T22:02:06.681Z side +1 fired AVPDL: YVWAP=29283.77; AVPDH=29236.98; AVPDL=29136.32; WVWAP=29667.65; MVWAP=30430.72
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 657, first known 2026-10-15T22:00:20.067Z, last known 2026-10-16T05:58:36.432Z; rebuilt-from-tape check 657/657/657; threshold values: theta_ticks=22, theta_pts=5.500
SIGNALS (raw events of the session: 30 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
160,2026-10-16T00:12:56.273Z,1,VWAP0__V,30041.08,30052.50,5.00,Y
161,2026-10-16T00:13:31.530Z,-1,VWAP0__V,30041.08,30033.50,5.00,no
162,2026-10-16T00:14:12.483Z,1,VWAP0__V,30041.12,30042.50,5.00,no
163,2026-10-16T00:14:23.834Z,-1,VWAP0__V,30041.11,30035.50,5.00,no
164,2026-10-16T00:14:34.458Z,1,VWAP0__V,30041.11,30046.25,5.00,no
165,2026-10-16T00:14:37.451Z,-1,VWAP0__V,30041.11,30038.00,5.00,no
166,2026-10-16T00:14:46.956Z,1,VWAP0__V,30041.11,30048.50,5.00,no
167,2026-10-16T00:15:04.906Z,-1,VWAP0__V,30041.11,30035.75,5.00,no
168,2026-10-16T00:15:07.006Z,1,VWAP0__V,30041.11,30043.75,5.00,no
169,2026-10-16T00:15:13.901Z,-1,VWAP0__V,30041.11,30032.00,5.00,no
256,2026-10-16T00:44:44.002Z,1,VWAP0__V,30026.98,30037.00,5.00,no
259,2026-10-16T00:45:42.763Z,-1,VWAP0__V,30027.01,30023.25,5.00,no
260,2026-10-16T00:46:01.810Z,1,VWAP0__V,30027.01,30033.75,5.00,no
261,2026-10-16T00:46:22.611Z,-1,VWAP0__V,30027.03,30027.00,5.00,no
262,2026-10-16T00:46:54.465Z,1,VWAP0__V,30027.03,30041.00,5.00,no
264,2026-10-16T00:48:01.316Z,1,VWAP0__V,30027.06,30038.00,5.00,no
266,2026-10-16T00:49:00.092Z,1,VWAP0__V,30027.10,30039.00,5.00,no
270,2026-10-16T00:50:22.430Z,1,VWAP0__V,30027.14,30040.75,5.00,no
412,2026-10-16T02:23:42.708Z,1,AVPDH__V,30090.76,30102.50,5.00,no
455,2026-10-16T03:36:03.995Z,-1,AVPDH__V,30092.22,30082.25,5.00,no
457,2026-10-16T03:37:02.616Z,-1,AVPDH__V,30092.22,30084.00,5.00,no
459,2026-10-16T03:37:52.360Z,-1,AVPDH__V,30092.22,30078.25,5.00,no
460,2026-10-16T03:39:20.556Z,1,AVPDH__V,30092.22,30103.00,5.00,no
463,2026-10-16T03:40:41.487Z,-1,AVPDH__V,30092.21,30089.25,5.00,no
464,2026-10-16T03:40:53.505Z,1,AVPDH__V,30092.21,30096.25,5.00,no
465,2026-10-16T03:41:20.495Z,-1,AVPDH__V,30092.21,30074.00,5.00,no
469,2026-10-16T03:43:05.946Z,-1,AVPDH__V,30092.20,30080.00,5.00,no
472,2026-10-16T03:43:59.545Z,1,AVPDH__V,30092.19,30094.75,5.00,no
473,2026-10-16T03:44:09.584Z,-1,AVPDH__V,30092.19,30085.50,5.00,no
474,2026-10-16T03:46:32.477Z,1,AVPDH__V,30092.18,30151.50,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
160,1,2026-10-16T00:12:57.891Z,30047.25,0.4398,30047.36,2026-10-16T03:50:13.117Z,30167.36,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 13 bars before to 1 bar after each traded signal bar, 15 of 657 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
147,2026-10-16T00:07:33.949Z,30031.50,30031.50,30024.50,30024.50,5.00,2026-10-16T00:07:30Z,2026-10-16T00:07:00Z,AVPDL=29971.22,VWAP0=30041.64,
148,2026-10-16T00:07:47.866Z,30024.50,30032.25,30024.50,30032.25,5.00,2026-10-16T00:07:33Z,2026-10-16T00:07:00Z,AVPDL=29971.22,VWAP0=30041.64,
149,2026-10-16T00:07:51.186Z,30032.25,30032.25,30026.75,30026.75,5.00,2026-10-16T00:07:47Z,2026-10-16T00:07:00Z,AVPDL=29971.22,VWAP0=30041.64,
150,2026-10-16T00:08:09.200Z,30026.75,30032.75,30026.75,30032.75,5.00,2026-10-16T00:07:51Z,2026-10-16T00:07:00Z,AVPDL=29971.22,VWAP0=30041.64,
151,2026-10-16T00:08:35.002Z,30032.75,30032.75,30023.50,30023.50,5.00,2026-10-16T00:08:09Z,2026-10-16T00:08:00Z,AVPDL=29971.23,VWAP0=30041.53,
152,2026-10-16T00:08:44.359Z,30023.50,30030.00,30023.50,30030.00,5.00,2026-10-16T00:08:35Z,2026-10-16T00:08:00Z,AVPDL=29971.23,VWAP0=30041.53,
153,2026-10-16T00:08:57.090Z,30030.00,30030.00,30022.75,30022.75,5.00,2026-10-16T00:08:44Z,2026-10-16T00:08:00Z,AVPDL=29971.23,VWAP0=30041.53,
154,2026-10-16T00:09:32.165Z,30022.75,30039.50,30022.75,30039.50,5.00,2026-10-16T00:08:57Z,2026-10-16T00:08:00Z,AVPDL=29971.23,VWAP0=30041.53,
155,2026-10-16T00:10:36.023Z,30039.50,30039.50,30018.25,30018.25,5.00,2026-10-16T00:09:32Z,2026-10-16T00:09:00Z,AVPDL=29971.25,VWAP0=30041.37,
156,2026-10-16T00:11:38.406Z,30018.25,30044.25,30018.25,30044.25,5.00,2026-10-16T00:10:36Z,2026-10-16T00:10:00Z,VWAP0=30041.29,AVPDH=30111.78,
157,2026-10-16T00:11:48.791Z,30044.25,30044.25,30031.75,30031.75,5.00,2026-10-16T00:11:38Z,2026-10-16T00:11:00Z,AVPDL=29971.30,VWAP0=30041.13,
158,2026-10-16T00:12:03.551Z,30031.75,30038.00,30031.75,30038.00,5.00,2026-10-16T00:11:48Z,2026-10-16T00:11:00Z,AVPDL=29971.30,VWAP0=30041.13,
159,2026-10-16T00:12:17.373Z,30038.00,30038.00,30032.50,30032.50,5.00,2026-10-16T00:12:03Z,2026-10-16T00:12:00Z,AVPDL=29971.32,VWAP0=30041.08,
160,2026-10-16T00:12:56.273Z,30032.50,30052.50,30032.50,30052.50,5.00,2026-10-16T00:12:17Z,2026-10-16T00:12:00Z,VWAP0=30041.08,AVPDH=30111.27,+1 VWAP0
161,2026-10-16T00:13:31.530Z,30052.50,30052.50,30033.50,30033.50,5.00,2026-10-16T00:12:56Z,2026-10-16T00:12:00Z,AVPDL=29971.32,VWAP0=30041.08,-1 VWAP0
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=160 2026-10-16T00:12:56.273Z side +1 fired VWAP0: VWAP0=30041.08; YVWAP=29921.82; AVPDH=30111.27; AVPDL=29971.32; WVWAP=30422.16; MVWAP=30846.35
```

#### td 20261009 (sess_id 202610090, Asia session, grid week 183)
- bars of the session: 341, first known 2026-10-08T22:00:00.178Z, last known 2026-10-09T05:59:48.752Z; rebuilt-from-tape check 341/341/341; threshold values: theta_ticks=23, theta_pts=5.750
SIGNALS (raw events of the session: 57 in total, 2 shown (those inside the input windows or traded); all are in the CSV file; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
21,2026-10-08T22:23:23.226Z,1,AVPDH__V,31045.88,31053.75,5.00,Y
22,2026-10-08T22:24:07.426Z,-1,AVPDH__V,31045.89,31039.50,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
21,1,2026-10-08T22:23:24.260Z,31045.50,0.4398,31045.61,2026-10-09T05:39:24.734Z,31165.61,Target,120.0,120.0,120.00,2395.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 13 bars before to 1 bar after each traded signal bar, 15 of 341 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
8,2026-10-08T22:01:56.081Z,31022.75,31022.75,31012.25,31012.25,5.00,2026-10-08T22:01:43Z,2026-10-08T22:01:00Z,AVPDL=30930.50,AVPDH=31046.01,
9,2026-10-08T22:02:11.329Z,31012.25,31019.50,31012.25,31019.50,5.00,2026-10-08T22:01:56Z,2026-10-08T22:01:00Z,AVPDL=30930.50,AVPDH=31046.01,
10,2026-10-08T22:03:14.095Z,31019.50,31019.50,30995.00,30995.00,5.00,2026-10-08T22:02:11Z,2026-10-08T22:02:00Z,AVPDL=30930.60,AVPDH=31045.99,
11,2026-10-08T22:04:24.910Z,30995.00,31018.75,30995.00,31018.75,5.00,2026-10-08T22:03:14Z,2026-10-08T22:03:00Z,AVPDL=30930.67,AVPDH=31045.98,
12,2026-10-08T22:04:55.309Z,31018.75,31018.75,31009.25,31009.25,5.00,2026-10-08T22:04:24Z,2026-10-08T22:04:00Z,AVPDL=30930.79,AVPDH=31045.95,
13,2026-10-08T22:05:34.634Z,31009.25,31017.75,31009.25,31017.75,5.00,2026-10-08T22:04:55Z,2026-10-08T22:04:00Z,AVPDL=30930.79,AVPDH=31045.95,
14,2026-10-08T22:05:49.846Z,31017.75,31017.75,31011.75,31011.75,5.00,2026-10-08T22:05:34Z,2026-10-08T22:05:00Z,AVPDL=30930.86,AVPDH=31045.94,
15,2026-10-08T22:06:02.511Z,31011.75,31022.00,31011.75,31022.00,5.00,2026-10-08T22:05:49Z,2026-10-08T22:05:00Z,AVPDL=30930.86,AVPDH=31045.94,
16,2026-10-08T22:06:17.176Z,31022.00,31022.00,31013.75,31013.75,5.00,2026-10-08T22:06:02Z,2026-10-08T22:06:00Z,AVPDL=30930.93,AVPDH=31045.93,
17,2026-10-08T22:10:40.633Z,31013.75,31036.25,31013.75,31036.25,5.00,2026-10-08T22:06:17Z,2026-10-08T22:06:00Z,AVPDL=30930.93,AVPDH=31045.93,
18,2026-10-08T22:10:58.677Z,31036.25,31036.25,31017.75,31017.75,5.00,2026-10-08T22:10:40Z,2026-10-08T22:10:00Z,AVPDL=30931.17,AVPDH=31045.91,
19,2026-10-08T22:15:51.979Z,31017.75,31055.50,31017.75,31055.50,5.00,2026-10-08T22:10:58Z,2026-10-08T22:10:00Z,AVPDH=31045.91,YVWAP=31084.65,
20,2026-10-08T22:18:57.550Z,31055.50,31055.50,31043.50,31043.50,5.00,2026-10-08T22:15:51Z,2026-10-08T22:15:00Z,AVPDL=30931.48,AVPDH=31045.88,
21,2026-10-08T22:23:23.226Z,31043.50,31053.75,31043.50,31053.75,5.00,2026-10-08T22:18:57Z,2026-10-08T22:18:00Z,AVPDH=31045.88,YVWAP=31084.65,+1 AVPDH
22,2026-10-08T22:24:07.426Z,31053.75,31053.75,31039.50,31039.50,5.00,2026-10-08T22:23:23Z,2026-10-08T22:23:00Z,AVPDL=30932.01,AVPDH=31045.89,-1 AVPDH
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=21 2026-10-08T22:23:23.226Z side +1 fired AVPDH: YVWAP=31084.65; AVPDH=31045.88; AVPDL=30931.82; WVWAP=31269.40; MVWAP=31120.04
```

### BOOK W4a911926 (Asia): tsf_10_60 + ob15 level break (n 1, k 0.0), BOTH sides, bracket plain60/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 4 of 4 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W4a911926 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W4a911926_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W4a911926.parquet` (356 events: 204 long, 152 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `tsf_10_60`, module `trig_levels_ob15` (code/th_grid/trig_levels_ob15.py -> triggers_d/lv_ob15.py), variant `break`, params {"n": 1, "k": 0.0}, bracket `plain60/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/tsf_10_60/trig_levels_ob15.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 314, L6M 993, L3M 1127; t 4.5 over 218 trades; mark: new.
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
Variant `break` (n=1, k=0.0): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: n=1, k=0.0 -> k*u = 0.000 pt.
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
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; tsf thresholds use s_vol.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 97; share whose signal bar is bar 0 of the session: 0.12; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 3, 7, 12, 41.
- [SPEC] Held weeks only: 10 grid trades; share on bar 0: 0.10; signal-bar index quantiles: 0, 3, 4, 11.5, 33.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: OB15_BEARLO 7, OB15_BULHI 2, OB15_BEARHI 1.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W4a911926_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261022 (sess_id 202610220, Asia session, grid week 185)
- bars of the session: 37, first known 2026-10-21T22:03:02.464Z, last known 2026-10-22T05:59:59.408Z; rebuilt-from-tape check 37/37/37; threshold values: L=10, thr_contracts=59.799, s_vol=0.997
SIGNALS (raw events of the session: 2 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
15,2026-10-22T02:06:41.553Z,-1,OB15_BULHI,29744.25,29741.75,5.00,Y
16,2026-10-22T02:17:24.459Z,-1,OB15_BULLO,29715.50,29700.25,5.00,no
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
15,-1,2026-10-22T02:06:42.869Z,29740.50,0.4398,29740.39,2026-10-22T02:32:39.248Z,29680.39,Target,60.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 37 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
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
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
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
INPUTS (all 19 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
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
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
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
INPUTS (all 24 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
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

### BOOK W0778abb1 (Asia): frenko_40 + fibr on level false break native (M 1, k 0.0), BOTH sides, bracket fixed30/90
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 17 of 17 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W0778abb1 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W0778abb1_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W0778abb1.parquet` (326 events: 170 long, 156 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `bfl17`, bar row `frenko_40`, module `trig_levels_fibr_on` (code/th_grid/trig_levels_fibr_on.py -> triggers_d/lv_fibr_on.py), variant `false_break_native`, params {"M": 1, "k": 0.0}, bracket `fixed30/90`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/bfl17/frenko_40/trig_levels_fibr_on.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 401, L6M 821, L3M 564; t 4.4 over 322 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 169..185 (2026-06-28 to 2026-10-24) = 17 held week(s); months in the cell file: 202606, 202607, 202608, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w181 2026-09-20 stored -30.65 / mine -30.65 pts, 1 / 1 trades; w182 2026-09-27 stored 59.11 / mine 59.11 pts, 2 / 2 trades; w183 2026-10-04 stored 72.20 / mine 72.20 pts, 3 / 3 trades; w184 2026-10-11 stored 89.76 / mine 89.76 pts, 1 / 1 trades; w185 2026-10-18 stored -30.90 / mine -30.90 pts, 1 / 1 trades (last 5 of 17 held weeks shown; 17 of 17 equal)

**1. BAR**
**BAR** row `frenko_40` = FLEX (hybrid) Renko (reversal = half a brick) RENKO. [SPEC] kernel k_renko (kernels.py lines 59-95), build_month.py lines 108-113: brick B = max(2, round(40 x s_rng)) ticks, reversal distance R = max(1, B//2), open offset O = 0, no wicks. State per session key: first print sets bo = bc = p, d = 0. d = 0: p >= bo + B -> up brick [bo, bo+B]; p <= bo - B -> down brick. d = +1: p >= bc + B -> continuation brick [bc, bc + B]; p <= bc - R -> reversal brick opening at bc - O = bc and closing at bc - R (height R, direction flips). Mirror for d = -1. A loop re-tests the same print, so one print can emit several bricks (same timestamp; volume to the first). Brick OHLC = (open, max, min, close) with no wicks; known time = timestamp of the completing print; no bar for an unfinished brick at the session end. Brick on the sample days: 20261021: brick_ticks=91, brick_pts=22.75, reversal_ticks=45; 20261012: brick_ticks=88, brick_pts=22.00, reversal_ticks=44; 20261008: brick_ticks=92, brick_pts=23.00, reversal_ticks=46. [SPEC] Price-only (D8_BUILD_SPEC line 13). [SPEC] The live class FlexRenkoBuilder (D8Asia.cs) is this kernel with R = B//2.
- [SPEC] Bars per Asia session in the loaded months: median 62 (min 3, max 478, 222 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/frenko_40/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261021: 102 stored / 102 rebuilt / 102 identical (o,h,l,c,known_ts,part); td 20261012: 59 stored / 59 rebuilt / 59 identical (o,h,l,c,known_ts,part); td 20261008: 36 stored / 36 rebuilt / 36 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **exists**: frenko_40 specified (D8_BUILD_SPEC L6b373671); class FlexRenkoBuilder in D8Asia.cs (same book bar).

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_fibr_on` (th_grid/triggers_d/lv_fibr_on.py; lines fd_levels2.py lines 131-146; ON__H/L fd_levels.py line 30 and function after()). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 18 lines FIBR_ON_*. H, L = ON__H, ON__L = high / low of the overnight minutes of the CURRENT label day (18:00-09:30 ET, tord < 930), AVAILABLE ONLY FROM 09:30 ET until the label day ends at 18:00 ET (fd_levels.py after(arr, 930) sets NaN for tord < 930). CONSEQUENCE [SPEC, measured below]: during the whole Asia session (and London and pre-market) of a label day these lines are NaN; the only Asia bars that can see them are those whose decision time T0 falls before 18:00 ET, i.e. the FIRST Asia bar of the session (its T0 = last bar of the previous 'close' session).
- Range fibs (fd_levels2.py range_fib, lines 131-137): with range R = H - L (NaN unless R >= 8 points): DNxxx = H - r R and UPxxx = L + r R for r = 0.236, 0.382, 0.5, 0.618, 0.65, 0.786 (names DN236 DN382 DN500 DN618 DN650 DN786 UP236 .. UP786); XUxxxx = H + (e-1) R for e = 1.272, 1.618, 2.0 (XU1272 XU1618 XU2000); XDxxxx = L - (e-1) R (XD1272 XD1618 XD2000). List order: DN236 DN382 DN500 DN618 DN650 DN786 UP236 UP382 UP500 UP618 UP650 UP786 XU1272 XU1618 XU2000 XD1272 XD1618 XD2000 (18 lines).
Variant `false_break_native` (M=1, k=0.0): [SPEC] false_break(M, k) (fd_common.level_events): up = close > L + k*u, dn = close < L - k*u (level-true, not edge); SHORT if up was true on ANY of the previous M bars (j-M..j-1) and now close < L; LONG if dn was true on any of the previous M bars and now close > L (fade of the failed break); edge(). All earlier closes are compared with the level L of bar j (frozen at T0_j), not with the level that stood at those earlier bars.
[SPEC] u (native) = rolling median of (high - low) over the previous 100 bars of THIS book's bar series (bars j-100..j-1, shifted one bar, min_periods 20, floor 0.5 pt; NaN before 20 bars) (fd_common.unit); every tolerance below is x u. With these parameters: M=1, k=0.0 -> k*u = 0.0 x u.
[SPEC] Combination over the line set (lv_base.make): for each line in LIST ORDER whose store file exists, compute long/short event masks with the level of that line at the bar's decision time; LONG mask = OR over lines, SHORT mask = OR over lines; the FIRST line (list order) that fires on a bar is recorded as the fired line; a bar that is both long and short is dropped (events_to_frame); each remaining row is one signal (side +1 buy / -1 sell, bar_idx, sig_ts = t_close of the bar).
[SPEC] (same for every book in this stack) Level lookup (fd_common.line_index / line_at, th_grid/triggers_d/fd_common.py): decision time T0_j = t_close[j-1] in WHOLE SECONDS (the stored bar frames carry no t_open, gjob.load_bars, so T0 is the previous bar's known time even when bar j opened later; for the first bar of a session this previous bar belongs to the PREVIOUS session of the same bar row, e.g. the 16:00-18:00 ET 'close' session or the pre-market session). The level of a line at bar j = the minute-grid entry of the last 1-minute START <= T0_j; NaN if that minute start is more than 120 s older than T0 or T0 < 0. The entry of minute i uses only minutes < i (the minute that contains T0 is NOT included) or complete sessions/days. The bar's own o/h/l/c are compared with the level frozen at T0_j.
- [SPEC, measured on the 222 Asia sessions loaded] Share of bars of this book's session whose level is finite (decision-time lookup, all signal-session bars): FIBR_ON_DN236 0.01, FIBR_ON_DN382 0.01, FIBR_ON_DN500 0.01, FIBR_ON_DN618 0.01, FIBR_ON_DN650 0.01, FIBR_ON_DN786 0.01, FIBR_ON_UP236 0.01, FIBR_ON_UP382 0.01, FIBR_ON_UP500 0.01, FIBR_ON_UP618 0.01, FIBR_ON_UP650 0.01, FIBR_ON_UP786 0.01, FIBR_ON_XU1272 0.01, FIBR_ON_XU1618 0.01, FIBR_ON_XU2000 0.01, FIBR_ON_XD1272 0.01, FIBR_ON_XD1618 0.01, FIBR_ON_XD2000 0.01.
- [READING] Module status: **spec exists**: D8_NYAM_SPEC_L43f0cbfb verified the 18 overnight Fibonacci lines from tape (NY AM, false_break M 3, k 0.5); not in D8Asia.cs; here the Asia effect (lines NaN except bar 0) is new.

**3. SIGNAL -> ORDER (grid engine)**
See section A of this page (ENGINE text). Book-specific: bracket `fixed30/90` = stop 30 pts / target 90 pts, fixed (no unit rule); session window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET); side both; lots 1.
- [SPEC] Slippage ticks used for this book (table by session code, family `rng (price bars)`): Asia 0.6389, London 0.2891, NY AM 0.1776, NY PM 0.1787

**4. SIDES, BRACKET, UNITS.** [SPEC] BOTH sides (the cell mode is both; the hold list contains only both-sides cells). stop 30 pts / target 90 pts, fixed (no unit rule). Cost 0.242 pt per round trip (4.84 USD). One NQ lot ($20 per point).
**5. OTHER-MARKET INPUTS.** [SPEC] None. NQ trade tape only. NQ 1-minute series only.
**6. ONE POSITION / SESSION WINDOW / WARM-UP.**
- [SPEC] One position at a time per book and bracket (a signal whose entry print is not after the last exit print is skipped; reset each UTC month in the grid; the live engine drops events while in a trade, D8_BUILD_SPEC (b2)). Signals only from bars with part == 0 and session code 0; window 18:00-02:00 ET (session code 0; signal bars with sess_id%10 == 0; flat at 02:00 ET).
- [SPEC] Warm-up of the level lines: The current day's overnight range, complete only at 09:30 ET.
- [SPEC] Warm-up of the trigger: native u needs 20 earlier bars of the continuous series (rolling 100, shifted). Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; box/theta uses s_rng.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 84; share whose signal bar is bar 0 of the session: 1.00; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 0, 0, 0, 0.
- [SPEC] Held weeks only: 28 grid trades; share on bar 0: 1.00; signal-bar index quantiles: 0, 0, 0, 0, 0.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: FIBR_ON_DN236 6, FIBR_ON_DN618 4, FIBR_ON_DN382 4, FIBR_ON_DN786 3, FIBR_ON_XU1272 2, FIBR_ON_DN500 2, FIBR_ON_UP650 2, FIBR_ON_XD1272 1, FIBR_ON_XU1618 1, FIBR_ON_XU2000 1, FIBR_ON_XD1618 1, FIBR_ON_UP786 1.
- **FLAG [SPEC]: this book trades essentially ONLY on bar 0 of the session**, because its level lines are NaN for the rest of the session (mean finite share over the lines in this session 0.01, section 2); bar 0 uses the lines of the label day that is still current at the previous session's close (T0 = last bar of the previous session). A coder who computes the lines live for Asia bars after 18:00 ET would see no levels and no trades.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W0778abb1_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261021 (sess_id 202610210, Asia session, grid week 185)
- bars of the session: 102, first known 2026-10-20T22:00:02.248Z, last known 2026-10-21T05:46:26.195Z; rebuilt-from-tape check 102/102/102; threshold values: brick_ticks=91, brick_pts=22.750, reversal_ticks=45
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-20T22:00:02.248Z,1,FIBR_ON_XU1272,29891.90,29947.75,11.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,1,2026-10-20T22:00:03.362Z,29948.00,0.6389,29948.16,2026-10-20T22:42:08.338Z,29917.50,Stop,30.0,90.0,-30.66,-618.03
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 2 of 102 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-20T22:00:02.248Z,29925.00,29947.75,29925.00,29947.75,11.00,2026-10-20T20:57:51Z,2026-10-20T20:57:00Z,FIBR_ON_XU1272=29891.90,FIBR_ON_XU1618=30004.35,+1 FIBR_ON_XU1272
1,2026-10-20T22:01:30.944Z,29947.75,29970.50,29947.75,29970.50,11.00,2026-10-20T22:00:02Z,2026-10-20T22:00:00Z,,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-20T22:00:02.248Z side +1 fired FIBR_ON_XU1272: FIBR_ON_DN236=29726.80; FIBR_ON_DN382=29679.35; FIBR_ON_DN500=29641.00; FIBR_ON_DN618=29602.65; FIBR_ON_DN650=29592.25; FIBR_ON_DN786=29548.05; FIBR_ON_UP236=29555.20; FIBR_ON_UP382=29602.65; FIBR_ON_UP500=29641.00; FIBR_ON_UP618=29679.35; FIBR_ON_UP650=29689.75; FIBR_ON_UP786=29733.95; FIBR_ON_XU1272=29891.90; FIBR_ON_XU1618=30004.35; FIBR_ON_XU2000=30128.50; FIBR_ON_XD1272=29390.10; FIBR_ON_XD1618=29277.65; FIBR_ON_XD2000=29153.50
```

#### td 20261012 (sess_id 202610120, Asia session, grid week 184)
- bars of the session: 59, first known 2026-10-11T22:02:05.787Z, last known 2026-10-12T05:47:09.073Z; rebuilt-from-tape check 59/59/59; threshold values: brick_ticks=88, brick_pts=22.000, reversal_ticks=44
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-11T22:02:05.787Z,1,FIBR_ON_DN382,31146.74,31167.50,11.50,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,1,2026-10-11T22:02:06.905Z,31167.25,0.6389,31167.41,2026-10-11T23:28:09.295Z,31257.41,Target,30.0,90.0,90.00,1795.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (windows of 6 bars before to 1 bar after each traded signal bar, 2 of 59 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-11T22:02:05.787Z,31145.50,31167.50,31145.50,31167.50,11.50,2026-10-09T20:59:12Z,2026-10-09T20:59:00Z,FIBR_ON_UP650=31156.78,FIBR_ON_DN236=31192.51,+1 FIBR_ON_DN382
1,2026-10-11T22:09:10.390Z,31167.50,31189.50,31167.50,31189.50,11.50,2026-10-11T22:02:05Z,2026-10-11T22:02:00Z,,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-11T22:02:05.787Z side +1 fired FIBR_ON_DN382: FIBR_ON_DN236=31192.51; FIBR_ON_DN382=31146.74; FIBR_ON_DN500=31109.75; FIBR_ON_DN618=31072.76; FIBR_ON_DN650=31062.72; FIBR_ON_DN786=31020.09; FIBR_ON_UP236=31026.99; FIBR_ON_UP382=31072.76; FIBR_ON_UP500=31109.75; FIBR_ON_UP618=31146.74; FIBR_ON_UP650=31156.78; FIBR_ON_UP786=31199.41; FIBR_ON_XU1272=31351.77; FIBR_ON_XU1618=31460.24; FIBR_ON_XU2000=31580.00; FIBR_ON_XD1272=30867.73; FIBR_ON_XD1618=30759.26; FIBR_ON_XD2000=30639.50
```

#### td 20261008 (sess_id 202610080, Asia session, grid week 183)
- bars of the session: 36, first known 2026-10-07T22:02:10.798Z, last known 2026-10-08T05:58:23.059Z; rebuilt-from-tape check 36/36/36; threshold values: brick_ticks=92, brick_pts=23.000, reversal_ticks=46
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-07T22:02:10.798Z,1,FIBR_ON_UP650,31410.84,31426.00,11.50,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,1,2026-10-07T22:02:12.698Z,31424.00,0.6389,31424.16,2026-10-08T00:29:34.360Z,31393.75,Stop,30.0,90.0,-30.41,-613.03
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 36 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-07T22:02:10.798Z,31403.00,31426.00,31403.00,31426.00,11.50,2026-10-07T19:55:00Z,2026-10-07T19:55:00Z,FIBR_ON_UP650=31410.84,FIBR_ON_DN236=31446.72,+1 FIBR_ON_UP650
1,2026-10-07T23:15:07.894Z,31426.00,31449.00,31426.00,31449.00,11.50,2026-10-07T22:02:10Z,2026-10-07T22:02:00Z,,,
2,2026-10-07T23:45:27.879Z,31449.00,31449.00,31437.50,31437.50,11.50,2026-10-07T23:15:07Z,2026-10-07T23:15:00Z,,,
3,2026-10-08T00:06:35.626Z,31437.50,31437.50,31414.50,31414.50,11.50,2026-10-07T23:45:27Z,2026-10-07T23:45:00Z,,,
4,2026-10-08T00:18:36.892Z,31414.50,31426.00,31414.50,31426.00,11.50,2026-10-08T00:06:35Z,2026-10-08T00:06:00Z,,,
5,2026-10-08T00:18:46.505Z,31426.00,31426.00,31414.50,31414.50,11.50,2026-10-08T00:18:36Z,2026-10-08T00:18:00Z,,,
6,2026-10-08T00:29:43.359Z,31414.50,31414.50,31391.50,31391.50,11.50,2026-10-08T00:18:46Z,2026-10-08T00:18:00Z,,,
7,2026-10-08T01:02:57.143Z,31391.50,31403.00,31391.50,31403.00,11.50,2026-10-08T00:29:43Z,2026-10-08T00:29:00Z,,,
8,2026-10-08T01:10:23.543Z,31403.00,31403.00,31391.50,31391.50,11.50,2026-10-08T01:02:57Z,2026-10-08T01:02:00Z,,,
9,2026-10-08T01:16:57.062Z,31391.50,31403.00,31391.50,31403.00,11.50,2026-10-08T01:10:23Z,2026-10-08T01:10:00Z,,,
10,2026-10-08T01:23:02.268Z,31403.00,31403.00,31391.50,31391.50,11.50,2026-10-08T01:16:57Z,2026-10-08T01:16:00Z,,,
11,2026-10-08T01:23:31.199Z,31391.50,31403.00,31391.50,31403.00,11.50,2026-10-08T01:23:02Z,2026-10-08T01:23:00Z,,,
12,2026-10-08T01:33:07.814Z,31403.00,31426.00,31403.00,31426.00,11.50,2026-10-08T01:23:31Z,2026-10-08T01:23:00Z,,,
13,2026-10-08T01:56:45.340Z,31426.00,31449.00,31426.00,31449.00,11.50,2026-10-08T01:33:07Z,2026-10-08T01:33:00Z,,,
14,2026-10-08T01:59:43.915Z,31449.00,31449.00,31437.50,31437.50,11.50,2026-10-08T01:56:45Z,2026-10-08T01:56:00Z,,,
15,2026-10-08T02:22:47.052Z,31437.50,31449.00,31437.50,31449.00,11.50,2026-10-08T01:59:43Z,2026-10-08T01:59:00Z,,,
16,2026-10-08T02:40:52.417Z,31449.00,31449.00,31437.50,31437.50,11.50,2026-10-08T02:22:47Z,2026-10-08T02:22:00Z,,,
17,2026-10-08T02:43:01.528Z,31437.50,31449.00,31437.50,31449.00,11.50,2026-10-08T02:40:52Z,2026-10-08T02:40:00Z,,,
18,2026-10-08T02:47:52.954Z,31449.00,31449.00,31437.50,31437.50,11.50,2026-10-08T02:43:01Z,2026-10-08T02:43:00Z,,,
19,2026-10-08T02:55:00.644Z,31437.50,31437.50,31414.50,31414.50,11.50,2026-10-08T02:47:52Z,2026-10-08T02:47:00Z,,,
20,2026-10-08T03:14:39.802Z,31414.50,31414.50,31391.50,31391.50,11.50,2026-10-08T02:55:00Z,2026-10-08T02:55:00Z,,,
21,2026-10-08T03:26:34.203Z,31391.50,31403.00,31391.50,31403.00,11.50,2026-10-08T03:14:39Z,2026-10-08T03:14:00Z,,,
22,2026-10-08T03:34:22.065Z,31403.00,31403.00,31391.50,31391.50,11.50,2026-10-08T03:26:34Z,2026-10-08T03:26:00Z,,,
23,2026-10-08T03:52:47.307Z,31391.50,31391.50,31368.50,31368.50,11.50,2026-10-08T03:34:22Z,2026-10-08T03:34:00Z,,,
24,2026-10-08T04:27:01.493Z,31368.50,31380.00,31368.50,31380.00,11.50,2026-10-08T03:52:47Z,2026-10-08T03:52:00Z,,,
25,2026-10-08T04:55:28.877Z,31380.00,31403.00,31380.00,31403.00,11.50,2026-10-08T04:27:01Z,2026-10-08T04:27:00Z,,,
26,2026-10-08T04:56:53.835Z,31403.00,31403.00,31391.50,31391.50,11.50,2026-10-08T04:55:28Z,2026-10-08T04:55:00Z,,,
27,2026-10-08T05:10:08.453Z,31391.50,31403.00,31391.50,31403.00,11.50,2026-10-08T04:56:53Z,2026-10-08T04:56:00Z,,,
28,2026-10-08T05:18:22.916Z,31403.00,31403.00,31391.50,31391.50,11.50,2026-10-08T05:10:08Z,2026-10-08T05:10:00Z,,,
29,2026-10-08T05:19:38.701Z,31391.50,31403.00,31391.50,31403.00,11.50,2026-10-08T05:18:22Z,2026-10-08T05:18:00Z,,,
30,2026-10-08T05:25:38.317Z,31403.00,31403.00,31391.50,31391.50,11.50,2026-10-08T05:19:38Z,2026-10-08T05:19:00Z,,,
31,2026-10-08T05:35:58.532Z,31391.50,31403.00,31391.50,31403.00,11.50,2026-10-08T05:25:38Z,2026-10-08T05:25:00Z,,,
32,2026-10-08T05:37:14.217Z,31403.00,31403.00,31391.50,31391.50,11.50,2026-10-08T05:35:58Z,2026-10-08T05:35:00Z,,,
33,2026-10-08T05:43:08.403Z,31391.50,31391.50,31368.50,31368.50,11.50,2026-10-08T05:37:14Z,2026-10-08T05:37:00Z,,,
34,2026-10-08T05:50:52.251Z,31368.50,31368.50,31345.50,31345.50,11.50,2026-10-08T05:43:08Z,2026-10-08T05:43:00Z,,,
35,2026-10-08T05:58:23.059Z,31345.50,31345.50,31322.50,31322.50,11.50,2026-10-08T05:50:52Z,2026-10-08T05:50:00Z,,,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-07T22:02:10.798Z side +1 fired FIBR_ON_UP650: FIBR_ON_DN236=31446.72; FIBR_ON_DN382=31400.77; FIBR_ON_DN500=31363.62; FIBR_ON_DN618=31326.48; FIBR_ON_DN650=31316.41; FIBR_ON_DN786=31273.61; FIBR_ON_UP236=31280.53; FIBR_ON_UP382=31326.48; FIBR_ON_UP500=31363.62; FIBR_ON_UP618=31400.77; FIBR_ON_UP650=31410.84; FIBR_ON_UP786=31453.64; FIBR_ON_XU1272=31606.61; FIBR_ON_XU1618=31715.52; FIBR_ON_XU2000=31835.75; FIBR_ON_XD1272=31120.64; FIBR_ON_XD1618=31011.73; FIBR_ON_XD2000=30891.50
```

### BOOK W0d8714f7 (Asia): tsf_10_250 + piv floor level break (n 1, k 0.0), BOTH sides, bracket plain60/60
**STATUS OF THIS BOOK.** GRID ENGINE REPRODUCED the stored grid weekly table of this cell exactly in 17 of 17 held weeks (points to 0.02, trade counts equal); the 3 dated sessions below were re-simulated with gcore2x sim_slice and an independent print-by-print scan (agree on all trades listed); the bars of those sessions were rebuilt from the stored tape with the engine kernel and are identical to the stored bars.

**0. IDENTITY AND PROVENANCE**
- [SPEC] Grid cell id W0d8714f7 (W + md5 of session|row|module|params|bracket|mode, FORWARD_REGISTER_STACKS.md); exact set `TL3_ALN_AS_W0d8714f7_R0RT`; raw events `/mnt/l2/l2vast/_rota/ev/W0d8714f7.parquet` (1082 events: 547 long, 535 short; columns ts, side, stop_pts, tgt_pts, lots, exit_ts).
- [SPEC] Cell (from /mnt/l2/l2vast/_test8/cells_T8.json): tag `p1real`, bar row `tsf_10_250`, module `trig_levels_piv_floor` (code/th_grid/trig_levels_piv_floor.py -> triggers_d/lv_piv_floor.py), variant `break`, params {"n": 1, "k": 0.0}, bracket `plain60/60`, mode `both`; grid result file /mnt/l2/l2vast/_grid/res/p1real/tsf_10_250/trig_levels_piv_floor.npz.
- [SPEC] Register numbers (Test 8 quick screen, 2023-04..2026-10, equal weight 1 lot, grid cost in): $/lot/wk 635, L6M 1239, L3M 1891; t 4.3 over 841 trades; mark: new.
- [SPEC] Held by the Test 8 primary (picks_t4_test8.json, hold = [first, end) grid weeks, Sunday-start weeks since 2023-04-02): weeks 156..168 (2026-03-29 to 2026-06-27); weeks 182..185 (2026-09-27 to 2026-10-24) = 17 held week(s); months in the cell file: 202603, 202604, 202605, 202606, 202609, 202610. The list of week 182 (data to 2026-10-25) is the register's source.
- [SPEC] Held-week reproduction (stored grid npz vs my re-run of signal_fn + gcore2x.sim_slice on the bar row loaded from 170 days before the first held week): w168 2026-06-21 stored -42.77 / mine -42.77 pts, 14 / 14 trades; w182 2026-09-27 stored 97.69 / mine 97.69 pts, 12 / 12 trades; w183 2026-10-04 stored 5.00 / mine 5.00 pts, 6 / 6 trades; w184 2026-10-11 stored 77.88 / mine 77.88 pts, 9 / 9 trades; w185 2026-10-18 stored 176.49 / mine 176.49 pts, 9 / 9 trades (last 5 of 17 held weeks shown; 17 of 17 equal)

**1. BAR**
**BAR** row `tsf_10_250` = TRADE-SIZE-FILTERED VOLUME bar (L = 10, N = 250). [SPEC] build_month.py lines 97-100 with kernel k_cum (kernels.py lines 11-33), mode 0: metric = print size if size >= 10 else 0; threshold thr = 250 x s_vol contracts (s_vol = abs_vol / r0_vol, fixed for the session). Per session key a bar opens at the first print; EVERY print updates o/h/l/c, volume, count (all prints, not only the counted ones; the registry text in th_bars/spec.py says 'OHLC uses only counted prints' but the code does not do that: code governs); cum += metric; the bar CLOSES at the print for which cum >= thr (the closing print stays in the bar, no split); known time = that print's timestamp; the last bar of the session is emitted with part = 1 (known at its last print) and is never a signal bar. Threshold on the sample days: 20261022: L=10, thr_contracts=249.16, s_vol=1.00; 20261016: L=10, thr_contracts=217.67, s_vol=0.87; 20261009: L=10, thr_contracts=214.28, s_vol=0.86. [SPEC] This row is an ACTIVITY (volume-accumulating) bar and the old-engine tape treats every MBO trade record as one print; D8_PRINT_RULE.md section 2 shows that volume-accumulating bars (vol, vsess, tick, dlt, cdr, dib ...) are DIFFERENT between contract level, run merge and the old engine bars (2% to 28% identical for volume-type bars). tsf is NOT in that proof table and has no run-merge version in /mnt/l2/l2vast/_d8spec/bars_c or bars_r. [READING] Because the filter acts on the SIZE of one print (record size >= L lots), merging records of the same price and side into one print (the D8 rule) changes which prints pass the filter and therefore every bar boundary: the grid result for this book is NOT proven for the D8 print stream, and a live bar builder cannot be matched without deciding the print granularity. RISK FLAG.
- [SPEC] Bars per Asia session in the loaded months: median 5 (min 1, max 21, 287 sessions).
- [SPEC] Bar store read by the grid: `/mnt/l2/l2vast/_bars/tsf_10_250/<YYYYMM>.parquet` (the old engine store; columns o,h,l,c in ticks, vol, n, dlt, known_ts, sess_id, part, spb; gjob.load_bars scales to points and sorts ALL sessions into ONE continuous series by t_close). Rebuild check on the 3 dated sessions below: td 20261022: 12 stored / 12 rebuilt / 12 identical (o,h,l,c,known_ts,part); td 20261016: 4 stored / 4 rebuilt / 4 identical (o,h,l,c,known_ts,part); td 20261009: 4 stored / 4 rebuilt / 4 identical (o,h,l,c,known_ts,part).
- [READING] Builder status in the live pages/code: **NEW**: no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision.

**2. TRIGGER / LEVEL MODULE**
Module `trig_levels_piv_floor` (th_grid/triggers_d/lv_piv_floor.py; lines fd_levels2.py lines 148-167). Family `levels`, DATA_NEED per module header. Details of the line set:
[SPEC] Level set = 16 lines in this list order: PIV_D_P, PIV_D_R1, PIV_D_R2, PIV_D_R3, PIV_D_S1, PIV_D_S2, PIV_D_S3, PIV_W_P, PIV_W_R1, PIV_W_R2, PIV_W_R3, PIV_W_S1, PIV_W_S2, PIV_W_S3, CPR_TC, CPR_BC.
- Daily: from the prior RTH day high H, low L and close C (PD_RTH__H, PD_RTH__L, PD_C__C): P = (H+L+C)/3; R1 = 2P - L; S1 = 2P - H; R2 = P + (H-L); S2 = P - (H-L); R3 = H + 2(P - L); S3 = L - 2(H - P). Constant over the label day.
- Weekly: the same formulas from the previous ISO week's high / low / last 1-minute close (all minutes of that week, label-date weeks), constant over the next ISO week.
- CPR_BC = (H+L)/2, CPR_TC = 2P - BC from the prior RTH day.
- Raw price = adj - off.
Variant `break` (n=1, k=0.0): [SPEC] break(n, k) (fd_common.level_events): up = close > L + k*u; a LONG event needs the last n closes (bars j-n+1..j) ALL > L + k*u (each compared with the level L of bar j) AND the close n bars back, c[j-n], <= L + k*u (fresh); then edge() (only the first bar where it becomes true). SHORT mirrored (close < L - k*u, c[j-n] >= L - k*u).
[SPEC] u (plain variant) = 5.0 points (lv_base.U0), a constant; every tolerance below is x 5.0 pt. With these parameters: n=1, k=0.0 -> k*u = 0.000 pt.
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
- [SPEC] Warm-up of the trigger: plain u = 5.0 pt needs no history. Memory M / hold n of the variant: 1 bar(s). The bar series is ONE continuous series of ALL sessions (all six session codes), so the previous-session bars (close 16:00-18:00 ET, pre-market 08:30-09:30 ET etc.) must be built and kept; the first bar of the session sees them (T0 = previous bar's close).
- [SPEC] Warm-up of the bar: none beyond the daily scale table (trailing 20 stats rows; fewer than 5 rows fall back to r0) because every kernel restarts at each session boundary; tsf thresholds use s_vol.

**7. WHAT ACTUALLY TRADES (grid trades, measured)**
- [SPEC] All grid trades of this cell in the loaded months (from 170 days before the first held week to the data end): 427; share whose signal bar is bar 0 of the session: 0.31; signal-bar index within its session, quantiles (min, 25%, median, 75%, max): 0, 0, 1, 3, 19.
- [SPEC] Held weeks only: 139 grid trades; share on bar 0: 0.29; signal-bar index quantiles: 0, 0, 2, 3, 10.
- [SPEC] Fired line (first line in list order that fired) over the held-week trades: PIV_D_P 33, PIV_D_R1 26, PIV_D_S1 21, CPR_TC 17, PIV_D_R2 11, PIV_D_S2 7, PIV_W_P 6, PIV_W_R1 5, PIV_D_R3 4, CPR_BC 3, PIV_D_S3 3, PIV_W_S2 2.

**8. PARITY DATA: 3 dated sessions (bars, levels, signal, entry, exit)** Engine = gcore2x (grid). Full per-bar tables with every line value: `autopilot/spec_stack_inputs/W0d8714f7_td<td>.csv` (one file per session; small). Raw tape pages are NOT written (the tape is /mnt/l2/l2vast/_bars/trades/<UTC day>.parquet; D8_PARITY_TAPE pages are 7.9 MB each, box1 is 99% full).

#### td 20261022 (sess_id 202610220, Asia session, grid week 185)
- bars of the session: 12, first known 2026-10-21T23:11:05.851Z, last known 2026-10-22T05:59:59.408Z; rebuilt-from-tape check 12/12/12; threshold values: L=10, thr_contracts=249.164, s_vol=0.997
SIGNALS (raw events of the session: 3 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
0,2026-10-21T23:11:05.851Z,-1,PIV_D_R1,29930.42,29826.00,5.00,Y
2,2026-10-22T01:30:18.663Z,-1,PIV_D_S1,29808.17,29786.00,5.00,Y
8,2026-10-22T04:34:52.355Z,-1,PIV_D_S2,29618.58,29600.00,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
0,-1,2026-10-21T23:11:07.233Z,29825.25,0.4398,29825.14,2026-10-21T23:54:39.650Z,29765.14,Target,60.0,60.0,60.00,1195.16
2,-1,2026-10-22T01:30:20.083Z,29786.00,0.4398,29785.89,2026-10-22T02:08:27.254Z,29725.89,Target,60.0,60.0,60.00,1195.16
8,-1,2026-10-22T04:34:53.463Z,29593.25,0.4398,29593.14,2026-10-22T05:41:14.110Z,29533.14,Target,60.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 3 trades.
INPUTS (all 12 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-21T23:11:05.851Z,29984.00,29993.25,29805.25,29826.00,5.00,2026-10-21T20:59:59Z,2026-10-21T20:59:00Z,CPR_TC=29674.54,PIV_D_R1=29930.42,-1 PIV_D_R1
1,2026-10-22T00:19:38.257Z,29826.50,29854.50,29753.50,29810.00,5.00,2026-10-21T23:11:05Z,2026-10-21T23:11:00Z,PIV_D_S1=29808.17,CPR_BC=29942.00,
2,2026-10-22T01:30:18.663Z,29810.00,29826.25,29756.50,29786.00,5.00,2026-10-22T00:19:38Z,2026-10-22T00:19:00Z,PIV_D_S2=29618.58,PIV_D_S1=29808.17,-1 PIV_D_S1
3,2026-10-22T01:38:03.085Z,29786.75,29798.50,29745.00,29745.00,5.00,2026-10-22T01:30:18Z,2026-10-22T01:30:00Z,PIV_D_S2=29618.58,PIV_D_S1=29808.17,
4,2026-10-22T02:14:03.581Z,29745.25,29768.00,29720.00,29720.00,5.00,2026-10-22T01:38:03Z,2026-10-22T01:38:00Z,PIV_D_S2=29618.58,PIV_D_S1=29808.17,
5,2026-10-22T03:02:47.535Z,29719.25,29723.25,29670.00,29670.00,5.00,2026-10-22T02:14:03Z,2026-10-22T02:14:00Z,PIV_D_S2=29618.58,PIV_D_S1=29808.17,
6,2026-10-22T03:32:39.439Z,29669.75,29692.00,29649.50,29650.00,5.00,2026-10-22T03:02:47Z,2026-10-22T03:02:00Z,PIV_D_S2=29618.58,PIV_D_S1=29808.17,
7,2026-10-22T03:35:42.342Z,29649.50,29651.00,29631.00,29631.00,5.00,2026-10-22T03:32:39Z,2026-10-22T03:32:00Z,PIV_D_S2=29618.58,PIV_D_S1=29808.17,
8,2026-10-22T04:34:52.355Z,29630.50,29653.25,29600.00,29600.00,5.00,2026-10-22T03:35:42Z,2026-10-22T03:35:00Z,PIV_D_S3=29466.17,PIV_D_S2=29618.58,-1 PIV_D_S2
9,2026-10-22T05:24:38.180Z,29599.75,29627.00,29570.00,29570.00,5.00,2026-10-22T04:34:52Z,2026-10-22T04:34:00Z,PIV_D_S3=29466.17,PIV_D_S2=29618.58,
10,2026-10-22T05:44:11.388Z,29570.25,29598.50,29530.00,29530.00,5.00,2026-10-22T05:24:38Z,2026-10-22T05:24:00Z,PIV_D_S3=29466.17,PIV_D_S2=29618.58,
11,2026-10-22T05:59:59.408Z,29529.75,29548.75,29507.25,29545.00,5.00,2026-10-22T05:44:11Z,2026-10-22T05:44:00Z,PIV_D_S3=29466.17,PIV_D_S2=29618.58,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=0 2026-10-21T23:11:05.851Z side -1 fired PIV_D_R1: PIV_D_P=29661.08; PIV_D_R1=29930.42; PIV_D_R2=30172.83; PIV_D_R3=30442.17; PIV_D_S1=29418.67; PIV_D_S2=29149.33; PIV_D_S3=28906.92; PIV_W_P=29983.08; PIV_W_R1=30697.42; PIV_W_R2=32003.58; PIV_W_R3=32717.92; PIV_W_S1=28676.92; PIV_W_S2=27962.58; PIV_W_S3=26656.42; CPR_TC=29674.54; CPR_BC=29647.62
k=2 2026-10-22T01:30:18.663Z side -1 fired PIV_D_S1: PIV_D_P=29960.58; PIV_D_R1=30150.17; PIV_D_R2=30302.58; PIV_D_R3=30492.17; PIV_D_S1=29808.17; PIV_D_S2=29618.58; PIV_D_S3=29466.17; PIV_W_P=29983.08; PIV_W_R1=30697.42; PIV_W_R2=32003.58; PIV_W_R3=32717.92; PIV_W_S1=28676.92; PIV_W_S2=27962.58; PIV_W_S3=26656.42; CPR_TC=29979.17; CPR_BC=29942.00
k=8 2026-10-22T04:34:52.355Z side -1 fired PIV_D_S2: PIV_D_P=29960.58; PIV_D_R1=30150.17; PIV_D_R2=30302.58; PIV_D_R3=30492.17; PIV_D_S1=29808.17; PIV_D_S2=29618.58; PIV_D_S3=29466.17; PIV_W_P=29983.08; PIV_W_R1=30697.42; PIV_W_R2=32003.58; PIV_W_R3=32717.92; PIV_W_S1=28676.92; PIV_W_S2=27962.58; PIV_W_S3=26656.42; CPR_TC=29979.17; CPR_BC=29942.00
```

#### td 20261016 (sess_id 202610160, Asia session, grid week 184)
- bars of the session: 4, first known 2026-10-15T23:28:24.976Z, last known 2026-10-16T05:59:58.154Z; rebuilt-from-tape check 4/4/4; threshold values: L=10, thr_contracts=217.666, s_vol=0.871
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
1,2026-10-16T02:27:30.569Z,1,CPR_TC,30063.38,30114.00,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
1,1,2026-10-16T02:27:31.742Z,30113.75,0.4398,30113.86,2026-10-16T03:50:17.816Z,30173.86,Target,60.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 4 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-15T23:28:24.976Z,30089.00,30128.00,30010.50,30022.00,5.00,2026-10-15T20:59:59Z,2026-10-15T20:59:00Z,PIV_D_S1=29955.08,CPR_TC=30246.46,
1,2026-10-16T02:27:30.569Z,30022.00,30114.75,29959.25,30114.00,5.00,2026-10-15T23:28:24Z,2026-10-15T23:28:00Z,CPR_TC=30063.38,PIV_D_R1=30350.50,+1 CPR_TC
2,2026-10-16T04:47:48.904Z,30114.25,30211.75,30074.00,30197.00,5.00,2026-10-16T02:27:30Z,2026-10-16T02:27:00Z,CPR_TC=30063.38,PIV_D_R1=30350.50,
3,2026-10-16T05:59:58.154Z,30196.50,30225.00,30161.75,30191.25,5.00,2026-10-16T04:47:48Z,2026-10-16T04:47:00Z,CPR_TC=30063.38,PIV_D_R1=30350.50,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=1 2026-10-16T02:27:30.569Z side +1 fired CPR_TC: PIV_D_P=29986.50; PIV_D_R1=30350.50; PIV_D_R2=30560.75; PIV_D_R3=30924.75; PIV_D_S1=29776.25; PIV_D_S2=29412.25; PIV_D_S3=29202.00; PIV_W_P=31177.25; PIV_W_R1=31562.50; PIV_W_R2=32001.75; PIV_W_R3=32387.00; PIV_W_S1=30738.00; PIV_W_S2=30352.75; PIV_W_S3=29913.50; CPR_TC=30063.38; CPR_BC=29909.62
```

#### td 20261009 (sess_id 202610090, Asia session, grid week 183)
- bars of the session: 4, first known 2026-10-08T23:57:04.562Z, last known 2026-10-09T05:59:57.199Z; rebuilt-from-tape check 4/4/4; threshold values: L=10, thr_contracts=214.280, s_vol=0.857
SIGNALS (raw events of the session: 1 in total; 'trade' = Y if the grid engine took it, otherwise blocked by the open position or entry after the session end [READING])
```csv
k,signal_bar_known_utc,side,fired_line,level_at_T0,close,u_trigger,trade
2,2026-10-09T03:59:21.116Z,1,PIV_D_P,31046.00,31115.00,5.00,Y
```
TRADES (grid engine; entry = first print >= signal known time + 1 s, plus slippage; entry_raw = that print's price; net = gross - 0.242 pt)
```csv
k,side,entry_utc,entry_raw,slip_ticks,entry_px,exit_utc,exit_px,exit_reason,stop_pts,tgt_pts,gross_pts,net_usd
2,1,2026-10-09T03:59:22.226Z,31116.25,0.4398,31116.36,2026-10-09T05:56:19.744Z,31176.36,Target,60.0,60.0,60.00,1195.16
```
- check: the independent print-by-print scan equals the sim_slice points for all of 1 trades.
INPUTS (all 4 bars; u_trigger = the trigger's own unit (5.0 pt for plain variants; rolling-100 median bar range shifted one bar for native variants; NOT the bracket unit, which is the stop/target of TRADES); level columns = the nearest finite line below / at-or-below the close and above the close among the module's lines at the bar's decision time T0; every line value is in the CSV file)
```csv
k,known_utc,open,high,low,close,u_trigger,T0_utc,line_minute_utc,line_below,line_above,event
0,2026-10-08T23:57:04.562Z,31020.50,31072.50,30967.75,30984.00,5.00,2026-10-08T20:59:59Z,2026-10-08T20:59:00Z,PIV_D_S3=30939.17,PIV_D_S2=31041.08,
1,2026-10-09T01:40:39.014Z,30984.50,31034.00,30953.00,31011.00,5.00,2026-10-08T23:57:04Z,2026-10-08T23:57:00Z,PIV_W_P=30896.08,CPR_TC=31011.12,
2,2026-10-09T03:59:21.116Z,31011.00,31115.50,31009.50,31115.00,5.00,2026-10-09T01:40:39Z,2026-10-09T01:40:00Z,CPR_BC=31080.88,PIV_D_R1=31300.00,+1 PIV_D_P
3,2026-10-09T05:59:57.199Z,31114.75,31177.00,31097.50,31158.25,5.00,2026-10-09T03:59:21Z,2026-10-09T03:59:00Z,CPR_BC=31080.88,PIV_D_R1=31300.00,
```
LINES at each traded signal bar (all finite lines at T0, price points):
```
k=2 2026-10-09T03:59:21.116Z side +1 fired PIV_D_P: PIV_D_P=31046.00; PIV_D_R1=31300.00; PIV_D_R2=31623.75; PIV_D_R3=31877.75; PIV_D_S1=30722.25; PIV_D_S2=30468.25; PIV_D_S3=30144.50; PIV_W_P=30896.08; PIV_W_R1=31435.42; PIV_W_R2=31821.83; PIV_W_R3=32361.17; PIV_W_S1=30509.67; PIV_W_S2=29970.33; PIV_W_S3=29583.92; CPR_TC=31011.12; CPR_BC=31080.88
```

## D. EXISTING VERSUS NEW, AND A ROUGH LIST OF WHAT WOULD HAVE TO BE CODED (READING; effort words are my judgement, not an estimate in hours)
**D1. Shared infrastructure for any of these books** (nothing here is specific to one book): (1) a continuous per-row bar series over ALL six session codes with the engine's reset rule at every session boundary and contract roll; (2) the daily scale table (stats_day: trailing-20-row medians of daily volume / prints / range, r0 constants; D8_BAR_DEFS section 2) built nightly, hole handling decided (stored vs hole-filled, as in the NY AM pages); (3) a 1-minute NQ series with roll back-adjustment and the label-day / ISO-week / month bookkeeping (D8Asia.cs already keeps a 1-minute series, READING); (4) the T0 level lookup (previous bar's whole-second close, minute index, 120 s staleness) and the line-at-minute-i convention (uses minutes < i); (5) the generic level_events logic for the variants used (below) with plain u = 5.0 pt or native u (rolling-100 median range shifted one bar, min 20, floor 0.5 pt) - D8Asia.cs has LevelBreakNative (break_native, n = 2) only; (6) session filter, part == 0, one position, flat at the session end, and the book's bracket (fixed points or the unit rule clip(m x u, 10, 120)).

**D2. Bar builders needed on this page:**
- `dchg`: spec exists, class by parameter - dchg_40 specified (D8_BUILD_SPEC L8cfda948); SwingBuilder(theta) in D8Asia.cs is the same kernel; theta rule here = max(2, round(N x s_rng)) not the ATR rule. Effort: small (SwingBuilder with theta = max(2, round(N x s_rng))).
- `frenko`: exists - frenko_40 specified (D8_BUILD_SPEC L6b373671); class FlexRenkoBuilder in D8Asia.cs (same book bar). Effort: small (class exists).
- `tsf`: NEW - no spec page, no class; VolumeBuilder (cumulative volume) exists but tsf needs a per-print size filter AND the print-granularity decision. Effort: medium plus a DECISION on print granularity (see risk flag).

**D3. Level modules needed on this page:**
- `fibr_on`: spec exists - D8_NYAM_SPEC_L43f0cbfb verified the 18 overnight Fibonacci lines from tape (NY AM, false_break M 3, k 0.5); not in D8Asia.cs; here the Asia effect (lines NaN except bar 0) is new. Effort: small (18 lines from the overnight H/L, available only from 09:30 ET).
- `ob15`: NEW - no spec, no class. Effort: medium (15-min aggregation, ATR14 ewm, order-block state machine with 10-day memory).
- `ob5`: NEW - no spec, no class. Effort: medium (as ob15 on 5-min bars, 3-day memory).
- `piv_floor`: lines exist in D8Asia.cs; trigger by parameter - pivot lines (Piv()) and LevelBreakNative (break_native n=2, k) exist for L6b373671; plain break n=1, k=0 and the 16-line set incl. weekly and CPR need checking against pivLines. Effort: small (lines exist in D8Asia.cs; check list incl. weekly and CPR).
- `swsr5`: NEW - no spec, no class. Effort: medium-large (5-min fractal pivots, broken-swing polarity lines, equal-high/low clusters).
- `vwap`: lines spec only; no VWAP code in D8Asia.cs - break (plain and native) specified for L7cc56d99 / L9c2622b0 / D8_TRIGGER_DEFS 3.7 D; retest and the 8 VWAP lines are specified in 3.7 but there is no VWAP class in D8Asia.cs (grep 'vwap' = 0 hits). Effort: medium (8 anchored VWAP series on the 1-minute series: day / RTH / London / prior-day / two anchored at the prior RTH extreme minutes / week / month, each with its validity gate).

**D4. Trigger variants needed:** `break`, `break_native`, `false_break_native`, `retest` (definitions in each book's section 2; the 4 base events break / reject / retest / false_break are all in fd_common.level_events, about 35 lines of Python).

**D5. Per book: what has to be coded on top of D1 (READING)**
- Wff6cb74e (false_break_native M=1/k=0.0): bar `tsf_2_700` [NEW]; module `ob5` [NEW].
- W1539c680 (break_native n=3/k=0.5): bar `tsf_10_30` [NEW]; module `swsr5` [NEW].
- W87b89d8f (retest M=10/tol=0.5): bar `dchg_10` [spec exists, class by parameter]; module `vwap` [lines spec only; no VWAP code in D8Asia.cs].
- W4a911926 (break n=1/k=0.0): bar `tsf_10_60` [NEW]; module `ob15` [NEW].
- W0778abb1 (false_break_native M=1/k=0.0): bar `frenko_40` [exists]; module `fibr_on` [spec exists].
- W0d8714f7 (break n=1/k=0.0): bar `tsf_10_250` [NEW]; module `piv_floor` [lines exist in D8Asia.cs; trigger by parameter].

**D6. Match test plan (READING):** run the live builder on the same tape for the three dated sessions of each book and compare (a) the bar closes and known times, (b) the line value of each line at T0 (CSV file), (c) the signal bars and fired lines (SIGNALS block), (d) order time = floor(known) + 2 s for the live engine versus signal known time + 1 s for the grid, (e) the exit reason and, within the stated slippage, the trade prices.

## E. OPEN POINTS FOR LEAD (READING unless marked)
- Print granularity for `tsf` (and any activity bar): the grid used the old per-record tape; D8 uses run-merged prints. A tsf book needs a LEAD decision before coding (build the old record semantics, or re-run the books on a run-merge `tsf`).
- Line files are the engine's stored files (written 2026-11-17, data to 2026-11-13). The trade tape has no files for 2026-10-31..11-04 (D8_BAR_DEFS), which touches profile / pivot / volume lines built over those days (see D8_NYAM_SPEC_Le4fede95 / B7bfd33b7 for the PRF5 hole); every dated session on this page is before 2026-10-25, so none is affected.
- Shared inputs inside the register [SPEC]: `dchg_N` and `kagi_N` rows are the SAME bars (same kernel, same thresholds), so a dchg book and a kagi book with the same module/variant/params/bracket produce the same signals (the Test 8 table lists such pairs, e.g. Wb1ab799c vs W050c781f, W10e7f4cd vs Wca8c5296); books on the same bar row share the bars but not the signals. A coder needs one builder for both.
- The 'level at T0' rule and the fact that Asia bar 0 / NY AM bar 0 take their lines and memory from the previous session are engine behaviours an NT8 coder would not guess; they are the main source of mismatch risk.
