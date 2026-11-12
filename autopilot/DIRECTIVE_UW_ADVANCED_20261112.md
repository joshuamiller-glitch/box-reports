# ORDER (user, 2026-11-12 20:40Z) — UNUSUAL WHALES, one month of API Advanced ($375), bought to test thoroughly (supersedes the 20:35Z 7-day Basic trial order). Key is in env var UW_API_KEY on the box — never printed, logged or written to a file. Read their API docs first; do not guess endpoints.
DAY 1 (report at the top of MORNING.md): what the plan really returns and at what resolution and depth of history — 1-minute SPX market-maker exposure, GEX / charm / vanna / delta by strike and expiry (SPX, SPY, QQQ, NDX), Market Tide and net premium ticks, dark pool prints, daily open interest. Say plainly which series have 2 years of INTRADAY history and which are daily only or recent only.
PULL everything available inside the limits to /mnt/l2/l2vast/uw/ in the first 3 days, so the history is owned whatever happens to the subscription.
RECORD LIVE from day 1 by WebSocket (SPX exposure stream, option trades summary, Market Tide) to forward_register/uw_live/ — the forward test and a check that live matches the history.
SCORE, exact for finalists, one set per job, four windows as far as the history allows, WF, placebo and family null, scorecard a-e, trend-week clause, on JN05W2 / JN05W2J and the NOCUT bases:
 (a) REGIME: dealer long-gamma vs short-gamma (level and 1-minute change) as the chop-vs-trend flag for the loss cut, the profit rules, the dials and "press the trend day";
 (b) LEVELS: call wall, put wall, zero gamma, largest same-day-expiry strikes mapped to NQ (state the mapping) for targets in front, stops behind, zone HALF, retargets;
 (c) INTRADAY FLOW: Market Tide / net premium slope and flips as entry skip / half, near-zone take / hold, early cut — K7, M7, U7, H7 in RTH, per session;
 (d) charm / vanna into the close and around expiry as a time-of-day dial;
 (e) dark pool prints and unusual flow in the top NQ weights as a shock / support flag (expect little; report it anyway).
Then JOINT with the v1.9 survivors. Recents first; rule 2a tolerance.
DELIVER DS3_UW.md: day 1, day 3, then every 2 days; by day 20 a plain verdict — keep at $375, drop to Basic at $150 (if the 1-minute series adds nothing over what Basic has), or cancel — with $ per week at the user's lots against the monthly cost, and the live path (which stream, update rate, what D7 or a sidecar must read).
