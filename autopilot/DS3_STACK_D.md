# DS3_STACK_D - same-direction concurrency caps on the live stack (D3SKD, T-STACK section D), 2026-10-28

Research only; no live / execution / chart change. Prereg `l2vast/ds3/prereg/D3SKD_prereg.md` sha256 `9d101e7f2c5762159d24950b4dc6bee9f168556c6df671051dde0904f840cabe` (DECISIONS.md, before any cap cell was scored), 9 cells, F handoff = 60 (T-STACK program). Pre-holdout text `autopilot/DS3_STACK_D_PREHOLD.md` (PRE only; HOLD and X read once, looks logged D3SKD_GD, D3SKD_GD_SPAN2). Code `l2vast/ds3/code/stk_d/`, outputs `l2vast/ds3/out/stk_d/` (pre_results.json, final_results.json, final_series.pkl, affected.json, pre_weekly_series.parquet).

## Verdict
**0 PASS, 0 CANDIDATE, 9 DEAD. A stack-level cap on same-direction lots or books does not improve the live stack; it costs income roughly in proportion to the exposure it removes and does not bind harder in the bad weeks.** The share of entries a cap touches is the same in the audit's 20 worst weeks, the 20 best weeks and the middle (e.g. D_B2s 34% / 36% / 36%; D_L20s 29% / 29% / 29%; D_L30s 11/11/11%), so the "all books pile up in one direction in chop weeks" hypothesis is not visible in concurrency: same-direction pile-ups are as common in the best weeks. Raw, every heavy cap saves money in the 20 worst weeks (D_B2s +$1.72M, D_L20s +$1.45M, D_B3s +$0.82M of a base -$3.74M) and gives up more in the other 165 weeks (D_B2s -$5.44M, D_L20s -$4.71M, D_B3s -$2.91M); net WF raw mean D_B2s -20,053/wk [-36,582,-4,129] (MDE 23,252), D_L20s -16,176 [-31,016,-2,142], D_B3s -9,953 [-21,075,+774], D_B3e -10,057 [-20,344,-164] (CI excludes 0 on the negative side for B2s, L20s, B3e). Lot-matched (same PRE lot-seconds as the stack, c_LM 1.02-1.50), WF mean is -113 (D_B4s) to -7,770 (D_B2s) for the eight cells other than D_L40s (+2,875); the 2023 span (X) is negative for all nine cells; the PRE random-thinning placebo rank is below 0.95 for every cell except D_L40s (0.94, not cleared either); and the lot-matched worst-20-week saving shrinks to +$0.7M (D_B2s) / +$0.47M (D_L20s) against -$2.7M / -$2.0M given up elsewhere. The two lighter caps (D_L40s 2% of entries, D_B4s 7%) are inside their MDE (WF raw +1,788 [-1,176,+4,839], MDE 4,295; -3,624 [-10,084,+2,843], MDE 9,233): not distinguishable from zero, inconclusive rather than proven null.

Best cell regardless of verdict: **D_L40s** (cap 40 weighted lots per direction, first-in, later entry skipped; 1.9% of entries). Only cell with LM mean delta > 0 in both PRE (+3,385 [-879,+7,909], MDE 6,289) and HOLD (+2,270, p 0.118, MDE 5,531); WF raw +1,788/wk, d_Sharpe +0.18, maxDD WF raw -10,482, worst week 0; passes G1, G5, G7, G8; FAILS G2 (HOLD CI spans 0), G3 (HOLD LM maxDD +2,966 and worst -7,254), G4 (HOLD thin-placebo rank 0.61; PRE 0.94/1.00), G6 (2023 span LM -5,475/wk, maxDD -17,923 ok, worst -20,551), so DEAD. Its effect is a +0.1 Sharpe nudge of 2% of entries: noise-level.

**PRE-selected F handoff (pre-registered rule: best PRE LM worst-20-week improvement subject to PRE LM mean delta >= -MDE): D_B2s** (max 2 books per direction, later skipped): PRE-only worst-20 LM delta +$1.44M, PRE LM mean -14,572 (MDE 36,635). I would NOT carry it as a rule that helps: it fails all 8 gates (WF raw -20,053/wk, HOLD LM -153 but HOLD maxDD LM +264k, the 20 audit worst weeks gain only because 36% of ALL entries are removed). If F needs a concurrency rule anyway, the only one with the right sign on both PRE and HOLD mean is D_L40s (near-free, near-zero effect). Recommendation for F: do not stack section D.

### Trade-off line (lot-matched, whole 185-week span, base worst-20 = -$3.74M)
D_B2s: saved +$711k in the 20 worst weeks (+35.6k/wk), given up -$2.68M in the other 165 (-16.3k/wk), net -$1.97M. D_L20s: +$475k vs -$2.00M. D_B3s: +$172k vs -$1.08M. D_B3h: +$424k vs -$1.20M. D_L40s: +$13k vs +$155k (net +$167k, i.e. free but nil). Raw versions and the losing-vs-winning week split are in the trade-off table below. The caps give up $2-6 for every $1 saved in the worst weeks, worse than the volatility gates of D3DVG.

