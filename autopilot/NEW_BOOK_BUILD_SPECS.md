# NEW_BOOK_BUILD_SPECS - what a NinjaScript builder needs to code each new NY book EXACTLY as tested
Owner W-SPEC. Order 1415Z (autopilot/DIRECTIVE_NY_FIRST_BUILD_SPECS_20261118_1415Z.md). Research only; nothing here touches the execution server or a live chart.
**Version v0 (14:25Z): COMMON FACTS + TRIGGER-FAMILY READINGS + SPEC TEMPLATE + TOOLING. No finalist is entered yet.** v1 (provisional top 6 per NY session) is due 16:30Z, final 19:00Z.
Finalists come from autopilot/NEW_BOOK_SHORTLIST.md (W-SHORT) and autopilot/NEW_BOOK_ENGINE.md (engine rows). Every row below states which stage it has reached; a row whose look-ahead gate (stage 1, autopilot/BAR_LOOKAHEAD_GATE.md) is not PASS is marked "NOT FINAL".
Facts are read from the harness code (file : function). Where something is unknown it says UNKNOWN.

---
## A. COMMON FACTS (apply to every finalist unless its own block overrides them)

### A1. What the screen numbers mean (so the build reproduces the tested trades)
| item | rule as tested | where |
|---|---|---|
| Signal timing | a signal is an EVENT on the bar series, emitted at the bar's KNOWN time (`t_close`, ns): the print that completes the bar. Row i uses bars 0..i only; the harness runs a truncation (look-ahead) test on every module. | th_grid/README_TRIGGER_CONTRACT.md; th_grid/check_trigger.py; th_grid/gaudit.py : audit_cell (6 random cuts) |
| Level / line timing | every level used at bar j is the value known at the bar's decision time T0_j = max(t_close[j-1], t_open[j]) (the START of bar j); level lines are 1-minute-grid arrays whose entry i uses minutes < i only (last minute with start <= T0, stale limit 120 s); the bar's own o/h/l/c are compared with that frozen level. | th_grid/triggers_d/fd_common.py : decision_s, line_index, line_at |
| Entry | first trade print with ts >= signal ts + 1 s (`LAT_FILL` = 1 s), plus measured adverse slippage: mean adverse points per (session, bar family) at 2 lots, latency 0 ms, window ALL. NY AM: range/price bars 0.178, volume/activity bars 0.121, time bars -0.093 (favourable on average). NY PM: 0.179 / 0.101 / -0.050. | th_grid/gcore.py : run_multi (`i0 = searchsorted(ts, t + 1e9)`); th_grid/gjob.py : slip_table (BAR_SLIPPAGE_TABLE.csv); th_swap/fill.py : tape_fill |
| Entry price used in P&L | raw first print price (in ticks) + side x slippage. NEVER the bar close. | gcore.run_multi : `e = px[i0] + s*slip_t` |
| Stop | resting stop at entry -/+ stop points; hit = first print AT or THROUGH the stop; exit price = that print -/+ 1 tick adverse (stop slippage 1 tick). | gcore.run_multi |
| Target | resting limit at entry +/- target points; hit only when a print trades 1 tick THROUGH the level; exit AT the level. | gcore.run_multi |
| Session end | flat at the last print before the session end (-/+ 1 tick): sessions end 02:00 (Asia), 08:30 (London), 09:30 (pre), 12:00 (NY AM), 16:00 (NY PM), 18:00 ET. | th_swap/common.py : sess_end_ns, sess_code |
| One position | one position at a time per (signal set, bracket): a signal whose entry print is at/before the previous exit print is skipped. No stacking, no re-entry rule beyond that. | gcore.run_multi (`last_exit`) |
| Cost | $4.84 round trip per NQ contract = 0.242 pt, subtracted from every trade. Engine dollars are BASE lots; live lots = max(1, floor(1.75*base+0.5)). | gcore.py COST_PTS; outputs/FEES.md |
| Sessions (ET) | Asia 18:00-02:00 (code 0), London 02:00-08:30 (1), pre 08:30-09:30 (2), **NY AM 09:30-12:00 (3)**, **NY PM 12:00-16:00 (4)**, close 16:00-18:00 (5). The session of a signal is the session of its SIGNAL bar. | th_swap/iface.py (SESS); th_swap/common.py : sess_code |
| Trading date | `sess_id = trading_date*10 + code`, trading_date = (ET time + 6 h) calendar date (the 18:00 ET open belongs to the NEXT trading date). | th_swap/common.py : sess_id_of |
| Part bars | the last (truncated) bar of a session is flagged `part=1` and is NEVER a signal bar. | th_grid/gjob.py : run (`part_ok`) |

