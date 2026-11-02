# DS3 D7 TAKE LINES (1-s evaluation) - the five THP_POLICY_D7 profit lines scored on the D7 v1.3 EXACT base (BASE-4)

Rolling page, written 2026-11-02T11:00Z. Prereg l2vast/ds3/prereg/D7_TAKE_LINES_prereg.md sha256 af2bb13bad8e3288b3f3b98114b0db5f5d21bf9be1446497fe605721ed4c59da (DECISIONS.md, logged before any line-effect statistic was read). dead_lookup before: the five specs are NOT FOUND in DEAD_CELLS (0 hits); append_cells after (see end). POST-HOC labels only; no PASS claim; mean and MDE (2.8 x SE of the weekly mean, paired for deltas) are columns, drawdown first.

**Base.** d7_v13x.run_v13x: D7 v1.3 EXACT (live11 lots, U7 exact = never binds, TH-L2 loss ON / profit-path OFF, HALF D20 + OTE-62 B73 D30, X1-X5 and signal-state Shadow, Native stops, ER(20) sizer, engine per-book locks; combined 12R stack week lock OFF = HEADLINE (user text), ON = Part B). "lines off" = the same base with the profit side empty. 1-S VERSION: lines evaluated EVERY PATH SECOND (redo 1-s path to 2026-10-30; rel_tot8 / rel_ahead8 rebuilt at 1 s from the 1-s L2 tables, ET-hour-normalised vs the prior 20 label days like curDepthRel, corr 0.95 with the 10-s cache values); first second where pct >= a and the rel gate holds; take exit cost 0.995 pt, tighten 30 = exit 1.01 pt when favourable extreme - current >= 30 pts. Weeks are ISO weeks of the label day; windows: F9 = 2026-02-07..2026-10-31 (the Feb-Oct window), L1M L2M L3M L6M HOLD MID PRE X' as windows.py. Equal-risk mean = mean x (lines-off worst-20 over ALL history / line worst-20 over ALL history), linear lot scaling (the integer-lot engine search is not run per row). Cells: "mean (MDE) / maxDD / worst-20 / SD / Calmar" all $k per week (maxDD of the weekly cumulative sum; worst-20 = sum of the 20 worst weeks, or the worst quarter of the weeks if the window has <20; Calmar = weekly mean / maxDD).

**READ FIRST (lock convention).** The user's literal lock text is: per-book week floor 12R + per-book day give-back lock (arm 2R, keep 50%) + ER(20) running-max sizer, with NO combined stack lock. The engine always carries those per-book locks, so PART A (combined stack lock OFF) is the HEADLINE and follows the user's text. PART B repeats everything WITH the combined 12R stack lock (the v1.1 convention). The five-line maxDD cut exists ONLY under the combined stack lock (F9 117.8k -> 132.6k, i.e. 13% WORSE, with it off; section A1); the lead is asking the user whether live D7 carries the combined 12R stack lock.

# PART A - HEADLINE: per-book locks only (combined stack lock OFF)

## A1. Headline: lines OFF vs the five lines ON - combined lock OFF (per-book locks only) - HEADLINE

| row | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| lines OFF | 33.7 (28.6) / 132.1 / -297.0 / 63.0 / 0.26 | 12.7 (94.8) / 97.7 / -97.7 / 75.7 / 0.13 | 23.4 (65.9) / 97.7 / -134.5 / 70.6 / 0.24 | 15.5 (45.8) / 97.7 / -166.2 / 58.9 / 0.16 | 37.1 (37.9) / 132.1 / 120.5 / 70.4 / 0.28 | 31.2 (23.5) / 139.2 / -540.9 / 60.4 / 0.22 | 23.3 (33.0) / 51.2 / -74.6 / 40.8 / 0.46 | 17.1 (14.8) / 166.3 / -753.1 / 45.8 / 0.10 | 4.7 (12.3) / 91.2 / -446.5 / 29.1 / 0.05 |
| five lines ON | 40.8 (24.8) / 56.7 / -0.9 / 54.6 / 0.72 | 27.6 (53.3) / 17.0 / -17.0 / 42.6 / 1.62 | 29.8 (39.5) / 17.0 / -26.5 / 42.3 / 1.75 | 23.1 (29.8) / 27.5 / -53.5 / 38.3 / 0.84 | 43.4 (30.1) / 56.7 / 348.1 / 55.8 / 0.77 | 37.5 (21.4) / 77.0 / -300.4 / 55.1 / 0.49 | 31.6 (42.5) / 29.0 / -64.7 / 52.6 / 1.09 | 16.6 (13.1) / 114.5 / -635.3 / 40.5 / 0.14 | 6.2 (11.7) / 62.0 / -355.8 / 27.8 / 0.10 |
| equal-risk mean ON | 54.1 (x1.33) | 36.7 | 39.6 | 30.7 | 57.6 | 49.7 | 41.9 | 22.0 | 8.2 |

Effect of the lines (ON minus OFF): F9: DD 132.1->56.7 (+57%) d+7.1k(MDE 13.0); L3M: DD 97.7->27.5 (+72%) d+7.6k(MDE 26.1); L6M: DD 132.1->56.7 (+57%) d+6.3k(MDE 16.2); HOLD: DD 139.2->77.0 (+45%) d+6.3k(MDE 12.4); MID: DD 51.2->29.0 (+43%) d+8.3k(MDE 20.2); PRE: DD 166.3->114.5 (+31%) d-0.6k(MDE 7.3); X': DD 91.2->62.0 (+32%) d+1.5k(MDE 8.3)

Tier columns for the five lines together: STRICT - / TOLERANT Y / NOW-ONLY Y.

F9 maxDD carrier week (trough): OFF 202637 (depth 132.1k); ON 202632 (56.7k).

## A2. One line at a time - combined lock OFF (per-book locks only) - HEADLINE
Contribution of a line = (system with the line) - (system without it): ADD = line alone on the lines-off base; REMOVE = full package minus full-without-that-line. Cell: DD without -> with (cut %) and delta mean (paired MDE). Positive cut = the line lowers maxDD.

