# D8_SCALE_ROWS_LATEST: engine-rule s_vol / s_n / s_rng for td 20261117 to 20261126, and the London session-volume median for td 20261126

Written 2026-11-26 ~14:50Z by W-NYAMSPEC2 (relay sub-agent, not typed by Josh). Order: LEAD message 2026-11-26 ~14:25Z, copy of autopilot/DIRECTIVE_20261126_1420Z_SCALE_ROWS_LIVE_CHECK.md. Information only: no engine run, nothing queued, nothing edited, nothing live, no spend. nice -n 10.

## 0. ONE-LINE ANSWERS
1. The engine rule gives s_rng about 4.2 to 4.5 for td 20261126 (4.156 with the as-stored rows plus the new days, 4.536 with the holes filled; 4.29 / 4.69 if the partial 20261125 row is counted), NOT near 3 and NOT near 6.9. The engine on the stored table as it stands would still give the td 20261113 row (s_rng 3.216, s_vol 1.117, s_n 1.382) because the store ends 20261113 and the code clamps to the last row. Today's live s_rng of about 6.9 is 1.5 to 1.7 times the engine rule (6.9 / 4.536 = 1.52; 6.9 / 4.156 = 1.66), and 2.3 times the last stored 3.048 of 20261110.
2. s_vol: engine 1.31 to 1.42, live 1.52-1.55 (live 1.1 to 1.2 times higher). s_n: engine 1.64 to 1.80, live 2.56 (live 1.4 to 1.6 times higher).
3. Why (measured, not proved): the engine takes the median of the last 20 stats rows; if the same rows are medianed over the last 8 rows only (20261113 to 20261124) the engine's own definitions give s_vol 1.536 (matches the live 1.52-1.55), s_n 2.00 (live 2.56: not matched), s_rng 5.41 (live 6.9: not matched). So the 8-day window explains the s_vol and about two thirds of the s_rng gap; the rest of s_rng (and s_n) must come from how the live file measures the daily range / print count (not verifiable from here: I do not have the live file or its inputs; the engine's daily range is the stats.py piece rule, section 2, which is smaller than the true high-low of a trading date).
4. London session-volume median for td 20261126, engine rule: **A (engine store as stored, clamped to td 20261113) 69,734 contracts -> volume bar 348.67; Bp (store rows + appended days) 77,924 -> 389.62; B (hole-filled) 76,926.5 -> 384.63**. The live file's 171.0 (= median 34,200 / 200) is about 0.44 to 0.49 of any of them: the live London median is less than half of the engine's. 
5. td 20261126 is today and has no rows on the box (raw files end 20261125 17:30Z); the engine scale for td 20261126 only uses rows BEFORE it, so the missing day does not matter; what matters is that td 20261125 is PARTIAL on the box (see section 1).

## 1. What data exists on the box (checked, not assumed)
- engine stats store `/mnt/l2/l2vast/_bars/stats_day.parquet`, `stats_sess.parquet`: 20230403 to 20261113, with no rows for 20261102-20261104 and a HALF day for 20261105 (571,100 contracts against 1,241,173 in hist_replica). No row after 20261113. These are the "as stored" rows.
- hist_replica day files `/mnt/l2/l2vast/_hist_replica/days/2026/NQ_<td>.npz` and coverage.csv: complete through td 20261124 (coverage_summary: last 20261124, written 2026-11-26 01:41Z). Its n_prints and contracts equal the engine store on 50 of the 51 days of 20260901-20261113 (the exception is the half day 20261105). BUT the 20261123 file (built 2026-11-24 18:33Z) is SHORT in NY PM: 860,340 prints / 1,069,596 contracts against 887,739 / 1,103,065 in the raw files now (NY PM volume 290,015 vs 323,490). I used the raw rebuild for 20261123 and 20261124 (20261124 equals the hist_replica file exactly: 760,929 prints, 932,114 contracts).
- raw mbp-10 files `/mnt/l2/l2vast/raw/NQ_mbp10_extra/NQ_mbp10_<UTC range>.dbn.zst` (the 01:30Z top-up): td 20261123 and 20261124 COMPLETE. **td 20261125 is INCOMPLETE: the file NQ_mbp10_20261125T13_20261125T17.dbn.zst is truncated (the reader warns "DBN file is truncated or contains an incomplete record") and ends at 2026-11-25 14:40:27Z (09:40 ET); the file NQ_mbp10_20261125T17_20261125T17.dbn.zst covers only 17:00:00-17:30:03Z; nothing from 14:40 to 17:00Z and nothing after 17:30Z (to 22:00Z).** Rebuilt row for 20261125 from what exists: 305,088 prints, 372,768 contracts, range 1,082.75 pts (a lower bound); Asia and London are complete, NY AM only 13:30-14:40Z, NY PM only 17:00-17:30Z (volume by session code 0-4: 96,962 / 98,920 / 37,922 / 52,345 / 86,619). No file for td 20261126 exists.
- Handling of the partial days: the engine scale for a td uses only rows strictly before it (build_month.py line 20: `w=x[max(0,i-20):i]`), so td 20261126's own partial day is never used; the partial 20261125 row only affects td 20261126. Both ways are given: excluded (X) and included as it stands (P). Which is right for the live NT8 is the relay's / LEAD's call.

