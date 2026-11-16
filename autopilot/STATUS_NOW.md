# STATUS_NOW (written 2026-11-16 18:45Z by status_now.py; judgment sections from STATUS_NOTES.md)

## UTC TIME WRITTEN
2026-11-16 18:45Z

## NEEDS HELP
- Server 2: identity PASSED 18:42Z; copy ~135 of ~305 GB (ETA ~60 min); W-S2 told to start real jobs at cap 16 and ramp the knee on real jobs.
- Per-second MBO tables for 2026-11-01..11-05 are missing (W-CF2 checking raw files / quote only).

## NEEDS THE USER
- DS7.cs LINE 1790 BUG (v2.0): persist counter cleared on every winning second: the K7/U7/M7 book-reading profit lines (persist >= 2) can never fire live. You said keep them inert until the engine says whether firing helps: the 21:00Z page gives both worlds. (One-line fix in autopilot/DS7_PROFIT_LINES_SPEC.md.)
- JL2 does NOT model the persist=1 profit lines that DO fire live (takes at pct>=0.95-0.9875, P7/U7/H7 locks, NKD take): base mismatch being sized (W-RP replay by 20:30Z).

## PASSED SINCE LAST FILE
- none (no candidate has beaten all its persistent-draw controls yet)

## FAILED / WITHDRAWN SINCE LAST FILE
- London range skip (LS1/LS125): no HOLD DD cut at any k; old random controls invalid; Off/Shadow.
- Profit lines K7 lock / U7 tighten / M7 step: 43-month replay net negative and dead live by the line 1790 bug.

## EACH SERVER
Server 1 (this box): MemAvail 83.9 GB; live reservations 11 (11 GB); workers 28, of which TP-adopted 28 (RSS 49.7 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 42.35, 38.55, 36.22
  by tag: CF quota 4 running 2 hungry True RSS 4.2 GB PSS 3.9 GB; D10 quota 10 running 19 hungry False RSS 33.6 GB PSS 26.2 GB; BD quota 10 running 6 hungry True RSS 9.8 GB PSS 8.6 GB; FL quota 4 running 1 hungry True RSS 2.1 GB PSS 2.0 GB
  cell-months finished last hour (DONE markers): 337
  top running jobs: TL3_CF_L3D_W30_P20_SKIP_JL2 (x4);TL3_BD_F_sqz0_T30_U7_lo (x4);TL3_FL_LEADU70_SKIP_PD (x2);
Server 2 (rs4 metal): load / disk / tp_launch procs: 7.72, 3.33, 1.58|/dev/md2         28T  696G   28T   3% /mnt/l2|19|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261116_1826Z_profit-lines-leave-one-out.md 20261116_1827Z_rebuild-addendum2-tape-speed.md 20261116_1830Z_status-file-and-faster-mirror.md 20261116_1838Z_fill-the-cap.md 20261116_1840Z_core-meter-both-servers.md
- lead 18:38Z INBOX 20261116_1838Z_fill-the-cap.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the action)
- lead 18:39Z INBOX 20261116_1840Z_core-meter-both-servers.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the action)
- lead 18:43Z INBOX 20261116_1838Z_fill-the-cap.md DONE: (1) WHY SLOTS WERE EMPTY: no single blocker; the worker cap (28) was binding in bursts (admit.log 17:41
