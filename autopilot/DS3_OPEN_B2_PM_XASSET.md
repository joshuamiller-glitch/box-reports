# DS3_OPEN_B2_PM_XASSET - T-OPEN block (ii), families 3.8 and 3.9 (D3O4) - STATUS 2026-10-27 22:20Z: PREREGS HASHED, SIGNALS BUILT, NOT SCORED (waiting for the shared harness of D3O1)
No cell scored; no P&L computed; no holdout read.
## Built
- Signals (17 NQ-traded, market entry): l2vast/ds3/out/open2/pmxa_signals.parquet; builder l2vast/ds3/code/open2/pmxa_signals.py. Counts: S1c/S1r 182, S2c/S2r 394, S3a 95, S3b 124, S4a 856, S4b 485, X1a/X1b 469, X2a 268, X2b 114, X2c 401, X3a 171, X3b 172, X4a 449, X4b 183 (days 2023-02..2026-10; ES/RTY/YM/ZN/6E-dependent signals end 2026-10-16).
- As-of audit: poison every bar at/after cut (09:31, 09:35, 09:40, 10:00): 0 mismatches; control (cut too early) 3,438 mismatching rows.
- Placebo (b) same-rule-random-clock draws: out/open2/pmxa_placebo_b_0_200.parquet (200 draws, anchor 11:30-14:00, FOMC days excluded; S1/S2 keep real side/days).
- Preregs: l2vast/ds3/prereg/TOPEN_B2_PMXA1..9_prereg.md (+ .sha256), 17 signals x 12 brackets = 204 cells, hashes in DECISIONS.md. Per-cell mechanism, predicted effect, MDE: most small-n cells are BELOW MDE at plausible effects (disclosed in each prereg).
- Block (vii) preparation: l2vast/ds3/code/open2/second_opens.py (OR-break and drive signals for CL 09:00, GC/SI/ZN 08:20, 6E 03:00/08:30, NQ 03:00, ES/RTY/YM 09:30 -> out/open2/second_opens_signals.parquet; tick-based fill model with FEES grade WEAK for RTY/YM/CL/GC/SI/ZN; equal_risk_lots; xcorr). Not scored.
- pmxa_interact.py: opening-type/pre-open conditioning tables with day-block bootstrap CIs (to run on harness trades).
## Pending
Scoring of the 204 cells through the D3O1 harness (open2/README_OPEN2.md not yet present), interaction tables, un-block comparison, verdicts.
