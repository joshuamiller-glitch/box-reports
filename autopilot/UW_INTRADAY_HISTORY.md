# UW INTRADAY HISTORY: what is real intraday, what is rebuilt (W-WF1112, order 0340Z item 4; read-only, no endpoint called, nothing bought)

## ANSWER FIRST
- TRUE intraday history of UW BY-STRIKE data (walls, per-strike GEX) exists ONLY from the live recorder: 9 trading days with data (2026-11-13, 16, 17, 18 (partial: from 18:28Z), 19, 20, 23, 24, 25; also a 97 MB partial 11-12). The recorder process (pid 75822) started Nov 18, but the files from 11-12/13 come from the earlier recorder run. 11-26 (holiday) and 11-27 (pre-open) are empty.
- For every PAST date before 11-12, by-strike data (spot_strike, spot_exp_strike, oi_strike, gex_levels, greek_exp) is ONE end-of-day snapshot (DS3_UW: "for a PAST date rebuilt from end-of-day data, every strike time = close"). So historically only STATIC-PER-DAY walls/flip are testable (2024-10-01..2026-11-12, 553 days).
- The intraday series that DO have real history back to 2024-10-01: 1-minute spot exposure (spot_1m: aggregate gamma/charm/vanna per 1%, price = ATM strike; ~490-560 rows per RTH day), Market Tide 1-min (back to 2022-09 per docs; 486 rows/day, 07:30 ET on), net_prem_ticks 1-min per ticker (QQQ SPY IWM DIA), gflow0 (1-min or 5-min delta flow, 4 tickers), flow_per_strike / nprem / flow_alerts (time-stamped trade-level, day files per ticker).
- Ready file for the exit agents (W-DYNL, W-DYNOF, W-DYNQ): /mnt/l2/l2vast/_dynexit/uw_intraday_walls.parquet (4,466 one-minute rows, 9 days listed above; code code/wf_m11m12/uw_walls.py; README text in its `note` column).

## Table per quantity
| UW quantity | (a) real intraday history, from when | (b) past dates only rebuilt? | notes |
|---|---|---|---|
| spot exposure 1-min (gex totals, gamma/charm/vanna per 1%) | YES, spot_1m 2024-10-01..2026-11-12 (553 files); live stream gex:SPX/SPY/QQQ/NDX since 11-12/13 | no | NOT by strike; price = ATM strike (rounded) |
| gamma flip (gex-levels) | NO intraday: one record per day (file `time` ~20:49Z = end of day) | YES, EOD only 2024-10..2026-11-12 | live stream has no flip field; file `gamma_flip_net_sign` in my parquet is MY reconstruction (nearest sign change of per-strike net OI gamma), not UW's |
| call wall / put wall | NO intraday for past; one value per day | YES static per day | from the live by-strike stream I reconstruct them per minute (OI gamma max / min); all-expiry walls sit at far round strikes (7000/8000) and barely move; the +-3% window versions move 1-4 times a day |
| by-strike GEX (spot_strike, spot_exp_strike) | live gex_strike:SPX stream only: 11-13..11-25 (9 days) | YES: past dates = EOD snapshot (500 strikes) | stream: ~1.0-1.35 M messages/day, ~2,100 strike messages per minute, whole strike ladder re-sent every few seconds; OI fields change little intraday, vol-gamma fields update (about 80% of rows non-zero mid-day) |
| OI by strike (oi_strike) | none (daily file) | static per day | OI is published once a day anyway |
| net premium (net_prem_ticks, nprem) | YES 1-min tape_time rows, 2024-10-01.. (QQQ SPY IWM DIA; megacaps nprem 17 tickers) | no | |
| Market Tide | YES 1-min since 2022-09 (pulled 2024-10..2026-11-12 + live market_tide channel since 11-12) | no | live lag 2.7 s median (below) |
| IV term / skew (iv_term, vol_stats) | NO: one row per expiry per day | EOD only 2024-10..2026-11-12 | used as prior-day input in M11 |
| flow alerts | YES time-stamped events (start_time ms), per-day files per ticker 2024-10-01..2026-11-12 | no | |
| dark pool (dp_levels) | levels per day; QQQ SPY + 8 megacaps 2025-11-14..2026-11-12 only (260 days) | static per day | |
| 0DTE (flow per strike, zdte shares) | flow_per_strike time-stamped (day window), 0DTE share = daily | partly | |
| option trades (live channel option_trades:SPX/NDX) | live only 11-12/13..11-25 | not available historically in this form | |

## (c) Recorder days with true intraday by-strike data (files autopilot/forward/uw_live/<date>/gex_strike_SPX.jsonl)
2026-11-13 (956k msgs), 11-16 (1.15M), 11-17 (1.20M), 11-18 (355k, partial), 11-19 (1.27M), 11-20 (1.35M), 11-23 (1.11M), 11-24 (1.04M), 11-25 (1.14M); 11-12 partial (76k). = 9 full-or-near-full days. Rows in the ready file run 11:36-11:37Z .. 21:14Z (the stream starts at the US pre-open and the file ends at the recorder's last RTH minute).

## (d) Cadence and delivery lag (measured on 2026-11-25 from recv_ns minus message timestamp)
| stream | median | p90 | p99 |
|---|---|---|---|
| gex:SPX / NDX / QQQ (aggregates) | 160 ms | 225-235 ms | 600-800 ms |
| gex_strike:SPX (per-minute median of 50-sample) | 220-430 ms by day (all days 9) | | tail minutes up to 7 s, max one minute 87 s (reconnect) |
| option_trades | 113 ms | 180 ms | 390 ms |
| market_tide | 2.7 s | 3.1 s | 3.2 s |
Cadence: gex aggregates about 12,500 msgs/day per index (~1 per 2 s); gex_strike whole ladder repeated every few seconds. Conservative lag: 120 s (the ready file carries `available_utc_conservative` = last publish in the minute + 120 s); measured delivery is < 1 s except reconnect gaps (recorder reconnects at 00:45Z and 02:09Z today; a gap of up to a few minutes occurs), so 60 s would also be safe in normal operation but 120 s covers reconnects. The panel used in M11 uses +180 s.
Mapping to NQ: the file is in SPX points with the percentage distance from SPX spot at publish (`*_pct`). NQ points = pct/100 x NQ price at use time. I could NOT map with NQ prices: the box has no NQ 1-min after 2026-11-10 07:59Z nor 1-s after 2026-10-16 (DS3_UWBOOKS_DATA); every recorder day is after that.

## (e) What UW sells for intraday strike history
Repo docs (DS3_UW.md, DS3_UWBOOKS_DATA.md) only say: current plan is the Advanced month ($375, order 11-12), history lookback 2 years on most endpoints, by-strike for past dates rebuilt from end of day; they quote no price for true intraday strike history. I have not looked anything up on the web and called no endpoint. If Josh wants a quote (does UW sell historical per-strike snapshots, e.g. an enterprise or Periscope-style feed), it needs a web look-up or a question to UW support: ASK LEAD.

## Consequence for the exit work
- Static-per-day walls/flip: testable on 2024-10..2026-11-12 (553 days) as day-level inputs (trailing prior-day levels).
- Intraday wall/flip movement (a stop or target following the wall minute by minute): 9 days, about 4,466 minutes: label THIN; run on those days only, and score daily from the live recorder on the forward register so evidence accumulates (each new trading day adds about 550 minutes).
