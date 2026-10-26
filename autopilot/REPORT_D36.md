# REPORT D36
**Verdict: NO** (2/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell VPIN30_hi_q0.67_x0.0_BLOCK: all-in weekly Sharpe uplift clean/H1/H2/all +0.55/-1.47/+0.48/+0.24. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

D36 VPIN approximation (mean per-minute |imbalance| over 30 minutes) tilt and switch.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| VPIN30_hi_q0.67_x0.0_BLOCK | +0.549 | 0.285 |
| VPIN30_hi_q0.8_x0.0_BLOCK | +0.459 | 0.172 |
| VPIN30_BLOCK_a0.5_sg-1 | +0.317 | 0.999 |
| VPIN30_hi_q0.67_x0.5_BLOCK | +0.115 | 0.285 |
| VPIN30_hi_q0.8_x0.5_BLOCK | -0.008 | 0.172 |
| VPIN30_BLOCK_a0.25_sg-1 | -0.168 | 0.999 |
| VPIN30_hi_q0.8_x0.5_ALL | -0.264 | 0.189 |
| VPIN30_ALL_a0.25_sg+1 | -0.271 | 1.000 |
| VPIN30_ALL_a0.25_sg-1 | -0.276 | 1.000 |
| VPIN30_ALL_a0.5_sg-1 | -0.296 | 1.000 |
| VPIN30_BLOCK_a0.25_sg+1 | -0.531 | 0.999 |
| VPIN30_BLOCK_a0.5_sg+1 | -0.603 | 0.999 |
| VPIN30_hi_q0.67_x0.5_ALL | -0.692 | 0.336 |
| VPIN30_ALL_a0.5_sg+1 | -0.836 | 1.000 |
| VPIN30_hi_q0.8_x0.0_ALL | -1.104 | 0.189 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 2.01 |
| clean | Sortino | 2.78 | 3.85 |
| clean | MAR | 4.75 | 4.81 |
| clean | net $ | 1,329,958.72 | 1,586,193.60 |
| clean | maxDD $ | 280,109.76 | 329,747.52 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -79,141.17 |
| clean | CVaR10 $ | -78,008.81 | -75,183.01 |
| clean | % neg wk | 42.86 | 40.95 |
| H1 | weekly Sharpe | 2.83 | 1.35 |
| H1 | Sortino | 6.09 | 2.35 |
| H1 | MAR | 3.91 | 1.30 |
| H1 | net $ | 593,797.44 | 293,272.00 |
| H1 | maxDD $ | 151,712.64 | 225,796.48 |
| H1 | worst wk $ | -78,287.36 | -78,597.12 |
| H1 | CVaR5 $ | -77,609.92 | -78,282.72 |
| H1 | CVaR10 $ | -66,029.97 | -77,832.64 |
| H1 | % neg wk | 39.29 | 42.86 |
| H2 | weekly Sharpe | 2.30 | 2.77 |
| H2 | Sortino | 4.69 | 6.04 |
| H2 | MAR | 3.50 | 5.18 |
| H2 | net $ | 761,254.40 | 865,317.44 |
| H2 | maxDD $ | 217,425.28 | 166,968.96 |
| H2 | worst wk $ | -82,524.48 | -79,763.20 |
| H2 | CVaR5 $ | -81,088.96 | -79,052.96 |
| H2 | CVaR10 $ | -79,185.12 | -78,557.12 |
| H2 | % neg wk | 44.44 | 36.11 |
| all | weekly Sharpe | 1.86 | 2.09 |
| all | Sortino | 3.63 | 4.04 |
| all | MAR | 9.59 | 8.32 |
| all | net $ | 2,685,010.56 | 2,744,783.04 |
| all | maxDD $ | 280,109.76 | 329,747.52 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -79,191.15 |
| all | CVaR10 $ | -78,243.12 | -77,203.07 |
| all | % neg wk | 42.86 | 40.48 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.549 / -1.474 / +0.479
- [PASS] 3 worst week not worse (all-in): -81,874 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.236 vs p95 +0.105 (median -0.497, rank 0.99, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.497, +0.961]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.654 / -1.320 / +0.467
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.62/-0.49/+1.63/+0.64
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): q x0.75: -0.201; q x1.25: +0.090

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.118)

- H0 2023-02-10..2023-07-31: uplift -1.109 -> FAIL
- Alternating months: odd-selected VPIN30_hi_q0.8_x0.0_BLOCK read on even -0.263; even-selected VPIN30_hi_q0.8_x0.5_ALL read on odd -1.007 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. VPIN approximation from per-minute tick-rule imbalance; multiplier or halve.

DONE D36