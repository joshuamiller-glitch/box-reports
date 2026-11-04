
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
| sample | instrument | predictor | target | rho (or rate difference) | p | n | MDE (rho at 80%% power) / rates |
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

## DIS-B: GLOBEX PRE-MARKET STRUCTURE BOOKS (S4a; interim table 2026-11-04 20:37Z; prereg autopilot/DIS_B_PREREG.md sha256 f8cf86b8...c4563; ledger DIS_B; rows FADE_ROWS_DISB.md)
Question: do the Globex pre-market (04:00-09:30 ET) range / volume / VWAP / 08:30-release / pre-open structures trade as books, either with entries after 09:30 (N family, session nyam) or as pre-market entries (P family, flat by 09:25)? 61 event variants x shapes = 1341 cells valued (1338 with >= 100 trades); FadeHarness live fill model, costs stop 2.45 / exit 0.80 / fee 0.242, base Q1-A ts2 stack for marginal values. Post-hoc, Shadow only, no PASS claims.
Stage 1: share of cells with L6M > 0 = 0.39, HOLD > 0 = 0.30, both L3M, L6M and HOLD > 0: 157 cells (140 N family, 17 P family). Placebo p <= 0.10: 14 of 157. Family max-T test over all 1338 cells: HOLD_mean: family p of the real max side 0.406 / days 0.168.
Ranked table (placebo p, then L6M; first 25 of 157; labels per FADE_ROWS rules, nothing here is a lead until the family test and the carrying-week checks are read):

