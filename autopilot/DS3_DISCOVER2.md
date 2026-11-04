
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

## DIS_H - after-stop / after-target follow-on books (Z2, 2026-11-04)
Prereg l2vast/ds3/prereg/DISH_prereg.md sha256 55a4aa636456877b90b996acacc4b0082d656c3b677d281b68d1fe27656e89a6 (+ addendum: RE = add-on position). dead_lookup: no standalone follow-on cell in the ledger; nearest RC1_RA (reverse-confirm exit actions, negative) and RE5_CUTWAIT (DEAD), cited. Rows: autopilot/FADE_ROWS_DISH.md; ledger DIS_H (108 cells); DISH_NTESTED 108. Code l2vast/ds3/code/dish/. No PASS claims.
Design: base = six live books (plain-bracket proxy, live Q1-A lots, P3 caveats). RS reverse at the stop second; RE add-on after a stop followed by a same-side base trade within 60 min; SL same-side second leg at the target second; sizes 0.5/1/2x; stop cost join 2.45 / native 1.28; entries by the live model.
Result: nothing survives. Of 108 cells: 86 NULL, 16 tolerant+v2a ("best-of-F"), 6 tolerant with short samples; zero LEAD. Median size-1 L6M/HOLD $/wk: RS -388/+216 (join), RE +277/+4, SL -2465/-1228. The family max-stat kills the positives: the real maximum L6M mean over the 108 cells ($10.1k, L_PE RE 2x, itself gate-failed) is below the median of the 120 null worlds' maxima ($13.2k; 95th pct $24.9k), so p_maxstat is 0.7-1.0 for every cell (note the statistic is unnormalised $, so the large-lot books dominate the null max, which makes it conservative for small cells). Tolerant-gate cells: L_PB SL (HOLD +300, L6M +472, but MID -953 and worst placebo p 0.83), L_PB RS (L6M +583, HOLD +876, placebo p 0.14, maxDD $13k), L_HM SL (L6M +1412 but L1M -3338, MID -3386, placebo p 0.72). Drawdowns at live lots are large (L_HM SL maxDD HOLD $48k) relative to the gains. Native 1.28 vs join 2.45 on the follow-on stop leg adds +$50-300/wk per cell but changes no label.
Conclusion: no follow-on book (reverse, re-entry add-on, second leg) shows an edge beyond the shifted-trigger placebo; reversing at the stop does not recover the stop loss (RS L6M median negative); the continuation leg after a target is negative at median. Sessions recent first in FADE_ROWS_DISH.md.

## DIS_K - range compression / expansion books on NQ (Z2, 2026-11-04)
Prereg l2vast/ds3/prereg/DISK_prereg.md sha256 0fcda083228285eb0fe52ce7f8c75517c40d7b8aceb1bd980f086fbe9841ad7d (+ addendum: EX125 threshold; n_tested 356). dead_lookup cited: NTE1 PDR.outside / squeeze skip rows (mostly DEAD), CF2-G1/G2 R_outside / RM_nr4 confirm entries, L2EB PDH/PDL level entries (1,350), SIZER_S2 range_so_far_ratio sizing; no standalone breakout/exhaustion book or state overlay existed. Rows autopilot/FADE_ROWS_DISK.md; ledger DIS_K 356 cells; DISK_NTESTED 356. Code l2vast/ds3/code/disk/, results /mnt/l2/l2vast/ds3_zones3_new/Z2_disk/. No PASS claims.
Design: 919 RTH days (2023-02..2026-10), 15 states (NR4 NR7 INSIDE OUTSIDE CLOSE_TOP/BOT COMP_LO/HI VOV_LO/HI ORC_LO/HI RSF_LO/HI ALL), BO (first 5-min close beyond the 09:30-10:00 range, with / against), EX / EX125 (range-so-far >= 1.5 / 1.25 x bucket median at a day extreme, fade), 2 geometries (60/60 T3600, 40/40 T1800), sessions nyam / nypm / RTH, 2 lots, live fill model; 336 book cells + 20 overlays on the Q1-A ts2 stack. Event counts: 862 BO (823 nyam, ~40 nypm because the first break is usually before 12:00), only 15 EX and 22 EX125 events in 3.5 years - all EX cells and all nypm cells are sample-short.
Result: no LEAD. 324 of 336 book cells NULL, 7 tolerant but sample short, 5 best-of-F (tolerant + gate_v2a): BO WITH-break on COMP_HI days (ATR5/ATR20 in its top third, i.e. expansion state), nyam: G1 L6M +882 / HOLD +785 / PRE +154 (MDE L6M 1,898, maxDD HOLD $9.8k, worst-20 -$33k), G2 L6M +893 / HOLD +557 / PRE +2 (MDE 1,368, maxDD $7.3k); RTH-pooled G1 +873 / +777 / +68. Their three placebos are favourable (shifted-state-date p 0.07-0.12, random side 0.01-0.05, shifted trigger time 0.02-0.08) but the family max-stat over 336 cells gives p_max 0.46-0.47 (the median of the world maxima is $843/wk, the real best cell is $893), the L6M mean is below its own MDE, MID is ~0 to -43 on the RTH pools, PA9 min HOLD Calmar only 0.07-0.08 and the stack Calmar gain is 0.000-0.002. Other best-of-F cells: CLOSE_BOT nyam WITH G2 (L6M +134, p_shift 0.33), ORC_LO nyam AGAINST G2 (L6M +329; p_state 0.02 but p_shift 0.43, p_max 1.00). Medians over all cells: BO WITH L6M -9 / HOLD +1, BO AGAINST 0 / -34, EX ~0 (too few events).
Overlays (state days x 0.5 / 1.5 on the live stack, separate 20-cell family): the largest L6M extra is VOV_HI x1.5 (+7,924/wk, MDE 8,969, p_state 0.28, p_max 0.54, stack Calmar gain HOLD -0.02), none clears the family (p_max >= 0.54), stack-Calmar gains all within +-0.05 and the 1.5x overlays raise HOLD drawdown (COMP_HI x1.5: $134k vs $105k). Conclusion: compression/expansion state does not give a tradeable book or a usable size overlay beyond what the shifted-state placebo and the family max-stat allow; the COMP_HI breakout-with line is the only item worth a forward Shadow watch label (best-of-F), not a lead.

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


