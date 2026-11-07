# T_REPLICA2_LABELS - label set of live TH-L2 decisions (LABELS agent, 2026-11-07, PRE-PROOF, nothing scored)
Files: /mnt/l2/l2vast/_replica2/labels.parquet (+ .csv), builder code/build_labels.py, frozen inputs live_frozen/ (all chmod a-w, MANIFEST.sha256). Seal: ds3_all_ea/manifest_after.json sha256 759f2258...965d2 before and after (unchanged).

## 0. Headline caveat (read first)
**There are NO live trade files for Feb-Sep 2026.** The earliest live row in data/live is 2026-10-04 (DualStrat). Live TH-L2 cuts exist only in DS6 (from 2026-10-29) and DS7 (blind week). So the directive's FIT set (Feb-Sep) is EMPTY: 0 rows. Every row is in the HOLDOUT split by the date rule (Oct 2026 + blind week). The only L2-cut labels: DS6 Oct 29-30 (17 CUT, 1 HELD) and the DS7 blind week (92 CUT, 13 HELD). Suggested fit/holdout substitute (CONV-ENGINE's call): FIT = DS6 Oct 29-30 (n=18) is too small; a within-DS7 chronological split (Sun-Tue fit / Wed-Thu hold, as DS3_THL2_LIVE_FIT did) is the only way to get a fit half. Column split_detail separates HOLDOUT_OCT (DS6 etc.) from HOLDOUT_BLINDWEEK. The NT8 file outputs/h2/NT8_DualStrat_trades_2026-02-07_to_10-14.csv (Feb-Oct) is account "Backtest" (NT8 Strategy Analyzer, 3,941 rows, Instrument NQ 12-26, no cut vocabulary besides _Target/_Stop...), NOT live; it is not a label source.

## 1. Inventory (rows = trade rows in file; exitName vocabulary after the strategy prefix)
| file | lineage | dates (entry) | rows | exit vocabulary | L2 cut? |
|--|--|--|--|--|--|
| StratTrades_DualStrat_<acct> | DualStrat (HM/ST/WT, D4-D5 era) | 2026-10-04..10-20 | 232 (4 with entry 0001-01-01) | LossExit 118, Stop 27, Target 81, ComboLock 5, SessionFlat | no (LossExit = price-path TH) |
| StratTrades_DualStrat2_<acct> | DualStrat2 | 10-20..10-26 | 82 (2 no entry) | LossExit, Stop, StopJoin(Fallback/Rejected), ComboLock, ProfitExit, Target | no |
| StratTrades_DualStrat_<sim-acct> / _<sim-acct> | DualStrat (sim accts) | 10-04..10-28 | 198 / 8 | LossExit, Stop, Target, ComboLock | no |
| StratTrades_DS3_<acct> / DS3_<sim-acct> | DS3 (KB/PB/SM/PE) | 10-26..10-30 | 31 / 45 | LossExit, Target, BookLock, StopJoin | no |
| StratTrades_DS4_Sim3 | DS4 | 10-27 | 5 | MV_LossExit, Target | no |
| StratTrades_DS5_<acct> | DS5 (K5/M5/N5/P5/S5/U5) | 10-27..10-28 | 52 | LossExit, StopJoin*, Target, BookLock | no |
| StratTrades_DS6_<acct> | D6 (A6/C6/H6/I6/K6/M6/P6/U6) | 10-28 18:06..10-30 | 113 | ThL2Cut 17, ThL2Trail 4, LossExit, Stop, Target, StopJoin, ComboLock, BookLock | yes, from 10-29 |
| StratTrades_DS7_<acct>_BLINDWEEK_reconstructed (sha 424c68da...7112; = the 11-05 22:05 synced bak) | D7 v1.4 | 11-01 18:36..11-05 11:04 | 187 | ThL2Cut 53, PolicyCut 39, PolicyTake, ThL2Trail, Stop, StopJoin*, BookLock, StackCut, Target | yes (DS7 ManageThL2) |
| K4Trades_<acct> / _<sim-acct> | K4 test log | 10-19..10-22 | 107 / 10 | not trade rows (et_time,kind,note; ENTRY/NOFILE) | no, unusable |
| outputs/h2/NT8_DualStrat_trades_2026-02-07_to_10-14.csv | NT8 backtest | 2026-02-08..10-14 | 3,941 | HM/ST_Target/Stop... | not live |
| nt8log_latest.txt | NT8 platform log 11-06 00:10.. | - | 68 ThL2Cut order lines (order events only, K7 1-lot, Nov 6, post blind week) | - | log not used for labels |
| nt8log_trace.20261021..23 | 10-21..23 | - | 0 ThL2/PolicyCut | - | - |
The unfrozen data/live/StratTrades_DS7_<acct>.csv was NOT read for labels (its extra rows are post-blind-week 11-05 11:04..11-06).

