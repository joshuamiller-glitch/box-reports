# DS3 BAR SWAP B (W-SWB): P7 / H7 / A7 / O7 on every bar row

Rule: standing selection rule (CLAUDE.md, user 11-17 18:10Z/18:13Z): pick on the trailing 6 months to the newest data, trailing 3M beside it; validated by rolling walk-forward; older years tolerant (AMBER 15-30% / RED >30% worse than the live bar). FIRST PASS standalone (tape fills, raw chassis, live bracket); engine swap test is section 4.
Pick window: 2026-05-18..2026-11-13 (trailing 6M); data end 2026-11-13; refit 2026-11-18 12:42:31 UTC (loop every 30 min, bi-weekly refit rule); trials counted 70666 candidates (rows x param sets x cells), correction White RC / Hansen SPA per cell on weekly differences vs the live bar; PBO not used (rolling walk-forward instead); in-sample = trailing window, walk-forward = month-end picks from 2023-10, untouched = none frozen.

## Plain summary
- Tried: every available bar row (~490 time / activity / information / price / composite rows) as the signal clock of P7, H7, A7, O7 in three versions side by side: transplanted live settings, transplanted + the book grid refit, and bar-NATIVE rules (bars / bricks as the unit, no minute ATR); standalone on the tape with live brackets, then the exact engine with the full JL3 stack (not gated on the naked result).
- What holds / does not (trailing 6M to the data end, rolling walk-forward from 2023-10, nulls; no cell is CONFIRMED until engine controls finish):
  - P7 NY AM: live bar L6M -1939 pts; trailing-6M pick cdr_1000__NE13_50a10s 1058 pts; rolling WF 6M->1M share of months beating the live bar 0.51 (OOS 3 vs live -75 pts/mo); random-clock pool share 0.62; older years RED
  - P7 London: live bar L6M 1575 pts; trailing-6M pick wrenko_56__NC40 913 pts; rolling WF 6M->1M share of months beating the live bar 0.49 (OOS -60 vs live -18 pts/mo); random-clock pool share 0.54; older years RED
  - H7 NY AM: live bar L6M 874 pts; trailing-6M pick tm300__NH20_55e50 1513 pts; rolling WF 6M->1M share of months beating the live bar 0.43 (OOS -11 vs live 12 pts/mo); random-clock pool share 0.65; older years RED
  - O7 NY AM: live bar L6M 141 pts; trailing-6M pick kagi_56__NO930_3 1582 pts; rolling WF 6M->1M share of months beating the live bar 0.27 (OOS -3 vs live 124 pts/mo); random-clock pool share 0.32; older years RED
  - A7 Asia: live bar L6M -160 pts; trailing-6M pick vsess_80__NE8_30a30s 1067 pts; rolling WF 6M->1M share of months beating the live bar 0.43 (OOS 32 vs live 85 pts/mo); random-clock pool share 0.41; older years RED
  - P7 Asia: live bar L6M 1200 pts; trailing-6M pick vsess_80__NE8_30a10s 962 pts; rolling WF 6M->1M share of months beating the live bar 0.30 (OOS -33 vs live 75 pts/mo); random-clock pool share 0.46; older years RED
  - H7 Asia: live bar L6M 624 pts; trailing-6M pick swing_pct_12__NH9_26e50 2041 pts; rolling WF 6M->1M share of months beating the live bar 0.57 (OOS 48 vs live 13 pts/mo); random-clock pool share 0.41; older years RED
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
| cdr_1000__A | 967 | 69 | 39 | 134 | 625 | 5206 |
| cdr_1000__G20t5 | 967 | 69 | 39 | 134 | 625 | 5206 |
| mom_20__NC10s | 3448 | 459 | 166 | 559 | 1922 | 18566 |
| renko_40__G40k3 | 1928 | 160 | 93 | 361 | 925 | 10382 |
| wrenko_112__NC20 | 614 | 30 | 35 | 121 | 396 | 3306 |
| trend_112__NC20 | 614 | 30 | 35 | 121 | 396 | 3306 |
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

Nulls (same pick procedure): shift11: OOS 12.9/mo share beat 0.59; shift23: OOS 29.9/mo share beat 0.59; shift37: OOS -28.0/mo share beat 0.59; random-clock pool: OOS 75.7/mo share beat 0.62

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

Live bar row `tm60__A`: 6M 1575 pts (n 559, ulcer 200, maxDD 470), 3M 450 pts. PICK (trailing 6M, pick): `wrenko_56__NC40` 913 pts (n 31, ulcer 26, maxDD 65); 3M-pick: `vnorm_400__NS6_1` (DISAGREES).
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
| wrenko_56__NC40 | 913 | 31 | 26 | 65 | 576 | 4918 |
| trend_56__NC40 | 913 | 31 | 26 | 65 | 576 | 4918 |
| dol_1700__G40k8 | 2050 | 125 | 62 | 244 | 539 | 11041 |
| rng_80__G20k3 | 1815 | 114 | 61 | 200 | 657 | 9773 |
| cusum_80__G20k3 | 1961 | 115 | 71 | 229 | 629 | 10562 |
| rng_80__A | 1804 | 110 | 69 | 212 | 408 | 9713 |
| rng_80__G20t5 | 1804 | 110 | 69 | 212 | 408 | 9713 |
| tsf_25_40__NE5_20a30 | 1477 | 119 | 61 | 215 | 858 | 7954 |
| tsf_25_40__NE5_20a10 | 1477 | 119 | 61 | 215 | 858 | 7954 |
| renko_20__NE20_80a30s | 1287 | 85 | 54 | 192 | 982 | 6931 |
| wrenko_56__G20k3 | 949 | 54 | 40 | 105 | 293 | 5109 |

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

Nulls (same pick procedure): shift11: OOS -29.7/mo share beat 0.49; shift23: OOS -70.9/mo share beat 0.49; shift37: OOS -10.8/mo share beat 0.54; random-clock pool: OOS -4.4/mo share beat 0.54

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

**Deliverable row**: P7 London: bar today 1-minute time (live) -> proposed wrenko_56 | construction: wrenko_56 (Renko with wicks (BetterRenko style): classic Renko bricks whose high/low include the raw print extremes since the previous brick) | param set NC40 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (BetterRenko third-party) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

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
| vol_6000__A | 992 | 43 | 42 | 135 | 452 | 1527 |
| vol_6000__G20_55t5 | 992 | 43 | 42 | 135 | 452 | 1527 |
| tm300__A | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__C | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__G20_55t5 | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__G20_55k1 | 1010 | 80 | 49 | 181 | 490 | 1554 |
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

Nulls (same pick procedure): shift11: OOS -31.1/mo share beat 0.57; shift23: OOS 29.7/mo share beat 0.59; shift37: OOS -13.5/mo share beat 0.57; random-clock pool: OOS 26.4/mo share beat 0.65

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
| refit | vib_40000__G1000_10 | 826 | 48 | 55 | 21.2 (123.9) | 0.27 | 0.35 | RED |
| native | dchg_56__NO930_3 | 1582 | 87 | 81 | -29.5 (123.9) | 0.27 | 0.30 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| kagi_56__NO930_3 | 1582 | 87 | 81 | 244 | 989 | 2433 |
| dchg_56__NO930_3 | 1582 | 87 | 81 | 244 | 989 | 2433 |
| vib_15000__NO930_8 | 1432 | 61 | 76 | 243 | 802 | 2204 |
| tm420__NO930_12 | 720 | 31 | 40 | 122 | 86 | 1108 |
| dchg_40__NO830_12 | 1141 | 53 | 70 | 163 | 435 | 1755 |
| kagi_40__NO830_12 | 1141 | 53 | 70 | 163 | 435 | 1755 |
| swing_pct_5__NO1000_8 | 1214 | 80 | 76 | 202 | 311 | 1867 |
| renko_28__NO1000_5 | 1091 | 47 | 71 | 203 | 492 | 1679 |
| vnorm_400__NO930_12 | 891 | 68 | 58 | 162 | 339 | 1370 |
| vib_40000__G1000_10 | 826 | 48 | 55 | 164 | 449 | 1271 |
| tsf_10_400__NO930_5 | 627 | 37 | 43 | 122 | 315 | 964 |
| tm10__NO1000_3 | 878 | 33 | 60 | 162 | 223 | 1350 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -3.4 | 123.9 | 0.27 | 522 | 157 |
| 6M->3M | 37 | 33.8 | 125.9 | 0.27 | 358 | 202 |
| 3M->1M | 37 | 34.5 | 123.9 | 0.32 | 440 | 157 |
| 3M->3M | 37 | 30.7 | 125.9 | 0.30 | 683 | 202 |
| 12M->1M | 37 | -5.9 | 123.9 | 0.35 | 327 | 157 |
| 12M->3M | 37 | 12.4 | 125.9 | 0.16 | 377 | 202 |
| 6M->2w | 37 | -8.8 | 125.7 | 0.32 | 473 | 146 |

