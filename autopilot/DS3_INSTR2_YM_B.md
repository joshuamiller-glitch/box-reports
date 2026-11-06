# DS3_INSTR2_YM_B - T-INSTR-2 YM family block B (BASE-4), 2026-11-05T22:59Z

Research only, $0, no PASS claims, Shadow only, nothing live. Scope l2vast/ds3/prereg/T2_YM_B_scope.md sha256 564f690ad64b2ab6388836ae2a45c2e5dd8318f6f28064ad10dd6d4ac50e0e53 (DECISIONS.md before any YM cell). Evaluator l2vast/ds3/code/instr2/instr2_eval.py, runner l2vast/ds3/code/instr2/t2b/. Base: YM 1-min, bar simulator, te2 cost proxies (fee $4.84 PROXY-STD (te2_lib; not in FEES.md); market 1 / stop 2 ticks, market cost on every exit), equal-$ risk R $1,200, integer lots, participation caps; carrying weeks dropped for the window table; stack V0/V2.

## Plain sentence
No YM block-B cell clears the tolerant gate, the per-cell placebo and the family max-statistic together (2268 scored, 1752 eligible for the world tests, 207 tolerant, 12 of those with per-cell p <= .10, family-surviving 0): no diversifier lead on this grid.

## 1. Counts
| stage | cells |
|--|--|
| cells in the grid | 3168 |
| untestable (< 10 trades) | 900 |
| scored (S1) | 2268 |
| eligible for the world tests (>= 10 trades L6M and >= 30 HOLD) = family F | 1752 |
| NOW-ONLY (L3M and L6M mean > 0) | 410 |
| tolerant gate + min sample (gate_v2a) | 207 |
| of those eligible | 207 |
| of those with persistence > 60% | 181 |
| tolerant AND per-cell placebo p_book <= .10 (best-of-F) | 12 |
| AND family max-statistic p <= .10 | 0 |
Family M vector (hash worlds, 200) saved: /mnt/l2/l2vast/ds3_instr2_b4/YM_B/M.npy; cell table /mnt/l2/l2vast/ds3_instr2_b4/YM_B/cells.csv. All-instrument n_tested total now 1881939.

