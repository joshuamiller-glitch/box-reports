# REPORT C1-F5 — cross-asset conditioning of the pair's entries (ZN, 6J, BTC)

**Result: no FOUND. No cell improves the pair's weekly Sharpe by +0.10 on clean, H1 and H2 together; the filter family is NO.** Pre-registration: `outputs/autopilot/PREREG_AUTOPILOT.md` (C1-F5, unchanged grid).

## Design
- Baseline = live pair `B.Cfg(wk_floor=8, wk_loss_pb=None)` on the corrected-engine rows (`ROWS_corrected_engine.parquet`, 13,089 rows), computed in a clean process (weekly Sharpe clean 1.46 / H1 2.83 / H2 2.30). Robustness vs `B.Cfg()` (1.35/1.65/2.26): the same filters were not re-run on it; given the results below that cannot change the verdict.
- Context variable = the instrument's log-return over the prior W in {5, 15, 60} minutes, ending at the bar closing 1 minute BEFORE the entry minute (causal; contract-roll returns zeroed; NaN if the last bar is >30 min stale => the trade is never filtered).
- Score z = sign x side x move. The sign and the cut are **fitted on clean only** (sign = sign of the clean correlation between side x move and trade points; cut = the q-quantile of z over clean trades, q = 1/3 main, 0.25 and 0.40 neighbours). The bad tail (z < cut) is skipped or half-sized in all spans; H1/H2 untouched.
- Cells: 3 instruments x 3 windows x 3 cuts x {skip, half} = 54. Matched random-removal null: same per-book removal count, random trades, full re-simulation through the live rules (60 draws per top cell); 2x slippage; paired week bootstrap (4,000) of the all-in Sharpe uplift; 26-week rolling Sharpe share.
- Fill model/slippage: unchanged corrected engine, 1 tick/side + $34.88 commission (no live-fills file yet).

## Does the context carry information? (clean fit, then H1 / H2 untouched)
| inst | W | corr clean (side x move vs trade pts) | fitted sign | corr H1 | corr H2 | coverage |
|---|---|---|---|---|---|---|
| ZN | 5 | +0.0152 | +1 | +0.0191 | +0.0262 | 97% |
| ZN | 15 | +0.0047 | +1 | -0.0056 | +0.0247 | 95% |
| ZN | 60 | -0.0044 | -1 | +0.0050 | -0.0096 | 96% |
| 6J | 5 | -0.0069 | -1 | -0.0431 | +0.0011 | 97% |
| 6J | 15 | -0.0035 | -1 | -0.0240 | -0.0205 | 95% |
| 6J | 60 | -0.0044 | -1 | +0.0029 | +0.0031 | 96% |
| BTC | 5 | -0.0006 | -1 | -0.0112 | -0.0117 | 95% |
| BTC | 15 | -0.0033 | -1 | -0.0447 | -0.0134 | 94% |
| BTC | 60 | -0.0259 | -1 | -0.0507 | -0.0081 | 94% |

Correlations between the cross-asset move and a trade's points are about zero (|r| < 0.03 on clean) and the H1/H2 correlations do not keep the clean sign systematically; the information is not there before any filtering.

## All 54 cells (uplift = change in weekly Sharpe vs the live pair; worst week and max DD are all-in vs baseline)

