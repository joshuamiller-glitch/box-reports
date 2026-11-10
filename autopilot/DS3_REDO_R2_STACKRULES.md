# DS3_REDO_R2_STACKRULES - A06 slots and B02 quiet-overnight on the state base (S1b-COMB), first version 2026-11-10 12:00Z

> FIRST-ORDER SCREEN ONLY (pnl per lot x lots; exact runs pending in the SZ-CORE queue), ROLL-EXCL (33 trades alive across a roll carry weight 0), PRE-PROOF, post-hoc, Shadow only. STANDING RULE: every layer stays ON; this page proposes settings only; the live setting is the reference row and stays unless a setting beats it out of sample. Numbers = sz_core.Z.score (all-week maxDD/w20/Ulcer, carry week dropped from means only). Rolls in the NQ bars fixed. Old-vs-new base: pending (old-base R2 cells were never published; OLD-BASE rerun of these grids not yet done).

## Summary block: setting | live value | best on the state base | holds OOS? | change recommended | panel field
| setting | live value | best on the state base (first-order) | holds OOS? | change? | panel field |
|--|--|--|--|--|--|
| A06 slots (x0.5 half-hours) | K7 0330,0400,0430,0500,0530,1430,1900,1930,2030,2100; P7 0330,0500,0830; U7 0200,0830; H7 0400,0530,0830,1030,1230,1300,1400,1830 | per-book greedy over 48 slots x {0,.5,1}: see below; stack greedy sets 74 slots (mostly x0) | NO: walk-forward of the picking procedure 27% raw, -22% at equal mean, mean -6634$/wk | NO: live slots stay | SlotList per book (x0.5 only in v1.5; x0 slots need v1.6) |
| B02 (quiet overnight, K7/P7/H7 x0.5, 10:30-18:00, lookback 20 d, ratio < .85) | L20 / .85 / x0.5 / 1030-1800 | best by SEL: K7P7H7 L20 thr 1.20 allday x0.0 (size-down of 7888 trades, d mean -2644$/wk) | EXACT: the first-order leads fail the engine; picking-procedure WF (all down-only B02 cells): 23% raw, 21% eq-mean, mean -449$/wk; restricted to the live form (K7P7H7, 10:30-18:00): 3% raw, -2% eq, -780$/wk | NO: live B02 retained. EXACT (ROLLFIX1) FAILS: K7P7H7 L20 thr 1.0 all-day x0 L6M cut -11.8, PRE -20.1; all books L6M -6.7, PRE -17.1 (first-order had said +35/+34) | B02 lookback / threshold / action fields |
| StackCut Asia | 50%, Asia-only, first same-side stop | EXACT (SZ-CDE, DS3_REDO_R2b_STACKCUT.md): best candidate = cut other books on EITHER side after an Asia stop: L6M cut +4.3, d mean +1055, equal-mean +7.7, PRE +0.7 / +284, but worst-20 L6M -8.3 / PRE -11.0 (worse); pct 25/75/100, all-sessions, second-stop variants all deepen L6M maxDD; OFF is -4.5 (reference row only) | no bi-weekly WF available | NO: live retained | StackCutPct, StackAsiaOnly |
| HM5 vs 1/3/15-min for H7 | HM5 | not run (bar-type engine change; no exact set exists) | n/a | NO: live retained, untested | H7 BarMinutes |










