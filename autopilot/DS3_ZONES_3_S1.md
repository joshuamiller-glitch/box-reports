
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

# NEW CAP interim 17:27Z (Z1, T-ZONES-3 section 1 on the REDO cap; checkpoint on the lead's order, workers killed)
Cap 20261031 (last day 20261030), windows L1M L2M L3M L6M HOLD MID PRE X' (L1M/L2M view only), REDO engine via redo_boot, 935 label days. POST-HOC, no PASS, Shadow only. Prereg addendum l2vast/ds3/prereg/ZONES3_S1_addendum_redo_prereg.md (sha in DECISIONS.md). Two bases through one engine (d7lib): D7 literal (7 lines D20 skip + OTE-62 B73 D30) and CV (one-convention composite = D.TIE, 8 lines skip D20; ties REDO-2: maxDD 245.1 without / 247.7 with the zone set in L6M).
What ran: all cubes (58 sets incl. 12R and TH-L2-off), equal-risk grids (340 runs), premise bootstrap/leave-one-episode-out for both bases; the 3 uncoded profile lines REBUILT on the new tape (code zones3/s1/build_prf.py, out/zones3/prf_redo/) and validated against the old store (fire-D20 agreement 99.995% on 44,370 common signals). Main stage (placebos, verification runs, subset landscape; 17,118 jobs in out/zones3/s1n/jobs_main.pkl) only 630 jobs done, so NO line placebo ranks, no equal-risk verification, no landscape yet. Premise placebo ranks therefore not yet filled.
## Premise check on the new windows (plain)
* D7 base: the zone set does NOT lower drawdown. maxDD without > with: L6M 92 > 156k, HOLD 201 > 215k, MID 116 > 130k, L3M/L2M/L1M 92 > 92k (unchanged: the Oct-26 week), PRE 250 > 192k (-23%), X' 136 > 127k (-7%). Effect only in PRE/X', bootstrap P(cut>0) 0.69 each; recent windows it is worse (P(cut>0) 0.21-0.22).
* CV composite: L6M 245 > 248k (-1%), HOLD 245 > 248k, MID 205 > 148k (+28%, P 0.84, one episode 2026-03-23), L3M 177 > 173k, PRE 304 > 241k (+21%), X' 118 > 121k (flat). The old-cap Jan-2026 one-week effect is now one of several episodes and is gone from L6M.
* Net: "lowers drawdown in every window" is false on the new windows; recent L6M/HOLD no effect or worse, older windows (PRE) mixed and not chance-distinguishable (placebo pending).
Tables from the run (placebo columns empty):

