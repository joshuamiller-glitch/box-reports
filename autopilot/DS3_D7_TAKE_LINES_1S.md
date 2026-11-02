# DS3 D7 TAKE LINES (1-s evaluation) - the five THP_POLICY_D7 profit lines scored on the D7 v1.3 EXACT base (BASE-4)

Rolling page, written 2026-11-02T04:38Z. Prereg l2vast/ds3/prereg/D7_TAKE_LINES_prereg.md sha256 af2bb13bad8e3288b3f3b98114b0db5f5d21bf9be1446497fe605721ed4c59da (DECISIONS.md, logged before any line-effect statistic was read). dead_lookup before: the five specs are NOT FOUND in DEAD_CELLS (0 hits); append_cells after (see end). POST-HOC labels only; no PASS claim; mean and MDE (2.8 x SE of the weekly mean, paired for deltas) are columns, drawdown first.

**Base.** d7_v13x.run_v13x: D7 v1.3 EXACT (live11 lots, U7 exact = never binds, TH-L2 loss ON / profit-path OFF, HALF D20 + OTE-62 B73 D30, X1-X5 and signal-state Shadow, Native stops, ER(20) sizer, engine per-book locks; combined 12R stack week lock OFF = HEADLINE (user text), ON = Part B). "lines off" = the same base with the profit side empty. 1-S VERSION: lines evaluated EVERY PATH SECOND (redo 1-s path to 2026-10-30; rel_tot8 / rel_ahead8 rebuilt at 1 s from the 1-s L2 tables, ET-hour-normalised vs the prior 20 label days like curDepthRel, corr 0.95 with the 10-s cache values); first second where pct >= a and the rel gate holds; take exit cost 0.995 pt, tighten 30 = exit 1.01 pt when favourable extreme - current >= 30 pts. Weeks are ISO weeks of the label day; windows: F9 = 2026-02-07..2026-10-31 (the Feb-Oct window), L1M L2M L3M L6M HOLD MID PRE X' as windows.py. Equal-risk mean = mean x (lines-off worst-20 over ALL history / line worst-20 over ALL history), linear lot scaling (the integer-lot engine search is not run per row). Cells: "mean (MDE) / maxDD / worst-20 / SD / Calmar" all $k per week (maxDD of the weekly cumulative sum; worst-20 = sum of the 20 worst weeks, or the worst quarter of the weeks if the window has <20; Calmar = weekly mean / maxDD).

**READ FIRST (lock convention).** The user's literal lock text is: per-book week floor 12R + per-book day give-back lock (arm 2R, keep 50%) + ER(20) running-max sizer, with NO combined stack lock. The engine always carries those per-book locks, so PART A (combined stack lock OFF) is the HEADLINE and follows the user's text. PART B repeats everything WITH the combined 12R stack lock (the v1.1 convention). The five-line maxDD cut exists ONLY under the combined stack lock (F9 117.8k -> 132.6k, i.e. 13% WORSE, with it off; section A1); the lead is asking the user whether live D7 carries the combined 12R stack lock.

# PART A - HEADLINE: per-book locks only (combined stack lock OFF)

## A1. Headline: lines OFF vs the five lines ON - combined lock OFF (per-book locks only) - HEADLINE

| row | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| lines OFF | 35.0 (28.6) / 117.8 / -272.1 / 63.0 / 0.30 | 15.5 (95.7) / 97.7 / -97.7 / 76.4 / 0.16 | 25.9 (65.5) / 97.7 / -134.5 / 70.2 / 0.26 | 17.2 (45.7) / 97.7 / -160.0 / 58.9 / 0.18 | 38.8 (38.0) / 117.8 / 146.2 / 70.6 / 0.33 | 33.0 (23.5) / 130.5 / -510.5 / 60.5 / 0.25 | 23.7 (32.4) / 45.0 / -69.4 / 40.1 / 0.53 | 17.9 (14.9) / 165.1 / -758.3 / 46.1 / 0.11 | 4.8 (12.3) / 91.2 / -445.6 / 29.1 / 0.05 |
| five lines ON | 19.7 (23.2) / 132.4 / -375.0 / 51.2 / 0.15 | 14.2 (56.7) / 34.7 / -34.7 / 45.3 / 0.41 | 20.6 (42.0) / 34.7 / -66.5 / 45.0 / 0.59 | 12.1 (32.8) / 72.2 / -121.4 / 42.2 / 0.17 | 27.3 (27.1) / 115.9 / 74.0 / 50.4 / 0.24 | 20.9 (20.4) / 201.4 / -664.9 / 52.6 / 0.10 | 1.0 (39.0) / 132.4 / -170.4 / 48.2 / 0.01 | 8.5 (12.5) / 192.6 / -725.1 / 38.6 / 0.04 | -0.5 (10.2) / 132.0 / -429.3 / 24.1 / -0.00 |
| equal-risk mean ON | 20.6 (x1.05) | 14.8 | 21.6 | 12.6 | 28.6 | 21.8 | 1.0 | 8.9 | -0.5 |

