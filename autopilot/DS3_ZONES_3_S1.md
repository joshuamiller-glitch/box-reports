
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

# NEW CAP, D7 v1.2 - interim (Z1, T-ZONES-3 section 1; written 2026-11-02 00:40Z)

POST-HOC, no PASS claims, Shadow only. Cap 20261031 (last day 20261030), windows L1M L2M L3M L6M HOLD MID PRE X' (L1M/L2M view only, never used to select). Base = D7 v1.2 (d7_v12.py: TH-L2 loss ON, profit OFF, U7 30-min post-cut blackout [agent-built assumption], zones HALF = the 7 non-OTE lines at D20 lots x0.5, OTE-62 B73 D30 unchanged, NY-AM 1 lot K7/H7/M7, X1-X5 + signal-state shadow, 12R lock). Headline frame HALF as shipped; SKIP frame beside. Preregs: ZONES3_S1_prereg.md (09ac46ad...), addendum (redo), addendum2 v12 (sha 3d0b218f1131...) in DECISIONS.md; dead_lookup NOT FOUND. Placebo draws so far: 1532 (tranches; n per context in the tables). Units $k, weekly-cumulative maxDD; worst-20 is not a tail measure in windows with < 20 losing weeks (marked *). Equal-risk = engine lot-table scale c* (ALL worst-20 matched), one verification run; "?" = not yet verified/skip frame.

## Plain answers
INTERIM (tranche placebos: 100 A + 100 B per premise and per M context on v1.1 so far; uncoded lines and OTE62 not yet; ER verification and v1.3 placebos pending). Everything post-hoc.
* PREMISE ("the zone layer lowers drawdown in every window"): on D7 v1.2 the shipped HALF layer cuts maxDD in L3M (70 > 40k, +43%), L6M/HOLD (157 > 128k, +19%) and PRE (198 > 114k, +43%), is flat in X' (270 > 277k) and makes MID WORSE (58 > 92k, the week of 2026-03-23). The SKIP frame cuts more (L6M +27%, PRE +56%, X' +10%, MID -14%). On v1.3 (profit side added) the layer cuts L6M 114 > 94k (+18%), MID +22%, PRE +33%, X' +22%, but L2M/L3M slightly worse (-6% / -4%). So "every window" is not true on v1.2 (X' flat, MID worse) and the recent L1M-L3M effect flips sign with the base.
* CHANCE: on v1.1 (the placebo-bearing base) the layer's cut beats the random-level / same-volume placebo only in PRE (rank 0.050 / 0.040); in L6M/HOLD it is 0.57 / 0.70, L3M 0.43 / 0.55, X' 0.47 / 0.41, MID 0.15 / 0.14: a half-lot layer of the same size would lower drawdown about as much at random. Leave-one-episode-out keeps the cut positive in every window on v1.1 and v1.2 PRE (+11% to +46%), so the cut is not one week on the new windows; it is an ordinary lot-reduction effect that is above chance only in PRE.
* LINES: no single line carries the layer. Under marginal-in-set contribution (sum of maxDD $k cut over L6M+PRE+X') the leaders are CRT4h, OTE-705, OTE-62 (as half line), OTE-62 B73 and kijun1h, but their cuts sit in X' and PRE, not L6M, and no line beats its placebo with PRE and X' agreeing: no line is RISK-KEEP. The three uncoded profile lines add nothing measurable (contribution about 0 to slightly negative; no placebo yet). Definitions: see the earlier section "PROFILE LINES: EXACT DEFINITIONS".


## 1. Premise check: does the 8-line zone layer lower drawdown? (D7 v1.2, zone piece OFF vs the shipped HALF layer; lock 12R)
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 32 > 30 (+6%) | [-575%, +6%] / 0.39 / 0.01 | 20261026 > 20261026 | n/a | n/a | 100 > 92 * | 45.3 > 48.2 | 0.62 > 0.61 | -1.6 (9.0) | 0.500 / - (17 / 0) | - |
| L2M (view) (9) | 73 > 62 (+15%) | [-46%, +20%] / 0.83 / 0.05 | 20260907 > 20260907 | n/a | +6% .. +15% | 133 > 153 * | 50.3 > 51.8 | 0.20 > 0.28 | +2.3 (6.7) | 0.389 / - (17 / 0) | - |
| L3M (13) | 70 > 40 (+43%) | [-3%, +43%] / 0.93 / 0.57 | 20260907 > 20260907 | n/a | +6% .. +43% | 136 > 175 * | 40.1 > 41.1 | 0.15 > 0.34 | +3.0 (5.1) | 0.222 / - (17 / 0) | - |
| L6M (27) | 157 > 128 (+19%) | [-3%, +27%] / 0.84 / 0.16 | 20260907 > 20260907 | +0% .. +19% (5 drops) | +3% .. +19% | -83 > -62 | 62.9 > 60.1 | 0.16 > 0.20 | +0.4 (3.9) | 0.556 / - (17 / 0) | 0.444 / - |
| HOLD (52) | 157 > 128 (+19%) | [-70%, +21%] / 0.47 / 0.07 | 20260907 > 20260907 | +0% .. +19% (9 drops) | -32% .. +19% | -452 > -449 | 55.9 > 53.3 | 0.15 > 0.17 | -2.3 (7.5) | 0.556 / - (17 / 0) | 0.833 / - |
| MID (12) | 58 > 92 (-60%) | [-118%, +21%] / 0.25 / 0.07 | 20260323 > 20260323 | n/a | -60% .. +1% | 213 > 136 * | 50.9 > 48.3 | 0.31 > 0.12 | -6.4 (20.8) | 0.833 / - (17 / 0) | - |
| PRE (75) | 198 > 114 (+43%) | [-1%, +59%] / 0.94 / 0.74 | 20240701 > 20240708 | +32% .. +50% (11 drops) | +27% .. +46% | -540 > -480 | 43.4 > 40.5 | 0.06 > 0.12 | +2.0 (7.7) | 0.056 / - (17 / 0) | 0.444 / - |
| X' (44) | 270 > 277 (-2%) | [-65%, +23%] / 0.41 / 0.07 | 20231204 > 20231218 | -13% .. +5% (5 drops) | -8% .. +13% | -401 > -375 | 21.8 > 18.2 | -0.02 > -0.02 | -0.7 (5.5) | 0.722 / - (17 / 0) | 0.722 / - |
| ALL (187) | 276 > 277 (-0%) | [-25%, +41%] / 0.74 / 0.33 | 20240701 > 20231218 | -5% .. -0% (11 drops) | -6% .. +15% | -707 > -649 | 45.6 > 42.4 | 0.04 > 0.04 | -0.0 (4.0) | 0.667 / - (17 / 0) | 0.778 / - |

### Same pair, SKIP frame (action skip instead of half)
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 32 > 15 (+54%) | [-502%, +54%] / 0.80 / 0.43 | 20261026 > 20261005 | n/a | n/a | 100 > 112 * | 45.3 > 44.9 | 0.62 > 1.50 | +2.5 (13.5) | - / - (0 / 0) | - |
| L2M (view) (9) | 73 > 62 (+14%) | [-73%, +33%] / 0.85 / 0.56 | 20260907 > 20260907 | n/a | +14% .. +54% | 133 > 169 * | 50.3 > 51.0 | 0.20 > 0.30 | +4.0 (7.7) | - / - (0 / 0) | - |
| L3M (13) | 70 > 30 (+57%) | [-1%, +61%] / 0.95 / 0.87 | 20260907 > 20260907 | n/a | +9% .. +57% | 136 > 206 * | 40.1 > 40.4 | 0.15 > 0.53 | +5.4 (6.9) | - / - (0 / 0) | - |
| L6M (27) | 157 > 114 (+27%) | [-2%, +40%] / 0.84 / 0.35 | 20260907 > 20260907 | +0% .. +27% (5 drops) | +7% .. +27% | -83 > -36 | 62.9 > 56.6 | 0.16 > 0.23 | +0.1 (7.1) | - / - (0 / 0) | - / - |
| HOLD (52) | 157 > 114 (+27%) | [-45%, +30%] / 0.52 / 0.17 | 20260907 > 20260907 | +16% .. +27% (8 drops) | -2% .. +27% | -452 > -455 | 55.9 > 50.9 | 0.15 > 0.18 | -3.5 (8.5) | - / - (0 / 0) | - / - |
| MID (12) | 58 > 66 (-14%) | [-102%, +30%] / 0.21 / 0.12 | 20260323 > 20260323 | n/a | -14% .. -11% | 213 > 87 * | 50.9 > 43.2 | 0.31 > 0.11 | -10.5 (24.8) | - / - (0 / 0) | - |
| PRE (75) | 198 > 87 (+56%) | [-4%, +62%] / 0.93 / 0.74 | 20240701 > 20240527 | +47% .. +56% (12 drops) | +34% .. +56% | -540 > -449 | 43.4 > 40.6 | 0.06 > 0.16 | +2.6 (8.9) | - / - (0 / 0) | - / - |
| X' (44) | 270 > 242 (+10%) | [-31%, +55%] / 0.74 / 0.48 | 20231204 > 20231218 | -31% .. +37% (5 drops) | -6% .. +21% | -401 > -400 | 21.8 > 23.2 | -0.02 > -0.01 | +2.5 (7.3) | - / - (0 / 0) | - / - |
| ALL (187) | 276 > 242 (+12%) | [-19%, +50%] / 0.82 / 0.50 | 20240701 > 20231218 | +5% .. +19% (14 drops) | -4% .. +44% | -707 > -642 | 45.6 > 41.5 | 0.04 > 0.05 | +1.0 (4.8) | - / - (0 / 0) | - / - |

### Per book and session, HALF frame (maxDD $k without > with [P(cut>0)] / worst-20 / mean d)
| book / session | L3M maxDD $k without > with [P(cut>0)] / worst-20 / mean d | L6M maxDD $k without > with [P(cut>0)] / worst-20 / mean d | HOLD maxDD $k without > with [P(cut>0)] / worst-20 / mean d | MID maxDD $k without > with [P(cut>0)] / worst-20 / mean d | PRE maxDD $k without > with [P(cut>0)] / worst-20 / mean d | X' maxDD $k without > with [P(cut>0)] / worst-20 / mean d |
|---|---|---|---|---|---|---|
| K6 | 26 > 20 [1.00] / 4 > 23 / +1.4 | 33 > 27 [0.91] / -29 > -23 / -0.1 | 43 > 45 [0.77] / -119 > -109 / -0.2 | 43 > 35 [0.97] / -20 > -2 / +1.5 | 47 > 46 [0.32] / -123 > -129 / -0.4 | 38 > 31 [0.35] / -79 > -75 / -0.4 |
| P6 | 24 > 14 [0.62] / 149 > 149 / +0.0 | 85 > 84 [0.71] / 2 > 7 / +0.4 | 85 > 84 [0.51] / -345 > -352 / -0.7 | 28 > 66 [0.16] / 123 > 59 / -5.3 | 136 > 66 [0.91] / -384 > -356 / +2.4 | 226 > 243 [0.23] / -336 > -324 / -0.6 |
| U6 | 23 > 22 [0.81] / -1 > -6 / -0.4 | 23 > 22 [0.53] / -79 > -74 / -0.4 | 28 > 22 [0.58] / -140 > -135 / -1.0 | 28 > 19 [0.72] / 59 > 51 / -0.6 | 63 > 69 [0.48] / -192 > -181 / -0.3 | 29 > 11 [0.98] / -88 > -50 / +0.4 |
| H6 | 42 > 23 [0.93] / -7 > 8 / +1.2 | 42 > 23 [0.87] / -39 > -23 / +0.4 | 42 > 28 [0.79] / -142 > -119 / -0.2 | 29 > 28 [0.93] / 16 > 15 / -0.1 | 59 > 53 [0.90] / -185 > -165 / +0.3 | 49 > 35 [0.94] / -111 > -85 / +0.2 |
| M6 | 26 > 22 [0.98] / -26 > -22 / +0.3 | 63 > 63 [0.49] / -82 > -80 / -0.0 | 77 > 87 [0.34] / -126 > -131 / -0.2 | 7 > 17 [0.05] / 30 > 14 / -1.3 | 78 > 61 [0.81] / -116 > -110 / +0.1 | 43 > 47 [0.19] / -65 > -63 / -0.1 |
| A6 | 7 > 4 [0.97] / 17 > 24 / +0.5 | 9 > 11 [0.54] / -23 > -19 / +0.1 | 13 > 13 [0.48] / -65 > -60 / -0.1 | 7 > 11 [0.35] / 4 > -2 / -0.5 | 15 > 15 [0.63] / -72 > -61 / -0.1 | 14 > 16 [0.31] / -36 > -37 / -0.2 |
| asia | 69 > 32 [1.00] / 136 > 195 / +4.6 | 93 > 88 [0.91] / -94 > -47 / +0.9 | 93 > 97 [0.57] / -394 > -350 / +0.0 | 63 > 74 [0.29] / 82 > 87 / +0.4 | 146 > 67 [0.96] / -426 > -349 / +1.2 | 218 > 157 [0.93] / -380 > -305 / +0.4 |
| london | 64 > 67 [0.52] / 10 > -23 / -2.6 | 85 > 85 [0.55] / -141 > -161 / -1.1 | 85 > 85 [0.28] / -286 > -305 / -2.0 | 43 > 66 [0.02] / 68 > -2 / -5.8 | 174 > 145 [0.78] / -447 > -433 / +1.3 | 190 > 198 [0.31] / -270 > -255 / -0.5 |
| nyam | 12 > 12 [0.88] / -7 > -0 / +0.5 | 15 > 18 [0.66] / -43 > -38 / +0.0 | 38 > 45 [0.09] / -121 > -143 / -0.8 | 7 > 13 [0.00] / 71 > 51 / -1.6 | 35 > 47 [0.50] / -195 > -195 / -0.3 | 92 > 110 [0.37] / -239 > -230 / -0.6 |
| nypm | 11 > 10 [0.99] / -3 > 3 / +0.5 | 20 > 11 [1.00] / -31 > -19 / +0.5 | 32 > 17 [0.97] / -53 > -43 / +0.4 | 11 > 7 [0.93] / -9 > -1 / +0.6 | 15 > 13 [0.68] / -53 > -52 / -0.1 | 8 > 7 [0.57] / -35 > -30 / +0.0 |

### Combined lock OFF sensitivity, HALF frame
| window | maxDD $k without > with (cut), combined lock OFF (sensitivity; headline has 12R) | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 98 > 99 (-1%) | 61 > 46 | 12.3 > 9.2 |
| L2M | 98 > 99 (-1%) | 150 > 170 | 16.7 > 18.9 |
| L3M | 98 > 99 (-1%) | 134 > 155 | 10.3 > 11.9 |
| L6M | 158 > 119 (+24%) | 66 > 102 | 33.4 > 34.3 |
| HOLD | 186 > 148 (+20%) | -614 > -534 | 28.3 > 29.9 |
| MID | 87 > 55 (+36%) | 241 > 245 | 20.1 > 20.4 |
| PRE | 134 > 139 (-3%) | -837 > -748 | 15.5 > 17.2 |
| X' | 114 > 104 (+9%) | -444 > -429 | 4.7 > 4.5 |
| ALL | 186 > 148 (+20%) | -1189 > -1088 | 17.1 > 18.0 |

### Where the trough week sits and what each line does to it (HALF; $k of that week: line alone vs zone off / marginal)
| window | trough week | without zone | base | kijun1h only / M | PDmid only / M | CRT4h only / M | KCup4h only / M | camH3 only / M | OTE705 only / M | OTE79 only / M | VAH15s only / M | LVN1_1hs only / M | HVN0_1hs only / M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 20260907 | -26 | -14 | -24 / -16 | -26 / -14 | -25 / -15 | -26 / -14 | -26 / -14 | -26 / -14 | -26 / -14 | -26 / -14 | -26 / -14 | -24 / -14 |
| HOLD | 20260907 | -26 | -14 | -24 / -16 | -26 / -14 | -25 / -15 | -26 / -14 | -26 / -14 | -26 / -14 | -26 / -14 | -26 / -14 | -26 / -14 | -24 / -14 |
| MID | 20260323 | -43 | -44 | -44 / -44 | -44 / -44 | -44 / -43 | -43 / -44 | -43 / -44 | -43 / -44 | -43 / -44 | -43 / -44 | -43 / -43 | -43 / -44 |
| PRE | 20240701 | -15 | -14 | -15 / -14 | -15 / -14 | -15 / -15 | -15 / -14 | -15 / -15 | -15 / -14 | -15 / -14 | -15 / -14 | -15 / -14 | -15 / -14 |
| X' | 20231204 | -21 | -16 | -21 / -16 | -20 / -17 | -19 / -16 | -21 / -16 | -21 / -16 | -17 / -16 | -18 / -16 | -17 / -16 | -22 / -20 | -23 / -20 |

## 1b. D7 v1.3 (v1.2 + gated THP take lines U6/P6) - premise pair, HALF layer (cube-level, no placebo yet)
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 17 > 16 (+8%) | [-122%, +50%] / 0.56 / 0.11 | 20261026 > 20261026 | n/a | n/a | 59 > 104 * | 39.1 > 44.2 | 0.68 > 1.29 | +9.0 (44.6) | - / - (0 / 0) | - |
| L2M (view) (9) | 32 > 34 (-6%) | [-118%, +29%] / 0.32 / 0.08 | 20260907 > 20260914 | n/a | -6% .. +8% | 209 > 105 * | 45.1 > 37.3 | 0.72 > 0.34 | -11.5 (45.4) | - / - (0 / 0) | - |
| L3M (13) | 42 > 44 (-4%) | [-87%, +26%] / 0.33 / 0.07 | 20260907 > 20260914 | n/a | -31% .. +8% | 217 > 106 * | 40.3 > 33.1 | 0.40 > 0.19 | -8.5 (31.1) | - / - (0 / 0) | - |
| L6M (27) | 114 > 94 (+18%) | [-54%, +36%] / 0.68 / 0.40 | 20260907 > 20260914 | -48% .. +18% (3 drops) | -5% .. +23% | 85 > -63 | 58.0 > 50.9 | 0.27 > 0.23 | -9.3 (20.2) | - / - (0 / 0) | - / - |
| HOLD (52) | 114 > 94 (+18%) | [-29%, +33%] / 0.75 / 0.38 | 20260907 > 20260914 | -6% .. +21% (9 drops) | -6% .. +23% | -413 > -369 | 51.4 > 47.8 | 0.23 > 0.25 | -3.2 (11.1) | - / - (0 / 0) | - / - |
| MID (12) | 55 > 43 (+22%) | [+2%, +31%] / 1.00 / 0.57 | 20260323 > 20260323 | n/a | +2% .. +22% | 182 > 237 * | 42.3 > 44.6 | 0.28 > 0.46 | +4.6 (9.9) | - / - (0 / 0) | - |
| PRE (75) | 261 > 175 (+33%) | [-54%, +45%] / 0.68 / 0.38 | 20250428 > 20250428 | +7% .. +33% (12 drops) | +0% .. +34% | -572 > -456 | 37.5 > 32.7 | 0.02 > 0.02 | -1.0 (6.7) | - / - (0 / 0) | - / - |
| X' (44) | 299 > 235 (+22%) | [-50%, +47%] / 0.71 / 0.43 | 20240115 > 20231120 | -58% .. +29% (6 drops) | +9% .. +34% | -387 > -369 | 19.9 > 18.8 | -0.02 > -0.02 | +1.0 (5.6) | - / - (0 / 0) | - / - |
| ALL (187) | 341 > 265 (+22%) | [-34%, +43%] / 0.72 / 0.37 | 20240226 > 20250428 | +14% .. +31% (15 drops) | -9% .. +41% | -682 > -562 | 41.7 > 37.6 | 0.03 > 0.03 | -1.0 (4.3) | - / - (0 / 0) | - / - |

### v1.3 line table (HALF, marginal-in-set)
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | kijun1h (coded) | -78 (-0.7%) | 93>94 (-1%) | 93>94 (-1%) | 47>43 (+7%) | 297>175 (+41%) | 253>235 (+7%) | -439>-456 | -384>-369 | -2.7 (7.7) / -0.6 (4.7) / +3.4 (10.3) / +1.5 (3.8) / +0.4 (1.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 2 | OTE62b73 (action) | 77 (0.7%) | 93>94 (-2%) | 93>94 (-2%) | 43>43 (+1%) | 215>175 (+19%) | 275>235 (+15%) | -474>-456 | -366>-369 | -1.2 (12.9) / +0.3 (6.8) / +0.0 (1.3) / +0.1 (2.3) / +1.0 (3.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | n/n/n | n/n | n | n |
| 3 | OTE705 (coded) | 396 (3.5%) | 113>94 (+17%) | 113>94 (+17%) | 45>43 (+4%) | 180>175 (+3%) | 257>235 (+9%) | -469>-456 | -365>-369 | -8.5 (17.6) / -4.3 (9.2) / +0.5 (1.6) / -0.8 (2.4) / +0.7 (2.4) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 4 | CRT4h (coded) | 311 (2.8%) | 89>94 (-6%) | 89>94 (-6%) | 44>43 (+3%) | 190>175 (+8%) | 268>235 (+12%) | -469>-456 | -377>-369 | -0.5 (1.3) / -0.2 (0.9) / +0.1 (2.2) / -0.1 (1.5) / +0.9 (1.3) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 5 | OTE79 (coded) | -29 (-0.3%) | 95>94 (+0%) | 95>94 (+0%) | 43>43 (+0%) | 218>175 (+20%) | 224>235 (-5%) | -463>-456 | -355>-369 | -0.2 (0.6) / +0.2 (0.7) / +1.3 (2.0) / +0.6 (1.2) / -0.1 (1.3) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 6 | OTE62act (coded) | -42 (-0.4%) | 93>83 (+11%) | 93>83 (+11%) | 43>43 (+1%) | 215>201 (+6%) | 275>266 (+3%) | -474>-469 | -366>-362 | +2.6 (7.4) / +1.4 (3.9) / +0.1 (2.5) / +0.1 (0.8) / +0.2 (0.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/Y/Y | Y/Y | n | Y |
| 7 | PDmid (coded) | 40 (0.4%) | 93>94 (-2%) | 93>94 (-2%) | 43>43 (+0%) | 186>175 (+6%) | 253>235 (+7%) | -459>-456 | -386>-369 | -0.6 (1.0) / -0.5 (0.7) / -0.2 (0.8) / +0.2 (0.4) / +0.5 (1.2) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 8 | camH3 (coded) | -12 (-0.1%) | 91>94 (-4%) | 91>94 (-4%) | 43>43 (+0%) | 171>175 (-3%) | 263>235 (+11%) | -449>-456 | -377>-369 | -0.3 (0.7) / -0.6 (0.7) / -1.2 (1.8) / -2.5 (3.5) / +0.8 (2.5) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | KCup4h (coded) | -2 (-0.0%) | 95>94 (+1%) | 95>94 (+1%) | 43>43 (+0%) | 191>175 (+8%) | 218>235 (-7%) | -461>-456 | -356>-369 | +0.0 (0.2) / -0.0 (0.4) / +0.0 (1.1) / -0.3 (2.1) / -0.3 (1.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 10 | HVN0_1hs (UNCODED) | -21 (-0.2%) | 94>91 (+4%) | 94>91 (+4%) | 43>47 (-10%) | 175>198 (-13%) | 235>227 (+3%) | -456>-450 | -369>-359 | -0.8 (2.3) / -0.4 (1.5) / -1.2 (2.2) / -0.3 (1.2) / +0.0 (0.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 11 | LVN1_1hs (UNCODED) | -17 (-0.2%) | 94>94 (-0%) | 94>94 (-0%) | 43>44 (-2%) | 175>184 (-5%) | 235>301 (-28%) | -456>-459 | -369>-373 | +0.4 (2.2) / +0.4 (1.2) / -0.1 (0.7) / -0.0 (0.5) / -1.6 (3.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 12 | VAH15s (UNCODED) | -56 (-0.5%) | 94>97 (-3%) | 94>97 (-3%) | 43>43 (-1%) | 175>254 (-45%) | 235>245 (-4%) | -456>-478 | -369>-379 | -0.3 (0.7) / -0.5 (1.0) / +0.1 (2.5) / -1.3 (1.6) / -0.5 (0.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |

### v1.3 episode-proofing
| line | L6M: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | HOLD: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | MID: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | PRE: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | X': cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag |
|---|---|---|---|---|---|
| kijun1h | -1% / -1% (20260914) / -1%..+2% / 0.27 / no cut | -1% / -1% (20260914) / -1%..+2% / 0.44 / no cut | +7% / +6% (20260323) / +6%..+7% / 0.88 / no cut | +41% / +43% (20250428) / +15%..+45% / 0.75 / holds | +7% / +7% (20231120) / -2%..+11% / 0.73 / no cut |
| OTE62b73 | -2% / -0% (20260907) / -4%..-0% / 0.24 / no cut | -2% / -0% (20260907) / -4%..+0% / 0.51 / no cut | +1% / +0% (20260323) / +0%..+1% / 0.96 / no cut | +19% / +17% (20250428) / -13%..+19% / 0.75 / holds | +15% / +12% (20231218) / -5%..+20% / 0.67 / holds |
| OTE705 | +17% / +24% (20260907) / -32%..+23% / 0.63 / holds | +17% / +24% (20260907) / +1%..+23% / 0.76 / holds | +4% / -0% (20260323) / -0%..+4% / 0.63 / no cut | +3% / +3% (20250428) / -17%..+3% / 0.56 / no cut | +9% / +9% (20231120) / -5%..+13% / 0.67 / no cut |
| CRT4h | -6% / -7% (20260914) / -10%..+5% / 0.15 / no cut | -6% / -7% (20260914) / -10%..-0% / 0.28 / no cut | +3% / -1% (20260323) / -1%..+3% / 0.78 / no cut | +8% / +6% (20250428) / -27%..+11% / 0.42 / no cut | +12% / +13% (20231120) / +5%..+14% / 0.97 / holds |
| OTE79 | +0% / +0% (20260914) / +0%..+2% / 0.60 / no cut | +0% / +0% (20260914) / -7%..+0% / 0.37 / no cut | +0% / -1% (20260323) / -1%..-0% / 0.17 / no cut | +20% / +22% (20250428) / +8%..+20% / 0.83 / holds | -5% / -5% (20231120) / -15%..+2% / 0.36 / no cut |
| OTE62act | +11% / +10% (20260907) / -1%..+13% / 0.72 / holds | +11% / +10% (20260907) / +1%..+13% / 0.74 / holds | +1% / -27% (20260323) / -27%..+1% / 0.62 / no cut | +6% / +5% (20250428) / -0%..+9% / 0.63 / no cut | +3% / +4% (20231218) / +1%..+5% / 0.81 / no cut |
| PDmid | -2% / -2% (20260914) / -2%..-0% / 0.00 / no cut | -2% / -2% (20260914) / -2%..-0% / 0.10 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.08 / no cut | +6% / +6% (20250428) / +1%..+9% / 0.73 / no cut | +7% / +10% (20231120) / +2%..+9% / 0.87 / no cut |
| camH3 | -4% / -4% (20260914) / -4%..-0% / 0.03 / no cut | -4% / -4% (20260914) / -4%..-0% / 0.01 / no cut | +0% / -0% (20260323) / -0%..-0% / 0.00 / no cut | -3% / +1% (20250428) / -52%..-2% / 0.12 / no cut | +11% / +11% (20231218) / -4%..+15% / 0.78 / holds |
| KCup4h | +1% / +2% (20260914) / -0%..+2% / 0.35 / no cut | +1% / +2% (20260914) / -0%..+2% / 0.26 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.00 / no cut | +8% / +11% (20250428) / -17%..+8% / 0.51 / no cut | -7% / -8% (20231120) / -11%..+1% / 0.30 / no cut |
| HVN0_1hs | +4% / +4% (20260914) / -1%..+5% / 0.49 / no cut | +4% / +4% (20260914) / -1%..+5% / 0.32 / no cut | -10% / -25% (20260323) / -25%..-10% / 0.00 / no cut | -13% / -16% (20250428) / -13%..+4% / 0.41 / no cut | +3% / +4% (20231120) / -0%..+5% / 0.67 / no cut |
| LVN1_1hs | -0% / -0% (20260914) / -0%..+11% / 0.67 / no cut | -0% / -0% (20260914) / -0%..+11% / 0.63 / no cut | -2% / +0% (20260323) / -2%..-0% / 0.00 / no cut | -5% / -2% (20250428) / -5%..+5% / 0.46 / no cut | -28% / -27% (20231120) / -36%..-4% / 0.04 / no cut |
| VAH15s | -3% / -4% (20260914) / -6%..+0% / 0.52 / no cut | -3% / -4% (20260914) / -4%..+0% / 0.48 / no cut | -1% / +25% (20260323) / -1%..+25% / 0.43 / no cut | -45% / -45% (20250428) / -45%..-13% / 0.07 / no cut | -4% / -4% (20231120) / -6%..-1% / 0.03 / no cut |

### v1.2 vs v1.3 maxDD cut per line (L6M / HOLD / MID / PRE / X')
| line | v1.2 | v1.3 |
|---|---|---|
| CRT4h | -0% / -0% / -106% / +3% / +12% | -6% / -6% / +3% / +8% / +12% |
| camH3 | +0% / +0% / -109% / +7% / +3% | -4% / -4% / +0% / -3% / +11% |
| OTE79 | +1% / +1% / +2% / +13% / -1% | +0% / +0% / +0% / +20% / -5% |
| OTE62b73 | +4% / +4% / -108% / -0% / +3% | -2% / -2% / +1% / +19% / +15% |
| kijun1h | +3% / +3% / +5% / +14% / -4% | -1% / -1% / +7% / +41% / +7% |
| OTE705 | -3% / -3% / +4% / +15% / -2% | +17% / +17% / +4% / +3% / +9% |
| KCup4h | -0% / -0% / +0% / +2% / +2% | +1% / +1% / +0% / +8% / -7% |
| OTE62act | -11% / -11% / +0% / -7% / +9% | +11% / +11% / +1% / +6% / +3% |
| HVN0_1hs | -3% / -3% / -7% / -2% / +1% | +4% / +4% / -10% / -13% / +3% |
| LVN1_1hs | -3% / -3% / -0% / +8% / -5% | -0% / -0% / -2% / -5% / -28% |
| VAH15s | +1% / +1% / +51% / -9% / -1% | -3% / -3% / -1% / -45% / -4% |
| PDmid | +5% / +5% / +1% / +0% / -9% | -2% / -2% / +0% / +6% / +7% |

## 2. Line table, ranked by drawdown contribution (HALF frame; marginal-in-set: coded line = shipped set minus the line -> shipped set; uncoded = shipped set -> set plus the line)
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | CRT4h (coded) | 186 (1.6%) | 128>128 (-0%) | 128>128 (-0%) | 45>92 (-106%) | 117>114 (+3%) | 315>277 (+12%) | -495>-480 | -375>-375 | -0.3 (1.8) / -1.5 (3.8) / -6.0 (15.9) / +0.3 (0.5) / +1.0 (1.8) | -2.4 / -2.9 / +2.2 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 2 | camH3 (coded) | -4 (-0.0%) | 128>128 (+0%) | 128>128 (+0%) | 44>92 (-109%) | 123>114 (+7%) | 286>277 (+3%) | -482>-480 | -381>-375 | -0.3 (1.0) / -2.3 (3.9) / -7.5 (16.1) / -1.7 (4.7) / +0.2 (1.6) | -2.5 / -4.8 / +1.4 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 3 | OTE79 (coded) | -70 (-0.6%) | 129>128 (+1%) | 129>128 (+1%) | 94>92 (+2%) | 131>114 (+13%) | 273>277 (-1%) | -490>-480 | -374>-375 | +0.2 (1.1) / +0.0 (0.8) / -0.1 (1.2) / +1.4 (2.6) / +0.0 (0.8) | +0.1 / +1.5 / -0.0 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/Y/Y | Y/Y | n | n |
| 4 | OTE62b73 (action) | 193 (1.7%) | 133>128 (+4%) | 133>128 (+4%) | 44>92 (-108%) | 113>114 (-0%) | 286>277 (+3%) | -496>-480 | -383>-375 | -0.2 (2.6) / -1.8 (6.5) / -5.8 (16.3) / +0.7 (1.1) / +0.2 (0.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | n/n/n | n/n | n | n |
| 5 | kijun1h (coded) | -362 (-3.3%) | 132>128 (+3%) | 132>128 (+3%) | 97>92 (+5%) | 133>114 (+14%) | 267>277 (-4%) | -489>-480 | -376>-375 | +0.5 (1.2) / +0.6 (0.9) / +1.4 (2.8) / +3.4 (5.8) / -0.3 (2.2) | -0.1 / +2.9 / +0.9 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/Y/Y | Y/Y | n | n |
| 6 | OTE705 (coded) | -4 (-0.0%) | 124>128 (-3%) | 124>128 (-3%) | 95>92 (+4%) | 134>114 (+15%) | 272>277 (-2%) | -495>-480 | -367>-375 | -0.6 (1.5) / -0.2 (0.9) / +0.8 (1.2) / +0.4 (0.9) / +0.0 (4.0) | -1.0 / +0.7 / +0.2 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 7 | KCup4h (coded) | -10 (-0.1%) | 127>128 (-0%) | 127>128 (-0%) | 92>92 (+0%) | 117>114 (+2%) | 283>277 (+2%) | -478>-480 | -375>-375 | -0.0 (0.1) / +0.0 (0.1) / +0.0 (0.5) / -0.0 (0.6) / +0.2 (0.7) | -0.0 / -0.0 / +0.2 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 8 | OTE62act (coded) | 286 (2.5%) | 133>148 (-11%) | 133>148 (-11%) | 44>44 (+0%) | 113>121 (-7%) | 286>259 (+9%) | -496>-496 | -383>-369 | -0.9 (1.9) / -1.5 (4.7) / -0.3 (2.5) / -2.6 (5.1) / +0.6 (0.9) | -0.9 / -2.5 / +0.5 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | HVN0_1hs (UNCODED) | -17 (-0.2%) | 128>131 (-3%) | 128>131 (-3%) | 92>98 (-7%) | 114>116 (-2%) | 277>274 (+1%) | -480>-474 | -375>-374 | -0.7 (1.9) / -0.3 (1.4) / -0.8 (2.2) / +0.0 (0.8) / -0.1 (0.6) | -1.1 / +0.6 / +0.3 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 10 | LVN1_1hs (UNCODED) | 2 (0.0%) | 128>132 (-3%) | 128>132 (-3%) | 92>93 (-0%) | 114>105 (+8%) | 277>291 (-5%) | -480>-483 | -375>-380 | +0.2 (1.0) / +0.3 (0.6) / -0.0 (0.2) / +0.1 (0.6) / -0.3 (0.5) | +0.1 / +0.0 / -0.3 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 11 | VAH15s (UNCODED) | 14 (0.1%) | 128>127 (+1%) | 128>127 (+1%) | 92>45 (+51%) | 114>124 (-9%) | 277>280 (-1%) | -480>-476 | -375>-382 | -0.2 (0.6) / +1.1 (3.9) / +6.3 (16.7) / -0.7 (1.1) / -0.1 (0.6) | -0.4 / -0.2 / +0.2 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 12 | PDmid (coded) | 172 (1.5%) | 134>128 (+5%) | 134>128 (+5%) | 93>92 (+1%) | 114>114 (+0%) | 255>277 (-9%) | -482>-480 | -368>-375 | -0.1 (1.1) / -1.9 (5.0) / -0.2 (0.8) / +0.1 (0.4) / -0.4 (1.5) | -0.2 / +0.2 / -0.4 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |

### View windows L1M / L2M / L3M (n 5 / 9 / 13 weeks, never selected on)
| line | L1M cut (n 5 wk) | L2M cut (n 9) | L3M cut (n 13) | mean d L1M / L2M / L3M $k/wk |
|---|---|---|---|---|
| CRT4h | +0% (30>30) | +1% (62>62) | -0% (40>40) | +0.0 / +0.2 / +0.1 |
| camH3 | +0% (30>30) | -1% (61>62) | +1% (40>40) | -0.0 / -0.5 / -0.3 |
| OTE79 | +0% (30>30) | +0% (62>62) | +2% (40>40) | -0.7 / +0.7 / +0.5 |
| OTE62b73 | +0% (30>30) | +13% (71>62) | +12% (45>40) | -3.3 / -1.0 / -0.9 |
| kijun1h | +4% (31>30) | +1% (62>62) | +10% (44>40) | +0.4 / +1.7 / +1.4 |
| OTE705 | +0% (30>30) | -2% (61>62) | -10% (36>40) | +0.0 / -0.1 / -0.3 |
| KCup4h | +0% (30>30) | -1% (61>62) | -1% (39>40) | +0.0 / -0.0 / -0.0 |
| OTE62act | +0% (30>30) | +1% (71>70) | -32% (45>60) | -1.8 / -0.7 / -1.6 |
| HVN0_1hs | +0% (30>30) | +0% (62>62) | -8% (40>43) | -0.8 / -1.2 / -1.1 |
| LVN1_1hs | +2% (30>30) | +1% (62>61) | -11% (40>44) | +0.4 / +0.3 / -0.2 |
| VAH15s | +0% (30>30) | +12% (62>54) | +1% (40>39) | +0.2 / +0.8 / +0.0 |
| PDmid | +0% (30>30) | +0% (62>62) | +14% (46>40) | +0.0 / +0.0 / +0.5 |

### One-at-a-time (zone off -> line alone)
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | CRT4h (coded) | 203 (1.8%) | 157>143 (+9%) | 157>143 (+9%) | 58>58 (-1%) | 198>181 (+9%) | 270>221 (+18%) | -540>-498 | -401>-384 | +1.0 (2.0) / +0.4 (1.2) / -0.3 (2.1) / +0.2 (1.8) / +0.1 (3.7) | +0.1 / +0.1 / +1.0 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/Y/Y | Y/Y | n | Y |
| 2 | OTE705 (coded) | 152 (1.3%) | 157>162 (-3%) | 157>162 (-3%) | 58>52 (+10%) | 198>139 (+30%) | 270>259 (+4%) | -540>-513 | -401>-364 | -0.6 (1.7) / -0.1 (1.0) / +0.8 (1.9) / +0.5 (1.6) / +0.4 (3.8) | +0.9 / +2.8 / +0.0 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 3 | kijun1h (coded) | -428 (-3.7%) | 157>150 (+4%) | 157>150 (+4%) | 58>49 (+15%) | 198>171 (+14%) | 270>239 (+12%) | -540>-558 | -401>-380 | +0.1 (1.8) / +0.3 (1.5) / +1.4 (4.8) / +1.2 (4.2) / +1.5 (2.2) | +0.2 / +1.3 / +1.8 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/n/Y | Y/Y | n | Y |
| 4 | PDmid (coded) | 17 (0.1%) | 157>149 (+5%) | 157>149 (+5%) | 58>59 (-2%) | 198>190 (+4%) | 270>247 (+9%) | -540>-551 | -401>-389 | -0.5 (1.7) / -0.5 (1.1) / -0.3 (0.8) / -0.2 (1.5) / +1.1 (2.0) | -0.6 / -0.2 / +1.5 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 5 | HVN0_1hs (UNCODED) | 88 (0.8%) | 157>150 (+4%) | 157>150 (+4%) | 58>58 (+0%) | 198>154 (+23%) | 270>293 (-8%) | -540>-538 | -401>-424 | -0.3 (1.9) / -0.4 (1.1) / -0.5 (1.8) / -0.4 (2.3) / -1.6 (3.8) | -3.2 / +0.9 / +0.5 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 6 | OTE62act (coded) | 152 (1.3%) | 157>170 (-8%) | 157>170 (-8%) | 58>57 (+0%) | 198>153 (+23%) | 270>280 (-3%) | -540>-534 | -401>-394 | -0.4 (1.7) / -0.2 (2.0) / -1.3 (4.5) / -0.9 (3.7) / -1.3 (4.3) | -1.0 / +2.0 / -0.1 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 7 | OTE62b73 (action) | 130 (1.1%) | 157>137 (+13%) | 157>137 (+13%) | 58>57 (+0%) | 198>199 (-0%) | 270>269 (+1%) | -540>-513 | -401>-399 | +0.7 (2.4) / +1.5 (2.9) / -0.6 (1.6) / -0.1 (3.0) / +0.2 (0.6) | +0.7 / +0.7 / +0.0 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | n/n/Y | Y/n | n | n |
| 8 | LVN1_1hs (UNCODED) | 77 (0.7%) | 157>157 (-0%) | 157>157 (-0%) | 58>58 (-0%) | 198>185 (+7%) | 270>272 (-0%) | -540>-538 | -401>-405 | -2.9 (9.7) / -1.4 (5.1) / -0.4 (1.3) / +0.1 (0.7) / -0.1 (0.8) | -2.8 / +0.1 / -0.1 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | KCup4h (coded) | 122 (1.1%) | 157>157 (+0%) | 157>157 (+0%) | 58>58 (+0%) | 198>191 (+4%) | 270>267 (+1%) | -540>-543 | -401>-402 | +0.3 (1.0) / +0.2 (0.6) / +0.1 (0.5) / -1.1 (2.9) / -0.6 (3.5) | -2.0 / -0.7 / +0.3 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 10 | VAH15s (UNCODED) | -157 (-1.4%) | 157>163 (-4%) | 157>163 (-4%) | 58>58 (+0%) | 198>192 (+3%) | 270>269 (+1%) | -540>-531 | -401>-406 | -0.6 (1.3) / -0.3 (0.9) / +1.0 (1.5) / +0.9 (4.1) / +0.8 (2.5) | -2.9 / +0.3 / +1.5 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 11 | OTE79 (coded) | -8 (-0.1%) | 157>155 (+1%) | 157>155 (+1%) | 58>49 (+14%) | 198>192 (+3%) | 270>282 (-4%) | -540>-528 | -401>-398 | +1.0 (2.1) / +1.2 (1.9) / +0.8 (2.3) / -0.2 (4.0) / -0.2 (2.1) | -1.8 / -1.1 / +1.2 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 12 | camH3 (coded) | 174 (1.5%) | 157>158 (-0%) | 157>158 (-0%) | 58>58 (-0%) | 198>206 (-4%) | 270>293 (-8%) | -540>-567 | -401>-369 | -0.4 (1.3) / -0.9 (1.3) / -1.6 (2.7) / -3.8 (6.2) / -0.5 (5.2) | -0.4 / -3.8 / -0.5 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |

### SKIP frame (same lines, action skip), marginal-in-set
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | CRT4h (coded) | 94 (0.9%) | 119>114 (+4%) | 119>114 (+4%) | 67>66 (+1%) | 100>87 (+13%) | 278>242 (+13%) | -484>-449 | -408>-400 | -0.4 (2.4) / -0.5 (1.7) / -0.5 (4.7) / +1.5 (1.3) / +1.0 (3.3) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 2 | OTE79 (coded) | 175 (1.6%) | 118>114 (+3%) | 118>114 (+3%) | 74>66 (+11%) | 146>87 (+40%) | 232>242 (-4%) | -472>-449 | -367>-400 | +0.5 (2.3) / -1.1 (3.6) / -0.8 (4.5) / +1.4 (2.1) / -0.9 (1.5) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | n/n | n | n |
| 3 | OTE705 (coded) | 108 (1.0%) | 110>114 (-3%) | 110>114 (-3%) | 74>66 (+11%) | 92>87 (+5%) | 291>242 (+17%) | -442>-449 | -397>-400 | -0.7 (2.7) / +0.8 (5.9) / +1.3 (1.9) / +0.9 (1.6) / +0.7 (3.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 4 | kijun1h (coded) | 100 (0.9%) | 125>114 (+9%) | 125>114 (+9%) | 76>66 (+13%) | 106>87 (+18%) | 246>242 (+2%) | -442>-449 | -407>-400 | +0.8 (2.5) / +0.2 (2.2) / -1.0 (7.6) / -0.2 (2.9) / +0.2 (1.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | Y |
| 5 | PDmid (coded) | 67 (0.6%) | 125>114 (+9%) | 125>114 (+9%) | 68>66 (+3%) | 88>87 (+1%) | 261>242 (+7%) | -457>-449 | -418>-400 | -0.6 (3.1) / -0.8 (1.9) / -0.2 (1.1) / +0.1 (0.6) / +0.8 (1.3) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 6 | OTE62b73 (action) | 111 (1.0%) | 120>114 (+4%) | 120>114 (+4%) | 48>66 (-36%) | 97>87 (+11%) | 244>242 (+1%) | -463>-449 | -399>-400 | +0.2 (1.7) / +0.4 (3.4) / -3.0 (12.4) / +0.7 (1.1) / -0.0 (0.2) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | n/n/n | n/n | n | Y |
| 7 | KCup4h (coded) | -28 (-0.3%) | 111>114 (-3%) | 111>114 (-3%) | 66>66 (+0%) | 93>87 (+7%) | 256>242 (+5%) | -452>-449 | -407>-400 | -0.2 (0.7) / -0.4 (0.8) / -1.0 (2.6) / +1.1 (3.7) / +0.8 (1.2) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 8 | HVN0_1hs (UNCODED) | 73 (0.7%) | 114>123 (-8%) | 114>123 (-8%) | 66>76 (-16%) | 87>90 (-4%) | 242>220 (+9%) | -449>-483 | -400>-394 | -1.3 (3.5) / -0.6 (2.0) / +0.1 (3.4) / +0.2 (1.9) / +0.0 (1.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | VAH15s (UNCODED) | 84 (0.8%) | 114>109 (+4%) | 114>109 (+4%) | 66>47 (+29%) | 87>92 (-6%) | 242>245 (-1%) | -449>-427 | -400>-421 | +0.1 (1.3) / +0.8 (3.3) / +5.3 (13.6) / -1.0 (4.8) / +0.0 (1.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 10 | camH3 (coded) | 403 (3.7%) | 112>114 (-2%) | 112>114 (-2%) | 45>66 (-47%) | 114>87 (+23%) | 199>242 (-22%) | -447>-449 | -399>-400 | -0.7 (1.7) / -3.9 (4.2) / -7.5 (12.7) / -2.9 (6.2) / -1.2 (3.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 11 | OTE62act (coded) | 265 (2.5%) | 120>152 (-27%) | 120>152 (-27%) | 48>46 (+4%) | 97>88 (+10%) | 244>250 (-3%) | -463>-466 | -399>-423 | -2.3 (4.4) / -2.3 (5.2) / +1.0 (3.6) / -0.8 (2.3) / -0.0 (2.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 12 | LVN1_1hs (UNCODED) | 137 (1.3%) | 114>132 (-16%) | 114>132 (-16%) | 66>71 (-8%) | 87>89 (-2%) | 242>259 (-7%) | -449>-465 | -400>-416 | -2.9 (8.4) / -1.1 (4.4) / -0.4 (1.2) / -0.3 (1.3) / -0.8 (1.2) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |

### Episode-proofing of the line cuts (HALF, marginal-in-set; ONE-WEEK = the cut is >= 10% but vanishes (< 5%) when the week carrying the before-series maxDD trough is dropped)
| line | L6M: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | HOLD: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | MID: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | PRE: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | X': cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag |
|---|---|---|---|---|---|
| CRT4h | -0% / -0% (20260907) / -3%..+0% / 0.18 / no cut | -0% / -0% (20260907) / -11%..+0% / 0.20 / no cut | -106% / -51% (20260323) / -106%..+4% / 0.14 / no cut | +3% / +1% (20240708) / -2%..+4% / 0.85 / no cut | +12% / +12% (20231218) / +6%..+14% / 0.99 / holds |
| camH3 | +0% / +0% (20260907) / -0%..+0% / 0.31 / no cut | +0% / +0% (20260907) / -13%..+0% / 0.15 / no cut | -109% / -57% (20260323) / -109%..-0% / 0.00 / no cut | +7% / +12% (20240708) / +0%..+7% / 0.71 / no cut | +3% / +3% (20231204) / -3%..+7% / 0.66 / no cut |
| OTE79 | +1% / +1% (20260907) / -0%..+1% / 0.48 / no cut | +1% / +1% (20260907) / -0%..+2% / 0.62 / no cut | +2% / +4% (20260323) / -4%..+2% / 0.69 / no cut | +13% / +15% (20240708) / +10%..+15% / 0.90 / holds | -1% / -2% (20231218) / -3%..+1% / 0.61 / no cut |
| OTE62b73 | +4% / -3% (20260907) / -19%..+8% / 0.40 / no cut | +4% / -3% (20260907) / -58%..+8% / 0.21 / no cut | -108% / -61% (20260323) / -108%..-3% / 0.05 / no cut | -0% / -1% (20240708) / -1%..+16% / 0.78 / no cut | +3% / +3% (20231218) / -0%..+4% / 0.76 / no cut |
| kijun1h | +3% / +3% (20260907) / -0%..+5% / 0.64 / no cut | +3% / +3% (20260907) / +1%..+5% / 0.80 / no cut | +5% / +9% (20260323) / -0%..+5% / 0.80 / no cut | +14% / +15% (20240708) / +7%..+14% / 0.91 / holds | -4% / -4% (20231218) / -14%..+5% / 0.32 / no cut |
| OTE705 | -3% / -4% (20260907) / -3%..+1% / 0.23 / no cut | -3% / -4% (20260907) / -3%..+4% / 0.47 / no cut | +4% / +7% (20260323) / -0%..+4% / 0.84 / no cut | +15% / +16% (20240708) / +5%..+15% / 0.83 / holds | -2% / -2% (20231218) / -29%..+14% / 0.50 / no cut |
| KCup4h | -0% / -0% (20260907) / -0%..-0% / 0.00 / no cut | -0% / -0% (20260907) / -0%..-0% / 0.16 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.03 / no cut | +2% / +3% (20240708) / -0%..+3% / 0.60 / no cut | +2% / +2% (20231218) / -3%..+4% / 0.69 / no cut |
| OTE62act | -11% / -14% (20260907) / -17%..+0% / 0.08 / no cut | -11% / -14% (20260907) / -52%..+0% / 0.14 / no cut | +0% / -26% (20260323) / -26%..-0% / 0.11 / no cut | -7% / -1% (20240708) / -10%..+9% / 0.51 / no cut | +9% / +10% (20231218) / +4%..+11% / 0.97 / no cut |
| HVN0_1hs | -3% / -3% (20260907) / -3%..+0% / 0.35 / no cut | -3% / -3% (20260907) / -7%..+0% / 0.18 / no cut | -7% / -12% (20260323) / -23%..-7% / 0.00 / no cut | -2% / +2% (20240708) / -4%..+3% / 0.58 / no cut | +1% / +0% (20231218) / -0%..+2% / 0.48 / no cut |
| LVN1_1hs | -3% / -3% (20260907) / -3%..+0% / 0.57 / no cut | -3% / -3% (20260907) / -3%..+0% / 0.39 / no cut | -0% / -2% (20260323) / -0%..-0% / 0.21 / no cut | +8% / +3% (20240708) / -0%..+10% / 0.63 / no cut | -5% / -4% (20231218) / -6%..-3% / 0.05 / no cut |
| VAH15s | +1% / +1% (20260907) / +0%..+1% / 0.85 / no cut | +1% / +1% (20260907) / +1%..+11% / 0.76 / no cut | +51% / +36% (20260323) / -0%..+51% / 0.78 / holds | -9% / -10% (20240708) / -14%..-1% / 0.26 / no cut | -1% / -1% (20231218) / -4%..+2% / 0.30 / no cut |
| PDmid | +5% / +5% (20260907) / -0%..+5% / 0.39 / no cut | +5% / +5% (20260907) / -0%..+5% / 0.53 / no cut | +1% / +1% (20260323) / -0%..+1% / 0.63 / no cut | +0% / +0% (20240708) / -1%..-0% / 0.34 / no cut | -9% / -10% (20231204) / -12%..+1% / 0.32 / no cut |

### Frame comparison: maxDD cut per line, HALF vs SKIP
| line | HALF (shipped): cut L6M / HOLD / MID / PRE / X' | SKIP frame: cut L6M / HOLD / MID / PRE / X' | mean d L6M HALF / SKIP $k/wk |
|---|---|---|---|
| CRT4h | -0% / -0% / -106% / +3% / +12% | +4% / +4% / +1% / +13% / +13% | -0.3 / -0.4 |
| camH3 | +0% / +0% / -109% / +7% / +3% | -2% / -2% / -47% / +23% / -22% | -0.3 / -0.7 |
| OTE79 | +1% / +1% / +2% / +13% / -1% | +3% / +3% / +11% / +40% / -4% | +0.2 / +0.5 |
| OTE62b73 | +4% / +4% / -108% / -0% / +3% | +4% / +4% / -36% / +11% / +1% | -0.2 / +0.2 |
| kijun1h | +3% / +3% / +5% / +14% / -4% | +9% / +9% / +13% / +18% / +2% | +0.5 / +0.8 |
| OTE705 | -3% / -3% / +4% / +15% / -2% | -3% / -3% / +11% / +5% / +17% | -0.6 / -0.7 |
| KCup4h | -0% / -0% / +0% / +2% / +2% | -3% / -3% / +0% / +7% / +5% | -0.0 / -0.2 |
| OTE62act | -11% / -11% / +0% / -7% / +9% | -27% / -27% / +4% / +10% / -3% | -0.9 / -2.3 |
| HVN0_1hs | -3% / -3% / -7% / -2% / +1% | -8% / -8% / -16% / -4% / +9% | -0.7 / -1.3 |
| LVN1_1hs | -3% / -3% / -0% / +8% / -5% | -16% / -16% / -8% / -2% / -7% | +0.2 / -2.9 |
| VAH15s | +1% / +1% / +51% / -9% / -1% | +4% / +4% / +29% / -6% / -1% | -0.2 / +0.1 |
| PDmid | +5% / +5% / +1% / +0% / -9% | +9% / +9% / +3% / +1% / +7% | -0.1 / -0.6 |

### D7 v1.1 (no U7) HALF frame - the placebo-bearing table (placebos run on v1.1 because a v1.2 draw costs 4x: U7 fixed point); marginal-in-set
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | CRT4h (coded) | 34 (0.3%) | 135>136 (-1%) | 135>136 (-1%) | 43>43 (+2%) | 129>127 (+2%) | 274>234 (+15%) | -514>-502 | -360>-357 | -0.3 (1.9) / +0.3 (1.9) / -0.5 (2.8) / +0.3 (0.5) / +1.0 (1.8) | ? / ? / ? | 0.713/0.634/- ; 0.257/0.287/- ; 0.099/0.059/- (n 100/100/0) | no | n/n/n | n/n | n | n |
| 2 | OTE705 (coded) | 14 (0.1%) | 129>136 (-5%) | 129>136 (-5%) | 43>43 (+0%) | 127>127 (+0%) | 276>234 (+15%) | -527>-502 | -356>-357 | -0.5 (1.6) / -0.2 (1.0) / +0.7 (1.7) / +0.5 (1.0) / +1.1 (3.2) | ? / ? / ? | 0.802/0.934/- ; 0.406/0.426/- ; 0.149/0.131/- (n 100/60/0) | no | n/n/n | n/n | n | n |
| 3 | OTE62act (coded) | -80 (-0.7%) | 151>156 (-3%) | 151>156 (-3%) | 44>44 (+0%) | 131>118 (+9%) | 245>218 (+11%) | -512>-510 | -368>-347 | -0.6 (1.4) / +0.2 (1.6) / +0.4 (1.4) / +0.8 (2.6) / +0.6 (1.0) | ? / ? / ? | 0.882/1.000/- ; 0.118/0.167/- ; 0.216/0.333/- (n 50/5/0) | no | n/n/n | n/n | n | n |
| 4 | OTE62b73 (action) | -25 (-0.2%) | 151>136 (+10%) | 151>136 (+10%) | 44>43 (+3%) | 131>127 (+3%) | 245>234 (+4%) | -512>-502 | -368>-357 | +0.8 (2.5) / +1.7 (2.9) / +0.5 (2.6) / +0.9 (1.3) / +0.3 (0.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | n/n/n | n/n | n | Y |
| 5 | kijun1h (coded) | -254 (-2.2%) | 142>136 (+4%) | 142>136 (+4%) | 43>43 (+0%) | 137>127 (+8%) | 238>234 (+2%) | -518>-502 | -363>-357 | +0.5 (1.2) / +0.2 (0.9) / -0.5 (2.4) / +1.2 (3.3) / +0.1 (2.1) | ? / ? / ? | 0.287/0.267/- ; 0.030/0.089/- ; 0.347/0.455/- (n 100/100/0) | no | Y/Y/Y | Y/Y | n | Y |
| 6 | KCup4h (coded) | -13 (-0.1%) | 137>136 (+1%) | 137>136 (+1%) | 43>43 (+0%) | 135>127 (+6%) | 241>234 (+3%) | -506>-502 | -357>-357 | +0.0 (0.2) / +0.0 (0.2) / +0.0 (0.5) / +0.0 (0.6) / +0.3 (0.7) | ? / ? / ? | 0.347/0.465/- ; 0.059/0.040/- ; 0.356/0.307/- (n 100/100/0) | no | Y/Y/Y | Y/Y | n | Y |
| 7 | OTE79 (coded) | 34 (0.3%) | 137>136 (+1%) | 137>136 (+1%) | 43>43 (+0%) | 141>127 (+11%) | 234>234 (-0%) | -517>-502 | -358>-357 | +1.7 (4.3) / +1.0 (2.4) / -0.6 (2.1) / +0.8 (1.4) / +0.1 (0.9) | ? / ? / ? | 0.627/0.549/- ; 0.118/0.137/- ; 0.824/0.686/- (n 50/50/0) | no | Y/Y/Y | Y/Y | n | n |
| 8 | HVN0_1hs (UNCODED) | 19 (0.2%) | 136>134 (+2%) | 136>134 (+2%) | 43>43 (+0%) | 127>125 (+1%) | 234>236 (-1%) | -502>-496 | -357>-357 | -0.4 (1.6) / -1.1 (2.2) / -0.7 (2.3) / -0.1 (0.9) / -0.2 (0.5) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | PDmid (coded) | 97 (0.8%) | 142>136 (+4%) | 142>136 (+4%) | 43>43 (+0%) | 128>127 (+1%) | 219>234 (-7%) | -504>-502 | -351>-357 | -0.2 (1.5) / -0.5 (1.0) / -0.3 (0.7) / -0.0 (0.3) / -0.3 (1.6) | ? / ? / ? | 0.089/0.119/- ; 0.129/0.198/- ; 0.941/0.950/- (n 100/100/0) | no | n/n/n | n/n | n | n |
| 10 | camH3 (coded) | 104 (0.9%) | 135>136 (-1%) | 135>136 (-1%) | 43>43 (+0%) | 106>127 (-20%) | 248>234 (+6%) | -505>-502 | -368>-357 | -0.3 (0.7) / -1.0 (1.2) / -2.0 (2.9) / -3.9 (6.5) / +0.4 (1.8) | ? / ? / ? | 0.485/0.663/- ; 0.931/0.921/- ; 0.356/0.198/- (n 100/100/0) | no | n/n/n | n/n | n | n |
| 11 | VAH15s (UNCODED) | 18 (0.2%) | 136>140 (-3%) | 136>140 (-3%) | 43>43 (+0%) | 127>125 (+2%) | 234>244 (-4%) | -502>-494 | -357>-366 | -0.5 (1.0) / -0.4 (0.7) / +0.7 (1.2) / -0.6 (1.0) / -0.3 (0.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 12 | LVN1_1hs (UNCODED) | 6 (0.1%) | 136>137 (-0%) | 136>137 (-0%) | 43>67 (-57%) | 127>120 (+5%) | 234>256 (-9%) | -502>-510 | -357>-360 | +0.3 (0.8) / -1.3 (4.3) / -6.9 (18.4) / +0.8 (2.7) / -0.5 (1.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/Y | n | n |

### v1.1 premise pair (zone piece off vs shipped HALF layer)
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 28 > 26 (+5%) | [-113%, +5%] / 0.39 / 0.01 | 20261026 > 20261026 | n/a | n/a | 109 > 110 * | 48.1 > 51.2 | 0.79 > 0.83 | +0.1 (6.7) | 0.545 / 0.455 (100 / 100) | - |
| L2M (view) (9) | 70 > 55 (+22%) | [-11%, +24%] / 0.90 / 0.17 | 20260907 > 20260907 | n/a | +5% .. +22% | 177 > 211 * | 54.6 > 55.6 | 0.28 > 0.43 | +3.7 (5.4) | 0.465 / 0.446 (100 / 100) | - |
| L3M (13) | 85 > 57 (+33%) | [+3%, +40%] / 0.97 / 0.60 | 20260907 > 20260907 | n/a | +10% .. +33% | 163 > 208 * | 45.3 > 46.3 | 0.15 > 0.28 | +3.5 (4.2) | 0.426 / 0.554 (100 / 100) | - |
| L6M (27) | 168 > 136 (+19%) | [+0%, +28%] / 0.97 / 0.23 | 20260907 > 20260907 | +12% .. +19% (5 drops) | +8% .. +33% | -62 > -33 | 66.3 > 65.2 | 0.17 > 0.22 | +2.0 (5.2) | 0.574 / 0.703 (100 / 100) | 0.426 / 0.426 |
| HOLD (52) | 168 > 136 (+19%) | [-3%, +32%] / 0.93 / 0.35 | 20260907 > 20260907 | +14% .. +24% (10 drops) | +8% .. +24% | -454 > -419 | 57.5 > 55.6 | 0.15 > 0.19 | +1.5 (4.7) | 0.574 / 0.703 (100 / 100) | 0.752 / 0.772 |
| MID (12) | 53 > 43 (+20%) | [+5%, +42%] / 0.99 / 0.61 | 20260216 > 20260323 | n/a | +10% .. +42% | 234 > 229 * | 49.7 > 42.9 | 0.36 > 0.45 | -0.4 (9.1) | 0.149 / 0.139 (100 / 100) | - |
| PRE (75) | 184 > 127 (+31%) | [-32%, +52%] / 0.78 / 0.51 | 20240701 > 20240930 | +11% .. +46% (12 drops) | -2% .. +46% | -585 > -502 | 44.3 > 39.4 | 0.06 > 0.08 | -1.0 (6.6) | 0.050 / 0.040 (100 / 100) | 0.208 / 0.139 |
| X' (44) | 291 > 234 (+20%) | [-24%, +38%] / 0.79 / 0.33 | 20231204 > 20231218 | +14% .. +29% (8 drops) | +15% .. +27% | -391 > -357 | 21.2 > 17.7 | -0.02 > -0.02 | +0.8 (5.1) | 0.465 / 0.406 (100 / 100) | 0.267 / 0.188 |
| ALL (187) | 291 > 234 (+20%) | [-11%, +41%] / 0.86 / 0.42 | 20231204 > 20231218 | +14% .. +20% (14 drops) | +15% .. +27% | -745 > -631 | 46.7 > 43.2 | 0.04 > 0.05 | +0.0 (3.2) | 0.356 / 0.317 (100 / 100) | 0.287 / 0.129 |

## 3. Rankings - v1.2 (cube-level; placebo columns thin)
### Honest (selected on PRE+X', recent windows looked at once)
| honest # | line | S_PX = mean(cut PRE, cut X') | cut PRE | cut X' | PX gate | ONE recent look: cut L6M | HOLD | MID | L3M (view L1M) | mean d L6M (MDE) / HOLD / MID | label | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | CRT4h | +0.075 | +3% | +12% | pass | -0% | -0% | -106% | -0% (+0%) | -0.3 (1.8) / -1.5 / -6.0 | no | n/n/n |
| 2 | camH3 | +0.052 | +7% | +3% | pass | +0% | +0% | -109% | +1% (+0%) | -0.3 (1.0) / -2.3 / -7.5 | no | n/n/n |
| - | OTE705 | +0.068 | +15% | -2% | fail: X' no cut, X' w20 worse | -3% | -3% | +4% | -10% (+0%) | -0.6 (1.5) / -0.2 / +0.8 | no | n/n/n |
| - | OTE79 | +0.059 | +13% | -1% | fail: X' no cut, X' w20 worse | +1% | +1% | +2% | +2% (+0%) | +0.2 (1.1) / +0.0 / -0.1 | no | Y/Y/Y |
| - | kijun1h | +0.053 | +14% | -4% | fail: X' no cut | +3% | +3% | +5% | +10% (+4%) | +0.5 (1.2) / +0.6 / +1.4 | no | n/Y/Y |
| - | KCup4h | +0.022 | +2% | +2% | fail: PRE w20 worse | -0% | -0% | +0% | -1% (+0%) | -0.0 (0.1) / +0.0 / +0.0 | no | n/n/n |
| - | LVN1_1hs | +0.015 | +8% | -5% | fail: X' no cut, PRE w20 worse, X' w20 worse, X' mean<-0.5MDE | -3% | -3% | -0% | -11% (+2%) | +0.2 (1.0) / +0.3 / -0.0 | no | n/n/n |
| - | OTE62b73 | +0.013 | -0% | +3% | fail: PRE no cut | +4% | +4% | -108% | +12% (+0%) | -0.2 (2.6) / -1.8 / -5.8 | n/a (action line, no placebo) | n/n/n |
| - | OTE62act | +0.010 | -7% | +9% | fail: PRE no cut, PRE w20 worse, PRE mean<-0.5MDE | -11% | -11% | +0% | -32% (+0%) | -0.9 (1.9) / -1.5 / -0.3 | no | n/n/n |
| - | HVN0_1hs | -0.004 | -2% | +1% | fail: PRE no cut | -3% | -3% | -7% | -8% (+0%) | -0.7 (1.9) / -0.3 / -0.8 | no | n/n/n |
| - | PDmid | -0.043 | +0% | -9% | fail: PRE no cut, X' no cut, X' w20 worse | +5% | +5% | +1% | +14% (+0%) | -0.1 (1.1) / -1.9 / -0.2 | no | n/n/n |
| - | VAH15s | -0.050 | -9% | -1% | fail: PRE no cut, X' no cut, X' w20 worse, PRE mean<-0.5MDE | +1% | +1% | +51% | +1% (+0%) | -0.2 (0.6) / +1.1 / +6.3 | no | n/n/n |

### Post-hoc (L6M cut; PRE/X' beside)
| post-hoc # | line | cut L6M | Calmar L6M before>after | cut HOLD | cut MID | cut L3M | PRE: cut, mean d (MDE) | X': cut, mean d (MDE) | S/T/N | TOL-B/nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | PDmid | +4.7% | 0.19 > 0.20 | +4.7% | +0.8% | +13.7% | +0.0%, +0.1 (0.4) | -8.5%, -0.4 (1.5) | n/n/n | n/n | no |
| 2 | OTE62b73 | +4.0% | 0.20 > 0.20 | +4.0% | -108.1% | +12.0% | -0.5%, +0.7 (1.1) | +3.0%, +0.2 (0.6) | n/n/n | n/n | n/a (action line, no placebo) |
| 3 | kijun1h | +3.2% | 0.19 > 0.20 | +3.2% | +4.9% | +9.8% | +14.4%, +3.4 (5.8) | -3.8%, -0.3 (2.2) | n/Y/Y | Y/Y | no |
| 4 | VAH15s | +0.7% | 0.20 > 0.20 | +0.7% | +50.8% | +0.8% | -9.1%, -0.7 (1.1) | -0.9%, -0.1 (0.6) | n/n/n | n/n | no |
| 5 | OTE79 | +0.6% | 0.20 > 0.20 | +0.6% | +1.9% | +1.8% | +13.3%, +1.4 (2.6) | -1.5%, +0.0 (0.8) | Y/Y/Y | Y/Y | no |
| 6 | camH3 | +0.2% | 0.21 > 0.20 | +0.2% | -108.6% | +0.7% | +7.2%, -1.7 (4.7) | +3.2%, +0.2 (1.6) | n/n/n | n/n | no |
| 7 | CRT4h | -0.0% | 0.21 > 0.20 | -0.0% | -105.8% | -0.0% | +2.9%, +0.3 (0.5) | +12.2%, +1.0 (1.8) | n/n/n | n/n | no |
| 8 | KCup4h | -0.4% | 0.20 > 0.20 | -0.4% | +0.0% | -1.2% | +2.4%, -0.0 (0.6) | +2.0%, +0.2 (0.7) | n/n/n | n/n | no |
| 9 | HVN0_1hs | -2.6% | 0.20 > 0.19 | -2.6% | -6.6% | -8.3% | -1.9%, +0.0 (0.8) | +1.2%, -0.1 (0.6) | n/n/n | n/n | no |
| 10 | LVN1_1hs | -3.1% | 0.20 > 0.20 | -3.1% | -0.5% | -11.1% | +8.0%, +0.1 (0.6) | -5.1%, -0.3 (0.5) | n/n/n | n/n | no |
| 11 | OTE705 | -3.5% | 0.22 > 0.20 | -3.5% | +3.6% | -10.5% | +15.2%, +0.4 (0.9) | -1.7%, +0.0 (4.0) | n/n/n | n/n | no |
| 12 | OTE62act | -11.1% | 0.20 > 0.17 | -11.1% | +0.0% | -32.3% | -7.1%, -2.6 (5.1) | +9.1%, +0.6 (0.9) | n/n/n | n/n | no |

### Best-of-N chance null (v1.2 (cube-level; placebo columns thin); family N=? lines, A-placebo draws, S_PX)
not enough draws yet

## 3. Rankings - v1.1 (placebo-bearing)
### Honest (selected on PRE+X', recent windows looked at once)
| honest # | line | S_PX = mean(cut PRE, cut X') | cut PRE | cut X' | PX gate | ONE recent look: cut L6M | HOLD | MID | L3M (view L1M) | mean d L6M (MDE) / HOLD / MID | label | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE62act | +0.101 | +9% | +11% | pass | -3% | -3% | +0% | +0% (+0%) | -0.6 (1.4) / +0.2 / +0.4 | no | n/n/n |
| 2 | CRT4h | +0.083 | +2% | +15% | pass | -1% | -1% | +2% | -2% (+0%) | -0.3 (1.9) / +0.3 / -0.5 | no | n/n/n |
| 3 | kijun1h | +0.048 | +8% | +2% | pass | +4% | +4% | +0% | +9% (+4%) | +0.5 (1.2) / +0.2 / -0.5 | no | Y/Y/Y |
| 4 | OTE62b73 | +0.038 | +3% | +4% | pass | +10% | +10% | +3% | +15% (-2%) | +0.8 (2.5) / +1.7 / +0.5 | n/a (action line, no placebo) | n/n/n |
| - | OTE705 | +0.077 | +0% | +15% | fail: X' w20 worse | -5% | -5% | +0% | -13% (+0%) | -0.5 (1.6) / -0.2 / +0.7 | no | n/n/n |
| - | OTE79 | +0.052 | +11% | -0% | fail: X' no cut | +1% | +1% | +0% | +2% (+0%) | +1.7 (4.3) / +1.0 / -0.6 | no | Y/Y/Y |
| - | KCup4h | +0.044 | +6% | +3% | fail: X' w20 worse | +1% | +1% | +0% | +2% (+0%) | +0.0 (0.2) / +0.0 / +0.0 | no | Y/Y/Y |
| - | HVN0_1hs | +0.001 | +1% | -1% | fail: X' no cut | +2% | +2% | +0% | +4% (+0%) | -0.4 (1.6) / -1.1 / -0.7 | no | n/n/n |
| - | VAH15s | -0.014 | +2% | -4% | fail: X' no cut, X' w20 worse, PRE mean<-0.5MDE, X' mean<-0.5MDE | -3% | -3% | +0% | -10% (+0%) | -0.5 (1.0) / -0.4 / +0.7 | no | n/n/n |
| - | LVN1_1hs | -0.023 | +5% | -9% | fail: X' no cut, PRE w20 worse, X' w20 worse | -0% | -0% | -57% | -2% (+2%) | +0.3 (0.8) / -1.3 / -6.9 | no | n/n/Y |
| - | PDmid | -0.028 | +1% | -7% | fail: X' no cut, X' w20 worse | +4% | +4% | +0% | +10% (+0%) | -0.2 (1.5) / -0.5 / -0.3 | no | n/n/n |
| - | camH3 | -0.069 | -20% | +6% | fail: PRE no cut, PRE mean<-0.5MDE | -1% | -1% | +0% | -2% (+0%) | -0.3 (0.7) / -1.0 / -2.0 | no | n/n/n |

### Post-hoc (L6M cut; PRE/X' beside)
| post-hoc # | line | cut L6M | Calmar L6M before>after | cut HOLD | cut MID | cut L3M | PRE: cut, mean d (MDE) | X': cut, mean d (MDE) | S/T/N | TOL-B/nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE62b73 | +10.0% | 0.20 > 0.22 | +10.0% | +2.7% | +15.2% | +3.1%, +0.9 (1.3) | +4.5%, +0.3 (0.7) | n/n/n | n/n | n/a (action line, no placebo) |
| 2 | PDmid | +4.4% | 0.22 > 0.22 | +4.4% | +0.0% | +9.9% | +1.2%, -0.0 (0.3) | -6.7%, -0.3 (1.6) | n/n/n | n/n | no |
| 3 | kijun1h | +4.2% | 0.21 > 0.22 | +4.2% | +0.0% | +9.4% | +7.9%, +1.2 (3.3) | +1.6%, +0.1 (2.1) | Y/Y/Y | Y/Y | no |
| 4 | HVN0_1hs | +1.7% | 0.22 > 0.23 | +1.7% | +0.0% | +4.1% | +1.2%, -0.1 (0.9) | -1.1%, -0.2 (0.5) | n/n/n | n/n | no |
| 5 | KCup4h | +1.0% | 0.22 > 0.22 | +1.0% | +0.0% | +2.4% | +6.1%, +0.0 (0.6) | +2.7%, +0.3 (0.7) | Y/Y/Y | Y/Y | no |
| 6 | OTE79 | +0.9% | 0.21 > 0.22 | +0.9% | +0.0% | +2.0% | +10.5%, +0.8 (1.4) | -0.1%, +0.1 (0.9) | Y/Y/Y | Y/Y | no |
| 7 | LVN1_1hs | -0.5% | 0.22 > 0.23 | -0.5% | -56.7% | -2.3% | +4.9%, +0.8 (2.7) | -9.4%, -0.5 (1.1) | n/n/Y | Y/Y | no |
| 8 | camH3 | -0.8% | 0.23 > 0.22 | -0.8% | +0.0% | -1.8% | -19.6%, -3.9 (6.5) | +5.8%, +0.4 (1.8) | n/n/n | n/n | no |
| 9 | CRT4h | -0.9% | 0.23 > 0.22 | -0.9% | +1.5% | -2.3% | +1.8%, +0.3 (0.5) | +14.7%, +1.0 (1.8) | n/n/n | n/n | no |
| 10 | OTE62act | -3.1% | 0.20 > 0.19 | -3.1% | +0.0% | +0.3% | +9.3%, +0.8 (2.6) | +10.9%, +0.6 (1.0) | n/n/n | n/n | no |
| 11 | VAH15s | -3.2% | 0.22 > 0.21 | -3.2% | +0.0% | -9.9% | +1.5%, -0.6 (1.0) | -4.2%, -0.3 (0.6) | n/n/n | n/n | no |
| 12 | OTE705 | -5.4% | 0.24 > 0.22 | -5.4% | +0.0% | -13.5% | +0.3%, +0.5 (1.0) | +15.1%, +1.1 (3.2) | n/n/n | n/n | no |

### Best-of-N chance null (v1.1 (placebo-bearing); family N=? lines, A-placebo draws, S_PX)
not enough draws yet

## 4. Lines that add nothing (pre-declared null rule and sign count; v1.2 and v1.1)
| line | rows newly acted on (all 187 wk) | pre-declared null rule | cuts (dDD% L6M / PRE / X') | mean d / MDE (L6M, PRE, X') | weakness |
|---|---|---|---|---|---|
| PDmid | 414 | not null | +4.7% / +0.0% / -8.5% | -0.06 / +0.16 / -0.28 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| VAH15s | 1321 | not null | +0.7% / -9.1% / -0.9% | -0.34 / -0.65 / -0.22 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| LVN1_1hs | 1008 | not null | -3.1% / +8.0% / -5.1% | +0.16 / +0.10 / -0.64 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| HVN0_1hs | 1207 | not null | -2.6% / -1.9% / +1.2% | -0.38 / +0.00 / -0.17 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| OTE62act | 1414 | not null | -11.1% / -7.1% / +9.1% | -0.48 / -0.51 / +0.63 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| KCup4h | 970 | not null | -0.4% / +2.4% / +2.0% | -0.46 / -0.03 / +0.33 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| OTE705 | 1458 | not null | -3.5% / +15.2% / -1.7% | -0.41 / +0.51 / +0.01 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| kijun1h | 1443 | not null | +3.2% / +14.4% / -3.8% | +0.41 / +0.59 / -0.12 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| OTE62b73 | 0 | not null | +4.0% / -0.5% / +3.0% | -0.08 / +0.58 / +0.36 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| OTE79 | 1664 | not null | +0.6% / +13.3% / -1.5% | +0.19 / +0.56 / +0.01 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| camH3 | 1632 | not null | +0.2% / +7.2% / +3.2% | -0.35 / -0.36 / +0.14 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| CRT4h | 1076 | not null | -0.0% / +2.9% / +12.2% | -0.14 / +0.69 / +0.56 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |

v1.1:
| line | rows newly acted on (all 187 wk) | pre-declared null rule | cuts (dDD% L6M / PRE / X') | mean d / MDE (L6M, PRE, X') | weakness |
|---|---|---|---|---|---|
| LVN1_1hs | 1008 | not null | -0.5% / +4.9% / -9.4% | +0.39 / +0.29 / -0.47 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| VAH15s | 1321 | not null | -3.2% / +1.5% / -4.2% | -0.56 / -0.61 / -0.51 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| camH3 | 1632 | not null | -0.8% / -19.6% / +5.8% | -0.39 / -0.59 / +0.20 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| PDmid | 414 | not null | +4.4% / +1.2% / -6.7% | -0.14 / -0.01 / -0.17 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| HVN0_1hs | 1207 | not null | +1.7% / +1.2% / -1.1% | -0.25 / -0.07 / -0.48 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| OTE79 | 1664 | not null | +0.9% / +10.5% / -0.1% | +0.39 / +0.60 / +0.10 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| KCup4h | 970 | not null | +1.0% / +6.1% / +2.7% | +0.14 / +0.06 / +0.37 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| kijun1h | 1443 | not null | +4.2% / +7.9% / +1.6% | +0.42 / +0.35 / +0.03 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| OTE62b73 | 0 | not null | +10.0% / +3.1% / +4.5% | +0.30 / +0.69 / +0.38 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| OTE62act | 1414 | not null | -3.1% / +9.3% / +10.9% | -0.41 / +0.30 / +0.60 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| OTE705 | 1458 | not null | -5.4% / +0.3% / +15.1% | -0.32 / +0.56 / +0.33 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| CRT4h | 1076 | not null | -0.9% / +1.8% / +14.7% | -0.18 / +0.58 / +0.57 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |

## 5. Subset landscape (v1.1 HALF, 2^10 subsets)
landscape not yet run (0 subsets)

## 6. Per book and per session, marginal-in-set, HALF frame (cell = dDD $k / dWorst20 $k (PRE, X' only) / d mean $k; negative dDD = better)

### by book, L6M
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| CRT4h | -4 / +0.1 | +0 / -0.0 | +0 / -0.6 | -3 / +0.2 | +0 / +0.0 | +0 / +0.0 |
| camH3 | +1 / -0.2 | +0 / +0.1 | +0 / +0.0 | +4 / -0.2 | +2 / -0.1 | +1 / -0.0 |
| OTE79 | +0 / +0.0 | +0 / +0.1 | -2 / +0.3 | -3 / -0.1 | +1 / -0.1 | +1 / -0.0 |
| OTE62b73 | +1 / +0.3 | -1 / -0.5 | +1 / -0.6 | -12 / +0.5 | -1 / +0.0 | +0 / +0.0 |
| kijun1h | +0 / +0.0 | +0 / +0.2 | -6 / +0.4 | -1 / -0.1 | +1 / -0.0 | +0 / +0.1 |
| OTE705 | -1 / -0.5 | +0 / -0.1 | -1 / -0.1 | +3 / +0.0 | -1 / +0.1 | +0 / +0.0 |
| KCup4h | +0 / -0.0 | +0 / +0.0 | +0 / -0.0 | +0 / +0.0 | +0 / -0.0 | +0 / -0.0 |
| OTE62act | +1 / -0.0 | +1 / -0.8 | +4 / -0.3 | -3 / +0.2 | -4 / +0.1 | -2 / -0.1 |
| HVN0_1hs | +4 / -0.2 | +0 / -0.5 | -4 / +0.2 | -2 / -0.1 | +1 / -0.1 | -2 / -0.1 |
| LVN1_1hs | +0 / -0.0 | +0 / +0.1 | -1 / +0.1 | -0 / +0.0 | -1 / +0.0 | +0 / +0.0 |
| VAH15s | +0 / -0.1 | +0 / -0.1 | +0 / +0.2 | +2 / -0.0 | +0 / -0.0 | +5 / -0.2 |
| PDmid | -1 / +0.1 | +0 / -0.1 | +0 / +0.1 | +0 / -0.1 | +0 / +0.0 | -0 / +0.1 |

### by session, L6M
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| CRT4h | +9 / -0.2 | -5 / -0.4 | -4 / +0.2 | -3 / +0.1 |
| camH3 | +3 / -0.2 | +2 / -0.1 | -1 / -0.0 | +0 / +0.0 |
| OTE79 | -1 / +0.2 | -1 / +0.1 | +1 / -0.1 | +0 / +0.0 |
| OTE62b73 | +0 / +1.1 | +2 / -1.5 | +1 / +0.0 | -1 / +0.2 |
| kijun1h | +0 / +0.2 | -3 / +0.2 | -3 / +0.1 | +0 / +0.0 |
| OTE705 | +2 / -0.6 | +0 / -0.1 | +6 / -0.2 | -7 / +0.3 |
| KCup4h | +0 / -0.0 | +0 / -0.0 | +0 / +0.0 | +0 / +0.0 |
| OTE62act | +1 / -1.1 | +3 / +0.1 | -0 / +0.1 | +0 / +0.0 |
| HVN0_1hs | -1 / -0.6 | +0 / -0.0 | +1 / -0.1 | +0 / -0.0 |
| LVN1_1hs | +0 / +0.2 | +1 / +0.0 | +0 / -0.0 | +0 / +0.0 |
| VAH15s | -0 / -0.3 | -4 / +0.0 | -3 / +0.1 | -0 / +0.0 |
| PDmid | -6 / -0.2 | +0 / +0.0 | -3 / +0.1 | +0 / +0.0 |

### by book, HOLD
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| CRT4h | -2 / +0.1 | +0 / -0.8 | +0 / -0.4 | +1 / -0.1 | +8 / -0.1 | +2 / -0.1 |
| camH3 | -2 / -0.1 | +0 / -1.0 | +0 / -0.5 | +0 / -0.4 | +11 / -0.2 | +2 / -0.1 |
| OTE79 | +0 / -0.0 | +0 / +0.2 | -2 / -0.1 | +0 / -0.1 | +1 / -0.0 | +1 / -0.0 |
| OTE62b73 | +5 / +0.1 | -1 / -1.4 | +1 / -0.5 | -7 / -0.1 | +4 / -0.1 | -0 / -0.0 |
| kijun1h | -2 / +0.2 | +0 / +0.0 | -6 / +0.2 | +0 / +0.1 | -1 / +0.0 | +1 / +0.0 |
| OTE705 | -0 / -0.1 | +0 / +0.0 | -1 / -0.2 | +0 / +0.1 | -1 / +0.0 | -1 / -0.0 |
| KCup4h | +1 / -0.0 | +0 / +0.1 | +0 / -0.1 | +0 / +0.0 | -0 / +0.0 | -1 / +0.0 |
| OTE62act | +10 / -0.1 | +1 / -1.5 | +4 / -0.2 | -3 / +0.1 | -9 / +0.2 | -2 / -0.0 |
| HVN0_1hs | +1 / +0.1 | +0 / -0.3 | -3 / +0.1 | +0 / -0.1 | +3 / -0.1 | -1 / -0.0 |
| LVN1_1hs | -0 / -0.0 | +0 / +0.0 | -1 / +0.1 | +0 / +0.1 | -1 / +0.0 | -1 / +0.0 |
| VAH15s | +2 / -0.1 | +0 / +0.7 | +0 / +0.2 | +0 / +0.2 | -9 / +0.1 | +3 / -0.1 |
| PDmid | +10 / -0.4 | +0 / -0.9 | +0 / -0.2 | -1 / -0.4 | +1 / -0.0 | +0 / -0.0 |

### by session, HOLD
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| CRT4h | +16 / -0.7 | -5 / -0.9 | -1 / +0.0 | -4 / +0.1 |
| camH3 | +12 / -0.8 | +2 / -1.3 | +0 / -0.2 | -2 / +0.0 |
| OTE79 | +1 / +0.3 | -1 / -0.2 | +1 / -0.1 | +0 / +0.0 |
| OTE62b73 | +10 / -0.3 | +2 / -1.3 | +10 / -0.5 | -5 / +0.2 |
| kijun1h | -2 / +0.6 | -3 / +0.0 | +0 / +0.0 | +3 / -0.1 |
| OTE705 | -0 / -0.2 | +0 / -0.1 | -0 / -0.1 | -11 / +0.2 |
| KCup4h | +1 / -0.0 | +0 / +0.0 | -1 / +0.0 | +0 / +0.0 |
| OTE62act | +1 / -1.6 | +3 / +0.5 | +14 / -0.4 | -4 / +0.1 |
| HVN0_1hs | +1 / -0.0 | +0 / -0.1 | +2 / -0.1 | +3 / -0.1 |
| LVN1_1hs | -3 / +0.2 | +1 / +0.1 | -2 / +0.0 | +0 / -0.0 |
| VAH15s | -10 / +0.2 | -4 / +0.4 | -16 / +0.6 | +2 / -0.0 |
| PDmid | +4 / -1.5 | +0 / -0.2 | +1 / -0.3 | +1 / -0.0 |

### by book, MID
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| CRT4h | -2 / +0.2 | +37 / -3.5 | +2 / -0.5 | +1 / -1.0 | +4 / -0.6 | +3 / -0.6 |
| camH3 | -2 / +0.2 | +38 / -4.5 | +0 / -0.9 | +0 / -1.1 | +5 / -0.9 | +3 / -0.3 |
| OTE79 | +0 / +0.0 | -1 / +0.2 | -1 / -0.3 | +0 / +0.1 | +0 / +0.0 | +1 / -0.1 |
| OTE62b73 | -5 / +0.5 | +39 / -3.4 | -0 / -0.7 | +0 / -1.0 | +5 / -1.0 | +2 / -0.2 |
| kijun1h | -2 / +0.8 | -2 / -0.4 | +1 / +0.2 | +0 / +0.7 | +0 / +0.2 | +0 / -0.1 |
| OTE705 | +0 / +0.4 | -1 / +0.1 | +0 / +0.0 | +0 / +0.4 | +0 / +0.0 | +0 / +0.0 |
| KCup4h | +0 / -0.1 | +0 / +0.2 | +0 / -0.2 | +0 / +0.0 | +0 / +0.0 | +0 / +0.1 |
| OTE62act | -2 / +0.0 | +5 / -0.5 | +0 / +0.0 | -1 / +0.1 | +0 / -0.0 | +0 / +0.0 |
| HVN0_1hs | +0 / -0.1 | +2 / -0.4 | +0 / -0.1 | +0 / -0.3 | +0 / -0.1 | +0 / +0.1 |
| LVN1_1hs | -0 / +0.0 | -2 / +0.1 | -1 / -0.2 | +0 / -0.1 | +0 / +0.0 | -1 / +0.1 |
| VAH15s | +2 / -0.1 | -40 / +3.6 | +0 / +0.6 | +0 / +1.1 | -5 / +0.8 | -2 / +0.2 |
| PDmid | +0 / +0.0 | +0 / +0.0 | +0 / +0.0 | -1 / +0.1 | +0 / +0.0 | +0 / -0.3 |

### by session, MID
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| CRT4h | +16 / -2.4 | +6 / -3.0 | +4 / -0.7 | -2 / +0.1 |
| camH3 | +23 / -2.0 | +15 / -4.6 | +4 / -1.0 | -2 / +0.1 |
| OTE79 | +1 / -0.1 | -0 / +0.1 | +0 / -0.0 | +0 / +0.0 |
| OTE62b73 | +18 / -1.6 | +9 / -3.8 | +4 / -0.8 | -4 / +0.3 |
| kijun1h | -2 / +2.3 | +8 / -0.5 | +0 / -0.1 | +0 / -0.2 |
| OTE705 | -1 / +0.3 | -2 / +0.2 | -1 / +0.0 | +0 / +0.3 |
| KCup4h | +1 / -0.1 | -2 / +0.1 | +0 / +0.0 | +0 / +0.0 |
| OTE62act | +0 / -0.3 | +0 / +0.5 | +6 / -0.7 | -2 / +0.1 |
| HVN0_1hs | +1 / +0.0 | +2 / -0.3 | +0 / -0.5 | +1 / -0.1 |
| LVN1_1hs | -3 / +0.2 | +3 / -0.3 | +0 / +0.0 | +0 / +0.0 |
| VAH15s | -24 / +2.2 | -9 / +3.5 | -4 / +0.8 | +2 / -0.1 |
| PDmid | -1 / -0.2 | +0 / +0.0 | -0 / +0.0 | +0 / +0.0 |

### by book, PRE
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| CRT4h | -4 / +11 / +0.1 | -4 / +6 / +0.1 | +2 / +0 / +0.0 | -0 / +2 / +0.2 | -4 / +3 / +0.0 | +0 / +1 / -0.0 |
| camH3 | +3 / -5 / -0.3 | -20 / -5 / -0.6 | +10 / -5 / -0.3 | +4 / +4 / -0.3 | +2 / -3 / -0.1 | -1 / +2 / -0.0 |
| OTE79 | -16 / +0 / +0.1 | -21 / +3 / +0.8 | -0 / +16 / +0.2 | -19 / +1 / +0.3 | -9 / +3 / +0.1 | +0 / -1 / -0.1 |
| OTE62b73 | -3 / +2 / -0.0 | +1 / +3 / +0.7 | -2 / +0 / -0.0 | +1 / +2 / +0.0 | +0 / -0 / -0.0 | +0 / +1 / -0.0 |
| kijun1h | -14 / -6 / +0.3 | -11 / +14 / +2.0 | +4 / +0 / -0.0 | +1 / +5 / +0.6 | -0 / -8 / +0.2 | +0 / +3 / +0.2 |
| OTE705 | +3 / -2 / -0.1 | -10 / +13 / +0.4 | -6 / +2 / -0.1 | -2 / +1 / +0.1 | -4 / +4 / +0.1 | +0 / +1 / +0.0 |
| KCup4h | +9 / -5 / -0.1 | -1 / -1 / -0.1 | +3 / +0 / +0.1 | -1 / -2 / +0.0 | -0 / +4 / +0.0 | -0 / +1 / +0.0 |
| OTE62act | -3 / +1 / -0.3 | -0 / +14 / -0.8 | +0 / -4 / -0.5 | +5 / +0 / -0.6 | +0 / +0 / -0.2 | +0 / -0 / -0.2 |
| HVN0_1hs | -4 / +6 / +0.1 | -2 / +7 / -0.1 | -4 / +11 / -0.0 | -3 / +3 / -0.0 | +0 / -0 / +0.0 | -2 / +4 / +0.1 |
| LVN1_1hs | -2 / +1 / +0.0 | -5 / +0 / -0.0 | -8 / +7 / +0.0 | +1 / -1 / +0.0 | -2 / +0 / +0.0 | +0 / +1 / +0.0 |
| VAH15s | -2 / +4 / +0.1 | +20 / +4 / -0.9 | -11 / +5 / +0.1 | +7 / +3 / -0.2 | +0 / +2 / +0.1 | +0 / -0 / -0.0 |
| PDmid | -0 / -1 / -0.0 | +0 / +1 / +0.1 | +1 / +0 / +0.1 | -4 / +4 / -0.0 | +0 / +1 / +0.0 | +0 / +1 / -0.0 |

### by session, PRE
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| CRT4h | -6 / +23 / +0.1 | +3 / +22 / +0.2 | +0 / -0 / +0.0 | +0 / +5 / +0.0 |
| camH3 | -2 / +18 / -0.8 | +16 / -12 / -0.3 | +10 / -9 / -0.4 | -1 / +1 / -0.1 |
| OTE79 | -9 / +9 / -0.2 | -59 / +37 / +1.3 | -1 / +8 / +0.3 | +1 / -5 / -0.0 |
| OTE62b73 | -14 / +5 / +0.6 | -8 / +7 / +0.2 | -0 / -0 / -0.2 | -0 / +0 / -0.0 |
| kijun1h | -29 / +8 / +2.4 | +3 / -33 / +0.4 | -15 / -14 / +0.5 | -4 / -1 / +0.0 |
| OTE705 | +0 / +23 / +0.3 | -8 / +4 / +0.1 | +1 / -0 / +0.1 | +2 / +1 / -0.0 |
| KCup4h | +0 / -0 / +0.1 | -4 / +1 / +0.1 | -0 / -5 / -0.1 | +0 / -1 / -0.1 |
| OTE62act | -7 / +2 / -2.0 | -10 / +6 / +0.1 | +11 / -2 / -0.8 | +0 / +2 / -0.0 |
| HVN0_1hs | +3 / +9 / +0.0 | +2 / +0 / -0.1 | -2 / -3 / +0.1 | +0 / -0 / -0.0 |
| LVN1_1hs | -0 / +0 / +0.0 | -6 / +0 / +0.1 | +1 / -4 / -0.0 | +0 / +1 / +0.0 |
| VAH15s | +9 / +7 / -0.9 | -23 / +27 / +0.3 | +12 / -9 / -0.2 | +0 / +1 / +0.0 |
| PDmid | -9 / +10 / -0.1 | +0 / +8 / +0.1 | +1 / +3 / +0.1 | +0 / +0 / +0.0 |

### by book, X'
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| CRT4h | +1 / -1 / -0.0 | -46 / +24 / +1.2 | +0 / +1 / -0.1 | +0 / +4 / +0.1 | +2 / -1 / -0.0 | -0 / -0 / -0.1 |
| camH3 | +1 / -1 / +0.0 | -6 / +3 / +0.1 | -1 / +4 / +0.2 | -1 / +3 / -0.0 | -0 / +0 / +0.0 | +0 / -2 / -0.0 |
| OTE79 | +1 / -2 / +0.0 | -1 / +2 / +0.0 | -1 / +3 / +0.0 | -0 / +0 / +0.0 | +1 / +1 / -0.0 | +0 / +0 / +0.0 |
| OTE62b73 | -0 / -1 / -0.0 | -11 / +7 / +0.2 | +2 / -1 / -0.0 | -1 / -2 / +0.1 | +0 / -0 / -0.0 | -0 / -0 / -0.0 |
| kijun1h | -11 / +9 / +0.3 | +28 / -19 / -0.6 | -2 / +3 / +0.0 | -6 / +6 / +0.2 | +1 / -0 / -0.0 | +2 / -0 / -0.0 |
| OTE705 | +7 / -7 / -0.4 | +1 / +1 / +0.1 | -1 / +8 / +0.1 | -8 / +10 / +0.2 | +1 / -2 / -0.0 | +2 / -2 / -0.0 |
| KCup4h | -2 / -1 / -0.0 | -2 / +0 / +0.1 | +0 / +3 / +0.1 | +1 / -0 / +0.0 | +1 / -1 / -0.0 | +0 / -0 / +0.1 |
| OTE62act | +0 / +1 / +0.0 | -22 / +16 / +0.5 | +3 / +4 / +0.0 | -3 / -1 / -0.1 | -2 / +2 / +0.1 | -0 / +2 / -0.0 |
| HVN0_1hs | -0 / +1 / +0.0 | -15 / +9 / +0.2 | +5 / -2 / -0.1 | +4 / -3 / -0.2 | +1 / +0 / -0.0 | +0 / -1 / -0.0 |
| LVN1_1hs | +1 / +0 / -0.0 | -0 / -1 / +0.0 | +0 / -1 / -0.1 | +4 / -5 / -0.2 | +0 / +0 / -0.0 | +0 / -1 / -0.0 |
| VAH15s | +2 / -2 / -0.1 | -2 / -3 / +0.1 | +6 / -6 / -0.1 | -8 / +5 / +0.0 | -1 / +2 / +0.0 | +3 / -3 / -0.1 |
| PDmid | -4 / +2 / +0.1 | +28 / -15 / -0.6 | +1 / -2 / +0.1 | -1 / -0 / +0.0 | +2 / -2 / -0.0 | +2 / -1 / -0.1 |

### by session, X'
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| CRT4h | -7 / +6 / +0.4 | -11 / +12 / +0.3 | -3 / +5 / +0.4 | +0 / -1 / -0.0 |
| camH3 | +0 / +16 / -0.0 | +21 / -11 / -0.5 | -17 / -1 / +0.5 | -4 / +0 / +0.3 |
| OTE79 | +3 / -6 / -0.3 | +6 / -2 / -0.1 | -11 / +15 / +0.4 | +1 / +0 / +0.0 |
| OTE62b73 | -0 / -1 / +0.1 | +1 / -0 / -0.1 | -8 / +7 / +0.2 | +1 / -0 / -0.0 |
| kijun1h | +5 / +11 / -0.0 | +12 / -13 / -0.3 | +5 / -6 / -0.2 | -4 / +8 / +0.2 |
| OTE705 | -0 / +9 / +0.4 | +21 / -18 / -0.5 | +10 / +7 / +0.1 | +2 / +1 / -0.1 |
| KCup4h | +7 / +5 / +0.5 | -1 / +2 / +0.0 | +8 / -7 / -0.2 | +0 / -3 / -0.0 |
| OTE62act | -9 / +14 / +0.3 | +3 / +6 / -0.0 | -14 / +13 / +0.3 | +1 / -0 / -0.0 |
| HVN0_1hs | +0 / +1 / +0.0 | +1 / +4 / -0.1 | +0 / +0 / -0.1 | -1 / +1 / +0.0 |
| LVN1_1hs | -1 / +1 / -0.2 | +4 / -3 / -0.1 | +1 / -1 / -0.0 | +0 / +0 / +0.0 |
| VAH15s | +12 / -4 / -0.1 | -15 / +9 / +0.3 | +11 / -5 / -0.3 | +4 / -3 / -0.1 |
| PDmid | +5 / +1 / -0.0 | +5 / -4 / -0.1 | +1 / +1 / -0.4 | -1 / +5 / +0.1 |

Profile definitions of the three uncoded lines: see the section "PROFILE LINES: EXACT DEFINITIONS" above (already published). Code l2vast/ds3/code/zones3/s1/ (zr12.py, jobs12.py, sr12.py, rp12.py, wr12.py, assemble12.py), results out/zones3/s1v12/.

# D7 v1.3-ASSUMED BASE (not the user EXACT v1.3; to be re-run on V13X) ROBUSTNESS SECTION - v13assumed (Z1, T-ZONES-3 section 1; 2026-11-02 02:50Z)

POST-HOC, no PASS claims, Shadow only. New cap 20261031, windows L1M L2M L3M L6M HOLD MID PRE X' (L1M/L2M view only). BASE = ASSUMED D7 v1.3 (v1.2 + gated THP take lines U6/P6; U7 blackout all books; NY-AM lots as assumed; zones HALF; 12R lock) - the user EXACT v1.3 (autopilot/DIRECTIVE_D7V13_EXACT) differs: every row below is ASSUMED BASE and will be re-run on V13X when BASE-4 announces it. Screening base V13x = v1.3 with the post-cut blackout U7 OFF (a v1.3 draw with U7 costs ~5x); V13h = v1.3 with U7 ON (cube-level, finalists); v1.1/v1.2 = comparison only. Placebos: A random-level same-count (stratified), B same-volume random, C shuffled-day line sets; draws so far: 4257 (n per context stated). Preregs: ZONES3_S1 (09ac46ad), addendum redo, addendum2 v12 (3d0b218f1131) in DECISIONS.md. Worst-20 is not a tail measure in windows with < 20 losing weeks (*).

## Plain answers
ALL ROWS BELOW ARE 'ASSUMED BASE' (v1.3-assumed, screen V13x = U7 off; placebo draws 100 per kind and context where stated). They will be re-run on the user's EXACT v1.3 (V13X) when BASE-4 announces it; where the cut changes that is base-dependence.
* LAYER (premise): the shipped HALF layer cuts maxDD on the assumed v1.3 screen in every window by sign (L6M/HOLD +7%, MID +25%, PRE +31%, X' +12%, L3M +19%), but only PRE is near chance-distinguishable on maxDD (rank 0.17 random-level / 0.12 same-volume) and L6M/HOLD are WORSE than a random same-size half-lot cut (rank 0.87 / 0.83). What the layer does beat is the TAIL: worst-20 in PRE -599 > -482k and ALL -753 > -618k, ranks 0.11 / 0.02 (PRE) and 0.10 / 0.02 (ALL) vs random-level / same-volume. With the blackout ON (V13h) the L6M cut is +18% but L2M/L3M flip to -6% / -4%: the recent cut changes sign with the base.
* DEFINITION SENSITIVITY (layer): L6M cut is 1% to 8% at every D (10..40) and -24% with the 'fresh or touched' variant; PRE cut +14% to +34% at all D; so the layer is not D-fragile in PRE but gives essentially nothing in L6M at any D.
* LINES (marginal-in-set, assumed base): only kijun1h (PRE +32%, beats all three placebos in PRE at ranks 0.02 / 0.01 / 0.01, but L6M -1% and X' +6%) and OTE-62 B73 (L6M +13%, PRE +18%, X' +13%, STRICT/TOLERANT/NOW-ONLY all yes, action line so no placebo) look like leads; OTE-62 B73 is the only line with all of L6M, HOLD, PRE, X' cutting. Neither is RISK-KEEP on the full standard (kijun1h fails X' and L6M; B73 has no placebo and PRE+X' cuts are below 20%). CRT4h, camH3, PDmid, KCup4h, OTE705 add nothing consistent. The three uncoded profile lines HURT: VAH15s PRE -18%, HVN0_1hs PRE -14%, LVN1_1hs X' -23% (rank 1.00 on all placebos); they should NOT be added.
* NOT DONE: swing strength / profile bin / anchor-shift variants, 1-s/3-s entry delay (no engine parameter), subset landscape still running, shuffled-day placebo done for premise and lines with draws shown.


## 1. Premise on v1.3 screening base V13x (zone piece off vs shipped HALF layer)
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 21 > 15 (+27%) | [-105%, +57%] / 0.56 / 0.40 | 20261012 > 20261005 | n/a | n/a | 70 > 113 * | 38.9 > 45.3 | 0.66 > 1.47 | +8.6 (52.8) | 0.257 / 0.297 (100 / 100) | - |
| L2M (view) (9) | 37 > 30 (+18%) | [-50%, +39%] / 0.70 / 0.14 | 20260907 > 20260907 | n/a | +18% .. +27% | 224 > 222 * | 48.6 > 46.8 | 0.67 > 0.81 | -0.3 (39.1) | 0.545 / 0.475 (100 / 100) | - |
| L3M (13) | 50 > 41 (+19%) | [-42%, +37%] / 0.69 / 0.15 | 20260907 > 20260907 | n/a | -8% .. +19% | 224 > 217 * | 43.0 > 41.3 | 0.35 > 0.41 | -0.6 (26.6) | 0.416 / 0.386 (100 / 100) | - |
| L6M (27) | 115 > 107 (+7%) | [-16%, +22%] / 0.82 / 0.06 | 20260907 > 20260907 | +0% .. +7% (3 drops) | -1% .. +13% | 4 > -11 | 58.5 > 57.7 | 0.24 > 0.25 | -0.2 (13.4) | 0.871 / 0.871 (100 / 100) | 0.792 / 0.733 |
| HOLD (52) | 115 > 107 (+7%) | [-11%, +36%] / 0.85 / 0.31 | 20260907 > 20260907 | +7% .. +36% (6 drops) | -1% .. +36% | -424 > -391 | 52.5 > 52.3 | 0.20 > 0.23 | +1.2 (7.4) | 0.832 / 0.832 (100 / 100) | 0.683 / 0.594 |
| MID (12) | 89 > 67 (+25%) | [+12%, +51%] / 0.99 / 0.77 | 20260323 > 20260323 | n/a | +25% .. +48% | 86 > 122 * | 42.4 > 38.9 | 0.08 > 0.15 | +3.0 (7.2) | 0.624 / 0.515 (100 / 100) | - |
| PRE (75) | 281 > 192 (+31%) | [-45%, +44%] / 0.73 / 0.41 | 20250428 > 20250428 | +12% .. +33% (10 drops) | -5% .. +36% | -599 > -482 | 39.3 > 33.2 | 0.01 > 0.01 | -1.3 (6.9) | 0.168 / 0.119 (100 / 100) | 0.109 / 0.020 |
| X' (44) | 288 > 253 (+12%) | [-87%, +46%] / 0.60 / 0.36 | 20240115 > 20231120 | +1% .. +24% (8 drops) | -5% .. +35% | -363 > -371 | 20.7 > 19.6 | -0.02 > -0.02 | +0.5 (6.3) | 0.703 / 0.792 (100 / 100) | 0.436 / 0.554 |
| ALL (187) | 326 > 284 (+13%) | [-33%, +41%] / 0.73 / 0.37 | 20240226 > 20250428 | +4% .. +22% (17 drops) | -11% .. +36% | -753 > -618 | 42.6 > 39.9 | 0.03 > 0.03 | -0.1 (3.8) | 0.673 / 0.663 (100 / 100) | 0.099 / 0.020 |

### Same pair with U7 ON (V13h, finalist frame; cube-level)
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 17 > 16 (+8%) | [-122%, +50%] / 0.56 / 0.11 | 20261026 > 20261026 | n/a | n/a | 59 > 104 * | 39.1 > 44.2 | 0.68 > 1.29 | +9.0 (44.6) | - / - (0 / 0) | - |
| L2M (view) (9) | 32 > 34 (-6%) | [-118%, +29%] / 0.32 / 0.08 | 20260907 > 20260914 | n/a | -6% .. +8% | 209 > 105 * | 45.1 > 37.3 | 0.72 > 0.34 | -11.5 (45.4) | - / - (0 / 0) | - |
| L3M (13) | 42 > 44 (-4%) | [-87%, +26%] / 0.33 / 0.07 | 20260907 > 20260914 | n/a | -31% .. +8% | 217 > 106 * | 40.3 > 33.1 | 0.40 > 0.19 | -8.5 (31.1) | - / - (0 / 0) | - |
| L6M (27) | 114 > 94 (+18%) | [-54%, +36%] / 0.68 / 0.40 | 20260907 > 20260914 | -48% .. +18% (3 drops) | -5% .. +23% | 85 > -63 | 58.0 > 50.9 | 0.27 > 0.23 | -9.3 (20.2) | - / - (0 / 0) | - / - |
| HOLD (52) | 114 > 94 (+18%) | [-29%, +33%] / 0.75 / 0.38 | 20260907 > 20260914 | -6% .. +21% (9 drops) | -6% .. +23% | -413 > -369 | 51.4 > 47.8 | 0.23 > 0.25 | -3.2 (11.1) | - / - (0 / 0) | - / - |
| MID (12) | 55 > 43 (+22%) | [+2%, +31%] / 1.00 / 0.57 | 20260323 > 20260323 | n/a | +2% .. +22% | 182 > 237 * | 42.3 > 44.6 | 0.28 > 0.46 | +4.6 (9.9) | - / - (0 / 0) | - |
| PRE (75) | 261 > 175 (+33%) | [-54%, +45%] / 0.68 / 0.38 | 20250428 > 20250428 | +7% .. +33% (12 drops) | +0% .. +34% | -572 > -456 | 37.5 > 32.7 | 0.02 > 0.02 | -1.0 (6.7) | - / - (0 / 0) | - / - |
| X' (44) | 299 > 235 (+22%) | [-50%, +47%] / 0.71 / 0.43 | 20240115 > 20231120 | -58% .. +29% (6 drops) | +9% .. +34% | -387 > -369 | 19.9 > 18.8 | -0.02 > -0.02 | +1.0 (5.6) | - / - (0 / 0) | - / - |
| ALL (187) | 341 > 265 (+22%) | [-34%, +43%] / 0.72 / 0.37 | 20240226 > 20250428 | +14% .. +31% (15 drops) | -9% .. +41% | -682 > -562 | 41.7 > 37.6 | 0.03 > 0.03 | -1.0 (4.3) | - / - (0 / 0) | - / - |

### Per book and session (V13h)
| book / session | L3M maxDD $k without > with [P(cut>0)] / worst-20 / mean d | L6M maxDD $k without > with [P(cut>0)] / worst-20 / mean d | HOLD maxDD $k without > with [P(cut>0)] / worst-20 / mean d | MID maxDD $k without > with [P(cut>0)] / worst-20 / mean d | PRE maxDD $k without > with [P(cut>0)] / worst-20 / mean d | X' maxDD $k without > with [P(cut>0)] / worst-20 / mean d |
|---|---|---|---|---|---|---|
| K6 | 19 > 16 [0.94] / 7 > 13 / +0.5 | 27 > 16 [0.94] / -23 > -13 / -0.0 | 48 > 38 [0.94] / -112 > -90 / -0.1 | 48 > 38 [1.00] / -15 > 2 / +1.4 | 51 > 70 [0.20] / -121 > -134 / -0.8 | 28 > 32 [0.29] / -79 > -76 / -0.2 |
| P6 | 12 > 14 [0.18] / 186 > 134 / -3.9 | 97 > 75 [0.71] / 107 > 21 / -4.1 | 97 > 75 [0.71] / -342 > -308 / -0.4 | 35 > 44 [0.25] / 98 > 119 / +1.8 | 200 > 178 [0.74] / -453 > -404 / +0.7 | 247 > 179 [0.86] / -368 > -316 / +1.9 |
| U6 | 20 > 31 [0.14] / 31 > -16 / -3.6 | 28 > 41 [0.05] / -51 > -89 / -2.1 | 28 > 41 [0.25] / -129 > -145 / -1.0 | 27 > 26 [0.71] / 29 > 39 / +0.9 | 109 > 85 [0.87] / -198 > -160 / +0.3 | 18 > 16 [0.41] / -67 > -57 / -0.4 |
| H6 | 26 > 55 [0.28] / -6 > -24 / -1.4 | 26 > 55 [0.23] / -27 > -57 / -2.6 | 26 > 55 [0.28] / -133 > -116 / -1.4 | 23 > 22 [0.83] / 36 > 45 / +0.8 | 30 > 48 [0.17] / -145 > -147 / -0.9 | 55 > 41 [0.71] / -114 > -97 / -0.1 |
| M6 | 14 > 18 [0.33] / -13 > -18 / -0.4 | 58 > 56 [0.68] / -80 > -70 / +0.0 | 70 > 63 [0.73] / -124 > -113 / +0.1 | 12 > 13 [0.12] / 28 > 27 / -0.1 | 70 > 65 [0.68] / -113 > -102 / +0.2 | 31 > 38 [0.49] / -66 > -61 / -0.1 |
| A6 | 7 > 4 [0.91] / 12 > 16 / +0.3 | 11 > 11 [0.31] / -20 > -27 / -0.5 | 14 > 16 [0.22] / -64 > -63 / -0.4 | 7 > 9 [0.53] / 6 > 5 / -0.1 | 12 > 17 [0.26] / -67 > -62 / -0.4 | 19 > 21 [0.44] / -39 > -36 / -0.1 |
| asia | 28 > 70 [0.08] / 162 > 116 / -3.5 | 79 > 125 [0.29] / 32 > -99 / -8.4 | 79 > 125 [0.38] / -323 > -314 / -3.3 | 52 > 44 [0.69] / 139 > 165 / +2.2 | 139 > 108 [0.59] / -415 > -352 / -1.9 | 240 > 171 [0.87] / -384 > -312 / +1.1 |
| london | 55 > 47 [0.80] / 49 > -9 / -4.4 | 58 > 47 [0.94] / -156 > -131 / -0.5 | 89 > 92 [0.63] / -334 > -298 / -0.7 | 76 > 92 [0.11] / 34 > 13 / -1.7 | 276 > 206 [0.97] / -495 > -386 / +1.8 | 155 > 139 [0.81] / -276 > -220 / +0.4 |
| nyam | 12 > 12 [0.36] / 7 > -7 / -1.0 | 15 > 16 [0.30] / -36 > -40 / -0.9 | 89 > 73 [0.69] / -176 > -162 / +0.6 | 34 > 35 [0.20] / 7 > 50 / +3.6 | 67 > 59 [0.78] / -224 > -179 / -0.5 | 68 > 98 [0.37] / -246 > -246 / -0.5 |
| nypm | 8 > 7 [1.00] / -1 > 5 / +0.5 | 19 > 12 [0.99] / -32 > -21 / +0.4 | 22 > 12 [0.92] / -52 > -45 / +0.2 | 9 > 8 [0.88] / 3 > 8 / +0.4 | 16 > 17 [0.44] / -54 > -50 / -0.4 | 5 > 5 [0.45] / -34 > -33 / +0.0 |

### Combined lock OFF sensitivity (V13h)
| window | maxDD $k without > with (cut), combined lock OFF (sensitivity; headline has 12R) | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 36 > 39 (-8%) | 109 > 93 | 21.7 > 18.6 |
| L2M | 36 > 39 (-8%) | 260 > 249 | 28.9 > 27.7 |
| L3M | 36 > 53 (-45%) | 270 > 252 | 20.8 > 19.4 |
| L6M | 142 > 136 (+5%) | 120 > 118 | 32.0 > 31.2 |
| HOLD | 142 > 136 (+5%) | -544 > -523 | 27.2 > 27.9 |
| MID | 59 > 48 (+19%) | 190 > 225 | 15.9 > 18.8 |
| PRE | 136 > 128 (+6%) | -817 > -684 | 10.8 > 12.6 |
| X' | 199 > 143 (+28%) | -536 > -464 | 0.3 > 0.4 |
| ALL | 199 > 143 (+28%) | -1161 > -1004 | 13.2 > 14.0 |

### Weekly vol terciles (weekly mean daily 1-min range, all 187 weeks): layer effect per line, marginal-in-set (V13x; mean delta $k/wk / worst-week delta / weeks)
| line | low-vol tercile: mean d $k/wk / worst-week d / weeks | mid | high |
|---|---|---|---|
| kijun1h | +0.2 / -7.2 / 62 | -0.5 / -14.5 / 63 | +0.3 / -89.2 / 62 |
| OTE62b73 | -0.3 / -53.8 / 62 | +0.5 / -3.8 / 63 | +3.1 / -15.4 / 62 |
| camH3 | -1.2 / -55.2 / 62 | -0.5 / -42.0 / 63 | -0.3 / -10.9 / 62 |
| OTE79 | +0.0 / -16.7 / 62 | +0.2 / -11.9 / 63 | +2.5 / -4.7 / 62 |
| OTE62act | +0.2 / -6.5 / 62 | -0.1 / -12.2 / 63 | +2.6 / -12.8 / 62 |
| KCup4h | -1.0 / -51.1 / 62 | -0.3 / -9.5 / 63 | +0.4 / -4.2 / 62 |
| OTE705 | +0.6 / -8.1 / 62 | +0.2 / -3.5 / 63 | -0.1 / -10.8 / 62 |
| PDmid | +0.1 / -8.6 / 62 | -0.2 / -7.0 / 63 | -0.5 / -12.2 / 62 |
| HVN0_1hs | -0.3 / -30.8 / 62 | +0.1 / -13.2 / 63 | -0.4 / -10.3 / 62 |
| CRT4h | -0.2 / -35.5 / 62 | -0.3 / -8.5 / 63 | -0.1 / -16.9 / 62 |
| VAH15s | -0.6 / -9.4 / 62 | -0.7 / -18.2 / 63 | -0.5 / -13.8 / 62 |
| LVN1_1hs | -1.1 / -62.8 / 62 | +0.2 / -2.4 / 63 | -0.1 / -17.2 / 62 |

## 2. Line table, V13x, ranked by drawdown contribution (marginal-in-set)
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | kijun1h (coded) | -95 (-0.8%) | 106>107 (-1%) | 106>107 (-1%) | 70>67 (+5%) | 283>192 (+32%) | 270>253 (+6%) | -497>-482 | -388>-371 | -3.3 (9.3) / -1.9 (4.8) / -0.8 (2.0) / +1.2 (3.0) / +0.4 (1.6) | ? / ? / ? | 0.564/0.653/0.634 ; 0.020/0.010/0.010 ; 0.228/0.317/0.178 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 2 | OTE62b73 (action) | -129 (-1.1%) | 123>107 (+13%) | 123>107 (+13%) | 68>67 (+1%) | 236>192 (+18%) | 290>253 (+13%) | -490>-482 | -367>-371 | +3.6 (8.5) / +3.1 (4.7) / +0.9 (2.3) / +0.2 (2.4) / +1.1 (4.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | Y/Y/Y | Y/Y | n | Y |
| 3 | camH3 (coded) | 87 (0.7%) | 107>107 (-0%) | 107>107 (-0%) | 66>67 (-2%) | 199>192 (+3%) | 283>253 (+10%) | -496>-482 | -377>-371 | -0.2 (0.7) / -0.5 (0.7) / -1.1 (1.9) / -1.8 (3.2) / +0.7 (2.5) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 4 | OTE79 (coded) | -83 (-0.7%) | 115>107 (+7%) | 115>107 (+7%) | 64>67 (-5%) | 245>192 (+21%) | 224>253 (-13%) | -495>-482 | -358>-371 | +5.1 (11.3) / +2.9 (5.9) / +0.3 (1.9) / +0.8 (1.2) / -0.6 (1.7) | ? / ? / ? | 0.257/0.139/0.228 ; 0.139/0.069/0.059 ; 0.891/0.941/0.921 (n 100/100/100) | no | n/Y/Y | Y/Y | n | n |
| 5 | OTE62act (coded) | -120 (-1.0%) | 123>123 (-0%) | 123>123 (-0%) | 68>46 (+31%) | 236>225 (+4%) | 290>277 (+5%) | -490>-491 | -367>-362 | +2.5 (8.3) / +3.1 (6.4) / +7.7 (20.7) / +0.0 (0.7) / +0.3 (0.7) | ? / ? / ? | 0.624/0.564/0.634 ; 0.267/0.178/0.248 ; 0.386/0.178/0.356 (n 100/100/100) | no | Y/n/Y | Y/Y | n | n |
| 6 | KCup4h (coded) | -4 (-0.0%) | 109>107 (+1%) | 109>107 (+1%) | 67>67 (+0%) | 219>192 (+12%) | 237>253 (-7%) | -496>-482 | -360>-371 | +0.0 (0.2) / -0.1 (0.4) / -0.0 (1.1) / -0.3 (2.2) / -0.3 (1.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 7 | OTE705 (coded) | 98 (0.8%) | 104>107 (-3%) | 104>107 (-3%) | 76>67 (+12%) | 216>192 (+11%) | 241>253 (-5%) | -501>-482 | -366>-371 | -0.6 (1.4) / -0.1 (0.8) / +0.9 (1.5) / +0.3 (0.8) / -0.1 (0.8) | ? / ? / ? | 0.733/0.683/0.832 ; 0.198/0.149/0.158 ; 0.842/0.842/0.891 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 8 | PDmid (coded) | 53 (0.5%) | 106>107 (-1%) | 106>107 (-1%) | 67>67 (-1%) | 194>192 (+1%) | 249>253 (-2%) | -486>-482 | -384>-371 | -0.7 (1.3) / -0.8 (0.9) / -0.3 (0.7) / +0.1 (0.4) / -0.0 (1.3) | ? / ? / ? | 0.782/0.733/0.804 ; 0.317/0.277/0.375 ; 0.881/0.772/0.875 (n 100/100/55) | no | n/n/n | n/n | n | n |
| 9 | HVN0_1hs (UNCODED) | 3 (0.0%) | 107>104 (+3%) | 107>104 (+3%) | 67>73 (-9%) | 192>219 (-14%) | 253>243 (+4%) | -482>-479 | -371>-361 | -0.5 (1.9) / -0.1 (1.4) / -1.1 (2.3) / -0.4 (1.3) / +0.1 (0.7) | ? / ? / ? | 0.317/0.297/0.228 ; 0.911/0.851/0.911 ; 0.307/0.307/0.327 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 10 | CRT4h (coded) | 227 (1.9%) | 103>107 (-4%) | 103>107 (-4%) | 68>67 (+1%) | 189>192 (-2%) | 247>253 (-3%) | -480>-482 | -380>-371 | -0.3 (1.4) / -0.2 (0.9) / -0.4 (2.0) / -0.3 (1.2) / -0.1 (2.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 11 | VAH15s (UNCODED) | -84 (-0.7%) | 107>110 (-2%) | 107>110 (-2%) | 67>66 (+1%) | 192>227 (-18%) | 253>268 (-6%) | -482>-495 | -371>-383 | -0.5 (0.9) / -0.3 (1.3) / +1.1 (3.9) / -0.8 (1.0) / -0.6 (0.7) | ? / ? / ? | 0.723/0.723/0.762 ; 0.812/0.921/0.881 ; 0.891/0.901/0.970 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 12 | LVN1_1hs (UNCODED) | 159 (1.4%) | 107>108 (-0%) | 107>108 (-0%) | 67>69 (-2%) | 192>195 (-1%) | 253>312 (-23%) | -482>-469 | -371>-376 | -0.2 (1.5) / +0.0 (0.8) / +0.0 (0.7) / -0.0 (0.8) / -1.5 (4.0) | ? / ? / ? | 0.554/0.604/0.545 ; 0.465/0.426/0.426 ; 1.000/1.000/1.000 (n 100/100/100) | no | n/n/n | n/n | n | n |

### One-at-a-time (zone off -> line alone), V13x
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE62b73 (action) | -229 (-1.9%) | 115>93 (+19%) | 115>93 (+19%) | 89>89 (+0%) | 281>196 (+30%) | 288>218 (+24%) | -599>-588 | -363>-363 | +4.1 (8.3) / +3.8 (4.8) / +2.0 (5.5) / +1.7 (2.4) / +2.5 (5.0) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | Y/Y/Y | Y/Y | Y | Y |
| 2 | PDmid (coded) | 179 (1.5%) | 115>116 (-1%) | 115>116 (-1%) | 89>87 (+2%) | 281>246 (+12%) | 288>249 (+14%) | -599>-565 | -363>-349 | -1.1 (1.8) / -1.0 (1.2) / +0.1 (1.1) / -0.8 (4.7) / +1.6 (2.0) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 3 | CRT4h (coded) | 246 (2.0%) | 115>111 (+4%) | 115>111 (+4%) | 89>88 (+1%) | 281>262 (+7%) | 288>247 (+14%) | -599>-533 | -363>-356 | +0.2 (1.1) / +0.0 (0.7) / -0.5 (1.8) / +0.5 (3.1) / +1.6 (1.8) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/Y/Y | Y/Y | n | Y |
| 4 | OTE62act (coded) | -124 (-1.0%) | 115>115 (-0%) | 115>115 (-0%) | 89>89 (+0%) | 281>249 (+11%) | 288>267 (+7%) | -599>-569 | -363>-363 | +2.7 (8.1) / +1.4 (4.3) / +0.4 (1.2) / +0.3 (3.2) / +2.3 (3.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/Y/Y | Y/Y | n | n |
| 5 | kijun1h (coded) | -36 (-0.3%) | 115>119 (-3%) | 115>119 (-3%) | 89>80 (+10%) | 281>258 (+8%) | 288>263 (+9%) | -599>-563 | -363>-370 | -3.7 (9.1) / -1.9 (4.8) / +0.5 (2.4) / +0.6 (6.1) / +0.7 (3.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 6 | OTE705 (coded) | 70 (0.6%) | 115>123 (-7%) | 115>123 (-7%) | 89>73 (+18%) | 281>275 (+2%) | 288>259 (+10%) | -599>-567 | -363>-369 | -0.8 (1.7) / +0.0 (1.2) / +1.7 (3.0) / -0.1 (2.7) / +1.2 (4.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 7 | camH3 (coded) | 150 (1.2%) | 115>118 (-2%) | 115>118 (-2%) | 89>90 (-1%) | 281>253 (+10%) | 288>299 (-4%) | -599>-578 | -363>-364 | -0.2 (1.0) / +0.0 (1.3) / +1.1 (4.5) / -1.4 (4.8) / +0.2 (4.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 8 | LVN1_1hs (UNCODED) | 146 (1.2%) | 115>116 (-1%) | 115>116 (-1%) | 89>94 (-5%) | 281>290 (-3%) | 288>288 (-0%) | -599>-596 | -363>-376 | -0.2 (1.7) / -0.1 (1.0) / -0.1 (1.0) / -0.3 (0.9) / -0.9 (2.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | HVN0_1hs (UNCODED) | 148 (1.2%) | 115>112 (+3%) | 115>112 (+3%) | 89>87 (+2%) | 281>306 (-9%) | 288>276 (+4%) | -599>-570 | -363>-364 | -0.4 (2.1) / +0.1 (1.4) / +1.4 (3.7) / -1.1 (3.5) / +0.3 (1.0) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 10 | KCup4h (coded) | 33 (0.3%) | 115>114 (+1%) | 115>114 (+1%) | 89>89 (+0%) | 281>292 (-4%) | 288>310 (-8%) | -599>-609 | -363>-396 | +0.3 (1.0) / +0.2 (0.7) / +0.5 (1.2) / -0.0 (0.8) / -1.1 (2.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 11 | VAH15s (UNCODED) | -59 (-0.5%) | 115>118 (-2%) | 115>118 (-2%) | 89>90 (-1%) | 281>337 (-20%) | 288>297 (-3%) | -599>-638 | -363>-382 | -0.5 (1.2) / -1.3 (2.4) / -0.6 (1.9) / +0.6 (4.2) / -0.1 (1.5) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 12 | OTE79 (coded) | 118 (1.0%) | 115>117 (-2%) | 115>117 (-2%) | 89>73 (+18%) | 281>338 (-20%) | 288>341 (-18%) | -599>-554 | -363>-384 | +1.4 (4.3) / +1.4 (2.4) / +2.0 (2.5) / +0.9 (5.1) / -2.3 (3.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |

### View windows
| line | L1M cut (n 5 wk) | L2M cut (n 9) | L3M cut (n 13) | mean d L1M / L2M / L3M $k/wk |
|---|---|---|---|---|
| kijun1h | +0% (15>15) | -5% (29>30) | -4% (39>41) | -5.4 / -9.2 / -6.4 |
| OTE62b73 | -3% (15>15) | +25% (40>30) | +21% (51>41) | +13.1 / +8.3 / +5.7 |
| camH3 | -2% (15>15) | +1% (31>30) | +6% (43>41) | -0.1 / -0.4 / -0.3 |
| OTE79 | +0% (15>15) | +19% (38>30) | +18% (49>41) | -0.7 / +11.0 / +7.6 |
| OTE62act | +4% (15>14) | +3% (40>39) | +2% (51>50) | +13.0 / +7.5 / +5.2 |
| KCup4h | +0% (15>15) | +4% (32>30) | +3% (42>41) | +0.0 / +0.2 / +0.1 |
| OTE705 | +0% (15>15) | -1% (30>30) | -7% (38>41) | +0.7 / +0.4 / -0.0 |
| PDmid | +0% (15>15) | +0% (30>30) | +0% (41>41) | +0.0 / +0.0 / -0.1 |
| HVN0_1hs | +0% (15>15) | +1% (30>30) | +2% (41>40) | -1.0 / -1.5 / -0.8 |
| CRT4h | +0% (15>15) | +1% (31>30) | +9% (45>41) | +0.0 / +0.3 / -0.1 |
| VAH15s | +0% (15>15) | +6% (30>28) | -10% (41>45) | +0.2 / +0.2 / -0.3 |
| LVN1_1hs | +0% (15>15) | +2% (30>30) | +3% (41>39) | -2.6 / -1.3 / -1.1 |

### Episode-proofing (named trough week, leave-month-out, bootstrap P, ONE-WEEK flag), V13x
| line | L6M: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | HOLD: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | MID: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | PRE: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | X': cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag |
|---|---|---|---|---|---|
| kijun1h | -1% / +0% (20260907) / -1%..+1% / 0.25 / no cut | -1% / +0% (20260907) / -1%..+5% / 0.40 / no cut | +5% / -11% (20260323) / -33%..+5% / 0.71 / no cut | +32% / +34% (20250428) / +8%..+36% / 0.73 / holds | +6% / +7% (20231120) / -2%..+10% / 0.74 / no cut |
| OTE62b73 | +13% / +5% (20260907) / -0%..+15% / 0.75 / holds | +13% / +5% (20260907) / +5%..+15% / 0.85 / holds | +1% / +25% (20260323) / +1%..+25% / 0.85 / no cut | +18% / +19% (20250428) / +0%..+18% / 0.78 / holds | +13% / +10% (20231218) / -5%..+20% / 0.66 / holds |
| camH3 | -0% / -1% (20260907) / -0%..-0% / 0.17 / no cut | -0% / -1% (20260907) / -2%..-0% / 0.13 / no cut | -2% / +1% (20260323) / -2%..+1% / 0.20 / no cut | +3% / -0% (20250428) / -41%..+4% / 0.23 / no cut | +10% / +11% (20231120) / -4%..+13% / 0.75 / holds |
| OTE79 | +7% / +0% (20260914) / -0%..+8% / 0.58 / no cut | +7% / +0% (20260914) / -5%..+8% / 0.38 / no cut | -5% / -1% (20260323) / -5%..-1% / 0.22 / no cut | +21% / +24% (20250428) / +7%..+23% / 0.88 / holds | -13% / -14% (20231120) / -25%..+2% / 0.23 / no cut |
| OTE62act | -0% / -1% (20260907) / -1%..+2% / 0.29 / no cut | -0% / -1% (20260907) / -1%..+27% / 0.65 / no cut | +31% / +4% (20260323) / +4%..+31% / 1.00 / ONE-WEEK | +4% / +3% (20250428) / -2%..+6% / 0.59 / no cut | +5% / +5% (20231218) / +2%..+6% / 0.83 / no cut |
| KCup4h | +1% / +0% (20260907) / -0%..+1% / 0.29 / no cut | +1% / +0% (20260907) / -0%..+1% / 0.22 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.00 / no cut | +12% / +12% (20250428) / +0%..+12% / 0.65 / holds | -7% / -7% (20231120) / -11%..+1% / 0.33 / no cut |
| OTE705 | -3% / -3% (20260907) / -7%..+0% / 0.26 / no cut | -3% / -3% (20260907) / -7%..+12% / 0.57 / no cut | +12% / +11% (20260323) / +0%..+12% / 0.92 / holds | +11% / +12% (20250428) / +3%..+13% / 0.81 / holds | -5% / -5% (20231120) / -8%..+0% / 0.23 / no cut |
| PDmid | -1% / -2% (20260907) / -1%..-0% / 0.00 / no cut | -1% / -2% (20260907) / -1%..-0% / 0.00 / no cut | -1% / +0% (20260323) / -1%..-0% / 0.00 / no cut | +1% / +1% (20250428) / -1%..+6% / 0.58 / no cut | -2% / +2% (20231120) / -11%..+4% / 0.48 / no cut |
| HVN0_1hs | +3% / +3% (20260907) / -0%..+4% / 0.80 / no cut | +3% / +3% (20260907) / -14%..+4% / 0.44 / no cut | -9% / -25% (20260323) / -25%..-9% / 0.03 / no cut | -14% / -17% (20250428) / -17%..+4% / 0.38 / no cut | +4% / +4% (20231120) / +0%..+6% / 0.70 / no cut |
| CRT4h | -4% / -5% (20260907) / -8%..+0% / 0.17 / no cut | -4% / -5% (20260907) / -8%..+1% / 0.31 / no cut | +1% / +1% (20260323) / +1%..+1% / 0.67 / no cut | -2% / -4% (20250428) / -11%..-2% / 0.24 / no cut | -3% / -1% (20231120) / -14%..+12% / 0.52 / no cut |
| VAH15s | -2% / +2% (20260907) / -2%..+2% / 0.67 / no cut | -2% / +2% (20260907) / -2%..+2% / 0.67 / no cut | +1% / +23% (20260323) / +1%..+50% / 0.75 / no cut | -18% / -19% (20250428) / -20%..-9% / 0.17 / no cut | -6% / -6% (20231120) / -8%..-2% / 0.00 / no cut |
| LVN1_1hs | -0% / -1% (20260907) / -0%..+5% / 0.69 / no cut | -0% / -1% (20260907) / -2%..+4% / 0.58 / no cut | -2% / +0% (20260323) / -2%..-0% / 0.33 / no cut | -1% / -0% (20250428) / -2%..+4% / 0.60 / no cut | -23% / -24% (20231120) / -30%..-2% / 0.03 / no cut |

### Same, V13h (U7 on)
| line | L6M: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | HOLD: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | MID: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | PRE: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | X': cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag |
|---|---|---|---|---|---|
| kijun1h | -1% / -1% (20260914) / -1%..+2% / 0.27 / no cut | -1% / -1% (20260914) / -1%..+2% / 0.44 / no cut | +7% / +6% (20260323) / +6%..+7% / 0.88 / no cut | +41% / +43% (20250428) / +15%..+45% / 0.75 / holds | +7% / +7% (20231120) / -2%..+11% / 0.73 / no cut |
| OTE62b73 | -2% / -0% (20260907) / -4%..-0% / 0.24 / no cut | -2% / -0% (20260907) / -4%..+0% / 0.51 / no cut | +1% / +0% (20260323) / +0%..+1% / 0.96 / no cut | +19% / +17% (20250428) / -13%..+19% / 0.75 / holds | +15% / +12% (20231218) / -5%..+20% / 0.67 / holds |
| OTE705 | +17% / +24% (20260907) / -32%..+23% / 0.63 / holds | +17% / +24% (20260907) / +1%..+23% / 0.76 / holds | +4% / -0% (20260323) / -0%..+4% / 0.63 / no cut | +3% / +3% (20250428) / -17%..+3% / 0.56 / no cut | +9% / +9% (20231120) / -5%..+13% / 0.67 / no cut |
| CRT4h | -6% / -7% (20260914) / -10%..+5% / 0.15 / no cut | -6% / -7% (20260914) / -10%..-0% / 0.28 / no cut | +3% / -1% (20260323) / -1%..+3% / 0.78 / no cut | +8% / +6% (20250428) / -27%..+11% / 0.42 / no cut | +12% / +13% (20231120) / +5%..+14% / 0.97 / holds |
| OTE79 | +0% / +0% (20260914) / +0%..+2% / 0.60 / no cut | +0% / +0% (20260914) / -7%..+0% / 0.37 / no cut | +0% / -1% (20260323) / -1%..-0% / 0.17 / no cut | +20% / +22% (20250428) / +8%..+20% / 0.83 / holds | -5% / -5% (20231120) / -15%..+2% / 0.36 / no cut |
| OTE62act | +11% / +10% (20260907) / -1%..+13% / 0.72 / holds | +11% / +10% (20260907) / +1%..+13% / 0.74 / holds | +1% / -27% (20260323) / -27%..+1% / 0.62 / no cut | +6% / +5% (20250428) / -0%..+9% / 0.63 / no cut | +3% / +4% (20231218) / +1%..+5% / 0.81 / no cut |
| PDmid | -2% / -2% (20260914) / -2%..-0% / 0.00 / no cut | -2% / -2% (20260914) / -2%..-0% / 0.10 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.08 / no cut | +6% / +6% (20250428) / +1%..+9% / 0.73 / no cut | +7% / +10% (20231120) / +2%..+9% / 0.87 / no cut |
| camH3 | -4% / -4% (20260914) / -4%..-0% / 0.03 / no cut | -4% / -4% (20260914) / -4%..-0% / 0.01 / no cut | +0% / -0% (20260323) / -0%..-0% / 0.00 / no cut | -3% / +1% (20250428) / -52%..-2% / 0.12 / no cut | +11% / +11% (20231218) / -4%..+15% / 0.78 / holds |
| KCup4h | +1% / +2% (20260914) / -0%..+2% / 0.35 / no cut | +1% / +2% (20260914) / -0%..+2% / 0.26 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.00 / no cut | +8% / +11% (20250428) / -17%..+8% / 0.51 / no cut | -7% / -8% (20231120) / -11%..+1% / 0.30 / no cut |
| HVN0_1hs | +4% / +4% (20260914) / -1%..+5% / 0.49 / no cut | +4% / +4% (20260914) / -1%..+5% / 0.32 / no cut | -10% / -25% (20260323) / -25%..-10% / 0.00 / no cut | -13% / -16% (20250428) / -13%..+4% / 0.41 / no cut | +3% / +4% (20231120) / -0%..+5% / 0.67 / no cut |
| LVN1_1hs | -0% / -0% (20260914) / -0%..+11% / 0.67 / no cut | -0% / -0% (20260914) / -0%..+11% / 0.63 / no cut | -2% / +0% (20260323) / -2%..-0% / 0.00 / no cut | -5% / -2% (20250428) / -5%..+5% / 0.46 / no cut | -28% / -27% (20231120) / -36%..-4% / 0.04 / no cut |
| VAH15s | -3% / -4% (20260914) / -6%..+0% / 0.52 / no cut | -3% / -4% (20260914) / -4%..+0% / 0.48 / no cut | -1% / +25% (20260323) / -1%..+25% / 0.43 / no cut | -45% / -45% (20250428) / -45%..-13% / 0.07 / no cut | -4% / -4% (20231120) / -6%..-1% / 0.03 / no cut |

### Line table V13h (U7 on, cube-level)
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | kijun1h (coded) | -78 (-0.7%) | 93>94 (-1%) | 93>94 (-1%) | 47>43 (+7%) | 297>175 (+41%) | 253>235 (+7%) | -439>-456 | -384>-369 | -2.7 (7.7) / -0.6 (4.7) / +3.4 (10.3) / +1.5 (3.8) / +0.4 (1.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 2 | OTE62b73 (action) | 77 (0.7%) | 93>94 (-2%) | 93>94 (-2%) | 43>43 (+1%) | 215>175 (+19%) | 275>235 (+15%) | -474>-456 | -366>-369 | -1.2 (12.9) / +0.3 (6.8) / +0.0 (1.3) / +0.1 (2.3) / +1.0 (3.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | n/n/n | n/n | n | n |
| 3 | OTE705 (coded) | 396 (3.5%) | 113>94 (+17%) | 113>94 (+17%) | 45>43 (+4%) | 180>175 (+3%) | 257>235 (+9%) | -469>-456 | -365>-369 | -8.5 (17.6) / -4.3 (9.2) / +0.5 (1.6) / -0.8 (2.4) / +0.7 (2.4) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 4 | CRT4h (coded) | 311 (2.8%) | 89>94 (-6%) | 89>94 (-6%) | 44>43 (+3%) | 190>175 (+8%) | 268>235 (+12%) | -469>-456 | -377>-369 | -0.5 (1.3) / -0.2 (0.9) / +0.1 (2.2) / -0.1 (1.5) / +0.9 (1.3) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 5 | OTE79 (coded) | -29 (-0.3%) | 95>94 (+0%) | 95>94 (+0%) | 43>43 (+0%) | 218>175 (+20%) | 224>235 (-5%) | -463>-456 | -355>-369 | -0.2 (0.6) / +0.2 (0.7) / +1.3 (2.0) / +0.6 (1.2) / -0.1 (1.3) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 6 | OTE62act (coded) | -42 (-0.4%) | 93>83 (+11%) | 93>83 (+11%) | 43>43 (+1%) | 215>201 (+6%) | 275>266 (+3%) | -474>-469 | -366>-362 | +2.6 (7.4) / +1.4 (3.9) / +0.1 (2.5) / +0.1 (0.8) / +0.2 (0.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/Y/Y | Y/Y | n | Y |
| 7 | PDmid (coded) | 40 (0.4%) | 93>94 (-2%) | 93>94 (-2%) | 43>43 (+0%) | 186>175 (+6%) | 253>235 (+7%) | -459>-456 | -386>-369 | -0.6 (1.0) / -0.5 (0.7) / -0.2 (0.8) / +0.2 (0.4) / +0.5 (1.2) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 8 | camH3 (coded) | -12 (-0.1%) | 91>94 (-4%) | 91>94 (-4%) | 43>43 (+0%) | 171>175 (-3%) | 263>235 (+11%) | -449>-456 | -377>-369 | -0.3 (0.7) / -0.6 (0.7) / -1.2 (1.8) / -2.5 (3.5) / +0.8 (2.5) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | KCup4h (coded) | -2 (-0.0%) | 95>94 (+1%) | 95>94 (+1%) | 43>43 (+0%) | 191>175 (+8%) | 218>235 (-7%) | -461>-456 | -356>-369 | +0.0 (0.2) / -0.0 (0.4) / +0.0 (1.1) / -0.3 (2.1) / -0.3 (1.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 10 | HVN0_1hs (UNCODED) | -21 (-0.2%) | 94>91 (+4%) | 94>91 (+4%) | 43>47 (-10%) | 175>198 (-13%) | 235>227 (+3%) | -456>-450 | -369>-359 | -0.8 (2.3) / -0.4 (1.5) / -1.2 (2.2) / -0.3 (1.2) / +0.0 (0.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 11 | LVN1_1hs (UNCODED) | -17 (-0.2%) | 94>94 (-0%) | 94>94 (-0%) | 43>44 (-2%) | 175>184 (-5%) | 235>301 (-28%) | -456>-459 | -369>-373 | +0.4 (2.2) / +0.4 (1.2) / -0.1 (0.7) / -0.0 (0.5) / -1.6 (3.6) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 12 | VAH15s (UNCODED) | -56 (-0.5%) | 94>97 (-3%) | 94>97 (-3%) | 43>43 (-1%) | 175>254 (-45%) | 235>245 (-4%) | -456>-478 | -369>-379 | -0.3 (0.7) / -0.5 (1.0) / +0.1 (2.5) / -1.3 (1.6) / -0.5 (0.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |

## 3. Rankings (V13x)
### Honest (selected on PRE+X', recent windows looked at once)
| honest # | line | S_PX = mean(cut PRE, cut X') | cut PRE | cut X' | PX gate | ONE recent look: cut L6M | HOLD | MID | L3M (view L1M) | mean d L6M (MDE) / HOLD / MID | label | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | kijun1h | +0.191 | +32% | +6% | pass | -1% | -1% | +5% | -4% (+0%) | -3.3 (9.3) / -1.9 / -0.8 | no | n/n/n |
| - | OTE62b73 | +0.155 | +18% | +13% | fail: X' w20 worse | +13% | +13% | +1% | +21% (-3%) | +3.6 (8.5) / +3.1 / +0.9 | n/a (action line, no placebo) | Y/Y/Y |
| - | camH3 | +0.067 | +3% | +10% | fail: PRE mean<-0.5MDE | -0% | -0% | -2% | +6% (-2%) | -0.2 (0.7) / -0.5 / -1.1 | no | n/n/n |
| - | OTE62act | +0.045 | +4% | +5% | fail: PRE w20 worse | -0% | -0% | +31% | +2% (+4%) | +2.5 (8.3) / +3.1 / +7.7 | no | Y/n/Y |
| - | OTE79 | +0.042 | +21% | -13% | fail: X' no cut, X' w20 worse | +7% | +7% | -5% | +18% (+0%) | +5.1 (11.3) / +2.9 / +0.3 | no | n/Y/Y |
| - | OTE705 | +0.030 | +11% | -5% | fail: X' no cut, X' w20 worse | -3% | -3% | +12% | -7% (+0%) | -0.6 (1.4) / -0.1 / +0.9 | no | n/n/n |
| - | KCup4h | +0.026 | +12% | -7% | fail: X' no cut, X' w20 worse | +1% | +1% | +0% | +3% (+0%) | +0.0 (0.2) / -0.1 / -0.0 | no | n/n/Y |
| - | PDmid | -0.005 | +1% | -2% | fail: X' no cut | -1% | -1% | -1% | +0% (+0%) | -0.7 (1.3) / -0.8 / -0.3 | no | n/n/n |
| - | CRT4h | -0.023 | -2% | -3% | fail: PRE no cut, X' no cut, PRE w20 worse | -4% | -4% | +1% | +9% (+0%) | -0.3 (1.4) / -0.2 / -0.4 | no | n/n/n |
| - | HVN0_1hs | -0.050 | -14% | +4% | fail: PRE no cut | +3% | +3% | -9% | +2% (+0%) | -0.5 (1.9) / -0.1 / -1.1 | no | n/n/n |
| - | VAH15s | -0.118 | -18% | -6% | fail: PRE no cut, X' no cut, PRE w20 worse, X' w20 worse, PRE mean<-0.5MDE, X' mean<-0.5MDE | -2% | -2% | +1% | -10% (+0%) | -0.5 (0.9) / -0.3 / +1.1 | no | n/n/n |
| - | LVN1_1hs | -0.122 | -1% | -23% | fail: PRE no cut, X' no cut, X' w20 worse | -0% | -0% | -2% | +3% (+0%) | -0.2 (1.5) / +0.0 / +0.0 | no | n/n/n |
### Post-hoc (L6M cut)
| post-hoc # | line | cut L6M | Calmar L6M before>after | cut HOLD | cut MID | cut L3M | PRE: cut, mean d (MDE) | X': cut, mean d (MDE) | S/T/N | TOL-B/nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE62b73 | +12.7% | 0.19 > 0.25 | +12.7% | +1.0% | +20.8% | +18.4%, +0.2 (2.4) | +12.7%, +1.1 (4.1) | Y/Y/Y | Y/Y | n/a (action line, no placebo) |
| 2 | OTE79 | +6.5% | 0.19 > 0.25 | +6.5% | -4.7% | +17.7% | +21.4%, +0.8 (1.2) | -13.1%, -0.6 (1.7) | n/Y/Y | Y/Y | no |
| 3 | HVN0_1hs | +3.4% | 0.25 > 0.26 | +3.4% | -8.7% | +2.0% | -13.9%, -0.4 (1.3) | +3.9%, +0.1 (0.7) | n/n/n | n/n | no |
| 4 | KCup4h | +1.3% | 0.25 > 0.25 | +1.3% | +0.0% | +3.3% | +12.1%, -0.3 (2.2) | -6.8%, -0.3 (1.1) | n/n/Y | Y/n | no |
| 5 | OTE62act | -0.1% | 0.19 > 0.21 | -0.1% | +31.5% | +2.5% | +4.5%, +0.0 (0.7) | +4.6%, +0.3 (0.7) | Y/n/Y | Y/Y | no |
| 6 | camH3 | -0.2% | 0.26 > 0.25 | -0.2% | -1.8% | +5.6% | +3.1%, -1.8 (3.2) | +10.3%, +0.7 (2.5) | n/n/n | n/n | no |
| 7 | LVN1_1hs | -0.4% | 0.25 > 0.25 | -0.4% | -2.4% | +3.4% | -1.4%, -0.0 (0.8) | -23.0%, -1.5 (4.0) | n/n/n | n/n | no |
| 8 | kijun1h | -1.0% | 0.29 > 0.25 | -1.0% | +4.6% | -3.7% | +31.9%, +1.2 (3.0) | +6.2%, +0.4 (1.6) | n/n/n | n/n | no |
| 9 | PDmid | -1.5% | 0.26 > 0.25 | -1.5% | -0.6% | +0.0% | +0.6%, +0.1 (0.4) | -1.6%, -0.0 (1.3) | n/n/n | n/n | no |
| 10 | VAH15s | -2.5% | 0.25 > 0.24 | -2.5% | +1.4% | -10.1% | -17.7%, -0.8 (1.0) | -5.9%, -0.6 (0.7) | n/n/n | n/n | no |
| 11 | OTE705 | -3.1% | 0.27 > 0.25 | -3.1% | +12.2% | -6.8% | +10.9%, +0.3 (0.8) | -5.0%, -0.1 (0.8) | n/n/n | n/n | no |
| 12 | CRT4h | -4.2% | 0.27 > 0.25 | -4.2% | +1.0% | +9.4% | -2.0%, -0.3 (1.2) | -2.6%, -0.1 (2.7) | n/n/n | n/n | no |

### Best-of-N chance null (V13x, N=? lines, S_PX)
not enough draws yet

## 4. Lines that add nothing
| line | rows newly acted on (all 187 wk) | pre-declared null rule | cuts (dDD% L6M / PRE / X') | mean d / MDE (L6M, PRE, X') | weakness |
|---|---|---|---|---|---|
| LVN1_1hs | 1008 | not null | -0.4% / -1.4% / -23.0% | -0.10 / -0.03 / -0.39 | cuts in 0 of 4 (L6M, HOLD, PRE, X') |
| VAH15s | 1321 | not null | -2.5% / -17.7% / -5.9% | -0.53 / -0.74 / -0.83 | cuts in 0 of 4 (L6M, HOLD, PRE, X') |
| CRT4h | 1076 | not null | -4.2% / -2.0% / -2.6% | -0.22 / -0.25 / -0.03 | cuts in 0 of 4 (L6M, HOLD, PRE, X') |
| HVN0_1hs | 1207 | not null | +3.4% / -13.9% / +3.9% | -0.24 / -0.33 / +0.11 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| PDmid | 414 | not null | -1.5% / +0.6% / -1.6% | -0.53 / +0.26 / -0.02 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| OTE705 | 1458 | not null | -3.1% / +10.9% / -5.0% | -0.45 / +0.33 / -0.16 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| KCup4h | 970 | not null | +1.3% / +12.1% / -6.8% | +0.14 / -0.13 / -0.24 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| OTE62act | 1414 | not null | -0.1% / +4.5% / +4.6% | +0.30 / +0.04 / +0.43 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| OTE79 | 1664 | not null | +6.5% / +21.4% / -13.1% | +0.45 / +0.67 / -0.34 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| camH3 | 1632 | not null | -0.2% / +3.1% / +10.3% | -0.33 / -0.57 / +0.30 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| OTE62b73 | 0 | not null | +12.7% / +18.4% / +12.7% | +0.43 / +0.08 / +0.26 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| kijun1h | 1443 | not null | -1.0% / +31.9% / +6.2% | -0.35 / +0.39 / +0.24 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |

## 5. Definition sensitivity (V13x)
### Whole layer
| whole layer (7 lines) at D | L6M maxDD cut | HOLD maxDD cut | MID maxDD cut | PRE maxDD cut | X' maxDD cut |
|---|---|---|---|---|---|
| D = 10 | +8% | +8% | +5% | +34% | -0% |
| D = 15 | +7% | +7% | +12% | +14% | +21% |
| D = 20 | +7% | +7% | +25% | +31% | +12% |
| D = 25 | +8% | +8% | +54% | +23% | +37% |
| D = 30 | +1% | +1% | +58% | +22% | +18% |
| D = 40 | +1% | +1% | +56% | +18% | +12% |
| freshness any (fresh or touched), D20 | -24% | -24% | +20% | +36% | +42% |
### Per line (others at D20)
| line | window | marginal-in-set maxDD cut at D = 10 / 15 / 20 / 25 / 30 / 40 (D20 = shipped; D+-25% = 15/25, +-50% = 10/30) | verdict |
|---|---|---|---|
| kijun1h | L6M | +1% / +0% / -1% / +0% / +1% / -6% | no cut at any D |
| kijun1h | PRE | +34% / +32% / +32% / +33% / +23% / +31% | holds at 6 of 6 D (cut >= 10%) |
| kijun1h | X' | +7% / +5% / +6% / +11% / +11% / -8% | holds at 2 of 6 D (cut >= 10%) |
| PDmid | L6M | -3% / -1% / -1% / -1% / -5% / -1% | no cut at any D |
| PDmid | PRE | +0% / +0% / +1% / -0% / +4% / -9% | no cut at any D |
| PDmid | X' | +0% / +0% / -2% / +3% / +5% / +9% | no cut at any D |
| CRT4h | L6M | -0% / -2% / -4% / -4% / -7% / -6% | no cut at any D |
| CRT4h | PRE | +2% / -3% / -2% / -3% / -8% / -5% | no cut at any D |
| CRT4h | X' | +6% / +11% / -3% / -2% / -2% / -3% | FRAGILE (cut >= 10% at one D only) |
| KCup4h | L6M | +1% / +1% / +1% / -0% / -2% / -2% | no cut at any D |
| KCup4h | PRE | +12% / +13% / +12% / +13% / +11% / -1% | holds at 5 of 6 D (cut >= 10%) |
| KCup4h | X' | +0% / -1% / -7% / -7% / -6% / -6% | no cut at any D |
| camH3 | L6M | +1% / +1% / -0% / +3% / +4% / +6% | no cut at any D |
| camH3 | PRE | +2% / -0% / +3% / -11% / -10% / -10% | no cut at any D |
| camH3 | X' | +0% / +2% / +10% / +14% / -1% / -8% | holds at 2 of 6 D (cut >= 10%) |
| OTE705 | L6M | -1% / -1% / -3% / -6% / -8% / -4% | no cut at any D |
| OTE705 | PRE | +2% / +5% / +11% / +5% / +9% / -4% | FRAGILE (cut >= 10% at one D only) |
| OTE705 | X' | -6% / -4% / -5% / -5% / -5% / -25% | no cut at any D |
| OTE79 | L6M | -1% / +0% / +7% / +7% / +7% / +6% | no cut at any D |
| OTE79 | PRE | +4% / +21% / +21% / +21% / +22% / +24% | holds at 5 of 6 D (cut >= 10%) |
| OTE79 | X' | -5% / -5% / -13% / +12% / +14% / -8% | holds at 2 of 6 D (cut >= 10%) |
| VAH15s | L6M | -1% / -3% / -2% / -4% / -4% / -6% | no cut at any D |
| VAH15s | PRE | -10% / -15% / -18% / -9% / -8% / -13% | no cut at any D |
| VAH15s | X' | -0% / -2% / -6% / -7% / -8% / -10% | no cut at any D |
| LVN1_1hs | L6M | +1% / -1% / -0% / -1% / +2% / -3% | no cut at any D |
| LVN1_1hs | PRE | +5% / +5% / -1% / +2% / -1% / -4% | no cut at any D |
| LVN1_1hs | X' | -0% / -22% / -23% / -23% / -19% / -19% | no cut at any D |
| HVN0_1hs | L6M | +3% / +3% / +3% / +2% / -0% / -7% | no cut at any D |
| HVN0_1hs | PRE | -7% / -6% / -14% / -1% / -1% / +7% | no cut at any D |
| HVN0_1hs | X' | +2% / +2% / +4% / +4% / +7% / -12% | no cut at any D |
Not done: swing strength 2/3 and profile bin 1/2 pt (need the POI streams rebuilt), anchor shifts, 1-s/3-s entry delay (the engine has no entry-delay parameter for B73/half).

## 6. Subset landscape (V13x, 2^10 subsets, OTE-62 B73 kept)
Subsets scored: 645 (all 2^10 subsets of the 7 lines + 3 uncoded lines, OTE-62 B73 kept, HALF frame). Baseline = zone piece off.

| set | lines | kept trades removed | maxDD cut L6M / HOLD / MID / PRE / X' | mean $k/wk L6M / HOLD / MID | Calmar ALL |
|---|---|---|---|---|---|
| SHIPPED | kijun1h+PDmid+CRT4h+KCup4h+camH3+OTE705+OTE79 | 4.8% | +7% / +7% / +25% / +31% / +12% | 27.3 / 24.8 / 10.2 | 0.03 |
| best by S_PX (PRE,X' only) #1 | kijun1h+PDmid+CRT4h+camH3+HVN0_1hs | 3.1% | +14% / +14% / +7% / +25% / +41% | 26.3 / 23.7 / 7.5 | 0.04 |
| S_PX #2 | kijun1h+PDmid+CRT4h+KCup4h+camH3+HVN0_1hs | 2.7% | +15% / +15% / +7% / +28% / +37% | 26.3 / 23.9 / 7.5 | 0.04 |
| S_PX #3 | kijun1h+PDmid+CRT4h+KCup4h+HVN0_1hs | 2.5% | +18% / +18% / +8% / +28% / +37% | 26.5 / 24.4 / 8.6 | 0.04 |
| post-hoc L6M cut #1 | kijun1h+PDmid+CRT4h+KCup4h+HVN0_1hs | 2.5% | +18% / +18% / +8% / +28% / +37% | 26.5 / 24.4 / 8.6 | 0.04 |
| post-hoc L6M cut #2 | PDmid+CRT4h+KCup4h+LVN1_1hs+HVN0_1hs | 4.1% | +17% / +17% / +9% / +13% / +4% | 29.9 / 26.2 / 9.0 | 0.03 |
| post-hoc L6M cut #3 | kijun1h+PDmid+KCup4h+LVN1_1hs+HVN0_1hs | 0.9% | +17% / +17% / +3% / +24% / -0% | 26.4 / 24.3 / 8.7 | 0.03 |
| half-volume set keeping >= 80% of the shipped PRE and HOLD cut #1 | kijun1h+PDmid+KCup4h+camH3+HVN0_1hs | -0.2% | +17% / +17% / +7% / +26% / +29% | 26.5 / 23.9 / 7.4 | 0.04 |
| half-volume set keeping >= 80% of the shipped PRE and HOLD cut #2 | kijun1h+KCup4h+OTE705+OTE79+HVN0_1hs | 0.6% | +13% / +13% / +19% / +30% / +17% | 28.0 / 26.1 / 10.3 | 0.04 |
| half-volume set keeping >= 80% of the shipped PRE and HOLD cut #3 | kijun1h+PDmid+KCup4h+OTE79+HVN0_1hs | 1.2% | +17% / +17% / +12% / +28% / -6% | 28.1 / 25.5 / 9.7 | 0.03 |

Rank of the shipped set among all 645 subsets by maxDD cut (1 = best): L6M 400, HOLD 400, MID 42, PRE 10, X' 148, S_PX 36.
Best-of-subsets caution: with 645 subsets the best S_PX in-sample is a selection effect; the line-level chance null below is the honest reference.

## 7. Per book and per session, marginal-in-set (V13x; dDD $k / dWorst20 (PRE, X') / d mean)

### by book, L6M
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| kijun1h | +0 / -0.7 | +0 / -0.8 | +0 / -0.5 | +1 / -1.1 | +1 / -0.3 | +0 / +0.0 |
| OTE62b73 | +2 / +0.9 | -7 / +1.1 | +0 / -0.5 | -16 / +1.5 | -8 / +0.4 | +0 / +0.1 |
| camH3 | -0 / -0.0 | +0 / +0.3 | +0 / -0.2 | +3 / -0.1 | +1 / -0.0 | +1 / -0.1 |
| OTE79 | +0 / +0.5 | +0 / +3.4 | -17 / +0.9 | -15 / -0.0 | +1 / +0.2 | +1 / +0.1 |
| OTE62act | -1 / +0.6 | +2 / +0.7 | +0 / -0.4 | -7 / +1.2 | -4 / +0.3 | -3 / +0.1 |
| KCup4h | +0 / -0.0 | +0 / +0.1 | +0 / +0.0 | +0 / +0.0 | +0 / +0.0 | +0 / -0.0 |
| OTE705 | -1 / -0.2 | +0 / -0.5 | +0 / +0.0 | +2 / +0.1 | +0 / +0.0 | +0 / -0.0 |
| PDmid | -1 / -0.1 | +0 / -0.4 | +1 / -0.1 | +0 / -0.1 | +0 / +0.0 | -0 / +0.1 |
| HVN0_1hs | -1 / +0.1 | +0 / -0.5 | -2 / +0.2 | -2 / -0.1 | +3 / -0.1 | -3 / -0.1 |
| CRT4h | +0 / -0.1 | +0 / +0.0 | +1 / -0.4 | -1 / +0.1 | +0 / +0.0 | +0 / +0.0 |
| VAH15s | +1 / -0.1 | -1 / -0.1 | +0 / +0.1 | +3 / -0.1 | +5 / -0.2 | +5 / -0.1 |
| LVN1_1hs | -1 / +0.1 | +0 / -0.4 | -2 / +0.2 | +0 / +0.0 | +2 / -0.0 | +0 / +0.0 |

### by session, L6M
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| kijun1h | -2 / -1.8 | -1 / -1.5 | -1 / -0.1 | +0 / +0.1 |
| OTE62b73 | -10 / +3.1 | -9 / +0.3 | +0 / +0.2 | +3 / +0.0 |
| camH3 | -0 / -0.3 | +0 / -0.0 | -1 / -0.1 | -5 / +0.2 |
| OTE79 | -30 / +1.2 | -3 / +3.6 | -2 / +0.2 | +0 / +0.0 |
| OTE62act | -1 / +2.3 | +4 / +0.2 | +1 / +0.0 | -1 / +0.0 |
| KCup4h | +0 / -0.0 | +0 / +0.1 | +0 / +0.0 | +0 / +0.0 |
| OTE705 | +3 / -0.8 | -1 / -0.1 | +0 / -0.1 | -8 / +0.4 |
| PDmid | +2 / -0.7 | +0 / +0.0 | -1 / +0.1 | +2 / -0.1 |
| HVN0_1hs | -1 / -0.4 | -2 / +0.0 | +0 / +0.0 | +3 / -0.1 |
| CRT4h | +8 / -0.2 | -2 / -0.3 | -1 / +0.2 | +0 / +0.0 |
| VAH15s | -2 / -0.1 | +0 / -0.3 | -1 / -0.1 | -0 / +0.0 |
| LVN1_1hs | -0 / -0.1 | +5 / +0.0 | +0 / -0.0 | -1 / +0.0 |

### by book, HOLD
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| kijun1h | +0 / -0.2 | +1 / -1.1 | +0 / -0.1 | +1 / -0.3 | +3 / -0.2 | +3 / -0.0 |
| OTE62b73 | -1 / +0.6 | -0 / +1.1 | -0 / +0.0 | -16 / +1.0 | -12 / +0.3 | +0 / +0.1 |
| camH3 | +0 / -0.1 | -0 / -0.1 | +0 / -0.1 | +3 / -0.1 | +1 / -0.0 | +0 / -0.1 |
| OTE79 | +0 / +0.2 | +1 / +1.9 | -14 / +0.5 | -15 / -0.0 | +0 / +0.3 | +0 / +0.1 |
| OTE62act | +9 / +0.2 | +2 / +1.3 | -1 / -0.1 | -7 / +1.1 | -18 / +0.6 | +1 / +0.0 |
| KCup4h | +0 / -0.0 | +0 / +0.1 | +0 / -0.1 | +0 / -0.1 | +0 / +0.0 | +0 / +0.0 |
| OTE705 | -5 / +0.0 | -0 / -0.2 | +0 / -0.0 | +2 / +0.1 | -1 / +0.0 | +1 / -0.0 |
| PDmid | +0 / -0.3 | +1 / -0.1 | +0 / -0.2 | +0 / -0.0 | +3 / -0.1 | +1 / -0.1 |
| HVN0_1hs | +0 / +0.3 | +0 / -0.4 | +0 / +0.2 | -2 / -0.1 | +4 / -0.1 | +0 / -0.0 |
| CRT4h | -1 / -0.0 | +0 / -0.2 | -4 / -0.1 | -1 / +0.0 | -2 / +0.0 | +0 / -0.1 |
| VAH15s | -0 / -0.0 | -0 / -0.2 | +0 / +0.2 | +3 / -0.2 | +2 / -0.1 | +2 / -0.1 |
| LVN1_1hs | +1 / +0.0 | +2 / -0.2 | -1 / +0.2 | +0 / +0.1 | +1 / -0.0 | +0 / +0.0 |

### by session, HOLD
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| kijun1h | -19 / +0.2 | +11 / -1.7 | +25 / -0.6 | -5 / +0.2 |
| OTE62b73 | -10 / +2.3 | +1 / +0.6 | -7 / +0.2 | +2 / +0.0 |
| camH3 | -0 / -0.2 | +4 / -0.3 | +0 / -0.1 | -2 / +0.0 |
| OTE79 | -30 / +0.6 | -2 / +1.8 | -4 / +0.4 | +0 / +0.0 |
| OTE62act | -1 / +1.6 | -6 / +1.3 | +1 / +0.2 | +1 / -0.0 |
| KCup4h | +0 / -0.2 | -4 / +0.1 | -0 / +0.0 | +0 / -0.0 |
| OTE705 | +3 / -0.2 | -0 / -0.1 | -3 / -0.0 | -8 / +0.2 |
| PDmid | +2 / -0.4 | +0 / -0.2 | -3 / -0.0 | +6 / -0.2 |
| HVN0_1hs | -1 / +0.0 | +7 / -0.1 | +2 / -0.0 | +5 / -0.1 |
| CRT4h | +8 / -0.3 | +4 / -0.2 | -3 / +0.2 | +0 / +0.0 |
| VAH15s | -2 / -0.1 | +0 / +0.0 | +6 / -0.2 | -0 / +0.0 |
| LVN1_1hs | -0 / +0.1 | +3 / -0.0 | +1 / -0.0 | -0 / +0.0 |

### by book, MID
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| kijun1h | +0 / +0.7 | +12 / -3.1 | +0 / +0.8 | -5 / +1.1 | +0 / -0.1 | +0 / -0.2 |
| OTE62b73 | -1 / +0.1 | +1 / +0.4 | -0 / +0.4 | -1 / +0.1 | +1 / -0.0 | +0 / +0.0 |
| camH3 | +0 / +0.0 | +4 / -0.7 | +0 / -0.0 | +1 / -0.2 | +0 / -0.1 | +0 / -0.1 |
| OTE79 | +0 / -0.0 | +0 / +0.3 | +0 / -0.1 | -0 / +0.1 | +0 / +0.0 | +0 / +0.0 |
| OTE62act | +9 / -0.7 | -0 / +4.4 | -1 / +0.6 | -1 / +1.7 | -2 / +1.8 | +1 / -0.1 |
| KCup4h | +0 / -0.1 | +0 / +0.4 | +0 / -0.5 | +0 / +0.0 | +0 / +0.0 | +0 / +0.1 |
| OTE705 | -5 / +0.5 | +0 / +0.0 | +0 / +0.0 | +0 / +0.4 | +0 / +0.0 | +0 / +0.0 |
| PDmid | +0 / +0.0 | +0 / +0.0 | +0 / +0.0 | +0 / -0.0 | +0 / +0.0 | +0 / -0.3 |
| HVN0_1hs | +0 / -0.0 | +0 / -0.8 | +0 / -0.1 | -1 / -0.2 | +0 / -0.1 | +0 / +0.1 |
| CRT4h | -1 / +0.0 | +0 / -0.7 | -4 / +0.6 | +3 / -0.1 | -1 / +0.2 | +0 / -0.4 |
| VAH15s | -0 / +0.4 | -2 / +0.3 | +0 / +0.6 | +1 / -0.4 | +0 / +0.3 | +1 / -0.1 |
| LVN1_1hs | +1 / -0.1 | +0 / -0.1 | -1 / +0.1 | +0 / +0.2 | -0 / +0.0 | +0 / +0.0 |

### by session, MID
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| kijun1h | -27 / +5.0 | +11 / -4.0 | +25 / -2.2 | +3 / +0.4 |
| OTE62b73 | -1 / -0.0 | +1 / +0.2 | -8 / +0.7 | +0 / -0.1 |
| camH3 | +1 / -0.0 | +4 / -0.8 | +0 / -0.3 | +0 / +0.0 |
| OTE79 | +5 / +0.0 | -2 / +0.3 | +0 / -0.0 | +0 / +0.0 |
| OTE62act | -22 / +1.6 | -6 / +5.4 | +1 / +0.8 | +2 / -0.1 |
| KCup4h | +0 / -0.3 | -4 / +0.3 | +0 / +0.0 | +0 / -0.0 |
| OTE705 | -7 / +0.7 | -0 / +0.1 | +0 / +0.1 | -0 / +0.0 |
| PDmid | +0 / -0.3 | +0 / +0.0 | +0 / +0.0 | +0 / +0.0 |
| HVN0_1hs | +6 / -0.2 | +7 / -0.4 | +6 / -0.5 | +0 / -0.0 |
| CRT4h | -6 / -0.3 | +4 / -0.2 | +0 / +0.1 | +0 / +0.0 |
| VAH15s | -1 / -0.1 | +0 / +1.2 | +2 / -0.1 | +0 / +0.0 |
| LVN1_1hs | -3 / +0.4 | +3 / -0.4 | +0 / +0.0 | +0 / +0.0 |

### by book, PRE
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| kijun1h | -20 / -5 / +0.1 | -35 / +5 / +0.6 | -11 / +4 / +0.1 | -8 / -1 / +0.1 | -2 / -6 / +0.1 | +0 / +3 / +0.1 |
| OTE62b73 | +0 / -0 / -0.1 | -21 / +7 / +0.7 | +16 / -14 / -0.2 | +16 / +3 / -0.2 | +0 / -0 / +0.0 | -1 / +1 / -0.1 |
| camH3 | +1 / +1 / -0.1 | -12 / +15 / -0.8 | -2 / +2 / +0.0 | -0 / -3 / -0.6 | +2 / +4 / -0.1 | -1 / +2 / -0.2 |
| OTE79 | -7 / +0 / +0.1 | -34 / +8 / +0.4 | -5 / +6 / +0.1 | -8 / +5 / +0.3 | -1 / -2 / -0.0 | -1 / -2 / -0.1 |
| OTE62act | +4 / +6 / -0.1 | -10 / +8 / +0.2 | +1 / -3 / -0.0 | +2 / +4 / -0.0 | +0 / +0 / +0.0 | +0 / +0 / -0.0 |
| KCup4h | +3 / -1 / -0.1 | -5 / +4 / -0.4 | -10 / +4 / +0.1 | -10 / +0 / +0.1 | +1 / -2 / -0.0 | -1 / +2 / +0.0 |
| OTE705 | -2 / +3 / -0.0 | -15 / +20 / +0.3 | +8 / +2 / -0.2 | -4 / -0 / +0.1 | -2 / +1 / +0.1 | +0 / +1 / -0.0 |
| PDmid | +0 / +0 / -0.0 | +0 / +0 / +0.1 | -10 / +4 / +0.1 | +0 / -1 / -0.1 | +0 / +1 / -0.0 | +0 / +1 / -0.0 |
| HVN0_1hs | -4 / +7 / +0.0 | +18 / -3 / -0.4 | +2 / +6 / +0.0 | -2 / +2 / -0.0 | +3 / -1 / -0.1 | -2 / +4 / +0.0 |
| CRT4h | +6 / +4 / -0.0 | -6 / +11 / +0.1 | +5 / -1 / -0.1 | +11 / +1 / -0.3 | -1 / +4 / +0.1 | +1 / +1 / -0.1 |
| VAH15s | +3 / -3 / -0.1 | +20 / -4 / -0.5 | -6 / -0 / +0.1 | +10 / -1 / -0.2 | +5 / -2 / +0.1 | +1 / -0 / -0.1 |
| LVN1_1hs | -1 / +0 / +0.0 | +0 / -3 / -0.2 | +2 / +6 / +0.0 | -2 / -2 / +0.0 | -8 / +7 / +0.1 | -0 / +1 / +0.0 |

### by session, PRE
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| kijun1h | -65 / +35 / +1.1 | -48 / -5 / +0.6 | +11 / -18 / -0.5 | -0 / -4 / -0.0 |
| OTE62b73 | -12 / +2 / +1.0 | +17 / -42 / -0.5 | -2 / -1 / -0.3 | +2 / +1 / -0.0 |
| camH3 | +0 / +8 / -1.2 | -36 / +43 / +0.5 | +4 / -1 / -1.1 | +1 / -1 / -0.0 |
| OTE79 | -24 / +25 / +0.4 | +2 / +12 / +0.0 | +4 / +6 / +0.4 | +1 / -3 / -0.0 |
| OTE62act | +1 / +9 / +0.1 | +8 / +3 / -0.1 | -1 / +5 / +0.0 | -2 / +3 / +0.0 |
| KCup4h | -40 / +17 / +0.4 | +14 / +0 / -0.1 | +1 / -7 / -0.5 | +2 / -0 / -0.1 |
| OTE705 | -10 / +18 / -0.1 | -9 / +5 / +0.2 | +0 / +6 / +0.1 | -2 / +2 / +0.0 |
| PDmid | -5 / +3 / -0.1 | +0 / +8 / +0.2 | +1 / +2 / +0.1 | +0 / +0 / +0.0 |
| HVN0_1hs | +15 / +6 / -0.1 | +32 / +6 / -0.1 | +0 / -2 / -0.3 | +1 / -0 / -0.0 |
| CRT4h | -9 / +17 / -0.9 | -49 / +39 / +0.6 | +0 / +4 / +0.2 | +3 / +0 / -0.1 |
| VAH15s | +23 / -14 / -0.8 | -9 / +4 / +0.1 | +12 / -16 / -0.0 | +1 / +0 / -0.0 |
| LVN1_1hs | -2 / -1 / -0.2 | -15 / +33 / +0.5 | -1 / +0 / -0.3 | -1 / +0 / +0.0 |

### by book, X'
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| kijun1h | -4 / +3 / +0.1 | -8 / +11 / +0.2 | -0 / +4 / -0.1 | -9 / +7 / +0.2 | +2 / -1 / -0.0 | -1 / +1 / -0.0 |
| OTE62b73 | -2 / +0 / +0.0 | -47 / -0 / +1.2 | +3 / -9 / -0.3 | -3 / +0 / +0.1 | -1 / -0 / +0.1 | +3 / -3 / -0.1 |
| camH3 | -3 / -1 / +0.1 | -25 / +3 / +0.5 | -3 / +6 / +0.2 | +1 / +4 / +0.0 | -0 / +0 / +0.0 | +0 / -2 / -0.0 |
| OTE79 | +2 / -2 / -0.1 | +22 / -20 / -0.5 | -9 / +9 / +0.2 | -3 / -1 / -0.1 | +2 / -2 / -0.0 | +0 / +0 / -0.1 |
| OTE62act | -1 / +2 / +0.0 | -15 / +9 / +0.4 | +0 / +1 / -0.1 | -3 / +3 / -0.0 | -1 / +1 / +0.0 | +1 / +1 / -0.1 |
| KCup4h | +1 / -2 / -0.1 | +8 / -3 / -0.1 | +2 / -2 / -0.1 | +6 / -1 / -0.0 | +1 / -1 / -0.0 | +0 / +0 / +0.1 |
| OTE705 | +5 / -2 / -0.3 | -9 / -1 / +0.3 | -5 / +0 / +0.0 | -1 / +6 / +0.0 | +4 / -0 / -0.1 | +5 / -4 / -0.1 |
| PDmid | +3 / -4 / -0.3 | +0 / +2 / -0.1 | -8 / +8 / +0.2 | -4 / +3 / +0.2 | +2 / +1 / -0.0 | -0 / -1 / +0.0 |
| HVN0_1hs | -1 / +1 / +0.0 | -13 / +11 / +0.2 | -3 / +6 / -0.0 | +4 / -4 / -0.2 | -3 / +2 / +0.1 | +0 / -1 / -0.0 |
| CRT4h | +2 / -1 / -0.0 | -5 / +19 / +0.2 | -5 / +7 / -0.1 | -2 / +8 / +0.2 | +5 / -4 / -0.1 | +0 / -1 / -0.2 |
| VAH15s | +5 / -3 / -0.1 | +19 / -17 / -0.6 | -2 / +3 / +0.1 | -4 / +8 / +0.1 | +1 / +0 / -0.0 | +3 / -3 / -0.1 |
| LVN1_1hs | +0 / +1 / -0.0 | +54 / -1 / -1.4 | +0 / +0 / -0.1 | +0 / -1 / -0.0 | +0 / +0 / -0.1 | -3 / +2 / +0.0 |

### by session, X'
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| kijun1h | -7 / +14 / +0.2 | -14 / +8 / +0.3 | +3 / -3 / -0.2 | +0 / +2 / +0.1 |
| OTE62b73 | -18 / -1 / +0.6 | -6 / -1 / +0.1 | -1 / +1 / +0.4 | +0 / -2 / -0.0 |
| camH3 | +0 / +23 / +0.5 | +26 / -21 / -0.6 | -21 / -1 / +0.5 | -2 / +1 / +0.3 |
| OTE79 | +1 / -3 / -0.7 | +10 / -3 / -0.2 | -10 / +20 / +0.2 | +0 / +3 / +0.1 |
| OTE62act | -3 / +9 / -0.2 | -2 / +1 / +0.0 | -15 / +14 / +0.4 | +0 / +2 / +0.1 |
| KCup4h | +16 / -9 / +0.1 | +1 / +2 / -0.0 | +7 / -6 / -0.3 | +0 / -3 / -0.0 |
| OTE705 | -9 / +26 / +0.6 | -6 / +4 / +0.2 | +23 / -6 / -0.8 | +1 / -2 / -0.1 |
| PDmid | -1 / +18 / +0.7 | -26 / +24 / +0.5 | +37 / -7 / -1.1 | +1 / -4 / -0.2 |
| HVN0_1hs | +2 / -1 / -0.2 | -3 / +6 / +0.0 | -15 / +14 / +0.2 | +1 / +1 / -0.0 |
| CRT4h | +2 / +3 / -0.3 | -34 / +38 / +0.8 | +11 / +12 / -0.7 | -1 / +1 / +0.0 |
| VAH15s | +13 / -10 / -0.5 | -5 / -1 / +0.1 | +10 / -3 / -0.2 | +0 / +0 / -0.0 |
| LVN1_1hs | +24 / -9 / -1.0 | +9 / -2 / -0.2 | +1 / +0 / -0.3 | +0 / +1 / +0.0 |

# A2 PROFILE-LINE VARIANTS, B1 SESSION-STRUCTURE LINES, LOCK FRAMES - interim (Z1; 2026-11-02 04:37Z; base D7 v1.3 EXACT V13eh, marginal-in-set unless stated)

POST-HOC, no PASS, Shadow only. Frames: lock 12R (combined stack lock + per-book locks) and lock OFF (per-book locks only, the user literal lock text). HEADLINE = lock OFF until the user confirms the combined lock; a cut that exists only with the combined lock is LOCK-ONLY (not a lead).

## Layer and lines in both lock frames (V13eh)
### Whole layer, lock OFF
| window | maxDD $k without > with (cut), combined lock OFF (sensitivity; headline has 12R) | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 35 > 37 (-6%) | 96 > 98 | 19.2 > 19.6 |
| L2M | 35 > 37 (-6%) | 218 > 225 | 24.2 > 25.0 |
| L3M | 53 > 50 (+7%) | 193 > 210 | 14.8 > 16.1 |
| L6M | 146 > 133 (+9%) | 6 > 27 | 27.4 > 26.9 |
| HOLD | 146 > 133 (+9%) | -635 > -604 | 23.3 > 23.9 |
| MID | 78 > 63 (+19%) | 140 > 131 | 11.7 > 10.9 |
| PRE | 245 > 178 (+27%) | -859 > -734 | 7.7 > 10.0 |
| X' | 190 > 135 (+29%) | -517 > -445 | -1.8 > -1.2 |
| ALL | 245 > 178 (+27%) | -1134 > -973 | 10.8 > 11.9 |
### Per line
| line | cut with combined 12R lock: L6M / HOLD / MID / PRE / X' | cut lock OFF (per-book locks only): L6M / HOLD / MID / PRE / X' | mean d $k/wk L6M lock12 / lock-off | flag |
|---|---|---|---|---|
| PDmid | -2% / -4% / +3% / +2% / +22% | -1% / -1% / +1% / -3% / +10% | -1.0 / -1.0 | survives lock-off |
| HVN0_1hs | +1% / +1% / +0% / +15% / +5% | -7% / -7% / -5% / -1% / +4% | -0.6 / -1.0 | LOCK-ONLY in PRE |
| kijun1h | -2% / +1% / +2% / +7% / +13% | +1% / +1% / +9% / -5% / +2% | +0.2 / -0.2 | LOCK-ONLY in X' |
| camH3 | +4% / +6% / -0% / +2% / +15% | -4% / -4% / -2% / +1% / +10% | +0.0 / -0.3 | no cut in either |
| VAH15s | -2% / +2% / +0% / +7% / +3% | +3% / +3% / -1% / +9% / +3% | -0.4 / -0.5 | no cut in either |
| CRT4h | +2% / +0% / +7% / +4% / +0% | +5% / +5% / +7% / +5% / +11% | +0.7 / +0.5 | survives lock-off |
| OTE705 | -12% / +5% / +6% / +7% / -7% | +3% / +3% / +5% / +2% / -1% | -0.6 / -0.3 | no cut in either |
| OTE79 | -1% / -1% / -1% / -1% / -1% | +4% / +4% / +2% / +12% / -9% | +0.0 / -0.0 | survives lock-off |
| OTE62act | +9% / -42% / +0% / -9% / +5% | -1% / +6% / +4% / +12% / +3% | +2.9 / -1.0 | survives lock-off |
| KCup4h | +7% / +1% / +0% / -7% / +3% | +0% / +0% / +0% / +1% / -4% | +0.4 / +0.2 | no cut in either |
| OTE62b73 | +6% / -37% / +1% / -4% / -4% | +1% / +8% / -2% / +8% / +18% | +3.8 / +0.7 | survives lock-off |
| LVN1_1hs | -2% / +1% / +2% / -2% / -10% | -2% / -2% / +4% / +0% / +5% | -0.3 / -0.6 | no cut in either |

## Plain answers (A2 / B1 / lock frames)
* LOCK FRAMES (V13X): the whole 7-line HALF layer SURVIVES with the combined lock removed (lock OFF: maxDD L6M/HOLD +9%, MID +19%, PRE +27%, X' +29%, worst-20 PRE -859 > -734k, X' -517 > -445k), so the layer is not a lock artefact (it cuts more without the combined lock than with it in PRE/X', less in MID/L6M). Per line, OTE-62 B73, OTE79, CRT4h and PDmid keep a lock-off cut in PRE or X'; HVN0_1hs and kijun1h cuts are LOCK-ONLY.
* PROFILE LINES (A2): NOT dead on every variant in the lock-12 frame: VAH15s with swing strength 3 passes the PRE+X' gate (cut PRE +21%, X' +13%, L6M +6%) and beats all three placebos in PRE (ranks 0.02 / 0.04 / 0.05) and X' (0.04 / 0.04 / 0.03), but the cut is LOCK-ONLY (lock OFF: PRE +10%, X' 0%), L6M is below 20%, and it is the best of 24 variants tried: labelled LOCK-ONLY, not a lead. Every other variant (bin 2/4 ticks, anchor shifts, session-anchored Asia/London/RTH value areas, LVN1/HVN0 at any variant) fails the gate: the profile lines are DEAD on every variant except the lock-only VAH15s swing-3.
* B1 SESSION LINES: of 37 session-structure lines none cuts L6M and PRE and X' together; seven pass the PRE+X' gate in the lock-12 frame (PDX prior-RTH low, week open, Globex open, Asia low, session-VWAP RTH -2 sigma, ...), but the PRE cuts are LOCK-ONLY for prior-RTH low, week open and Globex open (lock OFF PRE <= 2%), and Asia low / RTH VWAP -2 sigma have no lock-off cut. No B1 line is a lead on this evidence; placebo ranks follow below where run.

## A2. Profile-line variants (swing strength 3, bin 2 / 4 ticks, anchor shifts endconf / startm1, session-anchored Asia / London / RTH value areas) - marginal-in-set (line added to the shipped set)
| variant | rows firing D20 | kept removed | maxDD cut L6M / HOLD / MID / PRE / X' | worst-20 PRE b>a / X' b>a | mean d L6M / PRE / X' $k/wk (MDE) | PX gate | S/T/N |
|---|---|---|---|---|---|---|---|
| VAH15s_w3 | 1938 | -52 | +6% / +3% / +2% / +21% / +13% | -512>-498 ; -342>-338 | +0.0 (0.6) / +1.0 (2.0) / +0.5 (1.4) | pass | n/Y/Y |
| HVN0_1hs_bin4 | 1920 | -21 | +1% / +2% / +3% / +15% / +6% | -512>-518 ; -342>-329 | -0.5 (1.9) / +0.3 (1.7) / +0.2 (0.7) | fail | n/n/n |
| HVN0_1hs_bin2 | 1922 | 17 | +1% / +1% / +0% / +15% / +5% | -512>-519 ; -342>-329 | -0.6 (1.9) / -0.1 (2.0) / +0.2 (0.7) | fail | n/n/n |
| HVN0_1hs_w3 | 1681 | -23 | +7% / +1% / +0% / +12% / +0% | -512>-516 ; -342>-341 | -0.7 (1.7) / +0.0 (1.3) / +0.0 (0.3) | fail | n/n/n |
| HVN0_1hs_endconf | 1468 | 44 | +1% / +0% / +0% / +7% / +4% | -512>-513 ; -342>-336 | -0.2 (1.7) / -0.2 (2.1) / +0.2 (0.4) | fail | n/n/n |
| SESS_rth_val | 533 | 59 | +5% / +1% / +2% / +24% / -15% | -512>-467 ; -342>-347 | -0.6 (1.9) / +0.8 (1.6) / -0.6 (1.3) | fail | n/n/n |
| VAH15s_bin4 | 1945 | 226 | +3% / +2% / +0% / +7% / +2% | -512>-495 ; -342>-351 | -3.7 (9.1) / -0.2 (0.9) / +0.3 (1.8) | fail | n/n/n |
| VAH15s_endconf | 2456 | -79 | +9% / -3% / -6% / +26% / -18% | -512>-496 ; -342>-356 | +0.3 (1.2) / +0.2 (1.9) / -0.4 (2.7) | fail | n/Y/Y |
| SESS_asia_val | 732 | 4 | +5% / +0% / +0% / +0% / +7% | -512>-507 ; -342>-339 | +0.1 (0.4) / -0.3 (0.6) / +0.3 (0.6) | pass | n/n/Y |
| VAH15s_bin2 | 1973 | 212 | +3% / +2% / +0% / +1% / +3% | -512>-509 ; -342>-350 | -3.5 (9.1) / -0.4 (1.0) / +0.3 (1.8) | fail | n/n/n |
| SESS_london_val | 357 | 5 | +0% / +0% / +0% / +0% / +3% | -512>-512 ; -342>-337 | -0.0 (0.1) / +0.0 (0.1) / +0.1 (0.4) | pass | n/n/n |
| SESS_london_vah | 517 | -49 | +0% / +0% / +0% / -0% / +3% | -512>-512 ; -342>-342 | +0.1 (0.9) / -0.0 (0.4) / +0.1 (0.3) | fail | n/n/n |
| LVN1_1hs_w3 | 1202 | -124 | -1% / +1% / +2% / +1% / +2% | -512>-489 ; -342>-335 | -0.2 (0.7) / +1.6 (4.1) / +0.1 (0.6) | pass | n/n/n |
| SESS_asia_vah | 935 | 5 | +1% / +0% / +0% / +2% / -1% | -512>-513 ; -342>-340 | +0.0 (0.1) / -0.0 (0.3) / -0.0 (0.3) | fail | n/n/Y |
| SESS_asia_poc | 587 | 10 | +1% / +0% / +1% / -0% / +1% | -512>-512 ; -342>-339 | +0.1 (0.2) / -0.1 (0.4) / +0.0 (0.3) | fail | n/n/Y |
| SESS_london_poc | 291 | -6 | -7% / +0% / +0% / +2% / -3% | -512>-507 ; -342>-343 | -0.2 (0.5) / +0.1 (0.2) / -0.1 (0.2) | fail | n/n/n |
| HVN0_1hs_startm1 | 1975 | 22 | +6% / -2% / +0% / -0% / -1% | -512>-518 ; -342>-338 | +0.1 (1.3) / -0.2 (1.5) / -0.0 (0.4) | fail | n/n/n |
| LVN1_1hs_endconf | 1461 | 28 | -3% / +8% / -0% / -2% / -1% | -512>-503 ; -342>-339 | -0.3 (1.1) / +0.6 (1.8) / -0.0 (0.4) | fail | n/n/n |
| VAH15s_startm1 | 1890 | 49 | -2% / -1% / -2% / +0% / -4% | -512>-511 ; -342>-346 | -0.0 (0.5) / +0.0 (1.7) / -0.2 (0.3) | fail | n/n/n |
| SESS_rth_poc | 618 | 42 | +0% / -0% / +0% / -8% / +3% | -512>-523 ; -342>-338 | -0.2 (0.7) / -0.3 (0.8) / +0.1 (0.4) | fail | n/n/n |
| LVN1_1hs_startm1 | 1432 | -42 | -10% / +2% / +5% / -2% / -7% | -512>-526 ; -342>-346 | -1.0 (1.9) / -0.4 (0.7) / -0.3 (0.5) | fail | n/n/n |
| SESS_rth_vah | 715 | 150 | +0% / +4% / +0% / +0% / -9% | -512>-514 ; -342>-334 | +0.1 (0.3) / +0.0 (0.1) / -0.4 (2.0) | fail | n/n/Y |
| LVN1_1hs_bin2 | 1434 | -11 | -3% / +1% / +2% / +0% / -10% | -512>-489 ; -342>-344 | -0.3 (2.2) / +0.2 (1.0) / -0.4 (0.7) | fail | n/n/n |
| LVN1_1hs_bin4 | 1405 | -13 | -3% / +1% / +0% / -0% / -10% | -512>-489 ; -342>-344 | +0.3 (0.9) / +0.3 (1.0) / -0.4 (0.7) | fail | n/n/n |

### one-at-a-time (zone off -> variant alone)
| variant | rows firing D20 | kept removed | maxDD cut L6M / HOLD / MID / PRE / X' | worst-20 PRE b>a / X' b>a | mean d L6M / PRE / X' $k/wk (MDE) | PX gate | S/T/N |
|---|---|---|---|---|---|---|---|
| VAH15s_bin4 | 1945 | 124 | -2% / +4% / +4% / +6% / +11% | -608>-597 ; -386>-381 | -0.4 (0.8) / -0.1 (1.6) / -0.9 (3.2) | pass | n/n/n |
| VAH15s_bin2 | 1973 | 13 | -2% / +3% / +3% / +7% / +9% | -608>-593 ; -386>-383 | -0.5 (1.0) / +0.0 (1.7) / +0.0 (1.0) | pass | n/n/n |
| VAH15s_startm1 | 1890 | 133 | -3% / -1% / -1% / +8% / +6% | -608>-563 ; -386>-387 | +0.1 (0.6) / +0.3 (1.8) / +0.1 (0.6) | fail | n/Y/Y |
| HVN0_1hs_w3 | 1681 | 173 | +3% / +2% / +2% / +10% / -3% | -608>-546 ; -386>-373 | -0.9 (1.8) / +0.4 (2.5) / -0.2 (2.7) | fail | n/n/n |
| SESS_asia_vah | 935 | -8 | -0% / -7% / -9% / +4% / +3% | -608>-601 ; -386>-382 | -0.0 (0.1) / +0.6 (1.4) / +0.1 (0.3) | pass | n/n/n |
| SESS_asia_val | 732 | 5 | +4% / +1% / +1% / -2% / +8% | -608>-614 ; -386>-386 | +0.0 (0.4) / -0.4 (0.6) / +0.3 (0.6) | fail | n/n/Y |
| SESS_london_vah | 517 | 11 | +0% / +0% / +0% / +0% / +4% | -608>-611 ; -386>-389 | +0.2 (0.7) / -0.0 (0.4) / +0.1 (0.4) | fail | n/n/n |
| LVN1_1hs_w3 | 1202 | 105 | -2% / +1% / +1% / -9% / +13% | -608>-605 ; -386>-359 | -0.2 (0.7) / -0.7 (1.7) / +0.2 (1.8) | fail | n/n/n |
| SESS_rth_poc | 618 | 69 | +0% / +1% / +1% / +0% / +3% | -608>-617 ; -386>-394 | -0.4 (0.8) / -0.4 (1.6) / +0.0 (0.9) | fail | n/n/n |
| SESS_asia_poc | 587 | 4 | -4% / +0% / -0% / -1% / +2% | -608>-609 ; -386>-384 | -0.1 (0.3) / -0.0 (0.3) / +0.1 (0.4) | fail | n/n/n |
| VAH15s_w3 | 1938 | 392 | -2% / +3% / +3% / +5% / -4% | -608>-593 ; -386>-365 | +0.1 (0.8) / +0.1 (1.3) / -1.1 (3.8) | fail | n/Y/Y |
| SESS_london_val | 357 | 7 | +0% / +0% / +0% / +0% / +0% | -608>-608 ; -386>-386 | -0.0 (0.1) / +0.0 (0.1) / +0.0 (0.0) | fail | n/n/n |
| SESS_london_poc | 291 | 25 | +0% / +0% / +0% / -1% / -2% | -608>-607 ; -386>-386 | +0.0 (0.0) / +0.0 (0.3) / -0.0 (0.2) | fail | n/n/n |
| HVN0_1hs_bin2 | 1922 | 230 | +1% / +26% / +12% / +9% / -19% | -608>-562 ; -386>-382 | -0.8 (1.9) / +0.7 (2.3) / -0.4 (2.5) | fail | n/n/n |
| LVN1_1hs_bin4 | 1405 | 71 | -4% / -2% / -2% / -13% / +0% | -608>-611 ; -386>-396 | +0.3 (1.0) / -0.5 (1.7) / -0.1 (0.9) | fail | n/n/n |
| LVN1_1hs_bin2 | 1434 | 51 | -4% / -2% / -3% / -13% / -0% | -608>-611 ; -386>-397 | -0.3 (2.2) / -0.4 (1.8) / -0.1 (0.9) | fail | n/n/n |
| VAH15s_endconf | 2456 | 93 | +2% / -4% / -4% / +8% / -24% | -608>-591 ; -386>-376 | +0.1 (1.2) / +0.3 (2.2) / -0.8 (3.0) | fail | n/Y/Y |
| HVN0_1hs_endconf | 1468 | 148 | +9% / +24% / +9% / +11% / -30% | -608>-558 ; -386>-399 | -0.2 (1.9) / +1.4 (1.6) / -1.2 (2.8) | fail | n/n/n |
| HVN0_1hs_startm1 | 1975 | 241 | +6% / +5% / +7% / +7% / -26% | -608>-564 ; -386>-376 | -0.1 (1.3) / +0.5 (2.3) / -0.9 (2.7) | fail | n/n/n |
| HVN0_1hs_bin4 | 1920 | 255 | -0% / +28% / +14% / +9% / -29% | -608>-561 ; -386>-392 | -0.7 (1.9) / +0.8 (2.3) / -1.0 (2.6) | fail | n/n/n |
| SESS_rth_vah | 715 | 104 | +0% / +4% / +2% / +1% / -25% | -608>-618 ; -386>-388 | +0.2 (0.3) / +0.0 (0.5) / -0.9 (3.0) | fail | n/n/Y |
| LVN1_1hs_startm1 | 1432 | 67 | -11% / -2% / -2% / -0% / -24% | -608>-606 ; -386>-401 | -1.0 (2.0) / +0.1 (0.7) / -1.2 (2.5) | fail | n/n/n |
| LVN1_1hs_endconf | 1461 | 158 | -2% / +7% / +2% / -9% / -18% | -608>-606 ; -386>-397 | -0.1 (1.0) / -0.1 (1.9) / -0.7 (2.4) | fail | n/n/n |
| SESS_rth_val | 533 | 116 | +5% / +1% / +2% / +10% / -45% | -608>-589 ; -386>-376 | -0.1 (0.8) / +0.6 (1.1) / -1.3 (4.2) | fail | n/n/n |

### Placebos (3 kinds) and lock frames for the variants that pass the PRE+X' gate
| line (marginal-in-set, V13X exact) | maxDD cut L6M / HOLD / MID / PRE / X' | placebo A random-level / B same-volume / C shuffled-day: rank of the cut in L6M ; PRE ; X' (n) | worst-20 rank PRE A/B/C | S/T/N | verdict |
|---|---|---|---|---|---|
| VAH15s_w3 | +6% / +3% / +2% / +21% / +13% | 0.185/0.238/0.219 ; 0.020/0.040/0.053 ; 0.040/0.040/0.026 (n 150/150/150) | 0.238/0.245/0.232 | n/Y/Y | chance-level |

| line (marginal-in-set) | cut lock 12R: L6M / HOLD / MID / PRE / X' | cut lock OFF: L6M / HOLD / MID / PRE / X' | flag |
|---|---|---|---|
| VAH15s_w3 | +6% / +3% / +2% / +21% / +13% | -1% / -1% / -2% / +10% / +0% | LOCK-ONLY in X' |

## B1. Session-structure lines (Asia H/L, London H/L, overnight H/L, RTH initial balance H/L, prior RTH H/L/C/M, NY lunch H/L, Globex open print, weekly / monthly open, prior week / month, session VWAP and +-1/2 sigma for Asia / London / RTH) - marginal-in-set
Definitions: causal, row exists only after the source window closed (ET minutes: Asia 18:00-02:00, London 02:00-08:30, overnight 18:00-09:30, IB 09:30-10:30, lunch 12:00-13:00; VWAP/sigma = running session volume-weighted (h+l+c)/3 sampled every 900 s from data before the sample); life 24 h (7 d weekly open, 31 d monthly open, 900 s VWAP samples) or first 1-s touch; D = 20 pts nearest fresh ahead; skip/half action as the layer (HALF).
| variant | rows firing D20 | kept removed | maxDD cut L6M / HOLD / MID / PRE / X' | worst-20 PRE b>a / X' b>a | mean d L6M / PRE / X' $k/wk (MDE) | PX gate | S/T/N |
|---|---|---|---|---|---|---|---|
| B1_PDX_rth_L | 536 | 184 | -1% / -0% / -0% / +13% / +8% | -512>-512 ; -342>-334 | +0.0 (1.5) / +0.0 (1.6) / +0.3 (1.0) | pass | n/Y/Y |
| B1_WeekOpen | 58 | -17 | +1% / +1% / +1% / +13% / +6% | -512>-510 ; -342>-332 | +0.0 (0.1) / +1.0 (2.6) / +0.2 (0.6) | pass | Y/Y/Y |
| B1_PDX_rth_M | 1153 | -105 | -0% / -1% / -2% / +10% / +9% | -512>-518 ; -342>-341 | +0.2 (1.2) / +0.7 (2.0) / +0.4 (0.5) | fail | Y/n/Y |
| B1_SVRTH_m2 | 1688 | 37 | +0% / -1% / -1% / +8% / +10% | -512>-490 ; -342>-331 | +0.1 (0.1) / -0.5 (3.3) / +0.4 (0.5) | pass | n/n/Y |
| B1_SVLon_m2 | 1083 | -38 | -3% / +2% / +2% / +10% / +6% | -512>-523 ; -342>-333 | +0.4 (2.0) / -0.1 (1.7) / +0.2 (0.5) | fail | n/n/n |
| B1_SVLon_p1 | 534 | -53 | +1% / -11% / +0% / +14% / +1% | -512>-505 ; -342>-343 | -0.1 (0.6) / +0.5 (1.1) / +0.0 (0.2) | fail | n/n/n |
| B1_SVAsia_m1 | 435 | -27 | -5% / +0% / -6% / +8% / +5% | -512>-515 ; -342>-348 | -0.1 (0.6) / +0.1 (1.4) / +0.5 (1.7) | fail | n/n/n |
| B1_GlobexOpen | 280 | -20 | +1% / +1% / +1% / +12% / +1% | -512>-510 ; -342>-334 | +0.1 (0.3) / +1.0 (2.6) / +0.0 (0.8) | pass | Y/Y/Y |
| B1_AsiaL | 823 | -16 | +2% / +3% / +0% / +3% / +3% | -512>-505 ; -342>-337 | +1.2 (3.1) / +0.3 (0.3) / +0.1 (0.5) | pass | Y/Y/Y |
| B1_ONH | 777 | -14 | +1% / -0% / +0% / -0% / +6% | -512>-512 ; -342>-337 | +0.1 (0.1) / -0.0 (0.3) / +0.2 (0.4) | fail | n/n/Y |
| B1_LunchL | 507 | -7 | -2% / -1% / -1% / +10% / -5% | -512>-512 ; -342>-348 | -0.1 (0.3) / +0.4 (0.9) / -0.2 (0.4) | fail | n/n/n |
| B1_SVLon_m1 | 460 | 7 | +0% / -1% / -2% / +3% / +2% | -512>-505 ; -342>-342 | -0.2 (0.5) / +0.2 (0.5) / +0.1 (0.6) | pass | n/n/n |
| B1_ONL | 526 | -8 | +5% / +0% / +0% / +1% / +5% | -512>-512 ; -342>-332 | +0.2 (0.3) / +0.0 (0.1) / +0.2 (0.5) | fail | Y/n/Y |
| B1_PDX_rth_H | 1146 | 44 | -6% / -1% / +0% / +7% / -1% | -512>-496 ; -342>-340 | -0.2 (0.9) / +0.4 (1.6) / -0.1 (0.7) | fail | n/n/n |
| B1_SVAsia_vwap | 296 | -9 | -32% / +1% / -1% / -1% / +6% | -512>-510 ; -342>-340 | -0.8 (2.4) / -0.0 (0.3) / +0.6 (1.8) | fail | n/n/n |
| B1_LonH | 765 | 0 | -1% / +0% / +0% / +0% / +4% | -512>-513 ; -342>-342 | -0.0 (0.1) / +0.1 (0.2) / +0.1 (0.3) | fail | n/n/n |
| B1_LunchH | 720 | 50 | -3% / +0% / +0% / -0% / +3% | -512>-512 ; -342>-337 | -0.1 (0.2) / -0.1 (0.1) / +0.1 (0.5) | fail | n/n/n |
| B1_SVLon_vwap | 244 | 5 | +0% / +0% / +0% / +1% / +2% | -512>-511 ; -342>-342 | -0.1 (0.7) / +0.1 (0.1) / +0.1 (0.2) | pass | n/n/n |
| B1_SVAsia_p2 | 1199 | -73 | -16% / +28% / +1% / -5% / +8% | -512>-529 ; -342>-341 | -4.4 (9.0) / -0.1 (1.8) / +0.7 (2.2) | fail | n/n/n |
| B1_PDX_rth_C | 229 | 26 | +0% / -1% / +0% / -3% / +5% | -512>-511 ; -342>-337 | +0.0 (0.0) / +0.0 (0.5) / +0.2 (0.4) | fail | n/n/n |
| B1_LonL | 660 | -1 | +3% / +0% / +0% / +0% / +2% | -512>-512 ; -342>-339 | +0.1 (0.2) / -0.1 (0.2) / +0.1 (0.2) | fail | n/n/Y |
| B1_IBH | 846 | -30 | -6% / +3% / +0% / +8% / -6% | -512>-495 ; -342>-344 | -0.2 (0.4) / +0.6 (1.5) / -0.2 (0.4) | fail | n/n/n |
| B1_SVAsia_p1 | 450 | 14 | +1% / -3% / -2% / -2% / +4% | -512>-510 ; -342>-344 | +0.2 (1.0) / -0.2 (0.3) / +0.1 (0.7) | fail | n/n/n |
| B1_IBL | 451 | 53 | -15% / -0% / -0% / +1% / -0% | -512>-515 ; -342>-343 | -0.3 (1.0) / -0.4 (1.0) / -0.0 (0.2) | fail | n/n/n |
| B1_SVRTH_p1 | 1055 | -18 | +0% / +0% / +0% / -4% / +5% | -512>-521 ; -342>-341 | +0.0 (0.1) / -0.1 (0.3) / +0.2 (0.8) | fail | n/n/Y |
| B1_MonthOpen | 3 | 0 | +0% / +0% / +0% / +0% / +0% | -512>-512 ; -342>-342 | +0.0 (0.0) / +0.0 (0.0) / +0.0 (0.0) | fail | n/n/n |
| B1_PDX_month_L | 11 | 0 | +0% / +0% / +0% / +0% / +0% | -512>-512 ; -342>-342 | +0.0 (0.0) / +0.0 (0.0) / +0.0 (0.0) | fail | n/n/n |
| B1_PDX_week_L | 105 | -4 | -1% / +1% / +0% / +0% / -1% | -512>-512 ; -342>-342 | -0.1 (0.3) / -0.0 (0.0) / -0.0 (0.1) | fail | n/n/n |
| B1_PDX_week_H | 264 | 60 | +0% / +0% / +0% / +0% / -1% | -512>-483 ; -342>-343 | -0.0 (0.1) / +0.4 (1.0) / -0.0 (0.0) | fail | n/n/n |
| B1_PDX_month_H | 92 | 0 | +0% / +0% / +0% / -1% / +0% | -512>-512 ; -342>-342 | -0.0 (0.1) / -0.1 (0.1) / +0.0 (0.0) | fail | n/n/n |
| B1_SVAsia_m2 | 1001 | -18 | -3% / -3% / -1% / +2% / -8% | -512>-486 ; -342>-364 | +0.2 (1.2) / +0.3 (1.7) / -0.0 (2.1) | fail | n/Y/Y |
| B1_AsiaH | 1278 | 9 | +9% / -0% / +0% / -1% / -5% | -512>-513 ; -342>-348 | +0.1 (1.1) / +0.0 (0.5) / -0.2 (0.6) | fail | n/n/n |
| B1_SVLon_p2 | 1738 | -16 | -3% / +7% / +1% / +3% / -11% | -512>-474 ; -342>-349 | -0.3 (1.2) / +0.1 (1.2) / -0.4 (1.4) | fail | n/n/n |
| B1_SVRTH_p2 | 2995 | 7 | +2% / -2% / +0% / +1% / -16% | -512>-508 ; -342>-344 | +0.2 (0.3) / +0.5 (1.6) / -0.6 (2.0) | fail | n/Y/Y |
| B1_SVRTH_m1 | 996 | 55 | +1% / +0% / +0% / -10% / -7% | -512>-511 ; -342>-342 | -0.0 (0.2) / -0.3 (1.0) / -0.3 (0.6) | fail | n/n/n |
| B1_SVRTH_vwap | 649 | -3 | +0% / +0% / +0% / -1% / -17% | -512>-512 ; -342>-342 | +0.0 (0.0) / +0.4 (1.4) / -0.7 (1.8) | fail | n/Y/Y |
| B1_PDX_week_O | 154 | 34 | +6% / +0% / +0% / +0% / -19% | -512>-512 ; -342>-344 | -0.2 (0.9) / -0.0 (0.0) / -0.7 (1.8) | fail | n/n/n |

### one-at-a-time
| variant | rows firing D20 | kept removed | maxDD cut L6M / HOLD / MID / PRE / X' | worst-20 PRE b>a / X' b>a | mean d L6M / PRE / X' $k/wk (MDE) | PX gate | S/T/N |
|---|---|---|---|---|---|---|---|
| B1_WeekOpen | 58 | 11 | +0% / -0% / -0% / +14% / -0% | -608>-607 ; -386>-386 | +0.0 (0.1) / +0.6 (3.6) / +0.2 (0.5) | fail | Y/Y/Y |
| B1_GlobexOpen | 280 | 24 | +0% / -0% / -0% / +15% / -1% | -608>-607 ; -386>-382 | +0.1 (0.3) / +0.7 (3.6) / +0.2 (0.7) | fail | Y/Y/Y |
| B1_SVRTH_m2 | 1688 | -57 | +0% / -0% / -0% / +5% / +8% | -608>-601 ; -386>-380 | +0.1 (0.1) / +0.4 (1.8) / +0.2 (0.6) | pass | n/Y/Y |
| B1_SVAsia_vwap | 296 | 0 | -31% / +1% / +1% / +9% / +3% | -608>-606 ; -386>-381 | -0.6 (2.5) / +0.4 (1.3) / +0.1 (0.7) | pass | n/n/n |
| B1_SVLon_vwap | 244 | -53 | +0% / +0% / +0% / +9% / +3% | -608>-610 ; -386>-385 | -0.1 (0.7) / +0.4 (1.2) / +0.1 (0.2) | fail | n/n/n |
| B1_LunchH | 720 | -16 | -3% / +0% / +0% / +9% / +3% | -608>-607 ; -386>-383 | +0.1 (0.5) / -0.1 (1.7) / +0.0 (0.5) | pass | n/n/n |
| B1_SVRTH_p1 | 1055 | -61 | +0% / +0% / +0% / +12% / -3% | -608>-598 ; -386>-386 | +0.0 (0.1) / +0.5 (1.2) / +0.1 (0.8) | fail | n/n/n |
| B1_AsiaL | 823 | -102 | -1% / +3% / +2% / +9% / -1% | -608>-605 ; -386>-386 | +1.1 (3.0) / +0.9 (1.6) / +0.1 (0.5) | fail | Y/Y/Y |
| B1_SVAsia_p2 | 1199 | -65 | -11% / -1% / -2% / +9% / -1% | -608>-574 ; -386>-382 | -1.5 (2.4) / +0.4 (2.0) / +0.1 (0.9) | fail | n/n/n |
| B1_PDX_rth_M | 1153 | 8 | -0% / +3% / +2% / -13% / +20% | -608>-585 ; -386>-371 | -0.5 (4.4) / +0.4 (2.4) / +0.9 (2.0) | fail | n/n/n |
| B1_SVLon_p1 | 534 | 0 | -0% / +6% / +2% / +4% / +1% | -608>-601 ; -386>-387 | -0.2 (0.7) / +0.3 (0.5) / +0.0 (0.2) | fail | n/n/n |
| B1_SVAsia_m1 | 435 | -223 | -4% / +2% / +0% / +3% / +1% | -608>-610 ; -386>-392 | +1.8 (4.9) / +0.3 (2.3) / +0.1 (0.7) | fail | Y/n/Y |
| B1_IBL | 451 | 28 | -13% / -0% / -0% / +1% / +2% | -608>-611 ; -386>-373 | -0.6 (1.6) / -0.1 (0.3) / +0.3 (0.7) | fail | n/n/n |
| B1_LonH | 765 | 4 | -1% / +0% / +0% / -0% / +3% | -608>-609 ; -386>-386 | -0.0 (0.1) / +0.1 (0.2) / -0.0 (0.4) | fail | n/n/n |
| B1_LunchL | 507 | 39 | -2% / -1% / -2% / +0% / +2% | -608>-610 ; -386>-372 | -0.1 (0.3) / -0.0 (0.1) / +0.3 (0.7) | fail | n/n/n |
| B1_AsiaH | 1278 | 47 | +5% / +2% / +2% / -1% / +2% | -608>-603 ; -386>-376 | -0.2 (1.0) / -0.1 (0.3) / +0.1 (0.6) | fail | n/n/n |
| B1_ONH | 777 | 7 | +0% / +2% / +2% / -1% / +2% | -608>-608 ; -386>-386 | +0.1 (0.2) / -0.0 (0.2) / +0.1 (0.4) | fail | n/n/Y |
| B1_PDX_week_H | 264 | -8 | +0% / -5% / -6% / +0% / +0% | -608>-580 ; -386>-386 | -0.0 (0.1) / +0.4 (1.0) / -0.1 (0.1) | fail | n/n/n |
| B1_IBH | 846 | 15 | -1% / +7% / +2% / +3% / -3% | -608>-597 ; -386>-386 | -0.0 (0.1) / +0.1 (0.4) / -0.3 (0.7) | fail | n/n/n |
| B1_PDX_rth_L | 536 | 148 | -13% / +0% / +0% / -4% / +4% | -608>-610 ; -386>-373 | -0.7 (1.6) / -0.0 (2.1) / +0.4 (0.9) | fail | n/n/n |
| B1_MonthOpen | 3 | 0 | +0% / +0% / +0% / +0% / +0% | -608>-608 ; -386>-386 | +0.0 (0.0) / +0.0 (0.0) / +0.0 (0.0) | fail | n/n/n |
| B1_PDX_week_L | 105 | 0 | -1% / +1% / +1% / +0% / +0% | -608>-608 ; -386>-386 | -0.0 (0.1) / -0.0 (0.0) / -0.0 (0.1) | fail | n/n/n |
| B1_PDX_month_L | 11 | 0 | +0% / +0% / +0% / +0% / +0% | -608>-608 ; -386>-386 | +0.0 (0.0) / +0.0 (0.0) / +0.0 (0.0) | fail | n/n/n |
| B1_LonL | 660 | -2 | +0% / +0% / +0% / +0% / -0% | -608>-608 ; -386>-385 | +0.0 (0.0) / -0.1 (0.2) / -0.0 (0.2) | fail | n/n/n |
| B1_ONL | 526 | 0 | +1% / +0% / +0% / +1% / -1% | -608>-607 ; -386>-385 | +0.1 (0.1) / +0.0 (0.2) / +0.1 (0.4) | fail | Y/Y/Y |
| B1_PDX_month_H | 92 | 0 | +0% / +0% / +0% / -1% / +0% | -608>-608 ; -386>-386 | -0.0 (0.1) / -0.0 (0.1) / +0.0 (0.0) | fail | n/n/n |
| B1_SVLon_p2 | 1738 | -31 | -3% / +11% / +2% / -1% / -0% | -608>-569 ; -386>-381 | -0.3 (1.2) / +0.2 (1.4) / -0.2 (1.0) | fail | n/n/n |
| B1_SVLon_m2 | 1083 | 26 | -4% / +3% / +3% / +3% / -6% | -608>-605 ; -386>-395 | +0.8 (2.0) / -0.1 (0.9) / +0.2 (1.1) | fail | n/n/n |
| B1_PDX_rth_H | 1146 | 63 | -1% / -1% / -1% / -8% / +5% | -608>-600 ; -386>-385 | -0.0 (0.7) / -0.9 (2.2) / -0.2 (0.8) | fail | n/n/n |
| B1_SVLon_m1 | 460 | 13 | +0% / -0% / -0% / -0% / -4% | -608>-610 ; -386>-391 | -0.2 (0.5) / -0.1 (0.3) / +0.1 (0.6) | fail | n/n/n |
| B1_SVAsia_p1 | 450 | -14 | +1% / -2% / -2% / -2% / -2% | -608>-606 ; -386>-381 | +0.1 (1.1) / -0.3 (0.4) / +0.2 (0.6) | fail | n/n/n |
| B1_PDX_rth_C | 229 | 158 | +0% / -1% / -1% / -19% / +10% | -608>-608 ; -386>-384 | +0.0 (0.1) / -1.2 (2.2) / +0.4 (1.3) | fail | n/n/n |
| B1_SVRTH_m1 | 996 | 0 | +1% / +0% / +0% / -2% / -9% | -608>-615 ; -386>-386 | -0.0 (0.2) / -0.1 (0.4) / -0.3 (0.6) | fail | n/n/n |
| B1_SVAsia_m2 | 1001 | -36 | -3% / -3% / -4% / -9% / -6% | -608>-581 ; -386>-399 | +0.1 (1.2) / +0.6 (2.4) / -1.5 (3.5) | fail | n/n/n |
| B1_SVRTH_vwap | 649 | -20 | +0% / +0% / +0% / -1% / -28% | -608>-609 ; -386>-386 | +0.0 (0.0) / -0.1 (0.2) / -1.0 (2.9) | fail | n/n/n |
| B1_PDX_week_O | 154 | 41 | +6% / +0% / +0% / -1% / -30% | -608>-608 ; -386>-386 | -0.2 (0.9) / -0.1 (0.1) / -1.1 (2.9) | fail | n/n/n |
| B1_SVRTH_p2 | 2995 | -80 | +1% / -1% / -1% / -3% / -35% | -608>-597 ; -386>-397 | +0.2 (0.2) / +0.4 (2.5) / -1.6 (3.2) | fail | n/n/Y |

### B1 candidates (PX gate pass): placebos and lock frames
| line (marginal-in-set, V13X exact) | maxDD cut L6M / HOLD / MID / PRE / X' | placebo A random-level / B same-volume / C shuffled-day: rank of the cut in L6M ; PRE ; X' (n) | worst-20 rank PRE A/B/C | S/T/N | verdict |
|---|---|---|---|---|---|
| B1_PDX_rth_L | -1% / -0% / -0% / +13% / +8% | 0.654/-/- ; 0.269/-/- ; 0.038/-/- (n 25/0/0) | 0.808/-/- | n/Y/Y | chance-level |
| B1_WeekOpen | +1% / +1% / +1% / +13% / +6% | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | -/-/- | Y/Y/Y | placebo pending |
| B1_GlobexOpen | +1% / +1% / +1% / +12% / +1% | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | -/-/- | Y/Y/Y | placebo pending |
| B1_AsiaL | +2% / +3% / +0% / +3% / +3% | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | -/-/- | Y/Y/Y | placebo pending |
| B1_SVRTH_m2 | +0% / -1% / -1% / +8% / +10% | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | -/-/- | n/n/Y | placebo pending |

| line (marginal-in-set) | cut lock 12R: L6M / HOLD / MID / PRE / X' | cut lock OFF: L6M / HOLD / MID / PRE / X' | flag |
|---|---|---|---|
| B1_PDX_rth_L | -1% / -0% / -0% / +13% / +8% | -3% / -3% / +1% / +1% / -12% | LOCK-ONLY in PRE |
| B1_WeekOpen | +1% / +1% / +1% / +13% / +6% | +0% / +0% / +2% / +2% / +0% | LOCK-ONLY in PRE |
| B1_GlobexOpen | +1% / +1% / +1% / +12% / +1% | +0% / +0% / +2% / -0% / -2% | LOCK-ONLY in PRE |
| B1_AsiaL | +2% / +3% / +0% / +3% / +3% | +1% / +1% / +0% / +3% / +7% | no cut lock-off |
| B1_SVRTH_m2 | +0% / -1% / -1% / +8% / +10% | +0% / +0% / -1% / +6% / +2% | no cut lock-off |

# D7 v1.3 EXACT (V13X) ROBUSTNESS SECTION - v13exact (Z1, T-ZONES-3 section 1; 2026-11-02 05:53Z)

POST-HOC, no PASS claims, Shadow only. New cap 20261031, windows L1M L2M L3M L6M HOLD MID PRE X (L1M/L2M view only). BASE = D7 v1.3 EXACT (d7_v13x.py: exact U7 SM same-side 30 min [never binds], exact NY-AM lots, 5 exact take/tighten lines, per-book 12R floor + day give-back lock, ER(20), zones HALF, 12R combined lock). Headline frame V13eh; the earlier ASSUMED v1.3 base (V13x/V13h) is shown only as comparison and labelled assumed. Placebos: A random-level same-count, B same-volume random, C shuffled-day; draws 7584 total, n per context in tables. Preregs: ZONES3_S1 (09ac46ad), addendum redo, addendum2 v12 (3d0b218f1131) in DECISIONS.md; draws and cells follow the same definitions.

## Plain answers
ALL ROWS BELOW ARE 'ASSUMED BASE' (v1.3-assumed, screen V13x = U7 off; placebo draws 100 per kind and context where stated). They will be re-run on the user's EXACT v1.3 (V13X) when BASE-4 announces it; where the cut changes that is base-dependence.
* LAYER (premise): the shipped HALF layer cuts maxDD on the assumed v1.3 screen in every window by sign (L6M/HOLD +7%, MID +25%, PRE +31%, X' +12%, L3M +19%), but only PRE is near chance-distinguishable on maxDD (rank 0.17 random-level / 0.12 same-volume) and L6M/HOLD are WORSE than a random same-size half-lot cut (rank 0.87 / 0.83). What the layer does beat is the TAIL: worst-20 in PRE -599 > -482k and ALL -753 > -618k, ranks 0.11 / 0.02 (PRE) and 0.10 / 0.02 (ALL) vs random-level / same-volume. With the blackout ON (V13h) the L6M cut is +18% but L2M/L3M flip to -6% / -4%: the recent cut changes sign with the base.
* DEFINITION SENSITIVITY (layer): L6M cut is 1% to 8% at every D (10..40) and -24% with the 'fresh or touched' variant; PRE cut +14% to +34% at all D; so the layer is not D-fragile in PRE but gives essentially nothing in L6M at any D.
* LINES (marginal-in-set, assumed base): only kijun1h (PRE +32%, beats all three placebos in PRE at ranks 0.02 / 0.01 / 0.01, but L6M -1% and X' +6%) and OTE-62 B73 (L6M +13%, PRE +18%, X' +13%, STRICT/TOLERANT/NOW-ONLY all yes, action line so no placebo) look like leads; OTE-62 B73 is the only line with all of L6M, HOLD, PRE, X' cutting. Neither is RISK-KEEP on the full standard (kijun1h fails X' and L6M; B73 has no placebo and PRE+X' cuts are below 20%). CRT4h, camH3, PDmid, KCup4h, OTE705 add nothing consistent. The three uncoded profile lines HURT: VAH15s PRE -18%, HVN0_1hs PRE -14%, LVN1_1hs X' -23% (rank 1.00 on all placebos); they should NOT be added.
* NOT DONE: swing strength / profile bin / anchor-shift variants, 1-s/3-s entry delay (no engine parameter), subset landscape still running, shuffled-day placebo done for premise and lines with draws shown.


## 1. Premise on v1.3 screening base V13x (zone piece off vs shipped HALF layer)
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 39 > 16 (+58%) | [+8%, +71%] / 1.00 / 0.88 | 20261012 > 20261026 | n/a | n/a | 15 > 118 * | 39.5 > 47.3 | 0.08 > 1.43 | +20.5 (47.6) | 0.249 / 0.284 (200 / 200) | - |
| L2M (view) (9) | 54 > 27 (+50%) | [-3%, +66%] / 0.75 / 0.54 | 20261012 > 20260907 | n/a | -10% .. +58% | 109 > 216 * | 45.0 > 46.5 | 0.22 > 0.89 | +11.9 (27.0) | 0.269 / 0.214 (200 / 200) | - |
| L3M (13) | 54 > 40 (+26%) | [+2%, +57%] / 0.97 / 0.53 | 20261012 > 20260907 | n/a | +9% .. +56% | 96 > 205 * | 39.6 > 41.7 | 0.14 > 0.40 | +8.4 (18.9) | 0.303 / 0.284 (200 / 200) | - |
| L6M (27) | 72 > 74 (-2%) | [-5%, +44%] / 0.68 / 0.23 | 20260907 > 20260907 | -2% .. +9% (4 drops) | -14% .. +25% | -143 > -52 | 53.1 > 50.0 | 0.27 > 0.30 | +2.8 (9.9) | 0.478 / 0.622 (200 / 200) | 0.368 / 0.488 |
| HOLD (52) | 118 > 119 (-1%) | [-36%, +31%] / 0.65 / 0.17 | 20260323 > 20260323 | -8% .. -1% (6 drops) | -23% .. +30% | -447 > -405 | 50.4 > 48.6 | 0.16 > 0.17 | +0.7 (7.4) | 0.896 / 0.791 (200 / 200) | 0.572 / 0.443 |
| MID (12) | 95 > 79 (+17%) | [+2%, +32%] / 0.96 / 0.31 | 20260323 > 20260323 | n/a | +16% .. +40% | 65 > 64 * | 43.0 > 39.2 | 0.06 > 0.07 | -0.1 (9.0) | 0.458 / 0.204 (200 / 200) | - |
| PRE (75) | 329 > 252 (+23%) | [-13%, +57%] / 0.88 / 0.60 | 20250414 > 20250414 | +18% .. +30% (10 drops) | +10% .. +33% | -608 > -512 | 37.8 > 34.0 | 0.01 > 0.02 | +1.7 (7.0) | 0.448 / 0.373 (200 / 200) | 0.224 / 0.164 |
| X' (44) | 145 > 174 (-20%) | [-222%, +32%] / 0.25 / 0.12 | 20240115 > 20240129 | -52% .. -3% (9 drops) | -53% .. +29% | -386 > -342 | 22.9 > 18.4 | -0.01 > -0.02 | -2.4 (5.8) | 0.463 / 0.756 (200 / 200) | 0.070 / 0.045 |
| ALL (187) | 329 > 252 (+23%) | [-38%, +44%] / 0.68 / 0.32 | 20250414 > 20250414 | +10% .. +23% (16 drops) | -1% .. +36% | -733 > -619 | 39.9 > 37.2 | 0.02 > 0.03 | +0.4 (3.7) | 0.279 / 0.318 (200 / 200) | 0.109 / 0.050 |

### Comparison: ASSUMED v1.3 base (screen, U7 off) premise pair
| window (weeks) | maxDD $k without > with (cut) | 90% block-bootstrap CI of the cut / P(cut>0) / P(cut>=20%) | trough week without > with | leave-one-episode-out cut range | leave-one-month-out cut range | worst-20 $k without > with | weekly SD $k | Calmar | mean d $k/wk (MDE) | placebo rank of the maxDD cut: random-level / same-volume (n draws) | worst-20 rank A / B |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 21 > 15 (+27%) | [-105%, +57%] / 0.56 / 0.40 | 20261012 > 20261005 | n/a | n/a | 70 > 113 * | 38.9 > 45.3 | 0.66 > 1.47 | +8.6 (52.8) | 0.257 / 0.297 (100 / 100) | - |
| L2M (view) (9) | 37 > 30 (+18%) | [-50%, +39%] / 0.70 / 0.14 | 20260907 > 20260907 | n/a | +18% .. +27% | 224 > 222 * | 48.6 > 46.8 | 0.67 > 0.81 | -0.3 (39.1) | 0.545 / 0.475 (100 / 100) | - |
| L3M (13) | 50 > 41 (+19%) | [-42%, +37%] / 0.69 / 0.15 | 20260907 > 20260907 | n/a | -8% .. +19% | 224 > 217 * | 43.0 > 41.3 | 0.35 > 0.41 | -0.6 (26.6) | 0.416 / 0.386 (100 / 100) | - |
| L6M (27) | 115 > 107 (+7%) | [-16%, +22%] / 0.82 / 0.06 | 20260907 > 20260907 | +0% .. +7% (3 drops) | -1% .. +13% | 4 > -11 | 58.5 > 57.7 | 0.24 > 0.25 | -0.2 (13.4) | 0.871 / 0.871 (100 / 100) | 0.792 / 0.733 |
| HOLD (52) | 115 > 107 (+7%) | [-11%, +36%] / 0.85 / 0.31 | 20260907 > 20260907 | +7% .. +36% (6 drops) | -1% .. +36% | -424 > -391 | 52.5 > 52.3 | 0.20 > 0.23 | +1.2 (7.4) | 0.832 / 0.832 (100 / 100) | 0.683 / 0.594 |
| MID (12) | 89 > 67 (+25%) | [+12%, +51%] / 0.99 / 0.77 | 20260323 > 20260323 | n/a | +25% .. +48% | 86 > 122 * | 42.4 > 38.9 | 0.08 > 0.15 | +3.0 (7.2) | 0.624 / 0.515 (100 / 100) | - |
| PRE (75) | 281 > 192 (+31%) | [-45%, +44%] / 0.73 / 0.41 | 20250428 > 20250428 | +12% .. +33% (10 drops) | -5% .. +36% | -599 > -482 | 39.3 > 33.2 | 0.01 > 0.01 | -1.3 (6.9) | 0.168 / 0.119 (100 / 100) | 0.109 / 0.020 |
| X' (44) | 288 > 253 (+12%) | [-87%, +46%] / 0.60 / 0.36 | 20240115 > 20231120 | +1% .. +24% (8 drops) | -5% .. +35% | -363 > -371 | 20.7 > 19.6 | -0.02 > -0.02 | +0.5 (6.3) | 0.703 / 0.792 (100 / 100) | 0.436 / 0.554 |
| ALL (187) | 326 > 284 (+13%) | [-33%, +41%] / 0.73 / 0.37 | 20240226 > 20250428 | +4% .. +22% (17 drops) | -11% .. +36% | -753 > -618 | 42.6 > 39.9 | 0.03 > 0.03 | -0.1 (3.8) | 0.673 / 0.663 (100 / 100) | 0.099 / 0.020 |

### Per book and session (V13h)
| book / session | L3M maxDD $k without > with [P(cut>0)] / worst-20 / mean d | L6M maxDD $k without > with [P(cut>0)] / worst-20 / mean d | HOLD maxDD $k without > with [P(cut>0)] / worst-20 / mean d | MID maxDD $k without > with [P(cut>0)] / worst-20 / mean d | PRE maxDD $k without > with [P(cut>0)] / worst-20 / mean d | X' maxDD $k without > with [P(cut>0)] / worst-20 / mean d |
|---|---|---|---|---|---|---|
| K6 | 14 > 11 [0.98] / 7 > 41 / +2.6 | 18 > 16 [0.80] / -18 > 6 / +0.6 | 64 > 59 [0.81] / -109 > -104 / +0.2 | 64 > 56 [0.89] / -36 > -36 / -0.0 | 66 > 68 [0.62] / -135 > -129 / +0.0 | 14 > 16 [0.14] / -63 > -70 / -0.7 |
| P6 | 17 > 20 [0.31] / 102 > 136 / +2.6 | 54 > 49 [0.54] / -21 > 6 / +1.2 | 102 > 98 [0.67] / -361 > -347 / +0.0 | 69 > 43 [0.46] / 37 > 21 / -1.3 | 249 > 189 [0.85] / -506 > -441 / +1.9 | 141 > 162 [0.35] / -384 > -330 / -0.9 |
| U6 | 13 > 18 [0.24] / 28 > 11 / -1.3 | 23 > 27 [0.03] / -55 > -74 / -1.0 | 29 > 27 [0.35] / -133 > -141 / -0.4 | 29 > 27 [0.91] / 11 > 23 / +1.0 | 79 > 64 [0.79] / -184 > -167 / +0.1 | 20 > 23 [0.35] / -76 > -67 / -0.4 |
| H6 | 43 > 26 [1.00] / -39 > 3 / +3.2 | 43 > 26 [0.92] / -81 > -54 / +1.5 | 43 > 26 [0.88] / -127 > -107 / +0.5 | 13 > 13 [0.80] / 39 > 35 / -0.3 | 45 > 44 [0.67] / -132 > -118 / -0.1 | 28 > 25 [0.59] / -84 > -68 / -0.1 |
| M6 | 18 > 23 [0.56] / -16 > -12 / +0.3 | 27 > 33 [0.50] / -48 > -44 / +0.1 | 40 > 36 [0.79] / -98 > -98 / +0.5 | 12 > 13 [0.45] / 7 > 19 / +1.0 | 68 > 63 [0.64] / -105 > -101 / -0.0 | 25 > 35 [0.23] / -55 > -57 / -0.5 |
| A6 | 7 > 4 [0.97] / 13 > 25 / +0.9 | 14 > 16 [0.41] / -31 > -22 / +0.3 | 14 > 16 [0.22] / -68 > -63 / +0.0 | 7 > 8 [0.05] / 8 > 2 / -0.5 | 22 > 18 [0.41] / -71 > -63 / -0.3 | 26 > 18 [0.94] / -46 > -34 / +0.2 |
| asia | 38 > 24 [0.98] / 100 > 195 / +7.3 | 56 > 56 [0.76] / -98 > -43 / +2.7 | 77 > 62 [0.75] / -337 > -319 / +0.5 | 77 > 62 [0.74] / 164 > 147 / -1.4 | 162 > 95 [0.98] / -442 > -306 / +1.4 | 142 > 111 [0.68] / -326 > -283 / -0.5 |
| london | 56 > 54 [0.74] / 15 > 9 / -0.5 | 56 > 54 [0.77] / -122 > -125 / -0.3 | 103 > 105 [0.59] / -320 > -329 / -0.4 | 103 > 105 [0.78] / -71 > -66 / +0.4 | 300 > 235 [0.95] / -506 > -451 / +1.2 | 153 > 147 [0.72] / -295 > -247 / +0.1 |
| nyam | 17 > 13 [0.97] / -11 > -1 / +0.8 | 17 > 13 [0.99] / -40 > -25 / +0.6 | 98 > 98 [0.81] / -204 > -157 / +0.7 | 53 > 38 [0.76] / -24 > -16 / +0.7 | 76 > 92 [0.36] / -256 > -245 / -0.7 | 65 > 76 [0.30] / -240 > -233 / -1.9 |
| nypm | 9 > 4 [0.99] / -7 > 2 / +0.7 | 19 > 29 [0.34] / -27 > -32 / -0.2 | 31 > 38 [0.45] / -54 > -55 / -0.0 | 14 > 13 [0.71] / -3 > -1 / +0.2 | 25 > 33 [0.31] / -63 > -61 / -0.2 | 9 > 9 [0.41] / -33 > -32 / -0.1 |

### Combined lock OFF sensitivity (V13h)
| window | maxDD $k without > with (cut), combined lock OFF (sensitivity; headline has 12R) | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 35 > 37 (-6%) | 96 > 98 | 19.2 > 19.6 |
| L2M | 35 > 37 (-6%) | 218 > 225 | 24.2 > 25.0 |
| L3M | 53 > 50 (+7%) | 193 > 210 | 14.8 > 16.1 |
| L6M | 146 > 133 (+9%) | 6 > 27 | 27.4 > 26.9 |
| HOLD | 146 > 133 (+9%) | -635 > -604 | 23.3 > 23.9 |
| MID | 78 > 63 (+19%) | 140 > 131 | 11.7 > 10.9 |
| PRE | 245 > 178 (+27%) | -859 > -734 | 7.7 > 10.0 |
| X' | 190 > 135 (+29%) | -517 > -445 | -1.8 > -1.2 |
| ALL | 245 > 178 (+27%) | -1134 > -973 | 10.8 > 11.9 |

### Weekly vol terciles (weekly mean daily 1-min range, all 187 weeks): layer effect per line, marginal-in-set (V13x; mean delta $k/wk / worst-week delta / weeks)
| line | low-vol tercile: mean d $k/wk / worst-week d / weeks | mid | high |
|---|---|---|---|
| PDmid | +0.9 / -3.2 / 62 | -0.0 / -7.2 / 63 | -0.6 / -21.4 / 62 |
| HVN0_1hs | -0.2 / -7.3 / 62 | +0.0 / -27.9 / 63 | -0.3 / -10.3 / 62 |
| kijun1h | +0.7 / -3.7 / 62 | -0.4 / -28.2 / 63 | +1.8 / -5.0 / 62 |
| camH3 | -0.4 / -35.6 / 62 | +0.6 / -23.2 / 63 | -1.7 / -116.1 / 62 |
| VAH15s | +0.1 / -8.8 / 62 | -0.1 / -10.0 / 63 | -1.3 / -53.3 / 62 |
| CRT4h | +0.2 / -34.3 / 62 | +0.0 / -27.4 / 63 | +0.5 / -8.1 / 62 |
| OTE705 | +0.1 / -6.9 / 62 | +0.3 / -5.9 / 63 | +0.0 / -6.1 / 62 |
| OTE79 | -0.0 / -22.4 / 62 | +1.6 / -18.9 / 63 | -0.1 / -26.9 / 62 |
| OTE62act | +0.7 / -2.9 / 62 | -0.4 / -28.9 / 63 | +0.1 / -80.6 / 62 |
| KCup4h | -0.7 / -32.4 / 62 | -0.5 / -22.5 / 63 | +0.0 / -3.2 / 62 |
| OTE62b73 | -0.5 / -17.0 / 62 | -0.3 / -29.3 / 63 | +1.3 / -80.9 / 62 |
| LVN1_1hs | +0.2 / -9.7 / 62 | +0.0 / -3.0 / 63 | -0.2 / -18.6 / 62 |

## 2. Line table, V13X EXACT (V13eh), ranked by drawdown contribution (marginal-in-set)
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | PDmid (coded) | -4 (-0.0%) | 72>74 (-2%) | 114>119 (-4%) | 81>79 (+3%) | 257>252 (+2%) | 221>174 (+22%) | -524>-512 | -361>-342 | -1.0 (2.2) / -0.8 (1.3) / -0.1 (1.0) / +0.2 (0.7) / +1.1 (2.1) | -0.9 / +1.2 / +1.0 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 2 | HVN0_1hs (UNCODED) | 17 (0.1%) | 74>73 (+1%) | 119>118 (+1%) | 79>78 (+0%) | 252>215 (+15%) | 174>165 (+5%) | -512>-519 | -342>-329 | -0.6 (1.9) / -0.2 (1.0) / -0.2 (0.7) / -0.1 (2.0) / +0.2 (0.7) | -3.3 / -1.5 / +1.1 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 3 | kijun1h (coded) | -447 (-3.8%) | 72>74 (-2%) | 120>119 (+1%) | 80>79 (+2%) | 272>252 (+7%) | 200>174 (+13%) | -516>-512 | -338>-342 | +0.2 (1.1) / +0.0 (0.7) / -0.3 (1.8) / +0.7 (2.6) / +0.6 (1.9) | -0.2 / +1.3 / +0.5 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/Y/Y | Y/Y | n | Y |
| 4 | camH3 (coded) | 143 (1.2%) | 77>74 (+4%) | 126>119 (+6%) | 78>79 (-0%) | 258>252 (+2%) | 203>174 (+15%) | -538>-512 | -343>-342 | +0.0 (0.7) / -0.1 (1.0) / +0.3 (3.5) / -1.7 (4.7) / +0.7 (2.4) | -0.0 / -1.5 / +0.1 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | Y |
| 5 | VAH15s (UNCODED) | 95 (0.8%) | 74>75 (-2%) | 119>117 (+2%) | 79>78 (+0%) | 252>235 (+7%) | 174>169 (+3%) | -512>-494 | -342>-350 | -0.4 (0.6) / -1.4 (3.1) / -3.5 (12.9) / -0.3 (0.9) / +0.3 (1.8) | -0.8 / +0.3 / +0.2 | 0.535/0.594/0.609 ; 0.505/0.436/0.406 ; 0.396/0.297/0.319 (n 100/100/68) | no | n/n/n | n/n | n | Y |
| 6 | CRT4h (coded) | 301 (2.4%) | 76>74 (+2%) | 119>119 (+0%) | 85>79 (+7%) | 262>252 (+4%) | 175>174 (+0%) | -530>-512 | -376>-342 | +0.7 (2.0) / -0.1 (2.0) / -2.6 (8.0) / +0.6 (1.2) / +0.0 (2.7) | +0.9 / +1.5 / -0.1 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/Y/Y | Y/Y | n | Y |
| 7 | OTE705 (coded) | 69 (0.6%) | 66>74 (-12%) | 126>119 (+5%) | 84>79 (+6%) | 272>252 (+7%) | 162>174 (-7%) | -526>-512 | -335>-342 | -0.6 (1.1) / -0.2 (0.7) / +0.4 (1.4) / +0.7 (0.8) / -0.3 (0.8) | -1.1 / +1.2 / -0.3 | 0.836/0.782/0.891 ; 0.442/0.366/0.436 ; 0.830/0.911/0.802 (n 164/100/100) | no | n/n/n | n/n | n | n |
| 8 | OTE79 (coded) | 21 (0.2%) | 73>74 (-1%) | 118>119 (-1%) | 78>79 (-1%) | 250>252 (-1%) | 171>174 (-1%) | -534>-512 | -340>-342 | +0.0 (0.8) / -0.3 (1.2) / -2.2 (5.4) / +1.3 (3.7) / -0.1 (0.9) | -0.4 / +1.9 / -0.1 | 0.465/0.495/0.584 ; 0.584/0.554/0.574 ; 0.564/0.525/0.475 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 9 | OTE62act (coded) | 121 (1.0%) | 78>71 (+9%) | 87>124 (-42%) | 80>79 (+0%) | 243>265 (-9%) | 167>160 (+5%) | -509>-509 | -337>-329 | +2.9 (8.4) / +0.0 (6.2) / +0.3 (1.0) / +0.2 (1.9) / +0.2 (0.6) | +2.8 / +0.3 / +0.2 | 0.139/0.099/0.099 ; 0.752/0.812/0.703 ; 0.228/0.257/0.337 (n 100/100/100) | no | Y/n/Y | Y/Y | n | n |
| 10 | KCup4h (coded) | 78 (0.6%) | 79>74 (+7%) | 121>119 (+1%) | 79>79 (+0%) | 235>252 (-7%) | 178>174 (+3%) | -496>-512 | -345>-342 | +0.4 (0.6) / -0.2 (1.3) / -1.8 (6.5) / -0.7 (1.4) / +0.1 (0.6) | -3.5 / -1.7 / +1.5 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 11 | OTE62b73 (action) | 20 (0.2%) | 78>74 (+6%) | 87>119 (-37%) | 80>79 (+1%) | 243>252 (-4%) | 167>174 (-4%) | -509>-512 | -337>-342 | +3.8 (9.2) / +1.2 (6.7) / +0.2 (0.6) / +0.2 (1.7) / -0.1 (0.7) | +0.1 / -1.4 / +0.7 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | n/n/Y | Y/Y | n | n |
| 12 | LVN1_1hs (UNCODED) | -9 (-0.1%) | 74>75 (-2%) | 119>118 (+1%) | 79>77 (+2%) | 252>257 (-2%) | 174>192 (-10%) | -512>-494 | -342>-344 | -0.3 (2.2) / +0.2 (1.2) / +0.6 (1.6) / +0.2 (1.0) / -0.4 (0.7) | -0.3 / +0.1 / -0.3 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |

### One-at-a-time (zone off -> line alone), V13eh
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE62b73 (action) | -51 (-0.4%) | 72>61 (+16%) | 118>131 (-11%) | 95>93 (+2%) | 329>264 (+20%) | 145>121 (+16%) | -608>-603 | -386>-383 | +4.4 (9.1) / +2.0 (6.8) / +1.4 (2.8) / +1.1 (2.7) / +0.3 (1.0) | +4.0 / +1.8 / +0.1 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | Y/Y/Y | Y/Y | n | n |
| 2 | CRT4h (coded) | 247 (1.9%) | 72>65 (+10%) | 118>115 (+3%) | 95>92 (+3%) | 329>303 (+8%) | 145>121 (+16%) | -608>-561 | -386>-365 | +0.2 (1.1) / +0.3 (0.9) / -0.1 (1.6) / +0.6 (2.4) / -0.3 (4.0) | +0.2 / +1.7 / -0.9 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/Y/Y | Y/Y | n | Y |
| 3 | PDmid (coded) | 119 (0.9%) | 72>73 (-1%) | 118>113 (+4%) | 95>91 (+5%) | 329>311 (+5%) | 145>153 (-6%) | -608>-579 | -386>-378 | -1.7 (3.9) / -1.1 (2.1) / +0.2 (1.2) / +0.1 (1.2) / -0.4 (1.7) | -0.5 / +0.8 / -1.3 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 4 | VAH15s (UNCODED) | 33 (0.3%) | 72>76 (-5%) | 118>117 (+2%) | 95>93 (+2%) | 329>336 (-2%) | 145>131 (+10%) | -608>-594 | -386>-381 | -0.6 (0.9) / -1.3 (2.4) / -0.3 (1.4) / -0.3 (1.2) / +0.3 (0.7) | -0.9 / +1.4 / +0.1 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 5 | HVN0_1hs (UNCODED) | 230 (1.8%) | 72>72 (+1%) | 118>88 (+26%) | 95>84 (+12%) | 329>302 (+8%) | 145>172 (-19%) | -608>-562 | -386>-382 | -0.8 (1.9) / +0.2 (1.6) / +2.3 (5.0) / +0.7 (2.3) / -0.4 (2.5) | +0.4 / +2.3 / -0.4 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 6 | KCup4h (coded) | 81 (0.6%) | 72>72 (+0%) | 118>117 (+1%) | 95>94 (+2%) | 329>299 (+9%) | 145>178 (-23%) | -608>-605 | -386>-383 | +0.4 (1.0) / +0.4 (0.6) / +0.7 (1.1) / +0.1 (1.8) / -1.6 (3.5) | +0.4 / +0.1 / -1.6 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/Y/Y | Y/Y | n | n |
| 7 | OTE62act (coded) | 151 (1.2%) | 72>67 (+7%) | 118>114 (+3%) | 95>92 (+3%) | 329>328 (+0%) | 145>170 (-18%) | -608>-554 | -386>-377 | +3.2 (8.3) / +1.8 (4.4) / +0.7 (0.9) / +0.7 (3.2) / -1.0 (2.7) | +3.2 / +1.4 / -1.2 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/Y/Y | Y/Y | n | n |
| 8 | OTE705 (coded) | 198 (1.6%) | 72>86 (-20%) | 118>109 (+8%) | 95>89 (+7%) | 329>343 (-4%) | 145>146 (-1%) | -608>-580 | -386>-386 | -0.5 (1.2) / -0.0 (0.8) / +0.7 (1.6) / +0.5 (1.4) / -1.2 (3.7) | -0.6 / +2.2 / -1.3 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | camH3 (coded) | 198 (1.6%) | 72>72 (+1%) | 118>94 (+20%) | 95>94 (+1%) | 329>281 (+15%) | 145>224 (-55%) | -608>-573 | -386>-396 | -0.1 (0.9) / +0.4 (1.6) / +2.4 (6.1) / +0.2 (1.8) / -2.3 (4.0) | -0.3 / +0.9 / -1.5 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 10 | OTE79 (coded) | 181 (1.4%) | 72>74 (-3%) | 118>118 (+0%) | 95>95 (+0%) | 329>369 (-12%) | 145>150 (-4%) | -608>-590 | -386>-393 | -0.2 (0.8) / +0.3 (0.7) / +0.2 (1.1) / +0.4 (4.3) / -1.5 (3.7) | -3.2 / +1.5 / -0.3 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 11 | LVN1_1hs (UNCODED) | 51 (0.4%) | 72>75 (-4%) | 118>121 (-2%) | 95>98 (-3%) | 329>376 (-14%) | 145>145 (-0%) | -608>-616 | -386>-397 | -0.2 (2.2) / +0.2 (1.2) / +0.3 (1.4) / -0.5 (1.8) / -0.2 (0.9) | -1.6 / +0.4 / -0.9 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 12 | kijun1h (coded) | 4 (0.0%) | 72>75 (-4%) | 118>117 (+1%) | 95>94 (+2%) | 329>373 (-13%) | 145>202 (-40%) | -608>-589 | -386>-383 | -0.0 (1.3) / +0.1 (0.8) / +0.0 (1.7) / -0.1 (2.4) / -1.6 (3.0) | +0.2 / +2.4 / -1.6 | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |

### View windows
| line | L1M cut (n 5 wk) | L2M cut (n 9) | L3M cut (n 13) | mean d L1M / L2M / L3M $k/wk |
|---|---|---|---|---|
| PDmid | +0% (16>16) | +0% (27>27) | +0% (40>40) | +0.0 / +0.0 / -0.1 |
| HVN0_1hs | +0% (16>16) | +1% (27>27) | +2% (40>39) | -1.7 / -1.8 / -1.2 |
| kijun1h | +7% (18>16) | +12% (31>27) | -7% (37>40) | +0.4 / +1.1 / +0.8 |
| camH3 | +0% (16>16) | +4% (28>27) | +9% (44>40) | -0.1 / -0.1 / +0.1 |
| VAH15s | +0% (16>16) | +12% (27>24) | -7% (40>43) | +0.2 / +0.4 / -0.2 |
| CRT4h | +0% (16>16) | +2% (28>27) | +19% (49>40) | +0.0 / +0.2 / +0.2 |
| OTE705 | +0% (16>16) | -2% (26>27) | -7% (37>40) | +0.0 / -0.0 / -0.2 |
| OTE79 | +0% (16>16) | +0% (27>27) | +1% (40>40) | -0.2 / -0.5 / -0.4 |
| OTE62act | +20% (33>26) | +16% (41>34) | +4% (41>39) | +14.4 / +8.3 / +5.7 |
| KCup4h | +0% (16>16) | +16% (32>27) | +11% (45>40) | +0.0 / +0.6 / +0.4 |
| OTE62b73 | +50% (33>16) | +34% (41>27) | +3% (41>40) | +18.4 / +10.0 / +6.9 |
| LVN1_1hs | -2% (16>17) | +3% (27>26) | -0% (40>40) | -3.8 / -2.0 / -1.6 |

### Episode-proofing (named trough week, leave-month-out, bootstrap P, ONE-WEEK flag), V13eh
| line | L6M: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | HOLD: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | MID: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | PRE: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | X': cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag |
|---|---|---|---|---|---|
| PDmid | -2% / -2% (20260907) / -2%..-0% / 0.00 / no cut | -4% / -9% (20260323) / -9%..+3% / 0.22 / no cut | +3% / +6% (20260323) / -0%..+3% / 0.53 / no cut | +2% / +2% (20250414) / -0%..+4% / 0.68 / no cut | +22% / +22% (20240129) / +9%..+32% / 0.99 / holds |
| HVN0_1hs | +1% / +1% (20260907) / -1%..+3% / 0.56 / no cut | +1% / -0% (20260323) / -0%..+1% / 0.60 / no cut | +0% / +1% (20260323) / -0%..+0% / 0.52 / no cut | +15% / +16% (20250414) / -1%..+16% / 0.67 / holds | +5% / +9% (20240129) / -1%..+10% / 0.82 / no cut |
| kijun1h | -2% / -3% (20260824) / -8%..+1% / 0.32 / no cut | +1% / +4% (20260323) / +1%..+4% / 0.67 / no cut | +2% / +5% (20260323) / +2%..+9% / 0.87 / no cut | +7% / +8% (20250414) / -13%..+19% / 0.47 / no cut | +13% / +15% (20240129) / -0%..+20% / 0.74 / holds |
| camH3 | +4% / +3% (20260907) / -0%..+4% / 0.47 / no cut | +6% / +12% (20260323) / -0%..+12% / 0.69 / no cut | -0% / +21% (20260323) / -0%..+25% / 0.57 / no cut | +2% / +2% (20250414) / -9%..+6% / 0.57 / no cut | +15% / +16% (20240129) / -5%..+22% / 0.69 / holds |
| VAH15s | -2% / +1% (20260907) / -2%..+1% / 0.51 / no cut | +2% / +2% (20260323) / +0%..+3% / 0.56 / no cut | +0% / +3% (20260323) / +0%..+5% / 0.37 / no cut | +7% / +8% (20250414) / +3%..+8% / 0.81 / no cut | +3% / -5% (20240129) / -5%..+7% / 0.65 / no cut |
| CRT4h | +2% / +1% (20260907) / -2%..+2% / 0.57 / no cut | +0% / +2% (20260323) / +0%..+5% / 0.84 / no cut | +7% / +2% (20260323) / +5%..+7% / 0.61 / no cut | +4% / +4% (20250414) / -2%..+4% / 0.63 / no cut | +0% / -2% (20240129) / -16%..+22% / 0.51 / no cut |
| OTE705 | -12% / -12% (20260907) / -16%..-1% / 0.09 / no cut | +5% / +1% (20260323) / +1%..+7% / 0.63 / no cut | +6% / +11% (20260323) / +3%..+6% / 0.89 / no cut | +7% / +7% (20250414) / +4%..+9% / 0.92 / no cut | -7% / -12% (20240129) / -12%..-0% / 0.21 / no cut |
| OTE79 | -1% / -1% (20260907) / -1%..-0% / 0.31 / no cut | -1% / -1% (20260323) / -2%..-1% / 0.06 / no cut | -1% / -2% (20260323) / -1%..-1% / 0.00 / no cut | -1% / +7% (20250414) / -6%..+10% / 0.73 / no cut | -1% / -4% (20240129) / -9%..+7% / 0.42 / no cut |
| OTE62act | +9% / +8% (20260907) / -0%..+14% / 0.66 / no cut | -42% / -25% (20260323) / -45%..-1% / 0.41 / no cut | +0% / +3% (20260323) / +0%..+2% / 0.77 / no cut | -9% / -10% (20250414) / -17%..+3% / 0.46 / no cut | +5% / +6% (20240129) / -2%..+7% / 0.71 / no cut |
| KCup4h | +7% / +0% (20260907) / -0%..+7% / 0.45 / no cut | +1% / +0% (20260323) / -0%..+2% / 0.38 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.03 / no cut | -7% / -8% (20250414) / -10%..-1% / 0.20 / no cut | +3% / +0% (20240129) / -2%..+5% / 0.71 / no cut |
| OTE62b73 | +6% / +6% (20260907) / -0%..+23% / 0.76 / no cut | -37% / -22% (20260323) / -44%..+5% / 0.52 / no cut | +1% / +0% (20260323) / +1%..+1% / 0.99 / no cut | -4% / -4% (20250414) / -29%..+7% / 0.47 / no cut | -4% / -7% (20240129) / -8%..+1% / 0.31 / no cut |
| LVN1_1hs | -2% / -3% (20260907) / -3%..+6% / 0.56 / no cut | +1% / +0% (20260323) / -0%..+2% / 0.69 / no cut | +2% / -5% (20260323) / -0%..+2% / 0.66 / no cut | -2% / -2% (20250414) / -5%..-0% / 0.51 / no cut | -10% / -8% (20240129) / -17%..-3% / 0.06 / no cut |

### Comparison: ASSUMED v1.3 base, episode-proofing
| line | L6M: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | HOLD: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | MID: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | PRE: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | X': cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag |
|---|---|---|---|---|---|
| kijun1h | -1% / +0% (20260907) / -1%..+1% / 0.25 / no cut | -1% / +0% (20260907) / -1%..+5% / 0.40 / no cut | +5% / -11% (20260323) / -33%..+5% / 0.71 / no cut | +32% / +34% (20250428) / +8%..+36% / 0.73 / holds | +6% / +7% (20231120) / -2%..+10% / 0.74 / no cut |
| OTE62b73 | +13% / +5% (20260907) / -0%..+15% / 0.75 / holds | +13% / +5% (20260907) / +5%..+15% / 0.85 / holds | +1% / +25% (20260323) / +1%..+25% / 0.85 / no cut | +18% / +19% (20250428) / +0%..+18% / 0.78 / holds | +13% / +10% (20231218) / -5%..+20% / 0.66 / holds |
| camH3 | -0% / -1% (20260907) / -0%..-0% / 0.17 / no cut | -0% / -1% (20260907) / -2%..-0% / 0.13 / no cut | -2% / +1% (20260323) / -2%..+1% / 0.20 / no cut | +3% / -0% (20250428) / -41%..+4% / 0.23 / no cut | +10% / +11% (20231120) / -4%..+13% / 0.75 / holds |
| OTE79 | +7% / +0% (20260914) / -0%..+8% / 0.58 / no cut | +7% / +0% (20260914) / -5%..+8% / 0.38 / no cut | -5% / -1% (20260323) / -5%..-1% / 0.22 / no cut | +21% / +24% (20250428) / +7%..+23% / 0.88 / holds | -13% / -14% (20231120) / -25%..+2% / 0.23 / no cut |
| OTE62act | -0% / -1% (20260907) / -1%..+2% / 0.29 / no cut | -0% / -1% (20260907) / -1%..+27% / 0.65 / no cut | +31% / +4% (20260323) / +4%..+31% / 1.00 / ONE-WEEK | +4% / +3% (20250428) / -2%..+6% / 0.59 / no cut | +5% / +5% (20231218) / +2%..+6% / 0.83 / no cut |
| KCup4h | +1% / +0% (20260907) / -0%..+1% / 0.29 / no cut | +1% / +0% (20260907) / -0%..+1% / 0.22 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.00 / no cut | +12% / +12% (20250428) / +0%..+12% / 0.65 / holds | -7% / -7% (20231120) / -11%..+1% / 0.33 / no cut |
| OTE705 | -3% / -3% (20260907) / -7%..+0% / 0.26 / no cut | -3% / -3% (20260907) / -7%..+12% / 0.57 / no cut | +12% / +11% (20260323) / +0%..+12% / 0.92 / holds | +11% / +12% (20250428) / +3%..+13% / 0.81 / holds | -5% / -5% (20231120) / -8%..+0% / 0.23 / no cut |
| PDmid | -1% / -2% (20260907) / -1%..-0% / 0.00 / no cut | -1% / -2% (20260907) / -1%..-0% / 0.00 / no cut | -1% / +0% (20260323) / -1%..-0% / 0.00 / no cut | +1% / +1% (20250428) / -1%..+6% / 0.58 / no cut | -2% / +2% (20231120) / -11%..+4% / 0.48 / no cut |
| HVN0_1hs | +3% / +3% (20260907) / -0%..+4% / 0.80 / no cut | +3% / +3% (20260907) / -14%..+4% / 0.44 / no cut | -9% / -25% (20260323) / -25%..-9% / 0.03 / no cut | -14% / -17% (20250428) / -17%..+4% / 0.38 / no cut | +4% / +4% (20231120) / +0%..+6% / 0.70 / no cut |
| CRT4h | -4% / -5% (20260907) / -8%..+0% / 0.17 / no cut | -4% / -5% (20260907) / -8%..+1% / 0.31 / no cut | +1% / +1% (20260323) / +1%..+1% / 0.67 / no cut | -2% / -4% (20250428) / -11%..-2% / 0.24 / no cut | -3% / -1% (20231120) / -14%..+12% / 0.52 / no cut |
| VAH15s | -2% / +2% (20260907) / -2%..+2% / 0.67 / no cut | -2% / +2% (20260907) / -2%..+2% / 0.67 / no cut | +1% / +23% (20260323) / +1%..+50% / 0.75 / no cut | -18% / -19% (20250428) / -20%..-9% / 0.17 / no cut | -6% / -6% (20231120) / -8%..-2% / 0.00 / no cut |
| LVN1_1hs | -0% / -1% (20260907) / -0%..+5% / 0.69 / no cut | -0% / -1% (20260907) / -2%..+4% / 0.58 / no cut | -2% / +0% (20260323) / -2%..-0% / 0.33 / no cut | -1% / -0% (20250428) / -2%..+4% / 0.60 / no cut | -23% / -24% (20231120) / -30%..-2% / 0.03 / no cut |

### Comparison: ASSUMED v1.3 base line table
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | kijun1h (coded) | -95 (-0.8%) | 106>107 (-1%) | 106>107 (-1%) | 70>67 (+5%) | 283>192 (+32%) | 270>253 (+6%) | -497>-482 | -388>-371 | -3.3 (9.3) / -1.9 (4.8) / -0.8 (2.0) / +1.2 (3.0) / +0.4 (1.6) | ? / ? / ? | 0.564/0.653/0.634 ; 0.020/0.010/0.010 ; 0.228/0.317/0.178 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 2 | OTE62b73 (action) | -129 (-1.1%) | 123>107 (+13%) | 123>107 (+13%) | 68>67 (+1%) | 236>192 (+18%) | 290>253 (+13%) | -490>-482 | -367>-371 | +3.6 (8.5) / +3.1 (4.7) / +0.9 (2.3) / +0.2 (2.4) / +1.1 (4.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | Y/Y/Y | Y/Y | n | Y |
| 3 | camH3 (coded) | 87 (0.7%) | 107>107 (-0%) | 107>107 (-0%) | 66>67 (-2%) | 199>192 (+3%) | 283>253 (+10%) | -496>-482 | -377>-371 | -0.2 (0.7) / -0.5 (0.7) / -1.1 (1.9) / -1.8 (3.2) / +0.7 (2.5) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 4 | OTE79 (coded) | -83 (-0.7%) | 115>107 (+7%) | 115>107 (+7%) | 64>67 (-5%) | 245>192 (+21%) | 224>253 (-13%) | -495>-482 | -358>-371 | +5.1 (11.3) / +2.9 (5.9) / +0.3 (1.9) / +0.8 (1.2) / -0.6 (1.7) | ? / ? / ? | 0.257/0.139/0.228 ; 0.139/0.069/0.059 ; 0.891/0.941/0.921 (n 100/100/100) | no | n/Y/Y | Y/Y | n | n |
| 5 | OTE62act (coded) | -120 (-1.0%) | 123>123 (-0%) | 123>123 (-0%) | 68>46 (+31%) | 236>225 (+4%) | 290>277 (+5%) | -490>-491 | -367>-362 | +2.5 (8.3) / +3.1 (6.4) / +7.7 (20.7) / +0.0 (0.7) / +0.3 (0.7) | ? / ? / ? | 0.624/0.564/0.634 ; 0.267/0.178/0.248 ; 0.386/0.178/0.356 (n 100/100/100) | no | Y/n/Y | Y/Y | n | n |
| 6 | KCup4h (coded) | -4 (-0.0%) | 109>107 (+1%) | 109>107 (+1%) | 67>67 (+0%) | 219>192 (+12%) | 237>253 (-7%) | -496>-482 | -360>-371 | +0.0 (0.2) / -0.1 (0.4) / -0.0 (1.1) / -0.3 (2.2) / -0.3 (1.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/Y | Y/n | n | n |
| 7 | OTE705 (coded) | 98 (0.8%) | 104>107 (-3%) | 104>107 (-3%) | 76>67 (+12%) | 216>192 (+11%) | 241>253 (-5%) | -501>-482 | -366>-371 | -0.6 (1.4) / -0.1 (0.8) / +0.9 (1.5) / +0.3 (0.8) / -0.1 (0.8) | ? / ? / ? | 0.733/0.683/0.832 ; 0.198/0.149/0.158 ; 0.842/0.842/0.891 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 8 | PDmid (coded) | 53 (0.5%) | 106>107 (-1%) | 106>107 (-1%) | 67>67 (-1%) | 194>192 (+1%) | 249>253 (-2%) | -486>-482 | -384>-371 | -0.7 (1.3) / -0.8 (0.9) / -0.3 (0.7) / +0.1 (0.4) / -0.0 (1.3) | ? / ? / ? | 0.782/0.733/0.752 ; 0.317/0.277/0.347 ; 0.881/0.772/0.851 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 9 | HVN0_1hs (UNCODED) | 3 (0.0%) | 107>104 (+3%) | 107>104 (+3%) | 67>73 (-9%) | 192>219 (-14%) | 253>243 (+4%) | -482>-479 | -371>-361 | -0.5 (1.9) / -0.1 (1.4) / -1.1 (2.3) / -0.4 (1.3) / +0.1 (0.7) | ? / ? / ? | 0.317/0.297/0.228 ; 0.911/0.851/0.911 ; 0.307/0.307/0.327 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 10 | CRT4h (coded) | 227 (1.9%) | 103>107 (-4%) | 103>107 (-4%) | 68>67 (+1%) | 189>192 (-2%) | 247>253 (-3%) | -480>-482 | -380>-371 | -0.3 (1.4) / -0.2 (0.9) / -0.4 (2.0) / -0.3 (1.2) / -0.1 (2.7) | ? / ? / ? | 0.832/0.824/0.871 ; 0.356/0.319/0.419 ; 0.703/0.780/0.677 (n 100/90/30) | no | n/n/n | n/n | n | n |
| 11 | VAH15s (UNCODED) | -84 (-0.7%) | 107>110 (-2%) | 107>110 (-2%) | 67>66 (+1%) | 192>227 (-18%) | 253>268 (-6%) | -482>-495 | -371>-383 | -0.5 (0.9) / -0.3 (1.3) / +1.1 (3.9) / -0.8 (1.0) / -0.6 (0.7) | ? / ? / ? | 0.723/0.723/0.762 ; 0.812/0.921/0.881 ; 0.891/0.901/0.970 (n 100/100/100) | no | n/n/n | n/n | n | n |
| 12 | LVN1_1hs (UNCODED) | 159 (1.4%) | 107>108 (-0%) | 107>108 (-0%) | 67>69 (-2%) | 192>195 (-1%) | 253>312 (-23%) | -482>-469 | -371>-376 | -0.2 (1.5) / +0.0 (0.8) / +0.0 (0.7) / -0.0 (0.8) / -1.5 (4.0) | ? / ? / ? | 0.554/0.604/0.545 ; 0.465/0.426/0.426 ; 1.000/1.000/1.000 (n 100/100/100) | no | n/n/n | n/n | n | n |

## 3. Rankings (V13eh)
### Honest (selected on PRE+X', recent windows looked at once)
| honest # | line | S_PX = mean(cut PRE, cut X') | cut PRE | cut X' | PX gate | ONE recent look: cut L6M | HOLD | MID | L3M (view L1M) | mean d L6M (MDE) / HOLD / MID | label | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | PDmid | +0.117 | +2% | +22% | pass | -2% | -4% | +3% | +0% (+0%) | -1.0 (2.2) / -0.8 / -0.1 | no | n/n/n |
| 2 | camH3 | +0.083 | +2% | +15% | pass | +4% | +6% | -0% | +9% (+0%) | +0.0 (0.7) / -0.1 / +0.3 | no | n/n/Y |
| 3 | CRT4h | +0.021 | +4% | +0% | pass | +2% | +0% | +7% | +19% (+0%) | +0.7 (2.0) / -0.1 / -2.6 | no | n/Y/Y |
| - | kijun1h | +0.102 | +7% | +13% | fail: X' w20 worse | -2% | +1% | +2% | -7% (+7%) | +0.2 (1.1) / +0.0 / -0.3 | no | Y/Y/Y |
| - | HVN0_1hs | +0.098 | +15% | +5% | fail: PRE w20 worse | +1% | +1% | +0% | +2% (+0%) | -0.6 (1.9) / -0.2 / -0.2 | no | n/n/n |
| - | VAH15s | +0.049 | +7% | +3% | fail: X' w20 worse | -2% | +2% | +0% | -7% (+0%) | -0.4 (0.6) / -1.4 / -3.5 | no | n/n/n |
| - | OTE705 | +0.002 | +7% | -7% | fail: X' no cut, X' w20 worse | -12% | +5% | +6% | -7% (+0%) | -0.6 (1.1) / -0.2 / +0.4 | no | n/n/n |
| - | OTE79 | -0.012 | -1% | -1% | fail: PRE no cut, X' no cut, X' w20 worse | -1% | -1% | -1% | +1% (+0%) | +0.0 (0.8) / -0.3 / -2.2 | no | n/n/n |
| - | OTE62act | -0.022 | -9% | +5% | fail: PRE no cut, PRE w20 worse | +9% | -42% | +0% | +4% (+20%) | +2.9 (8.4) / +0.0 / +0.3 | no | Y/n/Y |
| - | KCup4h | -0.024 | -7% | +3% | fail: PRE no cut, PRE w20 worse | +7% | +1% | +0% | +11% (+0%) | +0.4 (0.6) / -0.2 / -1.8 | no | n/n/Y |
| - | OTE62b73 | -0.037 | -4% | -4% | fail: PRE no cut, X' no cut, PRE w20 worse, X' w20 worse | +6% | -37% | +1% | +3% (+50%) | +3.8 (9.2) / +1.2 / +0.2 | n/a (action line, no placebo) | n/n/Y |
| - | LVN1_1hs | -0.060 | -2% | -10% | fail: PRE no cut, X' no cut, X' w20 worse, X' mean<-0.5MDE | -2% | +1% | +2% | -0% (-2%) | -0.3 (2.2) / +0.2 / +0.6 | no | n/n/n |
### Post-hoc (L6M cut)
| post-hoc # | line | cut L6M | Calmar L6M before>after | cut HOLD | cut MID | cut L3M | PRE: cut, mean d (MDE) | X': cut, mean d (MDE) | S/T/N | TOL-B/nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE62act | +9.1% | 0.24 > 0.30 | -42.1% | +0.3% | +4.4% | -8.9%, +0.2 (1.9) | +4.5%, +0.2 (0.6) | Y/n/Y | Y/Y | no |
| 2 | KCup4h | +6.5% | 0.28 > 0.30 | +1.2% | +0.0% | +11.5% | -7.4%, -0.7 (1.4) | +2.6%, +0.1 (0.6) | n/n/Y | Y/n | no |
| 3 | OTE62b73 | +5.6% | 0.24 > 0.30 | -36.8% | +1.4% | +2.7% | -3.7%, +0.2 (1.7) | -3.7%, -0.1 (0.7) | n/n/Y | Y/Y | n/a (action line, no placebo) |
| 4 | camH3 | +3.7% | 0.29 > 0.30 | +5.6% | -0.4% | +8.6% | +2.1%, -1.7 (4.7) | +14.6%, +0.7 (2.4) | n/n/Y | Y/n | no |
| 5 | CRT4h | +2.3% | 0.29 > 0.30 | +0.1% | +7.3% | +19.2% | +3.7%, +0.6 (1.2) | +0.5%, +0.0 (2.7) | n/Y/Y | Y/Y | no |
| 6 | HVN0_1hs | +1.4% | 0.30 > 0.30 | +0.8% | +0.3% | +2.0% | +14.7%, -0.1 (2.0) | +5.0%, +0.2 (0.7) | n/n/n | n/n | no |
| 7 | OTE79 | -1.3% | 0.31 > 0.30 | -1.2% | -1.0% | +0.8% | -1.0%, +1.3 (3.7) | -1.5%, -0.1 (0.9) | n/n/n | n/n | no |
| 8 | LVN1_1hs | -1.7% | 0.30 > 0.29 | +1.2% | +1.8% | -0.2% | -1.8%, +0.2 (1.0) | -10.3%, -0.4 (0.7) | n/n/n | n/n | no |
| 9 | VAH15s | -2.1% | 0.30 > 0.29 | +2.1% | +0.4% | -7.1% | +7.0%, -0.3 (0.9) | +2.9%, +0.3 (1.8) | n/n/n | n/n | no |
| 10 | PDmid | -2.2% | 0.32 > 0.30 | -4.3% | +3.2% | +0.0% | +1.9%, +0.2 (0.7) | +21.5%, +1.1 (2.1) | n/n/n | n/n | no |
| 11 | kijun1h | -2.3% | 0.31 > 0.30 | +0.7% | +2.3% | -7.3% | +7.0%, +0.7 (2.6) | +13.3%, +0.6 (1.9) | Y/Y/Y | Y/Y | no |
| 12 | OTE705 | -12.2% | 0.35 > 0.30 | +5.1% | +6.2% | -6.9% | +7.3%, +0.7 (0.8) | -7.0%, -0.3 (0.8) | n/n/n | n/n | no |

### Best-of-N chance null (V13eh, N=? lines, S_PX)
not enough draws yet

## 4. Lines that add nothing
| line | rows newly acted on (all 187 wk) | pre-declared null rule | cuts (dDD% L6M / PRE / X') | mean d / MDE (L6M, PRE, X') | weakness |
|---|---|---|---|---|---|
| LVN1_1hs | 1008 | not null | -1.7% / -1.8% / -10.3% | -0.14 / +0.14 / -0.60 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| OTE62b73 | 0 | not null | +5.6% / -3.7% / -3.7% | +0.42 / +0.10 / -0.20 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| KCup4h | 970 | not null | +6.5% / -7.4% / +2.6% | +0.57 / -0.49 / +0.17 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| OTE62act | 1414 | not null | +9.1% / -8.9% / +4.5% | +0.34 / +0.13 / +0.29 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| OTE79 | 1664 | not null | -1.3% / -1.0% / -1.5% | +0.01 / +0.36 / -0.06 | cuts in 0 of 4 (L6M, HOLD, PRE, X') |
| OTE705 | 1458 | not null | -12.2% / +7.3% / -7.0% | -0.52 / +0.82 / -0.31 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| CRT4h | 1076 | not null | +2.3% / +3.7% / +0.5% | +0.35 / +0.52 / +0.00 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| VAH15s | 1321 | not null | -2.1% / +7.0% / +2.9% | -0.67 / -0.29 / +0.18 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| camH3 | 1632 | not null | +3.7% / +2.1% / +14.6% | +0.01 / -0.37 / +0.28 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| kijun1h | 1443 | not null | -2.3% / +7.0% / +13.3% | +0.17 / +0.25 / +0.31 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| HVN0_1hs | 1207 | not null | +1.4% / +14.7% / +5.0% | -0.29 / -0.03 / +0.29 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| PDmid | 414 | not null | -2.2% / +1.9% / +21.5% | -0.44 / +0.33 / +0.51 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |

## 5. Definition sensitivity (V13eh)
### Whole layer
| whole layer (7 lines) at D | L6M maxDD cut | HOLD maxDD cut | MID maxDD cut | PRE maxDD cut | X' maxDD cut |
|---|---|---|---|---|---|
| D = 10 | +5% | -5% | +3% | +14% | -77% |
| D = 15 | +9% | -0% | +4% | +32% | -1% |
| D = 20 | -2% | -1% | +17% | +23% | -20% |
| D = 25 | -2% | +16% | +35% | +8% | -31% |
| D = 30 | -16% | +13% | +35% | +15% | -63% |
| D = 40 | +3% | +28% | +38% | +22% | -28% |
| freshness any (fresh or touched), D20 | -17% | +27% | +25% | +38% | +1% |
### Per line (others at D20)
| line | window | marginal-in-set maxDD cut at D = 10 / 15 / 20 / 25 / 30 / 40 (D20 = shipped; D+-25% = 15/25, +-50% = 10/30) | verdict |
|---|---|---|---|
| kijun1h | L6M | +0% / -1% / -2% / -2% / -6% / -8% | no cut at any D |
| kijun1h | PRE | +19% / +17% / +7% / +8% / +11% / +11% | holds at 4 of 6 D (cut >= 10%) |
| kijun1h | X' | +13% / +11% / +13% / +20% / +22% / +19% | holds at 6 of 6 D (cut >= 10%) |
| PDmid | L6M | -5% / -2% / -2% / -1% / -6% / -0% | no cut at any D |
| PDmid | PRE | +11% / +11% / +2% / +2% / +6% / +2% | holds at 2 of 6 D (cut >= 10%) |
| PDmid | X' | +1% / +22% / +22% / +27% / +27% / +28% | holds at 5 of 6 D (cut >= 10%) |
| CRT4h | L6M | -0% / +5% / +2% / +3% / +1% / +3% | no cut at any D |
| CRT4h | PRE | -0% / +2% / +4% / +13% / +15% / +7% | holds at 2 of 6 D (cut >= 10%) |
| CRT4h | X' | +13% / +21% / +0% / +2% / +2% / +7% | holds at 2 of 6 D (cut >= 10%) |
| KCup4h | L6M | +7% / +7% / +7% / +5% / +2% / +2% | no cut at any D |
| KCup4h | PRE | -8% / -7% / -7% / -7% / +17% / +14% | holds at 2 of 6 D (cut >= 10%) |
| KCup4h | X' | -2% / +3% / +3% / -1% / -6% / -7% | no cut at any D |
| camH3 | L6M | +5% / +6% / +4% / +7% / +4% / +8% | no cut at any D |
| camH3 | PRE | -6% / -8% / +2% / -10% / -4% / +5% | no cut at any D |
| camH3 | X' | +1% / +0% / +15% / +4% / -21% / -21% | FRAGILE (cut >= 10% at one D only) |
| OTE705 | L6M | -7% / -7% / -12% / -15% / -19% / -4% | no cut at any D |
| OTE705 | PRE | +2% / +12% / +7% / +5% / +7% / +2% | FRAGILE (cut >= 10% at one D only) |
| OTE705 | X' | -5% / -4% / -7% / -8% / -8% / -7% | no cut at any D |
| OTE79 | L6M | -4% / -1% / -1% / -1% / -1% / -5% | no cut at any D |
| OTE79 | PRE | -9% / -3% / -1% / -9% / -9% / -10% | no cut at any D |
| OTE79 | X' | -4% / -2% / -1% / -2% / -2% / -7% | no cut at any D |
| VAH15s | L6M | -2% / -4% / -2% / -1% / -7% / -0% | no cut at any D |
| VAH15s | PRE | +7% / +8% / +7% / +7% / +17% / +15% | holds at 2 of 6 D (cut >= 10%) |
| VAH15s | X' | +10% / +7% / +3% / +2% / +1% / +1% | no cut at any D |
| LVN1_1hs | L6M | +0% / -3% / -2% / -0% / +3% / -34% | no cut at any D |
| LVN1_1hs | PRE | -2% / -2% / -2% / +4% / +4% / +4% | no cut at any D |
| LVN1_1hs | X' | -2% / -10% / -10% / -10% / -4% / -3% | no cut at any D |
| HVN0_1hs | L6M | +0% / +1% / +1% / +2% / -1% / -13% | no cut at any D |
| HVN0_1hs | PRE | +12% / +15% / +15% / +4% / +3% / -25% | holds at 3 of 6 D (cut >= 10%) |
| HVN0_1hs | X' | +2% / +2% / +5% / +7% / +10% / +12% | holds at 2 of 6 D (cut >= 10%) |
Not done: swing strength 2/3 and profile bin 1/2 pt (need the POI streams rebuilt), anchor shifts, 1-s/3-s entry delay (the engine has no entry-delay parameter for B73/half).

## 6. Subset landscape (V13eh, 2^10 subsets, OTE-62 B73 kept)
landscape not yet run (0 subsets)

## 7. Per book and per session, marginal-in-set (V13eh; dDD $k / dWorst20 (PRE, X') / d mean)

### by book, L6M
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| PDmid | -1 / -0.5 | +0 / -0.4 | +0 / -0.1 | +0 / -0.1 | +0 / +0.0 | -1 / +0.1 |
| HVN0_1hs | -1 / -0.1 | +0 / -0.5 | -4 / +0.3 | +0 / -0.0 | +0 / -0.1 | -6 / -0.1 |
| kijun1h | +0 / -0.0 | +0 / +0.3 | +1 / -0.1 | -2 / +0.0 | +1 / -0.1 | +0 / +0.1 |
| camH3 | +1 / -0.1 | +0 / +0.2 | +0 / -0.1 | +0 / -0.0 | +0 / +0.0 | +1 / -0.0 |
| VAH15s | -1 / -0.1 | +1 / -0.1 | +0 / -0.0 | -2 / +0.0 | +1 / -0.0 | +5 / -0.2 |
| CRT4h | +8 / -0.2 | -5 / +1.0 | +1 / -0.2 | -1 / +0.2 | +3 / -0.1 | +0 / +0.0 |
| OTE705 | -1 / -0.1 | +2 / -0.5 | +0 / -0.0 | +0 / +0.0 | +0 / +0.0 | +0 / -0.1 |
| OTE79 | +0 / +0.1 | +0 / -0.1 | -2 / +0.2 | +0 / -0.3 | +1 / -0.0 | +1 / +0.0 |
| OTE62act | -1 / +0.7 | +8 / +0.8 | -1 / -0.4 | -6 / +1.4 | +0 / +0.1 | -6 / +0.2 |
| KCup4h | +0 / +0.1 | +0 / +0.2 | +0 / +0.0 | +0 / -0.1 | +0 / +0.1 | +0 / +0.0 |
| OTE62b73 | -0 / +1.0 | -6 / +1.5 | +4 / -0.6 | -12 / +1.5 | +4 / +0.2 | +0 / +0.2 |
| LVN1_1hs | +0 / +0.1 | +0 / -0.5 | +0 / +0.1 | +0 / +0.0 | -1 / +0.1 | +0 / +0.0 |

### by session, L6M
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| PDmid | +0 / -0.5 | +0 / -0.0 | -1 / -0.1 | +9 / -0.3 |
| HVN0_1hs | -3 / -0.3 | -1 / -0.2 | -0 / -0.0 | -2 / -0.0 |
| kijun1h | +0 / +0.1 | +4 / -0.1 | -2 / +0.1 | +0 / +0.0 |
| camH3 | +0 / -0.0 | +0 / -0.0 | -0 / +0.1 | +0 / +0.0 |
| VAH15s | +1 / -0.1 | +5 / -0.3 | -1 / +0.0 | -0 / +0.0 |
| CRT4h | +0 / +0.3 | -4 / +0.2 | -3 / +0.2 | +0 / +0.0 |
| OTE705 | -0 / -0.5 | +1 / -0.2 | -1 / +0.1 | -1 / +0.0 |
| OTE79 | +0 / -0.2 | -2 / +0.2 | +0 / -0.0 | +0 / +0.0 |
| OTE62act | -7 / +2.4 | +3 / +0.4 | -1 / +0.0 | -2 / +0.1 |
| KCup4h | +0 / +0.2 | -1 / +0.1 | +0 / +0.0 | +0 / +0.0 |
| OTE62b73 | -0 / +3.6 | +2 / -0.2 | +0 / +0.2 | -0 / +0.2 |
| LVN1_1hs | +0 / -0.2 | -1 / -0.2 | +0 / +0.1 | -1 / +0.0 |

### by book, HOLD
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| PDmid | +2 / -0.3 | -6 / -0.2 | +0 / -0.2 | +0 / +0.1 | +3 / -0.1 | -1 / -0.1 |
| HVN0_1hs | -2 / +0.1 | +7 / -0.4 | +0 / +0.2 | +0 / -0.0 | +4 / -0.1 | -4 / +0.0 |
| kijun1h | +0 / +0.0 | -4 / -0.1 | -1 / +0.0 | -2 / -0.1 | -4 / +0.1 | +0 / +0.1 |
| camH3 | +2 / -0.2 | -15 / +0.1 | +0 / -0.0 | +0 / -0.0 | -5 / +0.1 | +1 / -0.1 |
| VAH15s | -1 / -0.2 | -1 / -0.3 | +1 / -0.2 | -2 / -0.2 | +14 / -0.3 | +5 / -0.2 |
| CRT4h | -0 / -0.3 | -1 / +0.5 | -1 / -0.2 | -1 / +0.1 | +5 / -0.2 | +0 / -0.1 |
| OTE705 | -6 / +0.1 | -2 / -0.2 | +0 / -0.0 | +0 / -0.0 | +0 / +0.0 | +0 / -0.0 |
| OTE79 | +0 / -0.0 | +0 / -0.3 | -4 / -0.0 | +0 / -0.1 | +0 / +0.2 | +1 / -0.1 |
| OTE62act | -3 / +0.3 | +25 / -0.9 | +1 / -0.2 | -6 / +0.5 | -3 / +0.1 | -4 / +0.2 |
| KCup4h | -1 / +0.0 | +0 / -0.1 | +0 / -0.2 | +0 / +0.1 | +0 / +0.1 | +0 / -0.0 |
| OTE62b73 | +1 / +0.4 | +17 / +0.1 | +0 / -0.2 | -12 / +0.6 | -4 / +0.2 | +0 / +0.2 |
| LVN1_1hs | +0 / +0.0 | +0 / -0.3 | -0 / +0.2 | +0 / +0.2 | +0 / +0.0 | +0 / +0.0 |

### by session, HOLD
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| PDmid | -3 / -0.2 | +0 / -0.3 | -4 / -0.1 | +9 / -0.2 |
| HVN0_1hs | +1 / +0.0 | +6 / -0.2 | -0 / -0.0 | -1 / -0.0 |
| kijun1h | +2 / +0.2 | +3 / -0.1 | +0 / +0.0 | +3 / -0.1 |
| camH3 | +0 / -0.2 | +3 / -0.2 | -15 / +0.3 | -2 / +0.0 |
| VAH15s | -1 / -0.8 | +5 / -0.3 | -0 / -0.2 | +1 / -0.0 |
| CRT4h | -5 / -0.5 | -3 / -0.1 | -1 / +0.5 | -1 / +0.0 |
| OTE705 | -4 / -0.1 | -1 / -0.1 | +0 / +0.0 | -1 / +0.0 |
| OTE79 | +5 / -0.8 | +0 / +0.1 | -1 / +0.4 | -1 / +0.0 |
| OTE62act | -1 / +0.1 | -3 / +0.3 | +22 / -0.4 | -1 / +0.0 |
| KCup4h | +0 / -0.4 | -4 / +0.1 | +0 / +0.0 | -3 / +0.1 |
| OTE62b73 | -1 / +1.3 | -2 / +0.1 | +20 / -0.3 | -1 / +0.1 |
| LVN1_1hs | -2 / +0.1 | -1 / -0.0 | +0 / +0.1 | -0 / +0.0 |

### by book, MID
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| PDmid | +0 / +0.0 | +0 / +0.0 | +0 / +0.0 | -3 / +0.2 | +0 / +0.0 | +0 / -0.3 |
| HVN0_1hs | -0 / +0.6 | +7 / -0.7 | +0 / -0.2 | +1 / -0.0 | +0 / -0.2 | +0 / +0.3 |
| kijun1h | +0 / +0.1 | -4 / -1.1 | -1 / +0.4 | +2 / -0.6 | +0 / +0.7 | +0 / +0.2 |
| camH3 | +0 / -0.4 | -15 / +0.5 | +0 / +0.2 | +0 / -0.1 | +0 / +0.3 | +1 / -0.3 |
| VAH15s | -0 / -0.4 | -1 / -0.1 | +1 / -0.9 | +0 / -0.6 | +1 / -1.2 | +0 / -0.3 |
| CRT4h | -0 / -0.5 | -1 / -1.0 | -1 / -0.2 | +2 / +0.2 | -1 / -0.5 | +0 / -0.6 |
| OTE705 | -6 / +0.6 | -1 / -0.0 | +0 / +0.0 | +0 / -0.1 | +0 / +0.0 | +0 / +0.0 |
| OTE79 | +0 / -0.4 | +0 / -1.6 | -4 / -0.2 | +0 / +0.3 | +0 / -0.0 | +0 / -0.3 |
| OTE62act | -3 / +0.6 | +3 / -0.3 | +1 / -0.1 | +0 / +0.1 | +0 / -0.2 | +0 / +0.2 |
| KCup4h | +0 / -0.2 | +0 / -0.9 | +0 / -1.0 | +0 / +0.4 | +0 / +0.0 | +0 / -0.2 |
| OTE62b73 | -1 / -0.1 | -5 / +0.3 | +0 / +0.2 | -1 / -0.0 | +1 / -0.1 | +0 / +0.0 |
| LVN1_1hs | +0 / +0.0 | +0 / -0.0 | -2 / +0.2 | +0 / +0.5 | +0 / +0.0 | +0 / +0.0 |

### by session, MID
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| PDmid | -3 / +0.0 | +0 / +0.0 | +0 / -0.1 | +0 / +0.0 |
| HVN0_1hs | +1 / +0.3 | +6 / -0.5 | -0 / +0.0 | +0 / +0.0 |
| kijun1h | +2 / +0.5 | +3 / -0.3 | +0 / -0.1 | +3 / -0.3 |
| camH3 | +0 / -0.4 | +3 / -0.5 | -15 / +1.3 | +0 / +0.0 |
| VAH15s | -1 / -3.2 | +5 / -0.2 | +0 / -0.0 | -3 / -0.0 |
| CRT4h | -5 / -2.3 | -3 / -0.3 | -1 / -0.1 | +0 / +0.1 |
| OTE705 | -4 / +0.3 | -1 / +0.2 | +0 / +0.0 | -0 / +0.0 |
| OTE79 | +6 / -2.6 | +0 / +0.3 | +0 / -0.1 | +0 / +0.1 |
| OTE62act | -1 / -0.0 | -0 / +0.1 | +3 / -0.0 | -2 / +0.2 |
| KCup4h | +0 / -2.2 | -4 / +0.1 | +0 / -0.1 | -2 / +0.3 |
| OTE62b73 | -1 / +0.1 | +1 / -0.0 | +0 / -0.1 | -2 / +0.2 |
| LVN1_1hs | -2 / +0.3 | -1 / -0.0 | +0 / +0.3 | +0 / +0.0 |

### by book, PRE
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| PDmid | +1 / +0 / -0.0 | +3 / +0 / +0.1 | -16 / +11 / +0.2 | +4 / +0 / -0.1 | +0 / +1 / +0.0 | +0 / +1 / +0.0 |
| HVN0_1hs | -5 / +2 / -0.0 | -19 / +11 / -0.3 | -4 / +11 / +0.1 | -6 / +3 / +0.1 | +0 / -1 / -0.0 | -2 / +4 / +0.1 |
| kijun1h | -6 / -14 / -0.1 | -21 / +2 / +0.7 | +1 / +1 / -0.0 | +3 / +1 / -0.1 | +0 / +1 / +0.2 | +0 / +1 / +0.0 |
| camH3 | +0 / -5 / -0.3 | -20 / +22 / -0.8 | +7 / +1 / -0.1 | +2 / -1 / -0.3 | -1 / +2 / -0.0 | -1 / +1 / -0.2 |
| VAH15s | -2 / +2 / -0.0 | -14 / +13 / -0.2 | +0 / -0 / -0.0 | +1 / +1 / -0.0 | +0 / +1 / +0.0 | +0 / +0 / -0.0 |
| CRT4h | -1 / +0 / -0.0 | -2 / +14 / +0.5 | -12 / -1 / +0.1 | -8 / +3 / +0.1 | +0 / +5 / +0.1 | +0 / +0 / -0.1 |
| OTE705 | -0 / +7 / +0.1 | +12 / +14 / +0.2 | -3 / +14 / +0.0 | -20 / +9 / +0.3 | -5 / +1 / +0.0 | +0 / +5 / +0.1 |
| OTE79 | +15 / +3 / +0.1 | -18 / +21 / +0.7 | -25 / +16 / +0.3 | -31 / +7 / +0.4 | +0 / -1 / -0.1 | -1 / -3 / -0.1 |
| OTE62act | -5 / +10 / +0.1 | +1 / -3 / +0.3 | -0 / -1 / -0.0 | +4 / +3 / -0.0 | +0 / +1 / -0.1 | +0 / -0 / -0.0 |
| KCup4h | +6 / -6 / -0.1 | +20 / -9 / -0.5 | +1 / -5 / -0.0 | +1 / -1 / -0.0 | +0 / -2 / +0.0 | -1 / +3 / -0.0 |
| OTE62b73 | +1 / +2 / +0.0 | +2 / -9 / +0.4 | +10 / -7 / -0.2 | +2 / +3 / -0.0 | +0 / +0 / -0.0 | +0 / +2 / -0.1 |
| LVN1_1hs | -0 / +0 / +0.0 | -4 / +21 / +0.2 | +5 / +7 / -0.0 | +5 / -4 / -0.1 | +0 / +1 / +0.0 | +0 / +1 / -0.0 |

### by session, PRE
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| PDmid | -5 / +7 / -0.0 | -3 / +8 / +0.2 | +0 / +2 / +0.1 | +0 / +0 / +0.0 |
| HVN0_1hs | -11 / -8 / +0.3 | +39 / -34 / -0.6 | +0 / +0 / +0.2 | +0 / +0 / -0.0 |
| kijun1h | -19 / +28 / +0.7 | -68 / +14 / +0.8 | +8 / -18 / -0.7 | +6 / -7 / -0.1 |
| camH3 | -5 / +6 / -1.3 | -22 / +24 / +0.3 | +10 / -8 / -0.6 | +1 / +3 / -0.1 |
| VAH15s | +1 / +3 / -0.3 | -21 / +5 / +0.2 | +12 / -8 / -0.1 | -1 / +1 / +0.0 |
| CRT4h | -8 / +11 / +0.1 | -7 / +6 / +0.0 | +0 / +30 / +0.6 | -1 / +0 / -0.1 |
| OTE705 | -44 / +62 / +1.0 | +1 / -8 / -0.0 | +6 / +2 / -0.3 | -2 / +1 / +0.0 |
| OTE79 | -8 / +27 / +0.4 | -33 / +50 / +0.5 | -3 / +9 / +0.5 | +10 / +0 / -0.1 |
| OTE62act | +15 / +12 / -0.0 | -11 / +12 / +0.1 | +1 / -1 / +0.0 | -6 / +4 / +0.1 |
| KCup4h | -9 / +2 / -0.1 | +11 / +0 / -0.0 | +10 / -15 / -0.4 | +7 / -5 / -0.2 |
| OTE62b73 | -6 / +15 / +0.4 | -11 / +17 / +0.2 | +9 / -18 / -0.4 | +3 / -0 / -0.0 |
| LVN1_1hs | +1 / -4 / -0.1 | -8 / +7 / +0.1 | +1 / +7 / +0.2 | -1 / +0 / +0.0 |

### by book, X'
| line | K6 | P6 | U6 | H6 | M6 | A6 |
|---|---|---|---|---|---|---|
| PDmid | +0 / -1 / +0.0 | -32 / +12 / +0.7 | -4 / +2 / +0.1 | -0 / -0 / +0.0 | -5 / +4 / +0.1 | -0 / -0 / +0.1 |
| HVN0_1hs | -1 / +0 / +0.0 | -6 / +5 / +0.1 | -3 / +3 / -0.1 | -2 / +2 / +0.1 | -4 / +4 / +0.1 | +0 / -1 / -0.0 |
| kijun1h | -5 / +4 / +0.3 | -13 / -9 / +0.3 | +3 / +1 / -0.1 | +4 / -4 / -0.1 | -2 / +4 / +0.1 | -1 / +2 / +0.1 |
| camH3 | +0 / +0 / +0.2 | -17 / +2 / +0.4 | -3 / +6 / +0.2 | -3 / +2 / -0.0 | +2 / +0 / -0.0 | +0 / -2 / -0.0 |
| VAH15s | +4 / -2 / +0.1 | +2 / -12 / -0.0 | +0 / +1 / +0.1 | -2 / +2 / +0.2 | +1 / -1 / -0.0 | +0 / -3 / -0.0 |
| CRT4h | -3 / +2 / -0.0 | -26 / +27 / +0.6 | +0 / -1 / -0.4 | -1 / +5 / +0.0 | +5 / -3 / -0.1 | +0 / +1 / -0.1 |
| OTE705 | +4 / -4 / -0.3 | -7 / -4 / +0.2 | -4 / +0 / +0.0 | +4 / -3 / -0.1 | +0 / -0 / -0.0 | +4 / -1 / -0.1 |
| OTE79 | +1 / -4 / -0.1 | +2 / -6 / -0.0 | +5 / -5 / -0.1 | -0 / -2 / +0.1 | -0 / +2 / +0.0 | -1 / +1 / +0.1 |
| OTE62act | -2 / +5 / +0.1 | +6 / -1 / -0.1 | -7 / +16 / +0.3 | +1 / +3 / -0.1 | +0 / -0 / -0.0 | +2 / -0 / -0.1 |
| KCup4h | -0 / +0 / -0.0 | -5 / +4 / +0.1 | +0 / +1 / +0.0 | +1 / -0 / -0.0 | -0 / -1 / +0.0 | +0 / +0 / +0.0 |
| OTE62b73 | +0 / -0 / -0.0 | +3 / -0 / -0.1 | -3 / -2 / -0.1 | +0 / +1 / +0.1 | +0 / -0 / -0.0 | +0 / -0 / -0.0 |
| LVN1_1hs | +0 / +1 / +0.0 | +8 / +1 / -0.2 | +5 / -6 / -0.2 | +1 / -0 / -0.0 | +1 / -1 / -0.0 | -0 / -1 / -0.0 |

### by session, X'
| line | asia | london | nyam | nypm |
|---|---|---|---|---|
| PDmid | -10 / -2 / +0.3 | -39 / +15 / +0.9 | +7 / +1 / -0.1 | +0 / -1 / +0.0 |
| HVN0_1hs | -3 / -0 / -0.0 | +2 / +5 / -0.0 | -14 / +14 / +0.3 | +0 / +0 / -0.1 |
| kijun1h | -14 / -6 / -0.1 | -13 / -3 / +0.3 | -12 / -7 / +0.2 | -0 / +1 / +0.2 |
| camH3 | -1 / +12 / +0.5 | +22 / -19 / -0.5 | -19 / +1 / +0.4 | -1 / +1 / +0.3 |
| VAH15s | +3 / +2 / +0.4 | -18 / -1 / +0.4 | +11 / -17 / -0.6 | -1 / +1 / +0.1 |
| CRT4h | +9 / +0 / -0.5 | -23 / +31 / +0.5 | -18 / +22 / -0.1 | +0 / +2 / +0.1 |
| OTE705 | -6 / +6 / +0.1 | +4 / -1 / -0.1 | +3 / -2 / -0.1 | +0 / -3 / -0.2 |
| OTE79 | -18 / -2 / +0.2 | +2 / +1 / -0.0 | +2 / -6 / -0.3 | +0 / +0 / +0.1 |
| OTE62act | +2 / +9 / -0.1 | -10 / +10 / +0.2 | -1 / +6 / +0.1 | +0 / -1 / -0.1 |
| KCup4h | +2 / +3 / +0.0 | -2 / +0 / +0.0 | -7 / +7 / +0.1 | +1 / -3 / -0.0 |
| OTE62b73 | +1 / -10 / -0.3 | -4 / -0 / +0.1 | -0 / +1 / +0.1 | +0 / -0 / +0.0 |
| LVN1_1hs | +3 / -3 / -0.2 | +8 / -3 / -0.2 | +1 / +0 / -0.0 | +0 / +0 / +0.0 |


## 8. LOCK OFF frame (per-book locks only = the user literal lock text) - HEADLINE until the combined 12R lock is confirmed; placebos plc0 (draws in n)
### Premise pair
| window | maxDD $k without > with (cut), combined lock OFF (sensitivity; headline has 12R) | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 35 > 37 (-6%) | 96 > 98 | 19.2 > 19.6 |
| L2M | 35 > 37 (-6%) | 218 > 225 | 24.2 > 25.0 |
| L3M | 53 > 50 (+7%) | 193 > 210 | 14.8 > 16.1 |
| L6M | 146 > 133 (+9%) | 6 > 27 | 27.4 > 26.9 |
| HOLD | 146 > 133 (+9%) | -635 > -604 | 23.3 > 23.9 |
| MID | 78 > 63 (+19%) | 140 > 131 | 11.7 > 10.9 |
| PRE | 245 > 178 (+27%) | -859 > -734 | 7.7 > 10.0 |
| X' | 190 > 135 (+29%) | -517 > -445 | -1.8 > -1.2 |
| ALL | 245 > 178 (+27%) | -1134 > -973 | 10.8 > 11.9 |
### Line table, lock OFF
| # | line | kept trades removed (% of kept) | maxDD $k L6M before>after (cut) | HOLD | MID | PRE | X' | worst-20 PRE | worst-20 X' | mean d $k/wk (MDE) L6M / HOLD / MID / PRE / X' | equal-risk mean d L6M / PRE / X' | placebo rank random-level A / same-volume B (L6M, PRE, X') | label | S/T/N | TOL-B / TOL-nc | PRE and X' cut >= 20% | sign-agree PRE, X', HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE62b73 (action) | -87 (-0.5%) | 134>133 (+1%) | 145>133 (+8%) | 62>63 (-2%) | 194>178 (+8%) | 165>135 (+18%) | -740>-734 | -504>-445 | +0.7 (2.7) / +1.7 (2.4) / +0.8 (3.9) / +0.7 (1.4) / +1.6 (3.4) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | n/a (action line, no placebo) | Y/Y/Y | Y/Y | n | Y |
| 2 | CRT4h (coded) | 39 (0.2%) | 140>133 (+5%) | 140>133 (+5%) | 68>63 (+7%) | 187>178 (+5%) | 151>135 (+11%) | -738>-734 | -449>-445 | +0.5 (2.2) / -0.1 (1.4) / -0.8 (3.1) / +0.6 (0.9) / -0.0 (1.2) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/Y/Y | Y/Y | n | Y |
| 3 | OTE62act (coded) | -51 (-0.3%) | 134>136 (-1%) | 145>136 (+6%) | 62>59 (+4%) | 194>172 (+12%) | 165>160 (+3%) | -740>-695 | -504>-493 | -1.0 (1.5) / -0.1 (1.2) / +1.7 (3.0) / +0.6 (2.0) / +0.1 (1.1) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 4 | VAH15s (UNCODED) | 1 (0.0%) | 133>128 (+3%) | 133>128 (+3%) | 63>64 (-1%) | 178>162 (+9%) | 135>131 (+3%) | -734>-697 | -445>-458 | -0.5 (0.8) / -0.7 (1.5) / -0.1 (5.3) / -0.1 (1.0) / -0.9 (2.3) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | Y |
| 5 | OTE79 (coded) | 62 (0.3%) | 139>133 (+4%) | 139>133 (+4%) | 64>63 (+2%) | 203>178 (+12%) | 123>135 (-9%) | -762>-734 | -429>-445 | -0.0 (0.9) / -0.0 (0.8) / -0.6 (1.5) / +0.6 (1.2) / -0.5 (0.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 6 | camH3 (coded) | 10 (0.1%) | 127>133 (-4%) | 127>133 (-4%) | 61>63 (-2%) | 180>178 (+1%) | 149>135 (+10%) | -747>-734 | -477>-445 | -0.3 (0.8) / -0.6 (0.9) / -0.9 (1.5) / +0.1 (0.8) / +0.2 (1.5) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 7 | PDmid (coded) | 13 (0.1%) | 131>133 (-1%) | 131>133 (-1%) | 63>63 (+1%) | 174>178 (-3%) | 150>135 (+10%) | -729>-734 | -472>-445 | -1.0 (2.2) / -0.7 (1.2) / +0.0 (1.1) / -0.1 (0.4) / +0.9 (2.4) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 8 | OTE705 (coded) | 76 (0.4%) | 136>133 (+3%) | 136>133 (+3%) | 66>63 (+5%) | 183>178 (+2%) | 134>135 (-1%) | -749>-734 | -445>-445 | -0.3 (2.0) / -0.1 (1.1) / +0.1 (2.0) / +0.4 (0.7) / -0.0 (0.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 9 | LVN1_1hs (UNCODED) | 9 (0.0%) | 133>135 (-2%) | 133>135 (-2%) | 63>60 (+4%) | 178>178 (+0%) | 135>129 (+5%) | -734>-707 | -445>-450 | -0.6 (2.2) / +0.0 (1.3) / +0.4 (1.6) / +0.2 (1.2) / -0.4 (0.9) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 10 | KCup4h (coded) | -6 (-0.0%) | 133>133 (+0%) | 133>133 (+0%) | 63>63 (+0%) | 179>178 (+1%) | 130>135 (-4%) | -742>-734 | -456>-445 | +0.2 (0.5) / +0.1 (0.4) / +0.2 (1.1) / +0.0 (0.6) / +0.0 (0.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | Y/Y/Y | Y/Y | n | n |
| 11 | kijun1h (coded) | 22 (0.1%) | 134>133 (+1%) | 134>133 (+1%) | 68>63 (+9%) | 170>178 (-5%) | 138>135 (+2%) | -736>-734 | -446>-445 | -0.2 (0.9) / -0.3 (0.8) / -0.9 (2.7) / -0.1 (1.1) / -0.4 (1.0) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
| 12 | HVN0_1hs (UNCODED) | -10 (-0.1%) | 133>142 (-7%) | 133>142 (-7%) | 63>66 (-5%) | 178>180 (-1%) | 135>129 (+4%) | -734>-724 | -445>-438 | -1.0 (2.6) / -0.4 (1.4) / -0.1 (1.5) / +0.2 (0.9) / -0.1 (0.7) | ? / ? / ? | -/-/- ; -/-/- ; -/-/- (n 0/0/0) | no | n/n/n | n/n | n | n |
### Episode-proofing, lock OFF
| line | L6M: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | HOLD: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | MID: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | PRE: cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag | X': cut / cut without the trough week (date) / leave-month-out range / P(cut>0) / flag |
|---|---|---|---|---|---|
| OTE62b73 | +1% / +1% (20260817) / -6%..+9% / 0.49 / no cut | +8% / +1% (20260209) / +1%..+15% / 0.83 / no cut | -2% / -8% (20260209) / -8%..+25% / 0.51 / no cut | +8% / +11% (20250414) / +5%..+22% / 0.89 / no cut | +18% / +17% (20230925) / -9%..+28% / 0.83 / holds |
| CRT4h | +5% / +2% (20260817) / +1%..+11% / 0.79 / no cut | +5% / +2% (20260817) / -1%..+5% / 0.52 / no cut | +7% / -4% (20260323) / -4%..+7% / 0.65 / no cut | +5% / +4% (20250414) / +1%..+9% / 0.77 / no cut | +11% / +1% (20230911) / +2%..+15% / 0.57 / ONE-WEEK |
| OTE62act | -1% / +2% (20260817) / -7%..-1% / 0.42 / no cut | +6% / -1% (20260209) / -1%..+8% / 0.78 / no cut | +4% / -2% (20260209) / -2%..+19% / 0.74 / no cut | +12% / +5% (20250414) / +5%..+23% / 0.79 / holds | +3% / +9% (20230925) / -9%..+9% / 0.67 / no cut |
| VAH15s | +3% / +3% (20260817) / -1%..+5% / 0.77 / no cut | +3% / -1% (20260817) / -2%..+3% / 0.49 / no cut | -1% / -6% (20260323) / -6%..-1% / 0.13 / no cut | +9% / +3% (20250414) / +2%..+11% / 0.97 / no cut | +3% / +3% (20230911) / -8%..+6% / 0.30 / no cut |
| OTE79 | +4% / +6% (20260817) / +2%..+5% / 0.90 / no cut | +4% / +6% (20260817) / +0%..+4% / 0.67 / no cut | +2% / +0% (20260323) / +0%..+2% / 0.75 / no cut | +12% / +13% (20250414) / +5%..+16% / 0.83 / holds | -9% / -11% (20230911) / -10%..-1% / 0.06 / no cut |
| camH3 | -4% / -3% (20260817) / -6%..-2% / 0.05 / no cut | -4% / +2% (20260817) / -6%..+3% / 0.41 / no cut | -2% / -3% (20260323) / -3%..-2% / 0.03 / no cut | +1% / +1% (20250414) / -1%..+4% / 0.57 / no cut | +10% / +15% (20230904) / +4%..+15% / 0.83 / no cut |
| PDmid | -1% / +0% (20260817) / -3%..-0% / 0.00 / no cut | -1% / +0% (20260817) / -1%..-0% / 0.16 / no cut | +1% / +0% (20260323) / -0%..+1% / 0.70 / no cut | -3% / -2% (20250414) / -3%..+1% / 0.23 / no cut | +10% / +9% (20230925) / +5%..+16% / 0.87 / holds |
| OTE705 | +3% / +5% (20260817) / -11%..+12% / 0.83 / no cut | +3% / +5% (20260817) / -4%..+3% / 0.63 / no cut | +5% / -10% (20260323) / -10%..+5% / 0.62 / no cut | +2% / -1% (20250414) / -3%..+8% / 0.47 / no cut | -1% / -1% (20230911) / -6%..+3% / 0.64 / no cut |
| LVN1_1hs | -2% / -0% (20260817) / -5%..+1% / 0.24 / no cut | -2% / -0% (20260817) / -5%..+1% / 0.61 / no cut | +4% / +0% (20260323) / -0%..+4% / 0.63 / no cut | +0% / +2% (20250414) / +0%..+14% / 0.74 / no cut | +5% / +5% (20230911) / +0%..+7% / 0.48 / no cut |
| KCup4h | +0% / +0% (20260817) / -0%..+4% / 0.31 / no cut | +0% / +0% (20260817) / -0%..+3% / 0.17 / no cut | +0% / +0% (20260323) / -0%..-0% / 0.00 / no cut | +1% / +5% (20250414) / +0%..+5% / 0.84 / no cut | -4% / -4% (20230911) / -14%..+2% / 0.53 / no cut |
| kijun1h | +1% / +0% (20260817) / -2%..+2% / 0.76 / no cut | +1% / +0% (20260817) / -0%..+1% / 0.73 / no cut | +9% / +2% (20260323) / +2%..+9% / 0.93 / no cut | -5% / -1% (20250414) / -10%..+5% / 0.56 / no cut | +2% / +2% (20230911) / -1%..+5% / 0.33 / no cut |
| HVN0_1hs | -7% / -8% (20260817) / -13%..+3% / 0.18 / no cut | -7% / -8% (20260817) / -7%..+3% / 0.48 / no cut | -5% / +9% (20260323) / -5%..+9% / 0.45 / no cut | -1% / +0% (20250414) / -1%..+11% / 0.83 / no cut | +4% / +4% (20230911) / -1%..+7% / 0.52 / no cut |
### Honest ranking, lock OFF
| honest # | line | S_PX = mean(cut PRE, cut X') | cut PRE | cut X' | PX gate | ONE recent look: cut L6M | HOLD | MID | L3M (view L1M) | mean d L6M (MDE) / HOLD / MID | label | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OTE62b73 | +0.132 | +8% | +18% | pass | +1% | +8% | -2% | -2% (-21%) | +0.7 (2.7) / +1.7 / +0.8 | n/a (action line, no placebo) | Y/Y/Y |
| 2 | CRT4h | +0.077 | +5% | +11% | pass | +5% | +5% | +7% | +11% (-2%) | +0.5 (2.2) / -0.1 / -0.8 | no | n/Y/Y |
| 3 | OTE62act | +0.074 | +12% | +3% | pass | -1% | +6% | +4% | -7% (-12%) | -1.0 (1.5) / -0.1 / +1.7 | no | n/n/n |
| 4 | camH3 | +0.053 | +1% | +10% | pass | -4% | -4% | -2% | -6% (-10%) | -0.3 (0.8) / -0.6 / -0.9 | no | n/n/n |
| - | VAH15s | +0.062 | +9% | +3% | fail: X' w20 worse | +3% | +3% | -1% | +5% (-2%) | -0.5 (0.8) / -0.7 / -0.1 | no | n/n/n |
| - | PDmid | +0.037 | -3% | +10% | fail: PRE no cut, PRE w20 worse | -1% | -1% | +1% | -3% (+0%) | -1.0 (2.2) / -0.7 / +0.0 | no | n/n/n |
| - | LVN1_1hs | +0.025 | +0% | +5% | fail: X' w20 worse | -2% | -2% | +4% | +1% (-12%) | -0.6 (2.2) / +0.0 / +0.4 | no | n/n/n |
| - | HVN0_1hs | +0.018 | -1% | +4% | fail: PRE no cut | -7% | -7% | -5% | +3% (-19%) | -1.0 (2.6) / -0.4 / -0.1 | no | n/n/n |
| - | OTE79 | +0.013 | +12% | -9% | fail: X' no cut, X' w20 worse, X' mean<-0.5MDE | +4% | +4% | +2% | +5% (+0%) | -0.0 (0.9) / -0.0 / -0.6 | no | n/n/n |
| - | OTE705 | +0.009 | +2% | -1% | fail: X' no cut | +3% | +3% | +5% | -11% (+1%) | -0.3 (2.0) / -0.1 / +0.1 | no | n/n/n |
| - | kijun1h | -0.014 | -5% | +2% | fail: PRE no cut | +1% | +1% | +9% | +2% (+0%) | -0.2 (0.9) / -0.3 / -0.9 | no | n/n/n |
| - | KCup4h | -0.017 | +1% | -4% | fail: X' no cut | +0% | +0% | +0% | +0% (+6%) | +0.2 (0.5) / +0.1 / +0.2 | no | Y/Y/Y |
### Post-hoc ranking, lock OFF
| post-hoc # | line | cut L6M | Calmar L6M before>after | cut HOLD | cut MID | cut L3M | PRE: cut, mean d (MDE) | X': cut, mean d (MDE) | S/T/N | TOL-B/nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | CRT4h | +5.1% | 0.19 > 0.20 | +5.1% | +7.3% | +10.6% | +4.7%, +0.6 (0.9) | +10.6%, -0.0 (1.2) | n/Y/Y | Y/Y | no |
| 2 | OTE79 | +4.3% | 0.19 > 0.20 | +4.3% | +1.6% | +5.4% | +11.9%, +0.6 (1.2) | -9.3%, -0.5 (0.9) | n/n/n | n/n | no |
| 3 | VAH15s | +3.4% | 0.20 > 0.21 | +3.4% | -1.4% | +5.2% | +9.4%, -0.1 (1.0) | +2.9%, -0.9 (2.3) | n/n/n | n/n | no |
| 4 | OTE705 | +2.7% | 0.20 > 0.20 | +2.7% | +5.1% | -11.4% | +2.5%, +0.4 (0.7) | -0.6%, -0.0 (0.9) | n/n/n | n/n | no |
| 5 | kijun1h | +0.9% | 0.20 > 0.20 | +0.9% | +8.6% | +2.1% | -5.0%, -0.1 (1.1) | +2.2%, -0.4 (1.0) | n/n/n | n/n | no |
| 6 | OTE62b73 | +0.9% | 0.20 > 0.20 | +8.4% | -1.5% | -2.1% | +8.1%, +0.7 (1.4) | +18.3%, +1.6 (3.4) | Y/Y/Y | Y/Y | n/a (action line, no placebo) |
| 7 | KCup4h | +0.0% | 0.20 > 0.20 | +0.0% | +0.0% | +0.0% | +0.5%, +0.0 (0.6) | -3.8%, +0.0 (0.7) | Y/Y/Y | Y/Y | no |
| 8 | PDmid | -1.2% | 0.21 > 0.20 | -1.2% | +1.0% | -3.4% | -2.8%, -0.1 (0.4) | +10.3%, +0.9 (2.4) | n/n/n | n/n | no |
| 9 | OTE62act | -1.3% | 0.20 > 0.19 | +6.3% | +4.4% | -6.6% | +11.7%, +0.6 (2.0) | +3.1%, +0.1 (1.1) | n/n/n | n/n | no |
| 10 | LVN1_1hs | -1.9% | 0.20 > 0.19 | -1.9% | +3.7% | +0.8% | +0.4%, +0.2 (1.2) | +4.6%, -0.4 (0.9) | n/n/n | n/n | no |
| 11 | camH3 | -4.1% | 0.21 > 0.20 | -4.1% | -1.9% | -5.8% | +1.0%, +0.1 (0.8) | +9.7%, +0.2 (1.5) | n/n/n | n/n | no |
| 12 | HVN0_1hs | -7.4% | 0.20 > 0.18 | -7.4% | -5.2% | +2.6% | -0.8%, +0.2 (0.9) | +4.4%, -0.1 (0.7) | n/n/n | n/n | no |
### Lines that add nothing, lock OFF
| line | rows newly acted on (all 187 wk) | pre-declared null rule | cuts (dDD% L6M / PRE / X') | mean d / MDE (L6M, PRE, X') | weakness |
|---|---|---|---|---|---|
| HVN0_1hs | 1207 | not null | -7.4% / -0.8% / +4.4% | -0.41 / +0.27 / -0.21 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| kijun1h | 1443 | not null | +0.9% / -5.0% / +2.2% | -0.16 / -0.05 / -0.36 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| KCup4h | 970 | not null | +0.0% / +0.5% / -3.8% | +0.45 / +0.04 / +0.00 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| LVN1_1hs | 1008 | not null | -1.9% / +0.4% / +4.6% | -0.27 / +0.15 / -0.41 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| OTE705 | 1458 | not null | +2.7% / +2.5% / -0.6% | -0.14 / +0.55 / -0.02 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| PDmid | 414 | not null | -1.2% / -2.8% / +10.3% | -0.46 / -0.28 / +0.39 | cuts in 1 of 4 (L6M, HOLD, PRE, X') |
| camH3 | 1632 | not null | -4.1% / +1.0% / +9.7% | -0.36 / +0.06 / +0.11 | cuts in 2 of 4 (L6M, HOLD, PRE, X') |
| OTE79 | 1664 | not null | +4.3% / +11.9% / -9.3% | -0.01 / +0.51 / -0.53 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| VAH15s | 1321 | not null | +3.4% / +9.4% / +2.9% | -0.61 / -0.07 / -0.40 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| OTE62act | 1414 | not null | -1.3% / +11.7% / +3.1% | -0.65 / +0.29 / +0.09 | cuts in 3 of 4 (L6M, HOLD, PRE, X') |
| CRT4h | 1076 | not null | +5.1% / +4.7% / +10.6% | +0.22 / +0.66 / -0.02 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
| OTE62b73 | 0 | not null | +0.9% / +8.1% / +18.3% | +0.26 / +0.50 / +0.46 | cuts in 4 of 4 (L6M, HOLD, PRE, X') |
### Per line, lock 12R vs lock OFF
| line | cut with combined 12R lock: L6M / HOLD / MID / PRE / X' | cut lock OFF (per-book locks only): L6M / HOLD / MID / PRE / X' | mean d $k/wk L6M lock12 / lock-off | flag |
|---|---|---|---|---|
| PDmid | -2% / -4% / +3% / +2% / +22% | -2% / -4% / +3% / +2% / +22% | -1.0 / -1.0 | survives lock-off |
| HVN0_1hs | +1% / +1% / +0% / +15% / +5% | +1% / +1% / +0% / +15% / +5% | -0.6 / -0.6 | survives lock-off |
| kijun1h | -2% / +1% / +2% / +7% / +13% | -2% / +1% / +2% / +7% / +13% | +0.2 / +0.2 | survives lock-off |
| camH3 | +4% / +6% / -0% / +2% / +15% | +4% / +6% / -0% / +2% / +15% | +0.0 / +0.0 | survives lock-off |
| VAH15s | -2% / +2% / +0% / +7% / +3% | -2% / +2% / +0% / +7% / +3% | -0.4 / -0.4 | no cut in either |
| CRT4h | +2% / +0% / +7% / +4% / +0% | +2% / +0% / +7% / +4% / +0% | +0.7 / +0.7 | no cut in either |
| OTE705 | -12% / +5% / +6% / +7% / -7% | -12% / +5% / +6% / +7% / -7% | -0.6 / -0.6 | no cut in either |
| OTE79 | -1% / -1% / -1% / -1% / -1% | -1% / -1% / -1% / -1% / -1% | +0.0 / +0.0 | no cut in either |
| OTE62act | +9% / -42% / +0% / -9% / +5% | +9% / -42% / +0% / -9% / +5% | +2.9 / +2.9 | no cut in either |
| KCup4h | +7% / +1% / +0% / -7% / +3% | +7% / +1% / +0% / -7% / +3% | +0.4 / +0.4 | no cut in either |
| OTE62b73 | +6% / -37% / +1% / -4% / -4% | +6% / -37% / +1% / -4% / -4% | +3.8 / +3.8 | no cut in either |
| LVN1_1hs | -2% / +1% / +2% / -2% / -10% | -2% / +1% / +2% / -2% / -10% | -0.3 / -0.3 | no cut in either |

# A2 PROFILE-LINE VARIANTS, B1 SESSION-STRUCTURE LINES, LOCK FRAMES - final (Z1; 2026-11-02 05:53Z; base D7 v1.3 EXACT V13eh, marginal-in-set unless stated)

POST-HOC, no PASS, Shadow only. Frames: lock 12R (combined stack lock + per-book locks) and lock OFF (per-book locks only, the user literal lock text). HEADLINE = lock OFF until the user confirms the combined lock; a cut that exists only with the combined lock is LOCK-ONLY (not a lead).

## Layer and lines in both lock frames (V13eh)
### Whole layer, lock OFF
| window | maxDD $k without > with (cut), combined lock OFF (sensitivity; headline has 12R) | worst-20 | mean $k/wk |
|---|---|---|---|
| L1M | 35 > 37 (-6%) | 96 > 98 | 19.2 > 19.6 |
| L2M | 35 > 37 (-6%) | 218 > 225 | 24.2 > 25.0 |
| L3M | 53 > 50 (+7%) | 193 > 210 | 14.8 > 16.1 |
| L6M | 146 > 133 (+9%) | 6 > 27 | 27.4 > 26.9 |
| HOLD | 146 > 133 (+9%) | -635 > -604 | 23.3 > 23.9 |
| MID | 78 > 63 (+19%) | 140 > 131 | 11.7 > 10.9 |
| PRE | 245 > 178 (+27%) | -859 > -734 | 7.7 > 10.0 |
| X' | 190 > 135 (+29%) | -517 > -445 | -1.8 > -1.2 |
| ALL | 245 > 178 (+27%) | -1134 > -973 | 10.8 > 11.9 |
### Per line
| line | cut with combined 12R lock: L6M / HOLD / MID / PRE / X' | cut lock OFF (per-book locks only): L6M / HOLD / MID / PRE / X' | mean d $k/wk L6M lock12 / lock-off | flag |
|---|---|---|---|---|
| PDmid | -2% / -4% / +3% / +2% / +22% | -2% / -4% / +3% / +2% / +22% | -1.0 / -1.0 | survives lock-off |
| HVN0_1hs | +1% / +1% / +0% / +15% / +5% | +1% / +1% / +0% / +15% / +5% | -0.6 / -0.6 | survives lock-off |
| kijun1h | -2% / +1% / +2% / +7% / +13% | -2% / +1% / +2% / +7% / +13% | +0.2 / +0.2 | survives lock-off |
| camH3 | +4% / +6% / -0% / +2% / +15% | +4% / +6% / -0% / +2% / +15% | +0.0 / +0.0 | survives lock-off |
| VAH15s | -2% / +2% / +0% / +7% / +3% | -2% / +2% / +0% / +7% / +3% | -0.4 / -0.4 | no cut in either |
| CRT4h | +2% / +0% / +7% / +4% / +0% | +2% / +0% / +7% / +4% / +0% | +0.7 / +0.7 | no cut in either |
| OTE705 | -12% / +5% / +6% / +7% / -7% | -12% / +5% / +6% / +7% / -7% | -0.6 / -0.6 | no cut in either |
| OTE79 | -1% / -1% / -1% / -1% / -1% | -1% / -1% / -1% / -1% / -1% | +0.0 / +0.0 | no cut in either |
| OTE62act | +9% / -42% / +0% / -9% / +5% | +9% / -42% / +0% / -9% / +5% | +2.9 / +2.9 | no cut in either |
| KCup4h | +7% / +1% / +0% / -7% / +3% | +7% / +1% / +0% / -7% / +3% | +0.4 / +0.4 | no cut in either |
| OTE62b73 | +6% / -37% / +1% / -4% / -4% | +6% / -37% / +1% / -4% / -4% | +3.8 / +3.8 | no cut in either |
| LVN1_1hs | -2% / +1% / +2% / -2% / -10% | -2% / +1% / +2% / -2% / -10% | -0.3 / -0.3 | no cut in either |

## Plain answers (A2 / B1 / lock frames)
* LOCK FRAMES (V13X): the whole 7-line HALF layer SURVIVES with the combined lock removed (lock OFF: maxDD L6M/HOLD +9%, MID +19%, PRE +27%, X' +29%, worst-20 PRE -859 > -734k, X' -517 > -445k), so the layer is not a lock artefact (it cuts more without the combined lock than with it in PRE/X', less in MID/L6M). Per line, OTE-62 B73, OTE79, CRT4h and PDmid keep a lock-off cut in PRE or X'; HVN0_1hs and kijun1h cuts are LOCK-ONLY.
* PROFILE LINES (A2): NOT dead on every variant in the lock-12 frame: VAH15s with swing strength 3 passes the PRE+X' gate (cut PRE +21%, X' +13%, L6M +6%) and beats all three placebos in PRE (ranks 0.02 / 0.04 / 0.05) and X' (0.04 / 0.04 / 0.03), but the cut is LOCK-ONLY (lock OFF: PRE +10%, X' 0%), L6M is below 20%, and it is the best of 24 variants tried: labelled LOCK-ONLY, not a lead. Every other variant (bin 2/4 ticks, anchor shifts, session-anchored Asia/London/RTH value areas, LVN1/HVN0 at any variant) fails the gate: the profile lines are DEAD on every variant except the lock-only VAH15s swing-3.
* B1 SESSION LINES: of 37 session-structure lines none cuts L6M and PRE and X' together; seven pass the PRE+X' gate in the lock-12 frame (PDX prior-RTH low, week open, Globex open, Asia low, session-VWAP RTH -2 sigma, ...), but the PRE cuts are LOCK-ONLY for prior-RTH low, week open and Globex open (lock OFF PRE <= 2%), and Asia low / RTH VWAP -2 sigma have no lock-off cut. No B1 line is a lead on this evidence; placebo ranks follow below where run.

## A2. Profile-line variants (swing strength 3, bin 2 / 4 ticks, anchor shifts endconf / startm1, session-anchored Asia / London / RTH value areas) - marginal-in-set (line added to the shipped set)
| variant | rows firing D20 | kept removed | maxDD cut L6M / HOLD / MID / PRE / X' | worst-20 PRE b>a / X' b>a | mean d L6M / PRE / X' $k/wk (MDE) | PX gate | S/T/N |
|---|---|---|---|---|---|---|---|
| VAH15s_w3 | 1938 | -52 | +6% / +3% / +2% / +21% / +13% | -512>-498 ; -342>-338 | +0.0 (0.6) / +1.0 (2.0) / +0.5 (1.4) | pass | n/Y/Y |
| HVN0_1hs_bin4 | 1920 | -21 | +1% / +2% / +3% / +15% / +6% | -512>-518 ; -342>-329 | -0.5 (1.9) / +0.3 (1.7) / +0.2 (0.7) | fail | n/n/n |
| HVN0_1hs_bin2 | 1922 | 17 | +1% / +1% / +0% / +15% / +5% | -512>-519 ; -342>-329 | -0.6 (1.9) / -0.1 (2.0) / +0.2 (0.7) | fail | n/n/n |
| HVN0_1hs_w3 | 1681 | -23 | +7% / +1% / +0% / +12% / +0% | -512>-516 ; -342>-341 | -0.7 (1.7) / +0.0 (1.3) / +0.0 (0.3) | fail | n/n/n |
| HVN0_1hs_endconf | 1468 | 44 | +1% / +0% / +0% / +7% / +4% | -512>-513 ; -342>-336 | -0.2 (1.7) / -0.2 (2.1) / +0.2 (0.4) | fail | n/n/n |
| SESS_rth_val | 533 | 59 | +5% / +1% / +2% / +24% / -15% | -512>-467 ; -342>-347 | -0.6 (1.9) / +0.8 (1.6) / -0.6 (1.3) | fail | n/n/n |
| VAH15s_bin4 | 1945 | 226 | +3% / +2% / +0% / +7% / +2% | -512>-495 ; -342>-351 | -3.7 (9.1) / -0.2 (0.9) / +0.3 (1.8) | fail | n/n/n |
| VAH15s_endconf | 2456 | -79 | +9% / -3% / -6% / +26% / -18% | -512>-496 ; -342>-356 | +0.3 (1.2) / +0.2 (1.9) / -0.4 (2.7) | fail | n/Y/Y |
| SESS_asia_val | 732 | 4 | +5% / +0% / +0% / +0% / +7% | -512>-507 ; -342>-339 | +0.1 (0.4) / -0.3 (0.6) / +0.3 (0.6) | pass | n/n/Y |
| VAH15s_bin2 | 1973 | 212 | +3% / +2% / +0% / +1% / +3% | -512>-509 ; -342>-350 | -3.5 (9.1) / -0.4 (1.0) / +0.3 (1.8) | fail | n/n/n |
| SESS_london_val | 357 | 5 | +0% / +0% / +0% / +0% / +3% | -512>-512 ; -342>-337 | -0.0 (0.1) / +0.0 (0.1) / +0.1 (0.4) | pass | n/n/n |
| SESS_london_vah | 517 | -49 | +0% / +0% / +0% / -0% / +3% | -512>-512 ; -342>-342 | +0.1 (0.9) / -0.0 (0.4) / +0.1 (0.3) | fail | n/n/n |
| LVN1_1hs_w3 | 1202 | -124 | -1% / +1% / +2% / +1% / +2% | -512>-489 ; -342>-335 | -0.2 (0.7) / +1.6 (4.1) / +0.1 (0.6) | pass | n/n/n |
| SESS_asia_vah | 935 | 5 | +1% / +0% / +0% / +2% / -1% | -512>-513 ; -342>-340 | +0.0 (0.1) / -0.0 (0.3) / -0.0 (0.3) | fail | n/n/Y |
| SESS_asia_poc | 587 | 10 | +1% / +0% / +1% / -0% / +1% | -512>-512 ; -342>-339 | +0.1 (0.2) / -0.1 (0.4) / +0.0 (0.3) | fail | n/n/Y |
| SESS_london_poc | 291 | -6 | -7% / +0% / +0% / +2% / -3% | -512>-507 ; -342>-343 | -0.2 (0.5) / +0.1 (0.2) / -0.1 (0.2) | fail | n/n/n |
| HVN0_1hs_startm1 | 1975 | 22 | +6% / -2% / +0% / -0% / -1% | -512>-518 ; -342>-338 | +0.1 (1.3) / -0.2 (1.5) / -0.0 (0.4) | fail | n/n/n |
| LVN1_1hs_endconf | 1461 | 28 | -3% / +8% / -0% / -2% / -1% | -512>-503 ; -342>-339 | -0.3 (1.1) / +0.6 (1.8) / -0.0 (0.4) | fail | n/n/n |
| VAH15s_startm1 | 1890 | 49 | -2% / -1% / -2% / +0% / -4% | -512>-511 ; -342>-346 | -0.0 (0.5) / +0.0 (1.7) / -0.2 (0.3) | fail | n/n/n |
| SESS_rth_poc | 618 | 42 | +0% / -0% / +0% / -8% / +3% | -512>-523 ; -342>-338 | -0.2 (0.7) / -0.3 (0.8) / +0.1 (0.4) | fail | n/n/n |
| LVN1_1hs_startm1 | 1432 | -42 | -10% / +2% / +5% / -2% / -7% | -512>-526 ; -342>-346 | -1.0 (1.9) / -0.4 (0.7) / -0.3 (0.5) | fail | n/n/n |
| SESS_rth_vah | 715 | 150 | +0% / +4% / +0% / +0% / -9% | -512>-514 ; -342>-334 | +0.1 (0.3) / +0.0 (0.1) / -0.4 (2.0) | fail | n/n/Y |
| LVN1_1hs_bin2 | 1434 | -11 | -3% / +1% / +2% / +0% / -10% | -512>-489 ; -342>-344 | -0.3 (2.2) / +0.2 (1.0) / -0.4 (0.7) | fail | n/n/n |
| LVN1_1hs_bin4 | 1405 | -13 | -3% / +1% / +0% / -0% / -10% | -512>-489 ; -342>-344 | +0.3 (0.9) / +0.3 (1.0) / -0.4 (0.7) | fail | n/n/n |

### one-at-a-time (zone off -> variant alone)
| variant | rows firing D20 | kept removed | maxDD cut L6M / HOLD / MID / PRE / X' | worst-20 PRE b>a / X' b>a | mean d L6M / PRE / X' $k/wk (MDE) | PX gate | S/T/N |
|---|---|---|---|---|---|---|---|
| VAH15s_bin4 | 1945 | 124 | -2% / +4% / +4% / +6% / +11% | -608>-597 ; -386>-381 | -0.4 (0.8) / -0.1 (1.6) / -0.9 (3.2) | pass | n/n/n |
| VAH15s_bin2 | 1973 | 13 | -2% / +3% / +3% / +7% / +9% | -608>-593 ; -386>-383 | -0.5 (1.0) / +0.0 (1.7) / +0.0 (1.0) | pass | n/n/n |
| VAH15s_startm1 | 1890 | 133 | -3% / -1% / -1% / +8% / +6% | -608>-563 ; -386>-387 | +0.1 (0.6) / +0.3 (1.8) / +0.1 (0.6) | fail | n/Y/Y |
| HVN0_1hs_w3 | 1681 | 173 | +3% / +2% / +2% / +10% / -3% | -608>-546 ; -386>-373 | -0.9 (1.8) / +0.4 (2.5) / -0.2 (2.7) | fail | n/n/n |
| SESS_asia_vah | 935 | -8 | -0% / -7% / -9% / +4% / +3% | -608>-601 ; -386>-382 | -0.0 (0.1) / +0.6 (1.4) / +0.1 (0.3) | pass | n/n/n |
| SESS_asia_val | 732 | 5 | +4% / +1% / +1% / -2% / +8% | -608>-614 ; -386>-386 | +0.0 (0.4) / -0.4 (0.6) / +0.3 (0.6) | fail | n/n/Y |
| SESS_london_vah | 517 | 11 | +0% / +0% / +0% / +0% / +4% | -608>-611 ; -386>-389 | +0.2 (0.7) / -0.0 (0.4) / +0.1 (0.4) | fail | n/n/n |
| LVN1_1hs_w3 | 1202 | 105 | -2% / +1% / +1% / -9% / +13% | -608>-605 ; -386>-359 | -0.2 (0.7) / -0.7 (1.7) / +0.2 (1.8) | fail | n/n/n |
| SESS_rth_poc | 618 | 69 | +0% / +1% / +1% / +0% / +3% | -608>-617 ; -386>-394 | -0.4 (0.8) / -0.4 (1.6) / +0.0 (0.9) | fail | n/n/n |
| SESS_asia_poc | 587 | 4 | -4% / +0% / -0% / -1% / +2% | -608>-609 ; -386>-384 | -0.1 (0.3) / -0.0 (0.3) / +0.1 (0.4) | fail | n/n/n |
| VAH15s_w3 | 1938 | 392 | -2% / +3% / +3% / +5% / -4% | -608>-593 ; -386>-365 | +0.1 (0.8) / +0.1 (1.3) / -1.1 (3.8) | fail | n/Y/Y |
| SESS_london_val | 357 | 7 | +0% / +0% / +0% / +0% / +0% | -608>-608 ; -386>-386 | -0.0 (0.1) / +0.0 (0.1) / +0.0 (0.0) | fail | n/n/n |
| SESS_london_poc | 291 | 25 | +0% / +0% / +0% / -1% / -2% | -608>-607 ; -386>-386 | +0.0 (0.0) / +0.0 (0.3) / -0.0 (0.2) | fail | n/n/n |
| HVN0_1hs_bin2 | 1922 | 230 | +1% / +26% / +12% / +9% / -19% | -608>-562 ; -386>-382 | -0.8 (1.9) / +0.7 (2.3) / -0.4 (2.5) | fail | n/n/n |
| LVN1_1hs_bin4 | 1405 | 71 | -4% / -2% / -2% / -13% / +0% | -608>-611 ; -386>-396 | +0.3 (1.0) / -0.5 (1.7) / -0.1 (0.9) | fail | n/n/n |
| LVN1_1hs_bin2 | 1434 | 51 | -4% / -2% / -3% / -13% / -0% | -608>-611 ; -386>-397 | -0.3 (2.2) / -0.4 (1.8) / -0.1 (0.9) | fail | n/n/n |
| VAH15s_endconf | 2456 | 93 | +2% / -4% / -4% / +8% / -24% | -608>-591 ; -386>-376 | +0.1 (1.2) / +0.3 (2.2) / -0.8 (3.0) | fail | n/Y/Y |
| HVN0_1hs_endconf | 1468 | 148 | +9% / +24% / +9% / +11% / -30% | -608>-558 ; -386>-399 | -0.2 (1.9) / +1.4 (1.6) / -1.2 (2.8) | fail | n/n/n |
| HVN0_1hs_startm1 | 1975 | 241 | +6% / +5% / +7% / +7% / -26% | -608>-564 ; -386>-376 | -0.1 (1.3) / +0.5 (2.3) / -0.9 (2.7) | fail | n/n/n |
| HVN0_1hs_bin4 | 1920 | 255 | -0% / +28% / +14% / +9% / -29% | -608>-561 ; -386>-392 | -0.7 (1.9) / +0.8 (2.3) / -1.0 (2.6) | fail | n/n/n |
| SESS_rth_vah | 715 | 104 | +0% / +4% / +2% / +1% / -25% | -608>-618 ; -386>-388 | +0.2 (0.3) / +0.0 (0.5) / -0.9 (3.0) | fail | n/n/Y |
| LVN1_1hs_startm1 | 1432 | 67 | -11% / -2% / -2% / -0% / -24% | -608>-606 ; -386>-401 | -1.0 (2.0) / +0.1 (0.7) / -1.2 (2.5) | fail | n/n/n |
| LVN1_1hs_endconf | 1461 | 158 | -2% / +7% / +2% / -9% / -18% | -608>-606 ; -386>-397 | -0.1 (1.0) / -0.1 (1.9) / -0.7 (2.4) | fail | n/n/n |
| SESS_rth_val | 533 | 116 | +5% / +1% / +2% / +10% / -45% | -608>-589 ; -386>-376 | -0.1 (0.8) / +0.6 (1.1) / -1.3 (4.2) | fail | n/n/n |

### Placebos (3 kinds) and lock frames for the variants that pass the PRE+X' gate
| line (marginal-in-set, V13X exact) | maxDD cut L6M / HOLD / MID / PRE / X' | placebo A random-level / B same-volume / C shuffled-day: rank of the cut in L6M ; PRE ; X' (n) | worst-20 rank PRE A/B/C | S/T/N | verdict |
|---|---|---|---|---|---|
| VAH15s_w3 | +6% / +3% / +2% / +21% / +13% | 0.185/0.238/0.219 ; 0.020/0.040/0.053 ; 0.040/0.040/0.026 (n 150/150/150) | 0.238/0.245/0.232 | n/Y/Y | chance-level |

| line (marginal-in-set) | cut lock 12R: L6M / HOLD / MID / PRE / X' | cut lock OFF: L6M / HOLD / MID / PRE / X' | flag |
|---|---|---|---|
| VAH15s_w3 | +6% / +3% / +2% / +21% / +13% | -1% / -1% / -2% / +10% / +0% | LOCK-ONLY in X' |

## B1. Session-structure lines (Asia H/L, London H/L, overnight H/L, RTH initial balance H/L, prior RTH H/L/C/M, NY lunch H/L, Globex open print, weekly / monthly open, prior week / month, session VWAP and +-1/2 sigma for Asia / London / RTH) - marginal-in-set
Definitions: causal, row exists only after the source window closed (ET minutes: Asia 18:00-02:00, London 02:00-08:30, overnight 18:00-09:30, IB 09:30-10:30, lunch 12:00-13:00; VWAP/sigma = running session volume-weighted (h+l+c)/3 sampled every 900 s from data before the sample); life 24 h (7 d weekly open, 31 d monthly open, 900 s VWAP samples) or first 1-s touch; D = 20 pts nearest fresh ahead; skip/half action as the layer (HALF).
| variant | rows firing D20 | kept removed | maxDD cut L6M / HOLD / MID / PRE / X' | worst-20 PRE b>a / X' b>a | mean d L6M / PRE / X' $k/wk (MDE) | PX gate | S/T/N |
|---|---|---|---|---|---|---|---|
| B1_PDX_rth_L | 536 | 184 | -1% / -0% / -0% / +13% / +8% | -512>-512 ; -342>-334 | +0.0 (1.5) / +0.0 (1.6) / +0.3 (1.0) | pass | n/Y/Y |
| B1_WeekOpen | 58 | -17 | +1% / +1% / +1% / +13% / +6% | -512>-510 ; -342>-332 | +0.0 (0.1) / +1.0 (2.6) / +0.2 (0.6) | pass | Y/Y/Y |
| B1_PDX_rth_M | 1153 | -105 | -0% / -1% / -2% / +10% / +9% | -512>-518 ; -342>-341 | +0.2 (1.2) / +0.7 (2.0) / +0.4 (0.5) | fail | Y/n/Y |
| B1_SVRTH_m2 | 1688 | 37 | +0% / -1% / -1% / +8% / +10% | -512>-490 ; -342>-331 | +0.1 (0.1) / -0.5 (3.3) / +0.4 (0.5) | pass | n/n/Y |
| B1_SVLon_m2 | 1083 | -38 | -3% / +2% / +2% / +10% / +6% | -512>-523 ; -342>-333 | +0.4 (2.0) / -0.1 (1.7) / +0.2 (0.5) | fail | n/n/n |
| B1_SVLon_p1 | 534 | -53 | +1% / -11% / +0% / +14% / +1% | -512>-505 ; -342>-343 | -0.1 (0.6) / +0.5 (1.1) / +0.0 (0.2) | fail | n/n/n |
| B1_SVAsia_m1 | 435 | -27 | -5% / +0% / -6% / +8% / +5% | -512>-515 ; -342>-348 | -0.1 (0.6) / +0.1 (1.4) / +0.5 (1.7) | fail | n/n/n |
| B1_GlobexOpen | 280 | -20 | +1% / +1% / +1% / +12% / +1% | -512>-510 ; -342>-334 | +0.1 (0.3) / +1.0 (2.6) / +0.0 (0.8) | pass | Y/Y/Y |
| B1_AsiaL | 823 | -16 | +2% / +3% / +0% / +3% / +3% | -512>-505 ; -342>-337 | +1.2 (3.1) / +0.3 (0.3) / +0.1 (0.5) | pass | Y/Y/Y |
| B1_ONH | 777 | -14 | +1% / -0% / +0% / -0% / +6% | -512>-512 ; -342>-337 | +0.1 (0.1) / -0.0 (0.3) / +0.2 (0.4) | fail | n/n/Y |
| B1_LunchL | 507 | -7 | -2% / -1% / -1% / +10% / -5% | -512>-512 ; -342>-348 | -0.1 (0.3) / +0.4 (0.9) / -0.2 (0.4) | fail | n/n/n |
| B1_SVLon_m1 | 460 | 7 | +0% / -1% / -2% / +3% / +2% | -512>-505 ; -342>-342 | -0.2 (0.5) / +0.2 (0.5) / +0.1 (0.6) | pass | n/n/n |
| B1_ONL | 526 | -8 | +5% / +0% / +0% / +1% / +5% | -512>-512 ; -342>-332 | +0.2 (0.3) / +0.0 (0.1) / +0.2 (0.5) | fail | Y/n/Y |
| B1_PDX_rth_H | 1146 | 44 | -6% / -1% / +0% / +7% / -1% | -512>-496 ; -342>-340 | -0.2 (0.9) / +0.4 (1.6) / -0.1 (0.7) | fail | n/n/n |
| B1_SVAsia_vwap | 296 | -9 | -32% / +1% / -1% / -1% / +6% | -512>-510 ; -342>-340 | -0.8 (2.4) / -0.0 (0.3) / +0.6 (1.8) | fail | n/n/n |
| B1_LonH | 765 | 0 | -1% / +0% / +0% / +0% / +4% | -512>-513 ; -342>-342 | -0.0 (0.1) / +0.1 (0.2) / +0.1 (0.3) | fail | n/n/n |
| B1_LunchH | 720 | 50 | -3% / +0% / +0% / -0% / +3% | -512>-512 ; -342>-337 | -0.1 (0.2) / -0.1 (0.1) / +0.1 (0.5) | fail | n/n/n |
| B1_SVLon_vwap | 244 | 5 | +0% / +0% / +0% / +1% / +2% | -512>-511 ; -342>-342 | -0.1 (0.7) / +0.1 (0.1) / +0.1 (0.2) | pass | n/n/n |
| B1_SVAsia_p2 | 1199 | -73 | -16% / +28% / +1% / -5% / +8% | -512>-529 ; -342>-341 | -4.4 (9.0) / -0.1 (1.8) / +0.7 (2.2) | fail | n/n/n |
| B1_PDX_rth_C | 229 | 26 | +0% / -1% / +0% / -3% / +5% | -512>-511 ; -342>-337 | +0.0 (0.0) / +0.0 (0.5) / +0.2 (0.4) | fail | n/n/n |
| B1_LonL | 660 | -1 | +3% / +0% / +0% / +0% / +2% | -512>-512 ; -342>-339 | +0.1 (0.2) / -0.1 (0.2) / +0.1 (0.2) | fail | n/n/Y |
| B1_IBH | 846 | -30 | -6% / +3% / +0% / +8% / -6% | -512>-495 ; -342>-344 | -0.2 (0.4) / +0.6 (1.5) / -0.2 (0.4) | fail | n/n/n |
| B1_SVAsia_p1 | 450 | 14 | +1% / -3% / -2% / -2% / +4% | -512>-510 ; -342>-344 | +0.2 (1.0) / -0.2 (0.3) / +0.1 (0.7) | fail | n/n/n |
| B1_IBL | 451 | 53 | -15% / -0% / -0% / +1% / -0% | -512>-515 ; -342>-343 | -0.3 (1.0) / -0.4 (1.0) / -0.0 (0.2) | fail | n/n/n |
| B1_SVRTH_p1 | 1055 | -18 | +0% / +0% / +0% / -4% / +5% | -512>-521 ; -342>-341 | +0.0 (0.1) / -0.1 (0.3) / +0.2 (0.8) | fail | n/n/Y |
| B1_MonthOpen | 3 | 0 | +0% / +0% / +0% / +0% / +0% | -512>-512 ; -342>-342 | +0.0 (0.0) / +0.0 (0.0) / +0.0 (0.0) | fail | n/n/n |
| B1_PDX_month_L | 11 | 0 | +0% / +0% / +0% / +0% / +0% | -512>-512 ; -342>-342 | +0.0 (0.0) / +0.0 (0.0) / +0.0 (0.0) | fail | n/n/n |
| B1_PDX_week_L | 105 | -4 | -1% / +1% / +0% / +0% / -1% | -512>-512 ; -342>-342 | -0.1 (0.3) / -0.0 (0.0) / -0.0 (0.1) | fail | n/n/n |
| B1_PDX_week_H | 264 | 60 | +0% / +0% / +0% / +0% / -1% | -512>-483 ; -342>-343 | -0.0 (0.1) / +0.4 (1.0) / -0.0 (0.0) | fail | n/n/n |
| B1_PDX_month_H | 92 | 0 | +0% / +0% / +0% / -1% / +0% | -512>-512 ; -342>-342 | -0.0 (0.1) / -0.1 (0.1) / +0.0 (0.0) | fail | n/n/n |
| B1_SVAsia_m2 | 1001 | -18 | -3% / -3% / -1% / +2% / -8% | -512>-486 ; -342>-364 | +0.2 (1.2) / +0.3 (1.7) / -0.0 (2.1) | fail | n/Y/Y |
| B1_AsiaH | 1278 | 9 | +9% / -0% / +0% / -1% / -5% | -512>-513 ; -342>-348 | +0.1 (1.1) / +0.0 (0.5) / -0.2 (0.6) | fail | n/n/n |
| B1_SVLon_p2 | 1738 | -16 | -3% / +7% / +1% / +3% / -11% | -512>-474 ; -342>-349 | -0.3 (1.2) / +0.1 (1.2) / -0.4 (1.4) | fail | n/n/n |
| B1_SVRTH_p2 | 2995 | 7 | +2% / -2% / +0% / +1% / -16% | -512>-508 ; -342>-344 | +0.2 (0.3) / +0.5 (1.6) / -0.6 (2.0) | fail | n/Y/Y |
| B1_SVRTH_m1 | 996 | 55 | +1% / +0% / +0% / -10% / -7% | -512>-511 ; -342>-342 | -0.0 (0.2) / -0.3 (1.0) / -0.3 (0.6) | fail | n/n/n |
| B1_SVRTH_vwap | 649 | -3 | +0% / +0% / +0% / -1% / -17% | -512>-512 ; -342>-342 | +0.0 (0.0) / +0.4 (1.4) / -0.7 (1.8) | fail | n/Y/Y |
| B1_PDX_week_O | 154 | 34 | +6% / +0% / +0% / +0% / -19% | -512>-512 ; -342>-344 | -0.2 (0.9) / -0.0 (0.0) / -0.7 (1.8) | fail | n/n/n |

### one-at-a-time
| variant | rows firing D20 | kept removed | maxDD cut L6M / HOLD / MID / PRE / X' | worst-20 PRE b>a / X' b>a | mean d L6M / PRE / X' $k/wk (MDE) | PX gate | S/T/N |
|---|---|---|---|---|---|---|---|
| B1_WeekOpen | 58 | 11 | +0% / -0% / -0% / +14% / -0% | -608>-607 ; -386>-386 | +0.0 (0.1) / +0.6 (3.6) / +0.2 (0.5) | fail | Y/Y/Y |
| B1_GlobexOpen | 280 | 24 | +0% / -0% / -0% / +15% / -1% | -608>-607 ; -386>-382 | +0.1 (0.3) / +0.7 (3.6) / +0.2 (0.7) | fail | Y/Y/Y |
| B1_SVRTH_m2 | 1688 | -57 | +0% / -0% / -0% / +5% / +8% | -608>-601 ; -386>-380 | +0.1 (0.1) / +0.4 (1.8) / +0.2 (0.6) | pass | n/Y/Y |
| B1_SVAsia_vwap | 296 | 0 | -31% / +1% / +1% / +9% / +3% | -608>-606 ; -386>-381 | -0.6 (2.5) / +0.4 (1.3) / +0.1 (0.7) | pass | n/n/n |
| B1_SVLon_vwap | 244 | -53 | +0% / +0% / +0% / +9% / +3% | -608>-610 ; -386>-385 | -0.1 (0.7) / +0.4 (1.2) / +0.1 (0.2) | fail | n/n/n |
| B1_LunchH | 720 | -16 | -3% / +0% / +0% / +9% / +3% | -608>-607 ; -386>-383 | +0.1 (0.5) / -0.1 (1.7) / +0.0 (0.5) | pass | n/n/n |
| B1_SVRTH_p1 | 1055 | -61 | +0% / +0% / +0% / +12% / -3% | -608>-598 ; -386>-386 | +0.0 (0.1) / +0.5 (1.2) / +0.1 (0.8) | fail | n/n/n |
| B1_AsiaL | 823 | -102 | -1% / +3% / +2% / +9% / -1% | -608>-605 ; -386>-386 | +1.1 (3.0) / +0.9 (1.6) / +0.1 (0.5) | fail | Y/Y/Y |
| B1_SVAsia_p2 | 1199 | -65 | -11% / -1% / -2% / +9% / -1% | -608>-574 ; -386>-382 | -1.5 (2.4) / +0.4 (2.0) / +0.1 (0.9) | fail | n/n/n |
| B1_PDX_rth_M | 1153 | 8 | -0% / +3% / +2% / -13% / +20% | -608>-585 ; -386>-371 | -0.5 (4.4) / +0.4 (2.4) / +0.9 (2.0) | fail | n/n/n |
| B1_SVLon_p1 | 534 | 0 | -0% / +6% / +2% / +4% / +1% | -608>-601 ; -386>-387 | -0.2 (0.7) / +0.3 (0.5) / +0.0 (0.2) | fail | n/n/n |
| B1_SVAsia_m1 | 435 | -223 | -4% / +2% / +0% / +3% / +1% | -608>-610 ; -386>-392 | +1.8 (4.9) / +0.3 (2.3) / +0.1 (0.7) | fail | Y/n/Y |
| B1_IBL | 451 | 28 | -13% / -0% / -0% / +1% / +2% | -608>-611 ; -386>-373 | -0.6 (1.6) / -0.1 (0.3) / +0.3 (0.7) | fail | n/n/n |
| B1_LonH | 765 | 4 | -1% / +0% / +0% / -0% / +3% | -608>-609 ; -386>-386 | -0.0 (0.1) / +0.1 (0.2) / -0.0 (0.4) | fail | n/n/n |
| B1_LunchL | 507 | 39 | -2% / -1% / -2% / +0% / +2% | -608>-610 ; -386>-372 | -0.1 (0.3) / -0.0 (0.1) / +0.3 (0.7) | fail | n/n/n |
| B1_AsiaH | 1278 | 47 | +5% / +2% / +2% / -1% / +2% | -608>-603 ; -386>-376 | -0.2 (1.0) / -0.1 (0.3) / +0.1 (0.6) | fail | n/n/n |
| B1_ONH | 777 | 7 | +0% / +2% / +2% / -1% / +2% | -608>-608 ; -386>-386 | +0.1 (0.2) / -0.0 (0.2) / +0.1 (0.4) | fail | n/n/Y |
| B1_PDX_week_H | 264 | -8 | +0% / -5% / -6% / +0% / +0% | -608>-580 ; -386>-386 | -0.0 (0.1) / +0.4 (1.0) / -0.1 (0.1) | fail | n/n/n |
| B1_IBH | 846 | 15 | -1% / +7% / +2% / +3% / -3% | -608>-597 ; -386>-386 | -0.0 (0.1) / +0.1 (0.4) / -0.3 (0.7) | fail | n/n/n |
| B1_PDX_rth_L | 536 | 148 | -13% / +0% / +0% / -4% / +4% | -608>-610 ; -386>-373 | -0.7 (1.6) / -0.0 (2.1) / +0.4 (0.9) | fail | n/n/n |
| B1_MonthOpen | 3 | 0 | +0% / +0% / +0% / +0% / +0% | -608>-608 ; -386>-386 | +0.0 (0.0) / +0.0 (0.0) / +0.0 (0.0) | fail | n/n/n |
| B1_PDX_week_L | 105 | 0 | -1% / +1% / +1% / +0% / +0% | -608>-608 ; -386>-386 | -0.0 (0.1) / -0.0 (0.0) / -0.0 (0.1) | fail | n/n/n |
| B1_PDX_month_L | 11 | 0 | +0% / +0% / +0% / +0% / +0% | -608>-608 ; -386>-386 | +0.0 (0.0) / +0.0 (0.0) / +0.0 (0.0) | fail | n/n/n |
| B1_LonL | 660 | -2 | +0% / +0% / +0% / +0% / -0% | -608>-608 ; -386>-385 | +0.0 (0.0) / -0.1 (0.2) / -0.0 (0.2) | fail | n/n/n |
| B1_ONL | 526 | 0 | +1% / +0% / +0% / +1% / -1% | -608>-607 ; -386>-385 | +0.1 (0.1) / +0.0 (0.2) / +0.1 (0.4) | fail | Y/Y/Y |
| B1_PDX_month_H | 92 | 0 | +0% / +0% / +0% / -1% / +0% | -608>-608 ; -386>-386 | -0.0 (0.1) / -0.0 (0.1) / +0.0 (0.0) | fail | n/n/n |
| B1_SVLon_p2 | 1738 | -31 | -3% / +11% / +2% / -1% / -0% | -608>-569 ; -386>-381 | -0.3 (1.2) / +0.2 (1.4) / -0.2 (1.0) | fail | n/n/n |
| B1_SVLon_m2 | 1083 | 26 | -4% / +3% / +3% / +3% / -6% | -608>-605 ; -386>-395 | +0.8 (2.0) / -0.1 (0.9) / +0.2 (1.1) | fail | n/n/n |
| B1_PDX_rth_H | 1146 | 63 | -1% / -1% / -1% / -8% / +5% | -608>-600 ; -386>-385 | -0.0 (0.7) / -0.9 (2.2) / -0.2 (0.8) | fail | n/n/n |
| B1_SVLon_m1 | 460 | 13 | +0% / -0% / -0% / -0% / -4% | -608>-610 ; -386>-391 | -0.2 (0.5) / -0.1 (0.3) / +0.1 (0.6) | fail | n/n/n |
| B1_SVAsia_p1 | 450 | -14 | +1% / -2% / -2% / -2% / -2% | -608>-606 ; -386>-381 | +0.1 (1.1) / -0.3 (0.4) / +0.2 (0.6) | fail | n/n/n |
| B1_PDX_rth_C | 229 | 158 | +0% / -1% / -1% / -19% / +10% | -608>-608 ; -386>-384 | +0.0 (0.1) / -1.2 (2.2) / +0.4 (1.3) | fail | n/n/n |
| B1_SVRTH_m1 | 996 | 0 | +1% / +0% / +0% / -2% / -9% | -608>-615 ; -386>-386 | -0.0 (0.2) / -0.1 (0.4) / -0.3 (0.6) | fail | n/n/n |
| B1_SVAsia_m2 | 1001 | -36 | -3% / -3% / -4% / -9% / -6% | -608>-581 ; -386>-399 | +0.1 (1.2) / +0.6 (2.4) / -1.5 (3.5) | fail | n/n/n |
| B1_SVRTH_vwap | 649 | -20 | +0% / +0% / +0% / -1% / -28% | -608>-609 ; -386>-386 | +0.0 (0.0) / -0.1 (0.2) / -1.0 (2.9) | fail | n/n/n |
| B1_PDX_week_O | 154 | 41 | +6% / +0% / +0% / -1% / -30% | -608>-608 ; -386>-386 | -0.2 (0.9) / -0.1 (0.1) / -1.1 (2.9) | fail | n/n/n |
| B1_SVRTH_p2 | 2995 | -80 | +1% / -1% / -1% / -3% / -35% | -608>-597 ; -386>-397 | +0.2 (0.2) / +0.4 (2.5) / -1.6 (3.2) | fail | n/n/Y |

### B1 candidates (PX gate pass): placebos and lock frames
| line (marginal-in-set, V13X exact) | maxDD cut L6M / HOLD / MID / PRE / X' | placebo A random-level / B same-volume / C shuffled-day: rank of the cut in L6M ; PRE ; X' (n) | worst-20 rank PRE A/B/C | S/T/N | verdict |
|---|---|---|---|---|---|
| B1_PDX_rth_L | -1% / -0% / -0% / +13% / +8% | 0.672/0.705/0.525 ; 0.213/0.066/0.082 ; 0.033/0.033/0.049 (n 60/60/60) | 0.656/0.541/0.607 | n/Y/Y | chance-level |
| B1_WeekOpen | +1% / +1% / +1% / +13% / +6% | 0.246/0.082/0.180 ; 0.033/0.033/0.016 ; 0.049/0.033/0.016 (n 60/60/60) | 0.082/0.148/0.131 | Y/Y/Y | LEAD (PRE beats 3 placebos; L6M cut 1% < 20% so not RISK-KEEP) |
| B1_GlobexOpen | +1% / +1% / +1% / +12% / +1% | 0.311/0.328/0.410 ; 0.049/0.115/0.098 ; 0.361/0.279/0.230 (n 60/60/60) | 0.459/0.230/0.410 | Y/Y/Y | chance-level |
| B1_AsiaL | +2% / +3% / +0% / +3% / +3% | 0.361/0.328/0.443 ; 0.656/0.393/0.590 ; 0.328/0.279/0.295 (n 60/60/60) | 0.213/0.295/0.164 | Y/Y/Y | chance-level |
| B1_SVRTH_m2 | +0% / -1% / -1% / +8% / +10% | 0.525/0.833/- ; 0.311/0.500/- ; 0.164/0.333/- (n 60/5/0) | 0.131/0.333/- | n/n/Y | chance-level |

| line (marginal-in-set) | cut lock 12R: L6M / HOLD / MID / PRE / X' | cut lock OFF: L6M / HOLD / MID / PRE / X' | flag |
|---|---|---|---|
| B1_PDX_rth_L | -1% / -0% / -0% / +13% / +8% | -3% / -3% / +1% / +1% / -12% | LOCK-ONLY in PRE |
| B1_WeekOpen | +1% / +1% / +1% / +13% / +6% | +0% / +0% / +2% / +2% / +0% | LOCK-ONLY in PRE |
| B1_GlobexOpen | +1% / +1% / +1% / +12% / +1% | +0% / +0% / +2% / -0% / -2% | LOCK-ONLY in PRE |
| B1_AsiaL | +2% / +3% / +0% / +3% / +3% | +1% / +1% / +0% / +3% / +7% | no cut lock-off |
| B1_SVRTH_m2 | +0% / -1% / -1% / +8% / +10% | +0% / +0% / -1% / +6% / +2% | no cut lock-off |