### D7 base - zone set without > with
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 92 > 92 (+0%) | [-20%, +19%] / 0.69 / 0.03 | 20261026 > 20261026 | n/a | n/a | -60 > -58 * | 31.7 > 34.8 | -0.13 > -0.13 | +0.3 (12.1) | 0.423 / 0.473 (200 / 200) | - |
| L2M (view) (9) | 92 > 92 (+0%) | [-16%, +19%] / 0.64 / 0.01 | 20261026 > 20261026 | n/a | +0% .. +0% | 95 > 70 * | 45.3 > 39.4 | 0.12 > 0.08 | -2.8 (13.4) | 0.428 / 0.473 (200 / 200) | - |
| L3M (13) | 92 > 92 (+0%) | [-8%, +28%] / 0.80 / 0.15 | 20261026 > 20261026 | n/a | +0% .. +21% | 107 > 102 * | 41.4 > 37.0 | 0.09 > 0.09 | -0.4 (9.7) | 0.428 / 0.473 (200 / 200) | - |
| L6M (27) | 92 > 156 (-70%) | [-240%, +6%] / 0.21 / 0.01 | 20261026 > 20260803 | -233% .. +0% (4 drops) | -233% .. +0% | 74 > -112 | 64.8 > 62.8 | 0.37 > 0.15 | -10.4 (12.5) | 0.950 / 0.960 (200 / 200) | 0.881 / 0.975 |
| HOLD (52) | 201 > 215 (-7%) | [-132%, +6%] / 0.22 / 0.01 | 20260216 > 20260302 | -70% .. -7% (8 drops) | -70% .. -2% | -661 > -757 | 61.3 > 58.6 | 0.12 > 0.09 | -6.4 (7.8) | 0.905 / 0.905 (200 / 200) | 0.935 / 0.940 |
| MID (12) | 116 > 130 (-13%) | [-70%, +25%] / 0.18 / 0.07 | 20260216 > 20260302 | n/a | -13% .. -0% | 94 > 33 * | 58.5 > 53.8 | 0.07 > 0.02 | -5.1 (16.0) | 0.871 / 0.826 (200 / 200) | - |
| PRE (75) | 250 > 192 (+23%) | [-26%, +47%] / 0.68 / 0.40 | 20250414 > 20240916 | -20% .. +38% (10 drops) | -20% .. +38% | -878 > -763 | 48.8 > 46.7 | 0.04 > 0.07 | +3.6 (5.5) | 0.622 / 0.522 (200 / 200) | 0.418 / 0.433 |
| X' (44) | 136 > 127 (+7%) | [-28%, +40%] / 0.69 / 0.28 | 20231113 > 20231120 | -10% .. +7% (9 drops) | -10% .. +16% | -475 > -392 | 30.0 > 27.2 | 0.03 > 0.04 | +1.5 (5.8) | 0.632 / 0.612 (200 / 200) | 0.229 / 0.244 |
| ALL (187) | 250 > 215 (+14%) | [-42%, +35%] / 0.54 / 0.19 | 20250414 > 20260302 | -7% .. +23% (12 drops) | -7% .. +29% | -1126 > -1146 | 49.3 > 45.9 | 0.05 > 0.06 | +0.2 (3.6) | 0.741 / 0.652 (200 / 200) | 0.856 / 0.900 |

### D7 base - 12R lock sensitivity
| window | maxDD $k without > with (cut), 12R lock | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 77 > 68 (+12%) | -62 > -58 | -12.3 > -11.5 |
| L2M | 77 > 73 (+5%) | 34 > 16 | 3.8 > 1.8 |
| L3M | 82 > 73 (+10%) | 7 > 3 | 0.6 > 0.3 |
| L6M | 129 > 111 (+14%) | -241 > -256 | 21.3 > 17.2 |
| HOLD | 129 > 111 (+14%) | -542 > -616 | 17.1 > 14.0 |
| MID | 52 > 76 (-47%) | 123 > 21 | 10.2 > 1.7 |
| PRE | 292 > 194 (+34%) | -648 > -590 | 5.5 > 9.2 |
| X' | 194 > 114 (+41%) | -453 > -378 | -1.2 > 4.6 |
| ALL | 292 > 194 (+34%) | -780 > -749 | 8.1 > 10.2 |