Effect of the lines (ON minus OFF): F9: DD 117.8->132.4 (-12%) d-15.3k(MDE 15.7); L3M: DD 97.7->72.2 (+26%) d-5.1k(MDE 25.1); L6M: DD 117.8->115.9 (+2%) d-11.5k(MDE 20.5); HOLD: DD 130.5->201.4 (-54%) d-12.1k(MDE 13.0); MID: DD 45.0->132.4 (-194%) d-22.8k(MDE 19.2); PRE: DD 165.1->192.6 (-17%) d-9.5k(MDE 8.1); X': DD 91.2->132.0 (-45%) d-5.3k(MDE 7.6)

Tier columns for the five lines together: STRICT - / TOLERANT - / NOW-ONLY -.

F9 maxDD carrier week (trough): OFF 202637 (depth 117.8k); ON 202613 (132.4k).

## A2. One line at a time - combined lock OFF (per-book locks only) - HEADLINE
Contribution of a line = (system with the line) - (system without it): ADD = line alone on the lines-off base; REMOVE = full package minus full-without-that-line. Cell: DD without -> with (cut %) and delta mean (paired MDE). Positive cut = the line lowers maxDD.

### ADD
| line | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | DD 117.8->94.7 (+20%) d+0.1k(MDE 2.7) | DD 97.7->94.7 (+3%) d+1.1k(MDE 2.7) | DD 97.7->94.7 (+3%) d+0.7k(MDE 5.4) | DD 97.7->94.7 (+3%) d+1.0k(MDE 4.5) | DD 117.8->94.7 (+20%) d+0.3k(MDE 3.4) | DD 130.5->137.6 (-5%) d+0.2k(MDE 2.2) | DD 45.0->51.0 (-13%) d-0.4k(MDE 4.1) | DD 165.1->163.8 (+1%) d+0.3k(MDE 1.8) | DD 91.2->90.2 (+1%) d+0.3k(MDE 1.1) | Y/Y/Y |
| P7 | DD 117.8->111.4 (+5%) d-9.7k(MDE 11.9) | DD 97.7->65.9 (+33%) d-9.9k(MDE 35.0) | DD 97.7->65.9 (+33%) d-6.8k(MDE 19.3) | DD 97.7->68.5 (+30%) d-5.7k(MDE 16.1) | DD 117.8->111.4 (+5%) d-6.2k(MDE 15.0) | DD 130.5->156.6 (-20%) d-6.5k(MDE 10.0) | DD 45.0->101.1 (-125%) d-16.7k(MDE 16.4) | DD 165.1->218.3 (-32%) d-8.2k(MDE 6.2) | DD 91.2->126.3 (-38%) d-3.6k(MDE 6.1) | -/-/- |
| H7 | DD 117.8->113.8 (+3%) d-4.1k(MDE 4.6) | DD 97.7->98.3 (-1%) d-2.7k(MDE 9.1) | DD 97.7->98.3 (-1%) d-2.2k(MDE 8.4) | DD 97.7->98.3 (-1%) d-2.3k(MDE 6.0) | DD 117.8->113.8 (+3%) d-5.3k(MDE 5.7) | DD 130.5->135.3 (-4%) d-4.8k(MDE 3.6) | DD 45.0->35.9 (+20%) d-1.2k(MDE 7.0) | DD 165.1->142.5 (+14%) d-0.7k(MDE 2.2) | DD 91.2->83.9 (+8%) d+0.1k(MDE 2.4) | -/-/- |
| U7 | DD 117.8->137.8 (-17%) d-2.8k(MDE 5.3) | DD 97.7->56.8 (+42%) d+8.9k(MDE 26.8) | DD 97.7->56.8 (+42%) d+2.5k(MDE 16.4) | DD 97.7->56.8 (+42%) d+2.1k(MDE 11.3) | DD 117.8->137.8 (-17%) d-1.8k(MDE 6.7) | DD 130.5->137.8 (-6%) d-1.9k(MDE 4.0) | DD 45.0->34.0 (+25%) d-4.8k(MDE 8.2) | DD 165.1->172.2 (-4%) d-1.0k(MDE 2.3) | DD 91.2->118.8 (-30%) d-2.2k(MDE 2.4) | -/-/- |
| W* | DD 117.8->116.2 (+1%) d+1.2k(MDE 2.2) | DD 97.7->95.3 (+3%) d+1.4k(MDE 4.4) | DD 97.7->95.3 (+3%) d+0.6k(MDE 3.0) | DD 97.7->95.3 (+3%) d-0.2k(MDE 2.2) | DD 117.8->116.2 (+1%) d+1.5k(MDE 2.5) | DD 130.5->126.7 (+3%) d+0.8k(MDE 1.8) | DD 45.0->45.0 (+0%) d+0.4k(MDE 4.0) | DD 165.1->172.3 (-4%) d+0.1k(MDE 1.1) | DD 91.2->95.7 (-5%) d+0.1k(MDE 1.4) | -/-/- |

