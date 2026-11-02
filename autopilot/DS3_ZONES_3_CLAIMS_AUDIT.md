# DS3_ZONES_3_CLAIMS_AUDIT - independent re-computation of the headline numbers behind DS3_ZONES_3.md sections 15-17 and MORNING_FLAGS.md (Z3, 2026-11-02 ~13:10Z)
Method: every engine number was re-run by me from the base modules (`d7_v13x/y/z.run_*`, no BASE-4 pickles used) with my own window/maxDD code (`zones3_s3/audit_an.py`: weekly = ISO week of the label day, maxDD = weekly-cumulative peak-to-trough, windows from `s3_v13y/calendar.npz` = cap/windows.py); stored tables (layer-vs-size draws, ZL-1 base rows, ZL-3 split totals, noise-band draws) were re-aggregated by me from the raw per-draw / per-trade arrays and, where possible, reconciled to a FRESH engine run. Scripts: `audit_run.py`, `audit_an.py`, `lvs_audit.py`, `band_audit.py`, `band_spot.py`, `bt_audit.py`, `keymask_audit.py`, `split_rerun.py`, `onesec_audit.py`, `plain_audit.py`, `cand_audit.py` in `l2vast/ds3/code/zones3_s3/`; outputs `l2vast/ds3/out/zones3/audit/`. "Match" = same value to the displayed precision.
**Result: every number checked matches (Y). No claim is wrong. Four reading notes at the bottom (definition differences and interim-vs-final band values) could mislead a reader.**

## 1. Shipped layer vs no layer (BASE-4 composite pages / change table row "shipped layer vs no layer")
Re-run: `run_v13{x,y,z}({})` vs `{'zone': False}` (zone off, no OTE-62), lock none, cut = (maxDD none - maxDD shipped) / maxDD none.
| claim | source | recomputed | match |
|---|---|---|---|
| V13Y F9 +25%, PRE +23% | DS3_ZONES_COMPOSITE_V13Y.md; CHANGE_TABLE row | F9 +25 (127.6 -> 96.2k), L6M +25, HOLD +19, MID +31, PRE +23, X' +13 | Y |
| V13Z F9 +12%, PRE +24% | DS3_ZONES_COMPOSITE_V13Z.md; CHANGE_TABLE | F9 +12 (208.4 -> 182.8k), L6M +12, HOLD +12, MID +21, PRE +24, X' +18 | Y |
| V13X F9 +9%, PRE +27% (X column) | CHANGE_TABLE | F9 +9, L6M +9, HOLD +9, MID +19, PRE +27, X' +29 | Y |
| (extra) V13Z 12R: shipped vs none F9 -8%, PRE +13% | not claimed | for reference: 12R is where the layer looks different (Z 12R F9 -8, L6M -8, HOLD +23, MID +35, PRE +13, X' -24) | n/a |

## 2. Layer vs random half layers at equal risk (DS3_ZONES_LAYER_VS_SIZE{,_V13Y,_V13Z}.md; CHANGE_TABLE section 3)
Re-aggregated from the 100 stored "A" draws per base (`ds3_base4/lvs{,_y,_z}/A_*_L0.pkl`, equal-risk lot-scaled totals + `REF_L0.pkl` target), my own metric code, gap-corrected linearly (x target/achieved worst-20), rank = share of draws at least as good (mean >=, maxDD <=, Calmar >=).
| window (mean / maxDD / Calmar rank) | claimed X / Y / Z | recomputed X / Y / Z | match |
|---|---|---|---|
| F9 | .48/.41/.43 ; .21/.17/.11 ; .34/.69/.62 | .48/.41/.43 ; .21/.17/.11 ; .34/.69/.62 | Y |
| L6M | .40/.41/.38 ; .17/.17/.10 ; .38/.69/.64 | identical | Y |
| HOLD | .58/.39/.42 ; .29/.20/.16 ; .52/.69/.72 | identical | Y |
| PRE | .06/.11/.05 ; .02/.01/.00 ; .00/.01/.00 | .06/.10/.05 (X maxDD .105 rounds .10/.11) ; .02/.01/.00 ; .00/.01/.00 | Y |
| X' | .81/.59/.80 ; .80/.50/.73 ; .39/.47/.40 | identical | Y |
| V13Z MID maxDD rank 0.12 ; 12R F9-X' ranks 0.31-0.96 | LAYER_VS_SIZE_V13Z.md | 0.12 ; 12R range 0.31 (HOLD maxDD) - 0.96 (X' Calmar) | Y |
Not recomputed: the PRE third/slice attribution (8 of 42 slices <= 0.05), the 50 stratified "B" draws' ranks (I recomputed the B ranks but they were not quoted), and the draws themselves (stored lot-search results; one engine re-run with the same lscale ties: shipped totals identical to the page's target).

