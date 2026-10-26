# REPORT REGIME - the 'intraday extension-fade' factor, its break and its drivers (PREREG_REGIME.md, registered before any factor was computed)

**Verdict: the pattern is real as a pre/post contrast but NOT identified as a structural break by the pre-registered tests, and no on-disk driver survives the drift-neutral null.** A 20-rule fade factor (8 frozen selected cells + 12 neutral draws; ES, NQ, RTY, YM) has net weekly-annualised Sharpe -1.74 in 2013-22 and +0.28 in 2023-26; the gross factor goes from -0.48 to +1.23, so about 1.7 of the 2.0 Sharpe units of improvement is gross edge and about 0.3 is the falling cost drag (price-scaled cost version: -1.18 -> +0.23). The break is significant against the sign-randomised null ONLY for the 8 frozen rules (supF p = 0.03, Chow 2023-01 p = 0.02) - which were selected on 2023-25 data and therefore carry the break by construction - and NOT for the 12 neutral rules (supF p = 0.58) or for all 20 together (supF p = 0.16, best date 2022-07, Chow 2023-01 p = 0.17). So the data support 'the selected fades work after 2023' (already known) but not 'a common regime change turned all index fades on'. Forward implication: a regime-watch series is provided; the observable that would flag the end of the regime is a rolling-63-day gross factor Sharpe below -1.10 (5th percentile of its 2023-26 distribution) for two consecutive weeks.

## 1. Factor construction (frozen; see PREREG_REGIME.md for the 20 components and the seeded neutral draw)
Equal-weight average of 20 normalised component P&L series per index (each divided by its own full-sample daily SD), net of 1 tick/side + $4.36; RTY from 2017-07. Three versions: net (fixed cost), gross (no cost) and price-scaled cost (per-trade cost x raw entry price / median clean raw price). 80 component series were re-run for the gross and price-scaled versions (ap_regime_gross.py); their net equals the stored runs to the cent except for three new days after the extension.
Note on the eight named rules: BI8 (ES long after a >= 1.5 ATR20 range day) is not a fade (REPORT_BI8B withdrew it as long beta) and BJ2/BM1 are late-day fades of the day's move; all eight are kept as instructed, and the 7-rule sensitivity (no BI8) gives the same conclusion (supF p 0.21, Chow 2023-01 p 0.22).

## 2. Factor Sharpe by version and index
| version | index | Sharpe 2013-19 | 2020-22 | 2013-22 | 2023-26 |
|---|---|---|---|---|---|
| net(fixed cost) | ES | -2.66 | -2.05 | -2.12 | -0.17 |
| net(fixed cost) | NQ | -1.53 | -1.59 | -1.32 | 0.69 |
| net(fixed cost) | RTY | -2.14 | -0.42 | -0.96 | 0.45 |
| net(fixed cost) | YM | -1.66 | -1.44 | -1.44 | -0.03 |
| net(fixed cost) | ALL | -2.21 | -1.62 | -1.74 | 0.28 |
| gross | ES | -0.26 | -1.02 | -0.59 | 0.94 |
| gross | NQ | -0.43 | -1.24 | -0.77 | 0.99 |
| gross | RTY | -0.68 | 0.52 | 0.12 | 1.53 |
| gross | YM | -0.21 | -0.74 | -0.44 | 0.75 |
| gross | ALL | -0.30 | -0.75 | -0.48 | 1.23 |
| price-scaled cost | ES | -1.26 | -1.75 | -1.37 | -0.22 |
| price-scaled cost | NQ | -0.73 | -1.47 | -0.98 | 0.67 |
| price-scaled cost | RTY | -1.78 | -0.33 | -0.79 | 0.37 |
| price-scaled cost | YM | -0.94 | -1.29 | -1.03 | -0.07 |
| price-scaled cost | ALL | -1.16 | -1.42 | -1.18 | 0.23 |

