# D8_NYAM_SPEC_Le4fede95: hand-verified coding spec, NY AM weighted-stack member Le4fede95.BRF90_30 (bars swing_atr_0.4, profile-node false break M 2 / k 0.5, both sides, bracket fixed 90 stop / 30 target)

Written 2026-11-24 ~21:00Z by a relay sub-agent (not typed by Josh), order autopilot/DIRECTIVE_20261124_2026Z_JOSH_NYAM_WEIGHTED_NINE_FIT_AND_CODE_NOW.md item 5. Information only: no engine edit, nothing queued, nothing live, no spend, nothing deleted (nice -n 10). Companion pages: autopilot/D8_BUILD_SPEC.md block AUTO:BOOK:Le4fede95, autopilot/D8_TRIGGER_DEFS.md 3.7, autopilot/D8_PARITY_Le4fede95_20261027.md / _20261110.md, raw tape of td 20261110 NY AM: autopilot/D8_PARITY_TAPE_20261110_NYAM.md (records, side_d8; the swing bars use every record UNMERGED).

STATUS (what is verified, what is open). VERIFIED by me against the engine and the stored data on td 20261027 and td 20261110 (and over the whole history where stated): (1) bars rebuilt from the raw tape with the engine kernel k_dchg = stored bars on every column (98 / 184 bars, 0 differing rows); (2) the module `trig_levels_profile_nodes` false_break_native re-run on the stored bars reproduces the engine events file Le4fede95_R0_F90_30.parquet EXACTLY: 19,161 of 19,161 events (all history) and 17 / 27 on the two sample days; (3) my own re-implementation of the rule from the INPUTS tables below reproduces the 17 and 27 signals; (4) the ten profile lines (PRF1 HVN1, HVN2, LVN1, LVN2, SPH, SPL; PRF5 HVN1, HVN2, LVN1, LVN2) recomputed from the raw tape with the engine's own profile functions (code/th_grid/triggers_d/fd_profile.py:19-45 copied) equal the stored line values to 0.01 pt on both days; (5) T0 and u columns of the INPUTS = the engine helpers fd_common.decision_s / unit on the stored bars; (6) the TRADES blocks = the engine runs (9 and 12 trades). OPEN / NOT VERIFIED: the PRF5 composite on td 20261110 uses only the five store days 1029, 1030, 1105, 1106, 1109 because the engine store has no 1102-1104 (see section 5); td 20261125 scale constants (see section 2); roll handling (no roll in the sample days); fill simulation (section 7, cited not re-run); the NT8 chart cannot reproduce the profile lines unless the strategy keeps its own volume-at-price history (section 4).

## 1. Identity
- Stack entry `Le4fede95.BRF90_30`, session NY AM (ET 09:30-12:00, session code 3), cell: row `swing_atr_0.4`, module `trig_levels_profile_nodes`, variant `false_break_native`, params {"M": 2, "k": 0.5}, mode both (code/th_brkt/firstlook cells; /mnt/l2/l2vast/_nye/ladder_cells.json). The ladder cell label says bracket sym15u; the STACK entry uses the FIXED bracket F90_30 (name BRF90_30): stop 90 points, target 30 points, both fixed, 1 lot. Events file /mnt/l2/l2vast/_brkt/ev/Le4fede95_R0_F90_30.parquet (19,161 events, columns ts, side, stop_pts, tgt_pts, lots, exit_ts; stop_pts = 90 and tgt_pts = 30 on every row, checked). Engine base set TL3_ALN_NY_Le4fede95_R0BRF90_30.
- Sides: BOTH (events file: 9444 long, 9717 short).
- Entries per day (signals = events file rows, before the one-position rule): mean 26.1, median 23, p90 51, max 121 over 733 trading days; last 20 trading days mean 24.3. Sample days: td 20261027 = 17 signals, td 20261110 = 27 signals. Engine TRADES per day after the one-position rule (days with at least one trade, 2026): mean 8.5, median 7, max 35; last 20 days mean 7.9; sample days 9 and 12 trades.

## 2. Bar kernel: swing_atr_0.4 (directional-change leg bar), exact rules
Code: code/th_bars/kernels.py:197-223 `k_dchg` (integer ticks of 0.25 pt, every tape RECORD is one step, NO print merge: this row is UNAFFECTED by the D8 print rule, autopilot/D8_PRINT_RULE.md section 5); built at code/th_bars/build_month.py:130-132.
- Reversal size theta (ticks, constant for the whole trading date): `atr = max(1.0, 4 * abs_rng / 10)` where abs_rng = the trailing-20-row median daily range in POINTS (table below; build_month.py:131), `theta = max(2, round(0.4 * atr))` (build_month.py:132; numpy round = half to even). The "ATR" is therefore a daily-range quantity written in points and used AS ticks: td 20261110: abs_rng 583.75 -> atr 233.5 -> 0.4 x 233.5 = 93.4 -> theta 93 ticks = 23.25 pts; td 20261027: 419.375 -> 167.75 -> 67.1 -> 67 ticks = 16.75 pts. NOT an intraday ATR.
- State reset: at every change of session key (td x 10 + session code) or instrument id the state restarts (kernels.py:202): `started=False`, bar index 0. The first print of a session sets ehi = elo = st = p, d = 0 (no direction), volume/count/delta counters start.
- Every record adds its size to the open leg's volume and +1 to its count (kernels.py:206) BEFORE the tests (the confirming print is in the closing leg).
- Undecided phase (d = 0, kernels.py:208-212): update ehi/elo; if p - elo >= theta then UP leg: d = 1, st = elo (the low), ext = p; elif ehi - p >= theta then DOWN leg: d = -1, st = ehi, ext = p (the up test is first).
- Up leg (d = 1, kernels.py:213-217): if p > ext: ext = p (new extreme, strictly greater); elif ext - p >= theta: the leg is COMPLETE: emit a bar o = st, h = ext, l = st, c = ext (open = low = start level, close = high = extreme level), volume/count/delta of the leg including the confirming print, first-print time t0, `known` time = the timestamp of the confirming print itself (ts[i]); then st = ext, d = -1, ext = p (the confirming print price), counters reset to 0, t0 = ts[i]. Down leg mirrored (kernels.py:218-222): p < ext -> ext = p; elif p - ext >= theta: emit o = h = st, l = c = ext; st = ext, d = 1, ext = p.
- A print that makes a new extreme never reverses (the `elif`). The reversal print's price becomes the new leg's first extreme `ext` (not the old extreme). The leg that is still open at session end is NOT emitted (no flush, part is always 0 for this row). Bar `known_ts` is the closing (confirming) print's timestamp; it is a whole bar only at that print.
- Timestamps are the tape's record timestamps (store convention; the NT8 export differs by ~13 ms, see autopilot/D8_ASIA_NEWBOOK_INPUTS.md section 1).
- VERIFIED: rebuilt from the tape of td 20261027 (NY AM records: 169,694 records; session key 202610273) and td 20261110 (234,912 records, raw tape page) with theta 67 and 93: 98 and 184 bars, all of o, h, l, c, volume, n, t0, known, part identical to the stored bars (/mnt/l2/l2vast/_bars/swing_atr_0.4/). Bar counts per day (NY AM): 98 and 184.
**Day scales (how the per-day constant is built; identical code for every book of this page).** code/th_bars/build_month.py:13-32 `scales()`: for each trading date (td = ET + 6 h) the stats row of the 20 stats rows BEFORE that td (the current day is never used; values <= 0 dropped; at least 5 values, else the first-60-day median) are medianed; scale = that median / (median of the first 60 days). Columns: `rng` = daily range in points, built per UTC trade file, max over the pieces, / 4 (code/th_bars/stats.py:18; the quirk and the A/B holes are written out in autopilot/D8_ASIA_NEWBOOK_INPUTS.md section 2); `vol` = contracts of every record of the td; `n` = number of PRINTS of the td (run merge, same price and same tape side, never across a session code), table /mnt/l2/l2vast/_d8spec/runstats/stats_day.parquet. Checked here: for td 20261110 the runstats `n` = 463,946 = my own run count of the store tape (same price + same store side, break at session-code change): equal; the `_bars` stats_day.parquet holds the record count 530,480 instead (different column), so a coder must use the merged-print count for dib / tick rows.
**Data end / holes (read first).** The engine's stats tables end at td 20261113 and have no row for 20261102, 20261103, 20261104 (and 20261105 is a half day; autopilot/D8_ASIA_NEWBOOK_INPUTS.md header). The engine trade store also lacks the days 20261102-20261104 (trade files present: 1026-1030, 1105, 1106, 1108, 1109, 1110..1113). Column A = the engine as stored (what the stored bars and events used); column B (rng-based constants only) = the same function on a table with the holes filled and 1116-1120 added from hist_replica (a FORMULA result from D8_ASIA_NEWBOOK_INPUTS.md section 2, not an engine run). Which of A or B NT8 should copy for tomorrow is NOT decided here (lead).
```csv
td,in_engine_store,s_vol,s_n,s_rng,abs_rng_pts,pnf_14_box_ticks,swing_atr_0.4_theta_ticks,vol_1700_thr_contracts,dib_6000_T0_prints
20261026,True,1.042014,1.494671,2.189948,419.375,31,67,1771.424,8968.026
20261027,True,1.042014,1.494671,2.189948,419.375,31,67,1771.424,8968.026
20261102,False,1.085206,1.577418,2.651436,507.750,37,81,1844.850,9464.511
20261103,False,1.085206,1.577418,2.651436,507.750,37,81,1844.850,9464.511
20261104,False,1.085206,1.577418,2.651436,507.750,37,81,1844.850,9464.511
20261105,True,1.085206,1.577418,2.651436,507.750,37,81,1844.850,9464.511
20261106,True,1.085206,1.577418,2.766319,529.750,39,85,1844.850,9464.511
20261109,True,1.099768,1.628065,2.929504,561.000,41,90,1869.606,9768.390
20261110,True,1.111026,1.667632,3.048303,583.750,43,93,1888.743,10005.795
20261111,True,1.105650,1.701727,3.047650,583.625,43,93,1879.605,10210.365
20261112,True,1.105650,1.701727,3.097258,593.125,43,95,1879.605,10210.365
20261113,True,1.117061,1.710014,3.216057,615.875,45,99,1899.004,10260.085
```
```csv
td,B_abs_rng_pts,B_s_rng,B_pnf_14_box_ticks,B_swing_atr_0.4_theta_ticks
20261109,583.750,3.048303,43,93
20261110,625.375,3.265666,46,100
20261111,625.375,3.265666,46,100
20261112,625.375,3.265666,46,100
20261113,648.000,3.383812,47,104
20261116,648.000,3.383812,47,104
20261117,718.250,3.750653,53,115
20261118,784.250,4.095300,57,125
20261119,784.250,4.095300,57,125
20261120,784.250,4.095300,57,125
```
Rows 20261102-04 of table A are what the engine function returns for days with no row (it clamps to the next stored row; not used by any stored bar). For td 20261125 neither column exists yet (engine store ends 20261113; hist_replica ends 20261120 in the Asia page): NOT verified.
For this book only these columns matter: `abs_rng_pts` -> `swing_atr_0.4_theta_ticks` (A) and `B_swing_atr_0.4_theta_ticks` (B).

