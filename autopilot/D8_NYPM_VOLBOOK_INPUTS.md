# D8_NYPM_VOLBOOK_INPUTS: inputs for the D8 port of NY PM book L8e0bf58c (anch_PDN_B25 volume bars + ZN trigger)

Written 2026-11-23 by a relay sub-agent (not typed by Josh). Order: autopilot/DIRECTIVE_NYPM_VOLUME_INPUTS_20261123_1745Z.md. Information only: no new test, no gate or rule change, nothing live, no spend, no data deleted, no credentials. Compute: nice -n 10, read-only on engine files.

DATA END (read this first): the NQ book tape under /mnt/l2/l2vast/_bars/book/ is complete through td 20261111 (file 20261111.parquet, 07:00-20:59:59 UTC). td 20261112 is a 1-hour stub (07:00-07:59 UTC, 254,243 rows) and td 20261113 does not exist there. The activity table _bars/b2_act.parquet (built 2026-11-17 20:45Z) ends with that stub (td 20261112 session 1 only). The ZN 1-minute file /mnt/l2/l2vast/_alpha_breadth/ZN_1m.parquet ends 2026-11-10 07:59 UTC (last minute start). The NQ 1-minute store _bars/feat_d/nq1m.npz runs to 2026-11-13 21:59 UTC but has a hole (nothing for td 20261102 to 20261104 and half of 20261105). NEWEST DAY USED for item 1 (full engine pipeline): **20261111**. Rows for 20261112 and 20261113 are given in a separate small table with the volume taken from nq1m.npz (labelled), because their trade tape is not on disk. Item 2 uses the engine events file as it stands (events to td 202610/early 11, ZN to 2026-11-10 07:59Z). The catch-up ingest has not landed; nothing here uses it.

## 1. Daily table for the last 40 trading days (td 20260917 to 20261111)

Column rules (each checked against code):
- ny_rth_volume = sum of traded contracts of all trade records (action 84) with ET time of day 09:30:00 to 15:59:59.999 = W-BAR session codes 3 + 4, from the book tape: code/th_bars/b2_lib.py (activity_day: volume = sz.sum() per session; SESS 3 = 570-720 min, 4 = 720-960 min ET) written to _bars/b2_act.parquet by code/th_bars/b2_build.py (`act`). Continuous NQ.v.0 tape, no roll filtering beyond that.
- M = median of the 20 trading days BEFORE the td of that volume (min 10 days): code/th_bars/b2_anch.py span_vol() (`shift(1).rolling(20, min_periods=10).median()` on codes 3+4) and code/d8_spec4/rebuild_anch.py (same). Days are the rows present in b2_act (all weekdays with a tape; no day was skipped in this window).
- V = max(1, round(M / 25)) contracts (b2_anch.py: `V = max(1, int(round(v / k)))`, k = 25 = the B25 of anch_PDN_B25). Python round(), so a .5 case would go to even (none occurs in this table).
- previous_day_POC in points = ppoc ticks x 0.25, ppoc = the previous trading day's NY RTH volume-profile point of control (price tick with the largest volume, ties = lowest tick) from _bars/tpo_30m (b2_anch.py reads `ppoc`, group 1, last row of the day). Re-derived independently from the tape (volume per price tick 09:30-16:00 ET, lowest tick on ties) for the days 20261103, 20261106, 20261109, 20261110, 20261111: identical to the store in 5 of 5. The values for 20261102 (28,795.00), 20261103 (28,340.00) and 20261110 (27,940.00) are the same as in the parity pages.
- anchor_time_utc = timestamp of the first trade print at or through the previous POC after 09:30:00 ET (column a_t0 of the stored bars _bars/anch_PDN_B25/<yyyymm>.parquet; the first bucket opens with that print). NONE = no such print before 16:00 ET, so the day has no bars. Every NONE day in this window and every anchor time was re-derived with code/d8_spec4/rebuild_anch.py from the raw tape (run 2026-11-23, 40 days): the 17 anchored days gave identical bars to the store (known time, OHLC, volume: identical on all of them); the 23 NONE days gave "no print at/through the previous POC".
- Sanity check vs the parity pages: M for 20261102 = 453,627.0 / V 18,145; 20261103 = 456,883.5 / 18,275; 20261110 = 526,591.5 / 21,064 (pages: 453,627; 456,884; 526,592).

