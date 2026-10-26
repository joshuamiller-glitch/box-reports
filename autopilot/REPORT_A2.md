# REPORT A2
**Verdict: NO** (0/6 gates; replication 0/2). Variant {} with {'stp': 120, 'stm': 2.0}: uplift vs the same 1-minute engine with the live NQ signals clean/H1/H2/all -0.21/-0.39/-1.86/-0.66.

A2 Supertrend bands from NQ price with the ATR taken from ES bars (converted to NQ points); HM unchanged.


Engine: 1-minute NQ (p1_core account, fixed 60/60 bracket, live rules, 1 tick/side + $34.88/8 lots), window 2023-02..2026-10; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04. Pre-declared variant.

| source | trades | trades/day | avg pts | win rate | whipsaws | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 2,816,378 | 1.65 / 2.60 / 2.04 |
| A2 variant | 6275 | 7.87 | +2.37 | 51.9% | 216 | 1,934,248 | 1.44 / 2.20 / 0.17 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.211 / -0.394 / -1.862
- [FAIL] 3 worst week not worse (all-in): -84,963 vs -78,823
- [FAIL] 4 own null p95 on all-in uplift: real -0.659 vs p95 -0.235 (median -0.582, rank 0.38, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-1.213, -0.136]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.277 / -0.705 / -2.100
- Replication H0: -1.439 -> FAIL; alternating months odd/even -1.097 / -0.122 -> FAIL

Plateau neighbours (all-in uplift vs the baseline engine): nb:stp x0.75: -0.817; nb:stp x1.25: -0.490; nb:stm x0.75: -0.657; nb:stm x1.25: -0.498

Null: ES shifted by a random whole number of weeks (60 draws). Executability: NT8 multi-series strategy computing the alternative price path in OnBarUpdate; orders and brackets on NQ unchanged; ERA not run (window 2023-26 only).

DONE A2