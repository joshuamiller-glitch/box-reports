> ROLL-EXCL: the 33 base trades alive across a contract roll carry weight 0 in every first-order number below (COMB, NOCUT, UNIF; OLD-BASE comparison rows are not roll-excluded).
> STANDING RULE (user 17:20Z): every D7 layer stays ON; this page recommends SETTINGS only (P7 session lots, slots, gates), never dropping a layer; live setting is always the reference row and stays if nothing beats it OOS.
> VOID: every earlier EXACT table-mode row (sz_exact keyed on arm time, fixed to the signal second) is void and not shown; exact sets are re-queued with the fixed driver. ROLL FIX: NQ roll jumps (12 quarterly, 2 were flagged) are now adjusted in the FGH bars; affected features were gap, on_ratio, TWAP deviation/slope, dip, EMA slope, ATR/ADX on roll nights; zone-line features inherit the raw replica frame and were not re-derived.
> ALL NUMBERS BELOW ARE FIRST-ORDER SCREEN ONLY (pnl per planned lot x lots) unless marked EXACT. User addendum 1: first-order is not a verdict. EXACT runs (SZ-CORE queue, memory-bound): FGH_P744 0 months done; FGH_P644 33 months done; FGH_P444 23 months done; FGH_GREEDY 33 months done; FGH_BESTH 0 months done; FGH_BESTG 0 months done; FGH_DOW2 0 months done; FGH_TREND 0 months done; FGH_L2K2 0 months done.

TESTING-DEFECT CHECK (addendum 1c) across my three live-chain bases (COMB, NOCUT, UNIF): of 6788 common cells, L6M maxDD identical to the dollar: 0; PRE: 0. No defect found among my own scores; the first-order scorer cannot see exit/re-entry/lock changes, so the verdict needs EXACT runs.

# SZ_FGH - families F (time/session), G (signal quality), H (regime) + K slice (P7 lot table), refreshed 2026-11-10 14:31Z

Label: PRE-PROOF, post-hoc, Shadow only, FIRST-ORDER on S1b-COMB (pnl per lot x lots; mean unreliable, drawdown ranking usable), no PASS claims, entry match < .85. Prereg SZ_FGH_PREREG.md (sha in DECISIONS.md). 6786 cells x 3 bases (COMB live, NOCUT, UNIF controls). Ledger /mnt/l2/l2vast/_th_sz/ledger_FGH*.parquet; lots ratios of top cells M_FGH.npz.

Reading: cut = maxDD cut vs Q1-A at equal lots (objective a, + = shallower); eq-mean cut = objective b (every cell scaled by one global factor so L6M mean = Q1-A, size-down-everything cannot win); SEL = mean of eq-mean cut on L6M/PRE/X'; w20/Ulcer = cell/ref on L6M at equal lots (<1 better); $/wk per $1k = L6M mean change per $1k of L6M maxDD removed (+ = the cell also gains mean); p own = lot ratio permuted within book x session (100 draws), "degenerate" = whole book x session group moved, placebo cannot vary; p fam = max-stat over all cells (about 1 for everything with 6786 cells: labelled, not used to kill). All numbers are sz_core.Z.score (SZ-CORE convention: rolling windows as of 2026-11-09, maxDD/worst-20/Ulcer on ALL weeks of the window, carrying week dropped from means only); my own scorer (complete weeks only) agrees on L6M/PRE maxDD cuts exactly and differs in the equal-mean columns (L6M mean window), see section 8. Base data end 2026-10-30. Placebo p own = fgh SEL statistic (permutation within book x session, 100 draws); finalists also get sz_core placebo p (L6M/PRE cut).
Unavailable and proxied: DS7 St1Dist/signal-state arrays are not owned at trade level (proxies: dip size, EMA/TWAP slope, TWAP deviation, zone distances, EX-FEAT entry-second L2 features, 83% matched); L2 confirmation count is a proxy; no volume in nq1m_state (TWAP not VWAP); ES/RTY 1-s data ends 2026-10-16 (later trades neutral).
Calendar: FOMC/CPI/NFP dates entered from public schedules (memory); CHECKED against the owned NQ 1-min bars: median 08:30 ET one-minute range on listed CPI days 12.6x the pre-open norm (norm 2.1x), NFP 9.8x, FOMC 14:00 10.0x; 83% of CPI and 97% of FOMC days sit above the 90th percentile of all days; two NFP entries were wrong (2024-10 should be 10-04; 2025-10 had no release) and were fixed; the 08:30 spikes not on my list are PPI/ECI days (not used). Opex = 3rd Friday, roll_wk = days 7-14 of Mar/Jun/Sep/Dec, half-days = day after Thanksgiving, Dec 24, Jul 3 weekdays. Not checked against an official file.


<!--FGHFINAL-->
## EXACT vs FIRST-ORDER (ROLLFIX1 engine, exact rows read with sz_exact.py score; written 2026-11-10 14:31Z)
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

### Rule 2a labels on the EXACT rows (USER DECISION 13:45Z: PRE mean floor = 25% of the live PRE mean; old fixed -$1k label beside)
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

## 1. Walk-forward of the picking procedure (purged monthly, 26 w train, 7 d embargo, 2024-01..2026-10, picks max equal-mean maxDD cut on the train weeks, 34 months)
| subset | OOS maxDD cut raw % | at equal mean % | d mean $/wk | w20 OOS/ref | picks/months |
|--|--|--|--|--|--|
| COMB F | 5.8 | -13.7 | -2827 | 1.02 | 34/34 |
| COMB G | 34.9 | -58.5 | -9757 | 0.65 | 34/34 |
| COMB H | 20.5 | -56.4 | -8134 | 0.89 | 34/34 |
| COMB K | 38.5 | 35.2 | -840 | 0.78 | 34/34 |
| COMB ALL | 11.0 | -189.0 | -11454 | 0.68 | 34/34 |
| COMB F_slot48 | 4.6 | 1.4 | -542 | 0.97 | 34/34 |
| COMB F_lot_table | 31.1 | 32.6 | +367 | 0.80 | 34/34 |
| COMB G_qgate | 23.1 | -57.7 | -8481 | 0.69 | 34/34 |
| COMB H_regime | 20.5 | -56.4 | -8134 | 0.89 | 34/34 |
| COMB H_atr | -7.8 | -25.4 | -2318 | 0.93 | 34/34 |
| COMB H_atr_P7 | -7.8 | -17.8 | -1399 | 0.90 | 33/34 |
| COMB K_joint | 35.6 | 29.8 | -1368 | 0.79 | 31/34 |
| COMB F_event_dow_edge | 5.8 | -21.2 | -3686 | 1.01 | 34/34 |
| COMB G_zone_l2 | 16.2 | -2.6 | -3031 | 0.82 | 34/34 |
| COMB UP_allowed_lot_table | 1.5 | 6.5 | +894 | 0.94 | 34/34 |
| NOCUT K | 21.3 | 16.1 | -897 | 0.79 | 34/34 |
| NOCUT K_joint | 29.6 | 26.8 | -554 | 0.77 | 33/34 |
| NOCUT F_lot_table | 11.3 | 6.6 | -713 | 0.83 | 34/34 |
| NOCUT H_atr | 3.3 | -34.5 | -4046 | 0.83 | 34/34 |
| NOCUT F | 11.4 | -10.0 | -2800 | 0.90 | 34/34 |
| NOCUT G | 11.8 | -33.9 | -4911 | 0.78 | 34/34 |
| NOCUT H | 41.4 | 15.9 | -4363 | 0.71 | 34/34 |
| UNIF K | 25.9 | 27.0 | +242 | 0.76 | 34/34 |
| UNIF K_joint | 35.7 | 28.0 | -1620 | 0.78 | 34/34 |
| UNIF F_lot_table | 25.9 | 29.1 | +687 | 0.80 | 34/34 |
| UNIF H_atr | 29.5 | 23.8 | -1129 | 0.72 | 34/34 |
| UNIF F | 22.8 | 17.0 | -1051 | 0.87 | 34/34 |
| UNIF G | 8.5 | -60.3 | -6464 | 0.76 | 34/34 |
| UNIF H | 37.6 | 18.9 | -3485 | 0.73 | 34/34 |

