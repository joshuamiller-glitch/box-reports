# DS3_LIVE_CUT_VALUE - what the live cuts did (Test 2, 2026-11-08). CUT-VALUE agent
**PRE-PROOF-free zone: uses ONLY live decisions (the exits in the frozen live trade files) and real prices (owned NQ print tape). No engine, no simulated cut, no reconstructed book.** Code and row table: /mnt/l2/l2vast/_cutvalue/cv.py, rep.py, cv_rows.pkl (one row per trade). Seal ds3_all_ea/manifest_after.json 759f2258...965d2 before and after (unchanged). Never read data/live/StratTrades_DS7_<acct>.csv.

## PLAIN SENTENCE
**On live decisions and real prices, the L2 cut (ThL2Cut + PolicyCut, 109 trades: 92 D7 blind week + 17 D6 Oct 29-30) COST $58,998 gross versus holding each to the original 60/60 bracket (O7 40/90): cut P&L -$172,380, hold-to-bracket -$113,382. The saving sits in the 80 trades that went on to the stop (cut saved $83,011, about 30 pts x lots each); the cost sits in the 27 trades that went on to the target (hold earned $139,059 more) and 2 flat marks (+$2,950). The cost is concentrated: P7 alone is +$39,259 of it (13 PolicyCut + 11 ThL2Cut, 7-lot), the 5 largest single misses are all P7/P6 at $12.7-14.1k each, and ex-P7 the L2 cut cost only $19,738. The median cut saved $550. Cuts whose price then travelled >= 90 pts in the trade direction (26 trades) account for +$137k of hold advantage; every smaller-travel bin is a small saving (-$80k in total).**
Price-path cuts (PP_CUT, the older LossExit rule, 241 live trades): the cut SAVED $7,474 (cut -$806,350 vs hold -$813,824) - a wash between large offsetting legs (HM/ST/KB/SM cost, P6/K6/U6/N5 saved). All 350 live cuts together: holding would have earned $51,524 more.

## Headline numbers
| set | N | cut P&L (gross) | hold-to-bracket (gross) | hold minus cut |
|--|--|--|--|--|
| L2 cuts (ThL2Cut 70 + PolicyCut 39) | 109 | -172,380 | -113,382 | +58,998 (cut COST) |
| - D7 blind week only (92) | 92 | -140,350 | -89,098 | +51,252 (cut COST) |
| - D6 Oct 29-30 (17) | 17 | -32,030 | -24,284 | +7,746 (cut COST) |
| PP_CUT (LossExit, live acct, Oct 4-30) | 241 | -806,350 | -813,824 | -7,474 (cut SAVED) |
| all live cuts | 350 | -978,730 | -927,206 | +51,524 (cut COST) |
Net of the $4.84/contract RT proxy both legs fall by the same fees (one round trip each; cut-vs-hold differences are fee-independent). Live commission columns in all files are BLANK, so pnlNet is gross and the proxy is the only fee. Net columns are in table A.