## 3. Take-line tables (DS3_V13Z_CHANGE_TABLE.md section 1; DS3_V13Z_BASE.md)
Re-run: lines ON (`{}`) vs lines OFF (`{'lines':'empty'}`) on X, Y, Z, lock none.
| claim | source | recomputed (X / Y / Z) | match |
|---|---|---|---|
| five lines ON vs OFF maxDD cut F9 -13 / +27 / -38; L6M same; HOLD -2 / +26 / -31; MID -39 / +41 / +1; PRE -8 / +22 / -4; X' -48 / +24 / +3 % | CHANGE_TABLE 1 | exactly these 18 values | Y |
| d mean F9 -12.5 / -8.1 / -19.1; L6M -11.9 / -8.4 / -20.3; HOLD -9.1 / -6.6 / -16.3; MID -12.8 / -6.9 / -14.8; PRE -8.0 / -5.0 / -8.7; X' -6.0 / -3.1 / -3.5 $k/wk | CHANGE_TABLE 1 | exactly these 18 values | Y |
| PLAIN 0.70 take all books 1-s cut (Y / Z): F9 +57 / +2, HOLD +45 / +7, MID +43 / +4, PRE +31 / +12, X' +32 / +28 %; d mean F9 +7.1 / -9.0, PRE -0.6 / -5.9 | CHANGE_TABLE 1; DS3_PLAIN_PCT_TAKE_V13Y.md | re-run with lines {book: ((book,),0.7,0.0,0,0.0,'tot')} grid '1sh': Y 57/57/45/43/31/32 %, +7.1/+6.3/+6.3/+8.3/-0.6/+1.5k; Z 2/2/7/4/12/28 %, -9.0/-9.2/-8.1/-7.7/-5.9/-0.3k | Y |
| 1-s five lines ON: V13Y F9 24.7 / DD 80.2, L3M 16.4 / 53.5, HOLD 23.1 / 134.9, MID 8.9 / 63.7, PRE 10.8 / 149.5 ; V13Z F9 12.1 / 174.1, L3M 4.8 / 85.1, HOLD 11.1 / 185.9, MID -0.2 / 112.4, PRE 5.9 / 223.7 | DS3_V13Z_BASE.md | identical (grid '1sh') | Y |
| candidate layers vs shipped (X / Y / Z) F9: sA40 +36/+36/+34, nA60 +38/+36/+32, PUL k3 +1/-6/+7, ALL7 skip n/a/-35/-27; PRE: sA40 +14/0/+18, nA60 -6/-36/-8, PUL +17/-6/+5, ALL7 -9 (Y) -15 (Z); X': sA40 +27/-5/+14, nA60 +31/+7/+19, PUL +11/0/0, ALL7 +6/+7 | CHANGE_TABLE 2 | identical (CRT4h60 not re-run: needs the Z2 mask harness) | Y |

## 4. V13Z base lines (DS3_V13Z_BASE.md and the lead's headline pair)
Re-run `run_v13z({'lines':'empty'})` and `run_v13z({})`, lock none (and 12R, V13X/Y too):
| claim | recomputed | match |
|---|---|---|
| V13Z lines OFF F9 33.7k / maxDD 132.1k ; PRE 17.1 / 166.3 ; X' 4.7 / 91.2 | 33.7 / 132.1 ; 17.1 / 166.3 ; 4.7 / 91.2 | Y |
| V13Z lines ON F9 14.6k / 182.8k ; PRE 8.4 / 172.9 ; X' 1.2 / 88.5 | 14.6 / 182.8 ; 8.4 / 172.9 ; 1.2 / 88.5 | Y |
| V13Y lines ON F9 25.6k / 96.2k ; PRE 12.1 / 129.7 ; X' 1.6 / 69.7 | identical ; V13Y lines OFF identical to V13Z lines OFF (33.7 / 132.1) as the page states | Y |
| V13X -> V13Y (lock none): F9 maxDD 132.6k -> 96.2k, PRE 178k -> 130k (178.4 -> 129.7), X' 135k -> 70k (134.8 -> 69.7), F9 mean +3.1k (22.5 -> 25.6) | identical | Y |
| V13X 12R lines: F9 maxDD 135.9k -> 78.5k, mean -10.1k/wk; PRE 126.5k -> 252.4k | 135.9 -> 78.5, -10.1; 126.5 -> 252.4 | Y |
| V13Y with nfix False == V13Y; Z tie-out | V13Y and Z lines-off series identical; shipped Y vs Z differ only through the profit side | Y |

