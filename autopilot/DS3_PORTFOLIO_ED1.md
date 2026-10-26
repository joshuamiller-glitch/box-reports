# DS3_PORTFOLIO - DS2 alone vs DS3 alone vs DS2+DS3 (D3L, 2026-10-26; research only, no spec is a live recommendation)
Prereg l2vast/ds3/prereg/T-G_prereg.md sha256 c821879363ebdddd58aaf337e4babcb0d2fce196743ee5ad14454ab0573388c4 (16 cells, DECISIONS.md; ledger 31,123). Pre-holdout text autopilot/DS3_TG_PREHOLD.md, holdout look logged once (DS3_TG). Code l2vast/ds3/code/tg_run.py; full numbers l2vast/ds3/out/TG_final.json; rows l2vast/ds3/rows/DS3_TG.json. Edition 1 (T+~1 h on the box clock; updated if later tracks add books).

## Verdict line
DS3 books: 0 PASS, 2 CANDIDATE: ST10 (the DS2 ST book, fails only the per-book timing placebo, 0.68), TB7_ORBNY_k3_P60_N (fails only the 2023-04..2024-01 sign, -$137/wk). DS2 alone: $25,840/wk, SD 106,637, maxDD 537,851. DS2+DS3: $36,276/wk, SD 139,590, maxDD 620,551, worst week -303,652, CI [4,418, 16,477] (difference vs DS2 alone, 8-wk block bootstrap, 10,000 draws), placebo r 0.992 (WF Sharpe rank among 500 random library portfolios; weak null, see caveats), holdout + (HOLD diff +$9,805/wk, CI [1,524, 18,392]), peak lots 50 (upper bound = DS2 27 + DS3 23).

## What DS3 is (selection fixed by the prereg on WF-PRE only)
Pool (no privilege): ST10, HM10, WT7 (DS2 per-book locks), TB1_ST_k15, TB7_ORBNY_k3, TB9_RENKO_c2, TB9_RENKO_c5 (exact 1-s lock re-score by D3B; c5 is DEAD after it). Greedy forward on risk-parity Sharpe with between-book corr <= 0.5: **ST10, TB7_ORBNY_k3_P60_N, TB9_RENKO_c2_k1_P60_N**. **ST is in the DS3 set; HM and WT are not** (adding HM or WT does not raise the WF-PRE portfolio Sharpe under the 0.5 cap; HM corr 0.49 with the Renko book). No T-A/C/D/E/H/I/J/K cell is a book (all DEAD); TF1_FOMC_NY is a filter, not a book. Risk-parity weights are monthly, inverse trailing-26-week SD; the per-book locks (day -2R/+5R, give-back 2R keep 50%, week floor 12R, R = 12,000) are inside each book series (DS2 exact engine; TB books exact 1-s engine via asm_lib).

## Three lines on identical windows and cost (WF = 142 weeks 2024-02..2026-10; Sharpe annualised weekly; costs: live, 1.5x, 2x)
| line | WF $/wk | SD | Sharpe | maxDD | worst wk | L8W $/wk | HOLD $/wk | HOLD maxDD | diff vs DS2 WF CI | HOLD diff [CI] | WF 1.5x / 2x | avg lots | peak lots (upper bound) | 2023-04..24-01 $/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DS2 alone (ST10/HM10/WT7 per-book) | 25,840 | 106,637 | 1.75 | 537,851 | -221,854 | 17,643 | 27,848 | 498,491 | - | - | 20,986 / 13,758 | 27.0 | 27 | 11,156 |
| DS3 alone, equal weekly SD | 27,384 | 106,637 | 1.85 | 640,166 | -214,646 | 71,067 | 25,730 | 437,570 | [-12,789, 16,519] | -2,117 [-21,739, 18,269] | 21,746 / 15,943 | 29.2 | 60 | -156 |
| DS3 alone, same contract-equivalent budget (27) | 25,317 | 98,589 | 1.85 | 591,851 | -198,446 | 65,704 | 23,788 | 404,545 | [-14,140, 13,737] | -4,059 [-22,798, 15,477] | 20,105 / 14,740 | 27.0 | 56 | -144 |
| DS3 alone, half the equal-SD scale | 13,692 | 53,319 | 1.85 | 320,083 | -107,323 | 35,534 | 12,865 | 218,785 | [-23,586, -34] | -14,983 [-31,303, 1,661] | 10,873 / 7,972 | 14.6 | 30 | -78 |
| DS2 + DS3 (DS3 at peak 23, cap 50) | 36,276 | 139,590 | 1.87 | 620,551 | -303,652 | 44,725 | 37,653 | 620,551 | [4,418, 16,477] | 9,805 [1,524, 18,392] | 29,273 / 19,834 | 38.1 | 50 | 11,096 |