By calendar year, ALL factor:
| year | net (fixed cost) | gross | price-scaled cost |
|---|---|---|---|
| 2013 | -4.02 | 0.01 | -1.24 |
| 2014 | -3.03 | -0.12 | -1.15 |
| 2015 | -1.84 | 0.25 | -0.53 |
| 2016 | -1.68 | 1.23 | 0.11 |
| 2017 | -2.52 | 0.95 | -0.75 |
| 2018 | -2.60 | -1.46 | -2.13 |
| 2019 | -2.54 | -0.69 | -1.82 |
| 2020 | -1.59 | -0.75 | -1.29 |
| 2021 | -2.29 | -1.11 | -2.15 |
| 2022 | -1.32 | -0.57 | -1.17 |
| 2023 | -1.09 | 0.39 | -0.84 |
| 2024 | 0.16 | 1.23 | 0.15 |
| 2025 | 0.77 | 1.48 | 0.69 |
| 2026 | 0.73 | 1.64 | 0.43 |

Reading: the net factor loses in every year 2013-2023 and is positive from 2024. The GROSS factor is the cleaner picture: about zero in 2013-15, positive in 2016-17, NEGATIVE in 2018-2022 (-0.57 to -1.46: fades lose in the persistent-trend years), positive from 2023 (+0.39, +1.23, +1.48, +1.64). Components x indices with a positive gross Sharpe: 33 of 80 before 2023, 57 of 80 after. Costs take 3-4 Sharpe units off the factor in 2013-17 (gross about 0 to +1.2, net -1.7 to -4.0) but only 0.7-1.5 units in 2022-26 (ranges and price levels rose against a fixed tick and commission); the net factor becomes positive only from 2024, when the gross Sharpe exceeds about +1.2. Monthly and rolling-quarter Sharpe series: regime/factor_month_sharpe.csv, factor_roll63_sharpe.csv, factor_daily.csv.

