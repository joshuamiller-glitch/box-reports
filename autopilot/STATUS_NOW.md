# STATUS_NOW (written 2026-11-18 04:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-18 04:00Z | box1: busy 97%, load1 40.26, workers 11, MemAvail 106 GB | server2: busy 99%, load1 73.97, workers 14, MemAvail 1451 GB | pending box1-eligible 1645 / server2-eligible 41010 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-18 04:00Z

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
Server 1 (this box): MemAvail 105.6 GB; live reservations 0 (0 GB); workers 11, of which TP-adopted 11 (RSS 13.7 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 40.26, 38.70, 39.87
  by tag: NT quota 8 running 8 hungry False RSS 8.8 GB PSS 7.8 GB; SWB quota 4 running 3 hungry True RSS 4.9 GB PSS 4.5 GB; NT quota 0 running 8 hungry False RSS 8.8 GB PSS 7.8 GB
  cell-months finished last hour (DONE markers): 198
  top running jobs: TL3_SWB_P70_d23a42 (x6);TL3_NT_ID1 (x4);TL3_NT_ID0 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 69.33, 74.49, 76.20|/dev/md2         28T  994G   27T   4% /mnt/l2|24|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261118_0216Z_top40-candidates-into-pass2.md 20261118_0255Z_no-extra-server-tonight-order-of-work.md 20261118_0327Z_all-80-top-cells-recovered-seed-stage-a.md 20261118_0344Z_top-cells-NYPM-and-Asia-rows.md 20261118_0400Z_near-target-engine-rows-first.md
- lead 03:58Z INBOX 20261118_0400Z_near-target-engine-rows-first.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the action)
- lead 03:59Z INBOX 20261118_0400Z_near-target-engine-rows-first received: research order, accepted and DONE: _nt/first.txt (4 identity lines + K7/M7 sets on 20
