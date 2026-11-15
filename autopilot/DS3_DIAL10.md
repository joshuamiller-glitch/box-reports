## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 0 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | (not scored yet) | | | |
| H7 asia | (not scored yet) | | | |
| H7 nyam | (not scored yet) | | | |
| K7 asia | (not scored yet) | | | |
| K7 london | (not scored yet) | | | |
| K7 nyam | (not scored yet) | | | |
| K7 nypm | (not scored yet) | | | |
| M7 london | (not scored yet) | | | |
| M7 nyam | (not scored yet) | | | |
| P7 asia | (not scored yet) | | | |
| P7 london | (not scored yet) | | | |
| P7 nyam | (not scored yet) | | | |
| U7 asia | (not scored yet) | | | |
| U7 london | (not scored yet) | | | |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Dial 10: trade-horizon bracket
**VERDICT (plain, not a PASS): 139 of 386 registered cells scored through L3M, 30 through L6M, 2 through HOLD; 2 (cell,scope) leads pass the tolerant gate in every scored window (0 at scope all) - before placebo; this is the GLOBAL one-setting-for-all-books family only, the per-book per-session test (B1) is in the section above and still running. Best L3M cell inside the mean gate: M1_50_g00_c1_d10_c20_tb_B_tcoracle0.9T75 (DD +67.0%, +85531 $/wk).**

Identity: TL3_D10_M1_50_g00_c1_d10_c20_tb_B 202610 (hook active, g=0): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL. Prereg autopilot/DIAL10_PREREG.md (sha line in DECISIONS.md 2026-11-14T22:33Z). Order: ADDENDUM_DIAL10_20261114.md. Code code/th_dial10 (d10_core.py features, d10_coef.py coefficient table, d10_hooks.py hook, d10_driver.py). Bulk /mnt/l2/l2vast/_dial10. Tag D10 (quota 3).
**LOT BASIS**: engine dollars are BASE lots (live user lots x1.75, live caps = engine caps x1.75); the engine charges its raw $1.18/contract RT with the engine fills, FEES.md says $4.84 RT. Every $ column is raw $1.18 unless it says $4.84; the $4.84 columns reprice delta mean/wk as net - lots x 3.66 per trade for cell and JN05W2 alike (no rerun) and show the lot change per week.
Definition: at the signal second the hook computes EM = expected NQ range over the book+session holding horizon H (H50 = median, H75 = 75th pct of the book+session holding time, causal) from own 1-min bars (last 15/30/60/120 min range and realised vol, same-clock normal level of the previous 20 sessions, own session level, range used so far, elapsed fraction) with a walk-forward ridge (coefficients refit every 14 days; M2 adds the T-RANGE2 session forecast and calendar flags). r = EM / ref, ref = trailing-120-day median of the fitted EM for that book+session (so k = stop/ref is fitted on earlier data and tracks price/vol level). W = clip(stop x r^g, lo, hi) with dead band |r-1|<=db => W=stop. Version A: target, state-cut arm and ctxcut arms, K7 flat cut, TH-L2 LOSS_MIN and TIGHT_TRAIL, MINDIP add dip, BookLock R from actual lots and the profit-side 30-point tighten threshold all scale with W/stop. Lots: c = constant dollars at the stop (lots x stop/W, increase capped x1.5/x2/x3, wide brackets reduce lots), h = lots follow half the change in W. O7 fixed. Cell name = TL3_D10_<forecast>_<H tag>_g<10g>_c<clip 1=30..100 2=25..120 3=20..150>_d<db %>_<lots><cap x10>_t<target ratio: b book own, 08 10 12 15 x W, m moving>_<half B both N narrow-only W wide-only>.
**The hard-coded 30-point profit-side tighten threshold (sim.py manage_th_l2, `unreal < 30.0`)** is fixed through the hook: while the old-panel profit tighten is on (before 2026-11-02 08:50 ET; none of it in the live panel after that), the hook shows sim an entry reference shifted so that unreal/W-ratio is tested against 30, i.e. the trigger becomes 30 x W/stop points of open profit (tight trail already scaled via TIGHT_TRAIL). Pair cells with `_x30` in the name run the unfixed version. Effect: narrow brackets start the profit tighten earlier (at 30W/stop), wide ones later; it only matters in months before 2026-11-02, never after.

### Holding time per book and session (JN05W2 exact trades, all 43 months, minutes)
| book | session | trades | median | 75th pct | last causal H50 / H75 used |
|---|---|---|---|---|---|
| A7 | asia | 1156 | 144 | 409 | 152 / 423 |
| H7 | asia | 700 | 229 | 511 | 244 / 515 |
| H7 | nyam | 348 | 43 | 117 | 43 / 117 |
| K7 | asia | 2596 | 88 | 270 | 91 / 279 |
| K7 | london | 1781 | 64 | 139 | 64 / 140 |
| K7 | nyam | 1565 | 23 | 64 | 23 / 64 |
| K7 | nypm | 1136 | 42 | 103 | 42 / 103 |
| M7 | london | 2489 | 73 | 172 | 74 / 174 |
| M7 | nyam | 1496 | 22 | 60 | 22 / 60 |
| O7 | nyam | 452 | 14 | 33 | 15 / 33 |
| P7 | asia | 2161 | 96 | 325 | 98 / 332 |
| P7 | london | 1537 | 60 | 136 | 60 / 136 |
| P7 | nyam | 1050 | 24 | 57 | 24 / 57 |
| U7 | asia | 686 | 201 | 456 | 208 / 459 |
| U7 | london | 645 | 109 | 243 | 110 / 244 |