```csv
td,ny_rth_volume,M,V,previous_day_POC,anchor_time_utc
20260917,322294,351221.5,14049,29460.00,NONE
20260918,340044,347409.0,13896,29738.00,2026-09-18T14:02:22.006Z
20260921,396676,345259.0,13810,29730.00,NONE
20260922,346729,345259.0,13810,30805.00,2026-09-22T13:30:24.812Z
20260923,418759,345446.5,13818,30900.00,2026-09-23T13:45:51.647Z
20260924,481956,347596.5,13904,30740.00,2026-09-24T16:18:05.513Z
20260925,416282,347596.5,13904,30768.75,2026-09-25T13:32:42.781Z
20260928,498272,347596.5,13904,30912.00,NONE
20260929,430334,351221.5,14049,30638.00,2026-09-29T13:33:18.965Z
20260930,413278,351221.5,14049,30615.00,NONE
20261001,594818,369808.5,14792,30850.00,2026-10-01T13:33:36.623Z
20261002,409775,369808.5,14792,30634.25,NONE
20261005,319886,391157.0,15646,31060.00,2026-10-05T13:30:00.064Z
20261006,348459,391157.0,15646,31228.00,NONE
20261007,361068,391157.0,15646,31530.00,NONE
20261008,530490,391157.0,15646,31353.00,2026-10-08T14:28:40.163Z
20261009,332465,403225.5,16129,31235.00,NONE
20261012,308626,403225.5,16129,31080.00,NONE
20261013,360183,403225.5,16129,30890.00,NONE
20261014,542317,403225.5,16129,30770.00,NONE
20261015,545150,403225.5,16129,30163.50,2026-10-15T19:18:38.416Z
20261016,632861,411526.5,16461,29970.00,2026-10-16T13:31:29.346Z
20261019,438071,414780.0,16591,29400.00,NONE
20261020,491588,417520.5,16701,29780.00,2026-10-20T14:17:58.278Z
20261021,454472,424546.5,16982,29770.00,NONE
20261022,600062,434202.5,17368,30030.00,NONE
20261023,452782,434202.5,17368,29300.00,2026-10-23T14:51:28.094Z
20261026,459295,445426.5,17817,29150.00,NONE
20261027,400375,445426.5,17817,29480.00,NONE
20261028,435140,445426.5,17817,29790.00,2026-10-28T13:48:29.418Z
20261029,526842,445426.5,17817,29844.00,NONE
20261030,754744,445426.5,17817,29561.25,NONE
20261102,537108,453627.0,18145,28795.00,2026-11-02T15:17:12.475Z
20261103,416021,456883.5,18275,28340.00,2026-11-03T14:42:33.743Z
20261104,600952,456883.5,18275,28320.00,NONE
20261105,985628,475441.5,19018,28586.00,NONE
20261106,559237,475441.5,19018,26880.00,NONE
20261109,526341,509215.0,20369,27180.00,NONE
20261110,485546,526591.5,21064,27940.00,2026-11-10T14:55:34.572Z
20261111,442914,526591.5,21064,27800.00,NONE
```

Reading notes. (a) 20261105 volume 985,628 is the engine's value (NY AM 642,822 + NY PM 342,806 in b2_act); the NQ 1-minute store holds only half of that day, so it cannot confirm it; the book tape is the source. (b) 20261015 has an anchor at 19:18:38Z (15:18 ET) and therefore only 3 bars. (c) The newest tape day, 20261111, has no anchor (NONE).

