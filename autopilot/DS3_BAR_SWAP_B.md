# DS3 BAR SWAP B (W-SWB): P7 / H7 / A7 / O7 on every bar row

Rule: standing selection rule (CLAUDE.md, user 11-17 18:10Z/18:13Z): pick on the trailing 6 months to the newest data, trailing 3M beside it; validated by rolling walk-forward; older years tolerant (AMBER 15-30% / RED >30% worse than the live bar). FIRST PASS standalone (tape fills, raw chassis, live bracket); engine swap test is section 4.
Pick window: 2026-05-18..2026-11-13 (trailing 6M); data end 2026-11-13; refit 2026-11-18 03:48:56 UTC (loop every 30 min, bi-weekly refit rule); trials counted 58101 candidates (rows x param sets x cells), correction White RC / Hansen SPA per cell on weekly differences vs the live bar; PBO not used (rolling walk-forward instead); in-sample = trailing window, walk-forward = month-end picks from 2023-10, untouched = none frozen.

## Plain summary
- Tried: every available bar row (~490 time / activity / information / price / composite rows) as the signal clock of P7, H7, A7, O7 in three versions side by side: transplanted live settings, transplanted + the book grid refit, and bar-NATIVE rules (bars / bricks as the unit, no minute ATR); standalone on the tape with live brackets, then the exact engine with the full JL3 stack (not gated on the naked result).
- What holds / does not (trailing 6M to the data end, rolling walk-forward from 2023-10, nulls; no cell is CONFIRMED until engine controls finish):
  - P7 NY AM: live bar L6M -1939 pts; trailing-6M pick cdr_1000__NE13_50a10s 1058 pts; rolling WF 6M->1M share of months beating the live bar 0.51 (OOS 3 vs live -75 pts/mo); random-clock pool share 0.65; older years RED
  - P7 London: live bar L6M 1575 pts; trailing-6M pick trend_56__NC40 913 pts; rolling WF 6M->1M share of months beating the live bar 0.49 (OOS -60 vs live -18 pts/mo); random-clock pool share 0.46; older years RED
  - H7 NY AM: live bar L6M 874 pts; trailing-6M pick tm300__NH20_55e50 1513 pts; rolling WF 6M->1M share of months beating the live bar 0.43 (OOS -11 vs live 12 pts/mo); random-clock pool share 0.65; older years RED
  - O7 NY AM: live bar L6M 141 pts; trailing-6M pick kagi_56__NO930_3 1582 pts; rolling WF 6M->1M share of months beating the live bar 0.30 (OOS 4 vs live 124 pts/mo); random-clock pool share 0.35; older years RED
  - A7 Asia: live bar L6M -160 pts; trailing-6M pick tm900__A 679 pts; rolling WF 6M->1M share of months beating the live bar 0.46 (OOS 54 vs live 85 pts/mo); random-clock pool share 0.43; older years RED
  - P7 Asia: live bar L6M 1200 pts; trailing-6M pick vsess_80__NE8_30a10s 962 pts; rolling WF 6M->1M share of months beating the live bar 0.30 (OOS -33 vs live 75 pts/mo); random-clock pool share 0.49; older years RED
  - H7 Asia: live bar L6M 624 pts; trailing-6M pick swing_pct_12__NH9_26e50 2041 pts; rolling WF 6M->1M share of months beating the live bar 0.57 (OOS 48 vs live 13 pts/mo); random-clock pool share 0.57; older years RED
- Needs in DS7: per row (native NT8 bar type or a custom BarsType with the build rule given); layers (ER ladder, ATR-skip, ThreeBar, state features, NTZ/OTE) stay on time bars in every engine test (see section 0).
- Engine: hook identity (live 1-min bar through the hook = JL3 trade for trade): P7 NY AM and O7 exact on 202504 and 202610 (hook v1); P7 London and H7 NY AM exact on 202504 with hook v2 (swb_inject2; 202610 and the other cells in section 4 as they land); sets TL3_SWB_* queued per cell: top 5 naked (6M), top 5 naked (3M), best row per bar family, 30 random-clock controls on the primary pick; verdict = engine rows in section 4 only.
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
| refit | cdr_1000__G20t5 | 967 | 69 | 39 | 23.9 (-74.6) | 0.59 | 0.54 | RED |
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
| 3M->1M | 37 | -4.2 | -74.6 | 0.59 | 441 | 2066 |
| 3M->3M | 37 | 32.8 | -88.1 | 0.70 | 561 | 5992 |
| 12M->1M | 37 | 69.2 | -74.6 | 0.62 | 637 | 2066 |
| 12M->3M | 37 | 11.0 | -88.1 | 0.43 | 2557 | 5992 |
| 6M->2w | 37 | -53.0 | 10.7 | 0.46 | 1034 | 1648 |

Nulls (same pick procedure): shift11: OOS 12.9/mo share beat 0.59; shift23: OOS 29.9/mo share beat 0.59; shift37: OOS -28.0/mo share beat 0.59; random-clock pool: OOS 65.5/mo share beat 0.65

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 4 vs -79 (n 36); +3M 45 vs -102 (n 34); +6M -95 vs -98 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 18.6 | -41.1 | -145% | -91% | -86% | GREEN |
| Y2023 | -15.0 | 77.9 | +119% | +151% | +35% | RED |
| Y2024 | -7.7 | 1.6 | +581% | -30% | -21% | RED |
| Y2025 | 16.4 | -30.5 | -154% | -90% | -87% | GREEN |
| Y2026 | 18.8 | -7.7 | -345% | -75% | -71% | GREEN |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.473, 'spa_p': 0.001, 'T': 26, 'K': 12388}

**Deliverable row**: P7 NY AM: bar today 1-minute time (live) -> proposed cdr_1000 | construction: cdr_1000 (cumulative-delta-range bar: closes when (max - min) of the running cumulative delta inside the bar >= D) | param set NE13_50a10s | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType | scaling: size x s_vol; s_vol = trailing-20-prior-trading-date median of daily volume / R0 (R0 = median of the first 60 trading dates 2023-04..06, a unit consta (new custom BarsType)

### P7 London

Live bar row `tm60__A`: 6M 1575 pts (n 559, ulcer 200, maxDD 470), 3M 450 pts. PICK (trailing 6M, pick): `trend_56__NC40` 913 pts (n 31, ulcer 26, maxDD 65); 3M-pick: `vnorm_400__NS6_1` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | rng_80__A | 1804 | 110 | 69 | -30.5 (-17.6) | 0.46 | 0.54 | RED |
| refit | dol_1700__G40k8 | 2050 | 125 | 62 | -62.7 (-17.6) | 0.46 | 0.54 | RED |
| native | lbrk_5_10__NC40 | 2389 | 157 | 46 | -37.2 (-17.6) | 0.57 | 0.49 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| lbrk_5_10__NC40 | 2389 | 157 | 46 | 141 | 1321 | 12865 |
| trend_56__NC40 | 913 | 31 | 26 | 65 | 576 | 4918 |
| wrenko_56__NC40 | 913 | 31 | 26 | 65 | 576 | 4918 |
| dol_1700__G40k8 | 2050 | 125 | 62 | 244 | 539 | 11041 |
| rng_80__G20k3 | 1815 | 114 | 61 | 200 | 657 | 9773 |
| cusum_80__G20k3 | 1961 | 115 | 71 | 229 | 629 | 10562 |
| rng_80__A | 1804 | 110 | 69 | 212 | 408 | 9713 |
| rng_80__G20t5 | 1804 | 110 | 69 | 212 | 408 | 9713 |
| tsf_25_40__NE5_20a30 | 1477 | 119 | 61 | 215 | 858 | 7954 |
| tsf_25_40__NE5_20a10 | 1477 | 119 | 61 | 215 | 858 | 7954 |
| renko_20__NE20_80a30s | 1287 | 85 | 54 | 192 | 982 | 6931 |
| trend_56__G20k3 | 949 | 54 | 40 | 105 | 293 | 5109 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -59.6 | -17.6 | 0.49 | 2163 | 1806 |
| 6M->3M | 37 | -58.5 | -18.0 | 0.54 | 4554 | 5373 |
| 3M->1M | 37 | -16.4 | -17.6 | 0.62 | 489 | 1806 |
| 3M->3M | 37 | -27.3 | -18.0 | 0.51 | 1686 | 5373 |
| 12M->1M | 37 | -11.9 | -17.6 | 0.59 | 711 | 1806 |
| 12M->3M | 37 | -15.7 | -18.0 | 0.46 | 2342 | 5373 |
| 6M->2w | 37 | -29.3 | -101.3 | 0.46 | 1088 | 2126 |

Nulls (same pick procedure): shift11: OOS -29.7/mo share beat 0.49; shift23: OOS -70.9/mo share beat 0.49; shift37: OOS -10.8/mo share beat 0.54; random-clock pool: OOS 0.1/mo share beat 0.46

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -72 vs -14 (n 36); +3M -60 vs -22 (n 34); +6M 30 vs 6 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -11.2 | 0.7 | +1779% | -41% | -47% | RED |
| Y2023 | -0.3 | 20.1 | +102% | -56% | -62% | RED |
| Y2024 | -12.7 | -32.4 | -61% | -71% | -64% | GREEN |
| Y2025 | -7.7 | -11.3 | -32% | -68% | -70% | GREEN |
| Y2026 | -21.9 | -4.6 | +372% | -64% | -60% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.974, 'spa_p': 0.434, 'T': 26, 'K': 9419}

