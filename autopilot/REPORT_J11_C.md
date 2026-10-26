# REPORT J11-C
**Verdict: NO** (1/6 measured gates pass). Selected cell {"comb": "AND", "F": 6}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.00/+0.00/+0.07/+0.02. GAPMAP cells D11 H6 M7 NQ. Cells in grid: 4.

Mechanism: Two independent stress readings together isolate genuine stress weeks with fewer false flags. Prior (pre-registered): 2%. Registered in PREREG_AUTOPILOT.md (BATCH J11 block) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 4 cells); H1/H2 read once for the selected cell. Pool of 5. Thresholds: rolling 252-label-day percentile ranks (no look-ahead), state read at the last label day before the week. ERA FLAG: not testable pre-2023 (pair rows start 2023-02); weekly states use 2013-26 history for percentile ranks only. H0 (2023-02..07) increment net $ pair->cell: see below.

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| comb   |   F |   flag_weeks |   clean_sharpe |   clean_up |   clean_net |   clean_ww |
|:-------|----:|-------------:|---------------:|-----------:|------------:|-----------:|
| AND    |   6 |           29 |          1.46  |      0.001 | 1.32225e+06 |   -79867.8 |
| AND    |   4 |           29 |          1.399 |     -0.061 | 1.25507e+06 |   -79867.8 |
| OR     |   6 |           88 |          1.374 |     -0.085 | 1.24378e+06 |   -79867.8 |
| OR     |   4 |           88 |          1.166 |     -0.294 | 1.01401e+06 |   -79867.8 |

Clean uplift distribution over the grid: median -0.073, share of cells > 0: 25%, best +0.001.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.46 |
| clean | Sortino | 2.78 | 2.82 |
| clean | MAR | 4.75 | 4.73 |
| clean | net $ | 1,329,958.72 | 1,322,249.28 |
| clean | maxDD $ | 280,109.76 | 279,556.80 |
| clean | worst wk $ | -81,873.92 | -79,867.84 |
| clean | CVaR5 $ | -78,735.52 | -77,874.88 |
| clean | CVaR10 $ | -78,008.81 | -77,126.98 |
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
| all | MAR | 9.59 | 9.64 |
| all | net $ | 2,685,010.56 | 2,693,625.28 |
| all | maxDD $ | 280,109.76 | 279,556.80 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -78,386.31 |
| all | CVaR10 $ | -78,243.12 | -76,783.00 |
| all | % neg wk | 42.86 | 43.45 |

Flagged weeks: 29 of 193 weeks (15%). Increment net $ by span: clean -7,709, H1 +0, H2 +16,324, all +8,615.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.00/+0.00/+0.01/+0.00; m=0.2: +0.00/+0.00/+0.01/+0.00; m=0.3: +0.00/+0.00/+0.02/+0.01; m=0.5: +0.00/+0.00/+0.04/+0.01

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.001 / +0.000 / +0.073
- [PASS] 3 worst week (all-in) not worse: -82,524 vs baseline -82,524
- [FAIL] 4 matched random-switch null (200): real all-in +0.017 vs p95 +0.039, rank 0.90; null mean -0.100
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.104, +0.113]
- [FAIL] 5 plateau: 50% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1): all +0.027 / clean +0.116; (1.25, 1): all -0.017 / clean -0.027; (1, 0.75): all -0.223 / clean -0.114; (1, 1.25): all +0.013 / clean +0.010
- [FAIL] 5 2x slippage uplift >= +0.10 each span: -0.001 / +0.000 / -0.276
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): -0.33
- [INFO] selection-aware null (12 permutations of the whole 4-cell grid, best clean uplift): median +0.018, max +0.140; real best +0.001 (share of permutations >= real: 67%). This is the chance level of the clean selection itself.
- [INFO] replication read-outs (only meaningful if gates 3-5 met): H0 2023-02..07 increment net $ +16,230 (cell 142,898 vs pair 126,668); alternating-month increment net $ (2023-02..2026-10): odd months +46,894, even months -22,050. Not formally run: no cell met the clean/H1/H2 uplift gate.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct +0.3, cvar5_impr +1.1, cvar10_impr +1.9, worst_week_impr +0.0, maxdd_impr +0.2; insurance flag all-in: False.

## Executability / NT8 spec

As J11-A and J11-B combined (two weekly state files). Margin unchanged.

Note: AND flags few weeks (about 20); H1 has no flagged week (uplift 0.00). Clean +0.00 so nothing to replicate. Disclosure as J11-B for the term state. ERA n/a.

DONE J11-C