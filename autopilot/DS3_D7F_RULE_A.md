# DS3_D7F_RULE_A - D7 rule (a) "skip the first 60 min of each session": does it lower drawdown? (SIXTY-2, 2026-10-31). POST-HOC, nothing here is a PASS

Research only. Masks capped 20260206, UNTOUCHED never read. Prereg `l2vast/ds3/prereg/D7F_RULE_A_prereg.md` sha256 9d86f03734fe07723400ceb31524c9f9a8324173472951f4c4d1c3d14873a0df (DECISIONS.md, before the scored run). Engine = DS3_ONE_CONVENTION (`l2vast/ds3/code/oneconv/oc_lib.py`; run `code/sixty2/rule_a_run.py`, tables `rule_a_tab.py`, data `out/sixty2/rule_a.pkl`): live lots, 70/30 integer, PE 45 s, zone skip, Asia-stop cut, ER half-up min 1, parity stop, slip +0.25, SizeMult = running max over TAKEN signals. **D7 convention (user answer): a skipped signal does NOT update SizeMult (the filter runs before the sizer)**; implemented by removing the skipped rows from the engine, so they feed neither the max nor the combined-lock R. Tie-out: composite L6M 41.1 $k/wk with no lock, 32.3 with 12R(m0 1.0), equal to DS3_ONE_CONVENTION Table A2; the skip mask ties to the D7F feature file on all shared rows (21,747 of 61,401 engine rows are in a first hour, 35%). C = composite, A = composite + rule (a). Weekly series; maxDD = max peak-to-trough of the weekly cumulative; Sharpe = weekly mean/SD x sqrt(52); worst-20 = sum of the 20 worst weeks (L3M 14 / L6M 28 / HOLD 32 weeks: fewer than 20 losing weeks, so that sum is positive and not a loss measure there; it is n/a for the equal-risk line, use SD or maxDD matches). The equal-risk lines are a LINEAR rescale of the rule's weekly series (not a re-run at integer lots). Intervals are paired 4-week-block bootstrap (1000 draws); no significance claim.

## PAGE 1

**Answer: no, rule (a) does not lower drawdown where it matters now.** In L3M/L6M the first-hour skip DOUBLES the maxDD (21.4 to 44.0 and 22.9 to 44.0 $k, no lock; 26.6 to 51.1 with the 12R lock; one week of -44 / -41 against -23 / -27 for the composite), raises the SD by 4-12% (44.7 to 50.0 L3M; 42.7 to 44.5 L6M), lowers Sharpe (6.94 to 5.80 L6M) and the mean (-5.3 $k/wk L6M no lock; -0.2 with 12R). The bootstrap interval of the maxDD difference excludes 0 in L3M and L6M (no lock) but is a handful of weeks (one bad week). In HOLD the maxDD falls (97 to 44, driven by one -68 week in C), and in PRE / X' it falls too (PRE 241 to 208 no lock, 233 to 124 with 12R; X' 121 to 67), but PRE is the window where the worst-20 gets WORSE without a lock (-875 to -1112), and the mean falls 9 $k/wk in PRE. At equal risk the rule loses: scaled to the composite's SD it earns 34.4 vs 41.1 L6M (28.8 vs 34.4 L3M), 14.2 vs 23.1 in PRE; it beats the composite at equal SD only in HOLD (41.9 vs 38.6) and X' (9.8 vs 8.0). So the sign flips between regimes (the same flip D7F saw in the rate: first hour positive 2025-26, negative PRE) and nothing says it lowers drawdown reliably. D7 ships (a) OFF; this keeps it OFF.