### ADD
| line | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | DD 132.1->89.4 (+32%) d+2.3k(MDE 3.5) | DD 97.7->80.6 (+17%) d+3.3k(MDE 13.7) | DD 97.7->80.6 (+17%) d+1.9k(MDE 8.6) | DD 97.7->80.6 (+17%) d+2.9k(MDE 6.5) | DD 132.1->89.4 (+32%) d+2.5k(MDE 4.2) | DD 139.2->142.6 (-2%) d+1.9k(MDE 2.9) | DD 51.2->57.4 (-12%) d+1.8k(MDE 5.9) | DD 166.3->151.2 (+9%) d+0.4k(MDE 2.2) | DD 91.2->77.6 (+15%) d+0.4k(MDE 1.9) | Y/Y/Y |
| P7 | DD 132.1->110.0 (+17%) d+2.6k(MDE 8.6) | DD 97.7->63.4 (+35%) d+7.4k(MDE 27.2) | DD 97.7->63.4 (+35%) d+4.2k(MDE 19.5) | DD 97.7->63.4 (+35%) d+4.2k(MDE 14.7) | DD 132.1->110.0 (+17%) d+2.4k(MDE 10.2) | DD 139.2->110.0 (+21%) d+3.1k(MDE 8.4) | DD 51.2->41.2 (+19%) d+2.8k(MDE 15.4) | DD 166.3->146.4 (+12%) d-1.8k(MDE 5.0) | DD 91.2->61.4 (+33%) d-0.2k(MDE 6.0) | -/Y/Y |
| H7 | DD 132.1->128.9 (+2%) d-0.6k(MDE 3.2) | DD 97.7->102.0 (-4%) d-1.9k(MDE 5.4) | DD 97.7->102.0 (-4%) d-1.5k(MDE 3.9) | DD 97.7->102.0 (-4%) d-1.9k(MDE 3.3) | DD 132.1->128.9 (+2%) d-1.8k(MDE 3.1) | DD 139.2->140.4 (-1%) d-1.0k(MDE 2.8) | DD 51.2->44.0 (+14%) d+2.2k(MDE 7.3) | DD 166.3->147.8 (+11%) d+0.6k(MDE 1.6) | DD 91.2->93.8 (-3%) d+0.5k(MDE 2.1) | -/-/- |
| U7 | DD 132.1->110.6 (+16%) d+1.4k(MDE 3.7) | DD 97.7->67.9 (+31%) d+5.2k(MDE 18.6) | DD 97.7->67.9 (+31%) d+1.9k(MDE 10.9) | DD 97.7->67.9 (+31%) d+2.5k(MDE 8.0) | DD 132.1->110.6 (+16%) d+2.1k(MDE 4.8) | DD 139.2->119.9 (+14%) d+1.3k(MDE 3.0) | DD 51.2->45.2 (+12%) d-0.3k(MDE 4.7) | DD 166.3->164.3 (+1%) d+0.0k(MDE 1.5) | DD 91.2->101.6 (-11%) d+0.2k(MDE 1.8) | Y/Y/Y |
| W* | DD 132.1->124.3 (+6%) d+1.4k(MDE 2.2) | DD 97.7->94.1 (+4%) d+0.9k(MDE 3.7) | DD 97.7->94.1 (+4%) d+0.0k(MDE 2.9) | DD 97.7->94.1 (+4%) d-0.2k(MDE 2.1) | DD 132.1->124.3 (+6%) d+1.1k(MDE 2.4) | DD 139.2->130.9 (+6%) d+0.9k(MDE 1.8) | DD 51.2->45.8 (+10%) d+1.9k(MDE 4.4) | DD 166.3->168.7 (-1%) d+0.3k(MDE 1.3) | DD 91.2->94.0 (-3%) d+0.5k(MDE 1.4) | -/-/- |

### RM
| line | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | DD 77.6->56.7 (+27%) d+2.3k(MDE 3.5) | DD 34.1->17.0 (+50%) d+3.3k(MDE 13.7) | DD 34.1->17.0 (+50%) d+1.9k(MDE 8.6) | DD 37.0->27.5 (+26%) d+2.9k(MDE 6.5) | DD 77.6->56.7 (+27%) d+2.5k(MDE 4.2) | DD 77.6->77.0 (+1%) d+1.9k(MDE 2.9) | DD 23.0->29.0 (-26%) d+1.8k(MDE 5.9) | DD 127.3->114.5 (+10%) d+0.4k(MDE 2.2) | DD 69.2->62.0 (+10%) d+0.4k(MDE 1.9) | Y/Y/Y |
| P7 | DD 65.1->56.7 (+13%) d+2.6k(MDE 8.6) | DD 51.4->17.0 (+67%) d+7.4k(MDE 27.2) | DD 51.4->17.0 (+67%) d+4.2k(MDE 19.5) | DD 51.4->27.5 (+47%) d+4.2k(MDE 14.7) | DD 65.1->56.7 (+13%) d+2.4k(MDE 10.2) | DD 116.2->77.0 (+34%) d+3.1k(MDE 8.4) | DD 38.9->29.0 (+26%) d+2.8k(MDE 15.4) | DD 133.0->114.5 (+14%) d-1.8k(MDE 5.0) | DD 85.3->62.0 (+27%) d-0.2k(MDE 6.0) | -/-/Y |
| H7 | DD 73.7->56.7 (+23%) d-0.6k(MDE 3.2) | DD 12.8->17.0 (-33%) d-1.9k(MDE 5.4) | DD 12.8->17.0 (-33%) d-1.5k(MDE 3.9) | DD 25.4->27.5 (-8%) d-1.9k(MDE 3.3) | DD 73.7->56.7 (+23%) d-1.8k(MDE 3.1) | DD 74.1->77.0 (-4%) d-1.0k(MDE 2.8) | DD 36.1->29.0 (+20%) d+2.2k(MDE 7.3) | DD 130.7->114.5 (+12%) d+0.6k(MDE 1.6) | DD 64.2->62.0 (+4%) d+0.5k(MDE 2.1) | -/-/- |
| U7 | DD 59.6->56.7 (+5%) d+1.4k(MDE 3.7) | DD 46.9->17.0 (+64%) d+5.2k(MDE 18.6) | DD 46.9->17.0 (+64%) d+1.9k(MDE 10.9) | DD 46.9->27.5 (+41%) d+2.5k(MDE 8.0) | DD 59.6->56.7 (+5%) d+2.1k(MDE 4.8) | DD 94.6->77.0 (+19%) d+1.3k(MDE 3.0) | DD 34.9->29.0 (+17%) d-0.3k(MDE 4.7) | DD 118.6->114.5 (+4%) d+0.0k(MDE 1.5) | DD 61.2->62.0 (-1%) d+0.2k(MDE 1.8) | Y/Y/Y |
| W* | DD 65.1->56.7 (+13%) d+1.4k(MDE 2.2) | DD 20.7->17.0 (+18%) d+0.9k(MDE 3.7) | DD 20.7->17.0 (+18%) d+0.0k(MDE 2.9) | DD 26.7->27.5 (-3%) d-0.2k(MDE 2.1) | DD 65.1->56.7 (+13%) d+1.1k(MDE 2.4) | DD 83.7->77.0 (+8%) d+0.9k(MDE 1.8) | DD 45.1->29.0 (+36%) d+1.9k(MDE 4.4) | DD 116.9->114.5 (+2%) d+0.3k(MDE 1.3) | DD 56.2->62.0 (-10%) d+0.5k(MDE 1.4) | -/-/- |

