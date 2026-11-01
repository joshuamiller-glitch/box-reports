
# OLD CAP interim (Z1, T-ZONES-3 section 1; wall ~15:45Z 2026-11-01; checkpoint on the lead's order T-RECENT-REDO, workers stopped)
Everything below is scored to the OLD CAP (label day 20260206; windows L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 wk), POST-HOC, no PASS claim, Shadow only. Base = interim one-convention composite (8 lines skipped at D20, lock off), tie-out exact (L6M +41.1k/wk, maxDD 22.9k, PRE 241.2k; without the zone piece 57.2 / 57.2 / 143.4 / 303.7 / 118.3). Prereg l2vast/ds3/prereg/ZONES3_S1_prereg.md sha256 09ac46ad9ef1810b504630ddab2bd7ba67abe31f1b8f2c4c96d3cbe342fb3771 (DECISIONS.md). Code l2vast/ds3/code/zones3/s1/, results l2vast/ds3/out/zones3/s1/ (d7 adapter d7z.py/jobs7.py written and tied out EXACTLY to BASE-1 loo_literal for BASE and "-zone", not run further). Placebos: premise 200 A + about 80 B draws done; line placebos only partly run (1150 of 9200 draws), so line labels below that need B-ranks are PROVISIONAL.

## Page 1a - premise check (task 0): does the 8-line skip lower drawdown "in every window"?
Plain answer: NO, not in every window. It holds in the recent episodes, is weak in PRE, and is absent in X' on maxDD.
* L3M/L6M: maxDD 57 -> 21-23k (-60%), but this is ONE week (2026-01-19, -57k -> -21k). Drop that episode (leave-one-episode-out) and the L6M cut becomes -30% (the skip makes it worse); bootstrap P(cut>0) is 0.79 in L6M. L3M is inside L6M inside HOLD: one recent episode, not three windows.
* HOLD: 143 -> 97k (-32%), two separate episodes (July 2025 and Jan 2026) both helped, cut survives dropping either (+32% .. +60%); CI [-8%, +60%], P(cut>0) 0.94.
* PRE: 304 -> 241k (-21%), CI [-26%, +34%], P(cut>=20%) 0.29, leave-one-month-out -26% .. +21%; placebo rank 0.36 (random-level) / 0.26 (same-volume): not distinguishable from chance volume cut.
* X': 118 -> 121k (+2%, "flat" = no maxDD effect); worst-20 -576 -> -420k (rank 0.06 / 0.04) and SD 36 -> 33k improve, so only a tail effect.
* 2%-rank placebo re-derived: L6M rank 0.010 (A) / 0.012 (B partial) = DD-1's 2%; it is the only window where chance is beaten (L3M 0.010 same week). HOLD 0.24, PRE 0.36, X' 0.45.
* With the 12R combined lock the pattern flips: L6M +54%, HOLD +39%, X' +62%, PRE -8% (worse): consistent with DD-1 that no piece agrees in PRE and X' without a combined lock.
* Books/sessions: skip hurts U6 (L6M 30 -> 41k, mean -2.7k/wk); helps K6, P6, H6. PRE/X' effect lives in Asia (PRE 210 -> 129k P=0.98, X' 159 -> 122k P=0.97); nyam carries the L6M/HOLD mean (+4.2k); nypm worsens X' (14 -> 26k).
* PROVISIONAL D7-base reading (BASE-1 loo_literal, not mine): removing the zone set moves maxDD L6M 84.8 -> 85.1k (flat), HOLD 94.1 -> 84.8, PRE 246.9 -> 190.7 (-23%), X' 136.3 -> 126.5 (-7%): on D7 the L6M effect is absent. Re-run needed on the final base.

| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | week of the maxDD trough without > with | leave-one-episode-out: cut range (episodes dropped) | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean $k/wk (MDE) | placebo rank maxDD cut: random-level same-count / same-volume skip | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M (14) | 57 > 21 (+63%) | [+50%, +73%] / 1.00 / 0.99 | 20260119 > 20260119 | n/a (window too short) | +52% .. +63% | 406 > 482 * | 51.5 > 44.7 | 0.51 > 1.61 | +5.4 (10.8) | 0.010 / 0.005 (n 200 / 200) | - |
| L6M (28) | 57 > 23 (+60%) | [-30%, +71%] / 0.79 / 0.75 | 20260119 > 20251020 | -30% .. +63% (4 drops) | -8% .. +63% | 313 > 371 * | 43.6 > 42.7 | 0.63 > 1.80 | +5.3 (9.6) | 0.010 / 0.005 (n 200 / 200) | - |
| HOLD (32) | 143 > 97 (+32%) | [-8%, +60%] / 0.94 / 0.92 | 20250721 > 20250721 | +32% .. +60% (6 drops) | +32% .. +60% | 35 > 136 * | 59.1 > 51.8 | 0.24 > 0.40 | +3.5 (10.5) | 0.239 / 0.189 (n 200 / 200) | - |
| PRE (75) | 304 > 241 (+21%) | [-26%, +34%] / 0.76 / 0.29 | 20240930 > 20240930 | +6% .. +21% (9 drops) | -26% .. +21% | -977 > -875 | 59.1 > 55.7 | 0.07 > 0.10 | +2.7 (8.6) | 0.363 / 0.264 (n 200 / 200) | 0.254 / 0.144 |
| X' (44) | 118 > 121 (-2%) | [-40%, +55%] / 0.72 / 0.48 | 20230814 > 20230515 | -25% .. +32% (7 drops) | -18% .. +44% | -576 > -420 | 36.1 > 32.6 | 0.04 > 0.07 | +3.8 (7.8) | 0.453 / 0.428 (n 200 / 200) | 0.060 / 0.030 |
| ALL (149) | 304 > 241 (+21%) | [-12%, +36%] / 0.85 / 0.37 | 20240930 > 20240930 | +6% .. +21% (13 drops) | -9% .. +21% | -1286 > -1098 | 54.5 > 50.3 | 0.06 > 0.09 | +3.2 (5.3) | 0.353 / 0.264 (n 200 / 200) | 0.055 / 0.020 |

