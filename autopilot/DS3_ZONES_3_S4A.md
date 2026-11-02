# DS3_ZONES_3_S4A - T-ZONES-3 section 4, first half (EVEN-index streams) of the other POI streams: AHEAD / BEHIND / AT frames

**BASE LABEL: this file is on D7 V13Y (the fixed base: add-fill ordering fix; V13X results are in DS3_ZONES_3_S4A_V13X_DEFECT_BASE.md and are labelled defect base). Original V13X note: sections 0-14 were on V13X = DEFECT BASE (BASE-4 found d7lib dropped TH-L2 loss cuts and take-line exits that preceded the resting-add fill, 846 rows). Section 15 re-runs the leads on the FIXED base V13Y; the full V13Y re-screen is in progress and will replace the headline. Original header: D7 v1.3 EXACT (V13X, user paste 02:45Z). HEADLINE FRAME = combined stack lock OFF (lock=None: the engine's own per-book 12R week floor and day give-back locks remain), as the lead ordered at 04:30Z; the same cells with the combined 12R lock ON are in the columns marked 'lock12'. A cut that exists only with lock 12 is LOCK-ONLY. The older assumed-base file is DS3_ZONES_3_S4A_ASSUMED_BASE.md.**

STATUS: S4a deliverable written 2026-11-02 12:15Z (V13Y; placebos 100 draws x3 for the 3 band-relevant cells, none for the rest; BEHIND/AT on V13Y pending, V13X versions are in the defect-base file). POST-HOC, Shadow only, no PASS claim, nothing here is a lead until the robustness standard is met; labels below say how far each cell got.
Prereg l2vast/ds3/prereg/ZONES3_S4A_prereg.md sha256 e8d9004f35ecf860d2beaac5372bdd274862c0db1225523eb12a877ac3fcb66d (DECISIONS.md). dead_lookup before: out/zones3_new/s4a_dead_lookup.txt (NOT FOUND for every spec); append_cells after: see end. NEW windows only (code/cap/windows.py): L1M L2M (view, n weeks 5/9) L3M L6M HOLD MID PRE X'. Old-cap numbers are not used.

## 0. Plain verdict

* On the FIXED base V13Y (D7 v1.3 exact + add-fill ordering fix) with the combined lock off, NO even-half stream clears the robustness standard and none passes the Z3 band rule (L6M and PRE/X' above band) except SWG|f3L|15s D40 half (L6M +.44, X' +.29, but MID -1.09 and equal-risk PRE -.56: VOLUME/FRAGILE). The V13X leads did not survive: EQL tight D40 falls to L6M +.11 / PRE +.08 / X' +.27 (below band, ONE-EPISODE), FIB ote705_dn D20 and MAS bb_mid D20 are DEAD (PRE/X' negative). The screen itself is at chance: of 763 eligible cells only 40 (5.2 %) are positive in L6M AND PRE AND X' with lock off against 5.7-7.7 % expected from random same-volume masks (section 13).
* Finalists with a positive cut in L6M AND PRE AND X' (lock off; the finalists were SELECTED from such cells, so this count is by construction): 16 of 24; with lock 12 the same count is 2.
  * EQL|EQL_tight|5m D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.12, screen +0.12, placebo ranks A/B/C 0.02/0.01/0.02 (n=100), label ONE-WEEK.
  * SES|asia_H|prev D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.10, screen +0.10, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label ONE-WEEK.
  * MAS|bb_up|1h D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.10, screen +0.10, placebo ranks A/B/C 0.02/0.05/0.05 (n=100), label -.
  * MAS|bb_lo|1h D40 half: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.10, screen +0.10, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.
  * MAS|bb_mid|4h D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.08, screen +0.08, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.
  * EQL|EQL_tight|5m D40 half: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.06, screen +0.06, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.
  * PIV|cam_H3|week D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.06, screen +0.06, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.
  * SES|asia_H|prev D40 half: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.06, screen +0.06, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.

## 1. Data and tie-out

* poi_store_redo has only 143 stream files (PDX, PIV, MAS 1h/4h, FIB 15m, CRT 4h, 3 PRF). The other 109 FIB/MAS/CRT streams and ARR (126), PRF (76), SES, KZ, DEV, OPN, GAP, ORB, SWG, EQL, BOS, WYK were rebuilt on the redo path (poi_gen / poi_adapt UNCHANGED, ARR and PRF from out/confirm_redo/streams) into /mnt/l2/l2vast/ds3_zones3_new/s4_streams (shared with S4b) and features for all 663 streams on the 88,490 D7 engine rows into /mnt/l2/l2vast/ds3_zones3_new/s4_feats.
* Tie to the OLD store on the old windows (44,370 old trades, 8 channels x 663 streams = 235,338,480 cells): 1,061 mismatching cells (0.0005 %), all in 11 streams: 10 month-anchored PDX/PIV|month streams (the last month closes differently at the old cap: 13-38 cells each) and PRF|npoc|day (830 cells). All other 652 streams tie exactly. out/zones3_new/s4a_feature_tie.csv. RND and BKS are not in the registry (named gap).

## 2. Screen (V13X EXACT, lock off, 1,272 distinct masks of 332 streams x D20/40 x half/skip), top 25 by excess cut over the same-volume placebo curve

| # | stream | D | frame | fires | vol | cut L1M | cut L2M | cut L3M | cut L6M | cut HOLD | cut MID | cut PRE | cut X | K | STRICT | TOL | NOW |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | SWG|f3L|15s | 40 | half | 42423 | 0.238 | +0.22 | +0.22 | +0.13 | +0.44 | +0.12 | -1.09 | +0.05 | +0.29 | +0.305 |  |  |  |
| 2 | DEV|on_L|so_far | 20 | half | 10884 | 0.073 | +0.61 | +0.20 | +0.45 | +0.69 | +0.22 | -0.43 | -0.30 | +0.17 | +0.287 |  |  | Y |
| 3 | SWG|f3L|3m | 20 | half | 19378 | 0.109 | +0.39 | +0.39 | +0.39 | +0.51 | +0.38 | -0.85 | -0.22 | +0.10 | +0.278 |  |  | Y |
| 4 | SWG|f5L|3m | 20 | half | 15731 | 0.087 | +0.28 | +0.28 | +0.34 | +0.24 | +0.29 | -0.44 | -0.01 | +0.06 | +0.234 |  |  | Y |
| 5 | SWG|f7L|3m | 20 | half | 13233 | 0.070 | +0.03 | +0.03 | +0.15 | +0.34 | +0.33 | -0.31 | -0.07 | -0.12 | +0.213 |  |  | Y |
| 6 | DEV|sess_L|so_far | 20 | half | 22088 | 0.114 | +0.64 | +0.48 | +0.33 | +0.70 | +0.27 | -0.74 | -0.17 | -0.37 | +0.192 |  |  | Y |
| 7 | SWG|f3L|15s | 20 | half | 37498 | 0.210 | +0.25 | +0.25 | +0.09 | +0.44 | +0.10 | -1.11 | -0.36 | +0.26 | +0.191 |  |  |  |
| 8 | SWG|f7L|15s | 20 | half | 29604 | 0.166 | +0.57 | +0.19 | +0.09 | +0.51 | +0.12 | -1.01 | -0.09 | -0.13 | +0.183 |  |  |  |
| 9 | MAS|bb_lo|1h | 40 | skip | 4531 | 0.052 | +0.06 | +0.06 | -0.31 | +0.31 | +0.01 | +0.13 | -0.03 | +0.08 | +0.182 |  |  |  |
| 10 | FIB|ret50|1h | 40 | skip | 3921 | 0.051 | +0.03 | +0.03 | -0.50 | +0.28 | +0.24 | -0.13 | -0.26 | +0.09 | +0.180 |  |  |  |
| 11 | DEV|on_L|so_far | 40 | half | 14378 | 0.100 | +0.52 | +0.41 | +0.58 | +0.68 | +0.08 | -1.03 | -0.61 | +0.21 | +0.178 |  |  |  |
| 12 | SWG|f5L|15s | 20 | half | 32550 | 0.183 | +0.50 | +0.34 | +0.25 | +0.53 | +0.13 | -0.96 | -0.33 | +0.00 | +0.165 |  |  |  |
| 13 | FIB|ext127|15m | 20 | skip | 4176 | 0.040 | +0.01 | +0.01 | +0.13 | +0.39 | -0.04 | -0.09 | -0.07 | +0.00 | +0.163 |  |  | Y |
| 14 | DEV|day_L|so_far | 20 | half | 15531 | 0.088 | +0.61 | +0.21 | +0.45 | +0.67 | +0.22 | -0.45 | -0.33 | -0.30 | +0.157 |  |  | Y |
| 15 | ARR|iplFVG|30m | 40 | skip | 5476 | 0.065 | +0.39 | +0.39 | -0.14 | +0.33 | +0.19 | -0.37 | -0.27 | +0.00 | +0.156 |  |  | Y |
| 16 | MAS|supertrend|4h | 40 | skip | 1328 | 0.012 | +0.09 | +0.09 | -0.08 | +0.30 | +0.05 | +0.20 | -0.02 | +0.18 | +0.146 |  |  |  |
| 17 | SWG|f5H|30m | 20 | skip | 5063 | 0.049 | -0.05 | -0.17 | -0.30 | +0.12 | +0.06 | -0.18 | +0.02 | -0.00 | +0.144 |  |  |  |
| 18 | SWG|f3L|10m | 20 | half | 10863 | 0.056 | +0.07 | +0.07 | -0.10 | +0.30 | +0.25 | -0.21 | -0.09 | -0.12 | +0.143 |  |  |  |
| 19 | SWG|f3H|30m | 20 | skip | 7122 | 0.075 | +0.01 | -0.06 | -0.17 | +0.01 | +0.07 | -0.16 | -0.02 | +0.14 | +0.141 |  |  |  |
| 20 | BOS|BOS_dn|1m | 40 | skip | 4482 | 0.045 | -0.05 | -0.05 | -0.02 | +0.18 | +0.04 | +0.25 | -0.19 | +0.16 | +0.141 |  |  |  |
| 21 | EQL|EQL_tight|5m | 40 | skip | 2062 | 0.023 | -0.04 | -0.04 | -0.05 | +0.11 | +0.01 | -0.10 | +0.08 | +0.27 | +0.137 |  |  | Y |
| 22 | DEV|day_L|so_far | 40 | half | 21611 | 0.130 | +0.51 | +0.42 | +0.57 | +0.66 | +0.07 | -0.89 | -0.65 | +0.14 | +0.136 |  |  |  |
| 23 | MAS|bb_up|1h | 40 | skip | 6792 | 0.065 | +0.13 | +0.13 | +0.24 | +0.14 | +0.13 | -0.03 | -0.03 | -0.06 | +0.135 |  |  | Y |
| 24 | ARR|BRK|3m | 20 | skip | 4442 | 0.046 | +0.40 | +0.39 | +0.03 | +0.17 | +0.12 | +0.14 | -0.17 | +0.06 | +0.135 |  |  | Y |
| 25 | MAS|bb_mid|4h | 40 | skip | 3345 | 0.036 | +0.35 | +0.35 | -0.03 | +0.15 | +0.13 | -0.24 | -0.01 | -0.03 | +0.134 |  |  |  |

cut = 1 - maxDD(cell)/maxDD(base), weekly cumulative. K = mean over L6M/HOLD/PRE/X' of (cut - placebo-curve cut at equal volume share). Base maxDD (v1.3 screen): L1M 27266, L2M 27266, L3M 31081, L6M 96181, HOLD 102968, MID 30181, PRE 129681, X 69748.

## 3. The 24 finalists on V13X lock off, ranked by the equal-risk cut (lock off, mean of L6M/HOLD/PRE/X'); the top 20 across both halves is merged by the lead

Base (v1.3, U7, 12R): maxDD L3M 31081, L6M 96181, HOLD 102968, MID 30181, PRE 129681, X 69748; mean $/wk L3M 19721, L6M 28755, HOLD 24582, MID 16396, PRE 12110, X 1641. Equal-risk = lot-table scale c so that the ALL worst-20 equals the base's (c shown), exact re-run.

| rank | stream | D | frame | vol | cut L6M | HOLD | MID | PRE | X' | ER c | ER cut L6M | HOLD | PRE | X' | ER dmean ALL $/wk | d L6M (MDE) | Calmar L6M base>cell | lock12 cut L6M/PRE | STRICT/TOL/NOW | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | EQL|EQL_tight|5m | 40 | skip | 0.023 | +0.11 | +0.01 | -0.10 | +0.08 | +0.27 | 1.00 | +0.11 | +0.01 | +0.08 | +0.27 | +237 | +1066 (4555) | 0.30>0.35 | +0.17/+0.02 | 0/0/1 | ONE-WEEK |
| 2 | SES|asia_H|prev | 20 | skip | 0.009 | +0.12 | -0.02 | +0.00 | +0.07 | +0.22 | 1.00 | +0.12 | -0.02 | +0.07 | +0.22 | -170 | -670 (2158) | 0.30>0.33 | +0.02/+0.03 | 0/0/0 | ONE-WEEK |
| 3 | MAS|bb_up|1h | 20 | skip | 0.027 | +0.17 | +0.14 | +0.07 | +0.03 | +0.05 | 1.00 | +0.17 | +0.14 | +0.03 | +0.05 | +425 | +1046 (3012) | 0.30>0.37 | +0.01/+0.38 | 1/1/1 | untagged |
| 4 | MAS|bb_lo|1h | 40 | half | 0.024 | +0.15 | -0.01 | +0.11 | +0.06 | +0.18 | 1.00 | +0.15 | -0.01 | +0.06 | +0.18 | -183 | -1003 (2998) | 0.30>0.34 | -0.10/-0.07 | 0/0/0 | untagged |
| 5 | MAS|bb_mid|4h | 20 | skip | 0.013 | +0.20 | -0.04 | -0.09 | +0.02 | +0.15 | 1.00 | +0.20 | -0.04 | +0.02 | +0.15 | +456 | +1056 (1976) | 0.30>0.39 | +0.01/+0.11 | 1/1/1 | untagged |
| 6 | EQL|EQL_tight|5m | 40 | half | 0.010 | +0.04 | +0.02 | +0.00 | +0.03 | +0.17 | 1.00 | +0.04 | +0.02 | +0.03 | +0.17 | +140 | +976 (2041) | 0.30>0.32 | +0.12/-0.05 | 0/0/1 | untagged |
| 7 | PIV|cam_H3|week | 40 | skip | 0.008 | +0.02 | +0.00 | -0.10 | +0.02 | +0.19 | 1.00 | +0.02 | +0.00 | +0.02 | +0.19 | -401 | +406 (1347) | 0.30>0.31 | +0.01/+0.04 | 0/0/1 | untagged |
| 8 | SES|asia_H|prev | 40 | half | 0.009 | +0.08 | -0.00 | -0.08 | +0.03 | +0.12 | 1.00 | +0.08 | -0.00 | +0.03 | +0.12 | -182 | +679 (1801) | 0.30>0.33 | +0.01/+0.00 | 0/1/1 | untagged |
| 9 | SES|nypm_H|prev | 20 | skip | 0.011 | +0.14 | +0.04 | +0.02 | +0.00 | +0.04 | 1.00 | +0.14 | +0.04 | +0.00 | +0.04 | +135 | -160 (2230) | 0.30>0.35 | -0.02/-0.03 | 0/0/0 | untagged |
| 10 | MAS|supertrend|4h | 40 | half | 0.005 | +0.04 | +0.04 | +0.13 | +0.03 | +0.10 | 1.00 | +0.04 | +0.04 | +0.03 | +0.10 | -141 | -246 (819) | 0.30>0.31 | +0.01/+0.21 | 0/0/0 | untagged |
| 11 | ARR|iplFVG|3m | 20 | half | 0.042 | +0.02 | -0.00 | -0.03 | +0.00 | +0.19 | 1.00 | +0.02 | -0.00 | +0.00 | +0.19 | -1065 | -2917 (4369) | 0.30>0.27 | -0.67/+0.36 | 0/0/0 | untagged |
| 12 | SWG|f3L|3m | 20 | half | 0.109 | +0.51 | +0.38 | -0.85 | -0.22 | +0.10 | 1.14 | +0.34 | +0.39 | -0.48 | -0.05 | -465 | +1639 (7982) | 0.30>0.64 | -0.03/+0.28 | 0/0/1 | (L6M/recent only) |
| 13 | MAS|bb_lo|1h | 40 | skip | 0.052 | +0.31 | +0.01 | +0.13 | -0.03 | +0.08 | 0.97 | +0.32 | +0.01 | -0.30 | +0.17 | -2582 | -1748 (7995) | 0.30>0.40 | +0.01/-0.11 | 0/0/0 | (L6M/recent only) |
| 14 | SWG|f3L|15s | 20 | half | 0.210 | +0.44 | +0.10 | -1.11 | -0.36 | +0.26 | 1.12 | +0.44 | +0.12 | -0.55 | +0.18 | -1940 | -3086 (11456) | 0.30>0.48 | -0.37/+0.30 | 0/0/0 | (L6M/recent only) |
| 15 | SES|asia_H|prev | 40 | skip | 0.021 | +0.09 | +0.02 | -0.61 | +0.05 | +0.14 | 0.96 | +0.22 | +0.04 | -0.17 | +0.05 | -2569 | +647 (4271) | 0.30>0.34 | -0.08/+0.20 | 0/1/1 | untagged |
| 16 | SES|close_H|prev | 20 | skip | 0.027 | +0.04 | -0.02 | -0.06 | +0.01 | +0.12 | 1.00 | +0.04 | -0.02 | +0.01 | +0.12 | +129 | -219 (3498) | 0.30>0.31 | +0.01/+0.08 | 0/0/0 | untagged |
| 17 | FIB|ret38|4h | 40 | skip | 0.029 | +0.10 | -0.10 | -0.20 | +0.10 | +0.02 | 1.00 | +0.10 | -0.10 | +0.10 | +0.02 | +308 | +1100 (4292) | 0.30>0.35 | -0.08/+0.17 | 0/1/1 | untagged |
| 18 | MAS|ema50|1d | 40 | skip | 0.005 | +0.18 | +0.22 | +0.00 | +0.01 | +0.02 | 1.02 | +0.14 | -0.12 | +0.01 | -0.04 | +307 | +1011 (1949) | 0.30>0.38 | +0.01/+0.06 | 0/0/1 | untagged |
| 19 | DEV|on_L|so_far | 20 | half | 0.073 | +0.69 | +0.22 | -0.43 | -0.30 | +0.17 | 1.14 | +0.56 | +0.09 | -0.64 | -0.10 | +218 | +1730 (10076) | 0.30>1.04 | +0.01/-0.08 | 0/0/1 | (L6M/recent only) |
| 20 | SWG|f5L|3m | 20 | half | 0.087 | +0.24 | +0.29 | -0.44 | -0.01 | +0.06 | 1.17 | +0.21 | +0.26 | -0.46 | -0.11 | -295 | +1012 (6219) | 0.30>0.41 | -0.13/+0.25 | 0/0/1 | ONE-WEEK |
| 21 | DEV|sess_L|so_far | 20 | half | 0.114 | +0.70 | +0.27 | -0.74 | -0.17 | -0.37 | 1.16 | +0.53 | +0.27 | -0.45 | -0.57 | -396 | +2183 (10176) | 0.30>1.06 | +0.01/-0.09 | 0/0/1 | (L6M/recent only) |
| 22 | SWG|f7L|15s | 20 | half | 0.166 | +0.51 | +0.12 | -1.01 | -0.09 | -0.13 | 1.17 | +0.34 | +0.06 | -0.41 | -0.24 | -1064 | -324 (11104) | 0.30>0.61 | -0.33/+0.28 | 0/0/0 | (L6M/recent only) |
| 23 | SWG|f7L|3m | 20 | half | 0.070 | +0.34 | +0.33 | -0.31 | -0.07 | -0.12 | 1.11 | +0.13 | +0.18 | -0.31 | -0.26 | +386 | +2199 (5311) | 0.30>0.49 | -0.07/+0.15 | 0/0/1 | (L6M/recent only) |
| 24 | SWG|f3L|15s | 40 | half | 0.238 | +0.44 | +0.12 | -1.09 | +0.05 | +0.29 | 1.24 | +0.15 | +0.05 | -0.56 | +0.06 | -1484 | -2417 (10555) | 0.30>0.49 | -0.17/+0.34 | 0/0/0 | untagged |