## A3. Wildcard line by book (this lock setting, ADD on lines-off)
| cell | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| * on MV | DD 132.1->124.3 (+6%) d+1.4k(MDE 2.2) | DD 97.7->94.1 (+4%) d-0.2k(MDE 2.1) | DD 132.1->124.3 (+6%) d+1.1k(MDE 2.4) | DD 139.2->130.9 (+6%) d+0.9k(MDE 1.8) | DD 51.2->45.8 (+10%) d+1.9k(MDE 4.4) | DD 166.3->168.7 (-1%) d+0.3k(MDE 1.3) | DD 91.2->94.0 (-3%) d+0.5k(MDE 1.4) |
| * on PB | DD 132.1->132.1 (+0%) d+0.0k(MDE 0.0) | DD 97.7->97.7 (+0%) d+0.0k(MDE 0.0) | DD 132.1->132.1 (+0%) d+0.0k(MDE 0.0) | DD 139.2->139.2 (+0%) d+0.0k(MDE 0.0) | DD 51.2->51.2 (+0%) d+0.0k(MDE 0.0) | DD 166.3->166.3 (+0%) d+0.0k(MDE 0.0) | DD 91.2->91.2 (+0%) d+0.0k(MDE 0.0) |
| * on MV+PB | DD 132.1->124.3 (+6%) d+1.4k(MDE 2.2) | DD 97.7->94.1 (+4%) d-0.2k(MDE 2.1) | DD 132.1->124.3 (+6%) d+1.1k(MDE 2.4) | DD 139.2->130.9 (+6%) d+0.9k(MDE 1.8) | DD 51.2->45.8 (+10%) d+1.9k(MDE 4.4) | DD 166.3->168.7 (-1%) d+0.3k(MDE 1.3) | DD 91.2->94.0 (-3%) d+0.5k(MDE 1.4) |

Fallthrough reading of first-match (the * line also fires on K7/P7/H7/U7 when their own condition is not met), full vs the default full: F9: DD 56.7->77.9 (-38%) d-13.2k(MDE 9.0); L3M: DD 27.5->47.7 (-73%) d-5.1k(MDE 12.0); L6M: DD 56.7->77.9 (-38%) d-9.9k(MDE 10.9); HOLD: DD 77.0->130.2 (-69%) d-11.7k(MDE 7.7); PRE: DD 114.5->138.3 (-21%) d-4.6k(MDE 4.8)

## A4. Per book and per session (full minus lines-off)
Delta of the book (or session) own weekly series: mean $k/wk and maxDD of its own series off->on.

### F9
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +2.3 (3.5) | 63.4->38.3 |
| P7 | +2.6 (8.6) | 91.5->88.7 |
| U7 | +1.4 (3.7) | 39.3->18.6 |
| H7 | -0.6 (3.2) | 30.3->26.2 |
| M7 | +1.4 (2.2) | 58.4->29.5 |
| sess asia | +6.4 (10.1) | 82.8->37.9 |
| sess london | +0.6 (7.2) | 80.7->78.8 |
| sess nyam | +0.2 (2.0) | 25.2->32.3 |
| sess nypm | -0.1 (1.5) | 29.4->40.1 |

### L6M
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +2.5 (4.2) | 63.4->21.6 |
| P7 | +2.4 (10.2) | 91.5->88.7 |
| U7 | +2.1 (4.8) | 39.3->18.6 |
| H7 | -1.8 (3.1) | 30.3->26.2 |
| M7 | +1.1 (2.4) | 57.0->29.5 |
| sess asia | +5.6 (12.5) | 82.8->37.9 |
| sess london | +1.2 (9.1) | 80.7->78.8 |
| sess nyam | -0.2 (2.3) | 14.2->32.3 |
| sess nypm | -0.3 (1.8) | 27.2->40.1 |

### HOLD
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +1.9 (2.9) | 63.4->38.3 |
| P7 | +3.1 (8.4) | 143.7->102.8 |
| U7 | +1.3 (3.0) | 39.3->29.3 |
| H7 | -1.0 (2.8) | 30.3->26.2 |
| M7 | +0.9 (1.8) | 67.3->58.2 |
| sess asia | +5.0 (8.4) | 84.3->37.9 |
| sess london | +0.9 (5.8) | 110.0->95.5 |
| sess nyam | +0.4 (3.4) | 43.3->42.3 |
| sess nypm | +0.0 (1.3) | 37.4->52.1 |