### CV base - zone set without > with
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 119 > 137 (-15%) | [-242%, -15%] / 0.00 / 0.05 | 20261026 > 20261026 | n/a | n/a | 72 > 56 * | 83.2 > 94.5 | 0.12 > 0.08 | -3.3 (16.7) | 0.978 / - (183 / 0) | - |
| L2M (view) (9) | 119 > 137 (-15%) | [-15%, +100%] / 0.25 / 0.12 | 20261026 > 20261026 | n/a | -15% .. +8% | 281 > 359 * | 95.2 > 107.8 | 0.26 > 0.29 | +8.7 (20.0) | 0.799 / - (183 / 0) | - |
| L3M (13) | 177 > 173 (+2%) | [-15%, +11%] / 0.22 / 0.02 | 20260907 > 20260831 | n/a | -15% .. +2% | 222 > 294 * | 80.6 > 93.1 | 0.10 > 0.13 | +5.6 (16.8) | 0.288 / - (183 / 0) | - |
| L6M (27) | 245 > 248 (-1%) | [-26%, +11%] / 0.26 / 0.01 | 20260907 > 20260831 | -15% .. -1% (5 drops) | -15% .. +2% | -83 > -128 | 74.5 > 75.4 | 0.12 > 0.11 | -2.1 (12.3) | 0.266 / - (183 / 0) | 0.337 / - |
| HOLD (52) | 245 > 248 (-1%) | [-15%, +34%] / 0.67 / 0.33 | 20260907 > 20260831 | -1% .. +28% (8 drops) | -1% .. +28% | -830 > -696 | 68.7 > 67.1 | 0.11 > 0.12 | +1.1 (8.7) | 0.245 / - (183 / 0) | 0.022 / - |
| MID (12) | 205 > 148 (+28%) | [-42%, +42%] / 0.84 / 0.66 | 20260323 > 20260323 | n/a | -4% .. +28% | 144 > 166 * | 71.5 > 65.7 | 0.06 > 0.09 | +1.8 (22.6) | 0.310 / - (183 / 0) | - |
| PRE (75) | 304 > 241 (+21%) | [-26%, +34%] / 0.76 / 0.29 | 20240930 > 20240930 | +6% .. +21% (9 drops) | -26% .. +21% | -977 > -875 | 59.1 > 55.7 | 0.07 > 0.10 | +2.7 (8.6) | 0.277 / - (183 / 0) | 0.179 / - |
| X' (44) | 118 > 121 (-2%) | [-40%, +55%] / 0.72 / 0.48 | 20230814 > 20230515 | -25% .. +32% (7 drops) | -18% .. +44% | -576 > -420 | 36.1 > 32.6 | 0.04 > 0.07 | +3.8 (7.8) | 0.489 / - (183 / 0) | 0.060 / - |
| ALL (187) | 304 > 248 (+18%) | [-22%, +33%] / 0.69 / 0.26 | 20240930 > 20260831 | -1% .. +21% (12 drops) | -1% .. +21% | -1540 > -1426 | 58.8 > 55.4 | 0.07 > 0.09 | +2.4 (4.8) | 0.071 / - (183 / 0) | 0.304 / - |

### CV base - 12R lock sensitivity
| window | maxDD $k without > with (cut), 12R lock | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 43 > 43 (-0%) | 154 > 171 | 30.9 > 34.2 |
| L2M | 105 > 79 (+25%) | 304 > 404 | 33.8 > 44.9 |
| L3M | 82 > 71 (+13%) | 326 > 424 | 25.1 > 32.6 |
| L6M | 189 > 170 (+10%) | -187 > -248 | 24.7 > 22.9 |
| HOLD | 189 > 170 (+10%) | -496 > -523 | 22.7 > 21.3 |
| MID | 54 > 70 (-31%) | 153 > 98 | 12.8 > 8.2 |
| PRE | 216 > 233 (-8%) | -571 > -608 | 10.4 > 15.1 |
| X' | 312 > 120 (+62%) | -480 > -468 | -6.6 > 1.0 |
| ALL | 354 > 233 (+34%) | -797 > -754 | 11.8 > 15.5 |

### D7 base with TH-L2 exits off
| window | maxDD $k without > with (cut), TH-L2 exits OFF | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 110 > 94 (+15%) | -37 > -37 | -7.3 > -7.4 |
| L2M | 110 > 94 (+15%) | 196 > 267 | 21.7 > 29.7 |
| L3M | 213 > 230 (-8%) | 83 > 126 | 6.4 > 9.7 |
| L6M | 323 > 320 (+1%) | -329 > -408 | 18.4 > 14.0 |
| HOLD | 323 > 320 (+1%) | -968 > -915 | 24.4 > 20.6 |
| MID | 185 > 148 (+20%) | 70 > 11 | 5.8 > 0.9 |
| PRE | 310 > 245 (+21%) | -1222 > -1074 | 18.2 > 22.8 |
| X' | 102 > 114 (-11%) | -626 > -486 | 3.1 > 6.2 |
| ALL | 323 > 320 (+1%) | -1715 > -1571 | 18.6 > 20.6 |

Entry points: code l2vast/ds3/code/zones3/s1/ (boot.py FIRST import; zr.py engine+masks; jobsr.py runner; mkr.py/mkmain.py job lists; sr.py/rp.py scoring; premise_r.py; wr.py table writers incl. line tables, honest/post-hoc rankings, best-of-N, landscape). Resume: `python3 -I jobsr.py main <0|1|2> 3` (resumes from res_main_*.pkl), then premise_r.py, then wr.py writers into the report. Results in out/zones3/s1n/. Old-cap checkpoint above remains for history.

