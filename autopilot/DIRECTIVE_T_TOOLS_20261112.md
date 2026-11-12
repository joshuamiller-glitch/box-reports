# T-TOOLS (user, 2026-11-12 19:30Z) — new data and tools for profit- and loss-side protection. SPEND AUTHORITY for this order only: up to $1,500, bought history / one-month trials only, every purchase logged in MORNING.md before download; no recurring subscription without the user. Test on history first; a tool is recommended only if it beats its placebo AND its monthly cost. Bases JN05W2 / JN05W2J and the NOCUT bases (the live state cut is not firing). Uses for every feature: loss cut, early cut, near-zone take / hold, entry skip / half, regime flag, target / stop placement. Per book x session, recents first, exact for finalists, one set per job, scorecard a-e, trend-week clause. Rows in DS3_TOOLS.md, first page 2026-11-13 06:00Z, every 4 h. No execution / latency work in this order: NT8 already runs on a CME-colocated server, and order-handling settings belong to T-SMART B2 / B3.

T1. MBO (order-by-order): buy NQ MBO history (L3M first, quote L6M) and build:
 (a) queue position and fill probability of OUR resting orders -> re-score staggered targets, passive entries and work-the-cut with the real queue;
 (b) true icebergs (refills by order id at one price) ahead of / behind the trade;
 (c) stop runs (aggressive sweep through a prior swing with resting stop orders triggering);
 (d) who pulled: one large order vs many small, cancel vs modify-away, order age;
 (e) large single resting orders ahead / behind (>= N lots) and whether they survive;
 (f) flicker / spoof rate.
 Compare each with its MBP-10 proxy already in use: does MBO add anything.

T2. NATIVE NQ OPTIONS (GLBX options on NQ futures, incl. weekly and same-day expiries): open interest and volume by strike, intraday; call wall, put wall, zero-gamma estimate with real implied vols, pin strikes into expiry; as levels (targets in front of a wall, stops behind one) and as a chop-vs-trend regime. Then QUOTE (do not buy without the user) one month of GEXBot Quant and of FlashAlpha Alpha, and say whether a vendor archive would add anything over the native build.

T3. INTERNALS: find a purchasable history of NYSE / Nasdaq TICK, ADD, VOLD; if none, build breadth from whole-market 1-min bars (quoted $337 for L6M). Score as a trend-day flag and as an exit signal in RTH. State how close the stand-in is to the official series.

T4. NEWS TIMESTAMPS: quote a historical headline archive with second-level timestamps (Benzinga or similar). If a cheap sample exists, test shock labelling with real headline times against the price-based shock detector.

T5. OTHER CME DATA: MNQ and MES aggressor flow vs NQ / ES (small-lot against large-lot), CME block trades, daily open-interest change, settlement and CVOL.

T6. LIVE PATH for every survivor: which feed, monthly cost, the Python sidecar feature name and update rate, what D7 must read, and the break-even — $ per month saved vs $ per month paid.

Family null and forward placebo for every family; report how many cells would pass by chance. Say plainly when a family is null.

# T-TOOLS ADDENDUM (user, 2026-11-12 19:35Z) — MBO / deep-book work does NOT stop and does NOT return empty.
RULE: this is a standing program. Every page delivers the BEST deep-book feature found so far per use, with its honest evidence (four windows, WF, placebo p, scorecard, $ per week at the user's lots) — "none" is not a deliverable. A null family is logged and the next hypothesis starts the same hour. The placebo, family null and trend-week clause stay ON: never relabel noise as a pass; rank by evidence and say plainly how strong it is. Recents first; a feature that works on L3M / L6M and is only "a little worse" before is a candidate (rule 2a). If the $1,500 runs out, quote the next purchase and keep working on what is owned.
DIRECTION — the horizon is the point. Deep-book edge lives in seconds to a few minutes, so aim it at TIMING and EXECUTION first, outcome prediction second:
 1. ENTRY TIMING inside the signal: once a book signals, the next 0-120 s — enter now / wait for a book state (queue imbalance flips with, large order appears behind, absorption of the opposing aggressor, sweep exhausted) / skip if it never comes. Target: average entry k ticks better with the same fills. Score ticks saved x lots, and missed winners.
 2. ADVERSE-SELECTION FILTER: fills that happen INTO a large aggressor sweep, a pulled book or an iceberg on the other side — the "last one in before it turns" fills. Skip / delay / half.
 3. PASSIVE FILLS WITH REAL QUEUE: where to rest entry and target limits (behind a large order, in front of an iceberg, at the level with the shortest queue per unit of trade flow); expected fill time; cancel-and-chase rules.
 4. EXIT TIMING: at the target zone, at a floor, and at the cut — exit on the second the book says so (iceberg absorbing our direction, large order pulled ahead, queue at the target not shrinking) instead of at a fixed level.
 5. LIQUIDITY MAP as levels: where large resting orders sat and survived today / this session (the heatmap a Bookmap user watches) -> targets in front, stops behind, entries on the retest; refreshed intraday.
 6. ORDER-FLOW REGIME per minute: participation of large orders, cancel-to-trade ratio, order lifetime, depth resilience after a sweep (how fast the book refills) -> chop-vs-trend flag and size dial.
 7. EVENT STUDIES first, rules second: for each MBO event type (iceberg found, stop run, large pull, large add, refill failure) publish the average NQ path for the next 1 / 5 / 30 / 120 s and 5 / 15 min, by session and by side relative to an open D7 trade. Build rules only from events whose path beats the placebo.
 8. LEARNED short-horizon signal: predict the next 5-60 s mid move from MBO features (small monotone GBDT, purged WF, 3 seeds); use it ONLY for timing (items 1, 3, 4), never as a trade signal on its own.
 9. Then outcome uses: loss cut, early cut, near-zone, entry skip — with the best event features from 7.
LOOP: after each null, widen in this order — other sessions and books, other horizons (1 s to 15 min), ES and RTY MBO for the same events, combinations of two event types, conditioning on the entry context tag (fresh / rechase) and on the regime dials. Log every hypothesis tried so nothing is run twice.
DELIVER each page: (a) the current best timing feature and the ticks it saves per trade at the user's lots; (b) the current best protection feature; (c) the event-study table; (d) what is running next; (e) the live path and monthly cost for the leader.