### 1b. Rows for 20261112 and 20261113 (volume from the 1-minute store, NOT the tape)
No NQ tape for these days is on disk (see DATA END), so ny_rth_volume comes from _bars/feat_d/nq1m.npz (sum of minute volume with ET minute-of-day 570..959, ET date = column `ld`). This source was checked against the tape-based table: on the trading days 20261001 to 20261111 where both exist (all except 20261102 to 20261105) the difference is -1 to +30 contracts (typically 0 to 3; largest +30 on 20261008, +20 on 20261014, +7 on 20261109); the exception is 20261102 to 20261105, where the 1-minute store has a hole. Treat these two volumes as good to about 0.01%, not as the engine's number.

```csv
td,ny_rth_volume,M,V,previous_day_POC,anchor_time_utc
20261112,498254,508964.5,20359,28570.00,UNKNOWN_TAPE_NOT_ON_DISK
20261113,592283,494921.0,19797,UNKNOWN_TAPE_NOT_ON_DISK,UNKNOWN_TAPE_NOT_ON_DISK
```
M(20261112) uses the 20 tape days to 20261111; M(20261113) = median of the 20 days 20261016 to 20261112 including the 1-minute-derived 498,254. The previous POC for 20261112 = POC of the 20261111 tape = 114,280 ticks = 28,570.00 (computed here from book/20261111.parquet with the same rule as the store; the store itself has no row for 20261112). The previous POC for 20261113 needs the 20261112 tape (not on disk). Anchor times for these two days need the tape: not computable.

## 2. How much of the 1,861 events rests on the one-tick case
Method: code/d8_spec4/check4.py (trig_other, zseries, events_from) re-run on the stored anch_PDN_B25 bars and the ZN minute file; it reproduces all 1,861 engine events of /mnt/l2/l2vast/_brkt/ev/L8e0bf58c_R0_S8U.parquet (0 only-engine, 0 only-mine; same result as autopilot/D8_NYPM_NOTES.md section 2). |z| = the z at the signal bar (the bar where z first reaches the 1.0 threshold: z >= 1.0 on the UP edge, <= -1.0 on the DOWN edge). The z value used is the one read at the last completed ZN minute before the bar known time.

| cut | events | share of 1,861 |
|---|---|---|
| **|z| < 1.05** | **125** | 6.7% |
| **|z| < 1.10** | **280** | 15.0% |
| |z| < 1.01 | 26 | 1.4% |
| |z| < 1.02 | 34 | 1.8% |
| |z| < 1.20 | 772 | 41.5% |

Smallest |z| is 1.00004, largest 6.93. Long/short split of the 125: 60 long / 65 short; of the 280: 138 / 142.
One-tick share: the ZN minute return that triggers the event is a one-tick move (1/64 = 0.015625) in **1,461 of 1,861 events (78.5%)**; 2 ticks 309, 3 ticks 66, 4 ticks 13, 5+ ticks 12. All 125 events below 1.05 are one-tick moves, and 278 of the 280 below 1.10. Every event with a move of 2 ticks or more has |z| >= 1.0566. So the book as a whole rests on one-tick signals for 78.5%, but the part that is fragile to a 5% or 10% change of sigma is 6.7% or 15.0%.
Scale of sigma at these events: the sigma window holds a median 3,309 valid return minutes (125 low events: median 3,543); 406 events (21.8%) have fewer than 2,000. The parity-day window (n_obs 1,231, Monday after the DST change) is therefore on the thin side, where sigma is about 1.45e-4 and a one-tick move is z = 1.004 to 1.02; it is not typical of all 1,861 events.
Opposite direction (signals that would be created if sigma came out smaller): on NY PM bars with part 0 there are 165 bars with 0.95 <= |z| < 1.0 and 247 with 0.90 <= |z| < 1.0 (of 5,564 NY PM bars); some of them would become new edges. I did not count how many pass the edge test.
Test of the one concrete difference you named (which minutes exist): I rebuilt the ZN series with every empty minute inside an open Globex session (Sun 18:00 to Fri 17:00 ET minus the daily 17:00-18:00 break; holidays not removed) forward-filled with the previous close (so r1 = 0 on those minutes, as a bar series that creates bars for empty minutes would give), re-ran the same trigger and compared event sets: baseline 1,861; variant 1,952; common 1,856; only baseline 5; only variant 96. So filling empty minutes keeps 99.7% of the baseline events and adds 96 (5.2%). Script and numbers: scratchpad run 2026-11-23; code path = check4.minute_store / ret / events_from. This is an indicative test, not a re-run of the full engine (no fills, no P&L).

