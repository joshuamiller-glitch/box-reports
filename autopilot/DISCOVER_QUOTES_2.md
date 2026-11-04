# DISCOVER_QUOTES_2 (DQ, 2026-11-04) - metadata-only quotes, NOTHING bought or downloaded
Window 2023-04-01..2026-10-31 unless stated. Budget remaining ~$712; user must OK any pull. Scripts: outputs/l2vast/ds3/code/discover/dq_q3a.py, dq_q3b.py, dq_q3c.py (+ dq_q3b.json, dq_q3c.json). All quote calls succeeded, so the licence covers quoting/buying from every dataset below (no licence errors).

## (1) Equities: NVDA AAPL MSFT AMZN GOOGL META AVGO TSLA COST NFLX + QQQ (11 symbols)
Coverage: EQUS.MINI and DBEQ.BASIC from 2023-03-28 (full window OK); XNAS.ITCH from 2018-05; XNAS.BASIC and EQUS.SUMMARY only from 2024-07-01 (SUMMARY is ohlcv-1d only). RTH sub-selection works (13:30-20:00 UTC in EDT; one request per day, shift by 1 h in EST). RTH costs are 4 sample weeks (2023-10, 2024-10, 2025-10, 2026-10) x 187 weeks; +/-10%. ohlcv-1m is exact for the full window, all hours (pre/post included).
| dataset | ohlcv-1m (exact, all hours) | ohlcv-1s RTH (scaled; ~rec) | trades RTH (scaled; ~rec) | note |
|---|---|---|---|---|
| EQUS.MINI | $2.93 (4.68M rec, 0.26 GB) | ~$44 (71M, ~4.0 GB) | ~$57 (214M, ~10 GB) | consolidated-style, cheapest adequate |
| DBEQ.BASIC | $15.52 (8.50M, 0.48 GB) | ~$121 (66M) | ~$101 (141M) | |
| XNAS.ITCH | $4.78 (7.63M, 0.43 GB) | ~$78 (124M) | ~$303 (1.13B, ~54 GB) | Nasdaq-only prints; tick-level + full depth available |
| XNAS.BASIC | $3.55 (since 2024-07 only) | ~$94 (since 2024-07) | ~$790 (since 2024-07) | too short and pricey |
Cheapest adequate = **EQUS.MINI** (full window, all schemas). Per-day RTH bars of 1-s = ~$44 for all 11 names; 1-m is $2.93.

## (2) Volatility: CFE VX (dataset XCBF.PITCH, 2018-11..now, all schemas available)
Priced much higher per GB than CME. Continuous `VX.v.0`/`VX.c.0` identical here.
| item (window) | records | GB | USD |
|---|---|---|---|
| VX.v.0 front only ohlcv-1m, full | 1.25M | 0.07 | **$162.55** |
| VX.v.0 ohlcv-1m, last 12 mo (2025-11..2026-10) | 368k | 0.02 | $48.02 |
| VX.v.0 ohlcv-1m, last 6 mo | 172k | 0.01 | $22.39 |
| VX.v.0 + v.1 (front two) ohlcv-1m, full | 2.38M | 0.13 | $309.92 |
| VX.v.0 ohlcv-1s full / L12M / L6M | 6.38M/1.83M/0.74M | 0.36/0.10/0.04 | $831 / $238 / $96 |
| VX.v.0 trades full / L12M / L6M | 26.4M/7.5M/2.9M | 1.27/0.36/0.14 | $1,768 / $503 / $198 |
| VX.v.0 tbbo full / L12M / L6M | 26.4M/7.5M/2.9M | 2.11/0.60/0.24 | $2,947 / $838 / $329 |
| VX all months (VX.FUT) ohlcv-1m / 1s / trades, full | 6.9M/22.3M/74.1M | 0.39/1.25/3.56 | $903 / $2,903 / $4,971 |
| VX.v.0 ohlcv-1d, full | 2.2k | ~0 | **$1.05** |
VIX index: NOT available (VIX/$VIX/SPX/NDX/$NDX all fail symbology on XCBF.PITCH, XNAS.ITCH, DBEQ.BASIC; no index-feed dataset in the licence list). VX front future (or VX daily $1.05) is the proxy.

## (3) NDX / QQQ options
NDX index level: not available (above). QQQ options (OPRA.PILLAR, parent QQQ.OPT), one day 2026-10-12: ohlcv-1m $4.48 (306k rec), cbbo-1m $0.61 (4.1M rec, 0.33 GB), trades $11.73 (937k rec). Full-window ohlcv-1d = $685 (21.9M rec). NOT cheap: only a short sample is reasonable (e.g. 20 days cbbo-1m ~$12-15).

## (4) NQ MBO sample (GLBX.MDP3, NQ.v.0), 09:25-10:30 ET, 20 days 2026-10-05..10-30
mbo: 104.8M records, 5.87 GB, **$9.84** (cheap; ~$0.49/day). Same day full 24 h: 20.7M rec, 1.16 GB, $1.94. Comparison mbp-1 same 1-h window one day: $0.30. Scaled: a full 3.5-year 09:25-10:30 mbo book (~930 days) = ~$450; so MBO can be piloted for $10-20 and extended only if it shows edge. (Note: mid-day starts include a synthetic book snapshot.)

## (5) YM (ES/RTY 1-s derivable from owned ticks)
YM ohlcv-1s full: 22.9M rec, 1.29 GB, **$83.78**. YM trades full: 70.9M rec, 3.40 GB, $88.71. YM ohlcv-1m full $4.56 (already owned to 10-16).

## RECOMMENDED SET, ranked by research value, under $300
1. Equity leaders (EQUS.MINI): ohlcv-1m all hours $2.93 + ohlcv-1s RTH ~$44 + trades RTH ~$57 = **~$104** (without trades: ~$47).
2. VX: front-month ohlcv-1m full $162.55 + VX daily $1.05 = **$163.6** (cheaper alternative: L12M 1-min $48 + daily $1 = $49; add 1-s L6M $96 only if 1-min lead-lag shows edge).
3. NQ MBO pilot (20 days 09:25-10:30) **$9.84**.
Total of 1+2+3 = **~$278** (with the cheaper VX L12M alternative: ~$164, leaving room for item 4).
4. (optional, if VX L12M chosen) YM ohlcv-1s $83.78 -> total ~$247. Skip YM trades ($88.7).
Not recommended: VX two-month 1-min ($310), any VX 1-s/trades/tbbo beyond L6M, XNAS.BASIC, DBEQ.BASIC, QQQ options beyond a sample, anything for VIX/NDX index (unavailable).
