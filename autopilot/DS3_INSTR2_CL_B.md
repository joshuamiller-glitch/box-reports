# DS3_INSTR2_CL_B - T-INSTR-2 CL family block B (BASE-4), 2026-11-05T20:43Z

Research only, $0, no PASS claims, Shadow only, nothing live. Scope l2vast/ds3/prereg/T2_CL_B_scope.md sha256 3989bea523d1716a20c475514b9af607410b94075220aba33258d359042db1b2 (DECISIONS.md before any CL cell). Evaluator l2vast/ds3/code/instr2/instr2_eval.py; code l2vast/ds3/code/instr2/t2cl/. Base: CL.v.0 1-min 2013-2026-10-16, 1-min bar simulator, te2 cost proxies (fee $4.84 PROXY, 1 tick market / 2 ticks stop, market cost on every exit), equal-$ risk R $1,200, integer lots, participation caps; carrying weeks dropped; stack = Q1-A ts2 V0 and V2.

## Plain sentence
No CL block-B cell clears the tolerant gate, the per-cell placebo and the family max-statistic together (2964 cells scored, 2712 testable for placebo, F = 2712): CL block B yields no diversifier lead on this grid.

## 1. Counts (every cell is accounted for)
| stage | cells |
|--|--|
| cells in the grid (78 signal sets x 4 sessions x 12 brackets) | 3744 |
| untestable (< 10 trades over the data) | 780 |
| scored (S1) | 2964 |
| with >= 60 trades 2023-04..2026-10 = placebo family F (S2) | 2712 |
| NOW-ONLY (L3M and L6M mean > 0) | 773 |
| tolerant gate + min sample (gate_v2a) | 242 |
| of those with persistence > 60% of windows | 176 |
| tolerant AND placebo p_book <= .10 (per cell; best-of-F, not a lead) | 13 |
| tolerant AND p_book <= .10 AND family max-stat p <= .10 | 0 |
n_tested for CL block B = 3,744; all-instrument n_tested total at this moment: 1867095 (E.total_n_tested(), /mnt/l2/l2vast/instr2/n_tested.jsonl).

