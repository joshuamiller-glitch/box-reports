# DS3_INSTR2_6E_B - T-INSTR-2 6E family block B (ZL-2), 2026-11-05T22:29Z

Research only, $0, no PASS claims, Shadow only, nothing live. Scope l2vast/ds3/prereg/T2_6EJ_B_scope.md sha256 92604fab0e8c08ae0894003a201103e6394519f191f8f6736c40c8f55b34e90a (DECISIONS.md before any 6E cell). Evaluator l2vast/ds3/code/instr2/instr2_eval.py; code l2vast/ds3/code/instr2/t2cl/. Base: 6E.v.0 1-min 2013-2026-10-16, 1-min bar simulator, te2 cost proxies (fee $4.84 PROXY, 1 tick market / 2 ticks stop, market cost on every exit), equal-$ risk R $1,200, integer lots, participation caps; carrying weeks dropped; stack = Q1-A ts2 V0 and V2.

## Plain sentence
No 6E block-B cell clears the tolerant gate, the per-cell placebo and the family max-statistic together (2964 cells scored, 2604 testable for placebo, F = 2604): 6E block B yields no diversifier lead on this grid.

## 1. Counts (every cell is accounted for)
| stage | cells |
|--|--|
| cells in the grid (78 signal sets x 4 sessions x 12 brackets) | 3744 |
| untestable (< 10 trades over the data) | 780 |
| scored (S1) | 2964 |
| with >= 60 trades 2023-04..2026-10 = placebo family F (S2) | 2604 |
| NOW-ONLY (L3M and L6M mean > 0) | 214 |
| tolerant gate + min sample (gate_v2a) | 8 |
| of those with persistence > 60% of windows | 5 |
| tolerant AND placebo p_book <= .10 (per cell; best-of-F, not a lead) | 0 |
| tolerant AND p_book <= .10 AND family max-stat p <= .10 | 0 |
n_tested for 6E block B = 3,744; all-instrument n_tested total at this moment: 1872531 (E.total_n_tested(), /mnt/l2/l2vast/instr2/n_tested.jsonl).

