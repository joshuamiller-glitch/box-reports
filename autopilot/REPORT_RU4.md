# REPORT RU4
**Verdict: NO** (1/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell a0.25_N12_sg-1: all-in weekly Sharpe uplift clean/H1/H2/all +0.01/-0.06/-1.16/-0.29. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

RU4 tilts the pair's flips by the direction and age of the last closed 5-min NQ displacement bar (range >= 1.5 ATR14): 8 cells (a, N, sign), selection on clean, E3 gates; sg=-1 cells are the control direction. HG was dropped from RU2/RU6/RU7/RU9 (no tick/point-value spec in ap_i_load.SPEC; disclosed).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| a0.25_N12_sg-1 | +0.010 | 0.658 |
| a0.25_N36_sg-1 | -0.179 | 0.913 |
| a0.5_N12_sg+1 | -0.214 | 0.658 |
| a0.25_N12_sg+1 | -0.234 | 0.658 |
| a0.5_N12_sg-1 | -0.235 | 0.658 |
| a0.25_N36_sg+1 | -0.359 | 0.913 |
| a0.5_N36_sg-1 | -0.488 | 0.913 |
| a0.5_N36_sg+1 | -0.929 | 0.913 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.47 |
| clean | Sortino | 2.78 | 2.68 |
| clean | MAR | 4.75 | 4.69 |
| clean | net $ | 1,329,958.72 | 1,338,215.84 |
| clean | maxDD $ | 280,109.76 | 285,592.08 |
| clean | worst wk $ | -81,873.92 | -79,332.80 |
| clean | CVaR5 $ | -78,735.52 | -77,949.88 |
| clean | CVaR10 $ | -78,008.81 | -77,637.20 |
| clean | % neg wk | 42.86 | 46.67 |
| H1 | weekly Sharpe | 2.83 | 2.77 |
| H1 | Sortino | 6.09 | 5.91 |
| H1 | MAR | 3.91 | 2.50 |
| H1 | net $ | 593,797.44 | 541,870.56 |
| H1 | maxDD $ | 151,712.64 | 216,894.32 |
| H1 | worst wk $ | -78,287.36 | -78,283.36 |
| H1 | CVaR5 $ | -77,609.92 | -77,974.12 |
| H1 | CVaR10 $ | -66,029.97 | -66,477.39 |
| H1 | % neg wk | 39.29 | 25.00 |
| H2 | weekly Sharpe | 2.30 | 1.13 |
| H2 | Sortino | 4.65 | 2.19 |
| H2 | MAR | 3.58 | 1.96 |
| H2 | net $ | 778,370.56 | 382,407.76 |
| H2 | maxDD $ | 217,425.28 | 195,415.92 |
| H2 | worst wk $ | -82,524.48 | -77,878.24 |
| H2 | CVaR5 $ | -81,088.96 | -77,660.32 |
| H2 | CVaR10 $ | -79,185.12 | -77,220.34 |
| H2 | % neg wk | 43.24 | 48.65 |
| all | weekly Sharpe | 1.86 | 1.57 |
| all | Sortino | 3.63 | 2.94 |
| all | MAR | 9.65 | 7.92 |
| all | net $ | 2,702,126.72 | 2,262,494.16 |
| all | maxDD $ | 280,109.76 | 285,592.08 |
| all | worst wk $ | -82,524.48 | -79,332.80 |
| all | CVaR5 $ | -79,220.34 | -77,947.31 |
| all | CVaR10 $ | -78,243.12 | -77,611.32 |
| all | % neg wk | 42.60 | 43.79 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.010 / -0.056 / -1.163
- [PASS] 3 worst week not worse (all-in): -79,333 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real -0.285 vs p95 +0.217 (median -0.247, rank 0.44, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.785, +0.204]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 0% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.186 / +0.395 / -1.695
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.09/+0.51/-0.12/+0.09
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: -0.203; a x1.25: -0.151; N x0.75: -0.207; N x1.25: -0.193

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= -0.143)

- H0 2023-02-10..2023-07-31: uplift -0.335 -> FAIL
- Alternating months: odd-selected a0.25_N12_sg+1 read on even +0.092; even-selected a0.5_N12_sg+1 read on odd -0.396 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Per-flip multiplier clip(1 + a x sg x side x dir x w, 0.5, 1.5) from the direction of the last closed 5-minute NQ bar with range >= 1.5 ATR14 and the number of closed 5-minute bars since it (w = 1 if within N bars); computed in NT8 from the strategy own bars; contract counts normal (range 0.5-1.5).

DONE RU4