# PROFILE LINES: EXACT DEFINITIONS (user order DIRECTIVE_ZONES3_S1_DEFS_20261101; written wall ~18:00Z 2026-11-01)
Source of truth: `l2vast/ds3/code/confirm/cf_levels_profile.py` (profile_levels, value_area, swing_profiles, pivots, bars), `confirm/cfa1_streams.py` (line life), `poi/poi_core.py` (touch_expiry, feat_kernel, features). Rebuilt on the new cap by `zones3/s1/build_prf.py` (output out/zones3/prf_redo/); the rebuild reproduces the old store's fire-D20 mask on the 44,370 common signals at 99.995%. The three lines share one profile engine; they differ in swing bar size and in which level is read.

| item | VAH15s = PRF\|vah\|sw15 | LVN1_1hs = PRF\|lvn1\|sw1h | HVN0_1hs = PRF\|hvn0\|sw1h |
|---|---|---|---|
| swing bars | 15-minute bars | 1-hour bars | 1-hour bars |
| level read from the leg profile | value-area high | 2nd-lowest smoothed-volume trough | highest smoothed-volume peak |
| life in the store | 0.75 h (median gap of rows) | 4.0 h | 4.0 h |
| rows built (cap 20261030) | 22,552 | 4,029 with a level | 5,623 |

**(a) Price tick and bin.** Price grid = 1 tick = 0.25 pt; profile bin = 1 tick. Prices are the study path frame (raw 1-s price plus the per-day roll offset, median of path close minus raw close), rounded to ticks. Each 1-second bar (high, low, close, volume) puts its volume uniformly over the ticks low..high inclusive: each tick gets volume/(high-low+1). (VWAP uses (h+l+c)/3 and is not part of these lines.) If NT8 used another bin (e.g. 2 or 4 ticks, or volume at close only) the POC/VA/peaks move by that bin and the smoothing below is no longer 8 bins: results are NOT reproduced, see (h).

**(b) Swing anchoring.** Bars: epoch-second buckets of 900 s (15 m) or 3600 s (1 h) on the 1-s tape, only buckets containing data (not clock-aligned to 18:00 ET; the epoch bucket start is a multiple of 900/3600 s, which equals clock alignment for these sizes in UTC). Pivots: fractal 2/2: a bar high strictly above the two bars before and the two bars after is a swing high; the same for lows (a bar can be both). The pivot list is sorted by bar index; EVERY consecutive pair of pivots (any types, not alternating) defines a leg: first tape second of the first pivot bar (inclusive) to the last tape second of the second pivot bar (inclusive). Legs with fewer than 60 tape seconds (rows) are skipped. When a new pivot confirms a new leg (previous pivot to the new pivot) is built and gets its own row; the old row does NOT die: all rows stay live until their own life cap or first touch, so several rows (typically about 1 for VAH15s, 1-2 for the 1-h lines) are live at once, and the nearest fresh one ahead counts.

**(c) Value area and POC.** POC = tick of maximum volume; ties go to the candidate nearest the volume-weighted mean tick. Value area: 70% of total leg volume; start at the POC tick; repeat: volume of the next two ticks below vs the next two ticks above; add the larger side two ticks at a time (ties go DOWN); stop when accumulated >= 70%. VAH = top tick of the area (price = (low tick offset + top index) x 0.25); VAL = bottom tick. Only VAH15s uses this.

**(d) LVN/HVN selection.** Volume per tick smoothed with a Gaussian of sigma 2.0 pt = 8 ticks (scipy gaussian_filter1d, mode constant). HVN: `find_peaks` on the smoothed series with prominence >= 10% of the smoothed maximum; peaks ranked by smoothed height descending; HVN0 = the highest. LVN: `find_peaks` on the negated series with prominence >= 8% of the smoothed maximum; troughs ranked by smoothed volume ascending; LVN0 = lowest, LVN1 = second-lowest (a row exists only if at least two troughs qualify). Price = tick index x 0.25 (path frame).

**(e) Update time.** A row first exists at tk = the close (end second) of the 2nd bar AFTER the second pivot bar (fractal 2/2 confirmation), and is knowable from the first tape second >= tk (the stream index is the first SS print index >= tk). The profile is FROZEN at formation: it uses only the leg's tape up to the end of the second pivot bar, is never developed or re-computed afterwards; the 2 confirming bars are not in it.

