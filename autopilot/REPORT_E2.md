# REPORT E2 - ES-keyed exits for the pair's NQ trades
**Verdict: NO** (0/6 gates; replication 1/2). Selected clean-only cell adv_0.2_None: uplift vs the same engine without ES exits clean/H1/H2/all -0.25/-0.87/+0.10/-0.26.

E2 ES-keyed exits: early exit of the NQ trade when ES moves adversely, flips its own supertrend, or fails to confirm within N minutes.


Engine: as E1 (1-minute NQ, fixed 60/60 bracket, live rules); exit rule evaluated on ES closes aligned by minute; early exit at the NEXT NQ bar open after the trigger bar. Baseline = same engine without the ES exit. 1 tick/side + $34.88/8 lots.

## Clean-span grid (10 cells)

| cell | clean Sharpe | clean uplift | trades/day | avg pts | win rate |
|---|---|---|---|---|---|
| adv_0.2_None | 1.41 | -0.247 | 8.30 | +3.22 | 51.0% |
| adv_0.1_None | 1.23 | -0.420 | 10.72 | +2.35 | 42.2% |
| adv_0.15_None | 1.23 | -0.423 | 8.99 | +2.50 | 47.9% |
| conf_10_0.02 | 0.64 | -1.016 | 22.24 | +1.06 | 42.5% |
| conf_20_0.02 | 0.19 | -1.458 | 17.66 | +1.11 | 41.6% |
| conf_5_0.02 | -0.56 | -2.217 | 27.74 | +0.47 | 42.2% |
| conf_20_0.05 | -0.84 | -2.490 | 26.50 | +0.65 | 46.5% |
| conf_10_0.05 | -1.30 | -2.948 | 35.00 | +0.54 | 47.3% |
| flip_None_None | -1.36 | -3.008 | 36.20 | +0.35 | 38.5% |
| conf_5_0.05 | -3.47 | -5.127 | 42.45 | +0.18 | 47.3% |
| base (no ES exit) | 1.65 | 0 | 7.85 | +3.59 | 53.0% |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: -0.247 / -0.865 / +0.102
- [FAIL] 3 worst week not worse (all-in): -84,323 vs -78,823
- [FAIL] 4 own null p95 on all-in uplift: real -0.260 vs p95 +0.038 (median -0.331, rank 0.60, n=60)
- [FAIL] 4 bootstrap 90% CI >0: [-0.617, +0.080]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.200 / -0.720 / +0.113
- Replication H0: +0.777 -> PASS; alternating months odd/even +0.022 / -0.505 -> FAIL

Plateau neighbours (all-in uplift): nb:x x0.75: -0.525; nb:x x1.25: -0.009

Executability: NT8 two-series strategy (NQ + ES); the exit check runs in OnBarUpdate on ES closes and sends a market exit on NQ; no extra margin. ERA: not run.

DONE E2