### Greedy joint lot table (coordinate descent over the 15 book x session cells, daily P&L additive across disjoint trades; the picking procedure re-run each month on trailing 26 weeks)
| base | variant | WF OOS cut raw % | at equal mean % | d mean $/wk | in-sample table (book|session: lots) | in-sample cut L6M/PRE/X' % |
|--|--|--|--|--|--|--|
| COMB | down-only | 57.0 | 9.7 | -8678 | {"K7|0": 1, "K7|1": 0, "K7|4": 0, "M7|1": 1, "M7|3": 0, "P7|0": 6, "P7|1": 3, "P7|3": 0, "U7|1": 0} | 44/66/65 |
| COMB | up (UP, labelled) | 25.0 | 20.3 | -968 | {"A7|0": 6, "H7|0": 6, "H7|3": 4, "K7|0": 1, "K7|1": 1, "K7|3": 2, "K7|4": 0, "M7|1": 1, "M7|3": 0, "O7|3": 3, "P7|0": 8, "P7|3": 0, "U7|1": 6} | 2/40/36 |
| NOCUT | down-only | 42.7 | -34.2 | -8252 | {"H7|0": 1, "H7|3": 0, "K7|0": 1, "K7|1": 0, "M7|1": 1, "P7|0": 4, "P7|1": 1, "P7|3": 0, "U7|1": 3} | 75/63/68 |
| NOCUT | up (UP, labelled) | 7.7 | 17.7 | +1749 | {"A7|0": 8, "H7|0": 1, "H7|3": 8, "K7|0": 3, "K7|1": 7, "K7|3": 2, "K7|4": 5, "O7|3": 8, "P7|0": 6, "P7|1": 1, "P7|3": 0, "U7|1": 5} | 40/-2/9 |
| UNIF | down-only | 33.8 | -46.7 | -8260 | {"H7|0": 1, "H7|3": 0, "K7|1": 1, "M7|1": 1, "P7|0": 5, "P7|1": 4, "P7|3": 0, "U7|1": 2} | 64/53/54 |
| UNIF | up (UP, labelled) | 9.7 | 19.4 | +1802 | {"A7|0": 8, "H7|0": 1, "H7|3": 2, "K7|0": 5, "K7|1": 1, "K7|4": 8, "M7|1": 1, "M7|3": 4, "O7|3": 5, "P7|0": 6, "P7|1": 5, "P7|3": 0, "U7|1": 1} | 36/24/18 |

## 2. Lead 1 - P7 lot table by session (K slice): joint asia/london/nyam lots 3-7 (live 7/7/7). Top 12 of 20, drawdown-first by SEL
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7_lot_table_joint | {"q_asia": 7, "q_london": 4, "q_nyam": 4} | P7 | 27/21/32/24 | +359/-428 | 28/33/25 | 1.37 | 0.76 | +17 | 0.12 | 0.01 / 1.00 | 30,28 / 29,35 | -3802 | True |
| P7_lot_table_joint | {"q_asia": 7, "q_london": 3, "q_nyam": 4} | P7 | 26/21/36/22 | -330/-765 | 25/35/21 | 1.30 | 0.75 | -16 | 0.12 | 0.07 / 1.00 | 31,32 / 30,39 | -5373 | True |
| P7_lot_table_joint | {"q_asia": 6, "q_london": 4, "q_nyam": 4} | P7 | 29/31/33/34 | -1935/-1229 | 24/27/28 | 1.24 | 0.71 | -83 | 0.22 | 0.01 / 1.00 | 39,32 / 36,32 | -15368 | True |
| P7_lot_table_joint | {"q_asia": 7, "q_london": 4, "q_nyam": 3} | P7 | 28/21/32/23 | -438/-486 | 26/31/22 | 1.34 | 0.75 | -20 | 0.13 | 0.14 / 1.00 | 33,34 / 29,38 | -7404 | True |
| P7_lot_table_joint | {"q_asia": 6, "q_london": 3, "q_nyam": 4} | P7 | 28/29/36/33 | -2567/-1567 | 20/29/26 | 1.16 | 0.71 | -115 | 0.22 | 0.04 / 1.00 | 39,35 / 37,37 | -16939 | True |
| P7_lot_table_joint | {"q_asia": 7, "q_london": 3, "q_nyam": 3} | P7 | 26/21/36/22 | -1128/-742 | 23/33/18 | 1.27 | 0.76 | -54 | 0.13 | 0.40 / 1.00 | 34,36 / 30,42 | -8974 | True |
| P7_lot_table_joint | {"q_asia": 6, "q_london": 4, "q_nyam": 3} | P7 | 30/31/33/33 | -2699/-1221 | 22/25/26 | 1.20 | 0.70 | -114 | 0.22 | 0.03 / 1.00 | 42,35 / 35,35 | -18970 | True |
| P7_lot_table_joint | {"q_asia": 5, "q_london": 3, "q_nyam": 4} | P7 | 28/31/33/32 | -2071/-1560 | 21/26/25 | 1.09 | 0.72 | -91 | 0.22 | 0.10 / 1.00 | 46,32 / 38,31 | -25196 | True |
| P7_lot_table_joint | {"q_asia": 6, "q_london": 3, "q_nyam": 3} | P7 | 28/31/36/32 | -3331/-1477 | 18/27/23 | 1.13 | 0.70 | -147 | 0.22 | 0.15 / 1.00 | 42,38 / 37,40 | -20540 | True |
| P7_lot_table_joint | {"q_asia": 5, "q_london": 3, "q_nyam": 3} | P7 | 29/31/33/32 | -2723/-2224 | 18/23/22 | 1.05 | 0.71 | -119 | 0.23 | 0.33 / 1.00 | 49,33 / 38,34 | -28797 | True |
| P7_lot_table_joint | {"q_asia": 5, "q_london": 4, "q_nyam": 4} | P7 | 30/31/30/32 | -3579/-1289 | 19/19/21 | 1.15 | 0.72 | -151 | 0.22 | 0.02 / 1.00 | 46,29 / 36,26 | -23625 | True |
| P7_lot_table_joint | {"q_asia": 4, "q_london": 4, "q_nyam": 4} | P7 | 28/41/30/38 | -3956/-1797 | 12/14/24 | 0.94 | 0.70 | -174 | 0.23 | 0.02 / 1.00 | 51,28 / 36,23 | -34489 | True |

