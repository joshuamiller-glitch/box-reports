# DISCOVER_EVENT_STUDY (descriptive census, no books; built 2026-11-03)

Files: `DISCOVER_EVENT_STUDY.csv` (window stats by event_type x time x year, plus ALL), `DISCOVER_EVENT_STUDY_CONT.csv` (continuation vs fade), `DISCOVER_EVENT_STUDY_SURPRISE.csv` (sign of actual minus prior). Code: `l2vast/ds3/code/discover/event_study.py` (reads `l2vast/ds3/out/def/NQ.parquet`, 1-min front-month, 2022-01..2026-10-16; back-adjusted at instrument_id changes). Calendar: `DISCOVER_CALENDAR.csv` rows with data (events to 2026-10-16).

## Definitions
- P(t) = open of the 1-min bar starting at t (price at the instant t). Window [a,b] = P(T+b) - P(T+a), in NQ points, T = release time ET. Windows: pre60 (-60,0), pre5 (-5,0), m0_1, m1_5, m0_5, m1_30, m5_30, m30_120. Missing bars give NaN (skipped).
- baseline_mean_abs = mean |window| at the same clock time over 567 weekdays with none of NFP/CPI/PPI/PCE/GDP/retail/FOMC (decision, presser, minutes)/ISM (claims days are allowed in the baseline). ratio_vs_base = event mean|move| / baseline.
- Continuation: first move = P(T+1)-P(T) (1m) or P(T+5)-P(T) (5m); later move = (1,30) or (5,30). frac_continue = share where later has the same sign as the first move (zero first moves dropped); mean_signed_later = mean of sign(first) x later (points; positive = continuation edge before costs).
- Rows with window `day_range_0930_1600`: mean_pts = mean RTH (09:30-16:00) high-low range, mean_abs_pts = mean |close-open|, baseline_mean_abs = baseline mean range (270.8 pts), ratio = range ratio. `d1000_1600` = P(16:00)-P(10:00) (CPI, NFP, PCE, GDP, retail, FOMC day), `t_to_1600` = 14:00 to 16:00 on FOMC days.
- Surprise sign uses actual vs PRIOR (first print vs previous month's print as revised in the same vintage). Prior is not consensus, so this is a weak proxy: the sign of "better than last month", not a surprise.

## Headline census (ALL years, 2023-04..2026-10; n about 28 for FOMC, 42 for CPI/NFP/PPI)
Mean |move| in points and ratio to a normal day at the same clock time:

| event | pre60 | m0_5 (ratio) | m1_30 (ratio) | m30_120 (ratio) |
|---|---|---|---|---|
| NFP 08:30 | 24 (0.86) | 66.7 (5.5x) | 54.6 (2.4x) | 115 (1.35x) |
| CPI 08:30 | 26 (0.94) | 92.2 (7.6x) | 51.2 (2.3x) | 85 (0.99x) |
| PPI 08:30 | 25 (0.89) | 46.4 (3.8x) | 34.4 (1.5x) | 78 (0.91x) |
| PCE 08:30 | 30 (1.06) | 32.9 (2.7x) | 33.7 (1.5x) | 129 (1.5x) |
| GDP 08:30 | 25 (0.89) | 27.0 (2.2x) | 35.0 (1.55x) | 102 (1.2x) |
| Retail sales 08:30 | 17 (0.62) | 23.7 (2.0x) | 32.9 (1.5x) | 67 (0.79x) |
| Claims 08:30 | 28 (1.00) | 24.1 (2.0x) | 29.1 (1.3x) | 93 (1.1x) |
| ISM mfg 10:00 | 78 (1.18) | 25.2 (1.1x) | 68.5 (1.5x) | 80 (1.24x) |
| ISM svc 10:00 | 78 (1.18) | 39.8 (1.8x) | 56.2 (1.2x) | 70 (1.08x) |
| FOMC statement 14:00 | 28 (0.70) | 48.9 (4.25x) | 37.7 (1.4x) | 142 (3.0x) |
| FOMC presser 14:30 | 63 (1.58) | 35.2 (3.05x) | 88.7 (3.5x) | 125 (2.6x) |
| FOMC minutes 14:00 | 76 (1.88) | 18.5 (1.6x) | 36.8 (1.3x) | 69 (1.45x) |

- Nothing happens before the data (pre60 ratios about 0.6-1.2, i.e. normal or quieter) except FOMC minutes (1.9x, small n) and the presser window (14:30 pre60 includes the statement reaction).
- RTH day range vs normal (270.8 pts): NFP 1.33x, FOMC 1.23x, 10Y auction days 1.20x, ISM mfg 1.21x, PCE 1.20x, CPI 1.12x, month-end 1.12x, quarterly opex 1.10x, roll week 1.10x, early-close days 0.34x. Other types 0.94-1.16x.
- 10:00-16:00 on CPI days: mean |move| 109 vs 120 normal (0.91x), mean -4.8 pts (median +6.5): no trend-day excess on CPI. NFP days 10:00-16:00: 182 abs (1.52x), mean -77 (median -16; skewed by a few large down days). FOMC days 10:00-16:00: 154 abs (1.28x); 14:00-16:00 mean -54 pts, median -4, abs 155.

## Continuation vs fade (ALL years; positive mean_signed_later = continuation)
| event | first 1m -> (1,30): frac cont / mean pts | first 5m -> (5,30): frac cont / mean pts |
|---|---|---|
| CPI | 0.41 / -11.0 | 0.43 / -8.9 |
| NFP | 0.60 / +8.2 | 0.48 / +4.2 |
| PPI | 0.57 / +3.8 | 0.48 / -4.8 |
| PCE | 0.55 / +1.5 | 0.55 / +8.0 |
| GDP | 0.56 / +6.1 | 0.56 / +8.7 |
| Retail | 0.56 / +1.8 | 0.54 / +8.5 |
| Claims | 0.50 / +3.1 | 0.48 / -2.1 |
| ISM mfg | 0.38 / -27.5 | 0.49 / -18.0 |
| ISM svc | 0.43 / -10.7 | 0.43 / -14.6 |
| FOMC statement | 0.43 / -3.8 | 0.41 / -6.4 |
| FOMC presser | 0.61 / +29.6 | 0.46 / -26.0 |
Sampling: with n=28..43, a fraction between 0.35 and 0.65 is inside noise (binomial sd about 0.08). Only CPI fade (0.41-0.43, mean -9 to -11 pts) and ISM mfg first-minute fade (0.38) lean one way, and by year CPI flips (2023 cont 0.67 / +16, 2024 0.42 / -10, 2025 0.45 / -8, 2026 0.20 / -31): unstable across years, 4 data points. FOMC presser first-minute continuation (0.61 / +30 pts, n=28) has opposite sign at 5 min; treat as unconfirmed. By year the 5-min fade is stronger in 2026 for CPI (0.20, n=10), FOMC statement (0.17, n=6), while NFP 2026 continues (0.80, +38, n=10).

## Surprise proxy (actual vs prior), 08:30
| event | group | n | mean first 5m (pts) | frac up | mean (5,30) | frac cont (5,30) |
|---|---|---|---|---|---|---|
| NFP | actual > prior | 24 | -10.1 | 0.50 | +5.6 | 0.46 |
| NFP | actual < prior | 18 | +37.9 | 0.78 | -5.2 | 0.50 |
| CPI | actual > prior (hotter m/m) | 22 | -16.3 | 0.41 | +10.0 | 0.41 |
| CPI | actual < prior (cooler) | 20 | +67.5 | 0.85 | -14.4 | 0.45 |
| Claims | > prior | 72 | +3.2 | 0.53 | +5.5 | 0.47 |
| Claims | < prior | 103 | +3.0 | 0.49 | -3.3 | 0.47 |
Reading: a CPI m/m below the previous month's m/m is followed by an up first-5m in 17 of 20 cases (mean +67 pts); a higher print gives only a mild down skew. NFP below prior: up 78% of the time. These are the sign-vs-prior, not consensus, so they partly reflect mean reversion of the series, not market surprise; the (5,30) leg afterward is a coin flip (0.41-0.50). The reaction is therefore concentrated in the first minutes (prefer entry at T+1 only if the fill is possible; the harness must treat T+1 entry as measured fills).

## Caveats
- Descriptive census only: no multiple-comparison correction across about 12 event types x 8 windows x years; the table shows medians next to means in the CSV for skew.
- Data ends 2026-10-16 (NQ file), so Oct 2026 events after that (NFP 11-06, CPI 11-10, FOMC 10-28) are not in. 2023 starts 2023-04. Early-close days are included in the event samples where the clock window is available (they hold few events).
- Consensus is not available; ISM dates are rule-derived; Treasury auction rows are in the CSV under their own event types (13:00 ET).
- Price at T uses the open of the T bar (no look-ahead into the release minute).
