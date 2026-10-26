# REPORT IDEAS50K N3 / N7 / N8 (worker a3a74, 2026-10-17): term structure and calendar, multi-day books, portfolio-level mechanisms - METHOD-2 family scoring

**Verdict: 264 new families / 29,285 cells scored (N3 83 families / 7,667 cells; N7 130 / 12,488; N8 51 / 9,130); 12 pass gates a-d, against a chance expectation of 5.3-13.2 (2%-5% per family); 0 pass best-of-F at F_eff 594 (the best rank is 0.048). The passes are what chance predicts; none is a finding.** The 12 refill (K1) families around the passers (neighbouring cells, separate batch, never used to pick a family) pass in 10 of 12 cases, as neighbours of a passer would; that is plateau evidence of a shared effect, not independent evidence.

## Scope, data and what was not possible
- Data on disk only: 26 CME outrights daily, front (.v.0) and second (.v.1) continuous, 2013-01..2026-10-16 (RTY from 2017-07), back-adjusted with the T4 roll handling; VX futures daily from 2018-11. **Possible horizon for term structure: DAILY only** (intraday front/second-month data is not on disk). The NQ second-month series has only 28 days in the 2023-2026 window, so N3-CARRY-NQ and N3-SPREAD-NQ could not be scored (2 dropped families: N3-CARRY-NQ, N3-SPREAD-NQ); they count toward F as not scored.
- Engine: vectorised daily-hold simulator (ap_n_eng.py): decision at the close of day t from information up to t, P&L over day t+1 on back-adjusted closes, daily vol-targeted size (contracts = $1,000 / (ATR20 x point value), fractional, rebalanced daily), cost 1 tick/side + commission/2 per side on every size change, a roll inside the hold costs one extra round trip (calendar-spread books: four sides), per-cell volmatch to the library standard, series-hash dedupe against HASH50K. Fills are modelled at the close (MOC-like) - NT8 would use a market order at the last minute: a reconciliation item. No NT8 reconciliation of the daily simulator was done (market-entry daily books, class 2).
- METHOD-2: 12/3/3 tilt, first OOS week 2024-02, family null = 200 custom run-structure-matched random-entry worlds (per year: same number of runs, run lengths and sides = same long/short counts and exposure days, uniform starts; the same seed for every cell of a replicate), run only for families that pass the pre-screen (gates a, c and d on the real OOS series; families that fail it still count in F with rank 0). Because the null keeps the run lengths and sides, long-biased books face their own drift (e.g. N7-TREND-GC: OOS Sharpe 1.60 against a null mean of 1.79: rank 0.14), and the nulls are negative-mean for high-turnover books (costs).

## Counts per group (main batch)
| group | families | cells scored | pre-screen survivors (a,c,d) | gate b passes | gates a-d passes | chance at 2% / 5% per family | best-of-F >= 0.95 |
|---|---|---|---|---|---|---|---|
| N3 | 83 | 7,667 | 7 | 5 | 5 | 1.7 / 4.2 | 0 |
| N7 | 130 | 12,488 | 8 | 4 | 4 | 2.6 / 6.5 | 0 |
| N8 | 51 | 9,130 | 3 | 3 | 3 | 1.0 / 2.6 | 0 |
| total | 264 | 29,285 | 18 | 12 | 12 | 5.3 / 13.2 | 0 |

Cells: grammar-built 30,033 (after in-family direction dedupe) -> scored 29,285 (cells with < 20 active days in the window, non-finite volmatch and cells whose series hash is already in HASH50K were dropped). Enumerated per family kind and the grammar are in PREREG_N3N7N8.md.

