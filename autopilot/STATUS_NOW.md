# STATUS_NOW (written 2026-11-17 04:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-17 04:15Z | box1: busy 100%, load1 36.86, workers 28, MemAvail 84 GB | server2: busy 100%, load1 91.69, workers 97, MemAvail 1374 GB | pending box1-eligible 3882 / server2-eligible 17078 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-17 04:15Z

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
Server 1 (this box): MemAvail 83.7 GB; live reservations 1 (1 GB); workers 28, of which TP-adopted 28 (RSS 47.5 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 36.96, 36.19, 35.82
  by tag: CF quota 8 running 2 hungry True RSS 4.3 GB PSS 3.6 GB; BD quota 10 running 6 hungry True RSS 9.6 GB PSS 8.7 GB; FL quota 8 running 4 hungry True RSS 7.9 GB PSS 5.8 GB; JV quota 14 running 8 hungry True RSS 12.4 GB PSS 10.7 GB; TOOLS quota 8 running 8 hungry False RSS 13.3 GB PSS 10.6 GB
  cell-months finished last hour (DONE markers): 1327
  top running jobs: TL3_JV_PL_U (x8);TL3_CF_RS_D2 (x6);TL3_JV_PL_M (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 91.69, 90.90, 90.94|/dev/md2         28T  870G   28T   4% /mnt/l2|190|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261117_0007Z_box1-underfilled.md 20261117_0024Z_lead-note-and-box1.md 20261117_0146Z_wake-test.md 20261117_0312Z_flat-vs-book-explain-a-kp.md 20261117_0400Z_refill-both-queues-before-they-drain.md