## 3. Structural-break tests (weekly factor sums; null: 5,000 sign-randomised constructions)
Net factor:
| factor | weights | supF (date), p vs sign-randomised null | CUSUM p | Chow t 2020-03 (p) | 2022-01 (p) | 2022-10 (p) | 2023-01 (p) | supF p, circular-shift null |
|---|---|---|---|---|---|---|---|---|
| ES | all20 | 12.0 (20220701), p=0.256 | 0.220 | 0.20 (0.889) | 1.41 (0.389) | 2.51 (0.177) | 2.25 (0.227) | 0.538 |
| ES | frozen8 | 24.0 (20230929), p=0.031 | 0.040 | 1.96 (0.169) | 2.74 (0.051) | 3.47 (0.036) | 3.42 (0.058) | 0.000 |
| ES | neutral12 | 4.7 (20220701), p=0.670 | 0.665 | -1.02 (0.520) | 0.26 (0.885) | 1.42 (0.487) | 1.06 (0.587) | 0.953 |
| ES | no_BI8 | 10.9 (20220701), p=0.305 | 0.277 | 0.02 (0.987) | 1.26 (0.473) | 2.35 (0.227) | 2.06 (0.290) | 0.556 |
| NQ | all20 | 15.3 (20220701), p=0.142 | 0.097 | 0.59 (0.558) | 1.88 (0.130) | 2.62 (0.077) | 2.59 (0.104) | 0.189 |
| NQ | frozen8 | 34.4 (20240322), p=0.034 | 0.024 | 2.10 (0.071) | 3.33 (0.018) | 3.65 (0.018) | 3.75 (0.034) | 0.002 |
| NQ | neutral12 | 6.0 (20220617), p=0.449 | 0.395 | -0.56 (0.505) | 0.60 (0.609) | 1.49 (0.316) | 1.36 (0.353) | 0.756 |
| NQ | no_BI8 | 13.9 (20240126), p=0.165 | 0.124 | 0.48 (0.638) | 1.79 (0.160) | 2.49 (0.096) | 2.47 (0.119) | 0.264 |
| RTY | all20 | 8.6 (20240223), p=0.199 | 0.218 | 2.54 (0.074) | 1.53 (0.246) | 2.52 (0.143) | 2.18 (0.175) | 0.073 |
| RTY | frozen8 | 20.6 (20240112), p=0.024 | 0.024 | 2.74 (0.104) | 3.06 (0.017) | 4.38 (0.024) | 4.00 (0.024) | 0.043 |
| RTY | neutral12 | 3.5 (20191108), p=0.597 | 0.656 | 1.82 (0.179) | 0.10 (0.958) | 0.66 (0.650) | 0.41 (0.741) | 0.198 |
| RTY | no_BI8 | 6.8 (20240223), p=0.281 | 0.293 | 2.39 (0.090) | 1.38 (0.304) | 2.22 (0.203) | 1.82 (0.246) | 0.108 |
| YM | all20 | 7.8 (20220617), p=0.315 | 0.314 | 0.32 (0.810) | 1.60 (0.292) | 1.94 (0.261) | 1.78 (0.279) | 0.526 |
| YM | frozen8 | 12.8 (20220701), p=0.092 | 0.087 | 1.46 (0.332) | 2.73 (0.055) | 2.68 (0.065) | 2.52 (0.071) | 0.038 |
| YM | neutral12 | 3.9 (20220617), p=0.658 | 0.666 | -0.52 (0.694) | 0.55 (0.723) | 1.12 (0.519) | 0.96 (0.564) | 0.979 |
| YM | no_BI8 | 7.7 (20220617), p=0.319 | 0.326 | 0.22 (0.882) | 1.55 (0.320) | 1.88 (0.279) | 1.70 (0.301) | 0.503 |
| ALL | all20 | 15.6 (20220701), p=0.163 | 0.141 | 0.91 (0.532) | 1.92 (0.247) | 2.84 (0.146) | 2.66 (0.169) | 0.194 |
| ALL | frozen8 | 31.5 (20240105), p=0.031 | 0.022 | 2.52 (0.134) | 3.62 (0.006) | 4.25 (0.014) | 4.16 (0.022) | 0.000 |
| ALL | neutral12 | 5.4 (20220617), p=0.582 | 0.566 | -0.36 (0.798) | 0.46 (0.791) | 1.45 (0.496) | 1.19 (0.553) | 0.760 |
| ALL | no_BI8 | 14.3 (20220701), p=0.210 | 0.194 | 0.75 (0.621) | 1.80 (0.310) | 2.67 (0.194) | 2.47 (0.222) | 0.229 |

Gross and price-scaled-cost factors (ALL):
| version | weights | supF (date), p | CUSUM p | Chow t 2023-01 (p) | 2022-10 (p) | 2022-01 (p) |
|---|---|---|---|---|---|---|
| gross | all20 | 17.8 (20220701), p=0.126 | 0.111 | 2.84 (0.138) | 3.03 (0.122) | 2.16 (0.190) |
| gross | frozen8 | 32.2 (20240105), p=0.026 | 0.009 | 4.20 (0.021) | 4.29 (0.016) | 3.69 (0.007) |
| gross | neutral12 | 7.2 (20220617), p=0.442 | 0.424 | 1.46 (0.450) | 1.71 (0.394) | 0.77 (0.642) |
| price-scaled | all20 | 9.0 (20220701), p=0.353 | 0.342 | 1.87 (0.306) | 2.07 (0.267) | 1.14 (0.490) |
| price-scaled | frozen8 | 24.3 (20240105), p=0.022 | 0.023 | 3.62 (0.023) | 3.72 (0.023) | 3.07 (0.016) |
| price-scaled | neutral12 | 6.2 (20171124), p=0.560 | 0.535 | 0.36 (0.858) | 0.62 (0.769) | -0.37 (0.837) |

