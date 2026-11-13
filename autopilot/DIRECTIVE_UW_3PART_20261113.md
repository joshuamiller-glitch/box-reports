USER ORDER (one paste, three parts) — 2026-11-13. Research only: nothing on the execution server or any live chart changes. No new spend. UW key only via env var UW_API_KEY.

PART 1 — QUEUE ORDER. The user is not satisfied with UW results so far. Front of the queue, in this order:
(1) FLOW ALERTS (the data landed 22:57Z) as entry triggers and as filters on the live books: premium size, sweep vs block, opening vs closing, ask-side share, DTE bucket (0 / 1-5 / 6+), repeated hits on the same strike, call vs put, for QQQ SPY SPX NDX IWM and NVDA AAPL MSFT AMZN META GOOGL TSLA; on NQ and ES; follow and fade both tested; 1 / 5 / 15 / 60 min horizons; session by session.
(2) MEGACAP OPTION FLOW: megacap net premium and flow bursts leading NQ at 1 / 5 / 15 min, single names and the seven summed.
(3) PART 2 below.
Behind them: RTY/YM, pairs, metals and oil reruns. STOP spending cores on further dealer-exposure direction screens (gamma / vanna / charm as skip, press or entry direction): that family is closed unless a new input arrives.

PART 2 — T-RANGEUSE: PUT THE RANGE FORECAST ON D7's DIALS. Exact engine, JN05W2 base, all layers ON. Use the walk-forward range forecast from T-UWREGIME, known only as of each reading time. Score every dial with three forecasts: (a) ATR only, (b) ATR + IV term, (c) full UW model. The question on each dial is the gain of (b) and (c) over (a), not over "no rule". Dials, each per book and per session:
1. TARGET ONLY scaled by forecast range (x0.75 / x1 / x1.25 / x1.5 by tercile, and continuous); stop unchanged.
2. CONSTANT DOLLAR RISK: stop in points scaled with forecast range, lots scaled inversely so the dollar loss at the stop is fixed; also the half version.
3. CUT LEVELS in forecast-range units: the flat cuts (K7 -45, P7 -42) and the pct thresholds of every loss rule.
4. RANGE USED UP: remaining = forecast range minus range printed so far this session. (i) skip entries whose target distance exceeds k x remaining; (ii) take profit early when unrealized >= k x remaining; (iii) shrink the target to the remaining range. k = 0.5 / 0.75 / 1 / 1.25.
5. REPLACE atr_rel in the live layers (ATR-skip, REG half-size, SIGQ) with the forecast, thresholds re-fitted.
6. ENTRY DISTANCE: pullback depth, split-add dip, Keltner band multiple and chase_k limit scaled by forecast range.
7. LOCK LEVELS: the pct thresholds of the profit locks scaled by forecast range.
8. JOINT: top 3 settings per dial varied together, drawdown first.

PART 3 — EVENT CALENDAR. Add a macro calendar to the no-UW benchmark: FOMC decision and minutes, CPI, PPI, NFP, PCE, GDP, ISM, retail sales, Treasury auctions, Fed chair speeches, megacap earnings dates, back to 2024-10-01 with release times. Free public sources only. Add VIX and the VIX futures curve if a free daily history exists. Re-run the forecast test with benchmark = ATR + IV level + day of week + event flags and report how much gain survives for iv_term, flip, gamma, charm, vanna and tide; relabel any input whose gain disappears as "calendar proxy". Score the PART 2 dials on event days and non-event days separately.

RULES FOR ALL PARTS. Session by session, never pooled only. L3M and L6M from today first, then HOLD and PREUW; tolerant gate; a result must hold in BOTH the recent and the older window to be called a lead. Drawdown first (max DD, worst week, full stops/wk, best-5 weeks kept, winning weeks turned losing), then mean. Measured fills. Walk-forward every 2 weeks. Placebo (tags or events shifted 11 / 23 / 37 days) and the family null beside every number. New-book results are reported from the exact-engine injection hook, not the standalone harness, since the live gates cut standalone profit by about 85%. "Nothing" is not a deliverable: deliver the best per session or per dial with its evidence and say plainly how strong it is.

REPORTS. DS3_UW_FLOWALERTS.md, DS3_UW_MEGAFLOW.md, DS3_RANGEUSE.md: first page of each within 3 hours, updates every 3 hours, a plain one-line verdict at the top of each. If any part cannot start, say why in MORNING.md within 15 minutes.
