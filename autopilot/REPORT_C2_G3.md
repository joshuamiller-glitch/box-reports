# REPORT C2-G3 — EVENT-DAY BREAKOUT SLEEVE (NQ: FOMC / NFP / CPI)
Autopilot cycle 2. Grid pre-registered in `PREREG_AUTOPILOT.md` ('CYCLE 2', C2-G3) before any run: event x first-{1,5,15}-minute range after the release x target {1,1.5,2}R x exit {release+60 min, 16:55 ET = 15:55 CT} = 54 cells; stop = opposite side of the range; one trade per event.

## Verdict: NO. FOUND 0, LEADS 0 (no cell passes even the first gate set).
- **54 of 54 cells fail gate 3** (weekly Sharpe up >= 0.10 on clean, H1 and H2 separately). The best clean uplift at a 20% share is +0.01; at 50% share it is +0.01. Constant-risk: 0 INSURANCE cells. At a 20% share the worst week "improves" ~19-21% in every cell, but that is the pair being shrunk 20% (net falls ~20%, against the 5% limit), not the sleeve.
- **0 of 54 cells beat their own random-non-event-day null at p95 on standalone Sharpe** in the pair window (best rank 0.82).
- Why the sleeve can't move the pair: only 25 FOMC, 37 NFP and 37 CPI events in 3.2 years, one trade each, so the sleeve is active in 15-22% of weeks. A trade-sized sleeve is a rounding error next to the pair's ~3,900 trades a year.

## Baseline, data, fills
- Pair: B.Cfg(wk_floor=8, wk_loss_pb=None) in a clean process (clean / H1 / H2 weekly Sharpe 1.46 / 2.83 / 2.30); robustness column vs B.Cfg() (1.35 / 1.65 / 2.26). Spans clean 2023-08..2025-07, H1 2025-08-01..2026-02-06, H2 2026-02-07..2026-10-13; UNTOUCHED never read.
- Bars: 1-minute NQ (the box series for the pair window; purchased Databento ohlcv-1m `data/autopilot/ohlcv1m/NQ_<year>` for the 2013..2023-07 holdout). Sanity: the same FOMC cell on the box series and on the Databento bars gives identical trades and net ($4,262, 7 trades, 2023-08..2024-06). 1-minute (not 1-second) bars are used, as in T3 S3; the first-minute range is one 1-minute bar, so an intrabar break inside the range bar itself cannot be traded — entry is allowed from the next bar (causal).
- Fill model: stop-entry at range edge +1 tick (or the open if it gaps through), stop at the opposite side of the range, stop-first when a bar spans both levels, target filled only on a 1-tick trade-through, 1 tick/side slippage on entry and stop exits (none on target), $4.36/contract commission, contracts = $9,600 / (stop distance x $20), capped at 16 (sleeve at one pair-book of risk, as in T3 S3). Sizing scales with the share.
- **Event dates.** FOMC 2023-2026: VERIFIED against federalreserve.gov (32 scheduled statement dates, 2025-08-22 notation vote excluded; includes 2026-07-29, 2026-09-16, 2026-10-28). NFP and CPI 2023-2026: VERIFIED from the bls.gov schedule pages for 2023, 2024, 2025, 2026 (2025 shutdown: no October jobs/CPI release; Sep jobs 2025-11-20; Nov jobs 2025-12-16; Sep CPI 2025-10-24; Nov CPI 2025-12-18). Pre-2023-08 FOMC (2013-2022): FROM MEMORY, unverified (emergency 2020 meetings excluded). Pre-2023-08 NFP: the BLS 'third Friday after the reference week' rule plus the holiday adjustments, which reproduces all 41 verified non-shutdown 2023-2026 release dates; Oct-Nov 2013 excluded (shutdown); otherwise unverified. CPI has no pre-2023 calendar (not available), so CPI has no holdout. Events in the pair window: FOMC 25, NFP 37, CPI 37.

