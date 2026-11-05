# DS3_INSTR2_6J_B - T-INSTR-2 6J family block B (ZL-2), 2026-11-05T22:29Z

Research only, $0, no PASS claims, Shadow only, nothing live. Scope l2vast/ds3/prereg/T2_6EJ_B_scope.md sha256 92604fab0e8c08ae0894003a201103e6394519f191f8f6736c40c8f55b34e90a (DECISIONS.md before any 6J cell). Evaluator l2vast/ds3/code/instr2/instr2_eval.py; code l2vast/ds3/code/instr2/t2cl/. Base: 6J.v.0 1-min 2013-2026-10-16, 1-min bar simulator, te2 cost proxies (fee $4.84 PROXY, 1 tick market / 2 ticks stop, market cost on every exit), equal-$ risk R $1,200, integer lots, participation caps; carrying weeks dropped; stack = Q1-A ts2 V0 and V2.

## Plain sentence
No 6J block-B cell clears the tolerant gate, the per-cell placebo and the family max-statistic together (3468 cells scored, 3018 testable for placebo, F = 3018): 6J block B yields no diversifier lead on this grid.

## 1. Counts (every cell is accounted for)
| stage | cells |
|--|--|
| cells in the grid (78 signal sets x 5 sessions x 12 brackets) | 4680 |
| untestable (< 10 trades over the data) | 1212 |
| scored (S1) | 3468 |
| with >= 60 trades 2023-04..2026-10 = placebo family F (S2) | 3018 |
| NOW-ONLY (L3M and L6M mean > 0) | 218 |
| tolerant gate + min sample (gate_v2a) | 36 |
| of those with persistence > 60% of windows | 18 |
| tolerant AND placebo p_book <= .10 (per cell; best-of-F, not a lead) | 7 |
| tolerant AND p_book <= .10 AND family max-stat p <= .10 | 0 |
n_tested for 6J block B = 4,680; all-instrument n_tested total at this moment: 1879995 (E.total_n_tested(), /mnt/l2/l2vast/instr2/n_tested.jsonl).