## 2. Best cells on the placebo statistic (min of HOLD and L6M z vs the placebo worlds), tolerant gate passers; per-cell p; family p
| cell | n 2023-26 | L1M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | persist | p_book | p_family | pre-2023 years (+ / n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| donchian k=15,mode=fade,n=10 pre stop4ATR tgt 1R | 491 | +4 | +71 | +83 | +27 | +83 | -205 | -414 | 5596 | 75% | 0.11 | 1.00 | 4 / 10 |
| donchian k=15,mode=fade,n=10 pre stop6ATR tgt 2R | 481 | -47 | +10 | +82 | -8 | -164 | -64 | -350 | 5484 | 38% | 0.14 | 1.00 | 3 / 10 |
| donchian k=15,mode=fade,n=10 pre stop6ATR tgt none | 481 | -47 | +10 | +60 | -16 | -164 | -37 | -350 | 5827 | 38% | 0.15 | 1.00 | 3 / 10 |
| donchian k=1,mode=break,n=10 pre stop6ATR tgt none | 981 | +177 | +65 | +18 | -214 | +44 | -109 | -226 | 12466 | 62% | 0.17 | 1.00 | 0 / 10 |
| donchian k=5,mode=fade,n=55 nypm stop6ATR tgt 2R | 566 | +91 | +226 | +17 | -84 | -212 | -94 | +52 | 6396 | 62% | 0.23 | 1.00 | 3 / 10 |
| donchian k=5,mode=fade,n=55 nypm stop6ATR tgt none | 565 | +91 | +226 | +13 | -86 | -212 | -94 | +212 | 6396 | 62% | 0.24 | 1.00 | 1 / 10 |
| vwap_reclaim anchor_hm=570,hold=5,min_bars=15,span_min=390 nyam stop3ATR tgt none | 1247 | +334 | +124 | +104 | -716 | -2102 | -360 | -380 | 32155 | 50% | 0.37 | 1.00 | 0 / 10 |
| failed_pdhl N=10,X=0.25,rth=(570, 960) london stop2ATR tgt 2R | 196 | +15 | +15 | +7 | -20 | +133 | +24 | -35 | 4647 | 75% | 0.86 | 1.00 | 3 / 10 |
$/wk at equal-$-risk lots, carry-dropped. These are the best-of-F rows by construction: a low per-cell p among F = 2604 cells is expected for several cells by chance; only the family column counts.

## 3. Full evaluator (walk-forward over the family's parameter neighbours, correlation and stack effect V0/V2, bar verdict)
No cell reached the full evaluator stage.

## 4. Limits
* 1-min bar simulator, entry at the open of the bar after the signal bar, costs from te2 proxies charged as market on every exit (conservative on targets); ticks / 1-s re-run of finalists is not done here (6E ticks exist; request via Z2 tick_rerun.py).
* Placebo worlds simulate only the HOLD window trades (2025-11..2026-10); family statistic z = min(HOLD z, L6M z) with 100 worlds per kind, so the smallest attainable p is 0.0099; the family max-statistic is over the F cells with >= 60 trades in 2023-26.
* Block A (keltner_flip, supertrend_flip, pullback_band, momentum_vote, hma_vwap_cross) and everything else on 6E is another owner's family; the all-6E family size is larger than F.


## REPAIRED-BLOCKB (Z1, 2026-11-06): block-B survivors and gate flips on the BAD-PRINT-REPAIRED bars, original vs repaired
Source of the repair: CHAR-C's repaired 1-min copies (find_c/cache_c, rule cc_audit.py: bars whose high/low/close lie more than 10 sigma + 4 ticks outside their neighbours are clamped; originals untouched). The block-B bars (ohlcv1m dbn files) were matched by timestamp to the repaired copy and the o/h/l/c of every matched bar replaced (changed bars: YM 995, CL 523, 6E 19,721, 6J 14,455; all other cells of the bars identical). Everything else is unchanged: same signal sets, brackets, costs, caps, evaluator, gate. Code l2vast/ds3/code/repair_z1/ (rerun.py, compare.py, doc.py); results /mnt/l2/l2vast/repair_z1/.
Method (stated limits): (1) STAGE 1 for EVERY cell of the grid on repaired bars (exact, deterministic): tolerant-gate and NOW-ONLY status compared with the stored original of the same cell. (2) Placebo worlds (HOLD-window hash/side/shift5/days worlds as in the block) re-run for every cell that is tolerant in the original OR the repaired version, on the repaired bars AND, with the same per-cell seed, on the original bars again (the 'control'), because the placebos draw random numbers and the original runs used a different random stream: original-vs-control differences are Monte-Carlo noise. (3) p_family is evaluated against the ORIGINAL family world-max distribution M (the full family of ~2,600-3,000 eligible cells was not re-simulated; a few changed cells cannot move the max of the family materially, but this is an approximation and is labelled so).
| instrument | bad bars repaired | cells scored | cells whose L6M or HOLD mean changed (any / > 10%) | tolerant gate: original -> repaired (lost / gained) | NOW-ONLY (lost / gained) | tolerant + p_book <= .10: original / original-bars rerun (MC control) / repaired | in both original and repaired | only original / only repaired | family-surviving (p_family <= .10): original -> repaired |
|---|---|---|---|---|---|---|---|---|---|
| 6E | 19721 | 2964 | 2120 / 256 | 8 -> 10 (0 / 2) | 0 / 0 | 0 / 1 / 1 | 0 | 0 / 1 | 0 -> 0 |
### 6E - tolerant + p_book <= .10 in the original or in the repaired run (L6M / HOLD / PRE in $/wk at equal-risk lots, carry dropped; p_book original / original-bars rerun / repaired; p_family vs the original max)
| cell | L6M orig -> rep | HOLD orig -> rep | PRE orig -> rep | tolerant orig -> rep | p_book o / ctl / r | p_family o -> r |
|--|--|--|--|--|--|--|
| donchian k=15,mode=fade,n=10 pre stop4ATR tgt 1R | +83 -> +83 | +27 -> +20 | -205 -> -205 | True -> True | 0.11 / 0.07 / 0.08 | 1.00 -> 1.00 |

Full table and method limits: autopilot/REPAIRED_BARS_RERUN.md.