## All 54 cells (additive at 20%, plus 50% and the constant-risk 20% readings)
| cell | trades | net $ (pair window) | weekly Sharpe | own-null p95 | own-null rank | clean dSh @20% | H1 dSh @20% | H2 dSh @20% | clean dSh @50% | H1 dSh @50% | H2 dSh @50% | worst wk chg @20% | worst-decile corr | const-risk net @20% | const-risk worst-wk impr @20% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CPI N1 T1.0 60min | 31 | -54.9k | -1.04 | 0.90 | 0.03 | -0.01 | -0.00 | -0.01 | -0.02 | -0.01 | -0.03 | 0.0% | -0.16 | -20.4% | 20.0% |
| CPI N1 T1.0 close | 37 | -90.1k | -0.97 | 0.95 | 0.04 | -0.01 | -0.00 | -0.03 | -0.03 | -0.01 | -0.06 | 0.0% | -0.17 | -20.7% | 20.0% |
| CPI N1 T1.5 60min | 31 | -50.1k | -0.89 | 0.96 | 0.07 | -0.01 | -0.00 | -0.01 | -0.01 | -0.01 | -0.03 | 0.0% | -0.16 | -20.4% | 20.0% |
| CPI N1 T1.5 close | 37 | -93.8k | -0.97 | 0.82 | 0.04 | -0.01 | -0.00 | -0.02 | -0.04 | -0.00 | -0.05 | 0.0% | -0.17 | -20.7% | 20.0% |
| CPI N1 T2.0 60min | 31 | -45.3k | -0.74 | 0.86 | 0.10 | -0.00 | -0.00 | -0.01 | -0.01 | -0.01 | -0.03 | 0.0% | -0.16 | -20.3% | 20.0% |
| CPI N1 T2.0 close | 37 | -103.4k | -1.01 | 0.87 | 0.03 | -0.01 | 0.00 | -0.04 | -0.03 | 0.00 | -0.10 | 0.0% | -0.17 | -20.8% | 20.0% |
| CPI N5 T1.0 60min | 24 | 0.3k | 0.01 | 1.06 | 0.41 | -0.00 | 0.00 | -0.00 | -0.00 | 0.01 | -0.01 | 0.0% | -0.21 | -20.0% | 20.0% |
| CPI N5 T1.0 close | 37 | -54.3k | -0.64 | 1.01 | 0.09 | -0.01 | -0.00 | -0.02 | -0.03 | -0.01 | -0.04 | 0.0% | -0.19 | -20.4% | 20.0% |
| CPI N5 T1.5 60min | 24 | 2.4k | 0.07 | 0.86 | 0.54 | -0.00 | 0.00 | -0.00 | -0.00 | 0.01 | -0.01 | 0.0% | -0.21 | -20.0% | 20.0% |
| CPI N5 T1.5 close | 37 | -45.3k | -0.47 | 0.69 | 0.27 | -0.01 | 0.00 | -0.03 | -0.02 | 0.00 | -0.08 | 0.0% | -0.19 | -20.3% | 20.0% |
| CPI N5 T2.0 60min | 24 | 2.4k | 0.07 | 0.80 | 0.54 | -0.00 | 0.00 | -0.00 | -0.00 | 0.01 | -0.01 | 0.0% | -0.21 | -20.0% | 20.0% |
| CPI N5 T2.0 close | 37 | -45.3k | -0.42 | 0.72 | 0.30 | -0.00 | 0.00 | -0.04 | -0.01 | 0.01 | -0.10 | 0.0% | -0.19 | -20.3% | 20.0% |
| CPI N15 T1.0 60min | 17 | -4.5k | -0.21 | 0.77 | 0.38 | 0.00 | 0.00 | -0.00 | 0.00 | 0.00 | -0.01 | 0.0% | -0.10 | -20.0% | 20.0% |
| CPI N15 T1.0 close | 36 | -72.7k | -0.86 | 0.74 | 0.09 | -0.01 | -0.00 | -0.02 | -0.03 | -0.01 | -0.06 | 0.0% | -0.17 | -20.5% | 20.0% |
| CPI N15 T1.5 60min | 17 | -4.5k | -0.21 | 0.78 | 0.42 | 0.00 | 0.00 | -0.00 | 0.00 | 0.00 | -0.01 | 0.0% | -0.10 | -20.0% | 20.0% |
| CPI N15 T1.5 close | 36 | -85.3k | -0.94 | 0.72 | 0.07 | -0.01 | -0.01 | -0.04 | -0.02 | -0.03 | -0.10 | 0.0% | -0.17 | -20.6% | 20.0% |
| CPI N15 T2.0 60min | 17 | -4.5k | -0.21 | 0.66 | 0.47 | 0.00 | 0.00 | -0.00 | 0.00 | 0.00 | -0.01 | 0.0% | -0.10 | -20.0% | 20.0% |
| CPI N15 T2.0 close | 36 | -66.1k | -0.65 | 0.72 | 0.17 | -0.00 | -0.01 | -0.04 | -0.01 | -0.03 | -0.10 | 0.0% | -0.17 | -20.5% | 20.0% |
| FOMC N1 T1.0 60min | 25 | -19.8k | -0.24 | 0.74 | 0.45 | -0.00 | -0.01 | 0.00 | -0.01 | -0.02 | 0.01 | -0.8% | -0.26 | -20.1% | 20.6% |
| FOMC N1 T1.0 close | 25 | -30.9k | -0.36 | 0.70 | 0.38 | -0.01 | -0.01 | 0.00 | -0.02 | -0.02 | 0.01 | -0.8% | -0.26 | -20.2% | 20.6% |
| FOMC N1 T1.5 60min | 25 | -0.6k | -0.01 | 0.72 | 0.64 | 0.00 | -0.01 | -0.01 | 0.00 | -0.01 | -0.02 | 2.3% | 0.36 | -20.0% | 17.7% |
| FOMC N1 T1.5 close | 25 | -10.5k | -0.10 | 0.72 | 0.56 | -0.00 | -0.01 | -0.01 | -0.00 | -0.02 | -0.02 | 2.3% | 0.35 | -20.1% | 17.7% |
| FOMC N1 T2.0 60min | 25 | -2.7k | -0.02 | 0.68 | 0.61 | 0.00 | -0.00 | -0.03 | 0.01 | -0.01 | -0.08 | 2.3% | 0.21 | -20.0% | 17.7% |
| FOMC N1 T2.0 close | 25 | -11.8k | -0.10 | 0.68 | 0.57 | 0.00 | -0.00 | -0.03 | 0.00 | -0.01 | -0.08 | 2.3% | 0.20 | -20.1% | 17.7% |
| FOMC N5 T1.0 60min | 24 | 4.1k | 0.05 | 0.76 | 0.65 | 0.00 | 0.01 | -0.02 | 0.00 | 0.02 | -0.05 | 2.3% | 0.21 | -20.0% | 17.7% |
| FOMC N5 T1.0 close | 25 | -11.3k | -0.14 | 0.79 | 0.52 | -0.00 | 0.01 | -0.02 | -0.01 | 0.02 | -0.05 | 2.3% | 0.21 | -20.1% | 17.7% |
| FOMC N5 T1.5 60min | 24 | 42.1k | 0.45 | 0.79 | 0.81 | 0.01 | 0.01 | -0.02 | 0.01 | 0.04 | -0.05 | 2.3% | 0.21 | -19.7% | 17.7% |
| FOMC N5 T1.5 close | 25 | 33.1k | 0.32 | 0.82 | 0.74 | 0.00 | 0.01 | -0.02 | 0.01 | 0.03 | -0.05 | 2.3% | 0.21 | -19.8% | 17.7% |
| FOMC N5 T2.0 60min | 24 | 39.1k | 0.37 | 0.73 | 0.82 | 0.00 | 0.02 | -0.02 | 0.00 | 0.05 | -0.04 | 2.3% | 0.21 | -19.7% | 17.7% |
| FOMC N5 T2.0 close | 25 | 25.3k | 0.23 | 0.75 | 0.69 | -0.00 | 0.02 | -0.02 | -0.01 | 0.05 | -0.04 | 2.3% | 0.20 | -19.8% | 17.7% |
| FOMC N15 T1.0 60min | 24 | -3.1k | -0.04 | 0.61 | 0.60 | -0.00 | -0.00 | 0.00 | -0.01 | -0.01 | 0.00 | 1.1% | 0.21 | -20.0% | 18.9% |
| FOMC N15 T1.0 close | 25 | -17.1k | -0.21 | 0.74 | 0.44 | -0.01 | -0.01 | 0.00 | -0.02 | -0.03 | 0.01 | 2.3% | 0.37 | -20.1% | 17.7% |
| FOMC N15 T1.5 60min | 24 | 15.7k | 0.20 | 0.61 | 0.79 | -0.00 | -0.00 | 0.01 | -0.01 | -0.01 | 0.01 | 1.1% | 0.21 | -19.9% | 18.9% |
| FOMC N15 T1.5 close | 25 | 18.0k | 0.19 | 0.76 | 0.69 | -0.00 | -0.01 | 0.01 | -0.01 | -0.02 | 0.02 | 2.3% | 0.35 | -19.9% | 17.7% |
| FOMC N15 T2.0 60min | 24 | 12.6k | 0.16 | 0.63 | 0.75 | -0.00 | -0.01 | 0.01 | -0.01 | -0.02 | 0.02 | 1.1% | 0.21 | -19.9% | 18.9% |
| FOMC N15 T2.0 close | 25 | -18.3k | -0.18 | 0.72 | 0.45 | -0.00 | -0.02 | -0.01 | -0.01 | -0.05 | -0.02 | 2.3% | 0.19 | -20.1% | 17.7% |
| NFP N1 T1.0 60min | 34 | -44.3k | -0.63 | 0.94 | 0.16 | -0.01 | -0.03 | 0.01 | -0.02 | -0.06 | 0.01 | 1.5% | 0.52 | -20.3% | 18.3% |
| NFP N1 T1.0 close | 37 | -14.2k | -0.14 | 0.85 | 0.46 | -0.00 | -0.02 | 0.01 | -0.01 | -0.05 | 0.02 | 1.5% | 0.51 | -20.1% | 18.3% |
| NFP N1 T1.5 60min | 34 | -54.5k | -0.82 | 0.95 | 0.08 | -0.01 | -0.03 | 0.00 | -0.02 | -0.06 | 0.01 | 1.5% | 0.52 | -20.4% | 18.3% |
| NFP N1 T1.5 close | 37 | -67.0k | -0.62 | 0.84 | 0.15 | -0.01 | -0.02 | -0.01 | -0.01 | -0.06 | -0.03 | 1.5% | 0.45 | -20.5% | 18.3% |
| NFP N1 T2.0 60min | 34 | -54.5k | -0.82 | 0.87 | 0.09 | -0.01 | -0.03 | 0.00 | -0.02 | -0.06 | 0.01 | 1.5% | 0.52 | -20.4% | 18.3% |
| NFP N1 T2.0 close | 37 | -62.2k | -0.51 | 0.86 | 0.17 | -0.00 | -0.04 | -0.01 | -0.00 | -0.10 | -0.02 | 1.5% | 0.41 | -20.5% | 18.3% |
| NFP N5 T1.0 60min | 34 | -53.8k | -0.95 | 1.10 | 0.02 | -0.01 | -0.02 | -0.00 | -0.01 | -0.05 | -0.01 | 0.0% | -0.33 | -20.4% | 20.0% |
| NFP N5 T1.0 close | 37 | -45.3k | -0.46 | 0.99 | 0.14 | 0.00 | -0.04 | -0.00 | 0.01 | -0.10 | -0.01 | 0.0% | -0.26 | -20.3% | 20.0% |
| NFP N5 T1.5 60min | 34 | -57.1k | -1.04 | 0.87 | 0.02 | -0.01 | -0.02 | -0.00 | -0.02 | -0.05 | -0.01 | 0.0% | -0.33 | -20.4% | 20.0% |
| NFP N5 T1.5 close | 37 | -72.9k | -0.67 | 0.71 | 0.15 | -0.00 | -0.04 | -0.01 | -0.00 | -0.10 | -0.03 | 1.5% | 0.44 | -20.5% | 18.3% |
| NFP N5 T2.0 60min | 34 | -57.1k | -1.04 | 0.85 | 0.03 | -0.01 | -0.02 | -0.00 | -0.02 | -0.05 | -0.01 | 0.0% | -0.33 | -20.4% | 20.0% |
| NFP N5 T2.0 close | 37 | -69.0k | -0.61 | 0.72 | 0.19 | -0.00 | -0.04 | -0.01 | -0.01 | -0.10 | -0.03 | 1.5% | 0.48 | -20.5% | 18.3% |
| NFP N15 T1.0 60min | 29 | -0.1k | -0.00 | 0.87 | 0.53 | -0.00 | -0.01 | 0.01 | -0.00 | -0.03 | 0.01 | 0.0% | -0.33 | -20.0% | 20.0% |
| NFP N15 T1.0 close | 37 | -52.3k | -0.55 | 0.77 | 0.22 | -0.00 | -0.02 | -0.01 | -0.01 | -0.04 | -0.02 | 0.0% | -0.26 | -20.4% | 20.0% |
| NFP N15 T1.5 60min | 29 | -0.1k | -0.00 | 0.79 | 0.57 | -0.00 | -0.01 | 0.01 | -0.00 | -0.03 | 0.01 | 0.0% | -0.33 | -20.0% | 20.0% |
| NFP N15 T1.5 close | 37 | -31.2k | -0.28 | 0.80 | 0.39 | -0.00 | -0.01 | -0.00 | -0.01 | -0.03 | -0.01 | 1.5% | 0.44 | -20.2% | 18.3% |
| NFP N15 T2.0 60min | 29 | -0.1k | -0.00 | 0.66 | 0.63 | -0.00 | -0.01 | 0.01 | -0.00 | -0.03 | 0.01 | 0.0% | -0.33 | -20.0% | 20.0% |
| NFP N15 T2.0 close | 37 | -40.2k | -0.36 | 0.72 | 0.33 | -0.01 | -0.01 | 0.00 | -0.02 | -0.02 | 0.00 | 1.5% | 0.48 | -20.3% | 18.3% |