<!--FGHFINAL-->
## EXACT vs FIRST-ORDER (ROLLFIX1 engine, exact rows read with sz_exact.py score; written 2026-11-10 14:01Z)
| set | exact maxDD cut % (d mean $/wk) by window | exact worst-20 cut % (+ = better) |
|--|--|--|
| P7 7,4,0,4,0,0 (Q_P7_744), 39 months | L1M 22.5 (-3419) / L3M 22.5 (-939) / L6M 22.5 (+489) / HOLD 10.0 (-436) / PRE 14.8 (-1021) / X' 18.8 (+613) | L6M 28 / HOLD 18 / PRE 16 |
| P7 6,4,0,4,0,0 (FGH_P644), 33 months | L1M 51.0 (+13573) / L3M 33.9 (+567) / L6M 33.9 (-4043) / PRE 41.8 (-1713) / X' 63.4 (+2191) | L6M -5 / PRE 33 |
| P7 5,4,0,4,0,0 (Q_P7_544), 39 months | L1M 2.4 (+630) / L3M 2.5 (-3672) / L6M 2.5 (-4392) / HOLD 18.6 (-5361) / PRE 7.1 (-2858) / X' 55.1 (+795) | L6M -37 / HOLD 15 / PRE 19 |
| P7 4,4,0,4,0,0 (FGH_P444), 23 months | L1M 51.1 (+13583) / L3M -19.2 (-7306) / L6M -19.2 (-8758) / PRE 20.0 (-3849) | L6M -78 / PRE 30 |
| stack greedy lot table, down (FGH_GREEDY), 33 months | L1M 62.7 (+23154) / L3M 22.5 (-3992) / L6M 22.5 (-4826) / PRE 55.8 (-3899) / X' 72.0 (+4780) | L6M -58 / PRE 42 |
| H ATR >= 1.6 P7 x0 (FGH_BESTH), 33 months | L1M 63.8 (-388) / L3M 26.8 (+1817) / L6M 26.0 (+1903) / PRE 35.6 (-262) / X' 34.2 (+1482) | L6M 30 / PRE 15 |
| B02 K7P7H7 L20 thr 1.0 all-day x0 (FGH_B02A), 23 months | L1M 47.9 (+15278) / L3M 2.7 (+163) / L6M -11.8 (+767) / PRE -20.1 (-2149) | L6M -19 / PRE 7 |
| B02 all books L20 thr 1.0 all-day x0 (FGH_B02B), 23 months | L1M 55.0 (+16159) / L3M 12.9 (-708) / L6M -6.7 (-283) / PRE -17.1 (-2191) | L6M -33 / PRE 13 |
| K cap 3 (Q_KCAP3, reference to compare, not mine), 39 months | L1M 29.8 (-4656) / L3M 29.8 (+307) / L6M 26.9 (+2833) / HOLD 15.3 (+1379) / PRE 15.8 (+15) / X' 41.3 (+2029) | L6M 69 / HOLD 25 / PRE 17 |

### Rule 2a labels on the EXACT rows (USER DECISION 13:45Z: PRE mean floor = 25%% of the live PRE mean; old fixed -$1k label beside)
| set | L6M cut / d mean | PRE cut / d mean | bi-weekly exact WF % beat | allowed PRE deepening | PRE mean floor (new) | label NEW | label OLD (-$1k floor) |
|--|--|--|--|--|--|--|--|
| Q_P7_744 | 22.5 / +489 | 14.8 / -1021 | 73 | 25% | -3490 | **OK-PRIOR** | RECENT-ONLY |
| FGH_P644 | 33.9 / -4043 | 41.8 / -1713 | 66 | 25% | -3490 | **OK-PRIOR** | RECENT-ONLY |
| FGH_P444 | -19.2 / -8758 | 20.0 / -3849 | 77 | 15% | -3490 | **RECENT-ONLY** | RECENT-ONLY |
| FGH_GREEDY | 22.5 / -4826 | 55.8 / -3899 | 57 | 15% | -3490 | **RECENT-ONLY** | RECENT-ONLY |
| FGH_PBESTH | 26.0 / +1903 | 35.6 / -262 | 36 | 15% | -3490 | **OK-PRIOR** | OK-PRIOR |
| FGH_PB02A | -11.8 / +767 | -20.1 / -2149 | 32 | 15% | -3490 | **RECENT-ONLY** | RECENT-ONLY |
| FGH_PB02B | -6.7 / -283 | -17.1 / -2191 | 36 | 15% | -3490 | **RECENT-ONLY** | RECENT-ONLY |