## 2. Best cells on the placebo statistic (min of HOLD and L6M z vs the placebo worlds), tolerant gate passers; per-cell p; family p
| cell | n 2023-26 | L1M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | persist | p_book | p_family | pre-2023 years (+ / n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pdhl_break rth=(570, 960),x_atr=0.25 london stop3ATR tgt 2R | 336 | +750 | +905 | +780 | +398 | +811 | -221 | -13 | 10024 | 75% | 0.03 | 1.00 | 7 / 10 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=600 nyam stop3ATR tgt 2R | 1348 | +1209 | +1134 | +809 | +804 | +837 | -488 | -742 | 5107 | 75% | 0.04 | 1.00 | 0 / 10 |
| donchian k=5,mode=fade,n=34 nyam stop6ATR tgt none | 1022 | -129 | +532 | +444 | +410 | +581 | +117 | -99 | 4399 | 75% | 0.04 | 1.00 | 1 / 10 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=600 nyam stop4ATR tgt none | 1273 | +978 | +840 | +528 | +408 | +446 | -368 | -400 | 7643 | 75% | 0.06 | 1.00 | 0 / 10 |
| pdhl_break rth=(570, 960),x_atr=0.1 london stop6ATR tgt 1R | 338 | +397 | +441 | +385 | +176 | +576 | -130 | -11 | 7702 | 75% | 0.05 | 1.00 | 7 / 10 |
| donchian k=5,mode=fade,n=34 nyam stop6ATR tgt 1R | 1047 | -161 | +500 | +560 | +465 | +593 | -45 | -95 | 4367 | 62% | 0.04 | 1.00 | 0 / 10 |
| orb_failed anchor_hm=540,end_hm=840,fail_bars=10,minutes=15 pre stop4ATR tgt 1R | 337 | +553 | +724 | +285 | +264 | +210 | +23 | -13 | 3652 | 88% | 0.08 | 1.00 | 4 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 nypm stop4ATR tgt 2R | 268 | -315 | +192 | +331 | +139 | +130 | -70 | +207 | 4084 | 75% | 0.11 | 1.00 | 2 / 10 |
| pdhl_break rth=(570, 960),x_atr=0.25 london stop6ATR tgt 1R | 336 | +321 | +476 | +342 | +215 | +664 | -79 | +16 | 6837 | 88% | 0.09 | 1.00 | 6 / 10 |
| donchian k=5,mode=fade,n=34 nyam stop6ATR tgt 2R | 1023 | -129 | +532 | +444 | +410 | +581 | +123 | -99 | 4399 | 75% | 0.07 | 1.00 | 0 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 nypm stop4ATR tgt none | 268 | -315 | +124 | +291 | +124 | +130 | -63 | +207 | 4084 | 75% | 0.09 | 1.00 | 2 / 10 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 nypm stop2ATR tgt none | 271 | -551 | +327 | +433 | +140 | +256 | -169 | +411 | 6175 | 75% | 0.09 | 1.00 | 2 / 10 |
| pdhl_break rth=(570, 960),x_atr=0.25 london stop4ATR tgt 2R | 336 | +250 | +405 | +350 | +238 | +1063 | -64 | +96 | 10686 | 88% | 0.13 | 1.00 | 6 / 10 |
| donchian k=5,mode=fade,n=34 nyam stop4ATR tgt 1R | 1137 | -1 | +919 | +306 | +316 | +571 | -101 | -167 | 7115 | 62% | 0.09 | 1.00 | 1 / 10 |
| pdhl_break rth=(570, 960),x_atr=0.1 london stop4ATR tgt 1R | 338 | +260 | +222 | +355 | +84 | +550 | -166 | -100 | 10746 | 75% | 0.13 | 1.00 | 6 / 10 |
| donchian k=5,mode=fade,n=55 nyam stop6ATR tgt 1R | 944 | -281 | +138 | +302 | +152 | -180 | -94 | -206 | 4807 | 50% | 0.13 | 1.00 | 1 / 10 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=600 nyam stop4ATR tgt 2R | 1276 | +978 | +840 | +611 | +469 | +513 | -364 | -264 | 7643 | 75% | 0.12 | 1.00 | 0 / 10 |
| pdhl_break rth=(570, 960),x_atr=0.1 london stop4ATR tgt 2R | 338 | +326 | +288 | +364 | +190 | +1049 | -73 | +36 | 12005 | 88% | 0.10 | 1.00 | 6 / 10 |
| failed_or anchor_hm=540,minutes=15 pre stop4ATR tgt 1R | 282 | +333 | +504 | +386 | +357 | +375 | -1 | +13 | 3028 | 88% | 0.11 | 1.00 | 4 / 10 |
| pdhl_break rth=(570, 960),x_atr=0.1 london stop3ATR tgt none | 338 | +718 | +579 | +393 | +133 | +829 | -151 | +109 | 12228 | 88% | 0.11 | 1.00 | 5 / 10 |
$/wk at equal-$-risk lots, carry-dropped. These are the best-of-F rows by construction: a low per-cell p among F = 2712 cells is expected for several cells by chance; only the family column counts.

## 3. Full evaluator (walk-forward over the family's parameter neighbours, correlation and stack effect V0/V2, bar verdict)
* **pdhl_break rth=(570, 960),x_atr=0.25 london stop3ATR tgt 2R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.28 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -196/wk, p_rand 1.00, 12m: OOS -89/wk, p_rand 0.95). corr V0 0.03/0.13, V2 0.03/0.15 (daily/weekly); stack k* 5.00; WF {6: (-196, 1.0), 12: (-89, 0.95)}; pre-2023 pos years 7/10.
* **vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=600 nyam stop3ATR tgt 2R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.11 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -63/wk, p_rand 0.27, 12m: OOS -47/wk, p_rand 0.22). corr V0 -0.05/-0.08, V2 -0.05/-0.09 (daily/weekly); stack k* 5.00; WF {6: (-63, 0.27), 12: (-47, 0.22)}; pre-2023 pos years 0/10.
* **donchian k=5,mode=fade,n=34 nyam stop6ATR tgt none** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.29 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -80/wk, p_rand 0.24, 12m: OOS -151/wk, p_rand 0.43) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.01/0.06, V2 -0.00/0.06 (daily/weekly); stack k* 0.00; WF {6: (-80, 0.24), 12: (-151, 0.43)}; pre-2023 pos years 1/10.
* **vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=600 nyam stop4ATR tgt none** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.24 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -169/wk, p_rand 0.60, 12m: OOS -271/wk, p_rand 0.83). corr V0 -0.05/-0.06, V2 -0.04/-0.05 (daily/weekly); stack k* 5.00; WF {6: (-169, 0.6), 12: (-271, 0.83)}; pre-2023 pos years 0/10.
* **pdhl_break rth=(570, 960),x_atr=0.1 london stop6ATR tgt 1R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.21 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -86/wk, p_rand 1.00, 12m: OOS -37/wk, p_rand 0.97). corr V0 0.01/0.06, V2 0.01/0.07 (daily/weekly); stack k* 5.00; WF {6: (-86, 1.0), 12: (-37, 0.97)}; pre-2023 pos years 7/10.
* **donchian k=5,mode=fade,n=34 nyam stop6ATR tgt 1R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.32 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -232/wk, p_rand 0.60, 12m: OOS -305/wk, p_rand 0.79) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.01/0.07, V2 -0.00/0.07 (daily/weekly); stack k* 0.00; WF {6: (-232, 0.6), 12: (-305, 0.79)}; pre-2023 pos years 0/10.
* **orb_failed anchor_hm=540,end_hm=840,fail_bars=10,minutes=15 pre stop4ATR tgt 1R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.22 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -48/wk, p_rand 0.35, 12m: OOS -1/wk, p_rand 0.17). corr V0 -0.01/-0.13, V2 -0.00/-0.10 (daily/weekly); stack k* 5.00; WF {6: (-48, 0.35), 12: (-1, 0.17)}; pre-2023 pos years 4/10.
* **pdhl_break rth=(570, 960),x_atr=0.25 london stop6ATR tgt 1R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.29 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -86/wk, p_rand 1.00, 12m: OOS -37/wk, p_rand 0.97). corr V0 0.01/0.05, V2 0.01/0.05 (daily/weekly); stack k* 5.00; WF {6: (-86, 1.0), 12: (-37, 0.97)}; pre-2023 pos years 6/10.
* **donchian k=5,mode=fade,n=34 nyam stop6ATR tgt 2R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.26 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -110/wk, p_rand 0.36, 12m: OOS -202/wk, p_rand 0.60) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.01/0.06, V2 -0.01/0.06 (daily/weekly); stack k* 0.00; WF {6: (-110, 0.36), 12: (-202, 0.6)}; pre-2023 pos years 0/10.
* **vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 nypm stop4ATR tgt none** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.16 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -201/wk, p_rand 0.66, 12m: OOS -212/wk, p_rand 0.69). corr V0 0.01/-0.05, V2 -0.01/-0.04 (daily/weekly); stack k* 5.00; WF {6: (-201, 0.66), 12: (-212, 0.69)}; pre-2023 pos years 2/10.

