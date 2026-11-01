# USER ORDER T-ZONES-3 ADDENDUM (2026-11-01 ~15:40Z), saved verbatim

T-ZONES-3 ADDENDUM — the zones we have never built: ORDER-FLOW and TAPE zones (user, 2026-11-01 ~15:40Z)

Same rules and the same base as T-ZONES-3 (D7 v1.0d; drawdown first; per book and session; three columns; placebo = random levels of the same count and shuffled-day; prereg). This addendum is a NEW FAMILY, not a re-cut of the price lines: every zone below is built from the order book or the tape, not from bars. The POI map's own gap list names most of them as "not built": absorption PRICE of the last absorption event, last sweep LEVEL, session book-defended levels, touch counts, composite profiles. Build them, score them in the ZONES frames (AHEAD within D → skip / re-target / half / B73 / WT / delay; BEHIND → stop placement / skip; AT → take-only / size-up), and give D7 the definitions (D7 has the 10-level book, the print tape, and the absorption / iceberg / sweep / pulled detectors live; anything it cannot compute goes into the daily zones file).

A. The zones (each a stream with price, formed time, freshness = untouched since formed, strength, decay)
Absorption prices: the price of each absorption event (≥ k × median level hit at one price without the best moving for ≥ N s; the L2 gate's definition), kept as a level for 1 / 4 / 24 h with decay; strength = size absorbed. Side-aware: bid-side absorption = a defended floor, ask-side = a ceiling.
Iceberg prices: price of each iceberg refill event (≥ 2 refills at one price), same keeping and decay.
Sweep levels: the price of each sweep (a session / prior-day / swing high or low taken by ≥ 1 tick and reclaimed within N min) — the level that was swept, and the extreme of the sweep (where the stops were).
Book-defended levels: prices where resting size ≥ k × the median level persisted for ≥ N s while price traded within 2 ticks of it and did not go through; and the mirror — prices where a wall was PULLED as price approached (a fake level). From the mbp-10 history, every day since 2023-08.
Tape volume-at-price: session and day high-volume nodes (top decile of volume per 1-pt bin, from the 1-s print tape), low-volume nodes / single-print voids, and the developing POC; the 5 / 20 / 60-day composite (the three profile lines group 10 lacks, built properly here from the tape). Also delta-at-price: bins where aggressive volume was large and price did not progress (absorption seen in the tape rather than the book).
Cumulative-delta extremes: the price at the session's cumulative-delta high / low and at delta divergences (price new high, delta not); the price where the day's largest 60-s aggressor burst ended (exhaustion level).
Large-print prices: prices of prints ≥ 25 / 50 / 100 contracts (block trades) in the last 1 / 4 h; clusters of them.
Liquidity pools (stop clusters), measured not assumed: for every swing H/L, equal H/L and session H/L, the actual aggressor volume that printed within 2 ticks beyond it when it was broken, over history → the pools that really hold stops vs the ones that do not; use the measured pool size as the strength.
L2-zone density: how many of 1-8 sit within 20 / 40 / 60 pts ahead / behind at the signal; the distance to the nearest; ahead/behind ratio.
B. Scoring

Every zone in every ZONES frame, D = 10 / 20 / 30 / 40 / 60 pts and 25 / 50 / 75 % of the target, freshness, age, strength terciles, per book and session, drawdown first on the D7 base with the stack placebo; the combinations with the price lines (an L2 zone that coincides with a set line within 5 pts = confirmed zone; a set line with NO L2 evidence = weak line); and the ONE learned rule over price + L2 zones together (walk-forward, shuffled features, ≤ 6-rule tree). Capacity and latency as usual (1-s / 3-s delay on the actions that enter).

C. Deliver

DS3_ZONES_3_L2.md: the zone table ranked by maxDD cut at equal risk with the placebo beaten; per zone the exact live definition (what D7 computes from its own book/tape, what needs the daily file); the combined price + L2 zone layer vs the shipped group 10 vs the ZONES-3 price layer; the plain sentence "order-flow zones add X to the drawdown cut of the price zones / they are the same information / they are worse". Rows to RECENT_WINS; a ZONES-L2 line in the brief; MORNING.md every 2 h. Runs beside T-ZONES-3 with its own agents; this family is new, so it gets the full placebo set before any row is called a lead.
