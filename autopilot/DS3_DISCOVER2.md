
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

## DIS-B: GLOBEX PRE-MARKET STRUCTURE BOOKS (S4a; interim table 2026-11-04 19:28Z; prereg autopilot/DIS_B_PREREG.md sha256 f8cf86b8...c4563; ledger DIS_B; rows FADE_ROWS_DISB.md)
Question: do the Globex pre-market (04:00-09:30 ET) range / volume / VWAP / 08:30-release / pre-open structures trade as books, either with entries after 09:30 (N family, session nyam) or as pre-market entries (P family, flat by 09:25)? 61 event variants x shapes = 1341 cells valued (1338 with >= 100 trades); FadeHarness live fill model, costs stop 2.45 / exit 0.80 / fee 0.242, base Q1-A ts2 stack for marginal values. Post-hoc, Shadow only, no PASS claims.
Stage 1: share of cells with L6M > 0 = 0.39, HOLD > 0 = 0.30, both L3M, L6M and HOLD > 0: 157 cells (140 N family, 17 P family). Placebo p <= 0.10: 14 of 157. Family max-T test over all 1338 cells: pending.
Ranked table (placebo p, then L6M; first 25 of 157; labels per FADE_ROWS rules, nothing here is a lead until the family test and the carrying-week checks are read):

