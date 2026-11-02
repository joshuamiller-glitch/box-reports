# DS3_ZONES_3_L2_TAPE_V13Y_PA - phase-averaged re-flag of the screen with Z3's V13Y band, no-harm passers at 100 draws, side restriction quantified (ZL-2)

## 1. Re-flag with Z3's V13Y phase-averaged (PA) band
PA band (lock-off, flip 2% / 5%): L6M 15.5 / 20, HOLD 13.3 / 19.1, MID 26.8 / 39.8, PRE 11.5 / 16.1, X' 14.1 / 22.4 (DS3_ZONES_3_NOISE.md, V13Y section). Rule: PA cut above the band in L6M AND in PRE or X'; no-harm: PRE and MID PA cut not worse than minus the flip-2% band. PA cut = mean over K = 9 lock-reset phases (week key shifted -4..+4 label days, `de_engine._ENV['WK']`) of 1 - maxDD(cell)/maxDD(base) at the same phase; V13Y, lock none. 49 cells phase-averaged (the 45 cells within 0.7x of the band on the single path + the leads LP any D40, LP AGAINST, TLQ|SES|asia, day-POC, TCD A30 half).
Single-path screen of all 628 cells with the PA band numbers: band rule flip-2% 20, flip-5% 10; with no-harm 3 / 0.
**Phase-averaged (49 cells): band rule passes 15 at flip 2% and 9 at flip 5%; band + no-harm: 1 at flip 2%, 0 at flip 5%.**
| cell | PA F9 | PA L6M | PA HOLD | PA MID | PA PRE | PA X' | SD of L6M over phases | band 2% | band 5% | no harm |
|---|---|---|---|---|---|---|---|---|---|---|
| A25 TCD_ext skip | +66% | +67% | +26% | -19% | -40% | +24% | 0.05 | Y | Y | NO |
| A40 TCD_ext skip | +62% | +66% | +17% | -34% | -78% | +25% | 0.05 | Y | Y | NO |
| A50 TCD_ext half | +65% | +65% | +20% | -12% | -36% | +20% | 0.04 | Y | - | NO |
| A30 TCD_ext skip | +62% | +65% | +15% | -36% | -37% | +13% | 0.06 | - | - | NO |
| A60 TCD_ext half | +63% | +63% | +25% | +6% | -35% | +18% | 0.05 | Y | - | NO |
| A40 TCD_ext half | +59% | +59% | +22% | -6% | -50% | +24% | 0.05 | Y | Y | NO |
| A30 TCD_ext half | +52% | +52% | +21% | -14% | -25% | +16% | 0.04 | Y | - | NO |
| A40 TPF_lvn0_sw15 skip | +35% | +35% | +1% | -82% | -15% | +23% | 0.03 | Y | Y | NO |
| A40 TLQ_swg1h skip | +28% | +33% | -42% | -159% | +34% | -229% | 0.10 | Y | Y | NO |
| A40 TLQ_SWG_f3_1h skip | +27% | +33% | -45% | -166% | +35% | -216% | 0.10 | Y | Y | NO |
| A40 TCD_cdhi skip | +27% | +27% | +27% | +5% | -52% | +16% | 0.09 | Y | - | NO |
| A10 TCD_ext skip | +26% | +26% | +14% | -9% | -13% | +40% | 0.10 | Y | Y | NO |
| LP T10_24h_any_D40 | +26% | +26% | +9% | -124% | -4% | +30% | 0.07 | Y | Y | NO |
| A20 TVP_lvn_sess half | +24% | +25% | +1% | -72% | -40% | +14% | 0.11 | Y | - | NO |
| A20 TPF_lvn0_sw15 skip | +24% | +24% | +8% | -72% | -3% | +22% | 0.04 | Y | Y | NO |
| LP T25_4h_any_P75 | +23% | +23% | +14% | -18% | +8% | +2% | 0.04 | - | - | yes |
| B20 TVP_poc skip | +19% | +19% | +16% | +2% | -11% | +14% | 0.05 | - | - | yes |
| A50 TLP_p25_4h skip | +19% | +19% | +10% | -18% | +8% | +1% | 0.03 | - | - | yes |
| A40 TLP_p25_4h skip | +19% | +19% | +12% | -18% | +9% | +4% | 0.04 | - | - | yes |
| LP T25_4h_against_D40 | +16% | +16% | +13% | -15% | +3% | -16% | 0.03 | - | - | yes |
| A40 TCP_hvn1_60d half | +16% | +16% | +14% | +0% | -1% | +15% | 0.01 | Y | - | yes |
| LP T25_4h_any_D20 | +16% | +16% | +11% | -13% | +8% | +7% | 0.04 | - | - | yes |
| A20 TLP_p25 skip | +16% | +16% | +11% | -13% | +8% | +7% | 0.04 | - | - | yes |
| A20 TLP_p25_4h skip | +16% | +16% | +11% | -13% | +8% | +7% | 0.04 | - | - | yes |
(cut positive = shallower maxDD.) Reading: the cum-delta extremes (TCD_ext) pass the band through L6M and X' with PA PRE -25..-78% and MID -12..-36% (not no-harm); the volume lines TLQ swing 1h pass L6M/PRE with X' -216..-229% (a harm). The only band + no-harm cell is `A40__TCP_hvn1_60d__half` (652 rows): PA L6M +16% (band 15.5), X' +15% (band 14.1), PRE -1%: it clears the band by 0.5-1 point and its single-path PRE placebo rank is 0.02. LP_AGAINST: PA L6M +16%, PRE +3%, X' -16%: does not pass. LP any-side: PA L6M +19%, PRE +9%, X' +4%: does not pass (PRE below 11.5). Day-POC and TLQ|SES|asia are far below the band.

