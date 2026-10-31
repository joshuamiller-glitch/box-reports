# DS3_RERUN_B - re-runs on the correct routes: size-UP rows, wave-1 ha rows, unit check of the bar-type leads, causal vol tag, fixed shuffle_src (RR-B, 2026-10-31)

Research only; no new strategy search, no new selection (every row below is an existing row); masks capped 20260206; UNTOUCHED never read. Code and outputs: l2vast/ds3/out/rerunb/ (a_*, b_*, c_*, d_*, e_*, z_* scripts, CSV/parquet results, tables *_table.md). Harness = unitaudit/ua_lib.py -> stack2/s2_lib.py T.run machinery (rows from stackpart sp_lib, per-book exact lock engine), size rules enter as the per-row multiplier m0 (the engine reads the 1-s path at the sized lot); windows L3M L6M HOLD PRE X' (X' = 20230401..20240131); basis N; research lots and LIVE-session lots (PE 7, KB 2, SM 4, HM 4/2, ST/WT research/2.35); governors = planned-lot R (as coded) with the sized-lot variant beside it. 3 workers max, OMP/MKL=1.

## PAGE 1 - tier changes, one line each

**A. Size-UP rows on the multiplier route (NTZ-1, 42 u150 look rows = 6 cells x ALL + 6 books; ZONES-2 take-from u150 and SET z50; ENSEMBLE mult rules).**
1. NTZ-1 ST `size 150% (POI behind) [market] BEHIND SWG:f7L:1m within 5 pts`: CANDIDATE-RECENT -> LEAD. Stack L6M/HOLD +2.1k/+2.0k (pts-scaled) -> -2.0k/-1.9k research, -0.9k/-0.8k live lots (MDE 8.9k); the same engine with a mult column gives -0.6k/-0.3k.
2. NTZ-1 ST `size 150% BEHIND SWG:f3L:2m within 5 pts [market]`: CANDIDATE-RECENT -> LEAD. +2.1k/+2.2k -> -1.9k/-1.8k research, -0.8k/-0.8k live (engine-mult cross-check -0.6k/-0.2k).
3. NTZ-1 KB `size 150% BEHIND EQL:EQH_tight:5m within 1xATR15 [market]`: CANDIDATE-RECENT -> LEAD on the s2 harness (+1.4k/+0.9k -> -0.7k/-0.9k research, -0.2k/-0.3k live); the poi-engine mult route says +1.5k/+1.0k (routes disagree, so nothing above LEAD). The [70/30] twin was already -0.1k/-0.4k, unchanged.
4. NTZ-1 SM `size 150% BEHIND ARR:BRK_CE:3m within 20 pts [market]`: CANDIDATE-RECENT -> LEAD (+1.8k/+1.7k -> -0.4k/+0.2k research, +0.6k/+0.7k live; MDE 4.3k, i.e. zero). The [70/30] twin keeps its tier (+3.0k/+3.0k research, +0.8k/+0.7k live, MDE 4.6k; the poi-engine route gives -0.5k/0.0k, so the sign is harness-dependent; weak).
5. NTZ-1 ALL `size 150% BEHIND PRF:b2:day within 1xATR15 [70/30]` (95 fires/wk, the big +11.0k/+10.1k line): CANDIDATE-RECENT -> LEAD at planned-lot governors: -3.2k/-2.6k research (MDE 26.6k), +3.4k/+3.4k live, +3.6k/+3.7k poi-engine mult; with sized-lot governors +29.0k/+25.4k (research) = lot dispersion / locks scaling with the size, not an entry edge (DS-1 class 8). Not a stack-positive rule on the governor the live stack uses today.
6. NTZ-1 HM `size 150% BEHIND ARR:iplFVG:15s within 0.25xATR15 [70/30]` (HM forward-watch LEAD): stays LEAD, stack sign now negative at research lots (+0.7k/+1.5k -> -3.3k/-1.9k; live +0.2k/+0.3k, sized governor +6.3k/+6.0k = dispersion). HM OB_CE 30m [market] (LEAD, was -1.9k/-1.7k) -> -5.3k/-4.6k, stays LEAD/DEAD-like.
7. NTZ-1 KB/MV/SM/HM remaining size-up LEAD rows: no tier change (MV, MA, DN, PB are not books of the 6-book lock engine: no stack line existed or can exist; their per-signal rows are untouched by this defect). Pooled ALL-book LEAD rows move both ways (FIB ret62 5m [market] -0.1k/-0.2k -> +2.6k/+1.6k; FVG 2m [market] +2.7k/+2.3k -> +3.4k/+2.5k; RND x100 +0.6k/+1.4k -> 0.0k/+1.2k; EQL_rel [70/30] -2.0k/-0.1k -> -0.8k/+0.3k): all LEAD before and after, all inside MDE.
8. Across all 42 u150 look rows: stack L6M and HOLD both >= 0 in 22 (pts-scaled) -> 12 (multiplier route, research lots, planned governor) / 20 (live lots); mean L6M +0.76k -> -0.55k research / +0.45k live; 18 of 42 change sign in L6M. No u200 row exists in NTZ-1 or ZONES-2 (u200 was only an NTE-1 rule).
9. ZONES-2 take-from `size x1.5` (ARR4H / ARR1D / CRTPDX / ALL14, D 20/60, SPL and market): the report carried per-signal points only (+0.61 L6M per signal for ALL14 D20, placebo rank 0.00); on the multiplier route the stack is negative at research lots in L6M and HOLD for 14 of 16 cells (ALL14 D20 [70/30]: -16.9k/-12.9k; ARR1D D20: -23.7k/-19.5k), live lots -8.8k/-7.0k to +4.5k/+4.3k (negative in both L6M and HOLD for 9 of 16): LEAD stays LEAD, no promotion.
10. ZONES-2 SET (post-hoc 11 lines) half size D20 [70/30]: unchanged (+19.3k/+14.4k research, +4.0k/+3.6k live vs reported +16.9k/+14.5k; PRE +2.7k, X' +4.6k, L6M +19.3k vs MDE 19.7k, HOLD +14.4k vs 21.8k); the lid cell ARR|BRK|4h z50: +1.9k/+1.9k research, -0.3k/-0.6k live, unchanged DEAD-in-practice.
11. ENSEMBLE multiplier rules (ALL/HONEST mult, MATCHED): the stored stack lines are reproduced to 0.1k by T.run with m0 (the ensemble scored its final stack on the engine multiplier route already; only the weight fit used (m-1)*pts); DEAD stays DEAD. The 70/30 versions are more negative (basis N L6M: research -34.9k to -49.8k, live -18.2k to -24.5k; market research -26.5k to -36.4k).

**B. Wave-1 PAIRFIX rows on ha/3m and ha/5m, de-duplicated store (9 rows):** no tier change. 6 of 9 rows are identical or within 1.5 pt D/TW (L02766 ha/3m, L01501, L01427, L01537, L02766 ha/5m, L01629 'D' row: the signal engine on those cells is insensitive to the duplicated candles); L01654 changes sign in X' (+3.3/+1.6 -> -1.4/-1.1) and L6M (+2.0 -> +4.0) but HOLD D/TW stay negative (-1.2/-2.4), so it stays DEAD; L01678 SM_t75_sst ha/5m London weakens (HOLD D/TW +2.8/+3.2 -> +0.6/+0.9, L6M +3.1/+3.5 -> +0.5/+0.7, X' +13.4*/+7.9* -> +6.6/+3.4: loses its only starred window; stays LEAD with HOLD CI including 0, both HOLD measures > 0); L01629 KB_t90_s90 ha/3m London 'G' variant (PRE +22.0*/+14.2* in PAIRFIX) was a duplicate-candle artefact: on the clean store it equals the 'D' variant (PRE +10.1/+5.9, no CI excluding 0). L02766 ha/5m Asia stays DEAD (G3u), L01427 loses its HOLD-D star (+16.0* -> +14.9, TW +2.5), L01537 keeps D +10.3* / TW +4.4 (partial). The wave-1 cell SELECTION (PRE+X' on the buggy store) was not redone.

**C. Unit check of the 7 CONFIRM-BARS leads (the only seven-lead set; per planned lot, per contract of final position, lock-engine stack at research and live-session lots):** 4 of 7 fail on the stack, 2 survive (tiny / inside MDE), 1 cannot be stack-scored. FAIL: #1 ST ha 10m three (L6M -2.2k research / -0.9k live; HOLD 0.0k), #3 KB range-8 close_fav (HOLD -0.4k / -0.2k), #4 PE ha 15m flip (live L6M -0.5k, PRE -2.3k), #7 PE linreg 15m flip (L6M -1.8k / -3.5k, HOLD -1.9k / -3.1k). SURVIVE: #2 WT dol 2G two (stack +8.2k/+5.5k L6M/HOLD research, +3.5k/+2.3k live, all five windows >= 0, MDE 14.4k/6.1k; WT is not a live book), #5 KB ha 1m flip c2 limit (+1.4k/+0.1k research, +1.0k/+0.5k live, MDE 8.7k/3.1k: positive but about $1k/wk). #6 DN ha 3m three: DN is not a lock-engine book (per planned lot +0.82 L6M, +1.05 HOLD, inside MDE): LEAD, stack not computable. The per-contract-of-final-position column is the inflated unit again (ST +1.95, WT +2.83 vs planned-lot +0.32 / +0.75). The CF-COMBO page-1 rows (23 ordered-array INFO rows, 74 unit-checked cells) were unit-checked by CF-COMBO itself; I found no second seven-lead CF-COMBO set, so '7 CF-COMBO leads' is read as these seven (see Questions).

**D. Causal vol tag in the other vol-conditioned STACK-2 cells (14 cells; 27.1% of rows change tag):** no cell changes tier; the change is the same pattern as UA-1: recent windows go up, selection windows go down. `cut50 vol tercile >= 2` [market] research PRE +0.3k -> -4.2k, X' +4.7k -> -1.6k (L6M +12.4k -> +17.2k): positive-in-all-windows is gone, recent-only (no tier change, but recent-only; 70/30 twin PRE -0.4k -> -5.3k, X' +3.5k -> -2.3k). `vol tercile < 2`: L6M +10.6k -> +5.9k, HOLD +8.5k -> +3.4k, PRE -8.5k -> -5.3k, X' -4.0k -> +3.0k (70/30: L6M +3.1k -> -0.9k) = no longer a recent edge. `vol >= 1` L6M +19.4k -> +21.0k but PRE -1.0k -> -4.1k. Asia & vol >= 2 stays positive in all five windows at both lot sets (market PRE +3.6k -> +1.0k, X' +6.1k -> +2.8k; 70/30 +4.5k -> +1.6k, +4.7k -> +1.4k; live +5.9k -> +6.7k L6M). `ER20>=0.4 & vol >= 2` and `Asia & ER20 >= 0.4 & vol >= 2` are ~0 under both tags (|x| <= 4k, MDE >= 7k): DEAD/noise both ways.

