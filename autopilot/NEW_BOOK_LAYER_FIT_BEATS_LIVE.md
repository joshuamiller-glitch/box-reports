# NEW_BOOK_LAYER_FIT_BEATS_LIVE - own fitted layers of every D8 candidate that beats a live book (W-LAYERS, refreshed 2026-11-19 13:26Z)

Generator: code/th_layers/layer_gen.py (verified: reproduces all 81 XA3 sets byte-identically), cron code/th_layers/layer_cron.py every 30 min. Basis: each layer setting is the new book's own REPLACE row (base) + ONE layer on the exact engine vs TODAY's stack, fitted on the last 6 months (3 months beside), every live layer stays ON; prior years / 30 layered controls / 2-week roll still to run; provisional until Asia, London are decided (clock order). Columns = layered set minus its base row: stack ulcer (negative = better), worst week, max DD, mean $/wk (engine base lots, $4.84 RT proxy); a setting must keep trades >= 80% of the base.

## Progress and engine hours (read from autopilot/HEALTH.md at every refresh, never a fixed rate)
- engine rate: 3798 set-months/h (HEALTH.md at 13:25Z); layer queue (tag NYL, quota 36) landed 3509 set-months in the last hour, 4759 in 3 h; fast-path share of engine slots (W-FASTLADDER): 90%
- layer set-months queued 10053, landed 4755, remaining 5262; hours at the HEALTH rate (whole fleet) 1.4 h; at the measured NYL rate 1 h; at the fast-path rate: once W-FASTLADDER reports >= 90% of engine slots on the fast path the same remaining work counts at the fast-path speed-up (2.3x measured on one Asia ADD month; NY AM / REPLACE not yet timed)

| label | layer set-months queued | landed |
|---|---|---|
| Lda55d973xA7 | 432 | 382 |
| L5c9e11b3xA7 | 795 | 786 |
| La5b5d03axA7 | 432 | 0 |
| Ledfbf4d2xA7 | 746 | 730 |
| Lcb276f27xA7 | 432 | 0 |
| L0a809c2exA7 | 432 | 183 |
| Lf77e374bxA7 | 432 | 8 |
| L5d9e7166xA7 | 672 | 622 |
| L17ce266fxA7 | 432 | 0 |
| L63ff9ae8xA7 | 432 | 83 |
| L05222ff9xA7 | 721 | 432 |
| L7c368a4fxA7 | 432 | 38 |
| L0b1d7882xA7 | 432 | 31 |
| L1edb9fabxA7 | 432 | 26 |
| L6a25b155xK7 | 561 | 561 |
| L01811caaxK7 | 906 | 846 |
| L0f097450xK7 | 432 | 0 |
| L3701b464xK7 | 432 | 16 |
| M15f14debxA7 | 432 | 11 |

## D8 gates per candidate: ENGINE rule B (order 1122Z)
Rule B: the stack WITH the new book (REPLACE row) vs TODAY'S stack in the SAME prior year. Sign convention: every percentage is "% WORSE than today's stack" (positive = worse): stack ulcer higher, max DD deeper, worst week lower, mean $/wk lower; negative = better. RED if any > 30%, AMBER 15-30%, else GREEN; persistence = share of 2-week windows where the new stack is not below today's (engine weekly difference). Until a candidate has engine prior years its tier is PENDING (never fail); the screen rule A (bare stream) is shown only as a note and orders the queue. Gate (order 1324Z, Josh): L6M + L3M beat (the candidate rows) + no RED prior year (rule B) + ENGINE persistence >= 0.58 (share of 2-week windows where the new stack is not worse than today's); persistence not yet published = PENDING, never fail (W-LAYERS' own pooled prior-year value is shown as provisional and is not used to fail). Tier -1/FIRST = coordinator-ordered first tier, 0 = gate pass, 2 = pending, 3 = rule-B RED / persistence fail / duplicate stream; Asia before NY inside a tier.

