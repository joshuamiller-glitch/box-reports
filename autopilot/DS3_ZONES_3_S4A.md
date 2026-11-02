# DS3_ZONES_3_S4A - T-ZONES-3 section 4, first half (EVEN-index streams) of the other POI streams: AHEAD / BEHIND / AT frames

**BASE: D7 v1.3 EXACT (V13X, user paste 02:45Z). HEADLINE FRAME = combined stack lock OFF (lock=None: the engine's own per-book 12R week floor and day give-back locks remain), as the lead ordered at 04:30Z; the same cells with the combined 12R lock ON are in the columns marked 'lock12'. A cut that exists only with lock 12 is LOCK-ONLY. The older assumed-base file is DS3_ZONES_3_S4A_ASSUMED_BASE.md.**

STATUS: S4a deliverable written 2026-11-02 08:11Z (interim: BEHIND/AT frames for the 19 best finalist streams; per-cell placebos 16 draws per kind). POST-HOC, Shadow only, no PASS claim, nothing here is a lead until the robustness standard is met; labels below say how far each cell got.
Prereg l2vast/ds3/prereg/ZONES3_S4A_prereg.md sha256 e8d9004f35ecf860d2beaac5372bdd274862c0db1225523eb12a877ac3fcb66d (DECISIONS.md). dead_lookup before: out/zones3_new/s4a_dead_lookup.txt (NOT FOUND for every spec); append_cells after: see end. NEW windows only (code/cap/windows.py): L1M L2M (view, n weeks 5/9) L3M L6M HOLD MID PRE X'. Old-cap numbers are not used.

## 0. Plain verdict

* On the EXACT base with the combined lock off, no even-half stream clears the robustness standard; the screen leads of the assumed base mostly did not carry (base dependence), and many V13X lock-12 cuts disappear with the lock off (LOCK-ONLY). The three independent episodes are L6M, PRE and X' (L6M and HOLD share a trough); the 24 finalists are listed with how many keep a positive cut in all three.
* Finalists with a positive cut in L6M AND PRE AND X' (lock off): 10 of 24; with lock 12 the same count is 6.
  * FIB|ote705_dn|15m D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.13, screen +0.13, placebo ranks A/B/C 0.04/0.03/0.07 (n=155), label -.
  * FIB|ret50|1h D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.11, screen +0.16, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label (L6M/recent only).
  * ARR|iplFVG|15s D40 half: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.09, screen +0.17, placebo ranks A/B/C 0.07/0.07/0.24 (n=40), label (L6M/recent only).
  * EQL|EQL_tight|5m D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.09, screen +0.19, placebo ranks A/B/C 0.00/0.00/0.01 (n=300), label -.
  * MAS|bb_lo|1h D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.07, screen +0.11, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label (L6M/recent only).
  * SES|asia_H|prev D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.07, screen +0.09, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.
  * FIB|ext127|15m D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.07, screen +0.12, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label (L6M/recent only).
  * FIB|dr_high|15m D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.06, screen +0.10, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.

## 1. Data and tie-out

* poi_store_redo has only 143 stream files (PDX, PIV, MAS 1h/4h, FIB 15m, CRT 4h, 3 PRF). The other 109 FIB/MAS/CRT streams and ARR (126), PRF (76), SES, KZ, DEV, OPN, GAP, ORB, SWG, EQL, BOS, WYK were rebuilt on the redo path (poi_gen / poi_adapt UNCHANGED, ARR and PRF from out/confirm_redo/streams) into /mnt/l2/l2vast/ds3_zones3_new/s4_streams (shared with S4b) and features for all 663 streams on the 88,490 D7 engine rows into /mnt/l2/l2vast/ds3_zones3_new/s4_feats.
* Tie to the OLD store on the old windows (44,370 old trades, 8 channels x 663 streams = 235,338,480 cells): 1,061 mismatching cells (0.0005 %), all in 11 streams: 10 month-anchored PDX/PIV|month streams (the last month closes differently at the old cap: 13-38 cells each) and PRF|npoc|day (830 cells). All other 652 streams tie exactly. out/zones3_new/s4a_feature_tie.csv. RND and BKS are not in the registry (named gap).

## 2. Screen (V13X EXACT, lock off, 1,272 distinct masks of 332 streams x D20/40 x half/skip), top 25 by excess cut over the same-volume placebo curve

| # | stream | D | frame | fires | vol | cut L1M | cut L2M | cut L3M | cut L6M | cut HOLD | cut MID | cut PRE | cut X | K | STRICT | TOL | NOW |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | SWG|f3L|15s | 40 | half | 42423 | 0.238 | +0.39 | +0.39 | +0.23 | +0.45 | +0.31 | -0.00 | +0.06 | +0.41 | +0.295 |  |  |  |
| 2 | DEV|on_L|so_far | 20 | half | 10884 | 0.073 | +0.43 | +0.43 | +0.45 | +0.64 | +0.23 | -0.14 | -0.21 | +0.32 | +0.269 | Y | Y | Y |
| 3 | DEV|on_L|so_far | 40 | half | 14378 | 0.100 | +0.25 | +0.25 | +0.45 | +0.67 | +0.17 | -0.04 | -0.38 | +0.40 | +0.223 |  |  | Y |
| 4 | DEV|sess_L|so_far | 20 | half | 22088 | 0.114 | +0.45 | +0.45 | +0.41 | +0.67 | +0.31 | -0.24 | -0.14 | +0.02 | +0.212 |  |  | Y |
| 5 | EQL|EQL_tight|5m | 40 | skip | 2062 | 0.023 | -0.03 | -0.03 | +0.07 | +0.14 | +0.10 | +0.01 | +0.11 | +0.41 | +0.202 |  |  | Y |
| 6 | DEV|day_L|so_far | 20 | half | 15531 | 0.088 | +0.43 | +0.43 | +0.47 | +0.65 | +0.23 | -0.15 | -0.25 | +0.05 | +0.186 |  |  | Y |
| 7 | FIB|ret50|1h | 40 | skip | 3921 | 0.051 | +0.02 | +0.02 | -0.31 | +0.23 | +0.23 | +0.01 | -0.13 | +0.31 | +0.186 |  |  |  |
| 8 | DEV|day_L|so_far | 40 | half | 21611 | 0.130 | +0.25 | +0.25 | +0.45 | +0.69 | +0.12 | +0.04 | -0.43 | +0.33 | +0.165 |  |  | Y |
| 9 | SWG|f5L|15s | 40 | half | 38419 | 0.218 | +0.20 | +0.20 | +0.17 | +0.40 | +0.24 | -0.20 | -0.24 | +0.28 | +0.159 |  |  |  |
| 10 | ARR|iplFVG|15s | 40 | half | 29624 | 0.152 | -0.12 | -0.12 | +0.18 | +0.31 | +0.25 | +0.11 | -0.23 | +0.34 | +0.157 |  |  |  |
| 11 | EQL|EQL_tight|5m | 20 | skip | 1094 | 0.012 | -0.03 | -0.03 | +0.07 | +0.08 | +0.08 | +0.01 | +0.08 | +0.31 | +0.154 | Y | Y | Y |
| 12 | FIB|ote705_dn|15m | 20 | skip | 2237 | 0.031 | +0.07 | +0.07 | -0.07 | +0.17 | +0.15 | -0.02 | +0.11 | +0.07 | +0.145 |  |  |  |
| 13 | FIB|ext127|15m | 20 | skip | 4176 | 0.040 | -0.02 | -0.02 | +0.09 | +0.31 | +0.19 | -0.04 | +0.02 | -0.05 | +0.145 |  |  | Y |
| 14 | MAS|supertrend|1h | 40 | skip | 5469 | 0.046 | +0.16 | +0.02 | +0.16 | +0.18 | +0.05 | -0.05 | +0.22 | -0.00 | +0.140 |  |  |  |
| 15 | DEV|sess_L|so_far | 40 | half | 28769 | 0.161 | +0.32 | +0.32 | +0.37 | +0.54 | +0.19 | -0.16 | -0.40 | +0.27 | +0.140 |  |  |  |
| 16 | ARR|iplFVG|15s | 20 | half | 18272 | 0.091 | -0.11 | -0.11 | -0.07 | +0.30 | +0.06 | +0.02 | -0.24 | +0.38 | +0.137 |  |  |  |
| 17 | MAS|dc_up|4h | 20 | skip | 1407 | 0.014 | -0.07 | -0.07 | +0.07 | +0.05 | +0.05 | +0.00 | -0.01 | +0.38 | +0.135 |  |  | Y |
| 18 | MAS|kc_lo|4h | 40 | skip | 1452 | 0.016 | -0.01 | -0.01 | +0.17 | +0.39 | +0.16 | +0.03 | -0.02 | -0.04 | +0.135 |  |  | Y |
| 19 | MAS|bb_lo|1h | 40 | skip | 4531 | 0.052 | +0.03 | +0.03 | -0.20 | +0.32 | +0.07 | +0.09 | -0.03 | +0.08 | +0.134 |  |  |  |
| 20 | FIB|ext127|15m | 40 | skip | 8369 | 0.095 | -0.16 | -0.16 | +0.15 | +0.36 | -0.01 | -0.08 | -0.05 | +0.18 | +0.132 |  | Y | Y |
| 21 | ARR|FVG_CE|30m | 20 | skip | 4396 | 0.048 | -0.06 | -0.06 | +0.22 | +0.33 | +0.13 | -0.34 | -0.10 | +0.06 | +0.131 |  |  |  |
| 22 | SWG|f7L|15s | 40 | half | 36217 | 0.206 | +0.20 | +0.20 | +0.04 | +0.23 | +0.23 | -0.15 | -0.19 | +0.27 | +0.124 |  |  |  |
| 23 | FIB|dr_high|15m | 20 | skip | 4022 | 0.048 | +0.05 | +0.05 | +0.03 | +0.04 | +0.04 | -0.17 | +0.01 | +0.30 | +0.122 |  |  |  |
| 24 | ARR|iFVG|15s | 20 | half | 27578 | 0.133 | +0.12 | +0.12 | -0.23 | +0.22 | +0.06 | -0.05 | +0.12 | +0.11 | +0.118 |  |  |  |
| 25 | SES|close_H|prev | 40 | skip | 4010 | 0.058 | +0.01 | -0.10 | -0.10 | +0.17 | +0.05 | +0.15 | +0.19 | -0.04 | +0.117 |  |  |  |

cut = 1 - maxDD(cell)/maxDD(base), weekly cumulative. K = mean over L6M/HOLD/PRE/X' of (cut - placebo-curve cut at equal volume share). Base maxDD (v1.3 screen): L1M 36576, L2M 36576, L3M 49867, L6M 132615, HOLD 132615, MID 62624, PRE 178449, X 134776.

## 3. The 24 finalists on V13X lock off, ranked by the equal-risk cut (lock off, mean of L6M/HOLD/PRE/X'); the top 20 across both halves is merged by the lead

Base (v1.3, U7, 12R): maxDD L3M 49867, L6M 132615, HOLD 132615, MID 62624, PRE 178449, X 134776; mean $/wk L3M 16140, L6M 26854, HOLD 23886, MID 10925, PRE 9973, X -1217. Equal-risk = lot-table scale c so that the ALL worst-20 equals the base's (c shown), exact re-run.

| rank | stream | D | frame | vol | cut L6M | HOLD | MID | PRE | X' | ER c | ER cut L6M | HOLD | PRE | X' | ER dmean ALL $/wk | d L6M (MDE) | Calmar L6M base>cell | lock12 cut L6M/PRE | STRICT/TOL/NOW | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | FIB|ote705_dn|15m | 20 | skip | 0.031 | +0.17 | +0.15 | -0.02 | +0.11 | +0.07 | 1.00 | +0.17 | +0.15 | +0.11 | +0.07 | +165 | -43 (3345) | 0.20>0.24 | -0.03/+0.14 | 0/0/0 | untagged |
| 2 | FIB|ret50|1h | 40 | skip | 0.051 | +0.23 | +0.23 | +0.01 | -0.13 | +0.31 | 1.03 | +0.16 | +0.16 | -0.17 | +0.29 | -867 | -375 (4793) | 0.20>0.26 | -0.31/+0.20 | 0/0/0 | (L6M/recent only) |
| 3 | ARR|iplFVG|15s | 40 | half | 0.152 | +0.31 | +0.25 | +0.11 | -0.23 | +0.34 | 1.17 | +0.27 | +0.19 | -0.34 | +0.26 | +492 | -497 (7767) | 0.20>0.29 | +0.33/+0.29 | 0/0/0 | (L6M/recent only) |
| 4 | EQL|EQL_tight|5m | 40 | skip | 0.023 | +0.14 | +0.10 | +0.01 | +0.11 | +0.41 | 1.07 | -0.01 | -0.01 | -0.03 | +0.42 | +773 | +1371 (4567) | 0.20>0.25 | +0.19/-0.11 | 0/0/1 | untagged |
| 5 | MAS|bb_lo|1h | 40 | skip | 0.052 | +0.32 | +0.07 | +0.09 | -0.03 | +0.08 | 1.07 | +0.29 | +0.09 | -0.15 | +0.06 | +204 | -607 (8420) | 0.20>0.29 | +0.09/-0.17 | 0/0/0 | (L6M/recent only) |
| 6 | SES|asia_H|prev | 20 | skip | 0.009 | +0.09 | +0.06 | +0.00 | +0.07 | +0.15 | 1.03 | +0.07 | +0.05 | +0.02 | +0.14 | -148 | -947 (2754) | 0.20>0.21 | +0.17/+0.20 | 0/0/0 | untagged |
| 7 | FIB|ext127|15m | 20 | skip | 0.040 | +0.31 | +0.19 | -0.04 | +0.02 | -0.05 | 1.03 | +0.21 | +0.16 | -0.03 | -0.07 | +342 | +2011 (2856) | 0.20>0.31 | +0.23/+0.17 | 0/0/1 | (L6M/recent only) |
| 8 | FIB|dr_high|15m | 20 | skip | 0.048 | +0.04 | +0.04 | -0.17 | +0.01 | +0.30 | 1.02 | -0.00 | -0.00 | -0.04 | +0.29 | +331 | -1850 (6353) | 0.20>0.20 | -0.28/+0.37 | 0/0/0 | untagged |
| 9 | FIB|ote705_dn|1h | 40 | skip | 0.040 | +0.04 | +0.01 | -0.16 | +0.08 | +0.18 | 1.14 | +0.04 | +0.04 | +0.01 | +0.15 | +1590 | +306 (2237) | 0.20>0.21 | +0.07/+0.18 | 0/1/1 | FRAGILE |
| 10 | MAS|supertrend|1h | 40 | skip | 0.046 | +0.18 | +0.05 | -0.05 | +0.22 | -0.00 | 1.05 | +0.07 | +0.05 | +0.15 | -0.04 | +495 | -496 (5223) | 0.20>0.24 | +0.00/+0.23 | 0/0/0 | FRAGILE |
| 11 | EQL|EQL_tight|5m | 20 | skip | 0.012 | +0.08 | +0.08 | +0.01 | +0.08 | +0.31 | 1.05 | -0.02 | -0.02 | -0.02 | +0.29 | +355 | +435 (3147) | 0.20>0.22 | +0.07/-0.03 | 1/1/1 | untagged |
| 12 | MAS|bb_mid|4h | 20 | skip | 0.013 | +0.12 | +0.07 | +0.13 | +0.07 | +0.11 | 1.08 | +0.06 | +0.06 | -0.05 | +0.10 | +872 | +724 (1386) | 0.20>0.24 | -0.04/+0.13 | 1/1/1 | untagged |
| 13 | DEV|on_L|so_far | 20 | half | 0.073 | +0.64 | +0.23 | -0.14 | -0.21 | +0.32 | 1.20 | +0.59 | -0.02 | -0.62 | +0.17 | +1462 | +2632 (10393) | 0.20>0.62 | +0.33/-0.16 | 1/1/1 | (L6M/recent only) |
| 14 | ARR|iplFVG|15s | 20 | half | 0.091 | +0.30 | +0.06 | +0.02 | -0.24 | +0.38 | 1.15 | +0.10 | +0.05 | -0.41 | +0.31 | +861 | -182 (7285) | 0.20>0.29 | +0.25/+0.02 | 0/0/0 | FRAGILE |
| 15 | DEV|on_L|so_far | 40 | half | 0.100 | +0.67 | +0.17 | -0.04 | -0.38 | +0.40 | 1.19 | +0.49 | -0.04 | -0.66 | +0.25 | +682 | +137 (10987) | 0.20>0.62 | +0.50/-0.42 | 0/0/1 | (L6M/recent only) |
| 16 | SWG|f3L|15s | 40 | half | 0.238 | +0.45 | +0.31 | -0.00 | +0.06 | +0.41 | 1.37 | +0.12 | +0.06 | -0.39 | +0.15 | +192 | -1548 (11462) | 0.20>0.35 | +0.06/+0.17 | 0/0/0 | untagged |
| 17 | ARR|iFVG|15s | 20 | half | 0.133 | +0.22 | +0.06 | -0.05 | +0.12 | +0.11 | 1.23 | +0.11 | -0.05 | -0.14 | +0.01 | +916 | -1821 (7770) | 0.20>0.24 | -0.19/+0.54 | 0/0/0 | (volume effect) |
| 18 | DEV|sess_L|so_far | 20 | half | 0.114 | +0.67 | +0.31 | -0.24 | -0.14 | +0.02 | 1.22 | +0.60 | +0.07 | -0.58 | -0.17 | +546 | +2483 (9953) | 0.20>0.68 | +0.34/-0.15 | 0/0/1 | (L6M/recent only) |
| 19 | SES|close_H|prev | 40 | skip | 0.058 | +0.17 | +0.05 | +0.15 | +0.19 | -0.04 | 1.13 | +0.02 | +0.02 | +0.02 | -0.14 | +1004 | +413 (5043) | 0.20>0.25 | -0.06/+0.05 | 0/0/0 | (L6M/recent only) |
| 20 | PRF|lvn2|day | 40 | half | 0.010 | +0.04 | +0.04 | +0.00 | +0.09 | +0.22 | 1.15 | -0.11 | -0.11 | -0.06 | +0.16 | +1113 | +6 (2440) | 0.20>0.21 | +0.04/+0.05 | 0/0/1 | untagged |
| 21 | DEV|day_L|so_far | 20 | half | 0.088 | +0.65 | +0.23 | -0.15 | -0.25 | +0.05 | 1.19 | +0.46 | -0.01 | -0.63 | -0.13 | +921 | +2515 (10223) | 0.20>0.64 | +0.33/-0.16 | 0/0/1 | (L6M/recent only) |
| 22 | SWG|f5L|15s | 40 | half | 0.218 | +0.40 | +0.24 | -0.20 | -0.24 | +0.28 | 1.29 | +0.16 | -0.02 | -0.48 | -0.06 | +360 | -367 (11595) | 0.20>0.34 | +0.22/+0.18 | 0/0/0 | (L6M/recent only) |
| 23 | DEV|sess_L|so_far | 40 | half | 0.161 | +0.54 | +0.19 | -0.16 | -0.40 | +0.27 | 1.32 | +0.34 | -0.12 | -0.80 | -0.07 | +675 | -740 (11269) | 0.20>0.43 | +0.38/-0.11 | 0/0/0 | (L6M/recent only) |
| 24 | DEV|day_L|so_far | 40 | half | 0.130 | +0.69 | +0.12 | +0.04 | -0.43 | +0.33 | 1.32 | +0.44 | -0.23 | -0.87 | -0.01 | +1114 | +311 (10917) | 0.20>0.65 | +0.50/-0.46 | 0/0/1 | (L6M/recent only) |

## 4. Robustness of the finalists (v1.3 + U7 series; windows L6M and PRE)

| stream | D | frame | trough week base L6M | cut L6M | drop trough week | LOEO min..max | LOMO min..max | boot 5-95% | P(cut>0) | trough PRE | cut PRE | LOEO PRE | LOMO PRE | placebo rank A/B/C (n) | D variants x0.5/.75/1.25/1.5 mean4 cut | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| FIB|ote705_dn|15m | 20 | skip | 202634 | +0.17 | +0.20 | +0.07..+0.07 | -0.07..+0.20 | -0.12..+0.31 | 0.78 | 202516 | +0.11 | +0.02..+0.20 | +0.02..+0.23 | 0.04/0.03/0.07 (155) | +0.07 / +0.06 / +0.06 / +0.10 | untagged |
| FIB|ret50|1h | 40 | skip | 202634 | +0.23 | +0.34 | +0.02..+0.02 | -0.31..+0.42 | -0.45..+0.48 | 0.63 | 202516 | -0.13 | -0.25..-0.05 | -0.40..-0.04 | 1.00/1.00/1.00 (0) | -0.01 / +0.10 / +0.18 / +0.12 | (L6M/recent only) |
| ARR|iplFVG|15s | 40 | half | 202634 | +0.31 | +0.27 | -0.17..-0.17 | +0.14..+0.36 | -0.02..+0.37 | 0.95 | 202516 | -0.23 | -0.23..+0.13 | -0.33..+0.13 | 0.07/0.07/0.24 (40) | +0.13 / +0.12 / +0.13 / +0.12 | (L6M/recent only) |
| EQL|EQL_tight|5m | 40 | skip | 202634 | +0.14 | +0.16 | -0.05..-0.05 | +0.05..+0.20 | -0.05..+0.30 | 0.83 | 202516 | +0.11 | +0.02..+0.11 | -0.04..+0.17 | 0.00/0.00/0.01 (300) | +0.14 / +0.17 / +0.19 / +0.18 | untagged |
| MAS|bb_lo|1h | 40 | skip | 202634 | +0.32 | +0.46 | +0.03..+0.03 | -0.20..+0.54 | -0.27..+0.65 | 0.75 | 202516 | -0.03 | -0.03..+0.05 | -0.03..+0.08 | 1.00/1.00/1.00 (0) | +0.02 / +0.10 / +0.03 / -0.01 | (L6M/recent only) |
| SES|asia_H|prev | 20 | skip | 202634 | +0.09 | +0.10 | +0.00..+0.00 | +0.02..+0.13 | -0.02..+0.18 | 0.75 | 202516 | +0.07 | +0.07..+0.07 | +0.05..+0.16 | 1.00/1.00/1.00 (0) | -0.01 / +0.06 / +0.11 / +0.09 | untagged |
| FIB|ext127|15m | 20 | skip | 202634 | +0.31 | +0.32 | -0.02..-0.02 | +0.09..+0.36 | -0.07..+0.36 | 0.85 | 202516 | +0.02 | -0.09..+0.08 | -0.09..+0.16 | 1.00/1.00/1.00 (0) | -0.01 / +0.08 / +0.14 / +0.06 | (L6M/recent only) |
| FIB|dr_high|15m | 20 | skip | 202634 | +0.04 | +0.03 | +0.05..+0.05 | -0.07..+0.04 | -0.08..+0.05 | 0.62 | 202516 | +0.01 | -0.10..+0.13 | -0.10..+0.13 | 1.00/1.00/1.00 (0) | +0.01 / +0.01 / +0.10 / +0.08 | untagged |
| FIB|ote705_dn|1h | 40 | skip | 202634 | +0.04 | -0.02 | -0.01..-0.01 | -0.05..+0.13 | -0.07..+0.15 | 0.46 | 202516 | +0.08 | -0.02..+0.26 | -0.02..+0.26 | 1.00/1.00/1.00 (0) | -0.06 / -0.03 / +0.06 / +0.09 | FRAGILE |
| MAS|supertrend|1h | 40 | skip | 202634 | +0.18 | +0.15 | +0.16..+0.16 | -0.01..+0.25 | -0.10..+0.26 | 0.87 | 202516 | +0.22 | +0.14..+0.23 | +0.11..+0.29 | 1.00/1.00/1.00 (0) | -0.05 / -0.01 / +0.04 / +0.02 | FRAGILE |
| EQL|EQL_tight|5m | 20 | skip | 202634 | +0.08 | +0.09 | -0.03..-0.03 | +0.05..+0.08 | -0.01..+0.10 | 0.92 | 202516 | +0.08 | -0.00..+0.08 | -0.00..+0.13 | 0.01/0.01/0.01 (300) | +0.03 / +0.11 / +0.15 / +0.17 | untagged |
| MAS|bb_mid|4h | 20 | skip | 202634 | +0.12 | +0.09 | +0.02..+0.02 | +0.08..+0.12 | +0.02..+0.12 | 0.99 | 202516 | +0.07 | +0.07..+0.09 | +0.06..+0.16 | 0.04/0.03/0.03 (100) | +0.07 / +0.08 / +0.01 / +0.02 | untagged |
| DEV|on_L|so_far | 20 | half | 202634 | +0.64 | +0.63 | +0.30..+0.30 | +0.45..+0.70 | +0.45..+0.79 | 1.00 | 202516 | -0.21 | -0.21..+0.35 | -0.25..+0.18 | 0.01/0.01/0.01 (100) | +0.12 / +0.28 / +0.20 / +0.18 | (L6M/recent only) |
| ARR|iplFVG|15s | 20 | half | 202634 | +0.30 | +0.34 | -0.18..-0.18 | -0.07..+0.38 | -0.25..+0.47 | 0.72 | 202516 | -0.24 | -0.24..+0.14 | -0.30..+0.14 | 1.00/1.00/1.00 (0) | -0.03 / -0.02 / +0.14 / +0.12 | FRAGILE |
| DEV|on_L|so_far | 40 | half | 202634 | +0.67 | +0.67 | +0.25..+0.25 | +0.45..+0.71 | +0.29..+0.75 | 1.00 | 202516 | -0.38 | -0.38..+0.22 | -0.38..+0.16 | 1.00/1.00/1.00 (0) | +0.25 / +0.18 / +0.18 / +0.21 | (L6M/recent only) |
| SWG|f3L|15s | 40 | half | 202634 | +0.45 | +0.57 | +0.39..+0.39 | +0.23..+0.50 | +0.19..+0.55 | 1.00 | 202516 | +0.06 | +0.06..+0.41 | -0.02..+0.41 | 0.01/0.01/0.04 (100) | +0.11 / +0.24 / +0.30 / +0.32 | untagged |
| ARR|iFVG|15s | 20 | half | 202634 | +0.22 | +0.29 | +0.06..+0.06 | -0.23..+0.44 | -0.23..+0.47 | 0.83 | 202516 | +0.12 | +0.03..+0.34 | +0.02..+0.34 | 0.41/0.24/0.27 (40) | +0.05 / +0.16 / +0.12 / -0.06 | (volume effect) |
| DEV|sess_L|so_far | 20 | half | 202634 | +0.67 | +0.66 | +0.43..+0.43 | +0.41..+0.70 | +0.41..+0.79 | 1.00 | 202516 | -0.14 | -0.14..+0.26 | -0.21..+0.26 | 1.00/1.00/1.00 (0) | +0.13 / +0.19 / +0.14 / +0.12 | (L6M/recent only) |
| SES|close_H|prev | 40 | skip | 202634 | +0.17 | +0.19 | +0.01..+0.01 | -0.10..+0.22 | -0.10..+0.34 | 0.87 | 202516 | +0.19 | +0.13..+0.19 | -0.02..+0.35 | 1.00/1.00/1.00 (0) | +0.08 / +0.07 / +0.02 / -0.00 | (L6M/recent only) |
| PRF|lvn2|day | 40 | half | 202634 | +0.04 | +0.04 | -0.25..-0.25 | +0.00..+0.10 | -0.15..+0.15 | 0.68 | 202516 | +0.09 | -0.01..+0.26 | -0.01..+0.26 | 1.00/1.00/1.00 (0) | +0.08 / +0.07 / +0.08 / +0.06 | untagged |
| DEV|day_L|so_far | 20 | half | 202634 | +0.65 | +0.63 | +0.30..+0.30 | +0.47..+0.69 | +0.46..+0.78 | 1.00 | 202516 | -0.25 | -0.25..+0.31 | -0.26..+0.14 | 1.00/1.00/1.00 (0) | +0.08 / +0.23 / +0.13 / +0.12 | (L6M/recent only) |
| SWG|f5L|15s | 40 | half | 202634 | +0.40 | +0.49 | +0.20..+0.20 | +0.17..+0.47 | -0.01..+0.52 | 0.93 | 202516 | -0.24 | -0.24..+0.40 | -0.24..+0.34 | 1.00/1.00/1.00 (0) | +0.09 / +0.12 / +0.21 / +0.24 | (L6M/recent only) |
| DEV|sess_L|so_far | 40 | half | 202634 | +0.54 | +0.56 | +0.32..+0.32 | +0.37..+0.69 | +0.32..+0.69 | 1.00 | 202516 | -0.40 | -0.40..+0.36 | -0.53..+0.20 | 1.00/1.00/1.00 (0) | +0.21 / +0.12 / +0.11 / +0.24 | (L6M/recent only) |
| DEV|day_L|so_far | 40 | half | 202634 | +0.69 | +0.67 | +0.25..+0.25 | +0.45..+0.71 | +0.28..+0.76 | 1.00 | 202516 | -0.43 | -0.43..+0.35 | -0.49..+0.10 | 1.00/1.00/1.00 (0) | +0.17 / +0.12 / +0.16 / +0.28 | (L6M/recent only) |

Placebos (V13X lock off, the same engine as the screen): A random levels = same number of random rows per book x session x side x target-half stratum; B same-volume Bernoulli over eligible rows; C shuffled-day line set (circular shift of the fire vector inside each book x session in time order); statistic = mean of the L6M/HOLD/PRE/X' cuts; rank = (1+#placebo >= cell)/(1+n), n = 16 draws so 0.059 is the best achievable rank. Weeks named by ISO key. LOEO = drop each of the 3 largest base drawdown episodes, LOMO = drop each month, 300 month-block bootstrap draws.

## 5. Per book and per session (maxDD cut, HOLD window | PRE window), top 8 finalists; and mean change by vol tercile (HOLD, $ per week)

| stream | D | frame | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | pre | nyam | nypm | close | vol terc lo/mid/hi d$/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| FIB|ote705_dn|15m | 20 | skip | +0.10|-0.01 | +0.11|-0.02 | -0.08|+0.01 | +0.00|-0.03 | -0.12|-0.01 | +0.07|+0.00 | +0.08|+0.08 | -0.05|-0.04 | +0.00|+0.00 | +0.05|+0.09 | +0.17|-0.20 | +0.00|+0.00 | +624/-463/-400 |
| FIB|ret50|1h | 40 | skip | +0.13|+0.09 | +0.12|-0.22 | +0.11|+0.10 | -0.04|-0.50 | -0.04|-0.02 | +0.06|+0.00 | +0.17|-0.02 | +0.06|-0.10 | +0.00|+0.00 | -0.07|-0.05 | -0.01|-0.31 | +0.00|+0.00 | -773/+922/-1072 |
| ARR|iplFVG|15s | 40 | half | +0.07|-0.15 | +0.05|+0.07 | +0.15|+0.26 | -0.03|-0.33 | +0.14|+0.04 | +0.24|+0.03 | +0.18|-0.55 | +0.15|+0.21 | +0.00|+0.00 | +0.31|+0.00 | +0.06|-0.42 | +0.00|+0.00 | +1760/-817/-808 |
| EQL|EQL_tight|5m | 40 | skip | +0.01|-0.01 | +0.00|-0.05 | +0.00|-0.02 | +0.00|+0.02 | -0.10|+0.07 | +0.00|+0.21 | +0.02|+0.03 | -0.02|-0.09 | +0.00|+0.00 | +0.00|+0.00 | +0.01|-0.05 | +0.00|+0.00 | +427/+66/+217 |
| MAS|bb_lo|1h | 40 | skip | -0.03|+0.01 | +0.19|+0.11 | +0.08|+0.02 | -0.33|+0.11 | +0.05|-0.01 | -0.40|+0.00 | +0.01|+0.01 | +0.05|-0.00 | +0.00|+0.00 | +0.03|+0.00 | +0.00|+0.09 | +0.00|+0.00 | +1155/-1372/-457 |
| SES|asia_H|prev | 20 | skip | +0.01|+0.08 | -0.02|+0.07 | +0.04|-0.00 | +0.00|+0.05 | -0.01|+0.02 | +0.00|+0.00 | +0.00|+0.00 | -0.06|+0.02 | +0.00|+0.00 | +0.07|-0.01 | -0.02|+0.16 | +0.00|+0.00 | +26/-569/+3 |
| FIB|ext127|15m | 20 | skip | +0.01|-0.36 | +0.10|-0.17 | -0.06|+0.02 | -0.07|+0.16 | +0.01|+0.07 | -0.31|+0.51 | +0.03|+0.24 | +0.01|-0.08 | +0.00|+0.00 | +0.04|+0.03 | +0.09|-0.24 | +0.00|+0.00 | +892/+362/+144 |
| FIB|dr_high|15m | 20 | skip | +0.06|+0.10 | -0.04|-0.15 | +0.25|+0.06 | +0.18|-0.10 | +0.08|+0.10 | -0.23|+0.18 | -0.15|+0.05 | +0.08|-0.02 | +0.00|+0.00 | +0.06|+0.03 | +0.22|+0.30 | +0.00|+0.00 | -664/+170/-520 |

Sessions: a zone cut that lives in one session only is a different product (Asia carries the stack in 2026). Vol tercile = tercile of the day's mean library target distance (volatility proxy) inside HOLD.

## 6. BEHIND and AT frames (v1.3 + U7; streams = the 19 distinct finalist streams (top 20 ranks); cut vs the v1.3 base)

BEHIND: fresh POI between entry and stop within Db pts; actions skip / half / restop (stop moved to line - 2 ticks, only if tighter than the library stop; core books; re-simulated with the same jrun kernel as the engine, tie-out exact for the six core books; PE NY rows are not re-stopped = approximate; the TH-L2 loss cut interaction on re-stopped rows is approximate). AT: POI within 2 pts of the entry (fresh or touched, ahead or behind): take-only (skip rows not AT inside book x session cells with >= 50 AT rows; volume collapses, read with equal-risk) / sizeup (x1.5).

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
**BEHIND (top 25 by mean of L6M/HOLD/PRE/X' cut)**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| SWG|f3L|15s | BEHIND | 20 | skip | 28732 | +0.21 | +0.21 | +0.03 | +0.14 | +0.52 | -18892 (21066) | 0.08/0.20 |
| ARR|iFVG|15s | BEHIND | 20 | half | 22982 | +0.24 | +0.24 | +0.13 | +0.03 | +0.19 | -6976 (10603) | 0.20/0.20 |
| SWG|f5L|15s | BEHIND | 20 | skip | 24606 | +0.17 | +0.17 | -0.03 | -0.26 | +0.54 | -19778 (20074) | 0.06/0.20 |
| ARR|iFVG|15s | BEHIND | 20 | skip | 27380 | -0.02 | -0.06 | -0.05 | +0.42 | +0.25 | -16575 (18304) | 0.08/0.20 |
| SWG|f3L|15s | BEHIND | 20 | half | 23256 | +0.08 | +0.08 | +0.24 | +0.03 | +0.36 | -10464 (11558) | 0.13/0.20 |
| ARR|iplFVG|15s | BEHIND | 20 | skip | 19340 | +0.07 | +0.07 | -0.05 | +0.14 | +0.22 | -15949 (16634) | 0.09/0.20 |
| ARR|iFVG|15s | BEHIND | 10 | half | 14049 | -0.04 | -0.04 | +0.26 | +0.23 | +0.31 | -3341 (7200) | 0.17/0.20 |
| ARR|iFVG|15s | BEHIND | 10 | skip | 16798 | -0.06 | -0.06 | -0.01 | +0.27 | +0.28 | -4775 (14262) | 0.16/0.20 |
| ARR|iplFVG|15s | BEHIND | 10 | skip | 11300 | -0.02 | -0.02 | +0.12 | +0.00 | +0.36 | -8334 (15066) | 0.14/0.20 |
| ARR|iplFVG|15s | BEHIND | 20 | half | 16924 | -0.00 | -0.00 | +0.16 | +0.01 | +0.31 | -7988 (8315) | 0.14/0.20 |
| SWG|f5L|15s | BEHIND | 20 | half | 19696 | +0.05 | +0.05 | +0.43 | -0.18 | +0.31 | -10891 (11759) | 0.13/0.20 |
| DEV|day_L|so_far | BEHIND | 20 | skip | 1291 | +0.04 | +0.04 | +0.05 | -0.06 | +0.17 | -992 (2642) | 0.20/0.20 |
| DEV|on_L|so_far | BEHIND | 20 | skip | 1233 | +0.04 | +0.04 | +0.05 | -0.06 | +0.17 | -992 (2642) | 0.20/0.20 |
| SWG|f3L|15s | BEHIND | 10 | half | 15751 | -0.00 | -0.00 | +0.16 | -0.01 | +0.17 | -7780 (8637) | 0.14/0.20 |
| EQL|EQL_tight|5m | BEHIND | 20 | skip | 363 | +0.02 | +0.02 | +0.00 | +0.00 | +0.10 | -17 (407) | 0.21/0.20 |
| EQL|EQL_tight|5m | BEHIND | 10 | skip | 67 | +0.00 | +0.00 | +0.00 | +0.00 | +0.10 | +0 (0) | 0.20/0.20 |
| FIB|ret50|1h | BEHIND | 20 | skip | 263 | -0.00 | -0.00 | +0.06 | +0.02 | +0.06 | +250 (648) | 0.20/0.20 |
| EQL|EQL_tight|5m | BEHIND | 20 | half | 209 | +0.01 | +0.01 | +0.00 | +0.03 | +0.03 | -9 (203) | 0.20/0.20 |
| FIB|ret50|1h | BEHIND | 20 | half | 173 | +0.00 | +0.00 | +0.04 | +0.01 | +0.07 | +124 (251) | 0.20/0.20 |
| EQL|EQL_tight|5m | BEHIND | 10 | restop | 67 | +0.00 | +0.00 | +0.00 | +0.00 | +0.06 | +0 (0) | 0.20/0.20 |
| EQL|EQL_tight|5m | BEHIND | 20 | restop | 363 | +0.02 | +0.02 | +0.00 | +0.02 | -0.01 | +129 (338) | 0.21/0.20 |
| DEV|day_L|so_far | BEHIND | 10 | skip | 597 | +0.00 | +0.00 | +0.03 | -0.06 | +0.10 | -988 (1637) | 0.20/0.20 |
| FIB|ret50|1h | BEHIND | 20 | restop | 263 | +0.00 | +0.00 | +0.15 | -0.13 | +0.17 | +285 (701) | 0.21/0.20 |
| DEV|on_L|so_far | BEHIND | 10 | skip | 539 | +0.00 | +0.00 | +0.03 | -0.06 | +0.09 | -988 (1637) | 0.20/0.20 |
| EQL|EQL_tight|5m | BEHIND | 10 | half | 32 | +0.00 | +0.00 | +0.00 | +0.00 | +0.03 | +0 (0) | 0.20/0.20 |

**AT size-up (x1.5 on rows with a POI within 2 pts)**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| FIB|ote705_dn|15m | AT | 2 | sizeup | 573 | +0.25 | +0.13 | -0.08 | -0.14 | +0.03 | +1116 (2750) | 0.28/0.20 |
| EQL|EQL_tight|5m | AT | 2 | sizeup | 1501 | -0.00 | -0.00 | +0.01 | -0.00 | +0.06 | -112 (1773) | 0.20/0.20 |
| FIB|ret50|1h | AT | 2 | sizeup | 672 | +0.01 | +0.01 | +0.01 | -0.04 | +0.07 | +18 (720) | 0.20/0.20 |
| MAS|bb_mid|4h | AT | 2 | sizeup | 357 | +0.01 | +0.01 | -0.03 | -0.09 | +0.01 | -66 (970) | 0.20/0.20 |
| DEV|day_L|so_far | AT | 2 | sizeup | 2561 | +0.01 | +0.01 | -0.10 | -0.13 | -0.01 | +336 (2186) | 0.21/0.20 |
| DEV|on_L|so_far | AT | 2 | sizeup | 2061 | +0.01 | +0.01 | -0.09 | -0.13 | -0.02 | +216 (2227) | 0.21/0.20 |
| MAS|supertrend|1h | AT | 2 | sizeup | 363 | -0.04 | -0.04 | +0.00 | -0.03 | -0.02 | -139 (667) | 0.19/0.20 |
| FIB|ext127|15m | AT | 2 | sizeup | 727 | -0.09 | -0.09 | +0.01 | -0.13 | -0.04 | -539 (1382) | 0.18/0.20 |
| SWG|f5L|15s | AT | 2 | sizeup | 40445 | -0.19 | -0.19 | -0.22 | -0.82 | -0.29 | +8181 (10161) | 0.22/0.20 |
| ARR|iFVG|15s | AT | 2 | sizeup | 43232 | -0.30 | -0.30 | -0.25 | -0.67 | -0.41 | +7275 (10889) | 0.20/0.20 |
| ARR|iplFVG|15s | AT | 2 | sizeup | 45523 | -0.44 | -0.44 | -0.30 | -0.40 | -0.40 | +9595 (12078) | 0.19/0.20 |
| SWG|f3L|15s | AT | 2 | sizeup | 44555 | -0.39 | -0.39 | -0.31 | -1.00 | -0.40 | +8065 (10983) | 0.19/0.20 |

**AT take-only (skip every row not AT in cells with >= 50 AT rows): the volume collapses (rows = skipped rows, 8-50 % of the book), so the cut is mostly volume; read the mean column and Calmar, not the cut. Not a lead.**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| SWG|f5L|15s | AT | 2 | takeonly | 14848 | +0.66 | +0.40 | +0.56 | -0.31 | +0.18 | -6338 (16151) | 0.46/0.20 |
| SWG|f3L|15s | AT | 2 | takeonly | 10744 | +0.31 | +0.31 | +0.47 | -0.03 | +0.03 | -7064 (10315) | 0.22/0.20 |
| FIB|ext127|15m | AT | 2 | takeonly | 12735 | +0.06 | +0.06 | +0.04 | +0.00 | -0.01 | -908 (3907) | 0.21/0.20 |
| FIB|ote705_dn|15m | AT | 2 | takeonly | 7586 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.20/0.20 |
| MAS|bb_mid|4h | AT | 2 | takeonly | 0 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.20/0.20 |
| FIB|ret50|1h | AT | 2 | takeonly | 7521 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.20/0.20 |
| MAS|supertrend|1h | AT | 2 | takeonly | 7565 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.20/0.20 |
| ARR|iFVG|15s | AT | 2 | takeonly | 12071 | +0.31 | +0.31 | +0.23 | +0.08 | +0.04 | -9843 (12640) | 0.19/0.20 |
| ARR|iplFVG|15s | AT | 2 | takeonly | 9780 | +0.14 | -0.00 | +0.05 | +0.12 | +0.05 | -5828 (9708) | 0.18/0.20 |
| EQL|EQL_tight|5m | AT | 2 | takeonly | 33267 | +0.58 | +0.45 | +0.20 | -0.73 | +0.55 | -17426 (26320) | 0.17/0.20 |
| DEV|on_L|so_far | AT | 2 | takeonly | 21541 | +0.09 | +0.09 | -0.20 | -0.45 | +0.41 | -19785 (23907) | 0.06/0.20 |
| DEV|day_L|so_far | AT | 2 | takeonly | 28909 | +0.09 | +0.09 | -0.20 | -0.45 | +0.41 | -19785 (23907) | 0.06/0.20 |

## 7. New lines worth adding, with exact D7-computable definitions

None is yet a RISK-KEEP line. The ones to carry to the merged top 20 as screen LEADS (post-hoc, definitions exact; label shown):

* **FIB|ote705_dn|15m, AHEAD D 20 pts, fresh, action SKIP** (label -). Definition: Dealing range on 15m bars (bars at CLOSE): fractal-5 swing highs/lows (2 bars each side, confirmed 2 bars later); H3 = max of the last 3 confirmed swing highs, L3 = min of the last 3 confirmed swing lows, valid when H3-L3 >= 4 pts. Level = H3 - 0.705*(H3-L3)  (the 0.705 retracement measured down from the dealing-range high). Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 2237 of 88,490 rows (3.1 % of planned lot volume).
* **FIB|ret50|1h, AHEAD D 40 pts, fresh, action SKIP** (label (L6M/recent only)). Definition: Last confirmed fractal-5 leg on 1h bars (H = last swing high, L = last swing low, valid when H-L >= 4): retracement level at 50% of the leg (down leg: L + r*(H-L); up leg: H - r*(H-L)). Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 3921 of 88,490 rows (5.1 % of planned lot volume).
* **ARR|iplFVG|15s, AHEAD D 40 pts, fresh, action HALF** (label (L6M/recent only)). Definition: iplFVG zone on 15s bars (FVG = 3-bar imbalance; iFVG = inverted FVG; iplFVG = implied FVG; OB = order block; BRK = breaker), near edge used for the distance; bar-close knowable (CF-ENG s1 arrays); direction-bearing: counts AHEAD only if it supports the other side. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then scale the planned lots x0.5 (integer half-up, min 1; trades already halved by the shipped 7-line set are not quartered). Fires on 29624 of 88,490 rows (15.2 % of planned lot volume).
* **EQL|EQL_tight|5m, AHEAD D 40 pts, fresh, action SKIP** (label -). Definition: Equal lows (within 1.0 pt) between two fractal-5 swings on 5m bars (one of the last 8 swings, no bar in between exceeding), level = the higher (highs) or lower (lows) of the pair. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 2062 of 88,490 rows (2.3 % of planned lot volume).
* **MAS|bb_lo|1h, AHEAD D 40 pts, fresh, action SKIP** (label (L6M/recent only)). Definition: bb_lo on 1h bars at the last CLOSED bar (EMA/SMA n=50/100/200 of close; Bollinger 20,2 sd; Keltner 20 EMA +/- 2 ATR10; Donchian 20 high/low; Supertrend 10,3; Ichimoku 9/26/52 with spans displaced 26 bars forward). Line value fixed at the bar close until the next bar. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 4531 of 88,490 rows (5.2 % of planned lot volume).
* **SES|asia_H|prev, AHEAD D 20 pts, fresh, action SKIP** (label -). Definition: Previous completed asia window high (ET windows: asia 18-02, london 02-08:30, pre 08:30-09:30, nyam 09:30-12, nypm 12-15, close 15-17, on 18-09:30, rth 09:30-16; killzones asia 20-24, london 02-05, ny 07-10, lc 10-12), knowable at window end. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 1282 of 88,490 rows (0.9 % of planned lot volume).
* **FIB|ext127|15m, AHEAD D 20 pts, fresh, action SKIP** (label (L6M/recent only)). Definition: Last confirmed fractal-5 leg on 15m bars (H-L >= 4): extension at 127% beyond the leg end (down leg: H - r*(H-L); up leg: L + r*(H-L)). Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 4176 of 88,490 rows (4.0 % of planned lot volume).
* **FIB|dr_high|15m, AHEAD D 20 pts, fresh, action SKIP** (label -). Definition: Dealing range on 15m bars as above (fractal-5 swings, last 3 highs/lows, H3-L3 >= 4): level = H3. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 4022 of 88,490 rows (4.8 % of planned lot volume).

The 8 shipped lines and the 3 profile lines are not in this section. L1M/L2M columns are views, never selected on.

## 11. B8: the zone as TARGET (every even-index stream, V13X lock off, post-hoc)

Rule: when the nearest fresh line ahead lies between 4 pts and (target - 4 pts) from the entry, the first leg takes profit at the line; 'b73t' = share F of the lots (the engine's integer split share per book/session, 0.5-0.75) exits at the line and the rest keeps the library target (the OTE-62 B73 idea turned to the target side); 'rt' = all lots exit at the line. Simulated per lot with poi_sim.mkt_run (market entry at the signal price, N basis) and added to the engine's split outcome; exit second/type of the library trade unchanged (the 30% leg keeps the original exit time): APPROXIMATE, PE NY confirmed entries not touched. BASE-4 covers the shipped lines (DS3_B8_ZONE_TARGET_SHIPPED.md).

* 632 (stream, mode) cells scored; mean change in $/wk (ALL) averages -598 for b73t and -939 for rt: re-targeting to a line costs money on average (the library target is usually better than the first line). 132 cells improve the mean; 12 cells have a positive maxDD cut in L6M AND PRE AND X'.

**Top 12 by mean cut (L6M/HOLD/PRE/X')**

| stream | mode | rows | cut L6M | cut HOLD | cut MID | cut PRE | cut X | d L6M (MDE) | d ALL $/wk |
|--|--|--|--|--|--|--|--|--|--|
| ARR|iFVG|1h | rt | 3256 | +0.18 | +0.09 | +0.09 | +0.02 | +0.23 | +1401 (5842) | -558 |
| ARR|FVG_CE|1h | rt | 6368 | +0.13 | +0.13 | -0.09 | -0.05 | +0.27 | -3229 (8084) | +750 |
| ARR|iFVG|1h | b73t | 3256 | +0.09 | +0.09 | +0.12 | +0.06 | +0.18 | +196 (3877) | -542 |
| ARR|FVG|4h | rt | 3055 | +0.41 | -0.06 | -0.28 | +0.17 | -0.12 | +270 (7549) | +129 |
| PIV|cam_H1|rth | b73t | 1956 | +0.19 | +0.17 | +0.00 | +0.25 | -0.20 | +1828 (4481) | +612 |
| ARR|FVG|4h | b73t | 3055 | +0.29 | +0.04 | -0.19 | +0.14 | -0.08 | -21 (5120) | +138 |
| BOS|BOS_dn|1m | b73t | 3383 | +0.11 | +0.06 | +0.04 | +0.01 | +0.20 | -996 (4148) | -599 |
| PRF|hvn0|sess | b73t | 1561 | +0.29 | +0.28 | -0.07 | -0.08 | -0.14 | +3531 (5625) | +856 |
| FIB|dr_low|1d | rt | 124 | +0.31 | +0.07 | -0.00 | +0.00 | -0.04 | +1491 (4239) | +115 |
| ARR|FVG_CE|1h | b73t | 6368 | +0.07 | +0.07 | -0.07 | -0.08 | +0.28 | -2127 (5443) | +337 |
| BOS|BOS_dn|5m | b73t | 1531 | +0.09 | +0.09 | +0.02 | +0.03 | +0.13 | +133 (2444) | +168 |
| ARR|iFVG_CE|1h | b73t | 4527 | +0.10 | +0.10 | +0.13 | +0.01 | +0.10 | +409 (3325) | +292 |

**Top 8 by mean improvement ($/wk, ALL)**

| stream | mode | rows | d ALL $/wk | cut L6M | cut PRE | cut X' |
|--|--|--|--|--|--|--|
| ARR|FVG|1h | rt | 4634 | +1628 | -0.21 | +0.06 | +0.19 |
| FIB|ote705_up|1h | rt | 4713 | +1165 | -0.19 | -0.07 | +0.00 |
| PRF|poc|sess | rt | 1521 | +1057 | +0.19 | -0.07 | -0.19 |
| PRF|poc|sess | b73t | 1521 | +985 | +0.13 | -0.01 | -0.13 |
| ARR|FVG|1h | b73t | 4634 | +923 | -0.17 | +0.03 | +0.20 |
| PRF|hvn0|sess | b73t | 1561 | +856 | +0.29 | -0.08 | -0.14 |
| ARR|BRK|3m | rt | 7013 | +803 | +0.07 | -0.31 | +0.24 |
| FIB|ote705_up|1h | b73t | 4713 | +797 | -0.11 | -0.03 | -0.05 |

**Random-level placebo (same rows, line distance uniform in [4, target-4]), statistic = mean cut L6M/HOLD/PRE/X'**

| cell | cell k4 | placebo mean | 95th pct | n | rank |
|--|--|--|--|--|--|
| ARR|FVG_CE|1h rt | +0.12 | +0.065 | +0.141 | 60 | 0.131 |
| ARR|iFVG|1h b73t | +0.10 | +0.033 | +0.072 | 60 | 0.016 |
| ARR|iFVG|1h rt | +0.13 | +0.015 | +0.067 | 60 | 0.016 |
| PIV|cam_H1|rth b73t | +0.10 | +0.085 | +0.127 | 60 | 0.344 |
| PRF|hvn0|sess b73t | +0.09 | +0.017 | +0.085 | 60 | 0.066 |
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
## 13. Is '10 of 24 finalists positive in L6M AND PRE AND X'' above chance? (V13X lock None)

The 24 finalists were picked from the screen as the cells with the best excess cut, so a positive triple is partly selection. Chance reference: the stored information-free placebo series (kinds A, B, C; 3090 draws of the 8 top cells, volume 1.3-24 %) were scored the same way; each of the 24 finalists was matched to the placebo cell of nearest volume and one random draw taken; 1,000 repetitions.
* Per-draw probability of a maxDD cut > 0 in all of L6M, PRE and X' for a random same-volume mask: 0.012->0.12, 0.013->0.09, 0.023->0.11, 0.031->0.10, 0.073->0.08, 0.133->0.12, 0.152->0.18, 0.238->0.17 (volume share -> probability; n per cell 120-900).
* Expected count among 24 random finalist-like cells: 2.8 (sd 1.5); observed 10; P(chance count >= observed) = 0.000.
* Reading: 10 of 24 is above the chance count (p<=0.05), but the finalists are best-of-1,272 so the selection effect is not removed by this comparison. The finalists were selected on excess cut, the placebo cells were not; the comparison is therefore generous to the finalists.

## 14. B6: touch-count states of the shipped lines as the AHEAD condition (D20; V13X)

Touch = a 1-s print range within 1 tick (0.25) of the line; one touch EVENT = a touching second whose previous second is not touching; counted only for events that start before the entry second (ek-causal). State of a row = touch count of the NEAREST alive ahead line within D20 (and before the target): 0 (untouched), 1, 2+ (two or more). Lines: the shipped 8 (7 half-layer lines + OTE-62) and ALL8 (nearest of the eight). The state is evaluated as an ADDITIONAL layer on top of the shipped V13X layer (HALF: rows not already halved by the shipped layer; SKIP: all fired rows); 'untouched' by this definition is slightly stricter than the store's fresh (the store's fresh also tolerates a print within 1 tick). Band = Z3 final lock-off band, flip-5 value (L6M 0.21, PRE 0.26, X' 0.25); a cut counts only above the band in L6M AND in PRE or X'. No-harm = mean change $/wk over ALL with the paired MDE.

**lock none (headline)**

| line | state | action | fires | vol share | cut L6M | HOLD | MID | PRE | X' | above band (L6M & PRE/X') | d mean ALL $/wk (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| MAS|ich_kijun|1h | 0 | half | 46 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -20 (45) |
| MAS|ich_kijun|1h | 0 | skip | 2409 | 0.026 | +0.09 | +0.09 | +0.31 | -0.04 | -0.02 |  | +243 (830) |
| MAS|ich_kijun|1h | 1 | half | 140 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.02 |  | -44 (252) |
| MAS|ich_kijun|1h | 1 | skip | 189 | 0.002 | +0.03 | +0.03 | +0.00 | +0.01 | +0.02 |  | +38 (310) |
| MAS|ich_kijun|1h | 2+ | half | 102 | 0.000 | +0.03 | +0.03 | +0.00 | +0.00 | -0.02 |  | -5 (83) |
| MAS|ich_kijun|1h | 2+ | skip | 120 | 0.001 | +0.08 | +0.07 | +0.00 | +0.00 | -0.10 |  | -38 (224) |
| PDX|day|M | 0 | skip | 1172 | 0.016 | -0.02 | -0.02 | +0.15 | -0.01 | +0.04 |  | -269 (701) |
| PDX|day|M | 1 | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.01 |  | +44 (251) |
| PDX|day|M | 1 | skip | 104 | 0.001 | +0.01 | +0.01 | +0.00 | +0.00 | +0.01 |  | +248 (271) |
| PDX|day|M | 2+ | half | 38 | 0.000 | +0.00 | +0.00 | +0.00 | -0.01 | -0.02 |  | -62 (76) |
| PDX|day|M | 2+ | skip | 52 | 0.001 | +0.00 | +0.00 | +0.00 | -0.01 | -0.07 |  | -141 (183) |
| CRT|M|4h | 0 | skip | 1419 | 0.021 | -0.01 | -0.01 | +0.24 | -0.06 | +0.10 |  | +64 (858) |
| CRT|M|4h | 1 | half | 109 | 0.001 | -0.01 | -0.01 | +0.00 | +0.00 | +0.01 |  | +2 (51) |
| CRT|M|4h | 1 | skip | 164 | 0.002 | -0.07 | -0.07 | -0.03 | +0.01 | +0.04 |  | +33 (186) |
| CRT|M|4h | 2+ | half | 118 | 0.001 | -0.01 | -0.01 | +0.00 | +0.00 | -0.07 |  | -90 (162) |
| CRT|M|4h | 2+ | skip | 146 | 0.002 | -0.01 | -0.01 | +0.00 | +0.00 | -0.09 |  | -144 (291) |
| MAS|kc_up|4h | 0 | skip | 1178 | 0.010 | +0.01 | +0.01 | +0.00 | -0.02 | -0.12 |  | +101 (488) |
| MAS|kc_up|4h | 1 | half | 77 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -43 (87) |
| MAS|kc_up|4h | 1 | skip | 98 | 0.001 | +0.00 | +0.00 | +0.00 | -0.02 | +0.00 |  | -144 (202) |
| MAS|kc_up|4h | 2+ | half | 47 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.01 |  | -7 (48) |
| MAS|kc_up|4h | 2+ | skip | 55 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.01 |  | -21 (101) |
| PIV|cam_H3|rth | 0 | skip | 1490 | 0.015 | -0.04 | -0.04 | +0.00 | +0.02 | +0.02 |  | +163 (620) |
| PIV|cam_H3|rth | 1 | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -53 (136) |
| PIV|cam_H3|rth | 1 | skip | 93 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -148 (276) |
| PIV|cam_H3|rth | 2+ | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | -0.01 | +0.00 |  | -5 (62) |
| PIV|cam_H3|rth | 2+ | skip | 70 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -5 (147) |
| FIB|ote62_up|15m | 0 | half | 1363 | 0.010 | +0.01 | +0.01 | -0.02 | +0.11 | -0.10 |  | -263 (1047) |
| FIB|ote62_up|15m | 0 | skip | 2246 | 0.032 | +0.05 | +0.05 | +0.06 | +0.20 | +0.07 |  | -54 (1320) |
| FIB|ote62_up|15m | 1 | half | 133 | 0.001 | +0.00 | +0.00 | +0.00 | +0.03 | +0.01 |  | +41 (134) |
| FIB|ote62_up|15m | 1 | skip | 195 | 0.002 | +0.00 | +0.00 | +0.00 | +0.03 | +0.02 |  | +61 (342) |
| FIB|ote62_up|15m | 2+ | half | 111 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | +3 (129) |
| FIB|ote62_up|15m | 2+ | skip | 163 | 0.002 | -0.00 | -0.00 | +0.00 | +0.00 | -0.02 |  | +108 (367) |
| FIB|ote705_up|15m | 0 | skip | 2337 | 0.031 | -0.05 | -0.05 | +0.20 | -0.01 | +0.07 |  | +120 (821) |
| FIB|ote705_up|15m | 1 | half | 98 | 0.001 | +0.01 | +0.01 | +0.00 | +0.00 | +0.00 |  | +24 (119) |
| FIB|ote705_up|15m | 1 | skip | 221 | 0.003 | +0.02 | +0.02 | -0.04 | +0.01 | -0.03 |  | +50 (280) |
| FIB|ote705_up|15m | 2+ | half | 95 | 0.001 | -0.09 | -0.09 | +0.00 | +0.01 | -0.01 |  | -15 (224) |
| FIB|ote705_up|15m | 2+ | skip | 156 | 0.003 | -0.09 | -0.09 | +0.03 | +0.04 | -0.03 |  | -41 (325) |
| FIB|ote79_up|15m | 0 | skip | 2551 | 0.034 | +0.04 | +0.03 | +0.24 | -0.08 | -0.15 |  | -38 (925) |
| FIB|ote79_up|15m | 1 | half | 136 | 0.001 | +0.00 | +0.00 | +0.00 | -0.00 | +0.01 |  | -69 (202) |
| FIB|ote79_up|15m | 1 | skip | 196 | 0.002 | +0.00 | +0.00 | -0.00 | -0.01 | +0.04 |  | -36 (274) |
| FIB|ote79_up|15m | 2+ | half | 162 | 0.001 | -0.03 | -0.03 | +0.00 | -0.01 | +0.01 |  | -10 (124) |
| FIB|ote79_up|15m | 2+ | skip | 190 | 0.002 | -0.07 | -0.07 | +0.00 | -0.02 | +0.10 |  | -16 (294) |
| ALL8 | 0 | half | 1225 | 0.008 | +0.01 | +0.01 | -0.00 | +0.11 | -0.09 |  | -330 (1036) |
| ALL8 | 0 | skip | 9641 | 0.115 | +0.03 | +0.00 | +0.12 | -0.05 | +0.04 |  | -671 (1960) |
| ALL8 | 1 | half | 671 | 0.004 | +0.01 | +0.01 | +0.00 | +0.03 | +0.04 |  | +78 (315) |
| ALL8 | 1 | skip | 1017 | 0.012 | +0.03 | +0.03 | -0.07 | +0.02 | +0.06 |  | +7 (681) |
| ALL8 | 2+ | half | 608 | 0.003 | -0.09 | -0.09 | +0.00 | -0.01 | -0.11 |  | -184 (322) |
| ALL8 | 2+ | skip | 785 | 0.010 | -0.10 | -0.10 | +0.03 | +0.01 | -0.19 |  | -233 (681) |

Cells above the band (rule met): none.

**lock 12R**

| line | state | action | fires | vol share | cut L6M | HOLD | MID | PRE | X' | above band (L6M & PRE/X') | d mean ALL $/wk (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| MAS|ich_kijun|1h | 0 | half | 46 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -7 (19) |
| MAS|ich_kijun|1h | 0 | skip | 2409 | 0.026 | +0.02 | +0.16 | +0.14 | -0.18 | +0.23 |  | +664 (1887) |
| MAS|ich_kijun|1h | 1 | half | 140 | 0.001 | +0.00 | -0.02 | -0.02 | +0.10 | +0.02 |  | -160 (812) |
| MAS|ich_kijun|1h | 1 | skip | 189 | 0.002 | +0.02 | -0.05 | -0.03 | +0.13 | +0.04 |  | -25 (836) |
| MAS|ich_kijun|1h | 2+ | half | 102 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.03 |  | -25 (54) |
| MAS|ich_kijun|1h | 2+ | skip | 120 | 0.001 | +0.00 | +0.00 | +0.00 | +0.02 | -0.09 |  | -70 (172) |
| PDX|day|M | 0 | skip | 1172 | 0.016 | -0.04 | +0.04 | +0.07 | +0.02 | +0.19 |  | +185 (1837) |
| PDX|day|M | 1 | half | 56 | 0.000 | +0.00 | -0.02 | -0.02 | +0.09 | +0.03 |  | +677 (1704) |
| PDX|day|M | 1 | skip | 104 | 0.001 | +0.02 | -0.05 | -0.03 | +0.12 | +0.05 |  | +873 (1776) |
| PDX|day|M | 2+ | half | 38 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | -0.02 |  | -23 (41) |
| PDX|day|M | 2+ | skip | 52 | 0.001 | +0.00 | +0.00 | +0.00 | -0.00 | -0.05 |  | -45 (105) |
| CRT|M|4h | 0 | skip | 1419 | 0.021 | +0.01 | +0.14 | +0.14 | +0.07 | +0.32 |  | +689 (2207) |
| CRT|M|4h | 1 | half | 109 | 0.001 | -0.01 | -0.01 | +0.00 | +0.00 | +0.01 |  | -8 (44) |
| CRT|M|4h | 1 | skip | 164 | 0.002 | -0.09 | -0.01 | +0.00 | +0.03 | +0.05 |  | +24 (169) |
| CRT|M|4h | 2+ | half | 118 | 0.001 | -0.01 | -0.00 | +0.00 | +0.00 | -0.02 |  | -42 (136) |
| CRT|M|4h | 2+ | skip | 146 | 0.002 | -0.03 | -0.00 | +0.00 | -0.01 | -0.03 |  | -50 (211) |
| MAS|kc_up|4h | 0 | skip | 1178 | 0.010 | +0.04 | -0.04 | +0.00 | -0.00 | +0.22 |  | +617 (941) |
| MAS|kc_up|4h | 1 | half | 77 | 0.000 | +0.02 | +0.00 | +0.00 | +0.00 | +0.00 |  | -266 (688) |
| MAS|kc_up|4h | 1 | skip | 98 | 0.001 | +0.02 | +0.00 | +0.00 | -0.01 | +0.00 |  | -340 (710) |
| MAS|kc_up|4h | 2+ | half | 47 | 0.000 | +0.00 | -0.02 | +0.00 | +0.00 | -0.01 |  | -14 (44) |
| MAS|kc_up|4h | 2+ | skip | 55 | 0.000 | +0.00 | -0.04 | +0.00 | -0.00 | -0.01 |  | -16 (120) |
| PIV|cam_H3|rth | 0 | skip | 1490 | 0.015 | -0.06 | -0.11 | +0.00 | +0.12 | +0.20 |  | -133 (1221) |
| PIV|cam_H3|rth | 1 | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | -279 (803) |
| PIV|cam_H3|rth | 1 | skip | 93 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | -0.01 |  | -229 (695) |
| PIV|cam_H3|rth | 2+ | half | 56 | 0.000 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 |  | +14 (50) |
| PIV|cam_H3|rth | 2+ | skip | 70 | 0.001 | +0.00 | +0.00 | +0.00 | +0.00 | -0.01 |  | +29 (97) |
| FIB|ote62_up|15m | 0 | half | 1363 | 0.010 | +0.08 | -0.01 | +0.00 | -0.01 | +0.13 |  | +124 (747) |
| FIB|ote62_up|15m | 0 | skip | 2246 | 0.032 | -0.01 | +0.02 | +0.00 | -0.02 | +0.21 |  | -205 (1484) |
| FIB|ote62_up|15m | 1 | half | 133 | 0.001 | -0.02 | +0.00 | +0.00 | +0.01 | +0.01 |  | +11 (66) |
| FIB|ote62_up|15m | 1 | skip | 195 | 0.002 | -0.04 | -0.10 | -0.10 | +0.01 | +0.08 |  | -244 (748) |
| FIB|ote62_up|15m | 2+ | half | 111 | 0.001 | +0.00 | +0.00 | +0.00 | +0.11 | +0.00 |  | +133 (426) |
| FIB|ote62_up|15m | 2+ | skip | 163 | 0.002 | -0.01 | +0.00 | +0.00 | +0.12 | +0.01 |  | -93 (1057) |
| FIB|ote705_up|15m | 0 | skip | 2337 | 0.031 | -0.02 | +0.31 | -0.01 | +0.13 | +0.32 |  | +937 (2043) |
| FIB|ote705_up|15m | 1 | half | 98 | 0.001 | +0.05 | +0.00 | +0.00 | +0.00 | +0.00 |  | +54 (96) |
| FIB|ote705_up|15m | 1 | skip | 221 | 0.003 | +0.06 | -0.02 | -0.03 | +0.02 | +0.20 |  | +230 (579) |
| FIB|ote705_up|15m | 2+ | half | 95 | 0.001 | +0.00 | +0.00 | +0.00 | +0.06 | -0.01 |  | +111 (267) |
| FIB|ote705_up|15m | 2+ | skip | 156 | 0.003 | +0.01 | +0.02 | +0.03 | +0.06 | -0.02 |  | -371 (1352) |
| FIB|ote79_up|15m | 0 | skip | 2551 | 0.034 | -0.17 | -0.05 | +0.02 | +0.20 | +0.37 |  | +833 (2456) |
| FIB|ote79_up|15m | 1 | half | 136 | 0.001 | +0.00 | +0.00 | +0.00 | +0.01 | +0.00 |  | -66 (197) |
| FIB|ote79_up|15m | 1 | skip | 196 | 0.002 | +0.00 | -0.00 | -0.00 | +0.09 | +0.02 |  | +29 (341) |
| FIB|ote79_up|15m | 2+ | half | 162 | 0.001 | -0.06 | +0.02 | +0.00 | +0.00 | +0.00 |  | -18 (103) |
| FIB|ote79_up|15m | 2+ | skip | 190 | 0.002 | -0.12 | +0.02 | +0.00 | -0.01 | +0.06 |  | -31 (257) |
| ALL8 | 0 | half | 1225 | 0.008 | +0.09 | -0.01 | -0.01 | -0.01 | +0.09 |  | +89 (737) |
| ALL8 | 0 | skip | 9641 | 0.115 | -0.17 | +0.06 | +0.28 | +0.16 | +0.37 |  | +439 (3322) |
| ALL8 | 1 | half | 671 | 0.004 | +0.05 | -0.03 | -0.02 | +0.11 | +0.06 |  | +510 (1845) |
| ALL8 | 1 | skip | 1017 | 0.012 | +0.09 | -0.18 | -0.17 | +0.10 | +0.29 |  | +843 (2068) |
| ALL8 | 2+ | half | 608 | 0.003 | -0.06 | +0.00 | +0.00 | +0.06 | -0.06 |  | +27 (326) |
| ALL8 | 2+ | skip | 785 | 0.010 | -0.12 | -0.00 | +0.03 | +0.08 | -0.09 |  | -404 (1435) |

Cells above the band (rule met): none.

## 8. Not done / named gaps
* Only the AHEAD frame was swept over all 332 streams; BEHIND/AT were run for 19 streams. Placebo draws (16 per kind) are the compute budget; ranks have 0.06 resolution. The purged walk-forward is owned by Z3. 1-s/3-s decision delay was not run (AHEAD skip/half are signal-second decisions; B73/WT/re-target are in section 3). Parameter variants of the line itself (swing strength, profile bin, anchor shifts) are separate streams in the grid (SWG f3/f5/f7, PRF b1-b3, anchors), not re-parameterised. RND and BKS streams were not built. D7 v1.3 profit lines are an agent-built assumption (THP_POLICY_D7.txt not on disk); U7 is an assumption.


## 10. Structural reading and decision delay
* Of the 24 finalists (V13X, lock off) 10 keep a positive maxDD cut in L6M AND PRE AND X' (the three independent episodes); with the combined lock 12 6. The cut depends on which few weeks a line removes, and on the base.
* Decision delay: AHEAD skip/half are evaluated at the signal second on a line knowable earlier (bar-close or prior-period lines) and place no order, so a 1-s/3-s delay changes nothing except the freshness check (tested on the assumed base for PRF|vwap|day: no change). BEHIND restop re-places the stop at the fill and was not delay-tested (named gap).
* maxDD noise band (Z3 DS3_ZONES_3_NOISE.md): not yet applied.
