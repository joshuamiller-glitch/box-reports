# NEW_BOOK_LAYER_FIT_BEATS_LIVE - own fitted layers of every D8 candidate that beats a live book (W-LAYERS, refreshed 2026-11-19 12:25Z)

Generator: code/th_layers/layer_gen.py (verified: reproduces all 81 XA3 sets byte-identically), cron code/th_layers/layer_cron.py every 30 min. Basis: each layer setting is the new book's own REPLACE row (base) + ONE layer on the exact engine vs TODAY's stack, fitted on the last 6 months (3 months beside), every live layer stays ON; prior years / 30 layered controls / 2-week roll still to run; provisional until Asia, London are decided (clock order). Columns = layered set minus its base row: stack ulcer (negative = better), worst week, max DD, mean $/wk (engine base lots, $4.84 RT proxy); a setting must keep trades >= 80% of the base.

## Progress and engine hours (read from autopilot/HEALTH.md at every refresh, never a fixed rate)
- engine rate: 2806 set-months/h (HEALTH.md at 12:25Z); layer queue (tag NYL, quota 36) landed 753 set-months in the last hour, 858 in 3 h; fast-path share of engine slots (W-FASTLADDER): 90%
- layer set-months queued 7812, landed 822, remaining 6954; hours at the HEALTH rate (whole fleet) 2.5 h; at the measured NYL rate 9 h; at the fast-path rate: once W-FASTLADDER reports >= 90% of engine slots on the fast path the same remaining work counts at the fast-path speed-up (2.3x measured on one Asia ADD month; NY AM / REPLACE not yet timed)

| label | layer set-months queued | landed |
|---|---|---|
| Lda55d973xA7 | 432 | 62 |
| L5c9e11b3xA7 | 432 | 70 |
| La5b5d03axA7 | 432 | 0 |
| Ledfbf4d2xA7 | 432 | 0 |
| Lcb276f27xA7 | 432 | 0 |
| L0a809c2exA7 | 432 | 0 |
| Lf77e374bxA7 | 432 | 0 |
| L5d9e7166xA7 | 432 | 0 |
| L17ce266fxA7 | 432 | 0 |
| L63ff9ae8xA7 | 432 | 76 |
| L05222ff9xA7 | 432 | 0 |
| L7c368a4fxA7 | 432 | 0 |
| L0b1d7882xA7 | 432 | 0 |
| L1edb9fabxA7 | 432 | 0 |
| L6a25b155xK7 | 432 | 253 |
| L01811caaxK7 | 432 | 361 |
| L0f097450xK7 | 432 | 0 |
| L3701b464xK7 | 432 | 0 |

## D8 gates per candidate: ENGINE rule B (order 1122Z)
Rule B: the stack WITH the new book (REPLACE row) vs TODAY'S stack in the SAME prior year. Sign convention: every percentage is "% WORSE than today's stack" (positive = worse): stack ulcer higher, max DD deeper, worst week lower, mean $/wk lower; negative = better. RED if any > 30%, AMBER 15-30%, else GREEN; persistence = share of 2-week windows where the new stack is not below today's (engine weekly difference). Until a candidate has engine prior years its tier is PENDING (never fail); the screen rule A (bare stream) is shown only as a note and orders the queue. Tier 0 = B pass, 1 = pending (screen pass / years landing), 2 = pending (screen not passing), 3 = B fail; Asia before NY inside a tier.