## Disclosures (read these)
- Smoke test before the prereg: a base-only reproduction (WF 45,947.3/wk, 185 label weeks) and counts of entries a cap would touch (40.7/18.0/3.1% lots>20/30/40; 45.0/25.5/10.7% with >=2/3/4 same-side books open) and the PRE per-book edge rank (KB 17.6, SM 15.1, PE 10.0, ST 8.0, HM 6.0, WT 4.6 $/1000 lot-seconds) were printed before the prereg was written; no cell P&L. Prereg sha256 above written after those and before any cell score.
- Defect found after the first PRE scoring run (PRE only, no HOLD/X number read): pass 2 of the cap pass used only rows filled in pass 1, so entries skipped in pass 1 reverted to full size (affected shares appeared as 3% / 1% / 0% / 4% instead of 29% / 11% / 2% / 36%; first-run PRE LM means D_L20s +1,016, D_B2s +2,622). Definition unchanged; fix: candidates are all base-filled rows in every pass (a skipped row stays a candidate), exits come from the previous pass where the row filled. That run is kept as `out/stk_d/pre_results_BUGGY_pass2.json`; all reported numbers are from the corrected run (placebos 200 + 200 draws, corrected). The HOLD / X look happened only after the corrected PRE text was logged.
- Implementation simplifications (all in the prereg): a skipped entry is removed after the book's busy chain (the book stays flat); "largest edge keeps it" is implemented as exemption of the two highest PRE-edge books (KB, SM) from the cap (D_B3e), not as pre-emption of an open position (exits are dead); the 2x-cost row reuses the 1x multipliers; placebos use one engine pass, actual cells two (PRE raw mean differs by <= 1.8k between pass 1 and 2; pass-2 results reported). MM (mean-matched) is not solvable for D_B2s on PRE (c_MM would exceed the 3.0 bracket), so its G7 fails by construction; c_MM for D_L40s is 0.95 (the cell is already above base mean on PRE).
- Lot-matching raises the lots by c_LM 1.02-1.50; total weighted lots (both directions) already peak at 50.0 in the base, so a lot-matched cap cell exceeds the 50-contract concurrent cap and is not live-eligible in that form; the raw rows (cap respected) are the live-eligible reading, and they lose money.
- Exits in the engine are size-dependent only through the lock thresholds (locks stay in nominal-lot R, as in D3DVG): halving/removing entries changes which locks trigger, which is included.
- The span 2023-04..2026-10 follows D3D2A/D3DVG (HOLD includes 2026-02..2026-10 as in those official series); nothing after 2026-10-16.


## Verdict table (9 cells)
WF = 2024-02..2026-10 (142 wk), LM = lot-matched (c from PRE lot-seconds), PRE = 2024-02..2025-06 (75 wk), HOLD = 2025-07..2026-10 (68 wk), X = 2023-04..2024-01 (44 wk). MDE = 2.8 SD_diff/sqrt(n) of the paired weekly delta.

| cell | rule | entries affected | tier | failed gates | WF raw d_mean [CI] (MDE) | WF LM d_mean | PRE LM d_mean | HOLD LM d_mean (MDE) | WF raw d_Sharpe |
|---|---|---|---|---|---|---|---|---|---|
| D_L20s | lots cap 20, first-in keeps the slot | 29% | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | -16,176 [-31,016,-2,142] (20,653) | -3,731 | -9,420 | +2,598 (32,535) | -0.34 |
| D_L30s | lots cap 30, first-in | 11% | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | -7,470 [-16,305,+1,079] (12,538) | -1,441 | -8,252 | +6,094 (17,187) | -0.10 |
| D_L40s | lots cap 40, first-in | 2% | DEAD | G2,G3,G4,G6 | +1,788 [-1,176,+4,839] (4,295) | +2,875 | +3,385 | +2,270 (5,531) | +0.18 |
| D_B2s | max 2 books per direction, later skipped | 36% | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | -20,053 [-36,582,-4,129] (23,252) | -7,770 | -14,572 | -153 (37,369) | -0.54 |
| D_B3s | max 3 books per direction, later skipped | 18% | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | -9,953 [-21,075,+774] (15,657) | -2,011 | -6,063 | +2,488 (22,048) | -0.19 |
| D_B4s | max 4 books per direction, later skipped | 7% | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | -3,624 [-10,084,+2,843] (9,233) | -113 | -648 | +478 (12,477) | -0.03 |
| D_B3h | max 3 books per direction, later halved | 25% | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | -5,771 [-14,604,+3,121] (12,703) | -1,614 | -2,527 | -584 (17,281) | -0.06 |
| D_B3e | max 3 books per direction, top-2 PRE-edge books (KB,SM) exempt so the lower-edge books are the ones squeezed out ("largest edge keeps it") | 16% | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | -10,057 [-20,344,-164] (14,451) | -3,334 | -8,614 | +2,538 (20,220) | -0.24 |
| D_L30t | lots cap 30, later entry trimmed to the room left | 13% | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | -5,119 [-11,945,+1,718] (9,811) | -1,657 | -3,811 | +743 (13,675) | -0.11 |

Gates (as D3DVG, never softened; G4 placebos = matched random thinning AND direction shuffle, 200 draws each, both >= 0.95 in PRE and HOLD): G1 LM mean>0 PRE&HOLD; G2 HOLD CI low>0; G3 LM maxDD<=0 & worst>=0 PRE&HOLD; G4; G5 >=2 of 3 years positive, none >60%; G6 X LM mean>=0, maxDD<=0, worst>=0; G7 mean-matched SD,maxDD<=0 & worst>=0 PRE&HOLD; G8 2x-cost WF LM>0. Best-of-F bar HOLD p <= 0.05/60 = 0.000833.

## Per window detail (raw and lot-matched; base mean/SD/maxDD/worst, cell deltas)

### PRE (75 wk); base mean 44,127, SD 131,184, maxDD 477,701, worst -306,664