### PRE
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.4 (2.2) | 36.9->41.1 |
| P7 | -1.8 (5.0) | 100.6->110.5 |
| U7 | +0.0 (1.5) | 63.4->55.4 |
| H7 | +0.6 (1.6) | 66.7->47.6 |
| M7 | +0.3 (1.3) | 87.9->61.6 |
| sess asia | -1.2 (4.4) | 64.9->48.8 |
| sess london | -0.8 (3.9) | 322.2->430.7 |
| sess nyam | +1.3 (3.5) | 56.2->55.5 |
| sess nypm | +0.2 (1.1) | 38.1->30.7 |

Book x session cells (F9 and HOLD delta mean $k/wk; only cells where the lines act):

| book|session | F9 | HOLD | PRE |
|---|---|---|---|
| K7|asia | +2.2 (2.4) | +1.6 (2.0) | +0.3 (1.1) |
| K7|london | -0.0 (1.8) | +0.0 (1.4) | -0.2 (0.9) |
| K7|nyam | +0.3 (1.2) | +0.3 (1.1) | +0.0 (0.9) |
| K7|nypm | -0.1 (1.5) | +0.0 (1.3) | +0.2 (1.1) |
| P7|asia | +3.8 (6.7) | +3.5 (5.4) | -1.6 (3.1) |
| P7|london | -1.2 (5.8) | -0.5 (4.9) | -1.4 (2.6) |
| P7|nyam | -0.0 (0.1) | +0.2 (2.8) | +1.1 (3.4) |
| U7|asia | +1.2 (2.8) | +1.1 (2.2) | -0.6 (1.0) |
| U7|london | +0.2 (2.0) | +0.3 (1.6) | +0.6 (1.3) |
| H7|asia | -0.8 (3.1) | -1.1 (2.6) | +0.6 (1.5) |
| H7|nyam | +0.2 (1.0) | +0.1 (0.8) | -0.0 (0.6) |
| M7|london | +1.7 (1.7) | +1.1 (1.4) | +0.2 (1.0) |
| M7|nyam | -0.3 (1.2) | -0.2 (1.1) | +0.1 (0.7) |

## A6. Placebos (full package replaced by random exits). Rank = share of placebo draws whose effect vs lines-OFF is at least as good as the real lines (maxDD cut larger / mean delta larger); small = real beats the placebo.

| placebo | window | draws | real maxDD cut | placebo median [5,95] | rank cut | real d mean | placebo med d mean | rank mean |
|---|---|---|---|---|---|---|---|---|
| P1 | F9 | 100 | +57% | -126% [-192,-50] | 0.00 | +7.1 | -35.8 | 0.00 |
| P1 | L3M | 100 | +72% | -100% [-190,-26] | 0.00 | +7.6 | -29.7 | 0.00 |
| P1 | L6M | 100 | +57% | -126% [-185,-44] | 0.00 | +6.3 | -35.9 | 0.00 |
| P1 | HOLD | 100 | +45% | -136% [-236,-74] | 0.00 | +6.3 | -33.3 | 0.00 |
| P1 | MID | 100 | +43% | -187% [-371,-48] | 0.00 | +8.3 | -32.3 | 0.00 |
| P1 | PRE | 100 | +31% | -450% [-575,-343] | 0.00 | -0.6 | -28.3 | 0.00 |
| P1 | X' | 100 | +32% | -423% [-558,-291] | 0.00 | +1.5 | -15.2 | 0.00 |
| P2 | F9 | 100 | +57% | -45% [-90,+3] | 0.00 | +7.1 | -16.5 | 0.00 |
| P2 | L3M | 100 | +72% | -18% [-77,+12] | 0.00 | +7.6 | -13.8 | 0.00 |
| P2 | L6M | 100 | +57% | -45% [-90,+3] | 0.00 | +6.3 | -16.4 | 0.00 |
| P2 | HOLD | 100 | +45% | -48% [-83,-15] | 0.00 | +6.3 | -16.2 | 0.00 |
| P2 | MID | 100 | +43% | -51% [-155,+3] | 0.00 | +8.3 | -16.0 | 0.00 |
| P2 | PRE | 100 | +31% | -91% [-182,-16] | 0.00 | -0.6 | -13.9 | 0.00 |
| P2 | X' | 100 | +32% | -129% [-257,-20] | 0.00 | +1.5 | -7.8 | 0.00 |
| P3 | F9 | 100 | +57% | +43% [+20,+60] | 0.13 | +7.1 | +5.8 | 0.24 |
| P3 | L3M | 100 | +72% | +33% [+12,+53] | 0.00 | +7.6 | +5.6 | 0.22 |
| P3 | L6M | 100 | +57% | +43% [+20,+60] | 0.13 | +6.3 | +6.4 | 0.56 |
| P3 | HOLD | 100 | +45% | +35% [+13,+52] | 0.13 | +6.3 | +5.1 | 0.28 |
| P3 | MID | 100 | +43% | +27% [-6,+57] | 0.23 | +8.3 | +3.5 | 0.05 |
| P3 | PRE | 100 | +31% | +22% [+8,+34] | 0.14 | -0.6 | +1.1 | 0.96 |
| P3 | X' | 100 | +32% | +30% [+2,+43] | 0.41 | +1.5 | +0.9 | 0.27 |

## A7. Leave-one-week-out (ISO 2026-W38) and leave-one-month-out, five lines vs lines off 

| window | all weeks | drop W38 | LOMO min cut | LOMO max cut | LOMO d mean range |
|---|---|---|---|---|---|
| F9 | DD 132.1->56.7 (+57%) d+7.1k(MDE 13.0) | DD 132.1->56.7 (+57%) d+7.8k(MDE 13.2) | +50% (drop 202609) | +70% (drop 202607) | +5.7..+8.8 |
| L3M | DD 97.7->27.5 (+72%) d+7.6k(MDE 26.1) | DD 97.7->27.5 (+72%) d+9.8k(MDE 27.5) | +54% (drop 202610) | +83% (drop 202608) | +2.4..+14.2 |
| L6M | DD 132.1->56.7 (+57%) d+6.3k(MDE 16.2) | DD 132.1->56.7 (+57%) d+7.2k(MDE 16.6) | +50% (drop 202609) | +72% (drop 202607) | +4.1..+8.6 |
| HOLD | DD 139.2->77.0 (+45%) d+6.3k(MDE 12.4) | DD 139.2->77.0 (+45%) d+6.8k(MDE 12.5) | +29% (drop 202601) | +46% (drop 202511) | +4.9..+8.0 |


