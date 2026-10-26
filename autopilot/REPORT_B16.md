# REPORT B16 - graded week de-risking (Q-2)
**Verdict: NO. FOUND 0, LEAD 0. All 6 cells lose Sharpe on clean (best X=5R, 50% size: -0.23 clean; H1 -0.89, H2 -0.55); bootstrap 90% CI [-0.69, -0.12], null p95 +0.18 (rank 0%).**
Cells 6 (X in {3,4,5}R x size {50%, 25%}); runtime about 2.5 min (pool of 5). Pre-registered in PREREG_AUTOPILOT.md (B15/B16 section) before the first run.

## Set-up and fill model
- Same engine/fill as B15 (b11_nt8, ROWS_corrected_engine, 1 tick/side + $34.88, minute marks, clean-process baseline reproduced exactly). Rule: once the week equity (after the day-lock stage) first reaches <= -X R, new entries for the rest of the week are taken at size k; open positions untouched; -8R floor applied on the reduced-size equity.
- Selection clean only (clean weekly Sharpe uplift vs 1.46): X5/k.50 -0.234, X3/k.50 -0.342, X5/k.25 -0.347, X4/k.50 -0.416, X3/k.25 -0.596, X4/k.25 -0.678. All negative; X5/k.50 carried (74 trigger weeks), H1/H2 read once.

## Gate checklist (X=5R, k=50%)
| gate | result | pass |
|---|---|---|
| uplift >= +0.10 clean / H1 / H2 | -0.23 / -0.89 / -0.55 | NO |
| worst week not worse | -79.5k vs -81.9k clean, -78.5k vs -78.3k H1, -76.2k vs -82.5k H2 (all-in -79.5k vs -82.5k, 3% better) | yes |
| random-switch null p95 (200 draws, 74 random weeks, random minute, k=50%) | real -0.40 vs p95 +0.18 (null mean -0.01, rank 0%) | NO |
| bootstrap 90% CI all-in | [-0.69, -0.12] | NO |
| plateau (X 3.75/6.25, k .375/.625) | all-in -0.48 / -0.23 / -0.52 / -0.33 | NO |
| 2x slippage uplift | -0.19 / -0.81 / -0.55 | NO |
| insurance | not insurance: net -24% all-in, maxDD 383k vs 280k clean (worse), CVaR5 only -1% better all-in, % neg weeks 51 vs 43 | NO |
| corr(delta, baseline) in worst-decile weeks | -0.05 (descriptive) | n/a |
| NT8-codable | yes (week-equity tracker setting size multiplier) | yes |
Vs B.Cfg(): modification on Cfg() vs Cfg() -0.21 / -0.12 / -0.46 (all-in -0.25).

## Insurance metric set (variant / baseline)
| span | net $ | weekly Sharpe | Sortino | MAR | maxDD $ | worst wk $ | CVaR5 | CVaR10 | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | 1.093M / 1.330M | 1.23 / 1.46 | 2.43 / 2.78 | 2.85 / 4.75 | 383k / 280k | -79.5k / -81.9k | -77.8k / -78.7k | -74.6k / -78.0k | 50 / 43 |
| H1 | 422k / 594k | 1.94 / 2.83 | 4.02 / 6.09 | 2.48 / 3.91 | 170k / 152k | -78.5k / -78.3k | -77.9k / -77.6k | -67.0k / -66.0k | 50 / 39 |
| H2 | 525k / 761k | 1.74 / 2.30 | 3.74 / 4.69 | 2.63 / 3.50 | 200k / 217k | -76.2k / -82.5k | -66.2k / -81.1k | -60.9k / -79.2k | 50 / 44 |
| all | 2.039M / 2.685M | 1.46 / 1.86 | 2.94 / 3.63 | 5.33 / 9.59 | 383k / 280k | -79.5k / -82.5k | -77.7k / -79.2k | -72.2k / -78.2k | 51 / 43 |

## Why it fails
Weeks that reach -3..-5R intraweek recover often enough (the pair has positive edge and the recoveries are what the week floor already cost) that cutting size after the dip removes more upside than it saves: net falls 20-30% while worst week improves only 3%. Smaller size (k=25%) and lower X are worse monotonically. Mean-reversion of weekly P&L (lag-1 autocorr negative) is the opposite of what de-risking assumes.
Executability: DualStrat change; not recommended.

Files: code/census/night_ins/ap_b15_core.py, ap_b15_run.py; outputs/autopilot/b16/.
DONE B16
