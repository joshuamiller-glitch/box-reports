# REPORT G8-D
**Verdict: NO** (1/6 measured gates pass). Selected cell {"feat": "pc", "P": 67, "dir": "LO", "m": 1.5}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.28/-2.01/-0.65/-0.29. GAPMAP cells D03 H5 M4,M8 NQ. Cells in grid: 36.

Mechanism: High prior-session option activity proxies dealer hedging/0DTE intensity (pinning vs amplification) next day; scale entries by it. Prior (pre-registered): 3%. Registered in PREREG_AUTOPILOT.md (G8 block, 2026-10-16T17:10Z) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 36 cells); H1/H2 read once for the selected cell. Thresholds are percentiles of clean entries; all features use data strictly before the entry bar. Pool of 5. ERA FLAG: not testable pre-2023 (pair rows and the harness 1-min series start 2023-02).

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| feat   |   P | dir   |   m |   flag_share |   clean_sharpe |   clean_up |        clean_net |   clean_ww |
|:-------|----:|:------|----:|-------------:|---------------:|-----------:|-----------------:|-----------:|
| pc     |  67 | LO    | 1.5 |        0.687 |          1.743 |      0.283 |      1.68378e+06 |   -78662.2 |
| pc     |  33 | LO    | 1.5 |        0.314 |          1.718 |      0.258 |      1.67678e+06 |   -81046.9 |
| pc     |  50 | LO    | 1.5 |        0.519 |          1.555 |      0.095 |      1.51092e+06 |   -78662.2 |
| ov     |  50 | LO    | 1.5 |        0.502 |          1.512 |      0.052 |      1.50522e+06 |   -82482.7 |
| ov     |  33 | LO    | 0.5 |        0.334 |          1.49  |      0.031 |      1.22205e+06 |   -78283.2 |
| pc     |  33 | LO    | 0.5 |        0.314 |          1.434 |     -0.026 |      1.20195e+06 |   -79867.8 |
| ov     |  50 | LO    | 0.5 |        0.502 |          1.398 |     -0.062 |      1.03574e+06 |   -78135.5 |
| pc     |  67 | LO    | 0.5 |        0.687 |          1.391 |     -0.069 |      1.04688e+06 |   -77904.8 |
| pc     |  50 | LO    | 0.5 |        0.519 |          1.341 |     -0.119 |      1.08544e+06 |   -77680.6 |
| ov     |  67 | LO    | 0.5 |        0.66  |          1.327 |     -0.133 | 966751           |   -82963.2 |

Clean uplift distribution over the grid: median -0.292, share of cells > 0: 14%, best +0.283.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.74 |
| clean | Sortino | 2.78 | 3.39 |
| clean | MAR | 4.75 | 5.88 |
| clean | net $ | 1,329,958.72 | 1,683,777.44 |
| clean | maxDD $ | 280,109.76 | 286,128.48 |
| clean | worst wk $ | -81,873.92 | -78,662.24 |
| clean | CVaR5 $ | -78,735.52 | -77,975.65 |
| clean | CVaR10 $ | -78,008.81 | -77,685.40 |
| clean | % neg wk | 42.86 | 40.95 |
| H1 | weekly Sharpe | 2.83 | 0.82 |
| H1 | Sortino | 6.09 | 1.49 |
| H1 | MAR | 3.91 | 0.64 |
| H1 | net $ | 593,797.44 | 236,476.80 |
| H1 | maxDD $ | 151,712.64 | 369,040.00 |
| H1 | worst wk $ | -78,287.36 | -78,889.44 |
| H1 | CVaR5 $ | -77,609.92 | -78,651.44 |
| H1 | CVaR10 $ | -66,029.97 | -78,540.69 |
| H1 | % neg wk | 39.29 | 46.43 |
| H2 | weekly Sharpe | 2.30 | 1.64 |
| H2 | Sortino | 4.69 | 3.11 |
| H2 | MAR | 3.50 | 2.39 |
| H2 | net $ | 761,254.40 | 619,055.20 |
| H2 | maxDD $ | 217,425.28 | 258,945.76 |
| H2 | worst wk $ | -82,524.48 | -79,176.16 |
| H2 | CVaR5 $ | -81,088.96 | -78,867.44 |
| H2 | CVaR10 $ | -79,185.12 | -78,523.20 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.57 |
| all | Sortino | 3.63 | 2.97 |
| all | MAR | 9.59 | 6.13 |
| all | net $ | 2,685,010.56 | 2,539,309.44 |
| all | maxDD $ | 280,109.76 | 414,147.52 |
| all | worst wk $ | -82,524.48 | -79,176.16 |
| all | CVaR5 $ | -79,220.34 | -78,527.04 |
| all | CVaR10 $ | -78,243.12 | -78,143.73 |
| all | % neg wk | 42.86 | 42.86 |

Flagged share: 68.7% of entries. Increment net $ by span: clean +353,819, H1 -357,321, H2 -142,199, all -145,701.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.05/-0.18/-0.02/+0.00; m=0.2: +0.09/-0.38/-0.05/-0.00; m=0.3: +0.13/-0.60/-0.09/-0.02; m=0.5: +0.20/-1.04/-0.21/-0.07

Uplift vs B.Cfg() (per-book week rule on): clean/H1/H2/all +0.31/-0.04/-0.62/+0.05; vs live pair engine +0.20/-1.21/-0.65/-0.19.

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.283 / -2.010 / -0.650
- [PASS] 3 worst week (all-in) not worse: -79,176 vs baseline -82,524
- [FAIL] 4 matched random-switch null (200): real all-in -0.290 vs p95 -0.264, rank 0.94; null mean -0.601
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.872, +0.284]
- [FAIL] 5 plateau: 0% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1.0, 1.0): all -0.278 / clean +0.083; (1.25, 1.0, 1.0): all -0.678 / clean -0.225; (1.0, 0.75, 1.0): all -0.463 / clean +0.134; (1.0, 1.25, 1.0): all -0.600 / clean -0.082
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.264 / -1.756 / -0.922
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): -0.29
- [INFO] selection-aware null (12 permutations of the whole 36-cell grid, best clean uplift): median +0.444, max +1.141; real best +0.283 (share of permutations >= real: 58%). This is the chance level of the clean selection itself.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct -5.4, cvar5_impr +0.9, cvar10_impr +0.1, worst_week_impr +4.1, maxdd_impr -47.9; insurance flag all-in: False.

## Executability / NT8 spec

Needs the prior session's total CME NQ option volume and put share (CME daily volume report or Databento/Rithmic ohlcv-1d of NQ.OPT) fed in at the session start; scale entries by m. External data dependency.

Data caveat: the NQ.OPT daily file carries only NQ-rooted contracts; expiry/OI are not on disk, so this is a crude activity proxy and NOT a gamma-exposure estimate. A real GEX estimate needs the (incomplete) statistics and definition downloads; D03 intraday cells belong to the OPT0DTE family.

DONE G8-D