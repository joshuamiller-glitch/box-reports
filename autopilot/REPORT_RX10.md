# REPORT RX10
**Verdict: LEAD** (4/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell K4ens_a0.25: all-in weekly Sharpe uplift clean/H1/H2/all +0.03/+0.93/+0.36/+0.25. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

RX10 RW5 K4 modulator with the 5-seed K4 probability ensemble (single pre-declared cell).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| K4ens_a0.25 | +0.035 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.49 |
| clean | Sortino | 2.78 | 2.86 |
| clean | MAR | 4.75 | 4.66 |
| clean | net $ | 1,329,958.72 | 1,433,994.83 |
| clean | maxDD $ | 280,109.76 | 307,772.08 |
| clean | worst wk $ | -81,873.92 | -78,675.42 |
| clean | CVaR5 $ | -78,735.52 | -78,105.22 |
| clean | CVaR10 $ | -78,008.81 | -77,713.73 |
| clean | % neg wk | 42.86 | 40.95 |
| H1 | weekly Sharpe | 2.83 | 3.76 |
| H1 | Sortino | 6.09 | 10.16 |
| H1 | MAR | 3.91 | 6.78 |
| H1 | net $ | 593,797.44 | 924,676.55 |
| H1 | maxDD $ | 151,712.64 | 136,444.63 |
| H1 | worst wk $ | -78,287.36 | -78,406.53 |
| H1 | CVaR5 $ | -77,609.92 | -77,792.30 |
| H1 | CVaR10 $ | -66,029.97 | -67,739.17 |
| H1 | % neg wk | 39.29 | 28.57 |
| H2 | weekly Sharpe | 2.30 | 2.65 |
| H2 | Sortino | 4.69 | 5.68 |
| H2 | MAR | 3.50 | 3.88 |
| H2 | net $ | 761,254.40 | 881,873.16 |
| H2 | maxDD $ | 217,425.28 | 227,530.08 |
| H2 | worst wk $ | -82,524.48 | -80,213.45 |
| H2 | CVaR5 $ | -81,088.96 | -79,936.01 |
| H2 | CVaR10 $ | -79,185.12 | -77,656.06 |
| H2 | % neg wk | 44.44 | 36.11 |
| all | weekly Sharpe | 1.86 | 2.11 |
| all | Sortino | 3.63 | 4.31 |
| all | MAR | 9.59 | 10.53 |
| all | net $ | 2,685,010.56 | 3,240,544.54 |
| all | maxDD $ | 280,109.76 | 307,772.08 |
| all | worst wk $ | -82,524.48 | -80,213.45 |
| all | CVaR5 $ | -79,220.34 | -78,652.38 |
| all | CVaR10 $ | -78,243.12 | -77,997.13 |
| all | % neg wk | 42.86 | 38.10 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.035 / +0.935 / +0.356
- [PASS] 3 worst week not worse (all-in): -80,213 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.254 vs p95 +0.192 (median -0.130, rank 0.97, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.128, +0.642]
- [PASS] 5 plateau >=75% of neighbours keep >=75%: 100% of 4
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.283 / +0.874 / +0.322
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.15/+0.93/+0.90/+0.44
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.240; a x1.25: +0.316; single seed: +0.468; seeds 5-9: +0.280

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.127)

- H0 2023-02-10..2023-07-31: uplift -0.025 -> FAIL
- Alternating months: odd-selected K4ens_a0.25 read on even +0.416; even-selected K4ens_a0.25 read on odd +0.010 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Daily file from the 5-seed K4 ensemble (16:15 ET refresh); per-flip multiplier long x(1+a z), short x(1-a z).

DONE RX10