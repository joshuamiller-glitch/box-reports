# REPORT G8-A
**Verdict: NO** (1/6 measured gates pass). Selected cell {"feat": "rvr", "P": 80, "dir": "HI", "m": 0.5}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.14/+0.40/-0.46/+0.04. GAPMAP cells D08 H2,H3 M4,M8 NQ. Cells in grid: 24.

Mechanism: When the last hour is unusually volatile versus the same clock minute over the prior 20 sessions, pair flips are either noise (whipsaws through brackets) or trend-continuation; sizing them down or up tilts the pair toward its better vol state. Prior (pre-registered): 4%. Registered in PREREG_AUTOPILOT.md (G8 block, 2026-10-16T17:10Z) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 24 cells); H1/H2 read once for the selected cell. Thresholds are percentiles of clean entries; all features use data strictly before the entry bar. Pool of 5. ERA FLAG: not testable pre-2023 (pair rows and the harness 1-min series start 2023-02).

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| feat   |   P | dir   |   m |   flag_share |   clean_sharpe |   clean_up |        clean_net |   clean_ww |
|:-------|----:|:------|----:|-------------:|---------------:|-----------:|-----------------:|-----------:|
| rvr    |  80 | HI    | 0.5 |        0.172 |          1.605 |      0.145 |      1.48035e+06 |   -79371.4 |
| rvr    |  50 | HI    | 0.5 |        0.451 |          1.5   |      0.04  |      1.29217e+06 |   -80090.6 |
| rvr    |  50 | HI    | 0   |        0.451 |          1.481 |      0.021 |      1.22159e+06 |   -79953   |
| rvr    |  33 | LO    | 0   |        0.299 |          1.407 |     -0.052 |      1.07447e+06 |   -81873.9 |
| rvr    |  67 | HI    | 0.5 |        0.295 |          1.377 |     -0.083 |      1.24335e+06 |   -80346.4 |
| rvr    |  67 | HI    | 0   |        0.295 |          1.34  |     -0.119 |      1.14105e+06 |   -79618.6 |
| rvr    |  80 | HI    | 0   |        0.172 |          1.305 |     -0.155 |      1.20423e+06 |   -80448.3 |
| rvr    |  33 | HI    | 0.5 |        0.607 |          1.261 |     -0.198 |      1.0265e+06  |   -78320.2 |
| rvr    |  67 | LO    | 0.5 |        0.611 |          1.177 |     -0.283 | 861840           |   -83915.5 |
| rvr    |  50 | HI    | 1.5 |        0.451 |          1.164 |     -0.296 |      1.10481e+06 |   -82620.6 |

Clean uplift distribution over the grid: median -0.336, share of cells > 0: 12%, best +0.145.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.60 |
| clean | Sortino | 2.78 | 3.06 |
| clean | MAR | 4.75 | 4.47 |
| clean | net $ | 1,329,958.72 | 1,480,345.44 |
| clean | maxDD $ | 280,109.76 | 331,139.52 |
| clean | worst wk $ | -81,873.92 | -79,371.36 |
| clean | CVaR5 $ | -78,735.52 | -77,946.75 |
| clean | CVaR10 $ | -78,008.81 | -77,587.65 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 3.22 |
| H1 | Sortino | 6.09 | 7.06 |
| H1 | MAR | 3.91 | 4.35 |
| H1 | net $ | 593,797.44 | 697,527.84 |
| H1 | maxDD $ | 151,712.64 | 160,497.92 |
| H1 | worst wk $ | -78,287.36 | -77,247.52 |
| H1 | CVaR5 $ | -77,609.92 | -77,228.72 |
| H1 | CVaR10 $ | -66,029.97 | -70,518.40 |
| H1 | % neg wk | 39.29 | 32.14 |
| H2 | weekly Sharpe | 2.30 | 1.83 |
| H2 | Sortino | 4.69 | 3.63 |
| H2 | MAR | 3.50 | 2.99 |
| H2 | net $ | 761,254.40 | 652,513.92 |
| H2 | maxDD $ | 217,425.28 | 218,430.40 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -81,088.96 |
| H2 | CVaR10 $ | -79,185.12 | -79,381.00 |
| H2 | % neg wk | 44.44 | 50.00 |
| all | weekly Sharpe | 1.86 | 1.90 |
| all | Sortino | 3.63 | 3.71 |
| all | MAR | 9.59 | 8.55 |
| all | net $ | 2,685,010.56 | 2,830,387.20 |
| all | maxDD $ | 280,109.76 | 331,139.52 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -78,654.83 |
| all | CVaR10 $ | -78,243.12 | -77,972.58 |
| all | % neg wk | 42.86 | 42.26 |

Flagged share: 17.2% of entries. Increment net $ by span: clean +150,387, H1 +103,730, H2 -108,740, all +145,377.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.02/+0.07/-0.04/+0.01; m=0.2: +0.04/+0.13/-0.08/+0.02; m=0.3: +0.05/+0.18/-0.13/+0.03; m=0.5: +0.09/+0.27/-0.22/+0.04

Uplift vs B.Cfg() (per-book week rule on): clean/H1/H2/all +0.26/+1.09/-0.56/+0.20; vs live pair engine +0.15/-0.08/-0.59/-0.04.

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.145 / +0.395 / -0.464
- [PASS] 3 worst week (all-in) not worse: -82,524 vs baseline -82,524
- [FAIL] 4 matched random-switch null (200): real all-in +0.041 vs p95 +0.073, rank 0.94; null mean -0.215
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.210, +0.289]
- [FAIL] 5 plateau: 25% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1.0, 1.0): all +0.154 / clean +0.188; (1.25, 1.0, 1.0): all -0.013 / clean -0.019; (1.0, 0.75, 1.0): all -0.036 / clean +0.037; (1.0, 1.25, 1.0): all -0.221 / clean +0.116
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.359 / +0.295 / -0.740
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): -0.37
- [INFO] selection-aware null (12 permutations of the whole 24-cell grid, best clean uplift): median +0.277, max +1.020; real best +0.145 (share of permutations >= real: 83%). This is the chance level of the clean selection itself.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct +5.4, cvar5_impr +0.7, cvar10_impr +0.3, worst_week_impr +0.0, maxdd_impr -18.2; insurance flag all-in: False.

## Executability / NT8 spec

Per pair entry compute rvr from the last 60 completed 1-min bars of NQ and the same-ET-minute 60-bar variance averaged over the prior 20 sessions; scale entry quantity by m when rvr crosses the clean-percentile threshold. Quantity change is a per-entry order size (NT8 supports); peak exposure is at most 1.5x for m=1.5. No change to exits, locks or sessions. Margin: unchanged at m<=1; +50% per flagged entry at m=1.5.

DONE G8-A