# STATUS_NOW (written 2026-11-19 11:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 10:55Z | box1: busy 100%, load1 74.56, workers 30, MemAvail 68 GB | server2: busy 100%, load1 158.85, workers 26, MemAvail 945 GB | pending box1-eligible 157376 / server2-eligible 157376 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 279.22, workers 101 (grid) + 102 (engine), 128 threads, MemAvail 1167 GB | serverB: busy 100%, load1 264.53, workers 101 (grid) + 99 (engine), 128 threads, MemAvail 1125 GB

## UTC TIME WRITTEN
2026-11-19 11:00Z

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
Server 1 (this box): MemAvail 68.4 GB; live reservations 7 (7 GB); workers 28, of which TP-adopted 27 (RSS 46.8 GB) vs others 1 (RSS 0.6 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 75.16, 77.27, 81.10
  by tag: ASI quota 16 running 6 hungry True RSS 10.5 GB PSS 9.7 GB; NYL quota 12 running 6 hungry True RSS 12.2 GB PSS 8.3 GB; NYR quota 16 running 9 hungry True RSS 14.0 GB PSS 13.0 GB; LON quota 12 running 6 hungry True RSS 10.0 GB PSS 8.7 GB; REST quota 0 running 1 hungry False RSS 0.6 GB PSS 0.5 GB
  cell-months finished last hour (DONE markers): 2519
  top running jobs: TL3_NYW_L0f097450_ADDLO (x18);TL3_ASI_L1edb9fab_RH7 (x10);TL3_LON_LA4_CT21p (x8);
Server 2 (rs4 metal): load / disk / tp_launch procs: 157.27, 156.13, 150.44|/dev/md2         28T  1.9T   27T   7% /mnt/l2|53|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_0633Z_engine-is-the-bottleneck-make-the-ladder-engine-faster.md 20261119_0740Z_Dallas-cap-follower-is-undoing-the-engine-cap.md 20261119_0849Z_Asia-counts-frozen-and-Frankfurt-real-pass1.md 20261119_0956Z_Answer-alert-G-NYENG-and-explain-real-pass1-finished.md 20261119_1014Z_Mode-bug-do-not-void-engine-winners.md