**Deliverable row**: P7 London: bar today 1-minute time (live) -> proposed trend_56 | construction: trend_56 (TrendBars (stated definition): gapless bars; trend bar closes at +N ticks beyond prior close in the trend direction; reversal bar opens at prior close and closes 2N against; wicks = raw print extremes) | param set NC40 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (NT8 TrendBars-style) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

### H7 NY AM

Live bar row `tm60__A`: 6M 874 pts (n 86, ulcer 86, maxDD 245), 3M 445 pts. PICK (trailing 6M, pick): `tm300__NH20_55e50` 1513 pts (n 91, ulcer 35, maxDD 123); 3M-pick: `drb_2000__B` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | vol_6000__A | 992 | 43 | 42 | -45.8 (12.1) | 0.43 | 0.46 | RED |
| refit | dib_25000__G12_34k3 | 1656 | 83 | 61 | 79.8 (12.1) | 0.59 | 0.65 | RED |
| native | tm300__NH20_55e50 | 1513 | 91 | 35 | -13.6 (12.1) | 0.41 | 0.59 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| tm300__NH20_55e50 | 1513 | 91 | 35 | 123 | 489 | 2328 |
| tm300__NHc | 1392 | 93 | 40 | 125 | 428 | 2142 |
| dib_25000__G12_34k3 | 1656 | 83 | 61 | 168 | 755 | 2548 |
| dib_70000__G12_34k3 | 865 | 30 | 35 | 100 | 428 | 1331 |
| vol_6000__G20_55t5 | 992 | 43 | 42 | 135 | 452 | 1527 |
| vol_6000__A | 992 | 43 | 42 | 135 | 452 | 1527 |
| tm300__G20_55k1 | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__G20_55t5 | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__A | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__C | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__NH20_55e200 | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm180__G12_34k3 | 1330 | 71 | 68 | 182 | 310 | 2045 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -11.1 | 12.1 | 0.43 | 749 | 668 |
| 6M->3M | 37 | 13.8 | 4.9 | 0.62 | 1578 | 2222 |
| 3M->1M | 37 | -28.4 | 12.1 | 0.46 | 863 | 668 |
| 3M->3M | 37 | -17.5 | 4.9 | 0.57 | 1452 | 2222 |
| 12M->1M | 37 | -52.8 | 12.1 | 0.43 | 1708 | 668 |
| 12M->3M | 37 | -51.5 | 4.9 | 0.38 | 3655 | 2222 |
| 6M->2w | 37 | 44.6 | 4.3 | 0.54 | 468 | 458 |

Nulls (same pick procedure): shift11: OOS -31.1/mo share beat 0.57; shift23: OOS 29.7/mo share beat 0.59; shift37: OOS -13.5/mo share beat 0.57; random-clock pool: OOS 49.1/mo share beat 0.65

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -13 vs 12 (n 36); +3M 13 vs 10 (n 34); +6M 7 vs 27 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -2.4 | -7.5 | -68% | +7% | +15% | GREEN |
| Y2023 | 0.3 | 1.9 | +84% | +1% | -21% | RED |
| Y2024 | -21.4 | -27.5 | -22% | -19% | -17% | GREEN |
| Y2025 | 20.0 | 14.1 | -42% | +13% | +6% | GREEN |
| Y2026 | 20.9 | 4.8 | -336% | -3% | +4% | GREEN |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.98, 'spa_p': 0.965, 'T': 26, 'K': 6575}

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

Live bar row `tm60__A`: 6M 1200 pts (n 669, ulcer 358, maxDD 1021), 3M 914 pts. PICK (trailing 6M, pick): `vsess_80__NE8_30a10s` 962 pts (n 35, ulcer 20, maxDD 62); 3M-pick: `dchg_40__G40k3` (DISAGREES).
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
| vsess_80__NE8_30a10s | 962 | 35 | 20 | 62 | 301 | 8876 |
| vsess_80__NE8_30a30s | 962 | 35 | 20 | 62 | 301 | 8876 |
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
| 12M->1M | 37 | -40.2 | 75.0 | 0.38 | 1332 | 416 |
| 12M->3M | 37 | -12.6 | 87.6 | 0.24 | 1988 | 564 |
| 6M->2w | 37 | 12.1 | 126.4 | 0.41 | 305 | 244 |

Nulls (same pick procedure): shift11: OOS -19.0/mo share beat 0.35; shift23: OOS -55.2/mo share beat 0.38; shift37: OOS -2.1/mo share beat 0.38; random-clock pool: OOS 34.2/mo share beat 0.49

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -37 vs 81 (n 36); +3M -14 vs 105 (n 34); +6M -47 vs 121 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 14.6 | 10.6 | -38% | -78% | -73% | GREEN |
| Y2023 | -4.9 | -18.4 | -73% | -68% | -72% | GREEN |
| Y2024 | 9.4 | 16.5 | +43% | -80% | -79% | RED |
| Y2025 | 14.8 | 21.5 | +31% | -57% | -57% | RED |
| Y2026 | 9.6 | 11.5 | +17% | -75% | -73% | AMBER |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.894, 'spa_p': 0.878, 'T': 26, 'K': 9123}

