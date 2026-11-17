# STATUS_NOW (written 2026-11-17 00:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-17 00:15Z | box1 AUTO-FILL: SIGCONT of 0 stopped admission/launch/driver procs []; admit.log silent -3 s; ql_drivers alive before=4 restarted=[]; workers 17

## UTC TIME WRITTEN
2026-11-17 00:15Z

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
Server 1 (this box): MemAvail 102.5 GB; live reservations 5 (5 GB); workers 17, of which TP-adopted 17 (RSS 32.0 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 27.65, 27.82, 26.94
  by tag: CF quota 8 running 1 hungry True RSS 2.0 GB PSS 1.9 GB; EV quota 8 running 3 hungry True RSS 4.9 GB PSS 4.1 GB; BD quota 10 running 6 hungry True RSS 11.5 GB PSS 9.5 GB; FL quota 8 running 2 hungry True RSS 4.7 GB PSS 3.4 GB; TOOLS quota 8 running 5 hungry False RSS 8.8 GB PSS 6.9 GB
  cell-months finished last hour (DONE markers): 631
  top running jobs: TL3_FL_HOLDL5_W60 (x4);TL3_FL_HOLDL5_W30 (x4);TL3_BD_F_fix_T35_K7_as_mr1_p267 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 93.74, 92.50, 91.72|/dev/md2         28T  868G   28T   4% /mnt/l2|188|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261116_2134Z_server2-is-starving.md 20261116_2151Z_server2-still-idle.md 20261116_2242Z_lead-status-note.md 20261116_2333Z_box1-has-zero-workers.md 20261117_0007Z_box1-underfilled.md
- lead 00:07Z INBOX 20261117_0007Z_box1-underfilled.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the action)
