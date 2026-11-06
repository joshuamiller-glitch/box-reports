# DS3_INSTR2_GC_B - T-INSTR-2 GC family block B (BASE-4), 2026-11-06T01:30Z

Research only, $0, no PASS claims, Shadow only, nothing live. Scope l2vast/ds3/prereg/T2_GC_B_scope.md sha256 0c822b07265ddee13c11a33b8689af82341d871c01cbfd38c5dafa7318104ba8 (DECISIONS.md before any GC cell). Evaluator l2vast/ds3/code/instr2/instr2_eval.py, runner l2vast/ds3/code/instr2/t2b/. Base: GC 1-min, bar simulator, te2 cost proxies (fee $4.84 PROXY-STD (te2_lib; not in FEES.md); market 1 / stop 2 ticks, market cost on every exit), equal-$ risk R $1,200, integer lots, participation caps; carrying weeks dropped for the window table; stack V0/V2.

## Plain sentence
No GC block-B cell clears the tolerant gate, the per-cell placebo and the family max-statistic together (3840 scored, 3000 eligible for the world tests, 392 tolerant, 42 of those with per-cell p <= .10, family-surviving 0): no diversifier lead on this grid.

## 1. Counts
| stage | cells |
|--|--|
| cells in the grid | 5400 |
| untestable (< 10 trades) | 1560 |
| scored (S1) | 3840 |
| eligible for the world tests (>= 10 trades L6M and >= 30 HOLD) = family F | 3000 |
| NOW-ONLY (L3M and L6M mean > 0) | 906 |
| tolerant gate + min sample (gate_v2a) | 392 |
| of those eligible | 392 |
| of those with persistence > 60% | 343 |
| tolerant AND per-cell placebo p_book <= .10 (best-of-F) | 42 |
| AND family max-statistic p <= .10 | 0 |
Family M vector (hash worlds, 200) saved: /mnt/l2/l2vast/ds3_instr2_b4/GC_B/M.npy; cell table /mnt/l2/l2vast/ds3_instr2_b4/GC_B/cells.csv. All-instrument n_tested total now 1935108.

