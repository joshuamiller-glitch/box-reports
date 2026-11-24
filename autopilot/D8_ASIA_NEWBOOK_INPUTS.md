# D8_ASIA_NEWBOOK_INPUTS: coding inputs for the D8 port of the two new Asia books L9c2622b0 (pnf_7, VWAP-line break) and L4aaacdb2 (vsess_30, session-VWAP band break)

Written 2026-11-24 by a relay sub-agent (not typed by Josh). Order: autopilot/DIRECTIVE_20261124_1356Z_ASIA_NEW_BOOKS_CODING_INPUTS.md. Information only: no new test, no gate or rule change, nothing queued, nothing live, no spend, no data deleted, no credentials, engine files read-only (nice -n 10).

DATA END (read first). NEWEST DAY USED: **td 20261120** (hist_replica day file /mnt/l2/l2vast/_hist_replica/days/2026/NQ_20261120.npz, complete = true in its meta_json; coverage.csv last row 20261120). td 20261123 is NOT used (it will be added after the data top-up). The ENGINE's own stores (/mnt/l2/l2vast/_d8spec/runstats/stats_day.parquet and stats_sess.parquet, identical in rng and session volume to /mnt/l2/l2vast/_bars/stats_*.parquet) end at **td 20261113** and have holes: no stats_day row for 20261102, 20261103, 20261104; no Asia (code 0) stats_sess row for 20261102 to 20261105; the stats_day row of 20261105 is a half day (volume 571,100 versus 1,241,173 in hist_replica). The engine bars for both books (stored pnf_7 in /mnt/l2/l2vast/_bars/pnf_7, vsess_30 in /mnt/l2/l2vast/_d8spec/bars_c/vsess_30) were built from those stores, so every "engine used" number below is the engine store as it is, holes included. Where I also give a "hole-filled" number it is a formula result (the engine's own function on a table completed from hist_replica), clearly labelled; it is not something the engine ran.