## Scope, coverage, assumptions (every one)
* **Live data window is Oct 4 - Nov 5 2026 only.** There are no live trade files for Feb-Sep 2026 (see T_REPLICA2_LABELS.md sec 0); the "Feb-Oct" directive scope reduces to Oct 4 - Nov 5. By month = only 2026-10 and 2026-11. "Worst 20 weeks" cannot exist: only 5 trading weeks are in the files, so table G lists all 5 and G2/G3 give the worst 20 DAYS.
* Files (frozen copies, sha in MANIFEST.sha256): DualStrat_<acct>, DualStrat2_<acct>, DS3_<acct>, DS5_<acct>, DS6_<acct>, DS7 blind week (sha 424c68da...7112). Sim-account files (DualStrat_<sim-acct>/<sim-acct>, DS3_<sim-acct>, DS4_Sim3) are analysed separately (A2: 165 PP_CUT, hold better by $36,200) and are NOT in the headline. K4 test logs and the NT8 backtest csv are not live trade rows and are not used.
* **exitName vocabulary used:** CUT classes = ThL2Cut (THL2, 70), PolicyCut (POLICY, 39), any *_LossExit incl. MV_LossExit (PP_CUT, price-path rule, 406 total/241 live). **Excluded (not cuts):** Target, Stop, StopJoin, StopJoinFallback, StopJoinRejected, BookLock, ComboLock, ProfitExit, PolicyTake, ThL2Trail (profit-side trail), ProtectRejected, SessionFlat. (StackCut mentioned in the labels note does not occur in the frozen files.) DS6 rows with LossExit before the first ThL2Cut are PP_CUT; the 3x/10 s vs 30x/5 s parameter uncertainty of the 17 DS6 L2 cuts stays (labels doc sec 2).
* **Price path:** owned NQ mbp-10 PRINT tape (every trade record, quarter-point prices; finer than 1-s). warm2_prints (ts_recv) 2026-09-01 00:00Z to 10-12; warm_prints (ts_event) 10-12 to 10-30 20:59:59Z; blind_prints (ts_event) 11-01 23:00Z to 11-05 16:04:59Z (=11:04:59 ET). Not used: instr_1s / ohlcv1s forward files (prints cover every row). Coverage: all 350 live + 165 sim cuts had prints after the exit; **0 cut rows dropped for coverage**. Dropped non-cut rows: 6 (entry time 0001-01-01 or entryPx 0: DualStrat 4, DualStrat2 2) and 1 DS7 P7 trade entered 11:04:30 ET Thu (tape ends). Walk truncated by tape end: 0; gaps > 300 s inside any walk: 0 (no outage flagged).
* **Walk:** from the first print strictly after the exit second, in the original direction, until the first of: stop level (fill average -60 against; O7 -40), target level (+60; O7 +90), or the time exit. Hold fill assumed AT the level (no slippage, no gap-through); flagged. **Stop level: signal price is not in any file, so EVERY row uses fill average +-60 (flag stop_flag_signal_unknown = True for all rows)**; entryPx is the file's lot-averaged price. Real stops were signal-based; the bracket also assumed unchanged by PolicyBracket lines (the Policy/books may have used other stop distances; not documented per trade) and for the older lineages 60/60 is an assumption.
* **Time exit:** neither hit -> mark at the last print before the next 16:55 ET (DS6/DS7 FlattenAtHHmm; O7 16:00). 13 cuts (FLAT) all in PP_CUT or the close session. Positions are NOT held through the weekend/maintenance break. No PolicyTimeExit minutes were modelled (not recorded per trade).
* **Lots / P&L:** live qty; $20/pt per NQ contract. Cut P&L = live row pnlNet (which is gross; rows with sliced entries differ from the price-diff by up to a few $k, e.g. P7 70/30 adds); hold P&L = pnlNet + (hold price - live exitPx) x dir x $20 x qty, so slice effects cancel. Fee proxy $4.84/contract RT (FEES.md) applies equally to both legs.
* **Session clocks (ET) of the cut time:** asia 18:00-01:59, london 02:00-08:29, pre 08:30-09:29, nyam 09:30-11:59, nypm 12:00-14:59; "close" 15:00-17:59 added for the remaining clock.
* Held-at-minus-30 test: non-cut exits whose print-path adverse from entryPx (entry minute floor to exit second) reached 30; the cut counterfactual = exit at exactly -30 pts (a naive -30 rule, NOT the L2 condition) = -$600 x qty.
* **FIRST-ORDER counterfactual, flagged:** holding ignores re-entries, the flip/cascade effects on later signals (a held book blocks or delays its next signal; FlipOther), the profit-side rules that would also have acted (ThL2Trail, PolicyTake, BookLock, ComboLock) and the per-book/day loss limits. Net effects can differ in both directions.


## Tables (all USD, gross unless named net)

### A. Live account <acct>, by cut class (USD; hold_minus_cut > 0 means holding to bracket would have earned more = the cut COST that much)
| cls | N | stop | target | flat | cut_gross | hold_gross | hold_minus_cut | cut_net | hold_net | cut_saved |
|--|--|--|--|--|--|--|--|--|--|--|
| POLICY | 39 | 27 | 12 | 0 | -66,880 | -31,012 | 35,868 | -67,345 | -31,476 | -35,868 |
| PP_CUT | 241 | 163 | 68 | 10 | -806,350 | -813,824 | -7,474 | -814,941 | -822,415 | 7,474 |
| THL2 | 70 | 53 | 15 | 2 | -105,500 | -82,371 | 23,129 | -106,250 | -83,121 | -23,129 |
| L2 total (THL2+POLICY) | 109 | 80 | 27 | 2 | -172,380 | -113,382 | 58,998 | -173,595 | -114,597 | -58,998 |
| ALL live cuts | 350 | 243 | 95 | 12 | -978,730 | -927,206 | 51,524 | -988,536 | -937,012 | -51,524 |