| label | tier | rule B verdict (and screen note) | 2023 d ulcer / d DD / d worst wk / d $/wk (% worse) colour | 2024 | 2025 | engine persistence |
|---|---|---|---|---|---|---|
| L01811caaxK7 | FIRST | FIRST (coordinator order 1156Z, position 1) | GATE PASS: 3 prior years none RED (AMBER 2023), engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.577 | -21% / +10% / +19% / -20% AMBER | -14% / -4% / +6% / -12% GREEN | -12% / -10% / -12% / -7% GREEN | 0.58 |
| L6a25b155xK7 | FIRST | FIRST (coordinator order 1156Z, position 2) | GATE PASS: 3 prior years none RED, engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.577 | -4% / +13% / +5% / -25% GREEN | +10% / -3% / -3% / -14% GREEN | +3% / +3% / +0% / -7% GREEN | 0.58 |
| L01811caa | FIRST | FIRST (coordinator order 1156Z, position 3) | GATE PASS: 3 prior years none RED, engine persistence 0.600 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.60 (ADD base); W-LAYERS 2023-25-only 0.676 | -15% / -2% / +7% / -39% GREEN | -12% / -1% / +3% / -10% GREEN | -17% / -16% / -2% / -14% GREEN | 0.68 |
| L6a25b155 | FIRST | FIRST (coordinator order 1156Z, position 4) | GATE PASS: 3 prior years none RED, engine persistence 0.650 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.65 (ADD base); W-LAYERS 2023-25-only 0.648 | -18% / +3% / -8% / -42% GREEN | +12% / -0% / -7% / -16% GREEN | -6% / +0% / +11% / -17% GREEN | 0.65 |
| L0f097450 | 0 | GATE PASS: 3 prior years none RED, engine persistence 0.580 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.58 (ADD base); W-LAYERS 2023-25-only 0.592 | -12% / +10% / +12% / -23% GREEN | -3% / -9% / -6% / -14% GREEN | -22% / -20% / -13% / -10% GREEN | 0.59 |
| M15f14debxA7 | 2 | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L5c9e11b3xA7 | 2 | pending: 3 prior years none RED (AMBER 2025); engine persistence not published yet (W-LAYERS provisional 0.507, not used to fail) | screen A (bare stream, ordering only): persistence 0.622, prior years R/wk +0.35/+0.63/+0.42 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 GREEN/2025 AMBER | -1% / +1% / +1% / -24% GREEN | +5% / +1% / -15% / +8% GREEN | +410% / +85% / +92% / +381% RED | 0.51 |
| Lda55d973xA7 | 2 | pending: 3 prior years none RED (AMBER 2024,2025); engine persistence not published yet (W-LAYERS provisional 0.437, not used to fail) | screen A (bare stream, ordering only): persistence 0.561, prior years R/wk +0.06/+0.24/+0.15 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 AMBER/2025 AMBER | +1% / +9% / -3% / -6% GREEN | +3% / -1% / -17% / +19% AMBER | +411% / +85% / +92% / +330% RED | 0.44 |
| L0a809c2exA7 | 2 | pending: 3 prior years none RED (AMBER 2024); engine persistence not published yet (W-LAYERS provisional 0.437, not used to fail) | screen A (bare stream, ordering only): persistence 0.549, prior years R/wk +0.20/+0.01/+0.45 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 AMBER/2025 GREEN | -13% / -7% / -4% / -26% GREEN | +21% / -2% / -17% / +25% AMBER | +402% / +84% / +92% / +327% RED | 0.44 |
| L7c368a4fxA7 | 2 | pending: 3 prior years none RED; engine persistence not published yet (W-LAYERS provisional 0.437, not used to fail) | screen A (bare stream, ordering only): persistence 0.537, prior years R/wk +0.07/+0.48/+0.26 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 GREEN/2025 GREEN | -5% / -2% / +4% / -16% GREEN | -6% / -9% / -21% / +1% GREEN | +417% / +85% / +92% / +304% RED | 0.44 |
| L1edb9fabxA7 | 2 | pending: 3 prior years none RED; engine persistence not published yet (W-LAYERS provisional 0.437, not used to fail) | screen A (bare stream, ordering only): persistence 0.500, prior years R/wk +0.07/+0.49/+0.22 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 GREEN/2025 GREEN | -4% / -2% / +4% / -16% GREEN | -5% / -9% / -21% / +4% GREEN | +416% / +85% / +92% / +312% RED | 0.44 |
| Ledfbf4d2xA7 | 2 | pending: 3 prior years none RED; engine persistence not published yet (W-LAYERS provisional 0.423, not used to fail) | screen A (bare stream, ordering only): persistence 0.622, prior years R/wk +0.23/+0.43/+0.29 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 GREEN/2025 GREEN | +1% / +7% / -3% / -17% GREEN | -1% / -4% / -12% / +6% GREEN | +415% / +85% / +92% / +306% RED | 0.42 |
| L0b1d7882xA7 | 2 | pending: 3 prior years none RED (AMBER 2024); engine persistence not published yet (W-LAYERS provisional 0.408, not used to fail) | screen A (bare stream, ordering only): persistence 0.488, prior years R/wk +0.07/+0.02/-0.16, negative 2025 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 AMBER/2025 GREEN | -10% / -6% / -0% / -17% GREEN | +4% / -15% / -9% / +27% AMBER | +410% / +85% / +92% / +284% RED | 0.41 |
| L5d9e7166xA7 | 2 | pending: 3 prior years none RED (AMBER 2024); engine persistence not published yet (W-LAYERS provisional 0.394, not used to fail) | screen A (bare stream, ordering only): persistence 0.622, prior years R/wk +0.07/+0.21/+0.18 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 AMBER/2025 GREEN | +5% / +9% / -2% / -14% GREEN | +8% / -4% / -16% / +19% AMBER | +411% / +85% / +92% / +302% RED | 0.39 |
| L05222ff9xA7 | 2 | pending: 3 prior years none RED (AMBER 2024); engine persistence not published yet (W-LAYERS provisional 0.394, not used to fail) | screen A (bare stream, ordering only): persistence 0.598, prior years R/wk +0.08/+0.18/+0.26 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 AMBER/2025 GREEN | +5% / +9% / -2% / -15% GREEN | +8% / -4% / -16% / +20% AMBER | +411% / +85% / +92% / +305% RED | 0.39 |
| Lf77e374bxA7 | 2 | pending: 3 prior years none RED (AMBER 2023,2024,2025); engine persistence not published yet (W-LAYERS provisional 0.380, not used to fail) | screen A (bare stream, ordering only): persistence 0.512, prior years R/wk +0.02/+0.07/-0.09, negative 2025 | rule B from W-ASIA FIXED table: 2023 AMBER/2024 AMBER/2025 AMBER | +13% / +15% / -4% / -4% AMBER | +4% / -6% / -13% / +25% AMBER | +411% / +85% / +92% / +279% RED | 0.38 |
| L3701b464xK7 | 2 | pending: no engine prior year landed yet | W-NYENG pooled 43-month engine persistence 0.54 (REPLACE base); W-LAYERS 2023-25-only n/a | n/a | n/a | n/a | n/a |
| La5b5d03axA7 | 3 | B FAIL: RED in 2023 | screen A (bare stream, ordering only): persistence 0.573, prior years R/wk +0.20/+0.17/-0.06, negative 2025 | rule B from W-ASIA FIXED table: 2023 RED/2024 GREEN/2025 GREEN | +30% / +27% / +3% / -28% RED | +1% / +2% / -26% / +4% GREEN | -27% / -23% / -11% / -59% GREEN | 0.52 |
| Lcb276f27xA7 | 3 | B FAIL: RED in 2023 | screen A (bare stream, ordering only): persistence 0.573, prior years R/wk +0.19/+0.20/-0.03, negative 2025 | rule B from W-ASIA FIXED table: 2023 RED/2024 GREEN/2025 GREEN | +30% / +27% / +3% / -29% RED | +2% / +4% / -25% / +4% GREEN | -28% / -23% / -12% / -59% GREEN | 0.52 |
| L0f097450xK7 | 3 | B FAIL: RED in 2023 | W-NYENG pooled 43-month engine persistence 0.55 (REPLACE base); W-LAYERS 2023-25-only 0.606 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| L17ce266fxA7 | 3 | same stream as L5d9e7166xA7: its layer programme serves both (queued after, not dropped) | pending: 3 prior years none RED (AMBER 2024); engine persistence not published yet (W-LAYERS provisional 0.394, not used to fail) | screen A (bare stream, ordering only): persistence 0.622, prior years R/wk +0.07/+0.21/+0.18 | rule B from W-ASIA FIXED table: 2023 GREEN/2024 AMBER/2025 GREEN | +5% / +9% / -2% / -14% GREEN | +8% / -4% / -16% / +19% AMBER | +411% / +85% / +92% / +302% RED | 0.39 |
| L63ff9ae8xA7 | 3 | same stream as L05222ff9xA7: its layer programme serves both (queued after, not dropped) | pending: no engine prior year landed yet | screen A (bare stream, ordering only): persistence 0.598, prior years R/wk +0.08/+0.18/+0.26 | n/a | n/a | n/a | n/a |

