# REPORT RW8
**Verdict: LEAD** (4/6 measured gates, replication 1/2 available; D1-harness class NO). Selected cell ER240_ALL_a0.25_sg+1: all-in weekly Sharpe uplift clean/H1/H2/all +0.40/+0.65/+0.22/+0.43. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

R8 trailing efficiency-ratio regime tilt (24 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| ER240_ALL_a0.25_sg+1 | +0.398 | 1.000 |
| ER240_BLOCK_a0.25_sg+1 | +0.279 | 0.999 |
| ER120_ALL_a0.5_sg+1 | +0.219 | 1.000 |
| ER120_BLOCK_a0.5_sg+1 | +0.118 | 1.000 |
| ER240_BLOCK_a0.5_sg+1 | +0.093 | 0.999 |
| ER60_BLOCK_a0.25_sg-1 | +0.071 | 0.999 |
| ER60_BLOCK_a0.5_sg-1 | +0.055 | 0.999 |
| ER60_ALL_a0.25_sg-1 | +0.044 | 1.000 |
| ER240_ALL_a0.5_sg+1 | -0.024 | 1.000 |
| ER60_ALL_a0.5_sg+1 | -0.045 | 1.000 |
| ER120_ALL_a0.25_sg+1 | -0.046 | 1.000 |
| ER60_ALL_a0.5_sg-1 | -0.090 | 1.000 |
| ER120_BLOCK_a0.25_sg-1 | -0.130 | 1.000 |
| ER60_BLOCK_a0.5_sg+1 | -0.226 | 0.999 |
| ER120_BLOCK_a0.25_sg+1 | -0.246 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.86 |
| clean | Sortino | 2.78 | 3.63 |
| clean | MAR | 4.75 | 5.42 |
| clean | net $ | 1,329,958.72 | 1,688,340.33 |
| clean | maxDD $ | 280,109.76 | 311,460.38 |
| clean | worst wk $ | -81,873.92 | -79,814.81 |
| clean | CVaR5 $ | -78,735.52 | -78,229.81 |
| clean | CVaR10 $ | -78,008.81 | -77,838.85 |
| clean | % neg wk | 42.86 | 40.95 |
| H1 | weekly Sharpe | 2.83 | 3.47 |
| H1 | Sortino | 6.09 | 9.87 |
| H1 | MAR | 3.91 | 5.96 |
| H1 | net $ | 593,797.44 | 879,349.10 |
| H1 | maxDD $ | 151,712.64 | 147,588.15 |
| H1 | worst wk $ | -78,287.36 | -79,591.25 |
| H1 | CVaR5 $ | -77,609.92 | -78,360.69 |
| H1 | CVaR10 $ | -66,029.97 | -61,067.95 |
| H1 | % neg wk | 39.29 | 32.14 |
| H2 | weekly Sharpe | 2.30 | 2.51 |
| H2 | Sortino | 4.69 | 5.40 |
| H2 | MAR | 3.50 | 3.85 |
| H2 | net $ | 761,254.40 | 927,007.99 |
| H2 | maxDD $ | 217,425.28 | 240,805.59 |
| H2 | worst wk $ | -82,524.48 | -80,056.90 |
| H2 | CVaR5 $ | -81,088.96 | -79,939.15 |
| H2 | CVaR10 $ | -79,185.12 | -79,158.10 |
| H2 | % neg wk | 44.44 | 33.33 |
| all | weekly Sharpe | 1.86 | 2.29 |
| all | Sortino | 3.63 | 4.79 |
| all | MAR | 9.59 | 11.22 |
| all | net $ | 2,685,010.56 | 3,494,697.42 |
| all | maxDD $ | 280,109.76 | 311,460.38 |
| all | worst wk $ | -82,524.48 | -80,056.90 |
| all | CVaR5 $ | -79,220.34 | -78,936.11 |
| all | CVaR10 $ | -78,243.12 | -78,232.72 |
| all | % neg wk | 42.86 | 38.10 |

## Gate checklist

- [PASS] 3 uplift>=+0.10 clean/H1/H2: +0.398 / +0.647 / +0.219
- [PASS] 3 worst week not worse (all-in): -80,057 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.433 vs p95 +0.190 (median -0.142, rank 1.00, n=100)
- [PASS] 4 bootstrap 90% CI >0: [+0.036, +0.837]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 33% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.332 / +0.578 / -0.259
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.54/+0.73/+0.63/+0.61
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.399; a x1.25: +0.128; W 120: +0.056

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.216)

- H0 2023-02-10..2023-07-31: uplift +0.379 -> PASS
- Alternating months: odd-selected ER240_BLOCK_a0.25_sg+1 read on even +0.368; even-selected ER240_BLOCK_a0.5_sg+1 read on odd +0.036 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Efficiency ratio of NQ closes over the last W minutes computed in-strategy; multiplier 0.5-1.5.

DONE RW8