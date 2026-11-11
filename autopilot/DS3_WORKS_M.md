# DS3_WORKS_M - T-WORKS / P7 FIX families M N O P (adaptive response, side-level stack governor, the flip, no-follow-through exit), W-M

Page stamp 2026-11-11T19:35Z. Label: PRE-PROOF, post-hoc, Shadow only, no PASS claims. Prereg autopilot/WORKS_M_PREREG.md (sha in DECISIONS.md before any cell). Code code/th_works_m/ (private tree). Reference stacks: LPB_BASE (live panel base) and JN04RM.

## Plain-sentence summary (first page, first-order only; exact sets are queued and no exact number exists yet)
Status: the hooks for all four families are written (code/th_works_m/m_hooks.py: probe, stricter confirm after a loss, side governor, flip, no-follow-through exit) and 24 exact sets (WM_*) are queued one set per job on LPB_BASE through m_mgr.py. ACTUALLY LAUNCHED at 19:36Z: 1 set (WM_N1, 0 of 6 L6M months finished); FINISHED: 0 months of any set; the box had 5-67 GB free and jobs wait on the 50-62 GB gates. Queue priority per lead: C1-C4 stricter confirm, D2 re-arm on evidence (new session extreme since the last failure), N1. The hooks have not yet run once in the engine: WM_T2 (all features on, 202610) and the identity set WM_T1 are the first proofs and must pass before any exact row is believed. JN04RM versions (WMJ_) follow after the LPB winners.
Family O (the flip): dead at first order. After two failed same-side P7 exits in a session the opposite-side signal earns 54 USD per lot (n=116, 45.7 percent wins) against 61 USD per lot for all P7 signals, so it is not a better-than-average signal; sizing it up 1.5x or 2x gives L6M cut -2.5 to -2.8 and costs the live week. The same-side signal after two failures earns -16 USD per lot (n=98): blocking it removes 11.6k of losses but also trend winners, L6M eq-cut about 0.
Family N (side governor): only fires at 0.5R or 0.75R of one-side realised loss (P7 day cap 8,400 = 1R means 1R or more almost never prints). Best: block P7 after 0.5R P7 net loss on that side, release on a new session extreme: eq-cut L6M 14.1, PRE 8.6, HOLD 9.6, 75 trades changed; it removes 15.8k of trend-week winners against 6.9k of worst-week losses and costs 22.7k in the frozen live week. The stack-wide loss count (all books, block P7) gives PRE 18 but L6M 4.6 and takes 88.7k from trend weeks.
Family M (probe / blackout): the plain blackout beats the probe at first order. Both-side 120-minute blackout: eq-cut L6M 37.3, PRE 33.6, HOLD 15.2, but it removes 178k from trend weeks and costs 41k in the live week. Probe at 0.5 after a loss, both sides, restore after the probe wins: L6M 16.6, PRE 30.0, HOLD 11.3, live week -15.9k; probe at 1 lot is lighter on the live week (-28k) with less benefit. Stricter confirm (90-s confirm, 2-3 L2 confirmations) cannot be scored first-order; exact sets WM_C1-C4 are queued.
Family P (no-follow-through exit): on all P7 trades it fails (mean -9.5k per week, trend weeks -705k). Restricted to the 3rd-and-later P7 trade of a session: exit if MFE < 12 pt after 3 minutes gives eq-cut L6M 9.8, PRE 20.9, HOLD 6.1 (841 trades, worst-20 weeks +135k, trend weeks -219k, live week -22k); Asia only, 5 minutes: 11.0 / 19.7 / 12.8, live week -19k. On M7 the chase-flagged version raises the mean (L6M +1.4k per week, eq-cut 25.8 at X=10, N=5) but PRE is near 7; K7 and U7 show little (fo_PK.csv).
Behavioural scorecard (interim, P7, first-order, my own m_card.py until W-Q's tool exists; card_fo.csv): LPB_BASE L6M has 0.4 full stops per week (-1.2k per week), 2.9 give-backs per week (MFE >= 80 percent of target, closed below 50 percent; -7.6k per week), 2.7 round-trips per week, a maximum of 5 consecutive same-side losing entries in one session and -37.4k lost on the 3rd-and-later; the frozen live week has 3 give-backs (-13.0k). The families M, N, O act on item (c) only: the 3rd-and-later loss falls to -15.3k (30-min blackout), 0 (120-min both-side blackout), -13.6k (probe 1 lot), -13.8k (N3), -19.2k (N1), unchanged for the same-side block after two failures; none of them moves full stops or give-backs by half, except the 120-minute both-side blackout (give-backs 1.5 per week, full stops 0.2) which pays for it with 41k of the live week and 178k of trend weeks. Verdict at first order: no M, N or O cell passes the standing gate (a, b, c each halved without (e) exceeding the saving, trend week not turned losing); item (b) needs a profit-side rule, not a re-entry rule. Exact numbers and the worst-10 session replay follow on the next pages.
Expressible in v1.7 today: only the plain P7 post-exit blackout (PostExitBlackoutMins, same side) and the P7 session string; probe, side governor, flip, stricter confirm and no-follow-through exit need v1.8 fields (session loss counter per side, probe-lots-after-loss with restore-on-win, per-side session governor limit in R with release on new session extreme, confirm strictness after a loss, per-trade follow-through clock). Worked rows come with the first exact winner.
Dead-lookup: no prior row for these families (hits for 'flip', 'mfe', 'stall' were profit-side HMM/EXP1/THPC cells on other books). Addendum logged in DECISIONS.md: N grid extended to 0.5R/0.75R, P first pass on roll-adjusted bars voided and rerun on raw bars.

## First-order tables (equal-lot trade list, 3.5 years of LPB_BASE trades plus the 180 frozen-week rows; ranking only, exact decides)
Columns: eqcut_* = stack maxDD cut at equal mean (percent, window L6M/PRE/HOLD), cut_* = plain maxDD cut, dmean_L6M = weekly mean change in USD, n_chg = trades changed (3.5 years), d_worst20 / d_trend20 = P&L change in the 20 worst / 20 best P7 weeks (positive = the rule removed losses; negative = it removed winners), live_d = change in the frozen live week 11-01..05.

### N side-level stack governor (192 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N|X=0.5R|act=block|loss=p7|apply=p7|sess=all|release=False | 10.8 | 9.0 | 6.1 | 9.2 | 7.3 | 4.4 | -6.8 | 313.4 | 113 | -126.6 | -34534.8 | -41883.9 |
| N|X=0.5R|act=block|loss=p7|apply=p7|sess=all|release=True | 14.1 | 8.6 | 9.6 | 9.2 | 3.4 | 4.4 | -6.8 | 1068.4 | 75 | 6853.3 | -15829.2 | -22715.8 |
| N|X=0.5R|act=block|loss=p7|apply=p7|sess=asia|release=True | 12.3 | 6.7 | 7.7 | 9.2 | 3.4 | 4.4 | -6.8 | 656.1 | 55 | 9250.9 | -13213.8 | -24610.1 |
| N|X=0.5R|act=block|loss=p7|apply=all|sess=all|release=True | 12.1 | 6.0 | -0.8 | 8.7 | 2.3 | -4.7 | -4.0 | 731.7 | 269 | 2753.6 | -10989.1 | -25733.0 |
| N|X=0.5R|act=block|loss=p7|apply=p7|sess=asia|release=False | 7.7 | 5.8 | 2.8 | 9.2 | 7.3 | 4.4 | -6.8 | -293.1 | 85 | 3469.8 | -33984.4 | -43778.3 |
| N|X=0.5R|act=half|loss=p7|apply=p7|sess=all|release=False | 5.4 | 5.7 | 3.7 | 4.0 | 4.3 | 2.2 | -2.9 | 271.9 | 104 | 3661.3 | -10920.8 | -18468.7 |
| N|X=0.5R|act=half|loss=p7|apply=p7|sess=all|release=True | 6.3 | 4.8 | 4.6 | 4.0 | 2.3 | 2.2 | -2.9 | 479.5 | 70 | 5054.0 | -5089.9 | -9941.1 |
| N|X=0.5R|act=block|loss=all|apply=p7|sess=all|release=False | 4.6 | 19.0 | 1.0 | 3.4 | 18.0 | -0.2 | -9.2 | 222.1 | 344 | 15047.7 | -88722.7 | -44114.7 |
| N|X=0.5R|act=block|loss=p7|apply=all|sess=asia|release=True | 7.9 | 4.0 | -2.9 | 6.3 | 2.3 | -4.7 | -4.0 | 332.5 | 225 | 5151.2 | -9602.3 | -27627.4 |
| N|X=0.5R|act=half|loss=p7|apply=p7|sess=asia|release=True | 5.4 | 3.8 | 3.7 | 4.0 | 2.3 | 2.2 | -2.9 | 289.1 | 53 | 5054.0 | -4381.6 | -10888.3 |

### M probe after a loss and plain blackout reference (52 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M|blackout=120|same=False|sess=all | 37.3 | 33.6 | 15.2 | 31.6 | 27.5 | 7.5 | -20.0 | 1945.0 | 1759 | 255222.0 | -177880.1 | -41310.3 |
| M|blackout=15|same=False|sess=all | 28.8 | 25.8 | -1.5 | 19.6 | 16.3 | -14.5 | -2.8 | 2194.7 | 432 | 66591.1 | -26316.9 | -600.0 |
| M|blackout=15|same=False|sess=asia | 19.4 | 21.8 | -4.8 | 17.2 | 19.7 | -7.7 | -0.3 | 588.2 | 180 | 51733.6 | -28812.4 | -5278.7 |
| M|probe=0.5|scope=both|restore=probe|sess=all | 16.6 | 30.0 | 11.3 | 8.4 | 23.1 | 2.6 | -0.9 | 1716.4 | 1220 | 100789.1 | -51260.0 | -15860.4 |
| M|probe=0.5|scope=both|restore=anywin|sess=all | 16.6 | 30.0 | 11.3 | 8.4 | 23.1 | 2.6 | -0.9 | 1716.4 | 1220 | 100789.1 | -51260.0 | -15860.4 |
| M|blackout=120|same=False|sess=asia | 10.7 | 11.6 | 10.6 | 5.9 | 6.8 | 5.9 | -27.3 | 1149.8 | 826 | 183828.8 | -133948.5 | -29365.8 |
| M|probe=1|scope=both|restore=probe|sess=all | 9.8 | 18.9 | 11.6 | 5.4 | 14.9 | 7.3 | -13.1 | 805.8 | 1220 | 165925.0 | -91596.2 | -28346.4 |
| M|probe=1|scope=both|restore=anywin|sess=all | 9.8 | 18.9 | 11.6 | 5.4 | 14.9 | 7.3 | -13.1 | 805.8 | 1220 | 165925.0 | -91596.2 | -28346.4 |
| M|blackout=15|same=True|sess=all | 8.9 | 26.0 | 0.1 | 1.1 | 19.6 | -8.5 | -2.9 | 1469.4 | 212 | 31625.9 | -996.6 | -600.0 |
| M|probe=0.5|scope=same|restore=probe|sess=all | 8.9 | 20.9 | -0.1 | 7.6 | 19.8 | -1.5 | 2.8 | 295.7 | 648 | 43594.7 | -24377.1 | -10648.9 |

### O flip (28 cells)
Flip statistics (mean P&L per lot of the flip signal versus all P7 signals and versus the same-side signal after the same failures):
| cell | n_flip | flip_mean_per_lot | flip_win | all_p7_mean_per_lot | all_p7_win | same_n | same_mean_per_lot | same_win |
|---|---|---|---|---|---|---|---|---|
| Ostat|k=2|sess=all | 116.0 | 54.21 | 0.46 | 61.26 | 0.45 | 98.0 | -15.77 | 0.42 |
| Ostat|k=2|sess=asia | 56.0 | 42.77 | 0.45 | 64.83 | 0.45 | 40.0 | -248.11 | 0.35 |
| Ostat|k=3|sess=all | 13.0 | 117.78 | 0.46 | 61.26 | 0.45 | 13.0 | -442.98 | 0.31 |
| Ostat|k=3|sess=asia | 8.0 | -51.53 | 0.38 | 64.83 | 0.45 | 7.0 | -670.73 | 0.29 |

### O flip (28 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O|k=2|flip_m=full|sess=asia | 1.3 | 16.8 | 3.3 | 0.0 | 15.7 | 2.1 | 0.0 | 236.1 | 40.0 | 8335.4 | -4099.4 | -0.0 |
| O|k=3|flip_m=2.0|sess=all | 0.8 | 6.7 | 0.8 | 0.0 | 6.0 | 0.0 | 0.0 | 143.9 | 13.0 | 2565.4 | 721.9 | -0.0 |
| O|k=2|flip_m=2.0|sess=all | 1.1 | 0.8 | 3.1 | -2.8 | -3.1 | -0.7 | -4.4 | 691.9 | 116.0 | -23118.5 | -1853.6 | 8351.1 |
| O|k=3|flip_m=1.5|sess=all | 0.5 | 4.1 | 0.5 | 0.0 | 3.6 | 0.0 | 0.0 | 95.9 | 13.0 | 1881.3 | -38.9 | -0.0 |
| O|k=3|flip_m=full|sess=all | 0.3 | 11.1 | 0.3 | 0.0 | 10.8 | 0.0 | 0.0 | 48.0 | 10.0 | 10782.7 | -57.8 | -0.0 |
| O|k=3|flip_m=2.0|sess=asia | 0.0 | 6.0 | 0.0 | 0.0 | 6.0 | 0.0 | 0.0 | 0.0 | 8.0 | 5989.1 | -3278.7 | -0.0 |
| O|k=3|flip_m=full|sess=asia | 0.0 | 10.8 | 0.0 | 0.0 | 10.8 | 0.0 | 0.0 | 0.0 | 6.0 | 10782.7 | -2459.0 | -0.0 |
| O|k=3|flip_m=1.5|sess=asia | 0.0 | 3.6 | 0.0 | 0.0 | 3.6 | 0.0 | 0.0 | 0.0 | 8.0 | 3593.1 | -1639.4 | -0.0 |
| O|k=2|same_side_m=0.5|sess=all | -0.0 | 4.7 | -1.9 | 0.0 | 4.7 | -1.9 | 0.0 | -0.8 | 70.0 | 413.6 | -2441.1 | -8192.3 |
| O|k=3|same_side_m=0.5|sess=all | -0.1 | 1.7 | -0.1 | 0.0 | 1.8 | 0.0 | 0.0 | -25.3 | 10.0 | -564.3 | -326.6 | -2387.8 |

### P no-follow-through exit on P7 (370 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P|mfe|X=12|N=5|scope=late3|sess=asia | 11.0 | 19.7 | 12.8 | 14.6 | 23.0 | 16.3 | -2.2 | -692.4 | 406 | 73435.7 | -222842.2 | -19405.2 |
| P|mfe|X=5|N=5|scope=late3|sess=asia | 10.4 | 21.0 | 12.3 | 8.7 | 19.5 | 10.6 | -3.2 | 331.6 | 213 | 67888.7 | -127551.4 | 3744.0 |
| P|mfe|X=12|N=3|scope=late3|sess=all | 9.8 | 20.9 | 6.1 | 18.0 | 28.0 | 14.6 | 1.9 | -1542.5 | 841 | 135366.8 | -218754.3 | -22384.2 |
| P|mfe|X=12|N=3|scope=late3|sess=asia | 9.0 | 16.0 | 10.9 | 14.6 | 21.1 | 16.4 | -2.0 | -1050.6 | 488 | 101304.0 | -231587.3 | -27821.6 |
| P|mfe|X=8|N=5|scope=late3|sess=asia | 5.8 | 16.3 | 7.7 | 13.8 | 23.4 | 15.6 | -5.3 | -1455.0 | 300 | 87392.7 | -171866.9 | -1491.8 |
| P|mfe|X=12|N=5|scope=late3|sess=all | 4.1 | 24.5 | 6.0 | 9.1 | 28.5 | 11.0 | 1.8 | -899.1 | 694 | 104857.2 | -210539.2 | -16136.4 |
| P|mfe|X=5|N=8|scope=late3|sess=asia | 1.0 | 16.0 | 3.0 | 3.7 | 18.3 | 5.7 | -3.4 | -593.1 | 160 | 46488.2 | -105250.4 | 2924.0 |
| P|mfe|X=10|N=5|scope=late3|sess=asia | 0.5 | 13.5 | 2.5 | 8.4 | 20.3 | 10.3 | -2.2 | -1359.7 | 357 | 71356.7 | -212591.7 | -14709.2 |
| P|mfe|X=5|N=10|scope=late3|sess=asia | 0.0 | 13.8 | 2.1 | 2.4 | 15.8 | 4.4 | -3.3 | -511.2 | 143 | 43854.2 | -80295.6 | 2784.0 |
| P|mfe|X=12|N=5|scope=reentry|sess=all | -1.4 | 5.3 | -3.9 | 11.7 | 17.5 | 9.5 | -13.0 | -2199.8 | 997 | 112590.6 | -306735.5 | -37107.0 |

### P no-follow-through exit on K7/M7/U7 (444 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PM7|mfe|X=5|N=3|scope=chase|sess=all | 18.0 | 10.6 | 10.4 | 13.9 | 6.1 | 5.9 | 0.3 | 797.3 | 1163 | 22087.0 | -43147.0 | -3282.0 |
| PM7|mfe|X=8|N=3|scope=chase|sess=all | 19.4 | 8.8 | 11.2 | 16.5 | 5.5 | 8.1 | -0.9 | 564.5 | 1543 | 32255.0 | -56200.5 | -101.8 |
| PM7|mfe|X=10|N=3|scope=chase|sess=all | 17.7 | 8.2 | 13.3 | 14.9 | 5.1 | 10.4 | -7.7 | 536.1 | 1760 | 26033.0 | -60006.5 | -3754.0 |
| PM7|mfe|X=10|N=5|scope=chase|sess=all | 25.8 | 7.2 | 13.2 | 20.3 | 0.3 | 6.8 | -5.8 | 1366.3 | 1473 | 14624.0 | -42846.5 | -4783.0 |
| PM7|mfe|X=5|N=5|scope=chase|sess=all | 20.1 | 7.1 | 10.3 | 14.7 | 0.7 | 4.1 | -4.4 | 1092.1 | 933 | 5802.5 | -30407.0 | -3599.0 |
| PM7|mfe|X=10|N=2|scope=chase|sess=all | 14.3 | 6.9 | 12.2 | 13.5 | 6.0 | 11.4 | -8.2 | 175.6 | 2014 | 17802.5 | -56532.5 | -2063.8 |
| PM7|mfe|X=12|N=5|scope=chase|sess=all | 25.4 | 6.2 | 18.9 | 21.0 | 0.7 | 14.2 | -9.6 | 1088.9 | 1661 | 8879.0 | -43581.0 | -4362.0 |
| PM7|mfe|X=12|N=3|scope=chase|sess=all | 19.8 | 6.1 | 17.2 | 18.2 | 4.3 | 15.6 | -7.2 | 361.3 | 1943 | 17992.5 | -55481.0 | -3754.0 |
| PM7|mfe|X=5|N=3|scope=all|sess=all | 11.7 | 5.7 | 7.0 | 8.2 | 2.0 | 3.3 | -8.8 | 627.3 | 1629 | 25605.0 | -53862.0 | -7954.0 |
| PM7|mfe|X=15|N=5|scope=chase|sess=all | 30.9 | 5.0 | 19.3 | 25.8 | -2.1 | 13.2 | -9.5 | 1379.9 | 1907 | 16153.5 | -47900.0 | -4362.0 |