## 4. Robustness of the finalists (v1.3 + U7 series; windows L6M and PRE)

| stream | D | frame | trough week base L6M | cut L6M | drop trough week | LOEO min..max | LOMO min..max | boot 5-95% | P(cut>0) | trough PRE | cut PRE | LOEO PRE | LOMO PRE | placebo rank A/B/C (n) | D variants x0.5/.75/1.25/1.5 mean4 cut | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m | 40 | skip | 202632 | +0.11 | +0.00 | -0.18..-0.18 | -0.18..+0.11 | -0.18..+0.14 | 0.57 | 202440 | +0.08 | +0.04..+0.08 | +0.04..+0.14 | 0.02/0.01/0.02 (100) | pending | ONE-WEEK |
| SES|asia_H|prev | 20 | skip | 202632 | +0.12 | +0.00 | +0.02..+0.02 | +0.00..+0.12 | -0.02..+0.18 | 0.69 | 202440 | +0.07 | +0.04..+0.07 | +0.04..+0.07 | 1.00/1.00/1.00 (0) | pending | ONE-WEEK |
| MAS|bb_up|1h | 20 | skip | 202632 | +0.17 | +0.12 | +0.04..+0.04 | +0.04..+0.18 | -0.00..+0.22 | 0.94 | 202440 | +0.03 | +0.03..+0.04 | +0.03..+0.08 | 0.02/0.05/0.05 (100) | pending | untagged |
| MAS|bb_lo|1h | 40 | half | 202632 | +0.15 | +0.23 | +0.04..+0.04 | -0.12..+0.23 | -0.49..+0.27 | 0.68 | 202440 | +0.06 | +0.02..+0.06 | +0.02..+0.10 | 1.00/1.00/1.00 (0) | pending | untagged |
| MAS|bb_mid|4h | 20 | skip | 202632 | +0.20 | +0.21 | +0.00..+0.00 | +0.00..+0.21 | +0.00..+0.24 | 0.91 | 202440 | +0.02 | +0.02..+0.04 | +0.02..+0.09 | 1.00/1.00/1.00 (0) | pending | untagged |
| EQL|EQL_tight|5m | 40 | half | 202632 | +0.04 | -0.03 | -0.11..-0.11 | -0.11..+0.04 | -0.11..+0.06 | 0.39 | 202440 | +0.03 | -0.01..+0.03 | -0.01..+0.06 | 1.00/1.00/1.00 (0) | pending | untagged |
| PIV|cam_H3|week | 40 | skip | 202632 | +0.02 | +0.02 | -0.00..-0.00 | -0.00..+0.02 | -0.00..+0.08 | 0.84 | 202440 | +0.02 | -0.01..+0.02 | -0.01..+0.02 | 1.00/1.00/1.00 (0) | pending | untagged |
| SES|asia_H|prev | 40 | half | 202632 | +0.08 | -0.03 | +0.00..+0.00 | -0.03..+0.08 | -0.03..+0.17 | 0.52 | 202440 | +0.03 | -0.00..+0.03 | -0.00..+0.03 | 1.00/1.00/1.00 (0) | pending | untagged |
| SES|nypm_H|prev | 20 | skip | 202632 | +0.14 | +0.17 | -0.06..-0.06 | -0.06..+0.17 | -0.06..+0.18 | 0.73 | 202440 | +0.00 | +0.00..+0.00 | -0.08..+0.06 | 1.00/1.00/1.00 (0) | pending | untagged |
| MAS|supertrend|4h | 40 | half | 202632 | +0.04 | +0.01 | +0.00..+0.00 | +0.00..+0.04 | -0.06..+0.06 | 0.65 | 202440 | +0.03 | -0.01..+0.03 | -0.01..+0.03 | 1.00/1.00/1.00 (0) | pending | untagged |
| ARR|iplFVG|3m | 20 | half | 202632 | +0.02 | +0.16 | +0.06..+0.06 | +0.01..+0.11 | -0.01..+0.24 | 0.81 | 202440 | +0.00 | +0.00..+0.01 | +0.00..+0.12 | 1.00/1.00/1.00 (0) | pending | untagged |
| SWG|f3L|3m | 20 | half | 202632 | +0.51 | +0.43 | +0.29..+0.29 | +0.29..+0.55 | +0.29..+0.56 | 1.00 | 202440 | -0.22 | -0.28..+0.02 | -0.62..+0.05 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| MAS|bb_lo|1h | 40 | skip | 202632 | +0.31 | +0.45 | +0.22..+0.22 | -0.24..+0.45 | -0.92..+0.57 | 0.74 | 202440 | -0.03 | -0.08..-0.03 | -0.08..+0.12 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SWG|f3L|15s | 20 | half | 202632 | +0.44 | +0.55 | +0.30..+0.38 | +0.14..+0.63 | -0.34..+0.79 | 0.88 | 202440 | -0.36 | -0.42..+0.08 | -0.84..+0.08 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SES|asia_H|prev | 40 | skip | 202632 | +0.09 | -0.05 | +0.03..+0.03 | -0.05..+0.09 | -0.05..+0.23 | 0.63 | 202440 | +0.05 | +0.00..+0.11 | +0.00..+0.11 | 1.00/1.00/1.00 (0) | pending | untagged |
| SES|close_H|prev | 20 | skip | 202632 | +0.04 | +0.01 | +0.02..+0.02 | +0.01..+0.04 | +0.01..+0.10 | 0.98 | 202440 | +0.01 | +0.01..+0.05 | -0.03..+0.05 | 1.00/1.00/1.00 (0) | pending | untagged |
| FIB|ret38|4h | 40 | skip | 202632 | +0.10 | +0.11 | -0.27..-0.27 | -0.27..+0.11 | -0.30..+0.21 | 0.64 | 202440 | +0.10 | +0.06..+0.10 | +0.06..+0.18 | 1.00/1.00/1.00 (0) | pending | untagged |
| MAS|ema50|1d | 40 | skip | 202632 | +0.18 | +0.21 | +0.00..+0.00 | +0.00..+0.21 | +0.00..+0.24 | 0.72 | 202440 | +0.01 | -0.04..+0.07 | -0.04..+0.07 | 1.00/1.00/1.00 (0) | pending | untagged |
| DEV|on_L|so_far | 20 | half | 202632 | +0.69 | +0.66 | +0.21..+0.21 | +0.21..+0.72 | +0.21..+0.80 | 1.00 | 202440 | -0.30 | -0.36..+0.19 | -0.36..+0.19 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SWG|f5L|3m | 20 | half | 202632 | +0.24 | +0.12 | +0.32..+0.32 | +0.12..+0.32 | +0.12..+0.44 | 1.00 | 202440 | -0.01 | -0.06..+0.02 | -0.17..+0.15 | 0.01/0.05/0.12 (100) | pending | ONE-WEEK |
| DEV|sess_L|so_far | 20 | half | 202632 | +0.70 | +0.68 | +0.38..+0.38 | +0.37..+0.72 | +0.36..+0.82 | 1.00 | 202440 | -0.17 | -0.22..+0.19 | -0.37..+0.19 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SWG|f7L|15s | 20 | half | 202632 | +0.51 | +0.60 | +0.34..+0.35 | +0.14..+0.60 | -0.20..+0.68 | 0.91 | 202440 | -0.09 | -0.14..+0.04 | -0.53..+0.18 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SWG|f7L|3m | 20 | half | 202632 | +0.34 | +0.24 | +0.19..+0.19 | +0.19..+0.40 | +0.15..+0.41 | 1.00 | 202440 | -0.07 | -0.12..-0.02 | -0.20..+0.17 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SWG|f3L|15s | 40 | half | 202632 | +0.44 | +0.40 | +0.24..+0.35 | +0.18..+0.49 | -0.19..+0.53 | 0.92 | 202440 | +0.05 | +0.00..+0.26 | -0.09..+0.26 | 0.01/0.01/0.09 (100) | pending | untagged |

Placebos (V13X lock off, the same engine as the screen): A random levels = same number of random rows per book x session x side x target-half stratum; B same-volume Bernoulli over eligible rows; C shuffled-day line set (circular shift of the fire vector inside each book x session in time order); statistic = mean of the L6M/HOLD/PRE/X' cuts; rank = (1+#placebo >= cell)/(1+n), n = 16 draws so 0.059 is the best achievable rank. Weeks named by ISO key. LOEO = drop each of the 3 largest base drawdown episodes, LOMO = drop each month, 300 month-block bootstrap draws.

## 5. Per book and per session (maxDD cut, HOLD window | PRE window), top 8 finalists; and mean change by vol tercile (HOLD, $ per week)

| stream | D | frame | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | pre | nyam | nypm | close | vol terc lo/mid/hi d$/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m | 40 | skip | +0.01|+0.00 | +0.00|-0.03 | +0.00|+0.00 | +0.08|+0.00 | -0.07|+0.08 | +0.00|+0.21 | -0.06|+0.04 | -0.14|-0.16 | +0.00|+0.00 | +0.03|+0.00 | +0.01|-0.05 | +0.00|+0.00 | +455/-60/+116 |
| SES|asia_H|prev | 20 | skip | +0.01|+0.07 | -0.02|+0.08 | +0.03|-0.01 | +0.00|+0.00 | +0.06|+0.02 | +0.00|+0.00 | +0.00|+0.00 | -0.05|+0.02 | +0.00|+0.00 | +0.08|-0.01 | -0.02|+0.09 | +0.00|+0.00 | +11/-404/+3 |
| MAS|bb_up|1h | 20 | skip | +0.00|-0.02 | +0.05|+0.19 | +0.00|-0.03 | +0.19|+0.01 | +0.03|+0.06 | +0.00|+0.35 | +0.09|-0.07 | +0.07|-0.02 | +0.00|+0.00 | +0.11|-0.01 | +0.01|-0.12 | +0.00|+0.00 | +696/+227/+253 |
| MAS|bb_lo|1h | 40 | half | -0.00|-0.01 | +0.05|-0.05 | +0.04|+0.03 | +0.12|+0.17 | +0.06|-0.02 | -0.06|+0.00 | -0.07|+0.01 | -0.07|-0.04 | +0.00|+0.00 | +0.06|+0.03 | -0.13|+0.01 | +0.00|+0.00 | +413/-191/-930 |
| MAS|bb_mid|4h | 20 | skip | -0.11|-0.00 | -0.05|+0.14 | +0.12|+0.00 | +0.05|+0.06 | -0.03|+0.03 | -0.12|+0.00 | +0.18|+0.00 | -0.03|+0.05 | +0.00|+0.00 | -0.29|+0.28 | +0.02|+0.02 | +0.00|+0.00 | +489/+216/+280 |
| EQL|EQL_tight|5m | 40 | half | +0.00|+0.00 | +0.00|-0.02 | +0.00|+0.00 | +0.04|+0.00 | +0.01|+0.02 | +0.00|+0.14 | -0.00|+0.03 | -0.06|-0.07 | +0.00|+0.00 | +0.00|+0.02 | +0.00|+0.00 | +0.00|+0.00 | +320/+153/-28 |
| PIV|cam_H3|week | 40 | skip | +0.00|+0.02 | +0.00|-0.04 | +0.00|+0.00 | +0.00|-0.01 | +0.09|+0.02 | +0.00|+0.00 | +0.03|-0.01 | +0.01|-0.01 | +0.00|+0.00 | +0.19|+0.00 | +0.06|+0.05 | +0.00|+0.00 | +15/+176/+112 |
| SES|asia_H|prev | 40 | half | +0.00|-0.01 | -0.00|-0.01 | +0.02|+0.02 | +0.00|-0.01 | +0.01|+0.14 | +0.00|+0.00 | -0.01|+0.00 | -0.03|+0.06 | +0.00|+0.00 | +0.05|+0.00 | +0.01|+0.03 | +0.00|+0.00 | +289/-343/-66 |

Sessions: a zone cut that lives in one session only is a different product (Asia carries the stack in 2026). Vol tercile = tercile of the day's mean library target distance (volatility proxy) inside HOLD.

## 6. BEHIND and AT frames (v1.3 + U7; streams = the 19 distinct finalist streams (top 20 ranks); cut vs the v1.3 base)