Heavy tail: some holds run for days (stop-less P7/K7 waiting); H is clipped to 5..600 min (median) and 8..900 (75th).

### FORECAST QUALITY TABLE: expected NQ move over the trade horizon, walk-forward (14-day blocks, expanding, min 90 days), R2 / Spearman rank, per session
Target = ln(high-low over the next H minutes / price) at each trade signal second of JN05W2 (H = causal median holding time of that book+session, tag 50; 75th pct tag 75). B0 is the session-start forecast the first Dial 9 used (available since 2025-03-19), B2 the T-RANGE2 v1 session forecast (HAR+CME, from 2023-10), both fed through the same ridge with ln H. Window "since 2025-03" is the like-for-like sample (all models on the same trades); "ALL43" scores M1/B1 on every trade from ~2023-05 (each model only where its input exists, n differs).

**Horizon = median holding time**
| session | window | n (like-for-like) | B0 start fc b (D9) | B2 T-RANGE2 | B1 own sess level | **M1 bars only** | M1 w/o same-clock | M2 +T-RANGE2+cal (file) |
|---|---|---|---|---|---|---|---|---|
| asia | since 2025-03 | 4424 | 0.32 / 0.55 | 0.36 / 0.57 | 0.19 / 0.42 | 0.49 / 0.68 | 0.42 / 0.61 | 0.49 / 0.68 |
| asia | L6M | 2006 | 0.26 / 0.52 | 0.33 / 0.57 | 0.25 / 0.50 | 0.46 / 0.67 | 0.37 / 0.60 | 0.46 / 0.66 |
| asia | L3M | 875 | 0.12 / 0.41 | 0.16 / 0.44 | 0.07 / 0.34 | 0.27 / 0.55 | 0.25 / 0.50 | 0.28 / 0.56 |
| asia | ALL43 (M1/B1) | 7125 | 0.32 / 0.55 | 0.33 / 0.56 | 0.11 / 0.35 | 0.50 / 0.68 | 0.45 / 0.63 | 0.51 / 0.69 |
| london | since 2025-03 | 3535 | 0.19 / 0.46 | 0.28 / 0.55 | 0.08 / 0.34 | 0.45 / 0.67 | 0.36 / 0.60 | 0.46 / 0.68 |
| london | L6M | 1406 | 0.10 / 0.38 | 0.22 / 0.48 | 0.07 / 0.28 | 0.32 / 0.58 | 0.25 / 0.51 | 0.34 / 0.59 |
| london | L3M | 673 | 0.07 / 0.30 | 0.09 / 0.32 | -0.09 / 0.19 | 0.13 / 0.43 | 0.06 / 0.40 | 0.18 / 0.45 |
| london | ALL43 (M1/B1) | 6298 | 0.19 / 0.46 | 0.37 / 0.57 | 0.14 / 0.38 | 0.55 / 0.71 | 0.46 / 0.65 | 0.56 / 0.72 |
| nyam | since 2025-03 | 1955 | 0.16 / 0.43 | 0.24 / 0.51 | 0.01 / 0.22 | 0.50 / 0.71 | 0.50 / 0.71 | 0.51 / 0.71 |
| nyam | L6M | 600 | 0.23 / 0.53 | 0.28 / 0.56 | 0.05 / 0.26 | 0.61 / 0.78 | 0.61 / 0.78 | 0.61 / 0.78 |
| nyam | L3M | 271 | -0.08 / 0.33 | 0.04 / 0.35 | -0.35 / 0.10 | 0.42 / 0.64 | 0.43 / 0.65 | 0.44 / 0.65 |
| nyam | ALL43 (M1/B1) | 4742 | 0.16 / 0.43 | 0.30 / 0.53 | 0.11 / 0.34 | 0.53 / 0.70 | 0.53 / 0.70 | 0.53 / 0.71 |
| nypm | since 2025-03 | 326 | 0.13 / 0.41 | 0.35 / 0.65 | 0.05 / 0.20 | 0.53 / 0.72 | 0.53 / 0.72 | 0.56 / 0.74 |
| nypm | L6M | 150 | 0.20 / 0.51 | 0.37 / 0.69 | 0.08 / 0.26 | 0.61 / 0.79 | 0.61 / 0.79 | 0.64 / 0.80 |
| nypm | L3M | 56 | -0.33 / 0.12 | -0.18 / 0.16 | -0.82 / -0.06 | 0.19 / 0.54 | 0.17 / 0.53 | 0.25 / 0.50 |
| nypm | ALL43 (M1/B1) | 967 | 0.13 / 0.41 | 0.21 / 0.54 | 0.09 / 0.29 | 0.50 / 0.68 | 0.50 / 0.68 | 0.51 / 0.69 |