**(f) Freshness.** Line life (maxage) = min(median gap between rows of the stream, 30 d) after formation: 0.75 h (VAH15s), 4.0 h (LVN1_1hs, HVN0_1hs). It ends earlier at the first touch: the first 1-second print after formation whose range contains the level, i.e. low_s <= level <= high_s for that second (poi_core.touch_expiry, strict k > formation index). A signal sees a row as FRESH if signal index is in [formation, min(first touch, cap)). Ahead rule: a fresh row counts if its level lies between entry price and target (direction-neutral line, both sides), at distance |level - entry| <= D = 20 pts; the nearest fresh row ahead decides; if any of the stream's lines (or any other line of the set) is within D the signal is skipped.

**(g) Weight on the recent windows.** Not yet fully scored (placebos, equal-risk and landscape wait for the main run). Existing cube rows on the NEW cap (marginal-in-set = the line added to the shipped skip set; one-at-a-time = the line alone vs zone off; maxDD $k before>after, mean change $k/wk; no placebo yet):

| base | line | context | kept trades removed | L6M | HOLD | MID | PRE | X' | mean d L6M / HOLD / MID / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|
| D7 | VAH15s | added to shipped set | 276 | 156>162 (-4%) | 215>205 (+5%) | 130>127 (+2%) | 192>188 (+2%) | 127>118 (+7%) | -0.6 / -0.5 / -0.4 / +0.1 / +0.3 |
| D7 | VAH15s | alone vs zone off | 396 | 92>90 (+2%) | 201>193 (+4%) | 116>116 (+0%) | 250>206 (+17%) | 136>116 (+15%) | -2.0 / -1.4 / -0.8 / +0.2 / +0.3 |
| D7 | LVN1_1hs | added to shipped set | 163 | 156>168 (-8%) | 215>218 (-1%) | 130>135 (-3%) | 192>204 (-6%) | 127>133 (-5%) | +0.1 / +0.4 / +0.2 / -0.2 / -0.1 |
| D7 | LVN1_1hs | alone vs zone off | 275 | 92>90 (+2%) | 201>201 (-0%) | 116>117 (-1%) | 250>213 (+15%) | 136>130 (+4%) | -0.3 / +0.1 / -0.2 / +0.3 / +0.5 |
| D7 | HVN0_1hs | added to shipped set | 255 | 156>160 (-2%) | 215>203 (+6%) | 130>119 (+9%) | 192>192 (-0%) | 127>122 (+3%) | -1.8 / -0.6 / +0.5 / +0.3 / -0.3 |
| D7 | HVN0_1hs | alone vs zone off | 378 | 92>108 (-18%) | 201>201 (+0%) | 116>113 (+2%) | 250>239 (+4%) | 136>138 (-1%) | -1.8 / -1.0 / +0.0 / +0.5 / +0.4 |
| CV | VAH15s | added to shipped set | 265 | 248>256 (-3%) | 248>256 (-3%) | 148>140 (+6%) | 241>229 (+5%) | 121>110 (+9%) | +0.8 / +0.4 / +2.2 / +0.6 / +0.1 |
| CV | VAH15s | alone vs zone off | 406 | 245>233 (+5%) | 245>233 (+5%) | 205>191 (+7%) | 304>283 (+7%) | 118>106 (+11%) | +1.4 / +1.7 / +3.9 / -0.8 / +1.1 |
| CV | LVN1_1hs | added to shipped set | 179 | 248>267 (-8%) | 248>267 (-8%) | 148>145 (+2%) | 241>260 (-8%) | 121>116 (+4%) | +0.0 / +0.6 / -0.2 / +0.3 / -1.2 |
| CV | LVN1_1hs | alone vs zone off | 274 | 245>276 (-13%) | 245>276 (-13%) | 205>213 (-4%) | 304>310 (-2%) | 118>151 (-28%) | +1.0 / +1.2 / -0.5 / +0.8 / -0.7 |
| CV | HVN0_1hs | added to shipped set | 218 | 248>251 (-1%) | 248>251 (-1%) | 148>156 (-5%) | 241>232 (+4%) | 121>128 (-7%) | -0.7 / +0.2 / +0.8 / +1.0 / -0.9 |
| CV | HVN0_1hs | alone vs zone off | 295 | 245>260 (-6%) | 245>260 (-6%) | 205>211 (-3%) | 304>267 (+12%) | 118>136 (-15%) | -0.3 / -0.2 / -1.2 / +1.1 / -2.0 |

