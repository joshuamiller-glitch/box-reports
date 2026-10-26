# REPORT RW5
**Verdict: LEAD** (5/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell K4_a0.25_both_sg+1: all-in weekly Sharpe uplift clean/H1/H2/all +0.25/+1.06/+0.62/+0.47. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

R5 K4 daily direction probability as a continuous day-level modulator of pair flips (long x(1+a z), short x(1-a z)); 8 cells.


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| K4_a0.25_both_sg+1 | +0.253 | 1.000 |
| K4_a0.5_HM_sg+1 | +0.132 | 0.415 |
| K4_a0.5_both_sg+1 | -0.113 | 1.000 |
| K4_a0.25_HM_sg+1 | -0.126 | 0.415 |
| K4_a0.25_HM_sg-1 | -0.142 | 0.415 |
| K4_a0.25_both_sg-1 | -0.446 | 1.000 |
| K4_a0.5_HM_sg-1 | -0.510 | 0.415 |
| K4_a0.5_both_sg-1 | -0.613 | 1.000 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.71 |
| clean | Sortino | 2.78 | 3.34 |
| clean | MAR | 4.75 | 5.63 |
| clean | net $ | 1,329,958.72 | 1,620,614.87 |
| clean | maxDD $ | 280,109.76 | 287,754.21 |
| clean | worst wk $ | -81,873.92 | -79,844.30 |
| clean | CVaR5 $ | -78,735.52 | -78,232.03 |
| clean | CVaR10 $ | -78,008.81 | -77,802.00 |
| clean | % neg wk | 42.86 | 39.05 |
| H1 | weekly Sharpe | 2.83 | 3.89 |
| H1 | Sortino | 6.09 | 10.22 |
| H1 | MAR | 3.91 | 7.55 |
| H1 | net $ | 593,797.44 | 931,121.65 |
| H1 | maxDD $ | 151,712.64 | 123,303.42 |
| H1 | worst wk $ | -78,287.36 | -78,428.87 |
| H1 | CVaR5 $ | -77,609.92 | -78,168.82 |
| H1 | CVaR10 $ | -66,029.97 | -67,408.50 |
| H1 | % neg wk | 39.29 | 28.57 |
| H2 | weekly Sharpe | 2.30 | 2.92 |
| H2 | Sortino | 4.69 | 6.39 |
| H2 | MAR | 3.50 | 4.27 |
| H2 | net $ | 761,254.40 | 970,286.63 |
| H2 | maxDD $ | 217,425.28 | 227,355.37 |
| H2 | worst wk $ | -82,524.48 | -79,289.58 |
| H2 | CVaR5 $ | -81,088.96 | -79,003.50 |
| H2 | CVaR10 $ | -79,185.12 | -76,693.22 |
| H2 | % neg wk | 44.44 | 33.33 |
| all | weekly Sharpe | 1.86 | 2.32 |
| all | Sortino | 3.63 | 4.82 |
| all | MAR | 9.59 | 12.24 |
| all | net $ | 2,685,010.56 | 3,522,023.15 |
| all | maxDD $ | 280,109.76 | 287,754.21 |
| all | worst wk $ | -82,524.48 | -79,844.30 |
| all | CVaR5 $ | -79,220.34 | -78,457.41 |
| all | CVaR10 $ | -78,243.12 | -77,901.47 |
| all | % neg wk | 42.86 | 36.31 |

## Gate checklist

- [PASS] 3 uplift>=+0.10 clean/H1/H2: +0.253 / +1.062 / +0.620
- [PASS] 3 worst week not worse (all-in): -79,844 vs -82,524
- [PASS] 4 own null p95 on all-in uplift: real +0.468 vs p95 +0.190 (median -0.142, rank 1.00, n=100)
- [PASS] 4 bootstrap 90% CI >0: [+0.065, +0.890]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 2
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.418 / +0.923 / +0.330
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.33/+1.00/+1.11/+0.60
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.107; a x1.25: +0.343

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.234)

- H0 2023-02-10..2023-07-31: uplift +0.196 -> FAIL
- Alternating months: odd-selected K4_a0.5_HM_sg+1 read on even +0.475; even-selected K4_a0.25_both_sg+1 read on odd +0.146 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Daily file from the 16:15 ET K4 model (average probability over ES/NQ/RTY/YM) read by DualStrat as a per-flip quantity multiplier (long x(1+a z), short x(1-a z)).

DONE RW5