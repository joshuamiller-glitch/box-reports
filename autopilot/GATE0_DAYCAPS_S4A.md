# GATE0_DAYCAPS_S4A (PRE-PROOF, post-hoc, frozen live file only; no PASS claim) - 2026-11-07
Source read, not inferred: data/live_code/DS7.cs (sha256 54697597...; SetDefaults 379-436 and 400-414, books 523-545, CheckLimits 3453, CheckBookLock 3414, rollover 669-698, entry gates 766/1204, SessionDateNow 3476) + GATE0_ANSWERS_1106 s3/s5/s6. Code: l2vast/ds3/code/gate0/daycaps.py (new; BookLock class + audit()). Live file: data/live_frozen/..._reconstructed.csv sha256 424c68da... (187 rows).

## 1. What the live code does (exact)
- **Two separate mechanisms.** (a) Caps +5R/-2R are NOT ComboProfitCapR/ComboLossFloorR (both 0 = OFF in SetDefaults). They are per-book dollar properties MaxDailyProfit/MaxDailyLoss read by CheckLimits() on every 1-min bar: REALIZED day P&L (net of commission) >= profit or <= -loss -> DayHalt (exit "DayHalt" if in trade). K7 12000/4800, M7 12000/4800, U7 24000/9600, P7 42000/16800, H7 24000/9600, A7 6000/2400; O7, B7/E7/R7 none. (b) CheckBookLock (PerBook, >=2 s on prints, realized + OPEN pnl): week floor wk <= -12R; day give-back once GbPeak (running max of day equity, reset each session) >= 2R and day <= 0.5 x GbPeak -> GbLocked + DayHalt, exit "BookLock". Week give-back arm = 0 (off). Skip reason `dayHalt` (DayHalt) / `weekHalt` / `locked` (GbLocked) block entries.
- **R** = BaseQty x StopPts x $20 with BASE lots (not session-table lots): K7 2,400; M7 2,400; U7 4,800; P7 8,400; H7 4,800; A7 1,200; O7 800 (40-pt stop). Scales only with SizeMult>1 (never).
- **Day boundary** = first bar of the chart session template = 18:00 ET (Sun 18:00 opens Monday): resets SessionBase, GbPeak/GbLocked, DayHalt = WeekHalt. **Week boundary** = Monday of the CALENDAR date of the bar (Sunday maps to the prior Monday), so WeekBase/WeekHalt reset at Mon 00:00 ET, not Sun 18:00.
- ExitPending only gates entries/exits (no P&L effect); a lock calls RequestBookExit (market) so the exit fill carries slippage.

## 2. Test on the frozen week (daycaps.audit, trade-close resolution; the file has no open-pnl path)
- **Entries while halted by the rule: 0. Realized-only triggers missed: 0. Week floor: never near (worst running week realized: M7 -5,060 vs -28,800).**
- **K7 daily loss cap explained**: K7 trading day 11-02 18:00 -> 11-03 18:00 realized -5,090 at Tue 11:39:37 (cap -4,800) -> DayHalt; next K7 entry Tue 18:06 (new day). So the code explains K7's Tue 11:40-18:00 silence. It does NOT explain M7 (+140 day), P7 (+21,160, last exit 13:08:49), U7, A7, O7: no book entered anywhere Mon 14:01-18:21 or Tue 13:08-18:06 (other than the K7 case), consistent with the outage hypothesis, not with caps.
- **Tue 02:55-08:20 (superseded by outage)**: K7 at 02:55:35 day -3,840 (-1.60R) vs cap -4,800: caps do not fire, so the code does not explain it; consistent with the platform outage. P7 +16.7k, M7 -1,615 stop 02:47 also below caps.
- **BookLock exits in the file (3, plus note on the coordinator's labels)**:
| exit | book | day equity before -> at lock | realized peak | arm 2R | give-back needs true peak in |
|---|---|---|---|---|---|
| Mon 11-02 01:44:15 (this is A7, not P7) | A7 | +1,705 -> +1,310 | +1,705 | 2,400 | [2,620, 3,410) |
| Wed 11-04 07:25:04 (the only P7 BookLock; not 01:44) | P7 | +9,150 -> +9,060 (trade -90, 4 s after entry) | +15,255 | 16,800 | [18,120, 18,300) |
| Thu 11-05 04:35:14 | K7 | +3,915 -> +3,060 (trade -855) | +5,320 | 4,800 | [6,120, 7,830) |
 None is explained by REALIZED equity alone (realized peaks are below the arm or the floor); all three are explained iff the intraday OPEN-pnl peak was higher than realized by the amounts above (A7 +915, P7 +2,865, K7 +800). Plausible (open-pnl peaks are in the rule) but UNVERIFIED: needs the NQ 1-s path under each position. The P7 window is only 180 wide (the lock fired 4 s after entry when equity was just above the floor), so it is a tight, not a loose, consistency. Halts held: no further entries those days.

## 3. Engine day-cap handling (blind/lock_rules.py = sl_lib._stage/run_book, ENGINE_CONFIG_LIVE_Q1A rows 3/13) vs live: differences
1. Caps: engine skips an entry when realized net of CLOSED trades at the entry second is >=+5R / <=-2R, for every book; live applies them only to books with dollar caps (none for O7, B7/E7/R7), evaluated once per 1-min bar (up to ~60 s lag before DayHalt, so a re-entry in that minute is possible), and flattens an open trade on breach.
2. R: engine = planned lot x 60 x 20 (matches live for K7/M7/U7/P7/H7/A7); O7 (stop 40, R 800) and any session-lot vs base-lot treatment must be checked in the book table; live uses BASE lots always.
3. Day give-back: engine e(t) = realized + open MTM on a 1-s path, flatten at path[ks+1]; live samples >=2 s on prints, exits by market order (slippage, lock-to-fill latency, PumpExit); same 2R/50% arithmetic. Live commissions enter Realized only at close (engine same via cost on exit).
4. Week: engine week = label-day week starting Sun 18:00 ET; live week resets Mon 00:00 ET (Sun 18:00-24:00 P&L is in the prior week's base). Irrelevant this week (floor -12R never near), but not identical.
5. Order: engine applies caps, then give-back, then floor sequentially on surviving rows; live runs them concurrently, cap per bar, lock per 2 s.
6. Live lock also fires while flat (equity moved by realized only) - engine does too (e is continuous). Entry-gate uses three flags (dayHalt/weekHalt/locked); engine cancels all later entries of the label day after a give-back (equivalent).
7. State persistence: live reloads LimitState after restart (CarryDay); not modelled.

## 4. gate0_check.py updated (l2vast/ds3/code/gate0/gate0_check.py; backup in scratchpad)
- Default --live = frozen blind-week file (LIVE0), asserted on sha256 + 187 rows + net sum before every default run (confirmed; unchanged).
- Policy line in force (s6) recorded as POLICY_LINE and policy_arm_pts(book) (0.50 x stop: 30 pts on 60, 20 on O7); printed in every report. The harness compares exits, it does not simulate the cut.
- Outage Tue 11-03 02:55-08:20 ET always excluded from both sides (entry in [start,end)) before any denominator; live/engine positions entered before and exiting after the window start are listed (control: K7 01:48->02:55:35 flagged). `--excl-optional` (default off) also excludes Mon 11-02 14:01-18:21 and Tue 11-03 13:08-18:06 ET. Control run (live as engine) unaffected (control, not evidence).