| book | session | anchor | trigger | shape | L1M | L3M | L6M | HOLD | MID | PRE | X' | regime-conditioned | placebo | stack gain | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=mid stop=1.00ATR T60m | +73 | +322 | +1404 | +1207 | +195 | +144 | -550 | ON L6M +1404 / HOLD +993 / MID +195 (n 156); 2023-25 same switch PRE -120 / X' -507 (n 91) | p 0.010 | 0.5x HOLD +0.025 / L6M +0.002; 1.0x HOLD +0.056 / L6M +0.003 | TOLERANT REGIME |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=mid stop=1.00ATR T120m | +73 | +322 | +1275 | +1165 | +305 | +216 | -550 | ON L6M +1275 / HOLD +951 / MID +305 (n 156); 2023-25 same switch PRE -127 / X' -507 (n 91) | p 0.010 | 0.5x HOLD +0.026 / L6M +0.002; 1.0x HOLD +0.056 / L6M +0.003 | TOLERANT REGIME |
| DIS_B trend | pre | REL | P_REL_cont_m1.0 | tgt=r1 stop=1.00ATR T30m | +367 | +911 | +410 | +707 | +850 | +298 | +517 | ON L6M +410 / HOLD +515 / MID +850 (n 188); 2023-25 same switch PRE +265 / X' +289 (n 116) | p 0.059 | 0.5x HOLD +0.008 / L6M +0.014; 1.0x HOLD +0.016 / L6M +0.028 | TOLERANT CONDITIONAL |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_hi | tgt=mid stop=1.00ATR T60m | -890 | +108 | +581 | +1168 | +825 | -151 | -690 | ON L6M +581 / HOLD +997 / MID +825 (n 122); 2023-25 same switch PRE -85 / X' -373 (n 61) | p 0.069 | 0.5x HOLD +0.031 / L6M -0.021; 1.0x HOLD +0.070 / L6M -0.041 | NOW-ONLY REGIME |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_hi | tgt=mid stop=1.00ATR T120m | -890 | +108 | +452 | +1101 | +825 | -80 | -690 | ON L6M +452 / HOLD +930 / MID +825 (n 122); 2023-25 same switch PRE -91 / X' -373 (n 61) | p 0.069 | 0.5x HOLD +0.031 / L6M -0.021; 1.0x HOLD +0.070 / L6M -0.041 | NOW-ONLY REGIME |
| DIS_B trend | pre | REL | P_REL_cont_m1.0 | tgt=r2 stop=1.00ATR T30m | +12 | +935 | +284 | +663 | +801 | +197 | -82 | ON L6M +284 / HOLD +442 / MID +801 (n 188); 2023-25 same switch PRE +332 / X' +46 (n 116) | p 0.069 | 0.5x HOLD +0.009 / L6M -0.016; 1.0x HOLD +0.019 / L6M -0.032 | TOLERANT CONDITIONAL |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T120m | -1353 | +516 | +1310 | +1853 | +576 | +266 | -416 | ON L6M +1310 / HOLD +1477 / MID +576 (n 96); 2023-25 same switch PRE -356 / X' -343 (n 53) | p 0.089 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.052 / L6M -0.001 | NOW-ONLY REGIME |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T120m | +2794 | +3342 | +2328 | +1314 | +233 | -363 | -694 | ON L6M +2328 / HOLD +1409 / MID +233 (n 270); 2023-25 same switch PRE +52 / X' -1069 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T30m | +2794 | +3342 | +2328 | +1274 | +233 | -400 | -686 | ON L6M +2328 / HOLD +1369 / MID +233 (n 270); 2023-25 same switch PRE +67 / X' -958 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME |
| DIS_B fade | nyam | REL | N_REL_rev_m0.5 | tgt=r1 stop=1.00ATR T60m | +2794 | +3342 | +2328 | +1302 | +233 | -363 | -694 | ON L6M +2328 / HOLD +1396 / MID +233 (n 270); 2023-25 same switch PRE +52 / X' -1069 (n 156) | p 0.099 | 0.5x HOLD +0.014 / L6M +0.009; 1.0x HOLD +0.030 / L6M +0.018 | NOW-ONLY REGIME |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T30m | -1353 | +516 | +1510 | +1845 | +93 | +201 | -416 | ON L6M +1510 / HOLD +1469 / MID +93 (n 96); 2023-25 same switch PRE -380 / X' -343 (n 53) | p 0.099 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.051 / L6M -0.001 | NOW-ONLY REGIME |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=mid stop=0.25ATR T60m | -1353 | +516 | +1465 | +1896 | +415 | +255 | -416 | ON L6M +1465 / HOLD +1520 / MID +415 (n 96); 2023-25 same switch PRE -356 / X' -343 (n 53) | p 0.099 | 0.5x HOLD +0.024 / L6M -0.000; 1.0x HOLD +0.052 / L6M -0.001 | NOW-ONLY REGIME |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_hi | tgt=mid stop=1.00ATR T60m | -890 | +108 | +489 | +1066 | +825 | -220 | -632 | ON L6M +489 / HOLD +895 / MID +825 (n 126); 2023-25 same switch PRE -159 / X' -373 (n 63) | p 0.099 | 0.5x HOLD +0.031 / L6M -0.022; 1.0x HOLD +0.068 / L6M -0.043 | NOW-ONLY REGIME |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_hi | tgt=mid stop=1.00ATR T120m | -890 | +108 | +360 | +999 | +825 | -149 | -632 | ON L6M +360 / HOLD +828 / MID +825 (n 126); 2023-25 same switch PRE -165 / X' -373 (n 63) | p 0.099 | 0.5x HOLD +0.031 / L6M -0.022; 1.0x HOLD +0.068 / L6M -0.043 | NOW-ONLY REGIME |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g1.0_any | tgt=mid stop=0.25ATR T30m | -2555 | +156 | +1319 | +1088 | -1228 | +378 | -881 | ON L6M +1319 / HOLD +900 / MID -1228 (n 245); 2023-25 same switch PRE -197 / X' -486 (n 136) | p 0.109 | 0.5x HOLD +0.022 / L6M -0.033; 1.0x HOLD +0.047 / L6M -0.062 | NOW-ONLY REGIME |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T60m | +555 | +205 | +637 | +657 | +1439 | -902 | -399 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -259 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T30m | +555 | +205 | +637 | +657 | +1439 | -902 | -439 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -283 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g1.0_lo | tgt=r1 stop=0.50ATR T120m | +555 | +205 | +637 | +657 | +1439 | -902 | -399 | ON L6M +637 / HOLD +686 / MID +1439 (n 192); 2023-25 same switch PRE -165 / X' -259 (n 121) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.004; 1.0x HOLD +0.015 / L6M -0.009 | NOW-ONLY REGIME |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T60m | +197 | +67 | +475 | +539 | +1439 | -670 | -304 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -213 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T120m | +197 | +67 | +475 | +539 | +1439 | -670 | -304 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -213 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME |
| DIS_B trend | nyam | GAPGO | N_GAPGO_t31_g0.5_lo | tgt=r1 stop=0.50ATR T30m | +197 | +67 | +475 | +539 | +1439 | -670 | -344 | ON L6M +475 / HOLD +567 / MID +1439 (n 205); 2023-25 same switch PRE -149 / X' -237 (n 132) | p 0.109 | 0.5x HOLD +0.007 / L6M -0.007; 1.0x HOLD +0.013 / L6M -0.013 | NOW-ONLY REGIME |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T30m | -1353 | +278 | +1330 | +1597 | +190 | +308 | -312 | ON L6M +1330 / HOLD +1306 / MID +190 (n 93); 2023-25 same switch PRE -262 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.024 / L6M -0.001; 1.0x HOLD +0.052 / L6M -0.003 | TOLERANT REGIME |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T60m | -1353 | +278 | +1285 | +1648 | +512 | +259 | -312 | ON L6M +1285 / HOLD +1356 / MID +512 (n 93); 2023-25 same switch PRE -340 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.024 / L6M -0.001; 1.0x HOLD +0.053 / L6M -0.003 | TOLERANT REGIME |
| DIS_B fade | nyam | IMB | N_IMB_rev_th0.1 | tgt=vwap stop=0.25ATR T120m | -1353 | +278 | +1131 | +1591 | +611 | +259 | -312 | ON L6M +1131 / HOLD +1299 / MID +611 (n 93); 2023-25 same switch PRE -340 / X' -314 (n 52) | p 0.119 | 0.5x HOLD +0.025 / L6M -0.001; 1.0x HOLD +0.053 / L6M -0.003 | TOLERANT REGIME |
| DIS_B fade | nyam | GAPFILL | N_GAPFILL_t31_g0.5_any | tgt=mid stop=0.25ATR T30m | -2555 | +156 | +1337 | +1031 | -1228 | +162 | -933 | ON L6M +1337 / HOLD +842 / MID -1228 (n 255); 2023-25 same switch PRE -261 / X' -486 (n 143) | p 0.129 | 0.5x HOLD +0.021 / L6M -0.033; 1.0x HOLD +0.046 / L6M -0.062 | NOW-ONLY REGIME |

