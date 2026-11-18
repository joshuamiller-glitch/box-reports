# DS3 BAR SWAP B (W-SWB): P7 / H7 / A7 / O7 on every bar row

Rule: standing selection rule (CLAUDE.md, user 11-17 18:10Z/18:13Z): pick on the trailing 6 months to the newest data, trailing 3M beside it; validated by rolling walk-forward; older years tolerant (AMBER 15-30% / RED >30% worse than the live bar). FIRST PASS standalone (tape fills, raw chassis, live bracket); engine swap test is section 4.
Pick window: 2026-05-18..2026-11-13 (trailing 6M); data end 2026-11-13; refit 2026-11-18 00:49:36 UTC (loop every 30 min, bi-weekly refit rule); trials counted 42601 candidates (rows x param sets x cells), correction White RC / Hansen SPA per cell on weekly differences vs the live bar; PBO not used (rolling walk-forward instead); in-sample = trailing window, walk-forward = month-end picks from 2023-10, untouched = none frozen.

## Plain summary
- Tried: every available bar row (~490 time / activity / information / price / composite rows) as the signal clock of P7, H7, A7, O7 in three versions side by side: transplanted live settings, transplanted + the book grid refit, and bar-NATIVE rules (bars / bricks as the unit, no minute ATR); standalone on the tape with live brackets, then the exact engine with the full JL3 stack (not gated on the naked result).
- What holds / does not (trailing 6M to the data end, rolling walk-forward from 2023-10, nulls; no cell is CONFIRMED until engine controls finish):
  - P7 NY AM: live bar L6M -1939 pts; trailing-6M pick cdr_1000__NE13_50a10s 1058 pts; rolling WF 6M->1M share of months beating the live bar 0.51 (OOS 3 vs live -75 pts/mo); random-clock pool share 0.65; older years RED
  - P7 London: live bar L6M 1575 pts; trailing-6M pick wrenko_56__NC40 913 pts; rolling WF 6M->1M share of months beating the live bar 0.49 (OOS -60 vs live -18 pts/mo); random-clock pool share 0.49; older years RED
  - H7 NY AM: live bar L6M 874 pts; trailing-6M pick tm300__NH20_55e50 1513 pts; rolling WF 6M->1M share of months beating the live bar 0.41 (OOS -38 vs live 12 pts/mo); random-clock pool share 0.68; older years RED
  - O7 NY AM: live bar L6M 141 pts; trailing-6M pick kagi_56__NO930_3 1582 pts; rolling WF 6M->1M share of months beating the live bar 0.30 (OOS 4 vs live 124 pts/mo); random-clock pool share 0.35; older years RED
  - A7 Asia: live bar L6M -160 pts; trailing-6M pick tm900__A 679 pts; rolling WF 6M->1M share of months beating the live bar 0.46 (OOS 54 vs live 85 pts/mo); random-clock pool share 0.43; older years RED
  - P7 Asia: live bar L6M 1200 pts; trailing-6M pick vsess_80__NE8_30a30s 962 pts; rolling WF 6M->1M share of months beating the live bar 0.30 (OOS -33 vs live 75 pts/mo); random-clock pool share 0.49; older years RED
  - H7 Asia: live bar L6M 624 pts; trailing-6M pick cusum_10__G12_34k5 3076 pts; rolling WF 6M->1M share of months beating the live bar 0.51 (OOS 18 vs live 13 pts/mo); random-clock pool share 0.46; older years RED
- Needs in DS7: per row (native NT8 bar type or a custom BarsType with the build rule given); layers (ER ladder, ATR-skip, ThreeBar, state features, NTZ/OTE) stay on time bars in every engine test (see section 0).
- Engine: hook swb_inject2 (identity exact on P7 NY AM, P7 London, H7 NY AM, O7, 202504 and 202610); sets TL3_SWB_* queued per cell: top 5 naked (6M), top 5 naked (3M), best row per bar family, 30 random-clock controls on the primary pick; verdict = engine rows in section 4 only.
- Next: H7 / A7 native + grid stages (loop), controls, refit every 2 weeks; layers-recomputed-on-the-picked-bar version is not built.

## 0. Which inputs run on which clock (book x input x source)  [user order 19:45Z item 1]
Source: NEW = recomputed from the swapped bar series; TIME = still read from time bars (1-min / 5-min / 45-s) built from the clock; CLOCK = wall-clock rule (minutes, sessions). "Transplanted" = live parameters laid over the new bar; "native" = rule rewritten in the bar's own units.

