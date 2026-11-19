# STATUS QUESTION 20261119_1823Z - what does the search cover, component by component? (REPORT ONLY)

From: Josh's chat assistant (coordinator). This is a question, not an order to change anything. Do NOT change any queue, priority, code, gate or study because of it. No engine time. One written answer.

Josh wants to know exactly what the current Asia / NY AM search covers. For each component below, state plainly: (a) is it VARIED in the big grid (how many values, examples), (b) is it tested only on the best books afterwards (which stage), or (c) NOT covered at all. If something is only partly covered, say which part. Do not round up: "not covered" is a fine answer.

1. Bar type (base candle): how many bar types / sizes per session, list the families.
2. Trigger (entry signal): how many trigger modules and parameter sets; list the families.
3. Stop / target: fixed brackets (which values) and non-fixed exits (which of the 68 recipes / 7 families are engine-runnable today, which are not).
4. Confluence: extra conditions that must line up before an entry (e.g. two or more signals agreeing, higher-timeframe agreement, momentum + level). Is any confluence tested as an ENTRY FILTER on top of a trigger? Which, where?
5. Level filters: supply / demand zones, session levels, VWAP, volume profile, order-book walls. Used as TRIGGERS (which modules) and / or as FILTERS on other triggers (which)?
6. Sizer: efficiency-ratio trend sizer and any other sizer (signal-quality, Calmar-type). Varied where?
7. Session and time window: which sessions, any time-of-day or no-trade windows varied?
8. Side: long-only / short-only / both: how is each cell's side set, and is every cell tested in all three?
9. Entry method: market on signal vs split entry / dip entry / order-book (L2) confirmation as the live books use. Varied or fixed?
10. In-trade management: early loss cut and early profit take (Trade Health rules). On new books: tested where?
11. Re-entry rules: cooldown after a cut, no re-chasing. Tested where?
12. Market-type filter: trend vs range regime gating of entries. Tested where?
13. Account-level protection: daily loss limit, day-done, stack cuts, locks, same-side cap. Fixed at today's settings or refitted for a new stack?
14. Refit schedule: is the 2-week refit / walk-forward of settings part of the evidence for new books?
15. Data used as triggers or confluence from OTHER instruments or feeds (ES, options flow, order book): what is in the grid?

Format: one table (component | varied in the grid | tested later on best books | not covered | note), then five lines: the biggest gaps in your own judgement. Put it in autopilot/SEARCH_COVERAGE.md and one LEAD NOTE saying it is posted. Again: report only; change nothing.