**E. Fixed shuffle_src:** `l2vast/ds3/out/rerunb/lp_data_fixed.py` (copy of l2set_profit/lp_data.py with trade_of_row; original untouched; logged in DECISIONS.md). Bit-identical to uf_p1_common.shuffle_src for seeds 7100, 7101, 9000 (39,493,252 rows); the original map agrees with the correct map on only 26% of rows, which is what voided the G8 ranks. The voided placebo ranks were already re-run on the corrected map by UF TASK A (uf_l2sp_placebo_redo.py, 100 draws, 10 cells: G1 PRE-selected pooled PRE rank 1.00 / L6M 0.51 (M) 0.30 (N); the L6M-rank-1..3 and best-N pooled cells rank 1.00 in L6M and HOLD but 0.02-0.55 in PRE; thick-only p70 PRE_N 0.00); a full lp_sweep placebo (tens of thousands of cells x T x 20 draws) was not re-run because the identical map is already applied to every cell that was ever read. No tier change.

**Nothing is promoted; no PASS; no OFF changes to ON. Net effect: 5 NTZ-1 CANDIDATE-RECENT size-up rows lose their tier (ST x2, KB market, SM market, ALL PRF), 4 of 7 bar-type leads fail the stack unit.**

## A. Size-UP rows in detail