| inst | W min | action | cut q | trades hit | clean dSh | H1 dSh | H2 dSh | all dSh | all net | all worst wk | all max DD | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6J | 15 | half-size | 0.25 | 21% | +0.10 | -0.11 | +0.08 | +0.07 | +2% | +0% | +1% | NO |
| ZN | 15 | half-size | 0.25 | 19% | -0.12 | +0.36 | -0.19 | -0.07 | -4% | +1% | -6% | NO |
| ZN | 15 | half-size | 0.40 | 33% | +0.10 | +0.29 | -0.27 | +0.02 | +0% | +4% | -3% | NO |
| 6J | 5 | half-size | 0.25 | 25% | -0.28 | -0.31 | +0.17 | -0.16 | -12% | +3% | +7% | NO |
| ZN | 15 | half-size | 0.33 | 28% | -0.09 | -0.33 | -0.31 | -0.18 | -9% | +3% | +2% | NO |
| ZN | 5 | half-size | 0.40 | 34% | -0.33 | +0.29 | -0.39 | -0.27 | -11% | +2% | +48% | NO |
| ZN | 15 | skip | 0.25 | 19% | -0.33 | +0.36 | -0.42 | -0.25 | -13% | -0% | +37% | NO |
| ZN | 5 | half-size | 0.33 | 25% | -0.11 | +0.05 | -0.46 | -0.17 | -6% | +3% | -8% | NO |
| ZN | 5 | half-size | 0.25 | 20% | -0.03 | -0.16 | -0.46 | -0.15 | -4% | +3% | -20% | NO |
| 6J | 15 | half-size | 0.33 | 31% | +0.04 | -0.55 | -0.24 | -0.11 | -10% | +1% | +1% | NO |
| ZN | 60 | half-size | 0.25 | 24% | -0.35 | -0.55 | +0.36 | -0.21 | -10% | +1% | +13% | NO |
| 6J | 60 | half-size | 0.33 | 34% | -0.08 | -0.56 | -0.40 | -0.22 | -15% | +2% | +37% | NO |
| ZN | 60 | half-size | 0.40 | 40% | -0.64 | -0.23 | -0.52 | -0.53 | -30% | -0% | +92% | NO |
| ZN | 15 | skip | 0.33 | 28% | -0.27 | -0.36 | -0.68 | -0.38 | -24% | +2% | +37% | NO |
| ZN | 5 | skip | 0.25 | 20% | -0.34 | -0.17 | -0.72 | -0.38 | -17% | +2% | -19% | NO |
| 6J | 15 | half-size | 0.40 | 40% | -0.17 | -0.74 | -0.05 | -0.23 | -19% | +4% | +7% | NO |
| ZN | 60 | skip | 0.25 | 24% | -0.54 | -0.80 | -0.23 | -0.51 | -28% | +1% | +24% | NO |
| BTC | 5 | skip | 0.33 | 31% | -0.39 | +0.31 | -0.80 | -0.35 | -23% | +1% | +5% | NO |
| 6J | 60 | half-size | 0.25 | 23% | -0.26 | -0.81 | +0.23 | -0.23 | -15% | +0% | +26% | NO |
| BTC | 5 | skip | 0.25 | 22% | -0.34 | -0.18 | -0.82 | -0.40 | -23% | +5% | -2% | NO |
| 6J | 60 | half-size | 0.40 | 41% | -0.35 | -0.02 | -0.83 | -0.40 | -27% | +2% | +40% | NO |
| ZN | 5 | skip | 0.40 | 34% | -0.39 | -0.30 | -0.85 | -0.47 | -24% | +2% | +5% | NO |
| ZN | 60 | half-size | 0.33 | 32% | -0.85 | -0.30 | -0.22 | -0.61 | -35% | -1% | +76% | NO |
| BTC | 15 | half-size | 0.25 | 22% | +0.07 | +0.21 | -0.86 | -0.10 | -6% | +3% | +22% | NO |
| BTC | 15 | half-size | 0.33 | 30% | +0.16 | -0.88 | -0.58 | -0.15 | -13% | +1% | +12% | NO |
| ZN | 5 | skip | 0.33 | 25% | -0.30 | +0.06 | -0.89 | -0.37 | -16% | +2% | -9% | NO |
| ZN | 15 | skip | 0.40 | 33% | -0.11 | -0.14 | -0.94 | -0.31 | -23% | +2% | +10% | NO |
| 6J | 5 | half-size | 0.33 | 37% | -0.58 | -0.32 | -0.98 | -0.63 | -41% | +3% | +11% | NO |
| 6J | 5 | skip | 0.25 | 25% | -0.92 | -1.03 | -0.58 | -0.86 | -49% | -2% | +8% | NO |
| 6J | 5 | half-size | 0.40 | 41% | -0.45 | -0.09 | -1.07 | -0.55 | -39% | +3% | +12% | NO |
| 6J | 60 | skip | 0.40 | 41% | -0.71 | -0.60 | -1.07 | -0.75 | -47% | +5% | +18% | NO |
| BTC | 5 | half-size | 0.33 | 31% | -0.36 | +0.47 | -1.11 | -0.42 | -24% | -3% | +32% | NO |
| 6J | 15 | skip | 0.25 | 21% | -0.16 | -0.86 | -1.14 | -0.48 | -29% | +3% | +1% | NO |
| 6J | 60 | skip | 0.33 | 34% | -0.42 | -0.54 | -1.16 | -0.60 | -35% | +4% | +11% | NO |
| BTC | 60 | half-size | 0.25 | 22% | -0.33 | -1.21 | -0.02 | -0.36 | -24% | +3% | +10% | NO |
| 6J | 15 | skip | 0.33 | 31% | -0.73 | -0.74 | -1.23 | -0.84 | -51% | +3% | +19% | NO |
| 6J | 60 | skip | 0.25 | 23% | -0.66 | -0.97 | -1.26 | -0.84 | -46% | +0% | +29% | NO |
| BTC | 5 | half-size | 0.25 | 22% | -0.48 | +0.35 | -1.37 | -0.56 | -30% | -3% | +37% | NO |
| BTC | 5 | half-size | 0.40 | 37% | -0.31 | -0.13 | -1.37 | -0.53 | -32% | +3% | +28% | NO |
| BTC | 15 | half-size | 0.40 | 36% | +0.00 | -1.40 | -0.89 | -0.41 | -26% | +1% | +8% | NO |
| 6J | 15 | skip | 0.40 | 40% | -0.70 | -1.04 | -1.60 | -0.96 | -60% | +1% | +17% | NO |
| BTC | 60 | half-size | 0.33 | 30% | -0.38 | -1.60 | -0.65 | -0.61 | -36% | +2% | -1% | NO |
| BTC | 60 | half-size | 0.40 | 37% | -0.33 | -1.75 | -0.85 | -0.65 | -39% | -0% | +12% | NO |
| 6J | 5 | skip | 0.33 | 37% | -1.23 | -1.17 | -1.77 | -1.31 | -76% | +3% | +16% | NO |
| BTC | 60 | skip | 0.25 | 22% | -0.28 | -1.83 | -1.28 | -0.75 | -42% | -2% | +18% | NO |
| BTC | 5 | skip | 0.40 | 37% | -0.62 | -0.50 | -1.84 | -0.83 | -52% | +1% | +11% | NO |
| BTC | 15 | skip | 0.25 | 22% | +0.25 | -1.12 | -1.84 | -0.42 | -24% | +4% | +10% | NO |
| ZN | 60 | skip | 0.33 | 32% | -1.03 | -0.74 | -2.02 | -1.17 | -68% | +1% | +110% | NO |
| 6J | 5 | skip | 0.40 | 41% | -1.41 | -1.79 | -2.05 | -1.60 | -89% | +3% | +68% | NO |
| BTC | 60 | skip | 0.33 | 30% | -0.42 | -2.18 | -1.23 | -0.87 | -49% | +1% | +21% | NO |
| BTC | 15 | skip | 0.33 | 30% | -0.46 | -2.15 | -2.42 | -1.17 | -65% | -3% | +85% | NO |
| ZN | 60 | skip | 0.40 | 40% | -0.78 | -0.18 | -2.55 | -1.02 | -62% | +3% | +114% | NO |
| BTC | 60 | skip | 0.40 | 37% | -0.14 | -2.65 | -1.59 | -0.88 | -52% | +2% | +31% | NO |
| BTC | 15 | skip | 0.40 | 36% | -0.56 | -2.48 | -2.99 | -1.45 | -80% | +0% | +118% | NO |

