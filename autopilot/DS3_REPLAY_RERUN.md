# DS3_REPLAY_RERUN - re-run of the 5 memguard-killed ssa_direct replay months (user OK 2026-10-29 ~21:30Z). Data only: nothing rescored, no existing report edited.

## Plain line
All 5 killed months re-ran to completion on the first and only re-run (0 memguard kills; memguard.log last entry still 2026-10-29T01:26:29Z). The 5 months now exist as complete R_<month>.parquet with done markers. Their results are bit-identical to every other queue wave's replay of the same entries (see Comparison). The PARTIAL data holes in q2, q4 and q6 are therefore closed at the replay level; the tier upgrade (PARTIAL -> COMPLETE) itself needs the owners to rescore the three waves with these months included (not done here, per instruction).

## Verified list of killed months (memguard.log + claim-without-done markers in /mnt/l2/l2vast/ds3_ssa_q*/)
memguard.log has 5 ssa_direct kill lines: 19:31:47Z Oct28 (2024-06, re-run once earlier, done), 21:20:48Z (q2 2023-12 per MORNING), 23:49:32Z, 23:58:16Z, 01:26:29Z Oct29 (wave/month not named in the log). That is 4 kills after 2024-06 for 5 missing months, so one missing month has no matching memguard line (the log does not name the month; not resolved, immaterial). The claim-without-done check below is authoritative. Claims with no done marker: q2 2023-12; q4 2025-06, 2025-10, 2025-11; q6 2025-10. No other wave has a hole. Matches the user's list exactly.

## How it was run
Worker invoked directly (same code, `ssa_direct.py worker <ym>`, venv python) with SSA_ENT = out/ssa/entries_q<N>.parquet (the wave's own entries) and SSA_OUTD = a NEW directory /mnt/l2/l2vast/ds3_ssa_q<N>_rerun/ (original dirs, claim files and logs untouched, nothing deleted). Not routed through corepool/orchestrator because the original claim_<month> O_EXCL files block the orchestrator and I may not delete them; the governor-gated path is the same engine and the same worker function. Driver: sequential, ONE month at a time (one worker alive at any time), launch gated on MemAvailable >= 32 GB (avail at launches 83-127 GB), stop-on-failure; worker RSS ~4.5-6 GB (own limit 25 GB). The 13 frozen held-track workers (corepool slots 8,9,12,13,15,16,20,21,22,23,24,27,28) were not signalled or touched; the governor (pid 1997918) was left running; replay workers alive stayed far below cap 24 (5-6 at start incl. other agents' jobs). Wall: 21:28Z to 23:20Z. Only my own processes were started; none killed.

| wave | month | start - end (Z) | rc | entries | rows (V0+V1+VC) | days |
|---|---|---|---|---|---|---|
| q2 sd2a | 2023-12 | 21:28 - 21:55 | 0 | 942 | 2,826 | 20 |
| q4 sd34 | 2025-06 | 21:55 - 22:19 | 0 | 200 | 600 | 20 |
| q4 sd34 | 2025-10 | 22:19 - 22:59 | 0 | 214 | 642 | 22 |
| q4 sd34 | 2025-11 | 22:59 - 23:10 | 0 | 172 | 516 | 19 |
| q6 sb3 | 2025-10 | 23:10 - 23:20 | 0 | 1,786 | 5,358 | 23 |

## Comparison to what was already there
The PARTIAL scores contain no rows for the missing months (that is the hole), so there is nothing to overlap in the same wave. Overlap was checked instead against OTHER waves' completed replays of the SAME month, matching entries by (t_ent, side, stop ticks, target ticks, lot class) and comparing entry_avg, exit_avg, status, xtype for V0, V1, VC:
| rerun | identical entries found in other waves | rows compared (3 variants) | mismatches |
|---|---|---|---|
| q2 2023-12 | 118 (q3 2, q4 4, q5 2, q6 66, q7 30, q8 14) | 354 | 0 |
| q4 2025-06 | 36 (q2 6, q3 2, q5 2, q6 22, q7 4) | 108 | 0 |
| q4 2025-10 | 16 (q2 14, q7 2) | 48 | 0 |
| q4 2025-11 | 28 (q2 6, q5 2, q6 18, q7 2) | 84 | 0 |
| q6 2025-10 | 334 (q1 4, q2 146, q3 24, q5 70, q7 32, q8 58) | 1,002 | 0 |
Pass-1 wave 0 (ds3_ssa) shares some entries too and differs on a few (e.g. 15 of 54 compared fields for 2023-12): those are entries whose forced-flat instant t_fl differs between the pass-1 and queue entry files (the pass-1 rows exit at an earlier exact-round time, xtype 4), not an engine difference; same-t_fl entries match. Not used as a tier basis.