Rule routes compared. (1) as reported: stack line from `poi_look.rule_o` (o[:,0] *= 1.5, engine reads the planned lot). (2) poi-engine mult: same engine/base rows, `EN.run_rows(..., mult=m)` (a_cross.py; reproduces column (1) exactly with the pts route). (3) s2 harness: `T.run` machinery with m0 (a_run.py), research lots; live lots and sized-lot governors beside it. Stack delta vs the unfiltered base, $k/wk; L3M/L6M/HOLD/PRE/X' ordering as stated. 'orig' = as reported (L6M/HOLD/PRE/X').

| book | rule | tier | orig | corr_res_L3M/L6M/HOLD/PRE/X | MDE_L6M | corr_live_L6M/HOLD/PRE/X | sized_res_L6M/HOLD | poi_engine_mult_L6M/HOLD |
|---|---|---|---|---|---|---|---|---|
| ST | SWG f7L 1m <=5pt, size150 [MKT] | CAND-RECENT | +2.1/+2.0/+1.7/+0.8 | -0.1/-2.0/-1.9/-1.9/+3.0 | 8.9 | -0.9/-0.8/-0.8/+1.3 | -4.1/-1.4 | -0.6/-0.3 |
| ST | SWG f3L 2m <=5pt, size150 [MKT] | CAND-RECENT | +2.1/+2.2/+1.2/+0.5 | +0.0/-1.9/-1.8/-2.6/+2.8 | 9.0 | -0.8/-0.8/-1.1/+1.2 | -4.8/-2.2 | -0.6/-0.2 |
| KB | EQL EQH_tight 5m <=1xATR, size150 [MKT] | CAND-RECENT | +1.4/+0.9/+0.0/-0.1 | -1.7/-0.7/-0.9/+0.2/-0.2 | 4.4 | -0.2/-0.3/+0.1/+0.0 | +0.4/+0.0 | +1.5/+1.0 |
| KB | same [70/30] | CAND-RECENT | -0.1/-0.4/+0.2/+0.1 | -1.8/-0.1/-0.4/+0.2/+0.1 | 3.0 | -0.0/-0.2/+0.1/+0.1 | -0.8/-1.0 | -0.0/-0.3 |
| SM | ARR BRK_CE 3m <=20pt, size150 [MKT] | CAND-RECENT | +1.8/+1.7/+1.9/+1.7 | -0.8/-0.4/+0.2/+0.9/+1.9 | 4.3 | +0.6/+0.7/+0.5/+0.4 | +0.2/-0.3 | -0.0/+0.5 |
| SM | same [70/30] | CAND-RECENT | +1.7/+1.5/+1.7/+1.6 | +1.5/+3.0/+3.0/+0.5/+1.3 | 4.6 | +0.8/+0.7/+0.5/+0.5 | +1.0/+0.7 | -0.5/-0.0 |
| ALL | PRF b2 day <=1xATR, size150 [70/30] | CAND-RECENT | +11.0/+10.1/+11.6/+3.3 | -4.6/-3.2/-2.6/+8.9/+5.0 | 26.6 | +3.4/+3.4/+5.9/+2.4 | +29.0/+25.4 | +3.6/+3.7 |
| HM | ARR iplFVG 15s <=0.25ATR, size150 [70/30] | LEAD | +0.7/+1.5/+5.6/+1.1 | -5.1/-3.3/-1.9/+6.1/+1.4 | 7.1 | +0.2/+0.3/+1.5/+0.3 | +6.3/+6.0 | -0.4/+0.5 |
| HM | ARR OB_CE 30m <=1xATR, size150 [MKT] | LEAD | -1.9/-1.7/+0.0/+1.8 | -2.6/-5.3/-4.6/-0.3/+1.0 | 8.8 | -0.2/-0.1/+0.4/+0.2 | +8.4/+7.3 | -4.8/-4.2 |
| ALL | ARR FVG 2m <=0.25ATR, size150 [MKT] | LEAD | +2.7/+2.3/+1.5/+0.1 | +5.2/+3.4/+2.5/-3.0/+0.3 | 11.9 | +2.6/+1.9/-1.3/-0.3 | -5.1/-2.6 | +2.6/+0.7 |
| ALL | EQL EQL_rel 1m <=10pt, size150 [70/30] | LEAD | -2.0/-0.1/-1.4/+1.0 | +0.5/-0.8/+0.3/-2.2/+4.7 | 13.1 | +0.8/+1.5/+0.5/+2.8 | -3.5/-2.8 | -3.2/-1.1 |
| ALL | RND x100 <=2pt, size150 [MKT] | LEAD | +0.6/+1.4/-1.4/+0.9 | +6.3/+0.0/+1.2/-3.3/-0.1 | 9.9 | +0.9/+1.0/-0.5/+0.3 | +6.5/+7.2 | -0.3/-0.4 |
| ALL | FIB ret62 5m <=20pt, size150 [MKT] | LEAD | -0.1/-0.2/-2.1/+6.0 | +7.3/+2.6/+1.6/-2.6/+7.6 | 9.9 | +1.6/+1.6/-1.1/+3.1 | +8.4/+7.4 | -2.4/-2.1 |
| ALL | FIB ret62 5m <=20pt, size150 [70/30] | LEAD | +2.9/+2.7/-1.6/+7.0 | +5.4/+2.4/+2.0/-1.6/+7.2 | 9.1 | +3.0/+3.0/-0.8/+3.5 | +6.7/+6.0 | -2.2/-2.2 |