| book | input | transplanted, live settings (sets A/B/C) and refit (G*) | native (sets N*) |
|---|---|---|---|
| P7 | trend regime: Supertrend(10, 3.0) on hl2 of 5-min buckets | A: 5-min CLOCK buckets of the new bars; B: every 5th new bar (NEW); ATR comes from the bar ranges of the new series | EMA(fast)/EMA(slow) of the NEW closes in BARS (brick / bar moving average), channel slope, or N-bar streak; no ATR |
| P7 | pullback level: EMA(20) of 1-min closes | NEW (20 bars of the new series) | NEW: EMA(fast bars) / channel mid / counter-bar count M |
| P7 | arm window 30 bars, break of the pull bar (T2) | NEW (bars) | NEW (10 / 30 bars) |
| P7 | speed / volatility measure | none | optional speed gate: bar duration EMA(5) below its trailing median (time per bar; 'spd' sets, non-time bars only) |
| P7 | 90-minute gap disarm, session / lot table, time guards | CLOCK | CLOCK |
| P7 | ThreeBar confirmation in NY AM / NY PM (45-s sub-bars), ER ladder (5-min closes), ATR-skip REG (5-min ATR14 of 1-min bars), signal-state St1Dist, NTZ / OTE lines (1-min / 15-min bars) | TIME (engine layers, unchanged by the swap) | TIME (unchanged) |
| P7 | context cut, new-evidence, trade-health cuts (loss + profit), flat lines, stack cap, day stop, profit locks | tick / L2 / seconds based (no bar input) | same |
| H7 | HMA(20), HMA(55) of close - VWAP; buckets | A: 5-min CLOCK buckets; B: every 5th new bar; C: every new bar (periods in bars) | periods in BARS (6/17 ... 45/120) and a CLOCK-MATCHED set (periods scaled to the series' median bar duration); EMA filter 50 / 200 bars |
| H7 | VWAP (day, UTC-4 anchor) | volume of the new bars (NEW) | NEW |
| H7 | slow-slope confirm, EMA200 on close | NEW (bar count) | NEW (50 / 200 bars or clock-matched) |
| H7 | slots / session guards, ER ladder, ATR-skip, state features | CLOCK / TIME | CLOCK / TIME |
| A7 | regime Supertrend(10, 3.0) 10-min; ATR14 on 5-min bars for the level; W15; T1 | A: 10-min / 5-min CLOCK buckets; B: every 10th / 5th new bar | the P7-native rules (EMA / channel / streak) in the Asia session |
| O7 | open window 09:30 (also 02:00 / 03:00 / 08:30 / 10:00 tested), drive 10 min, hi-lo of the first 5 min (20-day median), pullback window 09:40-09:44 | CLOCK windows; direction of each bar (close vs open) NEW | window start CLOCK; drive = first N bars (3/5/8/12), threshold 0.5 x median hi-lo of the first N/2 bars (20 days), pullback = first counter bar within N/2 bars |
| O7 | bracket 40 / 90 points, 16:00 time exit | points / CLOCK | points / CLOCK |

Layers that still read TIME bars in every engine test below (version "layers on time bars"): ER ladder, ATR-skip, ThreeBar confirm (P7 NY), signal-state features, NTZ / OTE lines. The version "layers recomputed on the picked bar" is NOT built yet: those five layers are hard-wired to the engine's 1-min / 5-min / 45-s series (replica sim.py on_1m / on_45s); the other layers (cuts, locks, stack cap, day stop) read no bars, so the two versions differ only in those five. Until the recomputation is coded every engine row is "layers on time bars" (stated on the row).

"With layers (fast)" score: no fast replay of the live layer stack on arbitrary-bar trades exists on the box; the exact engine with the full JL3 stack IS the with-layers score, so no row is gated on the naked result: for every weak cell the engine gets the top 5 naked (6M), the top 5 naked (3M), the best row of each bar family and 30 random-clock controls. The swap verdict of a cell is the engine-with-layers row only.


## 1. Fidelity (live time bar vs engine raw chassis S0, sig_ts within 2 s)

Pipeline bars (MBO trades table, tm60):

|           |   mean |   sum |   size |
|:----------|-------:|------:|-------:|
| ('A7', 0) | 0.9589 |   816 |    851 |
| ('H7', 0) | 0.9752 |   512 |    525 |
| ('H7', 3) | 0.9938 |   320 |    322 |
| ('O7', 3) | 0.9714 |   374 |    385 |
| ('P7', 0) | 0.9931 |  1579 |   1590 |
| ('P7', 1) | 1      |  1231 |   1231 |
| ('P7', 3) | 0.9882 |  1342 |   1358 |

Engine own 1-min bars (month cache, all 43 months):

|           |   mean |   size |
|:----------|-------:|-------:|
| ('A7', 0) | 0.9966 |   1165 |
| ('H7', 0) | 0.9898 |    684 |
| ('H7', 3) | 1      |    411 |
| ('O7', 3) | 1      |    506 |
| ('P7', 0) | 0.9991 |   2128 |
| ('P7', 1) | 1      |   1664 |
| ('P7', 3) | 1      |   1803 |

Finding: the live bar closes at the FIRST PRINT AFTER the boundary (thin Asia/London: 2-14 s late); regime / HMA / ATR buckets use the NOMINAL boundary. Remaining pipeline misses (A7 ~96%) are ts_event vs ts_recv on thin Asia / Sunday-open minutes and months missing from the bar store (O7 median history).

## 2. Book-on-bar by cell (standalone, net points per 1 lot incl. 4.84 RT and slip; $ = pts x 20 x live lots)

### P7 NY AM

Live bar row `tm60__A`: 6M -1939 pts (n 529, ulcer 1136, maxDD 2315), 3M -1857 pts. PICK (trailing 6M, pick): `cdr_1000__NE13_50a10s` 1058 pts (n 68, ulcer 39, maxDD 131); 3M-pick: `tsf_5_700__NC40` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | cdr_1000__A | 967 | 69 | 39 | -55.7 (-74.6) | 0.49 | 0.51 | RED |
| refit | cdr_1000__G20t5 | 967 | 69 | 39 | 29.9 (-74.6) | 0.59 | 0.51 | RED |
| native | cdr_1000__NE13_50a10s | 1058 | 68 | 39 | 47.0 (-74.6) | 0.54 | 0.49 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| cdr_1000__NE13_50a10s | 1058 | 68 | 39 | 131 | 665 | 5699 |
| cdr_1000__NE13_50a30s | 1041 | 69 | 39 | 131 | 665 | 5606 |
| cdr_1000__G20t5 | 967 | 69 | 39 | 134 | 625 | 5206 |
| cdr_1000__A | 967 | 69 | 39 | 134 | 625 | 5206 |
| mom_20__NC10s | 3448 | 459 | 166 | 559 | 1922 | 18566 |
| renko_40__G40k3 | 1928 | 160 | 93 | 361 | 925 | 10382 |
| trend_112__NC20 | 614 | 30 | 35 | 121 | 396 | 3306 |
| wrenko_112__NC20 | 614 | 30 | 35 | 121 | 396 | 3306 |
| swing_pct_35__NE5_20a30s | 952 | 48 | 57 | 252 | 362 | 5126 |
| swing_pct_35__NE5_20a10s | 952 | 48 | 57 | 252 | 362 | 5126 |
| vrb_10000__NC20 | 1237 | 76 | 79 | 213 | 763 | 6660 |
| tm900__NS4_1 | 591 | 30 | 38 | 150 | 192 | 3182 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 3.3 | -74.6 | 0.51 | 826 | 2066 |
| 6M->3M | 37 | 10.6 | -88.1 | 0.65 | 1620 | 5992 |
| 3M->1M | 37 | 0.9 | -74.6 | 0.62 | 410 | 2066 |
| 3M->3M | 37 | 27.6 | -88.1 | 0.68 | 637 | 5992 |
| 12M->1M | 37 | 76.1 | -74.6 | 0.62 | 582 | 2066 |
| 12M->3M | 37 | 30.9 | -88.1 | 0.49 | 1874 | 5992 |
| 6M->2w | 37 | -53.0 | 10.7 | 0.46 | 1034 | 1648 |

Nulls (same pick procedure): shift11: OOS 16.9/mo share beat 0.59; shift23: OOS 33.8/mo share beat 0.62; shift37: OOS -32.1/mo share beat 0.57; random-clock pool: OOS 64.4/mo share beat 0.65

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 4 vs -79 (n 36); +3M 45 vs -102 (n 34); +6M -95 vs -98 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 18.6 | -41.1 | -145% | -91% | -86% | GREEN |
| Y2023 | -15.0 | 77.9 | +119% | +151% | +35% | RED |
| Y2024 | -7.7 | 1.6 | +581% | -30% | -21% | RED |
| Y2025 | 16.4 | -30.5 | -154% | -90% | -87% | GREEN |
| Y2026 | 18.8 | -7.7 | -345% | -75% | -71% | GREEN |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.468, 'spa_p': 0.001, 'T': 26, 'K': 11994}

