# DS3_OPEN_B2_PM_XASSET - T-OPEN block (ii): families 3.8 (pre-market / 08:30 hand-off) and 3.9 (cross-asset at the open, NQ-traded) - D3O4, 2026-10-27T22:34:47Z
## Verdict
**0 PASS, 0 CANDIDATE, 202 DEAD** of 204 prereg'd cells (17 signals x 12 CORE12 brackets; 2 cells X2a|VWAP and X2b|VWAP and basis M of S4a|VWAP had no valid trades and are empty). One cell, X4b|ORX, was CANDIDATE at the pre stage (beat placebo (b), rank 1.0, effect +23 pts) and died on the holdout look (HOLD stack d_sharpe -0.02, second holdout 2023-04..2024-01 mean -2,632 $/wk). Best-of-N null: best (b)-effect cell ranks 0.50 (M) / 0.63 (T) of its own null; no cell beats the group best-of-N p95.
## Un-block comparison (the question of the block)
Baseline (README_OPEN2): un-blocking 09:30-09:59 of the existing books is worth about +5.8k $/wk (WF). Against the stack with the whole 09:00-10:00 block removed, 199 of 201 cells are worse (best X4a|HOLD +685 $/wk, X1b|HOLD +531 $/wk, both fail gates); against the 09:30-09:59-only un-block every cell is negative. Nothing in 3.8 / 3.9 beats simply un-blocking KB/SM/ST.
## Bracket beta
113 of 201 cells add Sharpe to the live stack, but this is bracket beta: random-direction 09:31 entries earn +1.6k to +4.0k $/wk on the long-hold exits (controls.pkl), so a positive stack-add on T1030/T1200/HOLD is not information; 45 cells beat placebo (b), 29 beat the bracket-beta placebo (d), and none beats both with the stack-add and holdout gates.
## Top 15 cells by stack-add Sharpe delta regardless of verdict (basis M; verdict is the lower tier of M and T)
| cell | n valid | stack-add Sharpe d (vs live, WFPRE, basis M) | d mean $/wk | MDE $/wk | fwd weeks to settle | d maxDD $ | d mean vs un-block-all $/wk | vs un-block 09:30-09:59 $/wk | HOLD mean $/wk | rank vs (b) | rank vs beta (d) | failed gates (M or T) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X3a|HOLD | 171 | +0.34 | +6,289 | 7,933 | 119 | +30,306 | -196 | -1,437 | +2,119 | 0.88 | 0.94 | beats_b,beats_beta,beats_c,best_of_N,hold,span2,stack_add_pre,year_share |
| X3a|T1200 | 171 | +0.31 | +5,679 | 7,599 | 134 | +29,906 | -806 | -2,047 | +3,039 | 0.88 | 1.00 | beats_b,best_of_N,span2,stack_add_pre |
| X4a|HOLD | 449 | +0.29 | +7,170 | 10,253 | 153 | -20,969 | +685 | -556 | +4,730 | 1.00 | 1.00 | beats_c,best_of_N,span2 |
| X3a|T1030 | 171 | +0.28 | +5,095 | 6,302 | 115 | +8,107 | -1,390 | -2,631 | +3,664 | 1.00 | 1.00 | best_of_N,span2,stack_add_pre |
| X4b|T1200 | 183 | +0.27 | +4,979 | 6,351 | 122 | -32,194 | -1,507 | -2,748 | +1,486 | 1.00 | 1.00 | best_of_N,hold,span2,year_share |
| X4b|HOLD | 183 | +0.26 | +5,917 | 7,638 | 125 | -30,294 | -568 | -1,809 | +1,345 | 1.00 | 1.00 | best_of_N,hold,span2,year_share |
| X4a|T1200 | 449 | +0.21 | +5,109 | 9,810 | 277 | +42,417 | -1,377 | -2,618 | +5,603 | 1.00 | 0.94 | beats_b,beats_beta,beats_c,best_of_N,stack_add_pre |
| X4a|T1030 | 449 | +0.20 | +3,993 | 8,577 | 346 | +67,367 | -2,493 | -3,734 | +6,880 | 1.00 | 1.00 | beats_b,beats_beta,beats_c,best_of_N,stack_add_pre |
| X1b|T1200 | 469 | +0.20 | +5,207 | 8,996 | 224 | -49,175 | -1,278 | -2,519 | -1,126 | 1.00 | 0.94 | beats_b,beats_beta,beats_c,best_of_N,hold,stack_add_pre,year_share |
| X1b|HOLD | 469 | +0.20 | +7,016 | 10,378 | 164 | -27,905 | +531 | -710 | -267 | 1.00 | 0.94 | beats_b,beats_beta,beats_c,best_of_N,hold,year_share |
| S2r|ONHL | 209 | +0.18 | +3,709 | 5,262 | 151 | +28,455 | -2,777 | -4,018 | -372 | 1.00 | 1.00 | beats_b,best_of_N,hold,span2,stack_add_pre,year_share |
| S4b|HOLD | 483 | +0.17 | +2,546 | 9,886 | 1,131 | -47,288 | -3,940 | -5,181 | -2,800 | 1.00 | 0.25 | beats_b,beats_beta,beats_c,best_of_N,hold,span2,stack_add_pre,year_share |
| S4a|HOLD | 850 | +0.17 | +6,411 | 12,152 | 269 | +47,133 | -74 | -1,315 | +4,185 | 0.88 | 0.94 | beats_b,beats_beta,beats_c,best_of_N,hold,stack_add_pre |
| X4b|T1030 | 183 | +0.17 | +3,457 | 4,772 | 143 | -21,494 | -3,029 | -4,270 | +915 | 0.94 | 1.00 | beats_b,beats_beta,beats_c,best_of_N,hold,span2,year_share |
| S4a|STRAIL | 850 | +0.16 | +2,800 | 7,728 | 571 | +34,192 | -3,685 | -4,926 | +2,448 | 0.88 | 0.88 | beats_b,beats_beta,beats_c,best_of_N,hold,stack_add_pre |

