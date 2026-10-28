# DS3_OPEN_FINAL - the opening-drive study, block (ii) screens + blocks (iii)/(iv) on the top signals (compiled by D3O1, 2026-10-28; research only, nothing goes live)
Written from the report/rows files of D3O1 (3.1, 3.2, block iii, confirmations, classifier), D3O2 (3.3/3.4), D3O3 (3.5/3.6/3.7), D3O4 (3.8/3.9) as of this writing; the lead may amend with later blocks (vii)-(x). Rows: l2vast/ds3/rows/DS3_TOPEN_B2_*.json.

## 1. Verdict line
**Open: harness-primary 12 PASS and 23 CANDIDATE in 11,689 scored rows, ALL of them one idea (NQ 5-minute drive with |move| >= 0.5 x median 5-min opening range, first 1- or 3-minute pullback entry; DR5m_pb1/pb3_rm0.5); every OTHER family (3.1 OR breaks 7,200 cells, 3.3/3.4 gap and fade 360, 3.5-3.7 pullback/levels/IB 579, 3.8/3.9 pre-market and cross-asset 202, 3.10/3.11 confirmations 160 (2 CANDIDATE = the same cluster)) is 0 PASS / 0 CANDIDATE. Best NQ open book: DR5m_pb1_rm0.5 stop 60 / target 75, 2.3 trades/wk, +$4.7k (M) to +$5.3k (T) /wk added to the live stack (selection-window +$6.5-6.7k, holdout +$2.4-3.8k), vs same-rule-random-clock +17 pts [CI lower > 0], stack-add Sharpe +0.19 / +0.22 (WF), maxDD 76-81k better. Best other-instrument open: not run (block vii). Un-block comparison: un-blocking 09:30-09:59 of the existing books is worth +$5.8k/wk (WF; PRE +12.1k, HOLD -0.06k); the best candidate is -$1.1k / -$0.6k per week below it in mean (WF) but +76-81k better maxDD and positive in the holdout; no open book beats un-blocking with a confidence interval.**
Program-level best-of-N column in the verdict line: PASS/CANDIDATE labels counted against N = 11,292 registered cells (3.1 7,200 + 3.2 2,295 + block iii 896 + confirmations 160 + second opens 264 + the other families' cells are additional): null p95 about 140 pts of the pooled placebo cells; all 35 labels FAIL it.
HEALTH WARNING (kept visible): the PASS labels are from block (iii)'s 896-cell family (null p95 16 pts) and the cluster was picked from ~10,000 block-(ii) cells; against the program-level best-of-N (N = 10,868, p95 140 pts) all 35 labels FAIL, against the per-bracket-class secondary column the 12 block-(iii) PASS pass and all 10 block-(ii) CANDIDATEs fail; cell-level bootstrap z is 1.9-2.9 (Bonferroni needs ~4.4). Recommended status: forward-register (shadow) only.

## Counts by block (rows = block, harness-primary tier after the lower-of-two-bases rule)
| blk    |   CANDIDATE |   DEAD |   PASS |
|:-------|------------:|-------:|-------:|
| B3GRID |          11 |    871 |     12 |
| CONF   |           2 |    158 |      0 |
| DRbase |           0 |    288 |      0 |
| DRcond |          10 |   1997 |      0 |
| FADE   |           0 |    197 |      0 |
| GAP    |           0 |    163 |      0 |
| ORbase |           0 |    910 |      0 |
| ORcond |           0 |   5442 |      0 |
| ORre   |           0 |    848 |      0 |
| PB     |           0 |    579 |      0 |
| PM     |           0 |    201 |      0 |

## 2. Top 10 cells by stack-add Sharpe delta (WF, vs the live stack) regardless of verdict, with failed gate, MDE and forward weeks to settle
| cell | block | verdict | worst basis | stack d_Sharpe WF vs live | d_mean $/wk | MDE $/wk | fwd weeks | failed gates (worst basis) | HOLD d_Sharpe | 2023-span $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| DR10m_pb1_rm0.5__c3_X40_120 | B3GRID | DEAD | T | +0.425 | 9,164 | 5,611 | 53 | beats_c, beats_beta, span2, best_of_N | +0.41 | -1,803 |
| DR10m_pb1_rm0.5__c5_OH3 | B3GRID | DEAD | T | +0.423 | 9,891 | 7,378 | 79 | beats_b, beats_beta, stack_add_pre, best_of_N | +0.42 | 1,250 |
| DR10m_pb1_rm0.5__c3_X60_120 | B3GRID | DEAD | T | +0.413 | 9,067 | 6,570 | 75 | beats_b, beats_beta, stack_add_pre, best_of_N | +0.51 | 867 |
| DR10m_pb1_rm0.5__c4_X75_120 | B3GRID | DEAD | T | +0.391 | 8,446 | 6,807 | 92 | beats_b, beats_beta, stack_add_pre, best_of_N | +0.52 | 1,272 |
| DR10m_pb1_rm0.5__c5_OH2 | B3GRID | DEAD | T | +0.390 | 8,408 | 6,379 | 82 | beats_b, beats_beta, stack_add_pre, best_of_N | +0.34 | 921 |
| DR5m_pb3_rm0.5__c4_X75_120 | B3GRID | DEAD | T | +0.371 | 8,904 | 6,562 | 77 | span2 | +0.42 | -814 |
| DR10m_pb1_rm0.5__c5_AT0.5 | B3GRID | DEAD | T | +0.369 | 8,826 | 7,198 | 94 | beats_b, beats_beta, stack_add_pre, best_of_N | +0.39 | 1,649 |
| DR10m_pb1_rm0.5__c5_AT0.75 | B3GRID | DEAD | T | +0.358 | 9,246 | 7,874 | 103 | beats_b, beats_beta, stack_add_pre, best_of_N | +0.41 | 834 |
| DR10m_pb1_rm0.5__c5_AT1 | B3GRID | DEAD | T | +0.351 | 9,665 | 8,303 | 105 | beats_b, beats_beta, stack_add_pre, best_of_N | +0.40 | 70 |
| DR10m_pb1_rm0.5__c2_X30_120 | B3GRID | DEAD | T | +0.350 | 7,100 | 5,262 | 78 | beats_b, beats_c, beats_beta, span2, best_of_N | +0.37 | -1,075 |
These ten are all long-hold / wide-target 10-minute-drive cells: their stack gain is partly bracket beta (random-direction entries with the same long-hold exits earn +1.2k to +4.2k $/wk in the selection span); each fails the random-direction (beats_beta) or random-clock gate or the best-of-N line.
### Same ranking restricted to cells that do not fail beats_b / beats_beta
| cell | block | verdict | worst basis | stack d_Sharpe WF vs live | d_mean $/wk | MDE $/wk | fwd weeks | failed gates (worst basis) | HOLD d_Sharpe | 2023-span $/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| DR5m_pb3_rm0.5__c4_X75_120 | B3GRID | DEAD | T | +0.371 | 8,904 | 6,562 | 77 | span2 | +0.42 | -814 |
| DR5m_pb1_rm0.5__c5_AT0.75 | B3GRID | PASS | T | +0.330 | 9,545 | 7,784 | 94 |  | +0.25 | 670 |
| DR5m_pb1_rm0.5__c3_X60_120 | B3GRID | DEAD | T | +0.321 | 7,702 | 6,457 | 100 | span2 | +0.27 | -799 |
| DR5m_pb1_rm0.5__c5_AT1 | B3GRID | PASS | T | +0.308 | 9,503 | 8,244 | 107 |  | +0.25 | 1,192 |
| DR5m_pb1_rm0.5__c5_AT0.5 | B3GRID | DEAD | T | +0.302 | 8,371 | 7,328 | 109 | span2 | +0.20 | -300 |
| DR5m_pb3_rm0.5__c5_AT0.75 | B3GRID | DEAD | M | +0.293 | 9,671 | 7,951 | 96 | span2 | +0.17 | -319 |
| DR5m_pb1_rm0.5__c4_X75_120 | B3GRID | DEAD | T | +0.287 | 7,396 | 6,766 | 119 | beats_c, span2 | +0.28 | -1,844 |
| DR5m_pb3_rm0.5__c4_X75_90 | B3GRID | DEAD | T | +0.282 | 6,218 | 5,248 | 101 | span2, best_of_N | +0.32 | -624 |
| DR5m_pb1_rm0.5__c3_X40_120 | B3GRID | DEAD | T | +0.272 | 6,388 | 5,533 | 107 | beats_c | +0.21 | 1,473 |
| DR5m_pb1_rm0.5__c4_TM1300 | B3GRID | PASS | T | +0.271 | 7,649 | 7,398 | 133 |  | +0.15 | 769 |


## 3. RECOMMENDED-FOR-SIM opening book
DR5m_pb1_rm0.5 | stop 60 / target 75 (NQ, NT8 1-minute bars, window 09:35-10:29, 10 lots, the stack's per-book locks). Parameter-level spec: `autopilot/DS3_SPEC_TOPEN_DR5m_pb1_rm0.5_X60_75.md`. Forward-register entry ds3_TOPEN_DR5m_pb1_rm0.5_X60_75 (shadow). It is PASS(primary) on both bases, passes the class-null secondary, fails the program-level null; it is the cleanest member of the cluster (fixed bracket, small bracket beta).

## 4. The block question
Does any open book beat un-blocking KB/SM/ST in 09:00-10:00? Baselines (WF 142 weeks): live stack $44.9k/wk; with 09:30-09:59 un-blocked $50.7k (+5.8k, maxDD +23k worse, Sharpe 2.4 -> 2.6); D3SL as published (09:00-09:59 traded) $48.6k. The existing books' own 09:30-09:59 flips: PRE +12.1k/wk, WF +6.3k, HOLD -0.06k, 2023 span +0.4k, maxDD +99k worse. The DR5m cluster adds +3.5k to +9.2k/wk (WF) with 20-96k better maxDD and +1.8k to +8.8k in the holdout; against un-blocking: DR5m_pb3_rm0.5 HOLD-bracket +3.3-3.7k/wk better with 36k better maxDD, the fixed-bracket cells -0.2k to -2.8k/wk in mean with 40-96k better maxDD. Answer: not with a confidence interval; the open cluster is the only candidate that is level with un-blocking in mean, better in drawdown and better in the holdout. Everything else (3.1, 3.3-3.9) is worse than simply un-blocking.

## 5. Structural read
- Opening types: strict open-drive is too rare (1.4-6.8% of days) to carry a result; the cluster earns on OTD/ORR/OD days at the 09:35 cut, little on OA; high VIX negative. Continuation vs reversal: only drive CONTINUATION after a strong enough 5-10 minute drive pays (the mirror fade loses 5-9k/wk); OR breaks, gap plays, fades, first-pullback, level and IB cells, pre-market and cross-asset cells add nothing beyond bracket beta.
- Targets: the pay-off is convex trend capture: stack d_Sharpe rises with stop and target (60/120 best, 10-20 stops with small targets negative); fixed 60/75 is the cleanest cell; time exits 11:00-16:00 are the same idea with more bracket beta; scale-out and ATR targets work (ATR20 x 0.75/1 = hold-type).
- Bars/order types/tape: this study used 1-minute bars with market entries; delta/book confirmations (3.10/3.11) removed trades without adding weekly dollars; the 09:29 classifiers have no useful skill: direction (PRE AUC 0.483, HOLD 0.448); 4-class opening type (CLS4): accuracy 0.672 vs majority 0.675 (PRE), 0.616 vs 0.616 (HOLD), AUC for 'drive type' 0.549 PRE / 0.552 HOLD with CIs reaching 0.49-0.50 (permutation p 0.03 PRE, driven by pm_pos / ORR AUC 0.67 PRE, 0.64 HOLD), gated P&L inside noise (HOLD gated - ungated -4 to +24 pts, all CIs include 0). Not yet run: other bar types, limit/stop-limit/OCO order types, footprint standalone triggers, L2 triggers, direct L2 replay.
## 6. Cross-instrument table (block vii, prereg SECONDOPENS master sha256 01a58565..., 264 cells = 11 opens x 4 signals x 6 brackets, 11 holdout looks; bar-based conservative tick basis, WEAK fee labels on RTY / YM / CL / GC / SI / ZN, 6E fee WEAK; pre-lock series added to the live stack; margin and the 50-cap not modelled)
**0 PASS, 0 CANDIDATE, 264 DEAD.** Best-of-N null p95 (effect vs random clock, 10-lot-equivalent pts): family 25.6, program-level (N=11,292) 28.4, per class target 10.2 / time 12.7 / hold 25.6.
| open | cells | median stack d_Sharpe (WF) | share d_Sharpe>0 | median stand-alone WF $/wk |
|---|---|---|---|---|
| NQ 03:00 + 09:30 (48) | 48 | -0.180 | 0.31 | -559 |
| ES 09:30 | 24 | -0.213 | 0.13 | -1,418 |
| RTY 09:30 | 24 | -0.110 | 0.25 | -684 |
| YM 09:30 | 24 | -0.254 | 0.04 | -2,430 |
| CL 09:00 | 24 | -0.288 | 0.00 | -4,731 |
| GC 08:20 | 24 | -0.178 | 0.04 | -1,487 |
| SI 08:20 | 24 | -0.928 | 0.00 | -16,048 |
| ZN 08:20 | 24 | -0.488 | 0.00 | -9,229 |
| 6E 03:00 + 08:30 (48) | 48 | -0.222 | 0.00 | -3,684 |
The only positive structure is the NQ 09:30 15-minute drive (DRV15c with S1T1.5 / S1T2 / S1TM60 / S1HOLD: stack d_Sharpe +0.22 to +0.26, WF +$5.9k to +$9.0k/wk, effect vs random clock +13 to +22 pts rank 1.00; they fail span2 or beats_beta and best_of_N; the first three pass the per-class secondary), i.e. the block-(ii) drive result reappearing on a bar-only basis; RTY 09:30 ORb15 S1HOLD +0.15 is bracket beta (fails beats_b / beats_beta). No other instrument's open shows a cell above the placebo lines; costs of the thin instruments (SI, ZN, CL) dominate their small ranges (R5 costs 8-30% of risk). An open edge that exists on all four index futures is therefore NOT supported: ES, RTY, YM do not replicate the NQ drive cell. Portfolio-of-opens sleeve (x): not formed (no positive cell to pool).
## 7. Fill cost and capacity (tape-book walk, not a replay): 10 lots at 09:35-09:59 cost +1.3 ticks beyond the touch at entry (p90 2.0), +1.0 tick at a 15:59:59 exit; fill-cost-by-second and the capacity curve from the real book at the entry second need the direct replay (queue it: open_direct.py orch). Concurrency with the live stack: the 50-contract cap is exceeded on 2.4-2.7% of trades (cap cost <= 6.4% of the cell's P&L); margin proxy about $1.2M at the 57-lot peak (flag).
## 8. Power statement per family
3.1 / 3.2 / block iii: stack weekly-mean MDE 3-10k $/wk per cell (PRE 75 weeks), per-trade 6-12 pts, family-wise nulls over 7,668 / 2,304 / 896 cells; 3.3/3.4 MDE 5-9k; 3.5-3.7 5-10k; 3.8/3.9 6-10k (their reports). A null here reads: could not see a stack gain below roughly 5-8k $/wk for a single cell, and no family cleared the program-level line. Forward weeks for the cluster to settle: 120-190.
## 9. Deviations/disclosures: see DS3_OPEN_B2_HARNESS.md section 2/5, DS3_OPEN_B2_OR_DRIVE.md section 9/10 and DS3_OPEN_B2_OR_DRIVE_B3.md section 6, and DECISIONS.md (ORbase pre-text rewrite, min_n gate, harness price-space fix).
