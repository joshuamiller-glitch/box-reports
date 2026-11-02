> **DEFECT BASE (V13X):** every cut, rank, lead and withdrawal on this page was computed on D7 V13X, which dropped the TH-L2 loss cut and take-line exits that came before the resting add filled (846 rows; BASE-4 fixed it in V13Y). Treat all numbers here as 'defect base (V13X)'; the V13Y re-run of the leads is in progress and will supersede them.

# DS3_ZONES_3_L2_TAPE_LOCKNONE - the tape-zone cells in the LOCK-NONE frame (per-book locks only; the user's literal text), D7 v1.3 EXACT (V13X), ZL-2

Frame: `V13X.run_v13x(lock=None)`. Base maxDD (lock none): F9 132.6k, key episode 202627 -> 202634 -> 202639 (trough week 2026-08-17). Cuts below are POSITIVE = shallower maxDD (cut = 1 - maxDD(cell)/maxDD(base)). Noise bands = Z3 FINAL lock-off band (n=107, DS3_ZONES_3_NOISE.md), flip 2%% / 5%%: L3M 17/23, L6M 16/21, HOLD 15/20, MID 20/33, PRE 22/26, X' 15/25. Rule: cut above the band in L6M AND in PRE or X'; NO-HARM column: PRE and MID not worse than -(flip-2%% band) = -22%% / -20%%.

