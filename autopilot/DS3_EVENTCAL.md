# DS3_EVENTCAL - macro event calendar + VIX for the no-UW benchmark (W-CAL). Rebuilt 2026-11-14T00:42Z by code/th_cal/cal_loop.sh (every 3 h). Research only, NO PASS claim.

**Verdict: Calendar and VIX do not erase the UW range forecast: most of it survives. Of 42 watched session/input pairs (iv_term, flip, gamma, charm, vanna, tide x 7 sessions) 16 keep a YES over ATR+IV+DOW+events+VIX positive in L6M, L3M and H1 (asia/iv_term, asia/flip, asia/tide, london/iv_term, london/flip, pre/iv_term, nyam/iv_term, nyam/vanna, nyam2/iv_term, nyam2/flip, nypm/flip, nypm/gamma, nypm/tide, late/flip, late/gamma, late/tide); 4 keep a YES but not in all windows (london/tide, nyam/charm, nyam2/gamma, nyam2/vanna); 4 are relabelled "calendar proxy" (pre/flip, nyam2/charm, nypm/iv_term, late/iv_term); 17 are weak only; calendar and VIX add real gain by themselves only in pre and nypm (event flags). Range-class YES rows 98 (vs IV) -> 88 (vs CAL). No PASS.**

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

## 3. Forecast re-run: gain over ATR + IV + DOW (IV) vs over ATR + IV + DOW + event flags + VIX set (CAL)
- Rows: 8302 (read x session x target x group). Same panel, same ridge walk-forward (min 120 d, refit every 10 trading days), same shifted-time null draws (20) and family null as W-UR1. Gains in percentage points of variance explained. IV = strict W-UR1 benchmark; CAL = IV + event flags (target session and day) + VIX set (prior close).
- YES = gain>0, 90% block-bootstrap CI low>0, gain>family q95 (max over groups x readings per session-target). weak = gain>0 and > own null q95. A lead needs the recent windows (L6M, L3M) and the older window (H1) all positive; none claimed here as PASS.

