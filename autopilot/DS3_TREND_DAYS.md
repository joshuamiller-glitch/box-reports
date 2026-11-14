# DS3_TREND_DAYS - P9 trend days from D7's own trades (W-TD)

**VERDICT (plain): 17 trend-day cells scored, none yet passes the tolerant gate in L3M, L6M and the older windows together; best by L6M drawdown is C5_c1 (DD cut 0.0%, d mean 1794 $/wk, gate Y). No PASS claim.**

Rebuilt 2026-11-14T20:24Z (epoch 1794687846) by code/th_trendevent/td_loop.sh. Research only, NO PASS claim. Prereg autopilot/TRENDEVENT_PREREG.md (sha 902e8acf65f05aa0 + addenda A b7faa5d87fc820e1, B 69bc618cfb2721f2, C faab906024e809c7, D 6bf6f88e5100fc03, E c61df02737498986 in DECISIONS.md, logged before scoring).

Identity: TL3_TD_ID 202610 (hook path active, neutral): 598 trades net_fee 25943.82 vs JN05W2 598 / 25943.82 -> IDENTICAL (trade lists equal row by row).
Base JN05W2 exact engine, all layers ON; score = MEASURED net (gross - $4.84/ct RT - excess slip entry +0.23 / cut +0.40 / stop +0.44 / target 0 pt, +1.36 pt on non-target exits 08:30-08:44 ET); Globex label day; windows L3M (08-01..10-31) L6M (05-01..) HOLD (2025-11-01..) GAP (2025-07..10) PRE (2024-10..2025-06) X' (2023-04..2024-09). Max DD of the recent windows is one week (2026-W44): every row shows the DD cut with and without that week. Calendar not needed here: all 43 months scored (X' included).

## 1. Where the stack makes its money (hindsight market character, JN05W2 measured net, 43 months)

Trend day (hindsight, only to describe the market): |close-open| >= 0.45 x day range and day range >= 1.0 x expected range (median range of the previous 20 days). 314 of 921 Globex days (34%) are trend days; they carry $1,376,936 of $1,624,235 total (85%), mean $4,385/day vs $407/day on the other days.

