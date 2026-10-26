# REPORT H8-C
**Verdict: NO** (1/6 measured gates pass). Selected cell {"dir": "HI", "P": 67, "F": 12}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.13/-0.00/+0.36/+0.16. GAPMAP cells D08 H5,H6 M7 NQ. Cells in grid: 24.

Mechanism: Inverted/flat VX term = stress regime with fatter weekly tails: a tighter floor insures; steep contango = calm, loosen. Distinct from J8 (label-level size switch). Prior (pre-registered): 3%. Registered in PREREG_AUTOPILOT.md (H8 block) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 24 cells); H1/H2 read once for the selected cell. Pool of 5. Thresholds: rolling 252-label-day percentile ranks (no look-ahead), state read at the last label day before the week. ERA FLAG: not testable pre-2023 (pair rows start 2023-02); for H8-B the 2013-22 gross pair replica is training labels only. H0 (2023-02..07) increment net $ pair->cell: see below.

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| dir   |   P |   F |   flag_weeks |   clean_sharpe |   clean_up |   clean_net |   clean_ww |
|:------|----:|----:|-------------:|---------------:|-----------:|------------:|-----------:|
| HI    |  67 |  12 |           52 |          1.594 |      0.134 | 1.45953e+06 |  -116217   |
| HI    |  80 |  12 |           36 |          1.58  |      0.12  | 1.44935e+06 |  -116217   |
| HI    |  50 |  12 |           78 |          1.536 |      0.076 | 1.42035e+06 |  -116217   |
| LO    |  20 |   4 |           65 |          1.507 |      0.047 | 1.34915e+06 |   -81873.9 |
| HI    |  67 |  10 |           52 |          1.467 |      0.007 | 1.34622e+06 |  -100939   |
| HI    |  80 |  10 |           36 |          1.452 |     -0.007 | 1.33604e+06 |  -100939   |
| HI    |  80 |   6 |           36 |          1.451 |     -0.009 | 1.31261e+06 |   -79867.8 |
| HI    |  50 |  10 |           78 |          1.436 |     -0.024 | 1.32479e+06 |  -100939   |
| HI    |  50 |   6 |           78 |          1.435 |     -0.025 | 1.29606e+06 |   -79867.8 |
| HI    |  67 |   6 |           52 |          1.421 |     -0.038 | 1.28787e+06 |   -79867.8 |

Clean uplift distribution over the grid: median -0.061, share of cells > 0: 21%, best +0.134.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.59 |
| clean | Sortino | 2.78 | 2.98 |
| clean | MAR | 4.75 | 4.34 |
| clean | net $ | 1,329,958.72 | 1,459,525.12 |
| clean | maxDD $ | 280,109.76 | 336,053.44 |
| clean | worst wk $ | -81,873.92 | -116,216.64 |
| clean | CVaR5 $ | -78,735.52 | -94,411.15 |
| clean | CVaR10 $ | -78,008.81 | -86,146.76 |
| clean | % neg wk | 42.86 | 40.95 |
| H1 | weekly Sharpe | 2.83 | 2.83 |
| H1 | Sortino | 6.09 | 6.08 |
| H1 | MAR | 3.91 | 3.91 |
| H1 | net $ | 593,797.44 | 593,585.92 |
| H1 | maxDD $ | 151,712.64 | 151,712.64 |
| H1 | worst wk $ | -78,287.36 | -78,498.88 |
| H1 | CVaR5 $ | -77,609.92 | -77,715.68 |
| H1 | CVaR10 $ | -66,029.97 | -66,100.48 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 2.66 |
| H2 | Sortino | 4.69 | 5.75 |
| H2 | MAR | 3.50 | 3.92 |
| H2 | net $ | 761,254.40 | 851,834.56 |
| H2 | maxDD $ | 217,425.28 | 217,425.28 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -79,970.08 |
| H2 | CVaR10 $ | -79,185.12 | -74,322.88 |
| H2 | % neg wk | 44.44 | 41.67 |
| all | weekly Sharpe | 1.86 | 2.02 |
| all | Sortino | 3.63 | 3.94 |
| all | MAR | 9.59 | 8.64 |
| all | net $ | 2,685,010.56 | 2,904,945.60 |
| all | maxDD $ | 280,109.76 | 336,053.44 |
| all | worst wk $ | -82,524.48 | -116,216.64 |
| all | CVaR5 $ | -79,220.34 | -89,433.99 |
| all | CVaR10 $ | -78,243.12 | -82,804.39 |
| all | % neg wk | 42.86 | 41.07 |

Flagged weeks: 52 of 193 weeks (27%). Increment net $ by span: clean +129,566, H1 -212, H2 +90,580, all +219,935.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.02/-0.00/+0.04/+0.02; m=0.2: +0.03/-0.00/+0.08/+0.04; m=0.3: +0.05/-0.00/+0.12/+0.06; m=0.5: +0.08/-0.00/+0.19/+0.09

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.134 / -0.002 / +0.363
- [FAIL] 3 worst week (all-in) not worse: -116,217 vs baseline -82,524
- [PASS] 4 matched random-switch null (200): real all-in +0.162 vs p95 +0.115, rank 0.98; null mean -0.012
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.074, +0.449]
- [FAIL] 5 plateau: 50% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1, 1, 1): all +0.113 / clean +0.076; (1.25, 1, 1, 1): all +0.193 / clean +0.179; (1, 0.75, 1, 1): all +0.012 / clean -0.080; (1, 1.25, 1, 1): all +0.129 / clean +0.088
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.130 / -0.020 / +0.336
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): +0.15
- [INFO] selection-aware null (12 permutations of the whole 24-cell grid, best clean uplift): median +0.174, max +0.325; real best +0.134 (share of permutations >= real: 75%). This is the chance level of the clean selection itself.
- [INFO] replication read-outs (only meaningful if gates 3-5 met): H0 2023-02..07 increment net $ -37,963 (cell 88,705 vs pair 126,668); alternating-month increment net $ (2023-02..2026-10): odd months -39,867, even months +221,839. Not formally run: no cell met the clean/H1/H2 uplift gate.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct +8.2, cvar5_impr -12.9, cvar10_impr -5.8, worst_week_impr -40.8, maxdd_impr -20.0; insurance flag all-in: False.

## Executability / NT8 spec

As H8-A with VIX/VIX3M (CBOE daily closes, prior session) in place of realised vol; external data feed needed (Cboe delayed daily file) written to a weekly parameter file.

DONE H8-C