MaxDD carrier weeks (trough week of the weekly-cumulative maxDD): F9: off 202637 / on 202632; L3M: off 202644 / on 202632; L6M: off 202637 / on 202632; HOLD: off 202608 / on 202549; PRE: off 202437 / on 202437; X': off 202347 / on 202351

# PART B - WITH the combined 12R stack lock (v1.1 convention)

## B1. Headline: lines OFF vs the five lines ON - 12R combined lock ON

| row | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| lines OFF | 26.8 (26.8) / 150.2 / -359.6 / 59.0 / 0.18 | 20.7 (61.1) / 26.3 / -26.3 / 48.8 / 0.79 | 21.8 (51.7) / 63.3 / -63.3 / 55.4 / 0.34 | 14.9 (35.7) / 65.7 / -75.5 / 45.9 / 0.23 | 29.2 (34.9) / 150.2 / -49.0 / 64.8 / 0.19 | 24.5 (21.6) / 150.2 / -436.3 / 55.7 / 0.16 | 19.0 (34.8) / 43.8 / -82.6 / 43.1 / 0.43 | 8.9 (12.7) / 132.4 / -507.8 / 39.4 / 0.07 | -4.6 (7.5) / 233.9 / -357.4 / 17.7 / -0.02 |
| five lines ON | 33.5 (25.8) / 81.1 / -206.7 / 56.8 / 0.41 | 22.1 (58.0) / 17.0 / -17.0 / 46.3 / 1.30 | 19.7 (42.1) / 24.0 / -32.4 / 45.1 / 0.82 | 15.4 (30.5) / 36.7 / -52.5 / 39.3 / 0.42 | 34.0 (31.5) / 81.1 / 97.0 / 58.4 / 0.42 | 27.9 (21.4) / 97.3 / -384.6 / 55.0 / 0.29 | 29.5 (43.8) / 46.1 / -68.2 / 54.2 / 0.64 | 10.9 (12.8) / 144.5 / -497.2 / 39.6 / 0.08 | -1.0 (10.0) / 140.7 / -361.0 / 23.7 / -0.01 |
| equal-risk mean ON | 36.8 (x1.10) | 24.3 | 21.6 | 16.9 | 37.4 | 30.6 | 32.4 | 12.0 | -1.1 |

Effect of the lines (ON minus OFF): F9: DD 150.2->81.1 (+46%) d+6.7k(MDE 11.8); L3M: DD 65.7->36.7 (+44%) d+0.4k(MDE 18.3); L6M: DD 150.2->81.1 (+46%) d+4.7k(MDE 12.8); HOLD: DD 150.2->97.3 (+35%) d+3.4k(MDE 9.8); MID: DD 43.8->46.1 (-5%) d+10.5k(MDE 24.4); PRE: DD 132.4->144.5 (-9%) d+2.1k(MDE 7.3); X': DD 233.9->140.7 (+40%) d+3.6k(MDE 9.4)

Tier columns for the five lines together: STRICT Y / TOLERANT Y / NOW-ONLY Y.

F9 maxDD carrier week (trough): OFF 202637 (depth 150.2k); ON 202634 (81.1k).

## B2. One line at a time - 12R combined lock ON
Contribution of a line = (system with the line) - (system without it): ADD = line alone on the lines-off base; REMOVE = full package minus full-without-that-line. Cell: DD without -> with (cut %) and delta mean (paired MDE). Positive cut = the line lowers maxDD.

### ADD
| line | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | DD 150.2->147.9 (+2%) d+0.1k(MDE 1.9) | DD 26.3->25.2 (+4%) d+0.1k(MDE 6.1) | DD 63.3->61.7 (+3%) d-0.9k(MDE 4.5) | DD 65.7->62.7 (+5%) d-0.5k(MDE 3.3) | DD 150.2->147.9 (+2%) d+0.2k(MDE 2.5) | DD 150.2->147.9 (+2%) d+0.9k(MDE 2.4) | DD 43.8->44.0 (-0%) d-0.3k(MDE 2.5) | DD 132.4->147.7 (-12%) d+0.8k(MDE 3.2) | DD 233.9->232.2 (+1%) d+0.1k(MDE 1.3) | -/-/- |
| P7 | DD 150.2->119.2 (+21%) d+1.5k(MDE 6.5) | DD 26.3->15.3 (+42%) d+1.3k(MDE 10.8) | DD 63.3->30.8 (+51%) d-0.2k(MDE 15.1) | DD 65.7->51.0 (+22%) d-1.4k(MDE 10.9) | DD 150.2->119.2 (+21%) d+1.3k(MDE 6.4) | DD 150.2->119.2 (+21%) d+0.2k(MDE 5.7) | DD 43.8->51.7 (-18%) d+1.9k(MDE 15.5) | DD 132.4->172.3 (-30%) d-0.2k(MDE 4.9) | DD 233.9->260.1 (-11%) d+0.7k(MDE 7.5) | -/-/- |
| H7 | DD 150.2->155.0 (-3%) d-2.3k(MDE 5.4) | DD 26.3->26.3 (+0%) d-0.7k(MDE 2.9) | DD 63.3->55.8 (+12%) d+0.3k(MDE 3.5) | DD 65.7->61.7 (+6%) d-0.0k(MDE 2.9) | DD 150.2->155.0 (-3%) d-1.2k(MDE 2.7) | DD 150.2->155.0 (-3%) d-2.5k(MDE 4.3) | DD 43.8->50.3 (-15%) d-4.6k(MDE 16.4) | DD 132.4->130.3 (+2%) d+0.3k(MDE 1.5) | DD 233.9->157.7 (+33%) d+2.1k(MDE 5.1) | -/-/- |
| U7 | DD 150.2->129.4 (+14%) d-2.6k(MDE 6.5) | DD 26.3->20.8 (+21%) d+1.8k(MDE 6.5) | DD 63.3->61.1 (+4%) d+0.4k(MDE 4.4) | DD 65.7->46.7 (+29%) d+1.6k(MDE 5.3) | DD 150.2->129.4 (+14%) d+0.7k(MDE 3.2) | DD 150.2->129.4 (+14%) d-1.1k(MDE 6.9) | DD 43.8->74.0 (-69%) d-9.7k(MDE 18.5) | DD 132.4->134.0 (-1%) d-0.1k(MDE 1.6) | DD 233.9->241.5 (-3%) d+0.0k(MDE 1.2) | -/-/Y |
| W* | DD 150.2->144.6 (+4%) d-1.4k(MDE 9.0) | DD 26.3->20.7 (+21%) d+1.9k(MDE 3.3) | DD 63.3->67.7 (-7%) d-11.8k(MDE 37.0) | DD 65.7->70.6 (-7%) d-8.2k(MDE 25.5) | DD 150.2->144.6 (+4%) d-2.8k(MDE 12.5) | DD 150.2->144.6 (+4%) d-1.3k(MDE 6.6) | DD 43.8->43.3 (+1%) d+1.7k(MDE 4.2) | DD 132.4->121.4 (+8%) d+0.8k(MDE 1.3) | DD 233.9->189.1 (+19%) d+1.2k(MDE 1.6) | -/-/- |

