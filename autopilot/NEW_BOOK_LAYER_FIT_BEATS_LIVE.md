# NEW_BOOK_LAYER_FIT_BEATS_LIVE - own fitted layers of every D8 candidate that beats a live book (W-LAYERS, refreshed 2026-11-19 15:45Z)

Generator: code/th_layers/layer_gen.py (verified: reproduces all 81 XA3 sets byte-identically), cron code/th_layers/layer_cron.py every 30 min. Basis: each layer setting is the new book's own REPLACE row (base) + ONE layer on the exact engine vs TODAY's stack, fitted on the last 6 months (3 months beside), every live layer stays ON; prior years / 30 layered controls / 2-week roll still to run; provisional until Asia, London are decided (clock order). Columns = layered set minus its base row: stack ulcer (negative = better), worst week, max DD, mean $/wk (engine base lots, $4.84 RT proxy); a setting must keep trades >= 80% of the base.

## Progress and engine hours (read from autopilot/HEALTH.md at every refresh, never a fixed rate)
- engine rate: 2642 set-months/h (HEALTH.md at 15:45Z); layer queue (tag NYL, quota 36) landed 1832 set-months in the last hour, 5581 in 3 h; fast-path share of engine slots (W-FASTLADDER): 90%
- layer set-months queued 3594, landed 3320, remaining 238; hours at the HEALTH rate (whole fleet) 0.1 h; at the measured NYL rate 0 h; at the fast-path rate: once W-FASTLADDER reports >= 90% of engine slots on the fast path the same remaining work counts at the fast-path speed-up (2.3x measured on one Asia ADD month; NY AM / REPLACE not yet timed)

| label | layer set-months queued | landed |
|---|---|---|
| L5c9e11b3xA7 | 795 | 788 |
| L6a25b155xK7 | 561 | 561 |
| L01811caaxK7 | 906 | 906 |
| L01811caaxP7 | 432 | 431 |
| L01811caaxM7 | 432 | 431 |
| L01811caaxH7 | 432 | 203 |

## D8 gates per candidate: ENGINE rule B (order 1122Z)
Rule B: the stack WITH the new book (REPLACE row) vs TODAY'S stack in the SAME prior year. Sign convention: every percentage is "% WORSE than today's stack" (positive = worse): stack ulcer higher, max DD deeper, worst week lower, mean $/wk lower; negative = better. RED if any > 30%, AMBER 15-30%, else GREEN; persistence = share of 2-week windows where the new stack is not below today's (engine weekly difference). Until a candidate has engine prior years its tier is PENDING (never fail); the screen rule A (bare stream) is shown only as a note and orders the queue. Gate (order 1324Z, Josh): L6M + L3M beat (the candidate rows) + no RED prior year (rule B) + ENGINE persistence >= 0.58 (share of 2-week windows where the new stack is not worse than today's); persistence not yet published = PENDING, never fail (W-LAYERS' own pooled prior-year value is shown as provisional and is not used to fail). Tier -1/FIRST = coordinator-ordered first tier, 0 = gate pass, 2 = pending, 3 = rule-B RED / persistence fail / duplicate stream; Asia before NY inside a tier.

