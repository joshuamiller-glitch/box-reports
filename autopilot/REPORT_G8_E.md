# REPORT G8-E
**Verdict: NO** (2/6 measured gates pass). Selected cell {"feat": "oinear", "P": 67, "dir": "HI", "m": 0.0}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.38/-0.11/-0.36/+0.17. GAPMAP cells D03 H5 M4,M8 NQ. Cells in grid: 54.

Mechanism: Open-interest structure proxies dealer positioning/0DTE-weekly pinning intensity (near-expiry OI share) and hedging demand (put share); scale entries by it. Prior (pre-registered): 3%. Registered in PREREG_AUTOPILOT.md (G8 block, 2026-10-16T17:10Z) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 54 cells); H1/H2 read once for the selected cell. Thresholds are percentiles of clean entries; all features use data strictly before the entry bar. Pool of 5. ERA FLAG: not testable pre-2023 (pair rows and the harness 1-min series start 2023-02).

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| feat   |   P | dir   |   m |   flag_share |   clean_sharpe |   clean_up |        clean_net |   clean_ww |
|:-------|----:|:------|----:|-------------:|---------------:|-----------:|-----------------:|-----------:|
| oinear |  67 | HI    | 0   |        0.226 |          1.841 |      0.381 |      1.38796e+06 |   -81873.9 |
| oinear |  67 | HI    | 0.5 |        0.226 |          1.67  |      0.21  |      1.34695e+06 |   -81873.9 |
| oirat  |  67 | HI    | 0   |        0.318 |          1.66  |      0.2   |      1.26511e+06 |   -78083.2 |
| oirat  |  67 | HI    | 0.5 |        0.318 |          1.65  |      0.19  |      1.38614e+06 |   -78083.2 |
| oipc   |  67 | LO    | 0.5 |        0.739 |          1.607 |      0.147 |      1.06415e+06 |   -77719   |
| oinear |  33 | LO    | 0.5 |        0.395 |          1.586 |      0.126 |      1.39472e+06 |   -79867.8 |
| oipc   |  33 | LO    | 0.5 |        0.465 |          1.564 |      0.104 |      1.23534e+06 |   -81873.9 |
| oipc   |  50 | LO    | 0.5 |        0.635 |          1.539 |      0.079 |      1.06135e+06 |   -81873.9 |
| oipc   |  33 | LO    | 0   |        0.465 |          1.505 |      0.045 |      1.09514e+06 |   -81873.9 |
| oirat  |  33 | HI    | 0.5 |        0.686 |          1.479 |      0.019 | 947141           |   -78083.2 |

Clean uplift distribution over the grid: median -0.205, share of cells > 0: 20%, best +0.381.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.84 |
| clean | Sortino | 2.78 | 3.94 |
| clean | MAR | 4.75 | 5.46 |
| clean | net $ | 1,329,958.72 | 1,387,963.20 |
| clean | maxDD $ | 280,109.76 | 254,249.28 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,452.59 |
| clean | CVaR10 $ | -78,008.81 | -66,996.25 |
| clean | % neg wk | 42.86 | 27.62 |
| H1 | weekly Sharpe | 2.83 | 2.72 |
| H1 | Sortino | 6.09 | 5.81 |
| H1 | MAR | 3.91 | 3.82 |
| H1 | net $ | 593,797.44 | 579,457.60 |
| H1 | maxDD $ | 151,712.64 | 151,712.64 |
| H1 | worst wk $ | -78,287.36 | -78,287.36 |
| H1 | CVaR5 $ | -77,609.92 | -77,609.92 |
| H1 | CVaR10 $ | -66,029.97 | -68,112.00 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 1.93 |
| H2 | Sortino | 4.69 | 3.85 |
| H2 | MAR | 3.50 | 2.61 |
| H2 | net $ | 761,254.40 | 567,268.48 |
| H2 | maxDD $ | 217,425.28 | 217,425.28 |
| H2 | worst wk $ | -82,524.48 | -79,653.44 |
| H2 | CVaR5 $ | -81,088.96 | -78,534.56 |
| H2 | CVaR10 $ | -79,185.12 | -73,605.12 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 2.02 |
| all | Sortino | 3.63 | 4.23 |
| all | MAR | 9.59 | 9.97 |
| all | net $ | 2,685,010.56 | 2,534,689.28 |
| all | maxDD $ | 280,109.76 | 254,249.28 |
| all | worst wk $ | -82,524.48 | -81,873.92 |
| all | CVaR5 $ | -79,220.34 | -78,463.96 |
| all | CVaR10 $ | -78,243.12 | -70,634.41 |
| all | % neg wk | 42.86 | 33.33 |

Flagged share: 22.6% of entries. Increment net $ by span: clean +58,004, H1 -14,340, H2 -193,986, all -150,321.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.06/-0.01/-0.01/+0.04; m=0.2: +0.11/-0.02/-0.03/+0.07; m=0.3: +0.17/-0.03/-0.06/+0.11; m=0.5: +0.26/-0.05/-0.12/+0.16

Uplift vs B.Cfg() (per-book week rule on): clean/H1/H2/all +0.32/-0.07/-0.56/+0.06; vs live pair engine +0.21/-1.25/-0.59/-0.19.

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.381 / -0.110 / -0.362
- [PASS] 3 worst week (all-in) not worse: -81,874 vs baseline -82,524
- [PASS] 4 matched random-switch null (200): real all-in +0.167 vs p95 +0.088, rank 0.97; null mean -0.460
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.321, +0.675]
- [FAIL] 5 plateau: 50% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1.0, 1.0): all -0.618 / clean -0.047; (1.25, 1.0, 1.0): all +0.016 / clean +0.013; (1.0, 0.75, 1.0): all +0.201 / clean +0.290; (1.0, 1.25, 1.0): all +0.167 / clean +0.381
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.545 / -0.077 / -0.362
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): +0.06
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct -5.6, cvar5_impr +1.0, cvar10_impr +9.7, worst_week_impr +0.8, maxdd_impr +9.2; insurance flag all-in: False.

## Executability / NT8 spec

Needs the prior session's NQ option open interest (CME daily OI file, published ~10:00 ET next day, so lag 2 dates) fed in at the start; scale entries by m. External data dependency.

Data caveat: the NQ.OPT daily file carries only NQ-rooted contracts; expiry/OI are not on disk, so this is a crude activity proxy and NOT a gamma-exposure estimate. A real GEX estimate needs the (incomplete) statistics and definition downloads; D03 intraday cells belong to the OPT0DTE family.

DONE G8-E