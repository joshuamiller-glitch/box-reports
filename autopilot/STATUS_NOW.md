# STATUS_NOW (written 2026-11-22 22:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-22 22:15Z | box1: busy 100%, load1 69.16, workers 18, MemAvail 70 GB | server2: busy 96%, load1 82.23, workers 27, MemAvail 1038 GB | pending box1-eligible 947050 / server2-eligible 5120 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 186.31, workers 105 (grid) + 102 (engine), 128 threads, MemAvail 1022 GB | serverB: busy 100%, load1 176.54, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 977 GB | serverC: busy 99%, load1 135.39, workers 1 (grid) + 136 (engine), 128 threads, MemAvail 1375 GB | serverD: busy 96%, load1 63.68, workers 1 (grid) + 67 (engine), 64 threads, MemAvail 1441 GB

## UTC TIME WRITTEN
2026-11-22 22:15Z

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
Server 1 (this box): MemAvail 69.9 GB; live reservations 5 (5 GB); workers 18, of which TP-adopted 17 (RSS 21.0 GB) vs others 1 (RSS 1.1 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 70.51, 67.41, 64.15
  by tag: NYE quota 16 running 14 hungry False RSS 19.1 GB PSS 17.4 GB; TOOLS quota 0 running 3 hungry False RSS 1.9 GB PSS 1.4 GB; REST quota 0 running 1 hungry False RSS 1.1 GB PSS 1.0 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_L3655649c_ALN (x15);TL3_SR_AS_STKd8106b26ef_BF1_NL3_TAKEMF4_TK8 (x6);TL3_NYE_L3bbe44f5_ALN (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 80.56, 83.02, 84.90|/dev/md2         28T  2.8T   26T  10% /mnt/l2|46|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261122_1612Z_Josh-recent-basis-prior-year-check-fix.md 20261122_2140Z_layer-keys-definitions-for-the-port.md 20261122_2200Z_nyam-two-generic-book-specs.md 20261122_2205Z_london-nypm-stack-loops-see-no-books.md 20261122_2210Z_Josh-asia-stack-weights.md
