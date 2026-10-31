# DS3_INTRADAY_MAP - T-QUIT-WHEN-UP section A: when the stack makes money and when it gives it back (agent QW-2, 2026-10-31)

Research only; no live / execution / chart change; UNTOUCHED never read (everything capped at label day 20260206). Prereg `autopilot/QUITWHENUP_A_prereg.md` sha256 784c99ea453c1b1f0f907caf339fad6ca9b054ab7de534259471810327b55142 (logged in DECISIONS.md before any section-A output). Code `l2vast/ds3/code/quitwhenup/` (qw_cap.py, qw_core.py, qw_dayfeat.py, qw_A_stats.py, qw_A_doc.py); outputs `l2vast/ds3/out/quitwhenup/` (A_stats.pkl, secA_paths.pkl, A_grid_*.csv: the full 5-minute grids).

## 0. Page 1 - what the map says (D6 composite at live lots, recent first; R = K6 BookR = 2 lots x 60 pts x $20 = $2,400)

**Reading.** The stack's afternoon is negative after a good morning in the last six months, and not in the 2023-2025 sample (the sign changes by quarter). The give-back (peak minus close) is large in dollars, but about 93-95% of it is what a day with the same 5-minute increments in random order would show; the excess is small (7-8%) though it exceeds every one of 300 shuffles in PRE+X and over all days. The plain lines:

1. **"On days when the stack is up >= 2R ($4.8k) by noon (12:00 ET), the afternoon (12:00 -> 17:00) averages -1.4k (median -1.3k) and is negative 55% of the time (last 6 months, 69 days)"**; for all days the afternoon averages +0.4k and is negative 50%. In PRE+X (2023-04 .. 2025-06, 557 days) the same statement reads: averages +0.1k (median -0.0k), negative 47% (239 days; all days -0.1k / 48%). The sign flips between windows: the last-6-months effect is not present in the longer history.
2. **"After a +3R morning (up >= $7.2k by 12:00) the afternoon's expectation is -1.2k (median -1.2k, negative 53%, 64 days, last 6 months); PRE+X +0.1k (median -0.0k, negative 46%, 216 days)."**
3. **"Friday afternoons (12:00 -> 17:00) average +0.5k in the last 6 months (27 Fridays) and +0.1k in PRE+X (112 Fridays)"**; on Fridays up >= 2R by noon: -3.4k (n=14, last 6 months) and +1.2k (n=50, PRE+X). Mid-week is the weak afternoon in the longer history (Wednesday PRE+X -2.3k, Thursday L6M -1.5k), Friday is not special. The user's example (last trade 12:30 ET, a Friday, up $19k) is a +8R day: see section 5.
4. **"The hour that gives back most"** (mean P&L change over the hour, over days that are up >= 2R at its start, n >= 20 days): last 6 months 12:00-13:00 (-0.8k, n=69; the unconditional mean of that hour is -0.0k); PRE+X 06:00-07:00 (-1.1k, n=174; unconditional -0.5k). By the hour of the day's PEAK: days whose peak falls in 09:30-12:00 give back 16.2k (L6M) / 17.4k (PRE+X) from peak to close, 12:00-14:00 11.3k / 8.2k, 14:00-17:00 1.6k / 1.9k (little time left), Asia/overnight peaks 29.7k / 25.9k (the day then closes -13.6k / -13.4k on average: an early peak is a losing day).
5. **Give-back size.** The stack's day peak (realised + open, 1-second path, floored at 0) averages 28.1k (L6M) against a mean close of +8.9k: give-back mean 19.1k, median 16.0k, 80th percentile 31.8k, positive on 94% of days. PRE+X: 22.4k / +4.0k / 18.4k / 14.8k / 32.9k. That is large because the book swings +-$20k intraday on ~25 lots, not because it reverses: against a placebo that keeps each day's 5-minute P&L increments but shuffles their time order (300 draws), the mean grid give-back is 17.8k observed vs 16.9k placebo in L6M (placebo share of draws >= observed = 0.143), 17.1k vs 15.9k in PRE+X (p = 0.000), 17.2k vs 16.1k all 707 days (p = 0.000). So there is a small real excess of give-back over a random walk with the same increments (+8% PRE+X, +7% all), not the "uncanny" pattern at stack scale.
6. **What is new (drift).** The afternoon after an up-2R noon (T = 12:00) is negative in 8 of 12 quarters (negative: 2023Q2, 2023Q3, 2023Q4, 2024Q1, 2024Q4, 2025Q1, 2025Q4, 2026Q1; positive: 2024Q2, 2024Q3, 2025Q2, 2025Q3): the sign changes with the quarter and no quarter-sign rule is stable. The mean day peak rose from 17.3k (2023Q2-Q4 average) to 28.3k (2025Q2-2026Q1 average) as lots and trade counts rose, and the give-back / peak ratio fell from 93% to 73%.
7. **Consequence for section B.** The cheap quit rules key on "up X by T" and stop the afternoon; the afternoon here has small mean P&L at live lots (only K6 and A6 trade NY-PM; P6, U6, H6, M6 are Asia / London / NY-AM only), so a quit at 12:00 is expected to forgo little and avoid little at the stack level (to be measured in section B, not assumed); most of the give-back happens in the overnight and morning sessions and inside open trades, which a quit at 12:00 cannot reach. Section B scores that exactly.

## 1. Definitions, engine, tie-out

