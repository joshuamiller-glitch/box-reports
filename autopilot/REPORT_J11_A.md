# REPORT J11-A
**Verdict: NO** (1/6 measured gates pass). Selected cell {"f": "WR", "P": 80, "F": 4}; all-in weekly-Sharpe uplift clean/H1/H2/all +0.06/-0.66/-0.26/-0.11. GAPMAP cells D11 H6 M7 NQ. Cells in grid: 12.

Mechanism: Weekly volatility clustering: after an expanded prior week, a gap-heavy weekend, or a choppy 8-week regime the pair weekly loss tail is fatter, so a week floor of 4 or 6R (never above the live 8R) cuts the left tail. Prior (pre-registered): 3%. Registered in PREREG_AUTOPILOT.md (BATCH J11 block) before any run. Engine: B11 corrected NT8-faithful engine (b11_nt8, clean process), live rules, 8/8, fill = 1 tick/side + $34.88 per 8-lot RT (2x slippage = 1.0 pt RT), ET clock; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean/H1/H2/all weekly Sharpe 1.46/2.83/2.30/1.86. Selection on CLEAN only (best clean weekly-Sharpe uplift of 12 cells); H1/H2 read once for the selected cell. Pool of 5. Thresholds: rolling 252-label-day percentile ranks (no look-ahead), state read at the last label day before the week. ERA FLAG: not testable pre-2023 (pair rows start 2023-02); weekly states use 2013-26 history for percentile ranks only. H0 (2023-02..07) increment net $ pair->cell: see below.

## Clean-only selection grid (top 10 of the grid; H1/H2 not shown)

| f   |   P |   F |   flag_weeks |   clean_sharpe |   clean_up |   clean_net |   clean_ww |
|:----|----:|----:|-------------:|---------------:|-----------:|------------:|-----------:|
| WR  |  80 |   4 |           38 |          1.522 |      0.063 | 1.36073e+06 |   -79867.8 |
| WR  |  80 |   6 |           38 |          1.487 |      0.027 | 1.34136e+06 |   -79867.8 |
| GAP |  80 |   6 |           51 |          1.453 |     -0.007 | 1.31409e+06 |   -79867.8 |
| WR  |  67 |   4 |           65 |          1.429 |     -0.031 | 1.26385e+06 |   -79867.8 |
| WR  |  67 |   6 |           65 |          1.413 |     -0.047 | 1.27816e+06 |   -79867.8 |
| GAP |  67 |   6 |           75 |          1.39  |     -0.07  | 1.26285e+06 |   -79867.8 |
| WER |  80 |   6 |           36 |          1.303 |     -0.157 | 1.19905e+06 |   -81873.9 |
| GAP |  80 |   4 |           51 |          1.218 |     -0.242 | 1.08968e+06 |   -79867.8 |
| WER |  80 |   4 |           36 |          1.132 |     -0.328 | 1.03018e+06 |   -81873.9 |
| WER |  67 |   6 |           61 |          1.109 |     -0.351 | 1.02989e+06 |   -79867.8 |

Clean uplift distribution over the grid: median -0.114, share of cells > 0: 17%, best +0.063.

## Selected cell vs baseline pair

| span | metric | baseline | cell |
|---|---|---|---|
| clean | weekly Sharpe | 1.46 | 1.52 |
| clean | Sortino | 2.78 | 3.04 |
| clean | MAR | 4.75 | 5.38 |
| clean | net $ | 1,329,958.72 | 1,360,728.96 |
| clean | maxDD $ | 280,109.76 | 252,726.08 |
| clean | worst wk $ | -81,873.92 | -79,867.84 |
| clean | CVaR5 $ | -78,735.52 | -77,874.88 |
| clean | CVaR10 $ | -78,008.81 | -75,995.05 |
| clean | % neg wk | 42.86 | 44.76 |
| H1 | weekly Sharpe | 2.83 | 2.17 |
| H1 | Sortino | 6.09 | 4.34 |
| H1 | MAR | 3.91 | 2.43 |
| H1 | net $ | 593,797.44 | 481,193.92 |
| H1 | maxDD $ | 151,712.64 | 197,664.32 |
| H1 | worst wk $ | -78,287.36 | -78,287.36 |
| H1 | CVaR5 $ | -77,609.92 | -77,609.92 |
| H1 | CVaR10 $ | -66,029.97 | -66,029.97 |
| H1 | % neg wk | 39.29 | 42.86 |
| H2 | weekly Sharpe | 2.30 | 2.03 |
| H2 | Sortino | 4.69 | 4.15 |
| H2 | MAR | 3.50 | 3.14 |
| H2 | net $ | 761,254.40 | 682,271.68 |
| H2 | maxDD $ | 217,425.28 | 217,425.28 |
| H2 | worst wk $ | -82,524.48 | -82,524.48 |
| H2 | CVaR5 $ | -81,088.96 | -81,088.96 |
| H2 | CVaR10 $ | -79,185.12 | -79,185.12 |
| H2 | % neg wk | 44.44 | 47.22 |
| all | weekly Sharpe | 1.86 | 1.75 |
| all | Sortino | 3.63 | 3.50 |
| all | MAR | 9.59 | 9.99 |
| all | net $ | 2,685,010.56 | 2,524,194.56 |
| all | maxDD $ | 280,109.76 | 252,726.08 |
| all | worst wk $ | -82,524.48 | -82,524.48 |
| all | CVaR5 $ | -79,220.34 | -78,662.19 |
| all | CVaR10 $ | -78,243.12 | -76,935.64 |
| all | % neg wk | 42.86 | 45.24 |