## 2. No-harm passers: 100-draw row-level placebos (random rows, same count per day; share of draws the real cut beats) and episode checks, V13Y lock none
| cell | rows | F9 | L3M | HOLD | PRE | episode checks |
|---|---|---|---|---|---|---|
| A40 TPF_poc_sw15 skip | 3485 | 0.92 | 0.90 | 0.94 | 0.14 | PRE -17%; min LOMO F9 -17%; per-year $k +93 / +3 / -66 / +51 |
| A40 TCP_hvn1_60d skip | 652 | 0.87 | 0.36 | 0.23 | 0.02 | F9 cut without the key week 2026-08-03 +26%; ONE-WEEK; X' ONE-WEEK; per-year $k +15 / -3 / +25 / +24 (2023-26); min leave-one-month-out F9 -3%, PRE -8% |
| A40 TPF_hvn0_sw15 skip | 3357 | 0.82 | 0.44 | 0.83 | 0.64 | F9 without key week +12%; min LOMO F9 -27%; per-year $k +73 / +36 / -73 / +18 |
| A20 TCD_cdhi half | 5956 | 0.97 | 0.66 | 0.45 | 0.06 | F9 ONE-WEEK; PRE -19%; per-year $k -7 / -42 / -61 / -31 (loses every year) |
Reading: with 100 draws none has all of F9, HOLD and PRE ranks >= 0.90 (TPF hvn0_sw15: 0.82 / 0.83 / 0.64; TCP hvn1_60d: PRE 0.02; TCD_cdhi half PRE 0.06, loses money in every year). **No no-harm passer survives the placebo.**