Gate 3 (+0.10 weekly Sharpe on clean, H1 and H2 each, worst week not worse in each): **0 of 54 cells pass**. Best min-span uplift: -0.11 (6J). Screen verdicts: 0 SURVIVES, 0 INSURANCE (screen uses the report keys on net and max DD only; no CVaR column).

## Top-3 cells per instrument by minimum span uplift: nulls, 2x slippage, bootstrap, rolling

| inst | cell | clean/H1/H2/all dSh | null p95 (clean/H1/H2/all) | rank in null (all) | 2x slip dSh (clean/H1/H2/all) | bootstrap 90% CI all dSh | rolling >= base |
|---|---|---|---|---|---|---|---|
| ZN | W15 half q.33 | -0.09/-0.33/-0.31/-0.18 | +0.07/+0.93/+0.52/+0.26 | 53% | +0.14/-0.36/-0.55/-0.09 | [-0.60, +0.23] | 27% |
| ZN | W5 half q.33 | -0.11/+0.05/-0.46/-0.17 | +0.05/+1.21/+0.86/+0.06 | 55% | -0.24/+0.18/-0.38/-0.20 | [-0.54, +0.18] | 25% |
| ZN | W15 skip q.33 | -0.27/-0.36/-0.68/-0.38 | +0.13/+1.35/+0.57/+0.14 | 62% | -0.05/-1.24/-0.80/-0.39 | [-1.00, +0.23] | 23% |
| 6J | W15 half q.33 | +0.04/-0.55/-0.24/-0.11 | +0.00/+1.51/+0.74/+0.13 | 63% | +0.24/-0.64/-0.36/-0.02 | [-0.53, +0.32] | 35% |
| 6J | W60 half q.33 | -0.08/-0.56/-0.40/-0.22 | +0.14/+1.47/+0.95/+0.21 | 45% | +0.12/+0.06/-0.53/-0.05 | [-0.78, +0.31] | 30% |
| 6J | W5 half q.33 | -0.58/-0.32/-0.98/-0.63 | +0.09/+1.43/+0.37/+0.09 | 7% | -0.38/-0.21/-1.48/-0.61 | [-1.15, -0.12] | 1% |
| BTC | W5 skip q.33 | -0.39/+0.31/-0.80/-0.35 | +0.43/+0.82/+0.39/+0.12 | 52% | -0.18/+0.31/-1.08/-0.28 | [-1.05, +0.37] | 21% |
| BTC | W15 half q.33 | +0.16/-0.88/-0.58/-0.15 | +0.15/+1.23/+0.81/+0.18 | 65% | +0.31/-1.18/-0.80/-0.16 | [-0.61, +0.29] | 30% |
| BTC | W5 half q.33 | -0.36/+0.47/-1.11/-0.42 | +0.17/+1.30/+0.26/+0.13 | 22% | -0.18/+0.50/-1.36/-0.34 | [-0.94, +0.08] | 27% |

## Reading
- 52 of 54 cells (96%) LOWER the all-in weekly Sharpe. Removing or halving about a third of the entries changes the path through the per-book rules and the day lock, and that interaction costs more than any information in the context adds; this is the same behaviour as every other entry filter in the programme.
- Plateau: no cell has a positive uplift on all three spans, so there is no neighbourhood to measure (gate 5 not reachable).
- Gates 6 and 7 translated for a filter: gate 6 (worst-decile correlation) is not a diversification test for an entry filter; the adapted test is worst week not worse in each span (reported in the table). Gate 7: implementing any of these would need DualStrat to subscribe to a second instrument's 1-minute data (ZN or 6J futures on Rithmic via NT8 can be added as a secondary data series in the strategy; BTC would need the CME crypto feed, unconfirmed at NinjaTrader Brokerage) and compute the prior-W-minute move at the signal bar; nothing is recommended since no cell passes.
- Hypothesis (risk-on/off context from rates, yen or crypto improves the pair's entries): rejected on this sample. Prior 6%.

DONE C1_F5