## 5. BT swing flip: three-base table (ZL-1 `three_bases.csv`)
Recomputed from the raw trade tables `zl1/base_rows_{y,nfix}{none,lock12}.pkl` (per-trade `net`, `drow`, `ld`) with the S4b/ZL-1 mask `mask_BT_swing_F10_4h_D40.npy`: saved $ = -sum(net of flagged taken trades) per window. All four rows (V13Y / V13Y+nfix x none / 12R): taken 18,827 / 12,835 / 18,815 / 12,224, flagged 1,035 / 704 / 1,032 / 668, flag_mean -196.4 / -408.0 / -226.1 / -467.8, unflag_mean 155.5 / 146.4 / 106.6 / 94.1, and saved $k L3M, L6M, HOLD, MID, PRE, X', ALL (e.g. V13Y none 30.43 / 69.78 / 74.92 / 17.87 / 103.43 / 50.13 / 203.2) all match to 0.01. **The base-row tables reconcile EXACTLY with a fresh engine run**: per-day sum of `net` equals the V13Y / V13Z (lock none and 12R) engine daily total with max|diff| 0.0 $ and totals 2,563,277 / 1,488,587 / 1,663,073 / 774,686 $. Y

## 6. 70/30 split cells (DS3_D7_SPLIT_V13Y.md)
Re-aggregated from `ZL-3/split_v13y{,_NOLOCK}.pkl` totals against my fresh V13Y shipped run (the stored 'ship' total ties to my run within 0.0026 $/day = float32 storage), and the F = 1.0 market-entry cell RE-RUN with ZL-3's own simulator (`zl3lib.run_split`, reproduces the stored total to 0.0038 $/day).
| cell | claimed lock-none cut L3M/L6M/HOLD/MID/PRE/X' ; d mean L6M | recomputed | match |
|---|---|---|---|
| F 1.0 (market) | -43/-32/-23/-28/+4/-17 ; -3,068 | identical (also on the fresh re-run) | Y |
| F 0.5 X3 | -10/-17/-16/-26/-5/-9 ; -1,342 | identical | Y |
| F 0.7 X3 uniform | +4/-13/-5/-2/-2/+2 ; -133 | identical | Y |
| F 0.9 X3 | -54/-42/-33/-29/+1/-24 ; -4,322 | identical | Y |
| F 0.7 X1 / X2 / X5 | -35/-49/-40/-34/-8/-21, -47/-41/-32/-4/-1/-7, -3/-8/-5/-6/-21/-3 ; -5,811 / -4,657 / -3,260 | identical | Y |
| 12R: F 1.0 -56/-61/-24/-18/+6/-6 ; F 0.7 X3 -56/-4/+1/+7/+32/0 ; F 0.9 -63/-70/-10/-17/+1/-8 | | identical | Y |
Not recomputed: the equal-risk lot scales (0.93), the random-share and shuffled-dip placebo rows (stored totals only).

## 7. The V13Y noise band (my own)
Re-aggregated from the raw 9-phase draws (`phase_y_noise_*.pkl`, 60 draws x 2 flip sizes x 9 phases x 2 frames) with a second implementation (`audit_an` instead of `an9`): all 24 band values reproduce the published `phase_y_band.csv` to 1e-16 (e.g. lock-off flip2 / flip5 L6M 0.1568 / 0.1995, PRE 0.1143 / 0.1741, X' 0.1590 / 0.2299; 12R flip2 / flip5 L6M 0.1173 / 0.2392, PRE 0.1309 / 0.1311, X' 0.1000 / 0.1449). Four draws (flip 2% j=3 phase 0 lock-off; flip 5% j=17 phase 2 lock-off; flip 5% j=9 phase -3 12R; base phase 4 12R) were RE-RUN from scratch through the engine and reproduce the stored arrays with max|diff| 0.0. Y