Reading: (a) candidate dates: 2022-10 and 2023-01 give the largest Chow t (2.8 and 2.7 for all 20), but their p-values against the sign-randomised null are 0.15-0.17 (not significant); 2020-03 is never significant (the COVID date is not a break of this factor); (b) the supF-maximising date of the unselected sets is 2022-06/07; for the frozen 8 it is 2024-01 (the clean selection window starts 2023-08); (c) the circular-shift (drift-neutral) reference agrees: p = 0.19 for all 20, 0.00 for the frozen 8, 0.76 for the neutral 12; (d) leave-one-out (regime/leave_one_out.csv) does not rescue significance. The honest reading is that a post-2022 improvement exists in the average (t about 2.7) but is within what correlated random-sign constructions produce 15-20% of the time, and the strongly significant sub-factor is the selected one.

## 4. Candidate drivers (on-disk data; coverage stated; Bonferroni threshold 0.05/6 = 0.0083)
| driver | coverage (months) | break t at 2020-03 / 2022-01 / 2022-10 / 2023-01 | detrended corr with the ALL factor (p), lag 0 / lag 1 | first-difference corr (p), lag 0 / lag 1 | within 2023-26 corr (p) | factor mean, top vs bottom driver tercile | survives? |
|---|---|---|---|---|---|---|---|
| VIX_level | 201301..202610 (n=166) | 6.8 / 2.3 / 0.1 / -0.7 | -0.17 (0.061) / -0.15 (0.135) | 0.02 (0.771) / -0.01 (0.873) | 0.33 (0.026) | -0.72 vs -0.24 | no |
| VVIX_level | 201301..202610 (n=166) | 5.8 / 0.2 / -1.2 / -0.8 | -0.31 (0.000) / -0.27 (0.000) | -0.09 (0.231) / 0.02 (0.896) | 0.13 (0.435) | -0.79 vs -0.22 | no |
| VIX_changeSD | 201301..202610 (n=166) | 2.5 / -0.3 / -0.9 / -0.7 | -0.15 (0.070) / -0.11 (0.158) | -0.06 (0.521) / 0.04 (0.637) | 0.27 (0.024) | -0.80 vs -0.16 | no |
| first_hour_range_frac | 201301..202610 (n=166) | -1.0 / -1.2 / -0.3 / -0.8 | 0.10 (0.218) / 0.04 (0.715) | 0.04 (0.718) / -0.05 (0.630) | -0.33 (0.049) | -0.42 vs -0.58 | no |
| ES_realised_vol | 201301..202610 (n=166) | 4.9 / 3.1 / 1.5 / 0.9 | -0.12 (0.145) / -0.06 (0.388) | -0.03 (0.633) / 0.04 (0.607) | 0.41 (0.000) | -0.60 vs -0.21 | no |
| ES_volume_growth12m | 201401..202610 (n=154) | 0.3 / 0.2 / -1.2 / -1.7 | -0.18 (0.028) / 0.04 (0.588) | -0.21 (0.006) / 0.18 (0.058) | 0.10 (0.406) | -0.65 vs -0.28 | no |
| NDX_0DTE_share | 201901..202610 (n=94) | 13.4 / 13.3 / 17.8 / 17.9 | 0.18 (0.092) / 0.16 (0.129) | -0.00 (0.979) / 0.06 (0.629) | 0.10 (0.270) | 0.28 vs -1.10 | no |


