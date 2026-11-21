# 0037Z Sat: debug tables for the two Asia stack books (written by the relay (Claude), not typed by Josh)

Documentation only, no new tests, low priority (must not take engine slots; it is W-D8SPEC table work on box 1). The Asia main final has been L7c368a4f + La010c3eb on pool 22, 23 and 24. It may still change after the fits; the tables are for starting the NT8 port early. If the stack changes I will ask for the new book.

Same format and care as D8_TRIGDEBUG_L488784d8.md / D8_TRIGDEBUG_L7cc56d99.md (exact definitions from the code first, then per-bar rows, recompute checked against the module over the whole series, history-needed paragraph). Trading date 20261110, Asia session plus 300 bars before it.

1. **autopilot/D8_TRIGDEBUG_L7c368a4f.md**: time_m_5 bars + trig_pullback_ema depth {"len": 10, "w": 0.5}. Say exactly: how the 5-minute bar is stamped and when it is known (epoch-aligned? print on the boundary?), empty buckets, session/roll handling; EMA seed and resets; every intermediate value per bar; the event rule; event time; the stop/target (plain 60/60) and the session-end flat time.
2. **autopilot/D8_TRIGDEBUG_La010c3eb.md**: vol_500 bars on the _CANC print rule + trig_trend_libstack ema_stack {"set": "10-20-50"}, both sides as engine-run. Say exactly: the day's volume threshold (500 x s_vol with the value for 20261110), which print closes the bar and whether overflow volume carries, session resets; EMA seeds/resets; per-bar values; event rule (what "stack" means, edge or level, both sides); event time.
3. **autopilot/D8_VECTORS_CANC_La010c3eb.md**: the vol_500 _CANC bars of the Asia session 20261110 (known time, o, h, l, c, volume, delta), like the earlier vector files, so I can check the NT8 bar builder on Josh's own tick export first.

4. **Check, one line (W-GRIDOPS):** the 00:30Z heartbeat still reads canc bulk 749/3668 and Asia first-look cells 577/1239, both unchanged since 00:00Z, and the exit stage-1 that held the slots was due to drain by 00:15-00:30Z. How many slots does the D8 canonical class have now, and what is running in the rest? If it is still 0, give it the slots as the lead's 00:01Z countdown planned.