Month-level outputs (raw engine fills, before the P9 target correction that scoring adds):
| rerun | TAKEN share V0/V1/VC | mean pts/trade V0 / V1 / VC |
|---|---|---|
| q2 2023-12 | 98.9% (10 EXPIRED_UNFILLED of 942, all variants) | -0.87 / -0.79 / -1.06 |
| q4 2025-06 | 100% | +3.47 / +2.49 / +2.81 |
| q4 2025-10 | 100% | +0.99 / +1.00 / +1.54 |
| q4 2025-11 | 100% | +2.65 / +2.78 / +3.41 |
| q6 2025-10 | 100% | -0.55 / -0.69 / -0.84 |
(Month means are descriptive; no gate or tier was recomputed.)

## Which tiers can be upgraded (PARTIAL -> COMPLETE) once rescored by the owners
| wave | missing month(s) -> window | cell-sessions | current tier | hole size (miss_share) | upgrade |
|---|---|---|---|---|---|
| q2 sd2a | 2023-12 -> X span (10th of 10 months) | 37 scored; 16 pass MEASURED gate (PRE/HOLD gates were already complete) | the 16 MEASURED-gate survivors are SESSION-CANDIDATE-PARTIAL | 0.6% - 2.8% of rows | data is now COMPLETE for all 37; the 16 can drop PARTIAL (X-span statistics change, so rescoring may move individual numbers/gates) |
| q4 sd34 | 2025-06 (PRE), 2025-10, 2025-11 (H25 HOLD) | 7 | 0 passed MEASURED; stored tiers NEAR(half fails) x4, SESSION-CANDIDATE x3 | 8.5% - 13.0% | data COMPLETE; nothing to upgrade by tier (no MEASURED-gate survivor), but HOLD/H25 gates are now evaluable on a rescore |
| q6 sb3 | 2025-10 (H25 HOLD) | 56; 20 pass MEASURED gate | the 20 are SESSION-CANDIDATE-PARTIAL (gated HOLD incomplete) | 1.5% - 8.4% | data COMPLETE; the 20 can drop PARTIAL after a rescore confirms the HOLD/H25 gate (a pass at the old rate is not guaranteed: HOLD means include ~8% of rows that were missing) |
Total flagged SESSION-CANDIDATE-PARTIAL cell-sessions: 36 (16 + 20), matching D6LINE line 79. None of the five D6 legs sits in a PARTIAL wave, so no D6 leg changes.
I did NOT claim a tier change: PARTIAL -> COMPLETE here means "replay data complete, eligible for rescoring"; a tier can only be assigned by ssa_score with these months included (point the loader at /mnt/l2/l2vast/ds3_ssa_q<N>_rerun/R_<month>.parquet in addition to the original directory; pass --partial off).

## Exact lines the report owners should change (originals NOT edited)
- DS3_SESSION2_Q_sd2a.md line 73: "FLAG PARTIAL: q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete)" -> "q2 sd2a: month 2023-12 re-run 2026-10-29 (complete, out dir ds3_ssa_q2_rerun); rescore pending; PARTIAL flag lifts after rescore".
- DS3_SESSION2_Q_sd34.md line 39: "FLAG PARTIAL: q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing ..." -> months re-run 2026-10-29 (ds3_ssa_q4_rerun); rescore pending.
- DS3_SESSION2_Q_sb3.md line 77: "FLAG PARTIAL: q6 sb3: month 2025-10 (H25 HOLD) missing (worker killed) ..." -> month re-run 2026-10-29 (ds3_ssa_q6_rerun); rescore pending; the 20 "SESSION-CANDIDATE-PARTIAL" rows (lines 25-44) become SESSION-CANDIDATE only if the rescored HOLD/H25 gate holds.
- DS3_SESSION2_Q_BOOKS.md lines 4-7 (PARTIAL waves header and the q6/q2/q4 bullets) and the q6 "SESSION-CANDIDATE-PARTIAL" rows in its table (lines 44-104, 20 rows): same replacement, pending rescore.
- DS3_SESSION2_D_D6LINE.md line 79 ("36 SESSION-CANDIDATE-PARTIAL") and line 80 ("Partial waves, tiers PARTIAL and not imputed: ...") -> "replay holes closed 2026-10-29 (DS3_REPLAY_RERUN.md); tiers re-labelled after rescore".
- MORNING.md lines 303, 305, 311, 318, 327 (q2/q4/q6 PARTIAL notes and the 'awaiting user OK' question at line ~325): question answered (user OK 2026-10-29 21:30Z, re-run done).
- DS3_SESSION2_A.md line 24 already states 2024-06 re-run once; add "queue-wave months 2023-12 (q2), 2025-06/10/11 (q4), 2025-10 (q6) re-run once on 2026-10-29".

## Files
Outputs /mnt/l2/l2vast/ds3_ssa_q2_rerun/R_2023-12.parquet, ds3_ssa_q4_rerun/R_2025-{06,10,11}.parquet, ds3_ssa_q6_rerun/R_2025-10.parquet (+ done_/claim_/log_ files); code unchanged (l2vast/ds3/code/ssa_direct.py); driver script in the session scratchpad (rerun.sh, gated >=32 GB, stop on first failure).
