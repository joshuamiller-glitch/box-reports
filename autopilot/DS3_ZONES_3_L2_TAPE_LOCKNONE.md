# DS3_ZONES_3_L2_TAPE_LOCKNONE - the tape-zone cells in the LOCK-NONE frame (per-book locks only; the user's literal text), D7 v1.3 EXACT (V13X), ZL-2

Frame: `V13X.run_v13x(lock=None)`. Base maxDD (lock none): F9 132.6k, key episode 202627 -> 202634 -> 202639 (trough week 2026-08-17). Cuts below are POSITIVE = shallower maxDD (cut = 1 - maxDD(cell)/maxDD(base)). Noise bands = Z3 FINAL lock-off band (n=107, DS3_ZONES_3_NOISE.md), flip 2%% / 5%%: L3M 17/23, L6M 16/21, HOLD 15/20, MID 20/33, PRE 22/26, X' 15/25. Rule: cut above the band in L6M AND in PRE or X'; NO-HARM column: PRE and MID not worse than -(flip-2%% band) = -22%% / -20%%.

## Counts over 583 scored cells
| rule | flip 2%% band | flip 5%% band |
|---|---|---|
| band rule (L6M and PRE-or-X') | 15 | 2 |
| band rule + no harm (PRE, MID) | 7 | 0 |

## Cells passing the band rule at flip 2%
| cell | rows fired | F9 | L3M | L6M | HOLD | MID | PRE | X' | mean L6M $k/wk (MDE) | no harm | cut without the key week F9 / L6M / PRE / X' | leave-one-month-out min (F9) | placebo ranks F9 sv/rd/sd (n) ; PRE sv/rd/sd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A25 TCD_ext skip | 11984 | +43% | +24% | +71% | +21% | -20% | -16% | +26% | +1.7 (+12.6) | NO | +40% / +69% / -27% / +25% | -20% |  |
| A30 TCD_ext skip | 13563 | +42% | +26% | +71% | +13% | -23% | -11% | +17% | +4.6 (+13.6) | NO | +38% / +69% / -22% / +17% | -23% |  |
| A40 TCD_ext skip | 15965 | +54% | +5% | +54% | +15% | +2% | -52% | +27% | +2.8 (+13.0) | NO | +50% / +69% / -65% / +27% | +2% | 0.98/0.98/0.98 (52) ; PRE 0.15/0.17/0.04 |
| A30 TCD_ext half | 13563 | +46% | +21% | +52% | +7% | -13% | -10% | +15% | +2.1 (+8.1) | yes | +43% / +49% / -10% / +15% | -13% | 0.96/1.00/1.00 (49) ; PRE 0.33/0.32/0.18 |
| A40 TCD_ext half | 15965 | +51% | +10% | +51% | +8% | +1% | -32% | +18% | +2.2 (+9.0) | NO | +50% / +61% / -27% / +18% | +1% |  |
| A50 TCD_ext half | 17805 | +48% | +2% | +48% | +12% | -1% | -20% | +18% | +2.0 (+8.3) | yes | +49% / +61% / -11% / +17% | -1% |  |
| A60 TCD_ext half | 19375 | +46% | -1% | +46% | +17% | -1% | -18% | +24% | +1.0 (+8.6) | yes | +49% / +61% / -10% / +23% | -1% |  |
| A20 TCD_cdlo skip | 4170 | +34% | +1% | +42% | +2% | -41% | -32% | +18% | +4.5 (+6.4) | NO | +29% / +48% / -25% / +17% | -41% |  |
| A40 TCD_cdhi skip | 8807 | +41% | +20% | +41% | +26% | +27% | -22% | +17% | -2.1 (+9.8) | NO | +39% / +39% / -23% / +16% | +27% |  |
| A20 TVP_lvn_sess skip | 18233 | +5% | -40% | +35% | -50% | -101% | -20% | +20% | +1.0 (+11.1) | NO | -1% / +54% / -32% / +19% | -101% |  |
| A40 TPF_poc_sw15 skip | 3485 | +21% | +22% | +21% | +17% | +13% | -9% | +41% | +0.4 (+3.4) | yes | +18% / +18% / -20% / +40% | +10% | 0.77/0.92/0.94 (52) ; PRE 0.44/0.28/0.38 |
| A40 TPF_val_sess skip | 3315 | +20% | +12% | +20% | +12% | +15% | -20% | +36% | +0.6 (+3.0) | yes | +25% / +25% / -25% / +38% | +15% |  |
| A10 TCD_ext skip | 5592 | +18% | +7% | +18% | +2% | -17% | -3% | +27% | -1.6 (+8.2) | yes | +20% / +20% / -14% / +27% | -17% |  |
| A40 TPF_hvn0_sw15 skip | 3357 | +17% | +13% | +17% | +12% | -13% | +8% | +45% | +0.8 (+3.4) | yes | +14% / +14% / -1% / +44% | -13% |  |
| A40 TPF_lvn0_sw15 skip | 2787 | +16% | +4% | +16% | -13% | -11% | -30% | +19% | +1.1 (+3.2) | NO | +17% / +17% / -20% / +18% | -11% |  |

## Reading
* The only cells that pass the band are the cum-delta-extreme family (TCD ext/cdlo/cdhi: skip or half, fire on 12-16%% of rows) and a few small TPF lines at D40 (poc_sw15, val_sess, hvn0_sw15, lvn0_sw15, lvn0_sess; 2.8-3.5k rows) plus one developing-LVN session cell. They pass through L6M and X' while PRE and MID are negative for most of them; the no-harm column keeps 7 at flip 2%% and none at flip 5%%.
* The L6M / F9 cut does not depend on the base's key week (2026-08-17): dropping that week leaves the cut (table), so these are not ONE-WEEK; the leave-one-month-out minimum is negative for the TCD cells.
* TCD family (fires 12-16%% of rows): same-volume placebo draws in this frame cut F9 by only 2-10%% on average; the real TCD cells beat them on F9 (ranks 0.96-1.00) but are WORSE than random in PRE (ranks 0.04-0.33): a recent-window effect, not a stable one.
* The developing-POC cells and the 12R-lock leads are not in this table: with the lock off they do not pass (page DS3_ZONES_3_L2_TAPE_POC.md).
