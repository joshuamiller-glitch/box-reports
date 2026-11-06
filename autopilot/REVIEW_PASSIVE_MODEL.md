# REVIEW_PASSIVE_MODEL - independent review of ZL-1's passive maker / queue model (CHAR-C, 2026-11-06)

Scope: read-only on ZL-1's files. Cell reviewed in full: ES NY-AM, CHAR-A prior-day-level touch + burst (vol5 >= 90th pct, buf 0), direction = approach (continuation), hold h = 60 s (also h = 300, 1800 as a check). All bulk output under /mnt/l2/l2vast/find_c/review/. Code: l2vast/ds3/code/find_c/{review_sim.py (my simulator), review_run.py, review_an.py, review_an2.py, review_hand.py, review_ts.py, review_z1copy.py}. No purchase, no live claim, no PASS claim.

## Verdict in six lines
1. MATCH on mechanics: my own simulator (written from the event-store rows, not from maker.py) reproduces ZL-1 on all 428 ES events: same 428 placed, same 416 fills, 100% identical fill timestamp (ns), fill price, queue-ahead at arrival, and per-order net (max abs difference 0.0 ticks). On ZL-1's own order window (369 orders) it gives 357 fills, net/order +2.32 (disc +2.54, test +2.03), exactly ZL-1's published row.
2. Premise correction: Z1's deep_maker.py is NOT an independent implementation. It imports ZL-1's maker_study.work and maker.py unchanged and only feeds it CHAR-A's events. I ran a copy of it for ES (output to my review dir): disc 2.54 / test 2.03 at h60, 2.98 / 3.08 at h300 = ZL-1's numbers to 2 decimals. So item (4) is MATCH, but it is one implementation seen twice; the only independent implementation is mine.
3. Hand-check 10 of 10 MATCH (details below).
4. No look-ahead in the event definition: stored vol5 equals the traded volume in [ts0-5 s, ts0) in 94% of 107 sampled events exactly (0% for any window after ts0); the level touch happens at or before ts0 (median -0.4 s).
5. The model is not obviously over-generous: random-time orders in the same direction (the shifted null) lose (-0.24 ticks/order at h60). The inflation risk is in the fill rule: fill rate is 97% and 26% of the fills occur with price NOT trading through our level (queue exhausted by volume at our price).
6. Under pessimistic variants the edge shrinks but does not vanish against the shifted-time null; the traded-through-only variant leaves +0.8 ticks/order (t 1.2), carried by 5 orders. The edge is a small momentum drift (about +2.6 ticks after a touch+burst at h60, t 3.6 on 428 events), worth about $25 per order, 130 orders a year: not an economic strategy by itself.

## (1) Assumptions that can inflate fills or profits (from maker.py, maker_study.py, maker_pre.py, FIND_1BD_addendum2.md)
| # | assumption in the model | direction of bias | how I tested it |
|--|--|--|--|
| A1 | queue ahead = displayed touch size at the last consistent row before arrival; arrival = decision second + 1 s; events inside that 1 s are skipped (size increases there are behind us, decreases are lost) | small, either way | V4 (+2 s latency) |
| A2 | trades at our price deplete the queue only if aggressor side matches; all volume counts against `ahead` and fill when ahead < 0 (one lot, all-or-nothing, no partial fills) | optimistic if hidden/iceberg or pro-rata allocation exists; ES is price-time so fair | V3 |
| A3 | a trade priced strictly through our price fills us at once, regardless of queue | fair (price-time) | V3 keeps it |
| A4 | cancels ahead: proportional share ahead/(level - pending trades), M (modify) rows treated as cancels, size increases ignored | optimistic if cancels cluster behind us (queue front is stickier: orders at the front are old and rarely cancel) | V1 (no cancel credit) and V2 (all cancels ahead) |
| A5 | the level size change that follows a trade is matched to the trade by a `pend` counter; any residual is a cancel | can over-credit cancels when trade and size rows are separated in time | V1 |
| A6 | j1 variant (one tick back) uses touch size as queue | not used in the cells reviewed | n/a |
| A7 | adverse cancel: order cancelled 1 s after a consistent-row mid move of -1 tick; orders still fill during that 1 s | slightly optimistic (cancel latency 1 s; exchange latency is lower, so likely fair) | not varied |
| A8 | timeout min(2h, 1800) s: at h60 the order rests up to 120 s; 104 s fills occur | long-wait fills are the cheapest-looking ones | order 8 in hand check |
| A9 | passive exit joins the opposite touch with queue model and no cancel; fallback taker at the far touch 1 s after the exit window, no extra slippage | optimistic: exit fills 96% (conditional on trend direction); passive exit adds +1.0 tick (spread) over taker on every filled order (hand check) | taker-exit column |
| A10 | fee $4.84 round trip charged once, no maker rebate, no exchange/clearing differences, no slippage on taker fallback | fair/neutral | none |
| A11 | per-order net counts unfilled orders as 0 and fills as capture + later drift; the fills are conditioned on price coming to us | normal for maker studies; not a bias by itself | null comparison |
| A12 | timestamps: events are ns event-level; the 1-s convention (ts = bin END) only enters through ts0 and vol5 | none found | review_ts.py |
| A13 | selection: cells picked after seeing CHAR-A's map (1 of 240 per instrument); WY family covers only 11 tested cells; the null is a forward same-day shift 120-1800 s with the same direction, not a random-side null | optimistic multiplicity; the 'p .005' is not 1-in-200 against the whole search | stated; not re-estimated |
| A14 | order set: ZL-1/Z1 drop events in the first 30 s of RTH and within 2h+12 s of the close (59 of 428 ES events); those 59 events earn +0.41 ticks/order at h60 and -1.5 at h1800 | the dropped bucket is the weaker one, but the window filter was fixed before scoring (no evidence of tuning) | subset split in tables |
| A15 | single-contract price-time priority, our order has no market impact and the displayed book is not changed by our presence | neutral at 1 lot | n/a |