### Session lot-table cells (one book x session at a time, down-only), top 12 of 41
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 1, "sess": 1} | P7 | 28/-5/44/8 | +243/-165 | 29/45/9 | 1.12 | 0.78 | +11 | 0.08 | 0.03 / 1.00 | 25,31 / 29,42 | +654 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 0, "sess": 1} | P7 | 28/-20/51/5 | -639/-104 | 25/49/3 | 1.03 | 0.73 | -29 | 0.08 | 1.00(degenerate) / 1.00 | 29,36 / 31,49 | -385 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 0, "sess": 3} | P7 | 15/22/16/32 | +711/-1990 | 18/18/34 | 1.57 | 0.84 | +57 | 0.06 | 1.00(degenerate) / 1.00 | 35,28 / 26,29 | -15995 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 1, "sess": 3} | P7 | 15/18/12/31 | +1298/-1513 | 19/16/34 | 1.49 | 0.84 | +110 | 0.05 | 0.01 / 1.00 | 30,24 / 21,23 | -11696 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 2, "sess": 3} | P7 | 11/18/11/23 | +1110/-1492 | 15/15/26 | 1.43 | 0.87 | +121 | 0.05 | 0.07 / 1.00 | 26,21 / 17,21 | -11696 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 2, "sess": 1} | P7 | 23/-6/40/6 | -1824/-212 | 18/36/-1 | 1.07 | 0.81 | -99 | 0.08 | 0.25 / 1.00 | 20,30 / 25,37 | +2242 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 3, "sess": 1} | P7 | 19/5/28/7 | -305/-310 | 17/27/5 | 1.01 | 0.88 | -20 | 0.08 | 0.33 / 1.00 | 14,25 / 19,27 | +824 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 4, "sess": 1} | P7 | 17/8/25/9 | -906/+28 | 14/22/6 | 1.08 | 0.88 | -69 | 0.08 | 0.07 / 1.00 | 14,22 / 17,23 | +2394 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 4, "sess": 3} | P7 | 5/13/8/16 | +1088/-662 | 9/11/19 | 1.31 | 0.94 | +263 | 0.05 | 0.03 / 1.00 | 16,14 / 12,12 | -6197 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 3, "sess": 3} | P7 | 5/13/7/13 | +290/-1466 | 6/9/14 | 1.28 | 0.93 | +67 | 0.05 | 0.54 / 1.00 | 19,14 / 11,15 | -9798 | True |
| lot_table_cell | {"book": "U7", "live_q": 4, "q": 0, "sess": 1} | U7 | 14/0/13/-1 | +15/-232 | 14/13/-1 | 0.98 | 0.95 | +1 | 0.03 | 1.00(degenerate) / 1.00 | 3,17 / -1,14 | +4160 | True |
| lot_table_cell | {"book": "U7", "live_q": 4, "q": 1, "sess": 1} | U7 | 8/-1/9/5 | -159/-138 | 8/9/5 | 0.94 | 0.99 | -24 | 0.03 | 0.19 / 1.00 | 2,12 / -1,10 | +3966 | True |

### UP-allowed lot-table cells (labelled UP, never promoted), top 6
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| lot_table_cell | {"book": "A7", "live_q": 1, "q": 8, "sess": 0} | A7 | -15/-11/18/11 | +3083/+4392 | -2/27/21 | 1.00 | 1.18 | -250 | 0.05 | 0.39 / 1.00 | -4,3 / -3,5 | -7025 | True |
| lot_table_cell | {"book": "A7", "live_q": 1, "q": 7, "sess": 0} | A7 | -11/-9/15/11 | +2743/+3903 | 0/24/20 | 1.05 | 1.16 | -299 | 0.05 | 0.31 / 1.00 | -4,3 / -4,4 | -6330 | True |
| lot_table_cell | {"book": "A7", "live_q": 1, "q": 6, "sess": 0} | A7 | -10/-6/12/11 | +2169/+3090 | -1/20/18 | 1.08 | 1.13 | -264 | 0.05 | 0.34 / 1.00 | -2,2 / -2,4 | -4915 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 5, "sess": 1} | P7 | 8/3/17/9 | +50/+98 | 8/17/9 | 1.01 | 0.98 | +8 | 0.07 | 0.09 / 1.00 | 7,15 / 8,16 | +2233 | True |
| lot_table_cell | {"book": "A7", "live_q": 1, "q": 5, "sess": 0} | A7 | -8/-6/10/9 | +1829/+2602 | 0/17/15 | 1.12 | 1.12 | -300 | 0.05 | 0.46 / 1.00 | -3,2 / -3,3 | -4220 | True |
| lot_table_cell | {"book": "U7", "live_q": 4, "q": 8, "sess": 0} | U7 | 3/-10/-7/1 | +2530/+1312 | 13/4/11 | 1.37 | 0.99 | +937 | 0.03 | 1.00(degenerate) / 1.00 | 17,-8 / 14,-10 | +2405 | True |

## 3. Lead 2 - ATR regime (>= 1.3-1.6x the prior-20-day median of the daily median 5-min ATR): skip or halve. Picking-procedure WF FAILS (-7.8% raw, -25.4% equal mean)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | P7 | 22/37/36/54 | +3463/-2590 | 32/44/60 | 1.39 | 0.75 | +199 | 0.09 | 0.02 / 1.00 | 26,38 / 12,49 | -39590 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | ALL | -2/18/53/58 | +2990/-6889 | 10/58/63 | 1.31 | 0.67 | -1902 | 0.51 | 0.05 / 1.00 | 37,-3 / 30,29 | -81695 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | P7 | -1/19/43/64 | +2572/-2874 | 9/48/67 | 1.36 | 0.74 | -3183 | 0.12 | 0.08 / 1.00 | 37,5 / 32,37 | -51095 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | ALL | 6/24/22/57 | +2021/-1428 | 13/28/61 | 1.28 | 0.78 | +446 | 0.16 | 0.01 / 1.00 | 19,16 / 23,22 | -27584 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | ALL | 6/25/41/62 | -2187/-5352 | -2/36/58 | 1.08 | 0.91 | -451 | 0.40 | 0.03 / 1.00 | 17,47 / 9,55 | -61700 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0.5} | ALL | 12/19/25/46 | -46/-1140 | 12/24/46 | 1.27 | 0.85 | -5 | 0.11 | 0.01 / 1.00 | 10,26 / 6,32 | -22102 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | P7 | 2/21/18/42 | +2018/-963 | 10/25/47 | 1.30 | 0.87 | +1298 | 0.11 | 0.01 / 1.00 | 20,10 / 22,16 | -22162 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0.5} | P7 | 12/26/19/36 | +980/-823 | 15/22/38 | 1.36 | 0.86 | +104 | 0.08 | 0.01 / 1.00 | 13,26 / 8,23 | -17009 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | M7 | -1/13/8/12 | +1090/+32 | 4/13/16 | 1.22 | 1.01 | -1770 | 0.12 | 0.04 / 1.00 | -4,18 / 5,18 | -8350 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | K7 | 3/-9/4/7 | +75/-1671 | 3/5/7 | 1.07 | 0.94 | +35 | 0.20 | 0.11 / 1.00 | 5,-3 / 13,4 | -16475 | True |