**Deliverable row**: P7 NY AM: bar today 1-minute time (live) -> proposed cdr_1000 | construction: cdr_1000 (cumulative-delta-range bar: closes when (max - min) of the running cumulative delta inside the bar >= D) | param set NE13_50a10s | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType | scaling: size x s_vol; s_vol = trailing-20-prior-trading-date median of daily volume / R0 (R0 = median of the first 60 trading dates 2023-04..06, a unit consta (new custom BarsType)

### P7 London

Live bar row `tm60__A`: 6M 1575 pts (n 559, ulcer 200, maxDD 470), 3M 450 pts. PICK (trailing 6M, pick): `wrenko_56__NC40` 913 pts (n 31, ulcer 26, maxDD 65); 3M-pick: `vnorm_400__NS6_1` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | rng_80__A | 1804 | 110 | 69 | -30.5 (-17.6) | 0.46 | 0.54 | RED |
| refit | dol_1700__G40k8 | 2050 | 125 | 62 | -48.2 (-17.6) | 0.49 | 0.54 | RED |
| native | lbrk_5_10__NC40 | 2389 | 157 | 46 | -37.2 (-17.6) | 0.57 | 0.49 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| lbrk_5_10__NC40 | 2389 | 157 | 46 | 141 | 1321 | 12865 |
| wrenko_56__NC40 | 913 | 31 | 26 | 65 | 576 | 4918 |
| trend_56__NC40 | 913 | 31 | 26 | 65 | 576 | 4918 |
| dol_1700__G40k8 | 2050 | 125 | 62 | 244 | 539 | 11041 |
| rng_80__G20k3 | 1815 | 114 | 61 | 200 | 657 | 9773 |
| cusum_80__G20k3 | 1961 | 115 | 71 | 229 | 629 | 10562 |
| rng_80__A | 1804 | 110 | 69 | 212 | 408 | 9713 |
| rng_80__G20t5 | 1804 | 110 | 69 | 212 | 408 | 9713 |
| tsf_25_40__NE5_20a10 | 1477 | 119 | 61 | 215 | 858 | 7954 |
| tsf_25_40__NE5_20a30 | 1477 | 119 | 61 | 215 | 858 | 7954 |
| renko_20__NE20_80a30s | 1287 | 85 | 54 | 192 | 982 | 6931 |
| wrenko_56__G20k3 | 949 | 54 | 40 | 105 | 293 | 5109 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -59.6 | -17.6 | 0.49 | 2163 | 1806 |
| 6M->3M | 37 | -58.5 | -18.0 | 0.54 | 4554 | 5373 |
| 3M->1M | 37 | -21.8 | -17.6 | 0.59 | 649 | 1806 |
| 3M->3M | 37 | -23.6 | -18.0 | 0.51 | 1379 | 5373 |
| 12M->1M | 37 | -21.9 | -17.6 | 0.57 | 734 | 1806 |
| 12M->3M | 37 | -13.0 | -18.0 | 0.46 | 1880 | 5373 |
| 6M->2w | 37 | -29.3 | -101.3 | 0.46 | 1088 | 2126 |

Nulls (same pick procedure): shift11: OOS -35.4/mo share beat 0.49; shift23: OOS -70.9/mo share beat 0.49; shift37: OOS -9.5/mo share beat 0.54; random-clock pool: OOS -10.4/mo share beat 0.49

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -72 vs -14 (n 36); +3M -60 vs -22 (n 34); +6M 30 vs 6 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -11.2 | 0.7 | +1779% | -41% | -47% | RED |
| Y2023 | -0.3 | 20.1 | +102% | -56% | -62% | RED |
| Y2024 | -12.7 | -32.4 | -61% | -71% | -64% | GREEN |
| Y2025 | -7.7 | -11.3 | -32% | -68% | -70% | GREEN |
| Y2026 | -21.9 | -4.6 | +372% | -64% | -60% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.975, 'spa_p': 0.442, 'T': 26, 'K': 9157}

