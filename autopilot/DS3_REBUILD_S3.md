# DS3_REBUILD_S3 - T-REBUILD stage 3: exits jointly on the raw chassis, chosen walk-forward (W-S3). FIRST PASS. Updated 2026-11-27 16:53Z
> VALIDATION (W-S3, FIRST PASS, 2026-11-17): trials counted = 497 grid sets (7 books x 71) = N_low, 1,065 book-session-candidates = N_used (TRIALS_LEDGER.csv RB3); correction = walk-forward (select on 2023-04..2025-10 only, freeze, then HOLD 2025-11..2026-04 and L6M 2026-05..10 untouched) + ulcer reality check over the grid + CSCV PBO + >= 30 persistent random-exit engine controls on the chosen cells; numbers shown: none yet (no selection frozen; grid still landing); missing controls = NOT FINISHED, never passing. Prereg: DECISIONS.md line 2026-11-17 W-S3 PREREG.

VERDICT (data ends 2026-10-30; FIRST PASS; NO RESULT YET: the grid is landing and the selection is not frozen): grid of 497 raw-chassis exit sets is queued (20518 set-months pending of 21,385); identity gate PASSED; landed set-months so far 2062 (SEL + HOLD + L6M, all S3 grid sets); measured landing rate over the last hour 0 set-months/h (0 shown as nan until an hour of history exists). Order: server 2 takes from the front (identity, then HOLD+L6M months for every cell), box 1 takes from the back (oldest SEL months), so both ends close in on the middle.

**FIRST BUILD FAILED IDENTITY (11-17 09:07Z) and was discarded.** d10_hooks overrides check_book_lock and ignores the ev_layers lock_off switch, so K7/P7/A7 sets re-enabled the per-book give-back lock (ID_K7 202610: 237 vs 335 trades, 12 BookLock exits that S0 does not have). Fix: an outermost hook s3_nolock (code/th_rb_s3/s3_nolock.py) turns the lock off again; all TL3_RB_S3_* run dirs and leases of the first build were deleted (own prefix only) and the grid is rebuilt; no grid result is read until identity.ok.

## THP grammar extension needed in DS7 (parser change for the Table 1 policy lines)
```
bracket <book> <session|*> stop=<pts> target=<pts> [timestop=<minutes>[:<min open profit pts>]] [halfoff=<pts> [be]]
  session: asia | london | nyam | nypm (the existing lines 'bracket K7 * target=59' stay valid; today only target= exists)
  stop=<pts>      initial stop distance in points; lots scale x 60/stop (min 1) as ApplyPolicyBracket does
  timestop=N:M    N minutes after the entry fill, if open profit < M points exit at market (M omitted = unconditional exit at N)
  halfoff=X [be]  at +X points take half (live lots floor, min 1); with 'be' the rest moves to breakeven
```
New parser tokens: stop=, timestop=, halfoff= and a session in the third column of 'bracket'. Everything on these pages is raw-chassis research until the exact JL3 assembly and 30 random-bracket controls (S3J) are scored.

## 1. Design
Chassis = TL3_RB_S0_<book> (JL2 engine, one book alone, every layer off: no LOT/SIGQ/REG, no cuts/locks/caps/blackout/NTZ, native lots), months 202304..202610 (43, nothing from 202611). Exit cell = d10_hooks static bracket (stop S, target T in points; lots x 60/S, min 1 = live ApplyPolicyBracket, so every stop is compared at the same dollar risk; the book trades the SAME setting in all its sessions) + bd_hooks time stop (exit at N minutes after the fill if open profit < +M points, M99 = unconditional) or half-off at +X with breakeven on the rest. 71 settings per book:
- 41 brackets: stop {30,40,50,60,75,90} x target {20,30,40,50,60,75,90} less the native point (K7 M7 U7 P7 H7 A7 60/60, O7 40/90). Code S<stop>T<target>.
- 24 time stops: N {30,60,120,240} min x M {0 (exit if not in profit), 99 (hard)} on three anchor brackets A0 native, A1 40/40, A2 50/30. Code A<anchor>N<min>M<pts>.
- 6 half-off: take half at +20/+30/+40 pts, breakeven on the rest off/on, native bracket. Code HX<pts>B<0|1>.
Per-session choice: the grid runs one setting for all sessions of the book; the per-session pick reads that session's trades from the uniform-setting set (approximation: sessions interact only through the one-position rule); the frozen picks are then run as an ASSEMBLED set per book (exact) and that run is the reported one.
Selection rule (frozen before any result, s3_select.py): per book x session cell with >= 150 native SEL trades (15 cells), candidates = grid sets with all 31 SEL months landed; floor SEL mean $/wk >= native -25%; lowest SEL ulcer (RMS of daily drawdown, dollars); keep native unless ulcer falls >= 10%.

