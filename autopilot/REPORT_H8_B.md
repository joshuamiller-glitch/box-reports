# REPORT H8-B
**Verdict: NO** (1/6 measured gates pass). Selected cell {"model": "ridge", "par": 1000.0, "win": null, "thr": "neutral"}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.05/-0.17/+0.03/+0.06. GAPMAP cells D12 H5,H6 M4,M8 NQ. Cells in grid: 16.

Mechanism: A regularised linear model on ten causal daily state features predicts the sign of the pair next-week P&L; weeks predicted bad get half size (B14 was entry-level GBM; this is week-level and linear; label history = p1 gross pair daily replica 2013-2026). Prior (pre-registered): 2%. Registered in PREREG_AUTOPILOT.md (H8 block) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 16 cells); H1/H2 read once for the selected cell. Pool of 5. Thresholds: rolling 252-label-day percentile ranks (no look-ahead), state read at the last label day before the week. ERA FLAG: not testable pre-2023 (pair rows start 2023-02); for H8-B the 2013-22 gross pair replica is training labels only. H0 (2023-02..07) increment net $ pair->cell: see below.

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| model   |     par |   win | thr     |   flag_weeks |   clean_sharpe |   clean_up |   clean_net |   clean_ww |
|:--------|--------:|------:|:--------|-------------:|---------------:|-----------:|------------:|-----------:|
| ridge   | 1000    |   nan | neutral |           99 |          1.515 |      0.055 | 1.06717e+06 |   -81873.9 |
| logit   |    0.05 |   260 | cons    |           35 |          1.51  |      0.05  | 1.28523e+06 |   -81873.9 |
| ridge   |  100    |   nan | neutral |          102 |          1.502 |      0.042 | 1.07997e+06 |   -81873.9 |
| ridge   |  100    |   260 | neutral |           92 |          1.484 |      0.024 | 1.05117e+06 |   -81873.9 |
| ridge   | 1000    |   260 | cons    |            0 |          1.46  |      0     | 1.32996e+06 |   -81873.9 |
| ridge   | 1000    |   nan | cons    |            0 |          1.46  |      0     | 1.32996e+06 |   -81873.9 |
| ridge   |  100    |   260 | cons    |           10 |          1.437 |     -0.023 | 1.29232e+06 |   -81873.9 |
| logit   |    0.5  |   nan | cons    |           29 |          1.374 |     -0.086 | 1.15457e+06 |   -81873.9 |
| logit   |    0.5  |   260 | cons    |           42 |          1.335 |     -0.125 | 1.14102e+06 |   -81873.9 |
| logit   |    0.05 |   nan | cons    |           15 |          1.308 |     -0.152 | 1.17448e+06 |   -81873.9 |

Clean uplift distribution over the grid: median -0.106, share of cells > 0: 25%, best +0.055.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.51 |
| clean | Sortino | 2.78 | 2.80 |
| clean | MAR | 4.75 | 5.72 |
| clean | net $ | 1,329,958.72 | 1,067,170.24 |
| clean | maxDD $ | 280,109.76 | 186,708.80 |
| clean | worst wk $ | -81,873.92 | -81,873.92 |
| clean | CVaR5 $ | -78,735.52 | -78,343.60 |
| clean | CVaR10 $ | -78,008.81 | -68,969.76 |
| clean | % neg wk | 42.86 | 41.90 |
| H1 | weekly Sharpe | 2.83 | 2.66 |
| H1 | Sortino | 6.09 | 5.33 |
| H1 | MAR | 3.91 | 3.09 |
| H1 | net $ | 593,797.44 | 579,770.08 |
| H1 | maxDD $ | 151,712.64 | 187,921.28 |
| H1 | worst wk $ | -78,287.36 | -78,287.36 |
| H1 | CVaR5 $ | -77,609.92 | -78,183.04 |
| H1 | CVaR10 $ | -66,029.97 | -77,766.19 |
| H1 | % neg wk | 39.29 | 35.71 |
| H2 | weekly Sharpe | 2.30 | 2.33 |
| H2 | Sortino | 4.69 | 4.75 |
| H2 | MAR | 3.50 | 3.55 |
| H2 | net $ | 761,254.40 | 771,190.40 |
| H2 | maxDD $ | 217,425.28 | 217,425.28 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -81,088.96 |
| H2 | CVaR10 $ | -79,185.12 | -79,185.12 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 1.92 |
| all | Sortino | 3.63 | 3.70 |
| all | MAR | 9.59 | 11.12 |
| all | net $ | 2,685,010.56 | 2,418,130.72 |
| all | maxDD $ | 280,109.76 | 217,425.28 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -79,113.88 |
| all | CVaR10 $ | -78,243.12 | -74,696.28 |
| all | % neg wk | 42.86 | 41.07 |

Flagged weeks: 99 of 193 weeks (51%). Increment net $ by span: clean -262,788, H1 -14,027, H2 +9,936, all -266,880.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.02/-0.02/+0.00/+0.02; m=0.2: +0.04/-0.03/+0.01/+0.04; m=0.3: +0.06/-0.05/+0.01/+0.05; m=0.5: +0.08/-0.08/+0.02/+0.07

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.055 / -0.168 / +0.033
- [PASS] 3 worst week (all-in) not worse: -82,524 vs baseline -82,524
- [FAIL] 4 matched random-switch null (40 draws; reduced from 200 for runtime on the loaded box after the clean gate had already failed): real all-in +0.064 vs p95 +0.245, rank 0.82; null mean -0.085
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.314, +0.470]
- [FAIL] 5 plateau: 50% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (1, 1, 0.75, 1): all -0.019 / clean +0.014; (1, 1, 1.25, 1): all +0.101 / clean +0.130; (1, 0.75, 1, 1): all +0.054 / clean -0.002; (1, 1.25, 1, 1): all +0.024 / clean -0.020
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.241 / -0.126 / +0.041
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): +0.38
- [INFO] selection-aware null (4 permutations of the whole 16-cell grid, best clean uplift): median +0.208, max +0.332; real best +0.055 (share of permutations >= real: 100%). This is the chance level of the clean selection itself.
- [INFO] replication read-outs (only meaningful if gates 3-5 met): H0 2023-02..07 increment net $ -100,257 (cell 26,411 vs pair 126,668); alternating-month increment net $ (2023-02..2026-10): odd months -261,860, even months -105,276. Not formally run: no cell met the clean/H1/H2 uplift gate.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct -9.9, cvar5_impr +0.1, cvar10_impr +4.5, worst_week_impr +0.0, maxdd_impr +22.4; insurance flag all-in: False.

## Executability / NT8 spec

Weekly Sunday job (outside NT8, python/CSV) refits a ridge or logistic model on ten daily features and writes one number per week (size multiplier 1 or 0.5) read by the strategies at the Sunday 18:00 session open. Trade sizing unchanged otherwise; peak exposure never above 1x.

Note: H8-B week-level label history is the p1 gross pair replica; flag rate and per-cell clean uplifts are in h8/B_stage1_clean.csv.

DONE H8-B