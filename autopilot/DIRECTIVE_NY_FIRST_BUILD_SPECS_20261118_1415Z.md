# 1415Z — NY FIRST: engine verdict + BUILD SPECS for NY AM / NY PM by 19:00Z (Josh wants new NY books coded before Globex opens at 23:00Z)

From: Josh's chat assistant (relay). Research orders only; no spend; nothing here touches the execution server or a live chart. (This file is also the live test of wake_watchdog.py: log "WATCHDOG fired: A" and the time you started reading it.)

CHANGE TO THE 1333Z FUNNEL: same five stages, but NY AM and NY PM go FIRST and four hours earlier, because the chat assistant needs the afternoon to code. London and Asia keep the 23:00Z deadline.

NEW TIMES FOR NY AM + NY PM:
- stage 1 look-ahead gate: 15:00Z (unchanged; construction check already PASSED 13:30Z - finish the fill-delay test +4/+14/+29 s)
- stage 2 shortlist (12 per session): 15:15Z
- stage 3 trust + nulls: 16:15Z
- stage 4 exits + layers (fast replay): 17:30Z
- stage 5 exact engine, best 3 per NY session: start the engine sets for the provisional top 6 per NY session NOW in parallel (do not wait for stages 3-4; drop the ones that fail later) so engine rows land by 19:00Z. Give NY new-book engine sets priority over P7L, SWA/SWB and ME queues; near-target controls keep 8 slots.

ENGINE QUESTION PER FINALIST (drawdown first): (a) ADDED to the live stack as a new book at 1 base lot; (b) REPLACING the weakest live book of that session (NY AM: K7, P7, M7 each tried; NY PM: K7); last 6 months, last 3 months, each prior year; stack ulcer and worst week change, then mean $/week; daily P&L correlation with the live books of that session; 10 controls now, 30 by tomorrow. Label: BUILD-READY / NEEDS MORE / DROPPED.

BUILD SPEC PAGE (autopilot/NEW_BOOK_BUILD_SPECS.md, first version 16:30Z for the provisional top 6 per NY session, final 19:00Z): for each finalist, everything needed to code it in NinjaScript EXACTLY as tested, no gaps:
1. BAR: type, size, and the exact construction rule in prints (when a bar closes, what the first bar of a session does, how the size is set each day if it scales, session-reset times in ET). Say if NT8 has it natively (Second, Volume, Tick, Range) or needs a custom BarsType. PREFER, among near-equal finalists, the one on a native NT8 bar: a native-bar book can be coded today; a Kagi / point-and-figure / dollar / delta book needs a custom bar type first.
2. TRIGGER: the level definition step by step (how the zone / level / line is found, lookbacks, tolerances, what invalidates it, how many levels are live at once, first-touch rule), the entry event (break / reject / retest / false break / limit) with every parameter value, long / short / both, and the exact code path (file + function) in the harness.
3. ORDER: entry order type and timing as tested (first print after the confirming print + measured slippage), bracket in POINTS (stop, target) or the exit recipe with all values, flat time, one position at a time or stacking, re-entry rule.
4. SESSION WINDOW in ET, and any no-trade times used.
5. LAYERS that were ON in the engine run and their settings (so the build can map them to the D7 layer names), and which D7 layers were NOT applied.
6. DATA: anything beyond NQ trades (order book, tape side, another market).
7. Three worked example trades from the last month (date, time ET, level price, entry, exit, P&L) so the build can be checked against them on a chart.

If, by 16:30Z, no NY finalist on a native bar is within reach of the best custom-bar finalist, say so and name the single simplest custom bar that carries the most finalists (so one BarsType covers several books).

CORES: both machines 90%+. Reply in MORNING.md: accepted, the provisional top 6 per NY session going to the engine now, and whether 19:00Z holds.