## 2. Progress (set-months landed)
| book | cells | SEL months landed (of 31 x 71) | HOLD months landed (of 6 x 71) | L6M months landed (of 6 x 71) |
|--|--|--|--|--|
| K7 | 71 | 193 / 2201 (4 cells complete) | 42 / 426 | 60 / 426 |
| M7 | 71 | 219 / 2201 (5 cells complete) | 42 / 426 | 60 / 426 |
| P7 | 71 | 191 / 2201 (4 cells complete) | 42 / 426 | 60 / 426 |
| U7 | 71 | 218 / 2201 (5 cells complete) | 42 / 426 | 60 / 426 |
| H7 | 71 | 245 / 2201 (6 cells complete) | 42 / 426 | 60 / 426 |
| A7 | 71 | 245 / 2201 (6 cells complete) | 42 / 426 | 60 / 426 |
| O7 | 71 | 65 / 2201 (0 cells complete) | 14 / 426 | 60 / 426 |

Identity gate (TL3_RB_S3_ID_<book> vs TL3_RB_S0_<book>, 202610 and 202504, trade for trade):
```
TL3_RB_S3_ID_K7 202610: 335 vs 335 trades, net 10511.92 vs 10511.92 -> IDENTICAL
TL3_RB_S3_ID_K7 202504: 356 vs 356 trades, net 14696.92 vs 14696.92 -> IDENTICAL
TL3_RB_S3_ID_M7 202610: 141 vs 141 trades, net -23246.40 vs -23246.40 -> IDENTICAL
TL3_RB_S3_ID_M7 202504: 164 vs 164 trades, net 14229.32 vs 14229.32 -> IDENTICAL
TL3_RB_S3_ID_P7 202610: 243 vs 243 trades, net 6907.14 vs 6907.14 -> IDENTICAL
TL3_RB_S3_ID_P7 202504: 286 vs 286 trades, net -102022.68 vs -102022.68 -> IDENTICAL
TL3_RB_S3_ID_U7 202610: 41 vs 41 trades, net -14237.52 vs -14237.52 -> IDENTICAL
TL3_RB_S3_ID_U7 202504: 39 vs 39 trades, net -16339.08 vs -16339.08 -> IDENTICAL
TL3_RB_S3_ID_H7 202610: 35 vs 35 trades, net 21759.20 vs 21759.20 -> IDENTICAL
TL3_RB_S3_ID_H7 202504: 32 vs 32 trades, net 22628.44 vs 22628.44 -> IDENTICAL
TL3_RB_S3_ID_A7 202610: 75 vs 75 trades, net -5783.50 vs -5783.50 -> IDENTICAL
TL3_RB_S3_ID_A7 202504: 33 vs 33 trades, net 1711.06 vs 1711.06 -> IDENTICAL
TL3_RB_S3_ID_O7 202610: 9 vs 9 trades, net -6425.62 vs -6425.62 -> IDENTICAL
TL3_RB_S3_ID_O7 202504: 13 vs 13 trades, net -2375.34 vs -2375.34 -> IDENTICAL
```

## Results
NOT YET: selection is frozen only when every grid set has its 31 SEL months; HOLD and L6M of grid cells stay unread until then.
