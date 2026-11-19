# STATUS_NOW (written 2026-11-19 13:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 13:00Z | box1: busy 100%, load1 78.18, workers 33, MemAvail 70 GB | server2: busy 100%, load1 105.65, workers 26, MemAvail 1012 GB | pending box1-eligible 156420 / server2-eligible 157918 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 245.80, workers 89 (grid) + 101 (engine), 128 threads, MemAvail 1206 GB | serverB: busy 100%, load1 213.78, workers 89 (grid) + 99 (engine), 128 threads, MemAvail 1143 GB

## UTC TIME WRITTEN
2026-11-19 13:00Z

## NEEDS HELP
- Server 2: identity PASSED; first real jobs finished 18:48Z (T-REBUILD stage 0 raw books, K7 202610 92 s); ramp to knee running (cap 16 now); copy ~150/305 GB.
- Per-second MBO tables for 2026-11-01..11-05 are missing (W-CF2 checking raw files / quote only).

## NEEDS THE USER
- DS7.cs LINE 1790 BUG (v2.0): persist counter cleared on every winning second: the K7/U7/M7 book-reading profit lines (persist >= 2) can never fire live. You said keep them inert until the engine says whether firing helps: the 21:00Z page gives both worlds. (One-line fix in autopilot/DS7_PROFIT_LINES_SPEC.md.)
- JL2 does NOT model the persist=1 profit lines that DO fire live: size (replay): mean -3%, whole-stack max DD -74.4k -> -79.6k (L6M -22.6k -> -29.5k); P7 hit most. So live is ~5k DD worse than JL2 from these lines: engine build JL3 queued (W-EV).

## PASSED SINCE LAST FILE
- none (no candidate has beaten all its persistent-draw controls yet)

## FAILED / WITHDRAWN SINCE LAST FILE
- London range skip (LS1/LS125): no HOLD DD cut at any k; old random controls invalid; Off/Shadow.
- Profit lines K7 lock / U7 tighten / M7 step: 43-month replay net negative and dead live by the line 1790 bug.

## EACH SERVER
Server 1 (this box): MemAvail 69.3 GB; live reservations 7 (7 GB); workers 33, of which TP-adopted 33 (RSS 46.1 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 78.18, 70.95, 75.62
  by tag: ASI quota 16 running 6 hungry True RSS 7.3 GB PSS 6.3 GB; NYL quota 36 running 13 hungry True RSS 19.5 GB PSS 13.2 GB; NYR quota 16 running 9 hungry True RSS 11.9 GB PSS 10.5 GB; LON quota 12 running 5 hungry True RSS 7.4 GB PSS 6.1 GB
  cell-months finished last hour (DONE markers): 3340
  top running jobs: TL3_NYW_L542b562b_ADD (x18);TL3_LON_LA4_CT105m (x10);TL3_ASI_Mdcdb0b6e_RA7 (x8);
Server 2 (rs4 metal): load / disk / tp_launch procs: 103.97, 100.28, 105.83|/dev/md2         28T  2.0T   27T   7% /mnt/l2|54|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_1014Z_Mode-bug-do-not-void-engine-winners.md 20261119_1105Z_Engine-rate-flat-fast-kinds-NT-stalled.md 20261119_1122Z_Engine-prior-year-red-definition.md 20261119_1156Z_Fake-fill-scan-layers-rate-G-SHORT.md 20261119_1233Z_Fast-share-dropped-calibration-cores.md
