# SZ_CDE_TRAIL2 - T-TRAIL-L2 items 2 and 3: STATE-ADAPTIVE trail distance and the PROFIT CUT (loss-cut mirror), seven books (SZ-CDE) - 2026-11-10 17:53Z

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. FIRST-ORDER on the shared PTR engine (LPB_BASE trade list, slip 1.2, equal lots, stack = LPB_BASE with the book's fired trades replaced; re-entries/locks not re-simulated: ranking only). Windows L1M/L3M/L6M/HOLD/PRE/X-prime; equal-MEAN cut = stack maxDD cut at lots rescaled to the live L6M mean; placebo = random exit at the same arm pct and count (100 draws) with own-draw p and the family null over the top-100 cells of the family; bi-weekly WF vs LPB_BASE; Rule 2a label via Z.prior_info [old fixed-floor label beside].**

**Item 2, adaptive trail** (code/th_ptr/ptr_adapt.py, kernel action 5 already in ptr_kern): trail = max(trail, fav - X0 x clip((ahead_rel / behind_rel)^p, lo, hi)) every second once armed (ratchets only in the trade's favour); p < 0 = THICK AHEAD -> TIGHTER and THICK BEHIND -> WIDER (the order's direction), p = 0 is the fixed tighten X0 (reference), p > 0 the opposite. Grid per book: arm 0.2-0.9 x X0 {5,10,15,20,30,40} x p {-1,-.5,-.25,0,.25,.5,1} x (lo,hi) {(.25,3),(.5,2)} x baseline {fast, slow} = 1,248 cells. The grammar text form is an extension (`profit B * pct>=A adapt X0 p=.. lo=.. hi=.. tag=f|s persist=P`, parser ptr_adapt.parse); exact promotion needs the hook to call ptr_kern action 5 (the kernel is shared, so the engine hook can run it; the text parser is the only missing piece: REDO-R5 informed).

**Item 3, profit cut** (the loss cut mirrored on a winner): `profit <book> * pct>=A pulled_mult>=MULT secs_fav<=S take win=W persist=P` = own-side support leaving (net cancels / MedLevel) at a NEW favourable extreme (secs_fav <= S) -> exit. First the loss cut's live values (MULT 30, win 5, persist 5, secs_fav <= 5) at each arm = "live mirror" rows, then the grid: arm 0.2-0.9 x MULT {3,5,10,20,30,50,100,200} x win {2,3,5,8,10,15} x persist {1,2,3,5,10} x secs_fav<= {2,5,10} = 5,760 cells per book.


## K7


## Summary

| book | best fixed trail: L6M cut / eq-mean | best adaptive trail: L6M cut / eq-mean (delta vs fixed) | best profit cut: L6M / PRE / eq-mean L6M / d mean L6M | profit-cut placebo p own L6M / PRE | best live-mirror row L6M cut |
|--|--|--|--|--|--|
| K7 | +29.2 / +28.1 | +30.5 / +28.9 (+1.3) | +28.7 / +2.9 / +25.3 / -932 | 0.01 / 0.08 | +0.0 |
| P7 | +53.2 / +50.5 | +51.3 / +47.6 (-1.9) | +66.3 / +40.9 / +68.8 / +1271 | 0.01 / 0.02 | +0.0 |
| U7 | +19.3 / +17.7 | +19.1 / +22.5 (-0.1) | +28.8 / +10.8 / +32.3 / +1101 | 0.01 / 0.25 | +0.0 |
| H7 | +6.3 / +4.1 | +4.0 / -0.1 (-2.3) | +14.3 / -13.3 / +8.9 / -1258 | 0.01 / 0.97 | +0.0 |
| M7 | +28.8 / +26.8 | +29.9 / +28.0 (+1.1) | +32.2 / -3.7 / +30.4 / -486 | 0.01 / 0.79 | +0.0 |
| A7 | +7.3 / +5.3 | +8.1 / +6.0 (+0.8) | +13.0 / +1.3 / +12.7 / -67 | 0.02 / 0.30 | +0.0 |
| O7 | +3.4 / +2.5 | +3.5 / +2.7 (+0.1) | +4.4 / -0.6 / +4.6 / +38 | 0.01 / 0.89 | +0.0 |

### Item 2: adaptive trail vs the fixed trail (same grid)

Best fixed tighten (p=0): `profit K7 * pct>=0.6 adapt 30 p=0 lo=0.25 hi=3 tag=s persist=1` L6M cut +29.2, equal-mean +28.1, d mean -325. Best adaptive overall: `profit K7 * pct>=0.6 adapt 40 p=0.25 lo=0.25 hi=3 tag=s persist=1` L6M cut +30.5, equal-mean +28.9, d mean -465. Best in the ORDER's direction (p<0, thick ahead tighter): `profit K7 * pct>=0.6 adapt 30 p=-0.25 lo=0.25 hi=3 tag=f persist=1` L6M cut +30.4, equal-mean +31.3, d mean +209. Difference adaptive minus fixed: +1.3 points of L6M stack maxDD cut (positive = the state-dependent distance helps).

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit K7 * pct>=0.6 adapt 40 p=0.25 lo=0.25 hi=3 tag=f persist=1` | 1976 | +30.5 / +30.5 / +9.6 | +1.4 | +6.6 | -1.1 | +28.9 / +4.4 | -465 / -946 | +19.8 | 0.01 / 0.20 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit K7 * pct>=0.6 adapt 40 p=0.25 lo=0.25 hi=3 tag=s persist=1` | 1976 | +30.5 / +30.5 / +9.6 | +1.4 | +6.6 | -1.1 | +28.9 / +4.4 | -465 / -946 | +19.8 | 0.01 / 0.20 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit K7 * pct>=0.6 adapt 40 p=0.25 lo=0.5 hi=2 tag=f persist=1` | 1976 | +30.5 / +30.5 / +9.6 | +1.4 | +6.6 | -1.1 | +28.8 / +4.4 | -471 / -947 | +19.9 | 0.01 / 0.20 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit K7 * pct>=0.6 adapt 30 p=-0.25 lo=0.25 hi=3 tag=f persist=1` | 2299 | +30.4 / +30.4 / +7.4 | +1.5 | +10.1 | +4.2 | +31.3 / +11.2 | +209 / -1002 | +15.4 | 0.01 / 0.07 | 1.00 | 32 | OK-PRIOR [RECENT-ONLY] |
| 5 | `profit K7 * pct>=0.6 adapt 30 p=-0.25 lo=0.25 hi=3 tag=s persist=1` | 2299 | +30.4 / +30.4 / +7.4 | +1.5 | +10.1 | +4.2 | +31.3 / +11.2 | +206 / -1002 | +15.4 | 0.01 / 0.07 | 1.00 | 32 | OK-PRIOR [RECENT-ONLY] |
| 6 | `profit K7 * pct>=0.6 adapt 30 p=-0.25 lo=0.5 hi=2 tag=f persist=1` | 2298 | +30.4 / +30.4 / +7.2 | +2.3 | +10.1 | +4.2 | +31.2 / +11.2 | +199 / -1002 | +15.2 | 0.01 / 0.16 | 1.00 | 32 | OK-PRIOR [RECENT-ONLY] |
| 7 | `profit K7 * pct>=0.6 adapt 30 p=0 lo=0.25 hi=3 tag=f persist=1` | 2000 | +29.2 / +29.2 / +11.0 | -2.0 | +9.7 | -0.8 | +28.1 / +8.2 | -325 / -989 | +20.4 | 0.03 / 0.07 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit K7 * pct>=0.6 adapt 30 p=0 lo=0.25 hi=3 tag=s persist=1` | 2000 | +29.2 / +29.2 / +11.0 | -2.0 | +9.7 | -0.8 | +28.1 / +8.2 | -325 / -989 | +20.4 | 0.03 / 0.07 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit K7 * pct>=0.6 adapt 40 p=-0.25 lo=0.25 hi=3 tag=f persist=1` | 1957 | +29.4 / +29.4 / +9.5 | -2.5 | +7.1 | -0.1 | +27.4 / +4.6 | -543 / -1064 | +15.9 | 0.02 / 0.25 | 1.00 | 24 | OK-PRIOR [RECENT-ONLY] |
| 10 | `profit K7 * pct>=0.6 adapt 40 p=-0.25 lo=0.25 hi=3 tag=s persist=1` | 1957 | +29.4 / +29.4 / +9.5 | -2.5 | +7.1 | -0.1 | +27.4 / +4.6 | -544 / -1064 | +15.8 | 0.02 / 0.25 | 1.00 | 24 | OK-PRIOR [RECENT-ONLY] |
| 11 | `profit K7 * pct>=0.6 adapt 40 p=-0.25 lo=0.5 hi=2 tag=f persist=1` | 1956 | +29.4 / +29.4 / +9.4 | -2.5 | +7.1 | -0.1 | +27.4 / +4.5 | -551 / -1064 | +15.7 | 0.04 / 0.31 | 1.00 | 24 | OK-PRIOR [RECENT-ONLY] |
| 12 | `profit K7 * pct>=0.6 adapt 40 p=-0.5 lo=0.5 hi=2 tag=f persist=1` | 2214 | +29.4 / +29.4 / +8.4 | +2.9 | +9.3 | +2.1 | +30.0 / +10.1 | +142 / -956 | +15.2 | 0.01 / 0.13 | 1.00 | 33 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit K7 * pct>=0.6 adapt 40 p=-0.5 lo=0.5 hi=2 tag=s persist=1` | 2214 | +29.4 / +29.4 / +8.4 | +2.9 | +9.3 | +2.1 | +30.0 / +10.0 | +140 / -955 | +15.1 | 0.01 / 0.13 | 1.00 | 33 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit K7 * pct>=0.6 adapt 40 p=-0.5 lo=0.25 hi=3 tag=f persist=1` | 2252 | +28.1 / +28.1 / +7.8 | +2.5 | +9.5 | +0.8 | +28.2 / +9.6 | +30 / -955 | +12.4 | 0.02 / 0.15 | 1.00 | 30 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit K7 * pct>=0.6 adapt 30 p=0.25 lo=0.25 hi=3 tag=f persist=1` | 2330 | +27.2 / +27.2 / +9.2 | +2.6 | +10.6 | +2.7 | +25.1 / +8.0 | -567 / -1045 | +16.1 | 0.03 / 0.10 | 1.00 | 32 | OK-PRIOR [RECENT-ONLY] |
| 16 | `profit K7 * pct>=0.6 adapt 30 p=0.25 lo=0.5 hi=2 tag=f persist=1` | 2330 | +27.2 / +27.2 / +9.2 | +2.6 | +10.6 | +2.7 | +25.1 / +8.0 | -572 / -1045 | +16.2 | 0.03 / 0.10 | 1.00 | 32 | OK-PRIOR [RECENT-ONLY] |
| 17 | `profit K7 * pct>=0.6 adapt 30 p=0.25 lo=0.25 hi=3 tag=s persist=1` | 2330 | +27.2 / +27.2 / +9.2 | +2.6 | +10.6 | +2.7 | +25.1 / +8.0 | -569 / -1045 | +16.1 | 0.03 / 0.10 | 1.00 | 32 | OK-PRIOR [RECENT-ONLY] |
| 18 | `profit K7 * pct>=0.6 adapt 40 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 2311 | +27.2 / +27.2 / +8.8 | +3.0 | +8.4 | +0.5 | +24.6 / +5.1 | -696 / -979 | +15.5 | 0.03 / 0.17 | 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit K7 * pct>=0.6 adapt 40 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 2310 | +27.2 / +27.2 / +8.8 | +3.0 | +9.2 | +0.5 | +24.6 / +6.0 | -704 / -965 | +15.3 | 0.04 / 0.18 | 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit K7 * pct>=0.6 adapt 30 p=-0.5 lo=0.5 hi=2 tag=f persist=1` | 2553 | +27.5 / +27.5 / +6.5 | +3.4 | +8.4 | +3.4 | +23.8 / +3.6 | -781 / -1280 | +10.3 | 0.01 / 0.15 | 1.00 | 19 | OK-PRIOR [RECENT-ONLY] |

### Item 3: profit cut

Live-mirror rows (MULT 30, win 5, persist 5, secs_fav <= 5, by arm): arm 0.2: fires 30, L6M cut +0.0, PRE cut +0.0, d mean L6M -94; arm 0.3: fires 24, L6M cut +0.0, PRE cut +0.0, d mean L6M -77; arm 0.4: fires 20, L6M cut +0.0, PRE cut +0.0, d mean L6M -139; arm 0.5: fires 14, L6M cut +0.0, PRE cut +0.0, d mean L6M -51; arm 0.6: fires 10, L6M cut +0.0, PRE cut +0.0, d mean L6M -46; arm 0.7: fires 8, L6M cut +0.0, PRE cut +0.0, d mean L6M -18; arm 0.8: fires 5, L6M cut +0.0, PRE cut +0.0, d mean L6M -10; arm 0.9: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit K7 * pct>=0.5 pulled_mult>=10 secs_fav<=5 take win=15 persist=10 wall_ticks=8` | 3241 | +28.7 / +28.7 / +10.3 | -0.3 | +2.9 | -2.0 | +25.3 / -1.7 | -932 / -969 | +5.9 | 0.01 / 0.08 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit K7 * pct>=0.5 pulled_mult>=10 secs_fav<=10 take win=5 persist=5 wall_ticks=8` | 3134 | +25.5 / +25.5 / +9.8 | +4.4 | +6.6 | +1.9 | +23.8 / +4.4 | -458 / -1184 | +17.0 | 0.03 / 0.04 | 0.79 | 39 | OK-PRIOR [RECENT-ONLY] |
| 3 | `profit K7 * pct>=0.5 pulled_mult>=3 secs_fav<=5 take win=10 persist=10 wall_ticks=8` | 3817 | +25.1 / +25.1 / +9.6 | -1.8 | +2.0 | +8.4 | +20.7 / -3.7 | -1129 / -1329 | +3.6 | 0.02 / 0.09 | 0.97 | 30 | OK-PRIOR [RECENT-ONLY] |
| 4 | `profit K7 * pct>=0.5 pulled_mult>=5 secs_fav<=5 take win=15 persist=10 wall_ticks=8` | 3837 | +24.9 / +24.9 / +9.5 | -2.9 | +2.0 | +2.0 | +20.1 / -4.3 | -1227 / -1277 | +2.6 | 0.03 / 0.06 | 0.96 | 28 | OK-PRIOR [RECENT-ONLY] |
| 5 | `profit K7 * pct>=0.5 pulled_mult>=3 secs_fav<=5 take win=15 persist=10 wall_ticks=8` | 3889 | +24.9 / +24.9 / +9.5 | -2.9 | +1.7 | +9.1 | +20.5 / -4.1 | -1140 / -1262 | +2.1 | 0.01 / 0.04 | 0.85 | 32 | OK-PRIOR [RECENT-ONLY] |
| 6 | `profit K7 * pct>=0.5 pulled_mult>=10 secs_fav<=2 take win=10 persist=3 wall_ticks=8` | 3476 | +25.6 / +25.6 / +4.9 | +4.7 | -1.2 | -3.1 | +23.1 / -4.7 | -638 / -1495 | +9.0 | 0.02 / 0.24 | 1.00 | 20 | OK-PRIOR [RECENT-ONLY] |
| 7 | `profit K7 * pct>=0.5 pulled_mult>=10 secs_fav<=2 take win=10 persist=5 wall_ticks=8` | 2580 | +26.0 / +26.0 / +3.3 | +6.5 | -5.3 | +4.6 | +22.0 / -11.1 | -1063 / -845 | +3.0 | 0.02 / 0.64 | 1.00 | 28 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit K7 * pct>=0.5 pulled_mult>=3 secs_fav<=10 take win=2 persist=5 wall_ticks=8` | 2739 | +25.2 / +25.2 / +5.3 | -3.3 | +14.1 | -0.3 | +22.6 / +11.2 | -669 / -904 | +14.2 | 0.04 / 0.01 | 0.58 | 23 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit K7 * pct>=0.5 pulled_mult>=10 secs_fav<=5 take win=10 persist=5 wall_ticks=8` | 3572 | +24.7 / +24.7 / +5.6 | +5.2 | +1.9 | -5.7 | +24.6 / +1.8 | -4 / -1335 | +3.8 | 0.01 / 0.15 | 1.00 | 37 | OK-PRIOR [RECENT-ONLY] |
| 10 | `profit K7 * pct>=0.5 pulled_mult>=10 secs_fav<=2 take win=8 persist=3 wall_ticks=8` | 2870 | +24.4 / +24.4 / +6.1 | +6.7 | +5.4 | +7.2 | +22.0 / +2.5 | -590 / -883 | +15.7 | 0.05 / 0.13 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit K7 * pct>=0.6 pulled_mult>=10 secs_fav<=5 take win=5 persist=1 wall_ticks=8` | 3488 | +24.4 / +24.4 / +5.5 | -0.7 | +10.3 | -7.5 | +20.5 / +5.8 | -984 / -1232 | +7.3 | 0.11 / 0.08 | 1.00 | 28 | OK-PRIOR [RECENT-ONLY] |
| 12 | `profit K7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=8 persist=5 wall_ticks=8` | 3437 | +24.0 / +24.0 / +6.9 | +5.7 | -6.5 | -3.5 | +19.4 / -12.9 | -894 / -1071 | +3.2 | 0.04 / 0.64 | 1.00 | 34 | OK-PRIOR [RECENT-ONLY] |
| 13 | `profit K7 * pct>=0.6 pulled_mult>=10 secs_fav<=2 take win=8 persist=1 wall_ticks=8` | 3510 | +24.0 / +24.0 / +6.2 | -0.4 | +10.0 | -1.6 | +20.1 / +5.4 | -998 / -1317 | +10.7 | 0.07 / 0.10 | 1.00 | 29 | OK-PRIOR [RECENT-ONLY] |
| 14 | `profit K7 * pct>=0.5 pulled_mult>=10 secs_fav<=5 take win=8 persist=3 wall_ticks=8` | 3744 | +24.6 / +24.6 / +3.3 | +3.3 | -5.7 | -3.2 | +25.9 / -3.9 | +304 / -1588 | +11.1 | 0.02 / 0.58 | 1.00 | 29 | OK-PRIOR [RECENT-ONLY] |
| 15 | `profit K7 * pct>=0.5 pulled_mult>=20 secs_fav<=10 take win=15 persist=5 wall_ticks=8` | 3363 | +24.1 / +24.1 / +5.0 | +6.0 | +2.7 | +0.5 | +20.4 / -2.1 | -917 / -1036 | +0.8 | 0.07 / 0.06 | 1.00 | 33 | OK-PRIOR [RECENT-ONLY] |
| 16 | `profit K7 * pct>=0.5 pulled_mult>=5 secs_fav<=5 take win=5 persist=10 wall_ticks=8` | 1368 | +20.0 / +20.0 / +19.6 | +11.7 | +5.9 | -2.5 | +19.9 / +5.8 | -36 / -418 | +18.7 | 0.03 / 0.16 | 1.00 | 14 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit K7 * pct>=0.6 pulled_mult>=10 secs_fav<=10 take win=5 persist=1 wall_ticks=8` | 3613 | +23.8 / +23.8 / +4.1 | -1.4 | +10.5 | -9.7 | +19.8 / +5.7 | -1035 / -1102 | +5.7 | 0.06 / 0.05 | 0.98 | 27 | OK-PRIOR [RECENT-ONLY] |
| 18 | `profit K7 * pct>=0.5 pulled_mult>=5 secs_fav<=5 take win=10 persist=10 wall_ticks=8` | 3487 | +22.1 / +22.1 / +9.8 | -0.8 | +5.0 | -4.1 | +20.6 / +3.2 | -311 / -1236 | +4.6 | 0.08 / 0.07 | 1.00 | 27 | OK-PRIOR [RECENT-ONLY] |
| 19 | `profit K7 * pct>=0.6 pulled_mult>=5 secs_fav<=2 take win=5 persist=1 wall_ticks=8` | 3863 | +23.2 / +23.2 / +5.3 | -1.9 | +7.5 | -3.9 | +20.4 / +4.1 | -683 / -1507 | +13.1 | 0.03 / 0.07 | 1.00 | 22 | OK-PRIOR [RECENT-ONLY] |
| 20 | `profit K7 * pct>=0.5 pulled_mult>=5 secs_fav<=5 take win=8 persist=5 wall_ticks=8` | 4071 | +23.4 / +23.4 / +3.8 | +5.3 | -2.2 | +4.5 | +23.2 / -2.5 | -49 / -1682 | -0.0 | 0.01 / 0.21 | 1.00 | 32 | OK-PRIOR [RECENT-ONLY] |


## P7

### Item 2: adaptive trail vs the fixed trail (same grid)

Best fixed tighten (p=0): `profit P7 * pct>=0.7 adapt 5 p=0 lo=0.25 hi=3 tag=f persist=1` L6M cut +53.2, equal-mean +50.5, d mean -1074. Best adaptive overall: `profit P7 * pct>=0.7 adapt 10 p=1 lo=0.5 hi=2 tag=f persist=1` L6M cut +51.3, equal-mean +47.6, d mean -1398. Best in the ORDER's direction (p<0, thick ahead tighter): `profit P7 * pct>=0.7 adapt 5 p=-1 lo=0.25 hi=3 tag=s persist=1` L6M cut +50.7, equal-mean +50.0, d mean -263. Difference adaptive minus fixed: -1.9 points of L6M stack maxDD cut (positive = the state-dependent distance helps).

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit P7 * pct>=0.7 adapt 5 p=0 lo=0.25 hi=3 tag=f persist=1` | 2380 | +53.2 / +53.2 / +29.5 | +11.2 | +19.3 | +31.3 | +50.5 / +14.7 | -1074 / -244 | +59.3 | 0.06 / 0.35 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit P7 * pct>=0.7 adapt 5 p=0 lo=0.25 hi=3 tag=s persist=1` | 2380 | +53.2 / +53.2 / +29.5 | +11.2 | +19.3 | +31.3 | +50.5 / +14.7 | -1074 / -244 | +59.3 | 0.06 / 0.35 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit P7 * pct>=0.7 adapt 10 p=1 lo=0.5 hi=2 tag=f persist=1` | 2320 | +51.3 / +51.3 / +29.3 | +9.1 | +20.3 | +28.4 | +47.6 / +14.3 | -1398 / -360 | +51.9 | 0.23 / 0.32 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit P7 * pct>=0.7 adapt 10 p=1 lo=0.5 hi=2 tag=s persist=1` | 2320 | +51.3 / +51.3 / +29.3 | +9.2 | +20.3 | +28.4 | +47.6 / +14.3 | -1395 / -360 | +52.0 | 0.23 / 0.32 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit P7 * pct>=0.7 adapt 10 p=1 lo=0.25 hi=3 tag=f persist=1` | 2337 | +51.7 / +51.7 / +27.3 | +10.6 | +22.8 | +30.4 | +49.0 / +18.4 | -1053 / -189 | +57.1 | 0.14 / 0.08 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit P7 * pct>=0.7 adapt 5 p=1 lo=0.5 hi=2 tag=f persist=1` | 2471 | +49.9 / +49.9 / +30.0 | +15.0 | +24.6 | +31.9 | +48.8 / +22.9 | -430 / +224 | +74.2 | 0.55 / 0.01 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit P7 * pct>=0.7 adapt 5 p=1 lo=0.5 hi=2 tag=s persist=1` | 2471 | +49.9 / +49.9 / +30.0 | +15.0 | +24.7 | +31.8 | +48.7 / +23.0 | -435 / +228 | +74.1 | 0.55 / 0.01 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit P7 * pct>=0.7 adapt 5 p=-1 lo=0.25 hi=3 tag=f persist=1` | 2465 | +50.7 / +50.7 / +25.7 | +12.0 | +21.7 | +32.0 | +50.0 / +20.6 | -284 / -50 | +72.7 | 0.25 / 0.06 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit P7 * pct>=0.7 adapt 5 p=-1 lo=0.25 hi=3 tag=s persist=1` | 2465 | +50.7 / +50.7 / +25.7 | +12.0 | +21.8 | +32.1 | +50.0 / +20.8 | -263 / -49 | +73.3 | 0.25 / 0.05 | 1.00 | 46 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit P7 * pct>=0.7 adapt 5 p=-1 lo=0.5 hi=2 tag=f persist=1` | 2458 | +50.7 / +50.7 / +25.7 | +12.0 | +23.7 | +32.1 | +49.6 / +22.1 | -425 / -9 | +71.0 | 0.30 / 0.01 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit P7 * pct>=0.7 adapt 5 p=-0.5 lo=0.25 hi=3 tag=f persist=1` | 2433 | +50.6 / +50.6 / +25.6 | +11.3 | +23.3 | +32.3 | +48.7 / +20.3 | -747 / -37 | +64.8 | 0.25 / 0.03 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit P7 * pct>=0.7 adapt 5 p=-0.5 lo=0.25 hi=3 tag=s persist=1` | 2433 | +50.6 / +50.6 / +25.6 | +11.3 | +23.3 | +32.3 | +48.7 / +20.3 | -747 / -38 | +64.8 | 0.25 / 0.03 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit P7 * pct>=0.7 adapt 5 p=-0.5 lo=0.5 hi=2 tag=f persist=1` | 2432 | +50.6 / +50.6 / +25.6 | +11.3 | +22.6 | +32.3 | +48.7 / +19.6 | -730 / -45 | +65.4 | 0.29 / 0.04 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit P7 * pct>=0.7 adapt 5 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 2437 | +50.1 / +50.1 / +26.0 | +14.6 | +24.3 | +32.5 | +48.6 / +21.9 | -607 / +26 | +68.9 | 0.56 / 0.01 | 1.00 | 46 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit P7 * pct>=0.7 adapt 5 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 2437 | +50.1 / +50.1 / +26.0 | +14.6 | +24.3 | +32.5 | +48.6 / +21.9 | -607 / +22 | +68.9 | 0.56 / 0.01 | 1.00 | 46 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit P7 * pct>=0.7 adapt 5 p=0.5 lo=0.5 hi=2 tag=f persist=1` | 2437 | +50.1 / +50.1 / +26.0 | +14.6 | +24.3 | +32.5 | +48.6 / +21.9 | -608 / +28 | +68.8 | 0.56 / 0.01 | 1.00 | 46 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit P7 * pct>=0.7 adapt 5 p=1 lo=0.25 hi=3 tag=f persist=1` | 2473 | +48.8 / +48.8 / +30.0 | +15.3 | +24.6 | +32.0 | +47.4 / +22.5 | -521 / +246 | +71.8 | 0.64 / 0.01 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit P7 * pct>=0.7 adapt 5 p=0.25 lo=0.25 hi=3 tag=f persist=1` | 2410 | +49.9 / +49.9 / +24.5 | +10.7 | +23.5 | +33.4 | +47.7 / +20.1 | -835 / -109 | +62.9 | 0.42 / 0.02 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit P7 * pct>=0.7 adapt 5 p=0.25 lo=0.25 hi=3 tag=s persist=1` | 2410 | +49.9 / +49.9 / +24.5 | +10.7 | +23.5 | +33.4 | +47.7 / +20.1 | -826 / -109 | +63.1 | 0.42 / 0.02 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit P7 * pct>=0.7 adapt 5 p=0.25 lo=0.5 hi=2 tag=f persist=1` | 2410 | +49.9 / +49.9 / +24.5 | +10.7 | +23.5 | +33.4 | +47.7 / +20.1 | -835 / -109 | +62.9 | 0.42 / 0.02 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |

### Item 3: profit cut

Live-mirror rows (MULT 30, win 5, persist 5, secs_fav <= 5, by arm): arm 0.2: fires 26, L6M cut -0.3, PRE cut +0.0, d mean L6M -199; arm 0.3: fires 23, L6M cut -0.3, PRE cut +0.0, d mean L6M -126; arm 0.4: fires 16, L6M cut -0.3, PRE cut +0.0, d mean L6M -126; arm 0.5: fires 11, L6M cut +0.0, PRE cut +0.0, d mean L6M +32; arm 0.6: fires 8, L6M cut +0.0, PRE cut +0.0, d mean L6M -31; arm 0.7: fires 5, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.8: fires 3, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.9: fires 0, L6M cut +0.0, PRE cut +0.0, d mean L6M +0

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit P7 * pct>=0.2 pulled_mult>=30 secs_fav<=5 take win=15 persist=2 wall_ticks=8` | 2031 | +66.3 / +71.5 / +60.2 | +0.9 | +40.9 | +14.6 | +68.8 / +45.2 | +1271 / -392 | +72.8 | 0.01 / 0.02 | 0.59 | 58 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit P7 * pct>=0.2 pulled_mult>=30 secs_fav<=5 take win=15 persist=3 wall_ticks=8` | 1785 | +66.6 / +66.6 / +49.6 | +10.3 | +47.9 | +11.7 | +69.6 / +52.6 | +1574 / +42 | +80.5 | 0.01 / 0.01 | 0.04 | 53 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=8 persist=2 wall_ticks=8` | 1979 | +65.5 / +65.5 / +48.0 | -15.0 | +17.6 | +15.9 | +68.9 / +25.8 | +1762 / +353 | +98.1 | 0.01 / 0.21 | 1.00 | 42 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit P7 * pct>=0.2 pulled_mult>=30 secs_fav<=2 take win=15 persist=1 wall_ticks=8` | 1937 | +63.4 / +63.4 / +47.3 | +20.7 | +36.8 | +14.1 | +67.6 / +44.0 | +2048 / +753 | +96.9 | 0.01 / 0.03 | 0.73 | 54 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit P7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=5 persist=2 wall_ticks=8` | 2202 | +58.3 / +58.3 / +66.3 | +23.3 | +15.3 | -0.7 | +57.4 / +13.5 | -353 / +500 | +50.8 | 0.01 / 0.08 | 1.00 | 47 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=8 persist=3 wall_ticks=8` | 1582 | +60.0 / +60.0 / +50.7 | -11.1 | +11.8 | +19.6 | +63.3 / +19.1 | +1562 / +1001 | +64.8 | 0.01 / 0.35 | 1.00 | 32 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=8 persist=1 wall_ticks=8` | 2383 | +61.8 / +61.8 / +42.4 | -10.4 | +12.4 | +20.9 | +64.4 / +18.4 | +1261 / -431 | +91.5 | 0.01 / 0.49 | 1.00 | 42 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit P7 * pct>=0.3 pulled_mult>=20 secs_fav<=5 take win=10 persist=3 wall_ticks=8` | 1911 | +61.7 / +61.7 / +42.3 | -0.4 | +25.5 | +9.5 | +62.5 / +26.9 | +343 / +132 | +45.1 | 0.01 / 0.04 | 0.92 | 47 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit P7 * pct>=0.4 pulled_mult>=10 secs_fav<=5 take win=10 persist=10 wall_ticks=8` | 1674 | +53.7 / +57.6 / +61.3 | +10.9 | +20.2 | +9.3 | +47.0 / +8.7 | -2428 / +509 | +30.9 | 0.03 / 0.03 | 0.96 | 35 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit P7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=5 persist=2 wall_ticks=8` | 3030 | +58.1 / +58.1 / +48.5 | +32.6 | +14.3 | +2.5 | +57.1 / +12.3 | -409 / -363 | +42.6 | 0.01 / 0.07 | 0.96 | 71 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit P7 * pct>=0.5 pulled_mult>=10 secs_fav<=5 take win=10 persist=10 wall_ticks=8` | 1453 | +55.9 / +56.0 / +52.0 | +19.8 | +29.2 | +11.1 | +51.1 / +21.7 | -1853 / +1264 | +31.7 | 0.01 / 0.03 | 0.65 | 28 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit P7 * pct>=0.3 pulled_mult>=5 secs_fav<=5 take win=8 persist=10 wall_ticks=8` | 2637 | +54.9 / +54.9 / +54.3 | -22.0 | +19.8 | +16.5 | +51.8 / +14.4 | -1004 / -815 | +43.4 | 0.02 / 0.08 | 0.98 | 49 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit P7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=5 persist=1 wall_ticks=8` | 2791 | +54.5 / +54.5 / +55.0 | +17.5 | +4.2 | +30.9 | +53.0 / +1.1 | -545 / -666 | +49.1 | 0.03 / 0.32 | 1.00 | 54 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit P7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=10 persist=10 wall_ticks=8` | 2146 | +54.5 / +54.5 / +53.2 | +18.3 | +3.3 | +4.2 | +53.2 / +0.4 | -454 / -586 | +39.0 | 0.01 / 0.53 | 1.00 | 48 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit P7 * pct>=0.3 pulled_mult>=5 secs_fav<=5 take win=10 persist=10 wall_ticks=8` | 3000 | +54.6 / +54.6 / +50.6 | -18.5 | +14.0 | +17.9 | +52.2 / +9.4 | -895 / -1338 | +47.0 | 0.02 / 0.07 | 0.99 | 57 | OK-PRIOR [RECENT-ONLY] |
| 16 | `profit P7 * pct>=0.3 pulled_mult>=3 secs_fav<=2 take win=3 persist=5 wall_ticks=8` | 1471 | +56.8 / +56.8 / +40.8 | +14.6 | +6.5 | +15.4 | +46.2 / -16.5 | -3785 / -640 | +11.8 | 0.01 / 0.27 | 1.00 | 32 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=5 persist=1 wall_ticks=8` | 1732 | +57.1 / +57.1 / +35.4 | -11.8 | +12.7 | +23.3 | +63.0 / +24.7 | +2756 / +271 | +93.8 | 0.01 / 0.34 | 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit P7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=8 persist=5 wall_ticks=8` | 2679 | +54.4 / +54.4 / +46.3 | -1.9 | +2.0 | +7.3 | +47.0 / -13.8 | -2209 / -1011 | +6.3 | 0.02 / 0.38 | 1.00 | 52 | OK-PRIOR [RECENT-ONLY] |
| 19 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=10 persist=3 wall_ticks=8` | 2153 | +56.8 / +56.8 / +34.9 | -6.9 | +26.3 | +16.2 | +57.7 / +27.8 | +359 / +571 | +61.0 | 0.01 / 0.11 | 1.00 | 51 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit P7 * pct>=0.2 pulled_mult>=20 secs_fav<=5 take win=10 persist=2 wall_ticks=8` | 2450 | +53.2 / +53.2 / +49.1 | -8.9 | +27.9 | +13.2 | +51.6 / +25.4 | -575 / -886 | +38.1 | 0.03 / 0.14 | 1.00 | 52 | OK-PRIOR [OK-PRIOR] |


## U7

### Item 2: adaptive trail vs the fixed trail (same grid)

Best fixed tighten (p=0): `profit U7 * pct>=0.2 adapt 30 p=0 lo=0.25 hi=3 tag=s persist=1` L6M cut +19.3, equal-mean +17.7, d mean -374. Best adaptive overall: `profit U7 * pct>=0.7 adapt 30 p=0.25 lo=0.5 hi=2 tag=s persist=1` L6M cut +19.1, equal-mean +22.5, d mean +933. Best in the ORDER's direction (p<0, thick ahead tighter): `profit U7 * pct>=0.2 adapt 40 p=-0.5 lo=0.5 hi=2 tag=s persist=1` L6M cut +17.1, equal-mean +10.4, d mean -1241. Difference adaptive minus fixed: -0.1 points of L6M stack maxDD cut (positive = the state-dependent distance helps).

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit U7 * pct>=0.2 adapt 30 p=0 lo=0.25 hi=3 tag=f persist=1` | 845 | +19.3 / +19.3 / +19.8 | -3.7 | +13.7 | -22.0 | +17.7 / +12.0 | -374 / -1598 | +2.2 | 0.01 / 0.07 | 0.83 | 22 | OK-PRIOR [RECENT-ONLY] |
| 2 | `profit U7 * pct>=0.2 adapt 30 p=0 lo=0.25 hi=3 tag=s persist=1` | 845 | +19.3 / +19.3 / +19.8 | -3.7 | +13.7 | -22.0 | +17.7 / +12.0 | -374 / -1598 | +2.2 | 0.01 / 0.07 | 0.83 | 22 | OK-PRIOR [RECENT-ONLY] |
| 3 | `profit U7 * pct>=0.7 adapt 30 p=0.25 lo=0.25 hi=3 tag=f persist=1` | 395 | +19.1 / +19.1 / +11.1 | -6.5 | +14.1 | -1.3 | +22.5 / +17.8 | +933 / -532 | +33.5 | 0.14 / 0.13 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit U7 * pct>=0.7 adapt 30 p=0.25 lo=0.25 hi=3 tag=s persist=1` | 395 | +19.1 / +19.1 / +11.1 | -6.5 | +14.1 | -1.3 | +22.5 / +17.8 | +933 / -532 | +33.5 | 0.14 / 0.13 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit U7 * pct>=0.7 adapt 30 p=0.25 lo=0.5 hi=2 tag=f persist=1` | 395 | +19.1 / +19.1 / +11.1 | -6.5 | +14.1 | -1.3 | +22.5 / +17.8 | +933 / -532 | +33.5 | 0.14 / 0.13 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit U7 * pct>=0.7 adapt 40 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 396 | +18.9 / +18.9 / +11.6 | -6.1 | +15.2 | -0.1 | +22.0 / +18.4 | +841 / -581 | +32.8 | 0.12 / 0.12 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit U7 * pct>=0.7 adapt 40 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 396 | +18.9 / +18.9 / +11.6 | -6.1 | +15.2 | -0.1 | +22.0 / +18.4 | +841 / -581 | +32.8 | 0.12 / 0.12 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit U7 * pct>=0.7 adapt 40 p=0.5 lo=0.5 hi=2 tag=f persist=1` | 385 | +19.0 / +19.0 / +11.2 | -4.9 | +16.9 | -0.2 | +22.3 / +20.3 | +894 / -512 | +33.6 | 0.14 / 0.04 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit U7 * pct>=0.2 adapt 40 p=-0.5 lo=0.5 hi=2 tag=f persist=1` | 922 | +17.1 / +17.1 / +17.7 | +0.3 | +10.0 | -19.9 | +10.4 / +2.6 | -1241 / -1600 | -17.1 | 0.02 / 0.11 | 1.00 | 20 | OK-PRIOR [RECENT-ONLY] |
| 10 | `profit U7 * pct>=0.2 adapt 40 p=-0.5 lo=0.5 hi=2 tag=s persist=1` | 921 | +17.1 / +17.1 / +17.7 | +0.3 | +10.0 | -19.9 | +10.4 / +2.6 | -1241 / -1598 | -17.1 | 0.05 / 0.13 | 1.00 | 20 | OK-PRIOR [RECENT-ONLY] |
| 11 | `profit U7 * pct>=0.3 adapt 30 p=0 lo=0.25 hi=3 tag=f persist=1` | 743 | +16.4 / +16.4 / +19.8 | -13.3 | +9.3 | -19.5 | +13.1 / +5.7 | -814 / -1148 | +13.3 | 0.09 / 0.24 | 1.00 | 25 | OK-PRIOR [RECENT-ONLY] |
| 12 | `profit U7 * pct>=0.7 adapt 40 p=-1 lo=0.5 hi=2 tag=f persist=1` | 425 | +18.4 / +18.4 / +11.4 | -7.5 | +14.3 | -3.5 | +22.0 / +18.2 | +1001 / -681 | +34.1 | 0.09 / 0.14 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit U7 * pct>=0.7 adapt 40 p=-1 lo=0.5 hi=2 tag=s persist=1` | 425 | +18.4 / +18.4 / +11.4 | -7.5 | +14.3 | -3.5 | +22.0 / +18.2 | +1001 / -681 | +34.1 | 0.09 / 0.14 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit U7 * pct>=0.7 adapt 20 p=0 lo=0.25 hi=3 tag=f persist=1` | 437 | +18.3 / +18.3 / +11.4 | -7.4 | +14.5 | -2.7 | +22.0 / +18.3 | +997 / -710 | +33.8 | 0.10 / 0.13 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit U7 * pct>=0.7 adapt 20 p=0 lo=0.25 hi=3 tag=s persist=1` | 437 | +18.3 / +18.3 / +11.4 | -7.4 | +14.5 | -2.7 | +22.0 / +18.3 | +997 / -710 | +33.8 | 0.10 / 0.13 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit U7 * pct>=0.7 adapt 40 p=1 lo=0.5 hi=2 tag=f persist=1` | 431 | +18.3 / +18.3 / +11.4 | -7.4 | +14.5 | -4.0 | +22.1 / +18.5 | +1020 / -666 | +34.3 | 0.21 / 0.11 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit U7 * pct>=0.7 adapt 40 p=1 lo=0.5 hi=2 tag=s persist=1` | 431 | +18.3 / +18.3 / +11.4 | -7.4 | +14.5 | -4.0 | +22.1 / +18.5 | +1020 / -666 | +34.3 | 0.21 / 0.11 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit U7 * pct>=0.7 adapt 30 p=-0.5 lo=0.25 hi=3 tag=f persist=1` | 455 | +17.7 / +17.7 / +12.4 | -10.5 | +12.2 | -5.8 | +20.8 / +15.5 | +839 / -709 | +34.1 | 0.19 / 0.29 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit U7 * pct>=0.7 adapt 30 p=-0.5 lo=0.25 hi=3 tag=s persist=1` | 455 | +17.7 / +17.7 / +12.4 | -10.5 | +12.2 | -5.8 | +20.7 / +15.4 | +810 / -709 | +34.1 | 0.19 / 0.29 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit U7 * pct>=0.7 adapt 30 p=-0.5 lo=0.5 hi=2 tag=f persist=1` | 453 | +17.7 / +17.7 / +12.4 | -10.1 | +12.0 | -6.0 | +20.6 / +15.2 | +787 / -745 | +33.7 | 0.16 / 0.20 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |

### Item 3: profit cut

Live-mirror rows (MULT 30, win 5, persist 5, secs_fav <= 5, by arm): arm 0.2: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M -36; arm 0.3: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.4: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.5: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.6: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.7: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.8: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.9: fires 0, L6M cut +0.0, PRE cut +0.0, d mean L6M +0

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=8 persist=10 wall_ticks=8` | 404 | +28.8 / +28.8 / +6.4 | -4.4 | +10.8 | +6.7 | +32.3 / +15.1 | +1101 / +366 | +49.9 | 0.01 / 0.25 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=10 persist=10 wall_ticks=8` | 487 | +28.8 / +28.8 / +6.4 | -4.4 | +10.2 | +3.5 | +32.0 / +14.2 | +996 / +463 | +49.5 | 0.01 / 0.26 | 1.00 | 30 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=15 persist=10 wall_ticks=8` | 565 | +28.8 / +28.8 / +6.4 | -4.4 | +10.2 | +3.2 | +32.0 / +14.2 | +996 / +259 | +49.5 | 0.03 / 0.28 | 1.00 | 30 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=10 persist=10 wall_ticks=8` | 342 | +28.8 / +28.8 / +6.4 | -2.6 | +11.8 | +3.2 | +32.9 / +16.9 | +1301 / +108 | +52.7 | 0.01 / 0.11 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=15 persist=10 wall_ticks=8` | 515 | +28.8 / +28.8 / +6.4 | -4.4 | +10.2 | +8.2 | +32.0 / +14.2 | +996 / +260 | +49.5 | 0.01 / 0.26 | 1.00 | 30 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit U7 * pct>=0.5 pulled_mult>=10 secs_fav<=2 take win=15 persist=10 wall_ticks=8` | 331 | +28.8 / +28.8 / +6.4 | -4.4 | +8.3 | +5.2 | +33.0 / +13.6 | +1324 / +294 | +52.3 | 0.01 / 0.27 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit U7 * pct>=0.3 pulled_mult>=10 secs_fav<=10 take win=3 persist=5 wall_ticks=8` | 189 | +23.6 / +23.6 / +8.2 | -9.7 | +7.5 | -2.1 | +25.8 / +10.1 | +554 / -43 | +7.3 | 0.01 / 0.06 | 0.92 | 5 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit U7 * pct>=0.4 pulled_mult>=10 secs_fav<=10 take win=3 persist=5 wall_ticks=8` | 167 | +23.6 / +23.6 / +8.2 | -5.4 | +7.5 | -0.8 | +24.3 / +8.3 | +187 / -154 | +14.2 | 0.01 / 0.23 | 1.00 | 6 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit U7 * pct>=0.2 pulled_mult>=3 secs_fav<=5 take win=2 persist=5 wall_ticks=8` | 631 | +18.0 / +18.0 / +27.5 | -4.3 | +3.1 | +0.2 | +14.3 / -1.3 | -831 / -1435 | -11.2 | 0.03 / 0.50 | 1.00 | 34 | OK-PRIOR [RECENT-ONLY] |
| 10 | `profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=8 persist=10 wall_ticks=8` | 247 | +23.0 / +23.0 / +6.4 | -2.6 | +9.7 | +4.5 | +27.6 / +15.0 | +1342 / +134 | +53.2 | 0.02 / 0.10 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit U7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=5 persist=5 wall_ticks=8` | 566 | +20.7 / +20.7 / +15.3 | -5.6 | +17.7 | +0.5 | +21.8 / +18.9 | +267 / -655 | +24.2 | 0.03 / 0.01 | 0.93 | 25 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit U7 * pct>=0.4 pulled_mult>=30 secs_fav<=10 take win=10 persist=2 wall_ticks=8` | 401 | +22.9 / +22.9 / +6.1 | -0.9 | +5.7 | -0.5 | +24.4 / +7.6 | +379 / -329 | +12.9 | 0.04 / 0.44 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=5 persist=10 wall_ticks=8` | 191 | +24.6 / +24.6 / -1.1 | -2.2 | +14.5 | +1.5 | +29.6 / +20.2 | +1367 / -42 | +47.8 | 0.01 / 0.06 | 0.43 | 10 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit U7 * pct>=0.6 pulled_mult>=20 secs_fav<=10 take win=5 persist=1 wall_ticks=8` | 347 | +24.0 / +24.0 / -0.3 | -1.2 | +10.3 | +2.0 | +26.5 / +13.2 | +713 / -50 | +31.4 | 0.01 / 0.29 | 1.00 | 20 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit U7 * pct>=0.6 pulled_mult>=10 secs_fav<=5 take win=2 persist=1 wall_ticks=8` | 501 | +22.8 / +22.8 / +1.4 | +0.1 | +17.8 | +2.4 | +21.2 / +16.1 | -442 / -137 | +10.8 | 0.04 / 0.03 | 0.89 | 32 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit U7 * pct>=0.6 pulled_mult>=20 secs_fav<=5 take win=5 persist=1 wall_ticks=8` | 282 | +23.1 / +23.1 / -0.3 | -0.7 | +11.0 | +2.0 | +24.1 / +12.3 | +300 / -308 | +20.5 | 0.01 / 0.11 | 1.00 | 10 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit U7 * pct>=0.7 pulled_mult>=30 secs_fav<=10 take win=15 persist=3 wall_ticks=8` | 339 | +22.3 / +22.3 / +1.5 | -4.2 | +16.7 | +1.2 | +23.6 / +18.1 | +346 / -48 | +25.4 | 0.06 / 0.10 | 0.92 | 16 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit U7 * pct>=0.7 pulled_mult>=10 secs_fav<=10 take win=2 persist=1 wall_ticks=8` | 462 | +22.1 / +22.1 / +2.4 | -1.8 | +16.2 | -2.3 | +23.4 / +17.5 | +328 / -157 | +25.0 | 0.06 / 0.08 | 0.99 | 27 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit U7 * pct>=0.5 pulled_mult>=30 secs_fav<=10 take win=8 persist=1 wall_ticks=8` | 260 | +21.8 / +21.8 / +2.9 | +1.0 | +7.2 | -0.0 | +23.5 / +9.2 | +444 / +183 | +20.2 | 0.04 / 0.21 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit U7 * pct>=0.2 pulled_mult>=5 secs_fav<=5 take win=2 persist=5 wall_ticks=8` | 229 | +18.0 / +18.0 / +18.0 | -7.7 | +18.3 | +7.5 | +14.5 / +14.9 | -780 / -111 | -8.4 | 0.04 / 0.01 | 0.73 | 19 | OK-PRIOR [OK-PRIOR] |


## H7

### Item 2: adaptive trail vs the fixed trail (same grid)

Best fixed tighten (p=0): `profit H7 * pct>=0.3 adapt 40 p=0 lo=0.25 hi=3 tag=s persist=1` L6M cut +6.3, equal-mean +4.1, d mean -438. Best adaptive overall: `profit H7 * pct>=0.5 adapt 40 p=1 lo=0.25 hi=3 tag=f persist=1` L6M cut +4.0, equal-mean -0.1, d mean -768. Best in the ORDER's direction (p<0, thick ahead tighter): `profit H7 * pct>=0.8 adapt 30 p=-0.5 lo=0.5 hi=2 tag=f persist=1` L6M cut +2.7, equal-mean +3.5, d mean +140. Difference adaptive minus fixed: -2.3 points of L6M stack maxDD cut (positive = the state-dependent distance helps).

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit H7 * pct>=0.5 adapt 40 p=1 lo=0.25 hi=3 tag=f persist=1` | 566 | +4.0 / +4.0 / -2.5 | +4.3 | -13.5 | +8.0 | -0.1 / -18.4 | -768 / -895 | -24.6 | 0.40 / 0.94 | 1.00 | 28 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit H7 * pct>=0.5 adapt 40 p=1 lo=0.25 hi=3 tag=s persist=1` | 566 | +4.0 / +4.0 / -2.5 | +4.3 | -13.5 | +8.0 | -0.1 / -18.4 | -768 / -895 | -24.6 | 0.40 / 0.94 | 1.00 | 28 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit H7 * pct>=0.8 adapt 20 p=0 lo=0.25 hi=3 tag=f persist=1` | 236 | +2.9 / +2.9 / +0.0 | +3.1 | +0.6 | +14.1 | +3.0 / +0.7 | +21 / -324 | +0.2 | 0.07 / 0.06 | 0.95 | 18 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit H7 * pct>=0.8 adapt 20 p=0 lo=0.25 hi=3 tag=s persist=1` | 236 | +2.9 / +2.9 / +0.0 | +3.1 | +0.6 | +14.1 | +3.0 / +0.7 | +21 / -324 | +0.2 | 0.07 / 0.06 | 0.95 | 18 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit H7 * pct>=0.8 adapt 40 p=1 lo=0.5 hi=2 tag=f persist=1` | 233 | +2.9 / +2.9 / +0.0 | +3.1 | +0.5 | +14.0 | +2.9 / +0.6 | +10 / -320 | -0.0 | 0.08 / 0.15 | 0.96 | 18 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit H7 * pct>=0.7 adapt 20 p=0 lo=0.25 hi=3 tag=f persist=1` | 330 | +2.8 / +2.8 / +0.0 | +3.1 | -1.6 | +17.0 | +2.4 / -2.0 | -78 / -603 | -5.4 | 0.15 / 0.25 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit H7 * pct>=0.8 adapt 30 p=-0.5 lo=0.5 hi=2 tag=f persist=1` | 234 | +2.7 / +2.7 / +0.0 | +3.4 | -1.1 | +13.8 | +3.5 / -0.2 | +140 / -299 | +2.7 | 0.15 / 0.32 | 1.00 | 14 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit H7 * pct>=0.8 adapt 30 p=-0.5 lo=0.5 hi=2 tag=s persist=1` | 234 | +2.7 / +2.7 / +0.0 | +3.4 | -1.1 | +13.8 | +3.5 / -0.2 | +140 / -299 | +2.7 | 0.15 / 0.32 | 1.00 | 14 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit H7 * pct>=0.5 adapt 5 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 698 | +5.5 / +5.5 / -11.1 | +5.5 | -12.0 | +8.0 | -1.0 / -19.6 | -1118 / -911 | -20.6 | 0.06 / 0.16 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit H7 * pct>=0.5 adapt 5 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 698 | +5.5 / +5.5 / -11.1 | +5.5 | -12.0 | +8.0 | -1.0 / -19.6 | -1118 / -911 | -20.6 | 0.06 / 0.16 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit H7 * pct>=0.5 adapt 5 p=0.5 lo=0.5 hi=2 tag=f persist=1` | 698 | +5.5 / +5.5 / -11.1 | +5.5 | -12.0 | +8.0 | -1.0 / -19.6 | -1119 / -911 | -20.6 | 0.06 / 0.16 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit H7 * pct>=0.5 adapt 15 p=1 lo=0.5 hi=2 tag=f persist=1` | 655 | +4.9 / +4.9 / -9.1 | +5.1 | -12.2 | +8.5 | +2.6 / -15.0 | -447 / -819 | -20.4 | 0.75 / 0.76 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit H7 * pct>=0.5 adapt 15 p=1 lo=0.5 hi=2 tag=s persist=1` | 655 | +4.9 / +4.9 / -9.1 | +5.1 | -12.2 | +8.5 | +2.6 / -15.0 | -447 / -820 | -20.4 | 0.75 / 0.76 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit H7 * pct>=0.5 adapt 5 p=1 lo=0.5 hi=2 tag=f persist=1` | 699 | +5.4 / +5.4 / -11.0 | +5.1 | -12.1 | +8.0 | -0.8 / -19.5 | -1076 / -916 | -20.1 | 0.06 / 0.97 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit H7 * pct>=0.5 adapt 5 p=1 lo=0.5 hi=2 tag=s persist=1` | 699 | +5.4 / +5.4 / -11.0 | +5.1 | -12.1 | +8.0 | -0.8 / -19.5 | -1074 / -915 | -20.1 | 0.06 / 0.97 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit H7 * pct>=0.5 adapt 5 p=1 lo=0.25 hi=3 tag=f persist=1` | 699 | +5.4 / +5.4 / -11.1 | +5.2 | -12.1 | +7.9 | -0.7 / -19.3 | -1061 / -914 | -19.9 | 0.06 / 0.14 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit H7 * pct>=0.8 adapt 40 p=-1 lo=0.5 hi=2 tag=f persist=1` | 227 | +2.6 / +2.6 / +0.0 | +3.1 | +0.6 | +13.6 | +2.7 / +0.6 | +15 / -295 | -0.2 | 0.12 / 0.09 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit H7 * pct>=0.8 adapt 40 p=-1 lo=0.5 hi=2 tag=s persist=1` | 227 | +2.6 / +2.6 / +0.0 | +3.1 | +0.6 | +13.6 | +2.7 / +0.6 | +15 / -295 | -0.2 | 0.12 / 0.09 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit H7 * pct>=0.5 adapt 5 p=0.25 lo=0.25 hi=3 tag=f persist=1` | 696 | +5.3 / +5.3 / -10.8 | +5.4 | -12.1 | +7.9 | -1.1 / -19.6 | -1108 / -842 | -20.7 | 0.09 / 0.16 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit H7 * pct>=0.5 adapt 5 p=0.25 lo=0.25 hi=3 tag=s persist=1` | 696 | +5.3 / +5.3 / -10.8 | +5.4 | -12.1 | +7.9 | -1.1 / -19.6 | -1108 / -842 | -20.7 | 0.09 / 0.16 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |

### Item 3: profit cut

Live-mirror rows (MULT 30, win 5, persist 5, secs_fav <= 5, by arm): arm 0.2: fires 3, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.3: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.4: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.5: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.6: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.7: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.8: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.9: fires 0, L6M cut +0.0, PRE cut +0.0, d mean L6M +0

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit H7 * pct>=0.3 pulled_mult>=3 secs_fav<=2 take win=2 persist=3 wall_ticks=8` | 282 | +14.3 / +14.3 / -11.3 | +1.4 | -13.3 | +9.6 | +8.9 / -20.5 | -1258 / -504 | -13.2 | 0.01 / 0.97 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit H7 * pct>=0.4 pulled_mult>=10 secs_fav<=2 take win=3 persist=2 wall_ticks=8` | 185 | +11.9 / +11.9 / -4.7 | +1.0 | -0.8 | -0.2 | +10.8 / -2.0 | -207 / -112 | -5.6 | 0.01 / 0.18 | 1.00 | 4 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit H7 * pct>=0.4 pulled_mult>=3 secs_fav<=2 take win=2 persist=3 wall_ticks=8` | 247 | +12.0 / +12.0 / -6.3 | +1.8 | -10.0 | +9.6 | +8.8 / -13.9 | -730 / -368 | -8.3 | 0.01 / 0.96 | 1.00 | 14 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit H7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=3 persist=2 wall_ticks=8` | 217 | +12.1 / +12.1 / -9.6 | +0.5 | -2.1 | -0.2 | +8.6 / -6.2 | -728 / -148 | -16.5 | 0.02 / 0.26 | 1.00 | 4 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit H7 * pct>=0.4 pulled_mult>=10 secs_fav<=5 take win=5 persist=5 wall_ticks=8` | 293 | +11.8 / +11.8 / -8.2 | +1.0 | -1.5 | -2.0 | +8.2 / -5.6 | -732 / -267 | -14.2 | 0.02 / 0.28 | 1.00 | 9 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit H7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=5 persist=5 wall_ticks=8` | 348 | +11.9 / +11.9 / -11.8 | +0.4 | -3.6 | -2.0 | +6.3 / -10.2 | -1121 / -500 | -25.1 | 0.02 / 0.12 | 1.00 | 6 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit H7 * pct>=0.3 pulled_mult>=20 secs_fav<=2 take win=10 persist=2 wall_ticks=8` | 280 | +10.6 / +10.6 / -6.9 | +0.1 | -10.1 | -1.4 | +6.6 / -15.1 | -915 / -596 | -10.7 | 0.03 / 0.82 | 1.00 | 9 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit H7 * pct>=0.2 pulled_mult>=10 secs_fav<=2 take win=3 persist=2 wall_ticks=8` | 251 | +10.0 / +10.0 / -5.1 | -0.4 | -2.3 | -0.2 | +6.0 / -6.9 | -810 / -243 | -21.2 | 0.03 / 0.27 | 1.00 | 0 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit H7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=8 persist=5 wall_ticks=8` | 266 | +9.9 / +9.9 / -4.9 | +4.4 | -6.2 | +0.2 | +6.3 / -10.4 | -819 / -559 | -5.4 | 0.03 / 0.59 | 1.00 | 10 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit H7 * pct>=0.2 pulled_mult>=5 secs_fav<=5 take win=5 persist=10 wall_ticks=8` | 259 | +10.6 / +10.6 / -8.1 | +0.4 | -5.5 | -1.5 | +6.2 / -10.7 | -982 / -500 | -10.8 | 0.02 / 0.58 | 1.00 | 6 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit H7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=3 persist=3 wall_ticks=8` | 330 | +9.7 / +9.7 / -5.9 | +2.2 | -9.5 | +3.7 | +6.8 / -13.1 | -586 / -462 | -15.2 | 0.05 / 0.77 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit H7 * pct>=0.4 pulled_mult>=5 secs_fav<=2 take win=3 persist=3 wall_ticks=8` | 284 | +8.0 / +8.0 / +0.7 | +2.5 | -6.8 | +3.7 | +5.7 / -9.5 | -457 / -460 | -13.5 | 0.10 / 0.72 | 1.00 | 8 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit H7 * pct>=0.2 pulled_mult>=3 secs_fav<=2 take win=2 persist=3 wall_ticks=8` | 321 | +10.0 / +10.0 / -7.9 | +1.1 | -8.9 | +9.6 | +5.7 / -14.1 | -962 / -341 | -3.9 | 0.03 / 0.76 | 1.00 | 23 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit H7 * pct>=0.2 pulled_mult>=10 secs_fav<=2 take win=8 persist=5 wall_ticks=8` | 294 | +8.2 / +8.2 / -1.1 | +3.7 | -7.9 | +0.2 | +4.2 / -12.6 | -791 / -666 | -16.0 | 0.10 / 0.67 | 1.00 | 9 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit H7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=5 persist=5 wall_ticks=8` | 355 | +8.4 / +8.4 / -2.0 | +5.5 | -4.5 | +1.8 | +4.2 / -9.4 | -829 / -475 | -20.3 | 0.08 / 0.21 | 1.00 | 19 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit H7 * pct>=0.3 pulled_mult>=20 secs_fav<=2 take win=10 persist=1 wall_ticks=8` | 383 | +10.6 / +10.6 / -10.8 | +3.8 | -12.1 | -2.2 | +6.9 / -16.8 | -751 / -467 | -21.4 | 0.04 / 0.79 | 1.00 | 14 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit H7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=5 persist=2 wall_ticks=8` | 430 | +9.3 / +9.3 / -5.5 | -0.3 | -9.3 | +0.0 | +4.4 / -15.1 | -951 / -812 | -23.8 | 0.05 / 0.50 | 1.00 | 8 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit H7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=10 persist=5 wall_ticks=8` | 434 | +9.4 / +9.4 / -6.6 | +4.5 | -8.4 | +3.6 | +4.7 / -14.0 | -927 / -460 | -23.6 | 0.05 / 0.45 | 1.00 | 20 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit H7 * pct>=0.2 pulled_mult>=5 secs_fav<=10 take win=5 persist=10 wall_ticks=8` | 566 | +10.0 / +10.0 / -9.8 | +4.3 | -8.4 | +5.9 | +6.1 / -13.2 | -783 / -617 | -24.9 | 0.08 / 0.31 | 1.00 | 33 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit H7 * pct>=0.3 pulled_mult>=30 secs_fav<=2 take win=15 persist=1 wall_ticks=8` | 285 | +9.2 / +9.2 / -6.6 | -0.5 | -10.6 | -0.7 | +2.9 / -18.3 | -1368 / -279 | -17.1 | 0.03 / 0.75 | 1.00 | 5 | OK-PRIOR [OK-PRIOR] |


## M7

### Item 2: adaptive trail vs the fixed trail (same grid)

Best fixed tighten (p=0): `profit M7 * pct>=0.2 adapt 5 p=0 lo=0.25 hi=3 tag=f persist=1` L6M cut +28.8, equal-mean +26.8, d mean -524. Best adaptive overall: `profit M7 * pct>=0.2 adapt 5 p=-0.5 lo=0.25 hi=3 tag=s persist=1` L6M cut +29.9, equal-mean +28.0, d mean -493. Best in the ORDER's direction (p<0, thick ahead tighter): `profit M7 * pct>=0.2 adapt 5 p=-0.5 lo=0.25 hi=3 tag=s persist=1` L6M cut +29.9, equal-mean +28.0, d mean -493. Difference adaptive minus fixed: +1.1 points of L6M stack maxDD cut (positive = the state-dependent distance helps).

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit M7 * pct>=0.2 adapt 5 p=-0.5 lo=0.25 hi=3 tag=s persist=1` | 3415 | +29.9 / +29.9 / +13.0 | +17.5 | -4.3 | -24.1 | +28.0 / -7.1 | -493 / -735 | +24.9 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit M7 * pct>=0.2 adapt 5 p=-0.5 lo=0.5 hi=2 tag=s persist=1` | 3415 | +29.9 / +29.9 / +13.0 | +17.5 | -4.3 | -23.5 | +28.0 / -7.1 | -494 / -730 | +24.9 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit M7 * pct>=0.2 adapt 5 p=-0.5 lo=0.25 hi=3 tag=f persist=1` | 3415 | +29.8 / +29.8 / +13.0 | +17.5 | -4.3 | -24.1 | +27.9 / -7.1 | -496 / -735 | +24.8 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit M7 * pct>=0.2 adapt 5 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 3415 | +29.5 / +29.5 / +14.0 | +18.1 | -4.1 | -24.1 | +27.7 / -6.7 | -459 / -768 | +24.5 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit M7 * pct>=0.2 adapt 5 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 3415 | +29.5 / +29.5 / +14.0 | +18.1 | -4.1 | -24.1 | +27.7 / -6.7 | -459 / -768 | +24.5 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit M7 * pct>=0.2 adapt 5 p=0.5 lo=0.5 hi=2 tag=f persist=1` | 3415 | +29.5 / +29.5 / +14.0 | +18.1 | -4.2 | -24.2 | +27.7 / -6.9 | -471 / -770 | +24.5 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit M7 * pct>=0.2 adapt 5 p=-0.25 lo=0.25 hi=3 tag=f persist=1` | 3415 | +29.3 / +29.3 / +14.1 | +17.0 | -5.1 | -23.5 | +27.3 / -8.1 | -516 / -751 | +24.0 | 0.01 / 1.00 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit M7 * pct>=0.2 adapt 5 p=-0.25 lo=0.25 hi=3 tag=s persist=1` | 3415 | +29.3 / +29.3 / +14.1 | +17.0 | -5.1 | -23.5 | +27.3 / -8.1 | -516 / -751 | +24.0 | 0.01 / 1.00 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit M7 * pct>=0.2 adapt 5 p=-0.25 lo=0.5 hi=2 tag=f persist=1` | 3415 | +29.3 / +29.3 / +14.1 | +17.0 | -5.1 | -23.5 | +27.3 / -8.1 | -517 / -751 | +24.0 | 0.01 / 1.00 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit M7 * pct>=0.2 adapt 5 p=0.25 lo=0.25 hi=3 tag=f persist=1` | 3415 | +29.3 / +29.3 / +13.3 | +17.4 | -4.8 | -23.6 | +27.1 / -7.9 | -547 / -734 | +23.4 | 0.01 / 1.00 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit M7 * pct>=0.2 adapt 5 p=0.25 lo=0.25 hi=3 tag=s persist=1` | 3415 | +29.3 / +29.3 / +13.3 | +17.4 | -4.8 | -23.6 | +27.1 / -7.9 | -546 / -734 | +23.4 | 0.01 / 1.00 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit M7 * pct>=0.2 adapt 5 p=0.25 lo=0.5 hi=2 tag=f persist=1` | 3415 | +29.3 / +29.3 / +13.3 | +17.4 | -4.8 | -23.6 | +27.1 / -7.9 | -547 / -734 | +23.4 | 0.01 / 1.00 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit M7 * pct>=0.2 adapt 5 p=-1 lo=0.25 hi=3 tag=f persist=1` | 3416 | +29.0 / +29.0 / +13.4 | +17.7 | -4.4 | -24.3 | +27.3 / -6.9 | -447 / -764 | +25.2 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit M7 * pct>=0.2 adapt 5 p=-1 lo=0.25 hi=3 tag=s persist=1` | 3416 | +29.0 / +29.0 / +13.3 | +17.7 | -4.3 | -24.3 | +27.3 / -6.9 | -448 / -762 | +25.1 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit M7 * pct>=0.2 adapt 5 p=0 lo=0.25 hi=3 tag=f persist=1` | 3415 | +28.8 / +28.8 / +13.2 | +16.8 | -5.7 | -23.8 | +26.8 / -8.7 | -524 / -754 | +24.0 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit M7 * pct>=0.2 adapt 5 p=0 lo=0.25 hi=3 tag=s persist=1` | 3415 | +28.8 / +28.8 / +13.2 | +16.8 | -5.7 | -23.8 | +26.8 / -8.7 | -524 / -754 | +24.0 | 0.01 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit M7 * pct>=0.2 adapt 5 p=1 lo=0.25 hi=3 tag=f persist=1` | 3416 | +28.7 / +28.7 / +13.5 | +18.0 | -3.3 | -24.3 | +26.7 / -6.0 | -487 / -735 | +24.2 | 0.01 / 0.99 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit M7 * pct>=0.2 adapt 5 p=1 lo=0.25 hi=3 tag=s persist=1` | 3416 | +28.7 / +28.7 / +13.5 | +18.0 | -3.2 | -24.3 | +26.7 / -6.1 | -494 / -734 | +24.0 | 0.01 / 0.99 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit M7 * pct>=0.2 adapt 5 p=1 lo=0.5 hi=2 tag=f persist=1` | 3416 | +28.5 / +28.5 / +13.7 | +18.0 | -3.4 | -24.4 | +26.6 / -6.2 | -489 / -734 | +24.0 | 0.03 / 0.99 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit M7 * pct>=0.2 adapt 10 p=1 lo=0.25 hi=3 tag=f persist=1` | 3410 | +28.3 / +28.3 / +14.3 | +17.2 | -4.7 | -24.5 | +25.6 / -8.5 | -666 / -782 | +20.9 | 0.07 / 1.00 | 1.00 | 35 | OK-PRIOR [OK-PRIOR] |

### Item 3: profit cut

Live-mirror rows (MULT 30, win 5, persist 5, secs_fav <= 5, by arm): arm 0.2: fires 16, L6M cut +0.0, PRE cut +0.0, d mean L6M -26; arm 0.3: fires 11, L6M cut +0.0, PRE cut +0.0, d mean L6M -47; arm 0.4: fires 10, L6M cut +0.0, PRE cut +0.0, d mean L6M -47; arm 0.5: fires 7, L6M cut +0.0, PRE cut +0.0, d mean L6M -35; arm 0.6: fires 4, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.7: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.8: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.9: fires 0, L6M cut +0.0, PRE cut +0.0, d mean L6M +0

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=5 persist=3 wall_ticks=8` | 3304 | +32.2 / +32.2 / +11.0 | +13.1 | -3.7 | -24.3 | +30.4 / -6.5 | -486 / -709 | +23.5 | 0.01 / 0.79 | 1.00 | 39 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=5 take win=5 persist=3 wall_ticks=8` | 3292 | +31.1 / +31.1 / +11.0 | +13.3 | -2.9 | -25.8 | +29.3 / -5.6 | -480 / -670 | +23.2 | 0.03 / 0.72 | 1.00 | 41 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=5 persist=2 wall_ticks=8` | 3344 | +31.2 / +31.2 / +10.0 | +16.7 | -1.1 | -23.6 | +28.6 / -4.9 | -666 / -653 | +18.9 | 0.02 / 0.44 | 1.00 | 42 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit M7 * pct>=0.2 pulled_mult>=5 secs_fav<=2 take win=5 persist=1 wall_ticks=8` | 3301 | +30.1 / +30.1 / +11.9 | +20.0 | -5.8 | -21.4 | +27.6 / -9.6 | -646 / -715 | +22.7 | 0.01 / 0.97 | 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=5 persist=1 wall_ticks=8` | 3064 | +29.7 / +29.7 / +13.0 | +20.4 | -4.3 | -12.3 | +28.0 / -6.9 | -454 / -755 | +20.4 | 0.08 / 0.83 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=2 take win=3 persist=1 wall_ticks=8` | 3335 | +30.3 / +30.3 / +10.6 | +20.3 | -3.8 | -24.5 | +28.0 / -7.3 | -613 / -718 | +20.3 | 0.05 / 0.90 | 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=3 persist=1 wall_ticks=8` | 3368 | +30.0 / +30.0 / +11.7 | +19.6 | -3.2 | -25.0 | +27.6 / -6.8 | -615 / -700 | +20.7 | 0.01 / 0.92 | 1.00 | 33 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=15 persist=3 wall_ticks=8` | 3300 | +30.2 / +30.2 / +10.8 | +14.6 | -3.8 | -23.5 | +27.7 / -7.5 | -638 / -755 | +20.4 | 0.03 / 0.83 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=5 take win=3 persist=1 wall_ticks=8` | 3359 | +30.0 / +30.0 / +11.7 | +20.0 | -3.1 | -24.8 | +27.6 / -6.6 | -607 / -707 | +20.9 | 0.02 / 0.89 | 1.00 | 33 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=8 persist=2 wall_ticks=8` | 3132 | +30.2 / +30.2 / +10.5 | +18.0 | -0.5 | -11.6 | +28.1 / -3.5 | -535 / -748 | +20.2 | 0.08 / 0.48 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit M7 * pct>=0.2 pulled_mult>=5 secs_fav<=10 take win=10 persist=3 wall_ticks=8` | 3328 | +30.1 / +30.1 / +10.6 | +14.7 | -1.8 | -24.3 | +27.6 / -5.4 | -643 / -615 | +20.2 | 0.03 / 0.64 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit M7 * pct>=0.2 pulled_mult>=5 secs_fav<=10 take win=8 persist=3 wall_ticks=8` | 3311 | +30.0 / +30.0 / +10.8 | +14.8 | -3.7 | -23.4 | +27.7 / -7.1 | -595 / -694 | +20.6 | 0.04 / 0.85 | 1.00 | 39 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=8 persist=2 wall_ticks=8` | 3223 | +30.1 / +30.1 / +10.2 | +17.3 | -2.8 | -20.2 | +27.7 / -6.4 | -628 / -845 | +18.5 | 0.06 / 0.70 | 1.00 | 29 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=15 persist=3 wall_ticks=8` | 3342 | +29.9 / +29.9 / +10.7 | +14.6 | -2.1 | -23.8 | +27.3 / -5.8 | -659 / -616 | +19.7 | 0.04 / 0.62 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit M7 * pct>=0.2 pulled_mult>=5 secs_fav<=10 take win=15 persist=3 wall_ticks=8` | 3339 | +29.9 / +29.9 / +10.7 | +14.6 | -2.1 | -25.2 | +27.3 / -5.9 | -659 / -602 | +19.7 | 0.08 / 0.71 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=2 take win=2 persist=1 wall_ticks=8` | 3300 | +29.8 / +29.8 / +11.0 | +20.5 | -4.7 | -25.1 | +27.7 / -7.8 | -548 / -695 | +19.2 | 0.04 / 0.90 | 1.00 | 39 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=10 persist=3 wall_ticks=8` | 3340 | +29.9 / +29.9 / +10.7 | +14.7 | -2.1 | -25.1 | +27.3 / -5.8 | -654 / -596 | +19.9 | 0.06 / 0.67 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=15 persist=2 wall_ticks=8` | 3326 | +30.1 / +30.1 / +9.6 | +17.0 | -2.5 | -20.9 | +26.9 / -7.1 | -811 / -771 | +16.2 | 0.02 / 0.70 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit M7 * pct>=0.2 pulled_mult>=3 secs_fav<=10 take win=8 persist=3 wall_ticks=8` | 3334 | +29.8 / +29.8 / +10.7 | +14.7 | -2.1 | -25.1 | +27.2 / -5.8 | -663 / -632 | +19.6 | 0.05 / 0.67 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit M7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=15 persist=2 wall_ticks=8` | 3338 | +30.0 / +30.0 / +9.6 | +16.9 | -2.5 | -24.0 | +26.8 / -7.2 | -817 / -753 | +16.1 | 0.04 / 0.70 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |


## A7

### Item 2: adaptive trail vs the fixed trail (same grid)

Best fixed tighten (p=0): `profit A7 * pct>=0.3 adapt 15 p=0 lo=0.25 hi=3 tag=s persist=1` L6M cut +7.3, equal-mean +5.3, d mean -360. Best adaptive overall: `profit A7 * pct>=0.3 adapt 30 p=-1 lo=0.5 hi=2 tag=s persist=1` L6M cut +8.1, equal-mean +6.0, d mean -368. Best in the ORDER's direction (p<0, thick ahead tighter): `profit A7 * pct>=0.3 adapt 30 p=-1 lo=0.5 hi=2 tag=f persist=1` L6M cut +8.1, equal-mean +6.0, d mean -368. Difference adaptive minus fixed: +0.8 points of L6M stack maxDD cut (positive = the state-dependent distance helps).

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit A7 * pct>=0.3 adapt 30 p=-1 lo=0.5 hi=2 tag=f persist=1` | 831 | +8.1 / +8.1 / +0.0 | +2.5 | -0.3 | +1.3 | +6.0 / -2.6 | -368 / -427 | -5.2 | 0.22 / 0.66 | 1.00 | 33 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit A7 * pct>=0.3 adapt 30 p=-1 lo=0.5 hi=2 tag=s persist=1` | 831 | +8.1 / +8.1 / +0.0 | +2.5 | -0.3 | +1.3 | +6.0 / -2.6 | -368 / -427 | -5.2 | 0.22 / 0.66 | 1.00 | 33 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit A7 * pct>=0.3 adapt 20 p=-1 lo=0.5 hi=2 tag=f persist=1` | 876 | +7.4 / +7.4 / +2.0 | +2.1 | +0.2 | -0.1 | +6.2 / -1.0 | -210 / -375 | -2.6 | 0.31 / 0.23 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit A7 * pct>=0.3 adapt 20 p=-1 lo=0.5 hi=2 tag=s persist=1` | 876 | +7.4 / +7.4 / +2.0 | +2.1 | +0.2 | -0.1 | +6.2 / -1.0 | -210 / -375 | -2.6 | 0.31 / 0.23 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit A7 * pct>=0.3 adapt 15 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 890 | +7.3 / +7.3 / +2.0 | +2.0 | +0.6 | -0.2 | +5.4 / -1.4 | -335 / -362 | -4.3 | 0.74 / 0.07 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit A7 * pct>=0.3 adapt 15 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 890 | +7.3 / +7.3 / +2.0 | +2.0 | +0.6 | -0.2 | +5.4 / -1.4 | -335 / -362 | -4.3 | 0.74 / 0.07 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit A7 * pct>=0.3 adapt 20 p=-0.5 lo=0.5 hi=2 tag=f persist=1` | 850 | +7.3 / +7.3 / +1.9 | +2.8 | -0.1 | +0.5 | +6.0 / -1.5 | -234 / -382 | -3.1 | 0.51 / 0.47 | 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit A7 * pct>=0.3 adapt 20 p=1 lo=0.25 hi=3 tag=f persist=1` | 897 | +7.4 / +7.4 / +1.3 | +2.1 | +0.7 | -0.4 | +5.5 / -1.4 | -346 / -360 | -5.0 | 0.24 / 0.02 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit A7 * pct>=0.3 adapt 20 p=1 lo=0.25 hi=3 tag=s persist=1` | 897 | +7.4 / +7.4 / +1.3 | +2.1 | +0.7 | -0.4 | +5.5 / -1.4 | -346 / -360 | -5.0 | 0.24 / 0.02 | 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit A7 * pct>=0.3 adapt 20 p=-0.5 lo=0.5 hi=2 tag=s persist=1` | 850 | +7.3 / +7.3 / +1.9 | +2.8 | -0.1 | +0.5 | +5.9 / -1.5 | -235 / -382 | -3.2 | 0.51 / 0.47 | 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit A7 * pct>=0.3 adapt 5 p=1 lo=0.5 hi=2 tag=f persist=1` | 912 | +7.4 / +7.4 / +1.4 | +2.2 | -0.3 | -1.9 | +6.0 / -1.8 | -254 / -414 | -0.9 | 0.03 / 0.02 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit A7 * pct>=0.3 adapt 5 p=1 lo=0.5 hi=2 tag=s persist=1` | 912 | +7.4 / +7.4 / +1.4 | +2.2 | -0.3 | -1.9 | +6.0 / -1.8 | -253 / -414 | -0.9 | 0.03 / 0.02 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit A7 * pct>=0.3 adapt 15 p=0.5 lo=0.5 hi=2 tag=f persist=1` | 889 | +7.3 / +7.3 / +1.8 | +1.9 | +0.6 | -0.2 | +5.4 / -1.4 | -326 / -363 | -4.1 | 0.70 / 0.06 | 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit A7 * pct>=0.3 adapt 5 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 912 | +7.3 / +7.3 / +1.5 | +2.0 | -0.3 | -1.9 | +5.8 / -2.0 | -273 / -414 | -1.7 | 0.98 / 1.00 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit A7 * pct>=0.3 adapt 5 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 912 | +7.3 / +7.3 / +1.5 | +2.0 | -0.3 | -1.9 | +5.8 / -2.0 | -273 / -414 | -1.7 | 0.98 / 1.00 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit A7 * pct>=0.3 adapt 5 p=0.5 lo=0.5 hi=2 tag=f persist=1` | 912 | +7.3 / +7.3 / +1.5 | +2.0 | -0.3 | -1.9 | +5.8 / -2.0 | -274 / -414 | -1.7 | 0.98 / 1.00 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit A7 * pct>=0.3 adapt 15 p=0 lo=0.25 hi=3 tag=f persist=1` | 840 | +7.3 / +7.3 / +1.5 | +2.6 | +0.1 | +0.4 | +5.3 / -2.1 | -360 / -393 | -5.3 | 0.36 / 0.30 | 1.00 | 39 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit A7 * pct>=0.3 adapt 15 p=0 lo=0.25 hi=3 tag=s persist=1` | 840 | +7.3 / +7.3 / +1.5 | +2.6 | +0.1 | +0.4 | +5.3 / -2.1 | -360 / -393 | -5.3 | 0.36 / 0.30 | 1.00 | 39 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit A7 * pct>=0.3 adapt 5 p=1 lo=0.25 hi=3 tag=f persist=1` | 912 | +7.3 / +7.3 / +1.4 | +2.1 | -0.3 | -1.9 | +5.7 / -1.9 | -271 / -412 | -1.5 | 0.98 / 0.02 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit A7 * pct>=0.3 adapt 30 p=1 lo=0.5 hi=2 tag=f persist=1` | 837 | +7.1 / +7.1 / +1.5 | +2.6 | +0.5 | +0.6 | +5.2 / -1.6 | -331 / -401 | -4.6 | 0.47 / 0.34 | 1.00 | 41 | OK-PRIOR [OK-PRIOR] |

### Item 3: profit cut

Live-mirror rows (MULT 30, win 5, persist 5, secs_fav <= 5, by arm): arm 0.2: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.3: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.4: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.5: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.6: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.7: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.8: fires 0, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.9: fires 0, L6M cut +0.0, PRE cut +0.0, d mean L6M +0

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit A7 * pct>=0.3 pulled_mult>=3 secs_fav<=2 take win=5 persist=10 wall_ticks=8` | 256 | +13.0 / +13.0 / +0.7 | +2.4 | +1.3 | -0.0 | +12.7 / +1.0 | -67 / -4 | +6.8 | 0.02 / 0.30 | 1.00 | 23 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=5 persist=1 wall_ticks=8` | 514 | +12.1 / +12.1 / +1.6 | +2.7 | +0.0 | +0.3 | +14.2 / +2.4 | +400 / -332 | +9.4 | 0.01 / 0.43 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit A7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=5 persist=1 wall_ticks=8` | 711 | +10.9 / +10.9 / +4.2 | +2.5 | +1.7 | -0.3 | +11.6 / +2.5 | +124 / -305 | +3.6 | 0.04 / 0.17 | 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit A7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=2 persist=1 wall_ticks=8` | 733 | +11.2 / +11.2 / +2.9 | +4.2 | +2.9 | -0.9 | +10.8 / +2.4 | -80 / -253 | +0.1 | 0.04 / 0.04 | 0.98 | 35 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=8 persist=1 wall_ticks=8` | 709 | +10.5 / +10.5 / +3.9 | +3.6 | +2.6 | -1.4 | +9.2 / +1.2 | -231 / -203 | -1.3 | 0.01 / 0.08 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=10 persist=2 wall_ticks=8` | 747 | +10.4 / +10.4 / +3.3 | +3.2 | +1.5 | -2.1 | +8.4 / -0.7 | -363 / -223 | -3.8 | 0.04 / 0.21 | 1.00 | 29 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit A7 * pct>=0.3 pulled_mult>=20 secs_fav<=10 take win=10 persist=2 wall_ticks=8` | 692 | +10.4 / +10.4 / +3.0 | +2.8 | +0.7 | -3.7 | +10.1 / +0.4 | -55 / -95 | -2.1 | 0.07 / 0.35 | 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit A7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=8 persist=10 wall_ticks=8` | 316 | +11.8 / +11.8 / -2.9 | +1.8 | +0.7 | -0.7 | +11.7 / +0.7 | -10 / -153 | +0.5 | 0.02 / 0.48 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit A7 * pct>=0.3 pulled_mult>=3 secs_fav<=5 take win=2 persist=5 wall_ticks=8` | 525 | +10.6 / +10.6 / +0.4 | +4.4 | -1.2 | -2.8 | +9.3 / -2.6 | -233 / -303 | +0.2 | 0.06 / 0.73 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit A7 * pct>=0.2 pulled_mult>=3 secs_fav<=5 take win=2 persist=5 wall_ticks=8` | 574 | +10.8 / +10.8 / -0.7 | +6.6 | -3.0 | -1.7 | +9.6 / -4.3 | -216 / -304 | +0.4 | 0.01 / 0.88 | 1.00 | 22 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit A7 * pct>=0.3 pulled_mult>=5 secs_fav<=10 take win=3 persist=3 wall_ticks=8` | 850 | +9.9 / +9.9 / +2.5 | +0.8 | +0.8 | -4.1 | +8.5 / -0.8 | -260 / -230 | -3.6 | 0.05 / 0.13 | 1.00 | 42 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit A7 * pct>=0.3 pulled_mult>=10 secs_fav<=10 take win=5 persist=2 wall_ticks=8` | 809 | +9.9 / +9.9 / +1.9 | +1.5 | +1.0 | -4.5 | +8.3 / -0.8 | -294 / -98 | -4.1 | 0.06 / 0.12 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit A7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=5 persist=2 wall_ticks=8` | 787 | +9.9 / +9.9 / +2.2 | +1.5 | +1.3 | -4.6 | +8.5 / -0.2 | -245 / -94 | -3.3 | 0.08 / 0.18 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=10 persist=3 wall_ticks=8` | 705 | +9.8 / +9.8 / +2.2 | +3.5 | +1.5 | -1.5 | +7.7 / -0.8 | -368 / -227 | -4.0 | 0.06 / 0.20 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit A7 * pct>=0.2 pulled_mult>=20 secs_fav<=10 take win=8 persist=3 wall_ticks=8` | 619 | +9.4 / +9.4 / +3.5 | +3.9 | +2.7 | -1.1 | +9.5 / +2.8 | +19 / -228 | +2.7 | 0.08 / 0.15 | 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit A7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=3 persist=2 wall_ticks=8` | 748 | +8.8 / +8.8 / +5.7 | +5.5 | +2.5 | -2.6 | +7.9 / +1.5 | -188 / -215 | -3.2 | 0.05 / 0.07 | 1.00 | 30 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit A7 * pct>=0.3 pulled_mult>=20 secs_fav<=10 take win=15 persist=3 wall_ticks=8` | 772 | +9.6 / +9.6 / +2.2 | +3.4 | +0.6 | -2.8 | +7.7 / -1.6 | -343 / -204 | -3.8 | 0.12 / 0.33 | 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit A7 * pct>=0.3 pulled_mult>=3 secs_fav<=2 take win=8 persist=10 wall_ticks=8` | 462 | +10.9 / +10.9 / -2.9 | +1.7 | +2.5 | -1.5 | +9.3 / +0.7 | -317 / -109 | +1.3 | 0.06 / 0.17 | 1.00 | 20 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit A7 * pct>=0.2 pulled_mult>=10 secs_fav<=10 take win=8 persist=10 wall_ticks=8` | 636 | +9.1 / +9.1 / +4.3 | +3.9 | +1.3 | -3.1 | +8.0 / +0.2 | -192 / -303 | -0.4 | 0.08 / 0.27 | 1.00 | 29 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit A7 * pct>=0.3 pulled_mult>=20 secs_fav<=5 take win=15 persist=2 wall_ticks=8` | 734 | +9.6 / +9.6 / +2.2 | +3.3 | +1.0 | -2.9 | +8.3 / -0.4 | -232 / -339 | -1.2 | 0.11 / 0.21 | 1.00 | 33 | OK-PRIOR [OK-PRIOR] |


## O7

### Item 2: adaptive trail vs the fixed trail (same grid)

Best fixed tighten (p=0): `profit O7 * pct>=0.4 adapt 5 p=0 lo=0.25 hi=3 tag=f persist=1` L6M cut +3.4, equal-mean +2.5, d mean -183. Best adaptive overall: `profit O7 * pct>=0.4 adapt 5 p=0.25 lo=0.25 hi=3 tag=f persist=1` L6M cut +3.5, equal-mean +2.7, d mean -175. Best in the ORDER's direction (p<0, thick ahead tighter): `profit O7 * pct>=0.4 adapt 5 p=-0.25 lo=0.5 hi=2 tag=s persist=1` L6M cut +3.4, equal-mean +2.3, d mean -232. Difference adaptive minus fixed: +0.1 points of L6M stack maxDD cut (positive = the state-dependent distance helps).

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit O7 * pct>=0.4 adapt 5 p=0.25 lo=0.25 hi=3 tag=f persist=1` | 266 | +3.5 / +3.5 / +2.3 | +2.1 | +0.4 | +2.5 | +2.7 / -0.5 | -175 / -441 | -2.1 | 0.95 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit O7 * pct>=0.4 adapt 5 p=0.25 lo=0.25 hi=3 tag=s persist=1` | 266 | +3.5 / +3.5 / +2.3 | +2.1 | +0.4 | +2.5 | +2.7 / -0.5 | -175 / -441 | -2.1 | 0.95 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit O7 * pct>=0.4 adapt 5 p=0.25 lo=0.5 hi=2 tag=f persist=1` | 266 | +3.5 / +3.5 / +2.3 | +2.1 | +0.4 | +2.5 | +2.7 / -0.5 | -175 / -441 | -2.1 | 0.95 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit O7 * pct>=0.4 adapt 5 p=0 lo=0.25 hi=3 tag=f persist=1` | 266 | +3.4 / +3.4 / +2.3 | +2.1 | +0.4 | +2.5 | +2.5 / -0.6 | -183 / -440 | -2.3 | 0.95 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit O7 * pct>=0.4 adapt 5 p=0 lo=0.25 hi=3 tag=s persist=1` | 266 | +3.4 / +3.4 / +2.3 | +2.1 | +0.4 | +2.5 | +2.5 / -0.6 | -183 / -440 | -2.3 | 0.95 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit O7 * pct>=0.4 adapt 5 p=-0.25 lo=0.25 hi=3 tag=f persist=1` | 267 | +3.4 / +3.4 / +2.3 | +2.1 | +0.5 | +2.4 | +2.3 / -0.7 | -232 / -438 | -3.5 | 0.99 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit O7 * pct>=0.4 adapt 5 p=-0.25 lo=0.25 hi=3 tag=s persist=1` | 267 | +3.4 / +3.4 / +2.3 | +2.1 | +0.5 | +2.4 | +2.3 / -0.7 | -232 / -438 | -3.5 | 0.99 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit O7 * pct>=0.4 adapt 5 p=-0.25 lo=0.5 hi=2 tag=f persist=1` | 267 | +3.4 / +3.4 / +2.3 | +2.1 | +0.5 | +2.4 | +2.3 / -0.7 | -232 / -438 | -3.5 | 0.99 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit O7 * pct>=0.4 adapt 10 p=-0.5 lo=0.25 hi=3 tag=f persist=1` | 265 | +3.4 / +3.4 / +2.4 | +2.1 | +0.5 | +2.8 | +3.6 / +0.7 | +36 / -458 | -1.6 | 0.96 / 0.95 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit O7 * pct>=0.4 adapt 10 p=-0.5 lo=0.25 hi=3 tag=s persist=1` | 265 | +3.4 / +3.4 / +2.4 | +2.1 | +0.5 | +2.8 | +3.6 / +0.7 | +36 / -458 | -1.6 | 0.96 / 0.95 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit O7 * pct>=0.4 adapt 10 p=-0.5 lo=0.5 hi=2 tag=f persist=1` | 265 | +3.4 / +3.4 / +2.4 | +2.1 | +0.5 | +2.8 | +3.6 / +0.7 | +36 / -458 | -1.6 | 0.96 / 0.95 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit O7 * pct>=0.4 adapt 5 p=1 lo=0.25 hi=3 tag=f persist=1` | 267 | +3.4 / +3.4 / +2.3 | +2.1 | +0.4 | +2.5 | +2.2 / -0.9 | -241 / -451 | -3.6 | 0.99 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit O7 * pct>=0.4 adapt 5 p=1 lo=0.25 hi=3 tag=s persist=1` | 267 | +3.4 / +3.4 / +2.3 | +2.1 | +0.4 | +2.5 | +2.2 / -0.9 | -241 / -451 | -3.6 | 0.99 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit O7 * pct>=0.4 adapt 5 p=1 lo=0.5 hi=2 tag=f persist=1` | 267 | +3.4 / +3.4 / +2.3 | +2.1 | +0.4 | +2.5 | +2.2 / -0.9 | -241 / -451 | -3.6 | 0.99 / 1.00 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit O7 * pct>=0.4 adapt 30 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 231 | +3.6 / +3.6 / +1.6 | +1.9 | +0.8 | +4.3 | +3.9 / +1.1 | +57 / -335 | -0.9 | 0.56 / 0.26 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit O7 * pct>=0.4 adapt 30 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 231 | +3.6 / +3.6 / +1.6 | +1.9 | +0.8 | +4.3 | +3.9 / +1.1 | +57 / -335 | -0.9 | 0.56 / 0.26 | 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit O7 * pct>=0.4 adapt 10 p=0.5 lo=0.25 hi=3 tag=f persist=1` | 265 | +3.4 / +3.4 / +2.3 | +2.1 | +0.3 | +2.8 | +2.4 / -0.7 | -197 / -452 | -2.4 | 0.96 / 0.95 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit O7 * pct>=0.4 adapt 10 p=0.5 lo=0.25 hi=3 tag=s persist=1` | 265 | +3.4 / +3.4 / +2.3 | +2.1 | +0.3 | +2.8 | +2.4 / -0.7 | -197 / -452 | -2.4 | 0.96 / 0.95 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit O7 * pct>=0.4 adapt 10 p=0.5 lo=0.5 hi=2 tag=f persist=1` | 265 | +3.4 / +3.4 / +2.3 | +2.1 | +0.3 | +2.8 | +2.4 / -0.7 | -196 / -452 | -2.4 | 0.96 / 0.95 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit O7 * pct>=0.4 adapt 20 p=0 lo=0.25 hi=3 tag=f persist=1` | 233 | +3.6 / +3.6 / +1.6 | +1.8 | +0.7 | +4.8 | +3.8 / +0.9 | +37 / -342 | -1.4 | 0.53 / 0.78 | 1.00 | 25 | OK-PRIOR [OK-PRIOR] |

### Item 3: profit cut

Live-mirror rows (MULT 30, win 5, persist 5, secs_fav <= 5, by arm): arm 0.2: fires 3, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.3: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.4: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.5: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.6: fires 2, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.7: fires 1, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.8: fires 0, L6M cut +0.0, PRE cut +0.0, d mean L6M +0; arm 0.9: fires 0, L6M cut +0.0, PRE cut +0.0, d mean L6M +0

| # | line | nfire | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | placebo p own L6M / PRE | family p | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=5 persist=5 wall_ticks=8` | 155 | +4.4 / +4.4 / +2.1 | +1.5 | -0.6 | -1.2 | +4.6 / -0.4 | +38 / -243 | +1.9 | 0.01 / 0.89 | 1.00 | 14 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit O7 * pct>=0.2 pulled_mult>=30 secs_fav<=5 take win=8 persist=2 wall_ticks=8` | 52 | +4.7 / +4.7 / +0.0 | +2.6 | -0.5 | +0.0 | +6.7 / +1.6 | +375 / -52 | +4.2 | 0.01 / 0.84 | 1.00 | 9 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=8 persist=5 wall_ticks=8` | 153 | +4.1 / +4.1 / +2.3 | +3.1 | -0.7 | -0.6 | +3.9 / -0.9 | -46 / -123 | -0.7 | 0.04 / 0.87 | 1.00 | 14 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=2 take win=8 persist=1 wall_ticks=8` | 150 | +4.0 / +4.0 / +2.3 | +1.5 | -0.0 | +0.0 | +3.3 / -0.8 | -132 / -128 | -1.3 | 0.07 / 0.80 | 1.00 | 10 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=5 take win=8 persist=3 wall_ticks=8` | 136 | +4.0 / +4.0 / +2.5 | +2.1 | -0.8 | +0.0 | +3.6 / -1.2 | -68 / -158 | +0.6 | 0.08 / 0.88 | 1.00 | 10 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=10 take win=10 persist=10 wall_ticks=8` | 93 | +4.0 / +4.0 / +2.3 | +2.2 | -0.6 | +0.0 | +4.0 / -0.6 | +11 / -83 | +2.9 | 0.02 / 0.87 | 1.00 | 8 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=2 take win=8 persist=2 wall_ticks=8` | 99 | +4.0 / +4.0 / +2.3 | +2.1 | -1.1 | +0.0 | +4.3 / -0.8 | +52 / -62 | +3.1 | 0.02 / 0.88 | 1.00 | 8 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=2 take win=10 persist=5 wall_ticks=8` | 223 | +4.0 / +4.0 / +2.3 | +3.1 | -0.8 | +0.8 | +3.4 / -1.4 | -103 / -266 | -1.1 | 0.11 / 0.98 | 1.00 | 16 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit O7 * pct>=0.3 pulled_mult>=20 secs_fav<=2 take win=15 persist=5 wall_ticks=8` | 184 | +4.0 / +4.0 / +2.3 | +3.1 | -0.8 | -1.1 | +3.7 / -1.1 | -46 / -145 | +0.2 | 0.07 / 0.93 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit O7 * pct>=0.2 pulled_mult>=10 secs_fav<=5 take win=5 persist=5 wall_ticks=8` | 181 | +4.0 / +4.0 / +2.1 | +2.8 | +0.4 | -2.4 | +4.2 / +0.6 | +37 / -190 | -1.0 | 0.01 / 0.85 | 1.00 | 16 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=10 take win=3 persist=3 wall_ticks=8` | 216 | +4.0 / +4.0 / +2.3 | +1.4 | +0.3 | +2.2 | +4.4 / +0.8 | +81 / -272 | -0.2 | 0.09 / 0.85 | 1.00 | 16 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit O7 * pct>=0.3 pulled_mult>=10 secs_fav<=5 take win=3 persist=3 wall_ticks=8` | 184 | +3.9 / +3.9 / +2.3 | +1.4 | +0.3 | +3.0 | +3.4 / -0.2 | -109 / -275 | -0.5 | 0.07 / 0.77 | 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit O7 * pct>=0.4 pulled_mult>=30 secs_fav<=2 take win=15 persist=1 wall_ticks=8` | 150 | +3.9 / +3.9 / +2.4 | +1.7 | +1.8 | +0.0 | +3.3 / +1.2 | -121 / -136 | -1.1 | 0.08 / 0.20 | 1.00 | 11 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit O7 * pct>=0.3 pulled_mult>=3 secs_fav<=2 take win=8 persist=5 wall_ticks=8` | 275 | +3.9 / +3.9 / +2.3 | +3.1 | -0.8 | +1.7 | +3.2 / -1.5 | -139 / -480 | -0.9 | 0.12 / 1.00 | 1.00 | 11 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit O7 * pct>=0.3 pulled_mult>=3 secs_fav<=2 take win=10 persist=5 wall_ticks=8` | 283 | +3.9 / +3.9 / +2.3 | +3.1 | +0.6 | +2.4 | +3.3 / +0.0 | -108 / -455 | -0.0 | 0.07 / 0.99 | 1.00 | 19 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit O7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=10 persist=5 wall_ticks=8` | 274 | +3.9 / +3.9 / +2.3 | +3.1 | +0.6 | +1.7 | +3.2 / -0.1 | -131 / -473 | -0.7 | 0.10 / 0.98 | 1.00 | 16 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit O7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=8 persist=5 wall_ticks=8` | 258 | +3.9 / +3.9 / +2.3 | +3.1 | -0.8 | +0.8 | +2.7 / -2.0 | -210 / -404 | -2.8 | 0.06 / 0.99 | 1.00 | 13 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit O7 * pct>=0.3 pulled_mult>=5 secs_fav<=2 take win=3 persist=3 wall_ticks=8` | 166 | +3.8 / +3.8 / +2.4 | +3.4 | -0.1 | -0.2 | +3.5 / -0.4 | -64 / -197 | -0.6 | 0.04 / 0.89 | 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit O7 * pct>=0.2 pulled_mult>=30 secs_fav<=5 take win=10 persist=2 wall_ticks=8` | 97 | +3.9 / +3.9 / +1.9 | +2.6 | -2.2 | +0.0 | +5.0 / -1.0 | +196 / +6 | +1.6 | 0.01 / 0.99 | 1.00 | 10 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit O7 * pct>=0.4 pulled_mult>=20 secs_fav<=2 take win=10 persist=1 wall_ticks=8` | 179 | +3.8 / +3.8 / +2.4 | +2.1 | -0.7 | -2.2 | +3.0 / -1.5 | -164 / -200 | -2.1 | 0.09 / 0.80 | 1.00 | 8 | OK-PRIOR [OK-PRIOR] |