Exact reading: P7 7,4,0,4 is the only table that cuts L6M and PRE without costing L6M mean (+489). 6,4,0,4 cuts more but gives up -$4.0k/wk (equal-mean cut 22.2 vs 23.9) and its L6M worst-20 is worse; 4,4,0,4 DEEPENS L6M maxDD (-19%) although the first-order screen said +28%; the stack-greedy table is +22.5 at -$4.8k/wk, equal-mean cut ~1: not a candidate. First-order screens are not verdicts. NEW EXACT (23 months each): the P7 ATR>=1.6 skip (FGH_PBESTH) holds exact: L6M +26.0 (d mean +1903), L3M +26.8, PRE +35.6 (-262), worst-20 L6M +30 -> label LEAD+ / OK-PRIOR (selected as the best of 854 H cells, family p ~1; the ATR family bi-weekly WF with the equal-mean picker beats live in 70% of periods, OOS cut +33%, d mean -$2.9k/wk because the picker also chooses size-down cells); the two B02 first-order leads FAIL exact (FGH_PB02A/B L6M -11.8/-6.7, PRE -20.1/-17.1), so B02 stays live.

First-order screen of the same P7 7/4/4 (sz_core, ROLL-EXCL): cut L6M 29.4 / HOLD 18.5 / PRE 32.1 / X' 27.4, d mean L6M +372 / PRE -446. Exact: L6M 22.5 / HOLD 10.0 / PRE 14.8 / X' 18.8, d mean L6M +489 / PRE -1021. The first-order screen overstates PRE (about +17 points) and X'; L6M agrees within 6.9 points; only exact numbers are verdicts.

Rule 2/2a label of the exact P7 7,4,0,4,0,0: recents L1M/L3M/L6M cut 22.5/22.5/22.5 (d mean L6M +489); PRE cut 14.8% and d mean -1021$/wk; allowed PRE deepening 25% (bi-weekly re-pick WF of the P7-table family with the equal-mean picker beats live in 86% of 74 refit periods, OOS cut 36.1%, d mean -1344$/wk) -> **OK-PRIOR** (old label under the -$1k floor: RECENT-ONLY; new floor = 25% of the live PRE mean = -3490$/wk; the exact PRE d mean is -1021). The lead-reported exact WF for 7/4/4 itself is 73% beat.

### Bi-weekly re-pick walk-forward (PRIMARY OOS test; trailing 26 w -> next 2 w, 7-day purge; first-order daily series, ROLL-EXCL; pick = lowest trailing maxDD else live)
| family | candidates | picker: lowest trailing maxDD: OOS cut % / d mean $/wk / % periods beating live | picker: best EQUAL-MEAN cut: OOS cut % / d mean $/wk / % beating live | switches / periods (eq picker) |
|--|--|--|--|--|
| P7_tables | 125 | 36.1 / -3624 / 91 | 36.1 / -1344 / 86 | 74 / 74 |
| U7_tables | 49 | 12.6 / -1362 / 42 | -5.7 / -1483 / 34 | 72 / 74 |
| B02 | 72 | 25.7 / -4178 / 89 | 11.9 / -264 / 91 | 74 / 74 |
| B02_liveform | 12 | 0.0 / -364 / 61 | 5.1 / -984 / 62 | 74 / 74 |
| H_atr | 26 | 34.6 / -3729 / 74 | 33.1 / -2920 / 70 | 74 / 74 |