### RM
| line | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | DD 140.2->132.4 (+6%) d+0.1k(MDE 2.7) | DD 36.7->34.7 (+5%) d+1.1k(MDE 2.7) | DD 42.1->34.7 (+18%) d+0.7k(MDE 5.4) | DD 76.8->72.2 (+6%) d+1.0k(MDE 4.5) | DD 131.7->115.9 (+12%) d+0.3k(MDE 3.4) | DD 208.0->201.4 (+3%) d+0.2k(MDE 2.2) | DD 140.2->132.4 (+6%) d-0.4k(MDE 4.1) | DD 192.8->192.6 (+0%) d+0.3k(MDE 1.8) | DD 150.5->132.0 (+12%) d+0.3k(MDE 1.1) | Y/-/Y |
| P7 | DD 118.9->132.4 (-11%) d-9.7k(MDE 11.9) | DD 51.9->34.7 (+33%) d-9.9k(MDE 35.0) | DD 51.9->34.7 (+33%) d-6.8k(MDE 19.3) | DD 58.1->72.2 (-24%) d-5.7k(MDE 16.1) | DD 118.9->115.9 (+2%) d-6.2k(MDE 15.0) | DD 130.2->201.4 (-55%) d-6.5k(MDE 10.1) | DD 39.1->132.4 (-239%) d-16.7k(MDE 16.4) | DD 149.5->192.6 (-29%) d-8.2k(MDE 6.2) | DD 110.8->132.0 (-19%) d-3.6k(MDE 6.1) | -/-/- |
| H7 | DD 127.5->132.4 (-4%) d-4.2k(MDE 4.6) | DD 42.1->34.7 (+18%) d-2.7k(MDE 9.1) | DD 42.1->34.7 (+18%) d-2.2k(MDE 8.4) | DD 70.1->72.2 (-3%) d-2.3k(MDE 6.0) | DD 127.5->115.9 (+9%) d-5.3k(MDE 5.7) | DD 161.2->201.4 (-25%) d-4.7k(MDE 3.6) | DD 106.2->132.4 (-25%) d-1.2k(MDE 7.0) | DD 202.7->192.6 (+5%) d-0.6k(MDE 2.2) | DD 146.8->132.0 (+10%) d+0.1k(MDE 2.4) | -/-/- |
| U7 | DD 97.9->132.4 (-35%) d-2.8k(MDE 5.3) | DD 61.0->34.7 (+43%) d+8.9k(MDE 26.8) | DD 61.0->34.7 (+43%) d+2.5k(MDE 16.4) | DD 77.4->72.2 (+7%) d+2.1k(MDE 11.3) | DD 91.3->115.9 (-27%) d-1.8k(MDE 6.7) | DD 164.7->201.4 (-22%) d-1.9k(MDE 4.0) | DD 97.9->132.4 (-35%) d-4.8k(MDE 8.2) | DD 184.5->192.6 (-4%) d-1.0k(MDE 2.3) | DD 103.8->132.0 (-27%) d-2.2k(MDE 2.4) | -/-/- |
| W* | DD 122.7->132.4 (-8%) d+1.2k(MDE 2.2) | DD 32.2->34.7 (-8%) d+1.4k(MDE 4.4) | DD 34.7->34.7 (+0%) d+0.6k(MDE 3.0) | DD 66.1->72.2 (-9%) d-0.2k(MDE 2.2) | DD 122.6->115.9 (+5%) d+1.5k(MDE 2.5) | DD 195.5->201.4 (-3%) d+0.8k(MDE 1.8) | DD 122.7->132.4 (-8%) d+0.4k(MDE 4.0) | DD 211.7->192.6 (+9%) d+0.1k(MDE 1.1) | DD 147.0->132.0 (+10%) d+0.1k(MDE 1.4) | -/-/- |

## A3. Wildcard line by book (this lock setting, ADD on lines-off)
| cell | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| * on MV | DD 117.8->116.2 (+1%) d+1.2k(MDE 2.2) | DD 97.7->95.3 (+3%) d-0.2k(MDE 2.2) | DD 117.8->116.2 (+1%) d+1.5k(MDE 2.5) | DD 130.5->126.7 (+3%) d+0.8k(MDE 1.8) | DD 45.0->45.0 (+0%) d+0.4k(MDE 4.0) | DD 165.1->172.3 (-4%) d+0.1k(MDE 1.1) | DD 91.2->95.7 (-5%) d+0.1k(MDE 1.4) |
| * on PB | DD 117.8->117.8 (+0%) d+0.0k(MDE 0.0) | DD 97.7->97.7 (+0%) d+0.0k(MDE 0.0) | DD 117.8->117.8 (+0%) d+0.0k(MDE 0.0) | DD 130.5->130.5 (+0%) d+0.0k(MDE 0.0) | DD 45.0->45.0 (+0%) d+0.0k(MDE 0.0) | DD 165.1->165.1 (+0%) d+0.0k(MDE 0.0) | DD 91.2->91.2 (+0%) d+0.0k(MDE 0.0) |
| * on MV+PB | DD 117.8->116.2 (+1%) d+1.2k(MDE 2.2) | DD 97.7->95.3 (+3%) d-0.2k(MDE 2.2) | DD 117.8->116.2 (+1%) d+1.5k(MDE 2.5) | DD 130.5->126.7 (+3%) d+0.8k(MDE 1.8) | DD 45.0->45.0 (+0%) d+0.4k(MDE 4.0) | DD 165.1->172.3 (-4%) d+0.1k(MDE 1.1) | DD 91.2->95.7 (-5%) d+0.1k(MDE 1.4) |