**Deliverable row**: P7 Asia: bar today 1-minute time (live) -> proposed vsess_80 | construction: vsess_80 (volume-clock / session-relative: N equal-volume bars per session; bar volume = trailing median session volume / N (a session with a typical volume curve gets N bars; NY open fast, lunch slow in clock ) | param set NE8_30a10s | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (volume threshold set at session start from a trailing table) | scaling: N bars per session; bar volume = trailing-20-date median volume of that session code / N (new custom BarsType)

### H7 Asia (phase 2)

Live bar row `tm60__A`: 6M 624 pts (n 138, ulcer 156, maxDD 360), 3M 24 pts. PICK (trailing 6M, pick): `swing_pct_12__NH9_26e50` 2041 pts (n 105, ulcer 45, maxDD 126); 3M-pick: `cusum_14__G30_80k3` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | tib_1200__B | 1604 | 141 | 72 | 8.6 (13.1) | 0.54 | 0.62 | RED |
| refit | cusum_14__G30_80k3 | 2457 | 228 | 62 | 67.2 (13.1) | 0.49 | 0.54 | RED |
| native | swing_pct_12__NH9_26e50 | 2041 | 105 | 45 | 17.7 (13.1) | 0.57 | 0.46 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| swing_pct_12__NH9_26e50 | 2041 | 105 | 45 | 126 | 598 | 10991 |
| cusum_14__G30_80k3 | 2457 | 228 | 62 | 175 | 1651 | 13228 |
| mom_28__NH12_34e50 | 2576 | 231 | 73 | 240 | 1560 | 13872 |
| vsess_50__NH9_26e200 | 2150 | 170 | 61 | 243 | 794 | 11579 |
| vnorm_250__NH12_34e50 | 1997 | 166 | 60 | 264 | 1005 | 10751 |
| swing_pct_12__NH9_26e200 | 1586 | 87 | 47 | 161 | 281 | 8539 |
| mrenko_14__G12_34k3 | 1954 | 175 | 60 | 271 | 849 | 10519 |
| rng_10__G30_80k5 | 2424 | 248 | 85 | 272 | 1240 | 13054 |
| frenko_14__G12_34t5 | 2105 | 150 | 74 | 276 | 722 | 11333 |
| swing_atr_0.4__NH9_26e200 | 2295 | 205 | 85 | 302 | 1233 | 12357 |
| wrenko_28__NH9_26e200 | 1944 | 134 | 73 | 220 | 1086 | 10467 |
| trend_28__NH9_26e200 | 1944 | 134 | 73 | 220 | 1086 | 10467 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 47.7 | 13.1 | 0.57 | 170 | 552 |
| 6M->3M | 37 | 6.9 | 17.7 | 0.51 | 1496 | 1363 |
| 3M->1M | 37 | -22.2 | 13.1 | 0.43 | 632 | 552 |
| 3M->3M | 37 | -13.7 | 17.7 | 0.46 | 1931 | 1363 |
| 12M->1M | 37 | 20.3 | 13.1 | 0.46 | 898 | 552 |
| 12M->3M | 37 | -7.9 | 17.7 | 0.59 | 3523 | 1363 |
| 6M->2w | 37 | 62.2 | 47.2 | 0.51 | 126 | 254 |

Nulls (same pick procedure): shift11: OOS -13.5/mo share beat 0.49; shift23: OOS 7.5/mo share beat 0.46; shift37: OOS -23.6/mo share beat 0.43; random-clock pool: OOS 6.0/mo share beat 0.57

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 48 vs 14 (n 36); +3M -32 vs 18 (n 34); +6M -5 vs 6 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -3.0 | -18.2 | -84% | -42% | -31% | GREEN |
| Y2023 | -2.5 | 7.0 | +136% | +11% | +3% | RED |
| Y2024 | 4.5 | 17.0 | +74% | +146% | +83% | RED |
| Y2025 | 0.8 | -9.1 | -109% | -46% | +11% | GREEN |
| Y2026 | -10.6 | -23.7 | -55% | +10% | -10% | GREEN |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.735, 'spa_p': 0.124, 'T': 26, 'K': 5544}

**Deliverable row**: H7 Asia: bar today 1-minute time (live) -> proposed swing_pct_12 | construction: swing_pct_12 (swing / zigzag bars: leg ends when price retraces pct (basis points of price) from the extreme (id swing_pct_bps) or ATR multiple (swing_atr_k, ATR of 5-min ranges trailing)) | param set NH9_26e50 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (ZigZag-style) | scaling: none (clock/price units are absolute) (new custom BarsType)

## 4. Engine swap test (hook swb_inject on JL3; same book object, native entries in the swapped session suppressed, bar signals injected)

### Identity (live 1-minute bar signals through the hook vs JL3, trade for trade; key = book, side, entry second, lots)

| set | month | JL3 trades | swap trades | identical | JL3 net | swap net |
|---|---|---:|---:|---:|---:|---:|
| TL3_SWB_ID2_A70 | 202504 | 637 | 637 | 635 | 41239.76 | 39066.26 |
| TL3_SWB_ID2_A70 | 202610 | 691 | 691 | 685 | 37159.82 | 36528.82 |
| TL3_SWB_ID2_H70 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID2_H70 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID2_H73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID2_H73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID2_O73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID2_O73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
| TL3_SWB_ID2_P70 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID2_P70 | 202610 | 691 | 690 | 688 | 37159.82 | 28687.82 |
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
| TL3_SWB_ID3_O73 | 202504 | 637 | 637 | 637 | 41239.76 | 41239.76 |
| TL3_SWB_ID3_O73 | 202610 | 691 | 691 | 691 | 37159.82 | 37159.82 |
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

### TL3_SWB_O73_4d5758 (BEST-AVAILABLE-NOT-PROVEN | row kagi_56 set NO930_3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10876 | -1.4% | 31109 | 30641 | -15728 | -15728 | 16098 | 18224 | 1981/1996 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19033 | -1.4% | 54441 | 53621 | -27524 | -27524 | 28172 | 31893 | 1981/1996 |
| L6M | 3/6 | $4.84 base lots | 11035 | 10876 | -1.4% | 31109 | 30641 | -15728 | -15728 | 16098 | 18224 | 1981/1996 |
| L6M | 3/6 | $4.84 x1.75 | 19311 | 19033 | -1.4% | 54441 | 53621 | -27524 | -27524 | 28172 | 31893 | 1981/1996 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 -2601 -> -2601; H7 15819 -> 16758; K7 33493 -> 41675; M7 22641 -> 24222; O7 4434 -> 20756; P7 122661 -> 123333; U7 23321 -> 23321

### TL3_SWB_P70_0ceb3c (BEST-AVAILABLE-NOT-PROVEN | row dlt_70 set NC10)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 12408 | +12.4% | 31109 | 38071 | -15728 | -22434 | 16098 | 13914 | 1981/1942 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 21714 | +12.4% | 54441 | 66624 | -27524 | -39259 | 28172 | 24350 | 1981/1942 |
| L6M | 6/6 | $4.84 base lots | 9612 | 12000 | +24.8% | 31109 | 38071 | -15728 | -22434 | 18755 | 12265 | 4292/4108 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 21000 | +24.8% | 54441 | 66624 | -27524 | -39259 | 32822 | 21464 | 4292/4108 |
| HOLD | 6/6 | $4.84 base lots | 29372 | 33240 | +13.2% | 83756 | 79059 | -37324 | -40883 | 9280 | 6533 | 3311/3243 |
| HOLD | 6/6 | $4.84 x1.75 | 51402 | 58170 | +13.2% | 146574 | 138353 | -65316 | -71545 | 16240 | 11434 | 3311/3243 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 42057; K7 83430 -> 88548; M7 4691 -> -4214; O7 10923 -> 9262; P7 304772 -> 128540; U7 59410 -> 68940

