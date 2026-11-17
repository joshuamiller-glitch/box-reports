# STATUS_NOW (written 2026-11-17 13:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-17 13:00Z | box1: busy 100%, load1 37.88, workers 28, MemAvail 86 GB | server2: busy 100%, load1 93.49, workers 97, MemAvail 1374 GB | pending box1-eligible 31365 / server2-eligible 46849 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-17 13:00Z

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
Server 1 (this box): MemAvail 85.7 GB; live reservations 0 (0 GB); workers 28, of which TP-adopted 28 (RSS 51.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 37.81, 39.04, 38.73
  by tag: CF quota 8 running 3 hungry True RSS 5.1 GB PSS 4.2 GB; EV quota 8 running 3 hungry True RSS 5.0 GB PSS 4.2 GB; JV quota 14 running 9 hungry True RSS 17.9 GB PSS 12.4 GB; SURVIVORS quota 12 running 5 hungry False RSS 9.1 GB PSS 7.2; TOOLS quota 8 running 8 hungry False RSS 14.7 GB PSS 11.7 GB
  cell-months finished last hour (DONE markers): 1427
  top running jobs: TL3_CT_C_N_M7L_S87 (x6);TL3_CT_C_N_M7L_S61 (x6);TL3_CF_ST_23_S_RND (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 93.77, 92.92, 92.63|/dev/md2         28T  880G   28T   4% /mnt/l2|192|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261117_0545Z_stage1-survivors-lookahead-and-selection.md 20261117_0728Z_after-stage1-three-families-and-cell-tests.md 20261117_0816Z_stop-moot-permutations-restore-engine-cap.md 20261117_1048Z_m7-london-controls-first.md 20261117_1235Z_m7-london-finish-the-tier.md