### 3a. What the calendar and VIX add by themselves (over ATR + IV + DOW; range class)
| session | group | best reading/target | gain full | L6M | L3M | H1 | CI90 | null q95 | fam q95 | verdict | gain on event days | non-event days |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| asia | cal:events_sess | R0 lnrng | -0.10 | +0.10 | +0.31 | -0.00 | [-0.36,+0.08] | +0.17 | +3.98 | no | -0.14 | -0.07 |
| asia | cal:events_day | R0 lnrv | -0.21 | -1.80 | +0.33 | -0.50 | [-1.04,+0.68] | +0.00 | +1.91 | no | +0.19 | -0.52 |
| asia | vix:set | R0 lnrv | +0.08 | -8.87 | -2.40 | +4.54 | [-2.69,+2.41] | +0.93 | +1.91 | no | +3.00 | -2.12 |
| london | cal:events_sess | R0 lnrng | +0.00 | -0.00 | +0.00 | +0.00 | [-0.00,+0.00] | +0.00 | +1.79 | no | -0.00 | +0.00 |
| london | cal:events_day | R0 lnrng | -0.12 | +0.83 | +4.43 | +0.46 | [-2.39,+1.33] | +0.15 | +1.79 | no | +0.09 | -0.28 |
| london | vix:set | R0 lnrng | +0.45 | +3.87 | +3.29 | -1.67 | [-1.46,+3.63] | +1.62 | +1.79 | no | +2.00 | -0.72 |
| pre | cal:events_sess | R1 lnrng | +15.01 | +32.23 | +42.31 | +9.13 | [+8.56,+24.03] | -0.53 | +2.30 | YES | +19.56 | +8.14 |
| pre | cal:events_day | R1 lnrng | +7.32 | +21.03 | +29.18 | +1.94 | [+2.80,+16.16] | -0.48 | +2.30 | YES | +6.69 | +8.28 |
| pre | vix:set | R1 lnrng | +1.73 | +2.97 | +4.81 | +1.18 | [-8.16,+6.72] | +0.73 | +2.30 | weak | +5.30 | -3.67 |
| nyam | cal:events_sess | R0 lnrv | +0.07 | -0.72 | +0.36 | +0.33 | [-1.02,+1.30] | -0.30 | +1.64 | weak | +1.30 | -0.56 |
| nyam | cal:events_day | R0 lnrv | +0.61 | +0.98 | +2.04 | +0.54 | [-0.47,+1.72] | -0.41 | +1.64 | weak | +2.63 | -0.44 |
| nyam | vix:set | R1 lnrv | +0.75 | +0.06 | -5.70 | +1.56 | [+0.00,+1.64] | +0.47 | +1.64 | weak | +1.11 | +0.57 |
| nyam2 | cal:events_sess | R3 lnrng | -0.42 | -0.55 | +1.10 | -0.04 | [-1.17,+0.52] | -0.13 | +3.04 | no | -0.88 | -0.19 |
| nyam2 | cal:events_day | R3 lnrv | -0.32 | -0.24 | -0.14 | -0.11 | [-0.77,+0.06] | -0.39 | +1.81 | no | -0.62 | -0.17 |
| nyam2 | vix:set | R3 lnrv | -0.36 | -0.62 | -3.66 | -0.16 | [-0.98,+0.23] | +0.43 | +1.81 | no | -0.35 | -0.36 |
| nypm | cal:events_sess | R3 lnrv | +5.31 | +8.91 | +13.73 | +4.35 | [+2.35,+8.66] | +1.11 | +2.01 | YES | +12.54 | -0.10 |
| nypm | cal:events_day | R1 lnrv | +1.53 | +2.32 | +3.18 | +0.90 | [-0.96,+3.78] | +0.32 | +2.01 | weak | +4.01 | -0.33 |
| nypm | vix:set | R1 lnrv | +0.42 | +1.49 | +1.13 | -0.07 | [-0.63,+1.35] | +0.40 | +2.01 | weak | +0.70 | +0.21 |
| late | cal:events_sess | R3 lnrv | -0.02 | -0.06 | +0.11 | +0.00 | [-0.20,+0.16] | +0.16 | +1.89 | no | -0.06 | +0.01 |
| late | cal:events_day | R3 lnrng | +1.98 | +5.74 | -2.64 | +1.38 | [-0.20,+4.57] | +0.12 | +3.00 | weak | +2.80 | +1.17 |
| late | vix:set | R3 lnrng | +1.35 | +8.26 | +9.16 | -2.33 | [-1.80,+7.17] | +0.12 | +3.00 | weak | +1.59 | +1.11 |

