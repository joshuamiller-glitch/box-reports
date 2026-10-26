# REPORT GC FADE v2 - combined GC report: B7 GC cell + L93 neighbourhood ensemble, with the replication battery pre-registered up front

**Verdict: LEAD stays (strong, mechanism not replicated); FOUND 0.** The pre-registered battery (PREREG_AUTOPILOT.md, 'GC FADE v2', written before any v2 run) fails its cross-section tests: the effect exists only in the 08:00-15:30 ET day-session split of gold (overnight and all-hours splits lose, COMEX-RTH-only fails H2), none of five other commodities replicates it (PL, HO, RB, NG, ZC; SI and HG failed earlier), the alternating-month test passes for the single cells but not the 108-cell ensemble (odd-month half 34% of the uplift), and the 2013-22 walk shows a regime effect: net Sharpe is positive in only 6 of 10 older years and the gain is concentrated in 2025-26 (net Sharpe 2.4 and 2.1 for the centre cell) against 0.4-0.5 in 2023-24. The neighbourhood is NOT counted as independent evidence (the centre cell's clean/H1/H2 were read in B7). R5 (newest weeks) cannot run until the data extension lands.

**Correction of an earlier number.** REPORT_B7 and REPORT_L93 (and the CANDIDATES line) said 'worst single trade -$19.6k at 19 contracts'. That figure is the worst single trade of ONE contract. At the 20%-share size (3.9 GC contracts for the centre cell) the worst single trade is -$76k with no stop and -$36k with the 0.5 x ADR20 catastrophic stop. Reports are corrected.

Fill model: next 1-minute open after the 5-minute bar close, 1 tick adverse per side (GC tick $10), stop-market at the stop with 1 tick slippage, $4.36 per contract round trip; baseline pair B.Cfg(wk_floor=8, wk_loss_pb=None).

## R1. GC 2013-2022 walk with cost decomposition (gross = no cost; net = fixed cost; price-scaled = per-trade cost x raw entry price / median clean raw price). $ per trade at 1 contract.
| object | 2013-22 weekly Sharpe gross / net / price-scaled | clean gross / net |
|---|---|---|
| O1 | 0.58 / -0.11 / 0.16 | 1.88 / 1.45 |
| O2 | 0.50 / 0.05 / 0.23 | 1.89 / 1.59 |
| O3 | 0.68 / 0.14 / 0.36 | 1.63 / 1.30 |

By year:
| object | year | trades | gross $/trade | net $/trade | price-scaled net $/trade | Sharpe gross | net | price-scaled |
|---|---|---|---|---|---|---|---|---|
| O1 ensemble108 | 2013 | 29995 | 87.4 | 63.1 | 73.6 | 2.05 | 1.48 | 1.73 |
| O1 ensemble108 | 2014 | 33161 | -7.7 | -32.1 | -20.3 | -0.18 | -1.21 | -0.72 |
| O1 ensemble108 | 2015 | 33293 | -21.6 | -46.0 | -33.1 | -0.65 | -1.63 | -1.11 |
| O1 ensemble108 | 2016 | 34522 | 41.4 | 17.0 | 28.9 | 1.32 | 0.49 | 0.90 |
| O1 ensemble108 | 2017 | 33940 | 19.0 | -5.4 | 6.5 | 0.93 | -0.32 | 0.29 |
| O1 ensemble108 | 2018 | 33701 | 4.5 | -19.9 | -8.2 | 0.19 | -0.94 | -0.39 |
| O1 ensemble108 | 2019 | 34579 | 26.8 | 2.4 | 12.9 | 1.05 | 0.09 | 0.50 |
| O1 ensemble108 | 2020 | 33597 | -1.9 | -26.2 | -19.5 | -0.02 | -0.48 | -0.36 |
| O1 ensemble108 | 2021 | 34045 | -3.9 | -28.2 | -21.8 | -0.03 | -0.60 | -0.45 |
| O1 ensemble108 | 2022 | 34599 | 66.9 | 42.5 | 48.9 | 1.43 | 0.90 | 1.04 |
| O1 ensemble108 | 2023 | 34743 | 8.4 | -15.9 | -11.0 | 0.26 | -0.37 | -0.24 |
| O1 ensemble108 | 2024 | 34953 | 34.7 | 10.3 | 10.8 | 0.78 | 0.30 | 0.31 |
| O1 ensemble108 | 2025 | 34065 | 279.2 | 254.8 | 244.7 | 2.59 | 2.37 | 2.27 |
| O1 ensemble108 | 2026 | 27027 | 341.6 | 317.2 | 296.3 | 1.95 | 1.80 | 1.68 |
| O2 centre no stop | 2013 | 252 | 88.6 | 64.3 | 74.8 | 1.34 | 0.97 | 1.13 |
| O2 centre no stop | 2014 | 276 | -27.5 | -51.8 | -40.1 | -0.73 | -1.38 | -1.07 |
| O2 centre no stop | 2015 | 275 | -46.4 | -70.7 | -57.9 | -1.22 | -1.86 | -1.52 |
| O2 centre no stop | 2016 | 281 | 68.2 | 43.8 | 55.7 | 1.45 | 0.93 | 1.18 |
| O2 centre no stop | 2017 | 277 | 23.2 | -1.2 | 10.7 | 0.89 | -0.05 | 0.41 |
| O2 centre no stop | 2018 | 275 | 9.6 | -14.7 | -3.0 | 0.30 | -0.46 | -0.09 |
| O2 centre no stop | 2019 | 282 | 63.0 | 38.7 | 49.1 | 1.52 | 0.93 | 1.18 |
| O2 centre no stop | 2020 | 280 | -27.6 | -52.0 | -45.3 | -0.36 | -0.68 | -0.59 |
| O2 centre no stop | 2021 | 269 | 20.3 | -4.1 | 2.4 | 0.32 | -0.06 | 0.04 |
| O2 centre no stop | 2022 | 281 | 79.5 | 55.2 | 61.6 | 1.12 | 0.78 | 0.87 |
| O2 centre no stop | 2023 | 277 | 51.6 | 27.3 | 32.2 | 0.85 | 0.45 | 0.53 |
| O2 centre no stop | 2024 | 287 | 55.1 | 30.7 | 31.2 | 0.74 | 0.41 | 0.42 |
| O2 centre no stop | 2025 | 281 | 415.7 | 391.3 | 381.2 | 2.57 | 2.42 | 2.36 |
| O2 centre no stop | 2026 | 226 | 523.2 | 498.8 | 477.9 | 2.17 | 2.07 | 1.99 |
| O3 centre stop0.5 | 2013 | 267 | 118.1 | 93.8 | 104.3 | 2.03 | 1.61 | 1.79 |
| O3 centre stop0.5 | 2014 | 294 | -26.7 | -51.0 | -39.2 | -0.85 | -1.62 | -1.25 |
| O3 centre stop0.5 | 2015 | 293 | -36.9 | -61.3 | -48.4 | -1.08 | -1.79 | -1.42 |
| O3 centre stop0.5 | 2016 | 300 | 60.8 | 36.4 | 48.3 | 1.47 | 0.88 | 1.17 |
| O3 centre stop0.5 | 2017 | 296 | 11.9 | -12.4 | -0.6 | 0.42 | -0.44 | -0.02 |
| O3 centre stop0.5 | 2018 | 296 | -5.5 | -29.9 | -18.1 | -0.18 | -0.96 | -0.59 |
| O3 centre stop0.5 | 2019 | 297 | 54.3 | 29.9 | 40.4 | 1.59 | 0.87 | 1.18 |
| O3 centre stop0.5 | 2020 | 304 | -24.7 | -49.1 | -42.4 | -0.42 | -0.83 | -0.72 |
| O3 centre stop0.5 | 2021 | 299 | 34.7 | 10.3 | 16.8 | 0.65 | 0.19 | 0.31 |
| O3 centre stop0.5 | 2022 | 298 | 94.2 | 69.8 | 76.2 | 1.62 | 1.20 | 1.31 |
| O3 centre stop0.5 | 2023 | 309 | 61.8 | 37.5 | 42.4 | 1.26 | 0.76 | 0.86 |
| O3 centre stop0.5 | 2024 | 311 | 21.4 | -3.0 | -2.5 | 0.35 | -0.05 | -0.04 |
| O3 centre stop0.5 | 2025 | 296 | 422.7 | 398.4 | 388.2 | 2.97 | 2.80 | 2.73 |
| O3 centre stop0.5 | 2026 | 238 | 520.2 | 495.9 | 474.9 | 2.31 | 2.20 | 2.11 |

ERA FLAG: O2 and O3 'positive pre-2023' (net 2013-22 +0.05 and +0.14), O1 'gross-positive, cost-negative pre-2023' (net -0.11, price-scaled +0.16). The edge is regime-dependent: positive net years 2013, 2016, 2019, 2022 (O2), negative 2014-15, 2017-18, 2020, 2021; then +0.4, +0.4, +2.4, +2.1 in 2023-26.

## R2. Sizing, micro contracts, tail
| object | contracts per signal slot at 100% share | max simultaneous (sum) at 100% | at 20% share: per slot / max sum | MGC per slot at 20% | worst single trade $ at 20% | worst week clean $ at 100% | worst week pair window $ at 100% |
|---|---|---|---|---|---|---|---|
| O1 | 0.23 | 25.2 | 0.05 / 5.0 | 0.5 | -1,110 | -128,846 | -332,428 |
| O2 | 19.47 | 19.5 | 3.89 / 3.9 | 38.9 | -76,482 | -120,704 | -466,239 |
| O3 | 20.18 | 20.2 | 4.04 / 4.0 | 40.4 | -36,134 | -123,809 | -378,101 |

Reading: 20% share = 3.9 GC contracts for the single centre cell (4.0 with the 0.5 ADR stop), equivalent to 39-40 MGC (10 oz each; MGC costs the same per ounce but the commission assumption of $1.40 per MGC round trip is unverified, so 39 MGC would add about $55 per signal against $17 for 4 GC); for the ensemble the exposure is spread over 108 slots (max about 5 GC-equivalents if every slot held at once). The worst-week numbers are at 100% share; at 20% multiply by 0.2. Margin (unverified general knowledge): GC roughly $10-12k per contract initial (day-trade margin is lower), MGC roughly one tenth; 4 contracts is about $45k of margin on a $700k account.

## R3. Other markets and session splits (ensemble recipe, vol-matched, additive 20%)
| GC session split | cells | standalone Sharpe clean / H1 / H2 | uplift@20% clean / H1 / H2 | all-in | boot lo | 2x-slip all-in | H0 |
|---|---|---|---|---|---|---|---|
| ALL | 432 | -0.02 / 0.69 / -1.67 | -0.06 / 0.19 / -0.60 | -0.15 | -0.43 | -0.30 | 0.38 |
| all | 108 | -1.13 / -1.53 / -1.80 | -0.24 / -0.93 / -0.99 | -0.50 | -0.83 | -0.68 | 1.75 |
| day | 108 | 1.45 / 2.19 / 1.53 | 0.20 / 0.95 / 0.83 | 0.44 | 0.15 | 0.38 | 0.29 |
| ovn | 108 | -1.12 / -2.99 / -3.83 | -0.23 / -2.01 / -1.81 | -0.86 | -1.23 | -0.98 | -0.19 |
| rth | 108 | 0.54 / 1.75 / -0.40 | 0.02 / 0.95 / -0.16 | 0.15 | -0.18 | 0.09 | -0.16 |

| instrument | standalone Sharpe clean / H1 / H2 (ensemble) | uplift@20% clean / H1 / H2 | all-in |
|---|---|---|---|
| PL | -0.73 / 0.97 / -0.94 | -0.19 / 0.12 / -0.44 | -0.18 |
| HO | -0.80 / 1.30 / -0.96 | -0.22 / 0.12 / -0.58 | -0.26 |
| RB | -0.14 / 1.76 / 1.05 | -0.11 / 0.18 / 0.27 | 0.00 |
| NG | -0.95 / -1.61 / -0.59 | -0.22 / -0.72 / -0.08 | -0.26 |
| ZC | -3.50 / -3.57 / -0.72 | -0.72 / -0.60 / -0.13 | -0.58 |
| SI (earlier) | 0.51 all-in | -0.10 / -0.10 / -0.34 | -0.07 |
| HG (earlier) | -0.39 all-in | -0.27 / -0.02 / 0.19 | -0.12 |

Pass rule: uplift >= +0.10 on H1 and H2 with clean positive for at least 2 of the 5 other instruments, and positive all-in uplift in at least 3 of the 4 GC session splits. Result: 0 of 5 other instruments (RB has positive H1/H2 uplift but clean -0.11, 0.00 all-in) and 2 of 4 GC session splits (day +0.44, COMEX-RTH-only +0.15; overnight -0.86, all-hours -0.50): FAIL.

## R4. Alternating months (2023-08..2026-10; all-in uplift at 20% on odd-month days only and even-month days only)
| object | full-window uplift@20% | odd months | even months |
|---|---|---|---|
| O1 | 0.44 | 0.15 | 0.68 |
| O2 | 0.54 | 0.29 | 0.71 |
| O3 | 0.52 | 0.26 | 0.73 |

Pass rule: both halves positive and each >= 50% of the full uplift: O1 FAILS (odd 0.15 vs 0.22 needed), O2 passes (0.29 vs 0.27), O3 passes narrowly (0.26 vs 0.26). The imbalance is large in every object (even months carry 2-5x the odd-month uplift). Cell-level split (108 cells): the 10 cells best on odd months have a mean even-month uplift of 0.54 against 0.51 for all cells; the 10 best on even months have a mean odd-month uplift of 0.09 against 0.07 for all cells; the odd/even cell uplifts are uncorrelated (rho = 0.00). Both directions are positive and there is no peak-chasing (the picked cells do no better than the average cell), so the effect belongs to the whole neighbourhood, but the odd-month uplift is small (about 0.07-0.09 per cell).

## R5. Newest weeks after the data extension
Frozen definitions: O1 = the 108-cell equal-risk ensemble, O2 = 5-min ST(14,2.0) fade hold 240 no stop, O3 = O2 with the 0.5 x ADR20 stop, day session 08:00-15:30 ET entries, full holds only. The series on disk end 2026-10-14 (no new weeks yet); the read happens once the weekly extension lands, with a sign test on >= 8 new weeks; no verdict is drawn from it before that.

## R6. Stop model and stress
| catastrophic stop (x ADR20) | uplift@20% all-in at 1 tick | at 3 ticks (stop-market stress, applied to entry and exit) | standalone all-in Sharpe 1 tick / 3 ticks |
|---|---|---|---|
| 0.5 | 0.41 | 0.27 | 1.47 / 1.07 |
| 0.75 | 0.45 | 0.31 | 1.50 / 1.12 |
| 1.0 | 0.45 | 0.32 | 1.47 / 1.10 |

The 0.5 ADR catastrophic stop costs nothing in the pair window (all-in uplift 0.41 vs 0.42 no stop) and survives 3-tick stop-market slippage (uplift 0.27-0.32). Worst single trade falls from -$76k to -$36k at the 20%-share size.

## Mechanism and dependence on current structure
Five-minute Supertrend flips in gold are mostly noise that mean-reverts over three to five hours during the COMEX day session, and the faded position collects the reversion. It is not seen overnight, outside the day session, or in other metals/commodities, and its net edge in 2013-22 is small and unstable; in 2025-26 gold's volatility and price level made the same gross edge several times larger (gross per trade $415-523 against $20-90 earlier). It plausibly depends on current structure and on one market's recent regime.

## Executability
NT8 strategy on GC (CME via Rithmic expected): 5-minute bars, Supertrend(14, 2.0) flip, enter OPPOSITE the flip at the next bar open, exit 240 minutes later (or 16:55 flat; skip entries without a full hold before 16:55), optional stop-market 0.5 x 20-day mean daily range from entry, entries 08:00-15:30 ET only, one position at a time; or the 108-cell ensemble as a multi-leg strategy. Size 3.9-4 GC (39-40 MGC) at 20% of pair risk.

Code ap_g93.py, ap_g93_v2.py, ap_l_cure.py (code/census/night_ins); data outputs/autopilot/l/g93, l93, g93v2.

DONE GC_FADE_V2