## 4F. F Time / session excluding lot tables (584 down-only cells, 198 gate, 56 gate + control-bases ok)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| dow | {"dow": 2, "m": 0} | ALL | 51/27/0/41 | +1120/-2427 | 54/5/44 | 0.88 | 0.56 | +27 | 0.20 | 0.01 / 1.00 | 55,31 / 39,24 | -28160 | True |
| dow | {"dow": 2, "m": 0} | P7 | 32/12/8/36 | +715/-1215 | 34/11/38 | 0.99 | 0.69 | +28 | 0.05 | 0.02 / 1.00 | 41,26 / 26,16 | -9060 | True |
| dow | {"dow": 0, "m": 0} | ALL | 24/-98/22/47 | -1865/-2093 | 18/15/43 | 0.58 | 0.73 | -96 | 0.19 | 0.09 / 1.00 | 1,23 / 16,16 | -28440 | True |
| dow | {"dow": 0, "m": 0} | P7 | 1/-22/13/47 | -798/-562 | -2/10/45 | 0.93 | 0.93 | -733 | 0.05 | 0.11 / 1.00 | 9,11 / 25,6 | -24760 | True |
| dow | {"dow": 2, "m": 0.5} | P7 | 14/6/6/20 | +674/-453 | 17/9/22 | 1.07 | 0.89 | +59 | 0.04 | 0.02 / 1.00 | 17,12 / 14,7 | -3410 | True |
| slot48 | {"m": 0, "slot": 20} | ALL | 4/11/3/35 | +503/-800 | 6/5/37 | 1.26 | 0.96 | +158 | 0.09 | 0.19 / 1.00 | 18,2 / 16,16 | +5745 | True |
| dow | {"dow": 2, "m": 0.5} | ALL | 15/11/6/25 | +46/-873 | 15/6/25 | 0.99 | 0.88 | +4 | 0.07 | 0.03 / 1.00 | 21,10 / 15,5 | -6193 | True |
| slot48 | {"m": 0, "slot": 20} | P7 | 7/13/4/29 | +298/-96 | 8/5/30 | 1.20 | 0.96 | +55 | 0.02 | 0.19 / 1.00 | 20,9 / 17,15 | +5610 | True |
| slot48 | {"m": 0, "slot": 22} | P7 | 7/7/5/11 | +1559/-838 | 12/11/17 | 1.21 | 0.96 | +281 | 0.01 | 0.10 / 1.00 | 11,7 / 7,3 | -6000 | True |
| slot48 | {"m": 0, "slot": 15} | ALL | 2/-2/9/2 | +2463/+189 | 11/17/11 | 1.11 | 1.09 | +1483 | 0.02 | 0.07 / 1.00 | -15,12 / -0,12 | +5425 | True |

## 4G. G Signal quality excluding lot tables (3542 down-only cells, 973 gate, 411 gate + control-bases ok)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "dB", "m": 0, "q": 0.2, "tail": "high"} | P7 | 28/39/33/0 | +3484/-4160 | 37/42/13 | 1.17 | 0.61 | +158 | 0.06 | 0.08 / 1.00 | 48,8 / 37,31 | -55565 | True |
| qgate_x_er | {"er": "erhigh", "feat": "f_sweep2_w30", "m": 0, "q": 0.2, "tail": "high"} | ALL | 18/8/27/0 | +3486/-2334 | 29/37/13 | 1.47 | 0.62 | +242 | 0.09 | 0.04 / 1.00 | 52,24 / 44,35 | +0 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.3, "tail": "high"} | ALL | 15/1/23/0 | +3995/-2240 | 28/35/15 | 1.25 | 0.67 | +327 | 0.24 | 0.06 / 1.00 | 26,22 / 20,42 | -28410 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.1, "tail": "high"} | ALL | 10/21/33/0 | +3427/-1359 | 22/42/13 | 1.24 | 0.89 | +417 | 0.09 | 0.03 / 1.00 | 19,17 / 12,23 | +710 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.3, "tail": "high"} | P7 | -2/18/32/0 | +3723/-1120 | 13/42/14 | 1.36 | 0.91 | -2690 | 0.06 | 0.09 / 1.00 | 36,17 / 22,35 | -12670 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.5, "tail": "high"} | P7 | 14/12/17/0 | +3416/-238 | 26/28/14 | 1.26 | 0.84 | +306 | 0.09 | 0.11 / 1.00 | 45,16 / 28,35 | -12950 | True |
| qgate_x_er | {"er": "erhigh", "feat": "dA", "m": 0, "q": 0.2, "tail": "high"} | ALL | 2/14/35/0 | +3303/-1854 | 13/42/12 | 1.08 | 0.98 | +2135 | 0.06 | 0.04 / 1.00 | -14,20 / -2,35 | +10570 | True |
| qgate | {"feat": "dB", "m": 0.5, "q": 0.2, "tail": "high"} | P7 | 14/21/32/0 | +2027/-1685 | 21/38/8 | 1.18 | 0.81 | +178 | 0.06 | 0.01 / 1.00 | 25,10 / 27,32 | -24625 | True |
| qgate | {"feat": "dB", "m": 0, "q": 0.1, "tail": "high"} | P7 | -6/15/35/0 | +3318/-2601 | 7/43/12 | 1.14 | 0.93 | -691 | 0.03 | 0.15 / 1.00 | 1,9 / -9,28 | -37575 | True |
| qgate_x_er | {"er": "erhigh", "feat": "dip30", "m": 0, "q": 0.5, "tail": "high"} | ALL | 23/22/55/0 | -1993/-3656 | 16/51/-8 | 1.38 | 0.52 | -110 | 0.20 | 0.01 / 1.00 | 54,49 / 47,57 | -47815 | False |

## 4H. H Regime excluding lot tables (854 down-only cells, 290 gate, 124 gate + control-bases ok)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | P7 | 22/37/36/54 | +3463/-2590 | 32/44/60 | 1.39 | 0.75 | +199 | 0.09 | 0.02 / 1.00 | 26,38 / 12,49 | -39590 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | ALL | -2/18/53/58 | +2990/-6889 | 10/58/63 | 1.31 | 0.67 | -1902 | 0.51 | 0.05 / 1.00 | 37,-3 / 30,29 | -81695 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | P7 | -1/19/43/64 | +2572/-2874 | 9/48/67 | 1.36 | 0.74 | -3183 | 0.12 | 0.08 / 1.00 | 37,5 / 32,37 | -51095 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | ALL | 6/24/22/57 | +2021/-1428 | 13/28/61 | 1.28 | 0.78 | +446 | 0.16 | 0.01 / 1.00 | 19,16 / 23,22 | -27584 | True |
| regime | {"cond": "adx5_ge20", "m": 0} | P7 | 36/28/57/42 | -3511/-5949 | 23/48/30 | 1.22 | 0.42 | -122 | 0.19 | 0.12 / 1.00 | 79,40 / 67,59 | -68150 | True |
| regime | {"cond": "on_ratio_ge0.6", "m": 0} | P7 | 32/40/48/34 | -1308/-778 | 28/45/29 | 0.96 | 0.63 | -51 | 0.11 | 0.29 / 1.00 | 69,56 / 41,46 | -41335 | True |
| regime | {"cond": "adx5_ge20", "m": 0.5} | P7 | 40/21/26/37 | -522/-2163 | 38/24/36 | 1.30 | 0.65 | -17 | 0.18 | 0.01 / 1.00 | 56,26 / 48,27 | -29763 | True |
| regime | {"cond": "adx5_ge20", "m": 0.5} | ALL | 41/20/38/42 | -2574/-3578 | 33/29/34 | 1.09 | 0.57 | -78 | 0.30 | 0.01 / 1.00 | 59,26 / 61,39 | -33303 | True |
| regime | {"cond": "prior_trend_day", "m": 0} | ALL | 6/-17/41/62 | -1433/-90 | -1/36/59 | 0.80 | 0.90 | -307 | 0.33 | 0.02 / 1.00 | 30,42 / 52,48 | -16660 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | ALL | 6/25/41/62 | -2187/-5352 | -2/36/58 | 1.08 | 0.91 | -451 | 0.40 | 0.03 / 1.00 | 17,47 / 9,55 | -61700 | True |

## 4K. K P7 excluding lot tables (0 down-only cells, 0 gate, 0 gate + control-bases ok)
none

