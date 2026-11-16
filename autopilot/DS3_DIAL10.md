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
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 14 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

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
**VERDICT (plain, not a PASS): 373 of 591 registered cells scored through L3M, 194 through L6M, 77 through HOLD; 22 (cell,scope) leads pass the tolerant gate in every scored window (5 at scope all) - before placebo; this is the GLOBAL one-setting-for-all-books family only, the per-book per-session test (B1) is in the section above and still running. Best L3M cell inside the mean gate: M1_50_g00_c1_d10_c20_tb_B_tcoracle0.9T75 (DD +67.0%, +85531 $/wk).**

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
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40 | +147 $/wk, DD +62.9%, ww +29432, stops 9.89(10.35), b5 73%, w2l 0 | -1909 $/wk, DD +62.3%, ww +26117, stops 11.07(10.99), b5 64%, w2l 0 | -1834 $/wk, DD +27.0%, ww +21859, stops 10.64(10.66), b5 64%, w2l 5 | -4651 $/wk, DD +14.9%, ww +28035, stops 10.54(10.88), b5 62%, w2l 2 | -4868 $/wk, DD +13.1%, ww +23441, stops 9.23(9.31), b5 48%, w2l 3 | +307 (lots -44/wk) | -1680 (lots -63/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s102 | -1113 $/wk, DD +61.7%, ww +29033, stops 10.12(10.35), b5 72%, w2l 0 | -3565 $/wk, DD +56.3%, ww +23942, stops 11.03(10.99), b5 64%, w2l 0 | -2899 $/wk, DD +27.2%, ww +16532, stops 10.53(10.66), b5 69%, w2l 4 | -5782 $/wk, DD +14.2%, ww +13310, stops 10.20(10.88), b5 70%, w2l 2 | n/a | -936 (lots -48/wk) | -3315 (lots -68/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s103 | -1046 $/wk, DD +60.8%, ww +23767, stops 10.27(10.35), b5 83%, w2l 0 | -3084 $/wk, DD +60.1%, ww +23767, stops 10.80(10.99), b5 72%, w2l 0 | n/a | n/a | n/a | -861 (lots -50/wk) | -2824 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p60 | +1046 $/wk, DD +60.0%, ww +25364, stops 12.17(10.35), b5 83%, w2l 0 | -2165 $/wk, DD +58.3%, ww +25364, stops 12.86(10.99), b5 67%, w2l 0 | -2892 $/wk, DD +20.8%, ww +15454, stops 12.56(10.66), b5 72%, w2l 4 | -4796 $/wk, DD +12.5%, ww +12232, stops 12.40(10.88), b5 75%, w2l 2 | n/a | +1220 (lots -47/wk) | -1918 (lots -68/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s102 | -1508 $/wk, DD +58.7%, ww +21213, stops 10.27(10.35), b5 78%, w2l 0 | -3257 $/wk, DD +58.7%, ww +21213, stops 10.80(10.99), b5 70%, w2l 0 | n/a | n/a | n/a | -1320 (lots -51/wk) | -2996 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60 | -2959 $/wk, DD +57.9%, ww +21434, stops 10.04(10.35), b5 75%, w2l 1 | -4470 $/wk, DD +57.9%, ww +21434, stops 10.65(10.99), b5 67%, w2l 1 | -3794 $/wk, DD +17.3%, ww +24303, stops 10.45(10.66), b5 74%, w2l 5 | -2765 $/wk, DD +31.7%, ww +24273, stops 10.29(10.88), b5 70%, w2l 2 | n/a | -2780 (lots -49/wk) | -4217 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p81 | -1472 $/wk, DD +57.2%, ww +23874, stops 10.35(10.35), b5 80%, w2l 0 | -3618 $/wk, DD +57.2%, ww +23874, stops 10.96(10.99), b5 71%, w2l 0 | n/a | n/a | n/a | -1283 (lots -52/wk) | -3362 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p60 | -614 $/wk, DD +57.1%, ww +23582, stops 12.10(10.35), b5 76%, w2l 0 | -3092 $/wk, DD +57.1%, ww +23582, stops 12.86(10.99), b5 69%, w2l 0 | -3044 $/wk, DD +11.4%, ww +20993, stops 12.24(10.66), b5 71%, w2l 4 | -3735 $/wk, DD +6.4%, ww +24515, stops 12.06(10.88), b5 76%, w2l 2 | n/a | -455 (lots -43/wk) | -2858 (lots -64/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s103 | +340 $/wk, DD +56.9%, ww +28027, stops 10.04(10.35), b5 80%, w2l 0 | -1838 $/wk, DD +56.9%, ww +28027, stops 10.99(10.99), b5 69%, w2l 0 | -2711 $/wk, DD +16.7%, ww +21859, stops 10.66(10.66), b5 64%, w2l 4 | -4539 $/wk, DD +29.6%, ww +28238, stops 10.46(10.88), b5 61%, w2l 2 | n/a | +526 (lots -51/wk) | -1592 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s101 | -1656 $/wk, DD +56.9%, ww +23969, stops 10.27(10.35), b5 77%, w2l 0 | -3525 $/wk, DD +56.9%, ww +23969, stops 10.77(10.99), b5 69%, w2l 0 | -3190 $/wk, DD +20.7%, ww +24703, stops 10.51(10.66), b5 74%, w2l 5 | -3398 $/wk, DD +30.1%, ww +26037, stops 10.37(10.88), b5 70%, w2l 2 | n/a | -1470 (lots -51/wk) | -3268 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2 | -1570 $/wk, DD +56.8%, ww +22941, stops 10.27(10.35), b5 77%, w2l 0 | n/a | n/a | n/a | n/a | -1375 (lots -53/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s2p92 | -3013 $/wk, DD +56.6%, ww +21370, stops 9.97(10.35), b5 73%, w2l 0 | -2983 $/wk, DD +56.6%, ww +21370, stops 10.77(10.99), b5 75%, w2l 0 | -2111 $/wk, DD +9.0%, ww +23322, stops 10.30(10.66), b5 77%, w2l 4 | +177 $/wk, DD +35.5%, ww +20541, stops 9.87(10.88), b5 75%, w2l 1 | n/a | -2825 (lots -51/wk) | -2731 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s2p81 | -3135 $/wk, DD +56.1%, ww +21341, stops 9.97(10.35), b5 72%, w2l 0 | -3478 $/wk, DD +56.1%, ww +21341, stops 10.84(10.99), b5 74%, w2l 0 | n/a | n/a | n/a | -2941 (lots -53/wk) | -3221 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s103 | -1004 $/wk, DD +56.0%, ww +23340, stops 11.41(10.35), b5 80%, w2l 0 | -2950 $/wk, DD +56.0%, ww +23340, stops 12.36(10.99), b5 75%, w2l 0 | -3088 $/wk, DD +12.9%, ww +21714, stops 12.43(10.66), b5 71%, w2l 3 | -4265 $/wk, DD +29.0%, ww +21318, stops 12.40(10.88), b5 66%, w2l 1 | n/a | -820 (lots -50/wk) | -2696 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 | -722 $/wk, DD +56.0%, ww +22141, stops 10.27(10.35), b5 83%, w2l 0 | -2640 $/wk, DD +56.0%, ww +22141, stops 10.88(10.99), b5 76%, w2l 0 | n/a | n/a | n/a | -531 (lots -52/wk) | -2380 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s103 | -1044 $/wk, DD +56.0%, ww +22541, stops 10.27(10.35), b5 79%, w2l 0 | -2789 $/wk, DD +56.0%, ww +22541, stops 10.88(10.99), b5 74%, w2l 0 | -3125 $/wk, DD +21.6%, ww +24171, stops 10.55(10.66), b5 70%, w2l 4 | -4601 $/wk, DD +27.9%, ww +20949, stops 10.37(10.88), b5 65%, w2l 2 | n/a | -853 (lots -52/wk) | -2527 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s101 | -368 $/wk, DD +55.8%, ww +21377, stops 11.72(10.35), b5 85%, w2l 0 | -2517 $/wk, DD +55.8%, ww +21377, stops 12.59(10.99), b5 76%, w2l 0 | -2683 $/wk, DD +16.7%, ww +23238, stops 12.56(10.66), b5 74%, w2l 4 | -3846 $/wk, DD +29.8%, ww +21359, stops 11.98(10.88), b5 69%, w2l 2 | n/a | -185 (lots -50/wk) | -2265 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p35 | -243 $/wk, DD +55.5%, ww +24610, stops 11.34(10.35), b5 84%, w2l 0 | -2131 $/wk, DD +55.5%, ww +24610, stops 12.10(10.99), b5 69%, w2l 0 | -2869 $/wk, DD +17.5%, ww +17265, stops 11.64(10.66), b5 72%, w2l 4 | -5139 $/wk, DD +14.1%, ww +14042, stops 11.22(10.88), b5 69%, w2l 2 | n/a | -61 (lots -50/wk) | -1881 (lots -68/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p35 | -348 $/wk, DD +55.4%, ww +24399, stops 11.49(10.35), b5 78%, w2l 0 | -2404 $/wk, DD +55.4%, ww +24399, stops 11.83(10.99), b5 70%, w2l 0 | -2995 $/wk, DD +12.7%, ww +22396, stops 11.45(10.66), b5 71%, w2l 4 | -4448 $/wk, DD +14.3%, ww +21310, stops 11.39(10.88), b5 69%, w2l 2 | n/a | -172 (lots -48/wk) | -2158 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p81 | -1229 $/wk, DD +55.1%, ww +20887, stops 12.55(10.35), b5 75%, w2l 0 | -3280 $/wk, DD +55.1%, ww +20887, stops 13.43(10.99), b5 69%, w2l 0 | -3325 $/wk, DD +5.2%, ww +20301, stops 12.73(10.66), b5 72%, w2l 5 | -3386 $/wk, DD +14.1%, ww +32710, stops 12.48(10.88), b5 72%, w2l 3 | n/a | -1073 (lots -43/wk) | -3054 (lots -62/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s101 | -3497 $/wk, DD +54.6%, ww +24004, stops 12.10(10.35), b5 74%, w2l 2 | -4579 $/wk, DD +54.6%, ww +24004, stops 12.63(10.99), b5 71%, w2l 2 | -3961 $/wk, DD +24.1%, ww +28381, stops 11.85(10.66), b5 63%, w2l 7 | -2301 $/wk, DD +34.8%, ww +28998, stops 11.55(10.88), b5 70%, w2l 2 | n/a | -3304 (lots -53/wk) | -4318 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40 | -46 $/wk, DD +54.5%, ww +21776, stops 13.39(10.35), b5 85%, w2l 0 | -2571 $/wk, DD +54.5%, ww +21776, stops 14.04(10.99), b5 75%, w2l 0 | -2954 $/wk, DD +7.7%, ww +19997, stops 14.27(10.66), b5 72%, w2l 4 | -5116 $/wk, DD +31.6%, ww +21318, stops 13.83(10.88), b5 63%, w2l 2 | n/a | +123 (lots -46/wk) | -2330 (lots -66/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s102 | -380 $/wk, DD +54.5%, ww +21138, stops 11.87(10.35), b5 82%, w2l 0 | -2761 $/wk, DD +54.5%, ww +21138, stops 12.52(10.99), b5 73%, w2l 0 | -2969 $/wk, DD +13.3%, ww +22473, stops 12.31(10.66), b5 73%, w2l 5 | -4098 $/wk, DD +29.1%, ww +21186, stops 11.98(10.88), b5 68%, w2l 2 | n/a | -199 (lots -49/wk) | -2510 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60 | -452 $/wk, DD +54.5%, ww +22540, stops 10.27(10.35), b5 83%, w2l 0 | -2683 $/wk, DD +54.5%, ww +22540, stops 10.88(10.99), b5 74%, w2l 0 | n/a | n/a | -4813 $/wk, DD +23.4%, ww +24830, stops 9.05(9.31), b5 55%, w2l 1 | -265 (lots -51/wk) | -2425 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s102 | -649 $/wk, DD +54.5%, ww +22018, stops 10.27(10.35), b5 82%, w2l 0 | -2830 $/wk, DD +54.5%, ww +22018, stops 10.88(10.99), b5 73%, w2l 0 | -2886 $/wk, DD +18.7%, ww +23535, stops 10.55(10.66), b5 72%, w2l 4 | -3961 $/wk, DD +30.6%, ww +20671, stops 10.37(10.88), b5 69%, w2l 2 | n/a | -459 (lots -52/wk) | -2569 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s101 | -1282 $/wk, DD +54.1%, ww +21959, stops 10.12(10.35), b5 74%, w2l 0 | -3339 $/wk, DD +54.1%, ww +21959, stops 11.03(10.99), b5 69%, w2l 0 | -2502 $/wk, DD +31.2%, ww +23532, stops 10.55(10.66), b5 74%, w2l 5 | -4372 $/wk, DD +24.6%, ww +28433, stops 10.46(10.88), b5 63%, w2l 3 | n/a | -1104 (lots -49/wk) | -3093 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s1p81 | +233 $/wk, DD +54.0%, ww +24228, stops 10.50(10.35), b5 85%, w2l 0 | -2776 $/wk, DD +54.0%, ww +24228, stops 10.99(10.99), b5 70%, w2l 0 | n/a | n/a | n/a | +419 (lots -51/wk) | -2520 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p92 | -1206 $/wk, DD +53.5%, ww +23074, stops 10.20(10.35), b5 84%, w2l 0 | -3692 $/wk, DD +53.5%, ww +23074, stops 10.84(10.99), b5 73%, w2l 0 | n/a | n/a | n/a | -1021 (lots -51/wk) | -3439 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p35 | +197 $/wk, DD +53.3%, ww +22115, stops 11.26(10.35), b5 81%, w2l 0 | -1404 $/wk, DD +53.3%, ww +22115, stops 12.02(10.99), b5 75%, w2l 0 | -2094 $/wk, DD +10.8%, ww +23494, stops 11.51(10.66), b5 69%, w2l 4 | -2802 $/wk, DD +33.1%, ww +20272, stops 11.72(10.88), b5 68%, w2l 2 | n/a | +381 (lots -50/wk) | -1157 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s1p92 | +305 $/wk, DD +53.0%, ww +23711, stops 10.50(10.35), b5 85%, w2l 0 | -2125 $/wk, DD +53.0%, ww +23711, stops 10.99(10.99), b5 71%, w2l 0 | -2534 $/wk, DD +19.5%, ww +15897, stops 10.57(10.66), b5 74%, w2l 3 | -4358 $/wk, DD +21.4%, ww +12675, stops 10.20(10.88), b5 66%, w2l 2 | n/a | +490 (lots -51/wk) | -1873 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p81 | -2961 $/wk, DD +52.9%, ww +22118, stops 12.17(10.35), b5 72%, w2l 0 | -2053 $/wk, DD +52.9%, ww +22118, stops 14.04(10.99), b5 74%, w2l 0 | -1887 $/wk, DD +7.5%, ww +18242, stops 12.93(10.66), b5 72%, w2l 4 | -891 $/wk, DD +29.1%, ww +15019, stops 12.14(10.88), b5 72%, w2l 2 | n/a | -2801 (lots -44/wk) | -1831 (lots -61/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p60 | -1042 $/wk, DD +52.9%, ww +22118, stops 11.95(10.35), b5 75%, w2l 0 | -1803 $/wk, DD +52.9%, ww +22118, stops 13.01(10.99), b5 75%, w2l 0 | -1596 $/wk, DD +12.9%, ww +24560, stops 12.25(10.66), b5 74%, w2l 4 | -509 $/wk, DD +24.6%, ww +23875, stops 12.06(10.88), b5 69%, w2l 1 | n/a | -873 (lots -46/wk) | -1567 (lots -65/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s102 | -3195 $/wk, DD +52.3%, ww +22798, stops 11.64(10.35), b5 78%, w2l 0 | -4172 $/wk, DD +52.3%, ww +22798, stops 12.25(10.99), b5 69%, w2l 0 | -4165 $/wk, DD +20.2%, ww +19938, stops 11.55(10.66), b5 65%, w2l 4 | -5250 $/wk, DD +18.6%, ww +16715, stops 11.72(10.88), b5 72%, w2l 2 | n/a | -2993 (lots -55/wk) | -3911 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s103 | -2805 $/wk, DD +46.3%, ww +23610, stops 11.64(10.35), b5 78%, w2l 1 | -3489 $/wk, DD +46.3%, ww +23610, stops 12.21(10.99), b5 73%, w2l 1 | -3043 $/wk, DD +21.3%, ww +28704, stops 11.62(10.66), b5 72%, w2l 5 | -2200 $/wk, DD +40.3%, ww +26988, stops 11.22(10.88), b5 70%, w2l 2 | n/a | -2607 (lots -54/wk) | -3228 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p81 | +50 $/wk, DD +45.5%, ww +22324, stops 12.71(10.35), b5 83%, w2l 1 | -2825 $/wk, DD +45.5%, ww +22324, stops 13.66(10.99), b5 64%, w2l 1 | -3184 $/wk, DD +13.9%, ww +20411, stops 13.19(10.66), b5 72%, w2l 5 | -5038 $/wk, DD +14.0%, ww +17189, stops 12.90(10.88), b5 73%, w2l 2 | n/a | +222 (lots -47/wk) | -2581 (lots -66/wk) |
| M1_50_g00_c1_d10_c20_tb_B_tcremhar05T75 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | n/a | n/a | -11257 (lots +126/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcremhar10T75 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | n/a | n/a | -7570 (lots +85/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40 | -3987 $/wk, DD +37.3%, ww +22661, stops 13.70(10.35), b5 67%, w2l 1 | -4120 $/wk, DD +37.3%, ww +22661, stops 14.57(10.99), b5 71%, w2l 1 | -4168 $/wk, DD +21.5%, ww +26230, stops 13.37(10.66), b5 63%, w2l 5 | -5059 $/wk, DD +15.2%, ww +23008, stops 13.16(10.88), b5 70%, w2l 2 | n/a | -3808 (lots -49/wk) | -3874 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_tcremown10T75 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | n/a | n/a | -6458 (lots +63/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s1 | +930 $/wk, DD +25.4%, ww +10509, stops 11.49(10.35), b5 96%, w2l 0 | +284 $/wk, DD +25.4%, ww +7146, stops 12.17(10.99), b5 100%, w2l 0 | -437 $/wk, DD -5.2%, ww +3352, stops 11.66(10.66), b5 95%, w2l 4 | -575 $/wk, DD +2.2%, ww +6298, stops 11.89(10.88), b5 102%, w2l 2 | -868 $/wk, DD +3.1%, ww -1, stops 9.69(9.31), b5 93%, w2l 0 | +912 (lots +5/wk) | +275 (lots +3/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x90 | -1332 $/wk, DD +24.5%, ww +14953, stops 10.27(10.35), b5 98%, w2l 1 | -2641 $/wk, DD +24.5%, ww +6860, stops 10.88(10.99), b5 98%, w2l 1 | n/a | n/a | n/a | -1323 (lots -3/wk) | -2637 (lots -1/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x90 | -2670 $/wk, DD +22.8%, ww +11680, stops 10.42(10.35), b5 96%, w2l 1 | -1093 $/wk, DD +22.8%, ww +11680, stops 11.03(10.99), b5 98%, w2l 1 | n/a | n/a | n/a | -2652 (lots -5/wk) | -1081 (lots -3/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | +900 $/wk, DD +22.5%, ww +10172, stops 10.73(10.35), b5 98%, w2l 0 | +710 $/wk, DD +22.5%, ww +5127, stops 11.34(10.99), b5 98%, w2l 1 | +948 $/wk, DD +5.3%, ww +2668, stops 10.85(10.66), b5 96%, w2l 1 | +597 $/wk, DD +2.4%, ww -554, stops 10.96(10.88), b5 106%, w2l 0 | -203 $/wk, DD +2.9%, ww +1125, stops 9.26(9.31), b5 98%, w2l 0 | +885 (lots +4/wk) | +692 (lots +5/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x40 | +303 $/wk, DD +22.1%, ww +10998, stops 12.40(10.35), b5 90%, w2l 0 | +708 $/wk, DD +22.1%, ww +8715, stops 13.62(10.99), b5 98%, w2l 0 | -536 $/wk, DD -13.4%, ww +4266, stops 12.70(10.66), b5 96%, w2l 4 | -1973 $/wk, DD +1.2%, ww +2963, stops 12.90(10.88), b5 102%, w2l 1 | n/a | +291 (lots +4/wk) | +694 (lots +4/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s2 | -1125 $/wk, DD +22.1%, ww +11862, stops 11.34(10.35), b5 96%, w2l 0 | -176 $/wk, DD +22.1%, ww +11862, stops 12.10(10.99), b5 100%, w2l 1 | -1031 $/wk, DD -3.4%, ww +3720, stops 11.60(10.66), b5 94%, w2l 4 | -2353 $/wk, DD +3.1%, ww +771, stops 11.89(10.88), b5 99%, w2l 1 | -1464 $/wk, DD +4.8%, ww -1, stops 9.67(9.31), b5 87%, w2l 0 | -1138 (lots +4/wk) | -190 (lots +4/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40 | +1149 $/wk, DD +20.9%, ww +12597, stops 12.63(10.35), b5 94%, w2l 0 | +1150 $/wk, DD +20.9%, ww +9505, stops 13.81(10.99), b5 99%, w2l 0 | -166 $/wk, DD -7.2%, ww +4623, stops 12.96(10.66), b5 93%, w2l 4 | -3119 $/wk, DD -4.7%, ww +2391, stops 13.33(10.88), b5 101%, w2l 1 | -1699 $/wk, DD +11.6%, ww +5169, stops 10.18(9.31), b5 87%, w2l 0 | +1119 (lots +8/wk) | +1123 (lots +8/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s1 | +2118 $/wk, DD +20.0%, ww +11372, stops 9.51(10.35), b5 101%, w2l 0 | +1334 $/wk, DD +20.0%, ww +5614, stops 10.12(10.99), b5 103%, w2l 0 | +779 $/wk, DD -3.2%, ww -223, stops 9.82(10.66), b5 103%, w2l 0 | -784 $/wk, DD -3.3%, ww -3445, stops 9.95(10.88), b5 100%, w2l 0 | +61 $/wk, DD +6.6%, ww -1, stops 8.92(9.31), b5 100%, w2l 0 | +2099 (lots +5/wk) | +1320 (lots +4/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x60 | +53 $/wk, DD +19.7%, ww +8749, stops 10.12(10.35), b5 100%, w2l 0 | -355 $/wk, DD +19.7%, ww +8749, stops 10.84(10.99), b5 94%, w2l 0 | -341 $/wk, DD +8.8%, ww -2324, stops 10.61(10.66), b5 101%, w2l 1 | -360 $/wk, DD +3.7%, ww +886, stops 10.80(10.88), b5 101%, w2l 1 | n/a | +36 (lots +5/wk) | -365 (lots +3/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s3 | +1384 $/wk, DD +18.1%, ww +9334, stops 11.03(10.35), b5 96%, w2l 0 | +805 $/wk, DD +18.1%, ww +9334, stops 12.06(10.99), b5 100%, w2l 1 | -188 $/wk, DD -4.1%, ww -2105, stops 11.58(10.66), b5 102%, w2l 2 | -678 $/wk, DD -6.2%, ww -5328, stops 11.64(10.88), b5 100%, w2l 0 | -309 $/wk, DD +3.0%, ww +399, stops 9.54(9.31), b5 92%, w2l 0 | +1375 (lots +3/wk) | +790 (lots +4/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x90 | -837 $/wk, DD +16.5%, ww +7135, stops 10.12(10.35), b5 92%, w2l 0 | -2284 $/wk, DD +16.5%, ww +7135, stops 10.88(10.99), b5 93%, w2l 0 | n/a | n/a | n/a | -846 (lots +3/wk) | -2279 (lots -2/wk) |
| M1_75_g10_c1_d10_c20_tb_W_bK7_sas | +691 $/wk, DD +16.3%, ww +8619, stops 10.27(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +692 (lots -0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s2 | +907 $/wk, DD +16.2%, ww +8536, stops 9.13(10.35), b5 106%, w2l 0 | +411 $/wk, DD +16.2%, ww +8536, stops 10.08(10.99), b5 101%, w2l 0 | +67 $/wk, DD +5.8%, ww +1236, stops 9.82(10.66), b5 103%, w2l 0 | -507 $/wk, DD -1.4%, ww -1987, stops 9.87(10.88), b5 101%, w2l 0 | +485 $/wk, DD +8.3%, ww -1, stops 8.97(9.31), b5 102%, w2l 0 | +899 (lots +2/wk) | +400 (lots +3/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90 | +1830 $/wk, DD +13.7%, ww +8914, stops 7.99(10.35), b5 101%, w2l 0 | +975 $/wk, DD +13.7%, ww +8914, stops 8.79(10.99), b5 99%, w2l 0 | +917 $/wk, DD +0.7%, ww -2284, stops 8.88(10.66), b5 100%, w2l 0 | -950 $/wk, DD -3.1%, ww -5507, stops 9.36(10.88), b5 98%, w2l 0 | +384 $/wk, DD +9.4%, ww +33, stops 8.62(9.31), b5 99%, w2l 0 | +1810 (lots +5/wk) | +958 (lots +5/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s3 | +3022 $/wk, DD +13.6%, ww +9860, stops 9.59(10.35), b5 105%, w2l 0 | +1972 $/wk, DD +13.6%, ww +9860, stops 10.08(10.99), b5 103%, w2l 1 | +728 $/wk, DD +3.7%, ww +1236, stops 9.90(10.66), b5 102%, w2l 1 | -1181 $/wk, DD -1.4%, ww -1987, stops 10.12(10.88), b5 95%, w2l 0 | +578 $/wk, DD +6.6%, ww +399, stops 9.08(9.31), b5 100%, w2l 0 | +3005 (lots +5/wk) | +1955 (lots +5/wk) |
| M1_75_g10_c1_d10_c20_t08_W | -1835 $/wk, DD +13.2%, ww +6516, stops 9.21(10.35), b5 82%, w2l 0 | n/a | n/a | n/a | n/a | -1901 (lots +18/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x60 | +534 $/wk, DD +12.1%, ww +9089, stops 10.12(10.35), b5 100%, w2l 0 | +282 $/wk, DD +12.1%, ww +9089, stops 10.73(10.99), b5 106%, w2l 0 | +123 $/wk, DD +1.9%, ww +5020, stops 10.62(10.66), b5 100%, w2l 0 | -607 $/wk, DD -1.1%, ww +2477, stops 11.30(10.88), b5 99%, w2l 0 | +14 $/wk, DD +11.3%, ww +9617, stops 9.28(9.31), b5 103%, w2l 0 | +501 (lots +9/wk) | +257 (lots +7/wk) |
| M1_75_g10_c1_d10_c20_tb_B_bK7_sas | +479 $/wk, DD +11.3%, ww +1079, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +421 (lots +16/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x60 | +52 $/wk, DD +10.9%, ww +9854, stops 10.73(10.35), b5 99%, w2l 0 | +384 $/wk, DD +10.9%, ww +9854, stops 11.03(10.99), b5 103%, w2l 0 | +742 $/wk, DD +5.5%, ww -1453, stops 10.66(10.66), b5 104%, w2l 0 | +1046 $/wk, DD +1.3%, ww -1895, stops 10.88(10.88), b5 103%, w2l 0 | +62 $/wk, DD -1.5%, ww -1860, stops 9.38(9.31), b5 97%, w2l 0 | +51 (lots +0/wk) | +387 (lots -1/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x60 | -292 $/wk, DD +10.0%, ww -331, stops 10.50(10.35), b5 102%, w2l 0 | -1196 $/wk, DD +10.0%, ww -331, stops 10.99(10.99), b5 92%, w2l 0 | n/a | n/a | n/a | -286 (lots -2/wk) | -1182 (lots -4/wk) |
| M1_75_g05_c1_d10_c20_tb_B_bM7_slo | +525 $/wk, DD +9.7%, ww +3120, stops 10.58(10.35), b5 102%, w2l 0 | n/a | n/a | n/a | n/a | +520 (lots +1/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_slo | +95 $/wk, DD +9.7%, ww -935, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +77 (lots +5/wk) | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_slo | +67 $/wk, DD +9.7%, ww +2585, stops 10.20(10.35), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | +53 (lots +4/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bM7_slo | +1130 $/wk, DD +9.5%, ww +4114, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +1118 (lots +3/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x40 | -2415 $/wk, DD +9.5%, ww -707, stops 10.27(10.35), b5 104%, w2l 1 | -773 $/wk, DD +9.5%, ww -707, stops 11.15(10.99), b5 99%, w2l 1 | n/a | n/a | n/a | -2509 (lots +26/wk) | -887 (lots +31/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x40 | -112 $/wk, DD +9.5%, ww +4687, stops 10.65(10.35), b5 98%, w2l 0 | -455 $/wk, DD +9.5%, ww +4687, stops 11.34(10.99), b5 93%, w2l 0 | +172 $/wk, DD +3.1%, ww -719, stops 11.01(10.66), b5 94%, w2l 2 | +608 $/wk, DD -5.3%, ww -3325, stops 11.22(10.88), b5 108%, w2l 0 | -36 $/wk, DD -12.7%, ww +881, stops 9.56(9.31), b5 109%, w2l 1 | -136 (lots +7/wk) | -475 (lots +6/wk) |
| M1_75_g10_c2_d20_c20_tb_B | -2648 $/wk, DD +9.3%, ww +7285, stops 12.93(10.35), b5 75%, w2l 2 | n/a | n/a | n/a | n/a | -2950 (lots +82/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_pl37_tcq50T75 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | n/a | n/a | -612 (lots +2/wk) | -2263 (lots +7/wk) |
| M1_75_g10_c1_d10_c20_tb_N_bK7_slo | -255 $/wk, DD +9.1%, ww -594, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -274 (lots +5/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x40 | -2043 $/wk, DD +9.1%, ww +4192, stops 12.78(10.35), b5 90%, w2l 0 | -518 $/wk, DD +9.1%, ww +4192, stops 13.66(10.99), b5 104%, w2l 0 | -807 $/wk, DD -6.9%, ww +3804, stops 12.68(10.66), b5 102%, w2l 4 | -2249 $/wk, DD +3.8%, ww +1468, stops 12.73(10.88), b5 101%, w2l 1 | -470 $/wk, DD +3.2%, ww -1884, stops 10.26(9.31), b5 90%, w2l 0 | -2057 (lots +4/wk) | -522 (lots +1/wk) |
| M1_50_g10_c1_d10_c20_tb_W_bK7_slo | +347 $/wk, DD +8.9%, ww +4637, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +346 (lots +0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | n/a | n/a | -125 (lots +1/wk) | -1221 (lots +3/wk) |
| M1_75_g10_c1_d20_c20_tb_B | -1154 $/wk, DD +7.5%, ww +7015, stops 12.71(10.35), b5 79%, w2l 2 | n/a | n/a | n/a | n/a | -1457 (lots +83/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bM7_slo | +1820 $/wk, DD +7.5%, ww +3044, stops 9.97(10.35), b5 104%, w2l 0 | n/a | n/a | n/a | n/a | +1823 (lots -1/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx60x40 | -358 $/wk, DD +7.4%, ww +3584, stops 10.58(10.35), b5 99%, w2l 0 | -364 $/wk, DD +7.4%, ww +3584, stops 11.22(10.99), b5 95%, w2l 0 | -175 $/wk, DD -4.5%, ww -719, stops 10.93(10.66), b5 93%, w2l 2 | +1304 $/wk, DD -5.3%, ww -3325, stops 11.13(10.88), b5 107%, w2l 0 | n/a | -382 (lots +6/wk) | -383 (lots +5/wk) |
| M1_50_g10_c1_d10_c20_tb_W_bK7_sas | -214 $/wk, DD +7.3%, ww +4284, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -214 (lots +0/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_sas | -1869 $/wk, DD +6.9%, ww +1079, stops 10.50(10.35), b5 100%, w2l 1 | n/a | n/a | n/a | n/a | -1920 (lots +14/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_slo | -290 $/wk, DD +6.5%, ww +3374, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -290 (lots -0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x90 | -2807 $/wk, DD +6.3%, ww +3265, stops 10.42(10.35), b5 96%, w2l 1 | -2890 $/wk, DD +6.3%, ww +2825, stops 10.99(10.99), b5 90%, w2l 1 | n/a | n/a | n/a | -2790 (lots -5/wk) | -2863 (lots -7/wk) |
| M1_75_g10_c1_d20_c20_tb_N | -288 $/wk, DD +6.1%, ww +6186, stops 13.09(10.35), b5 86%, w2l 2 | n/a | n/a | n/a | n/a | -598 (lots +85/wk) | n/a |
(293 more cells in /mnt/l2/l2vast/_dial10/cells.json)

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
| M1_75_g05_c1_d10_c20_tb_B_bA7_sas | A7/as | -192 $/wk, DD +10.1%, ww +412, stops 5.10(4.03), b5 81%, w2l 0 | -374 $/wk, DD -36.6%, ww +412, stops 4.30(3.96), b5 93%, w2l 1 |
| M1_75_g10_c1_d10_c20_tb_B_bA7_sas | A7/as | +47 $/wk, DD +25.6%, ww +1495, stops 5.55(4.03), b5 65%, w2l 0 | -163 $/wk, DD -29.2%, ww +1253, stops 4.26(3.96), b5 74%, w2l 0 |
| M1_75_g05_c1_d10_c20_tb_N_bA7_sas | A7/as | -186 $/wk, DD +10.0%, ww +552, stops 5.10(4.03), b5 81%, w2l 0 | -268 $/wk, DD -15.8%, ww +552, stops 4.72(3.96), b5 87%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_N_bA7_sas | A7/as | -18 $/wk, DD +17.7%, ww +722, stops 5.63(4.03), b5 65%, w2l 0 | -219 $/wk, DD -19.1%, ww +722, stops 5.06(3.96), b5 86%, w2l 0 |
| M1_75_g05_c1_d10_c20_tb_W_bA7_sas | A7/as | -1 $/wk, DD +1.4%, ww -140, stops 4.03(4.03), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bA7_sas | A7/as | -15 $/wk, DD +2.4%, ww -426, stops 3.96(4.03), b5 100%, w2l 0 | +2 $/wk, DD -13.6%, ww -426, stops 3.23(3.96), b5 88%, w2l 0 |
| M1_50_g10_c1_d10_c20_tb_N_bA7_sas | A7/as | -159 $/wk, DD -8.3%, ww +877, stops 5.93(4.03), b5 9%, w2l 3 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bA7_sas | A7/as | -48 $/wk, DD -3.0%, ww -426, stops 3.88(4.03), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bH7_sas | H7/as | -574 $/wk, DD -92.7%, ww -2409, stops 0.53(0.23), b5 111%, w2l 4 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bH7_sas | H7/as | +177 $/wk, DD -33.6%, ww -1228, stops 0.61(0.23), b5 93%, w2l 2 | +650 $/wk, DD +6.5%, ww +1483, stops 0.57(0.42), b5 116%, w2l 4 |
| M1_75_g05_c1_d10_c20_tb_N_bH7_sas | H7/as | -697 $/wk, DD -92.7%, ww -2409, stops 0.53(0.23), b5 101%, w2l 4 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bH7_sas | H7/as | +244 $/wk, DD -33.6%, ww -1228, stops 0.53(0.23), b5 98%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bH7_sas | H7/as | +123 $/wk, DD +0.0%, ww +0, stops 0.23(0.23), b5 110%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bH7_sas | H7/as | -67 $/wk, DD +0.0%, ww +0, stops 0.30(0.23), b5 95%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bH7_sas | H7/as | -355 $/wk, DD -120.5%, ww -2166, stops 0.53(0.23), b5 102%, w2l 4 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bH7_sas | H7/as | -312 $/wk, DD +0.0%, ww +0, stops 0.30(0.23), b5 74%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bH7_sam | H7/am | +87 $/wk, DD +15.5%, ww +1898, stops 0.61(0.61), b5 97%, w2l 0 | +95 $/wk, DD -20.4%, ww -213, stops 0.84(0.84), b5 108%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bH7_sam | H7/am | +281 $/wk, DD +12.6%, ww +1893, stops 0.53(0.61), b5 110%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bH7_sam | H7/am | +77 $/wk, DD +15.5%, ww +1898, stops 0.61(0.61), b5 97%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bH7_sam | H7/am | +258 $/wk, DD +12.6%, ww +1893, stops 0.53(0.61), b5 110%, w2l 1 | +35 $/wk, DD -19.5%, ww +0, stops 0.84(0.84), b5 100%, w2l 1 |
| M1_75_g05_c1_d10_c20_tb_W_bH7_sam | H7/am | +11 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bH7_sam | H7/am | +22 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bH7_sam | H7/am | +252 $/wk, DD +13.2%, ww +1853, stops 0.53(0.61), b5 109%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bH7_sam | H7/am | +30 $/wk, DD +0.8%, ww +0, stops 0.53(0.61), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bK7_sas | K7/as | +1823 $/wk, DD -28.8%, ww -3232, stops 0.00(0.00), b5 119%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_sas | K7/as | +1292 $/wk, DD -46.3%, ww -1012, stops 0.15(0.00), b5 124%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bK7_sas | K7/as | +1877 $/wk, DD -19.6%, ww -2412, stops 0.00(0.00), b5 119%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_sas | K7/as | +912 $/wk, DD -46.3%, ww -1012, stops 0.15(0.00), b5 125%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bK7_sas | K7/as | -54 $/wk, DD -0.7%, ww -404, stops 0.00(0.00), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_sas | K7/as | +297 $/wk, DD +0.0%, ww +0, stops 0.00(0.00), b5 100%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_sas | K7/as | +355 $/wk, DD -86.2%, ww -5644, stops 0.00(0.00), b5 127%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bK7_sas | K7/as | -401 $/wk, DD -35.9%, ww +0, stops 0.00(0.00), b5 90%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bK7_slo | K7/lo | -9 $/wk, DD +8.7%, ww +4326, stops 0.23(0.30), b5 91%, w2l 1 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_slo | K7/lo | +481 $/wk, DD -25.5%, ww +4257, stops 0.38(0.30), b5 53%, w2l 3 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bK7_slo | K7/lo | -123 $/wk, DD -4.2%, ww +4733, stops 0.23(0.30), b5 82%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_slo | K7/lo | -31 $/wk, DD -42.3%, ww +4122, stops 0.38(0.30), b5 45%, w2l 3 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bK7_slo | K7/lo | +27 $/wk, DD +0.5%, ww +0, stops 0.30(0.30), b5 106%, w2l 1 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_slo | K7/lo | +157 $/wk, DD -4.8%, ww +0, stops 0.30(0.30), b5 99%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_slo | K7/lo | -182 $/wk, DD -13.7%, ww +3097, stops 0.23(0.30), b5 45%, w2l 2 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bK7_slo | K7/lo | +431 $/wk, DD -3.3%, ww +0, stops 0.30(0.30), b5 103%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bK7_sam | K7/am | +672 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 103%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_sam | K7/am | +879 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 107%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bK7_sam | K7/am | +535 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_sam | K7/am | +703 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 103%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bK7_sam | K7/am | +137 $/wk, DD +0.0%, ww +0, stops 0.38(0.38), b5 103%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_sam | K7/am | +176 $/wk, DD +0.0%, ww +0, stops 0.38(0.38), b5 104%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_sam | K7/am | +416 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 102%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bK7_sam | K7/am | +252 $/wk, DD +0.0%, ww +0, stops 0.38(0.38), b5 105%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bK7_spm | K7/pm | -270 $/wk, DD -24.3%, ww +0, stops 0.30(0.38), b5 102%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_spm | K7/pm | -184 $/wk, DD -15.3%, ww +0, stops 0.46(0.38), b5 105%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bK7_spm | K7/pm | -266 $/wk, DD -24.6%, ww +0, stops 0.38(0.38), b5 102%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_spm | K7/pm | -254 $/wk, DD -21.6%, ww +0, stops 0.53(0.38), b5 105%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bK7_spm | K7/pm | -4 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_spm | K7/pm | +70 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 100%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_spm | K7/pm | +48 $/wk, DD -16.0%, ww +0, stops 0.53(0.38), b5 105%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bK7_spm | K7/pm | +442 $/wk, DD -0.0%, ww +0, stops 0.30(0.38), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bM7_slo | M7/lo | +1147 $/wk, DD -8.1%, ww +130, stops 1.07(0.91), b5 127%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bM7_slo | M7/lo | +1142 $/wk, DD -23.2%, ww -729, stops 0.91(0.91), b5 138%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bM7_slo | M7/lo | +417 $/wk, DD -10.9%, ww -1075, stops 1.14(0.91), b5 107%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bM7_slo | M7/lo | -366 $/wk, DD -20.4%, ww +80, stops 1.29(0.91), b5 79%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bM7_slo | M7/lo | +688 $/wk, DD +4.4%, ww +1400, stops 0.84(0.91), b5 119%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bM7_slo | M7/lo | +1614 $/wk, DD +4.9%, ww +1190, stops 0.53(0.91), b5 162%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bM7_slo | M7/lo | +476 $/wk, DD -19.9%, ww +1144, stops 1.45(0.91), b5 89%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bM7_slo | M7/lo | +538 $/wk, DD -1.3%, ww -80, stops 0.84(0.91), b5 134%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bM7_sam | M7/am | +23 $/wk, DD -9.0%, ww -2038, stops 1.22(1.14), b5 103%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bM7_sam | M7/am | +363 $/wk, DD -3.3%, ww -218, stops 1.37(1.14), b5 105%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bM7_sam | M7/am | +17 $/wk, DD -9.0%, ww -2038, stops 1.29(1.14), b5 103%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bM7_sam | M7/am | +346 $/wk, DD -3.3%, ww -218, stops 1.45(1.14), b5 105%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bM7_sam | M7/am | +6 $/wk, DD +0.0%, ww +0, stops 1.07(1.14), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bM7_sam | M7/am | +16 $/wk, DD +0.0%, ww +0, stops 1.07(1.14), b5 100%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bM7_sam | M7/am | +383 $/wk, DD +0.3%, ww -530, stops 1.29(1.14), b5 108%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bM7_sam | M7/am | +6 $/wk, DD +0.0%, ww +0, stops 1.07(1.14), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bP7_sas | P7/as | -5946 $/wk, DD -1.0%, ww +6944, stops 0.15(0.15), b5 50%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bP7_sas | P7/as | -3315 $/wk, DD -36.1%, ww -13164, stops 0.53(0.15), b5 77%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bP7_sas | P7/as | -5762 $/wk, DD -1.0%, ww +9022, stops 0.15(0.15), b5 50%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bP7_sas | P7/as | -2696 $/wk, DD -7.8%, ww -10346, stops 0.53(0.15), b5 75%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bP7_sas | P7/as | -184 $/wk, DD -4.9%, ww -2079, stops 0.15(0.15), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bP7_sas | P7/as | -491 $/wk, DD -25.2%, ww -10331, stops 0.15(0.15), b5 102%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bP7_sas | P7/as | -3918 $/wk, DD -0.4%, ww -4286, stops 0.46(0.15), b5 71%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bP7_sas | P7/as | -816 $/wk, DD -22.6%, ww -9033, stops 0.15(0.15), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bP7_slo | P7/lo | +894 $/wk, DD +29.6%, ww -1633, stops 0.08(0.08), b5 88%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bP7_slo | P7/lo | +1179 $/wk, DD -9.8%, ww -5408, stops 0.15(0.08), b5 114%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bP7_slo | P7/lo | +386 $/wk, DD +28.5%, ww -1328, stops 0.08(0.08), b5 76%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bP7_slo | P7/lo | +1322 $/wk, DD -14.4%, ww -5203, stops 0.15(0.08), b5 116%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bP7_slo | P7/lo | +385 $/wk, DD -1.9%, ww -238, stops 0.08(0.08), b5 112%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bP7_slo | P7/lo | -142 $/wk, DD +2.7%, ww -458, stops 0.08(0.08), b5 97%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bP7_slo | P7/lo | +927 $/wk, DD +19.7%, ww -3009, stops 0.08(0.08), b5 87%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bP7_slo | P7/lo | +265 $/wk, DD +1.1%, ww +0, stops 0.08(0.08), b5 110%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bP7_sam | P7/am | +105 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 96%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bP7_sam | P7/am | +697 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 94%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bP7_sam | P7/am | -13 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 95%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bP7_sam | P7/am | +543 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 94%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bP7_sam | P7/am | +118 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bP7_sam | P7/am | +16 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 99%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bP7_sam | P7/am | -544 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 95%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bU7_sas | U7/as | -800 $/wk, DD +6.6%, ww -2883, stops 2.05(1.83), b5 92%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bU7_sas | U7/as | +71 $/wk, DD +8.3%, ww -1836, stops 1.98(1.83), b5 93%, w2l 3 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bU7_sas | U7/as | -162 $/wk, DD +6.6%, ww +57, stops 2.05(1.83), b5 92%, w2l 1 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bU7_sas | U7/as | +502 $/wk, DD +8.3%, ww +983, stops 1.98(1.83), b5 92%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bU7_sas | U7/as | -637 $/wk, DD +0.0%, ww -2883, stops 1.83(1.83), b5 100%, w2l 1 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bU7_sas | U7/as | -431 $/wk, DD +0.0%, ww -1836, stops 1.83(1.83), b5 101%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bU7_sas | U7/as | +1222 $/wk, DD +15.6%, ww -265, stops 1.90(1.83), b5 88%, w2l 2 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bU7_sas | U7/as | -648 $/wk, DD +0.0%, ww -2883, stops 1.83(1.83), b5 100%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bU7_slo | U7/lo | -891 $/wk, DD -25.4%, ww -3538, stops 1.52(1.45), b5 50%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bU7_slo | U7/lo | -1728 $/wk, DD -105.5%, ww -7540, stops 1.60(1.45), b5 59%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bU7_slo | U7/lo | +393 $/wk, DD +17.2%, ww +1796, stops 1.45(1.45), b5 91%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bU7_slo | U7/lo | +246 $/wk, DD +3.1%, ww -1185, stops 1.45(1.45), b5 97%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bU7_slo | U7/lo | -1284 $/wk, DD -44.3%, ww -6280, stops 1.52(1.45), b5 59%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bU7_slo | U7/lo | -1975 $/wk, DD -109.8%, ww -6355, stops 1.60(1.45), b5 63%, w2l 2 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bU7_slo | U7/lo | -41 $/wk, DD -9.9%, ww -1991, stops 1.52(1.45), b5 102%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bU7_slo | U7/lo | -839 $/wk, DD -33.9%, ww -4122, stops 1.37(1.45), b5 81%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_tcq50T75 | A7/as | -17 $/wk, DD +0.0%, ww +0, stops 4.03(4.03), b5 98%, w2l 0 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40 | A7/as | +205 $/wk, DD +24.7%, ww +2588, stops 6.62(4.03), b5 38%, w2l 2 | +400 $/wk, DD +24.7%, ww +2274, stops 6.96(3.96), b5 104%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | A7/as | -373 $/wk, DD -2.3%, ww +1411, stops 4.49(4.03), b5 47%, w2l 2 | -111 $/wk, DD -19.9%, ww +1207, stops 4.34(3.96), b5 98%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90 | A7/as | -20 $/wk, DD -34.2%, ww -532, stops 1.52(4.03), b5 113%, w2l 3 | -415 $/wk, DD -93.7%, ww -532, stops 1.60(3.96), b5 94%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x40 | A7/as | +879 $/wk, DD +38.1%, ww +2338, stops 6.24(4.03), b5 67%, w2l 1 | +620 $/wk, DD +18.3%, ww -327, stops 6.73(3.96), b5 113%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x90 | A7/as | -23 $/wk, DD -68.2%, ww -4785, stops 1.45(4.03), b5 133%, w2l 1 | -86 $/wk, DD -127.0%, ww -4785, stops 1.37(3.96), b5 86%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x40 | A7/as | -159 $/wk, DD -54.1%, ww -2126, stops 6.54(4.03), b5 75%, w2l 3 | -39 $/wk, DD -90.5%, ww -2126, stops 6.73(3.96), b5 114%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x60 | A7/as | -614 $/wk, DD -87.0%, ww -2571, stops 4.41(4.03), b5 89%, w2l 3 | -384 $/wk, DD -176.9%, ww -2571, stops 3.99(3.96), b5 99%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x90 | A7/as | -944 $/wk, DD -175.4%, ww -3751, stops 1.37(4.03), b5 73%, w2l 3 | -235 $/wk, DD -260.9%, ww -3751, stops 1.26(3.96), b5 92%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x40 | H7/as | -350 $/wk, DD -97.5%, ww -2100, stops 0.53(0.23), b5 115%, w2l 4 | -546 $/wk, DD -29.3%, ww +2102, stops 0.80(0.42), b5 65%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x60 | H7/as | -311 $/wk, DD -42.9%, ww -1200, stops 0.30(0.23), b5 65%, w2l 3 | -623 $/wk, DD +2.3%, ww +2567, stops 0.49(0.42), b5 64%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x90 | H7/as | -393 $/wk, DD +47.1%, ww +341, stops 0.23(0.23), b5 52%, w2l 2 | -634 $/wk, DD +19.0%, ww +3419, stops 0.11(0.42), b5 41%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx60x40 | H7/as | -205 $/wk, DD -91.8%, ww -2847, stops 0.53(0.23), b5 167%, w2l 3 | -32 $/wk, DD -25.6%, ww +1674, stops 0.76(0.42), b5 116%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx60x90 | H7/as | -720 $/wk, DD +4.5%, ww -1633, stops 0.23(0.23), b5 21%, w2l 5 | -673 $/wk, DD +20.7%, ww +1566, stops 0.11(0.42), b5 62%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x40 | H7/as | +151 $/wk, DD -129.9%, ww -2100, stops 0.61(0.23), b5 215%, w2l 4 | +241 $/wk, DD -50.5%, ww +2102, stops 0.80(0.42), b5 106%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x60 | H7/as | -336 $/wk, DD -59.3%, ww -2623, stops 0.30(0.23), b5 116%, w2l 4 | -265 $/wk, DD -6.6%, ww +0, stops 0.49(0.42), b5 88%, w2l 7 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x90 | H7/as | -1014 $/wk, DD -17.5%, ww -4123, stops 0.30(0.23), b5 41%, w2l 6 | -731 $/wk, DD +1.4%, ww +398, stops 0.15(0.42), b5 53%, w2l 8 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x40 | H7/am | +23 $/wk, DD -31.6%, ww +1516, stops 0.61(0.61), b5 120%, w2l 1 | +79 $/wk, DD -6.0%, ww +1937, stops 0.88(0.84), b5 108%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x60 | H7/am | +201 $/wk, DD +13.6%, ww +1980, stops 0.38(0.61), b5 100%, w2l 1 | -8 $/wk, DD +2.6%, ww +1138, stops 0.72(0.84), b5 97%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x90 | H7/am | +112 $/wk, DD +1.8%, ww +1980, stops 0.23(0.61), b5 94%, w2l 1 | -67 $/wk, DD -2.3%, ww +1138, stops 0.57(0.84), b5 101%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx60x40 | H7/am | -307 $/wk, DD -106.7%, ww -1634, stops 0.84(0.61), b5 129%, w2l 1 | -68 $/wk, DD -35.5%, ww -1173, stops 1.07(0.84), b5 108%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx60x90 | H7/am | -9 $/wk, DD -0.5%, ww +1614, stops 0.38(0.61), b5 91%, w2l 0 | -12 $/wk, DD -6.6%, ww -213, stops 0.65(0.84), b5 105%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x40 | H7/am | -265 $/wk, DD -106.7%, ww -1634, stops 0.91(0.61), b5 130%, w2l 1 | +276 $/wk, DD -35.5%, ww -1173, stops 1.10(0.84), b5 117%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x60 | H7/am | -138 $/wk, DD -39.2%, ww +0, stops 0.76(0.61), b5 98%, w2l 1 | +121 $/wk, DD +4.2%, ww +0, stops 0.91(0.84), b5 104%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x90 | H7/am | -323 $/wk, DD -66.9%, ww +1270, stops 0.53(0.61), b5 85%, w2l 1 | +41 $/wk, DD -9.5%, ww -213, stops 0.72(0.84), b5 110%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x40 | K7/as | +2200 $/wk, DD -27.4%, ww -2748, stops 0.08(0.00), b5 154%, w2l 1 | +2615 $/wk, DD -21.0%, ww -4436, stops 0.46(0.08), b5 110%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x60 | K7/as | +1019 $/wk, DD -23.2%, ww -2510, stops 0.00(0.00), b5 89%, w2l 1 | +841 $/wk, DD +1.5%, ww -1768, stops 0.08(0.08), b5 81%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x90 | K7/as | -1386 $/wk, DD -74.1%, ww -8079, stops 0.08(0.00), b5 26%, w2l 3 | -1634 $/wk, DD -34.2%, ww -4193, stops 0.04(0.08), b5 41%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x40 | K7/as | +2577 $/wk, DD -42.7%, ww -6350, stops 0.15(0.00), b5 161%, w2l 3 | +2934 $/wk, DD +6.2%, ww -2464, stops 0.49(0.08), b5 134%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x90 | K7/as | -1015 $/wk, DD -79.0%, ww -2751, stops 0.00(0.00), b5 47%, w2l 2 | -358 $/wk, DD -34.0%, ww +1135, stops 0.00(0.08), b5 70%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x40 | K7/as | +2627 $/wk, DD -107.1%, ww -13878, stops 0.00(0.00), b5 118%, w2l 3 | +3367 $/wk, DD -44.0%, ww -9992, stops 0.38(0.08), b5 143%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x60 | K7/as | +42 $/wk, DD -42.9%, ww -5353, stops 0.00(0.00), b5 36%, w2l 3 | +1029 $/wk, DD -26.4%, ww -3515, stops 0.08(0.08), b5 113%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x90 | K7/as | -637 $/wk, DD -7.8%, ww -3407, stops 0.00(0.00), b5 20%, w2l 3 | +821 $/wk, DD +19.8%, ww +480, stops 0.00(0.08), b5 72%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x40 | K7/lo | -636 $/wk, DD -128.9%, ww -1301, stops 0.53(0.30), b5 -16%, w2l 5 | -1500 $/wk, DD -294.8%, ww -1301, stops 0.42(0.27), b5 1%, w2l 10 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x60 | K7/lo | +294 $/wk, DD +29.6%, ww -309, stops 0.08(0.30), b5 44%, w2l 2 | +155 $/wk, DD +12.7%, ww -309, stops 0.15(0.27), b5 55%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x90 | K7/lo | -653 $/wk, DD -21.1%, ww +4018, stops 0.08(0.30), b5 -11%, w2l 4 | -1042 $/wk, DD -114.8%, ww +3418, stops 0.08(0.27), b5 1%, w2l 7 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx60x40 | K7/lo | -867 $/wk, DD -63.8%, ww +1839, stops 0.61(0.30), b5 59%, w2l 3 | -1438 $/wk, DD -193.9%, ww -2533, stops 0.57(0.27), b5 51%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx60x90 | K7/lo | -908 $/wk, DD -13.7%, ww +5133, stops 0.15(0.30), b5 32%, w2l 2 | -642 $/wk, DD -45.8%, ww +3893, stops 0.08(0.27), b5 68%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x40 | K7/lo | -545 $/wk, DD -129.7%, ww -2936, stops 0.53(0.30), b5 13%, w2l 4 | -2467 $/wk, DD -482.9%, ww -4381, stops 0.53(0.27), b5 -25%, w2l 9 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x60 | K7/lo | -162 $/wk, DD +20.8%, ww +4081, stops 0.46(0.30), b5 40%, w2l 2 | -600 $/wk, DD -46.0%, ww +1757, stops 0.38(0.27), b5 4%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x90 | K7/lo | -1172 $/wk, DD -8.8%, ww +2119, stops 0.23(0.30), b5 -22%, w2l 4 | -1026 $/wk, DD -95.7%, ww +2119, stops 0.15(0.27), b5 -27%, w2l 8 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx40x40 | K7/am | +1701 $/wk, DD -3.6%, ww -522, stops 0.53(0.38), b5 104%, w2l 0 | -117 $/wk, DD +14.2%, ww -836, stops 0.72(0.46), b5 89%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx40x60 | K7/am | +1360 $/wk, DD +0.0%, ww +0, stops 0.38(0.38), b5 105%, w2l 0 | +457 $/wk, DD +13.6%, ww -390, stops 0.46(0.46), b5 95%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx40x90 | K7/am | +1057 $/wk, DD -2.6%, ww -105, stops 0.38(0.38), b5 107%, w2l 0 | +562 $/wk, DD +8.4%, ww -1130, stops 0.42(0.46), b5 94%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx60x40 | K7/am | +974 $/wk, DD -3.6%, ww -522, stops 0.61(0.38), b5 109%, w2l 1 | -332 $/wk, DD -9.4%, ww -522, stops 0.76(0.46), b5 100%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx60x90 | K7/am | -137 $/wk, DD -21.9%, ww -105, stops 0.38(0.38), b5 103%, w2l 2 | -327 $/wk, DD -9.4%, ww -330, stops 0.42(0.46), b5 98%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx85x40 | K7/am | +974 $/wk, DD -9.3%, ww -1751, stops 0.53(0.38), b5 102%, w2l 0 | -365 $/wk, DD +5.3%, ww -1751, stops 0.72(0.46), b5 94%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx85x60 | K7/am | -270 $/wk, DD -15.2%, ww -1528, stops 0.38(0.38), b5 95%, w2l 0 | -155 $/wk, DD +7.4%, ww -1528, stops 0.46(0.46), b5 93%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx85x90 | K7/am | -1093 $/wk, DD -60.0%, ww -2500, stops 0.38(0.38), b5 89%, w2l 1 | -929 $/wk, DD -14.7%, ww -2500, stops 0.42(0.46), b5 93%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx40x40 | K7/pm | -113 $/wk, DD -11.0%, ww +0, stops 0.38(0.38), b5 101%, w2l 2 | -17 $/wk, DD +20.4%, ww +0, stops 0.49(0.46), b5 103%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx40x60 | K7/pm | -167 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 95%, w2l 1 | -75 $/wk, DD +6.9%, ww +0, stops 0.46(0.46), b5 104%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx40x90 | K7/pm | +189 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 94%, w2l 0 | -367 $/wk, DD +10.3%, ww -316, stops 0.42(0.46), b5 95%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx60x40 | K7/pm | +247 $/wk, DD -20.5%, ww +0, stops 0.38(0.38), b5 105%, w2l 1 | +323 $/wk, DD +6.2%, ww +0, stops 0.49(0.46), b5 107%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx60x90 | K7/pm | +75 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 93%, w2l 1 | -307 $/wk, DD -1.9%, ww +0, stops 0.42(0.46), b5 95%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx85x40 | K7/pm | +718 $/wk, DD -34.3%, ww +0, stops 0.38(0.38), b5 116%, w2l 1 | +1235 $/wk, DD +3.7%, ww +0, stops 0.49(0.46), b5 107%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx85x60 | K7/pm | +167 $/wk, DD -3.3%, ww +0, stops 0.38(0.38), b5 106%, w2l 0 | +524 $/wk, DD -12.3%, ww -2618, stops 0.46(0.46), b5 102%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx85x90 | K7/pm | -2 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 95%, w2l 1 | -10 $/wk, DD +13.8%, ww +0, stops 0.38(0.46), b5 100%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx40x40 | M7/lo | -2038 $/wk, DD -44.1%, ww -1957, stops 1.90(0.91), b5 60%, w2l 3 | -863 $/wk, DD -80.0%, ww -1957, stops 2.17(0.84), b5 79%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx40x60 | M7/lo | -505 $/wk, DD +24.7%, ww +4006, stops 0.68(0.91), b5 47%, w2l 2 | +586 $/wk, DD +24.7%, ww +4006, stops 0.68(0.84), b5 84%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx40x90 | M7/lo | -243 $/wk, DD +27.6%, ww +4508, stops 0.23(0.91), b5 65%, w2l 0 | +82 $/wk, DD +19.2%, ww +4508, stops 0.19(0.84), b5 62%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx60x40 | M7/lo | -143 $/wk, DD -35.0%, ww -7887, stops 1.98(0.91), b5 126%, w2l 1 | -462 $/wk, DD -59.1%, ww -7887, stops 2.28(0.84), b5 124%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx60x90 | M7/lo | +456 $/wk, DD +24.4%, ww +2810, stops 0.15(0.91), b5 98%, w2l 0 | +203 $/wk, DD +24.1%, ww +2810, stops 0.23(0.84), b5 79%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx85x40 | M7/lo | -782 $/wk, DD -57.9%, ww -5887, stops 1.90(0.91), b5 62%, w2l 3 | +188 $/wk, DD -109.7%, ww -5887, stops 1.98(0.84), b5 86%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx85x60 | M7/lo | -862 $/wk, DD -13.2%, ww +1000, stops 0.99(0.91), b5 42%, w2l 1 | -634 $/wk, DD -87.2%, ww +1000, stops 0.76(0.84), b5 45%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx85x90 | M7/lo | +656 $/wk, DD +25.6%, ww +4310, stops 0.30(0.91), b5 101%, w2l 0 | +947 $/wk, DD +13.2%, ww +4310, stops 0.30(0.84), b5 72%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx40x40 | M7/am | +16 $/wk, DD +0.0%, ww +576, stops 1.60(1.14), b5 101%, w2l 1 | -1471 $/wk, DD -96.6%, ww -771, stops 2.02(1.26), b5 93%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx40x60 | M7/am | -641 $/wk, DD -1.0%, ww -1093, stops 1.14(1.14), b5 80%, w2l 1 | -824 $/wk, DD -28.2%, ww -1093, stops 1.22(1.26), b5 86%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx40x90 | M7/am | -941 $/wk, DD -9.5%, ww -2243, stops 1.14(1.14), b5 87%, w2l 0 | -993 $/wk, DD -54.0%, ww -2243, stops 1.03(1.26), b5 96%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx60x40 | M7/am | +584 $/wk, DD -16.4%, ww -1769, stops 1.67(1.14), b5 136%, w2l 1 | -622 $/wk, DD -83.7%, ww -1769, stops 1.98(1.26), b5 114%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx60x90 | M7/am | -694 $/wk, DD -10.3%, ww -737, stops 1.14(1.14), b5 96%, w2l 0 | -507 $/wk, DD -37.6%, ww -737, stops 1.03(1.26), b5 101%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx85x40 | M7/am | +680 $/wk, DD -19.9%, ww -2720, stops 1.67(1.14), b5 123%, w2l 1 | -419 $/wk, DD -38.8%, ww -2720, stops 2.02(1.26), b5 108%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx85x60 | M7/am | +145 $/wk, DD -5.3%, ww -2264, stops 1.14(1.14), b5 102%, w2l 0 | +363 $/wk, DD -4.5%, ww -2264, stops 1.26(1.26), b5 109%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx85x90 | M7/am | -39 $/wk, DD -2.5%, ww -3020, stops 1.14(1.14), b5 106%, w2l 0 | +195 $/wk, DD -1.7%, ww -3020, stops 1.03(1.26), b5 117%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx40x40 | P7/as | -1998 $/wk, DD +2.2%, ww +3504, stops 0.38(0.15), b5 77%, w2l 2 | -2485 $/wk, DD -139.6%, ww +3504, stops 0.38(0.08), b5 76%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx40x60 | P7/as | +1709 $/wk, DD -10.8%, ww -4303, stops 0.08(0.15), b5 86%, w2l 1 | -173 $/wk, DD -10.8%, ww -4303, stops 0.04(0.08), b5 75%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx40x90 | P7/as | -276 $/wk, DD -16.0%, ww -6252, stops 0.00(0.15), b5 69%, w2l 3 | -2594 $/wk, DD -16.0%, ww -6252, stops 0.00(0.08), b5 64%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx60x40 | P7/as | -22 $/wk, DD -8.9%, ww +3400, stops 0.61(0.15), b5 87%, w2l 1 | -731 $/wk, DD -91.8%, ww +3400, stops 0.57(0.08), b5 100%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx60x90 | P7/as | -748 $/wk, DD -21.0%, ww -8247, stops 0.00(0.15), b5 70%, w2l 1 | -3283 $/wk, DD -21.0%, ww -8247, stops 0.00(0.08), b5 76%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx85x40 | P7/as | -2998 $/wk, DD -56.3%, ww -581, stops 0.68(0.15), b5 90%, w2l 2 | -2074 $/wk, DD -95.9%, ww -581, stops 0.72(0.08), b5 85%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx85x60 | P7/as | +1657 $/wk, DD -26.7%, ww -10608, stops 0.30(0.15), b5 107%, w2l 1 | +1783 $/wk, DD -26.7%, ww -10608, stops 0.19(0.08), b5 96%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx85x90 | P7/as | -1216 $/wk, DD -15.2%, ww -5963, stops 0.00(0.15), b5 62%, w2l 1 | -4208 $/wk, DD -15.2%, ww -5963, stops 0.08(0.08), b5 62%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx40x40 | P7/lo | -646 $/wk, DD -23.7%, ww -9688, stops 0.15(0.08), b5 85%, w2l 3 | -1137 $/wk, DD -118.0%, ww -9688, stops 0.23(0.19), b5 91%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx40x60 | P7/lo | +991 $/wk, DD +42.4%, ww -57, stops 0.08(0.08), b5 75%, w2l 0 | +158 $/wk, DD +7.8%, ww -57, stops 0.08(0.19), b5 82%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx40x90 | P7/lo | -818 $/wk, DD +54.1%, ww +2856, stops 0.08(0.08), b5 48%, w2l 2 | -301 $/wk, DD +46.5%, ww +2330, stops 0.08(0.19), b5 56%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx60x40 | P7/lo | -1503 $/wk, DD -73.4%, ww -9391, stops 0.15(0.08), b5 111%, w2l 1 | -1951 $/wk, DD -182.9%, ww -9391, stops 0.23(0.19), b5 104%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx60x90 | P7/lo | -968 $/wk, DD +16.1%, ww +756, stops 0.08(0.08), b5 86%, w2l 2 | -775 $/wk, DD -2.6%, ww -1655, stops 0.15(0.19), b5 71%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx85x40 | P7/lo | -2397 $/wk, DD -40.0%, ww -11199, stops 0.30(0.08), b5 34%, w2l 2 | -2714 $/wk, DD -202.1%, ww -11199, stops 0.30(0.19), b5 21%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx85x60 | P7/lo | -461 $/wk, DD +14.4%, ww +1011, stops 0.23(0.08), b5 64%, w2l 0 | -1331 $/wk, DD -83.0%, ww -3165, stops 0.27(0.19), b5 31%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx85x90 | P7/lo | -940 $/wk, DD +28.1%, ww +2210, stops 0.23(0.08), b5 75%, w2l 0 | -219 $/wk, DD +28.1%, ww +497, stops 0.23(0.19), b5 52%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx40x40 | P7/am | -905 $/wk, DD +0.0%, ww +0, stops 0.46(0.61), b5 89%, w2l 0 | -942 $/wk, DD +0.0%, ww +0, stops 0.49(0.49), b5 93%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx40x60 | P7/am | -182 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 98%, w2l 0 | -1 $/wk, DD +0.0%, ww +0, stops 0.46(0.49), b5 96%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx40x90 | P7/am | -139 $/wk, DD +0.0%, ww +0, stops 0.30(0.61), b5 102%, w2l 0 | -205 $/wk, DD +0.0%, ww +0, stops 0.38(0.49), b5 95%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx60x40 | P7/am | -441 $/wk, DD +0.0%, ww +0, stops 0.46(0.61), b5 92%, w2l 0 | +70 $/wk, DD +0.0%, ww +0, stops 0.49(0.49), b5 98%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx60x90 | P7/am | -519 $/wk, DD +0.0%, ww +0, stops 0.30(0.61), b5 102%, w2l 1 | -224 $/wk, DD +0.0%, ww +0, stops 0.38(0.49), b5 100%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx85x40 | P7/am | -1404 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 80%, w2l 0 | -803 $/wk, DD +0.0%, ww +0, stops 0.53(0.49), b5 93%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx85x60 | P7/am | -1227 $/wk, DD +0.0%, ww +0, stops 0.68(0.61), b5 83%, w2l 0 | -215 $/wk, DD +0.0%, ww +0, stops 0.53(0.49), b5 97%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx85x90 | P7/am | -824 $/wk, DD +0.0%, ww +0, stops 0.38(0.61), b5 94%, w2l 1 | +152 $/wk, DD +0.0%, ww +0, stops 0.42(0.49), b5 101%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x40 | U7/as | +1733 $/wk, DD +30.8%, ww -4307, stops 1.75(1.83), b5 114%, w2l 2 | +1503 $/wk, DD +30.8%, ww +260, stops 2.09(1.83), b5 110%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x60 | U7/as | -178 $/wk, DD +35.0%, ww +1288, stops 1.45(1.83), b5 79%, w2l 2 | +147 $/wk, DD +35.0%, ww +3310, stops 1.37(1.83), b5 86%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x90 | U7/as | -1860 $/wk, DD -31.7%, ww -1661, stops 0.76(1.83), b5 53%, w2l 2 | -678 $/wk, DD -31.7%, ww +2542, stops 0.65(1.83), b5 66%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx60x40 | U7/as | +920 $/wk, DD -22.1%, ww -3107, stops 2.59(1.83), b5 121%, w2l 3 | +1009 $/wk, DD -24.8%, ww -2681, stops 2.89(1.83), b5 117%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx60x90 | U7/as | -2913 $/wk, DD -36.2%, ww -6366, stops 0.84(1.83), b5 56%, w2l 4 | -1600 $/wk, DD -36.2%, ww -1838, stops 0.76(1.83), b5 61%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx85x40 | U7/as | +355 $/wk, DD -65.8%, ww -7904, stops 2.89(1.83), b5 139%, w2l 5 | +1392 $/wk, DD -153.6%, ww -3337, stops 3.20(1.83), b5 100%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx85x60 | U7/as | -3502 $/wk, DD -115.3%, ww -8377, stops 2.43(1.83), b5 77%, w2l 5 | -941 $/wk, DD -192.1%, ww -3810, stops 2.21(1.83), b5 59%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx85x90 | U7/as | -3324 $/wk, DD -105.3%, ww -7522, stops 0.99(1.83), b5 70%, w2l 4 | -1303 $/wk, DD -159.6%, ww -2955, stops 0.88(1.83), b5 43%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx40x40 | U7/lo | -96 $/wk, DD -41.7%, ww -2340, stops 1.52(1.45), b5 65%, w2l 1 | -448 $/wk, DD -80.2%, ww -9069, stops 1.86(1.60), b5 82%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx40x60 | U7/lo | -136 $/wk, DD +39.0%, ww +931, stops 1.07(1.45), b5 66%, w2l 0 | -782 $/wk, DD -8.2%, ww -2521, stops 1.33(1.60), b5 59%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx40x90 | U7/lo | +201 $/wk, DD +39.9%, ww +398, stops 0.61(1.45), b5 65%, w2l 0 | -459 $/wk, DD -29.8%, ww -1075, stops 0.84(1.60), b5 56%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx60x40 | U7/lo | +467 $/wk, DD -23.3%, ww +860, stops 1.75(1.45), b5 86%, w2l 1 | +596 $/wk, DD -23.3%, ww -7869, stops 2.05(1.60), b5 110%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx60x90 | U7/lo | -32 $/wk, DD -12.7%, ww -2350, stops 0.68(1.45), b5 82%, w2l 0 | -350 $/wk, DD -12.7%, ww -896, stops 0.99(1.60), b5 71%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx85x40 | U7/lo | +657 $/wk, DD -50.8%, ww -1813, stops 1.90(1.45), b5 80%, w2l 1 | -1502 $/wk, DD -374.1%, ww -8247, stops 2.32(1.60), b5 41%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx85x60 | U7/lo | -1165 $/wk, DD -102.3%, ww -4462, stops 1.67(1.45), b5 70%, w2l 1 | -2222 $/wk, DD -236.5%, ww -5405, stops 1.98(1.60), b5 30%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx85x90 | U7/lo | -1307 $/wk, DD -134.1%, ww -850, stops 0.84(1.45), b5 51%, w2l 3 | -661 $/wk, DD -134.1%, ww +604, stops 1.10(1.60), b5 36%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s1 | A7/as | -85 $/wk, DD -17.0%, ww +673, stops 5.48(4.03), b5 64%, w2l 2 | +80 $/wk, DD -17.0%, ww -2130, stops 5.36(3.96), b5 118%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s2 | A7/as | +111 $/wk, DD +22.4%, ww +517, stops 5.25(4.03), b5 89%, w2l 0 | -160 $/wk, DD +10.2%, ww +517, stops 5.21(3.96), b5 93%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s3 | A7/as | +243 $/wk, DD +29.7%, ww -1424, stops 4.95(4.03), b5 61%, w2l 1 | +81 $/wk, DD +12.5%, ww -1424, stops 5.17(3.96), b5 100%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s1 | A7/as | -23 $/wk, DD -0.7%, ww +1475, stops 3.12(4.03), b5 82%, w2l 0 | +232 $/wk, DD -15.1%, ww +1475, stops 2.97(3.96), b5 107%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s2 | A7/as | +55 $/wk, DD -19.0%, ww +1866, stops 2.74(4.03), b5 135%, w2l 2 | -540 $/wk, DD -41.4%, ww +1265, stops 3.04(3.96), b5 95%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s3 | A7/as | +10 $/wk, DD -16.9%, ww -660, stops 3.20(4.03), b5 94%, w2l 1 | -41 $/wk, DD -53.6%, ww -660, stops 2.89(3.96), b5 103%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x40s1 | U7/as | +77 $/wk, DD -2.7%, ww -1716, stops 1.90(1.83), b5 106%, w2l 1 | +514 $/wk, DD -6.6%, ww +2851, stops 1.98(1.83), b5 104%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x40s2 | U7/as | +1223 $/wk, DD +0.1%, ww -427, stops 1.67(1.83), b5 120%, w2l 2 | +427 $/wk, DD -9.2%, ww -2199, stops 2.02(1.83), b5 114%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x40s3 | U7/as | +1405 $/wk, DD +2.6%, ww -349, stops 1.67(1.83), b5 127%, w2l 1 | +773 $/wk, DD -20.1%, ww -4846, stops 1.94(1.83), b5 124%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40 | A7/as | +128 $/wk, DD +12.5%, ww +2821, stops 7.53(4.03), b5 31%, w2l 2 | +401 $/wk, DD +12.5%, ww +2050, stops 7.88(3.96), b5 107%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s101 | A7/as | +141 $/wk, DD -29.6%, ww +3271, stops 5.78(4.03), b5 62%, w2l 3 | +56 $/wk, DD -29.6%, ww +1628, stops 5.86(3.96), b5 83%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s102 | A7/as | -734 $/wk, DD -56.0%, ww +189, stops 5.78(4.03), b5 66%, w2l 2 | -842 $/wk, DD -56.0%, ww +189, stops 5.59(3.96), b5 62%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s103 | A7/as | +433 $/wk, DD +7.5%, ww +3108, stops 5.48(4.03), b5 88%, w2l 1 | +136 $/wk, DD +7.5%, ww +1569, stops 5.44(3.96), b5 80%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40 | U7/as | +817 $/wk, DD +33.5%, ww -3187, stops 2.05(1.83), b5 98%, w2l 2 | +483 $/wk, DD +25.8%, ww +1380, stops 2.32(1.83), b5 101%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s101 | U7/as | -1182 $/wk, DD -9.2%, ww -3181, stops 2.13(1.83), b5 78%, w2l 2 | -1103 $/wk, DD -9.2%, ww -2122, stops 2.17(1.83), b5 84%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s102 | U7/as | -401 $/wk, DD +5.1%, ww -695, stops 2.05(1.83), b5 84%, w2l 2 | -926 $/wk, DD -6.4%, ww +3231, stops 2.21(1.83), b5 85%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s103 | U7/as | +315 $/wk, DD +11.3%, ww -735, stops 1.90(1.83), b5 104%, w2l 1 | +49 $/wk, DD +9.3%, ww +1362, stops 2.02(1.83), b5 114%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40 | K7/am | +1028 $/wk, DD -2.2%, ww +2449, stops 3.65(0.38), b5 98%, w2l 1 | +23 $/wk, DD +25.9%, ww -1431, stops 3.69(0.46), b5 75%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s101 | K7/am | +654 $/wk, DD +6.0%, ww +3031, stops 1.98(0.38), b5 102%, w2l 1 | +50 $/wk, DD +32.6%, ww +428, stops 2.24(0.46), b5 80%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s102 | K7/am | +693 $/wk, DD +0.6%, ww -137, stops 2.13(0.38), b5 99%, w2l 1 | -168 $/wk, DD +28.8%, ww -137, stops 2.17(0.46), b5 71%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s103 | K7/am | +93 $/wk, DD +3.2%, ww +251, stops 1.67(0.38), b5 94%, w2l 1 | -345 $/wk, DD +24.4%, ww +251, stops 2.02(0.46), b5 69%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60 | K7/am | +697 $/wk, DD +3.2%, ww +2449, stops 0.53(0.38), b5 95%, w2l 1 | -52 $/wk, DD +30.7%, ww +1423, stops 0.53(0.46), b5 70%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 | K7/am | +375 $/wk, DD +6.0%, ww +3249, stops 0.53(0.38), b5 98%, w2l 1 | -35 $/wk, DD +32.6%, ww +1423, stops 0.53(0.46), b5 74%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s102 | K7/am | +500 $/wk, DD +6.0%, ww +1668, stops 0.53(0.38), b5 93%, w2l 1 | -199 $/wk, DD +32.6%, ww +1668, stops 0.53(0.46), b5 70%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s103 | K7/am | +53 $/wk, DD +3.2%, ww +1268, stops 0.53(0.38), b5 94%, w2l 1 | -184 $/wk, DD +28.0%, ww +1268, stops 0.53(0.46), b5 71%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60 | K7/lo | -651 $/wk, DD +4.9%, ww -812, stops 0.08(0.30), b5 33%, w2l 2 | -619 $/wk, DD -16.1%, ww -812, stops 0.15(0.27), b5 43%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s101 | K7/lo | -21 $/wk, DD -7.4%, ww -349, stops 0.30(0.30), b5 76%, w2l 1 | -348 $/wk, DD -18.2%, ww -349, stops 0.23(0.27), b5 52%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s102 | K7/lo | +395 $/wk, DD -12.7%, ww -596, stops 0.30(0.30), b5 103%, w2l 2 | +290 $/wk, DD -12.7%, ww -596, stops 0.23(0.27), b5 85%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s103 | K7/lo | +994 $/wk, DD +23.5%, ww +144, stops 0.15(0.30), b5 88%, w2l 0 | +475 $/wk, DD -9.1%, ww +144, stops 0.15(0.27), b5 78%, w2l 2 |

### Leads (tolerant gate in every scored window incl. L3M and L6M, DD cut > 0 in some window)
| cell | scope | L6M DD cut % | L6M d mean | windows | W44 removed L3M / L6M |
|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 | nyam | +42.3 | -19 | 2 | +1314 $/wk, DD +47.6%, ww +1732, stops 1.14(1.29), b5 86%, w2l 1 / -19 $/wk, DD +42.3%, ww +4319, stops 1.67(1.67), b5 64%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p92 | london | +28.2 | +336 | 2 | -34 $/wk, DD +28.2%, ww +6232, stops 2.51(2.74), b5 84%, w2l 0 / +336 $/wk, DD +28.2%, ww +6232, stops 2.74(2.89), b5 82%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | all | +22.5 | +710 | 5 | +900 $/wk, DD +22.5%, ww +10172, stops 10.73(10.35), b5 98%, w2l 0 / +710 $/wk, DD +22.5%, ww +5127, stops 11.34(10.99), b5 98%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p81 | nyam | +22.1 | -28 | 4 | +818 $/wk, DD +44.9%, ww +2094, stops 1.29(1.29), b5 78%, w2l 1 / -28 $/wk, DD +22.1%, ww +3278, stops 2.05(1.67), b5 69%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | nypm | +16.5 | +245 | 2 | +245 $/wk, DD +16.5%, ww +185, stops 0.08(0.08), b5 131%, w2l 1 / +245 $/wk, DD +16.5%, ww +185, stops 0.08(0.08), b5 95%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | nyam | +8.0 | +173 | 2 | +622 $/wk, DD +14.2%, ww +0, stops 1.37(1.29), b5 103%, w2l 1 / +173 $/wk, DD +8.0%, ww +2555, stops 1.71(1.67), b5 91%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s103 | london | +7.2 | +647 | 2 | +44 $/wk, DD +7.2%, ww +6382, stops 2.43(2.74), b5 82%, w2l 0 / +647 $/wk, DD +7.2%, ww +6382, stops 2.66(2.89), b5 80%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x60 | london | +4.4 | +106 | 5 | +114 $/wk, DD +4.4%, ww +2874, stops 2.74(2.74), b5 99%, w2l 0 / +106 $/wk, DD +4.4%, ww +2874, stops 2.89(2.89), b5 100%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_N_bH7_sam | nyam | +0.8 | +35 | 2 | +258 $/wk, DD +6.8%, ww +285, stops 1.22(1.29), b5 96%, w2l 0 / +35 $/wk, DD +0.8%, ww +180, stops 1.67(1.67), b5 95%, w2l 0 |
| M1_75_g05_c1_d10_c20_tb_B_bH7_sam | nyam | +0.4 | +95 | 2 | +87 $/wk, DD +1.3%, ww +0, stops 1.29(1.29), b5 98%, w2l 0 / +95 $/wk, DD +0.4%, ww +90, stops 1.67(1.67), b5 96%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bH7_sas | asia | +0.4 | +1181 | 2 | +689 $/wk, DD +0.4%, ww -346, stops 6.47(6.24), b5 101%, w2l 0 / +1181 $/wk, DD +0.4%, ww -346, stops 6.47(6.35), b5 98%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bH7_sas | all | +0.4 | +1513 | 2 | +614 $/wk, DD +0.4%, ww +185, stops 10.58(10.35), b5 98%, w2l 0 / +1513 $/wk, DD +0.4%, ww +185, stops 11.18(10.99), b5 98%, w2l 0 |
| M1_75_g05_c1_d10_c20_tb_B_bA7_sas | all | +0.2 | -205 | 2 | -543 $/wk, DD +0.2%, ww +35, stops 11.26(10.35), b5 97%, w2l 0 / -205 $/wk, DD +0.2%, ww +35, stops 11.18(10.99), b5 99%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_W_bA7_sas | asia | +0.2 | +187 | 2 | -24 $/wk, DD +0.2%, ww -215, stops 6.16(6.24), b5 100%, w2l 0 / +187 $/wk, DD +0.2%, ww -215, stops 5.63(6.35), b5 99%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_W_bA7_sas | all | +0.2 | +777 | 2 | -24 $/wk, DD +0.2%, ww -215, stops 10.27(10.35), b5 100%, w2l 0 / +777 $/wk, DD +0.2%, ww -215, stops 10.27(10.99), b5 99%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bA7_sas | asia | +0.1 | -326 | 2 | +481 $/wk, DD +0.1%, ww -232, stops 7.61(6.24), b5 97%, w2l 0 / -326 $/wk, DD +0.1%, ww -232, stops 6.62(6.35), b5 93%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bA7_sas | all | +0.1 | +620 | 2 | +1092 $/wk, DD +0.1%, ww -232, stops 11.64(10.35), b5 96%, w2l 0 / +620 $/wk, DD +0.1%, ww -232, stops 11.18(10.99), b5 95%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x60 | london | +0.0 | +894 | 5 | +778 $/wk, DD +0.0%, ww +0, stops 2.66(2.74), b5 104%, w2l 0 / +894 $/wk, DD +0.0%, ww +0, stops 2.85(2.89), b5 104%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x60 | nyam | +0.0 | -8 | 2 | +201 $/wk, DD +4.5%, ww +0, stops 1.07(1.29), b5 99%, w2l 0 / -8 $/wk, DD +0.0%, ww +0, stops 1.56(1.67), b5 96%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx85x90 | asia | +0.0 | -137 | 5 | -274 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 1 / -137 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx85x40 | nyam | +0.0 | +68 | 2 | -15 $/wk, DD +11.8%, ww -160, stops 1.37(1.29), b5 93%, w2l 0 / +68 $/wk, DD +0.0%, ww +0, stops 1.75(1.67), b5 106%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x40 | nyam | -0.8 | +79 | 2 | +23 $/wk, DD +2.3%, ww +62, stops 1.29(1.29), b5 91%, w2l 0 / +79 $/wk, DD -0.8%, ww -171, stops 1.71(1.67), b5 89%, w2l 0 |

### Placebos beside the finalists (forecast shifted 11 / 23 / 37 sessions at the same clock; random other session at the same clock), scope all, L6M (a real lead must beat all of them)
| finalist | real | pl11 | pl23 | pl37 | random |
|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 | -2640 $/wk, DD +56.0%, ww +22141, stops 10.88(10.99), b5 76%, w2l 0 | pending | pending | pending | pending |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p92 | -3692 $/wk, DD +53.5%, ww +23074, stops 10.84(10.99), b5 73%, w2l 0 | pending | pending | pending | pending |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | +710 $/wk, DD +22.5%, ww +5127, stops 11.34(10.99), b5 98%, w2l 1 | pending | pending | pending | pending |

### Combined with the chop call and the trend-day call (item 7)
| cell | mode | L3M | L6M |
|---|---|---|---|

### FOR THE LIVE BUILD: what D7 needs at the signal second
1. Own 1-minute NQ bars only (closed bars up to the signal second): range and realised vol of the last 15/30/60/120 min; the same offset-into-session range over the previous 20 sessions (median); the range of the previous 5 and 20 sessions of the same session type; range so far in the current session; last close. D7 computes all of these itself from its own bars (preferred). 2. A small coefficient table (per session: 14 weights, mean, sd, intercept for the median-horizon and 75th-pct models) plus per book+session H50/H75 and ref EM, refit every 14 days: a static file pushed from the box every 2 weeks (the only file). 3. Nothing intraday from the box for M1. M2 (T-RANGE2 session forecast + calendar flags) needs the T-RANGE2 file and the event calendar at the session start: ranks below an equal M1 version. 4. The chop-call and trend-day cells additionally need those call files (not computable from D7 bars alone): rank below the bars-only version.

### Reading
Drawdown first; a result needs the gate in recent AND older windows and has to beat the placebos. Cells that cut drawdown only through L3M, or only with full stops up, are not leads. Expected move forecast quality (table above) is a forecasting result scored on all 43 months; the exact cells decide whether it makes a better bracket. No PASS claim.