## 3. Trigger: trig_levels_profile_nodes, variant false_break_native, M 2, k 0.5 (exact rule, every constant and unit)
Code: code/th_grid/triggers_d/lv_profile_nodes.py (line set, order below), lv_base.py:23-45 `make`, fd_common.py:58 `level_events` (false_break branch at fd_common.py:82-87), fd_common.py:20-37 (decision time and line lookup), fd_common.py:38-45 `unit`, fd_common.py:46-57 `edge` / `roll_any`, fd_common.py:112-119 `events_to_frame`; params {"M": 2, "k": 0.5}, variant string `false_break_native` (lv_base.py: `nat = var.endswith('_native')`).
1. Series: ONE continuous series of all stored swing_atr_0.4 bars (all sessions, since 2023-04; code/th_grid/gjob.py:32-46 load_bars sorts by known time). Indicators carry state across session breaks; only the SIGNAL bar must be a NY AM bar with part = 0.
2. Unit u (points) = rolling median of (high - low) of the previous 100 bars of that series, SHIFTED by one bar (bars j-100..j-1, the signal bar itself is excluded), min_periods 20, floor 0.5 pt, NaN until 20 prior bars exist (fd_common.py:38-45). The series includes bars of earlier sessions (Asia, London, ...), so NT8 needs the last 100 completed swing bars of ANY session at 09:30. Tested value on td 20261110: u 36.75 at the 6th bar, 42.25 at the last bar (column u_native_pts in INPUTS). k x u = 0.5 x u (column k_times_u).
3. Lines (10, raw prices in points, one value per minute; list order = priority order): PRF1__HVN1, PRF1__HVN2, PRF1__LVN1, PRF1__LVN2, PRF1__SPH, PRF1__SPL (previous RTH day profile) and PRF5__HVN1, PRF5__HVN2, PRF5__LVN1, PRF5__LVN2 (5-day composite). Construction in section 4.
4. Level at bar j: the value of the line at the last minute whose START is <= T0_j, where T0_j = the PREVIOUS bar's known time in whole seconds, t_close[j-1] // 1e9 (fd_common.py:20-28; the stored frames have no open time, so the decision time is the previous bar's CLOSE, even if bar j opened later; for the first NY AM bar the previous bar is the last bar of the previous session). If that minute start is more than 120 s older than T0 the level is NaN (fd_common.py:29-37). The profile lines of a day are valid from 18:00 ET of the evening before through the next RTH close, so they exist before 09:30. The bar's own close is compared with the level frozen at T0_j.
5. Per line: up_j = close_j > L_j + 0.5 u_j; dn_j = close_j < L_j - 0.5 u_j (level-true, NOT edge; each bar uses its OWN L and u); SHORT mask = (up on ANY of bars j-2, j-1) AND close_j < L_j; LONG mask = (dn on ANY of bars j-2, j-1) AND close_j > L_j; then `edge`: the mask is kept only if it was False on bar j-1 (first bar of a run). `roll_any` M = 2 looks at j-2 and j-1 only (fd_common.py:53-57). Strict inequalities. Lines with NaN level or NaN u never fire.
6. Over the 10 lines: long mask = OR of the per-line long masks, short mask = OR of the short masks; the first line (list order) that fires on a bar is the `fired` line; a bar with BOTH a long and a short (from different lines) is DROPPED (events_to_frame, fd_common.py:112-114). Each remaining bar is one signal: side +1 LONG / -1 SHORT, known at the bar's known time. The false break is FADED: failed upside break -> SHORT, failed downside break -> LONG.
7. A signal only counts as an engine event if the signal bar is in session code 3 and has part = 0 (see the ENTRY paragraph in section 5). Warm-up: 20 prior bars for u; no other warm-up.
VERIFIED: (a) module re-run on the stored bars = events file, 19,161 / 19,161 (all history; `left_only` = 0, `right_only` = 0); sample days 17 and 27, same timestamps and sides; (b) my own numpy implementation of items 4-6 operating only on the INPUTS tables below gives the same 17 and 27 signals (first bars j < 2 of a session cannot be tested from the table alone; none of the signals is there).

