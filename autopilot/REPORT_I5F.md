# REPORT I5F - IDEAS-5000 family F: regime monitors (report-only), 71 series x 3 horizons x 2 targets

Written 2026-10-17 by worker FA. Registered in outputs/ideas5000/PREREG_IDEAS5000.md (family F section and amendment F1) before any correlation was run. Code: code/census/night_ins/ap_i5f_build.py, ap_i5f_run.py, ap_i5f_switch.py, ap_i5f_report.py. Outputs: outputs/ideas5000/i5f/ (weekly_drivers.pkl, coverage.csv, tests.csv, tests_grouped.csv, switch.csv, hits_*.csv), 213 rows in outputs/ideas5000/CELLS.csv (family F), 1 row in TALLY.csv. No purchases; gates unchanged; report-only (no sleeve, no library save).

## 1. Verdict

**No ex-ante switch survives. After FDR across 426 tests the smallest q is 0.213 (0 survivors at q <= 0.10); the 57 tests at p <= 0.05 (21.3 expected) are essentially one block of volatility/volume-level series against the 2013-26 engine-proxy pair Sharpe, and the same series do nothing on the real pair (2023-26) or on the REGIME fade factor.** The three best series fail the out-of-sample switch test (clean uplift -0.17 to -0.20). FOUND 0, LEAD 0, FOUND-PENDING 0 from this family. This repeats the REGIME study's finding.

## 2. What was tested