Coverage: VIX (1990+) and VVIX (2006+) daily files, used 2013-2026; ES 1-minute series 2013-2026 (realised vol, volume, first-hour range); NDX option 0DTE volume share only 2019-01..2026-10 (94 months) from outputs/autopilot/opt/ndx_vol_daily.parquet (NDX only, no SPX/SPXW or OPRA definitions bought; SPXF/NDXF GEX tables exist but are not a 0DTE share).
Results: NO driver survives (a survivor needs p < 0.0083 on detrended levels AND first differences at both lags). The closest: VVIX (detrended correlation -0.31, p = 0.000 at lag 0 and -0.27 at lag 1: the factor is better in low vol-of-vol months) but its first-difference correlation is -0.09 (p = 0.23); ES 12-month volume growth (first-difference corr -0.22, p = 0.006 at lag 0, detrended p = 0.028); 0DTE share has an enormous 'break' (t 13-18, it ramps from 0.2 to 0.6) and an insignificant drift-neutral association (detrended corr 0.18, p = 0.09; difference corr 0.00): its link to the factor is a shared trend, not a relationship. Within 2023-26 (46 months) the net factor is positively related to ES realised volatility (corr 0.41, p = 0.000), VIX level (0.33, p = 0.026) and VIX change SD (0.28, p = 0.024) and negatively to the first-hour range fraction (-0.33, p = 0.049): consistent with a fixed-dollar cost being a smaller share of a larger range, not with a new mechanism. The first-hour fraction did not break at any candidate date (|t| < 1.2); ES realised volatility has t of 1.5 and 0.9 at 2022-10 and 2023-01 (a break only at 2020-03 and 2022-01); the VIX level, VVIX and VIX-change SD means are no different pre/post 2023 (17.9 vs 17.3, 97.0 vs 95.4, 1.51 vs 1.36).

## 5. Forward implication and regime watch
Break date: not identified (best estimate 2022-07 for all 20 rules, p = 0.16; 2024-01 for the selected 8). Driver: none identified. Regime-end observable, stated without a driver: ALL-factor rolling-63-day gross Sharpe below -1.10 (5th percentile of its 2023-26 distribution; median +0.93; last value +0.77 on 2026-10-16, net -0.42 with a net median of -0.29) for two consecutive weeks. Regime-watch series: `outputs/autopilot/forward/series/REGIME_live.csv` (+ `.meta.json`; ALL net, gross and price-scaled factor in sigma units with the two rolling Sharpes) written as a NEW file; refresh script `code/census/night_ins/refresh_regime.py`. The extension worker's registry files (ap_forward_score.py, PRED_EXTRA.json, FORWARD.md) were NOT edited; the row to add is: lead id REGIME, kind 'tracked factor (not a trade)', live REGIME_live.csv, tracked statistic = rolling_63 gross Sharpe, flag when below -1.10 twice in a row, expectation 'positive gross (median +0.93)'.

## 6. Insurance view (net factor as a sleeve on the pair, 2023-26 only; 2013-22 shown alongside; B.Cfg(wk_floor=8, wk_loss_pb=None))
| sleeve | additive 10% (clean/H1/H2) | 20% | 30% | 50% | worst-week change at 20% (%) | constant-risk 30%: net % / worst-week impr % / CVaR5 impr % | standalone Sharpe clean / H1 / H2 | wd corr |
|---|---|---|---|---|---|---|---|---|
| ALL | +0.10/-0.22/+0.21 | +0.18/-0.49/+0.37 | +0.25/-0.80/+0.48 | +0.33/-1.42/+0.54 | 19.7 | -22.1 / 0.4 / 9.3 | 0.79 / -1.61 / 1.14 | -0.18 |
| ES | +0.06/-0.22/+0.12 | +0.11/-0.48/+0.20 | +0.14/-0.79/+0.24 | +0.15/-1.41/+0.19 | 18.6 | -29.9 / -7.2 / 7.2 | 0.39 / -1.81 / 0.44 | -0.07 |
| NQ | +0.17/-0.12/+0.26 | +0.33/-0.33/+0.46 | +0.48/-0.61/+0.58 | +0.70/-1.23/+0.60 | 34.2 | -13.4 / -21.3 / 6.9 | 1.32 / -1.01 / 1.34 | -0.00 |
| RTY | +0.06/-0.11/+0.15 | +0.11/-0.25/+0.26 | +0.14/-0.42/+0.34 | +0.16/-0.80/+0.38 | 23.2 | -20.3 / -10.1 / 11.0 | 0.88 / -0.90 / 0.80 | -0.49 |
| YM | +0.03/-0.28/+0.14 | +0.05/-0.57/+0.26 | +0.05/-0.88/+0.34 | +0.01/-1.45/+0.42 | 17.2 | -29.0 / 0.6 / 8.3 | 0.14 / -1.81 / 1.32 | -0.08 |