### A2. Sim accounts (<sim-acct>/Sim3/<sim-acct>), PP_CUT only, NOT in headline
| cls | N | stop | target | flat | cut_gross | hold_gross | hold_minus_cut | cut_net | hold_net | cut_saved |
|--|--|--|--|--|--|--|--|--|--|--|
| PP_CUT | 165 | 102 | 62 | 1 | -102,880 | -66,680 | 36,200 | -104,221 | -68,021 | -36,200 |

### B. By book (live, all classes)
| cls | book | N | stop | target | flat | hold_minus_cut |
|--|--|--|--|--|--|--|
| POLICY | A7 | 7 | 3 | 4 | 0 | 6,140 |
| POLICY | H7 | 1 | 1 | 0 | 0 | -600 |
| POLICY | K7 | 11 | 10 | 1 | 0 | -2,905 |
| POLICY | M7 | 4 | 3 | 1 | 0 | -1,155 |
| POLICY | O7 | 2 | 1 | 1 | 0 | 2,140 |
| POLICY | P7 | 13 | 8 | 5 | 0 | 32,958 |
| POLICY | X3 | 1 | 1 | 0 | 0 | -710 |
| PP_CUT | A6 | 7 | 5 | 2 | 0 | -75 |
| PP_CUT | H6 | 5 | 4 | 1 | 0 | 905 |
| PP_CUT | HM | 38 | 18 | 13 | 7 | 67,591 |
| PP_CUT | K5 | 15 | 10 | 5 | 0 | -4,496 |
| PP_CUT | K6 | 11 | 10 | 1 | 0 | -15,728 |
| PP_CUT | KB | 9 | 5 | 3 | 1 | 20,370 |
| PP_CUT | M5 | 9 | 6 | 3 | 0 | 455 |
| PP_CUT | M6 | 4 | 4 | 0 | 0 | -7,775 |
| PP_CUT | N5 | 5 | 4 | 1 | 0 | -15,334 |
| PP_CUT | P5 | 2 | 0 | 2 | 0 | 15,455 |
| PP_CUT | P6 | 16 | 13 | 3 | 0 | -42,703 |
| PP_CUT | PB | 3 | 3 | 0 | 0 | -9,380 |
| PP_CUT | S5 | 1 | 0 | 1 | 0 | 4,540 |
| PP_CUT | SM | 5 | 2 | 3 | 0 | 34,764 |
| PP_CUT | ST | 93 | 68 | 23 | 2 | -49,904 |
| PP_CUT | U5 | 1 | 1 | 0 | 0 | -5,475 |
| PP_CUT | U6 | 2 | 2 | 0 | 0 | -11,955 |
| PP_CUT | WT | 15 | 8 | 7 | 0 | 11,270 |
| THL2 | A6 | 1 | 1 | 0 | 0 | -605 |
| THL2 | A7 | 7 | 4 | 3 | 0 | 3,785 |
| THL2 | H6 | 1 | 1 | 0 | 0 | -550 |
| THL2 | H7 | 1 | 1 | 0 | 0 | -1,025 |
| THL2 | K6 | 6 | 4 | 1 | 1 | 1,790 |
| THL2 | K7 | 19 | 15 | 4 | 0 | -720 |
| THL2 | M6 | 2 | 2 | 0 | 0 | -1,935 |
| THL2 | M7 | 9 | 8 | 1 | 0 | 2,047 |
| THL2 | P6 | 5 | 3 | 1 | 1 | 3,650 |
| THL2 | P7 | 11 | 9 | 2 | 0 | 6,301 |
| THL2 | U6 | 2 | 1 | 1 | 0 | 5,395 |
| THL2 | U7 | 3 | 2 | 1 | 0 | 2,985 |
| THL2 | X3 | 1 | 0 | 1 | 0 | 3,625 |
| THL2 | X4 | 1 | 1 | 0 | 0 | -625 |
| THL2 | X5 | 1 | 1 | 0 | 0 | -990 |

