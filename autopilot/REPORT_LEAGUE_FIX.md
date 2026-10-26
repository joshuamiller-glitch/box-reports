# REPORT_LEAGUE_FIX (2026-10-19): PAPER-ALL audit marking + ENDI (16:55 flatten) rescore

## Table first
| item | result |
|---|---|
| League rows | 177 (174 + 3 new K4-EXACT rows). Status: CLEAN 62, FLAGGED-LIVE-FORM 103, LOOKAHEAD-VOID 9, PROVISIONAL 2, FAIL 1 (strict R14) |
| VOID rows (not in N, kill rules, promotions; P&L listed separately in LEAGUE.md / FORWARD.md) | 9: the six N1 rows, SK_K4BOOKS, SK_K4BOOKS_ESHEDGED, TINYMERGE:RW:market (holds R10 = 16:00 fill filtered by the 16:17 K4 probability, R12 same-day SKEW, R9 IBS same-bar: real lookahead). Per the lead ruling TINYMERGE:I:market (same-close MOC fill) and TINYMERGE:L:market (same-print K4-type cells, no real-lookahead input found) are FLAGGED-LIVE-FORM; I:market carries the CORRECTED series (I9 columns replaced by the 15:59-open live form; merged-I 1.39 -> 1.19, null rank 0.97, gates a-d PASS, best-of-F ~0), L:market is not individually rescored |
| Multiplicity N (live counted rows) | 144 -> 143 (6 N1 + SK_K4BOOKS + RW removed, K4-EXACT hedged added; I and L stay counted); z line single 3.33 |
| Top forward z before / after | N1-RT_ZB_ZT-30m-MR +8.15 (was rank 1) -> VOID, shown separately (+11.03 this refresh); top counted row is now M2-A-A9-stk2-V1 +2.71 (FLAGGED, 1 week) |
| League gate a-d passers | 72 as registered (header said 67, stale) +2 K4-EXACT -> 74 as scored; 70 after removing the 4 VOID passers (N1-EN_HO_RB, SK_K4BOOKS, ESHEDGED, TINYMERGE:RW); 56 still pass in audited form (14 FLAGGED passers lose a gate: 10 daily-bar rows, WT432:ATR20_m4 borderline, B7XC at $4.36/micro, Range, Renko, M2R3-RENKO-ES) |
| FAMILY_RESULTS gate a-d passers (87 unique) | 87 -> 83 without VOID -> 73 audited (10 daily rows lose a gate); N1: 1 -> 0; N3/N7/N8 22 -> 16 |
| K4-EXACT 17 cells | PROVISIONAL: SK_K4EXACT17_HEDGED (counts once in N), SK_K4EXACT17_UNHEDGED (variant), gates a-d pass, best-of-F 0.00 at 1,208/761/594 (FAIL); strict R14 row SK_K4EXACT_STRICT_R14 = FAIL (0.50/0.40, b,c,d fail), variant, not counted |
| ENDI rescore (16:55 flatten), 258 families scored (4 had <10 active cells) | gate a-d passers 3 -> 3, no status change; best-of-F still 0 everywhere |