### Per book and per session (maxDD $k without > with [bootstrap P(cut>0)] / worst-20 / mean d)
| book / session | L3M maxDD $k without > with [P(cut>0)] / worst-20 $k / mean d $k | L6M maxDD $k without > with [P(cut>0)] / worst-20 $k / mean d $k | HOLD maxDD $k without > with [P(cut>0)] / worst-20 $k / mean d $k | PRE maxDD $k without > with [P(cut>0)] / worst-20 $k / mean d $k | X' maxDD $k without > with [P(cut>0)] / worst-20 $k / mean d $k |
|---|---|---|---|---|---|
| K6 | 69 > 40 [1.00] / 8 > 48 / +2.8 | 59 > 35 [0.99] / -44 > -10 / +1.0 | 59 > 37 [0.94] / -119 > -79 / +0.6 | 35 > 39 [0.36] / -250 > -239 / +0.0 | 39 > 36 [0.76] / -144 > -127 / +0.3 |
| P6 | 29 > 26 [0.69] / 239 > 313 / +5.3 | 52 > 33 [0.85] / 129 > 200 / +5.3 | 53 > 51 [0.94] / -27 > 59 / +4.1 | 304 > 281 [0.69] / -783 > -713 / +2.5 | 82 > 75 [0.75] / -366 > -299 / +2.3 |
| U6 | 30 > 41 [0.26] / 11 > -34 / -3.2 | 30 > 41 [0.32] / -73 > -79 / -2.7 | 30 > 41 [0.16] / -87 > -105 / -2.9 | 98 > 85 [0.88] / -339 > -300 / +0.2 | 30 > 50 [0.28] / -99 > -112 / +0.4 |
| H6 | 34 > 27 [0.74] / 130 > 137 / +0.5 | 15 > 12 [0.75] / -5 > 46 / +1.6 | 27 > 12 [0.94] / -50 > 4 / +1.4 | 59 > 42 [0.61] / -241 > -208 / -0.1 | 54 > 48 [0.74] / -169 > -141 / +0.2 |
| M6 | 37 > 31 [0.81] / -7 > -4 / +0.2 | 37 > 31 [0.71] / -65 > -55 / +0.2 | 37 > 31 [0.74] / -99 > -84 / +0.2 | 85 > 53 [0.79] / -232 > -220 / +0.2 | 53 > 46 [0.91] / -154 > -135 / +0.2 |
| A6 | 15 > 14 [0.66] / 24 > 22 / -0.1 | 15 > 14 [0.30] / -16 > -18 / -0.0 | 15 > 14 [0.58] / -32 > -30 / +0.0 | 15 > 14 [0.69] / -97 > -78 / -0.0 | 18 > 18 [0.76] / -60 > -51 / +0.3 |
| asia | 76 > 62 [0.76] / 280 > 292 / +0.9 | 63 > 41 [0.60] / 70 > 80 / +1.6 | 63 > 50 [0.68] / -70 > -89 / -0.4 | 210 > 129 [0.98] / -803 > -604 / +1.5 | 159 > 122 [0.97] / -595 > -422 / +4.5 |
| london | 60 > 49 [0.90] / 60 > 70 / +0.8 | 67 > 65 [0.83] / -113 > -101 / -0.2 | 67 > 65 [0.85] / -212 > -169 / -0.2 | 231 > 233 [0.68] / -836 > -781 / +0.1 | 143 > 117 [0.83] / -495 > -418 / +1.3 |
| nyam | 52 > 46 [0.75] / 79 > 128 / +3.5 | 52 > 50 [0.87] / -155 > -88 / +4.2 | 55 > 51 [0.91] / -251 > -183 / +4.1 | 128 > 119 [0.55] / -452 > -451 / +1.1 | 138 > 128 [0.38] / -421 > -449 / -1.4 |
| nypm | 19 > 15 [0.67] / -13 > -9 / +0.3 | 19 > 15 [0.40] / -36 > -42 / -0.2 | 19 > 15 [0.56] / -48 > -45 / +0.0 | 49 > 48 [0.56] / -123 > -109 / -0.1 | 14 > 26 [0.07] / -62 > -68 / -0.7 |

### 12R combined lock sensitivity
| window | maxDD $k without > with (cut) lock 12R | worst-20 | mean $k/wk |
|---|---|---|---|
| L3M | 58 > 27 (+54%) | 374 > 406 | 26.7 > 29.0 |
| L6M | 58 > 27 (+54%) | 105 > 181 | 26.8 > 32.3 |
| HOLD | 58 > 35 (+39%) | -72 > -6 | 28.0 > 31.4 |
| PRE | 216 > 233 (-8%) | -571 > -608 | 10.4 > 15.1 |
| X' | 312 > 120 (+62%) | -480 > -468 | -6.6 > 1.0 |
| ALL | 354 > 233 (+34%) | -722 > -688 | 9.3 > 14.7 |

