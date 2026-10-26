# REPORT A3
**Verdict: NO** (0/6 gates; replication 0/2). Variant {} with {'hf': 20, 'hs': 55}: uplift vs the same 1-minute engine with the live NQ signals clean/H1/H2/all -0.04/+0.37/-0.36/-0.06.

A3 HM with the VWAP weighted by ES volume (NQ price x ES volume); ST unchanged.


Engine: 1-minute NQ (p1_core account, fixed 60/60 bracket, live rules, 1 tick/side + $34.88/8 lots), window 2023-02..2026-10; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04. Pre-declared variant.

| source | trades | trades/day | avg pts | win rate | whipsaws | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 2,816,378 | 1.65 / 2.60 / 2.04 |
| A3 variant | 6204 | 7.84 | +3.47 | 52.9% | 212 | 2,745,364 | 1.61 / 2.97 / 1.67 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.045 / +0.374 / -0.363
- [FAIL] 3 worst week not worse (all-in): -81,417 vs -78,823
- [FAIL] 4 own null p95 on all-in uplift: real -0.057 vs p95 +0.215 (median +0.083, rank 0.15, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-0.291, +0.168]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.048 / +0.248 / -0.353
- Replication H0: -0.625 -> FAIL; alternating months odd/even +0.097 / -0.172 -> FAIL

Plateau neighbours (all-in uplift vs the baseline engine): nb:hf x0.75: +0.132; nb:hf x1.25: +0.016; nb:hs x0.75: -0.061; nb:hs x1.25: +0.130

Null: ES shifted by a random whole number of weeks (60 draws). Executability: NT8 multi-series strategy computing the alternative price path in OnBarUpdate; orders and brackets on NQ unchanged; ERA not run (window 2023-26 only).

DONE A3