With-trend vs counter-trend trade P&L (trade side vs the day's close-open direction): on trend days with-trend $2,691,358, counter $-1,314,422; on non-trend days with $1,175,441, counter $-928,142. Counter-trend trades are NOT a loss centre on the best days in hindsight: see the best-30 table (several best days are two-way days where the counter side made most of the money), so a blanket 'block counter-trend' only works if the causal call is early and right.

### 1b. The 30 best stack days: what capped the profit

| day | pnl | pnl_with | pnl_ctr | eff | rr | trendday | n | lots | tgt | stop | cut | dayhalt | in_trade | session_lots0 | time_block | disabled | screen_gate | blackout | no_trade_zone | halts | left2x_usd | left_usd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 20240926 | 54920 | 50845 | 4075 | 0.30 | 1.20 | False | 29 | 61.0 | 22 | 0 | 7 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 48455 | 129870 |
| 20240730 | 53224 | 37257 | 15968 | 0.62 | 2.00 | True | 30 | 65.0 | 23 | 0 | 7 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 40805 | 233995 |
| 20241220 | 47412 | 2195 | 45217 | 0.17 | 3.23 | False | 41 | 83.0 | 28 | 1 | 12 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 10240 | 69550 |
| 20240419 | 41867 | 38246 | 3621 | 0.81 | 1.89 | True | 26 | 61.0 | 18 | 0 | 8 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 40795 | 154120 |
| 20260921 | 39848 | 40778 | -931 | 0.89 | 2.66 | True | 23 | 45.0 | 19 | 0 | 4 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 45080 | 432610 |
| 20250127 | 39461 | 42532 | -3071 | 0.39 | 2.52 | False | 48 | 104.0 | 27 | 1 | 20 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 58775 | 610695 |
| 20260609 | 39114 | 12902 | 26212 | 0.20 | 3.40 | False | 61 | 87.0 | 33 | 5 | 23 | 0.0 | 84.0 | 82.0 | 271.0 | 1290.0 | 0.0 | 0.0 | 3.0 | nan | 26380 | 389505 |
| 20260619 | 38364 | 32254 | 6110 | 0.29 | 0.69 | False | 33 | 76.0 | 19 | 2 | 12 | 0.0 | 98.0 | 45.0 | 43.0 | 180.0 | 0.0 | 0.0 | 3.0 | BOOK GIVE#BACK LOCK day # peak # | 40375 | 86955 |
| 20260508 | 37540 | 43618 | -6078 | 0.89 | 1.99 | True | 29 | 68.0 | 22 | 0 | 7 | 0.0 | 122.0 | 62.0 | 81.0 | 229.0 | 0.0 | 0.0 | 4.0 | nan | 53110 | 380350 |
| 20260330 | 37093 | 3437 | 33656 | 0.13 | 1.02 | False | 43 | 65.0 | 25 | 1 | 17 | 0.0 | 101.0 | 73.0 | 122.0 | 439.0 | 0.0 | 0.0 | 3.0 | nan | 13795 | 39990 |
| 20260708 | 36816 | 14068 | 22748 | 0.10 | 0.92 | False | 56 | 106.0 | 30 | 2 | 24 | 5.0 | 57.0 | 58.0 | 209.0 | 842.0 | 0.0 | 0.0 | 1.0 | DAY PROFIT cap # | 25955 | 98540 |
| 20250731 | 36144 | 20275 | 15869 | 0.65 | 2.42 | True | 22 | 41.0 | 16 | 1 | 5 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 22795 | 108460 |
| 20260723 | 34274 | 24793 | 9481 | 0.43 | 1.29 | False | 69 | 133.0 | 37 | 2 | 30 | 0.0 | 54.0 | 59.0 | 188.0 | 643.0 | 0.0 | 0.0 | 1.0 | nan | 55895 | 486925 |
| 20240620 | 32731 | 23763 | 8968 | 0.44 | 1.81 | False | 23 | 39.0 | 18 | 3 | 2 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 12080 | 39710 |
| 20260626 | 31369 | 21021 | 10348 | 0.60 | 1.05 | True | 65 | 96.0 | 30 | 5 | 30 | 19.0 | 29.0 | 49.0 | 379.0 | 1127.0 | 0.0 | 11.0 | 3.0 | BOOK GIVE#BACK LOCK day # peak # | 37085 | 193385 |
| 20260513 | 31238 | 32404 | -1166 | 0.77 | 1.20 | True | 42 | 80.0 | 23 | 3 | 16 | 0.0 | 90.0 | 72.0 | 101.0 | 317.0 | 0.0 | 0.0 | 3.0 | nan | 46175 | 191870 |
| 20260414 | 31048 | 33002 | -1954 | 0.94 | 0.84 | False | 20 | 31.0 | 17 | 1 | 2 | 0.0 | 109.0 | 61.0 | 71.0 | 131.0 | 0.0 | 0.0 | 2.0 | nan | 32680 | 139775 |
| 20250324 | 30957 | 30957 | 0 | 0.81 | 0.75 | False | 17 | 34.0 | 15 | 0 | 2 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 32220 | 99580 |
| 20250508 | 30313 | 22825 | 7488 | 0.53 | 0.82 | False | 32 | 81.0 | 20 | 3 | 9 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 40585 | 127395 |
| 20251001 | 29774 | 18646 | 11128 | 0.40 | 1.66 | False | 29 | 60.0 | 18 | 1 | 10 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 22980 | 68825 |
| 20240731 | 29589 | 31193 | -1605 | 0.90 | 2.65 | True | 27 | 48.0 | 17 | 1 | 9 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 39615 | 308200 |
| 20251211 | 29339 | 3430 | 25908 | 0.10 | 1.37 | False | 30 | 63.0 | 17 | 1 | 12 | 37.0 | 64.0 | 45.0 | 110.0 | 318.0 | 0.0 | 0.0 | 1.0 | BOOK GIVE#BACK LOCK day # peak # | 9610 | 38890 |
| 20260601 | 29106 | 20979 | 8128 | 0.24 | 0.79 | False | 27 | 49.0 | 18 | 2 | 7 | 36.0 | 101.0 | 45.0 | 136.0 | 344.0 | 0.0 | 0.0 | 4.0 | BOOK GIVE#BACK LOCK day # peak # | 29625 | 82630 |
| 20240222 | 28746 | 31254 | -2508 | 0.80 | 1.77 | True | 20 | 38.0 | 14 | 0 | 6 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 33055 | 123950 |
| 20260309 | 27790 | 24429 | 3361 | 0.58 | 2.35 | True | 51 | 98.0 | 28 | 3 | 20 | 6.0 | 85.0 | 59.0 | 281.0 | 796.0 | 0.0 | 0.0 | 3.0 | BOOK GIVE#BACK LOCK day # peak # | 37230 | 404650 |
| 20260512 | 27377 | 33380 | -6003 | 0.39 | 1.68 | False | 42 | 77.0 | 23 | 1 | 18 | 0.0 | 74.0 | 52.0 | 116.0 | 445.0 | 0.0 | 0.0 | 5.0 | nan | 50415 | 353265 |
| 20240102 | 27342 | 29954 | -2613 | 0.68 | 2.12 | True | 18 | 35.0 | 11 | 1 | 6 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 31140 | 109485 |
| 20260811 | 27303 | 14726 | 12577 | 0.38 | 0.54 | False | 39 | 66.0 | 23 | 0 | 16 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 26540 | 67715 |
| 20240807 | 27049 | 399 | 26650 | 0.29 | 1.58 | False | 37 | 68.0 | 20 | 1 | 16 | nan | nan | nan | nan | nan | nan | nan | nan | nan | 11990 | 83050 |
| 20260303 | 27019 | 32581 | -5562 | 0.42 | 1.46 | False | 35 | 70.0 | 18 | 3 | 14 | 84.0 | 67.0 | 45.0 | 182.0 | 771.0 | 0.0 | 0.0 | 1.0 | BOOK GIVE#BACK LOCK day # peak # | 46795 | 279385 |

Columns: eff = |close-open|/range, rr = range / expected range; tgt/stop/cut = exits by type; dayhalt / in_trade / session_lots0 / time_block / disabled / screen_gate / blackout / no_trade_zone = number of SKIPPED signals that Globex day by reason (engine log of the identity run TL3_TD_ID; "disabled" = book not enabled in that session; "in_trade" = the book already holds a position; session_lots0 = the lot table says 0 for that book/session); halts = the day-profit / give-back / day-cap lines that fired; left2x_usd = extra a target twice as wide would have paid on the with-trend TARGET exits IF it had been reached (min(favourable move after exit to the day extreme, one more target distance) x lots x $20; ignores the stop-outs a wider target also brings, so an upper bound); left_usd = same to the day extreme (looser upper bound).

Skipped signals on the 30 best days, by cause: dayhalt 187, in_trade 1135, session_lots0 807, time_block 2290, disabled 7872, screen_gate 0, blackout 11, no_trade_zone 37. Days with at least one day-done/give-back/day-cap halt line: 7 of 30. STACK-cap truncations (London, same-side lots cap): see the cap dump counts in section 2.

## 2. The causal call in the base world (TL3_TD_ID dump, 43 of 43 months so far)

Static view before the engine response: base trades ENTERED while the call was active, split with-trend (same side as the call) / counter-trend. "right_dir" = share of called days whose close-open direction equals the call side; "trendday" = share of called days that are trend days in hindsight (all days: about 34%).

| call | mode | win | days | of_days | call_min_per_day | right_dir | trendday | n_with | pnl_with | n_ctr | pnl_ctr | static_ct | static_sz15 | static_sz2 | pnl_called_days | pnl_all |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C1 | K3K4 | L3M | 27 | 65 | 676.19 | 0.89 | 0.78 | 66 | 19193 | 30 | -4431 | 4431 | 9596 | 19193 | 155914 | 207173 |
| C1 | K3K4 | L6M | 63 | 131 | 614.35 | 0.89 | 0.70 | 193 | 55438 | 88 | 8611 | -8611 | 27719 | 55438 | 429778 | 562288 |
| C1 | K3K4 | HOLD | 129 | 257 | 801.78 | 0.88 | 0.69 | 359 | 44395 | 149 | -20962 | 20962 | 22198 | 44395 | 693029 | 774202 |
| C1 | K3K4 | GAP | 43 | 89 | 800.98 | 0.93 | 0.60 | 94 | 19871 | 54 | -170 | 170 | 9935 | 19871 | 234691 | 183796 |
| C1 | K3K4 | PRE | 94 | 192 | 830.59 | 0.90 | 0.69 | 210 | -10107 | 99 | 11848 | -11848 | -5054 | -10107 | 403548 | 358392 |
| C1 | K3K4 | XP | 182 | 383 | 779.51 | 0.92 | 0.70 | 359 | 43851 | 131 | 7399 | -7399 | 21926 | 43851 | 864238 | 307845 |
| C2 | K1K3 | L3M | 58 | 65 | 595.14 | 0.86 | 0.38 | 173 | 36479 | 69 | -14867 | 14867 | 18240 | 36479 | 266948 | 207173 |
| C2 | K1K3 | L6M | 122 | 131 | 610.98 | 0.84 | 0.37 | 443 | 84765 | 171 | 16974 | -16974 | 42383 | 84765 | 652093 | 562288 |
| C2 | K1K3 | HOLD | 227 | 257 | 685.80 | 0.82 | 0.40 | 779 | 92350 | 294 | -14133 | 14133 | 46175 | 92350 | 976414 | 774202 |
| C2 | K1K3 | GAP | 78 | 89 | 779.22 | 0.85 | 0.33 | 171 | 5082 | 68 | -3532 | 3532 | 2541 | 5082 | 252354 | 183796 |
| C2 | K1K3 | PRE | 157 | 192 | 697.67 | 0.81 | 0.41 | 400 | 22478 | 164 | 9515 | -9515 | 11239 | 22478 | 519293 | 358392 |
| C2 | K1K3 | XP | 302 | 383 | 693.84 | 0.83 | 0.43 | 625 | 106354 | 226 | -10352 | 10352 | 53177 | 106354 | 845847 | 307845 |
| C3 | K1K2K3 | L3M | 39 | 65 | 519.49 | 0.82 | 0.38 | 135 | 26982 | 58 | -11164 | 11164 | 13491 | 26982 | 258933 | 207173 |
| C3 | K1K2K3 | L6M | 71 | 131 | 617.17 | 0.83 | 0.42 | 310 | 82452 | 118 | -7363 | 7363 | 41226 | 82452 | 529236 | 562288 |
| C3 | K1K2K3 | HOLD | 140 | 257 | 603.14 | 0.79 | 0.43 | 540 | 113937 | 202 | -27721 | 27721 | 56968 | 113937 | 875053 | 774202 |
| C3 | K1K2K3 | GAP | 53 | 89 | 680.02 | 0.83 | 0.38 | 119 | -12895 | 44 | 194 | -194 | -6448 | -12895 | 143091 | 183796 |
| C3 | K1K2K3 | PRE | 107 | 192 | 559.65 | 0.79 | 0.47 | 292 | 7255 | 114 | 6147 | -6147 | 3628 | 7255 | 548587 | 358392 |
| C3 | K1K2K3 | XP | 227 | 383 | 627.49 | 0.81 | 0.43 | 474 | 85762 | 158 | 2588 | -2588 | 42881 | 85762 | 766667 | 307845 |
| C4 | 3of4 | L3M | 45 | 65 | 583.53 | 0.84 | 0.47 | 146 | 33179 | 61 | -12240 | 12240 | 16589 | 33179 | 242885 | 207173 |
| C4 | 3of4 | L6M | 92 | 131 | 602.96 | 0.85 | 0.48 | 365 | 86962 | 144 | 1722 | -1722 | 43481 | 86962 | 511011 | 562288 |
| C4 | 3of4 | HOLD | 182 | 257 | 707.77 | 0.82 | 0.48 | 646 | 118411 | 250 | -26303 | 26303 | 59205 | 118411 | 898200 | 774202 |
| C4 | 3of4 | GAP | 66 | 89 | 811.14 | 0.86 | 0.39 | 159 | -4132 | 65 | -1536 | 1536 | -2066 | -4132 | 241648 | 183796 |
| C4 | 3of4 | PRE | 129 | 192 | 711.68 | 0.82 | 0.50 | 323 | 3581 | 142 | 11083 | -11083 | 1790 | 3581 | 557012 | 358392 |
| C4 | 3of4 | XP | 275 | 383 | 691.86 | 0.83 | 0.47 | 563 | 85504 | 202 | 2111 | -2111 | 42752 | 85504 | 882300 | 307845 |
| C5 | all4 | L3M | 15 | 65 | 799.87 | 1.00 | 0.80 | 55 | 12996 | 27 | -3354 | 3354 | 6498 | 12996 | 135242 | 207173 |
| C5 | all4 | L6M | 33 | 131 | 811.27 | 0.97 | 0.82 | 138 | 50928 | 62 | -474 | 474 | 25464 | 50928 | 425445 | 562288 |
| C5 | all4 | HOLD | 66 | 257 | 821.89 | 0.91 | 0.79 | 252 | 40872 | 100 | -21736 | 21736 | 20436 | 40872 | 594942 | 774202 |
| C5 | all4 | GAP | 26 | 89 | 651.85 | 0.92 | 0.69 | 54 | 11108 | 33 | 1561 | -1561 | 5554 | 11108 | 117211 | 183796 |
| C5 | all4 | PRE | 60 | 192 | 741.58 | 0.88 | 0.78 | 177 | -8814 | 70 | 7812 | -7812 | -4407 | -8814 | 401422 | 358392 |
| C5 | all4 | XP | 113 | 383 | 794.08 | 0.95 | 0.75 | 263 | 52269 | 82 | 4613 | -4613 | 26134 | 52269 | 693648 | 307845 |

static_ct = P&L change if every counter-trend entry during the call were skipped (no re-routing of the capital, no path effects); static_sz15 / static_sz2 = +50% / +100% of the with-trend entries P&L (ignores that bigger size also magnifies the with-trend losers' stops: they are in pnl_with already). pnl_called_days > pnl_all means the days that never get called lose money in total. These static numbers are NOT drawdown results: section 3 is the engine.

## 3. Engine cells (exact JN05W2 + hook), scope all stack

Columns: dMean = cell minus JN05W2 $/wk; DDcut = max-DD cut in % (positive = smaller drawdown; second figure with week 2026-W44 removed from both); dWorstWk = worst week cell minus reference ($); stops_wk = full stops per week cell(ref); best5 = % of the reference five best weeks kept; w2l = winning weeks turned losing; wf2w = % of 2-week blocks in which cell >= reference in $ (the walk-forward block test; the call parameters are FIXED in the prereg, there is nothing to refit); gate = tolerant gate (maxDD not worse by >2%, worst week not worse by >2% of ref, mean not lower by >3%).

| cell | win | dMean | DDcut | DDcut_noW44 | dWorstWk | stops_wk | best5 | w2l | wf2w | gate |
|---|---|---|---|---|---|---|---|---|---|---|
| C1_pr2 | L3M | -5803 | 29.3 | 36.9 | 16908 | 9.69(10.46) | 66 | 1 | 29 | n |
| C2_c1 | L3M | 4026 | 6.7 | -6.3 | 3741 | 10.46(10.46) | 118 | 0 | 86 | Y |
| C2_lift | L3M | 292 | 6.6 | 0.0 | 3704 | 10.46(10.46) | 99 | 0 | 86 | Y |
| C1_pr1 | L3M | -2189 | 1.7 | 1.4 | 4806 | 10.23(10.46) | 91 | 0 | 57 | n |
| C2_pr1 | L3M | -902 | 1.7 | -7.2 | 4806 | 10.08(10.46) | 99 | 0 | 43 | n |
| C1_ct | L3M | 124 | 0.0 | -1.7 | 0 | 10.46(10.46) | 101 | 0 | 71 | n |
| C1_sz2 | L3M | 554 | 0.0 | -14.6 | 0 | 10.38(10.46) | 104 | 0 | 57 | Y |
| C1_tg | L3M | 534 | 0.0 | 0.0 | 0 | 10.46(10.46) | 101 | 0 | 86 | Y |
| C1_tg2tr | L3M | -572 | 0.0 | -14.7 | 0 | 10.46(10.46) | 102 | 0 | 43 | n |
| C1_lift | L3M | -14 | 0.0 | 0.0 | 0 | 10.46(10.46) | 99 | 0 | 86 | n |
| C1_c2 | L3M | 464 | 0.0 | 0.0 | 0 | 10.38(10.46) | 100 | 0 | 57 | n |
| C2_tg | L3M | 386 | 0.0 | 0.0 | 0 | 10.62(10.46) | 96 | 0 | 71 | n |
| C5_sz2 | L3M | 480 | 0.0 | -12.2 | 0 | 10.38(10.46) | 103 | 0 | 57 | Y |
| C5_c1 | L3M | 1688 | -0.0 | -11.1 | 0 | 10.38(10.46) | 105 | 0 | 71 | Y |
| C5_c1 | L6M | 1794 | 0.0 | -11.1 | 0 | 10.95(11.03) | 103 | 0 | 79 | Y |
| C1_c1 | L3M | 2210 | -0.0 | 0.0 | 0 | 10.38(10.46) | 105 | 0 | 86 | Y |
| C2_ct | L3M | 290 | -1.7 | -2.5 | -941 | 10.62(10.46) | 101 | 0 | 71 | n |
| C2_sz2 | L3M | 1984 | -5.9 | -24.0 | 0 | 10.31(10.46) | 113 | 0 | 86 | n |

## 4. Cost on wrongly called days and capital kept on non-trend days

Per cell and window: days with at least one called minute (cell's own dump); right_dir / wrong_dir = call side vs the day's close-open direction (hindsight); delta P&L = cell minus JN05W2 summed over those days. dPnl_uncalled should be ~0 (days never called); a non-zero value is path dependence (week/lock state carried over).

| cell | win | called_days | right_dir | wrong_dir | dPnl_called | dPnl_wrong_dir | dPnl_called_trendday | dPnl_called_nontrend | dPnl_uncalled |
|---|---|---|---|---|---|---|---|---|---|
| C1_pr2 | L3M | 27 | 24 | 3 | -25504 | -31595 | 10242 | -35745 | -49938 |
| C2_c1 | L3M | 58 | 50 | 8 | 52344 | 89 | 58959 | -6614 | 0 |
| C2_lift | L3M | 58 | 50 | 8 | 3791 | 0 | 7044 | -3254 | 0 |
| C1_pr1 | L3M | 27 | 24 | 3 | 8302 | -8118 | 23351 | -15049 | -36762 |
| C2_pr1 | L3M | 58 | 50 | 8 | -10501 | -20073 | 46528 | -57028 | -1231 |
| C1_ct | L3M | 27 | 24 | 3 | 1614 | -794 | 2408 | -794 | 0 |
| C1_sz2 | L3M | 27 | 24 | 3 | 7207 | -1036 | 9316 | -2110 | 0 |
| C1_tg | L3M | 27 | 24 | 3 | 6937 | 71 | 6866 | 71 | 0 |
| C1_tg2tr | L3M | 27 | 24 | 3 | -7442 | 356 | -7798 | 356 | 0 |
| C1_lift | L3M | 27 | 24 | 3 | -176 | -3167 | 2990 | -3167 | 0 |
| C1_c2 | L3M | 27 | 24 | 3 | 6033 | -4346 | 10379 | -4346 | 0 |
| C2_tg | L3M | 58 | 50 | 8 | 5019 | 1070 | 20794 | -15775 | 0 |
| C5_sz2 | L3M | 15 | 15 | 0 | 6246 | 0 | 8075 | -1828 | 0 |
| C5_c1 | L3M | 15 | 15 | 0 | 21950 | 0 | 24404 | -2454 | 0 |
| C5_c1 | L6M | 33 | 32 | 1 | 47012 | -1191 | 47297 | -285 | 0 |

## 5. Exact placebos (call table shifted 11 / 23 / 37 business days, same clock time, same actions)

| cell | win | dMean | DDcut | DDcut_noW44 | dWorstWk | stops_wk | best5 | w2l | wf2w | gate |
|---|---|---|---|---|---|---|---|---|---|---|
| C1_pr2 | L3M | -5803 | 29.3 | 36.9 | 16908 | 9.69(10.46) | 66 | 1 | 29 | n |
| C2_c1 | L3M | 4026 | 6.7 | -6.3 | 3741 | 10.46(10.46) | 118 | 0 | 86 | Y |
| C2_lift | L3M | 292 | 6.6 | 0.0 | 3704 | 10.46(10.46) | 99 | 0 | 86 | Y |
| C1_pr1 | L3M | -2189 | 1.7 | 1.4 | 4806 | 10.23(10.46) | 91 | 0 | 57 | n |

## 6. Would a competent discretionary trader do it?

- Block counter-trend once the day is called (a_ct): yes in principle (a trader stops fading a one-way tape) but only after the call is firm; the hindsight table shows several best days profit on the counter side, so an early or wrong call costs real money.
- Lots x1.5 or x2.0 with-trend (a_sz, a_sz2; JN05W2 has no STACK cap, see prereg addendum B): yes, 'press the winner' is what a desk does, provided the first with-trend trades already paid (K1) and risk per day stays inside the loss cap.
- Wider target x1.5 / x2 with a give-back trail (a_tg, a_tg2tr): yes, the standard way to stay with a trend; the trail protects the open profit.
- Relax the day-profit cap and give-back lock with-trend only (a_lift): a trader does not stop at an arbitrary dollar number while the tape trends; the risk is giving back more than the cap saved.

## 7. Best setting with evidence and plain strength

- No cell passes in every window scored yet. Best by L6M drawdown: **C5_c1** L3M: DD cut -0.0%, dMean 1688, gate Y, L6M: DD cut 0.0%, dMean 1794, gate Y. Strength: not a lead.

## 8. Hand-off
Best rules are sent to W-JV (a5266a6235f1c7bbb) as they land (SendMessage); the exact spec of every cell is td_cells.py (call: H=90 min, r=1.0, n1=2, dist=0.15, frozen from the X calibration, prereg addendum A; actions as in the prereg).