Nulls (same pick procedure): shift11: OOS 30.7/mo share beat 0.30; shift23: OOS 26.8/mo share beat 0.32; shift37: OOS 2.8/mo share beat 0.32; random-clock pool: OOS 6.8/mo share beat 0.32

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -8 vs 122 (n 36); +3M 65 vs 141 (n 34); +6M 61 vs 138 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 34.9 | 45.5 | +23% | +115% | +95% | RED |
| Y2023 | 7.8 | -13.3 | -159% | -32% | -5% | GREEN |
| Y2024 | 8.8 | 40.2 | +78% | +206% | +90% | RED |
| Y2025 | 49.4 | 26.6 | -86% | -13% | +39% | RED |
| Y2026 | -18.3 | 58.8 | +131% | +326% | +204% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.538, 'spa_p': 0.296, 'T': 26, 'K': 3181}

**Deliverable row**: O7 NY AM: bar today 1-minute time (live) -> proposed kagi_56 | construction: kagi_56 (Kagi line segments: reversal amount N ticks; bar per segment between reversals (shoulder/waist thickness change recorded by the segment extent)) | param set NO930_3 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: native Kagi | scaling: size x s_rng (same, daily high-low range in points) (native)

### A7 Asia (phase 2)

Live bar row `tm60__A`: 6M -160 pts (n 367, ulcer 475, maxDD 1039), 3M -323 pts. PICK (trailing 6M, pick): `vsess_80__NE8_30a30s` 1067 pts (n 34, ulcer 20, maxDD 61); 3M-pick: `tsf_5_200__Gk10t5` (DISAGREES).
Side by side (trailing-6M pick within each class; WF = rolling pick at month ends, OOS mean pts/month vs live bar; share = months pick beat live bar; older-year worst):

| class | pick row__set | 6M pts | n | ulcer | WF 6M->1M OOS/mo (live) | share beat | WF 6M->2w share beat | older years |
|---|---|---:|---:|---:|---|---:|---:|---|
| live-settings | tm900__A | 679 | 31 | 30 | 68.6 (84.8) | 0.51 | 0.43 | RED |
| refit | vrb_2000__Gk10t5 | 640 | 31 | 21 | 40.0 (84.8) | 0.43 | 0.43 | RED |
| native | vsess_80__NE8_30a10s | 1067 | 34 | 20 | 25.1 (84.8) | 0.41 | 0.35 | RED |

(live-settings = transplanted, live book parameters; refit = transplanted + the book grid; native = bar-native rules, see input table. Earlier rows stay labelled transplanted.)

Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| vsess_80__NE8_30a30s | 1067 | 34 | 20 | 61 | 318 | 1642 |
| vsess_80__NE8_30a10s | 1067 | 34 | 20 | 61 | 318 | 1642 |
| dib_10000__NS3_2s | 795 | 32 | 20 | 62 | 328 | 1223 |
| vrb_2000__Gk10t5 | 640 | 31 | 21 | 61 | 436 | 985 |
| tsf_5_200__Gk10t5 | 979 | 33 | 35 | 182 | 702 | 1505 |
| tm420__Gk10k2 | 1082 | 71 | 42 | 122 | 221 | 1665 |
| tsf_5_200__Gk5t5 | 1129 | 51 | 47 | 139 | 757 | 1736 |
| dib_70000__Gk3k5 | 836 | 33 | 35 | 182 | 409 | 1285 |
| vib_10000__NS4_1s | 800 | 33 | 36 | 139 | 323 | 1230 |
| tm900__Gt10t5 | 679 | 31 | 30 | 106 | 182 | 1045 |
| tm900__A | 679 | 31 | 30 | 106 | 182 | 1045 |
| pasl_40__NC40 | 992 | 44 | 45 | 122 | 475 | 1526 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 31.9 | 84.8 | 0.43 | 538 | 299 |
| 6M->3M | 37 | 38.8 | 90.4 | 0.38 | 838 | 571 |
| 3M->1M | 37 | 17.8 | 84.8 | 0.35 | 361 | 299 |
| 3M->3M | 37 | 42.9 | 90.4 | 0.35 | 234 | 571 |
| 12M->1M | 37 | 41.8 | 84.8 | 0.54 | 227 | 299 |
| 12M->3M | 37 | 37.2 | 90.4 | 0.41 | 605 | 571 |
| 6M->2w | 37 | 52.9 | 114.1 | 0.38 | 242 | 211 |

Nulls (same pick procedure): shift11: OOS 19.8/mo share beat 0.43; shift23: OOS 24.7/mo share beat 0.49; shift37: OOS 26.4/mo share beat 0.49; random-clock pool: OOS 25.8/mo share beat 0.41

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 29 vs 89 (n 36); +3M 43 vs 94 (n 34); +6M -4 vs 87 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 15.5 | 31.5 | +51% | -61% | -43% | RED |
| Y2023 | -5.4 | 4.4 | +221% | +17% | -20% | RED |
| Y2024 | 10.5 | 26.1 | +60% | -47% | -52% | RED |
| Y2025 | 13.6 | 20.8 | +34% | -72% | -65% | RED |
| Y2026 | 16.0 | 55.3 | +71% | +2% | -5% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.584, 'spa_p': 0.016, 'T': 26, 'K': 8704}

