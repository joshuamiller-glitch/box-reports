# REPORT C3-H3 - the 5-minute NQ trend family on 2013-2022 (untouched pre-2023 history)

Registered in PREREG_AUTOPILOT.md (CYCLE 3) before any run. **Pre-stated reading (binding):** the family is a FOUND-quality candidate only if the additive Sharpe uplift is >= +0.10 over 2013-2022 as a whole AND in at least 6 of 10 calendar years AND worst-decile correlation <= +0.30.

## Verdict
**The 5-minute family has no edge on 2013-2022 and fails the pre-stated reading at every share.** The ensemble's standalone weekly Sharpe over 2013-2022 is **+0.07** (net of 1 tick/side + commission); the additive uplift to the pair is **+0.001** at a 20% share (needs >= +0.10), and the uplift is >= +0.10 in only 4 of 10 years (needs 6). The negative worst-decile correlation (-0.09) is the only gate it meets. The 2023-08..2026 result (uplift +0.16 clean vs the live pair at 20%) was a feature of that window.

## What was run (and two corrections to the V5 specs)
- Data: purchased NQ 1-minute bars 2013-01-02..2026-10-13, difference-back-adjusted at 55 rolls (see REPORT_C3_H2.md). 5-min bars are built from the 1-minute bars by position within the trading day exactly as `b10_gsig.resample`; signals from `b10_gsig.make`; engine = my numba re-implementation (below) with the V5 book recipe: market entry at the next 1-min open, 60-pt stop / 60-pt target (stop first), one trade at a time, 10 NQ per book, R = $12,000, per-book 5R/-2R daily rule, commission $2.49 x 2 x 10 plus slippage 0.5 pt per round trip (1 tick/side).
- **Correction 1 - clock and windows.** The B10 G books use the harness `hm` clock, which is **fixed UTC-4** (not DST-aware): the 18:05 entry start and the 16:40 flatten are therefore 17:05 and 15:40 ET in winter. The engine reproduces the stored trades only with this clock.
- **Correction 2 - entry guards.** SPECS_5MIN.md says the G books have no 09:00-09:58 block. The stored trades show otherwise: the STStrat `BASE` guards stay active (`guard_ny` 09:00-10:00 and `guard_asia` 15:00-16:50 on the same clock) because `b10_grun` overrides only `win_start/win_end/force`. Exits at the flatten are at the close of the last bar before the cutoff. With both corrections the re-implementation matches the stored trades (2023-02..2026-10):

