# REPORT A7
**Verdict: NO** (1/6 gates; replication 0/2). Variant {'qr': 0.2} with {'hf': 20, 'hs': 55, 'qr': None}: uplift vs the same 1-minute engine with the live NQ signals clean/H1/H2/all +0.05/-0.97/-0.33/-0.20.

A7 Kalman-filtered close (local level, qr in 0.05/0.2) as the HM input; ST unchanged.


Engine: 1-minute NQ (p1_core account, fixed 60/60 bracket, live rules, 1 tick/side + $34.88/8 lots), window 2023-02..2026-10; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04. Pre-declared variant; cell grid 2 with clean-only selection.

| source | trades | trades/day | avg pts | win rate | whipsaws | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 2,816,378 | 1.65 / 2.60 / 2.04 |
| A7 variant | 6195 | 7.75 | +3.50 | 52.9% | 212 | 2,584,718 | 1.70 / 1.62 / 1.70 |

Clean-span grid: {'qr': 0.05} 1.23; {'qr': 0.2} 1.70

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.051 / -0.973 / -0.332
- [FAIL] 3 worst week not worse (all-in): -79,251 vs -78,823
- [PASS] 4 own null p95 on all-in uplift: real -0.205 vs p95 -1.668 (median -2.478, rank 1.00, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-0.737, +0.359]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.093 / -0.892 / -0.353
- Replication H0: -1.136 -> FAIL; alternating months odd/even -0.279 / -0.119 -> FAIL

Plateau neighbours (all-in uplift vs the baseline engine): nb:hf x0.75: -0.179; nb:hf x1.25: -0.256; nb:hs x0.75: -0.123; nb:hs x1.25: -0.128; nb:qr x0.75: -0.206; nb:qr x1.25: +0.023

Null: random signal times with the same count and side mix per book (60 draws). Executability: NT8 multi-series strategy computing the alternative price path in OnBarUpdate; orders and brackets on NQ unchanged; ERA not run (window 2023-26 only).

DONE A7