## 4. Limits
* 1-min bar simulator, entry at the open of the bar after the signal bar, costs from te2 proxies charged as market on every exit (conservative on targets); ticks / 1-s re-run of finalists is not done here (CL ticks exist; request via Z2 tick_rerun.py).
* Placebo worlds simulate only the HOLD window trades (2025-11..2026-10); family statistic z = min(HOLD z, L6M z) with 100 worlds per kind, so the smallest attainable p is 0.0099; the family max-statistic is over the F cells with >= 60 trades in 2023-26.
* Block A (keltner_flip, supertrend_flip, pullback_band, momentum_vote, hma_vwap_cross) and everything else on CL is another owner's family; the all-CL family size is larger than F.

Note (appended): section 2 p_book is the stage-2 per-cell p of z = min(HOLD z, L6M z) (HOLD-window placebo worlds); section 3 re-computes p_book inside the full evaluator (HOLD mean, L6M mean and the stack-Calmar-gain statistic with its own seed and full-history placebo sims), which is why the 13 per-cell-only cells show larger p there (0.16-0.32). Neither changes the family result: family p = 1.00 for all of them. Finalist trade frames: /mnt/l2/l2vast/instr2_trades/CL/<cell_id>.parquet (25 evaluated cells).
Correction to the note above: 10 cells were run through the full evaluator (the 10 best per-cell-only cells; 0 family survivors), so 10 trade frames come from this block (the CL folder also holds frames from other owners).