## Identity (inert hook = base row, trade for trade)
- Asia: PASS 9/9 inert sets equal to TL3_ASI_Lda55d973_RA7 on 202610,202608 trade for trade
- NYAM: PASS 9/9 inert sets equal to TL3_NYE_L6a25b155_RK7 on 202610,202608 trade for trade
- NYAM-ADD: pending 

## Candidates
| label | session | replaced book | variant | layer base set (REPLACE = default; ADD only when the three-row rule picks it) | stage | fit sets | L6M scored | top-2 prior-year sets | joint sets |
|---|---|---|---|---|---|---|---|---|---|
| Lda55d973xA7 | Asia | A7 | both | TL3_ASI_Lda55d973_RA7 | fit queued | 72 | - | 0 | 0 |
| L5c9e11b3xA7 | Asia | A7 | both | TL3_ASI_L5c9e11b3_RA7 | scored | 72 | 2026-11-19 12:55Z | 9 | 5 |
| La5b5d03axA7 | Asia | A7 | both | TL3_ASI_La5b5d03a_RA7 | fit queued | 72 | - | 0 | 0 |
| Ledfbf4d2xA7 | Asia | A7 | both | TL3_ASI_Ledfbf4d2_RA7 | scored | 72 | 2026-11-19 13:05Z | 8 | 3 |
| Lcb276f27xA7 | Asia | A7 | both | TL3_ASI_Lcb276f27_RA7 | fit queued | 72 | - | 0 | 0 |
| L0a809c2exA7 | Asia | A7 | both | TL3_ASI_L0a809c2e_RA7 | fit queued | 72 | - | 0 | 0 |
| Lf77e374bxA7 | Asia | A7 | both | TL3_ASI_Lf77e374b_RA7 | fit queued | 72 | - | 0 | 0 |
| L5d9e7166xA7 | Asia | A7 | both | TL3_ASI_L5d9e7166_RA7 | scored | 72 | 2026-11-19 12:55Z | 6 | 3 |
| L17ce266fxA7 | Asia | A7 | both | TL3_ASI_L17ce266f_RA7 | fit queued | 72 | - | 0 | 0 |
| L63ff9ae8xA7 | Asia | A7 | both | TL3_ASI_L63ff9ae8_RA7 | fit queued | 72 | - | 0 | 0 |
| L05222ff9xA7 | Asia | A7 | both | TL3_ASI_L05222ff9_RA7 | scored | 72 | 2026-11-19 13:23Z | 7 | 5 |
| L7c368a4fxA7 | Asia | A7 | both | TL3_ASI_L7c368a4f_RA7 | fit queued | 72 | - | 0 | 0 |
| L0b1d7882xA7 | Asia | A7 | both | TL3_ASI_L0b1d7882_RA7 | fit queued | 72 | - | 0 | 0 |
| L1edb9fabxA7 | Asia | A7 | both | TL3_ASI_L1edb9fab_RA7 | fit queued | 72 | - | 0 | 0 |
| M15f14debxA7 | Asia | A7 | long | TL3_ASI_M15f14deb_RA7 | fit queued | 72 | - | 0 | 0 |
| L01811caa | NYAM | ADD | ADD | - | new | 0 | - | 0 | 0 |
| L6a25b155 | NYAM | ADD | ADD | - | new | 0 | - | 0 | 0 |
| L0f097450 | NYAM | ADD | ADD | - | new | 0 | - | 0 | 0 |
| L6a25b155xK7 | NYAM | K7 | both | TL3_NYE_L6a25b155_RK7 | scored | 72 | 2026-11-19 12:55Z | 3 | 3 |
| L01811caaxK7 | NYAM | K7 | both | TL3_NYE_L01811caa_RK7 | scored | 72 | 2026-11-19 12:45Z | 12 | 5 |
| L0f097450xK7 | NYAM | K7 | both | TL3_NYE_L0f097450_RK7 | fit queued | 72 | - | 0 | 0 |
| L3701b464xK7 | NYAM | K7 | both | TL3_NYE_L3701b464_RK7 | fit queued | 72 | - | 0 | 0 |

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
| M15f14debxA7 | Asia | A7 | long |  |
| L01811caa | NYAM | ADD | ADD | ADD base: W-NYENG rule pick (ADD beats REPLACE on L6M+L3M, none RED) |
| L6a25b155 | NYAM | ADD | ADD | ADD base: W-NYENG rule pick (ADD beats REPLACE on L6M+L3M, none RED) |
| L0f097450 | NYAM | ADD | ADD | ADD base: W-NYENG rule pick (ADD beats REPLACE on L6M+L3M, none RED) |
| L0f097450xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L3701b464xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |

## L5c9e11b3xA7 (Asia, replaces A7; base TL3_ASI_L5c9e11b3_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 30 min | +245 | -707 | -1068 | -38 | 0.96 | -71 / +124 | n/a | n/a | n/a |
| CP | own day loss cap 3 stops ($3600 base), profit cap 12,000 | -136 | +0 | +1013 | -188 | 0.97 | -213 / +103 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | +214 | -2413 | -2088 | -534 | 1.08 | +505 / -864 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -24 | +0 | +0 | -637 | 1.00 | -186 / +369 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +20 | -144 | +446 | +1235 | +17 | 1.08 | -118 / -470 | n/a | n/a | n/a |
| LK | lock at 80% -> stop to entry+0 pts | -202 | +0 | +525 | +11 | 1.05 | +29 / -550 | n/a | n/a | n/a |
| NT | no new entries 1830-1900 ET | -195 | +0 | +1013 | -64 | 0.97 | -262 / -115 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | -76 | -110 | +903 | -76 | 1.00 | -183 / +11 | n/a | n/a | n/a |

## Ledfbf4d2xA7 (Asia, replaces A7; base TL3_ASI_Ledfbf4d2_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +17 | +0 | +0 | -156 | 1.00 | -33 / +91 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -426 | -5894 | +282 | -526 | 0.76 | -639 / -814 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | -0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | +825 | -5733 | -3718 | +1120 | 1.05 | +1540 / +1199 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: own day cap loss $2400, profit 6000 | -161 | -112 | -517 | +45 | 0.93 | -421 / +548 | n/a | n/a | n/a |
| LK | lock at 80% -> stop to entry+0 pts | -93 | +260 | +2485 | +52 | 1.03 | -238 / +658 | n/a | n/a | n/a |
| NT | no new entries 2000-2030 ET | -103 | -582 | +0 | -129 | 0.95 | -140 / +197 | n/a | n/a | n/a |
| TK | take at 65% of target after 30 s without a new extreme | -601 | -286 | +7319 | -897 | 1.18 | -1045 / -1011 | n/a | n/a | n/a |