# DS3_DISCOVER2 - DIS-J (ZL-1): OPTION-LEVEL books on NQ - interim 1, 2026-11-04 ~21:30Z. Research only, Shadow only, no PASS. Prereg DIS_J_PREREG.md sha256 88104ddf2a3c0bb33a942134fda3e266975e9ffdf3f4e97e0ca200de575fdbb7 (DECISIONS.md, before any outcome). Ledger DIS_J (652 cells), rows FADE_ROWS_DISJ.md, n_tested 668 (DISJ).
**Plain sentence: option-OI strike levels (walls, max pain, OI centroid, top-OI strikes from NDX and CME-NQ options) do not make a tolerant, placebo-clean fade or break book on NQ; the best cells are NY-AM break-continuation and failed-break trades that earn in 2026 (L6M +0.3k to +1.3k per week at 1 lot) and lose in 2024-25, and the strongest of them (NDX OI centroid, +926/wk L6M) is reproduced by randomly shifted lines (p .10), i.e. it is a generic NY-AM trend-continuation effect, not an options effect.**
dead_lookup first (1.54 M stored cells): no stored cell uses option strike levels (maxpain 0, strike 0, option 0 hits); the gamma-regime filters on the live books are DEAD (INST_D nq_gex_norm skip/half: e.g. entry|nq_gex_norm<=-0.01309|act=skip|scope=ALL6 L6M +2,143 / PRE -7,354; F1DD, DISC_E, A3SZ) and FADE_GM (117 cells, CAL) found no gamma-sign predictor: not retested.
## Method (as preregistered)
Pre-open open interest (OI snapshot of day d = prior close, causal): NDX OPRA OI by strike (expiries within 7 calendar days; NDX OI exists only from 2024-03: it is empty 2023-04..2024-02) and CME NQ option OI by strike (all listed quarterly expiries); levels per day: CW call wall, PW put wall, MP max pain, CENT OI-weighted centroid within +-5% of spot, T1K/T2K/T3K the three largest-OI strikes (>= 25 pt apart) = 14 families (N_ = NDX-based, Q_ = CME-NQ-based). NDX levels are mapped to NQ by basis(d) = previous-day NQ raw close minus the NDX index level from NDXP put-call parity (5-day rolling median; basis mean +117 pt, median +111, recent +230-250), CME strikes are NQ strikes; all in the RAW frame, converted to the path frame by + frame offset (frame_off/4). Sessions NYAM, NYPM; triggers T1 touch-reject, T2 failed break, T4 break-continuation (close beyond the level by 0.1 ATR then the next close further). Stage 1 = 76 cells with >= 30 trades (84 planned), default shape (stop = 5-bar extreme +0.5 ATR, 1R, 60 min); stage 2 = top 8 cells x 72 shapes (576 shapes). Evaluation FadeHarness gate_v3 (corrected carrying weeks), 100-draw placebos (shift5 / side / days), CAL R_F40 conditioning, shifted-line placebo (every level moved +-10-80 pt in the raw frame, 40 draws), family max-T (running). MDE/limits: OI exists only from 2024-03, so PRE covers 2024-03..2025-06 (about 16 months), X' (2023-04..2024-01) has NO data (n/a) and gate_v2a (which demands X' trades) cannot be met by construction; samples are small (stage-1 cells 30-260 trades over 2.6 years).
## Stage 1 (76 cells): NOW-ONLY 24, TOLERANT 11, STRICT 0, gate_v2a 0 (structural). Top by key (L3M + L6M)/2, $/wk at 1 lot (n; L1M L3M L6M HOLD MID PRE):
Q_MP NYAM T2 (96; 0 +765 +788 +364 -243 -168), N_CENT NYAM T4 (232; +906 +363 +926 +343 -62 -139), N_T2K NYAM T4 (111; +253 +408 +657 +380 -392 -83), Q_T2K NYAM T4 (70; +279 +405 +448 +122 -502 -200), Q_CENT NYPM T4 (174; +560 +355 +202 +270 +349 -71), Q_T3K NYAM T1 (74; 0 +231 +277 +269 +445 -101), N_MP NYAM T4 (114; 0 +91 +272 +579 +66 +150 = positive in every window, TOLERANT), N_T1K NYPM T4 (64; +158 +278 +34 +43 +130 +272, TOLERANT), N_MP NYPM T4 (84; +209 +36 +230 +141 +60 +121, TOLERANT).
## Stage 2 (576 shapes): NOW-ONLY 268, TOLERANT 29, STRICT 0. Best by key: N_CENT NYAM T4 (buffer 0.25, 1R, T60; 243 trades) L1M +738 / L3M +907 / L6M +1,272 / HOLD +605 / MID -73 / PRE -167; Q_MP NYAM T2 (b0.25 1.5R T60; 95) +0 / +810 / +1,238 / +545 / -496 / -124. The tolerant stage-2 shapes are N_CENT NYPM T1 / NYAM T4 variants with small means (NYPM T1: HOLD +115..+203, MID +141..+377, PRE +2..+76, L6M +26..+110).
## Placebos, 55 candidates (100 draws x 3 kinds; p = worst kind) and the shifted-line placebo
Cells with L6M-mean placebo p <= .10 (19 of 55) are all NOT tolerant (PRE negative): N_CENT NYAM T4 b0.25 1R T60 (HOLD-mean p .05, L6M p .02), Q_MP NYAM T2 b1 1R T60 (.05 / .02), N_T2K NYAM T4 default (.06 / .04). **None of the 33 tolerant candidates has L6M p <= .10** (best .119: N_CENT NYAM T4 b0.25 2R T120 L6M +759, HOLD +448, PRE +38; N_CENT NYPM T1 b0.5 1.5R T15, HOLD-mean p .05). Stack gain (carry-dropped, 1x): positive but tiny (+0.003..+0.02 Calmar) because a 1-lot book is 4% of the stack; stack-gain placebo p .07-.64.
Shifted-line placebo (stage-1 cells, 40 draws): 13 of 76 cells have p(L6M) <= .10, 8 with both L6M and HOLD <= .10: N_T2K NYAM T4 (n 111; real L6M +657 vs shifted p95 +553: p .02 / HOLD .07), N_CW NYPM T2 (n 34, tolerant: p .02 / .02), N_MP NYAM T4 (114; .07 / .02), N_T2K NYPM T4 (69; .10 / .02), Q_T3K NYPM T2 (50; .07 / .07), Q_CW NYAM T1, N_T1K NYPM T2, Q_CENT NYPM T4. The headline N_CENT NYAM T4 (+926) is NOT line-specific (p .10 / .39): shifted centroid lines earn the same.
## Verdict (flag rule: TOLERANT + placebo p <= .10 + positive carry-dropped stack gain + line-placebo p <= .10): NO cell meets all four. Nearest: N_MP NYAM T4 (default shape: tolerant, positive in all six windows, HOLD +579, line-placebo p .07 / .02, but the 100-draw placebo L6M p is .67 and n = 114) and N_T2K NYPM T4 (tolerant, line p .10 / .02, n 69). Both are too small to carry (MDE of a 114-trade book over 2.6 years is of the order of its own mean). Family max-T (HOLD Calmar, 652 books, 100 worlds): running, appended below.
## Not done / next: stage 3 (option levels as stop / target placements on the live KB trades; 8 cells) not reached; streaming reproduction diff is not run because nothing is flagged; if a level family is promoted the streaming check (level construction from the raw OI file) is the first step.
Files: /mnt/l2/l2vast/dis_j/ (oi_strikes.parquet, basis.parquet, events_raw.parquet, stage1.pkl, stage2.pkl, final_*.pkl, lineplc_table.csv, final_table.csv); code code/dis_j/ (dj_oi.py, dj_basis.py, dj_events.py, dj_stage.py, dj_final.py, dj_lineplc.py, dj_famnull.py).

