# REPORT A5
**Verdict: NO** (0/6 gates; replication 0/2). Variant {} with {'stp': 120, 'stm': 2.0, 'hf': 20, 'hs': 55}: uplift vs the same 1-minute engine with the live NQ signals clean/H1/H2/all -0.16/-1.26/-0.46/-0.41.

A5 composite ES+NQ price path re-sampled to composite-volume-clock bars; ST and HM on those bars.


Engine: 1-minute NQ (p1_core account, fixed 60/60 bracket, live rules, 1 tick/side + $34.88/8 lots), window 2023-02..2026-10; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04. Pre-declared variant.

| source | trades | trades/day | avg pts | win rate | whipsaws | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 2,816,378 | 1.65 / 2.60 / 2.04 |
| A5 variant | 5951 | 7.45 | +3.39 | 52.8% | 239 | 2,156,549 | 1.49 / 1.34 / 1.58 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.161 / -1.260 / -0.456
- [FAIL] 3 worst week not worse (all-in): -80,035 vs -78,823
- [FAIL] 4 own null p95 on all-in uplift: real -0.407 vs p95 -0.388 (median -0.911, rank 0.93, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-1.177, +0.350]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 8
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.302 / -1.237 / -0.481
- Replication H0: -1.239 -> FAIL; alternating months odd/even -1.019 / +0.261 -> FAIL

Plateau neighbours (all-in uplift vs the baseline engine): nb:stp x0.75: -0.380; nb:stp x1.25: -0.613; nb:stm x0.75: -0.351; nb:stm x1.25: -0.102; nb:hf x0.75: -0.633; nb:hf x1.25: -0.555; nb:hs x0.75: -0.539; nb:hs x1.25: -0.448

Null: ES shifted by a random whole number of weeks (60 draws). Executability: NT8 multi-series strategy computing the alternative price path in OnBarUpdate; orders and brackets on NQ unchanged; ERA not run (window 2023-26 only).

DONE A5