**Deliverable row**: P7 London: bar today 1-minute time (live) -> proposed wrenko_56 | construction: wrenko_56 (Renko with wicks (BetterRenko style): classic Renko bricks whose high/low include the raw print extremes since the previous brick) | param set NC40 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (BetterRenko third-party) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

### H7 NY AM

Live bar row `tm60__A`: 6M 874 pts (n 86, ulcer 86, maxDD 245), 3M 445 pts. PICK (trailing 6M, pick): `tm300__NH20_55e50` 1513 pts (n 91, ulcer 35, maxDD 123); 3M-pick: `drb_2000__B` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | vol_6000__A | 992 | 43 | 42 | -45.8 (12.1) | 0.43 | 0.46 | RED |
| refit | cdr_250__G12_34k3 | 768 | 61 | 110 | 4.7 (55.3) | 0.53 | 0.59 | RED |
| native | tm300__NH20_55e50 | 1513 | 91 | 35 | 29.8 (12.1) | 0.57 | 0.65 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| tm300__NH20_55e50 | 1513 | 91 | 35 | 123 | 489 | 2328 |
| tm300__NHc | 1392 | 93 | 40 | 125 | 428 | 2142 |
| vol_6000__A | 992 | 43 | 42 | 135 | 452 | 1527 |
| tm300__C | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__NH20_55e200 | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__A | 1010 | 80 | 49 | 181 | 490 | 1554 |
| drb_2000__B | 1073 | 45 | 61 | 207 | 698 | 1651 |
| dib_15000__A | 786 | 55 | 48 | 135 | 386 | 1209 |
| vsess_200__A | 1071 | 88 | 66 | 172 | 440 | 1648 |
| mrenko_28__B | 852 | 46 | 56 | 132 | 373 | 1311 |
| tsf_10_60__B | 784 | 30 | 53 | 181 | 204 | 1207 |
| trb_3500__A | 710 | 49 | 49 | 167 | 443 | 1092 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -37.5 | 12.1 | 0.41 | 1108 | 668 |
| 6M->3M | 37 | 1.5 | 4.9 | 0.43 | 1516 | 2222 |
| 3M->1M | 37 | 9.4 | 12.1 | 0.54 | 522 | 668 |
| 3M->3M | 37 | 9.9 | 4.9 | 0.62 | 872 | 2222 |
| 12M->1M | 37 | -26.4 | 12.1 | 0.46 | 1057 | 668 |
| 12M->3M | 37 | 7.8 | 4.9 | 0.46 | 1244 | 2222 |
| 6M->2w | 37 | -104.7 | 4.3 | 0.46 | 1396 | 458 |