Same-weekly-SD scale: DS3 lots (average NQ lots in the WF window) ST 9.0, TB7 11.0, TB9c2 9.2 (29.2 lots); contract-equivalent line ST 8.3, TB7 10.2, TB9c2 8.5 (27.0); half-SD line 4.5/5.5/4.6 (14.6); DS3 inside DS2+DS3 3.4/4.2/3.5 (11.1). "Peak lots" is the sum of book peaks (ST 10, TB7 20, TB9c2 20 at nominal; a conservative upper bound: ST/HM/WT concurrency is capped by the engine and the real concurrent maximum is lower). The equal-SD and contract-matched DS3 lines exceed 50 on this bound (60 and 56); only the 23-lot DS3 respects the cap by construction. Margin proxy: contracts only (no margin figure exists on the box).

## Which line is best (WF unless stated)
- mean: DS2+DS3 (36,276) >> DS3 equal-SD (27,384) > DS2 (25,840) > DS3 at 27 lots (25,317) > half-SD (13,692).
- SD: lowest is half-SD DS3 (53k) by construction; at full size DS3 at 27 lots 98.6k < DS2 106.6k = DS3 equal-SD < DS2+DS3 139.6k.
- maxDD: DS2 alone is best at full size (537,851); DS3 equal-SD 640,166 (+102k), DS3 at 27 lots 591,851, DS2+DS3 620,551. In the holdout the DS3 lines have the smaller maxDD (437.6k / 404.5k vs 498.5k).
- worst week: DS3 at 27 lots (-198,446) < DS3 equal-SD (-214,646) < DS2 (-221,854) < DS2+DS3 (-303,652).
- L8W: DS3 (71,067 equal-SD, 65,704 at 27 lots) vs DS2 17,643 (the DS3 books are carried by TB9c2's last 8 weeks, +60k/wk: 8 weeks is one episode).
- holdout (2025-07+): DS2+DS3 (37,653) > DS2 (27,848) > DS3 equal-SD (25,730) > DS3 at 27 lots (23,788).
- CI of the difference vs DS2 alone (WF): DS3 equal-SD [-12,789, +16,519] and DS3 at 27 lots [-14,140, +13,737] include 0 (MDE 20.9k / 19.9k: the weekly test cannot see a difference of this size); half-SD [-23,586, -34] is negative as expected; DS2+DS3 [+4,418, +16,477] excludes 0.
- Replacement test: **DS3 is not shown better than DS2 as a replacement.** At equal weekly SD DS3 has Sharpe 1.85 vs 1.75 (difference not distinguishable from 0), a 19% larger maxDD, a lower holdout mean, and the 2023-04..2024-01 span is negative for the portfolio (-$156/wk vs DS2 +$11,156/wk), which fails the second-holdout sign bar. DS2+DS3 raises the mean by $10.4k/wk (CI excludes 0, holdout agrees) but at +$33k SD (CI [27.4k, 38.1k]), +$83k maxDD and a worse worst week; Sharpe moves 1.75 -> 1.87; weekly corr DS2 vs DS3 0.75 because ST is in both (the gain is mostly more ST exposure plus two small books).
- Cost: WF mean at 1.5x/2x: DS2 20,986 / 13,758; DS3 equal-SD 21,746 / 15,943 (relatively less cost-sensitive, TB books are 6-13 trades/wk); DS2+DS3 29,273 / 19,834.

## Leave-one-out (marginal portfolio Sharpe, risk-parity, scale-invariant; WF / HOLD / WF-PRE)
ST +0.45 / +0.63 / +0.27; TB7_ORBNY +0.21 / +0.03 / +0.37; TB9_RENKO_c2 +0.007 / -0.049 / +0.05 (adds nothing; negative in holdout). Portfolio Sharpe WF 1.85 (WF-PRE 1.92, HOLD 1.75, L8W 4.07) vs DS2 1.75 (1.72, 1.77, 0.85) and ST/HM/WT risk-parity 1.49. Other sets at equal SD: ST+HM+WT risk-parity $22,047/wk, maxDD 651,936, Sharpe 1.49 (worse than DS2 10/10/7: the per-book DS2 sizing is better than risk-parity weights); all-7 pool $22,357, maxDD 477,638, Sharpe 1.51; selected set at equal risk weights $25,776, Sharpe 1.74.

## Placebo, DSR
Placebo: 500 portfolios of 3 random library books (deduped eligible census pool, re-costed pnl_live, each scaled to the WF weekly SD of its counterpart book, between-book corr cap 0.5, same monthly risk-parity): the real set's WF Sharpe 1.85 ranks 0.992 (holdout 0.978); placebo median -0.68, p95 0.92. Caveat: the null draws from a pool where 19,760 of 31,081 series fail holdout, so it is an easy null; the timing-destroyed null of T-B (rank 1.0 per cell) and the census best-of-library result (31k series at chance) say the selection effect is large. DSR of the DS3 weekly series 0.35 at N = 31,123 cumulative trials (below any conventional bar).

## Books against the DS3 inclusion bar (D3X specs: autopilot/DS3_SPEC_*.md; weekly corr table in DS3_BOOKS.md)
| book | holdout>0 | corr<=0.5 | LOO Sharpe up | >=3 tr/wk | NT8 executable | placebo>=.95 | 2023-04..24-01 | status |
|---|---|---|---|---|---|---|---|---|
| ST10 | 16,463 | yes | +0.45 | 26 | yes (live book) | 0.68 (census timing null) FAIL | +6,055 | CANDIDATE |
| TB7_ORBNY_k3_P60_N | 4,812 | yes | +0.21 (hold +0.03) | 6.0 | yes (0.00% mismatch) | 1.00 | -137 FAIL | CANDIDATE |
| TB9_RENKO_c2_k1_P60_N | 6,037 | yes | +0.007 (hold -0.05) FAIL | 13.1 | yes (1.04% vs causal rule) | 1.00 | -5,245 FAIL | DEAD (lock-dependent: unlocked WF -2,427) |
| TB1_ST_k15_P60_N | 11,521 | yes | not selected, pair Sharpe down FAIL | 14.2 | yes | 1.00 | -3,101 FAIL | DEAD |
| HM10 | 10,598 | 0.49 vs Renko | not selected FAIL | 23.9 | yes (live book) | 0.62 FAIL | +3,808 | DEAD for DS3 (not in set) |
| WT7 | 786 | yes | not selected FAIL | 38.2 | yes | 0.39 FAIL | +1,293 | DEAD for DS3 |
The portfolio scored above is the pre-registered selection (ST, TB7, TB9c2); TB9c2 is carried in the scored lines although it fails the book bar individually (its weight is zero-value: LOO +0.007). No PASS exists, so no 3x3 widening grid was triggered. No register to PAPER-ALL beyond the T-B cells D3B already registered (ST is live).

## Caveats
- Weights scale post-lock daily P&L proportionally; integer-lot rounding and the P9 size table are not re-run for the portfolio lots. DS2 locks are exact-engine series; TB books use the exact 1-s lock re-score by D3B (the lock window for stop/target exits runs to the end of the exit bar). The between-book (DS2 vs DS3) lock interaction does not exist by design (per-book locks).
- Peak lots is the sum of book peaks, not a concurrency replay (DS2 ST/HM/WT interval tables are not on disk; TB interval tables are).
- The T-G rerun fixed a numerical bug in the placebo weights (zero-variance trailing windows); the selection and portfolio numbers were unchanged by it. Holdout was looked once.
- Several tracks were still reporting (T-H/T-I/T-K: all DEAD at writing); a later PASS/CANDIDATE would reopen the pool (this edition scored once on the pool as of now).
