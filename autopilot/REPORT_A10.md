# REPORT A10
**Verdict: NO** (1/6 gates; replication 0/2). Variant {} with {'stp': 120, 'stm': 2.0}: uplift vs the same 1-minute engine with the live NQ signals clean/H1/H2/all -0.46/+0.03/-0.02/-0.25.

A10 Supertrend computed on a 3-bar causal median of the close; HM unchanged.


Engine: 1-minute NQ (p1_core account, fixed 60/60 bracket, live rules, 1 tick/side + $34.88/8 lots), window 2023-02..2026-10; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04. Pre-declared variant.

| source | trades | trades/day | avg pts | win rate | whipsaws | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 2,816,378 | 1.65 / 2.60 / 2.04 |
| A10 variant | 5908 | 7.45 | +3.83 | 53.1% | 210 | 2,589,929 | 1.19 / 2.63 / 2.02 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.459 / +0.031 / -0.016
- [FAIL] 3 worst week not worse (all-in): -80,791 vs -78,823
- [PASS] 4 own null p95 on all-in uplift: real -0.249 vs p95 -1.586 (median -2.455, rank 1.00, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-0.939, +0.425]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.575 / +0.155 / +0.107
- Replication H0: -1.394 -> FAIL; alternating months odd/even -0.285 / -0.059 -> FAIL

Plateau neighbours (all-in uplift vs the baseline engine): nb:stp x0.75: -0.100; nb:stp x1.25: -0.304; nb:stm x0.75: -0.340; nb:stm x1.25: -0.565

Null: random signal times with the same count and side mix per book (60 draws). Executability: NT8 multi-series strategy computing the alternative price path in OnBarUpdate; orders and brackets on NQ unchanged; ERA not run (window 2023-26 only).

DONE A10