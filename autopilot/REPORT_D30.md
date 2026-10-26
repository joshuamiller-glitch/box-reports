# REPORT D30
**Verdict: NO** (1/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell VOL5_BLOCK_a0.5_sg+1: all-in weekly Sharpe uplift clean/H1/H2/all +0.24/-0.45/-0.81/-0.08. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

D30 volume-at-flip percentile tilt (VOL5/VOL30).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| VOL5_BLOCK_a0.5_sg+1 | +0.243 | 0.999 |
| VOL30_ALL_a0.5_sg-1 | +0.039 | 1.000 |
| VOL5_ALL_a0.25_sg-1 | -0.021 | 1.000 |
| VOL30_BLOCK_a0.5_sg+1 | -0.072 | 0.999 |
| VOL5_BLOCK_a0.25_sg-1 | -0.077 | 0.999 |
| VOL5_BLOCK_a0.25_sg+1 | -0.086 | 0.999 |
| VOL30_BLOCK_a0.25_sg+1 | -0.096 | 0.999 |
| VOL30_BLOCK_a0.5_sg-1 | -0.132 | 0.999 |
| VOL30_ALL_a0.25_sg-1 | -0.177 | 1.000 |
| VOL30_BLOCK_a0.25_sg-1 | -0.236 | 0.999 |
| VOL5_ALL_a0.5_sg-1 | -0.301 | 1.000 |
| VOL5_ALL_a0.5_sg+1 | -0.349 | 1.000 |
| VOL5_ALL_a0.25_sg+1 | -0.508 | 1.000 |
| VOL30_ALL_a0.25_sg+1 | -0.541 | 1.000 |
| VOL5_BLOCK_a0.5_sg-1 | -0.757 | 0.999 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.70 |
| clean | Sortino | 2.78 | 3.19 |
| clean | MAR | 4.75 | 5.10 |
| clean | net $ | 1,329,958.72 | 1,483,161.40 |
| clean | maxDD $ | 280,109.76 | 290,925.55 |
| clean | worst wk $ | -81,873.92 | -80,109.67 |
| clean | CVaR5 $ | -78,735.52 | -79,307.13 |
| clean | CVaR10 $ | -78,008.81 | -78,465.21 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.38 |
| H1 | Sortino | 6.09 | 4.85 |
| H1 | MAR | 3.91 | 2.67 |
| H1 | net $ | 593,797.44 | 565,437.18 |
| H1 | maxDD $ | 151,712.64 | 212,002.64 |
| H1 | worst wk $ | -78,287.36 | -79,003.60 |
| H1 | CVaR5 $ | -77,609.92 | -78,964.51 |
| H1 | CVaR10 $ | -66,029.97 | -78,541.09 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 1.48 |
| H2 | Sortino | 4.69 | 2.80 |
| H2 | MAR | 3.50 | 1.69 |
| H2 | net $ | 761,254.40 | 513,699.21 |
| H2 | maxDD $ | 217,425.28 | 304,050.48 |
| H2 | worst wk $ | -82,524.48 | -80,017.53 |
| H2 | CVaR5 $ | -81,088.96 | -79,016.70 |
| H2 | CVaR10 $ | -79,185.12 | -78,268.59 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.77 |
| all | Sortino | 3.63 | 3.35 |
| all | MAR | 9.59 | 8.43 |
| all | net $ | 2,685,010.56 | 2,562,297.79 |
| all | maxDD $ | 280,109.76 | 304,050.48 |
| all | worst wk $ | -82,524.48 | -80,109.67 |
| all | CVaR5 $ | -79,220.34 | -79,309.93 |
| all | CVaR10 $ | -78,243.12 | -78,523.10 |
| all | % neg wk | 42.86 | 41.07 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.243 / -0.449 / -0.815
- [PASS] 3 worst week not worse (all-in): -80,110 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.084 vs p95 +0.004 (median -0.329, rank 0.87, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.602, +0.446]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 3
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.456 / -0.944 / -1.345
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.16/-0.23/+0.01/+0.06
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: -0.363; a x1.25: -0.159; feat VOL30: -0.308

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.042)

- H0 2023-02-10..2023-07-31: uplift -0.376 -> FAIL
- Alternating months: odd-selected VOL30_ALL_a0.25_sg-1 read on even -0.236; even-selected VOL5_ALL_a0.5_sg+1 read on odd -0.862 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Per-flip multiplier from the last-N-minute traded volume (volume percentile vs expanding history), computed from the NT8 tick stream; contract counts normal (range 0.5-1.5).

DONE D30