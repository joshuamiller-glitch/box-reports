# ORDER (research only): news-release rules on D8, entries AND open trades
**Josh's words are quoted; lines marked (relay) are the relay's reading. Research only: nothing live, no gate or rule change, no spend, no data deleted.**

Josh, 23 Nov 11:20 MT: "we aren't blocking huge news releases? like FED days ? CPI, PPI ? aren't those candles HUGE?"
Josh, 11:21 MT (after the relay offered the test): "yes my concern there is if in open trade it could get taken for a huge ride - i don't thikn a good retail trader would trade it  -YES"

Relay note: the earlier event-window study (DS3_EVENT_WINDOWS.md) was on the D7 base. Nothing of the kind has been run on the D8 books. Calendar: /mnt/l2/l2vast/_calendar/events.csv (say plainly from which date it has events and what the earlier months are scored as).

## What to run (relay), on the delivered 2-lot picks, 2 lots per book only
New layer family NW (news window), per release type (CPI, PPI, NFP, PCE, GDP, retail sales, ISM, JOLTS and other 10:00 ET releases in the calendar, FOMC decision, FOMC press conference, FOMC minutes, chair speeches), per session and per book:
1. ENTRY BLOCK: no new entry from A minutes before to B minutes after the release. A in {2, 5, 15}, B in {5, 15, 30, 60}.
2. OPEN-TRADE RULE (Josh's concern, the main item): a trade open at release minus A is (a) closed at market at release minus A, or (b) kept with its stop moved to break-even if in profit, else closed, or (c) left alone (reference row). Same A values.
3. FED DAYS (decision 14:00 ET, press 14:30 ET), NY PM: entry block + open-trade rule as above, and two wider settings: no NY PM entries from 13:55 ET to the bell with open trades closed at 13:55; NY PM skipped for the whole afternoon.
4. 08:30 ET RELEASES and the London book: London is flattened at 08:30:01 ET, into the release. Test flattening London at 08:25 and at 08:28 on release days (and a London entry block from 08:00 on those days) against today's rule.
5. Report every row, nothing dropped: per release type and pooled, L6M with L3M beside, $/wk, max drawdown, worst week, worst day, trades removed or closed early, and separately the WORST SINGLE TRADE and worst day on release days with and without the rule (that is what Josh is asking about). Prior years as far as the calendar goes.
6. Verdict the approved way for fitted settings (pick on recent, walk-forward at least 58%, prior years not a disaster, best-of-many null 4 of 5; say how many settings would look good by luck). Drawdown first. Deliverable = the best NW setting per session with exact clock rules the relay can code; "none" is a reference row only. The top settings then enter the next joint refit.
7. Fills: the close-before-release exits are market orders on the measured basis at 2 lots, like every other exit.

## Rank (relay)
Behind the NY PM 2-lot joint and the Asia re-run; level with the time-window (TW) screen. Machines stay full. Post `autopilot/D8_NEWS_WINDOWS.md` and a count + ETA line in MORNING.md when queued.
