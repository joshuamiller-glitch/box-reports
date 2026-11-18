# STATUS_NOW (written 2026-11-18 18:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-18 18:30Z | box1: busy 100%, load1 40.28, workers 13, MemAvail 38 GB | server2: busy 100%, load1 187.75, workers 14, MemAvail 1239 GB | pending box1-eligible 1823 / server2-eligible 41036 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-18 18:30Z

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
Server 1 (this box): MemAvail 37.6 GB; live reservations 4 (4 GB); workers 13, of which TP-adopted 12 (RSS 19.3 GB) vs others 1 (RSS 3.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 40.28, 43.14, 43.76
  by tag: NYF quota 20 running 8 hungry True RSS 13.0 GB PSS 11.5 GB; LON quota 8 running 4 hungry True RSS 6.3 GB PSS 5.6 GB; REST quota 2 running 1 hungry False RSS 3.0 GB PSS 2.9 GB
  cell-months finished last hour (DONE markers): 326
  top running jobs: TL3_LON_LA4_ADDM (x8);TL3_NYE_XA3_CT35m (x6);TL3_NYW_XA3_ADD (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 157.50, 120.79, 103.83|/dev/md2         28T  1.2T   27T   5% /mnt/l2|23|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261118_1505Z_new-books-which-layers-and-bare-vs-engine.md 20261118_1610Z_specs-for-the-HEADLINE-rows-WP10-WP1.md 20261118_1722Z_NO-DEADLINE-full-search-then-controls-then-gates-then-D8.md 20261118_1731Z_ADDENDUM-day-done-is-a-setting-clock-order-Asia-replaceable.md 20261118_1830Z_check-server2-thread-count-same-model-as-A-B.md
- 18:29Z INBOX 20261118_1830Z_check-server2-thread-count-same-model-as-A-B.md received (accepted, research only); LEAD NOTE: ANSWER: server 2 really is 64 threa