## 2. The exact rule and where it is in the code
- Daily stats rows `outputs/code/th_bars/stats.py` lines 6-20: per trade-table file (UTC day) and per (td, instrument id): vol = sum of `sz` of every trade record, n = number of trade records ("prints" = rows, no merge), hi / lo = max / min price; td (common.py lines 10-17: trading date = ET + 6 h); line 17 sums vol, n per td; **line 18: rng of a td = the MAX over its (file, instrument) pieces of (hi - lo) / 4 points** (a td spans two UTC day files, so the stored range is the larger of the two pieces, not the high-low of the whole trading date: e.g. 20261019 stored 414.75 vs true 757.5).
- Scale rows `outputs/code/th_bars/build_month.py` scales() lines 13-32: for each column in (vol, n, dol, rng, rv): r0 = median of the first 60 rows (line 18; r0_vol = 610,702, r0_n = 373,169, r0_rng = 191.5 pts, re-computed from the store today and equal); tr[i] = median of the previous up to 20 ROWS (not calendar days; rows before row i, line 20-21), values > 0 only, at least 5 values else r0; s = tr / r0 (line 22). Lookup per print `build_month.py` line 71: `ix = searchsorted(sc['td'], td); ix = minimum(ix, len(sc['td']) - 1)`: **a td after the last stored row gets the LAST stored row (20261113)**.
- Variants below. A = the engine function on the store as it is (so for every td after 20261113 it returns the 20261113 row). Bp = the same function on the store rows PLUS the appended new days (20261116-20 from hist_replica, 20261123-24 from the raw files), holes and the half day left as they are: what a re-run of stats.py on the extended trade store would give. B = Bp with the holes 20261102-04 added and 20261105 replaced by the full day (from hist_replica): a formula result, NOT something the engine ran.

