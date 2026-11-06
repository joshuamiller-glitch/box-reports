# DS3_INSTR2_MBT_B - T-INSTR-2 MBT family block B (BASE-4), 2026-11-06T02:07Z

Research only, $0, no PASS claims, Shadow only, nothing live. Scope l2vast/ds3/prereg/T2_MBT_B_scope.md sha256 da8442950df3fcdf9daa90b31f6dd7012cfb7b059bc5a3e95b67262e45efc18a (DECISIONS.md before any MBT cell). Evaluator l2vast/ds3/code/instr2/instr2_eval.py, runner l2vast/ds3/code/instr2/t2b/. Base: MBT 1-min, bar simulator, te2 cost proxies (fee $1.78 PROXY-MICRO (FEES.md MES value; not CME-published here); market 2 / stop 3 ticks, market cost on every exit), equal-$ risk R $1,200, integer lots, participation caps; carrying weeks dropped for the window table; stack V0/V2.

## Plain sentence
No MBT block-B cell clears the tolerant gate, the per-cell placebo and the family max-statistic together (2052 scored, 1560 eligible for the world tests, 55 tolerant, 9 of those with per-cell p <= .10, family-surviving 0): no diversifier lead on this grid.

## 1. Counts
| stage | cells |
|--|--|
| cells in the grid | 3168 |
| untestable (< 10 trades) | 1116 |
| scored (S1) | 2052 |
| eligible for the world tests (>= 10 trades L6M and >= 30 HOLD) = family F | 1560 |
| NOW-ONLY (L3M and L6M mean > 0) | 236 |
| tolerant gate + min sample (gate_v2a) | 55 |
| of those eligible | 55 |
| of those with persistence > 60% | 28 |
| tolerant AND per-cell placebo p_book <= .10 (best-of-F) | 9 |
| AND family max-statistic p <= .10 | 0 |
Family M vector (hash worlds, 200) saved: /mnt/l2/l2vast/ds3_instr2_b4/MBT_B/M.npy; cell table /mnt/l2/l2vast/ds3_instr2_b4/MBT_B/cells.csv. All-instrument n_tested total now 1936155.

