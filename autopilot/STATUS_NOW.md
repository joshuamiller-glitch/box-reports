# STATUS_NOW (written 2026-11-19 19:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 19:30Z | box1: busy 100%, load1 106.32, workers 32, MemAvail 50 GB | server2: busy 100%, load1 143.47, workers 27, MemAvail 882 GB | pending box1-eligible 52202 / server2-eligible 58700 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 246.77, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 1074 GB | serverB: busy 100%, load1 218.06, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 949 GB

## UTC TIME WRITTEN
2026-11-19 19:30Z

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
Server 1 (this box): MemAvail 50.2 GB; live reservations 15 (15 GB); workers 32, of which TP-adopted 32 (RSS 49.6 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 108.78, 104.38, 98.40
  by tag: NYR quota 12 running 7 hungry True RSS 8.7 GB PSS 6.8 GB; ASI quota 14 running 6 hungry True RSS 10.6 GB PSS 8.4 GB; EXE quota 2 running 8 hungry False RSS 14.4 GB PSS 11.1 GB; NYL quota 5 running 6 hungry False RSS 8.5 GB PSS 6.4 GB; LON quota 12 running 5 hungry True RSS 7.5 GB PSS 5.4 GB
  cell-months finished last hour (DONE markers): 5592
  top running jobs: TL3_NYE_L21f079b6_RK7CT21p (x8);TL3_ASI_L548972b6_RA7CT56m (x8);TL3_NYE_L21f079b6_RK7CT14p (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 145.20, 144.70, 141.84|/dev/md2         28T  2.3T   26T   8% /mnt/l2|52|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_1750Z_Rate-dip-exit-families-base-lots.md 20261119_1806Z_Josh-best-books-on-own-merit-not-vs-D7.md 20261119_1823Z_STATUS-QUESTION-coverage-by-component.md 20261119_1850Z_PASS-2-plan-prepare-now-start-when-first-looks-finish.md 20261119_1917Z_cold-archive-move-yes.md
