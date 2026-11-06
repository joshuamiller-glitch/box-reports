# DS3_INSTR2_ZN_B - T-INSTR-2 ZN family block B (BASE-4), 2026-11-06T01:49Z

Research only, $0, no PASS claims, Shadow only, nothing live. Scope l2vast/ds3/prereg/T2_ZN_B_scope.md sha256 832d7489c6ed39a52e80efd9a5a10903bfb03e13f5b5213dac76c6d1c236ba65 (DECISIONS.md before any ZN cell). Evaluator l2vast/ds3/code/instr2/instr2_eval.py, runner l2vast/ds3/code/instr2/t2b/. Base: ZN 1-min, bar simulator, te2 cost proxies (fee $4.84 PROXY-STD (te2_lib; not in FEES.md); market 1 / stop 2 ticks, market cost on every exit), equal-$ risk R $1,200, integer lots, participation caps; carrying weeks dropped for the window table; stack V0/V2.

## Plain sentence
No ZN block-B cell clears the tolerant gate, the per-cell placebo and the family max-statistic together (3492 scored, 2617 eligible for the world tests, 0 tolerant, 0 of those with per-cell p <= .10, family-surviving 0): no diversifier lead on this grid.

## 1. Counts
| stage | cells |
|--|--|
| cells in the grid | 4320 |
| untestable (< 10 trades) | 828 |
| scored (S1) | 3492 |
| eligible for the world tests (>= 10 trades L6M and >= 30 HOLD) = family F | 2617 |
| NOW-ONLY (L3M and L6M mean > 0) | 120 |
| tolerant gate + min sample (gate_v2a) | 0 |
| of those eligible | 0 |
| of those with persistence > 60% | 0 |
| tolerant AND per-cell placebo p_book <= .10 (best-of-F) | 0 |
| AND family max-statistic p <= .10 | 0 |
Family M vector (hash worlds, 200) saved: /mnt/l2/l2vast/ds3_instr2_b4/ZN_B/M.npy; cell table /mnt/l2/l2vast/ds3_instr2_b4/ZN_B/cells.csv. All-instrument n_tested total now 1935603.

## 2. Top tolerant cells by zj (min of L6M and HOLD z on the ALLINST hash worlds)
| cell | n 2023-26 | L1M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | persist | zj | p_book | p_family | pre-2023 years (+ / n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| (no eligible cell passes the tolerant gate) | | | | | | | | | | | | | | |
$/wk at equal-$-risk lots, carry-dropped; best-of-F by construction, only the family column counts.

## 3. Full evaluator for the family survivors and the 10 best tolerant cells
No cell reached this stage.

## 4. Limits
* 1-min bar simulator (entry at the next bar open, stop first in a bar), te2 cost proxies charged as market on every exit; no tick re-run. Hash-world null is random-side only (ALLINST design); shift5 / days worlds are my own forward-only extras (100 each). Windows end where the data end (L1M/L2M partial for non-index instruments).
* Other owners' grids on ZN are different cells; the all-ZN family is larger than F.