## A4. Per book and per session (full minus lines-off)
Delta of the book (or session) own weekly series: mean $k/wk and maxDD of its own series off->on.

### F9
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.1 (2.7) | 63.4->51.2 |
| P7 | -9.7 (11.9) | 85.7->101.0 |
| U7 | -2.8 (5.3) | 39.3->33.3 |
| H7 | -4.1 (4.6) | 30.3->29.6 |
| M7 | +1.2 (2.2) | 51.4->34.5 |
| A6 | +0.0 (0.0) | 17.9->17.9 |
| sess asia | -11.3 (11.4) | 82.8->111.7 |
| sess london | -2.7 (10.1) | 74.9->89.2 |
| sess nyam | -0.7 (2.3) | 25.2->52.1 |
| sess nypm | -0.7 (1.1) | 28.5->52.6 |

### L6M
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.3 (3.4) | 63.4->40.9 |
| P7 | -6.3 (15.0) | 85.7->63.0 |
| U7 | -1.8 (6.7) | 39.3->32.0 |
| H7 | -5.2 (5.7) | 30.3->29.6 |
| M7 | +1.5 (2.5) | 50.0->34.5 |
| A6 | +0.0 (0.0) | 17.9->17.9 |
| sess asia | -12.5 (15.5) | 82.8->111.7 |
| sess london | +1.8 (12.5) | 74.9->62.9 |
| sess nyam | +0.1 (2.1) | 14.2->24.2 |
| sess nypm | -0.9 (1.5) | 26.2->44.2 |

### HOLD
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.2 (2.2) | 63.4->51.2 |
| P7 | -6.6 (10.0) | 137.6->163.7 |
| U7 | -1.9 (4.0) | 39.3->33.3 |
| H7 | -4.7 (3.6) | 30.3->29.6 |
| M7 | +0.8 (1.8) | 56.4->48.7 |
| A6 | +0.0 (0.0) | 19.3->19.3 |
| sess asia | -9.7 (9.2) | 84.3->146.4 |
| sess london | -1.5 (7.8) | 87.8->116.3 |
| sess nyam | -0.6 (3.2) | 41.4->58.4 |
| sess nypm | -0.3 (1.0) | 38.6->59.1 |

### PRE
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.3 (1.8) | 35.4->39.1 |
| P7 | -8.2 (6.2) | 100.6->171.9 |
| U7 | -1.0 (2.3) | 63.4->44.2 |
| H7 | -0.6 (2.2) | 66.7->35.3 |
| M7 | +0.1 (1.1) | 87.9->64.2 |
| A6 | -0.0 (0.1) | 17.4->17.4 |
| sess asia | -4.9 (5.8) | 64.9->85.8 |
| sess london | -2.3 (3.7) | 310.7->450.1 |
| sess nyam | -2.7 (3.9) | 56.2->85.0 |
| sess nypm | +0.3 (0.8) | 32.2->30.3 |

Book x session cells (F9 and HOLD delta mean $k/wk; only cells where the lines act):

| book|session | F9 | HOLD | PRE |
|---|---|---|---|
| K7|asia | +1.1 (1.8) | +0.7 (1.4) | +0.2 (0.8) |
| K7|london | -0.4 (1.8) | -0.5 (1.4) | -0.2 (0.7) |
| K7|nyam | +0.1 (1.0) | +0.2 (0.9) | -0.1 (0.6) |
| K7|nypm | -0.7 (1.1) | -0.3 (1.0) | +0.3 (0.8) |
| P7|asia | -5.9 (7.8) | -4.2 (6.4) | -3.4 (3.8) |
| P7|london | -2.9 (8.7) | -1.6 (6.9) | -2.5 (2.8) |
| P7|nyam | -0.9 (1.8) | -0.8 (2.8) | -2.2 (3.6) |
| U7|asia | -2.2 (3.3) | -1.7 (2.6) | -1.4 (1.5) |
| U7|london | -0.6 (3.0) | -0.2 (2.4) | +0.4 (1.7) |
| H7|asia | -4.2 (4.4) | -4.6 (3.4) | -0.2 (2.2) |
| H7|nyam | +0.1 (1.1) | -0.1 (1.0) | -0.4 (0.7) |
| M7|london | +1.2 (1.8) | +0.7 (1.4) | +0.1 (0.8) |
| M7|nyam | +0.0 (0.9) | +0.1 (0.9) | +0.0 (0.6) |
| A6|asia | +0.0 (0.0) | +0.0 (0.0) | -0.0 (0.1) |

## A7. Leave-one-week-out (ISO 2026-W38) and leave-one-month-out, five lines vs lines off 

