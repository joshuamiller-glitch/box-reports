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

## CL (ZL-1, own-parameter grid keltner / supertrend / momentum_vote / pullback_band / hma_vwap; 2026-11-05): see DS3_INSTR2_CL.md - 66,024 cells, 30 stage-2 finalists, none clears (placebo p_book min 0.13, family p min 0.17, corr to the stack <= 0.12); label: REGIME / best-of-F, no lead. Scope sha256 77e4df99... (+ addendum 1); ledger T2_CL; rows FADE_ROWS_T2_CL.md. BASE-4 block B (other families) is separate.

## CL (ZL-1, own-parameter grid keltner / supertrend / momentum_vote / pullback_band / hma_vwap; 2026-11-05): see DS3_INSTR2_CL.md - 66,024 cells, 30 stage-2 finalists, none clears (placebo p_book min 0.13, family p min 0.17, corr to the stack <= 0.12); label: REGIME / best-of-F, no lead. Scope sha256 77e4df99... (+ addendum 1); ledger T2_CL; rows FADE_ROWS_T2_CL.md. BASE-4 block B (other families) is separate.

## 2026-11-05 20:10Z block 2 MERGE (CAL assembler; evaluator md5 cc29db32 in force; stack bases V0 and V2 named in owner rows; all-instrument n_tested 1,075,248+)
Columns kept: instrument | session | family/params | L1M L3M L6M HOLD MID PRE X' ($/wk, equal-risk lots, carry weeks dropped) | placebo | label. maxDD/Calmar are not columns of the owner row; dCalmar is inside 'stack gain'. Top 3 rows per instrument = first 3 rows of the owner page (owners sorted them).
### RTY: 12 stage-2 rows; clears the bar: none (every label begins FAILS)
- RTY | b10 | RTY K m2.0 | L1M nyam L3M K L6M b10 HOLD ema8 MID atr14 PRE m2.0 X' orient 1 | +466 | corr/stack: +466 | +1166
- RTY | b3 | RTY K m2.0 | L1M pre L3M K L6M b3 HOLD ema13 MID atr7 PRE m2.0 X' orient 1 | +1113 | corr/stack: +1352 | +781
- RTY | b15 | RTY MV pre | L1M MV L3M b15 L6M thr0.25 HOLD k3 MID orient 1 PRE D1200 tgt1 T30 (n 2079) X' +500 | +657 | corr/stack: +300 | +177
### YM: 12 stage-2 rows; clears the bar: none (every label begins FAILS)
- YM | b15 | YM S asia | L1M S L3M b15 L6M atr7 HOLD m2.0 MID orient -1 PRE D600 tgt1 T30 (n 3012) X' +119 | +168 | corr/stack: +170 | +141
- YM | b1 | YM K m1.0 | L1M nyam L3M K L6M b1 HOLD ema13 MID atr7 PRE m1.0 X' orient 1 | +1716 | corr/stack: +1711 | +1272
- YM | b1 | YM K m1.0 | L1M nyam L3M K L6M b1 HOLD ema13 MID atr7 PRE m1.0 X' orient 1 | +2626 | corr/stack: +2724 | +1681
### CL: 30 stage-2 rows; clears the bar: none (every label begins FAILS)
- CL | pre | CL hma_vwap_cross stop ('usd', 600) tgt 1.5R T30 (n 1057) | L1M +615 L3M +515 L6M +552 HOLD +529 MID +1751 PRE -406 X' -157 | p_book 0.21 (shift5/side/days x HOLD,L6M,stac | corr/stack: k*=0.00: HOLD dCalmar +0.000 L6M dCalmar +0.000; corr V0 0.05/-0.05 V2 0.05/-0.07 (daily/weekly) | FAILS: tolerant gate (PRE mean -406 < -0.5 MDE (-268))
- CL | pre | CL keltner_flip stop ('usd', 1200) tgt 2R T60 (n 187) | L1M +32 L3M +101 L6M +120 HOLD +165 MID +234 PRE +53 X' -215 | p_book 0.73 (shift5/side/days x HOLD,L6M,stac | corr/stack: k*=0.00: HOLD dCalmar +0.000 L6M dCalmar +0.000; corr V0 0.05/0.00 V2 0.04/-0.02 (daily/weekly) | FAILS: tolerant gate (min sample L3M (trades 9/10, active weeks 6/6); min sample L6M (trad
- CL | pre | CL keltner_flip stop ('usd', 600) tgt 1R T120 (n 856) | L1M +847 L3M +565 L6M +955 HOLD +594 MID +1290 PRE -223 X' +85 | p_book 0.47 (shift5/side/days x HOLD,L6M,stac | corr/stack: k*=0.00: HOLD dCalmar +0.000 L6M dCalmar +0.000; corr V0 0.01/0.07 V2 0.02/0.05 (daily/weekly) | FAILS: placebo p_book 0.47 > .10
Plain sentences: RTY - 8,490 of 486,360 cells pass the tolerant gate, none reaches the family test (best family p 0.80); stage-2 rows have placebo p_book 0.17-0.77, family p 1.00, walk-forward not positive: no diversifier. YM - 11,605 of 487,872 pass tolerant, best family p 0.88; best stage-2 row p_book 0.06-0.10 but family p 1.00 and walk-forward negative: no diversifier. CL (ZL-1 five families) - 66,024 cells, 30 finalists, placebo p_book min 0.13, family p min 0.17, uncorrelated with the stack (|r|<=0.12): REGIME / best-of-F, no lead; BASE-4 block B (other CL families) pending.
Other pages: NQ13 (ZL-2 interim 1): no walk-forward selector beats the fixed live parameters on 2023-26, no refit rule. MBO7 (ZL-1): the seven are uncorrelated with the stack (daily -0.04, weekly -0.02) but drawdown-heavy ($229k alone); at k 0.33 the stack Calmar goes 0.121 to 0.137 with maxDD unchanged and worst-20 weeks $7k worse; file ends 2026-02-06 so no H2 test; this is a third-leg SIZE question, not a diversifier-bar pass (no placebo/walk-forward on it yet).
Look-ahead incident: Z1's sig_lib._levels gave the overnight high/low as the whole-night extreme (look-ahead); unfixed RTY run showed 126 false LEAD-CANDIDATES. Z2 reruns RTY/YM on fixed code (numbers above are fixed); Z1 sig_lib v2 fixed two level look-aheads and ES is re-running; ZL-1 families.py audit 5,116 checks 0 failures; S4a GC 780 checks 0; S4b 1,369 checks 0; Z3 0 so far. Z1's superseded ES v1 run must not be merged.
Prereg status: RTY/YM scope + grid + exec note logged 19:34Z, before rows (20:05Z): OK. CL scope 77e4df99 logged before cells: OK per owner page (see DECISIONS grep). Z2/ZL-2/ZL-1/BASE-4/S4b/Z3 lines: OK. S4a GC prereg file INSTR2_GC_PREREG.md exists; no DECISIONS line seen at this merge (check). No rows from ES, GC, ZN, ZB, 6E, 6J, NKD, BTC, MBT yet.
Bar status: NOTHING clears the diversifier bar at this merge.
(block 2 correction) S4a GC prereg sha 6bfc4902 IS logged in DECISIONS.md line 5095 at 19:42Z, before any GC outcome: OK.
- Z1 T-INSTR-2 ES stage-1 page: autopilot/DS3_INSTR2_ES.md (CAL: merge into DS3_INSTR2.md ranked table).