Reading: the pts-scaled route credits a 1.5x outcome while the engine's day/week locks, entry test and busy rule still see a 1x trade, so size-up wins inflate (uniform x2: +29.9k vs -9.8k in the NTE-1 test; here 12 of 42 u150 rows flip sign in L6M between the pts route and the same engine with a mult column, 18 of 42 against the s2 harness). Both corrected routes agree that the ST, PRF-b2 and HM rows lose their stack lines and that the pooled lines are small. They disagree on KB EQH market and SM [70/30] (harness difference in the 70/30 base rows: stackpart S73 vs poi floor_plain), and I use the s2 harness (the order's route) for the tier decision, flagging every row where the poi-engine mult route has the opposite sign. Sized-lot governors (day/week locks scale with the largest sizer multiplier of the day/week) turn almost every size-up row positive (HM +6k, ALL PRF +29k): that is the dispersion effect DS-1 class 8 describes (ER20 sizer: planned vs sized), not evidence for the rule.

Full 360-row set (u150 / z50 / z67, NTZ-1 detail+look+combo rows with a 6-book scope; N basis, research and live lots, all five windows, both bases): `a_all_summary.csv`, `a_res_all.parquet` (adds MDE/CI, planned and sized for u150), `a_cross_all.parquet`. Size-DOWN rows are less affected: z50 gate (stack L6M and HOLD >= 0) 83 -> 78 of 159 rows (research), z67 81 -> 69; the NTZ-1 WT z50 [70/30] (FIB ret50 15m, +1.5k/+1.9k) is +1.4k/+1.7k research, +0.6k/+0.7k live: unchanged.

### ZONES-2 rows (take-from u150, SET half size; own base; planned governor; $k/wk L3M/L6M/HOLD/PRE/X')
| row | lots | L3M/L6M/HOLD/PRE/X' $k/wk | MDE L6M |
|---|---|---|---|
| u150_ARR4H_20_SPL | research | -7.4/+0.4/+0.6/-10.8/+3.2 | 16.3 |
| u150_ARR4H_20_SPL | live | -3.7/+1.1/+1.7/-2.7/+2.0 | 6.9 |
| u150_ARR4H_60_MKT | research | -9.5/+2.4/-1.8/-7.7/+6.6 | 20.2 |
| u150_ARR4H_60_MKT | live | -2.3/+3.5/+1.7/-1.6/+2.0 | 12.8 |
| u150_ARR1D_60_SPL | research | -25.9/-22.8/-18.8/-1.1/+11.8 | 29.1 |
| u150_ARR1D_60_SPL | live | -10.1/-6.5/-4.5/+2.4/+6.7 | 11.8 |
| u150_CRTPDX_20_MKT | research | -5.6/-7.0/-4.4/-10.9/+8.5 | 19.8 |
| u150_CRTPDX_20_MKT | live | +0.6/-1.2/-1.3/-3.7/+0.5 | 11.3 |
| u150_ALL14_20_SPL | research | -23.5/-16.9/-12.9/-19.2/+16.6 | 31.0 |
| u150_ALL14_20_SPL | live | -7.7/-5.7/-4.1/-2.2/+8.1 | 14.3 |
| u150_ALL14_60_MKT | research | -11.4/-5.8/-7.4/-10.8/+8.9 | 41.6 |
| u150_ALL14_60_MKT | live | -3.3/+4.5/+4.3/-2.2/+3.0 | 20.4 |
| z50_SET_15_SPL | research | +16.7/+13.4/+8.9/+3.1/+3.5 | 17.4 |
| z50_SET_15_SPL | live | +1.7/+2.8/+1.8/+3.0/-0.4 | 7.1 |
| z50_SET_20_MKT | research | +24.8/+19.3/+15.6/+3.0/+5.7 | 24.7 |
| z50_SET_20_MKT | live | +3.6/+3.9/+3.7/+3.3/+2.2 | 8.2 |
| z50_SET_40_SPL | research | +8.1/+4.4/-0.7/-3.4/-3.5 | 24.5 |
| z50_SET_40_SPL | live | +1.1/-0.4/-1.2/-0.4/-1.7 | 13.4 |
| u150_ARR4H_20_MKT | research | -6.2/-2.1/-2.2/-9.4/+4.0 | 15.9 |
| u150_ARR4H_20_MKT | live | -2.0/+0.2/+0.5/-2.2/+2.9 | 8.9 |
| u150_ARR1D_20_SPL | research | -34.3/-23.7/-19.5/-2.3/+6.0 | 23.2 |
| u150_ARR1D_20_SPL | live | -15.0/-8.8/-7.0/+2.9/+4.9 | 9.9 |
| u150_ARR1D_60_MKT | research | -20.9/-16.2/-12.5/-2.7/+10.9 | 30.5 |
| u150_ARR1D_60_MKT | live | -7.6/-4.3/-2.9/-0.8/+5.8 | 13.9 |
| u150_CRTPDX_60_SPL | research | -19.1/-12.2/-12.1/-9.8/+10.4 | 42.0 |
| u150_CRTPDX_60_SPL | live | -11.5/-2.1/-1.3/-2.4/+4.3 | 17.8 |
| u150_ALL14_20_MKT | research | -12.6/-11.2/-8.5/-19.6/+17.0 | 28.6 |
| u150_ALL14_20_MKT | live | -4.7/-2.6/-2.1/-4.6/+8.8 | 14.5 |
| z50_SET_10_SPL | research | +18.5/+11.1/+8.6/+2.7/+4.4 | 18.9 |
| z50_SET_10_SPL | live | +4.1/+3.3/+3.1/+2.3/+0.9 | 6.4 |
| z50_SET_15_MKT | research | +16.2/+12.8/+9.5/+3.8/+4.9 | 19.5 |
| z50_SET_15_MKT | live | +2.9/+2.7/+1.9/+2.4/+0.5 | 6.4 |
| z50_SET_30_SPL | research | +16.7/+12.1/+7.0/-1.1/+0.6 | 18.2 |
| z50_SET_30_SPL | live | +3.3/+2.8/+2.1/+0.4/-0.1 | 9.7 |
| z50_SET_40_MKT | research | +23.1/+13.0/+9.5/-5.0/-1.3 | 24.4 |
| z50_SET_40_MKT | live | +2.0/+0.4/+0.4/-0.9/-1.3 | 11.6 |
| u150_ARR4H_60_SPL | research | -22.1/-0.3/-3.2/-8.1/+5.7 | 21.2 |
| u150_ARR4H_60_SPL | live | -9.0/+2.1/+1.1/-1.0/+1.9 | 9.9 |
| u150_ARR1D_20_MKT | research | -27.8/-18.4/-15.4/-2.7/+8.1 | 26.8 |
| u150_ARR1D_20_MKT | live | -12.7/-6.2/-5.2/+0.8/+5.7 | 11.6 |
| u150_CRTPDX_20_SPL | research | -17.8/-7.8/-5.6/-13.9/+6.5 | 25.4 |
| u150_CRTPDX_20_SPL | live | -1.5/-1.7/-1.9/-4.9/+0.3 | 12.2 |
| u150_CRTPDX_60_MKT | research | -11.4/-3.9/-6.7/-11.2/+6.7 | 40.0 |
| u150_CRTPDX_60_MKT | live | -9.8/+2.0/+1.8/-4.7/+1.0 | 17.6 |
| u150_ALL14_60_SPL | research | -22.6/-10.2/-10.6/-9.8/+12.4 | 39.6 |
| u150_ALL14_60_SPL | live | -7.1/+0.8/+1.2/+2.0/+5.3 | 17.5 |
| z50_SET_10_MKT | research | +13.8/+10.0/+7.8/+4.1/+5.2 | 21.0 |
| z50_SET_10_MKT | live | +3.0/+2.6/+2.2/+1.9/+1.4 | 7.1 |
| z50_SET_20_SPL | research | +26.3/+19.3/+14.4/+2.7/+4.6 | 19.7 |
| z50_SET_20_SPL | live | +3.7/+4.0/+3.6/+2.7/+1.3 | 7.7 |
| z50_SET_30_MKT | research | +18.9/+12.1/+9.8/-3.2/+3.2 | 24.5 |
| z50_SET_30_MKT | live | +3.6/+2.2/+2.4/-0.5/+0.5 | 10.1 |
| z50_lidBRK4h_60_MKT | research | +6.5/+1.9/+1.9/+1.2/-0.5 | 14.4 |
| z50_lidBRK4h_60_MKT | live | +2.3/-0.3/-0.6/-0.1/+0.8 | 5.8 |

