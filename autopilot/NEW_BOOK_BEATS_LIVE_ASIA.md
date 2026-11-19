# NEW_BOOK_BEATS_LIVE_ASIA - does a new book beat the live Asia book(s) in the exact engine? (W-ASIA, order 0400Z), refreshed 2026-11-19 11:24Z

**vs TODAY's stack (JL3, today's DAY-DONE); Asia is decided FIRST; label BETTER = calibration pending, NOT calibrated.** Asia rule (higher bar, order 1731Z / 0210Z item 4): a REPLACE row (new book ON, the named live Asia book's Asia entries OFF) beats that live book only if on BOTH L6M and L3M the stack ulcer is LOWER (drawdown first) AND mean $/wk is not lower AND worst week and max drawdown are not worse; then prior years (no RED = >30% worse; AMBER shown), persistence > 0.60, 30 date-shift controls, calibration. du = d stack ulcer (negative = better), dm = d mean $/wk (base lots, $4.84 RT).

**Counts:** Asia cells with any engine row 614; cells with a finished REPLACE verdict (L6M+L3M landed) 422; cells that beat at least one live Asia book on L6M+L3M under the Asia rule (BETTER, calibration pending) 14 (under the looser NY rule 31); ADD rows finished 600.

| live Asia book replaced | cells finished | beat it | pending |
|---|---|---|---|
| K7 | 66 | 0 | 5 |
| P7 | 59 | 0 | 5 |
| A7 | 422 | 14 | 34 |
| H7 | 62 | 0 | 6 |
| U7 | 62 | 0 | 5 |

**Corrected counts (order 1014Z; a both-side engine result is valid for the both-side book that was run; the engine is the judge): beat a live Asia book on L6M+L3M - both-side 14 (of 361 tested; 514 cells with rows), long-only 0 (of 61 tested; 100 cells so far), short-only 0 (of 0 tested; 0 cells so far).** Old ids of screen-long/short cells are labelled "(both sides, engine-tested)"; M-ids = the mode-correct long-only / short-only twin.

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
| L5c9e11b3 vol_750 | both-side | A7 | -603 | +1062 | +3289 | +4781 | -1151 | +3460 | +3289 | +4781 | yes |
| M5c9e11b3 vol_750 | long-only | A7 | -306 | -6 | +540 | -204 | +164 | +959 | +540 | -204 | no |
| Ledfbf4d2 vol_350 | both-side | A7 | -459 | +384 | +4405 | +1029 | -548 | +1331 | +4405 | +1029 | yes |
| Medfbf4d2 vol_350 | long-only | A7 | -181 | -280 | +16 | -202 | +396 | +179 | +16 | -202 | no |
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
| M1edb9fab tm300 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L0a809c2e kagi_40 | both-side | A7 | 0.549 | +0.86 | +0.20 / +0.01 / +0.45 | RED / RED / RED | no | GREEN / AMBER / RED | fail | fail |
| M0a809c2e kagi_40 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L17ce266f tm240 | both-side | A7 | 0.622 | +0.70 | +0.07 / +0.21 / +0.18 | RED / RED / RED | no | GREEN / AMBER / RED | PASS | fail |
| M17ce266f tm240 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L5d9e7166 tm240 | both-side | A7 | 0.622 | +0.70 | +0.07 / +0.21 / +0.18 | RED / RED / RED | no | GREEN / AMBER / RED | PASS | fail |
| M5d9e7166 tm240 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L05222ff9 time_m_4 | both-side | A7 | 0.598 | +0.74 | +0.08 / +0.18 / +0.26 | RED / RED / RED | no | GREEN / AMBER / RED | fail | fail |
| M05222ff9 time_m_4 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L63ff9ae8 time_m_4 | both-side | A7 | 0.598 | +0.74 | +0.08 / +0.18 / +0.26 | RED / RED / RED | no | pending / pending / pending | fail | fail |
| M63ff9ae8 time_m_4 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L7c368a4f time_m_5 | both-side | A7 | 0.537 | +1.17 | +0.07 / +0.48 / +0.26 | RED / RED / RED | no | GREEN / GREEN / RED | fail | fail |
| L5c9e11b3 vol_750 | both-side | A7 | 0.622 | +1.36 | +0.35 / +0.63 / +0.42 | RED / RED / RED | no | GREEN / GREEN / RED | PASS | fail |
| M5c9e11b3 vol_750 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| Ledfbf4d2 vol_350 | both-side | A7 | 0.622 | +1.10 | +0.23 / +0.43 / +0.29 | RED / RED / RED | no | GREEN / GREEN / RED | PASS | fail |
| Medfbf4d2 vol_350 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| Lf77e374b tm240 | both-side | A7 | 0.512 | +1.23 | +0.02 / +0.07 / -0.09 | RED / RED / RED | yes | AMBER / AMBER / RED | fail | fail |
| Mf77e374b tm240 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |
| L0b1d7882 tm30 | both-side | A7 | 0.488 | +0.20 | +0.07 / +0.02 / -0.16 | RED / RED / RED | yes | GREEN / AMBER / RED | fail | fail |
| M0b1d7882 tm30 | long-only (mode-correct twin) | A7 | not screened here (csv = both-side stream) | | | | | pending / pending / pending | pending | pending |

Gate A pass 4, Gate B pass 0 among the both-side beaters listed (see MORNING.md for the reconciliation note). Short-only rows: none of the beating cells has screen mode short, so no short-only twin exists for them.

## RULE B TABLE (engine prior years, order 1122Z): stack WITH the new book (REPLACE row) vs TODAY'S stack in the same year
**Sign convention (all four % columns): positive = the new stack is WORSE than today's stack** (d ulcer % = ulcer higher; d max DD % = max drawdown deeper; d worst week % = worst week deeper (e.g. +10% = worst week is 10% more negative); d $/wk % = mean $/week lower). Negative = better. Colour = worst of the four: RED > 30%, AMBER 15-30%, else GREEN. **Overall verdict: any RED year under B = fails the prior-year gate**; years not landed = pending (not fail). Engine persistence = share of non-overlapping 2-week blocks (all months landed, 2023-04..2026-10) where REPLACE minus today's stack is >= 0; bare persistence (screen stream) shown beside it; gate > 0.60. Rule A colours (screen, bare stream: prior-year weekly R >30% worse than own L6M) are in their OWN column and only order the queue.

| cell | stream | book beaten | year | d ulcer % | d max DD % | d worst week % | d $/wk % | RULE B colour (as run) | RULE B colour EX-ARTEFACT | RULE A colour (screen) | overall B verdict (as run / ex-artefact) | engine persistence (blocks) | bare persistence |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
**NOTE (2025 REPLACE rows are an ENGINE ARTEFACT, not an A7 effect; W-ASIA 11:3xZ):** in the 2025 window ALL new-book sets (ADD rows too, not only REPLACE-A7) carry ONE MF1 trade on 2025-11-28 with gross -506,325 on 1 lot (exit_ns 2025-11-28 07:00:01Z: an exit at a time with no usable print, price ~0); 157 of the 184 Asia set-months landed for 202511 contain it, JL3 itself has none. It makes the 2025 worst week ~-$510k vs -$39k and gives the identical +410% ulcer / +550% max DD / +1,219% worst week across cells. Real 2025 stack: A7 earned +$49,829 in the Asia session in 2025 (304 trades), K7 +35,095, H7 +33,248, P7 +176,090, U7 +16,540 in JL3 (all five live books exist in the 2025 stack; JL3 is the SAME stack definition as today, run on 2025 data). The EX-ARTEFACT column removes the artefact trade(s) (gross < -$100k) and keeps everything else as run; it is a diagnostic, NOT a delivered number - the engine owners must fix the exit (events file exit_ts / price) and the sets be re-run. 2023/2024 are unaffected by the artefact.

| Lda55d973 vol_750 | both-side | A7 | 2023 | +1 | +10 | -3 | -7 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.561 |
| Lda55d973 vol_750 | both-side | A7 | 2024 | +3 | -1 | -14 | +16 | AMBER | AMBER | RED |  |  |  |
| Lda55d973 vol_750 | both-side | A7 | 2025 | +411 | +551 | +1221 | +144 | RED | AMBER | RED |  |  |  |
| La5b5d03a time_m_2 | both-side | A7 | 2023 | +30 | +37 | +3 | -40 | RED | RED | RED | RED / RED |  | 0.573 |
| La5b5d03a time_m_2 | both-side | A7 | 2024 | +1 | +2 | -20 | +4 | GREEN | GREEN | RED |  |  |  |
| La5b5d03a time_m_2 | both-side | A7 | 2025 | -27 | -19 | -10 | -141 | GREEN | GREEN | RED |  |  |  |
| Lcb276f27 tm120 | both-side | A7 | 2023 | +30 | +37 | +3 | -41 | RED | RED | ok | RED / RED |  | 0.573 |
| Lcb276f27 tm120 | both-side | A7 | 2024 | +2 | +4 | -20 | +4 | GREEN | GREEN | ok |  |  |  |
| Lcb276f27 tm120 | both-side | A7 | 2025 | -28 | -19 | -10 | -142 | GREEN | GREEN | RED |  |  |  |
| L1edb9fab tm300 | both-side | A7 | 2023 | -4 | -2 | +5 | -19 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.500 |
| L1edb9fab tm300 | both-side | A7 | 2024 | -5 | -8 | -17 | +4 | GREEN | GREEN | RED |  |  |  |
| L1edb9fab tm300 | both-side | A7 | 2025 | +416 | +560 | +1221 | +147 | RED | GREEN | RED |  |  |  |
| L0a809c2e kagi_40 | both-side | A7 | 2023 | -13 | -7 | -4 | -35 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.549 |
| L0a809c2e kagi_40 | both-side | A7 | 2024 | +21 | -2 | -14 | +20 | AMBER | AMBER | RED |  |  |  |
| L0a809c2e kagi_40 | both-side | A7 | 2025 | +402 | +537 | +1215 | +144 | RED | GREEN | RED |  |  |  |
| L17ce266f tm240 | both-side | A7 | 2023 | +5 | +10 | -2 | -17 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.622 |
| L17ce266f tm240 | both-side | A7 | 2024 | +8 | -3 | -14 | +16 | AMBER | AMBER | RED |  |  |  |
| L17ce266f tm240 | both-side | A7 | 2025 | +411 | +553 | +1219 | +150 | RED | GREEN | RED |  |  |  |
| L5d9e7166 tm240 | both-side | A7 | 2023 | +5 | +10 | -2 | -17 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.622 |
| L5d9e7166 tm240 | both-side | A7 | 2024 | +8 | -3 | -14 | +16 | AMBER | AMBER | RED |  |  |  |
| L5d9e7166 tm240 | both-side | A7 | 2025 | +411 | +553 | +1219 | +150 | RED | GREEN | RED |  |  |  |
| L05222ff9 time_m_4 | both-side | A7 | 2023 | +5 | +10 | -2 | -17 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.598 |
| L05222ff9 time_m_4 | both-side | A7 | 2024 | +8 | -4 | -14 | +17 | AMBER | AMBER | RED |  |  |  |
| L05222ff9 time_m_4 | both-side | A7 | 2025 | +411 | +553 | +1219 | +149 | RED | GREEN | RED |  |  |  |
| L7c368a4f time_m_5 | both-side | A7 | 2023 | -5 | -2 | +4 | -19 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.537 |
| L7c368a4f time_m_5 | both-side | A7 | 2024 | -6 | -8 | -17 | +1 | GREEN | GREEN | RED |  |  |  |
| L7c368a4f time_m_5 | both-side | A7 | 2025 | +417 | +559 | +1221 | +149 | RED | GREEN | RED |  |  |  |
| L5c9e11b3 vol_750 | both-side | A7 | 2023 | -1 | +1 | +1 | -31 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.622 |
| L5c9e11b3 vol_750 | both-side | A7 | 2024 | +5 | +1 | -13 | +7 | GREEN | GREEN | RED |  |  |  |
| L5c9e11b3 vol_750 | both-side | A7 | 2025 | +410 | +546 | +1219 | +136 | RED | AMBER | RED |  |  |  |
| Ledfbf4d2 vol_350 | both-side | A7 | 2023 | +1 | +7 | -3 | -21 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.622 |
| Ledfbf4d2 vol_350 | both-side | A7 | 2024 | -1 | -4 | -11 | +6 | GREEN | GREEN | RED |  |  |  |
| Ledfbf4d2 vol_350 | both-side | A7 | 2025 | +415 | +555 | +1228 | +149 | RED | GREEN | RED |  |  |  |
| Lf77e374b tm240 | both-side | A7 | 2023 | +13 | +18 | -4 | -4 | AMBER | AMBER | RED | RED / no RED, all 3 years |  | 0.512 |
| Lf77e374b tm240 | both-side | A7 | 2024 | +4 | -6 | -11 | +20 | AMBER | AMBER | RED |  |  |  |
| Lf77e374b tm240 | both-side | A7 | 2025 | +411 | +553 | +1225 | +156 | RED | AMBER | RED |  |  |  |
| L0b1d7882 tm30 | both-side | A7 | 2023 | -10 | -6 | -0 | -21 | GREEN | GREEN | RED | RED / no RED, all 3 years |  | 0.488 |
| L0b1d7882 tm30 | both-side | A7 | 2024 | +4 | -13 | -9 | +21 | AMBER | AMBER | RED |  |  |  |
| L0b1d7882 tm30 | both-side | A7 | 2025 | +410 | +550 | +1218 | +154 | RED | GREEN | RED |  |  |  |
**Prior years against ALL live Asia books and ADD (where the A7-removal effect is absent or different): both-side beaters, rule B colours as run / ex-artefact, landed years only (pending = not run).**

| cell | variant | 2023 as run / ex-art | 2024 as run / ex-art | 2025 as run / ex-art |
|---|---|---|---|---|
| Lda55d973 vol_750 (both-side) | ADD | GREEN / GREEN | GREEN / GREEN | RED / AMBER |
| Lda55d973 vol_750 (both-side) | RA7 | GREEN / GREEN | AMBER / AMBER | RED / AMBER |
| La5b5d03a time_m_2 (both-side) | ADD | RED / RED | GREEN / GREEN | GREEN / GREEN |
| La5b5d03a time_m_2 (both-side) | RA7 | RED / RED | GREEN / GREEN | GREEN / GREEN |
| Ma5b5d03a time_m_2 (long-only) | ADD | pending | pending | GREEN / GREEN |
| Lcb276f27 tm120 (both-side) | ADD | RED / RED | GREEN / GREEN | GREEN / GREEN |
| Lcb276f27 tm120 (both-side) | RA7 | RED / RED | GREEN / GREEN | GREEN / GREEN |
| L1edb9fab tm300 (both-side) | ADD | GREEN / GREEN | GREEN / GREEN | RED / AMBER |
| L1edb9fab tm300 (both-side) | RA7 | GREEN / GREEN | GREEN / GREEN | RED / GREEN |
| L1edb9fab tm300 (both-side) | RH7 | pending | GREEN / GREEN | RED / GREEN |
| L1edb9fab tm300 (both-side) | RU7 | AMBER / AMBER | GREEN / GREEN | RED / GREEN |
| M1edb9fab tm300 (long-only) | ADD | pending | pending | RED / AMBER |
| L0a809c2e kagi_40 (both-side) | ADD | GREEN / GREEN | GREEN / GREEN | RED / AMBER |
| L0a809c2e kagi_40 (both-side) | RA7 | GREEN / GREEN | AMBER / AMBER | RED / GREEN |
| L17ce266f tm240 (both-side) | ADD | AMBER / AMBER | GREEN / GREEN | RED / AMBER |
| L17ce266f tm240 (both-side) | RA7 | GREEN / GREEN | AMBER / AMBER | RED / GREEN |
| L5d9e7166 tm240 (both-side) | ADD | AMBER / AMBER | GREEN / GREEN | RED / AMBER |
| L5d9e7166 tm240 (both-side) | RA7 | GREEN / GREEN | AMBER / AMBER | RED / GREEN |
| L05222ff9 time_m_4 (both-side) | ADD | AMBER / AMBER | GREEN / GREEN | RED / AMBER |
| L05222ff9 time_m_4 (both-side) | RA7 | GREEN / GREEN | AMBER / AMBER | RED / GREEN |
| L7c368a4f time_m_5 (both-side) | ADD | GREEN / GREEN | GREEN / GREEN | RED / AMBER |
| L7c368a4f time_m_5 (both-side) | RA7 | GREEN / GREEN | GREEN / GREEN | RED / GREEN |
| L7c368a4f time_m_5 (both-side) | RH7 | RED / RED | GREEN / GREEN | RED / GREEN |
| L7c368a4f time_m_5 (both-side) | RU7 | AMBER / AMBER | GREEN / GREEN | RED / GREEN |
| L5c9e11b3 vol_750 (both-side) | ADD | GREEN / GREEN | GREEN / GREEN | RED / AMBER |
| L5c9e11b3 vol_750 (both-side) | RA7 | GREEN / GREEN | GREEN / GREEN | RED / AMBER |
| L5c9e11b3 vol_750 (both-side) | RH7 | RED / RED | GREEN / GREEN | RED / AMBER |
| M5c9e11b3 vol_750 (long-only) | ADD | GREEN / GREEN | GREEN / GREEN | RED / AMBER |
| Ledfbf4d2 vol_350 (both-side) | ADD | GREEN / GREEN | GREEN / GREEN | RED / AMBER |
| Ledfbf4d2 vol_350 (both-side) | RA7 | GREEN / GREEN | GREEN / GREEN | RED / GREEN |
| Lf77e374b tm240 (both-side) | ADD | AMBER / AMBER | GREEN / GREEN | RED / AMBER |
| Lf77e374b tm240 (both-side) | RA7 | AMBER / AMBER | AMBER / AMBER | RED / AMBER |
| L0b1d7882 tm30 (both-side) | ADD | GREEN / GREEN | GREEN / GREEN | RED / GREEN |
| L0b1d7882 tm30 (both-side) | RA7 | GREEN / GREEN | AMBER / AMBER | RED / GREEN |


Rule B so far: as run 13 beater/book rows with >= 1 engine prior year landed have a RED year, 0 none; EX-ARTEFACT (see note) 2 RED, 11 none. Rows without any landed engine prior year are not listed (pending).


## Engine throughput and queue (Asia sets TL3_ASI_*)
Asia set-months landed: last 1 h 2022, last 3 h 6715; Asia queue lines pending (not DONE): 51041.

## Proof that Asia sets are launched ahead of NY AM
- QUEUES.txt order on server 2 dispatcher: _asi position 5, _nye/pending_l 12, _nye/pending_w , _lon 13 (lower = earlier).
- PRIORITY.txt admission order (TP admit, all hosts): NT > EXE > ASI > NYL > NYR > NYF > FR > NYE > NYW > LON
- box1 running engine sets by tag: 16 TL3_NYL_      14 TL3_NYW_      14 TL3_NYE_      11 TL3_ASI_       6 TL3_LON_       2 TL3_EXE_
- server2 running engine sets by tag: 54 TL3_ASI_
- A running engine sets by tag: 198 TL3_ASI_
- B running engine sets by tag: 190 TL3_ASI_

## Best five rows (drawdown first: most negative L6M du among cells with a finished REPLACE row)
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | controls |
|---|---|---|---|---|---|---|---|
| AB6 trb_240 / levels_fib15.break_native {"n": 3, "k": 0.5} / plain60/60 / both | no (L6M du +335 dm +1217 | L3M du +511 dm -702) | no (L6M du +2242 dm -2808 | L3M du +3964 dm -6870) | not run | no (L6M du +49 dm +370 | L3M du +377 dm -199) | no (L6M du -296 dm -526 | L3M du -327 dm -1249) | no (L6M du -1396 dm -146 | L3M du -2236 dm -914) | 0 of 30 |
| Lda55d973 vol_750 / momentum_stoch.zone_break_native {"len": 9, "lvl": 80} / plain60/60 / both (both sides, engine-tested; screen mode long) | yes (L6M du -1672 dm +2260 | L3M du -2265 dm +1965 RED Y2025) | no (L6M du +360 dm -2813 | L3M du +724 dm -4895) | no (L6M du +1702 dm -8194 | L3M du +2043 dm -6482) | yes (L6M du -1222 dm +911 | L3M du -1416 dm +2143 RED Y2025) | no (L6M du -99 dm -268 | L3M du -1462 dm +1191) | no (L6M du -1348 dm -66 | L3M du -1355 dm -1789) | 0 of 30 |
| La5b5d03a time_m_2 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / both (both sides, engine-tested; screen mode long) | no (L6M du +222 dm +485 | L3M du +463 dm -51 RED Y2023) | no (L6M du +926 dm -2686 | L3M du +2289 dm -5618) | no (L6M du +3399 dm -9027 | L3M du +3705 dm -6504) | yes (L6M du -1197 dm +1547 | L3M du -892 dm +1038 RED Y2023) | no (L6M du +1058 dm -152 | L3M du -311 dm -616) | no (L6M du +99 dm -575 | L3M du -1062 dm -419) | 0 of 30 |
| Lcb276f27 tm120 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / both (both sides, engine-tested; screen mode long) | no (L6M du +269 dm +872 | L3M du +546 dm +19 RED Y2023) | no (L6M du +985 dm -2570 | L3M du +2381 dm -5549) | no (L6M du +3438 dm -8996 | L3M du +3770 dm -6434) | yes (L6M du -1146 dm +1567 | L3M du -811 dm +1085 RED Y2023) | no (L6M du +1110 dm -122 | L3M du -214 dm -547) | no (L6M du +134 dm -550 | L3M du -996 dm -348) | 0 of 30 |
| M1edb9fab tm300 / pullback_ema.depth {"len": 10, "w": 0.5} / plain60/60 / long-only | no (L6M du +785 dm +115 | L3M du +6 dm +623 RED Y2025) | pending | pending | no (L6M du -1085 dm +630 | L3M du -1067 dm +1519) | pending | pending | 0 of 30 |

## Cells that beat a live Asia book (Asia rule, yes), drawdown first
| cell | ADD | REPLACE K7 | REPLACE P7 | REPLACE A7 | REPLACE H7 | REPLACE U7 | prior years run | controls |
|---|---|---|---|---|---|---|---|---|
| Lda55d973 vol_750 / momentum_stoch.zone_break_native {"len": 9, "lvl": 80} / plain60/60 / both (both sides, engine-tested; screen mode long) | yes (L6M du -1672 dm +2260 | L3M du -2265 dm +1965 RED Y2025) | no (L6M du +360 dm -2813 | L3M du +724 dm -4895) | no (L6M du +1702 dm -8194 | L3M du +2043 dm -6482) | yes (L6M du -1222 dm +911 | L3M du -1416 dm +2143 RED Y2025) | no (L6M du -99 dm -268 | L3M du -1462 dm +1191) | no (L6M du -1348 dm -66 | L3M du -1355 dm -1789) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| La5b5d03a time_m_2 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / both (both sides, engine-tested; screen mode long) | no (L6M du +222 dm +485 | L3M du +463 dm -51 RED Y2023) | no (L6M du +926 dm -2686 | L3M du +2289 dm -5618) | no (L6M du +3399 dm -9027 | L3M du +3705 dm -6504) | yes (L6M du -1197 dm +1547 | L3M du -892 dm +1038 RED Y2023) | no (L6M du +1058 dm -152 | L3M du -311 dm -616) | no (L6M du +99 dm -575 | L3M du -1062 dm -419) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| Lcb276f27 tm120 / bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} / sym8u / both (both sides, engine-tested; screen mode long) | no (L6M du +269 dm +872 | L3M du +546 dm +19 RED Y2023) | no (L6M du +985 dm -2570 | L3M du +2381 dm -5549) | no (L6M du +3438 dm -8996 | L3M du +3770 dm -6434) | yes (L6M du -1146 dm +1567 | L3M du -811 dm +1085 RED Y2023) | no (L6M du +1110 dm -122 | L3M du -214 dm -547) | no (L6M du +134 dm -550 | L3M du -996 dm -348) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L0a809c2e kagi_40 / trend_ma_t3.price_native {"len": 13, "width": 0.25} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du -47 dm +1439 | L3M du -1599 dm +1297 RED Y2025) | no (L6M du -464 dm -2469 | L3M du -671 dm -4382) | no (L6M du +3556 dm -9315 | L3M du +3509 dm -8084) | yes (L6M du -789 dm +402 | L3M du -1498 dm +1029 RED Y2025) | no (L6M du -554 dm -71 | L3M du -1326 dm +708) | no (L6M du -84 dm -1395 | L3M du -2134 dm -968) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L7c368a4f time_m_5 / pullback_ema.depth {"len": 10, "w": 0.5} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +682 dm +2019 | L3M du -454 dm +1240 RED Y2025) | no (L6M du -649 dm -1287 | L3M du -1529 dm -2786) | no (L6M du +2892 dm -7177 | L3M du +3173 dm -4564) | yes (L6M du -199 dm +1810 | L3M du -1260 dm +3199 RED Y2025) | no (L6M du +334 dm +628 | L3M du -711 dm +811 RED Y2025,Y2023) | no (L6M du +52 dm +184 | L3M du -2119 dm +569 RED Y2025) | K7:0,P7:0,A7:3,H7:3,U7:3 | 0 of 30 |
| L5c9e11b3 vol_750 / momentum_mvote.v3of5 {"scale": 0.25, "thr": 0.25} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du -815 dm +2152 | L3M du -1706 dm +3570 RED Y2025) | no (L6M du +1530 dm -2252 | L3M du +2684 dm -3703) | no (L6M du +2680 dm -9625 | L3M du +2168 dm -6262) | yes (L6M du -603 dm +1062 | L3M du -1151 dm +3460 RED Y2025) | no (L6M du -451 dm +87 | L3M du -636 dm +2865 RED Y2025,Y2023) | no (L6M du -169 dm -472 | L3M du -651 dm +1123) | K7:0,P7:0,A7:3,H7:3,U7:0 | 0 of 30 |
| L1edb9fab tm300 / pullback_ema.depth {"len": 10, "w": 0.5} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +747 dm +1854 | L3M du -411 dm +1205 RED Y2025) | no (L6M du -584 dm -1527 | L3M du -1448 dm -2924) | no (L6M du +3214 dm -7331 | L3M du +3583 dm -4483) | yes (L6M du -142 dm +1606 | L3M du -1252 dm +3083 RED Y2025) | no (L6M du +391 dm +413 | L3M du -685 dm +692 RED Y2025) | no (L6M du +246 dm +17 | L3M du -1893 dm +426 RED Y2025) | K7:0,P7:0,A7:3,H7:2,U7:3 | 0 of 30 |
| Ledfbf4d2 vol_350 / bands_bollinger.break_native {"clk": 20, "k": 1.5} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du -813 dm +880 | L3M du -949 dm +64 RED Y2025) | no (L6M du -567 dm -1956 | L3M du -296 dm -3836) | no (L6M du +3368 dm -10349 | L3M du +3215 dm -7631) | yes (L6M du -459 dm +384 | L3M du -548 dm +1331 RED Y2025) | no (L6M du -541 dm -839 | L3M du -443 dm -582) | no (L6M du -421 dm -1230 | L3M du -860 dm -2636) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L17ce266f tm240 / momentum_rsi.mom {"len": 10, "lvl": 60} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +485 dm +1043 | L3M du -887 dm +1432 RED Y2025) | no (L6M du +307 dm -2490 | L3M du +377 dm -3602) | no (L6M du +3589 dm -9936 | L3M du +2867 dm -7615) | yes (L6M du -406 dm +659 | L3M du -119 dm +1682 RED Y2025) | no (L6M du +64 dm -701 | L3M du -890 dm +788) | no (L6M du +1029 dm -1071 | L3M du -43 dm -807) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L5d9e7166 tm240 / momentum_rsi.mom_native {"len": 10, "lvl": 60} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +485 dm +1043 | L3M du -887 dm +1432 RED Y2025) | no (L6M du +307 dm -2490 | L3M du +377 dm -3602) | no (L6M du +3589 dm -9936 | L3M du +2867 dm -7615) | yes (L6M du -406 dm +659 | L3M du -119 dm +1682 RED Y2025) | no (L6M du +64 dm -701 | L3M du -890 dm +788) | no (L6M du +1029 dm -1071 | L3M du -43 dm -807) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| Lf77e374b tm240 / bands_donchian.break {"n": 10, "buf": 0.0} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +1118 dm +533 | L3M du +373 dm -278 RED Y2025) | no (L6M du +716 dm -1957 | L3M du +1701 dm -4841) | no (L6M du +3792 dm -9480 | L3M du +4392 dm -8197) | yes (L6M du -403 dm +1440 | L3M du -202 dm +2270 RED Y2025) | no (L6M du +2636 dm -1345 | L3M du +1734 dm -1341) | no (L6M du +1820 dm -1319 | L3M du +1943 dm -3101) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L05222ff9 time_m_4 / momentum_rsi.mom_native {"len": 10, "lvl": 60} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +497 dm +464 | L3M du -884 dm +1412 RED Y2025) | no (L6M du +305 dm -2648 | L3M du +376 dm -3622) | no (L6M du +3608 dm -10597 | L3M du +2854 dm -7634) | yes (L6M du -395 dm +85 | L3M du -122 dm +1676 RED Y2025) | no (L6M du +76 dm -1277 | L3M du -883 dm +769) | no (L6M du +1042 dm -1651 | L3M du -39 dm -826) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |
| L63ff9ae8 time_m_4 / momentum_rsi.mom {"len": 10, "lvl": 60} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +497 dm +464 | L3M du -884 dm +1412) | not run | not run | yes (L6M du -395 dm +85 | L3M du -122 dm +1676) | not run | not run | K7:0,P7:0,A7:0,H7:0,U7:0 | 0 of 30 |
| L0b1d7882 tm30 / bands_vwap.break {"minbars": 10, "k": 1.0} / plain60/60 / both (both sides, engine-tested; screen mode long) | no (L6M du +782 dm +300 | L3M du +39 dm +724 RED Y2025) | no (L6M du +235 dm -3361 | L3M du +231 dm -4322) | no (L6M du +4343 dm -9748 | L3M du +3897 dm -6152) | yes (L6M du -65 dm +395 | L3M du -152 dm +1541 RED Y2025) | no (L6M du +1224 dm -1762 | L3M du +1599 dm -1201) | no (L6M du -117 dm -1186 | L3M du -2415 dm -21) | K7:0,P7:0,A7:3,H7:0,U7:0 | 0 of 30 |

## D8 gate (orders 0213Z, 0228Z)
Nothing enters D8 without the EXIT RUN (68 recipes) on its own entries. Candidates are appended to autopilot/D8_CANDIDATES.txt (append-only, session Asia). Engine cost after the exit screen for the 14 Asia cell(s) that beat a live book today: about 24122 set-months (prior years + 30 controls + layers/exit rows ~1,723 per candidate).

All other cells: see /mnt/l2/l2vast/_asi_lad/beats_rows.csv (verdict per live book: no / pending). Asia ladder state: `python3 code/th_asia/asia_ladder.py status`.