### REFIT 2026-11-22 - EXACT series only (ROLLFIX1; Z.refit_pick over the exact daily series of the sets below, trailing 26 weeks to the data end, drawdown first; the live setting is retained unless a cell has a lower trailing maxDD). Exact scores are in /mnt/l2/l2vast/_th_sz/fgh_exact_scores.csv (NOT the shared exact_b/sz_exact.csv, which is overwritten by whoever scores last).
| rank | set | trailing maxDD | trailing worst-20 | trailing mean | prior label |
|--|--|--|--|--|--|
| 1 | FGH_P644 | 52808 | 136103 | +21134 | OK-PRIOR-UNKNOWN-WF |
| 2 | FGH_PBESTH | 59115 | 190027 | +24212 | OK-PRIOR-UNKNOWN-WF |
| 3 | Q_P7_744 | 61893 | 184693 | +25327 | OK-PRIOR-UNKNOWN-WF |
| 4 | FGH_GREEDY | 61963 | 54397 | +16470 | RECENT-ONLY-UNKNOWN-WF |
| 5 | LIVE (live) | 79907 | 130579 | +24124 | PRIOR-UNKNOWN |
| 6 | FGH_PB02B | 85280 | 103231 | +22500 | RECENT-ONLY-UNKNOWN-WF |
| 7 | FGH_PB02A | 89333 | 128398 | +23398 | RECENT-ONLY-UNKNOWN-WF |
| 8 | FGH_P444 | 95230 | 18195 | +13773 | RECENT-ONLY-UNKNOWN-WF |
Pick today: **FGH_P644**. Exact bi-weekly WF per set (live vs set, contiguous complete block): Q_P7_744 73% of 44 periods beat live, OOS cut 14.8%, d mean -1610; FGH_P644 66% of 44 periods beat live, OOS cut 41.8%, d mean -690; FGH_P444 77% of 22 periods beat live, OOS cut 20.0%, d mean -2509; FGH_GREEDY 57% of 44 periods beat live, OOS cut 55.5%, d mean -1050; FGH_PBESTH 36% of 44 periods beat live, OOS cut 31.2%, d mean +647; FGH_PB02A 32% of 22 periods beat live, OOS cut -22.9%, d mean -3627; FGH_PB02B 36% of 22 periods beat live, OOS cut -11.2%, d mean -4915; 
Reading the refit: the drawdown-first pick is the table with the lowest trailing maxDD, but it also gives up trailing mean (FGH_P644); the installed 7,4,0,4,0,0 has trailing maxDD 61893 vs live 79907 at trailing mean +25327 vs live +24124, so the recommendation stays 7,4,0,4,0,0 (installed) and the refit pick above is a re-check item for 2026-11-22, not a change.

### Rule-2 ranking key (recents): mean of equal-mean cut on L6M, L3M, L1M, first-order sz_core rows; labels by rule 2a
| candidate | recents key | cut L1M/L3M/L6M | PRE cut / d mean | prior label (allow %) | bi-weekly WF beat % (equal-mean picker, family) |
|--|--|--|--|--|--|
| ATR>=1.6 x20d median, P7 x0 (exact FGH_PBESTH) | 40.7 | 52.1/21.8/21.8 | 36.0 / -2590 | OK-PRIOR (25%) | 70 |
| P7 7,4,0,4,0,0 | 31.9 | 32.0/31.5/29.4 | 32.1 / -446 | OK-PRIOR (25%) | 86 |
| P7 6,4,0,4,0,0 | 28.5 | 33.4/33.5/33.5 | 32.6 / -1247 | OK-PRIOR (25%) | 86 |
| P7 4,4,0,4,0,0 | 19.0 | 36.7/32.7/32.7 | 30.2 / -1815 | OK-PRIOR (25%) | 86 |
| stack greedy lot table (down; in-sample table, bi-weekly WF not valid) | 40.9 | 56.6/56.6/43.6 | 66.4 / -3815 | RECENT-ONLY-UNKNOWN-WF (15%) | nan |
| stack greedy lot table (UP, labelled) | 42.4 | 42.1/42.1/16.0 | 51.8 / +4102 | OK-PRIOR-UNKNOWN-WF (15%) | nan |
| A06 48-slot greedy (down; in-sample table) | 66.5 | 63.1/63.2/62.3 | 78.6 / -1993 | OK-PRIOR-UNKNOWN-WF (15%) | nan |
| B02 K7P7H7 L20 1.20 allday x0.0 | 68.5 | 73.3/73.3/57.7 | 16.7 / -499 | OK-PRIOR (25%) | 91 |
| B02 K7P7H7 L20 1.00 allday x0.0 | 63.7 | 82.7/78.1/34.7 | 14.6 / +751 | OK-PRIOR (25%) | 91 |
| B02 allbooks L20 1.00 allday x0.0 | 70.2 | 99.7/68.7/33.7 | 23.3 / +332 | OK-PRIOR (25%) | 91 |

