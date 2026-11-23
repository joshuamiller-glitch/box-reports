# STATUS_NOW (written 2026-11-23 07:45Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-23 07:45Z | box1: busy 100%, load1 69.39, workers 21, MemAvail 75 GB | server2: busy 96%, load1 86.61, workers 27, MemAvail 747 GB | pending box1-eligible 951510 / server2-eligible 135859 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 184.57, workers 105 (grid) + 99 (engine), 128 threads, MemAvail 1010 GB | serverB: busy 100%, load1 188.71, workers 105 (grid) + 95 (engine), 128 threads, MemAvail 969 GB | serverC: busy 97%, load1 132.86, workers 1 (grid) + 136 (engine), 128 threads, MemAvail 1394 GB | serverD: busy 91%, load1 59.63, workers 1 (grid) + 66 (engine), 64 threads, MemAvail 1442 GB

## UTC TIME WRITTEN
2026-11-23 07:45Z

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
Server 1 (this box): MemAvail 74.9 GB; live reservations 7 (7 GB); workers 21, of which TP-adopted 20 (RSS 26.3 GB) vs others 1 (RSS 1.2 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 69.39, 69.77, 66.18
  by tag: NYR quota 12 running 15 hungry False RSS 19.8 GB PSS 16.6 GB; NYE quota 16 running 1 hungry False RSS 1.5 GB PSS 1.4 GB; TOOLS quota 0 running 4 hungry False RSS 5.0 GB PSS 4.7 GB; REST quota 0 running 1 hungry False RSS 1.2 GB PSS 1.1 GB
  cell-months finished last hour (DONE markers): 11052
  top running jobs: TL3_LYR_NJT9_L32cec996_c8 (x14);TL3_NYE_Led06426a_RK7CT70m (x12);TL3_NYE_Led06426a_RK7CT77m (x8);
Server 2 (rs4 metal): load / disk / tp_launch procs: 86.76, 84.60, 83.96|/dev/md2         28T  2.8T   26T  10% /mnt/l2|50|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261123_0640Z_Josh-asia-daily-loss-stop-test.md 20261123_0645Z_Josh-session-end-run-vs-flatten-test.md 20261123_0740Z_Josh-depth-book-lock-info.md 20261123_0745Z_Josh-all-session-combined-numbers.md 20261123_0750Z_Josh-cross-session-locks-test.md
- 07:45Z INBOX 20261123_0750Z_Josh-cross-session-locks-test.md received. Josh (quoted): "we also don't have combined session locks right ? loss and profit yet?"