## 6E (ZL-1 stage B, 2026-11-05): see DS3_INSTR2_6E.md - 65,835 cells, 30 finalists, none clears (placebo p_book min 0.13, family p min 0.36, walk-forward positive 0 of 30, corr to stack <= 0.23); winners are pre-market Supertrend/Keltner cells negative in 2024-25 and before 2023 (REGIME-ONLY). Scope T2_6EJ_ZL1_scope.md sha256 d75d3cc8...; ledger T2_6E; trade frames /mnt/l2/l2vast/instr2_trades/6E/ (30), CL's 30 backfilled to /mnt/l2/l2vast/instr2_trades/CL/.

## 2026-11-05T20:40:25Z block 3 MERGE (CAL; md5 d3eb4c8a; bases V0/V2 as in owner rows)
Rows pages now present: 6E BTC CL ES GC NKD RTY YM ZB ZN (MBT merged into BTC). Per-owner pages DS3_INSTR2_<inst>.md exist for all ten. Verdict extraction below is from each page's FAILS labels: see each page's plain sentence; I only restate it where I read it.
### 6E
**Plain sentence: no 6E book from these five families clears the diversifier bar: of 65,835 cells 11.9% are NOW-ONLY, the winners are all pre-market (08:30-09:30 ET) 3-5 minute Supertrend / Keltner cells (L6M +$100-540 a week) that lost money in 2024-25 (PRE -$150 to -$510) and in every earlier year but one or two (13-year percent-frame check: mean per trade -$16 to -$150), the 30 finalists have placebo p_book 0.13-0.92 (none <= .10), family p 0.36-1.00 (none <= .10), no walk-forward positive at both lookbacks (0 of 30), correlation to the NQ stack at most 0.23: REGIME-ONLY / best-of-F, no lead.**
Scope T2_6EJ_ZL1_scope.md (sha256 d75d3cc897c244b55a30af74e6b5ca2a09732c4901e3bba816132779f8e5196c; DECISIONS.md, before any ZL-1 cell); Z3 stage A (all 16 library families x 6 sessions x 2 brackets) is separate (l2vast/ds3/out/instr2/6E/, T2_Z3_addendum1.md sha256 2693abea...). Code l2vast/ds3/code/t2cl/ (t2_grid.py, t2_stage2.py, t2_stage3.py, t2_finish.py), library instr2/families.py (look-ahead audit PASS), evaluator instr2_eval.py. Output /mnt/l2/l2vast/instr2_6e/. Ledger T2_6E 65835 rows; rows FADE_ROWS_T2_6E.md; finalist trade frames /mnt/l2/l2vast/instr2_trades/6E/ (30); all-instrument n_tested registry 1,643,823. 
rows page: 31 lines; BAR CLEARED lines: 0
### BTC
**Plain sentence (interim, stage 1):** over 144,648 cells per series, 96% of the cells lose money after costs (median mean R -0.07 to -0.08); the few that survive the tolerant gate and persistence are one signal cluster, the 10-minute Keltner flip with a wide 2.5-ATR band in the Asia session (n 165-350 trades, t about 3.4 against 144,648 cells tested), plus a few Supertrend 15-minute and HMA-VWAP cells; correlation to the NQ stack is about 0.0-0.08, which is the diversification property, but the dollars at the participation cap are negligible and the family test decides whether any of it is more than best-of-F.
rows page: 21 lines; BAR CLEARED lines: 0
### ES
## 0. Plain sentence
**STAGE-1 RESULT (ES): 0 LEAD CANDIDATES. Of 502,740 grid cells 486,864 were evaluated (456,498 eligible), 42,162 are positive in L3M, L6M and HOLD, 8,149 pass the tolerant gate, 28,986 are NOW-ONLY (REGIME); the best tolerant cell has family p 0.64 (the family null max z_j has median 3.57 and 95th percentile 4.01; the best real z_j is 4.26), and the 15 cells with family p <= .10 are all NOW-ONLY London/regime cells with PRE and X' deeply negative. Every tolerant cell sits inside what the random-side null produces over the grid (best-of-F), so none is a lead.**
rows page: 31 lines; BAR CLEARED lines: 0
### GC
**Plain sentence: GC has no book on this evidence. Of 141,120 cells (448 signal sets x 5 liquid sessions x 63 brackets), 1,756 pass the tolerant gate, and they are one pattern: trend-following flips (Keltner 1,125, Supertrend 398, plus VWAP-reclaim, momentum, pullback, HMA-VWAP, Donchian, ORB) in NY-AM and the 08:30 pre session that pay in 2026; all 40 finalists fail the shared evaluator (placebo p_book .06-.99, family p 1.00 at F = 132,286), and every one is NEGATIVE in 2013-2023 (percent frame; 0-6 of 11 pre-2023 years positive; $-362k to $-2k over the 10 years), with the 1-min pipeline calibrated against the tick-built 1-s path at weekly correlation 0.93-1.00 (>= 0.90, so the verdict is f
## Setup
rows page: 41 lines; BAR CLEARED lines: 0
### NKD
**Plain sentence (interim, stage 1):** NKD loses money after costs in essentially every cell: no cell of the 144,564 has a positive full-sample mean R (median -0.17 R per trade), the best full-sample t is 1.10, zero cells pass the tolerant gate with persistence, and the 102 cells that pass the tolerant gate alone are all negative over the full 13 years; with the cap below one contract in every session NKD cannot be a diversifier on this evidence. The family null for NKD is not needed to reject (the observed best t is 1.1; a random-side null on 144,564 cells would put the max above that), and it is still queued at a reduced world count under the 3-worker rule.
rows page: 7 lines; BAR CLEARED lines: 0
### ZB
Plain sentence: of 5426 stage-A rows, 30 have L3M, L6M and HOLD all positive and 3 pass the screen gate (older windows tolerant, L6M n>=20); none has a placebo, walk-forward or stack check yet, so none is a lead; the stage-B bracket sweep on the top 300 cells is running.

rows page: 0 lines; BAR CLEARED lines: 0
### ZN
Plain sentence: of 5426 stage-A rows, 57 have L3M, L6M and HOLD all positive and 8 pass the screen gate (older windows tolerant, L6M n>=20); none has a placebo, walk-forward or stack check yet, so none is a lead; the stage-B bracket sweep on the top 300 cells is running.

rows page: 0 lines; BAR CLEARED lines: 0
Reproduction audit addendum: INSTR2_REPRO_AUDIT.md (200 frames; net $ exact; window tables agree except 5 GC cells; micro screen: micros lose about $50-60/wk to fee drag).

## 6J (ZL-1 stage B, 2026-11-05): see DS3_INSTR2_6J.md - 82,152 cells (2.6% NOW-ONLY), 30 finalists, none clears (placebo p_book min 0.12, family p min 0.39, walk-forward positive 2 of 30, corr to stack <= 0.27); REGIME-ONLY. Scope T2_6EJ_ZL1_scope.md sha256 d75d3cc8...; ledger T2_6J; trade frames /mnt/l2/l2vast/instr2_trades/6J/ (30).