## DIS-I INTERIM 2 (BASE-4, addendum to the section above): L6M_mean family, overlay placebo, ledger
* **Entry family, statistic L6M_mean** (512 books, 100 worlds per kind): best book AUCT_LONG|london|DRIFT_S|SH1 (+$1,252/wk L6M, 16 trades in L6M); family p of the real maximum: side null 0.218, days null 0.832; books with p_maxT <= 0.10: 0; BH q <= 0.10: 0 (smallest q 1.00). Raw p <= 0.05: 20 under the side null (26 expected), 16 under the days null, 6 under both. The five London DRIFT_S books at the top (AUCT_LONG, MS1, ISM, TOM, MS3) are short-drift entries 15 minutes after the London open; four of them (MS1, ISM, TOM, MS3) are nested sets of month-start days (the L6M trade days of MS1 are all inside MS3, which is inside TOM; ISM shares 6-11 days with them) and AUCT_LONG is a separate set of days with 0 shared L6M days; PRE and X' are negative (AUCT_LONG london DRIFT_S PRE -88, X' -56): a REGIME? label, not a lead.
* **Overlay placebo** for the only cell above the L6M and X' bands, OV|MS3|asia|QUARTER (PA9 L6M +20.0): P1 shifted calendar p 0.09 (L6M) / 0.09 (HOLD) / 0.36 (PRE), P2 random days per quarter 0.11 / 0.12 / 0.34, P3 weekday-matched random days 0.12 / 0.05 / 0.28; its carry-dropped L6M cut is 0.0, so the L6M cut is the carrying week alone: ONE-WEEK, no lead.
* **Final tally:** ADDITION lead 0, overlay LEAD 0, WEAK (placebos pass, family fails) 5 entry books; EINT2-covered 12 overlay cells cited. n_tested DISI = 1,038. Ledger DIS_I: 1,050 rows appended to DEAD_CELLS.csv (800 entry cells, 238 scored overlays, 12 covered overlays; spec grammar `entry|dis_i|cal=FLAG|ses=S|kind=K|shape=SH` and `sizing|dis_i|cal=FLAG|scope=SC|act=AN`, label in `extra`). Rows: FADE_ROWS_DISI.md (59 TOLERANT / STRICT entry books, top 40 overlays).
* **Limits:** flagged-day counts are small (L6M: 2-30 per flag), so no cell can show a window mean outside its MDE (0 of 512 entry books have L6M and HOLD means above their own MDE); the family statistics are HOLD Calmar (dominated by books with tiny drawdowns, e.g. ROLL_WEEK nyam FADE SH2 with HOLD maxDD $64) and L6M mean; the overlay family test is linearised (Pearson 0.82 with the engine cut); the CAL regime switch column is not filled (n/a); the genuine PA9 was applied to the overlays only (the entry books' stack gain is 1x / 0.5x with the carrying weeks dropped, within +-0.02 Calmar).

## DIS-J family max-T, scale-free HOLD Calmar (652 books = 76 stage-1 + 576 stage-2 shapes, 100 worlds each of random side and shuffled-day; ZL-1, ~22:30Z): family p of the real maximum 0.17 (side) / 0.32 (shuffled-day); 0 of 652 books with max-T p <= 0.10 or BH q <= 0.10 (smallest q 0.748). N_MP NYAM T4: p_raw 0.04, max-T 1.0, q 0.748; N_T2K NYAM T4 p_raw 0.04, q 0.748; Q_MP NYAM T2 p_raw 0.089, q 0.748; N_CENT NYAM T4 p_raw 0.20, q 0.773; N_T2K NYPM T4 0.228 / 0.773; N_CW NYPM T2 0.109 / 0.748. **No option-level book survives a family test on HOLD Calmar.** The L6M-dollar max-T run is in progress (stat L6M_mean, 100 worlds) and will be appended to this file.