### 3b. Survival of the watched inputs (best ticker/reading per session; range class = ln range, ln RV; vs IV then vs CAL)
| session | input family | best row (group, read, target) | IV gain | IV verdict | CAL gain | CAL L6M | CAL L3M | CAL H1 | CAL CI90 | CAL null q95 | CAL fam q95 | CAL verdict | bench R2 IV / CAL | adj gain vs stronger bench | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| asia | iv_term | QQQ:iv_term R0 lnrng | +9.82 | YES | +11.84 | +9.15 | +7.32 | +15.53 | [+4.93,+17.11] | +1.41 | +6.10 | YES | 30.2 / 26.9 | +8.55 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| asia | flip | SPY:flip R0 lnrv | +2.84 | YES | +3.05 | +5.81 | +4.18 | +1.20 | [+1.74,+5.28] | -0.13 | +2.67 | YES | 62.9 / 62.9 | +3.05 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| asia | gamma | QQQ:gamma R0 lnrv | +1.88 | weak | +2.01 | +6.58 | +2.45 | -0.39 | [+0.27,+3.99] | +0.23 | +2.67 | weak | 62.9 / 62.9 | +2.01 | weak only (beats own null, not family null) |
| asia | charm | SPX:charm R0 lnrv | +0.36 | weak | +0.50 | +2.25 | +0.99 | -0.62 | [-0.30,+1.34] | -0.05 | +2.67 | weak | 62.9 / 62.9 | +0.50 | weak only (beats own null, not family null) |
| asia | vanna | SPX:vanna R0 lnrv | -0.36 | no | +0.22 | +2.10 | +6.03 | -0.46 | [-0.91,+1.14] | -0.29 | +2.67 | weak | 62.9 / 62.9 | +0.22 | weak only (beats own null, not family null) |
| asia | tide | tide R0 lnrv | +3.17 | YES | +2.67 | +5.53 | +4.25 | +0.40 | [+1.33,+4.07] | +0.10 | +2.67 | YES | 62.9 / 62.9 | +2.67 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| london | iv_term | QQQ:iv_term R0 lnrv | +6.04 | YES | +6.46 | +12.81 | +0.43 | +6.51 | [+3.72,+9.20] | +0.64 | +2.41 | YES | 56.0 / 55.8 | +6.20 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| london | flip | ALL4:flip R0 lnrv | +3.10 | YES | +3.13 | +1.97 | +1.21 | +3.28 | [+0.75,+5.63] | -0.09 | +2.41 | YES | 56.0 / 55.8 | +2.87 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| london | gamma | SPY:gamma R0 lnrv | +1.84 | weak | +1.96 | +6.87 | +7.20 | -0.40 | [-0.00,+4.18] | -0.09 | +2.41 | weak | 56.0 / 55.8 | +1.70 | weak only (beats own null, not family null) |
| london | charm | SPY:charm R0 lnrng | +2.24 | weak | +3.19 | -2.41 | -3.72 | +5.62 | [-1.70,+6.89] | +0.36 | +3.06 | weak | 23.6 / 24.0 | +3.19 | weak only (beats own null, not family null) |
| london | vanna | QQQ:vanna R0 lnrng | +1.39 | weak | +1.22 | -0.63 | -3.99 | +1.35 | [+0.03,+2.23] | +0.97 | +3.06 | weak | 23.6 / 24.0 | +1.22 | weak only (beats own null, not family null) |
| london | tide | tide R0 lnrv | +3.22 | YES | +2.81 | +2.66 | -2.29 | +1.27 | [+1.27,+4.51] | +0.46 | +2.41 | YES | 56.0 / 55.8 | +2.56 | survives (YES vs CAL) but not positive in all windows |
| pre | iv_term | QQQ:iv_term R0 lnrv | +7.66 | YES | +6.90 | +9.97 | +4.87 | +8.22 | [+3.25,+9.93] | +0.61 | +1.47 | YES | 40.9 / 46.6 | +6.90 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| pre | flip | NDX:flip R0 lnrng | -1.09 | no | +1.69 | +0.94 | +1.37 | +2.47 | [-1.94,+3.83] | +0.91 | +2.83 | weak | 26.3 / 34.8 | +1.69 | calendar proxy (YES vs IV, no YES left vs CAL) |
| pre | gamma | QQQ:gamma R0 lnrv | +0.32 | weak | +0.72 | +4.59 | +4.80 | -1.24 | [-0.26,+2.17] | +0.25 | +1.47 | weak | 40.9 / 46.6 | +0.72 | weak only (beats own null, not family null) |
| pre | charm | SPY:charm R1 lnrng | -0.41 | no | +0.55 | -1.06 | +0.13 | +1.30 | [-2.11,+1.97] | +0.50 | +2.83 | weak | 24.8 / 37.5 | +0.55 | weak only (beats own null, not family null) |
| pre | vanna | IWM:vanna R1 lnrng | -0.87 | no | +0.32 | -1.11 | -0.35 | +0.40 | [-3.07,+2.57] | +1.06 | +2.83 | no | 24.8 / 37.5 | +0.32 | no gain |
| pre | tide | tide R0 lnrv | +0.88 | weak | +0.68 | +0.96 | +0.14 | -0.18 | [-0.21,+1.67] | -0.08 | +1.47 | weak | 40.9 / 46.6 | +0.68 | weak only (beats own null, not family null) |
| nyam | iv_term | SPY:iv_term R0 lnrv | +7.34 | YES | +7.14 | +14.94 | +5.54 | +3.05 | [+3.41,+11.55] | +0.11 | +1.47 | YES | 45.7 / 46.2 | +7.14 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| nyam | flip | SPY:flip R2 lnrng | +1.36 | weak | +1.97 | -4.92 | -4.08 | +5.48 | [-1.58,+4.71] | +0.23 | +2.40 | weak | 25.3 / 21.9 | -1.45 | weak only (beats own null, not family null) |
| nyam | gamma | MEGA:gamma R1 lnrng | +1.27 | weak | +1.82 | +5.15 | +4.80 | +4.54 | [-3.00,+4.83] | -0.70 | +2.40 | weak | 24.3 / 22.1 | -0.37 | weak only (beats own null, not family null) |
| nyam | charm | SPX:charm R1 lnrv | +7.36 | YES | +6.67 | +8.36 | -8.29 | +5.50 | [+2.05,+11.78] | -0.23 | +1.47 | YES | 57.4 / 58.0 | +6.67 | survives (YES vs CAL) but not positive in all windows |
| nyam | vanna | QQQ:vanna R1 lnrv | +4.93 | YES | +4.94 | +10.19 | +4.45 | +2.11 | [+0.26,+10.29] | +0.33 | +1.47 | YES | 57.4 / 58.0 | +4.94 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| nyam | tide | tide R0 lnrv | +0.52 | weak | +0.70 | +0.24 | -2.58 | +0.49 | [-1.14,+2.41] | +0.01 | +1.47 | weak | 45.7 / 46.2 | +0.70 | weak only (beats own null, not family null) |
| nyam2 | iv_term | IWM:iv_term R3 lnrv | +3.00 | YES | +3.63 | +9.78 | +9.12 | +1.13 | [+1.68,+6.40] | +0.18 | +1.96 | YES | 62.3 / 61.1 | +2.39 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| nyam2 | flip | NDX:flip R3 lnrv | +2.20 | YES | +2.08 | +2.85 | +10.79 | +0.54 | [+0.61,+3.56] | -0.07 | +1.96 | YES | 62.3 / 61.1 | +0.84 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| nyam2 | gamma | SPX:gamma R3 lnrv | +3.01 | YES | +2.75 | +3.70 | -0.88 | +1.71 | [+0.12,+6.15] | -0.11 | +1.96 | YES | 62.3 / 61.1 | +1.50 | survives (YES vs CAL) but not positive in all windows |
| nyam2 | charm | SPX:charm R3 lnrv | +3.54 | YES | +3.13 | -0.42 | -10.17 | +4.88 | [-0.19,+7.62] | -0.42 | +1.96 | weak | 62.3 / 61.1 | +1.88 | calendar proxy (YES vs IV, no YES left vs CAL) |
| nyam2 | vanna | QQQ:vanna R3 lnrv | +2.68 | weak | +3.30 | +4.89 | -7.35 | +2.06 | [+0.02,+7.04] | +0.18 | +1.96 | YES | 62.3 / 61.1 | +2.05 | survives (YES vs CAL) but not positive in all windows |
| nyam2 | tide | tide R3 lnrv | -0.14 | no | +0.39 | +3.15 | +4.93 | -1.49 | [-2.81,+2.63] | +0.15 | +1.96 | weak | 62.3 / 61.1 | -0.86 | weak only (beats own null, not family null) |
| nypm | iv_term | QQQ:iv_term R0 lnrv | +3.24 | YES | +1.55 | +0.48 | -6.06 | +2.51 | [-0.02,+2.93] | -0.13 | +1.66 | weak | 47.4 / 50.9 | +1.55 | calendar proxy (YES vs IV, no YES left vs CAL) |
| nypm | flip | QQQ:flip R3 lnrv | +5.02 | YES | +5.43 | +14.97 | +20.05 | +1.31 | [+2.74,+8.39] | -0.18 | +1.66 | YES | 52.5 / 57.6 | +5.43 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| nypm | gamma | SPX:gamma R1 lnrv | +1.16 | weak | +1.72 | +5.91 | +11.32 | +0.72 | [+0.04,+3.42] | -0.10 | +1.66 | YES | 51.7 / 56.0 | +1.72 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| nypm | charm | IWM:charm R1 lnrng | +1.26 | weak | +1.58 | +1.35 | +1.94 | +1.65 | [-3.21,+3.46] | +0.58 | +4.25 | weak | 26.1 / 23.9 | -0.61 | weak only (beats own null, not family null) |
| nypm | vanna | DIA:vanna R1 lnrv | +0.34 | no | +1.07 | +1.52 | +5.19 | +0.83 | [-0.23,+2.51] | +0.63 | +1.66 | weak | 51.7 / 56.0 | +1.07 | weak only (beats own null, not family null) |
| nypm | tide | tide R3 lnrv | +2.84 | YES | +3.14 | +10.67 | +16.31 | +1.28 | [+1.49,+4.94] | -0.15 | +1.66 | YES | 52.5 / 57.6 | +3.14 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| late | iv_term | SPY:iv_term R0 lnrng | +2.50 | weak | +1.69 | +0.64 | +0.60 | +2.35 | [+0.05,+2.93] | +0.81 | +3.66 | weak | 30.0 / 31.0 | +1.69 | calendar proxy (YES vs IV, no YES left vs CAL) |
| late | flip | QQQ:flip R3 lnrv | +6.64 | YES | +7.68 | +15.78 | +19.23 | +3.38 | [+4.41,+11.37] | -0.48 | +1.67 | YES | 46.2 / 48.0 | +7.68 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| late | gamma | SPX:gamma R3 lnrv | +3.03 | YES | +3.52 | +7.46 | +13.83 | +1.09 | [+1.41,+5.81] | +0.12 | +1.67 | YES | 46.2 / 48.0 | +3.52 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |
| late | charm | SPY:charm R3 lnrng | -0.60 | no | +1.60 | -1.47 | +2.78 | +3.58 | [-3.56,+4.04] | +0.92 | +3.66 | weak | 29.7 / 33.0 | +1.60 | weak only (beats own null, not family null) |
| late | vanna | SPY:vanna R0 lnrng | -0.68 | no | +1.67 | -5.24 | -4.85 | +4.85 | [-7.32,+7.64] | -0.31 | +3.66 | weak | 30.0 / 31.0 | +1.67 | weak only (beats own null, not family null) |
| late | tide | tide R3 lnrv | +2.49 | YES | +3.15 | +9.74 | +13.46 | +0.81 | [+1.47,+4.99] | -0.19 | +1.67 | YES | 46.2 / 48.0 | +3.15 | survives (YES vs CAL; L6M, L3M, H1 all positive; weak lead, not PASS) |

