# STATUS_NOW (written 2026-11-19 20:45Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 20:45Z | box1: busy 100%, load1 70.41, workers 32, MemAvail 49 GB | server2: busy 100%, load1 152.46, workers 27, MemAvail 800 GB | pending box1-eligible 47424 / server2-eligible 53963 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 223.80, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 1093 GB | serverB: busy 100%, load1 216.39, workers 105 (grid) + 97 (engine), 128 threads, MemAvail 1018 GB | serverC: busy 88%, load1 112.44, workers 1 (grid) + 111 (engine), 128 threads, MemAvail 1366 GB

## UTC TIME WRITTEN
2026-11-19 20:45Z

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
Server 1 (this box): MemAvail 48.3 GB; live reservations 11 (11 GB); workers 32, of which TP-adopted 32 (RSS 47.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 70.41, 74.45, 77.57
  by tag: NYR quota 12 running 11 hungry True RSS 16.5 GB PSS 13.8 GB; ASI quota 14 running 3 hungry True RSS 4.5 GB PSS 3.7 GB; EXE quota 2 running 8 hungry False RSS 13.3 GB PSS 10.8 GB; NYL quota 5 running 5 hungry False RSS 6.1 GB PSS 4.7 GB; LON quota 12 running 5 hungry True RSS 7.3 GB PSS 5.7 GB
  cell-months finished last hour (DONE markers): 6191
  top running jobs: TL3_NYE_L59b66d32_RK7CT7p (x8);TL3_NYE_L59b66d32_RK7CT14p (x6);TL3_NYE_L4560e541_RK7 (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 147.16, 151.44, 147.10|/dev/md2         28T  2.3T   26T   9% /mnt/l2|52|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_1823Z_STATUS-QUESTION-coverage-by-component.md 20261119_1850Z_PASS-2-plan-prepare-now-start-when-first-looks-finish.md 20261119_1917Z_cold-archive-move-yes.md 20261119_1933Z_fast-share-stack-kinds.md 20261119_2025Z_stale-exit-results-and-three-checks.md