| book | session | anchor | trigger | shape | L1M | L3M | L6M | HOLD | MID | PRE | X' | regime-conditioned | placebo | stack gain | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=mid stop=1.00ATR T60m | +73 | +322 | +1404 | +1207 | +195 | +144 | -550 | ON L6M +1404 / HOLD +993 / MID +195 (n 156); 2023-25 same switch PRE -120 / X' -507 (n 91) | p 0.010 | 0.5x HOLD +0.025 / L6M +0.002; 1.0x HOLD +0.056 / L6M +0.003 | TOLERANT REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=mid stop=1.00ATR T120m | +73 | +322 | +1275 | +1165 | +305 | +216 | -550 | ON L6M +1275 / HOLD +951 / MID +305 (n 156); 2023-25 same switch PRE -127 / X' -507 (n 91) | p 0.010 | 0.5x HOLD +0.026 / L6M +0.002; 1.0x HOLD +0.056 / L6M +0.003 | TOLERANT REGIME [family maxT p 1.00] |
| DIS_B trend | pre | REL | P_REL_cont_m1.0 | tgt=r1 stop=1.00ATR T30m | +367 | +911 | +410 | +707 | +850 | +298 | +517 | ON L6M +410 / HOLD +515 / MID +850 (n 188); 2023-25 same switch PRE +265 / X' +289 (n 116) | p 0.059 | 0.5x HOLD +0.008 / L6M +0.014; 1.0x HOLD +0.016 / L6M +0.028 | TOLERANT CONDITIONAL [family maxT p 1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_hi | tgt=mid stop=1.00ATR T60m | -890 | +108 | +581 | +1168 | +825 | -151 | -690 | ON L6M +581 / HOLD +997 / MID +825 (n 122); 2023-25 same switch PRE -85 / X' -373 (n 61) | p 0.069 | 0.5x HOLD +0.031 / L6M -0.021; 1.0x HOLD +0.070 / L6M -0.041 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_hi | tgt=mid stop=1.00ATR T120m | -890 | +108 | +452 | +1101 | +825 | -80 | -690 | ON L6M +452 / HOLD +930 / MID +825 (n 122); 2023-25 same switch PRE -91 / X' -373 (n 61) | p 0.069 | 0.5x HOLD +0.031 / L6M -0.021; 1.0x HOLD +0.070 / L6M -0.041 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B trend | pre | REL | P_REL_cont_m1.0 | tgt=r2 stop=1.00ATR T30m | +12 | +935 | +284 | +663 | +801 | +197 | -82 | ON L6M +284 / HOLD +442 / MID +801 (n 188); 2023-25 same switch PRE +332 / X' +46 (n 116) | p 0.069 | 0.5x HOLD +0.009 / L6M -0.016; 1.0x HOLD +0.019 / L6M -0.032 | TOLERANT CONDITIONAL [family maxT p 1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T120m | -1353 | +516 | +1310 | +1853 | +576 | +266 | -416 | ON L6M +1310 / HOLD +1477 / MID +576 (n 96); 2023-25 same switch PRE -356 / X' -343 (n 53) | p 0.089 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.052 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T120m | +2794 | +3342 | +2328 | +1314 | +233 | -363 | -694 | ON L6M +2328 / HOLD +1409 / MID +233 (n 270); 2023-25 same switch PRE +52 / X' -1069 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T30m | +2794 | +3342 | +2328 | +1274 | +233 | -400 | -686 | ON L6M +2328 / HOLD +1369 / MID +233 (n 270); 2023-25 same switch PRE +67 / X' -958 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T60m | +2794 | +3342 | +2328 | +1302 | +233 | -363 | -694 | ON L6M +2328 / HOLD +1396 / MID +233 (n 270); 2023-25 same switch PRE +52 / X' -1069 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T30m | -1353 | +516 | +1510 | +1845 | +93 | +201 | -416 | ON L6M +1510 / HOLD +1469 / MID +93 (n 96); 2023-25 same switch PRE -380 / X' -343 (n 53) | p 0.099 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.051 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T60m | -1353 | +516 | +1465 | +1896 | +415 | +255 | -416 | ON L6M +1465 / HOLD +1520 / MID +415 (n 96); 2023-25 same switch PRE -356 / X' -343 (n 53) | p 0.099 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.052 / L6M -0.001 | NOW-ONLY REGIME [family maxT p 0.97] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_hi | tgt=mid stop=1.00ATR T60m | -890 | +108 | +489 | +1066 | +825 | -220 | -632 | ON L6M +489 / HOLD +895 / MID +825 (n 126); 2023-25 same switch PRE -159 / X' -373 (n 63) | p 0.099 | 0.5x HOLD +0.031 / L6M -0.022; 1.0x HOLD +0.068 / L6M -0.043 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_hi | tgt=mid stop=1.00ATR T120m | -890 | +108 | +360 | +999 | +825 | -149 | -632 | ON L6M +360 / HOLD +828 / MID +825 (n 126); 2023-25 same switch PRE -165 / X' -373 (n 63) | p 0.099 | 0.5x HOLD +0.031 / L6M -0.022; 1.0x HOLD +0.068 / L6M -0.043 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_any | tgt=mid stop=0.25ATR T30m | -2555 | +156 | +1319 | +1088 | -1228 | +378 | -881 | ON L6M +1319 / HOLD +900 / MID -1228 (n 245); 2023-25 same switch PRE -197 / X' -486 (n 136) | p 0.109 | 0.5x HOLD +0.022 / L6M -0.033; 1.0x HOLD +0.047 / L6M -0.062 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T60m | +555 | +205 | +637 | +657 | +1439 | -902 | -399 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -259 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T30m | +555 | +205 | +637 | +657 | +1439 | -902 | -439 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -283 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T120m | +555 | +205 | +637 | +657 | +1439 | -902 | -399 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -259 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T60m | +197 | +67 | +475 | +539 | +1439 | -670 | -304 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -213 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T120m | +197 | +67 | +475 | +539 | +1439 | -670 | -304 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -213 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T30m | +197 | +67 | +475 | +539 | +1439 | -670 | -344 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -237 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T30m | -1353 | +278 | +1330 | +1597 | +190 | +308 | -312 | ON L6M +1330 / HOLD +1306 / MID +190 (n 93); 2023-25 same switch PRE -262 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.024 / L6M -0.001; 1.0x HOLD +0.052 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T60m | -1353 | +278 | +1285 | +1648 | +512 | +259 | -312 | ON L6M +1285 / HOLD +1356 / MID +512 (n 93); 2023-25 same switch PRE -340 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.024 / L6M -0.001; 1.0x HOLD +0.053 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T120m | -1353 | +278 | +1131 | +1591 | +611 | +259 | -312 | ON L6M +1131 / HOLD +1299 / MID +611 (n 93); 2023-25 same switch PRE -340 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.025 / L6M -0.001; 1.0x HOLD +0.053 / L6M -0.003 | TOLERANT REGIME [family maxT p 1.00] |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_any | tgt=mid stop=0.25ATR T30m | -2555 | +156 | +1337 | +1031 | -1228 | +162 | -933 | ON L6M +1337 / HOLD +842 / MID -1228 (n 255); 2023-25 same switch PRE -261 / X' -486 (n 143) | p 0.129 | 0.5x HOLD +0.021 / L6M -0.033; 1.0x HOLD +0.046 / L6M -0.062 | NOW-ONLY REGIME [family maxT p 1.00] |

Reading (S4a, interim; post-hoc, Shadow only):
- **P_REL_cont_m1.0 (08:30 release continuation, entry at the 08:35 close, flat by 09:25; the only cell positive in every window L1M..X')**: tgt R1, stop 1.0 ATR, time 30 min: 379 trades, +$67k total over the sample, mean $177 per trade at about 4.7 lots; the profit is SHORT-ONLY (shorts +$64.6k, longs +$2.5k), 2025 is negative (-$17k), non-event days +$56.7k vs event days +$10.4k, and its neighbours are NOT positive (stop 0.5 ATR -$11k, R2 +$12.8k, stop 0.25 ATR/60 min -$2.7k, R2/0.5 ATR -$23.5k; release threshold 0.5 ATR: +$47.9k only at the same shape, other shapes negative). Label: FRAGILE (single-shape spike, one side), not a lead.
- **N_REL_rev_m0.5 (NY-AM reversal of the 08:30 release move, entry 09:31, target = PM mid)**: placebo p .01 (best in the family). It is a plateau along the 'mid' target shapes (stop 0.25 / 0.5 / 1.0 ATR, 60 min: +$101k / +$78k / +$41k, 313 / 321 / 304 trades; the R1 targets of the same trades are negative), but the years alternate (2023 -$34k, 2024 +$68k, 2025 -$34k, 2026 +$41k) and the profit sits on non-event days (+$47.5k vs -$6.3k on event days). Label: REGIME / year-alternating until the family test is read.
- Release-move reversals at 08:35 (P_REL_rev) lose in every shape (-$80k..-$221k): the pre-market release move continues or noise, it does not mean-revert before 09:25.
- **Family test, HOLD mean (all 1,338 cells with >= 100 trades, 100 worlds, random-side and shuffled-day nulls):** family p of the real max 0.41 (side) / 0.17 (days). The best cell, N_REL_rev_m0.5 mid / 0.25 ATR / 60 min (HOLD +$2,337 per week), has raw placebo p .01 but max-T p .41 and BH q .83; P_REL_cont_m1.0 (r1, 1.0, 30 min) has raw p .01, max-T p 1.0, q .83. Read: with 1,338 cells tried, the best pre-market book is what chance produces; no lead. L6M Calmar test running.


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