**Horizon = 75th percentile holding time**
| session | window | n (like-for-like) | B0 start fc b (D9) | B2 T-RANGE2 | B1 own sess level | **M1 bars only** | M1 w/o same-clock | M2 +T-RANGE2+cal (file) |
|---|---|---|---|---|---|---|---|---|
| asia | since 2025-03 | 4424 | 0.30 / 0.54 | 0.35 / 0.54 | 0.14 / 0.36 | 0.44 / 0.65 | 0.36 / 0.58 | 0.45 / 0.66 |
| asia | L6M | 2006 | 0.12 / 0.45 | 0.23 / 0.49 | 0.19 / 0.44 | 0.32 / 0.59 | 0.18 / 0.50 | 0.32 / 0.59 |
| asia | L3M | 875 | -0.11 / 0.27 | -0.01 / 0.31 | -0.07 / 0.21 | 0.05 / 0.40 | -0.02 / 0.39 | 0.06 / 0.41 |
| asia | ALL43 (M1/B1) | 7125 | 0.30 / 0.54 | 0.30 / 0.53 | 0.09 / 0.32 | 0.49 / 0.67 | 0.43 / 0.62 | 0.49 / 0.68 |
| london | since 2025-03 | 3535 | 0.16 / 0.42 | 0.23 / 0.49 | 0.07 / 0.33 | 0.56 / 0.75 | 0.48 / 0.69 | 0.57 / 0.76 |
| london | L6M | 1406 | 0.07 / 0.29 | 0.14 / 0.41 | 0.06 / 0.27 | 0.47 / 0.68 | 0.37 / 0.61 | 0.48 / 0.68 |
| london | L3M | 673 | 0.03 / 0.23 | 0.02 / 0.27 | -0.10 / 0.26 | 0.31 / 0.61 | 0.23 / 0.54 | 0.35 / 0.60 |
| london | ALL43 (M1/B1) | 6297 | 0.16 / 0.42 | 0.31 / 0.52 | 0.12 / 0.34 | 0.59 / 0.76 | 0.53 / 0.72 | 0.61 / 0.77 |
| nyam | since 2025-03 | 1955 | 0.18 / 0.46 | 0.27 / 0.54 | 0.04 / 0.28 | 0.47 / 0.69 | 0.47 / 0.69 | 0.48 / 0.70 |
| nyam | L6M | 600 | 0.22 / 0.51 | 0.26 / 0.55 | 0.09 / 0.33 | 0.55 / 0.74 | 0.55 / 0.74 | 0.54 / 0.73 |
| nyam | L3M | 271 | -0.08 / 0.27 | 0.06 / 0.37 | -0.24 / 0.23 | 0.33 / 0.56 | 0.34 / 0.58 | 0.34 / 0.56 |
| nyam | ALL43 (M1/B1) | 4742 | 0.18 / 0.46 | 0.31 / 0.54 | 0.11 / 0.34 | 0.48 / 0.67 | 0.47 / 0.67 | 0.48 / 0.68 |
| nypm | since 2025-03 | 326 | 0.18 / 0.41 | 0.38 / 0.67 | 0.04 / 0.16 | 0.45 / 0.65 | 0.44 / 0.64 | 0.51 / 0.70 |
| nypm | L6M | 150 | 0.24 / 0.49 | 0.42 / 0.72 | 0.07 / 0.26 | 0.54 / 0.73 | 0.54 / 0.72 | 0.61 / 0.77 |
| nypm | L3M | 56 | -0.81 / 0.15 | -0.52 / 0.07 | -1.58 / -0.18 | -0.56 / 0.30 | -0.64 / 0.28 | -0.40 / 0.25 |
| nypm | ALL43 (M1/B1) | 962 | 0.18 / 0.41 | 0.23 / 0.54 | 0.06 / 0.25 | 0.40 / 0.62 | 0.40 / 0.61 | 0.43 / 0.65 |

Reading: cell = R2 / Spearman. Out-of-sample, no look-ahead (inputs closed bars up to the signal second; training targets ended before the block start). "Bars only" = D7 can compute everything from its own 1-minute bars plus a small coefficient table that is refit every 14 days; M2 needs the T-RANGE2 file and the calendar. Not a PASS claim: a better forecast does not by itself make a better bracket (exact cells below decide).


### Which setting carries it (median over cells, scope all, delta vs JN05W2; DD cut + = smaller drawdown; cells of the plain family only, no book/session restriction)
| group | cells L3M | median DD cut L3M % | median d mean L3M $/wk | median d worst week L3M | median d full stops/wk | L6M median DD cut % / d mean / cells |
|---|---|---|---|---|---|---|
| g=0.5 | 6 | -10.9 | -3267 | -3640 | +1.41 | -10.9 / -4207 / 6 |
| g=1.0 | 61 | -7.3 | -4332 | -2716 | +2.74 | -7.9 / -2767 / 16 |
| g=1.5 | 14 | -24.2 | -9917 | -8149 | +3.96 | -19.5 / -7725 / 1 |
| g=2.0 | 6 | -54.3 | -11675 | -4932 | +4.18 | -97.4 / -6163 / 1 |
| clip=1 | 51 | -7.6 | -3321 | -2716 | +2.59 | -14.4 / -3584 / 15 |
| clip=2 | 29 | -14.4 | -7400 | -4214 | +3.35 | -7.5 / -3555 / 5 |
| clip=3 | 8 | -18.3 | -7847 | -4405 | +3.77 | -12.7 / -4193 / 4 |
| tag=50 | 28 | -20.5 | -6312 | -7032 | +3.08 | -17.5 / -3785 / 10 |
| tag=75 | 60 | -7.3 | -4536 | -2581 | +2.85 | -3.7 / -2465 / 14 |
| db=0 | 6 | -4.4 | -3308 | -2989 | +3.23 | -4.7 / -2454 / 1 |
| db=10 | 76 | -14.4 | -5659 | -4085 | +3.01 | -12.7 / -3569 / 22 |
| db=20 | 6 | +2.5 | -1901 | +2207 | +2.66 | -18.0 / -3931 / 1 |
| lots=c15 | 6 | -8.2 | -4353 | -2553 | +3.16 | -8.5 / -3215 / 2 |
| lots=c20 | 70 | -14.4 | -5036 | -3969 | +2.93 | -11.1 / -3555 / 19 |
| lots=c30 | 6 | -4.8 | -3613 | -1831 | +3.20 | -12.3 / -2579 / 2 |
| lots=h | 6 | -12.0 | -9251 | -6042 | +2.59 | -16.6 / -5544 / 1 |
| tr=08 | 4 | +2.3 | -5800 | +3333 | +2.13 | n/a |
| tr=10 | 4 | -2.5 | -1797 | -810 | +3.20 | -1.3 / -2207 / 2 |
| tr=12 | 4 | -62.2 | -8339 | -17857 | +3.31 | n/a |
| tr=15 | 5 | -29.4 | -6990 | -11398 | +3.58 | n/a |
| tr=b | 66 | -12.0 | -4911 | -4085 | +3.04 | -14.4 / -3684 / 22 |
| tr=m | 5 | -7.6 | -6257 | -3998 | +2.51 | n/a |
| half=B | 60 | -16.9 | -5986 | -4620 | +3.12 | -14.4 / -3785 / 19 |
| half=N | 14 | +0.1 | -2737 | +154 | +3.50 | +0.1 / -2202 / 5 |
| half=W | 14 | -7.3 | -1406 | -2716 | -0.30 | n/a |
| fc=M1 | 83 | -11.0 | -4933 | -3816 | +3.12 | -11.1 / -3555 / 23 |
| fc=M2 | 5 | -36.2 | -11406 | -10331 | +2.59 | -36.2 / -6578 / 1 |

