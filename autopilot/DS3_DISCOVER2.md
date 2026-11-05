
# DS3_DISCOVER2 - DIS-A (Z3): T-DISCOVER family D1 multi-hour holds and D2 pyramids (rolling)
Shadow only, no PASS claims. Prereg l2vast/ds3/prereg/DIS_A_prereg.md sha256 2280ce04cb18676efffb7d872d6054561e6ef0e68f31f1d6a9a118cbb4cc1945 (DECISIONS.md, before any statistic). Harness FadeHarness, Q1-A ts2 stack, live fill model (first fill +1 s, stop 2.45 / market 0.80 / fee 0.242), equal-$-risk entries ($1,200 per entry), flat by 16:55 ET, gate_v3 carry weeks. Ledger program DIS_A. Rows: FADE_ROWS_DISA.md (when finished).
## INTERIM 1 (2026-11-04 19:14 UTC) - D1 scored, family max-stat and placebos pending
D1 grid: 9 entry sources x session x stop (1/2 ATR15) x time stop (2/4/6 h) x target (none / 2R) = 264 books with >= 30 signals per source-session (all 264 have >= 100 trades); 29 pass the TOLERANT gate; 107 of 264 have a positive L6M mean. Weekly $ at $1,200 risk per entry. Mean of book means by entry source (L6M / HOLD / MID / PRE / X'):
        mean_L6M  mean_HOLD  mean_MID  mean_PRE  mean_X'
source                                                  
L_HM       195.0      696.0     120.0     513.0   -173.0
L_KB      -673.0     -488.0    -842.0     183.0   -410.0
L_MV      -373.0      169.0     173.0      99.0   -628.0
L_PB        -5.0      320.0     471.0     504.0   -132.0
L_PE      -103.0      102.0    -187.0      23.0   -353.0
L_SM       -54.0      159.0     111.0     177.0   -292.0
S_B        -68.0      102.0      -8.0    -502.0   -761.0
S_E        -63.0      193.0    -308.0     104.0   -877.0
S_S       -467.0      -42.0     327.0    -424.0   -447.0
Best 10 by S (mean of the window means L6M, HOLD, MID, PRE, X'); NOT yet family-adjusted:
| book (source|session|stop ATR|tstop h|target) | session | trades | L6M | HOLD | MID | PRE | X' | TOLERANT | stack Calmar gain HOLD / L6M / PRE (1x, carrying weeks not dropped) |
|--|--|--|--|--|--|--|--|--|--|
| S_S|asia|1.0|4|2R | asia | 1499 (280 in L6M) | +1314 | +1230 | +2233 | +89 | -493 | yes | +0.011 / -0.083 / -0.010 |
| L_PB|asia|1.0|4|none | asia | 1096 (255 in L6M) | +1016 | +1345 | +1882 | +807 | -858 | no | -0.015 / +0.054 / -0.018 |
| L_PE|asia|1.0|2|2R | asia | 1877 (470 in L6M) | +1746 | +1545 | +1561 | -58 | -1073 | no | -0.003 / -0.068 / -0.012 |
| L_HM|asia|1.0|6|2R | asia | 1525 (359 in L6M) | +1116 | +1615 | +1076 | +462 | -553 | no | -0.001 / +0.006 / +0.000 |
| L_HM|asia|1.0|4|2R | asia | 1553 (367 in L6M) | +1286 | +1709 | +933 | +343 | -559 | no | -0.000 / +0.010 / +0.004 |
| S_S|asia|1.0|6|2R | asia | 1401 (272 in L6M) | +1543 | +1278 | +1224 | +53 | -605 | yes | +0.010 / -0.083 / -0.001 |
| S_S|nyam|1.0|6|none | nyam | 1003 (148 in L6M) | +6 | +1006 | +3288 | -369 | -491 | no | +0.064 / -0.040 / -0.035 |
| L_PE|asia|1.0|6|2R | asia | 1693 (420 in L6M) | +1767 | +1390 | +452 | +414 | -614 | yes | +0.001 / -0.072 / -0.003 |
| S_E|asia|1.0|4|none | asia | 1099 (208 in L6M) | +383 | +1088 | +1979 | +182 | -233 | yes | +0.000 / -0.088 / -0.006 |
| L_HM|nyam|2.0|6|none | nyam | 1052 (182 in L6M) | +90 | +718 | +1704 | +587 | +299 | no | +0.042 / -0.009 / -0.013 |
Reading so far: the ASIA-entry holds (Asia -> London exit) with a tight 1-ATR stop carry the positives (L6M, HOLD and MID positive, X' negative, PRE flat to positive for some); London-entry and NY-AM-entry holds are net negative in L6M. The Asia-entry result matches the earlier finding that Asia continuation is the live lead. Family max-stat (264 books, 100 worlds x side/days) and 100-draw placebos for the top books are running; D2 (48 pyramid books) follows.


# DS3_DISCOVER2 - section S4b: DIS-C weekend / Sunday-open books - interim 1, 2026-11-04 19:21Z
Prereg autopilot/DIS_C_PREREG.md (sha256 in DECISIONS.md; n_tested 21 + 180 + 28 = 229, FADE-style registration DIS_C in FADE_NTESTED.md); ledger DIS_C; rows autopilot/FADE_ROWS_DISC.md; code l2vast/ds3/code/disc/ (dc_weekend.py, dc_sunday.py, dc_stage2.py, dc_stackasia.py); data /mnt/l2/l2vast/ds3_dc/. Shadow only; no PASS claims. **n is small: 244 weekends 2022-01..2026-10 (183 in the harness era 2023-04..), so a rank correlation needs |rho| >= 0.18 and the weekly-mean MDE of a Sunday cell is about $1.2-1.9k/wk.**
## (a) Does the BTC / MBT weekend move predict the NQ Sunday-open gap and the first hours?
Method note: CME BTC / MBT futures are closed Fri 17:00 - Sun 18:00 ET, so the 'weekend move' is the Friday-close to Sunday-open JUMP, visible at the same 18:00 open as NQ: it is a coincident read of weekend crypto sentiment, not a lead.
| sample | instrument | predictor | target | rho (or rate difference) | p | n | MDE (rho at 80% power) / rates |
|---|---|---|---|---|---|---|---|
| all | mbt | rb | gap_bps | +0.443 | 0.000 | 243 | 0.18 |
| all | mbt | |rb| | |gap_bps| | +0.217 | 0.001 | 243 | 0.18 |
| all | mbt | rb | r30 | +0.115 | 0.074 | 243 | 0.18 |
| all | mbt | |rb| | |r30| | +0.200 | 0.002 | 243 | 0.18 |
| all | mbt | rb | r60 | +0.022 | 0.733 | 243 | 0.18 |
| all | mbt | |rb| | |r60| | +0.136 | 0.034 | 243 | 0.18 |
| all | mbt | rb | r120 | +0.072 | 0.267 | 243 | 0.18 |
| all | mbt | |rb| | |r120| | +0.152 | 0.018 | 243 | 0.18 |
| all | mbt | sign agrees | fill | -0.081 | 0.380 | 167 | agree 0.35 vs disagree 0.43 (n agree 118) |
| all | mbt | sign agrees | go | +0.022 | 0.863 | 167 | agree 0.59 vs disagree 0.57 (n agree 118) |
| all | btc | rb | gap_bps | +0.476 | 0.000 | 242 | 0.18 |
| all | btc | |rb| | |gap_bps| | +0.237 | 0.000 | 242 | 0.18 |
| all | btc | rb | r30 | +0.125 | 0.052 | 242 | 0.18 |
| all | btc | |rb| | |r30| | +0.223 | 0.000 | 242 | 0.18 |
| all | btc | rb | r60 | +0.032 | 0.618 | 242 | 0.18 |
| all | btc | |rb| | |r60| | +0.135 | 0.036 | 242 | 0.18 |
| all | btc | rb | r120 | +0.082 | 0.205 | 242 | 0.18 |
| all | btc | |rb| | |r120| | +0.103 | 0.109 | 242 | 0.18 |
| all | btc | sign agrees | fill | -0.124 | 0.162 | 166 | agree 0.34 vs disagree 0.46 (n agree 116) |
| all | btc | sign agrees | go | +0.035 | 0.733 | 166 | agree 0.59 vs disagree 0.56 (n agree 116) |
| all | - | event | fill | +0.096 | 0.249 | 168 | agree 0.44 vs disagree 0.34 (n agree 62) |
| 2023-04+ | mbt | rb | gap_bps | +0.392 | 0.000 | 182 | 0.21 |
| 2023-04+ | mbt | |rb| | |gap_bps| | +0.223 | 0.003 | 182 | 0.21 |
| 2023-04+ | mbt | rb | r30 | +0.054 | 0.470 | 182 | 0.21 |
| 2023-04+ | mbt | |rb| | |r30| | +0.159 | 0.032 | 182 | 0.21 |
| 2023-04+ | mbt | rb | r60 | -0.035 | 0.634 | 182 | 0.21 |
| 2023-04+ | mbt | |rb| | |r60| | +0.066 | 0.373 | 182 | 0.21 |
| 2023-04+ | mbt | rb | r120 | -0.006 | 0.935 | 182 | 0.21 |
| 2023-04+ | mbt | |rb| | |r120| | +0.095 | 0.204 | 182 | 0.21 |
| 2023-04+ | mbt | sign agrees | fill | -0.098 | 0.320 | 121 | agree 0.35 vs disagree 0.45 (n agree 83) |
| 2023-04+ | mbt | sign agrees | go | +0.074 | 0.549 | 121 | agree 0.63 vs disagree 0.55 (n agree 83) |
| 2023-04+ | btc | rb | gap_bps | +0.442 | 0.000 | 181 | 0.21 |
| 2023-04+ | btc | |rb| | |gap_bps| | +0.228 | 0.002 | 181 | 0.21 |
| 2023-04+ | btc | rb | r30 | +0.085 | 0.253 | 181 | 0.21 |
| 2023-04+ | btc | |rb| | |r30| | +0.185 | 0.013 | 181 | 0.21 |
| 2023-04+ | btc | rb | r60 | -0.010 | 0.895 | 181 | 0.21 |
| 2023-04+ | btc | |rb| | |r60| | +0.066 | 0.378 | 181 | 0.21 |
| 2023-04+ | btc | rb | r120 | +0.024 | 0.747 | 181 | 0.21 |
| 2023-04+ | btc | |rb| | |r120| | +0.050 | 0.502 | 181 | 0.21 |
| 2023-04+ | btc | sign agrees | fill | -0.110 | 0.310 | 120 | agree 0.35 vs disagree 0.46 (n agree 83) |
| 2023-04+ | btc | sign agrees | go | +0.086 | 0.423 | 120 | agree 0.63 vs disagree 0.54 (n agree 83) |
| 2023-04+ | - | event | fill | +0.102 | 0.269 | 122 | agree 0.44 vs disagree 0.33 (n agree 62) |
**Plain sentence:** the MBT / BTC weekend jump is strongly related to the NQ weekend gap (rho +0.44 / +0.48, p < .001; coincident) and its size to the NQ gap size and to the absolute return in the first 30 minutes (rho ~ +0.2, p .002), but its SIGN does not predict the direction of NQ over the next 30-120 minutes (rho +0.12 at 30 min in the full sample, p .05-.07, and +0.05 to +0.09 (p .25-.47) in 2023-04+; about 0 at 60 and 120 min), and it does not change whether the gap fills (fill rate 35% when the crypto jump agrees with the NQ gap vs 43% when it disagrees, p .38) or goes (58% unconditional). A weekend event on the Monday (CAL calendar) shows fill 44% vs 34% (p .25, 62 of 168 weekends): no significant conditioner. BH q <= .10 survivors among the 21 tests: mbt rb vs gap_bps (q 0.000), mbt |rb| vs |gap_bps| (q 0.003), mbt |rb| vs |r30| (q 0.006), mbt |rb| vs |r60| (q 0.083), mbt |rb| vs |r120| (q 0.053), btc rb vs gap_bps (q 0.000), btc |rb| vs |gap_bps| (q 0.001), btc |rb| vs |r30| (q 0.002), btc |rb| vs |r60| (q 0.083).
## (b) NQ Sunday 18:00-20:00 ET as its own session family (180 cells; live fill model; one trade per weekend)
Screen: 180 cells, NOW-ONLY 39, TOLERANT 21, STRICT 1, gate_v2a 9. By gate and direction:
| gate | direction | cells | median trades | median L6M | median HOLD | median PRE | NOW-ONLY | TOLERANT |
|---|---|---|---|---|---|---|---|---|
| G+ | against | 36 | 83 | -211 | -133 | -107 | 2 | 0 |
| G+ | with | 24 | 96 | -46 | -196 | -75 | 6 | 2 |
| G- | against | 36 | 94 | -278 | -159 | -207 | 1 | 0 |
| G- | with | 24 | 84 | +101 | -8 | -52 | 17 | 10 |
| none | against | 36 | 180 | -583 | -336 | -302 | 1 | 0 |
| none | with | 24 | 183 | +183 | -323 | -31 | 12 | 9 |
Best 10 by L6M (trades, $/wk):
| entry (min after open) | direction | stop ATR | target | time stop | gate | trades | L3M | L6M | HOLD | MID | PRE | X' | L6M MDE | gate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 30 | with | 1.0 | R2 | 120 | none | 183 | +679 | +869 | +472 | +737 | +218 | -2 | +1824 | TOLERANT |
| 30 | with | 1.0 | R2 | 120 | G+ | 96 | +332 | +855 | +352 | +795 | +123 | -89 | +1296 | TOLERANT |
| 30 | with | 1.0 | R2 | 60 | none | 183 | +817 | +793 | +424 | +699 | +190 | +5 | +1740 | STRICT |
| 30 | with | 1.0 | R2 | 60 | G+ | 96 | +504 | +747 | +287 | +757 | +134 | -102 | +1249 | TOLERANT |
| 15 | with | 1.0 | R2 | 120 | none | 180 | +559 | +714 | +186 | +282 | +110 | -332 | +1936 | TOLERANT |
| 30 | with | 0.5 | R2 | 60 | none | 183 | +644 | +513 | -268 | -1417 | +109 | -201 | +1436 | TOLERANT |
| 30 | with | 0.5 | R2 | 120 | none | 183 | +644 | +513 | -268 | -1417 | +109 | -220 | +1436 | TOLERANT |
| 5 | with | 0.5 | R2 | 60 | G- | 83 | +53 | +474 | +264 | +106 | -223 | -71 | +1064 | NOW-ONLY |
| 5 | with | 0.5 | R2 | 120 | G- | 83 | +53 | +474 | +264 | +106 | -223 | -71 | +1064 | NOW-ONLY |
| 15 | with | 1.0 | R2 | 120 | G- | 84 | +725 | +448 | +190 | -301 | +45 | -75 | +1510 | TOLERANT |
Shuffled-weekend placebo (entries moved to another Sunday, 100 draws) and the harness placebos for the 39 NOW-ONLY cells are in FADE_ROWS_DISC.md. **Family max-T over all 180 cells (100 worlds, random-side and shuffled-weekend): HOLD mean family p 0.95 / 0.81, L6M Calmar family p 0.94 / 0.98: the best Sunday cell cannot be told from the best-of-180 chance maximum.** The leading cell is the WITH-trend continuation entered 30 minutes after the open with a 1.0 ATR stop and a 2R target (183 trades: L6M +0.8-0.9k/wk, HOLD +0.4-0.5k, MID +0.7k, PRE +0.2k, X' 0; TOLERANT, harness placebo p .17-.18, shuffled-weekend p .02-.03, stack Calmar gain +0.01 HOLD / +0.07 L6M): within the weekly MDE of about $1.7k, thin, and REGIME-labelled where CAL's R_F40 ON state gives ON-state PRE +4 / X' +35 $/wk, i.e. about 0; the AGAINST (gap-fade / P0 gap-fill) shapes are negative in the median (L6M -0.6k) - the 'gap and go' side of the Sunday open pays slightly more than the fade. The MBT-jump gates (G+ / G-) do not improve the cells they were meant to condition.
## (c) The live stack's Asia cell on Monday / Tuesday label days conditioned on the preceding weekend's MBT jump (28 tests)
| day | series | predictor | rho | p | n | MDE |
|---|---|---|---|---|---|---|
| Mon | ALL | rb | -0.016 | 0.833 | 182 | 0.21 |
| Mon | ALL | |rb| | +0.079 | 0.292 | 182 | 0.21 |
| Tue | ALL | rb | -0.011 | 0.886 | 182 | 0.21 |
| Tue | ALL | |rb| | -0.047 | 0.530 | 182 | 0.21 |
**Plain sentence:** 0 of 28 tests reach p <= .05 (smallest p 0.19; MDE |rho| 0.21 at n = 182): the BTC / MBT weekend state does not explain the stack's Monday or Tuesday Asia P&L (Monday Asia total mean +$2.9k/day by rb tercile: low +4.7k, middle +0.4k, high +3.7k; Tuesday +1.1k / +5.1k / +2.4k), so the FRAGILE Mon-Tue 19:00 continuation (CAL) is not rescued by this conditioner.
## Verdict and next
DIS-C finds one coincident relationship (crypto jump <-> NQ gap, and size <-> early volatility) and no tradable one: no sign predictor, no gap-fill conditioner, no Sunday-open cell that survives the family null, no stack-Asia conditioning. The Sunday 18:30 continuation with a 2R target is the only WATCH-level cell (thin, inside its MDE). Not a lead.

## DIS-G: GLOBEX WEEKDAY OPEN / ASIA / LONDON OPEN STRUCTURE BOOKS (S4a; interim table 2026-11-04 22:35Z; prereg autopilot/DIS_G_PREREG.md sha256 b9670af2...a3142; ledger DIS_G; rows FADE_ROWS_DISG.md)
Question: do the Globex weekday 18:00 open gap, the Asia and London opening ranges, the Asia-range breaks / failed breaks during 02:00-04:00, the London-open stretch from the Asia VWAP and the 03:00 Frankfurt-open move trade as books (session families asia and london)? 28 event variants x shapes = 627 cells valued (525 with >= 100 trades); FadeHarness live fill model, costs stop 2.45 / exit 0.80 / fee 0.242, base Q1-A ts2 stack for marginal values. Post-hoc, Shadow only, no PASS claims; S4b's DIS-C (weekend / Sunday open) is separate.
Stage 1: share of cells with L6M > 0 = 0.27, HOLD > 0 = 0.20, both L3M, L6M and HOLD > 0: 54 cells (31 Asia family, 23 London family). Placebo p <= 0.10: 29 of 54. Family max-T test over all 525 cells: HOLD_mean: family p of the real max side 0.634 / days 0.149; L6M_calmar: family p of the real max side 0.574 / days 0.693.
Ranked table (placebo p, then L6M; first 25 of 54; labels per FADE_ROWS rules, nothing here is a lead until the family test and the carrying-week checks are read):

| book | session | anchor | trigger | shape | L1M | L3M | L6M | HOLD | MID | PRE | X' | regime-conditioned | placebo | stack gain | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=0.50ATR T120m | +1218 | +968 | +1166 | +839 | -157 | -90 | -580 | ON L6M +1166 / HOLD +864 / MID -157 (n 127); 2023-25 same switch PRE -16 / X' -214 (n 51) | p 0.010 | 0.5x HOLD +0.012 / L6M +0.039; 1.0x HOLD +0.026 / L6M +0.082 | NOW-ONLY REGIME [family maxT p 0.95/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=0.50ATR T60m | +1218 | +889 | +1011 | +786 | -177 | -151 | -557 | ON L6M +1011 / HOLD +810 / MID -177 (n 127); 2023-25 same switch PRE +8 / X' -156 (n 51) | p 0.010 | 0.5x HOLD +0.012 / L6M +0.037; 1.0x HOLD +0.025 / L6M +0.078 | NOW-ONLY REGIME [family maxT p 0.99/1.00] |
| DIS_G trend | london | AR | L_AR_brk_x0.25 | tgt=r1 stop=0.25ATR T30m | +1259 | +732 | +1016 | +410 | -463 | -409 | -403 | ON L6M +1016 / HOLD +251 / MID -463 (n 308); 2023-25 same switch PRE -126 / X' -143 (n 191) | p 0.020 | 0.5x HOLD +0.006 / L6M -0.009; 1.0x HOLD +0.013 / L6M -0.018 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.25_any | tgt=r1 stop=0.50ATR T120m | +1760 | +1402 | +1481 | +1161 | +323 | -471 | -340 | ON L6M +1481 / HOLD +1259 / MID +323 (n 213); 2023-25 same switch PRE +31 / X' -85 (n 101) | p 0.030 | 0.5x HOLD +0.012 / L6M +0.040; 1.0x HOLD +0.024 / L6M +0.083 | NOW-ONLY REGIME [family maxT p 0.63/0.98] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.25_any | tgt=r1 stop=1.00ATR T120m | -42 | +464 | +1121 | +1015 | +80 | -206 | -171 | ON L6M +1121 / HOLD +1076 / MID +80 (n 213); 2023-25 same switch PRE +84 / X' -95 (n 101) | p 0.030 | 0.5x HOLD +0.010 / L6M -0.020; 1.0x HOLD +0.021 / L6M -0.039 | NOW-ONLY REGIME [family maxT p 0.84/1.00] |
| DIS_G trend | london | AR | L_AR_brk_x0.25 | tgt=r1 stop=0.25ATR T120m | +674 | +263 | +790 | +295 | -300 | -486 | -372 | ON L6M +790 / HOLD +136 / MID -300 (n 308); 2023-25 same switch PRE -126 / X' -117 (n 191) | p 0.030 | 0.5x HOLD +0.008 / L6M -0.011; 1.0x HOLD +0.016 / L6M -0.020 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G trend | london | AR | L_AR_brk_x0.25 | tgt=r1 stop=0.25ATR T60m | +674 | +263 | +790 | +295 | -300 | -486 | -372 | ON L6M +790 / HOLD +136 / MID -300 (n 308); 2023-25 same switch PRE -126 / X' -117 (n 191) | p 0.030 | 0.5x HOLD +0.008 / L6M -0.011; 1.0x HOLD +0.016 / L6M -0.020 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.25_any | tgt=r1 stop=0.50ATR T60m | +1760 | +1535 | +1428 | +1142 | +243 | -553 | -342 | ON L6M +1428 / HOLD +1239 / MID +243 (n 213); 2023-25 same switch PRE +64 / X' -64 (n 101) | p 0.040 | 0.5x HOLD +0.011 / L6M +0.038; 1.0x HOLD +0.024 / L6M +0.079 | NOW-ONLY REGIME [family maxT p 0.64/0.98] |
| DIS_G trend | london | AR | L_AR_brk_x0.25 | tgt=r2 stop=0.25ATR T30m | +2722 | +1634 | +1253 | +135 | -837 | -495 | -526 | ON L6M +1253 / HOLD +130 / MID -837 (n 308); 2023-25 same switch PRE -228 / X' -272 (n 191) | p 0.040 | 0.5x HOLD +0.006 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=0.50ATR T30m | +1218 | +867 | +822 | +681 | -77 | -41 | -603 | ON L6M +822 / HOLD +705 / MID -77 (n 127); 2023-25 same switch PRE +50 / X' -112 (n 51) | p 0.040 | 0.5x HOLD +0.008 / L6M +0.035; 1.0x HOLD +0.016 / L6M +0.073 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=1.00ATR T120m | -569 | +252 | +801 | +695 | +104 | -112 | -455 | ON L6M +801 / HOLD +699 / MID +104 (n 127); 2023-25 same switch PRE +39 / X' -220 (n 51) | p 0.040 | 0.5x HOLD +0.011 / L6M -0.022; 1.0x HOLD +0.023 / L6M -0.042 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.25_any | tgt=r1 stop=0.25ATR T30m | -477 | +1016 | +745 | +761 | +1085 | -159 | -431 | ON L6M +745 / HOLD +863 / MID +1085 (n 206); 2023-25 same switch PRE -27 / X' -82 (n 100) | p 0.050 | 0.5x HOLD +0.008 / L6M +0.030; 1.0x HOLD +0.017 / L6M +0.062 | NOW-ONLY REGIME [family maxT p 0.99/1.00] |
| DIS_G trend | london | AR | L_AR_brk_x0.0 | tgt=r1 stop=1.00ATR T30m | +453 | +1511 | +640 | +391 | +547 | -95 | -1112 | ON L6M +640 / HOLD +491 / MID +547 (n 320); 2023-25 same switch PRE -108 / X' -688 (n 198) | p 0.050 | 0.5x HOLD +0.009 / L6M +0.009; 1.0x HOLD +0.018 / L6M +0.019 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=0.25ATR T30m | -35 | +774 | +603 | +521 | +470 | -6 | -460 | ON L6M +603 / HOLD +557 / MID +470 (n 121); 2023-25 same switch PRE -5 / X' -90 (n 51) | p 0.050 | 0.5x HOLD +0.009 / L6M +0.032; 1.0x HOLD +0.018 / L6M +0.068 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G trend | london | AR | L_AR_brk_x0.25 | tgt=r1 stop=0.50ATR T120m | +936 | +483 | +875 | +62 | -702 | -454 | -767 | ON L6M +875 / HOLD +18 / MID -702 (n 308); 2023-25 same switch PRE -108 / X' -418 (n 191) | p 0.059 | 0.5x HOLD +0.005 / L6M +0.011; 1.0x HOLD +0.010 / L6M +0.022 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.25_any | tgt=r1 stop=0.25ATR T120m | -477 | +1066 | +778 | +648 | +711 | -163 | -427 | ON L6M +778 / HOLD +750 / MID +711 (n 206); 2023-25 same switch PRE -16 / X' -160 (n 100) | p 0.059 | 0.5x HOLD +0.007 / L6M +0.030; 1.0x HOLD +0.015 / L6M +0.063 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.25_any | tgt=r1 stop=0.25ATR T60m | -477 | +951 | +723 | +641 | +688 | -234 | -391 | ON L6M +723 / HOLD +742 / MID +688 (n 206); 2023-25 same switch PRE -9 / X' -119 (n 100) | p 0.059 | 0.5x HOLD +0.007 / L6M +0.030; 1.0x HOLD +0.015 / L6M +0.063 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G trend | london | AR | L_AR_brk_x0.25 | tgt=r1 stop=0.50ATR T60m | +936 | +483 | +875 | +62 | -702 | -454 | -767 | ON L6M +875 / HOLD +18 / MID -702 (n 308); 2023-25 same switch PRE -108 / X' -418 (n 191) | p 0.069 | 0.5x HOLD +0.005 / L6M +0.011; 1.0x HOLD +0.010 / L6M +0.022 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=0.25ATR T120m | -35 | +840 | +644 | +412 | +95 | -37 | -427 | ON L6M +644 / HOLD +448 / MID +95 (n 121); 2023-25 same switch PRE -75 / X' -168 (n 51) | p 0.069 | 0.5x HOLD +0.008 / L6M +0.033; 1.0x HOLD +0.017 / L6M +0.069 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=1.00ATR T60m | -221 | +384 | +630 | +615 | +307 | -115 | -456 | ON L6M +630 / HOLD +618 / MID +307 (n 127); 2023-25 same switch PRE +62 / X' -103 (n 51) | p 0.069 | 0.5x HOLD +0.008 / L6M -0.014; 1.0x HOLD +0.017 / L6M -0.027 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=1.00ATR T30m | -413 | +157 | +581 | +693 | +592 | -30 | -449 | ON L6M +581 / HOLD +696 / MID +592 (n 127); 2023-25 same switch PRE +78 / X' -30 (n 51) | p 0.069 | 0.5x HOLD +0.007 / L6M -0.009; 1.0x HOLD +0.015 / L6M -0.019 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.25_any | tgt=r1 stop=1.00ATR T30m | -280 | +319 | +1028 | +1100 | +627 | -231 | -198 | ON L6M +1028 / HOLD +1097 / MID +627 (n 213); 2023-25 same switch PRE +83 / X' +80 (n 101) | p 0.079 | 0.5x HOLD +0.007 / L6M -0.005; 1.0x HOLD +0.014 / L6M -0.011 | NOW-ONLY CONDITIONAL [family maxT p 0.71/1.00] |
| DIS_G fade | asia | GAPFILL | A_GAPFILL_t01_g0.5_any | tgt=r1 stop=0.25ATR T60m | -35 | +694 | +574 | +397 | +72 | -53 | -412 | ON L6M +574 / HOLD +433 / MID +72 (n 121); 2023-25 same switch PRE -44 / X' -127 (n 51) | p 0.079 | 0.5x HOLD +0.008 / L6M +0.033; 1.0x HOLD +0.017 / L6M +0.069 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G trend | london | AR | L_AR_brk_x0.0 | tgt=r1 stop=1.00ATR T60m | -731 | +1030 | +471 | +300 | +614 | -267 | -1144 | ON L6M +471 / HOLD +410 / MID +614 (n 320); 2023-25 same switch PRE -198 / X' -669 (n 198) | p 0.079 | 0.5x HOLD +0.007 / L6M +0.004; 1.0x HOLD +0.015 / L6M +0.008 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_G trend | london | AR | L_AR_brk_x0.0 | tgt=r1 stop=0.50ATR T30m | +660 | +840 | +383 | +140 | -558 | -672 | -655 | ON L6M +383 / HOLD +146 / MID -558 (n 320); 2023-25 same switch PRE -245 / X' -366 (n 198) | p 0.079 | 0.5x HOLD +0.004 / L6M +0.020; 1.0x HOLD +0.009 / L6M +0.041 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |

Reading (S4a, DIS-G final; post-hoc, Shadow only): 627 cells valued, 525 with >= 100 trades, 54 candidates (L3M, L6M, HOLD > 0), 29 with placebo p <= .10, every candidate labelled NOW-ONLY (PRE and X' negative for all; MID negative for many) and almost all REGIME. Family max-T over the 525 cells: HOLD mean p 0.63 (side) / 0.15 (days), L6M Calmar p 0.57 / 0.69: the best Asia / London opening book is what chance gives. The leading raw-p cells (A_GAPFILL_t01 g0.25-0.5 fills of the Globex weekday open gap, +$1.0-1.5k per week in L6M; L_AR_brk_x0.25 Asia-range breaks, +$0.8-1.0k) are 2026-only effects: no lead. DIS-G closes; Sunday-evening open books are S4b's DIS-C.

## DIS-U INTERIM 1 (ZL-1, 2026-11-04 ~22:10Z; RE-APPENDED ZL-1 after the file overwrite; condensed from the original) - REGIME EPISODE HISTORY AND DURATION
Prereg l2vast/ds3/prereg/DISU_prereg.md sha256 be47bffe3f8797ec07941cf1b684b2c4c9de20a24be6241ddb3064e709aee670 (logged first); dead_lookup first (no scored regime-duration cell); ledger DIS_U 20 rows; n_tested FADE_DISU 52. Code l2vast/ds3/code/disu/, output /mnt/l2/l2vast/ds3_disu/ (h1_log.txt, h234_log.txt). No PASS claim.
Data limit: earliest NQ tick/L2 date on disk 2023-02-09; daily series 2023-04-03..2026-10-30 (935 days). (DIS-W later found 1-min NQ back to 2013 on disk; see DS3_HISTORY_EXTENSION.md.) Prereg note: the A2 formula in the prereg text has a stray factor 5; A2 = sum(R_k^2)/sum(r^2), 1 = random walk.
H1: multiple mean-shift (exact DP, min segment 60 d, K<=4, BIC): BIC K=0/1/2/3/4 = 15,743.9/15,735.7/15,741.0/15,751.9/15,758.3, one shift. Bundle S1 (study lots 2; live 0.5x): 2023-04-03..2026-02-09 (746 d) -224 $/day (live -112); 2026-02-10..10-30 (189 d) +1,481 (live +740), Welch t 4.48; MAP 2026-02-10, median 2025-11-27, 90% 2025-06-13..2026-02-12. HMM: one switch 2025-11-20, ON absorbing (means -249/+1,196). K=2 (not selected) front-loads the episode (+2,844 to 2026-05-04, then +847). No earlier episode: 11 non-overlapping 60-day windows before 2026 have t between -1.44 and +0.97. Detection probability of the 2026 step (1,705 $/day) for 40/60/90 days: 0.65/0.82/0.94. ES, RTY, YM bundles: no shift. Live NY-AM sleeve S2: no shift, inside 187 vs outside 774 $/day (t -1.57).
H2: first-hour share shifts up 2025-12-02 (t +3.30, agrees); gap-fill A3 shifts DOWN 2025-10-20 (.62 to .48, t -2.69, opposite to a gap-fill signature); OR-break S3 .894 to .813 (n.s.); lag-1 autocorrelation 10-11h A1 and VR(5) A2: no shift (inside -0.013 vs -0.004; .966 vs 1.016). 1 of 5 directional series agrees; shifted-label placebo P(>=1) = .15.
H3 (exact Garwood): 0 ends in 189 ON days -> mean ON duration >= 63 d (90%) / 51 d (95%), no upper bound; OFF: 1 completed stretch 746 d (left-censored), start-rate 90% interval [0.00007, 0.00636]/day. P(still ON after D more days) at the 95%-upper hazard: D=21/63/126/252 -> .72/.37/.14/.02; at the point hazard 1/189: .89/.72/.51/.26.
H4 (bundle at 0.5x; always-on $56,470 total; HOLD $2,786/wk, maxDD $23,311; PRE -$1,038/wk, maxDD $88,036): total gated $: weekly CUSUM k.4 h3/h4/h5 110,132/133,272/115,326 (false-ON days 195/196/16; the h3/h4 false alarm of 2025-05-12 never switched off); daily CUSUM k.2 h4/h5 86,535/68,649; R_F20 95,119; R_F40 109,407; R_F40ANY 81,672; R_AND 16,910. Only weekly h5 and R_F40 beat a circularly shifted copy on total (p .012); none beats it on Calmar (p .10-.50): the gain is mostly "being off in the long losing stretch". PRE maxDD gated: weekly h5 0 (not trading), R_F40 $30k, R_F20 $30k vs $88k always-on.
Break-even: live-size ON +$740/day, OFF -$112/day. Gating beats always-on iff lag x 740 < OFF-stretch x 112 x (1 - false-ON share); required OFF stretch: lag 9 d (R_F20) 59 d; lag 27 d (R_F40) 178 d (292 d with its 39% false-ON); lag 56-61 d (weekly CUSUM) 370-403 d. The one OFF stretch seen was 746 d.
Plain sentence: the NQ NY-AM reversion regime has occurred once in the 3.6 years of data then on disk (bundle shift 2026-02-10, 90% 2025-06..2026-02), no earlier episode of that size exists in 2023-04..2025-11, its duration cannot be bounded above from one censored episode (exact lower bound about 2-3 months), the 5-minute lag-1 and VR(5) statistics do not show it, and the causal switches earn their keep mostly by being OFF in the long losing stretch.

## DIS-B: GLOBEX PRE-MARKET STRUCTURE BOOKS (S4a; interim table 2026-11-04 22:36Z; prereg autopilot/DIS_B_PREREG.md sha256 f8cf86b8...c4563; ledger DIS_B; rows FADE_ROWS_DISB.md)
Question: do the Globex pre-market (04:00-09:30 ET) range / volume / VWAP / 08:30-release / pre-open structures trade as books, either with entries after 09:30 (N family, session nyam) or as pre-market entries (P family, flat by 09:25)? 61 event variants x shapes = 1341 cells valued (1338 with >= 100 trades); FadeHarness live fill model, costs stop 2.45 / exit 0.80 / fee 0.242, base Q1-A ts2 stack for marginal values. Post-hoc, Shadow only, no PASS claims.
Stage 1: share of cells with L6M > 0 = 0.39, HOLD > 0 = 0.30, both L3M, L6M and HOLD > 0: 157 cells (140 N family, 17 P family). Placebo p <= 0.10: 14 of 157. Family max-T test over all 1338 cells: HOLD_mean: family p of the real max side 0.406 / days 0.168; L6M_calmar: family p of the real max side 0.426 / days 0.495.
Ranked table (placebo p, then L6M; first 25 of 157; labels per FADE_ROWS rules, nothing here is a lead until the family test and the carrying-week checks are read):

| book | session | anchor | trigger | shape | L1M | L3M | L6M | HOLD | MID | PRE | X' | regime-conditioned | placebo | stack gain | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=mid stop=1.00ATR T60m | +73 | +322 | +1404 | +1207 | +195 | +144 | -550 | ON L6M +1404 / HOLD +993 / MID +195 (n 156); 2023-25 same switch PRE -120 / X' -507 (n 91) | p 0.010 | 0.5x HOLD +0.025 / L6M +0.002; 1.0x HOLD +0.056 / L6M +0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=mid stop=1.00ATR T120m | +73 | +322 | +1275 | +1165 | +305 | +216 | -550 | ON L6M +1275 / HOLD +951 / MID +305 (n 156); 2023-25 same switch PRE -127 / X' -507 (n 91) | p 0.010 | 0.5x HOLD +0.026 / L6M +0.002; 1.0x HOLD +0.056 / L6M +0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | pre | REL | P_REL_cont_m1.0 | tgt=r1 stop=1.00ATR T30m | +367 | +911 | +410 | +707 | +850 | +298 | +517 | ON L6M +410 / HOLD +515 / MID +850 (n 188); 2023-25 same switch PRE +265 / X' +289 (n 116) | p 0.059 | 0.5x HOLD +0.008 / L6M +0.014; 1.0x HOLD +0.016 / L6M +0.028 | TOLERANT CONDITIONAL [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_hi | tgt=mid stop=1.00ATR T60m | -890 | +108 | +581 | +1168 | +825 | -151 | -690 | ON L6M +581 / HOLD +997 / MID +825 (n 122); 2023-25 same switch PRE -85 / X' -373 (n 61) | p 0.069 | 0.5x HOLD +0.031 / L6M -0.021; 1.0x HOLD +0.070 / L6M -0.041 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_hi | tgt=mid stop=1.00ATR T120m | -890 | +108 | +452 | +1101 | +825 | -80 | -690 | ON L6M +452 / HOLD +930 / MID +825 (n 122); 2023-25 same switch PRE -91 / X' -373 (n 61) | p 0.069 | 0.5x HOLD +0.031 / L6M -0.021; 1.0x HOLD +0.070 / L6M -0.041 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | pre | REL | P_REL_cont_m1.0 | tgt=r2 stop=1.00ATR T30m | +12 | +935 | +284 | +663 | +801 | +197 | -82 | ON L6M +284 / HOLD +442 / MID +801 (n 188); 2023-25 same switch PRE +332 / X' +46 (n 116) | p 0.069 | 0.5x HOLD +0.009 / L6M -0.016; 1.0x HOLD +0.019 / L6M -0.032 | TOLERANT CONDITIONAL [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T120m | -1353 | +516 | +1310 | +1853 | +576 | +266 | -416 | ON L6M +1310 / HOLD +1477 / MID +576 (n 96); 2023-25 same switch PRE -356 / X' -343 (n 53) | p 0.089 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.052 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97/1.00] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T120m | +2794 | +3342 | +2328 | +1314 | +233 | -363 | -694 | ON L6M +2328 / HOLD +1409 / MID +233 (n 270); 2023-25 same switch PRE +52 / X' -1069 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00/0.96] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T30m | +2794 | +3342 | +2328 | +1274 | +233 | -400 | -686 | ON L6M +2328 / HOLD +1369 / MID +233 (n 270); 2023-25 same switch PRE +67 / X' -958 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00/0.96] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T60m | +2794 | +3342 | +2328 | +1302 | +233 | -363 | -694 | ON L6M +2328 / HOLD +1396 / MID +233 (n 270); 2023-25 same switch PRE +52 / X' -1069 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00/0.96] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T30m | -1353 | +516 | +1510 | +1845 | +93 | +201 | -416 | ON L6M +1510 / HOLD +1469 / MID +93 (n 96); 2023-25 same switch PRE -380 / X' -343 (n 53) | p 0.099 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.051 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T60m | -1353 | +516 | +1465 | +1896 | +415 | +255 | -416 | ON L6M +1465 / HOLD +1520 / MID +415 (n 96); 2023-25 same switch PRE -356 / X' -343 (n 53) | p 0.099 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.052 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_hi | tgt=mid stop=1.00ATR T60m | -890 | +108 | +489 | +1066 | +825 | -220 | -632 | ON L6M +489 / HOLD +895 / MID +825 (n 126); 2023-25 same switch PRE -159 / X' -373 (n 63) | p 0.099 | 0.5x HOLD +0.031 / L6M -0.022; 1.0x HOLD +0.068 / L6M -0.043 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_hi | tgt=mid stop=1.00ATR T120m | -890 | +108 | +360 | +999 | +825 | -149 | -632 | ON L6M +360 / HOLD +828 / MID +825 (n 126); 2023-25 same switch PRE -165 / X' -373 (n 63) | p 0.099 | 0.5x HOLD +0.031 / L6M -0.022; 1.0x HOLD +0.068 / L6M -0.043 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_any | tgt=mid stop=0.25ATR T30m | -2555 | +156 | +1319 | +1088 | -1228 | +378 | -881 | ON L6M +1319 / HOLD +900 / MID -1228 (n 245); 2023-25 same switch PRE -197 / X' -486 (n 136) | p 0.109 | 0.5x HOLD +0.022 / L6M -0.033; 1.0x HOLD +0.047 / L6M -0.062 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T60m | +555 | +205 | +637 | +657 | +1439 | -902 | -399 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -259 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T30m | +555 | +205 | +637 | +657 | +1439 | -902 | -439 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -283 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T120m | +555 | +205 | +637 | +657 | +1439 | -902 | -399 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -259 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T60m | +197 | +67 | +475 | +539 | +1439 | -670 | -304 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -213 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T120m | +197 | +67 | +475 | +539 | +1439 | -670 | -304 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -213 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T30m | +197 | +67 | +475 | +539 | +1439 | -670 | -344 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -237 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T30m | -1353 | +278 | +1330 | +1597 | +190 | +308 | -312 | ON L6M +1330 / HOLD +1306 / MID +190 (n 93); 2023-25 same switch PRE -262 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.024 / L6M -0.001; 1.0x HOLD +0.052 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T60m | -1353 | +278 | +1285 | +1648 | +512 | +259 | -312 | ON L6M +1285 / HOLD +1356 / MID +512 (n 93); 2023-25 same switch PRE -340 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.024 / L6M -0.001; 1.0x HOLD +0.053 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T120m | -1353 | +278 | +1131 | +1591 | +611 | +259 | -312 | ON L6M +1131 / HOLD +1299 / MID +611 (n 93); 2023-25 same switch PRE -340 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.025 / L6M -0.001; 1.0x HOLD +0.053 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_any | tgt=mid stop=0.25ATR T30m | -2555 | +156 | +1337 | +1031 | -1228 | +162 | -933 | ON L6M +1337 / HOLD +842 / MID -1228 (n 255); 2023-25 same switch PRE -261 / X' -486 (n 143) | p 0.129 | 0.5x HOLD +0.021 / L6M -0.033; 1.0x HOLD +0.046 / L6M -0.062 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |

Reading (S4a, interim; post-hoc, Shadow only):
- **P_REL_cont_m1.0 (08:30 release continuation, entry at the 08:35 close, flat by 09:25; the only cell positive in every window L1M..X')**: tgt R1, stop 1.0 ATR, time 30 min: 379 trades, +$67k total over the sample, mean $177 per trade at about 4.7 lots; the profit is SHORT-ONLY (shorts +$64.6k, longs +$2.5k), 2025 is negative (-$17k), non-event days +$56.7k vs event days +$10.4k, and its neighbours are NOT positive (stop 0.5 ATR -$11k, R2 +$12.8k, stop 0.25 ATR/60 min -$2.7k, R2/0.5 ATR -$23.5k; release threshold 0.5 ATR: +$47.9k only at the same shape, other shapes negative). Label: FRAGILE (single-shape spike, one side), not a lead.
- **N_REL_rev_m0.5 (NY-AM reversal of the 08:30 release move, entry 09:31, target = PM mid)**: placebo p .01 (best in the family). It is a plateau along the 'mid' target shapes (stop 0.25 / 0.5 / 1.0 ATR, 60 min: +$101k / +$78k / +$41k, 313 / 321 / 304 trades; the R1 targets of the same trades are negative), but the years alternate (2023 -$34k, 2024 +$68k, 2025 -$34k, 2026 +$41k) and the profit sits on non-event days (+$47.5k vs -$6.3k on event days). Label: REGIME / year-alternating until the family test is read.
- Release-move reversals at 08:35 (P_REL_rev) lose in every shape (-$80k..-$221k): the pre-market release move continues or noise, it does not mean-revert before 09:25.
- **Family test, HOLD mean (all 1,338 cells with >= 100 trades, 100 worlds, random-side and shuffled-day nulls):** family p of the real max 0.41 (side) / 0.17 (days). The best cell, N_REL_rev_m0.5 mid / 0.25 ATR / 60 min (HOLD +$2,337 per week), has raw placebo p .01 but max-T p .41 and BH q .83; P_REL_cont_m1.0 (r1, 1.0, 30 min) has raw p .01, max-T p 1.0, q .83. Read: with 1,338 cells tried, the best pre-market book is what chance produces; no lead. L6M Calmar test running.
- **Family test, L6M Calmar:** family p of the real max 0.43 (side) / 0.50 (days). Both statistics (HOLD mean, L6M Calmar) are inside the null of the best of 1,338 cells: **DIS-B closes with no lead**. The two ranked candidates (P_REL_cont_m1.0 r1/1.0/30 min and N_REL_rev_m0.5 mid/1.0/60 min) are carried as watch rows for ZL-2's DIS-T bundle (trade lists in /mnt/l2/l2vast/ds3_dist/), not as books.


## RESTORED BY LEAD 2026-11-04T22:40Z from the 22:27Z snapshot after a second overwrite at 22:36Z (suspect: whole-file rewrite by an owner); sections below are verbatim, headers listed in MORNING.md

## DIS-B: GLOBEX PRE-MARKET STRUCTURE BOOKS (S4a; interim table 2026-11-04 21:41Z; prereg autopilot/DIS_B_PREREG.md sha256 f8cf86b8...c4563; ledger DIS_B; rows FADE_ROWS_DISB.md)
Question: do the Globex pre-market (04:00-09:30 ET) range / volume / VWAP / 08:30-release / pre-open structures trade as books, either with entries after 09:30 (N family, session nyam) or as pre-market entries (P family, flat by 09:25)? 61 event variants x shapes = 1341 cells valued (1338 with >= 100 trades); FadeHarness live fill model, costs stop 2.45 / exit 0.80 / fee 0.242, base Q1-A ts2 stack for marginal values. Post-hoc, Shadow only, no PASS claims.
Stage 1: share of cells with L6M > 0 = 0.39, HOLD > 0 = 0.30, both L3M, L6M and HOLD > 0: 157 cells (140 N family, 17 P family). Placebo p <= 0.10: 14 of 157. Family max-T test over all 1338 cells: HOLD_mean: family p of the real max side 0.406 / days 0.168; L6M_calmar: family p of the real max side 0.426 / days 0.495.
Ranked table (placebo p, then L6M; first 25 of 157; labels per FADE_ROWS rules, nothing here is a lead until the family test and the carrying-week checks are read):

| book | session | anchor | trigger | shape | L1M | L3M | L6M | HOLD | MID | PRE | X' | regime-conditioned | placebo | stack gain | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=mid stop=1.00ATR T60m | +73 | +322 | +1404 | +1207 | +195 | +144 | -550 | ON L6M +1404 / HOLD +993 / MID +195 (n 156); 2023-25 same switch PRE -120 / X' -507 (n 91) | p 0.010 | 0.5x HOLD +0.025 / L6M +0.002; 1.0x HOLD +0.056 / L6M +0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=mid stop=1.00ATR T120m | +73 | +322 | +1275 | +1165 | +305 | +216 | -550 | ON L6M +1275 / HOLD +951 / MID +305 (n 156); 2023-25 same switch PRE -127 / X' -507 (n 91) | p 0.010 | 0.5x HOLD +0.026 / L6M +0.002; 1.0x HOLD +0.056 / L6M +0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | pre | REL | P_REL_cont_m1.0 | tgt=r1 stop=1.00ATR T30m | +367 | +911 | +410 | +707 | +850 | +298 | +517 | ON L6M +410 / HOLD +515 / MID +850 (n 188); 2023-25 same switch PRE +265 / X' +289 (n 116) | p 0.059 | 0.5x HOLD +0.008 / L6M +0.014; 1.0x HOLD +0.016 / L6M +0.028 | TOLERANT CONDITIONAL [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_hi | tgt=mid stop=1.00ATR T60m | -890 | +108 | +581 | +1168 | +825 | -151 | -690 | ON L6M +581 / HOLD +997 / MID +825 (n 122); 2023-25 same switch PRE -85 / X' -373 (n 61) | p 0.069 | 0.5x HOLD +0.031 / L6M -0.021; 1.0x HOLD +0.070 / L6M -0.041 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_hi | tgt=mid stop=1.00ATR T120m | -890 | +108 | +452 | +1101 | +825 | -80 | -690 | ON L6M +452 / HOLD +930 / MID +825 (n 122); 2023-25 same switch PRE -91 / X' -373 (n 61) | p 0.069 | 0.5x HOLD +0.031 / L6M -0.021; 1.0x HOLD +0.070 / L6M -0.041 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | pre | REL | P_REL_cont_m1.0 | tgt=r2 stop=1.00ATR T30m | +12 | +935 | +284 | +663 | +801 | +197 | -82 | ON L6M +284 / HOLD +442 / MID +801 (n 188); 2023-25 same switch PRE +332 / X' +46 (n 116) | p 0.069 | 0.5x HOLD +0.009 / L6M -0.016; 1.0x HOLD +0.019 / L6M -0.032 | TOLERANT CONDITIONAL [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T120m | -1353 | +516 | +1310 | +1853 | +576 | +266 | -416 | ON L6M +1310 / HOLD +1477 / MID +576 (n 96); 2023-25 same switch PRE -356 / X' -343 (n 53) | p 0.089 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.052 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97/1.00] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T120m | +2794 | +3342 | +2328 | +1314 | +233 | -363 | -694 | ON L6M +2328 / HOLD +1409 / MID +233 (n 270); 2023-25 same switch PRE +52 / X' -1069 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00/0.96] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T30m | +2794 | +3342 | +2328 | +1274 | +233 | -400 | -686 | ON L6M +2328 / HOLD +1369 / MID +233 (n 270); 2023-25 same switch PRE +67 / X' -958 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00/0.96] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T60m | +2794 | +3342 | +2328 | +1302 | +233 | -363 | -694 | ON L6M +2328 / HOLD +1396 / MID +233 (n 270); 2023-25 same switch PRE +52 / X' -1069 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00/0.96] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T30m | -1353 | +516 | +1510 | +1845 | +93 | +201 | -416 | ON L6M +1510 / HOLD +1469 / MID +93 (n 96); 2023-25 same switch PRE -380 / X' -343 (n 53) | p 0.099 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.051 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T60m | -1353 | +516 | +1465 | +1896 | +415 | +255 | -416 | ON L6M +1465 / HOLD +1520 / MID +415 (n 96); 2023-25 same switch PRE -356 / X' -343 (n 53) | p 0.099 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.052 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_hi | tgt=mid stop=1.00ATR T60m | -890 | +108 | +489 | +1066 | +825 | -220 | -632 | ON L6M +489 / HOLD +895 / MID +825 (n 126); 2023-25 same switch PRE -159 / X' -373 (n 63) | p 0.099 | 0.5x HOLD +0.031 / L6M -0.022; 1.0x HOLD +0.068 / L6M -0.043 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_hi | tgt=mid stop=1.00ATR T120m | -890 | +108 | +360 | +999 | +825 | -149 | -632 | ON L6M +360 / HOLD +828 / MID +825 (n 126); 2023-25 same switch PRE -165 / X' -373 (n 63) | p 0.099 | 0.5x HOLD +0.031 / L6M -0.022; 1.0x HOLD +0.068 / L6M -0.043 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_any | tgt=mid stop=0.25ATR T30m | -2555 | +156 | +1319 | +1088 | -1228 | +378 | -881 | ON L6M +1319 / HOLD +900 / MID -1228 (n 245); 2023-25 same switch PRE -197 / X' -486 (n 136) | p 0.109 | 0.5x HOLD +0.022 / L6M -0.033; 1.0x HOLD +0.047 / L6M -0.062 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T60m | +555 | +205 | +637 | +657 | +1439 | -902 | -399 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -259 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T30m | +555 | +205 | +637 | +657 | +1439 | -902 | -439 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -283 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T120m | +555 | +205 | +637 | +657 | +1439 | -902 | -399 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -259 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T60m | +197 | +67 | +475 | +539 | +1439 | -670 | -304 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -213 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T120m | +197 | +67 | +475 | +539 | +1439 | -670 | -304 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -213 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T30m | +197 | +67 | +475 | +539 | +1439 | -670 | -344 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -237 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T30m | -1353 | +278 | +1330 | +1597 | +190 | +308 | -312 | ON L6M +1330 / HOLD +1306 / MID +190 (n 93); 2023-25 same switch PRE -262 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.024 / L6M -0.001; 1.0x HOLD +0.052 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T60m | -1353 | +278 | +1285 | +1648 | +512 | +259 | -312 | ON L6M +1285 / HOLD +1356 / MID +512 (n 93); 2023-25 same switch PRE -340 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.024 / L6M -0.001; 1.0x HOLD +0.053 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T120m | -1353 | +278 | +1131 | +1591 | +611 | +259 | -312 | ON L6M +1131 / HOLD +1299 / MID +611 (n 93); 2023-25 same switch PRE -340 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.025 / L6M -0.001; 1.0x HOLD +0.053 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00/1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_any | tgt=mid stop=0.25ATR T30m | -2555 | +156 | +1337 | +1031 | -1228 | +162 | -933 | ON L6M +1337 / HOLD +842 / MID -1228 (n 255); 2023-25 same switch PRE -261 / X' -486 (n 143) | p 0.129 | 0.5x HOLD +0.021 / L6M -0.033; 1.0x HOLD +0.046 / L6M -0.062 | NOW-ONLY REGIME [family maxT p 1.00/1.00] |

Reading (S4a, interim; post-hoc, Shadow only):
- **P_REL_cont_m1.0 (08:30 release continuation, entry at the 08:35 close, flat by 09:25; the only cell positive in every window L1M..X')**: tgt R1, stop 1.0 ATR, time 30 min: 379 trades, +$67k total over the sample, mean $177 per trade at about 4.7 lots; the profit is SHORT-ONLY (shorts +$64.6k, longs +$2.5k), 2025 is negative (-$17k), non-event days +$56.7k vs event days +$10.4k, and its neighbours are NOT positive (stop 0.5 ATR -$11k, R2 +$12.8k, stop 0.25 ATR/60 min -$2.7k, R2/0.5 ATR -$23.5k; release threshold 0.5 ATR: +$47.9k only at the same shape, other shapes negative). Label: FRAGILE (single-shape spike, one side), not a lead.
- **N_REL_rev_m0.5 (NY-AM reversal of the 08:30 release move, entry 09:31, target = PM mid)**: placebo p .01 (best in the family). It is a plateau along the 'mid' target shapes (stop 0.25 / 0.5 / 1.0 ATR, 60 min: +$101k / +$78k / +$41k, 313 / 321 / 304 trades; the R1 targets of the same trades are negative), but the years alternate (2023 -$34k, 2024 +$68k, 2025 -$34k, 2026 +$41k) and the profit sits on non-event days (+$47.5k vs -$6.3k on event days). Label: REGIME / year-alternating until the family test is read.
- Release-move reversals at 08:35 (P_REL_rev) lose in every shape (-$80k..-$221k): the pre-market release move continues or noise, it does not mean-revert before 09:25.
- **Family test, HOLD mean (all 1,338 cells with >= 100 trades, 100 worlds, random-side and shuffled-day nulls):** family p of the real max 0.41 (side) / 0.17 (days). The best cell, N_REL_rev_m0.5 mid / 0.25 ATR / 60 min (HOLD +$2,337 per week), has raw placebo p .01 but max-T p .41 and BH q .83; P_REL_cont_m1.0 (r1, 1.0, 30 min) has raw p .01, max-T p 1.0, q .83. Read: with 1,338 cells tried, the best pre-market book is what chance produces; no lead. L6M Calmar test running.
- **Family test, L6M Calmar:** family p of the real max 0.43 (side) / 0.50 (days). Both statistics (HOLD mean, L6M Calmar) are inside the null of the best of 1,338 cells: **DIS-B closes with no lead**. The two ranked candidates (P_REL_cont_m1.0 r1/1.0/30 min and N_REL_rev_m0.5 mid/1.0/60 min) are carried as watch rows for ZL-2's DIS-T bundle (trade lists in /mnt/l2/l2vast/ds3_dist/), not as books.


## DIS-A FINAL (Z3, 2026-11-04 ~22:00Z): D1 multi-hour holds and D2 pyramids - NO ADDITION; both families DEAD under the family max-stat null
Prereg sha256 2280ce04cb18676efffb7d872d6054561e6ef0e68f31f1d6a9a118cbb4cc1945. n_tested registered: DISA_D1 264, DISA_D2 48 (FADE_NTESTED.md). Ledger program DIS_A: 312 cells appended after dead_lookup (0 duplicates). Rows: FADE_ROWS_DISA.md (28 rows, 16 columns). Code: l2vast/ds3/code/dis_a/ (dis_lib.py, d1_run.py, d1_top.py, d2_pyr.py, d2_run.py, disa_final.py); data: l2vast/ds3/out/dis_a/.
Method as preregistered: standalone NQ books on the FadeHarness, Q1-A ts2 stack, live fills (first fill +1 s, stop 2.45 / market 0.80 / fee 0.242), equal-$-risk $1,200 per entry, flat 16:55, gate_v3 carry weeks. D2 pyramid simulator validated against the harness (adds off, no trail: 1,364 trades, correlation 0.9997, lots identical, max |diff| $372 from the slice-fill model).
### D1 (264 books, 9 entry sources x session x stop x time stop x target)
* 29 books pass the TOLERANT gate; 107 of 264 have a positive L6M mean; the positives are the ASIA-entry holds (Asia -> London exit) with a 1-ATR stop: e.g. S_S (Supertrend flip) asia 1.0 ATR / 4 h / 2R: L6M +1,314, HOLD +1,230, MID +2,233, PRE +89, X' -493 $/wk; L_PB asia 1.0 / 4 h: L6M +1,016, HOLD +1,345, MID +1,882, PRE +807, X' -858. London-entry and NY-AM-entry holds are net negative in L6M.
* FAMILY MAX-STAT NULL (100 worlds x random side and shuffled day; the best of 264 books): L6M mean p = 0.53 (side) / 0.92 (days); HOLD Calmar p = 0.66 / 0.71. Every one of the top 20 books has max-T p >= 0.71 on both statistics (raw p of the best HOLD-Calmar books 0.01-0.07). Placebo p_book of the top books 0.13-0.88 (best: S_S asia 1.0/4h/2R p 0.129), none <= 0.10. Stack Calmar gain at 1x (carry weeks dropped): HOLD +0.011 / L6M -0.083 for the best book; L_PB asia HOLD -0.015 / L6M +0.054; no book improves BOTH HOLD and L6M. Regime-conditioned (R_F40 ON): same numbers as pooled in 2026 (L6M +1,314 ON), and 2023-25 under the same switch is flat to negative (S_S: PRE -53 / X' -795): a 2026 Asia-trend regime, not a stable book.
* Plain sentence: multi-hour holds on the live books' own signals or on simple trend/continuation signals do not add a book: the Asia-entry holds are positive in the 2026 windows but are what a random-side / shuffled-day family null produces for the best of 264 books (max-T p 0.53-0.92), they fail on X', and none improves the stack Calmar in HOLD and L6M together.
### D2 (48 pyramid books, 4 sources x session x trail x adds)
* Mean of book means: S_B L6M -659 / HOLD -155 / PRE -528, S_E -752 / -240 / +151, S_LALL -1,170 / -466 / -287, S_S -1,160 / -651 / -444; by session asia -423 / -11 / +484, london -1,434 / -489 / -1,387, nyam -949 / -634 / +71. 3 of 48 have a positive L6M; 2 pass TOLERANT (S_S asia Chandelier 2 and 3 adds: L6M +999 / +1,162, HOLD +510 / +546, MID -1,095 / -1,206, X' -801 / -820), stack gain HOLD 0.000 / L6M -0.08.
* Family max-stat null (48 books, 100 worlds): L6M mean p = 0.67 (side) / 0.85 (days); HOLD Calmar p = 0.87 / 0.96. Pyramiding amplifies the losing trend entries (adds 0.8-1.3 per trade, mean lots 1.5-2.1).
* Plain sentence: scale-in/pyramid on continuation loses money in every source and session pooled and is DEAD; the only tolerant-gate passes are Asia Supertrend books that fail MID and X' and sit inside the family null.
### Next (user standing rule: start the next untested proposal)
Candidate for DIS-B (not yet run, no spend): the ASIA-entry continuation hold is the only repeated positive in D1 (and in CAL's D4 'Asia cont' rows). Proposal: test it as a REGIME book with the causal switch ONLY on Asia continuation (trailing-20/40-day Asia-continuation P&L > 0), 2023-25 under the same switch, walk-forward, with the family null restricted to the Asia sources; and a pairs test with the live Asia sleeve to see whether it is the same bet as K7/P7 Asia (correlation by session). Starting after the Lead's OK or on the next free worker.


## DIS-AA (BASE-4, 2026-11-04T21:49Z): PRE-2023 OUT-OF-SAMPLE OF THE FOUR FADE SURVIVORS - interim 1 (full page autopilot/DS3_FADE_OOS.md; scope DISAA_scope.md sha256 5927ec85d2caa1991a1fdeb43473019ec5c435047e75a099ee3cdf11600a6792; ledger DIS_AA; 1-minute signal-level object, not live P&L; no PASS)
Verdicts (rule: positive excess in >= 5 of 10 pre-2023 years AND bootstrap CI not entirely below 0, against each of P1c / other-day causal fade / opposite side / delayed re-derived fade): N_REL_rev: SURVIVES PRE-2023 (weak rule; not a PASS); ORBF: SURVIVES PRE-2023 (weak rule; not a PASS); ONRTH: SURVIVES PRE-2023 (weak rule; not a PASS); VWAPF: POST-2023 ONLY / not supported before 2023 (fails vs P1c); VB2NYPM_T1: SURVIVES PRE-2023 (weak rule; not a PASS); NYAM_bundle: SURVIVES PRE-2023 (weak rule; not a PASS). Calibration on 2023-04..2026-10: signal recall 0.98-0.99, per-trade corr 0.86-0.94, weekly corr 0.80-0.94. Reading: pre-2023 raw means are about zero (bundle -0.49 pts/trade, -$148/wk), the excess is positive in point estimate mostly because the benchmarks lose money; strong version (CI lower > 0) only for ORBF and the bundle vs other-day and delayed-fade (and ONRTH vs delayed-fade).


## DIS-N interim row 2 / CLOSE (2026-11-04T21:56Z): year stability of the 8 exact-engine TOLERANT clock cells and plain sentence
Stack delta of each cell by calendar year (exact engine, $ over the year; 15 active quarters): P7 minutes 30-34 skip -47,038 (2023) / -24,520 / -42,066 / +84,067 (2026), 7 of 15 quarters positive (half-size: -24,584 / -6,669 / -27,876 / +52,567); P7 minute :30 skip -26,887 / +42,828 / +2,264 / +61,036, 10 of 15 quarters positive (half: -11,606 / +19,776 / +3,282 / +13,088); H7 asia first-5-minutes skip +16,602 / -1,109 / -12,797 / -7,932, 5 of 15; London first-5-minutes all books skip -43 / +16,452 / +79 / -31,133, 7 of 14; P7 minutes 05-09 skip +1,225 / -9,161 / -6,120 / -2,745, 6 of 15. Only the P7 :30 cell is positive in three of four years, and it is a 56-row bucket (-$41k of P&L) selected from 471 cells with family p 1.00; the minutes 30-34 cell is a 2026-only gain (REGIME). Plain sentence (DIS-N closed): intraday-clock overlays on the six live signals - minute-of-hour marks, five-minute buckets, 08:30 / 10:00 / 14:00 release windows and session edges, as skip / half / double and as 1-5 minute entry delays - add nothing the stack can use: the best of 471 cells is inside the family null (p 0.80, BH q >= 0.14), the 8 exact-engine tolerant cells are small P7 and session-edge buckets whose gains are not stable by year, and entry delays worsen the stack in the low-fidelity screen; no flag, nothing applied. Open: P7 :30 as a forward-register observation only (56 rows in 3.5 years), and the unbuilt engine entry-delay hook. Ledger DIS_N 511 cells, rows FADE_ROWS_DISN.md (40), prereg 47c84c85....


## DIS-S (CAL, 2026-11-04) EQUITY-CURVE / STREAK DEPENDENCE of the live books - interim, no PASS claims
Prereg l2vast/ds3/prereg/DISS_prereg.md sha256 a45e41f3100e79d0d605a3508422b358b7a62eb189b6e066424b92af604a8a53 (DECISIONS.md). Code l2vast/ds3/code/discover/{diss_trades.py, diss.py, diss_a.py, diss_supp.py, diss_report.py}; out/diss_cells.csv, diss_supp.csv, diss_a_streak.csv, diss_a_acf.csv; rows FADE_ROWS_DISS.md; ledger DIS_S (42 cell rows appended); n_tested line DISS = 86 in FADE_NTESTED.md.
Dead lookup first: T-HALT-RESUME (A2DDRR, 1,786 cells on the GOV-1 engine: streakN, nN, wkN_N, rsN_N, eqmaN / eqmaNinv, dddN_N, ddtN_N, pfN, zN, day / w2 / ses / book scopes; median delta L6M -12.8k / HOLD -11.9k, 0 of 1,786 beat the MDE, NULL, DS3_HALT_RULES.md and DS3_DD_REREAD_A2.md), RHQ-HALT-RESUME (45), DD1 drawdown (80), EQR (222), F1DD (825), RE-2 skip-after-loser (DS3_EDGE_MONITOR.md). Hence the engine side is a small re-price on the Q1-A ts2 engine (28 cells); the Shadow fade bundle (14 cells) and the serial-dependence statistics are new.
Causal definition (as preregistered): paper track = the six books' taken signals in the no-lock live-lot run (17,396 trades, same stream the lock engine consumes); at the entry second of trade j only trades with exit index < entry index of j are used (a trade that straddles the decision is not known and is excluded); flag False during warm-up; SKIP = extra_skip, HALF = Q1-A multiplier x0.5; restore automatically. A live version needs the paper track of skipped signals.
(a) Serial dependence: no evidence. Per book, next-trade net after 1/2/3 consecutive completed losers vs all other trades: the raw differences look large (PE +218 after 2 losers, SM +210) but equal the circular-shift null mean (the difference is mechanical: time-of-day clustering), and the excess over the null is nil: 18 tests, smallest p 0.032 (MV, k=3), BH q about 0.5. Runs test z on trade signs per book |z| <= 0.7. Stack-level streak lines were dropped (books interleave and hedge each other; sign runs z -43 is a cross-book artefact, the circular null is invalid there). Daily stack P&L autocorrelation lags 1-10 (935 days): all within +-0.07; only lag 4 (+0.072; recent 250 days +0.117) leaves the iid permutation band and none leaves the 10-day block-bootstrap interval except lag 10 on the recent 250 days (+0.125 vs [-0.12, +0.11]); 30 lag-segment tests, expect 1-2 by chance.
(b) Engine overlays (28 cells, 45% of trades flagged for TR5/10/20 and EQMA, 24-36% for week states): every overlay cuts HOLD maxDD (base 122k): SKIP by 24-53%, HALF by 14-28%, but at a cost of $2-12k/wk of HOLD mean , and the cut is mostly the arithmetic of trading less. Random same-count skips match it: p_P2 0.17-0.44 for SKIP cells; the real S maximum 0.078 sits below the family null median (world max 0.18 median, 0.40 p95 for random skips, 0.19 / 0.66 circular P&L). Family p 0.97-1.00, BH q >= 0.68 for every cell. Skipped-vs-kept: in 2026 the flagged trades (after a losing stretch) do NOT earn less: TR20 BOOK flagged mean since May asia +386 vs +272 unflagged, london +59 vs +8, nypm +210 vs -269, nyam -64 vs -28; i.e. the P&L has mean reversion after losing stretches in the data, not momentum, which is why the filters pay a mean cost.
The single cell that beats its own placebos: TR20 BOOK HALF (halve a book when its last 20 completed trades sum below zero): maxDD cut L6M +45% / HOLD +28% / PRE +14% / X' +30%, mean change L6M -4.5k, HOLD -3.1k (MDE 3.8k), PRE -2.4k (MDE 2.6k), X' -1.7k; P1 shifted-state 0.020, P2 random halves 0.020, P3 circular P&L 0.069; PA9 L6M +33.0 / PRE +13.1 / X' +5.6 / HOLD +28.0 (pass2 true); but family p 0.99, BH q 0.68, stack Calmar change HOLD only +0.057. Label WEAK (cuts DD in all windows, fails family and BH), not a lead. Nine cells are REGIME (NOW-ONLY): the DD cut is in L6M/HOLD and negative in PRE and/or X' (TR10 BOOK SKIP: HOLD cut 53%, PRE -27%, X' -59%). 21 cells DEAD.
(c) Shadow fade bundle (7 states x SKIP/HALF): 7 cells cut maxDD in HOLD, PRE and X' (none in L6M: 0%) (HOLD 9-12%, PRE 6-15%, X' 15-46%) with a mean cost of $0.4-1.7k/wk in HOLD but a mean GAIN in PRE (+0.7k to +2.1k), stack dCalmar HOLD +0.02 to +0.03 (TR5 SKIP best +0.030). Placebos: shifted-state P1 0.010 (floor at 100 draws), random-day skips P2 0.04-0.10, circular P&L P3 0.09-0.13; family 1.00 and BH q 0.68. Bundle trades are daily and mean-reverting in P&L, so the filter helps a little in the old windows; labelled WEAK, no inference beyond that, PA9 n/a (outside the engine).
MDE: HOLD weekly paired MDE $3.2-10k for the engine cells (2.8 x SE), as large as most deltas; only the DD cuts, not the mean changes, are outside it.
Verdict: the stack's own recent result does not predict its next result; equity-curve overlays cut drawdown only as much as trading less would, at a mean cost; no overlay earns a place. Drawdown view: keep the weekly floor / locks already live (HALT-RESUME conclusion unchanged on Q1-A ts2).


## DIS-AD (BASE-4, 2026-11-04T21:58Z): PB ASIA RECONCILED - full page autopilot/DS3_PB_ASIA.md; scope DISAD_scope.md sha256 9ce7146c0e0893c0a8de0470a01b61330fecee0c51c5e83e92fce87ccd0a3044; ledger DIS_AD; no PASS
PB asia post-2023 net +3.98 pts/trade (V2) = unconditional side drift -1.22 + side/day information +4.20 + timing +1.00; timing +2.69 in 2023-25 and -1.79 in 2026, so the DIS-M "below drift" (L6M +12 vs delayed +532, excess -521) is a 2026-window statement about entry TIMING vs a delayed same-side entry (not drift); (i) is real for 2023-25 (gross -0.69 pre-2023, +5.01 post; 45% of post P&L in the top 5 weeks), (iii) +254 is the live-exit object in L6M (O3 +222 vs X3 replica +12). PB pre-2023 negativity: gross -0.69 (SE 1.15) + cost 1.43 under V2.

Correction (BASE-4, 2026-11-04T22:01Z, from DIS-AD) to the DIS-M section: the statistic called 'excess over causal matched drift' (P1c: the same trades, same side, entry delayed 5..120 min) is NOT drift - it keeps the signal's side and day selection and measures ENTRY TIMING only; it is renamed 'excess over delayed same-side entry (timing excess)'. The true drift term is the side-independent random-time drift (DIS-M items 1 and 3 benchmark books, and DIS-AD's D: random minute in the session, side fixed or drawn independently of the signal). The DIS-M labels EXCESS SURVIVES (ORBF, VB2 NYPM T1) depended on the timing excess (P1c) plus the random-side and other-day placebos and the family test; the NEGATIVE EXCESS labels of the live groups (e.g. LIVE PB|asia, L6M +12 vs +532) are 'below the delayed entry' statements, dominated by 2026 (for PB asia the timing term is +2.69 in 2023-25 and -1.79 in 2026; DS3_PB_ASIA.md). No DIS-M label is changed; only the wording. AUDIT_L2 benchmarks (a), (b), (c) are separate and stand.
Correction (BASE-4, 2026-11-04T22:01Z, from DIS-AD) to the DIS-Y section: 'causal drift' / 'drift_c' columns in FADE_ROWS_DISY.md are the delayed same-side entry (timing excess), not drift; all 22 DIS-Y labels depended on that statistic (P1c p <= .10 in L6M and HOLD) together with the random-side and other-day placebos and the 22-cell family test. Against the SIDE-INDEPENDENT random-time drift (random minute in the same session/day, side drawn independently with the list's own long/short share, 100 draws; disy_sideind.py, /mnt/l2/l2vast/ds3_base4/disy_sideind.pkl) the drift is about -50 to -500 $/wk (costs) for every list, and the four survivors clear it: N_REL_rev excess +1556 / +1421 (p .04 / .03), ORBF +1236 / +921 (.02 / .01), bundle +2700 / +3255 (.01 / .01), VB2 NYPM T1 +403 / +281 (.01 / .01). Ten more cells also clear it per cell (p <= .10 in L6M and HOLD) but not the timing-excess family test: Z1 swing, DIS-K, DIS-C, DIS-E, DIS-G, DIS-J, Q13, ONRTH, PD ASIA T2, OR15; not clearing: DIS-B P_REL_cont, DIS-Q 15:00 IMB, VWAPF, VB2 NYAM T3, the Q9 London-off sleeve and both Q4 amplifier forms (family test not recomputed on this statistic). No published label is changed; the survivors' label should be read as 'survives timing excess + placebos + family' and they also clear the true drift. AUDIT_L2 (a), (b), (c) are separate and stand.


## DIS-AG (BASE-4, 2026-11-04T22:06Z): SHADOW LOT CALIBRATION TABLE - autopilot/SHADOW_LOT_TABLE.md; scope DISAG_scope.md sha256 969561f947ac89f648129268252ae48064b9004ff063a3ab97ae6500d4ef46aa; ledger DIS_AG; a table for the user, not a recommendation; no PASS, nothing live
14 lines (5 SHADOW-2, NYAM books + bundle, 3 top-3 fades, OR15, N_REL_rev) at fixed 1/2/3/4/6 lots and equal-risk ($600 / $1,200) through the live fill model: equal-risk lots per trade 1.0 (60/60 lines) to 3.7 (DIS-C); naive vs winner-deflated expectation, HOLD/PRE stack maxDD change, worst week and HOLD-episode loss at each L, ER-ladder effective lots. Conservative (A) weekly expectations are negative for most lines at every size; the 2026-regime naive levels are the best-year levels.


## DIS-AC (Z3, 2026-11-04 ~22:45Z): Asia continuation hold as a causal-regime book - REGIME-2026 LEAD, NOT AN ADDITION
Prereg l2vast/ds3/prereg/DIS_AC_prereg.md sha256 3595f2c6fbfd6167b1d13ae267cb976b3388dd2aa77f3cf709ddfa7009976a83 (renamed from the DIS-B file sha 7c6fa241..., no statistic run before; DECISIONS.md). Ledger DIS_AC +288 cells (0 dup). Rows FADE_ROWS_DISAC.md (top 8 conditional books). n_tested DISAC = 288 (96 Asia hold books x 3 switches). Code l2vast/ds3/code/dis_a/ (dac_a.py, dac_b.py, dac_b_run.py, dac_b_an.py, dac_final.py); data out/dis_a/dac_a*.csv/pkl, out/dis_ac/dac_b_*.
Books = the DIS-A D1 Asia sub-grid (96 books with >= 100 trades: live HM/KB/PE/SM/PB Asia signals, session break, Supertrend, EMA cross; stop 1/2 ATR15, time stop 2/4/6 h, target none/2R, flat 08:30 ET, $1,200 risk per entry). Switches (causal): R20, R40 (own trailing 20/40-day P&L > 0) and RAS (pooled Asia-hold bundle trailing 20-day > 0). Placebo: forward-only delay (make_placebo shift5) only.
* T1 (2023-26, measured fills): 26 of 288 (book, switch) cells are CONDITIONAL (ON-state positive in L6M, HOLD and MID and PRE >= 0, X' >= 0 with the same switch in 2023-25): 17 with RAS, 7 R40, 2 R20; mean ON-state weekly $ (all cells) by switch L6M / HOLD / MID / PRE / X': R20 +145 / +215 / -3 / +87 / -158, R40 +64 / +165 / +115 / +75 / -18, RAS +411 / +379 / +82 / +114 / +47 (unconditional books: PRE +236 / X' -383). Best: L_HM asia stop 1.0 ATR, 4 h, 2R, RAS: ON-state L6M +1,826, HOLD +1,683, MID +728, PRE +38, X' +63 $/wk, ON on 67% of 2026 days; stack Calmar gain with the carrying weeks dropped at 0.5x / 1x: HOLD +0.005 / +0.009, L6M +0.007 / +0.014.
* T2 family max-stat (shift5 only, 100 worlds, best ON-state HOLD Calmar of 288): p = 0.079 (the two L_HM 1.0 ATR 4h/6h 2R RAS books: raw p 0.010, max-T 0.079); every other book has max-T p >= 0.86.
* T3 walk-forward (monthly top-5 of the 96 by trailing-6-month Calmar, 2024-01..2026-10): weekly $ L6M +506 / HOLD +325 / MID +269 / PRE +329 vs equal weight of all 96 +222 / +426 / +373 / +236 vs random 5-book chains +220 / +401 / +336 / +247; Calmar rank vs 100 random chains L6M 0.86 / HOLD 0.74 / PRE 0.61 (< .95); stack Calmar gain of the chain HOLD -0.005 / L6M -0.063 / PRE -0.002 (fails).
* T4 overlap: daily correlation with the live six books' Asia-session P&L (Q1-A ts2 stack): pooled bundle 0.67 (L6M) / 0.69 (HOLD) / 0.58 (PRE); the walk-forward chain 0.57 / 0.58 / 0.41: largely the SAME bet as the live Asia sleeve (the L_HM books are the live HM Asia signals held to London).
* T5 pre-2023 check of the switch on the owned 1-minute history (2013-2026, additive back-adjusted continuous NQ; signal-level object as in DS3_SIGNALS_2013.md: 1-min fills, next-bar open + 0.25, stop slip 1.5, flat 0.5, no TH exits/locks/zones; ATR stops are already volatility-scaled): the pooled Asia-hold bundle loses money in every year before 2024 (mean $/day -1,791 in 2013 improving to -185 in 2023, +43 in 2024, +53 in 2025, +165 in 2026) and the RAS switch is OFF in 2013-2017 (ON share 0.00-0.05), 0.04-0.12 in 2018-19, 0.27 / 0.43 in 2020-21, 0.06 in 2022, then 0.14 (2023), 0.52 / 0.54 / 0.60 (2024-26). By the preregistered rule 222 of 288 (book, switch) cells are 'validated' (ON minus OFF > 0 with a block-bootstrap 2.5th percentile > 0 in 2013-22), BUT the ON state earns nothing before 2023: only 7% of cells have a positive ON-state mean in 2013-22 (median ON -57 to -89 $/trade vs OFF -240 to -255); for the L_HM 1.0 ATR 4 h 2R RAS book ON -200 vs OFF -371 $/trade (diff +171, CI lo +49). The switch avoids the worst periods; it does not find profitable ones before 2023.
* Plain sentence: the Asia-continuation hold is a 2024-26 regime (profitable only since 2024, on in 2020-21 only partly) and a causal 'trailing Asia-hold P&L > 0' switch makes the L_HM Asia hold look conditional in 2023-26 (family max-T p 0.079, positive stack gain carry-dropped), but the same ON state lost money in 2013-2022, the walk-forward allocation does not beat random books (rank 0.61-0.86), and the book is 0.6-0.7 correlated with the live Asia sleeve: REGIME-2026 LEAD, not an addition; watch it on the forward register only.



## DIS-P (Z1): POST-STOP COOLDOWN / LOSS-STREAK OVERLAYS on the six live books, interim row 1 (2026-11-04T22:12Z) post-hoc, no PASS, Shadow only, \$0, on-disk
DIS-O (calendar-day overlays) is WITHDRAWN: dead_lookup shows it is covered (EINT2 590+ cells incl. d2.dow0.skip, d2.opexday.skip, d2.ev|fomc.skip, d2.ev|cpi.skip; NTE1 / NTE1C / RISKOFF_NTE2 more than 120,000 no-trade-expanded cells with event-relative and month-end timing; A2DDRR day-of-week halts; DD3 roll-week rollouts); gaps, overnight range and same-side concentration are also stored. Prereg l2vast/ds3/prereg/DISP_Z1_prereg.md sha256 26c73efa000bd0da328e4142b902d46248cf5853afc384598fdf955b0c20710f (DECISIONS.md before any DIS-P statistic); dead_lookup for the idea (consecutive loss, loss streak, after stop, cooldown): 0 hits. n_tested DISP = 336; 246 cells have >= 5 affected taken rows; ledger DIS_P; rows autopilot/FADE_ROWS_DISP.md (31 exact-engine rows). Code l2vast/ds3/code/zones3/fade_mz/disp_run.py.
Definition: a stop-out = a taken row of the Q1-A ts2 run that exits at or beyond 0.9 x its library stop (817 of 21,646 taken rows, 3.8%: the live exits (TH-L2 cuts, locks) end most losers earlier); after a stop-out in the same book (B), in any book on the same side (S) or in any book (A), optionally after two consecutive stop-outs of the book in a label day (streak2), signals within M = 15 / 30 / 60 / 120 minutes of the stop-out's EXIT time are skipped or halved (strictly causal: the exit precedes the signal). 3 triggers x 2 streak x 4 M x 2 actions x 7 scopes = 336 cells.
Results (surrogate first-order, carry dropped): NOW-ONLY 98, TOLERANT 16 of 246; family max-stat (100 worlds, one random shift of +-3..30 label days applied to the stop-out event times of ALL cells): null best S median 0.081, 95th 0.228, max 0.254; the best real cell (stop-out in any book on the same side, single, 30-minute cooldown, ALL books, skip; 167 rows) has S 0.098: stack maxDD cut L6M +14.1% / HOLD +5.6% / MID +7.7% / PRE -8.9% / X' +1.3%, mean change +\$119 / +\$120 per week (MDE \$3,146), cell placebos p 0.01 / 0.01 / 0.06 (event shift / random rows / shifted order) -> FAMILY p 0.39; minimum family p over all cells 0.39; BH q over the 53 screened cell-level (event-shift) p-values has minimum 0.03 but the cell-level placebo is not the family test; 6 screened cells have all three cell placebos <= 0.10. Exact engine (31 cells): TOLERANT 5, NOW-ONLY (REGIME) 18, DEAD 8; the surrogate-vs-exact correlation of the score is only 0.44. The exact best-S cells (any-book / same-side stop-out, 120-minute cooldown, book K7) cut L6M by 31-34% (PA9 +31% / +40%) but HOLD by -5% to -17%, MID -18% to -51% and PRE -1% to -11%: an L6M-only drawdown cut that makes HOLD and MID worse; they are NOT tolerant. The 5 exact-tolerant cells are tiny (18-153 affected rows; cuts of 1-2% on L6M and HOLD, X'/PRE 0) with family p 0.97-1.00.
Plain sentence: a stop-out cooldown on the live signals does not help the stack beyond what random same-size skips give - the best surrogate cell (S 0.098) is inside the family null (p 0.39), the L6M-heavy exact cells worsen HOLD and MID, and the exact-tolerant cells are 18-153 rows with 1-2% cuts; no flag, nothing applied. Note: the stop-out definition (exit at 0.9 of the stop) catches only 3.8% of rows because the live exits cut losers earlier; a looser 'loss' trigger (any losing row) is NOT covered by this prereg and would be a separate, registered variant.


## DIS-AJ (BASE-4, 2026-11-04T22:12Z): TRUE-DRIFT TEST FINISHED - interim 1; scope DISAJ_scope.md sha256 799e91a152698d3bc458f451505198a0268b4f6abd5a91ce3834184b572971e3; ledger DIS_AJ; n_tested DISAJ; full table = the appended "RANKED LIST (true-drift family)" section in DS3_DISCOVER.md; no PASS, nothing live
21 cells x 3 world sets x 200 worlds (W1 random minute + independent side, W2 day-shuffle, W3 matched clock). Labels: clears true drift + family 1 (NYAM fade bundle (ONRTH+VWAPF+ORBF)); clears per-cell only 13; drift-explained 7; negative 0. All four fade survivors pass the matched-clock test; only the NYAM bundle also clears the 21-cell family test (L6M 0.06 / HOLD 0.00). Corrects DIS-Y: its family test was on the timing excess.
Correction (Z1, DIS-P interim 1): the exact best-S cells with the 120-minute cooldown are on P7 (book index 1: 'S single 120 skip' and 'A single 120 skip/half'), M7 (index 4) and ALL books, not K7. Their exact stack cuts are L6M +24% to +34% (PA9 L6M +28% to +40%) with HOLD -10% to -21%, MID -18% to -60% and PRE between +5% and -11% (e.g. any-book single-stop 120-min skip on ALL books: L6M +32.2%, HOLD -21.3%, MID -60.3%, PRE +4.7%); the conclusion is unchanged.


## RESTORED SECTIONS (BASE-4, 2026-11-04T22:16Z): DS3_DISCOVER2.md lost content between the 21:06Z snapshot and 21:58Z (file was 430 lines at 21:06Z, 189 lines in the 21:58Z sync copy); the sections below are copied verbatim from /tmp/DS3_DISCOVER2.bak2 (21:06Z snapshot) for headers that are missing now. Sections written after 21:06Z and lost (DIS-M, DIS-Y, DIS-T, DIS-U, others) are restored or must be re-appended by their owners; nothing else was changed.

# DS3_DISCOVER2 - section S4b: DIS-E interim 2 (final) - plateau or point, other anchors, close - 2026-11-04 20:42Z
Addendum autopilot/DIS_E_ADD1_PREREG.md (sha256 in DECISIONS.md; written before the neighbourhood scores; n_tested +672 and +48 control cells, cumulative DIS_E 1,216 in DISE_NTESTED.md). Code l2vast/ds3/code/disc/ (dise_nbhd.py, dise_final.py); data /mnt/l2/l2vast/ds3_dise/.

## 1. Is F prevday|FAILURE NY-AM a plateau or a point?
**Neighbourhood N1 (648 cells: touch tolerance x lookback x refill-failure window x stop x target x time stop):**
- N1 cells 648: NOW-ONLY 320, TOLERANT 202 (31%), STRICT 82 (13%); share of cells positive in L6M 69%, HOLD 80%, PRE 58%, X' 39%.
By touch tolerance - 0.0: L6M +394, HOLD +210, PRE +170, TOLERANT 34%; 0.05: L6M +429, HOLD +314, PRE +63, TOLERANT 36%; 0.15: L6M +342, HOLD +174, PRE -90, TOLERANT 24%. By lookback - 5: L6M +188, HOLD +246, PRE +49, TOLERANT 22%; 10: L6M +475, HOLD +196, PRE -38, TOLERANT 20%; 20: L6M +438, HOLD +308, PRE +167, TOLERANT 51%. By refill-failure window - 3: L6M +152, HOLD +302, PRE +92, TOLERANT 25%; 5: L6M +388, HOLD +195, PRE +171, TOLERANT 45%; 10: L6M +556, HOLD +196, PRE -111, TOLERANT 23%. By stop - 0.5: L6M -563, HOLD +3, PRE -90, TOLERANT 0%; 0.75: L6M +508, HOLD +286, PRE -11, TOLERANT 33%; 1.0: L6M +629, HOLD +368, PRE +139, TOLERANT 48%; 1.5: L6M +519, HOLD +379, PRE +179, TOLERANT 43%. By target - 1: L6M +257, HOLD +139, PRE -36, TOLERANT 27%; 2: L6M +645, HOLD +343, PRE +184, TOLERANT 35%. By time stop - 30: L6M +401, HOLD +224, PRE +51, TOLERANT 32%; 60: L6M +389, HOLD +276, PRE +69, TOLERANT 31%; 90: L6M +382, HOLD +239, PRE +79, TOLERANT 30%.
The lead (0.05 / 10 / 5 bars / 0.75 ATR / 2R / 60 min; 317 trades) sits at the 93-th percentile of the neighbourhood on L6M and the 77-th on HOLD: **a plateau, not a point** along touch tolerance, lookback, time stop and any stop >= 0.75 ATR with a 2R target; the 0.5 ATR stop is dead (0% tolerant), the 1R target is weaker (medians L6M +0.26k vs +0.65k), and a 10-bar refill-failure window is weaker than 5 (PRE negative).
**Control - is it the refill-failure condition or just 'follow the break at the previous-day extreme'?** Same touch rule and shapes:
| refill-failure condition | shape | trades | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|
| none | 0.75 ATR 2R T60 | 544 | -402 | -22 | -137 | +124 | -282 |
| none | 1.00 ATR 2R T60 | 544 | -444 | +887 | +583 | +570 | -121 |
| absent | 0.75 ATR 2R T60 | 406 | -694 | -577 | -334 | +53 | -384 |
| absent | 1.00 ATR 2R T60 | 406 | -450 | +79 | -28 | +96 | -487 |
| required (the lead, >= 1 in the last 5 bars) | 0.75 ATR 2R T60 | 317 | +780 | +1361 | +478 | +314 | +23 |
Medians over the 24 shapes: no condition (all touches): +13 / -252 / +190; refill failures absent in the last 5 bars: -317 / -304 / +92; condition required (the lead's family, N1 at tol 0.05 / lookback 10 / window 5): L6M +388, HOLD +248, PRE +59. Plain sentence: all touches of the previous-day extreme followed together are flat (L6M ~0, HOLD -0.1k), the subset WITHOUT refill failures loses (L6M -0.3k to -0.6k), and the refill-failure subset carries the whole effect: the Q4 refill-failure hypothesis is the active ingredient of this book.
**Lead details (corrected carrying weeks, live lots; 317 trades, top-5 trades = 72% of its P&L):**
| window | $/wk | maxDD ($k) | Calmar | MDE ($/wk) |
|---|---|---|---|---|
| L1M | +2366 | 6.3 | 0.37 | 8756 |
| L2M | +767 | 13.2 | 0.06 | 7794 |
| L3M | +780 | 15.6 | 0.05 | 5982 |
| L6M | +1361 | 15.6 | 0.09 | 3616 |
| HOLD | +478 | 19.6 | 0.02 | 2117 |
| MID | +8 | 10.0 | 0.00 | 3322 |
| PRE | +314 | 15.8 | 0.02 | 1032 |
| X' | +23 | 16.7 | 0.00 | 1219 |
By year (net $ of the trade list): 2023: 51 trades +4247$ (hit 39%) / 2024: 72 trades +12201$ (hit 42%) / 2025: 97 trades -12324$ (hit 33%) / 2026: 97 trades +32797$ (hit 40%). By quarter: 2023Q2 +4728 | 2023Q3 -762 | 2023Q4 +281 | 2024Q1 -11135 | 2024Q2 -5817 | 2024Q3 +24561 | 2024Q4 +4592 | 2025Q1 +7170 | 2025Q2 +910 | 2025Q3 -20006 | 2025Q4 -398 | 2026Q1 -892 | 2026Q2 +24984 | 2026Q3 -3125 | 2026Q4 +11829.
Placebos x100: shift5 L6M 0.03 / HOLD 0.02 / stack-gain 0.05, random side L6M 0.07 / HOLD 0.16 / 0.32, shuffled day L6M 0.02 / HOLD 0.09. CAL R_F40 ON state: 181 trades, 2023-25 same switch PRE +77 / X' +60 (CONDITIONAL by CAL's rule, thin). Genuine PA9 of the stack Calmar gain at 0.5x: HOLD -0.004 (positive in 1 of 9 phases), L6M +0.122 (9 of 9). Stack with the corrected carrying weeks:
| scale | window | stack Calmar before -> after | stack maxDD before -> after ($k) |
|---|---|---|---|
| 0.5x | L6M | 0.695 -> 0.796 | 62.6 -> 55.9 |
| 0.5x | HOLD | 0.228 -> 0.230 | 122.0 -> 122.2 |
| 0.5x | PRE | 0.202 -> 0.207 | 75.1 -> 73.7 |
| 0.5x | X' | 0.061 -> 0.063 | 49.4 -> 46.8 |
| 0.5x | HOLD_dropH | 0.252 -> 0.257 | 104.8 -> 104.1 |
| 1.0x | L6M | 0.695 -> 0.925 | 62.6 -> 49.2 |
| 1.0x | HOLD | 0.228 -> 0.232 | 122.0 -> 122.3 |
| 1.0x | PRE | 0.202 -> 0.212 | 75.1 -> 72.3 |
| 1.0x | X' | 0.061 -> 0.065 | 49.4 -> 44.2 |
| 1.0x | HOLD_dropH | 0.252 -> 0.261 | 104.8 -> 103.3 |

## 2. The same refill-failure signal at other anchors (pre-stated N2: 24 cells)
| anchor | session | shape | trades | L3M | L6M | HOLD | MID | PRE | X' | gate |
|---|---|---|---|---|---|---|---|---|---|---|
| overnight | nyam | 0.75 ATR 2R T30 | 470 | -645 | -137 | -807 | -931 | -447 | -361 | - |
| overnight | nyam | 0.75 ATR 2R T60 | 470 | -48 | +229 | -524 | -832 | -221 | -280 | - |
| overnight | nyam | 1.50 ATR 2R T30 | 470 | -892 | +424 | -652 | -2767 | +381 | -37 | - |
| overnight | nyam | 1.50 ATR 1R T30 | 470 | -181 | +244 | -291 | -173 | +319 | -314 | - |
| overnight | nypm | 0.75 ATR 2R T30 | 279 | -898 | -1175 | -143 | -39 | -63 | +280 | - |
| overnight | nypm | 0.75 ATR 2R T60 | 279 | -506 | -1004 | -73 | -68 | -132 | +320 | - |
| overnight | nypm | 1.50 ATR 2R T30 | 279 | -598 | -875 | -223 | +82 | -197 | +446 | - |
| overnight | nypm | 1.50 ATR 1R T30 | 279 | -730 | -938 | -119 | +56 | -27 | +458 | - |
| prevday | nyam | 0.75 ATR 2R T30 | 317 | +622 | +1108 | +415 | -138 | +202 | -36 | TOLERANT |
| prevday | nyam | 0.75 ATR 2R T60 | 317 | +780 | +1361 | +478 | +8 | +314 | +23 | STRICT |
| prevday | nyam | 1.50 ATR 2R T30 | 317 | +134 | +857 | +445 | +633 | +108 | -168 | TOLERANT |
| prevday | nyam | 1.50 ATR 1R T30 | 317 | +185 | +435 | +40 | -203 | +310 | -211 | TOLERANT |
| prevday | nypm | 0.75 ATR 2R T30 | 222 | -2091 | -860 | -817 | -2541 | -189 | -295 | - |
| prevday | nypm | 0.75 ATR 2R T60 | 222 | -1984 | -652 | -839 | -2702 | -260 | -189 | - |
| prevday | nypm | 1.50 ATR 2R T30 | 222 | -1743 | -932 | -623 | -842 | -297 | -274 | - |
| prevday | nypm | 1.50 ATR 1R T30 | 222 | -1817 | -912 | -543 | -814 | -217 | -262 | - |
| round50 | nyam | 0.75 ATR 2R T30 | 822 | -3656 | -1484 | -2164 | -3401 | -1228 | -1360 | - |
| round50 | nyam | 0.75 ATR 2R T60 | 822 | -3433 | -1377 | -2108 | -3401 | -1122 | -1639 | - |
| round50 | nyam | 1.50 ATR 2R T30 | 822 | -1013 | +37 | -1452 | -3368 | -194 | -898 | - |
| round50 | nyam | 1.50 ATR 1R T30 | 822 | -962 | -565 | -1324 | -1492 | +63 | -770 | - |
| round50 | nypm | 0.75 ATR 2R T30 | 751 | -354 | +1372 | -59 | -964 | -453 | -521 | - |
| round50 | nypm | 0.75 ATR 2R T60 | 751 | +65 | +2365 | +544 | -1352 | -573 | -17 | NOW-ONLY |
| round50 | nypm | 1.50 ATR 2R T30 | 751 | -1623 | -78 | -281 | -420 | +53 | -181 | - |
| round50 | nypm | 1.50 ATR 1R T30 | 751 | -1328 | +247 | -215 | -589 | -19 | +29 | - |
Family max-T over the 24 N2 cells (100 worlds, random side / shuffled day): HOLD mean family p 0.92 / 0.76, L6M Calmar family p 0.38 / 0.39. Plain sentence: the signal does NOT carry over to the overnight high/low (L6M ~0 to +0.4k, HOLD negative), to round numbers in NY-AM (negative or about zero) or to the previous-day extreme in NY-PM (negative); round numbers in NY-PM show one NOW-ONLY cell (T60: L6M +2.4k, HOLD +0.5k, PRE -0.6k, not tolerant). The refill-failure follow is specific to the previous-day extreme in the NY-AM session.

## DIS-E close
**DIS-E closes: the book-pressure and queue-dynamics series (depth imbalance, cancel / add pressure, refill failure on their own, the liquidity-gated opening-range break, absorption and failure at round numbers and overnight extremes) are not entry signals; the one surviving book is 'follow the break of the previous-day high / low in NY-AM when the book has just shown refill failures' - a plateau, driven by the refill-failure condition (controls flat / negative without it), positive in 3 of 4 years and in every window L1M-X', but thin (317 trades, top-5 trades 72% of its P&L, L6M mean $1.4k/wk inside its $3.6k MDE, stack-gain placebo p .05-.32 on HOLD, family max-T over the small family 0.38-0.92) - a tracked Shadow WATCH, not a lead.**
**Correction note (S4b, same hour):** the lead sits at the 93rd percentile of its N1 neighbourhood on L6M and the 77th on HOLD (the figures in the section text, not the 61st / 60th quoted in the message to the coordinator): it is among the better neighbours, so its own numbers are the flattering end of the plateau; the neighbourhood medians (L6M about +0.39k, HOLD +0.24k, PRE +0.06k per week) are the fairer expectation.


## DIS-J CLOSED (ZL-1, ~22:45Z): L6M-dollar family max-T (652 books, 100 worlds each of random side and shuffled-day)
Family p of the real maximum (best book N_CENT NYAM T4 b1 1R T120, L6M +1,368/wk): 0.41 (side) / 0.040 (shuffled-day). 0 of 652 books reach max-T p <= 0.10 or BH q <= 0.10 (smallest max-T p 0.406, smallest q 0.612); requested books: N_CENT NYAM T4 default L6M +926 p_raw 0.069 / max-T 1.0 / q 0.612; Q_MP NYAM T2 +788 0.069 / 1.0 / 0.612; N_T2K NYAM T4 +657 0.02 / 1.0 / 0.612; N_MP NYAM T4 +272 0.327 / 1.0 / 0.786. With the HOLD-Calmar run (family p 0.17 / 0.32, min q 0.748) and the stage-3 result (option levels do not improve any live book's bracket), **DIS-J ends with no option-OI level book that survives a family test, and no flag.** Reserve item for a later program: SPX/SPXW OPRA and CME weekly option files (data gaps listed in Q4_NQ_STRUCTURE.md).



## DIS-G (Z1) interim row 2 (2026-11-04T20:48Z) post-hoc, no PASS, Shadow only, $0, on-disk
Prereg ADDENDUM 1 l2vast/ds3/prereg/DISG_Z1_addendum1.md sha256 4afeb32c1c31d8ed374cde0760e36060086052d3546fc74821d820b2eddc4367 (DECISIONS.md before any scored statistic); n_tested DISG += 47 (A 20, B 15, C 12) -> DISG 783. Code l2vast/ds3/code/zones3/fade_mz/ (disg_filter.py, disg_filter_run.py, disg_filter_plc.py, disg_ymcond.py, disg_ticks.py); rows appended to autopilot/FADE_ROWS_DISG.md (step A, 20 filter cells).
### Step A: other-index state as a SKIP filter on the six live books (Q1-A ts2, full engine runs, 88,490 library rows; the 'exit' variant needs an engine exit hook and was NOT run)
Base reproduces $2,520,149; stack maxDD (carry dropped) L6M $62.6k, HOLD $122.0k, MID $59.7k, PRE $75.1k, X' $49.4k. Cells (20): F1 NQ-ES stretch (z60 / z390, k = 1, 2), F2 beta-residual (k = 1.5, 2.5), F3 ES 15-min return against the trade (5 / 10 bp), F4 YM-decoupled day (skip or halve), each on all sessions or NY-AM rows only. Screen (cut > 0 on L6M, HOLD and PRE at a tolerant mean): NO cell passes - the L6M cut is exactly 0 for almost every cell (the L6M stack drawdown sits in books these filters do not touch) and the only cells with L6M > 0 (F2 1.5 / 2.5 on all sessions: +9.9% / +17.0%) have PRE -3.5% / -5.6%. Exploratory placebo (not required by the screen) for the four most interesting cells, 50 random skip / half sets of the same size stratified by book x session (full engine runs):
| cell | cut L6M / HOLD / MID / PRE / X' | mean change L6M / HOLD / PRE $/wk | placebo rank of the cut L6M / HOLD / MID / PRE / X' (share of placebos at least as good) |
|---|---|---|---|
| F4 halve all live rows on YM-decoupled days, NY-AM only (13.7% of rows) | 0 / +7.0% / +13.4% / +16.7% / +6.9% | 0 / -400 / -1,062 | 1.00 / 0.33 / 0.31 / 0.04 / 0.65 |
| F4 skip the same rows | 0 / +15.5% / +25.4% / +11.1% / +13.7% | -1,065 / -753 / -3,938 | 0.24 / 0.29 / 0.25 / 0.25 / 0.24 |
| F4 halve all live rows on YM-decoupled days, all sessions (57% of rows) | 0 / +21.5% / +33.6% / +35.9% / 0 | -19,189 / -9,480 / -3,112 | 0.98 / 0.12 / 0.27 / 0.06 / 0.90 |
| F2 skip if side x residual z >= 1.5, all sessions | +9.9% / +6.4% / +3.6% / -3.5% / -25.1% | -2,149 / -1,310 / -2,786 | 0.33 / 0.49 / 0.55 / 0.65 / 0.82 |
Reading: the YM-decoupling halving in NY-AM is better than a random same-size halving only in PRE (rank 0.04 on the cut, 16.7% vs a placebo median 7.4%) and not in HOLD, MID, X' or L6M; the all-sessions version is a volume cut (the flag is ON on 85% of L6M days) whose L6M cut (0%) is worse than random halving (36%). Every other filter is at or below its placebo. Verdict: no filter is a RISK-KEEP or better than random; DEAD for the live stack. Note the F1 k = 1 cells skip 59% of all rows (the 60/390-bar cumulative-spread z is large whenever the spread trends) and are volume cuts (HOLD maxDD -34% / +17%, X' -130% / -89%).
### Step B: YM-decoupling flag as a conditioning variable (daily level, 15 series x 4 windows = 60 tests; circular-shift placebo of the flag, 1,000 shifts)
The flag (trailing 20-day mean ES-YM correlation below its trailing 250-day median) is ON on 85% of L6M days, 69% of HOLD, 58% of PRE, 21% of X': it is a recent-period marker. Differences between flagged and unflagged days: 3 of 60 have p <= 0.05 (expected 3): H7 all sessions PRE (+517/day, p 0.04), M7 all sessions X' (+477, p 0.05), the CAL NY-AM fade bundle in X' (-1,689/day, p 0.01); also CAL bundle HOLD -1,121 (p 0.10), DIS-G G1 NY-AM L6M -618 (p 0.12), swing v2a lead no difference (p 0.2-0.7). No live book or fade book is conditioned by the flag in a way that survives multiplicity.
### Step C: ES / RTY aggressor delta (tick-derived 1-min delta, on disk) as a split of the best G1 / G4 cells (3 cells x 4 splits x 4 windows = 48 tests; permutation placebo of the split label, 1,000 shuffles)
When ES and RTY 5-min delta CONFIRM the fade direction the G4 NY-AM cell does worse: mean $/trade confirm vs not L6M -12 vs +183 (p 0.34), HOLD -91 vs +173 (p 0.06), PRE -198 vs +44 (p 0.03), X' -173 vs -18 (p 0.25); ES 5-min alone L6M -29 vs +284 (p 0.11), HOLD -2 vs +189 (p 0.15); the two G1 cells show no consistent sign (ES5 / RTY5 / ES1 differences +-40..+170 per trade with p 0.11-1.0). 2 of 48 tests have p <= 0.05 (expected 2.4): noise; the sign (flow with the fade = worse) is the same in all four windows for the G4 cell but not for the G1 cells.
Plain sentence: other-index state as a filter on the live books is dead (no cell is better than a random same-size skip except PRE-only for the NY-AM YM-decoupling halving), the YM-decoupling flag conditions nothing that survives multiplicity, and ES/RTY aggressor delta splits the G4 cell only at noise level; DIS-G stays unflagged.
Correction (Z1, interim row 2, step B): 2 of 60 tests have p <= 0.05 (CAL NY-AM fade bundle X' p 0.011, H7 all sessions PRE p 0.043), not 3; M7 all sessions X' is p 0.055. Expected 3 by chance. Step C count (2 of 48 at p <= 0.05: the G4 cell RTY5 confirms PRE p 0.048 and ES5+RTY5 confirm PRE p 0.026) is correct.



## DIS-F: POST-EARNINGS-DAY OVERLAY (CAL; interim 1, 2026-11-04 20:50Z; no PASS claims; ledger DIS_F 50 cells; rows FADE_ROWS_DISF.md; n_tested line DISF in FADE_NTESTED.md)
Prereg l2vast/ds3/prereg/DISF_prereg.md sha256 da35cf2b9f5247431085ed533dbf28bec2feb61758707a58b777b8cf5927353f (logged in DECISIONS.md 19:24Z before any scoring); dead_lookup before (no earlier earnings-day overlay cell; only CAL's own Q4_CAL flag cells) and append_cells after. Base: live Q1-A ts2 stack (sizer_harness engine, live lot order, integer lots, ts2 live fill model); fade books = CAL corrected study lists at live latency (2 lots each, added at 1x); carry-dropped columns use the corrected episodes (2026 W30-W37, PRE 2025 W06-W09). Flags known at the prior close: F8 = day after a top-8 mega-cap after-close report (88 of 935 days), F16 = top-16 (173 days). Cells: 2 flags x 5 variants (SIZE x0.5 / x1.5 / x2.0 on flagged days, FILTER_ON = only flagged days trade, FILTER_OFF = no trade on flagged days) x 5 targets (live NY-AM sleeve in the engine; ONRTH, VWAPF, ORBF, three-book bundle) = 50.
Plain sentence: a post-earnings-day overlay does NOT earn a place: the best cell raises the stack's HOLD Calmar by only +0.079 (live NY-AM entries only on days after a top-16 report) and does it by cutting the sleeve (L6M Calmar -0.019, PRE -0.027); the family max-stat (150 worlds) gives p = 0.225 for the best cell and every BH q is >= 0.91. The earlier amplifier p's (.013 / .001) were single cells of a 66-cell family (family p 0.018) and as an overlay they do not survive placebos and the recent windows.
Statistic S = change in the stack's HOLD Calmar (carry dropped) from the overlay; p_raw = the worst of three placebos (P1 shifted calendar +-1..5 trading days: only 10 shifts, so its floor is 0.09; P2 random day sets of the same size: 100 draws for engine cells, 200 for fade cells; P3 circular shift of the flag vector by >= 30 days, same counts). Family max-stat = 150 worlds with random day sets replacing both flags in all 50 cells: world-max median 0.057, p95 0.117, real max 0.079. Top 10 cells by S:
| flag | variant | target | dCalmar HOLD | dCalmar L6M | dCalmar PRE | dMaxDD HOLD | p_P1/P2/P3 -> worst | family p | BH q |
|---|---|---|---|---|---|---|---|---|---|
| EARN_PREV_AMC16 | FILTER_ON | SLEEVE | +0.0791 | -0.0185 | -0.0274 | -30,332 | 0.09/0.040/0.050 -> 0.09 | 0.225 | 0.91 |
| EARN_PREV_AMC16 | FILTER_OFF | BUNDLE3 | +0.0612 | -0.0660 | -0.0117 | -16,337 | 0.27/0.015/0.030 -> 0.27 | 0.444 | 1.00 |
| EARN_PREV_AMC16 | SIZE2.0 | SLEEVE | +0.0409 | -0.0040 | +0.0096 | -13,701 | 0.09/0.030/0.020 -> 0.09 | 0.762 | 0.91 |
| EARN_PREV_AMC8 | FILTER_ON | SLEEVE | +0.0359 | -0.0365 | -0.0586 | -20,420 | 0.36/0.426/0.564 -> 0.56 | 0.887 | 1.00 |
| EARN_PREV_AMC16 | SIZE1.5 | SLEEVE | +0.0333 | -0.0040 | +0.0042 | -11,788 | 0.09/0.010/0.020 -> 0.09 | 0.914 | 0.91 |
| EARN_PREV_AMC8 | FILTER_OFF | VWAPF | +0.0284 | -0.0016 | -0.0028 | -7,640 | 0.09/0.005/0.025 -> 0.09 | 0.987 | 0.91 |
| EARN_PREV_AMC16 | SIZE0.5 | BUNDLE3 | +0.0280 | -0.0343 | -0.0061 | -8,169 | 0.36/0.040/0.040 -> 0.36 | 0.987 | 1.00 |
| EARN_PREV_AMC8 | FILTER_OFF | BUNDLE3 | +0.0235 | -0.0738 | -0.0179 | -8,227 | 0.36/0.134/0.149 -> 0.36 | 1.000 | 1.00 |
| EARN_PREV_AMC16 | FILTER_OFF | ORBF | +0.0138 | -0.0695 | -0.0013 | -7,640 | 0.64/0.075/0.075 -> 0.64 | 1.000 | 1.00 |
| EARN_PREV_AMC8 | SIZE0.5 | VWAPF | +0.0136 | -0.0008 | -0.0014 | -3,820 | 0.09/0.005/0.025 -> 0.09 | 1.000 | 0.91 |

Counts: 23 of 50 cells have S > 0 (about 25 expected by chance); 16 have a positive L6M Calmar change; only 4 have both HOLD and L6M positive (F16 FILTER_OFF and SIZE0.5 on ONRTH and VWAPF: +0.0075/+0.0036, +0.0037/+0.0018, +0.0009/+0.0015, +0.0004/+0.0007; p_raw 0.18-0.36, family p 1.0), i.e. only 'trade the fades slightly less on post-earnings days', worth under 0.01 Calmar. No cell passes the prereg screen (S > 0, L6M change > 0, PRE change >= -0.02, p_raw <= 0.10, BH q <= 0.20).
Genuine PA9 (nine lock-reset phases, engine runs, corrected episodes) for the three sleeve cells with p_raw 0.09 (F16 SIZE x1.5, SIZE x2.0, FILTER_ON): stack maxDD cut % averaged over phases: L6M -4.4 / -5.0 / +3.6, HOLD +9.7 / +9.8 / +17.2, MID +7.1 / +4.8 / +37.5, PRE -15.2 / -17.4 / -10.1, X' +16.1 / +22.6 / -0.3; the PA9 bands (about 19-22% for L6M / HOLD) are met by none, and the size multipliers DEEPEN the L6M and PRE drawdowns. The shadow-fade cells are outside the engine (PA9 not applicable).
Power (flagged days per window; day-level MDE = 2.8 x SE of flagged-minus-other): F8 flagged days L1M 3, L3M 5, L6M 11, HOLD 21, MID 4, PRE 35, X' 24; F16 L1M 5, L3M 11, L6M 23, HOLD 46, MID 10, PRE 66, X' 45. Live NY-AM sleeve, F16, difference vs MDE ($/day): L6M -311 vs 2,593; HOLD +1428 vs 2,747; PRE +2407 vs 3,037. Fade bundle, F8: L6M +3650 vs 4,119; HOLD +1354 vs 3,786. In the recent windows (L1M..L6M, 3-23 flagged days) every effect is inside its MDE: the recent windows can neither confirm nor kill the overlay; only HOLD / PRE / X' have enough flagged days, and the sleeve's post-earnings premium sits in 2023-25 (PRE +2,407 $/day for F16) rather than 2026 (L6M -311).
Verdict: no overlay carried; the post-earnings-day flag stays a descriptive fact (Q4_NQ_STRUCTURE.md, section CAL).



# DS3_DISCOVER2 - section S4b: DIS-L NQ book state at the open (09:30-09:35) -> OR-break direction - interim 1, 2026-11-04 20:51Z
Prereg autopilot/DIS_L_PREREG.md (sha256 in DECISIONS.md; n_tested 92 in DISL_NTESTED.md; two deviations / additions logged before the trading cells); ledger DIS_L; rows FADE_ROWS_DISL.md; code l2vast/ds3/code/disc/ (dl_feat.py, dl_analyze.py, dl_trade.py); data /mnt/l2/l2vast/ds3_dl/. Shadow only, no PASS claims. Target: the first 1-min close beyond the 30-minute opening range between 10:00 and 11:30 ET (900 days with a break 2023-04..2026-10, up share 52%); features from the NQ 1-s L2 tables (MBO-derived book / queue / flow fields) over 09:30:00-09:34:59.

## (a) Which open features predict the break direction (block permutation, 5-day blocks; MDE |rho| 0.09 at n = 900)
| feature | rho with up-break | AUC | n | block-perm p | BH q (16) | MDE | 2026 only rho (p) | before 2025-10-23 rho (p) |
|---|---|---|---|---|---|---|---|---|
| F7 large-print imbalance | +0.135 | 0.576 | 709 | 0.0005 | 0.003 | 0.11 | +0.116 (0.124) | +0.155 (0.000) |
| F5 OFI5 share | +0.186 | 0.608 | 900 | 0.0005 | 0.003 | 0.09 | +0.153 (0.031) | +0.195 (0.000) |
| F11 first-5-min return / ATR | +0.182 | 0.605 | 900 | 0.0005 | 0.003 | 0.09 | +0.133 (0.051) | +0.195 (0.000) |
| F1 first-5-min aggressor delta share | +0.101 | 0.558 | 900 | 0.0040 | 0.016 | 0.09 | +0.060 (0.362) | +0.097 (0.016) |
| F10 queue-absorption imbalance | -0.080 | 0.453 | 900 | 0.0160 | 0.043 | 0.09 | -0.096 (0.155) | -0.067 (0.086) |
| F2 mean 5-level depth imbalance | -0.081 | 0.453 | 900 | 0.0160 | 0.043 | 0.09 | -0.035 (0.625) | -0.093 (0.019) |
| F12 first-5-min range / ATR | -0.076 | 0.456 | 900 | 0.0265 | 0.058 | 0.09 | -0.085 (0.210) | -0.078 (0.048) |
| F8 cancel pressure | +0.071 | 0.541 | 900 | 0.0290 | 0.058 | 0.09 | -0.078 (0.277) | +0.113 (0.003) |
| F16 trade-rate surge | -0.062 | 0.464 | 895 | 0.0600 | 0.102 | 0.09 | -0.095 (0.175) | -0.051 (0.187) |
| F6 sweep imbalance | +0.059 | 0.534 | 900 | 0.0640 | 0.102 | 0.09 | +0.020 (0.784) | +0.055 (0.168) |
| F14 depth5 | -0.048 | 0.472 | 900 | 0.1309 | 0.190 | 0.09 | -0.034 (0.664) | -0.052 (0.183) |
| F13 spread | +0.044 | 0.525 | 900 | 0.1649 | 0.205 | 0.09 | +0.036 (0.626) | +0.047 (0.233) |
| F3 mean level-1 imbalance | -0.046 | 0.473 | 900 | 0.1664 | 0.205 | 0.09 | +0.007 (0.916) | -0.058 (0.132) |
| F4 microprice offset | -0.041 | 0.476 | 900 | 0.2099 | 0.240 | 0.09 | +0.029 (0.674) | -0.058 (0.132) |
| F15 refill-failure count | +0.034 | 0.517 | 900 | 0.3053 | 0.326 | 0.09 | +0.057 (0.450) | +0.030 (0.437) |
| F9 add pressure | +0.004 | 0.502 | 900 | 0.9020 | 0.902 | 0.09 | +0.122 (0.079) | -0.031 (0.426) |
Plain sentence: four open features carry a real, same-direction signal on which way the opening range breaks - the first-5-min return (rho +0.18, AUC 0.605), the 5-min order-flow-imbalance share (+0.19, AUC 0.608), the large-print imbalance (+0.14, AUC 0.576) and the aggressor delta share (+0.10, AUC 0.558), all BH q <= .016 - a continuation: early buying pressure means the range breaks up. The queue-dynamics fields (depth imbalance, cancel / add pressure, refill failure, microprice, spread, depth, trade-rate surge) do not predict it (q > .04, and the depth-imbalance and queue-absorption signs are slightly negative).

## (b) Walk-forward models (expanding window, 150-day minimum, 2-day purge, monthly refit, test 2024-02..2026-10)
| model | OOS days | AUC | accuracy | log-loss (base) | permutation p |
|---|---|---|---|---|---|
| M16 | 668 | 0.583 | 0.582 | 0.6817 (0.6906) | 0.002 |
| M3 | 668 | 0.615 | 0.584 | 0.6699 (0.6906) | 0.002 |
| MF11 | 668 | 0.610 | 0.578 | n/a | 0.003 |
| M4 | 668 | 0.620 | 0.579 | n/a | 0.003 |
Plain sentence: the book state predicts the break direction out of sample with AUC 0.58-0.62 and 58% accuracy (permutation p .002-.003), stable before the break date (AUC 0.59-0.64) and in 2026 (0.57); but the first-5-min return ALONE gives AUC 0.610 and the four-feature model 0.620: the MBO-derived book state adds about +0.01 AUC to what the price move already says. The 16-feature model is worse (0.583) than the 3-feature one (0.615).

## (c) 40 trading cells (live fill model, gate_v3, corrected carrying weeks; lots capped at 6)
Baseline - every break traded WITH, unconditioned: stop 0.75 ATR 1R: 868 breaks, L6M -733, HOLD -1717, PRE -919 / stop 0.75 ATR 2R: 868 breaks, L6M +327, HOLD -1517, PRE -43 / stop 1.50 ATR 1R: 868 breaks, L6M -1665, HOLD -2198, PRE +332 / stop 1.50 ATR 2R: 868 breaks, L6M -1778, HOLD -1860, PRE +517.
| rule | cells | median trades | median L6M | median HOLD | median PRE | NOW-ONLY | TOLERANT |
|---|---|---|---|---|---|---|---|
| fade | 20 | 398 | +579 | +674 | -668 | 9 | 0 |
| with | 20 | 417 | -430 | -972 | -68 | 4 | 1 |
Best 8 by L6M:
| predictor | rule | stop ATR | R | trades | L3M | L6M | HOLD | MID | PRE | X' | L6M MDE | gate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M16 | fade | 0.75 | 2 | 279 | +2019 | +1522 | +1263 | -964 | -510 | +0 | +2940 | NOW-ONLY |
| F1 | fade | 0.75 | 2 | 398 | +1765 | +1338 | +1762 | -123 | -772 | -915 | +2757 | NOW-ONLY |
| F2 | fade | 0.75 | 2 | 472 | +624 | +964 | +1901 | +2091 | -1159 | -158 | +2304 | NOW-ONLY |
| F2 | fade | 1.50 | 2 | 472 | +341 | +932 | +1208 | +1582 | -1182 | +800 | +1893 | NOW-ONLY |
| F1 | fade | 1.50 | 2 | 398 | +206 | +920 | +497 | -347 | -990 | -1196 | +2232 | NOW-ONLY |
| F11 | fade | 1.50 | 1 | 379 | -295 | +874 | +893 | +87 | -639 | -722 | +1793 | - |
| F11 | fade | 1.50 | 2 | 379 | -424 | +858 | +433 | -111 | -969 | -842 | +1807 | - |
| M16 | fade | 1.50 | 1 | 279 | +620 | +776 | +553 | -913 | -11 | +0 | +1627 | NOW-ONLY |
**Family max-T over the 40 cells (100 worlds):** HOLD mean family p 0.109 (random side) / 0.010 (shuffled day); L6M Calmar 1.000 / 0.782.
Plain sentence: knowing the direction does not make a book. Trading the break WITH the book-state prediction loses or is flat in every window (median L6M -430, HOLD -972; no cell clears the gate except one M16 cell with a negative HOLD and MID); the FADE of a break that the book state did not expect pays in L6M / HOLD (median L6M +579, HOLD +674, up to +1.5k / +1.3k per week for the 16-feature model at 0.75 ATR 2R) but loses in PRE and X' (REGIME), no fade cell is TOLERANT, and the family null does not separate the best cell (HOLD mean family p 0.109 against random sides, 0.010 against shuffled days; L6M Calmar 0.78-1.0). The Q4 hypothesis (liquidity at the open and the OR-break outcome) is therefore reproduced as a PREDICTION result (price move and flow at the open predict the break direction) but not as a tradeable book.

## DIS-L close
**DIS-L closes (interim, no lead):** the open book state predicts the OR-break direction (OOS AUC about 0.6, stable across the 2025-10-23 break date) but only through the first 5 minutes' price move and order flow (+0.01 AUC from the MBO-derived features); no WITH or FADE book built on it clears the tolerant gate, the family null, or the PRE / X' years; recorded as a tracked prediction fact (the opening 5 minutes tell the break direction ~58% of the time), not a book.


## DIS-G CLOSED (2026-11-04T20:53Z) - plain sentence
DIS-G is closed with no flag: across 783 tested items (736 NQ entry cells driven by the state of ES, RTY and YM; 20 skip / half filters on the six live books; 15 YM-decoupling conditioning series x 4 windows; 12 ES / RTY aggressor-delta splits of the best cells) the state of the other indexes does not drive a tradable NQ entry or a useful filter beyond what the 2026 NY-AM regime gives any fade-like entry - the best of 728 entry cells has family p 0.56 (G4 beta-residual fade, NY-AM, L6M +$1,280/wk), no cell passes the tolerant gate with placebo p <= 0.10 (21 are tolerant with a failed placebo), none of the 20 live-book filters beats a random same-size skip except the NY-AM YM-decoupling halving in PRE alone (rank 0.04, not in HOLD, MID, X' or L6M), the YM-decoupling flag (on for 85% of L6M days, a recent-period marker) conditions nothing after multiplicity (2 of 60 at p <= 0.05, 3 expected), and ES / RTY aggressor delta splits the G4 cell only at noise level (2 of 48). Open items, not run: the exit-hook variant (a TH-L2-style cut driven by the other indexes; needs an engine hook) and tick-level order flow beyond the 1-min aggressor delta. Ledger DIS_G (748 cells), rows FADE_ROWS_DISG.md (63 + 20), prereg a8f296bb... and addendum 4afeb32c....



# DS3_DISCOVER2 - section S4b: DIS-P the open-direction fact as a side filter / size overlay - interim 1, 2026-11-04 21:00Z
Prereg autopilot/DIS_P_PREREG.md (sha256 in DECISIONS.md; n_tested 176 in DISP_NTESTED.md); ledger DIS_P; rows FADE_ROWS_DISP.md; code l2vast/ds3/code/disc/ (dp_build.py, dp_eval.py, dp_verify.py); data /mnt/l2/l2vast/ds3_dp/. dead_lookup first: no stored cell uses an open-direction overlay (grep 'side filter' 0 rows, 'openflow' 0 rows); neighbouring regions cited, not repeated: 'first5' 230 rows (NTE1, NTE1C, A2DDRR), 'drive' 3,290 rows (SDGAP2f5, DIS_G, NTE1), DIS_L 56 rows. Shadow only, no PASS claims, no purchases.

## Design
The DIS_L predictors (first-5-min return, OFI5 share, their composite, the walk-forward M4 probability; all known at 09:35) are applied to entries in 09:35-10:30 ET only (entries before 09:35 are excluded: K7/H7/M7 NY-AM 2,426 eligible rows (all three together), Shadow ONRTH 310, VWAPF 960, ORBF 778, O7 397, OR15 628, VB2 503 trades). A trade 'agrees' when its side equals the predicted break direction. Actions: skip when it disagrees, x0.5 when it disagrees, x1.5 when it agrees, both. **Sizing constraint found:** the live NY-AM lots of K7, H7 and M7 are 1, so x0.5 is impossible (min 1 lot; the x0.5 cells are exactly null in the ts2 engine) and x1.5 rounds to 2 lots (x2); the Shadow lines are run at the study 2 lots (x0.5 -> 1, x1.5 -> 3). 9 books x 4 predictors x 4 actions + 16 NY-AM fade bundle + 16 live-three = 176 cells.

## Screen (paired daily difference from the row-level trade $; windows with the corrected carrying weeks; delta in $/wk)
| book | cells | NOW-ONLY | TOLERANT | median delta L6M | median delta HOLD | median delta PRE | median L6M MDE |
|---|---|---|---|---|---|---|---|
| BUNDLE | 16 | 5 | 0 | -582 | -819 | +962 | +2141 |
| H7 | 16 | 4 | 3 | -213 | -17 | +67 | +783 |
| K7 | 16 | 4 | 2 | -98 | -112 | +203 | +900 |
| LIVE3 | 16 | 4 | 2 | -368 | -148 | +396 | +2160 |
| M7 | 16 | 4 | 0 | -17 | -26 | +171 | +1010 |
| O7 | 16 | 0 | 0 | +0 | +119 | +302 | +0 |
| ONRTH | 16 | 5 | 0 | -258 | -234 | +83 | +663 |
| OR15 | 16 | 4 | 0 | -1381 | -597 | +344 | +2596 |
| ORBF | 16 | 7 | 1 | -89 | -243 | +459 | +1181 |
| VB2 | 16 | 7 | 0 | -94 | -79 | -52 | +772 |
| VWAPF | 16 | 0 | 0 | -200 | -285 | +417 | +1342 |
Cells NOW-ONLY (delta L3M and L6M > 0) 44, overlay-TOLERANT 8 (no worse than -0.5 MDE in PRE and X', stack / book maxDD not more than 2% worse in HOLD and PRE). Family max-T over all 176 cells (100 worlds, shifted-feature-day): family p of the best delta L6M 0.96, of the best delta HOLD 0.79; smallest cell-level max-T p 0.96 (L6M) / 0.79 (HOLD); BH q >= 0.9. Placebo p of NOW-ONLY cells (worst of shifted-feature-day, random same-count rows, random direction with the same up-share): 1 of 44 NOW-ONLY cells have p <= .10 on L6M, 0 on HOLD.

## The overlay-TOLERANT cells
| book | predictor | action | acted rows | delta L1M | L3M | L6M | HOLD | MID | PRE | X' | L6M MDE | placebo p L6M / HOLD (worst of 3) | family max-T p L6M / HOLD | PA9 L6M / HOLD / PRE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE3 | P2 | A1 | 2426 | +1628 | +1247 | +840 | +232 | +310 | +273 | +59 | +2147 | 0.52 / 0.54 | 0.96 / 1.00 | +0.078 / -0.013 / -0.048 |
| LIVE3 | P3 | A1 | 2426 | +2001 | +1640 | +811 | +280 | +370 | +231 | -94 | +2078 | 0.51 / 0.61 | 0.99 / 1.00 | +0.078 / -0.021 / -0.053 |
| ORBF | P3 | A4 | 778 | +39 | +544 | +512 | +81 | +380 | +365 | -198 | +1323 | 0.13 / 0.40 | 1.00 / 1.00 | +0.002 / +0.009 / +0.003 |
| K7 | P2 | A1 | 904 | +1156 | +763 | +486 | +245 | +63 | +125 | -64 | +754 | 0.50 / 0.57 | 1.00 / 1.00 | +0.060 / -0.010 / -0.026 |
| H7 | P3 | A1 | 612 | +616 | +569 | +393 | +131 | +47 | -74 | +23 | +663 | 0.62 / 0.45 | 1.00 / 1.00 | +0.014 / -0.004 / -0.009 |
| K7 | P3 | A1 | 904 | +1156 | +817 | +377 | +264 | +171 | +192 | -78 | +782 | 0.50 / 0.54 | 1.00 / 1.00 | +0.060 / -0.015 / -0.026 |
| H7 | P1 | A1 | 612 | +716 | +399 | +291 | +12 | -212 | -27 | -43 | +773 | 0.73 / 0.67 | 1.00 / 1.00 | +0.002 / -0.004 / +0.007 |
| H7 | P2 | A1 | 612 | +368 | +184 | +189 | +38 | +44 | -23 | +51 | +691 | 0.89 / 0.64 | 1.00 / 1.00 | +0.014 / -0.001 / -0.002 |

## Engine verification of the stack-book cells (ts2 + lots_mult / extra_skip hooks, Q1-A reference, lock R scaled by the factor)
| cell | engine total delta ($, whole history) | linear approximation | corr (daily) | delta mean L6M / HOLD / PRE ($/wk) | delta stack maxDD L6M / HOLD / PRE ($k; negative = better) |
|---|---|---|---|---|---|
| ('K7', 'P2', 'A1') |  +32486 | +28609 | 0.95 | +790 / +405 / +113 | -3.6 / +1.6 / +5.6 |
| ('K7', 'P3', 'A1') |  +34700 | +33206 | 0.95 | +536 / +370 / +156 | -3.6 / +1.6 / +5.6 |
| ('H7', 'P1', 'A1') |  -7105 | -7105 | 1.00 | +292 / -38 / -41 | -1.6 / +0.4 / -0.6 |
| ('H7', 'P2', 'A1') |  -3206 | -2992 | 1.00 | +173 / +4 / -31 | -1.6 / +0.4 / +1.3 |
| ('H7', 'P3', 'A1') |  -3337 | -3337 | 1.00 | +264 / +28 / -74 | -1.6 / +0.4 / +1.3 |
| ('LIVE3', 'P2', 'A1') |  +40073 | +39520 | 0.98 | +934 / +203 / +242 | -6.7 / +2.9 / +9.7 |
| ('LIVE3', 'P3', 'A1') |  +30118 | +31733 | 0.99 | +628 / +130 / +181 | -6.7 / +2.9 / +9.7 |
Plain sentence: skipping the NY-AM entries of K7 / H7 / M7 (or of the live three together) that disagree with the open prediction raises the L6M mean by +0.2 to +0.9k/wk and cuts the L6M stack maxDD (-3.6k K7, -6.7k live three), but it RAISES the HOLD stack maxDD (+1.6k, +2.9k) and the PRE stack maxDD (+5.6k, +9.7k): the filter removes recent losers and some earlier hedge; every delta is inside its paired MDE (K7 +0.49k vs 0.75k; live three +0.84k vs 2.1k), the placebos are at chance (p .5-.9), the family p is 0.96 / 0.79, and PA9 of the stack maxDD cut is only +0.06-0.08 in L6M and negative in HOLD / PRE. The x1.5-when-agree overlay on M7 doubles the NY-AM lot (1 -> 2) and the engine shows no benefit (see rows).

## (b) Does the fade work when the open prediction was wrong? (NY-AM fade bundle and the other Shadow lines; mean $ per trade at the study lots; agree = the trade side equals the predicted break direction, i.e. the fade fights a break the open did NOT predict)
| book | predictor | trades agreeing (side = predicted direction) | disagreeing | mean $/trade agree | disagree | 2026 agree | 2026 disagree | 2026 acted trades |
|---|---|---|---|---|---|---|---|---|
| ONRTH | P1 | 87 | 223 | +262 | +105 | +1453 | +583 | 70 |
| ONRTH | P2 | 92 | 218 | +181 | +136 | +1567 | +575 | 70 |
| ONRTH | P3 | 89 | 221 | +229 | +117 | +1361 | +638 | 70 |
| ONRTH | P4 | 82 | 155 | +274 | +37 | +1671 | +465 | 70 |
| VWAPF | P1 | 552 | 406 | -24 | -35 | +19 | +289 | 258 |
| VWAPF | P2 | 534 | 426 | +105 | -184 | +23 | +284 | 258 |
| VWAPF | P3 | 540 | 420 | +31 | -93 | +87 | +207 | 258 |
| VWAPF | P4 | 425 | 347 | +51 | -50 | -32 | +355 | 258 |
| ORBF | P1 | 332 | 443 | -166 | -79 | +314 | +337 | 181 |
| ORBF | P2 | 315 | 463 | -48 | -146 | +537 | +188 | 182 |
| ORBF | P3 | 324 | 454 | -67 | -135 | +564 | +151 | 182 |
| ORBF | P4 | 258 | 341 | -119 | -92 | +438 | +253 | 182 |
| O7 | P1 | 367 | 30 | +398 | +267 | +1712 | +894 | 19 |
| O7 | P2 | 343 | 54 | +422 | +172 | +1820 | +898 | 19 |
| O7 | P3 | 356 | 41 | +382 | +443 | +1600 | +1759 | 19 |
| O7 | P4 | 245 | 46 | +644 | +262 | +1923 | +40 | 19 |
Plain sentence: for ORBF (which fades the break) a trade whose side agrees with the open prediction is a fade of an unexpected break; its mean is no better than the disagree trades (all years -166 vs -79 $/trade; 2026 +314 vs +337); ONRTH and OR15 earn more when the side agrees with the open (ONRTH 2026 +1,453 vs +583 per trade on 70 trades, OR15 2026 +226..+440 vs +700..+890 the other way), the signs are not stable across predictors, and the best bundle overlay (x1.5 when it agrees, composite predictor) adds +0.76k/wk in L6M and +2.3k in MID but loses -0.23k / -0.66k in PRE / X' (REGIME). **Nothing separates 'the fade works when the open was wrong'.**

## (c) O7 drive vs open-flow agreement
O7 trades with the drive, and the drive direction almost always agrees with the first-5-min price/flow (356 of 397 O7 trades agree for the composite predictor); the 41 disagreeing trades earn +443 $/trade (2026: 19 trades) against +382 for the agreeing ones, so skipping them removes P&L; 0 of 16 O7 cells is NOW-ONLY. The gate is not a filter on O7.

## DIS-P verdict
No overlay of the open-direction fact on the live or Shadow NY-AM books survives: every positive delta is inside its MDE, the placebos and the family max-T (0.96 / 0.79) are at chance, the skip filters on K7 / H7 / M7 trade L6M gains for HOLD / PRE drawdown, and the fade-bundle and O7 questions are answered no. The open-direction fact (DIS_L) stays a prediction fact, not a trading edge on the existing books.


## DIS-Q (CAL, 2026-11-04) LATE-DAY BOOKS 15:00-16:55 - interim, no PASS claims
Prereg l2vast/ds3/prereg/DISQ_prereg.md sha256 aa115f2ddb8272f8c2d8b7c6ebc92c2858c6525042fae50b016c51cb95ce4f5a (DECISIONS.md). Code l2vast/ds3/code/discover/{disq.py, disq_supp.py, disq_report.py}; out/disq_cells.csv, disq_p1fine.csv, disq_engine_bucket.csv; rows FADE_ROWS_DISQ.md; ledger DIS_Q (440 cells appended; 120 thin WITCH/RUSS rows carry clk=nan); n_tested line DISQ = 440 in FADE_NTESTED.md.
Dead lookup first: only DISC_C (mine) covers 15:30 look30/60 reversal/continuation (fade look30 60/60 L6M +310 / HOLD -454, DEAD) and the 15:50 MOC proxy by calendar (thin, DEAD); NTE1 moc/close_nypm rows are size/skip actions. Not covered, hence tested: day-drift, range-position and signed-volume triggers, post-close 16:00-16:55 entries, witching/rebalance cross-tabs.
Design: 5 clocks (15:00, 15:30, 15:50, 16:00, 16:30) x triggers M30 / DRIFT (vs 09:30 open) / IMB (10-min signed 1-min volume proxy, data end 2026-10-16; no real MOC feed on disk) / RPOS (day range position >= 0.8 or <= 0.2), each cont and fade, conditions ALL / EXT / MID, shapes 60/60 and 1R-ATR, 2 lots, 60 min time stop, live flat 16:55. 200 eligible cells; calendar cells (MEND 84 trades per book, OPEXM 29; WITCH and RUSS under 15 trades, not run) descriptive.
Results (200 eligible cells, S = mean $/wk over L6M, HOLD, MID, PRE, X' at 2 lots):
1. Continuation loses: mean S cont -318 $/wk vs fade +9; the cost line is about -155 $/wk per direction, so the family is a coin flip net of cost. 53 of 200 cells have S > 0; 31 are positive in L6M/HOLD but not PRE/X' (REGIME, NOW-ONLY); 8 are positive in every window but fail placebo/family; none are LEAD.
2. Best S: 15:50 DRIFT fade ALL 60/60 (n 891): L6M +1,306, HOLD +1,140, MID +1,114, PRE -585, X' -426 -> REGIME (NOW-ONLY), not CONDITIONAL. P2 side p 0.010, P3 trigger p 0.010, clock-shift P1 0.20 (fine grid of 16 shifts 0.059), family p 0.198, BH q 1.0. The 2026 intraday reversal regime again; drawdown (L6M maxDD $11-18k at 2 lots on a $1.1-1.3k/wk mean) is large.
3. Only all-window-positive cell with the tolerant gate True and a stack gain: 15:00 IMB fade ALL 60/60 (n 881): L6M +439, HOLD +1,254, MID +797, PRE +511, X' +166; P1 0.17 (fine 0.053), P2 0.04, P3 0.07, family p 0.40, BH q 1.0; stack Calmar gain 0.5x HOLD +0.00 / L6M +0.00 (zero to two decimals). It is the 14:50-15:00 volume sign, i.e. not an MOC imbalance. WEAK, not carried as a lead: it does not beat the best-of-200 null (null p95 of the world max 1,053 side / 769 shift, real max 854).
4. Calendar cross-tab: month/quarter end shows the best descriptive numbers (16:00 M30 fade MEND 60/60 L6M +227, HOLD +326, PRE +136, n 84) but 84 trades and a day-level MDE of several hundred $/wk; no inference. Witching, Russell day and monthly opex: n too small.
5. The 16:00-16:55 post-cash-close entries (16:00, 16:30) are the weakest clocks (mean S -150, -134).
Live stack P&L by clock bucket, descriptive (Q1-A ts2, taken rows, net_flat at live lots): the engine has NO entries after 15:00 and none in the 'close' session at all. nypm entries are all KB: before 13:00 +$21.7k over 322 trades (+114/wk), 13:00-14:00 -$4.3k (256), 14:00-15:00 -$8.3k (232); since 2026-05: +6.6k / -0.6k / -8.5k. So the live NY-PM book trades only until 15:00; the 15:00-16:55 window is unoccupied by the stack, which is why the late-day books have zero overlap (and no stack gain to speak of).
MDE: weekly L6M MDE 1,200-2,300 $/wk, HOLD 800-1,700 per book (2.8 x SE), as large as most of the S values; only the very top cells exceed it. PA9 not applicable (shadow books outside the engine). Verdict: no late-day book earns a place; 15:50 DRIFT fade is the regime watch item.



## DIS-N (Z1): INTRADAY-CLOCK OVERLAYS on the six live books, interim row 1 (2026-11-04T21:04Z) post-hoc, no PASS, Shadow only, $0, on-disk
Prereg l2vast/ds3/prereg/DISN_Z1_prereg.md sha256 47c84c85d7f311047c0be59aeee38b737e8dffdfc2c16b40773e65a04502094f (DECISIONS.md before any DIS-N statistic); dead_lookup first (9 queries, 0 exact hits; related rows cited: SIZER_S2 112 (time-of-day REMAINING RANGE as a sizing feature), ABRC2 180 DEAD (bracket by time-of-day), THPC2 88 (profit management 'tod'), A11EV / A9EV / A6EV / L2SP hour-total profit exits: none is a clock-bucket skip / half / double of the live signals); n_tested DISN = 817 (777 overlay cells + 40 delay cells). Code l2vast/ds3/code/zones3/fade_mz/ (disn_core.py, disn_sweep.py, disn_exact.py, disn_exact_an.py, disn_delay.py); rows autopilot/FADE_ROWS_DISN.md (40 exact-engine rows, 16 columns); ledger DIS_N.
Method: the taken rows of the six live books in the Q1-A ts2 run (21,646 rows; first-order per-row P&L from the engine's own row table, daily correlation with the true book series 0.947-0.996); 37 clock buckets (minute :00 / :15 / :30 / :45, the 12 five-minute buckets of the hour, 08:30 / 10:00 / 14:00 releases pre5 / post5 / post15 on calendar days, first / last 5 minutes of the six sessions) x 7 scopes (six books, ALL) x skip / half / double; 471 of the 777 cells have >= 5 rows. Surrogate for the family work, exact engine runs (extra_skip / lots_mult) for 40 cells (all 16 surrogate-tolerant cells, the 13 with all three placebos <= 0.10 and the 15 best by score; the surrogate-vs-exact correlation of the score is only 0.71, so exact numbers are the ones quoted).
Counts (471 cells, surrogate): NOW-ONLY 166, TOLERANT 16; exact engine on 40 cells: TOLERANT 8, NOW-ONLY (REGIME) 21. Score S = mean(stack maxDD cut L6M, HOLD), carry dropped. FAMILY max-stat (100 worlds, one random clock shift of +-3..50 minutes applied to ALL cells, statistic = best S): null best S median 0.162, 95th 0.225, max 0.225; the best real cell has S 0.151 (minutes 20-24 of the hour, ALL books, skip: L6M cut +27.8%, HOLD +2.5%, MID -17.5%, PRE -25.8%) -> family p 0.80; no cell has a family p below 0.80 on the surrogate and the BH q over the 109 screened cell-level p-values has minimum 0.14. Random-looking skips of 2-10% of rows routinely cut the L6M / HOLD stack drawdown by 10-25% in this window (a few trades carry the drawdown), which is what the family null measures. Cell-level placebos (clock shift / random same-count rows / shifted P&L order, 100 draws): 13 of the 109 screened cells have all three p <= 0.10 (expected well under 1 if independent; the draws are correlated across cells); none survives the family test.
Exact-engine reading of the cells that pass the tolerant gate (cuts carry-dropped; mean change vs MDE in the rows file):
| cell | rows | stack maxDD cut L6M / HOLD / MID / PRE / X' | mean change L6M / HOLD \$/wk (MDE L6M) | PA9 cut L6M / HOLD / PRE | placebo p (clock / rows / order), family p |
|---|---|---|---|---|---|
| minutes 30-34 | P7 | skip | 415 | +3.6% / +15.8% / +28.4% / +17.2% / +1.7% | -3075 / -426 (7544) | -4.4% / +12.8% / +14.1% | 0.09 / 0.20 / 0.08, 1.00 |
| minute :30 | P7 | skip | 56 | +3.6% / +10.5% / +13.4% / +7.3% / +0.0% | +1 / +688 (3799) | +3.2% / +7.0% / +6.4% | 0.08 / 0.02 / 0.07, 1.00 |
| minutes 30-34 | P7 | half | 415 | +1.8% / +5.1% / +13.7% / +9.3% / +0.4% | -1087 / -410 (2939) | -2.1% / +3.7% / +6.4% | 0.09 / 0.20 / 0.04, 1.00 |
| minute :30 | P7 | half | 56 | +1.8% / +5.0% / +6.7% / +3.6% / +0.0% | +54 / +245 (1822) | +1.6% / +3.7% / +3.5% | 0.05 / 0.04 / 0.03, 1.00 |
| asia first5 | H7 | skip | 173 | +3.7% / +1.6% / +3.2% / +1.2% / +17.5% | +320 / -403 (2114) | +3.7% / +1.1% / +2.0% | 0.02 / 0.16 / 0.04, 1.00 |
| minutes 05-09 | M7 | skip | 305 | +4.4% / +0.4% / +5.1% / +2.3% / +1.3% | +256 / +199 (1173) | +6.3% / -0.7% / +0.5% | 0.03 / 0.16 / 0.18, 1.00 |
| asia first5 | H7 | half | 173 | +1.8% / +0.8% / +1.6% / +0.6% / +10.0% | +121 / -192 (1031) | +1.9% / +0.5% / +0.9% | 0.02 / 0.19 / 0.08, 1.00 |
| london first5 | ALL | skip | 74 | +1.1% / +1.2% / +0.0% / +2.0% / +0.0% | -534 / -452 (1702) | +1.8% / +1.3% / +1.0% | 0.43 / 0.23 / 0.22, 1.00 |
Reading: the two clock cells that look most like a lead are both P7 (PE) cells - the 56 P7 entries at minute :30 (stack maxDD cut HOLD +10.5%, MID +13.4%, PRE +7.3%, L6M +3.6%, X' 0; mean change +\$1 / +\$688 per week against an MDE of \$3,660; PA9 cut +3.2% / +7.0% / +6.4%; placebo p 0.08 / 0.02 / 0.07) and the 415 P7 entries in minutes 30-34 (HOLD +15.8%, MID +28.4%, PRE +17.2%, L6M +3.6%; mean change -\$3,075 / -\$426; PA9 L6M -4.4%). The P7 :30 rows lose money in the sample (-\$41k over 56 rows: +\$23k in 2023, -\$29k in 2024, \$0 in 2025, -\$35k in 2026), so skipping them helps in 2024 and 2026 and hurts in 2023; the family p is 1.00, so a 56-row bucket picked from 471 cells is what chance produces. All-books :30 skip (671 rows, +\$260 / +\$462 weekly mean, HOLD cut +9.6%, L6M +9.7%, PRE +3.6%, X' -0.6%) is the best broad cell and fails the tolerant gate by 0.6 point in X' (placebo p 0.01 / 0.10 / 0.05, family p 1.00). Release-window cells are tiny (15 rows at most in the 14:00 post5 window; 08:30 and 10:00 windows fall in the existing 09:00-09:59 block or in asia/london with few rows) and show no effect; first/last-5-minute session edges give TOLERANT only for 74-173-row cells (asia first5 on M7, london first5 on all books) with L6M cuts of 1-4% and X' cuts of 0-17%.
Entry-delay variants (40 cells: 6 books + 4 session groups x k = 1, 2, 3, 5 minutes; harness-level re-simulation, bracket at the library stop / target, library flat time): the undelayed re-simulation correlates only 0.68-0.76 with the engine daily series for K7, P7, U7, H7, M7 (0.98 for A7), so this is a LOW-FIDELITY screen, not an engine result. No cell is tolerant (0 of 40), 13 are NOW-ONLY, minimum bootstrap p 0.020, minimum BH q 0.59; the largest first-order gains are P7 and London entries delayed 1 minute (+\$258k and +\$155k over the whole period, p 0.16-0.19, cut L6M -14% / -12%: they worsen the stack drawdown), the largest losses are NY-AM entries delayed 2-5 minutes (-\$221k to -\$317k, p 0.02-0.04): a delay is not an overlay that helps, and the fidelity of the screen forbids more.
Plain sentence (interim): intraday-clock effects on the live signals are not distinguishable from the sampling noise of picking a bucket out of 471 - the best real cell has S 0.151 against a null best of 0.162 (family p 0.80), no cell has a family p or a BH q below 0.14, the 8 exact-engine TOLERANT cells are small P7 and session-edge buckets (56-415 rows) whose gains do not repeat across years, and a 1-5 minute entry delay worsens the stack in the low-fidelity screen; nothing is flagged and nothing is applied. Open: a P7-specific :30 follow-up would need a forward register (56 rows in 3.5 years).
Correction (Z1, DIS-N interim 1): (1) the session-edge TOLERANT cell 'asia first5' is on book index 3 = H7 (HM), not M7. (2) Release-window cells have 11-52 taken rows each (08:30 pre5 24, 10:00 pre5 21 / post5 34 / post15 52, 14:00 post5 15 / post15 11; no taken rows exist in the 08:30 post5 / post15 windows); my explanatory clause that they 'fall in the 09:00-09:59 block or in asia/london' was a conjecture and is withdrawn - the fact is only the small counts. (3) The minimum family p over the 471 cells is 0.80 (not 'below 0.80').



## DIS-M (BASE-4): DRIFT BENCHMARK - interim 1 (RESTORED 2026-11-04T22:16Z, short form; the original section was lost; full tables in FADE_ROWS_DISM.md and l2vast/ds3/prereg/DISM_prereg.md + DISM_prereg_addendum1.md)
Drift benchmark books (random-time and fixed-clock long/short books per session x exit shape at live lots and at 1 lot), Shadow-watch candidates and live groups as excess over matched drift, stack with the drift hedged out. Look-ahead in the first placebo P1 found and corrected (addendum 1, causal P1c = delay 5..120 min). After the DIS-AD correction the statistic is the TIMING excess (excess over the delayed same-side entry), not drift. EXCESS survived only for NYAM ORBF (family .08 / .02, BH q .06 / .05) and VB2 NYPM T1 (.05 / .03). Plain sentence: most of the apparent edge of the live groups and watch lines in 2026 is the market's directional drift plus the timing of entries; the live-group NEGATIVE EXCESS labels (e.g. PB asia) are statements about entry timing in 2026.


## DIS-Y (BASE-4): DRIFT-EXCESS TABLE FOR THE WATCH CANDIDATES - interim 1 (RESTORED 2026-11-04T22:16Z, short form; table in FADE_ROWS_DISY.md; prereg l2vast/ds3/prereg/DISY_prereg.md sha256 860b18ca2f9c94ea180df13152816322f3fee19bb9c94f554adc1b85c8bbf9a3; ledger DIS_Y 22 rows; n_tested DISY 22)
22 watch cells as excess over the delayed same-side entry (renamed timing excess by the DIS-AD correction), plus random-side and other-day placebos and a 22-cell family max-T. Four survived (DIS-B N_REL_rev, NYAM ORBF, NYAM fade bundle, VB2 NYPM T1); all four pass the AUDIT_L2 fair benchmarks; the true-drift family test is DIS-AJ (only the NYAM bundle clears). The drift-adjusted RANKED LIST sections are in DS3_DISCOVER.md.


## RE-APPENDED Z2 2026-11-04T22:10Z (file-loss restore): DIS_H and DIS_K sections


## DIS_H - after-stop / after-target follow-on books (Z2, 2026-11-04)
Prereg l2vast/ds3/prereg/DISH_prereg.md sha256 55a4aa636456877b90b996acacc4b0082d656c3b677d281b68d1fe27656e89a6 (+ addendum: RE = add-on position). dead_lookup: no standalone follow-on cell in the ledger; nearest RC1_RA (reverse-confirm exit actions, negative) and RE5_CUTWAIT (DEAD), cited. Rows autopilot/FADE_ROWS_DISH.md; ledger DIS_H (108 cells); DISH_NTESTED 108. Code l2vast/ds3/code/dish/. No PASS claims.
Design: base = six live books (plain-bracket proxy, live Q1-A lots, P3 caveats). RS reverse at the stop second; RE add-on after a stop followed by a same-side base trade within 60 min; SL same-side second leg at the target second; sizes 0.5/1/2x; stop cost join 2.45 / native 1.28; entries by the live model.
Result: nothing survives. Of 108 cells: 86 NULL, 16 tolerant+v2a ("best-of-F"), 6 tolerant with short samples; zero LEAD. Median size-1 L6M/HOLD $/wk: RS -388/+216 (join), RE +277/+4, SL -2465/-1228. The family max-stat kills the positives: the real maximum L6M mean over the 108 cells ($10.1k, L_PE RE 2x, itself gate-failed) is below the median of the 120 null worlds' maxima ($13.2k; 95th pct $24.9k), so p_maxstat is 0.7-1.0 for every cell (the statistic is unnormalised $, so the large-lot books dominate the null max, which makes it conservative for small cells). Tolerant-gate cells: L_PB SL (HOLD +300, L6M +472, but MID -953 and worst placebo p 0.83), L_PB RS (L6M +583, HOLD +876, placebo p 0.14, maxDD $13k), L_HM SL (L6M +1412 but L1M -3338, MID -3386, placebo p 0.72). Drawdowns at live lots are large (L_HM SL maxDD HOLD $48k) relative to the gains. Native 1.28 vs join 2.45 on the follow-on stop leg adds +$50-300/wk per cell but changes no label.
Conclusion: no follow-on book (reverse, re-entry add-on, second leg) shows an edge beyond the shifted-trigger placebo; reversing at the stop does not recover the stop loss (RS L6M median negative); the continuation leg after a target is negative at median. Sessions recent first in FADE_ROWS_DISH.md.


## DIS_K - range compression / expansion books on NQ (Z2, 2026-11-04)
Prereg l2vast/ds3/prereg/DISK_prereg.md sha256 0fcda083228285eb0fe52ce7f8c75517c40d7b8aceb1bd980f086fbe9841ad7d (+ addendum: EX125 threshold; n_tested 356). dead_lookup cited: NTE1 PDR.outside / squeeze skip rows (mostly DEAD), CF2-G1/G2 R_outside / RM_nr4 confirm entries, L2EB PDH/PDL level entries (1,350), SIZER_S2 range_so_far_ratio sizing; no standalone breakout/exhaustion book or state overlay existed. Rows autopilot/FADE_ROWS_DISK.md; ledger DIS_K 356 cells; DISK_NTESTED 356. Code l2vast/ds3/code/disk/, results /mnt/l2/l2vast/ds3_zones3_new/Z2_disk/. No PASS claims.
Design: 919 RTH days (2023-02..2026-10), 15 states (NR4 NR7 INSIDE OUTSIDE CLOSE_TOP/BOT COMP_LO/HI VOV_LO/HI ORC_LO/HI RSF_LO/HI ALL), BO (first 5-min close beyond the 09:30-10:00 range, with / against), EX / EX125 (range-so-far >= 1.5 / 1.25 x bucket median at a day extreme, fade), 2 geometries (60/60 T3600, 40/40 T1800), sessions nyam / nypm / RTH, 2 lots, live fill model; 336 book cells + 20 overlays on the Q1-A ts2 stack. Event counts: 862 BO (823 nyam, ~40 nypm because the first break is usually before 12:00), only 15 EX and 22 EX125 events in 3.5 years - all EX cells and all nypm cells are sample-short.
Result: no LEAD. 324 of 336 book cells NULL, 7 tolerant but sample short, 5 best-of-F (tolerant + gate_v2a): BO WITH-break on COMP_HI days (ATR5/ATR20 in its top third, i.e. expansion state), nyam: G1 L6M +882 / HOLD +785 / PRE +154 (MDE L6M 1,898, maxDD HOLD $9.8k, worst-20 -$33k), G2 L6M +893 / HOLD +557 / PRE +2 (MDE 1,368, maxDD $7.3k); RTH-pooled G1 +873 / +777 / +68. Their three placebos are favourable (shifted-state-date p 0.07-0.12, random side 0.01-0.05, shifted trigger time 0.02-0.08) but the family max-stat over 336 cells gives p_max 0.46-0.47 (the median of the world maxima is $843/wk, the real best cell is $893), the L6M mean is below its own MDE, MID is ~0 to -43 on the RTH pools, PA9 min HOLD Calmar only 0.07-0.08 and the stack Calmar gain is 0.000-0.002. Other best-of-F cells: CLOSE_BOT nyam WITH G2 (L6M +134, p_shift 0.33), ORC_LO nyam AGAINST G2 (L6M +329; p_state 0.02 but p_shift 0.43, p_max 1.00). Medians over all cells: BO WITH L6M -9 / HOLD +1, BO AGAINST 0 / -34, EX ~0 (too few events).
Overlays (state days x 0.5 / 1.5 on the live stack, separate 20-cell family): the largest L6M extra is VOV_HI x1.5 (+7,924/wk, MDE 8,969, p_state 0.28, p_max 0.54, stack Calmar gain HOLD -0.02), none clears the family (p_max >= 0.54), stack-Calmar gains all within +-0.05 and the 1.5x overlays raise HOLD drawdown (COMP_HI x1.5: $134k vs $105k). Conclusion: compression/expansion state does not give a tradeable book or a usable size overlay beyond what the shifted-state placebo and the family max-stat allow; the COMP_HI breakout-with line is the only item worth a forward Shadow watch label (best-of-F), not a lead. Trade list for the watch bundle: /mnt/l2/l2vast/ds3_dist/DISK_comp_hi_trades.csv (282 rows, 2 lots).


## RE-APPENDED ZL-2 2026-11-04T22:30Z (my sections lost in the 21:06Z-21:58Z overwrite; re-appended with >> from MORNING.md / FADE_ROWS_DIST.md, not rewritten)
### DIS-T (ZL-2): watch-bundle portfolio of the 10 best-of-F candidates (condensed; full rows in FADE_ROWS_DIST.md, prereg DISTBUNDLE_prereg.md sha256 35e2d15318f4568f95a1a0f51aca30639248b49ca040278b728a4ba6487bf103, logged in DECISIONS.md 21:06Z before any outcome)
Equal-risk ($1,200 mean $ risk to the stop per trade) weekly $, FadeHarness live fill model, corrected carrying weeks. The ten candidates are nearly independent bets (weekly correlation .02, about 9.5 effective bets, -.08 with the stack). The equal-risk bundle cuts the stack HOLD maxDD by $41k (Calmar +0.18; HOLD_dropH +0.37, PRE +0.02, X' -0.02; survives leave-one-program-out), but 92% of the bundle P&L is 2026 (+$5.9k/wk vs +$165/wk in 2023-25); noise best-of-F would give an L6M sum of $21k vs the real $7.4k (p 1.0); winner's-curse-deflated forward mean is negative (-$3.2k/wk full history); empirical-Bayes tau^2 = 0 (pooled). Reading: a regime-contingent diversifier, expected forward mean between about -$3k and +$5k/wk depending on the selection model. Nothing flagged, nothing live.
Correction/confirmation (ZL-2, 2026-11-04T21:19Z, re-appended): BASE-4 AUDIT-PLC found my Q9/Q10/Q12 shifted-trigger placebos used a signed shift (entries could move earlier than the signal); the delay-only reruns in AUDIT_PLC.md are the valid numbers; no label changes. DIS-T used a noise best-of-F placebo bundle, not a shifted trigger, so no DIS-T label changes. Any time-shift placebo from here on uses only make_placebo(t,'shift5',rng) (forward-only).
### Pointers to my other deliverables (own files, intact): DS3_FWD_DD.md (DIS-V), DS3_STACK_2013.md (DIS-X: validation failed, stopped), DS3_SIGNALS_2013.md (signal-level 2013-2026), DS3_ERA_2023.md (DIS-Z), DS3_ATTRIBUTION.md (DIS-AB), DS3_TH_OOS.md (DIS-AE), DS3_TH_MECHANISM.md (DIS-AI); DIS-AK in progress.


## DIS-M (BASE-4): DRIFT BENCHMARK - interim 1, FULL SECTION RE-APPENDED 2026-11-04T22:19Z (the original was lost from this file; tables below are FADE_ROWS_DISM.md verbatim). Shadow only, no PASS claims, no purchases.
Prereg l2vast/ds3/prereg/DISM_prereg.md sha256 f32b531299744a09a4088c010839c53dbe7dde12df48d3f56bf6aaae52b10104 + addendum 1 (causal P1c) e28ad121ccbeb072e43b94df6e4d5c381e263e4909ca5c380fc328231231a3d3 (DECISIONS.md, the addendum logged after the live-book P1 draws were seen, disclosed); ledger DIS_M 112 rows; n_tested DISM 112; code l2vast/ds3/code/dism/. Harness FadeHarness, Q1-A ts2 base, gate_v3 windows with the carrying weeks dropped, live fill model.
**What was done.** (1) Unconditional drift benchmark books: random-time (100 draws) and fixed-clock (C15 / C60) long and short books per session x exit shape (X1 60/60 T60, X2 60/120 T120, X3 live 60/60 flat 16:55), at 1 lot and live lots. (2) The 20 live book-session groups (engine replica, live ts2 lots) and 21 candidates (Shadow lines and own DIS-I / Q11 cells) re-expressed against matched placebos: P1c = the same trades, same side, entry delayed 5..120 min (causal; the first P1, entry anywhere in the session, placed entries before the signal with the later path's side and is kept only as the look-ahead control P1x), P2 random side, P3 other day same weekday and clock, family max-T over the cells, BH q. (3) The replica stack with the delayed-entry benchmark subtracted (hedged), genuine PA9.
**Results.** Candidates: 2 EXCESS SURVIVES (NYAM ORBF, family .08 / .02, BH q .06 / .05; VB2 NYPM T1, family .05 / .03; nothing is a PASS), 17 DRIFT ONLY / inside the placebo band. Live groups: 4 NEGATIVE EXCESS (below the delayed same-side entry), 16 inside the band. Stack: replica HOLD mean $7363/week vs engine core $22589; the delayed-entry benchmark stack earns $3062/week in HOLD, hedged replica $4302/week; genuine PA9 of the maxDD change of hedged vs replica: L6M -53.4%, HOLD +10.1%, MID +5.2%, PRE +33.5%, X' +25.3%; daily correlation replica vs engine core 0.76, replica total / engine core total 0.63 (the replica is a signal-level approximation, not the live stack).
**Correction note (BASE-4, from DIS-AD):** the 'matched drift' P1c is a TIMING benchmark (delayed same-side entry), not drift; the side-independent random-time drift is the true drift term (items 1 of this section and DIS-AJ). Labels unchanged; see the correction lines below in this file and DS3_PB_ASIA.md.
**Plain sentence (DIS-M):** against a copy of themselves entered later in the same session, only NYAM ORBF and VB2 NYPM T1 of 21 candidates keep a significant excess, and four live groups (including PB asia in 2026) enter worse than their delayed copies; about 42% of the replica stack's HOLD mean ($3062 of $7363 per week) is what delayed same-side entries earn, so the stack's entry timing and exits, not the existence of the side, carry the rest.

### Tables (FADE_ROWS_DISM.md)

# FADE_ROWS_DISM - DIS-M drift benchmark (BASE-4; prereg DISM_prereg.md sha256 f32b531299744a09a4088c010839c53dbe7dde12df48d3f56bf6aaae52b10104 + addendum 1 e28ad121ccbeb072e43b94df6e4d5c381e263e4909ca5c380fc328231231a3d3). $/wk. Nothing is a PASS.


## 1. Unconditional benchmark books, RANDOM-TIME (100 draws, one trade per day-session-side), 1 lot, live fill model
| session | side | exit | L6M | HOLD | MID | PRE | X' | MDE_L6M | 5-95% L6M |
|--|--|--|--|--|--|--|--|--|--|
| asia | LONG | X1 | -184 | -168 | -123 | -41 | -131 | 1017 | -769 .. +321 |
| asia | LONG | X2 | -77 | -103 | -254 | +43 | -146 | 1390 | -821 .. +900 |
| asia | LONG | X3 | +5 | +26 | +362 | +18 | -312 | 1402 | -646 .. +719 |
| asia | SHORT | X1 | -30 | -36 | -107 | -164 | -98 | 1026 | -610 .. +574 |
| asia | SHORT | X2 | -177 | -111 | +11 | -184 | -83 | 1445 | -942 .. +537 |
| asia | SHORT | X3 | -311 | -277 | -483 | -315 | +6 | 1393 | -918 .. +538 |
| london | LONG | X1 | -214 | -172 | -187 | -56 | -54 | 1098 | -831 .. +438 |
| london | LONG | X2 | -461 | -319 | -162 | -139 | -40 | 1545 | -1196 .. +387 |
| london | LONG | X3 | -344 | -256 | -74 | -241 | +249 | 1450 | -1027 .. +357 |
| london | SHORT | X1 | -6 | -70 | -99 | -153 | -139 | 1084 | -543 .. +668 |
| london | SHORT | X2 | -76 | -13 | +26 | -186 | -158 | 1563 | -875 .. +759 |
| london | SHORT | X3 | +116 | -25 | -285 | -75 | -529 | 1452 | -693 .. +992 |
| nyam | LONG | X1 | -96 | -81 | +227 | -45 | +121 | 1338 | -1011 .. +670 |
| nyam | LONG | X2 | -254 | -52 | +232 | -59 | +313 | 1737 | -981 .. +501 |
| nyam | LONG | X3 | +70 | +14 | +234 | -194 | +359 | 1406 | -579 .. +742 |
| nyam | SHORT | X1 | -108 | -143 | -449 | -206 | -320 | 1315 | -720 .. +635 |
| nyam | SHORT | X2 | -350 | -385 | -745 | -193 | -618 | 1796 | -1260 .. +574 |
| nyam | SHORT | X3 | -188 | -249 | -576 | -79 | -745 | 1399 | -882 .. +608 |
| nypm | LONG | X1 | -321 | -385 | -615 | -214 | +23 | 1217 | -969 .. +272 |
| nypm | LONG | X2 | -697 | -602 | -769 | -350 | +212 | 1643 | -1346 .. -102 |
| nypm | LONG | X3 | -395 | -390 | -234 | -308 | +181 | 1469 | -1169 .. +197 |
| nypm | SHORT | X1 | +53 | +94 | +267 | -10 | -255 | 1218 | -614 .. +668 |
| nypm | SHORT | X2 | +154 | +87 | +125 | -101 | -399 | 1767 | -681 .. +857 |
| nypm | SHORT | X3 | +180 | +148 | -16 | +68 | -410 | 1457 | -500 .. +871 |

Exit shapes: X1 60/60 T60 min; X2 stop 60 / target 120 / T120 min; X3 live 60/60 flat 16:55. Fixed-clock C15 / C60 and the half-hour profile: /mnt/l2/l2vast/ds3_base4/dism_bench.csv, dism_bench_profile.csv.


## 2. Live groups: real replica vs matched drift (P1c = same side, entry delayed 5..120 min; P1x = look-ahead control, entry anywhere in the session)
| cell | L6M real / drift_c / drift_x | HOLD real / drift_c / drift_x | PRE real / drift_c | X' real / drift_c | P1c p (L6M / HOLD) | P2 side p | P3 day p | family max-T (L6M / HOLD) | label |
|--|--|--|--|--|--|--|--|--|--|
| LIVE KB|asia | +1402 / +262 / +3083 | +1217 / +500 / +2618 | +871 / +762 | -848 / -242 | 0.12 / 0.13 | 0.11 / 0.06 | 0.04 / 0.04 | 0.99 / 0.98 | DRIFT ONLY / inside the placebo band |
| LIVE KB|london | -368 / -1125 / +1406 | -156 / -454 / +1753 | +33 / -111 | -175 / -37 | 0.20 / 0.31 | 0.41 / 0.32 | 0.58 / 0.46 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE KB|nyam | -1915 / -550 / +1203 | -2010 / -273 / +1689 | +914 / +333 | +277 / -290 | 0.97 / 1.00 | 0.93 / 0.99 | 0.99 / 1.00 | 1.00 / 1.00 | NEGATIVE EXCESS (below the causal drift) |
| LIVE KB|nypm | +122 / +89 / +2200 | -441 / +383 / +1955 | +119 / -299 | -204 / -294 | 0.48 / 0.94 | 0.28 / 0.54 | 0.42 / 0.70 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PE|asia | +9003 / +5374 / +15391 | +5736 / +3894 / +13641 | +2802 / +770 | -1337 / -362 | 0.17 / 0.23 | 0.02 / 0.03 | 0.02 / 0.01 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PE|london | +4375 / -1309 / +10918 | +2798 / +164 / +10602 | -1949 / -1434 | +334 / +663 | 0.02 / 0.07 | 0.09 / 0.09 | 0.06 / 0.08 | 0.49 / 0.92 | DRIFT ONLY / inside the placebo band |
| LIVE PE|nyam | -5438 / -239 / +9145 | -5265 / -1570 / +9521 | +3459 / +1542 | +2602 / +46 | 0.93 / 0.96 | 0.68 / 0.80 | 0.89 / 0.95 | 1.00 / 1.00 | NEGATIVE EXCESS (below the causal drift) |
| LIVE SM|asia | +1627 / -1477 / +1914 | +773 / -824 / +1791 | +1175 / +690 | +1226 / +1318 | 0.02 / 0.03 | 0.07 / 0.17 | 0.12 / 0.11 | 0.14 / 0.48 | DRIFT ONLY / inside the placebo band |
| LIVE SM|london | -140 / -716 / +2579 | -146 / -835 / +2342 | +630 / +339 | +67 / -214 | 0.30 / 0.16 | 0.38 / 0.43 | 0.41 / 0.38 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE HM|asia | +2007 / +1841 / +7609 | +4259 / +1950 / +6560 | +865 / +479 | -550 / -831 | 0.45 / 0.02 | 0.10 / 0.01 | 0.08 / 0.01 | 1.00 / 0.35 | DRIFT ONLY / inside the placebo band |
| LIVE HM|nyam | -235 / -302 / +1346 | +305 / -179 / +1592 | +485 / +64 | -260 / -112 | 0.48 / 0.11 | 0.52 / 0.13 | 0.43 / 0.12 | 1.00 / 0.94 | DRIFT ONLY / inside the placebo band |
| LIVE MV|london | -362 / -405 / +3543 | +62 / +121 / +3514 | -145 / -325 | +25 / +393 | 0.49 / 0.61 | 0.38 / 0.26 | 0.57 / 0.34 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE MV|nyam | -168 / -360 / +1610 | +19 / -174 / +1945 | +917 / +211 | -546 / -7 | 0.41 / 0.31 | 0.32 / 0.20 | 0.45 / 0.28 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PB|asia | +12 / +532 / +5992 | +213 / +359 / +5044 | +988 / +579 | +227 / +318 | 0.81 / 0.66 | 0.38 / 0.27 | 0.29 / 0.14 | 1.00 / 1.00 | NEGATIVE EXCESS (below the causal drift) |
| LIVE KB|pooled | -759 / -1323 / +7891 | -1391 / +156 / +8015 | +1937 / +685 | -951 / -863 | 0.36 / 0.93 | 0.28 / 0.36 | 0.51 / 0.66 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PE|pooled | +7941 / +3826 / +35454 | +3269 / +2487 / +33764 | +4313 / +878 | +1599 / +347 | 0.18 / 0.40 | 0.06 / 0.04 | 0.05 / 0.08 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE SM|pooled | +1487 / -2193 / +4492 | +627 / -1659 / +4132 | +1805 / +1029 | +1293 / +1104 | 0.01 / 0.01 | 0.10 / 0.26 | 0.09 / 0.13 | 0.36 / 0.42 | DRIFT ONLY / inside the placebo band |
| LIVE HM|pooled | +1772 / +1538 / +8954 | +4563 / +1770 / +8152 | +1350 / +543 | -809 / -943 | 0.45 / 0.01 | 0.09 / 0.01 | 0.11 / 0.01 | 1.00 / 0.15 | DRIFT ONLY / inside the placebo band |
| LIVE MV|pooled | -530 / -765 / +5153 | +81 / -53 / +5460 | +772 / -115 | -521 / +385 | 0.43 / 0.38 | 0.36 / 0.11 | 0.50 / 0.26 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PB|pooled | +12 / +532 / +5992 | +213 / +359 / +5044 | +988 / +579 | +227 / +318 | 0.81 / 0.66 | 0.38 / 0.27 | 0.29 / 0.14 | 1.00 / 1.00 | NEGATIVE EXCESS (below the causal drift) |


## 3. Candidates re-expressed as EXCESS over the matched drift
| book | trades | L1M | L3M | L6M | HOLD | MID | PRE | X' | drift_c L6M / HOLD | excess L6M / HOLD | P1c p (L6M / HOLD) | P2 p | P3 p | family max-T (L6M / HOLD) | BH q (L6M / HOLD) | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| SHADOW NYAM ONRTH (1 lot) | 543 | +169 | +24 | +485 | +794 | +1958 | -25 | +35 | -174 / -287 | +660 / +1081 | 0.03 / 0.01 | 0.08 / 0.01 | 0.03 / 0.01 | 0.31 / 0.01 | 0.11 / 0.05 | DRIFT ONLY / inside the placebo band |
| SHADOW NYAM VWAPF (1 lot) | 3273 | -117 | +427 | +663 | +1247 | +3855 | -202 | +43 | -219 / -272 | +882 / +1519 | 0.08 / 0.01 | 0.08 / 0.01 | 0.09 / 0.01 | 0.93 / 0.08 | 0.21 / 0.05 | DRIFT ONLY / inside the placebo band |
| SHADOW NYAM ORBF (1 lot) | 914 | +1101 | +769 | +1052 | +745 | +790 | -811 | -406 | -150 / -292 | +1201 / +1037 | 0.01 / 0.01 | 0.01 / 0.01 | 0.02 / 0.01 | 0.08 / 0.02 | 0.06 / 0.05 | EXCESS SURVIVES (nothing is a PASS) |
| SHADOW FADE VB2NYPM_T1 (1 lot) | 523 | +212 | +128 | +384 | +238 | +17 | +38 | +20 | -72 / -104 | +456 / +342 | 0.01 / 0.01 | 0.01 / 0.03 | 0.01 / 0.01 | 0.05 / 0.03 | 0.06 / 0.05 | EXCESS SURVIVES (nothing is a PASS) |
| SHADOW FADE PDASIA_T2 (1 lot) | 317 | +695 | +604 | +234 | +299 | +576 | +0 | -16 | +20 / +12 | +214 / +287 | 0.09 / 0.01 | 0.05 / 0.02 | 0.03 / 0.01 | 0.99 / 0.16 | 0.22 / 0.05 | DRIFT ONLY / inside the placebo band |
| SHADOW FADE VB2NYAM_T3 (1 lot) | 893 | +10 | +631 | +402 | +356 | -20 | +15 | -107 | -59 / -109 | +461 / +466 | 0.07 / 0.04 | 0.12 / 0.04 | 0.03 / 0.02 | 0.95 / 0.63 | 0.21 / 0.13 | DRIFT ONLY / inside the placebo band |
| SHADOW FADE OR15NYAM_T2 (1 lot) | 935 | +900 | +2439 | +2663 | +738 | -1592 | +6 | -196 | +766 / +787 | +1897 / -49 | 0.01 / 0.56 | 0.01 / 0.17 | 0.01 / 0.03 | 0.02 / 1.00 | 0.06 / 0.71 | DRIFT ONLY / inside the placebo band |
| DIS-C Sunday 18:30 with-trend (re-derived, 1 lot) | 185 | +584 | +272 | +509 | +320 | +623 | +118 | -13 | +150 / +103 | +358 / +217 | 0.03 / 0.06 | 0.03 / 0.17 | 0.01 / 0.04 | 0.67 / 0.86 | 0.11 / 0.17 | DRIFT ONLY / inside the placebo band |
| DIS-B P_REL_cont all sides (re-derived, 1 lot) | 227 | +155 | -3 | -54 | +3 | -1 | +20 | -31 | -50 / -87 | -4 / +90 | 0.50 / 0.15 | 0.60 / 0.38 | 0.57 / 0.35 | 1.00 / 1.00 | 0.59 / 0.30 | DRIFT ONLY / inside the placebo band |
| DIS-B P_REL_cont shorts only (re-derived, 1 lot) | 108 | -9 | -50 | -47 | -12 | -34 | +81 | -17 | +33 / -14 | -80 / +2 | 0.79 / 0.48 | 0.61 / 0.48 | 0.90 / 0.63 | 1.00 / 1.00 | 0.86 / 0.62 | DRIFT ONLY / inside the placebo band |
| DIS-I ROLL_WEEK|nyam|FADE|SH2 ($1200 risk) | 56 | +0 | +45 | +19 | +147 | +493 | -116 | +155 | +55 / +106 | -36 / +41 | 0.59 / 0.33 | 0.40 / 0.24 | 0.32 / 0.05 | 1.00 / 1.00 | 0.68 / 0.51 | DRIFT ONLY / inside the placebo band |
| DIS-I ME3|asia|CONT|SH2 ($1200 risk) | 81 | +364 | +453 | +310 | +284 | +161 | +7 | -76 | +58 / +187 | +253 / +97 | 0.07 / 0.23 | 0.01 / 0.01 | 0.01 / 0.02 | 0.82 / 1.00 | 0.21 / 0.40 | DRIFT ONLY / inside the placebo band |
| DIS-I MS3|asia|CONT|SH1 ($1200 risk) | 86 | +997 | +493 | +226 | +216 | +47 | +60 | +19 | +84 / +201 | +142 / +15 | 0.08 / 0.46 | 0.01 / 0.14 | 0.19 / 0.16 | 0.94 / 1.00 | 0.21 / 0.61 | DRIFT ONLY / inside the placebo band |
| DIS-I TOM|asia|CONT|SH1 ($1200 risk) | 113 | +1244 | +501 | +312 | +333 | -55 | +110 | -37 | +59 / +301 | +253 / +33 | 0.01 / 0.39 | 0.01 / 0.03 | 0.15 / 0.07 | 0.56 / 1.00 | 0.06 / 0.55 | DRIFT ONLY / inside the placebo band |
| DIS-I NFP|nypm|DRIFT_S|SH1 ($1200 risk) | 40 | +125 | +52 | +267 | +193 | +33 | +26 | -78 | +97 / +63 | +170 / +129 | 0.01 / 0.01 | 0.06 / 0.04 | 0.23 / 0.17 | 0.02 / 0.16 | 0.06 / 0.05 | DRIFT ONLY / inside the placebo band |
| DIS-I RETAIL|nypm|DRIFT_S|SH2 ($1200 risk) | 43 | -247 | +87 | +184 | +194 | +289 | +44 | +179 | -41 / +1 | +224 / +193 | 0.03 / 0.03 | 0.10 / 0.04 | 0.04 / 0.03 | 0.41 / 0.20 | 0.11 / 0.11 | DRIFT ONLY / inside the placebo band |
| Q11 TD1_20 WITH PB_asia LONG SH1 (live lots) | 2193 | +293 | +321 | +366 | +290 | +502 | +109 | -15 | +155 / +154 | +212 / +136 | 0.12 / 0.11 | 0.13 / 0.03 | 0.13 / 0.07 | 0.99 / 0.95 | 0.26 / 0.25 | DRIFT ONLY / inside the placebo band |
| Q11 TD3_50 COUNTER PE_nyam ALL SH1 (live lots) | 1189 | +4446 | +8391 | +4368 | +4253 | -1200 | +2057 | +2876 | +2282 / +1009 | +2085 / +3244 | 0.20 / 0.06 | 0.22 / 0.11 | 0.07 / 0.04 | 1.00 / 0.79 | 0.35 / 0.17 | DRIFT ONLY / inside the placebo band |
| Q11 TD3_20 COUNTER PE_asia SHORT SH2 (live lots) | 604 | +950 | +1455 | +3488 | +2536 | -658 | +2 | -547 | +2677 / +2793 | +811 / -257 | 0.36 / 0.60 | 0.10 / 0.10 | 0.06 / 0.04 | 1.00 / 1.00 | 0.56 / 0.73 | DRIFT ONLY / inside the placebo band |


## 4. Replica stack with the drift hedged out (carrying weeks dropped for maxDD)
| window | engine core mean | replica mean | causal drift mean | hedged mean | replica maxDD | hedged maxDD | look-ahead drift mean (P1x) |
|--|--|--|--|--|--|--|--|
| L1M | +5305 | -20211 | +25533 | -45744 | +136044 | +228719 | +64812 |
| L2M | +13860 | +13415 | +18008 | -4593 | +136044 | +174738 | +72358 |
| L3M | +7746 | -320 | +9030 | -9351 | +136044 | +174738 | +65760 |
| L6M | +26999 | +9923 | +1616 | +8308 | +136044 | +174738 | +67936 |
| HOLD | +22589 | +7363 | +3062 | +4302 | +237460 | +210861 | +64566 |
| MID | +16851 | -4433 | -2342 | -2091 | +198904 | +196519 | +54304 |
| PRE | +13202 | +11164 | +3599 | +7565 | +190841 | +106930 | +38822 |
| X' | +3293 | +838 | +349 | +489 | +132199 | +91036 | +17386 |

Genuine PA9 maxDD cut of the hedged vs the replica stack (+ = hedging reduces the drawdown): L6M -53.4%, HOLD +10.1%, MID +5.2%, PRE +33.5%, X' +25.3%; daily correlation replica vs engine core 0.76; replica total / engine core total 0.63.



# DIS-I (BASE-4): FLOW-CALENDAR books on NQ, as entry books AND as size overlays on the live Q1-A ts2 stack

Shadow only, no PASS claims. Prereg l2vast/ds3/prereg/DISI_prereg.md sha256 be78eb84cf8ee640f09b3c347837597a0e69ce7bd361ee832fc9adefbf8b357b (DECISIONS.md, before any statistic); ledger program DIS_I; rows FADE_ROWS_DISI.md; n_tested DISI = 1,038 (800 entry books + 238 overlay cells). Harness FadeHarness, gate_v3 carry weeks, Q1-A ts2 base, live fill model, equal-$-risk entries ($1,200). Code l2vast/ds3/code/disi/ (disi_cal, disi_books, disi_run_entry, disi_run_overlay, disi_placebo_entry, disi_placebo_overlay, disi_family_entry, disi_family_overlay, disi_report); bulk /mnt/l2/l2vast/ds3_base4/disi_*.


## INTERIM 1 (2026-11-04 19:58 UTC) - everything scored; entry family test HOLD_calmar done, L6M_mean family and the one overlay placebo run still going

**dead_lookup first:** entry books on calendar flags: 0 rows in DEAD_CELLS (hits per flag are stack overlays EINT2, no-trade minute windows NTE1 / NTE1C, or other-instrument programs); 12 overlay cells (scope ALL, HALF) are EINT2 rows on STACK6 and were NOT re-scored (cited in the prereg: monthend, monthend3, monthstart, opexday, opexweek, quadday, hol before / after, early close, CPI, NFP, FOMC). The DISCOVER_EVENT_STUDY census (no books) is cited, not repeated.

**Flagged days per window** (trading days; prereg sec. 2 table): e.g. NFP 40 days (L1M 1, L3M 3, L6M 6, HOLD 11, MID 2, PRE 17, X' 9), CPI 42 (1/3/6/11/3/17/10), FOMC 29 (1/2/4/8/2/11/7), OPEX_M 29, TRIPLE_W 14 (L6M 2), REBAL 14 (L6M 2), ME1 43 (L6M 6), ME3 129 (L6M 18), TOM 172 (L6M 24), OPEX_WEEK 214 (L6M 30), ROLL_WEEK 70 (L6M 10), PRE_HOL 36 (L6M 4), RUSSELL 4 (excluded). A single-day flag has 2-6 flagged days in L6M: an entry book earns one trade per flagged day and session, so the MDE of a window mean is large (median over the 512 scored books: MDE_L6M $409/wk vs median |mean_L6M| $109/wk; MDE_HOLD $317 vs |mean| $83) and a window mean inside the MDE is not evidence.

### A. Entry books (800 built: 512 scored with >= 30 trades, 288 thin)

Gate counts on 512 scored books: STRICT 12 (2.3%), TOLERANT 59 (11.5%), NOW_ONLY 174, gate_v2a 0; all eight windows positive 5; L6M, HOLD, PRE and X' all positive 26. Books whose L6M AND HOLD means both exceed their own MDE: 0 of 512.

Weekly $ (mean over scored books) by kind: CONT L6M +17 / HOLD +22 / PRE -8 / X' -49 (n 104); DRIFT_L L6M -17 / HOLD +5 / PRE -50 / X' -29 (n 152); DRIFT_S L6M +26 / HOLD -4 / PRE +2 / X' -93 (n 152); FADE L6M -18 / HOLD -23 / PRE -54 / X' -28 (n 104). By session: asia -37 / -10 / -10 / -27; london +37 / +16 / -77 / -91; nyam -1 / +9 / -8 / -44; nypm +2 / -19 / -7 / -39. Every book-mean average is negative or inside a few dollars in PRE and X' (2023-25): no kind or session pays across regimes.

Placebos for the 59 TOLERANT survivors (P1 shifted calendar +-1..5 trading days, P2 random days with the same count per quarter x100, P3 random side x100; statistic HOLD Calmar): 5 of 59 pass all three (P1 p <= 0.10 means the real book beats all ten shifts; P2 and P3 p <= 0.10): NFP|nypm|DRIFT_S|SH1, RETAIL|nypm|DRIFT_S|SH2, ME3|asia|CONT|SH2, MS3|asia|CONT|SH1, TOM|asia|CONT|SH1.

Family max-statistic (HOLD_calmar, 512 books, 100 worlds per kind; the harness p_maxT of a book is the larger of its two kinds): best book ROLL_WEEK|nyam|FADE|SH2 (stat 2.292); family p of the real maximum: side-null 0.188, days-null 0.020; books with p_maxT <= 0.10: 0; BH q <= 0.10: 0 (smallest q 1.00). Raw per-book p <= 0.05: 29 under the side null (null expectation 26), 42 under the days null, 20 under both. The side null (random side at the real times) is rejected at about the null rate; the days null (each entry moved to a random day of the same weekday) is rejected more often, which says calendar days differ from random days of the same weekday in HOLD Calmar, not that the direction or timing of the entries is right; no book clears the family max-T.

Top 12 scored books by the mean of the five window means (L6M, HOLD, MID, PRE, X'), NOT family-adjusted (full list FADE_ROWS_DISI.md / disi_entry.csv):

| book | trades (L6M) | L6M | HOLD | MID | PRE | X' | TOLERANT | P1 / P2 / P3 (HOLD Calmar) | family p_maxT | label |
|--|--|--|--|--|--|--|--|--|--|--|
| AUCT_LONG|london|DRIFT_S|SH1 | 114 (16) | +1252 | +785 | +363 | -88 | -56 | no | not run (not TOLERANT) | 1.00 | REGIME? (L6M only) |
| ME3|nypm|CONT|SH1 | 88 (10) | +219 | +399 | +1276 | -195 | +150 | no | not run (not TOLERANT) | 0.97 | DEAD / no |
| OPEX_WEEK|london|FADE|SH1 | 153 (25) | +221 | +254 | +892 | +128 | +180 | yes | 0.18 / 0.07 / 0.10 | 1.00 | TOLERANT only, placebos fail |
| TOM|nyam|DRIFT_L|SH1 | 172 (24) | +139 | +514 | +1243 | +136 | -477 | no | not run (not TOLERANT) | 1.00 | DEAD / no |
| AUCT_LONG|nyam|DRIFT_S|SH1 | 114 (16) | +97 | +236 | +924 | +112 | +30 | no | not run (not TOLERANT) | 1.00 | DEAD / no |
| AUCT_LONG|london|FADE|SH1 | 81 (7) | +73 | +304 | +734 | +45 | +172 | yes | 0.09 / 0.01 / 0.20 | 1.00 | TOLERANT only, placebos fail |
| MS3|nyam|DRIFT_L|SH1 | 129 (18) | +126 | +489 | +1152 | +10 | -449 | no | not run (not TOLERANT) | 1.00 | DEAD / no |
| PRE_HOL|nyam|FADE|SH1 | 32 (4) | -10 | +99 | +774 | -91 | +516 | no | not run (not TOLERANT) | 1.00 | DEAD / no |
| MS1|london|DRIFT_S|SH1 | 43 (6) | +1227 | +491 | -209 | -103 | -182 | no | not run (not TOLERANT) | 1.00 | REGIME? (L6M only) |
| TOM|nyam|DRIFT_L|SH2 | 172 (24) | +114 | +447 | +1177 | -249 | -294 | no | not run (not TOLERANT) | 1.00 | REGIME? (L6M only) |
| NFP|london|CONT|SH1 | 31 (5) | +338 | +351 | +867 | -171 | -198 | no | not run (not TOLERANT) | 1.00 | REGIME? (L6M only) |
| OPEX_WEEK|london|FADE|SH2 | 153 (25) | +347 | +269 | +564 | +37 | -59 | yes | 0.27 / 0.14 / 0.04 | 1.00 | TOLERANT only, placebos fail |

Stack marginal of the best books (Q1-A ts2, 1x, carrying weeks dropped): HOLD Calmar change between -0.009 and +0.017, L6M between -0.016 and +0.042 over the 59 TOLERANT books - the books are small ($1,200 risk, 1-2 trades a flagged day) and move the stack by hundredths.

### B. Size overlays on the live Q1-A ts2 stack (238 scored cells; 12 EINT2 cells cited)

Overlay = m = Q1A x 0.5 (HALF) or x 0.25 (QUARTER) on the signals of flagged days in the scope (all / asia / london / nyam / nypm), live lots (never below 1 lot). Bands (maxDD cut %, PA9): L6M 18.8, PRE 7.8, X' 14.5. Cells with PA9 L6M above the band: 1; with L6M and PRE above their bands (pass2): 0; with L6M and (PRE or X') above (pass2_either): 1; with no-harm and mean inside the MDE (elig): 236. Carry-dropped (corrected weeks) L6M cut > 0.5 pt AND PRE > 0.5 pt: 24 cells, but their L6M cut is the same single flagged day in many cells (e.g. 33.25 in ME1 and TOM ALL QUARTER) - a ONE-DAY effect.
Best by PA9 L6M: OV|MS3|asia|QUARTER: PA9 L6M +20.0 / HOLD +5.9 / MID +0.0 / PRE +2.2 / X' +16.2, carry-dropped L6M -0.0 / PRE +2.2 / X' +0.3, mean change L6M -2.98 k$/wk (MDE 5.97), PRE -0.22 (MDE 1.43), mean lots 2.21 vs Q1-A 2.31: the L6M cut vanishes when the carrying week is dropped (ONE-WEEK).
Linearised family test (session-by-day P&L cube, 200 worlds of random day sets per quarter, statistic = mean carry-dropped maxDD cut in L6M, HOLD and PRE): real maximum 0.178 (OV|ME3|ALL|QUARTER), family p 0.40; BH q min 0.59; engine-vs-linear check over the 238 cells: Pearson 0.82, Spearman 0.45.

### Plain sentence
No calendar flag, as an entry book or as a size overlay, separates from chance once the family of 1,038 cells is accounted for: the best entry books have 4-30 trades in L6M and window means inside their MDE (see the count above), the family max-T p of the best book is 0.19, and the overlays that cut drawdown in L6M do so on one flagged day. Labels: ADDITION / LEAD none; WEAK = 5 entry books (placebos pass, family fails); the rest DEAD / THIN. Open items: L6M_mean family run, the overlay placebo on the one band-passing cell, ledger rows (DIS_I).


(DIS-I section RE-APPENDED 2026-11-04T22:19Z from the interim text /tmp/disi_interim.txt; rows in FADE_ROWS_DISI.md; ledger DIS_I 1,050 rows.)

RE-APPENDED ZL-1 22:26Z (DIS-U interim 1 was lost from this file in the overwrite; text copied from the 22:17Z snapshot)

- S4a DIS-B table: autopilot/DIS_B_TABLE.md (pointer only; append-only line)

- S4a DIS-B2 table: autopilot/DIS_B2_TABLE.md (pointer only; append-only line)

## DIS-AO (Z1, 2026-11-04 22:40Z): CROSS-INSTRUMENT REPLICATION of the NQ fade survivors on ES, RTY, YM - interim 1 (research only, no PASS, nothing live; re-appended 23:05Z after a stale-copy overwrite)
Scope DISAO_scope.md sha256 8a187d121ea55e04f1f2134e185326c6992968b9a3a9bfa2c36f9dee34e62051 (logged in DECISIONS.md before any number); ledger DIS_AO (24 cells); n_tested FADE_DISAO 400; code l2vast/ds3/code/disao/; tables l2vast/ds3/out/disao/disao_cells.csv, disao_boot.csv, disao_warm.csv.
**Plain sentence:** once scaled by each index ATR, the NY-AM fade excess over a random-minute trade is NOT NQ-only in 2026: ES shows the same sign and a significant per-cell excess for VWAPF and the bundle in HOLD and 2026 (not in L6M), YM is weaker, RTY shows nothing or the opposite; NQ-minus-ES is not distinguishable from zero (paired bootstrap), NQ is larger than RTY and YM; before 2023 there is no excess on any instrument; no family-level evidence (L6M family min p 0.76). No PASS.
**Method / departures:** Z2 xi_gen generators for ONRTH, VWAPF, ORBF, VB2 NYPM T1; N_REL_rev per DIS-B (09:31 entry); bracket 60 f; one numba 1-min simulator for all four (next-bar open + max(0.8f,1 tick) slip, stop first, stop slip max(2.45f,2 ticks), target needs 1-tick trade-through, per-trade time stop, 16:55 ET flat, one position per line, fee 4.84). Cross-check ES ONRTH equal-risk L6M 14.8 / HOLD 78.9 vs FADE_XI 9.9 / 72.9. New-cap windows but bars end 2026-10-16 (RTY 10-23): L6M 25 wk, HOLD 50. Statistic = equal-risk $/wk at $2,400 stop risk. ORBF W1 window 09:30-12:00 as scope. Bundle = sum of components. Family max-T over 24 combos with independent draws. 200 W1 and W3 worlds, warm-up sensitivity 100 W1.
**Equal-risk excess over W1 drift, $/wk (p) HOLD / 2026 / pre-2023:**
| line | NQ | ES | RTY | YM |
|--|--|--|--|--|
| ONRTH | +1463 (p 0.00) / +1174 (p 0.00) / +50 (p 0.29) | +363 (p 0.19) / +786 (p 0.06) / -10 (p 0.58) | -112 (p 0.58) / +60 (p 0.44) / +10 (p 0.51) | +496 (p 0.19) / +623 (p 0.15) / -83 (p 0.80) |
| VWAPF | +2735 (p 0.02) / +3298 (p 0.00) / -32 (p 0.64) | +2103 (p 0.03) / +2863 (p 0.00) / +20 (p 0.48) | +674 (p 0.28) / +660 (p 0.31) / -456 (p 0.86) | +18 (p 0.49) / +11 (p 0.50) / +65 (p 0.35) |
| ORBF | +873 (p 0.15) / +665 (p 0.24) / -164 (p 0.86) | +23 (p 0.51) / -148 (p 0.61) / +131 (p 0.21) | -652 (p 0.81) / -665 (p 0.80) / -494 (p 0.95) | +331 (p 0.30) / +950 (p 0.13) / +64 (p 0.35) |
| VB2 | +440 (p 0.11) / +301 (p 0.20) / -20 (p 0.53) | +77 (p 0.43) / +477 (p 0.15) / -38 (p 0.58) | -77 (p 0.58) / -39 (p 0.54) / +191 (p 0.13) | +238 (p 0.23) / +16 (p 0.48) / -312 (p 0.98) |
| N_REL_rev | +1042 (p 0.03) / +1052 (p 0.04) / -41 (p 0.58) | +436 (p 0.17) / +467 (p 0.16) / +215 (p 0.08) | -261 (p 0.69) / -121 (p 0.59) / -298 (p 0.90) | +342 (p 0.24) / +681 (p 0.14) / -172 (p 0.87) |
| BUNDLE | +5071 (p 0.00) / +5136 (p 0.00) / -146 (p 0.70) | +2489 (p 0.04) / +3501 (p 0.01) / +141 (p 0.29) | -90 (p 0.50) / +55 (p 0.46) / -939 (p 0.95) | +845 (p 0.28) / +1584 (p 0.18) / +46 (p 0.42) |

| line | inst | L6M exc (p) | HOLD exc (p) | family p L6M / HOLD | real pts/trade NQ-eq L6M / HOLD | W3 L6M / HOLD (p) | label |
|--|--|--|--|--|--|--|--|
| ONRTH | NQ | +953 (0.09) | +1463 (0.00) | 0.91 / 0.11 | +7.1 / +10.5 | +955 (0.11) / +1411 (0.01) | PER-CELL ONLY | W3 fails |
| ONRTH | ES | +234 (0.37) | +363 (0.19) | 1.00 / 1.00 | +0.6 / +1.2 | +330 (0.32) / +422 (0.21) | DRIFT-EXPLAINED | W3 fails |
| ONRTH | RTY | -296 (0.64) | -112 (0.58) | 1.00 / 1.00 | -6.1 / -3.7 | -281 (0.62) / -63 (0.58) | NEGATIVE | W3 fails |
| ONRTH | YM | +1174 (0.08) | +496 (0.19) | 0.89 / 1.00 | +8.3 / +1.8 | +1098 (0.12) / +432 (0.21) | DRIFT-EXPLAINED | W3 fails |
| VWAPF | NQ | +1393 (0.23) | +2735 (0.02) | 1.00 / 0.43 | +0.1 / +3.8 | +1079 (0.31) / +2374 (0.03) | DRIFT-EXPLAINED | W3 fails |
| VWAPF | ES | +61 (0.49) | +2103 (0.03) | 1.00 / 0.53 | -4.9 / +1.0 | -109 (0.52) / +1944 (0.04) | DRIFT-EXPLAINED | W3 fails |
| VWAPF | RTY | -220 (0.56) | +674 (0.28) | 1.00 / 1.00 | -4.5 / -2.0 | -498 (0.64) / +369 (0.38) | DRIFT-EXPLAINED | W3 fails |
| VWAPF | YM | -333 (0.55) | +18 (0.49) | 1.00 / 1.00 | -4.0 / -2.9 | -380 (0.60) / -86 (0.51) | DRIFT-EXPLAINED | W3 fails |
| ORBF | NQ | +687 (0.27) | +873 (0.15) | 1.00 / 0.97 | +0.8 / +2.0 | +548 (0.33) / +811 (0.17) | DRIFT-EXPLAINED | W3 fails |
| ORBF | ES | -373 (0.65) | +23 (0.51) | 1.00 / 1.00 | -5.1 / -3.0 | -296 (0.61) / +60 (0.50) | DRIFT-EXPLAINED | W3 fails |
| ORBF | RTY | -1320 (0.91) | -652 (0.81) | 1.00 / 1.00 | -9.2 / -5.7 | -1164 (0.89) / -585 (0.79) | NEGATIVE | W3 fails |
| ORBF | YM | +1050 (0.17) | +331 (0.30) | 1.00 / 1.00 | +3.5 / -0.7 | +1137 (0.18) / +353 (0.36) | DRIFT-EXPLAINED | W3 fails |
| VB2 | NQ | +287 (0.27) | +440 (0.11) | 1.00 / 0.96 | +3.2 / +2.6 | +278 (0.33) / +450 (0.15) | DRIFT-EXPLAINED | W3 fails |
| VB2 | ES | +407 (0.24) | +77 (0.43) | 1.00 / 1.00 | -2.0 / -2.2 | +444 (0.24) / +143 (0.41) | DRIFT-EXPLAINED | W3 fails |
| VB2 | RTY | +70 (0.46) | -77 (0.58) | 1.00 / 1.00 | -4.1 / -5.1 | +40 (0.48) / -84 (0.56) | DRIFT-EXPLAINED | W3 fails |
| VB2 | YM | -349 (0.73) | +238 (0.23) | 1.00 / 1.00 | -2.5 / -0.8 | -394 (0.73) / +241 (0.29) | DRIFT-EXPLAINED | W3 fails |
| N_REL_rev | NQ | +1525 (0.01) | +1042 (0.03) | 0.81 / 0.80 | +19.6 / +12.8 | +983 (0.08) / +663 (0.09) | PER-CELL ONLY | W3 PASS |
| N_REL_rev | ES | +1106 (0.04) | +436 (0.17) | 0.76 / 0.98 | +11.8 / +2.3 | +1018 (0.07) / +782 (0.05) | DRIFT-EXPLAINED | W3 PASS |
| N_REL_rev | RTY | -524 (0.78) | -261 (0.69) | 1.00 / 1.00 | -5.1 / -3.1 | -340 (0.77) / +255 (0.23) | NEGATIVE | W3 fails |
| N_REL_rev | YM | +1043 (0.12) | +342 (0.24) | 0.85 / 1.00 | +11.1 / +2.7 | +975 (0.07) / +386 (0.22) | DRIFT-EXPLAINED | W3 fails |
| BUNDLE | NQ | +3034 (0.08) | +5071 (0.00) | 0.91 / 0.02 | +1.3 / +4.4 | +2582 (0.12) / +4596 (0.00) | PER-CELL ONLY | W3 fails |
| BUNDLE | ES | -77 (0.53) | +2489 (0.04) | 1.00 / 0.62 | -4.1 / -0.1 | -75 (0.52) / +2427 (0.06) | DRIFT-EXPLAINED | W3 fails |
| BUNDLE | RTY | -1836 (0.84) | -90 (0.50) | 1.00 / 1.00 | -6.2 / -3.3 | -1944 (0.86) / -279 (0.52) | NEGATIVE | W3 fails |
| BUNDLE | YM | +1891 (0.18) | +845 (0.28) | 1.00 / 1.00 | -0.0 / -1.5 | +1855 (0.20) / +699 (0.30) | DRIFT-EXPLAINED | W3 fails |

**NQ minus instrument, paired day bootstrap, daily excess in NQ-eq points (mean diff [95%]; * = excludes 0):**
| line | vs | L6M | HOLD | 2026 | pre-2023 |
|--|--|--|--|--|--|
| ONRTH | ES | +3.7 [-7.3, +14.4] | +5.5 [-1.8, +13.1] | +2.0 [-6.2, +10.5] | +0.3 [-0.9, +1.4] |
| ONRTH | RTY | +5.2 [-5.9, +16.7] | +7.3 [-0.7, +15.5] | +4.9 [-3.7, +13.6] | +0.4 [-2.2, +2.9] |
| ONRTH | YM | -1.1 [-12.2, +10.5] | +4.9 [-3.8, +13.4] | +2.8 [-6.2, +11.3] | +0.7 [-0.8, +2.2] |
| VWAPF | ES | +7.0 [-13.3, +26.3] | +3.3 [-9.1, +16.0] | +2.4 [-11.4, +15.8] | -0.2 [-2.1, +1.6] |
| VWAPF | RTY | +7.6 [-11.6, +26.3] | +10.2 [-3.1, +24.1] | +13.1 [-2.6, +28.0] | +2.1 [-1.9, +6.3] |
| VWAPF | YM | +9.3 [-13.3, +30.5] | +14.0 [-0.9, +29.5] | +17.1 [+1.4, +32.3]* | -0.4 [-2.8, +2.1] |
| ORBF | ES | +5.5 [-7.6, +18.6] | +4.3 [-4.0, +12.5] | +4.1 [-5.0, +13.2] | -1.5 [-3.1, +0.1] |
| ORBF | RTY | +10.7 [-3.1, +26.1] | +7.8 [-2.0, +17.3] | +6.9 [-3.8, +17.9] | +0.2 [-3.3, +3.8] |
| ORBF | YM | -1.9 [-16.3, +12.6] | +2.7 [-7.3, +12.6] | -1.5 [-12.5, +9.5] | -1.1 [-3.2, +0.8] |
| VB2 | ES | +1.8 [-3.6, +7.0] | +1.8 [-1.7, +5.5] | +0.2 [-3.4, +4.0] | +0.0 [-0.5, +0.6] |
| VB2 | RTY | +2.8 [-2.2, +8.1] | +3.2 [-0.3, +6.8] | +3.5 [-0.4, +7.4] | -0.0 [-1.0, +1.0] |
| VB2 | YM | +2.5 [-1.6, +7.0] | +1.3 [-1.4, +4.3] | +1.8 [-1.4, +5.1] | +0.5 [-0.1, +1.2] |
| N_REL_rev | ES | +3.2 [-4.1, +10.5] | +3.2 [-0.9, +7.4] | +3.5 [-1.2, +8.5] | -0.4 [-0.9, +0.1] |
| N_REL_rev | RTY | +7.5 [-1.1, +16.1] | +4.7 [-1.3, +11.0] | +4.3 [-2.4, +11.2] | +0.8 [-0.6, +2.1] |
| N_REL_rev | YM | +3.6 [-7.2, +15.1] | +3.6 [-3.3, +10.3] | +3.3 [-4.7, +11.6] | +0.1 [-0.6, +0.9] |
| BUNDLE | ES | +16.2 [-11.1, +43.7] | +13.2 [-4.3, +30.7] | +8.5 [-9.2, +26.6] | -1.4 [-4.3, +1.6] |
| BUNDLE | RTY | +23.5 [-2.8, +51.0] | +25.2 [+7.6, +44.8]* | +24.8 [+3.3, +45.9]* | +2.6 [-4.2, +9.1] |
| BUNDLE | YM | +6.2 [-25.9, +37.4] | +21.6 [+1.7, +42.1]* | +18.4 [-4.5, +40.6] | -0.8 [-4.7, +3.0] |

Reading: ES real P&L is negative in L6M (bundle -2,967 $/wk) and its HOLD excess comes from a very negative random-minute benchmark (~-2.9k $/wk): the fade loses less than random. MDE (2.12 sd) ~1,000-1,700 $/wk per line, 3,000-4,700 bundle. Answer: favours a market-wide 2026 effect strongest in NQ and ES, nil pre-2023; NQ not shown different from ES. Closed at this interim; no PASS, nothing live.
- Protocol disclosure (Z1, 2026-11-04): for DIS-AO the dead_lookup was run AFTER scoring (to be run BEFORE); it returned no DIS_AO cells, only FADE_XI ES ONRTH overlap used as cross-check; nothing changed.

## DIS-AX (BASE-4, 2026-11-04T22:41Z): TH-L2 CUT COST / LATENCY SENSITIVITY - full page autopilot/DS3_TH_COST.md; scope DISAX_scope.md sha256 371a8908c9f97489855ea85ac4752e8efee49c33624069d6def8e3d7b0b5b0e3; ledger DIS_AX; no PASS, nothing live
TH-L2 post-cap gain +18076/wk at the engine cut cost (0.80 pt), +12902 at +1 pt, +7761 at +2, +2498 at +3; zero at +3.5 pts (total about 4.3 pt/lot); 2023-26 gain +2029/wk, zero at +0.69 pts; latency 0-3 s changes it by +0.5k..+1.5k; slicing no change; PE carries it.


# DS3_DISCOVER2 - section S4b: DIS-AU irregular-session behaviour of the live books, interim 1 - 2026-11-04 22:41Z
Prereg autopilot/DIS_AU_PREREG.md (sha256 5261b7a0bed063480f27445e1e40b4ee5df357a8a44f9ef94f349808eb2e5f2a in DECISIONS.md, before any statistic); n_tested 49 (DISAU_NTESTED.md); code l2vast/ds3/code/disc/da_build.py, da_eval.py, da_fam.py; data /mnt/l2/l2vast/ds3_dr/. Reference: Q1-A ts2 rows (88,490 engine rows, 21,397 taken here as 20,997 with finite P&L over 927 label days 2023-04..2026-10). Measurement only, Shadow, no PASS claims.
Day classes found: NORMAL 891, EARLY 34 (13:00 closes: Memorial/Juneteenth/Jul 3-4/Labour/Thanksgiving Friday/Christmas Eve and the Monday holidays MLK/Presidents), DAY_AFTER 30, HOLIDAY_OPEN 4 (20230407, 20250109, 20260403, 20261019 - the last is not a CME holiday and looks like a data-gap day: check by the lead), plus 1,495 Sunday-18:00 session trades on 185 Sundays.
## Do the live rules misbehave?
- **Early closes:** the engine's flat deadline on EARLY days is 12:59 (13:14 on the 3 July / Thanksgiving-Friday / Christmas Eve 13:15-type days); none of the 299 early-day trades has a flat deadline after the day's last RTH bar (0 of 299). The 84 entries after the last RTH bar on those days are all Asia-session entries at 18:01-23:58 ET, i.e. after the Globex reopen, not entries into a closed market.
- **Maintenance halt:** the flat deadline on every normal-length day is 16:54 ET, before the 17:00 halt, so no trade is held through the halt by construction (0 CROSS_MAINT by deadline). The ENTRY_CLOSED flag finds 24 entries with no minute bar within +-60 s (not on a specific class; listed in da_trades.pkl). **Not measurable at this layer:** actual exit second and exit price per trade (the engine rows expose the flat deadline, not the realised exit), so stop slippage by class is not measured and no substitute was invented.
## Performance by class (mean net $/trade at Q1-A lots versus NORMAL, same book; day-block bootstrap)
| class | book | trades | days | mean $/trade | NORMAL $/trade | diff | MDE (2.8 SE) | block-boot p | BH q | label |
|---|---|---|---|---|---|---|---|---|---|---|
| EARLY | HM | 48 | 26 | +118 | +92 | +26 | 913 | 0.95 | 0.95 | inside MDE |
| EARLY | KB | 85 | 30 | +63 | +25 | +38 | 431 | 0.81 | 0.95 | inside MDE |
| EARLY | MV | 50 | 23 | -77 | +1 | -77 | 437 | 0.61 | 0.91 | inside MDE |
| EARLY | PB | 17 | - | thin | - | - | - | - | - | thin, not tested |
| EARLY | PE | 73 | 29 | +54 | +317 | -263 | 1650 | 0.64 | 0.91 | inside MDE |
| EARLY | SM | 26 | 22 | +362 | +204 | +159 | 1334 | 0.77 | 0.95 | inside MDE |
| EARLY | STACK | 299 | 33 | +95 | +107 | -13 | 705 | 0.90 | 0.95 | inside MDE |
| HOLIDAY_OPEN | HM | 6 | - | thin | - | - | - | - | - | thin, not tested |
| HOLIDAY_OPEN | KB | 15 | - | thin | - | - | - | - | - | thin, not tested |
| HOLIDAY_OPEN | MV | 1 | - | thin | - | - | - | - | - | thin, not tested |
| HOLIDAY_OPEN | PB | 1 | - | thin | - | - | - | - | - | thin, not tested |
| HOLIDAY_OPEN | PE | 9 | - | thin | - | - | - | - | - | thin, not tested |
| HOLIDAY_OPEN | SM | 5 | - | thin | - | - | - | - | - | thin, not tested |
| HOLIDAY_OPEN | STACK | 37 | 4 | -539 | +107 | -647 | 555 | 0.00 | 0.00 | exceeds MDE |
| DAY_AFTER | HM | 108 | 29 | +240 | +92 | +148 | 504 | 0.43 | 0.78 | inside MDE |
| DAY_AFTER | KB | 241 | 29 | +150 | +25 | +125 | 179 | 0.03 | 0.34 | inside MDE |
| DAY_AFTER | MV | 111 | 28 | -110 | +1 | -111 | 306 | 0.33 | 0.78 | inside MDE |
| DAY_AFTER | PB | 43 | 25 | +338 | +105 | +233 | 525 | 0.20 | 0.63 | inside MDE |
| DAY_AFTER | PE | 138 | 29 | +318 | +317 | +1 | 1034 | 0.93 | 0.95 | inside MDE |
| DAY_AFTER | SM | 46 | 26 | +665 | +204 | +461 | 1041 | 0.21 | 0.63 | inside MDE |
| DAY_AFTER | STACK | 687 | 29 | +202 | +107 | +95 | 312 | 0.42 | 0.78 | inside MDE |
| SUNDAY | HM | 320 | 184 | +342 | +92 | +250 | 394 | 0.05 | 0.36 | inside MDE |
| SUNDAY | KB | 436 | 185 | +74 | +25 | +49 | 147 | 0.35 | 0.78 | inside MDE |
| SUNDAY | MV | 0 | - | thin | - | - | - | - | - | thin, not tested |
| SUNDAY | PB | 212 | 131 | -16 | +105 | -120 | 249 | 0.19 | 0.63 | inside MDE |
| SUNDAY | PE | 399 | 185 | +399 | +317 | +82 | 713 | 0.73 | 0.95 | inside MDE |
| SUNDAY | SM | 128 | 105 | +388 | +204 | +184 | 747 | 0.47 | 0.78 | inside MDE |
| SUNDAY | STACK | 1495 | 185 | +232 | +107 | +125 | 288 | 0.22 | 0.63 | inside MDE |

Family: day-shuffled class-label null over the 20 testable class x book cells, max |t| observed 3.22, family p 0.134 (200 worlds); BH q: HOLIDAY_OPEN STACK 0.000 at cell level but it is 37 trades on 4 days (all four days negative: -2.2k, -1.0k, -4.9k, -11.9k), so thin and not a rule; next best DAY_AFTER KB p 0.034 q 0.34, SUNDAY HM p 0.054 q 0.36.
**Plain sentence:** the live books do not misbehave on early closes or around the maintenance halt (flat deadlines respect the early close and the 17:00 halt; the day_complete=false cases SHADOW-2 flagged are research-filter artefacts of those same irregular days, not live rule breaks); the only large class gap is the HOLIDAY_OPEN stack loss on 4 days (one of which, 20261019, may be a data gap), which is thin and not family-significant (p 0.134); day-after-holiday and Sunday-open means are higher than NORMAL for KB and HM but inside or near MDE with q >= 0.34. No irregular-session switch is proposed. Stop slippage by class is not measurable from the engine rows.
Next in DIS-AU: (i) check 20261019 against the raw 1-s tables (data gap vs real session), (ii) 2013+ signal-level entry counts on irregular sessions (no P&L claim, per DIS-X), (iii) hold-time of EARLY-day trades if an exit-second can be recovered from the 1-s engine.
Correction note (S4b, DIS-AU interim 1): the reference line should read "88,490 engine rows, 21,397 taken trades with finite P&L over 927 label days" (my text above wrote 20,997 in error); and the early-day flat deadlines are 12:59 on most early days and 13:14 on the 3 July / Thanksgiving-Friday / Christmas-Eve type days (max observed 13:14), not 13:15. Class trade counts: NORMAL 18,879, SUNDAY 1,495, DAY_AFTER 687, EARLY 299, HOLIDAY_OPEN 37.

## DIS-AV (Z1, 2026-11-04 23:40Z): WHY ES BUT NOT RTY/YM? Descriptive link between the 2026 fade excess and each instrument's own intraday-structure changes - interim 1 (no causal claim, no PASS, nothing live)
Scope DISAV_scope.md sha256 9ec9d1dd4bc6b8bb29030170535f95e8b315c0fbc3f3c168dd7918fd9ce5d7b5 (logged in DECISIONS.md before any number); ledger DIS_AV (24 link cells); n_tested FADE_DISAV 69; code l2vast/ds3/code/disav/av.py; tables l2vast/ds3/out/disav/levels.csv, links.csv, pooled.csv, rank.csv.
**Plain sentence:** the 2026 move of the first hour toward a larger share of the day range and volume is visible on NQ, ES and YM (95% block-bootstrap intervals exclude 0) and not on RTY, and the 10-11h reversal rate did not change on any instrument; but the daily link between those changes and the fade excess is nil once forward-safe (lag 1: pooled r 0.02, 0.08 and 0.06 in absolute size, none passing the family test), and YM has the LARGEST first-hour concentration shift with a smaller excess than ES, so these three one-minute structure metrics do not explain why ES carries the excess and RTY/YM do not. Same-day reversal rate correlates +0.21 to +0.25 with the fade excess on every instrument (family p <= .025 each, pooled r 0.23 [0.17, 0.29]), but that is mechanical (the fade lines trade those hours) and vanishes at lag 1 (pooled 0.02). No PASS.
**Level shift 2026 vs baseline 2024-02..2025-10 (95% block bootstrap):** | inst | metric | baseline | 2026 | shift [CI] |
|--|--|--|--|--|
| NQ | rev1011 | 0.492 | 0.503 | +0.011 [-0.100, +0.093] |
| NQ | fh_range_share | 0.608 | 0.668 | +0.060 [+0.020, +0.097] * |
| NQ | fh_vol_share | 0.275 | 0.299 | +0.025 [+0.011, +0.035] * |
| ES | rev1011 | 0.481 | 0.495 | +0.013 [-0.073, +0.100] |
| ES | fh_range_share | 0.536 | 0.593 | +0.057 [+0.026, +0.092] * |
| ES | fh_vol_share | 0.240 | 0.251 | +0.011 [+0.002, +0.021] * |
| RTY | rev1011 | 0.482 | 0.483 | +0.001 [-0.074, +0.089] |
| RTY | fh_range_share | 0.659 | 0.683 | +0.024 [-0.018, +0.062] |
| RTY | fh_vol_share | 0.294 | 0.298 | +0.004 [-0.009, +0.016] |
| YM | rev1011 | 0.485 | 0.490 | +0.005 [-0.071, +0.090] |
| YM | fh_range_share | 0.606 | 0.688 | +0.082 [+0.051, +0.120] * |
| YM | fh_vol_share | 0.309 | 0.354 | +0.045 [+0.032, +0.057] * |

**Daily links over HOLD days (r with block-bootstrap CI; placebo p = circular day-shift; family p = max-|r| over the 24 tests):** | inst | metric | lag | r [CI] | p | family p | BH q | label |
|--|--|--|--|--|--|--|--|
| NQ | rev1011 | 0 | +0.233 [+0.125, +0.342] | 0.010 | 0.015 | 0.06 | ASSOCIATED |
| NQ | rev1011 | 1 | +0.096 [-0.010, +0.192] | 0.139 | 0.995 | 0.41 | NONE |
| NQ | fh_range_share | 0 | -0.110 [-0.235, +0.005] | 0.114 | 0.940 | 0.39 | NONE |
| NQ | fh_range_share | 1 | -0.070 [-0.176, +0.069] | 0.264 | 1.000 | 0.57 | NONE |
| NQ | fh_vol_share | 0 | -0.011 [-0.167, +0.134] | 0.841 | 1.000 | 0.92 | NONE |
| NQ | fh_vol_share | 1 | -0.012 [-0.125, +0.114] | 0.821 | 1.000 | 0.92 | NONE |
| ES | rev1011 | 0 | +0.212 [+0.085, +0.336] | 0.010 | 0.025 | 0.06 | ASSOCIATED |
| ES | rev1011 | 1 | -0.071 [-0.193, +0.013] | 0.284 | 1.000 | 0.57 | NONE |
| ES | fh_range_share | 0 | -0.039 [-0.159, +0.104] | 0.577 | 1.000 | 0.87 | NONE |
| ES | fh_range_share | 1 | -0.054 [-0.155, +0.079] | 0.353 | 1.000 | 0.65 | NONE |
| ES | fh_vol_share | 0 | +0.033 [-0.089, +0.168] | 0.622 | 1.000 | 0.88 | NONE |
| ES | fh_vol_share | 1 | -0.107 [-0.218, -0.010] | 0.090 | 0.965 | 0.36 | PER-TEST ONLY |
| RTY | rev1011 | 0 | +0.213 [+0.100, +0.324] | 0.005 | 0.025 | 0.06 | ASSOCIATED |
| RTY | rev1011 | 1 | +0.053 [-0.110, +0.183] | 0.388 | 1.000 | 0.67 | NONE |
| RTY | fh_range_share | 0 | -0.101 [-0.228, +0.029] | 0.154 | 0.975 | 0.41 | NONE |
| RTY | fh_range_share | 1 | -0.042 [-0.197, +0.083] | 0.542 | 1.000 | 0.87 | NONE |
| RTY | fh_vol_share | 0 | -0.023 [-0.166, +0.121] | 0.726 | 1.000 | 0.91 | NONE |
| RTY | fh_vol_share | 1 | -0.028 [-0.174, +0.088] | 0.667 | 1.000 | 0.89 | NONE |
| YM | rev1011 | 0 | +0.253 [+0.137, +0.370] | 0.010 | 0.015 | 0.06 | ASSOCIATED |
| YM | rev1011 | 1 | +0.003 [-0.120, +0.109] | 0.925 | 1.000 | 0.93 | NONE |
| YM | fh_range_share | 0 | -0.020 [-0.132, +0.107] | 0.761 | 1.000 | 0.91 | NONE |
| YM | fh_range_share | 1 | -0.144 [-0.239, -0.036] | 0.025 | 0.393 | 0.12 | PER-TEST ONLY |
| YM | fh_vol_share | 0 | -0.012 [-0.116, +0.092] | 0.881 | 1.000 | 0.92 | NONE |
| YM | fh_vol_share | 1 | -0.091 [-0.162, -0.000] | 0.179 | 1.000 | 0.43 | NONE |

Pooled (4 instruments stacked, day-block bootstrap): rev1011 lag 0 r +0.228 [+0.165, +0.291]; rev1011 lag 1 r +0.021 [-0.043, +0.065]; fh_range_share lag 0 r -0.068 [-0.140, +0.003]; fh_range_share lag 1 r -0.077 [-0.149, -0.000]; fh_vol_share lag 0 r -0.003 [-0.079, +0.073]; fh_vol_share lag 1 r -0.059 [-0.134, +0.006].
Between-instrument rank agreement of the 2026 level shift with the 2026 bundle excess (n = 4, descriptive, minimum one-sided p 0.042): rev1011 Spearman 0.8; fh_range_share Spearman 0.4; fh_vol_share Spearman 0.4. Excess pts/week 2026: NQ 128, ES 86, YM 37, RTY -1. Reading: RTY is the one index with no first-hour range/volume concentration shift AND no excess, which fits a flow-concentration story descriptively (3 of 4 points), but YM breaks the ordering (largest shift, smaller excess), and the reversal rate, the metric closest to the fade, did not shift anywhere.
Limits: spread and depth are not used (no daily series for all four, YM has no L2; Q4_NQ_STRUCTURE.md shows market-wide thinning on NQ/ES/RTY, so it does not separate ES from RTY either); n = 4 instruments; data end 2026-10-16; metrics are one-minute, so ES tick and NQ L2 daily series remain an open item. DIS-AV closed at this interim.


# DS3_DISCOVER2 - section S4b: DIS-AU interim 2 (data-gap day, HOLIDAY_OPEN revised, 2013+ counts) - 2026-11-04 22:45Z
Append-only; supersedes the HOLIDAY_OPEN / DAY_AFTER lines of interim 1 where stated.
## 20261019 verified: a derived-table gap, not a holiday and not a missing-data day in the 1-s tables
2026-10-19 is a Monday and not a CME equity holiday. The raw 1-s NQ tables hold 1,381 distinct minutes with rows for that label day (the normal count is 1,380), but the derived minute table ds3_fade/minute.parquet has only 120 bars for it (and 1,260 on 20261020, the missing 120 minutes being the same hole across the 18:00 label-day boundary). The 1-s engine therefore ran the day in full: 12 taken trades, -$11,916 at Q1-A lots (all in the stack). It is relabelled DATA_GAP (minute-table gap) and removed from HOLIDAY_OPEN; 20261020 is relabelled NORMAL (it had been classed DAY_AFTER only because of the hole).
**Revised HOLIDAY_OPEN:** n = 3 days (20230407 Good Friday, 20250109 national day of mourning, 20260403 Good Friday), 25 stack trades, -322 $/trade vs NORMAL +107 = diff -429 (MDE 374, block-bootstrap p < .001, BH q 0.28 over 20 cells). Family max-T (200 day-shuffled worlds) p 0.194. Three days only: thin, not a rule. DAY_AFTER (28 days, 644 trades): stack +219 vs +107 (diff +112, MDE 330); KB +137 (p 0.024, q 0.17), SM +694 (p 0.026, q 0.17) - inside MDE for the stack, not family-significant. SUNDAY unchanged (HM +251, p 0.052, q 0.26). Other classes unchanged.
## Other days with 1-s coverage < 98% of the live-session hours (2023-04-03..2026-10-30, 927 label days)
Coverage = minutes with at least one 1-s row divided by the minute-table bar count of the same label day (and by the class's own expected length). **Only 20261019 fails** (11.5 x: the minute table is the short one); every other label day has 1-s minute coverage within 100% of its minute-table bars, so there are no further 1-s data-gap days in 2023-26; the NORMAL-day minute count is 1,353-1,380 (1% quantile 1,369). The irregular days are short by design (early closes 1,140 minutes; Good Friday 909).
**How day_complete handles gap days:** Shadow2 Q13 requires >= 300 RTH bars, a 09:30 first bar and a 15:59 last bar from the streamed bars, so a day with a minute-bar hole is day_complete = False and the research row is dropped while the live logger still records its signals (the 8 / 12 / 1 flagged days of SHADOW_PACK_2 are of this kind and of the early-close kind); DIS-K requires >= 20,000 seconds with data; the 1-s engine has no completeness test and trades the day as it comes, which is why 20261019 carries 12 trades. A minute-table rebuild of 20261019 from the 1-s tables is needed before any minute-table research uses that day (flag for the lead; nothing in the live path is affected).
## 2013-2026 irregular-session entry counts (APX 1-minute signal layer of DIS-Y/X, entry streams with the APX flat rules; **signal-level, not live-stack P&L, no P&L claim**)
| period | class | days | APX entries | entries/day | mean $/trade at 1 lot (APX, not live) | win | spans 17:00 halt | open past early close | entry after early close |
|---|---|---|---|---|---|---|---|---|---|
| pre | NORMAL | 2473 | 26479 | 10.7 | -37 | 0.49 | 0 | 0 | 0 |
| pre | EARLY | 76 | 421 | 5.5 | +8 | 0.48 | 0 | 0 | 0 |
| pre | HOLIDAY_OPEN | 4 | 16 | 4.0 | +198 | 0.62 | 0 | 0 | 0 |
| pre | DAY_AFTER | 80 | 873 | 10.9 | +97 | 0.55 | 0 | 0 | 0 |
| pre | SUNDAY | 522 | 2563 | 4.9 | -20 | 0.49 | 0 | 0 | 0 |
| post | NORMAL | 853 | 21872 | 25.6 | +16 | 0.51 | 0 | 0 | 0 |
| post | EARLY | 33 | 348 | 10.5 | +62 | 0.52 | 0 | 0 | 0 |
| post | HOLIDAY_OPEN | 3 | 28 | 9.3 | -212 | 0.39 | 0 | 0 | 0 |
| post | DAY_AFTER | 28 | 736 | 26.3 | +119 | 0.55 | 0 | 0 | 0 |
| post | SUNDAY | 183 | 1470 | 8.0 | +77 | 0.54 | 0 | 0 | 0 |
Plain sentence: entries per day on EARLY days are about half of NORMAL in both eras (5.5 vs 10.7 pre-2023, 10.6 vs 25.6 from 2023), as expected for a 13:00 close; DAY_AFTER and SUNDAY entry rates are in line (DAY_AFTER 10.9 vs 10.7 / 26.3 vs 25.6); no APX trade spans the 17:00-18:00 halt, stays open past an early close, or enters after the early close in RTH (all zero) - but that is a property of the APX flat rules, so it confirms the sim, not the live engine, which was checked separately above (flat deadlines 12:59-13:14 on early days, 16:54 otherwise). Mean $/trade by class at the APX layer is of mixed sign and not claimed (HOLIDAY_OPEN has 16 and 28 trades). Only 4 pre-2023 and 3 post-2023 no-RTH-bar days exist in the cache, so holiday-open behaviour is not testable beyond n = 3-4 days per era.
**DIS-AU status:** measurement complete at the engine and APX layers; no irregular-session rule defect found; stop slippage by class not measurable from the engine rows (no exit price exposed). Closing DIS-AU; ledger revised rows appended.

## DIS-BC (Z1, 2026-11-05 ~00:30Z): DAILY LIQUIDITY SERIES (NQ, ES, RTY 1-s L2) vs the fade-bundle excess - interim 1 (descriptive, no causal claim, no PASS, nothing live)
Scope DISBC_scope.md sha256 1131b4e80fbbeaa3eacb0d9fd7fc40ea6843ce19d2cee27596b7bd7afabff1cf (in DECISIONS.md before any number; dead_lookup first, no rows); ledger DIS_BC (72 cells); n_tested FADE_DISBC 168; code l2vast/ds3/code/disbc/ (bc_micro.py, bc_an.py); tables l2vast/ds3/out/disbc/ (micro.parquet, levels.csv, nq_vs.csv, links.csv).
**Plain sentence:** from the 1-s L2 tables, the 2026 market got thinner on all three indices (top-of-book and 5-level depth down 0.5 to 1.0 baseline sd, trades smaller, spread wider), NQ with the largest spread widening (+0.9 sd against +0.3 on ES and RTY), and refill per print moved the opposite way on NQ (-0.9 sd) than on ES (+1.7) and RTY (+1.3); but none of these series, lagged one day, associates with the fade-bundle excess (36 tests, smallest family p 0.48; one per-test hit, ES 10-11h spread, p .07), and nothing separates ES (which has the excess) from RTY (which does not), because the thinning is common to both. So the liquidity data do not explain ES vs RTY; a YM comparison is impossible (no L2/tick table for YM). No PASS.
**Data/definitions:** 1-s tables NQ 2023-02.., ES and RTY 2023-08..2026-10 (the ES trade ticks under rootmoves were not needed: the 1-s table carries trades and book); YM and nothing else has no L2/ticks, so spread, depth, rate, size and refill cannot be built for YM, and the 4-instrument comparison of DIS-AV is impossible for them. RTY was added (its 1-s tables exist). Windows H1 09:30-10:29, H2 10:00-10:59 ET, day-window needs >= 80% of seconds. spread = mean 1-s spread_t (time-weighted, ticks, clip 0-50); tob = bsz1+asz1; depth5 = 5 levels both sides; rate = trades/s; msize = volume/trades; refill = refill_n/trades (refill SPEED in seconds is not stored; this is the refill count per print). Instrument units differ (NQ spread in 0.25 ticks), hence standardised shifts.
**Level shift 2026 vs 2024-02..2025-10, in baseline sd [95% block bootstrap]; * = excludes 0:** | inst | window | series | baseline | 2026 | z [CI] |
|--|--|--|--|--|--|
| NQ | H1 | spread | 2.574 | 3.382 | +0.90 [+0.47, +1.41] * |
| NQ | H1 | tob | 4.811 | 3.594 | -1.04 [-1.38, -0.72] * |
| NQ | H1 | depth5 | 45.015 | 32.428 | -0.97 [-1.30, -0.66] * |
| NQ | H1 | rate | 21.862 | 23.593 | +0.25 [-0.05, +0.48] |
| NQ | H1 | msize | 1.459 | 1.373 | -1.18 [-1.63, -0.77] * |
| NQ | H1 | refill | 0.407 | 0.349 | -0.88 [-1.35, -0.47] * |
| NQ | H2 | spread | 2.448 | 3.172 | +0.84 [+0.41, +1.33] * |
| NQ | H2 | tob | 5.134 | 3.877 | -0.92 [-1.27, -0.60] * |
| NQ | H2 | depth5 | 48.794 | 35.917 | -0.91 [-1.25, -0.59] * |
| NQ | H2 | rate | 16.591 | 17.127 | +0.09 [-0.14, +0.33] |
| NQ | H2 | msize | 1.490 | 1.404 | -1.05 [-1.48, -0.68] * |
| NQ | H2 | refill | 0.417 | 0.371 | -0.77 [-1.30, -0.28] * |
| ES | H1 | spread | 1.042 | 1.069 | +0.32 [+0.02, +0.60] * |
| ES | H1 | tob | 73.831 | 44.527 | -0.79 [-1.08, -0.54] * |
| ES | H1 | depth5 | 629.577 | 394.681 | -0.88 [-1.20, -0.63] * |
| ES | H1 | rate | 24.241 | 27.184 | +0.26 [-0.01, +0.53] |
| ES | H1 | msize | 3.070 | 2.806 | -0.53 [-0.89, -0.20] * |
| ES | H1 | refill | 0.260 | 0.378 | +1.73 [+1.45, +2.05] * |
| ES | H2 | spread | 1.035 | 1.059 | +0.29 [+0.01, +0.54] * |
| ES | H2 | tob | 76.574 | 48.913 | -0.74 [-1.03, -0.48] * |
| ES | H2 | depth5 | 662.311 | 438.512 | -0.82 [-1.14, -0.55] * |
| ES | H2 | rate | 19.580 | 21.555 | +0.19 [-0.07, +0.46] |
| ES | H2 | msize | 3.125 | 2.894 | -0.46 [-0.83, -0.13] * |
| ES | H2 | refill | 0.259 | 0.375 | +1.68 [+1.39, +2.02] * |
| RTY | H1 | spread | 1.804 | 1.898 | +0.31 [+0.01, +0.69] * |
| RTY | H1 | tob | 10.704 | 8.572 | -0.62 [-1.03, -0.31] * |
| RTY | H1 | depth5 | 134.547 | 103.024 | -0.82 [-1.27, -0.47] * |
| RTY | H1 | rate | 6.222 | 6.863 | +0.26 [-0.05, +0.60] |
| RTY | H1 | msize | 1.756 | 1.631 | -0.89 [-1.28, -0.56] * |
| RTY | H1 | refill | 0.536 | 0.593 | +1.33 [+0.98, +1.62] * |
| RTY | H2 | spread | 1.750 | 1.853 | +0.33 [+0.03, +0.71] * |
| RTY | H2 | tob | 11.417 | 9.352 | -0.54 [-0.98, -0.20] * |
| RTY | H2 | depth5 | 145.813 | 112.609 | -0.78 [-1.25, -0.43] * |
| RTY | H2 | rate | 4.171 | 4.473 | +0.14 [-0.13, +0.44] |
| RTY | H2 | msize | 1.768 | 1.660 | -0.73 [-1.16, -0.37] * |
| RTY | H2 | refill | 0.548 | 0.608 | +1.34 [+1.03, +1.65] * |

**NQ minus ES / RTY difference of standardised shifts [95%]:** | vs | window | series | NQ z | other z | diff [CI] |
|--|--|--|--|--|--|
| ES | H1 | spread | +0.90 | +0.32 | +0.58 [+0.08, +1.17] * |
| ES | H1 | tob | -1.04 | -0.79 | -0.24 [-0.69, +0.18] |
| ES | H1 | depth5 | -0.97 | -0.88 | -0.09 [-0.50, +0.37] |
| ES | H1 | rate | +0.25 | +0.26 | -0.01 [-0.41, +0.33] |
| ES | H1 | msize | -1.18 | -0.53 | -0.65 [-1.19, -0.11] * |
| ES | H1 | refill | -0.88 | +1.73 | -2.61 [-3.18, -2.10] * |
| ES | H2 | spread | +0.84 | +0.29 | +0.55 [+0.05, +1.09] * |
| ES | H2 | tob | -0.92 | -0.74 | -0.18 [-0.61, +0.24] |
| ES | H2 | depth5 | -0.91 | -0.82 | -0.09 [-0.53, +0.38] |
| ES | H2 | rate | +0.09 | +0.19 | -0.10 [-0.48, +0.24] |
| ES | H2 | msize | -1.05 | -0.46 | -0.60 [-1.12, -0.07] * |
| ES | H2 | refill | -0.77 | +1.68 | -2.45 [-3.08, -1.94] * |
| RTY | H1 | spread | +0.90 | +0.31 | +0.59 [+0.01, +1.15] * |
| RTY | H1 | tob | -1.04 | -0.62 | -0.42 [-0.89, +0.11] |
| RTY | H1 | depth5 | -0.97 | -0.82 | -0.15 [-0.61, +0.39] |
| RTY | H1 | rate | +0.25 | +0.26 | -0.01 [-0.49, +0.37] |
| RTY | H1 | msize | -1.18 | -0.89 | -0.29 [-0.84, +0.29] |
| RTY | H1 | refill | -0.88 | +1.33 | -2.21 [-2.77, -1.64] * |
| RTY | H2 | spread | +0.84 | +0.33 | +0.51 [-0.09, +1.07] |
| RTY | H2 | tob | -0.92 | -0.54 | -0.38 [-0.85, +0.17] |
| RTY | H2 | depth5 | -0.91 | -0.78 | -0.13 [-0.60, +0.46] |
| RTY | H2 | rate | +0.09 | +0.14 | -0.05 [-0.44, +0.29] |
| RTY | H2 | msize | -1.05 | -0.73 | -0.32 [-0.86, +0.24] |
| RTY | H2 | refill | -0.77 | +1.34 | -2.11 [-2.72, -1.55] * |

**Lag-1 (forward-safe) link of the series change to the bundle excess over HOLD days (r [CI], placebo p, family p of 36, BH q):** | inst | window | series | r [CI] | p | family p | q | label |
|--|--|--|--|--|--|--|--|
| NQ | H1 | spread | -0.02 [-0.14, +0.11] | 0.697 | 1.000 | 0.90 | NONE |
| NQ | H1 | tob | -0.04 [-0.18, +0.11] | 0.587 | 1.000 | 0.84 | NONE |
| NQ | H1 | depth5 | -0.05 [-0.19, +0.10] | 0.463 | 1.000 | 0.84 | NONE |
| NQ | H1 | rate | -0.02 [-0.16, +0.10] | 0.731 | 1.000 | 0.90 | NONE |
| NQ | H1 | msize | -0.04 [-0.17, +0.12] | 0.587 | 1.000 | 0.84 | NONE |
| NQ | H1 | refill | +0.01 [-0.10, +0.12] | 0.826 | 1.000 | 0.91 | NONE |
| NQ | H2 | spread | -0.04 [-0.15, +0.10] | 0.577 | 1.000 | 0.84 | NONE |
| NQ | H2 | tob | -0.05 [-0.22, +0.10] | 0.463 | 1.000 | 0.84 | NONE |
| NQ | H2 | depth5 | -0.05 [-0.20, +0.09] | 0.468 | 0.995 | 0.84 | NONE |
| NQ | H2 | rate | -0.01 [-0.14, +0.12] | 0.945 | 1.000 | 0.95 | NONE |
| NQ | H2 | msize | -0.04 [-0.18, +0.12] | 0.557 | 1.000 | 0.84 | NONE |
| NQ | H2 | refill | -0.00 [-0.11, +0.09] | 0.930 | 1.000 | 0.95 | NONE |
| ES | H1 | spread | +0.11 [-0.03, +0.21] | 0.144 | 0.736 | 0.84 | NONE |
| ES | H1 | tob | -0.06 [-0.17, +0.07] | 0.438 | 0.990 | 0.84 | NONE |
| ES | H1 | depth5 | -0.07 [-0.17, +0.06] | 0.443 | 0.985 | 0.84 | NONE |
| ES | H1 | rate | -0.03 [-0.15, +0.09] | 0.612 | 1.000 | 0.84 | NONE |
| ES | H1 | msize | -0.06 [-0.17, +0.06] | 0.463 | 0.990 | 0.84 | NONE |
| ES | H1 | refill | +0.11 [-0.03, +0.21] | 0.179 | 0.771 | 0.84 | NONE |
| ES | H2 | spread | +0.14 [-0.00, +0.25] | 0.070 | 0.483 | 0.84 | PER-TEST ONLY |
| ES | H2 | tob | -0.05 [-0.17, +0.07] | 0.473 | 0.995 | 0.84 | NONE |
| ES | H2 | depth5 | -0.06 [-0.17, +0.08] | 0.527 | 0.990 | 0.84 | NONE |
| ES | H2 | rate | +0.01 [-0.11, +0.16] | 0.900 | 1.000 | 0.95 | NONE |
| ES | H2 | msize | -0.03 [-0.14, +0.08] | 0.751 | 1.000 | 0.90 | NONE |
| ES | H2 | refill | +0.07 [-0.06, +0.18] | 0.338 | 0.965 | 0.84 | NONE |
| RTY | H1 | spread | +0.06 [-0.04, +0.16] | 0.388 | 0.990 | 0.84 | NONE |
| RTY | H1 | tob | -0.05 [-0.14, +0.08] | 0.378 | 1.000 | 0.84 | NONE |
| RTY | H1 | depth5 | -0.04 [-0.14, +0.08] | 0.373 | 1.000 | 0.84 | NONE |
| RTY | H1 | rate | +0.01 [-0.12, +0.14] | 0.831 | 1.000 | 0.91 | NONE |
| RTY | H1 | msize | -0.06 [-0.16, +0.07] | 0.249 | 0.995 | 0.84 | NONE |
| RTY | H1 | refill | -0.07 [-0.14, +0.05] | 0.229 | 0.975 | 0.84 | NONE |
| RTY | H2 | spread | +0.04 [-0.07, +0.14] | 0.632 | 1.000 | 0.84 | NONE |
| RTY | H2 | tob | -0.05 [-0.14, +0.07] | 0.289 | 1.000 | 0.84 | NONE |
| RTY | H2 | depth5 | -0.04 [-0.14, +0.07] | 0.358 | 1.000 | 0.84 | NONE |
| RTY | H2 | rate | +0.04 [-0.09, +0.16] | 0.463 | 1.000 | 0.84 | NONE |
| RTY | H2 | msize | -0.01 [-0.12, +0.13] | 0.811 | 1.000 | 0.91 | NONE |
| RTY | H2 | refill | -0.07 [-0.16, +0.04] | 0.204 | 0.975 | 0.84 | NONE |

Same-day links are mechanical and descriptive only: on ES eight of twelve same-day correlations have p <= .05 (spread +0.17/+0.18, top-of-book -0.17/-0.19, refill +0.23, mean size -0.18), on NQ none and on RTY three (H2 mean size -0.14, H2 refill +0.16, H1 mean size -0.11); this is the ES day-level co-movement with the fade bundle (more refill and wider spread on days the fade pays), not forward information (lag 1 is nil).
Limits: three instruments; ES/RTY start 2023-08; refill is a count per print, not a time; no tick-level spread (the 1-s grid is time-weighted); data end 2026-10-30 for the L2 tables but the DIS-AO excess ends 2026-10-16/23. DIS-BC closed at this interim.
- Correction (Z1, DIS-BC): on ES nine (not eight) of the twelve same-day correlations have p <= .05 (H1: spread, top-of-book, 5-level depth, refill; H2: spread, top-of-book, 5-level depth, mean size, refill); the rest of the paragraph stands.

## DIS-BB (BASE-4, 2026-11-04T22:53Z): CAN THE TH-L2 CUT BE A RESTING STOP? - full page autopilot/DS3_TH_AS_STOP.md; scope DISBB_scope.md sha256 833bc47c14ffa6ec1cfc6ea2365ec9bd34c6ed51a7e0704c7161f5861fcc5133; ledger DIS_BB; no PASS, nothing live
TH-L2 -30 as a resting 30-pt stop: post-cap gain vs TH off at the same stop cost +1880 / +2060 / -36 $/wk at c = 0.80 / 1.28 / 2.45 (box-side cut +12368 / +14597 / +18076), 2023-26 -7616 / -7945 / -9129, HOLD maxDD $208388 at c = 1.28 (TH off $85551, TH on $121322); break-even stop cost 2.43 pt post-cap, none over 2023-26; the liquidity condition adds about +1.4k/wk post-cap and all of the 2023-26 gain.


# DS3_DISCOVER2 - section S4b: DIS-BF stop and TARGET fills of the live signal streams (extends Z3 DS3_TAIL_STRESS section 4) - interim 1, 2026-11-04 22:56Z
Prereg autopilot/DIS_BF_PREREG.md (sha256 24098e733d33f465bb63f0196be3524eab0eb90e9ae15a4cec37e4d9da5bd8bb in DECISIONS.md, before any statistic); n_tested 24 (DISBF_NTESTED.md); code l2vast/ds3/code/disc/bf_run.py, bf_an.py, bf_bound.py (Z3 object reused from tail_stress/slip_tape.py: dis_a sources(), 60/60 bracket, lots 1, BookHarness.simulate on the 1-s path); data /mnt/l2/l2vast/ds3_dr/bf_*.pkl. Measurement only, Shadow, no PASS claims. **Object caveat: it is Z3's signal-level 60/60 bracket object, not the live exit stack (no Trade-Health exits, locks, zones, 70/30), so the dollar bound below is for that object only.**
**Reproduction check passed:** 12,955 stop exits, slip_next mean 0.147 pt, median -0.25, p95 5.0, p99 16.5, max 102.2 (Z3: 12,955; 0.15; -0.25; 5.0; 16.5; 102.3). Exit counts: 12,955 stops, 14,325 targets, 622 time exits.
## Stop slippage (slip_next = stop level minus the path close one second after the touch; adverse positive, points)
| factor | level | exits | mean (pt) | 95% CI | p95 | p99 |
|---|---|---|---|---|---|---|
| tod | 00-02 | 814 | -0.01 | -0.25..0.22 | 3.5 | 14.4 |
| tod | 02-08:30 | 3813 | -0.03 | -0.19..0.14 | 3.5 | 8.0 |
| tod | 08:30-09:30 | 718 | 2.23 | -0.02..4.12 | 34.5 | 74.4 |
| tod | 09:30-10:30 | 2135 | 0.11 | -0.13..0.40 | 7.1 | 13.5 |
| tod | 10:30-12 | 1709 | 0.03 | -0.16..0.23 | 5.5 | 11.2 |
| tod | 12-14 | 1064 | -0.12 | -0.36..0.10 | 4.0 | 8.3 |
| tod | 14-16 | 533 | -0.10 | -0.55..0.31 | 5.8 | 15.4 |
| tod | 16-17 | 30 | -0.33 | -1.14..0.48 | 3.4 | 4.0 |
| tod | 18-24 | 2139 | 0.16 | -0.01..0.33 | 4.8 | 11.2 |
| vol | V1 low | 2577 | -0.13 | -0.42..0.13 | 3.5 | 9.0 |
| vol | V2 mid | 3921 | 0.32 | 0.06..0.63 | 4.8 | 18.8 |
| vol | V3 high | 6457 | 0.15 | -0.04..0.32 | 6.0 | 20.0 |
| sess | asia | 2953 | 0.11 | -0.03..0.26 | 4.2 | 11.5 |
| sess | close | 257 | -0.03 | -0.40..0.41 | 3.3 | 11.6 |
| sess | london | 3813 | -0.03 | -0.17..0.14 | 3.5 | 8.0 |
| sess | nyam | 3844 | 0.07 | -0.08..0.25 | 6.2 | 12.8 |
| sess | nypm | 1370 | -0.14 | -0.38..0.10 | 4.8 | 10.5 |
| sess | pre | 718 | 2.23 | 0.19..4.30 | 34.5 | 74.4 |
| book | HM | 1513 | 0.17 | -0.05..0.37 | 5.2 | 13.4 |
| book | KB | 3751 | 0.19 | 0.03..0.40 | 5.5 | 17.5 |
| book | MV | 1741 | 0.37 | 0.09..0.67 | 6.2 | 22.6 |
| book | PB | 2397 | -0.14 | -0.44..0.16 | 3.5 | 9.5 |
| book | PE | 2922 | 0.09 | -0.10..0.28 | 5.2 | 18.4 |
| book | SM | 631 | 0.59 | 0.02..1.30 | 5.5 | 42.3 |

Plain finding: stop slippage is concentrated in the 08:30-09:30 ET release hour (the 'pre' session): mean 2.23 pt (n 718) against about 0 for every other hour, p95 34.5 and p99 74.4 pt; the other time-of-day buckets have means -0.33..+0.16 pt. The engine's flat 2.45 pt stop cost is about right on average in that hour and too high everywhere else, but the tail is what matters: the share of stop exits slipping more than 2.45 pt is 21% in 08:30-09:30 and 09:30-10:30 versus 8-9% overnight; by volatility tercile the mean is -0.13 / +0.32 / +0.15 pt (V1/V2/V3) and the tail share rises 9.6% -> 12.1% -> 16.0% with the day's range. Books: SM 0.59 and MV 0.37 pt highest, PB -0.14 lowest; the book factor is not significant (omnibus p 0.94).
| factor | level | exits | mean (pt) | 95% CI | p95 | p99 |
|---|---|---|---|---|---|---|
| tod | 00-02 | 814 | 1.35 | 1.12..1.58 | 4.8 | 13.3 |
| tod | 02-08:30 | 3813 | 1.30 | 1.18..1.44 | 4.3 | 12.0 |
| tod | 08:30-09:30 | 718 | 5.48 | 4.17..7.11 | 29.4 | 58.5 |
| tod | 09:30-10:30 | 2135 | 1.94 | 1.78..2.14 | 6.5 | 14.5 |
| tod | 10:30-12 | 1709 | 1.52 | 1.39..1.68 | 5.5 | 10.2 |
| tod | 12-14 | 1064 | 1.34 | 1.21..1.50 | 4.5 | 11.3 |
| tod | 14-16 | 533 | 1.71 | 1.42..2.07 | 6.8 | 16.9 |
| tod | 16-17 | 30 | 0.83 | 0.39..1.37 | 3.4 | 5.8 |
| tod | 18-24 | 2139 | 1.68 | 1.41..2.03 | 5.5 | 12.2 |
| vol | V1 low | 2577 | 1.22 | 1.09..1.38 | 4.3 | 11.3 |
| vol | V2 mid | 3921 | 1.75 | 1.54..2.04 | 5.8 | 18.5 |
| vol | V3 high | 6457 | 1.97 | 1.81..2.14 | 6.8 | 18.2 |

## Tail share (stop exits with slip_next > 2.45 pt = the engine's stop cost)
| factor | level | exits | share | 95%% CI |
|---|---|---|---|---|
| tod | 00-02 | 814 | 0.080 | 0.058..0.102 |
| tod | 02-08:30 | 3813 | 0.089 | 0.077..0.101 |
| tod | 08:30-09:30 | 718 | 0.213 | 0.170..0.255 |
| tod | 09:30-10:30 | 2135 | 0.207 | 0.187..0.229 |
| tod | 10:30-12 | 1709 | 0.143 | 0.122..0.164 |
| tod | 12-14 | 1064 | 0.133 | 0.114..0.155 |
| tod | 14-16 | 533 | 0.120 | 0.094..0.154 |
| tod | 16-17 | 30 | 0.167 | 0.034..0.333 |
| tod | 18-24 | 2139 | 0.139 | 0.122..0.153 |
| vol | V1 low | 2577 | 0.096 | 0.082..0.108 |
| vol | V2 mid | 3921 | 0.121 | 0.108..0.134 |
| vol | V3 high | 6457 | 0.160 | 0.149..0.171 |
| sess | asia | 2953 | 0.123 | 0.109..0.135 |
| sess | close | 257 | 0.101 | 0.063..0.144 |
| sess | london | 3813 | 0.089 | 0.077..0.101 |
| sess | nyam | 3844 | 0.179 | 0.163..0.196 |
| sess | nypm | 1370 | 0.135 | 0.116..0.154 |
| sess | pre | 718 | 0.213 | 0.171..0.259 |
| cls | DAY_AFTER | 382 | 0.110 | 0.071..0.147 |
| cls | EARLY | 166 | 0.108 | 0.058..0.160 |
| cls | NORMAL | 12381 | 0.136 | 0.129..0.143 |

## TARGET fills (new; margin = ticks (0.25 pt) by which the touch second's extreme went THROUGH the target level; touch-only = margin < 1 tick, i.e. the level was reached but not printed through in the touch second; reversal = touch-only and the next-second close is back on the entry side by >= 1 tick)
| factor | level | exits | mean (ticks) | 95% CI | p95 | p99 |
|---|---|---|---|---|---|---|
| tod | 00-02 | 1036 | 7.24 | 5.96..8.70 | 30.2 | 57.3 |
| tod | 02-08:30 | 4294 | 5.93 | 5.47..6.43 | 22.0 | 50.0 |
| tod | 08:30-09:30 | 863 | 19.34 | 14.34..25.82 | 113.0 | 255.5 |
| tod | 09:30-10:30 | 2210 | 6.79 | 6.36..7.36 | 24.0 | 48.0 |
| tod | 10:30-12 | 1812 | 6.18 | 5.67..6.85 | 23.0 | 52.0 |
| tod | 12-14 | 1131 | 6.21 | 5.39..7.07 | 22.0 | 46.8 |
| tod | 14-16 | 616 | 6.21 | 5.42..7.32 | 23.2 | 53.0 |
| tod | 16-17 | 34 | 21.59 | 10.35..33.95 | 114.1 | 119.3 |
| tod | 18-24 | 2329 | 8.28 | 7.40..9.36 | 29.6 | 81.7 |
| vol | V1 low | 2115 | 5.42 | 4.63..6.44 | 18.3 | 51.0 |
| vol | V2 mid | 4310 | 7.56 | 6.56..8.74 | 26.0 | 92.8 |
| vol | V3 high | 7900 | 7.93 | 7.49..8.50 | 29.0 | 65.0 |
| sess | asia | 3365 | 7.96 | 7.18..9.01 | 30.0 | 68.7 |
| sess | close | 275 | 7.75 | 5.79..9.82 | 33.3 | 88.3 |
| sess | london | 4294 | 5.93 | 5.47..6.39 | 22.0 | 50.0 |
| sess | nyam | 4022 | 6.52 | 6.13..6.91 | 24.0 | 49.8 |
| sess | nypm | 1506 | 6.28 | 5.67..7.05 | 22.8 | 52.8 |
| sess | pre | 863 | 19.34 | 14.25..25.13 | 113.0 | 255.5 |

Of 14,325 target exits, 19.8% are touch-only and 14.2% are touch-only followed by a reversal in the next second. Touch-only share falls with volatility (V1 24.1% -> V2 21.3% -> V3 17.8%), is highest in the london / close sessions (22.9% / 24.7%) and lowest in nyam 09:30-10:30 (15.9%); irregular days are not different (EARLY 16.1%, DAY_AFTER 20.8%, n 224 / 514). The 08:30-09:30 target margin averages 19 ticks (p95 113) against 5-8 elsewhere: when the release moves price, targets are overshot, not just touched.
| factor | level | exits | share | 95%% CI |
|---|---|---|---|---|
| tod | 00-02 | 1036 | 0.191 | 0.161..0.221 |
| tod | 02-08:30 | 4294 | 0.229 | 0.215..0.244 |
| tod | 08:30-09:30 | 863 | 0.181 | 0.151..0.210 |
| tod | 09:30-10:30 | 2210 | 0.159 | 0.142..0.176 |
| tod | 10:30-12 | 1812 | 0.195 | 0.175..0.217 |
| tod | 12-14 | 1131 | 0.197 | 0.173..0.223 |
| tod | 14-16 | 616 | 0.216 | 0.181..0.249 |
| tod | 16-17 | 34 | 0.235 | 0.105..0.400 |
| tod | 18-24 | 2329 | 0.184 | 0.168..0.201 |
| vol | V1 low | 2115 | 0.241 | 0.220..0.261 |
| vol | V2 mid | 4310 | 0.213 | 0.199..0.227 |
| vol | V3 high | 7900 | 0.178 | 0.170..0.187 |
| sess | asia | 3365 | 0.186 | 0.171..0.200 |
| sess | close | 275 | 0.247 | 0.195..0.297 |
| sess | london | 4294 | 0.229 | 0.217..0.246 |
| sess | nyam | 4022 | 0.175 | 0.160..0.188 |
| sess | nypm | 1506 | 0.197 | 0.176..0.217 |
| sess | pre | 863 | 0.181 | 0.152..0.210 |
| cls | DATA_GAP | 36 | 0.222 | 0.222..0.222 |
| cls | DAY_AFTER | 514 | 0.208 | 0.166..0.257 |
| cls | EARLY | 224 | 0.161 | 0.101..0.212 |
| cls | NORMAL | 13544 | 0.198 | 0.191..0.205 |

| factor | level | exits | share | 95%% CI |
|---|---|---|---|---|
| tod | 00-02 | 1036 | 0.142 | 0.119..0.166 |
| tod | 02-08:30 | 4294 | 0.164 | 0.151..0.175 |
| tod | 08:30-09:30 | 863 | 0.124 | 0.102..0.150 |
| tod | 09:30-10:30 | 2210 | 0.111 | 0.097..0.124 |
| tod | 10:30-12 | 1812 | 0.143 | 0.127..0.161 |
| tod | 12-14 | 1131 | 0.151 | 0.131..0.170 |
| tod | 14-16 | 616 | 0.170 | 0.139..0.207 |
| tod | 16-17 | 34 | 0.088 | 0.000..0.189 |
| tod | 18-24 | 2329 | 0.128 | 0.116..0.142 |
| vol | V1 low | 2115 | 0.173 | 0.155..0.190 |
| vol | V2 mid | 4310 | 0.152 | 0.140..0.164 |
| vol | V3 high | 7900 | 0.129 | 0.121..0.136 |
| sess | asia | 3365 | 0.132 | 0.121..0.146 |
| sess | close | 275 | 0.185 | 0.131..0.232 |
| sess | london | 4294 | 0.164 | 0.151..0.178 |
| sess | nyam | 4022 | 0.125 | 0.116..0.138 |
| sess | nypm | 1506 | 0.151 | 0.134..0.168 |
| sess | pre | 863 | 0.124 | 0.102..0.151 |

### Dollar bound on the touch-only targets (the 60/60 signal object, 1 lot, $20/pt; engine total = sum of net points of all exits 2023-26)
| book | target exits | touch-only flagged | engine total (1 lot, 60/60 object) | delta if flagged targets are not filled (run on) | per flagged trade |
|---|---|---|---|---|---|
| KB | 3951 | 736 | +20807 | +223058 | +303 |
| PE | 3117 | 605 | +60795 | +91885 | +152 |
| SM | 722 | 135 | +69803 | -86243 | -639 |
| HM | 1722 | 347 | +154823 | -78446 | -226 |
| MV | 1857 | 343 | +33993 | +24294 | +71 |
| PB | 2956 | 670 | +524171 | +77978 | +116 |

Reading: if every touch-only target were NOT filled and the trade ran on to its stop / time exit, the object's total would change by +$252,526 (+29% of the engine total; +$182,231 if only the 2,038 reversal cases are unfilled), because on average these trades continue in favour: +$89 per flagged trade; the result is book dependent (KB +$303, PE +$152, MV +$71, PB +$116 per flagged trade; SM -$639 and HM -$226 per flagged trade lose if the target is not filled). So a missed fill at the touch is NOT a cost on average in this object, but the SM and HM books are the exposed ones. This is a 60/60 bracket object without the live trailing logic: do not read it as a live-P&L bound.
## Omnibus tests (equal group means, day-block permutation) with BH over the 24 registered tests
| kind | metric | factor | omnibus p (day-block perm.) | BH q (24 registered) |
|---|---|---|---|---|
| stop | slip_next | tod | 0.079 | 0.126 |
| stop | slip_next | vol | 0.034 | 0.068 |
| stop | slip_next | sess | 0.015 | 0.035 |
| stop | slip_next | book | 0.941 | 0.996 |
| stop | slip_within | tod | 0.016 | 0.035 |
| stop | slip_within | vol | 0.001 | 0.004 |
| stop | slip_within | sess | 0.003 | 0.009 |
| stop | slip_within | book | 0.890 | 0.996 |
| stop | tail | tod | 0.140 | 0.210 |
| stop | tail | vol | 0.001 | 0.004 |
| stop | tail | sess | 0.002 | 0.007 |
| stop | tail | book | 0.946 | 0.996 |
| target | t_margin | tod | 0.006 | 0.016 |
| target | t_margin | vol | 0.001 | 0.004 |
| target | t_margin | sess | 0.001 | 0.004 |
| target | t_margin | book | 0.996 | 0.996 |
| target | touch_only | tod | 0.351 | 0.468 |
| target | touch_only | vol | 0.001 | 0.004 |
| target | touch_only | sess | 0.052 | 0.089 |
| target | touch_only | book | 0.978 | 0.996 |
| target | rev | tod | 0.192 | 0.271 |
| target | rev | vol | 0.001 | 0.004 |
| target | rev | sess | 0.037 | 0.068 |
| target | rev | book | 0.996 | 0.996 |

**Plain sentence:** stop slippage is time-of-day and volatility dependent, not book dependent: the 08:30-09:30 release hour carries 2.2 pt mean and a 74 pt p99 per stop exit, and high-volatility days carry a 16% tail share against 9.6% on quiet days (BH q 0.004); about one in five target exits only touches the level (a queue-fill risk proxy, higher in quiet markets and in london / close), and the cost of a missed touch is small on average but not zero for SM and HM. The pooled engine stop cost (2.45 pt) is not violated on average; the tails are concentrated in a known hour. Nothing here is a trading edge; it is an input for the live stop-cost assumption and the Monday 08:30 release-hour caution.
DIS-BF significance note (S4b): by BH over the 24 registered tests the strong effects are volatility (stop tail share q 0.004, slip_within q 0.004, target margin q 0.004, touch-only share q 0.004, reversal q 0.004), session (stop slip_next q 0.035, slip_within q 0.009, tail q 0.007, target margin q 0.004) and time of day for slip_within (q 0.035) and target margin (q 0.016); time of day for slip_next itself is not significant after BH (p 0.079, q 0.126), i.e. the 08:30-09:30 mean of 2.23 pt is carried by the 'pre' session factor (q 0.035) and a heavy tail, not by a smooth hour-of-day pattern; book is null for all six metrics (q >= 0.996). The 08:30-09:30 CI for slip_next by hour (-0.02..4.12) includes zero; by session label 'pre' it is 0.19..4.30. Dollar bound per flagged trade values: KB +303, PE +152, MV +71, PB +116, SM -639, HM -226.

## CORRECTION DIS_K (Z2, 2026-11-04T23:35Z): the DIS-K simulation ignored the time stops - rerun, conclusion unchanged
Found while building DIS-BG: my lib `dish_lib.DH.sim_raw` (used by DIS-K) did not apply the `tstop_s` column (flat 16:55 only); DIS-K lists carry tstop 3,600 s (G1) / 1,800 s (G2). Fixed (time stop = min(flat, signal + 1 s + tstop)); DIS-H, P3, Q7, DIS-AZ lists have no time stop and are not affected; ZL-2's own DIS-T / ranked-list runs apply tstop in their harness. DIS-K rerun with the fix (336 book cells, same prereg, same 120 worlds / 3 placebos; ledger program DIS_K_R2, rows autopilot/FADE_ROWS_DISK2.md; v1 files kept in /mnt/l2/l2vast/ds3_zones3_new/Z2_disk/v1_no_tstop/): still 0 LEAD; 322 NULL, 9 tolerant but sample short, 5 best-of-F. The best cell BO COMP_HI nyam G1: L6M +905 / HOLD +644 / PRE +91 (v1 +882 / +785 / +154), MDE L6M 1,875, placebo p_state 0.10 / side 0.04 / shifted time 0.07, family p_max 0.31 (v1 0.46; world-max median $793, 95th pct $1,404), PA9 min HOLD Calmar -0.00 not positive, stack Calmar gain -0.00; G2 cell is now NULL (not tolerant); RTH-pooled G1 +896 / +636. Others: CLOSE_TOP nyam WITH G1 best-of-F (L6M +35, HOLD -81), ORC_LO against G2 best-of-F (L6M +224). Overlays unchanged (+7,924 VOV_HI x1.5, p_max 0.54). Label stays best-of-F (Shadow-watch only); the 282 trade list sent to ZL-2 (DISK_comp_hi_trades.csv) has the same signal seconds in v1 and v2 (checked).

## DIS-BH (BASE-4, 2026-11-04T23:02Z): OPERATING CHARACTERISTICS OF THE SHADOW VERDICT RULES - full page autopilot/SHADOW_OC.md; scope DISBH_scope.md sha256 f05c6b92579b9bd689c8967fb2869b5144011b9b8fbec531a5cb63a996184c75; ledger DIS_BH; no PASS, nothing live
Per-line SPRT (alpha=beta=.10, H1 = half the 2026 research mean) needs 336-1009 trades = 223-1005 weeks at the observed rates for the five SHADOW-2 lines: no line decides within 2 years (P(CONSISTENT by wk104) <= 0.18 at the design truth); pooling the five lines decides in ~58 weeks; the weekly z test of the fade/NYAM runners inflates false CONTRADICTED; Monday table handles no-data/EARLY correctly but is not latched and its week index lags quiet fortnights.

Correction (BASE-4, 2026-11-04T23:02Z) to the DIS-BH lines: 'no line decides within 2 years' should read 'four of the five SHADOW-2 lines cannot decide within two years; DIS-K reaches CONSISTENT on 18% of paths by week 104 at the design truth (63% if the 2026 mean is true)'. Page autopilot/SHADOW_OC.md carries the corrected wording.

## DIS-W (ZL-1, 2026-11-05) - history extension memo and $0 2013-2023 out-of-sample: see autopilot/DS3_HISTORY_EXTENSION.md (prereg DISW sha256 4fbef5bd14e95c64a78d0b4507e7641ff170f6d6216d59b21ed1a9a5a4c74fe9). Plain sentence: on 10 years of owned 1-minute NQ no 2026 watch line replicates out of sample (Q13 -2.1, DIS-B -1.3, DIS-C -3.6 pt per trade; DIS-K and the live fade lines are null or negative), the 2026 regime has no earlier twin in 13.8 years (about one per decade), and no purchase is needed.

## DIS-BM (ZL-1, 2026-11-05) - pre-2023 OOS of the remaining watch lines, raw and percent frames: see autopilot/DS3_OOS_REMAINING.md (prereg DISBM sha256 49997bf430c25280756e4c04dbf7695d5a0249c4051369d98bfc2f3f1737f5f1). Plain sentence: none of the remaining 2026 watch lines (Z1 swing -6.0, G1 NQ-ES -3.1, DIS-Q 15:00 -1.8, DIS-Q 15:50 -2.4 pt per trade) earns anything before 2023, and the percent-frame re-run of the ten DIS-W lines changes no verdict; no line REPLICATES.


# DS3_DISCOVER2 - section S4b: DIS-BO hour- and volatility-dependent stop cost on the Q1-A ts2 stack (registered as DIS-BO; the claim line called DIS-BG) - interim 1, 2026-11-04 23:13Z
Prereg autopilot/DIS_BO_PREREG.md (sha256 e9254578a7ff0c14c3d24d5c91a7bc2e2ee50519eed02a840914cdb0c1d6f77b in DECISIONS.md, before any statistic); n_tested 28 (DISBO_NTESTED.md); code l2vast/ds3/code/disc/bo_build.py, bo_an.py; data /mnt/l2/l2vast/ds3_dr/bo_*.pkl. Measurement only, Shadow, no PASS claims. **BASE: the CURRENT Q1-A ts2 reference (tie-out: sum of per-trade net = $2,520,149.07 over 21,397 trades, exact). Every number below is on this base; it will be re-stated on ZL-2's live-window base (DIS-BJ, DS3_LIVE_WINDOWS_BASE.md) when that lands.** Cites DS3_TAIL_STRESS s4 (Z3), DIS-BF (S4b, above) and DS3_TH_COST.md (CAL).
## What the stack's stop exits are
Of 21,397 stack trades, only 767 end on the base stop (final exit = base exit of type 0; mean -$1,993 per trade), 8,305 on the target (+$2,494), 12,205 on a time / flat exit (-$1,352), and 120 on a TH-L2 cut or injected exit (not re-costed: their cost frame is the 0.80 pt/lot cut, DS3_TH_COST). So the stop-cost assumption touches 3.6% of the stack's trades. Contracts per trade from H.lots (mean 7.2 lots-equivalent at risk scale, 1-7 contracts).
## Re-costing results (cost_new = 2.45 + hour/volatility shape - pooled mean 0.147; delta = -contracts x $20 x change in cost; negative = the stack earns less)
| variant | book | stop exits | total delta $ (2023-26) | % of book | d $/wk L1M (MDE) | d $/wk L3M (MDE) | d $/wk L6M (MDE) | d $/wk HOLD (MDE) | d $/wk MID (MDE) | d $/wk PRE (MDE) | d $/wk X' (MDE) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| V1 | STACK | 767 | -5000 | -0.20 | -42 (nan) | -27 (52) | -11 (27) | +2 (23) | +29 (54) | -64 (75) | -13 (60) |
| V1 | KB | 65 | -722 | -0.31 | +1 (nan) | +0 (2) | -0 (4) | -2 (6) | -6 (23) | -6 (9) | -4 (14) |
| V1 | PE | 130 | -1469 | -0.10 | -32 (nan) | -24 (46) | -11 (23) | +0 (19) | +24 (39) | -28 (42) | +5 (34) |
| V1 | SM | 26 | -1210 | -0.36 | +0 (nan) | +0 (0) | +0 (1) | +0 (1) | +2 (4) | -14 (22) | -5 (26) |
| V1 | HM | 33 | +7 | 0.00 | +1 (nan) | +0 (2) | +0 (1) | -0 (1) | -0 (1) | +1 (1)* | -1 (13) |
| V1 | MV | 39 | -1364 | 9.54 | -16 (nan) | -9 (14) | -6 (8) | -2 (5) | +0 (2) | -15 (16) | -4 (12) |
| V1 | PB | 474 | -243 | -0.23 | +3 (nan) | +5 (3)* | +5 (2)* | +5 (6) | +10 (9)* | -1 (9) | -4 (11) |
| V2 | STACK | 767 | -6035 [p5 -19969, p95 +6188] | -0.24 | -53 (nan) | -20 (65) | -11 (34) | +2 (26) | +29 (46) | -70 (85) | -16 (62) |
| V2 | KB | 65 | -1022 [p5 -3881, p95 +1390] | -0.44 | +2 (nan) | +0 (3) | -0 (4) | -2 (5) | -5 (17) | -8 (13) | -7 (20) |
| V2 | PE | 130 | -1907 [p5 -14485, p95 +8997] | -0.13 | -57 (nan) | -18 (63) | -8 (30) | -1 (21) | +12 (24) | -29 (46) | +1 (31) |
| V2 | SM | 26 | -1331 [p5 -7453, p95 +3744] | -0.40 | +0 (nan) | +0 (0) | -0 (0) | +1 (3) | +6 (15) | -16 (29) | -2 (23) |
| V2 | HM | 33 | +50 [p5 -1993, p95 +1727] | 0.01 | +2 (nan) | +1 (2) | +0 (1) | +0 (1) | +1 (2) | +1 (1) | -0 (16) |
| V2 | MV | 39 | -1357 [p5 -5202, p95 +1560] | 9.50 | -3 (nan) | -4 (8) | -5 (9) | -1 (6) | +3 (7) | -16 (17) | -4 (12) |
| V2 | PB | 474 | -468 [p5 -3134, p95 +1950] | -0.45 | +4 (nan) | +1 (7) | +3 (6) | +5 (7) | +12 (15) | -2 (10) | -4 (13) |
| V3 | STACK | 767 | -7405 | -0.29 | -50 (nan) | -35 (54) | -20 (28) | -20 (20)* | -21 (49) | -50 (37)* | -38 (36)* |
| V3 | KB | 65 | -582 | -0.25 | +0 (nan) | +0 (0) | -2 (4) | -2 (3) | -3 (10) | -4 (5) | -5 (7) |
| V3 | PE | 130 | -3578 | -0.24 | -33 (nan) | -26 (49) | -12 (24) | -13 (16) | -14 (39) | -26 (24)* | -16 (24) |
| V3 | SM | 26 | -1373 | -0.41 | +0 (nan) | +0 (0) | +0 (0) | +0 (0) | +0 (0) | -10 (11) | -8 (15) |
| V3 | HM | 33 | -166 | -0.04 | +0 (nan) | +0 (0) | +0 (0) | +0 (0) | +0 (0) | +0 (0) | -4 (7) |
| V3 | MV | 39 | -957 | 6.69 | -17 (nan) | -10 (14) | -6 (8) | -4 (5) | +0 (0) | -7 (7)* | -2 (5) |
| V3 | PB | 474 | -749 | -0.72 | +0 (nan) | +0 (0) | +0 (0) | -2 (3) | -3 (10) | -4 (5) | -4 (5) |
(* = |delta| above the paired 2.8-SE MDE; V2 interval = 5th..95th percentile of 200 empirical draws.)
## Release hour (08:30-09:30 ET) stop exits and the entry-session split
81 of the 767 stop exits fall in 08:30-09:30 ET and they lose $219,186 in total (mean -$2,706 per exit, 14% of all stop-exit losses). **All 81 were entered before 08:30: 39 in the Asia session (entry 18:00-02:00 ET) and 42 in London; none entered inside the release hour** (the live book entry windows therefore do not matter for them; the 09:00-09:59 block was removed on 2026-10-20 per REPORT_0900_ENTRIES.md update, and the split makes the result independent of it). By book the release-hour stop exits are HM 2, KB 12, MV 17, PB 18, PE 19, SM 13 (of 33 / 65 / 39 / 474 / 130 / 26 stop exits). TH-L2 cut or injected exits in the release hour: 5 of 120, so cuts do not shield the release hour (cut cost 0.80 pt, DS3_TH_COST, untouched here).
**Plain sentence:** re-costing the 767 stop exits of the live stack with the measured hour and volatility dependence of stop slippage changes the 2023-26 total by -$5.0k (V1), -$6.0k (V2, 5-95% range in the table) or -$7.4k (V3, the upper bound putting the whole 2.08 pt release-hour excess on every release-hour stop), i.e. -0.2% to -0.3% of the $2.52M, or -$11 to -$20 per week in L6M; every window delta is inside its MDE except V3 in the PRE window (-$51/wk vs MDE $37, a $51 per week effect). The release hour hurts mostly the overnight holds: all 81 release-hour stop exits are Asia / London trades carried into the 08:30 release, and they are the stack's most expensive stop exits (average -$2.7k each). The stop-cost assumption is not what decides the stack's P&L: the 2.45 pt flat cost is adequate on average, and the real exposure is carrying Asia / London positions through the 08:30 release, which a cost model does not remove.
DIS-BO clarification (S4b): 'mean 7.2 lots-equivalent at risk scale' above refers to the engine's internal R['lots'] risk-scale field, which is NOT contracts; contracts per trade are H.lots(None) = 1, 2, 4 or 7 (12,305 / 3,974 / 3,436 / 1,682 trades) and are what the delta uses.

CLOCK-AUDIT (S4b, ZL-2 request): scripts checked for path-INDEX arithmetic used as time. DIS-BP flatten times: epoch based (bp_lib.epoch_et + searchsorted(SS, epoch)); verified before reading results: the injected indices map to 08:15:00 / 08:25:00 / 08:29:00 ET (99.2-99.6%% within 5 s of the target, first print at/after the clock time; 926-927 flatten seconds); 'rows flattened' uses index ORDER only (kin < flatten index < base exit index). DIS-BO: exit and entry seconds are SS[tx] / SS[te] epochs; the 08:30 carried test is epoch arithmetic. DIS-AU: SS[kin] / SS[kflat] epochs; hold in epoch minutes. DIS-R, DIS-L, DIS-E, DIS-C, T-FADE, patched minute table: built on the minute table (epoch ts, searchsorted on SS for flow) and 1-s tables (ts in ns), no index arithmetic as time; DIS-C bar offsets are guarded by an explicit timestamp equality check. DIS-BF: the ONLY index-arithmetic item: slip_next, t_rev1 and t_next_rest use the NEXT PATH INDEX (k + 1) = the next second with a print, exactly as in Z3's slip_tape.py, not a strict +1 s. Measured: the next-index gap is exactly 1 s for 95.6%% of stop exits and 96.5%% of target exits, <= 2 s for 98.8%%, > 5 s for 0.13%%, max 12 s; the gap exceeds 1 s in 9-12%% of overnight (00:00-02:59 and 19:00 / 23:00 hours) stops but only 0.3%% of the 09:00-09:59 stops. Stop exits with gap > 1 s have mean slip_next 1.51 pt (n 575) versus 0.08 pt when the gap is 1 s, so the overnight slip_next means are slightly overstated against a strict +1 s clock and the release-hour (08:30-09:30) figures (mean 2.23 pt) are almost unaffected; the Z3 reproduction (which uses the same index) is exact by construction. No numbers are changed; the reading is a mild upward bias on thin-hour slip_next, not on the release hour.

## DIS-BS (ZL-1, 2026-11-05) - T-INSTR YM U7 NY-PM pocket and BTC K7 London pre-2023: see autopilot/DS3_INSTR_OOS.md (prereg DISBS sha256 b5da27dc66c9979ddbd094c0bea5b544d41e2c49ed62ee5dcaf876596b794eb1). Plain sentence: the YM NY-PM Supertrend pocket is negative before 2023 (-0.05 R per trade over 872 trades, 0 of 181 neighbourhood cells replicate) and BTC K7 London has only 10 months of owned pre-2023 history (no information).


# DS3_DISCOVER2 - section S4b: DIS-BP pre-release flatten overlay on carried Asia / London positions - interim 1, 2026-11-04 23:57Z
Prereg autopilot/DIS_BP_PREREG.md (sha256 8452fc7c9c085b9e29d9f06d5a59c78246d1a6ff03c56c77da4b5695896b125f in DECISIONS.md, before any statistic; the family of 16 cells and the placebo design were fixed there); n_tested 16 (DISBP_NTESTED.md); code l2vast/ds3/code/disc/bp_lib.py, bp_run.py, bp_an.py, bp_sens.py; data /mnt/l2/l2vast/ds3_dr/bp_*.pkl. Shadow only, no PASS claims. **BASE: the CURRENT Q1-A ts2 reference (2,520,149.07); to be re-stated on the live-window base (DIS-BJ/BR) when it lands.** Flatten = d7_v13t.inject kind 'time', all lots, market exit at the path price of the flatten second, 0.80 pt/lot; flatten seconds verified to be exactly 08:15 / 08:25 / 08:29 ET (clock audit above). Selection charged: the 81 release-hour stop exits of DIS-BO were found after seeing the loss, so the family is 12 flatten cells + 4 event-clock controls (09:55 / 13:55) and the null is random flatten times on the same day set (100 draws per set, 100 family worlds x 16 cells).
## Drawdown first, then means (delta vs the unmodified stack; $ and $/wk)
| flatten ET | day set | positions flattened (rows) | total delta $ | d$/wk L3M | L6M (MDE) | HOLD | PRE | X' | d maxDD L6M / HOLD / PRE / X' ($) | worst day / week delta | cell p vs random times (L6M) | q | placebo p random / shifted days (L6M) | PA9 maxDD L6M/HOLD/PRE | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 08:15 | ALL | 3192 | -182092 | +483 | -893 |  (4182) | -575 | -1142 | -1053 | +22394 / +10301 / -1465 / +22469 | -611 / -8827 | 0.63 | 0.68 | 0.51 / - | -0.05 / -0.14 / -0.05 | fails |
| 08:15 | CAL08 | 1187 | -2875 | +1232 | +165 |  (1554) | +195 | +536 | -1479 | -7175 / -1236 / -9750 / +18217 | -611 / -1417 | 0.08 | 0.41 | 0.09 / - | -0.01 / +0.00 / +0.03 | TOLERANT |
| 08:15 | VER | 306 | -22945 | -115 | -174 |  (545) | +82 | -444 | -123 | +2845 / -899 / -6868 / +2946 | +0 / +0 | 0.26 | 0.41 | 0.26 / - | -0.00 / +0.01 / +0.05 | fails |
| 08:20 | ALL | 3153 | -158489 | +891 | -675 |  (4479) | -626 | -1007 | -718 | +22425 / +11777 / -5545 / +8831 | +633 / -9011 | 0.49 | 0.55 | 0.47 / - | +0.02 / -0.13 / -0.01 | fails |
| 08:20 | CAL08 | 1165 | +27427 | +1236 | -265 |  (1886) | -73 | +723 | -1078 | -1602 / +1339 / -13045 / +6059 | +0 / -458 | 0.22 | 0.41 | 0.22 / - | +0.00 / -0.00 / +0.06 | fails |
| 08:20 | VER | 311 | -25920 | -32 | -253 |  (765) | +5 | -465 | -20 | +1679 / +258 / -6798 / -5745 | +0 / +0 | 0.34 | 0.41 | 0.35 / - | +0.00 / -0.00 / +0.06 | fails |
| 08:25 | ALL | 3160 | -146417 | +1207 | +335 |  (3753) | -661 | -836 | -508 | +12938 / -1651 / -8114 / +17407 | +473 / -6567 | 0.30 | 0.41 | 0.25 / - | +0.20 / -0.04 / -0.04 | NOW-ONLY |
| 08:25 | CAL08 | 1159 | +36030 | +1330 | +345 |  (1871) | +217 | +839 | -1222 | +957 / -2286 / -12113 / +15671 | +0 / -305 | 0.02 | 0.32 | 0.07 / 0.34 | +0.01 / +0.01 / +0.05 | TOLERANT |
| 08:25 | VER | 300 | -38494 | +274 | -74 |  (889) | +65 | -490 | -267 | +2653 / +0 / -6536 / +5412 | +0 / +0 | 0.21 | 0.41 | 0.18 / 0.67 | +0.00 / +0.00 / +0.05 | fails |
| 08:29 | ALL | 3180 | -180099 | +2277 | +381 |  (4046) | -1097 | -687 | -1070 | +14612 / +10142 / -10281 / +14190 | +473 / -6620 | 0.18 | 0.41 | 0.25 / - | +0.17 / -0.14 / +0.04 | NOW-ONLY |
| 08:29 | CAL08 | 1155 | +52609 | +1727 | +319 |  (1822) | +144 | +1038 | -1139 | -4311 / -3620 / -21951 / +14737 | +0 / -2662 | 0.06 | 0.41 | 0.07 / - | -0.03 / +0.02 / +0.17 | TOLERANT |
| 08:29 | VER | 301 | -11188 | +916 | +89 |  (1207) | +102 | -260 | -63 | -2180 / +0 / -6703 / +2905 | +0 / +0 | 0.11 | 0.41 | 0.08 / - | +0.00 / +0.00 / +0.12 | TOLERANT |
| 09:55 | ALL | 1447 | -13341 | +518 | +324 |  (580) | +26 | +332 | -859 | -4769 / +963 / +3485 / +18180 | +0 / +363 | 0.31 | 0.41 | 0.25 / - | +0.04 / -0.01 / +0.09 | NOW-ONLY |
| 09:55 | ISM | 136 | -5313 | +0 | +0 |  (0) | -79 | -102 | +191 | +0 / +0 / -278 / +3522 | +0 / +0 | 0.72 | 0.72 | - / - | +0.00 / +0.00 / +0.00 | fails |
| 13:55 | ALL | 2070 | -78932 | -220 | +210 |  (717) | -27 | -294 | -634 | +2543 / -2302 / +3466 / +10187 | +0 / +1196 | 0.28 | 0.41 | 0.26 / - | +0.05 / -0.01 / -0.04 | fails |
| 13:55 | FOMC | 74 | -2794 | +99 | +108 |  (149) | +70 | +139 | -369 | -560 / +0 / +0 / +0 | +0 / +254 | 0.28 | 0.41 | - / - | +0.01 / +0.00 / +0.00 | TOLERANT |

(MDE = 2.8 SE paired of the L6M weekly delta; maxDD deltas negative = better; HOLD / PRE / X' drawdown windows with the corrected carrying weeks as in DIS-P.)
## Symmetric cost: what is given up
ALL days: flattening every day's carried positions at 08:25 changes 1,770 trades, forfeits $1.857M of gains on 822 winners and avoids $1.695M of losses on 948 losers, net -$146k (the family cell list shows the same -$146k to -$182k for 08:15-08:29 on all days): the carried Asia / London positions are net winners through the release on average and a blanket flatten is costly. CAL08 days (342 days with any 08:30 release): 08:25 changes 653 trades, forfeits $683k on 310 winners and saves $696k on 343 losers, net +$14k on the trade list and +$36.0k in the engine (locks, caps and re-entries: taken trades 21,417 vs 21,397, i.e. 20 more because freed slots are reused by the engine's own next signals); VER (CPI + NFP only, 84 days): 163 trades, -$211k / +$179k, net -$38k. The release-hour 'bad stops' are the 81 losers inside a population of 12,000 held positions whose gains and losses through the hour nearly cancel.
Flatten exit cost sensitivity (+1.0 pt extra on the market exit, xcost 1.80): 08:25 CAL08 total +$36.0k -> +$3.8k (L6M +345 -> +271/wk, HOLD +217 -> +111, PRE +839 -> +665); 08:29 CAL08 +$52.6k -> +$21.0k; 08:29 VER -$11.2k -> -$19.4k.
## Tests
- TOLERANT cells: 08:15 CAL08, 08:25 CAL08, 08:29 CAL08, 08:29 VER and 13:55 FOMC (74 rows, thin); NOW-ONLY: also 08:25 ALL, 08:29 ALL and 09:55 ALL (they fail the HOLD / PRE gates, and all-days flattens cost $146-182k in total).
- Family max-T (100 worlds, random flatten times on the same day sets, all 16 cells): best observed L6M delta +$381/wk is exceeded in 91% of worlds (p 0.911); best HOLD +$217/wk p 0.990. Cell-level p vs random times (L6M): 08:25 CAL08 0.02, 08:29 CAL08 0.06, 08:15 CAL08 0.08; BH q 0.32-0.41. Placebo (random times on the same day set): 08:25 CAL08 p 0.07, 08:29 CAL08 0.07; shifted-event-days placebo for 08:25 CAL08 p 0.34 (VER 0.67): an equal-count shift of the release days into other weeks does about as well, so the gain is not release-specific. PA9 of the maxDD cut for the tolerant CAL08 cells is +0.01 / +0.01 / +0.05 (L6M / HOLD / PRE): the drawdown improvements in HOLD (-$2.3k) and PRE (-$12.1k) are not tied to the week key. Every L6M delta is inside its MDE (+345 vs 1,871 for 08:25 CAL08). The X' window (2023) loses -$1.2k/wk for the CAL08 cells (inside half its MDE).
- Event-clock controls: 09:55 ALL is NOW-ONLY (+324 L6M, +26 HOLD, +332 PRE) with total -$13k; 13:55 ALL and 09:55 ISM fail; 13:55 FOMC has 74 flattened rows (+108 L6M) and is thin.
**Plain sentence:** a flatten of carried Asia / London positions before the 08:30 releases does not survive the selection charge: on release-calendar days it gives back $0.7M of gains to save $0.7M of losses (net +$14k on trades, +$36k in the engine at 0.80 pt/lot, +$4k at 1.80 pt/lot), the best cell is exceeded by random flatten times in 91% of family worlds, a shifted release calendar does about as well (p 0.34), and verified CPI / NFP days alone lose money (-$38k); the all-days version costs $146-182k. The improvement in HOLD / PRE drawdown for the calendar-day cells (-$2.3k / -$12.1k at 08:25) is real in the sample but has PA9 about 0.01-0.05 and does not pass the family test. Not a lead; label best-of-F WATCH at most for 08:25-08:29 CAL08 (REGIME in X').
DIS-BP table note (S4b): in the table above each L6M cell is followed by an extra column that carries only the L6M MDE in parentheses (the header lists 'L6M (MDE)'; the columns after it are shifted by one against the header: read the sequence as L3M, L6M, [MDE], HOLD, PRE, X', then the maxDD deltas L6M / HOLD / PRE / X', then worst day / worst week). **Drawdown in the 2023 window X' gets worse for the CAL08 flatten cells: stack maxDD +$18.2k (08:15), +$15.7k (08:25), +$14.7k (08:29) in X' while HOLD / PRE / L6M maxDD improve (08:25 CAL08: L6M +$1.0k worse, HOLD -$2.3k, PRE -$12.1k, X' +$15.7k worse).** The X' mean delta is -$1.1k to -$1.5k per week. So the HOLD / PRE drawdown gain is paid in the 2023 regime: label REGIME for the CAL08 cells; the 'TOLERANT' label above rests on X' being within half its MDE for the mean and does not test the X' maxDD in the gate (the prereg gate tests maxDD only in HOLD and PRE).