## 2. Best cells on the placebo statistic (min of HOLD and L6M z vs the placebo worlds), tolerant gate passers; per-cell p; family p
| cell | n 2023-26 | L1M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | persist | p_book | p_family | pre-2023 years (+ / n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| session_extreme_fade anchor_hm=570,cooldown=30,min_bars=30,span_min=390 nyam stop6ATR tgt 1R | 619 | -16 | +41 | +73 | -15 | +119 | -125 | -28 | 4838 | 50% | 0.03 | 1.00 | 0 / 10 |
| session_extreme_fade anchor_hm=180,cooldown=30,min_bars=30,span_min=600 nyam stop6ATR tgt none | 398 | +368 | +368 | +81 | +83 | +465 | -73 | -227 | 3473 | 75% | 0.03 | 1.00 | 0 / 10 |
| session_extreme_fade anchor_hm=180,cooldown=30,min_bars=30,span_min=600 nyam stop6ATR tgt 2R | 398 | +368 | +368 | +81 | +83 | +465 | -73 | -197 | 3473 | 75% | 0.03 | 1.00 | 1 / 10 |
| session_extreme_fade anchor_hm=570,cooldown=30,min_bars=30,span_min=390 nyam stop6ATR tgt none | 609 | -16 | +41 | +88 | -25 | +130 | -89 | +44 | 5617 | 62% | 0.03 | 1.00 | 0 / 10 |
| session_extreme_fade anchor_hm=570,cooldown=30,min_bars=30,span_min=390 nyam stop6ATR tgt 2R | 609 | -16 | +41 | +88 | -25 | +130 | -89 | +33 | 5617 | 62% | 0.03 | 1.00 | 0 / 10 |
| donchian k=5,mode=fade,n=55 nyam stop6ATR tgt 2R | 721 | +665 | +658 | +71 | -170 | -190 | -147 | -358 | 10278 | 50% | 0.10 | 1.00 | 1 / 10 |
| donchian k=5,mode=fade,n=34 pre stop4ATR tgt 1R | 616 | +55 | +32 | +39 | -193 | -796 | -199 | -506 | 11847 | 50% | 0.09 | 1.00 | 3 / 10 |
| donchian k=15,mode=fade,n=55 nyam stop4ATR tgt none | 424 | +903 | +879 | +243 | +34 | -4 | -158 | -264 | 6121 | 62% | 0.12 | 1.00 | 1 / 10 |
| session_extreme_fade anchor_hm=540,cooldown=30,min_bars=30,span_min=600 pre stop4ATR tgt 1R | 489 | +535 | +623 | +266 | -198 | -174 | -67 | -262 | 15021 | 50% | 0.17 | 1.00 | 2 / 10 |
| donchian k=15,mode=fade,n=55 nyam stop6ATR tgt none | 417 | +585 | +567 | +75 | +46 | +74 | -139 | -235 | 4789 | 75% | 0.25 | 1.00 | 1 / 10 |
| session_extreme_fade anchor_hm=540,cooldown=30,min_bars=30,span_min=600 pre stop4ATR tgt none | 487 | +585 | +673 | +258 | -315 | -148 | -227 | -65 | 19577 | 50% | 0.27 | 1.00 | 0 / 10 |
| donchian k=15,mode=fade,n=10 pre stop4ATR tgt 1R | 514 | +211 | +312 | +10 | -274 | -465 | +2 | -143 | 14537 | 62% | 0.26 | 1.00 | 3 / 10 |
| session_extreme_fade anchor_hm=540,cooldown=30,min_bars=30,span_min=600 pre stop4ATR tgt 2R | 487 | +585 | +673 | +254 | -300 | -149 | -223 | -105 | 19590 | 50% | 0.33 | 1.00 | 2 / 10 |
| session_extreme_fade anchor_hm=540,cooldown=30,min_bars=30,span_min=600 pre stop2ATR tgt 2R | 489 | +170 | +163 | +64 | -269 | -108 | -102 | -331 | 17025 | 50% | 0.48 | 1.00 | 2 / 10 |
| pdhl_fade rth=(570, 960),x_atr=0.25 london stop6ATR tgt 2R | 203 | +63 | +675 | +114 | -119 | -252 | -43 | +56 | 8262 | 62% | 0.50 | 1.00 | 1 / 10 |
| pdhl_fade rth=(570, 960),x_atr=0.1 london stop6ATR tgt 1R | 204 | +101 | +507 | +40 | -158 | -231 | -69 | +23 | 9012 | 62% | 0.52 | 1.00 | 1 / 10 |
| pdhl_fade rth=(570, 960),x_atr=0.1 london stop6ATR tgt none | 200 | +63 | +495 | +60 | -154 | -252 | -69 | +58 | 8793 | 62% | 0.55 | 1.00 | 1 / 10 |
| pdhl_fade rth=(570, 960),x_atr=0.25 london stop6ATR tgt none | 200 | +63 | +495 | +60 | -154 | -252 | -69 | +58 | 8793 | 62% | 0.57 | 1.00 | 1 / 10 |
| session_extreme_fade anchor_hm=540,cooldown=30,min_bars=30,span_min=600 pre stop3ATR tgt 2R | 488 | +375 | +474 | +71 | -366 | -212 | -39 | -128 | 21507 | 50% | 0.53 | 1.00 | 2 / 10 |
| pdhl_fade rth=(570, 960),x_atr=0.1 london stop6ATR tgt 2R | 203 | +63 | +675 | +114 | -119 | -252 | -43 | +56 | 8262 | 62% | 0.57 | 1.00 | 1 / 10 |
$/wk at equal-$-risk lots, carry-dropped. These are the best-of-F rows by construction: a low per-cell p among F = 3018 cells is expected for several cells by chance; only the family column counts.

## 3. Full evaluator (walk-forward over the family's parameter neighbours, correlation and stack effect V0/V2, bar verdict)
* **session_extreme_fade anchor_hm=570,cooldown=30,min_bars=30,span_min=390 nyam stop6ATR tgt 1R** [per-cell only (best-of-F, NOT a lead)]: FAILS: persistence 50% <= 60% | placebo p_book 0.91 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -22/wk, p_rand 0.01, 12m: OOS 34/wk, p_rand 0.00) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.02/0.11, V2 0.02/0.09 (daily/weekly); stack k* 0.00; WF {6: (-22, 0.01), 12: (34, 0.0)}; pre-2023 pos years 0/10.
* **session_extreme_fade anchor_hm=180,cooldown=30,min_bars=30,span_min=600 nyam stop6ATR tgt none** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.74 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -15/wk, p_rand 0.01, 12m: OOS -14/wk, p_rand 0.01). corr V0 -0.00/0.07, V2 0.01/0.05 (daily/weekly); stack k* 5.00; WF {6: (-15, 0.01), 12: (-14, 0.01)}; pre-2023 pos years 0/10.
* **session_extreme_fade anchor_hm=180,cooldown=30,min_bars=30,span_min=600 nyam stop6ATR tgt 2R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.73 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -15/wk, p_rand 0.00, 12m: OOS -14/wk, p_rand 0.01). corr V0 -0.00/0.06, V2 0.01/0.05 (daily/weekly); stack k* 5.00; WF {6: (-15, 0.0), 12: (-14, 0.01)}; pre-2023 pos years 1/10.
* **session_extreme_fade anchor_hm=570,cooldown=30,min_bars=30,span_min=390 nyam stop6ATR tgt none** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.90 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -15/wk, p_rand 0.01, 12m: OOS -14/wk, p_rand 0.01) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.03/0.12, V2 0.04/0.11 (daily/weekly); stack k* 0.00; WF {6: (-15, 0.01), 12: (-14, 0.01)}; pre-2023 pos years 0/10.
* **session_extreme_fade anchor_hm=570,cooldown=30,min_bars=30,span_min=390 nyam stop6ATR tgt 2R** [per-cell only (best-of-F, NOT a lead)]: FAILS: placebo p_book 0.86 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -15/wk, p_rand 0.00, 12m: OOS -14/wk, p_rand 0.01) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 0.03/0.12, V2 0.04/0.11 (daily/weekly); stack k* 0.00; WF {6: (-15, 0.0), 12: (-14, 0.01)}; pre-2023 pos years 0/10.
* **donchian k=5,mode=fade,n=55 nyam stop6ATR tgt 2R** [per-cell only (best-of-F, NOT a lead)]: FAILS: persistence 50% <= 60% | placebo p_book 0.75 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -115/wk, p_rand 0.00, 12m: OOS -12/wk, p_rand 0.00) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.00/-0.01, V2 -0.00/-0.04 (daily/weekly); stack k* 0.00; WF {6: (-115, 0.0), 12: (-12, 0.0)}; pre-2023 pos years 1/10.
* **donchian k=5,mode=fade,n=34 pre stop4ATR tgt 1R** [per-cell only (best-of-F, NOT a lead)]: FAILS: persistence 50% <= 60% | placebo p_book 0.86 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -392/wk, p_rand 0.16, 12m: OOS -51/wk, p_rand 0.00) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped). corr V0 -0.01/-0.09, V2 -0.00/-0.09 (daily/weekly); stack k* 0.00; WF {6: (-392, 0.16), 12: (-51, 0.0)}; pre-2023 pos years 3/10.

## 4. Limits
* 1-min bar simulator, entry at the open of the bar after the signal bar, costs from te2 proxies charged as market on every exit (conservative on targets); ticks / 1-s re-run of finalists is not done here (6J ticks exist; request via Z2 tick_rerun.py).
* Placebo worlds simulate only the HOLD window trades (2025-11..2026-10); family statistic z = min(HOLD z, L6M z) with 100 worlds per kind, so the smallest attainable p is 0.0099; the family max-statistic is over the F cells with >= 60 trades in 2023-26.
* Block A (keltner_flip, supertrend_flip, pullback_band, momentum_vote, hma_vwap_cross) and everything else on 6J is another owner's family; the all-6J family size is larger than F.
