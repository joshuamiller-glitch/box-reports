# DS3_ZONES_3_S4A - T-ZONES-3 section 4, first half (EVEN-index streams) of the other POI streams: AHEAD / BEHIND / AT frames

**BASE LABEL: every number in this file is on the ASSUMED base (v1.2 / v1.3-assumed: U7 blackout on all books both sides, assumed NY-AM lots and assumed profit lines). The EXACT D7 v1.3 (V13X, user paste 02:45Z) is being built by BASE-4; finalists are re-run on V13X when it is announced and those rows become the headline. Where V13X differs the file will say so (base dependence).**

STATUS: S4a deliverable written 2026-11-02 02:52Z (interim: BEHIND/AT frames for the 19 best finalist streams; per-cell placebos 16 draws per kind). POST-HOC, Shadow only, no PASS claim, nothing here is a lead until the robustness standard is met; labels below say how far each cell got.
Prereg l2vast/ds3/prereg/ZONES3_S4A_prereg.md sha256 e8d9004f35ecf860d2beaac5372bdd274862c0db1225523eb12a877ac3fcb66d (DECISIONS.md). dead_lookup before: out/zones3_new/s4a_dead_lookup.txt (NOT FOUND for every spec); append_cells after: see end. NEW windows only (code/cap/windows.py): L1M L2M (view, n weeks 5/9) L3M L6M HOLD MID PRE X'. Old-cap numbers are not used.

## 0. Plain verdict

