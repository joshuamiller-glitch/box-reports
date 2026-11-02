# DS3_ZONES_3_L2_TAPE_LP_AGAINST_NATURAL - flag #2 on the NATURAL touch reading (ZL-2, 2026-11-02, V13Y, Shadow only)
Convention (now PRIMARY, per lead order after ZL-1 clean-room): a print is knowable at second s+1; ANY trade at the print's price in any second after the print's own second ends its freshness, including the first usable second (code: zstream.episodes0; the legacy scan started one index later, episodes). Aggressor tape flag: A = SELL aggressor, B = BUY aggressor. Rule unchanged otherwise: print >= 25 lots, aggressor opposite to the trade, last 4 h, between entry and target within min(40, td).

## Mask
2,081 rows (538 taken lock none, 354 taken 12R); legacy 2,614 rows. Jaccard with legacy 0.796 (533 rows only in legacy, none only in natural). ZL-1 clean-room: 1,937 (primary, at-or-through) / 2,008 (range-contains) / 1,942 (range-contains, usable next second); Jaccard with mine 0.865 / 0.897 / 0.926. Row diff for ZL-1: ZL-2/lp_natural_row_diff_ZL2_vs_ZL1.csv. Residual = touch test (1-s range-contains vs at-or-through) and ~147 rows only mine (offset convention, per-4-h block vs per day/instrument, 16 roll days; pinned with ZL-1 pending).

## Row-level saved dollars (V13Y, $k = minus realised net of flagged taken rows)
| | L6M | HOLD | PRE | X' | ALL |
|--|--|--|--|--|--|
| lock none, natural (ZL-2) | 43.0 | 60.7 | 95.8 | 1.3 | 136.8 |
| lock none, legacy | 77 | 91 | 73 | -4 | 138 |
| lock none, ZL-1 clean-room | 44 | 53 | 56 | -11 | 83 |
| 12R, natural | 16.2 | 27.8 | 91.6 | 14.2 | 123.7 |
Per year (lock none, taken flagged / $ per flagged row / $ per other row / saved $k): 2023 102 / -64 / +24 / 6.5; 2024 138 / -393 / +155 / 54.3; 2025 125 / -193 / +168 / 24.1; 2026 173 / -300 / +168 / 52.0. Windows $ per flagged vs other row: L6M -380 vs +187, HOLD -296 vs +177, PRE -532 vs +150, X' -11 vs +29. Positive in every year.

## Multiplicity null (2,001 families, same natural scan inside every family, rows thinned to 2,081)
Statistic min(L6M,HOLD,PRE) saved $k, real 43.0 (lock none): p = 0.037 pooled (offset 0.000, shuffled-day 0.099, side-flip 0.011); with X' (min 1.3): p = 0.18 (offset 0.02, shuffled-day 0.15, side-flip 0.37). 12R: min3 16.2 p = 0.19; with X' p = 0.08. Legacy was p 0.004 / 0.20: the natural reading weakens the result; the shuffled-day family (keeps real price-offset structure) is the strictest and is not beaten. WITH-trade aggressor (flip) real: L6M -7.3 / HOLD -10.3 / PRE -70.6 / X' +17.5, so the sign of the aggressor matters directionally, but the null does not make it a confirmed effect. File: ds3_zl/lp_null_V13Y_natural.csv.

## Phase-averaged drawdown band (9 lock-reset phases, lock none, V13Y; band flip 2%: L6M 15.5, HOLD 13.3, MID 26.8, PRE 11.5, X' 14.1)
PA cut: L6M +12.4% (sd 2.9), HOLD +9.9, MID -16.1, PRE +2.5, X' -13.7. Below the L6M band, PRE and X' below band: FAILS the band (legacy mask was L6M +16%, also failed X'/PRE). Single phase 0: L6M +18.7. Not a drawdown cut; a dollar-saving row filter only.

## Walk-forward (purged, trailing 12 months, excess over random skipping, fixed natural grid masks_lp_var_fix.npz)
Default T25|4h|against|D40: +205.8k over 34 months, t 3.42, 23/34 positive (random setting +104.6k t 0.79 in the 144-setting against grid; small grid T25/T50: chosen +257.9k t 3.20, random +196.2k t 2.55). Months with the default positive: 23/34. Selection adds nothing over the default.

## Label
Flag #2 = LEAD-weak, Shadow only, relabelled on natural numbers: row-level dollars positive in every year and window but X' neutral; pooled null p 0.037 (0.18 with X'); PA drawdown band FAIL; walk-forward t 3.4 for the fixed default. No PASS. Shadow spec logs both conventions (natural A=sell/B=buy primary; legacy field lp_flag_legacy).