### A2. Brackets in the harness (the tested number is one of these seven)
`gjob.BR_NAMES = [plain60/60, sym8u, sym15u, sym30u, asym10u/20u, asym20u/10u, asym15u/30u]` (th_grid/gjob.py : bracket_arrays; th_grid/gcore2.py : bracket_pts).
u = trailing MEDIAN of (high - low) of the bar series over the last **50 bars** at the signal bar (min_periods 10, floor 0.25 pt); each stop and each target is clipped to **[10, 120] points**. plain60/60 = 60 pt stop and 60 pt target.
**Wide-bar warning:** on event / activity bars with a large median range (u of 8 pt or more) 15u or 30u hits the 120 clip, so "sym15u" or "asym20u/10u" IS a 120/120-point bracket (London cdr_100 and the NY AM vol_500 level cells are like this). Each finalist block states the median stop / target in points and dollars; do not code "15u" without that number.
Level modules also use a different "unit" for their own widths (the `_native` variants): `fd_common.unit(b, n=100)` = trailing median bar range over the last **100** bars shifted by one, floor 0.5 pt. The `plain` variants use fixed u0 = 5 points (lv_base.py U0).

### A3. Bar construction (W-BAR store; builder th_bars/build_month.py + kernels.py; registry autopilot/BAR_REGISTRY.csv)
- Bars are built from NQ TRADE PRINTS (MBO T records) per trading session; a bar never spans a session boundary; a bar is KNOWN at `known_ts` (the print that closes it; for time bars the bucket end; the truncated last bar of a session is `part=1`).
- Scaled sizes: threshold = size x s_x, where **s_x[date] = trailing median of the daily statistic x over the PRIOR 20 trading dates (needs >= 5, else R0) / R0**, R0 = median of x over the first 60 trading dates (constant). Fixed at session open from trailing data only (th_bars/build_month.py : scales). R0 constants: volume 610,702 contracts/day, prints 373,169/day, dollars 1.696e11, range 191.5 ticks (stats_day.parquet). Absolute thresholds on any date: `python3 -I code/th_spec/thresholds.py` (prints the last 10 dates, e.g. on 2026-11-13 vol_500 = 558.5 contracts, tick_500 = 691 prints, rng_80 = 257 ticks = 64.3 pt).
- Rules per type: volume: cumulative contracts >= size x s_vol, closing print belongs to the closing bar (NT8 splits the closing print: stand-in, see C); tick: prints >= size x s_n; range: a print that would make high-low exceed max(1, round(size x s_rng)) TICKS closes the bar and opens the next one (known at that print); dollar: cum price x 5 x size >= size x 300,000 x s_dol; delta: |cumulative aggressor delta| >= size x s_vol; cdr: (max - min) of the running cumulative delta >= size x s_vol. Others: the `definition` column of BAR_REGISTRY.csv, one row per type.

### A4. How the engine run was made (what "layers ON" means for a row)
The engine rows of NEW_BOOK_ENGINE.md come from the exact engine on JL3 (identity first: JL3 202610 = 691 trades / net_fee 37,159.82; 202504 = 637 / 41,239.76) with the cell's signals injected (th_swap_hook/swap_inject.py; th_grid/mk_sets.py). In an injected row the signals pass the host book's own try_entry, bracket, cuts, layers and lots; therefore a PLAIN 60/60-like cell is directly comparable with the engine, a cell with its own bracket is not (each finalist block states which it is). The live layers are listed in autopilot/ANSWER_LIVE_LAYERS_20261116.md; each finalist block lists which were ON in its engine run and which were NOT applied (the screen and fast-replay numbers have NO layers).