| window | all weeks | drop W38 | LOMO min cut | LOMO max cut | LOMO d mean range |
|---|---|---|---|---|---|
| F9 | DD 117.8->132.4 (-12%) d-15.3k(MDE 15.7) | DD 117.8->132.4 (-12%) d-15.1k(MDE 16.1) | -35% (drop 202607) | +2% (drop 202602) | -17.2..-11.8 |
| L3M | DD 97.7->72.2 (+26%) d-5.1k(MDE 25.1) | DD 97.7->72.2 (+26%) d-3.6k(MDE 26.9) | -40% (drop 202610) | +64% (drop 202608) | -6.4..-3.4 |
| L6M | DD 117.8->115.9 (+2%) d-11.5k(MDE 20.5) | DD 117.8->115.9 (+2%) d-11.0k(MDE 21.3) | -8% (drop 202609) | +41% (drop 202608) | -13.4..-5.6 |
| HOLD | DD 130.5->201.4 (-54%) d-12.1k(MDE 13.0) | DD 130.5->201.4 (-54%) d-11.9k(MDE 13.3) | -103% (drop 202601) | +2% (drop 202602) | -14.6..-9.4 |


MaxDD carrier weeks (trough week of the weekly-cumulative maxDD): F9: off 202637 / on 202613; L3M: off 202644 / on 202634; L6M: off 202637 / on 202634; HOLD: off 202608 / on 202613; PRE: off 202437 / on 202509; X': off 202347 / on 202339

# PART B - WITH the combined 12R stack lock (v1.1 convention)

## B1. Headline: lines OFF vs the five lines ON - 12R combined lock ON

| row | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| lines OFF | 27.7 (26.9) / 135.9 / -345.6 / 59.3 / 0.20 | 21.9 (64.1) / 26.3 / -26.3 / 51.2 / 0.83 | 23.4 (51.9) / 54.8 / -63.0 / 55.6 / 0.43 | 16.0 (36.0) / 57.2 / -67.0 / 46.3 / 0.28 | 30.5 (35.1) / 135.9 / -33.2 / 65.2 / 0.22 | 26.1 (21.6) / 135.9 / -418.7 / 55.6 / 0.19 | 19.1 (34.7) / 42.6 / -81.4 / 42.9 / 0.45 | 9.9 (12.7) / 126.5 / -501.9 / 39.4 / 0.08 | -4.5 (7.5) / 233.9 / -357.4 / 17.7 / -0.02 |
| five lines ON | 15.1 (20.3) / 103.9 / -347.5 / 44.7 / 0.15 | -1.7 (30.0) / 29.5 / -18.2 / 24.0 / -0.06 | 5.1 (37.0) / 58.1 / -58.1 / 39.6 / 0.09 | 2.3 (25.8) / 74.0 / -73.9 / 33.2 / 0.03 | 19.7 (25.0) / 103.9 / -69.1 / 46.4 / 0.19 | 16.3 (17.4) / 132.1 / -396.5 / 44.8 / 0.12 | 3.7 (31.1) / 96.2 / -86.0 / 38.5 / 0.04 | 4.3 (10.2) / 183.5 / -467.4 / 31.5 / 0.02 | -3.7 (7.8) / 164.1 / -329.0 / 18.4 / -0.02 |
| equal-risk mean ON | 16.5 (x1.09) | -1.8 | 5.5 | 2.5 | 21.4 | 17.7 | 4.0 | 4.6 | -4.0 |

Effect of the lines (ON minus OFF): F9: DD 135.9->103.9 (+24%) d-12.6k(MDE 15.3); L3M: DD 57.2->74.0 (-29%) d-13.7k(MDE 23.5); L6M: DD 135.9->103.9 (+24%) d-10.8k(MDE 18.6); HOLD: DD 135.9->132.1 (+3%) d-9.8k(MDE 11.6); MID: DD 42.6->96.2 (-126%) d-15.5k(MDE 27.0); PRE: DD 126.5->183.5 (-45%) d-5.6k(MDE 8.6); X': DD 233.9->164.1 (+30%) d+0.8k(MDE 7.8)

Tier columns for the five lines together: STRICT - / TOLERANT - / NOW-ONLY -.

F9 maxDD carrier week (trough): OFF 202637 (depth 135.9k); ON 202637 (103.9k).

## B2. One line at a time - 12R combined lock ON
Contribution of a line = (system with the line) - (system without it): ADD = line alone on the lines-off base; REMOVE = full package minus full-without-that-line. Cell: DD without -> with (cut %) and delta mean (paired MDE). Positive cut = the line lowers maxDD.

