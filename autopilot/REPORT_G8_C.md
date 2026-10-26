# REPORT G8-C
**Verdict: NO** (1/6 measured gates pass). Selected cell {"dir": "HI", "P": 67, "S": "S4"}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.39/-1.50/-0.38/-0.06. GAPMAP cells D08 H3,H4 M7 NQ. Cells in grid: 16.

Mechanism: On high-vol days single-day give-back and loss are larger in dollars, so a tighter day lock (lower cap / loss floor / earlier give-back) might protect more than it gives up. Prior (pre-registered): 3%. Registered in PREREG_AUTOPILOT.md (G8 block, 2026-10-16T17:10Z) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 16 cells); H1/H2 read once for the selected cell. Thresholds are percentiles of clean entries; all features use data strictly before the entry bar. Pool of 5. ERA FLAG: not testable pre-2023 (pair rows and the harness 1-min series start 2023-02).

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| dir   |   P | S   |   flag_share |   clean_sharpe |   clean_up |   clean_net |   clean_ww |
|:------|----:|:----|-------------:|---------------:|-----------:|------------:|-----------:|
| HI    |  67 | S4  |        0.492 |          1.849 |      0.389 | 1.65411e+06 |   -81873.9 |
| HI    |  80 | S4  |        0.358 |          1.577 |      0.117 | 1.39108e+06 |   -81873.9 |
| HI    |  67 | S2  |        0.492 |          1.481 |      0.021 | 1.36229e+06 |   -79860.8 |
| LO    |  20 | S2  |        0.133 |          1.476 |      0.016 | 1.33409e+06 |   -81873.9 |
| LO    |  33 | S2  |        0.218 |          1.465 |      0.005 | 1.32537e+06 |   -81873.9 |
| HI    |  80 | S2  |        0.358 |          1.463 |      0.003 | 1.32971e+06 |   -79867.8 |
| LO    |  33 | S4  |        0.218 |          1.437 |     -0.023 | 1.2646e+06  |   -81873.9 |
| LO    |  20 | S3  |        0.133 |          1.406 |     -0.054 | 1.23852e+06 |   -81873.9 |
| LO    |  33 | S3  |        0.218 |          1.406 |     -0.054 | 1.2413e+06  |   -81873.9 |
| LO    |  33 | S1  |        0.218 |          1.405 |     -0.055 | 1.24589e+06 |   -81873.9 |

Clean uplift distribution over the grid: median -0.054, share of cells > 0: 38%, best +0.389.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.85 |
| clean | Sortino | 2.78 | 3.52 |
| clean | MAR | 4.75 | 7.26 |
| clean | net $ | 1,329,958.72 | 1,654,111.36 |
| clean | maxDD $ | 280,109.76 | 227,704.32 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -79,397.39 |
| clean | CVaR10 $ | -78,008.81 | -78,433.63 |
| clean | % neg wk | 42.86 | 36.19 |
| H1 | weekly Sharpe | 2.83 | 1.33 |
| H1 | Sortino | 6.09 | 2.48 |
| H1 | MAR | 3.91 | 1.62 |
| H1 | net $ | 593,797.44 | 294,425.60 |
| H1 | maxDD $ | 151,712.64 | 181,657.28 |
| H1 | worst wk $ | -78,287.36 | -77,758.08 |
| H1 | CVaR5 $ | -77,609.92 | -77,530.40 |
| H1 | CVaR10 $ | -66,029.97 | -77,413.12 |
| H1 | % neg wk | 39.29 | 50.00 |
| H2 | weekly Sharpe | 2.30 | 1.91 |
| H2 | Sortino | 4.69 | 3.82 |
| H2 | MAR | 3.50 | 2.96 |
| H2 | net $ | 761,254.40 | 543,106.56 |
| H2 | maxDD $ | 217,425.28 | 183,345.28 |
| H2 | worst wk $ | -82,524.48 | -79,653.44 |
| H2 | CVaR5 $ | -81,088.96 | -71,372.48 |
| H2 | CVaR10 $ | -79,185.12 | -64,342.00 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.79 |
| all | Sortino | 3.63 | 3.42 |
| all | MAR | 9.59 | 10.94 |
| all | net $ | 2,685,010.56 | 2,491,643.52 |
| all | maxDD $ | 280,109.76 | 227,704.32 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -79,039.32 |
| all | CVaR10 $ | -78,243.12 | -78,157.20 |
| all | % neg wk | 42.86 | 40.48 |

Flagged share: 49.2% of days. Increment net $ by span: clean +324,153, H1 -299,372, H2 -218,148, all -193,367.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.05/-0.08/-0.00/+0.02; m=0.2: +0.10/-0.19/-0.01/+0.03; m=0.3: +0.15/-0.31/-0.03/+0.04; m=0.5: +0.24/-0.60/-0.08/+0.04

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.389 / -1.497 / -0.381
- [PASS] 3 worst week (all-in) not worse: -81,874 vs baseline -82,524
- [FAIL] 4 matched random-switch null (200): real all-in -0.064 vs p95 +0.150, rank 0.68; null mean -0.149
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.607, +0.459]
- [FAIL] 5 plateau: 0% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1.0, 1.0): all -0.116 / clean +0.322; (1.25, 1.0, 1.0): all -0.167 / clean -0.014; (1.0, 1.0, 0.75): all +0.112 / clean +0.326; (1.0, 1.0, 1.25): all -0.055 / clean +0.111
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.499 / -1.246 / -0.866
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): -0.10
- [INFO] selection-aware null (12 permutations of the whole 16-cell grid, best clean uplift): median +0.235, max +0.449; real best +0.389 (share of permutations >= real: 8%). This is the chance level of the clean selection itself.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct -7.2, cvar5_impr +0.2, cvar10_impr +0.1, worst_week_impr +0.8, maxdd_impr +18.7; insurance flag all-in: False.

## Executability / NT8 spec

At the start of each session compute the prior-20-RTH-session mean range; on flagged days replace the combined day-lock parameters (cap, loss floor, give-back arm/keep) with the tighter set. NT8: parameters of the existing combined day lock become day-dependent.

DONE G8-C