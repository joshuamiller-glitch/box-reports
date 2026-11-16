INBOX ORDER 20261116_2105Z_new-data-candidates-quotes-and-pilots (research only)
QUOTES ONLY. Buy nothing. Log every quote; the user approves any spend by
pasting to you directly. Runs on server 2 behind T-REBUILD stages 0/5;
the free pilots (items 5-7) can start now.

The user wants new outside data tested, chosen by what has actually shown
signal here: order flow at the entry second, other markets turning during
a trade, and range forecasting. Chart indicators and options "direction"
have not. Rank and scope these seven. For each: a Databento (or source)
cost quote for a ONE-MONTH pilot and for the full 2023-04..now history,
whether D7 could get it live and at what monthly cost, and a one-page
test design. Validation standard as in orders 1954Z / 2000Z.

1. MEGACAP CASH TAPE (top candidate). NVDA MSFT AAPL AMZN GOOGL META AVGO
   TSLA on Nasdaq TotalView-ITCH (Databento XNAS.ITCH): trades + top of
   book first (cheap), order-by-order second. Readings at the D7 entry
   second and in-trade: weighted megacap return over 1/5/15/60 s vs NQ
   (lead or lag), breadth (how many of 8 moving with the trade),
   aggressor imbalance and tape speed in the megacaps, one stock
   dragging the index. RTH and extended hours separately.
2. AUCTION IMBALANCE. Nasdaq opening and closing cross imbalance messages
   (XNAS.ITCH imbalance schema; NYSE imbalance if quoted): size and side
   of the paired / imbalance shares from 09:25 and from 15:50 ET. Test
   against O7 (opening drive), all books 09:30-10:00, and NY PM into the
   close.
3. ES ORDER-BY-ORDER. The L3 arrival-imbalance reading is the strongest
   single condition found, on NQ only. Quote ES MBO for a 3-month pilot;
   test the same reading on ES at NQ entry seconds, and ES-minus-NQ
   divergence.
4. INTRADAY DEALER GAMMA, 0DTE. A real-time gamma API with history
   (candidates: GEXBot, FlashAlpha; SpotGamma has no public API). The QQQ
   gamma press was +937..1,656 $/wk DD neutral on the old base. Test:
   distance to the largest gamma strike, sign of net gamma, and change in
   the 0DTE profile during the session, as range / target / exit inputs,
   not as direction. Quote history depth and price; check the vendor's
   history is point-in-time (not recomputed).
5. FREE PILOT - MACRO RELEASE SURPRISE. Timestamped actual vs consensus
   for US releases 2023-now (BLS / BEA / Fed calendars are free; consensus
   needs a source: quote Benzinga calendar API, Trading Economics). Test:
   stand-down / size windows around releases by surprise size, and the
   first 5 minutes after. The event calendar study used the calendar
   only, never the surprise.
6. FREE PILOT - ASIA DRIVERS. For the Asia session (33k of the 74k HOLD
   drawdown): USDJPY (6J), Nikkei (NKD / NIY), Hang Seng and China A50
   where free 1-s or 1-min exists, and BTC perpetual (free exchange
   data) as a 24-hour risk proxy. Same readings as the other-markets
   work: lead / lag at entry and turning against an open trade.
7. FREE PILOT - VOLATILITY TAPE. VX futures front two months and the VIX
   index intraday if a free or cheap source exists (state it): VX moving
   against NQ's direction at entry and in-trade, and VX term slope as a
   chop / trend-day input.

Deliver autopilot/DS3_NEW_DATA_CANDIDATES.md by 03:00Z: one table (item,
pilot cost, full cost, live cost, D7 can compute live yes/no, expected
overlap with what we already own), then the test designs. Start pilots 5,
6, 7 on whatever is free immediately and report first tables by 12:00Z.