## Gate a-d passing families (main batch), sorted by OOS Sharpe
| family | group | cells | OOS Sharpe | boot lo | halves Sharpe | null rank (null mean) | pair corr | plateau ratio / class | best-of-F F_eff / nominal / F=30 | N9 |
|---|---|---|---|---|---|---|---|---|---|---|
| N7-RSI-ES | N7 | 45 | 1.52 | 0.16 | 1.61 / 1.78 | 0.995 (+0.18) | +0.07 | 0.98 flat (~97%) | 0.007 / 0.000 / 0.778 | NT8-native (daily bars; orders at the cl |
| N8-DISP-6B | N8 | 72 | 1.30 | 0.04 | 1.33 / 1.30 | 1.000 (-0.47) | +0.13 | 0.43 peaked (~80%) | 0.000 / 0.000 / 0.571 | NEEDS FEED (26 daily series for the disp |
| N3-ROLL-ZB | N3 | 72 | 1.27 | 0.11 | 1.50 / 1.02 | 1.000 (-0.32) | +0.04 | 0.50 peaked (~80%) | 0.000 / 0.000 / 0.536 | NT8-native (needs a roll calendar; the v |
| N3-ROLL-ZN | N3 | 72 | 1.16 | 0.06 | 1.60 / 0.68 | 1.000 (-0.28) | +0.00 | 0.50 peaked (~80%) | 0.000 / 0.000 / 0.389 | NT8-native (needs a roll calendar; the v |
| N3-ROLL-ZF | N3 | 72 | 1.13 | 0.05 | 1.74 / 0.44 | 0.995 (-0.29) | -0.01 | 0.50 peaked (~80%) | 0.000 / 0.000 / 0.355 | NT8-native (needs a roll calendar; the v |
| N7-MRZ-HG | N7 | 140 | 1.07 | 0.04 | 0.43 / 1.87 | 0.995 (+0.06) | +0.16 | 0.92 flat (~97%) | 0.000 / 0.000 / 0.278 | NT8-native (daily bars; orders at the cl |
| N3-CARRY-ES | N3 | 80 | 1.07 | 0.04 | 0.24 / 1.78 | 0.965 (+0.07) | -0.01 | 0.54 peaked (~80%) | 0.000 / 0.000 / 0.272 | NEEDS FEED (second-month contract series |
| N3-ROLL-6J | N3 | 72 | 1.02 | 0.03 | 1.38 / 0.65 | 0.965 (-0.11) | +0.21 | 0.50 peaked (~80%) | 0.000 / 0.000 / 0.221 | NT8-native (needs a roll calendar; the v |
| N7-MRZ-YM | N7 | 143 | 1.00 | 0.05 | 0.68 / 2.12 | 0.985 (+0.19) | +0.06 | 0.94 flat (~97%) | 0.000 / 0.000 / 0.197 | NT8-native (daily bars; orders at the cl |
| N7-RSI-HE | N7 | 45 | 0.97 | 0.04 | 1.69 / 0.35 | 1.000 (-0.63) | -0.17 | 0.98 peaked (~80%) | 0.000 / 0.000 / 0.168 | NT8-native (daily bars; orders at the cl |
| N8-CORR-6B | N8 | 108 | 0.95 | 0.00 | 1.41 / 0.56 | 0.995 (-0.51) | +0.08 | 0.49 peaked (~80%) | 0.000 / 0.000 / 0.151 | NT8-native (ES and ZN daily series as ex |
| N8-RISK-6A | N8 | 288 | 0.85 | 0.01 | 0.62 / 1.37 | 1.000 (-0.21) | -0.09 | 0.49 peaked (~80%) | 0.000 / 0.000 / 0.073 | NT8-native (needs ES/ZN/GC/6x daily seri |

Reading: (i) the three bond roll-window families (ZB, ZN, ZF) and 6J are ONE bet (short- and medium-duration Treasuries move together around their quarterly rolls) and their windows are a causal calendar proxy; the cells are 'long/short from a days before to b days after the predicted roll'; their plateau ratio of 0.50 means the neighbouring cells do not retain the effect uniformly. (ii) N7-RSI-ES, N7-MRZ-YM and N7-MRZ-HG are short-horizon mean-reversion fades (equity indices and copper), the family of effects the pair does not trade; RSI-ES has the best plateau (0.98) and a drift-matched null mean of 0.18. (iii) N3-CARRY-ES and N8-DISP-6B / N8-CORR-6B / N8-RISK-6A are single-instrument passes with weak plateau (0.43-0.54) or a negative null mean from costs, and fail the best-of-F bar by a wide margin. None has pair correlation above 0.22 (an independent axis, but also not significant after multiplicity).

## Gate a-d near misses and drift-explained families (main batch, pre-screen survivors that failed the null)
| family | OOS Sharpe | null rank (null mean) | reading |
|---|---|---|---|
| N3-CARRY-GC | 1.61 | 0.880 (+1.14) | just below the 0.95 null bar |
| N7-TREND-GC | 1.60 | 0.135 (+1.79) | drift-explained: the matched random-entry null earns as much |
| N7-BRK-GC | 1.32 | 0.005 (+1.88) | drift-explained: the matched random-entry null earns as much |
| N7-MRZ-ES | 1.05 | 0.930 (+0.40) | just below the 0.95 null bar |
| N7-RSI-NQ | 0.96 | 0.945 (+0.15) | just below the 0.95 null bar |
| N3-VX-GC | 0.94 | 0.225 (+1.23) | drift-explained: the matched random-entry null earns as much |

## K1 refill batch (neighbouring cells of each passer; reported separately, never used to select a family)
| family | cells | OOS Sharpe | boot lo | halves | null rank (null mean) | gates a-d |
|---|---|---|---|---|---|---|
| N7-RSI-ES-K1 | 190 | 1.34 | 0.12 | 1.36 / 1.94 | 0.995 (+0.27) | PASS |
| N3-ROLL-6J-K1 | 128 | 1.34 | 0.11 | 1.74 / 0.97 | 0.970 (+0.03) | PASS |
| N7-RSI-HE-K1 | 186 | 1.16 | 0.06 | 1.92 / 0.48 | 1.000 (-0.76) | PASS |
| N8-RISK-6A-K1 | 256 | 1.14 | 0.03 | 1.14 / 1.18 | 1.000 (-0.67) | PASS |
| N3-ROLL-ZB-K1 | 128 | 1.09 | 0.09 | 1.41 / 0.75 | 0.985 (-0.26) | PASS |
| N7-MRZ-HG-K1 | 296 | 1.05 | 0.04 | 0.53 / 1.84 | 0.985 (+0.12) | PASS |
| N3-ROLL-ZN-K1 | 128 | 1.04 | 0.05 | 1.63 / 0.44 | 0.990 (-0.34) | PASS |
| N3-ROLL-ZF-K1 | 128 | 1.03 | 0.03 | 1.77 / 0.29 | 0.985 (-0.36) | PASS |
| N3-CARRY-ES-K1 | 38 | 1.00 | 0.01 | 0.39 / 1.56 | 0.950 (+0.29) | PASS |
| N7-MRZ-YM-K1 | 298 | 0.98 | 0.05 | 0.67 / 1.98 | 1.000 (+0.22) | PASS |
| N8-DISP-6B-K1 | 329 | 0.77 | -0.01 | 0.51 / 1.02 | 0.000 (+nan) | fail |
| N8-CORR-6B-K1 | 324 | -0.03 | -0.19 | -0.69 / 0.74 | 0.000 (+nan) | fail |

## Chance expectation vs observed (a778's master PREREG section 5 uses 5% per family at planned counts)
- Main batch: 12 passes (N3 5, N7 4, N8 3) in 264 families = 4.5%, against 2% (POWER2 false-positive rate for zero-edge/matched-null families: 5.3 expected) and 5% (the master prereg bound: 13.2 expected): inside the chance band. The gate-F-style multiplicity bar (best-of-F >= 0.95) is passed by none. Groups at or below their chance expectation are no evidence (master section 5).
- The families within an instrument share the return series and the passers cluster (Treasury rolls: 3 of 5 N3 passes), so the number of independent passes is smaller than 12.
- Every gate a-d passer is available to a778's PAPER-ALL feed (frozen weights, bands, kill rule are built there). Zero-capital artifacts only; no live change; no purchases.

## N9 (Josh-stack) classes of what was built
- N7 (trend, breakout, mean reversion, RSI, seasonal on the outright's own daily bars): NT8-native (daily series of the instrument; close fills approximated by a last-minute market order).
- N3-ROLL: NT8-native with a roll calendar. N3-CARRY / N3-SPREAD: NEEDS FEED (second-month contract as an extra data series; the calendar spread as a Globex spread instrument). N3-VX: class 3 (CFE VX futures are not offered through Rithmic; needs a CBOE/IBKR feed for the slope) - conditioner only.
- N8-RISK / N8-CORR: NT8-native with extra daily series (ES, ZN, GC, FX futures); N8-DISP: NEEDS FEED (26 daily series computed outside NT8).

Code: code/census/night_ins/ap_n_data.py, ap_n_eng.py, ap_n_fam.py, ap_n_run.py, ap_n_rep.py. Outputs: outputs/methods2/fam/N3-*, N7-*, N8-* (matrices), FAMILY_REGISTRY.csv / FAMILY_RESULTS.csv rows, outputs/ideas50k/N3N7N8_progress_*.pkl, PREREG_N3N7N8.md (also appended to PREREG_IDEAS50K.md), FAMILY_LIST.csv rows, HASH50K.csv series hashes.

DONE N3N7N8
