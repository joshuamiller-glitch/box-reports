# REPORT RX4
**Verdict: NO** (1/6 measured gates, replication 1/2 available; D1-harness class NO). Selected cell ER_ens_a0.25: all-in weekly Sharpe uplift clean/H1/H2/all +0.21/-0.08/-0.14/+0.12. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

RX4 RW8 efficiency-ratio cure: size up in trending regimes using the mean percentile of ER180/ER240/ER300 (single pre-declared cell, plateau fixed up front).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| ER_ens_a0.25 | +0.211 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.67 |
| clean | Sortino | 2.78 | 3.16 |
| clean | MAR | 4.75 | 4.71 |
| clean | net $ | 1,329,958.72 | 1,504,864.30 |
| clean | maxDD $ | 280,109.76 | 319,704.74 |
| clean | worst wk $ | -81,873.92 | -80,044.89 |
| clean | CVaR5 $ | -78,735.52 | -78,230.15 |
| clean | CVaR10 $ | -78,008.81 | -77,837.32 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.75 |
| H1 | Sortino | 6.09 | 6.87 |
| H1 | MAR | 3.91 | 4.86 |
| H1 | net $ | 593,797.44 | 727,443.14 |
| H1 | maxDD $ | 151,712.64 | 149,607.64 |
| H1 | worst wk $ | -78,287.36 | -78,311.05 |
| H1 | CVaR5 $ | -77,609.92 | -78,044.68 |
| H1 | CVaR10 $ | -66,029.97 | -77,814.37 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 2.15 |
| H2 | Sortino | 4.69 | 4.49 |
| H2 | MAR | 3.50 | 3.28 |
| H2 | net $ | 761,254.40 | 791,912.94 |
| H2 | maxDD $ | 217,425.28 | 241,425.88 |
| H2 | worst wk $ | -82,524.48 | -80,616.24 |
| H2 | CVaR5 $ | -81,088.96 | -79,309.88 |
| H2 | CVaR10 $ | -79,185.12 | -78,439.08 |
| H2 | % neg wk | 44.44 | 33.33 |
| all | weekly Sharpe | 1.86 | 1.98 |
| all | Sortino | 3.63 | 3.99 |
| all | MAR | 9.59 | 9.46 |
| all | net $ | 2,685,010.56 | 3,024,220.38 |
| all | maxDD $ | 280,109.76 | 319,704.74 |
| all | worst wk $ | -82,524.48 | -80,616.24 |
| all | CVaR5 $ | -79,220.34 | -78,501.79 |
| all | CVaR10 $ | -78,243.12 | -78,014.13 |
| all | % neg wk | 42.86 | 39.88 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.211 / -0.081 / -0.145
- [PASS] 3 worst week not worse (all-in): -80,616 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real +0.123 vs p95 +0.164 (median -0.117, rank 0.90, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.361, +0.598]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 40% of 5
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.333 / -0.140 / -0.183
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.30/+0.58/+0.56/+0.42
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: -0.038; a x1.25: +0.215; ER180 alone: -0.074; ER240 alone: +0.433; ER300 alone: -0.191

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.061)

- H0 2023-02-10..2023-07-31: uplift +0.268 -> PASS
- Alternating months: odd-selected ER_ens_a0.25 read on even +0.242; even-selected ER_ens_a0.25 read on odd -0.034 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Efficiency ratios of NQ closes over 180/240/300 minutes computed in-strategy; expanding percentile vs history; multiplier 0.5-1.5.

DONE RX4