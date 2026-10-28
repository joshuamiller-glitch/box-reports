# DS3_DIV_1_MAPS - time-of-day maps and event profiles, ES RTY YM CL ZN GC 6E (+ZB, NQ reference) (D3DV1, 2026-10-28)

DESCRIPTIVE ONLY: no cells scored, no P&L, no prereg, no placebo. Research only; no live/execution/chart change; no download or purchase. Code l2vast/ds3/code/div1/ (div1_maps.py computes, build_maps_md.py + assemble_md.py write this file). Machine-readable tables: l2vast/ds3/out/div1/ (windows_pooled_<SYM>.csv, windows_by_year_<SYM>.csv, windows_by_daytype_<SYM>.csv, windows_by_period_<SYM>.csv, map_flags_<SYM>.csv, events_steps_<SYM>.csv, events_summary_<SYM>.csv, dayinfo_<SYM>.csv, windows_worth_a_rule.json).

## Method and conventions (read first)
- **Data and dates.** 1-min OHLCV from cache_te2 (Databento .v.0 volume-roll, additive back-adjust; differences within a window use the adjusted series, bps use the raw close level). Trade dates **2022-06-01 .. 2026-02-06** only (trade date = ET wall time + 6 h, so Sunday 18:00 ET belongs to Monday). The program's UNTOUCHED boundary is after 2026-02-06 (RESUME.md section 3; HOLDOUT-1 was cancelled, UNTOUCHED already read once): nothing after it enters any number. The cache arrays run to 2026-10-16, so they were loaded whole and cut by trade date in the first statement of load(); no statistic touches the cut part. Holiday and half-day sessions with < 40% of the market's median bar count are dropped; windows with < 3 bars are dropped.
- **Windows.** 96 fifteen-minute ET-clock slots (ET wall clock, so DST is handled by the tz; a slot in the 17:00-18:00 halt has no data and is absent). Window return = last close minus first open inside the slot (bps of the raw price); range = high - low (bps and ticks); volume = sum. Statistics are over trade dates (one observation per day per slot), t = mean/(sd/sqrt n); n = 916-952 days per slot.
- **Years.** 2022 = Jun-Dec, 2023, 2024, 2025 are the four consistency years ('same sign /4' counts those whose mean has the sign of the pooled mean); 2026 (Jan 1 - Feb 6) is shown with a * and not counted. Drift flag Y = |t| >= 2 pooled AND >= 3 of 4 years same sign. Extra columns sel-span t (trade dates to 2025-06-30) and late mean (2025-07-01 .. 2026-02-06) are for the section-2 agents: the 2025-07+ part overlaps the DS3 HOLD span, so a window picked here was chosen with a partial look at HOLD (see disclosures).
- **Day type.** First-hour range (anchor .. anchor+60 min, bps; anchors: equity indices 09:30, CL 09:00, ZN/ZB 08:20, GC and 6E 03:00 ET) versus the median of the PRIOR 20 trade dates (>= 10 needed): wide = trend proxy, narrow = range proxy. Windows starting before anchor+60 min cannot be conditioned without look-ahead and show '-'.
- **Events.** Profile = mean signed return and mean range in 5-min steps from -30 to +60 min, by year. London-clock events (GC fixes 10:30 and 15:00 London, 6E London close 16:00 London) use Europe/London tz so the ET time shifts correctly in the ~3 weeks per year when US and UK clocks differ. 'rng ratio' = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before. cont30 = follow-through from +5 to +35 min aligned with the sign of the first 5-min move (positive = continuation). Releases (08:30) and 13:00 are all trading days: **no economic or auction calendar is on disk**, so CL Wed 10:30 is every Wednesday (delayed-release weeks are not separated), ZN 13:00 is not restricted to auction days, and NFP is proxied by the first Friday of the month (45 events).
- **Cost column.** |mean| / round-trip cost of a one-window trade (market in and out at 1 tick adverse each + the FEES.md-based fee: 4.84, 6E 5.30; WEAK for all but ES). A drift of 0.3x cost cannot be traded as a standalone window rule.
- **Multiple comparisons.** Each market has ~92 windows; about 4 will show |t| >= 2 under a null, ~0.3 will show |t| >= 3, and windows in the same market and across ES/RTY/YM/NQ are correlated (the equity indices are one factor, so their agreement is not independent replication).

## Cross-market summary
| mkt | windows with abs t >= 2 | abs t >= 3 | year-consistent drift (Y) | EXPANSION windows (>=1.5x median range) | DEAD windows | top 3 range windows (ET start, x median) | rules listed |
|---|---|---|---|---|---|---|---|---|
| ES | 4 / 92 | 1 | 4 | 28 | 8 | 09:30(3.2x), 10:00(3.1x), 09:45(2.8x) | 8 |
| RTY | 5 / 92 | 1 | 5 | 31 | 13 | 09:30(4.7x), 10:00(3.6x), 09:45(3.6x) | 9 |
| YM | 5 / 92 | 1 | 5 | 30 | 13 | 09:30(4.2x), 10:00(3.3x), 09:45(3.2x) | 10 |
| NQ | 3 / 92 | 1 | 3 | 29 | 7 | 09:30(3.9x), 10:00(3.3x), 09:45(3.2x) | 7 |
| CL | 8 / 92 | 2 | 8 | 12 | 24 | 09:00(2.2x), 09:30(2.1x), 10:30(2.0x) | 10 |
| ZN | 10 / 92 | 2 | 9 | 12 | 10 | 08:30(3.6x), 10:00(2.4x), 09:30(2.1x) | 6 |
| ZB | 7 / 92 | 2 | 7 | 15 | 14 | 08:30(3.5x), 10:00(2.5x), 09:30(2.3x) | 6 |
| GC | 8 / 92 | 3 | 7 | 12 | 2 | 08:30(2.5x), 10:00(2.4x), 09:30(2.3x) | 10 |
| 6E | 12 / 92 | 5 | 12 | 15 | 14 | 08:30(2.7x), 10:00(2.4x), 10:45(1.8x) | 10 |

Same window in every market (mean bps, (t; years same sign of 4)):

| window (ET) | ES | RTY | YM | NQ | CL | ZN | ZB | GC | 6E |
|---|---|---|---|---|---|---|---|---|---|
| 02:45-03:00 | -0.69 (-3.5; 4/4) | -0.99 (-3.9; 4/4) | -0.89 (-4.9; 4/4) | -0.66 (-2.7; 4/4) | -1.27 (-2.5; 3/4) | +0.04 (+0.3; 3/4) | +0.00 (+0.0; 2/4) | +0.34 (+1.3; 3/4) | -0.63 (-3.4; 4/4) |
| 03:00-03:15 | +0.24 (+0.6; 1/4) | +0.50 (+1.0; 1/4) | +0.43 (+1.3; 3/4) | +0.17 (+0.4; 1/4) | -0.53 (-0.7; 3/4) | -0.35 (-2.3; 3/4) | -0.82 (-3.0; 4/4) | +0.24 (+0.7; 2/4) | +0.72 (+3.0; 4/4) |
| 08:15-08:30 | -0.13 (-0.4; 3/4) | -0.32 (-0.7; 2/4) | -0.12 (-0.5; 3/4) | +0.07 (+0.2; 2/4) | +1.17 (+1.6; 2/4) | +0.55 (+2.6; 3/4) | +0.73 (+1.9; 3/4) | +0.25 (+0.5; 3/4) | +0.03 (+0.2; 3/4) |
| 10:45-11:00 | -1.03 (-2.1; 3/4) | -0.89 (-1.3; 3/4) | -0.29 (-0.7; 2/4) | -2.25 (-3.3; 4/4) | -1.22 (-1.1; 3/4) | +0.12 (+0.7; 3/4) | +0.32 (+1.0; 2/4) | +0.13 (+0.3; 2/4) | +0.18 (+0.7; 2/4) |
| 14:00-14:15 | -0.87 (-1.7; 4/4) | -0.73 (-1.0; 4/4) | -0.52 (-1.1; 3/4) | -0.98 (-1.5; 4/4) | -2.09 (-2.5; 4/4) | -0.17 (-0.9; 4/4) | -0.32 (-1.2; 3/4) | +0.26 (+0.7; 3/4) | +0.07 (+0.3; 3/4) |
| 14:30-14:45 | +1.36 (+2.4; 4/4) | +1.77 (+2.4; 4/4) | +1.39 (+2.8; 4/4) | +1.36 (+2.0; 4/4) | +2.55 (+3.8; 4/4) | +0.03 (+0.2; 2/4) | -0.05 (-0.2; 2/4) | +0.47 (+1.1; 3/4) | +0.47 (+2.4; 4/4) |
| 15:45-16:00 | +0.75 (+1.1; 3/4) | +0.56 (+0.8; 3/4) | +0.37 (+0.7; 3/4) | +0.82 (+1.1; 3/4) | -0.40 (-0.8; 3/4) | +0.50 (+3.6; 4/4) | +0.94 (+3.4; 4/4) | -0.13 (-0.5; 3/4) | -0.04 (-0.3; 2/4) |
| 16:45-17:00 | -0.13 (-0.7; 3/4) | -0.26 (-1.0; 3/4) | -0.01 (-0.1; 2/4) | +0.08 (+0.3; 2/4) | +0.91 (+2.3; 3/4) | -0.05 (-0.6; 2/4) | -0.01 (-0.1; 2/4) | +1.04 (+4.8; 3/4) | +0.37 (+4.4; 4/4) |

Reading: (1) the two clock effects that repeat across markets are 02:45-03:00 ET (the 15 min before the London/Europe open: equity indices, CL and 6E all negative, 6E bounces at 03:00) and 14:30-14:45 ET (ES, RTY, YM, NQ, CL, 6E positive; the CL settle is 14:30). They are the first candidates for sibling replication; the equity ones are one factor. (2) Range expansion is the same everywhere: it sits on scheduled information (08:30 releases, 09:30 open, 10:00 data, 15:45-16:00 MOC, CL 09:00/09:30/10:30, ZN/ZB 08:30 and 10:00) and is stable in every year (min-year ratio >= 1.5 in the top windows). (3) The 15:45-16:00 window is the largest volume event in the equity indices (~32x the median window) with a small, positive but statistically weak drift. (4) Dead windows cluster at 00:00-01:30 ET and 22:15-00:00 ET (CL also 16:00-17:00 and 18:15-20:00; GC has only 2 dead windows; see each market); no rule belongs there. (5) Below-cost drift: most statistically significant drifts in ZN, ZB and 6E are 0.1-0.5x the round-trip cost: real in sign but not tradable as a standalone 15-min window.

## ES
Days 952 (trade dates 2022-06-01..2026-02-06); median level 5,153; anchor for the day-type split 09:30 ET (first hour 09:30-+60 min; wide = first-hour range above the prior-20-day median, 50% of days); median 15-min window range 9.8 bps; round-trip cost for a one-window trade (1 tick adverse each side + 4.84 fee) = 1.16 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 23% | 5% | +0.01 | +0.000 |
| Europe 03:00-08:00 | 20 | 18% | 6% | +0.88 | +0.044 |
| Pre-open 08:00-09:30 | 6 | 8% | 5% | -0.48 | -0.081 |
| US RTH 09:30-16:00 | 26 | 48% | 80% | +2.65 | +0.102 |
| Post 16:00-17:00 | 4 | 3% | 4% | +0.71 | +0.178 |