## 4U. UP-allowed G/H variants (x1.5 on the flagged trades; labelled UP, never promoted; first-order overstates up-size mean by 10-18k/wk), top 8 of 1346
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate_UP | {"feat": "f_ice_ag_w30", "m": 1.5, "q": 0.5, "tail": "low"} | ALL | -18/-52/-3/0 | +11156/+4552 | 22/32/34 | 1.84 | 1.14 | -758 | 0.41 | 0.02 / 1.00 | -9,-25 / -1,-9 | +0 | True |
| qgate_UP | {"feat": "f_dlt_w30", "m": 1.5, "q": 0.5, "tail": "low"} | ALL | -13/-36/-8/0 | +10475/+5245 | 22/25/31 | 1.63 | 1.21 | -997 | 0.39 | 0.01 / 1.00 | -4,-27 / 0,-18 | +0 | True |
| qgate_UP | {"feat": "f_spread_t", "m": 1.5, "q": 0.5, "tail": "high"} | ALL | -46/-55/-26/0 | +13884/+8359 | 11/24/40 | 1.76 | 1.52 | -374 | 0.67 | 0.02 / 1.00 | -38,-60 / -24,-51 | +0 | True |
| regime_UP | {"cond": "twap_slope_with_ge0.10", "m": 1.5} | ALL | -22/-38/-19/-7 | +12158/+6771 | 20/22/30 | 1.93 | 1.25 | -700 | 0.47 | 0.02 / 1.00 | -38,-18 / -41,-23 | +46453 | True |
| regime_UP | {"cond": "both_agree_60", "m": 1.5} | ALL | -25/-39/-39/-7 | +13360/+7576 | 24/14/34 | 2.07 | 1.26 | -682 | 0.76 | 0.01 / 1.00 | -39,-50 / -35,-55 | +0 | True |
| qgate_UP | {"feat": "f_mom60", "m": 1.5, "q": 0.5, "tail": "low"} | ALL | -16/-24/7/0 | +8278/+3205 | 14/32/26 | 1.69 | 1.13 | -637 | 0.32 | 0.05 / 1.00 | -14,3 / -7,12 | +0 | True |
| qgate_UP | {"feat": "f_ema20_rel", "m": 1.5, "q": 0.5, "tail": "low"} | ALL | -23/-35/-4/0 | +8900/+3101 | 13/27/30 | 1.48 | 1.24 | -488 | 0.28 | 0.01 / 1.00 | -9,-13 / -23,3 | +0 | True |
| qgate_UP | {"feat": "f_tot_rel_base", "m": 1.5, "q": 0.5, "tail": "high"} | ALL | -15/-8/-3/0 | +8812/+4141 | 16/25/27 | 1.81 | 1.08 | -722 | 0.36 | 0.02 / 1.00 | 5,-6 / -8,-0 | +0 | True |

## 5. Calmar frontier vs Q1-A (down-only, first-order; mean is the weak side)
Cells that dominate Q1-A on BOTH L6M mean and maxDD (d mean L6M > 0, cut L6M > 0, cut PRE > 0, cut X' > -3): 456 (of 5041 down-only). Top 10 by SEL:
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | P7 | 22/37/36/54 | +3463/-2590 | 32/44/60 | 1.39 | 0.75 | +199 | 0.09 | 0.02 / 1.00 | 26,38 / 12,49 | -39590 | True |
| dow | {"dow": 2, "m": 0} | ALL | 51/27/0/41 | +1120/-2427 | 54/5/44 | 0.88 | 0.56 | +27 | 0.20 | 0.01 / 1.00 | 55,31 / 39,24 | -28160 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | ALL | 6/24/22/57 | +2021/-1428 | 13/28/61 | 1.28 | 0.78 | +446 | 0.16 | 0.01 / 1.00 | 19,16 / 23,22 | -27584 | True |
| qgate | {"feat": "dB", "m": 0, "q": 0.2, "tail": "high"} | P7 | 28/39/33/0 | +3484/-4160 | 37/42/13 | 1.17 | 0.61 | +158 | 0.06 | 0.08 / 1.00 | 48,8 / 37,31 | -55565 | True |
| P7_lot_table_joint | {"q_asia": 7, "q_london": 4, "q_nyam": 4} | P7 | 27/21/32/24 | +359/-428 | 28/33/25 | 1.37 | 0.76 | +17 | 0.12 | 0.01 / 1.00 | 30,28 / 29,35 | -3802 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 1, "sess": 1} | P7 | 28/-5/44/8 | +243/-165 | 29/45/9 | 1.12 | 0.78 | +11 | 0.08 | 0.03 / 1.00 | 25,31 / 29,42 | +654 | True |
| dow | {"dow": 2, "m": 0} | P7 | 32/12/8/36 | +715/-1215 | 34/11/38 | 0.99 | 0.69 | +28 | 0.05 | 0.02 / 1.00 | 41,26 / 26,16 | -9060 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | P7 | 2/21/18/42 | +2018/-963 | 10/25/47 | 1.30 | 0.87 | +1298 | 0.11 | 0.01 / 1.00 | 20,10 / 22,16 | -22162 | True |
| qgate_x_er | {"er": "erhigh", "feat": "f_sweep2_w30", "m": 0, "q": 0.2, "tail": "high"} | ALL | 18/8/27/0 | +3486/-2334 | 29/37/13 | 1.47 | 0.62 | +242 | 0.09 | 0.04 / 1.00 | 52,24 / 44,35 | +0 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.3, "tail": "high"} | ALL | 15/1/23/0 | +3995/-2240 | 28/35/15 | 1.25 | 0.67 | +327 | 0.24 | 0.06 / 1.00 | 26,22 / 20,42 | -28410 | True |

Cells that cut drawdown by giving up mean (gate on, d mean <= 0): 328; cheapest rate ($ weekly mean per $1k L6M maxDD removed), top 8:
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "RTY_disagree_60", "m": 0} | P7 | 0/20/19/39 | -971/-666 | -5/15/36 | 1.04 | 1.05 | -11180 | 0.05 | 0.17 / 1.00 | 9,13 / 17,13 | +0 | True |
| regime | {"cond": "RTY_leads_against_15", "m": 0.5} | P7 | 0/12/11/12 | -960/-935 | -4/8/8 | 1.03 | 0.93 | -11062 | 0.09 | 0.56 / 1.00 | 29,14 / 30,8 | +0 | True |
| regime | {"cond": "RTY_lags_60", "m": 0} | M7 | 0/4/3/3 | -638/-421 | -2/0/1 | 1.04 | 1.05 | -10209 | 0.06 | 0.54 / 1.00 | 4,12 / 3,8 | +0 | True |
| regime | {"cond": "RTY_lags_15", "m": 0.5} | ALL | 0/10/25/10 | -695/-1215 | -3/23/8 | 1.21 | 1.01 | -8005 | 0.09 | 0.08 / 1.00 | 30,25 / 28,31 | +0 | True |
| regime | {"cond": "RTY_lags_15", "m": 0} | M7 | 0/-1/11/7 | -597/+73 | -2/9/5 | 1.06 | 1.02 | -6881 | 0.06 | 0.14 / 1.00 | 1,16 / 3,16 | +0 | True |
| regime | {"cond": "RTY_leads_against_60", "m": 0.5} | K7 | 0/-3/2/12 | -421/-300 | -2/1/10 | 0.97 | 1.04 | -4847 | 0.03 | 0.05 / 1.00 | 6,-1 / 5,-0 | +0 | True |
| slot48 | {"m": 0.5, "slot": 6} | P7 | 0/2/3/6 | -417/+21 | -2/1/4 | 1.00 | 1.06 | -3694 | 0.01 | 0.49 / 1.00 | -4,4 / -1,4 | +1025 | True |
| regime | {"cond": "RTY_disagree_60", "m": 0.5} | P7 | 0/14/10/14 | -236/-360 | -1/9/14 | 1.09 | 1.05 | -2720 | 0.04 | 0.18 / 1.00 | 5,7 / 8,7 | +0 | True |