| cell | basis | d_mean [CI iid] (MDE) | d_SD | d_maxDD | d_worst | placebo rank thin/dir (mean) | rank worst thin/dir |
|---|---|---|---|---|---|---|---|
| D_L20s | raw | -19,647 [-40,674,+1,422] (30,099) | -45,976 | -67,382 | +117,359 | - | - |
| D_L20s | LM | -9,420 [-31,430,+12,602] (31,381) | -9,964 | +106,475 | +37,223 | 0.12/0.15 | 0.92/0.98 |
| D_L20s | MM | -0 [-26,846,+27,170] (38,684) | +37,308 | +352,020 | -73,172 | 0.33/0.27 | 0.35/0.50 |
| D_L30s | raw | -13,112 [-25,922,+158] (18,728) | -25,999 | +11,898 | +49,518 | - | - |
| D_L30s | LM | -8,252 [-21,053,+4,588] (18,261) | -9,517 | +88,617 | +9,223 | 0.07/0.01 | 0.79/0.91 |
| D_L30s | MM | +0 [-14,530,+14,394] (20,929) | +19,058 | +222,490 | -60,834 | 0.77/0.76 | 0.23/0.17 |
| D_L40s | raw | +2,327 [-2,104,+6,996] (6,472) | -6,798 | -65,784 | +13,233 | - | - |
| D_L40s | LM | +3,385 [-879,+7,909] (6,289) | -3,965 | -56,404 | +6,551 | 0.94/1.00 | 0.70/0.81 |
| D_L40s | MM | -0 [-5,013,+5,207] (7,277) | -13,030 | -86,420 | +27,934 | 0.08/0.10 | 0.92/0.98 |
| D_B2s | raw | -24,044 [-47,836,-373] (33,798) | -48,955 | -70,727 | +117,359 | - | - |
| D_B2s | LM | -14,572 [-40,650,+11,066] (36,635) | -8,004 | +134,072 | +22,446 | 0.09/0.04 | 0.82/0.97 |
| D_B2s | MM | n/a (c_MM unsolvable on PRE) | | | | | |
| D_B3s | raw | -12,944 [-29,009,+3,459] (23,305) | -25,620 | -71,521 | +49,518 | - | - |
| D_B3s | LM | -6,063 [-22,937,+10,695] (24,078) | -2,327 | +18,101 | -7,220 | 0.24/0.14 | 0.57/0.86 |
| D_B3s | MM | -0 [-18,774,+18,524] (26,632) | +18,588 | +98,999 | -58,299 | 0.50/0.45 | 0.36/0.42 |
| D_B4s | raw | -3,979 [-13,584,+5,719] (13,933) | -15,172 | -89,578 | +21,173 | - | - |
| D_B4s | LM | -648 [-10,137,+8,739] (13,689) | -5,548 | -57,383 | -2,509 | 0.47/0.51 | 0.57/0.85 |
| D_B4s | MM | +0 [-9,528,+9,439] (13,724) | -3,674 | -51,114 | -7,121 | 0.95/0.95 | 0.57/0.70 |
| D_B3h | raw | -6,428 [-19,399,+6,712] (18,542) | -17,407 | -53,829 | +52,041 | - | - |
| D_B3h | LM | -2,527 [-15,515,+10,578] (18,648) | -5,635 | -9,973 | +25,696 | 0.45/0.50 | 0.94/1.00 |
| D_B3h | MM | +0 [-13,364,+13,411] (19,125) | +1,991 | +18,439 | +8,629 | 0.86/0.82 | 0.80/0.95 |
| D_B3e | raw | -14,216 [-28,817,+551] (21,200) | -21,904 | -80,282 | +22,288 | - | - |
| D_B3e | LM | -8,614 [-23,755,+6,362] (21,779) | -1,435 | -5,842 | -30,977 | 0.05/0.04 | 0.34/0.36 |
| D_B3e | MM | +0 [-18,697,+18,343] (26,548) | +32,189 | +118,809 | -119,238 | 0.74/0.76 | 0.07/0.04 |
| D_L30t | raw | -6,963 [-16,830,+3,121] (14,411) | -15,705 | -64,781 | +19,835 | - | - |
| D_L30t | LM | -3,811 [-13,461,+6,113] (14,177) | -5,912 | -29,766 | -4,487 | 0.21/0.09 | 0.59/0.89 |
| D_L30t | MM | +0 [-9,998,+10,431] (14,821) | +5,930 | +12,578 | -33,901 | 0.54/0.54 | 0.34/0.45 |

### HOLD (68 wk); base mean 47,279, SD 140,987, maxDD 601,016, worst -318,557