### C. By session of the cut (live)
| cls | session | N | stop | target | flat | hold_minus_cut |
|--|--|--|--|--|--|--|
| POLICY | asia | 20 | 13 | 7 | 0 | 20,118 |
| POLICY | close | 1 | 0 | 1 | 0 | 1,805 |
| POLICY | london | 7 | 5 | 2 | 0 | 17,721 |
| POLICY | nyam | 7 | 5 | 2 | 0 | 340 |
| POLICY | nypm | 1 | 1 | 0 | 0 | -550 |
| POLICY | pre | 3 | 3 | 0 | 0 | -3,565 |
| PP_CUT | asia | 93 | 66 | 27 | 0 | -8,401 |
| PP_CUT | close | 6 | 2 | 0 | 4 | 16,440 |
| PP_CUT | london | 73 | 50 | 23 | 0 | 9,623 |
| PP_CUT | nyam | 28 | 23 | 5 | 0 | -59,409 |
| PP_CUT | nypm | 28 | 15 | 7 | 6 | 17,278 |
| PP_CUT | pre | 13 | 7 | 6 | 0 | 16,997 |
| THL2 | asia | 29 | 20 | 9 | 0 | 30,771 |
| THL2 | close | 2 | 0 | 0 | 2 | 2,950 |
| THL2 | london | 27 | 22 | 5 | 0 | -5,302 |
| THL2 | nyam | 8 | 8 | 0 | 0 | -6,640 |
| THL2 | nypm | 2 | 2 | 0 | 0 | -1,715 |
| THL2 | pre | 2 | 1 | 1 | 0 | 3,065 |

### D. By month (live, exit month)
| month | cls | N | stop | target | flat | cut_gross | hold_minus_cut |
|--|--|--|--|--|--|--|--|
| 2026-10 | PP_CUT | 241 | 163 | 68 | 10 | -806,350 | -7,474 |
| 2026-10 | THL2 | 17 | 12 | 3 | 2 | -32,030 | 7,746 |
| 2026-11 | POLICY | 39 | 27 | 12 | 0 | -66,880 | 35,868 |
| 2026-11 | THL2 | 53 | 41 | 12 | 0 | -73,470 | 15,384 |

### D2. By month, L2 cuts + PP_CUT combined
| month | N | cut_gross | hold_gross | hold_minus_cut | cut_net | hold_net |
|--|--|--|--|--|--|--|
| 2026-10 | 258 | -838,380 | -838,108 | 272 | -847,218 | -846,946 |
| 2026-11 | 92 | -140,350 | -89,098 | 51,252 | -141,318 | -90,066 |

### E. By travel in original direction after the cut (max favorable pts beyond cut price before bracket resolution), live
| L2 | tbin | N | stop | target | flat | hold_minus_cut |
|--|--|--|--|--|--|--|
| False | 0 (never above cut px) | 3 | 3 | 0 | 0 | -18,835 |
| False | 0-10 | 47 | 47 | 0 | 0 | -265,701 |
| False | 10-20 | 30 | 29 | 0 | 1 | -130,031 |
| False | 20-40 | 46 | 46 | 0 | 0 | -225,333 |
| False | 40-60 | 27 | 22 | 1 | 4 | -95,728 |
| False | 60-90 | 81 | 14 | 62 | 5 | 661,604 |
| False | >=90 | 7 | 2 | 5 | 0 | 66,550 |
| True | 0 (never above cut px) | 6 | 6 | 0 | 0 | -4,210 |
| True | 0-10 | 24 | 24 | 0 | 0 | -27,543 |
| True | 10-20 | 14 | 14 | 0 | 0 | -15,550 |
| True | 20-40 | 17 | 17 | 0 | 0 | -20,024 |
| True | 40-60 | 13 | 13 | 0 | 0 | -12,510 |
| True | 60-90 | 9 | 6 | 1 | 2 | 1,495 |
| True | >=90 | 26 | 0 | 26 | 0 | 137,339 |

