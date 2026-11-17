# STATUS_NOW (written 2026-11-17 00:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-16 23:55Z | box1 AUTO-FILL: SIGCONT of 0 stopped admission/launch/driver procs []; admit.log silent -3 s; ql_drivers alive before=4 restarted=[]; workers 27

## UTC TIME WRITTEN
2026-11-17 00:00Z

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
Server 1 (this box): MemAvail 93.5 GB; live reservations 3 (3 GB); workers 21, of which TP-adopted 21 (RSS 38.2 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 36.22, 30.50, 25.91
  by tag: CF quota 8 running 3 hungry True RSS 5.5 GB PSS 4.6 GB; EV quota 8 running 2 hungry True RSS 2.9 GB PSS 2.5 GB; BD quota 10 running 5 hungry True RSS 9.6 GB PSS 8.2 GB; FL quota 8 running 2 hungry True RSS 4.3 GB PSS 3.4 GB; RA quota 2 running 2 hungry False RSS 3.9 GB PSS 3.3 GB; TOOLS quota 8 running 7 hungry False RSS 12.0 GB PSS 9.5 GB
  cell-months finished last hour (DONE markers): 654
  top running jobs: TL3_CF_SP_L2_S15 (x6);TL3_BD_F_fix_T25_H7_am_mr1_p209 (x4);TL3_RA_JL2_PL3_M7L_CAP3 (x2);
Server 2 (rs4 metal): load / disk / tp_launch procs: 90.90, 90.65, 90.80|/dev/md2         28T  868G   28T   4% /mnt/l2|187|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261116_2105Z_new-data-candidates-quotes-and-pilots.md 20261116_2134Z_server2-is-starving.md 20261116_2151Z_server2-still-idle.md 20261116_2242Z_lead-status-note.md 20261116_2333Z_box1-has-zero-workers.md