## Page 1b - line table (marginal-in-set: coded line = 8-line set minus the line -> 8 lines; uncoded = 8 lines -> 8 + line), ranked by $ maxDD cut summed over L6M+PRE+X' (PROVISIONAL: placebo columns thin, labels may change)
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | PDmid (coded) | 65 (0.6%) | 23>23 (+1%) | 84>97 (-16%) | 260>241 (+7%) | 136>121 (+12%) | -866>-875 | -424>-420 | -0.2 (3.3) / -0.1 (1.5) / -0.2 (2.1) | -5.4 / -3.1 / -1.8 | L6M 0.091/- / PRE 0.091/- / X' 0.273/- | no | n/n/n | n/n | n | n |
| 2 | camH3 (coded) | 212 (2.0%) | 25>23 (+8%) | 92>97 (-6%) | 248>241 (+3%) | 137>121 (+12%) | -931>-875 | -485>-420 | +2.5 (6.4) / +0.6 (3.4) / -0.1 (3.4) | +1.0 / +0.6 / -0.6 | L6M -/- / PRE -/- / X' -/- | no | n/n/n | n/n | n | n |
| 3 | OTE62 (coded) | 251 (2.3%) | 28>23 (+17%) | 100>97 (+3%) | 272>241 (+11%) | 110>121 (-10%) | -876>-875 | -430>-420 | -1.6 (5.0) / -1.7 (3.2) / +0.0 (2.4) | -2.0 / -1.8 / +0.1 | L6M -/- / PRE -/- / X' -/- | no | n/n/n | n/n | n | n |
| 4 | VAH15s (UNCODED) | 174 (1.7%) | 23>23 (+0%) | 97>104 (-7%) | 241>229 (+5%) | 121>110 (+9%) | -875>-859 | -420>-384 | -2.2 (3.3) / +0.6 (3.4) / +0.1 (2.3) | -3.5 / +0.8 / -0.0 | L6M -/- / PRE -/- / X' -/- | no | n/n/n | n/n | n | n |
| 5 | OTE79 (coded) | 282 (2.6%) | 39>23 (+42%) | 116>97 (+16%) | 236>241 (-2%) | 116>121 (-4%) | -837>-875 | -417>-420 | +2.3 (6.2) / +0.2 (2.7) / +0.2 (2.2) | -3.0 / -2.4 / -1.7 | L6M -/- / PRE -/- / X' -/- | RISK-KEEP (volume effect) | Y/n/Y | Y/Y | n | n |
| 6 | kijun1h (coded) | 214 (2.0%) | 30>23 (+24%) | 105>97 (+8%) | 253>241 (+4%) | 107>121 (-13%) | -891>-875 | -429>-420 | +0.7 (2.9) / +0.6 (2.7) / -0.6 (3.0) | -2.1 / +0.4 / -1.3 | L6M 0.035/0.040 / PRE 0.363/0.323 / X' 0.871/0.905 | RISK-KEEP (L6M only) | n/Y/Y | Y/Y | n | n |
| 7 | HVN0_1hs (UNCODED) | 209 (2.0%) | 23>23 (+0%) | 97>86 (+11%) | 241>232 (+4%) | 121>128 (-7%) | -875>-824 | -420>-416 | -0.3 (3.1) / +1.0 (2.3) / -0.9 (2.4) | -3.5 / +0.8 / -1.6 | L6M -/- / PRE -/- / X' -/- | no | n/n/n | n/n | n | n |
| 8 | KCup4h (coded) | 98 (0.9%) | 25>23 (+9%) | 100>97 (+3%) | 239>241 (-1%) | 112>121 (-7%) | -918>-875 | -440>-420 | -1.5 (3.1) / -0.2 (1.6) / +1.0 (2.2) | -4.7 / -0.1 / +0.5 | L6M -/- / PRE -/- / X' -/- | no | n/n/n | n/n | n | n |
| 9 | CRT4h (coded) | 175 (1.6%) | 25>23 (+10%) | 116>97 (+17%) | 244>241 (+1%) | 103>121 (-17%) | -835>-875 | -387>-420 | +1.9 (2.4) / +1.2 (2.6) / -0.2 (2.4) | -3.5 / -1.6 / -2.0 | L6M -/- / PRE -/- / X' -/- | no | n/n/Y | Y/Y | n | n |
| 10 | LVN1_1hs (UNCODED) | 133 (1.3%) | 23>23 (+0%) | 97>96 (+1%) | 241>260 (-8%) | 121>116 (+4%) | -875>-851 | -420>-389 | +0.8 (3.5) / +0.3 (2.3) / -1.2 (3.2) | +0.7 / +0.8 / -1.2 | L6M -/- / PRE -/- / X' -/- | no | n/Y/Y | Y/Y | n | n |
| 11 | OTE705 (coded) | 130 (1.2%) | 23>23 (+0%) | 107>97 (+10%) | 228>241 (-6%) | 105>121 (-15%) | -877>-875 | -410>-420 | +0.3 (3.3) / +1.9 (3.3) / +1.8 (3.5) | -4.8 / -1.2 / +0.2 | L6M -/- / PRE -/- / X' -/- | no | Y/Y/Y | Y/Y | n | n |

