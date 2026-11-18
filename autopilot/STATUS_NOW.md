# STATUS_NOW (written 2026-11-18 04:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-18 04:30Z | box1: busy 100%, load1 39.90, workers 3, MemAvail 100 GB | server2: busy 100%, load1 66.41, workers 14, MemAvail 1350 GB | pending box1-eligible 1491 / server2-eligible 40772 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-18 04:30Z

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
Server 1 (this box): MemAvail 99.9 GB; live reservations 5 (5 GB); workers 3, of which TP-adopted 3 (RSS 2.6 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 39.90, 40.89, 39.65
  by tag: NT quota 8 running 2 hungry True RSS 1.9 GB PSS 1.8 GB; SWB quota 4 running 1 hungry True RSS 0.6 GB PSS 0.5 GB; NT quota 0 running 2 hungry False RSS 1.9 GB PSS 1.8 GB
  cell-months finished last hour (DONE markers): 272
  top running jobs: TL3_SWB_O73_9707f5 (x8);TL3_NT_SH_K7_k2 (x2);TL3_NT_SH_K7_k1 (x2);
Server 2 (rs4 metal): load / disk / tp_launch procs: 66.46, 66.00, 67.20|/dev/md2         28T 1014G   27T   4% /mnt/l2|24|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261118_0255Z_no-extra-server-tonight-order-of-work.md 20261118_0327Z_all-80-top-cells-recovered-seed-stage-a.md 20261118_0344Z_top-cells-NYPM-and-Asia-rows.md 20261118_0400Z_near-target-engine-rows-first.md 20261118_0424Z_EXIT-FAMILIES-seven-on-cells-that-show-life.md
- lead 04:23Z INBOX 20261118_0424Z_EXIT-FAMILIES-seven-on-cells-that-show-life.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the acti
- lead 04:24Z INBOX 20261118_0424Z_EXIT-FAMILIES received: research order, accepted: 7 exit families (structure stops, market targets, trailing, staged, time/be
