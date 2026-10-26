# REPORT A1
**Verdict: NO** (1/6 gates; replication 0/2). Variant {} with {'stp': 60, 'stm': 2.0, 'emp': 100}: uplift vs the same 1-minute engine with the live NQ signals clean/H1/H2/all -0.57/-0.23/+0.36/-0.30.

A1 Supertrend on 2-minute NQ bars (period 60, mult 2.0, EMA 100), brackets on the 1-minute path; HM unchanged.


Engine: 1-minute NQ (p1_core account, fixed 60/60 bracket, live rules, 1 tick/side + $34.88/8 lots), window 2023-02..2026-10; engine baseline weekly Sharpe clean/H1/H2 1.65/2.60/2.04. Pre-declared variant.

| source | trades | trades/day | avg pts | win rate | whipsaws | net $ | Sharpe clean/H1/H2 |
|---|---|---|---|---|---|---|---|
| live NQ signals | 6230 | 7.85 | +3.59 | 53.0% | 206 | 2,816,378 | 1.65 / 2.60 / 2.04 |
| A1 variant | 5899 | 7.48 | +3.19 | 52.6% | 222 | 2,399,163 | 1.08 / 2.37 / 2.40 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.573 / -0.228 / +0.361
- [FAIL] 3 worst week not worse (all-in): -80,692 vs -78,823
- [PASS] 4 own null p95 on all-in uplift: real -0.299 vs p95 -1.824 (median -2.608, rank 1.00, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-0.932, +0.340]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 6
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.641 / -0.171 / +0.361
- Replication H0: -0.987 -> FAIL; alternating months odd/even -0.164 / -0.425 -> FAIL

Plateau neighbours (all-in uplift vs the baseline engine): nb:stp x0.75: -0.192; nb:stp x1.25: -0.281; nb:stm x0.75: -0.318; nb:stm x1.25: -0.179; nb:emp x0.75: -0.405; nb:emp x1.25: -0.304

Null: random signal times with the same count and side mix per book (60 draws). Executability: NT8 multi-series strategy computing the alternative price path in OnBarUpdate; orders and brackets on NQ unchanged; ERA not run (window 2023-26 only).

DONE A1