### A5. Native NT8 vs custom BarsType (autopilot/BAR_REGISTRY.csv columns nt8_mapping / nt8_fidelity)
| our row | NT8 | fidelity note |
|---|---|---|
| time_s (seconds) | native Second | identical |
| time_m (minutes) | native Minute | identical for 1,2,3,5,10,15,30 min; DIFFERENT for 4,7,13,20,45,60,90,120,240 min in some sessions (NT8 anchors on its 18:00 template; offsets in NT8_FIDELITY.csv): odd periods need a custom anchor |
| tick | native Tick | print-count equality with the NT8 feed unverified; sizes are daily-scaled (s_n) so the live book needs the same scaling table |
| vol | native Volume | good stand-in; NT8 splits the closing print (28% of our bars carry an overshoot of mean 1.0 contract); sizes are daily-scaled (s_vol) |
| rng | native Range | same rule, N tick inclusive/exclusive unverified; sizes daily-scaled (s_rng) |
| renko | native Renko | same (2-brick reversal) |
| pnf, kagi | native PointAndFigure / Kagi | box / first-column init differs; construction look-ahead gate PASSED 13:30Z for pnf (W-GATE publishes the rest) |
| dol, vsess, tsf, tib, vib, dib, trb, vrb, drb, dlt, cdr, vnorm, cusum, urenko, mrenko, wrenko, ... | custom BarsType | buildable; rule text in BAR_REGISTRY.csv `definition` |
NOTE for the 16:30Z statement: a native-bar finalist is one on time_s, time_m (periods 1,2,3,5,10,15,30), tick, vol, rng, renko; the scaled-size rows additionally need the daily threshold table (`s_x`) delivered to the chart (a per-day constant), which is a small addition, not a custom bar.

---
## B. TRIGGER-FAMILY READINGS (so each finalist block can cite exactly)
Common code for every level trigger: `th_grid/triggers_d/lv_base.py : make` (module = a SET of lines, all tested with the same four event logics) and `fd_common.py : level_events`.
- **One signal per bar, any line of the set**: events are computed for every line of the set; a bar fires if ANY line fires (`LG |= lg`); a bar with both a long and a short event is dropped (`events_to_frame`); `fired` = the first listed line that fired (the level price shown in the worked examples). All lines of the set are live at the same time; there is no "first touch only" memory beyond the event edge (`edge(m)` = the bar where the condition first becomes true).
- **break(n, k)**: n consecutive closes beyond level +/- k x u (n = 1,2,3; k = 0, 0.25, 0.5), and the bar before the sequence was NOT beyond (fresh). Break up = long, break down = short. Event bar = the n-th close.
- **reject(tol, conf)**: previous close on one side; the bar pierces/touches within tol x u of the level (tol 0, 0.5, 1.0) and closes back on its original side (`conf='close'`), or also with the bar colour agreeing (`'body'`: close below open for a short at resistance, above open for a long at support). Short at resistance, long at support.
- **retest(M, tol)**: a break close (by k x u, k = 0 here) within the last M bars (M = 3, 6, 10), then a bar that tests the level (within tol) and closes beyond it with the break's colour.
- **false_break(M, k)**: closed beyond level +/- k x u within the last M bars (M = 1, 2, 3) and the current close is back through the level: trade the failure (fade).
- `_native` variants: u = fd_common.unit (100-bar trailing median bar range); plain variants: u = 5.0 points.
- Entry for ALL of these = the market order after the signal bar's close (first print +1 s + slippage); a resting limit at the level is NOT what these cells test (only the own-bracket sdx modes do).

