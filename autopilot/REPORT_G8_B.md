# REPORT G8-B
**Verdict: NO** (1/6 measured gates pass). Selected cell {"feat": "onr", "P": 67, "dir": "LO", "m": 0.5}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.37/-0.21/-0.41/+0.11. GAPMAP cells D08 H3 M4,M8 NQ. Cells in grid: 48.

Mechanism: A wide overnight range or a large opening gap (relative to 20-session norms) signals an event-driven day whose RTH trend/reversal mix differs; scale the pair's RTH entries by that state. Prior (pre-registered): 4%. Registered in PREREG_AUTOPILOT.md (G8 block, 2026-10-16T17:10Z) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 48 cells); H1/H2 read once for the selected cell. Thresholds are percentiles of clean entries; all features use data strictly before the entry bar. Pool of 5. ERA FLAG: not testable pre-2023 (pair rows and the harness 1-min series start 2023-02).

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| feat   |   P | dir   |   m |   flag_share |   clean_sharpe |   clean_up |   clean_net |   clean_ww |
|:-------|----:|:------|----:|-------------:|---------------:|-----------:|------------:|-----------:|
| onr    |  67 | LO    | 0.5 |        0.293 |          1.831 |      0.371 | 1.56308e+06 |   -81873.9 |
| gap    |  80 | LO    | 0.5 |        0.343 |          1.796 |      0.337 | 1.5175e+06  |   -81873.9 |
| gap    |  33 | HI    | 0.5 |        0.31  |          1.73  |      0.27  | 1.46607e+06 |   -81873.9 |
| onr    |  67 | LO    | 0   |        0.293 |          1.73  |      0.27  | 1.46888e+06 |   -81873.9 |
| gap    |  80 | LO    | 0   |        0.343 |          1.716 |      0.256 | 1.43382e+06 |   -81873.9 |
| gap    |  33 | HI    | 0   |        0.31  |          1.653 |      0.193 | 1.35642e+06 |   -81873.9 |
| onr    |  80 | LO    | 0.5 |        0.353 |          1.649 |      0.189 | 1.39386e+06 |   -81873.9 |
| gap    |  67 | LO    | 0   |        0.276 |          1.629 |      0.169 | 1.38591e+06 |   -81873.9 |
| onr    |  33 | LO    | 0.5 |        0.135 |          1.61  |      0.15  | 1.4578e+06  |   -81873.9 |
| onr    |  50 | LO    | 0   |        0.211 |          1.608 |      0.148 | 1.44923e+06 |   -81873.9 |

Clean uplift distribution over the grid: median -0.004, share of cells > 0: 48%, best +0.371.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.83 |
| clean | Sortino | 2.78 | 3.58 |
| clean | MAR | 4.75 | 6.67 |
| clean | net $ | 1,329,958.72 | 1,563,081.76 |
| clean | maxDD $ | 280,109.76 | 234,248.64 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,703.89 |
| clean | CVaR10 $ | -78,008.81 | -77,591.81 |
| clean | % neg wk | 42.86 | 40.95 |
| H1 | weekly Sharpe | 2.83 | 2.62 |
| H1 | Sortino | 6.09 | 5.33 |
| H1 | MAR | 3.91 | 3.97 |
| H1 | net $ | 593,797.44 | 521,153.12 |
| H1 | maxDD $ | 151,712.64 | 131,123.84 |
| H1 | worst wk $ | -78,287.36 | -78,448.96 |
| H1 | CVaR5 $ | -77,609.92 | -78,063.28 |
| H1 | CVaR10 $ | -66,029.97 | -71,090.83 |
| H1 | % neg wk | 39.29 | 42.86 |
| H2 | weekly Sharpe | 2.30 | 1.89 |
| H2 | Sortino | 4.69 | 3.61 |
| H2 | MAR | 3.50 | 3.04 |
| H2 | net $ | 761,254.40 | 628,601.44 |
| H2 | maxDD $ | 217,425.28 | 206,543.20 |
| H2 | worst wk $ | -82,524.48 | -79,653.44 |
| H2 | CVaR5 $ | -81,088.96 | -79,258.64 |
| H2 | CVaR10 $ | -79,185.12 | -78,764.60 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.97 |
| all | Sortino | 3.63 | 3.82 |
| all | MAR | 9.59 | 11.58 |
| all | net $ | 2,685,010.56 | 2,712,836.32 |
| all | maxDD $ | 280,109.76 | 234,248.64 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -79,039.40 |
| all | CVaR10 $ | -78,243.12 | -78,175.50 |
| all | % neg wk | 42.86 | 41.67 |

Flagged share: 29.3% of RTH entries. Increment net $ by span: clean +233,123, H1 -72,644, H2 -132,653, all +27,826.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.04/-0.01/-0.04/+0.02; m=0.2: +0.09/-0.02/-0.07/+0.04; m=0.3: +0.13/-0.03/-0.11/+0.06; m=0.5: +0.21/-0.07/-0.19/+0.08

Uplift vs B.Cfg() (per-book week rule on): clean/H1/H2/all +0.28/+0.13/-0.12/+0.17; vs live pair engine +0.17/-1.05/-0.15/-0.07.

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.371 / -0.211 / -0.408
- [PASS] 3 worst week (all-in) not worse: -81,874 vs baseline -82,524
- [FAIL] 4 matched random-switch null (200): real all-in +0.111 vs p95 +0.155, rank 0.81; null mean +0.012
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.200, +0.459]
- [FAIL] 5 plateau: 25% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1.0, 1.0): all +0.025 / clean +0.139; (1.25, 1.0, 1.0): all +0.028 / clean +0.267; (1.0, 0.75, 1.0): all +0.180 / clean +0.368; (1.0, 1.25, 1.0): all -0.091 / clean +0.236
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.386 / -0.126 / -0.841
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): +0.22
- [INFO] selection-aware null (12 permutations of the whole 48-cell grid, best clean uplift): median +0.455, max +0.611; real best +0.371 (share of permutations >= real: 83%). This is the chance level of the clean selection itself.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct +1.0, cvar5_impr +0.2, cvar10_impr +0.1, worst_week_impr +0.8, maxdd_impr +16.4; insurance flag all-in: False.

## Executability / NT8 spec

At 09:30 ET compute overnight range (18:00-09:29 high-low) / 20-session mean, and |open - prior RTH close| / 20-session mean RTH range; scale RTH entries that day by m. NT8: values fixed at 09:30 and held in a strategy variable.

DONE G8-B