## 2. Top tolerant cells by zj (min of L6M and HOLD z on the ALLINST hash worlds)
| cell | n 2023-26 | L1M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | persist | zj | p_book | p_family | pre-2023 years (+ / n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| donchian k=1,mode=break,n=34 nyam stop6ATR tgt 1R | 1981 | +102 | +333 | +343 | +186 | -132 | +3 | -97 | 6102 | 75% | 1.81 | 0.04 | 1.00 | 0 / 1 |
| donchian k=1,mode=break,n=34 nyam stop6ATR tgt 2R | 1857 | +52 | +380 | +152 | +25 | -5 | -67 | -137 | 7763 | 62% | 1.62 | 0.34 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=55 pre stop6ATR tgt 1R | 349 | +37 | +15 | +53 | +36 | +4 | -45 | -10 | 1649 | 75% | 1.56 | 0.04 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=55 pre stop6ATR tgt 2R | 344 | +37 | +35 | +71 | +8 | -93 | -31 | -28 | 2885 | 62% | 1.48 | 0.07 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=55 pre stop6ATR tgt none | 343 | +37 | +35 | +64 | +20 | -93 | -33 | -26 | 2885 | 62% | 1.44 | 0.06 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=55 pre stop3ATR tgt 2R | 350 | +37 | +51 | +53 | +18 | +23 | -37 | +8 | 1292 | 88% | 1.43 | 0.07 | 1.00 | 0 / 1 |
| donchian k=15,mode=fade,n=20 nypm stop3ATR tgt 2R | 492 | -4 | +3 | +54 | +19 | +133 | -55 | -29 | 1674 | 62% | 1.42 | 0.15 | 1.00 | 0 / 1 |
| donchian k=1,mode=break,n=20 nyam stop6ATR tgt 2R | 1937 | -98 | +306 | +170 | -16 | -135 | -80 | -111 | 5730 | 38% | 1.40 | 0.18 | 1.00 | 0 / 1 |
| donchian k=1,mode=break,n=55 nyam stop6ATR tgt 1R | 1827 | +3 | +213 | +328 | +115 | -24 | -73 | -95 | 4018 | 62% | 1.39 | 0.19 | 1.00 | 0 / 1 |
| donchian k=15,mode=fade,n=55 nypm stop3ATR tgt none | 365 | -6 | +1 | +28 | +9 | +118 | -41 | -40 | 1651 | 62% | 1.34 | 0.30 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=55 pre stop4ATR tgt none | 344 | +37 | +35 | +51 | +11 | -51 | -26 | -10 | 2086 | 62% | 1.34 | 0.10 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=34 pre stop4ATR tgt 2R | 465 | +37 | +35 | +48 | +19 | +39 | -37 | +20 | 2429 | 88% | 1.33 | 0.06 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=55 pre stop4ATR tgt 2R | 346 | +37 | +35 | +49 | -3 | -49 | -22 | +19 | 1763 | 62% | 1.28 | 0.14 | 1.00 | 0 / 1 |
| donchian k=1,mode=break,n=10 nyam stop4ATR tgt 1R | 2670 | +116 | +168 | +65 | -5 | +26 | +127 | +12 | 6633 | 88% | 1.27 | 0.19 | 1.00 | 0 / 1 |
| donchian k=1,mode=break,n=55 nyam stop3ATR tgt 2R | 2111 | -181 | +29 | +132 | -76 | -160 | -33 | +37 | 9181 | 50% | 1.23 | 0.50 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=55 pre stop3ATR tgt none | 344 | +37 | +5 | +33 | -4 | -54 | -26 | -8 | 2032 | 50% | 1.20 | 0.07 | 1.00 | 0 / 1 |
| donchian k=1,mode=break,n=34 nyam stop6ATR tgt none | 1835 | +52 | +380 | +143 | -49 | -150 | -143 | -157 | 9041 | 50% | 1.17 | 0.57 | 1.00 | 0 / 1 |
| donchian k=1,mode=break,n=20 nyam stop6ATR tgt 1R | 2069 | -64 | +244 | +254 | +16 | -283 | -116 | -20 | 6027 | 50% | 1.13 | 0.17 | 1.00 | 0 / 1 |
| donchian k=5,mode=break,n=34 pre stop4ATR tgt none | 462 | +37 | +35 | +51 | +13 | -12 | -36 | -18 | 2775 | 62% | 1.12 | 0.09 | 1.00 | 0 / 1 |
| donchian k=1,mode=break,n=10 nyam stop4ATR tgt 2R | 2265 | +348 | +719 | +157 | -33 | -210 | -37 | -19 | 7822 | 50% | 1.11 | 0.18 | 1.00 | 0 / 1 |
$/wk at equal-$-risk lots, carry-dropped; best-of-F by construction, only the family column counts.

## 3. Full evaluator for the family survivors and the 10 best tolerant cells
* **donchian k=1,mode=break,n=34 nyam stop6ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.35 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -69/wk, p_rand 0.16, 12m: OOS -157/wk, p_rand 0.41). corr V0 0.02/0.05, V2 0.03/0.06; stack k* 5.00; WF {6: (-69, 0.16), 12: (-157, 0.41)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/31c1b5071345_donchian.parquet
* **donchian k=1,mode=break,n=34 nyam stop6ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.66 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -311/wk, p_rand 0.84, 12m: OOS -199/wk, p_rand 0.51). corr V0 0.02/0.04, V2 0.02/0.06; stack k* 5.00; WF {6: (-311, 0.84), 12: (-199, 0.51)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/ab1923f34401_donchian.parquet
* **donchian k=5,mode=break,n=55 pre stop6ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.59 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -70/wk, p_rand 0.79, 12m: OOS -62/wk, p_rand 0.76) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.02/0.01, V2 -0.01/-0.00; stack k* 0.00; WF {6: (-70, 0.79), 12: (-62, 0.76)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/8b7160646f77_donchian.parquet
* **donchian k=5,mode=break,n=55 pre stop6ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 1.00 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -74/wk, p_rand 0.81, 12m: OOS -41/wk, p_rand 0.54) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.01/0.07, V2 -0.00/0.04; stack k* 0.00; WF {6: (-74, 0.81), 12: (-41, 0.54)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/ef3fce47b4c9_donchian.parquet
* **donchian k=5,mode=break,n=55 pre stop6ATR tgt none** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.98 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -71/wk, p_rand 0.80, 12m: OOS -34/wk, p_rand 0.47) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.01/0.06, V2 -0.01/0.03; stack k* 0.00; WF {6: (-71, 0.8), 12: (-34, 0.47)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/a8aaae5e9469_donchian.parquet
* **donchian k=5,mode=break,n=55 pre stop3ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.74 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -19/wk, p_rand 0.11, 12m: OOS -42/wk, p_rand 0.34) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.01/0.00, V2 -0.01/-0.01; stack k* 0.00; WF {6: (-19, 0.11), 12: (-42, 0.34)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/143d46abe0d0_donchian.parquet
* **donchian k=15,mode=fade,n=20 nypm stop3ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.52 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -19/wk, p_rand 0.08, 12m: OOS -43/wk, p_rand 0.19) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.03/0.02, V2 0.03/0.00; stack k* 0.00; WF {6: (-19, 0.08), 12: (-43, 0.19)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/d37c99c09c0b_donchian.parquet
* **donchian k=1,mode=break,n=20 nyam stop6ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: persistence 38% <= 60% | placebo p_book 0.79 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -311/wk, p_rand 0.84, 12m: OOS -199/wk, p_rand 0.51) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.06/0.06, V2 0.05/0.04; stack k* 0.00; WF {6: (-311, 0.84), 12: (-199, 0.51)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/8ea49140499a_donchian.parquet
* **donchian k=1,mode=break,n=55 nyam stop6ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.59 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -69/wk, p_rand 0.16, 12m: OOS -157/wk, p_rand 0.41). corr V0 -0.01/-0.00, V2 -0.00/-0.00; stack k* 5.00; WF {6: (-69, 0.16), 12: (-157, 0.41)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/27860a9c47b2_donchian.parquet
* **donchian k=15,mode=fade,n=55 nypm stop3ATR tgt none** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.76 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -46/wk, p_rand 0.17, 12m: OOS -18/wk, p_rand 0.06) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.04/-0.01, V2 0.04/-0.03; stack k* 0.00; WF {6: (-46, 0.17), 12: (-18, 0.06)}; pre-2023 pos years 0/1; frame /mnt/l2/l2vast/instr2_trades/MBT/c9b52e451e4e_donchian.parquet

## 4. Limits
* 1-min bar simulator (entry at the next bar open, stop first in a bar), te2 cost proxies charged as market on every exit; no tick re-run. Hash-world null is random-side only (ALLINST design); shift5 / days worlds are my own forward-only extras (100 each). Windows end where the data end (L1M/L2M partial for non-index instruments).
* Other owners' grids on MBT are different cells; the all-MBT family is larger than F.