Bi-weekly WF is NOT reported for the greedy A06 / lot tables: they are single tables fitted on the whole history, so a bi-weekly re-pick between them and live would leak the future. Their out-of-sample test is the monthly re-fit of the greedy procedure itself (SZ_FGH.md section 1 / R3 page): A06 greedy WF at equal mean -22% (FAILS), stack lot-table greedy down 22% raw/eq with mean -6443$/wk, UP 38% eq / +705$/wk.
<!--/FGHFINAL-->

## A06 - 48 half-hour slots x {0,.5,1}, per book (live slots: see summary)
One slot at a time vs the live multiplier (K7 0330 0400 0430 0500 0530 1430 1900 1930 2030 2100, H7 0400 0530 0830 1030 1230 1300 1400 1830, P7 0330 0500 0830, U7 0200 0830 at x0.5). Rule: the lots chain keeps the live B02; changing a slot replaces its multiplier.

Greedy joint slot set (coordinate descent over 149 book-slot cells, additive in first-order): down-only changes 74, in-sample cut L6M/PRE/X' 62/79/77%, d mean +854; WF raw 26.7% / eq-mean -22.3% / mean -6634$/wk -> overfit; UP-allowed (labelled): WF raw 37.6% / eq -4.6% / -6677$/wk.

Per-book greedy (other books live), down-only:
| book | changes (slot: multiplier) | cut L6M | cut PRE | cut X' | d mean L6M |
|--|--|--|--|--|--|
| K7 | 0100:0.0, 0130:0.0, 0230:0.0, 0300:0.0, 0330:0.0, 0500:0.0, 0530:0.0, 0600:0.5, 0630:0.5, 0700:0.5, 0730:0.0, 0800:0.0, 1300:0.0, 1330:0.5, 1400:0.0, 1800:0.0, 2100:0.0, 2130:0.5, 2200:0.0, 2230:0.0 | 9 | 25 | 18 | -925 |
| P7 | 0130:0.5, 0200:0.0, 0230:0.5, 0300:0.0, 0330:0.0, 0400:0.5, 0500:0.0, 0600:0.0, 0630:0.0, 0700:0.0, 0730:0.0, 1000:0.0, 1030:0.5, 1100:0.0, 1130:0.0, 1930:0.0, 2200:0.0, 2300:0.0 | 37 | 62 | 59 | +1867 |
| M7 | 0200:0.5, 0300:0.5, 0330:0.0, 0400:0.0, 0500:0.0, 0530:0.0, 0630:0.0, 0800:0.5, 1130:0.0 | 4 | 16 | 8 | +372 |
| U7 | 0000:0.0, 0030:0.0, 0200:0.0, 0230:0.0, 0630:0.5, 0730:0.0, 2030:0.0, 2230:0.0, 2300:0.0, 2330:0.5 | -2 | 12 | 4 | -634 |
| A7 | 0000:0.0, 1830:0.0, 1930:0.0, 2030:0.0, 2100:0.0, 2230:0.0 | 1 | 2 | 0 | +849 |
| H7 | 1030:0.0, 1830:0.0, 2130:0.0, 2230:0.0 | -1 | 2 | 5 | -334 |
| O7 | none (live stays) | 0 | 0 | 0 | +0 |