* **71 series** (daily values averaged to ISO weeks, Friday label; coverage per series in i5f/coverage.csv): Globex share and 18:00-02:00 ET share of daily volume (NQ, ES); 1-min price-change share (RTH, Globex); lag-1 autocorrelation, variance ratio VR(5) and Ornstein-Uhlenbeck half-life of 1-min RTH returns; log realised variance (RTH, Globex), 20-day vol-of-vol, |delta log RV|; log volume and range/volume; overnight-gap share of the daily range; NQ-ES 1-min beta and R2 (RTH, Globex); VIX level, VIX3M/VIX, VIX6M/VIX3M, VIX9D/VIX, VVIX, VVIX/VIX, SKEW, |dVIX|, 5-day VIX change, VIX minus ES realised vol; NDX 0DTE volume share, NDX put/call volume, NQ and ES option open interest (level and 5-day change) and option volume; MNQ/NQ and MES/ES volume share (count and notional); NDX top-7 dollar-volume concentration (AAPL MSFT NVDA AMZN GOOGL META TSLA vs AVGO NFLX COST in the basket panel, RTH); trade-flow series from the DRIVERS trade files (2023-02 on): average trade size (RTH, Globex), trades per minute, big-flow ratio, mean per-minute max trade, absolute signed-volume imbalance (NQ, ES).
* **Data-gated (not tested, nothing bought):** SPX 0DTE share of SPX volume (only NDX option volume is on disk; ndx_0dte_share is that series), fed-funds level and change (no series on disk), MNQ/NQ by session (only daily micro volume on disk), a true block-trade share (only the minute 'big' count exists, so bigshare_* is a big-flow ratio, ES values above 1 by construction).
* **3 horizons:** H1 = weekly value; H4 = trailing 4-week mean; H13 = trailing 13-week mean. **2 targets:** Y1 = pair rolling 13-week Sharpe (real library PAIR for series that start in 2023, otherwise the 2013-26 engine proxy of C3-H2: 1-min fixed 60/60 engine, net -$2.2M over 2013-22); Y2 = rolling 13-week Sharpe of the REGIME ALL_net fade factor (REGIME_live.csv). Contemporaneous Pearson r, both sides linearly detrended. 213 cells (series x horizon), 426 tests.
* **Null and FDR.** Per test p = max of (a) circular block permutation of the driver, 13-week blocks, 2,000 draws, and (b) Fourier phase randomisation of the driver, 2,000 draws (amendment F1: block permutation alone gave 111 tests at p <= 0.05 and 91 BH survivors, because 13-week blocks destroy the multi-year level shifts that driver and targets share; the phase null keeps the driver's autocorrelation; the stricter definition was adopted and the original count is reported). BH across all 426 tests; survivor = q <= 0.10.

## 3. Result

Tests with p <= 0.05 (chance expectation = 5% of tests; series share structure so the spread is wider than binomial; 'p_block05' and 'p_phase05' are the two component nulls):

By target:

| target | tests | p05 | exp05 | p_block05 | p_phase05 | minq |
|---|---|---|---|---|---|---|
| fade | 213.0 | 7.000 | 10.7 | 22.0 | 9.000 | 0.228 |
| pair | 213.0 | 50.0 | 10.7 | 89.0 | 50.0 | 0.213 |

By horizon:

| horizon | tests | p05 | exp05 | p_block05 | p_phase05 | minq |
|---|---|---|---|---|---|---|
| H1 | 142.0 | 12.0 | 7.100 | 32.0 | 12.0 | 0.228 |
| H13 | 142.0 | 24.0 | 7.100 | 41.0 | 25.0 | 0.213 |
| H4 | 142.0 | 21.0 | 7.100 | 38.0 | 22.0 | 0.228 |

By target source (the decisive split):

| target_src | tests | p05 | expected | block_only_p05 |
|---|---|---|---|---|
| REGIME ALL_net | 213.0 | 7.000 | 10.7 | 22.0 |
| engine proxy | 162.0 | 48.0 | 8.100 | 87.0 |
| real PAIR | 51.0 | 2.000 | 2.600 | 2.000 |

By series group:

| group | tests | p05 | exp05 | p_block05 | p_phase05 | minq |
|---|---|---|---|---|---|---|
| NQ-ES beta/R2 | 24.0 | 1.000 | 1.200 | 4.000 | 1.000 | 0.303 |
| VIX/vol-index | 60.0 | 9.000 | 3.000 | 20.0 | 9.000 | 0.228 |
| micro share/basket | 30.0 | 12.0 | 1.500 | 13.0 | 12.0 | 0.264 |
| microstructure / session (price-change, MR, gap, shares) | 96.0 | 12.0 | 4.800 | 42.0 | 12.0 | 0.228 |
| options/OI | 48.0 | 1.000 | 2.400 | 5.000 | 2.000 | 0.343 |
| realised vol / volume level | 72.0 | 17.0 | 3.600 | 21.0 | 17.0 | 0.213 |
| trade-flow (2023+) | 96.0 | 5.000 | 4.800 | 6.000 | 6.000 | 0.228 |

Top 15 tests by p (r on detrended weekly data, n = weeks):

| series | horizon | target | target_src | n | r | p_block | p_phase | p | q |
|---|---|---|---|---|---|---|---|---|---|
| lnRV_rth_NQ | H13 | pair | engine proxy | 706 | -0.424 | 0.000 | 0.000 | 0.000 | 0.213 |
| lnRV_glx_NQ | H13 | pair | engine proxy | 706 | -0.426 | 0.000 | 0.001 | 0.001 | 0.228 |
| range_per_vol_ES | H4 | pair | engine proxy | 706 | -0.334 | 0.000 | 0.003 | 0.003 | 0.228 |
| lnRV_rth_NQ | H4 | pair | engine proxy | 706 | -0.357 | 0.000 | 0.004 | 0.004 | 0.228 |
| range_per_vol_ES | H13 | pair | engine proxy | 706 | -0.366 | 0.000 | 0.004 | 0.004 | 0.228 |
| absimb_rth_ES | H4 | pair | real PAIR | 181 | 0.311 | 0.004 | 0.004 | 0.004 | 0.228 |
| vix_level | H4 | pair | engine proxy | 706 | -0.408 | 0.000 | 0.004 | 0.004 | 0.228 |
| lnRV_glx_ES | H4 | pair | engine proxy | 706 | -0.327 | 0.000 | 0.005 | 0.005 | 0.228 |
| lnRV_glx_ES | H13 | pair | engine proxy | 706 | -0.370 | 0.000 | 0.005 | 0.005 | 0.228 |
| vix_level | H13 | pair | engine proxy | 706 | -0.437 | 0.000 | 0.006 | 0.006 | 0.228 |
| lnRV_glx_NQ | H4 | pair | engine proxy | 706 | -0.351 | 0.000 | 0.006 | 0.006 | 0.228 |
| avgsize_rth_NQ | H13 | fade | REGIME ALL_net | 182 | -0.468 | 0.006 | 0.001 | 0.006 | 0.228 |
| vix_level | H1 | pair | engine proxy | 706 | -0.352 | 0.000 | 0.007 | 0.007 | 0.228 |
| nzchg_glx_ES | H13 | pair | engine proxy | 706 | -0.382 | 0.000 | 0.007 | 0.007 | 0.228 |
| lnRV_rth_ES | H4 | pair | engine proxy | 706 | -0.291 | 0.002 | 0.008 | 0.008 | 0.235 |

Reading.
1. **Against the real pair (2023-26, 51 tests, the only target that is the live system): 2 hits at p <= 0.05 against 2.6 expected.** Against the fade factor (213 tests): 7 against 10.7 expected, fewer than chance.
2. **The excess is against the 2013-26 engine-proxy pair: 48 of 162 tests (8.1 expected), 45 with a negative sign.** It is one pattern repeated across correlated series: weeks with high realised volatility, high VIX, high volume, wide range per volume, more price-change activity and a high Globex/Asia volume share coincide with a lower rolling pair Sharpe. This is the REGIME contrast again: the proxy pair loses over 2013-22 (including the high-volatility years 2018-22) and earns from 2023. The phase-randomised null removes 40% of the block-null hits and BH removes the rest; the strongest, log RV (NQ RTH, 13-week), r = -0.42, has q = 0.21. These series are far from independent (a dozen or so effective drivers), so 48 hits is a handful of effects counted many times.
3. **Horizon:** hits increase with smoothing (H13 24, H4 21, H1 12 of 142 tests each, 7.1 expected): slow series correlate with a slow 13-week target through shared trend, which the phase null is designed to discount.
4. **Series specifically requested:** micro share (MNQ/NQ, MES/ES), NDX top-7 concentration, NDX 0DTE share, open interest, NQ-ES beta/R2, VIX term slope, vol-of-vol, trade size, block-flow ratio, price-change rate, mean-reversion measures, gap share, Globex and Asia share: none has q below 0.21 on any horizon or target. All p-values are in i5f/tests.csv.

## 4. Out-of-sample switch test

No survivor, so the switch was run report-only on the three best distinct series (rule fixed in the prereg: driver vs its trailing 52-week terciles, 2-sided; the pair size is halved in the tercile whose expanding-window mean next-week proxy-pair P&L was lower, training strictly before the decision week, minimum 104 weeks of history; uplift on the real pair's weekly Sharpe):

| series | horizon | target | r | p | q | kind | clean | H1 | H2 | cut_share | gate3 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| lnRV_rth_NQ | H13 | pair | -0.424 | 0.000 | 0.213 | near-miss (report only) | -0.181 | 0.000 | 0.001 | 0.347 | False |
| lnRV_glx_NQ | H13 | pair | -0.426 | 0.001 | 0.228 | near-miss (report only) | -0.168 | 0.000 | -0.103 | 0.404 | False |
| range_per_vol_ES | H4 | pair | -0.334 | 0.003 | 0.228 | near-miss (report only) | -0.196 | 0.145 | -0.490 | 0.399 | False |

Gate 3 (+0.10 on clean, H1 and H2) fails for all three. The clean-span uplift is negative (-0.17 to -0.20): the rule trained on the 2013-22 proxy years, where high-volatility weeks lost money, and so cuts the real pair in 2023-26 when it earned in those weeks; H1/H2 are flat or mixed. The relation the correlation sees does not carry into the era the pair trades.

## 5. Chance accounting (TALLY.csv)

213 cells scored at stage 1, 426 tests, expected 21.3 at p <= 0.05, observed 57 (48 against the proxy pair on the engine-proxy target, 9 on the two others); BH survivors 0; gate-3 passes 0; LEAD 0, FOUND-PENDING 0, FOUND 0. Restricted to the real pair and the fade factor (264 tests, 13.2 expected) the observed count is 9, below chance.

## 6. Caveats

* Pair history before 2023 is the engine proxy, not live trading, and 2023-26 gives only 167 weeks (about 13 independent 13-week windows), so the real-pair tests have little power. A driver with a modest real effect would not be detected; what can be said is that none is large enough to pass FDR, and the one large effect visible (volatility level vs the proxy) does not reproduce on the real pair.
* Weekly-mean aggregation, 13-week blocks and contemporaneous (not forward) correlation are choices fixed in the prereg; a forward-looking version would be a new test.
* Trade-flow series cover 2023-26 (194 weeks), options/OI series 2019-26, micro-share series 2019-26.

DONE I5F