### TL3_SWB_P70_3deda2 (BEST-AVAILABLE-NOT-PROVEN | row vsess_80 set NE8_30a10s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 20973 | +90.1% | 31109 | 51196 | -15728 | -20088 | 16098 | 6793 | 1981/1766 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 36702 | +90.1% | 54441 | 89592 | -27524 | -35154 | 28172 | 11888 | 1981/1766 |
| L6M | 6/6 | $4.84 base lots | 9612 | 16379 | +70.4% | 31109 | 51196 | -15728 | -20088 | 18755 | 7748 | 4292/3780 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 28663 | +70.4% | 54441 | 89592 | -27524 | -35154 | 32822 | 13559 | 4292/3780 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 20751 | -29.4% | 83756 | 62831 | -37324 | -34877 | 9280 | 7465 | 3311/3132 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 36314 | -29.4% | 146574 | 109954 | -65316 | -61035 | 16240 | 13064 | 3311/3132 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27235 | -1.1% | 91441 | 69497 | -38896 | -47300 | 4849 | 3884 | 11949/11357 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 47661 | -1.1% | 160021 | 121620 | -68068 | -82775 | 8486 | 6798 | 11949/11357 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44612; K7 83430 -> 86863; M7 4691 -> -18125; O7 10923 -> 7201; P7 304772 -> 29826; U7 59410 -> 57325

### TL3_SWB_P70_4bba9c (BEST-AVAILABLE-NOT-PROVEN | row tick_3200 set G20k8)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11594 | +5.1% | 31109 | 28313 | -15728 | -16567 | 16098 | 10936 | 1981/1793 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20289 | +5.1% | 54441 | 49547 | -27524 | -28992 | 28172 | 19138 | 1981/1793 |
| L6M | 6/6 | $4.84 base lots | 9612 | 10945 | +13.9% | 31109 | 28313 | -15728 | -16567 | 18755 | 9630 | 4292/3812 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 19154 | +13.9% | 54441 | 49547 | -27524 | -28992 | 32822 | 16853 | 4292/3812 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 23781 | -19.0% | 83756 | 70337 | -37324 | -41348 | 9280 | 6513 | 3311/3123 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 41616 | -19.0% | 146574 | 123089 | -65316 | -72358 | 16240 | 11397 | 3311/3123 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 42514; K7 83430 -> 91585; M7 4691 -> -16861; O7 10923 -> 6736; P7 304772 -> 71628; U7 59410 -> 63199

### TL3_SWB_P70_4fddd4 (BEST-AVAILABLE-NOT-PROVEN | row dol_1700 set G40k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 17534 | +58.9% | 31109 | 44539 | -15728 | -15533 | 16098 | 9223 | 1981/1790 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 30684 | +58.9% | 54441 | 77944 | -27524 | -27182 | 28172 | 16141 | 1981/1790 |
| L6M | 6/6 | $4.84 base lots | 9612 | 14120 | +46.9% | 31109 | 44539 | -15728 | -15533 | 18755 | 10418 | 4292/3855 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 24710 | +46.9% | 54441 | 77944 | -27524 | -27182 | 32822 | 18231 | 4292/3855 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 21617 | -26.4% | 83756 | 66160 | -37324 | -45456 | 9280 | 6813 | 3311/3127 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 37829 | -26.4% | 146574 | 115781 | -65316 | -79548 | 16240 | 11924 | 3311/3127 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 43416; K7 83430 -> 93269; M7 4691 -> -13311; O7 10923 -> 8227; P7 304772 -> 84019; U7 59410 -> 64697

### TL3_SWB_P70_619496 (BEST-AVAILABLE-NOT-PROVEN | row swing_pct_8 set G40k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 19792 | +79.4% | 31109 | 49351 | -15728 | -16579 | 16098 | 8549 | 1981/1788 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 34636 | +79.4% | 54441 | 86365 | -27524 | -29013 | 28172 | 14961 | 1981/1788 |
| L6M | 6/6 | $4.84 base lots | 9612 | 15268 | +58.8% | 31109 | 49351 | -15728 | -16579 | 18755 | 10588 | 4292/3906 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 26719 | +58.8% | 54441 | 86365 | -27524 | -29013 | 32822 | 18529 | 4292/3906 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 25551 | -13.0% | 83756 | 70989 | -37324 | -43537 | 9280 | 5975 | 3311/3107 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 44715 | -13.0% | 146574 | 124231 | -65316 | -76189 | 16240 | 10456 | 3311/3107 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 45511; K7 83430 -> 91231; M7 4691 -> -10723; O7 10923 -> 8857; P7 304772 -> 89123; U7 59410 -> 60856

### TL3_SWB_P70_7adc47 (BEST-AVAILABLE-NOT-PROVEN | row pasl_28 set NC40)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11084 | +0.4% | 31109 | 28771 | -15728 | -14328 | 16098 | 9970 | 1981/1790 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19397 | +0.4% | 54441 | 50349 | -27524 | -25075 | 28172 | 17447 | 1981/1790 |
| L6M | 6/6 | $4.84 base lots | 9612 | 10731 | +11.6% | 31109 | 28771 | -15728 | -14328 | 18755 | 9562 | 4292/3804 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 18779 | +11.6% | 54441 | 50349 | -27524 | -25075 | 32822 | 16734 | 4292/3804 |
| HOLD | 6/6 | $4.84 base lots | 29372 | 23903 | -18.6% | 83756 | 73043 | -37324 | -44760 | 9280 | 6663 | 3311/3128 |
| HOLD | 6/6 | $4.84 x1.75 | 51402 | 41831 | -18.6% | 146574 | 127825 | -65316 | -78329 | 16240 | 11661 | 3311/3128 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44334; K7 83430 -> 89320; M7 4691 -> -14795; O7 10923 -> 6750; P7 304772 -> 70094; U7 59410 -> 60991

### TL3_SWB_P70_ca5cc9 (BEST-AVAILABLE-NOT-PROVEN | row dlt_70 set NS6_1)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 12866 | +16.6% | 31109 | 34671 | -15728 | -11574 | 16098 | 13018 | 1981/1889 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 22516 | +16.6% | 54441 | 60674 | -27524 | -20254 | 28172 | 22782 | 1981/1889 |
| L6M | 6/6 | $4.84 base lots | 9612 | 12069 | +25.6% | 31109 | 34671 | -15728 | -15556 | 18755 | 12300 | 4292/3961 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 21120 | +25.6% | 54441 | 60674 | -27524 | -27223 | 32822 | 21525 | 4292/3961 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 26203 | -10.8% | 83756 | 80146 | -37324 | -40870 | 9280 | 7374 | 3311/3147 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 45856 | -10.8% | 146574 | 140255 | -65316 | -71523 | 16240 | 12904 | 3311/3147 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 43711; K7 83430 -> 89369; M7 4691 -> -18567; O7 10923 -> 6136; P7 304772 -> 140216; U7 59410 -> 71508

### TL3_SWB_P70_cf6de1 (BEST-AVAILABLE-NOT-PROVEN | row tm420 set G10k5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 15293 | +38.6% | 31109 | 45351 | -15728 | -25998 | 16098 | 10117 | 1981/1840 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 26764 | +38.6% | 54441 | 79364 | -27524 | -45496 | 28172 | 17705 | 1981/1840 |
| L6M | 6/6 | $4.84 base lots | 9612 | 12805 | +33.2% | 31109 | 45351 | -15728 | -25998 | 18755 | 11940 | 4292/3996 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 22409 | +33.2% | 54441 | 79364 | -27524 | -45496 | 32822 | 20894 | 4292/3996 |
| HOLD | 6/6 | $4.84 base lots | 29372 | 22816 | -22.3% | 83756 | 70663 | -37324 | -35915 | 9280 | 8369 | 3311/3214 |
| HOLD | 6/6 | $4.84 x1.75 | 51402 | 39929 | -22.3% | 146574 | 123661 | -65316 | -62851 | 16240 | 14647 | 3311/3214 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46911; K7 83430 -> 78670; M7 4691 -> -6820; O7 10923 -> 5934; P7 304772 -> 139942; U7 59410 -> 58186