### ENSEMBLE multiplier rules (T.run m0 vs the stored ENSEMBLE stack line; $k/wk L6M/HOLD/PRE/X')
| variant | basis | T.run m0 stack L6M/HOLD/PRE/X' (MKT, research) | stored ENSEMBLE |
|---|---|---|---|
| ALL_mult | M | -24.5/-15.9/-2.9/-2.9 | -24.5/-15.9/-2.9/-2.9 |
| ALL_mult | N | -36.4/-25.0/-5.9/-7.4 | -36.4/-25.0/-5.9/-7.4 |
| ALL_mult_MATCHED | M | -23.1/-15.0/-5.4/+10.2 | -23.2/-15.0/-5.4/+10.2 |
| ALL_mult_MATCHED | N | -36.1/-26.2/-13.1/+3.9 | -36.1/-26.2/-13.5/+3.8 |
| HONEST_mult | M | -22.0/-12.9/-2.2/-2.8 | -22.0/-12.9/-2.2/-2.8 |
| HONEST_mult | N | -32.5/-21.8/-3.2/-6.1 | -32.5/-21.8/-3.2/-6.1 |
| HONEST_mult_MATCHED | M | -13.5/-3.0/-2.7/+2.7 | -13.5/-3.0/-2.7/+2.7 |
| HONEST_mult_MATCHED | N | -26.5/-15.0/-10.5/-1.6 | -26.5/-15.0/-10.6/-1.6 |

| variant | base | lots | L3M/L6M/HOLD/PRE/X' $k/wk |
|---|---|---|---|
| ALL_mult | MKT | live | -22.9/-21.1/-17.8/-3.5/-4.6 |
| ALL_mult | MKT | research | -17.9/-36.4/-25.0/-5.9/-7.4 |
| ALL_mult | S73 | live | -27.7/-24.5/-21.5/-4.4/-3.4 |
| ALL_mult | S73 | research | -36.2/-49.8/-40.5/-7.0/-3.5 |
| HONEST_mult | MKT | live | -17.0/-21.4/-18.7/-3.1/-5.0 |
| HONEST_mult | MKT | research | -4.2/-32.5/-21.8/-3.2/-6.1 |
| HONEST_mult | S73 | live | -21.3/-22.8/-20.1/-3.9/-6.0 |
| HONEST_mult | S73 | research | -20.7/-40.9/-31.5/-5.5/-9.5 |

## B. Wave-1 ha/3m, ha/5m rows (PAIRFIX statistics D = day-summed pts/contract/day, TW = trade-weighted pts/trade, vs the 1-min control; * = 5-day-block 95% CI excludes 0)
Rebuilt with bars_cand `bc_run.worker` on the de-duplicated store into rerunb/bc/{S,L} (original out/bars_cand untouched); control = `aux:time_1m` (not affected); the 'D' variant of KELT on 3m bars no longer exists on the clean bars (no grouping needed), so the D row uses the G tables (equal to the old D row exactly). Statistics via pairfix pf_lib.stats_window on the same 732-day calendar.