### RM
| line | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | DD 95.0->81.1 (+15%) d+3.6k(MDE 5.9) | DD 43.7->17.0 (+61%) d+5.2k(MDE 16.2) | DD 43.7->24.0 (+45%) d+2.0k(MDE 9.7) | DD 43.7->36.7 (+16%) d+2.2k(MDE 7.2) | DD 95.0->81.1 (+15%) d+2.0k(MDE 5.1) | DD 95.0->97.3 (-3%) d+0.2k(MDE 8.6) | DD 49.9->46.1 (+8%) d+6.8k(MDE 15.0) | DD 134.6->144.5 (-7%) d+1.5k(MDE 3.6) | DD 141.8->140.7 (+1%) d+0.2k(MDE 1.3) | Y/Y/Y |
| P7 | DD 76.6->81.1 (-6%) d+6.5k(MDE 10.8) | DD 15.3->17.0 (-11%) d-1.6k(MDE 7.9) | DD 51.0->24.0 (+53%) d-2.4k(MDE 14.2) | DD 31.3->36.7 (-17%) d-1.5k(MDE 11.8) | DD 76.6->81.1 (-6%) d+2.0k(MDE 8.8) | DD 76.6->97.3 (-27%) d+2.3k(MDE 10.2) | DD 58.4->46.1 (+21%) d+16.1k(MDE 27.2) | DD 145.6->144.5 (+1%) d+1.8k(MDE 6.6) | DD 127.8->140.7 (-10%) d+0.2k(MDE 6.5) | -/-/- |
| H7 | DD 48.8->81.1 (-66%) d-1.4k(MDE 3.2) | DD 15.3->17.0 (-11%) d-1.6k(MDE 3.4) | DD 24.0->24.0 (-0%) d-1.0k(MDE 2.2) | DD 22.6->36.7 (-63%) d-3.0k(MDE 4.7) | DD 48.1->81.1 (-68%) d-3.1k(MDE 3.0) | DD 100.4->97.3 (+3%) d-1.2k(MDE 2.6) | DD 48.8->46.1 (+6%) d+2.5k(MDE 6.9) | DD 152.0->144.5 (+5%) d-0.5k(MDE 1.1) | DD 226.3->140.7 (+38%) d+1.8k(MDE 4.8) | -/-/- |
| U7 | DD 122.8->81.1 (+34%) d+2.5k(MDE 5.1) | DD 43.3->17.0 (+61%) d+5.9k(MDE 15.4) | DD 43.3->24.0 (+45%) d+2.2k(MDE 9.2) | DD 49.1->36.7 (+25%) d+5.0k(MDE 12.0) | DD 122.8->81.1 (+34%) d+3.4k(MDE 6.7) | DD 122.8->97.3 (+21%) d+1.7k(MDE 3.8) | DD 50.6->46.1 (+9%) d+0.1k(MDE 5.2) | DD 134.1->144.5 (-8%) d+1.2k(MDE 3.2) | DD 181.3->140.7 (+22%) d+0.5k(MDE 3.4) | Y/-/Y |
| W* | DD 111.6->81.1 (+27%) d+1.6k(MDE 2.6) | DD 20.7->17.0 (+18%) d+1.5k(MDE 2.6) | DD 26.8->24.0 (+10%) d+0.5k(MDE 2.5) | DD 35.1->36.7 (-4%) d+0.1k(MDE 1.7) | DD 111.6->81.1 (+27%) d+2.1k(MDE 3.4) | DD 111.6->97.3 (+13%) d+0.8k(MDE 2.0) | DD 42.9->46.1 (-7%) d+0.2k(MDE 2.0) | DD 155.7->144.5 (+7%) d+0.9k(MDE 1.3) | DD 158.1->140.7 (+11%) d+0.4k(MDE 0.9) | Y/Y/Y |