### TL3_SWB_P70_d23a42 (BEST-AVAILABLE-NOT-PROVEN | row dib_10000 set NS3_2s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 19617 | +77.8% | 31109 | 48662 | -15728 | -18651 | 16098 | 7995 | 1981/1780 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 34330 | +77.8% | 54441 | 85159 | -27524 | -32640 | 28172 | 13991 | 1981/1780 |
| L6M | 6/6 | $4.84 base lots | 9612 | 15511 | +61.4% | 31109 | 48662 | -15728 | -18651 | 18755 | 8575 | 4292/3794 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 27144 | +61.4% | 54441 | 85159 | -27524 | -32640 | 32822 | 15007 | 4292/3794 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 22828 | -22.3% | 83756 | 67858 | -37324 | -42723 | 9280 | 6771 | 3311/3124 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 39949 | -22.3% | 146574 | 118752 | -65316 | -74765 | 16240 | 11850 | 3311/3124 |
| PRIOR | 1/31 | $4.84 base lots | 15714 | 13830 | -12.0% | 36477 | 32120 | -17668 | -12645 | 8746 | 7096 | 394/369 |
| PRIOR | 1/31 | $4.84 x1.75 | 27499 | 24202 | -12.0% | 63834 | 56210 | -30920 | -22130 | 15306 | 12419 | 394/369 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44991; K7 83430 -> 93295; M7 4691 -> -21682; O7 10923 -> 7763; P7 304772 -> 43471; U7 59410 -> 62189

### TL3_SWB_P70_e38278 (BEST-AVAILABLE-NOT-PROVEN | row kagi_40 set G40k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 17773 | +61.1% | 31109 | 44992 | -15728 | -16579 | 16098 | 9141 | 1981/1776 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 31103 | +61.1% | 54441 | 78736 | -27524 | -29013 | 28172 | 15997 | 1981/1776 |
| L6M | 6/6 | $4.84 base lots | 9612 | 14338 | +49.2% | 31109 | 44992 | -15728 | -16579 | 18755 | 9712 | 4292/3837 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 25092 | +49.2% | 54441 | 78736 | -27524 | -29013 | 32822 | 16996 | 4292/3837 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27156 | -7.5% | 83756 | 74085 | -37324 | -42723 | 9280 | 5392 | 3311/3108 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 47524 | -7.5% | 146574 | 129649 | -65316 | -74765 | 16240 | 9437 | 3311/3108 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 45811; K7 83430 -> 90650; M7 4691 -> -16044; O7 10923 -> 8999; P7 304772 -> 65832; U7 59410 -> 65596

### TL3_SWB_P70_f0eec5 (BEST-AVAILABLE-NOT-PROVEN | row dchg_40 set G40k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 17773 | +61.1% | 31109 | 44992 | -15728 | -16579 | 16098 | 9141 | 1981/1776 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 31103 | +61.1% | 54441 | 78736 | -27524 | -29013 | 28172 | 15997 | 1981/1776 |
| L6M | 6/6 | $4.84 base lots | 9612 | 14338 | +49.2% | 31109 | 44992 | -15728 | -16579 | 18755 | 9712 | 4292/3837 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 25092 | +49.2% | 54441 | 78736 | -27524 | -29013 | 32822 | 16996 | 4292/3837 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27156 | -7.5% | 83756 | 74085 | -37324 | -42723 | 9280 | 5392 | 3311/3108 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 47524 | -7.5% | 146574 | 129649 | -65316 | -74765 | 16240 | 9437 | 3311/3108 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 45811; K7 83430 -> 90650; M7 4691 -> -16044; O7 10923 -> 8999; P7 304772 -> 65832; U7 59410 -> 65596

### TL3_SWB_P70_f306e1 (BEST-AVAILABLE-NOT-PROVEN | row vsess_80 set NE8_30a30s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 20973 | +90.1% | 31109 | 51196 | -15728 | -20088 | 16098 | 6793 | 1981/1766 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 36702 | +90.1% | 54441 | 89592 | -27524 | -35154 | 28172 | 11888 | 1981/1766 |
| L6M | 6/6 | $4.84 base lots | 9612 | 16376 | +70.4% | 31109 | 51196 | -15728 | -20088 | 18755 | 7785 | 4292/3779 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 28658 | +70.4% | 54441 | 89592 | -27524 | -35154 | 32822 | 13623 | 4292/3779 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 20784 | -29.2% | 83756 | 62831 | -37324 | -34877 | 9280 | 7460 | 3311/3132 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 36371 | -29.2% | 146574 | 109954 | -65316 | -61035 | 16240 | 13055 | 3311/3132 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27474 | -0.2% | 91441 | 69497 | -38896 | -47300 | 4849 | 3858 | 11949/11358 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 48080 | -0.2% | 160021 | 121620 | -68068 | -82775 | 8486 | 6751 | 11949/11358 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44612; K7 83430 -> 86863; M7 4691 -> -18125; O7 10923 -> 7201; P7 304772 -> 30805; U7 59410 -> 57325

### TL3_SWB_P71_25dbb2 (BEST-AVAILABLE-NOT-PROVEN | row rng_80 set G20k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10526 | -4.6% | 31109 | 30517 | -15728 | -14635 | 16098 | 14714 | 1981/1815 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18421 | -4.6% | 54441 | 53405 | -27524 | -25611 | 28172 | 25749 | 1981/1815 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9362 | -2.6% | 31109 | 30517 | -15728 | -14635 | 18755 | 17300 | 4292/3962 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16384 | -2.6% | 54441 | 53405 | -27524 | -25611 | 32822 | 30276 | 4292/3962 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 26624 | -9.4% | 83756 | 77676 | -37324 | -36171 | 9280 | 8597 | 3311/3136 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 46593 | -9.4% | 146574 | 135934 | -65316 | -63299 | 16240 | 15044 | 3311/3136 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44553; K7 83430 -> 78881; M7 4691 -> -4418; O7 10923 -> 11075; P7 304772 -> 286268; U7 59410 -> 52614

### TL3_SWB_P71_2cbdad (BEST-AVAILABLE-NOT-PROVEN | row trend_56 set NC40)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10930 | -0.9% | 31109 | 32462 | -15728 | -18138 | 16098 | 15820 | 1981/1805 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19128 | -0.9% | 54441 | 56808 | -27524 | -31741 | 28172 | 27685 | 1981/1805 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9698 | +0.9% | 31109 | 32462 | -15728 | -18138 | 18755 | 17574 | 4292/3936 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16971 | +0.9% | 54441 | 56808 | -27524 | -31741 | 32822 | 30755 | 4292/3936 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 25661 | -12.6% | 83756 | 74372 | -37324 | -32320 | 9280 | 8311 | 3311/3088 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 44907 | -12.6% | 146574 | 130151 | -65316 | -56560 | 16240 | 14544 | 3311/3088 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 21727 | -21.1% | 91441 | 68930 | -38896 | -33726 | 4849 | 5468 | 11949/11156 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 38022 | -21.1% | 160021 | 120628 | -68068 | -59020 | 8486 | 9570 | 11949/11156 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44580; K7 83430 -> 85555; M7 4691 -> -2420; O7 10923 -> 12745; P7 304772 -> 283387; U7 59410 -> 52411