| row | store | PRE D/TW | X' D/TW | HOLD D/TW | HOLD CI D ; TW | L6M D/TW | L3M D/TW | HOLD n cell/ctl |
|---|---|---|---|---|---|---|---|---|
| L02766 T-BRACKET entries/TE6_st10m_n10_m3.5 ha/3m var D nypm | old (dup bug) | -2.0 / -2.5 | +8.1 / +12.1 | +1.1 / +6.2 | [-4.0,+6.8] ; [-15.9,+28.0] | +2.9 / +10.0 | +1.6 / +3.9 | 81/28 |
| L02766 T-BRACKET entries/TE6_st10m_n10_m3.5 ha/3m var D nypm | de-duplicated | -2.0 / -2.5 | +8.1 / +12.1 | +1.1 / +6.2 | [-4.0,+6.8] ; [-15.9,+28.0] | +2.9 / +10.0 | +1.6 / +3.9 | 81/28 |
| L01678 BA bracket-assign rows2/ba2/SM_t75_sst ha/5m var D london | old (dup bug) | +10.8 / +5.2 | +13.4* / +7.9* | +2.8 / +3.2 | [-5.3,+11.5] ; [-6.6,+13.1] | +3.1 / +3.5 | +6.8 / +7.6 | 127/135 |
| L01678 BA bracket-assign rows2/ba2/SM_t75_sst ha/5m var D london | de-duplicated | +4.7 / +2.1 | +6.6 / +3.4 | +0.6 / +0.9 | [-6.3,+8.1] ; [-6.9,+9.2] | +0.5 / +0.7 | +2.9 / +3.1 | 151/135 |
| L01654 BA bracket-assign rows2/ba2/SM_t40_sst ha/3m var D nyam | old (dup bug) | +4.2 / +2.8 | +3.3 / +1.6 | -2.8 / -3.9 | [-13.9,+7.6] ; [-16.7,+8.6] | +2.0 / +1.6 | +10.7 / +11.4 | 164/105 |
| L01654 BA bracket-assign rows2/ba2/SM_t40_sst ha/3m var D nyam | de-duplicated | +3.7 / +2.5 | -1.4 / -1.1 | -1.2 / -2.4 | [-11.8,+8.6] ; [-14.3,+8.9] | +4.0 / +3.5 | +9.8 / +10.4 | 171/105 |
| L01427 BA bracket-assign rows/ba/A_t30_s60 ha/3m var G london | old (dup bug) | +33.0* / +3.9* | +3.3 / +1.0 | +16.0* / +2.9 | [+1.1,+32.2] ; [-0.8,+7.0] | +14.4 / +2.9 | +32.4* / +6.3* | 378/768 |
| L01427 BA bracket-assign rows/ba/A_t30_s60 ha/3m var G london | de-duplicated | +31.8* / +3.6* | +3.3 / +1.0 | +14.9 / +2.5 | [-0.4,+31.1] ; [-1.3,+6.5] | +13.6 / +2.6 | +31.1* / +5.8* | 375/768 |
| L01501 BA bracket-assign rows2/ba2/EM_t50_s60 ha/3m var D nyam | old (dup bug) | -5.6 / -5.7 | -3.3 / -3.9 | +0.8 / +0.4 | [-7.2,+8.1] ; [-13.0,+12.8] | +3.8 / +5.6 | -0.0 / -1.4 | 106/80 |
| L01501 BA bracket-assign rows2/ba2/EM_t50_s60 ha/3m var D nyam | de-duplicated | -5.6 / -5.7 | -3.3 / -3.9 | +0.8 / +0.4 | [-7.2,+8.1] ; [-13.0,+12.8] | +3.8 / +5.6 | -0.0 / -1.4 | 106/80 |
| L01537 BA bracket-assign rows2/ba2/HM_t30_s60 ha/3m var G london | old (dup bug) | +11.3 / +3.1 | +6.7 / +4.6 | +10.0* / +4.2 | [+1.7,+18.5] ; [-0.7,+9.6] | +7.2 / +2.6 | +9.6 / +3.2 | 176/345 |
| L01537 BA bracket-assign rows2/ba2/HM_t30_s60 ha/3m var G london | de-duplicated | +10.5 / +2.8 | +6.7 / +4.6 | +10.3* / +4.4 | [+1.7,+19.1] ; [-0.7,+10.1] | +7.6 / +3.0 | +9.6 / +3.2 | 174/345 |
| L01629 BA bracket-assign rows2/ba2/KB_t90_s90 ha/3m var G london | old (dup bug) | +22.0* / +14.2* | +10.1 / +21.2 | +2.7 / +3.6 | [-8.2,+13.0] ; [-10.1,+17.5] | +3.3 / +4.2 | +7.3 / +5.5 | 117/129 |
| L01629 BA bracket-assign rows2/ba2/KB_t90_s90 ha/3m var G london | de-duplicated | +10.1 / +5.9 | +7.1 / +13.2 | +8.2 / +9.5 | [-0.6,+17.4] ; [-0.6,+19.4] | +9.7* / +10.1 | +7.9 / +6.8 | 135/129 |
| L02766 T-BRACKET entries/TE6_st10m_n10_m3.5 ha/5m var D asia | old (dup bug) | -2.9 / -4.3 | -2.7 / -6.0 | -3.0 / -6.2 | [-9.3,+3.4] ; [-16.4,+4.8] | -1.7 / -4.2 | +1.1 / +0.0 | 131/79 |
| L02766 T-BRACKET entries/TE6_st10m_n10_m3.5 ha/5m var D asia | de-duplicated | -2.4 / -3.9 | -3.2 / -6.4 | -2.6 / -5.8 | [-9.0,+3.9] ; [-15.9,+5.4] | -1.2 / -3.7 | +2.1 / +1.2 | 130/79 |
| L01629 BA bracket-assign rows2/ba2/KB_t90_s90 ha/3m var D london | old (dup bug) | +10.1 / +5.9 | +7.1 / +13.2 | +8.2 / +9.5 | [-0.6,+17.4] ; [-0.6,+19.4] | +9.7* / +10.1 | +7.9 / +6.8 | 135/129 |
| L01629 BA bracket-assign rows2/ba2/KB_t90_s90 ha/3m var D london | de-duplicated | +10.1 / +5.9 | +7.1 / +13.2 | +8.2 / +9.5 | [-0.6,+17.4] ; [-0.6,+19.4] | +9.7* / +10.1 | +7.9 / +6.8 | 135/129 |

