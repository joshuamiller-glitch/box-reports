ICT STUDY — comprehensive, mechanical, pre-registered. Instruments NQ (primary), ES, RTY; bars 1/3/5/15-min from the 1-second data; sessions in ET. Every concept below is defined as a rule with a parameter grid; each is scored in four use-modes: M1 standalone (bracket/trail exits), M2/M3 sleeve to the pair, M4 pair confirmation/filter/size tilt at the flip, M5 stop/target placement for the pair's trades. Nulls: timing-destroyed AND a random-level null (same rule on levels shifted by a random offset) — a level concept must beat both. Plateau, 2x slippage, era flag, library save. ~3,000 cells; write PREREG_ICT.md first; REPORT_ICT.md with a verdict per concept.

Structure and levels
1 Market structure: swing highs/lows by fractal {3,5,7}; BOS and CHoCH events; entry on BOS continuation and on CHoCH reversal; displacement filter (break candle range > {1,1.5,2} ATR)
2 Fair value gaps (3-candle imbalance), min size {0.25,0.5,1} ATR; entry on first return to the FVG {50% (consequent encroachment), full fill}; inversion FVG; FVG as pair target/stop level
3 Order blocks: last opposite candle before a displacement; entry on return to OB {open, 50%}; mitigation blocks; breaker blocks; propulsion/rejection blocks
4 Liquidity pools: equal highs/lows (within {1,2,3} ticks over {10,20,50} bars), prior-day/prior-week/session highs and lows, Asian-range extremes; (a) sweep-and-reverse entry (turtle soup / judas swing: sweep by >= x ticks then close back inside within N bars); (b) PAIR STOP PLACEMENT: move the pair's stops just beyond the nearest liquidity pool instead of fixed 60 pts (report how often the live 60-pt stop sits inside a pool that then gets swept)
5 Premium/discount: position of price in the dealing range (last swing low->high); only longs in discount / shorts in premium; OTE zone = 62-79% retracement, entry on touch with displacement confirmation
6 Balanced price range, volume imbalance, new-day / new-week opening gaps (NDOG/NWOG) as levels: fade and target
7 SMT divergence: NQ makes a new high/low while ES (or RTY) does not, at session extremes; as reversal entry and as pair-flip confirmation
8 Daily bias: previous-day close vs open, NDOG direction, and the 00:00 ET midnight open -> bias for RTH; as pair size tilt by direction agreement
9 Power of three / AMD: open, manipulation (sweep of overnight range), distribution; entry after the manipulation leg reverses through the open; as RTH model
10 Dealing-range / CBDR (14:00-20:00 ET) and Asian range (20:00-00:00) standard-deviation projections as targets
Time
11 Kill zones: Asia (20:00-00:00), London (02:00-05:00), NY AM (07:00-10:00), NY PM (13:00-16:00), London close (10:00-12:00): each concept restricted to each kill zone; and the pair's flips sized {0,50,100,150}% by kill zone (walk-forward)
12 Silver Bullet windows 03:00-04:00, 10:00-11:00, 14:00-15:00 ET: FVG entry inside the window only
13 ICT macros (09:50-10:10, 10:50-11:10, 11:50-12:10, 13:10-13:40, 15:15-15:45): liquidity-run behaviour inside the window; as pair pause or tilt
14 08:30 / 09:30 / 10:00 reversal times and the 'true day open' at 00:00: time-of-day reversal entries conditioned on a sweep
Composite models
15 '2022 model': liquidity sweep -> MSS/displacement -> FVG entry in a kill zone, target the opposite liquidity pool
16 'Silver Bullet model': FVG in the window with draw on liquidity
17 'Unicorn': breaker block overlapping an FVG
18 Turtle soup / judas swing standalone (item 4a) by session
19 ultraZen / BOS / FSD from outputs/strats/README.md specs (approximate ports), scored like the rest
Report: per concept, standalone and as a pair filter/tilt/stop rule; the random-level null is the gate that matters. Specifically answer: (i) do liquidity pools predict where the pair's stops get hit, and does pool-aware stop placement improve the pair; (ii) does SMT divergence at the flip improve the pair's win rate; (iii) does any kill-zone tilt survive walk-forward.
