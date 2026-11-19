# STATUS_NOW (written 2026-11-19 12:45Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 12:40Z | box1: busy 100%, load1 88.12, workers 25, MemAvail 72 GB | server2: busy 100%, load1 109.25, workers 30, MemAvail 799 GB | pending box1-eligible 156099 / server2-eligible 158176 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 247.33, workers 89 (grid) + 101 (engine), 128 threads, MemAvail 1182 GB | serverB: busy 100%, load1 209.41, workers 89 (grid) + 98 (engine), 128 threads, MemAvail 1114 GB

## UTC TIME WRITTEN
2026-11-19 12:45Z

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
Server 1 (this box): MemAvail 85.7 GB; live reservations 34 (34 GB); workers 11, of which TP-adopted 11 (RSS 17.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 76.02, 84.98, 88.64
  by tag: ASI quota 16 running 4 hungry True RSS 7.7 GB PSS 5.9 GB; NYR quota 16 running 2 hungry True RSS 3.3 GB PSS 3.1 GB; LON quota 12 running 5 hungry True RSS 6.8 GB PSS 6.2 GB
  cell-months finished last hour (DONE markers): 3273
  top running jobs: TL3_LON_LA4_CT91p (x8);TL3_NYW_L542b562b_ADD (x4);TL3_LON_LA4_CT84p (x2);
Server 2 (rs4 metal): load / disk / tp_launch procs: 100.88, 103.68, 116.96|/dev/md2         28T  1.9T   27T   7% /mnt/l2|18|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_1014Z_Mode-bug-do-not-void-engine-winners.md 20261119_1105Z_Engine-rate-flat-fast-kinds-NT-stalled.md 20261119_1122Z_Engine-prior-year-red-definition.md 20261119_1156Z_Fake-fill-scan-layers-rate-G-SHORT.md 20261119_1233Z_Fast-share-dropped-calibration-cores.md
