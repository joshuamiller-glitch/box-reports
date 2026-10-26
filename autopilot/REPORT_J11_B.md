# REPORT J11-B
**Verdict: NO** (1/6 measured gates pass). Selected cell {"f": "TERM", "P": 80, "F": 6}; all-in weekly-Sharpe uplift clean/H1/H2/all -0.01/+0.00/+0.07/+0.01. GAPMAP cells D08 H5,H6 M7 NQ. Cells in grid: 9.

Mechanism: H8-C chose a loosening floor and its worst week got worse; this variant only tightens on the flat/inverted-term state (insurance reading of the same mechanism). H1/H2 already read once for the parent. Prior (pre-registered): 2%. Registered in PREREG_AUTOPILOT.md (BATCH J11 block) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 9 cells); H1/H2 read once for the selected cell. Pool of 5. Thresholds: rolling 252-label-day percentile ranks (no look-ahead), state read at the last label day before the week. ERA FLAG: not testable pre-2023 (pair rows start 2023-02); weekly states use 2013-26 history for percentile ranks only. H0 (2023-02..07) increment net $ pair->cell: see below.

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| f    |   P |   F |   flag_weeks |   clean_sharpe |   clean_up |        clean_net |   clean_ww |
|:-----|----:|----:|-------------:|---------------:|-----------:|-----------------:|-----------:|
| TERM |  80 |   6 |           36 |          1.451 |     -0.009 |      1.31261e+06 |   -79867.8 |
| TERM |  50 |   6 |           78 |          1.435 |     -0.025 |      1.29606e+06 |   -79867.8 |
| TERM |  67 |   6 |           52 |          1.421 |     -0.038 |      1.28787e+06 |   -79867.8 |
| TERM |  67 |   3 |           52 |          1.26  |     -0.2   |      1.09512e+06 |   -79867.8 |
| TERM |  80 |   3 |           36 |          1.214 |     -0.246 |      1.06246e+06 |   -79867.8 |
| TERM |  67 |   4 |           52 |          1.139 |     -0.321 |      1.00523e+06 |   -79867.8 |
| TERM |  80 |   4 |           36 |          1.118 |     -0.342 | 991625           |   -79867.8 |
| TERM |  50 |   3 |           78 |          1.088 |     -0.371 | 907808           |   -79867.8 |
| TERM |  50 |   4 |           78 |          1.083 |     -0.377 | 951089           |   -79867.8 |

Clean uplift distribution over the grid: median -0.246, share of cells > 0: 0%, best -0.009.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.45 |
| clean | Sortino | 2.78 | 2.81 |
| clean | MAR | 4.75 | 4.31 |
| clean | net $ | 1,329,958.72 | 1,312,605.44 |
| clean | maxDD $ | 280,109.76 | 304,387.20 |
| clean | worst wk $ | -81,873.92 | -79,867.84 |
| clean | CVaR5 $ | -78,735.52 | -77,842.03 |
| clean | CVaR10 $ | -78,008.81 | -74,502.17 |
| clean | % neg wk | 42.86 | 43.81 |
| H1 | weekly Sharpe | 2.83 | 2.83 |
| H1 | Sortino | 6.09 | 6.09 |
| H1 | MAR | 3.91 | 3.91 |
| H1 | net $ | 593,797.44 | 593,797.44 |
| H1 | maxDD $ | 151,712.64 | 151,712.64 |
| H1 | worst wk $ | -78,287.36 | -78,287.36 |
| H1 | CVaR5 $ | -77,609.92 | -77,609.92 |
| H1 | CVaR10 $ | -66,029.97 | -66,029.97 |
| H1 | % neg wk | 39.29 | 39.29 |
| H2 | weekly Sharpe | 2.30 | 2.37 |
| H2 | Sortino | 4.69 | 4.94 |
| H2 | MAR | 3.50 | 3.58 |
| H2 | net $ | 761,254.40 | 777,578.56 |
| H2 | maxDD $ | 217,425.28 | 217,425.28 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -79,970.08 |
| H2 | CVaR10 $ | -79,185.12 | -75,157.68 |
| H2 | % neg wk | 44.44 | 44.44 |
| all | weekly Sharpe | 1.86 | 1.87 |
| all | Sortino | 3.63 | 3.72 |
| all | MAR | 9.59 | 8.82 |
| all | net $ | 2,685,010.56 | 2,683,981.44 |
| all | maxDD $ | 280,109.76 | 304,387.20 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -78,374.22 |
| all | CVaR10 $ | -78,243.12 | -75,022.02 |
| all | % neg wk | 42.86 | 43.45 |

Flagged weeks: 36 of 193 weeks (19%). Increment net $ by span: clean -17,353, H1 +0, H2 +16,324, all -1,029.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.00/+0.00/+0.01/+0.00; m=0.2: +0.00/+0.00/+0.01/+0.00; m=0.3: +0.00/+0.00/+0.02/+0.01; m=0.5: -0.00/+0.00/+0.04/+0.01

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: -0.009 / +0.000 / +0.073
- [PASS] 3 worst week (all-in) not worse: -82,524 vs baseline -82,524
- [FAIL] 4 matched random-switch null (200): real all-in +0.011 vs p95 +0.038, rank 0.92; null mean -0.116
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.119, +0.129]
- [FAIL] 5 plateau: 25% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1): all -0.059 / clean -0.028; (1.25, 1): all +0.000 / clean +0.000; (1, 0.75): all -0.267 / clean -0.293; (1, 1.25): all +0.023 / clean +0.024
- [FAIL] 5 2x slippage uplift >= +0.10 each span: -0.004 / +0.000 / +0.071
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): -0.15
- [INFO] selection-aware null (12 permutations of the whole 9-cell grid, best clean uplift): median +0.063, max +0.367; real best -0.009 (share of permutations >= real: 92%). This is the chance level of the clean selection itself.
- [INFO] replication read-outs (only meaningful if gates 3-5 met): H0 2023-02..07 increment net $ +16,230 (cell 142,898 vs pair 126,668); alternating-month increment net $ (2023-02..2026-10): odd months +82,058, even months -66,857. Not formally run: no cell met the clean/H1/H2 uplift gate.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct -0.0, cvar5_impr +1.1, cvar10_impr +4.1, worst_week_impr +0.0, maxdd_impr -8.7; insurance flag all-in: False.

## Executability / NT8 spec

As J11-A with VIX/VIX3M (CBOE daily closes, prior session) percentile; external daily Cboe file needed. Margin unchanged.

Disclosure: H1/H2 were read once for parent H8-C; tighten-only parent cells were already known negative on clean (HI F6 -0.04..-0.01). Tighten-only removes the worst-week deterioration (worst week unchanged -82.5k) but also removes the gain: the parent's clean gain was the loosening. Cells P50/67/80 x F3/4/6, ERA n/a (pair rows 2023+), H0/alt-month not run (clean/H1/H2 gate failed).

DONE J11-B