| book                                       |   ref |   me |   matched |   same |   net_ref |   net_me |
|:-------------------------------------------|------:|-----:|----------:|-------:|----------:|---------:|
| G1_pxma_kindZLEMA_n200_tf5_eNone_delta     |  3153 | 3177 |      3051 |   3045 |    809843 |   755648 |
| G4_macd_f5_s35_g5_modezero_tf5_eNone_delta |  3218 | 3227 |      3142 |   3132 |    827712 |   709313 |
| G4_macd_f12_s26_g9_modezero_tf5_eNone_none |  3356 | 3368 |      3290 |   3279 |    786480 |   760731 |
| G1_macross_kindEMA_f9_s21_tf5_eNone_adx20  |  3279 | 3282 |      3201 |   3191 |    669866 |   736414 |
| G3_supertrend_n14_m3.0_tf5_eNone_none      |  3431 | 3452 |      3369 |   3361 |    895593 |   906246 |

  (ref = V5 trades11.pkl, me = this engine; 'entry matched' = same entry minute; after the 5R/-2R rule, net at zero slippage. Residual differences are the daily rule's path dependence on the ~3% of unmatched entries.)
- **Deviation from the 5-book spec (disclosed).** Two of the five clean-chosen representatives use the real signed-**delta** confirmation, which needs trades data that does not exist before 2023-02. A bar-built proxy reproduces only 80-89% of their entries and gives very different nets (table below), so the **primary ensemble replaces those two by their `none` twins** (ZLEMA-200 `none`, MACD 5/35/5 `none`), which are exactly reproducible. The five-book ensemble with the proxy delta is reported as a sensitivity: its 2013-2022 uplift is -0.002 at 20% (primary +0.001) and its standalone Sharpe +0.05: same conclusion.

| book                                       | proxy                 |   n_real |   n_proxy |   matched |   net_real |   net_proxy |
|:-------------------------------------------|:----------------------|---------:|----------:|----------:|-----------:|------------:|
| G1_pxma_kindZLEMA_n200_tf5_eNone_delta     | sign(c-o)*v           |     3177 |      3214 |      2831 |     481448 |      322100 |
| G1_pxma_kindZLEMA_n200_tf5_eNone_delta     | closeloc*v            |     3177 |      3146 |      2666 |     481448 |      204743 |
| G1_pxma_kindZLEMA_n200_tf5_eNone_delta     | tick sign(c-c_prev)*v |     3177 |      3228 |      2843 |     481448 |      665806 |
| G4_macd_f5_s35_g5_modezero_tf5_eNone_delta | sign(c-o)*v           |     3227 |      3268 |      2620 |     427913 |      145665 |
| G4_macd_f5_s35_g5_modezero_tf5_eNone_delta | closeloc*v            |     3227 |      3193 |      2443 |     427913 |      767165 |
| G4_macd_f5_s35_g5_modezero_tf5_eNone_delta | tick sign(c-c_prev)*v |     3227 |      3276 |      2612 |     427913 |      276915 |

- Members (primary): ZLEMA-200 (tf5), MACD 5/35 zero (tf5), MACD 12/26 zero (tf5), EMA 9/21 cross with ADX(14)>20 (tf5), Supertrend ATR14 x3 (tf5). Each is divided by its clean (2023-08..2025-07) weekly std, averaged, and the sleeve is scaled so its clean weekly std = share x the live pair's clean weekly std (the V5 convention; same constants on the long history). The pair on the long history is the 1-minute-engine live-rules pair (REPORT_C3_H2.md).

## Results
Standalone weekly Sharpe, 2013-2022 ensemble: **+0.07**. By member: G1_pxma_kindZLEMA_n2 +0.44, G4_macd_f5_s35_g5_mo +0.09, G4_macd_f12_s26_g9_m +0.18, G1_macross_kindEMA_f +0.12, G3_supertrend_n14_m3 -0.50.

By calendar year (weekly Sharpe; uplift = Sharpe(pair + k x ensemble) - Sharpe(pair)):
|   year |   5-min ensemble standalone Sharpe |   1-min pair Sharpe |   uplift @10% |   uplift @20% |   uplift @30% |   uplift @50% |
|-------:|-----------------------------------:|--------------------:|--------------:|--------------:|--------------:|--------------:|
|   2013 |                              -0.64 |               -0.48 |         -0.08 |         -0.17 |         -0.24 |         -0.37 |
|   2014 |                               1.09 |               -1.09 |          0.04 |          0.1  |          0.18 |          0.43 |
|   2015 |                              -0.64 |                0.62 |         -0.03 |         -0.06 |         -0.12 |         -0.27 |
|   2016 |                               0.01 |                0.13 |          0.01 |          0.02 |          0.02 |          0.03 |
|   2017 |                               0    |                0.13 |          0.01 |          0.01 |          0.02 |          0.02 |
|   2018 |                               0.66 |               -1.18 |          0.05 |          0.11 |          0.2  |          0.41 |
|   2019 |                              -1.98 |               -0.09 |         -0.2  |         -0.4  |         -0.6  |         -0.96 |
|   2020 |                               1.03 |               -1.43 |          0.08 |          0.19 |          0.3  |          0.56 |
|   2021 |                               1.06 |               -0.75 |          0.11 |          0.24 |          0.37 |          0.64 |
|   2022 |                              -0.83 |               -2.09 |         -0.02 |         -0.03 |         -0.02 |          0.04 |
|   2023 |                              -1.31 |                0.2  |        nan    |        nan    |        nan    |        nan    |
|   2024 |                               0.37 |                2.18 |        nan    |        nan    |        nan    |        nan    |
|   2025 |                               1.05 |                2.25 |        nan    |        nan    |        nan    |        nan    |
|   2026 |                               1.79 |                1.68 |        nan    |        nan    |        nan    |        nan    |

2013-2022 summary by share:
| share   |   uplift_2013_2022 | years_ge_010   | ci90           |   null_p95 |   null_median |   rank |   up_2x_slippage | pre_2023_reading   |
|:--------|-------------------:|:---------------|:---------------|-----------:|--------------:|-------:|-----------------:|:-------------------|
| 10%     |             -0.005 | 1 / 10         | [-0.06, +0.05] |     -0.016 |        -0.067 |  0.975 |           -0.033 | FAIL               |
| 20%     |              0.001 | 4 / 10         | [-0.12, +0.11] |     -0.022 |        -0.124 |  0.975 |           -0.057 | FAIL               |
| 30%     |              0.015 | 4 / 10         | [-0.16, +0.18] |     -0.021 |        -0.171 |  0.975 |           -0.071 | FAIL               |
| 50%     |              0.069 | 4 / 10         | [-0.22, +0.34] |     -0.002 |        -0.231 |  0.975 |           -0.067 | FAIL               |

- **Correlation with the pair (2013-2022, weekly):** all weeks -0.19; the pair's worst-decile weeks (53 weeks) -0.09. In those weeks the sleeve at 20% share earned $2,631 a week on average. Rolling 26-week correlation: median -0.43, min -0.82, max +0.40.
- **Own timing-destroyed null (200 draws, random entries with each member's signal counts, same exits/costs/rule):** the null ensemble loses (median standalone Sharpe -0.70, p95 -0.22) because a 60/60 bracket with costs and no timing is negative; the real ensemble's +0.07 ranks above all 200. So the entries carry some timing information, but that information nets to about zero after cost, and the *uplift* is statistically indistinguishable from nothing: bootstrap 90% CIs of the uplift (5,000 week resamples) include zero at every share (20%: [-0.12, +0.11]).
- **Plateau (+-25% on every length/multiplier, all-members and one-at-a-time, and timeframes 3/4/6/8/10):** the uplift at 20% across the 17 neighbours ranges -0.076 to +0.116; the base is +0.001. No neighbour except the 8-minute ensemble (+0.116 at 20%, standalone +0.52) reaches +0.10. The 8-minute result is a post-hoc neighbour of 17 cells, selected after seeing the numbers: not evidence.
- **2x slippage:** uplift at 20% falls to -0.057.
- **Continuity on the live window:** same ensemble, same constants, vs the 1-minute pair: uplift +0.17 (clean), +0.47 (H1), +0.42 (H2) at 20%; vs the live pair on clean: +0.16. The family's standalone Sharpe: 2023 -1.31, 2024 +0.37, 2025 +1.05, 2026 +1.79.
- **Why the pair's pre-2023 losses do not rescue it:** the 1-minute pair loses in 2013-2022 (Sharpe -0.78); a sleeve with ~zero standalone Sharpe barely offsets that at any share.

## Caveats
Back-adjustment error at 55 rolls; bars are UTC-continuous v.0 (volume-front) so roll timing differs from the harness; the pair on the long history is the 1-minute engine (REPORT_C3_H2.md fidelity: weekly corr 0.88); the delta books are replaced as stated; slippage 1 tick/side.

DONE C3_H3