Best single slot changes (down-only), top 12 by SEL (equal-mean cut mean over L6M, PRE, X'):
| book | slot | m (live) | cut L6M/PRE/X' | d mean L6M | eq cut L6M/PRE/X' | trades changed | P&L removed (all history) |
|--|--|--|--|--|--|--|--|
| P7 | 1000 | 0.0 (1.0) | 7/4/29 | +665 | 9/7/31 | 513 | -17552 |
| P7 | 1100 | 0.0 (1.0) | 7/5/11 | +825 | 10/9/14 | 254 | +5098 |
| P7 | 1000 | 0.5 (1.0) | 3/2/13 | +594 | 6/5/15 | 432 | -25081 |
| P7 | 2030 | 0.0 (1.0) | -6/15/0 | +1145 | -1/19/5 | 147 | +48040 |
| P7 | 0400 | 0.0 (1.0) | 5/1/-2 | +1388 | 10/7/3 | 174 | +33466 |
| U7 | 0300 | 0.0 (1.0) | 0/-1/12 | +661 | 3/2/14 | 90 | -18356 |
| P7 | 1130 | 0.0 (1.0) | 4/4/1 | +819 | 7/7/4 | 223 | -12524 |
| P7 | 0630 | 0.0 (1.0) | -3/13/-3 | +791 | 0/16/1 | 114 | +39926 |
| K7 | 0230 | 0.0 (1.0) | 3/3/5 | +524 | 5/5/7 | 109 | -14126 |
| P7 | 1100 | 0.5 (1.0) | 3/2/6 | +515 | 5/4/8 | 208 | -3228 |
| M7 | 0500 | 0.0 (1.0) | 3/5/7 | +116 | 4/5/7 | 162 | -29891 |
| P7 | 0730 | 0.0 (1.0) | 2/4/-2 | +995 | 6/8/2 | 133 | +44788 |

## B02 - overnight range / median of prior L days, threshold, action, window, books (420 cells)
My ratio reproduces the replica gate on 98.6% of trades (L20, .85). Live = K7/P7/H7, window 10:30-18:00, x0.5, L20, .85. Cells with threshold > 1 flag most days (a size-down of most trades, listed but read at equal mean).

| setting | cut L6M/HOLD/PRE/X' % | d mean L6M/PRE $/wk | eq-mean cut L6M/PRE/X' % | w20 vs live | Ulcer vs live | $/wk per $1k | note |
|--|--|--|--|--|--|--|--|
| LIVE (reference) | 0/0/0/0 | +0/+0 | 0/0/0 | 1.00 | 1.00 | n/a | reference row |
| K7P7H7 L20 thr 1.20 allday x0.0 (7888 trades) | 58/31/17/74 | +303/-499 | 58/18/74 | 1.02 | 0.30 | -7 | P&L of the lots removed -258395$ at base lots (negative = losers removed) |
| K7P7H7 L20 thr 1.00 allday x0.0 (5572 trades) | 35/31/15/53 | -1072/+751 | 32/11/51 | 1.47 | 0.40 | +39 | P&L of the lots removed -557265$ at base lots (negative = losers removed) |
| allbooks L20 thr 1.00 allday x0.0 (8772 trades) | 34/47/23/55 | +2099/+332 | 39/30/59 | 1.27 | 0.39 | -78 | P&L of the lots removed -633351$ at base lots (negative = losers removed) |
| allbooks L5 thr 1.50 allday x0.5 (6262 trades) | 51/25/36/45 | -2123/-1342 | 45/30/40 | 1.21 | 0.43 | +52 | P&L of the lots removed +93575$ at base lots (negative = losers removed) |
| K7P7H7 L5 thr 1.50 allday x0.5 (4785 trades) | 45/16/26/41 | -3210/-462 | 38/16/33 | 1.27 | 0.51 | +89 | P&L of the lots removed +31476$ at base lots (negative = losers removed) |
| allbooks L20 thr 1.20 allday x0.5 (4584 trades) | 44/25/21/40 | +470/-51 | 45/23/42 | 1.26 | 0.49 | -13 | P&L of the lots removed -148373$ at base lots (negative = losers removed) |
| K7P7H7 L20 thr 1.20 allday x0.5 (3466 trades) | 40/16/11/41 | +1072/+700 | 43/15/43 | 1.32 | 0.56 | -33 | P&L of the lots removed -158426$ at base lots (negative = losers removed) |
| allbooks L20 thr 1.50 allday x0.5 (5770 trades) | 36/25/21/52 | -2264/-764 | 29/12/47 | 1.14 | 0.48 | +78 | P&L of the lots removed +13937$ at base lots (negative = losers removed) |
| K7P7H7 L20 thr 1.50 allday x0.5 (4389 trades) | 36/16/11/45 | -3369/-619 | 27/-2/38 | 1.23 | 0.54 | +118 | P&L of the lots removed -7743$ at base lots (negative = losers removed) |
| K7P7H7 L10 thr 1.50 allday x0.5 (4518 trades) | 36/16/11/49 | -4193/-1225 | 24/-5/39 | 1.17 | 0.54 | +146 | P&L of the lots removed +39175$ at base lots (negative = losers removed) |

Walk-forward of the B02 picking procedure (26 w train, 7 d embargo, 2024-01..2026-10): all down-only cells raw 23.3% / eq-mean 21.1% / -449$/wk (picks 34/34; most picked {'B02_allbooks_20_1.20_alld_0.0': 11, 'B02_allbooks_20_1.00_alld_0.0': 7, 'B02_allbooks_10_1.50_alld_0.0': 6}); live-form cells only 2.8% / -2.0% / -780$/wk.

Plain sentences: A06 - a greedy 48-slot fit is a textbook overfit (in-sample cut >60%, out-of-sample at equal mean negative); the live eight slots stay. B02 - see the WF line; a threshold/lookback change helps only if the picking procedure holds at equal mean; StackCut and HM5 need the exact engine and are pending.

## Old base vs new (first-order, same grid; OLD-BASE not roll-excluded)
Greedy 48-slot set WF at equal mean: new -22% / old -11%.

| B02 cell | cut L6M/PRE/X' NEW | OLD | delta L6M/PRE | SEL new/old | rank new/old (of 420) | identical to the dollar? |
|--|--|--|--|--|--|--|
| K7P7H7 L20 1.20 allday x0.0 | 58/17/74 | 66/16/43 | -9/+1 | 43.0/34.4 | 13/41 | no |
| K7P7H7 L20 1.00 allday x0.0 | 35/15/53 | 35/20/33 | -0/-5 | 38.9/39.2 | 20/31 | no |
| allbooks L20 1.00 allday x0.0 | 34/23/55 | 39/22/37 | -5/+1 | 37.8/38.5 | 21/34 | no |
| allbooks L5 1.50 allday x0.5 | 51/36/45 | 54/35/31 | -3/+1 | 36.8/33.5 | 25/44 | no |
| K7P7H7 L5 1.50 allday x0.5 | 45/26/41 | 55/30/27 | -10/-4 | 33.1/34.3 | 27/42 | no |
| allbooks L20 1.20 allday x0.5 | 44/21/40 | 54/22/13 | -10/-0 | 32.6/27.5 | 28/68 | no |
| K7P7H7 L20 1.20 allday x0.5 | 40/11/41 | 52/15/12 | -12/-4 | 31.0/26.9 | 31/71 | no |
| allbooks L20 1.50 allday x0.5 | 36/21/52 | 56/22/32 | -20/-0 | 26.0/28.9 | 40/57 | no |