**Deliverable row**: A7 Asia: bar today 1-minute time (live) -> proposed vsess_80 | construction: vsess_80 (volume-clock / session-relative: N equal-volume bars per session; bar volume = trailing median session volume / N (a session with a typical volume curve gets N bars; NY open fast, lunch slow in clock ) | param set NE8_30a30s | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (volume threshold set at session start from a trailing table) | scaling: N bars per session; bar volume = trailing-20-date median volume of that session code / N (new custom BarsType)

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

Nulls (same pick procedure): shift11: OOS -19.0/mo share beat 0.35; shift23: OOS -55.2/mo share beat 0.38; shift37: OOS -2.1/mo share beat 0.38; random-clock pool: OOS -8.3/mo share beat 0.46

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

Nulls (same pick procedure): shift11: OOS -13.5/mo share beat 0.49; shift23: OOS 7.5/mo share beat 0.46; shift37: OOS -23.6/mo share beat 0.43; random-clock pool: OOS 32.0/mo share beat 0.41

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

### TL3_SWB_A70_0ceb3c (BEST-AVAILABLE-NOT-PROVEN | row dlt_70 set NC10)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 12174 | +10.3% | 31109 | 41101 | -15728 | -18698 | 16098 | 18177 | 1981/2075 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 21305 | +10.3% | 54441 | 71926 | -27524 | -32722 | 28172 | 31810 | 1981/2075 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9912 | +3.1% | 31109 | 41101 | -15728 | -18698 | 18755 | 20183 | 4292/4453 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17346 | +3.1% | 54441 | 71926 | -27524 | -32722 | 32822 | 35321 | 4292/4453 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27520 | -6.3% | 83756 | 80609 | -37324 | -34576 | 9280 | 9289 | 3311/3332 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48159 | -6.3% | 146574 | 141065 | -65316 | -60508 | 16240 | 16256 | 3311/3332 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 50991; H7 46650 -> 48077; K7 83430 -> 91064; M7 4691 -> -1961; O7 10923 -> 11911; P7 304772 -> 294951; U7 59410 -> 72652

### TL3_SWB_A70_18c336 (BEST-AVAILABLE-NOT-PROVEN | row vrb_2000 set Gk10t5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 12361 | +12.0% | 31109 | 36807 | -15728 | -21789 | 16098 | 16255 | 1981/1904 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 21631 | +12.0% | 54441 | 64413 | -27524 | -38131 | 28172 | 28446 | 1981/1904 |
| L6M | 6/6 | $4.84 base lots | 9612 | 10263 | +6.8% | 31109 | 36807 | -15728 | -21789 | 18755 | 17900 | 4292/4084 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17961 | +6.8% | 54441 | 64413 | -27524 | -38131 | 32822 | 31325 | 4292/4084 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 32053 | +9.1% | 83756 | 87579 | -37324 | -35315 | 9280 | 8250 | 3311/3149 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 56093 | +9.1% | 146574 | 153264 | -65316 | -61801 | 16240 | 14438 | 3311/3149 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 10483; H7 46650 -> 48121; K7 83430 -> 94411; M7 4691 -> -9646; O7 10923 -> 6740; P7 304772 -> 303725; U7 59410 -> 50984

### TL3_SWB_A70_21e445 (BEST-AVAILABLE-NOT-PROVEN | row pasl_40 set NC40)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 12181 | +10.4% | 31109 | 35018 | -15728 | -27386 | 16098 | 15740 | 1981/1900 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 21316 | +10.4% | 54441 | 61282 | -27524 | -47926 | 28172 | 27545 | 1981/1900 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9910 | +3.1% | 31109 | 35018 | -15728 | -27386 | 18755 | 17658 | 4292/4090 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17343 | +3.1% | 54441 | 61282 | -27524 | -47926 | 32822 | 30902 | 4292/4090 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31132 | +6.0% | 83756 | 87289 | -37324 | -36514 | 9280 | 8237 | 3311/3154 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 54482 | +6.0% | 146574 | 152756 | -65316 | -63900 | 16240 | 14414 | 3311/3154 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 6197; H7 46650 -> 49120; K7 83430 -> 96316; M7 4691 -> -11679; O7 10923 -> 7582; P7 304772 -> 301507; U7 59410 -> 49269

### TL3_SWB_A70_3deda2 (BEST-AVAILABLE-NOT-PROVEN | row vsess_80 set NE8_30a10s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11608 | +5.2% | 31109 | 32338 | -15728 | -25046 | 16098 | 16053 | 1981/1908 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20315 | +5.2% | 54441 | 56592 | -27524 | -43831 | 28172 | 28093 | 1981/1908 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9892 | +2.9% | 31109 | 32338 | -15728 | -25046 | 18755 | 17705 | 4292/4108 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17311 | +2.9% | 54441 | 56592 | -27524 | -43831 | 32822 | 30983 | 4292/4108 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 30076 | +2.4% | 83756 | 85519 | -37324 | -34753 | 9280 | 8977 | 3311/3190 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 52633 | +2.4% | 146574 | 149658 | -65316 | -60818 | 16240 | 15710 | 3311/3190 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 28018 | +1.8% | 91441 | 80525 | -38896 | -39335 | 4849 | 4409 | 11949/11652 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 49032 | +1.8% | 160021 | 140918 | -68068 | -68836 | 8486 | 7715 | 11949/11652 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 17192; H7 46650 -> 46782; K7 83430 -> 92320; M7 4691 -> -8345; O7 10923 -> 7010; P7 304772 -> 301435; U7 59410 -> 43241

### TL3_SWB_A70_47f89f (BEST-AVAILABLE-NOT-PROVEN | row vib_3500 set NS6_2)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 9145 | -17.1% | 31109 | 24587 | -15728 | -13400 | 16098 | 18912 | 1981/1999 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 16005 | -17.1% | 54441 | 43028 | -27524 | -23449 | 28172 | 33096 | 1981/1999 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9137 | -4.9% | 31109 | 29605 | -15728 | -15784 | 18755 | 18577 | 4292/4253 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 15990 | -4.9% | 54441 | 51809 | -27524 | -27622 | 32822 | 32510 | 4292/4253 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31958 | +8.8% | 83756 | 87240 | -37324 | -38083 | 9280 | 8292 | 3311/3298 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 55927 | +8.8% | 146574 | 152670 | -65316 | -66645 | 16240 | 14511 | 3311/3298 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 30358; H7 46650 -> 46198; K7 83430 -> 73675; M7 4691 -> -2311; O7 10923 -> 9309; P7 304772 -> 302820; U7 59410 -> 63517

### TL3_SWB_A70_586135 (BEST-AVAILABLE-NOT-PROVEN | row cdr_100 set NS4_1s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10678 | -3.2% | 31109 | 31653 | -15728 | -19404 | 16098 | 16884 | 1981/1916 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18687 | -3.2% | 54441 | 55394 | -27524 | -33958 | 28172 | 29547 | 1981/1916 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9247 | -3.8% | 31109 | 31653 | -15728 | -19404 | 18755 | 17945 | 4292/4098 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16182 | -3.8% | 54441 | 55394 | -27524 | -33958 | 32822 | 31405 | 4292/4098 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 32352 | +10.1% | 83756 | 87272 | -37324 | -35315 | 9280 | 8423 | 3311/3169 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 56615 | +10.1% | 146574 | 152725 | -65316 | -61801 | 16240 | 14740 | 3311/3169 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 11965; H7 46650 -> 44389; K7 83430 -> 91444; M7 4691 -> -7235; O7 10923 -> 7010; P7 304772 -> 301036; U7 59410 -> 57431

### TL3_SWB_A70_b52de8 (BEST-AVAILABLE-NOT-PROVEN | row tm2700 set Gk5k5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11596 | +5.1% | 31109 | 33711 | -15728 | -27386 | 16098 | 15809 | 1981/1912 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20292 | +5.1% | 54441 | 58994 | -27524 | -47926 | 28172 | 27665 | 1981/1912 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9716 | +1.1% | 31109 | 33711 | -15728 | -27386 | 18755 | 17752 | 4292/4087 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17003 | +1.1% | 54441 | 58994 | -27524 | -47926 | 32822 | 31066 | 4292/4087 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 30152 | +2.7% | 83756 | 85552 | -37324 | -33685 | 9280 | 8433 | 3311/3151 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 52766 | +2.7% | 146574 | 149715 | -65316 | -58949 | 16240 | 14758 | 3311/3151 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 16893; H7 46650 -> 46782; K7 83430 -> 89944; M7 4691 -> -9777; O7 10923 -> 7010; P7 304772 -> 301658; U7 59410 -> 48318

### TL3_SWB_A70_bb72ac (BEST-AVAILABLE-NOT-PROVEN | row vrb_1200 set Gk10k2)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11567 | +4.8% | 31109 | 33830 | -15728 | -22277 | 16098 | 16211 | 1981/1914 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20241 | +4.8% | 54441 | 59203 | -27524 | -38985 | 28172 | 28369 | 1981/1914 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9847 | +2.4% | 31109 | 33830 | -15728 | -22277 | 18755 | 17911 | 4292/4092 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17232 | +2.4% | 54441 | 59203 | -27524 | -38985 | 32822 | 31344 | 4292/4092 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 32173 | +9.5% | 83756 | 88311 | -37324 | -35372 | 9280 | 8363 | 3311/3161 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 56302 | +9.5% | 146574 | 154544 | -65316 | -61901 | 16240 | 14636 | 3311/3161 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 17893; H7 46650 -> 47139; K7 83430 -> 87950; M7 4691 -> -8853; O7 10923 -> 6275; P7 304772 -> 305113; U7 59410 -> 49616

### TL3_SWB_A70_d23a42 (BEST-AVAILABLE-NOT-PROVEN | row dib_10000 set NS3_2s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11367 | +3.0% | 31109 | 32516 | -15728 | -27059 | 16098 | 15841 | 1981/1898 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19893 | +3.0% | 54441 | 56903 | -27524 | -47354 | 28172 | 27722 | 1981/1898 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9659 | +0.5% | 31109 | 32516 | -15728 | -27059 | 18755 | 17637 | 4292/4080 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16903 | +0.5% | 54441 | 56903 | -27524 | -47354 | 32822 | 30864 | 4292/4080 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31471 | +7.1% | 83756 | 85170 | -37324 | -35315 | 9280 | 8114 | 3311/3141 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 55075 | +7.1% | 146574 | 149048 | -65316 | -61801 | 16240 | 14199 | 3311/3141 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 29615 | +7.6% | 91441 | 85395 | -38896 | -36118 | 4849 | 4256 | 11949/11457 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 51825 | +7.6% | 160021 | 149440 | -68068 | -63206 | 8486 | 7448 | 11949/11457 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 11301; H7 46650 -> 46782; K7 83430 -> 94480; M7 4691 -> -9598; O7 10923 -> 7061; P7 304772 -> 299909; U7 59410 -> 47758

### TL3_SWB_A70_e02516 (BEST-AVAILABLE-NOT-PROVEN | row tm420 set Gk10k2)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11736 | +6.4% | 31109 | 35665 | -15728 | -18243 | 16098 | 16143 | 1981/1895 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20539 | +6.4% | 54441 | 62414 | -27524 | -31926 | 28172 | 28251 | 1981/1895 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9885 | +2.8% | 31109 | 35665 | -15728 | -18243 | 18755 | 18347 | 4292/4111 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17299 | +2.8% | 54441 | 62414 | -27524 | -31926 | 32822 | 32108 | 4292/4111 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 32545 | +10.8% | 83756 | 88038 | -37324 | -36429 | 9280 | 8298 | 3311/3168 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 56953 | +10.8% | 146574 | 154066 | -65316 | -63751 | 16240 | 14522 | 3311/3168 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 25020; H7 46650 -> 48031; K7 83430 -> 83136; M7 4691 -> -3690; O7 10923 -> 6740; P7 304772 -> 305544; U7 59410 -> 52208

### TL3_SWB_A70_f19d8f (BEST-AVAILABLE-NOT-PROVEN | row tsf_5_200 set Gk10t5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11706 | +6.1% | 31109 | 33868 | -15728 | -23086 | 16098 | 16283 | 1981/1906 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20485 | +6.1% | 54441 | 59268 | -27524 | -40401 | 28172 | 28495 | 1981/1906 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9819 | +2.2% | 31109 | 33868 | -15728 | -23086 | 18755 | 17761 | 4292/4100 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17183 | +2.2% | 54441 | 59268 | -27524 | -40401 | 32822 | 31082 | 4292/4100 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 32704 | +11.3% | 83756 | 89939 | -37324 | -37604 | 9280 | 8445 | 3311/3156 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 57232 | +11.3% | 146574 | 157394 | -65316 | -65808 | 16240 | 14778 | 3311/3156 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 6056; H7 46650 -> 48059; K7 83430 -> 94625; M7 4691 -> -8600; O7 10923 -> 6275; P7 304772 -> 303725; U7 59410 -> 50984

### TL3_SWB_A70_f306e1 (BEST-AVAILABLE-NOT-PROVEN | row vsess_80 set NE8_30a30s)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11608 | +5.2% | 31109 | 32338 | -15728 | -25046 | 16098 | 16053 | 1981/1908 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20315 | +5.2% | 54441 | 56592 | -27524 | -43831 | 28172 | 28093 | 1981/1908 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9877 | +2.8% | 31109 | 32338 | -15728 | -25046 | 18755 | 17797 | 4292/4107 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17284 | +2.8% | 54441 | 56592 | -27524 | -43831 | 32822 | 31145 | 4292/4107 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 30020 | +2.2% | 83756 | 85519 | -37324 | -34753 | 9280 | 9132 | 3311/3196 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 52535 | +2.2% | 146574 | 149658 | -65316 | -60818 | 16240 | 15981 | 3311/3196 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27998 | +1.7% | 91441 | 80421 | -38896 | -38130 | 4849 | 4453 | 11949/11649 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 48997 | +1.7% | 160021 | 140737 | -68068 | -66727 | 8486 | 7793 | 11949/11649 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 19680; H7 46650 -> 46782; K7 83430 -> 92320; M7 4691 -> -8345; O7 10923 -> 7010; P7 304772 -> 301435; U7 59410 -> 43241

### TL3_SWB_H70_02d9c0 (BEST-AVAILABLE-NOT-PROVEN | row lbrk_5_20 set NHc)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11237 | +1.8% | 31109 | 31474 | -15728 | -16542 | 16098 | 15782 | 1981/1933 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19666 | +1.8% | 54441 | 55080 | -27524 | -28949 | 28172 | 27618 | 1981/1933 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9224 | -4.0% | 31109 | 31474 | -15728 | -16542 | 18755 | 18028 | 4292/4200 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16142 | -4.0% | 54441 | 55080 | -27524 | -28949 | 32822 | 31549 | 4292/4200 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29662 | +1.0% | 83756 | 83053 | -37324 | -37485 | 9280 | 10043 | 3311/3268 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51909 | +1.0% | 146574 | 145343 | -65316 | -65599 | 16240 | 17574 | 3311/3268 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 17191; H7 46650 -> 22372; K7 83430 -> 96491; M7 4691 -> -1750; O7 10923 -> 9397; P7 304772 -> 302786; U7 59410 -> 61807

### TL3_SWB_H70_084e20 (BEST-AVAILABLE-NOT-PROVEN | row cusum_14 set G30_80k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 9546 | -13.5% | 31109 | 27324 | -15728 | -15146 | 16098 | 17144 | 1981/2031 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 16706 | -13.5% | 54441 | 47817 | -27524 | -26505 | 28172 | 30002 | 1981/2031 |
| L6M | 6/6 | $4.84 base lots | 9612 | 8639 | -10.1% | 31109 | 27766 | -15728 | -15146 | 18755 | 17577 | 4292/4339 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 15119 | -10.1% | 54441 | 48590 | -27524 | -26505 | 32822 | 30759 | 4292/4339 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 21509 | -26.8% | 83756 | 62007 | -37324 | -26128 | 9280 | 11511 | 3311/3344 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 37641 | -26.8% | 146574 | 108512 | -65316 | -45724 | 16240 | 20144 | 3311/3344 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 37433 | +36.0% | 91441 | 109947 | -38896 | -51602 | 4849 | 3412 | 11949/11807 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 65507 | +36.0% | 160021 | 192408 | -68068 | -90303 | 8486 | 5972 | 11949/11807 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 15945; H7 46650 -> 39155; K7 83430 -> 85372; M7 4691 -> -5596; O7 10923 -> 8398; P7 304772 -> 292406; U7 59410 -> 61439

### TL3_SWB_H70_1a4fbf (BEST-AVAILABLE-NOT-PROVEN | row tick_500 set NH12_34e50)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 9879 | -10.5% | 31109 | 27862 | -15728 | -16316 | 16098 | 17986 | 1981/2017 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 17288 | -10.5% | 54441 | 48758 | -27524 | -28553 | 28172 | 31476 | 1981/2017 |
| L6M | 6/6 | $4.84 base lots | 9612 | 8312 | -13.5% | 31109 | 27862 | -15728 | -16316 | 18755 | 18298 | 4292/4311 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 14546 | -13.5% | 54441 | 48758 | -27524 | -28553 | 32822 | 32022 | 4292/4311 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 23525 | -19.9% | 83756 | 72664 | -37324 | -26609 | 9280 | 11322 | 3311/3379 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 41168 | -19.9% | 146574 | 127162 | -65316 | -46566 | 16240 | 19814 | 3311/3379 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 14597; H7 46650 -> 37493; K7 83430 -> 99078; M7 4691 -> 4587; O7 10923 -> 6569; P7 304772 -> 290819; U7 59410 -> 63503

### TL3_SWB_H70_2e1eac (BEST-AVAILABLE-NOT-PROVEN | row vsess_50 set NH9_26e200)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10852 | -1.7% | 31109 | 29428 | -15728 | -16140 | 16098 | 16183 | 1981/1982 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18991 | -1.7% | 54441 | 51499 | -27524 | -28244 | 28172 | 28321 | 1981/1982 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9293 | -3.3% | 31109 | 29428 | -15728 | -16140 | 18755 | 18337 | 4292/4242 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16263 | -3.3% | 54441 | 51499 | -27524 | -28244 | 32822 | 32089 | 4292/4242 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27857 | -5.2% | 83756 | 80281 | -37324 | -27900 | 9280 | 10647 | 3311/3338 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48750 | -5.2% | 146574 | 140491 | -65316 | -48825 | 16240 | 18632 | 3311/3338 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 19038; H7 46650 -> 48270; K7 83430 -> 88636; M7 4691 -> 2098; O7 10923 -> 2943; P7 304772 -> 292449; U7 59410 -> 63808

### TL3_SWB_H70_303b01 (BEST-AVAILABLE-NOT-PROVEN | row dlt_100 set G12_34t5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11226 | +1.7% | 31109 | 30835 | -15728 | -14249 | 16098 | 16324 | 1981/1950 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19646 | +1.7% | 54441 | 53961 | -27524 | -24936 | 28172 | 28568 | 1981/1950 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9010 | -6.3% | 31109 | 30835 | -15728 | -14249 | 18755 | 18712 | 4292/4224 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 15768 | -6.3% | 54441 | 53961 | -27524 | -24936 | 32822 | 32745 | 4292/4224 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31511 | +7.3% | 83756 | 80119 | -37324 | -36517 | 9280 | 8613 | 3311/3263 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 55144 | +7.3% | 146574 | 140208 | -65316 | -63905 | 16240 | 15072 | 3311/3263 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 17191; H7 46650 -> 24069; K7 83430 -> 98053; M7 4691 -> 10488; O7 10923 -> 8611; P7 304772 -> 301586; U7 59410 -> 66964

### TL3_SWB_H70_5f4340 (BEST-AVAILABLE-NOT-PROVEN | row mom_28 set NH12_34e50)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10672 | -3.3% | 31109 | 30321 | -15728 | -14509 | 16098 | 18203 | 1981/2011 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18675 | -3.3% | 54441 | 53062 | -27524 | -25391 | 28172 | 31856 | 1981/2011 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9549 | -0.7% | 31109 | 30321 | -15728 | -14509 | 18755 | 18483 | 4292/4281 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16711 | -0.7% | 54441 | 53062 | -27524 | -25391 | 32822 | 32345 | 4292/4281 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 25969 | -11.6% | 83756 | 67558 | -37324 | -27185 | 9280 | 10789 | 3311/3383 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 45446 | -11.6% | 146574 | 118227 | -65316 | -47574 | 16240 | 18881 | 3311/3383 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 36872 | +33.9% | 91441 | 106458 | -38896 | -40640 | 4849 | 3384 | 11949/11962 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 64526 | +33.9% | 160021 | 186301 | -68068 | -71121 | 8486 | 5923 | 11949/11962 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 13795; H7 46650 -> 52106; K7 83430 -> 101178; M7 4691 -> 2646; O7 10923 -> 6564; P7 304772 -> 293092; U7 59410 -> 51938

### TL3_SWB_H70_7984f9 (BEST-AVAILABLE-NOT-PROVEN | row swing_pct_12 set NH45_120e50)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11283 | +2.2% | 31109 | 31721 | -15728 | -14407 | 16098 | 15659 | 1981/1939 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19744 | +2.2% | 54441 | 55512 | -27524 | -25213 | 28172 | 27403 | 1981/1939 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9194 | -4.3% | 31109 | 31721 | -15728 | -14407 | 18755 | 17932 | 4292/4175 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16090 | -4.3% | 54441 | 55512 | -27524 | -25213 | 32822 | 31381 | 4292/4175 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31381 | +6.8% | 83756 | 81158 | -37324 | -35095 | 9280 | 9423 | 3311/3268 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 54917 | +6.8% | 146574 | 142026 | -65316 | -61416 | 16240 | 16490 | 3311/3268 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 17191; H7 46650 -> 21971; K7 83430 -> 97195; M7 4691 -> 7088; O7 10923 -> 9377; P7 304772 -> 298486; U7 59410 -> 54259

### TL3_SWB_H70_81aa8b (BEST-AVAILABLE-NOT-PROVEN | row vnorm_80 set NH45_120e50)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11661 | +5.7% | 31109 | 33186 | -15728 | -16542 | 16098 | 14431 | 1981/1915 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20406 | +5.7% | 54441 | 58076 | -27524 | -28949 | 28172 | 25254 | 1981/1915 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9501 | -1.2% | 31109 | 33186 | -15728 | -16542 | 18755 | 16945 | 4292/4158 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16626 | -1.2% | 54441 | 58076 | -27524 | -28949 | 32822 | 29655 | 4292/4158 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31735 | +8.0% | 83756 | 89454 | -37324 | -36565 | 9280 | 9962 | 3311/3279 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 55536 | +8.0% | 146574 | 156545 | -65316 | -63988 | 16240 | 17433 | 3311/3279 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 17216; H7 46650 -> 4710; K7 83430 -> 88161; M7 4691 -> 4402; O7 10923 -> 10144; P7 304772 -> 298784; U7 59410 -> 55458

### TL3_SWB_H70_843d26 (BEST-AVAILABLE-NOT-PROVEN | row tib_1200 set B)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10449 | -5.3% | 31109 | 30401 | -15728 | -17185 | 16098 | 17249 | 1981/1988 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18286 | -5.3% | 54441 | 53202 | -27524 | -30075 | 28172 | 30185 | 1981/1988 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9013 | -6.2% | 31109 | 30401 | -15728 | -17185 | 18755 | 18920 | 4292/4284 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 15772 | -6.2% | 54441 | 53202 | -27524 | -30075 | 32822 | 33111 | 4292/4284 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 25730 | -12.4% | 83756 | 70774 | -37324 | -26229 | 9280 | 10773 | 3311/3333 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 45027 | -12.4% | 146574 | 123855 | -65316 | -45900 | 16240 | 18853 | 3311/3333 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 16584; H7 46650 -> 44975; K7 83430 -> 101445; M7 4691 -> 8021; O7 10923 -> 4732; P7 304772 -> 297054; U7 59410 -> 60113

### TL3_SWB_H70_8f9967 (BEST-AVAILABLE-NOT-PROVEN | row vnorm_250 set NH12_34e50)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11320 | +2.6% | 31109 | 33155 | -15728 | -17051 | 16098 | 15672 | 1981/1952 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19811 | +2.6% | 54441 | 58021 | -27524 | -29840 | 28172 | 27426 | 1981/1952 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9346 | -2.8% | 31109 | 33155 | -15728 | -17051 | 18755 | 18686 | 4292/4246 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16356 | -2.8% | 54441 | 58021 | -27524 | -29840 | 32822 | 32700 | 4292/4246 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 28228 | -3.9% | 83756 | 81286 | -37324 | -32928 | 9280 | 11066 | 3311/3347 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 49399 | -3.9% | 146574 | 142251 | -65316 | -57623 | 16240 | 19365 | 3311/3347 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 17632; H7 46650 -> 46209; K7 83430 -> 86119; M7 4691 -> 6138; O7 10923 -> 8032; P7 304772 -> 302078; U7 59410 -> 60364

### TL3_SWB_H70_aa35a9 (BEST-AVAILABLE-NOT-PROVEN | row tm30 set G30_80k5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10929 | -1.0% | 31109 | 33159 | -15728 | -19169 | 16098 | 15920 | 1981/1976 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19126 | -1.0% | 54441 | 58028 | -27524 | -33545 | 28172 | 27860 | 1981/1976 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9170 | -4.6% | 31109 | 33159 | -15728 | -19169 | 18755 | 19303 | 4292/4292 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16048 | -4.6% | 54441 | 58028 | -27524 | -33545 | 32822 | 33781 | 4292/4292 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29655 | +1.0% | 83756 | 83519 | -37324 | -35099 | 9280 | 10581 | 3311/3325 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51895 | +1.0% | 146574 | 146159 | -65316 | -61423 | 16240 | 18517 | 3311/3325 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18012; H7 46650 -> 38624; K7 83430 -> 102416; M7 4691 -> 7521; O7 10923 -> 7493; P7 304772 -> 301884; U7 59410 -> 67677

### TL3_SWB_H70_b52194 (BEST-AVAILABLE-NOT-PROVEN | row swing_pct_12 set NH9_26e50)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10441 | -5.4% | 31109 | 30766 | -15728 | -10556 | 16098 | 16102 | 1981/1946 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18273 | -5.4% | 54441 | 53840 | -27524 | -18474 | 28172 | 28179 | 1981/1946 |
| L6M | 6/6 | $4.84 base lots | 9612 | 8619 | -10.3% | 31109 | 30766 | -15728 | -10556 | 18755 | 19165 | 4292/4262 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 15083 | -10.3% | 54441 | 53840 | -27524 | -18474 | 32822 | 33538 | 4292/4262 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31403 | +6.9% | 83756 | 81890 | -37324 | -35095 | 9280 | 9058 | 3311/3288 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 54956 | +6.9% | 146574 | 143307 | -65316 | -61416 | 16240 | 15851 | 3311/3288 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27109 | -1.5% | 91441 | 80127 | -38896 | -42621 | 4849 | 4261 | 11949/11740 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 47442 | -1.5% | 160021 | 140221 | -68068 | -74586 | 8486 | 7457 | 11949/11740 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 17191; H7 46650 -> 45005; K7 83430 -> 88260; M7 4691 -> 10484; O7 10923 -> 9248; P7 304772 -> 300761; U7 59410 -> 68163

### TL3_SWB_H70_f497fe (BEST-AVAILABLE-NOT-PROVEN | row swing_pct_8 set NH9_26e200)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10665 | -3.4% | 31109 | 30594 | -15728 | -20148 | 16098 | 15564 | 1981/1953 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18664 | -3.4% | 54441 | 53539 | -27524 | -35260 | 28172 | 27237 | 1981/1953 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9275 | -3.5% | 31109 | 30594 | -15728 | -20148 | 18755 | 18167 | 4292/4244 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16231 | -3.5% | 54441 | 53539 | -27524 | -35260 | 32822 | 31792 | 4292/4244 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31629 | +7.7% | 83756 | 83175 | -37324 | -35999 | 9280 | 10518 | 3311/3275 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 55350 | +7.7% | 146574 | 145557 | -65316 | -62998 | 16240 | 18406 | 3311/3275 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 19683; H7 46650 -> 37132; K7 83430 -> 81389; M7 4691 -> -3020; O7 10923 -> 9106; P7 304772 -> 298420; U7 59410 -> 69566

### TL3_SWB_H73_094228 (BEST-AVAILABLE-NOT-PROVEN | row urenko_28 set G30_80k5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11342 | +2.8% | 31109 | 32989 | -15728 | -15845 | 16098 | 16061 | 1981/1972 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19848 | +2.8% | 54441 | 57731 | -27524 | -27729 | 28172 | 28107 | 1981/1972 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9822 | +2.2% | 31109 | 32989 | -15728 | -15845 | 18755 | 18738 | 4292/4277 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17189 | +2.2% | 54441 | 57731 | -27524 | -27729 | 32822 | 32791 | 4292/4277 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27683 | -5.8% | 83756 | 84367 | -37324 | -36139 | 9280 | 9760 | 3311/3289 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48445 | -5.8% | 146574 | 147642 | -65316 | -63243 | 16240 | 17080 | 3311/3289 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44920; K7 83430 -> 84629; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_0fde34 (BEST-AVAILABLE-NOT-PROVEN | row rng_112 set NH20_55e50)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11527 | +4.5% | 31109 | 33409 | -15728 | -15845 | 16098 | 15739 | 1981/1972 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20172 | +4.5% | 54441 | 58466 | -27524 | -27729 | 28172 | 27543 | 1981/1972 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9996 | +4.0% | 31109 | 33409 | -15728 | -15845 | 18755 | 18307 | 4292/4284 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17493 | +4.0% | 54441 | 58466 | -27524 | -27729 | 32822 | 32038 | 4292/4284 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27763 | -5.5% | 83756 | 83172 | -37324 | -36139 | 9280 | 9994 | 3311/3290 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48585 | -5.5% | 146574 | 145551 | -65316 | -63243 | 16240 | 17490 | 3311/3290 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 34820; K7 83430 -> 83132; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_4c1b7c (BEST-AVAILABLE-NOT-PROVEN | row tm300 set NH20_55e50)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10990 | -0.4% | 31109 | 31109 | -15728 | -15728 | 16098 | 16139 | 1981/1983 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19233 | -0.4% | 54441 | 54441 | -27524 | -27524 | 28172 | 28242 | 1981/1983 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9571 | -0.4% | 31109 | 31109 | -15728 | -15728 | 18755 | 18903 | 4292/4297 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16749 | -0.4% | 54441 | 54441 | -27524 | -27524 | 32822 | 33081 | 4292/4297 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29352 | -0.1% | 83756 | 84732 | -37324 | -37404 | 9280 | 9108 | 3311/3302 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51366 | -0.1% | 146574 | 148280 | -65316 | -65456 | 16240 | 15938 | 3311/3302 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 26031 | -5.5% | 91441 | 87845 | -38896 | -39076 | 4849 | 4897 | 11949/11945 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 45554 | -5.5% | 160021 | 153729 | -68068 | -68383 | 8486 | 8569 | 11949/11945 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 50671; K7 83430 -> 83430; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_57607b (BEST-AVAILABLE-NOT-PROVEN | row vol_6000 set A)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11283 | +2.2% | 31109 | 32009 | -15728 | -15845 | 16098 | 15639 | 1981/1975 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19745 | +2.2% | 54441 | 56016 | -27524 | -27729 | 28172 | 27368 | 1981/1975 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9790 | +1.9% | 31109 | 32009 | -15728 | -15845 | 18755 | 18739 | 4292/4279 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17133 | +1.9% | 54441 | 56016 | -27524 | -27729 | 32822 | 32793 | 4292/4279 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 28001 | -4.7% | 83756 | 84367 | -37324 | -36139 | 9280 | 9761 | 3311/3287 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 49001 | -4.7% | 146574 | 147642 | -65316 | -63243 | 16240 | 17082 | 3311/3287 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46455; K7 83430 -> 83132; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_9af800 (BEST-AVAILABLE-NOT-PROVEN | row wrenko_28 set NH30_80e200)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11274 | +2.2% | 31109 | 32009 | -15728 | -16223 | 16098 | 15449 | 1981/1979 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19730 | +2.2% | 54441 | 56016 | -27524 | -28391 | 28172 | 27036 | 1981/1979 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9770 | +1.6% | 31109 | 32009 | -15728 | -16223 | 18755 | 18521 | 4292/4287 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17098 | +1.6% | 54441 | 56016 | -27524 | -28391 | 32822 | 32412 | 4292/4287 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27389 | -6.8% | 83756 | 82926 | -37324 | -35598 | 9280 | 9851 | 3311/3322 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 47930 | -6.8% | 146574 | 145121 | -65316 | -62297 | 16240 | 17240 | 3311/3322 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 37528; K7 83430 -> 85585; M7 4691 -> 5320; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_a0aff8 (BEST-AVAILABLE-NOT-PROVEN | row dib_25000 set G12_34k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11214 | +1.6% | 31109 | 32009 | -15728 | -16301 | 16098 | 16090 | 1981/1985 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19625 | +1.6% | 54441 | 56016 | -27524 | -28526 | 28172 | 28157 | 1981/1985 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9795 | +1.9% | 31109 | 32009 | -15728 | -16301 | 18755 | 18808 | 4292/4298 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17141 | +1.9% | 54441 | 56016 | -27524 | -28526 | 32822 | 32914 | 4292/4298 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27939 | -4.9% | 83756 | 85837 | -37324 | -36139 | 9280 | 9620 | 3311/3304 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48894 | -4.9% | 146574 | 150214 | -65316 | -63243 | 16240 | 16835 | 3311/3304 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 26786 | -2.7% | 91441 | 95181 | -38896 | -37720 | 4849 | 4898 | 11949/11908 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 46875 | -2.7% | 160021 | 166567 | -68068 | -66010 | 8486 | 8571 | 11949/11908 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46892; K7 83430 -> 84629; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_abd77f (BEST-AVAILABLE-NOT-PROVEN | row vsess_200 set A)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11130 | +0.9% | 31109 | 31159 | -15728 | -15503 | 16098 | 16074 | 1981/1982 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19477 | +0.9% | 54441 | 54529 | -27524 | -27130 | 28172 | 28130 | 1981/1982 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9683 | +0.7% | 31109 | 31159 | -15728 | -15503 | 18755 | 18760 | 4292/4297 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16944 | +0.7% | 54441 | 54529 | -27524 | -27130 | 32822 | 32829 | 4292/4297 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29307 | -0.2% | 83756 | 85967 | -37324 | -36139 | 9280 | 9229 | 3311/3298 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51287 | -0.2% | 146574 | 150442 | -65316 | -63243 | 16240 | 16150 | 3311/3298 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 45587; K7 83430 -> 84629; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_b50e21 (BEST-AVAILABLE-NOT-PROVEN | row drb_2000 set B)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11173 | +1.3% | 31109 | 31129 | -15728 | -15845 | 16098 | 15792 | 1981/1972 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19553 | +1.3% | 54441 | 54476 | -27524 | -27729 | 28172 | 27635 | 1981/1972 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9757 | +1.5% | 31109 | 31129 | -15728 | -15845 | 18755 | 18666 | 4292/4276 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17074 | +1.5% | 54441 | 54476 | -27524 | -27729 | 32822 | 32665 | 4292/4276 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27703 | -5.7% | 83756 | 83457 | -37324 | -35229 | 9280 | 9519 | 3311/3286 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48481 | -5.7% | 146574 | 146049 | -65316 | -61650 | 16240 | 16658 | 3311/3286 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 43796; K7 83430 -> 82848; M7 4691 -> 4979; O7 10923 -> 10923; P7 304772 -> 305444; U7 59410 -> 59410

### TL3_SWB_H73_bcd8fd (BEST-AVAILABLE-NOT-PROVEN | row trend_28 set G30_80k1)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11274 | +2.2% | 31109 | 32009 | -15728 | -16223 | 16098 | 15449 | 1981/1979 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19730 | +2.2% | 54441 | 56016 | -27524 | -28391 | 28172 | 27036 | 1981/1979 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9770 | +1.6% | 31109 | 32009 | -15728 | -16223 | 18755 | 18521 | 4292/4287 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17098 | +1.6% | 54441 | 56016 | -27524 | -28391 | 32822 | 32412 | 4292/4287 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27389 | -6.8% | 83756 | 82926 | -37324 | -35598 | 9280 | 9851 | 3311/3322 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 47930 | -6.8% | 146574 | 145121 | -65316 | -62297 | 16240 | 17240 | 3311/3322 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 37528; K7 83430 -> 85585; M7 4691 -> 5320; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_cf8470 (BEST-AVAILABLE-NOT-PROVEN | row drb_2000 set G20_55k5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11173 | +1.3% | 31109 | 31129 | -15728 | -15845 | 16098 | 15792 | 1981/1972 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19553 | +1.3% | 54441 | 54476 | -27524 | -27729 | 28172 | 27635 | 1981/1972 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9757 | +1.5% | 31109 | 31129 | -15728 | -15845 | 18755 | 18666 | 4292/4276 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17074 | +1.5% | 54441 | 54476 | -27524 | -27729 | 32822 | 32665 | 4292/4276 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27703 | -5.7% | 83756 | 83457 | -37324 | -35229 | 9280 | 9519 | 3311/3286 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48481 | -5.7% | 146574 | 146049 | -65316 | -61650 | 16240 | 16658 | 3311/3286 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 43796; K7 83430 -> 82848; M7 4691 -> 4979; O7 10923 -> 10923; P7 304772 -> 305444; U7 59410 -> 59410

### TL3_SWB_H73_de0ce8 (BEST-AVAILABLE-NOT-PROVEN | row mrenko_28 set B)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11691 | +5.9% | 31109 | 32984 | -15728 | -15845 | 16098 | 15176 | 1981/1969 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20458 | +5.9% | 54441 | 57721 | -27524 | -27729 | 28172 | 26557 | 1981/1969 |
| L6M | 6/6 | $4.84 base lots | 9612 | 10174 | +5.8% | 31109 | 32984 | -15728 | -15845 | 18755 | 18061 | 4292/4272 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17804 | +5.8% | 54441 | 57721 | -27524 | -27729 | 32822 | 31607 | 4292/4272 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27699 | -5.7% | 83756 | 84367 | -37324 | -36139 | 9280 | 9519 | 3311/3287 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48473 | -5.7% | 146574 | 147642 | -65316 | -63243 | 16240 | 16658 | 3311/3287 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 31734; K7 83430 -> 79536; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_f45dbe (BEST-AVAILABLE-NOT-PROVEN | row tm300 set NHc)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10990 | -0.4% | 31109 | 31109 | -15728 | -15728 | 16098 | 16139 | 1981/1983 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19233 | -0.4% | 54441 | 54441 | -27524 | -27524 | 28172 | 28242 | 1981/1983 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9571 | -0.4% | 31109 | 31109 | -15728 | -15728 | 18755 | 18903 | 4292/4297 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16749 | -0.4% | 54441 | 54441 | -27524 | -27524 | 32822 | 33081 | 4292/4297 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29352 | -0.1% | 83756 | 84732 | -37324 | -37404 | 9280 | 9141 | 3311/3303 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51366 | -0.1% | 146574 | 148280 | -65316 | -65456 | 16240 | 15997 | 3311/3303 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 26308 | -4.5% | 91441 | 87845 | -38896 | -39076 | 4849 | 4880 | 11949/11948 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 46038 | -4.5% | 160021 | 153729 | -68068 | -68383 | 8486 | 8540 | 11949/11948 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 50671; K7 83430 -> 83430; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_f9241c (BEST-AVAILABLE-NOT-PROVEN | row dib_70000 set G12_34k3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11422 | +3.5% | 31109 | 32009 | -15728 | -15845 | 16098 | 15749 | 1981/1969 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19989 | +3.5% | 54441 | 56016 | -27524 | -27729 | 28172 | 27560 | 1981/1969 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9902 | +3.0% | 31109 | 32009 | -15728 | -15845 | 18755 | 18697 | 4292/4266 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17329 | +3.0% | 54441 | 56016 | -27524 | -27729 | 32822 | 32719 | 4292/4266 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27065 | -7.9% | 83756 | 82188 | -37324 | -33960 | 9280 | 9635 | 3311/3282 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 47363 | -7.9% | 146574 | 143830 | -65316 | -59431 | 16240 | 16862 | 3311/3282 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 44447; K7 83430 -> 83958; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_fac98a (BEST-AVAILABLE-NOT-PROVEN | row vol_6000 set G20_55t5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11283 | +2.2% | 31109 | 32009 | -15728 | -15845 | 16098 | 15639 | 1981/1975 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19745 | +2.2% | 54441 | 56016 | -27524 | -27729 | 28172 | 27368 | 1981/1975 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9790 | +1.9% | 31109 | 32009 | -15728 | -15845 | 18755 | 18739 | 4292/4279 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17133 | +1.9% | 54441 | 56016 | -27524 | -27729 | 32822 | 32793 | 4292/4279 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 28001 | -4.7% | 83756 | 84367 | -37324 | -36139 | 9280 | 9761 | 3311/3287 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 49001 | -4.7% | 146574 | 147642 | -65316 | -63243 | 16240 | 17082 | 3311/3287 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46455; K7 83430 -> 83132; M7 4691 -> 4691; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_H73_ff8c5b (BEST-AVAILABLE-NOT-PROVEN | row dlt_150 set NHc)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11023 | -0.1% | 31109 | 31134 | -15728 | -14970 | 16098 | 15834 | 1981/1984 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19291 | -0.1% | 54441 | 54485 | -27524 | -26197 | 28172 | 27709 | 1981/1984 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9669 | +0.6% | 31109 | 31134 | -15728 | -14970 | 18755 | 18535 | 4292/4291 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16920 | +0.6% | 54441 | 54485 | -27524 | -26197 | 32822 | 32436 | 4292/4291 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 28120 | -4.3% | 83756 | 84367 | -37324 | -36139 | 9280 | 9548 | 3311/3299 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 49210 | -4.3% | 146574 | 147642 | -65316 | -63243 | 16240 | 16710 | 3311/3299 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 37854; K7 83430 -> 85511; M7 4691 -> 5453; O7 10923 -> 10923; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_O73_06c1ce (BEST-AVAILABLE-NOT-PROVEN | row tm420 set NO930_12)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10986 | -0.4% | 31109 | 30641 | -15728 | -16314 | 16098 | 15635 | 1981/1959 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19226 | -0.4% | 54441 | 53621 | -27524 | -28549 | 28172 | 27362 | 1981/1959 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9589 | -0.2% | 31109 | 30641 | -15728 | -16314 | 18755 | 18454 | 4292/4261 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16780 | -0.2% | 54441 | 53621 | -27524 | -28549 | 32822 | 32295 | 4292/4261 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 32512 | +10.7% | 83756 | 87230 | -37324 | -40797 | 9280 | 8439 | 3311/3276 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 56895 | +10.7% | 146574 | 152653 | -65316 | -71396 | 16240 | 14768 | 3311/3276 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 83554; M7 4691 -> 5470; O7 10923 -> 1106; P7 304772 -> 305444; U7 59410 -> 59410

### TL3_SWB_O73_0af78b (BEST-AVAILABLE-NOT-PROVEN | row kagi_40 set NO830_12)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11835 | +7.2% | 31109 | 33800 | -15728 | -19398 | 16098 | 15935 | 1981/1989 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20711 | +7.2% | 54441 | 59151 | -27524 | -33947 | 28172 | 27886 | 1981/1989 |
| L6M | 6/6 | $4.84 base lots | 9612 | 10092 | +5.0% | 31109 | 33800 | -15728 | -19398 | 18755 | 18935 | 4292/4317 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17660 | +5.0% | 54441 | 59151 | -27524 | -33947 | 32822 | 33136 | 4292/4317 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29078 | -1.0% | 83756 | 83672 | -37324 | -36379 | 9280 | 9164 | 3311/3353 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 50886 | -1.0% | 146574 | 146425 | -65316 | -63663 | 16240 | 16038 | 3311/3353 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 77994; M7 4691 -> 2198; O7 10923 -> 23163; P7 304772 -> 305396; U7 59410 -> 59410

### TL3_SWB_O73_35eefb (BEST-AVAILABLE-NOT-PROVEN | row dchg_40 set NO830_12)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11835 | +7.2% | 31109 | 33800 | -15728 | -19398 | 16098 | 15935 | 1981/1989 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 20711 | +7.2% | 54441 | 59151 | -27524 | -33947 | 28172 | 27886 | 1981/1989 |
| L6M | 6/6 | $4.84 base lots | 9612 | 10092 | +5.0% | 31109 | 33800 | -15728 | -19398 | 18755 | 18935 | 4292/4317 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17660 | +5.0% | 54441 | 59151 | -27524 | -33947 | 32822 | 33136 | 4292/4317 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29078 | -1.0% | 83756 | 83672 | -37324 | -36379 | 9280 | 9164 | 3311/3353 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 50886 | -1.0% | 146574 | 146425 | -65316 | -63663 | 16240 | 16038 | 3311/3353 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 77994; M7 4691 -> 2198; O7 10923 -> 23163; P7 304772 -> 305396; U7 59410 -> 59410

### TL3_SWB_O73_3eba4c (BEST-AVAILABLE-NOT-PROVEN | row vrb_400 set NO1000_3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10986 | -0.4% | 31109 | 31109 | -15728 | -13933 | 16098 | 16715 | 1981/1993 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19226 | -0.4% | 54441 | 54441 | -27524 | -24383 | 28172 | 29252 | 1981/1993 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9619 | +0.1% | 31109 | 31109 | -15728 | -13933 | 18755 | 18964 | 4292/4310 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16833 | +0.1% | 54441 | 54441 | -27524 | -24383 | 32822 | 33187 | 4292/4310 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 28024 | -4.6% | 83756 | 80720 | -37324 | -37808 | 9280 | 9270 | 3311/3340 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 49042 | -4.6% | 146574 | 141261 | -65316 | -66165 | 16240 | 16223 | 3311/3340 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 81380; M7 4691 -> 2637; O7 10923 -> 20729; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_O73_4d5758 (BEST-AVAILABLE-NOT-PROVEN | row kagi_56 set NO930_3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10876 | -1.4% | 31109 | 30641 | -15728 | -15728 | 16098 | 18224 | 1981/1996 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19033 | -1.4% | 54441 | 53621 | -27524 | -27524 | 28172 | 31893 | 1981/1996 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9441 | -1.8% | 31109 | 30641 | -15728 | -15728 | 18755 | 19947 | 4292/4316 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16522 | -1.8% | 54441 | 53621 | -27524 | -27524 | 32822 | 34908 | 4292/4316 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 33184 | +13.0% | 83756 | 87479 | -37324 | -36653 | 9280 | 8301 | 3311/3320 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 58072 | +13.0% | 146574 | 153088 | -65316 | -64143 | 16240 | 14527 | 3311/3320 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27990 | +1.7% | 91441 | 97870 | -38896 | -38261 | 4849 | 4970 | 11949/12026 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 48983 | +1.7% | 160021 | 171273 | -68068 | -66957 | 8486 | 8698 | 11949/12026 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 47589; K7 83430 -> 92252; M7 4691 -> 6763; O7 10923 -> 30696; P7 304772 -> 305444; U7 59410 -> 59410

### TL3_SWB_O73_57dd20 (BEST-AVAILABLE-NOT-PROVEN | row tsf_10_400 set NO930_5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 11047 | +0.1% | 31109 | 31202 | -15728 | -15728 | 16098 | 16217 | 1981/1963 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19332 | +0.1% | 54441 | 54603 | -27524 | -27524 | 28172 | 28380 | 1981/1963 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9757 | +1.5% | 31109 | 31202 | -15728 | -15728 | 18755 | 18861 | 4292/4266 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 17076 | +1.5% | 54441 | 54603 | -27524 | -27524 | 32822 | 33007 | 4292/4266 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31430 | +7.0% | 83756 | 87866 | -37324 | -41433 | 9280 | 8815 | 3311/3295 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 55003 | +7.0% | 146574 | 153766 | -65316 | -72508 | 16240 | 15426 | 3311/3295 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 84673; M7 4691 -> 5470; O7 10923 -> 11002; P7 304772 -> 305444; U7 59410 -> 59410

### TL3_SWB_O73_58aa1f (BEST-AVAILABLE-NOT-PROVEN | row vib_700 set NO1000_5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10646 | -3.5% | 31109 | 30274 | -15728 | -14893 | 16098 | 16696 | 1981/1993 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18631 | -3.5% | 54441 | 52980 | -27524 | -26063 | 28172 | 29218 | 1981/1993 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9395 | -2.3% | 31109 | 30274 | -15728 | -14893 | 18755 | 19193 | 4292/4316 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16442 | -2.3% | 54441 | 52980 | -27524 | -26063 | 32822 | 33587 | 4292/4316 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 27536 | -6.3% | 83756 | 80617 | -37324 | -35050 | 9280 | 9540 | 3311/3350 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 48187 | -6.3% | 146574 | 141080 | -65316 | -61338 | 16240 | 16696 | 3311/3350 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 82002; M7 4691 -> 4294; O7 10923 -> 23974; P7 304772 -> 305444; U7 59410 -> 59410

### TL3_SWB_O73_68cfd2 (BEST-AVAILABLE-NOT-PROVEN | row vnorm_400 set NO930_12)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10476 | -5.1% | 31109 | 28846 | -15728 | -15728 | 16098 | 16271 | 1981/1976 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18333 | -5.1% | 54441 | 50480 | -27524 | -27524 | 28172 | 28475 | 1981/1976 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9252 | -3.7% | 31109 | 28846 | -15728 | -15728 | 18755 | 19057 | 4292/4292 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16192 | -3.7% | 54441 | 50480 | -27524 | -27524 | 32822 | 33349 | 4292/4292 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 33300 | +13.4% | 83756 | 90787 | -37324 | -40208 | 9280 | 8329 | 3311/3304 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 58275 | +13.4% | 146574 | 158878 | -65316 | -70364 | 16240 | 14575 | 3311/3304 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 83903; M7 4691 -> 5470; O7 10923 -> 17137; P7 304772 -> 305444; U7 59410 -> 59410

### TL3_SWB_O73_77799c (BEST-AVAILABLE-NOT-PROVEN | row vib_15000 set NO930_8)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10720 | -2.9% | 31109 | 28846 | -15728 | -16533 | 16098 | 16592 | 1981/1968 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18761 | -2.9% | 54441 | 50480 | -27524 | -28933 | 28172 | 29037 | 1981/1968 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9469 | -1.5% | 31109 | 28846 | -15728 | -16533 | 18755 | 18948 | 4292/4275 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16571 | -1.5% | 54441 | 50480 | -27524 | -28933 | 32822 | 33159 | 4292/4275 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31900 | +8.6% | 83756 | 85168 | -37324 | -37664 | 9280 | 8411 | 3311/3296 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 55824 | +8.6% | 146574 | 149043 | -65316 | -65913 | 16240 | 14720 | 3311/3296 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 29599 | +7.5% | 91441 | 99581 | -38896 | -38246 | 4849 | 4800 | 11949/11889 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 51799 | +7.5% | 160021 | 174266 | -68068 | -66931 | 8486 | 8400 | 11949/11889 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 83831; M7 4691 -> 3992; O7 10923 -> 14378; P7 304772 -> 306753; U7 59410 -> 59410

### TL3_SWB_O73_7a0171 (BEST-AVAILABLE-NOT-PROVEN | row cdr_100 set NO1000_5)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10642 | -3.6% | 31109 | 29927 | -15728 | -12595 | 16098 | 16884 | 1981/1996 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18623 | -3.6% | 54441 | 52373 | -27524 | -22041 | 28172 | 29548 | 1981/1996 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9322 | -3.0% | 31109 | 29927 | -15728 | -12595 | 18755 | 19468 | 4292/4327 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16314 | -3.0% | 54441 | 52373 | -27524 | -22041 | 32822 | 34069 | 4292/4327 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 29615 | +0.8% | 83756 | 84281 | -37324 | -37848 | 9280 | 9268 | 3311/3331 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 51826 | +0.8% | 146574 | 147492 | -65316 | -66235 | 16240 | 16219 | 3311/3331 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 84220; M7 4691 -> 5193; O7 10923 -> 28996; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_O73_93d721 (BEST-AVAILABLE-NOT-PROVEN | row vrb_1200 set NO930_12)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10435 | -5.4% | 31109 | 28876 | -15728 | -15728 | 16098 | 16536 | 1981/1980 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18262 | -5.4% | 54441 | 50532 | -27524 | -27524 | 28172 | 28938 | 1981/1980 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9244 | -3.8% | 31109 | 28876 | -15728 | -15728 | 18755 | 19417 | 4292/4297 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16177 | -3.8% | 54441 | 50532 | -27524 | -27524 | 32822 | 33980 | 4292/4297 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 32281 | +9.9% | 83756 | 90116 | -37324 | -40199 | 9280 | 8358 | 3311/3301 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 56491 | +9.9% | 146574 | 157704 | -65316 | -70348 | 16240 | 14626 | 3311/3301 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 83430; M7 4691 -> 4691; O7 10923 -> 28814; P7 304772 -> 304772; U7 59410 -> 59410

### TL3_SWB_O73_9707f5 (BEST-AVAILABLE-NOT-PROVEN | row dchg_56 set NO930_3)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10876 | -1.4% | 31109 | 30641 | -15728 | -15728 | 16098 | 18224 | 1981/1996 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 19033 | -1.4% | 54441 | 53621 | -27524 | -27524 | 28172 | 31893 | 1981/1996 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9441 | -1.8% | 31109 | 30641 | -15728 | -15728 | 18755 | 19947 | 4292/4316 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16522 | -1.8% | 54441 | 53621 | -27524 | -27524 | 32822 | 34908 | 4292/4316 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 33184 | +13.0% | 83756 | 87479 | -37324 | -36653 | 9280 | 8301 | 3311/3320 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 58072 | +13.0% | 146574 | 153088 | -65316 | -64143 | 16240 | 14527 | 3311/3320 |
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27990 | +1.7% | 91441 | 97870 | -38896 | -38261 | 4849 | 4970 | 11949/12026 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 48983 | +1.7% | 160021 | 171273 | -68068 | -66957 | 8486 | 8698 | 11949/12026 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 47589; K7 83430 -> 92252; M7 4691 -> 6763; O7 10923 -> 30696; P7 304772 -> 305444; U7 59410 -> 59410

### TL3_SWB_O73_fdd9da (BEST-AVAILABLE-NOT-PROVEN | row tsf_5_200 set NO930_8)

| window | months done/needed | dollar col | today ulcer | swap ulcer | change | today maxDD | swap maxDD | today worst wk | swap worst wk | today mean/wk | swap mean/wk | trades today/swap |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| L3M | 3/3 | $4.84 base lots | 11035 | 10703 | -3.0% | 31109 | 28846 | -15728 | -15728 | 16098 | 17265 | 1981/1979 |
| L3M | 3/3 | $4.84 x1.75 | 19311 | 18731 | -3.0% | 54441 | 50480 | -27524 | -27524 | 28172 | 30214 | 1981/1979 |
| L6M | 6/6 | $4.84 base lots | 9612 | 9547 | -0.7% | 31109 | 28846 | -15728 | -15728 | 18755 | 19116 | 4292/4289 |
| L6M | 6/6 | $4.84 x1.75 | 16821 | 16706 | -0.7% | 54441 | 50480 | -27524 | -27524 | 32822 | 33453 | 4292/4289 |
| HOLD | 6/6 | $4.84 base lots | 29373 | 31352 | +6.7% | 83756 | 89003 | -37324 | -39085 | 9280 | 9053 | 3311/3300 |
| HOLD | 6/6 | $4.84 x1.75 | 51403 | 54867 | +6.7% | 146574 | 155755 | -65316 | -68399 | 16240 | 15842 | 3311/3300 |

Freed-book / other-book effects (net_fee base lots, window L6M, today -> swap): A7 18691 -> 18691; H7 46650 -> 46650; K7 83430 -> 83811; M7 4691 -> 4254; O7 10923 -> 20709; P7 304772 -> 304772; U7 59410 -> 59410

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
| PRIOR | 31/31 | $4.84 base lots | 27534 | 31334 | +13.8% | 91441 | 78701 | -38896 | -40719 | 4849 | 3464 | 11949/11342 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 54834 | +13.8% | 160021 | 137727 | -68068 | -71259 | 8486 | 6061 | 11949/11342 |

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
| PRIOR | 31/31 | $4.84 base lots | 27534 | 26823 | -2.6% | 91441 | 89930 | -38896 | -41204 | 4849 | 4927 | 11949/11813 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 46940 | -2.6% | 160021 | 157377 | -68068 | -72107 | 8486 | 8622 | 11949/11813 |

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
| PRIOR | 31/31 | $4.84 base lots | 27534 | 27230 | -1.1% | 91441 | 91290 | -38896 | -41461 | 4849 | 4893 | 11949/11807 |
| PRIOR | 31/31 | $4.84 x1.75 | 48184 | 47652 | -1.1% | 160021 | 159758 | -68068 | -72557 | 8486 | 8563 | 11949/11807 |

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