**Range expansion** (mean window range >= 1.5x the market median window; 28 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 09:30-09:45 | 3.18 | 61.9 | 22.77 | 2.98 |
| 10:00-10:15 | 3.05 | 59.5 | 17.95 | 2.82 |
| 09:45-10:00 | 2.80 | 55.0 | 16.77 | 2.74 |
| 15:45-16:00 | 2.74 | 54.0 | 32.16 | 2.38 |
| 10:15-10:30 | 2.58 | 50.6 | 14.80 | 2.42 |
| 08:30-08:45 | 2.51 | 47.8 | 4.75 | 1.90 |
| 10:30-10:45 | 2.44 | 47.7 | 13.82 | 2.26 |
| 10:45-11:00 | 2.25 | 44.2 | 12.27 | 2.01 |
| 11:00-11:15 | 2.19 | 42.8 | 11.71 | 2.06 |
| 15:30-15:45 | 2.06 | 40.1 | 11.08 | 1.88 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 8 windows; runs (ET): 00:00-01:00, 22:45-23:00, 23:15-00:00.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 4 of 92 windows (null expectation ~4.2); |t|>=3 in 1 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 4 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 02:45-03:00 | 952 | -0.69 | -0.50 | -3.49 | -1.28 | -0.30 | -0.71 | -0.77 | 0.15 | 4 **Y** | 0.59 | -3.2 | -0.54 | - | - |
| 14:30-14:45 | 916 | +1.36 | +0.89 | +2.44 | 1.91 | 1.87 | 0.70 | 1.21 | 1.05 | 4 **Y** | 1.17 | +2.6 | -0.31 | +1.29 (+2.0) | +1.54 (+1.6) |
| 18:15-18:30 | 951 | +0.51 | +0.42 | +2.25 | 0.01 | 0.73 | 0.70 | 0.25 | 1.94 | 4 **Y** | 0.44 | +1.9 | +0.65 | - | - |
| 10:45-11:00 | 950 | -1.03 | -1.09 | -2.06 | -0.20 | 0.10 | -0.93 | -2.78 | -0.86 | 3 **Y** | 0.89 | -1.1 | -2.98 | -1.53 (-1.8) | -0.58 (-1.1) |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 20.4 bps vs narrow-day 15.3 bps (x1.33); mean volume wide/narrow x1.24. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: none

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| 09:30 open | 950 | -0.33 (-0.8) | +0.65 | +0.00 | +1.07 (+1.2) | +0.85 (+0.7) | 10.6/28.8 | 2.27 | +0.29 (+0.3, 51%) |
| 10:00 data | 950 | +0.99 (+1.1) | -0.77 | -0.38 | -0.22 (-0.2) | -0.83 (-0.7) | 9.5/26.4 | 1.01 | +1.58 (+1.9, 53%) |
| 15:50 MOC imbalance | 916 | -1.05 (-1.6) | +0.35 | +0.48 | +0.91 (+1.3) | +1.37 (+1.7) | 8.7/16.2 | 1.34 | +0.22 (+0.4, 50%) |
| 16:00 cash close | 916 | -0.23 (-0.3) | +0.06 | +0.31 | +0.56 (+1.2) | +0.70 (+1.3) | 5.7/9.3 | 0.65 | -0.31 (-0.9, 49%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| 09:30 open | +2.3 / +1.6 / 2.45 (n152) | +3.0 / -1.4 / 2.15 (n257) | -0.9 / +1.3 / 2.13 (n259) | +0.4 / +0.1 / 2.30 (n256) | +1.4 / +1.2 / 2.55 (n26) | 3 | 3 |
| 10:00 data | -0.7 / +5.0 / 0.97 (n152) | -0.7 / +0.5 / 1.04 (n257) | -0.4 / +0.6 / 1.07 (n259) | +0.8 / +2.0 / 0.99 (n256) | -1.3 / -2.0 / 0.91 (n26) | 3 | 4 |
| 15:50 MOC imbalance | -2.2 / +1.4 / 1.22 (n147) | +2.1 / -1.0 / 1.26 (n248) | +0.4 / +0.8 / 1.43 (n249) | +2.2 / +0.5 / 1.41 (n247) | +0.0 / -2.8 / 1.62 (n25) | 3 | 3 |
| 16:00 cash close | +0.5 / -0.3 / 0.61 (n147) | +1.3 / +0.3 / 0.60 (n248) | -0.1 / -0.4 / 0.67 (n249) | +0.6 / -0.5 / 0.69 (n247) | +0.5 / -3.9 / 0.90 (n25) | 3 | 3 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- 09:30 open: ret +0.0 -0.1 +0.0 +0.1 -0.2 -0.3 +0.6 +0.1 -0.8 +0.3 +0.5 +0.3 -0.8 +0.0 +0.4 +0.3 -0.1 -0.1 | rng 18 16 15 15 14 20 42 35 34 36 33 29 40 33 33 30 31 29 (peak range step at +0 min, 2.6x the pre-event average)
- 10:00 data: ret +0.6 +0.1 -0.8 +0.3 +0.5 +0.3 -0.8 +0.0 +0.4 +0.3 -0.0 -0.1 +0.1 -0.0 +0.4 +0.2 -0.9 -0.3 | rng 42 35 34 36 33 29 40 33 33 30 31 29 30 28 27 27 27 25 (peak range step at -30 min, 1.2x the pre-event average)
- 15:50 MOC imbalance: ret +0.2 -0.6 -0.0 -0.9 +0.1 +0.2 +0.4 +0.1 +0.1 +0.4 -0.1 +0.2 +0.1 -0.0 +0.2 +0.1 +0.0 +0.1 | rng 23 22 25 24 24 25 35 34 26 15 13 12 11 9 9 8 7 8 (peak range step at +0 min, 1.5x the pre-event average)
- 16:00 cash close: ret -0.0 -0.9 +0.1 +0.2 +0.3 +0.1 +0.1 +0.4 -0.1 +0.2 +0.1 -0.0 +0.2 +0.1 +0.0 +0.1 -0.1 -0.1 | rng 25 24 24 25 35 34 26 15 13 12 11 9 9 8 7 8 7 9 (peak range step at -10 min, 1.3x the pre-event average)

**Windows worth a rule (ES; 8 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT | 09:30 open: range x2.3 after vs before (4/4 yrs >=1.3); first-5-min follow-through +0.29 bps (t +0.3, same sign 3/4) | post-event rule: trade the first-5-min move after the event as continuation, bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 2 | DRIFT | 02:45-03:00 ET drift -0.69 bps (t -3.5, same sign 4/4 yrs, 0.59x cost; selection-span t -3.2, late-span mean -0.54) | drift rule: short at 02:45 open, flat at 03:00 |
| 3 | DRIFT | 14:30-14:45 ET drift +1.36 bps (t +2.4, same sign 4/4 yrs, 1.17x cost; selection-span t +2.6, late-span mean -0.31) | drift rule: long at 14:30 open, flat at 14:45 |
| 4 | DRIFT (below 0.5x cost) | 18:15-18:30 ET drift +0.51 bps (t +2.2, same sign 4/4 yrs, 0.44x cost; selection-span t +1.9, late-span mean +0.65) | drift rule: long at 18:15 open, flat at 18:30 |
| 5 | DRIFT | 10:45-11:00 ET drift -1.03 bps (t -2.1, same sign 3/4 yrs, 0.89x cost; selection-span t -1.1, late-span mean -2.98) | drift rule: short at 10:45 open, flat at 11:00 |
| 6 | RANGE | 08:30-08:45 ET range x2.51 of median (min-year x1.90) | range-expansion rule: break of the prior 15-min range (08:15-08:30) with a bracket at 1x/1.5x the median window range (10 bps ~ 19 ticks), flat at 08:45 |
| 7 | RANGE | 10:30-10:45 ET range x2.44 of median (min-year x2.26) | range-expansion rule: break of the prior 15-min range (10:15-10:30) with a bracket at 1x/1.5x the median window range (10 bps ~ 19 ticks), flat at 10:45 |
| 8 | RANGE | 11:00-11:15 ET range x2.19 of median (min-year x2.06) | range-expansion rule: break of the prior 15-min range (10:45-11:00) with a bracket at 1x/1.5x the median window range (10 bps ~ 19 ticks), flat at 11:15 |

## RTY
Days 952 (trade dates 2022-06-01..2026-02-06); median level 2,014; anchor for the day-type split 09:30 ET (first hour 09:30-+60 min; wide = first-hour range above the prior-20-day median, 49% of days); median 15-min window range 13.7 bps; round-trip cost for a one-window trade (1 tick adverse each side + 4.84 fee) = 1.47 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 21% | 4% | +0.01 | +0.000 |
| Europe 03:00-08:00 | 20 | 18% | 6% | +2.30 | +0.115 |
| Pre-open 08:00-09:30 | 6 | 9% | 6% | -1.96 | -0.327 |
| US RTH 09:30-16:00 | 26 | 49% | 79% | +2.03 | +0.078 |
| Post 16:00-17:00 | 4 | 3% | 5% | +0.98 | +0.244 |

**Range expansion** (mean window range >= 1.5x the market median window; 31 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 09:30-09:45 | 4.70 | 130.5 | 31.87 | 4.21 |
| 10:00-10:15 | 3.56 | 99.5 | 17.23 | 3.36 |
| 09:45-10:00 | 3.56 | 99.3 | 17.91 | 3.37 |
| 10:15-10:30 | 2.95 | 82.4 | 13.29 | 2.79 |
| 08:30-08:45 | 2.86 | 79.6 | 5.87 | 2.44 |
| 10:30-10:45 | 2.73 | 76.2 | 11.94 | 2.51 |
| 10:45-11:00 | 2.40 | 67.1 | 10.20 | 2.27 |
| 11:00-11:15 | 2.31 | 64.2 | 9.55 | 2.17 |
| 15:45-16:00 | 2.25 | 62.7 | 35.41 | 2.17 |
| 11:15-11:30 | 2.12 | 59.3 | 8.70 | 1.96 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 13 windows; runs (ET): 00:00-01:30, 22:15-00:00.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 5 of 92 windows (null expectation ~4.2); |t|>=3 in 1 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 5 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 02:45-03:00 | 952 | -0.99 | -0.54 | -3.87 | -1.45 | -0.30 | -1.21 | -1.17 | -1.02 | 4 **Y** | 0.67 | -3.4 | -1.15 | - | - |
| 09:15-09:30 | 951 | -1.28 | -0.93 | -2.80 | -3.86 | -2.85 | 0.23 | -0.21 | 3.75 | 3 **Y** | 0.87 | -2.7 | -0.53 | - | - |
| 14:30-14:45 | 916 | +1.77 | +1.48 | +2.36 | 2.77 | 1.83 | 0.83 | 1.94 | 2.93 | 4 **Y** | 1.20 | +2.8 | -0.88 | +2.14 (+2.4) | +1.54 (+1.3) |
| 16:30-16:45 | 916 | +0.48 | +0.00 | +2.10 | 1.23 | 0.55 | 0.25 | 0.43 | -1.80 | 4 **Y** | 0.33 | +2.3 | -0.04 | +0.22 (+0.6) | +0.71 (+2.3) |
| 18:15-18:30 | 948 | +0.71 | +0.00 | +2.08 | 0.09 | 0.94 | 0.49 | 0.98 | 1.59 | 4 **Y** | 0.48 | +1.8 | +0.61 | - | - |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 26.5 bps vs narrow-day 22.0 bps (x1.20); mean volume wide/narrow x1.20. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: none

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| 09:30 open | 950 | -2.25 (-3.7) | +0.53 | -0.51 | +0.86 (+0.5) | +0.25 (+0.1) | 23.5/52.3 | 2.95 | -0.04 (-0.0, 51%) |
| 10:00 data | 950 | +0.59 (+0.4) | -0.55 | -0.27 | -0.60 (-0.4) | -0.79 (-0.4) | 16.5/42.3 | 0.87 | +1.41 (+1.1, 52%) |
| 15:50 MOC imbalance | 916 | -1.67 (-2.1) | +0.69 | +1.37 | +1.15 (+1.6) | +1.46 (+1.8) | 10.0/17.5 | 1.24 | +0.19 (+0.3, 50%) |
| 16:00 cash close | 916 | -0.51 (-0.6) | +1.05 | +0.76 | +0.76 (+1.6) | +0.87 (+1.3) | 6.5/11.3 | 0.65 | -0.30 (-0.6, 46%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| 09:30 open | -4.3 / +3.7 / 3.27 (n152) | +4.5 / +0.1 / 3.10 (n257) | -1.1 / -3.0 / 2.65 (n259) | +1.5 / +0.5 / 2.84 (n256) | +8.0 / +1.6 / 3.65 (n26) | 2 | 1 |
| 10:00 data | +3.9 / +5.3 / 0.85 (n152) | -1.8 / -0.4 / 0.80 (n257) | -1.5 / +0.5 / 0.91 (n259) | -1.2 / +1.2 / 0.91 (n256) | -0.5 / +7.5 / 0.82 (n26) | 3 | 3 |
| 15:50 MOC imbalance | +2.6 / +1.0 / 1.22 (n147) | +0.9 / -1.6 / 1.20 (n248) | +0.8 / -0.0 / 1.28 (n249) | +0.5 / +1.7 / 1.26 (n247) | +5.3 / -0.7 / 1.26 (n25) | 4 | 2 |
| 16:00 cash close | +1.9 / +0.3 / 0.66 (n147) | +1.1 / -0.2 / 0.65 (n248) | +0.7 / -1.1 / 0.65 (n249) | -0.2 / +0.4 / 0.65 (n247) | +0.4 / -2.9 / 0.77 (n25) | 3 | 2 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- 09:30 open: ret -0.6 -0.2 -0.1 +0.1 -0.5 -1.0 +0.5 +0.1 -1.2 +0.8 +0.8 -0.2 -0.6 +0.2 +0.1 +0.4 -0.2 -0.5 | rng 27 24 23 23 23 32 94 67 64 63 58 49 64 54 53 48 49 46 (peak range step at +0 min, 3.7x the pre-event average)
- 10:00 data: ret +0.4 +0.1 -1.2 +0.7 +0.8 -0.2 -0.5 +0.2 +0.1 +0.4 -0.2 -0.5 +0.5 +0.1 +0.1 +0.3 -0.8 -0.3 | rng 94 67 64 63 58 49 64 54 53 48 49 46 46 44 42 41 40 37 (peak range step at -30 min, 1.4x the pre-event average)
- 15:50 MOC imbalance: ret +0.0 -0.9 -0.1 -1.2 +0.3 +0.2 +0.7 -0.4 +1.0 -0.1 -0.2 +0.1 +0.1 -0.2 +0.0 +0.2 +0.1 +0.0 | rng 29 28 30 29 27 30 41 38 29 18 17 14 13 11 11 10 9 11 (peak range step at +0 min, 1.4x the pre-event average)
- 16:00 cash close: ret -0.1 -1.2 +0.3 +0.2 +0.7 -0.4 +1.0 -0.1 -0.2 +0.1 +0.1 -0.2 +0.0 +0.2 +0.1 +0.0 -0.0 -0.3 | rng 30 29 27 30 41 38 29 18 17 14 13 11 11 10 9 11 11 14 (peak range step at -10 min, 1.2x the pre-event average)

**Windows worth a rule (RTY; 9 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT | 09:30 open: range x3.0 after vs before (4/4 yrs >=1.3); first-5-min follow-through -0.04 bps (t -0.0, same sign 1/4) | post-event rule: trade the first-5-min move after the event as reversal (fade), bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 2 | DRIFT | 02:45-03:00 ET drift -0.99 bps (t -3.9, same sign 4/4 yrs, 0.67x cost; selection-span t -3.4, late-span mean -1.15) | drift rule: short at 02:45 open, flat at 03:00 |
| 3 | DRIFT | 09:15-09:30 ET drift -1.28 bps (t -2.8, same sign 3/4 yrs, 0.87x cost; selection-span t -2.7, late-span mean -0.53) | drift rule: short at 09:15 open, flat at 09:30 |
| 4 | DRIFT | 14:30-14:45 ET drift +1.77 bps (t +2.4, same sign 4/4 yrs, 1.20x cost; selection-span t +2.8, late-span mean -0.88) | drift rule: long at 14:30 open, flat at 14:45 |
| 5 | DRIFT (below 0.5x cost) | 16:30-16:45 ET drift +0.48 bps (t +2.1, same sign 4/4 yrs, 0.33x cost; selection-span t +2.3, late-span mean -0.04) | drift rule: long at 16:30 open, flat at 16:45 |
| 6 | DRIFT (below 0.5x cost) | 18:15-18:30 ET drift +0.71 bps (t +2.1, same sign 4/4 yrs, 0.48x cost; selection-span t +1.8, late-span mean +0.61) | drift rule: long at 18:15 open, flat at 18:30 |
| 7 | RANGE | 08:30-08:45 ET range x2.86 of median (min-year x2.44) | range-expansion rule: break of the prior 15-min range (08:15-08:30) with a bracket at 1x/1.5x the median window range (14 bps ~ 28 ticks), flat at 08:45 |
| 8 | RANGE | 10:30-10:45 ET range x2.73 of median (min-year x2.51) | range-expansion rule: break of the prior 15-min range (10:15-10:30) with a bracket at 1x/1.5x the median window range (14 bps ~ 28 ticks), flat at 10:45 |
| 9 | RANGE | 11:00-11:15 ET range x2.31 of median (min-year x2.17) | range-expansion rule: break of the prior 15-min range (10:45-11:00) with a bracket at 1x/1.5x the median window range (14 bps ~ 28 ticks), flat at 11:15 |

## YM
Days 952 (trade dates 2022-06-01..2026-02-06); median level 3.88e+04; anchor for the day-type split 09:30 ET (first hour 09:30-+60 min; wide = first-hour range above the prior-20-day median, 49% of days); median 15-min window range 8.6 bps; round-trip cost for a one-window trade (1 tick adverse each side + 4.84 fee) = 0.76 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 21% | 7% | -1.34 | -0.037 |
| Europe 03:00-08:00 | 20 | 18% | 10% | +0.33 | +0.016 |
| Pre-open 08:00-09:30 | 6 | 8% | 7% | -0.47 | -0.078 |
| US RTH 09:30-16:00 | 26 | 50% | 73% | +4.19 | +0.161 |
| Post 16:00-17:00 | 4 | 3% | 3% | +0.34 | +0.086 |

**Range expansion** (mean window range >= 1.5x the market median window; 30 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 09:30-09:45 | 4.24 | 139.9 | 18.54 | 3.48 |
| 10:00-10:15 | 3.28 | 107.0 | 10.51 | 2.96 |
| 09:45-10:00 | 3.19 | 105.2 | 10.37 | 2.74 |
| 15:45-16:00 | 2.77 | 90.2 | 11.50 | 2.47 |
| 10:15-10:30 | 2.73 | 89.3 | 7.96 | 2.44 |
| 10:30-10:45 | 2.59 | 84.5 | 7.34 | 2.25 |
| 08:30-08:45 | 2.39 | 76.5 | 3.47 | 1.88 |
| 11:00-11:15 | 2.35 | 76.9 | 6.10 | 2.09 |
| 10:45-11:00 | 2.32 | 76.1 | 6.30 | 1.94 |
| 11:15-11:30 | 2.21 | 72.5 | 5.47 | 1.97 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 13 windows; runs (ET): 00:00-01:00, 01:15-01:30, 18:45-19:00, 22:15-00:00.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 5 of 92 windows (null expectation ~4.2); |t|>=3 in 1 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 5 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 02:45-03:00 | 952 | -0.89 | -0.75 | -4.94 | -1.24 | -0.38 | -1.18 | -1.01 | 0.17 | 4 **Y** | 1.16 | -4.4 | -0.78 | - | - |
| 14:30-14:45 | 916 | +1.39 | +0.89 | +2.79 | 1.98 | 1.83 | 0.92 | 1.08 | 1.35 | 4 **Y** | 1.82 | +3.1 | -0.40 | +0.62 (+1.0) | +2.24 (+2.9) |
| 23:30-23:45 | 952 | -0.31 | -0.25 | -2.27 | -0.44 | -0.26 | -0.22 | -0.41 | 0.00 | 4 **Y** | 0.40 | -2.2 | -0.12 | - | - |
| 18:00-18:15 | 951 | -0.80 | -1.01 | -2.10 | -0.86 | -1.30 | -0.32 | -0.71 | -1.08 | 4 **Y** | 1.04 | -2.3 | +0.25 | - | - |
| 18:15-18:30 | 950 | +0.41 | +0.27 | +2.01 | -0.09 | 0.75 | 0.46 | 0.24 | 1.11 | 3 **Y** | 0.53 | +1.7 | +0.45 | - | - |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 18.0 bps vs narrow-day 14.6 bps (x1.24); mean volume wide/narrow x1.18. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: 14:30 narrow +2.24 (t +2.9, n 444)

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| 09:30 open | 950 | +0.10 (+0.2) | +2.14 | +1.12 | +2.00 (+2.1) | +2.12 (+1.7) | 14.0/29.3 | 2.76 | -1.07 (-1.2, 47%) |
| 10:00 data | 950 | +1.91 (+2.0) | -0.93 | -0.55 | +0.12 (+0.1) | +0.33 (+0.3) | 8.9/24.3 | 0.88 | +0.89 (+1.2, 51%) |
| 15:50 MOC imbalance | 916 | -0.73 (-1.2) | +0.47 | +0.11 | +0.51 (+0.9) | +0.68 (+1.1) | 7.8/13.0 | 1.29 | -0.07 (-0.1, 48%) |
| 16:00 cash close | 916 | -0.20 (-0.3) | -0.11 | +0.09 | +0.10 (+0.3) | +0.31 (+0.8) | 4.7/7.8 | 0.63 | -0.70 (-2.5, 47%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| 09:30 open | +3.8 / -1.8 / 2.63 (n152) | +2.5 / -0.6 / 2.64 (n257) | -1.2 / -1.6 / 2.86 (n259) | +2.9 / -0.5 / 2.80 (n256) | +8.8 / -1.5 / 3.94 (n26) | 3 | 4 |
| 10:00 data | -0.5 / +2.7 / 0.93 (n152) | -1.0 / -0.0 / 0.90 (n257) | +0.2 / +0.3 / 0.84 (n259) | +1.2 / +0.9 / 0.88 (n256) | +3.2 / +5.6 / 0.67 (n26) | 2 | 3 |
| 15:50 MOC imbalance | -1.3 / -0.6 / 1.20 (n147) | +2.2 / -0.7 / 1.22 (n248) | -0.3 / +0.6 / 1.34 (n249) | +0.9 / +0.1 / 1.38 (n247) | -1.2 / -0.0 / 1.47 (n25) | 2 | 2 |
| 16:00 cash close | +1.1 / -1.4 / 0.59 (n147) | +0.5 / -0.7 / 0.59 (n248) | -0.8 / -0.4 / 0.66 (n249) | +0.3 / -0.6 / 0.67 (n247) | -2.3 / -1.1 / 0.90 (n25) | 3 | 4 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- 09:30 open: ret -0.0 +0.0 +0.2 -0.0 -0.2 +0.0 +2.1 -0.3 -0.7 -0.1 +0.4 +0.5 -0.9 +0.2 +0.2 +0.5 +0.1 +0.1 | rng 29 26 25 25 24 43 103 71 66 67 60 53 69 58 57 52 53 50 (peak range step at +0 min, 3.6x the pre-event average)
- 10:00 data: ret +2.1 -0.4 -0.7 -0.1 +0.4 +0.5 -0.9 +0.2 +0.2 +0.5 +0.1 +0.1 +0.0 +0.1 +0.4 +0.3 -0.6 +0.0 | rng 103 71 66 67 60 53 69 58 57 52 53 50 52 49 48 46 45 43 (peak range step at -30 min, 1.5x the pre-event average)
- 15:50 MOC imbalance: ret +0.2 -0.5 -0.0 -0.6 +0.2 +0.1 +0.5 -0.2 -0.1 +0.3 -0.1 +0.2 -0.1 -0.1 +0.2 +0.0 +0.0 +0.1 | rng 38 37 42 41 40 42 58 56 40 26 22 19 15 14 14 13 12 13 (peak range step at +0 min, 1.5x the pre-event average)
- 16:00 cash close: ret -0.0 -0.6 +0.2 +0.1 +0.5 -0.3 -0.1 +0.3 -0.1 +0.2 -0.1 -0.1 +0.2 +0.0 +0.0 +0.1 -0.0 -0.1 | rng 42 41 40 42 58 56 40 26 22 19 15 14 14 13 12 13 13 14 (peak range step at -10 min, 1.2x the pre-event average)

**Windows worth a rule (YM; 10 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT | 16:00 cash close: range x0.6 after vs before (0/4 yrs >=1.3); first-5-min follow-through -0.70 bps (t -2.5, same sign 4/4) | post-event rule: trade the first-5-min move after the event as reversal (fade), bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 2 | EVENT | 09:30 open: range x2.8 after vs before (4/4 yrs >=1.3); first-5-min follow-through -1.07 bps (t -1.2, same sign 4/4) | post-event rule: trade the first-5-min move after the event as reversal (fade), bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 3 | EVENT-DRIFT | 09:30 open: 0..+30 min drift +2.00 bps (t +2.1, same sign 3/4 yrs) | drift rule: long at the event, flat at +30 min |
| 4 | DRIFT | 02:45-03:00 ET drift -0.89 bps (t -4.9, same sign 4/4 yrs, 1.16x cost; selection-span t -4.4, late-span mean -0.78) | drift rule: short at 02:45 open, flat at 03:00 |
| 5 | DRIFT | 14:30-14:45 ET drift +1.39 bps (t +2.8, same sign 4/4 yrs, 1.82x cost; selection-span t +3.1, late-span mean -0.40) | drift rule: long at 14:30 open, flat at 14:45 |
| 6 | DRIFT (below 0.5x cost) | 23:30-23:45 ET drift -0.31 bps (t -2.3, same sign 4/4 yrs, 0.40x cost; selection-span t -2.2, late-span mean -0.12) | drift rule: short at 23:30 open, flat at 23:45 |
| 7 | DRIFT | 18:15-18:30 ET drift +0.41 bps (t +2.0, same sign 3/4 yrs, 0.53x cost; selection-span t +1.7, late-span mean +0.45) | drift rule: long at 18:15 open, flat at 18:30 |
| 8 | RANGE | 10:30-10:45 ET range x2.59 of median (min-year x2.25) | range-expansion rule: break of the prior 15-min range (10:15-10:30) with a bracket at 1x/1.5x the median window range (9 bps ~ 32 ticks), flat at 10:45 |
| 9 | RANGE | 08:30-08:45 ET range x2.39 of median (min-year x1.88) | range-expansion rule: break of the prior 15-min range (08:15-08:30) with a bracket at 1x/1.5x the median window range (9 bps ~ 32 ticks), flat at 08:45 |
| 10 | RANGE | 11:00-11:15 ET range x2.35 of median (min-year x2.09) | range-expansion rule: break of the prior 15-min range (10:45-11:00) with a bracket at 1x/1.5x the median window range (9 bps ~ 32 ticks), flat at 11:15 |

## CL
Days 952 (trade dates 2022-06-01..2026-02-06); median level 74.64; anchor for the day-type split 09:00 ET (first hour 09:00-+60 min; wide = first-hour range above the prior-20-day median, 49% of days); median 15-min window range 28.7 bps; round-trip cost for a one-window trade (1 tick adverse each side + 4.84 fee) = 3.33 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 23% | 9% | -4.56 | -0.127 |
| Europe 03:00-08:00 | 20 | 24% | 18% | +2.78 | +0.139 |
| Pre-open 08:00-09:30 | 6 | 10% | 13% | +0.62 | +0.104 |
| US RTH 09:30-16:00 | 26 | 40% | 58% | -6.33 | -0.244 |
| Post 16:00-17:00 | 4 | 2% | 1% | +1.93 | +0.484 |

**Range expansion** (mean window range >= 1.5x the market median window; 12 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 09:00-09:15 | 2.24 | 49.6 | 5.13 | 1.88 |
| 09:30-09:45 | 2.12 | 46.7 | 4.66 | 1.81 |
| 10:30-10:45 | 2.04 | 45.2 | 4.52 | 1.72 |
| 10:00-10:15 | 1.99 | 43.6 | 4.39 | 1.90 |
| 09:45-10:00 | 1.91 | 42.2 | 4.06 | 1.67 |
| 11:00-11:15 | 1.87 | 41.0 | 3.93 | 1.71 |
| 11:15-11:30 | 1.85 | 40.8 | 4.08 | 1.58 |
| 10:45-11:00 | 1.78 | 39.2 | 3.66 | 1.56 |
| 11:30-11:45 | 1.78 | 38.9 | 3.64 | 1.63 |
| 10:15-10:30 | 1.76 | 38.7 | 3.67 | 1.59 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 24 windows; runs (ET): 00:00-01:30, 16:00-17:00, 18:15-20:00, 22:15-00:00.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 8 of 92 windows (null expectation ~4.2); |t|>=3 in 2 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 8 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 14:30-14:45 | 922 | +2.55 | +1.69 | +3.81 | 0.24 | 2.05 | 5.36 | 1.75 | 0.71 | 4 **Y** | 0.76 | +3.6 | +1.84 | +2.90 (+2.9) | +2.29 (+2.5) |
| 18:00-18:15 | 948 | -3.83 | -3.30 | -3.74 | -2.72 | -3.40 | -4.55 | -3.29 | -12.58 | 4 **Y** | 1.15 | -3.6 | -2.30 | - | - |
| 16:00-16:15 | 920 | +0.98 | +0.00 | +2.73 | 0.55 | 1.14 | 0.26 | 1.77 | 1.06 | 4 **Y** | 0.29 | +2.0 | +1.88 | +1.24 (+2.3) | +0.82 (+1.8) |
| 02:45-03:00 | 951 | -1.27 | -1.05 | -2.47 | -3.72 | -0.72 | 0.42 | -1.78 | -4.37 | 3 **Y** | 0.38 | -1.3 | -3.99 | - | - |
| 14:00-14:15 | 947 | -2.09 | -1.59 | -2.46 | -3.02 | -3.85 | -1.14 | -1.24 | 2.85 | 4 **Y** | 0.63 | -2.4 | -1.04 | -1.38 (-1.1) | -2.45 (-2.2) |
| 16:45-17:00 | 918 | +0.91 | +0.00 | +2.30 | 1.84 | 0.09 | 1.25 | -0.04 | 9.42 | 3 **Y** | 0.27 | +2.2 | +0.74 | +0.75 (+1.3) | +0.84 (+1.6) |
| 13:45-14:00 | 947 | -1.53 | -1.43 | -2.09 | -4.75 | -1.70 | -0.70 | -0.68 | 2.15 | 4 **Y** | 0.46 | -1.7 | -2.25 | -1.24 (-1.1) | -1.52 (-1.6) |
| 23:00-23:15 | 951 | -0.78 | +0.00 | -2.03 | -1.11 | -1.15 | 0.10 | -1.22 | 0.44 | 3 **Y** | 0.23 | -2.5 | +0.77 | - | - |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 37.9 bps vs narrow-day 32.8 bps (x1.16); mean volume wide/narrow x1.13. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: 14:30 wide +2.90 (t +2.9, n 456); 14:30 narrow +2.29 (t +2.5, n 456)

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| Wed 10:30 EIA inventory | 191 | -4.84 (-1.5) | -1.28 | -2.54 | -1.64 (-0.4) | +0.10 (+0.0) | 29.6/63.6 | 1.61 | +3.93 (+0.9, 53%) |
| 14:30 settle | 920 | -3.42 (-2.5) | +1.54 | +2.50 | +2.93 (+3.5) | +4.16 (+3.8) | 10.0/23.2 | 0.68 | -0.01 (-0.0, 51%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| Wed 10:30 EIA inventory | +14.9 / +11.3 / 1.64 (n31) | -6.3 / +5.7 / 1.69 (n52) | -0.8 / +6.0 / 1.70 (n51) | -8.1 / -5.5 / 1.44 (n52) | +2.9 / +15.8 / 1.13 (n5) | 3 | 3 |
| 14:30 settle | +0.8 / -0.9 / 0.65 (n147) | +2.8 / -0.7 / 0.64 (n249) | +6.2 / +2.7 / 0.66 (n250) | +1.7 / -0.6 / 0.77 (n249) | -4.5 / -7.5 / 0.90 (n25) | 4 | 3 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- Wed 10:30 EIA inventory: ret -2.4 -1.1 -2.4 -2.1 +1.4 +1.7 -1.3 -3.5 +2.2 -1.5 +2.2 +0.2 -0.2 +2.0 -0.7 -0.9 +0.6 +1.0 | rng 25 23 23 21 20 18 44 31 29 26 26 23 26 25 23 24 23 25 (peak range step at +0 min, 2.0x the pre-event average)
- 14:30 settle: ret -0.9 -1.5 +0.1 -0.6 -0.1 -0.5 +1.5 +0.6 +0.3 +0.3 -0.1 +0.3 -0.1 +0.4 -0.1 +0.2 +0.5 +0.2 | rng 17 17 16 17 18 25 16 12 10 9 9 9 10 8 8 8 8 8 (peak range step at -5 min, 1.3x the pre-event average)

**Windows worth a rule (CL; 10 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT-DRIFT | 14:30 settle: 0..+30 min drift +2.93 bps (t +3.5, same sign 4/4 yrs) | drift rule: long at the event, flat at +30 min |
| 2 | EVENT | Wed 10:30 EIA inventory: range x1.6 after vs before (4/4 yrs >=1.3); first-5-min follow-through +3.93 bps (t +0.9, same sign 3/4) | post-event rule: trade the first-5-min move after the event as continuation, bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 3 | DRIFT (below 0.5x cost) | 16:00-16:15 ET drift +0.98 bps (t +2.7, same sign 4/4 yrs, 0.29x cost; selection-span t +2.0, late-span mean +1.88) | drift rule: long at 16:00 open, flat at 16:15 |
| 4 | DRIFT (below 0.5x cost) | 02:45-03:00 ET drift -1.27 bps (t -2.5, same sign 3/4 yrs, 0.38x cost; selection-span t -1.3, late-span mean -3.99) | drift rule: short at 02:45 open, flat at 03:00 |
| 5 | DRIFT | 14:00-14:15 ET drift -2.09 bps (t -2.5, same sign 4/4 yrs, 0.63x cost; selection-span t -2.4, late-span mean -1.04) | drift rule: short at 14:00 open, flat at 14:15 |
| 6 | DRIFT (below 0.5x cost) | 16:45-17:00 ET drift +0.91 bps (t +2.3, same sign 3/4 yrs, 0.27x cost; selection-span t +2.2, late-span mean +0.74) | drift rule: long at 16:45 open, flat at 17:00 |
| 7 | DRIFT (below 0.5x cost) | 13:45-14:00 ET drift -1.53 bps (t -2.1, same sign 4/4 yrs, 0.46x cost; selection-span t -1.7, late-span mean -2.25) | drift rule: short at 13:45 open, flat at 14:00 |
| 8 | RANGE | 09:00-09:15 ET range x2.24 of median (min-year x1.88) | range-expansion rule: break of the prior 15-min range (08:45-09:00) with a bracket at 1x/1.5x the median window range (29 bps ~ 22 ticks), flat at 09:15 |
| 9 | RANGE | 09:30-09:45 ET range x2.12 of median (min-year x1.81) | range-expansion rule: break of the prior 15-min range (09:15-09:30) with a bracket at 1x/1.5x the median window range (29 bps ~ 22 ticks), flat at 09:45 |
| 10 | RANGE | 10:00-10:15 ET range x1.99 of median (min-year x1.90) | range-expansion rule: break of the prior 15-min range (09:45-10:00) with a bracket at 1x/1.5x the median window range (29 bps ~ 22 ticks), flat at 10:15 |

## ZN
Days 952 (trade dates 2022-06-01..2026-02-06); median level 111.7; anchor for the day-type split 08:20 ET (first hour 08:20-+60 min; wide = first-hour range above the prior-20-day median, 49% of days); median 15-min window range 5.3 bps; round-trip cost for a one-window trade (1 tick adverse each side + 4.84 fee) = 3.23 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 26% | 9% | +0.34 | +0.010 |
| Europe 03:00-08:00 | 20 | 21% | 14% | -0.25 | -0.012 |
| Pre-open 08:00-09:30 | 6 | 13% | 18% | -0.38 | -0.063 |
| US RTH 09:30-16:00 | 26 | 36% | 55% | +0.37 | +0.014 |
| Post 16:00-17:00 | 4 | 4% | 4% | -0.24 | -0.061 |

**Range expansion** (mean window range >= 1.5x the market median window; 12 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 08:30-08:45 | 3.56 | 13.5 | 7.92 | 3.08 |
| 10:00-10:15 | 2.44 | 9.2 | 6.18 | 2.29 |
| 09:30-09:45 | 2.05 | 7.8 | 4.90 | 1.98 |
| 08:45-09:00 | 1.99 | 7.5 | 5.02 | 1.86 |
| 09:45-10:00 | 1.95 | 7.4 | 4.82 | 1.82 |
| 09:00-09:15 | 1.94 | 7.4 | 4.56 | 1.86 |
| 08:15-08:30 | 1.92 | 7.3 | 3.84 | 1.75 |
| 10:15-10:30 | 1.81 | 6.9 | 4.54 | 1.79 |
| 09:15-09:30 | 1.78 | 6.7 | 4.15 | 1.66 |
| 10:30-10:45 | 1.73 | 6.5 | 4.11 | 1.66 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 10 windows; runs (ET): 00:00-01:00, 18:45-19:00, 22:45-00:00.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 10 of 92 windows (null expectation ~4.2); |t|>=3 in 2 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 9 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 15:45-16:00 | 919 | +0.50 | +0.00 | +3.60 | 0.41 | 0.56 | 0.44 | 0.61 | -0.06 | 4 **Y** | 0.15 | +3.1 | +0.45 | +0.42 (+1.9) | +0.51 (+3.1) |
| 01:45-02:00 | 952 | +0.26 | +0.00 | +3.05 | 0.54 | 0.00 | 0.40 | 0.24 | -0.11 | 4 **Y** | 0.08 | +3.1 | +0.02 | - | - |
| 08:15-08:30 | 952 | +0.55 | +0.00 | +2.61 | 0.90 | 0.87 | -0.14 | 0.80 | -0.48 | 3 **Y** | 0.17 | +2.4 | +0.39 | - | - |
| 02:15-02:30 | 952 | +0.32 | +0.00 | +2.50 | 0.60 | 0.26 | 0.25 | 0.31 | 0.11 | 4 **Y** | 0.10 | +2.3 | +0.22 | - | - |
| 21:00-21:15 | 952 | +0.22 | +0.00 | +2.28 | 0.56 | 0.30 | 0.11 | 0.08 | -0.21 | 4 **Y** | 0.07 | +2.2 | +0.07 | - | - |
| 03:00-03:15 | 952 | -0.35 | +0.00 | -2.28 | 0.05 | -0.75 | -0.39 | -0.12 | -0.43 | 3 **Y** | 0.11 | -2.1 | -0.22 | - | - |
| 11:45-12:00 | 951 | -0.32 | +0.00 | -2.25 | -0.57 | -0.83 | 0.35 | -0.32 | -0.48 | 3 **Y** | 0.10 | -2.0 | -0.25 | -0.41 (-1.8) | -0.22 (-1.2) |
| 18:30-18:45 | 946 | -0.17 | +0.00 | -2.14 | -0.01 | -0.55 | -0.22 | 0.12 | 0.48 | 3 **Y** | 0.05 | -2.6 | +0.16 | - | - |
| 23:00-23:15 | 951 | +0.14 | +0.00 | +2.03 | 0.45 | 0.34 | -0.00 | -0.10 | 0.22 | 2 | 0.04 | +2.2 | -0.03 | - | - |
| 04:30-04:45 | 952 | -0.23 | +0.00 | -2.03 | -0.85 | -0.32 | 0.00 | -0.00 | -0.16 | 3 **Y** | 0.07 | -2.2 | +0.08 | - | - |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 7.4 bps vs narrow-day 6.4 bps (x1.17); mean volume wide/narrow x1.22. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: 15:45 narrow +0.51 (t +3.1, n 445)

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| 08:30 releases | 952 | +0.39 (+1.4) | -0.85 | -0.78 | -0.89 (-1.5) | -0.82 (-1.2) | 8.4/13.5 | 1.91 | -0.23 (-0.6, 46%) |
| 08:30 first-Friday (NFP) subset | 45 | +0.79 (+0.6) | -7.04 | -7.47 | -7.04 (-1.2) | -6.05 (-1.0) | 26.8/32.8 | 4.27 | +1.44 (+0.5, 51%) |
| 13:00 (auction time; auction calendar not on disk, all days) | 919 | +0.10 (+0.5) | +0.10 | +0.16 | +0.11 (+0.5) | +0.24 (+0.8) | 3.0/6.0 | 1.24 | -0.05 (-0.2, 41%) |
| 15:00 close | 919 | -0.01 (-0.1) | -0.13 | -0.12 | +0.06 (+0.4) | +0.70 (+3.0) | 2.2/4.7 | 0.96 | -0.63 (-3.3, 37%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| 08:30 releases | -1.8 / -0.3 / 1.75 (n152) | -1.4 / -0.3 / 1.93 (n258) | -0.6 / +0.0 / 2.25 (n259) | -0.0 / -0.4 / 1.69 (n257) | -1.9 / -0.4 / 1.64 (n26) | 4 | 3 |
| 08:30 first-Friday (NFP) subset | -23.2 / -1.6 / 4.15 (n7) | -9.0 / +3.3 / 3.77 (n12) | -4.6 / -5.3 / 6.24 (n12) | +1.0 / +8.2 / 3.24 (n12) | -1.4 / - / 0.93 (n2) | 3 | 2 |
| 13:00 (auction time; auction calendar not on disk, all days) | +0.2 / +0.3 / 1.24 (n147) | -0.1 / +0.1 / 1.28 (n249) | +0.1 / -0.4 / 1.27 (n250) | +0.2 / -0.1 / 1.18 (n248) | +0.3 / -0.1 / 1.06 (n25) | 3 | 2 |
| 15:00 close | -0.7 / -0.6 / 0.91 (n147) | +0.4 / -1.1 / 0.95 (n249) | -0.4 / -0.2 / 1.04 (n250) | +0.6 / -0.6 / 0.95 (n248) | +0.6 / -1.3 / 0.95 (n25) | 2 | 4 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- 08:30 releases: ret -0.2 +0.1 -0.1 +0.4 +0.1 +0.0 -0.8 -0.0 +0.1 -0.2 -0.0 +0.1 +0.3 -0.1 -0.0 -0.2 +0.2 -0.1 | rng 3 3 3 4 5 4 11 5 5 5 4 4 5 4 4 4 4 4 (peak range step at +0 min, 3.0x the pre-event average)
- 08:30 first-Friday (NFP) subset: ret -0.4 -0.3 -0.5 +0.3 +0.3 +1.3 -7.0 -0.6 +0.2 -1.3 +0.7 +1.1 -0.2 -0.5 +1.8 -1.3 +0.5 +0.7 | rng 3 3 3 3 5 6 34 9 8 8 7 6 6 6 6 5 5 5 (peak range step at +0 min, 8.4x the pre-event average)
- 13:00 (auction time; auction calendar not on disk, all days): ret -0.0 -0.0 +0.0 +0.1 -0.0 +0.0 +0.1 +0.1 -0.0 -0.1 +0.1 -0.0 +0.1 +0.0 +0.0 +0.0 -0.1 +0.0 | rng 3 3 3 3 3 3 4 3 3 3 3 3 3 3 2 2 2 2 (peak range step at +0 min, 1.6x the pre-event average)
- 15:00 close: ret -0.0 +0.0 -0.0 +0.1 +0.2 -0.2 -0.1 -0.0 +0.0 +0.0 +0.1 +0.1 -0.0 +0.2 +0.0 -0.0 +0.1 +0.4 | rng 3 3 3 3 3 3 3 3 2 2 2 2 2 2 2 2 2 3 (peak range step at -5 min, 1.2x the pre-event average)

**Windows worth a rule (ZN; 6 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT | 15:00 close: range x1.0 after vs before (0/4 yrs >=1.3); first-5-min follow-through -0.63 bps (t -3.3, same sign 4/4) | post-event rule: trade the first-5-min move after the event as reversal (fade), bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 2 | EVENT | 08:30 releases: range x1.9 after vs before (4/4 yrs >=1.3); first-5-min follow-through -0.23 bps (t -0.6, same sign 3/4) | post-event rule: trade the first-5-min move after the event as reversal (fade), bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 3 | EVENT | 08:30 first-Friday (NFP) subset: range x4.3 after vs before (4/4 yrs >=1.3); first-5-min follow-through +1.44 bps (t +0.5, same sign 2/4) | post-event rule: trade the first-5-min move after the event as continuation, bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 4 | RANGE | 10:00-10:15 ET range x2.44 of median (min-year x2.29) | range-expansion rule: break of the prior 15-min range (09:45-10:00) with a bracket at 1x/1.5x the median window range (5 bps ~ 4 ticks), flat at 10:15 |
| 5 | RANGE | 09:30-09:45 ET range x2.05 of median (min-year x1.98) | range-expansion rule: break of the prior 15-min range (09:15-09:30) with a bracket at 1x/1.5x the median window range (5 bps ~ 4 ticks), flat at 09:45 |
| 6 | RANGE | 09:00-09:15 ET range x1.94 of median (min-year x1.86) | range-expansion rule: break of the prior 15-min range (08:45-09:00) with a bracket at 1x/1.5x the median window range (5 bps ~ 4 ticks), flat at 09:15 |

## ZB
Days 948 (trade dates 2022-06-01..2026-02-06); median level 119.2; anchor for the day-type split 08:20 ET (first hour 08:20-+60 min; wide = first-hour range above the prior-20-day median, 50% of days); median 15-min window range 9.1 bps; round-trip cost for a one-window trade (1 tick adverse each side + 4.84 fee) = 5.65 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 24% | 7% | -1.01 | -0.028 |
| Europe 03:00-08:00 | 20 | 21% | 13% | -0.76 | -0.038 |
| Pre-open 08:00-09:30 | 6 | 13% | 18% | -1.14 | -0.190 |
| US RTH 09:30-16:00 | 26 | 38% | 57% | +1.21 | +0.047 |
| Post 16:00-17:00 | 4 | 4% | 5% | +0.05 | +0.013 |

**Range expansion** (mean window range >= 1.5x the market median window; 15 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 08:30-08:45 | 3.46 | 12.2 | 8.15 | 3.16 |
| 10:00-10:15 | 2.49 | 8.8 | 6.72 | 2.30 |
| 09:30-09:45 | 2.29 | 8.1 | 5.88 | 2.15 |
| 09:00-09:15 | 2.13 | 7.6 | 5.24 | 2.01 |
| 09:45-10:00 | 2.11 | 7.5 | 5.55 | 1.92 |
| 08:45-09:00 | 2.11 | 7.5 | 5.49 | 2.03 |
| 08:15-08:30 | 2.06 | 7.3 | 4.71 | 1.85 |
| 10:15-10:30 | 1.96 | 7.0 | 5.33 | 1.89 |
| 09:15-09:30 | 1.92 | 6.8 | 4.80 | 1.76 |
| 10:30-10:45 | 1.89 | 6.7 | 4.89 | 1.77 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 14 windows; runs (ET): 00:00-01:30, 18:45-19:00, 22:15-00:00.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 7 of 92 windows (null expectation ~4.2); |t|>=3 in 2 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 7 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 15:45-16:00 | 915 | +0.94 | +0.00 | +3.40 | 1.66 | 0.98 | 0.79 | 0.82 | -0.87 | 4 **Y** | 0.17 | +3.1 | +0.61 | +0.85 (+2.1) | +0.90 (+2.4) |
| 16:30-16:45 | 915 | +0.52 | +0.00 | +3.03 | 0.48 | 0.48 | 0.34 | 0.77 | 0.43 | 4 **Y** | 0.09 | +2.7 | +0.50 | +0.83 (+3.3) | +0.19 (+0.9) |
| 03:00-03:15 | 948 | -0.82 | +0.00 | -2.95 | -1.09 | -1.44 | -0.60 | -0.24 | -1.15 | 4 **Y** | 0.15 | -2.7 | -0.62 | - | - |
| 01:15-01:30 | 941 | +0.32 | +0.00 | +2.53 | 0.20 | 0.22 | 0.50 | 0.30 | 0.52 | 4 **Y** | 0.06 | +2.4 | +0.14 | - | - |
| 02:15-02:30 | 947 | +0.52 | +0.00 | +2.45 | 1.01 | 0.59 | 0.48 | 0.26 | 0.10 | 4 **Y** | 0.09 | +2.5 | +0.08 | - | - |
| 19:00-19:15 | 923 | -0.32 | +0.00 | -2.11 | -0.74 | -0.05 | -0.33 | -0.20 | -1.47 | 4 **Y** | 0.06 | -1.7 | -0.45 | - | - |
| 18:30-18:45 | 923 | -0.27 | +0.00 | -2.06 | -0.12 | -0.80 | -0.49 | 0.21 | 1.52 | 3 **Y** | 0.05 | -2.5 | +0.22 | - | - |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 13.5 bps vs narrow-day 11.8 bps (x1.15); mean volume wide/narrow x1.19. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: 16:30 wide +0.83 (t +3.3, n 467); 11:15 narrow -0.98 (t -2.5, n 469)

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| 08:30 releases | 948 | +0.32 (+0.6) | -1.47 | -1.60 | -1.84 (-1.9) | -1.48 (-1.3) | 13.3/24.2 | 1.78 | +0.52 (+0.8, 48%) |
| 08:30 first-Friday (NFP) subset | 45 | -0.20 (-0.1) | -13.19 | -16.76 | -17.77 (-1.9) | -16.19 (-1.6) | 39.4/52.1 | 3.71 | +3.05 (+0.5, 54%) |
| 13:00 (auction time; auction calendar not on disk, all days) | 915 | +0.40 (+1.1) | -0.04 | +0.09 | +0.00 (+0.0) | +0.48 (+0.8) | 5.8/11.8 | 1.28 | -0.12 (-0.3, 43%) |
| 15:00 close | 915 | -0.20 (-0.6) | -0.04 | -0.00 | +0.09 (+0.3) | +1.41 (+3.2) | 3.7/8.9 | 0.99 | -0.77 (-2.3, 37%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| 08:30 releases | -3.2 / +2.4 / 1.64 (n151) | -2.1 / -0.1 / 1.76 (n256) | -1.6 / +0.2 / 2.08 (n258) | -0.9 / +0.6 / 1.66 (n257) | -3.3 / -1.7 / 1.53 (n26) | 4 | 3 |
| 08:30 first-Friday (NFP) subset | -46.7 / +10.4 / 3.20 (n7) | -20.4 / -5.4 / 3.37 (n12) | -15.2 / -8.0 / 5.49 (n12) | -3.0 / +18.9 / 2.94 (n12) | -4.1 / - / 1.00 (n2) | 4 | 2 |
| 13:00 (auction time; auction calendar not on disk, all days) | -0.2 / -0.7 / 1.28 (n146) | -0.7 / +0.8 / 1.28 (n247) | -0.1 / -1.1 / 1.33 (n249) | +0.8 / +0.4 / 1.24 (n248) | +1.7 / -1.5 / 1.06 (n25) | 1 | 2 |
| 15:00 close | -1.8 / -0.6 / 0.96 (n146) | +1.0 / -1.5 / 1.01 (n247) | -0.4 / +0.1 / 1.04 (n249) | +0.9 / -1.0 / 0.95 (n248) | -0.2 / -1.4 / 0.86 (n25) | 2 | 3 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- 08:30 releases: ret -0.5 +0.4 -0.4 +0.6 +0.2 +0.0 -1.5 -0.1 -0.0 -0.2 -0.1 +0.1 +0.3 -0.1 -0.1 -0.3 +0.4 +0.1 | rng 3 3 3 4 5 4 9 5 5 4 4 4 5 4 4 4 4 4 (peak range step at +0 min, 2.6x the pre-event average)
- 08:30 first-Friday (NFP) subset: ret -0.6 -0.5 -1.3 +0.1 -0.4 +2.6 -13.2 -2.6 -1.0 -2.6 +0.8 +0.8 +0.2 -0.8 +2.6 -1.7 +0.9 +0.4 | rng 3 3 3 3 5 5 26 8 7 7 7 6 6 6 5 5 5 4 (peak range step at +0 min, 7.0x the pre-event average)
- 13:00 (auction time; auction calendar not on disk, all days): ret +0.0 +0.0 -0.0 +0.2 +0.0 +0.2 -0.0 +0.2 -0.0 -0.0 +0.2 -0.2 +0.3 +0.0 +0.1 +0.2 -0.1 -0.0 | rng 3 2 2 2 2 3 4 3 3 3 2 2 2 2 2 2 2 2 (peak range step at +0 min, 1.7x the pre-event average)
- 15:00 close: ret -0.1 -0.0 +0.0 -0.0 +0.3 -0.4 -0.0 -0.2 +0.3 -0.0 +0.0 +0.1 +0.0 +0.3 +0.2 +0.0 +0.3 +0.6 | rng 2 2 2 2 3 3 3 2 2 2 2 2 2 2 2 2 2 3 (peak range step at +55 min, 1.4x the pre-event average)

**Windows worth a rule (ZB; 6 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT | 15:00 close: range x1.0 after vs before (0/4 yrs >=1.3); first-5-min follow-through -0.77 bps (t -2.3, same sign 3/4) | post-event rule: trade the first-5-min move after the event as reversal (fade), bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 2 | EVENT | 08:30 releases: range x1.8 after vs before (4/4 yrs >=1.3); first-5-min follow-through +0.52 bps (t +0.8, same sign 3/4) | post-event rule: trade the first-5-min move after the event as continuation, bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 3 | EVENT | 08:30 first-Friday (NFP) subset: range x3.7 after vs before (4/4 yrs >=1.3); first-5-min follow-through +3.05 bps (t +0.5, same sign 2/4) | post-event rule: trade the first-5-min move after the event as continuation, bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 4 | RANGE | 10:00-10:15 ET range x2.49 of median (min-year x2.30) | range-expansion rule: break of the prior 15-min range (09:45-10:00) with a bracket at 1x/1.5x the median window range (9 bps ~ 4 ticks), flat at 10:15 |
| 5 | RANGE | 09:30-09:45 ET range x2.29 of median (min-year x2.15) | range-expansion rule: break of the prior 15-min range (09:15-09:30) with a bracket at 1x/1.5x the median window range (9 bps ~ 4 ticks), flat at 09:45 |
| 6 | RANGE | 09:00-09:15 ET range x2.13 of median (min-year x2.01) | range-expansion rule: break of the prior 15-min range (08:45-09:00) with a bracket at 1x/1.5x the median window range (9 bps ~ 4 ticks), flat at 09:15 |

## GC
Days 947 (trade dates 2022-06-01..2026-02-06); median level 2,305; anchor for the day-type split 03:00 ET (first hour 03:00-+60 min; wide = first-hour range above the prior-20-day median, 50% of days); median 15-min window range 12.7 bps; round-trip cost for a one-window trade (1 tick adverse each side + 4.84 fee) = 1.08 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 33% | 21% | +4.29 | +0.119 |
| Europe 03:00-08:00 | 20 | 21% | 18% | +2.23 | +0.112 |
| Pre-open 08:00-09:30 | 6 | 11% | 15% | +0.40 | +0.066 |
| US RTH 09:30-16:00 | 26 | 34% | 44% | +0.30 | +0.012 |
| Post 16:00-17:00 | 4 | 2% | 1% | +1.68 | +0.420 |

**Range expansion** (mean window range >= 1.5x the market median window; 12 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 08:30-08:45 | 2.55 | 80.8 | 4.72 | 1.82 |
| 10:00-10:15 | 2.39 | 80.1 | 5.11 | 2.02 |
| 09:30-09:45 | 2.33 | 79.5 | 4.55 | 2.13 |
| 09:45-10:00 | 2.10 | 70.4 | 4.18 | 1.88 |
| 10:15-10:30 | 1.97 | 68.2 | 3.56 | 1.75 |
| 10:30-10:45 | 1.86 | 63.0 | 3.36 | 1.60 |
| 09:00-09:15 | 1.84 | 61.8 | 3.33 | 1.63 |
| 08:15-08:30 | 1.72 | 57.1 | 2.79 | 1.49 |
| 08:45-09:00 | 1.71 | 56.1 | 3.02 | 1.46 |
| 11:00-11:15 | 1.67 | 57.1 | 2.89 | 1.49 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 2 windows; runs (ET): 16:15-16:45.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 8 of 92 windows (null expectation ~4.2); |t|>=3 in 3 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 7 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 16:45-17:00 | 909 | +1.04 | +0.58 | +4.79 | 0.53 | 1.28 | 1.45 | -0.00 | 8.01 | 3 **Y** | 0.96 | +5.1 | +0.99 | +1.51 (+4.3) | +0.61 (+2.5) |
| 05:00-05:15 | 946 | +1.18 | +1.08 | +4.21 | 1.31 | 0.26 | 1.27 | 1.24 | 8.01 | 4 **Y** | 1.10 | +3.5 | +2.41 | +1.55 (+3.3) | +0.86 (+2.7) |
| 05:15-05:30 | 945 | -0.89 | -0.62 | -3.22 | -0.03 | -0.34 | -1.08 | -0.97 | -8.56 | 4 **Y** | 0.83 | -1.7 | -3.08 | -1.30 (-2.9) | -0.51 (-1.6) |
| 05:30-05:45 | 946 | +0.69 | +0.58 | +2.65 | -0.23 | 0.74 | 1.03 | 0.16 | 7.38 | 3 **Y** | 0.64 | +1.9 | +1.55 | +1.20 (+2.8) | +0.13 (+0.4) |
| 13:15-13:30 | 945 | -0.84 | -0.43 | -2.35 | -0.80 | 0.29 | -0.42 | -1.61 | -8.62 | 3 **Y** | 0.78 | -1.5 | -2.51 | -1.49 (-2.5) | -0.17 (-0.4) |
| 20:30-20:45 | 947 | +0.73 | +0.38 | +2.29 | -0.59 | -0.05 | 1.14 | 1.16 | 7.65 | 2 | 0.68 | +0.1 | +4.29 | - | - |
| 21:45-22:00 | 947 | -0.87 | -0.38 | -2.28 | -0.63 | -0.20 | 0.28 | -2.01 | -8.76 | 3 **Y** | 0.80 | -1.4 | -3.20 | - | - |
| 12:45-13:00 | 947 | +0.57 | +0.85 | +2.01 | -0.57 | 0.28 | 1.63 | 0.86 | -3.26 | 3 **Y** | 0.53 | +2.2 | +0.38 | +0.48 (+1.1) | +0.70 (+1.9) |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 16.8 bps vs narrow-day 14.1 bps (x1.19); mean volume wide/narrow x1.10. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: 16:45 wide +1.51 (t +4.3, n 459); 05:00 wide +1.55 (t +3.3, n 469); 05:15 wide -1.30 (t -2.9, n 469); 05:30 wide +1.20 (t +2.8, n 469); 05:00 narrow +0.86 (t +2.7, n 467)

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| 10:30 London (AM fix, ~05:30 ET) | 946 | +0.07 (+0.2) | +0.08 | +0.27 | +0.62 (+1.6) | +1.32 (+2.4) | 3.8/11.8 | 1.02 | +0.17 (+0.5, 48%) |
| 15:00 London (PM fix, ~10:00 ET) | 947 | -0.53 (-0.6) | -1.24 | +0.31 | -0.58 (-0.6) | -0.41 (-0.3) | 9.9/25.2 | 1.07 | +1.32 (+1.3, 50%) |
| 13:30 settle | 941 | -1.03 (-2.1) | +0.55 | +0.63 | +1.04 (+2.1) | +1.59 (+2.3) | 4.6/12.1 | 0.94 | +1.03 (+1.9, 49%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| 10:30 London (AM fix, ~05:30 ET) | -0.5 / +0.4 / 1.03 (n150) | +1.0 / -0.3 / 1.05 (n255) | +1.2 / +0.4 / 1.02 (n258) | -0.6 / -0.7 / 1.00 (n257) | +10.2 / +9.3 / 1.00 (n26) | 2 | 2 |
| 15:00 London (PM fix, ~10:00 ET) | -0.9 / +2.2 / 1.08 (n150) | +0.9 / +0.6 / 1.08 (n255) | -0.9 / +0.7 / 1.10 (n258) | +1.7 / +2.5 / 1.02 (n258) | -32.0 / -2.5 / 1.14 (n26) | 2 | 4 |
| 13:30 settle | -1.2 / -0.0 / 0.99 (n149) | +1.1 / +0.5 / 0.90 (n254) | +0.6 / +0.1 / 0.89 (n257) | +1.3 / +1.7 / 0.98 (n255) | +14.5 / +14.2 / 1.04 (n26) | 3 | 3 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- 10:30 London (AM fix, ~05:30 ET): ret +0.6 +0.2 +0.4 -0.1 -0.2 -0.7 +0.1 +0.2 +0.0 +0.2 +0.1 +0.1 -0.0 +0.0 +0.3 +0.1 +0.1 +0.2 | rng 19 18 17 17 17 17 21 17 16 16 16 16 18 17 17 17 17 17 (peak range step at +0 min, 1.2x the pre-event average)
- 15:00 London (PM fix, ~10:00 ET): ret +0.2 -0.5 -0.2 +0.0 +0.4 -0.5 -1.2 +1.2 +0.3 -0.5 -0.3 -0.1 +0.1 +0.3 -0.3 +0.3 -0.4 +0.1 | rng 44 42 39 44 36 33 50 41 37 36 36 34 36 34 31 31 29 27 (peak range step at +0 min, 1.2x the pre-event average)
- 13:30 settle: ret +0.1 -0.1 -0.2 -0.2 -0.0 -0.6 +0.5 -0.0 +0.1 +0.4 +0.1 -0.1 -0.1 +0.1 +0.2 +0.1 +0.1 +0.1 | rng 22 19 19 19 20 23 22 18 17 16 16 15 22 19 17 17 16 16 (peak range step at -5 min, 1.1x the pre-event average)

**Windows worth a rule (GC; 10 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT-DRIFT | 13:30 settle: 0..+30 min drift +1.04 bps (t +2.1, same sign 3/4 yrs) | drift rule: long at the event, flat at +30 min |
| 2 | DRIFT | 16:45-17:00 ET drift +1.04 bps (t +4.8, same sign 3/4 yrs, 0.96x cost; selection-span t +5.1, late-span mean +0.99) | drift rule: long at 16:45 open, flat at 17:00 |
| 3 | DRIFT | 05:00-05:15 ET drift +1.18 bps (t +4.2, same sign 4/4 yrs, 1.10x cost; selection-span t +3.5, late-span mean +2.41) | drift rule: long at 05:00 open, flat at 05:15 |
| 4 | DRIFT | 05:15-05:30 ET drift -0.89 bps (t -3.2, same sign 4/4 yrs, 0.83x cost; selection-span t -1.7, late-span mean -3.08) | drift rule: short at 05:15 open, flat at 05:30 |
| 5 | DRIFT | 05:30-05:45 ET drift +0.69 bps (t +2.7, same sign 3/4 yrs, 0.64x cost; selection-span t +1.9, late-span mean +1.55) | drift rule: long at 05:30 open, flat at 05:45 |
| 6 | DRIFT | 13:15-13:30 ET drift -0.84 bps (t -2.4, same sign 3/4 yrs, 0.78x cost; selection-span t -1.5, late-span mean -2.51) | drift rule: short at 13:15 open, flat at 13:30 |
| 7 | DRIFT | 21:45-22:00 ET drift -0.87 bps (t -2.3, same sign 3/4 yrs, 0.80x cost; selection-span t -1.4, late-span mean -3.20) | drift rule: short at 21:45 open, flat at 22:00 |
| 8 | RANGE | 08:30-08:45 ET range x2.55 of median (min-year x1.82) | range-expansion rule: break of the prior 15-min range (08:15-08:30) with a bracket at 1x/1.5x the median window range (13 bps ~ 35 ticks), flat at 08:45 |
| 9 | RANGE | 10:00-10:15 ET range x2.39 of median (min-year x2.02) | range-expansion rule: break of the prior 15-min range (09:45-10:00) with a bracket at 1x/1.5x the median window range (13 bps ~ 35 ticks), flat at 10:15 |
| 10 | RANGE | 09:30-09:45 ET range x2.33 of median (min-year x2.13) | range-expansion rule: break of the prior 15-min range (09:15-09:30) with a bracket at 1x/1.5x the median window range (13 bps ~ 35 ticks), flat at 09:45 |

## 6E
Days 952 (trade dates 2022-06-01..2026-02-06); median level 1.086; anchor for the day-type split 03:00 ET (first hour 03:00-+60 min; wide = first-hour range above the prior-20-day median, 50% of days); median 15-min window range 6.2 bps; round-trip cost for a one-window trade (1 tick adverse each side + 5.30 fee) = 1.31 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 27% | 14% | +0.30 | +0.008 |
| Europe 03:00-08:00 | 20 | 26% | 26% | -0.71 | -0.035 |
| Pre-open 08:00-09:30 | 6 | 11% | 15% | +0.71 | +0.118 |
| US RTH 09:30-16:00 | 26 | 33% | 43% | +0.16 | +0.006 |
| Post 16:00-17:00 | 4 | 2% | 1% | +0.52 | +0.129 |

**Range expansion** (mean window range >= 1.5x the market median window; 15 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 08:30-08:45 | 2.73 | 36.9 | 4.13 | 2.26 |
| 10:00-10:15 | 2.35 | 31.8 | 3.76 | 2.04 |
| 10:45-11:00 | 1.85 | 24.9 | 3.57 | 1.71 |
| 10:15-10:30 | 1.84 | 24.8 | 2.60 | 1.66 |
| 08:45-09:00 | 1.82 | 24.6 | 2.67 | 1.58 |
| 09:00-09:15 | 1.82 | 24.6 | 2.64 | 1.59 |
| 09:45-10:00 | 1.81 | 24.4 | 2.91 | 1.59 |
| 10:30-10:45 | 1.79 | 24.2 | 2.48 | 1.57 |
| 09:30-09:45 | 1.79 | 24.1 | 2.67 | 1.57 |
| 09:15-09:30 | 1.64 | 22.1 | 2.15 | 1.48 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 14 windows; runs (ET): 00:00-00:45, 16:15-17:00, 18:15-19:00, 19:15-19:45, 23:15-00:00.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 12 of 92 windows (null expectation ~4.2); |t|>=3 in 5 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 12 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 16:45-17:00 | 943 | +0.37 | +0.45 | +4.40 | 0.12 | 0.31 | 0.25 | 0.70 | 0.23 | 4 **Y** | 0.28 | +4.4 | +0.20 | +0.42 (+3.7) | +0.33 (+2.6) |
| 07:45-08:00 | 951 | -0.78 | -0.91 | -4.32 | -1.01 | -1.36 | -0.47 | -0.44 | -0.06 | 4 **Y** | 0.59 | -4.7 | +0.13 | -0.89 (-3.4) | -0.55 (-2.3) |
| 08:00-08:15 | 951 | +0.64 | +0.91 | +3.62 | 0.02 | 0.96 | 0.89 | 0.52 | -0.12 | 4 **Y** | 0.49 | +3.8 | +0.01 | +0.88 (+3.2) | +0.34 (+1.5) |
| 02:45-03:00 | 951 | -0.63 | -0.46 | -3.41 | -1.18 | -0.45 | -0.29 | -0.80 | -0.79 | 4 **Y** | 0.48 | -2.8 | -0.82 | - | - |
| 03:00-03:15 | 951 | +0.72 | +0.86 | +3.01 | 1.25 | 0.81 | 0.10 | 1.00 | 0.18 | 4 **Y** | 0.55 | +2.7 | +0.54 | - | - |
| 04:30-04:45 | 951 | +0.45 | +0.46 | +2.54 | 0.88 | 0.69 | 0.14 | 0.35 | -0.29 | 4 **Y** | 0.35 | +2.6 | +0.05 | +0.79 (+2.7) | +0.15 (+0.7) |
| 14:30-14:45 | 946 | +0.47 | +0.00 | +2.40 | 1.48 | 0.53 | 0.21 | 0.03 | 0.88 | 4 **Y** | 0.36 | +3.2 | -0.66 | +0.38 (+1.5) | +0.58 (+2.0) |
| 00:00-00:15 | 951 | -0.23 | +0.00 | -2.39 | -0.42 | -0.28 | -0.08 | -0.24 | 0.16 | 4 **Y** | 0.17 | -2.6 | +0.03 | - | - |
| 13:15-13:30 | 948 | -0.35 | +0.00 | -2.21 | -0.71 | -0.22 | -0.02 | -0.64 | 0.18 | 4 **Y** | 0.26 | -2.1 | -0.19 | -0.48 (-2.1) | -0.19 (-0.9) |
| 22:00-22:15 | 951 | +0.25 | +0.00 | +2.18 | 0.25 | 0.20 | -0.19 | 0.74 | 0.24 | 3 **Y** | 0.19 | +1.7 | +0.42 | - | - |
| 00:15-00:30 | 951 | +0.18 | +0.00 | +2.13 | 0.43 | 0.01 | 0.04 | 0.33 | 0.13 | 4 **Y** | 0.13 | +2.4 | -0.03 | - | - |
| 05:00-05:15 | 951 | +0.37 | +0.46 | +2.02 | 0.53 | 0.40 | 0.18 | 0.44 | 0.28 | 4 **Y** | 0.28 | +1.6 | +0.54 | +0.33 (+1.2) | +0.43 (+1.9) |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 8.2 bps vs narrow-day 7.3 bps (x1.12); mean volume wide/narrow x1.12. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: 16:45 wide +0.42 (t +3.7, n 466); 07:45 wide -0.89 (t -3.4, n 468); 08:00 wide +0.88 (t +3.2, n 468); 04:30 wide +0.79 (t +2.7, n 468); 16:45 narrow +0.33 (t +2.6, n 467)

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| 08:30 releases | 951 | +0.80 (+2.8) | -0.01 | -0.02 | -0.06 (-0.1) | +0.10 (+0.1) | 7.1/13.5 | 1.83 | -0.15 (-0.4, 48%) |
| 16:00 London (close, ~11:00 ET) | 951 | +0.01 (+0.0) | +0.04 | +0.13 | +0.13 (+0.4) | -0.14 (-0.4) | 3.0/8.6 | 0.89 | +0.22 (+0.7, 50%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| 08:30 releases | +0.2 / -1.1 / 1.59 (n152) | -0.6 / +0.4 / 1.98 (n257) | -0.5 / +0.9 / 2.20 (n259) | +0.7 / -1.3 / 1.64 (n257) | +1.2 / +1.4 / 1.52 (n26) | 2 | 2 |
| 16:00 London (close, ~11:00 ET) | +0.0 / -0.1 / 0.87 (n152) | +0.7 / -0.1 / 0.87 (n256) | -0.1 / +0.0 / 0.90 (n259) | -0.0 / +0.9 / 0.91 (n258) | -1.0 / +0.7 / 0.91 (n26) | 2 | 2 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- 08:30 releases: ret +0.7 -0.3 +0.2 +0.0 +0.2 -0.1 -0.0 -0.0 +0.0 -0.1 +0.0 +0.0 +0.1 +0.2 -0.1 -0.2 -0.0 +0.1 | rng 11 10 10 12 12 11 29 16 15 15 14 13 14 14 13 13 13 12 (peak range step at +0 min, 2.6x the pre-event average)
- 16:00 London (close, ~11:00 ET): ret -0.1 +0.2 -0.3 +0.0 -0.4 +0.5 +0.0 -0.1 +0.2 -0.1 +0.1 -0.0 +0.0 -0.1 -0.0 +0.2 -0.1 -0.2 | rng 14 13 13 14 16 12 13 12 12 11 11 10 11 10 10 10 9 10 (peak range step at -10 min, 1.1x the pre-event average)

**Windows worth a rule (6E; 10 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT | 08:30 releases: range x1.8 after vs before (4/4 yrs >=1.3); first-5-min follow-through -0.15 bps (t -0.4, same sign 2/4) | post-event rule: trade the first-5-min move after the event as reversal (fade), bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 2 | DRIFT (below 0.5x cost) | 16:45-17:00 ET drift +0.37 bps (t +4.4, same sign 4/4 yrs, 0.28x cost; selection-span t +4.4, late-span mean +0.20) | drift rule: long at 16:45 open, flat at 17:00 |
| 3 | DRIFT | 07:45-08:00 ET drift -0.78 bps (t -4.3, same sign 4/4 yrs, 0.59x cost; selection-span t -4.7, late-span mean +0.13) | drift rule: short at 07:45 open, flat at 08:00 |
| 4 | DRIFT (below 0.5x cost) | 08:00-08:15 ET drift +0.64 bps (t +3.6, same sign 4/4 yrs, 0.49x cost; selection-span t +3.8, late-span mean +0.01) | drift rule: long at 08:00 open, flat at 08:15 |
| 5 | DRIFT (below 0.5x cost) | 02:45-03:00 ET drift -0.63 bps (t -3.4, same sign 4/4 yrs, 0.48x cost; selection-span t -2.8, late-span mean -0.82) | drift rule: short at 02:45 open, flat at 03:00 |
| 6 | DRIFT | 03:00-03:15 ET drift +0.72 bps (t +3.0, same sign 4/4 yrs, 0.55x cost; selection-span t +2.7, late-span mean +0.54) | drift rule: long at 03:00 open, flat at 03:15 |
| 7 | DRIFT (below 0.5x cost) | 04:30-04:45 ET drift +0.45 bps (t +2.5, same sign 4/4 yrs, 0.35x cost; selection-span t +2.6, late-span mean +0.05) | drift rule: long at 04:30 open, flat at 04:45 |
| 8 | RANGE | 10:00-10:15 ET range x2.35 of median (min-year x2.04) | range-expansion rule: break of the prior 15-min range (09:45-10:00) with a bracket at 1x/1.5x the median window range (6 bps ~ 14 ticks), flat at 10:15 |
| 9 | RANGE | 10:45-11:00 ET range x1.85 of median (min-year x1.71) | range-expansion rule: break of the prior 15-min range (10:30-10:45) with a bracket at 1x/1.5x the median window range (6 bps ~ 14 ticks), flat at 11:00 |
| 10 | RANGE | 09:00-09:15 ET range x1.82 of median (min-year x1.59) | range-expansion rule: break of the prior 15-min range (08:45-09:00) with a bracket at 1x/1.5x the median window range (6 bps ~ 14 ticks), flat at 09:15 |

## NQ (reference)
Days 952 (trade dates 2022-06-01..2026-02-06); median level 1.812e+04; anchor for the day-type split 09:30 ET (first hour 09:30-+60 min; wide = first-hour range above the prior-20-day median, 50% of days); median 15-min window range 12.7 bps; round-trip cost for a one-window trade (1 tick adverse each side + 4.84 fee) = 0.41 bps.

Session shape (share of summed 15-min mean range and of volume; sum of the pooled mean signed window returns = the segment drift, bps):

| segment (ET) | windows | range share | volume share | segment drift bps | mean per window |
|---|---|---|---|---|---|
| Asia 18:00-03:00 | 36 | 23% | 7% | +0.51 | +0.014 |
| Europe 03:00-08:00 | 20 | 18% | 7% | +1.03 | +0.052 |
| Pre-open 08:00-09:30 | 6 | 8% | 6% | -0.60 | -0.100 |
| US RTH 09:30-16:00 | 26 | 48% | 77% | +3.07 | +0.118 |
| Post 16:00-17:00 | 4 | 3% | 3% | +1.35 | +0.338 |

**Range expansion** (mean window range >= 1.5x the market median window; 29 windows). Top 10 (ET start-end, range x median, range in ticks, volume x median, lowest-year range ratio vs that year's median window):

| window | range x med | range ticks | vol x med | min-year ratio |
|---|---|---|---|---|
| 09:30-09:45 | 3.93 | 339.1 | 21.15 | 3.60 |
| 10:00-10:15 | 3.32 | 285.0 | 14.91 | 3.03 |
| 09:45-10:00 | 3.25 | 281.3 | 14.98 | 3.13 |
| 10:15-10:30 | 2.82 | 244.9 | 12.10 | 2.66 |
| 10:30-10:45 | 2.67 | 229.3 | 11.37 | 2.35 |
| 08:30-08:45 | 2.50 | 207.6 | 4.32 | 1.88 |
| 15:45-16:00 | 2.49 | 215.3 | 15.35 | 2.32 |
| 10:45-11:00 | 2.46 | 213.9 | 10.19 | 2.25 |
| 11:00-11:15 | 2.36 | 202.6 | 9.51 | 2.15 |
| 11:15-11:30 | 2.12 | 183.6 | 8.38 | 2.06 |

**Dead windows** (range <= 0.6x and volume <= 0.6x the median window): 7 windows; runs (ET): 00:15-01:00, 22:45-23:00, 23:15-00:00.

**Drift** (pooled signed return, open to close of the window; the 18:00-18:15 Globex reopen window starts at the first print of the session, which is not a tradable entry, and is excluded from the rule list). |t|>=2 in 3 of 92 windows (null expectation ~4.2); |t|>=3 in 1 (null ~0.3). Year-consistent flag = |t|>=2 AND same sign in >=3 of the 4 years 2022(Jun-Dec),2023,2024,2025: 3 windows. Day-type columns are shown only where the window starts >=60 min after the anchor (otherwise look-ahead, "-"). cost = |mean|/round-trip cost.

| window | n | mean bps | median | t | 2022 | 2023 | 2024 | 2025 | 2026* | same sign /4 | abs mean/cost | sel-span t (to 2025-06) | late mean (2025-07..) | wide d mean (t) | narrow d mean (t) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10:45-11:00 | 950 | -2.25 | -2.45 | -3.26 | -1.21 | -0.94 | -1.94 | -4.44 | -2.74 | 4 **Y** | 5.48 | -2.2 | -5.03 | -2.37 (-2.1) | -2.07 (-2.5) |
| 02:45-03:00 | 952 | -0.66 | -0.44 | -2.68 | -1.29 | -0.27 | -0.59 | -0.83 | 0.02 | 4 **Y** | 1.62 | -2.4 | -0.61 | - | - |
| 11:00-11:15 | 950 | +1.49 | +2.81 | +2.12 | -0.30 | 3.77 | 1.34 | 0.15 | 4.26 | 3 **Y** | 3.65 | +2.4 | -0.81 | +1.58 (+1.4) | +1.69 (+2.1) |
(*2026 = Jan 1-Feb 6 only; not counted in consistency. Y = year-consistent drift flag. Table = the 14 largest |t| windows with |t|>=2.)

Day type (usable windows only, no look-ahead): mean window range wide-day 25.4 bps vs narrow-day 20.9 bps (x1.22); mean volume wide/narrow x1.14. Pooled signed drift split by day type: the usable windows with |t|>=2 on either type (|t|>=2.5) are listed here: 11:45 narrow +2.01 (t +3.0, n 471); 10:45 narrow -2.07 (t -2.5, n 471)

**Event windows** (profile = -30..+60 min around the event; pre30 = move -30..0; cumN = move 0..+N; abs = mean absolute move; rng ratio = mean 5-min range in the first 15 min after / mean 5-min range in the 30 min before; cont30 = first-5-min-move-aligned follow-through +5..+35, positive = continuation).

| event | n | pre30 bps (t) | cum5 | cum15 | cum30 (t) | cum60 (t) | abs move 5/60 | rng ratio | cont30 bps (t, hit) |
|---|---|---|---|---|---|---|---|---|---|
| 09:30 open | 950 | -0.69 (-1.3) | +0.13 | -0.43 | +0.75 (+0.5) | +0.26 (+0.1) | 17.4/44.1 | 2.79 | +1.98 (+1.4, 51%) |
| 10:00 data | 950 | +0.55 (+0.4) | -0.94 | -0.03 | -0.48 (-0.4) | -1.84 (-1.2) | 13.0/36.3 | 0.93 | +0.37 (+0.3, 51%) |
| 15:50 MOC imbalance | 916 | -1.26 (-1.6) | +0.42 | +0.83 | +1.29 (+1.4) | +1.76 (+1.7) | 10.6/20.9 | 1.35 | +0.11 (+0.1, 50%) |
| 16:00 cash close | 916 | -0.19 (-0.2) | +0.42 | +0.78 | +0.95 (+1.4) | +1.34 (+1.7) | 7.9/13.4 | 0.74 | -0.75 (-1.3, 48%) |

By year (cum30 bps / cont30 bps / rng ratio):

| event | 2022 | 2023 | 2024 | 2025 | 2026* | cum30 same sign /4 | cont30 same sign /4 |
|---|---|---|---|---|---|---|---|
| 09:30 open | +1.8 / +4.1 / 2.84 (n152) | +4.4 / -1.0 / 2.78 (n257) | -2.4 / +3.3 / 2.72 (n259) | +0.2 / +2.2 / 2.78 (n256) | -5.1 / +4.0 / 3.14 (n26) | 3 | 3 |
| 10:00 data | -2.2 / +3.4 / 0.91 (n152) | -1.4 / -2.2 / 0.93 (n257) | +0.1 / -1.3 / 0.96 (n259) | +0.9 / +3.1 / 0.92 (n256) | -1.6 / -1.6 / 0.80 (n26) | 2 | 2 |
| 15:50 MOC imbalance | -1.6 / +0.9 / 1.24 (n147) | +2.8 / -1.4 / 1.29 (n248) | -0.3 / +1.3 / 1.41 (n249) | +3.3 / +0.4 / 1.43 (n247) | -1.1 / -4.5 / 1.62 (n25) | 2 | 3 |
| 16:00 cash close | -0.4 / -0.4 / 0.68 (n147) | +2.5 / +0.9 / 0.71 (n248) | +0.4 / -0.5 / 0.78 (n249) | +0.7 / -2.2 / 0.77 (n247) | +1.0 / -7.0 / 1.05 (n25) | 3 | 3 |

Profiles in words (all years; 5-min steps -30..+55 from the event; mean signed return bps | mean range ticks):
- 09:30 open: ret +0.2 -0.1 -0.0 +0.3 -0.4 -0.6 +0.1 +0.4 -0.9 +0.7 +0.5 +0.1 -0.9 +0.2 +0.8 +0.3 -0.0 -0.7 | rng 81 72 67 66 63 88 236 191 182 185 170 151 192 163 162 148 151 142 (peak range step at +0 min, 3.2x the pre-event average)
- 10:00 data: ret +0.1 +0.3 -0.9 +0.6 +0.4 +0.0 -0.9 +0.2 +0.8 +0.3 -0.0 -0.7 +0.2 +0.3 +0.4 +0.2 -1.8 -0.7 | rng 236 191 182 185 170 151 192 163 162 148 151 142 147 137 132 130 129 120 (peak range step at -30 min, 1.3x the pre-event average)
- 15:50 MOC imbalance: ret +0.0 -0.7 +0.1 -1.2 +0.1 +0.4 +0.4 -0.0 +0.4 +0.5 -0.2 +0.1 +0.1 -0.1 +0.2 +0.1 +0.0 +0.1 | rng 96 92 101 98 97 101 147 130 118 74 59 54 49 41 44 36 33 34 (peak range step at +0 min, 1.5x the pre-event average)
- 16:00 cash close: ret +0.1 -1.2 +0.1 +0.4 +0.4 -0.0 +0.4 +0.5 -0.2 +0.1 +0.1 -0.1 +0.2 +0.1 +0.0 +0.1 -0.1 +0.1 | rng 101 98 97 101 147 130 118 74 59 54 49 41 44 36 33 34 32 35 (peak range step at -10 min, 1.3x the pre-event average)

**Windows worth a rule (NQ; 7 of max 12; selection = event rules with range x>=1.3 in >=3/4 years or drift |t|>=2 same sign >=3/4; drift windows with |t|>=2, >=3/4 years and |mean| >= 0.25x round-trip cost (windows below that are in the table but get no rule); top range-expansion windows with min-year ratio >=1.3 not covered by an event; 15-min windows are in-sample picks from 96 per market, so expect ~2-4 false |t|>=2 per market):**

| # | type | window / evidence | the single obvious rule |
|---|---|---|---|
| 1 | EVENT | 09:30 open: range x2.8 after vs before (4/4 yrs >=1.3); first-5-min follow-through +1.98 bps (t +1.4, same sign 3/4) | post-event rule: trade the first-5-min move after the event as continuation, bracket 1x/1.5x the median 15-min range, flat at +35 min |
| 2 | DRIFT | 10:45-11:00 ET drift -2.25 bps (t -3.3, same sign 4/4 yrs, 5.48x cost; selection-span t -2.2, late-span mean -5.03) | drift rule: short at 10:45 open, flat at 11:00 |
| 3 | DRIFT | 02:45-03:00 ET drift -0.66 bps (t -2.7, same sign 4/4 yrs, 1.62x cost; selection-span t -2.4, late-span mean -0.61) | drift rule: short at 02:45 open, flat at 03:00 |
| 4 | DRIFT | 11:00-11:15 ET drift +1.49 bps (t +2.1, same sign 3/4 yrs, 3.65x cost; selection-span t +2.4, late-span mean -0.81) | drift rule: long at 11:00 open, flat at 11:15 |
| 5 | RANGE | 10:30-10:45 ET range x2.67 of median (min-year x2.35) | range-expansion rule: break of the prior 15-min range (10:15-10:30) with a bracket at 1x/1.5x the median window range (13 bps ~ 87 ticks), flat at 10:45 |
| 6 | RANGE | 08:30-08:45 ET range x2.50 of median (min-year x1.88) | range-expansion rule: break of the prior 15-min range (08:15-08:30) with a bracket at 1x/1.5x the median window range (13 bps ~ 87 ticks), flat at 08:45 |
| 7 | RANGE | 11:00-11:15 ET range x2.36 of median (min-year x2.15) | range-expansion rule: break of the prior 15-min range (10:45-11:00) with a bracket at 1x/1.5x the median window range (13 bps ~ 87 ticks), flat at 11:15 |

## Disclosures
1. **Selection overlaps HOLD.** The maps use 2022-06-01..2026-02-06, which includes 2025-07-01..2026-02-06 of the DS3 HOLD span (and 2022-06..2024-01 in X). The windows listed under 'worth a rule' were chosen with that partial look; section-2 agents should treat the HOLD for these windows as no longer clean, use the sel-span t and late-mean columns as the honest cut (sel-span = 2022-06..2025-06, late = 2025-07..2026-02-06), and the data after 2026-02-06 (UNTOUCHED, not read here) as the only unseen history. The by-year table is the program's required consistency check, not an OOS test.
2. **No calendar.** Release days, CL inventory holiday shifts, Treasury auction days, LBMA holidays and early-close days are not separated (see Method). Early-close days enter with the window data they have; events missing the prints at the event time or the pre-window are dropped (ES 15:50/16:00 n = 916 of 952, GC 13:30 941).
3. **Back-adjusted series.** Windows that contain a roll bar use the additive-adjusted differences (roll gap removed); the roll gap itself is not in any return. The adjusted price level is not used for bps.
4. **Reopen window.** The 18:00-18:15 slot opens at the first print after the daily halt; its drift (CL -3.8 bps, t -3.7, ES -0.5) is a first-print artifact, not a tradable entry; excluded from rule lists.
5. **Rule selection is mechanical** (stated under each table) and ranks by |t| or event strength; it is in-sample and descriptive, a to-do list for the per-market agents rather than evidence.
6. **No scored cells** and nothing here is a verdict; ledger unchanged.
