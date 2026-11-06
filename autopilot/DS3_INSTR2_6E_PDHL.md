# DS3_INSTR2_6E_PDHL - ONE post-hoc best-of-F test of the 6E pdhl_break cell picked after the bad-print repair (S4a, 2026-11-06)
Research only, Shadow only, no PASS claims, no purchase. Prereg l2vast/ds3/prereg/T2_6E_PDHL_POSTHOC.md sha256 95526298b1fb0746198f28675179980e7a8297d19442759a281cbbfa7e921b0a (DECISIONS.md, filed before any statistic; **POST-HOC**: the cell was picked by CHAR-C from the repaired pre-2023 year tables of the 90 tolerant 6E block-B cells, DATA_BAD_PRINTS.md). Cell: pdhl_break, rth 570-960, x_atr 0.25, session pre (08:30-09:30 ET), stop 4 ATR, no target, time stop 90 min, equal-$ risk $1,200, integer lots, cap 16. Base: repaired 6E 1-min (find_c/cache_c/6E.npz) 2013-2026-10-16, unadjusted frame with equal-$ lots, ZL-2 cost proxies, evaluator instr2_eval.py (BASE-4). Code l2vast/ds3/code/t2s4a/pdhl6e.py; results /mnt/l2/l2vast/ds3_t2/PDHL6E_eval.pkl and PDHL6E_null.pkl.

## Plain sentence
**The repaired 6E prior-day-break pre-market cell is not a lead: its pre-2023 gain (+$2,860 over 10 years, 5 of 10 years positive) is what the best of 90 cells produces by chance (selection-aware p 0.50), it has only 297 trades in 13 years so it fails the evaluator's minimum-sample gate, the forward-only placebo p_book is 0.78, the family p is 1.00, the walk-forward is negative, and only 2 of its 5 one-step neighbours are positive before 2023, so there is no plateau. Label: NULL / best-of-F.**

## Results (tests T1-T5 of the prereg)
* T1 windows and years: tolerant gate flag true (NOW-ONLY), gate_v2a false for minimum sample (L3M 5 of 10 trades, L6M 8 of 20, PRE 39 of 60, X' 25 of 40). Years (net $): 2013 -5,584; 2014 -9,776; 2015 +10,724; 2016 +6,610; 2017 +1,526; 2018 -3,123; 2019 -5,444; 2020 -1,030; 2021 +5,876; 2022 +3,080 (sum +2,860, 5 of 10); 2023 +4,891; 2024 +5,821; 2025 +6,931; 2026 -1,945.
* T2 forward-only placebos (shift5 / random side / shuffled days, 100 worlds): p_book 0.78; family size 90 (E.family_adjust over the 90 re-evaluated cells): p_family 1.00. Verdict string: FAILS tolerant gate (minimum sample), placebo, family, walk-forward, stack Calmar not up.
* T3 selection-aware pre-2023 null (90 cells x 200 hash_u random-side worlds, same trade timing): world maximum of the pre-2023 total has median $2,693 and p95 $17,938, so p13 = 0.50 for the picked cell's +$2,860; for years-positive the world maximum has median 6 and p95 8, p13 = 0.97. The cell itself, tested alone, would have p 0.11 (not family-adjusted). It is the 2nd of 90 by pre-2023 total (the best, rth 540-870 x .25 stop 4 1R, is +$4,707); 5 of the 90 cells have a positive pre-2023 total (median across null worlds: 2).
* T4 plateau: one-step neighbours of the picked cell: x_atr 0.10 (-$1,493), stop 3 ATR (-$4,844), stop 6 ATR (+$1,684), target 1R (-$3,553), rth 540-870 (+$1,170): 2 of 5 positive, below the stated half: no plateau. Among all 38 pdhl_break pre cells of the family, 5 are positive before 2023 and 33 are negative (down to -$35,925).
* T5 own walk-forward over the parameter neighbours: 6-month lookback OOS -$48 per week (p_rand 1.00), 12-month +$32 per week (p_rand 1.00): not positive at both lookbacks.
* Correlation to the NQ stack V2: daily -0.05, weekly +0.05 (diversifying, but with no edge). Stack Calmar: not up at equal risk (k* = 0).
Decision rule of the prereg: lead only if all hold; failing items: minimum sample, placebo, p_family, p13, plateau, walk-forward, stack Calmar. The earlier block-B verdict (DS3_INSTR2_6E_B.md) stands; CHAR-C's break-even reading is a selection effect. Ledger: this adds 1 test to the 90-cell family (no new grid).

## Companion check: ZL-1 LRS 6E / 6J finalists on the repaired 13-year bars (lead order)
Same lrs_lib code and parameters; bars = repaired copy; walk-forward folds extended back to 2015-04 (24 training months from 2013-04). Code l2vast/ds3/code/t2s4a/lrs13.py, results /mnt/l2/l2vast/find_c/lrs13_<SYM>.pkl.
| finalist | pre-2023 total (2015-2022) | years positive | 2023-26 total (reproduced) |
|--|--|--|--|
| 6E gp h15 nyam q.7 atr3 no-tgt s2 | -$644,908 | 0 of 8 | -$269,032 |
| 6E tree_rev h60 nyam q.7 atr3 2R s1 | -$375,231 | 0 of 8 | -$187,590 |
| 6E tree_rev h60 nyam q.7 atr3 no-tgt s1 | -$390,125 | 1 of 8 | -$180,438 |
| 6J tree_rev h15 pre q.7 atr3 no-tgt s2 | -$423,494 | 0 of 8 | -$210,313 |
| 6J gp h15 london q.85 atr3 no-tgt s1 | -$1,265,234 | 0 of 8 | -$503,175 |
| 6J gp h60 nypm q.85 atr2 1.5R s2 | -$242,837 | 0 of 8 | -$116,238 |
Plain sentence: the six LRS finalists lose money in 7 of 8 pre-2023 years or more on the repaired bars and in 2023-26 as well (all equal-$ lots, integer, cap), so nothing in the learned-rule search survives 13 years. Differences stated: the 2023-26 trades are re-learned in a longer fold sequence (the subsample random stream differs), so counts differ from the ZL-1 frames (for example 6E first finalist 1,892 vs 1,956 trades, net -$252k vs -$207k); both are negative. The 8 pre-2023 years start 2015 because the first fold needs 24 training months.