## 3. Aggressor-side conventions of LP_AGAINST (answered to ZL-1 for the clean-room reimplementation)
Tape flag 66 = buy aggressor (+1), 65 = sell aggressor (-1), 78 neutral; AGAINST = aggressor opposite to the trade direction. Single tape rows >= 25 contracts (not aggregated). Print usable from second+1; live while SS[kin] < print second + 1 + 14,400 s (upper end exclusive), window measured from the signal second SS[kin]. Touch = a path second (after the print's own second, through kin inclusive) whose 1-s [SL, SH] contains the print price p (a trade at or through p). Ahead: 0 <= side*(p - E) <= min(40, td). De-duplicated tape (NQ_dropin_redo), path-frame prices (per-4-h-block, per-contract offsets); 16 roll days have no prints. Mask: out/zl/features_tape/masks_lp_var.npz key `T25|4h|against|D40` (2,614 rows).

## 4. Does the side restriction matter? (V13Y, row level with day-clustered 95% CI and the same-count-per-day placebo rank; effect = with minus without)
| outcome | rule | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|
| V13Y realised $ lock none | any side (5,110 rows) | -676 [-1055, -342] rk 0.00 | -467 [-748, -195] rk 0.00 | -304 [-1149, +403] rk 0.27 | -164 [-457, +198] rk 0.18 | +171 [-291, +650] rk 0.51 |
| V13Y realised $ lock none | AGAINST the trade (2,614) | -790 [-1214, -357] rk 0.00 | -554 [-920, -235] rk 0.00 | -100 [-747, +614] rk 0.59 | -465 [-861, -68] rk 0.03 | +1 [-621, +605] rk 0.51 |
| V13Y realised $ lock none | WITH the trade (2,838) | -366 [-775, +107] rk 0.20 | -291 [-748, +115] rk 0.17 | -387 [-2010, +785] rk 0.19 | +173 [-281, +653] rk 0.79 | +169 [-564, +781] rk 0.48 |
| V13Y realised $ 12R | any side (5,110 rows) | -649 [-1105, -220] rk 0.02 | -418 [-818, -61] rk 0.05 | -173 [-1235, +770] rk 0.36 | -518 [-982, -129] rk 0.01 | +374 [-234, +1059] rk 0.82 |
| V13Y realised $ 12R | AGAINST the trade (2,614) | -738 [-1426, -32] rk 0.03 | -539 [-979, -108] rk 0.04 | -175 [-1149, +799] rk 0.51 | -795 [-1368, -220] rk 0.00 | +82 [-703, +851] rk 0.63 |
| V13Y realised $ 12R | WITH the trade (2,838) | -428 [-1019, +217] rk 0.25 | -184 [-754, +402] rk 0.27 | -37 [-1834, +1338] rk 0.41 | -219 [-757, +401] rk 0.21 | +523 [-264, +1326] rk 0.80 |
| library net pts/contract | any side (5,110 rows) | -5 [-12, +1] rk 0.07 | -5 [-10, -1] rk 0.01 | -6 [-15, +4] rk 0.09 | -3 [-7, +2] rk 0.19 | -2 [-8, +4] rk 0.33 |
| library net pts/contract | AGAINST the trade (2,614) | -1 [-10, +9] rk 0.34 | -2 [-9, +4] rk 0.20 | -4 [-14, +8] rk 0.32 | -6 [-14, +1] rk 0.12 | -4 [-12, +4] rk 0.43 |
| library net pts/contract | WITH the trade (2,838) | -9 [-17, +1] rk 0.05 | -8 [-14, -1] rk 0.00 | -7 [-21, +6] rk 0.01 | +0 [-5, +8] rk 0.69 | -0 [-8, +8] rk 0.45 |

Best-of-N null (saved $k of the flagged taken trades; families: price-level offset and shuffled-day, same density; rank = share of null families >= real):
| rule | frame | min(L6M,HOLD,PRE) real / rank | min(L6M,HOLD,PRE,X') real / rank |
|---|---|---|---|
| AGAINST the trade (2,001 families) | lock none | 73.1 / 0.004 | -4.2 / 0.201 |
| AGAINST the trade (2,001 families) | 12R | 46.1 / 0.041 | -4.6 / 0.282 |
| any side (400 families) | lock none | 9.2 / 0.060 | -51.9 / 0.253 |
| any side (400 families) | 12R | 57.2 / 0.003 | -55.7 / 0.560 |

**Reading.** In V13Y realised dollars the AGAINST rows are worse than the others in L6M / HOLD / PRE (lock none -$790 / -$554 / -$465 per taken row, ranks 0.00 / 0.00 / 0.03) while the WITH-the-trade rows are not distinguishable (-$366 / -$291 / +$173, ranks 0.20 / 0.17 / 0.79); the any-side rule sits in between (-$676 / -$467 / -$164). But the CIs overlap (L6M AGAINST [-1214, -357] vs WITH [-775, +107]), the library bracket outcome shows the REVERSE ordering (WITH -9 / -8 pts per contract in L6M / HOLD, AGAINST -1 / -2), and the best-of-N null does not separate them in 12R (any side rank 0.002 vs AGAINST 0.041 on min(L6M,HOLD,PRE)). **The side restriction improves the PRE leg in lock none (saved $73k vs $9k) but "side matters" is not established**: it holds for one outcome (V13Y realised $), in one frame, with overlapping intervals.