Reading: added to the shipped set none of the three lines cuts maxDD in L6M on either base (-2% to -8%, i.e. slightly worse), mean changes are inside noise (|d| <= 2.2k/wk); HVN0_1hs adds +9% in MID on D7, VAH15s +5% HOLD on D7 and +6% MID on CV, all single small cells without placebo. OLD CAP (to 2026-02-06) rows are in the earlier checkpoint above (they cut nothing in L6M either; VAH15s/camH3 only passed the PRE+X' gate). No claim of weight is made; placebo ranks follow in the main run.

**(h) Verdict per line: 1-minute bars in NT8 or the 1-second tape?** Quick test (1 worker, `zones3/s1/prf_1min.py`, result out/zones3/prf_redo/prf_1min_vs_1s.pkl): each line rebuilt from 1-MINUTE bars (volume spread uniformly over [low,high] of the minute, same pivots/smoothing/value-area rules, min leg 1 minute bar, touch = a later 1-minute bar whose [low,high] contains the level, known at that minute's close), compared with the 1-s version on the 88,490 engine signals of the new cap:

| line | legs 1-s / 1-min | line price within 1 tick / within 4 ticks (rows) | fire-D20 count 1-s / 1-min | fire-flag agreement (all signals) | Jaccard of the fired sets | fired only on 1-s / only on 1-min |
|---|---|---|---|---|---|---|
| VAH15s | 22,552 / 22,555 | 35% / 65% | 1,969 / 1,961 | 99.3% | 0.73 | 317 / 309 |
| LVN1_1hs | 3,647 rows with the level / same | 25% / 46% | 1,468 / 1,373 | 98.8% | 0.45 | 583 / 488 |
| HVN0_1hs | 5,621 / same | 38% / 66% | 1,926 / 1,935 | 99.4% | 0.76 | 260 / 269 |

* Swing legs are exact from 1-minute bars (15-m and 1-h bars aggregate exactly; pivots and leg boundaries identical; 22,552 vs 22,555 legs, the 3 extra are leg-length edge cases). The difference is only the volume distribution inside the leg: a minute bar spreads its volume uniformly over its whole range, while the 1-s tape spreads over 60 narrower ranges, so the profile is smoother/wider and VAH/peaks/troughs move by several ticks.
* VERDICT: all three lines NEED THE 1-SECOND TAPE (or tick data) to reproduce the researched lines. From 1-minute bars the lines are the same CONCEPT but a different level (VAH15s 35% of levels within 1 tick, 65% within 4; LVN1_1hs worst, 25% / 46%; HVN0_1hs 38% / 66%) and the fired signal sets overlap only 45-76% (LVN1_1hs least: 583 signals fire only on the 1-s version). VAH15s and HVN0_1hs are the best candidates for a 1-minute approximation (Jaccard 0.73 / 0.76) but would be a NEW rule that must be re-scored, not the researched line; LVN1_1hs should not be built from 1-minute bars (trough ranking is unstable). Touch detection at 1 s vs 1 min matters less than the profile (a level touched inside a minute is seen at that minute's close).
* Exact NT8 inputs: (1) 1-second OHLCV bars of NQ (high, low, volume per second; close not needed for these three lines) for the contract on the study path, with the same roll back-adjustment (additive per-day offset = path close minus raw close); or tick data aggregated to 1 s; (2) 15-minute and 60-minute OHLC bars built from epoch buckets (900 s and 3600 s; NT8 session templates must not shift the bucket start) for fractal 2/2 pivots; (3) the tick size 0.25 and a profile array of ticks from leg low to leg high; (4) the signal's entry price, target price and side, and per-second high/low since line formation for the touch test; (5) state: list of live rows (formation time, level, life cap = 0.75 h or 4 h) updated at each pivot confirmation and at each second for touches. Updates: new row only at pivot confirmation (close of the 2nd bar after the pivot bar); profile never re-computed.