Engine: `ss2_lib` lock engine (day entry test +5R / -2R realised, day give-back arm 2R keep 50% with the causal running-max SizeMult, week floor 12R; busy filter, re-entries and blocked entries real), via `sundaydecision/sdlib` (A6 = PB7). **Base 1 = D6 composite**: live lots K6 2 (Asia/London/NY-AM/NY-PM), P6 7 (Asia/London/NY-AM), U6 4 (Asia/London), H6 4 Asia / 2 NY-AM, M6 2 (London/NY-AM), A6 = PB7 1 (Asia); integer half-up min-1 ER lots; 70/30 add (add slippage 0.25) with A6 at market; PE 45-s confirmation; first-stop cut; zone skip; Native stop 1.28; basis N. Tie-out: 43,493 $/wk L6M (= D1's composite: +21.8k over the as-is stack). **Base 2 = the stack as it is** (market entries, no rules, join stop 2.45, same live lots): L6M 21,715 $/wk. Sum of the stack's day-close path equals the engine daily P&L to 1e-8 on all days.
P&L at time t = realised (net of 0.5 pt slip and commission) + open mark-to-market of every open child trade (no cost on the open part), at the first printed second at/after t; the day is the 18:00 ET rollover session labelled by its trading date; "afternoon" = P&L(17:00) - P&L(T). The 5-minute grid is 18:00, 18:05 ... 16:55 and the 17:00 close (277 points); 2023-04-03 .. 2026-02-06, 707 valid days (holidays/short days with no printed seconds are dropped; no-trade days are zero days and kept). Windows overlap (Y26 within L3M within L6M within HOLD).

## 2. The time-of-day curves (mean, median, 20th and 80th percentile of the cumulative day P&L)

Full 5-minute grids: `out/quitwhenup/A_grid_<stat>_<base>_<window>.csv`; charts: `out/quitwhenup/A_chart_*.png`. The tables show key times only. Recent first.

### D6 composite - MEAN path ($ cumulative from 18:00 ET)

| window | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y26 (25 d) | +0.0k | +0.9k | +3.9k | +5.7k | +5.6k | +5.9k | +5.7k | +6.2k | +6.1k | +8.1k | +7.7k | +7.3k | +7.5k |
| L3M (61 d) | +0.0k | +1.8k | +3.8k | +4.2k | +4.4k | +4.2k | +4.3k | +4.6k | +5.2k | +8.4k | +8.1k | +7.7k | +7.7k |
| L6M (129 d) | +0.0k | +1.8k | +2.8k | +3.8k | +4.9k | +4.8k | +5.3k | +5.3k | +6.2k | +8.5k | +8.6k | +8.8k | +8.9k |
| HOLD (150 d) | +0.0k | +1.5k | +2.0k | +3.2k | +4.3k | +4.3k | +4.5k | +4.7k | +5.5k | +7.4k | +7.7k | +7.7k | +7.9k |
| PRE (350 d) | +0.0k | +1.5k | +2.2k | +2.9k | +3.3k | +2.2k | +2.3k | +2.5k | +4.2k | +4.8k | +5.2k | +5.2k | +5.2k |
| X' (207 d) | +0.0k | -0.0k | +0.4k | +0.9k | +0.6k | +0.4k | +2.2k | +1.9k | +2.5k | +2.9k | +2.1k | +1.9k | +2.0k |
| ALL (707 d) | +0.0k | +1.0k | +1.6k | +2.4k | +2.7k | +2.1k | +2.8k | +2.8k | +4.0k | +4.8k | +4.8k | +4.8k | +4.8k |

### D6 composite - MEDIAN path ($ cumulative from 18:00 ET)

| window | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y26 (25 d) | +0.0k | -2.6k | -0.8k | +0.7k | +6.8k | +5.3k | +2.4k | +3.6k | +3.6k | +12.0k | +8.0k | +6.6k | +6.6k |
| L3M (61 d) | +0.0k | -0.7k | -0.5k | +1.8k | +0.8k | +4.7k | +2.2k | +3.6k | +4.8k | +8.3k | +10.9k | +10.9k | +10.9k |
| L6M (129 d) | +0.0k | +0.1k | +0.4k | +1.6k | +3.3k | +4.7k | +2.3k | +4.4k | +3.2k | +7.1k | +9.7k | +11.4k | +10.9k |
| HOLD (150 d) | +0.0k | +0.0k | -0.0k | +1.3k | +2.0k | +3.1k | +2.0k | +4.1k | +3.1k | +6.7k | +8.5k | +6.8k | +7.8k |
| PRE (350 d) | +0.0k | +0.0k | +0.1k | +0.3k | +0.6k | +0.3k | +0.1k | +0.2k | +0.8k | +0.6k | +0.7k | +0.8k | +0.3k |
| X' (207 d) | +0.0k | +0.0k | +0.0k | +0.0k | -0.2k | -0.2k | +0.0k | +0.0k | +2.3k | +1.8k | +1.5k | +2.1k | +2.3k |
| ALL (707 d) | +0.0k | +0.0k | +0.0k | +0.1k | +0.2k | +0.0k | +0.3k | +0.6k | +2.0k | +2.0k | +2.2k | +2.3k | +2.4k |

### D6 composite - 20th percentile path ($ cumulative from 18:00 ET)

| window | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y26 (25 d) | +0.0k | -8.7k | -8.9k | -7.8k | -17.4k | -19.2k | -18.8k | -17.9k | -18.7k | -23.5k | -20.3k | -21.4k | -21.4k |
| L3M (61 d) | +0.0k | -6.7k | -9.4k | -11.7k | -17.7k | -17.9k | -26.4k | -23.7k | -20.8k | -19.5k | -19.0k | -21.0k | -21.0k |
| L6M (129 d) | +0.0k | -5.1k | -7.6k | -7.7k | -12.5k | -12.7k | -15.4k | -16.3k | -13.0k | -13.7k | -15.1k | -15.2k | -15.3k |
| HOLD (150 d) | +0.0k | -5.0k | -8.4k | -8.2k | -12.8k | -12.6k | -15.2k | -16.3k | -12.9k | -13.5k | -13.5k | -15.2k | -15.3k |
| PRE (350 d) | +0.0k | -3.2k | -4.2k | -5.6k | -7.8k | -9.9k | -12.9k | -13.2k | -15.0k | -17.2k | -18.1k | -18.9k | -19.1k |
| X' (207 d) | +0.0k | -1.7k | -2.6k | -3.5k | -5.0k | -5.6k | -6.1k | -6.6k | -8.6k | -9.8k | -12.7k | -13.9k | -13.7k |
| ALL (707 d) | +0.0k | -2.8k | -4.1k | -5.5k | -7.2k | -9.0k | -11.2k | -11.9k | -12.9k | -14.2k | -15.4k | -16.3k | -16.0k |

### D6 composite - 80th percentile path ($ cumulative from 18:00 ET)

| window | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y26 (25 d) | +0.0k | +7.3k | +13.6k | +16.1k | +25.4k | +29.7k | +31.1k | +30.9k | +29.7k | +35.3k | +32.2k | +32.2k | +32.2k |
| L3M (61 d) | +0.0k | +7.8k | +13.2k | +16.3k | +24.3k | +29.1k | +31.7k | +29.5k | +29.0k | +36.3k | +31.5k | +31.5k | +31.5k |
| L6M (129 d) | +0.0k | +7.1k | +10.7k | +15.1k | +19.9k | +23.1k | +26.4k | +27.1k | +27.9k | +32.1k | +30.7k | +31.1k | +31.1k |
| HOLD (150 d) | +0.0k | +6.7k | +9.3k | +13.8k | +19.6k | +21.6k | +24.6k | +24.6k | +27.3k | +31.3k | +30.4k | +30.6k | +30.6k |
| PRE (350 d) | +0.0k | +5.8k | +7.5k | +10.3k | +15.3k | +14.1k | +17.6k | +18.6k | +21.8k | +27.0k | +28.6k | +28.9k | +28.7k |
| X' (207 d) | +0.0k | +1.3k | +2.6k | +4.6k | +5.5k | +6.5k | +12.7k | +12.1k | +15.0k | +17.2k | +16.3k | +17.2k | +17.2k |
| ALL (707 d) | +0.0k | +4.3k | +6.1k | +9.2k | +13.8k | +12.3k | +17.4k | +18.2k | +20.9k | +24.1k | +25.3k | +25.5k | +25.7k |

### Stack as it is - MEAN path and MEDIAN path

| window | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y26 (25 d) | +0.0k | -0.6k | +0.4k | +2.8k | +1.0k | +1.5k | +0.2k | +1.5k | +1.9k | +2.2k | +1.8k | +1.7k | +2.0k |
| L3M (61 d) | +0.0k | +0.1k | -0.4k | +0.6k | +1.0k | +1.0k | +1.5k | +1.9k | +2.9k | +2.7k | +2.6k | +2.4k | +2.4k |
| L6M (129 d) | +0.0k | +0.9k | +0.5k | +1.3k | +2.6k | +2.5k | +2.8k | +3.2k | +4.1k | +4.0k | +4.4k | +4.6k | +4.7k |
| HOLD (150 d) | +0.0k | +0.6k | -0.2k | +0.7k | +1.9k | +1.9k | +1.9k | +2.6k | +3.6k | +3.7k | +4.1k | +4.3k | +4.3k |
| PRE (350 d) | +0.0k | +1.1k | +1.6k | +2.0k | +2.3k | +1.6k | +1.7k | +1.7k | +3.3k | +3.2k | +3.8k | +3.9k | +3.8k |
| X' (207 d) | +0.0k | -0.5k | -0.5k | -0.1k | -0.9k | -1.3k | -0.0k | -0.2k | -0.3k | -0.1k | -0.8k | -0.5k | -0.5k |
| ALL (707 d) | +0.0k | +0.5k | +0.6k | +1.1k | +1.3k | +0.8k | +1.2k | +1.3k | +2.3k | +2.3k | +2.5k | +2.7k | +2.6k |

| window | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y26 (25 d) | +0.0k | -4.1k | -1.5k | +5.6k | +2.6k | +1.0k | -6.0k | -6.0k | +0.8k | +1.7k | +2.1k | -0.5k | -0.5k |
| L3M (61 d) | +0.0k | -2.2k | -2.2k | -1.8k | -1.0k | -3.0k | -1.5k | -1.5k | +0.8k | +4.8k | +2.3k | +2.3k | +2.3k |
| L6M (129 d) | +0.0k | -1.2k | -1.2k | -1.0k | -0.8k | -1.0k | +1.2k | +2.8k | +5.3k | +6.2k | +5.9k | +5.9k | +5.9k |
| HOLD (150 d) | +0.0k | -0.9k | -1.5k | -0.8k | +0.0k | -1.0k | +1.2k | +2.3k | +5.2k | +4.6k | +5.9k | +5.9k | +5.9k |
| PRE (350 d) | +0.0k | -0.6k | -0.2k | +0.4k | +0.6k | -0.1k | +0.7k | +1.0k | +1.7k | +1.8k | +1.4k | +1.8k | +1.6k |
| X' (207 d) | +0.0k | -0.8k | -0.8k | -0.7k | -1.8k | -1.6k | -0.9k | -0.9k | -0.1k | -0.3k | -1.5k | -1.0k | -1.2k |
| ALL (707 d) | +0.0k | -0.7k | -0.6k | -0.3k | -0.4k | -0.9k | -0.1k | +0.2k | +0.8k | +1.8k | +1.1k | +1.3k | +1.1k |

### By day of week (D6 composite, mean path)

**L6M**

| day | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Mon (25 d) | +0.0k | +3.5k | +7.2k | +8.4k | +11.5k | +12.2k | +15.0k | +15.3k | +19.4k | +18.9k | +19.3k | +18.6k | +19.0k |
| Tue (27 d) | +0.0k | +0.3k | +2.2k | +3.5k | +5.3k | +6.2k | +6.9k | +6.8k | +7.1k | +7.2k | +8.5k | +9.2k | +9.2k |
| Wed (26 d) | +0.0k | +3.2k | +1.3k | +6.2k | +4.6k | +4.1k | +1.6k | +1.8k | +0.4k | +6.2k | +5.7k | +6.8k | +7.0k |
| Thu (24 d) | +0.0k | +2.1k | +3.9k | -0.2k | +0.3k | -0.7k | +1.0k | +0.4k | -0.7k | +1.8k | +0.7k | +0.4k | +0.4k |
| Fri (27 d) | +0.0k | +0.2k | -0.2k | +1.3k | +2.7k | +2.3k | +2.1k | +2.4k | +4.8k | +8.2k | +8.6k | +8.5k | +8.7k |

**PRE+X**

| day | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Mon (105 d) | +0.0k | +1.5k | +2.8k | +3.8k | +3.5k | +2.6k | +3.6k | +3.6k | +5.0k | +3.6k | +4.3k | +4.4k | +4.3k |
| Tue (115 d) | +0.0k | -0.4k | +0.9k | +1.3k | +0.8k | -0.5k | +0.2k | -0.3k | +2.3k | +3.5k | +4.0k | +4.2k | +4.2k |
| Wed (113 d) | +0.0k | -0.1k | -0.2k | +1.5k | +1.8k | +0.4k | +1.9k | +2.3k | +3.3k | +4.8k | +3.1k | +2.5k | +2.5k |
| Thu (112 d) | +0.0k | +1.4k | +3.1k | +3.4k | +3.6k | +3.0k | +3.4k | +3.5k | +3.9k | +4.8k | +4.8k | +5.0k | +5.0k |
| Fri (112 d) | +0.0k | +2.2k | +1.0k | +0.9k | +2.1k | +2.3k | +2.5k | +2.4k | +3.5k | +3.8k | +4.1k | +3.9k | +3.9k |

### By day type (D6 composite, mean path; terciles cut on PRE+X days only; same-day descriptive tags, NOT known at the time)

**L6M**

| type | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| vol low (46 d) | +0.0k | +1.3k | +0.3k | +0.2k | -0.6k | -1.1k | +0.1k | +0.3k | -0.5k | +0.7k | +0.1k | +0.6k | +0.8k |
| vol mid (40 d) | +0.0k | +3.8k | +5.0k | +7.4k | +9.4k | +8.9k | +8.3k | +8.2k | +8.3k | +9.9k | +10.6k | +10.9k | +11.0k |
| vol high (43 d) | +0.0k | +0.5k | +3.4k | +4.4k | +6.7k | +7.4k | +8.0k | +8.1k | +11.5k | +15.6k | +15.8k | +15.5k | +15.6k |
| chop (RTH ER) (38 d) | +0.0k | +1.4k | +2.6k | +4.0k | +4.0k | +5.0k | +6.4k | +6.0k | +4.6k | +5.0k | +2.1k | +1.8k | +1.8k |
| mid (RTH ER) (43 d) | +0.0k | +2.9k | +2.6k | +5.7k | +7.3k | +6.9k | +7.8k | +8.3k | +8.2k | +9.9k | +9.8k | +9.5k | +9.6k |
| trend (RTH ER) (48 d) | +0.0k | +1.2k | +3.1k | +2.1k | +3.5k | +2.9k | +2.1k | +2.1k | +5.7k | +10.0k | +12.7k | +13.7k | +13.9k |

**PRE+X**

| type | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| vol low (186 d) | +0.0k | +0.3k | +0.5k | +1.3k | +0.9k | +0.0k | -0.8k | -1.2k | -2.4k | -4.6k | -5.6k | -5.9k | -6.0k |
| vol mid (185 d) | +0.0k | +0.1k | +0.4k | +0.0k | +0.0k | -0.7k | +0.2k | +0.3k | +1.8k | +0.6k | -0.2k | -0.6k | -0.6k |
| vol high (186 d) | +0.0k | +2.4k | +3.5k | +5.1k | +6.0k | +5.3k | +7.5k | +7.7k | +11.3k | +16.2k | +18.0k | +18.5k | +18.6k |
| chop (RTH ER) (186 d) | +0.0k | +0.3k | +0.9k | +1.3k | +1.3k | +0.3k | +0.5k | +0.2k | +0.8k | -1.9k | -3.6k | -4.2k | -4.2k |
| mid (RTH ER) (185 d) | +0.0k | +1.8k | +2.1k | +3.4k | +3.4k | +2.6k | +3.4k | +3.2k | +3.4k | +2.8k | +2.1k | +1.7k | +1.7k |
| trend (RTH ER) (186 d) | +0.0k | +0.6k | +1.6k | +1.8k | +2.3k | +1.7k | +3.0k | +3.4k | +6.5k | +11.4k | +13.7k | +14.5k | +14.5k |

### Day type: give-back and the afternoon after an up-2R noon (D6 composite)

**L6M**

| tag | tercile | days | mean close | give-back mean | median | afternoon all days: mean / %neg | afternoon | up>=2R @12:00: n: mean / median / %neg |
|---|---|---|---|---|---|---|---|
| vol tercile (day range) | low | 46 | +0.8k | 16.7k | 12.9k | +0.1k / 57% | n=19: -1.7k / -1.8k / 63% |
| vol tercile (day range) | mid | 40 | +11.0k | 19.5k | 18.6k | +1.1k / 45% | n=27: -0.7k / +0.0k / 48% |
| vol tercile (day range) | high | 43 | +15.6k | 21.4k | 18.9k | +0.1k / 49% | n=23: -1.8k / -1.2k / 57% |
| RTH efficiency ratio (chop -> trend) | chop | 38 | +1.8k | 23.3k | 20.3k | -3.2k / 71% | n=19: -5.2k / -4.5k / 79% |
| RTH efficiency ratio (chop -> trend) | mid | 43 | +9.6k | 19.6k | 15.6k | -0.3k / 56% | n=25: -1.7k / -1.7k / 64% |
| RTH efficiency ratio (chop -> trend) | trend | 48 | +13.9k | 15.5k | 10.6k | +3.9k / 29% | n=25: +1.9k / +1.8k / 28% |

**PRE+X**

| tag | tercile | days | mean close | give-back mean | median | afternoon all days: mean / %neg | afternoon | up>=2R @12:00: n: mean / median / %neg |
|---|---|---|---|---|---|---|---|
| vol tercile (day range) | low | 186 | -6.0k | 19.1k | 15.8k | -1.5k / 59% | n=46: -2.8k / -1.2k / 72% |
| vol tercile (day range) | mid | 185 | -0.6k | 21.4k | 17.8k | -1.2k / 52% | n=76: -1.9k / -0.9k / 54% |
| vol tercile (day range) | high | 186 | +18.6k | 14.6k | 9.8k | +2.4k / 32% | n=117: +2.5k / +1.2k / 32% |
| RTH efficiency ratio (chop -> trend) | chop | 186 | -4.2k | 22.3k | 19.0k | -2.3k / 61% | n=60: -3.2k / -1.1k / 63% |
| RTH efficiency ratio (chop -> trend) | mid | 185 | +1.7k | 20.3k | 16.5k | -1.1k / 53% | n=79: -2.1k / -1.1k / 59% |
| RTH efficiency ratio (chop -> trend) | trend | 186 | +14.5k | 12.5k | 6.4k | +3.1k / 29% | n=100: +3.8k / +2.6k / 27% |

### Where the money is made: mean P&L change per ET hour (D6 composite; hour starts at the time shown)

| hour | L6M all days | L6M | up>=2R at start | PRE+X all | PRE+X | up>=2R | ALL all | ALL | up>=2R |
|---|---|---|---|---|---|---|
| 18:00 | +0.0k | n<3 | +0.5k | n<3 | +0.4k | n<3 |
| 19:00 | +1.0k | +3.6k (n=11) | +0.6k | +0.4k (n=39) | +0.6k | +0.7k (n=52) |
| 20:00 | +0.8k | +2.0k (n=26) | -0.2k | -0.8k (n=86) | -0.0k | -0.0k (n=114) |
| 21:00 | +0.4k | +2.2k (n=34) | +0.3k | +0.7k (n=98) | +0.3k | +0.9k (n=136) |
| 22:00 | +0.3k | +0.5k (n=39) | +0.1k | +0.1k (n=107) | +0.2k | +0.2k (n=148) |
| 23:00 | +0.2k | +0.2k (n=41) | +0.1k | -0.0k (n=122) | +0.1k | +0.1k (n=165) |
| 00:00 | +0.4k | +0.7k (n=44) | +0.3k | +0.1k (n=120) | +0.3k | +0.3k (n=167) |
| 01:00 | +0.3k | +0.4k (n=39) | +0.3k | +0.4k (n=132) | +0.3k | +0.4k (n=174) |
| 02:00 | +0.3k | -0.1k (n=46) | +0.1k | +0.2k (n=146) | +0.2k | +0.1k (n=196) |
| 03:00 | +0.9k | +1.3k (n=50) | +0.1k | +0.0k (n=149) | +0.3k | +0.5k (n=204) |
| 04:00 | +0.2k | +1.7k (n=55) | +0.1k | -0.3k (n=149) | +0.1k | +0.2k (n=212) |
| 05:00 | -0.1k | -0.2k (n=60) | -0.2k | -0.8k (n=170) | -0.2k | -0.6k (n=238) |
| 06:00 | +0.0k | +0.6k (n=67) | -0.5k | -1.1k (n=174) | -0.4k | -0.6k (n=249) |
| 07:00 | +0.8k | +0.3k (n=64) | +0.5k | +1.0k (n=170) | +0.5k | +0.8k (n=242) |
| 08:00 | -0.3k | +1.1k (n=63) | +0.3k | -0.4k (n=178) | +0.1k | -0.1k (n=248) |
| 09:00 | +1.0k | -0.0k (n=59) | +0.7k | +0.7k (n=199) | +0.7k | +0.7k (n=267) |
| 10:00 | +0.8k | +0.4k (n=63) | +0.7k | +0.7k (n=234) | +0.7k | +0.7k (n=308) |
| 11:00 | +1.5k | +1.0k (n=67) | +0.5k | +0.5k (n=238) | +0.6k | +0.6k (n=315) |
| 12:00 | -0.0k | -0.8k (n=69) | +0.1k | +0.2k (n=239) | +0.2k | +0.1k (n=316) |
| 13:00 | +0.1k | -0.6k (n=71) | -0.2k | -0.2k (n=240) | -0.1k | -0.3k (n=320) |
| 14:00 | +0.2k | +0.2k (n=73) | +0.0k | +0.3k (n=235) | +0.0k | +0.2k (n=317) |
| 15:00 | -0.0k | +0.2k (n=72) | -0.1k | +0.0k (n=238) | -0.1k | +0.0k (n=319) |
| 16:00 | +0.1k | +0.1k (n=71) | +0.0k | -0.1k (n=243) | +0.0k | -0.0k (n=322) |

## 3. The give-back statistic (peak, time of peak, give-back = peak - close) - D6 composite

### By window

| cell | days | mean close | mean peak | give-back mean | median | 80th pct | give-back>0 |
|---|---|---|---|---|---|---|---|
| Y26 | 25 | +7.5k | 29.6k | 22.1k | 16.0k | 33.6k | 96% |
| L3M | 61 | +7.7k | 30.9k | 23.2k | 19.8k | 37.6k | 98% |
| L6M | 129 | +8.9k | 28.1k | 19.1k | 16.0k | 31.8k | 94% |
| HOLD | 150 | +7.9k | 26.5k | 18.7k | 14.2k | 31.4k | 94% |
| PRE | 350 | +5.2k | 24.9k | 19.7k | 15.3k | 35.3k | 95% |
| X' | 207 | +2.0k | 18.0k | 16.0k | 13.2k | 28.5k | 95% |
| ALL | 707 | +4.8k | 23.2k | 18.4k | 14.7k | 32.5k | 95% |
| PRE+X | 557 | +4.0k | 22.4k | 18.4k | 14.8k | 32.9k | 95% |

### By day of week

| cell | days | mean close | mean peak | give-back mean | median | 80th pct | give-back>0 |
|---|---|---|---|---|---|---|---|
| L6M Mon | 25 | +19.0k | 34.0k | 15.0k | 12.4k | 25.2k | 92% |
| L6M Tue | 27 | +9.2k | 27.7k | 18.6k | 10.4k | 35.1k | 96% |
| L6M Wed | 26 | +7.0k | 25.6k | 18.7k | 13.5k | 34.2k | 88% |
| L6M Thu | 24 | +0.4k | 24.8k | 24.5k | 21.9k | 34.7k | 96% |
| L6M Fri | 27 | +8.7k | 28.0k | 19.3k | 16.0k | 26.3k | 96% |
| PRE+X Mon | 105 | +4.3k | 22.8k | 18.5k | 15.2k | 34.1k | 95% |
| PRE+X Tue | 115 | +4.2k | 22.6k | 18.3k | 15.1k | 31.8k | 97% |
| PRE+X Wed | 113 | +2.5k | 20.9k | 18.4k | 14.2k | 32.5k | 92% |
| PRE+X Thu | 112 | +5.0k | 23.7k | 18.6k | 14.8k | 34.6k | 96% |
| PRE+X Fri | 112 | +3.9k | 21.8k | 17.9k | 14.3k | 30.0k | 95% |
| ALL Mon | 134 | +7.2k | 24.8k | 17.6k | 14.6k | 32.5k | 95% |
| ALL Tue | 147 | +5.4k | 23.5k | 18.1k | 14.5k | 31.7k | 96% |
| ALL Wed | 144 | +3.1k | 21.7k | 18.5k | 14.0k | 33.5k | 92% |
| ALL Thu | 140 | +4.0k | 23.7k | 19.7k | 16.3k | 34.8k | 96% |
| ALL Fri | 142 | +4.5k | 22.7k | 18.2k | 14.3k | 28.7k | 95% |

### By the time the peak occurred (ET block)

| cell | days | mean close | mean peak | give-back mean | median | 80th pct | give-back>0 |
|---|---|---|---|---|---|---|---|
| L6M 18-02 Asia | 31 | -13.6k | 16.2k | 29.7k | 24.7k | 45.4k | 100% |
| L6M 02-06 | 19 | +7.7k | 32.6k | 24.9k | 19.8k | 42.3k | 100% |
| L6M 06-09:30 | 24 | +5.6k | 26.7k | 21.1k | 19.5k | 31.6k | 100% |
| L6M 09:30-12 | 21 | +22.5k | 38.7k | 16.2k | 16.1k | 25.0k | 100% |
| L6M 12-14 | 18 | +22.9k | 34.2k | 11.3k | 6.0k | 21.6k | 89% |
| L6M 14-17 | 16 | +25.2k | 26.7k | 1.6k | 1.3k | 2.8k | 62% |
| PRE+X 18-02 Asia | 122 | -13.4k | 12.5k | 25.9k | 22.8k | 41.9k | 100% |
| PRE+X 02-06 | 88 | -8.4k | 18.9k | 27.4k | 25.7k | 39.7k | 100% |
| PRE+X 06-09:30 | 95 | +1.1k | 21.9k | 20.8k | 17.2k | 32.6k | 100% |
| PRE+X 09:30-12 | 115 | +7.6k | 25.1k | 17.4k | 15.1k | 26.9k | 100% |
| PRE+X 12-14 | 66 | +22.9k | 31.1k | 8.2k | 4.3k | 13.4k | 86% |
| PRE+X 14-17 | 70 | +30.1k | 32.0k | 1.9k | 1.1k | 2.8k | 74% |
| ALL 18-02 Asia | 161 | -14.0k | 12.9k | 26.8k | 23.0k | 42.3k | 100% |
| ALL 02-06 | 108 | -5.5k | 21.3k | 26.8k | 24.2k | 39.9k | 100% |
| ALL 06-09:30 | 120 | +2.0k | 22.7k | 20.7k | 17.9k | 32.0k | 100% |
| ALL 09:30-12 | 140 | +10.0k | 27.1k | 17.1k | 15.0k | 26.7k | 100% |
| ALL 12-14 | 89 | +22.9k | 31.5k | 8.6k | 5.0k | 15.8k | 87% |
| ALL 14-17 | 88 | +29.2k | 31.1k | 1.9k | 1.2k | 2.8k | 73% |

### By the size of the peak (K6 R = $2.4k)

| cell | days | mean close | mean peak | give-back mean | median | 80th pct | give-back>0 |
|---|---|---|---|---|---|---|---|
| L6M 0-1R | 9 | -16.2k | 0.9k | 17.1k | 21.2k | 23.2k | 100% |
| L6M 1-2R | 4 | -28.0k | 3.7k | 31.7k | 23.4k | 45.6k | 100% |
| L6M 2-4R | 16 | -17.6k | 7.2k | 24.8k | 17.4k | 46.5k | 100% |
| L6M 4-8R | 30 | -6.9k | 14.2k | 21.1k | 17.5k | 31.8k | 93% |
| L6M 8-99R | 70 | +27.1k | 43.6k | 16.5k | 15.0k | 30.3k | 91% |
| PRE+X 0-1R | 40 | -14.5k | 1.1k | 15.7k | 10.8k | 29.1k | 98% |
| PRE+X 1-2R | 50 | -14.3k | 3.6k | 18.0k | 13.8k | 32.0k | 98% |
| PRE+X 2-4R | 72 | -13.3k | 7.1k | 20.4k | 15.5k | 34.2k | 96% |
| PRE+X 4-8R | 143 | -6.3k | 14.2k | 20.5k | 17.1k | 35.1k | 94% |
| PRE+X 8-99R | 252 | +21.4k | 38.4k | 17.1k | 14.0k | 28.6k | 94% |
| ALL 0-1R | 50 | -14.7k | 1.1k | 15.7k | 10.8k | 25.4k | 98% |
| ALL 1-2R | 59 | -14.8k | 3.7k | 18.5k | 13.7k | 33.2k | 98% |
| ALL 2-4R | 91 | -13.9k | 7.1k | 21.0k | 15.3k | 35.3k | 97% |
| ALL 4-8R | 178 | -6.9k | 14.2k | 21.1k | 17.2k | 34.8k | 94% |
| ALL 8-99R | 329 | +22.8k | 39.5k | 16.7k | 13.9k | 28.6k | 93% |

### Stack as it is - by window

| cell | days | mean close | mean peak | give-back mean | median | 80th pct | give-back>0 |
|---|---|---|---|---|---|---|---|
| Y26 | 25 | +2.0k | 21.7k | 19.8k | 17.1k | 31.5k | 88% |
| L3M | 61 | +2.4k | 24.0k | 21.6k | 18.7k | 32.5k | 92% |
| L6M | 129 | +4.7k | 23.6k | 19.0k | 17.4k | 31.0k | 91% |
| HOLD | 150 | +4.3k | 23.3k | 19.0k | 17.0k | 31.5k | 92% |
| PRE | 350 | +3.8k | 23.4k | 19.6k | 18.7k | 32.0k | 93% |
| X' | 207 | -0.5k | 15.5k | 16.0k | 16.2k | 25.2k | 92% |
| ALL | 707 | +2.6k | 21.0k | 18.4k | 17.4k | 29.7k | 93% |
| PRE+X | 557 | +2.2k | 20.4k | 18.2k | 17.4k | 29.4k | 93% |

## 4. P(the afternoon is negative | the day is up X R by T) - D6 composite (R = $2.4k; X = 1, 2, 3, 4; afternoon = P&L(17:00) - P&L(T), realised + open)

**Y26**

| T (ET) | all days: mean / median / %neg | up>=1R: n: mean / median / %neg | up>=2R: n: mean / median / %neg | up>=3R: n: mean / median / %neg | up>=4R: n: mean / median / %neg |
|---|---|---|---|---|---|
| 10:30 | +1.4k / +2.4k / 44% | n=13: +1.7k / +2.4k / 38% | n=12: +0.6k / +1.5k / 42% | n=12: +0.6k / +1.5k / 42% | n=10: +1.4k / +2.5k / 30% |
| 11:00 | +1.2k / +0.0k / 48% | n=13: -1.0k / -0.6k / 54% | n=13: -1.0k / -0.6k / 54% | n=13: -1.0k / -0.6k / 54% | n=13: -1.0k / -0.6k / 54% |
| 11:30 | +0.6k / +0.0k / 48% | n=15: -1.0k / -0.3k / 53% | n=15: -1.0k / -0.3k / 53% | n=15: -1.0k / -0.3k / 53% | n=14: -1.6k / -2.4k / 57% |
| 12:00 | -0.5k / -1.5k / 64% | n=15: -1.8k / -2.5k / 73% | n=15: -1.8k / -2.5k / 73% | n=14: -1.7k / -2.0k / 71% | n=13: -1.0k / -1.5k / 69% |
| 13:00 | +0.0k / +0.0k / 44% | n=15: -0.7k / -1.2k / 60% | n=15: -0.7k / -1.2k / 60% | n=13: -0.1k / -1.1k / 54% | n=13: -0.1k / -1.1k / 54% |
| 14:00 | -0.2k / +0.0k / 44% | n=15: +0.0k / +0.0k / 47% | n=15: +0.0k / +0.0k / 47% | n=14: +0.1k / +0.0k / 43% | n=12: +1.2k / +0.0k / 33% |

**L3M**

| T (ET) | all days: mean / median / %neg | up>=1R: n: mean / median / %neg | up>=2R: n: mean / median / %neg | up>=3R: n: mean / median / %neg | up>=4R: n: mean / median / %neg |
|---|---|---|---|---|---|
| 10:30 | +2.6k / +1.3k / 43% | n=32: +0.9k / +0.5k / 47% | n=30: +0.6k / +0.5k / 47% | n=30: +0.6k / +0.5k / 47% | n=27: +1.1k / +0.8k / 41% |
| 11:00 | +1.5k / -0.6k / 51% | n=33: -1.2k / -1.2k / 61% | n=32: -1.0k / -1.1k / 59% | n=31: -0.9k / -1.0k / 58% | n=30: -0.8k / -0.9k / 57% |
| 11:30 | +0.5k / -0.3k / 51% | n=34: -1.8k / -1.8k / 59% | n=33: -1.8k / -2.0k / 58% | n=33: -1.8k / -2.0k / 58% | n=32: -2.1k / -2.1k / 59% |
| 12:00 | -0.7k / -1.2k / 56% | n=35: -3.0k / -2.5k / 66% | n=32: -3.4k / -2.5k / 66% | n=31: -3.5k / -2.5k / 65% | n=30: -3.2k / -2.1k / 63% |
| 13:00 | -0.0k / +0.0k / 36% | n=36: -0.9k / +0.0k / 44% | n=34: -0.8k / +0.0k / 41% | n=32: -0.6k / +0.0k / 38% | n=31: -0.4k / +0.0k / 35% |
| 14:00 | -0.3k / +0.0k / 36% | n=37: -0.3k / +0.0k / 35% | n=35: -0.3k / +0.0k / 31% | n=33: -0.2k / +0.0k / 27% | n=31: +0.2k / +0.0k / 23% |

**L6M**

| T (ET) | all days: mean / median / %neg | up>=1R: n: mean / median / %neg | up>=2R: n: mean / median / %neg | up>=3R: n: mean / median / %neg | up>=4R: n: mean / median / %neg |
|---|---|---|---|---|---|
| 10:30 | +2.7k / +1.7k / 40% | n=68: +1.4k / +0.8k / 46% | n=60: +1.1k / +0.8k / 45% | n=56: +1.4k / +0.8k / 45% | n=53: +1.7k / +1.9k / 42% |
| 11:00 | +1.9k / +0.0k / 48% | n=71: +0.7k / -0.9k / 52% | n=67: +0.4k / -1.0k / 54% | n=61: +0.5k / -1.0k / 54% | n=59: +0.6k / -1.0k / 54% |
| 11:30 | +1.6k / +0.0k / 48% | n=73: +0.1k / -1.2k / 52% | n=70: -0.0k / -1.2k / 53% | n=63: -0.2k / -1.2k / 52% | n=59: +0.0k / -1.2k / 53% |
| 12:00 | +0.4k / -0.0k / 50% | n=76: -0.9k / -1.2k / 54% | n=69: -1.4k / -1.3k / 55% | n=64: -1.2k / -1.2k / 53% | n=60: -1.3k / -1.2k / 53% |
| 13:00 | +0.4k / +0.0k / 39% | n=77: -0.3k / +0.0k / 44% | n=71: -0.4k / +0.0k / 42% | n=66: -0.2k / +0.0k / 41% | n=64: -0.2k / +0.0k / 39% |
| 14:00 | +0.3k / +0.0k / 36% | n=78: +0.2k / +0.0k / 36% | n=73: +0.4k / +0.0k / 34% | n=70: +0.5k / +0.0k / 31% | n=65: +0.8k / +0.0k / 28% |

**HOLD**

| T (ET) | all days: mean / median / %neg | up>=1R: n: mean / median / %neg | up>=2R: n: mean / median / %neg | up>=3R: n: mean / median / %neg | up>=4R: n: mean / median / %neg |
|---|---|---|---|---|---|
| 10:30 | +2.3k / +1.5k / 41% | n=79: +1.5k / +0.8k / 46% | n=70: +1.4k / +1.4k / 44% | n=65: +1.8k / +1.9k / 43% | n=62: +2.1k / +2.5k / 40% |
| 11:00 | +1.5k / -0.0k / 49% | n=81: +0.8k / -0.9k / 52% | n=77: +0.5k / -1.0k / 53% | n=69: +1.1k / -0.9k / 52% | n=67: +1.1k / -0.9k / 52% |
| 11:30 | +1.4k / +0.0k / 47% | n=82: +0.2k / -1.2k / 52% | n=79: +0.1k / -1.2k / 53% | n=71: +0.2k / -1.2k / 52% | n=67: +0.4k / -1.2k / 52% |
| 12:00 | +0.4k / -0.0k / 49% | n=85: -0.7k / -1.3k / 54% | n=77: -0.9k / -1.3k / 55% | n=72: -0.8k / -1.2k / 53% | n=68: -0.8k / -1.2k / 53% |
| 13:00 | +0.2k / +0.0k / 39% | n=87: -0.5k / +0.0k / 45% | n=80: -0.6k / +0.0k / 42% | n=75: -0.5k / +0.0k / 41% | n=71: -0.1k / +0.0k / 39% |
| 14:00 | +0.1k / +0.0k / 35% | n=88: -0.0k / +0.0k / 35% | n=82: +0.1k / +0.0k / 34% | n=79: +0.3k / +0.0k / 32% | n=73: +0.5k / +0.0k / 29% |

**PRE**

| T (ET) | all days: mean / median / %neg | up>=1R: n: mean / median / %neg | up>=2R: n: mean / median / %neg | up>=3R: n: mean / median / %neg | up>=4R: n: mean / median / %neg |
|---|---|---|---|---|---|
| 10:30 | +1.0k / -0.0k / 50% | n=166: +2.1k / +0.1k / 48% | n=159: +2.0k / +0.0k / 48% | n=140: +2.0k / +0.0k / 48% | n=127: +1.5k / +0.0k / 47% |
| 11:00 | +1.1k / -0.0k / 50% | n=166: +1.7k / -0.0k / 48% | n=154: +2.1k / +0.3k / 47% | n=137: +2.7k / +1.2k / 45% | n=130: +2.0k / +0.4k / 46% |
| 11:30 | +0.8k / +0.0k / 48% | n=166: +1.2k / +0.0k / 46% | n=156: +1.7k / +0.2k / 44% | n=139: +1.8k / +0.4k / 43% | n=128: +1.8k / +0.4k / 42% |
| 12:00 | +0.4k / +0.0k / 43% | n=163: +1.0k / +0.0k / 40% | n=152: +1.1k / +0.0k / 39% | n=140: +1.2k / +0.0k / 38% | n=130: +1.1k / +0.0k / 36% |
| 13:00 | -0.1k / +0.0k / 39% | n=163: +0.1k / +0.0k / 39% | n=153: +0.2k / +0.0k / 37% | n=139: +0.1k / +0.0k / 37% | n=133: +0.1k / +0.0k / 38% |
| 14:00 | -0.0k / +0.0k / 32% | n=163: +0.3k / +0.0k / 30% | n=151: +0.2k / +0.0k / 30% | n=140: +0.3k / +0.0k / 31% | n=134: +0.2k / +0.0k / 31% |

**X'**

| T (ET) | all days: mean / median / %neg | up>=1R: n: mean / median / %neg | up>=2R: n: mean / median / %neg | up>=3R: n: mean / median / %neg | up>=4R: n: mean / median / %neg |
|---|---|---|---|---|---|
| 10:30 | -0.6k / -0.9k / 54% | n=102: -2.0k / -1.9k / 59% | n=82: -2.2k / -3.1k / 60% | n=74: -2.7k / -3.5k / 59% | n=63: -3.9k / -4.4k / 63% |
| 11:00 | -0.9k / -0.3k / 53% | n=102: -2.5k / -1.8k / 60% | n=84: -3.2k / -5.1k / 63% | n=74: -3.7k / -5.3k / 64% | n=65: -3.9k / -5.4k / 63% |
| 11:30 | -0.8k / -0.4k / 52% | n=95: -2.2k / -1.9k / 60% | n=86: -2.6k / -2.5k / 64% | n=73: -2.6k / -2.3k / 64% | n=69: -2.5k / -2.2k / 64% |
| 12:00 | -0.9k / -0.6k / 55% | n=99: -1.4k / -0.9k / 59% | n=87: -1.7k / -1.2k / 61% | n=76: -1.9k / -1.3k / 62% | n=70: -1.9k / -1.3k / 63% |
| 13:00 | -0.5k / -0.0k / 50% | n=91: -0.7k / -0.8k / 55% | n=87: -0.7k / -1.0k / 56% | n=76: -0.7k / -0.9k / 57% | n=69: -0.8k / -0.8k / 55% |
| 14:00 | -0.2k / +0.0k / 47% | n=96: +0.2k / +0.0k / 47% | n=84: +0.3k / +0.0k / 45% | n=75: +0.3k / +0.0k / 45% | n=68: +0.2k / +0.0k / 46% |

**PRE+X**

| T (ET) | all days: mean / median / %neg | up>=1R: n: mean / median / %neg | up>=2R: n: mean / median / %neg | up>=3R: n: mean / median / %neg | up>=4R: n: mean / median / %neg |
|---|---|---|---|---|---|
| 10:30 | +0.4k / -0.3k / 52% | n=268: +0.6k / -0.3k / 52% | n=241: +0.6k / -0.6k / 52% | n=214: +0.4k / -0.5k / 52% | n=190: -0.3k / -0.9k / 53% |
| 11:00 | +0.4k / -0.1k / 51% | n=268: +0.2k / -0.8k / 53% | n=238: +0.3k / -1.2k / 53% | n=211: +0.4k / -0.8k / 52% | n=195: +0.1k / -0.8k / 52% |
| 11:30 | +0.2k / -0.0k / 50% | n=261: -0.0k / -0.2k / 51% | n=242: +0.2k / -0.3k / 51% | n=212: +0.3k / -0.1k / 50% | n=197: +0.3k / -0.0k / 50% |
| 12:00 | -0.1k / -0.0k / 48% | n=262: +0.1k / -0.0k / 47% | n=239: +0.1k / -0.0k / 47% | n=216: +0.1k / -0.0k / 46% | n=200: +0.0k / +0.0k / 46% |
| 13:00 | -0.3k / +0.0k / 43% | n=254: -0.2k / -0.0k / 45% | n=240: -0.1k / -0.0k / 44% | n=215: -0.2k / -0.0k / 44% | n=202: -0.2k / -0.0k / 44% |
| 14:00 | -0.1k / +0.0k / 38% | n=259: +0.2k / +0.0k / 36% | n=235: +0.3k / +0.0k / 36% | n=215: +0.3k / +0.0k / 36% | n=202: +0.2k / +0.0k / 36% |

**ALL**

| T (ET) | all days: mean / median / %neg | up>=1R: n: mean / median / %neg | up>=2R: n: mean / median / %neg | up>=3R: n: mean / median / %neg | up>=4R: n: mean / median / %neg |
|---|---|---|---|---|---|
| 10:30 | +0.8k / +0.0k / 50% | n=347: +0.8k / -0.0k / 50% | n=311: +0.7k / -0.1k / 50% | n=279: +0.7k / -0.0k / 50% | n=252: +0.3k / -0.0k / 50% |
| 11:00 | +0.6k / -0.0k / 50% | n=349: +0.3k / -0.8k / 52% | n=315: +0.3k / -1.1k / 53% | n=280: +0.6k / -0.9k / 52% | n=262: +0.3k / -0.9k / 52% |
| 11:30 | +0.4k / -0.0k / 49% | n=343: +0.0k / -0.3k / 51% | n=321: +0.2k / -0.3k / 52% | n=283: +0.2k / -0.3k / 51% | n=264: +0.3k / -0.1k / 50% |
| 12:00 | +0.0k / -0.0k / 48% | n=347: -0.1k / -0.0k / 49% | n=316: -0.1k / -0.0k / 49% | n=288: -0.1k / -0.0k / 48% | n=268: -0.2k / -0.0k / 47% |
| 13:00 | -0.1k / +0.0k / 42% | n=341: -0.3k / -0.0k / 45% | n=320: -0.3k / -0.0k / 43% | n=290: -0.3k / -0.0k / 43% | n=273: -0.2k / +0.0k / 42% |
| 14:00 | -0.0k / +0.0k / 37% | n=347: +0.2k / +0.0k / 36% | n=317: +0.2k / +0.0k / 35% | n=294: +0.3k / +0.0k / 35% | n=275: +0.3k / +0.0k / 34% |

Extension to larger X (the stack carries ~25 lots, so 1-4 K6-R is a small number of dollars): L6M, T = 12:00:

| window | up >= X by 12:00 | days | afternoon mean | median | %negative | %positive |
|---|---|---|---|---|---|---|
| L6M | 1 R = $2.4k | 76 | -0.9k | -1.2k | 54% | 41% |
| L6M | 2 R = $4.8k | 69 | -1.4k | -1.3k | 55% | 39% |
| L6M | 3 R = $7.2k | 64 | -1.2k | -1.2k | 53% | 41% |
| L6M | 4 R = $9.6k | 60 | -1.3k | -1.2k | 53% | 40% |
| L6M | 6 R = $14.4k | 54 | -1.1k | -0.1k | 50% | 43% |
| L6M | 8 R = $19.2k | 48 | -1.2k | -0.0k | 48% | 44% |
| L6M | 12 R = $28.8k | 31 | -1.4k | -0.0k | 48% | 45% |
| PRE+X | 1 R = $2.4k | 262 | +0.1k | -0.0k | 47% | 45% |
| PRE+X | 2 R = $4.8k | 239 | +0.1k | -0.0k | 47% | 45% |
| PRE+X | 3 R = $7.2k | 216 | +0.1k | -0.0k | 46% | 45% |
| PRE+X | 4 R = $9.6k | 200 | +0.0k | +0.0k | 46% | 46% |
| PRE+X | 6 R = $14.4k | 162 | +0.4k | +0.0k | 43% | 48% |
| PRE+X | 8 R = $19.2k | 131 | +0.6k | +0.3k | 40% | 50% |
| PRE+X | 12 R = $28.8k | 82 | +0.3k | +1.0k | 39% | 52% |
| ALL | 1 R = $2.4k | 347 | -0.1k | -0.0k | 49% | 44% |
| ALL | 2 R = $4.8k | 316 | -0.1k | -0.0k | 49% | 44% |
| ALL | 3 R = $7.2k | 288 | -0.1k | -0.0k | 48% | 44% |
| ALL | 4 R = $9.6k | 268 | -0.2k | -0.0k | 47% | 44% |
| ALL | 6 R = $14.4k | 223 | +0.1k | +0.0k | 45% | 46% |
| ALL | 8 R = $19.2k | 185 | +0.2k | +0.0k | 43% | 49% |
| ALL | 12 R = $28.8k | 116 | +0.0k | +0.5k | 41% | 51% |

### After the N-th winning trade (stack-level: the afternoon = P&L(17:00) - P&L at the close of the N-th winning parent trade of the day)

| window | N-th winner | days with it / days | mean P&L at that moment | rest of day mean | median | %negative |
|---|---|---|---|---|---|---|
| Y26 | 1 | 25 / 25 | +1.9k | +5.6k | +9.1k | 48% |
| Y26 | 2 | 25 / 25 | +1.3k | +6.2k | +6.8k | 44% |
| Y26 | 3 | 25 / 25 | +2.9k | +4.6k | +5.6k | 40% |
| Y26 | 4 | 25 / 25 | +4.8k | +2.7k | +2.9k | 48% |
| Y26 | 5 | 25 / 25 | +7.4k | +0.1k | -2.5k | 56% |
| L6M | 1 | 128 / 129 | +1.3k | +7.7k | +6.0k | 39% |
| L6M | 2 | 124 / 129 | +2.0k | +7.9k | +5.5k | 40% |
| L6M | 3 | 123 / 129 | +4.0k | +6.2k | +1.7k | 43% |
| L6M | 4 | 119 / 129 | +6.9k | +4.4k | +0.0k | 46% |
| L6M | 5 | 108 / 129 | +10.7k | +3.5k | +1.6k | 43% |
| PRE+X | 1 | 544 / 557 | +2.3k | +2.1k | +0.0k | 48% |
| PRE+X | 2 | 515 / 557 | +4.0k | +1.8k | +0.0k | 48% |
| PRE+X | 3 | 486 / 557 | +5.1k | +2.1k | -0.0k | 50% |
| PRE+X | 4 | 437 / 557 | +7.1k | +2.0k | +0.0k | 46% |
| PRE+X | 5 | 376 / 557 | +9.1k | +2.1k | +0.0k | 45% |
| ALL | 1 | 693 / 707 | +2.1k | +3.1k | +1.0k | 46% |
| ALL | 2 | 658 / 707 | +3.6k | +3.0k | +0.2k | 47% |
| ALL | 3 | 625 / 707 | +4.9k | +2.9k | -0.0k | 48% |
| ALL | 4 | 570 / 707 | +7.1k | +2.5k | +0.0k | 46% |
| ALL | 5 | 494 / 707 | +9.5k | +2.4k | +0.0k | 44% |

## 5. The Friday afternoon and the user's example

| window | T (ET) | Fridays | n | afternoon mean | median | %negative |
|---|---|---|---|---|---|---|
| L6M | 12:00 | all Fridays | 27 | +0.5k | -0.0k | 52% |
| L6M | 12:00 | up >= 2R | 14 | -3.4k | -0.3k | 57% |
| L6M | 12:00 | up >= $15k | 11 | -3.6k | -0.0k | 45% |
| L6M | 12:00 | up >= $19k | 10 | -3.6k | +0.0k | 40% |
| L6M | 12:30 | all Fridays | 27 | +1.1k | +0.0k | 37% |
| L6M | 12:30 | up >= 2R | 14 | -1.6k | +0.0k | 43% |
| L6M | 12:30 | up >= $15k | 11 | -1.3k | +0.0k | 27% |
| L6M | 12:30 | up >= $19k | 9 | -1.2k | +0.0k | 22% |
| L6M | 14:00 | all Fridays | 27 | +0.1k | +0.0k | 30% |
| L6M | 14:00 | up >= 2R | 15 | -0.3k | +0.0k | 27% |
| L6M | 14:00 | up >= $15k | 10 | +0.1k | +0.0k | 10% |
| L6M | 14:00 | up >= $19k | 9 | +0.1k | +0.0k | 11% |
| PRE+X | 12:00 | all Fridays | 112 | +0.1k | -0.0k | 48% |
| PRE+X | 12:00 | up >= 2R | 50 | +1.2k | +0.2k | 40% |
| PRE+X | 12:00 | up >= $15k | 26 | +2.3k | +1.7k | 31% |
| PRE+X | 12:00 | up >= $19k | 22 | +1.3k | +1.3k | 32% |
| PRE+X | 12:30 | all Fridays | 112 | -0.6k | -0.0k | 48% |
| PRE+X | 12:30 | up >= 2R | 50 | -0.1k | -0.0k | 48% |
| PRE+X | 12:30 | up >= $15k | 25 | +1.1k | +0.0k | 36% |
| PRE+X | 12:30 | up >= $19k | 24 | +1.1k | +0.0k | 38% |
| PRE+X | 14:00 | all Fridays | 112 | -0.2k | +0.0k | 37% |
| PRE+X | 14:00 | up >= 2R | 43 | -0.0k | +0.0k | 30% |
| PRE+X | 14:00 | up >= $15k | 29 | +0.5k | +0.0k | 28% |
| PRE+X | 14:00 | up >= $19k | 24 | +0.3k | +0.0k | 25% |
| ALL | 12:00 | all Fridays | 142 | +0.1k | -0.0k | 49% |
| ALL | 12:00 | up >= 2R | 64 | +0.2k | +0.0k | 44% |
| ALL | 12:00 | up >= $15k | 37 | +0.5k | +0.8k | 35% |
| ALL | 12:00 | up >= $19k | 32 | -0.2k | +0.4k | 34% |
| ALL | 12:30 | all Fridays | 142 | -0.3k | -0.0k | 47% |
| ALL | 12:30 | up >= 2R | 64 | -0.5k | -0.0k | 47% |
| ALL | 12:30 | up >= $15k | 36 | +0.3k | +0.0k | 33% |
| ALL | 12:30 | up >= $19k | 33 | +0.5k | +0.0k | 33% |
| ALL | 14:00 | all Fridays | 142 | -0.2k | +0.0k | 36% |
| ALL | 14:00 | up >= 2R | 58 | -0.1k | +0.0k | 29% |
| ALL | 14:00 | up >= $15k | 39 | +0.4k | +0.0k | 23% |
| ALL | 14:00 | up >= $19k | 33 | +0.2k | +0.0k | 21% |

Dollar thresholds are shown because the user's case ("closed the last trade at 12:30 ET on a Friday, up $19k") is a +8R day on this scale. Cells with n < 10 are anecdote.

## 6. Drift of the give-back statistic by calendar quarter (is it new?) - D6 composite

| quarter | days | mean close | mean peak | give-back | give-back / peak | afternoon (12:00->close), all days | n up>=2R@12:00 | afternoon | up>=2R | %neg |
|---|---|---|---|---|---|---|---|---|---|
| 2026Q1 | 25 | +7.5k | 29.6k | 22.1k | 75% | -0.5k | 15 | -1.8k | 73% |
| 2025Q4 | 62 | +9.5k | 30.2k | 20.7k | 68% | +0.1k | 30 | -2.0k | 50% |
| 2025Q3 | 63 | +6.3k | 21.7k | 15.3k | 71% | +1.2k | 32 | +0.5k | 50% |
| 2025Q2 | 62 | +7.4k | 31.9k | 24.4k | 77% | +0.2k | 29 | +1.7k | 31% |
| 2025Q1 | 60 | +7.3k | 29.3k | 22.0k | 75% | -0.5k | 32 | -0.6k | 50% |
| 2024Q4 | 62 | +3.9k | 22.2k | 18.3k | 82% | -0.2k | 26 | -1.2k | 38% |
| 2024Q3 | 63 | +6.9k | 26.8k | 19.9k | 74% | +1.1k | 27 | +3.8k | 26% |
| 2024Q2 | 63 | +3.0k | 19.3k | 16.3k | 84% | +1.2k | 22 | +2.2k | 36% |
| 2024Q1 | 61 | +3.6k | 20.1k | 16.5k | 82% | -1.1k | 27 | -0.8k | 59% |
| 2023Q4 | 62 | +1.7k | 15.9k | 14.2k | 89% | -0.1k | 27 | -1.3k | 63% |
| 2023Q3 | 62 | +3.0k | 19.4k | 16.4k | 84% | -1.2k | 26 | -1.3k | 65% |
| 2023Q2 | 62 | -0.9k | 16.5k | 17.4k | 105% | -0.5k | 23 | -1.5k | 52% |

The afternoon after an up-2R noon has the same sign in 8 of 12 quarters (negative), i.e. no stable sign; the give-back / peak ratio falls over time. The pattern is not new (2023Q2-Q4 shows the same size give-back) and not stable.

## 7. Per book (own BookR = planned lots x 60 pts x $20; own live sessions)

| book | window | days | mean close | mean peak | give-back mean | 80th | afternoon(12:00) all: mean / %neg | up>=2R_own @12:00 | up>=2R_own @14:00 |
|---|---|---|---|---|---|---|---|---|---|
| K6 (R=$2.4k) | L6M | 129 | +1.2k | 5.2k | 4.0k | 6.3k | +0.1k / 43% | n=29: -0.2k / 55% | n=31: -0.1k / 32% |
| K6 (R=$2.4k) | PRE+X | 557 | +0.6k | 4.4k | 3.8k | 6.5k | -0.0k / 38% | n=85: +0.2k / 48% | n=95: -0.0k / 43% |
| P6 (R=$8.4k) | L6M | 129 | +5.3k | 17.5k | 12.2k | 21.3k | +0.3k / 22% | n=30: -1.0k / 23% | n=30: +0.5k / 7% |
| P6 (R=$8.4k) | PRE+X | 557 | +2.1k | 13.9k | 11.8k | 21.7k | -0.1k / 24% | n=84: -0.2k / 29% | n=87: +0.0k / 7% |
| U6 (R=$4.8k) | L6M | 129 | -0.0k | 2.9k | 2.9k | 4.3k | +0.0k / 0% | n=5: +0.0k / 0% | n=5: +0.0k / 0% |
| U6 (R=$4.8k) | PRE+X | 557 | +0.5k | 3.1k | 2.6k | 4.6k | +0.0k / 1% | n=15: +0.0k / 0% | n=15: +0.0k / 0% |
| H6 (R=$4.8k) | L6M | 129 | +1.9k | 5.3k | 3.5k | 5.8k | +0.2k / 14% | n=12: +0.4k / 8% | n=14: +0.2k / 0% |
| H6 (R=$4.8k) | PRE+X | 557 | +0.3k | 3.9k | 3.6k | 6.5k | -0.0k / 22% | n=29: -0.1k / 17% | n=30: -0.0k / 3% |
| M6 (R=$2.4k) | L6M | 129 | +0.2k | 3.8k | 3.5k | 6.2k | -0.1k / 26% | n=19: -0.7k / 42% | n=18: +0.0k / 0% |
| M6 (R=$2.4k) | PRE+X | 557 | +0.2k | 3.0k | 2.8k | 5.5k | -0.0k / 24% | n=62: +0.1k / 21% | n=72: -0.1k / 3% |
| A6 (R=$1.2k) | L6M | 129 | +0.3k | 1.4k | 1.1k | 2.3k | -0.0k / 0% | n=10: -0.0k / 0% | n=10: +0.0k / 0% |
| A6 (R=$1.2k) | PRE+X | 557 | +0.3k | 1.1k | 0.8k | 2.2k | -0.0k / 1% | n=24: +0.0k / 0% | n=24: +0.0k / 0% |

Per-book mean paths at key times (L6M and PRE+X):

| book/window | 18:00 | 21:00 | 00:00 | 03:00 | 05:00 | 07:00 | 09:00 | 09:30 | 10:30 | 12:00 | 14:00 | 16:00 | 17:00 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K6 L6M | +0.0k | +0.1k | +0.3k | +0.3k | +0.5k | +0.6k | +0.9k | +1.0k | +1.0k | +1.1k | +1.1k | +1.2k | +1.2k |
| K6 PRE+X | +0.0k | +0.1k | +0.2k | +0.3k | +0.2k | +0.1k | +0.2k | +0.2k | +0.4k | +0.6k | +0.6k | +0.6k | +0.6k |
| P6 L6M | +0.0k | +1.0k | +1.3k | +1.9k | +2.5k | +2.5k | +3.0k | +3.0k | +3.5k | +5.0k | +5.1k | +5.2k | +5.3k |
| P6 PRE+X | +0.0k | +0.5k | +0.7k | +1.0k | +1.1k | +0.7k | +1.2k | +1.2k | +1.8k | +2.2k | +2.2k | +2.2k | +2.1k |
| U6 L6M | +0.0k | +0.1k | +0.1k | +0.3k | +0.3k | +0.1k | -0.1k | -0.1k | -0.0k | -0.0k | -0.0k | -0.0k | -0.0k |
| U6 PRE+X | +0.0k | +0.1k | +0.2k | +0.4k | +0.4k | +0.4k | +0.4k | +0.4k | +0.6k | +0.5k | +0.5k | +0.5k | +0.5k |
| H6 L6M | +0.0k | +0.6k | +0.9k | +1.1k | +1.3k | +1.2k | +1.2k | +1.3k | +1.4k | +1.7k | +1.8k | +1.9k | +1.9k |
| H6 PRE+X | +0.0k | +0.2k | +0.3k | +0.3k | +0.3k | +0.3k | +0.2k | +0.2k | +0.3k | +0.3k | +0.3k | +0.3k | +0.3k |
| M6 L6M | +0.0k | +0.0k | +0.0k | -0.0k | +0.1k | -0.0k | -0.0k | -0.1k | +0.0k | +0.4k | +0.3k | +0.2k | +0.2k |
| M6 PRE+X | +0.0k | +0.0k | +0.0k | +0.0k | +0.0k | -0.1k | -0.1k | -0.1k | +0.2k | +0.2k | +0.2k | +0.2k | +0.2k |
| A6 L6M | +0.0k | +0.1k | +0.1k | +0.3k | +0.3k | +0.4k | +0.4k | +0.3k | +0.3k | +0.3k | +0.3k | +0.3k | +0.3k |
| A6 PRE+X | +0.0k | +0.0k | +0.1k | +0.2k | +0.2k | +0.2k | +0.3k | +0.3k | +0.3k | +0.3k | +0.3k | +0.3k | +0.3k |

## 8. Notes and limits

- Descriptive only: no cell is selected, nothing here is a rule. Overlapping windows (Y26 < L3M < L6M < HOLD) are not independent looks. Day counts are beside every statistic; n < 30 cells are anecdote.
- "Up X by T" uses the realised + open P&L at T, which includes the overnight sessions: at live lots the stack is up >= 1R ($2.4k) on ~60% of days by 10:30 already, so X = 1-4 K6-R is a low bar for a 25-lot stack; the extension table goes to 12R.
- The afternoon is thin at live lots (median afternoon P&L is 0: P6 / U6 / H6 / M6 are not live after NY-AM except H6 2 lots in NY-AM; only K6 and A6 trade NY-PM), so medians of exactly 0 are "no afternoon trading", not "flat".
- The give-back placebo permutes the 5-minute increments inside each day (300 draws, seed 11): it removes the time-of-day structure but keeps the day total; it is a null for "the path is a random walk given its increments", not for the lock engine.
- Peak uses 1-second closes (no intra-second high/low); a few-percent understatement of the peak is possible.
- A6 = PB7 comes from the D1 wrapper; ST/WT/O6 are not in the live D6 set (O6 not in the engine).