Every cell is a **small-sample** book (< 100 trades in the pair window: 17-37 trades).

## Clean-only selection (best clean dSharpe at 20% additive per event type), read once on H1/H2
| choice | cell | trades | Sharpe | own-null p95 | clean dSh | H1 dSh | H2 dSh | boot 90% CI (all-in dSh) | shift-null rank | 2x slip clean/H1/H2 | vs B.Cfg() clean/H1/H2 | plateau (nbrs keep 75%) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FOMC | FOMC N5 T1.5 60min | 24 | 0.45 | 0.79 | 0.01 | 0.01 | -0.02 | -0.010..0.014 | 0.01 | 0.01/0.01/-0.02 | 0.01/0.02/-0.02 | 0.00 |
| NFP | NFP N5 T1.0 close | 37 | -0.46 | 0.99 | 0.00 | -0.04 | -0.00 | -0.016..0.009 | 0.96 | 0.00/-0.04/-0.00 | 0.00/-0.03/-0.01 | n/a |
| CPI | CPI N15 T2.0 60min | 17 | -0.21 | 0.66 | 0.00 | 0.00 | -0.00 | -0.004..0.002 | 0.51 | 0.00/0.00/-0.00 | -0.00/0.00/-0.00 | n/a |
| hold-best (not clean-selected) | NFP N5 T1.0 close | 37 | -0.46 | 0.99 | 0.00 | -0.04 | -0.00 | -0.016..0.009 | 0.96 | 0.00/-0.04/-0.00 | 0.00/-0.03/-0.01 | n/a |