Flagged weeks: 38 of 193 weeks (20%). Increment net $ by span: clean +30,770, H1 -112,604, H2 -78,983, all -160,816.

Mixed-in framing (pair + m x (cell - pair), weekly Sharpe uplift clean/H1/H2/all): m=0.1: +0.01/-0.06/-0.02/-0.01; m=0.2: +0.02/-0.13/-0.05/-0.02; m=0.3: +0.02/-0.20/-0.07/-0.03; m=0.5: +0.04/-0.33/-0.12/-0.05

## Gate checklist

- [FAIL] 3 uplift >= +0.10 clean/H1/H2 separately: +0.063 / -0.662 / -0.261
- [PASS] 3 worst week (all-in) not worse: -82,524 vs baseline -82,524
- [FAIL] 4 matched random-switch null (200): real all-in -0.106 vs p95 +0.031, rank 0.78; null mean -0.212
- [FAIL] 4 bootstrap 90% CI of all-in uplift > 0: [-0.312, +0.083]
- [FAIL] 5 plateau: 0% of 4 neighbours (x0.75/x1.25 of threshold percentile and of the action size or lock level) keep >=75% of all-in uplift: (0.75, 1): all -0.658 / clean -0.343; (1.25, 1): all -0.074 / clean -0.041; (1, 0.75): all -0.024 / clean +0.112; (1, 1.25): all -0.128 / clean +0.049
- [FAIL] 5 2x slippage uplift >= +0.10 each span: +0.010 / -0.583 / -0.227
- [INFO] 6 worst-decile-week corr of increment with pair (no hedge claim, not gated): -0.09
- [INFO] selection-aware null (12 permutations of the whole 12-cell grid, best clean uplift): median +0.038, max +0.223; real best +0.063 (share of permutations >= real: 33%). This is the chance level of the clean selection itself.
- [INFO] replication read-outs (only meaningful if gates 3-5 met): H0 2023-02..07 increment net $ -20,262 (cell 106,406 vs pair 126,668); alternating-month increment net $ (2023-02..2026-10): odd months +15,175, even months -196,253. Not formally run: no cell met the clean/H1/H2 uplift gate.
- [INFO] 1 pre-registered; 2 selection clean only, H1/H2 read once; 7 NT8 spec below.

## Insurance metrics (selected cell vs baseline; all-in)

cost_pct -6.0, cvar5_impr +0.7, cvar10_impr +1.7, worst_week_impr +0.0, maxdd_impr +9.8; insurance flag all-in: False.

## Executability / NT8 spec

Weekly Sunday job (python/CSV outside NT8) computes the prior-week range ratio / 8-week efficiency / weekend gap percentile vs the prior 104 weeks and writes the week-floor value (8 or F R) read by the strategies at the Sunday 18:00 session open; the floor logic is the existing combined week floor with a week-dependent parameter. Margin unchanged.

Note: states are causal weekly features from the 2013-26 NQ series (percentile vs prior 104 weeks). Tighten-only never worsened the worst week (-79.9k vs -81.9k clean) but the cut hurts H1 (-0.66) and H2 (-0.26): the selected clean cell is within the selection-aware null (sa null max +0.22). ERA n/a; H0/alt-month not run (gate failed).

DONE J11-A