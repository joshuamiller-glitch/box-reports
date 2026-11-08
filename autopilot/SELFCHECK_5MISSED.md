# SELFCHECK_5MISSED - why the live-cell row filter misses 5 of 86 replica cuts (PRE-PROOF, 2026-11-08)
Scratch: /mnt/l2/l2vast/_selfcheck/ (repro1.py finds the misses, repro3.py reads the engine's stop distance, repro4.py proves the fix). Seal ds3_all_ea/manifest_after.json sha 759f2258daac9d28 before and after: unchanged. No shared code edited.

## Cause (one line)
The 5 misses are all **PolicyCut**, not ThL2Cut. The live policy loss line is `pct <= -0.5` with pct = unreal / |avg entry - stop_px| (sim.py manage_policy, `stp`), not unreal <= -30 pt. The stop is placed 60 pt from the SIGNAL price (arm_px), not from the average fill, so |entry - stop| is 56.6 - 58.9 pt and the policy line fires at -28.3 .. -29.5 pt, 1-2 s before the ThL2 -30 pt line would. The row filter's fixed arm=30 never sees -30. It is NOT throttle phase, entry-average after add/slice, secs_ext window, row subsampling, ManagePolicy/ManageThL2 order, row timing or ITER12 vs 14: the ThL2 and Policy rows of the same second carry identical unreal/pulled/med/secs_ext, and the row is recorded at the cut second.

## The 5 trades (tid in REPLICA_StratTrades; cut time = engine cut = row decision 'cut'; row filter = fire None, i.e. never fires at arm 30 before the exit)
| tid | book side qty | cut ns (engine) | unreal at cut | |entry-stop| | 0.5 x stop dist | engine entry / stop |
|--|--|--|--|--|--|--|
| 45 | P7 S 4 | 1793669351.707 | -29.6875 | 58.9375 | 29.47 | 28215.56 / 28274.5 |
| 47 | K7 L 1 | 1793668284.440 | -29.50 | 57.75 | 28.88 | 28231.75 / 28174.0 |
| 79 | P7 L 3(7) | 1793749132.312 | -29.4167 | 56.917 | 28.46 | 28424.92 / 28368.0 |
| 182 | M7 L 2 | 1793865382.568 | -29.125 | 56.625 | 28.31 | 28307.625 / 28251.0 |
| 183 | P7 L 6(7) | 1793865382.568 | -29.2917 | 56.792 | 28.40 | 28307.79 / 28251.0 |
Each unreal sits 0.3-1.7 pt above the 30-pt arm; the last row before is -22..-28. (A 6th PolicyCut, O7, is outside L2GATE_BOOKS and its stop is 40 pt, so not in the 86.) All 99-100 ThL2Cut times match the filter exactly (consistent with TH_REDO_RULE_CODE.md).

## Minimal reproduction and fix
repro4.py: same scorer, same rows, arm = 0.5 x |entry - stop_px| per trade (the engine value) -> **86 / 86 cuts reproduced, 0 false** (was 81/86). Fix for the shadow scorer and any Tier S filter: express the loss arm as a fraction of the trade's actual stop distance, `-unreal >= (arm/60) x |avg_entry - stop_px|` (arm in pt on a 60-pt stop; for the live line 0.5), with stop_px from the live order (th_eval should log stop_px or stop distance; until then use signal price -/+ STOPPTS, or the proxy 0.5 x (STOPPTS - ~2.3) = ~28.8 pt for the 60-pt books, mean replica stop distance 57.7). Keep the fixed -30 pt for the ThL2 branch (it is in points: TH LOSS_MIN). Do not touch the 40 pt O7 book (stop 40, pct line = -20 pt, outside L2 scope).

## Bias of Tier S / A..G screens
Direction: the filter at a fixed arm in points slightly UNDER-counts and LATE-times cuts of the live cell and of any rule whose loss line is a policy pct; size on the blind week: 5 of 86 baseline cuts (5.8%), each late by about 1-2 s or absent, moves of 0.3-1.7 pt, i.e. roughly 0.2-1.7 pt x qty x 20 USD per affected trade = low hundreds of USD on 5 trades (on the order of 1% of the live-cut P&L), plus a changed path afterwards for those 5 (the filter holds them to the next row or to the true exit; the exits in rows end at the real cut, so the held path is unobserved - not quantifiable from rows). For a candidate with an arm in points >= 35 (P06 40, P07 40, P05 45 etc.) the same mismatch is a 0.5-2.3 pt shift of the effective arm (stop dist 57.7 not 60 -> arm x 0.96): candidates fire slightly later than a pct implementation, i.e. mildly CONSERVATIVE for the leads (their gain is slightly understated, <= 4% in arm terms), and the live-cell baseline is mildly flattered by missing 5.8% of cuts. Net: no change to any sign; magnitude small; correct it before the Gate 0 re-run. Not re-scored here.