Plateau is moot where the uplift is ~0 (the neighbours cannot keep 75% of nothing).

## Untouched pre-2023-08 holdout (2013-01..2023-07, same rules; the honest test for a few-trade sleeve)
| cell | events | trades | net $ | weekly Sharpe | own-null p95 | rank | win rate |
|---|---|---|---|---|---|---|---|
| NFP N5 T1.0 close | 125 | 123 | 101.3k | 0.39 | 0.27 | 0.98 | 0.55 |
| FOMC N1 T1.0 60min | 84 | 84 | 66.1k | 0.34 | 0.41 | 0.93 | 0.58 |
| FOMC N1 T1.0 close | 84 | 84 | 54.8k | 0.27 | 0.40 | 0.89 | 0.57 |
| FOMC N1 T1.5 60min | 84 | 84 | 48.7k | 0.21 | 0.35 | 0.88 | 0.46 |
| FOMC N1 T1.5 close | 84 | 84 | 50.9k | 0.21 | 0.37 | 0.89 | 0.46 |
| FOMC N1 T2.0 close | 84 | 84 | 32.1k | 0.12 | 0.37 | 0.79 | 0.40 |
| FOMC N15 T2.0 close | 84 | 83 | 22.4k | 0.09 | 0.39 | 0.70 | 0.43 |
| FOMC N1 T2.0 60min | 84 | 84 | 16.6k | 0.07 | 0.32 | 0.75 | 0.43 |
| NFP N15 T1.0 60min | 125 | 86 | 5.0k | 0.06 | 0.19 | 0.90 | 0.47 |
| NFP N1 T1.0 close | 125 | 124 | 12.3k | 0.05 | 0.30 | 0.83 | 0.48 |

