# DS3_INSTR2 merged ranked table (T-INSTR-2 assembler, CAL). Append-only (>>); one block per 6 h.
Columns: instrument | session | family | params | L1M L3M L6M HOLD MID PRE X' | maxDD | Calmar | corr to NQ stack | stack gain | placebo | label
Diversifier bar: tolerant gate; placebo p<=.10 and family max-stat; own-parameter walk-forward positive; corr to NQ stack <=0.3; stack Calmar up with carrying week dropped. Name the BASE on every number (V0 / V2).
Data owned: see INSTR2_DATA_INVENTORY.md.
## 2026-11-05 19:50Z block 0: no owner rows yet
Owners' pages not yet present (Z2 INSTR2_SESSIONS.md delivered; Z1/S4a/Z3/S4b FADE_ROWS_T2_* pending). No instrument clears the bar. Plain sentence: ES RTY YM GC CL ZN ZB 6E 6J BTC MBT NKD: no result yet.
## 2026-11-05 20:10Z block 1 status (2-hourly while owners active)
Prereg lines in DECISIONS.md before any rows: Z2 sessions (sha 2185a5c1), S4b BTC/MBT (21d03112), BASE-4 evaluator (dbaca779), ZL-2 NQ13, ZL-1 families (6735e760), Z3 ZN/ZB/6E/6J (171d83f1, 9abd67e3, 2a748324, fd387ee6). No scope line yet found for Z1 (ES/RTY/YM) or S4a (GC/CL): flag if rows appear without one.
FADE_ROWS_T2_*.md pages present: none. Instruments with rows: none. Clears the diversifier bar: none so far.

## LOOK-AHEAD AUDIT OF THE SHARED FAMILY LIBRARY (ZL-1, 2026-11-05T19:51Z) - after the sig_lib._levels incident
Result: NO failure in instr2/families.py. test_families_intraday.py (sha256 f3c28757a6c74fff4c8382373db4e31fd0d15e3730860738adbc1fa78e0d5147): 5,116 checks, 0 failures - signals, prior-day levels (RTH and all-hours), session VWAP (anchors 18:00 / 09:30 / 03:00) and ATR5 computed on bars truncated at 15-minute cuts across 17:00-18:30, 08:30-09:35 and 15:55-16:05 ET equal the full-series values on the same bars, on 9 days (Sunday open, 4 DST-change days, 2 roll days, a half-day, a plain Tuesday); brute-force recomputation from raw bars agrees. The earlier truncation test (496 checks, test_families.py) also passes. families.py sha256 bd1dbd70048322874a292bf0167f704e5f14bd481fd4ba50fcec57fc1a74258e (unchanged, no version bump). Any owner feature NOT from families.py (overnight high/low, session extremes, anchored levels) must be a running quantity of the bars since its anchor and should pass the same cut test; the library has no overnight-H/L feature.