### Honest ranking (selected on PRE+X', recent windows looked at once)
| honest # | line | selected on PX: S_PX = mean(cut PRE, cut X') | cut PRE | cut X' | PX gate | ONE recent look: cut L6M | cut HOLD | cut L3M | mean d L6M (MDE) | mean d HOLD | label | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | camH3 | +0.076 | +2.9% | +12.2% | pass | +8.0% | -5.8% | +14.2% | +2.5 (6.4) | +1.7 | no | n/n/n |
| 2 | VAH15s | +0.070 | +5.2% | +8.8% | pass | +0.0% | -7.4% | -5.7% | -2.2 (3.3) | -2.2 | no | n/n/n |
| - | PDmid | +0.094 | +7.1% | +11.7% | fail: PRE w20 worse | +1.4% | -16.1% | +0.2% | -0.2 (3.3) | -0.7 | no | n/n/n |
| - | OTE62 | +0.007 | +11.2% | -9.7% | fail: X' no cut, PRE mean < -0.5 MDE | +17.0% | +2.9% | +22.6% | -1.6 (5.0) | -1.4 | no | n/n/n |
| - | HVN0_1hs | -0.015 | +3.7% | -6.6% | fail: X' no cut | +0.0% | +11.3% | +17.7% | -0.3 (3.1) | +0.2 | no | n/n/n |
| - | LVN1_1hs | -0.021 | -7.7% | +3.6% | fail: PRE no cut | +0.0% | +1.1% | -5.8% | +0.8 (3.5) | +0.7 | no | n/Y/Y |
| - | OTE79 | -0.031 | -2.2% | -4.0% | fail: PRE no cut, X' no cut, PRE w20 worse, X' w20 worse | +41.8% | +16.5% | +45.7% | +2.3 (6.2) | +2.1 | RISK-KEEP (volume effect) | Y/n/Y |
| - | kijun1h | -0.040 | +4.5% | -12.6% | fail: X' no cut | +23.8% | +7.8% | +28.9% | +0.7 (2.9) | +0.6 | RISK-KEEP (L6M only) | n/Y/Y |
| - | KCup4h | -0.040 | -0.9% | -7.1% | fail: PRE no cut, X' no cut | +8.7% | +2.5% | +14.8% | -1.5 (3.1) | -1.5 | no | n/n/n |
| - | CRT4h | -0.079 | +1.3% | -17.2% | fail: X' no cut, PRE w20 worse, X' w20 worse | +9.9% | +16.7% | -13.4% | +1.9 (2.4) | +2.1 | no | n/n/Y |
| - | OTE705 | -0.105 | -5.9% | -15.0% | fail: PRE no cut, X' no cut, X' w20 worse | +0.0% | +9.7% | +0.0% | +0.3 (3.3) | +0.4 | no | Y/Y/Y |

