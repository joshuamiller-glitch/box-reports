# REPORT RY8
**Verdict: NO** (1/6 measured gates, replication 0/2 available; D1-harness class NO). Selected cell r_both_a0.25: all-in weekly Sharpe uplift clean/H1/H2/all +0.49/-0.34/-0.39/+0.19. Engine: B11 corrected NT8-faithful engine, 8/8, 1 tick/side + $34.88/8-lot RT, live rules; 6-worker pool.

RY8 VIX-rule directional pair modulator (rule-based analogue of RW5): long flips up and short flips down in benign VIX states, the reverse in stressed states (6 cells).


## Grid (clean uplift of every cell, top 15)

| cell | clean uplift | changed share |
|---|---|---|
| r_both_a0.25 | +0.493 | 0.529 |
| r_both_a0.5 | +0.393 | 0.529 |
| r_term_a0.25 | +0.389 | 0.971 |
| r_term_a0.5 | +0.286 | 0.971 |
| r_chg_a0.25 | -0.018 | 0.971 |
| r_chg_a0.5 | -0.145 | 0.971 |

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.95 |
| clean | Sortino | 2.78 | 3.82 |
| clean | MAR | 4.75 | 7.12 |
| clean | net $ | 1,329,958.72 | 1,732,876.72 |
| clean | maxDD $ | 280,109.76 | 243,300.48 |
| clean | worst wk $ | -81,873.92 | -80,177.28 |
| clean | CVaR5 $ | -78,735.52 | -78,874.49 |
| clean | CVaR10 $ | -78,008.81 | -78,241.34 |
| clean | % neg wk | 42.86 | 40.00 |
| H1 | weekly Sharpe | 2.83 | 2.48 |
| H1 | Sortino | 6.09 | 5.35 |
| H1 | MAR | 3.91 | 4.69 |
| H1 | net $ | 593,797.44 | 653,842.08 |
| H1 | maxDD $ | 151,712.64 | 139,265.20 |
| H1 | worst wk $ | -78,287.36 | -77,916.88 |
| H1 | CVaR5 $ | -77,609.92 | -77,799.04 |
| H1 | CVaR10 $ | -66,029.97 | -77,663.04 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 1.90 |
| H2 | Sortino | 4.69 | 3.78 |
| H2 | MAR | 3.50 | 2.86 |
| H2 | net $ | 761,254.40 | 656,324.72 |
| H2 | maxDD $ | 217,425.28 | 229,295.84 |
| H2 | worst wk $ | -82,524.48 | -79,128.32 |
| H2 | CVaR5 $ | -81,088.96 | -79,055.08 |
| H2 | CVaR10 $ | -79,185.12 | -78,636.56 |
| H2 | % neg wk | 44.44 | 38.89 |
| all | weekly Sharpe | 1.86 | 2.05 |
| all | Sortino | 3.63 | 4.07 |
| all | MAR | 9.59 | 12.51 |
| all | net $ | 2,685,010.56 | 3,043,043.52 |
| all | maxDD $ | 280,109.76 | 243,300.48 |
| all | worst wk $ | -82,524.48 | -80,177.28 |
| all | CVaR5 $ | -79,220.34 | -78,897.75 |
| all | CVaR10 $ | -78,243.12 | -78,290.09 |
| all | % neg wk | 42.86 | 39.88 |

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2: +0.493 / -0.344 / -0.390
- [PASS] 3 worst week not worse (all-in): -80,177 vs -82,524
- [FAIL] 4 own null p95 on all-in uplift: real +0.193 vs p95 +0.218 (median -0.188, rank 0.94, n=100)
- [FAIL] 4 bootstrap 90% CI >0: [-0.348, +0.733]
- [FAIL] 5 plateau >=75% of neighbours keep >=75%: 50% of 4
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.692 / -0.246 / -0.419
- [INFO] uplift vs default B.Cfg() pair: clean/H1/H2/all +0.38/+0.73/+0.37/+0.44
- [INFO] 1 pre-registered (PREREG_AUTOPILOT.md E-block); 2 clean-only selection, H1/H2 once; 6 n/a (pair change); 7 see below

Plateau neighbours (all-in uplift): a x0.75: +0.386; a x1.25: +0.230; rule r_term: +0.075; rule r_chg: -0.069

## Replication (same sign and >= 50 percent of the all-in uplift, i.e. >= +0.096)

- H0 2023-02-10..2023-07-31: uplift -0.077 -> FAIL
- Alternating months: odd-selected r_both_a0.25 read on even +0.614; even-selected r_both_a0.5 read on odd -0.756 -> FAIL
- Cross-instrument and newest-weeks: not applicable / not available.

Executability: NT8, NinjaTrader Brokerage via Rithmic. Daily VIX/VIX3M state file (CBOE closes) published after 16:15 ET; per-flip multiplier long x(1+a z), short x(1-a z).

DONE RY8