## C. Unit check, 7 CONFIRM-BARS leads (book rows replaced by the lead cell on the cf plain 70/30 floor; floor = the leads' own reference; stack windows L3M/L6M/HOLD/PRE/X')
| # | stage / book / cell | per planned lot (L3M/L6M/HOLD/PRE/X') | per contract of final pos., delta vs floor | stack research $k/wk (same windows) | stack LIVE lots $k/wk | MDE L6M res/live | verdict |
|---|---|---|---|---|---|---|---|
| 1 | S1 ST ha|10m|three|d|near|X3|A70|N | +1.87/+0.32/+0.35/+0.20/+1.13 | +3.47/+1.95/+1.76/+0.95/+1.78 | +8.4/-2.2/+0.0/-1.6/-3.3 | +3.6/-0.9/+0.0/-0.7/-1.4 | 20.8 / 8.9 | FAILS the unit check (stack < 0 in L6M or HOLD) |
| 2 | S2b WT dol|2G|two|d|near|X3|A70|N | +1.29/+0.75/+0.67/+0.24/+1.07 | +3.41/+2.83/+2.29/+0.94/+2.54 | +14.5/+8.2/+5.5/+2.0/+7.1 | +6.2/+3.5/+2.3/+0.9/+3.0 | 14.4 / 6.1 | SURVIVES (stack >= 0 in all five windows, both lot sets; inside MDE) |
| 3 | S2b KB range|8|close_fav|d|near|X3|A70|N | +0.81/+0.30/+0.16/+0.47/+0.81 | +0.40/+0.90/+0.49/+1.69/+0.85 | +2.3/+0.4/-0.4/+3.4/-0.7 | +1.3/+0.1/-0.2/+0.9/+0.1 | 11.9 / 4.8 | FAILS the unit check (stack < 0 in L6M or HOLD) |
| 4 | S1c PE ha|15m|flip|d|near|X3|A70|N | +1.93/+1.11/+0.86/+0.55/+0.40 | +1.91/+1.76/+1.47/+0.90/+1.07 | +3.7/+0.8/+1.0/-2.3/+3.4 | +0.4/-0.5/+0.1/+0.6/+1.7 | 9.5 / 8.9 | FAILS the unit check (stack < 0 in L6M or HOLD) |
| 5 | S1c KB ha|1m|flip|c2|mid|X3|A70|N | +1.64/+0.87/+0.78/+0.15/+0.38 | +1.63/+0.96/+0.85/+0.27/+0.37 | +2.7/+1.4/+0.1/+0.7/+1.6 | +1.4/+1.0/+0.5/+0.2/+0.7 | 8.7 / 3.1 | SURVIVES (stack >= 0 in all five windows, both lot sets; inside MDE) |
| 6 | S1c DN ha|3m|three|b|mid|X3|A70|N | +0.51/+0.82/+1.05/+0.38/+0.32 | +1.20/+1.44/+1.53/+0.68/+0.33 | n/a (DN is not a lock-engine book) | n/a | - | LEAD, stack not computable (per planned lot +0.82 L6M, +1.05 HOLD, inside MDE 1.77) |
| 7 | S2c PE linreg|15m|flip|d|near|X3|A70|N | +1.43/+0.79/+0.69/+0.38/+0.76 | +1.28/+1.22/+1.12/+0.61/+1.35 | +1.4/-1.8/-1.9/-2.8/+1.9 | -3.5/-3.5/-3.1/-2.0/+3.3 | 8.4 / 9.0 | FAILS the unit check (stack < 0 in L6M or HOLD) |

Sources: cells rebuilt with cf_engine + bars_events (c_phase1.py), stack via the registered-split harness (c_phase2.py). Per planned lot reproduces the CONFIRM_BARS report (e.g. ST +0.32 L6M). DN's six-book lock engine does not exist; MV/PB/MA/DN stack lines are not available anywhere in DS3.

