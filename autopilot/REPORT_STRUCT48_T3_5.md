# REPORT STRUCT48 T3.5 - NQ overnight drift confirmation (2026-10-24)

Prereg l2vast/struct48/prereg/T3_5.md sha256 51f4298845c195b8496b804d6ce41eb3b3a5dc75ad3ea0dac377ab124e2f6283 (frozen before scoring; DECISIONS.md; 20 cells in ledger/trials.jsonl, cumulative 28,216). Code code/t35run.py. Rows rows/T3_5_oos.json (pre-2024) and rows/T3_5_final.json. Weekly series out/T3_5/*.npz (unit weekly 1x/2x per sleeve, weeks from 2013). Pre-holdout text autopilot/REPORT_STRUCT48_T3_5_PREHOLD.md.

## Verdict: NOT CONFIRMED. 0 of 8 primary cells pass. The drift is real in sign (positive pre-2024 and 2024+, 2x-cost positive, 12/14 calendar years positive) but is NOT distinguishable from a random 17.6 h long hold in NQ (placebo), and the VIX9D/VIX<1 filter adds nothing over a random subset of nights.

## Disclosures
- 2024+ was already looked at for these sleeves in T3.3 (look #1, counted). This round's stage wf (calendar years 2024-2026, WF/HOLD portfolio) is look #2, logged in ledger/holdout_looks.jsonl (track T3_5) after the pre-holdout text. Stage oos computed no 2024+ number and used Set A only through 2024-01-31.
- The pre-2024 history is not virgin: T3.3 extra_evidence printed 2013-2023-02 by-year unit P&L for these sleeves. The filter choice itself came from T3.3 (2024+ seen), so selection is not blind.
- Data limits: NQ 1-min complete 2013-01-02..2026-10-15 (about 250 nights/yr). VIX/VIX9D/VIX3M/VIX6M cover all of 2013+. VX term file only from 2022-04-25 (VX neighbour has 315 pre-2024 nights). Set A starts 2023-02-10, so no Set A portfolio exists before that; pre-2024 is standalone, scaled with a frozen IS (2023-02-10..2024-01-31) SD factor. Roll handling: nights spanning a roll skipped (43 ON_none / 27 ON_VT in the OOS window; 54 of 3,432 overall); sensitivity keeping them on the back-adjusted series changes the weekly mean by <3% (ON_none 208 vs 210, ON_VT 169 vs 173). Cost $14.84 RT/lot; 2x $29.68.

## (1) Pre-2024 out-of-sample (NQ 2013-02..2023-12, 1 lot, about 568 weeks)
| sleeve | nights | $/night | hit | wk mean | CI (week-block) | 2x wk mean | yrs+ | max yr share | halves wk mean | placebo days | placebo clock | DSR |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ON_none | 2674 | 44.8 | 0.559 | 210 | [-20, 446] | 140 | 9/11 | 0.44 | 106 / 333 | n/a | 0.32 | 0.00 |
| ON_VT | 1979 | 49.8 | 0.566 | 173 | [7, 351] | 121 | 9/11 | 0.44 | 95 / 265 | 0.63 | 0.29 | 0.00 |
| ON_none@1550 (gate nb) | 2674 | 45.5 | 0.560 | 213 | [-12, 450] | 144 | 9/11 | 0.60 | 90 / 358 | n/a | n/a | 0.00 |
| ON_none@1559 (gate nb) | 2674 | 41.8 | 0.559 | 196 | [-22, 426] | 126 | 9/11 | 0.57 | 142 / 259 | n/a | n/a | 0.00 |
| ON_VT_a1 (gate nb) | 2476 | 48.4 | 0.558 | 210 | [17, 419] | 146 | 9/11 | 0.46 | 95 / 346 | n/a | n/a | 0.00 |
| ON_VT_a2 (gate nb) | 2490 | 32.3 | 0.557 | 141 | [-58, 345] | 76 | 9/11 | 0.45 | 93 / 197 | n/a | n/a | 0.00 |
| ON_VT_b (info) | 2311 | 45.4 | 0.564 | 184 | [1, 376] | 124 | 8/11 | 0.55 | 77 / 310 | n/a | n/a | 0.00 |
| ON_VX_C (info) | 315 | 103.8 | 0.508 | 57 | [-53, 176] | 49 | 2/2 | 0.85 | 0 / 125 | n/a | n/a | 0.00 |

ON_VX_C covers 2022-04-26..2023-12 only (315 nights; the weekly mean column is diluted by the empty earlier weeks; $104/night, hit 50.8%). Info only.
OOS gates (o1 mean>0, o2 CI excludes 0, o3 placebo>=0.95 (min of kinds), o4 2x>0, o5 year<=60%, o6 neighbours sign): ON_none fails o2 (CI [-20,446]) and o3 (clock rank 0.32; days-placebo degenerate); ON_VT fails o3 only (days 0.63, clock 0.29; CI [7,351]). Random-time 17.6 h long holds earn a median $254/wk (ON_none window) and $235/wk (ON_VT count) vs the candidates' $210/$173: the overnight session earns no more than any other long hold of that length on this sample. All 8 primary cells: oos_pass False.
IS-overlap portfolio (2023-02..2024-01, 51 weeks, in-sample, info): ON_none 0.25x maxDD -6.7%, 0.5x -4.8%; ON_VT 0.25x +5.9%, 0.5x +13.0%.

## (2) Calendar years 2013-2026, 1 lot (mean $/night, hit rate, share of total gain)
| year | ON_none $/night | hit | share | ON_VT $/night | hit | share |
|---|---|---|---|---|---|---|
| 2013 | 23 | 0.59 | 0.02 | 40 | 0.62 | 0.03 |
| 2014 | 20 | 0.58 | 0.02 | 26 | 0.59 | 0.02 |
| 2015 | 15 | 0.55 | 0.01 | 27 | 0.54 | 0.02 |
| 2016 | -18 | 0.54 | -0.02 | -5 | 0.54 | -0.00 |
| 2017 | 64 | 0.59 | 0.06 | 57 | 0.58 | 0.05 |
| 2018 | 30 | 0.56 | 0.03 | 9 | 0.60 | 0.01 |
| 2019 | 90 | 0.58 | 0.08 | 85 | 0.57 | 0.06 |
| 2020 | 214 | 0.61 | 0.19 | 236 | 0.60 | 0.17 |
| 2021 | 162 | 0.59 | 0.14 | 112 | 0.58 | 0.10 |
| 2022 | -238 | 0.44 | -0.21 | -216 | 0.46 | -0.13 |
| 2023 | 124 | 0.52 | 0.11 | 105 | 0.52 | 0.07 |
| 2024 | 326 | 0.55 | 0.28 | 269 | 0.53 | 0.19 |
| 2025 | 203 | 0.56 | 0.17 | 537 | 0.60 | 0.42 |
| 2026 | 178 | 0.53 | 0.12 | 13 | 0.52 | 0.01 |

ON_none: years positive 12/14, largest-year share 0.28 (2024), excluding best year 305 $/wk, rolling-252-night mean positive in 79% of windows (min -270).

ON_VT: years positive 12/14, largest-year share 0.42 (2025), excluding best year 226 $/wk, rolling-252-night mean positive in 86% of windows (min -149).

The 'one year > 60%' failure is a Set-A-portfolio-delta artefact of 2024+ (WF window): the portfolio ON_VT gain is 31% 2024, 68% 2025, 1% 2026 (2025 alone, driven by $537/night in 2025 and almost no VT-qualified nights in 2026 ($13/night)). On the standalone 2013-2026 history no year exceeds 42% (ON_VT, 2025) or 28% (ON_none, 2024). 2022 (-$216 to -$238/night, hit 44-46%) is the bad year; 2016 slightly negative.

## (3) Placebos (500 each; pre-2024 and WF)
Pre-2024: see table (ON_none clock 0.32; ON_VT days 0.63 / clock 0.29). WF window (portfolio, SD-matched): ON_none clock 0.884; ON_VT days 0.768, clock 0.936 (gate = min). Neither reaches 0.95 in either window; the earlier 0.85 rank is confirmed as a structural weakness rather than noise.

## (4) Neighbours / alternative filters (listed separately, never selection)
Pre-2024 OOS weekly means: VIX/VIX3M<1 $210 (CI [17,419], 2x ok), VIX3M/VIX6M<1 $141 (CI [-58,345]), VIX9D/VIX3M<1 $184 (CI [1,376]), ON_none@15:50 $213, @15:59 $196, VX contango (f2>f1) only 315 nights. WF unit means all positive ($927-$1,261/wk per lot-equivalent). No filter beats ON_none by more than noise (VIX/VIX3M<1 equals the unfiltered mean at 92% of the nights).

## Cell table (8 primary; WF 2024-02+ incl. HOLD 2025-07+, portfolio SD-matched on WF, 142 weeks; lots only change integer-lot columns)
| cell | stand WF $/wk | corr | port d mean | port d maxDD % | CI port d mean | placebo (min) | HOLD stand | HOLD port d | L8W port d | 2x d | WF yr max | frozen-IS-k d maxDD % | int-lot d mean / d maxDD | DSR | pass of 16 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ON_none_L1_R0.25 | 1179 | -0.00 | 3738 | -14.5 | [-428, 7963] | 0.884 | 1566 | 4965 | -6844 | 3518 | 0.50 | 15.1 | 1179 / -21769 | 0.40 | 12 | o2_ci_excl0, o3_placebo_ge95, p5_ci_excludes0, p6_placebo_ge95 |
| ON_none_L1_R0.5 | 1179 | -0.00 | 7476 | 16.4 | [-856, 15926] | 0.884 | 1566 | 9929 | -13688 | 7036 | 0.50 | 111.5 | 1179 / -21769 | 0.45 | 11 | o2_ci_excl0, o3_placebo_ge95, p1_maxdd_down_10pct, p5_ci_excludes0, p6_placebo_ge95 |
| ON_none_L2_R0.25 | 1179 | -0.00 | 3738 | -14.5 | [-428, 7963] | 0.884 | 1566 | 4965 | -6844 | 3518 | 0.50 | 15.1 | 2358 / -43538 | 0.40 | 12 | o2_ci_excl0, o3_placebo_ge95, p5_ci_excludes0, p6_placebo_ge95 |
| ON_none_L2_R0.5 | 1179 | -0.00 | 7476 | 16.4 | [-856, 15926] | 0.884 | 1566 | 9929 | -13688 | 7036 | 0.50 | 111.5 | 2358 / -43538 | 0.45 | 11 | o2_ci_excl0, o3_placebo_ge95, p1_maxdd_down_10pct, p5_ci_excludes0, p6_placebo_ge95 |
| ON_VT_L1_R0.25 | 1111 | -0.03 | 4220 | -7.4 | [137, 8729] | 0.768 | 998 | 3789 | -12755 | 4006 | 0.68 | -7.1 | 1111 / -11346 | 0.43 | 12 | o3_placebo_ge95, p1_maxdd_down_10pct, p6_placebo_ge95, year_ok_WF |
| ON_VT_L1_R0.5 | 1111 | -0.03 | 8439 | -7.0 | [275, 17457] | 0.768 | 998 | 7578 | -25510 | 8012 | 0.68 | 15.1 | 1111 / -11346 | 0.50 | 12 | o3_placebo_ge95, p1_maxdd_down_10pct, p6_placebo_ge95, year_ok_WF |
| ON_VT_L2_R0.25 | 1111 | -0.03 | 4220 | -7.4 | [137, 8729] | 0.768 | 998 | 3789 | -12755 | 4006 | 0.68 | -7.1 | 2223 / -22691 | 0.43 | 12 | o3_placebo_ge95, p1_maxdd_down_10pct, p6_placebo_ge95, year_ok_WF |
| ON_VT_L2_R0.5 | 1111 | -0.03 | 8439 | -7.0 | [275, 17457] | 0.768 | 998 | 7578 | -25510 | 8012 | 0.68 | 15.1 | 2223 / -22691 | 0.50 | 12 | o3_placebo_ge95, p1_maxdd_down_10pct, p6_placebo_ge95, year_ok_WF |

Conditions per cell: o1-o6 (OOS), p1-p6 (second-system), x2_ok, year_ok_WF, cy_year_le60_2013_2026, nb_sign_WF = 16 conditions; the table column "pass of 16" is pass_count_all out of 16 (see rows). Deflated Sharpe on the cumulative ledger (28,216 trials) is below 0.51 for every cell (reported, not a gate).

Failed conditions summary: ON_none (both lots): o2 CI standalone OOS, o3 placebo, p5 port CI (0.25x and 0.5x), p6 port placebo, and p1 maxDD at 0.5x (+16.4%); at 0.25x maxDD is -14.5% (meets p1). ON_VT (both lots, both ratios): o3 placebo OOS, p1 maxDD (-7.4% at 0.25x, -7.0% at 0.5x, need <= -10%), p6 port placebo (0.77), year_ok_WF (2025 = 68% of the WF gain). Common: worst week and L8W worse than Set A (L8W portfolio delta -6.8k to -25.5k/wk), corr with Set A about 0 (ok), holdout standalone positive (ON_none +1,566/wk, ON_VT +998/wk).

## Interpretation
The overnight edge is a mean-positive, uncorrelated (corr 0) long exposure that pays after 2x cost in 12 of 14 years, but (a) random same-length holds do as well pre-2024, so it is not evidence of a time-of-day edge, (b) the VIX-term filter does not beat random nights, (c) as a diversifier it meets neither the -10% maxDD (ON_VT) nor significance (ON_none) condition, and portfolio gains are concentrated in 2025 for ON_VT. A weak LEAD only as 'NQ long beta with a diversifying correlation'; nothing here is a spec or recommendation.