1 of 36 FOMC/NFP cells beats its own random-date null at p95 on the holdout: **NFP N5 T1.0 close** (Sharpe 0.39 vs p95 0.27, rank 0.98, 123 trades, +$101k over 10.5 years). In the pair window the same cell loses $45k (Sharpe -0.46, rank 0.14), so there is no persistence. With 36 holdout cells, one at p95 is the chance rate. The FOMC 1-minute-range cells are mildly positive on the holdout (Sharpe 0.2-0.34, rank 0.88-0.93, not significant) and about flat in the pair window.

## Gate checklist (FOUND needs all seven)
1. Pre-registered: yes. 2. Selection on clean only; H1/H2 read once: yes (selection table above), but nothing to select. 3. Additive uplift >= 0.10 on each span: **FAIL (54/54)**. 4. Own timing-destroyed null p95 + bootstrap CI > 0: **FAIL (0/54 beat the null; bootstrap lower bounds <= 0)**; the circular-shift null is reported (rank column) and would only gate a hedge claim. 5. Plateau / 2x slippage: not reached; 2x-slippage readings are in the selection table. 6. Worst-decile correlation <= +0.30: passes in most cells (17 weeks, imprecise; across the 54 cells at 20% share: FOMC -0.26..+0.37, NFP -0.33..+0.52, CPI -0.21..-0.10; some NFP/FOMC cells exceed +0.30) — but the sleeve is simply too small to matter. 7. Executability: NQ futures; one NT8 strategy that arms at the release time (calendar file with the event dates), places stop-entry orders at the first-N-minute range edges, OCO with the opposite-side stop and a target, flattens at release+60 min or 15:55 CT. DualStrat would need none of its logic; it is a separate strategy plus an events calendar. Margin (assumed, unverified, same convention as other autopilot reports): ~$22k per NQ contract overnight, intraday lower; the largest cell holds up to 16 contracts at 100% pair-book risk (about 9-12 contracts for the N=5 and N=15 ranges), i.e. 1.6-2.4 contracts at a 10-20% share.

## Reading
Event-day breakouts on NQ do not add to the pair. The clean, H1 and H2 uplifts are indistinguishable from zero at every share, the sleeve does not beat random non-event days at the same time of day, and the one holdout-significant cell (NFP, 5-minute range, 1R, to the close) reverses sign in the pair window. Nothing goes to CANDIDATES.md.

## Runtime
Simulation 9 s, scoring (54 cells x 8 share/framing rows, 2,000-draw bootstraps, 600-draw own nulls) 40 s, holdout (36 cells, 500-draw nulls) about 90 s, single process. Slippage 1 tick/side (live-fills file not received).

DONE C2_G3
