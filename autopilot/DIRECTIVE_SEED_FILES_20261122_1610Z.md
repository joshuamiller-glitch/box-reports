# seed-files-first-for-tonight-build (plumbing order, 2026-11-22 ~16:10Z)

Written by the relay (Claude), not typed by Josh. Plumbing / information only: no new tests, no gate or rule change.

Context: Josh asked (11:02 ET) whether Asia D8 can go on SIM around the Globex open tonight (23:00Z). The port of the five pinned Asia books (TL3_ALN_AS_STKd8106b26ef) is blocked on start-up values, not on research. Please give item 5 of order 1552Z its own agent NOW, beside items 1-4 (it needs almost no compute), in this order:

1. By ~18:00Z, one page autopilot/D8_SEED_ASIA_20261122.md (fenced CSV blocks), for the session that opens 2026-11-22 18:00 ET, per pinned book, every value the engine holds at session start that the live code cannot get from the first print of the session. At least:
   - Lb0e6dfa3 / all: the daily scale factors in force for that session (s_vol, s_n, s_rng) and the resulting bar thresholds / brick sizes actually used.
   - L6b373671: the pivot lines (name, price) and u at session start; the last 100 bar ranges if u needs them.
   - L92a90948: tick-bar threshold, S0, EMA200(d^2) state, q, the last 60 dq, last state.
   - L578701ed: the last 200 x values (or say that the window restarts each session).
   - L385f4f2e.J502: volume-bar threshold, Wilder RSI14 state (avg gain / avg loss, last close), the last 50 bar ranges for u, ema_stack state, PRF1_VAL, OPENS / FIB / SESSRUN anchor prices, and the ES 5-min and YM 15-min z-score windows.
   If a value truly restarts each session, say "restarts" so the port does the same.
2. For each of those values, one line on how the engine derives it from raw data (window, session boundaries, which contract), so the NT8 code can compute it itself from tomorrow and the seed page becomes a daily cross-check. Then publish the same page daily before 22:00Z.
3. Items 5b, 5c, 5d of order 1552Z (vsig minimum periods + edge definition; crossed / bid == ask / empty book levels; J502 identity DIFF at 2 / 4 lots) in two lines each on the same page.
4. When the Asia joint all-layers verdict is final, put the chosen settings for 1, 2 and 4 lots into AUTO:LAYERS as plain key = value lines (panel defaults), with the bare row beside.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
