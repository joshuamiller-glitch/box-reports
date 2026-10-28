
## 2026-10-27T11:42:56Z USER DIRECTIVE (replay priority, verbatim)
Replay governor priority, in order, all other replays paused until these finish: (1) D3PB base months 38-45 (PB_ST10_SWZ_T3 direct verdict), (2) TR1 direct on TR1A_ens_s0.5_k4 and TR1A_ens_s1.0_k3 only (drop the other 13), (3) D3XT exits replay to completion. Then resume T-BRACKET A/B and TR2. Report ETA per item in MORNING.

## 2026-10-27T11:54:28Z USER DIRECTIVE (spec request PB3B_R5_P1, verbatim)
SPEC REQUEST: write autopilot/DS3_SPEC_PB3B_R5_P1.md at the same parameter level as DS3_SPEC_PB_ST10_SWZ_T3.md (every rule needed to reproduce the trade list in NT8 OnBarClose from 1-min bars: 5-min Supertrend recursion and flip rule, EMA20 definition and seed, exact "touch" condition, how the pullback extreme is tracked and reset, exact extreme-break trigger and entry bar, one-entry-per-pullback and re-arm rules, invalidation, session windows, bracket, lots and locks; plus the identity-audit entry share, expectation table WF/HOLD/2023 with SD, maxDD, worst week, and the add-to-DS3 table). Then run the P9 robustness block on PB3B_R5_P1 only (cell-specific mirror, day-block bootstrap maxDD, VIX terciles, fill sensitivity, 1.5x/2x cost, capacity to 42 lots) as the pullback final recommended. Register it in the forward register as the DS3 PB replacement candidate.

## 2026-10-27T15:56:46Z USER DIRECTIVE (verbatim)
DIRECTIVE_PBX_CHOP_FULL.md is the current scope and the box is at 20% CPU. Start now, in parallel: T-PBX blocks (ii)-(v) (bars, order types, tape/footprint ends, direct replay of block (i)'s top cells and of every later survivor) and T-CHOP blocks 1-5 (band fades, range model, failed-breakout fades, session reversals, tape exhaustion, gates x bars x orders), each with the random-in-regime / random-in-gate placebo. Preregs in blocks of <= 30; 90% floor; report ETA per block in MORNING. Block 0 / block (i) results stand; do not re-run them.

## 2026-10-27 user directive: OVERNIGHT PROGRAM (items A-H, 10-27 -> 10-28 13:00Z). Full text (account ids redacted) in autopilot/DIRECTIVE_OVERNIGHT_20261027.md

## 2026-10-28 USER DIRECTIVE: CONFIRMATION PROGRAM (full text in autopilot/DIRECTIVE_CONFIRM_20261028.md)
Items A cross-instrument replication of DR5m & RVW1|F30 (ES/YM/RTY + NQ ref, 8 cells), B RVW1 queue-position execution replay (5/10 lots, 1s/3s delay), C DR5m at hard caps 40/50/60 + margin, D forward register (both rows, DS5 mix row + evaluator tz/PE fix, TR3_DON15_S alert -> 1.7 pt), E Sim specs if A passes. Reports DS3_CONFIRM_A/B/C/D.md, DS3_CONFIRM_FINAL.md. No grid, no re-tuning.