Nulls (same pick procedure): shift11: OOS 15.4/mo share beat 0.54; shift23: OOS 12.6/mo share beat 0.57; shift37: OOS 2.4/mo share beat 0.59; random-clock pool: OOS 67.4/mo share beat 0.68

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -39 vs 12 (n 36); +3M 19 vs 10 (n 34); +6M 63 vs 27 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -2.4 | -7.5 | -68% | +7% | +15% | GREEN |
| Y2023 | 0.3 | 1.9 | +84% | +1% | -21% | RED |
| Y2024 | -21.4 | -27.5 | -22% | -19% | -17% | GREEN |
| Y2025 | 20.0 | 14.1 | -42% | +13% | +6% | GREEN |
| Y2026 | 20.9 | 4.8 | -336% | -3% | +4% | GREEN |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 1.0, 'spa_p': 0.864, 'T': 26, 'K': 707}

**Deliverable row**: H7 NY AM: bar today 1-minute time (live) -> proposed tm300 | construction: 5-minute time bar | param set NH20_55e50 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: native NT8 Minute bar (OnBarClose at the first print after the boundary) (native)

### O7 NY AM

Live bar row `tm60__A`: 6M 141 pts (n 65, ulcer 232, maxDD 445), 3M -3 pts. PICK (trailing 6M, pick): `kagi_56__NO930_3` 1582 pts (n 87, ulcer 81, maxDD 244); 3M-pick: `vrb_400__NO1000_3` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | pasl_20__A | 772 | 42 | 70 | 55.2 (123.9) | 0.30 | 0.32 | RED |
| refit | cdr_400__G1000_10 | 422 | 32 | 92 | 17.0 (97.8) | 0.33 | 0.27 | RED |
| native | dchg_56__NO930_3 | 1582 | 87 | 81 | -29.5 (123.9) | 0.27 | 0.30 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| kagi_56__NO930_3 | 1582 | 87 | 81 | 244 | 989 | 2433 |
| dchg_56__NO930_3 | 1582 | 87 | 81 | 244 | 989 | 2433 |
| vib_15000__NO930_8 | 1432 | 61 | 76 | 243 | 802 | 2204 |
| tm420__NO930_12 | 720 | 31 | 40 | 122 | 86 | 1108 |
| kagi_40__NO830_12 | 1141 | 53 | 70 | 163 | 435 | 1755 |
| dchg_40__NO830_12 | 1141 | 53 | 70 | 163 | 435 | 1755 |
| swing_pct_5__NO1000_8 | 1214 | 80 | 76 | 202 | 311 | 1867 |
| renko_28__NO1000_5 | 1091 | 47 | 71 | 203 | 492 | 1679 |
| vnorm_400__NO930_12 | 891 | 68 | 58 | 162 | 339 | 1370 |
| tsf_10_400__NO930_5 | 627 | 37 | 43 | 122 | 315 | 964 |
| tm10__NO1000_3 | 878 | 33 | 60 | 162 | 223 | 1350 |
| vnorm_40__NO1000_8 | 919 | 35 | 67 | 203 | 286 | 1414 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 4.5 | 123.9 | 0.30 | 500 | 157 |
| 6M->3M | 37 | 33.0 | 125.9 | 0.24 | 373 | 202 |
| 3M->1M | 37 | 29.0 | 123.9 | 0.32 | 469 | 157 |
| 3M->3M | 37 | 25.2 | 125.9 | 0.27 | 776 | 202 |
| 12M->1M | 37 | -1.1 | 123.9 | 0.38 | 280 | 157 |
| 12M->3M | 37 | 19.0 | 125.9 | 0.16 | 335 | 202 |
| 6M->2w | 37 | -12.4 | 125.7 | 0.32 | 473 | 146 |

Nulls (same pick procedure): shift11: OOS 27.3/mo share beat 0.32; shift23: OOS 28.9/mo share beat 0.32; shift37: OOS -3.2/mo share beat 0.32; random-clock pool: OOS 25.5/mo share beat 0.35

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 0 vs 122 (n 36); +3M 60 vs 141 (n 34); +6M 61 vs 138 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 34.9 | 45.5 | +23% | +115% | +95% | RED |
| Y2023 | 7.8 | -13.3 | -159% | -32% | -5% | GREEN |
| Y2024 | 8.8 | 40.2 | +78% | +206% | +90% | RED |
| Y2025 | 49.4 | 26.6 | -86% | -13% | +39% | RED |
| Y2026 | -18.3 | 58.8 | +131% | +326% | +204% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.522, 'spa_p': 0.285, 'T': 26, 'K': 2406}

**Deliverable row**: O7 NY AM: bar today 1-minute time (live) -> proposed kagi_56 | construction: kagi_56 (Kagi line segments: reversal amount N ticks; bar per segment between reversals (shoulder/waist thickness change recorded by the segment extent)) | param set NO930_3 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: native Kagi | scaling: size x s_rng (same, daily high-low range in points) (native)

