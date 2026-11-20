# STATUS_NOW (written 2026-11-20 22:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-20 22:30Z | WARNING serverC below 85% busy for 307 readings in a row with jobs pending

## UTC TIME WRITTEN
2026-11-20 22:30Z

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
Server 1 (this box): MemAvail 93.4 GB; live reservations 2 (2 GB); workers 20, of which TP-adopted 20 (RSS 26.5 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 60.45, 62.10, 64.84
  by tag: NYR quota 12 running 13 hungry False RSS 17.8 GB PSS 14.9 GB; TOOLS quota 0 running 7 hungry False RSS 8.8 GB PSS 8.3 GB
  cell-months finished last hour (DONE markers): 14198
  top running jobs: TL3_LYR_P1_L1756b913_CU4 (x20);TL3_NYE_L37da9520_RK7CT91m (x12);TL3_NYE_L37da9520_RK7CT98m (x10);
Server 2 (rs4 metal): load / disk / tp_launch procs: 94.35, 92.71, 93.36|/dev/md2         28T  2.7T   26T  10% /mnt/l2|38|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261120_1822Z_Josh-bare-D7-results-NOW.md 20261120_1908Z_labels-must-use-own-checks-not-fitted-D7.md 20261120_1930Z_trigger-debug-tables-for-the-NT8-port.md 20261120_2103Z_asia_stack_which_loop.md 20261120_2155Z_Josh-no-artificial-cutoff.md
