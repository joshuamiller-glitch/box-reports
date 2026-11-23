# ORDER (research only): time-of-day entry blocks, EVERY 30-minute window, all four D8 sessions
**Josh's words are quoted; everything marked (relay) is the relay's reading. Research only: nothing live, no gate or rule change, no spend, no data deleted.**

Josh, 23 Nov 10:44 MT: "ok so we tested blocking like 9:30-10am and 3pm - 4pm - things like that?"
Relay answered: not on D8 (only on D7). Offered a test. Josh, 10:45 MT: "yes please usually that's the easiest way to lower DD - you are checking ALL 30 min windows?"

## What to run (relay)
1. New layer family TW (time window): NO NEW ENTRY while the order time falls inside the window; open trades are untouched (bracket and layers manage them as today).
2. EVERY 30-minute window of each session, on the session clock in ET (so it follows daylight time):
   - Asia 18:00-02:00 ET: 16 windows. London 02:00-08:30: 13. NY AM 09:30-12:00: 5. NY PM 12:00-16:00: 8.
3. Screen, per book AND for the whole stack: each single window blocked alone. Report every window, nothing dropped: per book and per stack, L6M with L3M beside, $/wk, max drawdown, worst week, worst day, trades removed, and the same for the three prior years.
4. Then joins: adjacent windows merged (for example first 60 minutes, last 60 / 90 minutes) and the best two or three separate windows together, per book and per stack.
5. Base and size: the delivered 2-lot picks (Asia BF2_JT19 or its replacement from the re-run, NY AM BF2_JT68, London bare, NY PM bare or its joint pick when landed). 2 lots per book only (order 1840Z).
6. Verdict the approved way for fitted settings: pick on recent, walk-forward at least 58%, prior years in the not-a-disaster band, best-of-many null 4 of 5. The null matters here: 42 windows x many books is a lot of tries, say plainly how many windows would look good by luck.
7. Drawdown first. The deliverable is the best TW setting per session (per book where it differs), with the engine key and exact clock times so the relay can code it; "none" is a reference row only.
8. The top TW candidates then enter the next joint refit with the other layers (not fitted on a frozen base as the final word).

## Rank / capacity (relay)
Behind the ordered 2-lot fits already running (Asia re-run, NY PM joint), level with the DL / session-end / carry-over screens. Machines stay full; this must not stall the first looks.

Post: `autopilot/D8_TIME_WINDOWS.md`, with a count and ETA line in MORNING.md when queued.
