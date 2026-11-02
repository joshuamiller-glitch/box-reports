# DS3_ZONES_3_S4A - T-ZONES-3 section 4, first half (EVEN-index streams) of the other POI streams: AHEAD / BEHIND / AT frames

**BASE: D7 v1.3 EXACT (V13X, user paste 02:45Z). HEADLINE FRAME = combined stack lock OFF (lock=None: the engine's own per-book 12R week floor and day give-back locks remain), as the lead ordered at 04:30Z; the same cells with the combined 12R lock ON are in the columns marked 'lock12'. A cut that exists only with lock 12 is LOCK-ONLY. The older assumed-base file is DS3_ZONES_3_S4A_ASSUMED_BASE.md.**

STATUS: S4a deliverable written 2026-11-02 05:42Z (interim: BEHIND/AT frames for the 19 best finalist streams; per-cell placebos 16 draws per kind). POST-HOC, Shadow only, no PASS claim, nothing here is a lead until the robustness standard is met; labels below say how far each cell got.
Prereg l2vast/ds3/prereg/ZONES3_S4A_prereg.md sha256 e8d9004f35ecf860d2beaac5372bdd274862c0db1225523eb12a877ac3fcb66d (DECISIONS.md). dead_lookup before: out/zones3_new/s4a_dead_lookup.txt (NOT FOUND for every spec); append_cells after: see end. NEW windows only (code/cap/windows.py): L1M L2M (view, n weeks 5/9) L3M L6M HOLD MID PRE X'. Old-cap numbers are not used.

## 0. Plain verdict

* On the EXACT base with the combined lock off, no even-half stream clears the robustness standard; the screen leads of the assumed base mostly did not carry (base dependence), and many V13X lock-12 cuts disappear with the lock off (LOCK-ONLY). The three independent episodes are L6M, PRE and X' (L6M and HOLD share a trough); the 24 finalists are listed with how many keep a positive cut in all three.
* Finalists with a positive cut in L6M AND PRE AND X' (lock off): 10 of 24; with lock 12 the same count is 6.
  * FIB|ote705_dn|15m D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.13, screen +0.13, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.
  * FIB|ret50|1h D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.11, screen +0.16, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label (L6M/recent only).
  * ARR|iplFVG|15s D40 half: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.09, screen +0.17, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label (L6M/recent only).
  * EQL|EQL_tight|5m D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X', lock off) +0.09, screen +0.19, placebo ranks A/B/C 1.00/1.00/1.00 (n=0), label -.
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
| 9 | FIB|ote705_dn|1h | 40 | skip | 0.040 | +0.04 | +0.01 | -0.16 | +0.08 | +0.18 | 1.14 | +0.04 | +0.04 | +0.01 | +0.15 | +1590 | +306 (2237) | 0.20>0.21 | +0.07/+0.18 | 0/1/1 | untagged |
| 10 | MAS|supertrend|1h | 40 | skip | 0.046 | +0.18 | +0.05 | -0.05 | +0.22 | -0.00 | 1.05 | +0.07 | +0.05 | +0.15 | -0.04 | +495 | -496 (5223) | 0.20>0.24 | +0.00/+0.23 | 0/0/0 | (L6M/recent only) |
| 11 | EQL|EQL_tight|5m | 20 | skip | 0.012 | +0.08 | +0.08 | +0.01 | +0.08 | +0.31 | 1.05 | -0.02 | -0.02 | -0.02 | +0.29 | +355 | +435 (3147) | 0.20>0.22 | +0.07/-0.03 | 1/1/1 | untagged |
| 12 | MAS|bb_mid|4h | 20 | skip | 0.013 | +0.12 | +0.07 | +0.13 | +0.07 | +0.11 | 1.08 | +0.06 | +0.06 | -0.05 | +0.10 | +872 | +724 (1386) | 0.20>0.24 | -0.04/+0.13 | 1/1/1 | untagged |
| 13 | DEV|on_L|so_far | 20 | half | 0.073 | +0.64 | +0.23 | -0.14 | -0.21 | +0.32 | 1.20 | +0.59 | -0.02 | -0.62 | +0.17 | +1462 | +2632 (10393) | 0.20>0.62 | +0.33/-0.16 | 1/1/1 | (L6M/recent only) |
| 14 | ARR|iplFVG|15s | 20 | half | 0.091 | +0.30 | +0.06 | +0.02 | -0.24 | +0.38 | 1.15 | +0.10 | +0.05 | -0.41 | +0.31 | +861 | -182 (7285) | 0.20>0.29 | +0.25/+0.02 | 0/0/0 | (L6M/recent only) |
| 15 | DEV|on_L|so_far | 40 | half | 0.100 | +0.67 | +0.17 | -0.04 | -0.38 | +0.40 | 1.19 | +0.49 | -0.04 | -0.66 | +0.25 | +682 | +137 (10987) | 0.20>0.62 | +0.50/-0.42 | 0/0/1 | (L6M/recent only) |
| 16 | SWG|f3L|15s | 40 | half | 0.238 | +0.45 | +0.31 | -0.00 | +0.06 | +0.41 | 1.37 | +0.12 | +0.06 | -0.39 | +0.15 | +192 | -1548 (11462) | 0.20>0.35 | +0.06/+0.17 | 0/0/0 | untagged |
| 17 | ARR|iFVG|15s | 20 | half | 0.133 | +0.22 | +0.06 | -0.05 | +0.12 | +0.11 | 1.23 | +0.11 | -0.05 | -0.14 | +0.01 | +916 | -1821 (7770) | 0.20>0.24 | -0.19/+0.54 | 0/0/0 | untagged |
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
| FIB|ote705_dn|15m | 20 | skip | 202634 | +0.17 | +0.20 | +0.07..+0.07 | -0.07..+0.20 | -0.12..+0.31 | 0.78 | 202516 | +0.11 | +0.02..+0.20 | +0.02..+0.23 | 1.00/1.00/1.00 (0) | pending | untagged |
| FIB|ret50|1h | 40 | skip | 202634 | +0.23 | +0.34 | +0.02..+0.02 | -0.31..+0.42 | -0.45..+0.48 | 0.63 | 202516 | -0.13 | -0.25..-0.05 | -0.40..-0.04 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| ARR|iplFVG|15s | 40 | half | 202634 | +0.31 | +0.27 | -0.17..-0.17 | +0.14..+0.36 | -0.02..+0.37 | 0.95 | 202516 | -0.23 | -0.23..+0.13 | -0.33..+0.13 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| EQL|EQL_tight|5m | 40 | skip | 202634 | +0.14 | +0.16 | -0.05..-0.05 | +0.05..+0.20 | -0.05..+0.30 | 0.83 | 202516 | +0.11 | +0.02..+0.11 | -0.04..+0.17 | 1.00/1.00/1.00 (0) | pending | untagged |
| MAS|bb_lo|1h | 40 | skip | 202634 | +0.32 | +0.46 | +0.03..+0.03 | -0.20..+0.54 | -0.27..+0.65 | 0.75 | 202516 | -0.03 | -0.03..+0.05 | -0.03..+0.08 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SES|asia_H|prev | 20 | skip | 202634 | +0.09 | +0.10 | +0.00..+0.00 | +0.02..+0.13 | -0.02..+0.18 | 0.75 | 202516 | +0.07 | +0.07..+0.07 | +0.05..+0.16 | 1.00/1.00/1.00 (0) | pending | untagged |
| FIB|ext127|15m | 20 | skip | 202634 | +0.31 | +0.32 | -0.02..-0.02 | +0.09..+0.36 | -0.07..+0.36 | 0.85 | 202516 | +0.02 | -0.09..+0.08 | -0.09..+0.16 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| FIB|dr_high|15m | 20 | skip | 202634 | +0.04 | +0.03 | +0.05..+0.05 | -0.07..+0.04 | -0.08..+0.05 | 0.62 | 202516 | +0.01 | -0.10..+0.13 | -0.10..+0.13 | 1.00/1.00/1.00 (0) | pending | untagged |
| FIB|ote705_dn|1h | 40 | skip | 202634 | +0.04 | -0.02 | -0.01..-0.01 | -0.05..+0.13 | -0.07..+0.15 | 0.46 | 202516 | +0.08 | -0.02..+0.26 | -0.02..+0.26 | 1.00/1.00/1.00 (0) | pending | untagged |
| MAS|supertrend|1h | 40 | skip | 202634 | +0.18 | +0.15 | +0.16..+0.16 | -0.01..+0.25 | -0.10..+0.26 | 0.87 | 202516 | +0.22 | +0.14..+0.23 | +0.11..+0.29 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| EQL|EQL_tight|5m | 20 | skip | 202634 | +0.08 | +0.09 | -0.03..-0.03 | +0.05..+0.08 | -0.01..+0.10 | 0.92 | 202516 | +0.08 | -0.00..+0.08 | -0.00..+0.13 | 1.00/1.00/1.00 (0) | pending | untagged |
| MAS|bb_mid|4h | 20 | skip | 202634 | +0.12 | +0.09 | +0.02..+0.02 | +0.08..+0.12 | +0.02..+0.12 | 0.99 | 202516 | +0.07 | +0.07..+0.09 | +0.06..+0.16 | 1.00/1.00/1.00 (0) | pending | untagged |
| DEV|on_L|so_far | 20 | half | 202634 | +0.64 | +0.63 | +0.30..+0.30 | +0.45..+0.70 | +0.45..+0.79 | 1.00 | 202516 | -0.21 | -0.21..+0.35 | -0.25..+0.18 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| ARR|iplFVG|15s | 20 | half | 202634 | +0.30 | +0.34 | -0.18..-0.18 | -0.07..+0.38 | -0.25..+0.47 | 0.72 | 202516 | -0.24 | -0.24..+0.14 | -0.30..+0.14 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| DEV|on_L|so_far | 40 | half | 202634 | +0.67 | +0.67 | +0.25..+0.25 | +0.45..+0.71 | +0.29..+0.75 | 1.00 | 202516 | -0.38 | -0.38..+0.22 | -0.38..+0.16 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SWG|f3L|15s | 40 | half | 202634 | +0.45 | +0.57 | +0.39..+0.39 | +0.23..+0.50 | +0.19..+0.55 | 1.00 | 202516 | +0.06 | +0.06..+0.41 | -0.02..+0.41 | 1.00/1.00/1.00 (0) | pending | untagged |
| ARR|iFVG|15s | 20 | half | 202634 | +0.22 | +0.29 | +0.06..+0.06 | -0.23..+0.44 | -0.23..+0.47 | 0.83 | 202516 | +0.12 | +0.03..+0.34 | +0.02..+0.34 | 1.00/1.00/1.00 (0) | pending | untagged |
| DEV|sess_L|so_far | 20 | half | 202634 | +0.67 | +0.66 | +0.43..+0.43 | +0.41..+0.70 | +0.41..+0.79 | 1.00 | 202516 | -0.14 | -0.14..+0.26 | -0.21..+0.26 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SES|close_H|prev | 40 | skip | 202634 | +0.17 | +0.19 | +0.01..+0.01 | -0.10..+0.22 | -0.10..+0.34 | 0.87 | 202516 | +0.19 | +0.13..+0.19 | -0.02..+0.35 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| PRF|lvn2|day | 40 | half | 202634 | +0.04 | +0.04 | -0.25..-0.25 | +0.00..+0.10 | -0.15..+0.15 | 0.68 | 202516 | +0.09 | -0.01..+0.26 | -0.01..+0.26 | 1.00/1.00/1.00 (0) | pending | untagged |
| DEV|day_L|so_far | 20 | half | 202634 | +0.65 | +0.63 | +0.30..+0.30 | +0.47..+0.69 | +0.46..+0.78 | 1.00 | 202516 | -0.25 | -0.25..+0.31 | -0.26..+0.14 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| SWG|f5L|15s | 40 | half | 202634 | +0.40 | +0.49 | +0.20..+0.20 | +0.17..+0.47 | -0.01..+0.52 | 0.93 | 202516 | -0.24 | -0.24..+0.40 | -0.24..+0.34 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| DEV|sess_L|so_far | 40 | half | 202634 | +0.54 | +0.56 | +0.32..+0.32 | +0.37..+0.69 | +0.32..+0.69 | 1.00 | 202516 | -0.40 | -0.40..+0.36 | -0.53..+0.20 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |
| DEV|day_L|so_far | 40 | half | 202634 | +0.69 | +0.67 | +0.25..+0.25 | +0.45..+0.71 | +0.28..+0.76 | 1.00 | 202516 | -0.43 | -0.43..+0.35 | -0.49..+0.10 | 1.00/1.00/1.00 (0) | pending | (L6M/recent only) |

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

(frames pending)

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

## 8. Not done / named gaps
* Only the AHEAD frame was swept over all 332 streams; BEHIND/AT were run for 19 streams. Placebo draws (16 per kind) are the compute budget; ranks have 0.06 resolution. The purged walk-forward is owned by Z3. 1-s/3-s decision delay was not run (AHEAD skip/half are signal-second decisions; B73/WT/re-target are in section 3). Parameter variants of the line itself (swing strength, profile bin, anchor shifts) are separate streams in the grid (SWG f3/f5/f7, PRF b1-b3, anchors), not re-parameterised. RND and BKS streams were not built. D7 v1.3 profit lines are an agent-built assumption (THP_POLICY_D7.txt not on disk); U7 is an assumption.


## 10. Structural reading and decision delay
* Of the 24 finalists (V13X, lock off) 10 keep a positive maxDD cut in L6M AND PRE AND X' (the three independent episodes); with the combined lock 12 6. The cut depends on which few weeks a line removes, and on the base.
* Decision delay: AHEAD skip/half are evaluated at the signal second on a line knowable earlier (bar-close or prior-period lines) and place no order, so a 1-s/3-s delay changes nothing except the freshness check (tested on the assumed base for PRF|vwap|day: no change). BEHIND restop re-places the stop at the fill and was not delay-tested (named gap).
* maxDD noise band (Z3 DS3_ZONES_3_NOISE.md): not yet applied.
