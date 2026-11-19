# NEW_BOOK_BEATS_LIVE_ASIA - does a new book beat the live Asia book(s) in the exact engine? (W-ASIA, order 0400Z), refreshed 2026-11-19 15:00Z

**vs TODAY's stack (JL3, today's DAY-DONE); Asia is decided FIRST; label BETTER = calibration pending, NOT calibrated.** Asia rule (higher bar, order 1731Z / 0210Z item 4): a REPLACE row (new book ON, the named live Asia book's Asia entries OFF) beats that live book only if on BOTH L6M and L3M the stack ulcer is LOWER (drawdown first) AND mean $/wk is not lower AND worst week and max drawdown are not worse; then prior years (no RED = >30% worse; AMBER shown), persistence > 0.60, 30 date-shift controls, calibration. du = d stack ulcer (negative = better), dm = d mean $/wk (base lots, $4.84 RT).

**Counts:** Asia cells with any engine row 729; cells with a finished REPLACE verdict (L6M+L3M landed) 601; cells that beat at least one live Asia book on L6M+L3M under the Asia rule (BETTER, calibration pending) 16 (under the looser NY rule 45); ADD rows finished 715.

| live Asia book replaced | cells finished | beat it | pending |
|---|---|---|---|
| K7 | 75 | 0 | 4 |
| P7 | 68 | 0 | 3 |
| A7 | 601 | 16 | 7 |
| H7 | 72 | 0 | 3 |
| U7 | 72 | 0 | 2 |

**Corrected counts (order 1014Z; a both-side engine result is valid for the both-side book that was run; the engine is the judge): beat a live Asia book on L6M+L3M - both-side 15 (of 373 tested; 486 cells with rows), long-only 1 (of 228 tested; 243 cells so far), short-only 0 (of 0 tested; 0 cells so far).** Old ids of screen-long/short cells are labelled "(both sides, engine-tested)"; M-ids = the mode-correct long-only / short-only twin.

## Beating cells: both-side vs long-only (M) vs short-only side by side (best by the D8 rule is the candidate; a long-only book that beats the both-side book replaces it)
| cell | variant | live book | L6M d ulcer | L6M d $/wk | L6M d worst wk | L6M d maxDD | L3M d ulcer | L3M d $/wk | L3M d worst wk | L3M d maxDD | Asia rule |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Lda55d973 vol_750 | both-side | A7 | -1222 | +911 | +1631 | +1609 | -1416 | +2143 | +1631 | +1609 | yes |
| Mda55d973 vol_750 | long-only | A7 | +20 | -263 | -2862 | -1524 | +475 | -151 | -2862 | -1524 | no |
| La5b5d03a time_m_2 | both-side | A7 | -1197 | +1547 | +3509 | +1430 | -892 | +1038 | +3509 | +1430 | yes |
| Ma5b5d03a time_m_2 | long-only | A7 | -891 | -314 | +2617 | +3982 | -667 | +684 | +2617 | +3982 | no |
| Lcb276f27 tm120 | both-side | A7 | -1146 | +1567 | +3471 | +1415 | -811 | +1085 | +3471 | +1415 | yes |
| Mcb276f27 tm120 | long-only | A7 | -889 | -376 | +1282 | +3982 | -665 | +579 | +1282 | +3982 | no |
| L1edb9fab tm300 | both-side | A7 | -142 | +1606 | +464 | +98 | -1252 | +3083 | +2203 | +5307 | yes |
| M1edb9fab tm300 | long-only | A7 | -1085 | +630 | -580 | +3817 | -1067 | +1519 | +258 | +3817 | no |
| L0a809c2e kagi_40 | both-side | A7 | -789 | +402 | +319 | +4417 | -1498 | +1029 | +319 | +4837 | yes |
| M0a809c2e kagi_40 | long-only | A7 | -52 | -718 | -2961 | +1017 | -91 | +468 | -2961 | +1017 | no |
| L17ce266f tm240 | both-side | A7 | -406 | +659 | +354 | +1128 | -119 | +1682 | +354 | +1128 | yes |
| M17ce266f tm240 | long-only | A7 | -697 | +373 | -784 | +1047 | -373 | +931 | -784 | +1047 | no |
| L5d9e7166 tm240 | both-side | A7 | -406 | +659 | +354 | +1128 | -119 | +1682 | +354 | +1128 | yes |
| M5d9e7166 tm240 | long-only | A7 | -697 | +373 | -784 | +1047 | -373 | +931 | -784 | +1047 | no |
| L05222ff9 time_m_4 | both-side | A7 | -395 | +85 | +354 | +1123 | -122 | +1676 | +354 | +1123 | yes |
| M05222ff9 time_m_4 | long-only | A7 | -697 | -156 | -854 | +1067 | -376 | +922 | -854 | +1067 | no |
| L63ff9ae8 time_m_4 | both-side | A7 | -395 | +85 | +354 | +1123 | -122 | +1676 | +354 | +1123 | yes |
| M63ff9ae8 time_m_4 | long-only | A7 | -697 | -156 | -854 | +1067 | -376 | +922 | -854 | +1067 | no |
| L7c368a4f time_m_5 | both-side | A7 | -199 | +1810 | +464 | +1810 | -1260 | +3199 | +2228 | +5312 | yes |
| L30aad100 drb_3500 | both-side | A7 | -634 | +162 | +171 | +848 | -179 | +722 | +171 | +848 | yes |
| L5c9e11b3 vol_750 | both-side | A7 | -603 | +1062 | +3289 | +4781 | -1151 | +3460 | +3289 | +4781 | yes |
| M5c9e11b3 vol_750 | long-only | A7 | -306 | -6 | +540 | -204 | +164 | +959 | +540 | -204 | no |
| Ledfbf4d2 vol_350 | both-side | A7 | -459 | +384 | +4405 | +1029 | -548 | +1331 | +4405 | +1029 | yes |
| Medfbf4d2 vol_350 | long-only | A7 | -181 | -280 | +16 | -202 | +396 | +179 | +16 | -202 | no |
| L15f14deb tm120 | both-side | A7 | +261 | +707 | -110 | -3605 | +672 | +610 | -110 | -3605 | no |
| M15f14deb tm120 | long-only | A7 | -480 | +276 | +503 | +1733 | -176 | +390 | +503 | +1733 | yes |
| Lf77e374b tm240 | both-side | A7 | -403 | +1440 | +116 | +1728 | -202 | +2270 | +116 | +1728 | yes |
| Mf77e374b tm240 | long-only | A7 | -106 | -4 | -8104 | -6546 | +717 | +604 | -8104 | -6546 | no |
| L0b1d7882 tm30 | both-side | A7 | -65 | +395 | +861 | +904 | -152 | +1541 | +861 | +904 | yes |
| M0b1d7882 tm30 | long-only | A7 | -307 | -940 | -11474 | -4655 | -36 | +124 | -11474 | -4655 | no |

## GATE TABLE for every Asia beater (reconciles W-SHORT R0 and W-LAYERS gates; both are shown)
**Definitions.** persistence = share of 2-week windows since 2023-10 with positive result on the BARE both-side stream (grid screen, R per week at equal risk), gate > 0.60. R/wk = bare-stream R per week: L6M and each prior year 2023 / 2024 / 2025 (W-SHORT csv asia_bothside.csv). **Standing rule (outputs/CLAUDE.md; W-SHORT csv red2023..red2025 = True means RED):** a prior year is RED when its weekly mean is more than 30% worse than the cell's OWN L6M weekly mean (AMBER 15-30%); because the L6M is the best-of-many selection window nearly every selected cell is RED in some year - these flags say "the recent window is far hotter than earlier years", not "negative". **W-LAYERS rule:** a prior year is red only if it is NEGATIVE (R/wk < 0). **Engine colours (rule B, order 1122Z)** in the RULE B column: the stack WITH the new book (REPLACE row) vs TODAY'S stack (TL3_EV_JL3) in the SAME year; ulcer / max DD / worst week / $ per week worse by >30% = RED, 15-30% AMBER, else GREEN; "pending" = prior-year lines not landed (NOT fail). The standing flags and Gate B columns are rule A (screen, bare stream, only orders the queue). **Gate A (W-LAYERS)** = persistence > 0.60 AND no negative prior year. **Gate B (W-SHORT R0 / standing rule)** = persistence > 0.60 AND no RED year vs own L6M. Both are SCREEN gates; the engine decides, and nothing is CONFIRMED without 30 controls.

| cell | stream | book beaten | bare persistence | R/wk L6M | R/wk 2023 / 2024 / 2025 | RULE A (screen) flags 23/24/25 | any negative year | RULE B (engine) colours 23/24/25 | Gate A (W-LAYERS, screen) | Gate B (R0, screen rule A) |
|---|---|---|---|---|---|---|---|---|---|---|
| Lda55d973 vol_750 | both-side | A7 | 0.561 | +1.95 | +0.06 / +0.24 / +0.15 | RED / RED / RED | no | GREEN / AMBER / RED | fail | fail |
| Mda55d973 vol_750 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| La5b5d03a time_m_2 | both-side | A7 | 0.573 | +0.34 | +0.20 / +0.17 / -0.06 | RED / RED / RED | yes | RED / GREEN / GREEN | fail | fail |
| Ma5b5d03a time_m_2 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| Lcb276f27 tm120 | both-side | A7 | 0.573 | +0.20 | +0.19 / +0.20 / -0.03 | ok / ok / RED | yes | RED / GREEN / GREEN | fail | fail |
| Mcb276f27 tm120 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L1edb9fab tm300 | both-side | A7 | 0.500 | +1.16 | +0.07 / +0.49 / +0.22 | RED / RED / RED | no | GREEN / GREEN / RED | fail | fail |
| M1edb9fab tm300 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | GREEN / GREEN / RED | pending | pending |
| L0a809c2e kagi_40 | both-side | A7 | 0.549 | +0.86 | +0.20 / +0.01 / +0.45 | RED / RED / RED | no | GREEN / AMBER / RED | fail | fail |
| M0a809c2e kagi_40 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L17ce266f tm240 | both-side | A7 | 0.622 | +0.70 | +0.07 / +0.21 / +0.18 | RED / RED / RED | no | GREEN / AMBER / RED | PASS | fail |
| M17ce266f tm240 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | GREEN / AMBER / RED | pending | pending |
| L5d9e7166 tm240 | both-side | A7 | 0.622 | +0.70 | +0.07 / +0.21 / +0.18 | RED / RED / RED | no | GREEN / AMBER / RED | PASS | fail |
| M5d9e7166 tm240 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | GREEN / AMBER / RED | pending | pending |
| L05222ff9 time_m_4 | both-side | A7 | 0.598 | +0.74 | +0.08 / +0.18 / +0.26 | RED / RED / RED | no | GREEN / AMBER / RED | fail | fail |
| M05222ff9 time_m_4 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L63ff9ae8 time_m_4 | both-side | A7 | 0.598 | +0.74 | +0.08 / +0.18 / +0.26 | RED / RED / RED | no | pending / pending / pending | fail | fail |
| M63ff9ae8 time_m_4 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L7c368a4f time_m_5 | both-side | A7 | 0.537 | +1.17 | +0.07 / +0.48 / +0.26 | RED / RED / RED | no | GREEN / GREEN / RED | fail | fail |
| L30aad100 drb_3500 | both-side (both-mode cell) | A7 | n/a (not in the old-mode csv) | | | | | pending / pending / pending | pending | pending |
| L5c9e11b3 vol_750 | both-side | A7 | 0.622 | +1.36 | +0.35 / +0.63 / +0.42 | RED / RED / RED | no | GREEN / GREEN / RED | PASS | fail |
| M5c9e11b3 vol_750 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| Ledfbf4d2 vol_350 | both-side | A7 | 0.622 | +1.10 | +0.23 / +0.43 / +0.29 | RED / RED / RED | no | GREEN / GREEN / RED | PASS | fail |
| Medfbf4d2 vol_350 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L15f14deb tm120 | both-side | A7 | 0.634 | +0.85 | +0.08 / +0.17 / +0.53 | RED / RED / RED | no | pending / pending / pending | PASS | fail |
| M15f14deb tm120 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| Lf77e374b tm240 | both-side | A7 | 0.512 | +1.23 | +0.02 / +0.07 / -0.09 | RED / RED / RED | yes | AMBER / AMBER / RED | fail | fail |
| Mf77e374b tm240 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L0b1d7882 tm30 | both-side | A7 | 0.488 | +0.20 | +0.07 / +0.02 / -0.16 | RED / RED / RED | yes | GREEN / AMBER / RED | fail | fail |
| M0b1d7882 tm30 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |

Gate A pass 5, Gate B pass 0 among the both-side beaters listed (see MORNING.md for the reconciliation note). Short-only rows: none of the beating cells has screen mode short, so no short-only twin exists for them.

## RULE B TABLE (engine prior years, order 1122Z): stack WITH the new book (REPLACE row) vs TODAY'S stack in the same year
**Sign convention (all four % columns): positive = the new stack is WORSE than today's stack** (d ulcer % = ulcer higher; d max DD % = max drawdown deeper; d worst week % = worst week deeper (e.g. +10% = worst week is 10% more negative); d $/wk % = mean $/week lower). Negative = better. Colour = worst of the four: RED > 30%, AMBER 15-30%, else GREEN. **Overall verdict: any RED year under B = fails the prior-year gate**; years not landed = pending (not fail). Engine persistence = share of non-overlapping 2-week blocks (all months landed, 2023-04..2026-10) where REPLACE minus today's stack is >= 0; bare persistence (screen stream) shown beside it; gate > 0.60. Rule A colours (screen, bare stream: prior-year weekly R >30% worse than own L6M) are in their OWN column and only order the queue.

| cell | stream | book beaten | year | d ulcer % | d max DD % | d worst week % | d $/wk % (2025 = FIXED F-set numbers where landed) | RULE B colour (as run, contaminated 2025) | RULE B colour FIXED (F = F sets landed; diag = ex-artefact diagnostic while F sets pending) | RULE A colour (screen) | overall B verdict (as run / fixed) | engine persistence (blocks) | bare persistence |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
**NOTE (2025 REPLACE rows are an ENGINE ARTEFACT, not an A7 effect; W-ASIA 11:3xZ):** in the 2025 window ALL new-book sets (ADD rows too, not only REPLACE-A7) carry ONE MF1 trade on 2025-11-28 with gross -506,325 on 1 lot (exit_ns 2025-11-28 07:00:01Z: an exit at a time with no usable print, price ~0); 157 of the 184 Asia set-months landed for 202511 contain it, JL3 itself has none. It makes the 2025 worst week ~-$510k vs -$39k and gives the identical +410% ulcer / +550% max DD / +1,219% worst week across cells. Real 2025 stack: A7 earned +$49,829 in the Asia session in 2025 (304 trades), K7 +35,095, H7 +33,248, P7 +176,090, U7 +16,540 in JL3 (all five live books exist in the 2025 stack; JL3 is the SAME stack definition as today, run on 2025 data). The EX-ARTEFACT column removes the artefact trade(s) (gross < -$100k) and keeps everything else as run; it is a diagnostic, NOT a delivered number - the engine owners must fix the exit (events file exit_ts / price) and the sets be re-run. 2023/2024 are unaffected by the artefact.

| Lda55d973 vol_750 | both-side | A7 | 2023 | +1 | +10 | -3 | -7 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.53 (19); pooled 0.52 (93 blocks) fail | 0.561 |
| Lda55d973 vol_750 | both-side | A7 | 2024 | +3 | -1 | -14 | +16 | AMBER | AMBER (as run, no artefact) | RED |  | year 0.42 (26) |  |
| Lda55d973 vol_750 | both-side | A7 | 2025 | +13 | +24 | +7 | +4 | RED | AMBER (F) | RED |  | year 0.38 (26) |  |
| La5b5d03a time_m_2 | both-side | A7 | 2023 | +30 | +37 | +3 | -40 | RED | RED (as run, no artefact) | RED | RED / RED | year 0.53 (19); pooled 0.52 (93 blocks) fail | 0.573 |
| La5b5d03a time_m_2 | both-side | A7 | 2024 | +1 | +2 | -20 | +4 | GREEN | GREEN (as run, no artefact) | RED |  | year 0.46 (26) |  |
| La5b5d03a time_m_2 | both-side | A7 | 2025 | -14 | -3 | -10 | -2 | GREEN | GREEN (F) | RED |  | year 0.54 (26) |  |
| Lcb276f27 tm120 | both-side | A7 | 2023 | +30 | +37 | +3 | -41 | RED | RED (as run, no artefact) | ok | RED / RED | year 0.53 (19); pooled 0.53 (93 blocks) fail | 0.573 |
| Lcb276f27 tm120 | both-side | A7 | 2024 | +2 | +4 | -20 | +4 | GREEN | GREEN (as run, no artefact) | ok |  | year 0.46 (26) |  |
| Lcb276f27 tm120 | both-side | A7 | 2025 | -15 | -3 | -10 | -2 | GREEN | GREEN (F) | RED |  | year 0.54 (26) |  |
| L1edb9fab tm300 | both-side | A7 | 2023 | -4 | -2 | +5 | -19 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.58 (19); pooled 0.53 (93 blocks) fail | 0.500 |
| L1edb9fab tm300 | both-side | A7 | 2024 | -5 | -8 | -17 | +4 | GREEN | GREEN (as run, no artefact) | RED |  | year 0.35 (26) |  |
| L1edb9fab tm300 | both-side | A7 | 2025 | +3 | +6 | +5 | +7 | RED | GREEN (F) | RED |  | year 0.42 (26) |  |
| L0a809c2e kagi_40 | both-side | A7 | 2023 | -13 | -7 | -4 | -35 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.63 (19); pooled 0.56 (93 blocks) fail | 0.549 |
| L0a809c2e kagi_40 | both-side | A7 | 2024 | +21 | -2 | -14 | +20 | AMBER | AMBER (as run, no artefact) | RED |  | year 0.27 (26) |  |
| L0a809c2e kagi_40 | both-side | A7 | 2025 | +6 | +7 | -2 | +4 | RED | GREEN (F) | RED |  | year 0.50 (26) |  |
| L17ce266f tm240 | both-side | A7 | 2023 | +5 | +10 | -2 | -17 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.53 (19); pooled 0.51 (93 blocks) fail | 0.622 |
| L17ce266f tm240 | both-side | A7 | 2024 | +8 | -3 | -14 | +16 | AMBER | AMBER (as run, no artefact) | RED |  | year 0.35 (26) |  |
| L17ce266f tm240 | both-side | A7 | 2025 | -0 | -1 | +9 | +10 | RED | GREEN (F) | RED |  | year 0.35 (26) |  |
| L5d9e7166 tm240 | both-side | A7 | 2023 | +5 | +10 | -2 | -17 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.53 (19); pooled 0.51 (93 blocks) fail | 0.622 |
| L5d9e7166 tm240 | both-side | A7 | 2024 | +8 | -3 | -14 | +16 | AMBER | AMBER (as run, no artefact) | RED |  | year 0.35 (26) |  |
| L5d9e7166 tm240 | both-side | A7 | 2025 | -0 | -1 | +9 | +10 | RED | GREEN (F) | RED |  | year 0.35 (26) |  |
| L05222ff9 time_m_4 | both-side | A7 | 2023 | +5 | +10 | -2 | -17 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.53 (19); pooled 0.51 (93 blocks) fail | 0.598 |
| L05222ff9 time_m_4 | both-side | A7 | 2024 | +8 | -4 | -14 | +17 | AMBER | AMBER (as run, no artefact) | RED |  | year 0.35 (26) |  |
| L05222ff9 time_m_4 | both-side | A7 | 2025 | -0 | -1 | +9 | +9 | RED | GREEN (F) | RED |  | year 0.35 (26) |  |
| L7c368a4f time_m_5 | both-side | A7 | 2023 | -5 | -2 | +4 | -19 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.58 (19); pooled 0.53 (93 blocks) fail | 0.537 |
| L7c368a4f time_m_5 | both-side | A7 | 2024 | -6 | -8 | -17 | +1 | GREEN | GREEN (as run, no artefact) | RED |  | year 0.35 (26) |  |
| L7c368a4f time_m_5 | both-side | A7 | 2025 | +4 | +5 | +5 | +9 | RED | GREEN (F) | RED |  | year 0.42 (26) |  |
| L5c9e11b3 vol_750 | both-side | A7 | 2023 | -1 | +1 | +1 | -31 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.68 (19); pooled 0.58 (93 blocks) PASS | 0.622 |
| L5c9e11b3 vol_750 | both-side | A7 | 2024 | +5 | +1 | -13 | +7 | GREEN | GREEN (as run, no artefact) | RED |  | year 0.46 (26) |  |
| L5c9e11b3 vol_750 | both-side | A7 | 2025 | +7 | +17 | +2 | -4 | RED | AMBER (F) | RED |  | year 0.42 (26) |  |
| Ledfbf4d2 vol_350 | both-side | A7 | 2023 | +1 | +7 | -3 | -21 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.58 (19); pooled 0.53 (93 blocks) fail | 0.622 |
| Ledfbf4d2 vol_350 | both-side | A7 | 2024 | -1 | -4 | -11 | +6 | GREEN | GREEN (as run, no artefact) | RED |  | year 0.38 (26) |  |
| Ledfbf4d2 vol_350 | both-side | A7 | 2025 | +11 | +14 | +7 | +9 | RED | GREEN (F) | RED |  | year 0.35 (26) |  |
| Lf77e374b tm240 | both-side | A7 | 2023 | +13 | +18 | -4 | -4 | AMBER | AMBER (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.47 (19); pooled 0.48 (93 blocks) fail | 0.512 |
| Lf77e374b tm240 | both-side | A7 | 2024 | +4 | -6 | -11 | +20 | AMBER | AMBER (as run, no artefact) | RED |  | year 0.38 (26) |  |
| Lf77e374b tm240 | both-side | A7 | 2025 | +5 | +7 | +1 | +16 | RED | AMBER (F) | RED |  | year 0.31 (26) |  |
| L0b1d7882 tm30 | both-side | A7 | 2023 | -10 | -6 | -0 | -21 | GREEN | GREEN (as run, no artefact) | RED | RED / no RED, all 3 years | year 0.53 (19); pooled 0.46 (93 blocks) fail | 0.488 |
| L0b1d7882 tm30 | both-side | A7 | 2024 | +4 | -13 | -9 | +21 | AMBER | AMBER (as run, no artefact) | RED |  | year 0.38 (26) |  |
| L0b1d7882 tm30 | both-side | A7 | 2025 | +4 | -2 | +7 | +15 | RED | GREEN (F) | RED |  | year 0.35 (26) |  |
**Prior years against ALL live Asia books and ADD (where the A7-removal effect is absent or different): both-side beaters, rule B colours as run / ex-artefact, landed years only (pending = not run).**

| cell | variant | 2023 as run / ex-art | 2024 as run / ex-art | 2025 as run / ex-art |
|---|---|---|---|---|
| Lda55d973 vol_750 (both-side) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| Lda55d973 vol_750 (both-side) | RA7 | GREEN / GREEN diag | AMBER / AMBER diag | RED / AMBER F |
| La5b5d03a time_m_2 (both-side) | ADD | RED / RED diag | GREEN / GREEN diag | GREEN / GREEN F |
| La5b5d03a time_m_2 (both-side) | RA7 | RED / RED diag | GREEN / GREEN diag | GREEN / GREEN F |
| Ma5b5d03a time_m_2 (long-only) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | GREEN / GREEN diag |
| Lcb276f27 tm120 (both-side) | ADD | RED / RED diag | GREEN / GREEN diag | GREEN / GREEN F |
| Lcb276f27 tm120 (both-side) | RA7 | RED / RED diag | GREEN / GREEN diag | GREEN / GREEN F |
| Mcb276f27 tm120 (long-only) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | GREEN / GREEN diag |
| L1edb9fab tm300 (both-side) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| L1edb9fab tm300 (both-side) | RA7 | GREEN / GREEN diag | GREEN / GREEN diag | RED / GREEN F |
| L1edb9fab tm300 (both-side) | RH7 | RED / RED diag | GREEN / GREEN diag | RED / GREEN F |
| L1edb9fab tm300 (both-side) | RU7 | AMBER / AMBER diag | GREEN / GREEN diag | RED / GREEN F |
| M1edb9fab tm300 (long-only) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| M1edb9fab tm300 (long-only) | RA7 | GREEN / GREEN diag | GREEN / GREEN diag | RED / GREEN F |
| L0a809c2e kagi_40 (both-side) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| L0a809c2e kagi_40 (both-side) | RA7 | GREEN / GREEN diag | AMBER / AMBER diag | RED / GREEN F |
| L17ce266f tm240 (both-side) | ADD | AMBER / AMBER diag | GREEN / GREEN diag | RED / AMBER F |
| L17ce266f tm240 (both-side) | RA7 | GREEN / GREEN diag | AMBER / AMBER diag | RED / GREEN F |
| M17ce266f tm240 (long-only) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| M17ce266f tm240 (long-only) | RA7 | GREEN / GREEN diag | AMBER / AMBER diag | RED / GREEN F |
| L5d9e7166 tm240 (both-side) | ADD | AMBER / AMBER diag | GREEN / GREEN diag | RED / AMBER F |
| L5d9e7166 tm240 (both-side) | RA7 | GREEN / GREEN diag | AMBER / AMBER diag | RED / GREEN F |
| M5d9e7166 tm240 (long-only) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| M5d9e7166 tm240 (long-only) | RA7 | GREEN / GREEN diag | AMBER / AMBER diag | RED / GREEN F |
| L05222ff9 time_m_4 (both-side) | ADD | AMBER / AMBER diag | GREEN / GREEN diag | RED / AMBER F |
| L05222ff9 time_m_4 (both-side) | RA7 | GREEN / GREEN diag | AMBER / AMBER diag | RED / GREEN F |
| L7c368a4f time_m_5 (both-side) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| L7c368a4f time_m_5 (both-side) | RA7 | GREEN / GREEN diag | GREEN / GREEN diag | RED / GREEN F |
| L7c368a4f time_m_5 (both-side) | RH7 | RED / RED diag | GREEN / GREEN diag | RED / GREEN F |
| L7c368a4f time_m_5 (both-side) | RU7 | AMBER / AMBER diag | GREEN / GREEN diag | RED / GREEN F |
| L5c9e11b3 vol_750 (both-side) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| L5c9e11b3 vol_750 (both-side) | RA7 | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| L5c9e11b3 vol_750 (both-side) | RH7 | RED / RED diag | GREEN / GREEN diag | RED / AMBER F |
| M5c9e11b3 vol_750 (long-only) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| Ledfbf4d2 vol_350 (both-side) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / AMBER F |
| Ledfbf4d2 vol_350 (both-side) | RA7 | GREEN / GREEN diag | GREEN / GREEN diag | RED / GREEN F |
| M15f14deb tm120 (long-only) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / GREEN F |
| Lf77e374b tm240 (both-side) | ADD | AMBER / AMBER diag | GREEN / GREEN diag | RED / AMBER F |
| Lf77e374b tm240 (both-side) | RA7 | AMBER / AMBER diag | AMBER / AMBER diag | RED / AMBER F |
| L0b1d7882 tm30 (both-side) | ADD | GREEN / GREEN diag | GREEN / GREEN diag | RED / GREEN F |
| L0b1d7882 tm30 (both-side) | RA7 | GREEN / GREEN diag | AMBER / AMBER diag | RED / GREEN F |


Rule B so far: as run 13 beater/book rows with >= 1 engine prior year landed have a RED year, 0 none; FIXED (F sets where landed, else diag) 2 RED, 11 none. Rows without any landed engine prior year are not listed (pending).

## THREE STACKS side by side: today / REPLACE (candidate) / ADD (reference, not a candidate) - order 1407Z REPLACE ONLY
**Sign convention:** stack levels (ulcer index in $, max DD and worst week in $ (negative = loss), mean $/week), base lots, $4.84 RT; 2025 uses the capped F sets. Lower ulcer, shallower (less negative) max DD / worst week and higher $/wk = better. **REPLACE = new book ON and the beaten live Asia book (A7 / K7 / P7 / H7 / U7) OFF - the ONLY kind of candidate (Josh, 1407Z: no add-ons).** The ADD column is a REFERENCE (reference, not a candidate): an ADD yes row alone is never a candidate.
**CANDIDATE RULE:** a REPLACE row beats today's stack on L6M with L3M (drawdown first, then dollars; Asia rule), no RED prior year (rule B, engine, same-year stack vs today's, 2025 capped F sets), engine persistence >= 0.58 on the REPLACE row (pooled, non-overlapping 2-week blocks), then 30 date-shift controls, layers, exit run.

| cell | window | ulcer today / REPLACE / ADD (reference) | max DD today / REPLACE / ADD | worst week today / REPLACE / ADD | $/wk today / REPLACE / ADD | stack |
|---|---|---|---|---|---|---|
| Lda55d973 vol_750 (both-side, REPLACE A7) | L6M | 9416 / 8195 / 7745 | -31109 / -29500 / -22647 | -15728 / -14097 / -14127 | 18755 / 19666 / 21015 |  |
| Lda55d973 vol_750 (both-side, REPLACE A7) | L3M | 11035 / 9619 / 8770 | -31109 / -29500 / -22647 | -15728 / -14097 / -9140 | 16098 / 18241 / 18064 |  |
| Lda55d973 vol_750 (both-side, REPLACE A7) | Y2023 | 18991 / 19175 / 19096 | -41848 / -45906 / -44288 | -17538 / -16947 / -19057 | 1797 / 1921 / 1922 |  |
| Lda55d973 vol_750 (both-side, REPLACE A7) | Y2024 | 28814 / 29702 / 25627 | -72026 / -71193 / -62728 | -37355 / -32036 / -32439 | 4549 / 3834 / 4923 |  |
| Lda55d973 vol_750 (both-side, REPLACE A7) | Y2025 | 33556 / 37946 / 35725 | -91441 / -113113 / -113679 | -38896 / -41753 / -44336 | 6846 / 6585 / 7285 | F |
| La5b5d03a time_m_2 (both-side, REPLACE A7) | L6M | 9416 / 8219 / 9639 | -31109 / -29679 / -31748 | -15728 / -12219 / -21575 | 18755 / 20302 / 19240 |  |
| La5b5d03a time_m_2 (both-side, REPLACE A7) | L3M | 11035 / 10143 / 11498 | -31109 / -29679 / -31748 | -15728 / -12219 / -15732 | 16098 / 17137 / 16048 |  |
| La5b5d03a time_m_2 (both-side, REPLACE A7) | Y2023 | 18991 / 24777 / 26951 | -41848 / -57457 / -58490 | -17538 / -18118 / -17960 | 1797 / 2512 / 2356 |  |
| La5b5d03a time_m_2 (both-side, REPLACE A7) | Y2024 | 28814 / 29111 / 28438 | -72026 / -73724 / -72100 | -37355 / -29759 / -30869 | 4549 / 4388 / 5328 |  |
| La5b5d03a time_m_2 (both-side, REPLACE A7) | Y2025 | 33556 / 28847 / 31307 | -91441 / -88307 / -87217 | -38896 / -34886 / -35196 | 6846 / 6955 / 7487 | F |
| Lcb276f27 tm120 (both-side, REPLACE A7) | L6M | 9416 / 8270 / 9685 | -31109 / -29694 / -31768 | -15728 / -12257 / -21585 | 18755 / 20322 / 19627 |  |
| Lcb276f27 tm120 (both-side, REPLACE A7) | L3M | 11035 / 10225 / 11581 | -31109 / -29694 / -31768 | -15728 / -12257 / -15742 | 16098 / 17183 / 16117 |  |
| Lcb276f27 tm120 (both-side, REPLACE A7) | Y2023 | 18991 / 24695 / 26845 | -41848 / -57137 / -58140 | -17538 / -18118 / -17990 | 1797 / 2531 / 2376 |  |
| Lcb276f27 tm120 (both-side, REPLACE A7) | Y2024 | 28814 / 29396 / 28746 | -72026 / -74814 / -73190 | -37355 / -29989 / -30974 | 4549 / 4377 / 5352 |  |
| Lcb276f27 tm120 (both-side, REPLACE A7) | Y2025 | 33556 / 28618 / 31058 | -91441 / -88282 / -87157 | -38896 / -34881 / -35191 | 6846 / 6971 / 7544 | F |
| L1edb9fab tm300 (both-side, REPLACE A7) | L6M | 9416 / 9274 / 10163 | -31109 / -31011 / -37086 | -15728 / -15264 / -16662 | 18755 / 20362 / 20609 |  |
| L1edb9fab tm300 (both-side, REPLACE A7) | L3M | 11035 / 9783 / 10624 | -31109 / -25803 / -25041 | -15728 / -13525 / -11246 | 16098 / 19182 / 17304 |  |
| L1edb9fab tm300 (both-side, REPLACE A7) | Y2023 | 18991 / 18137 / 18881 | -41848 / -40902 / -43977 | -17538 / -18327 / -18506 | 1797 / 2139 / 1999 |  |
| L1edb9fab tm300 (both-side, REPLACE A7) | Y2024 | 28814 / 27362 / 24465 | -72026 / -66000 / -59332 | -37355 / -30929 / -32855 | 4549 / 4367 / 5381 |  |
| L1edb9fab tm300 (both-side, REPLACE A7) | Y2025 | 33556 / 34416 / 34798 | -91441 / -96476 / -105421 | -38896 / -40930 / -40400 | 6846 / 6338 / 6879 | F |
| L0a809c2e kagi_40 (both-side, REPLACE A7) | L6M | 9416 / 8627 / 9370 | -31109 / -26693 / -31595 | -15728 / -15409 / -25014 | 18755 / 19157 / 20194 |  |
| L0a809c2e kagi_40 (both-side, REPLACE A7) | L3M | 11035 / 9538 / 9436 | -31109 / -26272 / -26449 | -15728 / -15409 / -13124 | 16098 / 17127 / 17396 |  |
| L0a809c2e kagi_40 (both-side, REPLACE A7) | Y2023 | 19004 / 16501 / 17070 | -41848 / -38958 / -42033 | -17538 / -16807 / -17907 | 1797 / 2430 / 2317 |  |
| L0a809c2e kagi_40 (both-side, REPLACE A7) | Y2024 | 28814 / 34848 / 29153 | -72026 / -70796 / -64528 | -37355 / -32010 / -35542 | 4549 / 3639 / 4650 |  |
| L0a809c2e kagi_40 (both-side, REPLACE A7) | Y2025 | 33556 / 35493 / 36896 | -91441 / -97750 / -107172 | -38896 / -38128 / -38482 | 6846 / 6555 / 7059 | F |
| L17ce266f tm240 (both-side, REPLACE A7) | L6M | 9416 / 9011 / 9901 | -31109 / -29981 / -31550 | -15728 / -15374 / -31550 | 18755 / 19414 / 19798 |  |
| L17ce266f tm240 (both-side, REPLACE A7) | L3M | 11035 / 10916 / 10148 | -31109 / -29981 / -25424 | -15728 / -15374 / -16179 | 16098 / 17780 / 17530 |  |
| L17ce266f tm240 (both-side, REPLACE A7) | Y2023 | 18991 / 19886 / 20586 | -41848 / -46162 / -49237 | -17538 / -17187 / -20012 | 1797 / 2101 / 1941 |  |
| L17ce266f tm240 (both-side, REPLACE A7) | Y2024 | 28814 / 31087 / 25259 | -72026 / -69545 / -60607 | -37355 / -32291 / -34218 | 4549 / 3817 / 4989 |  |
| L17ce266f tm240 (both-side, REPLACE A7) | Y2025 | 33556 / 33519 / 37319 | -91441 / -90338 / -107192 | -38896 / -42502 / -44906 | 6846 / 6171 / 6271 | F |
| L5d9e7166 tm240 (both-side, REPLACE A7) | L6M | 9416 / 9011 / 9901 | -31109 / -29981 / -31550 | -15728 / -15374 / -31550 | 18755 / 19414 / 19798 |  |
| L5d9e7166 tm240 (both-side, REPLACE A7) | L3M | 11035 / 10916 / 10148 | -31109 / -29981 / -25424 | -15728 / -15374 / -16179 | 16098 / 17780 / 17530 |  |
| L5d9e7166 tm240 (both-side, REPLACE A7) | Y2023 | 18991 / 19886 / 20586 | -41848 / -46162 / -49237 | -17538 / -17187 / -20012 | 1797 / 2101 / 1941 |  |
| L5d9e7166 tm240 (both-side, REPLACE A7) | Y2024 | 28814 / 31087 / 25259 | -72026 / -69545 / -60607 | -37355 / -32291 / -34218 | 4549 / 3817 / 4989 |  |
| L5d9e7166 tm240 (both-side, REPLACE A7) | Y2025 | 33556 / 33519 / 37319 | -91441 / -90338 / -107192 | -38896 / -42502 / -44906 | 6846 / 6171 / 6271 | F |
| L05222ff9 time_m_4 (both-side, REPLACE A7) | L6M | 9416 / 9021 / 9913 | -31109 / -29986 / -31545 | -15728 / -15374 / -31545 | 18755 / 18840 / 19219 |  |
| L05222ff9 time_m_4 (both-side, REPLACE A7) | L3M | 11035 / 10913 / 10151 | -31109 / -29986 / -25429 | -15728 / -15374 / -16179 | 16098 / 17775 / 17511 |  |
| L05222ff9 time_m_4 (both-side, REPLACE A7) | Y2023 | 18991 / 19866 / 20567 | -41848 / -46132 / -49207 | -17538 / -17182 / -20022 | 1797 / 2103 / 1943 |  |
| L05222ff9 time_m_4 (both-side, REPLACE A7) | Y2024 | 28814 / 31076 / 25264 | -72026 / -69490 / -60612 | -37355 / -32286 / -34213 | 4549 / 3790 / 4927 |  |
| L05222ff9 time_m_4 (both-side, REPLACE A7) | Y2025 | 33556 / 33399 / 37156 | -91441 / -90193 / -107052 | -38896 / -42472 / -44876 | 6846 / 6224 / 6326 | F |
| L63ff9ae8 time_m_4 (both-side, REPLACE A7) | L6M | 9416 / 9021 / 9913 | -31109 / -29986 / -31545 | -15728 / -15374 / -31545 | 18755 / 18840 / 19219 |  |
| L63ff9ae8 time_m_4 (both-side, REPLACE A7) | L3M | 11035 / 10913 / 10151 | -31109 / -29986 / -25429 | -15728 / -15374 / -16179 | 16098 / 17775 / 17511 |  |
| L7c368a4f time_m_5 (both-side, REPLACE A7) | L6M | 9416 / 9218 / 10098 | -31109 / -29299 / -36110 | -15728 / -15264 / -16662 | 18755 / 20565 / 20774 |  |
| L7c368a4f time_m_5 (both-side, REPLACE A7) | L3M | 11035 / 9775 / 10581 | -31109 / -25798 / -25056 | -15728 / -13500 / -11241 | 16098 / 19297 / 17339 |  |
| L7c368a4f time_m_5 (both-side, REPLACE A7) | Y2023 | 18991 / 18122 / 18878 | -41848 / -40922 / -43997 | -17538 / -18322 / -18511 | 1797 / 2139 / 1999 |  |
| L7c368a4f time_m_5 (both-side, REPLACE A7) | Y2024 | 28814 / 27024 / 24468 | -72026 / -66110 / -59717 | -37355 / -30909 / -32835 | 4549 / 4483 / 5415 |  |
| L7c368a4f time_m_5 (both-side, REPLACE A7) | Y2025 | 33556 / 34826 / 35124 | -91441 / -95951 / -105616 | -38896 / -40970 / -40440 | 6846 / 6203 / 6782 | F |
| L30aad100 drb_3500 (both-side, REPLACE A7) | L6M | 9416 / 8782 / 10280 | -31109 / -30261 / -31379 | -15728 / -15557 / -30239 | 18755 / 18917 / 18816 |  |
| L30aad100 drb_3500 (both-side, REPLACE A7) | L3M | 11035 / 10856 / 10925 | -31109 / -30261 / -28137 | -15728 / -15557 / -16796 | 16098 / 16820 / 16631 |  |
| L5c9e11b3 vol_750 (both-side, REPLACE A7) | L6M | 9416 / 8813 / 8601 | -31109 / -26328 / -27858 | -15728 / -12439 / -15772 | 18755 / 19817 / 20907 |  |
| L5c9e11b3 vol_750 (both-side, REPLACE A7) | L3M | 11035 / 9884 / 9329 | -31109 / -26328 / -24369 | -15728 / -12439 / -12241 | 16098 / 19559 / 19669 |  |
| L5c9e11b3 vol_750 (both-side, REPLACE A7) | Y2023 | 18991 / 18750 / 19212 | -41848 / -42077 / -45152 | -17538 / -17707 / -18947 | 1797 / 2352 / 2228 |  |
| L5c9e11b3 vol_750 (both-side, REPLACE A7) | Y2024 | 28814 / 30111 / 24611 | -72026 / -72566 / -62720 | -37355 / -32622 / -34549 | 4549 / 4220 / 5342 |  |
| L5c9e11b3 vol_750 (both-side, REPLACE A7) | Y2025 | 33556 / 35843 / 35608 | -91441 / -106894 / -113510 | -38896 / -39636 / -42066 | 6846 / 7130 / 7770 | F |
| Ledfbf4d2 vol_350 (both-side, REPLACE A7) | L6M | 9416 / 8957 / 8603 | -31109 / -30080 / -26839 | -15728 / -11323 / -17813 | 18755 / 19139 / 19635 |  |
| Ledfbf4d2 vol_350 (both-side, REPLACE A7) | L3M | 11035 / 10487 / 10086 | -31109 / -30080 / -26839 | -15728 / -11323 / -9580 | 16098 / 17429 / 16163 |  |
| Ledfbf4d2 vol_350 (both-side, REPLACE A7) | Y2023 | 18991 / 19189 / 19096 | -41848 / -44944 / -47700 | -17538 / -17087 / -17617 | 1797 / 2176 / 2291 |  |
| Ledfbf4d2 vol_350 (both-side, REPLACE A7) | Y2024 | 28814 / 28653 / 23857 | -72026 / -69473 / -58554 | -37355 / -33229 / -35156 | 4549 / 4294 / 5293 |  |
| Ledfbf4d2 vol_350 (both-side, REPLACE A7) | Y2025 | 33556 / 37173 / 36640 | -91441 / -104424 / -110691 | -38896 / -41671 / -44101 | 6846 / 6245 / 6674 | F |
| M15f14deb tm120 (long-only, REPLACE A7) | L6M | 9416 / 8936 / 9941 | -31109 / -29376 / -30873 | -15728 / -15225 / -15183 | 18755 / 19032 / 19379 |  |
| M15f14deb tm120 (long-only, REPLACE A7) | L3M | 11035 / 10859 / 11593 | -31109 / -29376 / -28061 | -15728 / -15225 / -13868 | 16098 / 16488 / 16181 |  |
| Lf77e374b tm240 (both-side, REPLACE A7) | L6M | 9416 / 9014 / 10535 | -31109 / -29381 / -36037 | -15728 / -15612 / -15101 | 18755 / 20195 / 19289 |  |
| Lf77e374b tm240 (both-side, REPLACE A7) | L3M | 11035 / 10833 / 11408 | -31109 / -29381 / -28600 | -15728 / -15612 / -15101 | 16098 / 18368 / 15821 |  |
| Lf77e374b tm240 (both-side, REPLACE A7) | Y2023 | 18991 / 21481 / 22332 | -41848 / -49287 / -49606 | -17538 / -16922 / -18221 | 1797 / 1864 / 1700 |  |
| Lf77e374b tm240 (both-side, REPLACE A7) | Y2024 | 28814 / 30058 / 25689 | -72026 / -68000 / -62279 | -37355 / -33073 / -34617 | 4549 / 3650 / 4853 |  |
| Lf77e374b tm240 (both-side, REPLACE A7) | Y2025 | 33556 / 35122 / 36470 | -91441 / -98122 / -110008 | -38896 / -39091 / -38679 | 6846 / 5733 / 6045 | F |
| L0b1d7882 tm30 (both-side, REPLACE A7) | L6M | 9416 / 9351 / 10198 | -31109 / -30206 / -36661 | -15728 / -14867 / -16848 | 18755 / 19150 / 19055 |  |
| L0b1d7882 tm30 (both-side, REPLACE A7) | L3M | 11035 / 10883 / 11074 | -31109 / -30206 / -27479 | -15728 / -14867 / -13046 | 16098 / 17640 / 16823 |  |
| L0b1d7882 tm30 (both-side, REPLACE A7) | Y2023 | 18991 / 17138 / 17729 | -41848 / -39476 / -39506 | -17538 / -17472 / -17947 | 1797 / 2172 / 2018 |  |
| L0b1d7882 tm30 (both-side, REPLACE A7) | Y2024 | 28814 / 30043 / 24602 | -72026 / -62531 / -58008 | -37355 / -34134 / -35899 | 4549 / 3574 / 4733 |  |
| L0b1d7882 tm30 (both-side, REPLACE A7) | Y2025 | 33556 / 35011 / 35301 | -91441 / -89401 / -99605 | -38896 / -41705 / -44544 | 6846 / 5839 / 6689 | F |

## REPLACE PASS LIST (provisional): REPLACE row beats today on L6M+L3M + no RED prior year (rule B) + engine persistence >= 0.58

| cell | stream | live book REPLACED | L6M / L3M beats today | prior years rule B (F-fixed 2025) | engine persistence pooled (>= 0.58) | PASS so far | still needs |
|---|---|---|---|---|---|---|---|
| Lda55d973 vol_750 | both-side | A7 | yes / yes | 2023 GREEN / 2024 AMBER / 2025 AMBER | 0.52 (93) fail | fail | - |
| La5b5d03a time_m_2 | both-side | A7 | yes / yes | 2023 RED / 2024 GREEN / 2025 GREEN | 0.52 (93) fail | fail | - |
| Lcb276f27 tm120 | both-side | A7 | yes / yes | 2023 RED / 2024 GREEN / 2025 GREEN | 0.53 (93) fail | fail | - |
| L1edb9fab tm300 | both-side | A7 | yes / yes | 2023 GREEN / 2024 GREEN / 2025 GREEN | 0.53 (93) fail | fail | - |
| L0a809c2e kagi_40 | both-side | A7 | yes / yes | 2023 GREEN / 2024 AMBER / 2025 GREEN | 0.56 (93) fail | fail | - |
| L17ce266f tm240 | both-side | A7 | yes / yes | 2023 GREEN / 2024 AMBER / 2025 GREEN | 0.51 (93) fail | fail | - |
| L5d9e7166 tm240 | both-side | A7 | yes / yes | 2023 GREEN / 2024 AMBER / 2025 GREEN | 0.51 (93) fail | fail | - |
| L05222ff9 time_m_4 | both-side | A7 | yes / yes | 2023 GREEN / 2024 AMBER / 2025 GREEN | 0.51 (93) fail | fail | - |
| L63ff9ae8 time_m_4 | both-side | A7 | yes / yes | pending | 0.54 (13) fail | fail | - |
| L7c368a4f time_m_5 | both-side | A7 | yes / yes | 2023 GREEN / 2024 GREEN / 2025 GREEN | 0.53 (93) fail | fail | - |
| L30aad100 drb_3500 | both-side | A7 | yes / yes | pending | 0.38 (13) fail | fail | - |
| L5c9e11b3 vol_750 | both-side | A7 | yes / yes | 2023 GREEN / 2024 GREEN / 2025 AMBER | 0.58 (93) PASS | PASS (3 prior years landed) | 30 controls of the REPLACE set; layers (W-LAYERS); exit run (D8_EXIT_SCREEN.md) |
| Ledfbf4d2 vol_350 | both-side | A7 | yes / yes | 2023 GREEN / 2024 GREEN / 2025 GREEN | 0.53 (93) fail | fail | - |
| M15f14deb tm120 | long-only | A7 | yes / yes | pending | 0.51 (67) fail | fail | - |
| Lf77e374b tm240 | both-side | A7 | yes / yes | 2023 AMBER / 2024 AMBER / 2025 AMBER | 0.48 (93) fail | fail | - |
| L0b1d7882 tm30 | both-side | A7 | yes / yes | 2023 GREEN / 2024 AMBER / 2025 GREEN | 0.46 (93) fail | fail | - |
## STRICT TABLE (Asia REPLACE rows; strict criterion = on BOTH L6M and L3M: stack ulcer lower AND $/wk not lower AND worst week not worse AND max DD not worse; no name exemptions)

**Counts (REPLACE first looks with L6M+L3M landed, distinct streams): 888 rows; STRICT pass 16; LOOSER (NY rule: ulcer lower and $/wk not lower only) pass 46; failing exactly ONE strict criterion 15.** (16 REPLACE-yes rows below = the strict recent-months passers; every one still has to clear no-RED-prior-year and engine persistence >= 0.58 to be a candidate).

Sign: d = REPLACE stack minus today's stack; for ulcer lower (negative d) is better; for $/wk, worst week, max DD higher (positive d) is better (worst week / max DD are negative levels, so d > 0 = shallower).

| cell | live book | window | d ulcer | d $/wk | d worst week | d max DD | ulcer lower | $/wk not lower | worst wk not worse | max DD not worse | recent-months verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Lda55d973 | A7 | L6M | -1222 | +911 | +1631 | +1609 | pass | pass | pass | pass | STRICT PASS |
| Lda55d973 | A7 | L3M | -1416 | +2143 | +1631 | +1609 | pass | pass | pass | pass | STRICT PASS |
| La5b5d03a | A7 | L6M | -1197 | +1547 | +3509 | +1430 | pass | pass | pass | pass | STRICT PASS |
| La5b5d03a | A7 | L3M | -892 | +1038 | +3509 | +1430 | pass | pass | pass | pass | STRICT PASS |
| Lcb276f27 | A7 | L6M | -1146 | +1567 | +3471 | +1415 | pass | pass | pass | pass | STRICT PASS |
| Lcb276f27 | A7 | L3M | -811 | +1085 | +3471 | +1415 | pass | pass | pass | pass | STRICT PASS |
| L0a809c2e | A7 | L6M | -789 | +402 | +319 | +4417 | pass | pass | pass | pass | STRICT PASS |
| L0a809c2e | A7 | L3M | -1498 | +1029 | +319 | +4837 | pass | pass | pass | pass | STRICT PASS |
| L30aad100 | A7 | L6M | -634 | +162 | +171 | +848 | pass | pass | pass | pass | STRICT PASS |
| L30aad100 | A7 | L3M | -179 | +722 | +171 | +848 | pass | pass | pass | pass | STRICT PASS |
| L5c9e11b3 | A7 | L6M | -603 | +1062 | +3289 | +4781 | pass | pass | pass | pass | STRICT PASS |
| L5c9e11b3 | A7 | L3M | -1151 | +3460 | +3289 | +4781 | pass | pass | pass | pass | STRICT PASS |
| M15f14deb | A7 | L6M | -480 | +276 | +503 | +1733 | pass | pass | pass | pass | STRICT PASS |
| M15f14deb | A7 | L3M | -176 | +390 | +503 | +1733 | pass | pass | pass | pass | STRICT PASS |
| Ledfbf4d2 | A7 | L6M | -459 | +384 | +4405 | +1029 | pass | pass | pass | pass | STRICT PASS |
| Ledfbf4d2 | A7 | L3M | -548 | +1331 | +4405 | +1029 | pass | pass | pass | pass | STRICT PASS |
| L5d9e7166 | A7 | L6M | -406 | +659 | +354 | +1128 | pass | pass | pass | pass | STRICT PASS |
| L5d9e7166 | A7 | L3M | -119 | +1682 | +354 | +1128 | pass | pass | pass | pass | STRICT PASS |
| L17ce266f | A7 | L6M | -406 | +659 | +354 | +1128 | pass | pass | pass | pass | STRICT PASS |
| L17ce266f | A7 | L3M | -119 | +1682 | +354 | +1128 | pass | pass | pass | pass | STRICT PASS |
| Lf77e374b | A7 | L6M | -403 | +1440 | +116 | +1728 | pass | pass | pass | pass | STRICT PASS |
| Lf77e374b | A7 | L3M | -202 | +2270 | +116 | +1728 | pass | pass | pass | pass | STRICT PASS |
| L63ff9ae8 | A7 | L6M | -395 | +85 | +354 | +1123 | pass | pass | pass | pass | STRICT PASS |
| L63ff9ae8 | A7 | L3M | -122 | +1676 | +354 | +1123 | pass | pass | pass | pass | STRICT PASS |
| L05222ff9 | A7 | L6M | -395 | +85 | +354 | +1123 | pass | pass | pass | pass | STRICT PASS |
| L05222ff9 | A7 | L3M | -122 | +1676 | +354 | +1123 | pass | pass | pass | pass | STRICT PASS |
| L7c368a4f | A7 | L6M | -199 | +1810 | +464 | +1810 | pass | pass | pass | pass | STRICT PASS |
| L7c368a4f | A7 | L3M | -1260 | +3199 | +2228 | +5312 | pass | pass | pass | pass | STRICT PASS |
| L1edb9fab | A7 | L6M | -142 | +1606 | +464 | +98 | pass | pass | pass | pass | STRICT PASS |
| L1edb9fab | A7 | L3M | -1252 | +3083 | +2203 | +5307 | pass | pass | pass | pass | STRICT PASS |
| L0b1d7882 | A7 | L6M | -65 | +395 | +861 | +904 | pass | pass | pass | pass | STRICT PASS |
| L0b1d7882 | A7 | L3M | -152 | +1541 | +861 | +904 | pass | pass | pass | pass | STRICT PASS |

### Near-pass list: REPLACE rows failing exactly ONE strict criterion (label BEST-AVAILABLE-NOT-PROVEN; first 40 by L6M ulcer improvement)

| cell | live book | failing criterion | L6M d ulcer / d $/wk / d worst / d maxDD | L3M d ulcer / d $/wk / d worst / d maxDD |
|---|---|---|---|---|
| M1edb9fab | A7 | L6M worst week not worse | -1085 / +630 / -580 / +3817 | -1067 / +1519 / +258 / +3817 |
| Ma5b5d03a | A7 | L6M $/wk not lower | -891 / -314 / +2617 / +3982 | -667 / +684 / +2617 / +3982 |
| Mcb276f27 | A7 | L6M $/wk not lower | -889 / -376 / +1282 / +3982 | -665 / +579 / +1282 / +3982 |
| Md60fb3e3 | A7 | L6M $/wk not lower | -771 / -733 / +2542 / +2275 | -918 / +585 / +2542 / +2275 |
| Mb0e6dfa3 | A7 | L6M $/wk not lower | -767 / -732 / +2542 / +2285 | -916 / +589 / +2542 / +2285 |
| L3ee2d289 | H7 | L6M $/wk not lower | -728 / -61 / +2380 / +7245 | -811 / +1385 / +2380 / +7245 |
| Leccc6042 | H7 | L6M $/wk not lower | -711 / -251 / +1178 / +3058 | -381 / +423 / +1178 / +3058 |
| Lfccd4faa | A7 | L6M $/wk not lower | -581 / -1355 / +1814 / +3707 | -1148 / +1300 / +4218 / +3707 |
| L4cab9322 | A7 | L6M $/wk not lower | -528 / -619 / +2669 / +4497 | -1814 / +1387 / +6819 / +4497 |
| La34ff0e1 | A7 | L6M $/wk not lower | -526 / -141 / +1596 / +1888 | -837 / +2090 / +1596 / +1888 |
| M1edb9fab | H7 | L6M $/wk not lower | -419 / -977 / +417 / +6212 | -736 / +165 / +3203 / +6212 |
| L03a14486 | H7 | L3M stack ulcer lower | -405 / +451 / +1943 / +3474 | +71 / +152 / +1943 / +3474 |
| L5c9e11b3 | U7 | L6M $/wk not lower | -169 / -472 / +1005 / +2760 | -651 / +1123 / +2086 / +5493 |
| L548972b6 | A7 | L3M stack ulcer lower | -2 / +865 / +943 / +3530 | +93 / +599 / +943 / +3530 |
| L1219f60d | A7 | L6M stack ulcer lower | +86 / +342 / +482 / +312 | -84 / +2487 / +482 / +312 |


**Asia REPLACE pass list so far: 1 candidate rows** (L5c9e11b3 both-side REPLACE A7). A REPLACE candidate that passes recent months, no RED prior year (rule B) and engine persistence >= 0.58 still needs the 30 date-shift controls of its REPLACE set, layers and the exit run before D8 (dates in MORNING.md).

## Twin cells (identical event stream; results shown are the canonical's, labelled; NOT counted again)

| twin cell | canonical | ADD | REPLACE A7 | verdicts copied |
|---|---|---|---|---|
| AX9 tm2700 | [twin of AX11] | no (L6M du +748 dm -129 | L3M du -331 dm -748 RED Y2025) | not run | copied |
| L0de97201 time_m_7 | [twin of L8a9fa508] | no (L6M du +942 dm -1128 | L3M du -25 dm +1089) | pending | copied |
| L243db8db vol_500 | [twin of L1f7c199b] | no (L6M du +2322 dm +62 | L3M du +2810 dm -3036) | not run | copied |
| L32bddb74 tm120 | [twin of L15f14deb] | no (L6M du +1265 dm +783 | L3M du +857 dm -852) | no (L6M du +261 dm +707 | L3M du +672 dm +610) | copied |
| L3e27a9ba time_m_5 | [twin of L348825a3] | no (L6M du +978 dm +260 | L3M du +1335 dm +461) | no (L6M du +736 dm -940 | L3M du +1180 dm +865) | copied |
| L49b3f8c9 time_m_10 | [twin of L0d3e549a] | no (L6M du +575 dm +157 | L3M du +293 dm +28) | no (L6M du +674 dm +1 | L3M du +1222 dm +1457) | copied |
| L6bfd0523 tm120 | [twin of L00277b0f] | no (L6M du +2302 dm -1519 | L3M du -287 dm +152) | not run | copied |
| L6d3f77d8 time_m_5 | [twin of L1b1788be] | no (L6M du +3564 dm -2103 | L3M du +547 dm -139) | not run | copied |
| L718570f8 time_m_4 | [twin of Lccd499e5] | no (L6M du +1476 dm -1018 | L3M du -18 dm +715) | no (L6M du -348 dm +416 | L3M du -206 dm +1183) | copied |
| L72f46746 dchg_14 | [twin of L5ca5030a] | pending | not run | copied |
| L76cff489 time_m_3 | [twin of L1f5315f5] | no (L6M du +1457 dm +166 | L3M du +604 dm +1387) | no (L6M du +182 dm -504 | L3M du -532 dm +1081) | copied |
| L8c63e140 tm120 | [twin of L7dfcc15f] | no (L6M du +1915 dm -213 | L3M du +1934 dm -820) | no (L6M du +349 dm +574 | L3M du +997 dm +332) | copied |
| L8d3d042d tm240 | [twin of L5381b8bb] | no (L6M du +2572 dm -1315 | L3M du +753 dm -622) | not run | copied |
| L8d866ea1 tm420 | [twin of L64313ba5] | no (L6M du +3366 dm +864 | L3M du +4699 dm -167) | no (L6M du +2441 dm +21 | L3M du +3893 dm -897) | copied |
| L912f47c2 time_m_2 | [twin of Lfa23bc21] | no (L6M du +2210 dm -808 | L3M du +2358 dm -896) | no (L6M du +747 dm +566 | L3M du +1598 dm +514) | copied |
| L9502269d tm45 | [twin of L780f8501] | no (L6M du +926 dm +466 | L3M du -41 dm -222) | no (L6M du +337 dm +75 | L3M du +589 dm -412) | copied |
| L994e0374 time_m_2 | [twin of L05236f50] | no (L6M du +2303 dm -1437 | L3M du -269 dm +144) | not run | copied |
| L9b318012 tm60 | [twin of L65624cfa] | no (L6M du +2476 dm +1173 | L3M du +3093 dm -1167) | no (L6M du +414 dm +773 | L3M du +584 dm +779) | copied |
| L9e2ad3ae time_m_3 | [twin of L82f920bb] | no (L6M du +2153 dm -389 | L3M du +1438 dm +1105) | no (L6M du +2015 dm -1653 | L3M du +3146 dm +213) | copied |
| L9fb39984 time_m_4 | [twin of L3253c811] | no (L6M du +1226 dm -227 | L3M du -61 dm -756) | not run | copied |
| La4bf1d85 time_m_2 | [twin of L00391b70] | no (L6M du +2344 dm +737 | L3M du +2925 dm +564) | no (L6M du +2404 dm +781 | L3M du +4415 dm -431) | copied |
| Lab3c87d4 dchg_28 | [twin of Lb304fd46] | no (L6M du +660 dm +477 | L3M du +211 dm -988) | not run | copied |
| Lb886cbc0 time_m_20 | [twin of L6b75ada3] | no (L6M du +1595 dm +534 | L3M du +1234 dm +468) | no (L6M du +1150 dm -604 | L3M du +1629 dm +558) | copied |
| Lba6d553c time_m_2 | [twin of L5dee2059] | no (L6M du +1989 dm +170 | L3M du +759 dm +1591) | no (L6M du +1173 dm -364 | L3M du +1425 dm +1168) | copied |
| Lbcfd73ea kagi_20 | [twin of L887fd783] | no (L6M du +2011 dm -427 | L3M du +803 dm -94) | not run | copied |
| Lca45e417 tm780 | [twin of L3cf94bc0] | no (L6M du +1536 dm -827 | L3M du -320 dm -767) | not run | copied |
| Lcdbcb17a tm300 | [twin of L79c9d5e2] | no (L6M du +1155 dm +692 | L3M du +643 dm +963) | no (L6M du +986 dm -183 | L3M du +822 dm +1596) | copied |
| Ld7058efc dchg_28 | [twin of L17010aa0] | no (L6M du -705 dm +405 | L3M du -1384 dm +532) | not run | copied |
| Le1b5e0fe tm420 | [twin of L973b5c8a] | no (L6M du +592 dm +1086 | L3M du +384 dm +1267) | no (L6M du +798 dm +533 | L3M du +1267 dm +1382) | copied |
| Le205d6db kagi_10 | [twin of L952625e3] | no (L6M du +508 dm -467 | L3M du -395 dm +290) | not run | copied |
| Le446464b tm15 | [twin of Lade83c7d] | no (L6M du +3652 dm +777 | L3M du +5371 dm -392) | no (L6M du +562 dm +1056 | L3M du +1355 dm +1124) | copied |
| Lf1737369 time_m_1 | [twin of Le2fc494e] | no (L6M du +2543 dm +1024 | L3M du +3214 dm -1272) | no (L6M du +444 dm +614 | L3M du +646 dm +661) | copied |
| Lf26d240b time_m_7 | [twin of L8a9fa508] | no (L6M du +942 dm -1128 | L3M du -25 dm +1089) | pending | copied |
| Lf2cfe47a tm420 | [twin of L22fed823] | no (L6M du +1419 dm -287 | L3M du +763 dm +768) | not run | copied |
| Lf493dcb1 time_m_3 | [twin of L72f3fe1c] | no (L6M du +1467 dm +272 | L3M du +2206 dm -146) | no (L6M du +613 dm +522 | L3M du +1519 dm +787) | copied |
| Lf4ed7e30 time_m_4 | [twin of L35596060] | no (L6M du +911 dm +322 | L3M du +549 dm -288) | no (L6M du +618 dm +314 | L3M du +1034 dm +1251) | copied |
| Lf7c7ee18 tm240 | [twin of L6f0b4896] | no (L6M du +1468 dm -1016 | L3M du -22 dm +718) | not run | copied |
| Lfefc2c66 time_m_7 | [twin of Ld9c0b52e] | no (L6M du +1007 dm +111 | L3M du +1338 dm +81) | no (L6M du +420 dm -220 | L3M du +889 dm +485) | copied |
| M5d2fdeae tm120 | [twin of M58190669] | no (L6M du +29 dm +917 | L3M du -146 dm +926) | no (L6M du +125 dm -438 | L3M du +235 dm +556) | copied |
| M717d326e tm120 | [twin of M1e8dd48e] | no (L6M du +1359 dm +281 | L3M du +903 dm -111) | no (L6M du -528 dm +274 | L3M du -186 dm +697) | copied |
| M76cff489 time_m_3 | [twin of M1f5315f5] | no (L6M du +847 dm +181 | L3M du +169 dm -326) | no (L6M du -280 dm -887 | L3M du +41 dm -181) | copied |
| M96c87f8d dchg_28 | [twin of M223d21bd] | no (L6M du +1298 dm -316 | L3M du -606 dm +239) | not run | copied |
| M994e0374 time_m_2 | [twin of M05236f50] | no (L6M du +992 dm +56 | L3M du -350 dm +323) | no (L6M du -1069 dm +45 | L3M du -1037 dm +426) | copied |
| M9b318012 tm60 | [twin of M65624cfa] | no (L6M du +535 dm +606 | L3M du +1118 dm -48) | no (L6M du -144 dm +32 | L3M du -103 dm +378) | copied |
| Mc57557da tm30 | [twin of M43ae1f08] | no (L6M du +6668 dm -2436 | L3M du +8638 dm -4193) | not run | copied |
| Mccd499e5 time_m_4 | [twin of M718570f8] | no (L6M du +180 dm +165 | L3M du -1464 dm +1300) | no (L6M du -1097 dm +263 | L3M du -1081 dm +975) | copied |
| Me7bb12d3 tm240 | [twin of M9805fd73] | no (L6M du +566 dm +207 | L3M du +946 dm -848) | no (L6M du -768 dm -599 | L3M du -919 dm -269) | copied |
| Mf4ed7e30 time_m_4 | [twin of M35596060] | no (L6M du -608 dm +693 | L3M du -1183 dm +1104) | no (L6M du -858 dm +450 | L3M du -930 dm +1934) | copied |
| Mf7c7ee18 tm240 | [twin of M6f0b4896] | no (L6M du +181 dm +157 | L3M du -1462 dm +1297) | no (L6M du -1094 dm +256 | L3M du -1079 dm +974) | copied |

# ASIA_REMAINING_WORK (W-ASIA, order 1337Z; refreshed 2026-11-19T14:45:02Z)

Cells in the Asia ladder: 3197 (old L-ids of screen long/short cells = both-side books + M twins + both-mode cells). **First look done: 624; WITHOUT a first look: 2573** (15410 stage-A lines left; unbuilt cells 0). Stages (all cells): {'C': 59, 'out (L6M negative)': 309, 'B': 127, 'out': 113, 'out (RED B)': 2, 'A': 2584, 'A2': 3}.

| part | queued now (not DONE) | still to be appended (estimate) | basis |
|---|---|---|---|
| stage A first look (ADD + REPLACE-vs-A7, L6M) | 14260 | 0 | queue lines |
| a2 REPLACE vs K7/P7/H7/U7 (L6M) | 4626 | ~23110 | 24 lines x alive share 0.37 x cells without first look |
| prior years (2023-04..2026-04, ADD/REPLACE sets) | 3858 | ~2089 | 37 months x ~1.5 sets x beater share 0.022 (follow-ups gated to cells that beat a live book) |
| controls (30 date-shift x 6 months per set) | 5180 (+ 0 passer-control lines in first.txt, same lines) | ~9673 | 180 x ~1.5 sets x beater share 0.022 x C share 0.95 |
| F-set re-runs (202511 capped exits) | 0 | cron :20/:50 adds new ones | contaminated 202511 set-months |
| older AB/AX lines (W-LONENG) | 2412 | 0 | queue lines |
| layers (W-LAYERS, tag NYL) | not in _asi | ~4.5 h per passer (W-LAYERS 11:07Z) | 8 passers |
| exit run (W-EXITENG / W-D8EXIT) | not in _asi | D8_EXIT_SCREEN.md | per candidate |

**Cells already OUT at an early rung with later-rung lines still queued: 87 cells, 2088 lines** (these are wasted work for W-DEDUP; the 8 passers and the 59-cell stage-C reset are NOT among them if the next line says 0).

Rate now: Asia landed last hour 1453 set-months/h (box-1 tree view; see MORNING.md for the post-change measurement).



## Engine throughput and queue (Asia sets TL3_ASI_*)
Asia set-months landed: last 1 h 1109, last 3 h 2166; Asia queue lines pending (not DONE): 30265.

## Proof that Asia sets are launched ahead of NY AM
- QUEUES.txt order on server 2 dispatcher: _asi position 5, _nye/pending_l 13, _nye/pending_w , _lon 14 (lower = earlier).
- PRIORITY.txt admission order (TP admit, all hosts): NT > EXE > ASI > NYL > NYR > NYF > FR > NYE > NYW > LON
- box1 running engine sets by tag: 15 TL3_CMB_      14 TL3_NYE_      10 TL3_NYL_       8 TL3_LON_       7 TL3_ASI_
- server2 running engine sets by tag: 56 TL3_NYL_
- A running engine sets by tag: 171 TL3_NYL_      16 TL3_NYE_
- B running engine sets by tag: 183 TL3_NYL_      12 TL3_NYE_

## Best five rows (drawdown first: most negative L6M du among cells with a finished REPLACE row)
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | controls |
|---|---|---|---|---|---|---|---|
| AB6 trb_240 / levels_fib15.break_native {"n": 3, "k": 0.5} / plain60/60 / both | no (L6M du +335 dm +1217 | L3M du +511 dm -702) | no (L6M du +2242 dm -2808 | L3M du +3964 dm -6870) | not run | no (L6M du +49 dm +370 | L3M du +377 dm -199) | no (L6M du -296 dm -526 | L3M du -327 dm -1249) | no (L6M du -1396 dm -146 | L3M du -2236 dm -914) | 0 of 30 |
| Lda55d973 vol_750 / momentum_stoch.zone_break_native {"len": 9, "lvl": 80} / plain60/60 / both (both sides, engine-tested; screen mode long) | yes (L6M du -1672 dm +2260 | L3M du -2265 dm +1965 RED Y2025) | no (L6M du +360 dm -2813 | L3M du +724 dm -4895) | no (L6M du +1702 dm -8194 | L3M du +2043 dm -6482) | yes (L6M du -1222 dm +911 | L3M du -1416 dm +2143 RED Y2025) | no (L6M du -99 dm -268 | L3M du -1462 dm +1191) | no (L6M du -1348 dm -66 | L3M du -1355 dm -1789) | 59 of 30 |
| La5b5d03a time_m_2 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / both (both sides, engine-tested; screen mode long) | no (L6M du +222 dm +485 | L3M du +463 dm -51 RED Y2023) | no (L6M du +926 dm -2686 | L3M du +2289 dm -5618) | no (L6M du +3399 dm -9027 | L3M du +3705 dm -6504) | yes (L6M du -1197 dm +1547 | L3M du -892 dm +1038 RED Y2023) | no (L6M du +1058 dm -152 | L3M du -311 dm -616) | no (L6M du +99 dm -575 | L3M du -1062 dm -419) | 0 of 30 |
| Lcb276f27 tm120 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / both (both sides, engine-tested; screen mode long) | no (L6M du +269 dm +872 | L3M du +546 dm +19 RED Y2023) | no (L6M du +985 dm -2570 | L3M du +2381 dm -5549) | no (L6M du +3438 dm -8996 | L3M du +3770 dm -6434) | yes (L6M du -1146 dm +1567 | L3M du -811 dm +1085 RED Y2023) | no (L6M du +1110 dm -122 | L3M du -214 dm -547) | no (L6M du +134 dm -550 | L3M du -996 dm -348) | 0 of 30 |
| M718570f8 time_m_4 / momentum_squeeze.fire_slope {"len": 14, "wd": 1.0} / asym10u/20u / long-only | no (L6M du +180 dm +165 | L3M du -1464 dm +1300) | not run | not run | no (L6M du -1097 dm +263 | L3M du -1081 dm +975) | not run | not run | 0 of 30 |

## Cells that beat a live Asia book (Asia rule, yes), drawdown first
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | prior years run | controls |
|---|---|---|---|---|---|---|---|---|
| Lda55d973 vol_750 / momentum_stoch.zone_break_native {"len": 9, "lvl": 80} / plain60/60 / both (both sides, engine-tested; screen mode long) | yes (L6M du -1672 dm +2260 | L3M du -2265 dm +1965 RED Y2025) | no (L6M du +360 dm -2813 | L3M du +724 dm -4895) | no (L6M du +1702 dm -8194 | L3M du +2043 dm -6482) | yes (L6M du -1222 dm +911 | L3M du -1416 dm +2143 RED Y2025) | no (L6M du -99 dm -268 | L3M du -1462 dm +1191) | no (L6M du -1348 dm -66 | L3M du -1355 dm -1789) | K7:0,P7:0,A7:3,H7:0,U7:0 | 59 of 30 |
| La5b5d03a time_m_2 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / both (both sides, engine-tested; screen mode long) | no (L6M du +222 dm +485 | L3M du +463 dm -51 RED Y2023) | no (L6M du +926 dm -2686 | L3M du +2289 dm -5618) | no (L6M du +3399 dm -9027 | L3M du +3705 dm -6504) | yes (L6M du -1197 dm +1547 | L3M du -892 dm +1038 RED Y2023) | no (L6M du +1058 dm -152 | L3M du -311 dm -616) | no (L6M du +99 dm -575 | L3M du -1062 dm -419) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| Lcb276f27 tm120 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / both (both sides, engine-tested; screen mode long) | no (L6M du +269 dm +872 | L3M du +546 dm +19 RED Y2023) | no (L6M du +985 dm -2570 | L3M du +2381 dm -5549) | no (L6M du +3438 dm -8996 | L3M du +3770 dm -6434) | yes (L6M du -1146 dm +1567 | L3M du -811 dm +1085 RED Y2023) | no (L6M du +1110 dm -122 | L3M du -214 dm -547) | no (L6M du +134 dm -550 | L3M du -996 dm -348) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L0a809c2e kagi_40 / trend_ma_t3.price_native {"len": 13, "width": 0.25} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du -47 dm +1439 | L3M du -1599 dm +1297 RED Y2025) | no (L6M du -464 dm -2469 | L3M du -671 dm -4382) | no (L6M du +3556 dm -9315 | L3M du +3509 dm -8084) | yes (L6M du -789 dm +402 | L3M du -1498 dm +1029 RED Y2025) | no (L6M du -554 dm -71 | L3M du -1326 dm +708) | no (L6M du -84 dm -1395 | L3M du -2134 dm -968) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L7c368a4f time_m_5 / pullback_ema.depth {"len": 10, "w": 0.5} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +682 dm +2019 | L3M du -454 dm +1240 RED Y2025) | no (L6M du -649 dm -1287 | L3M du -1529 dm -2786) | no (L6M du +2892 dm -7177 | L3M du +3173 dm -4564) | yes (L6M du -199 dm +1810 | L3M du -1260 dm +3199 RED Y2025) | no (L6M du +334 dm +628 | L3M du -711 dm +811 RED Y2025,Y2023) | no (L6M du +52 dm +184 | L3M du -2119 dm +569 RED Y2025) | K7:0,P7:0,A7:3,H7:3,U7:3 | 3 of 30 |
| L30aad100 drb_3500 / momentum_roc.break_native {"len": 20, "wd": 1.0} / plain60/60 / both | no (L6M du +864 dm +61 | L3M du -110 dm +532) | not run | not run | yes (L6M du -634 dm +162 | L3M du -179 dm +722) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L5c9e11b3 vol_750 / momentum_mvote.v3of5 {"scale": 0.25, "thr": 0.25} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du -815 dm +2152 | L3M du -1706 dm +3570 RED Y2025) | no (L6M du +1530 dm -2252 | L3M du +2684 dm -3703) | no (L6M du +2680 dm -9625 | L3M du +2168 dm -6262) | yes (L6M du -603 dm +1062 | L3M du -1151 dm +3460 RED Y2025) | no (L6M du -451 dm +87 | L3M du -636 dm +2865 RED Y2025,Y2023) | no (L6M du -169 dm -472 | L3M du -651 dm +1123) | K7:0,P7:0,A7:3,H7:3,U7:0 | 60 of 30 |
| L1edb9fab tm300 / pullback_ema.depth {"len": 10, "w": 0.5} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +747 dm +1854 | L3M du -411 dm +1205 RED Y2025) | no (L6M du -584 dm -1527 | L3M du -1448 dm -2924) | no (L6M du +3214 dm -7331 | L3M du +3583 dm -4483) | yes (L6M du -142 dm +1606 | L3M du -1252 dm +3083 RED Y2025) | no (L6M du +391 dm +413 | L3M du -685 dm +692 RED Y2025,Y2023) | no (L6M du +246 dm +17 | L3M du -1893 dm +426 RED Y2025) | K7:0,P7:0,A7:3,H7:3,U7:3 | 0 of 30 |
| Ledfbf4d2 vol_350 / bands_bollinger.break_native {"clk": 20, "k": 1.5} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du -813 dm +880 | L3M du -949 dm +64 RED Y2025) | no (L6M du -567 dm -1956 | L3M du -296 dm -3836) | no (L6M du +3368 dm -10349 | L3M du +3215 dm -7631) | yes (L6M du -459 dm +384 | L3M du -548 dm +1331 RED Y2025) | no (L6M du -541 dm -839 | L3M du -443 dm -582) | no (L6M du -421 dm -1230 | L3M du -860 dm -2636) | K7:0,P7:0,A7:3,H7:0,U7:0 | 29 of 30 |
| M15f14deb tm120 / momentum_mvote.v4of5 {"scale": 0.25, "thr": 0.25} / plain60/60 / long-only | no (L6M du +524 dm +624 | L3M du +558 dm +83 RED Y2025) | no (L6M du +1100 dm -3442 | L3M du +2476 dm -5291) | no (L6M du +6705 dm -10031 | L3M du +9565 dm -8755) | yes (L6M du -480 dm +276 | L3M du -176 dm +390) | no (L6M du -505 dm -645 | L3M du +68 dm -958) | no (L6M du -318 dm -866 | L3M du -713 dm -952) | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L17ce266f tm240 / momentum_rsi.mom {"len": 10, "lvl": 60} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +485 dm +1043 | L3M du -887 dm +1432 RED Y2025) | no (L6M du +307 dm -2490 | L3M du +377 dm -3602) | no (L6M du +3589 dm -9936 | L3M du +2867 dm -7615) | yes (L6M du -406 dm +659 | L3M du -119 dm +1682 RED Y2025) | no (L6M du +64 dm -701 | L3M du -890 dm +788) | no (L6M du +1029 dm -1071 | L3M du -43 dm -807) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L5d9e7166 tm240 / momentum_rsi.mom_native {"len": 10, "lvl": 60} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +485 dm +1043 | L3M du -887 dm +1432 RED Y2025) | no (L6M du +307 dm -2490 | L3M du +377 dm -3602) | no (L6M du +3589 dm -9936 | L3M du +2867 dm -7615) | yes (L6M du -406 dm +659 | L3M du -119 dm +1682 RED Y2025) | no (L6M du +64 dm -701 | L3M du -890 dm +788) | no (L6M du +1029 dm -1071 | L3M du -43 dm -807) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| Lf77e374b tm240 / bands_donchian.break {"n": 10, "buf": 0.0} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +1118 dm +533 | L3M du +373 dm -278 RED Y2025) | no (L6M du +716 dm -1957 | L3M du +1701 dm -4841) | no (L6M du +3792 dm -9480 | L3M du +4392 dm -8197) | yes (L6M du -403 dm +1440 | L3M du -202 dm +2270 RED Y2025) | no (L6M du +2636 dm -1345 | L3M du +1734 dm -1341) | no (L6M du +1820 dm -1319 | L3M du +1943 dm -3101) | K7:0,P7:0,A7:3,H7:0,U7:0 | 9 of 30 |
| L05222ff9 time_m_4 / momentum_rsi.mom_native {"len": 10, "lvl": 60} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +497 dm +464 | L3M du -884 dm +1412 RED Y2025) | no (L6M du +305 dm -2648 | L3M du +376 dm -3622) | no (L6M du +3608 dm -10597 | L3M du +2854 dm -7634) | yes (L6M du -395 dm +85 | L3M du -122 dm +1676 RED Y2025) | no (L6M du +76 dm -1277 | L3M du -883 dm +769) | no (L6M du +1042 dm -1651 | L3M du -39 dm -826) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L63ff9ae8 time_m_4 / momentum_rsi.mom {"len": 10, "lvl": 60} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +497 dm +464 | L3M du -884 dm +1412) | not run | not run | yes (L6M du -395 dm +85 | L3M du -122 dm +1676) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L0b1d7882 tm30 / bands_vwap.break {"minbars": 10, "k": 1.0} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +782 dm +300 | L3M du +39 dm +724 RED Y2025) | no (L6M du +235 dm -3361 | L3M du +231 dm -4322) | no (L6M du +4343 dm -9748 | L3M du +3897 dm -6152) | yes (L6M du -65 dm +395 | L3M du -152 dm +1541 RED Y2025) | no (L6M du +1224 dm -1762 | L3M du +1599 dm -1201) | no (L6M du -117 dm -1186 | L3M du -2415 dm -21) | K7:0,P7:0,A7:3,H7:0,U7:0 | 4 of 30 |

## D8 gate (orders 0213Z, 0228Z)
Nothing enters D8 without the EXIT RUN (68 recipes) on its own entries. Candidates are appended to autopilot/D8_CANDIDATES.txt (append-only, session Asia). Engine cost after the exit screen for the 16 Asia cell(s) that beat a live book today: about 27568 set-months (prior years + 30 controls + layers/exit rows ~1,723 per candidate).

All other cells: see /mnt/l2/l2vast/_asi_lad/beats_rows.csv (verdict per live book: no / pending). Asia ladder state: `python3 code/th_asia/asia_ladder.py status`.

