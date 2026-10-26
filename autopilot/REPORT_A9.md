# REPORT A9
**Verdict: NO** (0/6 gates; replication 0/2). Variant {} with {'hf': 20, 'hs': 55}: uplift vs the same 1-minute engine with the live NQ signals clean/H1/H2/all -0.16/+1.03/-1.19/-0.28.

A9 HM on the ES deviation from its own VWAP scaled to NQ; ST unchanged.


Engine: 1-minute NQ (p1_core account, fixed 60/60 bracket, live rules, 1 tick/side + $34.88/8 lots), window 2023-02..2026-10; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04. Pre-declared variant.

| source | trades | trades/day | avg pts | win rate | whipsaws | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 2,816,378 | 1.65 / 2.60 / 2.04 |
| A9 variant | 6203 | 7.80 | +3.82 | 53.2% | 222 | 2,614,039 | 1.50 / 3.62 / 0.85 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.156 / +1.027 / -1.189
- [FAIL] 3 worst week not worse (all-in): -79,233 vs -78,823
- [FAIL] 4 own null p95 on all-in uplift: real -0.275 vs p95 +0.003 (median -0.561, rank 0.88, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-0.914, +0.342]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.183 / +1.005 / -1.268
- Replication H0: -0.426 -> FAIL; alternating months odd/even -0.996 / +0.517 -> FAIL

Plateau neighbours (all-in uplift vs the baseline engine): nb:hf x0.75: -0.091; nb:hf x1.25: -0.497; nb:hs x0.75: -0.051; nb:hs x1.25: -0.441

Null: ES shifted by a random whole number of weeks (60 draws). Executability: NT8 multi-series strategy computing the alternative price path in OnBarUpdate; orders and brackets on NQ unchanged; ERA not run (window 2023-26 only).

DONE A9