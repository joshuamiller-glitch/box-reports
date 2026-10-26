# DS3_PORTFOLIO - EDITION 2 (D3L, 2026-10-26; edition 1 kept as DS3_PORTFOLIO_ED1.md). Research only; no spec is a live recommendation.
Edition 2 is a SECOND scoring of the DS3 pool: prereg l2vast/ds3/prereg/T-G2_prereg.md sha256 a355001dc65c3b099ce1155a7232a31ccb9ddc316ddb5d82165b8d7ca640c738 (15 cells, ledger 31,138, DECISIONS.md), written before scoring; it adds the T-ENTRY direct-L2 PASS series (D3E) to the pool. Pre-holdout text autopilot/DS3_TG2_PREHOLD.md, second holdout look logged (track DS3_TG2). Code l2vast/ds3/code/tg2_run.py, numbers l2vast/ds3/out/TG2_final.json, rows l2vast/ds3/rows/DS3_TG2.json.

## Verdict line
DS3 books: 2 PASS, 1 CANDIDATE: PASS TE7_kelt3m_n14_m1.0, TE6_st10m_n7_m3.0; CANDIDATE TE7_emax5m_f30_s50. DS2 alone: $25,840/wk, SD 106,637, maxDD 537,851. DS2+DS3: $39,391/wk, SD 123,683, maxDD 518,953, worst week -261,281, CI [8,401, 18,767], placebo r 1.000 (WF; holdout 0.994), holdout + (DS2+DS3 $38,598/wk vs DS2 $27,848, diff +$10,750, CI [3,255, 18,600]), peak lots 50 (DS2 27 + DS3 23; sum of book peaks).

## Pool, duplicates and selection
Pool (no privilege): ST10, HM10, WT7, TB1_ST_k15, TB7_ORBNY_k3, TB9_RENKO_c2 (T-B, exact 1-s locks), and the five distinct T-ENTRY PASS series: TE6_st10m_n10_m3.0 (== TE1_st_10m), TE6_st10m_n7_m3.0, TE6_st10m_n14_m3.0, TE7_emax5m_f30_s50, TE7_kelt3m_n14_m1.0 (10 lots, exact 1-s locks, direct-L2 S10x1 + XJ3 stop-join pricing). ST is counted once. Weekly corr WF: the three st10m cells are one cluster (n10-n7 0.81, n14-n7 0.66, n10-n14 0.78), so the 0.5 cap admits one (n7, the most distinct). D3X duplicate test vs live WT10 (10-min Wilder ATR14 x3.0 trail): rule DISTINCT (Supertrend on hl2 with ATR seeded H-L, flips on the current-bar band, no 09:00-09:58 blackout) but partly redundant: n7 shares a 10-min bar and side with a WT10 entry on 40% of its trades (51% within one bar), n10 49%, n14 59%; unlocked weekly corr 0.52 / 0.61 / 0.67 (box WF weekly corr of the locked series 0.54-0.65). So st10m is a neighbour of the already-scored WT10 family, not a new edge (V2 "no re-test under a new name"); n10 and n14 are not independent of n7 or of WT10 and are not counted as separate books. WT10 itself is not in the pool (library 8-lot series, not an exact-engine series).
Selection (WF-PRE only, greedy, corr cap 0.5, Sharpe must rise): **TE7_kelt3m_n14_m1.0, TE6_st10m_n7_m3.0, TB7_ORBNY_k3_P60_N** (WF-PRE portfolio Sharpe 3.37). ST10, HM10 and WT7 are NOT in the DS3 set (adding ST lowers WF-PRE Sharpe by 0.07 and raises WF/HOLD by 0.11/0.30; HM -0.06 WF; WT -0.46). **ST and HM are not in the DS3 set.** TB7 is carried because the prereg selected it, but in the final windows it is a negative contributor (LOO Sharpe -0.10 WF / -0.32 HOLD; without it the set scores WF 2.97, HOLD 2.60).

