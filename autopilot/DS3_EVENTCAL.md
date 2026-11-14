# DS3_EVENTCAL - macro event calendar + VIX for the no-UW benchmark (W-CAL). Rebuilt 2026-11-13T23:33Z by code/th_cal/cal_loop.sh (every 3 h). Research only, NO PASS claim.

**Verdict: Part 3 calendar and flags delivered; forecast re-run (iv_term, flip, gamma, charm, vanna, tide over ATR + IV + DOW + events + VIX) not yet scored.**

## 1. Calendar (free public sources only)
- File /mnt/l2/l2vast/_calendar/events.csv: 562 rows 2024-10-01..2026-12-31; columns epoch_s, date_et, time_et, kind, name, source_url, verified. verified = 1 (read from the official page), rule (ISM: published rule first/third business day 10:00 ET, dates computed, not read from a calendar), UNVERIFIED (excluded from flags): 1 row(s).
- Sources: Fed fomccalendars.htm (FOMC decision + minutes 14:00 ET), BLS archive/schedule pages (CPI, PPI, NFP 08:30), BEA schedule pages (GDP, Personal Income and Outlays=PCE; times read per row, some 10:00), Census MARTSreleasedates.xlsx (retail sales 08:30), TreasuryDirect TA_WS auctioned/announced json (note/bond/TIPS/FRN competitive close time, mostly 13:00), Fed ne-speeches.json + calendar.json (Chair/Chairman only), SEC EDGAR 8-K item 2.02 acceptance time (megacap earnings; BMO if before 09:30 ET, AMC if from 15:55), NVDA IR release (Nov 17 2026 AMC), ISM published rule.
- Known holes: BLS/BEA/Census data for Oct-Nov 2025 follow the funding-lapse re-schedule (CPI Oct 2025 not published; GDP Q3 2025 initial 2025-12-23; a BEA row with no View link on 2025-10-30 was dropped as postponed). Treasury auctions after about 2026-11-12 appear only when announced (Dec 2026 coupon auctions mostly not yet); the Oct 2024 2-year auction is missing from the TreasuryDirect window. 2026-10-27/28 FOMC minutes date is not on the Fed page (UNVERIFIED, excluded). Earnings times are EDGAR acceptance times (seconds-minutes after the press release). Fed speech times are as listed by the Fed (taken as ET). BLS pages block scripted curl (403): dates were read through the WebFetch tool from the BLS archive file names, so each BLS date is as read by that tool.

| kind | n | first | last |
|---|---|---|---|
| AUC_BOND_20Y | 26 | 2024-10-23 | 2026-11-18 |
| AUC_BOND_30Y | 26 | 2024-10-10 | 2026-11-12 |
| AUC_FRN_2Y | 22 | 2025-01-28 | 2026-10-28 |
| AUC_NOTE_10Y | 26 | 2024-10-09 | 2026-11-10 |
| AUC_NOTE_2Y | 24 | 2024-11-25 | 2026-10-26 |
| AUC_NOTE_3Y | 26 | 2024-10-08 | 2026-11-09 |
| AUC_NOTE_5Y | 25 | 2024-10-28 | 2026-10-27 |
| AUC_NOTE_7Y | 25 | 2024-10-29 | 2026-10-29 |
| AUC_TIPS_10Y | 13 | 2024-11-21 | 2026-11-19 |
| AUC_TIPS_30Y | 4 | 2025-02-20 | 2026-08-20 |
| AUC_TIPS_5Y | 9 | 2024-10-24 | 2026-10-22 |
| CHAIR_SPEECH | 27 | 2024-11-14 | 2026-11-16 |
| CPI | 26 | 2024-10-10 | 2026-12-10 |
| EARN_AMC | 62 | 2024-10-23 | 2026-11-17 |
| FOMC | 18 | 2024-11-07 | 2026-12-09 |
| FOMC_MIN | 18 | 2024-10-09 | 2026-11-18 |
| GDP | 26 | 2024-10-30 | 2026-12-23 |
| ISM_MFG | 27 | 2024-10-01 | 2026-12-01 |
| ISM_SVC | 27 | 2024-10-03 | 2026-12-03 |
| NFP | 26 | 2024-10-04 | 2026-12-04 |
| PCE | 26 | 2024-10-31 | 2026-12-23 |
| PPI | 26 | 2024-10-11 | 2026-12-15 |
| RETAIL | 27 | 2024-10-17 | 2026-12-16 |

## 2. Daily per-session flags
- File /mnt/l2/l2vast/_calendar/event_flags.parquet (+ .csv): one row per weekday 2024-10-01..2026-12-31; columns {hi,mac,chair,auc,earn,any,anyauc,n}_{asia,london,pre,nyam,nyam2,nypm,last90} + ev_day, hi_day, ev_day_any, earn_prev, earn_amc_today, kinds_day. Flags are for scheduled releases = known in advance, so they may be used at any reading time.
- Group hi = FOMC decision/CPI/NFP; mac = PPI/PCE/GDP/retail/ISM/FOMC minutes; any = hi|mac|chair|earn (auctions kept separate).

| session | days with any event (any_) | hi_ | mac_ | auc_ | earn_ | chair_ |
|---|---|---|---|---|---|---|
| asia | 3 | 0 | 0 | 0 | 0 | 3 |
| london | 0 | 0 | 0 | 0 | 0 | 0 |
| pre | 130 | 50 | 79 | 0 | 0 | 4 |
| nyam | 65 | 0 | 55 | 10 | 0 | 11 |
| nyam2 | 65 | 0 | 55 | 10 | 0 | 10 |
| nypm | 70 | 17 | 17 | 167 | 40 | 6 |
| last90 | 1 | 0 | 0 | 0 | 0 | 1 |
| day (ev_day / hi_day / ev_day_any) | 217 / 67 / 235 | | | | | |

(counts over 552 weekdays 2024-10-02..2026-11-12)

## 2b. VIX and VIX futures
- Free daily history exists: Cboe public csv cdn.cboe.com/api/global/us_indices/daily_prices/{VIX,VIX3M,VIX9D,VVIX}_History.csv (VVIX close only) and VX futures settles from cdn.cboe.com/data/us/futures/market_statistics/historical_data/VX/VX_<expiry>.csv (117 contract files). Built into /mnt/l2/l2vast/_calendar/vix_daily.parquet (569 rows 2024-09-02..2026-11-13; vix_ / vix3m_ / vix9d_ OHLC, vvix_CLOSE, vx1, vx2, vx_slope, vx1_basis, vix_term, vix9d_term). Use the PRIOR trading day close only.
- Last VIX close 18.70 on 2026-11-12; VX monthly contract per label is the file with the most rows (weekly files hold few rows); the dte columns are indicative only.

## 3. Forecast re-run
Pending (see verdict).