## (2) My independent simulator versus ZL-1 (ES NY-AM h60, 428 events, order = touch second t0, arrival t0+1 s)
Per-order comparison, my V0 (same rules, own code) against ZL-1's eval_order_stop output:
| item | result |
|--|--|
| placed | 428 vs 428, identical orders |
| filled | 416 vs 416, same set |
| fill timestamp | identical to the ns on all 416 |
| fill price, queue ahead at arrival | identical on all 416 |
| per-order net ticks | identical (max diff 0.0) |
| median fill delay after arrival | 0.42 s (mean 3.8 s) |
| ZL-1 window subset (369 orders) | 357 fills, +2.32 /order, disc +2.54 (210), test +2.03 (159): equals ZL-1 table |

Pessimistic and sensitivity variants (net ticks per order placed, h60; shifted-time null from the same seeds as ZL-1: forward shift 120-1800 s, 200 worlds; subset = ZL-1's 369-order window; t = per-order t-stat):
| variant | fills / orders | net/order | t | median | net/fill | null mean +- sd | p (1/201 floor .005) | test half-year edge |
|--|--|--|--|--|--|--|--|--|
| V0 proportional cancels (ZL-1 rule) | 357/369 | +2.32 | 3.0 | 1.61 | 2.40 | -0.24 +- 0.60 | .005 | |
| V1 no credit for cancels ahead (all cancels behind us; the conservative ZL-1 mode 1) | 320/369 | +1.65 | 2.2 | 0.00 | 1.91 | -0.71 +- 0.55 | .005 | |
| V2 every cancel ahead of us (optimistic, mode 2) | 357/369 | +2.52 | 3.3 | 1.61 | 2.60 | -0.07 +- 0.58 | .005 | |
| V3 traded-through only (fill only when a trade prints strictly through our price) | 256/369 | +0.82 | 1.2 | 0.00 | 1.18 | -0.97 +- 0.55 | .005 | top 5 orders = 103% of the sum |
| V4 arrival +2 s extra latency | 356/369 | +1.96 | 2.7 | 0.61 | 2.03 | -0.27 +- 0.60 | .005 | |
| V5 V1 + 2 s latency | 323/369 | +1.04 | 1.4 | 0.00 | 1.18 | -0.75 +- 0.59 | .005 | top 5 = 80% |
| V6 V3 + 2 s latency | 249/369 | +0.66 | 1.0 | 0.00 | 0.97 | -0.95 +- 0.54 | .005 | top 5 = 127% |
(The task wording 'all-ahead cancels' as pessimistic: all-ahead is the OPTIMISTIC bound, V2; the pessimistic cancel bound is V1. Both are reported.)

Other holds, same code (subset, V0 / V1 no-cancel / V3 through-only / V5): h300 +3.02 / +2.59 / +1.38 / +2.04 (null 0.02 / -0.49 / -0.87 / -0.49; V3 t 1.2); h1800 +5.64 / +4.26 / +3.41 / +4.54 (null +1.26 / +0.49 / -0.02 / +0.70; V3 t 1.4, p .02).

What the edge becomes: the headline +2.3 ticks/order falls to +1.65 with no cancel credit (-29%), +1.0 with no cancel credit and 2 s more latency (-55%), +0.8 when only trade-through fills count (-65%, t 1.2, median zero, five orders carry it). Over the shifted-time null the gap stays positive in every variant because the null gets worse as well (net edge over null 2.6 / 2.4 / 1.8 ticks for V0 / V1 / V3), so the 'beats the null' statement survives; the 'positive per order, family p .005' statement survives; 'robust positive money' does not: drop the top 5 orders and V0 is +1.38, V1 +0.79, V3 -0.03.
Drift behind the result: mid-to-mid signed drift after the touch is +2.64 ticks at h60 (sd 15.1, t 3.6, n 428) and is not stable by year (2023 -0.07 on 61 events, 2024 +2.3, 2025 +4.7, 2026 +2.4). The passive version adds the half spread on entry (+0.5) and the other tick on exit (+1.0 on the 96% of exits that fill passively) and pays 0.39 tick fee.

## (3) Hand check of 10 filled orders against raw rows (file: /mnt/l2/l2vast/find_c/review/handcheck.txt)
For each, I printed arrival book row, each trade at or through P by the hitting side, each level-size change at P, the running queue, and the fill row. All 10 fill rows are the ZL-1 fill ns timestamp exactly (10/10 MATCH). Orders (ET time, side, P, queue at arrival, delay to fill, ZL-1 net, book at fill):
| order | ET | side | P (ticks) | ahead0 | delay (s) | net | note |
|--|--|--|--|--|--|--|--|
| 8 | 2023-08-23 10:42:57 | buy | 17725 | 31 | 104.4 | +4.61 | queue worked down by 170 cancel/trade rows, filled by 1-lot trade at P with ahead -0.7; fill by queue exhaustion, bid unchanged |
| 55 | 2023-12-06 10:02:53 | buy | 18340 | 283 | 6.3 | -1.39 | a trade of 11 at the level; cancels credited fractionally, fill by a 1-lot print at ahead -0.4 |
| 99 | 2024-04-23 09:45:22 | buy | 20312 | 28 | 0.9 | +19.61 | 5-lot print finished the queue; spread was 2 ticks at arrival |
| 145 | 2024-08-22 11:43:03 | sell | 22454 | 12 | 0.2 | +25.61 | |
| 190 | 2024-12-12 10:08:20 | sell | 24293 | 115 | 20.6 | +11.61 | |
| 235 | 2025-05-29 11:58:13 | sell | 23578 | 19 | 0.5 | +9.61 | |
| 281 | 2025-09-18 09:30:05 | buy | 26748 | 25 | 0.05 | -14.39 | fills but the bid drops a tick under us (mid-P -0.5): adverse fill; this is in the 30-s open window ZL-1 excludes |
| 327 | 2026-02-02 10:06:34 | buy | 27962 | 11 | 0.15 | +9.61 | |
| 372 | 2026-05-04 09:58:48 | sell | 29025 | 40 | 26.8 | -5.39 | |
| 418 | 2026-09-28 10:40:03 | sell | 31012 | 17 | 0.5 | -0.39 | |
Findings: (a) the mechanics do what is documented; (b) every filled order shows capture +0.5 tick vs the mid at fill (or -0.5 once), and net = taker-exit net + exactly 1.0 tick (passive exit saved the spread); (c) the arrival row is 2 to 34 ms before arrival, so the displayed size is fresh; (d) these checks verify the rule is applied as written on real rows, they cannot verify that the real exchange queue would behave like the model: only a live shadow order test could. The variants V1/V3 are the honest brackets.

## (4) Z1 versus ZL-1 on the same orders
MATCH, with the caveat that it is the same code: deep_maker.py imports maker_study (MS.work -> maker.run_day -> maker.eval_order) unchanged and builds orders from the same deep_events.parquet; its order-time mapping (sod = ts0 - previous 18:00 ET, then back to epoch) reproduces the same 369 eligible orders (1107 = 3 holds x 369) and, run to a separate output dir, gives ES disc/test net per order +1.33/+1.08 (h30), +2.54/+2.03 (h60), +2.98/+3.08 (h300), filled 202/204/206 disc and 151/153/157 test: equal to ZL-1's cell table. Z1's own reported NQ result (156 test fills, WATCH) therefore inherits every assumption A1 to A15 above; it is not a second opinion on the queue model. My simulator is the only independent check, and it agrees.

## Residual risks and what I would require before any trust
- The fill rule at the touch (V0) versus traded-through-only (V3) differs by 1.5 ticks per order on a 2.3 headline; real fill probability is between them and unknown without live shadow orders.
- Selection (A13): 1 of 240 cells chosen after the map; family p over 11 cells only; the shifted-time null has the same direction and event timing so it cannot detect a model-wide bias that raises all fills equally.
- Year instability of the drift (2023 about 0) and the 59 open/close-window events excluded by design.
- No claim of PASS; nothing goes live. A cheaper first test: a 1-lot shadow (no order sent) logger that records the queue position at arrival and the actual print sequence for a few weeks, to calibrate A2/A4.