### F. Held trades that reached -30 (not cut), live: by exit type
| era | exitName | N | actual_pnl | cut_at_minus30_cf | hold_gain | n_hold_better | n_hold_worse |
|--|--|--|--|--|--|--|--|
| L2 era | BookLock | 1 | -855 | -600 | -255 | 0 | 1 |
| L2 era | PolicyTake | 1 | 840 | -600 | 1,440 | 1 | 0 |
| L2 era | Stop | 2 | -3,275 | -1,200 | -2,075 | 0 | 2 |
| L2 era | StopJoin | 1 | -5,070 | -4,200 | -870 | 0 | 1 |
| L2 era | Target | 9 | 40,000 | -21,000 | 61,000 | 9 | 0 |
| price-path era | BookLock | 1 | -16,325 | -8,400 | -7,925 | 0 | 1 |
| price-path era | ComboLock | 1 | -1,330 | -8,400 | 7,070 | 1 | 0 |
| price-path era | ProfitExit | 2 | 6,710 | -10,800 | 17,510 | 2 | 0 |
| price-path era | Stop | 32 | -358,135 | -181,200 | -176,935 | 0 | 32 |
| price-path era | StopJoin | 11 | -159,240 | -80,400 | -78,840 | 0 | 11 |
| price-path era | StopJoinFallback | 12 | -198,610 | -93,600 | -105,010 | 0 | 12 |
| price-path era | StopJoinRejected | 1 | -17,205 | -8,400 | -8,805 | 0 | 1 |
| price-path era | Target | 19 | 202,750 | -101,400 | 304,150 | 19 | 0 |

### F2. Held at -30, by era and total
| index | N | actual_pnl | cut_at_minus30_cf | hold_gain | n_hold_better | n_hold_worse |
|--|--|--|--|--|--|--|
| L2 era | 14 | 31,640 | -27,600 | 59,240 | 10 | 4 |
| price-path era | 79 | -541,385 | -492,600 | -48,785 | 22 | 57 |
| ALL | 93 | -509,745 | -520,200 | 10,455 | 32 | 61 |

### F3. Held at -30, by month
| month | N | actual_pnl | cut_at_minus30_cf | hold_gain | n_hold_better | n_hold_worse |
|--|--|--|--|--|--|--|
| 2026-10 | 80 | -546,455 | -496,800 | -49,655 | 22 | 58 |
| 2026-11 | 13 | 36,710 | -23,400 | 60,110 | 10 | 3 |

### G. Weekly P&L (gross, live acct <acct>, all rows; week = Monday of trading day). Only 5-6 weeks exist in the live files, so "worst 20 weeks" = all weeks. FIRST-ORDER counterfactual: every cut (THL2, POLICY, PP_CUT) treated as held to 60/60 bracket; ignores re-entries and cascade effects
| week | trades | actual | with_cuts_held | diff |
|--|--|--|--|--|
| 2026-10-19 | 73 | -152,845 | -169,125 | -16,280 |
| 2026-10-26 | 229 | -126,930 | -178,166 | -51,236 |
| 2026-10-05 | 104 | 3,555 | 91,959 | 88,404 |
| 2026-10-12 | 104 | 24,040 | 3,424 | -20,616 |
| 2026-11-02 | 187 | 104,095 | 155,347 | 51,252 |

### G2. Worst 20 trading days with cuts (actual), and the same days with cuts held
| tday | trades | actual | with_cuts_held | diff |
|--|--|--|--|--|
| 2026-10-29 | 81 | -97,325 | -171,705 | -74,380 |
| 2026-10-23 | 33 | -85,515 | -101,795 | -16,280 |
| 2026-10-21 | 9 | -85,315 | -85,315 | 0 |
| 2026-10-26 | 37 | -63,575 | -94,255 | -30,680 |
| 2026-10-15 | 28 | -43,280 | -38,389 | 4,891 |
| 2026-10-09 | 15 | -38,965 | -25,196 | 13,769 |
| 2026-10-20 | 16 | -23,200 | -23,200 | 0 |
| 2026-10-28 | 52 | -23,020 | -27,875 | -4,855 |
| 2026-10-05 | 12 | -7,925 | -2,990 | 4,935 |
| 2026-10-13 | 27 | -5,855 | -38,690 | -32,835 |
| 2026-10-08 | 31 | -5,600 | -7,447 | -1,847 |
| 2026-10-16 | 13 | 8,675 | -11,671 | -20,346 |
| 2026-10-12 | 8 | 15,365 | 15,365 | 0 |
| 2026-10-22 | 5 | 15,925 | 15,925 | 0 |
| 2026-11-03 | 26 | 16,660 | 25,960 | 9,300 |
| 2026-10-30 | 32 | 17,315 | 22,111 | 4,796 |
| 2026-10-07 | 30 | 20,450 | 98,997 | 78,547 |
| 2026-10-19 | 10 | 25,260 | 25,260 | 0 |
| 2026-11-02 | 43 | 27,725 | 18,980 | -8,745 |
| 2026-11-04 | 76 | 28,160 | 57,207 | 29,047 |

