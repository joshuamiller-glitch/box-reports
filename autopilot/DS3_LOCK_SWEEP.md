# DS3_LOCK_SWEEP - GOV-2: the D6 lock parameters on the D6-faithful engine (Sat 2026-10-31, characterisation only, NOT tuning)

Research only. Masks capped 20260206, UNTOUCHED never read. Windows L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131 (14 / 28 / 32 / 75 / 44 weeks). Engine: GOV-1 gf_lib extended in `l2vast/ds3/code/locksweep/ls2_lib.py` (spec override, fixed-SizeMult option, trough kernel); runs `run_sweep.py` (505 runs, ~4 min), tables `report.py page1.py report2.py`; outputs `l2vast/ds3/out/locksweep/` (sweep_long.csv = every setting x window: mean, SD, maxDD, worst-20, worst week, fire counts, deltas with MDE; lag_placebo.csv; tables_body.md / tables_body2.md; sweep_*.pkl). TIE-OUT: composite with D6 defaults + combined 12R(K6) = +17.9 / +16.5 / +15.3 / +0.3 / +2.3 vs the as-is stack (GOV-1 numbers to the dollar); without the combined lock +24.3 / +22.3 / +18.9 / +7.0 / +13.4.
**Everything below is post-hoc where a parameter is read off a window**: the grid was run once, I did not select a setting, and no row is a candidate. MDE is the paired-week 2.8 SE; `*` marks a delta beyond its MDE. Tier: STRUCTURE / measurement.