| cell | basis | d_mean [CI iid] (MDE) | d_SD | d_maxDD | d_worst | placebo rank thin/dir (mean) | rank worst thin/dir |
|---|---|---|---|---|---|---|---|
| D_L20s | raw | -12,110 [-30,709,+6,888] (27,171) | -22,283 | -13,809 | +85,994 | - | - |
| D_L20s | LM | +2,598 [-19,473,+25,611] (32,535) | +27,897 | +235,810 | -12,453 | 0.25/0.03 | 0.71/0.86 |
| D_L20s | MM | +16,634 [-16,379,+50,597] (48,648) | +94,130 | +611,630 | -147,381 | 0.65/0.46 | 0.17/0.16 |
| D_L30s | raw | -1,137 [-12,092,+9,782] (15,765) | -8,459 | -15,170 | +42,944 | - | - |
| D_L30s | LM | +6,094 [-5,930,+18,255] (17,187) | +12,308 | +76,632 | -245 | 0.57/0.76 | 0.69/0.87 |
| D_L30s | MM | +18,415 [+1,328,+35,463] (24,744) | +48,319 | +236,349 | -75,356 | 0.90/0.99 | 0.13/0.08 |
| D_L40s | raw | +1,166 [-2,471,+5,089] (5,474) | -1,645 | -10,482 | +0 | - | - |
| D_L40s | LM | +2,270 [-1,424,+6,266] (5,531) | +1,528 | +2,966 | -7,254 | 0.60/1.00 | 0.27/0.14 |
| D_L40s | MM | -1,261 [-5,284,+3,043] (6,062) | -8,626 | -40,067 | +15,959 | 0.23/0.07 | 0.81/0.98 |
| D_B2s | raw | -15,356 [-36,138,+6,083] (30,808) | -27,055 | -24,704 | +111,086 | - | - |
| D_B2s | LM | -153 [-25,931,+26,024] (37,369) | +29,727 | +264,392 | +7,007 | 0.17/0.04 | 0.94/0.99 |
| D_B2s | MM | n/a (c_MM unsolvable on PRE) | | | | | |
| D_B3s | raw | -6,508 [-20,744,+7,677] (20,194) | -14,859 | -20,444 | +37,567 | - | - |
| D_B3s | LM | +2,488 [-12,686,+18,056] (22,048) | +12,971 | +107,657 | -24,432 | 0.27/0.26 | 0.43/0.61 |
| D_B3s | MM | +10,428 [-7,913,+29,267] (26,618) | +37,966 | +223,480 | -80,225 | 0.49/0.63 | 0.27/0.21 |
| D_B4s | raw | -3,180 [-11,061,+5,079] (11,663) | -2,557 | -58,640 | +13,877 | - | - |
| D_B4s | LM | +478 [-8,070,+9,408] (12,477) | +8,927 | -13,648 | -11,397 | 0.21/0.40 | 0.45/0.47 |
| D_B4s | MM | +1,191 [-7,516,+10,355] (12,769) | +11,162 | -4,888 | -16,318 | 0.30/0.40 | 0.47/0.49 |
| D_B3h | raw | -4,962 [-16,793,+6,376] (16,724) | -9,640 | -59,595 | +28,180 | - | - |
| D_B3h | LM | -584 [-12,584,+11,378] (17,281) | +3,950 | -3,576 | -1,864 | 0.12/0.09 | 0.55/0.76 |
| D_B3h | MM | +2,253 [-10,446,+14,938] (18,265) | +12,755 | +32,715 | -21,328 | 0.21/0.20 | 0.48/0.70 |
| D_B3e | raw | -5,321 [-18,439,+8,016] (18,961) | -14,348 | -68,248 | +31,188 | - | - |
| D_B3e | LM | +2,538 [-11,352,+16,937] (20,220) | +9,373 | +31,543 | -22,638 | 0.25/0.37 | 0.39/0.37 |
| D_B3e | MM | +14,719 [-4,285,+33,983] (27,772) | +48,377 | +198,554 | -111,728 | 0.79/0.91 | 0.04/0.03 |
| D_L30t | raw | -3,010 [-12,276,+5,760] (12,889) | -3,275 | -4,434 | +13,843 | - | - |
| D_L30t | LM | +743 [-8,968,+10,166] (13,675) | +8,403 | +46,155 | -11,996 | 0.29/0.17 | 0.34/0.38 |
| D_L30t | MM | +5,283 [-6,016,+16,483] (15,946) | +22,525 | +107,333 | -43,244 | 0.53/0.66 | 0.20/0.07 |

### X 2023-04..2024-01 (44 wk); base mean 20,616, SD 112,784, maxDD 553,090, worst -157,300