### G3. Worst 20 trading days WITHOUT cuts (all cuts held), and actual on the same days
| tday | trades | actual | with_cuts_held | diff |
|--|--|--|--|--|
| 2026-10-29 | 81 | -97,325 | -171,705 | -74,380 |
| 2026-10-23 | 33 | -85,515 | -101,795 | -16,280 |
| 2026-10-26 | 37 | -63,575 | -94,255 | -30,680 |
| 2026-10-21 | 9 | -85,315 | -85,315 | 0 |
| 2026-10-13 | 27 | -5,855 | -38,690 | -32,835 |
| 2026-10-15 | 28 | -43,280 | -38,389 | 4,891 |
| 2026-10-28 | 52 | -23,020 | -27,875 | -4,855 |
| 2026-10-09 | 15 | -38,965 | -25,196 | 13,769 |
| 2026-10-20 | 16 | -23,200 | -23,200 | 0 |
| 2026-10-16 | 13 | 8,675 | -11,671 | -20,346 |
| 2026-10-08 | 31 | -5,600 | -7,447 | -1,847 |
| 2026-10-05 | 12 | -7,925 | -2,990 | 4,935 |
| 2026-10-12 | 8 | 15,365 | 15,365 | 0 |
| 2026-10-22 | 5 | 15,925 | 15,925 | 0 |
| 2026-11-02 | 43 | 27,725 | 18,980 | -8,745 |
| 2026-10-30 | 32 | 17,315 | 22,111 | 4,796 |
| 2026-10-19 | 10 | 25,260 | 25,260 | 0 |
| 2026-11-03 | 26 | 16,660 | 25,960 | 9,300 |
| 2026-10-06 | 16 | 35,595 | 28,595 | -7,000 |
| 2026-11-05 | 42 | 31,550 | 53,201 | 21,651 |

### G4. Weekly, only L2 cuts (THL2+POLICY) treated as held
| week | actual | l2cuts_held |
|--|--|--|
| 2026-10-05 | 3,555 | 3,555 |
| 2026-10-12 | 24,040 | 24,040 |
| 2026-10-19 | -152,845 | -152,845 |
| 2026-10-26 | -126,930 | -119,184 |
| 2026-11-02 | 104,095 | 155,347 |

### H. Sanity: DS7 blind week (gross = pnlNet in the file; commission column blank)
| index | rows | live_pnlNet_total | cut_rows | cuts_pnl | total_with_every_cut_held_to_bracket | diff | trunc_tape_end_cuts |
|--|--|--|--|--|--|--|--|
| 0 | 187 | 104,095 | 92 | -140,350 | 155,347 | 51,252 | 0 |

Blind week net of $4.84/contract RT proxy on all 423 contracts: live 102,048; with cuts held 153,300.

### I. Time to bracket hit after the cut (seconds, hold walk), L2 cuts
| outcome | count | min | 25% | 50% | 75% | max |
|--|--|--|--|--|--|--|
| FLAT | 2 | 1,069 | 1,069 | 1,069 | 1,069 | 1,069 |
| STOP | 80 | 3 | 101 | 442 | 1,075 | 8,007 |
| TARGET | 27 | 55 | 818 | 1,884 | 2,958 | 14,786 |

Gap flags (>300 s without a print in the walk): 0. Walk truncated by tape end: 0. Flat (16:55 ET / O7 16:00 time-exit mark): 13.

HEADLINE_L2: N=109 cut_vs_hold_usd=58,998 (cost 58,998); all live cuts N=350 delta=51,524