## 3. Scale rows td 20261117 to 20261126 (all numbers recomputed with the engine's own definitions; s = median of the previous 20 rows / r0)
Columns: A_* = engine store clamped; Bp_*, B_* as defined above (20261125 excluded from the window; for td 20261126 see the variant table below); abs_rng = the median daily range in points used.
```csv
td,A_s_vol,A_s_n,A_s_rng,Bp_s_vol,Bp_s_n,Bp_s_rng,Bp_abs_rng,B_s_vol,B_s_n,B_s_rng,B_abs_rng
20261117,1.117061,1.382269,3.216057,1.140864,1.447415,3.383812,648.000000,1.184654,1.466494,3.750653,718.250000
20261118,1.117061,1.382269,3.216057,1.140864,1.447415,3.750653,718.250000,1.245906,1.537092,4.095300,784.250000
20261119,1.117061,1.382269,3.216057,1.140864,1.447415,3.383812,648.000000,1.290784,1.601510,4.095300,784.250000
20261120,1.117061,1.382269,3.216057,1.220132,1.537092,3.750653,718.250000,1.290784,1.601510,4.095300,784.250000
20261123,1.117061,1.382269,3.216057,1.290784,1.601510,4.091384,783.500000,1.307952,1.642604,4.159922,796.625000
20261124,1.117061,1.382269,3.216057,1.307952,1.619765,4.156005,795.875000,1.352812,1.741782,4.290470,821.625000
20261125,1.117061,1.382269,3.216057,1.307952,1.642604,4.156005,795.875000,1.415310,1.804090,4.535901,868.625000
20261126,1.117061,1.382269,3.216057,1.307952,1.642604,4.156005,795.875000,1.415310,1.804090,4.535901,868.625000
```
td 20261126 with the 20261125 row excluded (X) or partial (P):
```csv
variant,s_vol,s_n,s_rng,median_range_pts,median_volume,median_prints
A engine store as stored (clamps to the 20261113 row),1.117061,1.382269,3.216057,615.875,,
Bp store rows + appended days 1116-1124 (1125 excluded; holes and the 1105 half day stay),1.307952,1.642604,4.156005,795.875,798769,612969
BpP same with the PARTIAL 20261125 row included,1.307952,1.642604,4.290470,821.625,798769,612969
B hole-filled (1102-04 added, 1105 full; 1125 excluded),1.415310,1.804090,4.535901,868.625,864332,673230
BP hole-filled with the PARTIAL 20261125 row,1.415310,1.804090,4.689295,898.000,864332,673230
```
Daily rows used (td, volume contracts, prints n, range points). B_* = the hole-filled table that feeds column B; A_*_store = what the engine store has for that day (blank = no row):
```csv
td,B_volume,B_prints_n,B_range_pts,B_source,A_volume_store,A_prints_n_store,A_range_pts_store
20261014,731443,522418,813.50,store,731443,522418,813.50
20261015,803455,601731,574.25,store,803455,601731,574.25
20261016,797048,575874,956.25,store,797048,575874,956.25
20261019,618718,445811,414.75,store,618718,445811,414.75
20261020,685726,509222,511.75,store,685726,509222,511.75
20261021,654002,485269,385.50,store,654002,485269,385.50
20261022,822195,611033,821.50,store,822195,611033,821.50
20261023,671788,506452,339.00,store,671788,506452,339.00
20261026,671473,493917,547.75,store,671473,493917,547.75
20261027,580311,420791,593.25,store,580311,420791,593.25
20261028,599843,457965,503.75,store,599843,457965,503.75
20261029,794025,597409,657.50,store,794025,597409,657.50
20261030,1022406,743727,898.25,store,1022406,743727,898.25
20261102,739211,544719,789.50,hist_replica,,,
20261103,642948,473166,411.25,hist_replica,,,
20261104,980160,753324,1353.25,hist_replica,,,
20261105,1241173,961135,2007.50,hist_replica,571100,431538,788.00
20261106,848817,674582,803.75,store,848817,674582,803.75
20261109,782544,597859,1378.00,store,782544,597859,1378.00
20261110,678657,530480,593.00,store,678657,530480,593.00
20261111,636496,470866,779.00,store,636496,470866,779.00
20261112,707730,549781,638.50,store,707730,549781,638.50
20261113,803513,628079,897.75,store,803513,628079,897.75
20261116,879848,671879,1032.75,hist_replica,,,
20261117,943647,731253,839.50,hist_replica,,,
20261118,910186,733369,563.50,hist_replica,,,
20261119,987685,786567,1402.00,hist_replica,,,
20261120,1358468,1121688,1596.25,hist_replica,,,
20261123,1103065,887739,1526.25,raw dbn (hist_replica day file is short in NY PM: 860,340 prints),,,
20261124,932114,760929,1038.00,raw dbn = hist_replica,,,
20261125,372768,305088,1082.75,PARTIAL raw dbn (to 14:40Z + 17:00-17:30Z),,,
```
The 20 rows used for B at td 20261126 are the rows 20261028 ... 20261124 of that table (20 rows: 1028, 1029, 1030, 1102, 1103, 1104, 1105, 1106, 1109, 1110, 1111, 1112, 1113, 1116, 1117, 1118, 1119, 1120, 1123, 1124): median volume 864,332.5, prints 673,230.5, range 868.625 pts -> s_vol 1.4153, s_n 1.8041, s_rng 4.5359.

## 4. Comparison with the live values (build v39 start-up, 14:10Z)
| quantity | live (8 rows) | engine, store + new days (Bp) | engine, hole-filled (B) | engine stored (A, clamped) | last stored 20261110 |
|---|---|---|---|---|---|
| s_rng | about 6.9 | 4.156 | 4.536 | 3.216 | 3.048 |
| s_vol | 1.52-1.55 | 1.308 | 1.415 | 1.117 | 1.111 |
| s_n | 2.56 | 1.643 | 1.804 | 1.382 | 1.668 |
Test of the 8-day hypothesis (engine definitions, last 8 rows 20261113-20261124): median range 1,035.4 pts (piece rule) or 1,041.3 pts (true full-td high-low): s_rng 5.41 / 5.44; median volume 937,880 -> s_vol 1.536; median prints 747,149 -> s_n 2.002. Live 6.9 x 191.5 = 1,321 pts and 2.56 x 373,169 = 955,000 prints would be needed to give the live numbers with the same r0 constants: the live file's s_rng and s_n are therefore not an 8-row median of the engine's definitions; they may use another daily-range / print-count definition or other r0 constants (not verifiable here: no access to the live file).
The 20-row window in the engine today still contains the large days of 20261104, 20261105 (hole-filled) and 20261119-20261123 (ranges 1,402 / 1,596 / 1,526 pts), so the engine's own s_rng has risen from 3.05 (20261110) to about 4.2-4.5.