| cell | basis | d_mean [CI iid] (MDE) | d_SD | d_maxDD | d_worst | placebo rank thin/dir (mean) | rank worst thin/dir |
|---|---|---|---|---|---|---|---|
| D_L20s | raw | -21,909 [-44,538,+822] (32,690) | -39,478 | +123,425 | +30,236 | - | - |
| D_L20s | LM | -22,532 [-45,813,+969] (33,735) | -8,497 | +411,280 | -23,527 | 0.06/0.04 | 0.91/0.86 |
| D_L20s | MM | -26,056 [-54,606,+3,093] (41,824) | +32,137 | +855,568 | -96,138 | 0.02/0.02 | 0.31/0.25 |
| D_L30s | raw | -16,437 [-29,976,-2,659] (19,875) | -25,404 | -26,217 | +6,711 | - | - |
| D_L30s | LM | -15,782 [-28,352,-2,752] (18,664) | -11,712 | +56,344 | -16,886 | 0.00/0.00 | 0.79/0.62 |
| D_L30s | MM | -14,763 [-28,787,-339] (20,633) | +12,024 | +200,123 | -57,892 | 0.01/0.00 | 0.30/0.10 |
| D_L40s | raw | -5,813 [-10,478,-1,036] (6,876) | -5,768 | -29,839 | -16,591 | - | - |
| D_L40s | LM | -5,475 [-10,020,-920] (6,653) | -3,331 | -17,923 | -20,551 | 0.04/0.00 | 0.15/0.04 |
| D_L40s | MM | -6,554 [-11,844,-1,135] (7,832) | -11,129 | -56,053 | -7,879 | 0.01/0.00 | 0.59/0.31 |
| D_B2s | raw | -19,785 [-43,662,+3,818] (34,521) | -39,960 | +15,919 | +43,918 | - | - |
| D_B2s | LM | -19,719 [-45,359,+5,399] (36,899) | -3,694 | +308,252 | -12,939 | 0.10/0.10 | 0.94/0.94 |
| D_B2s | MM | n/a (c_MM unsolvable on PRE) | | | | | |
| D_B3s | raw | -15,376 [-31,589,+435] (23,363) | -21,120 | -17,143 | +7,168 | - | - |
| D_B3s | LM | -14,219 [-30,205,+2,072] (23,862) | -895 | +101,112 | -25,958 | 0.06/0.01 | 0.73/0.47 |
| D_B3s | MM | -13,256 [-31,383,+5,171] (26,735) | +17,264 | +209,230 | -55,766 | 0.07/0.01 | 0.48/0.20 |
| D_B4s | raw | -11,275 [-20,089,-2,550] (12,739) | -11,295 | -48,599 | -1,655 | - | - |
| D_B4s | LM | -10,500 [-18,811,-1,841] (12,353) | -2,877 | -6,750 | -14,840 | 0.01/0.00 | 0.72/0.18 |
| D_B4s | MM | -10,349 [-18,732,-1,687] (12,396) | -1,238 | +1,398 | -17,408 | 0.01/0.00 | 0.68/0.28 |
| D_B3h | raw | -13,170 [-25,664,-628] (18,253) | -15,642 | +62,865 | +1,023 | - | - |
| D_B3h | LM | -12,400 [-24,718,+17] (18,031) | -5,591 | +126,595 | -15,147 | 0.01/0.00 | 0.67/0.41 |
| D_B3h | MM | -11,901 [-24,441,+868] (18,415) | +920 | +167,882 | -25,622 | 0.01/0.00 | 0.60/0.45 |
| D_B3e | raw | -18,643 [-33,104,-4,185] (21,193) | -17,632 | +3,780 | -6,875 | - | - |
| D_B3e | LM | -18,274 [-32,707,-3,553] (21,622) | +190 | +108,086 | -37,626 | 0.00/0.00 | 0.47/0.12 |
| D_B3e | MM | -18,062 [-36,584,+1,006] (27,266) | +29,469 | +289,990 | -88,643 | 0.00/0.00 | 0.10/0.03 |
| D_L30t | raw | -13,647 [-24,468,-2,955] (15,636) | -16,493 | +1,505 | +2,913 | - | - |
| D_L30t | LM | -13,056 [-23,437,-2,760] (15,000) | -8,327 | +48,534 | -10,179 | 0.00/0.00 | 0.81/0.57 |
| D_L30t | MM | -12,341 [-22,864,-1,803] (15,270) | +1,547 | +105,406 | -26,011 | 0.00/0.00 | 0.46/0.21 |

### WF (142 wk); base mean 45,947, SD 136,281, maxDD 601,016, worst -318,557

| cell | basis | d_mean [CI iid] (MDE) | d_SD | d_maxDD | d_worst | placebo rank thin/dir (mean) | rank worst thin/dir |
|---|---|---|---|---|---|---|---|
| D_L20s | raw | -16,176 [-31,016,-2,142] (20,653) | -33,796 | +31,295 | +85,994 | - | - |
| D_L20s | LM | -3,731 [-19,658,+11,948] (22,849) | +9,523 | +299,450 | -12,453 | 0.09/0.01 | 0.86/0.94 |
| D_L20s | MM | +7,965 [-13,501,+29,500] (31,018) | +66,564 | +682,692 | -147,381 | 0.65/0.46 | 0.19/0.23 |
| D_L30s | raw | -7,470 [-16,305,+1,079] (12,538) | -17,018 | +82,077 | +42,944 | - | - |
| D_L30s | LM | -1,441 [-10,454,+7,425] (12,786) | +1,670 | +189,117 | -245 | 0.17/0.05 | 0.89/0.95 |
| D_L30s | MM | +8,818 [-2,255,+20,247] (16,302) | +34,072 | +376,582 | -75,356 | 0.90/0.99 | 0.23/0.11 |
| D_L40s | raw | +1,788 [-1,176,+4,839] (4,295) | -4,253 | -10,482 | +0 | - | - |
| D_L40s | LM | +2,875 [-17,+5,904] (4,235) | -1,247 | +2,966 | -7,254 | 0.91/1.00 | 0.35/0.20 |
| D_L40s | MM | -604 [-3,977,+2,820] (4,806) | -10,868 | -40,067 | +15,959 | 0.23/0.07 | 0.85/0.99 |
| D_B2s | raw | -20,053 [-36,582,-4,129] (23,252) | -37,619 | -24,704 | +111,086 | - | - |
| D_B2s | LM | -7,770 [-26,361,+10,502] (26,456) | +11,534 | +264,392 | +7,007 | 0.06/0.01 | 0.98/1.00 |
| D_B2s | MM | n/a (c_MM unsolvable on PRE) | | | | | |
| D_B3s | raw | -9,953 [-21,075,+774] (15,657) | -20,293 | -20,444 | +37,567 | - | - |
| D_B3s | LM | -2,011 [-13,434,+9,368] (16,524) | +5,299 | +107,657 | -24,432 | 0.21/0.12 | 0.57/0.76 |
| D_B3s | MM | +4,994 [-7,980,+18,080] (18,965) | +28,281 | +223,480 | -80,225 | 0.49/0.63 | 0.34/0.28 |
| D_B4s | raw | -3,624 [-10,084,+2,843] (9,233) | -8,977 | -58,640 | +13,877 | - | - |
| D_B4s | LM | -113 [-6,656,+6,437] (9,361) | +1,583 | -13,648 | -11,397 | 0.25/0.47 | 0.64/0.56 |
| D_B4s | MM | +570 [-6,057,+7,242] (9,462) | +3,639 | -4,888 | -16,318 | 0.30/0.40 | 0.58/0.54 |
| D_B3h | raw | -5,771 [-14,604,+3,121] (12,703) | -14,014 | -59,595 | +28,180 | - | - |
| D_B3h | LM | -1,614 [-10,426,+7,458] (12,892) | -1,363 | -3,576 | -1,864 | 0.15/0.17 | 0.75/0.91 |
| D_B3h | MM | +1,079 [-8,103,+10,526] (13,371) | +6,832 | +32,715 | -21,328 | 0.21/0.20 | 0.62/0.76 |
| D_B3e | raw | -10,057 [-20,344,-164] (14,451) | -18,191 | -24,135 | +31,188 | - | - |
| D_B3e | LM | -3,334 [-13,818,+6,888] (15,070) | +3,928 | +83,919 | -22,638 | 0.07/0.07 | 0.58/0.55 |
| D_B3e | MM | +7,048 [-6,272,+20,432] (19,343) | +40,279 | +266,233 | -111,728 | 0.79/0.91 | 0.09/0.05 |
| D_L30t | raw | -5,119 [-11,945,+1,718] (9,811) | -9,630 | -4,434 | +13,843 | - | - |
| D_L30t | LM | -1,657 [-8,526,+5,293] (9,946) | +1,110 | +46,155 | -11,996 | 0.13/0.07 | 0.55/0.65 |
| D_L30t | MM | +2,530 [-5,004,+10,285] (10,917) | +14,098 | +107,333 | -43,244 | 0.53/0.66 | 0.29/0.20 |

