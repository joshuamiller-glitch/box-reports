# NEW_BOOK_LAYER_FIT_BEATS_LIVE - own fitted layers of every D8 candidate that beats a live book (W-LAYERS, refreshed 2026-11-19 11:07Z)

Generator: code/th_layers/layer_gen.py (verified: reproduces all 81 XA3 sets byte-identically), cron code/th_layers/layer_cron.py every 30 min. Basis: each layer setting is the new book's own REPLACE row (base) + ONE layer on the exact engine vs TODAY's stack, fitted on the last 6 months (3 months beside), every live layer stays ON; prior years / 30 layered controls / 2-week roll still to run; provisional until Asia, London are decided (clock order). Columns = layered set minus its base row: stack ulcer (negative = better), worst week, max DD, mean $/wk (engine base lots, $4.84 RT proxy); a setting must keep trades >= 80% of the base.

## Progress and engine hours (read from autopilot/HEALTH.md at every refresh, never a fixed rate)
- engine rate: 2428 set-months/h (HEALTH.md at 11:05Z); layer queue (tag NYL, quota 36) landed 88 set-months in the last hour, 88 in 3 h; fast-path share of engine slots (W-FASTLADDER): 90%
- layer set-months queued 7812, landed 52, remaining 7724; hours at the HEALTH rate (whole fleet) 3.2 h; at the measured NYL rate 88 h; at the fast-path rate: once W-FASTLADDER reports >= 90% of engine slots on the fast path the same remaining work counts at the fast-path speed-up (2.3x measured on one Asia ADD month; NY AM / REPLACE not yet timed)

| label | layer set-months queued | landed |
|---|---|---|
| Lda55d973xA7 | 432 | 52 |
| L5c9e11b3xA7 | 432 | 0 |
| La5b5d03axA7 | 432 | 0 |
| Ledfbf4d2xA7 | 432 | 0 |
| Lcb276f27xA7 | 432 | 0 |
| L0a809c2exA7 | 432 | 0 |
| Lf77e374bxA7 | 432 | 0 |
| L5d9e7166xA7 | 432 | 0 |
| L17ce266fxA7 | 432 | 0 |
| L63ff9ae8xA7 | 432 | 0 |
| L05222ff9xA7 | 432 | 0 |
| L7c368a4fxA7 | 432 | 0 |
| L0b1d7882xA7 | 432 | 0 |
| L1edb9fabxA7 | 432 | 0 |
| L6a25b155xK7 | 432 | 0 |
| L01811caaxK7 | 432 | 0 |
| L0f097450xK7 | 432 | 0 |
| L3701b464xK7 | 432 | 0 |

## D8 gates per candidate (persistence > 0.60, no red prior year; tier 0 = queued first)
| label | tier | gate detail |
|---|---|---|
| L5c9e11b3xA7 | 0 | persistence 0.622 > 0.60; prior years R/wk +0.35/+0.63/+0.42 |
| Ledfbf4d2xA7 | 0 | persistence 0.622 > 0.60; prior years R/wk +0.23/+0.43/+0.29 |
| L5d9e7166xA7 | 0 | persistence 0.622 > 0.60; prior years R/wk +0.07/+0.21/+0.18 |
| L17ce266fxA7 | 0 | persistence 0.622 > 0.60; prior years R/wk +0.07/+0.21/+0.18 |
| L6a25b155xK7 | 1 | engine prior years 3, none red (screen persistence not in the rows) |
| L01811caaxK7 | 1 | engine prior years 3, none red (screen persistence not in the rows) |
| L0f097450xK7 | 1 | engine prior years 3, none red (screen persistence not in the rows) |
| L3701b464xK7 | 2 | engine prior years not evaluated yet (pending) |
| Lda55d973xA7 | 3 | persistence 0.561 <= 0.60; prior years R/wk +0.06/+0.24/+0.15 |
| La5b5d03axA7 | 3 | persistence 0.573 <= 0.60; prior years R/wk +0.20/+0.17/-0.06 (RED: 2025 negative) |
| Lcb276f27xA7 | 3 | persistence 0.573 <= 0.60; prior years R/wk +0.19/+0.20/-0.03 (RED: 2025 negative) |
| L0a809c2exA7 | 3 | persistence 0.549 <= 0.60; prior years R/wk +0.20/+0.01/+0.45 |
| Lf77e374bxA7 | 3 | persistence 0.512 <= 0.60; prior years R/wk +0.02/+0.07/-0.09 (RED: 2025 negative) |
| L63ff9ae8xA7 | 3 | persistence 0.598 <= 0.60; prior years R/wk +0.08/+0.18/+0.26 |
| L05222ff9xA7 | 3 | persistence 0.598 <= 0.60; prior years R/wk +0.08/+0.18/+0.26 |
| L7c368a4fxA7 | 3 | persistence 0.537 <= 0.60; prior years R/wk +0.07/+0.48/+0.26 |
| L0b1d7882xA7 | 3 | persistence 0.488 <= 0.60; prior years R/wk +0.07/+0.02/-0.16 (RED: 2025 negative) |
| L1edb9fabxA7 | 3 | persistence 0.500 <= 0.60; prior years R/wk +0.07/+0.49/+0.22 |

## Identity (inert hook = base row, trade for trade)
- Asia: PASS 9/9 inert sets equal to TL3_ASI_Lda55d973_RA7 on 202610,202608 trade for trade
- NYAM: PASS 9/9 inert sets equal to TL3_NYE_L6a25b155_RK7 on 202610,202608 trade for trade

## Candidates
| label | session | replaced book | variant | stage | fit sets | L6M scored | top-2 prior-year sets | joint sets |
|---|---|---|---|---|---|---|---|---|
| Lda55d973xA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L5c9e11b3xA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| La5b5d03axA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| Ledfbf4d2xA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| Lcb276f27xA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L0a809c2exA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| Lf77e374bxA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L5d9e7166xA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L17ce266fxA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L63ff9ae8xA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L05222ff9xA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L7c368a4fxA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L0b1d7882xA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L1edb9fabxA7 | Asia | A7 | both | fit queued | 72 | - | 0 | 0 |
| L6a25b155xK7 | NYAM | K7 | both | fit queued | 72 | - | 0 | 0 |
| L01811caaxK7 | NYAM | K7 | both | fit queued | 72 | - | 0 | 0 |
| L0f097450xK7 | NYAM | K7 | both | fit queued | 72 | - | 0 | 0 |
| L3701b464xK7 | NYAM | K7 | both | fit queued | 72 | - | 0 | 0 |

## Variant notes (order 1014Z: every yes row counts, the engine is the judge)
| label | session | book | variant | note |
|---|---|---|---|---|
| Lda55d973xA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L5c9e11b3xA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| La5b5d03axA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Ledfbf4d2xA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lcb276f27xA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0a809c2exA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lf77e374bxA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L5d9e7166xA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L17ce266fxA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L63ff9ae8xA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L05222ff9xA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L7c368a4fxA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0b1d7882xA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L1edb9fabxA7 | Asia | A7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0f097450xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L3701b464xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