## 5. Books touched by a too-large s_rng / s_vol / s_n (from the spec pages; "engine scale" = bar size or threshold scales with it)
- s_rng scaled bars and boxes (every brick, box or threshold grows with s_rng; the brackets that use u = trailing median bar range grow too): NY AM: L43f0cbfb pnf_14 (box = max(2, round(14 x s_rng))), Lf0346d55 renko_20, Lca8ca9cb renko_14 (plus its own asym 10u/20u bracket from the brick height), L7cc56d99 lbrk_3_40 (box = max(2, round(40 x s_rng))), Le4fede95 swing_atr_0.4 and L8cfda948 dchg_40 (swing theta from the trailing median daily range: abs_rng, the same stats row), brackets S8U on L43f0cbfb and Bf428c4a1 (u = trailing median bar range); Asia: L9c2622b0 pnf_7, L6b373671 frenko_40; London: L12842dde rng_20 (box = max(1, round(20 x s_rng))), L19201dfc trend_20, Lc78f2492 renko_20; NY PM: L8e0bf58c S8U bracket (u rule). Example: live s_rng 6.9 gives the range-bar box 138 ticks and pnf_7 box 48 ticks (the relay's numbers), the engine today would give 20 x 4.536 = 91 ticks and 7 x 4.536 = 32 ticks (Bp: 83 and 29).
- s_vol scaled: Bf428c4a1 vol_1700, Asia L385f4f2e vol_2600 (and any dlt_ row).
- s_n scaled: B7bfd33b7 dib_6000 (threshold T0 = max(10, 6000 x s_n) prints), Asia L92a90948 tick_5000 (5000 x s_n).
- Session-volume medians (a different table, section 6): L39287638 vsess_50 (NY AM), L6d238076 vsess_50 (NY PM), Asia L4aaacdb2 vsess_30, London L74274eca vsess_200; L8e0bf58c (anch_PDN_B25) uses its own NY RTH volume median / 25.
- NOT touched by s_* : the time bars (L4407508c time_m_3, L64390867 time_m_20, Asia time_m_1 / tm bars, NY PM tm bars L2c6916a5 / L4bdd521a / L52359bf4 / L8dff280f), the trigger constants themselves (they are in bars or points), the fixed brackets (F/P shapes).
- This list is from the spec pages and D8_BUILD_SPEC.md bar rows; which of them are in the current live file (v39) is the relay's knowledge, not checked here.

## 6. London session-volume median for td 20261126 (and the 45-day table)
Rule (build_month.py lines 23-31 and the vsess line `np.maximum(svol/p,1.0)`, p = 200 for vsess_200): sess_vol[1][td] = median of the previous up to 20 London (session code 1, 02:00-08:30 ET) volumes of the stats rows, values > 0, >= 5 needed; thr = max(median / 200, 1.0) contracts. Engine values for td 20261126: A 69,734 -> 348.67 (the same number as td 20261110: the store clamps); Bp 77,924 -> 389.62; B 76,926.5 -> 384.63. The live file's 171.0 corresponds to a median of 34,200.
London volume per td and the three medians (A = engine store, clamped after 20261113; Bp = store rows + new days; B = hole-filled; London of 20261125 is complete in the raw files):
```csv
td,london_volume_contracts,london_source,A_median20_engine_store,A_thr200,Bp_median20_store_plus_new_rows,Bp_thr200,B_median20_hole_filled,B_thr200
20260925,44096,engine store,48377.5,241.89,48377.5,241.89,48377.5,241.89
20260928,66486,engine store,48377.5,241.89,48377.5,241.89,48377.5,241.89
20260929,53093,engine store,52022.5,260.11,52022.5,260.11,52022.5,260.11
20260930,53100,engine store,51746.5,258.73,51746.5,258.73,51746.5,258.73
20261001,97195,engine store,51746.5,258.73,51746.5,258.73,51746.5,258.73
20261002,58094,engine store,51746.5,258.73,51746.5,258.73,51746.5,258.73
20261005,55167,engine store,53096.5,265.48,53096.5,265.48,53096.5,265.48
20261006,50176,engine store,54133.5,270.67,54133.5,270.67,54133.5,270.67
20261007,69013,engine store,53096.5,265.48,53096.5,265.48,53096.5,265.48
20261008,70894,engine store,53096.5,265.48,53096.5,265.48,53096.5,265.48
20261009,57876,engine store,54133.5,270.67,54133.5,270.67,54133.5,270.67
20261012,49911,engine store,55510.5,277.55,55510.5,277.55,55510.5,277.55
20261013,52746,engine store,55510.5,277.55,55510.5,277.55,55510.5,277.55
20261014,52548,engine store,55510.5,277.55,55510.5,277.55,55510.5,277.55
20261015,89166,engine store,55510.5,277.55,55510.5,277.55,55510.5,277.55
20261016,52420,engine store,56521.5,282.61,56521.5,282.61,56521.5,282.61
20261019,69734,engine store,54133.5,270.67,54133.5,270.67,54133.5,270.67
20261020,68409,engine store,56521.5,282.61,56521.5,282.61,56521.5,282.61
20261021,69018,engine store,56521.5,282.61,56521.5,282.61,56521.5,282.61
20261022,79730,engine store,57985,289.93,57985,289.93,57985,289.93
20261023,83412,engine store,57985,289.93,57985,289.93,57985,289.93
20261026,80557,engine store,62290,311.45,62290,311.45,62290,311.45
20261027,73179,engine store,63251.5,316.26,63251.5,316.26,63251.5,316.26
20261028,52269,engine store,68711,343.56,68711,343.56,68711,343.56
20261029,69679,engine store,68711,343.56,68711,343.56,68711,343.56
20261030,92783,engine store,68711,343.56,68711,343.56,68711,343.56
20261102,61587,hist_replica,69015.5,345.08,69015.5,345.08,69015.5,345.08
20261103,72494,hist_replica,69015.5,345.08,69015.5,345.08,69015.5,345.08
20261104,135438,hist_replica,69015.5,345.08,69015.5,345.08,69348.5,346.74
20261105,72572,hist_replica,69015.5,345.08,69015.5,345.08,69706.5,348.53
20261106,92230,engine store,69018,345.09,69018,345.09,69706.5,348.53
20261109,98361,engine store,69679,348.39,69679,348.39,71114,355.57
20261110,58282,engine store,69734,348.67,69734,348.67,72533,362.67
20261111,75898,engine store,69679,348.39,69679,348.39,72533,362.67
20261112,62149,engine store,69734,348.67,69734,348.67,72875.5,364.38
20261113,57963,engine store,69734,348.67,69734,348.67,72533,362.67
20261116,77924,hist_replica,69734,348.67,69734,348.67,72533,362.67
20261117,75929,hist_replica,69734,348.67,73179,365.89,72875.5,364.38
20261118,82850,hist_replica,69734,348.67,73179,365.89,74538.5,372.69
20261119,67902,hist_replica,69734,348.67,75898,379.49,75913.5,379.57
20261120,99622,hist_replica,69734,348.67,75898,379.49,74538.5,372.69
20261123,97516,raw dbn,69734,348.67,75929,379.64,74538.5,372.69
20261124,111482,raw dbn,69734,348.67,77924,389.62,74538.5,372.69
20261125,98920,raw dbn partial day (London complete),69734,348.67,77924,389.62,75913.5,379.57
20261126,,not yet,69734,348.67,77924,389.62,76926.5,384.63
```
Source of the London volumes: engine store (stats_sess code 1) up to 20261113, hist_replica day files for 20261116-20 (and the holes), raw mbp-10 dbn for 20261123-25 (20261123 London equals the hist_replica value).

## 7. Open / not verified
1. The live file's own scale inputs (which days, which range and print definitions, which r0) were not available to me; section 4 is a consistency check, not an explanation.
2. td 20261125 is partial on the box (section 1): the 14:40-17:00Z and 17:30-22:00Z gap needs a fresh pull; until then td 20261126 values carry the partial / excluded choice (Bp vs BpP: s_rng 4.156 vs 4.290; B vs BP: 4.536 vs 4.689).
3. hist_replica 20261123 is short in NY PM (see section 1); the raw rebuild was used; the engine store never ran these days.
4. Stored versus hole-filled remains a LEAD / relay decision (A is what the engine would literally return today; it is stale, 11 trading days old).

Files read or run: autopilot/DIRECTIVE_20261126_1420Z_SCALE_ROWS_LIVE_CHECK.md; code th_bars/{stats,build_month,common}.py; stores _bars/stats_day.parquet, stats_sess.parquet, _hist_replica/coverage.csv and days/2026/*.npz, raw/NQ_mbp10_extra/*.dbn.zst (read with the databento reader, action T only).