| label | tier | rule B verdict (and screen note) | 2023 d ulcer / d DD / d worst wk / d $/wk (% worse) colour | 2024 | 2025 | engine persistence |
|---|---|---|---|---|---|---|
| L01811caaxK7 | FIRST | FIRST (coordinator order 1156Z, position 1) | GATE PASS: 3 prior years none RED (AMBER 2023), engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.577 | -21% / +10% / +19% / -20% AMBER | -14% / -4% / +6% / -12% GREEN | -12% / -10% / -12% / -7% GREEN | 0.58 |
| L6a25b155xK7 | FIRST | FIRST (coordinator order 1156Z, position 2) | GATE PASS: 3 prior years none RED, engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.577 | -4% / +13% / +5% / -25% GREEN | +10% / -3% / -3% / -14% GREEN | +3% / +3% / +0% / -7% GREEN | 0.58 |
| L5c9e11b3xA7 | FIRST | FIRST (coordinator order 1349Z, position 3) | W-ASIA PASS LIST: pass (pick REPLACE, pooled engine persistence 0.58 >= 0.58, 3 prior years no RED) | n/a | n/a | n/a | 0.58 |
| L01811caaxP7 | 1 | tier 1 (strict PASS, after the K7 / first-tier programmes): strict criterion computed by W-LAYERS (L6M ulcer -713 mean +714 worst wk +1209 max DD +4245 ok; L3M ulcer -1365 mean +832 worst wk +4654 max DD +5426 ok) | GATE PASS: 3 prior years none RED, engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.690 | -11% / +9% / +15% / -29% GREEN | -14% / -1% / +1% / -16% GREEN | -18% / -18% / +1% / -15% GREEN | 0.69 |
| L01811caaxM7 | 1 | tier 1 (strict PASS, after the K7 / first-tier programmes): strict criterion computed by W-LAYERS (L6M ulcer -457 mean +562 worst wk +2660 max DD +3039 ok; L3M ulcer -736 mean +505 worst wk +3831 max DD +3039 ok) | GATE PASS: 3 prior years none RED, engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.606 | -28% / -16% / -5% / -42% GREEN | -10% / -8% / -3% / -2% GREEN | -16% / -9% / -8% / -10% GREEN | 0.61 |
| L01811caaxH7 | 1 | tier 1 (strict PASS, after the K7 / first-tier programmes): strict criterion computed by W-LAYERS (L6M ulcer -222 mean +753 worst wk +319 max DD +2671 ok; L3M ulcer -590 mean +995 worst wk +3909 max DD +2671 ok) | GATE PASS: 3 prior years none RED, engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.662 | -20% / -6% / +5% / -36% GREEN | -16% / +0% / +4% / -15% GREEN | -16% / -15% / -7% / -14% GREEN | 0.66 |
| L0a809c2exA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L63ff9ae8xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| Lcb276f27xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L1edb9fabxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L7c368a4fxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| Ledfbf4d2xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| Lda55d973xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| La5b5d03axA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L17ce266fxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L5d9e7166xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L05222ff9xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| M15f14debxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| Lf77e374bxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L0b1d7882xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L30aad100xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L6a25b155xP7 | 2 | strict PASS but not gate pass yet: strict criterion computed by W-LAYERS (L6M ulcer -684 mean +152 worst wk +484 max DD +4245 ok; L3M ulcer -1386 mean +424 worst wk +484 max DD +4475 ok) | pending: no engine prior year landed yet | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only n/a | n/a | n/a | n/a | n/a |
| L0f097450xP7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -1014 mean +1313 worst wk -796 max DD +4245 NOT strict; L3M ulcer -2012 mean +1418 worst wk +724 max DD +8426 ok) | pending: no engine prior year landed yet | W-NYENG pooled 43-month engine persistence 0.55 (REPLACE base); W-LAYERS 2023-25-only n/a | n/a | n/a | n/a | n/a |
| L0f097450xM7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -799 mean +1497 worst wk -100 max DD +6039 NOT strict; L3M ulcer -1391 mean +1273 worst wk -100 max DD +6039 NOT strict) | pending: no engine prior year landed yet | W-NYENG pooled 43-month engine persistence 0.55 (REPLACE base); W-LAYERS 2023-25-only n/a | n/a | n/a | n/a | n/a |
| L0f097450xK7 | 3 | NOT first tier: strict criterion FAIL - W-NYENG strict table | B FAIL: RED in 2023 | W-NYENG pooled 43-month engine persistence 0.55 (REPLACE base); W-LAYERS 2023-25-only 0.606 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| L0f097450xH7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -637 mean +1537 worst wk -1686 max DD +4180 NOT strict; L3M ulcer -1427 mean +1801 worst wk -21 max DD +5671 NOT strict) | pending: no engine prior year landed yet | W-NYENG pooled 43-month engine persistence 0.55 (REPLACE base); W-LAYERS 2023-25-only n/a | n/a | n/a | n/a | n/a |
| L6a25b155xM7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -610 mean +112 worst wk -340 max DD +2089 NOT strict; L3M ulcer -967 mean +84 worst wk -340 max DD +2089 NOT strict) | pending: no engine prior year landed yet | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only n/a | n/a | n/a | n/a | n/a |
| L6a25b155xH7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -360 mean +313 worst wk -261 max DD +1720 NOT strict; L3M ulcer -798 mean +681 worst wk -261 max DD +1720 NOT strict) | pending: no engine prior year landed yet | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only n/a | n/a | n/a | n/a | n/a |
| L21f079b6xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | B FAIL: RED in 2023 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| Lf967df3bxK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | B FAIL: RED in 2023 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| Lbbb39855xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | B FAIL: RED in 2023 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| L0bd23639xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | B FAIL: RED in 2023 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| L77a763afxK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| Le728b0a3xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L21f079b6xP7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -1014 mean +1313 worst wk -796 max DD +4245 NOT strict; L3M ulcer -2012 mean +1418 worst wk +724 max DD +8426 ok) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L21f079b6xM7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -799 mean +1497 worst wk -100 max DD +6039 NOT strict; L3M ulcer -1391 mean +1273 worst wk -100 max DD +6039 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| Lf967df3bxM7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -799 mean +1497 worst wk -100 max DD +6039 NOT strict; L3M ulcer -1391 mean +1273 worst wk -100 max DD +6039 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| Lbbb39855xM7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -799 mean +1497 worst wk -100 max DD +6039 NOT strict; L3M ulcer -1391 mean +1273 worst wk -100 max DD +6039 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L21f079b6xH7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -637 mean +1537 worst wk -1686 max DD +4180 NOT strict; L3M ulcer -1427 mean +1801 worst wk -21 max DD +5671 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| Lf967df3bxH7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -637 mean +1537 worst wk -1686 max DD +4180 NOT strict; L3M ulcer -1427 mean +1801 worst wk -21 max DD +5671 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L0bd23639xM7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -799 mean +1497 worst wk -100 max DD +6039 NOT strict; L3M ulcer -1391 mean +1273 worst wk -100 max DD +6039 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L3701b464xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L0f097450xK7LO | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L3701b464xK7LO | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| M41ef5c77xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Mdcdb0b6exA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L4d206c8cxA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Mac4916e6xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| M98c7ae1dxA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L34e2c5abxA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lb5e883f6xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L01811caa | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L6a25b155 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L0f097450 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| Lda55d973 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| M41ef5c77 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| Mdcdb0b6e | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L4d206c8c | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| Mac4916e6 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| M98c7ae1d | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L34e2c5ab | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| Lb5e883f6 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |

## Identity (inert hook = base row, trade for trade)
- Asia: PASS 9/9 inert sets equal to TL3_ASI_Lda55d973_RA7 on 202610,202608 trade for trade
- NYAM: PASS 9/9 inert sets equal to TL3_NYE_L6a25b155_RK7 on 202610,202608 trade for trade
- NYAM-ADD: PASS 9/9 inert sets equal to TL3_NYW_L01811caa_ADD on 202610,202608 trade for trade
- Asia-ADD: PASS 9/9 inert sets equal to TL3_ASI_Lda55d973_ADD on 202610,202608 trade for trade

## Candidates
| label | session | replaced book | variant | layer base set (REPLACE = default; ADD only when the three-row rule picks it) | stage | fit sets | L6M scored | top-2 prior-year sets | joint sets |
|---|---|---|---|---|---|---|---|---|---|
| Lda55d973xA7 | Asia | A7 | both | TL3_ASI_Lda55d973_RA7 | scored | 72 | 2026-11-19 14:07Z | 12 | 7 |
| La5b5d03axA7 | Asia | A7 | both | TL3_ASI_La5b5d03a_RA7 | fit queued | 72 | - | 0 | 0 |
| Lcb276f27xA7 | Asia | A7 | both | TL3_ASI_Lcb276f27_RA7 | fit queued | 72 | - | 0 | 0 |
| L1edb9fabxA7 | Asia | A7 | both | TL3_ASI_L1edb9fab_RA7 | fit queued | 72 | - | 0 | 0 |
| L0a809c2exA7 | Asia | A7 | both | TL3_ASI_L0a809c2e_RA7 | scored | 72 | 2026-11-19 13:55Z | 6 | 3 |
| L17ce266fxA7 | Asia | A7 | both | TL3_ASI_L17ce266f_RA7 | fit queued | 72 | - | 0 | 0 |
| L5d9e7166xA7 | Asia | A7 | both | TL3_ASI_L5d9e7166_RA7 | scored | 72 | 2026-11-19 12:55Z | 6 | 3 |
| L05222ff9xA7 | Asia | A7 | both | TL3_ASI_L05222ff9_RA7 | scored | 72 | 2026-11-19 13:23Z | 7 | 5 |
| L63ff9ae8xA7 | Asia | A7 | both | TL3_ASI_L63ff9ae8_RA7 | fit queued | 72 | - | 0 | 0 |
| L7c368a4fxA7 | Asia | A7 | both | TL3_ASI_L7c368a4f_RA7 | fit queued | 72 | - | 0 | 0 |
| L30aad100xA7 | Asia | A7 | both | TL3_ASI_L30aad100_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L5c9e11b3xA7 | Asia | A7 | both | TL3_ASI_L5c9e11b3_RA7 | scored | 72 | 2026-11-19 12:55Z | 9 | 5 |
| Ledfbf4d2xA7 | Asia | A7 | both | TL3_ASI_Ledfbf4d2_RA7 | scored | 72 | 2026-11-19 13:05Z | 8 | 3 |
| M15f14debxA7 | Asia | A7 | long | TL3_ASI_M15f14deb_RA7 | fit queued | 72 | - | 0 | 0 |
| Lf77e374bxA7 | Asia | A7 | both | TL3_ASI_Lf77e374b_RA7 | fit queued | 72 | - | 0 | 0 |
| L0b1d7882xA7 | Asia | A7 | both | TL3_ASI_L0b1d7882_RA7 | fit queued | 72 | - | 0 | 0 |
| L6a25b155xK7 | NYAM | K7 | both | TL3_NYE_L6a25b155_RK7 | scored | 72 | 2026-11-19 12:55Z | 3 | 3 |
| L0f097450xP7 | NYAM | P7 | both | TL3_NYE_L0f097450_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0f097450xM7 | NYAM | M7 | both | TL3_NYE_L0f097450_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L01811caaxP7 | NYAM | P7 | both | TL3_NYE_L01811caa_RP7 | fit queued | 72 | - | 0 | 0 |
| L01811caaxK7 | NYAM | K7 | both | TL3_NYE_L01811caa_RK7 | scored | 72 | 2026-11-19 12:45Z | 12 | 5 |
| L6a25b155xP7 | NYAM | P7 | both | TL3_NYE_L6a25b155_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0f097450xK7 | NYAM | K7 | both | TL3_NYE_L0f097450_RK7 | fit queued | 72 | - | 0 | 0 |
| L0f097450xH7 | NYAM | H7 | both | TL3_NYE_L0f097450_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L6a25b155xM7 | NYAM | M7 | both | TL3_NYE_L6a25b155_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L01811caaxM7 | NYAM | M7 | both | TL3_NYE_L01811caa_RM7 | fit queued | 72 | - | 0 | 0 |
| L6a25b155xH7 | NYAM | H7 | both | TL3_NYE_L6a25b155_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L01811caaxH7 | NYAM | H7 | both | TL3_NYE_L01811caa_RH7 | fit queued | 72 | - | 0 | 0 |
| L21f079b6xK7 | NYAM | K7 | both | TL3_NYE_L21f079b6_RK7 | scored | 72 | 2026-11-19 15:15Z | 5 | 1 |
| Lf967df3bxK7 | NYAM | K7 | both | TL3_NYE_Lf967df3b_RK7 | scored | 72 | 2026-11-19 15:35Z | 5 | 1 |
| Lbbb39855xK7 | NYAM | K7 | both | TL3_NYE_Lbbb39855_RK7 | fit queued | 72 | - | 0 | 0 |
| L0bd23639xK7 | NYAM | K7 | both | TL3_NYE_L0bd23639_RK7 | fit queued | 72 | - | 0 | 0 |
| L77a763afxK7 | NYAM | K7 | both | TL3_NYE_L77a763af_RK7 | fit queued | 72 | - | 0 | 0 |
| Le728b0a3xK7 | NYAM | K7 | both | TL3_NYE_Le728b0a3_RK7 | fit queued | 72 | - | 0 | 0 |
| L21f079b6xP7 | NYAM | P7 | both | TL3_NYE_L21f079b6_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L21f079b6xM7 | NYAM | M7 | both | TL3_NYE_L21f079b6_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lf967df3bxM7 | NYAM | M7 | both | TL3_NYE_Lf967df3b_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lbbb39855xM7 | NYAM | M7 | both | TL3_NYE_Lbbb39855_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L21f079b6xH7 | NYAM | H7 | both | TL3_NYE_L21f079b6_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lf967df3bxH7 | NYAM | H7 | both | TL3_NYE_Lf967df3b_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0bd23639xM7 | NYAM | M7 | both | TL3_NYE_L0bd23639_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |

## Variant notes (order 1014Z: every yes row counts, the engine is the judge)
| label | session | book | variant | note |
|---|---|---|---|---|
| Lda55d973xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.52 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| La5b5d03axA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.52 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Lcb276f27xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.53 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L1edb9fabxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.53 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L0a809c2exA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.56 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L17ce266fxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L5d9e7166xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L05222ff9xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L63ff9ae8xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.54 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L7c368a4fxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.53 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L30aad100xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.38 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L5c9e11b3xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.58 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Ledfbf4d2xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.53 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| M15f14debxA7 | Asia | A7 | long | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Lf77e374bxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.48 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L0b1d7882xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.46 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L0f097450xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0f097450xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0f097450xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) [twin of L3701b464 here: same stream, one programme] |
| L0f097450xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L21f079b6xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lf967df3bxK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lbbb39855xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0bd23639xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L77a763afxK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Le728b0a3xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L21f079b6xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L21f079b6xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lf967df3bxM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lbbb39855xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L21f079b6xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lf967df3bxH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0bd23639xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |

## Lda55d973xA7 (Asia, replaces A7; base TL3_ASI_Lda55d973_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 30 min | -43 | +1060 | +2162 | +306 | 0.98 | -473 / +405 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -416 | -1201 | +4785 | -562 | 0.76 | -1240 / +523 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -48 pts | +846 | -4863 | -500 | -272 | 1.02 | +1386 / -408 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -69 | +0 | +0 | +53 | 1.00 | -103 / +156 | n/a | n/a | n/a |
| FR | W-FASTR pick: own day cap loss $2400, profit 9000 | -247 | +0 | +3475 | -416 | 0.92 | -609 / +408 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+20 pts | -335 | -28 | +1684 | -1203 | 1.17 | -344 / -2685 | n/a | n/a | n/a |
| NT | no new entries 1830-1900 ET | -508 | +3162 | +6741 | +167 | 0.98 | -833 / +382 | n/a | n/a | n/a |
| TK | take at 65% of target after 15 s without a new extreme | -160 | +472 | +3544 | -308 | 1.19 | +224 / -1750 | n/a | n/a | n/a |