MDE and forward weeks are the harness values (paired weekly difference; WFPRE 74 weeks); every top cell has |d mean| below its MDE, so the positive deltas are within noise: they cannot be distinguished from zero at the weekly level and would need 115-1,100 forward weeks to settle.
## Family read
- 3.8 (S1 08:30 spike, S2 08:30-09:29 drift, S3 pre-market trend vs open drive, S4 pre-market range break/fail): every cell DEAD. Continuation and reversal (S1c/S1r, S2c/S2r) both fail; best 3.8 cell S2r|ONHL (+3.7k/wk stack-add, fails (b), holdout, 2023-24, year-share). S4a (856 trades) is the cleanest sample: no bracket beats (b) and beta.
- 3.9: cross-asset cells have the highest raw deltas (X3a ZN-opposite-continuation, X4a 6E pre-open direction, X4b 6E confirms drive) but all fail best-of-N and at least one of holdout / second holdout / beta / (c); X4a|HOLD is positive on HOLD (+4.7k $/wk) yet loses (c) (random side inside the regime) and 2023-24. X2 (OR break confirmed by ES/RTY/YM) and X1 (NQ-ES relative strength) show nothing; X2c fade-unconfirmed-break is DEAD.
- Power: signal counts are small (S1 182, S3 95-124, X3 171, X4b 183); per-trade MDE is 10-35 pts on 30-60 pt brackets, above any plausible edge (prereg MDE tables). The null is therefore "could not see an effect smaller than ~$5-12k/wk", not "no effect".
## Interaction tables
Per-cell interaction tables (year, dow, opening type 09:35/10:00, gap class, VIX tercile, 08:30 type, 10:00-rule, FOMC, opex, month-end, side) are inside the harness pickles (l2vast/ds3/out/topen_b2/grp_TOPEN_B2_PMXA*/<signal>.pkl, key cells[(basis,bracket)]['cond']); none is promoted because no cell passed. Pre-open (09:29) feature quantile tables: l2vast/ds3/code/open2/pmxa_interact.py (not run: nothing to condition).
## Deviations and disclosures
1. Brackets are the harness CORE12 (F30,F45,F60,ORX,VWAP,ONHL,T1030,T1200,HOLD,STRAIL,CHAND,SCALE), not my placeholder labels; ORX height = NQ first-5-min range from the anchor. Placebo (b): anchors random 11:00-11:30 (harness window), 16 draws; look-back 90 min then overlaps the open window. Logged in DECISIONS.md before scoring. Best-of-N is over the combined 202 cells (all 9 groups), stricter than per group.
2. Both bases M (mapped conservative) and T (tape-direct-style) were run; verdict = lower tier. Neither is real-book replay (block (iii)+).
3. Holdout: one look per prereg group (9 looks logged in holdout_looks.jsonl, pre-holdout text sha 96274818e0e9775d9620c6d242628233f78a8ab1b33d8e1eb4e4fdf05705985a, pmxa_prehold.txt); ledger +204 cells.
4. Release flags: CPI, NFP, FOMC verified; claims/ISM RULE (unverified); other 08:30/10:00 releases UNAVAILABLE. S1 uses the empirical spike (as-of 09:29) instead of the calendar. 10:00-release days are in the windows (flat-09:58-10:02 variant not run in this block).
5. Data: ES/RTY/YM/ZN/6E feeds end 2026-10-16, NQ 2026-10-23; cross-asset signals end 2026-10-16; UNTOUCHED never read. Fills: 1 lot-style harness fills on bars/1-s quotes (09:00-12:00); entries after 12:00 use the no-quote fallback. Fees 4.84 RT. Overlaps flagged: S4a/X2a/X2b with D3O1 3.1 OR-break cells, S4b with D3O2 pre-market sweep fade, X2b subset of X2a.
6. Only 4 draws entered the M-basis best-of-N null for some cells (harness), so its p95 is coarse.
## Block (vii) preparation (not scored)
l2vast/ds3/code/open2/second_opens.py: ORb5/ORb15/DRV5/DRV15 signals (+ mirrors) for CL 09:00, GC/SI/ZN 08:20, 6E 03:00/08:30, NQ 03:00, ES/RTY/YM 09:30 -> out/open2/second_opens_signals.parquet (650-950 days per cell); tick-based fill model (slippage ticks, fee RT, grade) with RTY/YM/CL/GC/SI/ZN flagged WEAK PROXY (4.84 from ES), 6E 5.30 (addendum); equal_risk_lots (to ST10 weekly SD) and xcorr (same-cell cross-instrument weekly correlation, pooled and per-instrument verdicts) helpers. Prereg design for block (vii): cells = {instrument-open} x {ORb5, ORb15, DRV5, DRV15} x R-unit brackets (stop/target 1.0, 1.5, 2.0 x own R5, time exit +60 min, hold to the session end) with mirrors as controls and the same placebo (a)/(b)/(c)/(d) set; to be hashed at block (vii) start.
## Files
Preregs l2vast/ds3/prereg/TOPEN_B2_PMXA1..9_prereg.md; code l2vast/ds3/code/open2/pmxa_signals.py, pmxa_run.py, pmxa_final.py, pmxa_prereg.py, pmxa_interact.py, second_opens.py; results l2vast/ds3/out/topen_b2/pmxa_final.pkl, pmxa_pre.pkl, out/open2/pmxa_cells_M.csv; rows l2vast/ds3/rows/DS3_TOPEN_B2_PM.json. No series produced (no PASS/CANDIDATE).