## By year (WF summed weekly delta, raw / lot-matched) and the 2023 span
| cell | 2024 raw/LM | 2025 raw/LM | 2026 raw/LM | X 2023-04..2024-01 raw/LM sum | X LM maxDD / worst delta |
|---|---|---|---|---|---|
| D_L20s | -433,335/+202,110 | -1,493,755/-944,253 | -369,922/+212,317 | -964,014/-991,393 | +411,280 / -23,527 |
| D_L30s | -250,339/+15,820 | -973,275/-685,343 | +162,887/+464,966 | -723,207/-694,389 | +56,344 / -16,886 |
| D_L40s | +166,492/+214,663 | -39,175/+23,939 | +126,548/+169,619 | -255,754/-240,922 | -17,923 / -20,551 |
| D_B2s | -594,580/+57,132 | -1,867,093/-1,429,062 | -385,843/+268,627 | -870,551/-867,649 | +308,252 / -12,939 |
| D_B3s | -202,850/+182,404 | -1,154,042/-788,493 | -56,411/+320,556 | -676,525/-625,647 | +101,112 / -25,958 |
| D_B4s | -13,023/+147,560 | -420,039/-221,724 | -81,580/+58,053 | -496,083/-461,987 | -6,750 / -14,840 |
| D_B3h | +118,918/+332,863 | -1,000,501/-813,201 | +62,102/+251,132 | -579,496/-545,600 | +126,595 / -15,147 |
| D_B3e | -358,248/-60,313 | -990,104/-649,082 | -79,719/+235,922 | -820,300/-804,039 | +108,086 / -37,626 |
| D_L30t | -64,960/+94,792 | -609,219/-422,534 | -52,723/+92,464 | -600,453/-574,448 | +48,534 / -10,179 |

## Worst 20 / best 20 weeks (sums of weekly $ over those weeks)
WORST-20 list = the audit's 20 worst weeks (audit_lib.worst20, full 185 label weeks; base sum -3,735,079; of them 5 in PRE, 8 in HOLD, 7 in X). PRE-ONLY re-derived worst 20 (of 75 PRE weeks): base sum -2,304,797. Delta = cell minus base; positive = the cap saved money in those weeks.