Method (all with the engine's own code): scale function `scales()` in code/th_bars/build_month.py:13-32 imported and run on (a) the stored runstats tables (reproduces the spec values: td 20261110 s_rng 3.048303, sess_vol 85,212, thr 2,840.4, box 21 = /mnt/l2/l2vast/_d8spec/spec_scales_2days.json, exactly), (b) a copy of those tables with the holes filled and 20261116-20 added from hist_replica (rng built with the same file-piece rule as code/th_bars/stats.py, see 2.). Session split = `sessionize()` in code/th_bars/common.py:10-17 (ET clock; code 0 = Asia = ET minute-of-day >= 1080 or < 120; trading date = ET + 6 h, so the Asia session of td D starts 18:00 ET on the evening before D).

## 1. Asia session volume per trading date (last 45 td, 20260921 to 20261120)

What the number is. Volume = sum of `sz` (contracts) of EVERY trade record (print row of the tape) whose ET time falls in session code 0 of that td. It is **all records of the session, no filter** (no size, side, price or quality filter; no run merge; the engine sums the raw tape rows: code/th_bars/stats.py:`s=df.groupby(['td','code']).agg(vol=('vol','sum'),n=('px','size'))`, with vol = `sz` of every row). Contract: **one instrument id on every one of these 45 sessions: 261401** (the NQ continuous front, NQZ6 in this period; the id-to-name mapping is not stored in the day file, I did not find a symbol table here, so the name NQZ6 is my inference from the date and the roll history, not read from a file). The engine stats do not filter by instrument: they sum all instrument ids (code/th_bars/stats.py groups by (td, code) only). The vsess bar clock itself resets per (session, instrument id) (kernels.py k_cum, line 16). No roll occurred inside these 45 Asia sessions.
Source of the column asia_session0_contracts: hist_replica day files (npz `sz`, `ts`, `inst`). Cross-check: on all 36 td where the engine store has an Asia value (column engine_stats_sess_value) the two are **identical to the contract**. The engine tape /mnt/l2/l2vast/_bars/trades/ and hist_replica carry the same records (same count and volume per session) but their timestamps differ by about 13 to 14 ms (e.g. td 20261110 first Asia record: engine tape 23:00:00.000 and 23:00:00.001, hist_replica 23:00:00.013); I did not establish why (feed timestamp field not documented in the files I read).

```csv
td,asia_session0_contracts,tape_records,instrument_id,first_record_ET,engine_stats_sess_value
20260921,51227,38812,261401,18:00:00.053,51227
20260922,60435,44589,261401,18:00:00.014,60435
20260923,40506,31118,261401,18:00:00.012,40506
20260924,48660,36389,261401,18:00:00.010,48660
20260925,40210,31300,261401,18:00:00.010,40210
20260928,65882,51795,261401,18:00:00.062,65882
20260929,59712,44316,261401,18:00:00.019,59712
20260930,53030,40361,261401,18:00:00.012,53030
20261001,62986,47816,261401,18:00:00.011,62986
20261002,46807,36696,261401,18:00:00.011,46807
20261005,56097,42771,261401,18:00:00.063,56097
20261006,41519,32176,261401,18:00:00.014,41519
20261007,41464,31293,261401,18:00:00.012,41464
20261008,48533,36910,261401,18:00:00.012,48533
20261009,56511,43180,261401,18:00:00.011,56511
20261012,61613,47412,261401,18:00:00.083,61613
20261013,85212,64542,261401,18:00:00.021,85212
20261014,57292,43601,261401,18:00:00.014,57292
20261015,111514,86830,261401,18:00:00.012,111514
20261016,65325,52583,261401,18:00:00.010,65325
20261019,76729,58585,261401,18:00:00.089,76729
20261020,77936,59733,261401,18:00:00.011,77936
20261021,86630,68461,261401,18:00:00.015,86630
20261022,88843,67873,261401,18:00:00.012,88843
20261023,88022,71390,261401,18:00:00.012,88022
20261026,86113,68145,261401,18:00:00.085,86113
20261027,66450,53101,261401,18:00:00.015,66450
20261028,54773,43735,261401,18:00:00.012,54773
20261029,104646,82351,261401,18:00:00.013,104646
20261030,117552,89073,261401,18:00:00.012,117552
20261102,74429,56474,261401,18:00:00.070,HOLE_not_in_engine_store
20261103,67753,55345,261401,18:00:00.013,HOLE_not_in_engine_store
20261104,184771,144214,261401,18:00:00.013,HOLE_not_in_engine_store
20261105,103784,83105,261401,18:00:00.011,HOLE_not_in_engine_store
20261106,131618,104891,261401,18:00:00.011,131618
20261109,109651,89439,261401,18:00:00.109,109651
20261110,64484,51093,261401,18:00:00.013,64484
20261111,75835,58727,261401,18:00:00.011,75835
20261112,84184,66128,261401,18:00:00.026,84184
20261113,79803,63717,261401,18:00:00.010,79803
20261116,116443,88468,261401,18:00:00.097,NOT_YET_IN_ENGINE_STORE
20261117,86346,67455,261401,18:00:00.014,NOT_YET_IN_ENGINE_STORE
20261118,117228,91493,261401,18:00:00.023,NOT_YET_IN_ENGINE_STORE
20261119,101636,80017,261401,18:00:00.011,NOT_YET_IN_ENGINE_STORE
20261120,105870,86223,261401,18:00:00.014,NOT_YET_IN_ENGINE_STORE
```
(first_record_ET is the hist_replica timestamp of the first record in session 0; in the 45 days it is 18:00:00.010 to .109 ET. 20261016 .010 etc. are ET.)

### 1b. sess_vol median and vsess_30 threshold per td (last 10 td, plus 20261102-06 for context)

Engine rule, code/th_bars/build_month.py:23-31 and 76-78, 96: for td at row i of stats_day, sess_vol[0] = median of the Asia `vol` values of the 20 stats_day ROWS before row i (rows, not calendar days; window `x[max(0,i-20):i]`; the current session never used); values that are missing or <= 0 are dropped (`w=w[w>0]`); needs at least 5 values, else NaN, then back/forward fill. Threshold per print = `np.maximum(svol/p,1.0)` with p = 30 (line 96), fixed for the whole session of that td, in contracts (float). A bar closes at the first print whose cumulative bar volume is >= thr (kernels.py:21-31).
Columns: A = engine store as it is (what the stored bars used; holes included; blank = the engine store has no row for that td: it never ran those days). B = the same function on the table with the holes (20261102-05) filled and 20261116-20 added from hist_replica (FORMULA ONLY, not engine-run). thr30 = max(sess_vol/30, 1).

```csv
td,A_sess_vol_median20,A_vsess_30_thr,B_sess_vol_median20,B_vsess_30_thr
20261102,,,71589.5,2386.317
20261103,,,75579.0,2519.300
20261104,,,75579.0,2519.300
20261105,71589.5,2386.317,77332.5,2577.750
20261106,76729.0,2557.633,81574.0,2719.133
20261109,77936.0,2597.867,85662.5,2855.417
20261110,85212.0,2840.400,86371.5,2879.050
20261111,85212.0,2840.400,86371.5,2879.050
20261112,85212.0,2840.400,86371.5,2879.050
20261113,85212.0,2840.400,85148.5,2838.283
20261116,,,85148.5,2838.283
20261117,,,86371.5,2879.050
20261118,,,86488.0,2882.933
20261119,,,87184.0,2906.133
20261120,,,87184.0,2906.133
```
Checks: A for 20261109 and 20261110 = 77,936 and 85,212 as in autopilot/D8_BAR_DEFS.md 3.5 and spec_scales_2days.json (thr 2,840.4). The stored vsess_30 bars confirm A on 20261110: 22 closed bars have volume 2,841 to 2,851 (all >= 2,840.4) and the last bar is the open remainder (1,924, part = 1); bar volumes sum to 64,484 = the session volume. Same for 20261112 (bars 2,841-2,842, thr 2,840.4, 30 bars) and 20261113. Note 20261111 shows A = 85,212 because the window (20 rows) still holds the same median; and A and B differ by the holes (the median window for B includes the 1102-05 Asia sessions of 74,429, 67,753, 184,771, 103,784 that the engine never saw). Whether the NT8 build should copy A (engine as stored) or B (complete) is a decision for the lead; both are given.
For the day 20261123 (not computed here): the engine function on a completed table needs the 20 Asia volumes up to 20261120 from the table in 1; the median of the last 20 td of the A-style window can be formed from the CSV above (B-column logic).

## 2. s_rng per td and the pnf_7 box in ticks

Rules (code): box = `np.maximum(1,np.round(p*S['rng'])).astype(np.int64)` with p = 7, S['rng'] = s_rng of the print's td (build_month.py:73 `S={c:sc['s_'+c][ix] ...}`, line 136). np.round = half-to-even. Units: ticks of 0.25 point (prices are int ticks). s_rng = tr/r0 where tr = trailing median of the daily range `rng` (points) over the 20 stats_day ROWS before the td (values <= 0 dropped, at least 5) and **r0 = median of the first 60 days' range = 191.5 points** (build_month.py:16-22; `out['s_rng']=tr/r0`). Column abs_rng_pts = tr.
How the daily `rng` is built (stats.py:18, a quirk worth knowing): per trade FILE (UTC calendar day) per instrument id the range hi-lo of px is taken, then `rng` of the td = the MAX over the pieces, divided by 4 (points). A td spans two UTC day files (the Asia evening is in the first, the rest of the td in the second), so the td range is the larger of the two pieces, **not** the true full-td range. I reproduced this rule from hist_replica (split by UTC day) and it equals the engine value on every td where both exist (e.g. 20261019: true range 757.5, engine 414.75; piecewise 414.75). The B rows below use this same piecewise rule.
Columns A / B as in 1b. A_box = stored/engine; B_box = formula on the completed table.

```csv
td,A_s_rng,A_abs_rng_pts,A_pnf7_box_ticks,B_s_rng,B_abs_rng_pts,B_pnf7_box_ticks
20261109,2.929504,561.000,21,3.048303,583.750,21
20261110,3.048303,583.750,21,3.265666,625.375,23
20261111,3.047650,583.625,21,3.265666,625.375,23
20261112,3.097258,593.125,22,3.265666,625.375,23
20261113,3.216057,615.875,23,3.383812,648.000,24
20261116,,,,3.383812,648.000,24
20261117,,,,3.750653,718.250,26
20261118,,,,4.095300,784.250,29
20261119,,,,4.095300,784.250,29
20261120,,,,4.095300,784.250,29
```
(Rows 20261109 to 20261113 are the last 5 td with engine rows; the 20261116-20 A cells are empty because the engine store ends at 20261113; if the engine function were asked for those days it would clamp to the 20261113 row, `np.minimum(ix,len-1)` in build_month.py:71, i.e. s_rng 3.216057 and box 23; I did not run that, it is what the code does.)
Check against the stored bars: I rebuilt the stored pnf_7 Asia bars of 20261110, 20261112 and 20261113 from the engine tape with kernels.k_pnf and boxes 21, 22, 23: **99/173/89 bars, identical to the stored ones in O, H, L, C, volume and known time (all columns tested)**; with box +-1 the bar counts differ (e.g. 20261110: box 20 gives 99 bars with a different path, box 22 gives 87; the gcd of the stored |close-open| per column is 21 / 22 / 23). So the stored box was A: 21, 22, 23 on those three days. The ten-day rows for 20261102 to 20261106 were not asked; A has no row for 1102-1104.

## 3. k_pnf exact rules (code/th_bars/kernels.py:247-271; used at build_month.py:135-136 with rows [5,7,10,14,20,28,40,56])

All in integer ticks; B = box of the print's td; state resets (no bar emitted, open column dropped) at every change of key (session id = td x 10 + code) or instrument id (line 253).
1. First column start: the FIRST print of the session (key/iid) sets lvl = st = its price p and t0 = its time (line 255-256); d = 0 (undecided). While d == 0: first print with p >= lvl + B starts an UP column (d = 1, st = lvl, lvl = lvl + floor((p-lvl)/B)*B); first with p <= lvl - B starts a DOWN column (st = lvl, lvl = lvl - floor((lvl-p)/B)*B) (lines 258-260). Whichever comes first wins; the first column's st = the first print price.
2. Grid anchoring: there is no fixed price grid. Every level is the session's first print price plus or minus whole multiples of B (lvl moves by floor multiples, st = lvl -+ B on reversal). The grid is re-anchored at the first print of every session and after every instrument change.
3. New box in a column: in an UP column a print p >= lvl + B moves lvl up by floor((p-lvl)/B) boxes (several boxes at once if the print jumps); in a DOWN column p <= lvl - B moves lvl down likewise (lines 262, 267). No bar is emitted for these.
4. Reversal test: UP column reverses when p <= lvl - 3*B (**<=, so exactly 3 boxes counts**), DOWN column when p >= lvl + 3*B (lines 263, 268). It is tested only if the print did not extend the column (elif).
5. Emitted bar (one per COMPLETED column, at the confirming reversal print): UP column o = st, h = lvl, l = st, c = lvl; DOWN column o = st, h = st, l = lvl, c = lvl (lines 264, 269). High and low are the column extreme and start LEVELS on the grid, not the highest/lowest print of the column.
6. Open of the new column: st = lvl - B for an up-to-down reversal (one box beyond the old extreme, NOT the reversal price), st = lvl + B for down-to-up (lines 265, 270). The new lvl = old lvl -+ floor(|old lvl - p|/B)*B, so at least 3 boxes beyond the old extreme (it can be more if the print jumps). So the next bar's open = old extreme -+ 1 box, and its own extreme starts 2 boxes further than its open; the column is "3 boxes" deep when emitted only if no further box was added.
7. Volume (also count n and delta): accumulated per print from the column's first print, incl. the confirming reversal print (line 257 adds the print BEFORE the tests, and the bar is emitted with it). After the reversal vol, n, dlt are reset to 0 (265, 270), so the reversal print's volume is in the OLD column bar and not in the new one. The first column's volume starts at the first print of the session (it includes the undecided d == 0 phase).
8. Time: known_ts = t1 = the tape timestamp of the confirming (reversal) print itself (`ts[i]`); the first record whose price meets the test closes it (line 264: ..., t0, ts[i], ts[i]). t0 of a column = time of its first print for the first column of a session and ts[i] of the reversal print for later columns (so a later column's t0 equals the previous bar's known time). No wait for a later print.
9. The trailing open column at session end is NOT emitted (no flush in k_pnf; `part` is always 0). Example td 20261110: stored bar volumes sum to 64,325 against a session volume of 64,484 (the open column's 159 contracts are missing).
10. Print granularity: pnf is class UNAFFECTED by the D8 run-merge print rule (autopilot/D8_PRINT_RULE.md section 5 table, row pnf: 100.00% of run-merge bars equal the old-engine bars in O/H/L/C + close time, month 2026-10, 53,241 bars; section 2 same finding for the other price bars). So the book's pnf_7 bars are the old-engine (raw tape row) bars in /mnt/l2/l2vast/_bars/pnf_7; only the volume column of a bar can differ under a run merge. Verified here: rebuilt on the raw tape = stored. Example 20261110 first column: o 112256 (28,064.00) to c 112361 (28,090.25) = 105 ticks = 5 boxes of 21, t0 23:00:00.000 UTC, known 23:00:01.013655623 UTC, volume 73 (matches the parity page bar 1).
The VWAP-line break trigger itself (plain variant, u = 5.0 fixed points; line value = last 1-minute start <= T0 within 120 s from the stored line files) is in autopilot/D8_PARITY_L9c2622b0_20261110.md INPUTS and the AUTO:BOOK:L9c2622b0 block of autopilot/D8_BUILD_SPEC.md; not re-derived here (the line values come from the engine store, not from tape; per code/th_d8spec/gen_book_blocks.py:82 text).

## 4. TRADES block for 20261110

**The engine month 202611 has NOT landed for either book.** Checked: /mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/TL3_ALN_AS_L9c2622b0_R0BRP45/ and .../TL3_ALN_AS_L4aaacdb2_R0BRP30/ list months up to 202610 only (no 202611 directory in any runs*/ tree), and the TRADES section of autopilot/D8_PARITY_L9c2622b0_20261110.md and D8_PARITY_L4aaacdb2_20261110.md still reads "OPEN: the engine month 202611 is not landed". No TRADES values are given (none invented). What exists for 20261110 today: the BARS and SIGNALS blocks of those two pages. L9c2622b0 (pnf_7, box 21): 99 bars, 15 signals (side/stop/target 45/45 pts, listed in the page). L4aaacdb2 (vsess_30, thr 2,840.4): 23 bars (22 closed + the open remainder), 0 signals on that day.

## 5. vsess bars: closing print and first bar

Closing print: **stays whole in the closing bar, no split and no carry.** Code: code/th_bars/kernels.py:10-31 k_cum, docstring "The closing trade belongs to the closing bar (no split)"; the print is added to the bar (line 25-26, `vol+=sz[i]` and `cum+=metric[i]`) and then the test `cum>=thr[i]` (line 28 in mode 0, **>=**) closes the bar with that print (line 29), cum is reset to 0.0 at the next bar open (line 21: `cum=0.0` when `not opn`). So the overshoot stays in the closing bar and the next bar starts at 0. Data check on the stored bars_c vsess_30 of 20261110: bar volumes 2,841 to 2,851 against thr 2,840.4, i.e. overshoot of 0.6 to 10.6 contracts, and the bar volumes plus the open remainder sum to the full session volume 64,484 (so nothing is dropped or carried). D8_PRINT_RULE.md section 1 point 3 says the same for the D8 rule ("a print is one event: it is added whole to the bar it falls into; the closing print stays in the bar"). The bars_c (_CANC) builder SCRIPT itself I could not find (searched code/ and the _d8spec directory; only the original k_cum kernel exists in the files I read), so for the run-merged version the statement rests on D8_PRINT_RULE.md plus the stored-bar check, not on a line of its code.
First bar: **starts at the first print of the session key, i.e. the first (run-merged) print with ET time >= 18:00:00.000, no other filter.** Code: session code 0 = ET minute-of-day >= 1080 (common.py:15, `code[m>=1080]=0`), td = ET+6 h; k_cum opens a bar at the first print of a new key/iid (lines 16-21: reset on key or iid change, then open). Data: td 20261110, engine tape first Asia rows: 23:00:00.000000000 UTC (one record) and then 23:00:00.001023825; stored bars_c vsess_30 first bar t0 = 23:00:00.001023825, known 23:31:18.884. The explanation consistent with D8_PRINT_RULE.md section 4 (_CANC: a merged print is stamped with the time the run is KNOWN complete = the next different print's timestamp) is that the first run (the 23:00:00.000 record) is stamped .001023825; its volume is inside bar 1 (volumes add to the session total). I could not verify that run by run from code (no builder script), so: the first bar contains the first run of the session; its t0 stamp is the run's known-complete time, not the first record's time. For pnf_7 (raw tape rows, no merge) t0 is the first record's own time (23:00:00.000 on 20261110, 20261112, 20261113).
Late first prints: the first record is usually 18:00:00.01x ET (table 1); D8_BAR_DEFS.md 3.2 (time_m section) notes exceptions on 2026-09-04 (10.6 ms late) and 2026-06-23 (2 h late); I did not re-check them.

## 6. What could not be verified
1. td 20261123 (not on disk yet) and the engine stores after 20261113 (engine never ran 20261116-20; the A columns are empty there).
2. Which of A (engine holes) or B (completed table) NT8 should use: not for me to decide; both given. They differ materially from 20261110 on (box 21 vs 23 on 20261110; 85,212 vs 86,371.5 median).
3. The NQ instrument name behind id 261401 (NQZ6 is inference).
4. The bars_c builder script (run-merged vsess_30 code), the first-bar timestamp rule in it, and the reason for the 13 ms timestamp offset between the engine tape and hist_replica.
5. TRADES block for 20261110 (month not landed).
6. The VWAP-line values of L9c2622b0 (taken from the engine store, not re-derived).

Files read or run: autopilot/DIRECTIVE_20261124_1356Z_ASIA_NEW_BOOKS_CODING_INPUTS.md; autopilot/D8_NYPM_VOLBOOK_INPUTS.md (style); autopilot/D8_PRINT_RULE.md; autopilot/D8_BAR_DEFS.md; autopilot/D8_PARITY_L9c2622b0_20261110.md; autopilot/D8_PARITY_L4aaacdb2_20261110.md; code/th_bars/{build_month,kernels,stats,common}.py; code/th_d8spec/{auto_members,parity_gen,parity_md,gen_book_blocks}.py; /mnt/l2/l2vast/_hist_replica/{days/2026/NQ_2026*.npz,coverage.csv}; /mnt/l2/l2vast/_d8spec/{runstats/*,spec_scales_2days.json,bars_c/vsess_30}; /mnt/l2/l2vast/_bars/{stats_day,stats_sess,pnf_7,trades}; /mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/.