## Three lines on identical windows and cost (WF = 142 weeks 2024-02..2026-10; DS3 = TE7_kelt3m_n14_m1.0 + TE6_st10m_n7_m3.0 + TB7_ORBNY risk-parity, monthly weights)
| line | WF $/wk | SD | Sharpe | maxDD | worst wk | L8W $/wk | HOLD $/wk (Sharpe) | HOLD maxDD | 2023-04..24-01 $/wk | WF diff vs DS2 [CI] (MDE) | HOLD diff [CI] | WF 1.5x / 2x | avg lots | peak lots |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DS2 alone (ST10/HM10/WT7 per-book) | 25,840 | 106,637 | 1.75 | 537,851 | -221,854 | 17,643 | 27,848 (1.77) | 498,491 | 11,156 | - | - | 20,986 / 13,758 | 27 | 27 |
| DS3 alone, equal weekly SD | 42,461 | 106,637 | 2.87 | 481,735 | -191,980 | 55,303 | 33,684 (2.28) | 481,735 | 13,661 | +16,621 [-20, 33,639] (24.0k) | +5,836 [-19,310, 30,967] | 36,781 / 30,962 | 39.8 | 72 (> 50) |
| DS3 alone, same contract-equivalent budget (27) | 28,820 | 72,379 | 2.87 | 326,972 | -130,304 | 37,536 | 22,862 (2.28) | 326,972 | 9,272 | +2,980 [-10,968, 17,312] (20.0k) | -4,985 [-25,460, 15,631] | 24,965 / 21,015 | 27.0 | 49 |
| DS3 alone, half the equal-SD scale | 21,231 | 53,319 | 2.87 | 240,868 | -95,990 | 27,651 | 16,842 | 240,868 | 6,831 | -4,609 [-17,482, 8,750] | -11,006 [-29,810, 8,164] | 18,391 / 15,481 | 19.9 | 36 |
| DS2 + DS3 (DS3 at peak 23, cap 50) | 39,391 | 123,683 | 2.30 | 518,953 | -261,281 | 35,293 | 38,598 | 518,953 | 15,516 | +13,551 [8,401, 18,767] | +10,750 [3,255, 18,600] | 32,724 / 23,640 | 38.1 | 50 |
DS3 lots (average NQ lots, WF): equal-SD kelt 10.5, st10m 16.4, TB7 12.9; 27-contract line 7.1 / 11.1 / 8.7; half-SD 5.2 / 8.2 / 6.4; inside DS2+DS3 3.4 / 5.2 / 4.1. Peak lots = sum of book peaks (10 per T-ENTRY book, TB7 20): an upper bound; no interval table exists for the T-ENTRY books and none exists for DS2 ST/HM/WT, so a concurrency replay was not feasible. **The equal-SD DS3 line needs 40 average lots and breaches the 50 cap on this bound (72), so it is not a feasible account line; the 27-contract line (49) is.** Weekly SD difference DS2+DS3 vs DS2: CI [11,988, 21,999]; weekly corr DS3 vs DS2 0.38 (set vs DS2 books: kelt 0.40, st10m 0.08, TB7 0.22).

## Which line is best (WF unless stated)
- mean: DS2+DS3 (39,391) > DS3 equal-SD (42,461 is highest in raw terms but infeasible under the cap) > DS3 at 27 lots (28,820) > DS2 (25,840) > half-SD.
- SD: DS3 at 27 lots 72,379 (-32% vs DS2) < DS2 106,637 < DS2+DS3 123,683.
- maxDD: DS3 at 27 lots 326,972 (-39% vs DS2) < DS3 equal-SD 481,735 < DS2+DS3 518,953 < DS2 537,851.
- worst week: DS3 at 27 lots -130,304 < DS3 equal-SD -191,980 < DS2 -221,854 < DS2+DS3 -261,281.
- L8W: DS3 (37.5k at 27 lots, 55.3k equal-SD) > DS2+DS3 35.3k > DS2 17.6k.
- holdout mean: DS2+DS3 38,598 > DS3 equal-SD 33,684 > DS2 27,848 > DS3 at 27 lots 22,862. Holdout Sharpe 2.28 vs 1.77.
- CI of difference vs DS2 alone: DS3 at 27 lots [-10,968, +17,312] and DS3 equal-SD [-20, +33,639] include 0 (MDE 20-24k, the weekly test cannot resolve a $3-17k difference); DS2+DS3 [+8,401, +18,767] excludes 0, but carries +$17k SD and a worse worst week.
- Reading: at the same 27-contract budget DS3 is not distinguishable from DS2 on mean (+$3.0k, CI includes 0, holdout mean -$5.0k) but is much lower-risk (SD -32%, maxDD -39%, worst week -41%, L8W better, 2023-04..24-01 +$9.3k vs +$11.2k): a risk-efficiency gain, not an income gain. DS3 does not give DS2's mean at DS2's risk inside the 50-contract cap: raising DS3 to DS2's SD needs 40 lots. Cost: DS3 loses 14% at 2x (28,820 -> 21,015 at 27 lots; equal-SD 42,461 -> 30,962) vs DS2 -47% (25,840 -> 13,758): the T-ENTRY books are less cost-sensitive in the model (their 1.5x/2x series are approximations, see caveats).

