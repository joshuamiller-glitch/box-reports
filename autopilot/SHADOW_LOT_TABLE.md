# SHADOW_LOT_TABLE - Shadow lot calibration (DIS-AG), BASE-4, 2026-11-04T22:06Z

**A table for the user's lot decision, NOT a recommendation of lots.** Research numbers, nothing live, no PASS. Scope note l2vast/ds3/prereg/DISAG_scope.md sha256 969561f947ac89f648129268252ae48064b9004ff063a3ab97ae6500d4ef46aa (DECISIONS.md, before any number). The SHADOW-2 research lots (1 lot, 2 lots, risk lots min(2400/(stop*20),6)) are not live sizes (MORNING_FLAGS.md); every line below is simulated by FadeHarness (live fill model: signal at the bar close, first fill about 1 s later, 1 lot per 2 s slices, stop slip 2.45, market exit 0.80, fee 0.242 pt/lot; Q1-A ts2 frame; gate_v3 windows with the carrying weeks 2026 W29-W39 dropped in HOLD) on the research trade lists the Shadow code reproduces (diff 0). Code l2vast/ds3/code/disag/ (ag_run.py, ag_doc.py); data /mnt/l2/l2vast/ds3_base4/ag_res.pkl.

**Reference.** The live core stack (Q1-A ts2, ER ladder 0.5/1.0, session lots, zone HALF, A06/B02) earns $27851/wk mean in HOLD, $22571/wk in 2026 and $10856/wk in 2023-25; its HOLD maxDD is -$122025, PRE maxDD -$75057, HOLD worst week -$62576. One reference lot = one lot of a live 60-point-stop book = $1,200 stop risk ($1,249 with the 2.45 stop slip). Equal-risk lots per trade = $1,200 / (stop x $20), integer, minimum 1, cap 6 (the research cap); half = $600 (the "0.5x stack-risk-equivalent" of DIS-T).

**Live lot logic as it applies to a stand-alone Shadow line.** Live books: session lots -> A06 slot halving / B02 quiet-day halving (book- and slot-specific lists) -> ER(20) ladder (x0.5 below 0.30, else x1.0) -> zone HALF (x0.5 with a fresh swing line ahead), sequential rounding, minimum 1 lot. For a line the user sizes with L lots only the ER ladder and the 1-lot minimum are reproducible here (effective lots column); A06/B02 do not exist for a line and zone HALF needs the swing-line layer per signal (not computed; it would lower the effective lots further on the share of rows it flags).

## (a) Risk equivalence: lots at which each line has the same $ stop risk as one lot of the reference live book
| line | status / research size | trades | stop pts median (p10-p90) | $ stop risk per lot (median) | equal-risk lots per trade (mean, cap 6) | integer lots with equal mean $ risk (min 1) | share of signals with ER < 0.30 |
|--|--|--|--|--|--|--|--|
| Q13GAP_T1 | SHADOW-2 (research size 1 lot) | 275 | 30.9 (9.0-79.1) | $617 | 2.57 (uncapped 2.84) | 3 | 63% |
| DISK_BO_CH | SHADOW-2 (research size 2 lots) | 282 | 60.0 (60.0-60.0) | $1200 | 1.00 (uncapped 1.00) | 1 | 61% |
| DISB_PREL | SHADOW-2 (research risk lots min(2400/(stop*20),6)) | 379 | 22.5 (12.0-46.1) | $451 | 2.92 (uncapped 2.94) | 3 | 59% |
| DISE_PDF | SHADOW-2 (research risk lots min(2400/(stop*20),6)) | 317 | 22.7 (12.4-41.8) | $453 | 2.93 (uncapped 2.99) | 3 | 65% |
| DISC_SUN30 | SHADOW-2 (research risk lots min(2400/(stop*20),6)) | 182 | 17.2 (9.7-36.1) | $343 | 3.67 (uncapped 3.78) | 4 | 54% |
| ONRTH | NYAM bundle (1 lot each = 0.5x study) | 543 | 60.0 (60.0-60.0) | $1200 | 1.00 (uncapped 1.00) | 1 | 59% |
| VWAPF | NYAM bundle | 3273 | 60.0 (60.0-60.0) | $1200 | 1.00 (uncapped 1.00) | 1 | 84% |
| ORBF | NYAM bundle | 914 | 60.0 (60.0-60.0) | $1200 | 1.00 (uncapped 1.00) | 1 | 68% |
| NYAM_bundle | NYAM bundle (sum, 1 lot each) | 4730 | 60.0 (60.0-60.0) | $1200 | 1.00 (uncapped 1.00) | 1 | 78% |
| VB2NYPM_T1 | top-3 fade bundle (1 lot) | 523 | 20.7 (11.8-46.8) | $414 | 3.04 (uncapped 3.07) | 3 | 52% |
| PDASIA_T2 | top-3 fade bundle (1 lot) | 317 | 27.3 (11.4-67.3) | $545 | 2.61 (uncapped 2.70) | 3 | 49% |
| VB2NYAM_T3 | top-3 fade bundle (1 lot) | 893 | 28.3 (15.7-53.3) | $567 | 2.33 (uncapped 2.36) | 2 | 69% |
| OR15NYAM_T2 | optional REGIME line (1 lot) | 935 | 53.2 (29.3-105.6) | $1063 | 1.25 (uncapped 1.25) | 1 | 71% |
| N_REL_rev | candidate, not yet a Shadow line | 304 | 28.2 (14.6-52.1) | $563 | 2.42 (uncapped 2.43) | 2 | 50% |