### A7 Asia (phase 2)

Live bar row `tm60__A`: 6M -160 pts (n 367, ulcer 475, maxDD 1039), 3M -323 pts. PICK (trailing 6M, pick): `tm900__A` 679 pts (n 31, ulcer 30, maxDD 106); 3M-pick: `tsf_5_200__B` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | tm900__A | 679 | 31 | 30 | 68.6 (84.8) | 0.51 | 0.43 | RED |
| refit | cdr_400__Gt10k2 | 420 | 30 | 48 | -60.6 (63.7) | 0.18 | 0.12 | RED |
| native | tm300__NC20 | 1872 | 329 | 242 | 47.0 (84.8) | 0.49 | 0.41 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| tm900__A | 679 | 31 | 30 | 106 | 182 | 1045 |
| pasl_28__A | 976 | 101 | 57 | 123 | 716 | 1501 |
| tm300__A | 856 | 55 | 62 | 154 | 670 | 1317 |
| pasl_40__B | 678 | 55 | 49 | 125 | 346 | 1043 |
| renko_40__B | 801 | 62 | 59 | 182 | 325 | 1233 |
| tsf_5_200__B | 825 | 45 | 64 | 284 | 565 | 1269 |
| drb_2000__A | 651 | 41 | 57 | 122 | 363 | 1001 |
| lbrk_3_40__B | 539 | 39 | 54 | 182 | 370 | 829 |
| mrenko_40__B | 662 | 81 | 66 | 189 | 211 | 1018 |
| renko_14__A | 1483 | 353 | 161 | 410 | 1063 | 2282 |
| tsf_5_200__A | 954 | 59 | 108 | 222 | 837 | 1468 |
| lbrk_4_10__B | 1224 | 222 | 141 | 361 | 622 | 1883 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 54.4 | 84.8 | 0.46 | 162 | 299 |
| 6M->3M | 37 | 39.1 | 90.4 | 0.32 | 336 | 571 |
| 3M->1M | 37 | 56.4 | 84.8 | 0.51 | 195 | 299 |
| 3M->3M | 37 | 41.8 | 90.4 | 0.38 | 618 | 571 |
| 12M->1M | 37 | 77.1 | 84.8 | 0.51 | 144 | 299 |
| 12M->3M | 37 | 66.2 | 90.4 | 0.35 | 191 | 571 |
| 6M->2w | 37 | 34.6 | 114.1 | 0.38 | 210 | 211 |

Nulls (same pick procedure): shift11: OOS 72.2/mo share beat 0.49; shift23: OOS 29.0/mo share beat 0.51; shift37: OOS 19.1/mo share beat 0.43; random-clock pool: OOS 66.0/mo share beat 0.43

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 54 vs 89 (n 36); +3M 50 vs 94 (n 34); +6M 110 vs 87 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 23.3 | 31.5 | +26% | -91% | -88% | AMBER |
| Y2023 | 1.9 | 4.4 | +58% | -47% | -40% | RED |
| Y2024 | 15.6 | 26.1 | +40% | -79% | -75% | RED |
| Y2025 | 3.2 | 20.8 | +85% | -20% | -46% | RED |
| Y2026 | 39.7 | 55.3 | +28% | -86% | -87% | AMBER |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.052, 'spa_p': 0.139, 'T': 26, 'K': 516}

**Deliverable row**: A7 Asia: bar today 1-minute time (live) -> proposed tm900 | construction: 15-minute time bar | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: native NT8 Minute bar (OnBarClose at the first print after the boundary) (native)

### P7 Asia (phase 2)

Live bar row `tm60__A`: 6M 1200 pts (n 669, ulcer 358, maxDD 1021), 3M 914 pts. PICK (trailing 6M, pick): `vsess_80__NE8_30a30s` 962 pts (n 35, ulcer 20, maxDD 62); 3M-pick: `dchg_40__G40k3` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | renko_40__A | 908 | 100 | 79 | 7.1 (75.0) | 0.46 | 0.35 | RED |
| refit | dol_1700__G40k3 | 1941 | 168 | 71 | -6.4 (75.0) | 0.38 | 0.38 | RED |
| native | vsess_80__NE8_30a10s | 962 | 35 | 20 | -13.6 (75.0) | 0.41 | 0.43 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| vsess_80__NE8_30a30s | 962 | 35 | 20 | 62 | 301 | 8876 |
| vsess_80__NE8_30a10s | 962 | 35 | 20 | 62 | 301 | 8876 |
| dib_10000__NS3_2s | 754 | 32 | 21 | 64 | 316 | 6962 |
| dlt_70__NC10 | 3811 | 584 | 130 | 417 | 2174 | 35180 |
| dol_1700__G40k3 | 1941 | 168 | 71 | 215 | 1064 | 17914 |
| tm420__G10k5 | 2738 | 310 | 123 | 332 | 1447 | 25274 |
| swing_pct_8__G40k3 | 1914 | 161 | 86 | 269 | 961 | 17671 |
| vib_10000__NS4_1s | 773 | 34 | 34 | 127 | 316 | 7132 |
| dlt_70__G10t5 | 2850 | 520 | 141 | 336 | 1477 | 26307 |
| pasl_40__NC40 | 933 | 44 | 46 | 124 | 452 | 8610 |
| dol_1700__G10k3 | 1975 | 259 | 101 | 304 | 1297 | 18229 |
| tm1800__NC10 | 1417 | 110 | 74 | 304 | 744 | 13079 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -32.8 | 75.0 | 0.30 | 972 | 416 |
| 6M->3M | 37 | -26.7 | 87.6 | 0.16 | 2300 | 564 |
| 3M->1M | 37 | -43.6 | 75.0 | 0.35 | 1145 | 416 |
| 3M->3M | 37 | -9.4 | 87.6 | 0.22 | 1492 | 564 |
| 12M->1M | 37 | -43.0 | 75.0 | 0.38 | 1394 | 416 |
| 12M->3M | 37 | -14.2 | 87.6 | 0.24 | 2081 | 564 |
| 6M->2w | 37 | 12.1 | 126.4 | 0.41 | 305 | 244 |