### ADD
| line | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | DD 135.9->128.8 (+5%) d-0.4k(MDE 2.2) | DD 26.3->27.5 (-5%) d-0.0k(MDE 2.2) | DD 54.8->52.0 (+5%) d-0.4k(MDE 4.3) | DD 57.2->58.4 (-2%) d-0.6k(MDE 3.2) | DD 135.9->128.8 (+5%) d-0.1k(MDE 2.7) | DD 135.9->128.8 (+5%) d-0.0k(MDE 1.9) | DD 42.6->43.6 (-2%) d-1.0k(MDE 2.9) | DD 126.5->117.4 (+7%) d-0.2k(MDE 1.5) | DD 233.9->230.5 (+1%) d+0.1k(MDE 0.8) | -/-/- |
| P7 | DD 135.9->122.0 (+10%) d-4.4k(MDE 9.5) | DD 26.3->28.0 (-7%) d-10.8k(MDE 24.3) | DD 54.8->46.3 (+16%) d-6.4k(MDE 14.5) | DD 57.2->64.0 (-12%) d-5.6k(MDE 11.6) | DD 135.9->122.0 (+10%) d-3.6k(MDE 11.9) | DD 135.9->122.0 (+10%) d-2.3k(MDE 7.4) | DD 42.6->39.4 (+8%) d-5.8k(MDE 14.1) | DD 126.5->176.8 (-40%) d-5.4k(MDE 6.3) | DD 233.9->232.9 (+0%) d-0.5k(MDE 5.5) | -/-/- |
| H7 | DD 135.9->135.3 (+0%) d-4.3k(MDE 5.5) | DD 26.3->26.3 (+0%) d-1.6k(MDE 3.4) | DD 54.8->55.8 (-2%) d-1.0k(MDE 3.2) | DD 57.2->61.0 (-7%) d-0.9k(MDE 2.3) | DD 135.9->135.3 (+0%) d-3.4k(MDE 3.8) | DD 135.9->135.3 (+0%) d-2.6k(MDE 6.8) | DD 42.6->61.0 (-43%) d-6.1k(MDE 15.5) | DD 126.5->124.7 (+1%) d-0.5k(MDE 6.1) | DD 233.9->233.7 (+0%) d-0.3k(MDE 3.9) | -/-/- |
| U7 | DD 135.9->145.2 (-7%) d-4.6k(MDE 5.8) | DD 26.3->20.9 (+20%) d+4.9k(MDE 12.1) | DD 54.8->58.0 (-6%) d+0.0k(MDE 9.1) | DD 57.2->55.2 (+4%) d+0.4k(MDE 6.5) | DD 135.9->145.2 (-7%) d-1.9k(MDE 4.5) | DD 135.9->145.2 (-7%) d-2.2k(MDE 7.1) | DD 42.6->63.4 (-49%) d-10.5k(MDE 15.0) | DD 126.5->95.6 (+24%) d+0.2k(MDE 3.2) | DD 233.9->242.4 (-4%) d-0.5k(MDE 4.1) | -/-/- |
| W* | DD 135.9->125.0 (+8%) d-0.6k(MDE 6.2) | DD 26.3->20.6 (+22%) d+2.4k(MDE 4.4) | DD 54.8->51.9 (+5%) d+1.2k(MDE 3.1) | DD 57.2->58.9 (-3%) d+0.5k(MDE 2.2) | DD 135.9->125.0 (+8%) d+1.7k(MDE 2.3) | DD 135.9->125.0 (+8%) d-0.4k(MDE 4.6) | DD 42.6->66.7 (-57%) d-5.8k(MDE 18.9) | DD 126.5->120.9 (+4%) d+0.3k(MDE 0.8) | DD 233.9->225.1 (+4%) d+0.3k(MDE 0.9) | -/Y/Y |

### RM
| line | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | STRICT/TOL/NOW |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | DD 130.4->103.9 (+20%) d+0.0k(MDE 3.1) | DD 29.5->29.5 (+0%) d-0.6k(MDE 1.0) | DD 49.1->58.1 (-18%) d-2.1k(MDE 5.4) | DD 67.2->74.0 (-10%) d-1.2k(MDE 3.8) | DD 130.4->103.9 (+20%) d+0.3k(MDE 4.2) | DD 130.4->132.1 (-1%) d-2.1k(MDE 6.5) | DD 92.0->96.2 (-4%) d-0.7k(MDE 3.2) | DD 171.9->183.5 (-7%) d+1.0k(MDE 2.2) | DD 180.1->164.1 (+9%) d+0.1k(MDE 1.1) | -/-/- |
| P7 | DD 123.1->103.9 (+16%) d-6.8k(MDE 11.7) | DD 16.5->29.5 (-79%) d-29.2k(MDE 54.6) | DD 56.7->58.1 (-2%) d-17.7k(MDE 31.9) | DD 61.1->74.0 (-21%) d-13.2k(MDE 23.0) | DD 123.1->103.9 (+16%) d-7.3k(MDE 14.9) | DD 123.1->132.1 (-7%) d-5.9k(MDE 10.1) | DD 71.9->96.2 (-34%) d-5.1k(MDE 17.5) | DD 125.3->183.5 (-46%) d-3.5k(MDE 6.0) | DD 142.9->164.1 (-15%) d-1.2k(MDE 3.2) | -/-/- |
| H7 | DD 98.3->103.9 (-6%) d-6.3k(MDE 9.0) | DD 18.2->29.5 (-62%) d-20.0k(MDE 51.8) | DD 43.8->58.1 (-33%) d-12.7k(MDE 28.6) | DD 67.6->74.0 (-10%) d-8.5k(MDE 20.2) | DD 98.3->103.9 (-6%) d-7.2k(MDE 10.1) | DD 98.3->132.1 (-34%) d-6.6k(MDE 7.3) | DD 45.7->96.2 (-110%) d-3.8k(MDE 17.9) | DD 186.9->183.5 (+2%) d-0.4k(MDE 4.8) | DD 203.5->164.1 (+19%) d+0.6k(MDE 2.2) | -/-/- |
| U7 | DD 88.2->103.9 (-18%) d-3.8k(MDE 8.8) | DD 23.6->29.5 (-25%) d-13.5k(MDE 58.4) | DD 40.2->58.1 (-45%) d-11.8k(MDE 30.9) | DD 69.0->74.0 (-7%) d-7.2k(MDE 21.8) | DD 82.0->103.9 (-27%) d-6.2k(MDE 10.7) | DD 124.4->132.1 (-6%) d-3.6k(MDE 7.1) | DD 88.2->96.2 (-9%) d+2.1k(MDE 13.1) | DD 165.8->183.5 (-11%) d+1.3k(MDE 2.9) | DD 186.3->164.1 (+12%) d+0.0k(MDE 2.4) | -/-/- |
| W* | DD 133.7->103.9 (+22%) d+3.2k(MDE 4.2) | DD 29.5->29.5 (+0%) d+2.5k(MDE 4.3) | DD 60.7->58.1 (+4%) d+1.2k(MDE 3.1) | DD 76.0->74.0 (+3%) d+0.7k(MDE 2.1) | DD 133.7->103.9 (+22%) d+3.9k(MDE 5.7) | DD 147.0->132.1 (+10%) d+2.3k(MDE 3.2) | DD 111.8->96.2 (+14%) d+1.3k(MDE 3.7) | DD 281.8->183.5 (+35%) d+2.3k(MDE 3.1) | DD 188.1->164.1 (+13%) d+0.5k(MDE 1.9) | Y/Y/Y |