Reading: the 60/60 books (DIS-K, ONRTH, VWAPF, ORBF) are already at one reference lot; the ATR/structure-stop lines (Q13, DIS-B, DIS-E, DIS-C, VB2, PD ASIA, N_REL_rev) carry a stop of 17-30 points, so one lot is 0.3-0.5 reference risk and about 2.3-3.7 lots equal one reference lot. NYAM_bundle is three 60/60 lines (three reference lots of risk when all are open).

## (b) Expected weekly P&L and stack effect at 1 lot and at 0.5x stack-risk-equivalent ($600 per trade; $1,200 shown for reference); naive next to conservative
Conservative = DIS-T estimator (A), winner's-curse deflated: mean - SE x median max of F standard normals, F = the program n_tested (the line's F column). 2026 = label days 2026-01-01..2026-10-30 (all weeks); pre-2026 = 2023-04-03..2025-12-31; HOLD / PRE harness windows (carrying weeks dropped); ALL = 2023-04..2026-10 all weeks; EARLY = PRE + X'. $ per week.
| line | sizing (mean lots) | naive 2026 | naive pre-2026 | naive HOLD | naive ALL | conservative ALL | conservative HOLD | conservative EARLY | F |
|--|--|--|--|--|--|--|--|--|--|
| Q13GAP_T1 | 1 lot (1.00) | +445 | -12 | +136 | +96 | -161 | -560 | -364 | 477 |
| Q13GAP_T1 | 0.5x equal-risk ($600) (1.60) | +475 | -71 | +115 | +57 | -227 | -611 | -434 | 477 |
| Q13GAP_T1 | equal-risk ($1,200) (2.61) | +495 | -108 | +127 | +33 | -367 | -775 | -712 | 477 |
| DISK_BO_CH | 1 lot (1.00) | +336 | +85 | +295 | +145 | -121 | -441 | -265 | 356 |
| DISK_BO_CH | 0.5x equal-risk ($600) (1.00) | +336 | +85 | +295 | +145 | -121 | -441 | -265 | 356 |
| DISK_BO_CH | equal-risk ($1,200) (1.00) | +336 | +85 | +295 | +145 | -121 | -441 | -265 | 356 |
| DISB_PREL | 1 lot (1.00) | +148 | +31 | +189 | +58 | -143 | -303 | -278 | 1338 |
| DISB_PREL | 0.5x equal-risk ($600) (1.52) | +154 | +43 | +191 | +66 | -165 | -305 | -321 | 1338 |
| DISB_PREL | equal-risk ($1,200) (2.93) | +313 | +150 | +350 | +182 | -199 | -349 | -443 | 1338 |
| DISE_PDF | 1 lot (1.00) | +273 | -6 | +158 | +55 | -199 | -612 | -257 | 1216 |
| DISE_PDF | 0.5x equal-risk ($600) (1.51) | +248 | +29 | +116 | +79 | -223 | -687 | -284 | 1216 |
| DISE_PDF | equal-risk ($1,200) (2.92) | +189 | +46 | -14 | +76 | -450 | -1230 | -508 | 1216 |
| DISC_SUN30 | 1 lot (1.00) | +131 | +67 | +60 | +84 | -60 | -309 | -130 | 229 |
| DISC_SUN30 | 0.5x equal-risk ($600) (1.90) | +145 | +86 | +100 | +105 | -85 | -304 | -214 | 229 |
| DISC_SUN30 | equal-risk ($1,200) (3.65) | +325 | +127 | +213 | +183 | -156 | -511 | -417 | 229 |
| ONRTH | 1 lot (1.00) | +731 | +44 | +966 | +193 | -271 | -145 | -651 | 1054 |
| ONRTH | 0.5x equal-risk ($600) (1.00) | +731 | +44 | +966 | +193 | -271 | -145 | -651 | 1054 |
| ONRTH | equal-risk ($1,200) (1.00) | +731 | +44 | +966 | +193 | -271 | -145 | -651 | 1054 |
| VWAPF | 1 lot (1.00) | +1541 | -13 | +1245 | +347 | -430 | -894 | -1105 | 1054 |
| VWAPF | 0.5x equal-risk ($600) (1.00) | +1541 | -13 | +1245 | +347 | -430 | -894 | -1105 | 1054 |
| VWAPF | equal-risk ($1,200) (1.00) | +1541 | -13 | +1245 | +347 | -430 | -894 | -1105 | 1054 |
| ORBF | 1 lot (1.00) | +817 | -545 | +815 | -237 | -870 | -592 | -1655 | 1054 |
| ORBF | 0.5x equal-risk ($600) (1.00) | +817 | -545 | +815 | -237 | -870 | -592 | -1655 | 1054 |
| ORBF | equal-risk ($1,200) (1.00) | +817 | -545 | +815 | -237 | -870 | -592 | -1655 | 1054 |
| NYAM_bundle | 1 lot (1.00) | +3088 | -515 | +3026 | +302 | -894 | -48 | -2590 | 1054 |
| NYAM_bundle | 0.5x equal-risk ($600) (1.00) | +3088 | -515 | +3026 | +302 | -894 | -48 | -2590 | 1054 |
| NYAM_bundle | equal-risk ($1,200) (1.00) | +3088 | -515 | +3026 | +302 | -894 | -48 | -2590 | 1054 |
| VB2NYPM_T1 | 1 lot (1.00) | +274 | +29 | +226 | +86 | -85 | -159 | -222 | 1054 |
| VB2NYPM_T1 | 0.5x equal-risk ($600) (1.60) | +270 | +1 | +244 | +62 | -146 | -165 | -329 | 1054 |
| VB2NYPM_T1 | equal-risk ($1,200) (3.06) | +329 | +36 | +318 | +102 | -248 | -340 | -580 | 1054 |
| PDASIA_T2 | 1 lot (1.00) | +310 | +28 | +367 | +94 | -58 | -44 | -137 | 1054 |
| PDASIA_T2 | 0.5x equal-risk ($600) (1.52) | +314 | +7 | +380 | +78 | -88 | -39 | -177 | 1054 |
| PDASIA_T2 | equal-risk ($1,200) (2.63) | +349 | -20 | +406 | +65 | -158 | -73 | -285 | 1054 |
| VB2NYAM_T3 | 1 lot (1.00) | +207 | +17 | +298 | +65 | -279 | -564 | -442 | 1054 |
| VB2NYAM_T3 | 0.5x equal-risk ($600) (1.28) | +211 | -43 | +308 | +19 | -345 | -565 | -568 | 1054 |
| VB2NYAM_T3 | equal-risk ($1,200) (2.32) | -40 | -300 | +188 | -241 | -811 | -1091 | -1271 | 1054 |
| OR15NYAM_T2 | 1 lot (1.00) | +887 | -134 | +99 | +102 | -791 | -2622 | -1063 | 1054 |
| OR15NYAM_T2 | 0.5x equal-risk ($600) (1.03) | +877 | -133 | +89 | +101 | -795 | -2637 | -1065 | 1054 |
| OR15NYAM_T2 | equal-risk ($1,200) (1.32) | +847 | -183 | +34 | +59 | -891 | -2713 | -1181 | 1054 |
| N_REL_rev | 1 lot (1.00) | +421 | +21 | +460 | +113 | -226 | -582 | -437 | 1338 |
| N_REL_rev | 0.5x equal-risk ($600) (1.31) | +425 | +75 | +464 | +155 | -218 | -579 | -418 | 1338 |
| N_REL_rev | equal-risk ($1,200) (2.43) | +493 | +39 | +651 | +144 | -429 | -764 | -762 | 1338 |