Verdict: not insurance. At a 20% share the ALL sleeve adds +0.18 / -0.49 / +0.37 to the weekly Sharpe on clean / H1 / H2 (all-in 1.90 -> 2.03), the worst week gets 19.7% worse and CVaR5 worsens (about -$79k -> -$88k all-in); the constant-risk version at 30% costs 22% of net for a +0.4% worst-week change and +9% CVaR5. Per index: NQ is the only sleeve with positive uplift on two spans (+0.33 / -0.33 / +0.46 at 20%); the YM sleeve is flat.

| sleeve | 2013-22 weekly Sharpe at the same scale | cumulative 2013-22 $ at 20% share | cumulative 2023-26 $ at 20% share | worst day / worst week 2023-26 at 20% share | contracts per component slot at 20% (mean) / if all slots at once |
|---|---|---|---|---|---|
| ALL | -1.99 | $-1,162,947 | $104,550 | $-39,601 / $-43,296 | 0.38 / 30.7 |
| ES | -2.39 | $-1,345,172 | $-61,558 | $-40,198 / $-42,006 | 1.07 / 21.5 |
| NQ | -1.62 | $-745,421 | $290,866 | $-37,196 / $-50,284 | 0.67 / 13.4 |
| RTY | -0.78 | $-466,089 | $155,560 | $-32,396 / $-35,415 | 2.06 / 41.2 |
| YM | -1.49 | $-925,323 | $-11,770 | $-47,897 / $-46,110 | 1.41 / 28.2 |

Sized dollars (ALL sleeve, 20% share): the scale is $79.6k of sleeve per sigma-unit of the factor; mean 0.38 contracts per component slot per index (80 slots, up to 30.7 contracts if every slot were open at once, which does not happen: typical open exposure is a few contracts); worst day -$39.6k and worst week -$43.3k over 2023-26. The flat/negative period: at the same scale the sleeve would have lost about $1.16M over 2013-22 (weekly Sharpe -1.99) and made about $105k over 2023-26: the factor is a cost-dominated 2023-26 phenomenon, not a stable income source.

## 7. What is NOT identified
(i) A statistically significant common break date; (ii) any driver; (iii) a mechanism for the 2018-22 negative gross period (it coincides with the strongest trend years of the sample; the factor is short-trend by construction). The three-way summary is therefore: cost ratio (price level and range) explains a large part of the net improvement; gross edge turns from negative to positive around 2022-23; the evidence that this gross turn is common to the rules is only as strong as a 15-20% p-value, and the one significant aggregate is the selected subset.

## 8. Method notes and limits
Weekly sums use ISO weeks; supF uses 15% trimming; sign-randomisation null draws independent +/-1 signs per component (5,000); circular-shift reference 2,000 draws of the demeaned weekly factor; driver nulls use 5,000 circular shifts of the monthly driver. The factor scaling uses full-sample SD (a research diagnostic). Look-ahead: components are the already-run causal cells; drivers are monthly means contemporaneous to the factor month and lagged by one month (both reported). The 12 neutral cells were drawn before any P&L was read (ap_regime_draw.py, seed 20261018). No purchases. Files: outputs/autopilot/regime/ (factor_daily.csv, factor_year_sharpe.csv, factor_gross_net.csv, break_tests.csv, break_tests_gross.csv, drivers.csv, insurance_view.csv, leave_one_out.csv, component_sharpe.csv, regime_watch_thresholds.json); code ap_regime_draw.py, ap_regime_build.py, ap_regime_gross.py, ap_regime_two.py, ap_regime_three.py, ap_regime_tables.py, refresh_regime.py.

DONE REGIME