By session (tables below, post-hoc cuts of the same rule): Asia gets smoother in L6M/HOLD (no lock: SD 39.3 to 33.3 L6M, maxDD 41.0 to 35.4, Sharpe 4.24 to 4.75, mean -1.1) and in X' (maxDD 122 to 74), but worse in L3M with the 12R lock (maxDD 29.9 to 49.7) and PRE worst-20 slightly worse without a lock; NY-AM has a lower SD in every window (L6M 28.7 to 19.8) at -3.7 mean (equal-SD rescale 10.9 vs 10.3) and a flat/higher maxDD in X'; NY-PM goes from about 0 to +0.9 with a smaller maxDD but is a tiny book (SD 4); London is worse on SD/maxDD/Sharpe in L3M-PRE. At most these are leads for a per-session first-hour switch (Asia / NY-AM / NY-PM); a per-session rule would need its own prereg. Nothing here supports turning (a) ON for the whole stack.

## Tables (C / A pairs)

### Total stack, lock off: composite (C) vs composite + rule (a) (A); $k/wk; maxDD = weekly-cumulative; w20 = sum of worst 20 weeks in the window (negative = loss); Sharpe = mean/SD x sqrt52

| window | weeks | mean C / A | SD C / A | maxDD C / A | worst-20 C / A | worst week C / A | Sharpe C / A | dSD, dmaxDD, dw20 (95% block-bootstrap) | equal-risk by worst-20 (k; A mean x k vs C mean) | by SD (k; A mean x k) | by maxDD (k; A mean x k) |
|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 34.4 / 32.2 | 44.7 / 50.0 | 21.4 / 44.0 | 481.7 / 450.9 | -21.4 / -44.0 | 5.55 / 4.65 | SD -2.2..16.4; DD 9.1..66.6; w20 -190.5..25.5 | n/a (<20 losing weeks) | 0.89; 28.8 vs 34.4 | 0.49; 15.6 vs 34.4 |
| L6M | 28 | 41.1 / 35.8 | 42.7 / 44.5 | 22.9 / 44.0 | 371.0 / 305.2 | -22.9 / -44.0 | 6.94 / 5.80 | SD -5.4..8.3; DD 1.8..45.8; w20 -201.7..45.2 | n/a (<20 losing weeks) | 0.96; 34.4 vs 41.1 | 0.52; 18.6 vs 41.1 |
| HOLD | 32 | 38.6 / 34.6 | 51.8 / 42.8 | 97.0 / 44.0 | 136.5 / 182.3 | -68.0 / -44.0 | 5.37 / 5.84 | SD -24.8..5.4; DD -89.5..33.9; w20 -154.8..272.8 | n/a (<20 losing weeks) | 1.21; 41.9 vs 38.6 | 2.21; 76.4 vs 38.6 |
| PRE | 75 | 23.1 / 14.1 | 55.7 / 55.1 | 241.2 / 208.1 | -875.2 / -1111.7 | -119.6 / -122.2 | 2.99 / 1.84 | SD -7.9..7.9; DD -86.2..233.9; w20 -565.4..44.2 | 0.79; 11.1 vs 23.1 | 1.01; 14.2 vs 23.1 | 1.16; 16.3 vs 23.1 |
| X' | 44 | 8.0 / 9.5 | 32.6 / 31.7 | 120.5 / 67.1 | -419.6 / -341.9 | -65.7 / -58.6 | 1.76 / 2.16 | SD -7.3..5.3; DD -99.5..56.6; w20 -74.3..287.1 | 1.23; 11.7 vs 8.0 | 1.03; 9.8 vs 8.0 | 1.80; 17.1 vs 8.0 |

#### Per session (lock off; post-lock per-trade $ by entry session, summed over books; pre has no live lots): C / A, $k/wk