## 3. ZN "calendar front month" per day, 20261123 to 20261231, as matching OUR series
What our series is (not a calendar or expiry roll): Databento continuous symbol ZN.v.0 (volume-ranked front), schema ohlcv-1m, ts_event = minute start, instrument_id changes at the roll. Evidence: metadata of data/ext_20261110/ZN_ohlcv1m_20261110.dbn.zst = symbols ['ZN.v.0'], stype_in continuous, schema ohlcv-1m; request code code/th_fd/fd_buy_topup.py (`symbols=[sym + '.v.0']`); series description code/th_spec/build_specs.py YMFACTS (same loader for YM and ZN). The older part of ZN_1m.parquet (src ohlcv1m, 2013 to 2026-11-09) comes from the same loader; the parent-symbol download data/databento/ZN/ohlcv-1m_full.dbn.zst (symbols ZN.FUT) is the per-contract source of contract_of_day_ZN.csv and contract_minutes_ZN.parquet (up to 2026-10-13, last contract ZNZ6). I did NOT find the loader script for the 2013 to 2026-11-09 part of ZN_1m.parquet; that it is .v.0 too follows from the roll behaviour below and the shared description, not from a file I could read.
Last roll in the series: ZNU6 (instrument 42001136) to ZNZ6 (42001080), last old minute Fri 2026-08-28 16:59 ET, first new minute Sun 2026-08-30 18:00 ET (switch at 2026-08-29 00:00 UTC). Since then ZNZ6 only (66,409 rows 2026-08-30 to 2026-11-10; data/databento/ZN/contract_of_day_ZN.csv shows ZNZ6 on every day to 20261013).
Observed rule, from the 14 roll switches 2023-02 to 2026-08 (series ids in ZN_1m.parquet; per-contract UTC-day volumes in contract_minutes_ZN.parquet): the series switches at 00:00 UTC, in 11 of the 14 switches two UTC days after the first UTC day on which the next contract's volume exceeds the current one's (exceptions: 2023-02 and 2023-05 three days, 2024-02 one day; for 2025-08 the volume crossing could not be found because ZNU5/ZNZ5 volumes cross earlier in April 2025 data, so that case is not comparable). For the December-to-March roll the first-crossing UTC day was Tue 2023-11-28, Tue 2024-11-26, Tue 2025-11-25, and the switches happened at 00:00 UTC on 2023-11-30, 2024-11-28, 2025-11-27 (= Wed 19:00 ET each year). The crossing day equals "2 business days before the last business day of the month" in all six rolls I checked by hand (Nov 2023, 2024, 2025; Feb, May, Aug 2026).
Prediction for 2026: last business day of November = Mon 11-30; two business days before it (Thanksgiving closed) = Wed 11-25; switch expected at 00:00 UTC Fri 11-27 = **Thu 11-26 19:00 ET**, i.e. after the Thanksgiving NY PM window. **This is a prediction by the rule, not a measurement: ZNH7 volume is not on disk (ZN file ends 2026-11-10) and no catch-up data is here.** A one-day earlier switch (as 2024-02) would put the change at Tue 11-24 19:00 ET (Mar from 11-25); a later one (first-crossing on Fri 11-27) would put it at Sat 11-28 00:00 UTC = Sun 11-29 evening (Dec through 11-27).