Stack effect (HOLD / PRE, carrying weeks dropped): change in the core stack's maxDD when the line is added at that size ($; POSITIVE = shallower drawdown, the line helps), change in Calmar (mean / |maxDD|), and in the stack's worst week.
| line | sizing | HOLD maxDD change | PRE maxDD change | HOLD Calmar change | PRE Calmar change | HOLD worst week: stack alone -> with line |
|--|--|--|--|--|--|--|
| Q13GAP_T1 | 1 lot | +7987 | -422 | +0.017 | -0.002 | -62576 -> -61640 |
| Q13GAP_T1 | 0.5x equal-risk | +7987 | -611 | +0.017 | -0.002 | -62576 -> -61166 |
| Q13GAP_T1 | equal-risk | +5953 | -1095 | +0.013 | -0.005 | -62576 -> -59903 |
| DISK_BO_CH | 1 lot | -2030 | -1469 | -0.001 | -0.003 | -62576 -> -65083 |
| DISK_BO_CH | 0.5x equal-risk | -2030 | -1469 | -0.001 | -0.003 | -62576 -> -65083 |
| DISK_BO_CH | equal-risk | -2030 | -1469 | -0.001 | -0.003 | -62576 -> -65083 |
| DISB_PREL | 1 lot | +792 | +1439 | +0.003 | +0.004 | -62576 -> -63758 |
| DISB_PREL | 0.5x equal-risk | +792 | +2122 | +0.003 | +0.006 | -62576 -> -63758 |
| DISB_PREL | equal-risk | +1798 | +2350 | +0.006 | +0.009 | -62576 -> -63758 |
| DISE_PDF | 1 lot | -646 | +11 | +0.000 | +0.000 | -62576 -> -61468 |
| DISE_PDF | 0.5x equal-risk | -646 | +2280 | -0.000 | +0.008 | -62576 -> -61468 |
| DISE_PDF | equal-risk | +598 | +3082 | +0.001 | +0.012 | -62576 -> -61468 |
| DISC_SUN30 | 1 lot | +383 | +57 | +0.001 | +0.001 | -62576 -> -63245 |
| DISC_SUN30 | 0.5x equal-risk | +383 | -252 | +0.002 | +0.000 | -62576 -> -63245 |
| DISC_SUN30 | equal-risk | +1683 | -1220 | +0.005 | -0.003 | -62576 -> -63245 |
| ONRTH | 1 lot | +4487 | -981 | +0.017 | -0.002 | -62576 -> -66142 |
| ONRTH | 0.5x equal-risk | +4487 | -981 | +0.017 | -0.002 | -62576 -> -66142 |
| ONRTH | equal-risk | +4487 | -981 | +0.017 | -0.002 | -62576 -> -66142 |
| VWAPF | 1 lot | +13696 | -4986 | +0.040 | -0.017 | -62576 -> -63752 |
| VWAPF | 0.5x equal-risk | +13696 | -4986 | +0.040 | -0.017 | -62576 -> -63752 |
| VWAPF | equal-risk | +13696 | -4986 | +0.040 | -0.017 | -62576 -> -63752 |
| ORBF | 1 lot | -6563 | +1857 | -0.005 | -0.006 | -62576 -> -68591 |
| ORBF | 0.5x equal-risk | -6563 | +1857 | -0.005 | -0.006 | -62576 -> -68591 |
| ORBF | equal-risk | -6563 | +1857 | -0.005 | -0.006 | -62576 -> -68591 |
| NYAM_bundle | 1 lot | +11621 | -1882 | +0.051 | -0.019 | -62576 -> -73841 |
| NYAM_bundle | 0.5x equal-risk | +11621 | -1882 | +0.051 | -0.019 | -62576 -> -73841 |
| NYAM_bundle | equal-risk | +11621 | -1882 | +0.051 | -0.019 | -62576 -> -73841 |
| VB2NYPM_T1 | 1 lot | +758 | +1526 | +0.003 | +0.005 | -62576 -> -62716 |
| VB2NYPM_T1 | 0.5x equal-risk | +758 | +1838 | +0.003 | +0.006 | -62576 -> -62716 |
| VB2NYPM_T1 | equal-risk | +2051 | +2214 | +0.007 | +0.007 | -62576 -> -62754 |
| PDASIA_T2 | 1 lot | +555 | -178 | +0.004 | -0.000 | -62576 -> -62238 |
| PDASIA_T2 | 0.5x equal-risk | +555 | +195 | +0.004 | +0.001 | -62576 -> -62238 |
| PDASIA_T2 | equal-risk | +768 | +484 | +0.005 | +0.002 | -62576 -> -61969 |
| VB2NYAM_T3 | 1 lot | +1730 | +67 | +0.006 | +0.001 | -62576 -> -63207 |
| VB2NYAM_T3 | 0.5x equal-risk | +1730 | -708 | +0.006 | -0.002 | -62576 -> -63207 |
| VB2NYAM_T3 | equal-risk | -457 | -4767 | +0.001 | -0.017 | -62576 -> -63970 |
| OR15NYAM_T2 | 1 lot | -13803 | -13224 | -0.022 | -0.031 | -62576 -> -66194 |
| OR15NYAM_T2 | 0.5x equal-risk | -13803 | -13224 | -0.023 | -0.032 | -62576 -> -66194 |
| OR15NYAM_T2 | equal-risk | -13803 | -14009 | -0.023 | -0.033 | -62576 -> -66194 |
| N_REL_rev | 1 lot | +7225 | +4119 | +0.018 | +0.013 | -62576 -> -63705 |
| N_REL_rev | 0.5x equal-risk | +7225 | +4119 | +0.018 | +0.014 | -62576 -> -63705 |
| N_REL_rev | equal-risk | +10193 | +6742 | +0.027 | +0.023 | -62576 -> -63705 |

