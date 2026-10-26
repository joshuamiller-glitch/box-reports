# REPORT A8
**Verdict: NO** (0/6 gates; replication 0/2). Variant {'k': 3, 'conf': 'maj'} with {}: uplift vs the same 1-minute engine with the live NQ signals clean/H1/H2/all +0.07/-0.08/-0.97/-0.23.

A8 NQ flips confirmed by an ES (or NQ+ES+RTY majority) same-direction flip within k bars (6 cells).


Engine: 1-minute NQ (p1_core account, fixed 60/60 bracket, live rules, 1 tick/side + $34.88/8 lots), window 2023-02..2026-10; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04. Pre-declared variant; cell grid 6 with clean-only selection.

| source | trades | trades/day | avg pts | win rate | whipsaws | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 2,816,378 | 1.65 / 2.60 / 2.04 |
| A8 variant | 6095 | 7.61 | +3.52 | 53.0% | 221 | 2,519,886 | 1.72 / 2.52 / 1.06 |

Clean-span grid: {'k': 1, 'conf': 'es'} 0.56; {'k': 1, 'conf': 'maj'} 1.31; {'k': 2, 'conf': 'es'} 0.62; {'k': 2, 'conf': 'maj'} 1.24; {'k': 3, 'conf': 'es'} 1.24; {'k': 3, 'conf': 'maj'} 1.72

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.069 / -0.078 / -0.973
- [FAIL] 3 worst week not worse (all-in): -85,847 vs -78,823
- [FAIL] 4 own null p95 on all-in uplift: real -0.230 vs p95 +0.163 (median -0.253, rank 0.57, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-0.972, +0.483]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.041 / -0.034 / -1.162
- Replication H0: -1.825 -> FAIL; alternating months odd/even -0.658 / +0.269 -> FAIL

Plateau neighbours (all-in uplift vs the baseline engine): nb:k x0.75: -0.501; nb:k x1.25: -0.089

Null: ES shifted by a random whole number of weeks (60 draws). Executability: NT8 multi-series strategy computing the alternative price path in OnBarUpdate; orders and brackets on NQ unchanged; ERA not run (window 2023-26 only).

DONE A8