### 3c. Every input family vs CAL: range-class YES rows
- YES rows (range class) vs IV: 98; vs CAL: 88.
- asia: YES vs IV 6 groups; still YES vs CAL 4: QQQ:iv_level, QQQ:iv_term, SPY:flip, tide; YES vs IV but not vs CAL ("calendar proxy"): ALL4:flip, NDX:iv_term
- london: YES vs IV 4 groups; still YES vs CAL 4: ALL4:flip, QQQ:iv_level, QQQ:iv_term, tide; YES vs IV but not vs CAL ("calendar proxy"): NDX:iv_term
- pre: YES vs IV 8 groups; still YES vs CAL 4: NDX:iv_term, QQQ:iv_level, QQQ:iv_term, SPY:iv_term; YES vs IV but not vs CAL ("calendar proxy"): ALL4:flip, IWM:absflip_wall, IWM:iv_term, cal:events_day, cal:events_sess
- nyam: YES vs IV 6 groups; still YES vs CAL 6: DIA:iv_term, IWM:iv_term, QQQ:iv_term, QQQ:vanna, SPX:charm, SPY:iv_term; YES vs IV but not vs CAL ("calendar proxy"): none
- nyam2: YES vs IV 5 groups; still YES vs CAL 5: IWM:iv_term, NDX:flip, QQQ:vanna, SPX:gamma, SPY:iv_term; YES vs IV but not vs CAL ("calendar proxy"): SPX:charm
- nypm: YES vs IV 13 groups; still YES vs CAL 16: ALL4:flip, DIA:impmove_vs_actual, IWM:flip, IWM:impmove_vs_actual, NDX:flip, QQQ:flip, QQQ:gamma, QQQ:gamma_chg, QQQ:walls, SPX:flip, SPX:gamma, SPX:gamma_chg, SPX:walls, SPY:flip, SPY:walls, tide; YES vs IV but not vs CAL ("calendar proxy"): QQQ:iv_term, cal:events_sess
- late: YES vs IV 18 groups; still YES vs CAL 13: ALL4:flip, IWM:flip, NDX:flip, QQQ:flip, QQQ:gamma, QQQ:walls, SPX:flip, SPX:gamma, SPX:gamma_chg, SPX:walls, SPY:flip, SPY:walls, tide; YES vs IV but not vs CAL ("calendar proxy"): IWM:iv_term, NDX:impmove_vs_actual, QQQ:impmove_vs_actual, QQQ:iv_term, SPY:iv_term