### Post-hoc ranking (L6M cut, PRE/X' beside)
| post-hoc # | line | cut L6M | Calmar L6M before>after | cut HOLD | cut L3M | PRE: cut, mean d (MDE), TOL | X': cut, mean d (MDE) | S/T/N | TOL-B / TOL-nc | label |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE79 | +41.8% | 0.99 > 1.80 | +16.5% | +45.7% | -2.2%, +0.2 (2.7) | -4.0%, +0.2 (2.2) | Y/n/Y | Y/Y | RISK-KEEP (volume effect) |
| 2 | kijun1h | +23.8% | 1.35 > 1.80 | +7.8% | +28.9% | +4.5%, +0.6 (2.7) | -12.6%, -0.6 (3.0) | n/Y/Y | Y/Y | RISK-KEEP (L6M only) |
| 3 | OTE62 | +17.0% | 1.55 > 1.80 | +2.9% | +22.6% | +11.2%, -1.7 (3.2) | -9.7%, +0.0 (2.4) | n/n/n | n/n | no |
| 4 | CRT4h | +9.9% | 1.55 > 1.80 | +16.7% | -13.4% | +1.3%, +1.2 (2.6) | -17.2%, -0.2 (2.4) | n/n/Y | Y/Y | no |
| 5 | KCup4h | +8.7% | 1.70 > 1.80 | +2.5% | +14.8% | -0.9%, -0.2 (1.6) | -7.1%, +1.0 (2.2) | n/n/n | n/n | no |
| 6 | camH3 | +8.0% | 1.55 > 1.80 | -5.8% | +14.2% | +2.9%, +0.6 (3.4) | +12.2%, -0.1 (3.4) | n/n/n | n/n | no |
| 7 | PDmid | +1.4% | 1.78 > 1.80 | -16.1% | +0.2% | +7.1%, -0.1 (1.5) | +11.7%, -0.2 (2.1) | n/n/n | n/n | no |
| 8 | LVN1_1hs | +0.0% | 1.80 > 1.83 | +1.1% | -5.8% | -7.7%, +0.3 (2.3) | +3.6%, -1.2 (3.2) | n/Y/Y | Y/Y | no |
| 9 | OTE705 | +0.0% | 1.78 > 1.80 | +9.7% | +0.0% | -5.9%, +1.9 (3.3) | -15.0%, +1.8 (3.5) | Y/Y/Y | Y/Y | no |
| 10 | HVN0_1hs | +0.0% | 1.80 > 1.78 | +11.3% | +17.7% | +3.7%, +1.0 (2.3) | -6.6%, -0.9 (2.4) | n/n/n | n/n | no |
| 11 | VAH15s | +0.0% | 1.80 > 1.70 | -7.4% | -5.7% | +5.2%, +0.6 (3.4) | +8.8%, +0.1 (2.3) | n/n/n | n/n | no |

Reading: no single line carries the L6M cut; it is a union effect on the 2026-01-19 week (alone: OTE79 -57 -> -41k, kijun1h/OTE62 -57 -> -48.5k, all eight -21k). In PRE+X' only camH3 and VAH15s (uncoded) pass the PX gate and neither is RISK-KEEP; OTE79 and kijun1h cut L6M but fail PRE/X'. The three uncoded lines add nothing to the L6M maxDD. No line is "null" under the pre-declared rule (too strict); the 2047-subset landscape and best-of-N null were NOT run.

## Exact tape-built definitions for the 3 uncoded lines (from confirm/cf_levels_profile.py, used in the POI store)
Tape = 1-s bars (high, low, close, volume) in the study path frame (per-day additive roll offset), prices in 0.25-pt ticks. Profile bins = 1 tick; each second's volume is spread uniformly over the ticks [low, high]. Swing anchoring: 15-m (VAH15s) or 1-h (LVN1, HVN0) bars bucketed by epoch seconds; fractal 2/2 pivots (bar high above 2 bars each side, lows likewise); every consecutive pair of confirmed pivots (any type) defines a leg from the first second of the first pivot bar to the end of the second pivot bar (min 60 tape seconds); the profile becomes usable at the close of the 2nd bar after the second pivot (confirmation). POC = max-volume tick (ties: nearest the volume-weighted mean tick). Value area 70%: start at POC, repeatedly add the side with more volume taking two ticks at a time (ties go down) until >= 70% of total; VAH = top tick of the area. HVN0 = highest peak and LVN1 = second-lowest trough of the volume profile smoothed with a Gaussian sigma = 2.0 pt (8 ticks); peaks need prominence >= 10% of the smoothed max, troughs >= 8%. Line life in the store: 0.8 h (VAH15s), 4 h (LVN1, HVN0) from formation, ended earlier by the first 1-s touch ("fresh" = untouched); several rows can be live, nearest fresh ahead within D = 20 pts between entry and target counts. Limitation: 1-s bar volume approximation, not tick level.

## Not done at this checkpoint
D7-base run (adapter ready, ties exact), full line placebos, equal-risk verification runs (the equal-risk column shows ? where unverified), 2047-subset drop landscape, best-of-N family null, 12R line sensitivity. All to be re-run on the new cap (L1M|L2M|L3M|L6M|HOLD|MID|PRE|X') when REDO-1 and BASE-1 announce.