## (c) If the user picks L lots per trade: worst week and HOLD-episode loss added
L = fixed lots per trade, re-simulated. "Effective lots" = the mean lots after the live ER ladder with minimum 1 (max(1, floor(L x m + 0.5))); P&L above is at the nominal L (no ladder). Worst week = the lowest weekly P&L of the line alone (all weeks 2023-04..2026-10 / HOLD); HOLD episode = the line's own HOLD peak-to-trough loss; "added to the stack" = change of the stack's HOLD worst week / HOLD maxDD when the line is added (NEGATIVE = deeper).
| line | L | effective lots after ladder | worst week all weeks | worst week HOLD | own HOLD max drawdown | stack HOLD worst week change | stack HOLD maxDD change | weekly mean 2026 / pre-2026 / HOLD |
|--|--|--|--|--|--|--|--|--|
| Q13GAP_T1 | 1 | 1.00 | -3117 | -2643 | -9125 | +936 | +7987 | +445 / -12 / +136 |
| Q13GAP_T1 | 2 | 1.37 | -6324 | -5077 | -17774 | +1697 | +16068 | +893 / -20 / +271 |
| Q13GAP_T1 | 3 | 2.37 | -9525 | -7635 | -27134 | +2208 | +24105 | +1322 / -26 / +363 |
| Q13GAP_T1 | 4 | 2.74 | -12692 | -10093 | -36683 | +2754 | +31646 | +1752 / -32 / +451 |
| Q13GAP_T1 | 6 | 4.11 | -19051 | -14965 | -55608 | +4186 | +46219 | +2574 / -50 / +622 |
| DISK_BO_CH | 1 | 1.00 | -3820 | -3820 | -5133 | -2508 | -2030 | +336 / +85 / +295 |
| DISK_BO_CH | 2 | 1.39 | -7320 | -7320 | -9775 | -4945 | -3684 | +692 / +166 / +605 |
| DISK_BO_CH | 3 | 2.39 | -10626 | -10626 | -14563 | -7208 | -5549 | +1031 / +252 / +898 |
| DISK_BO_CH | 4 | 2.78 | -14146 | -14146 | -19429 | -9561 | -7158 | +1380 / +333 / +1198 |
| DISK_BO_CH | 6 | 4.17 | -21706 | -21706 | -28696 | -14241 | -10232 | +2047 / +491 / +1779 |
| DISB_PREL | 1 | 1.00 | -3922 | -3317 | -5218 | -1182 | +792 | +148 / +31 / +189 |
| DISB_PREL | 2 | 1.41 | -8055 | -6345 | -10116 | -2554 | +1580 | +311 / +55 / +376 |
| DISB_PREL | 3 | 2.41 | -12122 | -9227 | -14594 | -3915 | +2322 | +485 / +82 / +566 |
| DISB_PREL | 4 | 2.82 | -16345 | -12074 | -19012 | -5317 | +3045 | +666 / +110 / +772 |
| DISB_PREL | 6 | 4.23 | -25150 | -18364 | -28614 | -7985 | +4809 | +1016 / +174 / +1162 |
| DISE_PDF | 1 | 1.00 | -3863 | -2917 | -5271 | +1108 | -646 | +273 / -6 / +158 |
| DISE_PDF | 2 | 1.35 | -7696 | -5673 | -10433 | +1582 | -1617 | +552 / -6 / +359 |
| DISE_PDF | 3 | 2.35 | -11284 | -8450 | -15792 | +1871 | -2963 | +851 / -4 / +573 |
| DISE_PDF | 4 | 2.69 | -15138 | -11216 | -20906 | +2005 | -4283 | +1136 / +1 / +796 |
| DISE_PDF | 6 | 4.04 | -22954 | -16611 | -31943 | +1857 | -7585 | +1722 / +18 / +1257 |
| DISC_SUN30 | 1 | 1.00 | -1345 | -1345 | -4271 | -669 | +383 | +131 / +67 / +60 |
| DISC_SUN30 | 2 | 1.46 | -2666 | -2666 | -8273 | -1567 | +785 | +271 / +135 / +136 |
| DISC_SUN30 | 3 | 2.46 | -4011 | -4011 | -12400 | -2485 | +1103 | +393 / +201 / +197 |
| DISC_SUN30 | 4 | 2.92 | -5397 | -5397 | -16626 | -3368 | +1315 | +511 / +264 / +257 |
| DISC_SUN30 | 6 | 4.38 | -8373 | -8373 | -25810 | -5380 | +1326 | +704 / +394 / +326 |
| ONRTH | 1 | 1.00 | -4516 | -3820 | -6838 | -3566 | +4487 | +731 / +44 / +966 |
| ONRTH | 2 | 1.41 | -9067 | -7850 | -13647 | -7596 | +9114 | +1448 / +92 / +1908 |
| ONRTH | 3 | 2.41 | -13539 | -11486 | -20685 | -11232 | +13652 | +2114 / +145 / +2805 |
| ONRTH | 4 | 2.82 | -18060 | -15551 | -28339 | -15297 | +17904 | +2754 / +193 / +3695 |
| ONRTH | 6 | 4.23 | -27012 | -22816 | -41341 | -22562 | +29353 | +4173 / +319 / +5588 |
| VWAPF | 1 | 1.00 | -9129 | -9129 | -13016 | -1176 | +13696 | +1541 / -13 / +1245 |
| VWAPF | 2 | 1.16 | -17963 | -17963 | -26328 | -2296 | +27138 | +3116 / -36 / +2487 |
| VWAPF | 3 | 2.16 | -26962 | -26962 | -40429 | -3031 | +40579 | +4691 / -47 / +3721 |
| VWAPF | 4 | 2.32 | -35706 | -35706 | -54990 | -5425 | +51877 | +6249 / -53 / +4983 |
| VWAPF | 6 | 3.48 | -53334 | -53334 | -84093 | -15703 | +42575 | +9188 / -83 / +7276 |
| ORBF | 1 | 1.00 | -6269 | -6269 | -12791 | -6015 | -6563 | +817 / -545 / +815 |
| ORBF | 2 | 1.32 | -12728 | -12728 | -25039 | -12474 | -12805 | +1604 / -1130 / +1582 |
| ORBF | 3 | 2.32 | -19283 | -19283 | -38042 | -19029 | -19343 | +2304 / -1705 / +2286 |
| ORBF | 4 | 2.65 | -25667 | -25667 | -51334 | -25413 | -28070 | +2974 / -2297 / +2973 |
| ORBF | 6 | 3.97 | -38580 | -38580 | -77623 | -38326 | -51252 | +4327 / -3469 / +4384 |
| NYAM_bundle | 1 | 1.00 | -13968 | -11519 | -23311 | -11265 | +11621 | +3088 / -515 / +3026 |
| NYAM_bundle | 2 | 1.22 | -28172 | -23129 | -46882 | -22875 | +17183 | +6169 / -1074 / +5977 |
| NYAM_bundle | 3 | 2.22 | -41995 | -34053 | -69908 | -33799 | +7284 | +9108 / -1607 / +8812 |
| NYAM_bundle | 4 | 2.44 | -55763 | -45112 | -93579 | -44858 | -16387 | +11977 / -2157 / +11651 |
| NYAM_bundle | 6 | 3.66 | -82960 | -66511 | -140222 | -66257 | -63030 | +17688 / -3233 / +17248 |
| VB2NYPM_T1 | 1 | 1.00 | -2983 | -1688 | -3141 | -141 | +758 | +274 / +29 / +226 |
| VB2NYPM_T1 | 2 | 1.48 | -6067 | -3361 | -6352 | -287 | +1602 | +539 / +62 / +442 |
| VB2NYPM_T1 | 3 | 2.48 | -9180 | -5015 | -9592 | -513 | +2375 | +781 / +93 / +638 |
| VB2NYPM_T1 | 4 | 2.96 | -12298 | -6613 | -12998 | -663 | +3164 | +999 / +130 / +824 |
| VB2NYPM_T1 | 6 | 4.44 | -18800 | -9769 | -19890 | -1250 | +4951 | +1443 / +225 / +1193 |
| PDASIA_T2 | 1 | 1.00 | -3239 | -787 | -2192 | +337 | +555 | +310 / +28 / +367 |
| PDASIA_T2 | 2 | 1.51 | -6507 | -1583 | -4333 | +371 | +900 | +616 / +52 / +728 |
| PDASIA_T2 | 3 | 2.51 | -9766 | -2330 | -6340 | +404 | +1110 | +918 / +74 / +1089 |
| PDASIA_T2 | 4 | 3.02 | -13114 | -3067 | -8272 | +447 | +1350 | +1225 / +95 / +1461 |
| PDASIA_T2 | 6 | 4.53 | -19756 | -4500 | -12390 | +464 | +1975 | +1855 / +138 / +2223 |
| VB2NYAM_T3 | 1 | 1.00 | -3769 | -3005 | -5375 | -631 | +1730 | +207 / +17 / +298 |
| VB2NYAM_T3 | 2 | 1.31 | -7508 | -6151 | -10646 | -1886 | +3459 | +416 / +22 / +567 |
| VB2NYAM_T3 | 3 | 2.31 | -11217 | -9226 | -16276 | -3231 | +5234 | +604 / +17 / +799 |
| VB2NYAM_T3 | 4 | 2.62 | -14736 | -12347 | -22461 | -4956 | +6754 | +776 / +8 / +1015 |
| VB2NYAM_T3 | 6 | 3.93 | -22144 | -18443 | -39114 | -9292 | +8418 | +1063 / -3 / +1348 |
| OR15NYAM_T2 | 1 | 1.00 | -8490 | -8490 | -46980 | -3618 | -13803 | +887 / -134 / +99 |
| OR15NYAM_T2 | 2 | 1.29 | -16901 | -16901 | -95035 | -7456 | -28211 | +1710 / -277 / +150 |
| OR15NYAM_T2 | 3 | 2.29 | -25316 | -25316 | -143405 | -11138 | -52973 | +2521 / -421 / +178 |
| OR15NYAM_T2 | 4 | 2.58 | -33796 | -33796 | -190965 | -14321 | -88855 | +3356 / -561 / +209 |
| OR15NYAM_T2 | 6 | 3.87 | -50992 | -50992 | -285145 | -20815 | -159393 | +5055 / -840 / +299 |
| N_REL_rev | 1 | 1.00 | -3308 | -3308 | -11020 | -1130 | +7225 | +421 / +21 / +460 |
| N_REL_rev | 2 | 1.50 | -6081 | -6081 | -20931 | -2284 | +14226 | +877 / +51 / +962 |
| N_REL_rev | 3 | 2.50 | -8940 | -8940 | -30456 | -3489 | +20771 | +1293 / +82 / +1422 |
| N_REL_rev | 4 | 2.99 | -11911 | -11911 | -40082 | -4428 | +27452 | +1703 / +119 / +1889 |
| N_REL_rev | 6 | 4.49 | -17753 | -17753 | -59627 | -6043 | +41588 | +2538 / +191 / +2809 |