What Josh types into NinjaTrader (contract in force for the NY PM window 12:00-16:00 ET on each day; the switch itself, whenever it falls, happens at a UTC midnight = 19:00 ET (winter), never inside NY PM):

```csv
td,contract_in_force_during_NY_PM_12:00-16:00_ET,confidence,note
20261123,ZNZ6 (NT: ZN 12-26),high,
20261124,ZNZ6 (NT: ZN 12-26),high,
20261125,ZNZ6 (NT: ZN 12-26),high,
20261126,ZNZ6 (NT: ZN 12-26),medium (switch expected 19:00 ET this evening, after NY PM),US Thanksgiving (CME holiday schedule, not read from a file)
20261127,ZNH7 (NT: ZN 03-27),medium (alt: ZNZ6 if the switch is Sun 11-29 evening),day after Thanksgiving, early close (not read from a file)
20261130,ZNH7 (NT: ZN 03-27),high,
20261201,ZNH7 (NT: ZN 03-27),high,
20261202,ZNH7 (NT: ZN 03-27),high,
20261203,ZNH7 (NT: ZN 03-27),high,
20261204,ZNH7 (NT: ZN 03-27),high,
20261207,ZNH7 (NT: ZN 03-27),high,
20261208,ZNH7 (NT: ZN 03-27),high,
20261209,ZNH7 (NT: ZN 03-27),high,
20261210,ZNH7 (NT: ZN 03-27),high,
20261211,ZNH7 (NT: ZN 03-27),high,
20261214,ZNH7 (NT: ZN 03-27),high,
20261215,ZNH7 (NT: ZN 03-27),high,
20261216,ZNH7 (NT: ZN 03-27),high,
20261217,ZNH7 (NT: ZN 03-27),high,
20261218,ZNH7 (NT: ZN 03-27),high,
20261221,ZNH7 (NT: ZN 03-27),high,
20261222,ZNH7 (NT: ZN 03-27),high,
20261223,ZNH7 (NT: ZN 03-27),high,
20261224,ZNH7 (NT: ZN 03-27),high,early close (not read from a file)
20261225,ZNH7 (NT: ZN 03-27),high,Christmas, CME closed (not read from a file)
20261228,ZNH7 (NT: ZN 03-27),high,
20261229,ZNH7 (NT: ZN 03-27),high,
20261230,ZNH7 (NT: ZN 03-27),high,
20261231,ZNH7 (NT: ZN 03-27),high,
```
Confidence column: "high" = every past December roll switched no earlier than 2025-11-27 00:00 UTC, so 11-23 to 11-25 are Dec in all historical analogues; the two medium days are 11-26 and 11-27 (see the alternatives above). From 11-30 on all analogues are March (ZNH7) until the March roll (the next roll after that is outside this request). ZNZ6 expires 2026-12-21 (standard CME rule; not read from a file here), long after the switch, so no December-contract expiry effect enters the series. Practical check for Josh: on Tue 11-24 and Wed 11-25 compare the traded volume of ZN 12-26 and ZN 03-27 per UTC day; the switch is two UTC days after the first day March exceeds December. What NinjaTrader's own "continuous contract" roll does I could not verify here; type the fixed contract by this table instead of relying on NT's roll setting. Effect of a mismatch day: the series blanks r1 at the roll minute (code/d8_spec4/check4.py ret(): NaN if the instrument id changes inside [k-1, k]); a wrong contract on a day only changes the minute returns by contract-specific moves (same tick 1/64).