| session | window | mean | SD | maxDD | worst-20 | Sharpe | equal-risk k | A mean x k vs C |
|---|---|---|---|---|---|---|---|---|
| asia | L3M | 20.9 / 20.7 | 47.3 / 39.6 | 62.0 / 49.7 | 292.4 / 290.2 | 3.18 / 3.77 | nan | nan vs 20.9 |
| asia | L6M | 23.1 / 22.0 | 39.3 / 33.3 | 41.0 / 35.4 | 79.7 / 119.6 | 4.24 / 4.75 | nan | nan vs 23.1 |
| asia | HOLD | 20.7 / 19.4 | 39.7 / 32.0 | 50.5 / 35.4 | -89.0 / 9.8 | 3.77 / 4.37 | nan | nan vs 20.7 |
| asia | PRE | 12.1 / 7.7 | 38.6 / 34.5 | 129.3 / 100.4 | -604.5 / -641.1 | 2.27 / 1.61 | 0.94 | 7.3 vs 12.1 |
| asia | X' | 3.9 / 4.7 | 30.3 / 17.4 | 122.3 / 74.1 | -422.5 / -205.8 | 0.92 / 1.96 | 2.05 | 9.7 vs 3.9 |
| london | L3M | 5.0 / 3.4 | 21.9 / 28.5 | 49.0 / 90.7 | 70.4 / 47.6 | 1.65 / 0.86 | nan | nan vs 5.0 |
| london | L6M | 7.9 / 6.3 | 27.9 / 27.3 | 65.1 / 90.7 | -101.0 / -117.3 | 2.04 / 1.67 | 0.86 | 5.5 vs 7.9 |
| london | HOLD | 8.3 / 7.2 | 27.8 / 26.6 | 65.1 / 90.7 | -168.7 / -164.3 | 2.15 / 1.96 | 1.03 | 7.4 vs 8.3 |
| london | PRE | -0.5 / -2.4 | 30.5 / 33.3 | 232.6 / 309.7 | -781.5 / -881.6 | -0.13 / -0.52 | 0.89 | -2.1 vs -0.5 |
| london | X' | 1.3 / 2.9 | 25.6 / 25.8 | 116.7 / 128.5 | -417.9 / -363.7 | 0.36 / 0.81 | 1.15 | 3.3 vs 1.3 |
| nyam | L3M | 9.1 / 6.9 | 30.5 / 24.1 | 46.1 / 50.0 | 127.9 / 97.2 | 2.16 / 2.08 | nan | nan vs 9.1 |
| nyam | L6M | 10.3 / 6.6 | 28.7 / 19.8 | 50.2 / 50.0 | -88.3 / -53.4 | 2.58 / 2.41 | 1.65 | 10.9 vs 10.3 |
| nyam | HOLD | 9.6 / 7.1 | 30.1 / 19.2 | 50.8 / 50.0 | -182.8 / -86.7 | 2.31 / 2.69 | 2.11 | 15.0 vs 9.6 |
| nyam | PRE | 11.2 / 8.2 | 29.9 / 21.2 | 119.0 / 66.6 | -451.1 / -305.8 | 2.70 / 2.78 | 1.48 | 12.1 vs 11.2 |
| nyam | X' | 3.0 / 1.9 | 28.7 / 22.8 | 127.6 / 187.7 | -448.9 / -345.3 | 0.76 / 0.61 | 1.30 | 2.5 vs 3.0 |
| nypm | L3M | -0.6 / 1.1 | 4.1 / 4.2 | 15.1 / 5.3 | -9.0 / 15.9 | -1.12 / 1.94 | nan | nan vs -0.6 |
| nypm | L6M | -0.1 / 0.9 | 4.1 / 3.8 | 15.1 / 8.8 | -41.5 / -13.1 | -0.21 / 1.68 | 3.16 | 2.8 vs -0.1 |
| nypm | HOLD | -0.1 / 0.9 | 3.8 / 3.6 | 15.1 / 8.8 | -44.6 / -19.8 | -0.14 / 1.83 | 2.25 | 2.0 vs -0.1 |
| nypm | PRE | 0.3 / 0.6 | 5.4 / 4.7 | 47.7 / 39.1 | -109.3 / -91.4 | 0.43 / 0.88 | 1.20 | 0.7 vs 0.3 |
| nypm | X' | -0.2 / -0.1 | 4.0 / 3.9 | 26.2 / 25.0 | -67.5 / -62.6 | -0.40 / -0.09 | 1.08 | -0.1 vs -0.2 |