## Lines without a lot choice
* **BT swing-flip:** flag-only (no lots of its own); it flips D7 BT trades, so its size is the BT book's lots. Not tabled.
* **Sizer VT_Q1A and Z3_RVD30:** they scale the LIVE lots by a multiplier (VT m in [0.25, 1.0] down-only, mean lots 1.850 vs Q1-A 2.139 = -13.5%; Z3 m in [0.25, 2.0]); the user's choice is on/off per line, not a lot count (SHADOW_PACK.md section 2; near-miss / watch labels).

## Reading notes and limits (no recommendation)
* The conservative columns are negative or far below the naive ones for most lines: the DIS-T result that a best-of-F selection explains a level at least as large as the observed one carries over (HOLD conservative for the ten DIS-T lines was negative; NYAM/FADE lines use F = 1054, an assumption). The 2026-regime column is the naive in-sample level of the best year; pre-2026 is the out-of-regime comparison (most lines are near zero or negative there; ORBF -545 at 1 lot).
* Lots are linear scalings of a 1-lot series except for the live fill model's 1-lot-per-2-s slicing (harness-simulated at each L); caps: equal-risk lots are capped at 6 and rounded; the per-trade stop of the DIS-B/E/C lines is structural (0.3-3 ATR), so equal-risk lots vary by trade.
* Stack effect is computed on weekly sums with the Q1-A ts2 core stack; correlation with the stack is low for these lines (DIS-T: -0.08 .. +0.06 except Q13 -0.30), so a drawdown reduction in HOLD is partly the 2026 regime hedging the stack's own 2026 drawdown (DIS-T: HOLD_dropH gain much larger than PRE).
* Zone HALF and A06/B02 are not applied (see above); a live implementation would have to define them for a Shadow line. HOLD-episode loss is within HOLD only; PRE / X' episodes (2023-25) are in the stack-effect table (PRE maxDD change).

Note: for the 60/60 lines (DIS-K, ONRTH, VWAPF, ORBF, bundle) the 0.5x equal-risk size ($600) rounds to the 1-lot minimum, so the "1 lot" and "0.5x equal-risk" rows coincide; a line cannot be sized below one lot. Trades column = signals in the research list (the harness takes one position at a time, so VWAPF and the bundle trade fewer than listed).