## 8. LP_AGAINST natural (ZL-2) and the key masks (DS3_KEY_MASKS_V13Z.md)
| claim | source | recomputed | match |
|---|---|---|---|
| LP_AGAINST natural: 2,081 rows (538 taken); saved $k V13Y lock none L6M 43 / HOLD 61 / PRE 96 / X' 1 / ALL 137; 12R 16 / 28 / 92 / 14 / 124 | MORNING_FLAGS 11:00Z | flagged taken trades' -net from `base_rows_ynone/ylock12.pkl` x `mask_LP_AGAINST_fixscan.npy`: 538 taken; 43 / 61 / 96 / 1 / 137 and 16 / 28 / 92 / 14 / 124 ($k), MID 3 / 4, L3M 11 / 6 | Y |
| PA (9 phases) L6M +12.4, HOLD +9.9, PRE +2.5, X' -13.7, MID -16.1 % | MORNING_FLAGS 11:00Z; ZL-2 | my meanleads2 run on the same mask: +12.4 / +9.9 / -16.1 / +2.5 / -13.7 | Y |
| LP any side (A40 TLP p25 4h) PA L6M +19, PRE +9, X' +4 | MORNING_FLAGS 10:25Z | my LP: +18.6 / +8.9 / +3.5 | Y |
| KEY_MASKS V13Z lock none PA cut (band): LP +3/+7/+7/-2/+1/-7, BT20 +19/-2/-2/0/+6/-9, BT40 +25/-1/-1/+18/-6/-7 (L3M..X'); V13Y LP +7/+12/+10/-16/+2/-14, BT20 +6/-14/-13/+10/+2/-12, BT40 +12/-12/-11/+24/+3/-11; 12R V13Z LP +9/+5/+8/-1/+13/+7, BT20 +13/-1/-5/-8/+5/+9, BT40 +15/-1/-2/+7/+3/+8; 12R V13Y LP +10/+7/+7/-12/+11/+4, BT20 +14/-27/-7/+4/+2/+7, BT40 +17/-26/-15/-3/-4/+7 | DS3_KEY_MASKS_V13Z.md | all 72 PA cuts re-run (9 phases x 3 masks x 2 bases x 2 locks, `run_v13{y,z}` + `extra_skip`) identical | Y |
| KEY_MASKS saved $k V13Z lock none LP +12/+56/+67/-2/+50/-7, BT20 +27/+20/+15/+3/+93/+51, BT40 +21/+67/+100/+24/+98/+35; V13Y LP +10/+49/+61/+1/+49/-8, BT20 +26/+18/+35/+16/+89/+46, BT40 +22/+48/+93/+32/+98/+31 | DS3_KEY_MASKS_V13Z.md | identical when saved $ = MEAN over the 9 lock-reset phases of (total with mask - total without) | Y (definition: see note 1) |

## Reading notes (all numbers right, but a reader can be misled)
1. **Two different "saved $" definitions.** KEY_MASKS (BASE-4) = whole-run change of the total, averaged over 9 lock phases (LP V13Y PRE +49k); ZL-2/ZL-1 = minus the net of the FLAGGED TAKEN trades at phase 0 (LP V13Y PRE +96k). Both reproduce exactly; they differ by interactions (skipping a trade changes later lock decisions and sizing). The same-mask saved $ moves by +-5k (LP) to +-28k (BT, L6M) between lock phases (SD over 9 phases), so a single dollar figure has that noise.
2. **Interim vs final band values.** Messages and MORNING_FLAGS quote the n=50 interim V13Y PA band (lock-off flip2/flip5 L6M 15.5 / 20, PRE 11.5 / 16, X' 14 / 22); the final n=60 values are L6M 15.7 / 19.9, PRE 11.4 / 17.4, X' 15.9 / 23.0 (DS3_ZONES_3_NOISE.md final table, phase_y_band.csv). The differences are <= 1.4 points; a cell that clears a band by less than that (e.g. a cell at +16% in L6M against a 15.5 interim vs 15.7 final flip-2 band) is a marginal call either way and should be read with the final table.
3. **"Tie-out $0.0".** The statements "reproduces to $0.0" hold to float32 storage noise (0.0018 - 0.0038 $/day), not bit-exact; fine for every conclusion.
4. **Stale numbers in older files.** DS3_ZONES_3_S3.md / PHASE_AVG sections written on V13X (defect base) and the V12/V13-assumed sections carry the labels 'defect base' / 'assumed base'; the V13Y sections supersede them. The one claim in circulation that is on a superseded base is the 09:30Z SWG|f3L flag (withdrawn).
## Not verified here (outside the 8 requested items)
ZL-2's 2,001-family null p-values, S5's single-path placebo ranks, ZL-3's lock-audit tables, S4A's stage-2 screens, the BASE-4 episodes file, the CRT4h60 candidate rows, and every number on the V12 / V13-assumed bases. Say if you want any of them audited.


# EXTENSION (Z3, 2026-11-02 ~14:30Z): the previously unaudited items. Same rules: recomputed by me from raw arrays or fresh engine runs. Scripts `s5_audit.py`, `lockaudit.py`, `s4a_audit.py`, `ep_audit.py`, `saved_table.py` (+ the null re-aggregations quoted below) in `zones3_s3/`.
**Result: every number checked matches (Y). Three construction caveats on the nulls (rows not count-matched; config selection not priced; real vs null level rounding) are listed in section 9; none changes a verdict.**

## 9. Multiplicity nulls (ZL-2 LP_AGAINST natural, 2,001 families; ZL-1 BT, 1,980 families)
**9a ZL-2** (`ds3_zl/lp_null_V13Y_natural.csv`, code `code/zl2/lp_null.py`): re-aggregated by me. Real saved $k lock none L6M 42.99 / HOLD 60.70 / PRE 95.80 / X' 1.26 / (12R 16.20 / 27.77 / 91.64 / 14.19); the real row reproduces exactly from the raw trade table (section 8: 43 / 61 / 96 / 1 / 137). p = share of null families with the same statistic >= real:
| statistic | claimed | recomputed (offset / shuffled-day / side-flip / pooled 2,001) | match |
|---|---|---|---|
| min(L6M,HOLD,PRE) none | pooled .037; offset .000, shuffled-day .099, side-flip .011 | .000 / .099 / .010 / .0365 (.037 with +1) | Y |
| min(L6M,HOLD,PRE,X') none | pooled .18; offset .02, shuffled-day .15, side-flip .37 | .022 / .154 / .367 / .181 | Y |
| 12R min3 / min4 | p .19 / .08 | .194 / .080 | Y |
Construction check (read from the code): the real and the null families go through the SAME functions (`rule()` for the scan, `saved()` for the statistic: same realised-net table `v13y_row_net_*.pkl`, same core-book + taken-trade filter, same window masks, same 4 h / D40 / 25-lot / opposite-aggressor logic; the `withflip` row reproduces the WITH-trade aggressor numbers quoted). Differences that matter: (i) the null families are NOT row-count matched exactly: families are re-thinned only if their flagged-row count is more than 15% off the 2,081 target, so null row counts run 1,923-2,393 (median 2,133 offset / side-flip, 2,259 shuffled-day) vs 2,081 real - the nulls carry up to 15% MORE flagged rows, which slightly favours the null (conservative for the real mask); (ii) the real level prices are unrounded while null levels are rounded to the 0.25 tick (immaterial); (iii) the null prices the scan at the FIXED configuration (25 lots, 4 h, D40, against); the choice of that configuration among the 144-setting grid is not in the null (it is handled by ZL-2's walk-forward, which finds selection adds nothing): the p-values are conditional on the configuration. No error found.
**9b ZL-1** (`zl1/bnull2Y_2*.csv`, 1,980 families = 990 level-offset + 990 shuffled-day; page `DS3_BT_SWING_FLIP_CANDIDATE.md` section 4c): recomputed rank of the real statistic among the stored families (share of null >= real):
| frame | statistic | real | null max | rank | match |
|---|---|---|---|---|---|
| none | min(L6M,HOLD,PRE) | 69.78 | 37.36 | 0 of 1,980 (published 0.001 = 1/(N+1)) | Y |
| none | min(L6M,HOLD,PRE,X') | 50.13 | 17.17 | 0 of 1,980 | Y |
| 12R | min(L6M,HOLD,PRE) / +X' | 70.14 / 66.28 | 27.02 / 15.40 | 0 of 1,980 / 0 of 1,980 | Y |
The null p99 and maximum (16.2 / 37.4 for min3 none) also reproduce. Construction check: the null families flag 480-733 taken trades (mean 600, median 596) vs 1,035 real (704 in 12R) - the page states this ("null mean 600 vs BT 1035"), but the families are NOT count-matched, and a dollar statistic is larger for more flagged trades. I therefore re-ranked on a per-flagged-trade statistic (min over the windows of saved $k per flagged taken trade): real 0.0674 vs null max 0.0577 (min3, none), 0.0484 vs 0.0320 (min4), 12R 0.0996 vs 0.0599 and 0.0941 vs 0.0404: **the real BT mask still beats all 1,980 families per flagged trade (rank 0), so the count mismatch does not drive the result; the margin per trade is 1.17x the best null for min3 none, which is much thinner than the dollar margin (1.9x).** No null family has a count within +-25% of the real (n = 0), so a count-matched null does not exist in this file; the nulls only contain offset and shuffled-day families (no side-flip). The 144-config definition grid is not in the null (walk-forward handles it).

## 10. S5 single-path placebo ranks (master table / MORNING; `S5/resvy/ln__*.npz`, `lp__*__plA/plB/plC__*.npz`, 100 draws per kind)
Re-computed from the raw core series (lock none, V13Y): cut = (maxDD base - maxDD cell)/maxDD base vs `ln__base`. The table's placebo ranks (columns B/C/A) are the share of draws whose **L6M** cut is >= the real cell's L6M cut (small = real better); they are NOT a rank across windows.
| cell | real cut L6M / HOLD / PRE / X' | rank B / C / A (L6M) published | recomputed B / C / A | match |
|---|---|---|---|---|
| sopen40 half | .413 / .344 / .110 / .212 | .24 / .16 / .30 | .24 / .16 / .30 | Y |
| sA40>=1 skip | .364 / .161 / .001 / -.048 | .24 / .27 / .27 | .24 / .27 / .27 | Y |
| nA60>=1 skip | .364 / .091 / -.361 / .071 | .27 / .25 / .33 | .27 / .25 / .33 | Y |
| rho60>=2 skip | .411 / .140 / .014 / .356 | .15 / .20 / .10 | .15 / .20 / .10 | Y |
Extra (not published): shares with cut >= real in the other windows - sopen40 A/B/C: HOLD .28/.20/.12, PRE .25/.26/.24, X' .41/.37/.44; the mean-of-4-windows rank is .20/.11/.10, i.e. across windows the placebos at 100 draws beat sopen40 only 10-20% of the time but PRE and X' ranks are 0.24-0.44 (placebo-level); rho60 beats the placebos clearly in X' (.03-.05) and L6M (.10-.20) but not PRE (.12-.22). Placebo mean L6M cuts are +11 to +24% for sopen40 (volume), -1 to +10% for the 28-33% skips.

## 11. ZL-3 lock audit and S4a stage-2 screens
**11a ZL-3 lock audit** (`DS3_ZONES_3_LOCK_AUDIT.md`): re-ran V13Y for the combined-lock multiples with my own layer definitions (none = zone off + lines empty; zone only = lines empty; shipped = V13Y), cut vs 'none' at the same lock setting, L6M / HOLD / PRE / X' maxDD cut % and L6M mean change ($k/wk):
| combined lock | none maxDD $k (L6M, HOLD, PRE, X') | zone only | shipped | match |
|---|---|---|---|---|
| 8R | 141, 141, 147, 293 | +6 +6 +24 +45 ; +5.6 | +54 +54 -90 +42 ; -4.1 | Y |
| 10R | 160, 160, 160, 269 | +13 +13 +14 +22 ; +1.1 | +70 +48 -84 +36 ; -7.3 | Y |
| 12R (shipped arms) | 168, 168, 184, 291 | +11 +11 +28 +20 ; +0.8 | +69 +46 -54 +55 ; -7.3 | Y |
| 16R | 184, 184, 179, 247 | +15 +15 +22 +12 ; -3.1 | +61 +59 -12 +51 ; -6.9 | Y |
| 20R | 199, 199, 174, 139 | +11 +11 +22 -82 ; -9.1 | +58 +58 -21 +21 ; -11.8 | Y |
| none (per-book locks only) | 165, 165, 165, 77 | +20 +15 -1 -19 ; +0.5 | +42 +37 +21 +9 ; -7.8 | Y |
All 18 cells equal the page's rows (and the reading 'shipped L6M/HOLD cut +33..+73% at every lock setting; PRE worse by 12-90% under the combined lock at 8-20R, +21% lock-off' holds). Not re-run: the per-book arm / keep / floor rows (they need the CFG['spec'] hook of ZL-3) and the shipped+LP A40 column.
**11b S4a stage-2 finalists** (`s4a_stage2yn_vyn.csv` as read into the master table, V13Y, lock-none column): I rebuilt 10 finalist cells from the stream parquet features (`poi_core.features(...)[:,0] <= D`, half = 0.5 lots on mask & ~z7, skip = extra_skip of the mask, exactly the S4b library definitions) and re-ran V13Y lock none: DEV|sess_L|so_far D20 half, DEV|on_L|so_far D20 half, SWG|f7L|15s D20 half, SWG|f3L|3m D20 half, SWG|f3L|15s D40 half, SWG|f3L|15s D20 half, SWG|f7L|3m D20 half, MAS|bb_lo|1h D40 skip, SWG|f5L|3m D20 half, MAS|bb_mid|4h D20 skip: **10 of 10 match the published L6M / HOLD / PRE / X' cuts to 0.001** (e.g. SWG f3L 15s D40 half .440 / .118 / .046 / .288). This also confirms the master-table mapping note ('v13_ = lock-off, assumed') - the 'v13_' column of `stage2yn_vyn` is lock none.

## 12. Episodes file (`DS3_ZONES_EPISODES_V13Y.md`)
Recomputed from a fresh V13Y run (lock none and 12R, shipped layer) with my own episode finder (weekly cumulative restarted at the window start; peak = last week at the old high, trough = deepest week, recovery = first week back at the peak or open; top 3 by depth): **40 of 40 published episodes match** on peak week, trough week, recovery week, depth (+-0.05k) and length in weeks, for F9, L3M, L6M, HOLD, MID, PRE and X' in both frames (the 12R X' block parsed one episode of three - that block's remaining two were not compared). The carrier books / sessions in the file were not recomputed.

## 13. ONE table: the two 'saved $' definitions side by side ($k, per window; lock none and 12R; V13Y and V13Z; masks LP_AGAINST natural, BT swing D20 and D40)
(A) = minus the net of the FLAGGED TAKEN trades in the shipped run (ZL-1 / ZL-2 convention, phase 0, no interactions). (B) = whole-run total change with the mask skipped, phase 0 (includes interactions: later lock decisions, sizing, other books). (C) = (B) averaged over the 9 lock-reset phases (BASE-4 KEY_MASKS convention), with the SD over phases in brackets.
| mask | base | lock | taken flagged | definition | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|---|
| LP_AGAINST natural (2,081) | V13Y | none | 538 | (A) flagged taken trades, -net, phase 0 | +11 | +43 | +61 | +3 | +96 | +1 |
| | | | | (B) whole-run change, phase 0 | +12 | +46 | +62 | +7 | +41 | +13 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +10 (2) | +49 (6) | +61 (15) | +1 (7) | +49 (5) | -8 (10) |
| LP_AGAINST natural (2,081) | V13Y | 12R | 354 | (A) flagged taken trades, -net, phase 0 | +6 | +16 | +28 | +4 | +92 | +14 |
| | | | | (B) whole-run change, phase 0 | +4 | +44 | +189 | +96 | +81 | +26 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +4 (11) | +29 (14) | +112 (72) | +21 (35) | +106 (53) | +2 (32) |
| LP_AGAINST natural (2,081) | V13Z | none | 540 | (A) flagged taken trades, -net, phase 0 | +14 | +46 | +66 | +2 | +100 | -10 |
| | | | | (B) whole-run change, phase 0 | +16 | +54 | +67 | -0 | +42 | +1 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +12 (2) | +56 (7) | +67 (15) | -2 (3) | +50 (5) | -7 (7) |
| LP_AGAINST natural (2,081) | V13Z | 12R | 332 | (A) flagged taken trades, -net, phase 0 | +8 | +16 | +34 | +3 | +73 | +15 |
| | | | | (B) whole-run change, phase 0 | +6 | +41 | +92 | +6 | +62 | +34 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +5 (8) | +28 (14) | +104 (42) | +18 (21) | +115 (66) | +3 (39) |
| BT swing D20 (1,840) | V13Y | none | 662 | (A) flagged taken trades, -net, phase 0 | +36 | +35 | +19 | +13 | +103 | +62 |
| | | | | (B) whole-run change, phase 0 | +26 | +33 | +66 | +24 | +89 | +27 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +26 (1) | +18 (6) | +35 (13) | +16 (7) | +89 (27) | +46 (10) |
| BT swing D20 (1,840) | V13Y | 12R | 459 | (A) flagged taken trades, -net, phase 0 | +32 | +42 | +47 | +23 | +118 | +75 |
| | | | | (B) whole-run change, phase 0 | +19 | +75 | +201 | +17 | +156 | +70 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +22 (6) | +1 (30) | -5 (76) | -7 (10) | +81 (79) | +31 (34) |
| BT swing D20 (1,840) | V13Z | none | 661 | (A) flagged taken trades, -net, phase 0 | +38 | +40 | +27 | +15 | +110 | +64 |
| | | | | (B) whole-run change, phase 0 | +27 | +34 | +36 | +3 | +80 | +29 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +27 (1) | +20 (5) | +15 (9) | +3 (3) | +93 (26) | +51 (13) |
| BT swing D20 (1,840) | V13Z | 12R | 445 | (A) flagged taken trades, -net, phase 0 | +33 | +44 | +53 | +24 | +120 | +75 |
| | | | | (B) whole-run change, phase 0 | +25 | +38 | +128 | +7 | +131 | +76 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +20 (9) | +17 (16) | -7 (54) | -17 (20) | +102 (44) | +31 (34) |
| BT swing D40 (2,819) | V13Y | none | 1035 | (A) flagged taken trades, -net, phase 0 | +30 | +70 | +75 | +18 | +103 | +50 |
| | | | | (B) whole-run change, phase 0 | +18 | +64 | +125 | +46 | +85 | +17 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +22 (2) | +48 (6) | +93 (15) | +32 (10) | +98 (28) | +31 (13) |
| BT swing D40 (2,819) | V13Y | 12R | 704 | (A) flagged taken trades, -net, phase 0 | +25 | +70 | +107 | +47 | +123 | +66 |
| | | | | (B) whole-run change, phase 0 | +14 | +97 | +234 | +37 | +240 | +69 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +16 (5) | +5 (56) | -7 (116) | -22 (43) | +86 (89) | +29 (29) |
| BT swing D40 (2,819) | V13Z | none | 1032 | (A) flagged taken trades, -net, phase 0 | +33 | +80 | +90 | +21 | +115 | +50 |
| | | | | (B) whole-run change, phase 0 | +17 | +81 | +122 | +29 | +73 | +17 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +21 (1) | +67 (7) | +100 (10) | +24 (6) | +98 (28) | +35 (14) |
| BT swing D40 (2,819) | V13Z | 12R | 668 | (A) flagged taken trades, -net, phase 0 | +27 | +75 | +112 | +49 | +128 | +68 |
| | | | | (B) whole-run change, phase 0 | +22 | +116 | +246 | +44 | +158 | +72 |
| | | | | (C) whole-run change, mean of 9 phases (SD) | +17 (8) | +28 (74) | +30 (102) | +4 (25) | +129 (64) | +28 (30) |

**Reading.** (A) and (B) agree in sign and rough size in lock none for the long windows (e.g. BT D40 V13Y L6M +70 / +64, HOLD +75 / +125, PRE +103 / +85) but differ by interactions: LP PRE (A) +96 vs (B) +41, X' +1 vs +13. The phase-mean (C) removes the single-phase luck: in lock none the SD over phases is small (LP 2-15k, BT 1-28k) and (C) is close to (B); under the combined 12R lock the phase noise is huge (BT D40 V13Y L6M (B) +97 vs (C) +5 with SD 56; HOLD +234 vs -7, SD 116): **the 12R whole-run dollars are not stable across lock phase, only (A) (the flagged trades' own P&L) is**. Which one to quote: (A) answers 'what did the skipped trades earn?', (C) answers 'what is the expected change of the whole run'; never compare an (A) figure with a (C) figure.

## Not yet audited
S4a stage-2 cells beyond the 10 sampled; ZL-3's per-book lock rows and the shipped+LP column; the carrier lists of the episodes file; ZL-2's walk-forward and the ZL-1 definition-grid null; every number on the V12 / V13-assumed bases.

## 14. Update for V13T_LIVE (2026-11-02, appended)
Headline numbers on V13T_LIVE (xcost 0.80, lock none): band PA9 2% flip L6M .188 / HOLD .182 / MID .212 / PRE .078 / X' .145, 5% flip .219/.205/.322/.099/.182 (n=100, tl_band_final.csv; re-derived from raw pkl by tl_band_final.py, matched the partial n~45 table within 0.04). Shipped layer ranks among 100 random same-size layers: L6M .37, HOLD .37, MID .32, PRE .79, X' .23 (no 0.95). Monthly-refit WF6/WF12 L6M cut -.592/-.831 vs fixed. Statements from earlier sections that said "shipped layer indistinguishable from random" and "no survivor / walk-forward fails" remain true on V13T_LIVE. Statements quoting V13Y band values (15.7/19.9 etc.) are base-specific and should be labelled V13Y. Open: lead placebos, equal-risk and episode-drop were not re-run on V13T_LIVE (verdicts carried from V13Y).
