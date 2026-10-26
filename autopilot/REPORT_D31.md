# REPORT D31
**Verdict: NO** (1/6 measured gates, replication 1/2 available; D1-harness class NO). Selected cell BIG5_ALL_a0.25_sg+1: all-in weekly Sharpe uplift clean/H1/H2/all +0.06/+0.11/-0.64/-0.07. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

D31 large-trade volume share tilt (BIG5/BIG15; share not imbalance because the frame has unsigned big-trade volume).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| BIG5_ALL_a0.25_sg+1 | +0.059 | 1.000 |
| BIG15_BLOCK_a0.25_sg+1 | +0.015 | 0.999 |
| BIG15_BLOCK_a0.5_sg+1 | -0.018 | 0.999 |
| BIG5_BLOCK_a0.25_sg+1 | -0.026 | 0.999 |
| BIG15_ALL_a0.5_sg+1 | -0.243 | 1.000 |
| BIG5_BLOCK_a0.5_sg+1 | -0.388 | 0.999 |
| BIG15_ALL_a0.25_sg+1 | -0.392 | 1.000 |
| BIG5_ALL_a0.5_sg+1 | -0.480 | 1.000 |
| BIG15_ALL_a0.25_sg-1 | -0.545 | 1.000 |
| BIG15_BLOCK_a0.25_sg-1 | -0.624 | 0.999 |
| BIG5_ALL_a0.25_sg-1 | -0.754 | 1.000 |
| BIG5_BLOCK_a0.25_sg-1 | -0.878 | 0.999 |
| BIG15_BLOCK_a0.5_sg-1 | -0.889 | 0.999 |
| BIG15_ALL_a0.5_sg-1 | -0.981 | 1.000 |
| BIG5_ALL_a0.5_sg-1 | -1.098 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.52 |
| clean | Sortino | 2.78 | 2.70 |
| clean | MAR | 4.75 | 4.98 |
| clean | net $ | 1,329,958.72 | 1,390,574.20 |
| clean | maxDD $ | 280,109.76 | 279,459.41 |
| clean | worst wk $ | -81,873.92 | -81,346.07 |
| clean | CVaR5 $ | -78,735.52 | -78,922.09 |
| clean | CVaR10 $ | -78,008.81 | -78,329.36 |
| clean | % neg wk | 42.86 | 38.10 |
| H1 | weekly Sharpe | 2.83 | 2.94 |
| H1 | Sortino | 6.09 | 6.90 |
| H1 | MAR | 3.91 | 5.00 |
| H1 | net $ | 593,797.44 | 699,634.93 |
| H1 | maxDD $ | 151,712.64 | 139,821.78 |
| H1 | worst wk $ | -78,287.36 | -78,420.95 |
| H1 | CVaR5 $ | -77,609.92 | -77,768.94 |
| H1 | CVaR10 $ | -66,029.97 | -72,836.13 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 1.66 |
| H2 | Sortino | 4.69 | 3.20 |
| H2 | MAR | 3.50 | 2.65 |
| H2 | net $ | 761,254.40 | 561,204.19 |
| H2 | maxDD $ | 217,425.28 | 211,971.32 |
| H2 | worst wk $ | -82,524.48 | -79,811.65 |
| H2 | CVaR5 $ | -81,088.96 | -79,639.78 |
| H2 | CVaR10 $ | -79,185.12 | -78,704.39 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.79 |
| all | Sortino | 3.63 | 3.34 |
| all | MAR | 9.59 | 9.49 |
| all | net $ | 2,685,010.56 | 2,651,413.32 |
| all | maxDD $ | 280,109.76 | 279,459.41 |
| all | worst wk $ | -82,524.48 | -81,346.07 |
| all | CVaR5 $ | -79,220.34 | -79,046.13 |
| all | CVaR10 $ | -78,243.12 | -78,359.83 |
| all | % neg wk | 42.86 | 39.88 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.059 / +0.109 / -0.636
- [PASS] 3 worst week not worse (all-in): -81,346 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.068 vs p95 +0.149 (median -0.128, rank 0.63, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.550, +0.420]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.146 / +0.134 / -0.780
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.18/+0.49/-0.18/+0.16
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.004; a x1.25: -0.165; feat BIG15: -0.500

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.034)

- H0 2023-02-10..2023-07-31: uplift +0.236 -> PASS
- Alternating months: odd-selected BIG15_ALL_a0.25_sg-1 read on even -0.637; even-selected BIG5_BLOCK_a0.25_sg+1 read on odd -0.521 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Large-trade volume share from the NT8 tick stream (trade size threshold as in the data pipeline); multiplier 0.5-1.5.

DONE D31