| cell | basis | worst-20 (audit) delta | of which PRE / HOLD / X weeks | worst-20 PRE-only delta | best-20 (audit) delta | best-20 PRE-only delta | all other weeks delta (full 185) | worst-20 cell $ | share of entries affected: worst20 / best20 / mid |
|---|---|---|---|---|---|---|---|---|---|
| D_L20s | raw | +1,445,065 | +598,510 / +359,120 / +487,435 | +1,454,513 | -2,291,010 | -1,983,650 | -4,706,090 | -2,290,014 | 29% / 29% / 29% |
| D_L20s | LM | +474,536 | +362,068 / -147,997 / +260,466 | +1,092,728 | -1,007,180 | -1,157,333 | -1,995,756 | -3,260,542 | 29% / 29% / 29% |
| D_L30s | raw | +673,420 | +332,051 / +80,933 / +260,436 | +776,100 | -1,023,933 | -1,065,580 | -2,457,355 | -3,061,659 | 11% / 11% / 11% |
| D_L30s | LM | +193,660 | +202,887 / -150,139 / +140,912 | +536,555 | -348,454 | -614,501 | -1,092,606 | -3,541,419 | 11% / 11% / 11% |
| D_L40s | raw | +95,418 | +100,885 / -28,494 / +23,027 | +325,146 | -84,916 | -122,799 | -97,306 | -3,639,661 | 3% / 2% / 2% |
| D_L40s | LM | +12,537 | +76,851 / -64,566 / +252 | +280,066 | +34,628 | -35,779 | +154,763 | -3,722,542 | 3% / 2% / 2% |
| D_B2s | raw | +1,724,650 | +699,327 / +470,451 / +554,872 | +1,737,406 | -2,468,294 | -2,325,115 | -5,442,717 | -2,010,429 | 34% / 36% / 36% |
| D_B2s | LM | +711,199 | +468,536 / -76,505 / +319,168 | +1,444,108 | -1,051,659 | -1,528,957 | -2,682,151 | -3,023,880 | 34% / 36% / 36% |
| D_B3s | raw | +816,172 | +443,243 / +99,675 / +273,254 | +966,175 | -1,363,462 | -1,093,746 | -2,906,000 | -2,918,907 | 17% / 18% / 18% |
| D_B3s | LM | +172,126 | +285,903 / -221,559 / +107,783 | +670,813 | -487,246 | -464,804 | -1,083,307 | -3,562,952 | 17% / 18% / 18% |
| D_B4s | raw | +289,447 | +241,922 / -28,984 / +76,509 | +505,490 | -425,518 | -534,302 | -1,300,172 | -3,445,631 | 7% / 7% / 7% |
| D_B4s | LM | +3,625 | +166,070 / -160,424 / -2,020 | +356,234 | -18,301 | -251,444 | -481,724 | -3,731,453 | 7% / 7% / 7% |
| D_B3h | raw | +734,745 | +415,515 / +143,480 / +175,750 | +711,955 | -771,957 | -576,628 | -2,133,722 | -3,000,334 | 23% / 26% / 26% |
| D_B3h | LM | +424,314 | +338,866 / -2,621 / +88,068 | +547,150 | -299,881 | -228,200 | -1,199,120 | -3,310,765 | 23% / 26% / 26% |
| D_B3e | raw | +715,055 | +365,035 / +154,016 / +196,003 | +751,672 | -1,198,569 | -980,328 | -2,963,426 | -3,020,024 | 15% / 16% / 16% |
| D_B3e | LM | +149,383 | +216,821 / -108,502 / +41,064 | +460,760 | -423,862 | -425,174 | -1,426,895 | -3,585,696 | 15% / 16% / 16% |
| D_L30t | raw | +354,990 | +255,236 / -68,581 / +168,336 | +423,876 | -630,309 | -570,584 | -1,682,345 | -3,380,089 | 13% / 12% / 13% |
| D_L30t | LM | +68,366 | +178,825 / -206,305 / +95,845 | +264,378 | -231,395 | -284,508 | -878,092 | -3,666,713 | 13% / 12% / 13% |

## Trade-off line (dollars given up in good weeks vs saved in bad weeks), whole 185-week span
'Bad' = the audit's 20 worst base weeks; 'good/other' = the other 165 weeks. Also losing base weeks (base < 0) vs winning weeks. Per-week average in brackets.

| cell | basis | saved in 20 worst weeks | given up in other 165 weeks | net | saved in losing weeks (n) | given up in winning weeks (n) |
|---|---|---|---|---|---|---|
| D_L20s | raw | +1,445,065 (+72,253/wk) | -4,706,090 (-28,522/wk) | -3,261,025 | +3,382,095 (71) | -6,643,121 (114) |
| D_L20s | LM | +474,536 (+23,727/wk) | -1,995,756 (-12,095/wk) | -1,521,220 | +2,118,416 (71) | -3,639,636 (114) |
| D_L30s | raw | +673,420 (+33,671/wk) | -2,457,355 (-14,893/wk) | -1,783,935 | +1,800,947 (71) | -3,584,882 (114) |
| D_L30s | LM | +193,660 (+9,683/wk) | -1,092,606 (-6,622/wk) | -898,946 | +1,088,138 (71) | -1,987,084 (114) |
| D_L40s | raw | +95,418 (+4,771/wk) | -97,306 (-590/wk) | -1,888 | +573,640 (71) | -575,528 (114) |
| D_L40s | LM | +12,537 (+627/wk) | +154,763 (+938/wk) | +167,299 | +442,106 (71) | -274,807 (114) |
| D_B2s | raw | +1,724,650 (+86,233/wk) | -5,442,717 (-32,986/wk) | -3,718,067 | +4,022,290 (71) | -7,740,357 (114) |
| D_B2s | LM | +711,199 (+35,560/wk) | -2,682,151 (-16,255/wk) | -1,970,952 | +2,821,099 (71) | -4,792,051 (114) |
| D_B3s | raw | +816,172 (+40,809/wk) | -2,906,000 (-17,612/wk) | -2,089,828 | +2,210,519 (71) | -4,300,347 (114) |
| D_B3s | LM | +172,126 (+8,606/wk) | -1,083,307 (-6,565/wk) | -911,180 | +1,297,193 (71) | -2,208,374 (114) |
| D_B4s | raw | +289,447 (+14,472/wk) | -1,300,172 (-7,880/wk) | -1,010,725 | +918,070 (71) | -1,928,795 (114) |
| D_B4s | LM | +3,625 (+181/wk) | -481,724 (-2,920/wk) | -478,099 | +467,493 (71) | -945,592 (114) |
| D_B3h | raw | +734,745 (+36,737/wk) | -2,133,722 (-12,932/wk) | -1,398,977 | +1,447,103 (71) | -2,846,080 (114) |
| D_B3h | LM | +424,314 (+21,216/wk) | -1,199,120 (-7,267/wk) | -774,806 | +939,838 (71) | -1,714,644 (114) |
| D_B3e | raw | +715,055 (+35,753/wk) | -2,963,426 (-17,960/wk) | -2,248,371 | +1,659,269 (71) | -3,907,640 (114) |
| D_B3e | LM | +149,383 (+7,469/wk) | -1,426,895 (-8,648/wk) | -1,277,512 | +780,692 (71) | -2,058,204 (114) |
| D_L30t | raw | +354,990 (+17,750/wk) | -1,682,345 (-10,196/wk) | -1,327,355 | +941,453 (71) | -2,268,809 (114) |
| D_L30t | LM | +68,366 (+3,418/wk) | -878,092 (-5,322/wk) | -809,726 | +482,834 (71) | -1,292,560 (114) |