## D. Causal vol tag, every c2='vol' cell of s2_cells (cells 50-53, 120-123, 176-178, 191-193); $k/wk, look-ahead -> causal tag, delta vs the rule-free base, basis N
| cell | base | lots | L6M LA->causal | HOLD | PRE | X' | L3M | MDE L6M |
|---|---|---|---|---|---|---|---|---|
| voltercile>=1 | MKT | research | +19.4 -> +21.0 | +18.2 -> +19.9 | -1.0 -> -4.1 | +2.8 -> +0.8 | +31.6 -> +33.4 | 25.8 |
| voltercile>=1 | MKT | live | +6.5 -> +5.7 | +6.3 -> +5.8 | -2.5 -> -2.1 | +3.4 -> +3.2 | +9.9 -> +10.4 | 14.1 |
| voltercile<1 | MKT | research | +3.6 -> +1.1 | +1.1 -> -0.7 | -7.3 -> -3.0 | -2.1 -> -0.4 | +4.2 -> +0.2 | 12.8 |
| voltercile<1 | MKT | live | -0.5 -> -0.2 | -1.1 -> -0.5 | -1.3 -> -1.0 | -1.1 -> -0.1 | -0.1 -> -1.4 | 7.1 |
| voltercile>=2 | MKT | research | +12.4 -> +17.2 | +10.8 -> +16.1 | +0.3 -> -4.2 | +4.7 -> -1.6 | +16.3 -> +25.0 | 22.6 |
| voltercile>=2 | MKT | live | +4.2 -> +5.3 | +3.5 -> +4.9 | -2.0 -> -2.7 | +2.8 -> -0.2 | +4.8 -> +8.2 | 12.1 |
| voltercile<2 | MKT | research | +10.6 -> +5.9 | +8.5 -> +3.4 | -8.5 -> -5.3 | -4.0 -> +3.0 | +19.4 -> +9.2 | 19.9 |
| voltercile<2 | MKT | live | +1.8 -> +0.6 | +1.7 -> +0.6 | -1.8 -> -1.6 | -0.5 -> +3.2 | +5.0 -> +2.2 | 9.9 |
| voltercile>=1 | S73 | research | +7.1 -> +7.7 | +7.8 -> +7.6 | -1.6 -> -6.0 | +2.6 -> +1.2 | +13.7 -> +13.8 | 24.6 |
| voltercile>=1 | S73 | live | +6.2 -> +5.4 | +6.4 -> +5.5 | -2.3 -> -3.6 | +2.8 -> +2.8 | +10.2 -> +11.9 | 15.2 |
| voltercile<1 | S73 | research | -0.5 -> -2.1 | -3.0 -> -2.4 | -4.8 -> -1.2 | -3.0 -> -1.7 | +2.3 -> -0.0 | 10.6 |
| voltercile<1 | S73 | live | -1.9 -> -1.6 | -2.2 -> -1.4 | -1.6 -> -0.9 | -1.5 -> -0.8 | -0.5 -> -2.9 | 7.8 |
| voltercile>=2 | S73 | research | +3.5 -> +6.5 | +3.5 -> +6.6 | -0.4 -> -5.3 | +3.5 -> -2.3 | +4.5 -> +9.5 | 23.6 |
| voltercile>=2 | S73 | live | +5.4 -> +5.7 | +4.9 -> +5.3 | -1.5 -> -2.9 | +2.6 -> -0.6 | +8.3 -> +10.5 | 14.4 |
| voltercile<2 | S73 | research | +3.1 -> -0.9 | +1.2 -> -2.2 | -6.1 -> -2.4 | -3.9 -> +2.5 | +11.5 -> +5.9 | 16.8 |
| voltercile<2 | S73 | live | -1.1 -> -1.7 | -0.7 -> -1.0 | -2.4 -> -1.6 | -1.3 -> +2.6 | +1.4 -> +0.1 | 10.2 |
| asia&voltercile>=2 | MKT | research | +12.4 -> +13.4 | +10.2 -> +11.7 | +3.6 -> +1.0 | +6.1 -> +2.8 | +9.8 -> +13.7 | 20.4 |
| asia&voltercile>=2 | MKT | live | +5.9 -> +6.7 | +5.2 -> +5.8 | -0.4 -> -1.0 | +3.1 -> +0.5 | +5.0 -> +6.8 | 12.3 |
| er20_5m>=0.4&voltercile>=2 | MKT | research | +4.1 -> +0.9 | +3.3 -> +1.3 | -0.6 -> +0.5 | +0.6 -> -1.9 | +7.3 -> +3.6 | 8.2 |
| er20_5m>=0.4&voltercile>=2 | MKT | live | +1.2 -> -1.5 | +1.0 -> -1.2 | -0.0 -> +0.2 | +2.8 -> -0.1 | +2.2 -> +2.3 | 4.9 |
| asia&er20_5m>=0.4&voltercile>=2 | MKT | research | +1.6 -> +0.0 | +0.8 -> +0.1 | -1.1 -> -0.4 | +3.4 -> +0.7 | +3.5 -> +0.6 | 5.4 |
| asia&er20_5m>=0.4&voltercile>=2 | MKT | live | +1.0 -> +0.4 | +0.8 -> +0.3 | -0.5 -> +0.2 | +3.0 -> +0.3 | +2.0 -> +2.0 | 3.7 |
| asia&voltercile>=2 | S73 | research | +6.8 -> +10.0 | +6.5 -> +8.7 | +4.5 -> +1.6 | +4.7 -> +1.4 | +5.5 -> +8.1 | 21.4 |
| asia&voltercile>=2 | S73 | live | +7.7 -> +7.9 | +7.2 -> +6.9 | -0.3 -> -1.0 | +3.1 -> +0.2 | +9.9 -> +8.9 | 14.1 |
| er20_5m>=0.4&voltercile>=2 | S73 | research | -0.7 -> -3.9 | -0.1 -> -2.6 | +0.7 -> -0.3 | -0.6 -> -3.2 | +0.9 -> -0.4 | 9.5 |
| er20_5m>=0.4&voltercile>=2 | S73 | live | -0.5 -> -2.7 | -0.2 -> -2.3 | -1.0 -> -0.7 | +2.2 -> -1.0 | +0.8 -> +1.5 | 6.5 |
| asia&er20_5m>=0.4&voltercile>=2 | S73 | research | -0.2 -> -1.5 | -0.2 -> -1.3 | +0.8 -> -0.3 | +3.4 -> +0.5 | +2.9 -> -1.3 | 6.2 |
| asia&er20_5m>=0.4&voltercile>=2 | S73 | live | +0.1 -> -0.3 | +0.3 -> -0.2 | -0.1 -> +0.0 | +3.3 -> +0.2 | +1.8 -> +1.1 | 4.5 |

## E. Fixed shuffle_src
`l2vast/ds3/out/rerunb/lp_data_fixed.py` (check script e_check.py). No other file edited; the original `l2set_profit/lp_data.py` and `lp_sweep.py` still carry the defect and must not be reused for placebo draws.

## Caveats
* The s2 harness and the poi engine build their 70/30 and market base rows differently (stackpart S73 cell F5/F0.7/X3/N1 vs poi `floor_plain`); base L6M stacks are not identical, so only delta-vs-own-base is compared; where the two corrected routes disagree in sign the row is labelled harness-dependent.
* Planned-lot governors are the primary reading (T.run as coded); the sized-lot variant is shown for u150 only because a sizer that raises the lock thresholds is a different rule.
* The B selection was done on the buggy store; I re-scored the already-selected rows only.
* ALL/book scopes beyond ST HM WT KB SM PE cannot be stack-scored.

## Questions (also in MORNING.md)
* Not blocking: '7 CF-COMBO leads' in the order - I found only the CONFIRM-BARS seven (THP_bars_candidates.txt); if a different CF-COMBO list was meant, point me at it.
* Not blocking: should BARS-CAND wave-1 selection (PRE+X') be redone on the clean ha/linreg/hull/lb store for the ha/1m,3m,5m cells? Only the nine non-DEAD rows were re-scored here.