### 3d. Event-day vs non-event-day gain (same out-of-sample predictions, CAL benchmark), watched families, best row per session
| session | input family | best row | gain event days | non-event days | n event days in OOS (approx) |
|---|---|---|---|---|---|
| asia | iv_term | QQQ:iv_term R0 lnrng | +4.70 | +18.11 | |
| asia | flip | SPY:flip R0 lnrv | +3.00 | +3.09 | |
| asia | gamma | QQQ:gamma R0 lnrv | +2.88 | +1.36 | |
| asia | charm | SPX:charm R0 lnrv | +0.74 | +0.31 | |
| asia | vanna | SPX:vanna R0 lnrv | +0.21 | +0.23 | |
| asia | tide | tide R0 lnrv | +3.51 | +2.03 | |
| london | iv_term | QQQ:iv_term R0 lnrv | +6.11 | +6.70 | |
| london | flip | ALL4:flip R0 lnrv | +2.51 | +3.56 | |
| london | gamma | SPY:gamma R0 lnrv | +2.15 | +1.82 | |
| london | charm | SPY:charm R0 lnrng | +5.89 | +1.14 | |
| london | vanna | QQQ:vanna R0 lnrng | +0.51 | +1.75 | |
| london | tide | tide R0 lnrv | +4.20 | +1.85 | |
| pre | iv_term | QQQ:iv_term R0 lnrv | +5.52 | +8.06 | |
| pre | flip | NDX:flip R0 lnrng | +1.78 | +1.56 | |
| pre | gamma | QQQ:gamma R0 lnrv | +2.31 | -0.61 | |
| pre | charm | SPY:charm R1 lnrng | +1.13 | -0.33 | |
| pre | vanna | IWM:vanna R1 lnrng | +0.72 | -0.29 | |
| pre | tide | tide R0 lnrv | +0.78 | +0.60 | |
| nyam | iv_term | QQQ:iv_term R0 lnrv | +8.17 | +9.67 | |
| nyam | flip | SPY:flip R2 lnrng | +4.02 | +1.24 | |
| nyam | gamma | MEGA:gamma R1 lnrng | +11.16 | -1.51 | |
| nyam | charm | SPX:charm R1 lnrv | -0.46 | +10.35 | |
| nyam | vanna | QQQ:vanna R2 lnrv | +2.38 | +6.97 | |
| nyam | tide | tide R0 lnrv | +3.34 | -0.67 | |
| nyam2 | iv_term | IWM:iv_term R3 lnrv | +1.23 | +4.82 | |
| nyam2 | flip | NDX:flip R3 lnrng | +2.94 | +2.52 | |
| nyam2 | gamma | SPX:gamma R3 lnrv | +3.05 | +2.60 | |
| nyam2 | charm | SPX:charm R3 lnrv | -0.18 | +4.76 | |
| nyam2 | vanna | QQQ:vanna R3 lnrv | +2.51 | +3.69 | |
| nyam2 | tide | tide R3 lnrv | -0.50 | +0.82 | |
| nypm | iv_term | QQQ:iv_term R0 lnrv | +1.81 | +1.35 | |
| nypm | flip | QQQ:flip R3 lnrv | +6.48 | +4.64 | |
| nypm | gamma | SPX:gamma R3 lnrv | +3.96 | +1.56 | |
| nypm | charm | IWM:charm R1 lnrng | +3.10 | -0.88 | |
| nypm | vanna | DIA:vanna R1 lnrv | +0.94 | +1.16 | |
| nypm | tide | tide R3 lnrv | +2.80 | +3.40 | |
| late | iv_term | SPY:iv_term R0 lnrng | +0.85 | +2.53 | |
| late | flip | QQQ:flip R3 lnrv | +11.63 | +4.25 | |
| late | gamma | SPX:gamma R3 lnrv | +4.82 | +2.39 | |
| late | charm | SPY:charm R3 lnrng | +1.83 | +1.38 | |
| late | vanna | SPY:vanna R0 lnrng | +1.86 | +1.49 | |
| late | tide | tide R3 lnrv | +4.34 | +2.12 | |