## Counts over 631 scored cells
| rule | flip 2%% band | flip 5%% band |
|---|---|---|
| band rule (L6M and PRE-or-X') | 26 | 5 |
| band rule + no harm (PRE, MID) | 15 | 2 |

## Cells passing the band rule at flip 2%
| cell | rows fired | F9 | L3M | L6M | HOLD | MID | PRE | X' | mean L6M $k/wk (MDE) | no harm | cut without the key week F9 / L6M / PRE / X' | leave-one-month-out min (F9) | placebo ranks F9 sv/rd/sd (n) ; PRE sv/rd/sd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A25 TCD_ext skip | 11984 | +43% | +24% | +71% | +21% | -20% | -16% | +26% | +1.7 (+12.6) | NO | +40% / +69% / -27% / +25% | -20% |  |
| A30 TCD_ext skip | 13563 | +42% | +26% | +71% | +13% | -23% | -11% | +17% | +4.6 (+13.6) | NO | +38% / +69% / -22% / +17% | -23% |  |
| VAR TCD_ext age1h skip A40 | 11044 | +57% | +23% | +58% | +15% | +9% | -13% | +37% | +0.3 (+12.9) | yes |  |  |  |
| A40 TCD_ext skip | 15965 | +54% | +5% | +54% | +15% | +2% | -52% | +27% | +2.8 (+13.0) | NO | +50% / +69% / -65% / +27% | +2% | 0.98/0.96/0.97 (100) ; PRE 0.13/0.14/0.03 |
| VAR TCD_ext age24h skip A40 | 15965 | +54% | +5% | +54% | +15% | +2% | -52% | +27% | +2.8 (+13.0) | NO |  |  |  |
| A30 TCD_ext half | 13563 | +46% | +21% | +52% | +7% | -13% | -10% | +15% | +2.1 (+8.1) | yes | +43% / +49% / -10% / +15% | -13% | 0.98/1.00/1.00 (100) ; PRE 0.29/0.32/0.20 |
| VAR TCD_ext age24h half A30 | 13563 | +46% | +21% | +52% | +7% | -13% | -10% | +15% | +2.1 (+8.1) | yes |  |  |  |
| A40 TCD_ext half | 15965 | +51% | +10% | +51% | +8% | +1% | -32% | +18% | +2.2 (+9.0) | NO | +50% / +61% / -27% / +18% | +1% |  |
| A50 TCD_ext half | 17805 | +48% | +2% | +48% | +12% | -1% | -20% | +18% | +2.0 (+8.3) | yes | +49% / +61% / -11% / +17% | -1% |  |
| A60 TCD_ext half | 19375 | +46% | -1% | +46% | +17% | -1% | -18% | +24% | +1.0 (+8.6) | yes | +49% / +61% / -10% / +23% | -1% |  |
| A20 TCD_cdlo skip | 4170 | +34% | +1% | +42% | +2% | -41% | -32% | +18% | +4.5 (+6.4) | NO | +29% / +48% / -25% / +17% | -41% |  |
| A40 TCD_cdhi skip | 8807 | +41% | +20% | +41% | +26% | +27% | -22% | +17% | -2.1 (+9.8) | NO | +39% / +39% / -23% / +16% | +27% |  |
| VAR TCD_ext age1h half A30 | 9792 | +38% | +21% | +38% | +10% | -7% | -4% | +23% | +1.5 (+8.9) | yes |  |  |  |
| A20 TVP_lvn_sess skip | 18233 | +5% | -40% | +35% | -50% | -101% | -20% | +20% | +1.0 (+11.1) | NO | -1% / +54% / -32% / +19% | -101% |  |
| VAR TCD_ext strMid skip A40 | 5983 | +31% | +17% | +31% | +19% | +35% | +3% | +39% | -1.5 (+8.9) | yes |  |  |  |
| VAR TPF_poc_sw15 age4h skip A40 | 3421 | +21% | +22% | +21% | +17% | +13% | -9% | +33% | +0.4 (+3.4) | yes |  |  |  |
| VAR TPF_poc_sw15 age24h skip A40 | 3440 | +21% | +22% | +21% | +17% | +13% | -9% | +33% | +0.4 (+3.4) | yes |  |  |  |
| A40 TPF_poc_sw15 skip | 3485 | +21% | +22% | +21% | +17% | +13% | -9% | +41% | +0.4 (+3.4) | yes | +18% / +18% / -20% / +40% | +10% | 0.72/0.93/0.94 (100) ; PRE 0.52/0.32/0.34 |
| VAR TPF_val_sess strMid skip A40 | 1130 | +20% | +7% | +20% | +11% | -9% | +12% | +39% | +0.5 (+2.9) | yes |  |  |  |
| A40 TPF_val_sess skip | 3315 | +20% | +12% | +20% | +12% | +15% | -20% | +36% | +0.6 (+3.0) | yes | +25% / +25% / -25% / +38% | +15% | 0.68/0.88/0.91 (100) ; PRE 0.37/0.15/0.14 |
| VAR TPF_val_sess age4h skip A40 | 2440 | +18% | +17% | +18% | +13% | +21% | -31% | +44% | +0.0 (+2.3) | NO |  |  |  |
| A10 TCD_ext skip | 5592 | +18% | +7% | +18% | +2% | -17% | -3% | +27% | -1.6 (+8.2) | yes | +20% / +20% / -14% / +27% | -17% |  |
| VAR TPF_val_sess age24h skip A40 | 3102 | +17% | +11% | +17% | +12% | +16% | -22% | +48% | -0.3 (+2.6) | NO |  |  |  |
| A40 TPF_hvn0_sw15 skip | 3357 | +17% | +13% | +17% | +12% | -13% | +8% | +45% | +0.8 (+3.4) | yes | +14% / +14% / -1% / +44% | -13% |  |
| A40 TPF_lvn0_sw15 skip | 2787 | +16% | +4% | +16% | -13% | -11% | -30% | +19% | +1.1 (+3.2) | NO | +17% / +17% / -20% / +18% | -11% |  |
| VAR TLP_p25_4h strMid skip A40 | 1901 | +16% | +5% | +16% | +4% | +0% | +2% | +17% | +1.0 (+2.9) | yes |  |  |  |

## Reading
* The only cells that pass the band are the cum-delta-extreme family (TCD ext/cdlo/cdhi: skip or half, fire on 12-16%% of rows) and a few small TPF lines at D40 (poc_sw15, val_sess, hvn0_sw15, lvn0_sw15, lvn0_sess; 2.8-3.5k rows) plus one developing-LVN session cell. They pass through L6M and X' while PRE and MID are negative for most of them; the no-harm column keeps 7 at flip 2%% and none at flip 5%%.
* The L6M / F9 cut does not depend on the base's key week (2026-08-17): dropping that week leaves the cut (table), so these are not ONE-WEEK; the leave-one-month-out minimum is negative for the TCD cells.
* TCD family (fires 12-16%% of rows): same-volume placebo draws in this frame cut F9 by only 2-10%% on average; the real TCD cells beat them on F9 (ranks 0.96-1.00) but are WORSE than random in PRE (ranks 0.04-0.33): a recent-window effect, not a stable one.
* The developing-POC cells and the 12R-lock leads are not in this table: with the lock off they do not pass (page DS3_ZONES_3_L2_TAPE_POC.md).

## Freshness (age <= 1 h / 4 h / 24 h since the line formed) and strength-tercile variants of the candidates, lock none (maxDD change vs the lock-none base; negative = shallower)
| variant | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| TCD_ext age1h half A30 | 9792 | -38% | -21% | -38% | -10% | +7% | +4% | -23% |
| TCD_ext age1h skip A40 | 11044 | -57% | -23% | -58% | -15% | -9% | +13% | -37% |
| TCD_ext age24h half A30 | 13563 | -46% | -21% | -52% | -7% | +13% | +10% | -15% |
| TCD_ext age24h skip A40 | 15965 | -54% | -5% | -54% | -15% | -2% | +52% | -27% |
| TCD_ext age4h half A30 | 11307 | -46% | -21% | -47% | -7% | +13% | +7% | -10% |
| TCD_ext age4h skip A40 | 12995 | -51% | -6% | -52% | -15% | +3% | +14% | -9% |
| TCD_ext strHigh half A30 | 4650 | -4% | -5% | -4% | +8% | -1% | +11% | +9% |
| TCD_ext strHigh skip A40 | 5508 | +1% | +9% | +1% | +23% | +30% | +2% | +16% |
| TCD_ext strLow half A30 | 3996 | -34% | -7% | -34% | -13% | +26% | +3% | +4% |
| TCD_ext strLow skip A40 | 4707 | -35% | +0% | -41% | -13% | +37% | +40% | +5% |
| TCD_ext strMid half A30 | 5082 | -13% | -15% | -13% | -13% | -9% | -18% | -27% |
| TCD_ext strMid skip A40 | 5983 | -31% | -17% | -31% | -19% | -35% | -3% | -39% |
| TLP_p25_4h age1h skip A40 | 3741 | -16% | -4% | -16% | -8% | -26% | -1% | +16% |
| TLP_p25_4h age24h skip A40 | 5110 | -19% | -15% | -19% | -1% | -18% | -8% | +18% |
| TLP_p25_4h age4h skip A40 | 5110 | -19% | -15% | -19% | -1% | -18% | -8% | +18% |
| TLP_p25_4h strHigh skip A40 | 1904 | -7% | -6% | -7% | -5% | -21% | -10% | +28% |
| TLP_p25_4h strLow skip A40 | 1906 | +1% | -6% | +1% | +1% | -4% | +5% | -20% |
| TLP_p25_4h strMid skip A40 | 1901 | -16% | -5% | -16% | -4% | +0% | -2% | -17% |
| TLQ_SES_asia age1h half A40 | 690 | -4% | -11% | -4% | -4% | -2% | -3% | -8% |
| TLQ_SES_asia age24h half A40 | 4643 | -7% | -20% | -7% | +1% | -2% | -13% | -7% |
| TLQ_SES_asia age4h half A40 | 2110 | -10% | -23% | -10% | -4% | -2% | -10% | -2% |
| TLQ_SES_asia strHigh half A40 | 1503 | +0% | +0% | +0% | +0% | +0% | +0% | -1% |
| TLQ_SES_asia strLow half A40 | 1859 | -7% | -20% | -7% | +1% | -2% | -2% | +0% |
| TLQ_SES_asia strMid half A40 | 1281 | +0% | +0% | +0% | +0% | +0% | -11% | -7% |
| TPF_poc_sw15 age1h skip A40 | 2748 | -11% | -22% | -11% | -8% | -11% | -2% | -10% |
| TPF_poc_sw15 age24h skip A40 | 3440 | -21% | -22% | -21% | -17% | -13% | +9% | -33% |
| TPF_poc_sw15 age4h skip A40 | 3421 | -21% | -22% | -21% | -17% | -13% | +9% | -33% |
| TPF_poc_sw15 strHigh skip A40 | 510 | +1% | +3% | +1% | +1% | +1% | -3% | -10% |
| TPF_poc_sw15 strLow skip A40 | 1870 | -6% | -18% | -6% | -6% | -18% | -2% | -30% |
| TPF_poc_sw15 strMid skip A40 | 1105 | -13% | -19% | -13% | -13% | +7% | +2% | -7% |
| TPF_val_sess age1h skip A40 | 867 | -2% | -2% | -2% | -2% | +2% | -3% | -4% |
| TPF_val_sess age24h skip A40 | 3102 | -17% | -11% | -17% | -12% | -16% | +22% | -48% |
| TPF_val_sess age4h skip A40 | 2440 | -18% | -17% | -18% | -13% | -21% | +31% | -44% |
| TPF_val_sess strHigh skip A40 | 1152 | -3% | -3% | -3% | -3% | -26% | +32% | +8% |
| TPF_val_sess strLow skip A40 | 1033 | +0% | -2% | +0% | +0% | +0% | +1% | -4% |
| TPF_val_sess strMid skip A40 | 1130 | -20% | -7% | -20% | -11% | +9% | -12% | -39% |
Reading: for the cum-delta extremes the fresher the line the bigger the F9/L6M cut (age <= 1 h: -57%% F9 for D40 skip) and the cut sits in the LOW-strength tercile (|cum delta| small), not in the high-strength one: strength is not monotone, which argues against a real order-flow signal.

## TLQ|SES|asia (D40, half size): why the PRE/HOLD placebo ranks are ~0.5 while F9 is 0.97 (12R, 91 draws per kind)
The prior-Asia-session high/low line fires on 5%% of the rows. Its cuts are F9 -9%%, HOLD -9%%, PRE -15%% (12R) and -7%% / +1%% / -13%% (lock off). A same-volume random half-size of 5%% of the rows already gives a PRE cut of a similar size (the draws' PRE ranks are 0.43 / 0.49 / 0.68 for the three kinds), because PRE is a long window in which any size cut lowers the drawdown; only the Feb-Oct cut (rank 0.91 / 0.98 / 0.92) is above chance, and that window has 38 weeks of which the top weeks decide. So the line is a small LEAD in Feb-Oct, volume-equivalent in PRE/HOLD.

## Lock-none placebos at 100 draws per kind (rank = share of draws with a shallower cut than the real cell is worse than... i.e. real cut beats the draw; 1.00 = best)
| cell | F9 sv/rd/sd | L3M sv | HOLD sv | PRE sv/rd/sd | mean cut of the same-volume draws (F9) |
|---|---|---|---|---|---|
| A30 TCD_ext half | 0.98 / 1.00 / 1.00 | 0.93 | 0.68 | 0.29 / 0.32 / 0.20 | -1% |
| A40 TCD_ext skip | 0.98 / 0.96 / 0.97 | 0.74 | 0.78 | 0.13 / 0.14 / 0.03 | -8% |
| A40 TPF_poc_sw15 skip | 0.72 / 0.93 / 0.94 | 0.86 | 0.95 | 0.52 / 0.32 / 0.34 | -9% |
| A40 TPF_val_sess skip | 0.68 / 0.88 / 0.91 | 0.80 | 0.88 | 0.37 / 0.15 / 0.14 | -9% |
| A40 TLQ_SES_asia half | 0.75 / 0.78 / 0.80 | 0.95 | 0.42 | 0.93 / 0.89 / 0.98 | -1% |
| A40 TLP_p25_4h skip | 0.70 / 0.80 / 0.89 | 0.80 | 0.49 | 0.81 / 0.92 / 0.83 | -10% |
No candidate beats the placebos in BOTH F9 and PRE: the TCD cells beat them in F9 only and are worse than random in PRE; the TPF cells are volume-equivalent; the Asia line is above chance in F9 only. **Survivors list for ZL-3: none passes band + no-harm + placebo in the lock-none frame; the two small leads to carry into combinations are TLQ|SES|asia D40 half and TLP>=25-lot 4 h D40 skip (both TOLERANT in the 12R frame), and the developing day-POC (12R frame only).**