## 2. Cut-code lineage and parameters (quoted from data/live_code/DS7.cs header and GATE0_ANSWERS_1106.md)
* Price-path TH (exit "LossExit", NOT L2): DS6 v1.6a "TH loss-side on every book set to the HM lead L6_a30_r3_w10 (arm at 30 pts adverse, 3 of 3, 10-s windows) by user decision" (2026-10-29); code RequestBookExit(b,"LossExit") with "TradeHealth-LOSS TRIGGERED (cnt/3)". Earlier lineages (DualStrat, DS3-DS5) carry LossExit; these cannot be reproduced by pulled_mult.
* L2 cut v2.0: "DS6 v2.0 (2026-10-29): L2 TRADE HEALTH (group 06), user decision: the price-path TH rules ... are OFF (Mode=ReplacePath) and two order-book rules run instead ... loss side - a loser at -30, at a new adverse extreme, with >= 3x a normal level of its own-side support cancelled in 10 s -> cut. Measurements per the box's definitions; thresholds/actions = my reading, untested."
* v2.1 (2026-10-30): "Group 06 defaults set to the user's 10-30 settings (profit 30 / 2.0x / trail 30; loss -30 / 5 s / 30x)." DS7 defaults (L444): ThL2LossOn=true; ThL2LossMinPts=30; ThL2PulledSecs=5; ThL2PulledMult=30.0; ThL2WarmupSnapshots=300. The exact install time of v2.0 vs v2.1 on the chart is NOT documented; the 17 DS6 cuts (10-29 16:37 .. 10-30 10:37 ET) may be 3x/10 s (v2.0) or 30x/5 s (v2.1). Treat DS6 labels as parameter-uncertain; DS7 labels are the exact code (arm 30, pulled >= 30 x MedLevel, newMae 5 s, 60-pt stop; O7 40-pt stop = 20-pt arm via policy pct<=-0.50; policy line live from Mon 08:20 ET).
* DS7 cut mechanics (GATE0_ANSWERS_1106 sec 1-2): evaluated on each print, at most once/second/book, only if DepthLive (depth update within 120 s and >= 5 levels per side); unreal from the fill average EntryPx; PulledSupport = own-side cancelled (decrease net of traded at the price) over 5 s from per-print snapshots; MedLevel = EWMA 0.001 of top-5 mean level size seeded with the first snapshot; exit is a market order (log: Submitted->Filled in ~0.2 s).
* Policy line with exit name "PolicyCut" (pct<=-0.50 pulled_mult>=30 secs_ext<=5) is the same mechanics expressed relative to the stop distance; 39 of 92 DS7 cuts are PolicyCut. The X3/X4/X5 books' stop distance is not documented; arm 30 assumed (all 4 X cuts reached it).
* DS6 `l2_live` flag: exit time >= 2026-10-29 16:37:11 ET (first ThL2Cut exit; INFERRED start, not a documented install time). DS7 all True; other lineages False.

## 3. Definitions (labels table)
One row per trade with adverse excursion from the file's fill-average entryPx (lot-averaged) >= arm (30; 20 for O7) over [entry second, exit second], OR any CUT-type exit. Tape: owned NQ mbp-10 PRINTS (trade records, px in quarter points) from /mnt/l2/l2vast/_replica/data warm2_prints (09-01..10-12, ts_recv), warm_prints (10-12..10-30, ts_event) and blind_prints (11-01 23:00Z..11-05 16:05Z, ts_event); per-print resolution, last-print/worst-print adverse (not 1-s bars). Times: file times are NT8 local ET -> UTC with zoneinfo (DST ended 11-01 02:00; blind week EST, Oct EDT); epoch seconds (integer floor).
Columns: file, lineage, account, book, row_in_file, entryName, exitName, exit_kind, side, qty, entryTime_et, exitTime_et, entryPx, exitPx, entry_epoch, exit_epoch, date, month, arm, adv_extreme, adv_extreme_epoch, arm_epoch (first print epoch second at adverse >= arm), adv_at_exit, n_prints, tape, reached_arm, flag, l2_live, label, cut_reached_arm, split, split_detail.
label: CUT = exit_kind ThL2Cut or PolicyCut; HELD = reached arm and exited by anything else (Stop, Target, BookLock, StopJoin, ThL2Trail, PolicyTake, ...); PP_CUT = price-path LossExit (older lineages and DS6 before L2; a different mechanism, exclude from L2 scoring); NO_ENTRY_TIME = 6 rows with entry 0001-01-01 (no adverse computable). Use label in {CUT,HELD} with l2_live == True for scoring: 109 CUT + 14 HELD... (DS6 17+1, DS7 92+13 = 109 CUT, 14 HELD).

