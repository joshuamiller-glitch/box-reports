# DS3_UW — Unusual Whales API ADVANCED month ($375; user order 20:40Z supersedes the 20:35Z Basic trial; directive autopilot/DIRECTIVE_UW_ADVANCED_20261112.md). STATUS (2026-11-13 01:25Z): KEY RECEIVED; historical pulls FINISHED (1-min spot exposure + Market Tide 2024-10-01..2026-11-12, GEX levels/strike/greek daily, 1.7 GB under /mnt/l2/l2vast/uw); live websocket recorder running; scoring a-e NOT yet started (no scoring outputs exist at 01:25Z). Shadow only, no PASS claims.

## 1. API facts read from the official docs (api.unusualwhales.com/docs, llms.txt, operation pages)
Base https://api.unusualwhales.com, `Authorization: Bearer <key>` plus header `UW-CLIENT-API-ID: 100001`; all GET; 401 bad token, 402 payment paused, 403 not entitled (`historic_data_access_missing` = date before the token's earliest allowed date; also `advanced_tier_required`, `missing_access`), 422 bad input, 429/503 retry after `Retry-After`. Rate limits per plan are NOT stated in the docs (usage guide page has no numbers): puller runs 1 request/s and honours Retry-After until the real limit is measured.
| use | endpoint | params | resolution / depth per docs |
|---|---|---|---|
| 1-min MM exposure | GET /api/stock/{T}/spot-exposures | date (default last trading date) | ONE ROW PER MINUTE in the cash session: time, price (for index tickers = current ATM strike), gamma/charm/vanna per 1% move for OI, volume and directionalized volume. History depth NOT stated (Startup tier advertises 2-year lookback; 403 historic_data_access_missing if before the token's earliest date) |
| Market Tide | GET /api/market/market-tide | date, otm_only, interval_5m (docs conflict on default: test) | net_call_premium, net_put_premium, net_volume per 1-min (or 5-min) tick; data back to 2022-09-28 |
| GEX by strike (daily/EOD for past dates) | GET /api/stock/{T}/spot-exposures/strike | date, min/max_strike, limit<=500, page | strike rows with call/put gamma/delta/charm/vanna by oi, vol, ask, bid; recalculated per strike at most 1/s intraday but for a PAST date rebuilt from end-of-day data (every strike time = close) => NOT intraday history |
| strike x expiry | GET /api/stock/{T}/spot-exposures/expiry-strike (v2) ; /greek-exposure/strike-expiry needs expiry | date, expiry | daily |
| static greek exposure | GET /api/stock/{T}/greek-exposure, /greek-exposure/strike, /greek-exposure/expiry | date | daily |
| levels | GET /api/stock/{T}/gex-levels | date, source=vol|oi | call_wall, put_wall, gamma_magnet, gamma_flip (= zero gamma), nearby_flips; 'null' when none; docs: do not use gamma_flip for regime, use sign of call_gamma+put_gamma from greek-exposure |
Index tickers (SPX, VIX) can return null index prices / `missing_periscope` (CBOE approval) on some endpoints: probe SPX, SPXW, SPY, QQQ, NDX, NDXP and use whichever returns data.
Honest expectation: only `spot_1m` and `tide` can be intraday history; every other past-date product is end-of-day. Day-1 verdict decides.

## 2. Code (all in code/th_uw/; key read only from os.environ, never printed/logged/stored)
uw_common.py (client, rate limiter, store), uw_probe.py (day-1: endpoint x ticker x lookback 1d/1w/1m/6m/1y/2y/3y, prints only status/size/first-last timestamp, appends the 'UW day 1' verdict to MORNING.md), uw_pull.py (resumable, newest first, to /mnt/l2/l2vast/uw/<endpoint>/<ticker>/<date>.json), wait_key.sh (nohup loop, pid in /mnt/l2/l2vast/uw/wait_key.pid, polls `bash -ic 'test -n "$UW_API_KEY"'` every 10 min, then probe, then full pull).
Request budget: spot_1m + tide + gex_levels + greek_exp over ~1,000 weekdays since 2022-09-28 x 6 tickers = ~20k calls at 1 req/s = ~6 h; recents first so L6M lands in the first hour.

## 3. Scoring plan (starts the hour the data lands)
Features per 1-min bar (RTH): net gamma (sign of call+put gamma, OI/vol/dir variants), gamma per 1% move level, charm/vanna, distance of NQ-mapped spot to call wall / put wall / gamma_flip / gamma_magnet (SPX->NQ via NDX/QQQ rather than ES ratio: NQ-mapped level = level * NQ_price/index_price at the same minute; test both), Market Tide net premium slope and sign.
Uses: (a) chop-vs-trend regime flag (positive-gamma = chop) for T-WORKS B1 (best 5 and best 20 weeks must not lose: trend-week clause) and the LOT/SIGQ/REG dials; (b) levels as targets in front of a wall, stops behind one, zone HALF, near-zone take/hold; (c) entry skip/half and near-zone take/hold for K7, M7, U7, H7 in RTH (09:30-15:00 ET; Asia/London have no UW data).
Protocol: first-order screens on JN05W2 / JN05W2J / NOCUT trade lists (runs_rf) per book x RTH session, four windows as far as the history allows, bi-weekly WF, within-month permutation family null + forward-only placebo, report chance passes, behavioural scorecard a-e, trend-week clause first; exact for finalists via TP_ENGINE + tp_admit tag TOOLS. Output here by trial day 5 with a plain verdict: KEEP ($150/mo; live read would need the websocket channels gex:{TICKER} / market_tide in a Python sidecar + the daily gex-levels pull, and an NT8-readable feature file/port) or CANCEL.

## 4. Update for the 20:40Z ADVANCED order (offline work done while the key is not visible)
- Probe now also covers spot_exp_strike (v2 strike x expiry, daily), oi_strike (daily OI) and darkpool (path /api/darkpool/{ticker} UNVERIFIED: a 404 means look it up in llms.txt); day-1 verdict line goes to MORNING.md (append-only, so 'top' = newest line) and per-series depth is in /mnt/l2/l2vast/uw/probe.json.
- Pull plan: first 3 days; order = recents first, 1-minute series first (spot_1m, tide), then gex_levels (vol,oi), greek_exp, spot_strike, spot_exp_strike, oi_strike, darkpool; resumable (existing files skipped), 1 req/s until the real limit is measured (docs give none; Retry-After honoured).
- LIVE recorder code/th_uw/uw_live.py + live_watchdog.sh (pid /mnt/l2/l2vast/uw/live_watchdog.pid; recorder pid live_rec.pid; nice 15; disk guard 50 GB; backoff reconnect; key only from env, query-token auth wss://api.unusualwhales.com/socket?token=... per docs, never logged). Channels from the docs: gex:{T} (Unix-ms timestamp, price, gamma/delta/charm/vanna per 1% move _oi/_vol/_dir), gex_strike:{T}, gex_strike_expiry:{T}, market_tide (timestamp, net_volume, net_call_premium, net_put_premium, otm_* ), otm_market_tide; option_trades:{T} (channel assumed from UW naming, docs page not read). The docs pages do NOT give the join-message JSON: recorder sends {"channel": name, "msg_type": "join"} (UW examples) and logs the first server replies to uw_live/join_reply.log so a wrong format is visible at once; websockets library installed to /mnt/l2/l2vast/pylibs (root fs is nearly full). Output: forward_register/uw_live/<date>/<channel>.jsonl with recv_ns. Daily live-vs-history parity (live gex ticks vs the 1-min history for the same date) to be written (code/th_uw/uw_parity.py) once the first live day exists.
- Mapping to NQ (to state in every result): SPX levels x (NQ mid / SPX-index price at the same minute) [basis mapping]; NDX and QQQ levels mapped directly (NQ ~ NDX x basis, QQQ x ratio); compare both; no ES ratio unless SPX is what returns data.
- Stand-in design check on owned data (W-TL2: NQ options/ES options in /mnt/l2/l2vast/raw/NQ_opts, DS3_TOOLS_T2.md): the same feature builders (net gamma sign, distance to call/put wall, zero gamma) are written against that format first so UW data drops into the same scoring code; W-TL2's pipeline files t2_gamma.py / t2_feat.py are the template.
- Verdict due by day 20: keep $375 / drop to Basic $150 / cancel, with $/wk at the user's lots vs monthly cost + live path.

## 5. DAY 1 RESULT (probe 2026-11-12 ~20:40Z, key via bash -ic; raw: /mnt/l2/l2vast/uw/probe.json)
| series | resolution | history depth (200 vs 403 historic_data_access_missing) |
|---|---|---|
| spot-exposures (MM gamma/charm/vanna per 1% move, OI/vol/dir) SPX, SPY, QQQ | 1 row/min, ~11:30Z-21:00Z (incl. pre-market) | 2 YEARS INTRADAY (OK at 2024-11-12; 403 at 2023-11-13) |
| same, NDX | 1 row/min, ~14:30Z-21:00Z (+early 13:xx recently) | 2 YEARS INTRADAY |
| same, SPXW / NDXP | 0 rows | none |
| Market Tide (net call/put premium, net volume) | 1-min ticks | 2 YEARS INTRADAY (not 2022 as docs say) |
| gex-levels (call wall, put wall, gamma magnet, gamma flip) SPX SPY QQQ NDX | daily | 2 years |
| spot-exposures/strike | EOD snapshot for past dates | 2 years |
| spot-exposures/expiry-strike (v2) | daily | ~1 year (2y = 0 rows) |
| oi-per-strike | daily | 2 years |
| greek-exposure | series on last date (250 rows); 0 rows for date 1y/2y back | shape to check |
| dark pool prints | per print, 500/page (pagination) | SPY, QQQ yes; SPX/NDX 0 |
Live websocket: join format confirmed ({"channel": name, "msg_type": "join"} -> ["gex:SPX",{"response":{},"status":"ok"}]); recording gex:SPX/SPY/QQQ/NDX, gex_strike:SPX, market_tide, option_trades:SPX/NDX to autopilot/forward/uw_live/.
Pull status: spot_1m + tide for SPX/SPY/QQQ/NDX 2024-10-01..today (newest first) running at ~1 req/s with no rate-limit hit; secondary pulls chained after. Scoring starts when the 1-min files cover L6M (within the hour).