* Nothing in the even half of the 183 other streams clears the full robustness standard. The first screen on D7 v1.1 produced leads (EQL tight 5m D40, FIB ext127 15m D20, SWG f3L 30m D20...) that did NOT survive the move to D7 v1.3 (L6M cut 0.46 to 0.04 for EQL tight; the cut is carried by a handful of weeks and flips sign with the base, including the U7 blackout). The grid was therefore re-screened on v1.3 and only that screen is ranked.
* Cuts in this stack are fragile because the L6M and HOLD maxDD is ONE episode (the same trough in L6M and HOLD, week named in the table) and the engine is path dependent (12R lock, U7): a mask that removes 2-6 % of the planned volume moves the maxDD by +-30 % on any base. Treat every cut below as a screen result.
  * FIB|ote705_up|5m D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X') +0.32, screen +0.31, placebo ranks A/B/C 0.06/0.06/0.12 (n=16), label -.
  * PRF|vwap|day D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X') +0.26, screen +0.23, placebo ranks A/B/C 0.06/0.06/0.06 (n=16), label -.
  * FIB|ote705_dn|15m D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X') +0.25, screen +0.25, placebo ranks A/B/C 0.06/0.06/0.06 (n=16), label (L6M/recent only).
  * FIB|ote705_up|5m D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X') +0.21, screen +0.27, placebo ranks A/B/C 0.12/0.06/0.06 (n=16), label -.
  * FIB|pd50|5m D40 skip: equal-risk cut (mean of L6M/HOLD/PRE/X') +0.20, screen +0.19, placebo ranks A/B/C 0.06/0.12/0.12 (n=16), label -.
  * ARR|FVG|10m D20 skip: equal-risk cut (mean of L6M/HOLD/PRE/X') +0.19, screen +0.15, placebo ranks A/B/C 0.24/0.12/0.24 (n=16), label (L6M/recent only).
* Best cells on the whole standard: (i) PRF|vwap|day D20 skip: cuts L6M +0.17 HOLD +0.17 PRE +0.09 X' +0.59 (MID -0.46), equal-risk mean +947 $/wk, TOLERANT yes, leave-one-episode-out cut >= +0.17, placebo rank 0.06 for all three kinds (best possible with 16 draws), D x0.5..1.5 all +0.22..+0.24 (not fragile); but the bootstrap lower bound is 0.00 and MID (Feb-Apr) is a -46 % maxDD worsening, so it is a LEAD of the (L6M/PRE-positive, MID-negative) kind, volume 3.9 %; (ii) FIB|ote705_dn|15m D40 skip: cuts L6M +0.39 HOLD +0.33 MID +0.37 PRE +0.49 but X' -0.21, bootstrap 5-95 % +0.01..+0.42, LOEO >= +0.33, drop-the-trough-week +0.34 (so not ONE-WEEK), placebo 0.06 x3, but it needs D >= 30 (D20 variant -0.04), labelled (L6M/recent only) because X' worsens; it is the mirror line of the shipped ote705_up. (iii) FIB|ote705_up|5m D20/D40 skip: PRE and X' cuts +0.13..+0.73 but L6M/HOLD cut ~0 (no help on the recent episode). Everything else is a volume effect, ONE-WEEK-like or flips with the base.

## 1. Data and tie-out

* poi_store_redo has only 143 stream files (PDX, PIV, MAS 1h/4h, FIB 15m, CRT 4h, 3 PRF). The other 109 FIB/MAS/CRT streams and ARR (126), PRF (76), SES, KZ, DEV, OPN, GAP, ORB, SWG, EQL, BOS, WYK were rebuilt on the redo path (poi_gen / poi_adapt UNCHANGED, ARR and PRF from out/confirm_redo/streams) into /mnt/l2/l2vast/ds3_zones3_new/s4_streams (shared with S4b) and features for all 663 streams on the 88,490 D7 engine rows into /mnt/l2/l2vast/ds3_zones3_new/s4_feats.
* Tie to the OLD store on the old windows (44,370 old trades, 8 channels x 663 streams = 235,338,480 cells): 1,061 mismatching cells (0.0005 %), all in 11 streams: 10 month-anchored PDX/PIV|month streams (the last month closes differently at the old cap: 13-38 cells each) and PRF|npoc|day (830 cells). All other 652 streams tie exactly. out/zones3_new/s4a_feature_tie.csv. RND and BKS are not in the registry (named gap).

## 2. Screen (v1.3, U7 off for speed, 1,272 distinct masks of 332 streams x D20/40 x half/skip), top 25 by excess cut over the same-volume placebo curve

| # | stream | D | frame | fires | vol | cut L1M | cut L2M | cut L3M | cut L6M | cut HOLD | cut MID | cut PRE | cut X | K | STRICT | TOL | NOW |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | FIB|ote705_up|5m | 40 | skip | 4085 | 0.064 | +0.00 | +0.02 | -0.02 | +0.05 | +0.05 | +0.36 | +0.53 | +0.62 | +0.319 |  |  |  |
| 2 | FIB|ote705_up|5m | 20 | skip | 2760 | 0.044 | +0.00 | +0.23 | +0.29 | +0.12 | +0.12 | +0.54 | +0.23 | +0.60 | +0.287 | Y | Y | Y |
| 3 | FIB|ote705_dn|15m | 40 | skip | 4486 | 0.065 | -0.22 | +0.26 | +0.40 | +0.54 | +0.38 | +0.61 | +0.20 | -0.12 | +0.255 |  |  | Y |
| 4 | PRF|vwap|day | 20 | skip | 2865 | 0.039 | -0.88 | +0.04 | +0.29 | +0.05 | +0.05 | +0.10 | +0.18 | +0.62 | +0.249 |  |  |  |
| 5 | PRF|vwap|day | 40 | skip | 4523 | 0.064 | -0.87 | +0.05 | +0.29 | +0.09 | +0.09 | +0.39 | +0.07 | +0.68 | +0.239 |  |  |  |
| 6 | ARR|FVG|30m | 20 | skip | 2980 | 0.031 | +0.00 | -0.02 | +0.19 | +0.32 | +0.32 | +0.34 | +0.08 | +0.15 | +0.235 |  |  |  |
| 7 | ARR|FVG|30m | 40 | skip | 6421 | 0.075 | +0.00 | -0.36 | +0.26 | +0.40 | -0.13 | +0.27 | +0.18 | +0.43 | +0.217 |  | Y | Y |
| 8 | FIB|pd50|5m | 40 | skip | 2961 | 0.052 | -0.95 | -0.26 | +0.06 | +0.16 | +0.16 | -0.10 | +0.02 | +0.43 | +0.206 |  |  |  |
| 9 | FIB|ote705_dn|15m | 40 | half | 4486 | 0.027 | -0.14 | +0.21 | +0.21 | +0.36 | +0.36 | +0.51 | -0.07 | +0.12 | +0.194 |  |  |  |
| 10 | SWG|f7H|15s | 40 | half | 41034 | 0.192 | -1.80 | -0.42 | -0.06 | +0.28 | +0.28 | +0.34 | +0.35 | +0.20 | +0.188 |  |  |  |
| 11 | ARR|iplFVG|3m | 20 | skip | 9328 | 0.108 | +0.00 | +0.09 | -0.07 | +0.13 | +0.13 | +0.57 | +0.19 | +0.41 | +0.184 |  |  |  |
| 12 | ARR|iplFVG|15s | 20 | skip | 18272 | 0.210 | -0.53 | -0.34 | -0.18 | +0.36 | +0.36 | +0.51 | -0.02 | +0.38 | +0.172 |  |  |  |
| 13 | FIB|ret50|5m | 20 | skip | 2780 | 0.036 | +0.00 | +0.20 | +0.25 | +0.14 | +0.14 | +0.24 | +0.20 | +0.11 | +0.169 |  |  |  |
| 14 | SWG|f7H|30m | 40 | skip | 8394 | 0.088 | -0.30 | +0.23 | +0.17 | +0.05 | +0.05 | -0.19 | +0.36 | +0.26 | +0.168 |  |  |  |
| 15 | ARR|iFVG_CE|15s | 20 | half | 38991 | 0.195 | +0.00 | +0.26 | +0.03 | +0.11 | +0.11 | -0.08 | +0.26 | +0.54 | +0.167 |  |  |  |
| 16 | CRT|M|1h | 40 | skip | 2298 | 0.040 | +0.00 | +0.16 | +0.13 | +0.14 | +0.14 | +0.30 | -0.01 | +0.29 | +0.163 |  |  |  |
| 17 | FIB|dr_high|1h | 40 | skip | 4155 | 0.039 | +0.00 | +0.09 | -0.14 | -0.02 | -0.02 | -0.10 | +0.21 | +0.38 | +0.159 |  |  |  |
| 18 | FIB|pd50|5m | 20 | skip | 2042 | 0.036 | +0.00 | +0.22 | +0.29 | +0.07 | +0.07 | +0.16 | -0.04 | +0.46 | +0.158 |  |  |  |
| 19 | ARR|iplFVG|1h | 20 | skip | 1840 | 0.018 | +0.00 | +0.23 | +0.16 | +0.13 | +0.13 | +0.30 | -0.02 | +0.36 | +0.157 | Y | Y | Y |
| 20 | ARR|iFVG_CE|10m | 40 | skip | 11624 | 0.132 | +0.00 | -0.19 | -1.02 | +0.13 | +0.13 | +0.49 | +0.02 | +0.56 | +0.155 |  |  |  |
| 21 | ARR|FVG|10m | 20 | skip | 6007 | 0.068 | +0.00 | +0.08 | +0.29 | +0.14 | +0.14 | +0.11 | -0.22 | +0.53 | +0.151 |  | Y | Y |
| 22 | SWG|f3H|3m | 40 | half | 33490 | 0.160 | +0.17 | +0.23 | +0.13 | +0.21 | +0.21 | +0.34 | +0.24 | +0.31 | +0.151 |  |  |  |
| 23 | SES|nyam_H|prev | 40 | skip | 2423 | 0.018 | +0.00 | +0.02 | +0.34 | +0.11 | +0.11 | -0.13 | +0.08 | +0.27 | +0.150 |  | Y | Y |
| 24 | MAS|kc_lo|4h | 40 | skip | 1452 | 0.016 | +0.00 | -0.02 | +0.27 | +0.20 | +0.20 | -0.10 | +0.08 | +0.10 | +0.149 |  |  |  |
| 25 | ARR|iFVG|15s | 40 | half | 39918 | 0.202 | +0.00 | +0.26 | -0.07 | +0.04 | +0.04 | +0.56 | +0.34 | +0.50 | +0.142 |  |  |  |

cut = 1 - maxDD(cell)/maxDD(base), weekly cumulative. K = mean over L6M/HOLD/PRE/X' of (cut - placebo-curve cut at equal volume share). Base maxDD (v1.3 screen): L1M 15437, L2M 30359, L3M 40675, L6M 107305, HOLD 107305, MID 66992, PRE 192388, X 253329.

## 3. The 24 finalists on assumed-base v1.3 (with U7), ranked by the equal-risk cut (mean of L6M/HOLD/PRE/X'); the top 20 across both halves is merged by the lead

Base (v1.3, U7, 12R): maxDD L3M 43587, L6M 94071, HOLD 94071, MID 43072, PRE 175098, X 234635; mean $/wk L3M 8158, L6M 21332, HOLD 23492, MID 19719, PRE 2944, X -3921. Equal-risk = lot-table scale c so that the ALL worst-20 equals the base's (c shown), exact re-run.

| rank | stream | D | frame | vol | cut L6M | HOLD | MID | PRE | X' | ER c | ER cut L6M | HOLD | PRE | X' | ER dmean ALL $/wk | d L6M (MDE) | Calmar L6M base>cell | v1.2 cut L6M/PRE | lock-off cut L6M/PRE | STRICT/TOL/NOW | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | FIB|ote705_up|5m | 40 | skip | 0.064 | -0.00 | -0.00 | -0.01 | +0.43 | +0.58 | 0.90 | +0.21 | +0.21 | +0.13 | +0.73 | -783 | -425 (3279) | 0.23>0.22 | +0.14/-0.28 | +0.38/+0.02 | 0/0/0 | untagged |
| 2 | PRF|vwap|day | 20 | skip | 0.039 | +0.17 | +0.17 | -0.46 | +0.09 | +0.59 | 1.00 | +0.17 | +0.17 | +0.09 | +0.59 | +947 | +5158 (10311) | 0.23>0.34 | +0.10/+0.03 | -0.10/+0.13 | 0/1/1 | untagged |
| 3 | FIB|ote705_dn|15m | 40 | skip | 0.065 | +0.39 | +0.33 | +0.37 | +0.49 | -0.21 | 1.00 | +0.39 | +0.33 | +0.49 | -0.21 | +1196 | -876 (5556) | 0.23>0.36 | +0.51/-0.10 | +0.25/-0.13 | 0/0/0 | (L6M/recent only) |
| 4 | FIB|ote705_up|5m | 20 | skip | 0.044 | +0.06 | +0.06 | +0.48 | +0.15 | +0.57 | 1.00 | +0.06 | +0.06 | +0.15 | +0.57 | +1624 | +259 (2536) | 0.23>0.25 | -0.00/-0.29 | +0.00/+0.06 | 0/0/0 | untagged |
| 5 | FIB|pd50|5m | 40 | skip | 0.052 | -0.01 | -0.01 | -0.26 | -0.13 | +0.31 | 0.91 | +0.09 | +0.09 | +0.01 | +0.60 | +1335 | -2153 (7930) | 0.23>0.20 | +0.04/+0.12 | +0.10/-0.09 | 0/0/0 | untagged |
| 6 | ARR|FVG|10m | 20 | skip | 0.068 | +0.19 | +0.19 | -0.05 | -0.25 | +0.36 | 0.91 | +0.29 | +0.29 | -0.30 | +0.49 | +136 | +1081 (1978) | 0.23>0.29 | +0.16/-0.02 | +0.02/-0.17 | 0/0/1 | (L6M/recent only) |
| 7 | ARR|iFVG_CE|10m | 40 | skip | 0.132 | -0.43 | -0.43 | +0.19 | -0.15 | +0.34 | 0.85 | +0.02 | +0.02 | +0.07 | +0.57 | -750 | +4041 (13001) | 0.23>0.19 | +0.33/-0.30 | +0.05/-0.01 | 0/0/1 | untagged |
| 8 | SES|nyam_H|prev | 40 | skip | 0.018 | +0.09 | +0.09 | -0.25 | +0.05 | +0.30 | 1.00 | +0.09 | +0.09 | +0.05 | +0.30 | +48 | -182 (4038) | 0.23>0.25 | -0.21/+0.17 | +0.12/+0.03 | 0/0/0 | untagged |
| 9 | PRF|vwap|day | 40 | skip | 0.064 | -0.01 | -0.01 | +0.04 | +0.06 | +0.65 | 1.03 | -0.07 | -0.07 | +0.05 | +0.61 | +1230 | +1836 (10878) | 0.23>0.24 | +0.31/+0.02 | +0.01/+0.07 | 0/1/1 | (volume effect) |
| 10 | ARR|iFVG_CE|15s | 20 | half | 0.195 | +0.17 | +0.17 | -0.60 | +0.46 | +0.46 | 1.24 | -0.11 | -0.11 | +0.37 | +0.36 | +2739 | -1826 (9298) | 0.23>0.25 | +0.18/+0.01 | +0.21/+0.12 | 0/0/0 | (volume effect) |
| 11 | ARR|iplFVG|3m | 20 | skip | 0.108 | -0.10 | -0.10 | +0.32 | +0.18 | +0.25 | 0.95 | -0.00 | -0.00 | +0.22 | +0.28 | -982 | -1068 (9680) | 0.23>0.20 | +0.14/-0.06 | +0.09/+0.11 | 0/0/0 | untagged |
| 12 | ARR|FVG|30m | 40 | skip | 0.075 | +0.18 | -0.20 | +0.12 | +0.03 | +0.38 | 1.02 | +0.18 | +0.01 | -0.04 | +0.34 | +843 | +5017 (11373) | 0.23>0.34 | +0.41/+0.03 | +0.22/-0.16 | 0/0/1 | untagged |
| 13 | FIB|pd50|5m | 20 | skip | 0.036 | +0.16 | +0.16 | -0.15 | -0.18 | +0.35 | 1.00 | +0.16 | +0.16 | -0.18 | +0.35 | +1724 | +1480 (2369) | 0.23>0.29 | +0.03/+0.09 | +0.02/-0.11 | 1/0/1 | (L6M/recent only) |
| 14 | CRT|M|1h | 40 | skip | 0.040 | +0.06 | +0.06 | -0.05 | +0.01 | +0.33 | 1.00 | +0.06 | +0.06 | +0.01 | +0.33 | +1341 | +129 (2697) | 0.23>0.24 | +0.15/+0.08 | +0.13/-0.24 | 1/0/1 | untagged |
| 15 | FIB|ret50|5m | 20 | skip | 0.036 | +0.10 | +0.10 | -0.17 | +0.14 | +0.11 | 1.00 | +0.10 | +0.10 | +0.14 | +0.11 | +1541 | +975 (2498) | 0.23>0.26 | +0.25/+0.20 | +0.23/-0.07 | 1/0/1 | (volume effect) |
| 16 | FIB|ote705_dn|15m | 40 | half | 0.027 | +0.16 | +0.16 | -0.01 | -0.08 | +0.14 | 1.03 | +0.12 | +0.12 | +0.03 | +0.11 | +1763 | -452 (3149) | 0.23>0.26 | +0.27/-0.24 | +0.11/+0.13 | 0/0/0 | (L6M/recent only) |
| 17 | ARR|iplFVG|1h | 20 | skip | 0.018 | +0.06 | +0.06 | +0.00 | -0.02 | +0.25 | 1.00 | +0.06 | +0.06 | -0.02 | +0.25 | +1029 | +828 (1945) | 0.23>0.25 | +0.07/+0.05 | +0.02/+0.06 | 0/1/1 | (L6M/recent only) |
| 18 | ARR|FVG|30m | 20 | skip | 0.031 | +0.18 | +0.18 | +0.12 | -0.04 | -0.02 | 1.00 | +0.18 | +0.18 | -0.04 | -0.02 | +916 | +5565 (9325) | 0.23>0.35 | +0.25/-0.11 | +0.23/-0.07 | 1/0/1 | (L6M/recent only) |
| 19 | MAS|kc_lo|4h | 40 | skip | 0.016 | +0.01 | +0.01 | -0.60 | +0.06 | +0.10 | 1.03 | -0.03 | -0.03 | +0.16 | +0.07 | +471 | +723 (5625) | 0.23>0.24 | +0.21/+0.02 | +0.14/-0.22 | 0/1/1 | untagged |
| 20 | SWG|f7H|30m | 40 | skip | 0.088 | -0.14 | -0.14 | +0.15 | +0.38 | +0.12 | 1.03 | -0.19 | -0.19 | +0.32 | +0.12 | +1207 | -2017 (11099) | 0.23>0.18 | +0.09/+0.16 | +0.14/+0.20 | 0/0/0 | (volume effect) |
| 21 | SWG|f7H|15s | 40 | half | 0.192 | +0.16 | +0.16 | +0.30 | +0.42 | -0.00 | 1.18 | -0.04 | -0.04 | +0.20 | -0.12 | -849 | -5611 (14384) | 0.23>0.20 | +0.30/-0.00 | +0.08/-0.01 | 0/0/0 | (L6M/recent only) |
| 22 | SWG|f3H|3m | 40 | half | 0.160 | +0.29 | +0.29 | +0.33 | +0.01 | +0.24 | 1.22 | +0.09 | +0.09 | -0.48 | +0.26 | -416 | -2547 (13496) | 0.23>0.28 | +0.36/+0.04 | +0.11/+0.03 | 0/0/0 | untagged |
| 23 | ARR|iplFVG|15s | 20 | skip | 0.210 | -0.01 | -0.01 | +0.24 | -0.12 | +0.32 | 1.10 | -0.07 | -0.07 | -0.23 | +0.29 | +2983 | +3246 (11377) | 0.23>0.26 | +0.55/-0.35 | +0.41/-0.45 | 1/1/1 | (volume effect) |
| 24 | FIB|dr_high|1h | 40 | skip | 0.039 | -0.33 | -0.33 | -0.05 | +0.02 | +0.25 | 1.00 | -0.33 | -0.33 | +0.02 | +0.25 | +383 | -4588 (8958) | 0.23>0.13 | +0.12/-0.11 | +0.01/+0.03 | 0/0/0 | (volume effect) |

## 4. Robustness of the finalists (v1.3 + U7 series; windows L6M and PRE)

| stream | D | frame | trough week base L6M | cut L6M | drop trough week | LOEO min..max | LOMO min..max | boot 5-95% | P(cut>0) | trough PRE | cut PRE | LOEO PRE | LOMO PRE | placebo rank A/B/C (n) | D variants x0.5/.75/1.25/1.5 mean4 cut | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| FIB|ote705_up|5m | 40 | skip | 202638 | -0.00 | -0.00 | -0.00..+0.37 | -0.00..+0.17 | -0.07..+0.32 | 0.82 | 202518 | +0.43 | +0.39..+0.57 | +0.24..+0.66 | 0.06/0.06/0.12 (16) | +0.27 / +0.22 / +0.33 / +0.31 | untagged |
| PRF|vwap|day | 20 | skip | 202638 | +0.17 | +0.10 | +0.17..+0.35 | +0.09..+0.35 | -0.00..+0.38 | 0.83 | 202518 | +0.09 | +0.09..+0.14 | +0.09..+0.24 | 0.06/0.06/0.06 (16) | +0.23 / +0.23 / +0.24 / +0.22 | untagged |
| FIB|ote705_dn|15m | 40 | skip | 202638 | +0.39 | +0.34 | +0.33..+0.39 | +0.26..+0.46 | +0.01..+0.42 | 0.98 | 202518 | +0.49 | +0.49..+0.51 | +0.12..+0.66 | 0.06/0.06/0.06 (16) | -0.04 / +0.07 / +0.19 / +0.23 | (L6M/recent only) |
| FIB|ote705_up|5m | 20 | skip | 202638 | +0.06 | +0.07 | +0.06..+0.38 | +0.00..+0.17 | +0.00..+0.31 | 0.78 | 202518 | +0.15 | +0.15..+0.26 | +0.15..+0.40 | 0.12/0.06/0.06 (16) | +0.10 / +0.23 / +0.27 / +0.22 | untagged |
| FIB|pd50|5m | 40 | skip | 202638 | -0.01 | -0.08 | -0.01..+0.35 | -0.20..+0.14 | -0.41..+0.34 | 0.33 | 202518 | -0.13 | -0.13..+0.25 | -0.13..+0.25 | 0.06/0.12/0.12 (16) | +0.14 / +0.15 / +0.21 / +0.21 | untagged |
| ARR|FVG|10m | 20 | skip | 202638 | +0.19 | +0.14 | -0.08..+0.19 | -0.08..+0.24 | -0.08..+0.31 | 0.78 | 202518 | -0.25 | -0.25..+0.12 | -0.25..+0.13 | 0.24/0.12/0.24 (16) | +0.10 / +0.02 / +0.18 / +0.10 | (L6M/recent only) |
| ARR|iFVG_CE|10m | 40 | skip | 202638 | -0.43 | -0.55 | -0.43..+0.11 | -0.71..+0.11 | -1.71..+0.11 | 0.41 | 202518 | -0.15 | -0.15..-0.04 | -0.47..-0.02 | 0.18/0.06/0.12 (16) | +0.01 / +0.14 / +0.14 / +0.07 | untagged |
| SES|nyam_H|prev | 40 | skip | 202638 | +0.09 | +0.08 | +0.00..+0.09 | -0.18..+0.09 | -0.32..+0.27 | 0.36 | 202518 | +0.05 | +0.05..+0.13 | +0.05..+0.15 | 0.06/0.06/0.06 (16) | -0.01 / +0.12 / +0.17 / +0.17 | untagged |
| PRF|vwap|day | 40 | skip | 202638 | -0.01 | -0.09 | -0.01..+0.35 | -0.24..+0.35 | -0.30..+0.37 | 0.48 | 202518 | +0.06 | +0.06..+0.38 | +0.06..+0.38 | 0.12/0.18/0.12 (16) | +0.23 / +0.22 / +0.22 / +0.23 | (volume effect) |
| ARR|iFVG_CE|15s | 20 | half | 202638 | +0.17 | +0.10 | +0.17..+0.32 | +0.09..+0.31 | +0.07..+0.32 | 1.00 | 202518 | +0.46 | +0.46..+0.60 | +0.36..+0.67 | 0.12/0.18/0.24 (16) | +0.10 / +0.26 / +0.19 / +0.17 | (volume effect) |
| ARR|iplFVG|3m | 20 | skip | 202638 | -0.10 | -0.19 | -0.10..-0.08 | -0.20..-0.07 | -0.26..+0.09 | 0.09 | 202518 | +0.18 | +0.12..+0.26 | +0.00..+0.30 | 0.06/0.12/0.18 (16) | +0.09 / +0.18 / +0.19 / -0.13 | untagged |
| ARR|FVG|30m | 40 | skip | 202638 | +0.18 | +0.11 | +0.04..+0.18 | +0.04..+0.27 | +0.00..+0.37 | 0.75 | 202518 | +0.03 | +0.03..+0.28 | +0.01..+0.28 | 0.06/0.12/0.18 (16) | +0.22 / +0.26 / +0.14 / +0.05 | untagged |
| FIB|pd50|5m | 20 | skip | 202638 | +0.16 | +0.09 | +0.16..+0.34 | -0.01..+0.32 | -0.01..+0.33 | 0.64 | 202518 | -0.18 | -0.18..+0.23 | -0.18..+0.23 | 0.12/0.12/0.12 (16) | +0.06 / +0.09 / +0.16 / +0.15 | (L6M/recent only) |
| CRT|M|1h | 40 | skip | 202638 | +0.06 | +0.01 | +0.02..+0.06 | -0.08..+0.06 | -0.10..+0.19 | 0.49 | 202518 | +0.01 | +0.01..+0.34 | -0.04..+0.33 | 0.12/0.12/0.12 (16) | +0.08 / +0.16 / +0.16 / +0.15 | untagged |
| FIB|ret50|5m | 20 | skip | 202638 | +0.10 | +0.09 | +0.10..+0.34 | +0.01..+0.20 | +0.01..+0.33 | 0.97 | 202518 | +0.14 | +0.14..+0.44 | +0.09..+0.44 | 0.12/0.18/0.06 (16) | +0.11 / +0.11 / +0.14 / +0.11 | (volume effect) |
| FIB|ote705_dn|15m | 40 | half | 202638 | +0.16 | +0.09 | +0.16..+0.34 | -0.02..+0.34 | -0.06..+0.34 | 0.64 | 202518 | -0.08 | -0.08..+0.33 | -0.08..+0.28 | 0.06/0.06/0.06 (16) | +0.04 / +0.08 / +0.20 / +0.22 | (L6M/recent only) |
| ARR|iplFVG|1h | 20 | skip | 202638 | +0.06 | +0.04 | +0.06..+0.35 | +0.01..+0.16 | +0.01..+0.26 | 0.96 | 202518 | -0.02 | -0.02..+0.26 | -0.02..+0.32 | 0.12/0.12/0.06 (16) | +0.12 / +0.14 / +0.08 / +0.09 | (L6M/recent only) |
| ARR|FVG|30m | 20 | skip | 202638 | +0.18 | +0.11 | +0.18..+0.35 | +0.09..+0.35 | +0.00..+0.41 | 0.75 | 202518 | -0.04 | -0.04..+0.08 | -0.04..+0.12 | 0.12/0.06/0.12 (16) | +0.02 / +0.07 / +0.27 / +0.26 | (L6M/recent only) |
| MAS|kc_lo|4h | 40 | skip | 202638 | +0.01 | -0.07 | +0.00..+0.01 | -0.19..+0.01 | -0.25..+0.30 | 0.27 | 202518 | +0.06 | -0.01..+0.13 | -0.01..+0.13 | 0.06/0.06/0.18 (16) | +0.01 / +0.07 / +0.19 / +0.21 | untagged |
| SWG|f7H|30m | 40 | skip | 202638 | -0.14 | -0.23 | -0.50..-0.14 | -0.50..-0.14 | -1.67..+0.11 | 0.12 | 202518 | +0.38 | +0.38..+0.46 | +0.32..+0.58 | 0.18/0.18/0.12 (16) | +0.04 / +0.12 / +0.04 / +0.08 | (volume effect) |
| SWG|f7H|15s | 40 | half | 202638 | +0.16 | +0.09 | -0.01..+0.16 | -0.01..+0.18 | -0.49..+0.40 | 0.48 | 202518 | +0.42 | +0.39..+0.42 | +0.31..+0.60 | 0.06/0.06/0.12 (16) | +0.16 / +0.17 / +0.24 / +0.23 | (L6M/recent only) |
| SWG|f3H|3m | 40 | half | 202638 | +0.29 | +0.24 | -0.47..+0.29 | -0.47..+0.29 | -1.51..+0.49 | 0.54 | 202518 | +0.01 | +0.01..+0.30 | -0.00..+0.37 | 0.06/0.12/0.29 (16) | +0.13 / +0.05 / +0.21 / +0.16 | untagged |
| ARR|iplFVG|15s | 20 | skip | 202638 | -0.01 | -0.10 | -0.01..+0.42 | -0.10..+0.13 | -0.26..+0.33 | 0.59 | 202518 | -0.12 | -0.12..+0.29 | -0.16..+0.34 | 0.12/0.24/0.18 (16) | +0.11 / +0.16 / +0.26 / +0.32 | (volume effect) |
| FIB|dr_high|1h | 40 | skip | 202638 | -0.33 | -0.39 | -0.97..-0.33 | -0.97..-0.30 | -2.75..-0.19 | 0.00 | 202518 | +0.02 | +0.02..+0.09 | +0.02..+0.42 | 0.24/0.18/0.12 (16) | +0.04 / +0.05 / +0.15 / +0.19 | (volume effect) |

Placebos (v1.3 U7-off screen base, the same engine as the screen): A random levels = same number of random rows per book x session x side x target-half stratum; B same-volume Bernoulli over eligible rows; C shuffled-day line set (circular shift of the fire vector inside each book x session in time order); statistic = mean of the L6M/HOLD/PRE/X' cuts; rank = (1+#placebo >= cell)/(1+n), n = 16 draws so 0.059 is the best achievable rank. Weeks named by ISO key. LOEO = drop each of the 3 largest base drawdown episodes, LOMO = drop each month, 300 month-block bootstrap draws.

## 5. Per book and per session (maxDD cut, HOLD window | PRE window), top 8 finalists; and mean change by vol tercile (HOLD, $ per week)

| stream | D | frame | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | pre | nyam | nypm | close | vol terc lo/mid/hi d$/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| FIB|ote705_up|5m | 40 | skip | -0.04|+0.38 | -0.09|+0.35 | +0.01|+0.24 | +0.02|-0.20 | -0.01|+0.14 | -0.14|+0.04 | -0.08|+0.03 | -0.03|+0.40 | +0.00|+0.00 | -0.30|-0.25 | -0.65|+0.09 | +0.00|+0.00 | +547/-875/-2117 |
| PRF|vwap|day | 20 | skip | +0.15|+0.09 | -0.56|+0.15 | +0.13|-0.15 | +0.43|+0.17 | +0.14|+0.10 | +0.06|-0.01 | +0.10|-0.17 | +0.19|+0.11 | +0.00|+0.00 | -0.54|-0.03 | -0.06|-0.20 | +0.00|+0.00 | -1212/-515/+141 |
| FIB|ote705_dn|15m | 40 | skip | +0.26|+0.24 | +0.04|+0.43 | +0.48|-0.05 | +0.09|-0.43 | -0.29|+0.26 | +0.06|+0.05 | +0.26|+0.07 | +0.27|+0.06 | +0.00|+0.00 | +0.27|+0.21 | +0.08|-0.77 | +0.00|+0.00 | +29/-1369/-643 |
| FIB|ote705_up|5m | 20 | skip | +0.43|+0.24 | +0.00|+0.18 | -0.02|+0.01 | +0.08|-0.09 | +0.15|+0.01 | +0.06|+0.04 | +0.03|+0.01 | +0.22|+0.21 | +0.00|+0.00 | -0.05|-0.32 | -0.37|+0.10 | +0.00|+0.00 | +1245/-512/-534 |
| FIB|pd50|5m | 40 | skip | -0.09|+0.50 | -0.05|+0.27 | +0.31|+0.07 | +0.04|+0.16 | -0.07|-0.00 | +0.02|+0.04 | +0.14|+0.14 | -0.04|-0.12 | +0.00|+0.00 | +0.13|-0.14 | -0.18|-0.29 | +0.00|+0.00 | +673/-564/-686 |
| ARR|FVG|10m | 20 | skip | +0.02|+0.20 | +0.00|+0.04 | -0.11|+0.20 | +0.08|+0.24 | +0.00|-0.10 | +0.25|-0.40 | +0.07|+0.33 | +0.05|-0.51 | +0.00|+0.00 | -0.82|-0.20 | -0.24|-0.52 | +0.00|+0.00 | +233/-173/-989 |
| ARR|iFVG_CE|10m | 40 | skip | +0.50|+0.27 | -0.28|+0.01 | -0.19|+0.05 | +0.46|+0.02 | -0.25|+0.10 | -0.04|+0.05 | +0.28|-0.52 | +0.41|-0.13 | +0.00|+0.00 | -0.72|-0.35 | -0.27|-0.53 | +0.00|+0.00 | -506/-1245/+1065 |
| SES|nyam_H|prev | 40 | skip | -0.28|+0.15 | +0.00|+0.04 | +0.33|+0.02 | +0.21|+0.16 | -0.22|+0.01 | -0.08|+0.14 | +0.31|+0.13 | -0.07|-0.05 | +0.00|+0.00 | +0.01|-0.20 | -0.90|-0.11 | +0.00|+0.00 | -97/-603/-621 |

Sessions: a zone cut that lives in one session only is a different product (Asia carries the stack in 2026). Vol tercile = tercile of the day's mean library target distance (volatility proxy) inside HOLD.

## 6. BEHIND and AT frames (v1.3 + U7; streams = the 19 distinct finalist streams (top 20 ranks); cut vs the v1.3 base)

BEHIND: fresh POI between entry and stop within Db pts; actions skip / half / restop (stop moved to line - 2 ticks, only if tighter than the library stop; core books; re-simulated with the same jrun kernel as the engine, tie-out exact for the six core books; PE NY rows are not re-stopped = approximate; the TH-L2 loss cut interaction on re-stopped rows is approximate). AT: POI within 2 pts of the entry (fresh or touched, ahead or behind): take-only (skip rows not AT inside book x session cells with >= 50 AT rows; volume collapses, read with equal-risk) / sizeup (x1.5).

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
**BEHIND (top 25 by mean of L6M/HOLD/PRE/X' cut)**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ARR|iplFVG|15s | BEHIND | 20 | skip | 19340 | +0.10 | +0.29 | +0.31 | +0.29 | +0.53 | -10584 (20040) | 0.13/0.23 |
| ARR|iFVG_CE|10m | BEHIND | 10 | skip | 1402 | +0.13 | +0.13 | -0.01 | +0.05 | +0.30 | -686 (2028) | 0.25/0.23 |
| ARR|iFVG_CE|15s | BEHIND | 20 | half | 28556 | +0.36 | +0.36 | -0.34 | -0.06 | -0.09 | -2282 (15792) | 0.32/0.23 |
| ARR|iplFVG|15s | BEHIND | 20 | half | 16924 | +0.14 | +0.14 | +0.02 | +0.16 | +0.10 | -4717 (10546) | 0.21/0.23 |
| ARR|iplFVG|15s | BEHIND | 10 | half | 9872 | +0.21 | +0.19 | +0.07 | +0.03 | +0.07 | -4075 (9635) | 0.23/0.23 |
| CRT|M|1h | BEHIND | 10 | skip | 631 | +0.02 | +0.02 | -0.10 | -0.11 | +0.38 | +114 (165) | 0.23/0.23 |
| ARR|iFVG_CE|15s | BEHIND | 10 | half | 17861 | +0.15 | +0.15 | +0.38 | -0.08 | +0.10 | -4627 (12702) | 0.21/0.23 |
| ARR|iFVG_CE|10m | BEHIND | 20 | half | 3837 | +0.09 | +0.09 | +0.00 | -0.11 | +0.23 | +181 (12831) | 0.25/0.23 |
| ARR|iFVG_CE|10m | BEHIND | 20 | skip | 5072 | +0.05 | +0.05 | -0.02 | -0.07 | +0.25 | -621 (12872) | 0.23/0.23 |
| FIB|ret50|5m | BEHIND | 10 | skip | 2055 | +0.10 | +0.10 | +0.29 | -0.04 | +0.10 | -200 (1177) | 0.25/0.23 |
| FIB|pd50|5m | BEHIND | 20 | skip | 3643 | +0.12 | +0.12 | -0.01 | -0.07 | +0.07 | +426 (2243) | 0.26/0.23 |
| FIB|pd50|5m | BEHIND | 10 | half | 433 | +0.06 | +0.06 | +0.00 | +0.04 | +0.08 | +241 (637) | 0.24/0.23 |
| FIB|pd50|5m | BEHIND | 20 | half | 2609 | +0.14 | +0.14 | -0.01 | +0.08 | -0.12 | +116 (1268) | 0.26/0.23 |
| FIB|ote705_up|5m | BEHIND | 20 | skip | 4969 | +0.02 | +0.02 | +0.01 | -0.07 | +0.25 | +4102 (9399) | 0.28/0.23 |
| FIB|ote705_up|5m | BEHIND | 20 | half | 3652 | -0.01 | -0.01 | -0.31 | +0.08 | +0.17 | +242 (1153) | 0.23/0.23 |
| SWG|f7H|15s | BEHIND | 10 | half | 6120 | +0.09 | +0.09 | +0.06 | -0.13 | +0.14 | -1705 (4998) | 0.23/0.23 |
| FIB|pd50|5m | BEHIND | 10 | restop | 663 | +0.11 | +0.11 | +0.00 | +0.11 | -0.14 | +1335 (2357) | 0.27/0.23 |
| ARR|iplFVG|3m | BEHIND | 10 | half | 4183 | +0.13 | +0.13 | -0.04 | -0.20 | +0.12 | +3599 (10206) | 0.30/0.23 |
| ARR|iFVG_CE|10m | BEHIND | 10 | half | 1043 | +0.05 | +0.05 | -0.02 | -0.06 | +0.11 | -492 (1067) | 0.23/0.23 |
| PRF|vwap|day | BEHIND | 20 | restop | 3484 | +0.05 | +0.05 | -0.00 | -0.18 | +0.22 | -1291 (9196) | 0.23/0.23 |
| ARR|iplFVG|1h | BEHIND | 20 | skip | 824 | +0.01 | +0.01 | -0.14 | -0.02 | +0.13 | +632 (1769) | 0.24/0.23 |
| ARR|iplFVG|1h | BEHIND | 20 | half | 619 | +0.01 | +0.01 | -0.05 | -0.01 | +0.12 | +600 (1622) | 0.24/0.23 |
| ARR|iFVG_CE|15s | BEHIND | 20 | skip | 33895 | -0.04 | -0.04 | -0.12 | +0.19 | +0.03 | -12874 (19892) | 0.09/0.23 |
| ARR|FVG|10m | BEHIND | 20 | half | 5484 | -0.11 | -0.11 | -0.73 | +0.05 | +0.28 | -861 (10789) | 0.20/0.23 |
| CRT|M|1h | BEHIND | 10 | restop | 631 | +0.07 | +0.07 | -0.04 | -0.05 | -0.01 | +348 (801) | 0.25/0.23 |

**AT size-up (x1.5 on rows with a POI within 2 pts)**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| FIB|ret50|5m | AT | 2 | sizeup | 738 | +0.18 | +0.18 | -0.00 | -0.18 | -0.05 | +1471 (4981) | 0.29/0.23 |
| MAS|kc_lo|4h | AT | 2 | sizeup | 173 | +0.01 | +0.01 | +0.00 | -0.01 | +0.01 | +29 (144) | 0.23/0.23 |
| FIB|ote705_up|5m | AT | 2 | sizeup | 643 | -0.01 | -0.01 | -0.01 | -0.01 | -0.01 | +355 (942) | 0.23/0.23 |
| FIB|pd50|5m | AT | 2 | sizeup | 558 | +0.03 | +0.03 | -0.01 | +0.01 | -0.13 | -121 (551) | 0.23/0.23 |
| FIB|ote705_dn|15m | AT | 2 | sizeup | 573 | +0.01 | +0.01 | -0.05 | -0.13 | +0.04 | -257 (797) | 0.23/0.23 |
| CRT|M|1h | AT | 2 | sizeup | 550 | -0.02 | -0.02 | +0.00 | +0.01 | -0.05 | +49 (552) | 0.22/0.23 |
| SES|nyam_H|prev | AT | 2 | sizeup | 590 | +0.02 | +0.02 | +0.00 | -0.15 | +0.02 | +71 (230) | 0.23/0.23 |
| FIB|dr_high|1h | AT | 2 | sizeup | 433 | +0.00 | +0.00 | +0.00 | -0.06 | -0.03 | -253 (320) | 0.22/0.23 |
| PRF|vwap|day | AT | 2 | sizeup | 717 | +0.07 | +0.07 | -0.00 | -0.05 | -0.20 | +202 (585) | 0.25/0.23 |
| SWG|f7H|30m | AT | 2 | sizeup | 2303 | +0.06 | +0.06 | -0.12 | -0.15 | -0.27 | +544 (1387) | 0.25/0.23 |
| ARR|iFVG_CE|10m | AT | 2 | sizeup | 4909 | -0.29 | -0.29 | -0.07 | -0.19 | +0.08 | -316 (3597) | 0.17/0.23 |
| ARR|iplFVG|1h | AT | 2 | sizeup | 11989 | -0.52 | -0.52 | -0.68 | +0.18 | -0.46 | -385 (9806) | 0.15/0.23 |
| SWG|f3H|3m | AT | 2 | sizeup | 24669 | -0.17 | -0.17 | -1.21 | -0.54 | -0.49 | +3650 (10067) | 0.23/0.23 |
| ARR|iFVG_CE|15s | AT | 2 | sizeup | 36446 | -0.59 | -0.59 | -1.45 | -0.95 | -0.61 | +2920 (10548) | 0.16/0.23 |
| ARR|FVG|30m | AT | 2 | sizeup | 15596 | -0.87 | -0.87 | -1.35 | -0.76 | -0.33 | +883 (14211) | 0.13/0.23 |
| ARR|FVG|10m | AT | 2 | sizeup | 21984 | -0.72 | -0.72 | -1.37 | -1.08 | -0.36 | +558 (10904) | 0.14/0.23 |
| SWG|f7H|15s | AT | 2 | sizeup | 39659 | -0.67 | -0.67 | -1.59 | -1.06 | -0.55 | +2898 (9903) | 0.15/0.23 |
| ARR|iplFVG|15s | AT | 2 | sizeup | 45523 | -0.84 | -0.84 | -1.33 | -1.23 | -0.80 | +5719 (13760) | 0.16/0.23 |
| ARR|iplFVG|3m | AT | 2 | sizeup | 32417 | -1.08 | -1.08 | -1.14 | -1.45 | -0.44 | +2899 (13040) | 0.12/0.23 |

**AT take-only (skip every row not AT in cells with >= 50 AT rows): the volume collapses (rows = skipped rows, 8-50 % of the book), so the cut is mostly volume; read the mean column and Calmar, not the cut. Not a lead.**

| stream | frame | param | action | rows | cut L6M | HOLD | MID | PRE | X' | d L6M (MDE) | Calmar L6M cell/base |
|--|--|--|--|--|--|--|--|--|--|--|--|
| SWG|f7H|15s | AT | 2 | takeonly | 15627 | +0.62 | +0.14 | -0.88 | -0.07 | +0.09 | +152 (18283) | 0.61/0.23 |
| ARR|iFVG_CE|15s | AT | 2 | takeonly | 18844 | +0.60 | +0.54 | -0.01 | -0.06 | +0.27 | -5857 (19510) | 0.41/0.23 |
| ARR|iplFVG|15s | AT | 2 | takeonly | 9780 | +0.21 | +0.21 | -0.53 | -0.28 | +0.60 | -2048 (10482) | 0.26/0.23 |
| SES|nyam_H|prev | AT | 2 | takeonly | 11436 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.23/0.23 |
| FIB|ote705_dn|15m | AT | 2 | takeonly | 7586 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.23/0.23 |
| MAS|kc_lo|4h | AT | 2 | takeonly | 0 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.23/0.23 |
| FIB|dr_high|1h | AT | 2 | takeonly | 7565 | +0.00 | +0.00 | +0.00 | +0.00 | +0.00 | +0 (0) | 0.23/0.23 |
| SWG|f3H|3m | AT | 2 | takeonly | 30601 | +0.51 | -0.31 | -1.60 | -0.49 | +0.48 | -13320 (24810) | 0.17/0.23 |
| ARR|FVG|30m | AT | 2 | takeonly | 39409 | +0.45 | -0.32 | -1.53 | -0.25 | +0.57 | -12517 (27677) | 0.17/0.23 |
| ARR|iplFVG|3m | AT | 2 | takeonly | 22876 | -0.00 | -0.00 | -1.10 | +0.41 | +0.34 | -6486 (22400) | 0.16/0.23 |
| ARR|FVG|10m | AT | 2 | takeonly | 33035 | +0.33 | +0.33 | -0.04 | -0.61 | +0.57 | -13312 (27021) | 0.13/0.23 |
| ARR|iFVG_CE|10m | AT | 2 | takeonly | 48612 | +0.69 | +0.40 | +0.14 | +0.30 | +0.57 | -18559 (27387) | 0.10/0.23 |

## 7. New lines worth adding, with exact D7-computable definitions

None is yet a RISK-KEEP line. The ones to carry to the merged top 20 as screen LEADS (post-hoc, definitions exact; label shown):

* **FIB|ote705_up|5m, AHEAD D 40 pts, fresh, action SKIP** (label -). Definition: Dealing range on 5m bars (bars at CLOSE): fractal-5 swing highs/lows (2 bars each side, confirmed 2 bars later); H3 = max of the last 3 confirmed swing highs, L3 = min of the last 3 confirmed swing lows, valid when H3-L3 >= 4 pts. Level = L3 + 0.705*(H3-L3)  (the 0.705 retracement measured up from the dealing-range low). Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 4085 of 88,490 rows (6.4 % of planned lot volume).
* **PRF|vwap|day, AHEAD D 20 pts, fresh, action SKIP** (label -). Definition: Volume-weighted average price of the day anchor (CME day: from 18:00 ET) from the 1-s tape (cfa1 vwap stream; the same level for both directions: neutral line), updated as the day develops (stream rows at each knowable update), fresh = never traded through since that value was formed. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 2865 of 88,490 rows (3.9 % of planned lot volume).
* **FIB|ote705_dn|15m, AHEAD D 40 pts, fresh, action SKIP** (label (L6M/recent only)). Definition: Dealing range on 15m bars (bars at CLOSE): fractal-5 swing highs/lows (2 bars each side, confirmed 2 bars later); H3 = max of the last 3 confirmed swing highs, L3 = min of the last 3 confirmed swing lows, valid when H3-L3 >= 4 pts. Level = H3 - 0.705*(H3-L3)  (the 0.705 retracement measured down from the dealing-range high). Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 4486 of 88,490 rows (6.5 % of planned lot volume).
* **FIB|ote705_up|5m, AHEAD D 20 pts, fresh, action SKIP** (label -). Definition: Dealing range on 5m bars (bars at CLOSE): fractal-5 swing highs/lows (2 bars each side, confirmed 2 bars later); H3 = max of the last 3 confirmed swing highs, L3 = min of the last 3 confirmed swing lows, valid when H3-L3 >= 4 pts. Level = L3 + 0.705*(H3-L3)  (the 0.705 retracement measured up from the dealing-range low). Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 2760 of 88,490 rows (4.4 % of planned lot volume).
* **FIB|pd50|5m, AHEAD D 40 pts, fresh, action SKIP** (label -). Definition: Dealing range on 5m bars as above (fractal-5 swings, last 3 highs/lows, H3-L3 >= 4): level = (H3+L3)/2. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 2961 of 88,490 rows (5.2 % of planned lot volume).
* **ARR|FVG|10m, AHEAD D 20 pts, fresh, action SKIP** (label (L6M/recent only)). Definition: FVG zone on 10m bars (FVG = 3-bar imbalance; iFVG = inverted FVG; iplFVG = implied FVG; OB = order block; BRK = breaker), near edge used for the distance; bar-close knowable (CF-ENG s1 arrays); direction-bearing: counts AHEAD only if it supports the other side. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 20 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 6007 of 88,490 rows (6.8 % of planned lot volume).
* **ARR|iFVG_CE|10m, AHEAD D 40 pts, fresh, action SKIP** (label -). Definition: Consequent encroachment (50% midpoint) of the iFVG zone on 10m bars (ICT iFVG: FVG = 3-bar imbalance; iFVG = inverted FVG; iplFVG = implied FVG; OB = order block; BRK = breaker); direction-bearing: counts AHEAD only if it supports the other side. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 11624 of 88,490 rows (13.2 % of planned lot volume).
* **SES|nyam_H|prev, AHEAD D 40 pts, fresh, action SKIP** (label -). Definition: Previous completed nyam window high (ET windows: asia 18-02, london 02-08:30, pre 08:30-09:30, nyam 09:30-12, nypm 12-15, close 15-17, on 18-09:30, rth 09:30-16; killzones asia 20-24, london 02-05, ny 07-10, lc 10-12), knowable at window end. Rule for D7: at the signal second, if the nearest FRESH (never traded through since formed, knowable at the signal second) line lies between the entry and the target within 40 pts of the entry (for direction-bearing ARR zones only if the zone supports the other side), then skip the trade. Fires on 2423 of 88,490 rows (1.8 % of planned lot volume).

The 8 shipped lines and the 3 profile lines are not in this section. L1M/L2M columns are views, never selected on.

## 8. Not done / named gaps
* Only the AHEAD frame was swept over all 332 streams; BEHIND/AT were run for 19 streams. Placebo draws (16 per kind) are the compute budget; ranks have 0.06 resolution. The purged walk-forward is owned by Z3. 1-s/3-s decision delay was not run (AHEAD skip/half are signal-second decisions; B73/WT/re-target are in section 3). Parameter variants of the line itself (swing strength, profile bin, anchor shifts) are separate streams in the grid (SWG f3/f5/f7, PRF b1-b3, anchors), not re-parameterised. RND and BKS streams were not built. D7 v1.3 profit lines are an agent-built assumption (THP_POLICY_D7.txt not on disk); U7 is an assumption.

## 9. Follow-up on the two leads (v1.3 WITH U7, 12R lock; skip frame)

Placebos here use the v1.3+U7 engine itself (the section 4 placebos used the U7-off screen). Kinds: A = random rows, same count per day x book x session; B = same-volume Bernoulli; C = shuffled-day line set (circular shift in time order inside each book x session). Statistic = mean of the L6M/HOLD/PRE/X' cuts. Rank = (1+#placebo >= cell)/(1+n).

### PRF|vwap|day (lead D 20 skip)

**D scan (pts and % of target distance) and decision delay**

| variant | fires | cut L6M | cut HOLD | cut MID | cut PRE | cut X | mean4 |
|--|--|--|--|--|--|--|--|
| D 10 pts | 1540 | +0.17 | +0.17 | -0.40 | +0.00 | +0.37 | +0.18 |
| D 15 pts | 2267 | +0.17 | +0.16 | -0.47 | +0.06 | +0.60 | +0.25 |
| D 20 pts | 2865 | +0.17 | +0.17 | -0.46 | +0.09 | +0.59 | +0.26 |
| D 25 pts | 3418 | +0.17 | +0.11 | -0.00 | +0.09 | +0.62 | +0.25 |
| D 30 pts | 3884 | +0.11 | -0.02 | -0.06 | +0.11 | +0.62 | +0.20 |
| D 35 pts | 4256 | +0.14 | +0.14 | -0.06 | +0.05 | +0.64 | +0.25 |
| D 40 pts | 4523 | -0.01 | -0.01 | +0.04 | +0.06 | +0.65 | +0.17 |
| D 50 pts | 4990 | -0.03 | -0.03 | +0.23 | -0.12 | +0.65 | +0.12 |
| D 60 pts | 5390 | -0.00 | -0.00 | +0.21 | -0.06 | +0.65 | +0.14 |
| 25 % of target | 2065 | +0.17 | +0.16 | -0.47 | +0.06 | +0.60 | +0.25 |
| 50 % of target | 3617 | +0.11 | -0.02 | -0.06 | +0.11 | +0.62 | +0.20 |
| 75 % of target | 4619 | -0.01 | -0.01 | +0.04 | -0.06 | +0.65 | +0.14 |
| D 20 pts, signal decision delayed 1 s | 2805 | +0.17 | +0.17 | -0.52 | +0.09 | +0.59 | +0.26 |
| D 20 pts, signal decision delayed 3 s | 2735 | +0.15 | +0.15 | -0.52 | +0.09 | +0.59 | +0.25 |

**Placebos (v1.3+U7), cell mean4 cut +0.26**: A: n=100, placebo mean +0.058, 95th pct +0.218, rank 0.040; B: n=100, placebo mean -0.041, 95th pct +0.113, rank 0.020; C: n=66, placebo mean -0.023, 95th pct +0.174, rank 0.015

* L6M: cut +0.17, base trough week 202638, drop that week +0.10, drop worst week +0.17, LOEO +0.17..+0.35, LOMO +0.09..+0.35, month-block bootstrap 5-95 % -0.00..+0.38, P(cut>0) 0.83
* PRE: cut +0.09, base trough week 202518, drop that week +0.04, drop worst week +0.14, LOEO +0.09..+0.14, LOMO +0.09..+0.24, month-block bootstrap 5-95 % -0.15..+0.34, P(cut>0) 0.68
* X: cut +0.59, base trough week 202347, drop that week +0.59, drop worst week +0.59, LOEO -0.02..+0.00, LOMO +0.45..+0.63, month-block bootstrap 5-95 % +0.16..+0.68, P(cut>0) 0.99
* HOLD: cut +0.17, base trough week 202638, drop that week +0.10, drop worst week +0.17, LOEO -0.29..+0.17, LOMO -0.29..+0.26, month-block bootstrap 5-95 % -0.83..+0.17, P(cut>0) 0.30
* L6M with ISO week 202638 (2026-09-14..18, the base's maxDD trough, base weekly P&L -7207, cell +90518) removed: maxDD base 86864 cell 77796, cut +0.10
### FIB|ote705_dn|15m (lead D 40 skip)

**D scan (pts and % of target distance) and decision delay**

| variant | fires | cut L6M | cut HOLD | cut MID | cut PRE | cut X | mean4 |
|--|--|--|--|--|--|--|--|

**Explained weeks (v1.3+U7, weekly P&L cell minus base)**
* PRF|vwap|day D20: the L6M/HOLD cut is ONE WEEK: ISO 202638 delta +97.7k (the skip removed a trade cluster that lost ~98k in the base's trough week); every other L6M week moves by < 16k. MID (Feb-Apr) -0.46: week 202611 delta -68.5k (the skip removed a winning cluster), which creates a new 62.7k drawdown vs the base's 43.1k. So PRF vwap is a one-week lead for L6M, not a drawdown reduction.
* FIB|ote705_dn|15m D40: X' worsening (-0.21, maxDD 285k vs 235k) is diffuse over the whole window (cell DD episode 202314..202347); biggest negative deltas 202326 -23k, 202338 -21k, 202317 -16k, 202403 -11k, offset by 202334 +16k, 202402 +11k. It is the line removing winners over the whole 2023 downtrend, not one event. MID: the cut +0.37 comes from week 202613 (+28.7k) and 202614 (+12k), offset by 202611 -68.6k and 202617 -52k.


## 10. Structural reading and decision delay
* Of the 24 finalists on v1.3 (with U7), 9 keep a positive maxDD cut in L6M AND PRE AND X' (the three independent episodes; L6M and HOLD are one trough) and only 2 are positive in L6M, HOLD, MID, PRE and X' together. At equal risk 9 of 24 are positive in L6M, PRE and X' (a different set). The cut is not a property of 'zones' in general: it depends on which few weeks the line happens to remove.
* Decision delay: AHEAD skip/half are evaluated at the signal second on a line that is knowable earlier (bar-close or prior-period lines) and place no order, so a 1-s/3-s delay changes nothing except the freshness check; that check was re-run for the two leads (table above, rows 'decision delayed'). BEHIND restop re-places the stop at the fill and was NOT delay-tested (needs the entry kernel at kin+delay; named gap).
* maxDD noise band (Z3's DS3_ZONES_3_NOISE.md): applied in the next revision when published.