## REPAIRED-BLOCKB (Z1, 2026-11-06): block-B survivors and gate flips on the BAD-PRINT-REPAIRED bars, original vs repaired
Source of the repair: CHAR-C's repaired 1-min copies (find_c/cache_c, rule cc_audit.py: bars whose high/low/close lie more than 10 sigma + 4 ticks outside their neighbours are clamped; originals untouched). The block-B bars (ohlcv1m dbn files) were matched by timestamp to the repaired copy and the o/h/l/c of every matched bar replaced (changed bars: YM 995, CL 523, 6E 19,721, 6J 14,455; all other cells of the bars identical). Everything else is unchanged: same signal sets, brackets, costs, caps, evaluator, gate. Code l2vast/ds3/code/repair_z1/ (rerun.py, compare.py, doc.py); results /mnt/l2/l2vast/repair_z1/.
Method (stated limits): (1) STAGE 1 for EVERY cell of the grid on repaired bars (exact, deterministic): tolerant-gate and NOW-ONLY status compared with the stored original of the same cell. (2) Placebo worlds (HOLD-window hash/side/shift5/days worlds as in the block) re-run for every cell that is tolerant in the original OR the repaired version, on the repaired bars AND, with the same per-cell seed, on the original bars again (the 'control'), because the placebos draw random numbers and the original runs used a different random stream: original-vs-control differences are Monte-Carlo noise. (3) p_family is evaluated against the ORIGINAL family world-max distribution M (the full family of ~2,600-3,000 eligible cells was not re-simulated; a few changed cells cannot move the max of the family materially, but this is an approximation and is labelled so).
| instrument | bad bars repaired | cells scored | cells whose L6M or HOLD mean changed (any / > 10%) | tolerant gate: original -> repaired (lost / gained) | NOW-ONLY (lost / gained) | tolerant + p_book <= .10: original / original-bars rerun (MC control) / repaired | in both original and repaired | only original / only repaired | family-surviving (p_family <= .10): original -> repaired |
|---|---|---|---|---|---|---|---|---|---|
| CL | 523 | 2964 | 1673 / 540 | 242 -> 247 (3 / 8) | 15 / 13 | 13 / 17 / 16 | 11 | 2 / 5 | 0 -> 0 |
### CL - tolerant + p_book <= .10 in the original or in the repaired run (L6M / HOLD / PRE in $/wk at equal-risk lots, carry dropped; p_book original / original-bars rerun / repaired; p_family vs the original max)
| cell | L6M orig -> rep | HOLD orig -> rep | PRE orig -> rep | tolerant orig -> rep | p_book o / ctl / r | p_family o -> r |
|--|--|--|--|--|--|--|
| donchian k=5,mode=fade,n=34 nyam stop4ATR tgt 1R | +306 -> +288 | +316 -> +310 | -101 -> -105 | True -> True | 0.09 / 0.06 / 0.09 | 1.00 -> 1.00 |
| donchian k=5,mode=fade,n=34 nyam stop6ATR tgt 1R | +560 -> +560 | +465 -> +465 | -45 -> -48 | True -> True | 0.04 / 0.04 / 0.04 | 1.00 -> 1.00 |
| donchian k=5,mode=fade,n=34 nyam stop6ATR tgt 2R | +444 -> +444 | +410 -> +410 | +123 -> +120 | True -> True | 0.07 / 0.08 / 0.08 | 1.00 -> 1.00 |
| donchian k=5,mode=fade,n=34 nyam stop6ATR tgt none | +444 -> +444 | +410 -> +410 | +117 -> +114 | True -> True | 0.04 / 0.09 / 0.09 | 1.00 -> 1.00 |
| pdhl_break rth=(570, 960),x_atr=0.25 london stop3ATR tgt 2R | +780 -> +797 | +398 -> +405 | -221 -> -221 | True -> True | 0.03 / 0.02 / 0.04 | 1.00 -> 1.00 |
| pdhl_break rth=(570, 960),x_atr=0.25 london stop4ATR tgt 2R | +350 -> +368 | +238 -> +244 | -64 -> -64 | True -> True | 0.13 / 0.08 / 0.08 | 1.00 -> 1.00 |
| pdhl_break rth=(570, 960),x_atr=0.25 london stop6ATR tgt 1R | +342 -> +359 | +215 -> +222 | -79 -> -79 | True -> True | 0.09 / 0.05 / 0.09 | 1.00 -> 1.00 |
| donchian k=15,mode=break,n=55 pre stop3ATR tgt none | +164 -> +164 | +186 -> +188 | -38 -> -38 | True -> True | 0.17 / 0.10 / 0.10 | 1.00 -> 1.00 |
| pdhl_break rth=(570, 960),x_atr=0.1 london stop4ATR tgt 2R | +364 -> +382 | +190 -> +197 | -73 -> -53 | True -> True | 0.10 / 0.09 / 0.08 | 1.00 -> 1.00 |
| pdhl_break rth=(570, 960),x_atr=0.1 london stop6ATR tgt 1R | +385 -> +402 | +176 -> +183 | -130 -> -130 | True -> True | 0.05 / 0.05 / 0.07 | 1.00 -> 1.00 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 nypm stop2ATR tgt none | +433 -> +398 | +140 -> +76 | -169 -> -169 | True -> True | 0.09 / 0.19 / 0.24 | 1.00 -> 1.00 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 nypm stop4ATR tgt 2R | +331 -> +313 | +139 -> +110 | -70 -> -70 | True -> True | 0.11 / 0.09 / 0.10 | 1.00 -> 1.00 |
| vwap_reject anchor_hm=180,hold=5,min_bars=15,span_min=600 nypm stop4ATR tgt none | +291 -> +274 | +124 -> +95 | -63 -> -63 | True -> True | 0.09 / 0.10 / 0.13 | 1.00 -> 1.00 |
| orb_failed anchor_hm=540,end_hm=840,fail_bars=10,minutes=15 pre stop4ATR tgt 1R | +285 -> +285 | +264 -> +264 | +23 -> +38 | True -> True | 0.08 / 0.08 / 0.08 | 1.00 -> 1.00 |
| failed_or anchor_hm=540,minutes=15 pre stop4ATR tgt 1R | +386 -> +386 | +357 -> +357 | -1 -> +14 | True -> True | 0.11 / 0.07 / 0.07 | 1.00 -> 1.00 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=600 nyam stop3ATR tgt 2R | +809 -> +664 | +804 -> +748 | -488 -> -486 | True -> True | 0.04 / 0.07 / 0.07 | 1.00 -> 1.00 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=600 nyam stop4ATR tgt 2R | +611 -> +642 | +469 -> +481 | -364 -> -386 | True -> True | 0.12 / 0.14 / 0.09 | 1.00 -> 1.00 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=600 nyam stop4ATR tgt none | +528 -> +560 | +408 -> +420 | -368 -> -379 | True -> True | 0.06 / 0.05 / 0.04 | 1.00 -> 1.00 |

Full table and method limits: autopilot/REPAIRED_BARS_RERUN.md.