## Other sets (equal SD / 27 contracts)
ST+HM+WT risk parity $22,047 / 21,147, Sharpe 1.49 (worse than DS2 10/10/7 sizing); all 10 books risk parity $38,244 (maxDD 476,536, Sharpe 2.59, 44 avg lots) / 23,330 (maxDD 290,700); selected set at equal risk weights $40,779 (maxDD 534,396, Sharpe 2.76) / 27,391 (maxDD 358,956).
Leave-one-out marginal Sharpe (WF / HOLD / WF-PRE): TE7_kelt3m +0.90 / +0.53 / +1.22; TE6_st10m_n7 +0.68 / +0.78 / +0.60; TB7 -0.10 / -0.32 / +0.13. Portfolio Sharpe WF-PRE 3.37, WF 2.87, HOLD 2.28, L8W 7.87 vs DS2 1.72 / 1.75 / 1.77 / 0.85.

## Placebo, DSR, selection inflation (read before trusting the Sharpe)
Placebo: 500 portfolios of 3 random library books (same scaling and corr cap): WF rank 1.000 (median -0.68, p95 0.92), holdout 0.994: an easy null. DSR 0.92 at cumulative N = 31,138 (sr_var 0.0025); D3E's own DSR for the T-ENTRY cells was 0.56-0.96 at 191 trials. The two main books were picked as winners of a 191-cell T-ENTRY search (38 direct replays chosen on mapped PRE/holdout), then again as winners of the 10-book WF-PRE selection, and WF contains WF-PRE (selection window); D3E also saw the holdout when choosing the 38 cells to replay. So the WF Sharpe 2.87 and holdout 2.28 are optimistic; the cleanest out-of-selection evidence is the 2023-04..2024-01 span (portfolio +$13.7k/wk equal-SD, positive; kelt +6.4k, st10m_n7 +3.5k, TB7 -0.1k) and forward trading, of which none exists (0 forward weeks).

## Books against the DS3 bar
| book | holdout>0 | corr<=0.5 | marginal Sharpe up (LOO or add-one, WF / HOLD) | tr/wk | NT8 exec (entry+exit mismatch) | placebo>=.95 | 2023-04..24-01 | status |
|---|---|---|---|---|---|---|---|---|
| TE7_kelt3m_n14_m1.0 | 12,773 | yes (max 0.33) | +0.90 / +0.53 | 26.8 | DELIVERABLE 0.83% | 1.00 (D3E) | +6,365 | **PASS** |
| TE6_st10m_n7_m3.0 | 9,423 | yes (max 0.09) | +0.68 / +0.78 | 12.2 | DELIVERABLE 1.05% | 1.00 | +3,468 | **PASS** (family-redundant with WT10: corr 0.54) |
| TE7_emax5m_f30_s50 | 10,120 | yes (max 0.31) | add-one +0.07 / +0.38, WF-PRE -0.22 | 11.8 | DELIVERABLE 1.38% | 0.97 | +1,349 | **CANDIDATE** (fails only marginal Sharpe at WF-PRE) |
| TE6_st10m_n10_m3.0 / n14_m3.0 | 9,596 / 7,258 | no (0.81 / 0.66 vs n7) | add-one -0.07 / -0.23 | 12.1 / 12.2 | DELIVERABLE | 0.97 | +9,914 / +6,761 | same cluster as n7, not counted |
| TB7_ORBNY_k3_P60_N | 4,812 | yes | -0.10 / -0.32 FAIL | 6.0 | DELIVERABLE | 1.00 | -137 FAIL | DEAD (was CANDIDATE in ed.1) |
| ST10 | 16,463 | yes | add-one +0.11 / +0.30 (WF-PRE -0.07) | 26 | live | 0.68 FAIL | +6,055 | CANDIDATE in ed.1; ed.2 not in set (placebo + marginal fail): DEAD for DS3 |
| HM10, WT7, TB1, TB9c2 | 10,598 / 786 / 11,521 / 6,037 | - | negative | - | - | - | +3,808 / +1,293 / -3,101 / -5,245 | not in set |

## 3x3 widening grids (addendum 2), reported whole (D3E ran them as TE7 / TE6; all neighbours scored identically)
TE7_kelt3m (n in 14/20/30 x mult 1.0/1.5/2.0), direct-L2, columns WF $/wk | WF-PRE $/wk | 2023-04..24-01 $/wk | verdict: n14_m1.0 16,863 | 20,298 | +6,365 | PASS; n20_m1.0 17,235 | 18,528 | -6,667 | CANDIDATE; n30_m1.0 13,603 | 12,607 | -11,612 | CANDIDATE; n14_m1.5 8,453 | 12,382 | -3,995 | CANDIDATE; n20_m1.5 13,416 | 19,976 | -4,068 | CANDIDATE; n14_m2.0 8,565 | 6,947 | -2,769 | DEAD; n20_m2.0 7,586 | 8,612 | -1,088 | DEAD; n30_m1.5 and n30_m2.0 are not in the replayed 38 (see DS3_TENTRY.md). Not isolated: every replayed grid cell is positive in WF and WF-PRE, but 6 of 7 replayed neighbours are negative in 2023-04..2024-01 (only n14_m1.0 is positive), so the PASS depends on the one cell that passes the second holdout: fragile.
TE6_st10m (n in 7/10/14 x mult 2.5/3.0/3.5), same columns: n7_m3.0 PASS 8,749 | 8,743 | +3,468; n10_m3.0 PASS 8,799 | 8,979 | +9,914; n14_m3.0 PASS 6,980 | 7,630 | +6,761; n10_m3.5 CANDIDATE 5,304 | 5,853 | +4,114; n14_m2.5 DEAD 7,373 | 6,851 | +5,850 (other cells not replayed). Not isolated (3 PASS, 1 CANDIDATE); positive in all three windows.

