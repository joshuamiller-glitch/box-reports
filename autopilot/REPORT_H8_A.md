# REPORT H8-A
**Verdict: NO** (0/6 measured gates pass). Selected cell {"dir": "LO", "P": 20, "F": 12}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.04/-0.32/+0.00/-0.02. GAPMAP cells D08 H5,H6 M7 NQ. Cells in grid: 24.

Mechanism: The live week floor is a fixed -8R; scaling it with the trailing realised-vol percentile (tighter or looser on high- or low-vol weeks) is a risk rule that changes nothing in unflagged weeks. Prior (pre-registered): 3%. Registered in PREREG_AUTOPILOT.md (H8 block) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 24 cells); H1/H2 read once for the selected cell. Pool of 5. Thresholds: rolling 252-label-day percentile ranks (no look-ahead), state read at the last label day before the week. ERA FLAG: not testable pre-2023 (pair rows start 2023-02); for H8-B the 2013-22 gross pair replica is training labels only. H0 (2023-02..07) increment net $ pair->cell: see below.

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| dir   |   P |   F |   flag_weeks |   clean_sharpe |   clean_up |   clean_net |   clean_ww |
|:------|----:|----:|-------------:|---------------:|-----------:|------------:|-----------:|
| LO    |  20 |  12 |           67 |          1.495 |      0.036 | 1.38005e+06 |  -116801   |
| LO    |  33 |  12 |           83 |          1.482 |      0.022 | 1.37057e+06 |  -116801   |
| HI    |  80 |  12 |           39 |          1.481 |      0.021 | 1.34765e+06 |   -99520.3 |
| HI    |  50 |  10 |           85 |          1.441 |     -0.019 | 1.32808e+06 |  -100939   |
| HI    |  50 |  12 |           85 |          1.439 |     -0.021 | 1.33238e+06 |  -116217   |
| LO    |  50 |  12 |          108 |          1.43  |     -0.03  | 1.33491e+06 |  -116801   |
| HI    |  67 |  12 |           57 |          1.425 |     -0.035 | 1.30935e+06 |  -115358   |
| HI    |  80 |  10 |           39 |          1.404 |     -0.055 | 1.2914e+06  |   -96600.3 |
| LO    |  33 |   6 |           83 |          1.404 |     -0.056 | 1.27352e+06 |   -81873.9 |
| LO    |  20 |   6 |           67 |          1.382 |     -0.077 | 1.25966e+06 |   -81873.9 |

Clean uplift distribution over the grid: median -0.094, share of cells > 0: 12%, best +0.036.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.50 |
| clean | Sortino | 2.78 | 2.77 |
| clean | MAR | 4.75 | 4.93 |
| clean | net $ | 1,329,958.72 | 1,380,048.64 |
| clean | maxDD $ | 280,109.76 | 280,109.76 |
| clean | worst wk $ | -81,873.92 | -116,801.28 |
| clean | CVaR5 $ | -78,735.52 | -91,717.07 |
| clean | CVaR10 $ | -78,008.81 | -85,131.26 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.50 |
| H1 | Sortino | 6.09 | 4.77 |
| H1 | MAR | 3.91 | 3.15 |
| H1 | net $ | 593,797.44 | 555,137.92 |
| H1 | maxDD $ | 151,712.64 | 176,292.16 |
| H1 | worst wk $ | -78,287.36 | -115,592.00 |
| H1 | CVaR5 $ | -77,609.92 | -96,939.68 |
| H1 | CVaR10 $ | -66,029.97 | -78,916.48 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 2.30 |
| H2 | Sortino | 4.69 | 4.69 |
| H2 | MAR | 3.50 | 3.50 |
| H2 | net $ | 761,254.40 | 761,254.40 |
| H2 | maxDD $ | 217,425.28 | 217,425.28 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -81,088.96 |
| H2 | CVaR10 $ | -79,185.12 | -79,185.12 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.84 |
| all | Sortino | 3.63 | 3.48 |
| all | MAR | 9.59 | 9.63 |
| all | net $ | 2,685,010.56 | 2,696,440.96 |
| all | maxDD $ | 280,109.76 | 280,109.76 |
| all | worst wk $ | -82,524.48 | -116,801.28 |
| all | CVaR5 $ | -79,220.34 | -92,071.18 |
| all | CVaR10 $ | -78,243.12 | -85,121.39 |
| all | % neg wk | 42.86 | 42.26 |

Flagged weeks: 67 of 193 weeks (35%). Increment net $ by span: clean +50,090, H1 -38,660, H2 +0, all +11,430.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.01/-0.03/+0.00/+0.00; m=0.2: +0.01/-0.06/+0.00/+0.00; m=0.3: +0.02/-0.10/+0.00/+0.00; m=0.5: +0.03/-0.16/+0.00/-0.00

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.036 / -0.323 / +0.000
- [FAIL] 3 worst week (all-in) not worse: -116,801 vs baseline -82,524
- [FAIL] 4 matched random-switch null (200): real all-in -0.019 vs p95 +0.150, rank 0.43; null mean +0.002
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.191, +0.202]
- [FAIL] 5 plateau: 0% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1, 1, 1): all -0.019 / clean +0.036; (1.25, 1, 1, 1): all -0.020 / clean +0.034; (1, 0.75, 1, 1): all -0.042 / clean -0.045; (1, 1.25, 1, 1): all -0.071 / clean +0.004
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.040 / -0.308 / +0.000
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): +0.09
- [INFO] selection-aware null (12 permutations of the whole 24-cell grid, best clean uplift): median +0.147, max +0.265; real best +0.036 (share of permutations >= real: 100%). This is the chance level of the clean selection itself.
- [INFO] replication read-outs (only meaningful if gates 3-5 met): H0 2023-02..07 increment net $ -20,835 (cell 105,833 vs pair 126,668); alternating-month increment net $ (2023-02..2026-10): odd months -100,270, even months +90,865. Not formally run: no cell met the clean/H1/H2 uplift gate.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct +0.4, cvar5_impr -16.2, cvar10_impr -8.8, worst_week_impr -41.5, maxdd_impr -0.0; insurance flag all-in: False.

## Executability / NT8 spec

At the start of each ISO week compute the 252-label-day percentile rank of 20-day NQ close-to-close vol (daily closes) as of the prior session; for flagged weeks replace the combined week floor (-8R) by F R. NT8: week-floor parameter becomes week-dependent in the strategy (values frozen at the Sunday 18:00 open).

DONE H8-A