## 2. Top tolerant cells by zj (min of L6M and HOLD z on the ALLINST hash worlds)
| cell | n 2023-26 | L1M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | persist | zj | p_book | p_family | pre-2023 years (+ / n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| vwap_reclaim anchor_hm=500,hold=5,min_bars=15,span_min=600 london stop4ATR tgt 2R | 418 | -368 | +271 | +1689 | +897 | +1276 | -76 | +36 | 8473 | 75% | 2.82 | 0.01 | 0.81 | 1 / 10 |
| donchian k=1,mode=break,n=10 nyam stop2ATR tgt 1R | 3794 | +1535 | +1647 | +3706 | +2694 | -662 | -216 | +907 | 27174 | 75% | 2.76 | 0.01 | 0.24 | 1 / 10 |
| donchian k=1,mode=break,n=10 nyam stop2ATR tgt none | 2463 | +479 | +1042 | +951 | +1727 | -966 | -104 | +184 | 38437 | 75% | 2.26 | 0.02 | 1.00 | 0 / 10 |
| vwap_reject anchor_hm=570,hold=5,min_bars=15,span_min=390 nypm stop2ATR tgt none | 767 | +1221 | +503 | +1494 | +1205 | +823 | -394 | +63 | 14062 | 88% | 2.00 | 0.03 | 1.00 | 0 / 10 |
| donchian k=5,mode=fade,n=10 nyam stop6ATR tgt 2R | 1389 | -345 | +3 | +1231 | +1850 | +2181 | -97 | -337 | 11672 | 62% | 1.87 | 0.02 | 0.99 | 1 / 10 |
| donchian k=5,mode=fade,n=55 nyam stop6ATR tgt 2R | 817 | +505 | +70 | +1608 | +1990 | +1469 | -274 | -224 | 17943 | 75% | 1.79 | 0.01 | 1.00 | 3 / 10 |
| donchian k=5,mode=fade,n=55 nyam stop6ATR tgt none | 817 | +505 | +70 | +1608 | +1835 | +1469 | -262 | -224 | 17943 | 75% | 1.75 | 0.02 | 1.00 | 3 / 10 |
| donchian k=1,mode=break,n=10 nyam stop2ATR tgt 2R | 2792 | +492 | +1055 | +472 | +1484 | -548 | -153 | +582 | 29730 | 75% | 1.70 | 0.23 | 1.00 | 1 / 10 |
| donchian k=5,mode=fade,n=55 nyam stop3ATR tgt 1R | 933 | +299 | +107 | +1399 | +1451 | +1981 | -34 | -307 | 7391 | 75% | 1.64 | 0.03 | 1.00 | 0 / 10 |
| vwap_reject anchor_hm=500,hold=5,min_bars=15,span_min=600 nypm stop2ATR tgt none | 632 | -210 | +232 | +1324 | +664 | +33 | -191 | -237 | 13833 | 62% | 1.62 | 0.09 | 1.00 | 1 / 10 |
| donchian k=5,mode=break,n=34 asia stop6ATR tgt none | 2580 | +1733 | +2277 | +1990 | +2124 | +2125 | -222 | -563 | 28643 | 75% | 1.61 | 0.11 | 1.00 | 0 / 10 |
| donchian k=5,mode=fade,n=10 nyam stop4ATR tgt none | 1445 | +67 | +415 | +1003 | +1777 | +1776 | -107 | -360 | 20576 | 75% | 1.57 | 0.03 | 1.00 | 1 / 10 |
| orb_failed anchor_hm=500,end_hm=800,fail_bars=10,minutes=30 pre stop3ATR tgt none | 480 | +478 | +191 | +144 | +1251 | +120 | -142 | +283 | 14469 | 88% | 1.55 | 0.85 | 1.00 | 4 / 10 |
| failed_or anchor_hm=500,minutes=30 pre stop2ATR tgt 2R | 431 | +645 | +454 | +195 | +359 | +452 | -351 | -584 | 8298 | 75% | 1.55 | 0.65 | 1.00 | 4 / 10 |
| donchian k=5,mode=break,n=34 asia stop6ATR tgt 2R | 2591 | +2024 | +2513 | +2153 | +2512 | +2717 | -246 | -557 | 28643 | 75% | 1.54 | 0.04 | 1.00 | 0 / 10 |
| vwap_reject anchor_hm=500,hold=5,min_bars=15,span_min=600 nypm stop6ATR tgt none | 594 | -96 | +323 | +1564 | +650 | -165 | +20 | -155 | 10477 | 62% | 1.54 | 0.07 | 1.00 | 2 / 10 |
| failed_or anchor_hm=500,minutes=30 pre stop3ATR tgt none | 427 | +493 | +210 | +120 | +944 | +82 | -21 | +81 | 13260 | 88% | 1.53 | 0.55 | 1.00 | 3 / 10 |
| vwap_reject anchor_hm=500,hold=5,min_bars=15,span_min=600 nypm stop3ATR tgt none | 606 | -223 | +196 | +1445 | +634 | -237 | -28 | +44 | 12728 | 62% | 1.52 | 0.06 | 1.00 | 2 / 10 |
| vwap_reject anchor_hm=500,hold=5,min_bars=15,span_min=600 nypm stop6ATR tgt 2R | 596 | -96 | +323 | +1318 | +554 | -165 | +19 | -155 | 10477 | 62% | 1.51 | 0.11 | 1.00 | 2 / 10 |
| donchian k=5,mode=fade,n=55 nyam stop2ATR tgt 2R | 1042 | +773 | +423 | +1297 | +1503 | +1629 | -354 | -552 | 9100 | 75% | 1.49 | 0.04 | 1.00 | 0 / 10 |
$/wk at equal-$-risk lots, carry-dropped; best-of-F by construction, only the family column counts.

## 3. Full evaluator for the family survivors and the 10 best tolerant cells
* **vwap_reclaim anchor_hm=500,hold=5,min_bars=15,span_min=600 london stop4ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 1.00 > .10 | family p 0.81 > .10 | walk-forward not positive (6m: OOS 225/wk, p_rand 0.00, 12m: OOS -2/wk, p_rand 0.03). corr V0 0.03/0.11, V2 0.02/0.13; stack k* 5.00; WF {6: (225, 0.0), 12: (-2, 0.03)}; pre-2023 pos years 1/10; frame /mnt/l2/l2vast/instr2_trades/GC/cc2fa003aba0_vwap_reclaim.parquet
* **donchian k=1,mode=break,n=10 nyam stop2ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.12 > .10 | family p 0.24 > .10 | walk-forward not positive (6m: OOS -267/wk, p_rand 0.31, 12m: OOS 270/wk, p_rand 0.01). corr V0 0.01/0.04, V2 0.00/0.07; stack k* 5.00; WF {6: (-267, 0.31), 12: (270, 0.01)}; pre-2023 pos years 1/10; frame /mnt/l2/l2vast/instr2_trades/GC/6764d7ecabfd_donchian.parquet
* **donchian k=1,mode=break,n=10 nyam stop2ATR tgt none** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.39 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -90/wk, p_rand 0.33, 12m: OOS 307/wk, p_rand 0.04) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.03/0.04, V2 0.03/0.07; stack k* 0.00; WF {6: (-90, 0.33), 12: (307, 0.04)}; pre-2023 pos years 0/10; frame /mnt/l2/l2vast/instr2_trades/GC/5ae4b631c93d_donchian.parquet
* **vwap_reject anchor_hm=570,hold=5,min_bars=15,span_min=390 nypm stop2ATR tgt none** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.45 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS 129/wk, p_rand 0.28, 12m: OOS -34/wk, p_rand 0.64) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.02/0.12, V2 0.02/0.11; stack k* 0.00; WF {6: (129, 0.28), 12: (-34, 0.64)}; pre-2023 pos years 0/10; frame /mnt/l2/l2vast/instr2_trades/GC/008066656e10_vwap_reject.parquet
* **donchian k=5,mode=fade,n=10 nyam stop6ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.25 > .10 | family p 0.99 > .10 | walk-forward not positive (6m: OOS -19/wk, p_rand 0.42, 12m: OOS -39/wk, p_rand 0.42). corr V0 -0.02/0.02, V2 -0.01/0.01; stack k* 5.00; WF {6: (-19, 0.42), 12: (-39, 0.42)}; pre-2023 pos years 1/10; frame /mnt/l2/l2vast/instr2_trades/GC/fea0c2aef7cc_donchian.parquet
* **donchian k=5,mode=fade,n=55 nyam stop6ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.39 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -19/wk, p_rand 0.42, 12m: OOS -39/wk, p_rand 0.42). corr V0 0.03/0.09, V2 0.03/0.08; stack k* 1.03; WF {6: (-19, 0.42), 12: (-39, 0.42)}; pre-2023 pos years 3/10; frame /mnt/l2/l2vast/instr2_trades/GC/5ba0803702f7_donchian.parquet
* **donchian k=5,mode=fade,n=55 nyam stop6ATR tgt none** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.41 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -428/wk, p_rand 0.89, 12m: OOS -296/wk, p_rand 0.77). corr V0 0.03/0.08, V2 0.03/0.07; stack k* 1.03; WF {6: (-428, 0.89), 12: (-296, 0.77)}; pre-2023 pos years 3/10; frame /mnt/l2/l2vast/instr2_trades/GC/85617e2600c5_donchian.parquet
* **donchian k=1,mode=break,n=10 nyam stop2ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.28 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -592/wk, p_rand 0.78, 12m: OOS -379/wk, p_rand 0.52). corr V0 0.02/0.03, V2 0.02/0.04; stack k* 3.29; WF {6: (-592, 0.78), 12: (-379, 0.52)}; pre-2023 pos years 1/10; frame /mnt/l2/l2vast/instr2_trades/GC/d2d3a17b6581_donchian.parquet
* **donchian k=5,mode=fade,n=55 nyam stop3ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.22 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -342/wk, p_rand 0.63, 12m: OOS -234/wk, p_rand 0.47). corr V0 0.01/0.10, V2 0.01/0.08; stack k* 5.00; WF {6: (-342, 0.63), 12: (-234, 0.47)}; pre-2023 pos years 0/10; frame /mnt/l2/l2vast/instr2_trades/GC/e3b2eecdd2f5_donchian.parquet
* **vwap_reject anchor_hm=500,hold=5,min_bars=15,span_min=600 nypm stop2ATR tgt none** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.59 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS 129/wk, p_rand 0.28, 12m: OOS -34/wk, p_rand 0.64). corr V0 0.06/0.21, V2 0.06/0.21; stack k* 5.00; WF {6: (129, 0.28), 12: (-34, 0.64)}; pre-2023 pos years 1/10; frame /mnt/l2/l2vast/instr2_trades/GC/25526cbbabf2_vwap_reject.parquet

## 4. Limits
* 1-min bar simulator (entry at the next bar open, stop first in a bar), te2 cost proxies charged as market on every exit; no tick re-run. Hash-world null is random-side only (ALLINST design); shift5 / days worlds are my own forward-only extras (100 each). Windows end where the data end (L1M/L2M partial for non-index instruments).
* Other owners' grids on GC are different cells; the all-GC family is larger than F.