## L0a809c2exA7 (Asia, replaces A7; base TL3_ASI_L0a809c2e_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 30 min | +7 | +0 | +420 | -202 | 0.96 | -2 / +2 | n/a | n/a | n/a |
| CP | own day loss cap 4 stops ($4800 base), profit cap 12,000 | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +6 | -38 | +0 | -2 | 1.00 | +11 / -3 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | -390 | +477 | -298 | +455 | 1.02 | -797 / +1934 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +20 | -189 | -780 | -360 | +538 | 1.03 | +143 / +731 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -268 | +4141 | -1595 | +497 | 1.09 | +217 / +845 | n/a | n/a | n/a |
| NT | no new entries 1830-1900 ET | -246 | +639 | +1059 | +12 | 0.96 | -275 / +119 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +165 | -75 | -1369 | -165 | 0.99 | +242 / -192 | n/a | n/a | n/a |

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

## L21f079b6xK7 (NYAM, replaces K7; base TL3_NYE_L21f079b6_RK7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | +387 | +0 | -2606 | +260 | 0.99 | +849 / -514 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($2400 base), profit cap 12,000 | -23 | +0 | +0 | +40 | 0.99 | -42 / +82 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -120 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -96 pts | +412 | -2662 | -1669 | -420 | 1.04 | +743 / -356 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: own day cap loss $2400, profit 9000 | -24 | +0 | +0 | +218 | 0.97 | -42 / +82 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+0 pts | -4 | +0 | +0 | -1402 | 1.30 | -95 / -663 | n/a | n/a | n/a |
| NT | no new entries 1100-1130 ET | -48 | +0 | +0 | -28 | 0.97 | -84 / +98 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +18 | +0 | +0 | +133 | 1.01 | +23 / -52 | n/a | n/a | n/a |

## Lf967df3bxK7 (NYAM, replaces K7; base TL3_NYE_Lf967df3b_RK7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | +387 | +0 | -2606 | +260 | 0.99 | +849 / -514 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($2400 base), profit cap 12,000 | -23 | +0 | +0 | +40 | 0.99 | -42 / +82 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -120 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -96 pts | +412 | -2662 | -1669 | -420 | 1.04 | +743 / -356 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: own day cap loss $2400, profit 9000 | -24 | +0 | +0 | +218 | 0.97 | -42 / +82 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+0 pts | -4 | +0 | +0 | -1402 | 1.30 | -95 / -663 | n/a | n/a | n/a |
| NT | no new entries 1100-1130 ET | -48 | +0 | +0 | -28 | 0.97 | -84 / +98 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +18 | +0 | +0 | +133 | 1.01 | +23 / -52 | n/a | n/a | n/a |