Definitions. C = the Sunday composite on the D6-faithful engine (integer half-up min-1 lots, live lots, Native 1.28, N basis, ER sizer, 70/30 split, A6 at market, per-book SizeMult = running max over all the book's signals, BookR on the session planned lot). A = the stack as it is (join 2.45, no ER/split/PE/zone/cut, planned-lot R, SizeMult 1) run through the SAME lock engine. A0 = A with the D6 per-book locks and no combined lock = "the as-is stack as it is" of GOV-1. A(s) = A with the same lock setting s as the composite. "Lock effect" = the setting minus the same stack with that lock off, other locks at D6 defaults. Combined lock = stack MTM (realised + open) <= -F x K6 BookR, K6 BookR = 2 lots x running-max SizeMult of K6's signals today (1.0 before K6's first signal of the day, ASSUMPTION; D6 reset value unknown) x 60 pt x $20 = $2,400 x SizeMult per R; fires flatten all books and cancel the rest of the week. Week = ISO label week starting Sunday 18:00 ET.

## Page 1 - the table for the composite: the combined week lock multiple (other locks at D6 defaults)

**The open question for the user: what multiple is D6's combined week lock?** GOV-1 assumed 12R from the T-HALT-RESUME phrase 'the live week floor (-12R, off until Monday)'; the user's reply fixed only the unit (R = K6's BookR), not the multiple. Per-book floors are separately -12R of the book's own BookR. Everything in the table moves with the answer.

Each cell is L3M / L6M / HOLD / PRE / X' in $k per week (* beyond MDE). Fired = weeks fired per window (and of all 149). Forgone / avoided = per week, L6M ; PRE ; X' (forgone = weeks where the lock lost money vs no combined lock, avoided = weeks where it gained). maxDD and worst week = weekly series of the composite, same window order.

| combined lock | $ threshold at SizeMult 0.5 / 1 / 1.5 | C minus A0 (as-is as it is) | C(s) minus A(s) (same lock on both) | lock effect on C (vs no combined) | lock effect on A (vs no combined) | weeks fired (C) | weeks fired (A) | forgone / avoided $k per wk (C) | C maxDD $k | C worst week $k |
|---|---|---|---|---|---|---|---|---|---|---|
| off | - | +24.3*/+22.3*/+18.9*/+7.0/+13.4 | +24.3*/+22.3*/+18.9*/+7.0/+13.4 | +0.0/+0.0/+0.0/+0.0/+0.0 | +0.0/+0.0/+0.0/+0.0/+0.0 | 0/0/0/0/0 (all 0/149) | 0/0/0/0/0 (all 0/149) | -0.0 / 0.0 ; -0.0 / 0.0 ; -0.0 / 0.0 | 21/21/113/263/126 | -21/-21/-75/-121/-72 |
| 6R | 7.2/14.4/21.6k | -9.4/-8.8/-6.0/-10.8/-2.0 | +6.7/+9.6/+10.1/+4.9/+2.7 | -33.7/-31.1*/-24.9/-17.8*/-15.4* | -16.1/-18.4*/-16.1/-15.7*/-4.7 | 9/17/19/56/37 (all 112/149) | 11/21/24/57/35 (all 116/149) | 32.0 / 0.9 ; 26.6 / 8.8 ; 20.2 / 4.8 | 54/54/54/160/291 | -23/-23/-23/-23/-22 |
| 8R | 9.6/19.2/28.8k | +13.2/+8.5/+8.9/-7.4/-2.6 | +28.4/+22.9/+22.1/+6.0/+4.8 | -11.2/-13.8/-10.0/-14.4/-16.0* | -15.2/-14.4/-13.2/-13.4*/-7.5 | 5/11/13/49/34 (all 96/149) | 10/16/19/51/34 (all 104/149) | 14.6 / 0.7 ; 22.1 / 7.6 ; 20.1 / 4.1 | 29/29/29/161/309 | -29/-29/-29/-30/-32 |
| 10R | 12.0/24.0/36.0k | +18.0/+10.6/+10.3/-1.5/-2.3 | +24.0*/+20.2/+19.9/+7.6/+3.1 | -6.3/-11.7/-8.6/-8.6/-15.7* | -6.0/-9.6/-9.6/-9.1/-5.4 | 4/10/12/40/33 (all 85/149) | 7/12/15/42/28 (all 85/149) | 12.3 / 0.6 ; 15.3 / 6.8 ; 19.3 / 3.6 | 28/28/28/202/298 | -28/-28/-28/-38/-36 |
| 12R | 14.4/28.8/43.2k | +17.9/+16.5/+15.3/+0.3/+2.3 | +25.5*/+27.8*/+23.4*/+8.1/+8.0 | -6.5/-5.8/-3.5/-6.7/-11.1 | -7.6/-11.3/-8.1/-7.8/-5.7 | 4/8/10/35/28 (all 73/149) | 6/11/14/35/25 (all 74/149) | 6.2 / 0.4 ; 12.8 / 6.1 ; 13.9 / 2.8 | 28/28/28/274/214 | -28/-28/-28/-44/-44 |
| 15R | 18.0/36.0/54.0k | +17.1/+17.8/+16.3/-0.1/+3.2 | +22.3*/+27.7*/+23.8*/+8.3/+10.6 | -7.2/-4.5/-2.6/-7.1/-10.2 | -5.2/-9.9/-7.6/-8.4/-7.4 | 4/6/8/34/24 (all 66/149) | 5/9/12/29/21 (all 62/149) | 4.6 / 0.1 ; 12.8 / 5.7 ; 12.4 / 2.2 | 28/28/28/255/234 | -28/-28/-28/-55/-50 |
| 20R | 24.0/48.0/72.0k | +13.0/+15.5/+12.2/-0.6/+8.0 | +9.9/+18.5/+14.0/+4.1/+12.8 | -11.4/-6.8/-6.7/-7.7/-5.4 | +3.1/-3.0/-1.9/-4.7/-4.8 | 4/6/8/28/14 (all 50/149) | 1/3/5/20/12 (all 37/149) | 6.8 / 0.0 ; 11.9 / 4.2 ; 6.6 / 1.2 | 60/60/77/312/117 | -60/-60/-72/-72/-50 |
| 30R | 36.0/72.0/108.0k | +24.3*/+20.9*/+18.9*/-2.3/+10.5 | +22.9*/+20.2*/+18.1*/+0.1/+10.5 | +0.0/-1.4/+0.1/-9.3/-2.9 | +1.4/+0.7/+0.8/-2.4/-0.0 | 0/1/3/21/9 (all 33/149) | 1/1/2/10/1 (all 13/149) | 1.4 / 0.0 ; 11.6 / 2.3 ; 3.8 / 0.9 | 21/36/72/304/172 | -21/-36/-72/-92/-52 |
| 40R | 48.0/96.0/144.0k | +24.3*/+22.3*/+19.0*/-2.5/+11.7 | +24.3*/+22.3*/+19.0*/-1.8/+12.3 | +0.0/+0.0/+0.1/-9.6/-1.6 | +0.0/+0.0/+0.0/-0.7/-0.6 | 0/0/1/17/5 (all 23/149) | 0/0/0/4/1 (all 5/149) | -0.0 / 0.0 ; 11.1 / 1.5 ; 2.2 / 0.5 | 21/21/109/255/173 | -21/-21/-75/-92/-53 |
| 50R | 60.0/120.0/180.0k | +24.3*/+22.3*/+19.0*/+2.0/+13.6 | +24.3*/+22.3*/+19.0*/+2.4/+13.6 | +0.0/+0.0/+0.1/-5.0/+0.3 | +0.0/+0.0/+0.0/-0.4/+0.0 | 0/0/1/9/1 (all 11/149) | 0/0/0/1/0 (all 1/149) | -0.0 / 0.0 ; 5.7 / 0.7 ; -0.0 / 0.3 | 21/21/109/221/126 | -21/-21/-75/-92/-60 |
| 75R | 90.0/180.0/270.0k | +24.3*/+22.3*/+18.4*/+7.5/+13.4 | +24.3*/+22.3*/+18.4*/+7.5/+13.4 | +0.0/+0.0/-0.4/+0.5/+0.0 | +0.0/+0.0/+0.0/+0.0/+0.0 | 0/0/1/2/0 (all 3/149) | 0/0/0/0/0 (all 0/149) | -0.0 / 0.0 ; -0.0 / 0.5 ; -0.0 / 0.0 | 21/21/128/234/126 | -21/-21/-90/-92/-72 |

Reading (post-hoc, plain):
- The combined lock has NO multiple at which it adds mean P&L to the composite in any window: effect vs no combined lock is <= 0 in every row (the only positives are +0.3 / +0.5 in X' / PRE at 50R / 75R, i.e. 1 to 11 fires). Same on the as-is stack (A), where it costs MORE: at 12R -11.3k L6M on A vs -5.8k on C.
- Therefore the question the user asked ("do the locks help or hurt each?") has the answer: at 6R-20R it hurts both; it hurts the as-is stack roughly twice as much as the composite in L6M, so the like-for-like lead of the composite over the as-is stack (C(s) minus A(s)) is LARGER with the lock (+27.8k L6M at 12R) than without it (+22.3k), while the lead against the as-is stack as it is today with no combined lock (C minus A0) is smaller (+16.5k). Which of the two is the right comparison depends on whether the live as-is stack carries the combined lock.
- 6R-8R ruinous (-31k and -14k L6M); 10R-20R costs 4.5 to 12k a week in L6M and 7 to 11k in X'; 30R is almost inert in L3M/L6M/HOLD (-1.4k at most) but still costs -9.3k in PRE (21 PRE fires); 40R and above are inert in the recent windows (0 fires L3M/L6M, 1 HOLD) and cost -9.6k in PRE at 40R, -5.0k at 50R; 75R fires 3 times in 149 weeks. Fully inert (zero fires in 149 weeks) needs about 85R of K6 (deepest weekly trough in the no-lock world -84.4R in PRE).
- Protective only in the narrow tail sense: it caps the worst single week (PRE -121k to -44k at 12R, HOLD -75k to -28k, X' -72k to -44k) and weeks <= -40k fall from 2 to 0 in HOLD, but it does not lower maxDD (L6M 21k -> 28k, PRE 263k -> 274k, X' 126k -> 214k) and in L6M it makes the worst week worse (-21k -> -28k, the flatten slips). Weekly SD falls in PRE/X' (58 -> 53, 34 -> 29) and rises in L3M/L6M (47 -> 51, 45 -> 51). Risk lines per window are in sections 1 and Q3c below.
- Sensitivity to the K6 SizeMult at the lock is the biggest hidden factor: 57 of 73 fires at 12R happen while K6's running max is 0.5, i.e. the lock fires at $14.4k, not $28.8k (mean threshold at fire $19.5k). Fixing SizeMult at 1.5 makes 12R = $43.2k and the effect shrinks to -7.9 / -6.6 / -3.8 / -9.4 / -3.0 with 4 / 26 / 10 fires (L6M / PRE / X'); at 2.0 it is about -6.7 / -3.3 / -1.8 / -5.4 / -1.9. See Q3b.
- K6 at market / others 70-30 (the decision number): the same shape, 12R: C minus A0 = +16.0 / +16.0 / +15.1 / +0.9 / +1.4 (section 10).

## Plain statement of what each lock does to the Sunday composite (the user's item 3; effects vs the same lock off, composite, $k/wk, L3M / L6M / HOLD / PRE / X'; D6 values at the base of 12R combined; post-hoc, the windows are read)

| lock (D6 value) | effect on composite (comb 12R base) | effect on composite (no combined) | effect on the as-is stack A | fires L6M | in words |
|---|---|---|---|---|---|
| entry test win side, +5R | -0.2 / +0.1 / +0.1 / +0.1 / 0.0 | -0.1 / +0.2 / +0.2 / 0.0 / 0.0 | +0.8 / +0.3 / +0.3 / 0.0 / 0.0 | 27 signals skipped | inert. +3R: +1.0 / +0.9 / +0.7 / -1.1 / 0.0 (206 skips); +8R: nothing (0 skips L6M) |
| entry test loss side, -2R | +2.5 / +0.8 / +0.7 / -0.5 / -0.5 | +1.6 / -0.6 / -0.4 / +0.4 / -0.9 | +4.6 / +1.0 / +0.7 / +1.8 / -2.5 | 305 signals skipped | about zero on the composite (inside +-1k); mildly helps the as-is stack in L3M-PRE. -1R is ruinous (-19.1 L6M, 986 skips); -3R about -0.4 |
| day arm 2R keep 50% | +3.6 / +6.8 / +5.4 / +3.6 / +1.6 | +2.3 / +1.3 / +0.2 / +2.7 / +1.2 | -8.4 / -1.8 / -2.2 / +1.9 / -1.2 | 127 book-days | the one per-book lock that helps the composite in all five windows (small, +1 to +7k); it costs the as-is stack in the recent windows. Its neighbours in the grid (1.5R, 2.5R, 3R; keep 25 / 75%) are mixed sign from -13.6 to +6.1: a local peak, not a plateau |
| per-book week floor 12R | +0.3 / -0.2 / -0.1 / +0.1 / 0.0 | +0.6 / 0.0 / -0.3 / +0.1 / -0.3 | 0.0 everywhere | 6 book-weeks | inert (+-0.3k). 8R: -0.3 L6M with 12 fires; 15R: nothing |
| combined week lock, 12R(K6) | -6.5 / -5.8 / -3.5 / -6.7 / -11.1 | - | -7.6 / -11.3 / -8.1 / -7.8 / -5.7 | 8 weeks (4 L3M, 35 PRE, 28 X', 73 of 149) | costs money everywhere; see page 1 for the multiple |
| all locks together (D6 per-book + combined 12R) vs all locks OFF | -2.9 / -5.5 / -4.0 / -3.0 / -11.3 | D6 per-book locks alone vs off: +3.5 / +0.4 / -0.5 / +3.7 / -0.2 | per-book alone +9.8 / +3.7 / +3.9 / +5.8 / -4.4; with combined +2.2 / -7.5 / -4.2 / -2.0 / -10.1 | | lock-off placebo (section 9): the per-book locks are worth about zero to +4k on the composite and +4 to +10k on the as-is stack; the combined lock turns that negative on both |

What multiple makes the combined lock inert vs protective: inert in L3M / L6M (no fires) needs about 35R of K6 at the free-running SizeMult (deepest L6M weekly trough -34.6R, L3M -29.5R); in all 149 weeks about 85R (deepest -84.4R). With K6's SizeMult held at 1.0 the L6M fires are 0 from 30R (20R still fires 4; Q3b: 30R, SizeMult 1.0 = 0 / 8 / 1 fires L6M / PRE / X'); held at 0.5 the same 30R still fires 4 / 30 / 14 times. So the answer in dollars: a threshold of roughly $50k to $70k or more is inert in the recent windows; the multiple that gives it depends on the SizeMult in force (30R is $36k at 0.5, $72k at 1.0, $108k at 1.5). Protective (cuts the worst weeks) from about 12R down; the cost of that protection is the forgone line: at 12R the lock gives up $6.2k a week to avoid $0.4k a week in L6M (PRE 12.8 vs 6.1, X' 13.9 vs 2.8).

NO recommendation to change the live setting. The decision table is page 1 and the question is the one above.


## Q2. Why the combined lock fires in 73 of 149 weeks at 12R (the user's item 2)

Short answer, measured below: the threshold is small relative to what the stack does in a week. (i) The stack's weekly SD is 14-24 K6-R (the stack's live base lots total 20 against K6's 2, so one K6 R is about a tenth of the stack's risk unit); (ii) the intra-week trough of the stack (the quantity the lock tests) is below -12R in 49% of all weeks and below -8R in 64% even with no lock, the median trough is -7R in L6M and -11R in PRE; (iii) 57 of the 73 fires occur while K6's running-max SizeMult is 0.5 (K6 has not had a with-trend x1.5 signal yet today), so the live dollar threshold is $14.4k, mean $19.5k at the fire, not $28.8k; (iv) 41 of 73 fires happen on Sunday evening or Monday, so the lock removes most of the week.

### Q2a. Weekly composite P&L in K6-R units (R = $2,400 at SizeMult 1; the composite has no combined lock here)

| window | weeks | mean | SD | p5 | p25 | median | p75 | p95 | min | share of weeks P&L <= -12R | trough (intra-week min MTM) median R | share trough <= -6R | <=-8R | <=-12R | <=-20R | <=-30R | deepest trough R |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 14 | +15.9 | 19.5 | -6.1 | +3.0 | +12.1 | +21.2 | +50.4 | -8.6 | 0.00 | -7.2 | 0.71 | 0.43 | 0.29 | 0.29 | 0.00 | -29.5 |
| L6M | 28 | +19.3 | 18.9 | -7.1 | +6.2 | +14.0 | +31.0 | +50.1 | -8.6 | 0.00 | -7.0 | 0.61 | 0.39 | 0.29 | 0.21 | 0.04 | -34.6 |
| HOLD | 32 | +17.7 | 23.1 | -18.7 | +5.1 | +15.0 | +31.0 | +53.6 | -31.4 | 0.06 | -7.2 | 0.62 | 0.44 | 0.34 | 0.28 | 0.09 | -75.8 |
| PRE | 75 | +10.3 | 24.2 | -30.7 | -6.5 | +11.9 | +26.6 | +48.5 | -50.4 | 0.17 | -11.2 | 0.76 | 0.67 | 0.48 | 0.39 | 0.29 | -84.4 |
| X' | 44 | +4.1 | 14.2 | -16.8 | -5.6 | +3.3 | +13.1 | +27.9 | -29.8 | 0.07 | -15.6 | 0.84 | 0.77 | 0.64 | 0.32 | 0.20 | -60.3 |

Trough = minimum over the week of (stack MTM / (K6 R at the then running-max SizeMult)), i.e. exactly the quantity the combined lock tests (the lock fires when it reaches -F). Share of weeks with trough <= -F is therefore the fire rate of an F-lock (apart from path interaction after a fire).
All 149 weeks: share trough <= -6R 0.75, -8R 0.64, -12R 0.49, -20R 0.34, -30R 0.22, -50R 0.07, -75R 0.02; deepest -84.4R.

Scale: the stack's weekly SD relative to one K6 R is the reason 12R(K6) is a small threshold for the stack. Weekly SD in K6-R, by window: L3M 19.5R, L6M 18.9R, HOLD 23.1R, PRE 24.2R, X' 14.2R.

### Q2b. Fired weeks and the rest of the week

#### Combined 12R(K6): weeks that trigger and what the rest of the week earned (composite, $k)

| window | weeks | fired | fire rate | week P&L if no lock: fired weeks mean | locked-in week P&L (lock on): fired weeks mean | rest of week after trigger (forgone) mean | share of fired weeks where rest > 0 (lock cost) | share where rest < 0 (lock helped) | sum forgone (cost) $k | sum avoided (help) $k | net $k | non-fired weeks mean P&L | mean SizeMult at fire |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 4 | 0.29 | +4.7 | -18.0 | +22.6 | 0.75 | 0.25 | +97 | +6 | -91 | +51.5 | 0.50 |
| L6M | 28 | 8 | 0.29 | +3.1 | -17.3 | +20.4 | 0.75 | 0.25 | +174 | +11 | -163 | +63.6 | 0.50 |
| HOLD | 32 | 11 | 0.34 | -6.0 | -16.2 | +10.2 | 0.64 | 0.36 | +244 | +131 | -112 | +68.0 | 0.50 |
| PRE | 75 | 36 | 0.48 | -10.0 | -24.0 | +13.9 | 0.58 | 0.39 | +963 | +461 | -502 | +56.8 | 0.78 |
| X' | 44 | 28 | 0.64 | -1.8 | -19.2 | +17.4 | 0.64 | 0.32 | +610 | +122 | -488 | +30.1 | 0.61 |

Trigger day of week (ET, all 73 fired weeks): Sunday 9, Monday 32, Tuesday 17, Wednesday 9, Thursday 6, Friday 0. Mean open positions flattened 2.2; mean later entries cancelled 55.0. SizeMult of K6 at fire: 1.0: 6, 1.5: 10, 2.0: 0, 0.5: 57 (mean 0.68). Dollar threshold at fire: $19.5k mean.

#### Combined 8R(K6): weeks that trigger and what the rest of the week earned (composite, $k)

| window | weeks | fired | fire rate | week P&L if no lock: fired weeks mean | locked-in week P&L (lock on): fired weeks mean | rest of week after trigger (forgone) mean | share of fired weeks where rest > 0 (lock cost) | share where rest < 0 (lock helped) | sum forgone (cost) $k | sum avoided (help) $k | net $k | non-fired weeks mean P&L | mean SizeMult at fire |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 6 | 0.43 | +11.0 | -15.0 | +26.0 | 0.83 | 0.17 | +167 | +11 | -156 | +58.5 | 0.83 |
| L6M | 28 | 11 | 0.39 | +20.2 | -15.1 | +35.3 | 0.82 | 0.18 | +408 | +20 | -388 | +63.2 | 0.73 |
| HOLD | 32 | 14 | 0.44 | +9.4 | -13.4 | +22.8 | 0.71 | 0.29 | +470 | +150 | -320 | +68.4 | 0.68 |
| PRE | 75 | 50 | 0.67 | +6.0 | -15.6 | +21.7 | 0.64 | 0.34 | +1654 | +571 | -1083 | +62.1 | 0.77 |
| X' | 44 | 34 | 0.77 | +6.1 | -14.6 | +20.7 | 0.74 | 0.26 | +886 | +182 | -704 | +22.5 | 0.69 |

Trigger day of week (ET, all 96 fired weeks): Sunday 17, Monday 47, Tuesday 17, Wednesday 9, Thursday 4, Friday 2. Mean open positions flattened 2.4; mean later entries cancelled 61.0. SizeMult of K6 at fire: 1.0: 9, 1.5: 18, 2.0: 0, 0.5: 69 (mean 0.73). Dollar threshold at fire: $14.1k mean.

#### Combined 20R(K6): weeks that trigger and what the rest of the week earned (composite, $k)

| window | weeks | fired | fire rate | week P&L if no lock: fired weeks mean | locked-in week P&L (lock on): fired weeks mean | rest of week after trigger (forgone) mean | share of fired weeks where rest > 0 (lock cost) | share where rest < 0 (lock helped) | sum forgone (cost) $k | sum avoided (help) $k | net $k | non-fired weeks mean P&L | mean SizeMult at fire |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 4 | 0.29 | +4.7 | -35.1 | +39.8 | 1.00 | 0.00 | +159 | -0 | -159 | +51.5 | 0.62 |
| L6M | 28 | 6 | 0.21 | +0.4 | -31.4 | +31.8 | 1.00 | 0.00 | +191 | -0 | -191 | +58.9 | 0.58 |
| HOLD | 32 | 9 | 0.28 | -9.8 | -33.6 | +23.8 | 0.78 | 0.22 | +267 | +53 | -214 | +63.1 | 0.67 |
| PRE | 75 | 29 | 0.39 | -12.9 | -32.7 | +19.8 | 0.59 | 0.38 | +889 | +315 | -574 | +48.5 | 0.60 |
| X' | 44 | 14 | 0.32 | -12.8 | -29.7 | +16.9 | 0.71 | 0.21 | +290 | +53 | -237 | +20.4 | 0.57 |

Trigger day of week (ET, all 50 fired weeks): Sunday 2, Monday 21, Tuesday 13, Wednesday 8, Thursday 5, Friday 1. Mean open positions flattened 1.9; mean later entries cancelled 51.3. SizeMult of K6 at fire: 1.0: 7, 1.5: 2, 2.0: 0, 0.5: 41 (mean 0.61). Dollar threshold at fire: $29.3k mean.

### Q1c. Lag cost: what the entries after the lock would have earned, and a random-time placebo (composite, no-lock world trades; $ real)

First trades after a lock = the first 1 / first 3 entries (across books) after the trigger second; "all later entries" = every entry after the trigger in that week; "open tail" = the P&L the positions open at the trigger earned after the trigger (= total forgone minus later entries). Placebo = the same weeks with the trigger moved to a uniformly random second between the week's first and last entry (200 draws/week), same measure (later entries).

| F | window | fired weeks | mean later-entry count | first trade $ | first 3 trades $ | all later entries $ | open tail $ | total forgone $ | placebo all later entries $ (mean of draws) | actual minus placebo | share of placebo draws with later-entry sum >= actual |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 8 | L3M | 5 | 77.0 | -873 | -911 | +30,770 | -422 | +30,349 | +9,162 | +21,609 | 0.19 |
| 8 | L6M | 11 | 79.5 | +1,003 | +5,074 | +34,990 | +261 | +35,250 | +10,732 | +24,258 | 0.23 |
| 8 | HOLD | 13 | 74.3 | +1,966 | +5,771 | +20,160 | -289 | +19,871 | +2,308 | +17,852 | 0.26 |
| 8 | PRE | 49 | 70.6 | +928 | +2,017 | +23,213 | +739 | +23,952 | +9,182 | +14,031 | 0.38 |
| 8 | X' | 34 | 46.2 | +1,540 | +4,792 | +19,934 | -79 | +19,855 | +7,727 | +12,208 | 0.35 |
| 12 | L3M | 4 | 76.0 | -1,793 | -1,889 | +27,710 | -5,074 | +22,637 | +3,598 | +24,112 | 0.17 |
| 12 | L6M | 8 | 72.6 | -1,341 | -480 | +18,786 | +1,595 | +20,381 | +1,083 | +17,703 | 0.25 |
| 12 | HOLD | 10 | 66.8 | -708 | -335 | +208 | +4,067 | +4,276 | -7,469 | +7,678 | 0.33 |
| 12 | PRE | 35 | 63.5 | -104 | +186 | +17,364 | -537 | +16,826 | +5,086 | +12,277 | 0.39 |
| 12 | X' | 28 | 43.5 | +3,431 | +5,215 | +16,914 | -107 | +16,807 | +3,210 | +13,704 | 0.33 |
| 20 | L3M | 4 | 37.0 | +1,234 | +8,257 | +42,571 | -2,817 | +39,754 | +5,680 | +36,891 | 0.09 |
| 20 | L6M | 6 | 48.3 | +793 | +4,816 | +33,061 | -1,264 | +31,797 | +4,915 | +28,146 | 0.16 |
| 20 | HOLD | 8 | 44.0 | -869 | +1,702 | +15,519 | +1,743 | +17,262 | -7,260 | +22,779 | 0.29 |
| 20 | PRE | 28 | 61.8 | +578 | +3,167 | +24,778 | -1,305 | +23,473 | +6,934 | +17,844 | 0.33 |
| 20 | X' | 14 | 36.8 | +671 | +1,167 | +17,073 | -669 | +16,405 | +4,131 | +12,942 | 0.39 |

### Q3b. Sensitivity of the combined lock to the K6 SizeMult at the time of the lock (SizeMult fixed for the whole run, composite; threshold $ = F x 2,400 x SizeMult)

Cell = effect on the composite vs no combined lock, $k/wk, L3M / L6M / HOLD / PRE / X' (* beyond MDE); fires = weeks fired in L6M / PRE / X'.

| F | $ at SizeMult 0.5 | 1.0 | 1.5 | 2.0 | free running max (default) |
|---|---|---|---|---|---|
| 6R | -35.0 / -45.3* / -38.6* / -19.1* / -13.8 ; fires 23/62/40 | -34.7 / -37.0* / -30.7* / -19.2* / -16.0* ; fires 17/54/36 | -23.7 / -14.7 / -11.9 / -14.3* / -9.4 ; fires 9/46/26 | -14.8 / -8.9 / -7.4 / -12.3 / -5.6 ; fires 7/38/17 | -33.7 / -31.1* / -24.9 / -17.8* / -15.4* ; fires 17/56/37 |
| 8R | -32.2 / -40.2* / -33.0* / -17.8* / -14.9* ; fires 20/60/39 | -22.8 / -14.0 / -11.0 / -18.3* / -15.2* ; fires 9/50/31 | -14.8 / -8.9 / -7.4 / -12.3 / -5.6 ; fires 7/38/17 | -7.3 / -5.9 / -2.9 / -9.3 / -4.3 ; fires 4/28/13 | -11.2 / -13.8 / -10.0 / -14.4 / -16.0* ; fires 11/49/34 |
| 10R | -33.5 / -35.6* / -29.3* / -18.8* / -15.1* ; fires 17/58/38 | -24.6 / -13.5 / -11.0 / -15.7* / -8.7 ; fires 8/46/22 | -6.9 / -5.4 / -2.3 / -9.8 / -4.4 ; fires 4/30/14 | -8.8 / -7.3 / -4.7 / -8.5 / -4.0 ; fires 4/21/10 | -6.3 / -11.7 / -8.6 / -8.6 / -15.7* ; fires 10/40/33 |
| 12R | -34.7 / -37.0* / -30.7* / -19.2* / -16.0* ; fires 17/54/36 | -14.8 / -8.9 / -7.4 / -12.3 / -5.6 ; fires 7/38/17 | -7.9 / -6.6 / -3.8 / -9.4 / -3.0 ; fires 4/26/10 | -6.7 / -3.3 / -1.8 / -5.4 / -1.9 ; fires 1/14/5 | -6.5 / -5.8 / -3.5 / -6.7 / -11.1 ; fires 8/35/28 |
| 15R | -36.6 / -20.9 / -16.9 / -18.2* / -15.8* ; fires 11/52/32 | -6.9 / -5.4 / -2.3 / -9.8 / -4.4 ; fires 4/30/14 | -6.4 / -6.5 / -4.4 / -6.5 / -2.4 ; fires 3/16/6 | +0.0 / +0.0 / +0.2 / -1.2 / -0.0 ; fires 0/8/1 | -7.2 / -4.5 / -2.6 / -7.1 / -10.2 ; fires 6/34/24 |
| 20R | -24.6 / -13.5 / -11.0 / -15.7* / -8.7 ; fires 8/46/22 | -8.8 / -7.3 / -4.7 / -8.5 / -4.0 ; fires 4/21/10 | +0.0 / +0.0 / +0.2 / -1.2 / -0.0 ; fires 0/8/1 | +0.0 / +0.0 / +0.0 / -1.7 / +0.0 ; fires 0/4/0 | -11.4 / -6.8 / -6.7 / -7.7 / -5.4 ; fires 6/28/14 |
| 30R | -6.9 / -5.4 / -2.3 / -9.8 / -4.4 ; fires 4/30/14 | +0.0 / +0.0 / +0.2 / -1.2 / -0.0 ; fires 0/8/1 | +0.0 / +0.0 / +0.0 / +0.2 / +0.0 ; fires 0/1/0 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/0/0 | +0.0 / -1.4 / +0.1 / -9.3 / -2.9 ; fires 1/21/9 |
| 40R | -8.8 / -7.3 / -4.7 / -8.5 / -4.0 ; fires 4/21/10 | +0.0 / +0.0 / +0.0 / -1.7 / +0.0 ; fires 0/4/0 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/0/0 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/0/0 | +0.0 / +0.0 / +0.1 / -9.6 / -1.6 ; fires 0/17/5 |
| 50R | -6.8 / -3.4 / -2.1 / -6.0 / -1.4 ; fires 1/14/3 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/1/0 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/0/0 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/0/0 | +0.0 / +0.0 / +0.1 / -5.0 / +0.3 ; fires 0/9/1 |
| 75R | +0.0 / +0.0 / -0.4 / -1.5 / +0.0 ; fires 0/5/0 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/0/0 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/0/0 | +0.0 / +0.0 / +0.0 / +0.0 / +0.0 ; fires 0/0/0 | +0.0 / +0.0 / -0.4 / +0.5 / +0.0 ; fires 0/2/0 |

Dollar threshold of the combined lock ($k): 8R: 9.6/19.2/28.8/38.4; 12R: 14.4/28.8/43.2/57.6; 20R: 24.0/48.0/72.0/96.0; 30R: 36.0/72.0/108.0/144.0 at SizeMult 0.5/1/1.5/2.

### Q3c. Inert vs protective: risk and fires against the multiple (composite; L6M, PRE, X')

| F | fires L3M/L6M/HOLD/PRE/X' | L6M mean | L6M maxDD | L6M worst-20 mean | PRE mean | PRE maxDD | PRE worst-20 | X' mean | X' maxDD | X' worst-20 | worst week L6M | worst week PRE | worst week X' |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| off | 0/0/0/0/0 | 46.3 | 21 | 22 | 24.7 | 263 | -46 | 9.8 | 126 | -20 | -21 | -121 | -72 |
| 6R | 9/17/19/56/37 | 15.2 | 54 | -7 | 6.9 | 160 | -21 | -5.6 | 291 | -16 | -23 | -23 | -22 |
| 8R | 5/11/13/49/34 | 32.5 | 29 | 6 | 10.3 | 161 | -26 | -6.2 | 309 | -18 | -29 | -30 | -32 |
| 10R | 4/10/12/40/33 | 34.6 | 28 | 9 | 16.2 | 202 | -29 | -5.9 | 298 | -20 | -28 | -38 | -36 |
| 12R | 4/8/10/35/28 | 40.5 | 28 | 14 | 18.0 | 274 | -33 | -1.3 | 214 | -22 | -28 | -44 | -44 |
| 15R | 4/6/8/34/24 | 41.8 | 28 | 16 | 17.6 | 255 | -34 | -0.4 | 234 | -26 | -28 | -55 | -50 |
| 20R | 4/6/8/28/14 | 39.5 | 60 | 13 | 17.1 | 312 | -39 | 4.4 | 117 | -27 | -60 | -72 | -50 |
| 30R | 0/1/3/21/9 | 44.9 | 36 | 20 | 15.4 | 304 | -48 | 6.9 | 172 | -26 | -36 | -92 | -52 |
| 40R | 0/0/1/17/5 | 46.3 | 21 | 22 | 15.2 | 255 | -56 | 8.2 | 173 | -23 | -21 | -92 | -53 |
| 50R | 0/0/1/9/1 | 46.3 | 21 | 22 | 19.7 | 221 | -53 | 10.1 | 126 | -19 | -21 | -92 | -60 |
| 75R | 0/0/1/2/0 | 46.3 | 21 | 22 | 25.2 | 234 | -44 | 9.8 | 126 | -20 | -21 | -92 | -72 |


Reading of the fired weeks (12R): the lock fires at the intra-week trough and the rest of the week is, on average, strongly positive: +20.4k in L6M (8 weeks), +13.9k PRE, +17.4k X'; 75% of the L6M fired weeks and 58-64% of the PRE / X' ones would have recovered; the weeks where the lock helped (rest of week negative) are 25-39% and they avoid much less than the recoveries forgo (L6M 11k avoided vs 174k forgone; PRE 461k vs 963k; X' 122k vs 610k). The placebo (random trigger time in the same weeks, same measure = P&L of the entries after the trigger) averages -7k to +11k per fired week against +0.2k to +43k for the actual trigger, and the actual is larger than the placebo in all 15 F x window rows (by +7.7k to +36.9k): the rest of the week after the trigger is better than the rest of the week after a random time. This is expected for a lock that fires at a trough in a stack with a positive mean, and with 4 to 49 weeks per row it is directional (the share of placebo draws at least as large as the actual is 0.09-0.39, none below 0.09), not significant by itself. The first 1 to 3 trades after the lock are roughly zero (the lag cost is not the first trades but the next day or two): the money is in the later entries, mean 40-80 cancelled entries a week.



## Appendix: all one-parameter sweeps (D6-faithful base with combined 12R, then without), pairs, lock-off placebo, K6 at market

Sections: 1 = combined multiple (the page 1 table with all window metrics); 2 = per-book week floor (off, 8, 10, 12, 15R); 3 = day arm (arm 1.5 / 2 / 2.5 / 3R x keep 25 / 50 / 75% and off); 4a = entry win side (off, +3, +5, +8R); 4b = entry loss side (off, -1, -2, -3R); 5-8 = pairs (combined x floor, combined x arm, floor x arm, win x loss); 9 = lock-off placebo; 10 = K6 at market. Each group has: composite mean; C minus A0; C(s) minus A(s); lock effect on C; lock effect on A; fires per window (c combined weeks, a day-arm book-days, w week-floor book-weeks, h/l entry-test skipped signals); forgone / avoided; composite SD, maxDD, mean worst-20 weeks; as-is maxDD and worst-20. Worst-20 = mean of the 20 worst weeks in the window (all weeks if fewer: L3M has 14), maxDD = on the cumulative weekly series from the window start. Recent-first = the columns are ordered L3M, L6M, HOLD, PRE, X'. Full numbers with MDE: sweep_long.csv.

### 1. Combined week lock multiple (in R of K6; others = D6 defaults: entry +5R/-2R, arm 2R keep 50%, floor 12R)

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 38.1 | 46.3 | 42.6 | 24.7 | 9.8 |
| 6R | 4.4 | 15.2 | 17.7 | 6.9 | -5.6 |
| 8R | 27.0 | 32.5 | 32.6 | 10.3 | -6.2 |
| 10R | 31.8 | 34.6 | 34.0 | 16.2 | -5.9 |
| 12R | 31.7 | 40.5 | 39.1 | 18.0 | -1.3 |
| 15R | 30.9 | 41.8 | 40.0 | 17.6 | -0.4 |
| 20R | 26.8 | 39.5 | 35.9 | 17.1 | 4.4 |
| 30R | 38.1 | 44.9 | 42.6 | 15.4 | 6.9 |
| 40R | 38.1 | 46.3 | 42.7 | 15.2 | 8.2 |
| 50R | 38.1 | 46.3 | 42.7 | 19.7 | 10.1 |
| 75R | 38.1 | 46.3 | 42.1 | 25.2 | 9.8 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| 6R | -9.4 | -8.8 | -6.0 | -10.8 | -2.0 |
| 8R | +13.2 | +8.5 | +8.9 | -7.4 | -2.6 |
| 10R | +18.0 | +10.6 | +10.3 | -1.5 | -2.3 |
| 12R | +17.9 | +16.5 | +15.3 | +0.3 | +2.3 |
| 15R | +17.1 | +17.8 | +16.3 | -0.1 | +3.2 |
| 20R | +13.0 | +15.5 | +12.2 | -0.6 | +8.0 |
| 30R | +24.3* | +20.9* | +18.9* | -2.3 | +10.5 |
| 40R | +24.3* | +22.3* | +19.0* | -2.5 | +11.7 |
| 50R | +24.3* | +22.3* | +19.0* | +2.0 | +13.6 |
| 75R | +24.3* | +22.3* | +18.4* | +7.5 | +13.4 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| 6R | +6.7 | +9.6 | +10.1 | +4.9 | +2.7 |
| 8R | +28.4 | +22.9 | +22.1 | +6.0 | +4.8 |
| 10R | +24.0* | +20.2 | +19.9 | +7.6 | +3.1 |
| 12R | +25.5* | +27.8* | +23.4* | +8.1 | +8.0 |
| 15R | +22.3* | +27.7* | +23.8* | +8.3 | +10.6 |
| 20R | +9.9 | +18.5 | +14.0 | +4.1 | +12.8 |
| 30R | +22.9* | +20.2* | +18.1* | +0.1 | +10.5 |
| 40R | +24.3* | +22.3* | +19.0* | -1.8 | +12.3 |
| 50R | +24.3* | +22.3* | +19.0* | +2.4 | +13.6 |
| 75R | +24.3* | +22.3* | +18.4* | +7.5 | +13.4 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 6R | -33.7 | -31.1* | -24.9 | -17.8* | -15.4* |
| 8R | -11.2 | -13.8 | -10.0 | -14.4 | -16.0* |
| 10R | -6.3 | -11.7 | -8.6 | -8.6 | -15.7* |
| 12R | -6.5 | -5.8 | -3.5 | -6.7 | -11.1 |
| 15R | -7.2 | -4.5 | -2.6 | -7.1 | -10.2 |
| 20R | -11.4 | -6.8 | -6.7 | -7.7 | -5.4 |
| 30R | +0.0 | -1.4 | +0.1 | -9.3 | -2.9 |
| 40R | +0.0 | +0.0 | +0.1 | -9.6 | -1.6 |
| 50R | +0.0 | +0.0 | +0.1 | -5.0 | +0.3 |
| 75R | +0.0 | +0.0 | -0.4 | +0.5 | +0.0 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 6R | -16.1 | -18.4* | -16.1 | -15.7* | -4.7 |
| 8R | -15.2 | -14.4 | -13.2 | -13.4* | -7.5 |
| 10R | -6.0 | -9.6 | -9.6 | -9.1 | -5.4 |
| 12R | -7.6 | -11.3 | -8.1 | -7.8 | -5.7 |
| 15R | -5.2 | -9.9 | -7.6 | -8.4 | -7.4 |
| 20R | +3.1 | -3.0 | -1.9 | -4.7 | -4.8 |
| 30R | +1.4 | +0.7 | +0.8 | -2.4 | -0.0 |
| 40R | +0.0 | +0.0 | +0.0 | -0.7 | -0.6 |
| 50R | +0.0 | +0.0 | +0.0 | -0.4 | +0.0 |
| 75R | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 0c 84a 4w 21h 212l | 0c 127a 6w 27h 295l | 0c 137a 9w 28h 330l | 0c 241a 22w 128h 899l | 0c 73a 6w 1h 156l |
| 6R | 9c 85a 3w 26h 220l | 17c 126a 5w 33h 315l | 19c 135a 7w 34h 357l | 56c 239a 22w 139h 991l | 37c 74a 6w 1h 183l |
| 8R | 5c 84a 4w 26h 219l | 11c 127a 6w 33h 307l | 13c 136a 8w 34h 349l | 49c 240a 22w 140h 967l | 34c 74a 6w 1h 181l |
| 10R | 4c 84a 4w 26h 218l | 10c 127a 6w 33h 306l | 12c 136a 8w 34h 348l | 40c 242a 22w 140h 946l | 33c 73a 6w 1h 178l |
| 12R | 4c 84a 4w 21h 217l | 8c 127a 6w 27h 305l | 10c 137a 8w 28h 343l | 35c 242a 22w 140h 939l | 28c 73a 6w 1h 170l |
| 15R | 4c 84a 4w 21h 217l | 6c 127a 6w 27h 300l | 8c 137a 8w 28h 338l | 34c 242a 22w 140h 936l | 24c 73a 6w 1h 167l |
| 20R | 4c 84a 4w 21h 213l | 6c 127a 6w 27h 296l | 8c 137a 9w 28h 332l | 28c 241a 21w 140h 921l | 14c 73a 6w 1h 162l |
| 30R | 0c 84a 4w 21h 212l | 1c 127a 6w 27h 295l | 3c 137a 9w 28h 330l | 21c 241a 21w 128h 912l | 9c 73a 6w 1h 159l |
| 40R | 0c 84a 4w 21h 212l | 0c 127a 6w 27h 295l | 1c 137a 9w 28h 330l | 17c 240a 21w 128h 910l | 5c 73a 6w 1h 158l |
| 50R | 0c 84a 4w 21h 212l | 0c 127a 6w 27h 295l | 1c 137a 9w 28h 330l | 9c 242a 21w 128h 900l | 1c 73a 6w 1h 156l |
| 75R | 0c 84a 4w 21h 212l | 0c 127a 6w 27h 295l | 1c 137a 9w 28h 330l | 2c 241a 21w 128h 900l | 0c 73a 6w 1h 156l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| 6R | 34.7/0.9 | 32.0/0.9 | 29.9/5.0 | 26.6/8.8 | 20.2/4.8 |
| 8R | 11.9/0.8 | 14.6/0.7 | 14.7/4.7 | 22.1/7.6 | 20.1/4.1 |
| 10R | 6.9/0.6 | 12.3/0.6 | 13.0/4.4 | 15.3/6.8 | 19.3/3.6 |
| 12R | 6.9/0.4 | 6.2/0.4 | 7.6/4.1 | 12.8/6.1 | 13.9/2.8 |
| 15R | 7.4/0.1 | 4.6/0.1 | 6.2/3.6 | 12.8/5.7 | 12.4/2.2 |
| 20R | 11.4/0.0 | 6.8/0.0 | 8.3/1.6 | 11.9/4.2 | 6.6/1.2 |
| 30R | -0.0/0.0 | 1.4/0.0 | 1.2/1.3 | 11.6/2.3 | 3.8/0.9 |
| 40R | -0.0/0.0 | -0.0/0.0 | -0.0/0.1 | 11.1/1.5 | 2.2/0.5 |
| 50R | -0.0/0.0 | -0.0/0.0 | -0.0/0.1 | 5.7/0.7 | -0.0/0.3 |
| 75R | -0.0/0.0 | -0.0/0.0 | 0.4/0.0 | -0.0/0.5 | -0.0/0.0 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 46.9 | 45.4 | 55.5 | 58.1 | 34.0 |
| 6R | 33.0 | 40.7 | 45.5 | 38.2 | 18.0 |
| 8R | 53.2 | 50.4 | 53.1 | 44.6 | 19.8 |
| 10R | 51.0 | 49.4 | 52.6 | 50.6 | 23.0 |
| 12R | 51.3 | 50.7 | 53.9 | 52.6 | 28.7 |
| 15R | 52.1 | 49.8 | 53.4 | 53.4 | 31.1 |
| 20R | 57.2 | 53.2 | 59.0 | 55.6 | 34.4 |
| 30R | 46.9 | 47.3 | 54.4 | 58.4 | 35.8 |
| 40R | 46.9 | 45.4 | 55.2 | 59.9 | 35.5 |
| 50R | 46.9 | 45.4 | 55.2 | 58.9 | 33.4 |
| 75R | 46.9 | 45.4 | 56.5 | 56.9 | 34.0 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 20.6 | 20.6 | 113.4 | 262.7 | 125.7 |
| 6R | 54.4 | 54.4 | 54.4 | 160.2 | 291.0 |
| 8R | 29.2 | 29.2 | 29.2 | 161.5 | 309.1 |
| 10R | 28.2 | 28.2 | 28.2 | 202.2 | 298.4 |
| 12R | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |
| 15R | 28.1 | 28.1 | 28.4 | 255.0 | 234.1 |
| 20R | 60.1 | 60.1 | 77.5 | 311.9 | 117.5 |
| 30R | 20.6 | 36.0 | 72.2 | 304.5 | 171.7 |
| 40R | 20.6 | 20.6 | 109.4 | 255.0 | 172.5 |
| 50R | 20.6 | 20.6 | 109.4 | 220.8 | 125.7 |
| 75R | 20.6 | 20.6 | 127.8 | 233.7 | 125.7 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 38.1 | 22.0 | 9.0 | -45.6 | -19.8 |
| 6R | 4.4 | -7.5 | -10.7 | -21.0 | -15.6 |
| 8R | 27.0 | 5.7 | -3.0 | -25.6 | -18.0 |
| 10R | 31.8 | 8.7 | -0.7 | -29.0 | -19.7 |
| 12R | 31.7 | 13.9 | 3.7 | -32.9 | -21.7 |
| 15R | 30.9 | 15.7 | 5.1 | -34.2 | -25.9 |
| 20R | 26.8 | 12.5 | -1.4 | -39.2 | -26.7 |
| 30R | 38.1 | 20.1 | 9.1 | -48.1 | -25.6 |
| 40R | 38.1 | 22.0 | 9.2 | -55.6 | -23.4 |
| 50R | 38.1 | 22.0 | 9.2 | -53.5 | -19.3 |
| 75R | 38.1 | 22.0 | 8.3 | -43.7 | -19.8 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |
| 6R | 117.4 | 117.4 | 117.4 | 337.4 | 406.2 |
| 8R | 117.9 | 117.9 | 117.9 | 465.0 | 511.7 |
| 10R | 94.9 | 97.5 | 97.5 | 285.1 | 518.1 |
| 12R | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |
| 15R | 72.4 | 111.5 | 111.5 | 309.4 | 592.1 |
| 20R | 48.2 | 97.2 | 119.6 | 288.4 | 465.7 |
| 30R | 72.1 | 72.1 | 137.1 | 203.5 | 318.3 |
| 40R | 91.8 | 91.8 | 143.7 | 206.7 | 342.6 |
| 50R | 91.8 | 91.8 | 143.7 | 237.1 | 317.2 |
| 75R | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |
| 6R | -2.2 | -14.7 | -14.8 | -15.2 | -14.9 |
| 8R | -1.4 | -14.3 | -19.5 | -19.9 | -19.7 |
| 10R | 7.8 | -10.1 | -20.5 | -24.9 | -24.6 |
| 12R | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |
| 15R | 8.6 | -10.5 | -20.9 | -36.4 | -36.3 |
| 20R | 16.9 | -0.8 | -11.9 | -48.5 | -38.9 |
| 30R | 15.2 | 4.4 | -7.6 | -49.6 | -29.5 |
| 40R | 13.8 | 3.4 | -8.9 | -46.4 | -30.7 |
| 50R | 13.8 | 3.4 | -8.9 | -45.1 | -29.4 |
| 75R | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |

### 2. Per-book week floor, with combined 12R(K6) [D6-faithful]

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 31.4 | 40.7 | 39.2 | 17.9 | -1.3 |
| 8R | 31.5 | 40.3 | 38.9 | 18.6 | -0.8 |
| 10R | 31.7 | 40.6 | 39.1 | 18.2 | -1.3 |
| 12R | 31.7 | 40.5 | 39.1 | 18.0 | -1.3 |
| 15R | 31.4 | 40.6 | 39.2 | 17.9 | -1.3 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +17.6 | +16.6 | +15.5 | +0.2 | +2.3 |
| 8R | +17.7 | +16.3 | +15.2 | +0.9 | +2.7 |
| 10R | +17.9 | +16.6 | +15.4 | +0.5 | +2.3 |
| 12R | +17.9 | +16.5 | +15.3 | +0.3 | +2.3 |
| 15R | +17.6 | +16.6 | +15.4 | +0.2 | +2.3 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +25.2* | +27.9* | +23.6* | +8.0 | +8.0 |
| 8R | +25.3* | +27.6* | +23.3* | +8.9 | +8.5 |
| 10R | +25.5* | +27.9* | +23.5* | +8.3 | +8.0 |
| 12R | +25.5* | +27.8* | +23.4* | +8.1 | +8.0 |
| 15R | +25.2* | +27.9* | +23.5* | +8.0 | +8.0 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 8R | +0.1 | -0.3 | -0.3 | +0.7 | +0.5 |
| 10R | +0.3 | -0.1 | -0.1 | +0.3 | +0.0 |
| 12R | +0.3 | -0.2 | -0.1 | +0.1 | +0.0 |
| 15R | +0.0 | -0.0 | -0.0 | +0.0 | +0.0 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 8R | +0.0 | +0.0 | +0.0 | -0.2 | +0.0 |
| 10R | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 12R | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 15R | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 4c 84a 0w 21h 217l | 8c 127a 0w 27h 305l | 10c 137a 0w 28h 343l | 35c 242a 0w 140h 935l | 28c 73a 0w 1h 170l |
| 8R | 4c 84a 7w 21h 217l | 8c 127a 12w 27h 305l | 10c 137a 17w 28h 343l | 35c 242a 56w 140h 939l | 27c 73a 20w 1h 171l |
| 10R | 4c 84a 5w 21h 217l | 8c 127a 9w 27h 305l | 10c 137a 11w 28h 343l | 35c 242a 35w 140h 939l | 28c 73a 13w 1h 170l |
| 12R | 4c 84a 4w 21h 217l | 8c 127a 6w 27h 305l | 10c 137a 8w 28h 343l | 35c 242a 22w 140h 939l | 28c 73a 6w 1h 170l |
| 15R | 4c 84a 0w 21h 217l | 8c 127a 1w 27h 305l | 10c 137a 1w 28h 343l | 35c 242a 10w 140h 935l | 28c 73a 3w 1h 170l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| 8R | -0.0/0.1 | 0.4/0.1 | 0.4/0.1 | 0.3/0.9 | 0.2/0.6 |
| 10R | -0.0/0.3 | 0.3/0.2 | 0.2/0.2 | 0.1/0.4 | -0.0/0.0 |
| 12R | -0.0/0.3 | 0.3/0.1 | 0.3/0.1 | 0.1/0.2 | -0.0/0.0 |
| 15R | -0.0/0.0 | 0.0/0.0 | 0.0/0.0 | -0.0/0.0 | -0.0/0.0 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 51.4 | 50.9 | 54.1 | 52.7 | 28.7 |
| 8R | 51.4 | 50.8 | 53.9 | 52.2 | 28.6 |
| 10R | 51.3 | 50.8 | 53.9 | 52.5 | 28.7 |
| 12R | 51.3 | 50.7 | 53.9 | 52.6 | 28.7 |
| 15R | 51.4 | 50.9 | 54.1 | 52.7 | 28.7 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |
| 8R | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |
| 10R | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |
| 12R | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |
| 15R | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 31.4 | 14.1 | 3.5 | -32.9 | -21.7 |
| 8R | 31.5 | 13.7 | 3.6 | -31.7 | -21.7 |
| 10R | 31.7 | 14.0 | 3.7 | -32.9 | -21.7 |
| 12R | 31.7 | 13.9 | 3.7 | -32.9 | -21.7 |
| 15R | 31.4 | 14.1 | 3.5 | -32.9 | -21.7 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |
| 8R | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |
| 10R | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |
| 12R | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |
| 15R | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |
| 8R | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |
| 10R | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |
| 12R | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |
| 15R | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |

### 3. Day arm (arm R x keep), with combined 12R(K6) [D6-faithful]

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 28.0 | 33.7 | 33.6 | 14.4 | -2.9 |
| arm 1.5R keep 25% | 27.1 | 38.5 | 36.8 | 13.3 | -2.2 |
| arm 1.5R keep 50% | 21.9 | 35.2 | 33.9 | 14.6 | 0.8 |
| arm 1.5R keep 75% | 14.4 | 26.2 | 28.0 | 11.6 | 3.2 |
| arm 2R keep 25% | 34.2 | 36.7 | 35.7 | 18.5 | -2.4 |
| arm 2R keep 50% | 31.7 | 40.5 | 39.1 | 18.0 | -1.3 |
| arm 2R keep 75% | 29.8 | 35.1 | 34.5 | 14.2 | -1.1 |
| arm 2.5R keep 25% | 24.4 | 31.7 | 31.8 | 12.8 | -2.5 |
| arm 2.5R keep 50% | 19.4 | 29.0 | 29.3 | 13.9 | -0.7 |
| arm 2.5R keep 75% | 25.7 | 29.9 | 30.1 | 12.4 | -0.7 |
| arm 3R keep 25% | 28.0 | 33.7 | 33.6 | 14.5 | -2.9 |
| arm 3R keep 50% | 20.7 | 30.0 | 30.2 | 14.5 | -2.8 |
| arm 3R keep 75% | 26.9 | 34.0 | 33.8 | 13.9 | -1.3 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | +14.2 | +9.7 | +9.9 | -3.3 | +0.7 |
| arm 1.5R keep 25% | +13.3 | +14.5 | +13.1 | -4.4 | +1.3 |
| arm 1.5R keep 50% | +8.1 | +11.2 | +10.2 | -3.1 | +4.3 |
| arm 1.5R keep 75% | +0.6 | +2.2 | +4.3 | -6.1 | +6.8 |
| arm 2R keep 25% | +20.3 | +12.7 | +12.0 | +0.8 | +1.2 |
| arm 2R keep 50% | +17.9 | +16.5 | +15.3 | +0.3 | +2.3 |
| arm 2R keep 75% | +16.0 | +11.1 | +10.7 | -3.5 | +2.5 |
| arm 2.5R keep 25% | +10.6 | +7.7 | +8.1 | -5.0 | +1.1 |
| arm 2.5R keep 50% | +5.6 | +5.0 | +5.6 | -3.8 | +2.8 |
| arm 2.5R keep 75% | +11.9 | +5.9 | +6.4 | -5.3 | +2.9 |
| arm 3R keep 25% | +14.2 | +9.7 | +9.8 | -3.2 | +0.6 |
| arm 3R keep 50% | +6.9 | +5.9 | +6.4 | -3.2 | +0.8 |
| arm 3R keep 75% | +13.0 | +10.0 | +10.0 | -3.8 | +2.2 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | +13.4 | +19.2 | +15.8 | +6.4 | +5.2 |
| arm 1.5R keep 25% | +17.5 | +22.8 | +18.9 | +3.0 | +5.6 |
| arm 1.5R keep 50% | +14.7 | +19.9 | +16.2 | +4.9 | +5.9 |
| arm 1.5R keep 75% | +14.6 | +15.1 | +16.0 | +5.7 | +5.6 |
| arm 2R keep 25% | +24.4 | +24.2 | +19.9 | +8.7 | +6.2 |
| arm 2R keep 50% | +25.5* | +27.8* | +23.4* | +8.1 | +8.0 |
| arm 2R keep 75% | +30.5* | +24.9* | +22.3 | +8.6 | +6.3 |
| arm 2.5R keep 25% | +13.0 | +18.7 | +15.3 | +4.7 | +6.5 |
| arm 2.5R keep 50% | +9.1 | +15.3 | +12.2 | +6.9 | +7.4 |
| arm 2.5R keep 75% | +17.6 | +18.1 | +15.6 | +10.3 | +7.0 |
| arm 3R keep 25% | +14.7 | +20.3 | +16.7 | +6.0 | +5.1 |
| arm 3R keep 50% | +9.6 | +17.2 | +13.9 | +6.0 | +5.0 |
| arm 3R keep 75% | +17.5 | +23.4 | +19.6 | +8.5 | +6.1 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| arm 1.5R keep 25% | -0.9 | +4.8 | +3.2 | -1.1 | +0.7 |
| arm 1.5R keep 50% | -6.1 | +1.5 | +0.3 | +0.2 | +3.7 |
| arm 1.5R keep 75% | -13.6 | -7.5 | -5.6 | -2.9 | +6.1 |
| arm 2R keep 25% | +6.1 | +3.0 | +2.1 | +4.1 | +0.5 |
| arm 2R keep 50% | +3.6 | +6.8 | +5.4 | +3.6 | +1.6 |
| arm 2R keep 75% | +1.8 | +1.4 | +0.8 | -0.2 | +1.8 |
| arm 2.5R keep 25% | -3.6 | -2.0 | -1.8 | -1.7 | +0.4 |
| arm 2.5R keep 50% | -8.6 | -4.7 | -4.3 | -0.5 | +2.2 |
| arm 2.5R keep 75% | -2.3 | -3.8 | -3.6 | -2.0 | +2.2 |
| arm 3R keep 25% | -0.0 | +0.0 | -0.1 | +0.1 | -0.0 |
| arm 3R keep 50% | -7.4 | -3.8 | -3.5 | +0.1 | +0.1 |
| arm 3R keep 75% | -1.2 | +0.3 | +0.1 | -0.5 | +1.6 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| arm 1.5R keep 25% | -5.0 | +1.2 | +0.1 | +2.3 | +0.3 |
| arm 1.5R keep 50% | -7.4 | +0.8 | -0.0 | +1.7 | +3.0 |
| arm 1.5R keep 75% | -14.8 | -3.5 | -5.8 | -2.1 | +5.7 |
| arm 2R keep 25% | -4.8 | -2.0 | -2.0 | +1.7 | -0.5 |
| arm 2R keep 50% | -8.4 | -1.8 | -2.2 | +1.9 | -1.2 |
| arm 2R keep 75% | -15.3 | -4.3 | -5.6 | -2.4 | +0.7 |
| arm 2.5R keep 25% | -3.2 | -1.5 | -1.3 | +0.1 | -0.8 |
| arm 2.5R keep 50% | -4.2 | -0.8 | -0.7 | -1.1 | +0.0 |
| arm 2.5R keep 75% | -6.5 | -2.8 | -3.3 | -5.9 | +0.4 |
| arm 3R keep 25% | -1.2 | -1.1 | -1.0 | +0.5 | +0.0 |
| arm 3R keep 50% | -3.5 | -1.8 | -1.6 | +0.5 | +0.3 |
| arm 3R keep 75% | -5.2 | -3.9 | -3.6 | -2.6 | +0.7 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 6c 0a 3w 26h 219l | 11c 0a 5w 33h 307l | 13c 0a 7w 34h 345l | 38c 0a 25w 140h 933l | 29c 0a 7w 1h 170l |
| arm 1.5R keep 25% | 5c 85a 2w 21h 225l | 9c 146a 4w 27h 315l | 11c 156a 5w 28h 353l | 38c 332a 18w 141h 948l | 29c 126a 5w 1h 170l |
| arm 1.5R keep 50% | 5c 123a 2w 21h 225l | 9c 210a 4w 27h 315l | 11c 230a 5w 28h 353l | 36c 462a 17w 142h 946l | 25c 185a 4w 1h 168l |
| arm 1.5R keep 75% | 4c 157a 0w 22h 226l | 9c 285a 2w 29h 316l | 11c 317a 3w 30h 354l | 35c 655a 18w 142h 948l | 25c 254a 5w 1h 168l |
| arm 2R keep 25% | 5c 50a 2w 26h 219l | 10c 75a 4w 33h 307l | 12c 79a 6w 34h 345l | 35c 153a 23w 140h 936l | 29c 33a 6w 1h 170l |
| arm 2R keep 50% | 4c 84a 4w 21h 217l | 8c 127a 6w 27h 305l | 10c 137a 8w 28h 343l | 35c 242a 22w 140h 939l | 28c 73a 6w 1h 170l |
| arm 2R keep 75% | 4c 112a 1w 22h 217l | 9c 190a 3w 28h 305l | 11c 208a 5w 29h 343l | 36c 400a 21w 142h 941l | 28c 123a 7w 1h 170l |
| arm 2.5R keep 25% | 7c 24a 2w 26h 219l | 12c 36a 4w 33h 307l | 14c 38a 6w 34h 345l | 39c 66a 25w 140h 934l | 29c 19a 6w 1h 170l |
| arm 2.5R keep 50% | 6c 53a 2w 26h 218l | 11c 76a 4w 33h 306l | 13c 82a 6w 34h 344l | 38c 123a 24w 140h 935l | 28c 36a 6w 1h 170l |
| arm 2.5R keep 75% | 5c 77a 1w 26h 218l | 11c 127a 3w 33h 306l | 13c 139a 5w 34h 344l | 37c 252a 24w 142h 935l | 28c 66a 6w 1h 170l |
| arm 3R keep 25% | 6c 14a 2w 26h 219l | 11c 19a 4w 33h 307l | 13c 21a 6w 34h 345l | 38c 30a 24w 140h 933l | 29c 8a 7w 1h 170l |
| arm 3R keep 50% | 7c 32a 2w 26h 219l | 12c 44a 4w 33h 307l | 14c 48a 6w 34h 345l | 38c 63a 24w 140h 934l | 29c 17a 7w 1h 170l |
| arm 3R keep 75% | 6c 56a 2w 26h 219l | 11c 84a 4w 33h 307l | 13c 91a 6w 34h 345l | 37c 155a 24w 142h 939l | 28c 33a 7w 1h 170l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| arm 1.5R keep 25% | 8.5/7.6 | 5.6/10.4 | 5.9/9.1 | 7.3/6.2 | 1.7/2.3 |
| arm 1.5R keep 50% | 15.2/9.1 | 10.1/11.6 | 9.8/10.1 | 7.3/7.5 | 1.2/4.8 |
| arm 1.5R keep 75% | 24.9/11.3 | 17.9/10.4 | 16.9/11.3 | 11.5/8.6 | 1.0/7.1 |
| arm 2R keep 25% | 0.3/6.4 | 0.8/3.8 | 1.3/3.4 | 1.2/5.3 | 0.2/0.7 |
| arm 2R keep 50% | 5.4/9.1 | 3.6/10.4 | 3.6/9.0 | 3.5/7.1 | 1.0/2.6 |
| arm 2R keep 75% | 8.7/10.5 | 8.1/9.4 | 7.3/8.2 | 8.5/8.3 | 1.0/2.8 |
| arm 2.5R keep 25% | 4.9/1.2 | 2.7/0.8 | 2.5/0.7 | 2.2/0.5 | 0.2/0.6 |
| arm 2.5R keep 50% | 10.3/1.7 | 6.1/1.4 | 5.5/1.2 | 1.7/1.2 | 0.2/2.3 |
| arm 2.5R keep 75% | 7.6/5.2 | 7.3/3.4 | 6.6/3.0 | 4.9/2.9 | 0.1/2.3 |
| arm 3R keep 25% | 0.3/0.3 | 0.2/0.2 | 0.2/0.2 | 0.2/0.3 | 0.1/0.1 |
| arm 3R keep 50% | 7.6/0.3 | 4.3/0.6 | 4.0/0.5 | 0.5/0.6 | 0.1/0.2 |
| arm 3R keep 75% | 4.3/3.1 | 2.7/2.9 | 2.5/2.6 | 2.9/2.4 | 0.1/1.7 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 59.6 | 53.6 | 56.6 | 54.5 | 29.4 |
| arm 1.5R keep 25% | 59.3 | 54.6 | 56.7 | 50.1 | 28.9 |
| arm 1.5R keep 50% | 45.2 | 49.0 | 53.2 | 47.1 | 28.7 |
| arm 1.5R keep 75% | 28.8 | 40.1 | 45.1 | 45.9 | 30.9 |
| arm 2R keep 25% | 56.9 | 51.5 | 53.8 | 55.5 | 29.0 |
| arm 2R keep 50% | 51.3 | 50.7 | 53.9 | 52.6 | 28.7 |
| arm 2R keep 75% | 47.1 | 46.5 | 50.7 | 47.9 | 29.6 |
| arm 2.5R keep 25% | 59.9 | 54.0 | 56.6 | 53.3 | 28.9 |
| arm 2.5R keep 50% | 55.5 | 51.6 | 55.5 | 53.5 | 30.1 |
| arm 2.5R keep 75% | 51.0 | 49.1 | 53.9 | 48.6 | 31.0 |
| arm 3R keep 25% | 59.8 | 53.7 | 56.8 | 54.4 | 29.2 |
| arm 3R keep 50% | 59.2 | 53.4 | 56.9 | 54.2 | 29.4 |
| arm 3R keep 75% | 57.9 | 52.4 | 57.2 | 50.6 | 30.4 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 62.5 | 62.5 | 62.5 | 228.5 | 213.8 |
| arm 1.5R keep 25% | 47.1 | 43.3 | 43.3 | 227.0 | 202.3 |
| arm 1.5R keep 50% | 26.2 | 26.2 | 36.5 | 263.3 | 196.4 |
| arm 1.5R keep 75% | 28.8 | 51.1 | 51.1 | 204.3 | 196.1 |
| arm 2R keep 25% | 29.6 | 29.6 | 29.6 | 225.7 | 213.8 |
| arm 2R keep 50% | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |
| arm 2R keep 75% | 23.8 | 36.8 | 36.8 | 202.4 | 213.3 |
| arm 2.5R keep 25% | 54.1 | 54.1 | 54.1 | 230.0 | 213.8 |
| arm 2.5R keep 50% | 49.3 | 59.3 | 59.3 | 226.0 | 213.8 |
| arm 2.5R keep 75% | 24.7 | 36.8 | 36.8 | 210.4 | 213.7 |
| arm 3R keep 25% | 62.5 | 62.5 | 62.5 | 227.9 | 213.8 |
| arm 3R keep 50% | 67.6 | 82.6 | 82.6 | 229.0 | 213.8 |
| arm 3R keep 75% | 67.6 | 67.6 | 67.6 | 214.9 | 213.8 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 28.0 | 5.8 | -3.1 | -37.1 | -23.1 |
| arm 1.5R keep 25% | 27.1 | 10.1 | -1.3 | -33.6 | -21.9 |
| arm 1.5R keep 50% | 21.9 | 10.4 | -0.0 | -30.8 | -21.4 |
| arm 1.5R keep 75% | 14.4 | 6.0 | -0.7 | -32.6 | -21.9 |
| arm 2R keep 25% | 34.2 | 10.2 | 1.0 | -35.2 | -22.0 |
| arm 2R keep 50% | 31.7 | 13.9 | 3.7 | -32.9 | -21.7 |
| arm 2R keep 75% | 29.8 | 12.5 | 2.7 | -31.5 | -22.4 |
| arm 2.5R keep 25% | 24.4 | 3.0 | -5.9 | -36.6 | -22.0 |
| arm 2.5R keep 50% | 19.4 | 1.1 | -7.6 | -36.2 | -21.9 |
| arm 2.5R keep 75% | 25.7 | 4.1 | -5.0 | -34.4 | -22.8 |
| arm 3R keep 25% | 28.0 | 5.7 | -3.3 | -36.8 | -23.1 |
| arm 3R keep 50% | 20.7 | 1.5 | -7.9 | -36.3 | -23.1 |
| arm 3R keep 75% | 26.9 | 7.6 | -3.7 | -34.6 | -23.1 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 103.2 | 115.6 | 115.6 | 252.8 | 463.1 |
| arm 1.5R keep 25% | 116.2 | 116.7 | 116.7 | 224.3 | 458.6 |
| arm 1.5R keep 50% | 77.0 | 117.6 | 117.6 | 208.6 | 356.8 |
| arm 1.5R keep 75% | 82.8 | 86.9 | 86.9 | 322.0 | 265.8 |
| arm 2R keep 25% | 115.8 | 115.8 | 115.8 | 255.3 | 485.7 |
| arm 2R keep 50% | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |
| arm 2R keep 75% | 149.8 | 149.8 | 149.8 | 387.3 | 456.3 |
| arm 2.5R keep 25% | 116.4 | 116.4 | 116.4 | 238.5 | 498.3 |
| arm 2.5R keep 50% | 110.9 | 115.6 | 115.6 | 282.5 | 465.0 |
| arm 2.5R keep 75% | 90.6 | 116.0 | 116.0 | 394.1 | 445.5 |
| arm 3R keep 25% | 106.7 | 115.6 | 115.6 | 236.0 | 461.4 |
| arm 3R keep 50% | 100.5 | 115.6 | 115.6 | 253.9 | 455.8 |
| arm 3R keep 75% | 87.6 | 115.6 | 115.6 | 341.5 | 445.0 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 14.6 | -15.4 | -24.6 | -29.3 | -29.3 |
| arm 1.5R keep 25% | 9.6 | -10.5 | -19.8 | -29.5 | -29.2 |
| arm 1.5R keep 50% | 7.2 | -6.4 | -15.9 | -29.3 | -28.5 |
| arm 1.5R keep 75% | -0.2 | -9.5 | -18.9 | -29.2 | -28.2 |
| arm 2R keep 25% | 9.7 | -14.8 | -23.9 | -29.3 | -29.3 |
| arm 2R keep 50% | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |
| arm 2R keep 75% | -0.7 | -11.8 | -20.3 | -29.3 | -29.2 |
| arm 2.5R keep 25% | 11.4 | -15.1 | -23.7 | -29.3 | -29.3 |
| arm 2.5R keep 50% | 10.3 | -14.7 | -22.3 | -29.4 | -29.3 |
| arm 2.5R keep 75% | 8.1 | -12.4 | -20.3 | -29.4 | -29.2 |
| arm 3R keep 25% | 13.3 | -16.2 | -25.0 | -29.3 | -29.2 |
| arm 3R keep 50% | 11.1 | -16.7 | -24.4 | -29.3 | -29.3 |
| arm 3R keep 75% | 9.3 | -14.9 | -22.9 | -29.4 | -29.2 |

### 4a. Day entry test, win side (+R), with combined 12R(K6) [D6-faithful]

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 31.9 | 40.4 | 38.9 | 17.9 | -1.3 |
| 3R win | 32.8 | 41.2 | 39.7 | 16.8 | -1.3 |
| 5R win | 31.7 | 40.5 | 39.1 | 18.0 | -1.3 |
| 8R win | 31.9 | 40.4 | 38.9 | 17.9 | -1.3 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +18.1 | +16.4 | +15.2 | +0.2 | +2.3 |
| 3R win | +19.0 | +17.2 | +15.9 | -0.9 | +2.3 |
| 5R win | +17.9 | +16.5 | +15.3 | +0.3 | +2.3 |
| 8R win | +18.1 | +16.4 | +15.2 | +0.2 | +2.3 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +26.5* | +28.0* | +23.6* | +8.0 | +8.0 |
| 3R win | +28.0* | +29.4* | +24.7* | +8.4 | +7.9 |
| 5R win | +25.5* | +27.8* | +23.4* | +8.1 | +8.0 |
| 8R win | +26.3* | +27.9* | +23.5* | +8.0 | +8.0 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 3R win | +1.0 | +0.9 | +0.7 | -1.1 | -0.0 |
| 5R win | -0.2 | +0.1 | +0.1 | +0.1 | +0.0 |
| 8R win | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 3R win | -0.6 | -0.6 | -0.4 | -1.6 | +0.1 |
| 5R win | +0.8 | +0.3 | +0.3 | -0.0 | +0.0 |
| 8R win | +0.2 | +0.1 | +0.1 | +0.0 | +0.0 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 4c 84a 4w 0h 216l | 8c 127a 6w 0h 304l | 10c 137a 8w 0h 342l | 35c 248a 22w 0h 939l | 28c 73a 6w 0h 170l |
| 3R win | 4c 78a 4w 131h 216l | 8c 118a 6w 206h 304l | 10c 128a 8w 214h 342l | 36c 226a 22w 542h 939l | 28c 70a 6w 36h 170l |
| 5R win | 4c 84a 4w 21h 217l | 8c 127a 6w 27h 305l | 10c 137a 8w 28h 343l | 35c 242a 22w 140h 939l | 28c 73a 6w 1h 170l |
| 8R win | 4c 84a 4w 0h 216l | 8c 127a 6w 0h 304l | 10c 137a 8w 0h 342l | 35c 248a 22w 18h 939l | 28c 73a 6w 0h 170l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| 3R win | 2.0/3.0 | 1.6/2.5 | 1.5/2.2 | 2.1/0.9 | 0.1/0.1 |
| 5R win | 0.3/0.1 | 0.2/0.3 | 0.1/0.3 | 0.3/0.5 | -0.0/0.0 |
| 8R win | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 51.6 | 50.6 | 53.8 | 52.4 | 28.7 |
| 3R win | 50.5 | 49.2 | 52.6 | 50.6 | 28.6 |
| 5R win | 51.3 | 50.7 | 53.9 | 52.6 | 28.7 |
| 8R win | 51.6 | 50.6 | 53.8 | 52.5 | 28.7 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 28.1 | 28.1 | 28.1 | 275.5 | 213.7 |
| 3R win | 28.1 | 28.1 | 28.1 | 262.5 | 213.7 |
| 5R win | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |
| 8R win | 28.1 | 28.1 | 28.1 | 275.5 | 213.7 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 31.9 | 13.8 | 3.7 | -32.9 | -21.7 |
| 3R win | 32.8 | 16.1 | 5.1 | -32.3 | -21.7 |
| 5R win | 31.7 | 13.9 | 3.7 | -32.9 | -21.7 |
| 8R win | 31.9 | 13.8 | 3.7 | -32.9 | -21.7 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 108.0 | 116.5 | 116.5 | 264.7 | 526.2 |
| 3R win | 93.8 | 116.5 | 116.5 | 296.6 | 522.8 |
| 5R win | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |
| 8R win | 108.0 | 116.5 | 116.5 | 267.1 | 526.2 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 5.4 | -12.4 | -21.2 | -29.3 | -29.3 |
| 3R win | 4.8 | -10.4 | -19.0 | -29.3 | -29.3 |
| 5R win | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |
| 8R win | 5.6 | -12.4 | -21.2 | -29.3 | -29.3 |

### 4b. Day entry test, loss side (-R), with combined 12R(K6) [D6-faithful]

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 29.1 | 39.7 | 38.4 | 18.5 | -0.8 |
| 1R loss | 7.2 | 20.7 | 21.9 | 17.0 | -1.7 |
| 2R loss | 31.7 | 40.5 | 39.1 | 18.0 | -1.3 |
| 3R loss | 28.8 | 39.4 | 38.1 | 18.5 | -1.0 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +15.3 | +15.7 | +14.7 | +0.8 | +2.7 |
| 1R loss | -6.6 | -3.4 | -1.9 | -0.7 | +1.9 |
| 2R loss | +17.9 | +16.5 | +15.3 | +0.3 | +2.3 |
| 3R loss | +15.0 | +15.3 | +14.4 | +0.7 | +2.6 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +27.5* | +28.0* | +23.5* | +10.5 | +5.9 |
| 1R loss | +7.2 | +10.6 | +6.9 | +5.7 | +7.0 |
| 2R loss | +25.5* | +27.8* | +23.4* | +8.1 | +8.0 |
| 3R loss | +22.5 | +24.6* | +20.6 | +9.1 | +5.9 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 1R loss | -21.9 | -19.1 | -16.5 | -1.5 | -0.8 |
| 2R loss | +2.5 | +0.8 | +0.7 | -0.5 | -0.5 |
| 3R loss | -0.4 | -0.4 | -0.3 | -0.1 | -0.1 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 1R loss | -1.6 | -1.7 | +0.0 | +3.3 | -2.0 |
| 2R loss | +4.6 | +1.0 | +0.7 | +1.8 | -2.5 |
| 3R loss | +4.7 | +3.0 | +2.6 | +1.3 | -0.2 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 4c 86a 0w 21h 0l | 8c 130a 2w 27h 0l | 10c 140a 5w 28h 0l | 35c 244a 34w 140h 0l | 28c 75a 9w 1h 0l |
| 1R loss | 6c 81a 0w 26h 644l | 11c 118a 2w 33h 986l | 13c 127a 2w 34h 1069l | 31c 224a 16w 102h 2489l | 28c 73a 3w 1h 551l |
| 2R loss | 4c 84a 4w 21h 217l | 8c 127a 6w 27h 305l | 10c 137a 8w 28h 343l | 35c 242a 22w 140h 939l | 28c 73a 6w 1h 170l |
| 3R loss | 4c 86a 1w 21h 65l | 8c 130a 3w 27h 83l | 10c 140a 6w 28h 90l | 35c 243a 27w 140h 282l | 28c 74a 7w 1h 21l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| 1R loss | 26.8/4.9 | 23.1/4.0 | 20.2/3.7 | 8.8/7.3 | 6.5/5.7 |
| 2R loss | 1.0/3.5 | 1.2/2.0 | 1.0/1.7 | 2.4/1.9 | 0.9/0.5 |
| 3R loss | 1.3/1.0 | 0.9/0.5 | 0.8/0.5 | 0.6/0.5 | 0.1/0.0 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 51.8 | 52.4 | 55.2 | 54.4 | 29.8 |
| 1R loss | 32.8 | 37.7 | 44.0 | 44.8 | 29.3 |
| 2R loss | 51.3 | 50.7 | 53.9 | 52.6 | 28.7 |
| 3R loss | 52.1 | 51.6 | 54.6 | 54.5 | 29.8 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 34.3 | 34.3 | 34.3 | 209.8 | 210.7 |
| 1R loss | 35.0 | 49.8 | 49.8 | 235.5 | 253.6 |
| 2R loss | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |
| 3R loss | 31.8 | 31.8 | 31.8 | 238.9 | 210.5 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 29.1 | 12.2 | 1.8 | -34.9 | -22.6 |
| 1R loss | 7.2 | 0.9 | -6.7 | -25.1 | -21.7 |
| 2R loss | 31.7 | 13.9 | 3.7 | -32.9 | -21.7 |
| 3R loss | 28.8 | 12.1 | 1.9 | -35.4 | -22.7 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 146.7 | 146.7 | 146.7 | 354.1 | 406.0 |
| 1R loss | 94.2 | 94.2 | 94.2 | 236.2 | 441.1 |
| 2R loss | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |
| 3R loss | 116.6 | 116.6 | 116.6 | 357.0 | 413.4 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 1.6 | -15.2 | -25.1 | -29.4 | -29.2 |
| 1R loss | 0.0 | -8.0 | -12.5 | -29.2 | -29.3 |
| 2R loss | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |
| 3R loss | 6.3 | -9.4 | -18.5 | -29.8 | -29.3 |

### 2. Per-book week floor, without combined lock

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 37.5 | 46.3 | 42.9 | 24.7 | 10.1 |
| 8R | 36.2 | 45.3 | 41.9 | 23.1 | 9.0 |
| 10R | 37.9 | 46.3 | 42.6 | 23.3 | 9.4 |
| 12R | 38.1 | 46.3 | 42.6 | 24.7 | 9.8 |
| 15R | 37.5 | 46.3 | 42.9 | 25.0 | 10.0 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +23.7* | +22.3* | +19.2* | +7.0 | +13.7 |
| 8R | +22.4 | +21.3* | +18.2* | +5.4 | +12.6 |
| 10R | +24.1* | +22.3* | +18.9* | +5.6 | +12.9 |
| 12R | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| 15R | +23.7* | +22.3* | +19.2* | +7.3 | +13.6 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +23.7* | +22.3* | +19.2* | +7.0 | +13.7 |
| 8R | +22.1 | +21.1* | +18.0* | +6.6 | +12.6 |
| 10R | +24.2* | +22.3* | +18.9* | +5.6 | +12.9 |
| 12R | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| 15R | +23.7* | +22.3* | +19.2* | +7.3 | +13.6 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 8R | -1.3 | -1.0 | -1.0 | -1.6 | -1.1 |
| 10R | +0.4 | -0.0 | -0.3 | -1.4 | -0.8 |
| 12R | +0.6 | +0.0 | -0.3 | +0.1 | -0.3 |
| 15R | +0.0 | -0.0 | -0.0 | +0.3 | -0.1 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 8R | +0.3 | +0.2 | +0.1 | -1.3 | +0.0 |
| 10R | -0.0 | -0.0 | -0.0 | +0.0 | +0.0 |
| 12R | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 15R | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 0c 84a 0w 21h 212l | 0c 127a 0w 27h 295l | 0c 137a 0w 28h 330l | 0c 240a 0w 128h 899l | 0c 73a 0w 1h 156l |
| 8R | 0c 84a 7w 21h 215l | 0c 127a 11w 27h 298l | 0c 136a 17w 28h 333l | 0c 239a 56w 128h 914l | 0c 73a 19w 1h 157l |
| 10R | 0c 84a 5w 21h 213l | 0c 127a 8w 27h 296l | 0c 137a 11w 28h 331l | 0c 241a 34w 128h 903l | 0c 73a 12w 1h 156l |
| 12R | 0c 84a 4w 21h 212l | 0c 127a 6w 27h 295l | 0c 137a 9w 28h 330l | 0c 241a 22w 128h 899l | 0c 73a 6w 1h 156l |
| 15R | 0c 84a 0w 21h 212l | 0c 127a 1w 27h 295l | 0c 137a 1w 28h 330l | 0c 241a 11w 128h 895l | 0c 73a 3w 1h 156l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| 8R | 1.9/0.6 | 1.4/0.3 | 1.5/0.5 | 3.3/1.7 | 1.2/0.1 |
| 10R | 0.3/0.8 | 0.4/0.4 | 0.6/0.4 | 2.6/1.3 | 0.9/0.1 |
| 12R | -0.0/0.6 | 0.3/0.3 | 0.6/0.3 | 0.7/0.8 | 0.3/0.0 |
| 15R | -0.0/0.0 | 0.0/0.0 | 0.0/0.0 | 0.1/0.4 | 0.1/0.0 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 47.5 | 45.8 | 55.0 | 58.9 | 34.1 |
| 8R | 47.5 | 45.8 | 55.2 | 59.0 | 33.7 |
| 10R | 46.9 | 45.4 | 55.3 | 59.2 | 34.1 |
| 12R | 46.9 | 45.4 | 55.5 | 58.1 | 34.0 |
| 15R | 47.5 | 45.8 | 55.0 | 58.2 | 34.2 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 22.7 | 22.7 | 102.2 | 277.1 | 122.7 |
| 8R | 19.4 | 19.9 | 105.4 | 241.8 | 131.6 |
| 10R | 19.4 | 19.9 | 110.7 | 246.3 | 123.8 |
| 12R | 20.6 | 20.6 | 113.4 | 262.7 | 125.7 |
| 15R | 22.7 | 22.7 | 102.2 | 265.4 | 122.7 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 37.5 | 22.0 | 9.2 | -47.3 | -19.5 |
| 8R | 36.2 | 20.6 | 8.0 | -48.6 | -20.1 |
| 10R | 37.9 | 22.0 | 9.0 | -49.1 | -20.0 |
| 12R | 38.1 | 22.0 | 9.0 | -45.6 | -19.8 |
| 15R | 37.5 | 22.0 | 9.1 | -45.9 | -19.7 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |
| 8R | 91.8 | 91.8 | 143.7 | 226.3 | 317.2 |
| 10R | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |
| 12R | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |
| 15R | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |
| 8R | 14.1 | 3.6 | -8.7 | -45.5 | -29.4 |
| 10R | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |
| 12R | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |
| 15R | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |

### 3. Day arm (arm R x keep), without combined lock

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 35.9 | 45.0 | 42.4 | 22.0 | 8.6 |
| arm 1.5R keep 25% | 34.3 | 44.4 | 41.3 | 23.8 | 8.6 |
| arm 1.5R keep 50% | 31.7 | 42.6 | 39.4 | 23.2 | 10.3 |
| arm 1.5R keep 75% | 30.4 | 38.6 | 35.3 | 19.4 | 13.2 |
| arm 2R keep 25% | 38.9 | 46.4 | 43.1 | 23.8 | 9.2 |
| arm 2R keep 50% | 38.1 | 46.3 | 42.6 | 24.7 | 9.8 |
| arm 2R keep 75% | 38.2 | 43.8 | 41.1 | 20.4 | 10.3 |
| arm 2.5R keep 25% | 35.0 | 44.3 | 41.8 | 22.9 | 8.6 |
| arm 2.5R keep 50% | 29.8 | 41.6 | 39.4 | 23.0 | 9.3 |
| arm 2.5R keep 75% | 32.5 | 40.7 | 38.6 | 19.0 | 9.5 |
| arm 3R keep 25% | 35.7 | 44.9 | 42.3 | 22.9 | 8.6 |
| arm 3R keep 50% | 31.8 | 42.9 | 40.4 | 23.2 | 8.9 |
| arm 3R keep 75% | 35.5 | 44.8 | 42.2 | 20.7 | 9.2 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | +22.1 | +21.0* | +18.7* | +4.3 | +12.2 |
| arm 1.5R keep 25% | +20.5 | +20.4* | +17.6 | +6.1 | +12.2 |
| arm 1.5R keep 50% | +17.9 | +18.5* | +15.7 | +5.5 | +13.9 |
| arm 1.5R keep 75% | +16.5 | +14.5 | +11.6 | +1.7 | +16.8* |
| arm 2R keep 25% | +25.1 | +22.3* | +19.4* | +6.1 | +12.8 |
| arm 2R keep 50% | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| arm 2R keep 75% | +24.4 | +19.8 | +17.4 | +2.7 | +13.8 |
| arm 2.5R keep 25% | +21.1 | +20.3* | +18.1* | +5.2 | +12.2 |
| arm 2.5R keep 50% | +16.0 | +17.6 | +15.7 | +5.3 | +12.8 |
| arm 2.5R keep 75% | +18.7 | +16.7 | +14.9 | +1.3 | +13.0 |
| arm 3R keep 25% | +21.9 | +20.8* | +18.6* | +5.2 | +12.1 |
| arm 3R keep 50% | +18.0 | +18.8* | +16.7* | +5.5 | +12.4 |
| arm 3R keep 75% | +21.7 | +20.8* | +18.5* | +3.0 | +12.8 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | +18.9 | +18.8 | +16.5 | +8.6 | +12.3 |
| arm 1.5R keep 25% | +19.8 | +17.6 | +15.9 | +8.6 | +12.5 |
| arm 1.5R keep 50% | +21.2 | +18.5* | +16.1 | +7.2 | +12.7 |
| arm 1.5R keep 75% | +25.3* | +18.9* | +17.5* | +8.8 | +12.4 |
| arm 2R keep 25% | +24.6 | +22.9* | +19.6* | +7.1 | +13.4 |
| arm 2R keep 50% | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| arm 2R keep 75% | +29.5* | +24.1* | +21.8* | +6.3 | +12.6 |
| arm 2.5R keep 25% | +20.9 | +20.9* | +18.4* | +8.1 | +12.4 |
| arm 2.5R keep 50% | +14.4 | +16.5 | +14.5 | +8.1 | +12.7 |
| arm 2.5R keep 75% | +18.7 | +16.8 | +15.3 | +7.4 | +12.5 |
| arm 3R keep 25% | +20.2 | +20.5* | +18.0 | +7.7 | +11.9 |
| arm 3R keep 50% | +18.4 | +19.2* | +16.5 | +8.2 | +11.8 |
| arm 3R keep 75% | +24.4* | +24.0* | +20.9* | +7.7 | +11.7 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| arm 1.5R keep 25% | -1.6 | -0.6 | -1.1 | +1.8 | -0.0 |
| arm 1.5R keep 50% | -4.2 | -2.4 | -3.0 | +1.1 | +1.7 |
| arm 1.5R keep 75% | -5.5 | -6.4 | -7.1 | -2.6 | +4.6 |
| arm 2R keep 25% | +3.0 | +1.4 | +0.7 | +1.8 | +0.6 |
| arm 2R keep 50% | +2.3 | +1.3 | +0.2 | +2.7 | +1.2 |
| arm 2R keep 75% | +2.3 | -1.2 | -1.3 | -1.7 | +1.6 |
| arm 2.5R keep 25% | -0.9 | -0.7 | -0.6 | +0.9 | -0.0 |
| arm 2.5R keep 50% | -6.0 | -3.4 | -3.0 | +1.0 | +0.6 |
| arm 2.5R keep 75% | -3.3 | -4.3 | -3.7 | -3.0 | +0.8 |
| arm 3R keep 25% | -0.2 | -0.1 | -0.1 | +0.9 | -0.1 |
| arm 3R keep 50% | -4.1 | -2.1 | -2.0 | +1.2 | +0.2 |
| arm 3R keep 75% | -0.4 | -0.1 | -0.2 | -1.3 | +0.6 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| arm 1.5R keep 25% | -2.5 | +0.6 | -0.5 | +1.8 | -0.3 |
| arm 1.5R keep 50% | -6.4 | -2.2 | -2.6 | +2.5 | +1.3 |
| arm 1.5R keep 75% | -11.9 | -6.6 | -8.1 | -2.8 | +4.4 |
| arm 2R keep 25% | -2.7 | -2.7 | -2.4 | +3.2 | -0.6 |
| arm 2R keep 50% | -3.2 | -2.2 | -2.2 | +4.2 | +0.0 |
| arm 2R keep 75% | -8.3 | -6.5 | -6.6 | +0.6 | +1.3 |
| arm 2.5R keep 25% | -2.9 | -2.8 | -2.5 | +1.4 | -0.1 |
| arm 2.5R keep 50% | -1.5 | -1.1 | -1.0 | +1.4 | +0.2 |
| arm 2.5R keep 75% | -3.1 | -2.3 | -2.6 | -1.9 | +0.6 |
| arm 3R keep 25% | -1.5 | -1.9 | -1.6 | +1.8 | +0.2 |
| arm 3R keep 50% | -3.6 | -2.5 | -2.0 | +1.5 | +0.7 |
| arm 3R keep 75% | -5.8 | -5.4 | -4.6 | -0.5 | +1.1 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 0c 0a 4w 21h 212l | 0c 0a 6w 27h 295l | 0c 0a 8w 28h 330l | 0c 0a 24w 144h 896l | 0c 0a 7w 1h 156l |
| arm 1.5R keep 25% | 0c 85a 2w 21h 220l | 0c 146a 4w 27h 305l | 0c 156a 5w 28h 340l | 0c 330a 17w 129h 907l | 0c 126a 4w 1h 156l |
| arm 1.5R keep 50% | 0c 122a 2w 21h 220l | 0c 208a 4w 27h 305l | 0c 228a 6w 28h 340l | 0c 463a 16w 130h 915l | 0c 185a 4w 1h 156l |
| arm 1.5R keep 75% | 0c 157a 0w 22h 222l | 0c 284a 2w 29h 307l | 0c 316a 4w 30h 342l | 0c 653a 16w 130h 919l | 0c 254a 4w 1h 156l |
| arm 2R keep 25% | 0c 50a 3w 21h 213l | 0c 76a 5w 27h 296l | 0c 80a 7w 28h 331l | 0c 149a 22w 128h 899l | 0c 33a 6w 1h 156l |
| arm 2R keep 50% | 0c 84a 4w 21h 212l | 0c 127a 6w 27h 295l | 0c 137a 9w 28h 330l | 0c 241a 22w 128h 899l | 0c 73a 6w 1h 156l |
| arm 2R keep 75% | 0c 112a 2w 22h 212l | 0c 189a 4w 28h 295l | 0c 207a 6w 29h 330l | 0c 396a 20w 130h 903l | 0c 123a 6w 1h 156l |
| arm 2.5R keep 25% | 0c 24a 3w 21h 212l | 0c 36a 5w 27h 295l | 0c 38a 7w 28h 330l | 0c 63a 23w 140h 891l | 0c 19a 6w 1h 156l |
| arm 2.5R keep 50% | 0c 50a 3w 21h 211l | 0c 72a 5w 27h 294l | 0c 78a 7w 28h 329l | 0c 121a 23w 140h 894l | 0c 36a 6w 1h 156l |
| arm 2.5R keep 75% | 0c 74a 1w 22h 212l | 0c 123a 3w 28h 295l | 0c 135a 5w 29h 330l | 0c 249a 23w 142h 898l | 0c 66a 6w 1h 156l |
| arm 3R keep 25% | 0c 11a 3w 21h 211l | 0c 16a 5w 27h 294l | 0c 18a 7w 28h 329l | 0c 30a 23w 140h 890l | 0c 8a 7w 1h 156l |
| arm 3R keep 50% | 0c 30a 3w 21h 211l | 0c 41a 5w 27h 294l | 0c 45a 7w 28h 329l | 0c 63a 23w 140h 893l | 0c 17a 7w 1h 156l |
| arm 3R keep 75% | 0c 53a 2w 21h 211l | 0c 80a 4w 27h 294l | 0c 87a 6w 28h 329l | 0c 154a 23w 142h 902l | 0c 33a 7w 1h 156l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| arm 1.5R keep 25% | 7.4/5.9 | 5.4/4.9 | 5.6/4.5 | 4.7/6.5 | 3.2/3.2 |
| arm 1.5R keep 50% | 13.6/9.4 | 9.8/7.3 | 9.5/6.5 | 8.0/9.2 | 4.0/5.7 |
| arm 1.5R keep 75% | 16.8/11.2 | 14.1/7.6 | 13.9/6.8 | 13.9/11.3 | 3.4/8.0 |
| arm 2R keep 25% | 2.1/5.1 | 1.9/3.3 | 2.3/3.0 | 2.1/3.8 | 0.4/1.0 |
| arm 2R keep 50% | 5.6/7.8 | 3.9/5.3 | 4.4/4.6 | 3.6/6.3 | 1.2/2.4 |
| arm 2R keep 75% | 8.7/11.1 | 8.5/7.3 | 7.7/6.5 | 10.0/8.4 | 2.2/3.8 |
| arm 2.5R keep 25% | 2.2/1.3 | 1.5/0.8 | 1.4/0.8 | 1.0/1.9 | 0.4/0.4 |
| arm 2.5R keep 50% | 8.0/2.0 | 5.0/1.6 | 4.5/1.5 | 2.2/3.1 | 0.3/0.9 |
| arm 2.5R keep 75% | 9.9/6.5 | 8.6/4.2 | 7.7/3.9 | 7.9/4.9 | 0.7/1.5 |
| arm 3R keep 25% | 0.4/0.2 | 0.3/0.2 | 0.4/0.3 | 0.4/1.3 | 0.2/0.1 |
| arm 3R keep 50% | 4.4/0.3 | 2.7/0.6 | 2.6/0.6 | 1.0/2.2 | 0.1/0.4 |
| arm 3R keep 75% | 5.4/5.1 | 4.2/4.1 | 3.8/3.7 | 4.9/3.5 | 0.3/0.9 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 56.0 | 50.2 | 58.5 | 63.1 | 35.6 |
| arm 1.5R keep 25% | 54.7 | 49.3 | 56.3 | 56.7 | 35.5 |
| arm 1.5R keep 50% | 39.3 | 42.6 | 53.5 | 51.1 | 33.4 |
| arm 1.5R keep 75% | 33.0 | 35.3 | 47.7 | 48.9 | 34.2 |
| arm 2R keep 25% | 53.8 | 47.5 | 55.2 | 61.7 | 35.1 |
| arm 2R keep 50% | 46.9 | 45.4 | 55.5 | 58.1 | 34.0 |
| arm 2R keep 75% | 42.5 | 39.8 | 50.4 | 53.1 | 34.0 |
| arm 2.5R keep 25% | 55.7 | 49.5 | 57.4 | 61.3 | 35.4 |
| arm 2.5R keep 50% | 52.2 | 47.7 | 56.8 | 59.6 | 35.5 |
| arm 2.5R keep 75% | 48.9 | 43.5 | 53.9 | 54.1 | 35.4 |
| arm 3R keep 25% | 56.3 | 50.5 | 58.5 | 61.4 | 35.5 |
| arm 3R keep 50% | 55.8 | 50.0 | 58.7 | 60.6 | 35.6 |
| arm 3R keep 75% | 53.7 | 46.9 | 57.4 | 56.8 | 35.4 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 38.0 | 38.0 | 93.2 | 299.9 | 147.3 |
| arm 1.5R keep 25% | 25.5 | 25.5 | 94.8 | 226.1 | 120.3 |
| arm 1.5R keep 50% | 10.4 | 17.8 | 118.5 | 188.7 | 90.0 |
| arm 1.5R keep 75% | 6.2 | 20.8 | 129.2 | 206.3 | 85.4 |
| arm 2R keep 25% | 28.4 | 28.4 | 93.3 | 279.2 | 138.4 |
| arm 2R keep 50% | 20.6 | 20.6 | 113.4 | 262.7 | 125.7 |
| arm 2R keep 75% | 20.6 | 26.7 | 94.1 | 244.5 | 121.1 |
| arm 2.5R keep 25% | 38.6 | 38.6 | 93.3 | 287.5 | 148.9 |
| arm 2.5R keep 50% | 38.0 | 38.0 | 95.3 | 276.6 | 143.4 |
| arm 2.5R keep 75% | 40.7 | 40.7 | 93.9 | 244.9 | 143.9 |
| arm 3R keep 25% | 38.3 | 38.3 | 93.3 | 301.1 | 149.3 |
| arm 3R keep 50% | 38.1 | 38.1 | 98.3 | 294.0 | 146.0 |
| arm 3R keep 75% | 39.8 | 39.8 | 95.1 | 271.4 | 143.7 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 35.9 | 18.5 | 6.6 | -55.3 | -22.3 |
| arm 1.5R keep 25% | 34.3 | 18.4 | 5.9 | -43.8 | -22.6 |
| arm 1.5R keep 50% | 31.7 | 20.7 | 7.7 | -37.8 | -18.9 |
| arm 1.5R keep 75% | 30.4 | 20.5 | 7.3 | -37.0 | -17.6 |
| arm 2R keep 25% | 38.9 | 21.1 | 9.5 | -50.8 | -21.4 |
| arm 2R keep 50% | 38.1 | 22.0 | 9.0 | -45.6 | -19.8 |
| arm 2R keep 75% | 38.2 | 24.7 | 12.8 | -43.1 | -19.7 |
| arm 2.5R keep 25% | 35.0 | 18.0 | 6.3 | -50.6 | -22.0 |
| arm 2.5R keep 50% | 29.8 | 16.1 | 3.7 | -47.7 | -21.4 |
| arm 2.5R keep 75% | 32.5 | 19.2 | 6.7 | -45.5 | -21.3 |
| arm 3R keep 25% | 35.7 | 18.2 | 6.2 | -51.3 | -22.4 |
| arm 3R keep 50% | 31.8 | 16.5 | 4.0 | -49.6 | -22.1 |
| arm 3R keep 75% | 35.5 | 21.5 | 7.6 | -47.6 | -21.8 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 100.6 | 100.6 | 135.2 | 249.9 | 308.4 |
| arm 1.5R keep 25% | 86.7 | 86.7 | 157.0 | 219.3 | 357.6 |
| arm 1.5R keep 50% | 76.3 | 76.3 | 154.0 | 183.0 | 239.6 |
| arm 1.5R keep 75% | 76.5 | 76.5 | 141.1 | 168.3 | 175.9 |
| arm 2R keep 25% | 96.0 | 96.0 | 136.9 | 247.3 | 347.3 |
| arm 2R keep 50% | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |
| arm 2R keep 75% | 85.7 | 85.7 | 126.1 | 194.0 | 285.9 |
| arm 2.5R keep 25% | 96.9 | 96.9 | 136.6 | 287.1 | 313.4 |
| arm 2.5R keep 50% | 93.5 | 93.5 | 137.3 | 263.0 | 288.8 |
| arm 2.5R keep 75% | 83.8 | 83.8 | 124.3 | 226.0 | 270.0 |
| arm 3R keep 25% | 103.7 | 103.7 | 135.2 | 253.8 | 302.7 |
| arm 3R keep 50% | 105.9 | 105.9 | 129.6 | 275.1 | 298.6 |
| arm 3R keep 75% | 101.2 | 101.2 | 123.6 | 238.9 | 291.7 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| arm off | 17.0 | 0.9 | -11.9 | -58.2 | -29.7 |
| arm 1.5R keep 25% | 14.5 | 4.6 | -8.2 | -51.1 | -31.3 |
| arm 1.5R keep 50% | 10.5 | 5.7 | -7.1 | -42.6 | -27.6 |
| arm 1.5R keep 75% | 5.0 | 2.5 | -9.6 | -39.5 | -26.1 |
| arm 2R keep 25% | 14.3 | 0.5 | -11.6 | -48.9 | -31.0 |
| arm 2R keep 50% | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |
| arm 2R keep 75% | 8.7 | 1.5 | -9.2 | -41.3 | -29.2 |
| arm 2.5R keep 25% | 14.1 | -0.6 | -12.9 | -54.3 | -29.9 |
| arm 2.5R keep 50% | 15.5 | 1.3 | -10.5 | -50.9 | -29.1 |
| arm 2.5R keep 75% | 13.9 | 4.3 | -7.5 | -46.0 | -28.8 |
| arm 3R keep 25% | 15.5 | -0.9 | -13.5 | -54.5 | -29.6 |
| arm 3R keep 50% | 13.4 | -1.3 | -12.9 | -54.0 | -29.5 |
| arm 3R keep 75% | 11.2 | -0.7 | -12.7 | -51.7 | -29.4 |

### 4a. Day entry test, win side (+R), without combined lock

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 38.3 | 46.2 | 42.4 | 24.7 | 9.8 |
| 3R win | 39.1 | 46.9 | 43.1 | 23.0 | 9.7 |
| 5R win | 38.1 | 46.3 | 42.6 | 24.7 | 9.8 |
| 8R win | 38.3 | 46.2 | 42.4 | 24.7 | 9.8 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +24.5* | +22.1* | +18.7* | +7.0 | +13.4 |
| 3R win | +25.3* | +22.9* | +19.3* | +5.3 | +13.3 |
| 5R win | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| 8R win | +24.5* | +22.1* | +18.7* | +7.0 | +13.4 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +26.2* | +23.0* | +19.5* | +7.2 | +13.5 |
| 3R win | +27.0* | +23.6* | +19.8* | +8.1 | +13.2 |
| 5R win | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| 8R win | +26.0* | +22.9* | +19.4* | +7.2 | +13.5 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 3R win | +0.9 | +0.8 | +0.6 | -1.7 | -0.1 |
| 5R win | -0.1 | +0.2 | +0.2 | +0.0 | -0.0 |
| 8R win | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 3R win | +0.0 | +0.2 | +0.3 | -2.6 | +0.2 |
| 5R win | +1.7 | +0.9 | +0.8 | +0.2 | +0.1 |
| 8R win | +0.2 | +0.1 | +0.1 | +0.0 | +0.0 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 0c 84a 4w 0h 211l | 0c 127a 6w 0h 294l | 0c 137a 9w 0h 329l | 0c 246a 22w 0h 899l | 0c 73a 6w 0h 156l |
| 3R win | 0c 78a 4w 131h 211l | 0c 118a 6w 206h 294l | 0c 128a 9w 214h 329l | 0c 224a 22w 524h 897l | 0c 70a 6w 36h 156l |
| 5R win | 0c 84a 4w 21h 212l | 0c 127a 6w 27h 295l | 0c 137a 9w 28h 330l | 0c 241a 22w 128h 899l | 0c 73a 6w 1h 156l |
| 8R win | 0c 84a 4w 0h 211l | 0c 127a 6w 0h 294l | 0c 137a 9w 0h 329l | 0c 246a 22w 19h 899l | 0c 73a 6w 0h 156l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| 3R win | 2.3/3.2 | 1.8/2.6 | 1.6/2.3 | 3.2/1.5 | 0.5/0.4 |
| 5R win | 0.3/0.2 | 0.2/0.3 | 0.1/0.3 | 0.4/0.5 | 0.0/0.0 |
| 8R win | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 47.1 | 45.2 | 55.3 | 58.1 | 34.0 |
| 3R win | 45.9 | 43.6 | 54.3 | 56.1 | 34.0 |
| 5R win | 46.9 | 45.4 | 55.5 | 58.1 | 34.0 |
| 8R win | 47.1 | 45.2 | 55.3 | 58.2 | 34.0 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 20.6 | 20.6 | 113.4 | 264.0 | 125.7 |
| 3R win | 20.7 | 20.8 | 112.8 | 271.2 | 129.4 |
| 5R win | 20.6 | 20.6 | 113.4 | 262.7 | 125.7 |
| 8R win | 20.6 | 20.6 | 113.4 | 264.0 | 125.7 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 38.3 | 21.9 | 8.9 | -45.6 | -19.8 |
| 3R win | 39.1 | 24.1 | 10.5 | -46.5 | -20.2 |
| 5R win | 38.1 | 22.0 | 9.0 | -45.6 | -19.8 |
| 8R win | 38.3 | 21.9 | 8.9 | -45.6 | -19.8 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 91.8 | 91.8 | 143.7 | 212.6 | 322.2 |
| 3R win | 89.2 | 89.2 | 143.7 | 218.6 | 316.1 |
| 5R win | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |
| 8R win | 91.8 | 91.8 | 143.7 | 215.0 | 322.2 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 12.1 | 2.6 | -9.7 | -43.8 | -29.7 |
| 3R win | 12.1 | 5.7 | -6.3 | -42.4 | -29.3 |
| 5R win | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |
| 8R win | 12.3 | 2.6 | -9.7 | -43.8 | -29.7 |

### 4b. Day entry test, loss side (-R), without combined lock

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 36.6 | 46.9 | 42.9 | 24.4 | 10.7 |
| 1R loss | 27.1 | 35.8 | 34.6 | 21.8 | 8.5 |
| 2R loss | 38.1 | 46.3 | 42.6 | 24.7 | 9.8 |
| 3R loss | 35.4 | 46.1 | 42.5 | 26.2 | 10.4 |

**Composite C minus the as-is stack as it is (A0 = as-is, D6 per-book locks, no combined) $k/wk (* = beyond MDE)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +22.8* | +22.9* | +19.2* | +6.7 | +14.3 |
| 1R loss | +13.3 | +11.8 | +10.9 | +4.1 | +12.1 |
| 2R loss | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| 3R loss | +21.6* | +22.1* | +18.8* | +8.5 | +14.0 |

**Composite C minus the as-is stack with the SAME setting A(s) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +32.3* | +26.9* | +23.4* | +8.0 | +9.4 |
| 1R loss | +24.3 | +22.5* | +17.7 | +7.4 | +18.1* |
| 2R loss | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| 3R loss | +22.7 | +22.1* | +19.4* | +7.6 | +9.5 |

**Lock effect on the composite: C(s) minus C(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 1R loss | -9.5 | -11.1 | -8.3 | -2.6 | -2.2 |
| 2R loss | +1.6 | -0.6 | -0.4 | +0.4 | -0.9 |
| 3R loss | -1.2 | -0.8 | -0.5 | +1.8 | -0.3 |

**Lock effect on the as-is stack: A(s) minus A(lock off) $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 1R loss | -1.4 | -6.8 | -2.6 | -2.1 | -10.9 |
| 2R loss | +9.6 | +4.0 | +4.2 | +1.3 | -4.8 |
| 3R loss | +8.5 | +4.0 | +3.6 | +2.2 | -0.3 |

**Fires per window (c = combined lock weeks, a = day-arm book-days, w = week-floor book-weeks, h = entry +R skipped signals, l = entry -R skipped signals), composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 0c 85a 1w 21h 0l | 0c 129a 3w 27h 0l | 0c 139a 6w 28h 0l | 0c 241a 33w 128h 0l | 0c 75a 9w 1h 0l |
| 1R loss | 0c 80a 0w 22h 647l | 0c 117a 2w 28h 986l | 0c 126a 2w 29h 1066l | 0c 225a 13w 102h 2472l | 0c 73a 3w 1h 543l |
| 2R loss | 0c 84a 4w 21h 212l | 0c 127a 6w 27h 295l | 0c 137a 9w 28h 330l | 0c 241a 22w 128h 899l | 0c 73a 6w 1h 156l |
| 3R loss | 0c 85a 2w 21h 66l | 0c 129a 4w 27h 84l | 0c 139a 7w 28h 89l | 0c 241a 27w 128h 282l | 0c 74a 7w 1h 20l |

**Forgone / avoided $k per week on the composite (forgone = sum of weeks where lock-on lost vs lock-off, avoided = weeks where it gained; /number of weeks)**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 | -0.0/0.0 |
| 1R loss | 14.0/4.5 | 15.8/4.7 | 14.7/6.4 | 10.4/7.8 | 5.9/3.7 |
| 2R loss | 2.4/4.0 | 2.9/2.3 | 2.8/2.5 | 4.0/4.4 | 1.9/1.0 |
| 3R loss | 2.0/0.9 | 1.5/0.7 | 1.3/0.9 | 0.5/2.4 | 0.6/0.3 |

**Composite weekly SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 47.9 | 46.2 | 56.8 | 61.0 | 34.7 |
| 1R loss | 37.3 | 38.4 | 46.6 | 52.8 | 34.6 |
| 2R loss | 46.9 | 45.4 | 55.5 | 58.1 | 34.0 |
| 3R loss | 48.9 | 45.9 | 55.9 | 59.7 | 34.6 |

**Composite weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 28.5 | 28.5 | 121.7 | 205.9 | 124.7 |
| 1R loss | 17.2 | 49.2 | 55.6 | 263.6 | 131.0 |
| 2R loss | 20.6 | 20.6 | 113.4 | 262.7 | 125.7 |
| 3R loss | 32.8 | 32.8 | 113.6 | 192.0 | 130.7 |

**Composite mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 36.6 | 22.2 | 8.5 | -53.2 | -19.4 |
| 1R loss | 27.1 | 16.8 | 6.8 | -43.5 | -20.6 |
| 2R loss | 38.1 | 22.0 | 9.0 | -45.6 | -19.8 |
| 3R loss | 35.4 | 21.5 | 8.4 | -48.4 | -19.3 |

(A, as-is stack under the same setting: maxDD and worst-20)
**As-is weekly maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 121.3 | 121.3 | 171.7 | 141.2 | 207.3 |
| 1R loss | 85.9 | 85.9 | 85.9 | 139.5 | 473.7 |
| 2R loss | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |
| 3R loss | 72.8 | 72.8 | 170.0 | 165.0 | 205.4 |

**As-is mean of worst 20 weeks $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 4.2 | -4.2 | -18.6 | -53.1 | -26.1 |
| 1R loss | 2.8 | -3.6 | -9.3 | -38.7 | -35.7 |
| 2R loss | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |
| 3R loss | 12.7 | 3.6 | -9.6 | -46.9 | -26.3 |

### 5. Pair: combined multiple x per-book week floor

**C minus A0 (as-is as it is)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| combined \ floor | off | 8R | 10R | 12R | 15R |
|---|---|---|---|---|---|
| off | +23.7* / +22.3* / +19.2* / +7.0 / +13.7 | +22.4 / +21.3* / +18.2* / +5.4 / +12.6 | +24.1* / +22.3* / +18.9* / +5.6 / +12.9 | +24.3* / +22.3* / +18.9* / +7.0 / +13.4 | +23.7* / +22.3* / +19.2* / +7.3 / +13.6 |
| 6R | -9.4 / -8.6 / -5.8 / -11.2 / -2.0 | -8.0 / -8.2 / -5.5 / -10.3 / -2.0 | -9.4 / -8.8 / -6.0 / -10.8 / -2.0 | -9.4 / -8.8 / -6.0 / -10.8 / -2.0 | -9.4 / -8.6 / -5.8 / -11.2 / -2.0 |
| 8R | +12.9 / +8.6 / +9.0 / -7.5 / -2.6 | +13.0 / +8.3 / +8.7 / -6.9 / -2.7 | +13.2 / +8.5 / +8.9 / -7.0 / -2.6 | +13.2 / +8.5 / +8.9 / -7.4 / -2.6 | +12.9 / +8.6 / +9.0 / -7.5 / -2.6 |
| 10R | +17.8 / +10.7 / +10.4 / -1.6 / -2.3 | +17.9 / +10.4 / +10.2 / -1.0 / -1.6 | +18.1 / +10.7 / +10.4 / -1.1 / -2.3 | +18.0 / +10.6 / +10.3 / -1.5 / -2.3 | +17.8 / +10.7 / +10.4 / -1.6 / -2.3 |
| 12R | +17.6 / +16.6 / +15.5 / +0.2 / +2.3 | +17.7 / +16.3 / +15.2 / +0.9 / +2.7 | +17.9 / +16.6 / +15.4 / +0.5 / +2.3 | +17.9 / +16.5 / +15.3 / +0.3 / +2.3 | +17.6 / +16.6 / +15.4 / +0.2 / +2.3 |
| 15R | +16.8 / +17.9 / +16.4 / -0.2 / +3.2 | +16.9 / +17.6 / +16.1 / +0.1 / +2.9 | +17.2 / +17.9 / +16.3 / +0.1 / +3.0 | +17.1 / +17.8 / +16.3 / -0.1 / +3.2 | +16.8 / +17.9 / +16.4 / -0.2 / +3.2 |
| 20R | +12.7 / +15.6 / +12.3 / -0.7 / +8.2 | +13.0 / +15.4 / +12.1 / -0.6 / +7.7 | +13.1 / +15.6 / +12.3 / -0.4 / +7.8 | +13.0 / +15.5 / +12.2 / -0.6 / +8.0 | +12.7 / +15.6 / +12.3 / -0.7 / +8.2 |
| 30R | +23.7* / +20.9* / +18.9* / -2.5 / +10.8 | +22.4 / +19.8* / +17.0 / -2.1 / +10.0 | +24.1* / +20.8* / +18.9* / -2.1 / +10.3 | +24.3* / +20.9* / +18.9* / -2.3 / +10.5 | +23.7* / +20.8* / +18.9* / -2.4 / +10.7 |

**C(s) minus A(s) (same settings both)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| combined \ floor | off | 8R | 10R | 12R | 15R |
|---|---|---|---|---|---|
| off | +23.7* / +22.3* / +19.2* / +7.0 / +13.7 | +22.1 / +21.1* / +18.0* / +6.6 / +12.6 | +24.2* / +22.3* / +18.9* / +5.6 / +12.9 | +24.3* / +22.3* / +18.9* / +7.0 / +13.4 | +23.7* / +22.3* / +19.2* / +7.3 / +13.6 |
| 6R | +6.7 / +9.8 / +10.3 / +4.5 / +2.7 | +8.1 / +10.2 / +10.6 / +5.4 / +2.7 | +6.7 / +9.6 / +10.1 / +4.9 / +2.7 | +6.7 / +9.6 / +10.1 / +4.9 / +2.7 | +6.7 / +9.8 / +10.3 / +4.5 / +2.7 |
| 8R | +28.1 / +23.0 / +22.2 / +5.9 / +4.8 | +28.2 / +22.7 / +21.9 / +6.7 / +4.7 | +28.4 / +22.9 / +22.1 / +6.4 / +4.8 | +28.4 / +22.9 / +22.1 / +6.0 / +4.8 | +28.1 / +23.0 / +22.2 / +5.9 / +4.8 |
| 10R | +23.8* / +20.3 / +20.0 / +7.5 / +3.1 | +23.9* / +20.1 / +19.7 / +8.3 / +3.8 | +24.1* / +20.3 / +19.9 / +8.0 / +3.1 | +24.0* / +20.2 / +19.9 / +7.6 / +3.1 | +23.8* / +20.3 / +20.0 / +7.5 / +3.1 |
| 12R | +25.2* / +27.9* / +23.6* / +8.0 / +8.0 | +25.3* / +27.6* / +23.3* / +8.9 / +8.5 | +25.5* / +27.9* / +23.5* / +8.3 / +8.0 | +25.5* / +27.8* / +23.4* / +8.1 / +8.0 | +25.2* / +27.9* / +23.5* / +8.0 / +8.0 |
| 15R | +22.0* / +27.9* / +24.0* / +8.2 / +10.6 | +22.2* / +27.5* / +23.7* / +8.7 / +10.2 | +22.4* / +27.8* / +23.9* / +8.5 / +10.4 | +22.3* / +27.7* / +23.8* / +8.3 / +10.6 | +22.0* / +27.8* / +23.9* / +8.2 / +10.6 |
| 20R | +9.6 / +18.7 / +14.2 / +4.0 / +12.9 | +9.5 / +18.3 / +13.9 / +4.3 / +12.5 | +10.0 / +18.6 / +14.2 / +4.2 / +12.6 | +9.9 / +18.5 / +14.0 / +4.1 / +12.8 | +9.6 / +18.6 / +14.2 / +4.0 / +12.9 |
| 30R | +22.3* / +20.2* / +18.1* / -0.1 / +10.8 | +20.7 / +19.0* / +16.0 / +0.5 / +10.0 | +22.8* / +20.2* / +18.1* / +0.3 / +10.3 | +22.9* / +20.2* / +18.1* / +0.1 / +10.5 | +22.3* / +20.1* / +18.0* / +0.0 / +10.7 |

### 6. Pair: combined multiple x day arm (R, keep 50%)

**C minus A0 (as-is as it is)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| combined \ arm R | off | 1.5R | 2R | 2.5R | 3R |
|---|---|---|---|---|---|
| off | +22.1 / +21.0* / +18.7* / +4.3 / +12.2 | +17.9 / +18.5* / +15.7 / +5.5 / +13.9 | +24.3* / +22.3* / +18.9* / +7.0 / +13.4 | +16.0 / +17.6 / +15.7 / +5.3 / +12.8 | +18.0 / +18.8* / +16.7* / +5.5 / +12.4 |
| 6R | -14.6 / -15.4 / -11.3 / -11.2 / -3.1 | -14.1 / -5.5 / -3.7 / -13.1 / -2.1 | -9.4 / -8.8 / -6.0 / -10.8 / -2.0 | -16.1 / -15.9 / -11.9 / -12.0 / -1.1 | -14.7 / -15.2 / -11.3 / -11.2 / -3.0 |
| 8R | +9.8 / +6.2 / +7.5 / -7.7 / -2.0 | +2.7 / +9.0 / +8.7 / -8.3 / +0.0 | +13.2 / +8.5 / +8.9 / -7.4 / -2.6 | +5.2 / +3.8 / +5.2 / -8.2 / -1.9 | +5.8 / +4.2 / +5.5 / -7.6 / -1.9 |
| 10R | +10.3 / +6.2 / +7.2 / -6.9 / -1.9 | +7.6 / +11.2 / +10.4 / -4.1 / +1.1 | +18.0 / +10.6 / +10.3 / -1.5 / -2.3 | +5.9 / +3.8 / +5.0 / -5.9 / -1.6 | +7.2 / +4.5 / +5.6 / -6.6 / -1.7 |
| 12R | +14.2 / +9.7 / +9.9 / -3.3 / +0.7 | +8.1 / +11.2 / +10.2 / -3.1 / +4.3 | +17.9 / +16.5 / +15.3 / +0.3 / +2.3 | +5.6 / +5.0 / +5.6 / -3.8 / +2.8 | +6.9 / +5.9 / +6.4 / -3.2 / +0.8 |
| 15R | +13.7 / +10.8 / +10.7 / -1.8 / +3.6 | +7.2 / +12.1 / +10.6 / -2.0 / +3.4 | +17.1 / +17.8 / +16.3 / -0.1 / +3.2 | +5.0 / +6.1 / +6.4 / -2.2 / +3.9 | +10.5 / +9.2 / +9.1 / -1.5 / +3.7 |
| 20R | +10.2 / +13.7 / +11.4 / -2.5 / +7.6 | +4.5 / +10.5 / +10.4 / -1.8 / +9.2 | +13.0 / +15.5 / +12.2 / -0.6 / +8.0 | +5.4 / +11.0 / +8.8 / -2.5 / +7.9 | +7.2 / +12.2 / +9.9 / -1.8 / +7.7 |
| 30R | +22.2 / +19.6* / +15.9 / -3.9 / +8.9 | +17.9 / +17.0 / +15.8 / -4.1 / +11.7 | +24.3* / +20.9* / +18.9* / -2.3 / +10.5 | +14.2 / +15.2 / +11.9 / -4.1 / +9.9 | +15.8 / +16.4 / +12.8 / -3.1 / +9.1 |

**C(s) minus A(s) (same settings both)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| combined \ arm R | off | 1.5R | 2R | 2.5R | 3R |
|---|---|---|---|---|---|
| off | +18.9 / +18.8 / +16.5 / +8.6 / +12.3 | +21.2 / +18.5* / +16.1 / +7.2 / +12.7 | +24.3* / +22.3* / +18.9* / +7.0 / +13.4 | +14.4 / +16.5 / +14.5 / +8.1 / +12.7 | +18.4 / +19.2* / +16.5 / +8.2 / +11.8 |
| 6R | -4.7 / -0.4 / +1.8 / +6.3 / +2.0 | +1.4 / +13.4 / +9.9 / +2.0 / +0.8 | +6.7 / +9.6 / +10.1 / +4.9 / +2.7 | -1.9 / +1.7 / +3.5 / +4.6 / +3.8 | -0.7 / +1.9 / +3.6 / +5.2 / +1.9 |
| 8R | +17.5 / +17.6 / +18.0 / +8.3 / +6.8 | +21.6 / +24.6* / +19.9 / +4.9 / +4.0 | +28.4 / +22.9 / +22.1 / +6.0 / +4.8 | +16.8 / +17.6 / +17.9 / +7.2 / +6.8 | +17.3 / +17.5 / +17.7 / +7.3 / +6.8 |
| 10R | +7.4 / +13.4 / +14.7 / +4.9 / +4.3 | +15.4 / +19.6 / +15.7 / +4.2 / +6.0 | +24.0* / +20.2 / +19.9 / +7.6 / +3.1 | +7.4 / +12.1 / +13.3 / +5.7 / +4.4 | +7.8 / +13.6 / +14.7 / +3.9 / +4.1 |
| 12R | +13.4 / +19.2 / +15.8 / +6.4 / +5.2 | +14.7 / +19.9 / +16.2 / +4.9 / +5.9 | +25.5* / +27.8* / +23.4* / +8.1 / +8.0 | +9.1 / +15.3 / +12.2 / +6.9 / +7.4 | +9.6 / +17.2 / +13.9 / +6.0 / +5.0 |
| 15R | +4.7 / +12.2 / +9.9 / +9.2 / +10.5 | +16.5 / +17.2 / +14.2 / +4.9 / +7.9 | +22.3* / +27.7* / +23.8* / +8.3 / +10.6 | -1.1 / +11.6 / +9.2 / +7.3 / +11.0 | +6.8 / +13.2 / +10.6 / +8.9 / +10.3 |
| 20R | +3.8 / +14.4 / +10.8 / +6.1 / +13.8 | +5.9 / +12.5 / +11.7 / +4.5 / +11.3 | +9.9 / +18.5 / +14.0 / +4.1 / +12.8 | +0.7 / +12.8 / +9.2 / +6.3 / +12.0 | +4.8 / +16.8 / +12.7 / +6.3 / +11.4 |
| 30R | +17.0 / +16.4 / +12.4 / +5.2 / +10.1 | +20.9 / +16.8 / +15.9 / +0.5 / +11.6 | +22.9* / +20.2* / +18.1* / +0.1 / +10.5 | +11.0 / +13.3 / +9.8 / +3.5 / +10.9 | +13.8 / +15.5 / +11.4 / +4.2 / +9.7 |

### 7. Pair: per-book week floor x day arm (keep 50%), combined 12R

**C minus A0 (as-is as it is)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| floor \ arm R | off | 1.5R | 2R | 2.5R | 3R |
|---|---|---|---|---|---|
| off | +14.2 / +10.2 / +10.4 / -3.5 / +0.7 | +7.8 / +11.3 / +10.3 / -3.0 / +4.3 | +17.6 / +16.6 / +15.5 / +0.2 / +2.3 | +5.4 / +5.2 / +5.8 / -3.9 / +2.8 | +6.9 / +6.4 / +6.9 / -3.3 / +0.8 |
| 8R | +14.2 / +9.6 / +9.8 / -2.9 / +0.9 | +8.2 / +11.2 / +10.2 / -3.2 / +4.2 | +17.7 / +16.3 / +15.2 / +0.9 / +2.7 | +5.7 / +5.0 / +5.6 / -3.6 / +3.0 | +6.9 / +5.8 / +6.4 / -2.8 / +1.0 |
| 10R | +14.2 / +9.7 / +9.9 / -3.2 / +0.7 | +8.1 / +11.3 / +10.3 / -3.0 / +4.1 | +17.9 / +16.6 / +15.4 / +0.5 / +2.3 | +5.6 / +5.1 / +5.7 / -3.8 / +2.8 | +6.9 / +6.0 / +6.5 / -3.2 / +0.8 |
| 12R | +14.2 / +9.7 / +9.9 / -3.3 / +0.7 | +8.1 / +11.2 / +10.2 / -3.1 / +4.3 | +17.9 / +16.5 / +15.3 / +0.3 / +2.3 | +5.6 / +5.0 / +5.6 / -3.8 / +2.8 | +6.9 / +5.9 / +6.4 / -3.2 / +0.8 |
| 15R | +14.2 / +10.2 / +10.3 / -3.3 / +0.7 | +7.8 / +11.3 / +10.3 / -3.0 / +4.3 | +17.6 / +16.6 / +15.4 / +0.2 / +2.3 | +5.4 / +5.2 / +5.8 / -3.9 / +2.8 | +6.9 / +6.4 / +6.9 / -3.3 / +0.8 |

**C(s) minus A(s) (same settings both)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| floor \ arm R | off | 1.5R | 2R | 2.5R | 3R |
|---|---|---|---|---|---|
| off | +13.4 / +19.7 / +16.3 / +6.2 / +5.2 | +14.4 / +20.0 / +16.3 / +5.0 / +5.9 | +25.2* / +27.9* / +23.6* / +8.0 / +8.0 | +8.8 / +15.5 / +12.4 / +6.8 / +7.4 | +9.6 / +17.8 / +14.4 / +5.9 / +5.0 |
| 8R | +13.4 / +19.1 / +15.8 / +7.0 / +5.4 | +14.8 / +19.8 / +16.1 / +4.8 / +5.7 | +25.3* / +27.6* / +23.3* / +8.9 / +8.5 | +9.2 / +15.3 / +12.2 / +7.3 / +7.6 | +9.6 / +17.1 / +13.9 / +6.6 / +5.2 |
| 10R | +13.4 / +19.2 / +15.9 / +6.4 / +5.2 | +14.8 / +19.9 / +16.2 / +5.0 / +5.7 | +25.5* / +27.9* / +23.5* / +8.3 / +8.0 | +9.1 / +15.3 / +12.3 / +6.9 / +7.4 | +9.6 / +17.3 / +14.0 / +6.0 / +5.0 |
| 12R | +13.4 / +19.2 / +15.8 / +6.4 / +5.2 | +14.7 / +19.9 / +16.2 / +4.9 / +5.9 | +25.5* / +27.8* / +23.4* / +8.1 / +8.0 | +9.1 / +15.3 / +12.2 / +6.9 / +7.4 | +9.6 / +17.2 / +13.9 / +6.0 / +5.0 |
| 15R | +13.4 / +19.7 / +16.2 / +6.3 / +5.2 | +14.4 / +20.0 / +16.3 / +5.0 / +5.9 | +25.2* / +27.9* / +23.5* / +8.0 / +8.0 | +8.8 / +15.4 / +12.4 / +6.8 / +7.4 | +9.6 / +17.7 / +14.4 / +5.9 / +5.0 |

### 8. Pair: entry win x entry loss, combined 12R

**C minus A0 (as-is as it is)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| win \ loss | off | 1R | 2R | 3R |
|---|---|---|---|---|
| off | +15.6 / +15.6 / +14.6 / +0.7 / +2.7 | -6.3 / -3.3 / -1.8 / -0.5 / +1.9 | +18.1 / +16.4 / +15.2 / +0.2 / +2.3 | +15.3 / +15.3 / +14.3 / +0.6 / +2.6 |
| 3R | +16.5 / +16.4 / +15.3 / -0.3 / +2.7 | -1.1 / +0.0 / +1.1 / -2.3 / +2.0 | +19.0 / +17.2 / +15.9 / -0.9 / +2.3 | +16.1 / +16.1 / +14.9 / +0.1 / +2.6 |
| 5R | +15.3 / +15.7 / +14.7 / +0.8 / +2.7 | -6.6 / -3.4 / -1.9 / -0.7 / +1.9 | +17.9 / +16.5 / +15.3 / +0.3 / +2.3 | +15.0 / +15.3 / +14.4 / +0.7 / +2.6 |
| 8R | +15.6 / +15.6 / +14.6 / +0.7 / +2.7 | -6.3 / -3.3 / -1.8 / -0.4 / +1.9 | +18.1 / +16.4 / +15.2 / +0.2 / +2.3 | +15.3 / +15.3 / +14.3 / +0.6 / +2.6 |

**C(s) minus A(s) (same settings both)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| win \ loss | off | 1R | 2R | 3R |
|---|---|---|---|---|
| off | +28.7* / +28.2* / +23.7* / +10.3 / +5.9 | +7.9 / +10.8 / +7.1 / +5.9 / +7.0 | +26.5* / +28.0* / +23.6* / +8.0 / +8.0 | +24.5 / +25.3* / +21.2 / +8.8 / +5.9 |
| 3R | +31.3* / +33.6* / +28.2* / +10.4 / +5.8 | +13.7 / +14.5 / +10.2 / +6.8 / +7.0 | +28.0* / +29.4* / +24.7* / +8.4 / +7.9 | +25.0 / +26.2* / +21.8 / +9.1 / +5.8 |
| 5R | +27.5* / +28.0* / +23.5* / +10.5 / +5.9 | +7.2 / +10.6 / +6.9 / +5.7 / +7.0 | +25.5* / +27.8* / +23.4* / +8.1 / +8.0 | +22.5 / +24.6* / +20.6 / +9.1 / +5.9 |
| 8R | +28.5* / +28.1* / +23.6* / +10.3 / +5.9 | +7.7 / +10.8 / +7.1 / +5.9 / +7.0 | +26.3* / +27.9* / +23.5* / +8.0 / +8.0 | +24.3 / +25.2* / +21.1 / +8.8 / +5.9 |

### 7. Pair: per-book week floor x day arm (keep 50%), combined off

**C minus A0 (as-is as it is)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| floor \ arm R | off | 1.5R | 2R | 2.5R | 3R |
|---|---|---|---|---|---|
| off | +21.3 / +21.1* / +18.8* / +3.4 / +12.7 | +17.4 / +18.6* / +16.1 / +5.8 / +14.0 | +23.7* / +22.3* / +19.2* / +7.0 / +13.7 | +15.6 / +17.7 / +15.8 / +4.9 / +13.2 | +17.6 / +19.2* / +17.0* / +5.2 / +12.9 |
| 8R | +20.0 / +19.8* / +17.7 / +3.0 / +11.5 | +15.7 / +17.4 / +14.9 / +3.2 / +13.3 | +22.4 / +21.3* / +18.2* / +5.4 / +12.6 | +14.3 / +16.6 / +14.7 / +3.3 / +12.0 | +15.9 / +17.8 / +15.7 / +3.7 / +11.7 |
| 10R | +21.4 / +20.7* / +18.1* / +2.5 / +11.8 | +17.0 / +18.1* / +15.4 / +3.6 / +13.2 | +24.1* / +22.3* / +18.9* / +5.6 / +12.9 | +15.7 / +17.5 / +15.2 / +3.5 / +12.4 | +17.3 / +18.6* / +16.1 / +3.7 / +12.0 |
| 12R | +22.1 / +21.0* / +18.7* / +4.3 / +12.2 | +17.9 / +18.5* / +15.7 / +5.5 / +13.9 | +24.3* / +22.3* / +18.9* / +7.0 / +13.4 | +16.0 / +17.6 / +15.7 / +5.3 / +12.8 | +18.0 / +18.8* / +16.7* / +5.5 / +12.4 |
| 15R | +21.3 / +21.1* / +18.8* / +4.7 / +12.5 | +17.4 / +18.6* / +16.1 / +5.9 / +13.9 | +23.7* / +22.3* / +19.2* / +7.3 / +13.6 | +15.6 / +17.7 / +15.7 / +5.6 / +13.1 | +17.6 / +19.2* / +16.9* / +5.8 / +12.8 |

**C(s) minus A(s) (same settings both)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| floor \ arm R | off | 1.5R | 2R | 2.5R | 3R |
|---|---|---|---|---|---|
| off | +18.1 / +18.9 / +16.6 / +7.6 / +12.7 | +20.6 / +18.6* / +16.5 / +7.6 / +12.8 | +23.7* / +22.3* / +19.2* / +7.0 / +13.7 | +14.0 / +16.6 / +14.6 / +7.7 / +13.0 | +18.1 / +19.5* / +16.8 / +7.9 / +12.3 |
| 8R | +16.4 / +17.4 / +15.3 / +8.9 / +11.5 | +19.0 / +17.3 / +15.4 / +6.0 / +12.1 | +22.1 / +21.1* / +18.0* / +6.6 / +12.6 | +12.2 / +15.3 / +13.4 / +7.4 / +11.9 | +16.1 / +17.9 / +15.4 / +7.7 / +11.0 |
| 10R | +18.3 / +18.5 / +16.0 / +6.7 / +11.8 | +20.3 / +18.1* / +15.8 / +5.4 / +12.0 | +24.2* / +22.3* / +18.9* / +5.6 / +12.9 | +14.0 / +16.3 / +14.1 / +6.3 / +12.2 | +17.8 / +18.9* / +16.0 / +6.4 / +11.4 |
| 12R | +18.9 / +18.8 / +16.5 / +8.6 / +12.3 | +21.2 / +18.5* / +16.1 / +7.2 / +12.7 | +24.3* / +22.3* / +18.9* / +7.0 / +13.4 | +14.4 / +16.5 / +14.5 / +8.1 / +12.7 | +18.4 / +19.2* / +16.5 / +8.2 / +11.8 |
| 15R | +18.1 / +18.9 / +16.6 / +9.0 / +12.6 | +20.6 / +18.6* / +16.5 / +7.7 / +12.7 | +23.7* / +22.3* / +19.2* / +7.3 / +13.6 | +14.0 / +16.6 / +14.5 / +8.4 / +12.9 | +18.1 / +19.5* / +16.8 / +8.5 / +12.2 |

### 8. Pair: entry win x entry loss, combined off

**C minus A0 (as-is as it is)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| win \ loss | off | 1R | 2R | 3R |
|---|---|---|---|---|
| off | +23.0* / +22.8* / +19.1* / +6.6 / +14.3 | +13.4 / +11.6 / +10.7 / +4.3 / +12.1 | +24.5* / +22.1* / +18.7* / +7.0 / +13.4 | +21.8* / +22.0* / +18.6* / +8.5 / +14.0 |
| 3R | +23.8* / +23.5* / +19.7* / +5.2 / +14.1 | +14.5 / +12.4 / +11.4 / +3.1 / +12.0 | +25.3* / +22.9* / +19.3* / +5.3 / +13.3 | +22.7* / +22.7* / +19.3* / +6.9 / +13.8 |
| 5R | +22.8* / +22.9* / +19.2* / +6.7 / +14.3 | +13.3 / +11.8 / +10.9 / +4.1 / +12.1 | +24.3* / +22.3* / +18.9* / +7.0 / +13.4 | +21.6* / +22.1* / +18.8* / +8.5 / +14.0 |
| 8R | +23.0* / +22.8* / +19.1* / +6.6 / +14.3 | +13.4 / +11.6 / +10.7 / +4.4 / +12.1 | +24.5* / +22.1* / +18.7* / +7.0 / +13.4 | +21.8* / +22.0* / +18.6* / +8.5 / +14.0 |

**C(s) minus A(s) (same settings both)**, cell = L3M / L6M / HOLD / PRE / X' $k/wk (* beyond MDE)
| win \ loss | off | 1R | 2R | 3R |
|---|---|---|---|---|
| off | +34.3* / +27.6* / +24.1* / +8.1 / +9.6 | +25.7 / +23.0* / +18.1 / +7.9 / +18.3* | +26.2* / +23.0* / +19.5* / +7.2 / +13.5 | +24.7 / +22.8* / +20.0* / +7.8 / +9.6 |
| 3R | +35.1* / +28.2* / +24.4* / +9.2 / +9.2 | +27.2 / +24.1* / +18.9 / +9.6 / +18.0* | +27.0* / +23.6* / +19.8* / +8.1 / +13.2 | +25.5* / +23.4* / +20.4* / +8.8 / +9.3 |
| 5R | +32.3* / +26.9* / +23.4* / +8.0 / +9.4 | +24.3 / +22.5* / +17.7 / +7.4 / +18.1* | +24.3* / +22.3* / +18.9* / +7.0 / +13.4 | +22.7 / +22.1* / +19.4* / +7.6 / +9.5 |
| 8R | +34.1* / +27.5* / +24.0* / +8.1 / +9.6 | +25.5 / +22.9* / +18.0 / +7.9 / +18.3* | +26.0* / +22.9* / +19.4* / +7.2 / +13.5 | +24.5 / +22.7* / +20.0* / +7.8 / +9.6 |

### 9. Lock-off placebo (all locks off: no entry test, no day arm, no week floor, no combined)

**Composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | 34.6 | 46.0 | 43.1 | 21.1 | 10.0 |
| D6 per-book locks (no combined) | 38.1 | 46.3 | 42.6 | 24.7 | 9.8 |
| D6 per-book + combined 12R | 31.7 | 40.5 | 39.1 | 18.0 | -1.3 |

**Composite: setting minus all-locks-off**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| D6 per-book locks (no combined) | +3.5 | +0.4 | -0.5 | +3.7 | -0.2 |
| D6 per-book + combined 12R | -2.9 | -5.5 | -4.0 | -3.0 | -11.3 |

**As-is: setting minus all-locks-off**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| D6 per-book locks (no combined) | +9.8 | +3.7 | +3.9 | +5.8 | -4.4 |
| D6 per-book + combined 12R | +2.2 | -7.5 | -4.2 | -2.0 | -10.1 |

**Composite C minus as-is A, same settings**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | +30.6 | +25.7* | +23.2* | +9.2 | +9.2 |
| D6 per-book locks (no combined) | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| D6 per-book + combined 12R | +25.5* | +27.8* | +23.4* | +8.1 | +8.0 |

**Composite C minus A0**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | +20.8 | +22.0* | +19.4* | +3.4 | +13.6 |
| D6 per-book locks (no combined) | +24.3* | +22.3* | +18.9* | +7.0 | +13.4 |
| D6 per-book + combined 12R | +17.9 | +16.5 | +15.3 | +0.3 | +2.3 |

**Composite mean $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | 34.6 | 46.0 | 43.1 | 21.1 | 10.0 |
| D6 per-book locks (no combined) | 38.1 | 46.3 | 42.6 | 24.7 | 9.8 |
| D6 per-book + combined 12R | 31.7 | 40.5 | 39.1 | 18.0 | -1.3 |

**Composite SD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | 58.6 | 52.0 | 60.7 | 71.1 | 36.2 |
| D6 per-book locks (no combined) | 46.9 | 45.4 | 55.5 | 58.1 | 34.0 |
| D6 per-book + combined 12R | 51.3 | 50.7 | 53.9 | 52.6 | 28.7 |

**Composite maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | 50.0 | 50.0 | 102.2 | 319.5 | 142.1 |
| D6 per-book locks (no combined) | 20.6 | 20.6 | 113.4 | 262.7 | 125.7 |
| D6 per-book + combined 12R | 28.1 | 28.1 | 28.1 | 274.3 | 213.7 |

**Composite mean worst 20 wk $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | 34.6 | 18.8 | 5.7 | -66.5 | -21.6 |
| D6 per-book locks (no combined) | 38.1 | 22.0 | 9.0 | -45.6 | -19.8 |
| D6 per-book + combined 12R | 31.7 | 13.9 | 3.7 | -32.9 | -21.7 |

**As-is mean $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | 4.0 | 20.3 | 19.8 | 11.9 | 0.8 |
| D6 per-book locks (no combined) | 13.8 | 24.0 | 23.7 | 17.7 | -3.6 |
| D6 per-book + combined 12R | 6.2 | 12.7 | 15.6 | 9.9 | -9.3 |

**As-is maxDD $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | 142.8 | 142.8 | 168.5 | 288.4 | 231.9 |
| D6 per-book locks (no combined) | 91.8 | 91.8 | 143.7 | 209.7 | 317.2 |
| D6 per-book + combined 12R | 108.0 | 116.5 | 116.5 | 268.1 | 526.2 |

**As-is mean worst 20 wk $k**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ALL locks OFF | 4.0 | -9.1 | -23.2 | -69.7 | -26.8 |
| D6 per-book locks (no combined) | 13.8 | 3.4 | -8.9 | -43.7 | -29.4 |
| D6 per-book + combined 12R | 6.2 | -12.4 | -21.2 | -29.3 | -29.3 |

### 10. Composite with K6 at market / others 70-30 (the decision number), combined multiple

**K6-market composite mean $k/wk**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | 35.8 | 45.6 | 42.2 | 24.2 | 10.0 |
| 6R | 3.8 | 15.2 | 17.9 | 6.7 | -6.4 |
| 8R | 25.4 | 32.1 | 32.5 | 10.4 | -6.1 |
| 10R | 30.5 | 34.3 | 33.9 | 15.9 | -5.8 |
| 12R | 29.8 | 40.0 | 38.8 | 18.6 | -2.2 |
| 15R | 29.1 | 41.4 | 39.8 | 17.6 | -0.4 |
| 20R | 24.7 | 39.0 | 35.7 | 16.4 | 4.7 |
| 30R | 35.5 | 44.1 | 42.1 | 15.0 | 6.9 |
| 50R | 35.8 | 45.6 | 42.3 | 19.4 | 10.2 |

**K6-market composite minus A0**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +22.0* | +21.6* | +18.5* | +6.5 | +13.5 |
| 6R | -10.0 | -8.8 | -5.8 | -11.0 | -2.8 |
| 8R | +11.6 | +8.1 | +8.8 | -7.3 | -2.5 |
| 10R | +16.7 | +10.2 | +10.2 | -1.8 | -2.2 |
| 12R | +16.0 | +16.0 | +15.1 | +0.9 | +1.4 |
| 15R | +15.3 | +17.4 | +16.1 | -0.1 | +3.2 |
| 20R | +10.9 | +15.0 | +12.0 | -1.3 | +8.3 |
| 30R | +21.6* | +20.1* | +18.3* | -2.7 | +10.5 |
| 50R | +22.0* | +21.6* | +18.6* | +1.7 | +13.8 |

**K6-market composite minus as-is with same settings**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +22.0* | +21.6* | +18.5* | +6.5 | +13.5 |
| 6R | +6.1 | +9.6 | +10.3 | +4.7 | +2.0 |
| 8R | +26.8 | +22.5 | +22.0 | +6.1 | +4.9 |
| 10R | +22.7* | +19.9 | +19.7 | +7.3 | +3.2 |
| 12R | +23.6* | +27.3* | +23.1* | +8.7 | +7.1 |
| 15R | +20.5* | +27.3* | +23.7* | +8.3 | +10.6 |
| 20R | +7.8 | +18.0 | +13.9 | +3.3 | +13.1 |
| 30R | +20.2 | +19.4* | +17.5* | -0.3 | +10.5 |
| 50R | +22.0* | +21.6* | +18.6* | +2.1 | +13.8 |

**Combined lock effect on K6-market composite**
| setting | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| off | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 |
| 6R | -32.0 | -30.4* | -24.3 | -17.5* | -16.3* |
| 8R | -10.4 | -13.6 | -9.7 | -13.8 | -16.1* |
| 10R | -5.3 | -11.4 | -8.3 | -8.3 | -15.8* |
| 12R | -6.0 | -5.6 | -3.4 | -5.6 | -12.2* |
| 15R | -6.7 | -4.2 | -2.4 | -6.6 | -10.3 |
| 20R | -11.1 | -6.6 | -6.5 | -7.8 | -5.2 |
| 30R | -0.4 | -1.6 | -0.2 | -9.2 | -3.1 |
| 50R | +0.0 | +0.0 | +0.1 | -4.7 | +0.3 |