### Per cell, scope all (sorted by L3M drawdown cut; L6M, HOLD, GAP/MID and PRE when present)
| cell | L3M | L6M | HOLD | MID(GAP) | PRE | d mean/wk at $4.84 L3M | at $4.84 L6M |
|---|---|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_tcoracle0.9T75 | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | n/a | n/a | +85219 (lots +85/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcremhar05T75 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | n/a | n/a | -11257 (lots +126/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcremhar10T75 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | n/a | n/a | -7570 (lots +85/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcremown10T75 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | n/a | n/a | -6458 (lots +63/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x90 | -1332 $/wk, DD +24.5%, ww +14953, stops 10.27(10.35), b5 98%, w2l 1 | n/a | n/a | n/a | n/a | -1323 (lots -3/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x90 | -2670 $/wk, DD +22.8%, ww +11680, stops 10.42(10.35), b5 96%, w2l 1 | n/a | n/a | n/a | n/a | -2652 (lots -5/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | +900 $/wk, DD +22.5%, ww +10172, stops 10.73(10.35), b5 98%, w2l 0 | n/a | n/a | n/a | n/a | +885 (lots +4/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x40 | +303 $/wk, DD +22.1%, ww +10998, stops 12.40(10.35), b5 90%, w2l 0 | n/a | n/a | n/a | n/a | +291 (lots +4/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40 | +1149 $/wk, DD +20.9%, ww +12597, stops 12.63(10.35), b5 94%, w2l 0 | n/a | n/a | n/a | n/a | +1119 (lots +8/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x60 | +53 $/wk, DD +19.7%, ww +8749, stops 10.12(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +36 (lots +5/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90 | +1830 $/wk, DD +13.7%, ww +8914, stops 7.99(10.35), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | +1810 (lots +5/wk) | n/a |
| M1_75_g10_c1_d10_c20_t08_W | -1835 $/wk, DD +13.2%, ww +6516, stops 9.21(10.35), b5 82%, w2l 0 | n/a | n/a | n/a | n/a | -1901 (lots +18/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x60 | +534 $/wk, DD +12.1%, ww +9089, stops 10.12(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +501 (lots +9/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x60 | +52 $/wk, DD +10.9%, ww +9854, stops 10.73(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | +51 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x40 | -2415 $/wk, DD +9.5%, ww -707, stops 10.27(10.35), b5 104%, w2l 1 | n/a | n/a | n/a | n/a | -2509 (lots +26/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x40 | -112 $/wk, DD +9.5%, ww +4687, stops 10.65(10.35), b5 98%, w2l 0 | n/a | n/a | n/a | n/a | -136 (lots +7/wk) | n/a |
| M1_75_g10_c2_d20_c20_tb_B | -2648 $/wk, DD +9.3%, ww +7285, stops 12.93(10.35), b5 75%, w2l 2 | n/a | n/a | n/a | n/a | -2950 (lots +82/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_pl37_tcq50T75 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | n/a | n/a | -612 (lots +2/wk) | -2263 (lots +7/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x40 | -2043 $/wk, DD +9.1%, ww +4192, stops 12.78(10.35), b5 90%, w2l 0 | n/a | n/a | n/a | n/a | -2057 (lots +4/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | n/a | n/a | -125 (lots +1/wk) | -1221 (lots +3/wk) |
| M1_75_g10_c1_d20_c20_tb_B | -1154 $/wk, DD +7.5%, ww +7015, stops 12.71(10.35), b5 79%, w2l 2 | n/a | n/a | n/a | n/a | -1457 (lots +83/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx60x40 | -358 $/wk, DD +7.4%, ww +3584, stops 10.58(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | -382 (lots +6/wk) | n/a |
| M1_75_g10_c1_d20_c20_tb_N | -288 $/wk, DD +6.1%, ww +6186, stops 13.09(10.35), b5 86%, w2l 2 | n/a | n/a | n/a | n/a | -598 (lots +85/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x40 | +2976 $/wk, DD +4.7%, ww +3924, stops 10.65(10.35), b5 104%, w2l 0 | n/a | n/a | n/a | n/a | +2907 (lots +19/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x60 | -2729 $/wk, DD +3.6%, ww +1891, stops 10.50(10.35), b5 105%, w2l 1 | n/a | n/a | n/a | n/a | -2697 (lots -9/wk) | n/a |
| M1_75_g10_c1_d10_c20_t08_N | -4047 $/wk, DD +3.0%, ww +9786, stops 12.48(10.35), b5 66%, w2l 2 | n/a | n/a | n/a | n/a | -4529 (lots +132/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcq60T50 | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | n/a | n/a | -1658 (lots +29/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x90 | -3725 $/wk, DD +2.3%, ww +1945, stops 10.65(10.35), b5 99%, w2l 1 | n/a | n/a | n/a | n/a | -3690 (lots -10/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcremown05T75 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | n/a | n/a | -8805 (lots +113/wk) | n/a |
| M1_75_g10_c2_d10_c20_t08_B | -11450 $/wk, DD +1.6%, ww +150, stops 12.48(10.35), b5 46%, w2l 4 | n/a | n/a | n/a | n/a | -11882 (lots +118/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x90 | +621 $/wk, DD +1.2%, ww +1574, stops 7.91(10.35), b5 102%, w2l 0 | n/a | n/a | n/a | n/a | +618 (lots +1/wk) | n/a |
| M2_75_g10_c1_d10_c20_tb_W | -3321 $/wk, DD +0.7%, ww -1627, stops 9.82(10.35), b5 88%, w2l 0 | n/a | n/a | n/a | n/a | -3304 (lots -4/wk) | n/a |
| M1_75_g10_c2_d10_c20_tb_N | -2092 $/wk, DD +0.1%, ww +154, stops 14.08(10.35), b5 63%, w2l 2 | n/a | n/a | n/a | n/a | -2446 (lots +97/wk) | n/a |
| M1_75_g10_c1_d10_c15_tb_N | -288 $/wk, DD +0.1%, ww +154, stops 13.85(10.35), b5 74%, w2l 2 | -2202 $/wk, DD +0.1%, ww +154, stops 13.16(10.99), b5 76%, w2l 3 | n/a | n/a | n/a | -620 (lots +91/wk) | -2408 (lots +56/wk) |
| M1_75_g10_c1_d10_c20_tb_N | +236 $/wk, DD +0.1%, ww +154, stops 13.85(10.35), b5 75%, w2l 2 | -1949 $/wk, DD +0.1%, ww +154, stops 13.16(10.99), b5 76%, w2l 3 | n/a | n/a | n/a | -126 (lots +99/wk) | -2172 (lots +61/wk) |
| M1_75_g10_c1_d10_c30_tb_N | +236 $/wk, DD +0.1%, ww +154, stops 13.85(10.35), b5 75%, w2l 2 | n/a | n/a | n/a | n/a | -126 (lots +99/wk) | n/a |
| M1_75_g10_c1_d10_c20_t10_N | +236 $/wk, DD +0.1%, ww +154, stops 13.85(10.35), b5 75%, w2l 2 | -1949 $/wk, DD +0.1%, ww +154, stops 13.16(10.99), b5 76%, w2l 3 | n/a | n/a | n/a | -126 (lots +99/wk) | -2172 (lots +61/wk) |
| M1_75_g10_c1_d10_h_tb_N | -8583 $/wk, DD +0.1%, ww +130, stops 13.16(10.35), b5 52%, w2l 3 | n/a | n/a | n/a | n/a | -8754 (lots +47/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B | +0 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +0 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcq75T75 | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | +176 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_tcq50T75 | -17 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -17 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x40 | +23 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 98%, w2l 0 | n/a | n/a | n/a | n/a | +19 (lots +1/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x60 | +201 $/wk, DD +0.0%, ww +0, stops 10.12(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +201 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x90 | +112 $/wk, DD +0.0%, ww +0, stops 9.97(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +112 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx60x40 | -307 $/wk, DD +0.0%, ww +0, stops 10.58(10.35), b5 97%, w2l 0 | n/a | n/a | n/a | n/a | -312 (lots +1/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx60x90 | -9 $/wk, DD +0.0%, ww +0, stops 10.12(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | -9 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x40 | -265 $/wk, DD +0.0%, ww +0, stops 10.65(10.35), b5 98%, w2l 0 | n/a | n/a | n/a | n/a | -269 (lots +1/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x60 | -138 $/wk, DD +0.0%, ww +0, stops 10.50(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | -138 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x90 | -323 $/wk, DD +0.0%, ww +0, stops 10.27(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | -323 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcq50T75 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | +1452 (lots +9/wk) | +694 (lots +7/wk) |
| M1_50_g00_c1_d10_c20_tb_B_tcq50T75skip | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | +1410 (lots +9/wk) | n/a |
| M1_75_g10_c1_d10_c20_tm_N | -3553 $/wk, DD -0.7%, ww +1066, stops 13.16(10.35), b5 79%, w2l 3 | n/a | n/a | n/a | n/a | -3971 (lots +114/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x40 | +76 $/wk, DD -1.1%, ww -816, stops 10.58(10.35), b5 97%, w2l 0 | n/a | n/a | n/a | n/a | +50 (lots +7/wk) | n/a |
| M1_75_g10_c1_d10_c20_t08_B | -7554 $/wk, DD -1.1%, ww +150, stops 12.48(10.35), b5 61%, w2l 3 | n/a | n/a | n/a | n/a | -8006 (lots +123/wk) | n/a |
| M1_50_g15_c2_d20_c20_tb_B | -5730 $/wk, DD -1.2%, ww -1940, stops 14.76(10.35), b5 63%, w2l 2 | n/a | n/a | n/a | n/a | -6331 (lots +164/wk) | n/a |
| M1_75_g10_c1_d20_c20_tb_W | -161 $/wk, DD -1.3%, ww -1772, stops 9.97(10.35), b5 94%, w2l 0 | n/a | n/a | n/a | n/a | -153 (lots -2/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x60 | -633 $/wk, DD -1.7%, ww -907, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | -634 (lots +0/wk) | n/a |
| M1_75_g10_c2_d10_c30_tb_B | -4517 $/wk, DD -1.8%, ww -675, stops 13.62(10.35), b5 56%, w2l 2 | n/a | n/a | n/a | n/a | -4856 (lots +93/wk) | n/a |
| M1_75_g10_c1_d00_c20_tb_N | +84 $/wk, DD -1.8%, ww -146, stops 13.85(10.35), b5 71%, w2l 2 | n/a | n/a | n/a | n/a | -280 (lots +99/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x90 | +1557 $/wk, DD -2.1%, ww +399, stops 7.99(10.35), b5 105%, w2l 0 | n/a | n/a | n/a | n/a | +1551 (lots +2/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x60 | +30 $/wk, DD -2.1%, ww -1079, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +31 (lots -0/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_B | -2708 $/wk, DD -2.3%, ww -945, stops 13.47(10.35), b5 69%, w2l 2 | -1372 $/wk, DD -2.3%, ww -945, stops 11.91(10.99), b5 52%, w2l 2 | n/a | n/a | n/a | -3047 (lots +92/wk) | -1483 (lots +30/wk) |
| M1_75_g10_c1_d10_c30_tb_B | -2708 $/wk, DD -2.3%, ww -945, stops 13.47(10.35), b5 69%, w2l 2 | -1372 $/wk, DD -2.3%, ww -945, stops 11.91(10.99), b5 52%, w2l 2 | n/a | n/a | n/a | -3047 (lots +92/wk) | -1483 (lots +30/wk) |
| M1_75_g10_c1_d10_c20_t10_B | -2708 $/wk, DD -2.3%, ww -945, stops 13.47(10.35), b5 69%, w2l 2 | n/a | n/a | n/a | n/a | -3047 (lots +92/wk) | n/a |
| M1_75_g10_c2_d10_c20_tb_B | -4536 $/wk, DD -2.7%, ww -675, stops 13.62(10.35), b5 58%, w2l 2 | -2465 $/wk, DD -2.7%, ww -675, stops 11.79(10.99), b5 44%, w2l 2 | n/a | n/a | n/a | -4867 (lots +90/wk) | -2570 (lots +29/wk) |
| M1_75_g10_c2_d10_c20_t10_B | -4536 $/wk, DD -2.7%, ww -675, stops 13.62(10.35), b5 58%, w2l 2 | -2465 $/wk, DD -2.7%, ww -675, stops 11.79(10.99), b5 44%, w2l 2 | n/a | n/a | n/a | -4867 (lots +90/wk) | -2570 (lots +29/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x40 | -1067 $/wk, DD -3.6%, ww -5552, stops 10.58(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -1132 (lots +18/wk) | n/a |
| M1_75_g10_c1_d00_c20_tb_W | -1254 $/wk, DD -4.0%, ww -3816, stops 9.89(10.35), b5 95%, w2l 0 | n/a | n/a | n/a | n/a | -1238 (lots -4/wk) | n/a |
| M1_75_g10_c2_d00_c20_tb_B | -4332 $/wk, DD -4.2%, ww -1893, stops 13.70(10.35), b5 53%, w2l 2 | n/a | n/a | n/a | n/a | -4664 (lots +91/wk) | n/a |
| M1_75_g10_c1_d00_c20_tb_B | -2284 $/wk, DD -4.7%, ww -2163, stops 13.47(10.35), b5 64%, w2l 2 | -2454 $/wk, DD -4.7%, ww -2163, stops 11.79(10.99), b5 50%, w2l 2 | n/a | n/a | n/a | -2623 (lots +93/wk) | -2561 (lots +29/wk) |
| M1_50_g00_c1_d10_c20_tb_B_pl23_tcq50T75 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | n/a | n/a | -871 (lots +3/wk) | -1376 (lots +5/wk) |
| M1_50_g00_c1_d10_c20_tb_B_plR1_tcq50T75 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | n/a | n/a | -670 (lots +4/wk) | -1715 (lots +7/wk) |
| M1_75_g10_c2_d10_c15_tb_B | -5625 $/wk, DD -5.8%, ww -2391, stops 13.54(10.35), b5 58%, w2l 2 | n/a | n/a | n/a | n/a | -5914 (lots +79/wk) | n/a |
| M1_75_g10_c2_d10_c20_tb_W | -475 $/wk, DD -6.8%, ww -2446, stops 10.04(10.35), b5 96%, w2l 0 | n/a | n/a | n/a | n/a | -464 (lots -3/wk) | n/a |
| M1_75_g10_c2_d10_c20_tm_B | -6531 $/wk, DD -7.1%, ww -3998, stops 12.86(10.35), b5 71%, w2l 3 | n/a | n/a | n/a | n/a | -6940 (lots +112/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x90 | -34 $/wk, DD -7.2%, ww -5579, stops 10.50(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -24 (lots -3/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_W | -885 $/wk, DD -7.3%, ww -2716, stops 10.04(10.35), b5 95%, w2l 0 | n/a | n/a | n/a | n/a | -873 (lots -3/wk) | n/a |
| M1_75_g10_c1_d10_c15_tb_W | -885 $/wk, DD -7.3%, ww -2716, stops 10.04(10.35), b5 95%, w2l 0 | n/a | n/a | n/a | n/a | -873 (lots -3/wk) | n/a |
| M1_75_g10_c1_d10_c30_tb_W | -885 $/wk, DD -7.3%, ww -2716, stops 10.04(10.35), b5 95%, w2l 0 | n/a | n/a | n/a | n/a | -873 (lots -3/wk) | n/a |
| M1_75_g10_c1_d10_c20_t10_W | -885 $/wk, DD -7.3%, ww -2716, stops 10.04(10.35), b5 95%, w2l 0 | n/a | n/a | n/a | n/a | -873 (lots -3/wk) | n/a |
(59 more cells in /mnt/l2/l2vast/_dial10/cells.json)

### Narrow-only and wide-only for the leading cells (item 8; same cell, half B / N / W)
| base cell | half | L3M | L6M |
|---|---|---|---|
| (the N/W variants exist for g1 c1 H50/H75; the finalists get theirs from wave 2) | | | |

### Per book and per session (item 2): effect of the best whole-system cell on each book x session, and the best setting per book x session
Slice of the exact trade tables (books interact through day locks and caps, so single-book cells in the next table are the clean test). For every book x session the cell with the largest drawdown cut inside the tolerant mean gate in L3M (and in L6M when scored) is listed; "stays fixed" = no cell cuts drawdown inside the gate there.
| book | session | trades L3M | best cell | L3M | L6M | verdict |
|---|---|---|---|---|---|---|
| A7 | asia | 160 | M1_75_g10_c1_d10_c20_t08_N | +320 $/wk, DD +39.7%, ww +2974, stops 5.25(4.03), b5 6%, w2l 4 | n/a | L3M only |
| H7 | asia | 67 | M1_75_g10_c1_d10_c20_t15_N | +547 $/wk, DD +20.8%, ww -41, stops 0.53(0.23), b5 96%, w2l 3 | n/a | L3M only |
| H7 | nyam | 17 | M1_50_g15_c2_d10_c20_tm_B | +303 $/wk, DD +65.0%, ww +597, stops 0.15(0.38), b5 88%, w2l 0 | n/a | L3M only |
| K7 | asia | 333 | M1_75_g10_c2_d10_c20_t08_B | +1214 $/wk, DD +7.3%, ww +266, stops 0.15(0.00), b5 105%, w2l 1 | n/a | L3M only |
| K7 | london | 210 | M1_75_g10_c1_d10_c20_t12_N | +773 $/wk, DD +24.7%, ww +5048, stops 0.30(0.30), b5 82%, w2l 1 | n/a | L3M only |
| K7 | nyam | 88 | M1_50_g15_c2_d20_c20_tb_B | +1107 $/wk, DD +80.1%, ww +2337, stops 0.00(0.00), b5 86%, w2l 1 | n/a | L3M only |
| K7 | nypm | 56 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| M7 | london | 248 | M1_75_g10_c1_d10_c20_t12_W | +268 $/wk, DD +10.6%, ww +559, stops 0.76(0.91), b5 102%, w2l 0 | n/a | L3M only |
| M7 | nyam | 88 | M1_75_g20_c1_d10_c20_tb_B | +242 $/wk, DD +52.6%, ww +1195, stops 0.30(0.23), b5 35%, w2l 0 | n/a | L3M only |
| P7 | asia | 243 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| P7 | london | 166 | M1_50_g15_c2_d10_c20_tb_B | +619 $/wk, DD +45.5%, ww +3969, stops 0.15(0.08), b5 74%, w2l 1 | n/a | L3M only |
| P7 | nyam | 58 | M1_75_g10_c1_d10_h_tb_N | +1506 $/wk, DD +74.0%, ww +3983, stops 0.08(0.38), b5 23%, w2l 1 | n/a | L3M only |
| U7 | asia | 72 | M1_75_g10_c1_d10_h_tb_N | +654 $/wk, DD +37.1%, ww +1407, stops 1.90(1.83), b5 88%, w2l 1 | n/a | L3M only |
| U7 | london | 49 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |

Single-book and book x session cells (wave 3, clean test of item 2; same config as the wave-2 best; vs JN05W2 on the same book/session slice):
| cell | slice | L3M | L6M |
|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_tcq50T75 | A7/as | -17 $/wk, DD +0.0%, ww +0, stops 4.03(4.03), b5 98%, w2l 0 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40 | A7/as | +205 $/wk, DD +24.7%, ww +2588, stops 6.62(4.03), b5 38%, w2l 2 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | A7/as | -373 $/wk, DD -2.3%, ww +1411, stops 4.49(4.03), b5 47%, w2l 2 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90 | A7/as | -20 $/wk, DD -34.2%, ww -532, stops 1.52(4.03), b5 113%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x40 | A7/as | +879 $/wk, DD +38.1%, ww +2338, stops 6.24(4.03), b5 67%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x90 | A7/as | -23 $/wk, DD -68.2%, ww -4785, stops 1.45(4.03), b5 133%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x40 | A7/as | -159 $/wk, DD -54.1%, ww -2126, stops 6.54(4.03), b5 75%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x60 | A7/as | -614 $/wk, DD -87.0%, ww -2571, stops 4.41(4.03), b5 89%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x90 | A7/as | -944 $/wk, DD -175.4%, ww -3751, stops 1.37(4.03), b5 73%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x40 | H7/as | -350 $/wk, DD -97.5%, ww -2100, stops 0.53(0.23), b5 115%, w2l 4 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x60 | H7/as | -311 $/wk, DD -42.9%, ww -1200, stops 0.30(0.23), b5 65%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x90 | H7/as | -393 $/wk, DD +47.1%, ww +341, stops 0.23(0.23), b5 52%, w2l 2 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx60x40 | H7/as | -205 $/wk, DD -91.8%, ww -2847, stops 0.53(0.23), b5 167%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx60x90 | H7/as | -720 $/wk, DD +4.5%, ww -1633, stops 0.23(0.23), b5 21%, w2l 5 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x40 | H7/as | +151 $/wk, DD -129.9%, ww -2100, stops 0.61(0.23), b5 215%, w2l 4 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x60 | H7/as | -336 $/wk, DD -59.3%, ww -2623, stops 0.30(0.23), b5 116%, w2l 4 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x90 | H7/as | -1014 $/wk, DD -17.5%, ww -4123, stops 0.30(0.23), b5 41%, w2l 6 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x40 | H7/am | +23 $/wk, DD -31.6%, ww +1516, stops 0.61(0.61), b5 120%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x60 | H7/am | +201 $/wk, DD +13.6%, ww +1980, stops 0.38(0.61), b5 100%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x90 | H7/am | +112 $/wk, DD +1.8%, ww +1980, stops 0.23(0.61), b5 94%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx60x40 | H7/am | -307 $/wk, DD -106.7%, ww -1634, stops 0.84(0.61), b5 129%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx60x90 | H7/am | -9 $/wk, DD -0.5%, ww +1614, stops 0.38(0.61), b5 91%, w2l 0 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x40 | H7/am | -265 $/wk, DD -106.7%, ww -1634, stops 0.91(0.61), b5 130%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x60 | H7/am | -138 $/wk, DD -39.2%, ww +0, stops 0.76(0.61), b5 98%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x90 | H7/am | -323 $/wk, DD -66.9%, ww +1270, stops 0.53(0.61), b5 85%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x40 | K7/as | +2200 $/wk, DD -27.4%, ww -2748, stops 0.08(0.00), b5 154%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x60 | K7/as | +1019 $/wk, DD -23.2%, ww -2510, stops 0.00(0.00), b5 89%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x90 | K7/as | -1386 $/wk, DD -74.1%, ww -8079, stops 0.08(0.00), b5 26%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x40 | K7/as | +2577 $/wk, DD -42.7%, ww -6350, stops 0.15(0.00), b5 161%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x90 | K7/as | -1015 $/wk, DD -79.0%, ww -2751, stops 0.00(0.00), b5 47%, w2l 2 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x40 | K7/as | +2627 $/wk, DD -107.1%, ww -13878, stops 0.00(0.00), b5 118%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x60 | K7/as | +42 $/wk, DD -42.9%, ww -5353, stops 0.00(0.00), b5 36%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x90 | K7/as | -637 $/wk, DD -7.8%, ww -3407, stops 0.00(0.00), b5 20%, w2l 3 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x40 | K7/lo | -636 $/wk, DD -128.9%, ww -1301, stops 0.53(0.30), b5 -16%, w2l 5 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x60 | K7/lo | +294 $/wk, DD +29.6%, ww -309, stops 0.08(0.30), b5 44%, w2l 2 | n/a |

### Leads (tolerant gate in every scored window incl. L3M and L6M, DD cut > 0 in some window)
| cell | scope | L6M DD cut % | L6M d mean | windows | W44 removed L3M / L6M |
|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | nypm | +16.5 | +245 | 2 | +245 $/wk, DD +16.5%, ww +185, stops 0.08(0.08), b5 131%, w2l 1 / +245 $/wk, DD +16.5%, ww +185, stops 0.08(0.08), b5 95%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | nyam | +8.0 | +173 | 2 | +622 $/wk, DD +14.2%, ww +0, stops 1.37(1.29), b5 103%, w2l 1 / +173 $/wk, DD +8.0%, ww +2555, stops 1.71(1.67), b5 91%, w2l 2 |

### Placebos beside the finalists (forecast shifted 11 / 23 / 37 sessions at the same clock; random other session at the same clock), scope all, L6M (a real lead must beat all of them)
| finalist | real | pl11 | pl23 | pl37 | random |
|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | pending | pending | pending | pending |
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | pending | pending | pending | pending |

### Combined with the chop call and the trend-day call (item 7)
| cell | mode | L3M | L6M |
|---|---|---|---|

### FOR THE LIVE BUILD: what D7 needs at the signal second
1. Own 1-minute NQ bars only (closed bars up to the signal second): range and realised vol of the last 15/30/60/120 min; the same offset-into-session range over the previous 20 sessions (median); the range of the previous 5 and 20 sessions of the same session type; range so far in the current session; last close. D7 computes all of these itself from its own bars (preferred). 2. A small coefficient table (per session: 14 weights, mean, sd, intercept for the median-horizon and 75th-pct models) plus per book+session H50/H75 and ref EM, refit every 14 days: a static file pushed from the box every 2 weeks (the only file). 3. Nothing intraday from the box for M1. M2 (T-RANGE2 session forecast + calendar flags) needs the T-RANGE2 file and the event calendar at the session start: ranks below an equal M1 version. 4. The chop-call and trend-day cells additionally need those call files (not computable from D7 bars alone): rank below the bars-only version.

### Reading
Drawdown first; a result needs the gate in recent AND older windows and has to beat the placebos. Cells that cut drawdown only through L3M, or only with full stops up, are not leads. Expected move forecast quality (table above) is a forecasting result scored on all 43 months; the exact cells decide whether it makes a better bracket. No PASS claim.
