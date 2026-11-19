# STATUS_NOW (written 2026-11-19 15:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 15:25Z | box1: busy 100%, load1 81.17, workers 30, MemAvail 57 GB | server2: unreachable | pending box1-eligible 65206 / server2-eligible 75662 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 255.72, workers 105 (grid) + 102 (engine), 128 threads, MemAvail 1159 GB | serverB: busy 100%, load1 240.99, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 942 GB

## UTC TIME WRITTEN
2026-11-19 15:30Z

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
Server 1 (this box): MemAvail 55.7 GB; live reservations 10 (10 GB); workers 33, of which TP-adopted 32 (RSS 53.8 GB) vs others 1 (RSS 0.9 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 82.59, 81.63, 81.56
  by tag: ASI quota 16 running 3 hungry True RSS 3.7 GB PSS 2.8 GB; NYL quota 36 running 16 hungry True RSS 28.7 GB PSS 21.7 GB; NYR quota 11 running 3 hungry True RSS 4.5 GB PSS 3.4 GB; LON quota 12 running 4 hungry True RSS 6.9 GB PSS 6.4 GB; TOOLS quota 0 running 6 hungry False RSS 10.1 GB PSS 8.1 GB; REST quota 0 running 1 hungry False RSS 0.9 GB PSS 0.7 GB
  cell-months finished last hour (DONE markers): 3260
  top running jobs: TL3_LON_LA1_RM7 (x8);TL3_NYL_L01811caaxP7_FR2 (x4);TL3_NYE_L01811caa_RH7CT21p (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 134.62, 135.76, 129.94|/dev/md2         28T  2.1T   26T   8% /mnt/l2|48|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_1407Z_Josh-REPLACE-ONLY.md 20261119_1410Z_Josh-combination-stage.md 20261119_1426Z_All-resources-to-the-ladders.md 20261119_1439Z_URGENT-Singapore-engine-zero.md 20261119_1457Z_Fleet-rate-halved-why.md