| label | tier | rule B verdict (and screen note) | 2023 d ulcer / d DD / d worst wk / d $/wk (% worse) colour | 2024 | 2025 | engine persistence |
|---|---|---|---|---|---|---|
| L01811caaxK7 | FIRST | FIRST (coordinator order 1156Z, position 1) | B FAIL: persistence 0.58 <= 0.60 (engine weekly difference) | -21% / +10% / +19% / -20% AMBER | -14% / -4% / +6% / -12% GREEN | -12% / -10% / -12% / -7% GREEN | 0.58 |
| L6a25b155xK7 | FIRST | FIRST (coordinator order 1156Z, position 2) | B FAIL: persistence 0.58 <= 0.60 (engine weekly difference) | -4% / +13% / +5% / -25% GREEN | +10% / -3% / -3% / -14% GREEN | +3% / +3% / +0% / -7% GREEN | 0.58 |
| L5c9e11b3xA7 | FIRST | FIRST (coordinator order 1156Z, position 3) | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.622, prior years R/wk +0.35/+0.63/+0.42 | -1% / +1% / +1% / -24% GREEN | +5% / +1% / -15% / +8% GREEN | +410% / +85% / +92% / +381% RED | 0.51 |
| Ledfbf4d2xA7 | FIRST | FIRST (coordinator order 1156Z, position 4) | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.622, prior years R/wk +0.23/+0.43/+0.29 | +1% / +7% / -3% / -17% GREEN | -1% / -4% / -12% / +6% GREEN | +415% / +85% / +92% / +306% RED | 0.42 |
| L5d9e7166xA7 | FIRST | FIRST (coordinator order 1156Z, position 5) | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.622, prior years R/wk +0.07/+0.21/+0.18 | +5% / +9% / -2% / -14% GREEN | +8% / -4% / -16% / +19% AMBER | +411% / +85% / +92% / +302% RED | 0.39 |
| L63ff9ae8xA7 | 2 | pending: no engine prior year landed yet | screen A (bare stream, ordering only): persistence 0.598, prior years R/wk +0.08/+0.18/+0.26 | n/a | n/a | n/a | n/a |
| L3701b464xK7 | 2 | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| Lda55d973xA7 | 3 | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.561, prior years R/wk +0.06/+0.24/+0.15 | +1% / +9% / -3% / -6% GREEN | +3% / -1% / -17% / +19% AMBER | +411% / +85% / +92% / +330% RED | 0.44 |
| La5b5d03axA7 | 3 | B FAIL: RED in 2023 | screen A (bare stream, ordering only): persistence 0.573, prior years R/wk +0.20/+0.17/-0.06, negative 2025 | +30% / +27% / +3% / -28% RED | +1% / +2% / -26% / +4% GREEN | -27% / -23% / -11% / -59% GREEN | 0.52 |
| Lcb276f27xA7 | 3 | B FAIL: RED in 2023 | screen A (bare stream, ordering only): persistence 0.573, prior years R/wk +0.19/+0.20/-0.03, negative 2025 | +30% / +27% / +3% / -29% RED | +2% / +4% / -25% / +4% GREEN | -28% / -23% / -12% / -59% GREEN | 0.52 |
| L0a809c2exA7 | 3 | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.549, prior years R/wk +0.20/+0.01/+0.45 | -13% / -7% / -4% / -26% GREEN | +21% / -2% / -17% / +25% AMBER | +402% / +84% / +92% / +327% RED | 0.44 |
| Lf77e374bxA7 | 3 | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.512, prior years R/wk +0.02/+0.07/-0.09, negative 2025 | +13% / +15% / -4% / -4% AMBER | +4% / -6% / -13% / +25% AMBER | +411% / +85% / +92% / +279% RED | 0.38 |
| L05222ff9xA7 | 3 | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.598, prior years R/wk +0.08/+0.18/+0.26 | +5% / +9% / -2% / -15% GREEN | +8% / -4% / -16% / +20% AMBER | +411% / +85% / +92% / +305% RED | 0.39 |
| L7c368a4fxA7 | 3 | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.537, prior years R/wk +0.07/+0.48/+0.26 | -5% / -2% / +4% / -16% GREEN | -6% / -9% / -21% / +1% GREEN | +417% / +85% / +92% / +304% RED | 0.44 |
| L0b1d7882xA7 | 3 | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.488, prior years R/wk +0.07/+0.02/-0.16, negative 2025 | -10% / -6% / -0% / -17% GREEN | +4% / -15% / -9% / +27% AMBER | +410% / +85% / +92% / +284% RED | 0.41 |
| L1edb9fabxA7 | 3 | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.500, prior years R/wk +0.07/+0.49/+0.22 | -4% / -2% / +4% / -16% GREEN | -5% / -9% / -21% / +4% GREEN | +416% / +85% / +92% / +312% RED | 0.44 |
| L0f097450xK7 | 3 | B FAIL: RED in 2023 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| L17ce266fxA7 | 3 | same stream as L5d9e7166xA7: its layer programme serves both (queued after, not dropped) | B FAIL: RED in 2025 | screen A (bare stream, ordering only): persistence 0.622, prior years R/wk +0.07/+0.21/+0.18 | +5% / +9% / -2% / -14% GREEN | +8% / -4% / -16% / +19% AMBER | +411% / +85% / +92% / +302% RED | 0.39 |

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