## 4. Lines: how each one is built (and what NT8 needs)
Code: code/th_grid/triggers_d/fd_profile.py:19-45 (`va`, `levels`), :46-60 (per-day histogram, single prints), :61-71 (5-day composite), :72-86 (placement on minutes; value x 0.25, stored float32). All from every NQ trade record of ET 09:30-16:00 (minute-of-day 570 <= m < 960) of ONE ET calendar day d, prices in ticks, volume = size; no run merge; the instrument is the front contract (no roll in the sample range).
- Histogram: hist[price tick - low] = sum of sizes.
- Value area (`va`): POC = argmax hist (first max); start a = b = POC, acc = hist[POC]; while acc < 0.7 x total: up = sum of the next 2 rows above b (hist[b+1:b+3]), dn = sum of the next 2 rows below a (hist[a-2:a]); if up >= dn add the rows above (b moves up 2 rows, clipped at the top) else add the rows below. VAH = row b, VAL = row a.
- HVN1/HVN2: smooth hist with a Gaussian kernel sigma 8 ticks, +-24 ticks (`np.convolve(hist, k/k.sum(), 'same')`); candidate peaks = rows i with sm[i] >= sm[i-1] and sm[i] > sm[i+1] and |i - POC| > 8; the two with the highest smoothed value, in that order (HVN1 = highest).
- LVN1/LVN2: candidate troughs = rows i in [max(VAL,1), min(VAH,len-2)) with sm[i] <= sm[i-1] and sm[i] < sm[i+1]; the two with the LOWEST smoothed value (LVN1 = lowest). May be missing (NaN line) if fewer than two exist.
- SPH/SPL (single prints, 30-minute brackets from 09:30: bracket = (minute-of-day - 570) // 30): rows touched by exactly ONE bracket and with volume > 0 are single-print rows; the longest run of consecutive such rows with length >= 4 gives SPL = lowest row, SPH = highest row; otherwise the lines are NaN.
- PRF5 composite: for ET day number k in the list of available days (a day is available if it has >= 1000 RTH records AND is a file of the store): add the histograms of the days k-4..k (the five latest AVAILABLE days, NOT the five latest calendar days) on a common price grid and apply the same `levels` function (POC/VAH/VAL/HVN/LVN; no SP).
- Placement: the lines of RTH day d are used on the label day (trading date) after d, from 18:00 ET of the evening until the next day's RTH close (label day = ET + 6 h). For td 20261110 the profile is that of ET day 20261109; for td 20261027 that of 20261026.
VERIFIED: recomputed from the store tape with these functions: all 10 lines of td 20261027 and td 20261110 equal the INPUTS values (max abs difference < 0.01 pt; stored values are float32 of a 0.25-pt grid). Values (points): td 20261027: HVN1 29496.50, HVN2 29471.75, LVN1 29384.25, LVN2 29357.50, SPH 29396.75, SPL 29383.25, PRF5 HVN1 29266.75, HVN2 29137.00, LVN1 29600.75, LVN2 29632.75. td 20261110: HVN1 27971.00, HVN2 27952.75, LVN1 28069.25, LVN2 28003.00, SPH 27688.50, SPL 27481.25, PRF5 HVN1 27160.75, HVN2 27167.75, LVN1 28226.50, LVN2 29398.75.
**PRF5 hole (important).** The engine trade store has no files for 20261102-20261104, so for td 20261110 the "5-day composite" = ET days 1029, 1030, 1105, 1106, 1109 (a gap of three days inside it). A hole-filled composite (RTH days 1103, 1104, 1105, 1106, 1109 from hist_replica; FORMULA with the same code, not an engine run) would give for PRF5 HVN1 28314.00, HVN2 27176.75, LVN1 28195.75, LVN2 28958.50 (instead of 27160.75, 27167.75, 28226.50, 29398.75). A chart that keeps its own last five RTH days will therefore NOT match the engine for the PRF5 lines of that day; it matches from the day the five latest available days are the five latest calendar days. The lead decides whether the NT8 build copies the engine rule (five latest available store days) or the calendar rule; for tomorrow td 20261125 the days 1118-1124 are not in the engine store yet (NOT verified).
Data NT8 needs: the strategy must keep the volume-at-price histogram (every record, sizes) of ET 09:30-16:00 for the last five RTH days plus the current (it cannot be read from the bars).

## 5. Bracket, sides, window, one position
- Bracket: stop 90.0 pts and target 30.0 pts, fixed, from the entry fill (events file: stop_pts = 90, tgt_pts = 30 on all rows). No unit rule for this book (the ladder label sym15u is not used by the stack entry).
- Sides: both (long and short signals both trade).
- Window: signals only on swing bars of session code 3 (ET 09:30-12:00; tomorrow 14:30-17:00Z, EST) with part = 0; the scheduled exit at 12:00 ET + 1 s (17:00:01Z in the sample day 20261110, 16:00:01Z on 20261027 which was EDT).
**Signal to engine event (VERIFIED in code).** Event time `ts` = floor(known time of the signal bar to whole seconds) + 2 s (code/th_nyeng/ny_build.py:32; code/th_brkt/brkt_build.py:42); events with ts >= the session-end instant are dropped (ny_build.py:33, brkt_build.py:46); session-end instant = the next ET session boundary after the signal bar (code/th_swap/common.py:32-40; for NY AM = 12:00 ET); the exit cap (N = 120 s, code/th_fakefill/cap_exit.py:9,20) is applied to the event file. Only bars with session code 3 (ET 09:30-12:00; code/th_swap/common.py:41-44) and `part` = 0 (not the truncated last bar of a session) can signal (ny_build.py:29; brkt_build.py:38-39). Sample-day checks: my re-run of the engine module on the stored bars gives the engine events file exactly for both sample days (counts below) and over the whole history (counts below).
**One-position / fill / exits (SPEC text copied from autopilot/D8_BUILD_SPEC.md block (b2), simulator code/replica/sim.py: NOT re-verified here).** MARKET order sent at event time; filled 1.0 s later (LAT_FILL) walking the 10-level book (buy at the ask side, sell at the bid side); stop = stop order at fill -/+ stop_pts (triggered by a print at/through the level, then market order walking the book), target = resting limit at fill +/- tgt_pts; ONE position per book: an event while the book is in a trade, an exit is pending or an entry is in flight is dropped (the next event after the exit is traded); scheduled session-end exit at 12:00 ET + 1.0 s (if no print follows within 120 s the exit is the last print before it); contract roll: flat 1 ns before the roll second, entries skipped roll-120 s to roll+300 s. Sizes: 1 lot per book in the engine runs (bare R0 base set; no stack rules in the TRADES blocks).

## 6. CSV blocks, td 20261027 (EDT: NY AM 13:30-16:00Z)
BARS (98 rows = every stored NY AM swing_atr_0.4 bar; known_utc = the confirming print time; first_print_or_bucket_start_utc = t0 of the leg; verified equal to the stored bars and to my kernel rebuild):
```csv
known_utc,first_print_or_bucket_start_utc,open,high,low,close,volume,session_code,part
2026-10-27T13:30:30.146Z,2026-10-27T13:30:00.000Z,29561.25,29589.5,29561.25,29589.5,4366,3,0
2026-10-27T13:30:55.718Z,2026-10-27T13:30:30.146Z,29589.5,29589.5,29541.25,29541.25,1638,3,0
2026-10-27T13:31:33.301Z,2026-10-27T13:30:55.718Z,29541.25,29601.75,29541.25,29601.75,3102,3,0
2026-10-27T13:32:12.992Z,2026-10-27T13:31:33.301Z,29601.75,29601.75,29557.75,29557.75,2679,3,0
2026-10-27T13:32:29.474Z,2026-10-27T13:32:12.992Z,29557.75,29582.0,29557.75,29582.0,842,3,0
2026-10-27T13:32:34.708Z,2026-10-27T13:32:29.474Z,29582.0,29582.0,29563.75,29563.75,288,3,0
2026-10-27T13:32:59.142Z,2026-10-27T13:32:34.708Z,29563.75,29591.0,29563.75,29591.0,1047,3,0
2026-10-27T13:33:13.000Z,2026-10-27T13:32:59.142Z,29591.0,29591.0,29570.5,29570.5,644,3,0
2026-10-27T13:35:05.636Z,2026-10-27T13:33:13.000Z,29570.5,29630.5,29570.5,29630.5,5603,3,0
2026-10-27T13:36:10.284Z,2026-10-27T13:35:05.636Z,29630.5,29630.5,29581.25,29581.25,3723,3,0
2026-10-27T13:37:01.977Z,2026-10-27T13:36:10.284Z,29581.25,29617.5,29581.25,29617.5,2022,3,0
2026-10-27T13:37:23.685Z,2026-10-27T13:37:01.977Z,29617.5,29617.5,29599.5,29599.5,907,3,0
2026-10-27T13:37:38.343Z,2026-10-27T13:37:23.685Z,29599.5,29640.0,29599.5,29640.0,922,3,0
2026-10-27T13:37:49.665Z,2026-10-27T13:37:38.343Z,29640.0,29640.0,29622.5,29622.5,441,3,0
2026-10-27T13:38:30.694Z,2026-10-27T13:37:49.665Z,29622.5,29659.5,29622.5,29659.5,2181,3,0
2026-10-27T13:38:45.058Z,2026-10-27T13:38:30.694Z,29659.5,29659.5,29642.0,29642.0,454,3,0
2026-10-27T13:40:51.726Z,2026-10-27T13:38:45.058Z,29642.0,29680.25,29642.0,29680.25,4867,3,0
2026-10-27T13:41:05.706Z,2026-10-27T13:40:51.726Z,29680.25,29680.25,29663.0,29663.0,406,3,0
2026-10-27T13:41:17.388Z,2026-10-27T13:41:05.706Z,29663.0,29681.25,29663.0,29681.25,391,3,0
2026-10-27T13:41:37.034Z,2026-10-27T13:41:17.388Z,29681.25,29681.25,29661.0,29661.0,641,3,0
2026-10-27T13:41:55.133Z,2026-10-27T13:41:37.034Z,29661.0,29687.75,29661.0,29687.75,840,3,0
2026-10-27T13:42:20.639Z,2026-10-27T13:41:55.133Z,29687.75,29687.75,29657.75,29657.75,939,3,0
2026-10-27T13:43:10.653Z,2026-10-27T13:42:20.639Z,29657.75,29676.25,29657.75,29676.25,1287,3,0
2026-10-27T13:43:39.585Z,2026-10-27T13:43:10.653Z,29676.25,29676.25,29628.75,29628.75,1675,3,0
2026-10-27T13:43:59.521Z,2026-10-27T13:43:39.585Z,29628.75,29651.75,29628.75,29651.75,690,3,0
2026-10-27T13:44:35.898Z,2026-10-27T13:43:59.521Z,29651.75,29651.75,29626.5,29626.5,1429,3,0
2026-10-27T13:45:44.468Z,2026-10-27T13:44:35.898Z,29626.5,29677.75,29626.5,29677.75,2983,3,0
2026-10-27T13:47:15.711Z,2026-10-27T13:45:44.468Z,29677.75,29677.75,29602.75,29602.75,4390,3,0
2026-10-27T13:48:27.552Z,2026-10-27T13:47:15.711Z,29602.75,29619.5,29602.75,29619.5,1765,3,0
2026-10-27T13:48:45.040Z,2026-10-27T13:48:27.552Z,29619.5,29619.5,29590.5,29590.5,900,3,0
2026-10-27T13:49:06.560Z,2026-10-27T13:48:45.040Z,29590.5,29620.75,29590.5,29620.75,754,3,0
2026-10-27T13:50:41.709Z,2026-10-27T13:49:06.560Z,29620.75,29620.75,29542.0,29542.0,5299,3,0
2026-10-27T13:51:12.040Z,2026-10-27T13:50:41.709Z,29542.0,29568.75,29542.0,29568.75,1371,3,0
2026-10-27T13:51:23.480Z,2026-10-27T13:51:12.040Z,29568.75,29568.75,29535.25,29535.25,711,3,0
2026-10-27T13:51:46.663Z,2026-10-27T13:51:23.480Z,29535.25,29576.5,29535.25,29576.5,1184,3,0
2026-10-27T13:53:21.107Z,2026-10-27T13:51:46.663Z,29576.5,29576.5,29525.25,29525.25,3772,3,0
2026-10-27T13:53:44.893Z,2026-10-27T13:53:21.107Z,29525.25,29550.0,29525.25,29550.0,887,3,0
2026-10-27T13:53:59.336Z,2026-10-27T13:53:44.893Z,29550.0,29550.0,29523.75,29523.75,622,3,0
2026-10-27T13:55:53.064Z,2026-10-27T13:53:59.336Z,29523.75,29565.75,29523.75,29565.75,3365,3,0
2026-10-27T13:56:37.338Z,2026-10-27T13:55:53.064Z,29565.75,29565.75,29542.75,29542.75,1259,3,0
2026-10-27T13:57:13.554Z,2026-10-27T13:56:37.338Z,29542.75,29586.75,29542.75,29586.75,1880,3,0
2026-10-27T13:57:48.969Z,2026-10-27T13:57:13.554Z,29586.75,29586.75,29549.25,29549.25,959,3,0
2026-10-27T13:59:21.930Z,2026-10-27T13:57:48.969Z,29549.25,29581.5,29549.25,29581.5,1675,3,0
2026-10-27T13:59:44.958Z,2026-10-27T13:59:21.930Z,29581.5,29581.5,29560.75,29560.75,264,3,0
2026-10-27T14:00:29.856Z,2026-10-27T13:59:44.958Z,29560.75,29578.0,29560.75,29578.0,945,3,0
2026-10-27T14:02:33.278Z,2026-10-27T14:00:29.856Z,29578.0,29578.0,29526.0,29526.0,4533,3,0
2026-10-27T14:04:40.738Z,2026-10-27T14:02:33.278Z,29526.0,29572.75,29526.0,29572.75,3299,3,0
2026-10-27T14:05:04.411Z,2026-10-27T14:04:40.738Z,29572.75,29572.75,29548.25,29548.25,612,3,0
2026-10-27T14:05:31.693Z,2026-10-27T14:05:04.411Z,29548.25,29566.25,29548.25,29566.25,593,3,0
2026-10-27T14:06:53.189Z,2026-10-27T14:05:31.693Z,29566.25,29566.25,29545.0,29545.0,1619,3,0
2026-10-27T14:07:35.676Z,2026-10-27T14:06:53.189Z,29545.0,29566.25,29545.0,29566.25,846,3,0
2026-10-27T14:07:53.609Z,2026-10-27T14:07:35.676Z,29566.25,29566.25,29546.5,29546.5,348,3,0
2026-10-27T14:08:58.213Z,2026-10-27T14:07:53.609Z,29546.5,29570.25,29546.5,29570.25,1205,3,0
2026-10-27T14:11:37.466Z,2026-10-27T14:08:58.213Z,29570.25,29570.25,29507.5,29507.5,5586,3,0
2026-10-27T14:12:51.547Z,2026-10-27T14:11:37.466Z,29507.5,29538.25,29507.5,29538.25,1875,3,0
2026-10-27T14:13:59.743Z,2026-10-27T14:12:51.547Z,29538.25,29538.25,29517.0,29517.0,1298,3,0
2026-10-27T14:15:11.802Z,2026-10-27T14:13:59.743Z,29517.0,29537.75,29517.0,29537.75,1328,3,0
2026-10-27T14:17:43.878Z,2026-10-27T14:15:11.802Z,29537.75,29537.75,29494.5,29494.5,3770,3,0
2026-10-27T14:19:42.543Z,2026-10-27T14:17:43.878Z,29494.5,29532.0,29494.5,29532.0,2458,3,0
2026-10-27T14:20:05.999Z,2026-10-27T14:19:42.543Z,29532.0,29532.0,29502.5,29502.5,848,3,0
2026-10-27T14:21:31.464Z,2026-10-27T14:20:05.999Z,29502.5,29529.0,29502.5,29529.0,1543,3,0
2026-10-27T14:22:06.117Z,2026-10-27T14:21:31.464Z,29529.0,29529.0,29502.0,29502.0,950,3,0
2026-10-27T14:23:29.245Z,2026-10-27T14:22:06.117Z,29502.0,29548.0,29502.0,29548.0,2226,3,0
2026-10-27T14:23:42.951Z,2026-10-27T14:23:29.245Z,29548.0,29548.0,29526.0,29526.0,478,3,0
2026-10-27T14:26:21.149Z,2026-10-27T14:23:42.951Z,29526.0,29577.5,29526.0,29577.5,4189,3,0
2026-10-27T14:27:14.613Z,2026-10-27T14:26:21.149Z,29577.5,29577.5,29549.0,29549.0,1316,3,0
2026-10-27T14:27:58.591Z,2026-10-27T14:27:14.613Z,29549.0,29579.25,29549.0,29579.25,1147,3,0
2026-10-27T14:28:20.926Z,2026-10-27T14:27:58.591Z,29579.25,29579.25,29559.25,29559.25,420,3,0
2026-10-27T14:28:40.492Z,2026-10-27T14:28:20.926Z,29559.25,29595.0,29559.25,29595.0,1256,3,0
2026-10-27T14:28:46.142Z,2026-10-27T14:28:40.492Z,29595.0,29595.0,29578.0,29578.0,189,3,0
2026-10-27T14:29:04.949Z,2026-10-27T14:28:46.142Z,29578.0,29600.0,29578.0,29600.0,762,3,0
2026-10-27T14:29:44.892Z,2026-10-27T14:29:04.949Z,29600.0,29600.0,29578.75,29578.75,1238,3,0
2026-10-27T14:31:49.432Z,2026-10-27T14:29:44.892Z,29578.75,29643.25,29578.75,29643.25,5345,3,0
2026-10-27T14:32:47.568Z,2026-10-27T14:31:49.432Z,29643.25,29643.25,29611.25,29611.25,1737,3,0
2026-10-27T14:34:26.810Z,2026-10-27T14:32:47.568Z,29611.25,29671.75,29611.25,29671.75,4330,3,0
2026-10-27T14:35:52.506Z,2026-10-27T14:34:26.810Z,29671.75,29671.75,29637.0,29637.0,2788,3,0
2026-10-27T14:36:34.010Z,2026-10-27T14:35:52.506Z,29637.0,29673.5,29637.0,29673.5,1825,3,0
2026-10-27T14:39:25.234Z,2026-10-27T14:36:34.010Z,29673.5,29673.5,29615.0,29615.0,4731,3,0
2026-10-27T14:40:57.283Z,2026-10-27T14:39:25.234Z,29615.0,29661.75,29615.0,29661.75,3142,3,0
2026-10-27T14:41:35.049Z,2026-10-27T14:40:57.283Z,29661.75,29661.75,29641.5,29641.5,776,3,0
2026-10-27T14:42:05.771Z,2026-10-27T14:41:35.049Z,29641.5,29661.5,29641.5,29661.5,622,3,0
2026-10-27T14:45:56.743Z,2026-10-27T14:42:05.771Z,29661.5,29661.5,29631.25,29631.25,3644,3,0
2026-10-27T14:49:10.524Z,2026-10-27T14:45:56.743Z,29631.25,29679.25,29631.25,29679.25,3597,3,0
2026-10-27T14:50:36.322Z,2026-10-27T14:49:10.524Z,29679.25,29679.25,29661.5,29661.5,1163,3,0
2026-10-27T14:51:01.861Z,2026-10-27T14:50:36.322Z,29661.5,29679.0,29661.5,29679.0,575,3,0
2026-10-27T14:53:31.562Z,2026-10-27T14:51:01.861Z,29679.0,29679.0,29661.0,29661.0,1568,3,0
2026-10-27T14:57:17.783Z,2026-10-27T14:53:31.562Z,29661.0,29716.0,29661.0,29716.0,5640,3,0
2026-10-27T14:58:43.203Z,2026-10-27T14:57:17.783Z,29716.0,29716.0,29695.5,29695.5,1514,3,0
2026-10-27T15:04:12.827Z,2026-10-27T14:58:43.203Z,29695.5,29743.0,29695.5,29743.0,7907,3,0
2026-10-27T15:11:44.675Z,2026-10-27T15:04:12.827Z,29743.0,29743.0,29711.0,29711.0,8004,3,0
2026-10-27T15:21:04.166Z,2026-10-27T15:11:44.675Z,29711.0,29767.75,29711.0,29767.75,11239,3,0
2026-10-27T15:21:35.539Z,2026-10-27T15:21:04.166Z,29767.75,29767.75,29748.5,29748.5,534,3,0
2026-10-27T15:22:53.467Z,2026-10-27T15:21:35.539Z,29748.5,29772.75,29748.5,29772.75,1175,3,0
2026-10-27T15:24:09.316Z,2026-10-27T15:22:53.467Z,29772.75,29772.75,29752.25,29752.25,973,3,0
2026-10-27T15:30:37.808Z,2026-10-27T15:24:09.316Z,29752.25,29775.5,29752.25,29775.5,5141,3,0
2026-10-27T15:36:52.640Z,2026-10-27T15:30:37.808Z,29775.5,29775.5,29739.5,29739.5,5336,3,0
2026-10-27T15:48:00.843Z,2026-10-27T15:36:52.640Z,29739.5,29820.25,29739.5,29820.25,11347,3,0
2026-10-27T15:49:44.037Z,2026-10-27T15:48:00.843Z,29820.25,29820.25,29802.25,29802.25,1247,3,0
```
SIGNALS (17 rows; signal_bar_known_utc = exact known time of the signal bar from the module; engine order time = floor(known) + 2 s; fired_level_px / fired_line = the line that fired):
```csv
signal_bar_known_utc,engine_order_time_utc,side,stop_pts,target_pts,lots,session_end_exit_utc,fired_level_px,fired_line
2026-10-27T13:31:33.301Z,2026-10-27T13:31:35.000Z,1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29600.75,PRF5__LVN1
2026-10-27T13:35:05.636Z,2026-10-27T13:35:07.000Z,1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29600.75,PRF5__LVN1
2026-10-27T13:36:10.284Z,2026-10-27T13:36:12.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29600.75,PRF5__LVN1
2026-10-27T13:37:01.977Z,2026-10-27T13:37:03.000Z,1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29600.75,PRF5__LVN1
2026-10-27T13:37:23.685Z,2026-10-27T13:37:25.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29600.75,PRF5__LVN1
2026-10-27T13:37:38.343Z,2026-10-27T13:37:40.000Z,1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29632.75,PRF5__LVN2
2026-10-27T13:43:39.585Z,2026-10-27T13:43:41.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29632.75,PRF5__LVN2
2026-10-27T13:44:35.898Z,2026-10-27T13:44:37.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29632.75,PRF5__LVN2
2026-10-27T13:47:15.711Z,2026-10-27T13:47:17.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29632.75,PRF5__LVN2
2026-10-27T13:48:45.040Z,2026-10-27T13:48:47.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29600.75,PRF5__LVN1
2026-10-27T13:50:41.709Z,2026-10-27T13:50:43.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29600.75,PRF5__LVN1
2026-10-27T14:17:43.878Z,2026-10-27T14:17:45.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29496.5,PRF1__HVN1
2026-10-27T14:31:49.432Z,2026-10-27T14:31:51.000Z,1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29600.75,PRF5__LVN1
2026-10-27T14:34:26.810Z,2026-10-27T14:34:28.000Z,1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29632.75,PRF5__LVN2
2026-10-27T14:39:25.234Z,2026-10-27T14:39:27.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29632.75,PRF5__LVN2
2026-10-27T14:40:57.283Z,2026-10-27T14:40:59.000Z,1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29632.75,PRF5__LVN2
2026-10-27T14:45:56.743Z,2026-10-27T14:45:58.000Z,-1,90.0,30.0,1,2026-10-27T16:00:00.000Z,29632.75,PRF5__LVN2
```
INPUTS (per bar: decision time T0, close, u, k x u, the ten lines at T0; units points):
```csv
known_utc,T0_decision_utc_s,close,u_native_pts,k_times_u,PRF1__HVN1,PRF1__HVN2,PRF1__LVN1,PRF1__LVN2,PRF1__SPH,PRF1__SPL,PRF5__HVN1,PRF5__HVN2,PRF5__LVN1,PRF5__LVN2
2026-10-27T13:30:30.146Z,2026-10-27T13:28:05.000Z,29589.5,31.75,15.875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:30:55.718Z,2026-10-27T13:30:30.000Z,29541.25,31.625,15.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:31:33.301Z,2026-10-27T13:30:55.000Z,29601.75,31.75,15.875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:32:12.992Z,2026-10-27T13:31:33.000Z,29557.75,31.875,15.9375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:32:29.474Z,2026-10-27T13:32:12.000Z,29582.0,32.25,16.125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:32:34.708Z,2026-10-27T13:32:29.000Z,29563.75,32.25,16.125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:32:59.142Z,2026-10-27T13:32:34.000Z,29591.0,31.875,15.9375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:33:13.000Z,2026-10-27T13:32:59.000Z,29570.5,31.75,15.875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:35:05.636Z,2026-10-27T13:33:13.000Z,29630.5,31.625,15.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:36:10.284Z,2026-10-27T13:35:05.000Z,29581.25,31.625,15.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:37:01.977Z,2026-10-27T13:36:10.000Z,29617.5,31.75,15.875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:37:23.685Z,2026-10-27T13:37:01.000Z,29599.5,31.875,15.9375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:37:38.343Z,2026-10-27T13:37:23.000Z,29640.0,31.875,15.9375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:37:49.665Z,2026-10-27T13:37:38.000Z,29622.5,32.25,16.125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:38:30.694Z,2026-10-27T13:37:49.000Z,29659.5,31.875,15.9375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:38:45.058Z,2026-10-27T13:38:30.000Z,29642.0,31.875,15.9375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:40:51.726Z,2026-10-27T13:38:45.000Z,29680.25,31.75,15.875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:41:05.706Z,2026-10-27T13:40:51.000Z,29663.0,31.875,15.9375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:41:17.388Z,2026-10-27T13:41:05.000Z,29681.25,31.75,15.875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:41:37.034Z,2026-10-27T13:41:17.000Z,29661.0,31.75,15.875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:41:55.133Z,2026-10-27T13:41:37.000Z,29687.75,31.625,15.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:42:20.639Z,2026-10-27T13:41:55.000Z,29657.75,31.25,15.625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:43:10.653Z,2026-10-27T13:42:20.000Z,29676.25,31.25,15.625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:43:39.585Z,2026-10-27T13:43:10.000Z,29628.75,30.625,15.3125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:43:59.521Z,2026-10-27T13:43:39.000Z,29651.75,31.25,15.625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:44:35.898Z,2026-10-27T13:43:59.000Z,29626.5,31.25,15.625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:45:44.468Z,2026-10-27T13:44:35.000Z,29677.75,30.625,15.3125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:47:15.711Z,2026-10-27T13:45:44.000Z,29602.75,30.625,15.3125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:48:27.552Z,2026-10-27T13:47:15.000Z,29619.5,30.625,15.3125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:48:45.040Z,2026-10-27T13:48:27.000Z,29590.5,30.125,15.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:49:06.560Z,2026-10-27T13:48:45.000Z,29620.75,30.125,15.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:50:41.709Z,2026-10-27T13:49:06.000Z,29542.0,30.125,15.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:51:12.040Z,2026-10-27T13:50:41.000Z,29568.75,30.125,15.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:51:23.480Z,2026-10-27T13:51:12.000Z,29535.25,30.125,15.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:51:46.663Z,2026-10-27T13:51:23.000Z,29576.5,30.125,15.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:53:21.107Z,2026-10-27T13:51:46.000Z,29525.25,30.125,15.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:53:44.893Z,2026-10-27T13:53:21.000Z,29550.0,30.125,15.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:53:59.336Z,2026-10-27T13:53:44.000Z,29523.75,29.5,14.75,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:55:53.064Z,2026-10-27T13:53:59.000Z,29565.75,29.5,14.75,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:56:37.338Z,2026-10-27T13:55:53.000Z,29542.75,29.5,14.75,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:57:13.554Z,2026-10-27T13:56:37.000Z,29586.75,29.5,14.75,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:57:48.969Z,2026-10-27T13:57:13.000Z,29549.25,29.5,14.75,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:59:21.930Z,2026-10-27T13:57:48.000Z,29581.5,29.5,14.75,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T13:59:44.958Z,2026-10-27T13:59:21.000Z,29560.75,29.5,14.75,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:00:29.856Z,2026-10-27T13:59:44.000Z,29578.0,28.625,14.3125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:02:33.278Z,2026-10-27T14:00:29.000Z,29526.0,28.625,14.3125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:04:40.738Z,2026-10-27T14:02:33.000Z,29572.75,28.625,14.3125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:05:04.411Z,2026-10-27T14:04:40.000Z,29548.25,28.625,14.3125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:05:31.693Z,2026-10-27T14:05:04.000Z,29566.25,28.25,14.125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:06:53.189Z,2026-10-27T14:05:31.000Z,29545.0,28.125,14.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:07:35.676Z,2026-10-27T14:06:53.000Z,29566.25,27.625,13.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:07:53.609Z,2026-10-27T14:07:35.000Z,29546.5,27.0,13.5,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:08:58.213Z,2026-10-27T14:07:53.000Z,29570.25,27.0,13.5,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:11:37.466Z,2026-10-27T14:08:58.000Z,29507.5,26.75,13.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:12:51.547Z,2026-10-27T14:11:37.000Z,29538.25,27.0,13.5,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:13:59.743Z,2026-10-27T14:12:51.000Z,29517.0,27.0,13.5,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:15:11.802Z,2026-10-27T14:13:59.000Z,29537.75,27.0,13.5,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:17:43.878Z,2026-10-27T14:15:11.000Z,29494.5,27.0,13.5,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:19:42.543Z,2026-10-27T14:17:43.000Z,29532.0,27.625,13.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:20:05.999Z,2026-10-27T14:19:42.000Z,29502.5,27.625,13.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:21:31.464Z,2026-10-27T14:20:05.000Z,29529.0,27.625,13.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:22:06.117Z,2026-10-27T14:21:31.000Z,29502.0,27.0,13.5,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:23:29.245Z,2026-10-27T14:22:06.000Z,29548.0,26.875,13.4375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:23:42.951Z,2026-10-27T14:23:29.000Z,29526.0,26.875,13.4375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:26:21.149Z,2026-10-27T14:23:42.000Z,29577.5,26.75,13.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:27:14.613Z,2026-10-27T14:26:21.000Z,29549.0,26.75,13.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:27:58.591Z,2026-10-27T14:27:14.000Z,29579.25,26.875,13.4375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:28:20.926Z,2026-10-27T14:27:58.000Z,29559.25,27.125,13.5625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:28:40.492Z,2026-10-27T14:28:20.000Z,29595.0,26.875,13.4375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:28:46.142Z,2026-10-27T14:28:40.000Z,29578.0,27.125,13.5625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:29:04.949Z,2026-10-27T14:28:46.000Z,29600.0,26.875,13.4375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:29:44.892Z,2026-10-27T14:29:04.000Z,29578.75,26.875,13.4375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:31:49.432Z,2026-10-27T14:29:44.000Z,29643.25,26.75,13.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:32:47.568Z,2026-10-27T14:31:49.000Z,29611.25,26.875,13.4375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:34:26.810Z,2026-10-27T14:32:47.000Z,29671.75,27.125,13.5625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:35:52.506Z,2026-10-27T14:34:26.000Z,29637.0,27.625,13.8125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:36:34.010Z,2026-10-27T14:35:52.000Z,29673.5,28.125,14.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:39:25.234Z,2026-10-27T14:36:34.000Z,29615.0,28.125,14.0625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:40:57.283Z,2026-10-27T14:39:25.000Z,29661.75,28.25,14.125,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:41:35.049Z,2026-10-27T14:40:57.000Z,29641.5,28.375,14.1875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:42:05.771Z,2026-10-27T14:41:35.000Z,29661.5,28.375,14.1875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:45:56.743Z,2026-10-27T14:42:05.000Z,29631.25,28.375,14.1875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:49:10.524Z,2026-10-27T14:45:56.000Z,29679.25,28.75,14.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:50:36.322Z,2026-10-27T14:49:10.000Z,29661.5,28.75,14.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:51:01.861Z,2026-10-27T14:50:36.000Z,29679.0,28.75,14.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:53:31.562Z,2026-10-27T14:51:01.000Z,29661.0,28.375,14.1875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:57:17.783Z,2026-10-27T14:53:31.000Z,29716.0,28.375,14.1875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T14:58:43.203Z,2026-10-27T14:57:17.000Z,29695.5,28.75,14.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:04:12.827Z,2026-10-27T14:58:43.000Z,29743.0,28.375,14.1875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:11:44.675Z,2026-10-27T15:04:12.000Z,29711.0,28.75,14.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:21:04.166Z,2026-10-27T15:11:44.000Z,29767.75,29.25,14.625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:21:35.539Z,2026-10-27T15:21:04.000Z,29748.5,29.75,14.875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:22:53.467Z,2026-10-27T15:21:35.000Z,29772.75,29.25,14.625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:24:09.316Z,2026-10-27T15:22:53.000Z,29752.25,29.25,14.625,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:30:37.808Z,2026-10-27T15:24:09.000Z,29775.5,28.75,14.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:36:52.640Z,2026-10-27T15:30:37.000Z,29739.5,28.375,14.1875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:48:00.843Z,2026-10-27T15:36:52.000Z,29820.25,28.375,14.1875,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
2026-10-27T15:49:44.037Z,2026-10-27T15:48:00.000Z,29802.25,28.75,14.375,29496.5,29471.75,29384.25,29357.5,29396.75,29383.25,29266.75,29137,29600.75,29632.75
```
TRADES (engine month 202610 landed; bare run, 1 lot, the one-position rule applied):
```csv
entry_utc,entry_price,exit_utc,exit_price,exit_reason,side,lots,points,gross_usd,fee_engine_usd,fee_standard_usd_4.84_per_lot
2026-10-27T13:31:36.000Z,29588.0,2026-10-27T13:34:26.414Z,29618.0,Target,1,1,30,600,1.18,4.84
2026-10-27T13:35:08.000Z,29610.0,2026-10-27T13:37:36.344Z,29640.0,Target,1,1,30,600,1.18,4.84
2026-10-27T13:37:41.000Z,29632.0,2026-10-27T13:38:47.025Z,29662.0,Target,1,1,30,600,1.18,4.84
2026-10-27T13:43:42.000Z,29643.5,2026-10-27T13:46:37.567Z,29613.5,Target,-1,1,30,600,1.18,4.84
2026-10-27T13:47:18.000Z,29615.5,2026-10-27T13:49:24.584Z,29585.5,Target,-1,1,30,600,1.18,4.84
2026-10-27T13:50:44.000Z,29560.25,2026-10-27T13:53:00.981Z,29530.25,Target,-1,1,30,600,1.18,4.84
2026-10-27T14:17:46.000Z,29511.5,2026-10-27T14:29:51.514Z,29599.5,Stop,-1,1,-88,-1760,1.18,4.84
2026-10-27T14:31:52.000Z,29628.5,2026-10-27T14:33:48.090Z,29658.5,Target,1,1,30,600,1.18,4.84
2026-10-27T14:34:29.000Z,29660.5,2026-10-27T14:54:14.255Z,29690.5,Target,1,1,30,600,1.18,4.84
```

## 7. CSV blocks, td 20261110 (EST: NY AM 14:30-17:00Z)
BARS (184 rows):
```csv
known_utc,first_print_or_bucket_start_utc,open,high,low,close,volume,session_code,part
2026-11-10T14:30:03.614Z,2026-11-10T14:30:00.000Z,27742.5,27785.0,27742.5,27785.0,1189,3,0
2026-11-10T14:30:37.740Z,2026-11-10T14:30:03.614Z,27785.0,27785.0,27705.75,27705.75,3067,3,0
2026-11-10T14:30:42.152Z,2026-11-10T14:30:37.740Z,27705.75,27731.25,27705.75,27731.25,360,3,0
2026-11-10T14:30:59.018Z,2026-11-10T14:30:42.152Z,27731.25,27731.25,27670.75,27670.75,1650,3,0
2026-11-10T14:31:22.732Z,2026-11-10T14:30:59.018Z,27670.75,27698.25,27670.75,27698.25,1554,3,0
2026-11-10T14:31:30.593Z,2026-11-10T14:31:22.732Z,27698.25,27698.25,27668.25,27668.25,615,3,0
2026-11-10T14:32:01.915Z,2026-11-10T14:31:30.593Z,27668.25,27701.25,27668.25,27701.25,1597,3,0
2026-11-10T14:32:33.917Z,2026-11-10T14:32:01.915Z,27701.25,27701.25,27637.25,27637.25,2308,3,0
2026-11-10T14:32:51.343Z,2026-11-10T14:32:33.917Z,27637.25,27707.25,27637.25,27707.25,1382,3,0
2026-11-10T14:33:10.682Z,2026-11-10T14:32:51.343Z,27707.25,27707.25,27658.0,27658.0,1010,3,0
2026-11-10T14:33:32.228Z,2026-11-10T14:33:10.682Z,27658.0,27691.75,27658.0,27691.75,1057,3,0
2026-11-10T14:33:36.735Z,2026-11-10T14:33:32.228Z,27691.75,27691.75,27666.75,27666.75,252,3,0
2026-11-10T14:33:46.157Z,2026-11-10T14:33:36.735Z,27666.75,27698.0,27666.75,27698.0,400,3,0
2026-11-10T14:33:51.775Z,2026-11-10T14:33:46.157Z,27698.0,27698.0,27669.5,27669.5,293,3,0
2026-11-10T14:34:32.688Z,2026-11-10T14:33:51.775Z,27669.5,27765.25,27669.5,27765.25,2481,3,0
2026-11-10T14:34:38.512Z,2026-11-10T14:34:32.688Z,27765.25,27765.25,27732.25,27732.25,386,3,0
2026-11-10T14:35:01.540Z,2026-11-10T14:34:38.512Z,27732.25,27784.75,27732.25,27784.75,1512,3,0
2026-11-10T14:35:06.741Z,2026-11-10T14:35:01.540Z,27784.75,27784.75,27742.5,27742.5,490,3,0
2026-11-10T14:35:20.072Z,2026-11-10T14:35:06.741Z,27742.5,27772.25,27742.5,27772.25,810,3,0
2026-11-10T14:35:29.319Z,2026-11-10T14:35:20.072Z,27772.25,27772.25,27735.75,27735.75,654,3,0
2026-11-10T14:35:36.100Z,2026-11-10T14:35:29.319Z,27735.75,27762.0,27735.75,27762.0,352,3,0
2026-11-10T14:35:41.871Z,2026-11-10T14:35:36.100Z,27762.0,27762.0,27733.25,27733.25,292,3,0
2026-11-10T14:36:05.272Z,2026-11-10T14:35:41.871Z,27733.25,27801.0,27733.25,27801.0,2069,3,0
2026-11-10T14:36:14.390Z,2026-11-10T14:36:05.272Z,27801.0,27801.0,27765.5,27765.5,744,3,0
2026-11-10T14:37:07.619Z,2026-11-10T14:36:14.390Z,27765.5,27822.5,27765.5,27822.5,3492,3,0
2026-11-10T14:37:18.783Z,2026-11-10T14:37:07.619Z,27822.5,27822.5,27770.0,27770.0,1099,3,0
2026-11-10T14:37:55.174Z,2026-11-10T14:37:18.783Z,27770.0,27817.0,27770.0,27817.0,1631,3,0
2026-11-10T14:38:39.454Z,2026-11-10T14:37:55.174Z,27817.0,27817.0,27752.0,27752.0,2505,3,0
2026-11-10T14:38:41.828Z,2026-11-10T14:38:39.454Z,27752.0,27777.0,27752.0,27777.0,95,3,0
2026-11-10T14:39:03.920Z,2026-11-10T14:38:41.828Z,27777.0,27777.0,27743.25,27743.25,1048,3,0
2026-11-10T14:39:29.353Z,2026-11-10T14:39:03.920Z,27743.25,27808.5,27743.25,27808.5,1419,3,0
2026-11-10T14:39:41.812Z,2026-11-10T14:39:29.353Z,27808.5,27808.5,27772.0,27772.0,513,3,0
2026-11-10T14:40:17.553Z,2026-11-10T14:39:41.812Z,27772.0,27830.75,27772.0,27830.75,1893,3,0
2026-11-10T14:40:22.961Z,2026-11-10T14:40:17.553Z,27830.75,27830.75,27794.25,27794.25,362,3,0
2026-11-10T14:40:41.878Z,2026-11-10T14:40:22.961Z,27794.25,27818.0,27794.25,27818.0,675,3,0
2026-11-10T14:40:57.168Z,2026-11-10T14:40:41.878Z,27818.0,27818.0,27775.0,27775.0,988,3,0
2026-11-10T14:41:09.709Z,2026-11-10T14:40:57.168Z,27775.0,27801.5,27775.0,27801.5,441,3,0
2026-11-10T14:41:23.507Z,2026-11-10T14:41:09.709Z,27801.5,27801.5,27771.75,27771.75,562,3,0
2026-11-10T14:41:34.349Z,2026-11-10T14:41:23.507Z,27771.75,27812.0,27771.75,27812.0,427,3,0
2026-11-10T14:42:09.987Z,2026-11-10T14:41:34.349Z,27812.0,27812.0,27757.0,27757.0,1233,3,0
2026-11-10T14:42:27.463Z,2026-11-10T14:42:09.987Z,27757.0,27787.75,27757.0,27787.75,572,3,0
2026-11-10T14:42:54.155Z,2026-11-10T14:42:27.463Z,27787.75,27787.75,27747.0,27747.0,1234,3,0
2026-11-10T14:43:55.550Z,2026-11-10T14:42:54.155Z,27747.0,27844.25,27747.0,27844.25,3124,3,0
2026-11-10T14:44:22.203Z,2026-11-10T14:43:55.550Z,27844.25,27844.25,27812.25,27812.25,1082,3,0
2026-11-10T14:45:01.599Z,2026-11-10T14:44:22.203Z,27812.25,27863.5,27812.25,27863.5,2097,3,0
2026-11-10T14:45:12.728Z,2026-11-10T14:45:01.599Z,27863.5,27863.5,27823.75,27823.75,861,3,0
2026-11-10T14:45:22.337Z,2026-11-10T14:45:12.728Z,27823.75,27859.0,27823.75,27859.0,722,3,0
2026-11-10T14:45:34.677Z,2026-11-10T14:45:22.337Z,27859.0,27859.0,27808.75,27808.75,936,3,0
2026-11-10T14:45:56.209Z,2026-11-10T14:45:34.677Z,27808.75,27837.75,27808.75,27837.75,1055,3,0
2026-11-10T14:46:31.250Z,2026-11-10T14:45:56.209Z,27837.75,27837.75,27803.25,27803.25,1527,3,0
2026-11-10T14:46:38.630Z,2026-11-10T14:46:31.250Z,27803.25,27828.0,27803.25,27828.0,369,3,0
2026-11-10T14:47:01.103Z,2026-11-10T14:46:38.630Z,27828.0,27828.0,27786.25,27786.25,1064,3,0
2026-11-10T14:47:14.286Z,2026-11-10T14:47:01.103Z,27786.25,27815.75,27786.25,27815.75,490,3,0
2026-11-10T14:47:29.724Z,2026-11-10T14:47:14.286Z,27815.75,27815.75,27760.5,27760.5,754,3,0
2026-11-10T14:48:33.328Z,2026-11-10T14:47:29.724Z,27760.5,27804.5,27760.5,27804.5,2314,3,0
2026-11-10T14:49:02.944Z,2026-11-10T14:48:33.328Z,27804.5,27804.5,27754.5,27754.5,1191,3,0
2026-11-10T14:49:24.833Z,2026-11-10T14:49:02.944Z,27754.5,27790.5,27754.5,27790.5,887,3,0
2026-11-10T14:49:37.129Z,2026-11-10T14:49:24.833Z,27790.5,27790.5,27758.0,27758.0,523,3,0
2026-11-10T14:50:16.141Z,2026-11-10T14:49:37.129Z,27758.0,27833.25,27758.0,27833.25,2119,3,0
2026-11-10T14:50:46.315Z,2026-11-10T14:50:16.141Z,27833.25,27833.25,27784.0,27784.0,1365,3,0
2026-11-10T14:51:59.513Z,2026-11-10T14:50:46.315Z,27784.0,27850.5,27784.0,27850.5,2805,3,0
2026-11-10T14:52:58.260Z,2026-11-10T14:51:59.513Z,27850.5,27850.5,27796.0,27796.0,2117,3,0
2026-11-10T14:53:37.254Z,2026-11-10T14:52:58.260Z,27796.0,27853.25,27796.0,27853.25,1802,3,0
2026-11-10T14:54:04.852Z,2026-11-10T14:53:37.254Z,27853.25,27853.25,27830.0,27830.0,860,3,0
2026-11-10T14:54:11.734Z,2026-11-10T14:54:04.852Z,27830.0,27881.75,27830.0,27881.75,744,3,0
2026-11-10T14:54:29.564Z,2026-11-10T14:54:11.734Z,27881.75,27881.75,27838.25,27838.25,1057,3,0
2026-11-10T14:55:45.566Z,2026-11-10T14:54:29.564Z,27838.25,27947.75,27838.25,27947.75,4629,3,0
2026-11-10T14:56:02.963Z,2026-11-10T14:55:45.566Z,27947.75,27947.75,27910.5,27910.5,832,3,0
2026-11-10T14:57:33.487Z,2026-11-10T14:56:02.963Z,27910.5,27971.75,27910.5,27971.75,4647,3,0
2026-11-10T14:58:13.431Z,2026-11-10T14:57:33.487Z,27971.75,27971.75,27945.5,27945.5,1797,3,0
2026-11-10T14:59:44.342Z,2026-11-10T14:58:13.431Z,27945.5,28016.75,27945.5,28016.75,4962,3,0
2026-11-10T14:59:58.610Z,2026-11-10T14:59:44.342Z,28016.75,28016.75,27989.0,27989.0,628,3,0
2026-11-10T15:00:20.884Z,2026-11-10T14:59:58.610Z,27989.0,28030.0,27989.0,28030.0,1440,3,0
2026-11-10T15:00:30.986Z,2026-11-10T15:00:20.884Z,28030.0,28030.0,28006.25,28006.25,539,3,0
2026-11-10T15:02:03.785Z,2026-11-10T15:00:30.986Z,28006.25,28090.0,28006.25,28090.0,7020,3,0
2026-11-10T15:02:34.869Z,2026-11-10T15:02:03.785Z,28090.0,28090.0,28025.75,28025.75,2453,3,0
2026-11-10T15:03:03.043Z,2026-11-10T15:02:34.869Z,28025.75,28055.5,28025.75,28055.5,1262,3,0
2026-11-10T15:03:38.381Z,2026-11-10T15:03:03.043Z,28055.5,28055.5,27993.0,27993.0,2139,3,0
2026-11-10T15:04:53.459Z,2026-11-10T15:03:38.381Z,27993.0,28062.0,27993.0,28062.0,3499,3,0
2026-11-10T15:05:13.984Z,2026-11-10T15:04:53.459Z,28062.0,28062.0,28035.75,28035.75,838,3,0
2026-11-10T15:05:46.850Z,2026-11-10T15:05:13.984Z,28035.75,28080.0,28035.75,28080.0,1933,3,0
2026-11-10T15:07:06.313Z,2026-11-10T15:05:46.850Z,28080.0,28080.0,28013.5,28013.5,4011,3,0
2026-11-10T15:07:28.279Z,2026-11-10T15:07:06.313Z,28013.5,28037.0,28013.5,28037.0,765,3,0
2026-11-10T15:07:36.518Z,2026-11-10T15:07:28.279Z,28037.0,28037.0,28008.25,28008.25,374,3,0
2026-11-10T15:08:12.032Z,2026-11-10T15:07:36.518Z,28008.25,28068.75,28008.25,28068.75,1669,3,0
2026-11-10T15:09:31.793Z,2026-11-10T15:08:12.032Z,28068.75,28068.75,28005.5,28005.5,2415,3,0
2026-11-10T15:10:18.273Z,2026-11-10T15:09:31.793Z,28005.5,28058.0,28005.5,28058.0,1486,3,0
2026-11-10T15:11:31.713Z,2026-11-10T15:10:18.273Z,28058.0,28058.0,28016.5,28016.5,2076,3,0
2026-11-10T15:11:38.865Z,2026-11-10T15:11:31.713Z,28016.5,28041.0,28016.5,28041.0,248,3,0
2026-11-10T15:13:05.309Z,2026-11-10T15:11:38.865Z,28041.0,28041.0,27994.0,27994.0,2905,3,0
2026-11-10T15:13:39.492Z,2026-11-10T15:13:05.309Z,27994.0,28035.25,27994.0,28035.25,1092,3,0
2026-11-10T15:16:44.628Z,2026-11-10T15:13:39.492Z,28035.25,28035.25,27949.0,27949.0,6690,3,0
2026-11-10T15:17:21.553Z,2026-11-10T15:16:44.628Z,27949.0,28002.0,27949.0,28002.0,1471,3,0
2026-11-10T15:18:56.404Z,2026-11-10T15:17:21.553Z,28002.0,28002.0,27944.0,27944.0,2973,3,0
2026-11-10T15:19:37.658Z,2026-11-10T15:18:56.404Z,27944.0,27985.75,27944.0,27985.75,1231,3,0
2026-11-10T15:20:34.153Z,2026-11-10T15:19:37.658Z,27985.75,27985.75,27949.0,27949.0,1353,3,0
2026-11-10T15:21:57.450Z,2026-11-10T15:20:34.153Z,27949.0,28002.0,27949.0,28002.0,2333,3,0
2026-11-10T15:22:51.117Z,2026-11-10T15:21:57.450Z,28002.0,28002.0,27961.0,27961.0,1314,3,0
2026-11-10T15:23:09.552Z,2026-11-10T15:22:51.117Z,27961.0,27993.75,27961.0,27993.75,417,3,0
2026-11-10T15:23:28.188Z,2026-11-10T15:23:09.552Z,27993.75,27993.75,27941.0,27941.0,764,3,0
2026-11-10T15:23:43.368Z,2026-11-10T15:23:28.188Z,27941.0,27964.25,27941.0,27964.25,342,3,0
2026-11-10T15:24:43.661Z,2026-11-10T15:23:43.368Z,27964.25,27964.25,27893.25,27893.25,3548,3,0
2026-11-10T15:25:00.671Z,2026-11-10T15:24:43.661Z,27893.25,27919.0,27893.25,27919.0,603,3,0
2026-11-10T15:25:18.673Z,2026-11-10T15:25:00.671Z,27919.0,27919.0,27890.0,27890.0,764,3,0
2026-11-10T15:25:58.679Z,2026-11-10T15:25:18.673Z,27890.0,27964.5,27890.0,27964.5,1383,3,0
2026-11-10T15:27:25.764Z,2026-11-10T15:25:58.679Z,27964.5,27964.5,27920.5,27920.5,2281,3,0
2026-11-10T15:27:33.580Z,2026-11-10T15:27:25.764Z,27920.5,27951.75,27920.5,27951.75,285,3,0
2026-11-10T15:28:42.682Z,2026-11-10T15:27:33.580Z,27951.75,27951.75,27884.5,27884.5,1953,3,0
2026-11-10T15:29:22.019Z,2026-11-10T15:28:42.682Z,27884.5,27914.75,27884.5,27914.75,670,3,0
2026-11-10T15:29:53.620Z,2026-11-10T15:29:22.019Z,27914.75,27914.75,27878.0,27878.0,826,3,0
2026-11-10T15:30:16.545Z,2026-11-10T15:29:53.620Z,27878.0,27933.25,27878.0,27933.25,1036,3,0
2026-11-10T15:30:44.023Z,2026-11-10T15:30:16.545Z,27933.25,27933.25,27904.25,27904.25,847,3,0
2026-11-10T15:31:01.110Z,2026-11-10T15:30:44.023Z,27904.25,27928.0,27904.25,27928.0,402,3,0
2026-11-10T15:31:29.807Z,2026-11-10T15:31:01.110Z,27928.0,27928.0,27904.25,27904.25,722,3,0
2026-11-10T15:33:04.758Z,2026-11-10T15:31:29.807Z,27904.25,27978.5,27904.25,27978.5,3354,3,0
2026-11-10T15:34:01.198Z,2026-11-10T15:33:04.758Z,27978.5,27978.5,27934.25,27934.25,1523,3,0
2026-11-10T15:34:29.987Z,2026-11-10T15:34:01.198Z,27934.25,27960.25,27934.25,27960.25,524,3,0
2026-11-10T15:34:47.390Z,2026-11-10T15:34:29.987Z,27960.25,27960.25,27922.75,27922.75,574,3,0
2026-11-10T15:35:11.709Z,2026-11-10T15:34:47.390Z,27922.75,27956.25,27922.75,27956.25,527,3,0
2026-11-10T15:35:33.618Z,2026-11-10T15:35:11.709Z,27956.25,27956.25,27917.5,27917.5,565,3,0
2026-11-10T15:35:42.500Z,2026-11-10T15:35:33.618Z,27917.5,27940.75,27917.5,27940.75,201,3,0
2026-11-10T15:38:39.786Z,2026-11-10T15:35:42.500Z,27940.75,27940.75,27857.0,27857.0,4895,3,0
2026-11-10T15:39:30.848Z,2026-11-10T15:38:39.786Z,27857.0,27901.5,27857.0,27901.5,1203,3,0
2026-11-10T15:41:08.520Z,2026-11-10T15:39:30.848Z,27901.5,27901.5,27857.25,27857.25,2297,3,0
2026-11-10T15:41:22.527Z,2026-11-10T15:41:08.520Z,27857.25,27884.0,27857.25,27884.0,320,3,0
2026-11-10T15:42:00.139Z,2026-11-10T15:41:22.527Z,27884.0,27884.0,27836.0,27836.0,1612,3,0
2026-11-10T15:42:50.771Z,2026-11-10T15:42:00.139Z,27836.0,27864.5,27836.0,27864.5,1118,3,0
2026-11-10T15:43:02.137Z,2026-11-10T15:42:50.771Z,27864.5,27864.5,27832.0,27832.0,559,3,0
2026-11-10T15:43:13.525Z,2026-11-10T15:43:02.137Z,27832.0,27857.75,27832.0,27857.75,447,3,0
2026-11-10T15:43:29.058Z,2026-11-10T15:43:13.525Z,27857.75,27857.75,27827.5,27827.5,608,3,0
2026-11-10T15:44:04.567Z,2026-11-10T15:43:29.058Z,27827.5,27851.0,27827.5,27851.0,893,3,0
2026-11-10T15:45:51.173Z,2026-11-10T15:44:04.567Z,27851.0,27851.0,27786.75,27786.75,3746,3,0
2026-11-10T15:46:37.655Z,2026-11-10T15:45:51.173Z,27786.75,27829.25,27786.75,27829.25,1461,3,0
2026-11-10T15:48:05.128Z,2026-11-10T15:46:37.655Z,27829.25,27829.25,27760.0,27760.0,3360,3,0
2026-11-10T15:49:32.311Z,2026-11-10T15:48:05.128Z,27760.0,27796.5,27760.0,27796.5,2030,3,0
2026-11-10T15:50:24.728Z,2026-11-10T15:49:32.311Z,27796.5,27796.5,27707.0,27707.0,3494,3,0
2026-11-10T15:51:03.686Z,2026-11-10T15:50:24.728Z,27707.0,27773.75,27707.0,27773.75,1608,3,0
2026-11-10T15:52:04.823Z,2026-11-10T15:51:03.686Z,27773.75,27773.75,27711.0,27711.0,2352,3,0
2026-11-10T15:53:09.372Z,2026-11-10T15:52:04.823Z,27711.0,27757.75,27711.0,27757.75,1825,3,0
2026-11-10T15:54:00.023Z,2026-11-10T15:53:09.372Z,27757.75,27757.75,27715.75,27715.75,944,3,0
2026-11-10T15:54:29.777Z,2026-11-10T15:54:00.023Z,27715.75,27754.5,27715.75,27754.5,760,3,0
2026-11-10T15:54:52.704Z,2026-11-10T15:54:29.777Z,27754.5,27754.5,27730.75,27730.75,391,3,0
2026-11-10T15:55:37.030Z,2026-11-10T15:54:52.704Z,27730.75,27756.5,27730.75,27756.5,1044,3,0
2026-11-10T15:55:52.352Z,2026-11-10T15:55:37.030Z,27756.5,27756.5,27709.75,27709.75,618,3,0
2026-11-10T15:56:02.720Z,2026-11-10T15:55:52.352Z,27709.75,27735.0,27709.75,27735.0,227,3,0
2026-11-10T15:56:23.806Z,2026-11-10T15:56:02.720Z,27735.0,27735.0,27699.25,27699.25,820,3,0
2026-11-10T15:56:43.443Z,2026-11-10T15:56:23.806Z,27699.25,27739.75,27699.25,27739.75,500,3,0
2026-11-10T15:56:50.187Z,2026-11-10T15:56:43.443Z,27739.75,27739.75,27715.75,27715.75,213,3,0
2026-11-10T15:58:00.693Z,2026-11-10T15:56:50.187Z,27715.75,27783.0,27715.75,27783.0,2494,3,0
2026-11-10T15:59:45.898Z,2026-11-10T15:58:00.693Z,27783.0,27783.0,27731.75,27731.75,2789,3,0
2026-11-10T16:02:10.886Z,2026-11-10T15:59:45.898Z,27731.75,27814.25,27731.75,27814.25,5378,3,0
2026-11-10T16:03:16.268Z,2026-11-10T16:02:10.886Z,27814.25,27814.25,27775.0,27775.0,1519,3,0
2026-11-10T16:05:10.815Z,2026-11-10T16:03:16.268Z,27775.0,27828.25,27775.0,27828.25,2925,3,0
2026-11-10T16:06:21.264Z,2026-11-10T16:05:10.815Z,27828.25,27828.25,27771.5,27771.5,1613,3,0
2026-11-10T16:09:08.133Z,2026-11-10T16:06:21.264Z,27771.5,27852.75,27771.5,27852.75,3629,3,0
2026-11-10T16:12:09.264Z,2026-11-10T16:09:08.133Z,27852.75,27852.75,27789.75,27789.75,3296,3,0
2026-11-10T16:13:05.606Z,2026-11-10T16:12:09.264Z,27789.75,27829.25,27789.75,27829.25,1220,3,0
2026-11-10T16:15:02.872Z,2026-11-10T16:13:05.606Z,27829.25,27829.25,27796.5,27796.5,2369,3,0
2026-11-10T16:15:33.360Z,2026-11-10T16:15:02.872Z,27796.5,27851.25,27796.5,27851.25,1611,3,0
2026-11-10T16:18:55.559Z,2026-11-10T16:15:33.360Z,27851.25,27851.25,27773.5,27773.5,4315,3,0
2026-11-10T16:20:24.572Z,2026-11-10T16:18:55.559Z,27773.5,27814.25,27773.5,27814.25,1382,3,0
2026-11-10T16:22:15.486Z,2026-11-10T16:20:24.572Z,27814.25,27814.25,27753.5,27753.5,2269,3,0
2026-11-10T16:22:54.677Z,2026-11-10T16:22:15.486Z,27753.5,27797.0,27753.5,27797.0,901,3,0
2026-11-10T16:23:51.227Z,2026-11-10T16:22:54.677Z,27797.0,27797.0,27763.25,27763.25,999,3,0
2026-11-10T16:25:22.828Z,2026-11-10T16:23:51.227Z,27763.25,27817.0,27763.25,27817.0,1992,3,0
2026-11-10T16:27:26.149Z,2026-11-10T16:25:22.828Z,27817.0,27817.0,27728.0,27728.0,3178,3,0
2026-11-10T16:29:33.751Z,2026-11-10T16:27:26.149Z,27728.0,27778.0,27728.0,27778.0,1949,3,0
2026-11-10T16:29:57.194Z,2026-11-10T16:29:33.751Z,27778.0,27778.0,27754.25,27754.25,389,3,0
2026-11-10T16:30:36.650Z,2026-11-10T16:29:57.194Z,27754.25,27785.25,27754.25,27785.25,799,3,0
2026-11-10T16:31:14.698Z,2026-11-10T16:30:36.650Z,27785.25,27785.25,27751.0,27751.0,779,3,0
2026-11-10T16:33:30.014Z,2026-11-10T16:31:14.698Z,27751.0,27811.5,27751.0,27811.5,2556,3,0
2026-11-10T16:34:41.861Z,2026-11-10T16:33:30.014Z,27811.5,27811.5,27768.75,27768.75,1334,3,0
2026-11-10T16:35:30.637Z,2026-11-10T16:34:41.861Z,27768.75,27792.5,27768.75,27792.5,790,3,0
2026-11-10T16:38:34.754Z,2026-11-10T16:35:30.637Z,27792.5,27792.5,27726.75,27726.75,3145,3,0
2026-11-10T16:38:59.351Z,2026-11-10T16:38:34.754Z,27726.75,27759.0,27726.75,27759.0,338,3,0
2026-11-10T16:40:52.765Z,2026-11-10T16:38:59.351Z,27759.0,27759.0,27694.75,27694.75,2629,3,0
2026-11-10T16:42:11.215Z,2026-11-10T16:40:52.765Z,27694.75,27741.75,27694.75,27741.75,1169,3,0
2026-11-10T16:44:15.656Z,2026-11-10T16:42:11.215Z,27741.75,27741.75,27697.0,27697.0,2106,3,0
2026-11-10T16:45:15.625Z,2026-11-10T16:44:15.656Z,27697.0,27737.5,27697.0,27737.5,794,3,0
2026-11-10T16:50:05.694Z,2026-11-10T16:45:15.625Z,27737.5,27737.5,27650.5,27650.5,5664,3,0
2026-11-10T16:50:26.146Z,2026-11-10T16:50:05.694Z,27650.5,27679.75,27650.5,27679.75,448,3,0
2026-11-10T16:52:59.167Z,2026-11-10T16:50:26.146Z,27679.75,27679.75,27642.75,27642.75,2418,3,0
2026-11-10T16:54:43.451Z,2026-11-10T16:52:59.167Z,27642.75,27692.5,27642.75,27692.5,1656,3,0
2026-11-10T16:57:24.433Z,2026-11-10T16:54:43.451Z,27692.5,27692.5,27617.0,27617.0,3097,3,0
```
SIGNALS (27 rows):
```csv
signal_bar_known_utc,engine_order_time_utc,side,stop_pts,target_pts,lots,session_end_exit_utc,fired_level_px,fired_line
2026-11-10T14:30:59.018Z,2026-11-10T14:31:01.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
2026-11-10T14:32:01.915Z,2026-11-10T14:32:03.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
2026-11-10T14:32:51.343Z,2026-11-10T14:32:53.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
2026-11-10T14:33:10.682Z,2026-11-10T14:33:12.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
2026-11-10T14:33:32.228Z,2026-11-10T14:33:34.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
2026-11-10T14:33:46.157Z,2026-11-10T14:33:48.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
2026-11-10T14:34:32.688Z,2026-11-10T14:34:34.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
2026-11-10T14:57:33.487Z,2026-11-10T14:57:35.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T14:59:44.342Z,2026-11-10T14:59:46.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:02:03.785Z,2026-11-10T15:02:05.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,28069.25,PRF1__LVN1
2026-11-10T15:03:38.381Z,2026-11-10T15:03:40.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,28003.0,PRF1__LVN2
2026-11-10T15:05:46.850Z,2026-11-10T15:05:48.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,28069.25,PRF1__LVN1
2026-11-10T15:13:05.309Z,2026-11-10T15:13:07.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,28003.0,PRF1__LVN2
2026-11-10T15:16:44.628Z,2026-11-10T15:16:46.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:17:21.553Z,2026-11-10T15:17:23.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:18:56.404Z,2026-11-10T15:18:58.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:19:37.658Z,2026-11-10T15:19:39.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:20:34.153Z,2026-11-10T15:20:36.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27952.75,PRF1__HVN2
2026-11-10T15:21:57.450Z,2026-11-10T15:21:59.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:22:51.117Z,2026-11-10T15:22:53.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:23:28.188Z,2026-11-10T15:23:30.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:25:58.679Z,2026-11-10T15:26:00.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27952.75,PRF1__HVN2
2026-11-10T15:33:04.758Z,2026-11-10T15:33:06.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27971.0,PRF1__HVN1
2026-11-10T15:34:01.198Z,2026-11-10T15:34:03.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27952.75,PRF1__HVN2
2026-11-10T15:35:11.709Z,2026-11-10T15:35:13.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27952.75,PRF1__HVN2
2026-11-10T16:50:05.694Z,2026-11-10T16:50:07.000Z,-1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
2026-11-10T16:54:43.451Z,2026-11-10T16:54:45.000Z,1,90.0,30.0,1,2026-11-10T17:00:00.000Z,27688.5,PRF1__SPH
```
INPUTS:
```csv
known_utc,T0_decision_utc_s,close,u_native_pts,k_times_u,PRF1__HVN1,PRF1__HVN2,PRF1__LVN1,PRF1__LVN2,PRF1__SPH,PRF1__SPL,PRF5__HVN1,PRF5__HVN2,PRF5__LVN1,PRF5__LVN2
2026-11-10T14:30:03.614Z,2026-11-10T14:25:00.000Z,27785.0,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:30:37.740Z,2026-11-10T14:30:03.000Z,27705.75,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:30:42.152Z,2026-11-10T14:30:37.000Z,27731.25,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:30:59.018Z,2026-11-10T14:30:42.000Z,27670.75,36.375,18.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:31:22.732Z,2026-11-10T14:30:59.000Z,27698.25,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:31:30.593Z,2026-11-10T14:31:22.000Z,27668.25,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:32:01.915Z,2026-11-10T14:31:30.000Z,27701.25,36.375,18.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:32:33.917Z,2026-11-10T14:32:01.000Z,27637.25,36.375,18.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:32:51.343Z,2026-11-10T14:32:33.000Z,27707.25,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:33:10.682Z,2026-11-10T14:32:51.000Z,27658.0,37.25,18.625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:33:32.228Z,2026-11-10T14:33:10.000Z,27691.75,37.5,18.75,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:33:36.735Z,2026-11-10T14:33:32.000Z,27666.75,37.5,18.75,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:33:46.157Z,2026-11-10T14:33:36.000Z,27698.0,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:33:51.775Z,2026-11-10T14:33:46.000Z,27669.5,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:34:32.688Z,2026-11-10T14:33:51.000Z,27765.25,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:34:38.512Z,2026-11-10T14:34:32.000Z,27732.25,37.5,18.75,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:35:01.540Z,2026-11-10T14:34:38.000Z,27784.75,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:35:06.741Z,2026-11-10T14:35:01.000Z,27742.5,37.5,18.75,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:35:20.072Z,2026-11-10T14:35:06.000Z,27772.25,38.75,19.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:35:29.319Z,2026-11-10T14:35:20.000Z,27735.75,38.75,19.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:35:36.100Z,2026-11-10T14:35:29.000Z,27762.0,38.75,19.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:35:41.871Z,2026-11-10T14:35:36.000Z,27733.25,37.5,18.75,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:36:05.272Z,2026-11-10T14:35:41.000Z,27801.0,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:36:14.390Z,2026-11-10T14:36:05.000Z,27765.5,37.5,18.75,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:37:07.619Z,2026-11-10T14:36:14.000Z,27822.5,37.5,18.75,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:37:18.783Z,2026-11-10T14:37:07.000Z,27770.0,37.5,18.75,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:37:55.174Z,2026-11-10T14:37:18.000Z,27817.0,38.25,19.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:38:39.454Z,2026-11-10T14:37:55.000Z,27752.0,38.25,19.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:38:41.828Z,2026-11-10T14:38:39.000Z,27777.0,38.25,19.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:39:03.920Z,2026-11-10T14:38:41.000Z,27743.25,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:39:29.353Z,2026-11-10T14:39:03.000Z,27808.5,36.75,18.375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:39:41.812Z,2026-11-10T14:39:29.000Z,27772.0,38.25,19.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:40:17.553Z,2026-11-10T14:39:41.000Z,27830.75,38.25,19.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:40:22.961Z,2026-11-10T14:40:17.000Z,27794.25,40.875,20.4375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:40:41.878Z,2026-11-10T14:40:22.000Z,27818.0,40.875,20.4375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:40:57.168Z,2026-11-10T14:40:41.000Z,27775.0,40.875,20.4375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:41:09.709Z,2026-11-10T14:40:57.000Z,27801.5,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:41:23.507Z,2026-11-10T14:41:09.000Z,27771.75,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:41:34.349Z,2026-11-10T14:41:23.000Z,27812.0,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:42:09.987Z,2026-11-10T14:41:34.000Z,27757.0,41.25,20.625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:42:27.463Z,2026-11-10T14:42:09.000Z,27787.75,41.25,20.625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:42:54.155Z,2026-11-10T14:42:27.000Z,27747.0,39.875,19.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:43:55.550Z,2026-11-10T14:42:54.000Z,27844.25,39.875,19.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:44:22.203Z,2026-11-10T14:43:55.000Z,27812.25,39.875,19.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:45:01.599Z,2026-11-10T14:44:22.000Z,27863.5,38.0,19.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:45:12.728Z,2026-11-10T14:45:01.000Z,27823.75,38.0,19.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:45:22.337Z,2026-11-10T14:45:12.000Z,27859.0,38.0,19.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:45:34.677Z,2026-11-10T14:45:22.000Z,27808.75,36.5,18.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:45:56.209Z,2026-11-10T14:45:34.000Z,27837.75,38.0,19.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:46:31.250Z,2026-11-10T14:45:56.000Z,27803.25,36.5,18.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:46:38.630Z,2026-11-10T14:46:31.000Z,27828.0,36.5,18.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:47:01.103Z,2026-11-10T14:46:38.000Z,27786.25,36.5,18.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:47:14.286Z,2026-11-10T14:47:01.000Z,27815.75,36.5,18.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:47:29.724Z,2026-11-10T14:47:14.000Z,27760.5,36.5,18.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:48:33.328Z,2026-11-10T14:47:29.000Z,27804.5,38.0,19.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:49:02.944Z,2026-11-10T14:48:33.000Z,27754.5,39.625,19.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:49:24.833Z,2026-11-10T14:49:02.000Z,27790.5,40.0,20.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:49:37.129Z,2026-11-10T14:49:24.000Z,27758.0,40.0,20.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:50:16.141Z,2026-11-10T14:49:37.000Z,27833.25,40.0,20.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:50:46.315Z,2026-11-10T14:50:16.000Z,27784.0,40.5,20.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:51:59.513Z,2026-11-10T14:50:46.000Z,27850.5,41.25,20.625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:52:58.260Z,2026-11-10T14:51:59.000Z,27796.0,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:53:37.254Z,2026-11-10T14:52:58.000Z,27853.25,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:54:04.852Z,2026-11-10T14:53:37.000Z,27830.0,42.5,21.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:54:11.734Z,2026-11-10T14:54:04.000Z,27881.75,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:54:29.564Z,2026-11-10T14:54:11.000Z,27838.25,42.5,21.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:55:45.566Z,2026-11-10T14:54:29.000Z,27947.75,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:56:02.963Z,2026-11-10T14:55:45.000Z,27910.5,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:57:33.487Z,2026-11-10T14:56:02.000Z,27971.75,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:58:13.431Z,2026-11-10T14:57:33.000Z,27945.5,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:59:44.342Z,2026-11-10T14:58:13.000Z,28016.75,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T14:59:58.610Z,2026-11-10T14:59:44.000Z,27989.0,42.875,21.4375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:00:20.884Z,2026-11-10T14:59:58.000Z,28030.0,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:00:30.986Z,2026-11-10T15:00:20.000Z,28006.25,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:02:03.785Z,2026-11-10T15:00:30.000Z,28090.0,42.5,21.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:02:34.869Z,2026-11-10T15:02:03.000Z,28025.75,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:03:03.043Z,2026-11-10T15:02:34.000Z,28055.5,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:03:38.381Z,2026-11-10T15:03:03.000Z,27993.0,42.5,21.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:04:53.459Z,2026-11-10T15:03:38.000Z,28062.0,42.5,21.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:05:13.984Z,2026-11-10T15:04:53.000Z,28035.75,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:05:46.850Z,2026-11-10T15:05:13.000Z,28080.0,42.5,21.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:07:06.313Z,2026-11-10T15:05:46.000Z,28013.5,42.5,21.25,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:07:28.279Z,2026-11-10T15:07:06.000Z,28037.0,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:07:36.518Z,2026-11-10T15:07:28.000Z,28008.25,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:08:12.032Z,2026-11-10T15:07:36.000Z,28068.75,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:09:31.793Z,2026-11-10T15:08:12.000Z,28005.5,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:10:18.273Z,2026-11-10T15:09:31.000Z,28058.0,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:11:31.713Z,2026-11-10T15:10:18.000Z,28016.5,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:11:38.865Z,2026-11-10T15:11:31.000Z,28041.0,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:13:05.309Z,2026-11-10T15:11:38.000Z,27994.0,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:13:39.492Z,2026-11-10T15:13:05.000Z,28035.25,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:16:44.628Z,2026-11-10T15:13:39.000Z,27949.0,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:17:21.553Z,2026-11-10T15:16:44.000Z,28002.0,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:18:56.404Z,2026-11-10T15:17:21.000Z,27944.0,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:19:37.658Z,2026-11-10T15:18:56.000Z,27985.75,42.375,21.1875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:20:34.153Z,2026-11-10T15:19:37.000Z,27949.0,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:21:57.450Z,2026-11-10T15:20:34.000Z,28002.0,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:22:51.117Z,2026-11-10T15:21:57.000Z,27961.0,42.0,21.0,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:23:09.552Z,2026-11-10T15:22:51.000Z,27993.75,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:23:28.188Z,2026-11-10T15:23:09.000Z,27941.0,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:23:43.368Z,2026-11-10T15:23:28.000Z,27964.25,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:24:43.661Z,2026-11-10T15:23:43.000Z,27893.25,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:25:00.671Z,2026-11-10T15:24:43.000Z,27919.0,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:25:18.673Z,2026-11-10T15:25:00.000Z,27890.0,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:25:58.679Z,2026-11-10T15:25:18.000Z,27964.5,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:27:25.764Z,2026-11-10T15:25:58.000Z,27920.5,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:27:33.580Z,2026-11-10T15:27:25.000Z,27951.75,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:28:42.682Z,2026-11-10T15:27:33.000Z,27884.5,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:29:22.019Z,2026-11-10T15:28:42.000Z,27914.75,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:29:53.620Z,2026-11-10T15:29:22.000Z,27878.0,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:30:16.545Z,2026-11-10T15:29:53.000Z,27933.25,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:30:44.023Z,2026-11-10T15:30:16.000Z,27904.25,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:31:01.110Z,2026-11-10T15:30:44.000Z,27928.0,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:31:29.807Z,2026-11-10T15:31:01.000Z,27904.25,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:33:04.758Z,2026-11-10T15:31:29.000Z,27978.5,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:34:01.198Z,2026-11-10T15:33:04.000Z,27934.25,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:34:29.987Z,2026-11-10T15:34:01.000Z,27960.25,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:34:47.390Z,2026-11-10T15:34:29.000Z,27922.75,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:35:11.709Z,2026-11-10T15:34:47.000Z,27956.25,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:35:33.618Z,2026-11-10T15:35:11.000Z,27917.5,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:35:42.500Z,2026-11-10T15:35:33.000Z,27940.75,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:38:39.786Z,2026-11-10T15:35:42.000Z,27857.0,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:39:30.848Z,2026-11-10T15:38:39.000Z,27901.5,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:41:08.520Z,2026-11-10T15:39:30.000Z,27857.25,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:41:22.527Z,2026-11-10T15:41:08.000Z,27884.0,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:42:00.139Z,2026-11-10T15:41:22.000Z,27836.0,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:42:50.771Z,2026-11-10T15:42:00.000Z,27864.5,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:43:02.137Z,2026-11-10T15:42:50.000Z,27832.0,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:43:13.525Z,2026-11-10T15:43:02.000Z,27857.75,41.125,20.5625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:43:29.058Z,2026-11-10T15:43:13.000Z,27827.5,41.125,20.5625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:44:04.567Z,2026-11-10T15:43:29.000Z,27851.0,41.125,20.5625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:45:51.173Z,2026-11-10T15:44:04.000Z,27786.75,41.0,20.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:46:37.655Z,2026-11-10T15:45:51.000Z,27829.25,41.125,20.5625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:48:05.128Z,2026-11-10T15:46:37.000Z,27760.0,41.125,20.5625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:49:32.311Z,2026-11-10T15:48:05.000Z,27796.5,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:50:24.728Z,2026-11-10T15:49:32.000Z,27707.0,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:51:03.686Z,2026-11-10T15:50:24.000Z,27773.75,41.375,20.6875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:52:04.823Z,2026-11-10T15:51:03.000Z,27711.0,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:53:09.372Z,2026-11-10T15:52:04.000Z,27757.75,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:54:00.023Z,2026-11-10T15:53:09.000Z,27715.75,42.125,21.0625,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:54:29.777Z,2026-11-10T15:54:00.000Z,27754.5,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:54:52.704Z,2026-11-10T15:54:29.000Z,27730.75,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:55:37.030Z,2026-11-10T15:54:52.000Z,27756.5,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:55:52.352Z,2026-11-10T15:55:37.000Z,27709.75,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:56:02.720Z,2026-11-10T15:55:52.000Z,27735.0,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:56:23.806Z,2026-11-10T15:56:02.000Z,27699.25,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:56:43.443Z,2026-11-10T15:56:23.000Z,27739.75,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:56:50.187Z,2026-11-10T15:56:43.000Z,27715.75,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:58:00.693Z,2026-11-10T15:56:50.000Z,27783.0,41.625,20.8125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T15:59:45.898Z,2026-11-10T15:58:00.000Z,27731.75,41.75,20.875,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:02:10.886Z,2026-11-10T15:59:45.000Z,27814.25,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:03:16.268Z,2026-11-10T16:02:10.000Z,27775.0,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:05:10.815Z,2026-11-10T16:03:16.000Z,27828.25,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:06:21.264Z,2026-11-10T16:05:10.000Z,27771.5,43.0,21.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:09:08.133Z,2026-11-10T16:06:21.000Z,27852.75,43.0,21.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:12:09.264Z,2026-11-10T16:09:08.000Z,27789.75,43.0,21.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:13:05.606Z,2026-11-10T16:12:09.000Z,27829.25,43.0,21.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:15:02.872Z,2026-11-10T16:13:05.000Z,27796.5,43.0,21.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:15:33.360Z,2026-11-10T16:15:02.000Z,27851.25,43.0,21.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:18:55.559Z,2026-11-10T16:15:33.000Z,27773.5,43.0,21.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:20:24.572Z,2026-11-10T16:18:55.000Z,27814.25,43.0,21.5,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:22:15.486Z,2026-11-10T16:20:24.000Z,27753.5,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:22:54.677Z,2026-11-10T16:22:15.000Z,27797.0,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:23:51.227Z,2026-11-10T16:22:54.000Z,27763.25,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:25:22.828Z,2026-11-10T16:23:51.000Z,27817.0,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:27:26.149Z,2026-11-10T16:25:22.000Z,27728.0,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:29:33.751Z,2026-11-10T16:27:26.000Z,27778.0,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:29:57.194Z,2026-11-10T16:29:33.000Z,27754.25,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:30:36.650Z,2026-11-10T16:29:57.000Z,27785.25,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:31:14.698Z,2026-11-10T16:30:36.000Z,27751.0,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:33:30.014Z,2026-11-10T16:31:14.000Z,27811.5,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:34:41.861Z,2026-11-10T16:33:30.000Z,27768.75,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:35:30.637Z,2026-11-10T16:34:41.000Z,27792.5,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:38:34.754Z,2026-11-10T16:35:30.000Z,27726.75,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:38:59.351Z,2026-11-10T16:38:34.000Z,27759.0,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:40:52.765Z,2026-11-10T16:38:59.000Z,27694.75,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:42:11.215Z,2026-11-10T16:40:52.000Z,27741.75,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:44:15.656Z,2026-11-10T16:42:11.000Z,27697.0,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:45:15.625Z,2026-11-10T16:44:15.000Z,27737.5,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:50:05.694Z,2026-11-10T16:45:15.000Z,27650.5,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:50:26.146Z,2026-11-10T16:50:05.000Z,27679.75,42.625,21.3125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:52:59.167Z,2026-11-10T16:50:26.000Z,27642.75,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:54:43.451Z,2026-11-10T16:52:59.000Z,27692.5,41.875,20.9375,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
2026-11-10T16:57:24.433Z,2026-11-10T16:54:43.000Z,27617.0,42.25,21.125,27971,27952.75,28069.25,28003,27688.5,27481.25,27160.75,27167.75,28226.5,29398.75
```
TRADES (engine month 202611 landed in the engine for this set; 12 rows):
```csv
entry_utc,entry_price,exit_utc,exit_price,exit_reason,side,lots,points,gross_usd,fee_engine_usd,fee_standard_usd_4.84_per_lot
2026-11-10T14:31:02.000Z,27688.5,2026-11-10T14:32:07.496Z,27658.5,Target,-1,1,30.0,600,1.18,4.84
2026-11-10T14:32:54.000Z,27683.5,2026-11-10T14:33:55.002Z,27713.5,Target,1,1,30.0,600,1.18,4.84
2026-11-10T14:34:35.000Z,27735.75,2026-11-10T14:34:43.231Z,27765.75,Target,1,1,30.0,600,1.18,4.84
2026-11-10T14:57:36.000Z,27955.75,2026-11-10T14:58:31.889Z,27985.75,Target,1,1,30.0,600,1.18,4.84
2026-11-10T14:59:47.000Z,27996.5,2026-11-10T15:00:17.049Z,28026.5,Target,1,1,30.0,600,1.18,4.84
2026-11-10T15:02:06.000Z,28071.5,2026-11-10T15:15:59.384Z,27982.25,Stop,1,1,-89.25,-1785,1.18,4.84
2026-11-10T15:16:47.000Z,27975.75,2026-11-10T15:18:47.325Z,27945.75,Target,-1,1,30.0,600,1.18,4.84
2026-11-10T15:18:59.000Z,27963.0,2026-11-10T15:23:50.838Z,27933.0,Target,-1,1,30.0,600,1.18,4.84
2026-11-10T15:26:01.000Z,27935.5,2026-11-10T15:32:15.860Z,27965.5,Target,1,1,30.0,600,1.18,4.84
2026-11-10T15:33:07.000Z,27947.5,2026-11-10T15:38:22.957Z,27859.25,Stop,1,1,-88.25,-1765,1.18,4.84
2026-11-10T16:50:08.000Z,27676.5,2026-11-10T16:51:34.026Z,27646.5,Target,-1,1,30.0,600,1.18,4.84
2026-11-10T16:54:46.000Z,27663.5,2026-11-10T17:00:01.000Z,27626.25,UWTime,1,1,-37.25,-745,1.18,4.84
```

## 8. What is still open (plain list)
1. td 20261125 scale constants (theta): needs the engine stats rows 1114-1124 or the lead's A/B decision; both columns given for the days up to 1120.
2. PRF5 five-latest-available-days vs five-latest-calendar-days (section 4).
3. Fill simulation, one-position rule, stop/target handling, roll rules: cited from D8_BUILD_SPEC (b2), not re-verified by me.
4. Roll handling of the lines and bars (front-month roll mid-December): no roll in the sample days; not verified.
5. Timestamp convention: store timestamps vs NT8 export (~13 ms offset, autopilot/D8_ASIA_NEWBOOK_INPUTS.md section 1): not resolved.
6. Stack-level layers (locks, caps, lots 4/2/1 etc.) are NOT part of this page; the TRADES are bare R0, 1 lot.

## Relay questions 2026-11-24 21:25Z (answers from engine code, read-only)
- Q5a LVN rule = LOWEST smoothed value, not depth against neighbouring maxima: code/th_grid/triggers_d/fd_profile.py `levels`: candidates i in range(max(a,1), min(b,len(sm)-2)) (a = VAL row, b = VAH row; range end exclusive, so the VAH row itself is out) with sm[i] <= sm[i-1] and sm[i] < sm[i+1]; `sorted(tr, key=lambda i: sm[i])[:2]` = the two lowest smoothed values (Python sort is stable: equal values keep the lower row first). A plateau gives its FIRST (lowest) row for LVN (<= left, < right); for HVN (sm[i] >= sm[i-1] and sm[i] > sm[i+1], i in range(1,len-1), |i-POC| > 8 rows) a plateau gives its LAST row; HVN sorted by -sm, stable.
- Q5b Kernel: k = exp(-0.5*(arange(-24,25)/8)**2), 49 taps, normalised by its own full sum, `np.convolve(hist, k/k.sum(), 'same')` over the histogram from the lowest traded tick to the highest (zero padding at both ends, output length = len(hist), centred). Matches the relay's sigma 8, +-24, normalised, zero padding. Histogram rows = every RTH record (ET 09:30-16:00) price in ticks weighted by size, no run merge.
- Q5c Le4fede95 LVN2 on td 20261110 (profile of ET day 20261109): stored 28003.00 is right. Recomputed from the tape with the engine function: smoothed values around it (points: smoothed volume) 28002.75: 153.07, 28003.00: 152.89, 28003.25: 153.31, 28003.75: 155.57. 28003.00 is the strict local minimum; 28003.75 has a lower neighbour on its left so it cannot be a local minimum under ANY tie rule (strict, <=, inclusive of the VAH row: all give 28069.25 and 28003.00 as the two lowest). A 3-tick shift (0.75 pt) points to an alignment difference on the relay side (histogram start row, kernel offset, or a different record set); check that the kernel is centred and that the histogram index = price tick - lowest tick.
- Q5d PRF5 for td 20261110 (points). AS STORED / engine (days 1029, 1030, 1105, 1106, 1109 = the five latest days in the engine store): POC 29561.25, VAH 29677.00, VAL 27246.75, HVN1 27160.75, HVN2 27167.75, LVN1 28226.50, LVN2 29398.75. HOLE-FILLED (days 1103, 1104, 1105, 1106, 1109, 1103-04 from hist_replica; FORMULA with the same functions, NOT an engine run): POC 28320.00, VAH 28969.00, VAL 27221.50, HVN1 28314.00, HVN2 27176.75, LVN1 28195.75, LVN2 28958.50. PRF1 (day 1109): POC 27940.00, VAH 28095.50, VAL 27799.50, HVN1 27971.00, HVN2 27952.75, LVN1 28069.25, LVN2 28003.00, SPH 27688.50, SPL 27481.25.