Nulls (same pick procedure): shift11: OOS -19.0/mo share beat 0.35; shift23: OOS -55.2/mo share beat 0.38; shift37: OOS -2.1/mo share beat 0.38; random-clock pool: OOS 43.4/mo share beat 0.49

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -37 vs 81 (n 36); +3M -14 vs 105 (n 34); +6M -47 vs 121 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 15.7 | 10.6 | -49% | -71% | -61% | GREEN |
| Y2023 | -5.5 | -18.4 | -70% | -65% | -70% | GREEN |
| Y2024 | 9.5 | 16.5 | +42% | -80% | -78% | RED |
| Y2025 | 13.7 | 21.5 | +36% | -53% | -57% | RED |
| Y2026 | 12.8 | 11.5 | -11% | -65% | -61% | GREEN |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.892, 'spa_p': 0.876, 'T': 26, 'K': 8849}

**Deliverable row**: P7 Asia: bar today 1-minute time (live) -> proposed vsess_80 | construction: vsess_80 (volume-clock / session-relative: N equal-volume bars per session; bar volume = trailing median session volume / N (a session with a typical volume curve gets N bars; NY open fast, lunch slow in clock ) | param set NE8_30a30s | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (volume threshold set at session start from a trailing table) | scaling: N bars per session; bar volume = trailing-20-date median volume of that session code / N (new custom BarsType)

### H7 Asia (phase 2)

Live bar row `tm60__A`: 6M 624 pts (n 138, ulcer 156, maxDD 360), 3M 24 pts. PICK (trailing 6M, pick): `cusum_10__G12_34k5` 3076 pts (n 384, ulcer 118, maxDD 372); 3M-pick: `lbrk_5_20__A` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | tib_1200__B | 1604 | 141 | 72 | 8.6 (13.1) | 0.54 | 0.62 | RED |
| refit | cusum_10__G12_34k5 | 3076 | 384 | 118 | 46.6 (-23.5) | 0.53 | 0.53 | RED |
| native | tm300__NH30_80e200 | 991 | 113 | 141 | 52.2 (13.1) | 0.49 | 0.54 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| cusum_10__G12_34k5 | 3076 | 384 | 118 | 372 | 1465 | 16564 |
| tib_1200__B | 1604 | 141 | 72 | 245 | 757 | 8638 |
| cusum_10__G12_34t5 | 1807 | 172 | 115 | 334 | 780 | 9730 |
| urenko_28__C | 1507 | 149 | 116 | 311 | 929 | 8112 |
| dlt_70__A | 848 | 86 | 69 | 148 | 537 | 4567 |
| trb_400__C | 2187 | 357 | 183 | 468 | 994 | 11776 |
| tm240__C | 1500 | 168 | 131 | 426 | 503 | 8076 |
| tsf_2_400__C | 1512 | 136 | 135 | 369 | 229 | 8143 |
| drb_400__C | 1880 | 356 | 168 | 409 | 1206 | 10124 |
| vib_700__A | 1127 | 133 | 102 | 249 | 165 | 6066 |
| dib_400__A | 1230 | 136 | 113 | 301 | 321 | 6624 |
| vnorm_400__C | 1409 | 171 | 129 | 326 | 890 | 7585 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 18.0 | 13.1 | 0.51 | 842 | 552 |
| 6M->3M | 37 | 3.8 | 17.7 | 0.51 | 1849 | 1363 |
| 3M->1M | 37 | -2.0 | 13.1 | 0.49 | 613 | 552 |
| 3M->3M | 37 | 3.3 | 17.7 | 0.43 | 1316 | 1363 |
| 12M->1M | 37 | -20.9 | 13.1 | 0.41 | 1197 | 552 |
| 12M->3M | 37 | -30.2 | 17.7 | 0.41 | 4313 | 1363 |
| 6M->2w | 37 | 40.3 | 47.2 | 0.59 | 538 | 254 |

Nulls (same pick procedure): shift11: OOS 25.8/mo share beat 0.57; shift23: OOS 1.6/mo share beat 0.57; shift37: OOS 29.8/mo share beat 0.59; random-clock pool: OOS -4.0/mo share beat 0.46

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 4 vs 14 (n 36); +3M 6 vs 18 (n 34); +6M 39 vs 6 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -4.5 | -18.2 | -75% | +12% | +21% | AMBER |
| Y2023 | 0.0 | 7.0 | +100% | -100% | -100% | THIN(n=0) |
| Y2024 | 0.0 | 17.0 | +100% | -100% | -100% | THIN(n=0) |
| Y2025 | -19.7 | -9.1 | +118% | +0% | +41% | RED |
| Y2026 | 40.9 | -23.7 | -272% | +37% | +68% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.369, 'spa_p': 0.057, 'T': 26, 'K': 582}