## B3. Wildcard line by book (this lock setting, ADD on lines-off)
| cell | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| * on MV | DD 150.2->144.6 (+4%) d-1.4k(MDE 9.0) | DD 65.7->70.6 (-7%) d-8.2k(MDE 25.5) | DD 150.2->144.6 (+4%) d-2.8k(MDE 12.5) | DD 150.2->144.6 (+4%) d-1.3k(MDE 6.6) | DD 43.8->43.3 (+1%) d+1.7k(MDE 4.2) | DD 132.4->121.4 (+8%) d+0.8k(MDE 1.3) | DD 233.9->189.1 (+19%) d+1.2k(MDE 1.6) |
| * on PB | DD 150.2->150.2 (+0%) d+0.0k(MDE 0.0) | DD 65.7->65.7 (+0%) d+0.0k(MDE 0.0) | DD 150.2->150.2 (+0%) d+0.0k(MDE 0.0) | DD 150.2->150.2 (+0%) d+0.0k(MDE 0.0) | DD 43.8->43.8 (+0%) d+0.0k(MDE 0.0) | DD 132.4->132.4 (+0%) d+0.0k(MDE 0.0) | DD 233.9->233.9 (+0%) d+0.0k(MDE 0.0) |
| * on MV+PB | DD 150.2->144.6 (+4%) d-1.4k(MDE 9.0) | DD 65.7->70.6 (-7%) d-8.2k(MDE 25.5) | DD 150.2->144.6 (+4%) d-2.8k(MDE 12.5) | DD 150.2->144.6 (+4%) d-1.3k(MDE 6.6) | DD 43.8->43.3 (+1%) d+1.7k(MDE 4.2) | DD 132.4->121.4 (+8%) d+0.8k(MDE 1.3) | DD 233.9->189.1 (+19%) d+1.2k(MDE 1.6) |

Fallthrough reading of first-match (the * line also fires on K7/P7/H7/U7 when their own condition is not met), full vs the default full: F9: DD 81.1->109.5 (-35%) d-12.9k(MDE 12.5); L3M: DD 36.7->54.5 (-49%) d+0.0k(MDE 19.1); L6M: DD 81.1->109.5 (-35%) d-6.9k(MDE 13.0); HOLD: DD 97.3->127.2 (-31%) d-9.5k(MDE 9.8); PRE: DD 144.5->277.2 (-92%) d-4.6k(MDE 5.5)

## B4. Per book and per session (full minus lines-off)
Delta of the book (or session) own weekly series: mean $k/wk and maxDD of its own series off->on.

### F9
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +1.2 (2.4) | 52.2->48.4 |
| P7 | +1.9 (7.8) | 71.7->94.0 |
| U7 | +1.9 (3.8) | 26.1->19.0 |
| H7 | +1.0 (3.5) | 35.9->25.8 |
| M7 | +0.6 (2.0) | 44.8->39.0 |
| A6 | -0.1 (0.9) | 11.3->15.6 |
| sess asia | +6.9 (11.1) | 79.0->63.8 |
| sess london | +0.4 (6.6) | 71.3->67.2 |
| sess nyam | -0.5 (2.6) | 12.4->32.1 |
| sess nypm | -0.2 (1.2) | 21.4->32.1 |

### L6M
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +1.0 (2.9) | 30.7->25.6 |
| P7 | +0.9 (8.8) | 71.7->94.0 |
| U7 | +2.6 (4.7) | 26.1->19.0 |
| H7 | -0.2 (3.3) | 35.9->25.8 |
| M7 | +0.8 (2.4) | 44.8->39.0 |
| A6 | -0.4 (1.0) | 10.9->15.6 |
| sess asia | +4.1 (12.0) | 79.0->63.8 |
| sess london | +1.2 (7.8) | 71.3->67.2 |
| sess nyam | +0.0 (2.5) | 10.6->32.1 |
| sess nypm | -0.5 (1.5) | 10.9->28.4 |

### HOLD
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +1.2 (2.1) | 55.1->52.0 |
| P7 | +1.0 (6.5) | 72.7->117.5 |
| U7 | +0.8 (3.1) | 26.1->19.8 |
| H7 | +0.0 (2.9) | 35.9->25.8 |
| M7 | +0.4 (1.6) | 44.8->39.4 |
| A6 | -0.0 (0.7) | 11.3->15.6 |
| sess asia | +4.2 (8.6) | 79.0->63.8 |
| sess london | +0.2 (5.0) | 71.3->67.2 |
| sess nyam | -1.2 (3.6) | 51.2->109.2 |
| sess nypm | +0.1 (1.1) | 27.2->34.2 |

### PRE
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.4 (1.7) | 33.0->38.7 |
| P7 | +1.1 (5.7) | 97.3->145.6 |
| U7 | +0.3 (1.5) | 67.3->72.4 |
| H7 | -0.3 (1.7) | 40.1->38.5 |
| M7 | +0.5 (1.1) | 72.5->62.8 |
| A6 | +0.1 (0.4) | 17.3->15.8 |
| sess asia | -0.4 (4.7) | 73.8->75.4 |
| sess london | +0.4 (3.4) | 258.8->252.5 |
| sess nyam | +1.9 (3.6) | 87.2->93.1 |
| sess nypm | +0.2 (1.0) | 15.0->18.9 |

Book x session cells (F9 and HOLD delta mean $k/wk; only cells where the lines act):

| book|session | F9 | HOLD | PRE |
|---|---|---|---|
| K7|asia | +1.0 (2.2) | +0.6 (1.7) | +0.1 (0.8) |
| K7|london | +0.2 (1.6) | +0.1 (1.2) | +0.0 (0.7) |
| K7|nyam | +0.1 (1.1) | +0.3 (1.0) | +0.1 (0.6) |
| K7|nypm | -0.2 (1.2) | +0.1 (1.1) | +0.2 (1.0) |
| P7|asia | +3.1 (6.3) | +2.6 (4.8) | -0.2 (3.0) |
| P7|london | -0.7 (5.6) | -0.4 (4.4) | -0.5 (2.8) |
| P7|nyam | -0.4 (1.3) | -1.2 (3.0) | +1.8 (3.5) |
| U7|asia | +2.0 (3.6) | +1.0 (2.8) | -0.3 (0.9) |
| U7|london | -0.0 (2.0) | -0.2 (1.6) | +0.6 (1.1) |
| H7|asia | +0.9 (3.5) | -0.0 (2.8) | -0.1 (1.6) |
| H7|nyam | +0.1 (0.8) | +0.0 (0.7) | -0.2 (0.4) |
| M7|london | +0.9 (1.5) | +0.7 (1.2) | +0.3 (0.8) |
| M7|nyam | -0.3 (1.0) | -0.3 (0.9) | +0.2 (0.6) |
| A6|asia | -0.1 (0.9) | -0.0 (0.7) | +0.1 (0.4) |