## L5d9e7166xA7 (Asia, replaces A7; base TL3_ASI_L5d9e7166_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +40 | +0 | +0 | -47 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -231 | -2757 | +930 | -397 | 0.75 | -600 / -540 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | +753 | -6771 | -4814 | -441 | 1.05 | +1437 / -186 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | -417 | +2045 | +1505 | +93 | 1.00 | -721 / +222 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -49 | +3584 | +1100 | -1397 | 1.16 | -69 / -737 | n/a | n/a | n/a |
| NT | no new entries 1930-2000 ET | +52 | +0 | -615 | -421 | 0.99 | +9 / +82 | n/a | n/a | n/a |
| TK | take at 95% of target after 15 s without a new extreme | -442 | +1880 | +1380 | +123 | 1.00 | -683 / +183 | n/a | n/a | n/a |

## L05222ff9xA7 (Asia, replaces A7; base TL3_ASI_L05222ff9_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +40 | +0 | +0 | -47 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -221 | -3962 | +930 | -453 | 0.75 | -612 / -528 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | +739 | -6781 | -4824 | +243 | 1.04 | +1436 / +65 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | -403 | +2050 | +1440 | +83 | 1.00 | -703 / +211 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+20 pts | -249 | +1993 | -1851 | +333 | 1.32 | -234 / +286 | n/a | n/a | n/a |
| NT | no new entries 1930-2000 ET | +38 | +0 | -610 | +151 | 0.98 | +8 / +92 | n/a | n/a | n/a |
| TK | take at 95% of target after 15 s without a new extreme | -442 | +1955 | +1385 | +116 | 1.00 | -688 / +178 | n/a | n/a | n/a |