### Total stack, lock 12R: composite (C) vs composite + rule (a) (A); $k/wk; maxDD = weekly-cumulative; w20 = sum of worst 20 weeks in the window (negative = loss); Sharpe = mean/SD x sqrt52

| window | weeks | mean C / A | SD C / A | maxDD C / A | worst-20 C / A | worst week C / A | Sharpe C / A | dSD, dmaxDD, dw20 (95% block-bootstrap) | equal-risk by worst-20 (k; A mean x k vs C mean) | by SD (k; A mean x k) | by maxDD (k; A mean x k) |
|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 29.0 / 26.2 | 48.4 / 53.1 | 26.6 / 51.1 | 406.1 / 366.4 | -26.6 / -40.9 | 4.32 / 3.55 | SD -3.8..16.4; DD 8.6..65.6; w20 -232.5..9.9 | n/a (<20 losing weeks) | 0.91; 23.8 vs 29.0 | 0.52; 13.7 vs 29.0 |
| L6M | 28 | 32.3 / 32.1 | 45.2 / 47.1 | 26.6 / 51.1 | 180.9 / 201.8 | -26.6 / -40.9 | 5.15 / 4.91 | SD -5.2..9.2; DD -6.7..59.6; w20 -222.8..296.9 | n/a (<20 losing weeks) | 0.96; 30.7 vs 32.3 | 0.52; 16.7 vs 32.3 |
| HOLD | 32 | 31.4 / 30.7 | 48.9 / 45.4 | 35.3 / 51.1 | -6.2 / 55.3 | -26.6 / -40.9 | 4.63 / 4.88 | SD -14.0..6.1; DD -10.0..54.2; w20 -211.2..280.2 | n/a (<20 losing weeks) | 1.08; 33.1 vs 31.4 | 0.69; 21.2 vs 31.4 |
| PRE | 75 | 15.1 / 11.1 | 49.8 / 43.6 | 232.6 / 124.1 | -608.2 / -676.7 | -45.6 / -45.6 | 2.19 / 1.84 | SD -11.8..-0.2; DD -203.2..115.6; w20 -232.2..87.4 | 0.90; 10.0 vs 15.1 | 1.14; 12.7 vs 15.1 | 1.87; 20.9 vs 15.1 |
| X' | 44 | 1.0 / 5.2 | 30.1 / 29.7 | 119.6 / 100.9 | -468.2 / -402.2 | -44.7 / -37.4 | 0.25 / 1.26 | SD -7.1..5.3; DD -197.3..63.8; w20 -24.3..238.8 | 1.16; 6.0 vs 1.0 | 1.01; 5.2 vs 1.0 | 1.18; 6.1 vs 1.0 |

#### Per session (lock 12R; post-lock per-trade $ by entry session, summed over books; pre has no live lots): C / A, $k/wk