## Caveats
- T-ENTRY 1.5x/2x daily series were not on disk: built as the 1x series less a uniform per-active-day cost so the WF mean equals D3E's reported 2x mean (1.5x at the midpoint). All other cost lines are exact-engine (DS2, TB).
- The T-ENTRY series rely on the direct-L2 execution layer (S10x1 slicing, XJ3 stop-join): second-level timers, unvalidated live; D3X's identity tests cover the signal and bracket only (mismatch 0.83-1.38%).
- Peak lots are sum-of-peak bounds; a real concurrent-position replay (interval tables) exists only for the T-B books.
- Weights scale post-lock P&L proportionally (no integer-lot/P9 size-table re-run).
- Portfolio Sharpe 2.87 is selection-inflated (see above); treat DS3 vs DS2 as a hypothesis for forward paper trading, not a result.
- No book is a live recommendation; anything run goes to the Sim leader first.

## Running scorings (re-scored after each addendum-2 track; every one re-reads the holdout; running list, newest last)
| label | new books | selected set | Sharpe WF / HOLD | 27-contract line WF mean / SD / maxDD | equal-SD mean | DS2+DS3 mean / SD / maxDD | placebo rank | DSR | ledger N |
|---|---|---|---|---|---|---|---|---|---|
| TG3_1 | TE2_GC_KEL_k15, TE2_GC_VWAP_k15 | TE7_kelt3m_n14_m1.0, TE6_st10m_n7_m3.0, TB7_ORBNY_k3_P60_N, TE2_GC_VWAP_k15 | 2.96 / 2.44 | 24,601 / 59,839 / 325,693 | 43,841 (peak 101) | 35,814 / 116,683 / 473,149 | 1.000 | 0.93 | 34941 |
Note on TG3_1 (after E2/E3): the only new book selected is TE2_GC_VWAP_k15 (GC, MAPPED basis, 2023-04..24-01 -$20.4k/wk, D3INS does not recommend it, DSR 0.02-0.03). Its lots are GC contracts entered as NQ-equivalent lots (GC notional about 0.64 NQ per contract; the 50-cap bound 101 is therefore overstated or understated by that factor and is not comparable). The Sharpe gain (WF 2.96 vs 2.87, HOLD 2.44 vs 2.28) comes from a book that fails the second-holdout sign and the basis requirement: do not read TG3_1 as an improvement; the running best portfolio remains T-G2 (TE7_kelt3m_n14_m1.0 + TE6_st10m_n7_m3.0 + TB7).

## Track D (D3SZ: sizing, lock parameters, allocation, capacity), reports DS3_TD1..TD4.md, best line l2vast/ds3/out/D3SZ_BEST_LINE.md
- D1 ATR-targeted lots: 14 cells DEAD (proportional de-leveraging, as T-J). D2 per-book lock grids: 126 cells, 0 PASS, 1 CANDIDATE (TE7_emax5m at arm 3R / keep 67% / floor 16R, +$338/wk: not adopted over the shared lock 2R/50%/12R). D3 allocation: equal lots, risk parity and Sharpe-weighted all DEAD; risk parity ~ equal lots in Sharpe with lower maxDD and slightly lower mean; Sharpe-weighting worse. No new book, so no portfolio re-scoring was triggered by track D.
- D3SZ best sizing line (the three T-ENTRY books kelt3m, st10m_n7, emax5m at 9/9/9 equal lots = 27 contracts): WF $30,204/wk, SD 71,956, maxDD 312,267, holdout $29,085. This is comparable with the T-G2 27-contract line ($28,820, SD 72,379, maxDD 326,972, holdout $22,862; same selection-inflation caveat) and is a simpler, fixed-lot implementation.
- D4 concurrency (interval replay): peak lots DS2 27; DS2 + (kelt, st10m_n7, emax5m at 10 lots each) = 57, above 50 for 9.2% of the time; at 5 lots each 42. So the DS2+DS3 line in this file (DS3 at 23 NQ-eq by the sum-of-peaks bound) respects the cap by construction, while 10-lot books on top of DS2 do not. The margin proxy is an assumption (no margin file on disk).