## B6. Placebos (full package replaced by random exits). Rank = share of placebo draws whose effect vs lines-OFF is at least as good as the real lines (maxDD cut larger / mean delta larger); small = real beats the placebo.

| placebo | window | draws | real maxDD cut | placebo median [5,95] | rank cut | real d mean | placebo med d mean | rank mean |
|---|---|---|---|---|---|---|---|---|
| P1 | F9 | 100 | +46% | -20% [-70,+12] | 0.01 | +6.7 | -25.9 | 0.00 |
| P1 | L3M | 100 | +44% | -72% [-191,+8] | 0.00 | +0.4 | -20.0 | 0.00 |
| P1 | L6M | 100 | +46% | -18% [-66,+13] | 0.02 | +4.7 | -26.0 | 0.00 |
| P1 | HOLD | 100 | +35% | -40% [-95,-5] | 0.00 | +3.4 | -23.6 | 0.00 |
| P1 | MID | 100 | -5% | -117% [-242,-26] | 0.02 | +10.5 | -23.7 | 0.00 |
| P1 | PRE | 100 | -9% | -445% [-573,-356] | 0.00 | +2.1 | -17.2 | 0.00 |
| P1 | X' | 100 | +40% | -71% [-111,-31] | 0.00 | +3.6 | -4.5 | 0.00 |
| P2 | F9 | 100 | +46% | -7% [-32,+21] | 0.01 | +6.7 | -12.7 | 0.00 |
| P2 | L3M | 100 | +44% | -31% [-94,+20] | 0.01 | +0.4 | -11.6 | 0.02 |
| P2 | L6M | 100 | +46% | -7% [-32,+21] | 0.01 | +4.7 | -12.5 | 0.00 |
| P2 | HOLD | 100 | +35% | -7% [-39,+14] | 0.02 | +3.4 | -11.8 | 0.00 |
| P2 | MID | 100 | -5% | -27% [-114,+15] | 0.26 | +10.5 | -12.8 | 0.00 |
| P2 | PRE | 100 | -9% | -191% [-310,-58] | 0.00 | +2.1 | -9.5 | 0.00 |
| P2 | X' | 100 | +40% | -9% [-53,+36] | 0.04 | +3.6 | -0.8 | 0.00 |
| P3 | F9 | 100 | +46% | +34% [+2,+69] | 0.38 | +6.7 | +1.4 | 0.02 |
| P3 | L3M | 100 | +44% | +35% [-10,+63] | 0.38 | +0.4 | +0.8 | 0.53 |
| P3 | L6M | 100 | +46% | +34% [+2,+70] | 0.38 | +4.7 | +2.4 | 0.27 |
| P3 | HOLD | 100 | +35% | +32% [+2,+59] | 0.41 | +3.4 | +1.3 | 0.19 |
| P3 | MID | 100 | -5% | -5% [-60,+15] | 0.50 | +10.5 | -2.7 | 0.00 |
| P3 | PRE | 100 | -9% | -17% [-65,+10] | 0.34 | +2.1 | +1.9 | 0.46 |
| P3 | X' | 100 | +40% | +22% [-6,+48] | 0.18 | +3.6 | +2.2 | 0.18 |

## B7. Leave-one-week-out (ISO 2026-W38) and leave-one-month-out, five lines vs lines off 

| window | all weeks | drop W38 | LOMO min cut | LOMO max cut | LOMO d mean range |
|---|---|---|---|---|---|
| F9 | DD 150.2->81.1 (+46%) d+6.7k(MDE 11.8) | DD 150.2->81.1 (+46%) d+7.4k(MDE 12.0) | +30% (drop 202607) | +60% (drop 202608) | +4.1..+8.5 |
| L3M | DD 65.7->36.7 (+44%) d+0.4k(MDE 18.3) | DD 65.7->36.7 (+44%) d+2.1k(MDE 19.3) | +28% (drop 202608) | +44% (drop 202610) | -2.9..+4.4 |
| L6M | DD 150.2->81.1 (+46%) d+4.7k(MDE 12.8) | DD 150.2->81.1 (+46%) d+5.7k(MDE 13.0) | +43% (drop 202609) | +62% (drop 202608) | +2.3..+7.0 |
| HOLD | DD 150.2->97.3 (+35%) d+3.4k(MDE 9.8) | DD 150.2->97.3 (+35%) d+3.8k(MDE 10.0) | -31% (drop 202607) | +46% (drop 202602) | +1.2..+5.7 |


MaxDD carrier weeks (trough week of the weekly-cumulative maxDD): F9: off 202637 / on 202634; L3M: off 202637 / on 202634; L6M: off 202637 / on 202634; HOLD: off 202637 / on 202608; PRE: off 202440 / on 202512; X': off 202351 / on 202339


## BASIS CAVEAT (BASE-4, added after the fill-basis finding; see DS3_TAKE_FILL_ARTEFACT_V13Y.md)
The take / tighten deltas of this page are measured against the MEASURED baseline (pts_lib - fill_cost_pts) while the engine baseline is basis N (target exits carry no limit-fill cost). A take on a trade that would have exited at the target is therefore credited fill_cost_pts (mean 3.39 pts per lot) that the N baseline never paid; placebo exits carry the same credit, so the placebo RANKS are internally consistent, but the MEAN and the drawdown cut of the take lines are overstated relative to a pure N-basis comparison. With nfix=True (N-basis consistent delta) the gated lines and the plain take LOSE the benefit: lock none 1-s, gated exact F9 cut +39% -> -32%, d mean -9.0k -> -21.7k/wk; plain 0.70 all F9 +57% -> +2%, d mean +7.1k -> -9.0k; L6M +57% -> +2%. Which baseline is right depends on whether live target limit orders suffer the measured 3.4-pt fill shortfall (basis M: then taking at 70% saves it and the first numbers hold) or fill at the touch (basis N). THIS IS A QUESTION FOR THE USER/LEAD before any take-line is called a finding.