## B3. Wildcard line by book (this lock setting, ADD on lines-off)
| cell | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| * on MV | DD 135.9->125.0 (+8%) d-0.6k(MDE 6.2) | DD 57.2->58.9 (-3%) d+0.5k(MDE 2.2) | DD 135.9->125.0 (+8%) d+1.7k(MDE 2.3) | DD 135.9->125.0 (+8%) d-0.4k(MDE 4.6) | DD 42.6->66.7 (-57%) d-5.8k(MDE 18.9) | DD 126.5->120.9 (+4%) d+0.3k(MDE 0.8) | DD 233.9->225.1 (+4%) d+0.3k(MDE 0.9) |
| * on PB | DD 135.9->135.9 (+0%) d+0.0k(MDE 0.0) | DD 57.2->57.2 (+0%) d+0.0k(MDE 0.0) | DD 135.9->135.9 (+0%) d+0.0k(MDE 0.0) | DD 135.9->135.9 (+0%) d+0.0k(MDE 0.0) | DD 42.6->42.6 (+0%) d+0.0k(MDE 0.0) | DD 126.5->126.5 (+0%) d+0.0k(MDE 0.0) | DD 233.9->233.9 (+0%) d+0.0k(MDE 0.0) |
| * on MV+PB | DD 135.9->125.0 (+8%) d-0.6k(MDE 6.2) | DD 57.2->58.9 (-3%) d+0.5k(MDE 2.2) | DD 135.9->125.0 (+8%) d+1.7k(MDE 2.3) | DD 135.9->125.0 (+8%) d-0.4k(MDE 4.6) | DD 42.6->66.7 (-57%) d-5.8k(MDE 18.9) | DD 126.5->120.9 (+4%) d+0.3k(MDE 0.8) | DD 233.9->225.1 (+4%) d+0.3k(MDE 0.9) |

Fallthrough reading of first-match (the * line also fires on K7/P7/H7/U7 when their own condition is not met), full vs the default full: F9: DD 103.9->138.3 (-33%) d+0.4k(MDE 3.1); L3M: DD 74.0->79.3 (-7%) d+0.7k(MDE 3.6); L6M: DD 103.9->138.3 (-33%) d+0.5k(MDE 4.2); HOLD: DD 132.1->148.0 (-12%) d+1.8k(MDE 5.5); PRE: DD 183.5->237.2 (-29%) d-0.2k(MDE 2.2)

## B4. Per book and per session (full minus lines-off)
Delta of the book (or session) own weekly series: mean $k/wk and maxDD of its own series off->on.

### F9
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.1 (2.8) | 51.9->48.6 |
| P7 | -8.7 (9.7) | 65.9->56.7 |
| U7 | -2.0 (4.5) | 26.1->31.0 |
| H7 | -2.9 (4.5) | 37.0->50.7 |
| M7 | +0.9 (2.6) | 41.1->23.0 |
| A6 | -0.0 (0.9) | 11.3->13.9 |
| sess asia | -7.4 (12.3) | 79.0->71.3 |
| sess london | -4.5 (7.7) | 64.1->109.2 |
| sess nyam | -0.5 (1.9) | 10.3->23.8 |
| sess nypm | -0.2 (1.1) | 21.4->29.2 |