## 4. Counts (L2-live rows = scoring set)
| lineage | month | CUT | HELD | split |
|--|--|--|--|--|
| DS6 (10-29..10-30) | 2026-10 | 17 | 1 | HOLDOUT_OCT |
| DS7 blind week | 2026-11 | 92 (ThL2Cut 53, PolicyCut 39) | 13 | HOLDOUT_BLINDWEEK |
| FIT (Feb-Sep) | - | 0 | 0 | empty |
By book (CUT/HELD): DS6 A6 1/0, H6 1/0, K6 6/0, M6 2/0, P6 5/1, U6 2/0; DS7 A7 14/1, H7 2/0, K7 30/4, M7 13/3, O7 2/0, P7 24/4, U7 3/0, X3 2/0, X4 1/1, X5 1/0.
Non-L2 context (price-path era, not scoring): PP_CUT DualStrat 251, DualStrat2 28, DS3 45, DS4 4, DS5 33, DS6 45; HELD-without-L2 DualStrat 59, DualStrat2 31, DS3 5, DS5 5, DS6 4; 6 NO_ENTRY_TIME. Total table 639 rows.
Timing check: the cut exit second is a median 1 s (max 6 s) after the adverse-extreme second; median 5 s after the first print at arm (mean 177 s: cut waits for a pull). All 109 CUT rows reached their arm on the tape.

## 5. Raw mbp-10 coverage (NQ)
/mnt/l2/l2vast/raw/NQ/GLBX-20261013-Y3PCQ4MKV3: monthly files 2023-02-01..2026-10-11 (no Jan 2023); raw/NQ/ext/*: daily 2026-10-12..10-30 (10-17, 10-24 Saturdays absent; 10-18/25 Sunday sessions present); raw/NQ_blind: NQZ6 2026-11-01 23:00Z..11-05 16:30Z (tape ends 16:04:59Z = 11:04:59 ET); 2026-10-31 Saturday; 11-06 not on disk (NQ_sat_pull staged). Continuous NQ.v.0: front-month id changes at rolls (Dec-26 = Z6 from the Sep roll); all labelled trades are Z6 so no roll issue. Coverage flags: every table row had tape (flag empty except NO_ENTRY_TIME); first-print price within 60 pts of entryPx for all rows. The DS7 P7 trade entered 11:04:30 ET Thu is covered only 29 s. Note the tape used is prints only (no depth); pulled_mult needs the mbp-10 book for those dates (Oct 12-30 raw ext daily files and blind raw exist; Oct 4-12 are in the monthly file).

## 6. Caveats
Entry prices are lot-averaged (70/30 split with 30% add at 3 pts against, 2,000 ms slices), so the adverse reference moves after the add; the window starts at the file entryTime (minute-granular signal time for sliced books) not the per-slice fill times. exitTime has 1-s resolution; slice fills of the exit are averaged in exitPx. Older lineages' file entryTime for rows with 0001-01-01 is missing. Sessions without L2 cut code: all DualStrat, DS3, DS4, DS5, DS6 before 10-29 16:37 ET; DS6 live parameters (3x/10 s vs 30x/5 s) uncertain. Last-print adverse differs from NT8 "price" at the ~1-tick level; earlier work (DS3_THL2_LIVE_FIT) noted live cuts at -25..-29.5 on print measure for 4 trades; here 0 of 109 cuts fall short of the arm. HELD count here is 14 (13 in DS7; the earlier doc counted 12 on a different price measure).