## 2. Top tolerant cells by zj (min of L6M and HOLD z on the ALLINST hash worlds)
| cell | n 2023-26 | L1M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | persist | zj | p_book | p_family | pre-2023 years (+ / n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop2ATR tgt 1R | 1357 | +1126 | +1150 | +834 | +278 | -227 | -34 | +189 | 11674 | 75% | 2.06 | 0.07 | 1.00 | 1 / 10 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop3ATR tgt 1R | 1118 | +960 | +1226 | +886 | +594 | +162 | +11 | -388 | 6754 | 88% | 1.84 | 0.02 | 1.00 | 3 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=390 pre stop6ATR tgt 1R | 498 | +662 | +421 | +385 | +420 | -62 | -75 | +636 | 5176 | 75% | 1.65 | 0.98 | 1.00 | 3 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 pre stop6ATR tgt 1R | 498 | +662 | +421 | +385 | +420 | -62 | -75 | +636 | 5176 | 75% | 1.65 | 0.96 | 1.00 | 3 / 10 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop4ATR tgt none | 973 | +727 | +1120 | +1156 | +777 | +711 | -204 | +71 | 10459 | 88% | 1.56 | 0.07 | 1.00 | 2 / 10 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop4ATR tgt 2R | 974 | +565 | +958 | +1168 | +767 | +836 | -169 | +106 | 10646 | 88% | 1.55 | 0.09 | 1.00 | 1 / 10 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop6ATR tgt 2R | 970 | +847 | +1240 | +1081 | +845 | +1325 | -154 | +31 | 11318 | 88% | 1.50 | 0.07 | 1.00 | 2 / 10 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop6ATR tgt none | 969 | +847 | +1240 | +1081 | +830 | +1218 | -223 | +31 | 10983 | 88% | 1.50 | 0.03 | 1.00 | 2 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=390 pre stop4ATR tgt 2R | 505 | +1019 | +713 | +133 | +320 | +41 | -277 | +553 | 8556 | 88% | 1.48 | 0.95 | 1.00 | 3 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 pre stop4ATR tgt 2R | 505 | +1019 | +713 | +133 | +320 | +41 | -277 | +553 | 8556 | 88% | 1.48 | 0.97 | 1.00 | 3 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=390 pre stop6ATR tgt none | 492 | +486 | +245 | +219 | +300 | -156 | -202 | +864 | 7936 | 75% | 1.36 | 0.49 | 1.00 | 4 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 pre stop6ATR tgt none | 492 | +486 | +245 | +219 | +300 | -156 | -202 | +864 | 7936 | 75% | 1.36 | 0.67 | 1.00 | 4 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=390 pre stop6ATR tgt 2R | 492 | +486 | +245 | +238 | +337 | -86 | -131 | +598 | 6111 | 75% | 1.35 | 0.59 | 1.00 | 4 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 pre stop6ATR tgt 2R | 492 | +486 | +245 | +238 | +337 | -86 | -131 | +598 | 6111 | 75% | 1.35 | 0.69 | 1.00 | 4 / 10 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop2ATR tgt none | 1187 | +1941 | +2304 | +638 | +1239 | +1148 | -505 | +101 | 8071 | 88% | 1.21 | 0.62 | 1.00 | 2 / 10 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop2ATR tgt 2R | 1207 | +1865 | +2078 | +922 | +982 | +406 | -259 | -45 | 9639 | 75% | 1.20 | 0.44 | 1.00 | 2 / 10 |
| vwap_reject anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop2ATR tgt 1R | 1469 | +363 | +759 | +1213 | +433 | +535 | -72 | -365 | 11415 | 75% | 1.17 | 0.09 | 1.00 | 0 / 10 |
| orb_failed anchor_hm=570,end_hm=870,fail_bars=10,minutes=5 nyam stop4ATR tgt 2R | 708 | +394 | +906 | +859 | +477 | -158 | -225 | -271 | 16788 | 62% | 1.17 | 0.07 | 1.00 | 2 / 10 |
| session_extreme_fade anchor_hm=570,cooldown=30,min_bars=30,span_min=390 close stop2ATR tgt 1R | 219 | +328 | +328 | +39 | +254 | +500 | -5 | -35 | 3460 | 75% | 1.17 | 0.11 | 1.00 | 0 / 10 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop6ATR tgt 1R | 988 | +522 | +914 | +986 | +672 | +1080 | -214 | +28 | 13068 | 88% | 1.16 | 0.10 | 1.00 | 2 / 10 |
$/wk at equal-$-risk lots, carry-dropped; best-of-F by construction, only the family column counts.

## 3. Full evaluator for the family survivors and the 10 best tolerant cells
* **vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop2ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.60 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -400/wk, p_rand 0.96, 12m: OOS -206/wk, p_rand 0.76) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.04/-0.01, V2 0.03/-0.01; stack k* 0.00; WF {6: (-400, 0.96), 12: (-206, 0.76)}; pre-2023 pos years 1/10; frame /mnt/l2/l2vast/instr2_trades/YM/8a2d2dfb30a0_vwap_reclaim.parquet
* **vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop3ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.18 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS 23/wk, p_rand 0.48, 12m: OOS -33/wk, p_rand 0.64). corr V0 0.04/-0.01, V2 0.04/0.00; stack k* 5.00; WF {6: (23, 0.48), 12: (-33, 0.64)}; pre-2023 pos years 3/10; frame /mnt/l2/l2vast/instr2_trades/YM/1f63209890b3_vwap_reclaim.parquet
* **vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=390 pre stop6ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.66 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -47/wk, p_rand 1.00, 12m: OOS -157/wk, p_rand 1.00). corr V0 0.03/0.04, V2 0.01/0.04; stack k* 5.00; WF {6: (-47, 1.0), 12: (-157, 1.0)}; pre-2023 pos years 3/10; frame /mnt/l2/l2vast/instr2_trades/YM/131d73154e35_vwap_reject.parquet
* **vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 pre stop6ATR tgt 1R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.66 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -47/wk, p_rand 1.00, 12m: OOS -157/wk, p_rand 1.00). corr V0 0.03/0.04, V2 0.01/0.04; stack k* 5.00; WF {6: (-47, 1.0), 12: (-157, 1.0)}; pre-2023 pos years 3/10; frame /mnt/l2/l2vast/instr2_trades/YM/67b211f329eb_vwap_reject.parquet
* **orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop4ATR tgt none** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.64 > .10 | family p 1.00 > .10 | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.09/0.07, V2 0.10/0.08; stack k* 0.00; WF {6: (19, 0.09), 12: (178, 0.0)}; pre-2023 pos years 2/10; frame /mnt/l2/l2vast/instr2_trades/YM/cafd61912da3_orb_fade.parquet
* **orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop4ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.56 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -19/wk, p_rand 0.12, 12m: OOS 222/wk, p_rand 0.00) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.09/0.08, V2 0.09/0.08; stack k* 0.00; WF {6: (-19, 0.12), 12: (222, 0.0)}; pre-2023 pos years 1/10; frame /mnt/l2/l2vast/instr2_trades/YM/19e761fbccd7_orb_fade.parquet
* **orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop6ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.62 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -60/wk, p_rand 0.35, 12m: OOS 181/wk, p_rand 0.00) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.08/0.06, V2 0.09/0.05; stack k* 0.00; WF {6: (-60, 0.35), 12: (181, 0.0)}; pre-2023 pos years 2/10; frame /mnt/l2/l2vast/instr2_trades/YM/52a537498471_orb_fade.parquet
* **orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop6ATR tgt none** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.66 > .10 | family p 1.00 > .10 | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.08/0.06, V2 0.09/0.05; stack k* 0.00; WF {6: (24, 0.13), 12: (178, 0.0)}; pre-2023 pos years 2/10; frame /mnt/l2/l2vast/instr2_trades/YM/9355e374400c_orb_fade.parquet
* **vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=390 pre stop4ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.93 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -51/wk, p_rand 0.00, 12m: OOS -278/wk, p_rand 1.00). corr V0 0.02/-0.02, V2 0.00/-0.03; stack k* 5.00; WF {6: (-51, 0.0), 12: (-278, 1.0)}; pre-2023 pos years 3/10; frame /mnt/l2/l2vast/instr2_trades/YM/fa8586b112ce_vwap_reject.parquet
* **vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 pre stop4ATR tgt 2R** [top-10 tolerant by zj (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.93 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -51/wk, p_rand 0.00, 12m: OOS -278/wk, p_rand 1.00). corr V0 0.02/-0.02, V2 0.00/-0.03; stack k* 5.00; WF {6: (-51, 0.0), 12: (-278, 1.0)}; pre-2023 pos years 3/10; frame /mnt/l2/l2vast/instr2_trades/YM/f2d1da55d9f8_vwap_reject.parquet

## 4. Limits
* 1-min bar simulator (entry at the next bar open, stop first in a bar), te2 cost proxies charged as market on every exit; no tick re-run. Hash-world null is random-side only (ALLINST design); shift5 / days worlds are my own forward-only extras (100 each). Windows end where the data end (L1M/L2M partial for non-index instruments).
* Other owners' grids on YM are different cells; the all-YM family is larger than F.


## REPAIRED-BLOCKB (Z1, 2026-11-06): block-B survivors and gate flips on the BAD-PRINT-REPAIRED bars, original vs repaired
Source of the repair: CHAR-C's repaired 1-min copies (find_c/cache_c, rule cc_audit.py: bars whose high/low/close lie more than 10 sigma + 4 ticks outside their neighbours are clamped; originals untouched). The block-B bars (ohlcv1m dbn files) were matched by timestamp to the repaired copy and the o/h/l/c of every matched bar replaced (changed bars: YM 995, CL 523, 6E 19,721, 6J 14,455; all other cells of the bars identical). Everything else is unchanged: same signal sets, brackets, costs, caps, evaluator, gate. Code l2vast/ds3/code/repair_z1/ (rerun.py, compare.py, doc.py); results /mnt/l2/l2vast/repair_z1/.
Method (stated limits): (1) STAGE 1 for EVERY cell of the grid on repaired bars (exact, deterministic): tolerant-gate and NOW-ONLY status compared with the stored original of the same cell. (2) Placebo worlds (HOLD-window hash/side/shift5/days worlds as in the block) re-run for every cell that is tolerant in the original OR the repaired version, on the repaired bars AND, with the same per-cell seed, on the original bars again (the 'control'), because the placebos draw random numbers and the original runs used a different random stream: original-vs-control differences are Monte-Carlo noise. (3) p_family is evaluated against the ORIGINAL family world-max distribution M (the full family of ~2,600-3,000 eligible cells was not re-simulated; a few changed cells cannot move the max of the family materially, but this is an approximation and is labelled so).
| instrument | bad bars repaired | cells scored | cells whose L6M or HOLD mean changed (any / > 10%) | tolerant gate: original -> repaired (lost / gained) | NOW-ONLY (lost / gained) | tolerant + p_book <= .10: original / original-bars rerun (MC control) / repaired | in both original and repaired | only original / only repaired | family-surviving (p_family <= .10): original -> repaired |
|---|---|---|---|---|---|---|---|---|---|
| YM | 995 | 2268 | 1478 / 739 | 207 -> 208 (11 / 12) | 9 / 11 | 12 / 13 / 11 | 9 | 3 / 2 | 0 -> 0 |
### YM - tolerant + p_book <= .10 in the original or in the repaired run (L6M / HOLD / PRE in $/wk at equal-risk lots, carry dropped; p_book original / original-bars rerun / repaired; p_family vs the original max)
| cell | L6M orig -> rep | HOLD orig -> rep | PRE orig -> rep | tolerant orig -> rep | p_book o / ctl / r | p_family o -> r |
|--|--|--|--|--|--|--|
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop4ATR tgt 2R | +1168 -> +1168 | +767 -> +784 | -169 -> -206 | True -> True | 0.09 / 0.12 / 0.14 | 1.00 -> 1.00 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop4ATR tgt none | +1156 -> +1156 | +777 -> +797 | -204 -> -232 | True -> True | 0.07 / 0.07 / 0.08 | 1.00 -> 1.00 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop6ATR tgt 1R | +986 -> +985 | +672 -> +664 | -214 -> -205 | True -> True | 0.10 / 0.06 / 0.09 | 1.00 -> 1.00 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop6ATR tgt 2R | +1081 -> +1081 | +845 -> +835 | -154 -> -145 | True -> True | 0.07 / 0.06 / 0.05 | 1.00 -> 1.00 |
| orb_fade anchor_hm=570,end_hm=870,minutes=5 nyam stop6ATR tgt none | +1081 -> +1081 | +830 -> +821 | -223 -> -214 | True -> True | 0.03 / 0.03 / 0.03 | 1.00 -> 1.00 |
| orb_failed anchor_hm=570,end_hm=870,fail_bars=10,minutes=5 nyam stop4ATR tgt 2R | +859 -> +859 | +477 -> +446 | -225 -> -197 | True -> True | 0.07 / 0.07 / 0.08 | 1.00 -> 1.00 |
| orb_failed anchor_hm=570,end_hm=870,fail_bars=10,minutes=5 nyam stop6ATR tgt 2R | +652 -> +652 | +407 -> +400 | -109 -> -87 | True -> True | 0.07 / 0.07 / 0.07 | 1.00 -> 1.00 |
| orb_failed anchor_hm=570,end_hm=870,fail_bars=10,minutes=5 nyam stop6ATR tgt none | +652 -> +652 | +375 -> +368 | -115 -> -94 | True -> True | 0.07 / 0.10 / 0.12 | 1.00 -> 1.00 |
| failed_or anchor_hm=570,minutes=5 nyam stop6ATR tgt none | +644 -> +644 | +274 -> +259 | -207 -> -190 | True -> True | 0.10 / 0.10 / 0.18 | 1.00 -> 1.00 |
| session_extreme_fade anchor_hm=570,cooldown=30,min_bars=30,span_min=390 close stop2ATR tgt 1R | +39 -> +39 | +254 -> +254 | -5 -> -5 | True -> True | 0.11 / 0.06 / 0.06 | 1.00 -> 1.00 |
| orb_failed anchor_hm=570,end_hm=870,fail_bars=10,minutes=15 nyam stop4ATR tgt 2R | +49 -> +57 | +199 -> +175 | -246 -> -236 | True -> True | 0.10 / 0.10 / 0.10 | 1.00 -> 1.00 |
| vwap_reject anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop2ATR tgt 1R | +1213 -> +1261 | +433 -> +420 | -72 -> -51 | True -> True | 0.09 / 0.09 / 0.07 | 1.00 -> 1.00 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop2ATR tgt 1R | +834 -> +833 | +278 -> +315 | -34 -> -46 | True -> True | 0.07 / 0.05 / 0.04 | 1.00 -> 0.86 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop3ATR tgt 1R | +886 -> +810 | +594 -> +525 | +11 -> +24 | True -> True | 0.02 / 0.02 / 0.03 | 1.00 -> 0.98 |

Full table and method limits: autopilot/REPAIRED_BARS_RERUN.md.