BEHIND: fresh POI between entry and stop within Db pts; actions skip / half / restop (stop moved to line - 2 ticks, only if tighter than the library stop; core books; re-simulated with the same jrun kernel as the engine, tie-out exact for the six core books; PE NY rows are not re-stopped = approximate; the TH-L2 loss cut interaction on re-stopped rows is approximate). AT: POI within 2 pts of the entry (fresh or touched, ahead or behind): take-only (skip rows not AT inside book x session cells with >= 50 AT rows; volume collapses, read with equal-risk) / sizeup (x1.5).

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
**BEHIND (top 25 by mean of L6M/HOLD/PRE/X' cut)**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| SWG|f3L|15s | BEHIND | 20 | half | 23256 | +0.16 | +0.22 | +0.18 | -0.19 | +0.24 | -11469 (10409) | 0.22/0.30 |
| MAS|bb_lo|1h | BEHIND | 10 | half | 38 | +0.25 | +0.00 | +0.00 | +0.00 | -0.02 | +907 (2544) | 0.41/0.30 |
| MAS|bb_lo|1h | BEHIND | 20 | half | 151 | +0.25 | +0.00 | +0.00 | +0.00 | -0.04 | +907 (2544) | 0.41/0.30 |
| MAS|bb_up|1h | BEHIND | 20 | skip | 377 | +0.00 | +0.00 | +0.00 | +0.05 | +0.15 | +179 (753) | 0.30/0.30 |
| MAS|bb_up|1h | BEHIND | 20 | half | 305 | +0.00 | +0.00 | +0.00 | +0.03 | +0.14 | +130 (404) | 0.30/0.30 |
| MAS|bb_lo|1h | BEHIND | 10 | restop | 41 | +0.14 | +0.00 | +0.00 | +0.00 | +0.00 | +573 (1718) | 0.35/0.30 |
| EQL|EQL_tight|5m | BEHIND | 10 | skip | 67 | +0.00 | +0.00 | +0.00 | +0.00 | +0.14 | +0 (0) | 0.30/0.30 |
| MAS|bb_up|1h | BEHIND | 20 | restop | 377 | +0.00 | +0.00 | -0.53 | +0.05 | +0.09 | -448 (2505) | 0.29/0.30 |
| MAS|bb_lo|1h | BEHIND | 20 | restop | 176 | +0.14 | +0.00 | +0.00 | +0.00 | -0.01 | +636 (1716) | 0.36/0.30 |
| MAS|bb_lo|1h | BEHIND | 10 | skip | 41 | +0.16 | +0.00 | +0.00 | +0.00 | -0.03 | +598 (1701) | 0.36/0.30 |
| EQL|EQL_tight|5m | BEHIND | 10 | restop | 67 | +0.00 | +0.00 | +0.00 | +0.00 | +0.11 | +0 (0) | 0.30/0.30 |
| MAS|bb_lo|1h | BEHIND | 20 | skip | 176 | +0.16 | -0.01 | +0.00 | +0.00 | -0.10 | +642 (1699) | 0.36/0.30 |
| MAS|bb_up|1h | BEHIND | 10 | restop | 88 | +0.00 | +0.00 | +0.00 | +0.04 | +0.00 | +211 (592) | 0.30/0.30 |
| MAS|bb_up|1h | BEHIND | 10 | skip | 88 | +0.00 | +0.00 | +0.00 | +0.04 | +0.00 | -112 (221) | 0.30/0.30 |
| SWG|f3L|15s | BEHIND | 20 | skip | 28732 | -0.02 | +0.05 | -1.10 | -0.05 | +0.07 | -20114 (19371) | 0.09/0.30 |
| MAS|bb_mid|4h | BEHIND | 20 | skip | 94 | +0.00 | +0.00 | +0.00 | +0.00 | +0.04 | +24 (68) | 0.30/0.30 |
| EQL|EQL_tight|5m | BEHIND | 20 | skip | 363 | +0.00 | +0.00 | +0.00 | -0.10 | +0.13 | -17 (407) | 0.30/0.30 |
| MAS|bb_up|1h | BEHIND | 10 | half | 71 | +0.00 | +0.00 | +0.00 | +0.03 | +0.00 | -22 (62) | 0.30/0.30 |
| MAS|bb_mid|4h | BEHIND | 20 | half | 60 | +0.00 | +0.00 | +0.00 | +0.00 | +0.02 | +0 (0) | 0.30/0.30 |
| MAS|ema50|1d | BEHIND | 20 | half | 3 | +0.01 | +0.00 | +0.00 | +0.00 | +0.00 | +25 (69) | 0.30/0.30 |
| MAS|ema50|1d | BEHIND | 10 | half | 2 | +0.01 | +0.00 | +0.00 | +0.00 | +0.00 | +25 (69) | 0.30/0.30 |
| SES|asia_H|prev | BEHIND | 10 | restop | 1 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.30/0.30 |
| EQL|EQL_tight|5m | BEHIND | 10 | half | 32 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.30/0.30 |
| MAS|bb_mid|4h | BEHIND | 10 | skip | 14 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.30/0.30 |
| SES|asia_H|prev | BEHIND | 10 | skip | 1 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.30/0.30 |

**AT size-up (x1.5 on rows with a POI within 2 pts)**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| MAS|bb_lo|1h | AT | 2 | sizeup | 355 | +0.39 | -0.01 | -0.01 | +0.00 | -0.04 | +1073 (4445) | 0.51/0.30 |
| MAS|bb_mid|4h | AT | 2 | sizeup | 357 | +0.01 | +0.02 | -0.07 | -0.08 | +0.06 | -66 (970) | 0.30/0.30 |
| SES|asia_H|prev | AT | 2 | sizeup | 712 | -0.02 | -0.00 | -0.02 | +0.03 | -0.02 | +90 (1096) | 0.29/0.30 |
| MAS|bb_up|1h | AT | 2 | sizeup | 551 | +0.00 | +0.01 | +0.00 | +0.01 | -0.03 | +453 (757) | 0.30/0.30 |
| EQL|EQL_tight|5m | AT | 2 | sizeup | 1501 | -0.01 | -0.02 | +0.02 | -0.05 | +0.04 | +42 (1360) | 0.30/0.30 |
| SWG|f3L|3m | AT | 2 | sizeup | 22209 | +0.09 | +0.15 | -0.42 | -0.33 | +0.06 | +5104 (8571) | 0.38/0.30 |
| MAS|ema50|1d | AT | 2 | sizeup | 92 | -0.05 | +0.00 | +0.00 | +0.02 | -0.02 | -344 (522) | 0.28/0.30 |
| DEV|on_L|so_far | AT | 2 | sizeup | 2061 | -0.02 | +0.05 | -0.18 | -0.12 | -0.02 | +129 (2233) | 0.30/0.30 |
| SWG|f3L|15s | AT | 2 | sizeup | 44555 | -0.40 | -0.43 | -0.34 | -1.64 | -0.37 | +8412 (9761) | 0.28/0.30 |

**AT take-only (skip every row not AT in cells with >= 50 AT rows): the volume collapses (rows = skipped rows, 8-50 % of the book), so the cut is mostly volume; read the mean column and Calmar, not the cut. Not a lead.**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| MAS|bb_up|1h | AT | 2 | takeonly | 16838 | +0.14 | +0.03 | -0.15 | -0.06 | +0.01 | -850 (3302) | 0.34/0.30 |
| SES|asia_H|prev | AT | 2 | takeonly | 7415 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.30/0.30 |
| MAS|bb_mid|4h | AT | 2 | takeonly | 0 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.30/0.30 |
| MAS|bb_lo|1h | AT | 2 | takeonly | 0 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.30/0.30 |
| MAS|ema50|1d | AT | 2 | takeonly | 0 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.30/0.30 |
| EQL|EQL_tight|5m | AT | 2 | takeonly | 33267 | +0.55 | +0.14 | -0.51 | -0.83 | +0.24 | -17801 (25931) | 0.25/0.30 |
| SWG|f3L|15s | AT | 2 | takeonly | 10744 | +0.09 | +0.15 | +0.16 | -0.25 | +0.14 | -7753 (9639) | 0.24/0.30 |
| SWG|f3L|3m | AT | 2 | takeonly | 33060 | +0.29 | +0.29 | -1.44 | -0.08 | +0.26 | -16875 (21834) | 0.17/0.30 |
| DEV|on_L|so_far | AT | 2 | takeonly | 21541 | +0.03 | +0.10 | -0.79 | -0.46 | -0.17 | -19478 (23403) | 0.10/0.30 |

## 7. New lines worth adding, with exact D7-computable definitions

None is yet a RISK-KEEP line. The ones to carry to the merged top 20 as screen LEADS (post-hoc, definitions exact; label shown):

* **EQL|EQL_tight|5m, AHEAD D 40 pts, fresh, action SKIP** (label ONE-WEEK). Definition: Equal lows (within 1.0 pt) between two fractal-5 swings on 5m bars (one of the last 8 swings, no bar in between exceeding), level = the higher (highs) or lower (lows) of the pair. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 2062 of 88,490 rows (2.3 % of planned lot volume).
* **SES|asia_H|prev, AHEAD D 20 pts, fresh, action SKIP** (label ONE-WEEK). Definition: Previous completed asia window high (ET windows: asia 18-02, london 02-08:30, pre 08:30-09:30, nyam 09:30-12, nypm 12-15, close 15-17, on 18-09:30, rth 09:30-16; killzones asia 20-24, london 02-05, ny 07-10, lc 10-12), knowable at window end. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 1282 of 88,490 rows (0.9 % of planned lot volume).
* **MAS|bb_up|1h, AHEAD D 20 pts, fresh, action SKIP** (label -). Definition: bb_up on 1h bars at the last CLOSED bar (EMA/SMA n=50/100/200 of close; Bollinger 20,2 sd; Keltner 20 EMA +/- 2 ATR10; Donchian 20 high/low; Supertrend 10,3; Ichimoku 9/26/52 with spans displaced 26 bars forward). Line value fixed at the bar close until the next bar. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 3120 of 88,490 rows (2.7 % of planned lot volume).
* **MAS|bb_lo|1h, AHEAD D 40 pts, fresh, action HALF** (label -). Definition: bb_lo on 1h bars at the last CLOSED bar (EMA/SMA n=50/100/200 of close; Bollinger 20,2 sd; Keltner 20 EMA +/- 2 ATR10; Donchian 20 high/low; Supertrend 10,3; Ichimoku 9/26/52 with spans displaced 26 bars forward). Line value fixed at the bar close until the next bar. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then scale the planned lots x0.5 (integer half-up, min 1; trades already halved by the shipped 7-line set are not quartered). Fires on 4531 of 88,490 rows (2.4 % of planned lot volume).
* **MAS|bb_mid|4h, AHEAD D 20 pts, fresh, action SKIP** (label -). Definition: bb_mid on 4h bars at the last CLOSED bar (EMA/SMA n=50/100/200 of close; Bollinger 20,2 sd; Keltner 20 EMA +/- 2 ATR10; Donchian 20 high/low; Supertrend 10,3; Ichimoku 9/26/52 with spans displaced 26 bars forward). Line value fixed at the bar close until the next bar. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 1298 of 88,490 rows (1.3 % of planned lot volume).
* **EQL|EQL_tight|5m, AHEAD D 40 pts, fresh, action HALF** (label -). Definition: Equal lows (within 1.0 pt) between two fractal-5 swings on 5m bars (one of the last 8 swings, no bar in between exceeding), level = the higher (highs) or lower (lows) of the pair. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then scale the planned lots x0.5 (integer half-up, min 1; trades already halved by the shipped 7-line set are not quartered). Fires on 2062 of 88,490 rows (1.0 % of planned lot volume).
* **PIV|cam_H3|week, AHEAD D 40 pts, fresh, action SKIP** (label -). Definition: Camarilla H3 = C + 1.1*(H-L)/4 from the prior CME week H, L, C. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 1058 of 88,490 rows (0.8 % of planned lot volume).
* **SES|asia_H|prev, AHEAD D 40 pts, fresh, action HALF** (label -). Definition: Previous completed asia window high (ET windows: asia 18-02, london 02-08:30, pre 08:30-09:30, nyam 09:30-12, nypm 12-15, close 15-17, on 18-09:30, rth 09:30-16; killzones asia 20-24, london 02-05, ny 07-10, lc 10-12), knowable at window end. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then scale the planned lots x0.5 (integer half-up, min 1; trades already halved by the shipped 7-line set are not quartered). Fires on 2695 of 88,490 rows (0.9 % of planned lot volume).

The 8 shipped lines and the 3 profile lines are not in this section. L1M/L2M columns are views, never selected on.

## 11. B8: the zone as TARGET (every even-index stream, V13Y lock off, post-hoc)

Rule: when the nearest fresh line ahead lies between 4 pts and (target - 4 pts) from the entry, the first leg takes profit at the line; 'b73t' = share F of the lots (the engine's integer split share per book/session, 0.5-0.75) exits at the line and the rest keeps the library target (the OTE-62 B73 idea turned to the target side); 'rt' = all lots exit at the line. Simulated per lot with poi_sim.mkt_run (market entry at the signal price, N basis) and added to the engine's split outcome; exit second/type of the library trade unchanged (the 30% leg keeps the original exit time): APPROXIMATE, PE NY confirmed entries not touched. BASE-4 covers the shipped lines (DS3_B8_ZONE_TARGET_SHIPPED.md).

* 632 (stream, mode) cells scored; mean change in $/wk (ALL) averages -588 for b73t and -909 for rt: re-targeting to a line costs money on average (the library target is usually better than the first line). 131 cells improve the mean; 6 cells have a positive maxDD cut in L6M AND PRE AND X'.

**Top 12 by mean cut (L6M/HOLD/PRE/X')**

| stream | mode | rows | cut L6M | cut HOLD | cut MID | cut PRE | cut X | d L6M (MDE) | d ALL $/wk |
|--|--|--|--|--|--|--|--|--|--|
| ARR|FVG|4h | b73t | 3055 | +0.48 | -0.04 | -0.40 | +0.03 | +0.00 | +212 (5364) | +168 |
| FIB|dr_low|1d | rt | 124 | +0.42 | +0.00 | -0.01 | +0.00 | +0.00 | +1491 (4239) | +112 |
| ARR|FVG|4h | rt | 3055 | +0.55 | -0.12 | -0.58 | +0.02 | -0.05 | +438 (7762) | +126 |
| FIB|ret38|1d | rt | 628 | +0.18 | +0.04 | +0.00 | +0.15 | -0.03 | +965 (1791) | +388 |
| MAS|bb_lo|1h | b73t | 4130 | +0.19 | -0.12 | -0.33 | +0.02 | +0.18 | +801 (3748) | +23 |
| BOS|BOS_dn|15m | rt | 929 | +0.09 | +0.01 | +0.00 | +0.02 | +0.15 | +1631 (3101) | +427 |
| MAS|kc_lo|4h | b73t | 1593 | +0.39 | -0.04 | -0.25 | +0.02 | -0.11 | +1505 (3283) | +387 |
| MAS|ich_kijun|1d | rt | 737 | +0.15 | +0.04 | +0.02 | +0.00 | +0.05 | -17 (2504) | +86 |
| BOS|BOS_dn|1m | b73t | 3383 | +0.09 | +0.15 | +0.03 | -0.06 | +0.02 | -996 (4558) | -309 |
| PIV|cam_L2|week | rt | 639 | +0.38 | -0.05 | -0.14 | -0.00 | -0.13 | +249 (4372) | -147 |
| MAS|ich_kijun|1d | b73t | 737 | +0.14 | +0.02 | +0.02 | +0.00 | +0.03 | +98 (1755) | +139 |
| PRF|val|week | rt | 555 | +0.00 | +0.01 | -0.12 | +0.01 | +0.17 | +42 (1760) | +102 |

**Top 8 by mean improvement ($/wk, ALL)**

| stream | mode | rows | d ALL $/wk | cut L6M | cut PRE | cut X' |
|--|--|--|--|--|--|--|
| ARR|FVG|1h | rt | 4634 | +1809 | -0.30 | -0.03 | -0.14 |
| FIB|ote705_up|1h | rt | 4713 | +1313 | -0.26 | -0.08 | -0.26 |
| PRF|poc|sess | rt | 1521 | +948 | +0.17 | -0.23 | -0.48 |
| FIB|ote705_up|1h | b73t | 4713 | +859 | -0.16 | -0.04 | -0.29 |
| ARR|FVG|1h | b73t | 4634 | +821 | -0.29 | +0.02 | -0.08 |
| ARR|FVG_CE|1h | rt | 6368 | +762 | +0.13 | +0.03 | +0.01 |
| PRF|poc|sess | b73t | 1521 | +737 | +0.13 | -0.12 | -0.33 |
| ARR|BRK|3m | rt | 7013 | +735 | -0.03 | -0.37 | +0.07 |
## 12. EQL|EQL_tight|5m (equal lows, tight 1.0 pt, 5-min bars) - the flagged family: band, episodes, phases, placebos, books, definition, audit, base flip

**1. Noise band (Z3 final lock-off band, n=107: flip 2 % / flip 5 % of live rows): L6M 0.16 / 0.21, PRE 0.22 / 0.26, X' 0.15 / 0.25.** The cell changes 2,062 rows of ~25,800 live rows (about 8 %), so the flip-5 band applies (flip-2 shown in brackets).

| cell (V13X lock None) | cut L6M | band | cut PRE | band | cut X' | band | above band? |
|--|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m D40 skip | +0.14 | 0.21 (0.16) | +0.11 | 0.26 (0.22) | +0.41 | 0.25 (0.15) | X |
| EQL|EQL_tight|5m D20 skip | +0.08 | 0.21 (0.16) | +0.08 | 0.26 (0.22) | +0.31 | 0.25 (0.15) | X |
| FIB|ote705_dn|15m D20 skip | +0.17 | 0.21 (0.16) | +0.11 | 0.26 (0.22) | +0.07 | 0.25 (0.15) | none |
| MAS|bb_mid|4h D20 skip | +0.12 | 0.21 (0.16) | +0.07 | 0.26 (0.22) | +0.11 | 0.25 (0.15) | none |
| SWG|f3L|15s D40 half | +0.45 | 0.21 (0.16) | +0.06 | 0.26 (0.22) | +0.41 | 0.25 (0.15) | L6M, X |

Rule: a cut counts only above the band in L6M AND in PRE or X'. EQL tight D40: L6M +0.14 and PRE +0.11 sit BELOW the band; only X' +0.41 is above. By the rule it is NOISE in L6M (fails the rule), with X' the one window that clears the band.

**2. Leave-one-episode-out with the lock-None key episodes of DS3_ZONES_EPISODES.md (cut with that episode's weeks removed from both series)**

| cell | window | cut | drop ep1 | drop ep2 | drop ep3 | trough week |
|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m D40 | L6M | +0.14 | -0.05 | +0.14 | +0.14 | 202634 |
| EQL|EQL_tight|5m D40 | PRE | +0.11 | +0.02 | +0.11 | +0.11 | 202516 |
| EQL|EQL_tight|5m D40 | X | +0.41 |  |  |  | 202337 |
| EQL|EQL_tight|5m D20 | L6M | +0.08 | -0.03 | +0.08 | +0.08 | 202634 |
| EQL|EQL_tight|5m D20 | PRE | +0.08 | -0.00 | +0.08 | +0.08 | 202516 |
| EQL|EQL_tight|5m D20 | X | +0.31 |  |  |  | 202337 |
| FIB|ote705_dn|15m D20 | L6M | +0.17 | +0.07 | +0.17 | +0.17 | 202634 |
| FIB|ote705_dn|15m D20 | PRE | +0.11 | +0.02 | +0.20 | +0.11 | 202516 |
| FIB|ote705_dn|15m D20 | X | +0.07 |  |  |  | 202337 |
| MAS|bb_mid|4h D20 | L6M | +0.12 | +0.02 | +0.12 | +0.12 | 202634 |
| MAS|bb_mid|4h D20 | PRE | +0.07 | +0.09 | +0.07 | +0.07 | 202516 |
| MAS|bb_mid|4h D20 | X | +0.11 |  |  |  | 202337 |

**3. Phase-averaged cut (Z3 estimator: lock week key shifted by s = -2..+2 label days, K=5 phases; V13X)**

| cell | lock | window | cut by phase s=-2,-1,0,+1,+2 | mean over phases | min |
|--|--|--|--|--|--|
| EQL|EQL_tight|5m D40 | none | L6M | +0.12 +0.12 +0.14 +0.11 +0.13 | +0.12 | +0.11 |
| EQL|EQL_tight|5m D40 | none | PRE | +0.13 +0.05 +0.11 +0.11 +0.11 | +0.10 | +0.05 |
| EQL|EQL_tight|5m D40 | none | X | +0.43 +0.41 +0.41 +0.37 +0.34 | +0.39 | +0.34 |
| EQL|EQL_tight|5m D20 | none | L6M | +0.06 +0.06 +0.08 +0.06 +0.07 | +0.07 | +0.06 |
| EQL|EQL_tight|5m D20 | none | PRE | +0.10 +0.03 +0.08 +0.07 +0.08 | +0.07 | +0.03 |
| EQL|EQL_tight|5m D20 | none | X | +0.37 +0.20 +0.31 +0.32 +0.28 | +0.30 | +0.20 |
| FIB|ote705_dn|15m D20 | none | L6M | +0.10 +0.14 +0.17 +0.14 +0.17 | +0.14 | +0.10 |
| FIB|ote705_dn|15m D20 | none | PRE | +0.19 +0.09 +0.11 +0.16 +0.18 | +0.15 | +0.09 |
| FIB|ote705_dn|15m D20 | none | X | +0.01 -0.11 +0.07 +0.13 +0.09 | +0.04 | -0.11 |
| MAS|bb_mid|4h D20 | none | L6M | +0.08 +0.15 +0.12 +0.09 +0.02 | +0.09 | +0.02 |
| MAS|bb_mid|4h D20 | none | PRE | +0.08 +0.08 +0.07 +0.08 +0.08 | +0.08 | +0.07 |
| MAS|bb_mid|4h D20 | none | X | +0.09 -0.01 +0.11 +0.08 +0.02 | +0.06 | -0.01 |
| SWG|f3L|15s D40 | none | L6M | +0.51 +0.44 +0.45 +0.41 +0.40 | +0.44 | +0.40 |
| SWG|f3L|15s D40 | none | PRE | +0.08 +0.18 +0.06 +0.16 +0.12 | +0.12 | +0.06 |
| SWG|f3L|15s D40 | none | X | +0.39 +0.24 +0.41 +0.46 +0.45 | +0.39 | +0.24 |
| DEV|on_L|so_far D20 | none | L6M | +0.35 +0.52 +0.64 +0.48 +0.49 | +0.50 | +0.35 |
| DEV|on_L|so_far D20 | none | PRE | -0.08 -0.46 -0.21 -0.18 -0.00 | -0.19 | -0.46 |
| DEV|on_L|so_far D20 | none | X | +0.24 +0.07 +0.32 +0.33 +0.28 | +0.25 | +0.07 |
| EQL|EQL_tight|5m D40 | 12 | L6M | +0.12 +0.07 +0.19 +0.02 +0.03 | +0.09 | +0.02 |
| EQL|EQL_tight|5m D40 | 12 | PRE | +0.03 +0.03 -0.11 -0.11 +0.01 | -0.03 | -0.11 |
| EQL|EQL_tight|5m D40 | 12 | X | +0.23 +0.19 -0.02 +0.03 -0.20 | +0.05 | -0.20 |
| EQL|EQL_tight|5m D20 | 12 | L6M | +0.13 +0.07 +0.07 +0.02 +0.04 | +0.06 | +0.02 |
| EQL|EQL_tight|5m D20 | 12 | PRE | +0.05 +0.02 -0.03 -0.08 +0.08 | +0.01 | -0.08 |
| EQL|EQL_tight|5m D20 | 12 | X | +0.19 +0.04 -0.08 -0.05 -0.20 | -0.02 | -0.20 |
| FIB|ote705_dn|15m D20 | 12 | L6M | -0.16 -0.32 -0.03 +0.04 +0.04 | -0.09 | -0.32 |
| FIB|ote705_dn|15m D20 | 12 | PRE | +0.00 -0.04 +0.14 -0.19 -0.07 | -0.03 | -0.19 |
| FIB|ote705_dn|15m D20 | 12 | X | -0.09 -0.14 +0.01 -0.16 -0.17 | -0.11 | -0.17 |
| MAS|bb_mid|4h D20 | 12 | L6M | +0.04 +0.01 -0.04 +0.00 -0.16 | -0.03 | -0.16 |
| MAS|bb_mid|4h D20 | 12 | PRE | +0.01 +0.05 +0.13 +0.03 +0.04 | +0.05 | +0.01 |
| MAS|bb_mid|4h D20 | 12 | X | +0.03 -0.13 -0.10 -0.06 -0.55 | -0.16 | -0.55 |
| SWG|f3L|15s D40 | 12 | L6M | +0.33 +0.35 +0.06 +0.17 +0.27 | +0.24 | +0.06 |
| SWG|f3L|15s D40 | 12 | PRE | -0.06 +0.04 +0.17 +0.05 -0.12 | +0.02 | -0.12 |
| SWG|f3L|15s D40 | 12 | X | +0.33 -0.10 +0.49 +0.69 +0.19 | +0.32 | -0.10 |
| DEV|on_L|so_far D20 | 12 | L6M | +0.08 +0.05 +0.33 -0.06 +0.16 | +0.11 | -0.06 |
| DEV|on_L|so_far D20 | 12 | PRE | -0.25 -0.16 -0.16 +0.03 -0.31 | -0.17 | -0.31 |
| DEV|on_L|so_far D20 | 12 | X | +0.20 +0.29 +0.15 +0.51 -0.03 | +0.22 | -0.03 |

**4. Placebos (V13X lock None; statistic = mean of L6M/HOLD/PRE/X' cuts; A random rows same count per book x session x side x target-half, B same-volume Bernoulli, C shuffled-day circular shift; rank = (1+#>=)/(1+n))**

| cell | cell stat | kind | n | placebo mean | 95th pct | rank |
|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m D40 | +0.19 | A | 300 | -0.023 | +0.099 | 0.003 |
| EQL|EQL_tight|5m D40 | +0.19 | B | 300 | -0.021 | +0.096 | 0.003 |
| EQL|EQL_tight|5m D40 | +0.19 | C | 300 | -0.005 | +0.105 | 0.007 |
| EQL|EQL_tight|5m D20 | +0.14 | A | 300 | -0.016 | +0.087 | 0.013 |
| EQL|EQL_tight|5m D20 | +0.14 | B | 300 | +0.001 | +0.089 | 0.013 |
| EQL|EQL_tight|5m D20 | +0.14 | C | 300 | -0.001 | +0.095 | 0.010 |
| FIB|ote705_dn|15m D20 | +0.13 | A | 40 | -0.027 | +0.095 | 0.049 |
| FIB|ote705_dn|15m D20 | +0.13 | B | 40 | -0.013 | +0.084 | 0.049 |
| FIB|ote705_dn|15m D20 | +0.13 | C | 40 | -0.005 | +0.103 | 0.073 |
| MAS|bb_mid|4h D20 | +0.09 | A | 100 | -0.009 | +0.073 | 0.040 |
| MAS|bb_mid|4h D20 | +0.09 | B | 100 | -0.009 | +0.077 | 0.030 |
| MAS|bb_mid|4h D20 | +0.09 | C | 100 | -0.009 | +0.080 | 0.030 |

**5. EQL tight D40 skip: per book x session (change in $ over HOLD, cut of the book x session maxDD in HOLD | PRE)**

| book | asia | london | pre | nyam | nypm | close |
|--|--|--|--|--|--|--|
| K7 | -5052 (+0.02|-0.02) | -5407 (+0.00|-0.05) |  | +4405 (+0.28|+0.06) | +690 (+0.01|-0.05) |  |
| P7 | +24969 (+0.00|+0.16) | +9427 (-0.13|-0.10) |  | +2937 (+0.00|+0.09) |  |  |
| U7 | +8354 (+0.00|+0.05) | +606 (+0.00|+0.12) |  |  |  |  |
| H7 | +1511 (-0.07|+0.02) |  |  | +2462 (+0.00|-0.11) |  |  |
| M7 |  | -384 (+0.04|-0.10) |  | -6829 (-0.19|-0.01) |  |  |
| A6 | -776 (+0.00|+0.21) |  |  |  |  |  |

**6. Exact D7-computable definition of EQL|EQL_tight|5m ('equal lows, tight, 5-minute')**

* Bars: 5-minute bars of the back-adjusted 1-s path (bar = 300 s, label by open; bar k is *closed* at its last second; ek of a bar = the SS index of the first print second after the bar's close).
* Swing lows: fractal-5 (strength 2): bar j is a swing low if its low is strictly lower than the lows of the 2 bars before and the 2 bars after; it is CONFIRMED when bar j+2 has closed.
* Equal lows (tight): for each confirmed swing low j2 (value v2) look back over the previous 8 confirmed swing lows (j1 with value v1, nearest first); the first j1 with |v1 - v2| <= 1.0 pt and with no bar low strictly between j1 and j2 below min(v1,v2) - 1.0 pt makes an 'equal-lows' level = min(v1, v2). Knowable at the close of bar j2+2 (ek). One level per j2.
* Life: valid from ek until the first second whose low (SL) trades to or below the level ('touched', end) or 24 hours (cap = max(86400 s, 10 x 300 s)). FRESH = never touched since ek, evaluated at the signal second.
* Neutral line (direction 0): it counts AHEAD for either side: for a trade with side s and entry E, the level L is ahead when it lies between the entry and the target, i.e. 0 <= s*(L - E) <= td (for a short, an equal-lows pool below the entry).
* Rule tested: AHEAD D = 40 pts (and 20): if the nearest fresh equal-lows level lies within D pts of the entry in the travel direction (and before the target), SKIP the trade (core books; the shipped 7-line HALF layer is unchanged). Fires on 2,062 of 88,490 rows (about 2.3 % of planned lot volume) at D40, 1,094 rows at D20.

**7. 100-row causal audit (out/zones3_new/s4a_eql_audit100.csv)**: 100 random fired rows (all books incl. library books DN/MA/PBL/ST/WT that D7 does not run; core-book rows are 62 of 100). Per row: (a) the stream row's ek <= signal second; (b) never traded through between ek and the signal second (min SL over (ek, kin] > level); (c) an independent rebuild of the equal lows from the 5-min bars (swing + equality rule above) reproduces the (ek, level) pair; (d) the distance equals the feature. Result: 100 of 100 OK; line age at the signal 0 s to 79441 s (median 16830 s, cap 86,400 s).

**8. Why the L6M cut moved 0.46 (v1.1) -> 0.31 (assumed v1.3, U7 off) -> 0.04 (assumed v1.3 WITH the all-books U7 blackout) -> 0.14 (V13X lock None; -0.54 with lock 12)**

The skip removes the same 2,062 rows each time; what changes is the base path. Weekly-delta decomposition of L6M (cell minus base, $): v1.1: base maxDD 136k (weeks 202628..202637), delta inside that episode +63k, largest weeks 202631 +52k, 202621 +22k; assumed v1.3 U7 off: base 107k, inside-episode +41k, 202638 -102k (the skip removed a +100k week), 202631 +31k; assumed v1.3 WITH U7: base 94k, inside-episode only +4k (the all-books both-sides blackout already blocks entries after a cut, many of the same rows, so the skip has little left to remove), largest weeks 202621 -14k, 202619 +10k; V13X lock 12: base 74k, inside +19k, but 202620 +129k, 202625 +44k, 202640 +37k outside the episode make the cell maxDD 114k (cut -0.54); V13X lock None: base 133k (weeks 202628..202634), inside +19k, 202637 +27k, 202623 -26k, cell 114k (cut +0.14). So the same ~+19k to +63k of rows inside the one W27-39 episode is a 14-46 % cut when the base episode is 136k and a 4 % cut when U7 has already thinned it; the sign flips when the lock and take lines move a +129k week. The cut is a property of one episode and of the lock/take-line stack, which is why it is below the band and flips with the base.

**9. D scan, lock None, skip (cut by window; D = pts to the nearest fresh line, any D from 15 to 60)**

| stream | D | cut L6M | HOLD | MID | PRE | X' | mean4 |
|--|--|--|--|--|--|--|--|
| FIB|ote705_dn|15m | 15 | +0.16 | +0.16 | -0.09 | +0.02 | -0.10 | +0.06 |
| FIB|ote705_dn|15m | 20 | +0.17 | +0.15 | -0.02 | +0.11 | +0.07 | +0.13 |
| FIB|ote705_dn|15m | 25 | +0.07 | +0.07 | +0.03 | +0.08 | +0.01 | +0.06 |
| FIB|ote705_dn|15m | 30 | +0.15 | +0.15 | +0.02 | +0.10 | -0.00 | +0.10 |
| FIB|ote705_dn|15m | 35 | +0.18 | +0.18 | +0.02 | +0.07 | -0.13 | +0.08 |
| FIB|ote705_dn|15m | 40 | +0.22 | +0.22 | +0.02 | +0.09 | -0.25 | +0.07 |
| FIB|ote705_dn|15m | 50 | +0.17 | +0.17 | +0.20 | +0.08 | -0.36 | +0.02 |
| FIB|ote705_dn|15m | 60 | +0.24 | +0.24 | +0.20 | +0.08 | -0.31 | +0.06 |
| EQL|EQL_tight|5m | 15 | +0.05 | +0.05 | +0.01 | +0.03 | +0.32 | +0.11 |
| EQL|EQL_tight|5m | 20 | +0.08 | +0.08 | +0.01 | +0.08 | +0.31 | +0.14 |
| EQL|EQL_tight|5m | 25 | +0.07 | +0.07 | +0.01 | +0.09 | +0.36 | +0.15 |
| EQL|EQL_tight|5m | 30 | +0.12 | +0.10 | +0.01 | +0.08 | +0.37 | +0.17 |
| EQL|EQL_tight|5m | 35 | +0.14 | +0.10 | +0.01 | +0.09 | +0.37 | +0.17 |
| EQL|EQL_tight|5m | 40 | +0.14 | +0.10 | +0.01 | +0.11 | +0.41 | +0.19 |
| EQL|EQL_tight|5m | 50 | +0.13 | +0.13 | +0.06 | +0.05 | +0.45 | +0.19 |
| EQL|EQL_tight|5m | 60 | +0.14 | +0.13 | -0.06 | +0.00 | +0.47 | +0.18 |
| MAS|bb_mid|4h | 15 | +0.07 | +0.07 | +0.09 | +0.03 | +0.16 | +0.08 |
| MAS|bb_mid|4h | 20 | +0.12 | +0.07 | +0.13 | +0.07 | +0.11 | +0.09 |
| MAS|bb_mid|4h | 25 | +0.07 | +0.07 | +0.25 | -0.02 | -0.07 | +0.01 |
| MAS|bb_mid|4h | 30 | -0.06 | -0.06 | +0.22 | +0.08 | +0.13 | +0.02 |
| MAS|bb_mid|4h | 35 | +0.05 | +0.05 | +0.00 | +0.08 | +0.10 | +0.07 |
| MAS|bb_mid|4h | 40 | +0.08 | +0.08 | -0.18 | -0.00 | +0.13 | +0.07 |
| MAS|bb_mid|4h | 50 | +0.10 | +0.10 | -0.36 | -0.12 | +0.29 | +0.09 |
| MAS|bb_mid|4h | 60 | +0.07 | +0.07 | -0.26 | -0.15 | +0.27 | +0.07 |

**6. Exact D7-computable definition of EQL|EQL_tight|5m ('equal lows, tight, 5-minute')**

* Bars: 5-minute bars of the back-adjusted 1-s path (bar = 300 s, label by open; bar k is *closed* at its last second; ek of a bar = the SS index of the first print second after the bar's close).
* Swing lows: fractal-5 (strength 2): bar j is a swing low if its low is strictly lower than the lows of the 2 bars before and the 2 bars after; it is CONFIRMED when bar j+2 has closed.
* Equal lows (tight): for each confirmed swing low j2 (value v2) look back over the previous 8 confirmed swing lows (j1 with value v1, nearest first); the first j1 with |v1 - v2| <= 1.0 pt and with no bar low strictly between j1 and j2 below min(v1,v2) - 1.0 pt makes an 'equal-lows' level = min(v1, v2). Knowable at the close of bar j2+2 (ek). One level per j2.
* Life: valid from ek until the first second whose low (SL) trades to or below the level ('touched', end) or 24 hours (cap = max(86400 s, 10 x 300 s)). FRESH = never touched since ek, evaluated at the signal second.
* Neutral line (direction 0): it counts AHEAD for either side: for a trade with side s and entry E, the level L is ahead when it lies between the entry and the target, i.e. 0 <= s*(L - E) <= td (for a short, an equal-lows pool below the entry).
* Rule tested: AHEAD D = 40 pts (and 20): if the nearest fresh equal-lows level lies within D pts of the entry in the travel direction (and before the target), SKIP the trade (core books; the shipped 7-line HALF layer is unchanged). Fires on 2,062 of 88,490 rows (about 2.3 % of planned lot volume) at D40, 1,094 rows at D20.

**7. 100-row causal audit (out/zones3_new/s4a_eql_audit100.csv)**: 100 random fired rows (all books incl. library books DN/MA/PBL/ST/WT that D7 does not run; core-book rows are 62 of 100). Per row: (a) the stream row's ek <= signal second; (b) never traded through between ek and the signal second (min SL over (ek, kin] > level); (c) an independent rebuild of the equal lows from the 5-min bars (swing + equality rule above) reproduces the (ek, level) pair; (d) the distance equals the feature. Result: 100 of 100 OK; line age at the signal 0 s to 79441 s (median 16830 s, cap 86,400 s).

**8. Why the L6M cut moved 0.46 (v1.1) -> 0.31 (assumed v1.3, U7 off) -> 0.04 (assumed v1.3 WITH the all-books U7 blackout) -> 0.14 (V13X lock None; -0.54 with lock 12)**

The skip removes the same 2,062 rows each time; what changes is the base path. Weekly-delta decomposition of L6M (cell minus base, $): v1.1: base maxDD 136k (weeks 202628..202637), delta inside that episode +63k, largest weeks 202631 +52k, 202621 +22k; assumed v1.3 U7 off: base 107k, inside-episode +41k, 202638 -102k (the skip removed a +100k week), 202631 +31k; assumed v1.3 WITH U7: base 94k, inside-episode only +4k (the all-books both-sides blackout already blocks entries after a cut, many of the same rows, so the skip has little left to remove), largest weeks 202621 -14k, 202619 +10k; V13X lock 12: base 74k, inside +19k, but 202620 +129k, 202625 +44k, 202640 +37k outside the episode make the cell maxDD 114k (cut -0.54); V13X lock None: base 133k (weeks 202628..202634), inside +19k, 202637 +27k, 202623 -26k, cell 114k (cut +0.14). So the same ~+19k to +63k of rows inside the one W27-39 episode is a 14-46 % cut when the base episode is 136k and a 4 % cut when U7 has already thinned it; the sign flips when the lock and take lines move a +129k week. The cut is a property of one episode and of the lock/take-line stack, which is why it is below the band and flips with the base.

**9. D scan, lock None, skip (cut by window; D = pts of travel to the nearest fresh line)**

| stream | D | rows fired | cut L6M | HOLD | MID | PRE | X' | mean4 |
|--|--|--|--|--|--|--|--|--|
## 15. D7 V13Y (add-fill ordering fixed) re-run of the leads: V13X ('defect base') -> V13Y

**V13Y base maxDD, lock 12R: L6M 96181, HOLD 102968, MID 30181, PRE 129681, X 69748**

**V13Y base maxDD, lock 12: L6M 52814, HOLD 90366, MID 52299, PRE 282177, X 131521**


### V13Y, lock 12R: cut by D (skip/half as listed)

| stream | action | D | cut L6M | cut HOLD | cut MID | cut PRE | cut X | mean4 | above-band (L6M>.21 & (PRE>.26 or X'>.25)) |
|--|--|--|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m | skip | 15 | -0.02 | +0.02 | -0.09 | +0.01 | +0.16 | +0.04 |  |
| EQL|EQL_tight|5m | skip | 20 | +0.02 | +0.02 | -0.09 | +0.00 | +0.16 | +0.05 |  |
| EQL|EQL_tight|5m | skip | 25 | +0.01 | +0.02 | -0.09 | +0.00 | +0.16 | +0.05 |  |
| EQL|EQL_tight|5m | skip | 30 | +0.08 | +0.01 | -0.10 | +0.01 | +0.16 | +0.07 |  |
| EQL|EQL_tight|5m | skip | 35 | +0.11 | +0.01 | -0.10 | +0.07 | +0.21 | +0.10 |  |
| EQL|EQL_tight|5m | skip | 40 | +0.11 | +0.01 | -0.10 | +0.08 | +0.27 | +0.12 |  |
| EQL|EQL_tight|5m | skip | 50 | +0.12 | +0.05 | +0.03 | -0.06 | +0.33 | +0.11 |  |
| EQL|EQL_tight|5m | skip | 60 | +0.11 | +0.05 | -0.12 | -0.03 | +0.33 | +0.12 |  |
| FIB|ote705_dn|15m | skip | 15 | +0.22 | +0.03 | -0.15 | -0.16 | -0.27 | -0.05 |  |
| FIB|ote705_dn|15m | skip | 20 | +0.27 | -0.09 | -0.54 | -0.15 | -0.15 | -0.03 |  |
| FIB|ote705_dn|15m | skip | 25 | +0.12 | -0.11 | -0.61 | -0.21 | -0.18 | -0.09 |  |
| FIB|ote705_dn|15m | skip | 30 | +0.19 | -0.04 | -0.69 | -0.18 | -0.25 | -0.07 |  |
| FIB|ote705_dn|15m | skip | 35 | +0.25 | -0.08 | -0.57 | -0.21 | -0.32 | -0.09 |  |
| FIB|ote705_dn|15m | skip | 40 | +0.26 | -0.08 | -0.63 | -0.17 | -0.40 | -0.10 |  |
| FIB|ote705_dn|15m | skip | 50 | +0.28 | -0.06 | -0.56 | -0.16 | -0.50 | -0.11 |  |
| FIB|ote705_dn|15m | skip | 60 | +0.22 | -0.05 | -0.78 | -0.17 | -0.44 | -0.11 |  |
| MAS|bb_mid|4h | skip | 15 | +0.05 | -0.00 | +0.02 | +0.02 | +0.14 | +0.05 |  |
| MAS|bb_mid|4h | skip | 20 | +0.20 | -0.04 | -0.09 | +0.02 | +0.15 | +0.08 |  |
| MAS|bb_mid|4h | skip | 25 | +0.18 | -0.00 | +0.02 | -0.02 | -0.19 | -0.01 |  |
| MAS|bb_mid|4h | skip | 30 | -0.00 | +0.05 | -0.04 | -0.01 | +0.06 | +0.02 |  |
| MAS|bb_mid|4h | skip | 35 | +0.15 | +0.13 | -0.11 | -0.01 | -0.02 | +0.07 |  |
| MAS|bb_mid|4h | skip | 40 | +0.15 | +0.13 | -0.24 | -0.01 | -0.03 | +0.06 |  |
| MAS|bb_mid|4h | skip | 50 | +0.21 | +0.14 | -0.71 | -0.07 | +0.01 | +0.07 |  |
| MAS|bb_mid|4h | skip | 60 | +0.18 | +0.15 | -0.51 | -0.11 | +0.02 | +0.06 |  |
| SWG|f3L|15s | half | 15 | +0.44 | +0.16 | -1.30 | +0.00 | +0.19 | +0.19 |  |
| SWG|f3L|15s | half | 20 | +0.44 | +0.10 | -1.11 | -0.36 | +0.26 | +0.11 | YES |
| SWG|f3L|15s | half | 25 | +0.64 | +0.15 | -1.09 | -0.32 | +0.22 | +0.17 |  |
| SWG|f3L|15s | half | 30 | +0.65 | +0.08 | -0.96 | +0.03 | +0.27 | +0.26 | YES |
| SWG|f3L|15s | half | 35 | +0.54 | +0.09 | -1.00 | +0.07 | +0.29 | +0.25 | YES |
| SWG|f3L|15s | half | 40 | +0.44 | +0.12 | -1.09 | +0.05 | +0.29 | +0.22 | YES |
| SWG|f3L|15s | half | 50 | +0.44 | +0.11 | -1.12 | -0.05 | +0.31 | +0.20 | YES |
| SWG|f3L|15s | half | 60 | +0.43 | +0.19 | -0.79 | +0.04 | +0.31 | +0.24 | YES |
| PRF|vwap|day | skip | 15 | +0.11 | -0.05 | -0.14 | -0.01 | -0.02 | +0.01 |  |
| PRF|vwap|day | skip | 20 | -0.28 | -0.19 | -0.08 | +0.03 | -0.04 | -0.12 |  |
| PRF|vwap|day | skip | 25 | -0.27 | -0.19 | -0.03 | +0.04 | +0.01 | -0.10 |  |
| PRF|vwap|day | skip | 30 | -0.30 | -0.22 | -0.29 | -0.02 | +0.01 | -0.13 |  |
| PRF|vwap|day | skip | 35 | -0.40 | -0.31 | -0.19 | -0.08 | +0.01 | -0.19 |  |
| PRF|vwap|day | skip | 40 | -0.36 | -0.27 | -0.01 | +0.05 | +0.00 | -0.14 |  |
| PRF|vwap|day | skip | 50 | -0.40 | -0.31 | -0.17 | -0.28 | +0.03 | -0.24 |  |
| PRF|vwap|day | skip | 60 | -0.37 | -0.28 | -1.48 | -0.11 | +0.03 | -0.18 |  |
| DEV|on_L|so_far | half | 15 | +0.21 | +0.26 | -0.36 | -0.08 | +0.25 | +0.16 |  |
| DEV|on_L|so_far | half | 20 | +0.69 | +0.22 | -0.43 | -0.30 | +0.17 | +0.19 |  |
| DEV|on_L|so_far | half | 25 | +0.61 | +0.20 | -0.56 | -0.40 | +0.14 | +0.14 |  |
| DEV|on_L|so_far | half | 30 | +0.65 | +0.15 | -0.59 | -0.53 | +0.11 | +0.10 |  |
| DEV|on_L|so_far | half | 35 | +0.68 | +0.15 | -0.63 | -0.56 | +0.21 | +0.12 |  |
| DEV|on_L|so_far | half | 40 | +0.68 | +0.08 | -1.03 | -0.61 | +0.21 | +0.09 |  |
| DEV|on_L|so_far | half | 50 | +0.65 | -0.00 | -1.34 | -0.73 | +0.20 | +0.03 |  |
| DEV|on_L|so_far | half | 60 | +0.65 | +0.09 | -1.21 | -0.72 | +0.20 | +0.06 |  |
| ARR|iplFVG|15s | half | 15 | +0.24 | -0.12 | -0.50 | -0.68 | +0.20 | -0.09 |  |
| ARR|iplFVG|15s | half | 20 | +0.26 | +0.00 | -0.22 | -0.61 | +0.28 | -0.01 | YES |
| ARR|iplFVG|15s | half | 25 | +0.21 | +0.02 | -0.28 | -0.46 | +0.19 | -0.01 |  |
| ARR|iplFVG|15s | half | 30 | +0.06 | -0.02 | -0.74 | -0.44 | +0.17 | -0.06 |  |
| ARR|iplFVG|15s | half | 35 | +0.11 | +0.07 | -0.44 | -0.46 | +0.27 | -0.00 |  |
| ARR|iplFVG|15s | half | 40 | +0.16 | +0.17 | -0.29 | -0.50 | +0.32 | +0.04 |  |
| ARR|iplFVG|15s | half | 50 | +0.07 | +0.13 | +0.00 | -0.30 | +0.19 | +0.02 |  |
| ARR|iplFVG|15s | half | 60 | -0.11 | -0.04 | -0.15 | -0.05 | +0.02 | -0.05 |  |

### V13Y, lock 12: cut by D (skip/half as listed)

| stream | action | D | cut L6M | cut HOLD | cut MID | cut PRE | cut X | mean4 | above-band (L6M>.21 & (PRE>.26 or X'>.25)) |
|--|--|--|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m | skip | 15 | -0.01 | -0.05 | +0.01 | +0.03 | -0.00 | -0.01 |  |
| EQL|EQL_tight|5m | skip | 20 | +0.01 | -0.05 | +0.01 | +0.12 | -0.06 | +0.01 |  |
| EQL|EQL_tight|5m | skip | 25 | +0.01 | -0.05 | +0.01 | +0.12 | +0.03 | +0.03 |  |
| EQL|EQL_tight|5m | skip | 30 | +0.01 | -0.05 | +0.01 | +0.11 | +0.02 | +0.02 |  |
| EQL|EQL_tight|5m | skip | 35 | +0.01 | -0.05 | +0.01 | +0.02 | +0.02 | +0.00 |  |
| EQL|EQL_tight|5m | skip | 40 | +0.17 | -0.05 | +0.01 | +0.02 | -0.08 | +0.02 |  |
| EQL|EQL_tight|5m | skip | 50 | +0.17 | -0.05 | -0.07 | +0.05 | +0.05 | +0.06 |  |
| EQL|EQL_tight|5m | skip | 60 | +0.12 | -0.14 | -0.21 | +0.06 | +0.04 | +0.02 |  |
| FIB|ote705_dn|15m | skip | 15 | +0.01 | +0.04 | +0.09 | +0.17 | -0.16 | +0.01 |  |
| FIB|ote705_dn|15m | skip | 20 | +0.01 | +0.20 | +0.11 | +0.16 | -0.23 | +0.03 |  |
| FIB|ote705_dn|15m | skip | 25 | +0.16 | +0.16 | +0.12 | +0.26 | -0.13 | +0.11 |  |
| FIB|ote705_dn|15m | skip | 30 | +0.05 | +0.16 | +0.16 | +0.25 | -0.17 | +0.07 |  |
| FIB|ote705_dn|15m | skip | 35 | +0.16 | +0.08 | +0.19 | +0.20 | +0.02 | +0.12 |  |
| FIB|ote705_dn|15m | skip | 40 | +0.16 | +0.08 | +0.25 | +0.16 | +0.04 | +0.11 |  |
| FIB|ote705_dn|15m | skip | 50 | +0.17 | +0.09 | +0.40 | +0.19 | -0.08 | +0.09 |  |
| FIB|ote705_dn|15m | skip | 60 | +0.17 | +0.09 | +0.53 | +0.03 | -0.36 | -0.02 |  |
| MAS|bb_mid|4h | skip | 15 | +0.01 | +0.00 | +0.11 | +0.12 | -0.06 | +0.02 |  |
| MAS|bb_mid|4h | skip | 20 | +0.01 | +0.00 | +0.16 | +0.11 | -0.06 | +0.02 |  |
| MAS|bb_mid|4h | skip | 25 | -0.16 | +0.00 | +0.25 | -0.04 | -0.10 | -0.08 |  |
| MAS|bb_mid|4h | skip | 30 | -0.13 | +0.03 | +0.25 | -0.04 | -0.14 | -0.07 |  |
| MAS|bb_mid|4h | skip | 35 | -0.07 | +0.03 | +0.25 | -0.07 | -0.21 | -0.08 |  |
| MAS|bb_mid|4h | skip | 40 | -0.09 | +0.03 | +0.06 | +0.24 | -0.21 | -0.01 |  |
| MAS|bb_mid|4h | skip | 50 | -0.05 | +0.03 | -0.06 | -0.02 | -0.14 | -0.04 |  |
| MAS|bb_mid|4h | skip | 60 | -0.12 | +0.03 | -0.06 | +0.28 | +0.17 | +0.09 |  |
| SWG|f3L|15s | half | 15 | -0.33 | +0.01 | +0.22 | +0.25 | +0.43 | +0.09 |  |
| SWG|f3L|15s | half | 20 | -0.37 | +0.05 | +0.04 | +0.30 | +0.43 | +0.10 |  |
| SWG|f3L|15s | half | 25 | +0.02 | +0.10 | +0.38 | +0.29 | +0.43 | +0.21 |  |
| SWG|f3L|15s | half | 30 | +0.01 | +0.16 | +0.33 | +0.31 | +0.43 | +0.23 |  |
| SWG|f3L|15s | half | 35 | -0.06 | +0.15 | +0.28 | +0.29 | +0.46 | +0.21 |  |
| SWG|f3L|15s | half | 40 | -0.17 | +0.14 | +0.06 | +0.34 | +0.46 | +0.19 |  |
| SWG|f3L|15s | half | 50 | -0.28 | +0.13 | +0.32 | +0.29 | +0.69 | +0.21 |  |
| SWG|f3L|15s | half | 60 | -0.24 | +0.16 | +0.32 | +0.29 | +0.69 | +0.22 |  |
| PRF|vwap|day | skip | 15 | -0.24 | +0.00 | +0.06 | +0.15 | +0.50 | +0.10 |  |
| PRF|vwap|day | skip | 20 | -0.78 | -0.04 | +0.08 | +0.15 | +0.50 | -0.04 |  |
| PRF|vwap|day | skip | 25 | -0.66 | +0.03 | +0.17 | +0.30 | +0.50 | +0.04 |  |
| PRF|vwap|day | skip | 30 | -0.70 | -0.03 | +0.04 | +0.35 | +0.51 | +0.04 |  |
| PRF|vwap|day | skip | 35 | -0.63 | +0.02 | +0.07 | +0.35 | +0.51 | +0.06 |  |
| PRF|vwap|day | skip | 40 | -0.56 | +0.03 | +0.24 | +0.36 | +0.51 | +0.09 |  |
| PRF|vwap|day | skip | 50 | -0.57 | +0.05 | +0.07 | +0.30 | +0.51 | +0.07 |  |
| PRF|vwap|day | skip | 60 | -0.75 | -0.02 | -0.06 | +0.36 | +0.51 | +0.03 |  |
| DEV|on_L|so_far | half | 15 | +0.01 | -0.01 | +0.16 | +0.27 | +0.03 | +0.08 |  |
| DEV|on_L|so_far | half | 20 | +0.01 | +0.02 | +0.26 | -0.08 | +0.05 | -0.00 |  |
| DEV|on_L|so_far | half | 25 | +0.03 | +0.09 | +0.14 | -0.20 | +0.05 | -0.01 |  |
| DEV|on_L|so_far | half | 30 | +0.03 | +0.20 | +0.11 | -0.27 | +0.05 | +0.01 |  |
| DEV|on_L|so_far | half | 35 | +0.29 | +0.11 | +0.08 | -0.25 | +0.06 | +0.05 |  |
| DEV|on_L|so_far | half | 40 | +0.29 | -0.01 | +0.12 | -0.22 | +0.07 | +0.03 |  |
| DEV|on_L|so_far | half | 50 | +0.29 | -0.12 | -0.05 | -0.01 | +0.08 | +0.06 |  |
| DEV|on_L|so_far | half | 60 | +0.31 | -0.02 | -0.07 | +0.06 | +0.08 | +0.11 |  |
| ARR|iplFVG|15s | half | 15 | -0.01 | -0.14 | +0.10 | +0.21 | +0.10 | +0.04 |  |
| ARR|iplFVG|15s | half | 20 | +0.03 | +0.07 | +0.41 | +0.28 | +0.15 | +0.13 |  |
| ARR|iplFVG|15s | half | 25 | +0.03 | -0.00 | +0.23 | +0.32 | +0.38 | +0.18 |  |
| ARR|iplFVG|15s | half | 30 | +0.03 | +0.06 | +0.23 | +0.39 | +0.40 | +0.22 |  |
| ARR|iplFVG|15s | half | 35 | +0.03 | +0.40 | +0.23 | +0.31 | +0.40 | +0.29 |  |
| ARR|iplFVG|15s | half | 40 | +0.03 | +0.17 | +0.26 | +0.29 | +0.43 | +0.23 |  |
| ARR|iplFVG|15s | half | 50 | +0.03 | +0.21 | +0.28 | +0.40 | +0.45 | +0.27 |  |
| ARR|iplFVG|15s | half | 60 | +0.04 | +0.30 | +0.36 | +0.50 | +0.44 | +0.32 |  |
## 13. Is '10 of 24 finalists positive in L6M AND PRE AND X'' above chance? (V13X lock None)

The 24 finalists were picked from the screen as the cells with the best excess cut, so a positive triple is partly selection. Chance reference: the stored information-free placebo series (kinds A, B, C; 900 draws of the 8 top cells, volume 1.3-24 %) were scored the same way; each of the 24 finalists was matched to the placebo cell of nearest volume and one random draw taken; 1,000 repetitions.
* Per-draw probability of a maxDD cut > 0 in all of L6M, PRE and X' for a random same-volume mask: 0.023->0.08, 0.027->0.06, 0.238->0.07 (volume share -> probability; n per cell 300-300).
* Expected count among 24 random finalist-like cells: 1.6 (sd 1.3); observed 16; P(chance count >= observed) = 0.000.
* NB (V13Y): the 24 finalists were selected from cells that are already positive in all three windows, so 'observed 16 of 24' is true by construction and says nothing. The valid test is the whole screen: of the 763 eligible cells (volume 0.5-25 %, >= 300 fires) only 40 (5.2 %) are positive in L6M AND PRE AND X' with lock none, versus a per-draw chance of 5.7-7.7 % for random same-volume masks (expected 43-59): THE SCREEN IS AT OR BELOW CHANCE for this triple.
* Reading (V13X-style comparison, not valid here): 10 of 24 is above the chance count (p<=0.05), but the finalists are best-of-1,272 so the selection effect is not removed by this comparison. The finalists were selected on excess cut, the placebo cells were not; the comparison is therefore generous to the finalists.
"
**METHOD NOTE (program-wide chance benchmark, reusable per family).** Question: is "a cell has a positive maxDD cut in L6M AND PRE AND X'" informative? Procedure: (1) take the family's grid of cells and fix an eligibility rule (here volume share 0.5-25 %, >= 300 fires); count how many eligible cells are positive in the three independent episodes (L6M, PRE, X'; HOLD is not independent of L6M); (2) build information-free cells of the same volume: for 3-8 representative cells draw N >= 100 random masks (kinds: A random rows same count per stratum, B same-volume Bernoulli, C shuffled-day circular shift), run each through the SAME engine and base (V13Y lock none), and record the share positive in all three = the chance rate p3 (here 5.7-7.7 % at volume 2-24 %; per-window rates L6M 0.36-0.54, PRE 0.26-0.54, X' 0.48-0.72); (3) expected count = sum of p3 over the eligible cells (volume-matched), compare with the observed count (here 40 observed vs ~43-59 expected: at or below chance). Never apply it to a set that was selected on the same triple (finalists): the test is on the screen. Code: zones3_new/s4a/chance_y.py reads the stored placebo series (plcyn_res_*.pkl: key (cell, kind, draw) -> daily total) and the base (s2yn_base.pkl); a family needs only its own placebo draws and its eligible-cell table.

## 14. B6: touch-count states of the shipped lines as the AHEAD condition (D20; V13Y fixed base)

Touch = a 1-s print range within 1 tick (0.25) of the line; one touch EVENT = a touching second whose previous second is not touching; counted only for events that start before the entry second (ek-causal). State of a row = touch count of the NEAREST alive ahead line within D20 (and before the target): 0 (untouched), 1, 2+ (two or more). Lines: the shipped 8 (7 half-layer lines + OTE-62) and ALL8 (nearest of the eight). The state is evaluated as an ADDITIONAL layer on top of the shipped V13X layer (HALF: rows not already halved by the shipped layer; SKIP: all fired rows); 'untouched' by this definition is slightly stricter than the store's fresh (the store's fresh also tolerates a print within 1 tick). Band = Z3 final lock-off band, flip-5 value (L6M 0.21, PRE 0.26, X' 0.25); a cut counts only above the band in L6M AND in PRE or X'. No-harm = mean change $/wk over ALL with the paired MDE.

**lock none (headline)**

| line | state | action | fires | vol share | cut L6M | HOLD | MID | PRE | X' | above band (L6M & PRE/X') | d mean ALL $/wk (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| MAS|ich_kijun|1h | 0 | half | 46 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -21 (44) |
| MAS|ich_kijun|1h | 0 | skip | 2409 | 0.026 | +0.12 | +0.01 | +0.06 | +0.02 | +0.06 |  | +354 (941) |
| MAS|ich_kijun|1h | 1 | half | 140 | 0.001 | +0.01 | +0.00 | +0.00 | +0.00 | +0.00 |  | -39 (252) |
| MAS|ich_kijun|1h | 1 | skip | 189 | 0.002 | +0.03 | +0.00 | +0.00 | -0.05 | +0.00 |  | +34 (312) |
| MAS|ich_kijun|1h | 2+ | half | 102 | 0.000 | -0.00 | +0.00 | +0.00 | +0.00 | -0.03 |  | -5 (83) |
| MAS|ich_kijun|1h | 2+ | skip | 120 | 0.001 | +0.03 | +0.00 | +0.00 | -0.00 | -0.10 |  | -38 (224) |
| PDX|day|M | 0 | skip | 1172 | 0.016 | +0.00 | +0.03 | +0.12 | -0.01 | -0.01 |  | -355 (654) |
| PDX|day|M | 1 | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | +44 (251) |
| PDX|day|M | 1 | skip | 104 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | -0.01 |  | +249 (272) |
| PDX|day|M | 2+ | half | 38 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.02 |  | -62 (76) |
| PDX|day|M | 2+ | skip | 52 | 0.001 | +0.00 | +0.00 | +0.00 | +0.01 | -0.04 |  | -162 (178) |
| CRT|M|4h | 0 | skip | 1419 | 0.021 | -0.04 | -0.01 | -0.02 | -0.04 | +0.12 |  | +250 (630) |
| CRT|M|4h | 1 | half | 109 | 0.001 | -0.02 | +0.01 | +0.00 | -0.01 | +0.02 |  | -4 (58) |
| CRT|M|4h | 1 | skip | 164 | 0.002 | -0.12 | -0.05 | -0.06 | -0.01 | +0.09 |  | +20 (208) |
| CRT|M|4h | 2+ | half | 118 | 0.001 | -0.01 | +0.02 | +0.00 | +0.00 | +0.00 |  | -89 (161) |
| CRT|M|4h | 2+ | skip | 146 | 0.002 | -0.02 | +0.04 | +0.00 | -0.02 | +0.03 |  | -144 (291) |
| MAS|kc_up|4h | 0 | skip | 1178 | 0.010 | -0.00 | +0.00 | +0.00 | +0.02 | -0.10 |  | -4 (482) |
| MAS|kc_up|4h | 1 | half | 77 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -43 (87) |
| MAS|kc_up|4h | 1 | skip | 98 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -143 (203) |
| MAS|kc_up|4h | 2+ | half | 47 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.01 |  | -7 (48) |
| MAS|kc_up|4h | 2+ | skip | 55 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.03 |  | -21 (101) |
| PIV|cam_H3|rth | 0 | skip | 1490 | 0.015 | -0.04 | -0.01 | -0.08 | +0.00 | -0.01 |  | +81 (617) |
| PIV|cam_H3|rth | 1 | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.01 | +0.00 |  | -61 (134) |
| PIV|cam_H3|rth | 1 | skip | 93 | 0.001 | +0.00 | +0.00 | +0.00 | +0.02 | +0.00 |  | -164 (274) |
| PIV|cam_H3|rth | 2+ | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -5 (62) |
| PIV|cam_H3|rth | 2+ | skip | 70 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | +10 (155) |
| FIB|ote62_up|15m | 0 | half | 1363 | 0.010 | -0.02 | +0.03 | -0.06 | -0.04 | -0.05 |  | -159 (431) |
| FIB|ote62_up|15m | 0 | skip | 2246 | 0.032 | -0.01 | +0.06 | -0.05 | +0.02 | +0.09 |  | +166 (1055) |
| FIB|ote62_up|15m | 1 | half | 133 | 0.001 | +0.00 | +0.04 | +0.00 | +0.00 | +0.03 |  | +41 (134) |
| FIB|ote62_up|15m | 1 | skip | 195 | 0.002 | -0.00 | +0.07 | +0.00 | +0.00 | +0.07 |  | +57 (343) |
| FIB|ote62_up|15m | 2+ | half | 111 | 0.001 | +0.00 | +0.00 | +0.00 | -0.01 | +0.00 |  | +18 (116) |
| FIB|ote62_up|15m | 2+ | skip | 163 | 0.002 | -0.05 | +0.00 | +0.00 | -0.03 | +0.00 |  | +169 (488) |
| FIB|ote705_up|15m | 0 | skip | 2337 | 0.031 | -0.24 | -0.16 | +0.02 | +0.02 | +0.19 |  | +269 (1028) |
| FIB|ote705_up|15m | 1 | half | 98 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | +13 (112) |
| FIB|ote705_up|15m | 1 | skip | 221 | 0.003 | +0.00 | -0.03 | -0.09 | +0.00 | +0.01 |  | +7 (264) |
| FIB|ote705_up|15m | 2+ | half | 95 | 0.001 | -0.01 | +0.00 | +0.00 | +0.00 | +0.00 |  | +13 (101) |
| FIB|ote705_up|15m | 2+ | skip | 156 | 0.003 | -0.02 | +0.00 | +0.03 | +0.00 | -0.01 |  | -8 (223) |
| FIB|ote79_up|15m | 0 | skip | 2551 | 0.034 | +0.02 | -0.05 | -0.01 | -0.06 | -0.08 |  | -227 (858) |
| FIB|ote79_up|15m | 1 | half | 136 | 0.001 | +0.00 | +0.00 | +0.00 | -0.01 | +0.00 |  | -2 (74) |
| FIB|ote79_up|15m | 1 | skip | 196 | 0.002 | +0.00 | +0.00 | -0.00 | -0.03 | +0.03 |  | +6 (220) |
| FIB|ote79_up|15m | 2+ | half | 162 | 0.001 | -0.01 | +0.00 | +0.00 | +0.00 | +0.02 |  | -11 (123) |
| FIB|ote79_up|15m | 2+ | skip | 190 | 0.002 | -0.06 | +0.01 | +0.00 | -0.01 | +0.17 |  | +42 (369) |
| ALL8 | 0 | half | 1225 | 0.008 | -0.01 | +0.03 | -0.02 | -0.04 | -0.05 |  | -209 (405) |
| ALL8 | 0 | skip | 9641 | 0.115 | -0.24 | -0.16 | -0.16 | -0.07 | +0.03 |  | -724 (1842) |
| ALL8 | 1 | half | 671 | 0.004 | -0.00 | +0.05 | +0.00 | -0.01 | +0.05 |  | +76 (313) |
| ALL8 | 1 | skip | 1017 | 0.012 | -0.02 | +0.05 | -0.14 | -0.06 | +0.14 |  | -14 (676) |
| ALL8 | 2+ | half | 608 | 0.003 | -0.02 | +0.02 | +0.00 | -0.01 | -0.04 |  | -140 (247) |
| ALL8 | 2+ | skip | 785 | 0.010 | -0.08 | -0.01 | +0.07 | -0.04 | -0.06 |  | -116 (719) |

Cells above the band (rule met): none.

**lock 12R**

| line | state | action | fires | vol share | cut L6M | HOLD | MID | PRE | X' | above band (L6M & PRE/X') | d mean ALL $/wk (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| MAS|ich_kijun|1h | 0 | half | 46 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -7 (19) |
| MAS|ich_kijun|1h | 0 | skip | 2409 | 0.026 | -0.07 | +0.11 | +0.28 | -0.04 | +0.04 |  | +57 (891) |
| MAS|ich_kijun|1h | 1 | half | 140 | 0.001 | +0.00 | +0.00 | -0.02 | +0.09 | +0.03 |  | +128 (448) |
| MAS|ich_kijun|1h | 1 | skip | 189 | 0.002 | +0.01 | +0.00 | -0.05 | +0.11 | +0.05 |  | +126 (602) |
| MAS|ich_kijun|1h | 2+ | half | 102 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.00 |  | -10 (52) |
| MAS|ich_kijun|1h | 2+ | skip | 120 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | -0.07 |  | -61 (165) |
| PDX|day|M | 0 | skip | 1172 | 0.016 | -0.04 | -0.01 | +0.13 | +0.08 | +0.01 |  | -316 (987) |
| PDX|day|M | 1 | half | 56 | 0.000 | +0.00 | +0.00 | -0.02 | +0.09 | +0.03 |  | +41 (475) |
| PDX|day|M | 1 | skip | 104 | 0.001 | +0.01 | +0.00 | -0.05 | +0.09 | +0.05 |  | +216 (500) |
| PDX|day|M | 2+ | half | 38 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.00 |  | -18 (43) |
| PDX|day|M | 2+ | skip | 52 | 0.001 | +0.00 | +0.00 | +0.00 | -0.00 | -0.01 |  | -62 (97) |
| CRT|M|4h | 0 | skip | 1419 | 0.021 | -0.09 | +0.01 | +0.26 | +0.18 | +0.26 |  | +965 (1535) |
| CRT|M|4h | 1 | half | 109 | 0.001 | -0.04 | +0.00 | +0.00 | +0.00 | +0.00 |  | -11 (53) |
| CRT|M|4h | 1 | skip | 164 | 0.002 | -0.17 | +0.02 | -0.02 | +0.02 | +0.00 |  | -85 (352) |
| CRT|M|4h | 2+ | half | 118 | 0.001 | -0.01 | -0.00 | +0.00 | +0.00 | -0.30 |  | -388 (1071) |
| CRT|M|4h | 2+ | skip | 146 | 0.002 | -0.04 | -0.00 | +0.00 | -0.01 | -0.28 |  | -411 (1079) |
| MAS|kc_up|4h | 0 | skip | 1178 | 0.010 | +0.00 | +0.00 | +0.00 | -0.06 | +0.24 |  | +645 (1070) |
| MAS|kc_up|4h | 1 | half | 77 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | +21 (128) |
| MAS|kc_up|4h | 1 | skip | 98 | 0.001 | +0.00 | +0.00 | +0.00 | -0.01 | +0.00 |  | -49 (182) |
| MAS|kc_up|4h | 2+ | half | 47 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -14 (44) |
| MAS|kc_up|4h | 2+ | skip | 55 | 0.000 | +0.00 | +0.00 | +0.00 | -0.00 | +0.00 |  | -8 (134) |
| PIV|cam_H3|rth | 0 | skip | 1490 | 0.015 | -0.06 | -0.07 | +0.00 | +0.17 | -0.20 |  | -66 (1512) |
| PIV|cam_H3|rth | 1 | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -67 (134) |
| PIV|cam_H3|rth | 1 | skip | 93 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -52 (239) |
| PIV|cam_H3|rth | 2+ | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | +9 (51) |
| PIV|cam_H3|rth | 2+ | skip | 70 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | +4 (131) |
| FIB|ote62_up|15m | 0 | half | 1363 | 0.010 | +0.01 | +0.01 | +0.01 | -0.02 | -0.06 |  | +331 (1248) |
| FIB|ote62_up|15m | 0 | skip | 2246 | 0.032 | -0.00 | -0.02 | +0.10 | +0.00 | -0.11 |  | +820 (1576) |
| FIB|ote62_up|15m | 1 | half | 133 | 0.001 | +0.00 | +0.00 | +0.00 | +0.01 | +0.00 |  | +16 (69) |
| FIB|ote62_up|15m | 1 | skip | 195 | 0.002 | +0.00 | -0.13 | -0.14 | +0.01 | -0.03 |  | -181 (496) |
| FIB|ote62_up|15m | 2+ | half | 111 | 0.001 | +0.00 | +0.00 | +0.00 | +0.09 | +0.00 |  | +140 (423) |
| FIB|ote62_up|15m | 2+ | skip | 163 | 0.002 | -0.09 | +0.00 | +0.00 | +0.15 | +0.00 |  | +275 (547) |
| FIB|ote705_up|15m | 0 | skip | 2337 | 0.031 | -0.00 | +0.02 | +0.13 | +0.35 | +0.40 |  | +391 (2139) |
| FIB|ote705_up|15m | 1 | half | 98 | 0.001 | +0.01 | +0.00 | +0.00 | +0.00 | +0.00 |  | +43 (92) |
| FIB|ote705_up|15m | 1 | skip | 221 | 0.003 | +0.01 | +0.00 | -0.06 | +0.02 | +0.24 |  | +142 (619) |
| FIB|ote705_up|15m | 2+ | half | 95 | 0.001 | +0.00 | +0.00 | +0.00 | +0.03 | -0.01 |  | +33 (302) |
| FIB|ote705_up|15m | 2+ | skip | 156 | 0.003 | +0.01 | -0.00 | +0.04 | +0.03 | -0.02 |  | +13 (351) |
| FIB|ote79_up|15m | 0 | skip | 2551 | 0.034 | -0.23 | -0.09 | +0.19 | +0.07 | +0.46 |  | +98 (2541) |
| FIB|ote79_up|15m | 1 | half | 136 | 0.001 | +0.00 | +0.00 | +0.00 | +0.01 | +0.01 |  | -99 (296) |
| FIB|ote79_up|15m | 1 | skip | 196 | 0.002 | +0.00 | +0.00 | -0.00 | +0.02 | +0.02 |  | -106 (255) |
| FIB|ote79_up|15m | 2+ | half | 162 | 0.001 | -0.08 | +0.03 | +0.00 | +0.00 | +0.00 |  | -17 (102) |
| FIB|ote79_up|15m | 2+ | skip | 190 | 0.002 | -0.48 | +0.03 | +0.00 | -0.04 | +0.02 |  | -178 (473) |
| ALL8 | 0 | half | 1225 | 0.008 | +0.01 | -0.00 | -0.01 | -0.02 | -0.08 |  | +288 (1230) |
| ALL8 | 0 | skip | 9641 | 0.115 | -0.32 | -0.06 | +0.28 | +0.29 | +0.22 |  | +417 (3596) |
| ALL8 | 1 | half | 671 | 0.004 | -0.00 | +0.00 | -0.02 | +0.11 | +0.03 |  | +130 (489) |
| ALL8 | 1 | skip | 1017 | 0.012 | +0.01 | -0.24 | -0.26 | +0.13 | +0.24 |  | +435 (1262) |
| ALL8 | 2+ | half | 608 | 0.003 | -0.08 | +0.03 | +0.00 | +0.02 | -0.35 |  | -378 (1118) |
| ALL8 | 2+ | skip | 785 | 0.010 | -0.25 | +0.03 | +0.04 | +0.06 | -0.41 |  | -350 (1220) |

Cells above the band (rule met): none.

## 16. EQL|EQL_tight|5m: exact live definition and causal audit (base independent; the stream, the audit and the fired rows do not depend on V13X/V13Y)

* Bars: 5-minute bars of the back-adjusted 1-s path (300 s; a bar is closed at its last second; ek of a bar = the SS index of the first print second after its close).
* Swing lows: fractal-5 (strength 2): bar j is a swing low if its low is strictly below the lows of the 2 bars before and the 2 bars after; CONFIRMED when bar j+2 has closed.
* Equal lows (tight): for each confirmed swing low j2 (value v2) look back over the previous 8 confirmed swing lows (nearest first); the first j1 (value v1) with |v1 - v2| <= 1.0 pt and no bar low between j1 and j2 below min(v1, v2) - 1.0 pt makes a level = min(v1, v2). Knowable at the close of bar j2+2 (ek). One level per j2.
* Life: from ek until the first second whose low trades to or below the level (touched) or 24 h (cap = max(86,400 s, 10 x 300 s)). FRESH = never touched since ek, evaluated at the signal second.
* Neutral line (dr=0): AHEAD for either side when it lies between the entry and the target: 0 <= side*(L - E) <= td. Rule tested: if the nearest fresh equal-lows level is within D (40, and 20) pts of the entry in the travel direction, SKIP the trade (core books; the shipped layer is unchanged). D40 fires on 2,062 of 88,490 rows (about 2.3 % of planned lot volume), D20 on 1,094 rows.
* 100-row causal audit (out/zones3_new/s4a_eql_audit100.csv): 100 random fired rows; per row: stream ek <= signal second; never traded through between ek and the signal second (min of SL over (ek, kin] > level); an independent rebuild of the equal lows from the 5-min bars (swing + equality rule above) reproduces the (ek, level) pair; the distance equals the feature. Result 100 of 100 OK; line age at the signal 0 to 79441 s (median 16830 s, cap 86,400 s); 62 of the 100 rows are core D7 books, the rest library books that D7 does not run.

## 17. Phase-averaged (PA) band and no-harm test of the 24 V13Y finalists (K=9 lock-reset phases, week key shifted -4..+4 label days, Z3 estimator; paired with the shipped layer at the same phase)

PA band = Z3 FINAL V13Y band (DS3_ZONES_3_NOISE.md, 95th pct of |PA paired cut| for a random 2 % / 5 % half-lot flip): lock off L6M .157/.199, HOLD .145/.191, MID .261/.366, PRE .114/.174, X' .159/.230; lock 12R L6M .117/.239, HOLD .112/.117, MID .239/.373, PRE .131/.131, X' .100/.145 (flip 2 used for cells with < 1,000 fired rows, flip 5 otherwise). RULE: PA cut above the band in L6M AND in PRE or X'. NO-HARM (defined here, shared definition not published): no window among L6M/HOLD/MID/PRE/X' has a PA cut below minus its band (no window worsened beyond noise) AND the PA mean change over ALL is not below minus the paired MDE.

**lock off (headline)**

| stream | D | frame | fires | band | PA cut L6M | HOLD | MID | PRE | X' | min over phases L6M/PRE/X' | rule met | no-harm | PASS |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| SWG|f3L|15s | 40 | half | 42423 | flip5 | +0.46 | +0.17 | -0.48 | +0.16 | +0.27 | +0.39/+0.05/+0.20 | YES | NO |  |
| EQL|EQL_tight|5m | 40 | skip | 2062 | flip5 | +0.09 | +0.08 | +0.01 | +0.05 | +0.26 | +0.08/-0.02/+0.25 |  | yes |  |
| MAS|bb_up|1h | 20 | skip | 3120 | flip5 | +0.14 | +0.14 | +0.16 | +0.02 | +0.03 | +0.12/-0.08/+0.02 |  | yes |  |
| SES|asia_H|prev | 20 | skip | 1282 | flip5 | +0.11 | +0.09 | +0.08 | +0.04 | +0.22 | +0.09/+0.01/+0.19 |  | yes |  |
| MAS|ema50|1d | 40 | skip | 516 | flip2 | +0.15 | +0.12 | +0.02 | +0.02 | +0.04 | +0.14/-0.02/+0.02 |  | yes |  |
| MAS|bb_mid|4h | 20 | skip | 1298 | flip5 | +0.16 | +0.12 | -0.01 | +0.04 | +0.12 | +0.06/-0.02/+0.04 |  | yes |  |
| MAS|bb_lo|1h | 40 | half | 4531 | flip5 | +0.24 | +0.20 | +0.11 | +0.05 | +0.11 | +0.15/-0.03/-0.12 |  | yes |  |
| SES|asia_H|prev | 40 | skip | 2695 | flip5 | +0.08 | +0.07 | -0.58 | +0.05 | +0.09 | +0.03/-0.00/+0.07 |  | NO |  |
| EQL|EQL_tight|5m | 40 | half | 2062 | flip5 | +0.03 | +0.03 | +0.01 | +0.03 | +0.18 | +0.03/-0.01/+0.16 |  | yes |  |
| SES|nypm_H|prev | 20 | skip | 1056 | flip5 | +0.12 | +0.11 | +0.09 | +0.01 | +0.14 | +0.06/+0.00/+0.04 |  | yes |  |
| PIV|cam_H3|week | 40 | skip | 1058 | flip5 | +0.02 | +0.02 | -0.01 | +0.00 | +0.19 | +0.01/-0.01/+0.10 |  | yes |  |
| SES|asia_H|prev | 40 | half | 2695 | flip5 | +0.05 | +0.04 | -0.11 | +0.02 | +0.07 | +0.03/+0.00/+0.05 |  | yes |  |
| ARR|iplFVG|3m | 20 | half | 9328 | flip5 | +0.10 | +0.07 | -0.09 | +0.02 | +0.15 | -0.06/-0.07/+0.12 |  | yes |  |
| MAS|supertrend|4h | 40 | half | 1328 | flip5 | +0.05 | +0.05 | +0.09 | +0.02 | +0.09 | +0.00/-0.05/+0.06 |  | yes |  |
| FIB|ret38|4h | 40 | skip | 2546 | flip5 | +0.09 | +0.06 | -0.11 | +0.08 | -0.03 | +0.06/-0.03/-0.11 |  | yes |  |
| SES|close_H|prev | 20 | skip | 1942 | flip5 | +0.10 | +0.09 | -0.12 | -0.01 | +0.07 | +0.04/-0.14/+0.01 |  | yes |  |
| DEV|on_L|so_far | 20 | half | 10884 | flip5 | +0.53 | +0.23 | -0.35 | -0.26 | +0.16 | +0.38/-0.63/+0.10 |  | NO |  |
| SWG|f3L|3m | 20 | half | 19378 | flip5 | +0.47 | +0.36 | -0.67 | -0.10 | +0.31 | +0.37/-0.42/+0.10 | YES | NO |  |
| SWG|f5L|3m | 20 | half | 15731 | flip5 | +0.28 | +0.28 | -0.22 | -0.01 | +0.27 | +0.24/-0.06/+0.06 | YES | yes | PASS |
| SWG|f7L|3m | 20 | half | 13233 | flip5 | +0.42 | +0.26 | -0.20 | -0.02 | +0.09 | +0.34/-0.08/-0.12 |  | yes |  |
| DEV|sess_L|so_far | 20 | half | 22088 | flip5 | +0.56 | +0.21 | -0.62 | -0.11 | -0.13 | +0.52/-0.46/-0.37 |  | NO |  |
| SWG|f3L|15s | 20 | half | 37498 | flip5 | +0.48 | +0.21 | -0.56 | -0.11 | +0.22 | +0.42/-0.36/+0.10 |  | NO |  |
| SWG|f7L|15s | 20 | half | 29604 | flip5 | +0.54 | +0.11 | -1.09 | +0.04 | +0.04 | +0.40/-0.18/-0.13 |  | NO |  |
| MAS|bb_lo|1h | 40 | skip | 4531 | flip5 | +0.28 | +0.18 | +0.16 | -0.00 | +0.17 | +0.21/-0.12/+0.08 |  | yes |  |

Cells meeting the PA band rule: 3; passing band rule AND no-harm: 1.

**lock 12R**

| stream | D | frame | fires | band | PA cut L6M | HOLD | MID | PRE | X' | min over phases L6M/PRE/X' | rule met | no-harm | PASS |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| SWG|f3L|15s | 40 | half | 42423 | flip5 | +0.38 | +0.23 | -0.09 | +0.08 | +0.40 | -0.17/-0.20/+0.29 | YES | yes | PASS |
| EQL|EQL_tight|5m | 40 | skip | 2062 | flip5 | +0.08 | +0.08 | +0.07 | -0.02 | +0.14 | -0.02/-0.16/-0.08 |  | yes |  |
| MAS|bb_up|1h | 20 | skip | 3120 | flip5 | +0.06 | +0.08 | +0.12 | +0.00 | +0.17 | -0.00/-0.56/-0.29 |  | yes |  |
| SES|asia_H|prev | 20 | skip | 1282 | flip5 | +0.08 | +0.07 | -0.04 | +0.02 | +0.03 | +0.02/-0.01/-0.03 |  | yes |  |
| MAS|ema50|1d | 40 | skip | 516 | flip2 | +0.01 | -0.01 | +0.06 | -0.00 | -0.04 | -0.00/-0.06/-0.13 |  | yes |  |
| MAS|bb_mid|4h | 20 | skip | 1298 | flip5 | +0.02 | +0.00 | +0.07 | +0.09 | +0.04 | -0.08/+0.04/-0.07 |  | yes |  |
| MAS|bb_lo|1h | 40 | half | 4531 | flip5 | -0.05 | -0.00 | -0.04 | +0.01 | +0.04 | -0.11/-0.12/-0.11 |  | yes |  |
| SES|asia_H|prev | 40 | skip | 2695 | flip5 | +0.06 | -0.01 | -0.64 | +0.07 | +0.03 | -0.08/+0.00/-0.23 |  | NO |  |
| EQL|EQL_tight|5m | 40 | half | 2062 | flip5 | -0.01 | -0.01 | +0.01 | -0.02 | +0.11 | -0.05/-0.14/-0.03 |  | yes |  |
| SES|nypm_H|prev | 20 | skip | 1056 | flip5 | +0.00 | -0.01 | -0.02 | +0.02 | +0.18 | -0.03/-0.18/+0.08 |  | yes |  |
| PIV|cam_H3|week | 40 | skip | 1058 | flip5 | +0.03 | +0.06 | -0.02 | -0.02 | -0.03 | +0.00/-0.05/-0.05 |  | yes |  |
| SES|asia_H|prev | 40 | half | 2695 | flip5 | +0.02 | +0.03 | -0.33 | +0.01 | +0.00 | -0.02/-0.03/-0.05 |  | yes |  |
| ARR|iplFVG|3m | 20 | half | 9328 | flip5 | -0.06 | +0.05 | +0.09 | +0.14 | +0.11 | -0.67/-0.05/-0.07 |  | yes |  |
| MAS|supertrend|4h | 40 | half | 1328 | flip5 | +0.01 | +0.00 | -0.03 | +0.06 | +0.06 | -0.00/+0.00/-0.07 |  | yes |  |
| FIB|ret38|4h | 40 | skip | 2546 | flip5 | +0.04 | +0.10 | +0.08 | +0.06 | -0.07 | -0.08/+0.01/-0.21 |  | yes |  |
| SES|close_H|prev | 20 | skip | 1942 | flip5 | +0.09 | +0.12 | +0.14 | -0.05 | +0.10 | +0.01/-0.38/-0.17 |  | yes |  |
| DEV|on_L|so_far | 20 | half | 10884 | flip5 | +0.16 | +0.04 | -0.34 | -0.03 | +0.21 | +0.01/-0.17/+0.05 |  | yes |  |
| SWG|f3L|3m | 20 | half | 19378 | flip5 | +0.21 | -0.05 | -0.82 | -0.20 | +0.25 | -0.03/-0.66/+0.15 |  | NO |  |
| SWG|f5L|3m | 20 | half | 15731 | flip5 | +0.14 | +0.03 | -0.29 | +0.01 | +0.25 | -0.13/-0.21/+0.09 |  | yes |  |
| SWG|f7L|3m | 20 | half | 13233 | flip5 | +0.18 | +0.14 | -0.11 | +0.03 | +0.18 | -0.07/-0.11/-0.31 |  | yes |  |
| DEV|sess_L|so_far | 20 | half | 22088 | flip5 | +0.14 | -0.01 | -0.48 | +0.03 | +0.32 | -0.08/-0.09/+0.21 |  | NO |  |
| SWG|f3L|15s | 20 | half | 37498 | flip5 | +0.10 | +0.10 | -0.38 | -0.01 | +0.40 | -0.37/-0.14/+0.29 |  | NO |  |
| SWG|f7L|15s | 20 | half | 29604 | flip5 | +0.13 | +0.09 | -0.50 | +0.06 | +0.35 | -0.33/-0.14/+0.29 |  | NO |  |
| MAS|bb_lo|1h | 40 | skip | 4531 | flip5 | -0.00 | -0.04 | +0.09 | -0.10 | +0.04 | -0.31/-0.27/-0.07 |  | yes |  |

Cells meeting the PA band rule: 1; passing band rule AND no-harm: 1.

## 18. D x0.5 / 0.75 / 1.0 / 1.25 / 1.5 sensitivity on V13Y for the 7 lead cells (nearest grid D of 15,20,25,30,35,40,50,60), single path, mean cut L6M/HOLD/PRE/X'

| cell | D | lock | x0.5 | x0.75 | x1.0 | x1.25 | x1.5 | works at <=1 of 5 D (FRAGILE)? |
|--|--|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m skip | 40 | none | +0.05 | +0.07 | +0.12 | +0.11 | +0.12 |  |
| EQL|EQL_tight|5m skip | 40 | 12 | +0.01 | +0.02 | +0.02 | +0.06 | +0.02 | FRAGILE |
| EQL|EQL_tight|5m skip | 20 | none | +0.04 | +0.04 | +0.05 | +0.05 | +0.07 | FRAGILE |
| EQL|EQL_tight|5m skip | 20 | 12 | -0.01 | -0.01 | +0.01 | +0.03 | +0.02 | FRAGILE |
| FIB|ote705_dn|15m skip | 20 | none | -0.05 | -0.05 | -0.03 | -0.09 | -0.07 | FRAGILE |
| FIB|ote705_dn|15m skip | 20 | 12 | +0.01 | +0.01 | +0.03 | +0.11 | +0.07 |  |
| MAS|bb_mid|4h skip | 20 | none | +0.05 | +0.05 | +0.08 | -0.01 | +0.02 |  |
| MAS|bb_mid|4h skip | 20 | 12 | +0.02 | +0.02 | +0.02 | -0.08 | -0.07 | FRAGILE |
| SWG|f3L|15s half | 40 | none | +0.11 | +0.26 | +0.22 | +0.20 | +0.24 |  |
| SWG|f3L|15s half | 40 | 12 | +0.10 | +0.23 | +0.19 | +0.21 | +0.22 |  |
| PRF|vwap|day skip | 20 | none | +0.01 | +0.01 | -0.12 | -0.10 | -0.13 | FRAGILE |
| PRF|vwap|day skip | 20 | 12 | +0.10 | +0.10 | -0.04 | +0.04 | +0.04 |  |
| DEV|on_L|so_far half | 20 | none | +0.16 | +0.16 | +0.19 | +0.14 | +0.10 |  |
| DEV|on_L|so_far half | 20 | 12 | +0.08 | +0.08 | -0.00 | -0.01 | +0.01 |  |
| ARR|iplFVG|15s half | 40 | none | -0.01 | -0.06 | +0.04 | +0.02 | -0.05 | FRAGILE |
| ARR|iplFVG|15s half | 40 | 12 | +0.13 | +0.22 | +0.23 | +0.27 | +0.32 |  |
## 19. PRE-REGISTERED T3: mechanical two-episode requirement on the 24 V13Y finalists (lock none; prereg sha256 396e7256...)

Carrying episode = the base's episode 1 of the window (L6M weeks 202627-202638, PRE 202434-202451, X' 202321-202341). SURVIVES in a window if the full cut > 0 AND the cut with that episode removed > 0. TWO-EPISODE-OK = survives in at least 2 of L6M/PRE/X'.

| stream | D | frame | cut L6M (drop ep1) | cut PRE (drop ep1) | cut X' (drop ep1) | verdict |
|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m | 40 | skip | +0.11 (-0.18) | +0.08 (+0.04) | +0.27 (-0.06) | ONE-EPISODE |
| SES|asia_H|prev | 20 | skip | +0.12 (+0.02) | +0.07 (+0.04) | +0.22 (+0.02) | TWO-EPISODE-OK |
| MAS|bb_mid|4h | 20 | skip | +0.20 (+0.00) | +0.02 (+0.04) | +0.15 (-0.35) | ONE-EPISODE |
| SES|asia_H|prev | 40 | skip | +0.09 (+0.03) | +0.05 (+0.00) | +0.14 (-0.07) | TWO-EPISODE-OK |
| SES|nypm_H|prev | 20 | skip | +0.14 (-0.06) | +0.00 (+0.00) | +0.04 (-0.04) | ONE-EPISODE |
| SES|asia_H|prev | 40 | half | +0.08 (+0.00) | +0.03 (-0.00) | +0.12 (+0.04) | ONE-EPISODE |
| MAS|supertrend|4h | 40 | half | +0.04 (+0.00) | +0.03 (-0.01) | +0.10 (+0.00) | ONE-EPISODE |
| SES|close_H|prev | 20 | skip | +0.04 (+0.02) | +0.01 (+0.05) | +0.12 (-0.12) | TWO-EPISODE-OK |
| SWG|f3L|3m | 20 | half | +0.51 (+0.29) | -0.22 (-0.28) | +0.10 (-0.12) | ONE-EPISODE |
| SWG|f7L|3m | 20 | half | +0.34 (+0.19) | -0.07 (-0.12) | -0.12 (-0.36) | ONE-EPISODE |
| SWG|f3L|15s | 20 | half | +0.44 (+0.38) | -0.36 (-0.42) | +0.26 (+0.24) | TWO-EPISODE-OK |
| MAS|bb_lo|1h | 40 | skip | +0.31 (+0.22) | -0.03 (-0.08) | +0.08 (+0.20) | TWO-EPISODE-OK |
| SWG|f3L|15s | 40 | half | +0.44 (+0.35) | +0.05 (-0.05) | +0.29 (+0.24) | TWO-EPISODE-OK |
| MAS|bb_up|1h | 20 | skip | +0.17 (+0.04) | +0.03 (+0.04) | +0.05 (-0.14) | TWO-EPISODE-OK |
| MAS|ema50|1d | 40 | skip | +0.18 (+0.00) | +0.01 (-0.04) | +0.02 (+0.00) | ONE-EPISODE |
| MAS|bb_lo|1h | 40 | half | +0.15 (+0.04) | +0.06 (+0.02) | +0.18 (+0.09) | TWO-EPISODE-OK |
| EQL|EQL_tight|5m | 40 | half | +0.04 (-0.11) | +0.03 (-0.01) | +0.17 (+0.01) | ONE-EPISODE |
| PIV|cam_H3|week | 40 | skip | +0.02 (-0.00) | +0.02 (-0.01) | +0.19 (+0.00) | ONE-EPISODE |
| ARR|iplFVG|3m | 20 | half | +0.02 (+0.06) | +0.00 (+0.01) | +0.19 (-0.16) | TWO-EPISODE-OK |
| FIB|ret38|4h | 40 | skip | +0.10 (-0.27) | +0.10 (+0.06) | +0.02 (-0.59) | ONE-EPISODE |
| DEV|on_L|so_far | 20 | half | +0.69 (+0.21) | -0.30 (-0.36) | +0.17 (-0.14) | ONE-EPISODE |
| SWG|f5L|3m | 20 | half | +0.24 (+0.32) | -0.01 (-0.06) | +0.06 (-0.07) | ONE-EPISODE |
| DEV|sess_L|so_far | 20 | half | +0.70 (+0.38) | -0.17 (-0.22) | -0.37 (-0.20) | ONE-EPISODE |
| SWG|f7L|15s | 20 | half | +0.51 (+0.35) | -0.09 (-0.14) | -0.13 (+0.08) | ONE-EPISODE |

TWO-EPISODE-OK finalists: 9 of 24. CHANCE BENCHMARK: share of the stored kind-B random same-volume placebo series (cells 1138, 359, 569, 1208; n=400) that are TWO-EPISODE-OK by the same rule: 0.052; expected among 24 random finalist-like cells: 1.3 (observed 9).

## 20. PRE-REGISTERED T1 / T2 (prereg sha256 396e7256...; V13Y lock none, PA K=9, Z3 final band; placebos only for PASS)

| test | cell | session | fires | vol share | PA cut L6M | HOLD | MID | PRE | X' | min phase L6M/PRE/X' | rule | no-harm | PASS |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| T1 | EQL|EQL_tight|5m D40 skip | Asia | 588 | 0.011 | +0.10 | +0.08 | +0.05 | -0.01 | -0.04 | +0.09/-0.10/-0.05 |  | yes |  |
| T1 | EQL|EQL_tight|5m D40 skip | London | 733 | 0.008 | +0.00 | +0.00 | -0.01 | +0.03 | +0.18 | +0.00/+0.00/+0.16 |  | yes |  |
| T1 | FIB|ote705_dn|15m D20 skip | Asia | 896 | 0.017 | +0.25 | +0.17 | -0.17 | -0.06 | -0.15 | +0.22/-0.15/-0.18 |  | yes |  |
| T1 | FIB|ote705_dn|15m D20 skip | London | 603 | 0.008 | -0.02 | -0.03 | -0.20 | -0.03 | +0.01 | -0.03/-0.09/-0.02 |  | yes |  |
| T1 | FIB|ote705_dn|15m D40 skip | Asia | 1766 | 0.036 | +0.17 | +0.08 | -0.35 | -0.03 | -0.20 | +0.08/-0.12/-0.44 |  | yes |  |
| T1 | FIB|ote705_dn|15m D40 skip | London | 1136 | 0.017 | -0.10 | -0.09 | -0.13 | -0.05 | -0.00 | -0.19/-0.12/-0.03 |  | yes |  |
| T1 | SWG|f3L|15s D20 half | Asia | 9597 | 0.091 | +0.25 | +0.15 | +0.04 | -0.73 | +0.15 | +0.19/-1.02/-0.16 |  | NO |  |
| T1 | SWG|f3L|15s D20 half | London | 9264 | 0.062 | +0.19 | +0.14 | -0.61 | +0.17 | +0.04 | +0.11/+0.06/+0.03 |  | NO |  |
| T1 | SWG|f3L|15s D40 half | Asia | 10419 | 0.098 | +0.21 | +0.15 | -0.20 | -0.47 | +0.16 | +0.16/-0.62/-0.16 |  | NO |  |
| T1 | SWG|f3L|15s D40 half | London | 10214 | 0.069 | +0.12 | +0.12 | -0.38 | +0.16 | +0.06 | +0.03/+0.06/+0.04 |  | NO |  |
| T1 | SWG|f3L|3m D20 half | Asia | 5264 | 0.050 | -0.01 | -0.00 | +0.02 | -0.37 | +0.21 | -0.17/-0.73/+0.08 |  | NO |  |
| T1 | SWG|f3L|3m D20 half | London | 5106 | 0.035 | +0.15 | +0.15 | -0.42 | +0.12 | +0.10 | +0.07/+0.00/+0.09 |  | NO |  |
| T1 | SWG|f3L|3m D40 half | Asia | 7152 | 0.069 | +0.39 | +0.24 | -0.22 | -0.44 | +0.23 | +0.28/-0.72/+0.10 |  | NO |  |
| T1 | SWG|f3L|3m D40 half | London | 7090 | 0.051 | +0.09 | +0.08 | -0.51 | +0.16 | +0.05 | -0.10/+0.05/+0.05 |  | NO |  |
| T2 | POOL D20 half | all | 36171 | 0.211 | +0.66 | +0.31 | -0.93 | -0.14 | +0.20 | +0.60/-0.40/+0.03 |  | NO |  |
| T2 | POOL D40 half | all | 48074 | 0.288 | +0.34 | +0.12 | -0.77 | -0.45 | -0.00 | +0.10/-0.63/-0.13 |  | NO |  |

PASS cells: 0 of 16; cells positive in the PA triple (L6M, PRE, X'): 4 of 16.

**Chance benchmark (kind-B random masks at the cell volume, session-restricted for T1; share positive in L6M AND PRE AND X' on the single path, lock none)**

| benchmark cell | n | share positive in triple | share L6M>0 | PRE>0 | X>0 |
|--|--|--|--|--|--|
| EQL|EQL_tight|5m D40 skip Asia | 100 | 0.070 | 0.50 | 0.29 | 0.44 |
| EQL|EQL_tight|5m D40 skip London | 100 | 0.100 | 0.47 | 0.51 | 0.42 |
| SWG|f3L|3m D20 half Asia | 100 | 0.000 | 0.45 | 0.03 | 0.56 |
| SWG|f3L|3m D20 half London | 100 | 0.100 | 0.43 | 0.39 | 0.46 |
| SWG|f3L|15s D40 half Asia | 100 | 0.000 | 0.63 | 0.00 | 0.68 |
| SWG|f3L|15s D40 half London | 100 | 0.110 | 0.66 | 0.65 | 0.32 |
| POOL D20 | 100 | 0.080 | 0.75 | 0.19 | 0.60 |
| POOL D40 | 100 | 0.230 | 0.81 | 0.41 | 0.71 |

T1 benchmark reading: the 14 T1 cells are compared with the benchmark share above (expected positives = 14 x benchmark share).

## 21. Best cells re-run on D7 V13Z (V13Y + nfix: take-line fill-basis artefact removed), lock off PA K=9 and lock 12R single path

| cell | PA cut L6M | HOLD | MID | PRE | X' | min phase L6M/PRE/X' | band rule | lock12 single-path L6M/HOLD/MID/PRE/X' |
|--|--|--|--|--|--|--|--|--|
| EQL|EQL_tight|5m D40 skip | +0.15 | +0.15 | +0.01 | +0.07 | +0.24 | +0.10/+0.06/+0.22 |  | +0.36 -0.06 +0.00 -0.03 -0.08 |
| SWG|f3L|15s D40 half | +0.37 | +0.36 | -0.36 | +0.02 | +0.30 | +0.33/-0.10/+0.09 | YES | +0.15 +0.19 +0.36 +0.38 +0.47 |
| MAS|bb_up|1h D20 skip | +0.09 | +0.09 | +0.04 | +0.01 | +0.01 | +0.06/-0.02/-0.05 |  | +0.03 +0.02 +0.03 +0.40 -0.28 |
| MAS|bb_mid|4h D20 skip | +0.10 | +0.10 | +0.09 | +0.08 | +0.03 | +0.05/+0.07/-0.01 |  | -0.02 +0.02 +0.10 +0.04 -0.01 |
| EQL|EQL_tight|5m D20 skip | +0.09 | +0.09 | +0.00 | +0.08 | +0.17 | +0.06/+0.05/+0.14 |  | +0.08 -0.07 -0.02 +0.10 -0.23 |
| SWG|f5L|3m D20 half | +0.23 | +0.23 | -0.42 | -0.09 | +0.21 | +0.20/-0.17/+0.07 |  | -0.14 -0.09 +0.12 +0.19 +0.11 |
| SES|asia_H|prev D20 skip | +0.07 | +0.07 | +0.00 | +0.08 | +0.22 | +0.05/+0.05/+0.18 |  | +0.09 +0.03 +0.00 +0.03 -0.09 |
## 22. Reproducibility: chance-benchmark draws re-run with fixed integer seeds (prereg addendum 1, seed = 880000 + 1000*bi + k)

| benchmark cell | n new / old | share positive in L6M+PRE+X' new | old | L6M>0 new/old | PRE>0 new/old | X'>0 new/old |
|--|--|--|--|--|--|--|
| EQL tight D40 skip Asia | 100/100 | 0.120 | 0.070 | 0.58/0.50 | 0.37/0.29 | 0.51/0.44 |
| EQL tight D40 skip London | 100/100 | 0.100 | 0.100 | 0.45/0.47 | 0.54/0.51 | 0.51/0.42 |
| SWG f3L 3m D20 half Asia | 100/100 | 0.010 | 0.000 | 0.49/0.45 | 0.04/0.03 | 0.47/0.56 |
| SWG f3L 3m D20 half London | 100/100 | 0.070 | 0.100 | 0.46/0.43 | 0.44/0.39 | 0.42/0.46 |
| SWG f3L 15s D40 half Asia | 100/100 | 0.000 | 0.000 | 0.49/0.63 | 0.01/0.00 | 0.75/0.68 |
| SWG f3L 15s D40 half London | 100/100 | 0.070 | 0.110 | 0.57/0.66 | 0.68/0.65 | 0.26/0.32 |
| POOL D20 half | 100/100 | 0.080 | 0.080 | 0.71/0.75 | 0.20/0.19 | 0.70/0.60 |
| POOL D40 half | 100/100 | 0.270 | 0.230 | 0.81/0.81 | 0.41/0.41 | 0.79/0.71 |

Stability reading: shares from the two independent seed sets differ by sampling error only (binomial SE at n=100 is 0.03-0.05 for shares of 0.05-0.2); the new seeds are reproducible.

## 23. Diagnosis of the MID harm of the four London SWG fractal-low cells (V13Y lock none; MID = 2026-02-07..04-30, 12 ISO weeks)

Base MID: weekly mean +16.4k, weekly SD 38.7k, maxDD 30.2k (trough week 202613; the base's own MID drawdown is small: 2 weeks, W11-W13, depth 30k), so a 0.4-0.6 percentage cut change is only 11-19 $k.

| cell | MID cut | base maxDD > cell $k | maxDD change $k | change / base weekly SD | mean change $k/wk | / base weekly SD | worst weeks (delta $k) | books carrying (sum MID delta $k) | sessions |
|--|--|--|--|--|--|--|--|--|--|
| SWG f3L 15s D20 half London | -0.55 | 30.2 > 46.8 | +16.6 | +0.43 | -5.4 | -0.14 | 202610 -26.6, 202613 -11.8, 202607 -11.3 | P7 -60.3, U7 -6.0, K7 -4.1 | london -65.0, nypm -1.7, asia +0.0 |
| SWG f3L 3m D20 half London | -0.50 | 30.2 > 45.1 | +14.9 | +0.39 | -3.8 | -0.10 | 202610 -18.5, 202613 -15.4, 202618 -8.5 | P7 -33.9, K7 -6.3, U7 -4.6 | london -47.0, nypm -1.7, asia +0.0 |
| SWG f3L 15s D40 half London | -0.38 | 30.2 > 41.6 | +11.4 | +0.30 | -3.4 | -0.09 | 202610 -14.7, 202608 -9.4, 202618 -8.7 | P7 -32.6, U7 -6.7, K7 -4.1 | london -37.6, nypm -1.7, nyam -1.6 |
| SWG f3L 3m D40 half London | -0.63 | 30.2 > 49.2 | +19.1 | +0.49 | -3.5 | -0.09 | 202607 -13.8, 202610 -13.7, 202618 -10.9 | P7 -36.6, K7 -5.6, U7 -4.6 | london -43.2, nypm -1.7, asia +0.0 |
## 8. Not done / named gaps
* Only the AHEAD frame was swept over all 332 streams; BEHIND/AT were run for 19 streams. Placebo draws (16 per kind) are the compute budget; ranks have 0.06 resolution. The purged walk-forward is owned by Z3. 1-s/3-s decision delay was not run (AHEAD skip/half are signal-second decisions; B73/WT/re-target are in section 3). Parameter variants of the line itself (swing strength, profile bin, anchor shifts) are separate streams in the grid (SWG f3/f5/f7, PRF b1-b3, anchors), not re-parameterised. RND and BKS streams were not built. D7 v1.3 profit lines are an agent-built assumption (THP_POLICY_D7.txt not on disk); U7 is an assumption.


## 10. Structural reading and decision delay
* Of the 24 finalists (V13X, lock off) 16 keep a positive maxDD cut in L6M AND PRE AND X' (the three independent episodes); with the combined lock 12 2. The cut depends on which few weeks a line removes, and on the base.
* Decision delay: AHEAD skip/half are evaluated at the signal second on a line knowable earlier (bar-close or prior-period lines) and place no order, so a 1-s/3-s delay changes nothing except the freshness check (tested on the assumed base for PRF|vwap|day: no change). BEHIND restop re-places the stop at the fill and was not delay-tested (named gap).
* maxDD noise band (Z3 DS3_ZONES_3_NOISE.md): not yet applied.