Reading (S4a, interim; post-hoc, Shadow only):
- **P_REL_cont_m1.0 (08:30 release continuation, entry at the 08:35 close, flat by 09:25; the only cell positive in every window L1M..X')**: tgt R1, stop 1.0 ATR, time 30 min: 379 trades, +$67k total over the sample, mean $177 per trade at about 4.7 lots; the profit is SHORT-ONLY (shorts +$64.6k, longs +$2.5k), 2025 is negative (-$17k), non-event days +$56.7k vs event days +$10.4k, and its neighbours are NOT positive (stop 0.5 ATR -$11k, R2 +$12.8k, stop 0.25 ATR/60 min -$2.7k, R2/0.5 ATR -$23.5k; release threshold 0.5 ATR: +$47.9k only at the same shape, other shapes negative). Label: FRAGILE (single-shape spike, one side), not a lead.
- **N_REL_rev_m0.5 (NY-AM reversal of the 08:30 release move, entry 09:31, target = PM mid)**: placebo p .01 (best in the family). It is a plateau along the 'mid' target shapes (stop 0.25 / 0.5 / 1.0 ATR, 60 min: +$101k / +$78k / +$41k, 313 / 321 / 304 trades; the R1 targets of the same trades are negative), but the years alternate (2023 -$34k, 2024 +$68k, 2025 -$34k, 2026 +$41k) and the profit sits on non-event days (+$47.5k vs -$6.3k on event days). Label: REGIME / year-alternating until the family test is read.
- Release-move reversals at 08:35 (P_REL_rev) lose in every shape (-$80k..-$221k): the pre-market release move continues or noise, it does not mean-revert before 09:25.
