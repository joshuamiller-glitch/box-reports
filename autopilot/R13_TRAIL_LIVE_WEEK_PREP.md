# R13_TRAIL_LIVE_WEEK_PREP - held-out live week (frozen file only, 187 rows 11-01..05) for T-TRAIL-L2 (REDO-R13, 2026-11-10 ~17:40Z; PRE-PROOF; depth-pollution caveat: the live NQ book carried ES/RTY levels, the owned 1-s state arrays are clean mbp-10; the 10 v1.5 bug state cuts of 11-08/09 are not in this week)
Files (private, /mnt/l2/l2vast/_r13/trail/): live_week_trades.csv (one row per live trade: book, sess, sd, qty, times, prices, exit_name, tdist = target distance, mfe = max pct of target, mfe_pts, mae_pts, target, giveback, weak_giveback, pnl_net), live_week_paths.parquet (323,072 rows: one per trade-second from the entry second to the exit second; columns trade, book, t, fav, pct, ext, dd, secs_fav, med, pulled_own_W / pulled_against_W / mult_own_W / mult_against_W for W = 2,5,10,15, imb5, imb10, depth8_own, depth8_against, delta_against_1, delta_against_5; all signed with the trade; times = epoch seconds, trade = row index i of live_week_trades.csv). Code outputs/code/th_r13/r13_trail_prep.py.
Definitions: target distance = live exit - entry for the 86 rows that exited at Target, else the book's nominal (K7 P7 M7 U7 H7 A7 60, O7 90, X3 50, X4 40, X5 60); pct = favourable mid excursion / that distance; MFE = max pct; GIVE-BACK = MFE >= 0.5 and exit below entry; WEAK GIVE-BACK = MFE >= 0.5, exit above entry, not Target. tot_rel / ahead_rel / wall_ahead_mult / ice / sweep are not in the paths file (half-hour baseline and deeper book history): the evaluator computes them from the same state days.
### Per book
| book | trades | targets | mfe_ge_05 | giveback | weak_giveback | giveback_pnl | weak_pnl |
|--|--|--|--|--|--|--|--|
| A7 | 23 | 7 | 12 | 4 | 1 | -2485 | 504 |
| H7 | 3 | 1 | 3 | 2 | 0 | -1974 | 0 |
| K7 | 64 | 31 | 45 | 13 | 1 | -11888 | 539 |
| M7 | 28 | 13 | 18 | 4 | 1 | -4682 | 839 |
| O7 | 3 | 1 | 2 | 1 | 0 | -446 | 0 |
| P7 | 53 | 28 | 34 | 7 | 0 | -25059 | 0 |
| U7 | 6 | 3 | 3 | 0 | 0 | 0 | 0 |
| X3 | 3 | 1 | 1 | 0 | 0 | 0 | 0 |
| X4 | 2 | 1 | 2 | 1 | 0 | -1772 | 0 |
| X5 | 2 | 0 | 1 | 0 | 1 | 0 | 1763 |

### Live week (frozen, 187 rows): targets and give-backs per book / session (MFE from the 1-s mid; rows without a state path: 0)
| book | sess | trades | targets | mfe_ge_05 | giveback | weak_giveback | giveback_pnl | weak_pnl |
|--|--|--|--|--|--|--|--|--|
| A7 | asia | 23 | 7 | 12 | 4 | 1 | -2485 | 504 |
| H7 | asia | 1 | 0 | 1 | 1 | 0 | -1372 | 0 |
| H7 | nyam | 2 | 1 | 2 | 1 | 0 | -601 | 0 |
| K7 | asia | 32 | 15 | 23 | 7 | 1 | -7521 | 539 |
| K7 | london | 13 | 5 | 8 | 3 | 0 | -2449 | 0 |
| K7 | nyam | 11 | 7 | 9 | 2 | 0 | -1312 | 0 |
| K7 | nypm | 8 | 4 | 5 | 1 | 0 | -606 | 0 |
| M7 | london | 22 | 11 | 15 | 3 | 1 | -3966 | 839 |
| M7 | nyam | 6 | 2 | 3 | 1 | 0 | -716 | 0 |
| O7 | nyam | 3 | 1 | 2 | 1 | 0 | -446 | 0 |
| P7 | asia | 31 | 17 | 22 | 5 | 0 | -19597 | 0 |
| P7 | london | 15 | 6 | 8 | 2 | 0 | -5462 | 0 |
| P7 | nyam | 7 | 5 | 4 | 0 | 0 | 0 | 0 |
| U7 | asia | 1 | 1 | 1 | 0 | 0 | 0 | 0 |
| U7 | london | 5 | 2 | 2 | 0 | 0 | 0 | 0 |
| X3 | pre | 3 | 1 | 1 | 0 | 0 | 0 | 0 |
| X4 | london | 2 | 1 | 2 | 1 | 0 | -1772 | 0 |
| X5 | london | 2 | 0 | 1 | 0 | 1 | 0 | 1763 |