Families expected among NY finalists (modules in code/th_grid/trig_levels_*.py, real code in triggers_d/lv_*.py):
| module (line set) | lines (all live at once) | built by |
|---|---|---|
| levels_round | multiples of 100, 250 and 500 points nearest to the PREVIOUS bar close (price arithmetic only) | lv_round.py |
| levels_vwap | VWAP0 (anchored 18:00 ET, from minute 30, volume > 2,000), RVWAP0 (anchored 09:30), LVWAP0 (anchored 02:00), YVWAP (prior RTH day), AVPDH / AVPDL (VWAP anchored at the prior RTH day's high / low minute), WVWAP, MVWAP; typical price (H+L+C)/3 x 1-min volume | lv_vwap.py; fd_levels.py : vwap_anchored |
| levels_vwap_bands | +/-1 and +/-2 sigma bands of VWAP0 (18:00), RVWAP (09:30), LVWAP (02:00); sigma = volume-weighted std of typical price | lv_vwap_bands.py |
| levels_session_hl | completed-session highs/lows: Asia, London, pre, overnight (18:00-09:30), NY AM (usable only after the session completes) | lv_session_hl.py; fd_levels.py (`SESS` minute windows) |
| levels_open_range | OR5, OR15 high/low (09:30 + 5 / 15 min), IB30, IB60 (30 / 60 min) and 1.5 x IB extensions; usable only after the range completes | lv_open_range.py |
| levels_prior_day | prior-day RTH and full-session high / low, prior RTH close | lv_prior_day.py |
| levels_stack | confluence of families (fib, swing, pivot, vwap, profile, prior, supply-demand): nearest line per family to the previous close; stack = largest group within cw x u; k >= 2 families | lv_stack.py |
| levels_swsr5/15/60 | fractal swing S/R on 5m / 15m / 60m aggregated bars (strength 2 each side, confirmed at the END of the right-hand bar j+2), equal highs/lows, polarity-flip lines | fd_levels2.py (swings: `pivots`) |
| levels_fib*, fibr_* | Fibonacci retracement/extension of the last confirmed zigzag leg (R236...R786, E1272...E2000) on 5/15/60 m; range fibs from the prior RTH day / overnight / OR15 / IB30 / developing session | fd_levels2.py |
| levels_piv_* | daily floor pivots from the prior RTH day (P, R1-3, S1-3), Camarilla H1-4 / L1-4, weekly from the prior ISO week | fd_levels2.py : pivset |
| levels_sd*, sdx* (supply/demand) | zones drawn on aggregated time bars (5/15/30/60 m, or on rng_28 / renko_28 / vol_1100): full rules in autopilot/SD_ZONE_RULES.md (v1 strict + v2 definitions A, Abrk, Agap, B, E; entries rej, rej_flow, rej_zone, lim_prox, lim_mid, break, retest); zone code fd_sd.py / fd_sd2.py, entry code lv_sd_base.py | triggers_d |
Other families that may appear: bands (th_grid/trig_bands_*.py), structure (trig_structure_*), tape/order-flow (trig_tape_*, th_grid/triggers_c: need the order book and the aggressor side: DATA item 6), momentum, barnative, xmarket (other markets: DATA item 6).

---
## C. SPEC TEMPLATE (one block per finalist; every item mandatory)
```
### <session> #<n>  <one-line name>         stage reached: <2|3|4|5>   look-ahead gate: <PASS|FAIL|PENDING>   label: <BUILD-READY|NEEDS MORE|DROPPED>
Cell id: session | bar row | module.variant | params | bracket | side   (harness key; list file + function)
1. BAR   type, size, native or custom, construction rule in prints, first bar of a session, size per day (s_x formula + today's absolute threshold), session resets (ET), NT8 fidelity note.
2. TRIGGER  line set (every line, how found, lookbacks), event (break/reject/retest/false break/limit) with all parameter values, long/short/both, what invalidates a line, how many lines live, first-touch rule; code path file : function.
3. ORDER  entry order type/timing as tested (first print >= signal + 1 s, slippage by session/family), bracket in POINTS (median stop/target, min/max after the clip) or the exit recipe, flat time, one position, re-entry.
4. SESSION WINDOW (ET) and no-trade times used.
5. LAYERS ON in the engine run (D7 names) / layers NOT applied / lots.
6. DATA  anything beyond NQ prints.
7. THREE WORKED TRADES from the last month: date, time ET, level price, entry, exit, P&L.   (code/th_spec/examples.py, tape-walk reproduced)
Evidence line: L6M / L3M / each prior year in $ at 1 lot; trades per day; null percentile; engine row (add / replace K7,P7,M7); correlation with the live NY books.
```

---
## D. FINALISTS
*(none entered at v0 - waiting for NEW_BOOK_SHORTLIST.md stage 2 at 15:15Z and NEW_BOOK_ENGINE.md rows)*

---
## E. TOOLING (reproduce any number here)
- `code/th_spec/examples.py SESSION ROW MODULE VARIANT 'PARAMS' BRACKET [MODE] [from] [to] [N]` - worked example trades for a market-entry fixed-bracket cell: signal close (ET), fired level, fill, stop / target prices, exit, reason, net points and dollars at 1 lot. Brute-force tape walk identical to th_grid/gaudit.py. Run on a box with the tape cache (`/mnt/l2/l2vast/_grid/tape/<YYYYMM>`).
- `code/th_spec/thresholds.py` - R0 constants and today's absolute thresholds of the scaled bar rows.
- Level-cell lists: `/mnt/l2/l2vast/_grid/out/level_nr_best.csv`, `level_nr_qual.csv` (W-LEVEL), `candidates_all.csv`, `exit_results.csv`.