### L6M
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.0 (3.5) | 30.7->11.6 |
| P7 | -6.7 (13.2) | 65.9->56.7 |
| U7 | -0.9 (4.8) | 26.1->23.2 |
| H7 | -4.5 (4.6) | 37.0->50.7 |
| M7 | +1.5 (2.4) | 41.1->23.0 |
| A6 | -0.3 (0.8) | 10.9->13.9 |
| sess asia | -10.5 (14.5) | 79.0->71.3 |
| sess london | +0.1 (8.5) | 64.1->65.4 |
| sess nyam | +0.2 (1.8) | 10.3->15.4 |
| sess nypm | -0.6 (1.2) | 10.9->22.8 |

### HOLD
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | +0.1 (2.3) | 54.8->48.6 |
| P7 | -6.0 (7.6) | 72.7->98.6 |
| U7 | -1.7 (3.5) | 26.1->31.0 |
| H7 | -3.1 (3.4) | 37.0->50.7 |
| M7 | +0.8 (2.0) | 41.1->24.3 |
| A6 | +0.0 (0.7) | 11.3->13.9 |
| sess asia | -6.1 (9.2) | 79.0->71.3 |
| sess london | -3.0 (6.0) | 64.1->122.3 |
| sess nyam | -0.8 (3.6) | 53.5->82.8 |
| sess nypm | +0.1 (0.9) | 29.2->29.2 |

### PRE
| book / session | delta mean (MDE) | own maxDD off->on |
|---|---|---|
| K7 | -0.1 (1.5) | 26.7->42.5 |
| P7 | -4.5 (6.4) | 91.4->208.1 |
| U7 | -0.8 (1.9) | 67.3->83.5 |
| H7 | -0.3 (2.1) | 41.1->47.0 |
| M7 | +0.2 (0.9) | 72.5->63.4 |
| A6 | -0.1 (0.5) | 16.6->14.5 |
| sess asia | -3.2 (5.7) | 66.2->68.8 |
| sess london | -1.0 (3.6) | 274.9->323.4 |
| sess nyam | -1.4 (4.0) | 85.8->108.8 |
| sess nypm | -0.1 (0.7) | 15.0->15.0 |

Book x session cells (F9 and HOLD delta mean $k/wk; only cells where the lines act):

| book|session | F9 | HOLD | PRE |
|---|---|---|---|
| K7|asia | +0.2 (1.9) | +0.0 (1.5) | -0.0 (0.8) |
| K7|london | -0.2 (1.6) | -0.3 (1.3) | -0.0 (0.6) |
| K7|nyam | +0.2 (0.9) | +0.3 (0.9) | -0.0 (0.6) |
| K7|nypm | -0.2 (1.1) | +0.1 (0.9) | -0.1 (0.7) |
| P7|asia | -3.6 (7.7) | -2.0 (6.2) | -1.8 (3.4) |
| P7|london | -4.3 (5.5) | -2.9 (4.4) | -1.5 (3.0) |
| P7|nyam | -0.8 (1.8) | -1.0 (3.3) | -1.1 (3.6) |
| U7|asia | -1.0 (3.4) | -1.1 (2.6) | -1.2 (1.3) |
| U7|london | -0.9 (2.7) | -0.6 (2.2) | +0.5 (1.4) |
| H7|asia | -3.1 (4.3) | -3.0 (3.2) | -0.0 (2.1) |
| H7|nyam | +0.2 (0.9) | -0.1 (0.8) | -0.3 (0.5) |
| M7|london | +1.0 (2.0) | +0.7 (1.5) | +0.1 (0.6) |
| M7|nyam | -0.0 (1.0) | +0.1 (1.0) | +0.0 (0.6) |
| A6|asia | -0.0 (0.9) | +0.0 (0.7) | -0.1 (0.5) |

## B7. Leave-one-week-out (ISO 2026-W38) and leave-one-month-out, five lines vs lines off 

| window | all weeks | drop W38 | LOMO min cut | LOMO max cut | LOMO d mean range |
|---|---|---|---|---|---|
| F9 | DD 135.9->103.9 (+24%) d-12.6k(MDE 15.3) | DD 135.9->108.9 (+20%) d-12.3k(MDE 15.7) | -68% (drop 202607) | +24% (drop 202602) | -15.1..-8.7 |
| L3M | DD 57.2->74.0 (-29%) d-13.7k(MDE 23.5) | DD 57.2->79.0 (-38%) d-13.0k(MDE 25.5) | -43% (drop 202608) | -29% (drop 202610) | -18.8..-7.6 |
| L6M | DD 135.9->103.9 (+24%) d-10.8k(MDE 18.6) | DD 135.9->108.9 (+20%) d-10.4k(MDE 19.2) | -29% (drop 202607) | +41% (drop 202608) | -14.2..-4.9 |
| HOLD | DD 135.9->132.1 (+3%) d-9.8k(MDE 11.6) | DD 135.9->132.1 (+3%) d-9.5k(MDE 11.8) | -78% (drop 202607) | +24% (drop 202603) | -11.3..-6.8 |


MaxDD carrier weeks (trough week of the weekly-cumulative maxDD): F9: off 202637 / on 202637; L3M: off 202637 / on 202637; L6M: off 202637 / on 202637; HOLD: off 202637 / on 202613; PRE: off 202440 / on 202512; X': off 202351 / on 202347