## 4. NaN minutes and sigma_n_obs: confirmation
Confirmed, with the exact code:
- Minutes without a ZN trade are MISSING. ZN_1m.parquet has one row per minute that had at least one trade (volume column minimum 1, no zero-volume rows; Databento ohlcv-1m omits empty minutes). check4.minute_store() / the engine's fd_xm.dense() put the rows on a dense grid k = (ts - t0)/60 starting at the first NQ minute (2023-04-02 22:00 UTC) and the rest stay NaN (`cc = np.full(K, np.nan ...)`). Whole grid: 1,902,240 minutes, 1,189,582 with a close. In the NY PM window since 2026-08-01: 16,797 of 17,040 weekday minutes (98.6%) have a close, so the gaps are mostly overnight, weekend, holiday.
- r1 needs the minute AND the one before it: `ret(c, iid, K, 1)`: r[k] = c[k]/c[k-1] - 1, NaN if either close is NaN, NaN if the instrument id changed in [k-1, k] (ids forward-filled), first w minutes NaN. A minute with a trade whose previous minute is empty has NO r1: 61,277 such minutes on the grid (valid r1 = 1,128,302 vs 1,128,304 pairs with both closes; the 2 are roll blanks). 51.4% of the valid r1 values are exactly 0.
- sigma = `pd.Series(x).rolling(4320, min_periods=600).std().shift(1)`: sample std (ddof 1) over the last 4,320 GRID minutes (72 clock hours, not three trading days) ending one minute before the minute used; pandas skips NaN, so sigma_n_obs = the count of valid r1 in that window; fewer than 600 gives NaN, and z NaN is counted as 0 (no signal) by `np.nan_to_num(..., nan=0.0)` in trig_other().
- Reproduced for 20261102 at the minute used for the first NY PM bar (17:05:00 UTC): the window of 4,320 grid minutes holds 1,272 minutes with a close and **1,231 valid r1** = sigma_n_obs 1,231; sigma = 1.453023e-4, equal to the page value 0.000145302314 in D8_PARITY_L8e0bf58c_20261102.md. The window is short because it reaches back across the weekend closure (Fri 17:00 to Sun 18:00 ET = 49 of the 72 hours are closed), not because of a bug.
- What this means for NinjaTrader: use a ZN 1-minute series where an empty minute is NOT a bar, and compute r1 only when the previous bar's time is exactly 60 s earlier (time of bar k minus time of bar k-1 = 60 s); do not use Close[1] across a gap. Whether NT8 historical minute bars skip empty minutes, and how its time stamps align (NT stamps the bar END, Databento the START; the engine uses start + 60 s = known time), I could not verify from files here: it is on the list for the first ZN export from Josh. If NT created bars for empty minutes (flat carry), see the section 2 test (96 more events, 5 fewer).

## 5. What could not be verified
1. Rows 20261112 / 20261113 anchor times and the 20261113 POC (no tape).
2. The 2026-11 ZN roll day (prediction only, ZNH7 volume not on disk).
3. NinjaTrader's handling of empty ZN minutes and its roll setting.
4. The loader script of the older ZN_1m.parquet (inferred .v.0).
5. The catch-up ingest: not used.
6. Holiday and early-close notes in the calendar table are from general CME knowledge, not read from a file.

Files read or run: autopilot/DIRECTIVE_NYPM_VOLUME_INPUTS_20261123_1745Z.md; autopilot/D8_NYPM_NOTES.md; autopilot/D8_BUILD_SPEC.md (AUTO:BOOK:L8e0bf58c); code/d8_spec4/check4.py, rebuild_anch.py; code/th_bars/b2_anch.py, b2_lib.py, b2_build.py; code/th_spec/build_specs.py; code/th_fd/fd_buy_topup.py; /mnt/l2/l2vast/_bars/{b2_act.parquet,tpo_30m,anch_PDN_B25,book,feat_d/nq1m.npz}; /mnt/l2/l2vast/_brkt/ev/L8e0bf58c_R0_S8U.parquet; /mnt/l2/l2vast/_alpha_breadth/ZN_1m.parquet; data/databento/ZN/*; data/ext_20261110/ZN_ohlcv1m_20261110.dbn.zst.