### TL3_SWB_P71_3779d0 (BEST-AVAILABLE-NOT-PROVEN | row lbrk_5_10 set NC40)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 9825 | -11.0% | 31109 | 27013 | -15728 | -14811 | 16098 | 15531 | 1981/1845 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 17193 | -11.0% | 54441 | 47272 | -27524 | -25919 | 28172 | 27179 | 1981/1845 |
| L6M | 6/6 | $4.84 base lots | 9612 | 8890 | -7.5% | 31109 | 27013 | -15728 | -14811 | 18755 | 17695 | 4292/4006 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 15557 | -7.5% | 54441 | 47272 | -27524 | -25919 | 32822 | 30967 | 4292/4006 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27725 | -5.6% | 83756 | 73571 | -37324 | -33999 | 9280 | 8523 | 3311/3119 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48519 | -5.6% | 146574 | 128750 | -65316 | -59498 | 16240 | 14916 | 3311/3119 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 22886 | -16.9% | 91441 | 70633 | -38896 | -36987 | 4849 | 5299 | 11949/11349 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 40050 | -16.9% | 160021 | 123607 | -68068 | -64728 | 8486 | 9274 | 11949/11349 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 43381; K7 83430 -> 89796; M7 4691 -> 27; O7 10923 -> 12197; P7 304772 -> 278207; U7 59410 -> 56195

### TL3_SWB_P71_5c1f72 (BEST-AVAILABLE-NOT-PROVEN | row dol_1700 set G40k8)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 9908 | -10.2% | 31109 | 28085 | -15728 | -17399 | 16098 | 16992 | 1981/1833 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 17339 | -10.2% | 54441 | 49149 | -27524 | -30449 | 28172 | 29735 | 1981/1833 |
| L6M | 6/6 | $4.84 base lots | 9612 | 8985 | -6.5% | 31109 | 28085 | -15728 | -17399 | 18755 | 18688 | 4292/3987 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 15723 | -6.5% | 54441 | 49149 | -27524 | -30449 | 32822 | 32704 | 4292/3987 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 26540 | -9.6% | 83756 | 73675 | -37324 | -35155 | 9280 | 7956 | 3311/3137 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 46445 | -9.6% | 146574 | 128930 | -65316 | -61520 | 16240 | 13922 | 3311/3137 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44553; K7 83430 -> 91281; M7 4691 -> -5670; O7 10923 -> 13511; P7 304772 -> 313113; U7 59410 -> 49784

### TL3_SWB_P71_67b599 (BEST-AVAILABLE-NOT-PROVEN | row wrenko_56 set NC40)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10930 | -0.9% | 31109 | 32462 | -15728 | -18138 | 16098 | 15820 | 1981/1805 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19128 | -0.9% | 54441 | 56808 | -27524 | -31741 | 28172 | 27685 | 1981/1805 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9698 | +0.9% | 31109 | 32462 | -15728 | -18138 | 18755 | 17574 | 4292/3936 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16971 | +0.9% | 54441 | 56808 | -27524 | -31741 | 32822 | 30755 | 4292/3936 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 25661 | -12.6% | 83756 | 74372 | -37324 | -32320 | 9280 | 8311 | 3311/3088 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 44907 | -12.6% | 146574 | 130151 | -65316 | -56560 | 16240 | 14544 | 3311/3088 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 21727 | -21.1% | 91441 | 68930 | -38896 | -33726 | 4849 | 5468 | 11949/11156 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 38022 | -21.1% | 160021 | 120628 | -68068 | -59020 | 8486 | 9570 | 11949/11156 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44580; K7 83430 -> 85555; M7 4691 -> -2420; O7 10923 -> 12745; P7 304772 -> 283387; U7 59410 -> 52411

### TL3_SWB_P71_6ad7a8 (BEST-AVAILABLE-NOT-PROVEN | row vnorm_40 set NC40)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10965 | -0.6% | 31109 | 31865 | -15728 | -19644 | 16098 | 14993 | 1981/1792 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19189 | -0.6% | 54441 | 55764 | -27524 | -34377 | 28172 | 26238 | 1981/1792 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9690 | +0.8% | 31109 | 31865 | -15728 | -19644 | 18755 | 17210 | 4292/3921 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16958 | +0.8% | 54441 | 55764 | -27524 | -34377 | 32822 | 30118 | 4292/3921 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 26776 | -8.8% | 83756 | 76461 | -37324 | -35148 | 9280 | 8175 | 3311/3092 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 46858 | -8.8% | 146574 | 133806 | -65316 | -61509 | 16240 | 14305 | 3311/3092 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 43381; K7 83430 -> 81694; M7 4691 -> -1239; O7 10923 -> 13209; P7 304772 -> 276929; U7 59410 -> 52411

### TL3_SWB_P71_7f4d47 (BEST-AVAILABLE-NOT-PROVEN | row vnorm_150 set NS4_1s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10312 | -6.6% | 31109 | 29549 | -15728 | -18138 | 16098 | 15157 | 1981/1805 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18046 | -6.6% | 54441 | 51711 | -27524 | -31741 | 28172 | 26525 | 1981/1805 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9333 | -2.9% | 31109 | 29549 | -15728 | -18138 | 18755 | 17247 | 4292/3937 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16332 | -2.9% | 54441 | 51711 | -27524 | -31741 | 32822 | 30182 | 4292/3937 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 30942 | +5.3% | 83756 | 76347 | -37324 | -35148 | 9280 | 7557 | 3311/3074 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 54148 | +5.3% | 146574 | 133607 | -65316 | -61509 | 16240 | 13225 | 3311/3074 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 43381; K7 83430 -> 81722; M7 4691 -> -813; O7 10923 -> 12745; P7 304772 -> 277897; U7 59410 -> 52489

### TL3_SWB_P71_8c9ea9 (BEST-AVAILABLE-NOT-PROVEN | row tm780 set G40k5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 9189 | -16.7% | 31109 | 27096 | -15728 | -13976 | 16098 | 16986 | 1981/1834 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 16081 | -16.7% | 54441 | 47419 | -27524 | -24458 | 28172 | 29725 | 1981/1834 |
| L6M | 6/6 | $4.84 base lots | 9612 | 8469 | -11.9% | 31109 | 27096 | -15728 | -13976 | 18755 | 18847 | 4292/3996 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 14820 | -11.9% | 54441 | 47419 | -27524 | -24458 | 32822 | 32982 | 4292/3996 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 26287 | -10.5% | 83756 | 77922 | -37324 | -37366 | 9280 | 8708 | 3311/3097 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 46002 | -10.5% | 146574 | 136364 | -65316 | -65390 | 16240 | 15239 | 3311/3097 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44553; K7 83430 -> 88169; M7 4691 -> -1280; O7 10923 -> 13906; P7 304772 -> 312967; U7 59410 -> 52551

### TL3_SWB_P71_a9eb3b (BEST-AVAILABLE-NOT-PROVEN | row cdr_400 set G10k5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10144 | -8.1% | 31109 | 28538 | -15728 | -16684 | 16098 | 15482 | 1981/1801 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 17751 | -8.1% | 54441 | 49941 | -27524 | -29196 | 28172 | 27094 | 1981/1801 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9002 | -6.3% | 31109 | 28538 | -15728 | -16684 | 18755 | 17923 | 4292/3942 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 15754 | -6.3% | 54441 | 49941 | -27524 | -29196 | 32822 | 31366 | 4292/3942 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 28274 | -3.7% | 83756 | 79997 | -37324 | -35148 | 9280 | 8352 | 3311/3095 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 49479 | -3.7% | 146574 | 139995 | -65316 | -61509 | 16240 | 14616 | 3311/3095 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44553; K7 83430 -> 84855; M7 4691 -> 178; O7 10923 -> 10946; P7 304772 -> 291368; U7 59410 -> 53802

