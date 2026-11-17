# STATUS_NOW (written 2026-11-17 08:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-17 08:15Z | box1: busy 100%, load1 43.32, workers 25, MemAvail 90 GB | server2: busy 100%, load1 122.66, workers 78, MemAvail 1380 GB | pending box1-eligible 23239 / server2-eligible 38115 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-17 08:15Z

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
Server 1 (this box): MemAvail 89.6 GB; live reservations 3 (3 GB); workers 25, of which TP-adopted 25 (RSS 43.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 43.32, 42.29, 41.88
  by tag: CF quota 8 running 3 hungry True RSS 6.3 GB PSS 5.1 GB; EV quota 8 running 2 hungry True RSS 3.0 GB PSS 2.7 GB; BD quota 10 running 10 hungry False RSS 16.3 GB PSS 13.6 GB; FL quota 8 running 7 hungry True RSS 12.4 GB PSS 9.6 GB; JV quota 14 running 1 hungry True RSS 2.0 GB PSS 1.9 GB; TOOLS quota 8 running 2 hungry False RSS 3.7 GB PSS 3.5 GB
  cell-months finished last hour (DONE markers): 466
  top running jobs: TL3_EV_FB_A_KP (x4);TL3_CF_ST_9_S (x4);TL3_BD_F_fix_T35_K7_as_pl3_p37 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 122.66, 121.07, 120.47|/dev/md2         28T  878G   28T   4% /mnt/l2|152|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261117_0146Z_wake-test.md 20261117_0312Z_flat-vs-book-explain-a-kp.md 20261117_0400Z_refill-both-queues-before-they-drain.md 20261117_0545Z_stage1-survivors-lookahead-and-selection.md 20261117_0728Z_after-stage1-three-families-and-cell-tests.md