## L6a25b155xK7 (NYAM, replaces K7; base TL3_NYE_L6a25b155_RK7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +112 | +0 | +0 | -455 | 0.97 | +180 / -827 | n/a | n/a | n/a |
| CP | own day loss cap 2 stops ($4800 base), profit cap 12,000 | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -120 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -96 pts | +41 | +0 | +0 | -626 | 1.02 | +83 / -1138 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -56 | +551 | +551 | -2 | 0.98 | -43 / -352 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | +8 | -50 | +0 | -52 | 1.00 | +14 / -68 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+10 pts | -207 | +2165 | +692 | -30 | 1.14 | -156 / -260 | n/a | n/a | n/a |
| NT | no new entries 1100-1130 ET | +7 | -230 | -230 | +448 | 0.92 | +24 / +715 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +8 | -50 | +0 | -52 | 1.00 | +14 / -68 | n/a | n/a | n/a |

## L01811caaxK7 (NYAM, replaces K7; base TL3_NYE_L01811caa_RK7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | -56 | +845 | +0 | -616 | 0.89 | -46 / -589 | n/a | n/a | n/a |
| CP | own day loss cap 2 stops ($2400 base), profit cap 12,000 | -4 | +0 | +0 | -11 | 0.99 | -7 / -23 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | -31 | -1351 | +0 | -14 | 1.01 | -13 / -590 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -29 | +0 | +0 | -265 | 0.97 | -43 / -769 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +10 | -9 | +0 | +0 | -78 | 1.01 | +18 / -98 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -37 | +127 | +0 | -63 | 1.05 | -24 / +40 | n/a | n/a | n/a |
| NT | no new entries 1130-1200 ET | -8 | -350 | +0 | +18 | 0.89 | -20 / +164 | n/a | n/a | n/a |
| TK | take at 80% of target after 30 s without a new extreme | -4 | +610 | +0 | -145 | 1.03 | +8 / -90 | n/a | n/a | n/a |