## 1. League changes
Code: code/census/night_ins/ap_m2_paperall.py (status column, VOID exclusion from N/kill/promotion/LIVEPACK, separate VOID table, corrected headline counts, direct-matrix + ES-hedge scoring for K4-EXACT rows), ap_lf_status.py (writes outputs/autopilot/forward/m2/ROW_STATUS.csv: status, gates_audit, note per row), ap_lf_k4rows.py (K4-EXACT rows), ap_lf_refreeze_endi.py. Backups in outputs/autopilot/league_fix/bak/ and forward/m2/*.pre_leaguefix.*. Nothing deleted; voided rows keep weights, bands and weekly P&L. Scorer rerun (stale = STALE, never zero); LEAGUE.md and FORWARD.md regenerated.
Judgment calls (one line each in ROW_STATUS.csv to change): TINYMERGE:I:market was first set VOID, then corrected per the lead: FLAGGED-LIVE-FORM with the corrected series (ap_lf_fix_i.py; frozen weights/bands re-derived, old values in row['pre_leaguefix_I']; its W42 P&L is now -$12.6k over 0.8 weeks vs +$0.5k before). TINYMERGE:RW stays VOID because it contains real-lookahead cells (RW10/R10, R12 SKEW), not just same-close fills. Daily-bar rows N3/N7/N8/N10/N13 are FLAGGED-LIVE-FORM, not VOID (clock, not lookahead); 10 of them lose a gate when the Sunday stub is folded in and are shown as gates_audit FAIL.
K4-EXACT rows: weights = outputs/k4/vps_v4/CELLS_WEIGHTS_17.csv (tilt, fit 2025-08-01..2026-07-31); bands = headline-fill OOS series (reproduced: hedged 1.163, unhedged 1.419) cut at 2026-10-09 per the league rule (140 weeks; weekly mean hedged $1,980 / unhedged $2,475 vs report $2,021 / $2,466 over 141 weeks); hedge 0.903 ES (last-fold beta) applied while any cell is open. Live proxy = the as-scored 17 columns of fam/SK_K4BOOKS.npz (fill delta immaterial per K4 report s4). Forward W42 for all K4 rows is $0 (matrix shows no K cell entries in 10-12..10-16; not stale).
Not done / caveat: the K4 matrix is extended by the K4 owner; the K4-EXACT rows go STALE if it is not.

## 2. ENDI flatten bug
Cause: `np.flatnonzero(HM[s:e]>=1015)` with day rows starting at HM=1080 always returns row 0 (1080 is not < 1080), so the engine fell back to the day's last row (16:59). Fix: `(HM>=1015)&(HM<1080)` in ap_c10_s1_core, ap_c7_p1_core, ap_c5_m1_core, v5_p2_core (originals in league_fix/bak/; ENDI_LEGACY=1 reproduces the scored behaviour; legacy rerun matches stored real_CL.pkl exactly except the revised last day). ap_b_base (B7, B7X) already has the correct filtered test: B7/B7X NOT affected. ap_c11_dip_core not affected.
Method: all 16 (core,symbol) grids rerun at 16:55 (outputs/autopilot/league_fix/endi/), each family cell matched to its stored column (corr >= 0.9999999, 0 mismatches), same per-cell scale, scored as ap_m2_lib.score_one (12/3/3 tilt, series-level drift-adjusted signflip null, 200 reps, gates a-d), best-of-F = G(Sharpe)^F with the pooled family null, F_eff 1,208/761/594. Check: C10S1_CL:240_lr 1.664 -> 1.645, best-of-F 0.0014/0.016/0.040 identical to the CL240 audit.
| family set | families | mean dSharpe | max abs dSharpe | gate a-d passers old -> new | best-of-F max (594) |
|---|---|---|---|---|---|
| C10S1_* | 136 | -0.002 | 0.43 | 3 -> 3 | 0.040 (C10S1_CL:240_lr) |
| C7P1_* | 84 | +0.013 | 0.76 | 0 -> 0 | ~0 |
| C5M1_* | 32 | +0.006 | 0.09 | 0 -> 0 | ~0 |
| V5P2* | 6 | -0.011 | 0.05 | 0 -> 0 | ~0 |
Passers: C10S1_CL:240_lr 1.663 -> 1.645 (null 1.00 -> 1.00); C10S1_CL:240_macd 1.383 -> 1.359 (null 0.995 -> 0.975); C10S1_6E:240_macd 1.035 -> 1.022 (null 0.955 -> 0.950, borderline but passes). Status changes: none. All 19 PAPER-ALL rows on these cores (C10S1_*, C5M1_*) re-frozen (weights, g, bands) from the corrected OOS series; old values in row['pre_endifix']; their fam matrices replaced (originals in outputs/methods2/fam_pre_endifix/). Rows flagged FLAGGED-LIVE-FORM with the old -> new numbers. FAMILY_RESULTS and methods2/oos untouched; corrected numbers in outputs/autopilot/league_fix/ENDI_RESCORE.csv and methods2/FAMILY_AUDIT_FLAGS.csv (949 families: audit status, gates scored vs audited). The ~175 non-PAPER-ALL families on these cores keep old matrices (rescored values only in ENDI_RESCORE.csv).
Headline counts corrected in: LEAGUE.md/FORWARD.md header, notes appended to STATUS_1019.md and MORNING.md, DECISIONS.md. Older reports keep their original (superseded) numbers.

## 3. NET-BOOK re-freeze (lead instruction; REPORT_NETBOOK.md of a8aa0428c2a488c31)
Confirmed with that agent: CL240 NET_SERIES (main, _lr, _macd) are built on the 16:55-FIXED flatten (matrix identical to the audit live-form matrix). Snapshot PRED_PAPERALL.pre_netbook.json taken first; old values in row['pre_netbook'] (the earlier pre_endifix values stay).
Rows re-frozen on the net book, headline net_adj_fee4.36 (stored in row['net_series'], used as the live series; fee grid 0.436/1/2/4.36 in the row notes; status stays FLAGGED-LIVE-FORM with a NET-BOOK note). Gates a, c, d recomputed on the net OOS series; gate b (null) NOT recomputed.
| row | scored Sharpe | net Sharpe @ $4.36/micro | gates a/c/d |
|---|---|---|---|
| C11DIP | 1.43 | 1.41 | pass |
| C10S1_CL:240_lr | 1.65 | 1.52 | pass |
| C10S1_CL:240_macd | 1.36 | 1.19 | pass |
| BM13_NQ (6-cell) | 1.77 | 1.45 | pass |
| WT432:ATR30_m4 / ATR20_m4 / ATR10_m3 (passers) | 1.26 / 1.19 / 1.00 | -0.03 / -0.20 / -0.81 | FAIL |
| WT432:ATR30_m3, ATR14_m4, ATR10_m2, ATR20_m2, ATR20_m3 (non-passers) | 0.77 .. 0.59 | -0.63 / -0.62 / -1.36 / -1.48 / -1.20 | fail |
WT432:ATR14_m3 left unfrozen (does not reproduce); the WT432 pack row and the CL240 forward row are not PAPER-ALL league rows; BM11_NQ, BM12_NQ, T3S1_BOOKS_B:B_WT not rescored (unchanged).
B7XC and B1leg_BTC (B7X, BTCWT) are now status REPORT-ONLY (disabled on NT8): shown with the VOID table, out of N, kill rules, promotions and LIVEPACK.
Count changes: status CLEAN 62, FLAGGED-LIVE-FORM 101, LOOKAHEAD-VOID 9, REPORT-ONLY 2, PROVISIONAL 2, FAIL 1; N 143 -> 141; counted rows 166 (151 scored -> 149); gate a-d passers 74 as scored -> 68 without VOID/REPORT-ONLY -> 53 in audited form (3 WT432 passers now fail at $4.36/micro). Nominal promotions 0, kill-watch 0.

## 4. WT432 disabled on NT8 (user note, via lead)
All 9 PAPER-ALL rows WT432:ATR* set REPORT-ONLY (numbers, net-book freeze and forward P&L kept; listed with the VOID table; out of N, kill rules, promotions, LIVEPACK). The WT432 pack row is a codepack section row, not a league row (nothing to change there). No fee was changed (user FEES numbers not yet received).
Counts: CLEAN 62, FLAGGED-LIVE-FORM 92, LOOKAHEAD-VOID 9, REPORT-ONLY 11 (WT432 x9, B7XC, B1leg_BTC), PROVISIONAL 2, FAIL 1; counted rows 157; N = 132; 140 counted rows scored, 17 STALE; gate a-d passers 74 as scored -> 65 without VOID/REPORT-ONLY -> 53 audited.

## 5. Net-book rows re-frozen at the FEES.md standard (STD; user FEES v2)
The 12 net-book rows now use column net_adj_feeSTD (outputs/FEES.md) as frozen band and live series; the $4.36 series stays in row['net_series']['ref_col'] / net_book['ref_sharpe_4_36'] as the historical reference; pre_netbook and pre_endifix values kept. Net Sharpe at STD (gates a/c/d recomputed here; b not): C11DIP 1.43 pass; C10S1_CL:240_lr 1.60 pass; C10S1_CL:240_macd 1.29 pass; BM13_NQ 1.66 pass; WT432:ATR30_m4 0.63 / ATR20_m4 0.58 / ATR10_m3 0.48 (gate c fails: boot_lo < 0; a,d pass) and the five other WT432 grids 0.27, 0.19, -0.19, -0.28, -0.15. WT432 rows stay REPORT-ONLY. Counts unchanged: N = 132, counted rows 157 (140 scored, 17 STALE), CLEAN 62 / FLAGGED-LIVE-FORM 92 / LOOKAHEAD-VOID 9 / REPORT-ONLY 11 / PROVISIONAL 2 / FAIL 1; gate a-d passers 74 -> 65 -> 53 audited. The BM13 3-cell row and the WT432 pack / CL240 forward rows are not league rows (not added).
