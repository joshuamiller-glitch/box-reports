# DS3_DEEPEN_OUTSIDE (T-DEEPEN Part 4, QUOTE ONLY, W-CH3)

**VERDICT: no proxy supports a purchase. The free megacap/index proxy does not forecast CHOP under the W-CH1 fixed label, so the Nasdaq-100 minute bars ($21.69, EQUS.MINI) are not justified; ZN and 6E 1-minute history cost $0.00 on the plan (no purchase needed, usable when a Part 3 intermarket test wants it); DX costs $10.32 and 6E already stands in for it; headline feed and NYSE internals: no proxy to justify. Nothing bought, no PASS claimed.**

## 1. Nasdaq-100 components (update with the fixed label, DECISIONS sha afc0dbedcbd15899, /mnt/l2/l2vast/_chop/f1/label_sessions.parquet)
Re-ran the megacap proxy (7 names: avg pairwise corr, dispersion, up-share, NQ-vs-basket relative strength) with the W-CH1 chop label per session (nyam, nypm), walk-forward every 14 days, shifted-day placebos (code/th_chop3/b3_test_f1.py, results /mnt/l2/l2vast/_chop/b3/proxy_results_f1.csv). AUC gain of controls+proxy over controls (controls = yesterday chop, ATR, own efficiency so far, NQ/ES/RTY/YM corr and dispersion):
| clock | L1M | L3M | L6M | older | all OOS |
|---|---|---|---|---|---|
| nyam@30 | +0.03 | -0.02 | +0.01 | -0.01 | -0.01 |
| nypm@0 | -0.01 | +0.01 | +0.01 | -0.03 | -0.02 |
| nypm@30 | +0.01 | -0.02 | -0.02 | -0.01 | -0.01 |
All within noise (placebos match or beat in most windows; L1M/L3M are 23/65 sessions). This agrees with W-CH1's own input table (megacap:breadth/corr forecast one session each at +0.04..+0.07, disp and er none). The earlier own-label run showed the same null (one weak nypm@30 +0.035). So the free proxy captures what a 100-name measure could add, as far as 7 names can say; it is a bound, not a proof.
Cost options (Databento metadata.get_cost, ohlcv-1m, 101 names, 2023-04-01..2026-11-14; none at $0 on this plan): EQUS.MINI $21.69 (consolidated, includes volume; yearly 4.40/5.96/6.08/5.25); XNAS.ITCH $27.67 (Nasdaq prints only); DBEQ.BASIC $95.90; XNAS.BASIC $21.35 but only from 2024-07. Top 20 / top 30 on EQUS.MINI: $4.95 / $7.18. RTH-only saves under 10 percent. Massive (Polygon) Stocks Advanced $199/month. Ticker list and caveats in DS3_CHOP_BREADTH.md (list must be verified point-in-time before any buy).
Part 3 item it would improve: intermarket confirmation (6; megacap/semis leadership) and A-plus score (8). Current stand-in: UW megacap 1-minute prices (7 names), ES/RTY/YM.
Exact purchase ask: NONE (no proxy supports it). If the user wants it as an untested-hope buy: EQUS.MINI ohlcv-1m, the 101 names, 2023-04-01..2026-11-14, $21.69.

## 2. ZN and DX (or 6E), 1-minute history from 2023-04-01 (get_cost / get_record_count, nothing downloaded)
| item | dataset / symbol | cost | records |
|---|---|---|---|
| ZN front month | GLBX.MDP3, ZN.c.0, ohlcv-1m | $0.00 | 955,440 |
| 6E front month | GLBX.MDP3, 6E.c.0, ohlcv-1m | $0.00 | 459,983 |
| ZN + 6E + ZB | GLBX.MDP3, ohlcv-1m | $0.00 | 2,278,946 |
| DX front month (ICE US dollar index) | IFUS.IMPACT, DX.c.0, ohlcv-1m | $10.32 | 395,634 |
| DX all expiries | IFUS.IMPACT, DX.FUT parent | $28.97 | 1,110,754 |
CME futures are covered by the plan at $0.00 (so no purchase approval is needed for ZN/6E; the pull itself is only disk). Daily ZN/6E already exist on the box (ds3_daily), and ZN/6E were already studied as standalone instruments (T-INSTR-2), not as confirmation inputs. DX adds little over 6E (EUR is about 57 percent of the dollar index), so DX is not worth $10.32 unless 6E fails and the dollar leg shows promise.
Free proxy now: ES/RTY/YM minute bars, VIX, calendar. Part 3 item improved: intermarket confirmation (6), clock/calendar (7, rate-event days), A-plus score (8). Ask: none required; recommend pulling ZN.c.0 and 6E.c.0 ohlcv-1m ($0.00) when the Part 3 intermarket test is built, after the user's OK because it is a download.

## 3. Real-time headline feed with history (event shock flag, quiet-day flag)
Public-price facts I could confirm without signup: Massive (Polygon) Benzinga news dataset, "real-time financial news and analyst ratings", $99/month per dataset (massive.com/pricing). Alpaca historical + real-time news API (docs confirm a symbol/time-range news endpoint with WebSocket real-time; source field shows the feed; price and history depth not stated on the docs page I could read, so unverified). Finnhub: its pricing page returned no plan figures to me (unverified). I did not verify any other vendor price; not claimed. Treat $99/month as the only confirmed price.
Free proxy now: economic calendar (DS3_EVENTCAL), UW flow alerts, VIX, megacap proxy, range forecast. A scheduled-release calendar already captures most shock days; the unscheduled-headline flag is what a feed adds. Part 3 item improved: clock/calendar (7) and management (9, flatten before a release). Ask: none; no proxy yet tests an unscheduled-headline flag, so a feed is not supported by evidence (test first with the free calendar's largest-move days).

## 4. Real-time NYSE internals
Not quoted: DS3_TICK.md found no TICK use passing, so by the order nothing to quote. Ask: none.

All quotes logged in MORNING.md. Files: code/th_chop3/b3_quote.py, b3_quote2.py; /mnt/l2/l2vast/_chop/b3/quotes.json, quotes2.json.