Lot-matched rows are the lot-matched version of the same line (c_LM scales the lots so the cell trades the same PRE lot-seconds as the unchanged stack; c_LM values below).

## Entries affected, lot-match scale, peak
| cell | entries affected (all / skipped) | by year 2023/24/25/26 | by book ST/HM/WT/KB/SM/PE | c_LM | c_MM | peak total weighted lots | pass1 vs pass2 PRE raw mean |
|---|---|---|---|---|---|---|---|
| D_L20s | 29.3% / 29.3% | 36%/34%/28%/24% | 34%/43%/37%/17%/22%/18% | 1.423 | 1.981 | 49.8 | 23,865 vs 24,480 |
| D_L30s | 11.0% / 11.0% | 14%/13%/10%/8% | 13%/23%/11%/5%/9%/5% | 1.157 | 1.428 | 50.0 | 31,124 vs 31,015 |
| D_L40s | 1.9% / 1.9% | 3%/2%/1%/1% | 2%/3%/2%/1%/4%/1% | 1.023 | 0.950 | 50.0 | 46,454 vs 46,454 |
| D_B2s | 35.7% / 35.7% | 40%/38%/36%/32% | 36%/44%/44%/31%/27%/26% | 1.499 | nan | 49.8 | 18,332 vs 20,083 |
| D_B3s | 18.2% / 18.2% | 20%/20%/19%/15% | 17%/27%/21%/16%/14%/11% | 1.221 | 1.419 | 50.0 | 30,851 vs 31,183 |
| D_B4s | 7.3% / 7.3% | 8%/8%/8%/6% | 6%/13%/8%/5%/6%/4% | 1.083 | 1.099 | 50.0 | 40,116 vs 40,148 |
| D_B3h | 25.5% / 0.0% | 28%/28%/26%/22% | 23%/32%/34%/22%/17%/17% | 1.103 | 1.170 | 50.0 | 37,474 vs 37,699 |
| D_B3e | 16.1% / 16.1% | 18%/17%/17%/14% | 19%/29%/26%/0%/0%/12% | 1.187 | 1.495 | 50.0 | 29,673 vs 29,911 |
| D_L30t | 12.8% / 3.5% | 17%/16%/12%/9% | 13%/24%/14%/8%/11%/7% | 1.085 | 1.187 | 50.0 | 36,981 vs 37,165 |

## PRE-to-HOLD stability of the effect (sign of the LM mean delta and of the worst-20 relation)
| cell | PRE LM d_mean | HOLD LM d_mean | X LM d_mean | same sign PRE/HOLD/X |
|---|---|---|---|---|
| D_L20s | -9,420 | +2,598 | -22,532 | no |
| D_L30s | -8,252 | +6,094 | -15,782 | no |
| D_L40s | +3,385 | +2,270 | -5,475 | no |
| D_B2s | -14,572 | -153 | -19,719 | yes |
| D_B3s | -6,063 | +2,488 | -14,219 | no |
| D_B4s | -648 | +478 | -10,500 | no |
| D_B3h | -2,527 | -584 | -12,400 | yes |
| D_B3e | -8,614 | +2,538 | -18,274 | no |
| D_L30t | -3,811 | +743 | -13,056 | no |

## Per-book contribution to the WF raw delta ($/wk, nominal x weight, before sweep)
| cell | ST | HM | WT | KB | SM | PE |
|---|---|---|---|---|---|---|
| D_L20s | -5,218 | -5,269 | -2,397 | -1,289 | +187 | -2,190 |
| D_L30s | -1,713 | -4,075 | -684 | -669 | +700 | -1,030 |
| D_L40s | +676 | +159 | +232 | -99 | +779 | +40 |
| D_B2s | -5,186 | -5,255 | -2,325 | -3,073 | -591 | -3,623 |
| D_B3s | -1,365 | -4,360 | -663 | -1,407 | -11 | -2,147 |
| D_B4s | -575 | -1,419 | -1,398 | -411 | +538 | -360 |
| D_B3h | +1,096 | -1,739 | -907 | -1,944 | +158 | -2,435 |
| D_B3e | -1,753 | -5,490 | -1,474 | +0 | +0 | -1,341 |
| D_L30t | -463 | -2,855 | -673 | -1,043 | +684 | -770 |

## 2x cost (WF, engine cm 2 + sweep x2, multipliers from the 1x pass)
| cell | raw d_mean | LM d_mean |
|---|---|---|
| D_L20s | -13,883 | -7,340 |
| D_L30s | -8,768 | -5,439 |
| D_L40s | +409 | +1,101 |
| D_B2s | -17,790 | -12,917 |
| D_B3s | -11,498 | -7,414 |
| D_B4s | -4,878 | -2,793 |
| D_B3h | -6,201 | -3,738 |
| D_B3e | -11,575 | -8,122 |
| D_L30t | -7,826 | -5,945 |