| session | window | mean | SD | maxDD | worst-20 | Sharpe | equal-risk k | A mean x k vs C |
|---|---|---|---|---|---|---|---|---|
| asia | L3M | 24.7 / 18.0 | 42.3 / 41.2 | 29.9 / 49.7 | 346.5 / 251.8 | 4.21 / 3.15 | nan | nan vs 24.7 |
| asia | L6M | 23.6 / 22.3 | 37.9 / 32.2 | 29.9 / 29.7 | 93.5 / 128.1 | 4.49 / 4.99 | nan | nan vs 23.6 |
| asia | HOLD | 21.9 / 20.0 | 37.8 / 30.6 | 31.4 / 29.7 | -51.1 / 30.9 | 4.19 / 4.72 | nan | nan vs 21.9 |
| asia | PRE | 9.2 / 8.1 | 34.4 / 28.4 | 130.5 / 87.3 | -462.6 / -378.3 | 1.93 / 2.06 | 1.22 | 9.9 vs 9.2 |
| asia | X' | 1.2 / 4.3 | 26.9 / 15.0 | 104.9 / 47.4 | -373.0 / -165.2 | 0.32 / 2.07 | 2.26 | 9.7 vs 1.2 |
| london | L3M | 3.1 / 2.3 | 19.3 / 29.3 | 45.9 / 106.3 | 43.1 / 32.0 | 1.15 / 0.56 | nan | nan vs 3.1 |
| london | L6M | 4.2 / 3.6 | 26.1 / 28.2 | 83.6 / 106.3 | -158.9 / -194.8 | 1.16 / 0.91 | 0.82 | 2.9 vs 4.2 |
| london | HOLD | 4.3 / 3.6 | 25.1 / 26.7 | 83.6 / 106.3 | -215.0 / -244.3 | 1.23 / 0.98 | 0.88 | 3.2 vs 4.3 |
| london | PRE | -0.1 / -2.1 | 21.7 / 26.6 | 192.9 / 235.1 | -500.4 / -635.5 | -0.02 / -0.56 | 0.79 | -1.6 vs -0.1 |
| london | X' | -1.2 / -0.9 | 19.4 / 20.8 | 110.2 / 119.7 | -306.6 / -343.1 | -0.45 / -0.32 | 0.89 | -0.8 vs -1.2 |
| nyam | L3M | 1.4 / 4.7 | 24.0 / 19.2 | 46.1 / 32.9 | 19.7 / 66.3 | 0.42 / 1.78 | nan | nan vs 1.4 |
| nyam | L6M | 4.5 / 5.3 | 27.0 / 16.6 | 62.8 / 32.9 | -188.7 / -45.6 | 1.21 / 2.32 | 4.14 | 22.1 vs 4.5 |
| nyam | HOLD | 5.2 / 6.1 | 26.7 / 16.3 | 62.8 / 32.9 | -250.6 / -72.6 | 1.40 / 2.68 | 3.45 | 20.9 vs 5.2 |
| nyam | PRE | 5.5 / 4.5 | 21.9 / 18.6 | 126.3 / 54.8 | -308.8 / -281.7 | 1.82 / 1.74 | 1.10 | 4.9 vs 5.5 |
| nyam | X' | 1.3 / 2.0 | 23.2 / 20.7 | 111.4 / 146.8 | -325.2 / -282.7 | 0.41 / 0.69 | 1.15 | 2.3 vs 1.3 |
| nypm | L3M | -0.2 / 1.2 | 3.8 / 4.1 | 14.0 / 8.9 | -3.2 / 16.4 | -0.44 / 2.05 | nan | nan vs -0.2 |
| nypm | L6M | -0.0 / 0.9 | 3.6 / 3.7 | 14.1 / 11.8 | -34.5 / -12.9 | -0.06 / 1.76 | 2.68 | 2.4 vs -0.0 |
| nypm | HOLD | 0.0 / 0.9 | 3.3 / 3.5 | 14.1 / 11.8 | -35.3 / -19.7 | 0.09 / 1.90 | 1.79 | 1.7 vs 0.0 |
| nypm | PRE | 0.4 / 0.6 | 4.3 / 3.9 | 38.8 / 35.1 | -77.1 / -64.9 | 0.74 / 1.07 | 1.19 | 0.7 vs 0.4 |
| nypm | X' | -0.2 / -0.2 | 2.4 / 2.6 | 15.8 / 21.0 | -43.0 / -43.9 | -0.74 / -0.53 | 0.98 | -0.2 vs -0.2 |


Caveats. Post-hoc rule fixed by the user's text; earlier looks at the same family exist (N1c, EINT2 exclfirst60, DS3_D7_FILTERS); one scored run per lock setting. A6 is the PB7 Asia-only 1-lot book of the one-convention engine. Equal-risk rescaling is linear in the weekly series and ignores integer lot rounding and the lock re-firing at a changed R.