### TL3_SWB_P71_bd36bc (BEST-AVAILABLE-NOT-PROVEN | row vrb_3500 set G40k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10852 | -1.7% | 31109 | 32752 | -15728 | -15430 | 16098 | 15273 | 1981/1802 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18991 | -1.7% | 54441 | 57315 | -27524 | -27003 | 28172 | 26728 | 1981/1802 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9537 | -0.8% | 31109 | 32752 | -15728 | -15430 | 18755 | 17389 | 4292/3945 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16690 | -0.8% | 54441 | 57315 | -27524 | -27003 | 32822 | 30430 | 4292/3945 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 23409 | -20.3% | 83756 | 66098 | -37324 | -32717 | 9280 | 8972 | 3311/3116 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 40966 | -20.3% | 146574 | 115671 | -65316 | -57255 | 16240 | 15701 | 3311/3116 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44553; K7 83430 -> 84788; M7 4691 -> -4044; O7 10923 -> 11972; P7 304772 -> 276737; U7 59410 -> 57271

### TL3_SWB_P71_d678a2 (BEST-AVAILABLE-NOT-PROVEN | row vnorm_400 set NS6_1)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11470 | +3.9% | 31109 | 33268 | -15728 | -17644 | 16098 | 14533 | 1981/1797 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20073 | +3.9% | 54441 | 58218 | -27524 | -30878 | 28172 | 25433 | 1981/1797 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9805 | +2.0% | 31109 | 33268 | -15728 | -17644 | 18755 | 17338 | 4292/3944 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17158 | +2.0% | 54441 | 58218 | -27524 | -30878 | 32822 | 30342 | 4292/3944 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 24989 | -14.9% | 83756 | 75152 | -37324 | -35148 | 9280 | 8676 | 3311/3102 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 43731 | -14.9% | 146574 | 131515 | -65316 | -61509 | 16240 | 15183 | 3311/3102 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44553; K7 83430 -> 76527; M7 4691 -> -7321; O7 10923 -> 12177; P7 304772 -> 289289; U7 59410 -> 54693

### TL3_SWB_P73_07466d (BEST-AVAILABLE-NOT-PROVEN | row vsess_50 set NC10s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10562 | -4.3% | 31109 | 29254 | -15728 | -15100 | 16098 | 15487 | 1981/1956 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18483 | -4.3% | 54441 | 51195 | -27524 | -26424 | 28172 | 27103 | 1981/1956 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9522 | -0.9% | 31109 | 29254 | -15728 | -15100 | 18755 | 18179 | 4292/4255 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16664 | -0.9% | 54441 | 51195 | -27524 | -26424 | 32822 | 31814 | 4292/4255 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29160 | -0.7% | 83756 | 81526 | -37324 | -35632 | 9280 | 8728 | 3311/3287 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51030 | -0.7% | 146574 | 142670 | -65316 | -62356 | 16240 | 15275 | 3311/3287 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 45451; K7 83430 -> 77313; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 296199; U7 59410 -> 59410

### TL3_SWB_P73_293ecd (BEST-AVAILABLE-NOT-PROVEN | row cdr_1000 set G20t5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10562 | -4.3% | 31109 | 29254 | -15728 | -15100 | 16098 | 15393 | 1981/1953 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18483 | -4.3% | 54441 | 51195 | -27524 | -26424 | 28172 | 26938 | 1981/1953 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9341 | -2.8% | 31109 | 29254 | -15728 | -15100 | 18755 | 18350 | 4292/4254 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16346 | -2.8% | 54441 | 51195 | -27524 | -26424 | 32822 | 32113 | 4292/4254 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29287 | -0.3% | 83756 | 82310 | -37324 | -35061 | 9280 | 8859 | 3311/3287 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51253 | -0.3% | 146574 | 144043 | -65316 | -61357 | 16240 | 15503 | 3311/3287 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27189 | -1.3% | 91441 | 89930 | -38896 | -41204 | 4849 | 4893 | 11949/11809 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 47581 | -1.3% | 160021 | 157377 | -68068 | -72107 | 8486 | 8563 | 11949/11809 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 296606; U7 59410 -> 59410

### TL3_SWB_P73_5fc6c8 (BEST-AVAILABLE-NOT-PROVEN | row tm900 set NS4_1)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10559 | -4.3% | 31109 | 29254 | -15728 | -13965 | 16098 | 15573 | 1981/1956 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18478 | -4.3% | 54441 | 51195 | -27524 | -24438 | 28172 | 27254 | 1981/1956 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9337 | -2.9% | 31109 | 29254 | -15728 | -13965 | 18755 | 18452 | 4292/4255 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16340 | -2.9% | 54441 | 51195 | -27524 | -24438 | 32822 | 32291 | 4292/4255 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29301 | -0.2% | 83756 | 82310 | -37324 | -35061 | 9280 | 8722 | 3311/3284 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51277 | -0.2% | 146574 | 144043 | -65316 | -61357 | 16240 | 15263 | 3311/3284 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 299363; U7 59410 -> 59410

### TL3_SWB_P73_7d3082 (BEST-AVAILABLE-NOT-PROVEN | row tsf_5_700 set NC40)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10950 | -0.8% | 31109 | 31156 | -15728 | -15100 | 16098 | 15167 | 1981/1957 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19162 | -0.8% | 54441 | 54523 | -27524 | -26424 | 28172 | 26542 | 1981/1957 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9556 | -0.6% | 31109 | 31156 | -15728 | -15100 | 18755 | 18342 | 4292/4258 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16723 | -0.6% | 54441 | 54523 | -27524 | -26424 | 32822 | 32098 | 4292/4258 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29389 | +0.1% | 83756 | 82310 | -37324 | -35061 | 9280 | 8623 | 3311/3287 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51432 | +0.1% | 146574 | 144043 | -65316 | -61357 | 16240 | 15091 | 3311/3287 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 296397; U7 59410 -> 59410

### TL3_SWB_P73_84909b (BEST-AVAILABLE-NOT-PROVEN | row tsf_25_150 set G10k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10568 | -4.2% | 31109 | 29254 | -15728 | -15100 | 16098 | 15393 | 1981/1953 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18494 | -4.2% | 54441 | 51195 | -27524 | -26424 | 28172 | 26937 | 1981/1953 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9350 | -2.7% | 31109 | 29254 | -15728 | -15100 | 18755 | 18304 | 4292/4253 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16363 | -2.7% | 54441 | 51195 | -27524 | -26424 | 32822 | 32033 | 4292/4253 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29512 | +0.5% | 83756 | 82926 | -37324 | -35061 | 9280 | 8882 | 3311/3288 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51645 | +0.5% | 146574 | 145120 | -65316 | -61357 | 16240 | 15544 | 3311/3288 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 295361; U7 59410 -> 59410

### TL3_SWB_P73_8b6413 (BEST-AVAILABLE-NOT-PROVEN | row cdr_1000 set NE13_50a30s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10539 | -4.5% | 31109 | 29254 | -15728 | -15100 | 16098 | 15476 | 1981/1954 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18444 | -4.5% | 54441 | 51195 | -27524 | -26424 | 28172 | 27083 | 1981/1954 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9328 | -2.9% | 31109 | 29254 | -15728 | -15100 | 18755 | 18435 | 4292/4256 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16325 | -2.9% | 54441 | 51195 | -27524 | -26424 | 32822 | 32261 | 4292/4256 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29291 | -0.3% | 83756 | 82310 | -37324 | -35061 | 9280 | 8906 | 3311/3287 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51259 | -0.3% | 146574 | 144043 | -65316 | -61357 | 16240 | 15585 | 3311/3287 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27220 | -1.1% | 91441 | 91290 | -38896 | -41461 | 4849 | 4901 | 11949/11806 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 47634 | -1.1% | 160021 | 159758 | -68068 | -72557 | 8486 | 8576 | 11949/11806 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 298886; U7 59410 -> 59410