### Give-back trade list (MFE >= 0.5 of target, exit below entry)
| book | sess | entryTime | exitTime | qty | exit_name | mfe | mae_pts | pnl_net |
|--|--|--|--|--|--|--|--|--|
| A7 | asia | 2026-11-01 22:13:00 | 2026-11-02 01:44:15 | 1 | BookLock | 0.82 | -18.62 | -396.18 |
| H7 | asia | 2026-11-01 22:50:00 | 2026-11-02 01:21:10 | 2 | ThL2Cut | 0.54 | -33.76 | -1372.36 |
| P7 | asia | 2026-11-01 23:03:00 | 2026-11-02 01:21:10 | 2 | ThL2Cut | 0.52 | -34.88 | -1407.36 |
| M7 | london | 2026-11-02 02:35:00 | 2026-11-02 04:18:39 | 3 | ThL2Cut | 0.57 | -42.96 | -2423.54 |
| X4 | london | 2026-11-02 04:39:15 | 2026-11-02 07:06:08 | 2 | ThL2Cut | 0.64 | -42.51 | -1772.36 |
| P7 | london | 2026-11-02 07:51:01 | 2026-11-02 08:36:55 | 2 | PolicyCut | 0.51 | -31.99 | -1352.36 |
| M7 | nyam | 2026-11-02 10:22:00 | 2026-11-02 10:47:27 | 1 | ThL2Cut | 0.95 | -36.62 | -716.18 |
| H7 | nyam | 2026-11-02 10:25:00 | 2026-11-02 10:38:19 | 1 | PolicyCut | 0.50 | -32.25 | -601.18 |
| K7 | asia | 2026-11-02 18:21:00 | 2026-11-02 18:45:37 | 1 | ThL2Cut | 0.54 | -29.88 | -616.18 |
| P7 | asia | 2026-11-02 18:47:01 | 2026-11-02 20:29:16 | 4 | PolicyCut | 0.91 | -31.99 | -2409.72 |
| K7 | asia | 2026-11-02 20:09:00 | 2026-11-02 22:36:58 | 1 | PolicyCut | 0.61 | -39.88 | -806.18 |
| K7 | asia | 2026-11-03 01:48:01 | 2026-11-03 02:55:35 | 1 | Stop | 0.53 | -79.75 | -1661.18 |
| O7 | nyam | 2026-11-03 09:41:00 | 2026-11-03 09:53:39 | 1 | PolicyCut | 0.78 | -22.00 | -446.18 |
| K7 | nyam | 2026-11-03 10:57:00 | 2026-11-03 11:18:33 | 1 | PolicyCut | 0.82 | -32.38 | -656.18 |
| K7 | asia | 2026-11-03 18:06:00 | 2026-11-03 18:37:42 | 2 | PolicyCut | 0.88 | -43.13 | -1782.36 |
| A7 | asia | 2026-11-03 18:13:03 | 2026-11-03 18:31:21 | 1 | PolicyCut | 0.57 | -27.62 | -566.18 |
| P7 | asia | 2026-11-03 18:13:03 | 2026-11-03 18:37:42 | 7 | PolicyCut | 0.84 | -45.61 | -6518.26 |
| P7 | asia | 2026-11-03 20:44:00 | 2026-11-03 20:47:21 | 7 | PolicyCut | 0.69 | -35.36 | -5223.26 |
| A7 | asia | 2026-11-03 22:02:00 | 2026-11-03 22:16:47 | 1 | PolicyCut | 0.84 | -32.12 | -636.18 |
| K7 | asia | 2026-11-03 23:24:00 | 2026-11-03 23:39:04 | 1 | ThL2Cut | 0.53 | -34.88 | -706.18 |
| A7 | asia | 2026-11-04 00:44:00 | 2026-11-04 01:24:11 | 1 | PolicyCut | 0.75 | -43.62 | -886.18 |
| P7 | asia | 2026-11-04 00:53:00 | 2026-11-04 01:24:11 | 7 | PolicyCut | 0.81 | -40.33 | -4038.26 |
| K7 | asia | 2026-11-04 01:06:00 | 2026-11-04 01:19:12 | 2 | ThL2Cut | 0.55 | -35.26 | -1367.36 |
| K7 | london | 2026-11-04 02:12:00 | 2026-11-04 02:21:31 | 1 | ThL2Cut | 0.56 | -35.25 | -656.18 |
| K7 | london | 2026-11-04 03:36:00 | 2026-11-04 04:02:07 | 1 | PolicyCut | 0.54 | -55.50 | -1096.18 |
| P7 | london | 2026-11-04 03:36:00 | 2026-11-04 04:02:07 | 4 | PolicyCut | 0.61 | -51.63 | -4109.72 |
| K7 | nyam | 2026-11-04 11:06:00 | 2026-11-04 11:08:05 | 1 | ThL2Cut | 0.76 | -30.00 | -656.18 |
| K7 | nypm | 2026-11-04 14:33:00 | 2026-11-04 15:31:33 | 1 | PolicyCut | 0.83 | -29.12 | -606.18 |
| K7 | asia | 2026-11-04 21:18:01 | 2026-11-04 21:35:06 | 1 | PolicyCut | 0.84 | -30.12 | -581.18 |
| M7 | london | 2026-11-05 02:05:00 | 2026-11-05 02:22:04 | 1 | ThL2Cut | 0.57 | -39.12 | -791.18 |
| K7 | london | 2026-11-05 03:12:01 | 2026-11-05 04:09:53 | 1 | ThL2Cut | 0.98 | -34.75 | -696.18 |
| M7 | london | 2026-11-05 05:08:00 | 2026-11-05 07:22:47 | 1 | ThL2Cut | 0.98 | -39.75 | -751.18 |

### Weak give-back (MFE >= 0.5, exited above entry, not at target)
| book | sess | entryTime | exitTime | qty | exit_name | mfe | pnl_net |
|--|--|--|--|--|--|--|--|
| K7 | asia | 2026-11-01 20:09:01 | 2026-11-01 21:54:37 | 1 | ThL2Trail | 0.95 | 538.82 |
| A7 | asia | 2026-11-01 20:12:00 | 2026-11-01 21:54:37 | 1 | ThL2Trail | 0.91 | 503.82 |
| M7 | london | 2026-11-02 06:58:00 | 2026-11-02 08:05:20 | 1 | PolicyTake | 0.87 | 838.82 |
| X5 | london | 2026-11-02 07:20:00 | 2026-11-02 08:05:09 | 2 | PolicyTake | 0.97 | 1762.64 |