## 6. Per-book breakdown: best gated down-only cell acting on one book only (scope = book; stack effect), by SEL

**K7** (214 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "prior_trend_day", "m": 0} | K7 | 5/14/7/19 | -29/-963 | 5/7/19 | 1.06 | 1.04 | -7 | 0.11 | 0.12 / 1.00 | 0,3 / 4,2 | +5090 | True |
| regime | {"cond": "prior_close_high", "m": 0} | K7 | 7/0/2/15 | -54/-1203 | 7/2/15 | 0.95 | 1.03 | -10 | 0.09 | 0.09 / 1.00 | 5,-4 / 3,-4 | +0 | True |
| dow | {"dow": 2, "m": 0} | K7 | 3/5/4/7 | +699/-297 | 6/7/10 | 1.10 | 1.00 | +296 | 0.07 | 0.08 / 1.00 | 7,2 / 8,2 | -7620 | True |

**P7** (228 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | P7 | 22/37/36/54 | +3463/-2590 | 32/44/60 | 1.39 | 0.75 | +199 | 0.09 | 0.02 / 1.00 | 26,38 / 12,49 | -39590 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | P7 | -1/19/43/64 | +2572/-2874 | 9/48/67 | 1.36 | 0.74 | -3183 | 0.12 | 0.08 / 1.00 | 37,5 / 32,37 | -51095 | True |
| regime | {"cond": "adx5_ge20", "m": 0} | P7 | 36/28/57/42 | -3511/-5949 | 23/48/30 | 1.22 | 0.42 | -122 | 0.19 | 0.12 / 1.00 | 79,40 / 67,59 | -68150 | True |

**M7** (398 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "dip15", "m": 0, "q": 0.5, "tail": "high"} | M7 | 17/10/16/0 | +1759/-203 | 22/21/6 | 1.31 | 0.87 | +129 | 0.09 | 0.01 / 1.00 | 4,10 / 13,12 | +390 | True |
| l2_confirm_count_PROXY | {"k": 2, "m": 0} | M7 | 15/5/20/-3 | +842/-382 | 18/22/0 | 1.30 | 0.91 | +70 | 0.09 | 0.01 / 1.00 | 11,23 / 14,20 | +0 | True |
| qgate | {"feat": "f_ahead_rel_base", "m": 0, "q": 0.3, "tail": "low"} | M7 | 6/6/17/0 | +774/-308 | 9/20/3 | 1.20 | 0.99 | +155 | 0.05 | 0.03 / 1.00 | 13,14 / 15,20 | +0 | True |

**U7** (169 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "f_er20_5m", "m": 0, "q": 0.5, "tail": "low"} | U7 | 17/-5/3/0 | +924/-171 | 20/7/4 | 1.21 | 0.90 | +70 | 0.03 | 0.02 / 1.00 | 16,5 / 10,3 | +0 | True |
| regime | {"cond": "adx5_le20", "m": 0} | U7 | 11/11/10/3 | +307/+297 | 12/11/4 | 1.02 | 0.97 | +36 | 0.02 | 0.07 / 1.00 | 0,2 / -1,10 | +3890 | True |
| lot_table_cell | {"book": "U7", "live_q": 4, "q": 0, "sess": 1} | U7 | 14/0/13/-1 | +15/-232 | 14/13/-1 | 0.98 | 0.95 | +1 | 0.03 | 1.00(degenerate) / 1.00 | 3,17 / -1,14 | +4160 | True |

**A7** (59 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "prior_dir_with", "m": 0} | A7 | 5/0/1/1 | +559/-246 | 7/3/3 | 1.02 | 1.02 | +139 | 0.03 | 0.01 / 1.00 | 4,2 / 3,3 | +2425 | True |
| dow | {"dow": 2, "m": 0} | A7 | 2/1/1/-1 | +570/-58 | 5/3/2 | 1.06 | 1.04 | +339 | 0.01 | 0.03 / 1.00 | 2,3 / 3,3 | +1360 | True |
| qgate | {"feat": "twap_slope_sg", "m": 0, "q": 0.1, "tail": "low"} | A7 | 2/0/0/0 | +506/-111 | 4/2/2 | 1.06 | 1.05 | +285 | 0.00 | 0.04 / 1.00 | 1,0 / -0,0 | +670 | True |

**H7** (121 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "prior_close_low", "m": 0} | H7 | 3/0/-1/12 | -130/-317 | 2/-1/11 | 0.95 | 1.05 | -56 | 0.01 | 0.02 / 1.00 | -1,-1 / -1,-1 | +0 | True |
| regime | {"cond": "adx5_ge40", "m": 0} | H7 | 0/1/-1/8 | +102/-180 | 0/-0/8 | 0.96 | 1.07 | n/a | 0.00 | 0.06 / 1.00 | -1,-1 / 2,-1 | +0 | True |
| regime | {"cond": "RTY_disagree_60", "m": 0} | H7 | 0/2/1/0 | +493/-496 | 2/3/2 | 1.07 | 1.05 | +5678 | 0.01 | 0.04 / 1.00 | 3,1 / 3,1 | +0 | True |

**O7** (88 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "RTY_disagree_60", "m": 0} | O7 | 0/-2/1/6 | +278/-364 | 1/2/7 | 1.03 | 1.07 | n/a | 0.01 | 0.01 / 1.00 | 0,1 / 1,1 | +0 | True |
| regime | {"cond": "adx5_ge35", "m": 0} | O7 | 0/0/1/2 | +161/-218 | 1/2/3 | 1.00 | 1.07 | n/a | 0.01 | 0.06 / 1.00 | -0,2 / 0,2 | +695 | True |
| qgate | {"feat": "twap_slope_sg", "m": 0, "q": 0.3, "tail": "low"} | O7 | 0/-1/1/0 | +337/-6 | 1/2/1 | 1.01 | 1.08 | n/a | 0.00 | 0.06 / 1.00 | 1,1 / 2,1 | +0 | True |

## 7. Finalists (<= 12): down-only, tolerant gate, w20 not worse, p own <= .10; one per technique x scope; controls-ok cells first (NOCUT and UNIF cut > 0 on L6M and PRE), then the rest by SEL with the failing ones labelled in the last list below. NONE has p fam <= .10; none is a CANDIDATE; EXACT engine re-run pending (needs the lots-override hook).
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| dow | {"dow": 2, "m": 0} | ALL | 51/27/0/41 | +1120/-2427 | 54/5/44 | 0.88 | 0.56 | +27 | 0.20 | 0.01 / 1.00 | 55,31 / 39,24 | -28160 | True |
| regime | {"cond": "prior_trend_day", "m": 0} | ALL | 6/-17/41/62 | -1433/-90 | -1/36/59 | 0.80 | 0.90 | -307 | 0.33 | 0.02 / 1.00 | 30,42 / 52,48 | -16660 | True |
| dow | {"dow": 2, "m": 0} | P7 | 32/12/8/36 | +715/-1215 | 34/11/38 | 0.99 | 0.69 | +28 | 0.05 | 0.02 / 1.00 | 41,26 / 26,16 | -9060 | True |
| qgate | {"feat": "dB", "m": 0.5, "q": 0.3, "tail": "high"} | ALL | 18/23/38/0 | -214/-2021 | 17/37/-1 | 1.00 | 0.81 | -15 | 0.11 | 0.07 / 1.00 | 28,13 / 27,36 | -30428 | True |
| P7_lot_table_joint | {"q_asia": 4, "q_london": 4, "q_nyam": 4} | P7 | 28/41/30/38 | -3956/-1797 | 12/14/24 | 0.94 | 0.70 | -174 | 0.23 | 0.02 / 1.00 | 51,28 / 36,23 | -34489 | True |
| l2_confirm_count_PROXY | {"k": 2, "m": 0.5} | ALL | 28/40/19/31 | -3168/-2337 | 16/6/19 | 0.87 | 0.75 | -143 | 0.19 | 0.06 / 1.00 | 25,31 / 6,34 | +0 | True |
| zone_near_behind | {"dist": 30, "m": 0.5} | P7 | 1/2/0/17 | +52/-790 | 1/0/17 | 0.96 | 1.07 | +68 | 0.03 | 0.06 / 1.00 | 6,1 / 0,1 | +0 | True |
| qgate | {"feat": "twap_dev_sg", "m": 0, "q": 0.2, "tail": "low"} | O7 | 0/-1/1/0 | +199/+0 | 1/1/1 | 1.00 | 1.08 | n/a | 0.00 | 0.09 / 1.00 | 1,1 / 2,1 | +0 | True |
| l2_confirm_count_PROXY | {"k": 2, "m": 0} | U7 | 5/13/14/9 | -344/-1453 | 4/13/8 | 0.97 | 1.01 | -85 | 0.04 | 0.03 / 1.00 | 2,19 / -6,19 | +0 | True |
| regime | {"cond": "prior_close_high", "m": 0} | K7 | 7/0/2/15 | -54/-1203 | 7/2/15 | 0.95 | 1.03 | -10 | 0.09 | 0.09 / 1.00 | 5,-4 / 3,-4 | +0 | True |
| qgate | {"feat": "f_r_ab8", "m": 0, "q": 0.3, "tail": "high"} | U7 | 4/-0/13/0 | +393/-545 | 6/14/2 | 0.93 | 1.01 | +111 | 0.02 | 0.09 / 1.00 | 2,14 / -6,18 | +0 | True |
| regime | {"cond": "prior_close_low", "m": 0} | H7 | 3/0/-1/12 | -130/-317 | 2/-1/11 | 0.95 | 1.05 | -56 | 0.01 | 0.02 / 1.00 | -1,-1 / -1,-1 | +0 | True |

Control-base requirement: dow {"dow": 2, "m": 0} ALL = controls ok; regime {"cond": "prior_trend_day", "m": 0} ALL = controls ok; dow {"dow": 2, "m": 0} P7 = controls ok; qgate {"feat": "dB", "m": 0.5, "q": 0.3, "tail": "high"} ALL = controls ok; P7_lot_table_joint {"q_asia": 4, "q_london": 4, "q_nyam": 4} P7 = controls ok; l2_confirm_count_PROXY {"k": 2, "m": 0.5} ALL = controls ok; zone_near_behind {"dist": 30, "m": 0.5} P7 = controls ok; qgate {"feat": "twap_dev_sg", "m": 0, "q": 0.2, "tail": "low"} O7 = controls ok; l2_confirm_count_PROXY {"k": 2, "m": 0} U7 = FAILS control-base requirement (display only); regime {"cond": "prior_close_high", "m": 0} K7 = FAILS control-base requirement (display only); qgate {"feat": "f_r_ab8", "m": 0, "q": 0.3, "tail": "high"} U7 = FAILS control-base requirement (display only); regime {"cond": "prior_close_low", "m": 0} H7 = FAILS control-base requirement (display only)

ZONE-RAW flag: finalists using zone-line features (dA, dB, nA, nB) inherit the raw replica 1-min frame, which has contract-roll jumps (about 1% of days affected, not re-derived): qgate {"feat": "dB", "m": 0.5, "q": 0.3, "tail": "high"} ALL

Finalist live definitions (all multiplicative on live lots, round, min 1): see params; P7 table cells = SessionLots P7 asia,london,nyam; regime/slot/gate cells = multiplier x0 / x0.5 on the stated trades.

sz_core placebo (same lot-change values on random trades, same book x session; p of the cut): dow {"dow": 2, "m": 0} ALL: L6M 0.01 PRE 0.80; regime {"cond": "prior_trend_day", "m": 0} ALL: L6M 0.50 PRE 0.19; dow {"dow": 2, "m": 0} P7: L6M 0.04 PRE 0.62; qgate {"feat": "dB", "m": 0.5, "q": 0.3, "tail": "high"} ALL: L6M 0.07 PRE 0.01; P7_lot_table_joint {"q_asia": 4, "q_london": 4, "q_nyam": 4} P7: L6M 0.18 PRE 0.37; l2_confirm_count_PROXY {"k": 2, "m": 0.5} ALL: L6M 0.07 PRE 0.37; zone_near_behind {"dist": 30, "m": 0.5} P7: L6M 0.35 PRE 0.70; qgate {"feat": "twap_dev_sg", "m": 0, "q": 0.2, "tail": "low"} O7: L6M 0.75 PRE 0.16; l2_confirm_count_PROXY {"k": 2, "m": 0} U7: L6M 0.23 PRE 0.29; regime {"cond": "prior_close_high", "m": 0} K7: L6M 0.04 PRE 0.65; qgate {"feat": "f_r_ab8", "m": 0, "q": 0.3, "tail": "high"} U7: L6M 0.15 PRE 0.05; regime {"cond": "prior_close_low", "m": 0} H7: L6M 0.01 PRE 0.27

## 8. Scorer difference (fgh complete-weeks scorer vs sz_core): maxDD cut on L6M, PRE, X' identical to 0.1 point for the top-20 cells; the equal-mean columns differ because L6M means differ (carry-week and window edge). Gate counts COMB: sz_core 2306, fgh scorer 2215.

## 9. What is expressible in D7 v1.5 today vs v1.6 (finalists and leads)
v1.5 fields used: per-book session lot table (six values asia,london,pre,nyam,nypm,close, lots 0-8), A06 slot half-hour list (x0.5 only, books K7 H7 P7 U7 today), B02 quiet-overnight halving (K7 P7 H7), TrendEr ladder (Q1-A: ER(20,5m)<0.30 -> x0.5), zone HALF. Rounding is rnd(lots x mult), min 1, in the order session -> slot/B02 -> ER -> zone.

| cell | exact v1.5 panel value or v1.6 need |
|--|--|
| dow {"dow": 2, "m": 0} ALL | v1.6 code (needs dow feature / calendar at the entry second) |
| regime {"cond": "prior_trend_day", "m": 0} ALL | v1.6 code (needs regime feature / calendar at the entry second) |
| dow {"dow": 2, "m": 0} P7 | v1.6 code (needs dow feature / calendar at the entry second) |
| qgate {"feat": "dB", "m": 0.5, "q": 0.3, "tail": "high"} ALL | v1.6 code (needs qgate feature / calendar at the entry second) |
| P7_lot_table_joint {"q_asia": 4, "q_london": 4, "q_nyam": 4} P7 | v1.5 panel TODAY: P7 SessionLots = "4,4,0,4,0,0" (asia,london,pre,nyam,nypm,close; live "7,7,0,7,0,0") |
| l2_confirm_count_PROXY {"k": 2, "m": 0.5} ALL | v1.6 code (needs l2_confirm_count_PROXY feature / calendar at the entry second) |
| zone_near_behind {"dist": 30, "m": 0.5} P7 | v1.6 code (needs zone_near_behind feature / calendar at the entry second) |
| qgate {"feat": "twap_dev_sg", "m": 0, "q": 0.2, "tail": "low"} O7 | v1.6 code (needs qgate feature / calendar at the entry second) |
| l2_confirm_count_PROXY {"k": 2, "m": 0} U7 | v1.6 code (needs l2_confirm_count_PROXY feature / calendar at the entry second) |
| regime {"cond": "prior_close_high", "m": 0} K7 | v1.6 code (needs regime feature / calendar at the entry second) |
| qgate {"feat": "f_r_ab8", "m": 0, "q": 0.3, "tail": "high"} U7 | v1.6 code (needs qgate feature / calendar at the entry second) |
| regime {"cond": "prior_close_low", "m": 0} H7 | v1.6 code (needs regime feature / calendar at the entry second) |
| P7_lot_table_joint {"q_asia": 7, "q_london": 4, "q_nyam": 4} P7 | v1.5 panel TODAY: P7 SessionLots = "7,4,0,4,0,0" (asia,london,pre,nyam,nypm,close; live "7,7,0,7,0,0") |
| P7_lot_table_joint {"q_asia": 7, "q_london": 3, "q_nyam": 4} P7 | v1.5 panel TODAY: P7 SessionLots = "7,3,0,4,0,0" (asia,london,pre,nyam,nypm,close; live "7,7,0,7,0,0") |
| P7_lot_table_joint {"q_asia": 6, "q_london": 4, "q_nyam": 4} P7 | v1.5 panel TODAY: P7 SessionLots = "6,4,0,4,0,0" (asia,london,pre,nyam,nypm,close; live "7,7,0,7,0,0") |
| P7_lot_table_joint {"q_asia": 7, "q_london": 4, "q_nyam": 3} P7 | v1.5 panel TODAY: P7 SessionLots = "7,4,0,3,0,0" (asia,london,pre,nyam,nypm,close; live "7,7,0,7,0,0") |

Effective P7 lots through the chain (session table -> slot/B02 halving -> Q1-A ladder; zone HALF not shown): table 7 -> 7 normal, 4 in slots 0330/0500/0830 or quiet B02 days; ER<0.30 halves again (7 -> 4 -> 2 in a half slot). Table 4: 4 -> 2 in half slots, 2 on ER<0.30 (round half up, min 1). So the 7/4/4 table means asia 7, london 4, nyam 4 before the halvings.
Session lot-table re-fit (greedy, in-sample, COMB down-only): {"K7|0": 1, "K7|1": 0, "K7|4": 0, "M7|1": 1, "M7|3": 0, "P7|0": 6, "P7|1": 3, "P7|3": 0, "U7|1": 0} (book|session index 0 asia 1 london 2 pre 3 nyam 4 nypm 5 close: lots); NOT recommended (walk-forward at equal mean -0.7%). Only the P7 cells walk forward positive; each is a per-session value in the P7 session string, expressible today without code.

## 10. OLD base vs new (S1b-COMB) - my cells re-scored on OLD-BASE (replica ITER14 HOLD, timer bar close, per-print old cut), same grid, same scorer. FIRST-ORDER SCREEN ONLY on both.

Base-change proof (Q1-A lots row = the zero-rule row for sizing): trades | cut exits | mean trade $ | top exits | maxDD L6M / HOLD / PRE
|--|--|--|--|--|--|
| S1b-COMB (new) | 21135 | 7144 | 117 | Target 9565, StateCut 6709, StopJoin 1819, StopJoinFallback 1143, Stop 891 | 79907 / 99496 / 140288 |
| OLD-BASE | 23776 | 13631 | 76 | ThL2Cut 12242, Target 9149, PolicyCut 1262, StopJoin 240, TimeBlock 222 | 141835 / 141835 / 165018 |

| cell | cut L6M/PRE/X' NEW | cut L6M/PRE/X' OLD | delta L6M/PRE | SEL new / old | rank new / old (of 6786) | identical to the dollar? |
|--|--|--|--|--|--|--|
| dow {"dow": 2, "m": 0} ALL | 51/0/41 | 49/1/-36 | +2/-1 | 34.3 / 14.7 | 4 / 246 | no |
| regime {"cond": "prior_trend_day", "m": 0} ALL | 6/41/62 | 25/39/-29 | -19/+2 | 31.6 / 11.8 | 10 / 398 | no |
| dow {"dow": 2, "m": 0} P7 | 32/8/36 | 42/-5/-1 | -11/+13 | 27.4 / 17.3 | 16 / 145 | no |
| qgate {"feat": "dB", "m": 0.5, "q": 0.3, "tail": "high"} ALL | 18/38/0 | 22/30/0 | -5/+7 | 17.7 / 4.7 | 112 / 1178 | no |
| P7_lot_table_joint {"q_asia": 4, "q_london": 4, "q_nyam": 4} P7 | 28/30/38 | 41/40/19 | -12/-10 | 16.6 / 20.1 | 133 / 92 | no |
| l2_confirm_count_PROXY {"k": 2, "m": 0.5} ALL | 28/19/31 | 3/10/30 | +25/+9 | 13.7 / -2.8 | 192 / 4701 | no |
| zone_near_behind {"dist": 30, "m": 0.5} P7 | 1/0/17 | 1/1/18 | +0/-1 | 6.1 / 10.1 | 684 / 525 | no |
| qgate {"feat": "twap_dev_sg", "m": 0, "q": 0.2, "tail": "low"} O7 | 0/1/0 | 0/-0/0 | -0/+1 | 1.0 / 0.7 | 1903 / 2695 | no |
| l2_confirm_count_PROXY {"k": 2, "m": 0} U7 | 5/14/9 | -6/-10/18 | +11/+24 | 8.1 / -5.5 | 471 / 5314 | no |
| regime {"cond": "prior_close_high", "m": 0} K7 | 7/2/15 | 7/-8/9 | -0/+10 | 7.8 / 3.6 | 517 / 1422 | no |
| qgate {"feat": "f_r_ab8", "m": 0, "q": 0.3, "tail": "high"} U7 | 4/13/0 | 1/0/0 | +4/+13 | 7.4 / -2.4 | 555 / 4571 | no |
| regime {"cond": "prior_close_low", "m": 0} H7 | 3/-1/12 | 1/-1/5 | +2/+1 | 4.2 / 0.1 | 927 / 3139 | no |
| P7_lot_table_joint {"q_asia": 7, "q_london": 4, "q_nyam": 4} P7 | 27/32/24 | 21/37/-0 | +6/-5 | 28.6 / 17.0 | 14 / 150 | no |
| P7_lot_table_joint {"q_asia": 7, "q_london": 3, "q_nyam": 4} P7 | 26/36/22 | 22/41/1 | +4/-6 | 27.1 / 15.9 | 19 / 179 | no |
| P7_lot_table_joint {"q_asia": 6, "q_london": 4, "q_nyam": 4} P7 | 29/33/34 | 32/41/8 | -3/-9 | 26.5 / 25.3 | 20 / 41 | no |
| P7_lot_table_joint {"q_asia": 7, "q_london": 4, "q_nyam": 3} P7 | 28/32/23 | 17/37/-8 | +10/-5 | 26.4 / 9.6 | 21 / 577 | no |
| P7_lot_table_joint {"q_asia": 6, "q_london": 3, "q_nyam": 4} P7 | 28/36/33 | 33/45/8 | -5/-9 | 25.1 / 24.4 | 30 / 50 | no |
| P7_lot_table_joint {"q_asia": 7, "q_london": 3, "q_nyam": 3} P7 | 26/36/22 | 19/41/-6 | +8/-5 | 24.7 / 8.2 | 33 / 698 | no |

Spearman rank correlation of SEL, new vs old base, all 6766 common cells: 0.65. Cells with L6M and PRE maxDD identical to the dollar on both bases: 0 (these six are degenerate count-feature gates, nA20/nA40/nB20 >= quantile 0, that switch off EVERY trade: zero P&L on both bases, cut 100%; not a base-independence defect; cells with > 90% of trades changed are now excluded from the tables).