### TL3_SWB_P73_91d0ee (BEST-AVAILABLE-NOT-PROVEN | row dol_4000 set NS6_2s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10620 | -3.8% | 31109 | 29254 | -15728 | -15728 | 16098 | 15493 | 1981/1957 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18585 | -3.8% | 54441 | 51195 | -27524 | -27524 | 28172 | 27113 | 1981/1957 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9372 | -2.5% | 31109 | 29254 | -15728 | -15728 | 18755 | 18357 | 4292/4256 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16400 | -2.5% | 54441 | 51195 | -27524 | -27524 | 32822 | 32125 | 4292/4256 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29514 | +0.5% | 83756 | 82310 | -37324 | -35061 | 9280 | 8674 | 3311/3285 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51650 | +0.5% | 146574 | 144043 | -65316 | -61357 | 16240 | 15179 | 3311/3285 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 296795; U7 59410 -> 59410

### TL3_SWB_P73_96074d (BEST-AVAILABLE-NOT-PROVEN | row vrb_10000 set NC20)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10562 | -4.3% | 31109 | 29254 | -15728 | -15100 | 16098 | 15618 | 1981/1954 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18483 | -4.3% | 54441 | 51195 | -27524 | -26424 | 28172 | 27332 | 1981/1954 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9339 | -2.8% | 31109 | 29254 | -15728 | -15100 | 18755 | 18462 | 4292/4252 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16343 | -2.8% | 54441 | 51195 | -27524 | -26424 | 32822 | 32309 | 4292/4252 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29484 | +0.4% | 83756 | 82310 | -37324 | -35061 | 9280 | 8677 | 3311/3288 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51596 | +0.4% | 146574 | 144043 | -65316 | -61357 | 16240 | 15185 | 3311/3288 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 299620; U7 59410 -> 59410

### TL3_SWB_P73_b8997e (BEST-AVAILABLE-NOT-PROVEN | row mom_20 set NC10s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11381 | +3.1% | 31109 | 33555 | -15728 | -16151 | 16098 | 15115 | 1981/1962 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19916 | +3.1% | 54441 | 58720 | -27524 | -28263 | 28172 | 26450 | 1981/1962 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9951 | +3.5% | 31109 | 33555 | -15728 | -16151 | 18755 | 18122 | 4292/4263 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17414 | +3.5% | 54441 | 58720 | -27524 | -28263 | 32822 | 31714 | 4292/4263 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29486 | +0.4% | 83756 | 83296 | -37324 | -35061 | 9280 | 8841 | 3311/3283 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51600 | +0.4% | 146574 | 145768 | -65316 | -61357 | 16240 | 15471 | 3311/3283 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 75818; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 294999; U7 59410 -> 59410

### TL3_SWB_P73_be26bb (BEST-AVAILABLE-NOT-PROVEN | row cdr_1000 set A)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10562 | -4.3% | 31109 | 29254 | -15728 | -15100 | 16098 | 15393 | 1981/1953 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18483 | -4.3% | 54441 | 51195 | -27524 | -26424 | 28172 | 26938 | 1981/1953 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9341 | -2.8% | 31109 | 29254 | -15728 | -15100 | 18755 | 18350 | 4292/4254 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16346 | -2.8% | 54441 | 51195 | -27524 | -26424 | 32822 | 32113 | 4292/4254 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29287 | -0.3% | 83756 | 82310 | -37324 | -35061 | 9280 | 8859 | 3311/3287 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51253 | -0.3% | 146574 | 144043 | -65316 | -61357 | 16240 | 15503 | 3311/3287 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 296606; U7 59410 -> 59410

### TL3_SWB_P73_d6c62d (BEST-AVAILABLE-NOT-PROVEN | row cdr_1000 set NE13_50a10s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10539 | -4.5% | 31109 | 29254 | -15728 | -15100 | 16098 | 15476 | 1981/1954 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18444 | -4.5% | 54441 | 51195 | -27524 | -26424 | 28172 | 27083 | 1981/1954 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9328 | -2.9% | 31109 | 29254 | -15728 | -15100 | 18755 | 18435 | 4292/4256 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16325 | -2.9% | 54441 | 51195 | -27524 | -26424 | 32822 | 32261 | 4292/4256 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29291 | -0.3% | 83756 | 82310 | -37324 | -35061 | 9280 | 8860 | 3311/3286 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51259 | -0.3% | 146574 | 144043 | -65316 | -61357 | 16240 | 15505 | 3311/3286 |
| PRIOR | 30/31 | $4.84 base lots | 27406 | 27047 | -1.3% | 91441 | 91290 | -38896 | -41461 | 4824 | 4894 | 11704/11574 |
| PRIOR | 30/31 | $4.84 x1.75 | 47960 | 47333 | -1.3% | 160021 | 159758 | -68068 | -72557 | 8442 | 8565 | 11704/11574 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 298886; U7 59410 -> 59410

### TL3_SWB_P73_f69d14 (BEST-AVAILABLE-NOT-PROVEN | row mrenko_80 set G40t5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10568 | -4.2% | 31109 | 29254 | -15728 | -15100 | 16098 | 15393 | 1981/1953 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18494 | -4.2% | 54441 | 51195 | -27524 | -26424 | 28172 | 26938 | 1981/1953 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9339 | -2.8% | 31109 | 29254 | -15728 | -15100 | 18755 | 18371 | 4292/4252 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16343 | -2.8% | 54441 | 51195 | -27524 | -26424 | 32822 | 32149 | 4292/4252 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29734 | +1.2% | 83756 | 83251 | -37324 | -36002 | 9280 | 8650 | 3311/3288 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 52035 | +1.2% | 146574 | 145689 | -65316 | -63003 | 16240 | 15137 | 3311/3288 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 297144; U7 59410 -> 59410

### TL3_SWB_P73_faeb52 (BEST-AVAILABLE-NOT-PROVEN | row renko_40 set G40t5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10589 | -4.0% | 31109 | 29254 | -15728 | -15100 | 16098 | 15279 | 1981/1958 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18531 | -4.0% | 54441 | 51195 | -27524 | -26424 | 28172 | 26738 | 1981/1958 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9354 | -2.7% | 31109 | 29254 | -15728 | -15100 | 18755 | 18310 | 4292/4257 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16370 | -2.7% | 54441 | 51195 | -27524 | -26424 | 32822 | 32043 | 4292/4257 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29052 | -1.1% | 83756 | 81215 | -37324 | -35061 | 9280 | 8790 | 3311/3289 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 50840 | -1.1% | 146574 | 142126 | -65316 | -61357 | 16240 | 15382 | 3311/3289 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 80324; M7 4691 -> 4862; O7 10923 -> 10923; P7 304772 -> 295526; U7 59410 -> 59410

### Random-clock engine controls (same book / rules / bar count per session as the pick row, persistent draws seeds 101-130; L6M, $4.84 base lots; valid = all 6 months done)

| cell | pick set | valid controls | pick ulcer change | controls ulcer change median [min, max] | share of controls with a better (lower) ulcer change than the pick | pick mean/wk | controls mean/wk median |
|---|---|---:|---:|---|---:|---:|---:|
(no cell has 30 finished L6M controls yet)

