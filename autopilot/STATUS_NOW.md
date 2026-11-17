# STATUS_NOW (written 2026-11-17 22:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-17 22:30Z | box1: busy 98%, load1 42.48, workers 25, MemAvail 59 GB | server2: busy 60%, load1 17.80, workers 14, MemAvail 1482 GB | pending box1-eligible 38470 / server2-eligible 40094 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-17 22:30Z

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
Server 1 (this box): MemAvail 57.9 GB; live reservations 27 (27 GB); workers 25, of which TP-adopted 24 (RSS 28.2 GB) vs others 1 (RSS 3.4 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 42.48, 45.20, 49.98
  by tag: ME quota 10 running 6 hungry True RSS 7.5 GB PSS 6.8 GB; SWA quota 16 running 3 hungry True RSS 4.1 GB PSS 3.7 GB; SWB quota 16 running 1 hungry True RSS 1.2 GB PSS 1.0 GB; DD quota 6 running 2 hungry True RSS 2.0 GB PSS 1.8 GB; MB quota 4 running 2 hungry True RSS 2.2 GB PSS 2.0 GB; MF quota 4 running 5 hungry False RSS 5.6 GB PSS 5.1 GB; S3J quota 2 running 3 hungry False RSS 2.9 GB PSS 2.7 GB; CF quota 8 running 2 hungry True RSS 2.8 GB PSS 2.5 GB
  cell-months finished last hour (DONE markers): 368
  top running jobs: TL3_ME_C_LS_K2_M30_S27 (x10);TL3_CF_LAD_RAND (x6);TL3_SWA_ID6U7 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 16.35, 48.72, 65.45|/dev/md2         28T  934G   28T   4% /mnt/l2|22|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261117_1953Z_SIGNAL-x-BAR-GRID-every-trigger-on-every-bar.md 20261117_1957Z_SIGNAL-x-BAR-addendum-L2-orderflow-everything.md 20261117_2042Z_convert-recent-L2-days-and-data-quotes-wait.md 20261117_2046Z_TRIGGER-STUDY-is-priority-one-time-bars-included.md 20261117_2224Z_trigger-grid-speed-coarse-to-fine-not-cut.md
- lead 22:22Z INBOX 20261117_2224Z_trigger-grid-speed-coarse-to-fine-not-cut.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the action
- lead 22:22Z INBOX 20261117_2224Z_trigger-grid-speed-coarse-to-fine received: research order, accepted; owners: W-GRIDE (new helper: per-entry forward-path tab