**Deliverable row**: H7 Asia: bar today 1-minute time (live) -> proposed cusum_10 | construction: cusum_10 (CUSUM-filter events (Lopez de Prado): S+ = max(0,S+ + dp), S- = min(0,S- + dp) on print price changes; event when S+ > h or S- < -h, then reset; h = k x trailing sigma-scale (ticks)) | param set G12_34k5 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (event-driven) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

## 4. Engine swap test (hook swb_inject on JL3; same book object, native entries in the swapped session suppressed, bar signals injected)

### Identity (live 1-minute bar signals through the hook vs JL3, trade for trade; key = book, side, entry second, lots)

| set | month | JL3 trades | swap trades | identical | JL3 net | swap net |
|---|---|---:|---:|---:|---:|---:|
| TL3_SWB_ID2_H73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID2_H73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID2_O73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID2_O73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID2_P71 | 202504 | 637 | 634 | 632 | 41239.76 | 38913.48 |
| TL3_SWB_ID2_P71 | 202610 | 691 | 697 | 683 | 37159.82 | 37534.42 |
| TL3_SWB_ID2_P73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID2_P73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID3_A70 | 202504 | 637 | 637 | 635 | 41239.76 | 39066.26 |
| TL3_SWB_ID3_A70 | 202610 | 691 | 691 | 685 | 37159.82 | 36528.82 |
| TL3_SWB_ID3_H70 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID3_H70 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID3_H73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID3_H73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID3_P70 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID3_P70 | 202610 | 691 | 690 | 688 | 37159.82 | 28687.82 |
| TL3_SWB_ID3_P71 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID3_P71 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID3_P73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID3_P73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID_H73 | 202504 | 637 | 637 | 637 | 41239.76 | 41309.76 |
| TL3_SWB_ID_H73 | 202610 | 691 | 691 | 691 | 37159.82 | 37334.82 |
| TL3_SWB_ID_O73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID_O73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID_P71 | 202504 | 637 | 634 | 632 | 41239.76 | 38913.48 |
| TL3_SWB_ID_P71 | 202610 | 691 | 697 | 683 | 37159.82 | 37534.42 |
| TL3_SWB_ID_P73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID_P73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |

JL3 reference numbers: 202610 691 trades / 37,159.82; 202504 637 / 41,239.76.

### TL3_SWB_P73_8b6413 (BEST-AVAILABLE-NOT-PROVEN | row cdr_1000 set NE13_50a30s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10539 | -4.5% | 31109 | 29254 | -15728 | -15100 | 16098 | 15476 | 1981/1954 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18444 | -4.5% | 54441 | 51195 | -27524 | -26424 | 28172 | 27083 | 1981/1954 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9328 | -2.9% | 31109 | 29254 | -15728 | -15100 | 18755 | 18435 | 4292/4256 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16325 | -2.9% | 54441 | 51195 | -27524 | -26424 | 32822 | 32261 | 4292/4256 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 298886; U7 59410 -> 59410

### TL3_SWB_P73_d6c62d (BEST-AVAILABLE-NOT-PROVEN | row cdr_1000 set NE13_50a10s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10539 | -4.5% | 31109 | 29254 | -15728 | -15100 | 16098 | 15476 | 1981/1954 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18444 | -4.5% | 54441 | 51195 | -27524 | -26424 | 28172 | 27083 | 1981/1954 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9328 | -2.9% | 31109 | 29254 | -15728 | -15100 | 18755 | 18435 | 4292/4256 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16325 | -2.9% | 54441 | 51195 | -27524 | -26424 | 32822 | 32261 | 4292/4256 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 298886; U7 59410 -> 59410

### Random-clock engine controls (same book / rules / bar count per session as the pick row, persistent draws seeds 101-130; L6M, $4.84 base lots; valid = all 6 months done)

| cell | pick set | valid controls | pick ulcer change | controls ulcer change median [min, max] | share of controls with a better (lower) ulcer change than the pick | pick mean/wk | controls mean/wk median |
|---|---|---:|---:|---|---:|---:|---:|
(no cell has 30 finished L6M controls yet)

